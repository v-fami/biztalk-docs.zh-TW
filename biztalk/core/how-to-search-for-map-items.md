---
title: "如何搜尋對應項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.search
ms.assetid: 3dbb089a-6aa8-4921-a82d-81d3a193e933
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee61bccfae53a79d8fba6bd0aa5af2c537d98270
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-map-items"></a>如何搜尋對應項目
BizTalk 對應工具可讓您搜尋來源結構描述、目的結構描述與格線介面中的項目。 本主題提供如何執行此作業的相關資訊。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
## <a name="to-search-for-items"></a>搜尋項目  
 選取要搜尋的結構描述。 如果選取來源結構描述，BizTalk 對應工具只會在來源結構描述中搜尋。 但是，您可以同時選取來源和目的結構描述。  
  
> [!NOTE]
>  為確認選項，請尋找結構描述或結構描述項目前面的標記。  
  
 ![搜尋對應項目](../core/media/searching-map-items.gif "Searching_map_items")  
  
 在**搜尋**對應工具公用程式功能區上的方塊中，輸入您想要搜尋的項目名稱。 您可以在來源或目的結構描述的節點名稱中，以及運算質的名稱、標籤、註解、輸入或指令碼中搜尋字串。  
  
 當您輸入搜尋字串時，系統會反白符合搜尋條件的物件。 您可以再周遊搜尋結果中使用的箭頭按鍵在鍵盤上或![在清單中向上移動](../core/media/move-up-button.gif "Move_up_button")和![清單中向下移動](../core/media/move-down-button.gif "Move_down_button")公用程式功能區上的圖示。 如果搜尋結果分佈在三個檢視中，會以來源結構描述、關係檢視和目的結構描述的順序顯示搜尋結果。 之後經過搜尋結果，您可以關閉搜尋刪除搜尋字串，或按一下 (![清除對應工具搜尋](../core/media/mapper-search-cancel.gif "Mapper_Search_Cancel")) 搜尋字串旁的圖示。  
  
> [!NOTE]
>  您也可以按 CTRL+M、CTRL+J/CTRL+M、CTRL+K 來前/後周遊搜尋結果。 如需對應工具鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
> [!IMPORTANT]
>  如果在單一對應檢視中看不到關係檢視的搜尋結果，BizTalk 對應工具會顯示指向其他搜尋結果的閃爍箭號。 例如，向上箭號圖示 (![其他搜尋結果方向](../core/media/mapper-search-direction.gif "Mapper_Search_Direction")) 代表有可以向上捲動以檢視其他搜尋結果。 同樣地，若搜尋結果位於不同的對應頁面，則系統會以黃色反白顯示那些頁面的頁面索引標籤。 將滑鼠指標移反白顯示的頁面，在工具提示會顯示在該頁面上的搜尋相符項目數目。 狀態列會顯示搜尋結果。  
  
 ![狀態列顯示搜尋結果](../core/media/searching-map-items-statusbar.jpg "Searching_map_items_statusbar")  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具](../core/using-biztalk-mapper.md)