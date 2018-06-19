---
title: 如何設定 BizTalk Server 進行合作對象解析 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ac330b9-3498-4c98-a6e8-d2c02cd641dd
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9d7a21b4edf5df4bd903763bcb3d1a8a8c6e1ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250086"
---
# <a name="how-to-configure-biztalk-server-for-party-resolution"></a><span data-ttu-id="75c89-102">如何設定 BizTalk Server 進行合作對象解析</span><span class="sxs-lookup"><span data-stu-id="75c89-102">How to Configure BizTalk Server for Party Resolution</span></span>
<span data-ttu-id="75c89-103">若要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 進行合作對象解析，您必須遵循下列程序所列的步驟。</span><span class="sxs-lookup"><span data-stu-id="75c89-103">The following procedure lists the steps that you have to follow to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for party resolution.</span></span>  
  
-   <span data-ttu-id="75c89-104">在憑證存放區中安裝憑證以接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="75c89-104">To install the certificates in the certificates store to receive signed messages</span></span>  
  
-   <span data-ttu-id="75c89-105">建立代表夥伴的合作對象</span><span class="sxs-lookup"><span data-stu-id="75c89-105">To create a party to represent your partner</span></span>  
  
-   <span data-ttu-id="75c89-106">使用憑證建立合作對象解析的管線</span><span class="sxs-lookup"><span data-stu-id="75c89-106">To create a pipeline for party resolution using certificates</span></span>  
  
-   <span data-ttu-id="75c89-107">使用憑證設定合作對象解析的接收位置</span><span class="sxs-lookup"><span data-stu-id="75c89-107">To configure the receive location for party resolution using certificates</span></span>  
  
### <a name="to-install-the-certificates-in-the-certificates-store-to-receive-signed-messages"></a><span data-ttu-id="75c89-108">在憑證存放區中安裝憑證以接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="75c89-108">To install the certificates in the certificates store to receive signed messages</span></span>  
  
1.  <span data-ttu-id="75c89-109">夥伴 A 從憑證授權單位 (CA) 要求數位簽章的私密-公開金鑰組。</span><span class="sxs-lookup"><span data-stu-id="75c89-109">Partner A requests a private-public key pair for digital signatures from the certification authority (CA).</span></span>  
  
2.  <span data-ttu-id="75c89-110">夥伴 A 將其數位簽章的公開金鑰傳送給您。</span><span class="sxs-lookup"><span data-stu-id="75c89-110">Partner A sends you its public key for digital signatures.</span></span>  
  
