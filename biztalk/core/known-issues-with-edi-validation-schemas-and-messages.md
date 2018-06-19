---
title: EDI 驗證、 結構描述和訊息的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 417c3e18-9a97-4d59-bc2b-e96a8c33d388
caps.latest.revision: 42
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a508834ff81814b17bc12f1d698984d65748092
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264558"
---
# <a name="known-issues-with-edi-validation-schemas-and-messages"></a><span data-ttu-id="61201-102">EDI 驗證、結構描述和訊息的已知問題</span><span class="sxs-lookup"><span data-stu-id="61201-102">Known Issues with EDI Validation, Schemas, and Messages</span></span>
<span data-ttu-id="61201-103">本主題描述已知的驗證問題。</span><span class="sxs-lookup"><span data-stu-id="61201-103">This topic describes known validation issues.</span></span>  
  
## <a name="message-is-suspended-with-edi-validation-turned-off"></a><span data-ttu-id="61201-104">訊息在 EDI 驗證關閉的情況下遭到擱置</span><span class="sxs-lookup"><span data-stu-id="61201-104">Message Is Suspended with EDI Validation Turned Off</span></span>  
 <span data-ttu-id="61201-105">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="61201-105">**Symptom**</span></span>  
  
 <span data-ttu-id="61201-106">違反配對規則且驗證已關閉，但訊息被擱置 (預期的結果是訊息會進行序列化)。</span><span class="sxs-lookup"><span data-stu-id="61201-106">A paired rule is violated, and validation is turned off, but the message is suspended (expected results are that the message is serialized).</span></span>  
  
 <span data-ttu-id="61201-107">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="61201-107">**Possible Cause**</span></span>  
  
 <span data-ttu-id="61201-108">執行欄位/區段交互驗證，即使**EDI 類型**中取消選取了屬性**驗證和通知的產生設定**節點**EDI 屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="61201-108">Cross-field/segment validation is performed, even if **EDI type** property is deselected in the **Validation and ACK Generation Settings** node of the **EDI Properties** dialog box.</span></span> <span data-ttu-id="61201-109">驗證之所以執行，是因為在結構描述註解中開啟了它。</span><span class="sxs-lookup"><span data-stu-id="61201-109">Validation occurs because it is turned on in the schema annotation.</span></span>  
  
 <span data-ttu-id="61201-110">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="61201-110">**Resolution**</span></span>  
  
 <span data-ttu-id="61201-111">關閉結構描述註解中的驗證。</span><span class="sxs-lookup"><span data-stu-id="61201-111">Turn off validation in the schema annotation.</span></span>  
  
## <a name="the-biztalk-service-needs-to-be-restarted-after-a-schema-has-been-edited-and-redeployed"></a><span data-ttu-id="61201-112">BizTalk 服務在結構描述編輯和重新部署之後必須重新啟動</span><span class="sxs-lookup"><span data-stu-id="61201-112">The BizTalk service needs to be restarted after a schema has been edited and redeployed</span></span>  
 <span data-ttu-id="61201-113">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="61201-113">**Symptom**</span></span>  
  
 <span data-ttu-id="61201-114">BizTalk Server 在結構描述編輯和重新部署之後，未能成功處理有效訊息。</span><span class="sxs-lookup"><span data-stu-id="61201-114">BizTalk Server does not successfully process a valid message after a schema has been edited and redeployed.</span></span>  
  
 <span data-ttu-id="61201-115">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="61201-115">**Possible Cause**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="61201-116">快取逾時限制結構描述。</span><span class="sxs-lookup"><span data-stu-id="61201-116"> caches schemas with unlimited timeouts.</span></span>  
  
 <span data-ttu-id="61201-117">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="61201-117">**Resolution**</span></span>  
  
 <span data-ttu-id="61201-118">編輯和重新部署結構描述之後，重新啟動 BizTalk Server 應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="61201-118">After editing and redeploying a schema, restart the BizTalk Server Application service.</span></span> <span data-ttu-id="61201-119">若有管線使用重新部署的結構描述，則裝載該管線的主控件執行個體也必須重新啟動。</span><span class="sxs-lookup"><span data-stu-id="61201-119">You also must restart the host instance hosting the pipeline that is using the redeployed schema.</span></span>  
  
