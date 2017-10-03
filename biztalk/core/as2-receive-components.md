---
title: "AS2 接收元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdab87fd-15b9-4e3c-a4d7-984693262293
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c919a54a307a234237dd4086a0abf2a2c0c2fd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-receive-components"></a><span data-ttu-id="573d1-102">AS2 接收元件</span><span class="sxs-lookup"><span data-stu-id="573d1-102">AS2 Receive Components</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="573d1-103"> 使用數種元件接收 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="573d1-103"> uses several components to receive AS2 messages.</span></span>  
  
## <a name="as2-receive-pipelines"></a><span data-ttu-id="573d1-104">AS2 接收管線</span><span class="sxs-lookup"><span data-stu-id="573d1-104">AS2 Receive Pipelines</span></span>  
 <span data-ttu-id="573d1-105">大部分的 AS2 接收處理都是在下列 AS2 接收管線中執行。</span><span class="sxs-lookup"><span data-stu-id="573d1-105">Most AS2 receive processing is performed in the following AS2 receive pipelines.</span></span> <span data-ttu-id="573d1-106">這些管線安裝在`Microsoft.BizTalk.EdiInt.PipelineComponents.dll`\Program Files\Microsoft 20xx\Pipeline 的 BizTalk Server 元件中\\。</span><span class="sxs-lookup"><span data-stu-id="573d1-106">These pipelines are installed in `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components\\.</span></span>  
  
 <span data-ttu-id="573d1-107">**AS2EdiReceive 管線**</span><span class="sxs-lookup"><span data-stu-id="573d1-107">**AS2EdiReceive Pipeline**</span></span>  
  
 <span data-ttu-id="573d1-108">這個管線會處理透過 AS2 接收的 EDI 訊息，包括 MDN。</span><span class="sxs-lookup"><span data-stu-id="573d1-108">This pipeline processes EDI messages received over AS2, including MDNs.</span></span> <span data-ttu-id="573d1-109">這個管線包含下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="573d1-109">The pipeline consists of the following pipeline components:</span></span>  
  
-   <span data-ttu-id="573d1-110">AS2 解碼器</span><span class="sxs-lookup"><span data-stu-id="573d1-110">AS2 Decoder</span></span>  
  
-   <span data-ttu-id="573d1-111">EDI 解譯器</span><span class="sxs-lookup"><span data-stu-id="573d1-111">EDI Disassembler</span></span>  
  
-   <span data-ttu-id="573d1-112">BatchMarker</span><span class="sxs-lookup"><span data-stu-id="573d1-112">BatchMarker.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="573d1-113">使用 AS2EdiReceive 管線時，您必須將用來執行 BizTalk 外掛式主控件執行個體處理序的使用者帳戶新增至 BizTalk 應用程式使用者群組。</span><span class="sxs-lookup"><span data-stu-id="573d1-113">When using the AS2EdiReceive pipeline, you must add the user account that the BizTalk Isolated Host Instance process is running under to the BizTalk Application Users group.</span></span> <span data-ttu-id="573d1-114">AS2EdiReceive 管線會在 BizTalk 外掛式主控件執行個體處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="573d1-114">The AS2EdiReceive pipeline executes in the BizTalk Isolated Host Instance process.</span></span> <span data-ttu-id="573d1-115">AS2EdiReceive 管線會存取 SSO 存放區，而此存放區會要求使用者必須是「BizTalk 應用程式使用者」群組中的成員。</span><span class="sxs-lookup"><span data-stu-id="573d1-115">The AS2EdiReceive pipeline accesses the SSO store, which requires that the user is in the BizTalk Application Users group.</span></span>  
  
 <span data-ttu-id="573d1-116">**AS2Receive 管線**</span><span class="sxs-lookup"><span data-stu-id="573d1-116">**AS2Receive Pipeline**</span></span>  
  
 <span data-ttu-id="573d1-117">這個管線會處理透過 AS2 接收但非 EDI 編碼的訊息，</span><span class="sxs-lookup"><span data-stu-id="573d1-117">This pipeline processes messages received over AS2 when the messages are not encoded in EDI.</span></span> <span data-ttu-id="573d1-118">並且將這些訊息視為二進位訊息。</span><span class="sxs-lookup"><span data-stu-id="573d1-118">These messages are treated as binary messages.</span></span> <span data-ttu-id="573d1-119">這個管線也會處理透過 AS2 接收的 MDN。</span><span class="sxs-lookup"><span data-stu-id="573d1-119">The pipeline also processes MDNs received over AS2.</span></span> <span data-ttu-id="573d1-120">這個管線包含下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="573d1-120">The pipeline consists of the following pipeline components:</span></span>  
  
-   <span data-ttu-id="573d1-121">AS2 解碼器</span><span class="sxs-lookup"><span data-stu-id="573d1-121">AS2 Decoder</span></span>  
  
-   <span data-ttu-id="573d1-122">AS2 解譯器</span><span class="sxs-lookup"><span data-stu-id="573d1-122">AS2 Disassembler.</span></span>  
  
## <a name="as2-receive-pipeline-components"></a><span data-ttu-id="573d1-123">AS2 接收管線元件</span><span class="sxs-lookup"><span data-stu-id="573d1-123">AS2 Receive Pipeline Components</span></span>  
 <span data-ttu-id="573d1-124">AS2 接收管線會使用下列管線元件。</span><span class="sxs-lookup"><span data-stu-id="573d1-124">The AS2 receive pipelines use the following pipeline components.</span></span> <span data-ttu-id="573d1-125">這些元件安裝在`Microsoft.BizTalk.EdiInt.PipelineComponents.dll`\Program Files\Microsoft 20xx\Pipeline 的 BizTalk Server 元件中\\。</span><span class="sxs-lookup"><span data-stu-id="573d1-125">These components are installed in `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components\\.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="573d1-126">只有在 32 位元 BizTalk 主控件程序中，才支援 AS2 接收管線。</span><span class="sxs-lookup"><span data-stu-id="573d1-126">The AS2 Receive pipeline is only supported in a 32-bit BizTalk Host process.</span></span>  
  
 <span data-ttu-id="573d1-127">**AS2 解碼器**</span><span class="sxs-lookup"><span data-stu-id="573d1-127">**AS2 Decoder**</span></span>  
  
 <span data-ttu-id="573d1-128">「AS2 解碼器」包含在 AS2EDIReceivePipeline 和 AS2Receive 接收管線的解碼階段中。</span><span class="sxs-lookup"><span data-stu-id="573d1-128">The AS2 Decoder is included in the decode stage of both the AS2EDIReceivePipeline and AS2Receive receive pipelines.</span></span> <span data-ttu-id="573d1-129">它使用「BizTalk S/MIME 管線元件」，為 AS2 和 MDN 訊息提供 S/MIME 解碼功能。</span><span class="sxs-lookup"><span data-stu-id="573d1-129">It uses the BizTalk S/MIME Pipeline Component to provide S/MIME decoding functionality to AS2 and MDN messages.</span></span>  
  
