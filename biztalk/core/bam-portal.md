---
title: BAM 入口網站 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM portal, alerts
- activities [BAM], searching
- BAM portal
- BAM portal, features
- aggregations [BAM], BAM portal
- BAM portal, activity searches
- alerts, Alert Manager
- BAM portal, about BAM portal
- BAM, portals
- BAM portal, aggregations
ms.assetid: 593c9637-6b97-4ad8-8af7-2b49325acf10
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f86aad2a183653f00f1f7fc2533ac6956b2a85f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232078"
---
# <a name="bam-portal"></a><span data-ttu-id="dadc4-102">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="dadc4-102">BAM Portal</span></span>
<span data-ttu-id="dadc4-103">商務使用者使用 BAM 入口網站來監控「關鍵效能指標」(KPI)，此 KPI 會測量達到商務目標的進度，以及有關商務程序的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="dadc4-103">Business end users use the BAM portal to monitor Key Performance Indicators (KPIs), which measure progress toward a business goal, as well as other information about their business process.</span></span> <span data-ttu-id="dadc4-104">商務分析師使用 BAM 入口網站來監督觀察模型的建立，觀察模型是商務程序中可見性需求的高階定義。</span><span class="sxs-lookup"><span data-stu-id="dadc4-104">Business analysts use the BAM portal to oversee the creation of observation models, which are high-level definitions of the visibility requirements within the business process.</span></span> <span data-ttu-id="dadc4-105">系統管理員會在各種不同的監控活動中使用觀察模型，其中包括監控商務程序管理系統的狀況。</span><span class="sxs-lookup"><span data-stu-id="dadc4-105">Administrators use it for a variety of monitoring activities, including monitoring the health of the business process management system.</span></span>  
  
## <a name="what-is-the-bam-portal"></a><span data-ttu-id="dadc4-106">何謂 BAM 入口網站？</span><span class="sxs-lookup"><span data-stu-id="dadc4-106">What is the BAM portal?</span></span>  
 <span data-ttu-id="dadc4-107">BAM 入口網站提供商務程序即時、端對端的可見性，</span><span class="sxs-lookup"><span data-stu-id="dadc4-107">The BAM portal provides real-time, end-to-end visibility into a business process.</span></span> <span data-ttu-id="dadc4-108">它是 Web 架構的功能，其中包含 ASP.NET 網頁的集合。</span><span class="sxs-lookup"><span data-stu-id="dadc4-108">It is a Web-based feature that consists of a collection of ASP.NET pages.</span></span> <span data-ttu-id="dadc4-109">您可以自訂 BAM 來增強效能及使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="dadc4-109">You can customize BAM to enhance the performance and experience for your users.</span></span>  
  
## <a name="why-use-the-bam-portal"></a><span data-ttu-id="dadc4-110">為什麼要使用 BAM 入口網站？</span><span class="sxs-lookup"><span data-stu-id="dadc4-110">Why use the BAM portal?</span></span>  
 <span data-ttu-id="dadc4-111">BAM 入口網站可讓您執行搜尋、彙總資料並在 BAM 檢視 (屬於商務資料的觀點) 上設定警示。</span><span class="sxs-lookup"><span data-stu-id="dadc4-111">The BAM portal allows you to perform searches, aggregate data, and set alerts on a BAM view, which is a perspective on your business data.</span></span> <span data-ttu-id="dadc4-112">此可見性能夠為您的商務提供必要的 KPI 資訊，或是在您實作其他解決方案 (例如擴充 Microsoft Office Excel 試算表、使用 SQL Reporting 或建置自訂使用者介面 (UI)) 時，做為概念的證明。</span><span class="sxs-lookup"><span data-stu-id="dadc4-112">This visibility can provide the necessary KPI information for your business, or it can be used as proof of concept before you implement another solution such as extending a Microsoft Office Excel spreadsheet, using SQL Reporting, or building a custom user interface (UI).</span></span>  
  
