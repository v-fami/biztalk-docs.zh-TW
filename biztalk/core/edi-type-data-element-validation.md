---
title: "EDI 類型 （資料元素） 驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd53685f-a49c-41c8-813e-29700fc0b62b
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a989c58f59581795f641601938fe76bb7b1671f6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="edi-type-data-element-validation"></a><span data-ttu-id="5b1f6-102">EDI 類型 (資料元素) 驗證</span><span class="sxs-lookup"><span data-stu-id="5b1f6-102">EDI Type (Data Element) Validation</span></span>
<span data-ttu-id="5b1f6-103">EDI 接收管線和 EDI 傳送管線，可以對交易集資料元素執行 EDI 驗證。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-103">The EDI receive pipeline and EDI send pipeline perform EDI validation on transaction-set data elements.</span></span> <span data-ttu-id="5b1f6-104">這項驗證來自或通往特定合作對象，透過該合作對象的協議屬性的所有訊息上設定**驗證**頁面 (在**交易集設定**任一 X12 區段或 EDIFACT 協議）。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-104">This validation is configured for all messages from or to a specific party, through that party's agreement properties on the **Validation** page (under the **Transaction Set Settings** section for either X12 or EDIFACT agreements).</span></span> <span data-ttu-id="5b1f6-105">如果**EDI 類型驗證**屬性中未選取**驗證**頁面上，將不會執行驗證，本主題所描述的資料。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-105">If the **EDI Type Validation** property is not selected in the **Validation** page, the data validations described in this topic will not be performed.</span></span>  
  
 <span data-ttu-id="5b1f6-106">EDI 類型驗證已啟用內送與外寄訊息的選取**EDI 類型驗證**屬性**驗證**中雙向協議索引標籤頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-106">EDI type validation is enabled for incoming as well as outgoing messages by selecting the **EDI type Validation** property in the **Validation** page of the bi-directional agreement tabs in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="5b1f6-107">對於內送和外寄訊息，這個屬性預設會選取，因此預設會啟用 EDI 驗證。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-107">For both incoming and outgoing messages, this property is selected by default so that EDI validation is enabled by default.</span></span>  
  
## <a name="validation-checks"></a><span data-ttu-id="5b1f6-108">驗證檢查</span><span class="sxs-lookup"><span data-stu-id="5b1f6-108">Validation Checks</span></span>  
 <span data-ttu-id="5b1f6-109">EDI 接收管線或 EDI 傳送管線在執行 EDI 驗證時，會驗證下列項目：</span><span class="sxs-lookup"><span data-stu-id="5b1f6-109">When the EDI receive pipeline or EDI send pipeline performs EDI validation, it validates the following:</span></span>  
  
-   <span data-ttu-id="5b1f6-110">由結構描述之 EDI 屬性所定義的資料型別</span><span class="sxs-lookup"><span data-stu-id="5b1f6-110">Data types as defined by the EDI properties of the schema</span></span>  
  
-   <span data-ttu-id="5b1f6-111">長度限制</span><span class="sxs-lookup"><span data-stu-id="5b1f6-111">Length restrictions</span></span>  
  
-   <span data-ttu-id="5b1f6-112">空白資料元素和尾端分隔符號</span><span class="sxs-lookup"><span data-stu-id="5b1f6-112">Empty data elements and trailing separators</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5b1f6-113">這項驗證不會檢查程式碼集合 (列舉) 或 Min Occurs 或 Max Occurs。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-113">This validation does not check code sets (enumerations) or min or max occurs.</span></span>  
  
 <span data-ttu-id="5b1f6-114">**字元集**</span><span class="sxs-lookup"><span data-stu-id="5b1f6-114">**Character Sets**</span></span>  
  
 <span data-ttu-id="5b1f6-115">若要執行 EDI 資料元素驗證，EDI 接收和傳送管線會要求依下列方式來建立此字元集：</span><span class="sxs-lookup"><span data-stu-id="5b1f6-115">To perform EDI data element validations, the EDI receive and send pipelines require the character set to be established as follows:</span></span>  
  