## <a name="processing-has-been-aborted-for-messages-of-a-single-encoding-type-for-a-single-party"></a><span data-ttu-id="61201-120">已中止處理單一合作對象的單一編碼類型訊息</span><span class="sxs-lookup"><span data-stu-id="61201-120">Processing Has Been Aborted for Messages of a Single Encoding Type for a Single Party</span></span>  
 <span data-ttu-id="61201-121">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="61201-121">**Symptom**</span></span>  
  
 <span data-ttu-id="61201-122">已中止處理單一合作對象的單一編碼類型 (例如 X12 或 EDIFACT) 的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="61201-122">The processing of all messages of a single encoding type (for example, X12 or EDIFACT) for a single party have been aborted.</span></span> <span data-ttu-id="61201-123">處理同一合作對象的其他編碼類型訊息，或處理其他合作對象的任何訊息，則不受影響。</span><span class="sxs-lookup"><span data-stu-id="61201-123">Processing of messages of another encoding type for the same party, or any messages for another party, has not been affected.</span></span>  
  
 <span data-ttu-id="61201-124">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="61201-124">**Possible Cause**</span></span>  
  
 <span data-ttu-id="61201-125">交換、群組或交易集控制編號的長度超過允許的長度上限。</span><span class="sxs-lookup"><span data-stu-id="61201-125">The length of the interchange, group, or transaction set control number has exceeded the maximum allowable length.</span></span>  
  
 <span data-ttu-id="61201-126">若是 X12 訊息，控制編號的最大長度為 9 個數字。</span><span class="sxs-lookup"><span data-stu-id="61201-126">For X12 messages, the maximum length of a control number is nine digits.</span></span> <span data-ttu-id="61201-127">若是 EDIFACT 訊息，控制編號的最大長度為三個欄位 14 個數字。</span><span class="sxs-lookup"><span data-stu-id="61201-127">For EDIFACT message, the maximum length of a control number is 14 digits over three fields.</span></span>  
  
 <span data-ttu-id="61201-128">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="61201-128">**Resolution**</span></span>  
  
 <span data-ttu-id="61201-129">在受影響合作對象的 [EDI 屬性] 對話方塊，重設適當屬性頁中的控制編號。</span><span class="sxs-lookup"><span data-stu-id="61201-129">Reset the control number in the appropriate property page of the EDI Properties dialog box for the affected party.</span></span> <span data-ttu-id="61201-130">您可以編輯下列屬性頁中的控制編號：</span><span class="sxs-lookup"><span data-stu-id="61201-130">You can edit the control numbers in the following property pages:</span></span>  
  
-   <span data-ttu-id="61201-131">X12 交換控制編號：[X12] 屬性的 [ISA 區段定義] 頁面 (在 [做為交換接收者的合作對象] 節點中)</span><span class="sxs-lookup"><span data-stu-id="61201-131">X12 interchange control number: ISA Segment Definition page (in the Party as Interchange Receiver node) for X12 Properties</span></span>  
  
-   <span data-ttu-id="61201-132">X12 群組或交易集控制編號： [GS 和 ST 區段定義] 頁面 (在 [X12] 屬性的 [做為交換接收者的合作對象] 節點中)</span><span class="sxs-lookup"><span data-stu-id="61201-132">X12 group or transaction set control number: GS and ST Segment Definition page (in the Party as Interchange Receiver node for X12 Properties)</span></span>  
  
-   <span data-ttu-id="61201-133">EDIFACT 交換控制編號：[UNB 區段定義] 頁面 (在[EDIFACT] 屬性的 [做為交換接收者的合作對象] 節點中)</span><span class="sxs-lookup"><span data-stu-id="61201-133">EDIFACT interchange control number: UNB Segment Definition page (in the Party as Interchange Receiver node for EDIFACT Properties)</span></span>  
  
-   <span data-ttu-id="61201-134">EDIFACT 群組或交易集控制編號：[UNG 和 UNH 區段定義] 頁面 (在[EDIFACT] 屬性的 [做為交換接收者的合作對象] 節點中)</span><span class="sxs-lookup"><span data-stu-id="61201-134">EDIFACT group or transaction set control number: UNG and UNH Segment Definition page (in the Party as Interchange Receiver node for EDIFACT Properties)</span></span>  
  
