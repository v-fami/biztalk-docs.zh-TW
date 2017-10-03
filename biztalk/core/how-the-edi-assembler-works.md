---
title: "EDI 組合器如何運作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3785870-08ab-4fc2-8f7e-7c5a37639a7a
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f11fa41cabb6d5199953c2df005aa79965216f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-edi-assembler-works"></a>EDI 組合器如何運作
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會在 EDI 傳送管線 (`Microsoft.BizTalk.DefaultPipelines.EDISendPipeline`) 中執行對待傳送 EDI 編碼交換的大部分處理。 這個管線包含可執行下列處理的 EDI 組合器管線元件：  
  
-   序列化 EDI 交換，並將 XML 編碼訊息轉換為交換中的 EDI 交易集。  
  
-   執行 EDI 結構描述驗證、X-12 編碼訊息的欄位交互驗證 (若已設定)、EDI 結構化驗證，以及擴充的結構描述驗證 (若該結構描述已自訂為具有非 EDI 資料型別的節點)。  
  
-   將信封套用至 EDI 訊息。  
  
-   處理為了回應 EDI 訊息而接收的技術和功能通知，並會解除批次處理通知 (如果設定的話)。  
  
## <a name="applying-an-envelope-to-an-outgoing-edi-message"></a>將信封套用至外寄 EDI 訊息  
 當 EDI 傳送管線從中繼 XML 檔案建置外寄 EDI 訊息時，它會根據已針對接收端協議所建立的 EDI 屬性，將包含交換和群組標頭的信封套用至該訊息。 如果傳送管線無法從傳送埠判斷接收端協議，它就會使用後原協議來套用信封。  
  
 如果 `EdiOverride.OverrideEdiHeader` 內容屬性設定為 true，則 EDI 傳送管線會使用 EdiOverride 屬性集合中指定的值來建構信封。 如果集合中沒有某個值，則會使用協議屬性中的對應 EDI 值。 如果某個值既不存在於 EdiOverride 集合中，也不存在於協議屬性中，則會使用後援 EDI 協議中的屬性。  
  
 如果中繼 XML 檔案有保留標記或 ReuseEnvelope 內容屬性，訊息就是保留批次，而將不會套用該信封應用程式邏輯。  
  
### <a name="sources-for-x12-envelope-values"></a>X12 信封值的來源  
 下表列出 EDI 傳送管線會自何處取得 X12 信封之各個部分所需要的資訊：  
  
|標頭|Source|  
|------------|------------|  
|交換控制標頭 (ISA)|-EdiOverride 內容屬性 (如果`EdiOverride.OverrideEdiHeader`為 true)。<br />-如果已定義了協議，ISA 區段下不同頁面定義**交換設定**的單向協議屬性中的區段**協議屬性** 對話方塊。<br />-如果未定義協議時，ISA 區段下不同頁面定義**交換設定**一節中**EDIFACT 後援設定** 對話方塊。|  
|功能群組標頭 (GS)|-EdiOverride 內容屬性 (如果`EdiOverride.OverrideEdiHeader`為 true)<br />-如果已定義了協議，GS 區段定義**信封**頁面 (在**交易集設定**區段) 的單向協議屬性中**協議屬性**對話方塊<br />-如果未定義協議時，GS 區段定義**信封**頁面 (在**交易集設定**區段) 中**X12 後援設定**對話方塊<br /><br /> 如果定義了協議，傳送管線就會根據「交易集識別項」(ST1)、版本和目標命名空間的組合來判斷 GS 資料元素的值。 方格中比較這些值**信封**頁面 (在**交易集設定**區段) 的協議屬性 （如果已定義了協議） 或後援協議屬性 （如果未定義協議是）：<br /><br /> -如果沒有相符的資料列，則相符的資料列中包含的值會用於 GS 標頭。<br />-如果沒有相符項目，但預設資料列定義是，要預設列填入除 gs01 外的所有 GS 資料元素。 GS01 是根據 ST1 的值來動態決定。<br />-如果沒有相符的列，而且沒有預設值的資料列，則會擱置訊息。 **注意：**是唯一的其他群組的群組，不是所有的這些值可以是另一個群組相同。 <br /><br /> 如果未定義協議，則會從後援協議屬性填入 GS 資料元素。|  
  
