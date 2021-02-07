---
title: 面向 Web Forms ASP.NET Web Forms 开发人员的 Blazor
description: 了解如何使用 Blazor 和 .NET Core 以简单而熟悉的方式使用 .NET 构建全栈式 Web 应用。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 02/02/2021
ms.openlocfilehash: 267f7222865c5a92d20faaae41b052da08c284a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653467"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a><span data-ttu-id="49adb-103">面向 Web Forms ASP.NET Web Forms 开发人员的 Blazor</span><span class="sxs-lookup"><span data-stu-id="49adb-103">Blazor for ASP.NET Web Forms Developers</span></span>

![显示无服务器应用电子书封面的屏幕截图。](./media/index/blazor-for-aspnet-web-forms-developers.png)

> <span data-ttu-id="49adb-105">下载地址：<https://aka.ms/blazor-ebook></span><span class="sxs-lookup"><span data-stu-id="49adb-105">DOWNLOAD available at: <https://aka.ms/blazor-ebook></span></span>

<span data-ttu-id="49adb-106">**版本 v1.0**</span><span class="sxs-lookup"><span data-stu-id="49adb-106">**EDITION v1.0**</span></span>

<span data-ttu-id="49adb-107">请参阅[更改记录](https://aka.ms/blazor-ebook-changelog)了解书籍更新和社区贡献。</span><span class="sxs-lookup"><span data-stu-id="49adb-107">Refer [changelog](https://aka.ms/blazor-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="49adb-108">发布者</span><span class="sxs-lookup"><span data-stu-id="49adb-108">PUBLISHED BY</span></span>

<span data-ttu-id="49adb-109">Microsoft 开发人员部门、.NET 和 Visual Studio 产品团队</span><span class="sxs-lookup"><span data-stu-id="49adb-109">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="49adb-110">Microsoft Corporation 的一个部门</span><span class="sxs-lookup"><span data-stu-id="49adb-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="49adb-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="49adb-111">One Microsoft Way</span></span>

<span data-ttu-id="49adb-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="49adb-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="49adb-113">版权所有 © 2021 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="49adb-113">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="49adb-114">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="49adb-114">All rights reserved.</span></span> <span data-ttu-id="49adb-115">未经发布者书面许可，不得以任何形式或任何方式复制或传播本书中的任何内容。</span><span class="sxs-lookup"><span data-stu-id="49adb-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="49adb-116">本书“按原样”提供，表达作者的观点和看法。</span><span class="sxs-lookup"><span data-stu-id="49adb-116">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="49adb-117">本书中表达的观点、看法和信息（包括 URL 和其他 Internet 网站引用）如有更改，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="49adb-117">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="49adb-118">本书中提及的一些示例仅用于说明，纯属虚构。</span><span class="sxs-lookup"><span data-stu-id="49adb-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="49adb-119">不存在任何实际关联或联系，请勿妄加推断。</span><span class="sxs-lookup"><span data-stu-id="49adb-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="49adb-120">Microsoft 和 <https://www.microsoft.com> 上“商标”网页列出的商标是 Microsoft 集团公司的商标。</span><span class="sxs-lookup"><span data-stu-id="49adb-120">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="49adb-121">Mac 和 macOS 是 Apple Inc. 的商标</span><span class="sxs-lookup"><span data-stu-id="49adb-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="49adb-122">所有其他标记和徽标均为其各自所有者的财产。</span><span class="sxs-lookup"><span data-stu-id="49adb-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="49adb-123">作者：</span><span class="sxs-lookup"><span data-stu-id="49adb-123">Authors:</span></span>

> <span data-ttu-id="49adb-124">[Daniel Roth](https://github.com/danroth27)，Microsoft Corp 首席项目经理。</span><span class="sxs-lookup"><span data-stu-id="49adb-124">**[Daniel Roth](https://github.com/danroth27)**, Principal Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="49adb-125">[Jeff Fritz](https://github.com/csharpfritz)，Microsoft Corp 资深项目经理。</span><span class="sxs-lookup"><span data-stu-id="49adb-125">**[Jeff Fritz](https://github.com/csharpfritz)**, Senior Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="49adb-126">[Taylor Southwick](https://github.com/twsouthwick)，Microsoft Corp 资深软件工程师。</span><span class="sxs-lookup"><span data-stu-id="49adb-126">**[Taylor Southwick](https://github.com/twsouthwick)**, Senior Software Engineer, Microsoft Corp.</span></span>

> <span data-ttu-id="49adb-127">[Scott Addie](https://github.com/scottaddie)，Microsoft Corp 资深内容开发人员。</span><span class="sxs-lookup"><span data-stu-id="49adb-127">**[Scott Addie](https://github.com/scottaddie)**, Senior Content Developer, Microsoft Corp.</span></span>

> <span data-ttu-id="49adb-128">[Steve "ardalis" Smith](https://ardalis.com)，Ardalis Services LLC 软件设计师及培训师</span><span class="sxs-lookup"><span data-stu-id="49adb-128">**[Steve "ardalis" Smith](https://ardalis.com)**, Software Architect and Trainer, Ardalis Services LLC</span></span>

## <a name="introduction"></a><span data-ttu-id="49adb-129">介绍</span><span class="sxs-lookup"><span data-stu-id="49adb-129">Introduction</span></span>

<span data-ttu-id="49adb-130">长期以来，.NET 通过 ASP.NET 支持 Web 应用开发，ASP.NET 是用于构建任何类型的 Web 应用的一组全面的框架和工具。</span><span class="sxs-lookup"><span data-stu-id="49adb-130">.NET has long supported web app development through ASP.NET, a comprehensive set of frameworks and tools for building any kind of web app.</span></span> <span data-ttu-id="49adb-131">ASP.NET 拥有自己的 Web 框架和技术谱系，始于经典的 Active Server Pages (ASP)。</span><span class="sxs-lookup"><span data-stu-id="49adb-131">ASP.NET has its own lineage of web frameworks and technologies starting all the way back with classic Active Server Pages (ASP).</span></span> <span data-ttu-id="49adb-132">ASP.NET Web Forms、ASP.NET MVC、ASP.NET 网页以及最新的 ASP.NET Core 等框架，提供了一种高效而强大的方法来构建服务器呈现的 Web 应用，在这类应用中，会响应 HTTP 请求在服务器上动态生成 UI 内容。</span><span class="sxs-lookup"><span data-stu-id="49adb-132">Frameworks like ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web Pages, and more recently ASP.NET Core, provide a productive and powerful way to build *server-rendered* web apps, where UI content is dynamically generated on the server in response to HTTP requests.</span></span> <span data-ttu-id="49adb-133">每个 ASP.NET 框架都迎合不同的受众和应用构建理念。</span><span class="sxs-lookup"><span data-stu-id="49adb-133">Each ASP.NET framework caters to a different audience and app building philosophy.</span></span> <span data-ttu-id="49adb-134">ASP.NET Web Forms 随 .NET Framework 的原始版本一起提供，允许使用桌面应用程序开发人员熟悉的多种模式（如具有简单事件处理功能的可重用 UI 控件）实现 Web 开发。</span><span class="sxs-lookup"><span data-stu-id="49adb-134">ASP.NET Web Forms shipped with the original release of the .NET Framework and enabled web development using many of the patterns familiar to desktop developers, like reusable UI controls with simple event handling.</span></span> <span data-ttu-id="49adb-135">但是，没有 ASP.NET 框架提供运行在用户浏览器中执行的代码的方法。</span><span class="sxs-lookup"><span data-stu-id="49adb-135">However, none of the ASP.NET offerings provide a way to run code that executed in the user's browser.</span></span> <span data-ttu-id="49adb-136">要执行此操作，需要编写 JavaScript 并使用这些年来经历了流行和退流行的 JavaScript 框架和工具：jQuery、Knockout、Angular、React 等。</span><span class="sxs-lookup"><span data-stu-id="49adb-136">To do that requires writing JavaScript and using any of the many JavaScript frameworks and tools that have phased in and out of popularity over the years: jQuery, Knockout, Angular, React, and so on.</span></span>

<span data-ttu-id="49adb-137">[Blazor](https://blazor.net) 是一个新的 Web 框架，它为使用 .NET 构建 Web 应用带来了新的可能。</span><span class="sxs-lookup"><span data-stu-id="49adb-137">[Blazor](https://blazor.net) is a new web framework that changes what is possible when building web apps with .NET.</span></span> <span data-ttu-id="49adb-138">Blazor 是基于 C# 而不是 JavaScript 的客户端 Web UI 框架。</span><span class="sxs-lookup"><span data-stu-id="49adb-138">Blazor is a client-side web UI framework based on C# instead of JavaScript.</span></span> <span data-ttu-id="49adb-139">借助 Blazor，可用 C# 编写客户端逻辑和 UI 组件，将其编译成普通的 .NET 程序集，然后使用称为 WebAssembly 的新开放式 Web 标准在浏览器中直接运行它们。</span><span class="sxs-lookup"><span data-stu-id="49adb-139">With Blazor you can write your client-side logic and UI components in C#, compile them into normal .NET assemblies, and then run them directly in the browser using a new open web standard called WebAssembly.</span></span> <span data-ttu-id="49adb-140">或者，Blazor 可在服务器上运行 .NET UI 组件，并通过与浏览器的实时连接流畅地处理所有 UI 交互。</span><span class="sxs-lookup"><span data-stu-id="49adb-140">Or alternatively, Blazor can run your .NET UI components on the server and handle all UI interactions fluidly over a real-time connection with the browser.</span></span> <span data-ttu-id="49adb-141">与服务器上运行的 .NET 配对时，Blazor 支持使用 .NET 进行全栈式 Web 开发。</span><span class="sxs-lookup"><span data-stu-id="49adb-141">When paired with .NET running on the server, Blazor enables full-stack web development with .NET.</span></span> <span data-ttu-id="49adb-142">虽然 Blazor 与 ASP.NET Web Forms 具有许多共同点，例如具有可重用的组件模型和处理用户事件的简单方法，但它还在 .NET 的基础之上提供了现代化高性能 Web 开发体验。</span><span class="sxs-lookup"><span data-stu-id="49adb-142">While Blazor shares many commonalities with ASP.NET Web Forms, like having a reusable component model and a simple way to handle user events, it also builds on the foundations of .NET to provide a modern and high-performance web development experience.</span></span>

<span data-ttu-id="49adb-143">本书以 ASP.NET Web Forms 开发人员熟悉和方便的方式向其介绍 Blazor。</span><span class="sxs-lookup"><span data-stu-id="49adb-143">This book introduces ASP.NET Web Forms developers to Blazor in a way that is familiar and convenient.</span></span> <span data-ttu-id="49adb-144">它并排介绍 Blazor 概念与 ASP.NET Web Forms 中的类似概念，还阐释了读者可能不太熟悉的新概念。</span><span class="sxs-lookup"><span data-stu-id="49adb-144">It introduces Blazor concepts in parallel with analogous concepts in ASP.NET Web Forms while also explaining new concepts that may be less familiar.</span></span> <span data-ttu-id="49adb-145">它涵盖了广泛的主题和关注点，包括组件创作、路由、布局、配置和安全性。</span><span class="sxs-lookup"><span data-stu-id="49adb-145">It covers a broad range of topics and concerns including component authoring, routing, layout, configuration, and security.</span></span> <span data-ttu-id="49adb-146">尽管本书的内容主要是介绍新的开发方法，但其中也介绍了将现有 ASP.NET Web Forms 迁移到 Blazor 的指导原则和策略，当你想要对现有应用进行现代化时，可以使用这些原则和策略。</span><span class="sxs-lookup"><span data-stu-id="49adb-146">And while the content of this book is primarily for enabling new development, it also covers guidelines and strategies for migrating existing ASP.NET Web Forms to Blazor for when you want to modernize an existing app.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="49adb-147">本书的目标读者</span><span class="sxs-lookup"><span data-stu-id="49adb-147">Who should use the book</span></span>

<span data-ttu-id="49adb-148">本书适用于正在寻找可联系到现有知识和技能的 Blazor 介绍的 ASP.NET Web Forms 开发人员。</span><span class="sxs-lookup"><span data-stu-id="49adb-148">This book is for ASP.NET Web Forms developers looking for an introduction to Blazor that relates to their existing knowledge and skills.</span></span> <span data-ttu-id="49adb-149">本书可帮助你快速开始构建基于 Blazor 的新项目，或帮助你为现代化 ASP.NET Web Forms 应用程序制定路线图。</span><span class="sxs-lookup"><span data-stu-id="49adb-149">This book can help with quickly getting started on a new Blazor-based project or to help chart a roadmap for modernizing an existing ASP.NET Web Forms application.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="49adb-150">如何使用本书</span><span class="sxs-lookup"><span data-stu-id="49adb-150">How to use the book</span></span>

<span data-ttu-id="49adb-151">本书的第一部分介绍了什么是 Blazor，并将其与使用 ASP.NET Web Forms 进行 Web 应用开发进行了比较。</span><span class="sxs-lookup"><span data-stu-id="49adb-151">The first part of this book covers what Blazor is and compares it to web app development with ASP.NET Web Forms.</span></span> <span data-ttu-id="49adb-152">然后，本书逐章介绍各个 Blazor 主题，并将 Blazor 的每个概念与 ASP.NET Web Forms 中的相应概念相关联，或全面阐释任何全新概念。</span><span class="sxs-lookup"><span data-stu-id="49adb-152">The book then covers a variety of Blazor topics, chapter by chapter, and relates each Blazor concept to the corresponding concept in ASP.NET Web Forms, or explains fully any completely new concepts.</span></span> <span data-ttu-id="49adb-153">本书还有规律地引用在 ASP.NET Web Forms 和 Blazor 中实现的完整示例应用，以演示 Blazor 的功能并提供从 ASP.NET Web Forms 迁移到 Blazor 的案例研究。</span><span class="sxs-lookup"><span data-stu-id="49adb-153">The book also refers regularly to a complete sample app implemented in both ASP.NET Web Forms and Blazor to demonstrate Blazor features and to provide a case study for migrating from ASP.NET Web Forms to Blazor.</span></span> <span data-ttu-id="49adb-154">可在 [GitHub](https://github.com/dotnet-architecture/eshoponblazor) 上找到示例应用的两种实现（ASP.NET Web Forms 和 Blazor 版本）。</span><span class="sxs-lookup"><span data-stu-id="49adb-154">You can find both implementations of the sample app (ASP.NET Web Forms and Blazor versions) on [GitHub](https://github.com/dotnet-architecture/eshoponblazor).</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="49adb-155">本书未涵盖的内容</span><span class="sxs-lookup"><span data-stu-id="49adb-155">What this book doesn't cover</span></span>

<span data-ttu-id="49adb-156">本书是 Blazor 的简介，而不是全面的迁移指南。</span><span class="sxs-lookup"><span data-stu-id="49adb-156">This book is an introduction to Blazor, not a comprehensive migration guide.</span></span> <span data-ttu-id="49adb-157">尽管它确实有指南介绍如何将项目从 ASP.NET Web Forms 迁移到 Blazor，但它并未尝试涵盖所有细微差别和细节。</span><span class="sxs-lookup"><span data-stu-id="49adb-157">While it does include guidance on how to approach migrating a project from ASP.NET Web Forms to Blazor, it does not attempt to cover every nuance and detail.</span></span> <span data-ttu-id="49adb-158">有关从 ASP.NET 迁移到 ASP.NET Core 的更多常规指南，请参阅 ASP.NET Core 文档中的[迁移指南](/aspnet/core/migration/proper-to-2x/)。</span><span class="sxs-lookup"><span data-stu-id="49adb-158">For more general guidance on migrating from ASP.NET to ASP.NET Core, refer to the [migration guidance](/aspnet/core/migration/proper-to-2x/) in the ASP.NET Core documentation.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="49adb-159">其他资源</span><span class="sxs-lookup"><span data-stu-id="49adb-159">Additional resources</span></span>

<span data-ttu-id="49adb-160">可在 <https://blazor.net> 上找到 Blazor 的官方主页和文档。</span><span class="sxs-lookup"><span data-stu-id="49adb-160">You can find the official Blazor home page and documentation at <https://blazor.net>.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="49adb-161">提供你的反馈</span><span class="sxs-lookup"><span data-stu-id="49adb-161">Send your feedback</span></span>

<span data-ttu-id="49adb-162">我们正在不断完善本书和相关示例，欢迎你提供反馈！</span><span class="sxs-lookup"><span data-stu-id="49adb-162">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="49adb-163">如果对如何改进本书有任何建议，请使用 [GitHub 问题](https://github.com/dotnet/docs/issues)上任何页面底部的反馈部分进行反馈。</span><span class="sxs-lookup"><span data-stu-id="49adb-163">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="49adb-164">下一页</span><span class="sxs-lookup"><span data-stu-id="49adb-164">Next</span></span>](introduction.md)
