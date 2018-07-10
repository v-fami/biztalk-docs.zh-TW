---
title: 維護效能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae7e63ed-4e28-45b1-ab00-be9f9488a2e6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdaa00ebb244db6d389393a0bbf32c0075c1f3d3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984423"
---
# <a name="maintaining-performance"></a><span data-ttu-id="49c01-102">維護效能</span><span class="sxs-lookup"><span data-stu-id="49c01-102">Maintaining Performance</span></span>
<span data-ttu-id="49c01-103">本章節提供可協助您解決在例行維護檢查期間探索到的效能問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="49c01-103">This section provides information that is intended to help you resolve performance issues discovered during your routine maintenance checks.</span></span> <span data-ttu-id="49c01-104">您也可以使用的工具和技術，此處所述主動，來識別潛在的問題之前就嚴重的問題。</span><span class="sxs-lookup"><span data-stu-id="49c01-104">You can also use the tools and techniques described here proactively, to identify potential problems before they become critical issues.</span></span>  

 <span data-ttu-id="49c01-105">您通常必須在建立效能基準為用來評估目前的系統效能標準。</span><span class="sxs-lookup"><span data-stu-id="49c01-105">You will generally need to establish a performance baseline as a standard against which to assess current system performance.</span></span>  

 <span data-ttu-id="49c01-106">在本節中的主題，除了這份文件中的其他主題會解決效能問題。</span><span class="sxs-lookup"><span data-stu-id="49c01-106">In addition to the topics in this section, other topics in this document address performance issues.</span></span> <span data-ttu-id="49c01-107">這些主題會列出以下相關章節。</span><span class="sxs-lookup"><span data-stu-id="49c01-107">These topics are listed in Related Sections below.</span></span>  

## <a name="in-this-section"></a><span data-ttu-id="49c01-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="49c01-108">In This Section</span></span>  

-   [<span data-ttu-id="49c01-109">維護效能的最佳做法</span><span class="sxs-lookup"><span data-stu-id="49c01-109">Best Practices for Maintaining Performance</span></span>](../technical-guides/best-practices-for-maintaining-performance.md)  

-   [<span data-ttu-id="49c01-110">設定批次處理來改善配接器效能</span><span class="sxs-lookup"><span data-stu-id="49c01-110">Configuring Batching to Improve Adapter Performance</span></span>](../technical-guides/configuring-batching-to-improve-adapter-performance.md)  

-   [<span data-ttu-id="49c01-111">如何調整設定快取重新整理間隔</span><span class="sxs-lookup"><span data-stu-id="49c01-111">How to Adjust the Configuration Cache Refresh Interval</span></span>](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)  

-   [<span data-ttu-id="49c01-112">如何停用追蹤</span><span class="sxs-lookup"><span data-stu-id="49c01-112">How to Disable Tracking</span></span>](../technical-guides/how-to-disable-tracking.md)  

-   [<span data-ttu-id="49c01-113">疑難排解效能 Issues3</span><span class="sxs-lookup"><span data-stu-id="49c01-113">Troubleshooting Performance Issues3</span></span>](../technical-guides/troubleshooting-performance-issues3.md)  

## <a name="related-sections"></a><span data-ttu-id="49c01-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="49c01-114">Related Sections</span></span>  

