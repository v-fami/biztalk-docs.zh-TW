---
title: AS2 處理的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 941111d8-b394-4648-a675-e4a8f118a84b
caps.latest.revision: 40
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61ce04c572c95a1a4e2433d6b046028468eca805
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009391"
---
# <a name="known-issues-with-as2-processing"></a><span data-ttu-id="74444-102">AS2 處理的已知問題</span><span class="sxs-lookup"><span data-stu-id="74444-102">Known Issues with AS2 Processing</span></span>
<span data-ttu-id="74444-103">本節中的主題描述 BizTalk Server AS2 解決方案的已知的問題。</span><span class="sxs-lookup"><span data-stu-id="74444-103">This section contains topics that describe known issues with BizTalk Server AS2 solutions.</span></span>  
  
## <a name="as2-processing-not-supported-on-64-bit-computers"></a><span data-ttu-id="74444-104">64 位元電腦不支援 AS2 處理</span><span class="sxs-lookup"><span data-stu-id="74444-104">AS2 Processing Not Supported on 64-Bit Computers</span></span>  
 <span data-ttu-id="74444-105">BizTalk Server AS2 解決方案不支援在 64 位元電腦上。</span><span class="sxs-lookup"><span data-stu-id="74444-105">The BizTalk Server AS2 solution is not supported on 64-bit computers.</span></span> <span data-ttu-id="74444-106">AS2 處理只能在 32 位元電腦或 64 位元電腦的 WOW64 模擬器下運作。</span><span class="sxs-lookup"><span data-stu-id="74444-106">AS2 processing only works on 32-bit computers or when running under the WOW64 emulator on 64-bit computers.</span></span>  
  
## <a name="the-as2-receive-pipelines-require-the-account-that-the-biztalk-isolated-host-instance-process-is-running-under-to-be-part-of-the-biztalk-application-users-group"></a><span data-ttu-id="74444-107">AS2 接收管線需要執行 BizTalk 外掛式主控件執行個體處理序的帳戶，屬於 BizTalk 應用程式使用者群組的成員</span><span class="sxs-lookup"><span data-stu-id="74444-107">The AS2 Receive Pipelines Require the Account that the BizTalk Isolated Host Instance Process is Running Under to Be Part of the BizTalk Application Users Group</span></span>  
 <span data-ttu-id="74444-108">使用 AS2EdiReceive 或 AS2Receive 管線時，您必須將用來執行 BizTalk 外掛式主控件執行個體處理序的使用者帳戶，新增至 BizTalk 應用程式使用者群組。</span><span class="sxs-lookup"><span data-stu-id="74444-108">If you are using the AS2EdiReceive or AS2Receive pipeline, you must add the user account that the BizTalk Isolated Host Instance process is running under to the BizTalk Application Users group.</span></span> <span data-ttu-id="74444-109">AS2EdiReceive 和 AS2Receive 管線會在 BizTalk 外掛式主控件執行個體處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="74444-109">The AS2EdiReceive and AS2Receive pipelines execute in the BizTalk Isolated Host Instance process.</span></span>  
  
