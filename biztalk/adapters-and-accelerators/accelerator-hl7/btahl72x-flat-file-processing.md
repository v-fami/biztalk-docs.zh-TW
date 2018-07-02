---
title: BTAHL72X 一般檔案處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ACKs
- 2.X messages, disassembler
- property promotion, MSH-header schemas
- disassembler, validating messages
- HL7, errors
- 2.X messages, validating headers
- acknowledgements, generating
- assembler, validating messages
- messages, multi-part messages
- property promotion, property schemas
- generating aknowledgements
- messages, 2.X messages
- schemas, MSH-header schemas
- 2.X messages, validating message bodies
- 2.X messages
- schemas, property schemas
- message modes, 2.X messages
- errors, HL7 error format
- flat files
- validating, messages
- schemas, property promotion
- headers, validating
- 2.X messages, message modes
- 2.X messages, header validation
- 2.X messages, parsing flat files
ms.assetid: c92e2f70-0bfa-4bc8-8044-4a6e62cabee3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a0220d44386eed94efbddc1a5a22fe6704a7780
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975551"
---
# <a name="btahl72x-flat-file-processing"></a><span data-ttu-id="a82c1-102">BTAHL72X 一般檔案處理</span><span class="sxs-lookup"><span data-stu-id="a82c1-102">BTAHL72X Flat File Processing</span></span>
<span data-ttu-id="a82c1-103">在 Microsoft BizTalk Accelerator for HL7 的下列元件 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理 HL7 2.X （HL7 編碼） 訊息：</span><span class="sxs-lookup"><span data-stu-id="a82c1-103">The following components in Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) process HL7 2.X (HL7-encoded) messages:</span></span>  
  
- <span data-ttu-id="a82c1-104">管線和核心程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineCommon.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineMessageCore.dll</span><span class="sxs-lookup"><span data-stu-id="a82c1-104">Pipelines and core libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineCommon.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineMessageCore.dll</span></span>  
  
- <span data-ttu-id="a82c1-105">組合器和解譯器程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72fAsm.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72fDAsm.dll</span><span class="sxs-lookup"><span data-stu-id="a82c1-105">Assembler and disassembler libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fDAsm.dll</span></span>  
  
- <span data-ttu-id="a82c1-106">通知 (ACK) 的驗證程式庫用於雙向 MLLP 傳送配接器： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL7ACKHelper.dll</span><span class="sxs-lookup"><span data-stu-id="a82c1-106">The acknowledgment (ACK) validation library used for the two-way MLLP send adapter: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL7ACKHelper.dll</span></span>  
  
## <a name="hl7-message-modes"></a><span data-ttu-id="a82c1-107">HL7 訊息模式</span><span class="sxs-lookup"><span data-stu-id="a82c1-107">HL7 Message Modes</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a82c1-108"> 2.X 訊息支援下列的訊息模式：</span><span class="sxs-lookup"><span data-stu-id="a82c1-108"> supports the following message modes for 2.X messages:</span></span>  
  
- <span data-ttu-id="a82c1-109">發行者-訂閱 (pub sub) 模式</span><span class="sxs-lookup"><span data-stu-id="a82c1-109">Publisher-subscriber (pub-sub) mode</span></span>  
  
   <span data-ttu-id="a82c1-110">發行者會廣播至合作對象的 「 訂閱者 」 為宣告式或來路不明的更新。</span><span class="sxs-lookup"><span data-stu-id="a82c1-110">The publisher broadcasts to a party of subscribers, either as declarative or an unsolicited update.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a82c1-111"> 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供彈性，此模式中，因為您可以在設計階段之後管理訂用帳戶和合作對象。</span><span class="sxs-lookup"><span data-stu-id="a82c1-111"> and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provide flexibility to this mode, since you can manage subscriptions and parties after design time.</span></span>  
  
- <span data-ttu-id="a82c1-112">要求-回應模式</span><span class="sxs-lookup"><span data-stu-id="a82c1-112">Request-response mode</span></span>  
  
   <span data-ttu-id="a82c1-113">來自特定實體的特定要求回應訊息中產生 interrogative 或查詢訊息交換。</span><span class="sxs-lookup"><span data-stu-id="a82c1-113">An interrogative or query message exchange in which a specific request from a specific entity results in a responding message.</span></span>  
  
## <a name="flat-file-parsing"></a><span data-ttu-id="a82c1-114">一般檔案剖析</span><span class="sxs-lookup"><span data-stu-id="a82c1-114">Flat File Parsing</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a82c1-115"> 剖析 HL7 2.X 多部分的訊息分成三個部分：</span><span class="sxs-lookup"><span data-stu-id="a82c1-115"> parses HL7 2.X multi-part messages into three parts:</span></span>  
  
