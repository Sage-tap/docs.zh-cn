---
description: 了解详细信息：如何：用 x.509 证书对 XML 元素进行加密
title: 如何：使用 X.509 证书加密 XML 元素
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], X.509 certificates
- cryptography [.NET], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: f815d253b15823070e074c5d922d3024da602a0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685096"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="e24cd-103">如何：使用 X.509 证书加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="e24cd-103">How to: Encrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="e24cd-104">可以使用 <xref:System.Security.Cryptography.Xml> 命名空间中的类加密 XML 文档内的元素。</span><span class="sxs-lookup"><span data-stu-id="e24cd-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="e24cd-105">XML 加密是交换或存储加密的 XML 数据的一种标准方式，使用后就无需担心数据被轻易读取。</span><span class="sxs-lookup"><span data-stu-id="e24cd-105">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="e24cd-106">有关 XML 加密标准的详细信息，请参阅位于万维网联合会 (W3C) 规范 for XML Encryption <https://www.w3.org/TR/xmldsig-core/> 。</span><span class="sxs-lookup"><span data-stu-id="e24cd-106">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="e24cd-107">可以使用 XML 加密将任何 XML 元素或文档替换为包含加密 XML 数据的 <`EncryptedData`> 元素。</span><span class="sxs-lookup"><span data-stu-id="e24cd-107">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="e24cd-108"><`EncryptedData`> 元素可以包含一些子元素来收入关于加密期间使用的密钥和进程的信息。</span><span class="sxs-lookup"><span data-stu-id="e24cd-108">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="e24cd-109">XML 加密允许文档包含多个加密元素，并允许对一个元素进行多次加密。</span><span class="sxs-lookup"><span data-stu-id="e24cd-109">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="e24cd-110">此过程中的代码示例演示了如何创建一个 <`EncryptedData`> 元素和几个其他子元素，以便以后在解密过程中使用。</span><span class="sxs-lookup"><span data-stu-id="e24cd-110">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
<span data-ttu-id="e24cd-111">此示例使用两个密钥对 XML 元素进行加密。</span><span class="sxs-lookup"><span data-stu-id="e24cd-111">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="e24cd-112">该示例以编程方式检索证书，并使用它通过方法对 XML 元素进行加密 <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e24cd-112">The example programmatically retrieves a certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="e24cd-113">在内部，<xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> 方法创建一个单独的会话密钥，并将其用于加密 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="e24cd-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="e24cd-114">此方法对会话密钥进行加密，并将它与加密的 XML 一起保存在一个新的 <`EncryptedData`> 元素中。</span><span class="sxs-lookup"><span data-stu-id="e24cd-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  

