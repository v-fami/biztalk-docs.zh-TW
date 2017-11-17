---
title: "如何安裝數位簽章的憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 910ccd84-c022-46a5-a9de-b99046a480b8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a755e59c7c916f3abe037513ddbc9e2a89892fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-certificates-for-digital-signatures"></a><span data-ttu-id="737ed-102">如何安裝數位簽章的憑證</span><span class="sxs-lookup"><span data-stu-id="737ed-102">How to install the Certificates for Digital Signatures</span></span>
<span data-ttu-id="737ed-103">下列程序列出在安裝憑證來接收及傳送簽署的訊息時，所必須遵循的高層級步驟。</span><span class="sxs-lookup"><span data-stu-id="737ed-103">The following procedure lists the high-level steps that you have to follow to install the certificates for receiving and sending signed messages.</span></span>  
  
-   <span data-ttu-id="737ed-104">在憑證存放區中安裝憑證以接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="737ed-104">To install the certificates in the certificates store to receive signed messages</span></span>  
  
-   <span data-ttu-id="737ed-105">在憑證存放區中安裝用於傳送簽署訊息的簽署憑證</span><span class="sxs-lookup"><span data-stu-id="737ed-105">To install the signing certificates for sending signed messages in the certificates store</span></span>  
  
-   <span data-ttu-id="737ed-106">設定 BizTalk 群組來傳送簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="737ed-106">To configure the BizTalk Group for sending signed messages</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="737ed-107">您可以使用一個憑證來進行簽署及解密作業，或者也可以針對每一個功能使用一個憑證。</span><span class="sxs-lookup"><span data-stu-id="737ed-107">You can use one certificate for both signing and decryption operations, or you can use one certificate for each function.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="737ed-108">您只能指定一個簽署憑證，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用來簽署所有輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="737ed-108">You can only specify one signing certificate with which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] signs all outbound messages.</span></span> <span data-ttu-id="737ed-109">換句話說，您無法根據訊息的傳送對象來使用不同的簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="737ed-109">In other words, you cannot use different signing certificates depending on who you are sending the message to.</span></span>  
  
### <a name="to-install-the-certificates-in-the-certificates-store-to-receive-signed-messages"></a><span data-ttu-id="737ed-110">在憑證存放區中安裝憑證以接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="737ed-110">To install the certificates in the certificates store to receive signed messages</span></span>  
  
1.  <span data-ttu-id="737ed-111">夥伴 A 從憑證授權單位 (CA) 要求數位簽章的私密-公開金鑰組。</span><span class="sxs-lookup"><span data-stu-id="737ed-111">Partner A requests a private-public key pair for digital signatures from the certification authority (CA).</span></span>  
  
2.  <span data-ttu-id="737ed-112">夥伴 A 將其數位簽章的公開金鑰傳送給您。</span><span class="sxs-lookup"><span data-stu-id="737ed-112">Partner A sends you its public key for digital signatures.</span></span>  
  
