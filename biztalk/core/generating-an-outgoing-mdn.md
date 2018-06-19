---
title: 產生外寄 MDN |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12d7da1c-0d3c-42d4-9388-29f499353d13
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a903cc72a41362f6843449a4d635878706f2ea1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247950"
---
# <a name="generating-an-outgoing-mdn"></a><span data-ttu-id="8750e-102">產生外寄 MDN</span><span class="sxs-lookup"><span data-stu-id="8750e-102">Generating an Outgoing MDN</span></span>
<span data-ttu-id="8750e-103">AS2 接收管線會針對內送訊息產生 MDN (訊息處理通知) 回應。</span><span class="sxs-lookup"><span data-stu-id="8750e-103">The AS2 receive pipelines generate an MDN (Message Disposition Notification) response for an incoming message.</span></span> <span data-ttu-id="8750e-104">這項工作是由 AS2EDIReceive 接收管線中的 EDI 解譯器 (回應 EDI 編碼的訊息) 或 AS2Receive 接收管線中的 AS2 解譯器 (回應非 EDI 編碼的訊息) 負責執行。</span><span class="sxs-lookup"><span data-stu-id="8750e-104">This is performed by the EDI Disassembler pipeline component in the AS2EDIReceive receive pipeline (in response to an EDI-encoded message) or the AS2 Disassembler pipeline component in the AS2Receive receive pipeline (in response to a non-EDI-encoded message).</span></span>  
  
## <a name="when-and-how-an-mdn-is-generated"></a><span data-ttu-id="8750e-105">何時及如何產生 MDN</span><span class="sxs-lookup"><span data-stu-id="8750e-105">When and How an MDN is Generated</span></span>  
 <span data-ttu-id="8750e-106">MDN 通常是根據原始 AS2 訊息中的 AS2 標頭而產生，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8750e-106">An MDN is normally generated based upon the AS2 headers in the original AS2 message, as follows:</span></span>  
  
-   <span data-ttu-id="8750e-107">如果 AS2 訊息中出現 Disposition-Notification-To 標頭，將會傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-107">An MDN will be sent if the Disposition-Notification-To header is present in the AS2 message.</span></span>  
  
-   <span data-ttu-id="8750e-108">如果訊息中出現 Disposition-Notification-To 標頭和 Receipt-Delivery-Option 標頭，則會以非同步的方式傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-108">If the Disposition-Notification-To header and the Receipt-Delivery-Option header are present in the message, the MDN will be sent asynchronously.</span></span> <span data-ttu-id="8750e-109">它會透過與原始訊息不同的連線，傳送到 Receipt-Delivery-Option 標頭中的 URL。</span><span class="sxs-lookup"><span data-stu-id="8750e-109">It will be sent to the URL in the Receipt-Delivery-Option header, over a different connection than the original message.</span></span>  
  
-   <span data-ttu-id="8750e-110">如果訊息中出現 Disposition-Notification-To 標頭，但是沒有 Receipt-Delivery-Option 標頭，則會以同步的方式，透過與原始訊息相同的連線傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-110">If the Disposition-Notification-To header is present in the message, but the Receipt-Delivery-Option header is not present in the message, the MDN will be sent synchronously over the same connection as the original message.</span></span>  
  
 <span data-ttu-id="8750e-111">解譯器會從收到的 AS2 訊息中的 AS2-To 標頭，在 MDN 中建立 AS2-From 標頭，並從收到的 AS2 訊息中的 AS2-From 標頭，在 MDN 中建立 AS2-To 標頭。</span><span class="sxs-lookup"><span data-stu-id="8750e-111">The Disassembler creates the AS2-From header in the MDN from the AS2-To header in the received AS2 message, and it creates the AS2-To header in the MDN from the AS2-From header in the received AS2 message.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8750e-112"> 可讓您覆寫這些設定，包括根據合作對象的 AS2 協議屬性，指定是否產生 MDN 及其產生方式。</span><span class="sxs-lookup"><span data-stu-id="8750e-112"> enables you to override these settings, specifying whether an MDN will be generated and how it will be generated based upon a party's AS2 agreement properties.</span></span> <span data-ttu-id="8750e-113">您覆寫訊息中的 AS2 標頭設定**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性的單向 AS2 協議索引標籤中**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8750e-113">You override the AS2 header settings in the message using the **Use agreement settings for validation and MDN instead of message header** property in the one-way AS2 agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="8750e-114">這個屬性可讓您傳送 MDN (即使 AS2 標頭未呼叫它也一樣)，或是在 AS2 標頭指定同步連線時非同步傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-114">This property enables you to send an MDN even if the AS2 header does not call for one, or to send the MDN asynchronously when the AS2 header specifies a synchronous connection.</span></span>  
  
 <span data-ttu-id="8750e-115">如果您設定**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性中的值**要求 MDN**區段**傳送者 MDN 設定**頁面在單向 AS2 協議索引標籤的**協議屬性**對話方塊將會用於 MDN，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8750e-115">If you set the **Use agreement settings for validation and MDN instead of message header** property, the values in the **Request MDN** section of the **Sender MDN Settings** page in the one-way AS2 agreement tab of the **Agreement Properties** dialog box will be used for the MDN, as follows:</span></span>  
  