-   <span data-ttu-id="a82c1-116">標頭 MSH 組件</span><span class="sxs-lookup"><span data-stu-id="a82c1-116">Header-MSH part</span></span>  
  
-   <span data-ttu-id="a82c1-117">內文部分</span><span class="sxs-lookup"><span data-stu-id="a82c1-117">Body part</span></span>  
  
-   <span data-ttu-id="a82c1-118">Z 組件</span><span class="sxs-lookup"><span data-stu-id="a82c1-118">Z part</span></span>  
  
## <a name="hl7-header-validation"></a><span data-ttu-id="a82c1-119">HL7 標頭驗證</span><span class="sxs-lookup"><span data-stu-id="a82c1-119">HL7 Header Validation</span></span>  
 <span data-ttu-id="a82c1-120">HL7 反組譯工具和組譯工具執行 2.X 訊息，以確認它可以處理訊息的標頭的結構化與圖解驗證。</span><span class="sxs-lookup"><span data-stu-id="a82c1-120">The HL7 disassembler and assembler perform structural and schematic validation of the header of a 2.X message, in order to verify that it can process the message.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a82c1-121"> 基底上常見的標頭結構描述，MSH_25_GLO_DEF 圖解的驗證。</span><span class="sxs-lookup"><span data-stu-id="a82c1-121"> bases the schematic validation on the common header schema, MSH_25_GLO_DEF.</span></span>  
  
 <span data-ttu-id="a82c1-122">比方說，剖析器會判斷 MSH1 和 MSH2 欄位有正確的格式。</span><span class="sxs-lookup"><span data-stu-id="a82c1-122">For instance, the parser determines that the MSH1 and MSH2 fields are well formed.</span></span> <span data-ttu-id="a82c1-123">MSH1 必須只有一個字元。</span><span class="sxs-lookup"><span data-stu-id="a82c1-123">MSH1 must have only one character.</span></span> <span data-ttu-id="a82c1-124">MSH2 必須是介於兩個到四個字元，而且沒有字元可以重複。</span><span class="sxs-lookup"><span data-stu-id="a82c1-124">MSH2 must be between two and four characters, and no characters can repeat.</span></span>  
  
## <a name="hl7-body-validation"></a><span data-ttu-id="a82c1-125">HL7 主體驗證</span><span class="sxs-lookup"><span data-stu-id="a82c1-125">HL7 Body Validation</span></span>  
 <span data-ttu-id="a82c1-126">HL7 反組譯工具和組譯工具執行的 2.X 訊息內文的基本結構驗證和圖解的驗證，如果您啟用它。</span><span class="sxs-lookup"><span data-stu-id="a82c1-126">The HL7 disassembler and assembler perform basic structural validation of the body of a 2.X message, and schematic validation, if you enable it.</span></span>  
  
 <span data-ttu-id="a82c1-127">基本結構驗證的主體中，其中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]一律會執行，包括確認下列：</span><span class="sxs-lookup"><span data-stu-id="a82c1-127">The basic structural validation of the body, which [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] always performs, includes verifying the following:</span></span>  
  
- <span data-ttu-id="a82c1-128">區段中有三個字元</span><span class="sxs-lookup"><span data-stu-id="a82c1-128">That there are three characters in segments</span></span>  
  
- <span data-ttu-id="a82c1-129">區段分隔符號是\<CR\>或是\<CR\>\<LF\> （選擇性的最後一個區段）</span><span class="sxs-lookup"><span data-stu-id="a82c1-129">That the segment delimiter is \<CR\> or \<CR\>\<LF\> (optional for the last segment)</span></span>  
  
- <span data-ttu-id="a82c1-130">欄位分隔符號是適當</span><span class="sxs-lookup"><span data-stu-id="a82c1-130">That field delimiters are appropriate</span></span>  
  
- <span data-ttu-id="a82c1-131">未宣告的 Z 區段中有任何宣告的區段 （具有已定義的三個字元區段標記）</span><span class="sxs-lookup"><span data-stu-id="a82c1-131">That there are no declared segments (with a defined three-character segment tag) in an undeclared Z segment</span></span>  
  
  <span data-ttu-id="a82c1-132">更多的結構描述驗證的主體包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="a82c1-132">More extensive schema validation of the body includes the following:</span></span>  
  
- <span data-ttu-id="a82c1-133">尾端欄位分隔符號</span><span class="sxs-lookup"><span data-stu-id="a82c1-133">Trailing-field delimiters</span></span>  
  
   <span data-ttu-id="a82c1-134">在標頭 MSH 區段及本文區段</span><span class="sxs-lookup"><span data-stu-id="a82c1-134">In Header-MSH segment and body segments</span></span>  
  
- <span data-ttu-id="a82c1-135">Z 區段</span><span class="sxs-lookup"><span data-stu-id="a82c1-135">Z segment</span></span>  
  