3.  <span data-ttu-id="75c89-111">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，登入有執行處理常式之主控件執行個體的伺服器 (此處理常式將會從夥伴 A 接收訊息)。安裝夥伴 A 公開金鑰憑證，以驗證其在「其他人」存放區中的簽章。</span><span class="sxs-lookup"><span data-stu-id="75c89-111">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], log on to the server that has a host instance running a handler that will receive messages from Partner A. Install the Partner A public key certificate to verify their signature in the Other People store.</span></span> <span data-ttu-id="75c89-112">下圖顯示您安裝此憑證的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="75c89-112">The following figure shows the certificate store where you install the certificate.</span></span>  
  
     <span data-ttu-id="75c89-113">![接收安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span><span class="sxs-lookup"><span data-stu-id="75c89-113">![Certificates required to receive secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span></span>  
  
4.  <span data-ttu-id="75c89-114">在夥伴 A 中，安裝夥伴 A 私密金鑰憑證，在適當的存放區中簽署訊息</span><span class="sxs-lookup"><span data-stu-id="75c89-114">In Partner A, install the Partner A private key certificate for signing messages in the appropriate store.</span></span> <span data-ttu-id="75c89-115">(如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在要用於簽署傳送給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的訊息的帳戶之個人存放區中，安裝私密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="75c89-115">(If Partner A is using [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)], or [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)], or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], install the private key in the personal store for the account that will sign messages sent to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75c89-116">這個步驟是完全相同的步驟以安裝憑證來接收簽署的訊息的憑證存放區 」 中[如何安裝數位簽章的憑證](../core/how-to-install-the-certificates-for-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="75c89-116">This step is exactly same as the step "To install the certificates in the certificates store to receive signed messages" in [How to install the Certificates for Digital Signatures](../core/how-to-install-the-certificates-for-digital-signatures.md).</span></span>  
  
### <a name="to-create-a-party-to-represent-your-partner"></a><span data-ttu-id="75c89-117">建立代表夥伴的合作對象</span><span class="sxs-lookup"><span data-stu-id="75c89-117">To create a party to represent your partner</span></span>  
  
1.  <span data-ttu-id="75c89-118">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，建立夥伴 a 的合作對象如需如何建立合作對象的詳細資訊，請參閱[如何建立合作對象](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044)。</span><span class="sxs-lookup"><span data-stu-id="75c89-118">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a party for the Partner A. For more information about how to create a Party, see [How to Create a Party](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044).</span></span>  
  
2.  <span data-ttu-id="75c89-119">在**憑證**屬性中，選取簽署憑證，用來識別此合作對象，夥伴 a 公開金鑰</span><span class="sxs-lookup"><span data-stu-id="75c89-119">In the **Certificates** properties, select the public key signing certificate to use to identify this party, Partner A.</span></span>  
  
### <a name="to-create-a-pipeline-for-party-resolution-using-certificates"></a><span data-ttu-id="75c89-120">使用憑證建立合作對象解析的管線</span><span class="sxs-lookup"><span data-stu-id="75c89-120">To create a pipeline for party resolution using certificates</span></span>  
  
1.  <span data-ttu-id="75c89-121">在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，選取您要在其中建立管線的專案。</span><span class="sxs-lookup"><span data-stu-id="75c89-121">In Solution Explorer in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select the project in which you want to create the pipeline.</span></span>  
  
    1.  <span data-ttu-id="75c89-122">在**檔案**功能表上，按一下 **加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="75c89-122">On the **File** menu, click **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="75c89-123">在**加入新項目**對話方塊方塊中，展開 BizTalk 專案項目，按一下**管線檔案**，然後按一下 **接收管線**範本。</span><span class="sxs-lookup"><span data-stu-id="75c89-123">In the **Add New Item** dialog box, expand BizTalk Project Items, click **Pipeline Files**, and then click the **Receive Pipeline** template.</span></span>  
  
    3.  <span data-ttu-id="75c89-124">在**名稱**欄位中，輸入管線的名稱。</span><span class="sxs-lookup"><span data-stu-id="75c89-124">In the **Name** field, type a name for the pipeline.</span></span>  
  
    4.  <span data-ttu-id="75c89-125">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="75c89-125">Click **Add**.</span></span>  
  
         <span data-ttu-id="75c89-126">新管線隨即出現在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="75c89-126">The new pipeline appears in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="75c89-127">將 MIME/SMIME 解碼器管線元件拖曳**解碼**接收管線階段。</span><span class="sxs-lookup"><span data-stu-id="75c89-127">Drag the MIME/SMIME Decoder pipeline component into the **Decode** stage of a receive pipeline.</span></span>  
  
     <span data-ttu-id="75c89-128">![MIME &#47;SMIME 解碼器管線元件](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")</span><span class="sxs-lookup"><span data-stu-id="75c89-128">![MIME&#47;SMIME Decoder pipeline component](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")</span></span>  
  
    -   <span data-ttu-id="75c89-129">設定 MIME/SMIME 解碼器管線元件屬性中的**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="75c89-129">Configure the MIME/SMIME Decoder pipeline component properties in the **Properties** window.</span></span> <span data-ttu-id="75c89-130">如需 MIME/SMIME 解碼器的詳細資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="75c89-130">For more information about the MIME/SMIME decoder, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75c89-131">當您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台將此管線部署到 BizTalk 群組後，您可以為接收位置設定管線屬性。</span><span class="sxs-lookup"><span data-stu-id="75c89-131">You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="75c89-132">您可以針對 BizTalk 群組中的每一個接收位置設定不同的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="75c89-132">You can configure different pipeline properties for each receive location in the BizTalk group.</span></span> <span data-ttu-id="75c89-133">如需詳細資訊，請參閱[如何設定接收位置的每個執行個體管線屬性](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="75c89-133">For more information, see [How to Configure Per-instance Pipeline Properties for a Receive Location](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75c89-134">MIME/SMIME 解碼器管線元件會執行解密及數位簽章驗證 (當設定為執行這兩項功能時)。</span><span class="sxs-lookup"><span data-stu-id="75c89-134">The MIME/SMIME Decoder pipeline component performs both decryption and digital signature validation (when configured to perform both functions).</span></span> <span data-ttu-id="75c89-135">因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來接收加密及簽署的訊息，您可以使用相同的接收管線。</span><span class="sxs-lookup"><span data-stu-id="75c89-135">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted and signed messages, you can use the same receive pipeline.</span></span> <span data-ttu-id="75c89-136">換句話說，您不需要針對解密和數位簽章驗證建立個別的管線。</span><span class="sxs-lookup"><span data-stu-id="75c89-136">In other words, you do not have to create separate pipelines for decryption and digital signature validation.</span></span>  
  
3.  <span data-ttu-id="75c89-137">將合作對象解析管線元件拖曳**解析合作對象**接收管線階段。</span><span class="sxs-lookup"><span data-stu-id="75c89-137">Drag the Party Resolution pipeline component into the **ResolveParty** stage of a receive pipeline.</span></span> <span data-ttu-id="75c89-138">如需 「 合作對象解析 」 管線元件的詳細資訊，請參閱[如何設定合作對象解析管線元件](../core/how-to-configure-the-party-resolution-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="75c89-138">For more information about the Party Resolution pipeline component, see [How to Configure the Party Resolution Pipeline Component](../core/how-to-configure-the-party-resolution-pipeline-component.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75c89-139">您也可以使用預設的 XMLReceive 管線，而不需要建立新的接收管線。</span><span class="sxs-lookup"><span data-stu-id="75c89-139">You can also use the default XMLReceive pipeline instead of creating a new receive pipeline.</span></span> <span data-ttu-id="75c89-140">XMLReceive 管線會執行合作對象解析元件，它會解析合作對象識別碼。 可能的憑證</span><span class="sxs-lookup"><span data-stu-id="75c89-140">The XMLReceive pipeline runs the Party Resolution component, which resolves the certificate subject to the party ID.</span></span> <span data-ttu-id="75c89-141">請注意，XMLReceive 管線有有空的解碼階段，因此您不能使用它接收加密的訊息或驗證數位簽章。</span><span class="sxs-lookup"><span data-stu-id="75c89-141">Note that the XMLReceive pipeline has an empty Decode stage, and therefore you cannot use it for receiving encrypted messages or verifying digital signatures.</span></span>  
  
    -   <span data-ttu-id="75c89-142">在 [屬性] 視窗中設定合作對象解析管線屬性**依憑證解析合作對象**至`True`。</span><span class="sxs-lookup"><span data-stu-id="75c89-142">In the Properties window, configure the Party Resolution pipeline property **Resolve party by certificate** to `True`.</span></span>  
  
4.  <span data-ttu-id="75c89-143">建置和部署接收管線。</span><span class="sxs-lookup"><span data-stu-id="75c89-143">Build and deploy the receive pipeline.</span></span>  
  
### <a name="to-configure-the-receive-location-for-party-resolution-using-certificates"></a><span data-ttu-id="75c89-144">使用憑證設定合作對象解析的接收位置</span><span class="sxs-lookup"><span data-stu-id="75c89-144">To configure the receive location for party resolution using certificates</span></span>  
  
1.  <span data-ttu-id="75c89-145">將您在上一個程序中所建立的 BizTalk 組件加入到 BizTalk 應用程式中，包括用來接收簽署之訊息的接收位置。</span><span class="sxs-lookup"><span data-stu-id="75c89-145">Add the BizTalk assembly that you created in previous procedure to the BizTalk Application including the receive locations to receive signed messages.</span></span> <span data-ttu-id="75c89-146">如需如何新增 BizTalk 組件的詳細資訊，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="75c89-146">For more information about how to add BizTalk assemblies, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
2.  <span data-ttu-id="75c89-147">使用您在前述程序中建立的接收管線，在 BizTalk 應用程式中設定接收位置。</span><span class="sxs-lookup"><span data-stu-id="75c89-147">Configure the receive locations in the BizTalk Application with the receive pipeline that you created in previous procedure.</span></span> <span data-ttu-id="75c89-148">如需有關如何設定接收位置，請參閱[如何編輯接收位置的內容](../core/how-to-edit-the-properties-of-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="75c89-148">For more information about how to configure receive locations, see [How to Edit the Properties of a Receive Location](../core/how-to-edit-the-properties-of-a-receive-location.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c89-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75c89-149">See Also</span></span>  
 <span data-ttu-id="75c89-150">[如何設定 BizTalk Server 來接收簽署的訊息](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="75c89-150">[How to Configure BizTalk Server for Receiving Signed Messages](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md) </span></span>  
 <span data-ttu-id="75c89-151">[BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="75c89-151">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 <span data-ttu-id="75c89-152">[輸入訊息驗證](../core/inbound-message-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="75c89-152">[Inbound Message Authentication](../core/inbound-message-authentication.md) </span></span>  
 [<span data-ttu-id="75c89-153">使用憑證進行合作對象解析</span><span class="sxs-lookup"><span data-stu-id="75c89-153">Using Certificates for Party Resolution</span></span>](../core/using-certificates-for-party-resolution.md)