-   <span data-ttu-id="573d1-130">處理 AS2/HTTP 標頭</span><span class="sxs-lookup"><span data-stu-id="573d1-130">Processes AS2/HTTP headers</span></span>  
  
-   <span data-ttu-id="573d1-131">如果訊息已簽署，便驗證簽章</span><span class="sxs-lookup"><span data-stu-id="573d1-131">Verifies the signature, if the message was signed</span></span>  
  
-   <span data-ttu-id="573d1-132">如果訊息已加密，便解碼訊息 (適用於 EDI/AS2 訊息，而非 MDN)</span><span class="sxs-lookup"><span data-stu-id="573d1-132">Decrypts the messages, if the message was encrypted (for an EDI/AS2 message, not an MDN)</span></span>  
  
-   <span data-ttu-id="573d1-133">如果訊息已壓縮，便解壓縮訊息</span><span class="sxs-lookup"><span data-stu-id="573d1-133">Decompresses the message, if the message was compressed</span></span>  
  
-   <span data-ttu-id="573d1-134">協調收到的 MDN 與原始輸出訊息</span><span class="sxs-lookup"><span data-stu-id="573d1-134">Reconciles a received MDN with the original outbound message</span></span>  
  
-   <span data-ttu-id="573d1-135">在不可否認性的資料庫中更新記錄並使其相互關聯</span><span class="sxs-lookup"><span data-stu-id="573d1-135">Updates and correlates records in the non-repudiation database</span></span>  
  
