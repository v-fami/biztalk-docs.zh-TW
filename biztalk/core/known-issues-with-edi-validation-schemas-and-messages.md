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
# <a name="known-issues-with-edi-validation-schemas-and-messages"></a>EDI 驗證、結構描述和訊息的已知問題
本主題描述已知的驗證問題。  
  
## <a name="message-is-suspended-with-edi-validation-turned-off"></a>訊息在 EDI 驗證關閉的情況下遭到擱置  
 **徵兆**  
  
 違反配對規則且驗證已關閉，但訊息被擱置 (預期的結果是訊息會進行序列化)。  
  
 **可能的原因**  
  
 執行欄位/區段交互驗證，即使**EDI 類型**中取消選取了屬性**驗證和通知的產生設定**節點**EDI 屬性**對話方塊。 驗證之所以執行，是因為在結構描述註解中開啟了它。  
  
 **解決方式**  
  
 關閉結構描述註解中的驗證。  
  
## <a name="the-biztalk-service-needs-to-be-restarted-after-a-schema-has-been-edited-and-redeployed"></a>BizTalk 服務在結構描述編輯和重新部署之後必須重新啟動  
 **徵兆**  
  
 BizTalk Server 在結構描述編輯和重新部署之後，未能成功處理有效訊息。  
  
 **可能的原因**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]快取逾時限制結構描述。  
  
 **解決方式**  
  
 編輯和重新部署結構描述之後，重新啟動 BizTalk Server 應用程式服務。 若有管線使用重新部署的結構描述，則裝載該管線的主控件執行個體也必須重新啟動。  
  
## <a name="processing-has-been-aborted-for-messages-of-a-single-encoding-type-for-a-single-party"></a>已中止處理單一合作對象的單一編碼類型訊息  
 **徵兆**  
  
 已中止處理單一合作對象的單一編碼類型 (例如 X12 或 EDIFACT) 的所有訊息。 處理同一合作對象的其他編碼類型訊息，或處理其他合作對象的任何訊息，則不受影響。  
  
 **可能的原因**  
  
 交換、群組或交易集控制編號的長度超過允許的長度上限。  
  
 若是 X12 訊息，控制編號的最大長度為 9 個數字。 若是 EDIFACT 訊息，控制編號的最大長度為三個欄位 14 個數字。  
  
 **解決方式**  
  
 在受影響合作對象的 [EDI 屬性] 對話方塊，重設適當屬性頁中的控制編號。 您可以編輯下列屬性頁中的控制編號：  
  
-   X12 交換控制編號：[X12] 屬性的 [ISA 區段定義] 頁面 (在 [做為交換接收者的合作對象] 節點中)  
  
-   X12 群組或交易集控制編號： [GS 和 ST 區段定義] 頁面 (在 [X12] 屬性的 [做為交換接收者的合作對象] 節點中)  
  
-   EDIFACT 交換控制編號：[UNB 區段定義] 頁面 (在[EDIFACT] 屬性的 [做為交換接收者的合作對象] 節點中)  
  
-   EDIFACT 群組或交易集控制編號：[UNG 和 UNH 區段定義] 頁面 (在[EDIFACT] 屬性的 [做為交換接收者的合作對象] 節點中)  
  
## <a name="biztalk-server-validates-with-schemas-that-have-unh-segments-with-seven-data-elements"></a>BizTalk Server 使用包含有七個資料元素之 UNH 區段的結構描述進行驗證  
 在舊版 EDIFACT 中，UNH 區段有四個資料元素，而非新版 UNH 區段的七個元素 (其中三個為選擇項)。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用內含七個元素的較新版本進行驗證。  
  
## <a name="error-messages-generated-for-multiple-cross-field-validation-rules-will-not-be-specific-to-the-rule"></a>針對多個欄位交互驗證規則所產生的錯誤訊息與規則沒有關聯  
 如果結構描述包含多個欄位交互驗證規則來驗證訊息中的資料元素，而資料元素發生錯誤，每個驗證規則會各產生一個錯誤。 但是，每個錯誤的錯誤碼和描述都相同，即錯誤與驗證規則沒有關聯。  
  