-   <span data-ttu-id="8750e-116">如果會傳送 MDN**要求 MDN**選取屬性。</span><span class="sxs-lookup"><span data-stu-id="8750e-116">An MDN will be sent if the **Request MDN** property is selected.</span></span>  
  
-   <span data-ttu-id="8750e-117">如果**要求 MDN**選取屬性，而**要求非同步 MDN**屬性，將會以非同步方式傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-117">If the **Request MDN** property is selected, and the **Request asynchronous MDN** property is selected, the MDN will be sent asynchronously.</span></span> <span data-ttu-id="8750e-118">MDN 會傳送到的 URL，**回條傳遞選項 (URL)** 屬性設定為，透過與原始訊息不同的連線。</span><span class="sxs-lookup"><span data-stu-id="8750e-118">The MDN will be sent to the URL that the **Receipt-Delivery-Option (URL)** property is set to, over a different connection than the original message.</span></span>  
  
-   <span data-ttu-id="8750e-119">如果**要求 MDN**選取屬性，但**要求非同步 MDN**未選取屬性，將以同步方式傳送 MDN，透過與原始訊息相同的連線。</span><span class="sxs-lookup"><span data-stu-id="8750e-119">If the **Request MDN** property is selected, but the **Request asynchronous MDN** property is not selected, the MDN will be sent synchronously over the same connection as the original message.</span></span>  
  
 <span data-ttu-id="8750e-120">如果**對驗證與 MDN 使用協議設定，而非訊息標頭**設定屬性，AS2-從訊息中的屬性標頭會用來產生 MDN，但是 AS2-若要將取自協議屬性中，並管線會簽署 MDN 根據**要求簽署的 MDN**屬性。</span><span class="sxs-lookup"><span data-stu-id="8750e-120">If the **Use agreement settings for validation and MDN instead of message header** property is set, the AS2-From property in the message header will be used in generating the MDN, but AS2-To will be taken from the agreement properties, and the pipeline will sign the MDN according to the **Request Signed MDN** property.</span></span> <span data-ttu-id="8750e-121">AS2 標頭會依照下列方式對應至協議屬性：</span><span class="sxs-lookup"><span data-stu-id="8750e-121">The AS2 headers correspond to the agreement properties as follows:</span></span>  
  
