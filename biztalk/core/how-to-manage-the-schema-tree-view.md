---
title: "如何管理結構描述樹狀結構檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97fb7a88-e38a-4abb-93bc-a5be1bd091e6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f84ba68cd515c673daaac2e2ca96bb0e2346ecbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-the-schema-tree-view"></a>如何管理結構描述樹狀結構檢視
與結構描述樹狀結構檢視相關的管理工作可分為四類：變更大小、變更背景色彩與字型、變更警告對話方塊的使用，以及展開和摺疊其樹狀結構。 本主題提供這些不同工作的逐步說明。  
  
### <a name="to-make-the-schema-tree-view-taller-or-shorter"></a>調整結構描述樹狀結構檢視的高度  
  
1.  將滑鼠游標移至 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主要編輯視窗的下邊緣 (此視窗會將結構描述樹狀結構檢視與 XSD 檢視並排顯示)，直到游標變成標準的視窗垂直調整大小圖示。  
  
2.  按住滑鼠左鍵並上下拖曳視窗邊緣。  
  
     透過對整個主要編輯視窗進行垂直大小的重新調整，您已重新垂直調整結構描述樹狀結構檢視的大小。  
  
### <a name="to-make-the-schema-tree-view-wider-or-more-narrow"></a>調整結構描述樹狀結構檢視的寬度  
  
1.  將滑鼠游標移至 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主要編輯視窗中的窗格分割線 (用來分割結構描述樹狀結構檢視與 XSD 檢視)，直到游標變成標準的視窗水平調整大小圖示。  
  
2.  按住滑鼠左鍵並左右拖曳 (調整寬窄) 窗格邊緣。  
  
     透過變更主要編輯視窗相對於 XSD 檢視所分配給結構描述樹狀結構檢視的大小，您已重新水平調整結構描述樹狀結構檢視的大小。  
  
     您也可以透過對整個主要編輯視窗進行水平大小的重新調整，使結構描述樹狀結構檢視變得較寬或較窄。  
  
### <a name="to-change-the-background-color-andor-font-used-by-the-schema-tree-view"></a>變更結構描述樹狀結構檢視使用的背景顏色和 (或) 字型  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]的 **[工具]** 功能表上，按一下 **[選項]**。  
  
2.  在**選項**對話方塊中，按一下 [BizTalk 編輯器] 資料夾中，並有必要，展開**結構描述顯示**類別目錄，按一下加號 （+） 圖示。  
  
3.  使用下拉式色彩選擇器來變更背景色彩和/或字型和 （或)**字型**對話方塊相關聯**結構描述樹狀結構背景色彩**和**結構描述樹狀結構字型**屬性，分別。  
  
     存取**字型**對話方塊中，使用省略符號 (**...**) 按鈕位於右邊**結構描述樹狀結構字型**屬性值方塊。  
  
### <a name="to-change-the-warning-dialogs-used-when-working-in-the-schema-tree-view"></a>變更在結構描述樹狀結構檢視中工作時使用的警告對話方塊  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]的 **[工具]** 功能表上，按一下 **[選項]**。  
  
2.  在**選項**對話方塊中，按一下  **BizTalk 編輯器**資料夾中，如有必要，展開**編輯選項**區段，按一下加號 （+） 圖示。  
  
3.  設定下列屬性的任何**True**或**False**使用存取的個別屬性值方塊右邊的下拉式清單。  
  
    > [!NOTE]
    >  值**True**為預設值，所有三種警告對話方塊選項。  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |**顯示毀損結構警告對話方塊**|當設定為**True**，終結，所以結構描述結構，並可讓您取消破壞性作業之前，會顯示警告對話方塊。|  
    |**顯示編碼警告對話方塊**|當設定為**True**，會顯示一個對話方塊，當您輸入的節點名稱不可以是有效的 xml 編碼，讓您可以取消命名作業，或繼續進行名稱編碼。|  
    |**顯示無效插入對話方塊**|當設定為**True**、 顯示某些節點插入錯誤的警告 對話方塊，並提供選項，了解要如何繼續執行。 可能的節點插入錯誤包括：<br /><br /> -您已建立重複**欄位屬性**具有相同名稱和相同父節點的節點。<br />-您已建立重複**記錄**節點使用相同的名稱和相同父節點，但具有不同的基礎類型。|  
  
### <a name="to-completely-expand-all-or-part-of-the-schema-tree"></a>完全展開或部分展開結構描述樹狀結構  
  
-   選取要完全展開其結構描述樹狀結構的節點。  
  
     選取的節點旁必須有加號 (+) 或減號 (-) 圖示。  
  
     在**BizTalk**功能表上，或在該節點的捷徑功能表，按一下  **展開結構描述節點**。 所選節點下的所有節點都會完全展開。 如果所選節點下的結構描述樹狀結構已經完全展開， **展開結構描述節點**功能表項目會呈現灰色。  
  
    > [!NOTE]
    >  大型且複雜結構描述中，當您按一下**展開結構描述節點**節點上，其中包含複雜型別，結構描述中的某些節點可能會維持在摺疊的狀態。 這是因為此遞迴程序只會展開第一個出現的給定複雜型別， 您必須手動展開之後出現的相同型別。 這個行為的設計目的是要在大型和複雜結構描述中展開節點時，讓效能最佳化。  
  
### <a name="to-completely-collapse-all-or-part-of-the-schema-tree"></a>完全摺疊或部分摺疊結構描述樹狀結構  
  
1.  選取要完全摺疊其結構描述樹狀結構的節點。  
  
     選取的節點旁必須有加號 (+) 或減號 (-) 圖示。  
  
2.  在**BizTalk**功能表上，或在該節點的捷徑功能表，按一下 **摺疊結構描述節點**。  
  
     所選節點下的所有節點都會完全摺疊。  
  
    > [!NOTE]
    >  如果所選節點下的結構描述樹狀結構已經完全摺疊，**摺疊結構描述節點**功能表項目會呈現灰色。  
  
    > [!NOTE]
    >  這項作業不會記得個人在所選節點下做出的節點展開和摺疊設定。 換句話說，當您重新展開已摺疊的節點時，先前的個別設定會遺失，而您必須依逐個節點展開該點下的結構描述樹狀結構，或完全展開。  
  
### <a name="to-expand-a-node-of-the-schema-tree"></a>展開結構描述樹狀結構的節點  
  
-   按一下要展開之節點旁的加號 (+) 圖示。  
  
    > [!NOTE]
    >  就會展開選取的節點。 其底下的節點是展開還是摺疊，視選取的節點當初摺疊的方式，以及先前的展開和摺疊設定而異。  
  
### <a name="to-collapse-a-node-of-the-schema-tree"></a>折疊結構描述樹狀結構的節點  
  
-   按一下要摺疊之節點旁的減號 (-) 圖示。  
  
    > [!NOTE]
    >  就會摺疊選取的節點。  
  
    > [!NOTE]
    >  這項作業會記得個人在所選節點下做出的節點展開和摺疊設定。 換句話說，當您使用加號 (+) 圖示重新展開已摺疊的節點時，先前的個人設定不會遺失，而該節點下的結構描述樹狀結構會回到先前的展開/摺疊狀態。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 編輯器](../core/using-biztalk-editor.md)