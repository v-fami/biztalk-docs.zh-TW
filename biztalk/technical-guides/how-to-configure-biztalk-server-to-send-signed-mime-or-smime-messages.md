---
title: 如何設定 BizTalk Server 來傳送簽署 MIME 或 SMIME 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba42463b-2c12-4329-919e-aca427d14eee
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 623e8e6349494ce1d15089093b1620b4da76adbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297870"
---
# <a name="how-to-configure-biztalk-server-to-send-signed-mime-or-smime-messages"></a><span data-ttu-id="67f21-102">如何設定 BizTalk Server 來傳送簽署 MIME 或 SMIME 訊息</span><span class="sxs-lookup"><span data-stu-id="67f21-102">How to Configure BizTalk Server to Send Signed MIME or SMIME Messages</span></span>
<span data-ttu-id="67f21-103">本主題描述如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以使用憑證來傳送簽署的 MIME/SMIME 訊息。</span><span class="sxs-lookup"><span data-stu-id="67f21-103">This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use certificates to send signed MIME/SMIME messages.</span></span> <span data-ttu-id="67f21-104">下列程序也適用於設定透過 AS2 傳輸的簽章訊息傳送。</span><span class="sxs-lookup"><span data-stu-id="67f21-104">The procedure below also applies to configuring the sending of signed messages over AS2 transport.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="67f21-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="67f21-105">Prerequisites</span></span>  
 <span data-ttu-id="67f21-106">若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="67f21-106">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-signed-messages"></a><span data-ttu-id="67f21-107">若要設定 BizTalk Server 來傳送簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="67f21-107">To configure BizTalk Server to send signed messages</span></span>  
  
1.  <span data-ttu-id="67f21-108">建立管線來傳送簽署的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67f21-108">Create a pipeline to send signed messages, as follows:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67f21-109">設定 AS2 傳輸來傳送簽署的訊息的 AS2Send 和 AS2EdiSend 管線，因為包含在這個步驟並非必要[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]做這個函式。</span><span class="sxs-lookup"><span data-stu-id="67f21-109">This step is not necessary when configuring AS2 transport for sending signed messages because the AS2Send and AS2EdiSend pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.</span></span>  
  
    1.  <span data-ttu-id="67f21-110">建立傳送管線，然後將 MIME/SMIME 編碼器管線元件拖曳到管線的 「 編碼 」 階段。</span><span class="sxs-lookup"><span data-stu-id="67f21-110">Create a send pipeline and then drag the MIME/SMIME Encoder pipeline component into the Encode stage of the pipeline.</span></span>  
  
    2.  <span data-ttu-id="67f21-111">在**屬性**視窗中，設定 MIME/SMIME 編碼器管線元件簽章類型屬性 ClearSign 或 BlobSign。</span><span class="sxs-lookup"><span data-stu-id="67f21-111">In the **Properties** window, configure the MIME/SMIME Encoder pipeline component Signature type property to ClearSign or BlobSign.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67f21-112">如果您也要使用加密，您可以只選取 BlobSign。</span><span class="sxs-lookup"><span data-stu-id="67f21-112">If you are also using encryption, you can only select BlobSign.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67f21-113">將管線部署至 BizTalk 群組之後，您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定管線元件屬性。</span><span class="sxs-lookup"><span data-stu-id="67f21-113">You can configure the send pipeline component properties using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console after the pipeline has been deployed into a BizTalk group.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67f21-114">MIME/SMIME 編碼器管線元件會執行加密及數位簽章 (當設定為執行這兩項功能時)。</span><span class="sxs-lookup"><span data-stu-id="67f21-114">The MIME/SMIME Encoder pipeline component performs both encryption and digital signing (when configured to perform both functions).</span></span> <span data-ttu-id="67f21-115">因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送已加密及已簽署的訊息，可以使用相同的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="67f21-115">Therefore, if you are configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send encrypted and signed messages, you can use the same send pipeline.</span></span> <span data-ttu-id="67f21-116">也就是說，您不需要針對加密和數位簽章建立個別的管線。</span><span class="sxs-lookup"><span data-stu-id="67f21-116">In other words, you do not have to create separate pipelines for encryption and digital signing.</span></span>  
  
    3.  <span data-ttu-id="67f21-117">建置和部署傳送管線。</span><span class="sxs-lookup"><span data-stu-id="67f21-117">Build and deploy the send pipeline.</span></span>  
  
2.  <span data-ttu-id="67f21-118">設定傳送埠來傳送簽署的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67f21-118">Configure the send port for sending signed messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="67f21-119">將您建立包含 BizTalk 應用程式，其中包含傳送埠來傳送簽署的訊息的傳送管線的 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="67f21-119">Add the BizTalk assembly that you created containing the send pipeline to the BizTalk application that includes the send ports to send signed messages.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67f21-120">設定 AS2 傳輸來傳送簽署訊息，因為在 「 BizTalk EDI 應用程式中包含的 AS2Send 和 AS2EdiSend 管線時，不需要這個步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67f21-120">This step is not necessary when configuring AS2 transport for sending signed messages because the AS2Send and AS2EdiSend pipelines are included in the BizTalk EDI Application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="67f21-121">您在上一個程序中建立的傳送管線的 BizTalk 應用程式中設定的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="67f21-121">Configure the send port in the BizTalk application with the send pipeline that you created in the previous procedure.</span></span>  
  
3.  <span data-ttu-id="67f21-122">設定群組的憑證來傳送簽署的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67f21-122">Configure the group with a certificate for sending signed messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="67f21-123">設定 BizTalk 群組，展開 BizTalk 群組，在您安裝的簽章憑證[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="67f21-123">Configure the BizTalk group with the signing certificate that you installed by expanding the BizTalk group in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-clicking **BizTalk Group**, and then clicking **Properties**.</span></span>  
  
    2.  <span data-ttu-id="67f21-124">按一下 憑證 索引標籤，再按一下**瀏覽**選取適當的憑證，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="67f21-124">Click the Certificate tab, click **Browse**, select the appropriate certificate, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f21-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67f21-125">See Also</span></span>  
 [<span data-ttu-id="67f21-126">設定 MIME 或 SMIME 訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="67f21-126">Configuring Certificates for MIME or SMIME Messages</span></span>](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)