## <a name="biztalk-server-validates-with-schemas-that-have-unh-segments-with-seven-data-elements"></a><span data-ttu-id="61201-135">BizTalk Server 使用包含有七個資料元素之 UNH 區段的結構描述進行驗證</span><span class="sxs-lookup"><span data-stu-id="61201-135">BizTalk Server validates with schemas that have UNH segments with seven data elements</span></span>  
 <span data-ttu-id="61201-136">在舊版 EDIFACT 中，UNH 區段有四個資料元素，而非新版 UNH 區段的七個元素 (其中三個為選擇項)。</span><span class="sxs-lookup"><span data-stu-id="61201-136">In earlier versions of EDIFACT, the UNH segment has four elements, rather than the seven elements (three of which are optional) that the UNH segment has in later versions.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="61201-137">使用內含七個元素的較新版本進行驗證。</span><span class="sxs-lookup"><span data-stu-id="61201-137"> uses the later version with seven elements for validation.</span></span>  
  
## <a name="error-messages-generated-for-multiple-cross-field-validation-rules-will-not-be-specific-to-the-rule"></a><span data-ttu-id="61201-138">針對多個欄位交互驗證規則所產生的錯誤訊息與規則沒有關聯</span><span class="sxs-lookup"><span data-stu-id="61201-138">Error messages generated for multiple cross-field validation rules will not be specific to the rule</span></span>  
 <span data-ttu-id="61201-139">如果結構描述包含多個欄位交互驗證規則來驗證訊息中的資料元素，而資料元素發生錯誤，每個驗證規則會各產生一個錯誤。</span><span class="sxs-lookup"><span data-stu-id="61201-139">If a schema contains multiple cross-field validation rules for a data element in a message, and an error occurs with the data element, a separate error will be generated for each validation rule.</span></span> <span data-ttu-id="61201-140">但是，每個錯誤的錯誤碼和描述都相同，即錯誤與驗證規則沒有關聯。</span><span class="sxs-lookup"><span data-stu-id="61201-140">However, each of these errors will have the same error code and description; the errors will not be specific to the validation rule.</span></span>  
  
## <a name="if-edi-type-validation-is-disabled-on-receive-and-enabled-on-send-the-send-pipeline-will-not-be-able-to-serialize-the-message"></a><span data-ttu-id="61201-141">如果 EDI 類型驗證在接收時停用而在傳送時啟用，則傳送管線將無法序列化訊息。</span><span class="sxs-lookup"><span data-stu-id="61201-141">If EDI type validation is disabled on receive and enabled on send, the send pipeline will not be able to serialize the message</span></span>  
 <span data-ttu-id="61201-142">如果您在接收端關閉 EDI 類型驗證，EDI 接收管線會從接收的 EDI 訊息產生 XML 訊息，而不管訊息有效與否。</span><span class="sxs-lookup"><span data-stu-id="61201-142">If you turn off EDI type validation on the receive side, the EDI receive pipeline will generate an XML message from a received EDI message, whether or not the message is valid.</span></span> <span data-ttu-id="61201-143">如果 EDI 驗證在傳送端啟用，若 XML 檔案包含錯誤，EDI 傳送管線無法將 XML 重新處理成有效的 EDI 檔案，因此會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="61201-143">If EDI validation is enabled on the send side, the EDI send pipeline will not be able to reprocess the XML into a valid EDI file if the XML file contains errors, and as a result will generate an error.</span></span>  
  
