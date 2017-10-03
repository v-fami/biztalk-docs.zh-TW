---
title: "如何設定 BizTalk Server 接收 MIME 加密或 SMIME 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d72002c8-6bd8-458f-8149-1c0c4cbbb682
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e996ea258b8f3ab1c7df2d30ed12aa0d0150b35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-receive-encrypted-mime-or-smime-messages"></a><span data-ttu-id="bf151-102">如何設定 BizTalk Server 接收 MIME 加密或 SMIME 訊息</span><span class="sxs-lookup"><span data-stu-id="bf151-102">How to Configure BizTalk Server to Receive Encrypted MIME or SMIME Messages</span></span>
<span data-ttu-id="bf151-103">本主題描述如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以使用憑證來接收加密的 MIME/SMIME 訊息。</span><span class="sxs-lookup"><span data-stu-id="bf151-103">This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use certificates to receive encrypted MIME/SMIME messages.</span></span> <span data-ttu-id="bf151-104">下列程序也適用於接收加密訊息的設定透過 AS2 傳輸。</span><span class="sxs-lookup"><span data-stu-id="bf151-104">The procedure below also applies to configuring the receiving of encrypted messages over AS2 transport.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bf151-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="bf151-105">Prerequisites</span></span>  
 <span data-ttu-id="bf151-106">若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="bf151-106">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-receive-encrypted-messages"></a><span data-ttu-id="bf151-107">若要設定 BizTalk Server 接收加密的訊息</span><span class="sxs-lookup"><span data-stu-id="bf151-107">To configure BizTalk Server to receive encrypted messages</span></span>  
  
