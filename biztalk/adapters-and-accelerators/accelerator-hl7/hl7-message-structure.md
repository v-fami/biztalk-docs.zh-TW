---
title: HL7 訊息結構 |Microsoft 文件
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
ms.openlocfilehash: d3e705d3c8a72b5ca1072157a227bf6f218035d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22205086"
---
# <a name="hl7-message-structure"></a>HL7 訊息結構
HL7 訊息是觸發程序事件相關聯的階層式結構。 標準 HL7 「 健康照護 （，），建立資料流系統之間需要真實世界中的事件 」 定義觸發程序事件。 每個觸發程序事件是與定義的訊息需要支援觸發程序事件的資料類型的抽象訊息相關聯。 抽象的訊息片段的集合，而且包含重複和這些區段包含的規則。 下表顯示與觸發程序事件 A04 – 註冊病患相關聯的抽象訊息的範例。  
  
|觸發程序事件|抽象的訊息|  
|-------------------|----------------------|  
|ADT ^ A04 ^ ADT_A01|許可、 放電，以及傳輸|  
|MSH|訊息標頭|  
|EVN|事件類型|  
|PID|病患識別碼|  
|[PD1]|其他的人口統計資料|  
|[{ROL}]|角色|  
|[{NK1}]|你 / 相關聯的合作對象的下一步|  
|PV1|瀏覽病患|  
|[PV2]|病患造訪-其他資訊|  
|[{ROL}]|角色|  
|[{DB1}]|行動不便資訊|  
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
|入 [2]|保險的其他資訊|  
|[{入 3}]|保險的其他資訊的憑證。|  
|[{ROL}]|角色|  
|}]||  
|[帳戶]|意外的資訊|  
|[UB1]|通用的帳單資訊|  
|[UB2]|通用帳單 92年資訊|  
|[PDA]|病患死亡和 Autopsy|  
  
 上述的括號"["，"]"表示區段或群組的區段是選擇性的在大括號時"{"，"}"表示的區段或區段重複群組。  
  
 區段是一組欄位每個符合特定的資料類型。 欄位可以有一個簡單或複雜的結構。 根據其資料型別定義中定義的規則的元件所組成。 為了支援更複雜的資料類型，某些元件可能包含子元件。  
  
> [!NOTE]
>  HL7 訊息編碼使用指定的分隔符號的事實限制導入新的方法進一步分割資料的開發人員的能力。 可以有任何子子元件，因為這項作業需要發明，新的分隔符號類型。  
  
 第一個 HL7 規格中未定義抽象的訊息。 模式與觸發程序事件相關聯之區段的抽象的訊息。 同樣地，HL7 訊息包含區段的重複在一起，或區段群組的集合。 第一個 HL7 規格中未定義區段群組。 V2.3.1，開始，並在後續版本中繼續執行，此變更的原因需要支援 XML 編碼方式。 例如，在事件觸發程序表，訊息結構的名稱是"ADT_A01"。 這是用來支援 A01 – 承認病患區段的相同的模式。 為了方便起見，訊息結構的名稱會對應至 （依據 HL7 文件中的位置） 的第一個觸發程序會使用它們的事件。 同樣地，觸發程序事件上表開頭入 1，包括入 2、 入 3，以及 ROL 中的區段群組重複一次為群組。 它的名稱，開頭為 2.5 版是 「 保險 」 群組。  
  
 在第 2 版間的版本相容性規則支援介面的演進需要標準的後續版本不包含使先前版本的結構。 這需要您沒有移除觸發程序事件，而您執行觸發程序事件適用於不同的用途，或不同的抽象訊息比原本預期。 抽象訊息，這表示您無法從訊息中，移除區段，也可以您讓選擇性的必要區段或重複區段非重複。 如果您加入一個區段，您必須執行結尾的訊息或訊息中重複群組結尾處。  
  
 下列函式的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：  
  
-   支援的所有觸發程序事件與訊息結構 V2.1 開始，並延續到 2.5 版。  
  
-   透過新增區段以及選擇性地調整區段及重複當地語系化的支援。  
  
## <a name="see-also"></a>另請參閱  
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)