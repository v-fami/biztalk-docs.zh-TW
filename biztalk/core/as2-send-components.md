---
title: AS2 傳送元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35113732-fe32-4776-be25-971ec66c365c
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3378dbb623c2d47a56946805908f9d104500a8ac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994559"
---
# <a name="as2-send-components"></a><span data-ttu-id="b0320-102">AS2 傳送元件</span><span class="sxs-lookup"><span data-stu-id="b0320-102">AS2 Send Components</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b0320-103"> 使用數種元件來傳送 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="b0320-103"> uses several components to send AS2 messages.</span></span>  
  
## <a name="as2-send-pipelines"></a><span data-ttu-id="b0320-104">AS2 傳送管線</span><span class="sxs-lookup"><span data-stu-id="b0320-104">AS2 Send Pipelines</span></span>  
 <span data-ttu-id="b0320-105">大部分 AS2 傳送處理會在下列 AS2 傳送管線中執行。</span><span class="sxs-lookup"><span data-stu-id="b0320-105">Most AS2 send processing is performed in the following AS2 send pipelines.</span></span> <span data-ttu-id="b0320-106">這些管線安裝在`Microsoft.BizTalk.Edi.EdiIntPipelines.dll`\Program Files\Microsoft 20xx\Pipeline 的 BizTalk Server 元件中。</span><span class="sxs-lookup"><span data-stu-id="b0320-106">These pipelines are installed in `Microsoft.BizTalk.Edi.EdiIntPipelines.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0320-107">只有在 32 位元 BizTalk 主控件程序中，才支援 AS2 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="b0320-107">The AS2 Send pipeline is only supported in a 32-bit BizTalk Host process.</span></span>  
  
 <span data-ttu-id="b0320-108">**AS2EDISend 管線**</span><span class="sxs-lookup"><span data-stu-id="b0320-108">**AS2EDISend Pipeline**</span></span>  
  
 <span data-ttu-id="b0320-109">這個管線會透過 AS2 產生和傳送 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="b0320-109">This pipeline generates and sends EDI messages over AS2.</span></span> <span data-ttu-id="b0320-110">這個管線包含下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="b0320-110">The pipeline consists of the following pipeline components:</span></span>  
  
- <span data-ttu-id="b0320-111">EDI 組合器</span><span class="sxs-lookup"><span data-stu-id="b0320-111">EDI Assembler</span></span>  
  
- <span data-ttu-id="b0320-112">AS2 編碼器</span><span class="sxs-lookup"><span data-stu-id="b0320-112">AS2 Encoder</span></span>  
  
  <span data-ttu-id="b0320-113">此管線不會用來透過 AS2 產生和傳送 MDN，因為 MDN 不需要經過 EDI 組合器處理。</span><span class="sxs-lookup"><span data-stu-id="b0320-113">This pipeline is not used to generate and send MDNs over AS2, because the MDN does not need to be processed by the EDI Assembler.</span></span> <span data-ttu-id="b0320-114">請使用 AS2SendPipeline 傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="b0320-114">Use the AS2SendPipeline to send MDNs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0320-115">不支援從協調流程執行 AS2EDISend 管線。</span><span class="sxs-lookup"><span data-stu-id="b0320-115">Running the AS2EDISend pipeline from an orchestration is not supported.</span></span>  
  
 <span data-ttu-id="b0320-116">**AS2Send 管線**</span><span class="sxs-lookup"><span data-stu-id="b0320-116">**AS2Send Pipeline**</span></span>  
  
 <span data-ttu-id="b0320-117">這個管線會在訊息未以 EDI 編碼時，透過 AS2 傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b0320-117">This pipeline sends messages over AS2 when the messages are not encoded in EDI.</span></span> <span data-ttu-id="b0320-118">此外還會透過 AS2 傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="b0320-118">It also sends MDNs over AS2.</span></span> <span data-ttu-id="b0320-119">這個管線包含下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="b0320-119">The pipeline consists of the following pipeline components:</span></span>  
  
- <span data-ttu-id="b0320-120">AS2 編碼器。</span><span class="sxs-lookup"><span data-stu-id="b0320-120">AS2 Encoder.</span></span>  
  
  <span data-ttu-id="b0320-121">如果要透過 AS2 傳送的訊息不是 EDI 也不是 XML 訊息，則您可以建立自訂的 AS2Send 管線來處理這些訊息。</span><span class="sxs-lookup"><span data-stu-id="b0320-121">If the messages to be sent over AS2 are neither EDI nor XML messages, you can create a customized AS2Send pipeline to handle these messages.</span></span> <span data-ttu-id="b0320-122">此管線必須擁有自訂的組合器，才能在以 EDIINT/AS2 編碼訊息之前，先在 BizTalk Server 中將中繼 XML 轉換成其他格式。</span><span class="sxs-lookup"><span data-stu-id="b0320-122">This pipeline must have a customized assembler to convert the intermediate XML in BizTalk Server into the other format before encoding the message in EDIINT/AS2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0320-123">不支援從協調流程執行 AS2Send 管線。</span><span class="sxs-lookup"><span data-stu-id="b0320-123">Running the AS2Send pipeline from an orchestration is not supported.</span></span>  
  
## <a name="as2-send-pipeline-components"></a><span data-ttu-id="b0320-124">AS2 傳送管線元件</span><span class="sxs-lookup"><span data-stu-id="b0320-124">AS2 Send Pipeline Components</span></span>  
 <span data-ttu-id="b0320-125">AS2 傳送管線會使用下列管線元件。</span><span class="sxs-lookup"><span data-stu-id="b0320-125">The AS2 send pipelines use the following pipeline components.</span></span> <span data-ttu-id="b0320-126">這些元件會安裝在`Microsoft.BizTalk.EdiInt.PipelineComponents.dll`\Program Files\Microsoft 20xx\Pipeline 的 BizTalk Server 元件中\\。</span><span class="sxs-lookup"><span data-stu-id="b0320-126">These components are installed in `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components\\.</span></span>  
  
 <span data-ttu-id="b0320-127">**EDI 組合器**</span><span class="sxs-lookup"><span data-stu-id="b0320-127">**EDI Assembler**</span></span>  
  
 <span data-ttu-id="b0320-128">在 EDIINT 傳送管線中，EDI 組合器會將 EDI 交換序列化。</span><span class="sxs-lookup"><span data-stu-id="b0320-128">In the EDIINT send pipelines, the EDI Assembler serializes the EDI interchange.</span></span>  
  
 <span data-ttu-id="b0320-129">**AS2 編碼器**</span><span class="sxs-lookup"><span data-stu-id="b0320-129">**AS2 Encoder**</span></span>  
  
 <span data-ttu-id="b0320-130">AS2 編碼器包含在 AS2 傳送管線的編碼階段中。</span><span class="sxs-lookup"><span data-stu-id="b0320-130">The AS2 Encoder is included in the encode stage of the AS2 send pipelines.</span></span> <span data-ttu-id="b0320-131">它會使用 BizTalk S/MIME 管線元件為 AS2 和 MDN 訊息提供 S/MIME 編碼功能。</span><span class="sxs-lookup"><span data-stu-id="b0320-131">It uses the BizTalk S/MIME pipeline component to provide S/MIME encoding functionality to AS2 and MDN messages.</span></span> <span data-ttu-id="b0320-132">AS2 編碼器會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="b0320-132">The AS2 Encoder does the following:</span></span>  
  