## <a name="if-edi-type-validation-is-disabled-on-receive-and-enabled-on-send-the-send-pipeline-will-not-be-able-to-serialize-the-message"></a>如果 EDI 類型驗證在接收時停用而在傳送時啟用，則傳送管線將無法序列化訊息。  
 如果您在接收端關閉 EDI 類型驗證，EDI 接收管線會從接收的 EDI 訊息產生 XML 訊息，而不管訊息有效與否。 如果 EDI 驗證在傳送端啟用，若 XML 檔案包含錯誤，EDI 傳送管線無法將 XML 重新處理成有效的 EDI 檔案，因此會產生錯誤。  
  
## <a name="edi-promoted-properties-are-only-available-if-your-application-has-a-reference-to-the-biztalk-edi-application"></a>只有在您的應用程式有 BizTalk EDI 應用程式的參考時，EDI 升級屬性才會出現  
 **徵兆**  
  
 在您嘗試用於如協調流程或傳送埠篩選條件的升級屬性清單中，EDI 命名空間底下的升級屬性未顯示出來。  
  
 **可能的原因**  
  
 您使用的 BizTalk 應用程式沒有 BizTalk EDI 應用程式的參考。 EDI 升級屬性的屬性結構描述位於 Microsoft.BizTalk.Edi.BaseArtifacts.dll 中，這個檔案包含在 BizTalk EDI 應用程式的 [資源] 資料夾中。  
  
 **解決方式**  
  
 針對您目前使用的 BizTalk 應用程式，加入 BizTalk EDI 應用程式的參考。  
  
## <a name="the-data-element-name-in-a-context-property-name-contains-an-underscore-not-a-period"></a>內容屬性名稱中的資料元素名稱包含底線，而非句號  
 EDI 區段內資料元素的名稱包含句號，例如 UNB2.1 (UNB2 Sender 區段的識別欄位)。 不過，當 EDI 內容屬性中包含資料元素名稱時，便會將句號取代為底線。 例如，Sender Identification 資料元素是 EDI.UNB2_1，不是 EDI.UNB2.1。 這是因為內容屬性名稱不支援句號。  
  
## <a name="irrelevant-string-is-appended-to-instance-validation-error-message"></a>不相關的字串附加到執行個體驗證訊息  
 每當在執行個體驗證期間收到錯誤，字串 "BEC 2004" 都會附加到錯誤訊息。 您可以忽略此字串。  
  
## <a name="edifact-schema-names-are-case-sensitive"></a>EDIFACT 結構描述名稱區分大小寫  
 EDIFACT 結構描述的結構描述名稱 (如結構描述的 root_reference 資料元素中所示) 區分大小寫。 例如，EFACT_D98B_ORDERS 和 EFACT_d98B_Orders 是兩個不同的結構描述。  
  
## <a name="invalid-edi-messages-can-be-suspended-even-if-edi-type-validation-is-disabled"></a>即使 EDI 類型驗證已停用，仍可擱置無效的 EDI 訊息  
 即使 EDI 類型驗證已停用，EDI 結構驗證仍然會執行。 未通過基本結構驗證的交換將遭擱置，即使 EDI 類型驗證已停用。  
  
## <a name="the-edi-assembler-will-serialize-an-unbatched-interchange-even-if-a-separator-character-is-used-in-an-envelope-header"></a>即使在信封標頭中使用了分隔符號，EDI 組合器仍會序列化非批次交換  
 在任何交換、群組或交易集標頭或結尾欄位的定義中，都不能使用分隔標頭和結尾欄位的分隔符號，如做為交換接收者的合作對象的定義。 如果使用分隔符號字元，則無論是在傳送端 BizTalk Server 的「EDI 組合器」中，或是在接收合作對象的解譯器中，交換在處理時都會失敗。 如果交換是輸出批次，它在「EDI 組合器」中即會失敗，因為「組合器」會針對標頭控制 (服務) 結構描述驗證信封。 如果交換不是批次，則「EDI 組合器」會進行序列化，但會在接收合作對象的解譯器中處理失敗。  
  