## <a name="bam-portal-components"></a><span data-ttu-id="dadc4-113">BAM 入口網站元件</span><span class="sxs-lookup"><span data-stu-id="dadc4-113">BAM portal components</span></span>  
 <span data-ttu-id="dadc4-114">下列概要說明 BAM 入口網站元件。</span><span class="sxs-lookup"><span data-stu-id="dadc4-114">Following is a brief description of the BAM portal components.</span></span> <span data-ttu-id="dadc4-115">如需詳細資訊，請參閱＜另請參閱＞中的主題。</span><span class="sxs-lookup"><span data-stu-id="dadc4-115">For a more detailed description, see the topics in See Also.</span></span>  
  
### <a name="activity-searches"></a><span data-ttu-id="dadc4-116">活動搜尋</span><span class="sxs-lookup"><span data-stu-id="dadc4-116">Activity searches</span></span>  
 <span data-ttu-id="dadc4-117">您可以使用 BAM 入口網站對 BAM 資料執行搜尋，以尋找特定 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="dadc4-117">You use the BAM portal to perform searches against BAM data to find a specific BAM activity.</span></span> <span data-ttu-id="dadc4-118">您可以新增和移除搜尋子句，藉此建立查詢，以顯示符合您想要加以警示之準則的活動。</span><span class="sxs-lookup"><span data-stu-id="dadc4-118">You create queries by adding and removing search clauses that allow you to display those activities that match criteria for which you want to be alerted.</span></span>  
  
 <span data-ttu-id="dadc4-119">查詢可以儲存並重複使用，</span><span class="sxs-lookup"><span data-stu-id="dadc4-119">Queries can be saved and reused.</span></span> <span data-ttu-id="dadc4-120">也可以做為警示的基礎，例如收到特定客戶的訂單時的通知。</span><span class="sxs-lookup"><span data-stu-id="dadc4-120">They can also be the basis for an alert, such as a notification when a purchase order arrives from a specific customer.</span></span>  
  
### <a name="aggregations"></a><span data-ttu-id="dadc4-121">Aggregations</span><span class="sxs-lookup"><span data-stu-id="dadc4-121">Aggregations</span></span>  
 <span data-ttu-id="dadc4-122">入口網站可讓您擷取資料的快照集，並以圖形化圖表和樞紐分析表的形式顯示。</span><span class="sxs-lookup"><span data-stu-id="dadc4-122">The portal allows you to capture a snapshot of data and display it in the form of a graphical chart and accompanying PivotTable chart.</span></span> <span data-ttu-id="dadc4-123">此資料提供您對該程序或整體商務狀況的可見性。</span><span class="sxs-lookup"><span data-stu-id="dadc4-123">This data gives you visibility into the health of that process or the overall business.</span></span> <span data-ttu-id="dadc4-124">例如，使用者可能只需要簡單的圓形圖，顯示今天所收到的 1,000 張發票明細，以查看每張發票的處理階段 (400 張還在評估，400 張已拒絕，100 張已付款，100 張還在分配款項)。</span><span class="sxs-lookup"><span data-stu-id="dadc4-124">For example, a user may wish to see a simple pie chart that shows a breakdown of the 1,000 invoices received in a day in terms of what stage of processing has been reached by each invoice (400 still in "evaluation," 400 rejected, 100 paid, and 100 still in "fund allocation").</span></span>  
  
 <span data-ttu-id="dadc4-125">所呈現的資料可以做為建立警示的基礎，例如：如果超過 500 張發票都在「評估」階段時通知我。</span><span class="sxs-lookup"><span data-stu-id="dadc4-125">The data presented can be the basis for creating an alert, such as "Notify me if there are ever more than 500 invoices in the 'evaluation' stage of the process."</span></span>  
  