|<span data-ttu-id="8750e-122">協議屬性</span><span class="sxs-lookup"><span data-stu-id="8750e-122">Agreement Property</span></span>|<span data-ttu-id="8750e-123">訊息中的 AS2 標頭</span><span class="sxs-lookup"><span data-stu-id="8750e-123">AS2 Header in the Message</span></span>|  
|------------------------|-------------------------------|  
|<span data-ttu-id="8750e-124">產生 MDN</span><span class="sxs-lookup"><span data-stu-id="8750e-124">Generate MDN</span></span>|<span data-ttu-id="8750e-125">Disposition-Notification-To</span><span class="sxs-lookup"><span data-stu-id="8750e-125">Disposition-Notification-To</span></span>|  
|<span data-ttu-id="8750e-126">簽署 MDN</span><span class="sxs-lookup"><span data-stu-id="8750e-126">Sign MDN</span></span>|<span data-ttu-id="8750e-127">Signed-Receipt-Protocol</span><span class="sxs-lookup"><span data-stu-id="8750e-127">Signed-Receipt-Protocol</span></span>|  
|<span data-ttu-id="8750e-128">Receipt-Delivery-Option</span><span class="sxs-lookup"><span data-stu-id="8750e-128">Receipt-Delivery-Option</span></span>|<span data-ttu-id="8750e-129">Receipt-Delivery-Option</span><span class="sxs-lookup"><span data-stu-id="8750e-129">Receipt-Delivery-Option</span></span>|  
  
 <span data-ttu-id="8750e-130">如果 MDN 已啟用，接收管線將會升級下列內容屬性：</span><span class="sxs-lookup"><span data-stu-id="8750e-130">If an MDN is enabled, the receive pipeline will promote the following context properties:</span></span>  
  
-   `EdiIntAS.DispositionMode`  
  
-   `EdiIntAS.DispositionType`  
  
 <span data-ttu-id="8750e-131">這兩個內容屬性都必須升級，才能產生 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-131">Both of these context properties must be promoted in order for the MDN to be generated.</span></span> <span data-ttu-id="8750e-132">如需有關這些內容屬性的詳細資訊，請參閱[AS2 內容屬性](../core/as2-context-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8750e-132">For more information about these context properties, see [AS2 Context Properties](../core/as2-context-properties.md).</span></span>  
  
 <span data-ttu-id="8750e-133">若組態設定和內送訊息的標頭不一致，管線就會產生負 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-133">If the configuration settings and the headers in the incoming message are inconsistent, the pipeline will generate a negative MDN.</span></span>  
  
 <span data-ttu-id="8750e-134">如果在協議屬性中要求 MDN，則即使 AS2 處理中發生錯誤，接收管線也會嘗試傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-134">If the MDN is requested in the agreement properties, the receive pipeline will attempt to send an MDN even if an error occurs in AS2 processing.</span></span>  
  
## <a name="how-the-receive-pipeline-processes-a-generated-mdn"></a><span data-ttu-id="8750e-135">接收管線如何處理產生的 MDN</span><span class="sxs-lookup"><span data-stu-id="8750e-135">How the Receive Pipeline Processes a Generated MDN</span></span>  
 <span data-ttu-id="8750e-136">如果 MDN 產生根據上述規則 AS2EDIReceive 或 AS2Receive 接收管線就會以下列方式處理 MDN:</span><span class="sxs-lookup"><span data-stu-id="8750e-136">If an MDN is generated according to the above rules, the AS2EDIReceive or AS2Receive receive pipeline will process the MDN as follows:</span></span>  
  
-   <span data-ttu-id="8750e-137">如果已在單向 AS2 協議屬性中啟用，就複製 MDN (採用電傳格式) 並將它儲存在不可否認性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="8750e-137">Makes a copy of the MDN (in wire format), and stores it in the non-repudiation database, if enabled in the one-way AS2 agreement properties.</span></span>  
  
-   <span data-ttu-id="8750e-138">如果已在單向 AS2 協議屬性中啟用，則執行 MIME 處理，包括套用數位簽章。</span><span class="sxs-lookup"><span data-stu-id="8750e-138">Performs MIME processing, including applying a digital signature, if enabled in the one-way AS2 agreement properties.</span></span>  
  
-   <span data-ttu-id="8750e-139">計算 AS2 訊息內容的 MIC (訊息完整性檢查)，並將它附加到 MDN 的 Received-content-MIC 延伸模組欄位。</span><span class="sxs-lookup"><span data-stu-id="8750e-139">Calculates the MIC (Message Integrity Check) for the AS2 message payload and appends it to the Received-content-MIC extension field of the MDN.</span></span> <span data-ttu-id="8750e-140">要套用的 MIC 由內送訊息的簽署回條 micalg 標頭的演算法或**簽署演算法**屬性**傳送者 MDN 設定**頁面的單向協議索引標籤的**協議屬性**對話方塊 （當輸入的訊息屬性會覆寫）。</span><span class="sxs-lookup"><span data-stu-id="8750e-140">The algorithm to be applied for the MIC is determined by the signed-receipt-micalg header of the incoming message or the **Signing Algorithm** property on the **Sender MDN Settings** page of the one-way agreement tab of the **Agreement Properties** dialog box (when the inbound message properties are overridden).</span></span> <span data-ttu-id="8750e-141">它可以是 SHA1 或 MD5。</span><span class="sxs-lookup"><span data-stu-id="8750e-141">It can be either SHA1 or MD5.</span></span> <span data-ttu-id="8750e-142">演算法的值也會包括在 MDN 中。</span><span class="sxs-lookup"><span data-stu-id="8750e-142">The value of the algorithm is also included in the MDN.</span></span>  
  