-   <span data-ttu-id="5b1f6-116">對於 EDIFACT，資料元素中建立字元集**UNB1**的**字元集和分隔符號**單向協議索引標籤的頁面**協議屬性**對話方塊或**EDIFACT 後援設定**對話方塊 （若已建立協議）。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-116">For EDIFACT, the character set is established in data element **UNB1** of the **Charset and Separators** page of the one-way agreement tab of the **Agreement Properties** dialog box or the **EDIFACT Fallback Settings** dialog box (if no agreement has been established).</span></span>  
  
-   <span data-ttu-id="5b1f6-117">對於 KEDIFACT，字元在資料元素中建立**UNB1**的**字元集和分隔符號**單向協議索引標籤的頁面**協議屬性**對話方塊方塊中，EDIFACT 一樣。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-117">For KEDIFACT, the character is established in data element **UNB1** of the **Charset and Separators** page of the one-way agreement tab of the **Agreement Properties** dialog box, as for EDIFACT.</span></span> <span data-ttu-id="5b1f6-118">值**UNB1.1**元素必須設定為`KECA`。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-118">The value for the **UNB1.1** element must be set to `KECA`.</span></span>  
  
-   <span data-ttu-id="5b1f6-119">對於 X12，要在管線屬性中建立訊息的字元集。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-119">For X12, the character set is established for the message in the pipeline properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5b1f6-120">當 BizTalk 執行階段對訊息執行 EDI 驗證時，它會使用已在管線屬性中選取的 X12 字元集。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-120">When the BizTalk runtime performs EDI validation of a message, it will use the X12 character set selected in the pipeline properties.</span></span> <span data-ttu-id="5b1f6-121">不過，屬性的驗證輸入的頁面中**協議屬性**對話方塊使用的字元集中已選取執行**字元集和分隔符號**該對話方塊的頁面。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-121">However, validation of the properties entered in the pages of the **Agreement Properties** dialog box is performed using the character set selected in the **Charset and Separators** page of that dialog box.</span></span> <span data-ttu-id="5b1f6-122">在執行階段，管線會忽略此值的 x12 字元集屬性**字元集和分隔符號**頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-122">During runtime, the pipeline ignores the value of the X12 character set property **Charset and Separators** page of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="5b1f6-123">如果這兩項設定不相同 (也就是，X12 字元集屬性**協議屬性**對話方塊設**擴充**而管線屬性中的字元屬性設定為 X12**基本**)，可能會造成驗證錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-123">If these two settings are not the same (i.e., the X12 character set property in the **Agreement Properties** dialog box is set to **Extended** while the X12 character property in the pipeline properties is set to **Basic**), message validation errors could result.</span></span>  
  
 <span data-ttu-id="5b1f6-124">**資料型別驗證**</span><span class="sxs-lookup"><span data-stu-id="5b1f6-124">**Data Type Validation**</span></span>  
  
 <span data-ttu-id="5b1f6-125">對於 X12，結構描述中會標註下列 EDI 資料型別，應由接收管線或傳送管線中的解譯器/組合器元件進行驗證：Numeric、Decimal、Identifier、String、Date、Time、Binary 和 Composite。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-125">For X12, the following EDI data types are annotated in schema for validation by the Disassembler/Assembler components in the Receive or Send Pipelines: Numeric, Decimal, Identifier, String, Date, Time, Binary, and Composite.</span></span>  
  
 <span data-ttu-id="5b1f6-126">對於 EDIFACT，結構描述中會標註下列 EDI 資料型別，應由接收管線或傳送管線中的解譯器/組合器元件進行驗證：Alphabetic、Numeric、Identifier、String 和 Composite。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-126">For EDIFACT, the following EDI data types are annotated in schema for validation by the Disassembler/Assembler components in the Receive or Send Pipelines: Alphabetic, Numeric, Identifier, String, and Composite.</span></span>  
  
 <span data-ttu-id="5b1f6-127">**長度限制**</span><span class="sxs-lookup"><span data-stu-id="5b1f6-127">**Length Restrictions**</span></span>  
  
 <span data-ttu-id="5b1f6-128">對於 X12 和 EDIFACT，元素或子元素都必須通過長度 (最小值和最大值) 需求的驗證。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-128">For both X12 and EDIFACT, elements or sub-elements must be validated for length (minimum and maximum) requirement.</span></span> <span data-ttu-id="5b1f6-129">長度定義為所使用的字元位置數目。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-129">Length is defined as the number of character positions used.</span></span> <span data-ttu-id="5b1f6-130">長度不包括正負號和小數點標記。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-130">Length does not include signs and decimal notations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b1f6-131">如果是 X12_AN 字串資料型別，則會保留前置空格，而且允許任何區段中使用尾端空格以滿足最小長度需求。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-131">For the X12_AN string data type, leading spaces are preserved and trailing spaces are allowed in any segment to satisfy the minimum length requirement.</span></span>  
  
 <span data-ttu-id="5b1f6-132">對於 KECA，長度是解譯為位元組數目。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-132">For KECA, length is interpreted as the number of bytes.</span></span> <span data-ttu-id="5b1f6-133">例如，如果長度定義為三，則元素或子元素可以包含三個單一位元組字元，或是一個雙位元組字元和一個單一位元組字元的組合。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-133">For example, if the length is defined as three, the element or sub-element can include either three one-byte characters or the combination of one two-byte character and one one-byte character.</span></span>  
  
 <span data-ttu-id="5b1f6-134">**空白資料元素和尾端分隔符號驗證**</span><span class="sxs-lookup"><span data-stu-id="5b1f6-134">**Empty Data Elements and Trailing Separator Validation**</span></span>  
  
 <span data-ttu-id="5b1f6-135">對於 X12，如果區段出現不可空白執行個體中標示為必要的資料元素。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-135">For X12, data elements marked as mandatory cannot be empty in an instance if the segment is present.</span></span> <span data-ttu-id="5b1f6-136">若是複合資料元素，至少必須要有一個元件資料元素有設定值。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-136">If the data element is composite at least one component data element must be valued.</span></span>  
  
 <span data-ttu-id="5b1f6-137">對於 EDIFACT，可以排除非值和條件式資料元素 (和子元件)，不過分隔符號會加以保留。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-137">For EDIFACT, non-valued and conditional data elements (and sub-components) may be excluded; however, the separator is retained.</span></span>  
  
 <span data-ttu-id="5b1f6-138">尾端分隔符號對 X12 或 EDIFACT 來說都不是必要項，但建議使用它。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-138">Trailing separators are not required for either X12 or EDIFACT, but are recommended.</span></span>  
  
