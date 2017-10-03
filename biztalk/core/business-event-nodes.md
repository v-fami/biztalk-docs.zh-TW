---
title: "商務事件節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events, Tracking Profile Editor
- events, date specific
- events, time specific
- Tracking Profile Editor, node descriptions
- Business Event nodes [Tracking Profile Editor]
- Tracking Profile Editor, events
ms.assetid: 177bc3c4-e762-42fe-80bc-edede5cd4fcd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44c3d06e553f129abb36eb53c4dde9c5ab9c25f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="business-event-nodes"></a>商務事件節點
「商務事件」或里程碑節點定義特定日期或時間的事件。 預先定義的商務事件和里程碑資料夾存在於您從商務使用者匯入的活動定義中，若不重新匯入活動定義檔案則無法刪除。  
  
## <a name="working-with-business-event-nodes"></a>使用商務事件節點  
 您可以從協調流程拖曳圖形到「商務事件」資料夾，以便在圖形執行完成時追蹤那些事件。  
  
 TPE 使用圖形名稱做為事件資料夾名稱，並且此資料夾將有唯一的圖示。 例如，在範例貸款程序實例中，TPE 根據事件來命名，例如「已核准」或「已拒絕」。 當商務程序跨越多個追蹤設定檔時，您應該只在每個商務程序中追蹤一次商務事件。 如果協調流程中含有條件路徑，您可以同時選取兩個路徑中的商務事件，因為將只有一個會執行。 您不可以選取迴圈內的圖形。  
  
> [!NOTE]
>  雖然不重新匯入活動定義就無法刪除資料夾，但您還是可以刪除圖形 (事件)。  
  
## <a name="see-also"></a>另請參閱  
 [TPE 活動檢視節點](../core/tpe-activity-view-nodes.md)