---
title: 如何設定平行動作圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Parallel Actions shape [Orchestration Designer], Terminate shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer], synchronizing data access
- Parallel Actions shape [Orchestration Designer]
- configuring [Orchestration Designer], Parallel Actions shapes
- Parallel Actions shape [Orchestration Designer], branching
- Parallel Actions shape [Orchestration Designer], about Parallel Actions shape
- Terminate shape [Orchestration Designer], Parallel Actions shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer], configuring
ms.assetid: 396d6182-f5dd-4aab-9edc-92efe236fd3e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 125d479a09eefb6771a884d2cddbfa98f34aeb36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247798"
---
# <a name="how-to-configure-the-parallel-actions-shape"></a>如何設定平行動作圖形
![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")  
平行動作圖形  
  
> [!CAUTION]
>  如果您將放入**Terminate**圖形放**平行動作**圖形，並包含分支**終止**執行時，在執行個體完成立即不論其他分支是否完成執行。 取決於您的設計，在此情況下的結果可能會無法預料。  
  
## <a name="synchronization-of-data-access"></a>資料存取的同步處理  
 可能的多個分支**平行動作**圖形會嘗試存取相同的資料。 為了避免錯誤，請將存取資料的任何圖形都放置在同步的範圍內。 您可以指定的屬性中**範圍**圖形是同步或非同步。 如需詳細資訊，請參閱[範圍](../core/scopes.md)。  
  
#### <a name="to-add-a-branch-to-a-parallel-actions-shape"></a>若要將分支新增到平行動作圖形  
  
1.  以滑鼠右鍵按一下**平行動作**圖形，，然後按一下**新平行分支**。  
  
     -或者-  
  
2.  在兩個現有的分支之間拖曳新的圖形。  
  
> [!NOTE]
>  若要移除的分支**平行動作**圖形中，以滑鼠右鍵按一下您想要移除，然後按一下的分支**刪除**。