## <a name="mismatched-character-sets-can-result-in-suspended-interchanges"></a>不相符的字元集可能導致交換遭擱置  
 外寄交換使用的字元集應與用來建立插入交換的交易集的字元集相同。 如果不同，交換可能會遭擱置，並出現錯誤訊息，表示有無效字元。  
  
 例如，如果您使用 UNOA 字元集建立 EDIFACT 批次，但加入至批次的交易集有小寫字元，則批次處理協調流程將擱置訊息，因為 UNOA 不允許小寫字元。  
  
 另一個範例是，如果您使用「基礎」字元集設定 X12 交換的 EDI 傳送管線，但 X12 批次交換有小寫字元，原因是在做為交換接收者的合作對象的 [產生 X12 交換信封] 頁面中選取的 X12 字元集設為「擴充」或「UTF8/Unicode」，則當套用信封設定時，批次訊息將遭擱置。  
  
## <a name="using-unh25-for-schema-resolution-requires-an-update-to-the-schema"></a>使用 UNH2.5 進行結構描述解析時需要更新結構描述  
 如果您使用 UNH2.5 （關聯指定代碼） 來解析結構描述的內送 EDIFACT 交換時，您必須更新 \Program Files\Microsoft BizTalk Server 20xx\Schema 資料夾中的相關文件結構描述。 您必須將 UNH2.5 的值附加到 root_reference、display_reference 和 xs:element 名稱的現有值。 例如，如果 UNH2.5 是 "EAN008"，而您使用 EFACT_D96A_INVOIC 結構描述，就應將 root_reference、display_reference 和 xs:element 名稱設定為 "EFACT_D96A_INVOIC_EAN008"。  
  
## <a name="the-compressed-file-of-schemas-will-be-replaced-when-an-upgrade-is-performed"></a>執行升級時，會取代結構描述的壓縮檔  
 如果您將 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 升級到更新的組建，原來安裝中的 MicrosoftEdiXSDTemplates.exe 檔案會被取代為與升級相關聯的 MicrosoftEdiXSDTemplates.exe 檔案。 如果您打算繼續使用舊壓縮檔中的結構描述，除非備份舊壓縮檔，否則您在升級後將無法再存取這些壓縮檔。  
  
## <a name="if-a-group-contains-multiple-x12-transaction-sets-all-must-be-of-the-same-type"></a>如果群組包含多個 X12 交易集，所有必須是相同的型別  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援混用不同的交易集內同一個群組。 當群組包含多個交易時，ST01 值必須是相同的所有交易。  
  
## <a name="receiving-x12-interchanges-that-contain-non-ascii-delimiters-may-result-in-the-message-becoming-suspended"></a>接收 X12 包含非 ASCII 分隔符號的交換可能會導致變成擱置訊息  
 **徵兆**  
  
 當接收 X12 交換，它使用非 ASCII 分隔符號值，訊息可能會變成 「 已擱置和應用程式事件記錄檔中寫入錯誤。  
  
 **可能的原因**  
  
 如果交換不會編碼為 utf-8，則會發生這個問題。  
  
 **解決方式**  
  
 請確定任何內送 X12 交換包含非 ASCII 分隔符號會編碼為 utf-8。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 處理的已知的問題](../core/known-issues-with-edi-processing.md)   
 [EDI 傳訊](../core/edi-messaging.md)   
 [EDI 訊息驗證](../core/edi-message-validation.md)   
 [EDI 結構描述](../core/edi-schemas.md)   
 [開發 EDI 結構描述](../core/developing-edi-schemas.md)