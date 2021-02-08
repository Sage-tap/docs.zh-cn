---
description: 了解详细信息： <Crst_DisableSpinWait> 元素
title: <Crst_DisableSpinWait> 元素
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: fca6fed2dabc3d1319ad030bb13bbb35a561b9aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795100"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="27a89-103">\<Crst_DisableSpinWait> 元素</span><span class="sxs-lookup"><span data-stu-id="27a89-103">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="27a89-104">指定是否在争用时禁用临界区等待。</span><span class="sxs-lookup"><span data-stu-id="27a89-104">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="27a89-105">语法</span><span class="sxs-lookup"><span data-stu-id="27a89-105">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27a89-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="27a89-106">Attributes and Elements</span></span>

<span data-ttu-id="27a89-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="27a89-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27a89-108">特性</span><span class="sxs-lookup"><span data-stu-id="27a89-108">Attributes</span></span>  
  
|<span data-ttu-id="27a89-109">属性</span><span class="sxs-lookup"><span data-stu-id="27a89-109">Attribute</span></span>|<span data-ttu-id="27a89-110">说明</span><span class="sxs-lookup"><span data-stu-id="27a89-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27a89-111">**enabled**</span><span class="sxs-lookup"><span data-stu-id="27a89-111">**enabled**</span></span>|<span data-ttu-id="27a89-112">指定禁用已争用的关键部分时，是否旋转等待。</span><span class="sxs-lookup"><span data-stu-id="27a89-112">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="27a89-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="27a89-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="27a89-114">值</span><span class="sxs-lookup"><span data-stu-id="27a89-114">Value</span></span>|<span data-ttu-id="27a89-115">说明</span><span class="sxs-lookup"><span data-stu-id="27a89-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="27a89-116">1</span><span class="sxs-lookup"><span data-stu-id="27a89-116">1</span></span>|<span data-ttu-id="27a89-117">禁用在无法获取关键部分时等待自旋。</span><span class="sxs-lookup"><span data-stu-id="27a89-117">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="27a89-118">0</span><span class="sxs-lookup"><span data-stu-id="27a89-118">0</span></span>|<span data-ttu-id="27a89-119">不要在无法获取关键节时禁用自旋等待。</span><span class="sxs-lookup"><span data-stu-id="27a89-119">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="27a89-120">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="27a89-120">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27a89-121">子元素</span><span class="sxs-lookup"><span data-stu-id="27a89-121">Child Elements</span></span>  

 <span data-ttu-id="27a89-122">无。</span><span class="sxs-lookup"><span data-stu-id="27a89-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27a89-123">父元素</span><span class="sxs-lookup"><span data-stu-id="27a89-123">Parent Elements</span></span>  
  
|<span data-ttu-id="27a89-124">元素</span><span class="sxs-lookup"><span data-stu-id="27a89-124">Element</span></span>|<span data-ttu-id="27a89-125">说明</span><span class="sxs-lookup"><span data-stu-id="27a89-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="27a89-126">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="27a89-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="27a89-127">包含有关各种运行时配置设置的信息。</span><span class="sxs-lookup"><span data-stu-id="27a89-127">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27a89-128">示例</span><span class="sxs-lookup"><span data-stu-id="27a89-128">Example</span></span>  

<span data-ttu-id="27a89-129">下面的示例在争用时在关键部分禁用自旋。</span><span class="sxs-lookup"><span data-stu-id="27a89-129">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27a89-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="27a89-130">See also</span></span>

- [<span data-ttu-id="27a89-131">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="27a89-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="27a89-132">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="27a89-132">Configuration File Schema</span></span>](../index.md)
