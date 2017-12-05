---
title: "控制執行個體的節點訊息結構和變化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af8e6ce-282d-4318-a538-046b423ef033
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baa82def3f62c6a603ef67e098e53b48a49013a3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="nodes-that-control-instance-message-structure-and-variations"></a>控制執行個體訊息結構與變化的節點
您用來在 [BizTalk 編輯器] 中建立結構描述之部分類型的節點可以控制執行個體訊息的結構和其中的變化。 您使用**Sequence 群組**節點，以指定的項目序列必須發生在執行個體訊息中的對應位置的特定順序。 您使用**Choice 群組**節點，以指定的項目集合中的一個項目可能會發生在執行個體訊息中對應的位置。 您使用**All 群組**節點，以指定的所有指定的項目可以發生在任何順序，但是只能出現一次，在執行個體訊息中對應的位置。 **\<對等\>**節點和及其子節點會顯示在結構描述樹狀結構，表示執行個體訊息中以衍生為基礎的多型的位置生效，允許其中許多相關的複雜資料類型會出現在執行個體訊息中對應的位置。  
  
 本節其餘部分提供此節點類別的其他相關資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Sequence 群組節點](../core/sequence-group-nodes.md)  
  
-   [Choice 群組節點](../core/choice-group-nodes.md)  
  
-   [All 群組節點](../core/all-group-nodes.md)  
  
-   [\<對等\>節點和及其子節點](../core/equivalent-nodes-and-their-child-nodes.md)