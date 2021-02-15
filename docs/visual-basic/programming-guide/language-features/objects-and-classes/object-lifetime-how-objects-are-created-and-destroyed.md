---
description: '了解有关以下内容的详细信息：对象生存期：如何创建和销毁对象 (Visual Basic) '
title: 对象生存期：如何创建和销毁对象
ms.date: 07/20/2015
f1_keywords:
- vb.Constructor
helpviewer_keywords:
- destructors, object lifetime
- Sub Finalize destructor
- objects [Visual Basic], destroying
- lifetime [Visual Basic], objects
- Sub New constructor, object lifetime
- Finalize method [Visual Basic], object lifetime
- objects [Visual Basic], creating
- Class_Terminate
- Dispose method [Visual Basic], object lifetime
- Class_Initialize
- object creation [Visual Basic], object lifetime
- parameterized constructors
- objects [Visual Basic], lifetime
- objects [Visual Basic], garbage collection
- constructors [Visual Basic], object lifetime
- Sub Dispose destructor
- garbage collection [Visual Basic], Visual Basic
ms.assetid: f1ee8458-b156-44e0-9a8a-5dd171648cd8
ms.openlocfilehash: 424a5619ea50d9da9bf069488ce7cac16527efbe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438822"
---
# <a name="object-lifetime-how-objects-are-created-and-destroyed-visual-basic"></a><span data-ttu-id="49c3f-103">对象生存期：如何创建和销毁对象 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49c3f-103">Object Lifetime: How Objects Are Created and Destroyed (Visual Basic)</span></span>

<span data-ttu-id="49c3f-104">使用 `New` 关键字创建类的实例（即对象）。</span><span class="sxs-lookup"><span data-stu-id="49c3f-104">An instance of a class, an object, is created by using the `New` keyword.</span></span> <span data-ttu-id="49c3f-105">通常，初始化任务必须在使用之前在新对象上执行。</span><span class="sxs-lookup"><span data-stu-id="49c3f-105">Initialization tasks often must be performed on new objects before they are used.</span></span> <span data-ttu-id="49c3f-106">常见的初始化任务包括打开文件、连接到数据库以及读取注册表项的值。</span><span class="sxs-lookup"><span data-stu-id="49c3f-106">Common initialization tasks include opening files, connecting to databases, and reading values of registry keys.</span></span> <span data-ttu-id="49c3f-107">Visual Basic 使用称为 " *构造函数* " 的过程来控制新对象的初始化， (允许控制初始化) 的特殊方法。</span><span class="sxs-lookup"><span data-stu-id="49c3f-107">Visual Basic controls the initialization of new objects using procedures called *constructors* (special methods that allow control over initialization).</span></span>

<span data-ttu-id="49c3f-108">对象离开范围之后，由公共语言运行时 (CLR) 进行释放。</span><span class="sxs-lookup"><span data-stu-id="49c3f-108">After an object leaves scope, it is released by the common language runtime (CLR).</span></span> <span data-ttu-id="49c3f-109">Visual Basic 使用称为 *析构函数* 的过程控制系统资源的发行。</span><span class="sxs-lookup"><span data-stu-id="49c3f-109">Visual Basic controls the release of system resources using procedures called *destructors*.</span></span> <span data-ttu-id="49c3f-110">同时，构造函数和析构函数支持强大、可预测的类库的创建。</span><span class="sxs-lookup"><span data-stu-id="49c3f-110">Together, constructors and destructors support the creation of robust and predictable class libraries.</span></span>

## <a name="using-constructors-and-destructors"></a><span data-ttu-id="49c3f-111">使用构造函数和析构函数</span><span class="sxs-lookup"><span data-stu-id="49c3f-111">Using Constructors and Destructors</span></span>

