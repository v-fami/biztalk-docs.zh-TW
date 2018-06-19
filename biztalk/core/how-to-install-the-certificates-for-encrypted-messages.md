---
title: 如何安裝加密訊息的憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e11fdb81-041c-4ba6-849d-d511ead0e8be
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b1df2e9e5bf42a215420dac155fafac8e92ae21
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254774"
---
# <a name="how-to-install-the-certificates-for-encrypted-messages"></a><span data-ttu-id="a3d65-102">如何安裝加密訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="a3d65-102">How to Install the Certificates for Encrypted Messages</span></span>
<span data-ttu-id="a3d65-103">下列程序列出在安裝憑證來接收及傳送加密訊息時，所必須遵循的高層級步驟。</span><span class="sxs-lookup"><span data-stu-id="a3d65-103">The following procedure lists the high-level steps that you have to follow to install the certificates for receiving and sending encrypted messages.</span></span>  
  
-   <span data-ttu-id="a3d65-104">在憑證存放區中安裝用於解密的憑證</span><span class="sxs-lookup"><span data-stu-id="a3d65-104">To install certificates in the certificates store for decryption</span></span>  
  
-   <span data-ttu-id="a3d65-105">在憑證存放區中安裝用於加密的憑證</span><span class="sxs-lookup"><span data-stu-id="a3d65-105">To install certificates in the certificates store for encryption</span></span>  
  
-   <span data-ttu-id="a3d65-106">設定用於接收加密訊息的 BizTalk 主控件</span><span class="sxs-lookup"><span data-stu-id="a3d65-106">To configure BizTalk hosts for receiving encrypted messages</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3d65-107">您可以使用一個憑證來進行簽署及解密作業，或者也可以針對每一個功能使用一個憑證。</span><span class="sxs-lookup"><span data-stu-id="a3d65-107">You can use one certificate for both signing and decryption operations, or you can use one certificate for each function.</span></span>  
  
### <a name="to-install-the-decryption-certificates-in-the-certificates-store"></a><span data-ttu-id="a3d65-108">在憑證存放區中安裝解密憑證</span><span class="sxs-lookup"><span data-stu-id="a3d65-108">To install the decryption certificates in the certificates store</span></span>  
  
1.  <span data-ttu-id="a3d65-109">您組織中的系統管理員向憑證授權單位 (CA) 要求加密的私密-公開金鑰組，以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用。</span><span class="sxs-lookup"><span data-stu-id="a3d65-109">An administrator in your organization requests a private-public key pair for encryption from the certification authority (CA) for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use.</span></span>  
  
2.  <span data-ttu-id="a3d65-110">系統管理員將加密的公開金鑰傳送給夥伴 A。</span><span class="sxs-lookup"><span data-stu-id="a3d65-110">The administrator sends the public key for encryption to Partner A.</span></span>  
  
3.  <span data-ttu-id="a3d65-111">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，針對執行處理常式 (此處理常式將從夥伴 A 接收訊息) 的主控件執行個體，以其服務帳戶的身分登入。安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 私密金鑰憑證，以便為此服務帳戶之個人存放區中的訊息解密。</span><span class="sxs-lookup"><span data-stu-id="a3d65-111">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on as the service account for the host instance running the handler that will receive messages from Partner A. Install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] private key certificate for decrypting messages in the personal store for the service account.</span></span> <span data-ttu-id="a3d65-112">下圖顯示您安裝此憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a3d65-112">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="a3d65-113">![接收安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span><span class="sxs-lookup"><span data-stu-id="a3d65-113">![Certificates required to receive secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span></span>  
  
4.  <span data-ttu-id="a3d65-114">在夥伴 A 中，安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 公開金鑰憑證，以便在適當的存放區中加密傳送給夥伴 A 的訊息</span><span class="sxs-lookup"><span data-stu-id="a3d65-114">In Partner A, install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] public key certificate for encrypting messages sent to Partner A in the appropriate store.</span></span> <span data-ttu-id="a3d65-115">(如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在「其他人」存放區中安裝公開金鑰)。</span><span class="sxs-lookup"><span data-stu-id="a3d65-115">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the public key in the Other People store.)</span></span>  
  
### <a name="to-install-the-encryption-certificates-in-the-certificates-store"></a><span data-ttu-id="a3d65-116">在憑證存放區中安裝加密憑證</span><span class="sxs-lookup"><span data-stu-id="a3d65-116">To install the encryption certificates in the certificates store</span></span>  
  