-   <span data-ttu-id="573d1-136">寫入 AS2 狀態報告的記錄</span><span class="sxs-lookup"><span data-stu-id="573d1-136">Writes records for AS2 status reporting</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="573d1-137">如果接收端處理 AS2 訊息期間發生錯誤，「AS2 解碼器」會停止進一步的下游訊息處理 (例如，EDI 解譯器將不會剖析交換)。</span><span class="sxs-lookup"><span data-stu-id="573d1-137">If an error occurs during receive-side processing of an AS2 message, the AS2 Decoder will stop further downstream message processing (for example, the EDI disassembler will not parse the interchange).</span></span> <span data-ttu-id="573d1-138">不過，「AS2 解譯器」或「EDI 解譯器」仍必須產生 MDN。</span><span class="sxs-lookup"><span data-stu-id="573d1-138">However, the AS2 Disassembler or EDI Disassembler must still generate the MDN.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="573d1-139">AS2 訊息使用八位元編碼，</span><span class="sxs-lookup"><span data-stu-id="573d1-139">Eight-bit encoding is used on AS2 messages.</span></span> <span data-ttu-id="573d1-140">Base64 編碼只適用於 AS2 訊息和 MDN 中的簽章。</span><span class="sxs-lookup"><span data-stu-id="573d1-140">Base64 encoding is only applied to signatures in AS2 messages and MDNs.</span></span>  
  
 <span data-ttu-id="573d1-141">**AS2 解譯器**</span><span class="sxs-lookup"><span data-stu-id="573d1-141">**AS2 Disassembler**</span></span>  
  
 <span data-ttu-id="573d1-142">在 AS2Receive 接收管線中，「AS2 解譯器」會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="573d1-142">In the AS2Receive receive pipeline, the AS2 Disassembler does the following:</span></span>  
  
-   <span data-ttu-id="573d1-143">判斷 MDN 是否必要，以及 MDN 應該是同步還是非同步。</span><span class="sxs-lookup"><span data-stu-id="573d1-143">Determines whether an MDN is required, and whether the MDN should be synchronous or asynchronous.</span></span>  
  
-   <span data-ttu-id="573d1-144">產生 AS2 MDN。</span><span class="sxs-lookup"><span data-stu-id="573d1-144">Generates an AS2 MDN.</span></span>  
  
-   <span data-ttu-id="573d1-145">如果是同步 MDN，則會將 `EdiIntAS.IsAS2AsynchronousMDN` 屬性設定為 False；如果是非同步的 MDN，則會將該屬性設定為 True。</span><span class="sxs-lookup"><span data-stu-id="573d1-145">If the MDN is synchronous, sets the `EdiIntAS.IsAS2AsynchronousMDN` property to False; if asynchronous, sets the property to True.</span></span>  
  
