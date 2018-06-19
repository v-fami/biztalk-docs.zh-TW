---
title: 複雜全域型別衍生 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fbf429d0-64f4-4c43-a5f7-e8af050803b9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee4e6235af62b2c08c08382b897632d15e34e0cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231670"
---
# <a name="complex-global-type-derivation"></a>複雜全域型別衍生
XSD 有兩個類型的繼承：延伸模組與限制。 BizTalk 編輯器 」 可存取此 XSD 功能使用下列兩個**記錄**節點屬性：  
  
-   **基底資料型別**。 此屬性提供所有可做為基底資料型別的全域複雜型別與簡單型別的清單。 複雜全域型別可位在相同的結構描述或任何匯入的結構描述中。  
  
-   **由衍生**。 可使用此屬性來選擇由延伸模組衍生或由限制衍生。 這個屬性會自動設定為**延伸**當您將**基底資料型別**清單中的任何類型的屬性。 如果您將此屬性設定為 **（預設）**，任何在**基底資料型別**移除屬性，停用繼承節點。  
  
> [!NOTE]
>  **內容類型**屬性也設定為自動**ComplexContent**使用的延伸模組或限制衍生時。  
  
 本節將更詳盡說明使用延伸模組和限制機制的複雜型別衍生。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用延伸模組機制的複雜型別衍生](../core/complex-type-derivation-using-the-extension-mechanism.md)  
  
-   [使用限制機制的複雜型別衍生](../core/complex-type-derivation-using-the-restriction-mechanism.md)