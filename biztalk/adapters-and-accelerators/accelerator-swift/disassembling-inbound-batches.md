---
title: 解譯輸入批次使用 SWIFT |Microsoft Docs
description: 解除批次處理輸入的訊息，並自訂結構描述的批次使用 BizTalk Server 中的 SWIFT 加速器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11cb5672-1155-4648-b1fd-c9a3bc30e351
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f234ca9c867d978216972f8359c77de88aeebfa8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976239"
---
# <a name="disassemble-inbound-batches"></a><span data-ttu-id="02105-103">解譯輸入批次</span><span class="sxs-lookup"><span data-stu-id="02105-103">Disassemble Inbound Batches</span></span>

## <a name="debatch-inbound-message"></a><span data-ttu-id="02105-104">解除批次處理輸入的訊息</span><span class="sxs-lookup"><span data-stu-id="02105-104">Debatch inbound message</span></span>
<span data-ttu-id="02105-105">SWIFT 解譯器可輸入解除批次中的方法，它可以處理，或解譯輸入批次 （檔案或包含多個 SWIFT 訊息的訊息）。</span><span class="sxs-lookup"><span data-stu-id="02105-105">The SWIFT disassembler is able to inbound debatching in which it processes or disassembles inbound batches (files or messages containing multiple SWIFT messages).</span></span> <span data-ttu-id="02105-106">您會讓使用 SWIFT 解譯器設定屬性，具有相同名稱的輸入解除批次處理。</span><span class="sxs-lookup"><span data-stu-id="02105-106">You enable inbound debatching using the SWIFT disassembler configuration property of the same name.</span></span> <span data-ttu-id="02105-107">啟用輸入解除批次處理後，SWIFT 解譯器會預期要包含多個 SWIFT 訊息的批次接收所有訊息。</span><span class="sxs-lookup"><span data-stu-id="02105-107">After you enable inbound debatching, the SWIFT disassembler expects all messages that it receives to be batches that include multiple SWIFT messages.</span></span> <span data-ttu-id="02105-108">批次可能會或可能不會包含批次的信封 （批次標頭和批次結尾），以及每個個別的 SWIFT 訊息批次中可能會或可能不會包含訊息信封 （訊息標頭和訊息結尾）。</span><span class="sxs-lookup"><span data-stu-id="02105-108">A batch may or may not include a batch envelope (a batch header and a batch trailer), and each individual SWIFT message within a batch may or may not include a message envelope (a message header and a message trailer).</span></span> <span data-ttu-id="02105-109">您可以設定使用下列的 SWIFT 解譯器組態屬性這些批次屬性 （格式）：</span><span class="sxs-lookup"><span data-stu-id="02105-109">You can configure these batch attributes (formats) using the following SWIFT disassembler configuration properties:</span></span>  
  
- <span data-ttu-id="02105-110">批次標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="02105-110">Batch Header Schema</span></span>  
  
- <span data-ttu-id="02105-111">批次結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="02105-111">Batch Trailer Schema</span></span>  
  
- <span data-ttu-id="02105-112">訊息標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="02105-112">Message Header Schema</span></span>  
  
