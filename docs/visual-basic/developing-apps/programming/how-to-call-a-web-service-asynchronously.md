---
description: 详细了解：操作说明：异步调用 Web 服务 (Visual Basic)
title: 如何：以异步方式调用 Web 服务
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: a702177f60ac598f624676072116bd3ce78da0bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775248"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="90e27-103">如何：异步调用 Web 服务 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90e27-103">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="90e27-104">此示例在 Web 服务的异步处理程序事件中附加了一个处理程序，以便它能检索异步方法调用的结果。</span><span class="sxs-lookup"><span data-stu-id="90e27-104">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="90e27-105">此示例使用了 DemoTemperatureService Web 服务（位于 `http://www.xmethods.net`）。</span><span class="sxs-lookup"><span data-stu-id="90e27-105">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="90e27-106">在 Visual Studio 集成开发环境 (IDE) 中引用项目中的 Web 服务时，该服务将添加到 `My.WebServices` 对象中，且 IDE 将生成一个客户端代理类来访问指定的 Web 服务</span><span class="sxs-lookup"><span data-stu-id="90e27-106">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="90e27-107">使用此代理类可以同步调用 Web 服务方法，而应用程序则在 Web 服务方法内等待函数执行完成。</span><span class="sxs-lookup"><span data-stu-id="90e27-107">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="90e27-108">另外，代理还创建其他成员来协助异步调用方法。</span><span class="sxs-lookup"><span data-stu-id="90e27-108">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="90e27-109">对于每一个 Web 服务函数（*NameOfWebServiceFunction*），代理都会创建一个 *NameOfWebServiceFunction*`Async` 子例程、一个 *NameOfWebServiceFunction*`Completed` 事件和一个 *NameOfWebServiceFunction*`CompletedEventArgs` 类。</span><span class="sxs-lookup"><span data-stu-id="90e27-109">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="90e27-110">此示例演示如何使用异步成员访问 DemoTemperatureService Web 服务的 `getTemp` 函数。</span><span class="sxs-lookup"><span data-stu-id="90e27-110">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="90e27-111">因为 ASP.NET 不支持 `My.WebServices` 对象，所以这段代码不适用于 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="90e27-111">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="90e27-112">以异步方式调用 Web 服务</span><span class="sxs-lookup"><span data-stu-id="90e27-112">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="90e27-113">引用 DemoTemperatureService Web 服务（位于 `http://www.xmethods.net`）。</span><span class="sxs-lookup"><span data-stu-id="90e27-113">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="90e27-114">网址为</span><span class="sxs-lookup"><span data-stu-id="90e27-114">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="90e27-115">为 `getTempCompleted` 事件添加事件处理程序：</span><span class="sxs-lookup"><span data-stu-id="90e27-115">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="90e27-116">不能使用 `Handles` 语句将事件处理程序与 `My.WebServices` 对象的事件关联起来。</span><span class="sxs-lookup"><span data-stu-id="90e27-116">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="90e27-117">如果已将事件处理程序添加到 `getTempCompleted` 事件，则添加要跟踪的字段：</span><span class="sxs-lookup"><span data-stu-id="90e27-117">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="90e27-118">添加一个方法，以将事件处理程序添加到 `getTempCompleted` 事件（如有必要）并调用 `getTempAsync` 方法：</span><span class="sxs-lookup"><span data-stu-id="90e27-118">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

    ```vb
    Sub CallGetTempAsync(ByVal zipCode As Integer)
        If Not handlerAttached Then
            AddHandler My.WebServices.
                TemperatureService.getTempCompleted,
                AddressOf Me.TS_getTempCompleted
            handlerAttached = True
        End If
        My.WebServices.TemperatureService.getTempAsync(zipCode)
    End Sub
    ```

    <span data-ttu-id="90e27-119">若要以异步方式调用 `getTemp` Web 方法，请调用 `CallGetTempAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="90e27-119">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="90e27-120">当 Web 方法执行完成后，其返回值将被传递到 `getTempCompletedHandler` 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="90e27-120">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="90e27-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90e27-121">See also</span></span>

- [<span data-ttu-id="90e27-122">访问应用程序 Web 服务</span><span class="sxs-lookup"><span data-stu-id="90e27-122">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="90e27-123">My.WebServices 对象</span><span class="sxs-lookup"><span data-stu-id="90e27-123">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