-   <span data-ttu-id="8750e-143">在不可否認性的資料庫中建立相互關聯項目。</span><span class="sxs-lookup"><span data-stu-id="8750e-143">Makes correlation entries in the non-repudiation database.</span></span>  
  
-   <span data-ttu-id="8750e-144">建立 MDN 訊息的複本。</span><span class="sxs-lookup"><span data-stu-id="8750e-144">Makes a copy of the MDN message.</span></span>  
  
-   <span data-ttu-id="8750e-145">若要採同步方式傳輸 MDN，管線會將 `EdiIntAS.IsAS2AsynchronousMDN` 屬性設定為 False；若採非同步方式，則會將 Async 屬性設定為 True。</span><span class="sxs-lookup"><span data-stu-id="8750e-145">If the MDN is to be transmitted synchronously, the pipeline sets the `EdiIntAS.IsAS2AsynchronousMDN` property to False; if asynchronously, it sets the property to True.</span></span>  
  
-   <span data-ttu-id="8750e-146">若要採同步方式傳輸 MDN，與雙向接收埠關聯的 AS2Send 傳送管線將會依據 `EdiIntAS.IsAS2AsynchronousMDN` 屬性 (設定為 False) 和相互關聯 Token 來接受 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-146">If the MDN is to be transmitted synchronously, the AS2Send send pipeline associated with the two-way receive port will pick up the MDN based upon the `EdiIntAS.IsAS2AsynchronousMDN` property (set to False) and the correlation tokens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8750e-147">您也可以設定訂閱外寄同步 MDN 的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8750e-147">You can also set up a send port that subscribes to the outgoing synchronous MDN.</span></span> <span data-ttu-id="8750e-148">若要這樣做，請將傳送埠篩選條件設定為 `EdiIntAS.IsAS2MdnResponseMessage==True`。</span><span class="sxs-lookup"><span data-stu-id="8750e-148">To do so, set the send port filter to `EdiIntAS.IsAS2MdnResponseMessage==True`.</span></span>  
  
-   <span data-ttu-id="8750e-149">若要採非同步方式傳輸 MDN，接收管線會將 MDN 傳送至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="8750e-149">If the MDN is to be transmitted asynchronously, the receive pipeline routes the MDN to the MessageBox.</span></span> <span data-ttu-id="8750e-150">您必須將傳送埠設定為訂閱 MDN，並將傳送埠篩選條件設定為 `IsAS2AsynchronousMdn==True`。</span><span class="sxs-lookup"><span data-stu-id="8750e-150">You must set up a send port to subscribe to the MDN, setting the send port filter to `IsAS2AsynchronousMdn==True`.</span></span> <span data-ttu-id="8750e-151">AS2Send 傳送管線會依據該屬性和相互關聯 Token 來接受訊息。</span><span class="sxs-lookup"><span data-stu-id="8750e-151">The AS2Send send pipeline picks up the message based upon that property and the correlation tokens.</span></span> <span data-ttu-id="8750e-152">如果傳送埠是動態的，它會依據訊息標頭內 Receipt-Delivery-Notification 一行中的位址來傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="8750e-152">If the send port is dynamic, it will route the MDN based to the address in the Receipt-Delivery-Notification line in the header of the message.</span></span> <span data-ttu-id="8750e-153">如果傳送埠是靜態的，它會依據傳送埠的 [傳輸 URI] 屬性來路由訊息。</span><span class="sxs-lookup"><span data-stu-id="8750e-153">If the send port is static, it will route the message based upon Transport URI property of the send port.</span></span>  
  
