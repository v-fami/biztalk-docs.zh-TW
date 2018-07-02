---
title: 如何設定相互關聯集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- correlation sets, send activities
- correlation sets, assigning correlation types
- correlation types, correlation sets
- correlation sets, receive activities
- configuring, correlation sets
- correlation sets, configuring
- correlation types, assigning
ms.assetid: 060bf2ba-c173-4dca-a8c4-4c5341e5ceaa
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51c56d7f319023bb0379050452253c65634929c0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968855"
---
# <a name="how-to-configure-correlation-sets"></a>如何設定相互關聯集
若要設定相互關聯集，您可以選取現有的相互關聯類型、建立新的相互關聯類型，或修改現有的相互關聯類型。  
  
### <a name="to-assign-a-correlation-type-to-a-correlation-set"></a>指派相互關聯類型至相互關聯集  
  
- 選取現有的相互關聯類型。  
  
   \- 或 -  
  
   以滑鼠右鍵按一下新的相互關聯類型，然後選取**設定相互關聯屬性**。  
  
   \- 或 -  
  
   按一下省略符號 (**...**) 按鈕**相互關聯**中的屬性**屬性**視窗。  
  
   **相互關聯屬性**對話方塊隨即出現。 新增您要包含在相互關聯集內的屬性。 如果尚未指派相互關聯類型至相互關聯集，便會建立新的相互關聯類型。  
  
  如果相互關聯類型已經存在相互關聯集，而且您新增或移除的屬性**相互關聯屬性**對話方塊中，現有的相互關聯類型將予修改。  
  
#### <a name="to-associate-send-and-receive-activities-with-a-correlation-set"></a>建立傳送及接收活動與相互關聯集的關聯  
  
1.  依序展開**相互關聯集**節點。  
  
2.  從下拉式清單中選取傳送或接收活動。  
  
     \- 或 -  
  
     選取相互關聯集合中**初始相互關聯集**屬性或**沿用相互關聯集**中的屬性**屬性**每個視窗**傳送**或是**接收**您想要相互關聯集相關聯的圖形。  
  
#### <a name="to-disassociate-send-and-receive-activities-from-a-correlation-set"></a>取消傳送及接收活動與相互關聯集的關聯  
  
-   在 **協調流程檢視**視窗中，視需要展開相互關聯集節點，以滑鼠右鍵按一下您想要移除此項目，然後按一下 的活動**刪除**。  
  
     \- 或 -  
  
     清除 相互關聯集合中**初始相互關聯集**屬性或**沿用相互關聯集**中的屬性**屬性**視窗中的每個**傳送**或是**接收**您想要取消與相互關聯集的形狀。  
  
## <a name="see-also"></a>另請參閱  
 [與接收訊息圖形使用篩選器](../core/using-filters-with-the-receive-message-shape.md)   
 [在協調流程中使用相互關聯](../core/using-correlations-in-orchestrations.md)