- <span data-ttu-id="02105-113">訊息結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="02105-113">Message Trailer Schema</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="02105-114">設定任何這些屬性，以 「 無 」 表示輸入的批次不包含該特定的組件。</span><span class="sxs-lookup"><span data-stu-id="02105-114">Setting any of these properties to "None" indicates that the inbound batch does not include that particular part.</span></span>  
  
  <span data-ttu-id="02105-115">SWIFT 解譯器會預期要有下列結構的所有輸入批次：</span><span class="sxs-lookup"><span data-stu-id="02105-115">The SWIFT disassembler expects all inbound batches to have the following structure:</span></span>  
  
  <span data-ttu-id="02105-116">**批次標頭**</span><span class="sxs-lookup"><span data-stu-id="02105-116">**Batch Header**</span></span>  
  
  <span data-ttu-id="02105-117">**訊息標頭**</span><span class="sxs-lookup"><span data-stu-id="02105-117">**Message Header**</span></span>  
  
  <span data-ttu-id="02105-118">**SWIFT 的交換訊息 （SWIFT 區塊的 1 到 5）**</span><span class="sxs-lookup"><span data-stu-id="02105-118">**SWIFT Interchange/Message (SWIFT Blocks 1 to 5)**</span></span>  
  
  <span data-ttu-id="02105-119">**訊息結尾**</span><span class="sxs-lookup"><span data-stu-id="02105-119">**Message Trailer**</span></span>  
  
  <span data-ttu-id="02105-120">**批次結尾**</span><span class="sxs-lookup"><span data-stu-id="02105-120">**Batch Trailer**</span></span>  
  
  <span data-ttu-id="02105-121">在此結構中，您可以考慮 「 訊息區塊 」 要**訊息標頭 – SWIFT 交換 – 訊息結尾**組件。</span><span class="sxs-lookup"><span data-stu-id="02105-121">Within this structure, you can consider a "message block" to be the **Message Header – SWIFT Interchange – Message Trailer** parts.</span></span> <span data-ttu-id="02105-122">一系列的多個 「 訊息區塊 」 是由批次中的多個 SWIFT 訊息所組成。</span><span class="sxs-lookup"><span data-stu-id="02105-122">A series of multiple "message blocks" makes up the multiple SWIFT messages in a batch.</span></span> <span data-ttu-id="02105-123">批次標頭，訊息標頭，訊息結尾和批次結尾是選擇性的但是重複項目之間必須一致。</span><span class="sxs-lookup"><span data-stu-id="02105-123">The Batch Header, Message Header, Message Trailer, and Batch Trailer are optional, but must be consistent across repetitions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02105-124">請勿混淆 SWIFT 的標頭和結尾區塊的訊息信封 （訊息標頭和訊息結尾）。</span><span class="sxs-lookup"><span data-stu-id="02105-124">Do not confuse the message envelope (Message Header and Message Trailer) with the SWIFT header and trailer blocks.</span></span> <span data-ttu-id="02105-125">在批次內容中，您應該檢視 SWIFT 訊息 （交換），做為一個整體 (atomic) 的單位包括 SWIFT 標頭和結尾區塊。</span><span class="sxs-lookup"><span data-stu-id="02105-125">In the context of batches, you should view the SWIFT message (interchange), including the SWIFT header and trailer blocks, as a holistic (atomic) unit.</span></span> <span data-ttu-id="02105-126">在此情況下，訊息標頭和訊息結尾指信封包裝批次中的每個 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="02105-126">In this context, the Message Header and Message Trailer refer to the envelope that wraps each SWIFT message in a batch.</span></span>  
  
 <span data-ttu-id="02105-127">若要更正式的說法 express 這個結構，其選項，其可重複性，請考慮如何[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]定義批次：</span><span class="sxs-lookup"><span data-stu-id="02105-127">To express this structure, its options, and its repeatability more formally, consider how [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] defines a batch:</span></span>  
  
- <span data-ttu-id="02105-128">**批次標頭**由**BH**</span><span class="sxs-lookup"><span data-stu-id="02105-128">**Batch Header** is represented by **BH**</span></span>  
  
- <span data-ttu-id="02105-129">**訊息標頭**由**MH**</span><span class="sxs-lookup"><span data-stu-id="02105-129">**Message Header** is represented by **MH**</span></span>  
  
- <span data-ttu-id="02105-130">**SWIFT 交換**由**SI**</span><span class="sxs-lookup"><span data-stu-id="02105-130">**SWIFT Interchange** is represented by **SI**</span></span>  
  
- <span data-ttu-id="02105-131">**訊息結尾**由**MT**</span><span class="sxs-lookup"><span data-stu-id="02105-131">**Message Trailer** is represented by **MT**</span></span>  
  
