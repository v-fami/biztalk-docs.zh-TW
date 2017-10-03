---
title: "如何複製、 剪下及貼上連結與運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80b4792a-5ff6-4603-96cd-b3d3d530c12f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eec0ddc164af936e1c3739e4da167753a6e58c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-cut-and-paste-links-and-functoids"></a>如何複製、剪下與貼上連結和運算質
「BizTalk 對應工具」中的複製/剪下/貼上功能可讓人重複使用關係。 本主題提供在對應中複製、剪下及貼上運算質和/或連結的逐步指示。  
  
 當您要重複使用一組運算質和/或連結時，可以使用複製/貼上功能。 此外，當您要將選取範圍從現有位置移除並移到新位置時，可以使用剪下/貼上功能。  
  
> [!IMPORTANT]
>  您是否覺得剪下/貼上功能與移動功能很類似？ 有一個地方不同。 當您選取剪下時，只有選取範圍中的運算質和/或連結會自來源格線頁中移除。 但是當您選取移動時，關係中的所有運算質和連結 (不論選取範圍為何) 都會依照遞迴結構自來源格線頁中移除。 如需移動關係的詳細資訊，請參閱[如何移動關係格線頁之間](../core/how-to-move-a-relationship-between-grid-pages.md)。  
  
 當您複製/剪下一組運算質和/或連結時，會保留與該集合關聯的運算質、標籤、註解和常數值 (以及正確的預留位置)。  
  
 您只可以複製/剪下這些對應項目：  
  
-   從來源到目標結構描述的連結。  
  
-   從運算質到結構描述節點的連結 (只有在同時選取「運算質」和連結時)。  
  
-   從運算質到運算質的連結 (只有在同時選取兩個運算質和之間的連結時)。  
  
 您可以從下列位置複製/剪下運算質和/或連結：  
  
-   同一個對應格線頁內  
  
-   同一個對應中的不同格線頁之間  
  
-   同一個 Visual Studio 執行個體中的不同對應之間  
  
-   不同的 Visual Studio 執行個體之間  
  
 您可以復原或重做剪下與貼上作業。 如需詳細資訊，請參閱[如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。  
  
 此外，在貼上連結時，您還必須考慮下列幾點：  
  
-   若要貼上來源與目標結構描述之間的連結，目前對應 (要貼上連結的地方) 必須包含來源節點和目標節點，而且這個來源節點和目標節點的 XPath 必須與所貼連結之來源節點和目標節點的 XPath 相同。  
  
-   若要貼上來源與目標結構描述之間的連結，上述來源與目標節點之間必須沒有現有連結。  
  
-   若要貼上從運算質至目標結構描述的連結，目標節點的 XPath 必須與所貼連結之目標節點的 XPath 相同。  
  
-   若要貼上從來源結構描述至運算質的連結，來源節點的 XPath 必須與所貼連結之來源節點的 XPath 相同。  
  
> [!NOTE]
>  當您選取多個項目 (連結和/或運算質) 以至於無法剪下/複製部分項目時，則在執行剪下/複製命令時，Visual Studio 中的狀態列會顯示「無法剪下/複製部分選取的項目」警告訊息。 訊息也會顯示相關的詳細資訊。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-copy-and-paste-a-relationship"></a>若要複製並貼上關係  
  
1.  在 [方案總管] 中開啟 BizTalk 專案，然後按兩下對應以在 BizTalk 對應工具中加以開啟。  
  
2.  選取運算質和/或您要複製的連結。  
  
    > [!TIP]
    >  您可以選擇按住 CTRL 鍵，然後選取想要的運算質和/或連結，或者是將滑鼠拖曳過這些連結，以形成矩形選取範圍。  
  
    > [!NOTE]
    >  您可以使用「功能區選取」作業來選取多個連結和 (或) 運算質。 如需詳細資訊，請參閱[如何選取多個連結和運算質](../core/how-to-select-multiple-links-and-functoids.md)。  
  
3.  以滑鼠右鍵按一下選取範圍。 然後按一下 **複製**。 或者，您可以按鍵盤上的 CTRL+C。  
  
    > [!NOTE]
    >  如需鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
4.  將游標放在您想貼上選取範圍的位置。  
  
5.  在格線頁中，按一下滑鼠右鍵，然後按一下**貼上**。 或者，您可以選取並按鍵盤上的 CTRL+V。 選取範圍的複本會出現在新的位置。  
  
### <a name="to-cut-and-paste-a-relationship"></a>若要剪下並貼上關係  
  
1.  在 [方案總管] 中開啟 BizTalk 專案，然後按兩下對應以在 BizTalk 對應工具中加以開啟。  
  
2.  選取運算質和/或您要剪下的連結。  
  
    > [!TIP]
    >  您可以選擇按住 CTRL 鍵，然後選取想要的運算質和/或連結，或者是將滑鼠拖曳過這些連結，以形成矩形選取範圍。  
  
    > [!NOTE]
    >  您可以使用「功能區選取」作業來選取多個連結和 (或) 運算質。 如需詳細資訊，請參閱[如何選取多個連結和運算質](../core/how-to-select-multiple-links-and-functoids.md)。  
  
3.  選取範圍，以滑鼠右鍵按一下，然後按一下**剪下**。 或者，您可以按鍵盤上的 CTRL+X。  
  
    > [!NOTE]
    >  如需鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
4.  將游標放在您想貼上選取範圍的位置。  
  
5.  在格線頁中，按一下滑鼠右鍵，然後按一下**貼上**。 或者，您可以選取並按鍵盤上的 CTRL+V。 選取範圍就會從現有位置中刪除，並出現在新的位置。