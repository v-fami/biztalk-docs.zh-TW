---
title: 對等節點和其子節點 |Microsoft Docs
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
ms.openlocfilehash: 82c58b477130431ce2b115cb141af759b6614b57
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012047"
---
# <a name="equivalent-nodes-and-their-child-nodes"></a>對等節點和其子節點

## <a name="overview"></a>概觀
**\<相等\>** 節點及其子節點用於結構描述樹狀結構顯示出現的複雜資料型別多型。 當您從其他複雜資料型別衍生一個複雜資料型別時，在 XSD 中的多型可以讓這些資料型別中的任何一個發生在已指定基底複雜資料型別之位置的執行個體訊息中。 結構描述驗證期間的多個可能的複雜資料型別其中一個允許在特定位置的事實會隱含地表示相關聯的基底複雜資料型別名稱**基底**屬性**延伸模組**或是**限制**衍生的複雜資料類型的項目。 若要讓此多型結構描述樹狀結構中較明顯**\<相等\>** 節點及其子節點會明確地顯示。  

 **\<相等\>** 節點會顯示為子節點的項目之基底複雜資料型別，指出有可能會在該位置執行個體中發生的多個複雜資料型別訊息。 子節點**\<相等\>** 節點會顯示的值為**名稱**屬性的對應**complexType**多型，並顯示在角括弧內之 XSD 表示法中的項目 (\<名稱\>)。  

 **\<相等\>** 節點和其子系各有與其相關聯的只有兩個屬性：  

-   **\<對等\>** 節點：**節點名稱**和**基底型別**

-   子節點：**節點名稱**和**衍生型別**

這些屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="xsd-representation"></a>XSD 表示法  
 沒有任何直接的 XSD 表示法**\<相等\>** 節點及其子系。 此節點用於結構描述樹狀結構中，使複雜資料型別多型更容易觀察。  

## <a name="see-also"></a>另請參閱  
- [BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md)   
- [節點屬性](../core/node-properties.md)   
- **Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
- [如何設定節點屬性](../core/how-to-set-node-properties.md)
