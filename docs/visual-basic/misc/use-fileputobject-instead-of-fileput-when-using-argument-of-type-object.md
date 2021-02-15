---
description: 了解更多相关信息：使用 "Object" 类型的参数时，请使用 "FilePutObject" 而不是 "FilePut"
title: 在使用 "Object" 类型的自变量时，请使用 "FilePutObject"，而不要使用 "FilePut"
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 5e5822999aa39bff4d43f83a2719341034cdcadc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460093"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="18a1e-103">在使用 "Object" 类型的自变量时，请使用 "FilePutObject"，而不要使用 "FilePut"</span><span class="sxs-lookup"><span data-stu-id="18a1e-103">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>

<span data-ttu-id="18a1e-104">`FilePut` 方法包含 `Object`类型的参数。</span><span class="sxs-lookup"><span data-stu-id="18a1e-104">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="18a1e-105">应使用`FilePutObject` 替代 `FilePut` ，以避免多义性。</span><span class="sxs-lookup"><span data-stu-id="18a1e-105">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18a1e-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="18a1e-106">To correct this error</span></span>  
  
- <span data-ttu-id="18a1e-107">将 `FilePut` 替换为 `FilePutObject`。</span><span class="sxs-lookup"><span data-stu-id="18a1e-107">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="18a1e-108">将 `Object` 参数强制转换为一个更明确的类型。</span><span class="sxs-lookup"><span data-stu-id="18a1e-108">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="18a1e-109">使用 `My.Computer.FileSystem` 对象中的可用功能。</span><span class="sxs-lookup"><span data-stu-id="18a1e-109">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a1e-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="18a1e-110">See also</span></span>

- [<span data-ttu-id="18a1e-111">文件系统文件</span><span class="sxs-lookup"><span data-stu-id="18a1e-111">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="18a1e-112">文件 My.computer.filesystem.writeallbytes</span><span class="sxs-lookup"><span data-stu-id="18a1e-112">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
