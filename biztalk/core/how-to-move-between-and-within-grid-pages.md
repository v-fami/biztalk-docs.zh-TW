---
title: 如何移動之間以及在格線頁內 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.gridpreview
ms.assetid: 9553d9ad-1c57-4e73-bb77-0eaaa172090c
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928e9540c91e33b8e5027bd33757beeff62b145b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254318"
---
# <a name="how-to-move-between-and-within-grid-pages"></a>如何在格線頁之間以及在格線頁中移動
若您的對應很複雜，您很可能無法同時在單一格線頁內看見所有的連結與運算質。 這表示您必須能夠在格線頁內捲動。 而且，若您的對應具有多個格線頁，則您必須能夠在格線頁之間移動。 本主題提供這些作業的逐步指示。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-pan-within-a-grid-page"></a>若要在格線頁內移動瀏覽  
  
1.  在對應工具公用程式功能區中，按一下 ![捲動對應工具使用這個按鈕](../core/media/mapper-pan-hand.gif "Mapper_Pan_Hand")圖示。  
  
2.  按住滑鼠左鍵，然後將滑鼠往您要捲動對應的方向拖曳。  
  
    > [!NOTE]
    >  若要切換到標準模式，請按一下![捲動對應工具使用這個按鈕](../core/media/mapper-pan-hand.gif "Mapper_Pan_Hand")圖示。  
  
## <a name="to-scroll-within-a-grid-page-using-keyboard"></a>若要使用鍵盤在格線頁內捲動  
 按一下格線介面的任何位置使格線頁成為焦點。 然後，使用鍵盤的上下左右鍵，往您想要的方向捲動格線頁。 您可以一次移動一個方格資料格。  
  
 \-或者-  
  
 按一下格線介面的任何位置使格線頁成為焦點。 然後，使用鍵盤上的 Page Up / Page Down 按鍵捲動格線頁。  
  
## <a name="to-scroll-within-a-grid-page-using-mouse"></a>若要使用滑鼠在格線頁內捲動  
 滑鼠指標移到格線頁，並旋轉滑鼠滾輪上下移動對應。  
  
> [!NOTE]
>  您無法使用滑鼠在對應上左右移動。  
  
 或者，您可以移動滑鼠指標到邊緣或角落的格線頁中您想要捲動的方向。 游標會變更為箭號。 按住左鍵格線頁內瀏覽。  
  
### <a name="to-scroll-within-a-grid-page-by-using-the-grid-preview"></a>使用預覽格線在格線頁內捲動  
  
1.  在**BizTalk**功能表上，按一下 **預覽格線**。  
  
    > [!NOTE]
    >  您可以也在格線頁背景，按一下滑鼠右鍵，然後按一下**預覽格線**從捷徑功能表。 或者，您也可以按下鍵盤的 CTRL+M、CTRL+G。 如需對應工具鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
2.  在**預覽格線**對話方塊方塊中，將定位器方格拖曳至新位置。 當您移動定位器方格時，顯示的格線頁就會隨著捲動。  
  
    > [!NOTE]
    >  當巡覽具有許多散佈區域廣泛的運算質與連結的大型格線頁時，預覽格線就非常有用。  
  
     ![預覽格線](../core/media/gridpreview.gif "GridPreview")  
  
## <a name="to-zoom-the-grid-page"></a>若要縮放格線頁  
 拖曳縮放滑桿，以縮小或放大您正在使用的格線頁。 您可以縮小來查看夠小，以致於無法納入在完整的格線頁。 相反地，您可以放大以取得一部分的格線頁的特寫檢視。  
  
 ![拖曳來放大或縮小](../core/media/zoom-gridpage.gif "Zoom_gridpage")  
  
### <a name="to-move-between-grid-pages"></a>在格線頁之間移動  
  
1.  使用**移至最左邊**，**左移**，**右移**，和**移至最右邊**方格顯示索引標籤底部的箭號，顯示您要移動的格線頁名稱。  
  
     ![在地圖格線頁之間移動](../core/media/move-between-grid-pages.gif "Move_between_grid_pages")  
  
2.  按一下您要移往的目的格線頁索引標籤。  
  
    > [!TIP]
    >  或者，您可以以滑鼠右鍵按一下任何位置的區域中其中**移至最左邊**，**左移**，**右移**，和**移至最右邊**顯示箭號。 從內容功能表按一下您要移往的目的頁面。  
  
## <a name="see-also"></a>另請參閱  
 [使用格線頁](../core/working-with-grid-pages.md)