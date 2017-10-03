---
title: "如何設定待命圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Listen shape [Orchestration Designer], about Listen shape
- Listen shape [Orchestration Designer], configuring
- Listen shape [Orchestration Designer]
- Listen shape [Orchestration Designer], branching
- configuring [Orchestration Designer], Listen shapes
ms.assetid: 4765dc0a-a30e-4515-83bc-72b4f37268cf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd8f8bbcc08d41430b95a9d177aeb06a5288be4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-listen-shape"></a>如何設定待命圖形
待命動作讓應用程式能在一個或多個連接埠等候數個訊息之一，或是在指定的逾時間隔後停止等候，然後根據結果分支。  
  
 ![](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")  
待命圖形  
  
 您可以視需要盡量新增分支。 您可以將任何其他圖形下方初始放**接收**或**延遲**圖形。  
  
 您可使用啟動接收中**接聽**圖形。 如果的其中一個分支**接聽**圖形包含啟動接收，則所有分支都必須都包含啟動接收，且可以使用不會逾時。 啟動接收必須是每個分支中的第一個動作。  
  
 您可以使用**接聽**圖形至協調流程的分支會根據一或多個事件的發生。 每個分支中的第一個圖形必須是**延遲**或**接收**圖形。 符合其條件的第一個分支 — 的逾時的出現項目**延遲**圖形或接收的訊息**接收**圖形，將會執行。 您可以視需要新增其他分支。  
  
### <a name="to-configure-a-listen-shape"></a>若要設定待命圖形  
  
1.  選取某個分支。  
  
2.  在 [屬性] 視窗中，指定**分支類型**屬性。  
  
     -或者-  
  
     拖曳**延遲**或**接收**圖形拖曳到分支。  
  
### <a name="to-add-a-branch-to-a-listen-shape"></a>若要將分支新增到待命圖形  
  
-   以滑鼠右鍵按一下**接聽**圖形，然後按一下**新待命分支**。  
  
    > [!NOTE]
    >  若要移除的分支**接聽**圖形中，以滑鼠右鍵按一下您想要移除，然後按一下的分支**刪除**。