## <a name="mdn-generation-rules"></a><span data-ttu-id="8750e-154">MDN 產生規則</span><span class="sxs-lookup"><span data-stu-id="8750e-154">MDN Generation Rules</span></span>  
 <span data-ttu-id="8750e-155">下列規則適用於 MDN 的產生：</span><span class="sxs-lookup"><span data-stu-id="8750e-155">The following rules apply to MDN generation:</span></span>  
  
-   <span data-ttu-id="8750e-156">當訊息傳送者明確要求簽署回條，但處理訊息內容卻發生錯誤時，即使交易本身可能無效，訊息接收者仍然必須傳回簽署回條。</span><span class="sxs-lookup"><span data-stu-id="8750e-156">When a message sender specifically requests a signed receipt, but there is error in processing the contents of the message, the message receiver must still return a signed receipt, even though the transaction itself may not be valid.</span></span> <span data-ttu-id="8750e-157">必須在 "disposition-field" 中設定處理訊息內容時發生錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="8750e-157">The reason for the error in processing the contents of the message must be set in the "disposition-field".</span></span>  
  
-   <span data-ttu-id="8750e-158">當 MDN 回條的要求中明確指定簽署回條，但是原始訊息的接收者卻無法支援要求的通訊協定格式或要求的 MIC 演算法時，則應該會傳回已簽署或未簽署的回條。</span><span class="sxs-lookup"><span data-stu-id="8750e-158">When the request for the MDN receipt explicitly specifies that the receipt be signed, but the receiver of the original message cannot support either the requested protocol format or the requested MIC algorithm, then either a signed or unsigned receipt should be returned.</span></span>  
  
-   <span data-ttu-id="8750e-159">如果未明確要求簽章，或接收方合作對象的協議無法辨識簽署回條要求參數，則接收方合作對象可能會傳回未簽署的回條、簽署的回條或是不傳回回條。</span><span class="sxs-lookup"><span data-stu-id="8750e-159">When a signature is not explicitly requested, or if the signed receipt request parameter is not recognized by the agreement for the receiving party, then the receiving party may return an unsigned receipt, a signed receipt, or no receipt.</span></span>  
  
## <a name="mic-generation"></a><span data-ttu-id="8750e-160">MIC 產生</span><span class="sxs-lookup"><span data-stu-id="8750e-160">MIC Generation</span></span>  
 <span data-ttu-id="8750e-161">在需要 MDN 時，原始訊息的接收者會產生 MIC (訊息完整性檢查) 並將它加入至 MDN 中。</span><span class="sxs-lookup"><span data-stu-id="8750e-161">When an MDN is required, the receiver of the original message generates an MIC (Message Integrity Check) and adds it to the MDN.</span></span> <span data-ttu-id="8750e-162">當 EDI 交換屬於多部分 MIME 內容類型的一部分時，必須針對整個多部分內容來計算 MIC，包括 EDI 交換和 MIME 標頭。</span><span class="sxs-lookup"><span data-stu-id="8750e-162">When the EDI interchange is part of a multi-part MIME content-type, the MIC must be calculated across the entire multi-part content, including the EDI interchange and the MIME headers.</span></span> <span data-ttu-id="8750e-163">針對經過加密的未簽署訊息，則會在解密的 MIME 標頭和內容上計算要傳回的 MIC。</span><span class="sxs-lookup"><span data-stu-id="8750e-163">For encrypted, unsigned messages, the MIC to be returned is calculated on the decrypted MIME header and content.</span></span> <span data-ttu-id="8750e-164">針對未簽署、未加密的訊息，則必須計算不含 MIME 標頭之訊息內容的 MIC。</span><span class="sxs-lookup"><span data-stu-id="8750e-164">For unsigned, unencrypted messages, the MIC must be calculated over the message contents without the MIME headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8750e-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8750e-165">See Also</span></span>  
 [<span data-ttu-id="8750e-166">BizTalk Server 如何接收 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="8750e-166">How BizTalk Server Receives AS2 Messages</span></span>](../core/how-biztalk-server-receives-as2-messages.md)