## <a name="edi-promoted-properties-are-only-available-if-your-application-has-a-reference-to-the-biztalk-edi-application"></a><span data-ttu-id="61201-144">只有在您的應用程式有 BizTalk EDI 應用程式的參考時，EDI 升級屬性才會出現</span><span class="sxs-lookup"><span data-stu-id="61201-144">EDI promoted properties are only available if your application has a reference to the BizTalk EDI application</span></span>  
 <span data-ttu-id="61201-145">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="61201-145">**Symptom**</span></span>  
  
 <span data-ttu-id="61201-146">在您嘗試用於如協調流程或傳送埠篩選條件的升級屬性清單中，EDI 命名空間底下的升級屬性未顯示出來。</span><span class="sxs-lookup"><span data-stu-id="61201-146">Promoted properties under the EDI namespace are not displayed in the list of promoted properties that you are trying to use, for example, in an orchestration or in the filter conditions for a send port.</span></span>  
  
 <span data-ttu-id="61201-147">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="61201-147">**Possible Cause**</span></span>  
  
 <span data-ttu-id="61201-148">您使用的 BizTalk 應用程式沒有 BizTalk EDI 應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="61201-148">The BizTalk application that you are using does not have a reference to the BizTalk EDI Application.</span></span> <span data-ttu-id="61201-149">EDI 升級屬性的屬性結構描述位於 Microsoft.BizTalk.Edi.BaseArtifacts.dll 中，這個檔案包含在 BizTalk EDI 應用程式的 [資源] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="61201-149">The property schemas for the EDI promoted properties are in Microsoft.BizTalk.Edi.BaseArtifacts.dll, which is included in the Resources folder of BizTalk EDI Application.</span></span>  
  
 <span data-ttu-id="61201-150">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="61201-150">**Resolution**</span></span>  
  
 <span data-ttu-id="61201-151">針對您目前使用的 BizTalk 應用程式，加入 BizTalk EDI 應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="61201-151">To the BizTalk application that you are working in, add a reference to the BizTalk EDI Application.</span></span>  
  
## <a name="the-data-element-name-in-a-context-property-name-contains-an-underscore-not-a-period"></a><span data-ttu-id="61201-152">內容屬性名稱中的資料元素名稱包含底線，而非句號</span><span class="sxs-lookup"><span data-stu-id="61201-152">The Data Element Name in a Context Property Name Contains an Underscore, Not a Period</span></span>  
 <span data-ttu-id="61201-153">EDI 區段內資料元素的名稱包含句號，例如 UNB2.1 (UNB2 Sender 區段的識別欄位)。</span><span class="sxs-lookup"><span data-stu-id="61201-153">The name of a data element within an EDI segment contains a period, for example, UNB2.1, which is the identification field for the UNB2 Sender segment.</span></span> <span data-ttu-id="61201-154">不過，當 EDI 內容屬性中包含資料元素名稱時，便會將句號取代為底線。</span><span class="sxs-lookup"><span data-stu-id="61201-154">However, when the data element name is included as part of an EDI context property, the period is replaced with an underscore.</span></span> <span data-ttu-id="61201-155">例如，Sender Identification 資料元素是 EDI.UNB2_1，不是 EDI.UNB2.1。</span><span class="sxs-lookup"><span data-stu-id="61201-155">For example, the context property for the Sender Identification data element is EDI.UNB2_1, not EDI.UNB2.1.</span></span> <span data-ttu-id="61201-156">這是因為內容屬性名稱不支援句號。</span><span class="sxs-lookup"><span data-stu-id="61201-156">The reason for this is that a period is not supported in a context property name.</span></span>  
  
## <a name="irrelevant-string-is-appended-to-instance-validation-error-message"></a><span data-ttu-id="61201-157">不相關的字串附加到執行個體驗證訊息</span><span class="sxs-lookup"><span data-stu-id="61201-157">Irrelevant string is appended to instance validation error message</span></span>  
 <span data-ttu-id="61201-158">每當在執行個體驗證期間收到錯誤，字串 "BEC 2004" 都會附加到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="61201-158">Whenever you receive an error during instance validation, the string "BEC 2004" will be appended to the error message.</span></span> <span data-ttu-id="61201-159">您可以忽略此字串。</span><span class="sxs-lookup"><span data-stu-id="61201-159">You can ignore this string.</span></span>  
  
