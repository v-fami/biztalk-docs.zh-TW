---
title: 如何設定相互關聯集 |Microsoft 文件
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
ms.openlocfilehash: 52bcb0216fc24e14107c7632df97671b64f2ac1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248166"
---
# <a name="how-to-configure-correlation-sets"></a>如何設定相互關聯集
若要設定相互關聯集，您可以選取現有的相互關聯類型、建立新的相互關聯類型，或修改現有的相互關聯類型。  
  
### <a name="to-assign-a-correlation-type-to-a-correlation-set"></a>指派相互關聯類型至相互關聯集  
  
-   選取現有的相互關聯類型。  
  
     \-或者-  
  
     以滑鼠右鍵按一下新的相互關聯類型，然後選取**設定相互關聯屬性**。  
  
     \-或者-  
  
     按一下省略符號 (**...**) 上的按鈕**相互關聯**中的屬性**屬性**視窗。  
  
     **相互關聯屬性**對話方塊隨即出現。 新增您要包含在相互關聯集內的屬性。 如果尚未指派相互關聯類型至相互關聯集，便會建立新的相互關聯類型。  
  
 如果相互關聯類型已經存在相互關聯集，而且您加入或移除屬性**相互關聯屬性**對話方塊中，現有的相互關聯類型將予修改。  
  
#### <a name="to-associate-send-and-receive-activities-with-a-correlation-set"></a>建立傳送及接收活動與相互關聯集的關聯  
  
1.  展開**相互關聯集**節點。  
  
2.  從下拉式清單中選取傳送或接收活動。  
  
     \-或者-  
  
     選取相互關聯集在**初始化相互關聯集**屬性或**沿用相互關聯集**屬性**屬性**每個視窗**傳送**或**接收**您想要與相互關聯集關聯的圖形。  
  
#### <a name="to-disassociate-send-and-receive-activities-from-a-correlation-set"></a>取消傳送及接收活動與相互關聯集的關聯  
  
-   在**協調流程檢視**視窗中，視需要展開相互關聯集節點，以滑鼠右鍵按一下您想要移除，然後按一下 的活動**刪除**。  
  
     \-或者-  
  
     清除相互關聯集在**初始化相互關聯集**屬性或**沿用相互關聯集**屬性**屬性**每個視窗**傳送**或**接收**您要取消與相互關聯集的形狀。  
  
## <a name="see-also"></a>另請參閱  
 [使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md)   
 [協調流程中使用的相互關聯](../core/using-correlations-in-orchestrations.md)