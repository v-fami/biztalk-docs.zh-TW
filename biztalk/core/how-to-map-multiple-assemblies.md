---
title: "如何對應多個組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies, tracking profiles
- tracking profiles, mapping assemblies
- assemblies, maps
ms.assetid: 136f1943-9643-4551-8b5b-150c4b4bfebe
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20a55b6e88889ccfa36adcac11fe548ab1b25bc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-multiple-assemblies"></a>如何對應多個組件
BizTalk 應用程式可能由多個組件所組成，其中存有 BAM 活動參考的資料項目。 下列程序說明如何將多個組件對應到追蹤設定檔。  
  
### <a name="to-map-multiple-assemblies"></a>對應多個組件  
  
1.  開啟現有的追蹤設定檔或建立新的追蹤設定檔。 如需有關如何建立追蹤設定檔的詳細資訊，請參閱[如何建立追蹤設定檔](../core/how-to-create-a-tracking-profile.md)。  
  
2.  按一下**選取事件來源**按鈕 （位於右窗格中追蹤設定檔編輯器上方）。  
  
3.  選取**選取協調流程排程**從串聯功能表的功能表項目。  
  
4.  選取要繪製協調流程，按一下包含協調流程中的組件的父組件**組件名稱**清單方塊中，然後再按**下一步**。  
  
5.  選取的協調流程中的資料項目來源**協調流程名稱**清單方塊中，然後再按**確定**。  
  
6.  在右窗格中選取資料項目，然後拖曳到左窗格中活動的適當節點。  
  
7.  重複執行步驟 2 至 6 以對應其他組件。  
  
### <a name="to-map-the-second-assembly"></a>對應第二個組件  
  
1.  按一下**選取事件來源**。  
  
2.  選取**選取協調流程排程**從串聯功能表的功能表項目。  
  
3.  選取 [下一步要繪製協調流程，按一下包含協調流程中的組件的父組件**組件名稱**清單方塊中，然後再按**下一步**] 按鈕。  
  
4.  選取的協調流程中的資料項目來源**協調流程名稱**清單方塊中，然後再按**確定**。  
  
5.  在右窗格中選取資料項目，然後拖曳到左窗格中活動的適當節點。  
  
## <a name="see-also"></a>另請參閱  
 [如何對應事件來源](../core/how-to-map-event-sources.md)   
 [建立追蹤設定檔](../core/creating-tracking-profiles.md)