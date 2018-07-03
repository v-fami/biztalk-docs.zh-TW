---
title: 簡單型別衍生 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43932a0-039c-4211-82c0-087bae186145
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1b1904c96c2786abad283db7133a9755c8743d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998495"
---
# <a name="simple-type-derivation"></a>簡單型別衍生
XML 結構描述定義 (XSD) 語言提供數種機制，來定義，如下所示為基礎的現有的簡單型別衍生的簡單類型的變化：  
  
- **限制**。 使用限制機制的簡單型別衍生包含對該類型可能值的限制引用。 這類的範例有數字類型的最小和/或最大值，或是字串類型的最小和最大長度。  
  
- **清單**。 使用清單機制的簡單型別衍生允許將執行個體訊息中的單一屬性或項目值定義為包含特定類型的空格分隔的值清單。  
  
- **等位**。 使用聯集機制的簡單型別衍生允許將執行個體訊息中的單一屬性或項目值定義為數個指定類型的其中一個之單一值。  
  
  本節更詳細地描述這些簡單型別衍生，包括如何在 [屬性] 視窗中設定適當的節點屬性以定義這些衍生，以及對應的 XSD 之建構方式。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用限制機制的簡單類型衍生](../core/simple-type-derivation-using-the-restriction-mechanism.md)  
  
-   [使用清單機制的簡單類型衍生](../core/simple-type-derivation-using-the-list-mechanism.md)  
  
-   [使用聯集機制的簡單類型衍生](../core/simple-type-derivation-using-the-union-mechanism.md)