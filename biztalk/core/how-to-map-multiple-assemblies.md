---
title: 如何對應多個組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assemblies, tracking profiles
- tracking profiles, mapping assemblies
- assemblies, maps
ms.assetid: 136f1943-9643-4551-8b5b-150c4b4bfebe
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20a55b6e88889ccfa36adcac11fe548ab1b25bc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254350"
---
# <a name="how-to-map-multiple-assemblies"></a><span data-ttu-id="6b303-102">如何對應多個組件</span><span class="sxs-lookup"><span data-stu-id="6b303-102">How to Map Multiple Assemblies</span></span>
<span data-ttu-id="6b303-103">BizTalk 應用程式可能由多個組件所組成，其中存有 BAM 活動參考的資料項目。</span><span class="sxs-lookup"><span data-stu-id="6b303-103">BizTalk applications can consist of multiple assemblies in which the data items that a BAM activity references reside.</span></span> <span data-ttu-id="6b303-104">下列程序說明如何將多個組件對應到追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="6b303-104">The following procedure shows you how to map multiple assemblies to a tracking profile.</span></span>  
  
### <a name="to-map-multiple-assemblies"></a><span data-ttu-id="6b303-105">對應多個組件</span><span class="sxs-lookup"><span data-stu-id="6b303-105">To map multiple assemblies</span></span>  
  
1.  <span data-ttu-id="6b303-106">開啟現有的追蹤設定檔或建立新的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="6b303-106">Open an existing tracking profile or create a new tracking profile.</span></span> <span data-ttu-id="6b303-107">如需有關如何建立追蹤設定檔的詳細資訊，請參閱[如何建立追蹤設定檔](../core/how-to-create-a-tracking-profile.md)。</span><span class="sxs-lookup"><span data-stu-id="6b303-107">For more information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).</span></span>  
  
2.  <span data-ttu-id="6b303-108">按一下**選取事件來源**按鈕 （位於右窗格中追蹤設定檔編輯器上方）。</span><span class="sxs-lookup"><span data-stu-id="6b303-108">Click the **Select Event Source** button (located above the right pane in the Tracking Profile Editor).</span></span>  
  
3.  <span data-ttu-id="6b303-109">選取**選取協調流程排程**從串聯功能表的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="6b303-109">Select the **Select Orchestration Schedule** menu item from the cascading menu.</span></span>  
  
4.  <span data-ttu-id="6b303-110">選取要繪製協調流程，按一下包含協調流程中的組件的父組件**組件名稱**清單方塊中，然後再按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="6b303-110">Select the parent assembly from which to draw the orchestration by clicking the assembly containing the orchestration in the **Assembly Name** list box, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="6b303-111">選取的協調流程中的資料項目來源**協調流程名稱**清單方塊中，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="6b303-111">Select the orchestration that is the source for the data items in the **Orchestration Names** list box, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="6b303-112">在右窗格中選取資料項目，然後拖曳到左窗格中活動的適當節點。</span><span class="sxs-lookup"><span data-stu-id="6b303-112">Select the data items in the right pane and drag them to the appropriate nodes in the activity in the left pane.</span></span>  
  
7.  <span data-ttu-id="6b303-113">重複執行步驟 2 至 6 以對應其他組件。</span><span class="sxs-lookup"><span data-stu-id="6b303-113">Repeat steps 2 through 6 to map additional assemblies.</span></span>  
  
### <a name="to-map-the-second-assembly"></a><span data-ttu-id="6b303-114">對應第二個組件</span><span class="sxs-lookup"><span data-stu-id="6b303-114">To map the second assembly</span></span>  
  
1.  <span data-ttu-id="6b303-115">按一下**選取事件來源**。</span><span class="sxs-lookup"><span data-stu-id="6b303-115">Click the **Select Event Source**.</span></span>  
  
2.  <span data-ttu-id="6b303-116">選取**選取協調流程排程**從串聯功能表的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="6b303-116">Select the **Select Orchestration Schedule** menu item from the cascading menu.</span></span>  
  
3.  <span data-ttu-id="6b303-117">選取 [下一步要繪製協調流程，按一下包含協調流程中的組件的父組件**組件名稱**清單方塊中，然後再按**下一步**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6b303-117">Select the next parent assembly from which to draw the orchestration by clicking the assembly containing the orchestration in the **Assembly Name** list box, and then click the **Next** button.</span></span>  
  
4.  <span data-ttu-id="6b303-118">選取的協調流程中的資料項目來源**協調流程名稱**清單方塊中，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="6b303-118">Select the orchestration that is the source for the data items in the **Orchestration Names** list box, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="6b303-119">在右窗格中選取資料項目，然後拖曳到左窗格中活動的適當節點。</span><span class="sxs-lookup"><span data-stu-id="6b303-119">Select the data items in the right pane and drag them to the appropriate nodes in the activity in the left pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b303-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b303-120">See Also</span></span>  
 <span data-ttu-id="6b303-121">[如何對應事件來源](../core/how-to-map-event-sources.md) </span><span class="sxs-lookup"><span data-stu-id="6b303-121">[How to Map Event Sources](../core/how-to-map-event-sources.md) </span></span>  
 [<span data-ttu-id="6b303-122">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="6b303-122">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)