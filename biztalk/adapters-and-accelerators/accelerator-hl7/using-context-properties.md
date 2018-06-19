---
title: 使用內容屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, context properties
- messages, promoted properties
- promoted properties, context properties
- context properties, messages
ms.assetid: 306127a9-df03-4aaf-8dd8-76df51eb193d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a3fad82b8d537fcc017dfed175c5348cc1529d3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006751"
---
# <a name="using-context-properties"></a>使用內容屬性
BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 傳訊引擎和其元件內容屬性在內部使用。 不建議變更引擎的部分內容屬性所設定的值，因為它可能會影響引擎的執行邏輯。 不過，您可以變更大量的未由引擎所設定的屬性。 您可以使用內容屬性來建立傳送埠篩選條件運算式 (如需詳細資訊，請參閱[設定傳送埠的篩選條件運算式](../../adapters-and-accelerators/accelerator-hl7/setting-filter-expressions-on-send-ports.md))。 您也可以在篩選運算式中使用內容屬性，如協調流程。 屬性可用於篩選運算式，只要專案有參考的全域屬性結構描述 (其中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]時您可以使用其中一個常見的範本建立)。  
  
 下表包含一份[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]訊息內容屬性，「 傳訊引擎會使用。 引擎會使用許多這些屬性的路由。 序列化程式會使用其他人進行任何處理。 這些屬性包含前置詞[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。  
  
 如需有關[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]內容屬性 （其為 BTS 前置詞篩選條件運算式中識別），請參閱 BizTalk Server 說明中的 「 訊息內容屬性 」。 **BTS。SchemaStrongName**和**BTS。MessageType**兩個屬性，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎所使用。  
  
 下表中升級，而且需要資料行具有下列效果：  
  
-   當 IsPromoted 是"N"，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將值寫入內容中，而不是正在升級。  
  
-   IsRequired 時針對布林類型，"N"[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]寫入只有的值，如果為 true。  
  
-   IsRequired 時用於字串類型的"N"[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]寫入值，如果不是空白，或有預設值。  
  
|屬性名稱|升級|需要|注意|  
|-------------------|-----------------|-----------------|-----------|  
|BatchDateTime|Y|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理批次訊息時，請升級此屬性。|  
|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]訊息類型|Y|Y|序列化程式會使用這個屬性來區別單一和批次訊息。 HL7 解譯器會將它設定僅適用於批次處理的訊息。 屬性會指出訊息是單一訊息、 批次輸入的訊息或輸出批次訊息。 如果序列化程式找不到它，則會假設訊息是單一訊息。|  
|FHS10|Y|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理批次訊息時，請升級此屬性。|  
|FHS3|Y|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理批次訊息時，請升級此屬性。|  
|FHS4|Y|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理批次訊息時，請升級此屬性。|  
|FHS5|Y|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理批次訊息時，請升級此屬性。|  
|FHS6|Y|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理批次訊息時，請升級此屬性。|  
|FileDateTime|Y|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理批次訊息時，請升級此屬性。|  
|LastSegmentDelimiter 遺失|N|N|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]處理批次訊息時，請升級此屬性。|  
|MessageClass|Y|Y|包含**MessageClass2X**或**MessageClass2Xml**來區分兩種類別的訊息。|  
|MSA1|Y|Y|僅適用於 ACK 訊息。|  
|MSH1|N|Y|包含欄位分隔符號的欄位。 序列化程式會使用這個屬性。|  
|MSH2|N|Y|序列化程式會使用這個屬性。 包含編碼的字元 （元件分隔符號、 重複分隔符號、 逸出字元和子元件分隔符號） 的欄位。|  
|MSH3_1|Y|N|傳送應用程式欄位的第一個元件。|  
|MSH3_2|Y|N|傳送應用程式欄位的第二個元件。|  
|MSH3_3|Y|N|傳送應用程式欄位的第三個元件。|  
|MSH5_1|Y|N|接收應用程式欄位的第一個元件。|  
|MSH5_2|Y|N|接收應用程式欄位的第二個元件。|  
|MSH5_3|Y|N|接收應用程式欄位的第三個元件。|  
|ParseError|Y|Y|指出在剖析期間發生錯誤。|  
|SegmentDelimiter2Char|N|N|用來分隔區段的字元。|  
|ToBeBatched|Y|N|當設為 false，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不緩衝的訊息来批次處理更新版本，否則[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送訊息批次的一部分。|  
|ZPartPresent|Y|N|指示是否未宣告的 Z 區段不存在。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定傳送埠的篩選條件運算式](../../adapters-and-accelerators/accelerator-hl7/setting-filter-expressions-on-send-ports.md)