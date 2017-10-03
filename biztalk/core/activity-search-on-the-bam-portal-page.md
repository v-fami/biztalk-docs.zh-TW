---
title: "BAM 入口網站上的活動搜尋頁面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], searching
- Activity Search page [BAM portal]
- BAM portal, activity searches
ms.assetid: 24a5111c-026f-4f77-8a17-65955aafd24c
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 670d73cb33d9e3cc3aa1a9162cf929382a4dd58a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="activity-search-on-the-bam-portal-page"></a><span data-ttu-id="49571-102">BAM 入口網站頁面上的活動搜尋</span><span class="sxs-lookup"><span data-stu-id="49571-102">Activity Search on the BAM Portal Page</span></span>
<span data-ttu-id="49571-103">商務使用者、開發人員和商務分析師可以使用 BAM 入口網站頁面，視需要針對 BAM 資料執行搜尋以尋找特定程序的特定案例。</span><span class="sxs-lookup"><span data-stu-id="49571-103">Business end users, developers, and business analysts can use the BAM portal page when they need to perform searches against BAM data to find specific cases of a particular process.</span></span> <span data-ttu-id="49571-104">這些程序定義為 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="49571-104">These processes are defined as BAM activities.</span></span> <span data-ttu-id="49571-105">BAM 活動代表商務中的工作單位，例如訂單或貸款申請。</span><span class="sxs-lookup"><span data-stu-id="49571-105">A BAM activity represents a unit of work in a business, such as a purchase order or loan application.</span></span>  
  
## <a name="how-an-activity-search-works"></a><span data-ttu-id="49571-106">活動搜尋如何運作</span><span class="sxs-lookup"><span data-stu-id="49571-106">How an activity search works</span></span>  
 <span data-ttu-id="49571-107">活動搜尋讓您能夠依據 BAM 檢視所提供的追蹤值和項目指定搜尋準則，針對 BAM 資料執行搜尋以尋找符合條件的活動，並顯示活動讓您進行編輯或依據活動建立警示。</span><span class="sxs-lookup"><span data-stu-id="49571-107">An activity search allows you to perform searches against BAM data to find activities that match criteria you specify based on tracked values and items available in a BAM view, and to display the activities so that you can edit them or create alerts based on them.</span></span>  
  
 <span data-ttu-id="49571-108">您可以儲存和重複使用為了搜尋所建立的查詢。</span><span class="sxs-lookup"><span data-stu-id="49571-108">Queries that you create for your searches can be saved and reused.</span></span> <span data-ttu-id="49571-109">您也可以使用查詢做為警示的基礎，例如，「收到特定客戶的訂單時通知我」。</span><span class="sxs-lookup"><span data-stu-id="49571-109">You can also use them as the basis for an alert, for example, "Notify me any time a purchase order arrives from the specified customer."</span></span> <span data-ttu-id="49571-110">請使用內容頁面上方的按鈕來儲存、開啟和執行查詢，以及設定警示。</span><span class="sxs-lookup"><span data-stu-id="49571-110">You use the buttons at the top of the content page to save, open, and run queries, as well as to set alerts.</span></span>  
  
 <span data-ttu-id="49571-111">活動搜尋可以讓您找到所要監控的活動。</span><span class="sxs-lookup"><span data-stu-id="49571-111">Activity searches allow you to locate the activities that you want to monitor.</span></span> <span data-ttu-id="49571-112">一旦建立了活動搜尋，您即可使用該搜尋來建立警示以通知您感興趣的事件。</span><span class="sxs-lookup"><span data-stu-id="49571-112">Once you create an activity search, you can use that search to create an alert that will notify you of events that are of interest.</span></span>  
  
## <a name="the-activity-search-page"></a><span data-ttu-id="49571-113">活動搜尋頁面</span><span class="sxs-lookup"><span data-stu-id="49571-113">The Activity Search page</span></span>  
 <span data-ttu-id="49571-114">[活動搜尋] 頁面在 [內容] 框架中分成三個主要區段：</span><span class="sxs-lookup"><span data-stu-id="49571-114">The Activity Search page is divided into three main sections inside the Content frame:</span></span>  
  
-   <span data-ttu-id="49571-115">**查詢**： 這個區段可讓使用者以搜尋活動建立搜尋子句，根據特定的追蹤的資料的項目。</span><span class="sxs-lookup"><span data-stu-id="49571-115">**Query**: This section allows users to search for activities by building search clauses based on specific tracked data items.</span></span> <span data-ttu-id="49571-116">使用者可視需要新增和移除子句。</span><span class="sxs-lookup"><span data-stu-id="49571-116">The user can add and remove clauses as required.</span></span>  
  
-   <span data-ttu-id="49571-117">**資料行選擇器**： 這個區段可讓使用者指定的資料，從那些哪些項目可用在該檢視中，以傳回有任何記錄符合搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="49571-117">**Column Chooser**: This section allows users to specify which items of data, from those available in that view, to return if any records match the search criteria.</span></span>  
  
-   <span data-ttu-id="49571-118">**結果**： 此區段顯示查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="49571-118">**Results**: Results of the query display in this section.</span></span>  
  
 <span data-ttu-id="49571-119">如需活動搜尋和 [活動搜尋] 頁面的詳細資訊，請參閱[BAM 入口網站中的活動搜尋](../core/activity-searches-in-the-bam-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="49571-119">For more information about activity searches and the Activity Search page, see [Activity Searches in the BAM Portal](../core/activity-searches-in-the-bam-portal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49571-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49571-120">See Also</span></span>  
 <span data-ttu-id="49571-121">[BAM 入口網站](../core/bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="49571-121">[BAM Portal](../core/bam-portal.md) </span></span>  
 <span data-ttu-id="49571-122">[使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md) </span><span class="sxs-lookup"><span data-stu-id="49571-122">[Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md) </span></span>  
 [<span data-ttu-id="49571-123">BAM 入口網站上的警示管理員頁面</span><span class="sxs-lookup"><span data-stu-id="49571-123">Alert Manager on the BAM Portal Page</span></span>](../core/alert-manager-on-the-bam-portal-page.md)