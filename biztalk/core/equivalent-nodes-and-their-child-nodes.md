---
title: 對等節點和及其子節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a85c6a1-6121-4849-b958-7c4bd1c7c552
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05c5603cf1882aa7b262ecc5393a9d91dc93da10
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970804"
---
# <a name="equivalent-nodes-and-their-child-nodes"></a>對等節點和及其子節點

## <a name="overview"></a>概觀
**\<相等\>** 節點及其子節點用於結構描述樹狀結構顯示出現的複雜資料型別多型。 當您從其他複雜資料型別衍生一個複雜資料型別時，在 XSD 中的多型可以讓這些資料型別中的任何一個發生在已指定基底複雜資料型別之位置的執行個體訊息中。 結構描述驗證期間的特定位置允許多個可能複雜資料類型的其中一個的事實會隱含地表示相關聯的基底複雜資料型別名稱**基底**屬性**延伸**或**限制**衍生的複雜資料型別的元素。 若要讓此多型更明顯的結構描述樹狀目錄中， **\<相等\>** 節點及其子節點會明確地顯示。  
  
 **\<相等\>** 節點會顯示為子節點的項目之基底複雜資料型別，表示可能會在該位置執行個體中發生多個複雜資料型別訊息。 子節點**\<相等\>** 節點會顯示的值為**名稱**屬性對應**complexType**多型，顯示在角括號內之 XSD 表示法中的項目 (\<名稱\>)。  
  
 **\<相等\>** 節點和其子系每個沒有與其相關聯的只有兩個屬性：  
  
-   **\<對等\>** 節點：**節點名稱**和**基底型別**
  
-   子節點：**節點名稱**和**衍生型別**

這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="xsd-representation"></a>XSD 表示法  
 沒有直接的 XSD 表示法的**\<相等\>** 節點及其子系。 此節點用於結構描述樹狀結構中，使複雜資料型別多型更容易觀察。  
  
## <a name="see-also"></a>請參閱  
-  [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
-  [節點屬性](../core/node-properties.md)   
-  **Sequence 群組節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
-  [如何設定節點屬性](../core/how-to-set-node-properties.md)