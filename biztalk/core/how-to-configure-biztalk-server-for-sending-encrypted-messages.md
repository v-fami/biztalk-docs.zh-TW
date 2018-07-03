---
title: 如何設定 BizTalk Server 來傳送加密的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb751d7c-49cd-46f0-9630-254cf06c497e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49f7388e9f6b8e56397a3b6efdf466aec3383746
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023900"
---
# <a name="how-to-configure-biztalk-server-for-sending-encrypted-messages"></a><span data-ttu-id="614e3-102">如何設定 BizTalk Server 來傳送加密的訊息</span><span class="sxs-lookup"><span data-stu-id="614e3-102">How to Configure BizTalk Server for Sending Encrypted Messages</span></span>
<span data-ttu-id="614e3-103">下列程序列出在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送加密的訊息時，所必須遵循的步驟。</span><span class="sxs-lookup"><span data-stu-id="614e3-103">The following procedure lists the steps that you have to follow to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted messages.</span></span>  
  
-   <span data-ttu-id="614e3-104">建立管線來傳送加密的訊息</span><span class="sxs-lookup"><span data-stu-id="614e3-104">To create a pipeline to send encrypted messages</span></span>  
  
-   <span data-ttu-id="614e3-105">設定傳送埠來傳送加密的訊息</span><span class="sxs-lookup"><span data-stu-id="614e3-105">To configure the send port for sending encrypted messages</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="614e3-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="614e3-106">Prerequisites</span></span>  
 <span data-ttu-id="614e3-107">在設定之前先[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來傳送加密的訊息，您必須執行中的步驟[如何安裝加密訊息的憑證](../core/how-to-install-the-certificates-for-encrypted-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="614e3-107">Before configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s for sending encrypted messages, you must perform the steps in [How to Install the Certificates for Encrypted Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span></span>  
  
### <a name="to-create-a-pipeline-to-send-encrypted-messages"></a><span data-ttu-id="614e3-108">建立管線來傳送加密的訊息</span><span class="sxs-lookup"><span data-stu-id="614e3-108">To create a pipeline to send encrypted messages</span></span>  
  
1. <span data-ttu-id="614e3-109">在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，選取您要在其中建立管線的專案。</span><span class="sxs-lookup"><span data-stu-id="614e3-109">In Solution Explorer in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select the project in which you want to create the pipeline.</span></span>  
  
   1.  <span data-ttu-id="614e3-110">在 **檔案**功能表上，按一下**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="614e3-110">On the **File** menu, click **Add New Item**.</span></span>  
  
   2.  <span data-ttu-id="614e3-111">在 **加入新項目**對話方塊方塊中，展開 BizTalk 專案項目，按一下 **管線檔案**，然後按一下 **傳送管線**範本。</span><span class="sxs-lookup"><span data-stu-id="614e3-111">In the **Add New Item** dialog box, expand BizTalk Project Items, click **Pipeline Files**, and then click the **Send Pipeline** template.</span></span>  
  
   3.  <span data-ttu-id="614e3-112">在 **名稱**欄位中，輸入管線的名稱。</span><span class="sxs-lookup"><span data-stu-id="614e3-112">In the **Name** field, type a name for the pipeline.</span></span>  
  
   4.  <span data-ttu-id="614e3-113">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="614e3-113">Click **Add**.</span></span>  
  
        <span data-ttu-id="614e3-114">新管線隨即出現在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="614e3-114">The new pipeline appears in Solution Explorer.</span></span>  
  
2. <span data-ttu-id="614e3-115">將 MIME/SMIME 編碼器管線元件拖曳至接收管線的「編碼」階段中。</span><span class="sxs-lookup"><span data-stu-id="614e3-115">Drag the MIME/SMIME Encoder pipeline component into the Encode stage of a receive pipeline.</span></span>  
  
    <span data-ttu-id="614e3-116">![MIME&#47;SMIME 編碼器管線元件](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")</span><span class="sxs-lookup"><span data-stu-id="614e3-116">![MIME&#47;SMIME Encoder pipeline component](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")</span></span>  
  
   -   <span data-ttu-id="614e3-117">在 屬性 視窗中，設定 MIME/SMIME 編碼器管線元件**啟用加密**屬性設`True`。</span><span class="sxs-lookup"><span data-stu-id="614e3-117">In the Properties window, configure the MIME/SMIME Encoder pipeline component **Enable encryption** property to `True`.</span></span> <span data-ttu-id="614e3-118">如需詳細資訊**啟用加密**屬性，請參閱[如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="614e3-118">For more information about the **Enable encryption** property, see [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md).</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="614e3-119">將管線部署至 BizTalk 群組之後，您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定管線元件屬性。</span><span class="sxs-lookup"><span data-stu-id="614e3-119">You can configure the send pipeline component properties using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console after the pipeline has been deployed into a BizTalk group.</span></span> <span data-ttu-id="614e3-120">如需詳細資訊，請參閱 <<c0> [ 如何設定每個執行個體管線屬性的傳送埠](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="614e3-120">For more information, see [How to Configure Per-Instance Pipeline Properties for a Send Port](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md).</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="614e3-121">MIME/SMIME 編碼器管線元件會執行加密及數位簽章 (當設定為執行這兩項功能時)。</span><span class="sxs-lookup"><span data-stu-id="614e3-121">The MIME/SMIME Encoder pipeline component performs both encryption and digital signing (when configured to perform both functions).</span></span> <span data-ttu-id="614e3-122">因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送已加密及已簽署的訊息，可以使用相同的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="614e3-122">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted and signed messages, you can use the same send pipeline.</span></span> <span data-ttu-id="614e3-123">也就是說，您不需要針對加密和數位簽章建立個別的管線。</span><span class="sxs-lookup"><span data-stu-id="614e3-123">In other words, you do not have to create separate pipelines for encryption and digital signing.</span></span>  
  
3. <span data-ttu-id="614e3-124">建置和部署傳送管線。</span><span class="sxs-lookup"><span data-stu-id="614e3-124">Build and deploy the send pipeline.</span></span>  
  
### <a name="to-configure-the-send-port-for-sending-encrypted-messages"></a><span data-ttu-id="614e3-125">設定傳送埠來傳送加密的訊息</span><span class="sxs-lookup"><span data-stu-id="614e3-125">To configure the send port for sending encrypted messages</span></span>  
  
1.  <span data-ttu-id="614e3-126">將您在上一個程序中所建立的 BizTalk 組件加入到 BizTalk 應用程式中，包括用來傳送加密訊息的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="614e3-126">Add the BizTalk assembly that you created in previous procedure to the BizTalk Application including the send ports to send encrypted messages.</span></span> <span data-ttu-id="614e3-127">如需如何新增 BizTalk 組件的詳細資訊，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="614e3-127">For more information about how to add BizTalk assemblies, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
2.  <span data-ttu-id="614e3-128">您在先前的程序中建立的傳送管線的 BizTalk 應用程式中設定的傳送埠，然後將指派的加密憑證，您在安裝[如何安裝的憑證加密的訊息](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span><span class="sxs-lookup"><span data-stu-id="614e3-128">Configure the send port in the BizTalk Application with the send pipeline that you created in previous procedure, and then assign the encryption certificate that you installed in [How to Install the Certificates for Encrypted Messages](../core/how-to-install-the-certificates-for-encrypted-messages.md).</span></span> <span data-ttu-id="614e3-129">如需如何設定傳送埠的詳細資訊，請參閱[如何指派憑證給傳送埠](../core/how-to-assign-a-certificate-to-a-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="614e3-129">For more information about how to configure send ports, see [How to Assign a Certificate to a Send Port](../core/how-to-assign-a-certificate-to-a-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="614e3-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="614e3-130">See Also</span></span>  
 <span data-ttu-id="614e3-131">[如何設定 BizTalk Server 來接收加密的訊息](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="614e3-131">[How to Configure BizTalk Server for Receiving Encrypted Messages](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md) </span></span>  
 <span data-ttu-id="614e3-132">[BizTalk Server 用於加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="614e3-132">[Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span></span>  
 [<span data-ttu-id="614e3-133">傳送和接收加密訊息</span><span class="sxs-lookup"><span data-stu-id="614e3-133">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)