-   <span data-ttu-id="573d1-146">針對 MDN 設定相互關聯 Token 和屬性。</span><span class="sxs-lookup"><span data-stu-id="573d1-146">Sets the correlation tokens and properties on the MDN.</span></span>  
  
 <span data-ttu-id="573d1-147">**EDI 解譯器**</span><span class="sxs-lookup"><span data-stu-id="573d1-147">**EDI Disassembler**</span></span>  
  
 <span data-ttu-id="573d1-148">在 AS2EDIReceivePipeline 中，「EDI 解譯器」會將 EDI 訊息剖析為中繼 XML 訊息以供處理。</span><span class="sxs-lookup"><span data-stu-id="573d1-148">In the AS2EDIReceivePipeline, the EDI Disassembler will parse the EDI message into intermediate XML message(s) for processing.</span></span> <span data-ttu-id="573d1-149">如需詳細資訊，請參閱[EDI 解譯器的運作方式](../core/how-the-edi-disassembler-works.md)。</span><span class="sxs-lookup"><span data-stu-id="573d1-149">For more information, see [How the EDI Disassembler Works](../core/how-the-edi-disassembler-works.md).</span></span>  
  
 <span data-ttu-id="573d1-150">**BatchMarker**</span><span class="sxs-lookup"><span data-stu-id="573d1-150">**BatchMarker**</span></span>  
  
 <span data-ttu-id="573d1-151">在 AS2EDIReceivePipeline 中，BatchMarker 管線元件會設定批次交換處理所需的兩個內容屬性：AgreementPartIdForSend 和 ToBeBatched。</span><span class="sxs-lookup"><span data-stu-id="573d1-151">In the AS2EDIReceivePipeline, the BatchMarker pipeline component sets the AgreementPartIdForSend and ToBeBatched context properties that are required for processing a batched interchange.</span></span> <span data-ttu-id="573d1-152">此元件包含在 AS2EDIReceive 管線的最後一個階段 （協議解析）。</span><span class="sxs-lookup"><span data-stu-id="573d1-152">This component is included in the last stage (agreement resolution) of the AS2EDIReceive pipeline.</span></span> <span data-ttu-id="573d1-153">所有將批次處理 EDI 訊息的管線都應該包含 BatchMarker 管線元件。</span><span class="sxs-lookup"><span data-stu-id="573d1-153">All pipelines that will batch EDI messages should include the BatchMarker pipeline component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="573d1-154">BatchMarker 管線元件不會包含在用來處理非 EDI 訊息的 AS2Receive 管線中。</span><span class="sxs-lookup"><span data-stu-id="573d1-154">The BatchMarker pipeline component is not included in the AS2Receive pipeline that is used to process non-EDI messages.</span></span> <span data-ttu-id="573d1-155">不過，您可以在不包含「EDI 解譯器」的自訂接收管線中加入 BatchMarker 元件。</span><span class="sxs-lookup"><span data-stu-id="573d1-155">However, you can include the BatchMarker component in a custom receive pipeline that does not include the EDI Dissassembler.</span></span> <span data-ttu-id="573d1-156">如需詳細資訊，請參閱 「 非 EDI 訊息在 BatchMarker 元件處理 >[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="573d1-156">For more information, see "Processing Non-EDI Messages in the BatchMarker Component" in [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).</span></span>  
  
## <a name="http-adapter"></a><span data-ttu-id="573d1-157">HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="573d1-157">HTTP Adapter</span></span>  
 <span data-ttu-id="573d1-158">接收埠和位置用於 AS2 處理使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="573d1-158">The receive ports and locations used for AS2 processing use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Adapter.</span></span> <span data-ttu-id="573d1-159">HTTP 配接器設定適用於單向或要求-回應傳輸。</span><span class="sxs-lookup"><span data-stu-id="573d1-159">The HTTP Adapter is configured for either one-way and request-response transmission.</span></span>  
  
## <a name="non-repudiation-database"></a><span data-ttu-id="573d1-160">不可否認性的資料庫</span><span class="sxs-lookup"><span data-stu-id="573d1-160">Non-Repudiation Database</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="573d1-161"> 會使用不可否認性的資料庫 (BizTalkDTADb 資料庫的 EdiMessageContent 資料表) 來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="573d1-161"> uses the non-repudiation database (the EdiMessageContent table of the BizTalkDTADb database) to do the following:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="573d1-162">只有在已核取其中一個不可否認性的儲存區協議屬性時，BizTalkDTADb 資料庫中才有 EdiMessageContent 資料表。</span><span class="sxs-lookup"><span data-stu-id="573d1-162">The EdiMessageContent table exists in the BizTalkDTADb database only if one of the non-repudiation storage agreement properties has been checked.</span></span>  
  
-   <span data-ttu-id="573d1-163">為已簽署的 MDN 提供不可否認性的線索</span><span class="sxs-lookup"><span data-stu-id="573d1-163">Provides a non-repudiation trail for signed MDN</span></span>  
  
-   <span data-ttu-id="573d1-164">使輸出訊息與其內送 MDN 相互關聯</span><span class="sxs-lookup"><span data-stu-id="573d1-164">Correlates an outbound message with its incoming MDN</span></span>  
  
-   <span data-ttu-id="573d1-165">儲存各種狀態變更的訊息</span><span class="sxs-lookup"><span data-stu-id="573d1-165">Stores messages through various state changes</span></span>  
  
-   <span data-ttu-id="573d1-166">使錯誤碼與 HTTP 回應和 MDN 產生關聯</span><span class="sxs-lookup"><span data-stu-id="573d1-166">Associates error codes with HTTP Response and MDN</span></span>  
  
-   <span data-ttu-id="573d1-167">根據篩選準則顯示記錄</span><span class="sxs-lookup"><span data-stu-id="573d1-167">Displays records based on filter criteria</span></span>  
  
-   <span data-ttu-id="573d1-168">封存已標示的記錄</span><span class="sxs-lookup"><span data-stu-id="573d1-168">Archives marked records.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="573d1-169">為了確保不可否認性接收資料庫中所儲存訊息的真實性和完整性，資料庫中將儲存的所有訊息，包括原始 AS2 訊息和 MDN，都應使用數位簽章。</span><span class="sxs-lookup"><span data-stu-id="573d1-169">To ensure authentication and integrity of messages stored in the non-repudiation receipt database, digital signatures should be used on all messages that will be stored in the database, both original AS2 messages and MDNs.</span></span> <span data-ttu-id="573d1-170">如需詳細資訊，請參閱的 9.1 節 < [RFC 1430、 」 以 MIME 為基礎安全端對端商務資料交換使用 HTTP，Applicability Statement 2 (AS2) >](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212))。</span><span class="sxs-lookup"><span data-stu-id="573d1-170">For more information, see section 9.1 of [RFC 1430, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)"](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573d1-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="573d1-171">See Also</span></span>  
 [<span data-ttu-id="573d1-172">BizTalk Server 如何接收 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="573d1-172">How BizTalk Server Receives AS2 Messages</span></span>](../core/how-biztalk-server-receives-as2-messages.md)