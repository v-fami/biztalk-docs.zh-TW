---
title: 已知問題與 EDI 傳送處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1325dcd9-5dbb-48bb-b5a3-1502d1424d4e
caps.latest.revision: 31
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbebfa213aa125252a8c58e246df376e2a36527d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263310"
---
# <a name="known-issues-with-edi-send-processing"></a>EDI 傳送處理的已知問題
本主題說明處理 EDI 傳送管線的已知問題。  
  
## <a name="x12-implied-decimal-point-causes-length-validation-to-fail"></a>X12 隱含的小數點導致長度驗證失敗  
 **徵兆**  
  
 當 EDI 傳送管線在外寄的 EDI 交換中，將中繼 XML 中的 10 進制數值轉換成 Nn 格式的數字時，XML 交換的長度驗證程序失敗。  
  
 **可能的原因**  
  
 在序列化 X12 編碼的 EDI 交換時，EDI 傳送管線永遠都會將 10 進制數值轉換成具有隱含小數點的 Nn 格式數字。 例如，如果中繼 XML 檔案中有個值為 12.34，而其數字型別指定為 N2 時，EDI 傳送管線便會在 EDI 交換中將它轉換成 1234。 10 進制數值的長度將比 Nn 格式的數字大一。 如果 Nn 格式數字的長度是最大值，中繼 XML 中的 10 進制數值 XML 長度驗證可能會失敗。  
  
 這個問題只有在 X12 編碼的交換中才會發生。  
  
 **解決方式**  
  
 在 XML 數字的最大長度值加上 1 的值。  
  
## <a name="control-numbers-may-need-to-be-reset-archived-or-purged"></a>控制編號可能必須重設、封存或清除  
 如果有任何控制編號的長度已達到欄位長度限制的上限，BizTalk Server 會引發錯誤並擱置交換。 您必須重設輸入於 [EDI 屬性] 或 [EDI 全域屬性] 對話方塊中的控制編號。  
  
 控制編號儲存在 BizTalk MessageBox 資料庫的 dbo.EdiSequenceNumbers 資料表中。 您應該視情況清除資料表中的控制編號或是封存控制編號，以便管理這份資料庫資料表。  
  
 您也可以選取 啟用自動重設控制編號**重設為下限超出範圍時**EDI 屬性 對話方塊中。  
  
## <a name="the-data-element-name-in-a-context-property-name-contains-an-underscore-not-a-period"></a>內容屬性名稱中的資料元素名稱包含底線，而非句號  
 EDI 區段內資料元素的名稱包含句號，例如 UNB2.1 (UNB2 Sender 區段的識別欄位)。 不過，當 EDI 內容屬性中包含資料元素名稱時 (例如，在傳送埠的篩選運算式中)，便會將句號取代為底線。 例如，Sender Identification 資料元素是 EDI.UNB2_1，不是 EDI.UNB2.1。 這是因為內容屬性名稱不支援句號。  
  
## <a name="context-property-values-from-data-elements-must-not-contain-leading-or-trailing-spaces-in-filter-expressions"></a>資料元素中的內容屬性值在篩選運筫式中不能包含前置或尾端空格  
 如果 EDI 交換的信封中的資料元素包含前置或尾端空格，而接收管線又以該資料元素的值升級內容屬性，則接收管線將會從內容屬性中移除前置或尾端空格。 因此，使用該內容屬性建立篩選運算式時，您必須輸入不含前置或尾端空格的屬性值。 如果您的篩選運算式包含前置或尾端空格，則篩選運算式不會解析成與內容屬性相符的值，它將不會包含前置或尾端空格。  
  
## <a name="default-party-as-interchange-receiver-properties-for-preserved-interchange-will-cause-the-send-pipeline-to-fail"></a>以預設合作對象做為保留交換的交換接收者屬性將導致傳送管線失敗  
 如果 BizTalk Server 收到應該保留的批次交換 (交換因為發生錯誤而擱置)，若做為交換接收者之合作對象的屬性設定為其預設值，訂閱該交換的傳送管線將會失敗。 這些屬性，例如 ISA5 (傳送者辨識符號) 和 ISA6 (傳送者識別項)，必須設定為有效的值。 BizTalk Server 將會發佈錯誤，指出由於合作對象組態無效，因此無法序列化訊息。 這種處理方式並不正確，因為保留的交換在其標頭中具有必要的組態設定，例如傳送者辨識符號和傳送者識別項。  
  
