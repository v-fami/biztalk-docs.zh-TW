---
title: 處理內送 MDN |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd78e84c-4989-47e4-b95b-80582084ddec
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e599e9ebbc7a05a466cc047d891699222c2dabac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265262"
---
# <a name="processing-an-incoming-mdn"></a><span data-ttu-id="8d8d5-102">處理內送 MDN</span><span class="sxs-lookup"><span data-stu-id="8d8d5-102">Processing an Incoming MDN</span></span>
<span data-ttu-id="8d8d5-103">AS2 接收管線 （AS2EDIReceive 和 AS2Receive） 處理內送 MDN 做為 AS2 訊息接收者的合作對象根據協議屬性。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-103">The AS2 receive pipelines (AS2EDIReceive and AS2Receive) process an incoming MDN based upon the agreement properties for the party as an AS2 message receiver.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8d8d5-104">自動將 MDN 與外寄 AS2 訊息相互關聯。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-104"> automatically correlates the MDN to the outgoing AS2 message.</span></span>  
  
 <span data-ttu-id="8d8d5-105">以下是每個管線所執行的步驟：</span><span class="sxs-lookup"><span data-stu-id="8d8d5-105">The steps each pipeline performs are as follows:</span></span>  
  
-   <span data-ttu-id="8d8d5-106">藉由比對 AS2 判斷傳送合作對象-訊息的 AS2 標頭的值與 AS2 的值從-從清單中**識別碼**頁面的單向 AS2 協議索引標籤的**協議屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-106">Determines the sending party by matching the AS2-From value in the AS2 header of the message with the value for AS2-From list in the **Identifiers** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="8d8d5-107">如果找不到符合項，管線就會中止處理並引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-107">If a match is not found, the pipeline aborts processing and raises an exception.</span></span>  
  
-   <span data-ttu-id="8d8d5-108">將下列 AS2 屬性升級至內容：</span><span class="sxs-lookup"><span data-stu-id="8d8d5-108">Promotes the following AS2 properties to the context:</span></span>  
  
    -   <span data-ttu-id="8d8d5-109">IsAS2FailedMessage</span><span class="sxs-lookup"><span data-stu-id="8d8d5-109">IsAS2FailedMessage</span></span>  
  
    -   <span data-ttu-id="8d8d5-110">DispositionType</span><span class="sxs-lookup"><span data-stu-id="8d8d5-110">DispositionType</span></span>  
  
    -   <span data-ttu-id="8d8d5-111">GenerateAsynchronous200OKOnly</span><span class="sxs-lookup"><span data-stu-id="8d8d5-111">GenerateAsynchronous200OKOnly</span></span>  
  
    -   <span data-ttu-id="8d8d5-112">IsAS2MdnResponseMessage</span><span class="sxs-lookup"><span data-stu-id="8d8d5-112">IsAS2MdnResponseMessage</span></span>  
  
    -   <span data-ttu-id="8d8d5-113">IsAS2MessageSigned</span><span class="sxs-lookup"><span data-stu-id="8d8d5-113">IsAS2MessageSigned</span></span>  
  
    -   <span data-ttu-id="8d8d5-114">OriginalMessageId</span><span class="sxs-lookup"><span data-stu-id="8d8d5-114">OriginalMessageId</span></span>  
  
    -   <span data-ttu-id="8d8d5-115">ReceivedContentMic</span><span class="sxs-lookup"><span data-stu-id="8d8d5-115">ReceivedContentMic</span></span>  
  
    -   <span data-ttu-id="8d8d5-116">DispositionMode</span><span class="sxs-lookup"><span data-stu-id="8d8d5-116">DispositionMode</span></span>  
  
    -   <span data-ttu-id="8d8d5-117">MessageId</span><span class="sxs-lookup"><span data-stu-id="8d8d5-117">MessageId</span></span>  
  
-   <span data-ttu-id="8d8d5-118">將訊息的所有 HTTP 標頭設定成 InboundHttpHeaders 屬性，並將其升級至訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-118">Sets the InboundHttpHeaders property to all the HTTP headers of the message, and promotes it to the context of the message.</span></span>  
  
-   <span data-ttu-id="8d8d5-119">如果已在單向 AS2 協議屬性中啟用，則產生 MDN 的複本 (電傳格式)，並將此複本儲存在不可否認性資料庫中 (BizTalkDTADb 資料庫的 EdiMessageContent 資料表)。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-119">Makes a copy of the MDN (in wire format), and stores the copy in the non-repudiation database (the EdiMessageContent table of the BizTalkDTADb database), if enabled in the one-way AS2 agreement properties.</span></span>  
  
-   <span data-ttu-id="8d8d5-120">在已簽署 MDN 的情況下，執行 MIME 處理，其中包括驗證簽章。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-120">Performs MIME processing, including verifying the signature if the MDN was signed.</span></span>  
  
-   <span data-ttu-id="8d8d5-121">比較 MDN 中的 MIC (訊息完整性檢查)，以及當 AS2Send 管線傳送出原始訊息時所計算出之資料存放區中的 MIC (如果適用)。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-121">Compares the MIC (Message Integrity Check) in the MDN with the MIC in the data store that was computed by the AS2Send pipeline when it sent out the original message (if applicable).</span></span> <span data-ttu-id="8d8d5-122">如需詳細資訊，請參閱[MDN 訊息](../core/mdn-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-122">For more information, see [MDN Messages](../core/mdn-messages.md).</span></span>  
  
-   <span data-ttu-id="8d8d5-123">在不可否認性的資料庫中建立相互關聯項目。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-123">Makes correlation entries in the non-repudiation database.</span></span>  
  
