---
title: HL7 訊息結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- trigger events
- messages, trigger events
- segments, messages
- messages, message structure
ms.assetid: 4dbef56d-97ae-466d-bc8a-dc96c40896f6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a298a21b7df2605cdb8dc181898808c94cf40b33
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996951"
---
# <a name="hl7-message-structure"></a>HL7 訊息結構
HL7 訊息是觸發程序事件相關聯的階層式結構。 標準 HL7 定義 」 （，），會建立資料流各系統間需要美國衛生保健真實世界中的事件 」 觸發程序事件。 每個觸發程序事件是與定義的訊息需要支援觸發程序事件的資料類型的抽象訊息相關聯。 抽象訊息區段的集合，而且包含重複的這些區段包含的規則。 下表顯示與觸發程序事件 A04 – 註冊病患相關聯的抽象訊息的範例。  
  
|觸發程序事件|抽象訊息|  
|-------------------|----------------------|  
|ADT ^ A04 ^ ADT_A01|許可、 放電和傳輸|  
|MSH|訊息標頭|  
|EVN|事件類型|  
|PID|病患識別碼|  
|[PD1]|其他的人口統計資料|  
|[{ROL}]|角色|  
|[{NK1}]|家族相互交換 / 相關聯的合作對象的下一步|  
|PV1|瀏覽病患|  
|[PV2]|病患造訪-其他資訊|  
|[{ROL}]|角色|  
|[{DB1}]|傷殘保險資訊|  
|[{OBX}]|觀察/結果|  
|[{AL1}]|Allergy 資訊|  
|[{DG1}]|診斷資訊|  
|[DRG]|診斷相關的群組|  
|[{||  
|PR1|程序|  
|[{ROL}]|角色|  
|}]||  
|[{GT1}]|保證人角色|  
|[{||  
|入 1|Insurance|  
|[入 2]|保險的其他資訊|  
|[{入 3}]|保險的其他資訊的憑證。|  
|[{ROL}]|角色|  
|}]||  
|[帳戶]|意外的資訊|  
|[UB1]|通用的帳單資訊|  
|[UB2]|通用的帳單 92年資訊|  
|[PDA]|病患死了 Autopsy|  
  
 上述在方括號"["，"]"表示區段或群組的區段是選擇性的在大括號時"{"，"}"表示的區段或重複的區段群組。  
  
 區段是的群組欄位的每一個都符合特定資料型別。 欄位可以有一個簡單或複雜的結構。 根據其資料型別定義中定義的規則的元件所組成。 為了支援更複雜的資料類型，某些元件可能包含子元件。  
  
> [!NOTE]
>  HL7 訊息編碼會使用指定的分隔符號的事實會限制開發人員能夠帶來了新的細分資料的方式。 由於這項作業需要創造新的分隔符號類型時，則可以是任何子子元件。  
  
 第一個 HL7 規格並不會定義抽象的訊息。 抽象訊息是區段與觸發程序事件相關聯的模式。 同樣地，HL7 訊息包含的區段放在一起，重複或區段群組的集合。 第一個 HL7 規格並不會定義區段群組。 V2.3.1，從繼續在後續版本中，此變更的原因需要支援 XML 編碼方式。 例如，觸發程序事件上表中，訊息結構的名稱是"ADT_A01 」。 這是用來支援管理 A01 – 承認病患的區段相同模式。 為了方便起見，訊息結構的名稱會對應到 （依據 HL7 文件中的位置） 的第一個觸發程序會使用它們的事件。 同樣地，觸發程序事件上表開頭入 1，包括入 2、 入 3 和 ROL 中的區段群組重複做為群組。 它的名稱，開頭為 2.5 版是 「 保險 」 的群組。  
  
 第 2 版間的版本相容性規則支援介面的發展需要標準的後續版本不包含結構使先前的版本。 這需要您沒有移除觸發程序事件，且您執行使用觸發程序事件針對不同用途，或使用不同的抽象訊息比原本預期。 抽象訊息，這表示您無法移除訊息中的區段，也可以您讓選擇性的必要區段，或重複區段不重複。 如果您新增的區段時，您必須進行訊息結尾處，或在訊息中重複群組結尾處。  
  
 Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：  
  
-   支援的所有觸發程序事件與訊息結構 v2.1 將分別從開始，一直持續到 V2.5。  
  
-   透過加入區段和量身訂做區段選擇性和重複的本地化的支援。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)