<span data-ttu-id="49c3f-112">构造函数和析构函数控制对象的创建和析构。</span><span class="sxs-lookup"><span data-stu-id="49c3f-112">Constructors and destructors control the creation and destruction of objects.</span></span> <span data-ttu-id="49c3f-113">`Sub New`中的和 `Sub Finalize` 过程 Visual Basic 初始化和销毁对象; 它们替换 `Class_Initialize` `Class_Terminate` Visual Basic 6.0 及更早版本中使用的和方法。</span><span class="sxs-lookup"><span data-stu-id="49c3f-113">The `Sub New` and `Sub Finalize` procedures in Visual Basic initialize and destroy objects; they replace the `Class_Initialize` and `Class_Terminate` methods used in Visual Basic 6.0 and earlier versions.</span></span>

### <a name="sub-new"></a><span data-ttu-id="49c3f-114">Sub New</span><span class="sxs-lookup"><span data-stu-id="49c3f-114">Sub New</span></span>

<span data-ttu-id="49c3f-115">创建类时，`Sub New` 构造函数仅可运行一次。</span><span class="sxs-lookup"><span data-stu-id="49c3f-115">The `Sub New` constructor can run only once when a class is created.</span></span> <span data-ttu-id="49c3f-116">调用此函数的位置只能是相同类或派生类的另一个构造函数的代码的第一行。</span><span class="sxs-lookup"><span data-stu-id="49c3f-116">It cannot be called explicitly anywhere other than in the first line of code of another constructor from either the same class or from a derived class.</span></span> <span data-ttu-id="49c3f-117">此外，`Sub New` 方法中的代码始终在类中任何其他代码之前运行。</span><span class="sxs-lookup"><span data-stu-id="49c3f-117">Furthermore, the code in the `Sub New` method always runs before any other code in a class.</span></span> <span data-ttu-id="49c3f-118">`Sub New`如果未显式定义类的过程，则 Visual Basic 在运行时隐式创建构造函数 `Sub New` 。</span><span class="sxs-lookup"><span data-stu-id="49c3f-118">Visual Basic implicitly creates a `Sub New` constructor at run time if you do not explicitly define a `Sub New` procedure for a class.</span></span>

<span data-ttu-id="49c3f-119">若要创建类的构造函数，请在类定义中的任何位置创建一个名为 `Sub New` 的过程。</span><span class="sxs-lookup"><span data-stu-id="49c3f-119">To create a constructor for a class, create a procedure named `Sub New` anywhere in the class definition.</span></span> <span data-ttu-id="49c3f-120">若要创建参数化构造函数，请按指定任何其他过程的参数的方式，将参数名称和数据类型指定为 `Sub New`，如下面代码所示：</span><span class="sxs-lookup"><span data-stu-id="49c3f-120">To create a parameterized constructor, specify the names and data types of arguments to `Sub New` just as you would specify arguments for any other procedure, as in the following code:</span></span>