### <a name="sources-for-edifact-envelope-values"></a>EDIFACT 信封值的來源  
 下表列出 EDI 傳送管線會自何處取得 EDIFACT 信封之各個部分所需要的資訊：  
  
|標頭|Source|  
|------------|------------|  
|字串服務建議 (UNA)|-EdiOverride 內容屬性 (如果`EdiOverride.OverrideEdiHeader`為 true)。<br />-如果已定義了協議，UNA 區段定義**字元集和分隔符號**頁面的單向協議屬性中**協議屬性** 對話方塊。<br />-如果未定義協議時，UNA 區段定義**字元集和分隔符號**頁面**EDIFACT 後援設定** 對話方塊。|  
|交換控制標頭 (UNB)|-EdiOverride 內容屬性 (如果`EdiOverride.OverrideEdiHeader`為 true)。<br />-如果已定義了協議，UNB 區段下不同頁面定義**交換設定**的單向協議屬性中的區段**協議屬性** 對話方塊。<br />-如果未定義協議時，UNB 區段下不同頁面定義**交換設定**一節中**EDIFACT 後援設定** 對話方塊。|  
|功能群組標頭 (UNG)|-EdiOverride 內容屬性 (如果`EdiOverride.OverrideEdiHeader`為 true)。<br />-如果已定義了協議，UNG 和 UNH 區段定義**信封**頁面 (在**交易集設定**區段) 的單向協議屬性中**協議屬性**對話方塊<br />-如果未定義協議時，適用的 UNG 和 UNH 區段定義**信封**頁面 (在**交易集設定**區段) 的單向協議屬性中**協議屬性**對話方塊**EDIFACT 後援設定**對話方塊<br /><br /> 如果定義了協議，傳送管線就會根據訊息類型 (UNH2.1)、訊息版次號碼 (UNH2.3)、指定代碼 (UNH2.5)、版本和目標命名空間來判斷 UNG 資料元素的值。 **注意：**是唯一的其他群組的群組，不是所有的這些值可以是另一個群組相同。|  
  
### <a name="applying-transaction-set-header-and-trailer-segments"></a>套用交易集標頭和結尾區段  
 將序列化為外寄 EDI 交換的 XML 交易集，應該有交易集標頭和結尾。 不過，如果訊息沒有交易集標頭和結尾，「EDI 組合器」也會處理此訊息。 對 XML 交易集而言，X12 和 EDIFACT 結構描述中的交易集標頭和結尾都是選擇性項目。 如果交易沒有標頭或結尾，EDISend 或 AS2EDISend 傳送管線中的「EDI 組合器」就會將交易集標頭和結尾值加入至此交易。 這些值是根據對應或計算而定。 EDI 組合器會針對交換 XML (保留批次)、批次交易集 XML 和交易集 XML 執行這項作業。  
  
 如果對應造成驗證錯誤，XML 交易集或交換 XML 就會遭到擱置，並在事件檢視器中顯示適當錯誤，例如無效的長度或資料型別或無效的「控管單位代碼」。  
  
####  <a name="BKMK_X12"></a>X12 交易集標頭和結尾區段  
 對於沒有標頭和結尾區段的 X12 編碼交易集，EDI 組合器會將 ST 和 SE 區段設定如下：  
  
|頁首/頁尾區段|值|  
|----------------------------|-----------|  
|ST01 (交易集識別項代碼)|對應到內送 XML 交易集中 RootNode 名稱的最後三個字元。 例如，"X12_00401_855" 中的 "855"。 如果 HIPAA 主張有 TS 識別項代碼 837P、837D 或 837I，則會使用 "837"。|  
|ST02 (交易集控制編號)|值`EdiOverride.ST02`(如果`EdiOveride.OverrideEdiHeader`為 true，) 或對應至值**交易集控制編號 (ST02)**中**本機主機設定**頁面 (在**交換設定**) 的單向協議索引標籤中**協議屬性** 對話方塊。<br /><br /> 不論設定為何套用新的或遞增的控制編號**套用新識別碼**屬性。|  
|ST03 (版本識別項)|對應至內送交易集中的 ST03 值。 例如，5010 HIPAA 820 文件 (薪資扣除額) 的此值即為 “005010X218”。 系統會根據用以驗證交易集的結構描述來驗證 ST03。 **注意：** ST03 是強制性的所有 HIPAA 5010 版交易 835 除外。|  
|SE01 (已包括區段的數目)|設定為交易集中的區段總數，包括 ST 和 SE 區段。|  
|SE02 (交易集控制編號)|對應到交易集中的 ST02 值。|  
  
 交易集標頭中的其他資料元素 (例如 ST03) 是選擇項，因此不是已產生區段中的值。  
  