## <a name="when-edi-type-validation-is-disabled"></a><span data-ttu-id="5b1f6-139">當 EDI 類型驗證停用時</span><span class="sxs-lookup"><span data-stu-id="5b1f6-139">When EDI Type Validation Is Disabled</span></span>  
 <span data-ttu-id="5b1f6-140">如果您停用 EDI 類型驗證，則 EDI 接收管線或 EDI 傳送管線會處理由 EDI 類型驗證檢查出有錯誤的資料元素，而不會擱置要進行處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-140">If you deactivate the EDI type validation, the EDI receive pipeline or EDI send pipeline will process data elements that have errors checked by the EDI type validation without suspending the message being processed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b1f6-141">即使 EDI 類型驗證已停用，則會執行 EDI 結構驗證。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-141">EDI structural validation is performed even if the EDI type validation is disabled.</span></span> <span data-ttu-id="5b1f6-142">未通過基本結構驗證的交換將遭擱置，即使 EDI 類型驗證已停用。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-142">An interchange that fails the basic structural validations will be suspended, even if the EDI Type validation is disabled.</span></span>  
  
 <span data-ttu-id="5b1f6-143">下面是一些會被處理而不會造成訊息擱置的錯誤：</span><span class="sxs-lookup"><span data-stu-id="5b1f6-143">Some of the errors that will be processed without causing the message to be suspended are:</span></span>  
  