## <a name="edifact-schema-names-are-case-sensitive"></a><span data-ttu-id="61201-160">EDIFACT 結構描述名稱區分大小寫</span><span class="sxs-lookup"><span data-stu-id="61201-160">EDIFACT Schema Names Are Case-Sensitive</span></span>  
 <span data-ttu-id="61201-161">EDIFACT 結構描述的結構描述名稱 (如結構描述的 root_reference 資料元素中所示) 區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="61201-161">The schema name of an EDIFACT schema, as shown in the root_reference data element of the schema, is case-sensitive.</span></span> <span data-ttu-id="61201-162">例如，EFACT_D98B_ORDERS 和 EFACT_d98B_Orders 是兩個不同的結構描述。</span><span class="sxs-lookup"><span data-stu-id="61201-162">For example, EFACT_D98B_ORDERS and EFACT_d98B_Orders would be two different schemas.</span></span>  
  
## <a name="invalid-edi-messages-can-be-suspended-even-if-edi-type-validation-is-disabled"></a><span data-ttu-id="61201-163">即使 EDI 類型驗證已停用，仍可擱置無效的 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="61201-163">Invalid EDI Messages Can Be Suspended Even If EDI Type Validation Is Disabled</span></span>  
 <span data-ttu-id="61201-164">即使 EDI 類型驗證已停用，EDI 結構驗證仍然會執行。</span><span class="sxs-lookup"><span data-stu-id="61201-164">EDI structural validation is performed even if the EDI Type validation is disabled.</span></span> <span data-ttu-id="61201-165">未通過基本結構驗證的交換將遭擱置，即使 EDI 類型驗證已停用。</span><span class="sxs-lookup"><span data-stu-id="61201-165">An interchange that fails the basic structural validations will be suspended, even if the EDI Type validation is disabled.</span></span>  
  
## <a name="the-edi-assembler-will-serialize-an-unbatched-interchange-even-if-a-separator-character-is-used-in-an-envelope-header"></a><span data-ttu-id="61201-166">即使在信封標頭中使用了分隔符號，EDI 組合器仍會序列化非批次交換</span><span class="sxs-lookup"><span data-stu-id="61201-166">The EDI Assembler Will Serialize an Unbatched Interchange Even If a Separator Character Is Used in an Envelope Header</span></span>  
 <span data-ttu-id="61201-167">在任何交換、群組或交易集標頭或結尾欄位的定義中，都不能使用分隔標頭和結尾欄位的分隔符號，如做為交換接收者的合作對象的定義。</span><span class="sxs-lookup"><span data-stu-id="61201-167">The separator characters used to separate header and trailer fields must not be used in the definition of any of the interchange, group, or transaction set header or trailer fields, as defined for the party as interchange receiver.</span></span> <span data-ttu-id="61201-168">如果使用分隔符號字元，則無論是在傳送端 BizTalk Server 的「EDI 組合器」中，或是在接收合作對象的解譯器中，交換在處理時都會失敗。</span><span class="sxs-lookup"><span data-stu-id="61201-168">If they are, the interchange will fail processing either in the EDI Assembler of the sending BizTalk Server or in the disassembler of the receiving party.</span></span> <span data-ttu-id="61201-169">如果交換是輸出批次，它在「EDI 組合器」中即會失敗，因為「組合器」會針對標頭控制 (服務) 結構描述驗證信封。</span><span class="sxs-lookup"><span data-stu-id="61201-169">The interchange will fail in the EDI Assembler if it is an outbound batch, because the Assembler will validate the envelope against the header control (service) schema.</span></span> <span data-ttu-id="61201-170">如果交換不是批次，則「EDI 組合器」會進行序列化，但會在接收合作對象的解譯器中處理失敗。</span><span class="sxs-lookup"><span data-stu-id="61201-170">If the interchange is unbatched, the EDI Assembler will serialize it, but it will fail processing in the disassembler at the receiving party.</span></span>  
  