- <span data-ttu-id="02105-132">**批次結尾**由**BT**。</span><span class="sxs-lookup"><span data-stu-id="02105-132">**Batch Trailer** is represented by **BT**.</span></span>  
  
  <span data-ttu-id="02105-133">運算式，表示預期的批次結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="02105-133">The expression that represents the expected batch structure is as follows:</span></span>  
  
  `[BH] ([MH] SI [MT])* [BT]  `
  
  <span data-ttu-id="02105-134">在方括號 ( `[ ] ` ) 表示的部分是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="02105-134">The brackets ( `[ ] ` ) indicate that the part is optional.</span></span> <span data-ttu-id="02105-135">星號 (**\\* \* *) 表示的區塊是可重複。任何使用者建立的訊息批次，則必須使用訊息標頭 (*<em>MH</em>*) 和結尾 (*<em>MT</em>*) 中的每個重複以一致的方式 (`[MH] SI [MT]`)。</span><span class="sxs-lookup"><span data-stu-id="02105-135">The asterisk (\**\\*\*\*)indicates that the block is repeatable. Whoever builds the message batch must use the message header (*<em>MH</em>*) and trailer (*<em>MT</em>\*) consistently in each repetition of (`[MH] SI [MT]`).</span></span>  
  
  <span data-ttu-id="02105-136">SWIFT 解譯器可處理任何遵守上述的結構的輸入批次，因為在結構中的每個組件符合一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="02105-136">The SWIFT disassembler is able to process any inbound batch that obeys the above structure, because each part in the structure conforms to a flat-file schema.</span></span> <span data-ttu-id="02105-137">不過，如果您不使用訊息標頭/結尾與選擇性的批次標頭/結尾，訊息將會不符合這些結構描述。</span><span class="sxs-lookup"><span data-stu-id="02105-137">However, if you do not use the optional batch header/trailer and message header/trailer, the message will not conform to those schemas.</span></span> <span data-ttu-id="02105-138">如此一來，批次標頭結構描述、 批次結尾結構描述、 訊息標頭結構描述，並設定為 「 無 」 的訊息結尾結構描述屬性，會有包含連續的 SWIFT 訊息的批次。</span><span class="sxs-lookup"><span data-stu-id="02105-138">As a result, a batch containing only consecutive SWIFT messages will have the Batch Header Schema, Batch Trailer Schema, Message Header Schema, and Message Trailer Schema properties set to "None".</span></span>  

## <a name="customize-schemas-for-batching"></a><span data-ttu-id="02105-139">自訂批次結構的描述</span><span class="sxs-lookup"><span data-stu-id="02105-139">Customize schemas for batching</span></span>  
 <span data-ttu-id="02105-140">您可以自訂訊息標頭/結尾與批次標頭/結尾的結構描述。</span><span class="sxs-lookup"><span data-stu-id="02105-140">You can customize the schemas for the batch header/trailer and message header/trailer.</span></span> <span data-ttu-id="02105-141">舉例來說，下列批次：</span><span class="sxs-lookup"><span data-stu-id="02105-141">An example is the following batch:</span></span>  
  
```  
4  
SWIFT Message # 1  
$  
SWIFT Message # 2  
$  
SWIFT Message # 3  
$  
SWIFT Message # 4  
$  
```  
  
 <span data-ttu-id="02105-142">若要處理這種類型的批次，您會設定批次結構描述屬性如下所示：</span><span class="sxs-lookup"><span data-stu-id="02105-142">To handle this type of batch, you would set the schema properties for the batch as follows:</span></span>  
  
- <span data-ttu-id="02105-143">您可以設定批次標頭結構描述屬性至剖析單一數字 （訊息計數） 以換行字元分隔的一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="02105-143">You set the Batch Header Schema property to a flat-file schema that parses a single number (message count) delimited by carriage-return.</span></span>  
  
- <span data-ttu-id="02105-144">設定成剖析單一的 $ 符號和換行字元的一般檔案結構描述的訊息結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="02105-144">You set the Message Trailer Schema to a flat-file schema that parses a single $ symbol and carriage-return.</span></span>  
  
