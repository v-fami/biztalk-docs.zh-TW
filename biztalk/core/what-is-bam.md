---
title: "何謂 BAM？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], monitoring
- profiles, monitoring
- monitoring, alerts
- KPIs, BAM
- BAM, alerts
- profiles
- BAM, KPIs
- BAM
- alerts, monitoring
- BAM, aggregations
- BAM, about BAM
- monitoring, profiles
- KPIs, monitoring
- monitoring, KPIs
- alerts, BAM
- monitoring, BAM
- profiles, BAM
ms.assetid: 5160026a-1ffe-457e-8b75-35ed9bb3457c
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81eb5a228bb5183c9f57c671424bad5e5be05088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-bam"></a><span data-ttu-id="b3a1d-103">何謂 BAM？</span><span class="sxs-lookup"><span data-stu-id="b3a1d-103">What Is BAM?</span></span>
<span data-ttu-id="b3a1d-104">「商務活動監控」(Business Activity Monitoring，BAM) 是一組工具集合，可以讓您管理彙總、警示與設定檔，以監視相關的商務計量 (稱為「關鍵效能指標」(Key Performance Indicators，KPI)。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-104">Business Activity Monitoring (BAM) is a collection of tools that allow you to manage aggregations, alerts, and profiles to monitor relevant business metrics (called Key Performance Indicators, or KPIs).</span></span> <span data-ttu-id="b3a1d-105">BAM 提供您商務程序的端對端可見性，以及有關不同作業、程序和交易之狀態及結果的精確資訊，以便讓您找出問題所在並解決商務上的議題。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-105">It gives you end-to-end visibility into your business processes, providing accurate information about the status and results of various operations, processes, and transactions so you can address problem areas and resolve issues within your business.</span></span>  
  
 <span data-ttu-id="b3a1d-106">BAM 架構提供一個簡單、即時、交易一致的方式來監控異質商務應用程式，並呈現 SQL 查詢資料與彙總報告 (OLAP)。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-106">The BAM Framework provides an easy, real-time, transaction-consistent way to monitor heterogeneous business applications, and to present data for SQL queries and aggregated reports (OLAP).</span></span> <span data-ttu-id="b3a1d-107">不論商務以何種方式自動化，透過查詢與彙總，您不僅可以包括在執行商務程序期間呈現的資料，還可以加入執行中商務程序的靜態與動態狀態。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-107">Through queries and aggregations you can include not only the data that is present during the running business process, but also the state and the dynamics of the running business process, independent of how the business is automated.</span></span>  
  
 <span data-ttu-id="b3a1d-108">BAM 會將操作商務智慧與應用程式整合技術運用到自動化程序，以便持續地根據來自操作事件的直接回應進行修正。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-108">BAM applies operational business intelligence and application integration technologies to automated processes to continually refine them based on feedback that comes directly from knowledge of operational events.</span></span> <span data-ttu-id="b3a1d-109">除了稽核商務程序 (以及商務程序管理系統)，BAM 還會傳送事件驅動警示，通知決策者商務有所變更，可能需要採取行動。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-109">In addition to auditing business processes (and business process management systems), BAM can send event-driven alerts that can be used to alert decision makers to changes in the business that may require action.</span></span>  
  
## <a name="why-use-bam"></a><span data-ttu-id="b3a1d-110">為何要使用 BAM？</span><span class="sxs-lookup"><span data-stu-id="b3a1d-110">Why use BAM?</span></span>  
 <span data-ttu-id="b3a1d-111">現今，企業通常會使用各種不同的商務應用程式 (例如客戶關係管理 (CRM)、SAP 以及訂單管理等等)，這些應用程式可能是向外採購而來，或是由企業內部所開發。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-111">The typical enterprise today uses a variety of business applications, such as customer relationship management (CRM), SAP, and order management, purchased or developed internally over time.</span></span> <span data-ttu-id="b3a1d-112">這些應用程式使用的技術大多不相同，並且可執行做為異質作業系統，範圍從使用 COM 和 COM+ 的 COBOL 程式到 C# 和 Java 等。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-112">These applications frequently use disparate technologies and run as heterogeneous operating systems, ranging from COBOL programs using COM and COM+, to C# and Java.</span></span>  
  
 <span data-ttu-id="b3a1d-113">然而，一般企業還是有許多地方需要人力操作，例如撥打電話、傳真與電子郵件等等。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-113">At the same time, many aspects of a typical enterprise are based on human actions, such as phone calls, faxes, and e-mail.</span></span> <span data-ttu-id="b3a1d-114">在這麼複雜的環境中，要瞭解整個商務的運作狀況，變得愈來愈困難。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-114">It becomes increasingly difficult to see “what is going on in the business” in such a complex environment.</span></span> <span data-ttu-id="b3a1d-115">眼看市場的速度愈來愈快，企業更是面臨到前所未有的艱鉅挑戰，必須快速做出決策才能抓住市場機會或避免蒙受損失。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-115">Nevertheless, with the increasing speed of the market, it is more crucial for enterprises to make quick decisions to take advantage of market opportunities or to prevent losses.</span></span>  
  
 <span data-ttu-id="b3a1d-116">想要減少分散式 IT 環境的成本，同時又希望能夠改善服務品質的 IT 管理員，可以採用 BAM 做為監控解決方案。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-116">BAM can be used as a monitoring solution by IT managers who want to cut the cost of their distributed IT environments while improving service quality.</span></span> <span data-ttu-id="b3a1d-117">BAM 能夠監管整個公司內的所有重大商務伺服器與應用程式，並提供工程、設計與生產部門高效能工作站和應用程式的垂直觀點。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-117">BAM provides management oversight of the business-critical servers and applications across your company and offers a vertical view of high-performance workstations and applications within engineering, design, and production divisions.</span></span>  
  
 <span data-ttu-id="b3a1d-118">BAM 會公開端對端商務程序的可見性需求。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-118">BAM exposes the visibility requirements of the end-to-end business process.</span></span> <span data-ttu-id="b3a1d-119">使用了解商務內各種角色與商務程序，以及了解的互動的資料需求的互動方式，與 Microsoft Office 中的 BAM 設計階段介面互動商務分析師Excel 透過 BAM 精靈來建立活動和檢視定義，以支援各種角色的這些可見性需求。</span><span class="sxs-lookup"><span data-stu-id="b3a1d-119">Using an understanding of how the various roles within the business interact with the business process as well as an understanding of the data requirements for the interactions, the business analyst interacts with the BAM design-time surface in Microsoft Office Excel through the BAM wizards to create activity and view definitions to support these visibility needs of the various roles.</span></span>  
  
 <span data-ttu-id="b3a1d-120">具體而言，BAM 提供下列優點解決企業面臨的各種挑戰：</span><span class="sxs-lookup"><span data-stu-id="b3a1d-120">More specifically, BAM addresses challenges facing enterprises as follows:</span></span>  
  
-   <span data-ttu-id="b3a1d-121">透過 BAM 入口網站提升商務使用者的能力</span><span class="sxs-lookup"><span data-stu-id="b3a1d-121">Business end user empowerment through the BAM portal</span></span>  
  
-   <span data-ttu-id="b3a1d-122">商務警示與通知</span><span class="sxs-lookup"><span data-stu-id="b3a1d-122">Business alerts and notifications</span></span>  
  
-   <span data-ttu-id="b3a1d-123">建立更好的可見性，提供更棒的使用經驗</span><span class="sxs-lookup"><span data-stu-id="b3a1d-123">Better visibility creation and consumption experience</span></span>  
  
-   <span data-ttu-id="b3a1d-124">商務程序的端對端可見性</span><span class="sxs-lookup"><span data-stu-id="b3a1d-124">End-to-end visibility of the business process</span></span>  
  
-   <span data-ttu-id="b3a1d-125">支援管線 (並間接支援配接器和 Web 服務)</span><span class="sxs-lookup"><span data-stu-id="b3a1d-125">Support for pipelines (and indirectly, adapters and Web services)</span></span>  
  
-   <span data-ttu-id="b3a1d-126">活動變更隨時生效</span><span class="sxs-lookup"><span data-stu-id="b3a1d-126">Immediate Activity change-on-the-fly</span></span>  
  
-   <span data-ttu-id="b3a1d-127">攔截器與追蹤設定檔方針</span><span class="sxs-lookup"><span data-stu-id="b3a1d-127">Interceptor and tracking profile guidelines</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a1d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3a1d-128">See Also</span></span>  
 <span data-ttu-id="b3a1d-129">[使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md) </span><span class="sxs-lookup"><span data-stu-id="b3a1d-129">[Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md) </span></span>  
 <span data-ttu-id="b3a1d-130">[BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="b3a1d-130">[BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="b3a1d-131">[追蹤設定檔編輯器](../core/tracking-profile-editor.md) </span><span class="sxs-lookup"><span data-stu-id="b3a1d-131">[Tracking Profile Editor](../core/tracking-profile-editor.md) </span></span>  
 <span data-ttu-id="b3a1d-132">[BAM 入口網站](../core/bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="b3a1d-132">[BAM Portal](../core/bam-portal.md) </span></span>  
 [<span data-ttu-id="b3a1d-133">使用商務活動監控</span><span class="sxs-lookup"><span data-stu-id="b3a1d-133">Using Business Activity Monitoring</span></span>](../core/using-business-activity-monitoring.md)