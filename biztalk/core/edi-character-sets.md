---
title: "EDI 字元集 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57fae748-d66e-4ecf-be00-70147078ef93
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 108424cf9ef8670340e51a1c9747f42eec9cc4cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-character-sets"></a>EDI 字元集
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用字元集來驗證整個 EDI 交換。 用於 X12 編碼訊息以及 EDIFACT 或 KEDIFACT 編碼訊息的字元集會以不同方式決定。  
  
## <a name="edifact-character-set"></a>EDIFACT 字元集  
 EDIFACT 編碼交換以其字元集而言是能夠自我描述的， 所使用的是 UNB1 資料項目。 EDIFACT 要求標記名稱和分隔符號都必須是 ASCII 類型，因此您可以找出 UNB1 來為交換的其餘部分套用相關的字碼頁。  
  
 處理傳入的 EDIFACT 訊息時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]決定要使用從 UNB1 資料項目，該訊息的字元集。 交易夥伴協議中的沒有設定是必要的。  
  
 在處理外寄 EDIFACT 訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用交易夥伴協議或後援協議中設定的字元。 在中設定 UNB1 資料項目**字元集和分隔符號**頁面之雙向協議索引標籤 （如果已定義了協議） 或**字元集和分隔符號**的協議索引標籤中的頁面**EDIFACT 後援設定**對話方塊 （若未定義協議是）。 UNB1.1 是稱為「語法識別項」的必要複合資料項目。 UNB1.2 是 EDIFACT 字元集的版本。 UNB1 資料項目也用於驗證 （不時跳離欄位索引標籤上，或顯示不同的頁面） 儲存整個屬性集時，輸入交易夥伴管理使用者介面中的屬性值。  
  
 可用的字元集包括 KECA、UNOA、UNOB、UNOC、UNOD、UNOE、UNOF、UNOG、UNOH、UNOI、UNOJ、UNOK、UNOX 和 UNOY。 預設值為 [UNOB]。 這些層級的完整字元集是在「ISO 9735 EDIFACT 語法規則」中指定。  
  
> [!NOTE]
>  如果在內送或外寄交換中遇到 UNOC 字元集，「EDI 解譯器」或「EDI 組合器」會使用 Latin-1 字碼頁，而不是 UTF-8 字碼頁。 這是因為 UTF-8 不是 UNOC 的超集。 UNOC 中可接受的部分字元若當成 UTF-8 處理，會導致交換遭擱置。  
  
 某些 EDIFACT 字元集中的字元可能是雙位元組字元，而其他 EDIFACT 字元集中的字元則可能是單一位元組字元。 因此，當您根據交換中的字元數來設定批次的釋放準則時，交換中的位元組數可能會根據使用的字元集而有所不同。  
  
 [UNA 區段] 和 [區段名稱 UNB] 限制只能使用 ASCII 字元集中的值。  
  
## <a name="kedifact-character-set"></a>KEDIFACT 字元集  
 如同 EDIFACT，KEDIFACT 編碼交換的字元集也是在 UNB1 資料項目中建立。 對於 EDIFACT 字元集要套用的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料元素中的處理 KEDIFACT 交換建立時**UNB1**的**字元集和分隔符號**中雙向頁面協議索引標籤 （如果已定義了協議） 或**字元集和分隔符號**的協議索引標籤中的頁面**EDIFACT 後援設定**對話方塊 （若未定義協議是）。 值**識別項 (UNB1.1)**元素必須設定為 KECA。  
  
## <a name="x12-character-set"></a>X12 字元集  
 當 BizTalk 接收管線或傳送管線會執行 EDI 驗證的 X12 編碼訊息時，它會使用 X12 字元集管線的 CharacterSet 屬性中選取。 若要設定這個屬性，請開啟接收位置或傳送埠的 [屬性] 對話方塊，然後按一下接收或傳送管線旁邊的省略符號，再設定「解譯器」或「組合器」的 [CharacterSet] 屬性。  
  
 管線的 CharacterSet 屬性用來驗證 X12 與 EDIFACT 或 KEDIFACT，不同之 X12 編碼交換並非能夠自我描述以其字元集而言，因為交換。 讀取 ISA 標頭具有 ISO 或 UTF 編碼可能會導致不同的協議尋查值。 如此一來，BizTalk 必須知道要用於處理的訊息在協議尋查之前 （當它會取得協議的適當字元集） 的適當字元集。  
  
 指定 X12 字元集中的協議驗證要用於在**字元集和分隔符號**頁面之雙向協議索引標籤 （如果已定義了協議） 或**字元集和分隔符號**後援協議索引標籤中的頁面**X12 後援設定**對話方塊 （若未定義協議是）。 不過，BizTalk 只有在儲存整個屬性集時 (不是按下 TAB 鍵跳離欄位或顯示不同頁面時)，才會使用這些設定來驗證相關屬性的輸入值。 接收管線或傳送管線會忽略這些字元集屬性。  
  
> [!NOTE]
>  如果指定的字元集中的協議或後援協議不相符的字元集，選取要接收或傳送管線，可能會造成訊息驗證錯誤。 如果的 X12 協議中的字元將屬性設定為 擴充而管線屬性的字元集屬性設定為 基本 X12 是範例。  
  
 可用的字元集包括「基本」和「擴充的」(如＜X12 規格/實作指南＞所述) 以及 UTF8/Unicode。 預設為 UTF8。  
  
> [!NOTE]
>  雙向協議或後援協議中的資料元素分隔符號、 元件元素分隔符號以及區段結束字元輸入值會限制為 ASCII 字元集中的值。 驗證時，並不會針對 X12 字元集驗證這些屬性。  
  
 基本 」 字元集包括下列大寫字母、 數字、 空格和特殊字元： A 到 Z、 0 至 9、 ！ “ & ’ ( ) * + , - . / : ; ? = （空格）。  
  
 擴充字元集包括基本的字元組，以及小寫字母、 特定語言字元和其他特殊字元的字元： a 到 z、 %@ [] _ {} \ &#124;\< > ~ # $。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 傳訊](../core/edi-messaging.md)   
 [EDI 結構描述](../core/edi-schemas.md)