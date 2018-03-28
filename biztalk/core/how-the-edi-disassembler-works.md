---
title: EDI 解譯器如何運作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8da91ba4-e1c9-4e6b-bbd1-fe71ea880118
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4edf1353a9f06103205e1e6e4296c2aa77e74dc6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-the-edi-disassembler-works"></a>EDI 解譯器如何運作
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會在 EDI 接收管線 (`Microsoft.BizTalk.DefaultPipelines.EDIReceivePipeline`) 中執行對所收到 EDI 編碼交換的大部分處理。 此管線包含 EDI 解譯器管線元件，可執行下列處理：  
  
-   將單一訊息中的多個交換分割為不同的交換 (若接收位置的 "DetectMID" 管線屬性設定為 True)。 EDI 解譯器執行此工作的方式是搜尋交換控制標頭 (ISA、UNA 或 UNB)，即使已經找到交換控制結尾 (IEA 或 UNZ) 也一樣。  
  
-   驗證信封。  
  
-   解譯交換。  
  
-   處理 HIPAA 交換的觸發程序欄位。  
  
-   適用時，驗證 EDI 和夥伴特定的屬性。 這包含 EDI 結構描述驗證、X-12 編碼訊息的欄位交互驗證 (若已設定)、EDI 結構化驗證，以及擴充的結構描述驗證 (若結構描述已自訂的節點具有非 EDI 資料型別)。 如需詳細資訊，請參閱[驗證的接收 EDI 訊息](../core/validation-of-received-edi-messages.md)。  
  
-   驗證交換、 群組和交易集控制編號並未重複項目，如果在啟用檢查 **驗證** 頁面 (在 **交換設定**) 之雙向協議索引標籤的 **協議屬性** 對話方塊。 針對先前已接收的交換檢查交換控制編號。 針對交換內其他的群組控制編號檢查群組控制編號。 針對該群組內其他的交易集控制編號檢查交易集控制編號。 若發現重複，狀態報告會指出存在重複記錄。  
  
-   為各交易集產生 XML 文件。 在每個 XML 檔案上，升級 BTS.MessageType 的內容屬性，將它設定為含有命名空間的結構描述名稱。  
  
-   將整個交換轉換為 XML，如果 **輸入批次處理選項** 屬性設定為兩個的其中一個 **保留交換** 值。 這個屬性可以設定從 **本機主機設定** 頁面下 **交換設定** 雙向協議索引標籤的 **協議屬性** 對話方塊。 接收管線會升級 ReuseEnvelope 屬性，以識別保留的交換。  
  
-   產生「技術」和/或「功能」通知 (若已設定)。 這可包含批次處理通知 (若已設定)。 升級 BTS 的內容屬性。訊息類型，將它設定等於中的控制結構描述http://schemas.microsoft.com/EDI/ \<X12 或 EDIFACT\>命名空間 （例如，997 通知就是 X12_997_Root）。 另外，升級 EDI.DestinationPartyName 內容屬性，可確保會挑選要傳送的通知。 如需詳細資訊，請參閱[傳送 EDI 通知](../core/sending-an-edi-acknowledgment.md)。  
  
-   適用時，執行 HIPAA 276/277 (僅 5010 版) 834、835 (僅 4010 版) 和 837 文件分割。  
  
-   升級或寫入屬性至訊息內容 (參閱下一節)。  
  
## <a name="promoting-or-writing-properties-to-the-context"></a>升級或寫入屬性至內容  
 EDI 解譯器處理所接收的訊息時，會升級或寫入下列屬性至訊息內容：  
  
-   X12 編碼未批次訊息中，會升級信封的下列屬性︰ ISA06、 ISA08、 ISA15;GS01，GS02，GS03，GS08;ST03 和 ST01。  
  
    > [!NOTE]
    >  內送 HIPAA 837 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]支援三個 HIPAA 837 結構描述： claim-dental_837d、 宣告 Institutional_837I 和宣告 Professional_837P。 每個選項的 ST01 是"837"。下列三個結構描述版本 5010 中的 GS08 有不同的值:"005010X223A1"837I、 837d，如"005010X224A1"和"005010 X 222"837。 結構描述有的 GS08 在 4010 版中不同的值:"004010X096A1"837I、 837d，如"004010X097A1"為"004010X098A1"837。  
  
-   EDIFACT 編碼未批次訊息中，會升級信封的下列屬性︰ UNB2.1，UNB2.3，UNB3.1，UNB11;UNG1，UNG2.1，UNG3.1;UNH2.1，UNH2.2，UNH2.3。  
  
