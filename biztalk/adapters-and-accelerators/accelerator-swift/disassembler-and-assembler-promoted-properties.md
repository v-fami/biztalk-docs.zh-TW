---
title: 解譯器和組合器升級屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disassembler, promoted properties
- promoted properties, assembler
- promoted properties, disassembler
- assembler, promoted properties
ms.assetid: 342b0250-bdf7-45ce-8964-3aeda89989b1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bd97789ef793b386cc9ce132db69f89adf8ecdb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977215"
---
# <a name="disassembler-and-assembler-promoted-properties"></a>解譯器和組合器升級屬性
解譯器和組合器的內容分為兩類： 路由屬性、 路由和篩選，與執行階段屬性，供內部處理。  
  
本主題提供的屬性新增至，並升級所有的訊息發佈到 MessageBox 資料庫 SWIFT 解譯器的清單。  
  
## <a name="routing-properties"></a>路由屬性

SWIFT 解譯器會升級路由屬性。 您可以使用這些屬性的內容為基礎的路由 （傳送埠篩選條件），並接收協調流程中的篩選。  
  
|升級的名稱|描述|資料類型|數值範圍|使用範例|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**A4SWIFT_BatchId**|全域唯一識別碼，來動態產生 SWIFT 解譯器處理的輸入批次時。 解譯器會將此批次識別碼指派給所有發佈至 MessageBox 資料庫，來自相同的批次訊息。<br /><br /> 設定為 **-1** （不來自輸入的批次） 的單一訊息。|String|"-1"或*全域唯一識別碼 (GUID)*|具有相同的訊息相互關聯**A4SWIFT_BatchId**將它們回復到相同的原始送達的批次的值。|  
|**A4SWIFT_BreValidationErrors**|表示商務規則引擎 (BRE) 驗證期間發生驗證錯誤的數目。|數值|>= 0|未通過 BRE 驗證的訊息篩選條件 (**A4SWIFT_BREValidationErrors**等於零)。|  
|**A4SWIFT_Failed**|指出訊息處理 （剖析和驗證） 期間是否發生任何失敗。 設定為**真**如果**A4SWIFT_ParseErrors** + **A4SWIFT_XmlValidationErrors** + **A4SWIFT_BreValidationErrors** > 0。|布林|True、False|唯一有效的 SWIFT 訊息篩選條件 (**A4SWIFT_Failed** equals **False**)。|  
|**A4SWIFT_ParseErrors**|表示剖析期間發生剖析錯誤的數目。|數值|>= 0|未失敗剖析的訊息篩選條件 (**A4SWIFT_ParseErrors**等於零)。|  
|**A4SWIFT_PosInBatch**|表示來自輸入的批次訊息的序數位置。 批次包含*n*訊息**A4SWIFT_PosInBatch**接受從 1 到值*n*對應訊息的批次中的序數位置。<br /><br /> 設定為**0**如果訊息是批次標頭。<br /><br /> 設定為**n+1**如果訊息是批次的結尾。<br /><br /> 設定為**1**如果訊息本身就是整個批次 （已停用批次片段）。<br /><br /> 設定為 **-1** （不來自輸入的批次） 的單一訊息。|數值|>= -1|排序從相同的輸入批次訊息的送達的原始順序。|  
|**A4SWIFT_XmlValidationErrors**|表示 XML 驗證期間發生驗證錯誤的數目。|數值|>= 0|未通過 XML 驗證的訊息篩選條件 (**A4SWIFT_XmlValidationErrors**等於零)。|  
  
> [!NOTE]
>  一般情況下，所有輸入路由或篩選的運算式應該評估**A4SWIFT_Failed**之前評估任何其他路由的屬性。 只有**A4SWIFT_Failed**一定會升級且可用。 無法使用的有效單一訊息 （非批次訊息） 發佈至 MessageBox 資料庫的剩餘屬性。 其他屬性只會升級針對*失敗*單一訊息，並針對批次訊息 （有效或失敗）。  

## <a name="runtime-properties"></a>執行階段屬性

