---
title: 覆寫 EDI 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16c19d3d-eab2-4d44-8752-25aeadb537a4
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 510a3817d0fd99d43b6da9462c74dd8bc7c1bdf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265438"
---
# <a name="overriding-edi-headers"></a>覆寫 EDI 標頭
傳送 EDI 編碼交換時，套用至訊息的 EDI 信封通常是根據接收端協議的 EDI 屬性，或是後援協議屬性。 不過，根據執行階段產生的值來設定 EDI 信封屬性通常會很有用。  
  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您可以使用 EdiOverride 內容屬性來指定針對輸出文件產生 EDI 信封所用的值。  
  
## <a name="using-edioverride-context-properties"></a>使用 EdiOverride 內容屬性  
 EdiOverride 內容屬性可讓您覆寫用來產生 EDI 信封的所有或部分值。 EDI 傳送管線將使用包含有效值的 EdiOverride 內容屬性來建構信封。 如果沒有填入某個屬性，此管線將會使用協議屬性或後援協議屬性 (如果沒有定義協議的話) 中指定的值。 如果某個屬性包含無效的值，此管線將會擱置訊息並回報驗證錯誤。  
  
> [!NOTE]
>  只有當 `EdiOverride.OverrideEdiHeader` 屬性已寫入訊息的內容而且包含 “True” 值時，才會使用 EdiOverride 集合中指定的值。  
>   
>  系統不會設定預設值。  
  
### <a name="edioverride-properties-for-x12-envelope-values"></a>X12 信封值的 EdiOverride 屬性  
 下表顯示 EdiOverride 內容屬性以及對應的 X12 信封標頭：  
  
|標頭|屬性|  
|------------|----------------|  
|交換控制標頭 (ISA)|ISA01、ISA02、ISA03、ISA04、ISA05、ISA06、ISA07、ISA08、ISA09、ISA10、ISA11、ISA12、ISA13、ISA14、ISA15、ISA16|  
|功能群組標頭 (GS)|GS01、GS02、GS03、GS04、GS05、GS06、GS07、GS08|  
|交易集標頭|ST02|  
  
### <a name="edioverride-properties-for-edifact-envelope-values"></a>EDIFACT 信封值的 EdiOverride 屬性  
 下表顯示 EdiOverride 內容屬性以及對應的 EDIFACT 信封區段：  
  
|區段|屬性|  
|-------------|----------------|  
|字串服務建議 (UNA)|UNA1、UNA2、UNA3、UNA4、UNA5、UNA6、UNA6Suffix|  
|交換控制標頭 (UNB)|UNB1_1、UNB1_2、UNB2_1、UNB2_2、UNB2_3、UNB3_1、UNB3_2、UNB3_3、UNB4_1、UNB4_2、UNB5、UNB6_1、UNB7、UNB8、UNB9、UNB10、UNB11|  
|功能群組標頭 (UNG)|UNG1、UNG2_1、UNG2_2、UNG3_1、UNG3_2、UNG4_1、UNG4_2、UNG5、UNG6、UNG7_1、UNG7_2、UNG7_3、UNG8|  
|訊息標頭 (UNH)|UNH1|  
  
 因為 UNA 和 UNG EDIFACT 區段是選擇性的所以 GenerateUNA 和 GenerateUNG 屬性可用來判斷這些標頭是否產生，而不論**套用 UNA 區段**協議設定。 下列表格顯示導致產生這些區段的值：  
  
|GenerateUNA 內容屬性|套用 UNA 區段協議設定|引擎行為|  
|----------------------------------|-----------------------------------------|---------------------|  
|TRUE|CHECKED|產生 UNA|  
|TRUE|UNCHECKED|產生 UNA|  
|FALSE|CHECKED|不產生 UNA|  
|FALSE|UNCHECKED|不產生 UNA|  
|不存在 (OverrideEDIHeader 為 false)|CHECKED|產生 UNA|  
|不存在 (OverrideEDIHeader 為 false)|UNCHECKED|不產生 UNA|  
  
|GenerateUNG 內容屬性|套用 UNG 區段協議設定|引擎行為|  
|----------------------------------|------------------------------------------|---------------------|  
|TRUE|CHECKED|產生 UNG|  
|TRUE|UNCHECKED|產生 UNG|  
|FALSE|CHECKED|不產生 UNG|  
|FALSE|UNCHECKED|不產生 UNG|  
|不存在 (OverrideEDIHeader 為 false)|CHECKED|產生 UNG|  
|不存在 (OverrideEDIHeader 為 false)|UNCHECKED|不產生 UNG|  
  
### <a name="group-envelopes"></a>群組信封  
 群組信封會提出一項特殊挑戰，因為交換可能會存在多個群組。 為了處理這項挑戰，EDI 傳送管線可以將信封套用至交換中的所有群組，或將信封套用至交換中的唯一群組。  
  
 若為單一交易，可以覆寫所有 GS 或 UNG 欄位。若為批次交換，就只能覆寫下列欄位：  
  
-   GS04  
  
-   GS05  
  
-   UNG4_1  
  
-   UNG4_2  
  
### <a name="batching"></a>批次處理  
 覆寫批次訊息的交易集控制編號是由批次處理協調流程所處理。 下列屬性可以寫入動作會覆寫進行批次處理的任何訊息內容的交易集控制編號：  
  
-   ST02 (適用於 X12 訊息)  
  
-   UNH1 (適用於 EDIFACT 訊息)  
  
> [!NOTE]
>  如果多個內送訊息包含相同群組中的相同控制編號，系統將擱置含有重複編號的訊息。  
  
> [!NOTE]
>  請勿針對即將進行批次處理的訊息升級 EdiOverride 內容屬性 ISA、UNA、GS 或 UNG。 如果您需要覆寫這些屬性，請先針對批次協調流程的輸出訊息升級這些屬性，然後再傳送至 EDI 傳送管線。  
  
### <a name="delimiter-collision"></a>分隔符號衝突  
 每個欄位的分隔符號 (例如 UNA 標頭) 都必須包含唯一值。 覆寫分隔符號值 (例如 UNA 標頭) 時，您必須確定每個分隔符號值不僅在您所覆寫的值內部是唯一的，而且在根據協議或後援協議設定所使用的任何分隔符號值之間也是唯一的。  
  
 例如，如果您覆寫了 UNA1、UNA2 和 UNA4，而且 UNA3、UNA5、UNA6 和 UNA6Suffix 來自協議屬性，則每個屬性都必須包含唯一值 (相較於其他屬性而言)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)