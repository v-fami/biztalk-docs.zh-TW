---
title: 基底和通用結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base schemas
- schemas, common schemas
- schemas, base schemas
- common schemas
ms.assetid: 60eb24f6-cc4f-4c6d-ab15-9e3a6b4ed376
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b7f8f86e4b74b84cef556ae95bc6255d8575237
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012567"
---
# <a name="base-and-common-schemas"></a>基底和通用結構描述
Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]已實作的記錄和組成個別的訊息結構描述不同的結構描述中的項目。 此方法提供單一位置來提供更新的欄位和隔絕這類變更的訊息結構描述的格式。  
  
 基底結構描述 (**SWIFT 基底 Types.xsd**) 包含訊息結構描述參考的通用記錄及項目定義。 常見的記錄] 和 [項目定義對應至 SWIFT FIN 訊息欄位。 您要使用的訊息結構描述的任何專案中加入此結構描述。 基底結構描述會涵蓋常見的函式，與規則，並定義 A4SWIFT 驗證適當的訊息執行個體所使用的格式。 SWIFT 基底 Types.xsd 結構描述會定義 XSD **simpleType**和 SWIFT 欄位的複雜元素。 已定義 SWIFT **simpleType**所有基底欄位的詳細資訊，例如數量、 速率、 價格以及等等，SWIFT 使用中的許多欄位的項目。 SWIFT 基底 Types.xsd 結構描述也會定義 XSD 包含許多自訂欄位的複雜項目**simpleTypes**結構描述中定義。 例如， **BankIdentifierCode**銀行代碼、 國家/地區代碼、 區碼和分支程式碼，會使用複雜的項目。 使用者可以加入新**simpleTypes**和複雜的項目鏡像 SWIFT 的欄位，且可修改現有的型別。 您應該要特別注意，不過，當您修改現有的型別，因為 商務規則引擎 (BRE) 驗證 和 XML 驗證功能必須依賴這些定義的類型。  
  
 常見的結構描述 (**SWIFT 常見資料 Types.xsd**) 基底結構描述中定義的適當欄位的字元集。 SWIFT 定義這些字元集中，依照*SWIFT 使用者手冊*。 您也需要將常見的結構描述新增至您的結構描述專案。  
  
## <a name="see-also"></a>另請參閱  
 [使用結構描述](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)