---
title: 如何最佳化結構描述樹狀結構檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab4ad6b5-5bbd-443b-9041-6cddf9d64735
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aeeddd0893b80c1c7b37b2d0ee5f9f6cd68849d6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22255342"
---
# <a name="how-to-optimize-the-schema-tree-view"></a>如何最佳化結構描述樹狀結構檢視
您可以使用 **相關性檢視** BizTalk 對應工具最佳化來源和/或目標結構描述樹狀結構中。 本主題提供如何執行此作業的指示。  
  
 相關性檢視使用同層級結合 (Sibling Coalescence) 將不相關的結構描述項目摺疊起來，以提供更簡潔的結構描述檢視。 這樣可進一步減少捲動需求，協助您將焦點放在使用結構描述與對應時的需求。  
  
 下圖顯示相關性檢視關閉時的結構描述。 不論節點是否參與了任何關係，結構描述窗格都會顯示所有的節點。  
  
 ![結構描述相關性檢視關閉時](../core/media/off-schema-relevance-view.gif "Off_Schema_Relevance_View")  
  
 按一下![切換至相關性檢視](../core/media/mapper-intellitree.gif "Mapper_IntelliTree")開啟相關性檢視對應工具公用程式功能區上的圖示。 您可以切換到來源與 (或) 目標結構描述的相關性檢視，只要按一下來源來源與 (或) 目標結構描述的相關圖示即可。  
  
 切換到結構描述的相關性檢視時：  
  
-   所有其本身或其子欄位項目沒有相關連結的記錄項目都會呈現摺疊狀態。  
  
-   沒有任何連結的所有後續節點會結合起來，並會取代![聯合隱藏的節點](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On")圖示。 BizTalk 對應工具會尋找至少兩個可以結合的不相關連續節點。 您可以將滑鼠移到圖示上以檢視結合節點的清單。 請注意，infotip 只會列出前三個結合節點的名稱，即使事實上還有其他結合節點也是如此。 按一下即可檢視所有節點![聯合隱藏的節點](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On")圖示。  
  
    > [!NOTE]
    >  如需 infotip 的詳細資訊，請參閱[如何檢視資訊提示和工具提示](../core/how-to-view-infotip-and-tooltip.md)。  
  
## <a name="prerequisites"></a>必要條件  
 此作業需要執行中的 BizTalk 對應工具。  
  
## <a name="to-optimize-the-schema-tree-view"></a>若要最佳化結構描述樹狀結構  
 對應工具公用程式功能區中，開啟來源和 （或） 目標結構描述的相關性檢視，即可分別![切換至相關性檢視](../core/media/mapper-intellitree.gif "Mapper_IntelliTree")圖示。 下圖顯示相關性檢視開啟時的同一個結構描述。 所有不相關的節點會以取代![聯合隱藏的節點](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On")圖示，以提供更簡潔的結構描述檢視。  
  
 ![結構描述相關性檢視時 ON](../core/media/on-schema.gif "On_schema")  
  
 當您展開結合的節點，在來源及/或目的結構描述中![聯合隱藏的節點](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On")變為![聯合節點顯示](../core/media/switchoff-mapper-coalesence.jpg "SwitchOff_Mapper_Coalesence")圖示。  
  
> [!NOTE]
>  您可以按下 CTRL+M、CTRL+E 或 CTRL+M、CTRL+C，分別展開或摺疊來源結構描述中的樹狀結構節點。 同樣地，您可以按下 CTRL+M、CTRL+E 或 CTRL+M、CTRL+C，分別展開或摺疊目的結構描述中的樹狀結構節點。 您也可以分別按下 Ctrl+M、Ctrl+H 或 Ctrl+M、Ctrl+D，分別進行來源或目標結合。 如需對應工具鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具中的增強的功能](../core/using-enhanced-features-in-biztalk-mapper.md)