---
title: "EDI 標頭和結尾 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf1dae3-9570-413d-a85d-94dcbb561906
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 655a7261da5dc66687fdf0cd623802854c0fa4ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-headers-and-trailers"></a>EDI 標頭與結尾
EDI 交換的部分會以標頭和結尾分隔，這些標頭和結尾必須符合 X12 或 EDIFACT 標準。 交換控制標頭和結尾只會出現一次，而如果交易集和群組在交換內進行批次處理，則功能群組和交易集標頭和結尾會重複出現。 標頭和結尾是由一系列的資料項目組成，其中包括標頭和結尾所包含內容的相關資訊。  
  
 X12 和 EDIFACT 的標頭和結尾非常類似。 主要差異在於 EDIFACT 的「UNA 字串服務建議」標頭，它會定義交換中使用的分隔符號。 在 X12 編碼中，分隔符號是在「ISA 交換控制標頭」中定義。  
  
 交換控制和功能群組標頭和結尾會表示為信封區段。 當 BizTalk Server 將內送交換分割成交易集時，它會將這些信封區段儲存成內容屬性。 主要用於路由傳送的關鍵信封屬性會以個別屬性提供。 保留交換時不會有上述動作，因為在這種情況下，信封資料屬於訊息本身的一部分。  
  
 當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]產生外寄訊息，則根據交易夥伴協議 （或全域的合約，若無合作對象判定） 上的標頭和結尾。  
  
 標頭和結尾欄位和分隔符號字元來分隔它們在交換，兩者中定義的兩個合作對象之間的協議。 為協議所定義的分隔符號字元必須不使用任何交換、 群組或交易集標頭或結尾欄位的定義中。 如有需要，交換將會失敗處理傳送的 EDI 組合器處於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或接收的合作對象的解譯器中。 如果交換是輸出批次，它在「EDI 組合器」中即會失敗，因為「組合器」會針對標頭控制 (服務) 結構描述驗證信封。 如果未批次交換，EDI 組合器會進行序列化，但它無法解譯器在接收端協議中的處理。  
  
## <a name="x12-headers-and-trailers"></a>X12 標頭與結尾  
 X12 編碼訊息的標頭和結尾如下：  
  
```  
ISA Interchange Control Header  
  GS Functional Group Header  
    ST Transaction Set Header  
    SE Transaction Set Trailer  
  GE Functional Group Trailer  
IEA Interchange Control Trailer  
```  
  
 如果 ISA 標頭後面緊接跟著 IEA 結尾，表示交換是空的。 如果交易集存在，GS 標頭和 GE 結尾一定會存在。否則，它們是條件式。  
  
 X12 訊息中的 ISA 交換控制標頭欄位的長度是固定的。 針對某些欄位，您可以輸入長度少於欄位固定長度的值。 若這麼做，交換就必須包含尾端空格 (字串欄位) 或前置零 (數字欄位)，使每個欄位都符合必要長度。 當建立輸出交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會輸入尾端空格或前置零，以建立正確長度的交換控制標頭。 GS 群組標頭欄位和 ST 交易集標頭欄位的長度並不固定。  
  
 在 X12 編碼、 功能安全性標頭、 功能確保標頭、 功能安全性值區段和功能安全性結尾區段已超出範圍[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 和 AS2。 如果您收到含有這些區段的交換，系統就會擱置此作業並顯示錯誤記錄，表示這些是無法識別的區段。  
  
 ST01 欄位是交易集識別代碼，而 ST02 欄位是交易集控制編號。 ST03 欄位是結構描述版本識別項。 SE01 欄位表示交易集中包含的區段數目，而 SE02 欄位與 ST02 欄位相同 (都是交易集控制編號)。 當剖析內送訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會確認交易集中的區段數目是否與 SE01 欄位的值。 當產生外寄訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將 SE01 欄位設定為交易集中的區段的正確數目。  
  
 將序列化為外寄 EDI 交換的 XML 交易集，應該有交易集標頭和結尾。 不過，如果訊息沒有交易集標頭和結尾，「EDI 組合器」也會處理此訊息。 對 XML 交易集而言，X12 和 EDIFACT 結構描述中的交易集標頭和結尾都是選擇性項目。 如果交易沒有標頭或結尾，EDISend 或 AS2EDISend 傳送管線中的「EDI 組合器」就會將交易集標頭和結尾值加入至此交易。 這些值是根據對應或計算而定。 EDI 組合器會針對交換 XML (保留批次)、批次交易集 XML 和交易集 XML 執行這項作業。 如需詳細資訊，請參閱[X12 交易集標頭和結尾區段](../core/how-the-edi-assembler-works.md#BKMK_X12)或[EDIFACT 交易集標頭和結尾區段](../core/how-the-edi-assembler-works.md#BKMK_EDIFACT)。  
  
## <a name="edifact-headers-and-trailers"></a>EDIFACT 標頭和結尾  
 EDIFACT 編碼訊息的標頭和結尾如下：  
  
```  
UNA Service String Advice  
UNB Interchange Control Header  
  UNG Functional Group Header  
    UNH Message Header  
    UNT Message Trailer  
  UNE Functional Group Trailer  
UNZ Interchange Control Trailer  
```  
  
 UNA 標頭不是必要項目， 而 UNB 標頭是必要項目。 如果有 UNA 標頭存在，其中會包含在處理內送訊息時所要使用的分隔符號，否則將會使用為 EfactDelimiters 管線屬性定義的分隔符號。  
  
 如果 UNB 標頭後面緊接跟著 UNZ 結尾，表示交換是空的。 如果 UNG 標頭後面緊接跟著 UNE 結尾，表示群組是空的。 UNG 標頭和 UNE 結尾配對是選擇性項目，不一定要出現在訊息中。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 訊息結構](../core/edi-message-structure.md)