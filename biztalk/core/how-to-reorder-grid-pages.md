---
title: 如何重新排序格線頁 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.reorderpages
ms.assetid: bbf45501-109f-4333-8d1f-1ad47b010db0
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 622ee8346855e41c722898a59de6dbe3da90c8a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254798"
---
# <a name="how-to-reorder-grid-pages"></a>如何重新排序格線頁
如果您的對應較為複雜，您可以納入多個格線頁，並加以重新命名和重新排序。 本主題包含執行這些作業的逐步指示。  
  
 您可以納入一或多個格線頁，以簡化對應的版面，同時讓對應保持條理、方便讀取。 例如，您可以將所有與標頭資訊相關的連結與運算質放在某個頁面，然後將所有與對應內文相關的連結與運算質放在另一個頁面。 接著，您可以重新命名和重新排序您所建立的格線頁。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-add-and-rename-a-grid-page"></a>新增和重新命名格線頁  
  
1.  頁面索引標籤面板中，以滑鼠右鍵按一下，然後按一下 **新增網頁**。 您會看到對應中插入新頁面。  
  
     ![新增和重新命名格線頁](../core/media/adding-and-renaming-grid-page.gif "Adding_and_renaming_grid_page")  
  
2.  頁面索引標籤面板中，以滑鼠右鍵按一下，然後按一下 **重新命名頁面**。  
  
    > [!TIP]
    >  或者，您可以按兩下現有的頁面索引標籤，或按鍵盤上的 F2。  
  
3.  輸入格線頁的新名稱，然後按 ENTER。  
  
### <a name="to-reorder-grid-pages-using-reorder-map-pages-dialog-box"></a>若要使用重新排序對應頁面對話方塊來重新排序格線頁  
  
1.  頁面索引標籤面板中，以滑鼠右鍵按一下，然後按一下 **重新排序頁面**。  
  
2.  在**重新排序對應頁面**對話方塊中，選取您想要移動的頁面索引標籤，然後按一下向上鍵或向下鍵變更格線頁，相對位置，然後按一下 **確定**。  
  
     ![向上或向下重新排列格線頁移動](../core/media/reorder-map-pages.gif "Reorder_map_pages")  
  
### <a name="to-reorder-grid-pages-using-the-page-tabs-panel"></a>若要使用頁面索引標籤面板來重新排序格線頁  
  
1.  選取您要移動/重新排序的頁面索引標籤。  
  
2.  按住滑鼠鍵，並沿著頁面索引標籤面板移動它。  
  
3.  將頁面索引標籤移至頁面索引標籤面板上想要的位置後，放開滑鼠。  
  
    > [!TIP]
    >  只有在滑鼠游標在兩個頁面索引標籤之間變成垂直線時，才會移動/重新排序頁面。 垂直線表示要將頁面重新排序到的位置。  
  
### <a name="to-delete-a-grid-page"></a>刪除格線頁  
  
1.  選取您想要刪除之頁面的索引標籤。  
  
2.  頁面 索引標籤上按一下滑鼠右鍵，然後按一下**刪除頁面**。 頁面會以無訊息模式刪除。  
  
    > [!IMPORTANT]
    >  如果您不想刪除格線頁，請按 CTRL + Z 復原刪除作業。 如需有關如何復原或重做使用者作業的詳細資訊，請參閱[如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用格線頁](../core/working-with-grid-pages.md)