---
title: "基底和常見的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- base schemas
- schemas, common schemas
- schemas, base schemas
- common schemas
ms.assetid: 60eb24f6-cc4f-4c6d-ab15-9e3a6b4ed376
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88ca51abfcdbfe965bc3da8deeb97f72df736903
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="base-and-common-schemas"></a>基底和常見的結構描述
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]已實作的記錄和組成個別的訊息結構描述不同的結構描述中的項目。 這個方法會提供單一位置，以提供更新的欄位和隔離這類變更的訊息結構描述的格式。  
  
 基底結構描述 (**SWIFT 基底 Types.xsd**) 包含的訊息結構描述參考一般記錄和項目定義。 一般記錄和項目定義對應至 SWIFT FIN 訊息欄位。 您需要將這個結構描述加入至任何使用訊息結構描述的專案。 基底結構描述的規則和一般函數，涵蓋了，並定義 A4SWIFT 用來驗證適當的訊息執行個體的格式。 SWIFT 基底 Types.xsd 結構描述會定義 XSD **simpleType**和 SWIFT 欄位的複雜項目。 已定義 SWIFT **simpleType**元素的所有基底欄位的詳細資訊，例如金額、 速率、 價格以及等等，SWIFT 使用中的許多欄位。 SWIFT 基底 Types.xsd 結構描述也會定義可包含許多自訂的欄位，XSD 複雜的項目**simpleTypes**結構描述中定義。 例如， **BankIdentifierCode**銀行代碼、 國家/地區代碼、 區碼和分支程式碼，會使用複雜的項目。 使用者可以加入新**simpleTypes**和複雜的項目鏡像 SWIFT 的欄位，且可修改現有的類型。 您應該格外謹慎，不過，當您修改現有的型別，因為商務規則引擎 (BRE) 驗證 」 和 「 XML 驗證功能相依於這些定義的型別。  
  
 常見的結構描述 (**SWIFT 常見資料 Types.xsd**) 基底結構描述中定義適當的欄位的字元集。 SWIFT 定義中參考這些字元集， *SWIFT 使用者手冊*。 您也需要將通用的結構描述新增至您的結構描述專案。  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)