- <span data-ttu-id="a82c1-136">XSD 支援與自訂資料類型</span><span class="sxs-lookup"><span data-stu-id="a82c1-136">XSD-supported and custom data type</span></span>  
  
   <span data-ttu-id="a82c1-137">支援的 XSD 和非 XSD 型別 （TS （時間戳記）、 DT （日期）、 TM （時間） 和 TN （電話號碼）</span><span class="sxs-lookup"><span data-stu-id="a82c1-137">XSD supported and non-XSD types (TS (Time Stamp), DT (date), TM (time), and TN (telephone number)</span></span>  
  
- <span data-ttu-id="a82c1-138">列舉型別</span><span class="sxs-lookup"><span data-stu-id="a82c1-138">Enumerations</span></span>  
  
   <span data-ttu-id="a82c1-139">識別碼 （HL7 定義的資料表） 和 IS （使用者定義的資料表）</span><span class="sxs-lookup"><span data-stu-id="a82c1-139">ID (HL7-defined tables) and IS (user-defined tables)</span></span>  
  
- <span data-ttu-id="a82c1-140">選用性</span><span class="sxs-lookup"><span data-stu-id="a82c1-140">Optionality</span></span>  
  
   <span data-ttu-id="a82c1-141">必要和選擇性</span><span class="sxs-lookup"><span data-stu-id="a82c1-141">Required and optional</span></span>  
  
- <span data-ttu-id="a82c1-142">重複</span><span class="sxs-lookup"><span data-stu-id="a82c1-142">Repetition</span></span>  
  
   <span data-ttu-id="a82c1-143">區段和欄位</span><span class="sxs-lookup"><span data-stu-id="a82c1-143">Segment and field</span></span>  
  
- <span data-ttu-id="a82c1-144">逸出序列</span><span class="sxs-lookup"><span data-stu-id="a82c1-144">Escape sequences</span></span>  
  
   <span data-ttu-id="a82c1-145">字元編碼、 格式和字元集</span><span class="sxs-lookup"><span data-stu-id="a82c1-145">Encoding characters, formatting, and character sets</span></span>  
  
  <span data-ttu-id="a82c1-146">您可以啟用或停用圖解驗證接收自或傳送至特定合作對象 （來源合作對象的解譯器，組合器的目的合作對象） 的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="a82c1-146">You enable or disable schematic validation for all messages received from or sent to a specific party (source party for the disassembler, destination party for the assembler).</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a82c1-147"> 使用 HL7 2.X 結構描述，針對這項處理，由 MSH9.3 訊息結構標頭欄位、 MSH12 版本識別碼欄位 （2.3.1、 2.4、 2.5） 和在中設定的命名空間的直接[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。</span><span class="sxs-lookup"><span data-stu-id="a82c1-147"> uses the HL7 2.X schemas directly for this processing, as determined by the MSH9.3 message-structure header field, the MSH12 Version ID field (2.3.1, 2.4, or 2.5), and the namespace setting in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="hl7-disassembler-processing"></a><span data-ttu-id="a82c1-148">HL7 反組譯工具處理</span><span class="sxs-lookup"><span data-stu-id="a82c1-148">HL7 Disassembler Processing</span></span>  
 <span data-ttu-id="a82c1-149">HL7 反組譯工具會將連入 HL7 訊息剖析為 XML 區段進行處理。</span><span class="sxs-lookup"><span data-stu-id="a82c1-149">The HL7 disassembler parses incoming HL7 messages into XML segments for processing.</span></span> <span data-ttu-id="a82c1-150">剖析訊息，解譯器會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="a82c1-150">As it parses the messages, the disassembler performs the following tasks:</span></span>  
  
-   <span data-ttu-id="a82c1-151">控制代碼逸出序列</span><span class="sxs-lookup"><span data-stu-id="a82c1-151">Handles escape sequences</span></span>  
  
-   <span data-ttu-id="a82c1-152">處理必要/選用屬性的檢查</span><span class="sxs-lookup"><span data-stu-id="a82c1-152">Handles checks of the required/optional properties</span></span>  
  
-   <span data-ttu-id="a82c1-153">控制代碼定義區段和未定義或非預期的 Z 區段 (如需 Z 區段的說明，請參閱 <<c0> [ 透過 Z 物件自訂的訊息](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md))。</span><span class="sxs-lookup"><span data-stu-id="a82c1-153">Handles defined segments and undefined or unexpected Z segments (for a description of Z segments, see [Customizing Messages through Z Objects](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)).</span></span>  
  
-   <span data-ttu-id="a82c1-154">會忽略未預期的執行個體結尾的區段 （這會成為未宣告的 Z 區段）</span><span class="sxs-lookup"><span data-stu-id="a82c1-154">Ignores unexpected segments at the end of an instance (which become undeclared Z segments)</span></span>  
  
## <a name="error-reporting"></a><span data-ttu-id="a82c1-155">錯誤報告</span><span class="sxs-lookup"><span data-stu-id="a82c1-155">Error Reporting</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a82c1-156"> 報告的大部分錯誤標準 HL7 錯誤格式，其中包括的區段、 序列、 欄位和錯誤的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a82c1-156"> reports most errors in standard HL7 error format, which include the segment, sequence, field, and error code.</span></span> <span data-ttu-id="a82c1-157">不過，錯誤狀況可能是，並非所有版本都可用，比方說，若沒有結構描述，則。</span><span class="sxs-lookup"><span data-stu-id="a82c1-157">However, the error condition may be such that not all of these are available, for instance, if no schema is present.</span></span> <span data-ttu-id="a82c1-158">若要處理這種情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以報告在替代錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]錯誤格式。</span><span class="sxs-lookup"><span data-stu-id="a82c1-158">To handle such cases, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can report errors in an alternate [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] error format.</span></span> <span data-ttu-id="a82c1-159">在訊息中的錯誤區段包含兩個部分： 一個用於 HL7 錯誤，一個針對替代[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a82c1-159">The error segment in a message includes two parts: one for the HL7 error and one for the alternative [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] error.</span></span>  
  
## <a name="ack-generation"></a><span data-ttu-id="a82c1-160">通知的產生</span><span class="sxs-lookup"><span data-stu-id="a82c1-160">ACK Generation</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a82c1-161"> 2.X 訊息支援下列類型的通知 (Ack)。</span><span class="sxs-lookup"><span data-stu-id="a82c1-161"> supports the following types of acknowledgments (ACKs) for 2.X messages.</span></span> <span data-ttu-id="a82c1-162">HL7 錯誤類型和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]（替代） 的錯誤類型使用：</span><span class="sxs-lookup"><span data-stu-id="a82c1-162">Both the HL7 error type and the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] (alternate) error type are used:</span></span>  
  
-   <span data-ttu-id="a82c1-163">對應原始訊息和通知</span><span class="sxs-lookup"><span data-stu-id="a82c1-163">Mapping original message and ACK</span></span>  
  
-   <span data-ttu-id="a82c1-164">HL7 原始通知</span><span class="sxs-lookup"><span data-stu-id="a82c1-164">HL7 original ACKs</span></span>  
  
-   <span data-ttu-id="a82c1-165">HL7 增強 Ack</span><span class="sxs-lookup"><span data-stu-id="a82c1-165">HL7 enhanced ACKs</span></span>  
  
     <span data-ttu-id="a82c1-166">認可接受並接受應用程式</span><span class="sxs-lookup"><span data-stu-id="a82c1-166">Commit Accept and Application Accept</span></span>  
  
-   <span data-ttu-id="a82c1-167">靜態 proxy 通知</span><span class="sxs-lookup"><span data-stu-id="a82c1-167">Static/proxy ACK</span></span>  
  
     <span data-ttu-id="a82c1-168">ACK 或 NAK</span><span class="sxs-lookup"><span data-stu-id="a82c1-168">ACK or NAK</span></span>  
  
## <a name="property-promotion"></a><span data-ttu-id="a82c1-169">升級屬性</span><span class="sxs-lookup"><span data-stu-id="a82c1-169">Property Promotion</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="a82c1-170"> 支援升級下列 2.X 屬性：</span><span class="sxs-lookup"><span data-stu-id="a82c1-170"> supports promoting the following 2.X properties:</span></span>  
  
-   <span data-ttu-id="a82c1-171">屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="a82c1-171">Property schema</span></span>  
  
-   <span data-ttu-id="a82c1-172">MSH 標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="a82c1-172">MSH-header schema</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a82c1-173">本節內容</span><span class="sxs-lookup"><span data-stu-id="a82c1-173">In This Section</span></span>  
  
-   [<span data-ttu-id="a82c1-174">HL7 2.X 反組譯工具中的結構描述判斷</span><span class="sxs-lookup"><span data-stu-id="a82c1-174">Schema Determination in the HL7 2.X Disassembler</span></span>](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)  
  
-   [<span data-ttu-id="a82c1-175">HL7 2.X 組譯工具中的結構描述判斷</span><span class="sxs-lookup"><span data-stu-id="a82c1-175">Schema Determination in the HL7 2.X Assembler</span></span>](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)  
  
## <a name="see-also"></a><span data-ttu-id="a82c1-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a82c1-176">See Also</span></span>  
 <span data-ttu-id="a82c1-177">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="a82c1-177">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 <span data-ttu-id="a82c1-178">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="a82c1-178">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 [<span data-ttu-id="a82c1-179">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="a82c1-179">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)