## <a name="an-empty-receipt-delivery-option-header-will-cause-an-mdn-to-be-sent-synchronously"></a><span data-ttu-id="74444-110">空的 Receipt-Delivery-Option 標頭會導致以同步方式傳送 MDN</span><span class="sxs-lookup"><span data-stu-id="74444-110">An Empty Receipt-Delivery-Option Header Will Cause an MDN to Be Sent Synchronously</span></span>  
 <span data-ttu-id="74444-111">若 AS2Receive 管線所收到訊息之 receipt-delivery-option 標頭是空的，且收到非同步 MSN 要求，則管線會略過非同步 MSN 要求。</span><span class="sxs-lookup"><span data-stu-id="74444-111">If the AS2Receive pipeline receives a message with an empty receipt-delivery-option header, and an asynchronous MDN is requested, the pipeline will ignore the asynchronous MDN request.</span></span> <span data-ttu-id="74444-112">該管線反而會傳回同步 MDN，並在事件日誌和 AS2 狀態報告 (若已啟用) 公佈錯誤。</span><span class="sxs-lookup"><span data-stu-id="74444-112">It will send back a synchronous MDN instead, and post an error in the event log and in AS2 status reporting (if it is enabled).</span></span> <span data-ttu-id="74444-113">若未選取 [覆寫輸入訊息屬性] 屬性，就會發生這個情形。</span><span class="sxs-lookup"><span data-stu-id="74444-113">This occurs if the "Override inbound message properties" property is not selected.</span></span> <span data-ttu-id="74444-114">若已選取該屬性，就會以 [AS2 屬性] 對話方塊之 [做為 AS2 訊息傳送者的合作對象] 頁面中的 Receipt-Delivery-Option 屬性值，覆寫訊息中的 Receipt-Delivery-Option 標頭。</span><span class="sxs-lookup"><span data-stu-id="74444-114">If that property were selected, it would override the Receipt-Delivery-Option header in the message with the value of the Receipt-Delivery-Option property in the Party as AS2 Message Sender page of the AS2 Properties dialog box.</span></span>  
  
 <span data-ttu-id="74444-115">在這個例子中，由於 receipt-delivery-option 標頭是空的，因此 AS2Receive 管線沒有可以透過非同步連線傳送 MDN 回應的位址。</span><span class="sxs-lookup"><span data-stu-id="74444-115">In this instance, because the receipt-delivery-option header is empty, the AS2Receive pipeline does not have an address to send the MDN response to over an asynchronous connection.</span></span> <span data-ttu-id="74444-116">然而該管線仍具有開啟的同步連線，因此會透過該連線傳回 MDN。</span><span class="sxs-lookup"><span data-stu-id="74444-116">However, the pipeline still has an open synchronous connection, so it will send the MDN back over that connection.</span></span> <span data-ttu-id="74444-117">若為單向接收埠，BizTalk Server 傳送 HTTP 200OK 訊息後隨即會關閉連線。</span><span class="sxs-lookup"><span data-stu-id="74444-117">If it is a one-way receive port, BizTalk Server will close the connection after sending the HTTP 200OK message.</span></span>  
  
## <a name="use-of-unfolded-and-folded-http-line-headers"></a><span data-ttu-id="74444-118">使用展開和摺疊的 HTTP 行標頭</span><span class="sxs-lookup"><span data-stu-id="74444-118">Use of Unfolded and Folded HTTP Line Headers</span></span>  
 <span data-ttu-id="74444-119">為求達到最大的互通性，AS2 訊息應該使用展開的 HTTP 行標頭。</span><span class="sxs-lookup"><span data-stu-id="74444-119">For maximum interoperability, you should use unfolded HTTP line headers for AS2 messages.</span></span> <span data-ttu-id="74444-120">資訊服務 (IIS) 7.0 支援只有展開的 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="74444-120">Information Services (IIS) 7.0 supports only unfolded HTTP headers.</span></span> <span data-ttu-id="74444-121">IIS 6.0 支援摺疊與展開的標頭。</span><span class="sxs-lookup"><span data-stu-id="74444-121">IIS 6.0 supports folded and unfolded headers.</span></span> <span data-ttu-id="74444-122">然而，並不是所有系統都可以支援每行 80 個字元以上的標頭，針對這類系統，應該使用摺疊的標頭。</span><span class="sxs-lookup"><span data-stu-id="74444-122">However, not all systems can support headers with more than 80 characters per line, so for such systems folded lines should be used.</span></span>  
  
 <span data-ttu-id="74444-123">AS2 在 BizTalk Server 中的預設值是展開的 HTTP 行標頭。</span><span class="sxs-lookup"><span data-stu-id="74444-123">The default for AS2 in BizTalk Server is unfolded HTTP line headers.</span></span>  
  
