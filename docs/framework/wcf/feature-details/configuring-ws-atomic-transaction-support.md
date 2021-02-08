---
description: 了解详细信息：配置 WS-Atomic Transaction 支持
title: 配置 WS-Atomic 事务支持
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: c9b732bd0d6b6aa8cb1cf04803ae302a00348987
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780539"
---
# <a name="configure-ws-atomic-transaction-support"></a><span data-ttu-id="cac95-103">配置 WS-Atomic Transaction 支持</span><span class="sxs-lookup"><span data-stu-id="cac95-103">Configure WS-Atomic Transaction support</span></span>

<span data-ttu-id="cac95-104">本主题介绍如何通过 WS-AT 配置实用工具来配置 WS-AtomicTransaction (WS-AT) 支持。</span><span class="sxs-lookup"><span data-stu-id="cac95-104">This topic describes how you can configure WS-AtomicTransaction (WS-AT) support by using the WS-AT Configuration Utility.</span></span>

## <a name="use-the-ws-at-configuration-utility"></a><span data-ttu-id="cac95-105">使用 WS-AT 配置实用工具</span><span class="sxs-lookup"><span data-stu-id="cac95-105">Use the WS-AT configuration utility</span></span>

<span data-ttu-id="cac95-106">WS-AT 配置实用工具 (wsatConfig.exe) 用于配置 WS-AT 设置。</span><span class="sxs-lookup"><span data-stu-id="cac95-106">The WS-AT Configuration Utility (wsatConfig.exe) is used to configure WS-AT settings.</span></span> <span data-ttu-id="cac95-107">为了启用 WS-AT 协议服务，必须使用该配置实用工具为 WS-AT 配置 HTTPS 端口，将 X.509 证书绑定到该 HTTPS 端口，并通过指定证书主题名称或指纹来配置授权的合作伙伴证书。</span><span class="sxs-lookup"><span data-stu-id="cac95-107">In order to enable the WS-AT protocol service, you must use the configuration utility to configure the HTTPS port for WS-AT, bind an X.509 certificate to the HTTPS port, and configure authorized partner certificates by specifying certificate subject names or thumbprints.</span></span> <span data-ttu-id="cac95-108">通过该配置实用工具，还可以选择跟踪模式，设置默认的外发事务超时和最大传入事务超时。</span><span class="sxs-lookup"><span data-stu-id="cac95-108">The configuration utility also allows you to select the tracing mode and set default outgoing and maximum incoming transaction timeouts.</span></span>

<span data-ttu-id="cac95-109">使用“组件服务”管理控制台中的 Microsoft 管理控制台 (MMC) 属性页管理单元，或者在命令行窗口中，都可访问此工具的功能。</span><span class="sxs-lookup"><span data-stu-id="cac95-109">You can access this tool's functionality by using a Microsoft Management Console (MMC) property page snap-in in the Component Services management console, or from a command-line window.</span></span> <span data-ttu-id="cac95-110">通过命令行窗口配置本地计算机上的 WS-AT 支持；使用 MMC 管理单元配置本地和远程计算机上的设置。</span><span class="sxs-lookup"><span data-stu-id="cac95-110">Configure WS-AT support on the local machine through the command-line window; configure settings on both local and remote machines by using the MMC snap-in.</span></span>

<span data-ttu-id="cac95-111">在 Windows SDK 安装位置“%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation”中，可访问命令行窗口。</span><span class="sxs-lookup"><span data-stu-id="cac95-111">The command-line window can be accessed in the Windows SDK installation location "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".</span></span>

