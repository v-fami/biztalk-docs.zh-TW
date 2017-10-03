---
title: "BAM 入口網站頁面版面配置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal
- Portal page [BAM portal]
ms.assetid: 0d8833b7-dd2f-475c-a890-e925ee47d219
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5569021698eb856d7584a2510a27d69f092f37a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-portal-page-layout"></a><span data-ttu-id="d286a-102">BAM 入口網站頁面版面配置</span><span class="sxs-lookup"><span data-stu-id="d286a-102">BAM Portal Page Layout</span></span>
<span data-ttu-id="d286a-103">BAM 入口網站頁面的版面配置使用下列三個框架：</span><span class="sxs-lookup"><span data-stu-id="d286a-103">The BAM portal page is laid out in the following three frames:</span></span>  
  
-   <span data-ttu-id="d286a-104">橫幅</span><span class="sxs-lookup"><span data-stu-id="d286a-104">Banner</span></span>  
  
-   <span data-ttu-id="d286a-105">我的檢視</span><span class="sxs-lookup"><span data-stu-id="d286a-105">My Views</span></span>  
  
-   <span data-ttu-id="d286a-106">內容</span><span class="sxs-lookup"><span data-stu-id="d286a-106">Content</span></span>  
  
## <a name="banner"></a><span data-ttu-id="d286a-107">橫幅</span><span class="sxs-lookup"><span data-stu-id="d286a-107">Banner</span></span>  
 <span data-ttu-id="d286a-108">**橫幅**框架橫跨在入口網站頁面的頂端。</span><span class="sxs-lookup"><span data-stu-id="d286a-108">The **Banner** frame is located across the top of the portal page.</span></span> <span data-ttu-id="d286a-109">[橫幅] 框架包含商標資訊，如公司名稱和標誌、該頁面使用者介面 (UI) 的 [說明] 連結以及頁面標題。</span><span class="sxs-lookup"><span data-stu-id="d286a-109">The Banner frame contains branding information such as the company name and logo, links to Help for that page of the user interface (UI), and page titles.</span></span> <span data-ttu-id="d286a-110">您可以依據組織的需求自訂商標資訊。</span><span class="sxs-lookup"><span data-stu-id="d286a-110">You can customize the branding to conform to your organization's needs.</span></span> <span data-ttu-id="d286a-111">如需自訂橫幅中的商標資訊的詳細資訊，請參閱[自訂 BAM 入口網站組態](../core/customizing-the-bam-portal-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="d286a-111">For more information about customizing the branding information in the banner, see [Customizing the BAM Portal Configuration](../core/customizing-the-bam-portal-configuration.md).</span></span>  
  
## <a name="my-views"></a><span data-ttu-id="d286a-112">我的檢視</span><span class="sxs-lookup"><span data-stu-id="d286a-112">My Views</span></span>  
 <span data-ttu-id="d286a-113">**我的檢視**框架是在入口網站頁面的左半部。</span><span class="sxs-lookup"><span data-stu-id="d286a-113">The **My Views** frame is on the left side of the portal page.</span></span> <span data-ttu-id="d286a-114">[我的檢視] 會顯示目前的使用者有權檢視的所有項目。</span><span class="sxs-lookup"><span data-stu-id="d286a-114">My Views shows users all views for which they have been granted permissions.</span></span> <span data-ttu-id="d286a-115">使用者可以展開任一檢視，以查看在該檢視下可使用的功能。</span><span class="sxs-lookup"><span data-stu-id="d286a-115">Users can expand any view to see the features available to them for that view.</span></span> <span data-ttu-id="d286a-116">如果沒有顯示任何檢視，原因可能是因為尚未建立檢視 (通常是商務分析師的工作)，或尚未授與該使用者權限 (通常是系統管理員的工作)。</span><span class="sxs-lookup"><span data-stu-id="d286a-116">If there are no views shown, then either views have not been created, a task typically performed by a business analyst, or permissions have not been granted to the user, a task typically performed by an administrator.</span></span>  
  
 <span data-ttu-id="d286a-117">您可以在檢視中執行每個檢視所提供的三項工作：</span><span class="sxs-lookup"><span data-stu-id="d286a-117">Each view has three tasks that you can perform within the view:</span></span>  
  
-   <span data-ttu-id="d286a-118">**活動搜尋**： 可讓您建立查詢和活動為基礎的警示。</span><span class="sxs-lookup"><span data-stu-id="d286a-118">**Activity Search**: Allows you to create queries and alerts based on an activity.</span></span>  
  
-   <span data-ttu-id="d286a-119">**彙總**： 可讓您檢視彙總資料，並依據樞紐分析圖中的總計建立警示。</span><span class="sxs-lookup"><span data-stu-id="d286a-119">**Aggregations**: Allows you to view aggregate data and to create alerts based on totals in the PivotTable chart.</span></span>  
  
-   <span data-ttu-id="d286a-120">**警示管理員**： 可讓您建立、 編輯、 檢視和訂閱警示。</span><span class="sxs-lookup"><span data-stu-id="d286a-120">**Alert Manager**: Allows you to create, edit, view, and subscribe to alerts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d286a-121">如果您從「我的檢視」框架選取 [警示管理員]，則只能編輯現有的警示。</span><span class="sxs-lookup"><span data-stu-id="d286a-121">When selecting the Alert Manager from the My Views frame you can only edit an existing alert.</span></span> <span data-ttu-id="d286a-122">若要建立新警示，您必須從 [活動搜尋] 或 [彙總] 頁面移至 [警示管理員] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d286a-122">To create new alerts you must go to the Alerts Manager page from within the Activity Search or Aggregations page.</span></span>  
  
## <a name="content"></a><span data-ttu-id="d286a-123">內容</span><span class="sxs-lookup"><span data-stu-id="d286a-123">Content</span></span>  
 <span data-ttu-id="d286a-124">**內容**框架是在入口網站頁面的右側。</span><span class="sxs-lookup"><span data-stu-id="d286a-124">The **Content** frame is on the right side of the portal page.</span></span> <span data-ttu-id="d286a-125">內容頁面上包含各項「我的檢視」工作 ([活動搜尋]、[彙總] 和 [警示管理]) 所呈現的資訊。</span><span class="sxs-lookup"><span data-stu-id="d286a-125">The content page contains the information presented by each of the My View tasks (Activity Search, Aggregations, and Alert Management).</span></span> <span data-ttu-id="d286a-126">內容框架會隨著您選取的工作變更，以反映與該項工作相關聯的功能。</span><span class="sxs-lookup"><span data-stu-id="d286a-126">As you select a task, the content frame changes to reflect the functions associated with that task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d286a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d286a-127">See Also</span></span>  
 <span data-ttu-id="d286a-128">[BAM 入口網站上的活動搜尋頁面](../core/activity-search-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="d286a-128">[Activity Search on the BAM Portal Page](../core/activity-search-on-the-bam-portal-page.md) </span></span>  
 <span data-ttu-id="d286a-129">[BAM 入口網站上的彙總頁面](../core/aggregations-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="d286a-129">[Aggregations on the BAM Portal Page](../core/aggregations-on-the-bam-portal-page.md) </span></span>  
 <span data-ttu-id="d286a-130">[BAM 入口網站上的警示管理員頁面](../core/alert-manager-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="d286a-130">[Alert Manager on the BAM Portal Page](../core/alert-manager-on-the-bam-portal-page.md) </span></span>  
 [<span data-ttu-id="d286a-131">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="d286a-131">BAM Portal</span></span>](../core/bam-portal.md)