---
description: 了解详细信息：自定义筛选器
title: 自定义筛选器
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 95a419823cf69575f951c0984e2136f9e7afca56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704974"
---
# <a name="custom-filters"></a><span data-ttu-id="141ef-103">自定义筛选器</span><span class="sxs-lookup"><span data-stu-id="141ef-103">Custom Filters</span></span>

<span data-ttu-id="141ef-104">借助自定义筛选器，您可以定义无法通过系统提供的消息筛选器实现的匹配逻辑。</span><span class="sxs-lookup"><span data-stu-id="141ef-104">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="141ef-105">例如，您可以创建这样的自定义筛选器：该筛选器散列特定的消息元素，然后检查元素值以确定该筛选器应返回 true 还是 false。</span><span class="sxs-lookup"><span data-stu-id="141ef-105">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="141ef-106">实现</span><span class="sxs-lookup"><span data-stu-id="141ef-106">Implementation</span></span>  

 <span data-ttu-id="141ef-107">自定义筛选器是 <xref:System.ServiceModel.Dispatcher.MessageFilter> 抽象基类的实现。</span><span class="sxs-lookup"><span data-stu-id="141ef-107">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="141ef-108">当实现自定义筛选器时，构造函数可以选择接受一个字符串参数。</span><span class="sxs-lookup"><span data-stu-id="141ef-108">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="141ef-109">该参数包含传递到 MessageFilter 构造函数的配置信息，以便提供筛选器为执行匹配而在运行时需要的任何值或配置。</span><span class="sxs-lookup"><span data-stu-id="141ef-109">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="141ef-110">例如，该参数可用于提供筛选器在要进行求值的消息中查找的值。</span><span class="sxs-lookup"><span data-stu-id="141ef-110">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="141ef-111">下面的示例演示接受字符串参数的自定义消息筛选器的基本实现：</span><span class="sxs-lookup"><span data-stu-id="141ef-111">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="141ef-112">在实际实现中，Match 方法 (s) 包含将检查消息以确定此消息筛选器是否应返回 **true** 或 **false** 的逻辑。</span><span class="sxs-lookup"><span data-stu-id="141ef-112">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="141ef-113">性能</span><span class="sxs-lookup"><span data-stu-id="141ef-113">Performance</span></span>  

 <span data-ttu-id="141ef-114">实现自定义筛选器时，应考虑筛选器完成消息评估所需要的最长时间，这十分重要。</span><span class="sxs-lookup"><span data-stu-id="141ef-114">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="141ef-115">由于某个消息可能需通过多个筛选器进行评估才能找到匹配项，因此应确保客户端请求在评估完所有筛选器之前不会超时，这十分重要。</span><span class="sxs-lookup"><span data-stu-id="141ef-115">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="141ef-116">因此，自定义筛选器只应包含评估消息的内容或特性所需的代码，以便确定消息是否匹配筛选条件。</span><span class="sxs-lookup"><span data-stu-id="141ef-116">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="141ef-117">一般而言，在实现自定义筛选器时，应避免以下情况：</span><span class="sxs-lookup"><span data-stu-id="141ef-117">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="141ef-118">IO，如将数据保存到磁盘或数据库。</span><span class="sxs-lookup"><span data-stu-id="141ef-118">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="141ef-119">不必要的处理，如循环访问文档中的多个记录。</span><span class="sxs-lookup"><span data-stu-id="141ef-119">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="141ef-120">阻止操作，如涉及获取共享资源上的锁的调用或涉及对数据库执行查找的调用。</span><span class="sxs-lookup"><span data-stu-id="141ef-120">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="141ef-121">在生产环境中使用自定义筛选器之前，应运行性能测试以确定筛选器评估消息所花费的平均时间长度。</span><span class="sxs-lookup"><span data-stu-id="141ef-121">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="141ef-122">与筛选器表中使用的其他筛选器的平均处理时间相结合，您便可精确确定客户端应用程序应指定的最大超时值。</span><span class="sxs-lookup"><span data-stu-id="141ef-122">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="141ef-123">使用情况</span><span class="sxs-lookup"><span data-stu-id="141ef-123">Usage</span></span>  

 <span data-ttu-id="141ef-124">若要将自定义筛选器与路由服务一起使用，必须通过指定 "自定义" 类型的新筛选器项，将消息筛选器的完全限定类型名称和程序集的名称添加到筛选器表中。</span><span class="sxs-lookup"><span data-stu-id="141ef-124">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="141ef-125">与其他 MessageFilter 一样，您可以指定将传递到自定义筛选器的构造函数中的字符串 filterData。</span><span class="sxs-lookup"><span data-stu-id="141ef-125">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="141ef-126">下面的示例演示如何对路由服务使用自定义筛选器：</span><span class="sxs-lookup"><span data-stu-id="141ef-126">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"
            customType="CustomAssembly.MyMessageFilter,
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