-   若批次處理的交換已分割，會將 ISA_Segment 和 GS_Segment 寫入至 X12 編碼訊息的內容，或將 UNA_Segment、UNB_Segment 和 UNG_Segment 寫入至 EDIFACT 編碼訊息的內容。  
  
    > [!NOTE]
    >  以上區段會寫入內容。 他們不會升級至內容。 不過您可以使用「訊息豐富」範例，將這些區段附加至交易集。 您也可以擷取附加範例的程式碼，再將它新增至自訂管線元件。 如需詳細資訊，請參閱[訊息豐富 」 範例 （BizTalk Server 範例）](../core/message-enrichment-sample-biztalk-server-sample.md)。  
  
    > [!NOTE]
    >  ISA_Segment 已升級包含安全性/授權資訊 (ISA02「授權資訊」和 ISA04「安全性資訊」) 的屬性，可能導致資訊洩漏。 您可以使用 **遮罩內容屬性中的安全性/授權/密碼資訊屬性** (在 **本機主機設定** 頁面 **交換設定** 雙向協議屬性) 以 '#' 字元取代 ISA02 和 ISA04 欄位中的每個字元。 這是單向的程序: '#' 字元無法轉換成實際的字元。  
  
-   若為 X12 和 EDIFACT 編碼的訊息，請升級 ReuseEnvelope，這會指出批次處理的交換是否已分割或保留。  
  
