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
# <a name="business-event-nodes"></a><span data-ttu-id="09ee3-102">商務事件節點</span><span class="sxs-lookup"><span data-stu-id="09ee3-102">Business Event Nodes</span></span>
<span data-ttu-id="09ee3-103">「商務事件」或里程碑節點定義特定日期或時間的事件。</span><span class="sxs-lookup"><span data-stu-id="09ee3-103">Business Event or milestone nodes define events that are date- or time-specific.</span></span> <span data-ttu-id="09ee3-104">預先定義的商務事件和里程碑資料夾存在於您從商務使用者匯入的活動定義中，若不重新匯入活動定義檔案則無法刪除。</span><span class="sxs-lookup"><span data-stu-id="09ee3-104">Pre-defined business event and milestone folders exist in the activity definition you import from the business end user, and you cannot delete them without reimporting the activity definition file.</span></span>  
  
## <a name="working-with-business-event-nodes"></a><span data-ttu-id="09ee3-105">使用商務事件節點</span><span class="sxs-lookup"><span data-stu-id="09ee3-105">Working with business event nodes</span></span>  
 <span data-ttu-id="09ee3-106">您可以從協調流程拖曳圖形到「商務事件」資料夾，以便在圖形執行完成時追蹤那些事件。</span><span class="sxs-lookup"><span data-stu-id="09ee3-106">You can drag shapes from the orchestration into the Business Events folder to track those events as the execution of the shapes is completed.</span></span>  
  
 <span data-ttu-id="09ee3-107">TPE 使用圖形名稱做為事件資料夾名稱，並且此資料夾將有唯一的圖示。</span><span class="sxs-lookup"><span data-stu-id="09ee3-107">TPE uses the name of the shape for the name of the event folder, and this folder will have a unique icon.</span></span> <span data-ttu-id="09ee3-108">例如，在範例貸款程序實例中，TPE 根據事件來命名，例如「已核准」或「已拒絕」。</span><span class="sxs-lookup"><span data-stu-id="09ee3-108">For example, in the sample loan-process scenario, TPE names them according to the event, such as Approved or Denied.</span></span> <span data-ttu-id="09ee3-109">當商務程序跨越多個追蹤設定檔時，您應該只在每個商務程序中追蹤一次商務事件。</span><span class="sxs-lookup"><span data-stu-id="09ee3-109">You should only track business events once per business process when that business process spans multiple tracking profiles.</span></span> <span data-ttu-id="09ee3-110">如果協調流程中含有條件路徑，您可以同時選取兩個路徑中的商務事件，因為將只有一個會執行。</span><span class="sxs-lookup"><span data-stu-id="09ee3-110">If you have a conditional path in your orchestration, you can select the business event from both paths, as only one will ever execute.</span></span> <span data-ttu-id="09ee3-111">您不可以選取迴圈內的圖形。</span><span class="sxs-lookup"><span data-stu-id="09ee3-111">You should not select a shape inside a loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09ee3-112">雖然不重新匯入活動定義就無法刪除資料夾，但您還是可以刪除圖形 (事件)。</span><span class="sxs-lookup"><span data-stu-id="09ee3-112">While you cannot delete folders without reimporting the activity definition, you can delete shapes (events).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ee3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09ee3-113">See Also</span></span>  
 [<span data-ttu-id="09ee3-114">TPE 活動檢視節點</span><span class="sxs-lookup"><span data-stu-id="09ee3-114">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)