### <a name="alert-manager"></a><span data-ttu-id="dadc4-126">警示管理員</span><span class="sxs-lookup"><span data-stu-id="dadc4-126">Alert Manager</span></span>  
 <span data-ttu-id="dadc4-127">入口網站提供了使用者介面，可以用來建立警示和編輯現有警示。</span><span class="sxs-lookup"><span data-stu-id="dadc4-127">The portal provides a user interface for the creation of alerts and the editing of existing alerts.</span></span> <span data-ttu-id="dadc4-128">警示採用來自 [活動搜尋] 或 [彙總] 頁面所要監控的條件。</span><span class="sxs-lookup"><span data-stu-id="dadc4-128">Alerts take the conditions that are to be monitored from either the Activity Search or Aggregations page.</span></span> <span data-ttu-id="dadc4-129">您可以在「警示管理員」中填入警示的相關部分，例如通知對象、通知方式 (例如電子郵件)、其他人是否能看見以及訂閱警示等等。</span><span class="sxs-lookup"><span data-stu-id="dadc4-129">The Alert Manager is where you fill in the relevant parts of an alert, such as who to notify, how (for example, through e-mail), and whether others can see and subscribe to the alert.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dadc4-130">本節內容</span><span class="sxs-lookup"><span data-stu-id="dadc4-130">In This Section</span></span>  
  
-   [<span data-ttu-id="dadc4-131">BAM 入口網站的元件</span><span class="sxs-lookup"><span data-stu-id="dadc4-131">Components of the BAM Portal</span></span>](../core/components-of-the-bam-portal.md)  
  
-   [<span data-ttu-id="dadc4-132">規劃 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="dadc4-132">Planning for the BAM Portal</span></span>](../core/planning-for-the-bam-portal.md)  
  
-   [<span data-ttu-id="dadc4-133">BAM 入口網站中的活動搜尋</span><span class="sxs-lookup"><span data-stu-id="dadc4-133">Activity Searches in the BAM Portal</span></span>](../core/activity-searches-in-the-bam-portal.md)  
  
-   [<span data-ttu-id="dadc4-134">BAM 入口網站中的彙總</span><span class="sxs-lookup"><span data-stu-id="dadc4-134">Aggregations in the BAM Portal</span></span>](../core/aggregations-in-the-bam-portal.md)  
  
-   [<span data-ttu-id="dadc4-135">BAM 入口網站中的警示</span><span class="sxs-lookup"><span data-stu-id="dadc4-135">Alerts in the BAM Portal</span></span>](../core/alerts-in-the-bam-portal.md)  
  
-   [<span data-ttu-id="dadc4-136">BAM 入口網站的協助工具</span><span class="sxs-lookup"><span data-stu-id="dadc4-136">Accessibility for the BAM Portal</span></span>](../core/accessibility-for-the-bam-portal.md)  
  
-   [<span data-ttu-id="dadc4-137">BAM 入口網站的安全性考量</span><span class="sxs-lookup"><span data-stu-id="dadc4-137">Security Considerations for the BAM Portal</span></span>](../core/security-considerations-for-the-bam-portal.md)  
  
-   [<span data-ttu-id="dadc4-138">BAM 入口網站中的已知的問題</span><span class="sxs-lookup"><span data-stu-id="dadc4-138">Known Issues in the BAM Portal</span></span>](../core/known-issues-in-the-bam-portal.md)  
  
## <a name="see-also"></a><span data-ttu-id="dadc4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dadc4-139">See Also</span></span>  
 <span data-ttu-id="dadc4-140">[BAM 入口網站上的活動搜尋頁面](../core/activity-search-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="dadc4-140">[Activity Search on the BAM Portal Page](../core/activity-search-on-the-bam-portal-page.md) </span></span>  
 <span data-ttu-id="dadc4-141">[BAM 入口網站上的彙總頁面](../core/aggregations-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="dadc4-141">[Aggregations on the BAM Portal Page](../core/aggregations-on-the-bam-portal-page.md) </span></span>  
 [<span data-ttu-id="dadc4-142">BAM 入口網站上的警示管理員頁面</span><span class="sxs-lookup"><span data-stu-id="dadc4-142">Alert Manager on the BAM Portal Page</span></span>](../core/alert-manager-on-the-bam-portal-page.md)