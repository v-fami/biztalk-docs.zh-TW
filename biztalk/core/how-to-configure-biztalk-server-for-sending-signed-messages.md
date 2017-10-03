---
title: "如何設定 BizTalk Server 來傳送簽署的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be86fbb3-de80-4d9f-bcf0-c61347704229
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef71f5c11d6c1a000369644b822aa9f4d4ef792
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-for-sending-signed-messages"></a><span data-ttu-id="6ab09-102">如何設定 BizTalk Server 來傳送簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="6ab09-102">How to Configure BizTalk Server for Sending Signed Messages</span></span>
<span data-ttu-id="6ab09-103">下列程序列出在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送已簽署的訊息時，所必須遵循的步驟。</span><span class="sxs-lookup"><span data-stu-id="6ab09-103">The following procedure lists the steps that you have to follow to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send signed messages.</span></span>  
  
-   <span data-ttu-id="6ab09-104">若要建立管線來傳送簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="6ab09-104">To create a pipeline to send signed messages</span></span>  
  
-   <span data-ttu-id="6ab09-105">若要設定傳送埠來傳送簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="6ab09-105">To configure the send port for sending signed messages</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6ab09-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="6ab09-106">Prerequisites</span></span>  
 <span data-ttu-id="6ab09-107">然後再設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s 傳送簽署的訊息，您必須執行中的步驟[如何安裝數位簽章的憑證](../core/how-to-install-the-certificates-for-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab09-107">Before configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s for sending signed messages, you must perform the steps in [How to install the Certificates for Digital Signatures](../core/how-to-install-the-certificates-for-digital-signatures.md).</span></span>  
  
### <a name="to-create-a-pipeline-to-send-signed-messages"></a><span data-ttu-id="6ab09-108">若要建立管線來傳送簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="6ab09-108">To create a pipeline to send signed messages</span></span>  
  
1.  <span data-ttu-id="6ab09-109">在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，選取您要在其中建立管線的專案。</span><span class="sxs-lookup"><span data-stu-id="6ab09-109">In Solution Explorer in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select the project in which you want to create the pipeline.</span></span>  
  
    1.  <span data-ttu-id="6ab09-110">在**檔案**功能表上，按一下 **加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="6ab09-110">On the **File** menu, click **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="6ab09-111">在**加入新項目**對話方塊方塊中，展開 BizTalk 專案項目，按一下**管線檔案**，然後按一下 **傳送管線**範本。</span><span class="sxs-lookup"><span data-stu-id="6ab09-111">In the **Add New Item** dialog box, expand BizTalk Project Items, click **Pipeline Files**, and then click the **Send Pipeline** template.</span></span>  
  
    3.  <span data-ttu-id="6ab09-112">在**名稱**欄位中，輸入管線的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ab09-112">In the **Name** field, type a name for the pipeline.</span></span>  
  
    4.  <span data-ttu-id="6ab09-113">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="6ab09-113">Click **Add**.</span></span>  
  
         <span data-ttu-id="6ab09-114">新管線隨即出現在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="6ab09-114">The new pipeline appears in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="6ab09-115">將 MIME/SMIME 編碼器管線元件拖曳至接收管線的「編碼」階段中。</span><span class="sxs-lookup"><span data-stu-id="6ab09-115">Drag the MIME/SMIME Encoder pipeline component into the Encode stage of a receive pipeline.</span></span>  
  
     <span data-ttu-id="6ab09-116">![MIME &#47;SMIME 編碼器管線元件](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")</span><span class="sxs-lookup"><span data-stu-id="6ab09-116">![MIME&#47;SMIME Encoder pipeline component](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")</span></span>  
  
3.  <span data-ttu-id="6ab09-117">在 [屬性] 視窗中設定 MIME/SMIME 編碼器管線元件**簽章類型**屬性**ClearSign**或**BlobSign**。</span><span class="sxs-lookup"><span data-stu-id="6ab09-117">In the Properties window, configure the MIME/SMIME Encoder pipeline component **Signature type** property to **ClearSign**or **BlobSign**.</span></span> <span data-ttu-id="6ab09-118">如需有關**啟用加密**屬性，請參閱[如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab09-118">For more information about the **Enable encryption** property, see [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6ab09-119">如果您也要使用加密，您只能選取**BlobSign**。</span><span class="sxs-lookup"><span data-stu-id="6ab09-119">If you are also using encryption, you can only select **BlobSign**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ab09-120">將管線部署至 BizTalk 群組之後，您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定管線元件屬性。</span><span class="sxs-lookup"><span data-stu-id="6ab09-120">You can configure the send pipeline component properties using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console after the pipeline has been deployed into a BizTalk group.</span></span> <span data-ttu-id="6ab09-121">如需詳細資訊，請參閱[的傳送埠中設定每個執行個體管線屬性如何](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab09-121">For more information, see [How to Configure Per-Instance Pipeline Properties for a Send Port](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ab09-122">MIME/SMIME 編碼器管線元件會執行加密及數位簽章 (當設定為執行這兩項功能時)。</span><span class="sxs-lookup"><span data-stu-id="6ab09-122">The MIME/SMIME Encoder pipeline component performs both encryption and digital signing (when configured to perform both functions).</span></span> <span data-ttu-id="6ab09-123">因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送已加密及已簽署的訊息，可以使用相同的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="6ab09-123">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted and signed messages, you can use the same send pipeline.</span></span> <span data-ttu-id="6ab09-124">也就是說，您不需要針對加密和數位簽章建立個別的管線。</span><span class="sxs-lookup"><span data-stu-id="6ab09-124">In other words, you do not have to create separate pipelines for encryption and digital signing.</span></span>  
  
4.  <span data-ttu-id="6ab09-125">建置和部署傳送管線。</span><span class="sxs-lookup"><span data-stu-id="6ab09-125">Build and deploy the send pipeline.</span></span>  
  
### <a name="to-configure-the-send-port-for-sending-signed-messages"></a><span data-ttu-id="6ab09-126">若要設定傳送埠來傳送簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="6ab09-126">To configure the send port for sending signed messages</span></span>  
  
1.  <span data-ttu-id="6ab09-127">將您在前述程序中建立的 BizTalk 組件加入到 BizTalk 應用程式中，包括用來傳送已簽署訊息的接收位置。</span><span class="sxs-lookup"><span data-stu-id="6ab09-127">Add the BizTalk assembly that you created in previous procedure to the BizTalk Application including the receive locations to sending signed messages.</span></span> <span data-ttu-id="6ab09-128">如需如何新增 BizTalk 組件的詳細資訊，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab09-128">For more information about how to add BizTalk assemblies, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
2.  <span data-ttu-id="6ab09-129">使用您在前述程序中建立的傳送管線，在 BizTalk 應用程式中設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6ab09-129">Configure the send port in the BizTalk Application with the send pipeline that you created in previous procedure.</span></span> <span data-ttu-id="6ab09-130">如需如何設定傳送埠的詳細資訊，請參閱[建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab09-130">For more information about how to configure send ports, see [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md).</span></span>  
  
3.  <span data-ttu-id="6ab09-131">設定 BizTalk 群組的簽章的憑證，您在安裝[如何安裝數位簽章的憑證](../core/how-to-install-the-certificates-for-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab09-131">Configure the BizTalk group with the signing certificate that you installed in [How to install the Certificates for Digital Signatures](../core/how-to-install-the-certificates-for-digital-signatures.md).</span></span> <span data-ttu-id="6ab09-132">如需如何設定 BizTalk 群組，請參閱[如何修改群組內容](../core/how-to-modify-group-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab09-132">For more information how to configure a BizTalk group, see [How to Modify Group Properties](../core/how-to-modify-group-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ab09-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ab09-133">See Also</span></span>  
 <span data-ttu-id="6ab09-134">[如何設定 BizTalk Server 來接收簽署的訊息](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="6ab09-134">[How to Configure BizTalk Server for Receiving Signed Messages](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md) </span></span>  
 <span data-ttu-id="6ab09-135">[BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="6ab09-135">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 [<span data-ttu-id="6ab09-136">傳送及接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="6ab09-136">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)