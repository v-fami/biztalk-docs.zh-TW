---
title: 如何複製、 剪下和貼上運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 825847e4-87db-4b40-8e5d-5b5b1c79c6de
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9af3662fb866eb09c1dcb2516279ca097cc998f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249526"
---
# <a name="how-to-copy-cut-and-paste-a-functoid"></a>如何複製、剪下與貼上運算質
「BizTalk 對應工具」中的複製/剪下/貼上功能可讓人重複使用運算質。 在對應中，您可以將某個格線頁中的一或多個運算質複製、剪下及貼至另一個格線頁。 本主題提供執行這些作業的逐步指示。  
  
 當您要重複使用運算質時，可以使用複製/貼上功能。 此外，當您要將運算質從現有位置移除並移到新位置時，可以使用剪下/貼上功能。  
  
> [!IMPORTANT]
>  當您選擇複製運算質時，會同時複製運算質、其標籤、註解、常數輸入及預留位置索引。 同樣地，當您選擇剪下運算質時，會同時剪下運算質、其標籤、註解、常數輸入及預留位置索引。 但是，當您貼上 (在選擇剪下之後) 選取範圍時，只會保留運算質並且會刪除被遺棄的連結。 標籤、註解、常數輸入和預留位置索引並不會保留。  
  
 如果您只選取已連結至其他運算質或結構描述節點的運算質，則只會剪下或複製該運算質，而不會同時剪下或複製連結。 如果您剪下已連結至對應中其他運算質或是結構描述節點的運算質，則會刪除通往所剪下運算質的連結。  
  
 您可以從下列位置複製/剪下運算質：  
  
-   同一個對應格線頁內  
  
-   同一個對應中的不同格線頁之間  
  
-   兩個 Visual Studio 執行個體之間  
  
 您可以復原或重做剪下與貼上作業。 如需詳細資訊，請參閱[如何復原或重做使用者作業](../core/how-to-undo-or-redo-user-operations.md)。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-copy-and-paste-a-functoid"></a>若要 複製並貼上運算質  
  
1.  在 [方案總管] 中開啟 BizTalk 專案，然後按兩下對應以在 BizTalk 對應工具中加以開啟。  
  
2.  選取您要複製的 運算質 。 若要選取多個運算質，請按其中一個運算質，按住 CTRL 鍵，然後按一下其餘運算質。  
  
    > [!NOTE]
    >  您可以使用「功能區選取」作業來選取多個連結和 (或) 運算質。 如需詳細資訊，請參閱[如何選取多個連結和運算質](../core/how-to-select-multiple-links-and-functoids.md)。  
  
3.  選取範圍，以滑鼠右鍵按一下，然後按一下**複製**。 或者，您可以按一下**複製**從 Visual Studio**編輯**功能表或鍵盤上的按下 CTRL + C。  
  
    > [!NOTE]
    >  如需鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
4.  將游標放在您想貼上運算質的位置。  
  
5.  在格線頁中，按一下滑鼠右鍵，然後按一下**貼上**。 或者，您可以按一下**貼上**從 Visual Studio**編輯**功能表或鍵盤上的按 CTRL + V。 所 選取運算質或運算質群組的複本會出現在新的位置 。  
  
### <a name="to-cut-and-paste-a-functoid"></a>若要 剪下並貼上運算質  
  
1.  在 [方案總管] 中開啟 BizTalk 專案，然後按兩下對應以在 BizTalk 對應工具中加以開啟。  
  
2.  選取您要剪下的運算質。 若要選取多個運算質，請按其中一個運算質，按住 CTRL 鍵，然後按一下其餘運算質。  
  
3.  選取範圍，以滑鼠右鍵按一下，然後按一下**剪下**。 或者，您可以按一下**剪下**從 Visual Studio**編輯**功能表或鍵盤上的按下 CTRL + X。  
  
    > [!NOTE]
    >  如需鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
4.  將游標放在您想貼上運算質的位置。  
  
5.  在格線頁中，按一下滑鼠右鍵，然後按一下**貼上**。 或者，您可以按一下**貼上**從 Visual Studio**編輯**功能表或鍵盤上的按 CTRL + V。 所 選取運算質或運算質群組會自現有位置刪除，並出現在新的位置 。  
  
## <a name="see-also"></a>另請參閱  
 [使用運算質建立更複雜的對應](../core/using-functoids-to-create-more-complex-mappings.md)