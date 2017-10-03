---
title: "健全狀況與活動追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c5d7415-38da-47b5-8dbc-0a2ea74548d9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b1720535b58a50fe0c5bd3478bc9b9ec90d0d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="health-and-activity-tracking"></a><span data-ttu-id="4c366-102">狀況與活動追蹤</span><span class="sxs-lookup"><span data-stu-id="4c366-102">Health and Activity Tracking</span></span>
<span data-ttu-id="4c366-103">**健全狀況與活動追蹤 (HAT)**工具已移除[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]2009年。</span><span class="sxs-lookup"><span data-stu-id="4c366-103">The **Health and Activity Tracking (HAT)** tool was removed in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009.</span></span>  <span data-ttu-id="4c366-104">HAT 工具的角色是追蹤和顯示即時的相關資訊和歷史訊息資料儲存在 「 BizTalk 追蹤資料庫中。</span><span class="sxs-lookup"><span data-stu-id="4c366-104">The role of the HAT tool was to track and display information relating to live and historical message data stored in the BizTalk Tracking database.</span></span>  <span data-ttu-id="4c366-105">此工具可讓您針對協調流程的流程進行偵錯，也可以讓您透過循序畫面來檢視訊息的流程。</span><span class="sxs-lookup"><span data-stu-id="4c366-105">The tool allowed debugging of the flow of an orchestration and the ability to view the flow of a message through a sequential display.</span></span>  <span data-ttu-id="4c366-106">[查詢建立器] 允許對追蹤資料執行標準和自訂的查詢。</span><span class="sxs-lookup"><span data-stu-id="4c366-106">A Query Builder allowed standard and custom queries of the tracking data.</span></span>  
  
 <span data-ttu-id="4c366-107">雖然無法再從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 功能表直接叫用 [狀況與活動追蹤] 工具，但其追蹤功能仍然間接存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境內。</span><span class="sxs-lookup"><span data-stu-id="4c366-107">While the Health Activity Tracking tool is no longer invoked directly from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] menu, its tracking functionality still indirectly exists from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  <span data-ttu-id="4c366-108">健全狀況與活動資訊也可透過改良式整合其他追蹤 BizTalk Server 管理主控台中的 [群組中樞] 頁面中的查詢。</span><span class="sxs-lookup"><span data-stu-id="4c366-108">Health and activity information is available through improved integration and additional tracking queries within the Group Hub page in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="4c366-109">大部分的周圍的文件追蹤狀況與活動資料，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4c366-109">A majority of documentation surrounding tracking health and activity data can be found at [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  <span data-ttu-id="4c366-110">本章節內容資訊的某些部分包含[訊息和執行個體資料追蹤的最佳作法](../core/best-practices-for-message-and-instance-data-tracking.md)，[瞭解追蹤資料](../core/understanding-tracked-data.md)，[檢視歷程記錄和追蹤資料](../core/viewing-historical-and-tracked-data.md)，[檢視訊息流程](../core/viewing-message-flow.md)，和[偵錯協調流程](../core/debugging-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="4c366-110">Some of the information in this section includes [Best Practices for Message and Instance Data Tracking](../core/best-practices-for-message-and-instance-data-tracking.md), [Understanding Tracked Data](../core/understanding-tracked-data.md), [Viewing Historical and Tracked Data](../core/viewing-historical-and-tracked-data.md), [Viewing Message Flow](../core/viewing-message-flow.md), and [Debugging an Orchestration](../core/debugging-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="4c366-111">如需有關的改進與此頁面的其他查詢的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="4c366-111">For additional information on the improvements and the additional queries to this page, refer to the following topics:</span></span>  
  
-   <span data-ttu-id="4c366-112">[使用 [群組中樞] 頁面](../core/using-the-group-hub-page.md)</span><span class="sxs-lookup"><span data-stu-id="4c366-112">[Using the Group Hub Page](../core/using-the-group-hub-page.md)</span></span>  
  
-   [<span data-ttu-id="4c366-113">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="4c366-113">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)  
  
-   [<span data-ttu-id="4c366-114">如何搜尋追蹤的訊息事件</span><span class="sxs-lookup"><span data-stu-id="4c366-114">How to Search for Tracked Message Events</span></span>](../core/how-to-search-for-tracked-message-events.md)  
  
-   [<span data-ttu-id="4c366-115">如何搜尋受到追蹤的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="4c366-115">How to Search for Tracked Service Instances</span></span>](../core/how-to-search-for-tracked-service-instances.md)