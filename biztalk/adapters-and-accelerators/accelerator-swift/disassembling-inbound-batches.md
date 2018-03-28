---
title: 反組譯 SWIFT 與輸入批次 |Microsoft 文件
description: Debatch 輸入的訊息，並自訂結構描述的批次在 BizTalk Server 中使用 SWIFT 加速器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11cb5672-1155-4648-b1fd-c9a3bc30e351
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f14a199e3422a45235727d2d16fc1464e2e4927
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="disassemble-inbound-batches"></a><span data-ttu-id="d78b4-103">反組譯輸入批次</span><span class="sxs-lookup"><span data-stu-id="d78b4-103">Disassemble Inbound Batches</span></span>

## <a name="debatch-inbound-message"></a><span data-ttu-id="d78b4-104">Debatch 輸入的訊息</span><span class="sxs-lookup"><span data-stu-id="d78b4-104">Debatch inbound message</span></span>
<span data-ttu-id="d78b4-105">SWIFT 解譯器就能輸入解除批次處理即將它處理或反組譯輸入批次 （檔案或包含多個 SWIFT 訊息的訊息）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-105">The SWIFT disassembler is able to inbound debatching in which it processes or disassembles inbound batches (files or messages containing multiple SWIFT messages).</span></span> <span data-ttu-id="d78b4-106">您可以啟用輸入解除批次處理即將使用相同名稱的 SWIFT 解譯器組態屬性。</span><span class="sxs-lookup"><span data-stu-id="d78b4-106">You enable inbound debatching using the SWIFT disassembler configuration property of the same name.</span></span> <span data-ttu-id="d78b4-107">輸入解除批次處理即將啟用之後，SWIFT 解譯器會預期收到要包含多個 SWIFT 訊息的批次的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-107">After you enable inbound debatching, the SWIFT disassembler expects all messages that it receives to be batches that include multiple SWIFT messages.</span></span> <span data-ttu-id="d78b4-108">批次可能會或可能不會包含在批次的信封 （批次標頭和批次結尾），以及每個批次內的個別 SWIFT 訊息可能會或可能不會包含訊息信封 （訊息標頭和訊息結尾）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-108">A batch may or may not include a batch envelope (a batch header and a batch trailer), and each individual SWIFT message within a batch may or may not include a message envelope (a message header and a message trailer).</span></span> <span data-ttu-id="d78b4-109">您可以設定這些批次屬性 （格式） 使用下列 SWIFT 解譯器組態屬性：</span><span class="sxs-lookup"><span data-stu-id="d78b4-109">You can configure these batch attributes (formats) using the following SWIFT disassembler configuration properties:</span></span>  
  
-   <span data-ttu-id="d78b4-110">批次標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="d78b4-110">Batch Header Schema</span></span>  
  
-   <span data-ttu-id="d78b4-111">批次結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="d78b4-111">Batch Trailer Schema</span></span>  
  
-   <span data-ttu-id="d78b4-112">訊息標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="d78b4-112">Message Header Schema</span></span>  
  