-   <span data-ttu-id="5b1f6-144">未預期/未定義的交易集</span><span class="sxs-lookup"><span data-stu-id="5b1f6-144">An unexpected/undefined transaction set</span></span>  
  
-   <span data-ttu-id="5b1f6-145">位在區段/迴圈和資料元素層級的未預期/未定義的資料</span><span class="sxs-lookup"><span data-stu-id="5b1f6-145">Unexpected/undefined data at the segment/loop and data element level</span></span>  
  
-   <span data-ttu-id="5b1f6-146">位在區段/迴圈和資料元素層級的選用性 (Min Occurs 和 Max Occurs)</span><span class="sxs-lookup"><span data-stu-id="5b1f6-146">Optionality (min and max occurs) at the segment/loop and data element level</span></span>  
  
-   <span data-ttu-id="5b1f6-147">資料元素層級的長度 (最小值/最大值) 違規 (資料長度超過最大層級或低於最小層級)</span><span class="sxs-lookup"><span data-stu-id="5b1f6-147">Length (min/max) violation at the data element level (data with length exceeding the maximum level or below the minimum level)</span></span>  
  
-   <span data-ttu-id="5b1f6-148">資料元素層級位置的資料型別不符 (除了有專屬控制項的識別碼資料型別之外)</span><span class="sxs-lookup"><span data-stu-id="5b1f6-148">Data type mismatch at the data element level (except for the ID data type, which has its own control)</span></span>  
  
-   <span data-ttu-id="5b1f6-149">資料元素層級位置的無效列舉清單</span><span class="sxs-lookup"><span data-stu-id="5b1f6-149">Invalid enumeration list at the data element level.</span></span>  
  
 <span data-ttu-id="5b1f6-150">如果 EDI 類型驗證在接收端已停用，但在傳送端上是啟用狀態，則當 XML 檔案包含錯誤時，EDI 傳送管線就無法將接收管線所產生的 XML 重新處理成有效的 EDI 檔案。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-150">If EDI type validation is disabled on the receive side, but enabled on the send side, the EDI send pipeline will not be able to reprocess the XML produced by the receive pipeline into a valid EDI file if the XML file contains errors.</span></span> <span data-ttu-id="5b1f6-151">因此傳送管線就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-151">As a result, the send pipeline will generate an error.</span></span>  
  
 <span data-ttu-id="5b1f6-152">如果 EDI 類型驗證已停用，EDI 接收管線或傳送管線將依照下列方式處理錯誤：</span><span class="sxs-lookup"><span data-stu-id="5b1f6-152">If EDI Type validation is disabled, the EDI receive pipeline or send pipeline will handle errors as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b1f6-153">未預期的資料</span><span class="sxs-lookup"><span data-stu-id="5b1f6-153">Unexpected Data</span></span>|<span data-ttu-id="5b1f6-154">動作</span><span class="sxs-lookup"><span data-stu-id="5b1f6-154">Action</span></span>|  