- <span data-ttu-id="02105-145">您可以設定剩餘信封結構描述 （批次結尾結構描述和訊息標頭結構描述） 為 None。</span><span class="sxs-lookup"><span data-stu-id="02105-145">You set the remaining envelope schemas (Batch Trailer Schema and Message Header Schema) to None.</span></span>  
  
  <span data-ttu-id="02105-146">您可以設定 SWIFT 解譯器，它會處理任何 SWIFT 的訊息批次建立，並指定一般檔案信封結構描述的適當組合。</span><span class="sxs-lookup"><span data-stu-id="02105-146">You can configure the SWIFT disassembler such that it processes just about any SWIFT message batch by creating and specifying the appropriate combination of flat-file envelope schemas.</span></span> <span data-ttu-id="02105-147">這項功能是非常大的彈性。</span><span class="sxs-lookup"><span data-stu-id="02105-147">This functionality is very flexible.</span></span>  
  
  <span data-ttu-id="02105-148">SWIFT 解譯器一律會嘗試完成處理整個批次，即使發生錯誤，在過程中。</span><span class="sxs-lookup"><span data-stu-id="02105-148">The SWIFT disassembler always attempts to complete processing of an entire batch, even when it encounters errors along the way.</span></span> <span data-ttu-id="02105-149">這可讓它來收集和報告多個錯誤越好，全部一次。</span><span class="sxs-lookup"><span data-stu-id="02105-149">This enables it to collect and report as many errors as possible all at once.</span></span> <span data-ttu-id="02105-150">若要執行這個 「 最大努力 」 啟發式，SWIFT 解譯器必須進行某些決策和假設選取在遇到新的組件 時使用的結構描述時，或會發生剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="02105-150">To perform this "best effort" heuristic, the SWIFT disassembler must make certain decisions and assumptions when selecting the schema to use upon encountering a new part, or if a parsing error occurs.</span></span> <span data-ttu-id="02105-151">選取正確的結構描述不一定能夠根據本質和剖析錯誤和模稜兩可/之間的相似度信封結構描述和 SWIFT 交換結構描述的位置。</span><span class="sxs-lookup"><span data-stu-id="02105-151">Selecting the correct schema is not always possible depending upon the nature and location of a parse error and the ambiguity/similarity between envelope schemas and the SWIFT interchange schemas.</span></span> <span data-ttu-id="02105-152">在某些情況下，您可以減少可能會使用設計良好的信封結構描述，以選取錯誤的結構描述。</span><span class="sxs-lookup"><span data-stu-id="02105-152">In some cases, you can minimize the possibility of selecting the wrong schema by using well-designed envelope schemas.</span></span> <span data-ttu-id="02105-153">如果解譯器發生嚴重的剖析錯誤，或反組譯工具無法判斷正確的結構描述，解譯器將會失敗的批次，而不需處理剩餘的資料。</span><span class="sxs-lookup"><span data-stu-id="02105-153">If the disassembler encounters a fatal parse error or the disassembler cannot determine the correct schema, the disassembler will fail the batch without processing the remaining data.</span></span>  
  
  <span data-ttu-id="02105-154">當**輸入解除批次處理**是**啟用**(設定為**True**)，SWIFT 解譯器剖析使用指定的批次的信封 （批次的標頭結構描述的結構描述的批次和批次結尾結構描述） 和訊息信封 （訊息標頭結構描述和訊息結尾結構描述），以及指定用於剖析批次中 SWIFT 的訊息 （交換） 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="02105-154">When **Inbound Debatching** is **enabled** (set to **True**), the SWIFT disassembler parses the batch using the schemas specified for the batch envelope (Batch Header Schema and Batch Trailer Schema) and message envelope (Message Header Schema and Message Trailer Schema), as well as the schema specified for parsing the SWIFT messages (interchanges) in the batch.</span></span> <span data-ttu-id="02105-155">對於批次中 SWIFT 的訊息，訊息類型和結構描述可動態探索和載入單一的非批次訊息的相同方式 （藉由指定 SWIFT 標頭結構描述）。</span><span class="sxs-lookup"><span data-stu-id="02105-155">For the SWIFT messages in the batch, the message type and schema can be dynamically discovered and loaded in the same way as single non-batch messages (by specifying a SWIFT Header Schema).</span></span> <span data-ttu-id="02105-156">如需 SWIFT 解譯器的結構描述解析的執行方式的詳細資訊，請參閱[動態訊息類型探索和結構描述解析](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="02105-156">For more information about how the SWIFT disassembler performs schema resolution, see [Dynamic Message Type Discovery and Schema Resolution](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).</span></span>  
  
  <span data-ttu-id="02105-157">SWIFT 解譯器會剖析，並個別驗證輸入的批次中每個 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="02105-157">The SWIFT disassembler parses and validates each SWIFT message in an inbound batch individually.</span></span> <span data-ttu-id="02105-158">它會執行下列處理順序的批次：</span><span class="sxs-lookup"><span data-stu-id="02105-158">It performs the following batch processing sequence:</span></span>  
  
1. <span data-ttu-id="02105-159">如果您已經指定批次標頭結構描述，請剖析批次標頭。</span><span class="sxs-lookup"><span data-stu-id="02105-159">Parses the batch header if you have specified the Batch Header Schema.</span></span>  
  
2. <span data-ttu-id="02105-160">如果您已指定訊息標頭結構描述，請剖析訊息信封標頭。</span><span class="sxs-lookup"><span data-stu-id="02105-160">Parses the message envelope header if you have specified the Message Header Schema.</span></span>  
  
3. <span data-ttu-id="02105-161">剖析 SWIFT 的交換 （訊息）。</span><span class="sxs-lookup"><span data-stu-id="02105-161">Parses the SWIFT interchange (message).</span></span>  
  
4. <span data-ttu-id="02105-162">如果您已啟用 XML 驗證，請驗證 XML 條件約束 SWIFT 訊息。</span><span class="sxs-lookup"><span data-stu-id="02105-162">Validates the SWIFT message against XML constraints if you have enabled XML validation.</span></span>  
  
5. <span data-ttu-id="02105-163">如果您已啟用 BRE 驗證，請驗證 BRE 原則 （SWIFT 網路和使用方式規則） SWIFT 訊息。</span><span class="sxs-lookup"><span data-stu-id="02105-163">Validates the SWIFT message against BRE policies (SWIFT network and usage rules) if you have enabled BRE validation.</span></span>  
  
6. <span data-ttu-id="02105-164">如果指定了訊息結尾結構描述，請剖析訊息信封結尾。</span><span class="sxs-lookup"><span data-stu-id="02105-164">Parses the message envelope trailer if the Message Trailer Schema is specified.</span></span>  
  
7. <span data-ttu-id="02105-165">重複步驟 2 到 6，解譯器的批次中找不到任何訊息之前。</span><span class="sxs-lookup"><span data-stu-id="02105-165">Repeats Steps 2 to 6 until the disassembler does not find any more messages in the batch.</span></span>  
  
8. <span data-ttu-id="02105-166">如果您已經指定批次結尾結構描述，請剖析批次的結尾。</span><span class="sxs-lookup"><span data-stu-id="02105-166">Parses the batch trailer if you have specified the Batch Trailer Schema.</span></span>  
  
   <span data-ttu-id="02105-167">您可以設定 SWIFT 解譯器，以執行批次資料，它會剖析並驗證使用下列的 SWIFT 解譯器設定屬性使用不同的動作：</span><span class="sxs-lookup"><span data-stu-id="02105-167">You can configure the SWIFT disassembler to do different things with the batch data that it parses and validates using the following SWIFT disassembler configuration properties:</span></span>  
  
- <span data-ttu-id="02105-168">**片段**屬性會決定是否 SWIFT 解譯器應該在批次至 MessageBox 資料庫中個別發佈每則訊息 (也就是為每個訊息之後每次出現的上述的步驟 6,)，則它應該完成所有步驟 1 到 8，然後將整個批次中，發行以原生格式 （的輸入的完全相同複本），當作單一訊息至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="02105-168">The **Fragmentation** property determines if the SWIFT disassembler should publish each message in the batch to the MessageBox database individually (that is, for each message, after each occurrence of Step 6 above), or if it should complete all of steps 1 to 8 and then publish the entire batch, in native form (exact copy of input), as a single message to the MessageBox database.</span></span> <span data-ttu-id="02105-169">您設定**分散**要 **，則為 True**啟用片段，並個別發佈批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="02105-169">You set **Fragmentation** to **True** to enable fragmentation and publish messages from a batch individually.</span></span> <span data-ttu-id="02105-170">您設定**分散**要**False**停用片段，並將整個批次中，以原生格式，發佈當作單一訊息只有在處理整個批次之後。</span><span class="sxs-lookup"><span data-stu-id="02105-170">You set **Fragmentation** to **False** to disable fragmentation and publish the entire batch, in native form, as a single message only after processing the entire batch.</span></span> <span data-ttu-id="02105-171">一般而言，設定**片段**要**已停用**情況下，當您僅需要 BizTalk Accelerator for SWIFT ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]) 來剖析及驗證輸入批次，然後失敗，或轉送，在同一個表單[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收它們。</span><span class="sxs-lookup"><span data-stu-id="02105-171">Typically, set **Fragmentation** to **Disabled**for scenarios when you only need the BizTalk Accelerator for SWIFT ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]) to parse and validate inbound batches and either failed, or forwarded, in the same form that [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] received them.</span></span> <span data-ttu-id="02105-172">通常設定**分散**要**已啟用**的情況下您想[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]來轉換或修改的批次內的訊息之後剖析和驗證，, 或您想要[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]若要重新排序順序不同於批次中的訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]原來接收它們。</span><span class="sxs-lookup"><span data-stu-id="02105-172">You usually set **Fragmentation** to **Enabled** for scenarios in which you want [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to transform or modify messages within a batch after parsing and validation, or when you want [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to re-sort messages in a batch to an order different from what [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] originally received them in.</span></span> <span data-ttu-id="02105-173">您也設定**片段**要**已啟用**包含有不同的最終目的地的訊息之輸入批次的案例。</span><span class="sxs-lookup"><span data-stu-id="02105-173">You also set **Fragmentation** to **Enabled** for scenarios in which an inbound batch contains messages that have differing final destinations.</span></span>  
  
- <span data-ttu-id="02105-174">**保留批次標頭 / 保留批次結尾**屬性會決定 SWIFT 解譯器應該捨棄或保留批次的信封 （標頭和結尾） 資料之後剖析它。</span><span class="sxs-lookup"><span data-stu-id="02105-174">The **Preserve Batch Header / Preserve Batch Trailer** property determines if the SWIFT disassembler should discard or preserve the batch envelope (header and trailer) data after parsing it.</span></span> <span data-ttu-id="02105-175">如果您設定**保留的批次標頭或保留批次結尾**要 **，則為 True**，解譯器個別的訊息將對應的批次組件 (剖析的 XML) 發佈到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="02105-175">If you set **Preserve Batch Header or Preserve Batch Trailer** to **True**, the disassembler publishes the corresponding batch part (parsed XML) to the MessageBox database as individual messages.</span></span> <span data-ttu-id="02105-176">解譯器會將資料發佈在多部分訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="02105-176">The disassembler publishes the data in the body part of the multi-part message.</span></span> <span data-ttu-id="02105-177">解譯器會升級特殊的內容屬性，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以將它們是在批次內這些訊息的批次，其來源而來的序數位置相互關聯 (批次結尾的最後一個位置中的 批次標頭的第一個位置）。</span><span class="sxs-lookup"><span data-stu-id="02105-177">The disassembler promotes special context properties so that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can correlate these messages to the batch that they came from and the ordinal position they were in within the batch (first position for batch header, last position for batch trailer).</span></span> <span data-ttu-id="02105-178">如果您設定**保留的批次標頭或保留批次結尾**要**False**，解譯器剖析之後捨棄對應的批次組件 （剖析的資料）。</span><span class="sxs-lookup"><span data-stu-id="02105-178">If you set **Preserve Batch Header or Preserve Batch Trailer** to **False**, the disassembler discards the corresponding batch part (parsed data) after parsing.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="02105-179">這些組態屬性是有效的只有當啟用分割時 (**分散**設為 **，則為 True**)。</span><span class="sxs-lookup"><span data-stu-id="02105-179">These configuration properties are valid only when fragmentation is enabled (**Fragmentation** set to **True**).</span></span> <span data-ttu-id="02105-180">停用片段時，解譯器發佈的完全相同的複本，整個批次中，以原生格式，到 MessageBox 資料庫，因此保留設定無關 (*一切*保留)。</span><span class="sxs-lookup"><span data-stu-id="02105-180">When fragmentation is disabled, the disassembler publishes an exact copy of the entire batch, in native form, to the MessageBox database, so preservation settings are irrelevant (*everything* is preserved).</span></span>  
  
- <span data-ttu-id="02105-181">**保留的訊息標頭** / **保留訊息結尾**屬性會決定是否應該捨棄 SWIFT 解譯器，或者保留訊息信封 （訊息標頭和結尾）之後剖析它們。</span><span class="sxs-lookup"><span data-stu-id="02105-181">The **Preserve Message Header** / **Preserve Message Trailer** property determines if the SWIFT disassembler should discard or preserve the message envelopes (message headers and trailers) after parsing them.</span></span> <span data-ttu-id="02105-182">如果您設定**保留的訊息標頭或保留訊息結尾**要 **，則為 True**，解譯器會將對應的批次組件 (剖析的 XML) 發佈到 MessageBox 資料庫*連同它所包裝的個別 SWIFT 訊息*。</span><span class="sxs-lookup"><span data-stu-id="02105-182">If you set **Preserve Message Header or Preserve Message Trailer** to **True**, the disassembler publishes the corresponding batch part (parsed XML) to the MessageBox database *along with the individual SWIFT message that it wraps*.</span></span> <span data-ttu-id="02105-183">解譯器將發佈中的訊息信封標頭**標頭**多部分訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="02105-183">The disassembler publishes message envelope headers in the **header** part of the multi-part message.</span></span> <span data-ttu-id="02105-184">解譯器將發佈中的訊息信封結尾**結尾**多部分訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="02105-184">The disassembler publishes message envelope trailers in the **trailer** part of the multi-part message.</span></span> <span data-ttu-id="02105-185">解譯器會發佈在郵件信封中所包含的 SWIFT 訊息**主體**屬於相同的多部分訊息。</span><span class="sxs-lookup"><span data-stu-id="02105-185">The disassembler publishes the SWIFT message contained in the message envelope in the **body** part of the same multi-part message.</span></span> <span data-ttu-id="02105-186">解譯器會升級特殊的內容屬性，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以將這些訊息，其來源而批次，並已批次內的序數位置相互關聯。</span><span class="sxs-lookup"><span data-stu-id="02105-186">The disassembler promotes special context properties so that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can correlate these messages to the batch they came from and the ordinal position that they were in within the batch.</span></span> <span data-ttu-id="02105-187">如果您設定**保留的訊息標頭或保留訊息結尾**要**False**，解譯器剖析之後捨棄對應的批次組件 （剖析的資料）。</span><span class="sxs-lookup"><span data-stu-id="02105-187">If you set **Preserve Message Header or Preserve Message Trailer** to **False**, the disassembler discards the corresponding batch part (parsed data) after parsing.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="02105-188">這些組態屬性是有效的只有當啟用分割時 (**分散**設為 **，則為 True**)。</span><span class="sxs-lookup"><span data-stu-id="02105-188">These configuration properties are valid only when fragmentation is enabled (**Fragmentation** set to **True**).</span></span> <span data-ttu-id="02105-189">停用片段時，解譯器發佈的完全相同的複本，整個批次中，以原生格式，到 MessageBox 資料庫，因此保留設定無關 (*一切*保留)。</span><span class="sxs-lookup"><span data-stu-id="02105-189">When fragmentation is disabled, the disassembler publishes an exact copy of the entire batch, in native form, to the MessageBox database, so preservation settings are irrelevant (*everything* is preserved).</span></span>  
  
  <span data-ttu-id="02105-190">如需每個組態屬性的詳細資訊，以及其他使用方式和組態資訊，請參閱 < [SWIFT 解譯器設定屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="02105-190">For more information about each configuration property, as well as other usage and configuration information, see [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md).</span></span> <span data-ttu-id="02105-191">如需 MessageBox 資料庫發行和多部分訊息的詳細資訊，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="02105-191">For more information about MessageBox database publishing and multi-part messages, see BizTalk Server Help.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="02105-192">下一步</span><span class="sxs-lookup"><span data-stu-id="02105-192">Next step</span></span>
  
[<span data-ttu-id="02105-193">批次相關升級屬性</span><span class="sxs-lookup"><span data-stu-id="02105-193">Batch-Related Promoted Properties</span></span>](batch-related-promoted-properties.md)
