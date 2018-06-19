---
title: 如何管理檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4a865d7-b319-4264-a085-15f2155bdb2d
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 553e471826cf4744638e7498fd2bb7d52b2e326a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254638"
---
# <a name="how-to-manage-views"></a>如何管理檢視
在開發 BizTalk 對應，您可能想要變更來源或目的結構描述樹狀檢視的大小或格線檢視的大小。 有時候，您可能需要在先前關閉的檢視中開啟對應。 本主題提供這些工作的逐步解說。  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
### <a name="to-make-the-schema-tree-views-or-the-grid-view-taller-or-shorter"></a>若要使結構描述樹狀檢視或格線檢視較高或較矮  
  
1.  移動滑鼠游標至主要編輯視窗的下邊緣 (在格線檢視兩旁會顯示結構描述樹狀檢視)，直到游標變成標準的視窗垂直調整大小圖示。  
  
2.  按住滑鼠左鍵並上下拖曳視窗邊緣。  
  
     透過對整個主要編輯視窗進行垂直大小的重新調整，您已重新垂直調整結構描述樹狀檢視和格線檢視的大小。  
  
### <a name="to-make-the-schema-tree-views-or-the-grid-view-wider-or-more-narrow"></a>若要使結構描述樹狀檢視或格線檢視較寬或較窄  
  
1.  移動滑鼠游標至主要編輯視窗中兩條窗格分割線 (用來分割結構描述樹狀檢視和格線檢視) 的其中之一，直到游標變成標準的視窗水平調整大小圖示。  
  
2.  按住滑鼠左鍵並左右拖曳 (調整寬窄) 窗格邊緣。  
  
     透過變更主要編輯視窗分配給結構描述樹狀檢視的大小，您已重新水平調整結構描述樹狀檢視和格線檢視的大小。  
  
     或者，您也可以透過對整個主要編輯視窗進行水平大小的重新調整，來使結構描述樹狀檢視和格線檢視變得較寬或較窄。  
  
## <a name="remembering-the-current-view-of-mapper"></a>記住對應工具的目前檢視  
 [BizTalk 對應工具] 會記住所有設定，例如縮放比例；公用程式功能區選項的切換狀態，以及連結/運算質的目前對齊方式。  
  
> [!NOTE]
>  如果您在 BizTalk 專案或方案中有多個對應，則會分別記住每個對應的個別詳細資訊。  
  
> [!CAUTION]
>  前一個檢視的設定會儲存在 **\*.suo**檔案。 請確定您沒有在 Visual Studio 中從專案資料夾刪除此檔案。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具命令](../core/using-biztalk-mapper-commands.md)   
 [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)   
 [如何將檢視中選取的對應項目](../core/how-to-bring-selected-map-items-in-view.md)   
 [如何最佳化結構描述樹狀檢視](../core/how-to-optimize-the-schema-tree-view.md)