|<span data-ttu-id="5b1f6-155">未預期/未定義的交易集</span><span class="sxs-lookup"><span data-stu-id="5b1f6-155">Unexpected/undefined transaction set</span></span>|<span data-ttu-id="5b1f6-156">EDI 接收或傳送管線會接受交易集，即使其結構描述尚未部署</span><span class="sxs-lookup"><span data-stu-id="5b1f6-156">The EDI receive or send pipeline will accept a transaction set even if a schema for it has not been deployed</span></span>|  
|<span data-ttu-id="5b1f6-157">未預期的區段/記錄</span><span class="sxs-lookup"><span data-stu-id="5b1f6-157">Unexpected segment/record</span></span>|<span data-ttu-id="5b1f6-158">接收管線會產生具有適當的前置詞的標記： \<UnexpectedSegment_ %segmentid%\>。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-158">The receive pipeline will generate a tag with the appropriate prefix: \<UnexpectedSegment_%SegmentID%\>.</span></span><br /><br /> <span data-ttu-id="5b1f6-159">傳送管線會將 XML 標記名稱的前三個字元做為區段名稱。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-159">The send pipeline will use the first one to three characters of the XML Tag name as the segment name.</span></span>|  
|<span data-ttu-id="5b1f6-160">未預期的簡單資料元素</span><span class="sxs-lookup"><span data-stu-id="5b1f6-160">Unexpected simple data element</span></span>|<span data-ttu-id="5b1f6-161">接收管線會使用前置詞、區段識別項，以及表示區段中資料元素位置的索引，來產生 XML 標記：<UnexpectedDataElement_%FieldName%。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-161">The receive pipeline will generate an XML tag with a prefix, segment identifier, and index representing the position of the data element in the segment: <UnexpectedDataElement_%FieldName%.</span></span>|  
|<span data-ttu-id="5b1f6-162">未預期的複合資料元素</span><span class="sxs-lookup"><span data-stu-id="5b1f6-162">Unexpected composite data element</span></span>|<span data-ttu-id="5b1f6-163">接收管線會使用前置詞、區段識別項，以及表示區段中資料元素位置的索引，來產生 XML 標記：<UnexpectedCompositeDataElement_%FieldName%。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-163">The receive pipeline will generate an XML tags with prefix, segment identifier, and index representing the position of the data element in the segment: <UnexpectedCompositeDataElement_%FieldName%.</span></span>|  
|<span data-ttu-id="5b1f6-164">遺失必要的資料</span><span class="sxs-lookup"><span data-stu-id="5b1f6-164">Missing required data</span></span>|<span data-ttu-id="5b1f6-165">管線會將該資料視為選擇性。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-165">The pipeline will treat the data as optional.</span></span>|  
|<span data-ttu-id="5b1f6-166">資料元素長度違規</span><span class="sxs-lookup"><span data-stu-id="5b1f6-166">Data element length violation</span></span>|<span data-ttu-id="5b1f6-167">管線會將無效的資料元素長度視為有效 (最小值 = 0、最大值 = 無限制)。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-167">The pipeline will treat the invalid data element length as valid (min = 0 and max = unbounded).</span></span>|  
|<span data-ttu-id="5b1f6-168">執行個體中的無效列舉值 (適用於識別碼資料型別)</span><span class="sxs-lookup"><span data-stu-id="5b1f6-168">Invalid enumeration value in the instance (applicable to the ID data type)</span></span>|<span data-ttu-id="5b1f6-169">管線會忽略該錯誤並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-169">The pipeline will ignore the error and continue processing.</span></span>|  
|<span data-ttu-id="5b1f6-170">執行個體中出現「最大」重複違規</span><span class="sxs-lookup"><span data-stu-id="5b1f6-170">‘Max’ repletion violation in the instance</span></span>|<span data-ttu-id="5b1f6-171">管線會將這類重複資料視為有效 (Min Occurs = 0、Max Occurs = 無限制)。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-171">The pipeline will treat such repetitive data as valid (min occurs = 0 and max occurs = unbounded).</span></span>|  
  
 <span data-ttu-id="5b1f6-172">**錯誤報告**</span><span class="sxs-lookup"><span data-stu-id="5b1f6-172">**Error Reporting**</span></span>  
  
 <span data-ttu-id="5b1f6-173">當 EDI 類型驗證關閉時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不會在 [事件檢視器] 中報告錯誤，而是報告警告。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-173">When EDI type validation is turned off, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not report errors in the Event Viewer, but reports a warning.</span></span> <span data-ttu-id="5b1f6-174">此外，通知會向來源合作對象回報「接受」，其方法是將 AK501 和 AK901 設定為 "E" (對於 X12 997)，而將 UCI.4、UCM.3 和 UCF.4 設定為 "7" (對於 EDIFACT CONTRL)。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-174">In addition, the acknowledgment reports an ‘Accept’ back to the source party, setting AK501 and AK901 as “E” in an X12 997 or UCI.4, UCM.3, and UCF.4 as “7” in an EDIFACT CONTRL.</span></span> <span data-ttu-id="5b1f6-175">如此一來，未來傳輸中就沒有任何修正的機會。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-175">As a result, any chance of rectification in future transmissions will be eliminated.</span></span> <span data-ttu-id="5b1f6-176">不過，訊息接收者有機會透過手動處理來搶救文件，而不放任訊息遭拒絕或擱置。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-176">However, receivers of the message will have an opportunity to salvage the document via manual intervention rather than the message being rejected or suspended.</span></span> <span data-ttu-id="5b1f6-177">此外，當 EDI 接收管線遇到上述任何一種錯誤時，`Edi.ErrorsInTransactionSet` 內容屬性也會進行升級。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-177">Also, the `Edi.ErrorsInTransactionSet` context property will be promoted if any of these errors are encountered by the EDI receive pipeline.</span></span> <span data-ttu-id="5b1f6-178">如果遇到 EDI 或擴充驗證錯誤，這個屬性會升級為 "True"。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-178">This property will be promoted as "True" if EDI or Extended validation errors are encountered.</span></span> <span data-ttu-id="5b1f6-179">如果未遇到錯誤，則這個屬性將升級為 "False"。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-179">If not errors are encountered, the property will be promoted as "False".</span></span>  
  
 <span data-ttu-id="5b1f6-180">如果接收或傳送管線遇到未預期的資料，它會在父層級報告錯誤並忽略子層級錯誤，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5b1f6-180">If the receive or send pipeline encounters unexpected data, it will report the error at the parent level and ignore child level errors, as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b1f6-181">未預期的資料</span><span class="sxs-lookup"><span data-stu-id="5b1f6-181">Unexpected Data</span></span>|<span data-ttu-id="5b1f6-182">動作</span><span class="sxs-lookup"><span data-stu-id="5b1f6-182">Action</span></span>|  
