---
title: 協調流程偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging, Orchestration Debugger
- debugging, orchestrations
- Orchestration Debugger, about Orchestration Debugger
- Orchestrations Debugger
- orchestrations, debugging
- debugging, HAT
- HAT, debugging
ms.assetid: aae99cfd-d3dd-41c8-ae7a-b2733352cd69
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c231513ad75520fcadd88e5dd7d88104ddeeced5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238582"
---
# <a name="debugging-an-orchestration"></a><span data-ttu-id="4861f-102">偵錯協調流程</span><span class="sxs-lookup"><span data-stu-id="4861f-102">Debugging an Orchestration</span></span>
<span data-ttu-id="4861f-103">「協調流程偵錯工具」能讓您依圖形逐步追蹤單一協調流程執行個體的活動。</span><span class="sxs-lookup"><span data-stu-id="4861f-103">The Orchestration Debugger enables you to track the activity of a single orchestration instance on a shape-by-shape basis.</span></span> <span data-ttu-id="4861f-104">它會顯示「協調流程偵錯工具」中建立之轉換的協調流程檢視。</span><span class="sxs-lookup"><span data-stu-id="4861f-104">It displays a rendered view of the orchestration created in the Orchestration Designer.</span></span>  
  
 <span data-ttu-id="4861f-105">您存取在 BizTalk Server 管理主控台的 [群組概觀] 頁面中的協調流程偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="4861f-105">You access the Orchestration Debugger in the Group Overview Page in the BizTalk Server Administration Console.</span></span>  <span data-ttu-id="4861f-106">這是透過快顯功能表的追蹤查詢輸出中以滑鼠右鍵按一下任何服務或與協調流程類型的執行個體相關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="4861f-106">This is done from the output of a tracking query through a shortcut menu by right-clicking any service or message instance associated with an orchestration type.</span></span> <span data-ttu-id="4861f-107">一旦您在我此頁面上，您可以來回切換協調流程偵錯工具和訊息流程 檢視之間。</span><span class="sxs-lookup"><span data-stu-id="4861f-107">Once you're in i this page, you can switch back and forth between the Orchestration Debugger and the Message Flow view.</span></span>  
  
 <span data-ttu-id="4861f-108">「協調流程偵錯工具」提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="4861f-108">The Orchestration Debugger provides the following functionality:</span></span>  
  
-   <span data-ttu-id="4861f-109">顯示轉換的協調流程檢視，您可以在其中重新執行該特定協調流程的每一個處理步驟。</span><span class="sxs-lookup"><span data-stu-id="4861f-109">Displays a rendered view of the orchestration in which you can replay each processing step for that particular orchestration.</span></span>  
  
-   <span data-ttu-id="4861f-110">可讓您在任何協調流程圖形之前設定中斷點並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4861f-110">Enables you to set breakpoints before any orchestration shape and continue execution.</span></span>  
  
-   <span data-ttu-id="4861f-111">可讓您查看特定變數與訊息資料。</span><span class="sxs-lookup"><span data-stu-id="4861f-111">Enables you to look at specific variables and message data.</span></span>  
  
-   <span data-ttu-id="4861f-112">當執行個體在「協調流程偵錯工具」中開啟時，自動啟用特定協調流程執行個體的所有追蹤選項。</span><span class="sxs-lookup"><span data-stu-id="4861f-112">Automatically enables all of the tracking options for a particular orchestration instance when that instance opens in the Orchestration Debugger.</span></span>  
  
-   <span data-ttu-id="4861f-113">它提供您繼續、在偵錯下繼續，以及終止特定協調流程執行個體的能力。</span><span class="sxs-lookup"><span data-stu-id="4861f-113">It gives you the ability to continue, resume in debug, and terminate the particular orchestration instance.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4861f-114">當您解除部署組件時，資料庫會保留該解除部署組件的追蹤選項與中斷點資訊。</span><span class="sxs-lookup"><span data-stu-id="4861f-114">When you undeploy an assembly, the database maintains the tracking options and breakpoint information for the undeployed assembly.</span></span> <span data-ttu-id="4861f-115">若您之後部署相同的組件，就會還原該組件的選項與中斷點資訊。</span><span class="sxs-lookup"><span data-stu-id="4861f-115">If you subsequently deploy the same assembly, the options and breakpoint information for that assembly are restored.</span></span>  
  
 <span data-ttu-id="4861f-116">使用「協調流程偵錯工具」有兩種模式：</span><span class="sxs-lookup"><span data-stu-id="4861f-116">The two modes for using the Orchestration Debugger are:</span></span>  
  
-   [<span data-ttu-id="4861f-117">協調流程偵錯工具中的報告模式</span><span class="sxs-lookup"><span data-stu-id="4861f-117">Reporting Mode in Orchestration Debugger</span></span>](../core/reporting-mode-in-orchestration-debugger.md)  
  
-   [<span data-ttu-id="4861f-118">協調流程偵錯工具中的互動模式</span><span class="sxs-lookup"><span data-stu-id="4861f-118">Interactive Mode in Orchestration Debugger</span></span>](../core/interactive-mode-in-orchestration-debugger.md)  
  
 <span data-ttu-id="4861f-119">根據服務的狀態而有不同的能力。</span><span class="sxs-lookup"><span data-stu-id="4861f-119">The capabilities differ depending on the state of the service.</span></span> <span data-ttu-id="4861f-120">您可以從任何檢視叫用目前於「在中斷點」狀態的任何服務執行個體，以執行互動式偵錯。</span><span class="sxs-lookup"><span data-stu-id="4861f-120">You can perform interactive debugging by invoking any service instance currently in the In Breakpoint state, from any view.</span></span> <span data-ttu-id="4861f-121">如需偵錯協調流程的資訊，請參閱[如何叫用協調流程偵錯工具和訊息流程檢視](../core/how-to-invoke-the-orchestration-debugger-and-the-message-flow-views.md)。</span><span class="sxs-lookup"><span data-stu-id="4861f-121">For information about debugging an orchestration, see [How to Invoke the Orchestration Debugger and the Message Flow Views](../core/how-to-invoke-the-orchestration-debugger-and-the-message-flow-views.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4861f-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="4861f-122">In This Section</span></span>  
  
-   [<span data-ttu-id="4861f-123">協調流程偵錯工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="4861f-123">Orchestration Debugger User Interface</span></span>](../core/orchestration-debugger-user-interface.md)  
  
-   [<span data-ttu-id="4861f-124">使用協調流程偵錯工具時的考量</span><span class="sxs-lookup"><span data-stu-id="4861f-124">Considerations when Using Orchestration Debugger</span></span>](../core/considerations-when-using-orchestration-debugger.md)  
  
-   [<span data-ttu-id="4861f-125">使用協調流程偵錯工具檢視</span><span class="sxs-lookup"><span data-stu-id="4861f-125">Working with the Orchestration Debugger View</span></span>](../core/working-with-the-orchestration-debugger-view.md)