## <a name="mismatched-character-sets-can-result-in-suspended-interchanges"></a><span data-ttu-id="61201-171">不相符的字元集可能導致交換遭擱置</span><span class="sxs-lookup"><span data-stu-id="61201-171">Mismatched Character Sets Can Result in Suspended Interchanges</span></span>  
 <span data-ttu-id="61201-172">外寄交換使用的字元集應與用來建立插入交換的交易集的字元集相同。</span><span class="sxs-lookup"><span data-stu-id="61201-172">The character set used for an outgoing interchange should be the same as the character set used to create the transaction sets inserted into the interchange.</span></span> <span data-ttu-id="61201-173">如果不同，交換可能會遭擱置，並出現錯誤訊息，表示有無效字元。</span><span class="sxs-lookup"><span data-stu-id="61201-173">If not, the interchange will likely be suspended with an error message indicating that there were invalid characters.</span></span>  
  
 <span data-ttu-id="61201-174">例如，如果您使用 UNOA 字元集建立 EDIFACT 批次，但加入至批次的交易集有小寫字元，則批次處理協調流程將擱置訊息，因為 UNOA 不允許小寫字元。</span><span class="sxs-lookup"><span data-stu-id="61201-174">For example, if you create an EDIFACT batch using the UNOA character set, but a transaction set added to the batch has lower-case characters, the batching orchestration will suspend the message because UNOA does not allow lower-case characters.</span></span>  
  
 <span data-ttu-id="61201-175">另一個範例是，如果您使用「基礎」字元集設定 X12 交換的 EDI 傳送管線，但 X12 批次交換有小寫字元，原因是在做為交換接收者的合作對象的 [產生 X12 交換信封] 頁面中選取的 X12 字元集設為「擴充」或「UTF8/Unicode」，則當套用信封設定時，批次訊息將遭擱置。</span><span class="sxs-lookup"><span data-stu-id="61201-175">As another example, if you configure the EDI send pipeline for X12 interchanges with the "Basic" character set, but an X12 batched interchange has lower-case characters because the X12 character set selected in the X12 Interchange Envelop Generation page for the party as an interchange receiver is set to "Extended" or "UTF8/Unicode", the batched message will be suspended when envelope settings are applied.</span></span>  
  
## <a name="using-unh25-for-schema-resolution-requires-an-update-to-the-schema"></a><span data-ttu-id="61201-176">使用 UNH2.5 進行結構描述解析時需要更新結構描述</span><span class="sxs-lookup"><span data-stu-id="61201-176">Using UNH2.5 for schema resolution requires an update to the schema</span></span>  
 <span data-ttu-id="61201-177">如果您使用 UNH2.5 （關聯指定代碼） 來解析結構描述的內送 EDIFACT 交換時，您必須更新 \Program Files\Microsoft BizTalk Server 20xx\Schema 資料夾中的相關文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="61201-177">If you use UNH2.5 (the Association assigned code) for schema resolution of an incoming EDIFACT interchange, you will need to update the relevant document schema in the \Program Files\Microsoft BizTalk Server 20xx\Schema folder.</span></span> <span data-ttu-id="61201-178">您必須將 UNH2.5 的值附加到 root_reference、display_reference 和 xs:element 名稱的現有值。</span><span class="sxs-lookup"><span data-stu-id="61201-178">You will need to append the value of UNH2.5 to the existing values for the root_reference, display_reference, and xs:element name.</span></span> <span data-ttu-id="61201-179">例如，如果 UNH2.5 是 "EAN008"，而您使用 EFACT_D96A_INVOIC 結構描述，就應將 root_reference、display_reference 和 xs:element 名稱設定為 "EFACT_D96A_INVOIC_EAN008"。</span><span class="sxs-lookup"><span data-stu-id="61201-179">For example, if UNH2.5 is "EAN008" and you are using the EFACT_D96A_INVOIC schema, you would set root_reference, display_reference, and xs:element name to "EFACT_D96A_INVOIC_EAN008".</span></span>  
  
## <a name="the-compressed-file-of-schemas-will-be-replaced-when-an-upgrade-is-performed"></a><span data-ttu-id="61201-180">執行升級時，會取代結構描述的壓縮檔</span><span class="sxs-lookup"><span data-stu-id="61201-180">The compressed file of schemas will be replaced when an upgrade is performed</span></span>  
 <span data-ttu-id="61201-181">如果您將 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 升級到更新的組建，原來安裝中的 MicrosoftEdiXSDTemplates.exe 檔案會被取代為與升級相關聯的 MicrosoftEdiXSDTemplates.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="61201-181">If you upgrade Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to a later build, the MicrosoftEdiXSDTemplates.exe file in your installation will be replaced with the MicrosoftEdiXSDTemplates.exe file associated with the upgrade.</span></span> <span data-ttu-id="61201-182">如果您打算繼續使用舊壓縮檔中的結構描述，除非備份舊壓縮檔，否則您在升級後將無法再存取這些壓縮檔。</span><span class="sxs-lookup"><span data-stu-id="61201-182">If you plan to continue to use the schemas from the old compressed file, you will no longer have access to the compressed file after the upgrade unless you back up the old compressed file.</span></span>  
  
