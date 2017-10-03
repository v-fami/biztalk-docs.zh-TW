---
title: "EDI 內容屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a408af-daf5-4e9e-afb3-9fd1795e8c16
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc98b010edfbc92a07af5625af16a3af77674247
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-context-properties"></a>EDI 內容屬性
EDI 全域屬性結構描述中的訊息內容屬性都是公開屬性，因此您可以在像是訊息路由等作業中使用這些內容屬性。 這些內容屬性都是定義在 Microsoft.BizTalk.Edi.BaseArtifacts 組件的 PropertySchema.xsd 結構描述中。 屬性的命名空間是 `http://schemas.microsoft.com/ Edi/PropertySchema`。 如果升級，這些訊息內容屬性就可做為 Edi。\<*屬性名稱*> 中**篩選**頁面**傳送埠屬性 對話方塊** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。


## <a name="context-properties-list"></a>內容屬性清單  
 只要在協調流程專案中加入 Microsoft.BizTalk.Edi.BaseArtifacts 組件的參考，這些 EDI 內容屬性也可以用於協調流程。
  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|AK901|string|表示通知中 AK1 區段內所識別的功能群組為已接受或已拒絕 (僅限 X12 997 通知)。|  
|AttachmentId|字串|郵件附件的識別碼。|  
|AgreementID|int|寫入由 EDI 接收管線。 指定輸入的訊息會解析協議識別碼。 後援協議的此值為 0。|  
|AgreementName|字串|寫入由 EDI 接收管線。 指定的輸入的訊息會解析協議的名稱。 這個值會後援協議**BTSGuestParty**。|  
|AgreementNameForSend|字串|EDI 傳送管線用於輸出文件的協議解析。|  
|AgreementPartIDForSend|int|EDI 傳送管線用於輸出文件的協議解析。 這個值會寫入由 「 批次處理協調流程。|  
|AgreementPartIDOnReceive|int|寫入由 EDI 接收管線。 指定輸入的訊息會解析協議的單向協議的識別碼。 後援協議的此值為 0。|  
|BatchElementValidationFailure|boolean|表示當批次項目未通過驗證時，批次處理系統升級錯誤的指示。|  
|BatchEncodingType|string|編碼，BizTalk Server 類型，必須用來編碼外寄批次的交換。|  
|批次識別碼|int|處理時要使用這份文件，如果文件只符合一個批次篩選條件的批次組態批次識別碼。|  
|Batchid|字串|如果文件符合多個批次篩選條件，設定批次識別碼相符的批次篩選條件的清單。|  
|BatchingError|string|當批次處理系統擱置批次項目時，針對該批次處理系統所升級錯誤的說明。|  
|BatchName|字串|要處理這份文件時使用的批次組態的名稱。|  
|CodePage|string|要用來驗證交換的字碼頁。|  
|CONTRL_UCI4|string|CONTRL 通知的「動作代碼」欄位，表示交換已被接受 (值 "8")，或交換已因 UNA 或 UNB 區段錯誤而被拒絕 (值 "4") (僅限 EDIFACT CONTRL 通知)。|  
|DestinationPartyID (中已被取代[!INCLUDE[prague](../includes/prague-md.md)])|int|訊息應傳送目標之目的合作對象的識別碼。|  
|DestinationPartyName (中已被取代[!INCLUDE[prague](../includes/prague-md.md)])|string|訊息應傳送目標之目的合作對象的名稱。|  
|DestinationPartyReceiver<br />識別碼|string|訊息應傳送目標之目的合作對象的識別碼。 這個屬性可由自訂元件升級，以啟用傳送管線中的合作對象解析。|  
|DestinationPartyReceiver<br />Qualifier|string|訊息應傳送目標之目的合作對象的辨識符號。 這個屬性可由自訂元件升級，以啟用傳送管線中的合作對象解析。|  
|DestinationPartySender<br />識別碼|string|傳送訊息至目的合作對象之合作對象的識別碼。 這個屬性可由自訂元件升級，以啟用傳送管線中的合作對象解析。|  
|DestinationPartySender<br />Qualifier|string|傳送訊息至目的合作對象之合作對象的辨識符號。 這個屬性可由自訂元件升級，以啟用傳送管線中的合作對象解析。|  
|EncodingType|short|必須用來編碼外寄訊息的編碼，BizTalk Server 類型。|  
|ErrorDescription|string|對於擱置的訊息，其中會包含錯誤訊息的複本 (類似 EventViewer 中的訊息)。|  
|GS_Segment|string|完整的 GS (功能群組) 區段 (X12)<br /><br /> EDI 接收管線會在交換分割為交易集時 (而非保留交換時)，將此屬性寫入內容中。|  
|GS01|string|功能識別項代碼 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|GS02|string|應用程式傳送者代碼 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|GS03|string|應用程式接收者代碼 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|GS07|string|負責單位 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|GS08|string|版本/版次/產業識別項代碼 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|ISA_Segment|string|完整的 ISA (交換控制標頭) 區段 (X12)<br /><br /> BizTalk Server 會在交換分割為多個交易集時 (而非保留交換時)，將此屬性寫入內容中。<br /><br /> 這個屬性包含可能導致資訊洩漏的安全性/授權資訊 (ISA2 欄位包含授權資訊，而 ISA4 欄位包含安全性資訊)。 您可以使用 遮罩安全性/授權/密碼資訊屬性 (在**驗證和通知產生**頁面) 以"#"字元取代 ISA2 和 ISA4 欄位中的每個字元。 這是單向的程序:"#"字元無法轉換成實際的字元。<br /><br /> EDI 接收管線會在交換分割為交易集時 (而非保留交換時)，將此屬性寫入內容中。|  
|ISA05|string|交換傳送者辨識符號 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|ISA06|string|交換傳送者識別碼 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|ISA07|string|交換接收者辨識符號 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|ISA08|string|交換接收者識別碼 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|ISA15|string|使用狀況指示符號 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|IsResendControlMessage|int|AS2 引擎用來表示，就應該重新傳輸 AS2 訊息傳送，因為沒有設定的時間內收到的 MDN 回應。|  
|IsSystemGeneratedACK|boolean|表示訊息是系統產生的通知 (X12 TA1 或 997，或是 EDIFACT CONTRL)。 可以設定為 True 或 False。<br /><br /> 這是可做為 EDI 訊息內容屬性。在 IsSystemGeneratedACK**篩選**頁面**傳送埠屬性** 對話方塊。|  
|ReceiverPartyName|字串|寫入由 EDI 接收管線。 指定的訊息會解析協議中所提供的目的地夥伴的名稱。 這個值會後援協議**RECEIVE-PARTNER**。|  
|ReceiverPartyNameForSend|字串|EDI 傳送管線用於輸出文件的協議解析。|  
|ReuseEnvelope|boolean|指示交換為保留或是分割狀態。 如果交換是保留狀態，BizTalk Server 就會在處理要傳送的交換時重複使用該信封。|  
|SenderPartyName|字串|寫入由 EDI 接收管線。 指定的輸入的訊息會解析協議中所提供的來源協力電腦的名稱。 這個值會是後援協議**BTS-SENDER**。|  
|SenderPartyNameForSend|字串|EDI 傳送管線用於輸出文件的協議解析。|  
|ST01|string|交易集識別項代碼 (X12)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|ST03|string|版本/版次/產業識別項代碼 (X12)<br /><br /> 您可以撰寫和升級這個屬性的內容，並將它用於訊息路由。|  
|TA1_TA104|string|TA104 通知的「引擎行為」欄位，表示已接受交換 (值 "A")、已接受交換但發生錯誤 (值 "E")，或已拒絕/已擱置交換 (值 "R") (僅限 X12 TA1 通知)。|  
|ToBeBatched|boolean|指示訊息是否應與其他訊息一起由批次處理協調流程批次處理。<br /><br /> 在批次處理交換之後，批次處理協調流程會將此屬性設定為 False。|  
|ToBeRouted|boolean|指示訊息應該由路由協調流程收取，而該協調流程會依照批次項目的訂閱數來建立該批次項目相同數目的複本，然後將複本路由傳送至 MessageBox。|  
|UNA_Segment|string|完整的 UNA (字串服務建議) 區段 (EDIFACT)<br /><br /> EDI 接收管線會在交換分割為交易集時 (而非保留交換時)，將此屬性寫入內容中。|  
|UNB_Segment|string|完整的 UNB (交換控制標頭) 區段 (EDIFACT)<br /><br /> EDI 接收管線會在交換分割為交易集時 (而非保留交換時)，將此屬性寫入內容中。<br /><br /> 這個屬性包含可能導致資訊洩漏的安全性/授權資訊 (UNB6.1 和 UNB6.2)。 您可以使用 [遮罩安全性/授權/密碼資訊] 屬性，以"#"字元取代 UNB6.1 和 UNB6.2 欄位中的值。 請注意，"#"字元無法轉換成實際的字元。|  
|UNB11|string|使用狀況指示符號 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNB2_1|string|交換傳送者識別碼 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNB2_2|string|交換傳送者識別碼辨識符號 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNB2_3|string|反向路由的位址 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNB3_1|string|交換收件者識別碼 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNB3_2|string|交換收件者識別碼辨識符號 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNG_Segment|string|完整的 UNG (功能群組) 區段 (X12)<br /><br /> EDI 接收管線會在交換分割為交易集時 (而非保留交換時)，將此屬性寫入內容中。|  
|UNG1|string|功能群組識別碼 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNG2_1|string|應用程式傳送者識別碼 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNG3_1|string|應用程式收件者識別碼 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNH2_1|string|訊息類型 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNH2_2|string|訊息版本號碼 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
|UNH2_3|string|訊息版次號碼 (EDIFACT)<br /><br /> EDI 接收管線會將這個屬性升級到內容中 (如果該交換不是保留的批次交換)。|  
  
