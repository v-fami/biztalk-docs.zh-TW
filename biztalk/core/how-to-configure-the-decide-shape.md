---
title: "如何設定 「 決定 」 圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Decide shape [Orchestration Designer]
- Decide shape [Orchestration Designer], configuring
- Decide shape [Orchestration Designer], branching
- configuring [Orchestration Designer], Decide shapes
ms.assetid: 70910861-3834-49e7-ab1e-d62730ea2a95
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a22368134e2c1a0d8deb277e186792158a7c2dd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-decide-shape"></a>如何設定決定圖形
![](../core/media/ebiz-orch-decide.gif "ebiz_orch_decide")  
決定圖形  
  
 每個分支**決定**圖形，除了**else**分支，與它有關聯的規則。 您可以使用「BizTalk 運算式編輯器」，在規則中建立布林值運算式，針對該分支執行進行評估。 因為**else**分支表示否定上一個分支的布林值運算式，它沒有與它相關聯的運算式。  
  
 在規則或**else**子句中，分支**決定**圖形可以包含額外圖形，就像協調流程的任何其他部分一樣。  
  
### <a name="to-configure-a-decide-shape"></a>若要設定決定圖形  
  
1.  如果看不到 BizTalk 運算式編輯器，以滑鼠右鍵按一下規則，然後按一下**編輯布林值運算式**，或在 屬性 視窗中，按一下**省略**(**...**) 按鈕**運算式**屬性。  
  
2.  在 BizTalk 運算式編輯器，建立除了每個分支的布林值運算式**Else**分支。 例如，  
  
    ```  
    myMessage.Total > 1000  
    myObject.IsValid()  
    myMessage.VIP == true  
    ```  
  
### <a name="to-add-a-branch-to-a-decide-shape"></a>若要將分支加入至決定圖形  
  
1.  以滑鼠右鍵按一下**決定**圖形，，然後按一下**新規則分支**。  
  
     -或者-  
  
2.  在兩個現有的分支之間拖曳新的圖形。  
  
    > [!NOTE]
    >  若要移除的分支**決定**圖形中，以滑鼠右鍵按一下您想要移除，然後按一下的分支**刪除**，或選取規則分支，然後按**刪除**索引鍵。