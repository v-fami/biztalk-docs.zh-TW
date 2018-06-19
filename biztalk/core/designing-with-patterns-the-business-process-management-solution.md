---
title: 使用模式進行設計： 商務程序管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- patterns [process management solutions], examples
- patterns [process management solutions], designing
- examples, programming patterns
- designing, programming patterns
ms.assetid: 0583f4a4-01db-4d5b-a1f5-1694c1ddbd30
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91da8c63fc46ee90696e257bfd6142b5088af305
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239662"
---
# <a name="designing-with-patterns-the-business-process-management-solution"></a><span data-ttu-id="0c855-102">使用模式進行設計： 商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="0c855-102">Designing with Patterns: the Business Process Management Solution</span></span>
<span data-ttu-id="0c855-103">商務程序管理解決方案顯示在 BizTalk 應用程式中建構程序管理員的方式。</span><span class="sxs-lookup"><span data-stu-id="0c855-103">The business process management solution shows one way to construct a process manager in a BizTalk application.</span></span> <span data-ttu-id="0c855-104">解決方案使用元件以選取和控制訂單處理階段的順序。</span><span class="sxs-lookup"><span data-stu-id="0c855-104">The solution uses a component to select and control the sequence of stages in order processing.</span></span> <span data-ttu-id="0c855-105">解決方案會在傳遞訂單以進行處理之前，接收訂單 (可能用於新的服務、變更或取消服務)、加以記錄和認可訂單。</span><span class="sxs-lookup"><span data-stu-id="0c855-105">The solution takes an order—which may be for new service, a change, or cancellation of service—logs it, and acknowledges the order before passing it on for processing.</span></span> <span data-ttu-id="0c855-106">處理包含一或多個處理訂單的階段。</span><span class="sxs-lookup"><span data-stu-id="0c855-106">The processing consists of one or more stages that handle the order.</span></span> <span data-ttu-id="0c855-107">最後，解決方案會將最終回應傳回至原始訂單要求。</span><span class="sxs-lookup"><span data-stu-id="0c855-107">Finally, the solution returns a final response to the original order request.</span></span>  
  
 <span data-ttu-id="0c855-108">設計良好的程序管理解決方案可讓您從程序新增或刪減階段，無須重新建構應用程式的其他部分。</span><span class="sxs-lookup"><span data-stu-id="0c855-108">A well-designed process management solution enables you to add or subtract stages from the process without having to reconstruct the rest of the application.</span></span> <span data-ttu-id="0c855-109">此解決方案中採取的方法就可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="0c855-109">The approach taken in this solution allows for exactly that.</span></span> <span data-ttu-id="0c855-110">訂單程序分成不連續的獨立階段。</span><span class="sxs-lookup"><span data-stu-id="0c855-110">The order process is broken into discrete, independent stages.</span></span> <span data-ttu-id="0c855-111">所有階段都是從相同的連接埠讀取，並使用篩選條件來判斷要處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="0c855-111">All stages read from the same port and use a filter to determine which messages are theirs to process.</span></span> <span data-ttu-id="0c855-112">這會在下一節＜模式＞中詳細說明。</span><span class="sxs-lookup"><span data-stu-id="0c855-112">This is explained further in the following section, "Patterns."</span></span>  
  
 <span data-ttu-id="0c855-113">此解決方案也接受透過 Web 服務輸入，雖然您也可以透過 FTP 連線以此解決方案使用非服務介面。</span><span class="sxs-lookup"><span data-stu-id="0c855-113">This solution also accepts input through a Web service, although you can also use a non-service interface with this solution through an FTP connection.</span></span> <span data-ttu-id="0c855-114">此功能模擬在批次系統中使用應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="0c855-114">This facility simulates how the application might be used in a batch system.</span></span>  
  