####  <a name="BKMK_EDIFACT"></a>EDIFACT 交易集標頭和結尾區段  
 對於沒有標頭和結尾區段的 EDIFACT 編碼交易集，EDI 組合器會將 UNH 和 UNT 區段設定如下：  
  
|頁首/頁尾區段|值|  
|----------------------------|-----------|  
|UNH01 (訊息參考控制編號)|值`EdiOverride.UNH1`(如果`EdiOverride.OverrideEdiHeader`為 true，) 或對應至值**參考編號 (UNH1)**中**本機主機設定**頁面 (在**交換設定**)在單向協議索引標籤的**協議屬性** 對話方塊。 不論設定為何套用新的或遞增的控制編號**套用新識別碼**屬性。|  
|UNH2.1 (訊息類型)|對應到內送 XML 交易集中 RootNode 名稱的最後六個字元。 例如，"EFACT_D96A_INVOIC" 中的 "INVOIC"。|  
|UNH2.2 (訊息版本號碼)|對應到內送 XML 交易集中 RootNode 名稱的第七個字元。 例如，"EFACT_D96A_INVOIC" 中的 "D"。|  
|UNH2.3 (訊息版次號碼)|對應到內送 XML 交易集中 RootNode 名稱的第八、第九和第十個字元。 例如，"EFACT_D96A_INVOIC" 中的 "96A"。|  
|UNH2.4 (控管單位代碼)|永遠對應到字串 "UN"。|  
|UNT01 (包括的區段數目)|設定為交易集中的區段總數，包括 UNH 和 UNT 區段。|  
|UNT02 (訊息參考控制編號)|對應至值**參考編號 (UNH1)**中**本機主機設定**頁面 (在**交換設定**) 的單向協議索引標籤中**協議屬性**對話方塊|  
  
 UNH 交易集標頭中的其他資料元素 (例如 UNH3 到 UNH6) 是選擇項，因此不是已產生區段中的值。 如果上述其中任何一個欄位是必要項，您必須將它們設定為內送 XML 交易集中的值。  
  
### <a name="additional-processing-on-envelope-of-an-outgoing-message"></a>外寄訊息信封的其他處理  
 EDI 傳送管線會在外寄訊息信封上執行下列處理：  
  
#### <a name="control-numbers"></a>控制編號  
 EDI 傳送管線會在每個外寄交換的信封區段中，輸入交換控制編號、群組控制編號和交易集控制 (或參考) 編號。 下表說明這些編號：  
  
|控制編號|X12 欄位|EDIFACT 欄位|  
|--------------------|---------------|-------------------|  
|交換控制編號|ISA13|UNB5|  
|群組控制編號|GS6|UNG5|  
|交易集控制編號 (X12)<br /><br /> 交易集參考編號 (EDIFACT)|ST2|UNH1|  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將根據您在輸入的值的範圍上傳送的下一個交換的交換控制編號**交換控制編號 (ISA13)**屬性**本機主機設定**頁面 （在下**交換設定**) 的單向協議索引標籤中**協議屬性** 對話方塊。 它會將每個後續交換的此編號遞增，直到達到最大值為止。  
  
 如果使用 EdiOverride 內容屬性指定交換控制編號，指定的值將會用於此交換，且不會影響到協議中所指定的交換控制編號。  
  
> [!NOTE]
>  在 EDIFACT 中的群組控制編號才會遞增**套用 UNG 區段**屬性**信封**已選取 EDIFACT 協議屬性 頁面。 第二個欄位 (參考編號) 會遞增；前置詞和尾碼欄位不會遞增。 如果交易集控制編號才會遞增**套用新識別碼**選取屬性。  
  
> [!NOTE]
>  在保留的批次交換中，您可以使用「訊息豐富」範例，建立自訂的交換控制編號。 如需詳細資訊，請參閱[訊息豐富 」 範例 （BizTalk Server 範例）](../core/message-enrichment-sample-biztalk-server-sample.md)。  
  
 如果未定義協議，傳送管線就會從後援協議中的相同頁面擷取編號。 傳送管線會儲存上次使用的控制編號，然後針對下一個交換、群組和交易集輸入遞增的編號。  
  