## <a name="the-decimal-notation-in-a-message-will-be-changed-if-the-send-side-party-or-global-setting-specifies-a-different-decimal-notation"></a>如果傳送端合作對象或全域設定指定不同的小數點標記，訊息中的小數點標記將會改變  
 如果交換中使用的小數點標記與 UNA3 合作對象屬性針對外寄訊息所指定的小數點標記不同，BizTalk Server 便會在序列化交換以便傳送時，變更該交換的信封中所使用的小數點標記。 如果使用的是 UNA3 全域屬性而非 UNA3 合作對象屬性，也會發生這種情況。 例如，如果內送訊息中使用的小數點標記是句號，而決定外寄訊息小數點標記的 UNA3 合作對象屬性或 UNA3 全域屬性指定的是逗號，BizTalk Server 便會將外寄訊息中的小數點標記改成逗號。  
  
## <a name="edi-send-pipelines-cannot-be-executed-from-within-an-orchestration"></a>EDI 傳送管線無法從協調流程內部執行  
 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您通常可以執行 「 運算式 」 圖形內的傳送管線的協調流程。 不過，這並不適用於 EDISend 管線或 AS2EdiSend 管線。 這些管線必須從傳送埠內部執行。 如果您嘗試在協調流程中的「運算式」圖形中執行 EDISend 管線或 AS2EdiSend 管線，管線不會繫結至傳送埠，而且訊息也會擱置。  
  
## <a name="biztalk-edi-application-must-not-be-modified"></a>不得修改 BizTalk EDI 應用程式  
 不得修改或刪除 BizTalk EDI 應用程式內的成品。 應用程式一經修改就無法還原，取消設定和重新設定 EDI 與 AS2 的功能也不行。  
  
## <a name="using-the-default-row-in-the-functional-group-header-grid-can-result-in-a-message-type-mismatch-between-the-interchange-header-and-the-group-header"></a>在功能群組標頭格線中使用預設資料列可能會導致訊息類型不相符之間交換標頭和群組標頭  
 如果 UNH2.1 外寄 EDIFACT 編碼交換的值不符合方格中 UNG 和 UNH 區段定義頁面 針對訊息類型 UNH2.1 的值，UNG1 輸入訊息中的值可能無法對應至 UNH2.1 的值。  
  
 這可能是因為 BizTalk 會填入訊息值 UNG1 方格的預設資料列中的即使訊息沒有與 UNH2.1 項目，該預設資料列的相符項目。  
  
 如果外寄 X12 編碼交換的 ST1 的值不符合方格中 GS 和 ST 區段定義頁面 針對 ST1 的值，訊息中所輸入的 GS1 的值將會動態地決定根據 ST1 的值。  
  
## <a name="invalid-character-in-data-element"></a>無效的字元資料元素中  
 **徵兆**  
  
 傳送 EDI 交換使用 EDI 傳送管線，您可能會收到錯誤中的應用程式事件記錄檔，表示 '中資料元素 ' 有無效字元。  
  
 **可能的原因**  
  
 如果裝載資料中包含的字元也做為分隔符號，則會發生此錯誤。 比方說，如果您使用 ':' 字元為元件分隔符號，但裝載資料也包含 ':' 字元。  
  
 這個問題只有在 X12 編碼的交換中才會發生。  
  
 **解決方式**  
  
 使用**取代內容中的分隔符號**中設定**ISA 區段定義**應取代指定分隔字元是裝載資料中找到的 EDI 合作對象屬性頁面傳送的交換時，請指定取代字元。  
  
 比方說，選取**取代內容中的分隔符號**並輸入 '（& s) #124;' 字元將會取代出現分隔符號字元與裝載資料中的任何' &#124;' 字元交換時使用 EDI 傳送管線傳送。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 處理的已知的問題](../core/known-issues-with-edi-processing.md)   
 [BizTalk Server 如何傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)   
 [逐步解說 (X12)： 傳送 EDI 交換](../core/walkthrough-x12-sending-edi-interchanges.md)