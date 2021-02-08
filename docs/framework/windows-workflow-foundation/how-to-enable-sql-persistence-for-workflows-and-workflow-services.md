---
description: 了解详细信息：如何：为工作流和工作流服务启用 SQL 持久性
title: 如何：对工作流和工作流服务启用 SQL 持久性
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 5c124c4ec1d75d4b3b24468c04a4fb82236aa29a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777718"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="c3d69-103">如何：对工作流和工作流服务启用 SQL 持久性</span><span class="sxs-lookup"><span data-stu-id="c3d69-103">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="c3d69-104">本主题介绍如何通过编程方式以及使用配置文件来配置 SQL 工作流实例存储功能，以便为工作流和工作流服务启用持久性。</span><span class="sxs-lookup"><span data-stu-id="c3d69-104">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="c3d69-105">Windows Server App Fabric 大大简化了配置持久性的过程。</span><span class="sxs-lookup"><span data-stu-id="c3d69-105">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="c3d69-106">有关详细信息，请参阅 [应用构造持久性配置](/previous-versions/appfabric/ee790848(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="c3d69-106">For more information, see [App Fabric Persistence Configuration](/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="c3d69-107">使用 SQL 工作流实例存储功能之前，创建一个数据库以供该功能用来持久保存工作流实例。</span><span class="sxs-lookup"><span data-stu-id="c3d69-107">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="c3d69-108">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 安装程序将与 SQL 工作流实例存储功能相关联的 SQL 脚本文件复制到 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c3d69-108">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="c3d69-109">针对您希望 SQL 工作流实例存储用于持久保存工作流实例的 SQL Server 2005 或 SQL Server 2008 数据库，运行这些脚本文件。</span><span class="sxs-lookup"><span data-stu-id="c3d69-109">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="c3d69-110">首先运行 SqlWorkflowInstanceStoreSchema.sql 文件，之后运行 SqlWorkflowInstanceStoreLogic.sql 文件。</span><span class="sxs-lookup"><span data-stu-id="c3d69-110">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="c3d69-111">若要清除此持久性数据库以获得一个全新的数据库，请按下列顺序运行 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN 中的脚本。</span><span class="sxs-lookup"><span data-stu-id="c3d69-111">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="c3d69-112">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="c3d69-112">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="c3d69-113">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="c3d69-113">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3d69-114">如果不创建持久性数据库，则当宿主尝试持久保存工作流时，SQL 工作流实例存储功能将引发与以下异常类似的异常。</span><span class="sxs-lookup"><span data-stu-id="c3d69-114">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="c3d69-115">System.Data.SqlClient.SqlException: 找不到存储过程“System.Activities.DurableInstancing.CreateLockOwner”</span><span class="sxs-lookup"><span data-stu-id="c3d69-115">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="c3d69-116">下面介绍如何使用 SQL 工作流实例存储来为工作流与工作流服务启用持久性。</span><span class="sxs-lookup"><span data-stu-id="c3d69-116">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="c3d69-117">有关 SQL 工作流实例存储的属性的详细信息，请参阅 [Sql 工作流实例存储的属性](properties-of-sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="c3d69-117">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="c3d69-118">为使用 WorkflowApplication 的自承载工作流启用持久性</span><span class="sxs-lookup"><span data-stu-id="c3d69-118">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="c3d69-119">可通过使用 <xref:System.Activities.WorkflowApplication> 对象模型为以编程方式使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 的自承载工作流启用持久性。</span><span class="sxs-lookup"><span data-stu-id="c3d69-119">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="c3d69-120">以下过程包含了执行上述操作的步骤。</span><span class="sxs-lookup"><span data-stu-id="c3d69-120">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="c3d69-121">为自承载工作流启用持久性</span><span class="sxs-lookup"><span data-stu-id="c3d69-121">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="c3d69-122">添加对 System.Activities.DurableInstancing.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="c3d69-122">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="c3d69-123">将以下语句添加到源文件顶部的现有“using”语句后面。</span><span class="sxs-lookup"><span data-stu-id="c3d69-123">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="c3d69-124">如下面的代码示例中所示，构造一个 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>，并将其分配给 <xref:System.Activities.WorkflowApplication.InstanceStore%2A> 的 <xref:System.Activities.WorkflowApplication>。</span><span class="sxs-lookup"><span data-stu-id="c3d69-124">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="c3d69-125">根据您的 SQL Server 版本，该连接字符串服务器的名称可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="c3d69-125">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="c3d69-126">对 <xref:System.Activities.WorkflowApplication.Persist%2A> 对象调用 <xref:System.Activities.WorkflowApplication> 方法以持久保存工作流，或者调用 <xref:System.Activities.WorkflowApplication.Unload%2A> 方法以持久保存并卸载工作流。</span><span class="sxs-lookup"><span data-stu-id="c3d69-126">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="c3d69-127">还可以处理由 <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> 对象引发的 <xref:System.Activities.WorkflowApplication> 事件，并返回 <xref:System.Activities.PersistableIdleAction.Persist> 的适当的（<xref:System.Activities.PersistableIdleAction.Unload> 或 <xref:System.Activities.PersistableIdleAction>）成员。</span><span class="sxs-lookup"><span data-stu-id="c3d69-127">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="c3d69-128">有关分步说明，请参阅[入门教程](getting-started-tutorial.md)中的 "[如何：创建和运行长时间运行的工作流](how-to-create-and-run-a-long-running-workflow.md)" 步骤。</span><span class="sxs-lookup"><span data-stu-id="c3d69-128">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="c3d69-129">为使用 WorkflowServiceHost 的自承载工作流服务启用持久性</span><span class="sxs-lookup"><span data-stu-id="c3d69-129">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="c3d69-130">可通过使用 <xref:System.ServiceModel.WorkflowServiceHost> 类或者 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 类为以编程方式使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> 的自承载工作流服务启用持久性。</span><span class="sxs-lookup"><span data-stu-id="c3d69-130">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="c3d69-131">使用 SqlWorkflowInstanceStoreBehavior 类</span><span class="sxs-lookup"><span data-stu-id="c3d69-131">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="c3d69-132">以下过程包含使用 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 类来为自承载工作流服务启用持久性的步骤。</span><span class="sxs-lookup"><span data-stu-id="c3d69-132">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="c3d69-133">使用 SqlWorkflowInstanceStoreBehavior 启用持久性</span><span class="sxs-lookup"><span data-stu-id="c3d69-133">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="c3d69-134">添加对 System.ServiceModel.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="c3d69-134">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="c3d69-135">将以下语句添加到源文件顶部的现有“using”语句后面。</span><span class="sxs-lookup"><span data-stu-id="c3d69-135">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="c3d69-136">创建一个 `WorkflowServiceHost` 实例，并为该工作流服务添加终结点。</span><span class="sxs-lookup"><span data-stu-id="c3d69-136">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="c3d69-137">构造一个 `SqlWorkflowInstanceStoreBehavior` 对象，并设置该行为对象的属性。</span><span class="sxs-lookup"><span data-stu-id="c3d69-137">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="c3d69-138">打开工作流服务主机。</span><span class="sxs-lookup"><span data-stu-id="c3d69-138">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="c3d69-139">使用 DurableInstancingOptions 属性</span><span class="sxs-lookup"><span data-stu-id="c3d69-139">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="c3d69-140">应用 `SqlWorkflowInstanceStoreBehavior` 时，`DurableInstancingOptions.InstanceStore` 上的 `WorkflowServiceHost` 设置为使用配置值创建的 `SqlWorkflowInstanceStore` 对象。</span><span class="sxs-lookup"><span data-stu-id="c3d69-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="c3d69-141">如下面的代码示例中所示，你可以通过编程方式设置 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> 的 `WorkflowServiceHost` 属性（而不使用 `SqlWorkflowInstanceStoreBehavior` 类）来达到相同目的。</span><span class="sxs-lookup"><span data-stu-id="c3d69-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="c3d69-142">使用配置文件为使用 WorkflowServiceHost 的 WAS 承载工作流服务启用持久性</span><span class="sxs-lookup"><span data-stu-id="c3d69-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="c3d69-143">可使用配置文件为自承载或 Windows 进程激活服务 (WAS) 承载的工作流服务启用持久性。</span><span class="sxs-lookup"><span data-stu-id="c3d69-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="c3d69-144">WAS 承载的工作流服务与自承载工作流服务一样，都使用 WorkflowServiceHost。</span><span class="sxs-lookup"><span data-stu-id="c3d69-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="c3d69-145">`SqlWorkflowInstanceStoreBehavior`，一种服务行为，可用于通过 XML 配置方便地更改[SQL 工作流实例存储](sql-workflow-instance-store.md)属性。</span><span class="sxs-lookup"><span data-stu-id="c3d69-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="c3d69-146">对于 WAS 承载的工作流服务，请使用 Web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="c3d69-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="c3d69-147">下面的配置示例演示如何使用配置文件中的 `sqlWorkflowInstanceStore` 行为元素来配置 SQL 工作流实例存储。</span><span class="sxs-lookup"><span data-stu-id="c3d69-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="c3d69-148">如果没有设置 `connectionString` 或 `connectionStringName` 属性的值，则 SQL 工作流实例存储将使用默认命名连接字符串 `DefaultSqlWorkflowInstanceStoreConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="c3d69-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="c3d69-149">应用 `SqlWorkflowInstanceStoreBehavior` 时，`DurableInstancingOptions.InstanceStore` 上的 `WorkflowServiceHost` 设置为使用配置值创建的 `SqlWorkflowInstanceStore` 对象。</span><span class="sxs-lookup"><span data-stu-id="c3d69-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="c3d69-150">可以通过编程方式将 `SqlWorkflowInstanceStore` 与 `WorkflowServiceHost` 一起使用，而不使用服务行为元素来达到相同目的。</span><span class="sxs-lookup"><span data-stu-id="c3d69-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="c3d69-151">建议不要在 Web.config 文件中存储敏感信息，如用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="c3d69-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="c3d69-152">如果在 Web.config 文件中存储了敏感信息，应使用文件系统访问控制列表 (ACL) 来确保安全访问 Web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="c3d69-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="c3d69-153">此外，还可以在 [使用受保护配置加密配置信息](/previous-versions/aspnet/53tyfkaw(v=vs.100))中所述，保护配置文件中的配置值。</span><span class="sxs-lookup"><span data-stu-id="c3d69-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="c3d69-154">与 SQL 工作流实例存储功能相关的 Machine.config 元素</span><span class="sxs-lookup"><span data-stu-id="c3d69-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="c3d69-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 安装将以下与 SQL 工作流实例存储功能相关的元素添加到 Machine.config 文件中：</span><span class="sxs-lookup"><span data-stu-id="c3d69-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="c3d69-156">将以下行为扩展元素添加到 Machine.config 文件中，以便可以使用 \<sqlWorkflowInstanceStore> 配置文件中的服务行为元素来为服务配置持久性。</span><span class="sxs-lookup"><span data-stu-id="c3d69-156">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