-   <span data-ttu-id="b0320-133">套用 AS2/HTTP 標頭</span><span class="sxs-lookup"><span data-stu-id="b0320-133">Applies AS2/HTTP headers</span></span>  
  
-   <span data-ttu-id="b0320-134">簽署外寄訊息 (如果已啟用)</span><span class="sxs-lookup"><span data-stu-id="b0320-134">Signs outgoing messages, if enabled</span></span>  
  
-   <span data-ttu-id="b0320-135">加密外寄訊息 (如果已啟用) (針對 EDI/AS2 而非 MDN)</span><span class="sxs-lookup"><span data-stu-id="b0320-135">Encrypts outgoing messages, if enabled (for EDI/AS2, not MDN)</span></span>  
  
-   <span data-ttu-id="b0320-136">壓縮訊息 (如果已啟用) (針對 EDI/AS2 而非 MDN)</span><span class="sxs-lookup"><span data-stu-id="b0320-136">Compresses the message, if enabled (for EDI/AS2, not MDN)</span></span>  
  
-   <span data-ttu-id="b0320-137">以電傳格式儲存內容，如果**為輸出的解碼 AS2 訊息啟用 NRR**屬性，並選取以電傳格式儲存訊息，如果**為輸出的編碼 AS2 訊息啟用 NRR**選取屬性</span><span class="sxs-lookup"><span data-stu-id="b0320-137">Stores the payload in wire format if the **NRR enabled for outbound decoded AS2 messages** property is selected, and stores the message in wire format if the **NRR enabled for outbound encoded AS2 messages** property is selected</span></span>  
  
-   <span data-ttu-id="b0320-138">計算 MIC 值並將它儲存到資料存放區</span><span class="sxs-lookup"><span data-stu-id="b0320-138">Computes the MIC value and stores it in the data store</span></span>  
  
-   <span data-ttu-id="b0320-139">在不可否認性的接收資料庫中更新記錄並使其相互關聯</span><span class="sxs-lookup"><span data-stu-id="b0320-139">Updates and correlates records in the non-repudiation receipt database</span></span>  
  