> [!NOTE]
>  如果有任何控制編號達到所指定範圍的最大值，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 就會引發錯誤，並擱置交換。 您可以手動重設控制編號，或設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]自動重設為較低的限制，在**本機主機設定**頁面**協議屬性**對話方塊中，這兩個 x12 和EDIFACT 訊息。  
  
> [!NOTE]
>  控制編號儲存在 BizTalk MessageBox 資料庫的 dbo.EdiSequenceNumbers 資料表中。 您應該視情況清除資料表中的控制編號或是封存控制編號，以便管理這份資料庫資料表。  
  
 在 EDIFACT 中，控制編號由英數字元值所組成。 下列為支援的格式：  
  
-   Numbers (例如 "1")  
  
-   PrefixNumbersSuffix (例如 "WA1A")  
  
-   PrefixNumbers (例如 "AA1")  
  
-   NumbersSuffix (例如 "1AA")  
  
 使用這些格式時，數字字元可從 "0" 到 "9"，而前置詞和尾碼字元可以是數字以外的任何字元。 只有數字會一直遞增，直到達到最大值。  
  
#### <a name="count-of-segments"></a>區段計數  
 對於交換中的每個交易集，EDI 傳送管線會確認交易集中的區段計數，表示方式為 SE01 資料元素 (若是 X12) 和 UNT01 資料元素 (若是 EDIFACT)。 如果適當資料元素的值與實際數目不符，則傳送管線會更新此計數，以反映實際的區段數目。 交易集不會因錯誤計數而遭到拒絕。 計數的更新會記錄到事件檢視器的警告中。 這項更新並不會套用到保留批次的處理作業。  
  
## <a name="additional-steps-in-serializing-an-edi-interchange"></a>序列化 EDI 交換的其他步驟  
 EDI 傳送管線也會在序列化期間執行下列步驟。  
  
### <a name="serializing-the-release-indicator"></a>序列化釋放指示符號  
 在序列化 EDIFACT 訊息期間，EDI 傳送管線會在 EDI 交換中插入任何必要的釋放指示符號。 這時是假設路由至傳送管線的中繼 XML 不包含逸出的資料。 例如，如果路由至傳送管線的 XML 資料中出現釋放指示符號，該傳送管線就會在現有釋放指示符號前面加入另一個釋放指示符號，以使其逸出。  
  
 因此 EDI 驗證不會包括該釋放指示符號。 EDI 傳送管線計算長度限制時，不會計入該釋放指示符號。  
  
### <a name="adding-trailing-zeroes-to-meet-implied-decimal-requirements"></a>加入尾端零以符合隱含的十進位需求  
 如果 EDI 組合器遇到小數點後面有不足位數的數字，它會在小數點後加入尾端零，以符合隱含的十進位需求。 例如，如果 EDI 組合器在數字格式應該是 N2 時遇到數字 "4.5"，這時組合器會將此數字變更為 "4.50"。  
  
### <a name="replacing-separators-in-payload-data"></a>取代內容資料中的分隔符號  
 如果輸出訊息內的資料中有些字元同時也被設定做為資料、區段或元件的分隔符號，EDI 傳送管線可以取代這些字元。 比方說，如果訊息包含值為 「 測試 * 資料 」 和資料元素分隔符號設定為\*'，這可能會遇到剖析問題造成接收端系統。  
  
 EDI 傳送管線可以設定來取代此字元，藉由啟用**取代內容中的分隔符號**屬性並指定取代字元。 這個屬性位於**字元集和分隔符號**頁面的單向協議索引標籤中**協議屬性** 對話方塊。  
  
### <a name="transform-hipaa-records-based-on-trigger-fields"></a>根據 觸發程序欄位轉換 HIPAA 記錄  
 如果輸出文件是 HIPAA 交易集，EDI 組合器會將轉換任何相符的一般 EDI 區段將包含觸發程序欄位的唯一 XML 記錄 (請參閱[HIPAA 結構描述的觸發程序欄位註解](../core/hipaa-schema-trigger-field-annotations.md))。 這是藉由刪除 XML 記錄名稱 “_” 字元後的尾碼來達成。  
  
 例如，<N1_PayerIdentification_TS835W1_1000A> 與 <N1_PayeeIdentification_TS835W1_1000B> 兩個項目都會變成 N1 區段。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)