-   <span data-ttu-id="d78b4-113">訊息結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="d78b4-113">Message Trailer Schema</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d78b4-114">設定任一這些屬性為"None"，表示輸入批次不包含該特定部分。</span><span class="sxs-lookup"><span data-stu-id="d78b4-114">Setting any of these properties to "None" indicates that the inbound batch does not include that particular part.</span></span>  
  
 <span data-ttu-id="d78b4-115">SWIFT 解譯器需要輸入的所有批次會有下列結構：</span><span class="sxs-lookup"><span data-stu-id="d78b4-115">The SWIFT disassembler expects all inbound batches to have the following structure:</span></span>  
  
 <span data-ttu-id="d78b4-116">**批次標頭**</span><span class="sxs-lookup"><span data-stu-id="d78b4-116">**Batch Header**</span></span>  
  
 <span data-ttu-id="d78b4-117">**訊息標頭**</span><span class="sxs-lookup"><span data-stu-id="d78b4-117">**Message Header**</span></span>  
  
 <span data-ttu-id="d78b4-118">**SWIFT 的交換訊息 （SWIFT 區塊的 1 到 5）**</span><span class="sxs-lookup"><span data-stu-id="d78b4-118">**SWIFT Interchange/Message (SWIFT Blocks 1 to 5)**</span></span>  
  
 <span data-ttu-id="d78b4-119">**訊息結尾**</span><span class="sxs-lookup"><span data-stu-id="d78b4-119">**Message Trailer**</span></span>  
  
 <span data-ttu-id="d78b4-120">**批次結尾**</span><span class="sxs-lookup"><span data-stu-id="d78b4-120">**Batch Trailer**</span></span>  
  
 <span data-ttu-id="d78b4-121">在此結構中，您可以考慮使用 「 訊息區塊 」 是**– SWIFT 交換 – 訊息標頭訊息結尾**組件。</span><span class="sxs-lookup"><span data-stu-id="d78b4-121">Within this structure, you can consider a "message block" to be the **Message Header – SWIFT Interchange – Message Trailer** parts.</span></span> <span data-ttu-id="d78b4-122">一系列的多個 「 訊息區塊 」 是由批次中的多個 SWIFT 訊息所組成。</span><span class="sxs-lookup"><span data-stu-id="d78b4-122">A series of multiple "message blocks" makes up the multiple SWIFT messages in a batch.</span></span> <span data-ttu-id="d78b4-123">批次標頭、 訊息標頭、 訊息結尾和批次結尾是選擇性的但重複項目之間必須一致。</span><span class="sxs-lookup"><span data-stu-id="d78b4-123">The Batch Header, Message Header, Message Trailer, and Batch Trailer are optional, but must be consistent across repetitions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d78b4-124">請勿混淆 SWIFT 的標頭和結尾區塊的訊息信封 （訊息標頭和訊息結尾）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-124">Do not confuse the message envelope (Message Header and Message Trailer) with the SWIFT header and trailer blocks.</span></span> <span data-ttu-id="d78b4-125">在批次內容中，您應該檢視 SWIFT 訊息 （交換），做為一個整體 (atomic) 的單位包括 SWIFT 標頭和結尾區塊。</span><span class="sxs-lookup"><span data-stu-id="d78b4-125">In the context of batches, you should view the SWIFT message (interchange), including the SWIFT header and trailer blocks, as a holistic (atomic) unit.</span></span> <span data-ttu-id="d78b4-126">在此情況下，訊息標頭和訊息結尾指包裝批次中的每個 SWIFT 訊息的信封。</span><span class="sxs-lookup"><span data-stu-id="d78b4-126">In this context, the Message Header and Message Trailer refer to the envelope that wraps each SWIFT message in a batch.</span></span>  
  
 <span data-ttu-id="d78b4-127">若要多正式表示此結構，其選項，以及其重複性，請考慮如何[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]定義批次：</span><span class="sxs-lookup"><span data-stu-id="d78b4-127">To express this structure, its options, and its repeatability more formally, consider how [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] defines a batch:</span></span>  
  
-   <span data-ttu-id="d78b4-128">**批次標頭**由**BH**</span><span class="sxs-lookup"><span data-stu-id="d78b4-128">**Batch Header** is represented by **BH**</span></span>  
  
-   <span data-ttu-id="d78b4-129">**訊息標頭**由**MH**</span><span class="sxs-lookup"><span data-stu-id="d78b4-129">**Message Header** is represented by **MH**</span></span>  
  
-   <span data-ttu-id="d78b4-130">**SWIFT 交換**由**SI**</span><span class="sxs-lookup"><span data-stu-id="d78b4-130">**SWIFT Interchange** is represented by **SI**</span></span>  
  
-   <span data-ttu-id="d78b4-131">**訊息結尾**由**MT**</span><span class="sxs-lookup"><span data-stu-id="d78b4-131">**Message Trailer** is represented by **MT**</span></span>  
  