-   <span data-ttu-id="8d8d5-124">刪除 MDN，除非**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**屬性設定**傳送者 MDN 設定**頁面的單向 AS2 協議索引標籤的**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-124">Deletes the MDN, unless the **Process inbound MDN into MessageBox for routing/delivery options** property is set in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="8d8d5-125">如果**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**屬性設定**傳送者 MDN 設定**頁面的單向 AS2 協議索引標籤的**協議屬性**對話方塊中，接收管線將 MDN 路由至 AS2 解碼器當做通過訊息的電傳格式，並放入 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-125">If the **Process inbound MDN into MessageBox for routing/delivery options** property is set in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box, the receive pipeline routes the MDN in wire format through the AS2 Decoder as a passthrough message and drops it into the MessageBox.</span></span> <span data-ttu-id="8d8d5-126">電傳格式的 MDN 包含所有的 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-126">The MDN in wire format contains all HTTP headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8d8d5-127">您可以將傳送埠設定成訂閱已放入 MessageBox 中的已接收 MDN。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-127">You can set up a send port to subscribe to a received MDN that has been dropped into the MessageBox.</span></span> <span data-ttu-id="8d8d5-128">若要訂閱接收的 MDN，請將傳送埠篩選條件設定為 `IsAS2MdnResponseMessage==True`。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-128">To subscribe to the received MDN, set the send port filter to `IsAS2MdnResponseMessage==True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8d8d5-129">如果您使用 AS2EdiReceive 管線來處理收到的 MDN，您無法將 MDN 路由至 MessageBox 設定**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**屬性**傳送者 MDN設定**頁面的單向 AS2 協議索引標籤的**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-129">If you use the AS2EdiReceive pipeline to process a received MDN, you cannot route the MDN into the MessageBox by setting the **Process inbound MDN into MessageBox for routing/delivery options** property in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="8d8d5-130">嘗試這樣做會造成 EDI 錯誤，因為這樣 MDN 會傳遞至 EDI 解碼器，但是該解碼器無法處理 MDN。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-130">Trying to do so will result in an EDI error because the MDN will be passed to the EDI Decoder, which cannot process an MDN.</span></span> <span data-ttu-id="8d8d5-131">如果 MDN 沒有傳送至 MessageBox，AS2Decoder 便會使用 MDN，這樣 MDN 便不會傳遞至 EDI 解碼器。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-131">If the MDN is not sent to the MessageBox, the AS2Decoder will consume the MDN, so it will not be passed to the EDI Decoder.</span></span>  
  
## <a name="message-integrity-check"></a><span data-ttu-id="8d8d5-132">訊息完整性檢查</span><span class="sxs-lookup"><span data-stu-id="8d8d5-132">Message Integrity Check</span></span>  
 <span data-ttu-id="8d8d5-133">訊息完整性檢查 (MIC) 是用來確認 MDN 有和原始傳送的訊息相互關聯。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-133">The Message Integrity Check (MIC) is used to verify that an MDN correlates to the original sent message.</span></span> <span data-ttu-id="8d8d5-134">AS2Send 傳送管線會在產生原始 AS2 訊息時依據訊息內容計算 MIC，並將 MIC 儲存在資料存放區中。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-134">The AS2Send send pipeline calculates the MIC from the message payload when it generates the original AS2 message, and stores the MIC in the data store.</span></span> <span data-ttu-id="8d8d5-135">當需要 MDN 時，原始訊息的接收者會產生 MIC 並將它加入至 MDN 中。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-135">When an MDN is required, the recipient of the original message generates an MIC and adds it to the MDN.</span></span> <span data-ttu-id="8d8d5-136">當 AS2MdnReceive 接收管線接收 MDN 時，如果有要求簽署的 MDN，這項檢查就會比較 MDN 中的 MIC 與資料存放區中的 MIC。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-136">When the AS2MdnReceive receive pipeline receives the MDN, if a signed MDN was requested, it compares the MIC in the MDN with the MIC in the data store.</span></span>  
  
 <span data-ttu-id="8d8d5-137">MDN 中的 MIC 與資料存放區中 MIC 若是不相符，就表示在傳輸期間或訊息由接收合作對象接收時有發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8d8d5-137">A mismatch between the MIC in the MDN and the MIC in the data store indicates that there was an error during transmission or receipt of the message by the receiving party.</span></span> <span data-ttu-id="8d8d5-138">以下是發生這種失敗時所報告的值：</span><span class="sxs-lookup"><span data-stu-id="8d8d5-138">The values reported in such a failure are the following:</span></span>  
  
-   <span data-ttu-id="8d8d5-139">AS2DispositionType：失敗</span><span class="sxs-lookup"><span data-stu-id="8d8d5-139">AS2DispositionType: Failed</span></span>  
  
-   <span data-ttu-id="8d8d5-140">AS2DispositionModifierExtensionType：錯誤</span><span class="sxs-lookup"><span data-stu-id="8d8d5-140">AS2DispositionModifierExtensionType: Error</span></span>  
  
-   <span data-ttu-id="8d8d5-141">AS2DispositionModifierExtensionDescription：完整性檢查失敗</span><span class="sxs-lookup"><span data-stu-id="8d8d5-141">AS2DispositionModifierExtensionDescription: Integrity Check Failed</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8d5-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d8d5-142">See Also</span></span>  
 <span data-ttu-id="8d8d5-143">[BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="8d8d5-143">[How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md) </span></span>  
 [<span data-ttu-id="8d8d5-144">MDN 訊息</span><span class="sxs-lookup"><span data-stu-id="8d8d5-144">MDN Messages</span></span>](../core/mdn-messages.md)