<span data-ttu-id="cac95-112">有关命令行工具的详细信息，请参阅 [Ws-atomictransaction 配置实用工具 ( # A0) ](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="cac95-112">For more information about the command-line tool, see [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md).</span></span>

<span data-ttu-id="cac95-113">如果运行的是 Windows XP 或 Windows Server 2003，则可以通过导航到 **"控制面板"/"管理工具"/"组件服务**"，右键单击 **我的电脑**，然后选择 " **属性**" 来访问 MMC 管理单元。</span><span class="sxs-lookup"><span data-stu-id="cac95-113">If you are running Windows XP or Windows Server 2003, you can access the MMC snap-in by navigating to **Control Panel/Administrative Tools/Component Services**, right-clicking **My Computer**, and selecting **Properties**.</span></span> <span data-ttu-id="cac95-114">Microsoft 分布式事务处理协调器 (MSDTC) 也可以在这个位置配置。</span><span class="sxs-lookup"><span data-stu-id="cac95-114">This is the same location where you can configure the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="cac95-115">可用于配置的选项分组在 " **ws-at** " 选项卡下。如果运行的是 Windows Vista 或 Windows Server 2008，则可以通过单击 " **开始** " 按钮，并 `dcomcnfg.exe` 在 " **搜索** " 框中输入来找到 MMC 管理单元。</span><span class="sxs-lookup"><span data-stu-id="cac95-115">Options available for configuration are grouped under the **WS-AT** tab. If you are running Windows Vista or Windows Server 2008, the MMC snap-in can be found by clicking the **Start** button, and entering `dcomcnfg.exe` in the **Search** box.</span></span> <span data-ttu-id="cac95-116">打开 MMC 时，导航到 "我的 **Computer\Distributed Transaction 处理协调器 DTC** " 节点，右键单击并选择 " **属性**"。</span><span class="sxs-lookup"><span data-stu-id="cac95-116">When the MMC is opened, navigate to the **My Computer\Distributed Transaction Coordinator\Local DTC** node, right click and select **Properties**.</span></span> <span data-ttu-id="cac95-117">可用于配置的选项分组在 " **ws-at** " 选项卡下。</span><span class="sxs-lookup"><span data-stu-id="cac95-117">Options available for configuration are grouped under the **WS-AT** tab.</span></span>

<span data-ttu-id="cac95-118">有关管理单元的详细信息，请参阅 [Ws-atomictransaction 配置 MMC 管理单元](../ws-atomictransaction-configuration-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="cac95-118">For more information about the snap-in, see the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md).</span></span>

<span data-ttu-id="cac95-119">若要启用该工具的用户界面，必须首先注册 WsatUI.dll 文件，该文件位于以下路径下</span><span class="sxs-lookup"><span data-stu-id="cac95-119">To enable the tool's user interface, you must first register the WsatUI.dll file, located at the following path</span></span>

<span data-ttu-id="cac95-120">%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin</span><span class="sxs-lookup"><span data-stu-id="cac95-120">%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin</span></span>

<span data-ttu-id="cac95-121">若要注册产品，请在“命令提示”窗口中执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="cac95-121">To register the product, execute the following command from a Command Prompt window:</span></span>

`regasm.exe /codebase WsatUI.dll`

## <a name="enable-ws-at"></a><span data-ttu-id="cac95-122">启用 WS-AT</span><span class="sxs-lookup"><span data-stu-id="cac95-122">Enable WS-AT</span></span>

<span data-ttu-id="cac95-123">若要使用端口 443 和带私钥的 X.509 证书（已安装在本地机器存储区中）在 MSDTC 内启用 WS-AT 协议服务，请使用 wsatConfig.exe 工具执行以下命令。</span><span class="sxs-lookup"><span data-stu-id="cac95-123">To enable the WS-AT protocol service inside MSDTC using port 443 and an X.509 certificate with a private key that has been installed in the local machine store, use the wsatConfig.exe tool with the following command.</span></span>

`WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`

<span data-ttu-id="cac95-124">将相应的参数替换为与环境相关的值。</span><span class="sxs-lookup"><span data-stu-id="cac95-124">Substitute the respective parameters with values relevant to your environment.</span></span>

<span data-ttu-id="cac95-125">若要在 MSDTC 内禁用 WS-AT 协议服务，请使用 wsatConfig.exe 工具执行以下命令。</span><span class="sxs-lookup"><span data-stu-id="cac95-125">To disable the WS-AT protocol service inside MSDTC, use the wsatConfig.exe tool with the following command.</span></span>

`WsatConfig.exe –network:disable -restart`

## <a name="configure-trust-between-two-machines"></a><span data-ttu-id="cac95-126">在两台计算机之间配置信任</span><span class="sxs-lookup"><span data-stu-id="cac95-126">Configure trust between two machines</span></span>

<span data-ttu-id="cac95-127">WS-AT 协议服务要求管理员显式授权各个帐户参与分布式事务。</span><span class="sxs-lookup"><span data-stu-id="cac95-127">The WS-AT protocol service requires the administrator to explicitly authorize individual accounts to participate in distributed transactions.</span></span> <span data-ttu-id="cac95-128">如果您是两台计算机的管理员，可以按以下方式配置两台计算机以建立相互信任关系：在两台计算机之间交换正确的证书集，将这些证书安装到相应的证书存储区，然后使用 wsatConfig.exe 工具将每台计算机的证书添加到对方的授权参与者证书列表中。</span><span class="sxs-lookup"><span data-stu-id="cac95-128">If you are an administrator for two machines, you can configure both machines to establish a mutual trust relationship by exchanging the right set of certificates between the machines, installing them into the appropriate certificate stores, and using the wsatConfig.exe tool to add each machine's certificate to the other's list of authorized participant certificates.</span></span> <span data-ttu-id="cac95-129">若要在两台计算机之间使用 WS-AT 执行分布式事务，则必须执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="cac95-129">This step is necessary to perform distributed transactions between two machines using WS-AT.</span></span>

<span data-ttu-id="cac95-130">下面的示例概述了在两台计算机 A 和 B 之间建立信任关系的步骤。</span><span class="sxs-lookup"><span data-stu-id="cac95-130">In the following example outlines the steps to establish trust between two machines, A and B.</span></span>

### <a name="create-and-export-certificates"></a><span data-ttu-id="cac95-131">创建和导出证书</span><span class="sxs-lookup"><span data-stu-id="cac95-131">Create and export certificates</span></span>

<span data-ttu-id="cac95-132">此过程需要使用 MMC“证书”管理单元。</span><span class="sxs-lookup"><span data-stu-id="cac95-132">This procedure requires the MMC Certificates snap-in.</span></span> <span data-ttu-id="cac95-133">打开“开始”/“运行”菜单，并在输入框中输入“mmc”，然后按“确定”可访问该管理单元。</span><span class="sxs-lookup"><span data-stu-id="cac95-133">The snap-in can be accessed by opening the Start/Run menu, typing "mmc" in the input box and pressing OK.</span></span> <span data-ttu-id="cac95-134">然后，在 "**控制台** 1" 窗口中，导航到 **"文件"/"添加/删除**" 管理单元，单击 "添加"，然后从 "**可用的独立管理单元**" 列表中选择 "**证书**"。</span><span class="sxs-lookup"><span data-stu-id="cac95-134">Then, in the **Console1** window, navigate to **the File/Add-Remove** Snap-in, click Add, and choose **Certificates** from the **Available Standalone Snapins** list.</span></span> <span data-ttu-id="cac95-135">最后，选择要管理的 **计算机帐户** ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="cac95-135">Finally, select **Computer Account** to manage and click **OK**.</span></span> <span data-ttu-id="cac95-136">" **证书** " 节点显示在管理单元控制台中。</span><span class="sxs-lookup"><span data-stu-id="cac95-136">The **Certificates** node appears in the snap-in console.</span></span>

<span data-ttu-id="cac95-137">必须拥有必需的证书才能建立信任。</span><span class="sxs-lookup"><span data-stu-id="cac95-137">You must already possess the required certificates to establish trust.</span></span> <span data-ttu-id="cac95-138">若要了解如何在执行以下步骤之前创建和安装新证书，请参阅 [如何：在开发过程中在 WCF 中创建和安装临时客户端证书](/previous-versions/msp-n-p/ff650751(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="cac95-138">To learn how to create and install new certificates prior to the following steps, see [How to: Create and Install Temporary Client Certificates in WCF During Development](/previous-versions/msp-n-p/ff650751(v=pandp.10)).</span></span>

1. <span data-ttu-id="cac95-139">在计算机 A 上，使用 MMC“证书”管理单元将现有证书 (certA) 导入 LocalMachine\MY（“个人”节点）和 LocalMachine\ROOT 存储区（“受信任的根证书颁发机构”节点）。</span><span class="sxs-lookup"><span data-stu-id="cac95-139">On machine A, using the MMC Certificates snap-in, import the existing certificate (certA) into the LocalMachine\MY (Personal Node) and LocalMachine\ROOT store (trusted root certification authority node).</span></span> <span data-ttu-id="cac95-140">若要将证书导入到特定节点，请右键单击该节点，然后选择 " **所有任务/导入**"。</span><span class="sxs-lookup"><span data-stu-id="cac95-140">To import a certificate to a specific node, right-click the node and choose **All Tasks/Import**.</span></span>

2. <span data-ttu-id="cac95-141">在计算机 B 上，使用 MMC“证书”管理单元创建或获取带私钥的证书 certB，并将其导入 LocalMachine\MY（“个人”节点）和 LocalMachine\ROOT 存储区（“受信任的根证书颁发机构”节点）。</span><span class="sxs-lookup"><span data-stu-id="cac95-141">On machine B, using the MMC Certificates snap-in, create or obtain a certificate certB with a private key and import it into the LocalMachine\MY (Personal Node) and LocalMachine\ROOT store (trusted root certification authority node).</span></span>

3. <span data-ttu-id="cac95-142">如果 certA 的公钥还未导出到文件，则完成此操作。</span><span class="sxs-lookup"><span data-stu-id="cac95-142">Export certA's public key to a file if this has not been done already.</span></span>

4. <span data-ttu-id="cac95-143">如果 certB 的公钥还未导出到文件，则完成此操作。</span><span class="sxs-lookup"><span data-stu-id="cac95-143">Export certB's public key to a file if this has not been done already.</span></span>

### <a name="establish-mutual-trust-between-machines"></a><span data-ttu-id="cac95-144">在计算机之间建立相互信任</span><span class="sxs-lookup"><span data-stu-id="cac95-144">Establish mutual trust between machines</span></span>

1. <span data-ttu-id="cac95-145">在计算机 A 上，将 certB 的文件表示形式导入 LocalMachine\MY 和 LocalMachine\ROOT 存储区。</span><span class="sxs-lookup"><span data-stu-id="cac95-145">On machine A, import the file representation of certB into the LocalMachine\MY and LocalMachine\ROOT stores.</span></span> <span data-ttu-id="cac95-146">这表明计算机 A 信任 certB 与之通信。</span><span class="sxs-lookup"><span data-stu-id="cac95-146">This declares that machine A trusts certB to communicate with it.</span></span>

2. <span data-ttu-id="cac95-147">在计算机 B 上，将 certA 的文件表示形式导入 LocalMachine\MY 和 LocalMachine\ROOT 存储区。</span><span class="sxs-lookup"><span data-stu-id="cac95-147">On machine B, import certA’s file into the LocalMachine\MY and LocalMachine\ROOT stores.</span></span> <span data-ttu-id="cac95-148">这表示计算机 B 信任 certA 与之通信。</span><span class="sxs-lookup"><span data-stu-id="cac95-148">This implies that machine B trusts certA to communicate with it.</span></span>

<span data-ttu-id="cac95-149">完成这些步骤之后，即在两台计算机之间建立了信任，这时，就可以将它们配置为使用 WS-AT 相互通信。</span><span class="sxs-lookup"><span data-stu-id="cac95-149">After completing these steps, trust is established between the two machines, and they can be configured to communicate with each other using WS-AT.</span></span>

### <a name="configure-msdtc-to-use-certificates"></a><span data-ttu-id="cac95-150">将 MSDTC 配置为使用证书</span><span class="sxs-lookup"><span data-stu-id="cac95-150">Configure MSDTC to use certificates</span></span>

<span data-ttu-id="cac95-151">由于 WS-AT 协议服务既作为客户端又作为服务器，因此它必须侦听传入连接和发起传出连接。</span><span class="sxs-lookup"><span data-stu-id="cac95-151">Since the WS-AT protocol service acts as both a client and a server, it must both listen for incoming connections and initiate outgoing connections.</span></span> <span data-ttu-id="cac95-152">因此，需要对 MSDTC 进行配置，以使它知道在与外部各方通信时要使用哪个证书，在接受传入通信时要授权哪个证书。</span><span class="sxs-lookup"><span data-stu-id="cac95-152">Therefore, you need to configure MSDTC so that it knows which certificate to use when communicating with external parties, and which certificates to authorize when accepting incoming communication.</span></span>

<span data-ttu-id="cac95-153">可以使用 MMC WS-AT 管理单元进行这一配置。</span><span class="sxs-lookup"><span data-stu-id="cac95-153">You can configure this by using the MMC WS-AT snap-in.</span></span> <span data-ttu-id="cac95-154">有关此工具的详细信息，请参阅 [Ws-atomictransaction 配置 MMC 管理单元](../ws-atomictransaction-configuration-mmc-snap-in.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="cac95-154">For more information about this tool, see the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="cac95-155">下面的步骤介绍如何在运行 MSDTC 的两台计算机之间建立信任。</span><span class="sxs-lookup"><span data-stu-id="cac95-155">The following steps describe how to establish trust between two computers running MSDTC.</span></span>

1. <span data-ttu-id="cac95-156">配置计算机 A 的设置。</span><span class="sxs-lookup"><span data-stu-id="cac95-156">Configure machine A's settings.</span></span> <span data-ttu-id="cac95-157">对于 "终结点证书"，请选择 certA。</span><span class="sxs-lookup"><span data-stu-id="cac95-157">For "Endpoint Certificate", select certA.</span></span> <span data-ttu-id="cac95-158">对于 "授权的证书"，请选择 certB。</span><span class="sxs-lookup"><span data-stu-id="cac95-158">For "Authorized Certificates", select the certB.</span></span>

2. <span data-ttu-id="cac95-159">配置计算机 B 的设置。</span><span class="sxs-lookup"><span data-stu-id="cac95-159">Configure machine B's settings.</span></span> <span data-ttu-id="cac95-160">对于 "终结点证书"，请选择 certB。</span><span class="sxs-lookup"><span data-stu-id="cac95-160">For "Endpoint Certificate", select certB.</span></span> <span data-ttu-id="cac95-161">对于 "授权的证书"，请选择 certA。</span><span class="sxs-lookup"><span data-stu-id="cac95-161">For "Authorized Certificates", select the certA.</span></span>

> [!NOTE]
> <span data-ttu-id="cac95-162">当一台计算机向另一台计算机发送消息时，发送方尝试验证接收方证书的主题名称和接收方计算机的名称是否匹配。</span><span class="sxs-lookup"><span data-stu-id="cac95-162">When one machine sends a message to the other machine, the sender attempts to verify that the subject name of the recipient’s certificate and the name of the recipient’s machine match.</span></span> <span data-ttu-id="cac95-163">如果不匹配，则证书验证失败，并且两台计算机无法通信。</span><span class="sxs-lookup"><span data-stu-id="cac95-163">If they do not match, certificate verification fails and the two machines cannot communicate.</span></span>
>
> <span data-ttu-id="cac95-164">对于加入域的计算机，该名称为完全限定域名。</span><span class="sxs-lookup"><span data-stu-id="cac95-164">For a machine joined to a domain, the name is the fully qualified domain name.</span></span> <span data-ttu-id="cac95-165">默认情况下，工作站中的计算机名称就是计算机的 NetBIOS 名称。</span><span class="sxs-lookup"><span data-stu-id="cac95-165">By default, the name of a machine on a workgroup is the machine’s NetBIOS name.</span></span> <span data-ttu-id="cac95-166">但是，对于两台计算机之间所用的连接，如果存在域名系统 (DNS) 后缀，则名称中还可包含 DNS 后缀。</span><span class="sxs-lookup"><span data-stu-id="cac95-166">However, the name can also include a Domain Name System (DNS) suffix if one is present for the connection being used between the two machines.</span></span>
>
> <span data-ttu-id="cac95-167">如果计算机的名称更改，例如，当工作组计算机加入域时，必须重新颁发证书或手动配置 DNS 后缀。</span><span class="sxs-lookup"><span data-stu-id="cac95-167">If the name of the machine changes, for example, when a workgroup machine joins a domain, you must reissue certificates or manually configure DNS suffixes.</span></span>

## <a name="security"></a><span data-ttu-id="cac95-168">安全</span><span class="sxs-lookup"><span data-stu-id="cac95-168">Security</span></span>

<span data-ttu-id="cac95-169">由于某些与 MSDTC 和 WS-AT 关联的设置分别存储在注册表的 HKLM\Software\Microsoft\MSDTC 和 HKLM\Software\Microsoft\WSAT 下面，因此，请确保这些注册表项得到了保护，只有管理员才能写入这些项。</span><span class="sxs-lookup"><span data-stu-id="cac95-169">Since some of the settings related to MSDTC and WS-AT are stored in the registry at HKLM\Software\Microsoft\MSDTC and at HKLM\Software\Microsoft\WSAT, respectively, ensure that these registry keys are secured so that only administrators can write to them.</span></span> <span data-ttu-id="cac95-170">在 "注册表编辑器" 工具中，右键单击要保护的项，然后选择 " **权限** " 以设置适当的访问控制。</span><span class="sxs-lookup"><span data-stu-id="cac95-170">In the Registry Editor tool, right-click the key you want to secure and select **Permission** to set the appropriate access control.</span></span> <span data-ttu-id="cac95-171">对于系统的安全性和完整性而言，重要的项对于低权限用户只读至关重要。</span><span class="sxs-lookup"><span data-stu-id="cac95-171">It is crucial to the security and integrity of the system that important keys are read-only for low-privileged users.</span></span>

<span data-ttu-id="cac95-172">部署 MSDTC 时，管理员必须确保任何 MSDTC 数据交换都是安全的。</span><span class="sxs-lookup"><span data-stu-id="cac95-172">When deploying MSDTC, the administrator must ensure that any MSDTC data interchange is secure.</span></span> <span data-ttu-id="cac95-173">在工作组部署中，应将事务基础结构与恶意用户隔离；而在群集部署中，应保护群集注册表。</span><span class="sxs-lookup"><span data-stu-id="cac95-173">In a workgroup deployment, isolate the transactional infrastructure from malicious users; in a cluster deployment, secure the cluster registry.</span></span>

## <a name="tracing"></a><span data-ttu-id="cac95-174">跟踪</span><span class="sxs-lookup"><span data-stu-id="cac95-174">Tracing</span></span>

<span data-ttu-id="cac95-175">WS-AT 协议服务支持集成的事务特定跟踪，可通过使用 [Ws-atomictransaction 配置 MMC 管理单元](../ws-atomictransaction-configuration-mmc-snap-in.md) 工具启用和管理。</span><span class="sxs-lookup"><span data-stu-id="cac95-175">The WS-AT protocol service supports integrated, transaction-specific tracing that can be enabled and managed through the use of the [WS-AtomicTransaction Configuration MMC Snap-in](../ws-atomictransaction-configuration-mmc-snap-in.md) tool.</span></span> <span data-ttu-id="cac95-176">跟踪可包含指示以下内容的数据：特定事务的登记时间、事务达到其最终状态的时间、每个事务登记收到的结果。</span><span class="sxs-lookup"><span data-stu-id="cac95-176">Traces can include data indicating the time an enlistment is made for a specific transaction, the time a transaction reaches its terminal state, the outcome each transaction enlistment has received.</span></span> <span data-ttu-id="cac95-177">可以使用 [服务跟踪查看器工具 ( # A0) ](../service-trace-viewer-tool-svctraceviewer-exe.md) 工具查看所有跟踪。</span><span class="sxs-lookup"><span data-stu-id="cac95-177">All traces can be viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tool.</span></span>

<span data-ttu-id="cac95-178">通过 ETW 跟踪会话，WS-AT 协议服务还支持集成 ServiceModel 跟踪。</span><span class="sxs-lookup"><span data-stu-id="cac95-178">The WS-AT protocol service also supports integrated ServiceModel tracing through the ETW trace session.</span></span> <span data-ttu-id="cac95-179">这样，除了现有事务跟踪之外，可提供更多特定于通信的详细跟踪。</span><span class="sxs-lookup"><span data-stu-id="cac95-179">This provides more detailed, communication-specific traces in addition to the existing transaction traces.</span></span>  <span data-ttu-id="cac95-180">若要启用这些附加跟踪，请按照以下步骤操作</span><span class="sxs-lookup"><span data-stu-id="cac95-180">To enable these additional traces, follow these steps</span></span>

1. <span data-ttu-id="cac95-181">打开 " **开始/运行** " 菜单，在 "输入" 框中键入 "regedit"，然后选择 **"确定**"。</span><span class="sxs-lookup"><span data-stu-id="cac95-181">Open the **Start/Run** menu, type "regedit" in the input box and select **OK**.</span></span>

2. <span data-ttu-id="cac95-182">在 **注册表编辑器** 中，导航到左侧窗格中的以下文件夹，Hkey_Local_Machine \software\microsoft\wsat\3.0</span><span class="sxs-lookup"><span data-stu-id="cac95-182">In the **Registry Editor**, navigate to the following folder on the left pane, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0</span></span>\

3. <span data-ttu-id="cac95-183">右键单击 `ServiceModelDiagnosticTracing` 右窗格中的值，然后选择 " **修改**"。</span><span class="sxs-lookup"><span data-stu-id="cac95-183">Right-click the `ServiceModelDiagnosticTracing` value in the right pane and select **Modify**.</span></span>

4. <span data-ttu-id="cac95-184">在 " **值数据** 输入" 框中，输入以下有效值之一，以指定要启用的跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="cac95-184">In the **Value data** input box, enter one of the following valid values to specify the trace level you want to enable.</span></span>

- <span data-ttu-id="cac95-185">0：关闭</span><span class="sxs-lookup"><span data-stu-id="cac95-185">0: off</span></span>

- <span data-ttu-id="cac95-186">1：严重</span><span class="sxs-lookup"><span data-stu-id="cac95-186">1: critical</span></span>

- <span data-ttu-id="cac95-187">3：错误。</span><span class="sxs-lookup"><span data-stu-id="cac95-187">3: error.</span></span> <span data-ttu-id="cac95-188">此为默认值。</span><span class="sxs-lookup"><span data-stu-id="cac95-188">This is the default value</span></span>

- <span data-ttu-id="cac95-189">7：警告</span><span class="sxs-lookup"><span data-stu-id="cac95-189">7: warning</span></span>

- <span data-ttu-id="cac95-190">15：信息</span><span class="sxs-lookup"><span data-stu-id="cac95-190">15: information</span></span>

- <span data-ttu-id="cac95-191">31：详细</span><span class="sxs-lookup"><span data-stu-id="cac95-191">31: verbose</span></span>

## <a name="see-also"></a><span data-ttu-id="cac95-192">请参阅</span><span class="sxs-lookup"><span data-stu-id="cac95-192">See also</span></span>

- [<span data-ttu-id="cac95-193">WS-AtomicTransaction 配置实用工具 (wsatConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="cac95-193">WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span></span>](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [<span data-ttu-id="cac95-194">WS-AtomicTransaction 配置 MMC 管理单元</span><span class="sxs-lookup"><span data-stu-id="cac95-194">WS-AtomicTransaction Configuration MMC Snap-in</span></span>](../ws-atomictransaction-configuration-mmc-snap-in.md)