3.  <span data-ttu-id="737ed-113">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，登入有執行處理常式之主控件執行個體的伺服器 (此處理常式將會從夥伴 A 接收訊息)。安裝夥伴 A 公開金鑰憑證，以驗證其在「其他人」存放區中的簽章。</span><span class="sxs-lookup"><span data-stu-id="737ed-113">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on to the server that has a host instance running a handler that will receive messages from Partner A. Install the Partner A public key certificate to verify their signature in the Other People store.</span></span> <span data-ttu-id="737ed-114">下圖顯示您安裝此憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="737ed-114">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="737ed-115">![接收安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span><span class="sxs-lookup"><span data-stu-id="737ed-115">![Certificates required to receive secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span></span>  
  
4.  <span data-ttu-id="737ed-116">在夥伴 A 中，安裝夥伴 A 私密金鑰憑證，在適當的存放區中簽署訊息</span><span class="sxs-lookup"><span data-stu-id="737ed-116">In Partner A, install the Partner A private key certificate for signing messages in the appropriate store.</span></span> <span data-ttu-id="737ed-117">(如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在要用於簽署傳送給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的訊息的帳戶之個人存放區中，安裝私密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="737ed-117">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the private key in the personal store for the account that will sign messages sent to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)</span></span>  
  
### <a name="to-install-the-signing-certificates-for-sending-signed-messages-in-the-certificates-store"></a><span data-ttu-id="737ed-118">在憑證存放區中安裝用於傳送簽署訊息的簽署憑證</span><span class="sxs-lookup"><span data-stu-id="737ed-118">To install the signing certificates for sending signed messages in the certificates store</span></span>  
  
1.  <span data-ttu-id="737ed-119">您組織中的系統管理員從 CA 要求數位簽章的私密-公開金鑰組，以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用。</span><span class="sxs-lookup"><span data-stu-id="737ed-119">An administrator in your organization requests a private-public key pair for digital signatures from the CA for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use.</span></span>  
  
2.  <span data-ttu-id="737ed-120">系統管理員會將數位簽章的公開金鑰傳送給夥伴 A (及所有其他夥伴)。</span><span class="sxs-lookup"><span data-stu-id="737ed-120">The administrator sends Partner A (and all other partners) the public key for digital signatures.</span></span>  
  
3.  <span data-ttu-id="737ed-121">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，針對執行處理常式 (此處理常式將傳送訊息給夥伴 A) 的主控件執行個體，以其服務帳戶的身分登入。在該服務帳戶的個人存放區中，安裝簽署訊息所需的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 私密金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="737ed-121">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on as service account for the host instance running the handler that will send messages to Partner A. Install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] private key certificate for signing messages in the personal store for the service account.</span></span> <span data-ttu-id="737ed-122">下圖顯示您安裝此憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="737ed-122">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="737ed-123">![傳送安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span><span class="sxs-lookup"><span data-stu-id="737ed-123">![Certificates required to send secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span></span>  
  
4.  <span data-ttu-id="737ed-124">在夥伴 A 中，安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 公開金鑰憑證，以便驗證其在適當存放區中的數位簽章</span><span class="sxs-lookup"><span data-stu-id="737ed-124">In Partner A, install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] public key certificate for verifying its digital signature in the appropriate store.</span></span> <span data-ttu-id="737ed-125">(如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在「其他人」存放區中安裝公開金鑰)。</span><span class="sxs-lookup"><span data-stu-id="737ed-125">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the public key in the Other people store.)</span></span>  
  
### <a name="to-configure-the-biztalk-group-for-sending-signed-messages"></a><span data-ttu-id="737ed-126">設定 BizTalk 群組來傳送簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="737ed-126">To configure the BizTalk Group for sending signed messages</span></span>  
  
1.  <span data-ttu-id="737ed-127">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="737ed-127">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="737ed-128">以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="737ed-128">Right-click **BizTalk Group**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="737ed-129">在**群組內容**對話方塊中，按一下 **憑證**，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="737ed-129">On the **Group Properties** dialog box, click **Certificate**, click **Browse**.</span></span>  
  
4.  <span data-ttu-id="737ed-130">在**選取憑證**對話方塊中，選取您已安裝，簽署憑證，然後關閉所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="737ed-130">On the **Select Certificate** dialog box, select the signing certificate that you installed, and then close all of the dialog boxes.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="737ed-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="737ed-131">Next Steps</span></span>  
 <span data-ttu-id="737ed-132">建立管線來接收簽署的訊息[如何設定接收簽署訊息的 BizTalk 伺服器](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="737ed-132">You create a pipeline to receive signed messages in [How to Configure BizTalk Server for Receiving Signed Messages](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md).</span></span>  
  
 <span data-ttu-id="737ed-133">您建立管線來傳送簽署的訊息[傳送簽署的訊息設定 BizTalk Server 如何](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="737ed-133">You create a pipeline to send signed messages in [How to Configure BizTalk Server for Sending Signed Messages](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737ed-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="737ed-134">See Also</span></span>  
 <span data-ttu-id="737ed-135">[BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="737ed-135">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 [<span data-ttu-id="737ed-136">傳送及接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="737ed-136">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)