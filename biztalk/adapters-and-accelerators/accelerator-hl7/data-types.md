---
title: 資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data types, messages
- messages, data types
ms.assetid: 7a758289-1629-48a0-843d-6f6773bd5ba6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a7b8d75be35be01e9c961d6bd054dcaed6d3aee
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984671"
---
# <a name="data-types"></a>資料型別
資料類型規格是重要的工具，進行資料分割 HL7 標準的複雜度，並請務必了解 HL7 欄位的資料內容。 某些資料類型是簡單，而且包含只有一個元件，而且部分包含許多元件和子元件。 例如，PID.5 病患名稱有輸入 XPN 版本 2.4 中的資料。 此資料類型支援常見量度的英文語言名稱，比方說，姓氏、 名字、 中間名，以及後置詞，前置詞、 名稱型別程式碼和名稱的有效性 （日期） 範圍。  
  
 在新的 HL7 版本中，您可以新增，但不是會移除資料型別。 如果您將內容加入的資料類型，藉由新增新的元件或子元件，您只可以將它們在其中內嵌結構的結尾。 在某些情況下，HL7 組織會合併現有的資料類型，以形成新的。 這會導致需要支援先前在原始的資料類型的子元件的項目。  
  
 Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 支援標準的資料類型從 V2.1 所有 HL7 版本上。  
  
- 您可以限制資料型別在適當時開發介面。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [資料類型識別碼 HL7 2.1](../../adapters-and-accelerators/accelerator-hl7/data-type-id-in-hl7.md)