-   <span data-ttu-id="d78b4-132">**批次結尾**由**BT**。</span><span class="sxs-lookup"><span data-stu-id="d78b4-132">**Batch Trailer** is represented by **BT**.</span></span>  
  
 <span data-ttu-id="d78b4-133">表示預期的批次結構的運算式如下所示：</span><span class="sxs-lookup"><span data-stu-id="d78b4-133">The expression that represents the expected batch structure is as follows:</span></span>  
  
 `[BH] ([MH] SI [MT])* [BT]  `
  
 <span data-ttu-id="d78b4-134">在方括號 ( `[ ] ` ) 表示部分是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d78b4-134">The brackets ( `[ ] ` ) indicate that the part is optional.</span></span> <span data-ttu-id="d78b4-135">星號 (**\***) 表示區塊是可重複。</span><span class="sxs-lookup"><span data-stu-id="d78b4-135">The asterisk (**\***)indicates that the block is repeatable.</span></span> <span data-ttu-id="d78b4-136">誰會建立訊息批次，則必須使用訊息標頭 (**MH**) 和結尾 (**MT**) 一致的方式中的每個重複 (`[MH] SI [MT]`)。</span><span class="sxs-lookup"><span data-stu-id="d78b4-136">Whoever builds the message batch must use the message header (**MH**) and trailer (**MT**) consistently in each repetition of (`[MH] SI [MT]`).</span></span>  
  
 <span data-ttu-id="d78b4-137">SWIFT 解譯器就能夠處理遵守上述的結構，任何輸入批次，因為在結構中的每個組件符合一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="d78b4-137">The SWIFT disassembler is able to process any inbound batch that obeys the above structure, because each part in the structure conforms to a flat-file schema.</span></span> <span data-ttu-id="d78b4-138">不過，如果您未使用的選擇性批次標頭/結尾與訊息標頭/結尾，訊息將不符合這些結構描述。</span><span class="sxs-lookup"><span data-stu-id="d78b4-138">However, if you do not use the optional batch header/trailer and message header/trailer, the message will not conform to those schemas.</span></span> <span data-ttu-id="d78b4-139">如此一來，包含連續的 SWIFT 訊息的批次都有批次標頭結構描述、 批次結尾結構描述、 訊息標頭結構描述，以及訊息結尾結構描述屬性設定為"None"。</span><span class="sxs-lookup"><span data-stu-id="d78b4-139">As a result, a batch containing only consecutive SWIFT messages will have the Batch Header Schema, Batch Trailer Schema, Message Header Schema, and Message Trailer Schema properties set to "None".</span></span>  

## <a name="customize-schemas-for-batching"></a><span data-ttu-id="d78b4-140">自訂批次結構的描述</span><span class="sxs-lookup"><span data-stu-id="d78b4-140">Customize schemas for batching</span></span>  
 <span data-ttu-id="d78b4-141">您可以自訂訊息標頭/結尾與批次標頭/結尾的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d78b4-141">You can customize the schemas for the batch header/trailer and message header/trailer.</span></span> <span data-ttu-id="d78b4-142">下列批次是範例：</span><span class="sxs-lookup"><span data-stu-id="d78b4-142">An example is the following batch:</span></span>  
  
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
  
 <span data-ttu-id="d78b4-143">若要處理這種類型的批次，您應該設定為批次結構描述屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d78b4-143">To handle this type of batch, you would set the schema properties for the batch as follows:</span></span>  
  
-   <span data-ttu-id="d78b4-144">您設定批次標頭結構描述屬性為一般檔案結構描述剖析歸位字元分隔的單一數字 （郵件計數）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-144">You set the Batch Header Schema property to a flat-file schema that parses a single number (message count) delimited by carriage-return.</span></span>  
  
-   <span data-ttu-id="d78b4-145">設定成單一的 $ 符號和歸位字元-剖析一般檔案結構描述的訊息結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="d78b4-145">You set the Message Trailer Schema to a flat-file schema that parses a single $ symbol and carriage-return.</span></span>  
  
