---
title: "BTARN 接收管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, receive pipelines
- RNMimeDecoder component
- ReceiveMessageNonRepudiate component
- RNDAsm component
- receive pipelines, message flow
- RNPartyRes component
- receive pipelines, BTARN
- MessageUpdater component
- messages, message flow
ms.assetid: 811f2a6a-ddd2-49cc-a00b-4c9d0110a0d1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80d7d5951b40b5c76b533e6425ee4d898b41c6cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="btarn-receive-pipeline"></a><span data-ttu-id="21166-102">BTARN 接收管線</span><span class="sxs-lookup"><span data-stu-id="21166-102">BTARN Receive Pipeline</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="21166-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]執行 RosettaNet 實作架構 (RNIF) 訊息接收，會使用 RNIFReceive 管線 (RNIFReceive.btp)。</span><span class="sxs-lookup"><span data-stu-id="21166-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] performs RosettaNet Implementation Framework (RNIF) message reception with the RNIFReceive pipeline (RNIFReceive.btp).</span></span> <span data-ttu-id="21166-104">接收管線包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="21166-104">The receive pipeline includes the following components:</span></span>  
  
-   <span data-ttu-id="21166-105">ReceiveMessageNonRepudiate</span><span class="sxs-lookup"><span data-stu-id="21166-105">ReceiveMessageNonRepudiate</span></span>  
  
-   <span data-ttu-id="21166-106">RNMimeDecoder (MIME 前置處理器/解碼器)</span><span class="sxs-lookup"><span data-stu-id="21166-106">RNMimeDecoder (MIME Preprocessor/Decoder)</span></span>  
  
-   <span data-ttu-id="21166-107">RNDAsm (XML 解譯器)</span><span class="sxs-lookup"><span data-stu-id="21166-107">RNDAsm (XML Disassembler)</span></span>  
  
-   <span data-ttu-id="21166-108">RNPartyRes (「合作對象解析」元件)</span><span class="sxs-lookup"><span data-stu-id="21166-108">RNPartyRes (Party Resolution component)</span></span>  
  
-   <span data-ttu-id="21166-109">MessageUpdater</span><span class="sxs-lookup"><span data-stu-id="21166-109">MessageUpdater</span></span>  
  
## <a name="receivemessagenonrepudiate"></a><span data-ttu-id="21166-110">ReceiveMessageNonRepudiate</span><span class="sxs-lookup"><span data-stu-id="21166-110">ReceiveMessageNonRepudiate</span></span>  
 <span data-ttu-id="21166-111">此元件將接收到的訊息儲存於 MessageStorageIn 資料表。</span><span class="sxs-lookup"><span data-stu-id="21166-111">This component stores the received message in the MessageStorageIn table.</span></span> <span data-ttu-id="21166-112">元件會執行 RNIF 標準所需的不可否認性處理作業。</span><span class="sxs-lookup"><span data-stu-id="21166-112">This component performs the non-repudiation processing required by the RNIF standards.</span></span>  
  
## <a name="rnmimedecoder"></a><span data-ttu-id="21166-113">RNMimeDecoder</span><span class="sxs-lookup"><span data-stu-id="21166-113">RNMimeDecoder</span></span>  
 <span data-ttu-id="21166-114">此元件以原生 [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] MIME 前置處理器/解碼器為基礎。</span><span class="sxs-lookup"><span data-stu-id="21166-114">This component is based on the native [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] MIME Preprocessor/Decoder.</span></span> <span data-ttu-id="21166-115">RNMimeDecoder 為 RNIF 處理作業新增下列功能：</span><span class="sxs-lookup"><span data-stu-id="21166-115">RNMimeDecoder adds the following functionality for RNIF processing:</span></span>  
  
-   <span data-ttu-id="21166-116">對於 RNIF 2.01，解密服務內容和附件 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="21166-116">For RNIF 2.01, decrypts the service content and attachments, if they are present.</span></span>  
  
