---
title: "如何新增圖形至協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes, orchestrations
- orchestrations, shapes
- Construct Message shape [Orchestration Designer]
- Message Assignment shape [Orchestration Designer]
- Scope shape [Orchestration Designer]
ms.assetid: d39eb12c-cdc6-4918-93d9-536db1dfb889
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9fa6634adb20ffcf927da0af6f58e9daa2800ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-shapes-to-orchestrations"></a>如何新增圖形至協調流程
本節描述在您的協調流程中新增及移除圖形的程序。 如需可用圖形的詳細資訊，請參閱[協調流程圖形](../core/orchestration-shapes.md)。  
  
### <a name="to-add-a-shape-to-an-orchestration"></a>若要將圖形新增至協調流程  
  
1.  在工具箱中，在**BizTalk 協調流程**索引標籤上，將圖形的連接線，拖曳到協調流程設計介面上。  
  
     -或者-  
  
2.  以滑鼠右鍵按一下的連接線或圖形預留位置您要加入圖形，指向**插入圖形**，然後按一下您想要新增的圖形名稱。  
  
    > [!NOTE]
    >  尚未完全設定的圖形上會出現「智慧標籤」。  
  
> [!NOTE]
>  **轉換**圖形和**訊息指派**圖形只能存在於**建構訊息**圖形。 如果您加入其中一種圖形以外的協調流程**建構訊息**圖形，它會自動放置於新**建構訊息**圖形。  
  
> [!NOTE]
>  **攔截例外狀況**和**補償**區塊只能存在於下列**範圍**圖形。  
  
### <a name="to-remove-a-shape-from-an-orchestration"></a>若要從協調流程移除圖形  
  
1.  以滑鼠右鍵按一下設計介面上的圖形，然後按一下**刪除**。  
  
     -或者-  
  
2.  選取圖形，然後按**刪除**索引鍵。  
  
## <a name="see-also"></a>另請參閱  
 [建立協調流程](../core/creating-orchestrations.md)