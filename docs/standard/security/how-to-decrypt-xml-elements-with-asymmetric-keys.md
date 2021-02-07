---
description: 了解详细信息：如何：用非对称密钥对 XML 元素进行解密
title: 如何：用非对称密钥对 XML 元素进行解密
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: bd3bd142aa5800efa83bc20a4b1af6d5bc61eba2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675567"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="72830-103">如何：用非对称密钥对 XML 元素进行解密</span><span class="sxs-lookup"><span data-stu-id="72830-103">How to: Decrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="72830-104">可以使用 <xref:System.Security.Cryptography.Xml> 命名空间中的类对 XML 文档内的元素进行加密和解密。</span><span class="sxs-lookup"><span data-stu-id="72830-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="72830-105">XML 加密是交换或存储加密的 XML 数据的一种标准方式，使用后就无需担心数据被轻易读取。</span><span class="sxs-lookup"><span data-stu-id="72830-105">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="72830-106">有关 XML 加密标准的详细信息，请参阅万维网联合会 (W3C) 推荐 [XML 签名语法和处理](https://www.w3.org/TR/xmldsig-core/)。</span><span class="sxs-lookup"><span data-stu-id="72830-106">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  

> [!NOTE]
> <span data-ttu-id="72830-107">本文中的代码适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="72830-107">The code in this article applies to Windows.</span></span>

<span data-ttu-id="72830-108">此过程中的示例对使用 [如何：用非对称密钥加密 XML 元素](how-to-encrypt-xml-elements-with-asymmetric-keys.md)中所述的方法进行加密的 XML 元素进行解密。</span><span class="sxs-lookup"><span data-stu-id="72830-108">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="72830-109">它将查找 <`EncryptedData`> 元素，对元素进行解密，然后将元素替换为原始纯文本 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="72830-109">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="72830-110">此示例使用两个密钥对 XML 元素进行解密。</span><span class="sxs-lookup"><span data-stu-id="72830-110">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="72830-111">它从密钥容器中检索以前生成的 RSA 私钥，然后使用 RSA 密钥对存储在 <> 元素的 <> 元素中的会话密钥进行解密 `EncryptedKey` `EncryptedData` 。</span><span class="sxs-lookup"><span data-stu-id="72830-111">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="72830-112">然后此示例使用会话密钥对 XML 元素进行解密。</span><span class="sxs-lookup"><span data-stu-id="72830-112">The example then uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="72830-113">此示例适用于以下情况：多个应用程序必须共享加密数据，或应用程序必须保存其每次运行之间的加密数据。</span><span class="sxs-lookup"><span data-stu-id="72830-113">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="72830-114">用非对称密钥对 XML 元素进行解密</span><span class="sxs-lookup"><span data-stu-id="72830-114">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="72830-115">创建 <xref:System.Security.Cryptography.CspParameters> 对象，并指定密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="72830-115">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="72830-116">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 对象从容器中检索以前生成的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="72830-116">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="72830-117">当将 <xref:System.Security.Cryptography.CspParameters> 对象传递到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 构造函数中时，将自动从密钥容器中检索到密钥。</span><span class="sxs-lookup"><span data-stu-id="72830-117">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="72830-118">创建新 <xref:System.Security.Cryptography.Xml.EncryptedXml> 对象以对文档进行解密。</span><span class="sxs-lookup"><span data-stu-id="72830-118">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="72830-119">添加一个密钥/名称映射，以便 RSA 密钥与应该进行解密的文档中的元素相关联。</span><span class="sxs-lookup"><span data-stu-id="72830-119">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="72830-120">必须使用与加密文档时所用密钥名称相同的名称。</span><span class="sxs-lookup"><span data-stu-id="72830-120">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="72830-121">请注意，此名称独立于用来标识在步骤 1 中指定的密钥容器中的密钥名称。</span><span class="sxs-lookup"><span data-stu-id="72830-121">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="72830-122">调用 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法以解密 `EncryptedData`> 元素的 <。</span><span class="sxs-lookup"><span data-stu-id="72830-122">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="72830-123">此方法使用 RSA 密钥来解密会话密钥，并自动使用会话密钥来解密 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="72830-123">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="72830-124">它还会自动将 <`EncryptedData`> 元素替换为原始纯文本。</span><span class="sxs-lookup"><span data-stu-id="72830-124">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="72830-125">保存 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="72830-125">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="72830-126">示例</span><span class="sxs-lookup"><span data-stu-id="72830-126">Example</span></span>

<span data-ttu-id="72830-127">此示例假定名为 `test.xml` 的文件与已编译程序存在于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="72830-127">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="72830-128">它还假定 `test.xml` 包含使用 [如何：使用非对称密钥对 XML 元素进行加密](how-to-encrypt-xml-elements-with-asymmetric-keys.md)中描述的方法进行加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="72830-128">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72830-129">编译代码</span><span class="sxs-lookup"><span data-stu-id="72830-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="72830-130">在面向 .NET Framework 的项目中，包含对的引用 `System.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="72830-130">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="72830-131">在面向 .NET Core 或 .NET 5 的项目中，安装 NuGet 包 [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。</span><span class="sxs-lookup"><span data-stu-id="72830-131">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="72830-132">包括以下命名空间：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="72830-132">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="72830-133">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="72830-133">.NET Security</span></span>  

<span data-ttu-id="72830-134">永远不要以纯文本形式存储对称加密密钥，也不要以纯文本形式在计算机之间传输对称密钥。</span><span class="sxs-lookup"><span data-stu-id="72830-134">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="72830-135">此外，绝不存储或传输纯文本形式的非对称密钥的私钥。</span><span class="sxs-lookup"><span data-stu-id="72830-135">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="72830-136">有关对称和非对称加密密钥的详细信息，请参阅 [生成加密和解密密钥](generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="72830-136">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="72830-137">绝不将密钥直接嵌入源代码。</span><span class="sxs-lookup"><span data-stu-id="72830-137">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="72830-138">通过使用 [Ildasm.exe (IL 拆装器) ](../../framework/tools/ildasm-exe-il-disassembler.md) 或在文本编辑器（如记事本）中打开程序集，可以轻松地从程序集中读取嵌入的密钥。</span><span class="sxs-lookup"><span data-stu-id="72830-138">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="72830-139">当你使用加密密钥执行操作后，通过将每个字节设置为零或通过调用托管加密类的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法来将它从内存中清除。</span><span class="sxs-lookup"><span data-stu-id="72830-139">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="72830-140">加密密钥有时可从内存由调试器读取，或从硬盘读取（如果内存位置分页到磁盘）。</span><span class="sxs-lookup"><span data-stu-id="72830-140">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72830-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="72830-141">See also</span></span>

- [<span data-ttu-id="72830-142">加密模型</span><span class="sxs-lookup"><span data-stu-id="72830-142">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="72830-143">加密服务</span><span class="sxs-lookup"><span data-stu-id="72830-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="72830-144">跨平台加密</span><span class="sxs-lookup"><span data-stu-id="72830-144">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="72830-145">如何：使用非对称密钥加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="72830-145">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="72830-146">ASP.NET Core 数据保护</span><span class="sxs-lookup"><span data-stu-id="72830-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