-   <span data-ttu-id="21166-117">對於 RNIF 1.1，在承載結束時處理 8 位元組標頭及卸離的簽章標頭。</span><span class="sxs-lookup"><span data-stu-id="21166-117">For RNIF 1.1, handles the 8-byte header and the detached signature header at the end of the payload.</span></span>  
  
 <span data-ttu-id="21166-118">如需有關原生 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 前置處理器/解碼器的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」中的＜MIME/SMIME 解碼器管線元件＞。</span><span class="sxs-lookup"><span data-stu-id="21166-118">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] preprocessor/decoder, see "MIME/SMIME Decoder Pipeline Component" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="rndasm"></a><span data-ttu-id="21166-119">RNDAsm</span><span class="sxs-lookup"><span data-stu-id="21166-119">RNDAsm</span></span>  
 <span data-ttu-id="21166-120">此元件以原生 [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] XML 解譯器為基礎。</span><span class="sxs-lookup"><span data-stu-id="21166-120">This component is based on the native [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] XML Disassembler.</span></span> <span data-ttu-id="21166-121">RNDAsm 為 RNIF 處理作業新增下列功能：</span><span class="sxs-lookup"><span data-stu-id="21166-121">RNDAsm adds the following functionality for RNIF processing:</span></span>  
  
-   <span data-ttu-id="21166-122">如果內送文件含有 DOCTYPE 標頭，此元件會經由該標頭產生命名空間，並將內送文件中的所有節點移到該命名空間。</span><span class="sxs-lookup"><span data-stu-id="21166-122">If an incoming document has a DOCTYPE header, this component generates a namespace from it and moves all nodes in the incoming document to that namespace.</span></span>  
  
-   <span data-ttu-id="21166-123">執行訊息關聯以判斷內送訊息是否重複，若訊息重複，則會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="21166-123">Performs message correlation to determine whether an incoming message is a duplicate, and generates an error message if the message is a duplicate.</span></span>  
  
-   <span data-ttu-id="21166-124">將附件另存為訊息的額外部分。</span><span class="sxs-lookup"><span data-stu-id="21166-124">Stores attachments as additional parts of the message.</span></span>  
  