-   若已保留批次處理的交換，會升級下列屬性：  
  
    -   InboundTransportatLocation  
  
    -   InboundTransportType  
  
    -   ISA05  
  
    -   ISA07  
  
    -   ISA06  
  
    -   ISA08  
  
    -   ISA15  
  
    -   LastInterchangeMessage = {True &#124;False}  
  
    -   MessageType  
  
    -   ReceivePortID  
  
    -   ReceivePortName  
  
    -   ReuseEnvelope  
  
## <a name="parsing-the-envelope"></a>剖析信封  
 EDI 接收管線會使用標頭控制結構描述剖析已接收 EDI 訊息的信封，以及使用 EDI 文件結構描述剖析交換內的交易集/訊息。  
  
 若透過 HTTP/HTTPS 傳輸接收到 EDIINT/AS2 編碼的訊息，EDI 解譯器會檢查 BTS.MessageDestination 內容屬性。 若該屬性設定為 SuspendQueue，表示 AS2 處理中發生錯誤且已擱置訊息，EDI 解譯器會扮演通過管線元件的角色，並擱置傳送至 MessageBox 的訊息。  
  
 剖析 EDIFACT 交換時，EDI 接收管線會移除用來逸出字元的釋放指示符號。 EDI 驗證並未包含釋放指示符號。 EDI 接收管線計算長度限制時，並未包含釋放指示符號。  
  
 **字元集**  
  
 若為 X12 交換，[管線元件屬性] 會決定 EDI 解譯器處理交換時將使用的字元集。 可能是「基本」、「擴充的」或 UTF8/Unicode。 預設值是 UTF8。若為 EDIFACT 交換，UNB1.1 欄位會決定字元集。  
  
 **動態分隔符號探索**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收 EDI 交換時，沒有任何協議屬性會指示交換內的分隔符號應該是什麼。 反而是 EDI 解譯器會在執行階段探索分隔符號是哪些 (針對 X12 或 EDIFACT)。  
  
 若為 X12 訊息，EDI 解譯器會使用交換內的下列字元：  
  
|分隔符號|字元|  
|---------------|---------------|  
|資料項目分隔符號|ISA 第 4 個字元|  
|元件元素分隔符號|ISA16|  
|區段分隔符號|ISA 第 106 個字元|  
|區段結束字元尾碼|ISA 區段與 GS 區段之間的字元<br /><br /> **值︰** 無、 CR、 LF 或 CRLF **附註︰**  分隔符號可以採取上述的值。|  
|重複分隔符號或標準識別項<br /><br /> (根據上的 「 ISA11 使用狀況 協議屬性 **信封** 頁面的雙向協議索引標籤)|ISA11|  
  
 若為 EDIFACT 交換，EDI 解譯器會檢查定義交換內之分隔符號的 UNA 區段。 若交換沒有 UNA 區段 (選擇性)，解譯器會使用管線元件屬性內定義的預設值。  
  
|分隔符號|UNA 的字元|  
|---------------|----------------------|  
|元件元素分隔符號|第 4 個|  
|資料項目分隔符號|第 5 個|  
|小數點標記|第 6 個|  
|釋放字元|第 7 個|  
|重複字元|第 8 個|  
|區段分隔符號|第 9 個|  
|區段分隔符號尾碼|UNA 區段與 UNB 區段之間的字元<br /><br /> **值︰** 無、 CR、 LF 或 CRLF **附註︰**  分隔符號可以採取上述的值。|  
  
 UNA 字串是選擇性的。 若出現，會定義檔案的所有分隔符號。 若沒出現，EDI 解譯器會使用 EfactDelimiters 管線元件屬性決定分隔符號。 如需詳細資訊，請參閱[設定 EDI 管線屬性](../core/configuring-edi-pipeline-properties.md)。  
  
 **公佈錯誤**  
  
 若 EDI 解譯器發生 EDI 處理錯誤，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將下列兩個錯誤公佈到「事件檢視器」(若這類公佈已啟用)：  
  
-   來源 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在擱置訊息時記錄的錯誤。 這是和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理有關的必須公佈錯誤。  
  
-   由來源 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 所記錄的交易集內錯誤報告問題。 這個錯誤是 EDI 特有的。  
  
## <a name="using-agreement-properties"></a>使用協議屬性  
 EDI 解譯器若可識別協議，將會使用協議屬性 (請參閱[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md))。 如果找不到符合的協議或對應的值不能使用後援協議中，EDI 解譯器 」 中設定 **屬性** 將使用 Visual Studio 的視窗。 不過，將不會發生此後援如果需要驗證在接收埠屬性 (如果有任一 **驗證失敗時捨棄訊息** 或 **驗證失敗時保留訊息** 已選取)。 這時就必須設定協議，否則交換會遭擱置。  
  
 若要讓 EDI 解譯器使用協議屬性，需已設定下列協議屬性：  
  
|屬性|協議屬性頁面|  
|--------------|-------------------------------|  
|重複分隔符號|**信封** 頁面 (在 **交換設定**) 中雙向協議索引標籤|  
|執行 EDI 資料型別驗證|**驗證** 頁面下 **交易集設定** 在雙向協議索引標籤 （適用於 X12 和 EDIFACT 協議）|  
|擴充驗證|**驗證** 頁面下 **交易集設定** 在雙向協議索引標籤 （適用於 X12 和 EDIFACT 協議）|  
|允許前置和尾端零及空格|**驗證** 頁面下 **交易集設定** 在雙向協議索引標籤 （適用於 X12 和 EDIFACT 協議）|  
|如果允許尾端分隔符號，則建立空的 XML 標記|**本機主機設定** 頁面下 **交易集設定** 在雙向協議索引標籤 （適用於 X12 和 EDIFACT 協議）|  
|輸入批次處理選項|**本機主機設定** 頁面 (在 **交換設定**) 在雙向協議索引標籤 （適用於 X12 和 EDIFACT 協議）|  
|預設 EDIFACT 分隔符號|-|  
|遮罩安全性/授權/密碼資訊|**本機主機設定** 頁面 (在 **交換設定**) 在雙向協議索引標籤 （適用於 X12 和 EDIFACT 協議）|  
|將隱含的小數格式 Nn 轉換為 10 進制數值|**本機主機設定** 頁面下 **交易集設定** 雙向協議索引標籤中 (針對 X12 協議)|  
|將通知的路由設定為要求回應接收埠上的傳送管線|**本機主機設定** 頁面 (**接收者的設定** 區段) 下 **交換設定** 在雙向協議索引標籤 （適用於 X12 和 EDIFACT 協議）|  
|X12 字元集|X12 交換信封產生 **附註︰**  這項設定僅用於驗證協議屬性所輸入的值。 管線屬性內會選取用來進行執行階段處理的 X12 字元集。 如需詳細資訊，請參閱[EDI 字元集](../core/edi-character-sets.md)。|  
  
## <a name="using-hipaa-trigger-fields"></a>使用 HIPAA 觸發程序欄位  
 EDI 區段通常包含修飾區段意義的辨識符號。 例如，N1 區段可能包含 “BT” 辨識元素以表示「帳單收件人」，或可能包含 “ST” 辨識元素以表示「出貨收件人」。 商務邏輯決定如何解譯這些欄位通常會維持和解譯器會將 N1 區段的所有執行個體解析成相同的 XML 記錄名稱。不過，BizTalk Server 所隨附的 HIPAA 結構描述含有註解，可讓 EDI 解譯器來建立根據存在的辨識值的唯一 XML 記錄 (請參閱[HIPAA 結構描述的觸發程序欄位註解](../core/hipaa-schema-trigger-field-annotations.md))。  
  
 EDI 解譯器在收到 HIPAA 交易集時，若遇到含有觸發程序欄位的區段，便會使用觸發程序資訊來產生這個區段和觸發程序組合特有的 XML 記錄。  
  
 下表顯示 N1 區段如何根據 N101 的值轉譯為 XML 記錄：  
  
|N1 區段|結果產生的 XML 資料|  
|----------------|------------------------|  
|N1 * PR\*Contoso\*1763\*0000000 ~|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|N1 * PE\*Fabrikam\*FI\*9999999 ~|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)