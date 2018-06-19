---
title: ESB Management 入口網站功能參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8470b3af-8124-401b-b80f-3dc7346fed96
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdb9bd39ed46a7307d7fa6a6f57e5559a2fe46d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294406"
---
# <a name="esb-management-portal-feature-reference"></a><span data-ttu-id="85e83-102">ESB Management 入口網站功能參考</span><span class="sxs-lookup"><span data-stu-id="85e83-102">ESB Management Portal Feature Reference</span></span>
<span data-ttu-id="85e83-103">ESB 管理入口網站提供錯誤資訊的檢視，可讓您輕鬆監視、 管理和偵錯 ESB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="85e83-103">The ESB Management Portal provides views of fault information that make it easy to monitor, manage, and debug ESB applications.</span></span> <span data-ttu-id="85e83-104">它也提供可用來管理警示、 將 UDDI 資訊發佈和管理在入口網站的功能。</span><span class="sxs-lookup"><span data-stu-id="85e83-104">It also provides features that you can use to manage alerts, publish UDDI information, and administer the portal.</span></span> <span data-ttu-id="85e83-105">若要開啟 入口網站，請移至 http://localhost/ESB.Portal/。</span><span class="sxs-lookup"><span data-stu-id="85e83-105">To open the portal, go to http://localhost/ESB.Portal/.</span></span>  
  
 <span data-ttu-id="85e83-106">下列檢視可在入口網站：</span><span class="sxs-lookup"><span data-stu-id="85e83-106">The following views are available in the portal:</span></span>  
  
-   <span data-ttu-id="85e83-107">[入口網站首頁](../esb-toolkit/portal-home-page.md)。</span><span class="sxs-lookup"><span data-stu-id="85e83-107">[Portal Home Page](../esb-toolkit/portal-home-page.md).</span></span> <span data-ttu-id="85e83-108">此頁面會顯示整體的應用程式狀態、 錯誤的摘要、 UDDI 登錄和圖表，以顯示依類型或應用程式的錯誤明細的新要求。</span><span class="sxs-lookup"><span data-stu-id="85e83-108">This page displays the overall application state, a summary of faults, recent requests for UDDI registration, and charts that show a breakdown of faults by type and by application.</span></span>  
  
-   <span data-ttu-id="85e83-109">[入口網站錯誤網頁](../esb-toolkit/portal-faults-page.md)。</span><span class="sxs-lookup"><span data-stu-id="85e83-109">[Portal Faults Page](../esb-toolkit/portal-faults-page.md).</span></span> <span data-ttu-id="85e83-110">此頁面會顯示每一項錯誤; 的內容已截斷的清單依準則的範圍，它可以支援分析的錯誤。</span><span class="sxs-lookup"><span data-stu-id="85e83-110">This page displays a truncated list of properties for each fault; it supports analysis of faults by a range of criteria.</span></span>  
  
-   <span data-ttu-id="85e83-111">[入口網站的錯誤訊息檢視器](../esb-toolkit/portal-fault-message-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="85e83-111">[Portal Fault Message Viewer](../esb-toolkit/portal-fault-message-viewer.md).</span></span> <span data-ttu-id="85e83-112">此頁面才可以存取透過入口網站錯誤網頁。</span><span class="sxs-lookup"><span data-stu-id="85e83-112">This page is accessible only though the Portal Faults page.</span></span> <span data-ttu-id="85e83-113">它會顯示個別的錯誤訊息的詳細資料，並可讓您修復並重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="85e83-113">It displays details of individual fault messages and allows you to repair and resubmit messages.</span></span>  
  
-   <span data-ttu-id="85e83-114">[入口網站 [警示] 頁面](../esb-toolkit/portal-alerts-page.md)。</span><span class="sxs-lookup"><span data-stu-id="85e83-114">[Portal Alerts Page](../esb-toolkit/portal-alerts-page.md).</span></span> <span data-ttu-id="85e83-115">此頁面可讓使用者建立和修改警示，並設定警示的電子郵件設定。</span><span class="sxs-lookup"><span data-stu-id="85e83-115">This page allows users to create and modify alerts and to configure alert email settings.</span></span> <span data-ttu-id="85e83-116">入口網站可以傳送特定類型的錯誤或任何錯誤時的警示電子郵件訊息時，就會發生。</span><span class="sxs-lookup"><span data-stu-id="85e83-116">The portal can send an alert email message when a specific type of fault, or any fault, occurs.</span></span>  
  
-   <span data-ttu-id="85e83-117">[入口網站的報表頁面](../esb-toolkit/portal-reports-page.md)。</span><span class="sxs-lookup"><span data-stu-id="85e83-117">[Portal Reports Page](../esb-toolkit/portal-reports-page.md).</span></span> <span data-ttu-id="85e83-118">此頁面會顯示錯誤、 警示及重新提交訊息 」 活動從應用程式的觀點而言，指出圖表，並支援分析的應用程式中的個別服務的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="85e83-118">This page displays charts indicating the fault, alert, and message resubmission activity from an application perspective and supports analysis of the health of the individual services within applications.</span></span>  
  
-   <span data-ttu-id="85e83-119">[登錄入口網站頁面](../esb-toolkit/portal-registry-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="85e83-119">[Portal Registry Pages](../esb-toolkit/portal-registry-pages.md).</span></span> <span data-ttu-id="85e83-120">此頁面可讓 UDDI 服務使用者發佈服務端點 （例如，Microsoft BizTalk Server 接收位置）。</span><span class="sxs-lookup"><span data-stu-id="85e83-120">This page allows users to publish service endpoints (such as Microsoft BizTalk Server receive locations) to the UDDI service.</span></span> <span data-ttu-id="85e83-121">UDDI 服務可做為中央登錄的組織內服務端點。</span><span class="sxs-lookup"><span data-stu-id="85e83-121">The UDDI service acts as a central registry of service endpoints within an organization.</span></span>  
  
-   <span data-ttu-id="85e83-122">[入口網站管理頁面](../esb-toolkit/portal-admin-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="85e83-122">[Portal Admin Pages](../esb-toolkit/portal-admin-pages.md).</span></span> <span data-ttu-id="85e83-123">此頁面可讓系統管理員入口網站設定、 檢視稽核記錄的已編輯和重新提交訊息，以及管理使用者和群組的警示。</span><span class="sxs-lookup"><span data-stu-id="85e83-123">This page allows administrators to configure portal settings, view an audit log of edited and resubmitted messages, and manage alerts for users and groups.</span></span>  
  
-   <span data-ttu-id="85e83-124">[入口網站我的設定頁面](../esb-toolkit/portal-my-settings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="85e83-124">[Portal My Settings Page](../esb-toolkit/portal-my-settings-page.md).</span></span> <span data-ttu-id="85e83-125">此頁面可讓使用者選取的預設應用程式和入口網站的時間週期篩選條件。</span><span class="sxs-lookup"><span data-stu-id="85e83-125">This page allows users to select the default application and time-period filters for the portal.</span></span>