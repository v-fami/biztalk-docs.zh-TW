---
title: HL7 中的資料類型識別碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data types, data type ID
- data types, messages
- messages, data types
ms.assetid: d1412886-ff0b-4333-b01e-1c3ae45240e2
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d7251ce1c041ebfd2f523e3304bd253fec22fb9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983007"
---
# <a name="data-type-id-in-hl7"></a>HL7 中的資料類型識別碼
在 HL7 V2.1 的情況下的資料型別 ID 會是未定義的資料類型的預留位置。 其使用方式的範例如下：  
  
- ST 欄位的表單中的資料類型為 SI (順序 ID)。  
  
- NM 欄位的表單中的資料類型是複合欄位。  
  
  特別定義的複合資料類型的範例如下：  
  
- CK： 以檢查數字的複合識別碼。 例如：  
  
  ```  
  |128952^6^M11|  
  ```  
  
- CN： 複合的識別碼和名稱。 例如：  
  
  ```  
  |12372^RIGGINS^JOHN^""^MD|  
  |12372|  
  |^RIGGINS^JOHN^""^MD|  
  ```  
  
- 也是如此： 複合單位數量。 例如：  
  
  ```  
  |123.7^ML|  
  ```  
  
- CE： 自動程式化項目。 例如：  
  
  ```  
  |54.21^Laparoscopy^I9C^42112^^AS4|  
  ```  
  
  此資料類型會當地語系化，而且網站定義。 此外，HL7 V2.1 不提供此 HL7 Access 資料庫中的資料類型的涵蓋範圍。 用於產生結構描述，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 假設 HL7 V2.2 資料型別是否有效，然後使用此資訊來建置結構描述。 根據結構描述中的使用方式，適當的資料類型必須使用，這表示資料型別必須取代 CK、 也是如此，CE、 ST ^ SI，依此類推。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../adapters-and-accelerators/accelerator-hl7/data-types.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)