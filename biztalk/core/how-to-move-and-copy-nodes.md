---
title: 如何移動和複製節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4f1ec14-c607-4da3-9139-73a61963b819
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a55901e9ba6b27d05dccce0e547df618123ab466
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254766"
---
# <a name="how-to-move-and-copy-nodes"></a>如何移動和複製節點
您可能會遇到需要移動現有節點至結構描述樹狀結構中不同位置的情況。 您也可以在結構描述樹狀結構中複製現有的節點，然後將它貼到不同的位置來節省時間。 本主題提供執行這些工作的逐步解說。  
  
> [!NOTE]
>  BizTalk 編輯器僅支援在結構描述內複製和貼上節點，而不支援在結構描述之間執行這些動作。  
  
### <a name="to-move-a-node-within-a-schema"></a>移動結構描述中的節點  
  
1.  如有必要，展開結構描述樹狀結構以顯示您要移動的節點以及您要將它移動到的位置。 如需有關展開和摺疊結構描述樹狀檢視的詳細資訊，請參閱[管理結構描述樹狀結構檢視](../core/how-to-manage-the-schema-tree-view.md)。  
  
2.  按住您要移動的節點，將它拖曳到樹狀結構中的另一個位置。  
  
> [!NOTE]
>  當您開始在結構描述樹狀結構中往上和往下拖曳時，滑鼠指標會變更為向上、向下或是子箭頭。 此箭頭表示當您釋放滑鼠按鈕時要放置節點的位置，也就是節點之前、節點之後或是做為節點的子系。  
  
#### <a name="to-copy-a-node-within-a-schema"></a>複製結構描述中的節點  
  
1.  以滑鼠右鍵按一下您想要複製，，然後按一下節點**複製**。  
  
2.  以滑鼠右鍵按一下**記錄**節點或群組節點要插入複製的節點，然後按一下**貼上**。  
  
     複製的節點複本放置在的子節點結尾處**記錄**節點或您在步驟 2 中選取的群組節點。  
  
> [!NOTE]
>  您只能在單一結構描述中使用剪下/複製/貼上功能。 換句話說，您不能從某個結構描述複製節點到另一個結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [使用現有的節點](../core/working-with-existing-nodes.md)