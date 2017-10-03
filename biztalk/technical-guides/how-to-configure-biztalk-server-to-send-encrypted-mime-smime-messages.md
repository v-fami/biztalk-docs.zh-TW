---
title: "如何設定 BizTalk Server 來傳送加密的 MIME/SMIME 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f67152-5f80-4040-a9d6-0819fab7fcb5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c83b5f28ac3716376aa93cff22f933363825615e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-send-encrypted-mimesmime-messages"></a><span data-ttu-id="681fe-102">如何設定 BizTalk Server 傳送加密的 MIME/SMIME 訊息</span><span class="sxs-lookup"><span data-stu-id="681fe-102">How to Configure BizTalk Server to Send Encrypted MIME/SMIME Messages</span></span>
<span data-ttu-id="681fe-103">本主題描述如何設定 BizTalk Server 以使用憑證來傳送加密的 MIME/SMIME 訊息。</span><span class="sxs-lookup"><span data-stu-id="681fe-103">This topic describes how to configure BizTalk Server to use certificates to send encrypted MIME/SMIME messages.</span></span> <span data-ttu-id="681fe-104">下列程序也適用於設定透過 AS2 傳輸已加密的訊息傳送。</span><span class="sxs-lookup"><span data-stu-id="681fe-104">The procedure below also applies to configuring the sending of encrypted messages over AS2 transport.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="681fe-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="681fe-105">Prerequisites</span></span>  
 <span data-ttu-id="681fe-106">若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="681fe-106">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-encrypted-messages"></a><span data-ttu-id="681fe-107">若要設定 BizTalk Server 傳送加密的訊息</span><span class="sxs-lookup"><span data-stu-id="681fe-107">To configure BizTalk Server to send encrypted messages</span></span>  
  
1.  <span data-ttu-id="681fe-108">建立管線來傳送加密的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="681fe-108">Create a pipeline to send encrypted messages, as follows:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="681fe-109">設定 AS2 傳輸來傳送加密的訊息的 AS2Send 和 AS2EdiSend 管線，因為包含在這個步驟並非必要[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]做這個函式。</span><span class="sxs-lookup"><span data-stu-id="681fe-109">This step is not necessary when configuring AS2 transport for sending encrypted messages because the AS2Send and AS2EdiSend pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.</span></span>  
  
    1.  <span data-ttu-id="681fe-110">建立傳送管線，然後將 MIME/SMIME 編碼器管線元件拖曳到管線的 「 編碼 」 階段。</span><span class="sxs-lookup"><span data-stu-id="681fe-110">Create a send pipeline and then drag the MIME/SMIME Encoder pipeline component into the Encode stage of the pipeline.</span></span>  
  
    2.  <span data-ttu-id="681fe-111">在**屬性**視窗中，設定 MIME/SMIME 編碼器管線元件啟用加密內容**True**。</span><span class="sxs-lookup"><span data-stu-id="681fe-111">In the **Properties** window, configure the MIME/SMIME Encoder pipeline component Enable encryption property to **True**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="681fe-112">將管線部署至 BizTalk 群組之後，您可以使用 BizTalk Server 管理主控台來設定管線元件屬性。</span><span class="sxs-lookup"><span data-stu-id="681fe-112">You can configure the send pipeline component properties using the BizTalk Server Administration console after the pipeline has been deployed into a BizTalk group.</span></span>  
  
    3.  <span data-ttu-id="681fe-113">建置和部署傳送管線。</span><span class="sxs-lookup"><span data-stu-id="681fe-113">Build and deploy the send pipeline.</span></span>  
  
2.  <span data-ttu-id="681fe-114">設定傳送埠來傳送加密的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="681fe-114">Configure the send port for sending encrypted messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="681fe-115">將您建立包含 BizTalk 應用程式包括的接收位置來接收加密的訊息的傳送管線的 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="681fe-115">Add the BizTalk assembly that you created containing the send pipeline to the BizTalk application including the receive locations to receive encrypted messages.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="681fe-116">設定 AS2 傳輸來傳送加密的訊息，因為 AS2Send 和 AS2EdiSend 管線會包含在 「 BizTalk EDI 應用程式時，不需要此步驟。</span><span class="sxs-lookup"><span data-stu-id="681fe-116">This step is not necessary when configuring AS2 transport for sending encrypted messages because the AS2Send and AS2EdiSend pipelines are included in the BizTalk EDI Application.</span></span>  
  
    2.  <span data-ttu-id="681fe-117">您在上一個程序中建立的傳送管線的 BizTalk 應用程式中設定的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="681fe-117">Configure the send port in the BizTalk Application with the send pipeline that you created in the previous procedure.</span></span>  
  
    3.  <span data-ttu-id="681fe-118">將指定的加密憑證，以滑鼠右鍵按一下傳送埠，按一下您安裝**屬性**，然後按一下**憑證**。</span><span class="sxs-lookup"><span data-stu-id="681fe-118">Assign the encryption certificate that you installed by right-clicking the send port, clicking **Properties**, and then clicking **Certificate**.</span></span> <span data-ttu-id="681fe-119">按一下**瀏覽**，瀏覽至您想要指派給這個傳送埠，然後按一下 憑證**確定**。</span><span class="sxs-lookup"><span data-stu-id="681fe-119">Click **Browse**, browse to the certificate that you want to assign to this send port, and then click **OK**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="681fe-120">如果憑證不存在於本機電腦上**指紋**方塊中輸入或貼上憑證指紋，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="681fe-120">If the certificate does not exist on the local computer, in the **Thumbprint** box, type or paste the certificate thumbprint, and then click **OK**.</span></span> <span data-ttu-id="681fe-121">憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="681fe-121">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.</span></span>