---
title: 解譯器和組合器會升級屬性 |Microsoft 文件
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
ms.openlocfilehash: ab1e0cab902ded34f10cf03bc6e8229d28123be2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22211294"
---
# <a name="disassembler-and-assembler-promoted-properties"></a>解譯器和組合器會升級屬性
解譯器和組合器屬性分為兩類： 路由屬性、 路由和篩選。與執行階段屬性，針對內部處理。  
  
本主題提供新增、 和升級發佈至 MessageBox 資料庫 SWIFT 解譯器的所有訊息的屬性的清單。  
  
## <a name="routing-properties"></a>路由屬性

SWIFT 的解譯器會升級路由屬性。 您可以使用這些屬性的內容為基礎的路由 （傳送埠篩選條件），並接收協調流程中的篩選。  
  
|升級的名稱|Description|資料類型|數值範圍|使用範例|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**A4SWIFT_BatchId**|處理傳入的批次時，動態產生 SWIFT 解譯器的全域唯一識別碼。 解譯器會將此批次識別碼指派給發佈到 MessageBox 資料庫，來自相同的批次的所有訊息。<br /><br /> 設定為 **-1**單一訊息 （不來自傳入的批次）。|字串|"-1"或*全域唯一識別碼 (GUID)*|將訊息相互關聯相同**A4SWIFT_BatchId**可以將它們分組到相同的批次中原本到達值。|  
|**A4SWIFT_BreValidationErrors**|表示商務規則引擎 (BRE) 驗證期間發生的驗證錯誤的數目。|數值|>= 0|未通過 BRE 驗證的訊息篩選條件 (**A4SWIFT_BREValidationErrors**等於零)。|  
|**A4SWIFT_Failed**|指出訊息處理 （剖析及驗證） 期間是否發生任何失敗。 設定為**True**如果**A4SWIFT_ParseErrors** + **A4SWIFT_XmlValidationErrors** + **A4SWIFT_BreValidationErrors** > 0。|布林|True、False|唯一有效的 SWIFT 訊息篩選條件 (**A4SWIFT_Failed**等於**False**)。|  
|**A4SWIFT_ParseErrors**|指出在剖析期間發生的剖析錯誤數目。|數值|>= 0|未通過剖析的訊息篩選條件 (**A4SWIFT_ParseErrors**等於零)。|  
|**A4SWIFT_PosInBatch**|表示來自傳入的批次訊息的序數位置。 批次包含*n*訊息， **A4SWIFT_PosInBatch**接受從 1 到值*n*、 對應至訊息的批次中的序數位置。<br /><br /> 設定為**0**訊息是否為批次標頭。<br /><br /> 設定為**n + 1**訊息是否為批次結尾。<br /><br /> 設定為**1**如果訊息本身就是整個批次 （停用批次片段）。<br /><br /> 設定為 **-1**單一訊息 （不來自傳入的批次）。|數值|>= -1|從相同的傳入批次成為原始它們到達的順序排序訊息。|  
|**A4SWIFT_XmlValidationErrors**|表示 XML 驗證期間發生的驗證錯誤的數目。|數值|>= 0|未通過 XML 驗證的訊息篩選條件 (**A4SWIFT_XmlValidationErrors**等於零)。|  
  
> [!NOTE]
>  一般情況下，應該評估所有輸入路由或篩選運算式**A4SWIFT_Failed**之前評估其他路由的屬性。 只有**A4SWIFT_Failed**一定會升級及可用。 無法使用的有效單一訊息 （非批次訊息） 發佈到 MessageBox 資料庫的剩餘屬性。 其他屬性只會升級針對*失敗*單一訊息，並針對批次訊息 （有效或失敗）。  

## <a name="runtime-properties"></a>執行階段屬性

SWIFT 的解譯器會升級執行階段屬性，並使用它們進行內部處理序在執行階段。 它們只會升級，而且可供路由在某些情況下，視內容而定。 一般情況下，請勿使用這些內容的輸入路由或篩選。 它們不保證可並升級。 在某些情況下，您可以擷取，或使用路由屬性篩選之後，檢查這些屬性。 下表列出的執行階段屬性。  
  
|升級的名稱|Description|資料類型|數值範圍|使用範例|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**A4SWIFT_IsMessageHeaderValued**|表示是否資料存在於多部分訊息的標頭部分。 設定為**True**如果標頭部分包含資料 （來自批次訊息的訊息信封標頭）。 設定為**False**如果標頭部分是空的。|布林|True、False|決定是否要檢查 （例如，訊息修復的協調流程） 中擷取訊息標頭部分。|  
|**A4SWIFT_IsMessageTrailerValued**|表示是否資料存在於多部分訊息結尾部分。 設定為**True**如果結尾部分包含資料 （訊息來自批次訊息的信封結尾）。 設定為**False**如果是空的結尾部分。|布林|True、False|決定是否要檢查 （例如，訊息修復的協調流程） 中擷取訊息結尾部分。|  
|**A4SWIFT_MessageType**|指出 SWIFT SWIFT 的標頭中的三位數數字訊息類型 (**MT*xxx * * *)。|字串|*三位數字*|以動態方式識別訊息的 SWIFT 訊息類型。|  
|**A4SWIFT_MessageType2**|指出 SWIFT SWIFT 的標頭中的三位數數字訊息類型 (**MT*xxx * * *)。 使用唯有**A4SWIFT_MessageType** SWIFT 的標頭中找不到。|字串|*三位數字*|以動態方式識別訊息的 SWIFT 訊息類型。|  
|**A4SWIFT_NumberOfParts**|指出組件中多部分訊息數目。<br /><br /> 設定為**1**如果只有內文部分存在 （包含有效的個別 SWIFT 訊息不源自於批次或批次標頭或從批次封套的批次結尾）。<br /><br /> 設定為**2**的主體和錯誤組件是否存在 （包含失敗的訊息或批次錯誤組件包含錯誤集合 XML 內文部分）。<br /><br /> 設定為**3**主體、 標頭和結尾部分有包含有效個別 SWIFT 訊息來自批次中，標頭部分包含訊息信封標頭，如果使用，而且結尾部分包含的訊息 （內文部分信封結尾，如果使用- **A4SWIFT_IsMessageHeaderValued**和**A4SWIFT_IsMessageTrailerValued**表示標頭和結尾的組件中是否有資料存在)。|數值|1, 2, 3|使用組件的指定數目的訊息篩選條件 (例如，篩選**A4SWIFT_NumberOfParts**訊息修復協調流程等兩個接收圖形)。|  
|**A4SWIFT_SecondaryMessageType**|字串值，指出 SWIFT SWIFT 的標頭中訊息的子類型 (**MT*xxx_XYZ * * *)。|字串|*任何字串*|以動態方式識別訊息的 SWIFT 訊息子型別。|  
  
 
## <a name="see-also"></a>另請參閱  
[A4SWIFT_* 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)   