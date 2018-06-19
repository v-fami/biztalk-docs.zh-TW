---
title: 管理警示 （系統管理 檢視） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27f8bf7d-15b7-448d-8c13-e4969b90d021
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc5472e96414fe5141de27630ebe3c810d2df28c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294438"
---
# <a name="manage-alerts-administration-view"></a><span data-ttu-id="881d3-102">管理警示 （系統管理 檢視）</span><span class="sxs-lookup"><span data-stu-id="881d3-102">Manage Alerts (Administration View)</span></span>
<span data-ttu-id="881d3-103">圖 1 顯示系統管理 檢視中，系統管理員可以用來檢視所有警示和其活動的摘要清單中的 警示 頁面。</span><span class="sxs-lookup"><span data-stu-id="881d3-103">Figure 1 shows the Alerts page in administration view, which administrators can use to view a list of all alerts and a summary of their activity.</span></span> <span data-ttu-id="881d3-104">資料表會顯示每個警示的資料列。</span><span class="sxs-lookup"><span data-stu-id="881d3-104">A table displays a row for each alert.</span></span> <span data-ttu-id="881d3-105">警示名稱、 建立者的名稱、 一般統計資料 （例如數字的最後一個小時、 天、 或月份內的警示啟動），警示會顯示每個資料列的 「 訂閱者 」 的連結警示的檢視清單，以及動作資料行，內含一組 cli 計數在警示上執行動作的 ckable 圖示。</span><span class="sxs-lookup"><span data-stu-id="881d3-105">Each row shows the alert name, the name of the creator, general statistics for the alert (such as number of alert activations within the last hour, day, or month), a count of subscribers for the alerts with a link to view a list, and an Actions column containing a set of clickable icons to perform actions on the alert.</span></span>  
  
 <span data-ttu-id="881d3-106">![管理警示 頁面](../esb-toolkit/media/ch8-managealertspage.jpg "Ch8 ManageAlertsPage")</span><span class="sxs-lookup"><span data-stu-id="881d3-106">![Manage Alerts Page](../esb-toolkit/media/ch8-managealertspage.jpg "Ch8-ManageAlertsPage")</span></span>  
  
 <span data-ttu-id="881d3-107">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="881d3-107">**Figure 1**</span></span>  
  
 <span data-ttu-id="881d3-108">**ESB Management 入口網站管理通知 （管理 檢視） 頁面**</span><span class="sxs-lookup"><span data-stu-id="881d3-108">**The ESB Management Portal Manage Alerts (Administration view) page**</span></span>  
  
 <span data-ttu-id="881d3-109">下列清單說明如何使用 [ESB Management 入口網站管理警示] 頁面的功能：</span><span class="sxs-lookup"><span data-stu-id="881d3-109">The following list explains how you can use the features of the ESB Management Portal Manage Alerts page:</span></span>  
  
-   <span data-ttu-id="881d3-110">按一下**建立警示**頂端的 [建立新的警示] 頁面的連結。</span><span class="sxs-lookup"><span data-stu-id="881d3-110">Click the **Create Alert** link at the top of the page to create a new alert.</span></span>  
  
-   <span data-ttu-id="881d3-111">按一下**匯出至 Excel**警示的清單匯出為 Microsoft Excel 試算表的連結。</span><span class="sxs-lookup"><span data-stu-id="881d3-111">Click the **Export To Excel** link to export the list of alerts as a Microsoft Excel spreadsheet.</span></span>  
  
-   <span data-ttu-id="881d3-112">按一下 +**檢視 「 訂閱者 」** 顯示一份 「 訂閱者 」 警示的資料列中的連結。</span><span class="sxs-lookup"><span data-stu-id="881d3-112">Click the + **View Subscribers** link in a row to show a list of subscribers for the alert.</span></span> <span data-ttu-id="881d3-113">清單中資料列，就會展開並刪除圖示出現在每個可讓系統管理員從警示移除訂閱者的動作資料行。</span><span class="sxs-lookup"><span data-stu-id="881d3-113">The list expands within the row, and a delete icon appears in the Actions column for each one that allows administrators to remove a subscriber from the alert.</span></span> <span data-ttu-id="881d3-114">同時，此連結會變更-**隱藏的訂閱者**，讓您可以摺疊的訂閱者清單。</span><span class="sxs-lookup"><span data-stu-id="881d3-114">At the same time, the link changes to - **Hide Subscribers**, allowing you to collapse the list of subscribers.</span></span>  
  
-   <span data-ttu-id="881d3-115">按一下 執行工作，該資料列中警示的 動作 欄中的圖示。</span><span class="sxs-lookup"><span data-stu-id="881d3-115">Click an icon in the Actions column to perform a task for the alerts in that row.</span></span> <span data-ttu-id="881d3-116">（中出現的順序） 的圖示和工作如下所示：</span><span class="sxs-lookup"><span data-stu-id="881d3-116">The icons (in the order they appear) and the tasks are the following:</span></span>  
  
    -   <span data-ttu-id="881d3-117">**檢視警示詳細資料。**</span><span class="sxs-lookup"><span data-stu-id="881d3-117">**View alert details.**</span></span> <span data-ttu-id="881d3-118">此圖示會顯示所選警示的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="881d3-118">This icon displays details of the selected alert.</span></span>  
  
    -   <span data-ttu-id="881d3-119">**檢視歷程記錄**。</span><span class="sxs-lookup"><span data-stu-id="881d3-119">**View history**.</span></span> <span data-ttu-id="881d3-120">此圖示會顯示包含所選取警示的所有啟用的資料表。</span><span class="sxs-lookup"><span data-stu-id="881d3-120">This icon displays a table containing all the activations for the selected alert.</span></span>  
  
    -   <span data-ttu-id="881d3-121">**加入訂閱者**。</span><span class="sxs-lookup"><span data-stu-id="881d3-121">**Add subscriber**.</span></span> <span data-ttu-id="881d3-122">此圖示可讓系統管理員將訂閱者加入至選取的警示。</span><span class="sxs-lookup"><span data-stu-id="881d3-122">This icon allows administrators to add a subscriber to the selected alert.</span></span>  
  
    -   <span data-ttu-id="881d3-123">**編輯警示**。</span><span class="sxs-lookup"><span data-stu-id="881d3-123">**Edit alert**.</span></span> <span data-ttu-id="881d3-124">此連結可讓系統管理員可以編輯警示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="881d3-124">This link allows administrators to edit the alert details.</span></span>  
  
    -   <span data-ttu-id="881d3-125">**刪除警示**。</span><span class="sxs-lookup"><span data-stu-id="881d3-125">**Delete alert**.</span></span> <span data-ttu-id="881d3-126">此連結會刪除警示 」 和所有相關聯的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="881d3-126">This link deletes the alert and all associated subscriptions.</span></span>