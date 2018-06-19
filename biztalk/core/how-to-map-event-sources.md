---
title: 如何將事件來源對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, alerts
- orchestrations, schedules
- events, mapping sources
- orchestrations, tracking profiles
- events, orchestration schedules
- tracking profiles, orchestrations
- tracking profiles, alerts
- alerts, tracking profiles
- alerts, BAM
- tracking profiles, mapping event sources
- events, tracking profiles
ms.assetid: 507f1624-2cd8-4960-8c63-7797ab22519e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 588a394fb3404872554fc786efa3fe24fdd9b47a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253886"
---
# <a name="how-to-map-event-sources"></a>如何對應事件來源
您可以對應事件來源，以取得 BAM 追蹤用來產生警示之資料項目的存取權。  
  
> [!NOTE]
>  您可以對應四種不同的事件來源類型的資料項目： 協調流程排程、 訊息內容、 內容屬性或傳訊屬性。 本主題中的步驟說明如何從協調流程排程對應資料項目。  
  
### <a name="to-map-an-orchestration-schedule-as-an-event-source"></a>若要對應協調流程排程做為事件來源  
  
1.  開啟現有的追蹤設定檔或建立新的追蹤設定檔。 如需有關如何建立追蹤設定檔的詳細資訊，請參閱[如何建立追蹤設定檔](../core/how-to-create-a-tracking-profile.md)。  
  
2.  按一下**選取事件來源**按鈕 （位於右窗格中追蹤設定檔編輯器上方）。  
  
3.  選取**選取協調流程排程**從串聯功能表的功能表項目。  
  
4.  選取要繪製協調流程，按一下包含協調流程中的組件的父組件**組件名稱**清單方塊中，然後再按**下一步**。  
  
     ![選取做為 TPE 中的事件來源父組件](../core/media/tpeselectparentassembly.gif "TPESelectParentAssembly")  
  
5.  選取的協調流程中的資料項目來源**協調流程名稱**清單方塊中，然後再按**確定**。  
  
6.  在右窗格中選取資料項目，然後拖曳到左窗格中活動的適當節點。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)   
 [建立追蹤設定檔](../core/creating-tracking-profiles.md)