1.  <span data-ttu-id="a3d65-117">夥伴 A 從 CA 要求加密的私密-公開金鑰組。</span><span class="sxs-lookup"><span data-stu-id="a3d65-117">Partner A requests a private-public key pair for encryption from the CA.</span></span>  
  
2.  <span data-ttu-id="a3d65-118">夥伴 A 會在適當的存放區中安裝解密訊息的私密金鑰憑證</span><span class="sxs-lookup"><span data-stu-id="a3d65-118">Partner A installs the private key certificate for decrypting the messages in the appropriate store.</span></span> <span data-ttu-id="a3d65-119">(如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在個人憑證存放區中安裝私密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="a3d65-119">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the private key in the personal certificate store.)</span></span>  
  
3.  <span data-ttu-id="a3d65-120">夥伴 A 會把公開金鑰傳送給您，這個金鑰是用於加密傳送給夥伴 A 的訊息。</span><span class="sxs-lookup"><span data-stu-id="a3d65-120">Partner A sends you its public key for encrypting messages sent to Partner A.</span></span>  
  
4.  <span data-ttu-id="a3d65-121">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，登入有執行處理常式之主控件執行個體的伺服器 (此處理常式將會傳送訊息給夥伴 A)。安裝夥伴 A 公開金鑰憑證，以便在「其他人」存放區中加密傳送給夥伴 A 的訊息。</span><span class="sxs-lookup"><span data-stu-id="a3d65-121">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on to the server that has a host instance running a handler that will send messages to Partner A. Install the Partner A public key certificate for encrypting messages sent to Partner A in the Other People store.</span></span> <span data-ttu-id="a3d65-122">下圖顯示您安裝此憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a3d65-122">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="a3d65-123">![傳送安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span><span class="sxs-lookup"><span data-stu-id="a3d65-123">![Certificates required to send secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span></span>  
  
### <a name="to-configure-biztalk-hosts-for-receiving-encrypted-messages"></a><span data-ttu-id="a3d65-124">設定用於接收加密訊息的 BizTalk 主控件</span><span class="sxs-lookup"><span data-stu-id="a3d65-124">To configure BizTalk hosts for receiving encrypted messages</span></span>  
  
1.  <span data-ttu-id="a3d65-125">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a3d65-125">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a3d65-126">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**平台設定**，依序展開**主機**。</span><span class="sxs-lookup"><span data-stu-id="a3d65-126">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Platform Settings**, expand **Hosts**.</span></span>  
  
    1.  <span data-ttu-id="a3d65-127">在右窗格中，以滑鼠右鍵按一下 BizTalk 主控件的處理常式來接收加密的訊息，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a3d65-127">On the right pane, right-click a BizTalk host that is the handler for receiving the encrypted messages, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="a3d65-128">在**主控件屬性**對話方塊中，按一下 **憑證**，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="a3d65-128">On the **Host Properties** dialog box, click **Certificate**, click **Browse**.</span></span>  
  
    3.  <span data-ttu-id="a3d65-129">在**選取憑證**對話方塊中，選取您已安裝，解密憑證，然後關閉所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a3d65-129">On the **Select Certificate** dialog box, select the decryption certificate that you installed, and then close all of the dialog boxes.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a3d65-130">如需詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d65-130">For more information, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a3d65-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a3d65-131">Next Steps</span></span>  
 <span data-ttu-id="a3d65-132">建立管線來接收加密的訊息[如何設定 BizTalk Server 接收加密訊息](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)</span><span class="sxs-lookup"><span data-stu-id="a3d65-132">You create a pipeline to receive encrypted messages in [How to Configure BizTalk Server for Receiving Encrypted Messages](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)</span></span>  
  
 <span data-ttu-id="a3d65-133">您建立管線來傳送加密的訊息[如何設定 BizTalk Server 傳送加密訊息](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)</span><span class="sxs-lookup"><span data-stu-id="a3d65-133">You create a pipeline to send encrypted messages in [How to Configure BizTalk Server for Sending Encrypted Messages](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d65-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3d65-134">See Also</span></span>  
 <span data-ttu-id="a3d65-135">[BizTalk Server 會使用加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="a3d65-135">[Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span></span>  
 [<span data-ttu-id="a3d65-136">傳送和接收加密的訊息</span><span class="sxs-lookup"><span data-stu-id="a3d65-136">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)