## <a name="party-resolution-can-be-affected-by-a-localized-name"></a><span data-ttu-id="74444-124">合作對象解析可能受當地語系化名稱影響</span><span class="sxs-lookup"><span data-stu-id="74444-124">Party Resolution Can Be Affected by a Localized Name</span></span>  
 <span data-ttu-id="74444-125">BizTalk Server 在輸出的 AS2 訊息執行合作對象解析時，合作對象解析可能受訊息標頭中之當地語系化值的影響。</span><span class="sxs-lookup"><span data-stu-id="74444-125">When BizTalk Server performs party resolution on an outbound AS2 message, the party resolution can be affected by a localized value in the message headers.</span></span> <span data-ttu-id="74444-126">若 [AS2 屬性] 對話方塊之 [做為 AS2 訊息接收者的合作對象] 頁面中的 AS2-To 合作對象屬性預設為英文的合作對象名稱，而 AS2 訊息 AS2-To 標頭內的值設定為非英文名稱，則會找不到對應。</span><span class="sxs-lookup"><span data-stu-id="74444-126">If the AS2-To party property in the Party as AS2 Message Receiver page of the AS2 Properties dialog box is set by default to an English party name, and the value in the AS2-To header of the AS2 message is set to a non-English name, then the match will not be found.</span></span>  
  
## <a name="as2-message-size-limitation"></a><span data-ttu-id="74444-127">AS2 訊息大小限制</span><span class="sxs-lookup"><span data-stu-id="74444-127">AS2 Message Size Limitation</span></span>  
 <span data-ttu-id="74444-128">加密的 AS2 訊息應該小於 96 MB 才能處理。</span><span class="sxs-lookup"><span data-stu-id="74444-128">Encrypted AS2 messages should be smaller than 96 megabytes in order to be processed.</span></span> <span data-ttu-id="74444-129">這個限制是 AS2 解碼器所給予的，它屬於 AS2Receive 和 AS2EdiReceive 管線的一部分。</span><span class="sxs-lookup"><span data-stu-id="74444-129">This limitation is imposed by the AS2 Decoder, which is the part of the AS2Receive and AS2EdiReceive pipelines.</span></span>  
  
 <span data-ttu-id="74444-130">解決此大小限制的一種方法就是使用壓縮，因為 AS2 訊息會先壓縮再加密。</span><span class="sxs-lookup"><span data-stu-id="74444-130">One way to work around this size limitation is to use compression, because an AS2 message is compressed before it is encrypted.</span></span>  
  
## <a name="biztalk-edi-application-must-not-be-modified"></a><span data-ttu-id="74444-131">不得修改 BizTalk EDI 應用程式</span><span class="sxs-lookup"><span data-stu-id="74444-131">BizTalk EDI Application Must Not Be Modified</span></span>  
 <span data-ttu-id="74444-132">不得修改或刪除 BizTalk EDI 應用程式內的成品。</span><span class="sxs-lookup"><span data-stu-id="74444-132">Artifacts in the BizTalk EDI Application must not be modified or deleted.</span></span> <span data-ttu-id="74444-133">應用程式一經修改就無法還原，取消設定和重新設定 EDI 與 AS2 的功能也不行。</span><span class="sxs-lookup"><span data-stu-id="74444-133">If this application is modified, there is no way for you to revert to the original application by unconfiguring and reconfiguring the EDI and AS2 features.</span></span>  
  
