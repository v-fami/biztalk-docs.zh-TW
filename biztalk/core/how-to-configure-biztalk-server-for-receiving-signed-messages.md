---
title: 如何設定 BizTalk Server 來接收簽署的訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48479532-24a9-41d9-a3b8-2a23f4e76457
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 814aa3f25866f18a1d7fe536bc47a996f286916d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249094"
---
# <a name="how-to-configure-biztalk-server-for-receiving-signed-messages"></a><span data-ttu-id="8f589-102">如何設定 BizTalk Server 來接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="8f589-102">How to Configure BizTalk Server for Receiving Signed Messages</span></span>
<span data-ttu-id="8f589-103">下列程序列出在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 以接收加密訊息時，所必須遵循的步驟。</span><span class="sxs-lookup"><span data-stu-id="8f589-103">The following procedure lists the steps that you have to follow to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted messages.</span></span>  
  
-   <span data-ttu-id="8f589-104">若要建立管線來接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="8f589-104">To create a pipeline to receive signed messages</span></span>  
  
-   <span data-ttu-id="8f589-105">若要設定接收簽署之訊息的接收位置</span><span class="sxs-lookup"><span data-stu-id="8f589-105">To configure the receive location for receiving signed messages</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f589-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="8f589-106">Prerequisites</span></span>  
 <span data-ttu-id="8f589-107">然後再設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來接收簽署的訊息，您必須執行中的步驟[如何安裝數位簽章的憑證](../core/how-to-install-the-certificates-for-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="8f589-107">Before configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s for receiving signed messages, you must perform the steps in [How to install the Certificates for Digital Signatures](../core/how-to-install-the-certificates-for-digital-signatures.md).</span></span>  
  
### <a name="to-create-a-pipeline-to-receive-signed-messages"></a><span data-ttu-id="8f589-108">若要建立管線來接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="8f589-108">To create a pipeline to receive signed messages</span></span>  
  
1.  <span data-ttu-id="8f589-109">在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，選取您要在其中建立管線的專案。</span><span class="sxs-lookup"><span data-stu-id="8f589-109">In Solution Explorer in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select the project in which you want to create the pipeline.</span></span>  
  
    1.  <span data-ttu-id="8f589-110">在**檔案**功能表上，按一下 **加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="8f589-110">On the **File** menu, click **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="8f589-111">在**加入新項目**對話方塊方塊中，展開 BizTalk 專案項目，按一下**管線檔案**，然後按一下 **接收管線**範本。</span><span class="sxs-lookup"><span data-stu-id="8f589-111">In the **Add New Item** dialog box, expand BizTalk Project Items, click **Pipeline Files**, and then click the **Receive Pipeline** template.</span></span>  
  
    3.  <span data-ttu-id="8f589-112">在**名稱**欄位中，輸入管線的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f589-112">In the **Name** field, type a name for the pipeline.</span></span>  
  
    4.  <span data-ttu-id="8f589-113">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="8f589-113">Click **Add**.</span></span>  
  
         <span data-ttu-id="8f589-114">新管線隨即出現在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="8f589-114">The new pipeline appears in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="8f589-115">將 MIME/SMIME 解碼器管線元件拖曳**解碼**接收管線階段。</span><span class="sxs-lookup"><span data-stu-id="8f589-115">Drag the MIME/SMIME Decoder pipeline component into the **Decode** stage of a receive pipeline.</span></span>  
  
     <span data-ttu-id="8f589-116">![MIME &#47;SMIME 解碼器管線元件](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")</span><span class="sxs-lookup"><span data-stu-id="8f589-116">![MIME&#47;SMIME Decoder pipeline component](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")</span></span>  
  
    -   <span data-ttu-id="8f589-117">設定 MIME/SMIME 解碼器管線元件屬性中的**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="8f589-117">Configure the MIME/SMIME Decoder pipeline component properties in the **Properties** window.</span></span> <span data-ttu-id="8f589-118">如需 MIME/SMIME 解碼器的詳細資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8f589-118">For more information about the MIME/SMIME decoder, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f589-119">當您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台將此管線部署到 BizTalk 群組後，您可以為接收位置設定管線屬性。</span><span class="sxs-lookup"><span data-stu-id="8f589-119">You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="8f589-120">您可以針對 BizTalk 群組中的每一個接收位置設定不同的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="8f589-120">You can configure different pipeline properties for each receive location in the BizTalk group.</span></span> <span data-ttu-id="8f589-121">如需詳細資訊，請參閱[如何設定接收位置的每個執行個體管線屬性](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="8f589-121">For more information, see [How to Configure Per-instance Pipeline Properties for a Receive Location](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f589-122">MIME/SMIME 解碼器管線元件會執行解密及數位簽章驗證 (當設定為執行這兩項功能時)。</span><span class="sxs-lookup"><span data-stu-id="8f589-122">The MIME/SMIME Decoder pipeline component performs both decryption and digital signature validation (when configured to perform both functions).</span></span> <span data-ttu-id="8f589-123">因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來接收加密及簽署的訊息，您可以使用相同的接收管線。</span><span class="sxs-lookup"><span data-stu-id="8f589-123">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive encrypted and signed messages, you can use the same receive pipeline.</span></span> <span data-ttu-id="8f589-124">換句話說，您不需要針對解密和數位簽章驗證建立個別的管線。</span><span class="sxs-lookup"><span data-stu-id="8f589-124">In other words, you do not have to create separate pipelines for decryption and digital signature validation.</span></span>  
  
3.  <span data-ttu-id="8f589-125">建置和部署接收管線。</span><span class="sxs-lookup"><span data-stu-id="8f589-125">Build and deploy the receive pipeline.</span></span>  
  
### <a name="to-configure-the-receive-location-for-receiving-signed-messages"></a><span data-ttu-id="8f589-126">若要設定接收簽署之訊息的接收位置</span><span class="sxs-lookup"><span data-stu-id="8f589-126">To configure the receive location for receiving signed messages</span></span>  
  
1.  <span data-ttu-id="8f589-127">將您在上一個程序中所建立的 BizTalk 組件加入到 BizTalk 應用程式中，包括用來接收簽署之訊息的接收位置。</span><span class="sxs-lookup"><span data-stu-id="8f589-127">Add the BizTalk assembly that you created in previous procedure to the BizTalk Application including the receive locations to receive signed messages.</span></span> <span data-ttu-id="8f589-128">如需如何新增 BizTalk 組件的詳細資訊，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8f589-128">For more information about how to add BizTalk assemblies, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
2.  <span data-ttu-id="8f589-129">使用您在前述程序中建立的接收管線，在 BizTalk 應用程式中設定接收位置。</span><span class="sxs-lookup"><span data-stu-id="8f589-129">Configure the receive locations in the BizTalk Application with the receive pipeline that you created in previous procedure.</span></span> <span data-ttu-id="8f589-130">如需有關如何設定接收位置，請參閱[如何編輯接收位置的內容](../core/how-to-edit-the-properties-of-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="8f589-130">For more information about how to configure receive locations, see [How to Edit the Properties of a Receive Location](../core/how-to-edit-the-properties-of-a-receive-location.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f589-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f589-131">See Also</span></span>  
 <span data-ttu-id="8f589-132">[BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="8f589-132">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 <span data-ttu-id="8f589-133">[如何設定 BizTalk Server 來傳送簽署的訊息](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="8f589-133">[How to Configure BizTalk Server for Sending Signed Messages](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md) </span></span>  
 <span data-ttu-id="8f589-134">[驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md) </span><span class="sxs-lookup"><span data-stu-id="8f589-134">[Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md) </span></span>  
 [<span data-ttu-id="8f589-135">傳送及接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="8f589-135">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)