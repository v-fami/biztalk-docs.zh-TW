---
title: "如何將事件來源對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 588a394fb3404872554fc786efa3fe24fdd9b47a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-event-sources"></a><span data-ttu-id="423e6-102">如何對應事件來源</span><span class="sxs-lookup"><span data-stu-id="423e6-102">How to Map Event Sources</span></span>
<span data-ttu-id="423e6-103">您可以對應事件來源，以取得 BAM 追蹤用來產生警示之資料項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="423e6-103">You map event sources to gain access to data items that BAM tracks to generate alerts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="423e6-104">您可以對應四種不同的事件來源類型的資料項目： 協調流程排程、 訊息內容、 內容屬性或傳訊屬性。</span><span class="sxs-lookup"><span data-stu-id="423e6-104">You can map data items from four different event source types: orchestration schedules, message payloads, context properties, or messaging properties.</span></span> <span data-ttu-id="423e6-105">本主題中的步驟說明如何從協調流程排程對應資料項目。</span><span class="sxs-lookup"><span data-stu-id="423e6-105">The procedure in this topic outlines mapping data items from an orchestration schedule.</span></span>  
  
### <a name="to-map-an-orchestration-schedule-as-an-event-source"></a><span data-ttu-id="423e6-106">若要對應協調流程排程做為事件來源</span><span class="sxs-lookup"><span data-stu-id="423e6-106">To map an orchestration schedule as an event source</span></span>  
  
1.  <span data-ttu-id="423e6-107">開啟現有的追蹤設定檔或建立新的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="423e6-107">Open an existing tracking profile or create a new tracking profile.</span></span> <span data-ttu-id="423e6-108">如需有關如何建立追蹤設定檔的詳細資訊，請參閱[如何建立追蹤設定檔](../core/how-to-create-a-tracking-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="423e6-108">For more information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).</span></span>  
  
2.  <span data-ttu-id="423e6-109">按一下**選取事件來源**按鈕 （位於右窗格中追蹤設定檔編輯器上方）。</span><span class="sxs-lookup"><span data-stu-id="423e6-109">Click the **Select Event Source** button (located above the right pane in the Tracking Profile Editor).</span></span>  
  
3.  <span data-ttu-id="423e6-110">選取**選取協調流程排程**從串聯功能表的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="423e6-110">Select the **Select Orchestration Schedule** menu item from the cascading menu.</span></span>  
  
4.  <span data-ttu-id="423e6-111">選取要繪製協調流程，按一下包含協調流程中的組件的父組件**組件名稱**清單方塊中，然後再按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="423e6-111">Select the parent assembly from which to draw the orchestration by clicking the assembly containing the orchestration in the **Assembly Name** list box, and then click **Next**.</span></span>  
  
     <span data-ttu-id="423e6-112">![選取做為 TPE 中的事件來源父組件](../core/media/tpeselectparentassembly.gif "TPESelectParentAssembly")</span><span class="sxs-lookup"><span data-stu-id="423e6-112">![Select Parent Assembly as event Source in the TPE](../core/media/tpeselectparentassembly.gif "TPESelectParentAssembly")</span></span>  
  
5.  <span data-ttu-id="423e6-113">選取的協調流程中的資料項目來源**協調流程名稱**清單方塊中，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="423e6-113">Select the orchestration that is the source for the data items in the **Orchestration Names** list box, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="423e6-114">在右窗格中選取資料項目，然後拖曳到左窗格中活動的適當節點。</span><span class="sxs-lookup"><span data-stu-id="423e6-114">Select the data items in the right pane and drag them to the appropriate nodes in the activity in the left pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423e6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="423e6-115">See Also</span></span>  
 <span data-ttu-id="423e6-116">[追蹤設定檔編輯器](../core/tracking-profile-editor.md) </span><span class="sxs-lookup"><span data-stu-id="423e6-116">[Tracking Profile Editor](../core/tracking-profile-editor.md) </span></span>  
 [<span data-ttu-id="423e6-117">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="423e6-117">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)