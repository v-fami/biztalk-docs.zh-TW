---
title: "如何復原或重做使用者作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cb3708e-a9c2-4795-aba0-9c6d9635e08c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8358fc1624346b90d98fd1f1707dd2bfb02446dd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-undo-or-redo-user-operations"></a>如何復原或重做使用者作業
BizTalk 對應工具提供的另一項使用性輔助工具是支援復原/取消復原功能。 如果您不滿意所做的修改，或不慎做了錯誤的變更，您可以使用復原功能逐步回復至先前的原始狀態，然後再繼續修改。 取消復原功能可讓您重新套用已復原的編輯動作。 此主題說明可復原/取消復原之作業的相關資訊。  
  
> [!IMPORTANT]
>  只有在對應上至少執行一個編輯作業時，才能夠復原作業。 除非已使用復原命令，否則無法使用取消復原命令。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
## <a name="what-can-you-undoredo"></a>您可以復原/取消復原什麼項目？  
 您可以復原/取消復原所有編輯作業。 可復原/取消復原的作業如下所示：  
  
-   剪下/複製/貼上運算質和/或連結。  
  
     只是選取和複製任意數目的項目 (連結/運算質)，並無法復原或重做它們。 複製函數不會變更對應上的任何項目。  
  
    > [!NOTE]
    >  如需如何剪下/複製/貼上運算質的資訊，請參閱[如何複製、 剪下和貼上運算質](../core/how-to-copy-cut-and-paste-a-functoid.md)。 如需如何剪下/複製/貼上運算質和連結的詳細資訊，請參閱[如何剪下、 複製和貼上連結和運算質](../core/how-to-copy-cut-and-paste-links-and-functoids.md)。  
  
-   連結來源節點與目標節點或連結來源節點與運算質，連結運算質與另一個運算質或連結運算質與目標節點  
  
-   刪除運算質和/或連結  
  
-   將選取的連結與運算質移至另一個格線頁  
  
-   新增、移動、重新排序或刪除格線頁  
  
    > [!NOTE]
    >  如需加入資訊，移動、 重新排列或刪除格線頁，請參閱[如何重新排序格線頁](../core/how-to-reorder-grid-pages.md)。  
  
-   在建立對應時選取來源與目的結構描述  
  
-   取代來源/目的結構描述  
  
    > [!NOTE]
    >  如需如何取代來源/目的結構描述資訊，請參閱[如何取代結構描述](../core/how-to-replace-schemas.md)。  
  
-   設定運算質的輸入參數  
  
    > [!NOTE]
    >  如需詳細資訊，請參閱[如何設定運算質輸入參數](../core/how-to-configure-functoid-input-parameters.md)。  
  
-   設定/編輯連結的標籤  
  
    > [!NOTE]
    >  如需詳細資訊，請參閱[如何標示連結](../core/how-to-label-a-link.md)。  
  
-   設定/編輯運算質的標籤和 (或) 註解  
  
    > [!NOTE]
    >  如需詳細資訊，請參閱[如何加上標籤與註解的運算質](../core/how-to-label-and-comment-a-functoid.md)。  
  
-   對應工具格線的 [略過連結的命名空間] 和 [指令碼類型優先順序] 屬性。  
  
-   將連結的其中一端從某個節點或運算質拖曳至另一個節點或運算質，以取代連結。  
  
    > [!NOTE]
    >  如需詳細資訊，請參閱[如何建立連結](../core/how-to-create-links.md)。  
  
-   執行中的多個修改**設定\<運算質\>運算質**對話方塊中，會被視為單一作業。  
  
-   拖曳對應工具格線內的運算質和 (或) 連結。  
  
    > [!NOTE]
    >  如需詳細資訊，請參閱[如何移動關係格線頁之間](../core/how-to-move-a-relationship-between-grid-pages.md)。  
  
## <a name="how-can-you-undoredo-any-operation"></a>如何復原/取消復原任何作業？  
 您可以使用下列其中一種方法來復原/取消復原作業：  
  
-   從 Visual Studio**編輯**功能表。  
  
-   按一下工具列上的復原與取消復原圖示。  
  
-   按下 CTRL+Z 復原，按下 CTRL+Y 取消復原。  
  
## <a name="see-also"></a>請參閱  
 [使用格線頁](../core/working-with-grid-pages.md)