---
title: 如何移動格線頁之間的關聯性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.movetopage
ms.assetid: 185add4d-c876-44b6-b6e0-71c15a9b7c26
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5737adcb9159568bfea7c7cdde9dff8015b19706
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-a-relationship-between-grid-pages"></a>如何在格線頁之間移動關聯性
大型的對應會包含許多運算質與連結的集合，以致於您無法輕易地識別連結多個運算質的連結。 碰到這類情況時您可能需要將類似的運算質與連結的集合移至不同的格線頁，讓對應更容易為人所解讀。 本主題提供執行此作業的逐步指示。  
  
 您可以透過下列其中一種方式在格線頁之間移動關係 (但僅限於在同一張對應中)：  
  
-   使用**移動到頁面**對話方塊  
  
-   使用內含功能區選取運算質 (與連結) 之拖放功能  
  
> [!IMPORTANT]
>  您可以移動一或多個運算質與其連結。 當您移動關係時，所有與該關係關聯的標籤、註解與常數值 (連同正確的預留位置) 都會跟著一起移動。  
  
> [!IMPORTANT]
>  您無法只將連結拖放至另一個格線頁。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-move-a-relationship-using-move-to-page-dialog-box"></a>若要使用移至頁面對話方塊來移動關係  
  
1.  在對應上，選取要移動的關係所在的格線頁。  
  
2.  以滑鼠右鍵按一下運算質或連結您想要移動，然後按一下 關聯性中的**移動到頁面**。 隨即顯示訊息，說明將會移動所有選取的對應項目以及相關的連結和運算質。 按一下 **[確定]**。  
  
    > [!NOTE]
    >  若要停用快顯訊息，在 Visual Studio 功能表中，移至**工具**，按一下 **選項**，按一下  **BizTalk 對應工具**，按一下 **一般**，然後取消核取**移至頁面**選項。 如需一般選項的詳細資訊，請參閱[如何自訂 BizTalk 對應工具中的一般設定](../core/how-to-customize-general-settings-in-biztalk-mapper.md)。  
  
    > [!TIP]
    >  或者，您可以按 CTRL + M、 CTRL + M 開啟**移動到頁面** 對話方塊。 如需對應工具快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
     ![將選取的關聯性移至新頁面](../core/media/moving-a-functoid-new.gif "Moving_a_functoid_new")  
  
3.  在**移動到頁面**對話方塊方塊中，選取您想要移動關聯性，然後按一下目標格線頁**確定**。  
  
    > [!NOTE]
    >  您也可以建立新的頁面，選取 **\*（加入新的頁面）**，然後按一下**確定**。  
  
    > [!NOTE]
    >  或者，您也可以按 CTRL+M、CTRL+A 在對應中新增格線頁。 如需對應工具快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
     ![選取目標格線頁](../core/media/moving-a-functoid-step4.gif "Moving_a_functoid_Step4")  
  
     選取的運算質/連結 (連同相關的運算質與連結) 會一起移至新的格線頁。 下圖說明如何將選取的關係 (位於第 3 頁) 移至第 1 頁。  
  
     ![選取的關聯性移至新頁面](../core/media/moving-a-functoid-new2.gif "Moving_a_functoid_new2")  
  
### <a name="to-move-a-relationship-using-drag-and-drop"></a>若要使用拖放方式來移動關係  
  
1.  在對應上，選取要移動的關係所在的格線頁。  
  
2.  選取要移至另一個格線頁的運算質 (和連結)。 這會遞迴選取所有連接至選取範圍內所有運算質的連結。  
  
3.  將選取範圍拖曳至要將關係移至的頁面 (在頁面索引標籤上)。  
  
    > [!WARNING]
    >  在您執行步驟 4 之前，請不要放開滑鼠。  
  
4.  目標格線頁變成焦點時 (在上圖中，第一頁具有焦點)，請在格線頁的空儲存格上放下選取範圍。 這時選取的關係會移至新的格線頁。  
  
## <a name="see-also"></a>另請參閱  
 [使用格線頁](../core/working-with-grid-pages.md)