SWIFT 解譯器會升級執行階段屬性，並使用它們在執行階段內部處理程序。 它們只會升級且可供路由在某些情況下，視內容而定。 一般情況下，請勿用於這些屬性路由或篩選。 它們不保證升級和運作。 在某些情況下，您可以檢查這些屬性之後擷取，或使用路由屬性篩選。 下表列出執行階段屬性。  
  

|           升級的名稱            |                                                                                                                                                                                                                                                                                                                                                                                                            描述                                                                                                                                                                                                                                                                                                                                                                                                             | 資料類型 |      數值範圍       |                                                                           使用範例                                                                           |
|------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **A4SWIFT_IsMessageHeaderValued**  |                                                                                                                                                                                                                                                                                               指出資料是否在多部分訊息的標頭部分。 設定為 **，則為 True**如果標頭部分包含資料 （來自批次訊息的訊息信封標頭）。 設定為**False**如果是空的標頭部分。                                                                                                                                                                                                                                                                                                |  布林  |      True、False       |                        決定是否要檢查 （例如，在訊息修復協調流程） 擷取訊息的標頭部分。                         |
| **A4SWIFT_IsMessageTrailerValued** |                                                                                                                                                                                                                                                                                             指出資料是否在多部分訊息結尾部分。 設定為 **，則為 True**如果結尾部分包含資料 （訊息來自批次訊息的信封結尾）。 設定為**False**如果是空的結尾部分。                                                                                                                                                                                                                                                                                              |  布林  |      True、False       |                        決定是否要檢查 （例如，在訊息修復協調流程） 擷取訊息結尾部分。                        |
|      **A4SWIFT_MessageType**       |                                                                                                                                                                                                                                                                                                                                                                     指出 SWIFT SWIFT 標頭中的三位數數字訊息類型 (**MT\*xxx**\*)。                                                                                                                                                                                                                                                                                                                                                                      |  String   | *三位數字* |                                                     以動態方式識別訊息的 SWIFT 的訊息類型。                                                     |
|      **A4SWIFT_MessageType2**      |                                                                                                                                                                                                                                                                                                                              指出 SWIFT SWIFT 標頭中的三位數數字訊息類型 (**MT\*xxx**<em>)。使用才\* \*A4SWIFT_MessageType</em> \* SWIFT 標頭中找不到。                                                                                                                                                                                                                                                                                                                              |  String   | *三位數字* |                                                     以動態方式識別訊息的 SWIFT 的訊息類型。                                                     |
|     **A4SWIFT_NumberOfParts**      | 指出組件中多部分訊息數目。<br /><br /> 設定為**1**如果只有主體組件 （包含有效的個別 SWIFT 訊息不源自批次或批次標頭或從批次的信封的批次結尾）。<br /><br /> 設定為**2**主體和錯誤的組件是否存在 （包含失敗的訊息或批次，其中包含 XML 中的 [錯誤] 集合的錯誤組件內文部分）。<br /><br /> 設定為**3**主體、 標頭和結尾部分有包含來自批次標頭部分包含訊息信封標頭，如果使用，而且結尾部分包含訊息的有效個別的 SWIFT 訊息 （內文部分信封結尾，如果使用 — **A4SWIFT_IsMessageHeaderValued**並**A4SWIFT_IsMessageTrailerValued**指出資料是否在標頭和結尾的組件)。 |  數值  |        1, 2, 3         | 使用給定的組件數目的訊息篩選條件 (例如，篩選**A4SWIFT_NumberOfParts**訊息修復協調流程就等於兩個接收圖形)。 |
|  **A4SWIFT_SecondaryMessageType**  |                                                                                                                                                                                                                                                                                                                                                                    字串值，指出 SWIFT SWIFT 標頭中的訊息的子型別 (**MT\*xxx_XYZ**\*)。                                                                                                                                                                                                                                                                                                                                                                    |  String   |      *任何字串*      |                                                   以動態方式識別訊息的 SWIFT 訊息子型別。                                                    |
 
## <a name="see-also"></a>另請參閱  
[A4SWIFT_* 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)   