## <a name="if-a-group-contains-multiple-x12-transaction-sets-all-must-be-of-the-same-type"></a><span data-ttu-id="61201-183">如果群組包含多個 X12 交易集，所有必須是相同的型別</span><span class="sxs-lookup"><span data-stu-id="61201-183">If a group contains multiple X12 transaction sets, all must be of the same type</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="61201-184">不支援混用不同的交易集內同一個群組。</span><span class="sxs-lookup"><span data-stu-id="61201-184"> does not support mixing different transaction sets within the same group.</span></span> <span data-ttu-id="61201-185">當群組包含多個交易時，ST01 值必須是相同的所有交易。</span><span class="sxs-lookup"><span data-stu-id="61201-185">When a group contains multiple transactions, the value of ST01 must be the same for all transactions.</span></span>  
  
## <a name="receiving-x12-interchanges-that-contain-non-ascii-delimiters-may-result-in-the-message-becoming-suspended"></a><span data-ttu-id="61201-186">接收 X12 包含非 ASCII 分隔符號的交換可能會導致變成擱置訊息</span><span class="sxs-lookup"><span data-stu-id="61201-186">Receiving X12 interchanges that contain non-ASCII delimiters may result in the message becoming suspended</span></span>  
 <span data-ttu-id="61201-187">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="61201-187">**Symptom**</span></span>  
  
 <span data-ttu-id="61201-188">當接收 X12 交換，它使用非 ASCII 分隔符號值，訊息可能會變成 「 已擱置和應用程式事件記錄檔中寫入錯誤。</span><span class="sxs-lookup"><span data-stu-id="61201-188">When receiving an X12 interchange that uses non-ASCII delimiter values, the message may become suspended and an error written to the application event log.</span></span>  
  
 <span data-ttu-id="61201-189">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="61201-189">**Possible Cause**</span></span>  
  
 <span data-ttu-id="61201-190">如果交換不會編碼為 utf-8，則會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="61201-190">This problem can occur if the interchange is not encoded as UTF-8.</span></span>  
  
 <span data-ttu-id="61201-191">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="61201-191">**Resolution**</span></span>  
  
 <span data-ttu-id="61201-192">請確定任何內送 X12 交換包含非 ASCII 分隔符號會編碼為 utf-8。</span><span class="sxs-lookup"><span data-stu-id="61201-192">Ensure that any incoming X12 interchange that contains non-ASCII delimiters is encoded as UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61201-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61201-193">See Also</span></span>  
 <span data-ttu-id="61201-194">[EDI 處理的已知的問題](../core/known-issues-with-edi-processing.md) </span><span class="sxs-lookup"><span data-stu-id="61201-194">[Known Issues with EDI Processing](../core/known-issues-with-edi-processing.md) </span></span>  
 <span data-ttu-id="61201-195">[EDI 傳訊](../core/edi-messaging.md) </span><span class="sxs-lookup"><span data-stu-id="61201-195">[EDI Messaging](../core/edi-messaging.md) </span></span>  
 <span data-ttu-id="61201-196">[EDI 訊息驗證](../core/edi-message-validation.md) </span><span class="sxs-lookup"><span data-stu-id="61201-196">[EDI Message Validation](../core/edi-message-validation.md) </span></span>  
 <span data-ttu-id="61201-197">[EDI 結構描述](../core/edi-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="61201-197">[EDI Schemas](../core/edi-schemas.md) </span></span>  
 [<span data-ttu-id="61201-198">開發 EDI 結構描述</span><span class="sxs-lookup"><span data-stu-id="61201-198">Developing EDI Schemas</span></span>](../core/developing-edi-schemas.md)