-   <span data-ttu-id="21166-125">升級訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="21166-125">Promotes message properties.</span></span>  
  
 <span data-ttu-id="21166-126">如需有關原生 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 解譯器的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」中的＜XML 解譯器管線元件＞。</span><span class="sxs-lookup"><span data-stu-id="21166-126">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Disassembler, see "XML Disassembler Pipeline Component" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="rnpartyres"></a><span data-ttu-id="21166-127">RNPartyRes</span><span class="sxs-lookup"><span data-stu-id="21166-127">RNPartyRes</span></span>  
 <span data-ttu-id="21166-128">此元件以原生 [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 合作對象解析元件為基礎。</span><span class="sxs-lookup"><span data-stu-id="21166-128">This component is based on the native [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Party Resolution component.</span></span> <span data-ttu-id="21166-129">RNPartyRes 為 RNIF 處理作業新增下列功能：</span><span class="sxs-lookup"><span data-stu-id="21166-129">RNPartyRes adds the following functionality for RNIF processing:</span></span>  
  
-   <span data-ttu-id="21166-130">如果內送訊息簽署為 BizTalk 合作對象，則對應至傳送者憑證。</span><span class="sxs-lookup"><span data-stu-id="21166-130">Maps the sender certificate if the incoming message is signed to a BizTalk party.</span></span> <span data-ttu-id="21166-131">如果內送訊息未經簽署，且交易夥伴協議允許這種情形，此元件會從 RNIF 2.01 的傳遞標頭或 RNIF 1.1 的服務標頭擷取傳送者合作對象。</span><span class="sxs-lookup"><span data-stu-id="21166-131">If the incoming message is not signed, and the trading partner agreement allows for it, this component retrieves the sender party from the Delivery header for RNIF 2.01 or the Service header for RNIF 1.1.</span></span>  
  
-   <span data-ttu-id="21166-132">驗證傳送者是否存在，以及傳送者與主要組織是否有交易夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="21166-132">Validates that the sender exists and that the sender has a trading partner agreement with the home organization.</span></span>  
  
 <span data-ttu-id="21166-133">如需有關原生 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 合作對象解析元件的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」中的＜合作對象解析管線元件＞。</span><span class="sxs-lookup"><span data-stu-id="21166-133">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] party resolution component, see "Party Resolution Pipeline Component" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="messageupdater"></a><span data-ttu-id="21166-134">MessageUpdater</span><span class="sxs-lookup"><span data-stu-id="21166-134">MessageUpdater</span></span>  
 <span data-ttu-id="21166-135">此元件為 RNIF 處理作業新增下列功能：</span><span class="sxs-lookup"><span data-stu-id="21166-135">This component adds the following functionality for RNIF processing:</span></span>  
  
-   <span data-ttu-id="21166-136">使用 ReceiveMessageNonRepudiate 元件所儲存傳輸訊息的 PIP 代碼、PIP 版本、來源合作對象、目的合作對象及訊息追蹤識別碼，更新 MessageStorageIn 資料表。</span><span class="sxs-lookup"><span data-stu-id="21166-136">Updates the MessageStorageIn table with details about the PIP Code, PIP Version, Source Party, Destination Party, and Message Tracking ID of the wire message that was stored by the ReceiveMessageNonRepudiate component.</span></span>  
  
-   <span data-ttu-id="21166-137">如果 PIP 不需要不可否認性，則標示要刪除的記錄，設定 `ToBePurged = True`。</span><span class="sxs-lookup"><span data-stu-id="21166-137">If the PIP does not require non-repudiation, marks the record for deletion, setting `ToBePurged = True`.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="21166-138">訊息流程</span><span class="sxs-lookup"><span data-stu-id="21166-138">Message Flow</span></span>  
 <span data-ttu-id="21166-139">透過 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 接收管線的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="21166-139">The message flow through the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline is as follows:</span></span>  
  
1.  <span data-ttu-id="21166-140">HTTP 配接器透過 HTTP POST 接收 RNIF 1.1 物件或 RNIF 2.01 商務訊息。</span><span class="sxs-lookup"><span data-stu-id="21166-140">The HTTP adapter receives an RNIF 1.1 object or an RNIF 2.01 business message through HTTP POST.</span></span>  
  
2.  <span data-ttu-id="21166-141">如果配接器成功接收訊息，就會擷取 RosettaNet 物件或商務訊息，然後傳送到接收管線。</span><span class="sxs-lookup"><span data-stu-id="21166-141">If the adapter successfully receives the message, the adapter extracts the RosettaNet object or business message, and routes it to the receive pipeline.</span></span>  
  
3.  <span data-ttu-id="21166-142">如果物件或商務訊息已簽署，MIME 前置處理器/解碼器會移除簽章。</span><span class="sxs-lookup"><span data-stu-id="21166-142">If the object or business message is signed, the MIME Preprocessor/Decoder removes the signature.</span></span>  
  
4.  <span data-ttu-id="21166-143">如果簽章有效，解譯器會讀取前序。</span><span class="sxs-lookup"><span data-stu-id="21166-143">If the signature is valid, the disassembler reads the preamble.</span></span>  
  
5.  <span data-ttu-id="21166-144">如果訊息是動作訊息，而且需要不可否認性 (**來源與內容的不可否認**程序組態設定中的設定是`True`)，解碼器會計算並保留摘要。</span><span class="sxs-lookup"><span data-stu-id="21166-144">If the message is an action message, and non-repudiation is required (the **Non-Repudiation of Origin and Content** setting in the process configuration settings is `True`), the Decoder calculates and persists the digest.</span></span>  
  
6.  <span data-ttu-id="21166-145">解譯器會驗證前序 (使用全域變數中的訊息 (MSG) 指導方針和前序結構描述)。</span><span class="sxs-lookup"><span data-stu-id="21166-145">The disassembler validates the preamble (with message (MSG) guidelines and the preamble schema in the global variables).</span></span>  
  
7.  <span data-ttu-id="21166-146">對於 RNIF 2.01，解譯器會讀取傳遞標頭，並使用全域變數中的 MSG 指導方針和傳遞標頭結構描述來驗證標頭。</span><span class="sxs-lookup"><span data-stu-id="21166-146">For RNIF 2.01, the disassembler reads the delivery header, and validates the header using the MSG guidelines and the delivery header schema in the global variables.</span></span>  
  
8.  <span data-ttu-id="21166-147">對於 RNIF 2.01，解譯器會從傳遞標頭擷取交易夥伴資訊，並檢查簽章以確認是否屬於交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="21166-147">For RNIF 2.01, the disassembler extracts the partner information from the delivery header, and examines the signature to verify that it belongs to the partner.</span></span>  
  
9. <span data-ttu-id="21166-148">對於 RNIF 2.01，如果內容已加密，解碼器會解密內容容器。</span><span class="sxs-lookup"><span data-stu-id="21166-148">For RNIF 2.01, if the payload is encrypted, the decoder decrypts the payload container.</span></span>  
  
10. <span data-ttu-id="21166-149">解譯器會讀取服務標頭，並使用全域變數中的 MSG 指導方針及服務標頭結構描述來驗證標頭。</span><span class="sxs-lookup"><span data-stu-id="21166-149">The disassembler reads the service header, and validates the header using the MSG guidelines and the service header schema in the global variables.</span></span>  
  
11. <span data-ttu-id="21166-150">對於 RNIF 1.1，解譯器會從服務標頭擷取交易夥伴資訊，並檢查簽章以確認是否屬於交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="21166-150">For RNIF 1.1, the disassembler extracts the partner information from the service header, and examines the signature to verify that it belongs to the partner.</span></span>  
  
12. <span data-ttu-id="21166-151">解譯器會檢查交易夥伴是否具有 PIP 的授權。</span><span class="sxs-lookup"><span data-stu-id="21166-151">The disassembler checks whether the partner is authorized for the PIP.</span></span> <span data-ttu-id="21166-152">如果沒有，解譯器將以 HTTP 403 狀態訊息回覆 HTTP POST (如有必要)，然後發佈錯誤。</span><span class="sxs-lookup"><span data-stu-id="21166-152">If not, the disassembler will reply an HTTP POST with an HTTP 403 status message, if necessary, and post an error.</span></span>  
  
13. <span data-ttu-id="21166-153">如果訊息是已簽署的動作訊息和**來源與內容的不可否認**設`True`，ReceiveMessageNonRepudiate 元件會保留原始訊息於 MessageStorageIn 資料表。</span><span class="sxs-lookup"><span data-stu-id="21166-153">If the message is a signed action message and **Non-Repudiation of Origin and Content** is set to `True`, the ReceiveMessageNonRepudiate component persists the original message in the MessageStorageIn table.</span></span>  
  
14. <span data-ttu-id="21166-154">如果訊息是已簽署的信號訊息和**不可否認性所需**設`True`，則 ReceiveMessageNonRepudiate 元件會保留信號訊息於 MessageStorageIn 資料表。</span><span class="sxs-lookup"><span data-stu-id="21166-154">If the message is a signed signal message and **Non-Repudiation Required** is set to `True`, the ReceiveMessageNonRepudiate component persists the signal message in the MessageStorageIn table.</span></span>  
  
15. <span data-ttu-id="21166-155">如果訊息基於不可否認性而保留於 MessageStorageIn 資料表，則 MessageUpdater 會使用訊息的程序組態屬性更新 MessageStorageIn 資料表。</span><span class="sxs-lookup"><span data-stu-id="21166-155">If the message was persisted in the MessageStorageIn table for non-repudiation, the MessageUpdater updates the MessageStorageIn table with properties of the process configuration of the message.</span></span>  
  
16. <span data-ttu-id="21166-156">如果訊息是先前處理動作訊息的重複動作訊息，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將發佈錯誤。</span><span class="sxs-lookup"><span data-stu-id="21166-156">If the message is an action message that is a duplicate of a previously processed action message, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will post an error.</span></span>  
  
17. <span data-ttu-id="21166-157">對於 RNIF 2.01，如果動作訊息已加密，且 HTTP 同步性 (Synchronicity) 與 PIP 同步性的需求相符，解碼器將解密內容。</span><span class="sxs-lookup"><span data-stu-id="21166-157">For RNIF 2.01, the decoder will decrypt the payload if the action message is encrypted and there is a match between the HTTP synchronicity and PIP synchronicity requirements.</span></span>  
  
18. <span data-ttu-id="21166-158">解譯器會讀取服務內容，並使用 MSG 指導方針及結構描述加以驗證。</span><span class="sxs-lookup"><span data-stu-id="21166-158">The disassembler reads the service content, and validates it using the MSG guidelines and the schema.</span></span>  
  
19. <span data-ttu-id="21166-159">對於 RNIF 2.01，解譯器會驗證資訊清單是否有效，以及是否有內容識別碼。</span><span class="sxs-lookup"><span data-stu-id="21166-159">For RNIF 2.01, the disassembler verifies that the manifest is valid and the content ID is present.</span></span>  
  
20. <span data-ttu-id="21166-160">對於 RNIF 2.01，解譯器將讀取任何附件。</span><span class="sxs-lookup"><span data-stu-id="21166-160">For RNIF 2.01, the disassembler will read any attachments.</span></span>  
  
21. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="21166-161"> 會傳送 RosettaNet 標頭、服務內容和附件至公開程序。</span><span class="sxs-lookup"><span data-stu-id="21166-161"> routes the RosettaNet headers, service content, and attachments to the public process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21166-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21166-162">See Also</span></span>  
 [<span data-ttu-id="21166-163">BTARN 中的訊息處理</span><span class="sxs-lookup"><span data-stu-id="21166-163">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)