## <a name="partner-may-reject-multipart-messages"></a><span data-ttu-id="74444-134">協力廠商可能會拒絕多部分訊息</span><span class="sxs-lookup"><span data-stu-id="74444-134">Partner May Reject Multipart Messages</span></span>  
 <span data-ttu-id="74444-135">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="74444-135">**Symptom**</span></span>  
  
 <span data-ttu-id="74444-136">將傳送多部分訊息使用 AS2 傳送管線時，您的合作夥伴可以拒絕的訊息，因為遺漏的 Content-type MIME 標頭。</span><span class="sxs-lookup"><span data-stu-id="74444-136">When sending multipart messages using the AS2 send pipeline, your partner may reject the message due to a missing Content-Type MIME header.</span></span>  
  
 <span data-ttu-id="74444-137">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="74444-137">**Possible Cause**</span></span>  
  
 <span data-ttu-id="74444-138">內容類型是可以針對每個主體組件的多部分訊息中出現的選擇性標頭。</span><span class="sxs-lookup"><span data-stu-id="74444-138">Content-Type is an optional header that can be present for each body part in a multipart message.</span></span> <span data-ttu-id="74444-139">有些合作夥伴要求，此標頭會顯示每個內文部分、 集合，為特定的內容類型。</span><span class="sxs-lookup"><span data-stu-id="74444-139">Some partners require that this header is present for each body part, and set to a specific content-type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74444-140">訊息的本文會有設定透過 AS2 傳送管線中，內容類型的屬性，然而任何附件不會將內容類型屬性設定。</span><span class="sxs-lookup"><span data-stu-id="74444-140">The body of the message will have the Content-Type property set by the AS2 send pipeline, however any attachments will not have the Content-Type property set.</span></span>  
  
 <span data-ttu-id="74444-141">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="74444-141">**Resolution**</span></span>  
  
 <span data-ttu-id="74444-142">如果您的夥伴需要每個內文部分內容類型標頭值，您必須建立自訂管線元件會設定這個屬性，並使用的傳送管線中的元件。</span><span class="sxs-lookup"><span data-stu-id="74444-142">If your partner requires the Content-Type header value for each body part, you must create a custom pipeline component that sets this property and use the component in the send pipeline.</span></span>  
  
## <a name="when-receiving-multipart-messages-the-first-part-is-considered-the-body"></a><span data-ttu-id="74444-143">當接收多部分訊息，第一個部分會被視為主體</span><span class="sxs-lookup"><span data-stu-id="74444-143">When Receiving Multipart Messages, the First Part is Considered the Body</span></span>  
 <span data-ttu-id="74444-144">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="74444-144">**Symptom**</span></span>  
  
 <span data-ttu-id="74444-145">當接收多組件的 AS2 訊息、[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能不正確會識別附件的其中一個做為訊息主體。</span><span class="sxs-lookup"><span data-stu-id="74444-145">When receiving a multipart AS2 message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may incorrectly identify one of the attachments as the message body.</span></span>  
  
 <span data-ttu-id="74444-146">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="74444-146">**Possible Cause**</span></span>  
  
 <span data-ttu-id="74444-147">訊息 multipart/related 的 MIME 標頭可能包含一個選擇性指出哪些組件的 'start' 參數應視為訊息的本文藉由指定組件的內容識別碼。</span><span class="sxs-lookup"><span data-stu-id="74444-147">The MIME header of a multipart/related message may contain an optional ‘start’ parameter that indicates which of the parts should be treated as the body of the message by specifying the Content-ID of the part.</span></span> <span data-ttu-id="74444-148">如果 start 參數不存在，第一個部分應該視為訊息的本文。</span><span class="sxs-lookup"><span data-stu-id="74444-148">If the start parameter is not present, the first part should be considered the body of the message.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="74444-149">如果它存在，並且會一律將視為訊息本文的第一個部分，不接受啟動參數。</span><span class="sxs-lookup"><span data-stu-id="74444-149"> does not honor the start parameter if it is present, and will always treat the first part as the body of the message.</span></span>  
  
 <span data-ttu-id="74444-150">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="74444-150">**Resolution**</span></span>  
  
 <span data-ttu-id="74444-151">如果您的夥伴無法做為第一個部分 multipart/related 訊息的傳送主體時，您必須建立的管線元件，以正確識別訊息的本文。</span><span class="sxs-lookup"><span data-stu-id="74444-151">If your partner is unable to send the body as the first part of the multipart/related message, you must create a pipeline component that correctly identifies the body of the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74444-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="74444-152">See Also</span></span>  
 <span data-ttu-id="74444-153">[疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="74444-153">[Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md) </span></span>  
 <span data-ttu-id="74444-154">[AS2 方案架構](../core/as2-solution-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="74444-154">[AS2 Solution Architecture](../core/as2-solution-architecture.md) </span></span>  
 [<span data-ttu-id="74444-155">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="74444-155">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)