-   <span data-ttu-id="d78b4-146">您可以設定剩餘信封結構描述 （批次結尾結構描述和訊息標頭結構描述） 為 None。</span><span class="sxs-lookup"><span data-stu-id="d78b4-146">You set the remaining envelope schemas (Batch Trailer Schema and Message Header Schema) to None.</span></span>  
  
 <span data-ttu-id="d78b4-147">您可以設定 SWIFT 解譯器，會處理幾乎任何 SWIFT 訊息批次建立並指定一般檔案信封結構描述的適當組合。</span><span class="sxs-lookup"><span data-stu-id="d78b4-147">You can configure the SWIFT disassembler such that it processes just about any SWIFT message batch by creating and specifying the appropriate combination of flat-file envelope schemas.</span></span> <span data-ttu-id="d78b4-148">這項功能相當富彈性。</span><span class="sxs-lookup"><span data-stu-id="d78b4-148">This functionality is very flexible.</span></span>  
  
 <span data-ttu-id="d78b4-149">SWIFT 解譯器一律會嘗試完成處理整個批次，即使遇到在過程中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d78b4-149">The SWIFT disassembler always attempts to complete processing of an entire batch, even when it encounters errors along the way.</span></span> <span data-ttu-id="d78b4-150">這可讓它來收集和報告所有錯誤越好，一次。</span><span class="sxs-lookup"><span data-stu-id="d78b4-150">This enables it to collect and report as many errors as possible all at once.</span></span> <span data-ttu-id="d78b4-151">若要執行此 「 盡力 」 啟發式，SWIFT 解譯器必須進行某些決策和假設選取在遇到新的組件 時使用的結構描述時，或剖析錯誤，就會發生。</span><span class="sxs-lookup"><span data-stu-id="d78b4-151">To perform this "best effort" heuristic, the SWIFT disassembler must make certain decisions and assumptions when selecting the schema to use upon encountering a new part, or if a parsing error occurs.</span></span> <span data-ttu-id="d78b4-152">選取正確的結構描述不一定能的本質和剖析錯誤和模稜兩可/之間的相似度信封結構描述和 SWIFT 交換結構描述的位置而定。</span><span class="sxs-lookup"><span data-stu-id="d78b4-152">Selecting the correct schema is not always possible depending upon the nature and location of a parse error and the ambiguity/similarity between envelope schemas and the SWIFT interchange schemas.</span></span> <span data-ttu-id="d78b4-153">在某些情況下，您可以最小化，可能會使用設計良好的信封結構描述，以選取錯誤的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d78b4-153">In some cases, you can minimize the possibility of selecting the wrong schema by using well-designed envelope schemas.</span></span> <span data-ttu-id="d78b4-154">如果解譯器發生嚴重的剖析錯誤，或反組譯工具無法判斷正確的結構描述，解譯器將會失敗批次，而不需處理其餘的資料。</span><span class="sxs-lookup"><span data-stu-id="d78b4-154">If the disassembler encounters a fatal parse error or the disassembler cannot determine the correct schema, the disassembler will fail the batch without processing the remaining data.</span></span>  
  
 <span data-ttu-id="d78b4-155">當**輸入解除批次處理即將**是**啟用**(設定為**True**)，SWIFT 的解譯器剖析批次使用指定的批次的信封 （批次的標頭結構描述的結構描述和批次結尾結構描述） 和訊息信封 （訊息標頭結構描述和訊息結尾結構描述），以及指定用於剖析批次中的 SWIFT 訊息 （交換） 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d78b4-155">When **Inbound Debatching** is **enabled** (set to **True**), the SWIFT disassembler parses the batch using the schemas specified for the batch envelope (Batch Header Schema and Batch Trailer Schema) and message envelope (Message Header Schema and Message Trailer Schema), as well as the schema specified for parsing the SWIFT messages (interchanges) in the batch.</span></span> <span data-ttu-id="d78b4-156">對於批次中 SWIFT 的訊息，訊息類型和結構描述可動態探索和載入為單一的非批次訊息相同的方式 （藉由指定 SWIFT 標頭結構描述）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-156">For the SWIFT messages in the batch, the message type and schema can be dynamically discovered and loaded in the same way as single non-batch messages (by specifying a SWIFT Header Schema).</span></span> <span data-ttu-id="d78b4-157">如需如何 SWIFT 的解譯器會執行結構描述解析的詳細資訊，請參閱[動態的訊息類型探索和結構描述解析](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="d78b4-157">For more information about how the SWIFT disassembler performs schema resolution, see [Dynamic Message Type Discovery and Schema Resolution](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).</span></span>  
  
 <span data-ttu-id="d78b4-158">SWIFT 解譯器會剖析並個別驗證傳入的批次中每個 SWIFT 訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-158">The SWIFT disassembler parses and validates each SWIFT message in an inbound batch individually.</span></span> <span data-ttu-id="d78b4-159">它會執行下列處理順序的批次：</span><span class="sxs-lookup"><span data-stu-id="d78b4-159">It performs the following batch processing sequence:</span></span>  
  
1.  <span data-ttu-id="d78b4-160">如果您已經指定批次標頭結構描述，剖析批次標頭。</span><span class="sxs-lookup"><span data-stu-id="d78b4-160">Parses the batch header if you have specified the Batch Header Schema.</span></span>  
  
2.  <span data-ttu-id="d78b4-161">如果您已經指定訊息標頭結構描述，請剖析訊息信封標頭。</span><span class="sxs-lookup"><span data-stu-id="d78b4-161">Parses the message envelope header if you have specified the Message Header Schema.</span></span>  
  
3.  <span data-ttu-id="d78b4-162">剖析 SWIFT 的交換 （訊息）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-162">Parses the SWIFT interchange (message).</span></span>  
  
4.  <span data-ttu-id="d78b4-163">如果您已啟用 XML 驗證，請驗證 XML 條件約束 SWIFT 訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-163">Validates the SWIFT message against XML constraints if you have enabled XML validation.</span></span>  
  
5.  <span data-ttu-id="d78b4-164">如果您已啟用 BRE 驗證，請驗證 BRE 原則 （SWIFT 網路與使用規則） SWIFT 訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-164">Validates the SWIFT message against BRE policies (SWIFT network and usage rules) if you have enabled BRE validation.</span></span>  
  
6.  <span data-ttu-id="d78b4-165">如果訊息結尾結構描述指定，會剖析訊息信封結尾。</span><span class="sxs-lookup"><span data-stu-id="d78b4-165">Parses the message envelope trailer if the Message Trailer Schema is specified.</span></span>  
  
7.  <span data-ttu-id="d78b4-166">重複步驟 2 到 6，直到解譯器在批次中找不到任何其他訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-166">Repeats Steps 2 to 6 until the disassembler does not find any more messages in the batch.</span></span>  
  
8.  <span data-ttu-id="d78b4-167">如果您已經指定批次結尾結構描述，剖析批次結尾。</span><span class="sxs-lookup"><span data-stu-id="d78b4-167">Parses the batch trailer if you have specified the Batch Trailer Schema.</span></span>  
  
 <span data-ttu-id="d78b4-168">您可以設定 SWIFT 的解譯器，以執行不同的動作與批次資料，它會剖析並驗證使用的下列 SWIFT 解譯器組態屬性：</span><span class="sxs-lookup"><span data-stu-id="d78b4-168">You can configure the SWIFT disassembler to do different things with the batch data that it parses and validates using the following SWIFT disassembler configuration properties:</span></span>  
  
-   <span data-ttu-id="d78b4-169">**片段**屬性會決定是否 SWIFT 解譯器應該在批次至 MessageBox 資料庫中個別發行每個訊息 (也就是針對每個訊息之後每次發生上述的步驟 6,)，或是否應該完成所有步驟 1 到 8，然後發行整個批次中，以原生格式 （的輸入的完全相同複本），當做單一訊息至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d78b4-169">The **Fragmentation** property determines if the SWIFT disassembler should publish each message in the batch to the MessageBox database individually (that is, for each message, after each occurrence of Step 6 above), or if it should complete all of steps 1 to 8 and then publish the entire batch, in native form (exact copy of input), as a single message to the MessageBox database.</span></span> <span data-ttu-id="d78b4-170">您設定**片段**至**True**啟用片段和個別發行從批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-170">You set **Fragmentation** to **True** to enable fragmentation and publish messages from a batch individually.</span></span> <span data-ttu-id="d78b4-171">您設定**片段**至**False**停用片段並將整個批次中，以原生格式，發行為處理整個批次之後，只有單一訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-171">You set **Fragmentation** to **False** to disable fragmentation and publish the entire batch, in native form, as a single message only after processing the entire batch.</span></span> <span data-ttu-id="d78b4-172">一般而言，設定**片段**至**已停用**案例，當您僅需要 BizTalk Accelerator for SWIFT ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]) 剖析及驗證輸入批次和失敗，或轉送，在同一個表單[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收它們。</span><span class="sxs-lookup"><span data-stu-id="d78b4-172">Typically, set **Fragmentation** to **Disabled**for scenarios when you only need the BizTalk Accelerator for SWIFT ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]) to parse and validate inbound batches and either failed, or forwarded, in the same form that [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] received them.</span></span> <span data-ttu-id="d78b4-173">通常設定**片段**至**啟用**情況下您想在其中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]轉換或修改訊息的批次內之後剖析和驗證，, 或您想要[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]若要重新排序批次中的訊息順序不同什麼[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]原來接收它們。</span><span class="sxs-lookup"><span data-stu-id="d78b4-173">You usually set **Fragmentation** to **Enabled** for scenarios in which you want [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to transform or modify messages within a batch after parsing and validation, or when you want [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to re-sort messages in a batch to an order different from what [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] originally received them in.</span></span> <span data-ttu-id="d78b4-174">也設定**片段**至**啟用**包含具有不同的最終目的地的訊息之輸入批次的案例。</span><span class="sxs-lookup"><span data-stu-id="d78b4-174">You also set **Fragmentation** to **Enabled** for scenarios in which an inbound batch contains messages that have differing final destinations.</span></span>  
  
-   <span data-ttu-id="d78b4-175">**保留批次標頭 / 保留批次結尾**屬性會決定 SWIFT 解譯器應該捨棄或剖析它之後保留批次的信封 （標頭和結尾） 資料。</span><span class="sxs-lookup"><span data-stu-id="d78b4-175">The **Preserve Batch Header / Preserve Batch Trailer** property determines if the SWIFT disassembler should discard or preserve the batch envelope (header and trailer) data after parsing it.</span></span> <span data-ttu-id="d78b4-176">如果您設定**保留批次標頭或保留批次結尾**至**True**，解譯器將對應的批次部分 (剖析的 XML) 發佈到 MessageBox 資料庫當做個別訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-176">If you set **Preserve Batch Header or Preserve Batch Trailer** to **True**, the disassembler publishes the corresponding batch part (parsed XML) to the MessageBox database as individual messages.</span></span> <span data-ttu-id="d78b4-177">解譯器會將資料發行中多部分訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="d78b4-177">The disassembler publishes the data in the body part of the multi-part message.</span></span> <span data-ttu-id="d78b4-178">解譯器將特殊的內容屬性升級，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以相互關聯的批次內已這些訊息的批次，它們的來源和序數位置 （批次標頭的第一個位置，最後一個位置的批次結尾）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-178">The disassembler promotes special context properties so that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can correlate these messages to the batch that they came from and the ordinal position they were in within the batch (first position for batch header, last position for batch trailer).</span></span> <span data-ttu-id="d78b4-179">如果您設定**保留批次標頭或保留批次結尾**至**False**，解譯器會在之後剖析捨棄對應的批次部分 （剖析的資料）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-179">If you set **Preserve Batch Header or Preserve Batch Trailer** to **False**, the disassembler discards the corresponding batch part (parsed data) after parsing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d78b4-180">只有在啟用片段時，這些組態屬性是有效 (**片段**設**True**)。</span><span class="sxs-lookup"><span data-stu-id="d78b4-180">These configuration properties are valid only when fragmentation is enabled (**Fragmentation** set to **True**).</span></span> <span data-ttu-id="d78b4-181">停用片段時，解譯器發行整個批次，完全相同複本中的原生格式，到 MessageBox 資料庫，以便保留設定無關 (*一切*保留)。</span><span class="sxs-lookup"><span data-stu-id="d78b4-181">When fragmentation is disabled, the disassembler publishes an exact copy of the entire batch, in native form, to the MessageBox database, so preservation settings are irrelevant (*everything* is preserved).</span></span>  
  
-   <span data-ttu-id="d78b4-182">**保留訊息標頭** / **保留訊息結尾**屬性會決定 SWIFT 解譯器應該捨棄或保留訊息信封 （訊息標頭和結尾）之後剖析它們。</span><span class="sxs-lookup"><span data-stu-id="d78b4-182">The **Preserve Message Header** / **Preserve Message Trailer** property determines if the SWIFT disassembler should discard or preserve the message envelopes (message headers and trailers) after parsing them.</span></span> <span data-ttu-id="d78b4-183">如果您設定**保留訊息標頭或保留訊息結尾**至**True**，解譯器會將對應的批次部分 (剖析的 XML) 發佈到 MessageBox 資料庫*連同它所包裝的個別 SWIFT 訊息*。</span><span class="sxs-lookup"><span data-stu-id="d78b4-183">If you set **Preserve Message Header or Preserve Message Trailer** to **True**, the disassembler publishes the corresponding batch part (parsed XML) to the MessageBox database *along with the individual SWIFT message that it wraps*.</span></span> <span data-ttu-id="d78b4-184">解譯器將發佈中的訊息信封標頭**標頭**多部分訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="d78b4-184">The disassembler publishes message envelope headers in the **header** part of the multi-part message.</span></span> <span data-ttu-id="d78b4-185">解譯器將發佈中的訊息信封結尾**結尾**多部分訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="d78b4-185">The disassembler publishes message envelope trailers in the **trailer** part of the multi-part message.</span></span> <span data-ttu-id="d78b4-186">解譯器將發佈中的訊息信封中包含的 SWIFT 訊息**主體**屬於相同的多部分訊息。</span><span class="sxs-lookup"><span data-stu-id="d78b4-186">The disassembler publishes the SWIFT message contained in the message envelope in the **body** part of the same multi-part message.</span></span> <span data-ttu-id="d78b4-187">解譯器將特殊的內容屬性升級，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以相互關聯的這些訊息，它們來自批次，並將它們批次中的序數位置。</span><span class="sxs-lookup"><span data-stu-id="d78b4-187">The disassembler promotes special context properties so that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] can correlate these messages to the batch they came from and the ordinal position that they were in within the batch.</span></span> <span data-ttu-id="d78b4-188">如果您設定**保留訊息標頭或保留訊息結尾**至**False**，解譯器會在之後剖析捨棄對應的批次部分 （剖析的資料）。</span><span class="sxs-lookup"><span data-stu-id="d78b4-188">If you set **Preserve Message Header or Preserve Message Trailer** to **False**, the disassembler discards the corresponding batch part (parsed data) after parsing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d78b4-189">只有在啟用片段時，這些組態屬性是有效 (**片段**設**True**)。</span><span class="sxs-lookup"><span data-stu-id="d78b4-189">These configuration properties are valid only when fragmentation is enabled (**Fragmentation** set to **True**).</span></span> <span data-ttu-id="d78b4-190">停用片段時，解譯器發行整個批次，完全相同複本中的原生格式，到 MessageBox 資料庫，以便保留設定無關 (*一切*保留)。</span><span class="sxs-lookup"><span data-stu-id="d78b4-190">When fragmentation is disabled, the disassembler publishes an exact copy of the entire batch, in native form, to the MessageBox database, so preservation settings are irrelevant (*everything* is preserved).</span></span>  
  
 <span data-ttu-id="d78b4-191">如需有關每個組態屬性，以及其他使用方式和組態資訊，請參閱[SWIFT 解譯器組態屬性](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d78b4-191">For more information about each configuration property, as well as other usage and configuration information, see [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md).</span></span> <span data-ttu-id="d78b4-192">如需 MessageBox 資料庫發行和多部分訊息的詳細資訊，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="d78b4-192">For more information about MessageBox database publishing and multi-part messages, see BizTalk Server Help.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="d78b4-193">下一步</span><span class="sxs-lookup"><span data-stu-id="d78b4-193">Next step</span></span>
  
[<span data-ttu-id="d78b4-194">批次相關升級屬性</span><span class="sxs-lookup"><span data-stu-id="d78b4-194">Batch-Related Promoted Properties</span></span>](batch-related-promoted-properties.md)