|<span data-ttu-id="5b1f6-183">未預期的交易集</span><span class="sxs-lookup"><span data-stu-id="5b1f6-183">Unexpected transaction set</span></span>|<span data-ttu-id="5b1f6-184">通知會報告這個錯誤，並忽略區段/迴圈和資料元素層級位置的後續錯誤</span><span class="sxs-lookup"><span data-stu-id="5b1f6-184">The acknowledgment reports this error and ignores subsequent errors at the segment/loop and data element level</span></span>|  
|<span data-ttu-id="5b1f6-185">未預期的區段/迴圈</span><span class="sxs-lookup"><span data-stu-id="5b1f6-185">Unexpected segment/loop</span></span>|<span data-ttu-id="5b1f6-186">通知會報告這個錯誤，並忽略資料元素層級的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-186">The acknowledgment reports this error and ignores errors at the data element level.</span></span>|  
|<span data-ttu-id="5b1f6-187">未預期的資料元素</span><span class="sxs-lookup"><span data-stu-id="5b1f6-187">Unexpected data element</span></span>|<span data-ttu-id="5b1f6-188">通知會報告這個錯誤，並忽略與屬性 (如識別碼、長度、相符項目等) 相關的複合錯誤，以及與複合資料元素欄位相關的錯誤 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="5b1f6-188">The acknowledgment reports this error and ignores compound errors relating to properties like ID, length, occours, etc) and errors relating to composite data element fields (if applicable).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b1f6-189">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b1f6-189">See Also</span></span>  
 <span data-ttu-id="5b1f6-190">[EDI 訊息驗證](../core/edi-message-validation.md) </span><span class="sxs-lookup"><span data-stu-id="5b1f6-190">[EDI Message Validation](../core/edi-message-validation.md) </span></span>  
 [<span data-ttu-id="5b1f6-191">延伸 (BTS-XSD) 驗證</span><span class="sxs-lookup"><span data-stu-id="5b1f6-191">Extended (BTS-XSD) Validation</span></span>](../core/extended-bts-xsd-validation.md)