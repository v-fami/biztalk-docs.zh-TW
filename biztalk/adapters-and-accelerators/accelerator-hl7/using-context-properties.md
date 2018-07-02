---
title: 使用內容屬性 |Microsoft Docs
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
ms.openlocfilehash: b13af4b6325cddb4a642a24bcd61c42a102531e1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980679"
---
# <a name="using-context-properties"></a>使用內容屬性
BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 傳訊引擎和其元件內容屬性在內部使用。 不建議變更的部分內容屬性的引擎所設定的值，因為它可能會影響引擎的執行邏輯。 不過，您可以變更大量不由引擎設定的屬性。 您可以用於建立傳送埠上的篩選條件運算式中的內容屬性 (如需詳細資訊，請參閱 <<c0> [ 設定傳送埠的篩選條件運算式](../../adapters-and-accelerators/accelerator-hl7/setting-filter-expressions-on-send-ports.md))。 您也可以使用篩選條件運算式中的內容屬性，協調流程的選項。 屬性可用於篩選運算式，只要專案具有全域屬性結構描述的參考 (其[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]建立當您使用其中一個常見的範本)。  
  
 下表包含一份[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]訊息，傳訊引擎會使用的內容屬性。 引擎會使用許多這些屬性路由。 序列化程式會使用其他人進行任何處理。 這些屬性包含前置詞[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。  
  
 如需詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]內容屬性 （其識別篩選條件運算式中的 BTS 前置詞），請參閱 BizTalk Server 說明中的 [訊息內容屬性]。 **BTS。SchemaStrongName**和**BTS。MessageType**兩個屬性，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎所使用。  
  
 下表中，會升級且需要資料行有下列效果：  
  
- 當 IsPromoted 是"N"，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]值寫入內容，而非升級。  
  
- 當 IsRequired 是"n"名的布林值類型，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]寫入只有的值，如果為 true。  
  
- 當 IsRequired 是"n"名的字串類型，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]寫入值，如果不是空白，或存在於的預設值。  
  
|                                           屬性名稱                                            | 升級 | 需要 |                                                                                                                                                                      注意                                                                                                                                                                       |
|----------------------------------------------------------------------------------------------------|-------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                           BatchDateTime                                            |      Y      |      N      |                                                                                                [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 處理批次訊息時，請升級此屬性。                                                                                                 |
| [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]MessageType |      Y      |      Y      | 序列化程式會使用這個屬性來區別單一和批次的訊息。 HL7 反組譯工具會將它設定只針對批次訊息。 此屬性會指出訊息是單一訊息、 輸入批次訊息或輸出批次訊息。 如果序列化程式找不到它，它會假設訊息是單一訊息。 |
|                                               FHS10                                                |      Y      |      N      |                                                                                                [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 處理批次訊息時，請升級此屬性。                                                                                                 |
|                                                FHS3                                                |      Y      |      N      |                                                                                                [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 處理批次訊息時，請升級此屬性。                                                                                                 |
|                                                FHS4                                                |      Y      |      N      |                                                                                                [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 處理批次訊息時，請升級此屬性。                                                                                                 |
|                                                FHS5                                                |      Y      |      N      |                                                                                                [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 處理批次訊息時，請升級此屬性。                                                                                                 |
|                                                FHS6                                                |      Y      |      N      |                                                                                                [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 處理批次訊息時，請升級此屬性。                                                                                                 |
|                                            FileDateTime                                            |      Y      |      N      |                                                                                                [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 處理批次訊息時，請升級此屬性。                                                                                                 |
|                                    LastSegmentDelimiter 遺漏                                    |      N      |      N      |                                                                                                [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 處理批次訊息時，請升級此屬性。                                                                                                 |
|                                            MessageClass                                            |      Y      |      Y      |                                                                                                                  包含**MessageClass2X**或是**MessageClass2Xml**來區別兩個類別的訊息。                                                                                                                  |
|                                                MSA1                                                |      Y      |      Y      |                                                                                                                                                        只適用於通知訊息。                                                                                                                                                         |
|                                                MSH1                                                |      N      |      Y      |                                                                                                                                   包含欄位分隔符號的欄位。 序列化程式會使用這個屬性。                                                                                                                                   |
|                                                MSH2                                                |      N      |      Y      |                                                                                    序列化程式會使用這個屬性。 包含編碼的字元 （元件分隔符號、 重複分隔符號、 逸出字元和子元件分隔符號） 的欄位。                                                                                    |
|                                               MSH3_1                                               |      Y      |      N      |                                                                                                                                              傳送應用程式欄位的第一個元件。                                                                                                                                               |
|                                               MSH3_2                                               |      Y      |      N      |                                                                                                                                              傳送應用程式欄位的第二個元件。                                                                                                                                              |
|                                               MSH3_3                                               |      Y      |      N      |                                                                                                                                              傳送應用程式欄位的第三個元件。                                                                                                                                               |
|                                               MSH5_1                                               |      Y      |      N      |                                                                                                                                             接收的應用程式欄位的第一個元件。                                                                                                                                              |
|                                               MSH5_2                                               |      Y      |      N      |                                                                                                                                             接收的應用程式欄位的第二個元件。                                                                                                                                             |
|                                               MSH5_3                                               |      Y      |      N      |                                                                                                                                             接收的應用程式欄位的第三個元件。                                                                                                                                              |
|                                             ParseError                                             |      Y      |      Y      |                                                                                                                                                 指出在剖析期間發生錯誤。                                                                                                                                                 |
|                                       SegmentDelimiter2Char                                        |      N      |      N      |                                                                                                                                                      用來分隔區段的字元。                                                                                                                                                       |
|                                            ToBeBatched                                             |      Y      |      N      |                       當設定為 false 時，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]未緩衝的訊息要批次處理的更新版本，否則[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送訊息批次的一部分。                       |
|                                            ZPartPresent                                            |      Y      |      N      |                                                                                                                                              表示未宣告的 Z 區段是否存在。                                                                                                                                               |
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定傳送埠的篩選條件運算式](../../adapters-and-accelerators/accelerator-hl7/setting-filter-expressions-on-send-ports.md)