-   <span data-ttu-id="b0320-140">針對 MDN 訊息，做為通過管線使用，路由 AS2Receive 接收管線中的 AS2 解碼器產生的 MDN。</span><span class="sxs-lookup"><span data-stu-id="b0320-140">For MDN messages, acts as a passthrough pipeline, routing the MDN generated by the AS2 Decoder in the AS2Receive receive pipeline.</span></span> <span data-ttu-id="b0320-141">如果組態設定需要，AS2 編碼器將簽署 MDN。</span><span class="sxs-lookup"><span data-stu-id="b0320-141">If required by the configuration settings, the AS2 Encoder will sign the MDN.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0320-142">AS2 訊息使用八位元編碼，</span><span class="sxs-lookup"><span data-stu-id="b0320-142">Eight-bit encoding is used on AS2 messages.</span></span> <span data-ttu-id="b0320-143">Base64 編碼只適用於 AS2 訊息和 MDN 中的簽章。</span><span class="sxs-lookup"><span data-stu-id="b0320-143">Base64 encoding is only applied to signatures in AS2 messages and MDNs.</span></span>  
  
## <a name="http-adapter"></a><span data-ttu-id="b0320-144">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="b0320-144">HTTP Adapter</span></span>  
 <span data-ttu-id="b0320-145">EDIINT AS2 處理所使用的傳送埠會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="b0320-145">The send ports used for EDIINT AS2 processing use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Adapter.</span></span> <span data-ttu-id="b0320-146">HTTP 配接器設定同時適用於單向和請求-回應傳輸。</span><span class="sxs-lookup"><span data-stu-id="b0320-146">The HTTP Adapter is configured in both one-way and solicit-response transmission.</span></span>  
  
## <a name="non-repudiation-database"></a><span data-ttu-id="b0320-147">不可否認性的資料庫</span><span class="sxs-lookup"><span data-stu-id="b0320-147">Non-Repudiation Database</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b0320-148"> 會使用不可否認性的資料庫 (BizTalkDTADb 資料庫的 EdiMessageContent 資料表) 來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b0320-148"> uses the non-repudiation database (the EdiMessageContent table of the BizTalkDTADb database) to do the following:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0320-149">只有在已核取其中一個不可否認性的儲存區協議屬性時，BizTalkDTADb 資料庫中才有 EdiMessageContent 資料表。</span><span class="sxs-lookup"><span data-stu-id="b0320-149">The EdiMessageContent table exists in the BizTalkDTADb database only if one of the non-repudiation storage agreement properties are checked.</span></span>  
  
-   <span data-ttu-id="b0320-150">為已簽署的 MDN 提供不可否認性的線索</span><span class="sxs-lookup"><span data-stu-id="b0320-150">Provide a non-repudiation trail for signed MDN</span></span>  
  
-   <span data-ttu-id="b0320-151">使輸出訊息與其內送 MDN 相互關聯</span><span class="sxs-lookup"><span data-stu-id="b0320-151">Correlate an outbound message with its incoming MDN</span></span>  
  
-   <span data-ttu-id="b0320-152">儲存各種狀態變更的訊息</span><span class="sxs-lookup"><span data-stu-id="b0320-152">Store messages through various state changes</span></span>  
  
-   <span data-ttu-id="b0320-153">使錯誤碼與 HTTP 回應和 MDN 產生關聯</span><span class="sxs-lookup"><span data-stu-id="b0320-153">Associate error codes with HTTP Response and MDN</span></span>  
  
-   <span data-ttu-id="b0320-154">根據篩選準則顯示記錄</span><span class="sxs-lookup"><span data-stu-id="b0320-154">Display records based on filter criteria</span></span>  
  
-   <span data-ttu-id="b0320-155">封存已標示的記錄</span><span class="sxs-lookup"><span data-stu-id="b0320-155">Archive marked records</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0320-156">為了確保不可否認性資料庫中所儲存訊息的真實性和完整性，資料庫中將儲存的所有訊息，包括原始 AS2 訊息和 MDN，都應使用數位簽章。</span><span class="sxs-lookup"><span data-stu-id="b0320-156">To ensure authentication and integrity of messages stored in the non-repudiation database, digital signatures should be used on all messages that will be stored in the database, both original AS2 messages and MDNs.</span></span> <span data-ttu-id="b0320-157">如需詳細資訊，請參閱的 9.1 節[RFC 1430、 」 以 MIME 為基礎安全端對端商務資料交換使用 HTTP，Applicability Statement 2 (AS2) >](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212))。</span><span class="sxs-lookup"><span data-stu-id="b0320-157">For more information, see section 9.1 of [RFC 1430, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)"](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0320-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0320-158">See Also</span></span>  
 [<span data-ttu-id="b0320-159">BizTalk Server 如何傳送 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="b0320-159">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)