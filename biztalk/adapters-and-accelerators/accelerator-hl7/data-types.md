---
title: "資料型別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types, messages
- messages, data types
ms.assetid: 7a758289-1629-48a0-843d-6f6773bd5ba6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8580b4f6c2a3f1a9f461b112bb4125f1a11ebbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-types"></a>資料型別
資料類型規格是重要的工具適用於分割 HL7 standard 的複雜性和，請務必了解 HL7 欄位的資料內容。 某些資料類型是簡單，而且包含只有一個元件，而且某些包含許多元件和子元件。 例如，PID.5 病患名稱有輸入 XPN 2.4 版本中的資料。 此資料類型支援一般的細分的英文語言名稱，比方說，姓氏、 名字、 中間名，以及後置詞、 前置詞、 名稱類型程式碼，以及名稱 （日期） 的有效範圍。  
  
 在新 HL7 版本中，您可以新增，但不是會移除資料型別。 如果您將內容加入為資料類型，藉由新增新元件，您只可以將它們所在它們都巢狀結構的結尾。 在某些情況下，HL7 組織會合併現有的資料類型，以形成新的。 這會造成需要支援先前已在原始的資料類型的子元件的項目。  
  
 下列函式的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]支援標準的資料類型從 V2.1 HL7 版本上。  
  
-   您可以限制資料型別在適當時開發介面。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [資料類型識別碼中 HL7 2.1](../../adapters-and-accelerators/accelerator-hl7/data-type-id-in-hl7.md)