## <a name="patterns"></a><span data-ttu-id="0c855-115">模式</span><span class="sxs-lookup"><span data-stu-id="0c855-115">Patterns</span></span>  
 <span data-ttu-id="0c855-116">下圖顯示前面小節中所描述的商務程序管理解決方案中的模式簡化版本。</span><span class="sxs-lookup"><span data-stu-id="0c855-116">The following diagram shows a simplified version of the patterns in the business process management solution as described in the preceding section.</span></span>  
  
 <span data-ttu-id="0c855-117">![商務程序管理解決方案模式](../core/media/bts-cp-business-process-management-patterns.gif "bts_cp_Business_Process_Management_Patterns")</span><span class="sxs-lookup"><span data-stu-id="0c855-117">![Business Process Management Solution Patterns](../core/media/bts-cp-business-process-management-patterns.gif "bts_cp_Business_Process_Management_Patterns")</span></span>  
  
 <span data-ttu-id="0c855-118">解決方案包含下列部分： 服務介面、 FTP 通道、 各種轉譯程式、 處理序管理員，以及兩個處理階段。</span><span class="sxs-lookup"><span data-stu-id="0c855-118">The solution consists of the following parts: the service interface, the FTP channel, various translators, the process manager, and the two processing stages.</span></span> <span data-ttu-id="0c855-119">前置處理區段中的四個轉譯器會建立回到服務介面的通知訊息、在歷史或追蹤資料庫中產生項目，以及在服務系統中製作項目。</span><span class="sxs-lookup"><span data-stu-id="0c855-119">The four translators in the preprocessing section create an acknowledgement message that goes back to the service interface, generate an entry in a history or tracking database, and make an entry in the service system.</span></span> <span data-ttu-id="0c855-120">第四個轉譯器會建立程序管理員所需的訊息。</span><span class="sxs-lookup"><span data-stu-id="0c855-120">The fourth translator creates the message needed by the process manager.</span></span> <span data-ttu-id="0c855-121">接著，程序管理員控制處理階段。</span><span class="sxs-lookup"><span data-stu-id="0c855-121">The process manager in turn controls the processing stages.</span></span>  
  
 <span data-ttu-id="0c855-122">在許多程序管理員實作中，管理員會追蹤處理狀態。</span><span class="sxs-lookup"><span data-stu-id="0c855-122">In many process manager implementations, the manager tracks the processing state.</span></span> <span data-ttu-id="0c855-123">如圖所示，此實作會加以修改。</span><span class="sxs-lookup"><span data-stu-id="0c855-123">This implementation, as the diagram shows, modifies this.</span></span> <span data-ttu-id="0c855-124">在此解決方案中，程序管理員在訊息中設定旗標，以指示下一個處理訊息的處理階段。</span><span class="sxs-lookup"><span data-stu-id="0c855-124">In this solution, the process manager sets a flag in the message to indicate the processing stage that should next handle the message.</span></span> <span data-ttu-id="0c855-125">然後各個階段使用篩選條件來決定是否要處理特定訊息。</span><span class="sxs-lookup"><span data-stu-id="0c855-125">Each stage then uses a filter to determine whether it should handle a particular message.</span></span>  
  
 <span data-ttu-id="0c855-126">使用此方法，程序管理員不需維護任何路由資訊。</span><span class="sxs-lookup"><span data-stu-id="0c855-126">Using this approach, the process manager does not have to maintain any routing information.</span></span> <span data-ttu-id="0c855-127">在管理員和各階段之間的所有訊息都使用相同的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0c855-127">All messages between the manager and the various stages use the same ports.</span></span> <span data-ttu-id="0c855-128">若要新增階段，只需要在適當的連接埠上新增傳送和接收的元件，以及正確階段編號的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="0c855-128">To add a stage, you only have to add a component that sends and receives on the proper ports and filters for the correct stage number.</span></span> <span data-ttu-id="0c855-129">您不需要變更程序管理員本身。</span><span class="sxs-lookup"><span data-stu-id="0c855-129">You don't need to change anything in the process manager itself.</span></span>  
  
 <span data-ttu-id="0c855-130">請注意，還有很多內容不在圖形內。</span><span class="sxs-lookup"><span data-stu-id="0c855-130">Note that a lot is left out of the diagram.</span></span> <span data-ttu-id="0c855-131">處理階段可能 (事實上確實會) 和後端程序通訊。</span><span class="sxs-lookup"><span data-stu-id="0c855-131">The processing stages may—and, in fact, do—communicate with backend processes.</span></span> <span data-ttu-id="0c855-132">解決方案也會在程序中的多處收集歷史資訊。</span><span class="sxs-lookup"><span data-stu-id="0c855-132">The solution could also collect historical information at more than one point in the process.</span></span> <span data-ttu-id="0c855-133">或許，最值得注意的是未指定程序管理員的邏輯。</span><span class="sxs-lookup"><span data-stu-id="0c855-133">Perhaps, most significantly, the logic of the process manager isn't specified.</span></span> <span data-ttu-id="0c855-134">此外，未指定使用同步或非同步連線。</span><span class="sxs-lookup"><span data-stu-id="0c855-134">In addition, the use of synchronous or asynchronous connections is not specified.</span></span> <span data-ttu-id="0c855-135">這些會在下列各節中考量。</span><span class="sxs-lookup"><span data-stu-id="0c855-135">These will be considered in following sections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c855-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c855-136">See Also</span></span>  
 <span data-ttu-id="0c855-137">[商務程序管理解決方案中的模式](../core/patterns-in-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="0c855-137">[Patterns in the Business Process Management Solution](../core/patterns-in-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="0c855-138">轉譯商務程序管理解決方案的模式</span><span class="sxs-lookup"><span data-stu-id="0c855-138">Translating the Patterns of the Business Process Management Solution</span></span>](../core/translating-the-patterns-of-the-business-process-management-solution.md)