<span data-ttu-id="e24cd-115">若要对 XML 元素进行解密，请调用 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法，该方法会自动从存储中检索 x.509 证书并执行必要的解密。</span><span class="sxs-lookup"><span data-stu-id="e24cd-115">To decrypt the XML element, call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="e24cd-116">有关如何对按照此过程加密的 XML 元素进行解密的详细信息，请参阅[如何：用 X.509 证书对 XML 元素进行解密](how-to-decrypt-xml-elements-with-x-509-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="e24cd-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
<span data-ttu-id="e24cd-117">此示例适用于以下情况：多个应用程序需要共享加密数据，或应用程序需要保存它各次运行之间的加密数据。</span><span class="sxs-lookup"><span data-stu-id="e24cd-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="e24cd-118">使用 X.509 证书对 XML 元素进行加密</span><span class="sxs-lookup"><span data-stu-id="e24cd-118">To encrypt an XML element with an X.509 certificate</span></span>  

<span data-ttu-id="e24cd-119">若要运行此示例，需要创建测试证书，并将其保存到证书存储中。</span><span class="sxs-lookup"><span data-stu-id="e24cd-119">To run this example, you need to create a test certificate and save it in a certificate store.</span></span> <span data-ttu-id="e24cd-120">仅为 Windows 证书创建工具提供该任务的说明 [ ( # A0) ](/windows/desktop/SecCrypto/makecert)。</span><span class="sxs-lookup"><span data-stu-id="e24cd-120">Instructions for that task are provided only for the Windows [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span></span>

1. <span data-ttu-id="e24cd-121">使用 [Makecert.exe](/windows/desktop/SecCrypto/makecert) 生成 x.509 证书，并将其置于本地用户存储中。</span><span class="sxs-lookup"><span data-stu-id="e24cd-121">Use [Makecert.exe](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="e24cd-122">必须生成一个交换密钥，且该密钥必须可导出。</span><span class="sxs-lookup"><span data-stu-id="e24cd-122">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="e24cd-123">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e24cd-123">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="e24cd-124">创建 <xref:System.Security.Cryptography.X509Certificates.X509Store> 对象，并进行初始化，以便打开当前用户存储区。</span><span class="sxs-lookup"><span data-stu-id="e24cd-124">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="e24cd-125">在只读模式下打开存储区。</span><span class="sxs-lookup"><span data-stu-id="e24cd-125">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="e24cd-126">使用存储区中的所有证书初始化 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection>。</span><span class="sxs-lookup"><span data-stu-id="e24cd-126">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="e24cd-127">枚举存储区中的证书，找到具有相应名称的证书。</span><span class="sxs-lookup"><span data-stu-id="e24cd-127">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="e24cd-128">在此示例中，证书名为 `"CN=XML_ENC_TEST_CERT"`。</span><span class="sxs-lookup"><span data-stu-id="e24cd-128">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="e24cd-129">找到该证书后，关闭存储区。</span><span class="sxs-lookup"><span data-stu-id="e24cd-129">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="e24cd-130">通过从磁盘加载 XML 文件来创建 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="e24cd-130">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="e24cd-131"><xref:System.Xml.XmlDocument> 对象包含要加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="e24cd-131">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="e24cd-132">在 <xref:System.Xml.XmlDocument> 对象中查找指定元素，并创建一个新的 <xref:System.Xml.XmlElement> 对象来表示想要加密的元素。</span><span class="sxs-lookup"><span data-stu-id="e24cd-132">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="e24cd-133">在此示例中，加密了 `"creditcard"` 元素。</span><span class="sxs-lookup"><span data-stu-id="e24cd-133">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="e24cd-134">创建 <xref:System.Security.Cryptography.Xml.EncryptedXml> 类的新实例，并通过它使用 X.509 证书对指定元素进行加密。</span><span class="sxs-lookup"><span data-stu-id="e24cd-134">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="e24cd-135"><xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> 方法以 <xref:System.Security.Cryptography.Xml.EncryptedData> 对象的形式返回加密元素。</span><span class="sxs-lookup"><span data-stu-id="e24cd-135">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="e24cd-136">将原始 <xref:System.Xml.XmlDocument> 对象中的元素替换为 <xref:System.Security.Cryptography.Xml.EncryptedData> 元素。</span><span class="sxs-lookup"><span data-stu-id="e24cd-136">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="e24cd-137">保存 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="e24cd-137">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="e24cd-138">示例</span><span class="sxs-lookup"><span data-stu-id="e24cd-138">Example</span></span>  

 <span data-ttu-id="e24cd-139">此示例假定名为 `"test.xml"` 的文件与已编译程序存在于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="e24cd-139">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="e24cd-140">它还假定 `"test.xml"` 包含 `"creditcard"` 元素。</span><span class="sxs-lookup"><span data-stu-id="e24cd-140">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="e24cd-141">可以将以下 XML 放在名为 `test.xml` 的文件，并将其用于以下示例。</span><span class="sxs-lookup"><span data-stu-id="e24cd-141">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e24cd-142">编译代码</span><span class="sxs-lookup"><span data-stu-id="e24cd-142">Compiling the Code</span></span>  
  
- <span data-ttu-id="e24cd-143">在面向 .NET Framework 的项目中，包含对的引用 `System.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="e24cd-143">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="e24cd-144">在面向 .NET Core 或 .NET 5 的项目中，安装 NuGet 包 [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。</span><span class="sxs-lookup"><span data-stu-id="e24cd-144">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="e24cd-145">包括以下命名空间：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="e24cd-145">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="e24cd-146">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="e24cd-146">.NET Security</span></span>
  
<span data-ttu-id="e24cd-147">此示例中使用的 X.509 证书仅用于测试目的。</span><span class="sxs-lookup"><span data-stu-id="e24cd-147">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="e24cd-148">应用程序应使用由受信任的证书颁发机构生成的 x.509 证书。</span><span class="sxs-lookup"><span data-stu-id="e24cd-148">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e24cd-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="e24cd-149">See also</span></span>

- [<span data-ttu-id="e24cd-150">加密模型</span><span class="sxs-lookup"><span data-stu-id="e24cd-150">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="e24cd-151">加密服务</span><span class="sxs-lookup"><span data-stu-id="e24cd-151">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="e24cd-152">跨平台加密</span><span class="sxs-lookup"><span data-stu-id="e24cd-152">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="e24cd-153">如何：使用 X.509 证书解密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="e24cd-153">How to: Decrypt XML Elements with X.509 Certificates</span></span>](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="e24cd-154">ASP.NET Core 数据保护</span><span class="sxs-lookup"><span data-stu-id="e24cd-154">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
