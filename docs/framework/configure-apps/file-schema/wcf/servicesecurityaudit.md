---
description: 了解详细信息： <serviceSecurityAudit>
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 262341f44adb7657086edb8d33514c07195ddfa3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682743"
---
# \<serviceSecurityAudit>

<span data-ttu-id="2deab-102">指定用于在服务操作过程中启用安全事件审核的设置。</span><span class="sxs-lookup"><span data-stu-id="2deab-102">Specifies settings that enable auditing of security events during service operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceSecurityAudit>**  
  
## <a name="syntax"></a><span data-ttu-id="2deab-103">语法</span><span class="sxs-lookup"><span data-stu-id="2deab-103">Syntax</span></span>  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2deab-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2deab-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2deab-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2deab-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2deab-106">特性</span><span class="sxs-lookup"><span data-stu-id="2deab-106">Attributes</span></span>  
  
|<span data-ttu-id="2deab-107">属性</span><span class="sxs-lookup"><span data-stu-id="2deab-107">Attribute</span></span>|<span data-ttu-id="2deab-108">说明</span><span class="sxs-lookup"><span data-stu-id="2deab-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2deab-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="2deab-109">auditLogLocation</span></span>|<span data-ttu-id="2deab-110">指定审核日志的位置。</span><span class="sxs-lookup"><span data-stu-id="2deab-110">Specifies the location of the audit log.</span></span> <span data-ttu-id="2deab-111">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="2deab-111">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2deab-112">-默认：将安全事件写入 Windows XP 上的应用程序日志以及 Windows Server 2003 和 Windows Vista 上的事件日志。</span><span class="sxs-lookup"><span data-stu-id="2deab-112">-   Default: Security events are written to the application log on Windows XP, and to the Event Log on Windows Server 2003 and Windows Vista.</span></span><br /><span data-ttu-id="2deab-113">-应用程序：审核事件将写入到应用程序事件日志中。</span><span class="sxs-lookup"><span data-stu-id="2deab-113">-   Application: Audit events are written to the Application Event Log.</span></span><br /><span data-ttu-id="2deab-114">-Security：审核事件将写入安全事件日志。</span><span class="sxs-lookup"><span data-stu-id="2deab-114">-   Security: Audit events are written to the Security Event Log.</span></span><br /><br /> <span data-ttu-id="2deab-115">默认值为 Default。</span><span class="sxs-lookup"><span data-stu-id="2deab-115">The default value is Default.</span></span> <span data-ttu-id="2deab-116">有关详细信息，请参阅 <xref:System.ServiceModel.AuditLogLocation>。</span><span class="sxs-lookup"><span data-stu-id="2deab-116">For more information, see <xref:System.ServiceModel.AuditLogLocation>.</span></span>|  
|<span data-ttu-id="2deab-117">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="2deab-117">suppressAuditFailure</span></span>|<span data-ttu-id="2deab-118">一个布尔值，指定取消显示审核日志写入失败的行为。</span><span class="sxs-lookup"><span data-stu-id="2deab-118">A Boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span><br /><br /> <span data-ttu-id="2deab-119">应将对审核日志的写入错误通知给应用程序。</span><span class="sxs-lookup"><span data-stu-id="2deab-119">Applications should be notified for failures of writing to the audit log.</span></span> <span data-ttu-id="2deab-120">如果应用程序并不用于处理审核错误，则应使用此属性取消显示审核日志写入失败。</span><span class="sxs-lookup"><span data-stu-id="2deab-120">If your application is not designed to handle audit failures, you should use this attribute to suppress failures in writing to the audit log.</span></span><br /><br /> <span data-ttu-id="2deab-121">如果此属性为 `true`，则因尝试写入审核事件而导致的异常（OutOfMemoryException、StackOverFlowException、ThreadAbortException 和 ArgumentException 除外）将由系统进行处理并且不会传播到应用程序。</span><span class="sxs-lookup"><span data-stu-id="2deab-121">If this attribute is `true`, exceptions other than OutOfMemoryException, StackOverFlowException, ThreadAbortException, and ArgumentException that result from attempts to write audit events are handled by the system, and are not propagated to the application.</span></span> <span data-ttu-id="2deab-122">如果此属性为 `false`，则因尝试写入审核事件而导致的所有异常都将向上传递给应用程序。</span><span class="sxs-lookup"><span data-stu-id="2deab-122">If this attribute is `false`, all exceptions that result from attempts to write audit events are passed up to the application.</span></span><br /><br /> <span data-ttu-id="2deab-123">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="2deab-123">The default is `true`.</span></span>|  
|<span data-ttu-id="2deab-124">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="2deab-124">serviceAuthorizationAuditLevel</span></span>|<span data-ttu-id="2deab-125">指定审核日志中记录的授权事件的类型。</span><span class="sxs-lookup"><span data-stu-id="2deab-125">Specifies the types of authorization events that are recorded in the audit log.</span></span> <span data-ttu-id="2deab-126">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="2deab-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2deab-127">-None：不执行任何服务授权事件的审核。</span><span class="sxs-lookup"><span data-stu-id="2deab-127">-   None: No auditing of service authorization events is performed.</span></span><br /><span data-ttu-id="2deab-128">-Success：仅审核成功的服务授权事件。</span><span class="sxs-lookup"><span data-stu-id="2deab-128">-   Success: Only successful service authorization events are audited.</span></span><br /><span data-ttu-id="2deab-129">-失败：仅审核失败的服务授权事件。</span><span class="sxs-lookup"><span data-stu-id="2deab-129">-   Failure: Only failure service authorization events are audited.</span></span><br /><span data-ttu-id="2deab-130">-SuccessOrFailure：审核成功和失败的服务授权事件。</span><span class="sxs-lookup"><span data-stu-id="2deab-130">-   SuccessOrFailure: Both success and failure service authorization events are audited.</span></span><br /><br /> <span data-ttu-id="2deab-131">默认值为 None。</span><span class="sxs-lookup"><span data-stu-id="2deab-131">The default value is None.</span></span> <span data-ttu-id="2deab-132">有关详细信息，请参阅 <xref:System.ServiceModel.AuditLevel>。</span><span class="sxs-lookup"><span data-stu-id="2deab-132">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
|<span data-ttu-id="2deab-133">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="2deab-133">messageAuthenticationAuditLevel</span></span>|<span data-ttu-id="2deab-134">指定所记录的消息身份验证审核事件的类型。</span><span class="sxs-lookup"><span data-stu-id="2deab-134">Specifies the type of message authentication audit events logged.</span></span> <span data-ttu-id="2deab-135">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="2deab-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2deab-136">-None：不生成审核事件。</span><span class="sxs-lookup"><span data-stu-id="2deab-136">-   None: No audit events are generated.</span></span><br /><span data-ttu-id="2deab-137">-Success：仅记录成功安全 (完全验证，包括消息签名验证、密码和令牌验证) 事件。</span><span class="sxs-lookup"><span data-stu-id="2deab-137">-   Success: Only successful security (full validation including message signature validation, cipher, and token validation) events are logged.</span></span><br /><span data-ttu-id="2deab-138">-失败：只记录失败事件。</span><span class="sxs-lookup"><span data-stu-id="2deab-138">-   Failure: Only failure events are logged.</span></span><br /><span data-ttu-id="2deab-139">-SuccessOrFailure：成功和失败事件都被记录。</span><span class="sxs-lookup"><span data-stu-id="2deab-139">-   SuccessOrFailure: Both success and failure events are logged.</span></span><br /><br /> <span data-ttu-id="2deab-140">默认值为 None。</span><span class="sxs-lookup"><span data-stu-id="2deab-140">The default value is None.</span></span> <span data-ttu-id="2deab-141">有关详细信息，请参阅 <xref:System.ServiceModel.AuditLevel>。</span><span class="sxs-lookup"><span data-stu-id="2deab-141">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2deab-142">子元素</span><span class="sxs-lookup"><span data-stu-id="2deab-142">Child Elements</span></span>  

 <span data-ttu-id="2deab-143">无。</span><span class="sxs-lookup"><span data-stu-id="2deab-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2deab-144">父元素</span><span class="sxs-lookup"><span data-stu-id="2deab-144">Parent Elements</span></span>  
  