- <span data-ttu-id="49c01-115">如需有關效能問題的請參閱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南 》，網址[ http://go.microsoft.com/fwlink/?LinkID=150492 ](http://go.microsoft.com/fwlink/?LinkID=150492)。</span><span class="sxs-lookup"><span data-stu-id="49c01-115">For more information about performance issues in general, see [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Performance Optimization Guide at [http://go.microsoft.com/fwlink/?LinkID=150492](http://go.microsoft.com/fwlink/?LinkID=150492).</span></span>  

- <span data-ttu-id="49c01-116">分析每週效能監視器記錄檔，針對 [基準] 和 [臨界值的相關資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)、 「 尋找並消除中的瓶頸"[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南[ http://go.microsoft.com/fwlink/?LinkId=154675 ](http://go.microsoft.com/fwlink/?LinkId=154675)，以及[疑難排解效能 Issues3](../technical-guides/troubleshooting-performance-issues3.md)。</span><span class="sxs-lookup"><span data-stu-id="49c01-116">For information about analyzing weekly performance monitor logs against baseline and thresholds, see [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md), "Finding and Eliminating Bottlenecks" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Performance Optimization Guide at [http://go.microsoft.com/fwlink/?LinkId=154675](http://go.microsoft.com/fwlink/?LinkId=154675), and [Troubleshooting Performance Issues3](../technical-guides/troubleshooting-performance-issues3.md).</span></span>  

- <span data-ttu-id="49c01-117">如需確保系統不會遇到經常自動成長[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[定義資料庫的自動成長設定](../technical-guides/defining-auto-growth-settings-for-databases.md)，「 追蹤資料庫大小調整指導方針 」 中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在協助[ http://go.microsoft.com/fwlink/?LinkId=154677 ](http://go.microsoft.com/fwlink/?LinkId=154677)，和中的 「 識別資料庫層中的瓶頸 」[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[ http://go.microsoft.com/fwlink/?LinkId=154678 ](http://go.microsoft.com/fwlink/?LinkId=154678)。</span><span class="sxs-lookup"><span data-stu-id="49c01-117">For information about ensuring that the system is not experiencing frequent auto-growth of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see [Defining Auto-Growth Settings for Databases](../technical-guides/defining-auto-growth-settings-for-databases.md), "Tracking Database Sizing Guidelines" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154677](http://go.microsoft.com/fwlink/?LinkId=154677), and "Identifying Bottlenecks in the Database Tier" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154678](http://go.microsoft.com/fwlink/?LinkId=154678).</span></span>  

- <span data-ttu-id="49c01-118">如需維護 SQL Server[執行的 SQL Server 維護程序](~/technical-guides/checklist-configuring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="49c01-118">For information about maintaining SQL Server, [Performing SQL Server Maintenance Procedures](~/technical-guides/checklist-configuring-sql-server.md).</span></span>  

- <span data-ttu-id="49c01-119">若要檢查長回應時間和高資源使用量的高負載期間執行 SQL Server Profiler 的相關資訊，請參閱 「 使用 SQL Server Profiler"在 SQL Server 說明在[ http://go.microsoft.com/fwlink/?LinkID=106720 ](http://go.microsoft.com/fwlink/?LinkID=106720)。</span><span class="sxs-lookup"><span data-stu-id="49c01-119">For information about running SQL Server Profiler during high load to check for long response times and high resource usage, see "Using SQL Server Profiler" in SQL Server Help at [http://go.microsoft.com/fwlink/?LinkID=106720](http://go.microsoft.com/fwlink/?LinkID=106720).</span></span>  

- <span data-ttu-id="49c01-120">確保所有配接器的訊息批次處理適用於資源耗用量或延遲的相關資訊，請參閱[設定批次處理來改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="49c01-120">For information about ensuring that message batching for all adapters is appropriate for resource consumption or latency, see [Configuring Batching to Improve Adapter Performance](../technical-guides/configuring-batching-to-improve-adapter-performance.md).</span></span>  

- <span data-ttu-id="49c01-121">如需增加 BizTalk Server 快取重新整理間隔的詳細資訊，請參閱 <<c0> [ 如何調整設定快取重新整理間隔](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)。</span><span class="sxs-lookup"><span data-stu-id="49c01-121">For information about increasing the BizTalk Server cache refresh interval, see [How to Adjust the Configuration Cache Refresh Interval](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md).</span></span>  

- <span data-ttu-id="49c01-122">輸入和輸出主控件節流的相關資訊，請參閱 「 主控件節流為何？ 」</span><span class="sxs-lookup"><span data-stu-id="49c01-122">For information about inbound and outbound host throttling, see "What is Host Throttling?"</span></span> <span data-ttu-id="49c01-123">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154694 ](http://go.microsoft.com/fwlink/?LinkId=154694)。</span><span class="sxs-lookup"><span data-stu-id="49c01-123">in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154694](http://go.microsoft.com/fwlink/?LinkId=154694).</span></span> <span data-ttu-id="49c01-124">如需觸發程序、 動作和輸入和輸出節流的緩解策略，請參閱 「 節流狀況觸發程序、 動作和緩解策略 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154695 ](http://go.microsoft.com/fwlink/?LinkId=154695)。</span><span class="sxs-lookup"><span data-stu-id="49c01-124">For information about triggers, actions, and mitigation strategies for inbound and outbound throttling, see "Throttling condition triggers, actions, and mitigation strategies" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154695](http://go.microsoft.com/fwlink/?LinkId=154695).</span></span>  

- <span data-ttu-id="49c01-125">若要使用通過傳送管線，而不是預設值 XML 傳送管線，請參閱 「 管理傳送埠使用 BizTalk 總管 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkID=154696 ](http://go.microsoft.com/fwlink/?LinkID=154696)。</span><span class="sxs-lookup"><span data-stu-id="49c01-125">To use a PassThrough send pipeline instead of the default XML send pipeline, see "Managing Send Ports Using BizTalk Explorer" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkID=154696](http://go.microsoft.com/fwlink/?LinkID=154696).</span></span>  

- <span data-ttu-id="49c01-126">調整追蹤資料庫大小的相關資訊，請參閱"追蹤資料庫大小調整指導方針 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154677 ](http://go.microsoft.com/fwlink/?LinkId=154677)。</span><span class="sxs-lookup"><span data-stu-id="49c01-126">For information about sizing the tracking database, see "Tracking Database Sizing Guidelines" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154677](http://go.microsoft.com/fwlink/?LinkId=154677).</span></span>  

- <span data-ttu-id="49c01-127">調整大小的 MessageBox，BizTalkDTADb、 BAMPrimaryImport 資料庫的相關資訊，請參閱 「 識別瓶頸在資料庫層 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154678 ](http://go.microsoft.com/fwlink/?LinkId=154678)。</span><span class="sxs-lookup"><span data-stu-id="49c01-127">For information about sizing the MessageBox, BizTalkDTADb, and BAMPrimaryImport databases, see "Identifying Bottlenecks in the Database Tier" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=154678](http://go.microsoft.com/fwlink/?LinkId=154678).</span></span>  

- <span data-ttu-id="49c01-128">如需避免爭用 MessageBox 資料庫中的資訊，請參閱[如何避免磁碟爭用](http://go.microsoft.com/fwlink/?LinkId=158809)([http://go.microsoft.com/fwlink/?LinkId=158809](http://go.microsoft.com/fwlink/?LinkId=158809)) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南。</span><span class="sxs-lookup"><span data-stu-id="49c01-128">For information about avoiding contention in the MessageBox database, see [How to Avoid Disk Contention](http://go.microsoft.com/fwlink/?LinkId=158809) ([http://go.microsoft.com/fwlink/?LinkId=158809](http://go.microsoft.com/fwlink/?LinkId=158809)) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Performance Optimization Guide.</span></span>