[!code-vb[VbVbalrOOP#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#42)]

<span data-ttu-id="49c3f-121">构造函数常常重载，如下面代码所示：</span><span class="sxs-lookup"><span data-stu-id="49c3f-121">Constructors are frequently overloaded, as in the following code:</span></span>

[!code-vb[VbVbalrOOP#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/WhidbeyStuff.vb#116)]

<span data-ttu-id="49c3f-122">定义派生自另一个类的类时，构造函数的首行必须是对基类的构造函数的调用，除非此基类具有一个无参数且可访问的构造函数。</span><span class="sxs-lookup"><span data-stu-id="49c3f-122">When you define a class derived from another class, the first line of a constructor must be a call to the constructor of the base class, unless the base class has an accessible constructor that takes no parameters.</span></span> <span data-ttu-id="49c3f-123">例如，对包含以上构造函数的基类的调用将为 `MyBase.New(s)`。</span><span class="sxs-lookup"><span data-stu-id="49c3f-123">A call to the base class that contains the above constructor, for example, would be `MyBase.New(s)`.</span></span> <span data-ttu-id="49c3f-124">否则， `MyBase.New` 是可选的，Visual Basic 运行时将隐式调用它。</span><span class="sxs-lookup"><span data-stu-id="49c3f-124">Otherwise, `MyBase.New` is optional, and the Visual Basic runtime calls it implicitly.</span></span>

<span data-ttu-id="49c3f-125">编写了用于调用父对象构造函数的代码之后，你可以将任何附加初始化代码添加到 `Sub New` 过程。</span><span class="sxs-lookup"><span data-stu-id="49c3f-125">After you write the code to call the parent object's constructor, you can add any additional initialization code to the `Sub New` procedure.</span></span> <span data-ttu-id="49c3f-126">`Sub New` 在作为参数化构造函数调用时可接受自变量。</span><span class="sxs-lookup"><span data-stu-id="49c3f-126">`Sub New` can accept arguments when called as a parameterized constructor.</span></span> <span data-ttu-id="49c3f-127">这些参数是从调用构造函数的过程（例如，`Dim AnObject As New ThisClass(X)`）中传递的。</span><span class="sxs-lookup"><span data-stu-id="49c3f-127">These parameters are passed from the procedure calling the constructor, for example, `Dim AnObject As New ThisClass(X)`.</span></span>

### <a name="sub-finalize"></a><span data-ttu-id="49c3f-128">Sub Finalize</span><span class="sxs-lookup"><span data-stu-id="49c3f-128">Sub Finalize</span></span>

<span data-ttu-id="49c3f-129">释放对象之前，CLR 为定义 `Finalize` 过程的对象自动调用 `Sub Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="49c3f-129">Before releasing objects, the CLR automatically calls the `Finalize` method for objects that define a `Sub Finalize` procedure.</span></span> <span data-ttu-id="49c3f-130">`Finalize` 方法可包含恰在销毁对象之前需执行的代码，如关闭文件并保存状态消息的代码。</span><span class="sxs-lookup"><span data-stu-id="49c3f-130">The `Finalize` method can contain code that needs to execute just before an object is destroyed, such as code for closing files and saving state information.</span></span> <span data-ttu-id="49c3f-131">执行 `Sub Finalize` 会导致性能略微下降，所以应仅在需要显式释放对象时才定义 `Sub Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="49c3f-131">There is a slight performance penalty for executing `Sub Finalize`, so you should define a `Sub Finalize` method only when you need to release objects explicitly.</span></span>

> [!NOTE]
> <span data-ttu-id="49c3f-132">CLR 中的垃圾回收器不会 (，也不能) 处置 *非托管对象*，即操作系统直接在 CLR 环境之外执行的对象。</span><span class="sxs-lookup"><span data-stu-id="49c3f-132">The garbage collector in the CLR does not (and cannot) dispose of *unmanaged objects*, objects that the operating system executes directly, outside the CLR environment.</span></span> <span data-ttu-id="49c3f-133">这是因为不同的非托管对象必须以不同的方式释放。</span><span class="sxs-lookup"><span data-stu-id="49c3f-133">This is because different unmanaged objects must be disposed of in different ways.</span></span> <span data-ttu-id="49c3f-134">此信息不与非托管对象直接关联；必须存在于此对象的相应文档。</span><span class="sxs-lookup"><span data-stu-id="49c3f-134">That information is not directly associated with the unmanaged object; it must be found in the documentation for the object.</span></span> <span data-ttu-id="49c3f-135">使用非托管对象的类必须在其 `Finalize` 方法中释放它们。</span><span class="sxs-lookup"><span data-stu-id="49c3f-135">A class that uses unmanaged objects must dispose of them in its `Finalize` method.</span></span>

<span data-ttu-id="49c3f-136">`Finalize` 析构函数是一种仅可从其所属的类或派生类中调用的受保护方法。</span><span class="sxs-lookup"><span data-stu-id="49c3f-136">The `Finalize` destructor is a protected method that can be called only from the class it belongs to, or from derived classes.</span></span> <span data-ttu-id="49c3f-137">系统在对象被销毁时自动调用 `Finalize`，所以你不应从派生类的 `Finalize` 实现的外部显式调用 `Finalize`。</span><span class="sxs-lookup"><span data-stu-id="49c3f-137">The system calls `Finalize` automatically when an object is destroyed, so you should not explicitly call `Finalize` from outside of a derived class's `Finalize` implementation.</span></span>

<span data-ttu-id="49c3f-138">与 `Class_Terminate`（对象设置为 Nothing 就立即执行）不同，在对象失去范围到 Visual Basic 调用 `Finalize` 析构函数之间通常存在延迟。</span><span class="sxs-lookup"><span data-stu-id="49c3f-138">Unlike `Class_Terminate`, which executes as soon as an object is set to nothing, there is usually a delay between when an object loses scope and when Visual Basic calls the `Finalize` destructor.</span></span> <span data-ttu-id="49c3f-139">Visual Basic .NET 允许使用第二种析构函数， <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 可以随时显式调用它来立即释放资源。</span><span class="sxs-lookup"><span data-stu-id="49c3f-139">Visual Basic .NET allows for a second kind of destructor, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>, which can be explicitly called at any time to immediately release resources.</span></span>

> [!NOTE]
> <span data-ttu-id="49c3f-140">`Finalize` 析构函数不应引发异常，因为它们不能由应用程序处理，并且可能会导致应用程序终止。</span><span class="sxs-lookup"><span data-stu-id="49c3f-140">A `Finalize` destructor should not throw exceptions, because they cannot be handled by the application and can cause the application to terminate.</span></span>

### <a name="how-new-and-finalize-methods-work-in-a-class-hierarchy"></a><span data-ttu-id="49c3f-141">New 和 Finalize 方法如何在类层级中工作</span><span class="sxs-lookup"><span data-stu-id="49c3f-141">How New and Finalize Methods Work in a Class Hierarchy</span></span>

<span data-ttu-id="49c3f-142">每当创建类的实例时，公共语言运行时 (CLR) 都会尝试执行名为 `New` 的过程（如果存在于此对象）。</span><span class="sxs-lookup"><span data-stu-id="49c3f-142">Whenever an instance of a class is created, the common language runtime (CLR) attempts to execute a procedure named `New`, if it exists in that object.</span></span> <span data-ttu-id="49c3f-143">`New` 是一种调用 `constructor` 的过程，此过程用于在执行对象中任何其他代码之前初始化新对象。</span><span class="sxs-lookup"><span data-stu-id="49c3f-143">`New` is a type of procedure called a `constructor` that is used to initialize new objects before any other code in an object executes.</span></span> <span data-ttu-id="49c3f-144">`New` 构造函数可用于打开文件、连接到数据库、初始化变量以及处理需要在使用对象前完成的所有其他任务。</span><span class="sxs-lookup"><span data-stu-id="49c3f-144">A `New` constructor can be used to open files, connect to databases, initialize variables, and take care of any other tasks that need to be done before an object can be used.</span></span>

<span data-ttu-id="49c3f-145">创建派生类的实例时，首先执行基类的 `Sub New` 构造函数，再执行派生类中的构造函数。</span><span class="sxs-lookup"><span data-stu-id="49c3f-145">When an instance of a derived class is created, the `Sub New` constructor of the base class executes first, followed by constructors in derived classes.</span></span> <span data-ttu-id="49c3f-146">之所以发生此情况，原因在于 `Sub New` 构造函数中代码的首行使用语法 `MyBase.New()` 调用类层级中直接位于其上方的类的构造函数。</span><span class="sxs-lookup"><span data-stu-id="49c3f-146">This happens because the first line of code in a `Sub New` constructor uses the syntax `MyBase.New()`to call the constructor of the class immediately above itself in the class hierarchy.</span></span> <span data-ttu-id="49c3f-147">`Sub New`然后，为类层次结构中的每个类调用构造函数，直到达到基类的构造函数。</span><span class="sxs-lookup"><span data-stu-id="49c3f-147">The `Sub New` constructor is then called for each class in the class hierarchy until the constructor for the base class is reached.</span></span> <span data-ttu-id="49c3f-148">此时，先执行基类的构造函数中的代码，再执行所有的派生类中每个构造函数内的代码，最后执行大多数派生类中的代码。</span><span class="sxs-lookup"><span data-stu-id="49c3f-148">At that point, the code in the constructor for the base class executes, followed by the code in each constructor in all derived classes and the code in the most derived classes is executed last.</span></span>

![显示类层次结构和继承的屏幕截图。](./media/object-lifetime-how-objects-are-created-and-destroyed/subnew-constructor-inheritance.gif)

<span data-ttu-id="49c3f-150">一个对象不再被需要时，CRL 在释放其内存前为该对象调用 <xref:System.Object.Finalize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="49c3f-150">When an object is no longer needed, the CLR calls the <xref:System.Object.Finalize%2A> method for that object before freeing its memory.</span></span> <span data-ttu-id="49c3f-151"><xref:System.Object.Finalize%2A> 方法被称为 `destructor`，因为它执行清理任务（如保存状态信息、关闭文件、连接到数据库）以及必须在释放对象前完成的其他任务。</span><span class="sxs-lookup"><span data-stu-id="49c3f-151">The <xref:System.Object.Finalize%2A> method is called a `destructor` because it performs cleanup tasks, such as saving state information, closing files and connections to databases, and other tasks that must be done before releasing the object.</span></span>

![显示 Finalize 方法析构函数的屏幕截图。](./media/object-lifetime-how-objects-are-created-and-destroyed/finalize-method-destructor.gif)

## <a name="idisposable-interface"></a><span data-ttu-id="49c3f-153">IDisposable 接口</span><span class="sxs-lookup"><span data-stu-id="49c3f-153">IDisposable Interface</span></span>

<span data-ttu-id="49c3f-154">类实例经常控制不由 CLR 托管的资源，如窗口句柄和数据库连接。</span><span class="sxs-lookup"><span data-stu-id="49c3f-154">Class instances often control resources not managed by the CLR, such as Windows handles and database connections.</span></span> <span data-ttu-id="49c3f-155">这些资源必须在类的 `Finalize` 方法中释放，使其在垃圾回收器销毁对象时释放。</span><span class="sxs-lookup"><span data-stu-id="49c3f-155">These resources must be disposed of in the `Finalize` method of the class, so that they will be released when the object is destroyed by the garbage collector.</span></span> <span data-ttu-id="49c3f-156">但是，垃圾回收器仅在 CLR 需要更多可用内存时才销毁对象。</span><span class="sxs-lookup"><span data-stu-id="49c3f-156">However, the garbage collector destroys objects only when the CLR requires more free memory.</span></span> <span data-ttu-id="49c3f-157">这意味着资源可能在对象超出范围之后很久才释放。</span><span class="sxs-lookup"><span data-stu-id="49c3f-157">This means that the resources may not be released until long after the object goes out of scope.</span></span>

<span data-ttu-id="49c3f-158">为补充垃圾回收，你的类可以在系统资源实现 <xref:System.IDisposable> 接口时提供对其进行有效管理的机制。</span><span class="sxs-lookup"><span data-stu-id="49c3f-158">To supplement garbage collection, your classes can provide a mechanism to actively manage system resources if they implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="49c3f-159"><xref:System.IDisposable> 具有一种客户端使用对象完成时应调用的方法 <xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="49c3f-159"><xref:System.IDisposable> has one method, <xref:System.IDisposable.Dispose%2A>, which clients should call when they finish using an object.</span></span> <span data-ttu-id="49c3f-160">你可以使用 <xref:System.IDisposable.Dispose%2A> 方法立即释放资源和执行关闭文件和数据库连接等任务。</span><span class="sxs-lookup"><span data-stu-id="49c3f-160">You can use the <xref:System.IDisposable.Dispose%2A> method to immediately release resources and perform tasks such as closing files and database connections.</span></span> <span data-ttu-id="49c3f-161">与 `Finalize` 析构函数不同，<xref:System.IDisposable.Dispose%2A> 方法不能自动调用。</span><span class="sxs-lookup"><span data-stu-id="49c3f-161">Unlike the `Finalize` destructor, the <xref:System.IDisposable.Dispose%2A> method is not called automatically.</span></span> <span data-ttu-id="49c3f-162">要立即释放资源时，类的客户端必须显式调用 <xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="49c3f-162">Clients of a class must explicitly call <xref:System.IDisposable.Dispose%2A> when you want to immediately release resources.</span></span>

### <a name="implementing-idisposable"></a><span data-ttu-id="49c3f-163">正在实现 IDisposable</span><span class="sxs-lookup"><span data-stu-id="49c3f-163">Implementing IDisposable</span></span>

<span data-ttu-id="49c3f-164">实现 <xref:System.IDisposable> 接口的类应该包含代码的以下部分：</span><span class="sxs-lookup"><span data-stu-id="49c3f-164">A class that implements the <xref:System.IDisposable> interface should include these sections of code:</span></span>

- <span data-ttu-id="49c3f-165">用于跟踪对象是否已释放的字段：</span><span class="sxs-lookup"><span data-stu-id="49c3f-165">A field for keeping track of whether the object has been disposed:</span></span>

  ```vb
  Protected disposed As Boolean = False
  ```

- <span data-ttu-id="49c3f-166">可释放类的资源的 <xref:System.IDisposable.Dispose%2A> 的重载。</span><span class="sxs-lookup"><span data-stu-id="49c3f-166">An overload of the <xref:System.IDisposable.Dispose%2A> that frees the class's resources.</span></span> <span data-ttu-id="49c3f-167">应通过基类的 <xref:System.IDisposable.Dispose%2A> 和 `Finalize` 方法调用此方法：</span><span class="sxs-lookup"><span data-stu-id="49c3f-167">This method should be called by the <xref:System.IDisposable.Dispose%2A> and `Finalize` methods of the base class:</span></span>

  ```vb
  Protected Overridable Sub Dispose(ByVal disposing As Boolean)
      If Not Me.disposed Then
          If disposing Then
              ' Insert code to free managed resources.
          End If
          ' Insert code to free unmanaged resources.
      End If
      Me.disposed = True
  End Sub
  ```

- <span data-ttu-id="49c3f-168">仅包含以下代码的 <xref:System.IDisposable.Dispose%2A> 的实现：</span><span class="sxs-lookup"><span data-stu-id="49c3f-168">An implementation of <xref:System.IDisposable.Dispose%2A> that contains only the following code:</span></span>

  ```vb
  Public Sub Dispose() Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
  End Sub
  ```

- <span data-ttu-id="49c3f-169">仅包含以下代码的 `Finalize` 方法的重写：</span><span class="sxs-lookup"><span data-stu-id="49c3f-169">An override of the `Finalize` method that contains only the following code:</span></span>

  ```vb
  Protected Overrides Sub Finalize()
      Dispose(False)
      MyBase.Finalize()
  End Sub
  ```

### <a name="deriving-from-a-class-that-implements-idisposable"></a><span data-ttu-id="49c3f-170">派生自实现 IDisposable 的类</span><span class="sxs-lookup"><span data-stu-id="49c3f-170">Deriving from a Class that Implements IDisposable</span></span>

<span data-ttu-id="49c3f-171">从实现 <xref:System.IDisposable> 接口的基类派生出的类无需重写任何基方法，除非它使用需要释放的附加资源。</span><span class="sxs-lookup"><span data-stu-id="49c3f-171">A class that derives from a base class that implements the <xref:System.IDisposable> interface does not need to override any of the base methods unless it uses additional resources that need to be disposed.</span></span> <span data-ttu-id="49c3f-172">在这种情况下，派生类应重写基类的 `Dispose(disposing)` 方法以释放派生类的资源。</span><span class="sxs-lookup"><span data-stu-id="49c3f-172">In that situation, the derived class should override the base class's `Dispose(disposing)` method to dispose of the derived class's resources.</span></span> <span data-ttu-id="49c3f-173">此重写必须调用基类的 `Dispose(disposing)` 方法。</span><span class="sxs-lookup"><span data-stu-id="49c3f-173">This override must call the base class's `Dispose(disposing)` method.</span></span>

```vb
Protected Overrides Sub Dispose(ByVal disposing As Boolean)
    If Not Me.disposed Then
        If disposing Then
            ' Insert code to free managed resources.
        End If
        ' Insert code to free unmanaged resources.
    End If
    MyBase.Dispose(disposing)
End Sub
```

<span data-ttu-id="49c3f-174">派生类不应该重写基类的 <xref:System.IDisposable.Dispose%2A> 和 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="49c3f-174">A derived class should not override the base class's <xref:System.IDisposable.Dispose%2A> and `Finalize` methods.</span></span> <span data-ttu-id="49c3f-175">从派生类的实例中调用这些方法时，这些方法的基类的实现将调用 `Dispose(disposing)` 方法的派生类的重写。</span><span class="sxs-lookup"><span data-stu-id="49c3f-175">When those methods are called from an instance of the derived class, the base class's implementation of those methods call the derived class's override of the `Dispose(disposing)` method.</span></span>

## <a name="garbage-collection-and-the-finalize-destructor"></a><span data-ttu-id="49c3f-176">垃圾回收和 Finalize 析构函数</span><span class="sxs-lookup"><span data-stu-id="49c3f-176">Garbage Collection and the Finalize Destructor</span></span>

<span data-ttu-id="49c3f-177">.NET Framework 使用 *引用跟踪垃圾回收* 系统定期释放未使用的资源。</span><span class="sxs-lookup"><span data-stu-id="49c3f-177">The .NET Framework uses the *reference-tracing garbage collection* system to periodically release unused resources.</span></span> <span data-ttu-id="49c3f-178">Visual Basic 6.0 及更早版本使用称为 " *引用计数* " 的不同系统来管理资源。</span><span class="sxs-lookup"><span data-stu-id="49c3f-178">Visual Basic 6.0 and earlier versions used a different system called *reference counting* to manage resources.</span></span> <span data-ttu-id="49c3f-179">尽管两个系统自动执行同一功能，但还是有一些重要的区别。</span><span class="sxs-lookup"><span data-stu-id="49c3f-179">Although both systems perform the same function automatically, there are a few important differences.</span></span>

<span data-ttu-id="49c3f-180">当系统确定不再需要这些对象时，CLR 将定期对其进行销毁。</span><span class="sxs-lookup"><span data-stu-id="49c3f-180">The CLR periodically destroys objects when the system determines that such objects are no longer needed.</span></span> <span data-ttu-id="49c3f-181">系统资源短缺时对象释放得更快，而非短缺时释放频率更低。</span><span class="sxs-lookup"><span data-stu-id="49c3f-181">Objects are released more quickly when system resources are in short supply, and less frequently otherwise.</span></span> <span data-ttu-id="49c3f-182">对象失去范围到 CLR 释放它之间出现延迟，这意味着与 Visual Basic 6.0 及更低版本不同，你无法确定销毁对象的确切时间。</span><span class="sxs-lookup"><span data-stu-id="49c3f-182">The delay between when an object loses scope and when the CLR releases it means that, unlike with objects in Visual Basic 6.0 and earlier versions, you cannot determine exactly when the object will be destroyed.</span></span> <span data-ttu-id="49c3f-183">在这种情况下，认为对象具有 *不确定性的生存期*。</span><span class="sxs-lookup"><span data-stu-id="49c3f-183">In such a situation, objects are said to have *non-deterministic lifetime*.</span></span> <span data-ttu-id="49c3f-184">在大多数情况下，非确定性生存期不会更改你编写应用程序的方式，只要你记住`Finalize` 析构函数可能不会在对象失去范围时立即执行。</span><span class="sxs-lookup"><span data-stu-id="49c3f-184">In most cases, non-deterministic lifetime does not change how you write applications, as long as you remember that the `Finalize` destructor may not immediately execute when an object loses scope.</span></span>

<span data-ttu-id="49c3f-185">垃圾回收系统间的另一个区别涉及到 `Nothing` 的使用。</span><span class="sxs-lookup"><span data-stu-id="49c3f-185">Another difference between the garbage-collection systems involves the use of `Nothing`.</span></span> <span data-ttu-id="49c3f-186">为了在 Visual Basic 6.0 及更低版本中利用引用计数，程序员有时将 `Nothing` 分配到对象变量以释放这些变量持有的引用。</span><span class="sxs-lookup"><span data-stu-id="49c3f-186">To take advantage of reference counting in Visual Basic 6.0 and earlier versions, programmers sometimes assigned `Nothing` to object variables to release the references those variables held.</span></span> <span data-ttu-id="49c3f-187">如果变量持有对对象的最后引用，则会立即释放该对象的资源。</span><span class="sxs-lookup"><span data-stu-id="49c3f-187">If the variable held the last reference to the object, the object's resources were released immediately.</span></span> <span data-ttu-id="49c3f-188">在 Visual Basic 的更高版本中，虽然可能存在此过程仍有用的情况，但执行此过程不会使引用的对象立即释放其资源。</span><span class="sxs-lookup"><span data-stu-id="49c3f-188">In later versions of Visual Basic, while there may be cases in which this procedure is still valuable, performing it never causes the referenced object to release its resources immediately.</span></span> <span data-ttu-id="49c3f-189">若要立即释放资源，请使用对象的 <xref:System.IDisposable.Dispose%2A> 方法（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="49c3f-189">To release resources immediately, use the object's <xref:System.IDisposable.Dispose%2A> method, if available.</span></span> <span data-ttu-id="49c3f-190">只有当变量的生存期相对于垃圾回收器用于检测孤立对象的时间来说很长时，你才应该将变量设置为 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="49c3f-190">The only time you should set a variable to `Nothing` is when its lifetime is long relative to the time the garbage collector takes to detect orphaned objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="49c3f-191">请参阅</span><span class="sxs-lookup"><span data-stu-id="49c3f-191">See also</span></span>

- <xref:System.IDisposable.Dispose%2A>
- <span data-ttu-id="49c3f-192">[组件的初始化和终止](/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="49c3f-192">[Initialization and Termination of Components](/previous-versions/visualstudio/visual-studio-2013/ws9dc6t6(v=vs.120))</span></span>
- [<span data-ttu-id="49c3f-193">新建操作员</span><span class="sxs-lookup"><span data-stu-id="49c3f-193">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- <span data-ttu-id="49c3f-194">[清理未托管资源](../../../../standard/garbage-collection/unmanaged.md)（清理未托管资源）</span><span class="sxs-lookup"><span data-stu-id="49c3f-194">[Cleaning Up Unmanaged Resources](../../../../standard/garbage-collection/unmanaged.md)</span></span>
- [<span data-ttu-id="49c3f-195">无</span><span class="sxs-lookup"><span data-stu-id="49c3f-195">Nothing</span></span>](../../../language-reference/nothing.md)