|<span data-ttu-id="2deab-145">元素</span><span class="sxs-lookup"><span data-stu-id="2deab-145">Element</span></span>|<span data-ttu-id="2deab-146">说明</span><span class="sxs-lookup"><span data-stu-id="2deab-146">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2deab-147">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="2deab-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2deab-148">备注</span><span class="sxs-lookup"><span data-stu-id="2deab-148">Remarks</span></span>  

 <span data-ttu-id="2deab-149">此配置元素用于审核 Windows Communication Foundation (WCF) 身份验证事件。</span><span class="sxs-lookup"><span data-stu-id="2deab-149">This configuration element is used to audit Windows Communication Foundation (WCF) authentication events.</span></span> <span data-ttu-id="2deab-150">当启用了审核时，可对成功或失败的身份验证尝试（或这两者）进行审核。</span><span class="sxs-lookup"><span data-stu-id="2deab-150">When auditing is enabled, either successful or failed authentication attempts (or both) can be audited.</span></span> <span data-ttu-id="2deab-151">事件会写入到三个事件日志之一：操作系统版本的应用程序日志、安全日志或默认日志。</span><span class="sxs-lookup"><span data-stu-id="2deab-151">The events are written to one of three event logs: application, security, or the default log for the operating system version.</span></span> <span data-ttu-id="2deab-152">可以使用 Windows 事件查看器查看所有事件日志。</span><span class="sxs-lookup"><span data-stu-id="2deab-152">The event logs can all be viewed using the Windows Event viewer.</span></span>  
  
 <span data-ttu-id="2deab-153">有关使用此配置元素的详细示例，请参阅 [服务审核行为](../../../wcf/samples/service-auditing-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="2deab-153">For a detailed example of using this configuration element, see [Service Auditing Behavior](../../../wcf/samples/service-auditing-behavior.md).</span></span>  
  
 <span data-ttu-id="2deab-154">默认情况下，可在 Windows XP 上的应用程序日志中查看审核事件；而在 Windows Server 2003 和 Windows Vista 上，可在安全日志中查看审核事件。</span><span class="sxs-lookup"><span data-stu-id="2deab-154">By default, on Windows XP the audit events can be seen in the Application Log; while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="2deab-155">通过将 `auditLogLocation` 属性设置为“Application”或“Security”，可以指定审核事件的位置。</span><span class="sxs-lookup"><span data-stu-id="2deab-155">The location of audit events can be specified by setting the `auditLogLocation` attribute to 'Application' or 'Security'.</span></span> <span data-ttu-id="2deab-156">有关详细信息，请参阅 [如何：审核安全事件](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)。</span><span class="sxs-lookup"><span data-stu-id="2deab-156">For more information, see [How to: Audit Security Events](../../../wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="2deab-157">如果在安全日志中写入事件，则应将 > LocalSecurityPolicy 启用对象访问设置为 "成功" 和 "失败"。</span><span class="sxs-lookup"><span data-stu-id="2deab-157">If the events are written in the Security Log, the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="2deab-158">在查看事件日志时，审核事件的来源为“ServiceModel Audit 3.0.0.0”。</span><span class="sxs-lookup"><span data-stu-id="2deab-158">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="2deab-159">消息身份验证审核记录的类别为“MessageAuthentication”，而服务授权审核记录的类别为“ServiceAuthorization”。</span><span class="sxs-lookup"><span data-stu-id="2deab-159">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of 'ServiceAuthorization'.</span></span>  
  
 <span data-ttu-id="2deab-160">消息身份验证审核事件包含消息是否被篡改、消息是否已过期以及客户端是否可以向服务进行身份验证等信息。</span><span class="sxs-lookup"><span data-stu-id="2deab-160">Message authentication audit events cover whether the message was tampered with, whether the message has expired and whether the client can authenticate to the service.</span></span> <span data-ttu-id="2deab-161">这些事件还提供了有关身份验证是成功还是失败（以及客户端标识）的信息和有关消息所发送到的终结点（以及与消息关联的操作）的信息。</span><span class="sxs-lookup"><span data-stu-id="2deab-161">They provide information about whether the authentication succeeded or failed along with the identity of the client and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="2deab-162">服务授权审核事件包含服务授权管理器所做出的授权决定。</span><span class="sxs-lookup"><span data-stu-id="2deab-162">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="2deab-163">它们提供有关授权是成功还是失败以及客户端标识、消息所发送到的终结点、与消息关联的操作、从传入消息中生成的授权上下文的标识符和做出访问决定的授权管理器类型的信息。</span><span class="sxs-lookup"><span data-stu-id="2deab-163">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message and the type of the authorization manager that made the access decision.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2deab-164">示例</span><span class="sxs-lookup"><span data-stu-id="2deab-164">Example</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="2deab-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="2deab-165">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [<span data-ttu-id="2deab-166">安全行为</span><span class="sxs-lookup"><span data-stu-id="2deab-166">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2deab-167">审核</span><span class="sxs-lookup"><span data-stu-id="2deab-167">Auditing</span></span>](../../../wcf/feature-details/auditing-security-events.md)
- [<span data-ttu-id="2deab-168">如何：审核安全事件</span><span class="sxs-lookup"><span data-stu-id="2deab-168">How to: Audit Security Events</span></span>](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [<span data-ttu-id="2deab-169">服务审核行为</span><span class="sxs-lookup"><span data-stu-id="2deab-169">Service Auditing Behavior</span></span>](../../../wcf/samples/service-auditing-behavior.md)