1.  <span data-ttu-id="bf151-108">建立管線來接收加密的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf151-108">Create a pipeline to receive encrypted messages, as follows:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf151-109">設定 AS2 傳輸接收加密訊息的 AS2Receive 和 AS2EdiReceive 管線，因為包含在這個步驟並非必要[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]做這個函式。</span><span class="sxs-lookup"><span data-stu-id="bf151-109">This step is not necessary when configuring AS2 transport for receiving encrypted messages because the AS2Receive and AS2EdiReceive pipelines that are included in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] serve this function.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf151-110">MIME/SMIME 解碼器管線元件會執行解密及數位簽章驗證 (當設定為執行這兩項功能時)。</span><span class="sxs-lookup"><span data-stu-id="bf151-110">The MIME/SMIME Decoder pipeline component performs both decryption and digital signature validation (when configured to perform both functions).</span></span> <span data-ttu-id="bf151-111">因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來接收加密及簽署的訊息，您可以使用相同的接收管線。</span><span class="sxs-lookup"><span data-stu-id="bf151-111">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted and signed messages, you can use the same receive pipeline.</span></span> <span data-ttu-id="bf151-112">換句話說，您不需要針對解密和數位簽章驗證建立個別的管線。</span><span class="sxs-lookup"><span data-stu-id="bf151-112">In other words, you do not have to create separate pipelines for decryption and digital signature validation.</span></span>  
  
    1.  <span data-ttu-id="bf151-113">建立接收管線，然後將 MIME/SMIME 解碼器管線元件拖曳到管線的 「 解碼 」 階段。</span><span class="sxs-lookup"><span data-stu-id="bf151-113">Create a receive pipeline and then drag the MIME/SMIME Decoder pipeline component into the Decode stage of the pipeline.</span></span>  
  
    2.  <span data-ttu-id="bf151-114">在**屬性**視窗中，設定 MIME/SMIME 解碼器管線元件屬性。</span><span class="sxs-lookup"><span data-stu-id="bf151-114">In the **Properties** window, configure the MIME/SMIME Decoder pipeline component properties.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="bf151-115">設定 MIME/SMIME 解碼器管線元件屬性包含檢查撤銷清單屬性設為 True，如果您想要檢查傳送者用來簽署要傳送之訊息的憑證的憑證撤銷清單[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf151-115">Configuring the MIME/SMIME Decoder pipeline component properties includes setting the Check Revocation List property to True if you want to check the certificate revocation list for the certificates that senders use for signing messages that are being sent to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="bf151-116">停用此選項會提高元件的效能。</span><span class="sxs-lookup"><span data-stu-id="bf151-116">Disabling this option increases the performance of the component.</span></span> <span data-ttu-id="bf151-117">與憑證相關聯的憑證撤銷清單會從適當的憑證服務的網站下載。</span><span class="sxs-lookup"><span data-stu-id="bf151-117">The certificate revocation list associated with a certificate is downloaded from the appropriate certificate services Web site.</span></span> <span data-ttu-id="bf151-118">如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法連線到遠端網站上，在管線中的訊息就會失敗。</span><span class="sxs-lookup"><span data-stu-id="bf151-118">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot connect to the remote Web site, the message fails in the pipeline.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="bf151-119">當您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台將此管線部署到 BizTalk 群組後，您可以為接收位置設定管線屬性。</span><span class="sxs-lookup"><span data-stu-id="bf151-119">You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="bf151-120">您可以針對 BizTalk 群組中的每一個接收位置設定不同的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="bf151-120">You can configure different pipeline properties for each receive location in the BizTalk group.</span></span>  
  
    3.  <span data-ttu-id="bf151-121">建置和部署接收管線。</span><span class="sxs-lookup"><span data-stu-id="bf151-121">Build and deploy the receive pipeline.</span></span>  
  
2.  <span data-ttu-id="bf151-122">設定接收位置來接收加密的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf151-122">Configure the receive location for receiving encrypted messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="bf151-123">將您建立包含 BizTalk 應用程式包括的接收位置來接收加密的訊息的接收管線的 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="bf151-123">Add the BizTalk assembly that you created containing the receive pipeline to the BizTalk application including the receive locations to receive encrypted messages.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="bf151-124">設定 AS2 傳輸來接收加密的訊息，因為在 「 BizTalk EDI 應用程式中包含 AS2Receive 和 AS2EdiReceive 管線時，不需要這個步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf151-124">This step is not necessary when configuring AS2 transport for receiving encrypted messages because the AS2Receive and AS2EdiReceive pipelines are included in the BizTalk EDI Application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="bf151-125">您在上一個步驟中建立的接收管線的 BizTalk 應用程式中設定接收位置。</span><span class="sxs-lookup"><span data-stu-id="bf151-125">Configure the receive locations in the BizTalk application with the receive pipeline that you created in the previous step.</span></span>  
  
3.  <span data-ttu-id="bf151-126">設定用來主控件的接收處理常式的加密憑證，接收位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf151-126">Configure the host used as the receive handler for the receive location with the decryption certificate, as follows:</span></span>  
  
    1.  <span data-ttu-id="bf151-127">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下 BizTalk 也就是裝載的處理常式來接收加密的訊息，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="bf151-127">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click a BizTalk host that is the handler for receiving the encrypted messages, and then click **Properties**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="bf151-128">此程序不適用於 AS2 傳輸適用於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf151-128">This procedure does not apply for AS2 transport available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="bf151-129">它適用於 BizTalk MIME 解碼器，AS2 解碼器。</span><span class="sxs-lookup"><span data-stu-id="bf151-129">It applies for the BizTalk MIME Decoder, not the AS2 Decoder.</span></span> <span data-ttu-id="bf151-130">AS2 解碼器將會決定訊息中的憑證資訊為基礎的憑證。</span><span class="sxs-lookup"><span data-stu-id="bf151-130">The AS2 Decoder will determine the certificate based on certificate information in the message.</span></span>  
  
    2.  <span data-ttu-id="bf151-131">在**主控件屬性**對話方塊中，按一下 **憑證**，然後按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="bf151-131">In the **Host Properties** dialog box, click **Certificate**, and then click **Browse**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="bf151-132">上述程序可讓您設定您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，因此，只有特定主控件可以接收和處理特定訊息。</span><span class="sxs-lookup"><span data-stu-id="bf151-132">The above procedure enables you to configure your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment so that only certain hosts can receive and process particular messages.</span></span> <span data-ttu-id="bf151-133">當您將主控件設定用於訊息解碼和解密，憑證的指紋[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]該主機在 MessageBox 資料庫中建立應用程式屬性。</span><span class="sxs-lookup"><span data-stu-id="bf151-133">When you configure a host with the thumbprint of a certificate to use for message decoding and decryption, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] creates an application property for that host in the MessageBox database.</span></span> <span data-ttu-id="bf151-134">保護接收的訊息，並解密使用此指紋接著只會路由這個資料庫和其他已具有此指紋的主機。</span><span class="sxs-lookup"><span data-stu-id="bf151-134">Secure messages that are received and decrypted using this thumbprint are then only routed to this and other hosts that are configured with this thumbprint.</span></span>  
  
    3.  <span data-ttu-id="bf151-135">在**選取憑證**對話方塊中，選取您已安裝，解密憑證，然後關閉所有對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bf151-135">In the **Select Certificate** dialog box, select the decryption certificate that you installed, and then close all the dialog boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf151-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf151-136">See Also</span></span>  
 [<span data-ttu-id="bf151-137">設定 MIME 或 SMIME 訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="bf151-137">Configuring Certificates for MIME or SMIME Messages</span></span>](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)