## <a name="extracting-individual-fields-from-the-segment-context-properties"></a>從區段內容屬性擷取個別的欄位  
 有些屬性不會被 EDI 接收管線當做個別的屬性寫入或升級到訊息內容中，而只是做為區段字串的一部分。 這是基於效能的考量，因為屬性升級對效能會有影響。 例如，ISA 區段中的 ISA5、ISA6、ISA7、ISA8 和 ISA15 欄位會被接收管線當做個別的屬性來升級，但其餘 ISA 欄位只會做為 ISA_Segment 屬性的一部分寫入訊息內容中。 這些屬性會寫入或升級時，才**ReuseEnvelope**未設定為 True，表示不保留已接收的批次的交換。  
  
 如果您需要的其中一個區段 （ISA、 GS、 UNB、 UNG 或 UNA） 寫入至訊息內容中，個別的欄位，但該個別欄位不會寫入訊息內容根據預設，您必須撰寫自訂元件，以寫入訊息內容。 這個自訂元件必須剖析區段欄位，並將個別的欄位寫入到訊息內容。  
  
 「訊息豐富」範例示範如何使用剖析器，從區段中擷取個別的欄位並將其寫入至內容。 這個範例包含在\<磁碟機 >: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\SDK\Samples\EDI\MessageEnrichment。 如需詳細資訊，請參閱[訊息豐富 」 範例 （BizTalk Server 範例）](../core/message-enrichment-sample-biztalk-server-sample.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md)