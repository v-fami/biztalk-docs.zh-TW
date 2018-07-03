---
title: 瞭解 DTA 追蹤效能行為 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b1a70951-bfed-435c-97f4-0b28a8e4e4dc
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c0f1749e87556d52ec9cc1ab84ed64f64a88c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979703"
---
# <a name="understanding-dta-tracking-performance-behavior"></a><span data-ttu-id="f3db6-102">瞭解 DTA 追蹤效能行為</span><span class="sxs-lookup"><span data-stu-id="f3db6-102">Understanding DTA Tracking Performance Behavior</span></span>
<span data-ttu-id="f3db6-103">決定 DTA 追蹤之最大持續性輸送量 (MST) 的主要因素如下：</span><span class="sxs-lookup"><span data-stu-id="f3db6-103">The primary factors that determine maximum sustainable throughput (MST) for DTA tracking are:</span></span>  
  
- <span data-ttu-id="f3db6-104">系統所需的訊息輸送量，也就是每單位時間所收到的訊息量。</span><span class="sxs-lookup"><span data-stu-id="f3db6-104">The desired message throughput, that is, messages received per unit time, for the system.</span></span>  
  
- <span data-ttu-id="f3db6-105">針對每一個訊息所追蹤的資料量。</span><span class="sxs-lookup"><span data-stu-id="f3db6-105">How much data is being tracked for each message.</span></span>  
  
- <span data-ttu-id="f3db6-106">資料在清除之前存留於 BizTalkDTADb 資料庫內的時間，也就是資料保留視窗。</span><span class="sxs-lookup"><span data-stu-id="f3db6-106">How long the data is to live in the BizTalkDTADb database before being purged, that is, the data retention window.</span></span>  
  
- <span data-ttu-id="f3db6-107">BizTalkDTADb 資料是否會封存和清除。</span><span class="sxs-lookup"><span data-stu-id="f3db6-107">Whether or not the BizTalkDTADb data is archived as well as purged.</span></span> <span data-ttu-id="f3db6-108">封存是選擇性，但是清除則必須定期執行。</span><span class="sxs-lookup"><span data-stu-id="f3db6-108">Archiving is optional but purging must be performed periodically.</span></span>  
  
  <span data-ttu-id="f3db6-109">還有一件事，所有這些因素有共通： 處 DTA 可以接受和處理的速度 （封存和清除） 的資料。</span><span class="sxs-lookup"><span data-stu-id="f3db6-109">There is one thing that all of these factors have in common: the speed at which the DTA can accept and process (archive and purge) data.</span></span>  
  
## <a name="how-the-biztalkdtadb-insert-and-processing-speed-affects-your-system"></a><span data-ttu-id="f3db6-110">BizTalkDTADb 插入和處理速度如何影響您的系統</span><span class="sxs-lookup"><span data-stu-id="f3db6-110">How the BizTalkDTADb Insert and Processing Speed Affects Your System</span></span>  
 <span data-ttu-id="f3db6-111">現在，讓我們逐步追蹤資料路徑中所述[測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)，並評估 BizTalkDTADb 插入和處理速度系統的各種元件的影響。</span><span class="sxs-lookup"><span data-stu-id="f3db6-111">Now, let’s walk through the tracking data pathway that is described in [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md), and evaluate the affect of BizTalkDTADb insert and processing speed on the various components of the system.</span></span>  
  
 <span data-ttu-id="f3db6-112">從 trackingdata 和 spool 資料表開始，我們可以想像如果將這些資料表的資料移到 BizTalkDTADb 資料庫的處理序將資料插入 BizTalkDTADb 資料庫時，其速度比不上執行階段插入 trackingdata 和 spool 資料表的速度，則 spool 和 trackingdata 資料表將會開始累積待處理項目。</span><span class="sxs-lookup"><span data-stu-id="f3db6-112">Starting with the trackingdata and spool tables, we can imagine that, if the processes that move data from these tables to the BizTalkDTADb database are not able to insert data into the BizTalkDTADb database at least as fast as the runtime is inserting into the trackingdata and spool tables, then the spool and trackingdata tables will start to build up a backlog.</span></span> <span data-ttu-id="f3db6-113">就短期而言，這未必是一件壞事，只要您知道訊息輸送量將會減少，最後讓待處理項目清空即可。</span><span class="sxs-lookup"><span data-stu-id="f3db6-113">This isn’t necessarily a bad thing in the short term as long as you know the message throughput will be reduced to allow the backlog to eventually drain.</span></span> <span data-ttu-id="f3db6-114">但是，一旦資料仍然位於 spool 或 trackingdata 資料表中，就無法在 BizTalkDTADb 資料庫中提供這些資料來供 [群組中樞] 頁面中的追蹤查詢或其他任何工具查詢，</span><span class="sxs-lookup"><span data-stu-id="f3db6-114">However, as long as the data is still sitting in the spool or trackingdata tables, it will not be available in the BizTalkDTADb database for querying by tracking queries on the Group Hub page or any other tool.</span></span>  <span data-ttu-id="f3db6-115">因此，無法用這些資料來解決問題。</span><span class="sxs-lookup"><span data-stu-id="f3db6-115">Thus it will not be useful for problem resolution.</span></span> <span data-ttu-id="f3db6-116">因此，任何預期的待處理項目期間必須要夠短，好讓追蹤的資訊依然能夠及時提供，以免萬一發生問題，而需要使用 BizTalkDTADb 資料來進行調查。</span><span class="sxs-lookup"><span data-stu-id="f3db6-116">Therefore any expected backlog periods must be short enough that the tracked information is still available in a timely fashion should a problem arise that needs to be investigated using BizTalkDTADb data.</span></span>  
  
 <span data-ttu-id="f3db6-117">透過測試，我們知道待處理項目是否累積的決定因素並不是將追蹤資料移到 BizTalkDTADb 資料庫的這些處理序 (也就是 TDDS 和 TrackedMessages_Copy_BizTalkMsgBoxDb)，而是 BizTalkDTADb 資料庫在接受輸入時的速度。</span><span class="sxs-lookup"><span data-stu-id="f3db6-117">From testing, we know that it isn’t the processes that move tracking data to the BizTalkDTADb database (that is, TDDS and TrackedMessages_Copy_BizTalkMsgBoxDb) that are the determining factor if a backlog builds up, but the speed of the BizTalkDTADb database in accepting the input.</span></span> <span data-ttu-id="f3db6-118">一般來說，繫結 I/O 的是 BizTalkDTADb 資料庫的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="f3db6-118">Typically, it is the data file of the BizTalkDTADb database that is I/O bound.</span></span> <span data-ttu-id="f3db6-119">也就是說，BizTalkDTADb 資料庫資料檔案所在的磁碟機速度將會決定整體 DTA 的速度。</span><span class="sxs-lookup"><span data-stu-id="f3db6-119">That is, it is the speed of the drive that the BizTalkDTADb database data file resides on that will determine the speed of the DTA overall.</span></span>  
  
## <a name="how-the-amount-of-data-in-biztalkdtadb-affects-io-speed"></a><span data-ttu-id="f3db6-120">BizTalkDTADb 中的資料數量如何影響 I/O 速度</span><span class="sxs-lookup"><span data-stu-id="f3db6-120">How the Amount of Data in BizTalkDTADb Affects I/O Speed</span></span>  
 <span data-ttu-id="f3db6-121">另一個相關的 I/O 速度的關鍵因素是 BizTalkDTADb 資料庫中的資料量： 為在 BizTalkDTADb 資料庫增加的追蹤資料數量，BizTalkDTADb 資料庫的輸入和處理速度會減少，因為沒有更多的資料當插入新的資料，而這會影響所需的每個插入的 I/O 數量，進行排序。</span><span class="sxs-lookup"><span data-stu-id="f3db6-121">Another key factor related to the I/O speed is the amount of data in the BizTalkDTADb database: as the amount of tracked data in the BizTalkDTADb database increases, the input and processing speed of the BizTalkDTADb database decreases since there is simply more data to sort through as new data is inserted, and this affects the amount of I/O required for each insert.</span></span>  
  
 <span data-ttu-id="f3db6-122">這就是封存和清除進入的時候，因為讓 BizTalkDTADb 資料庫不要變得太大而無法保存的就是這些處理序。</span><span class="sxs-lookup"><span data-stu-id="f3db6-122">This is where archiving and purging enter the picture since it is these processes that keep the BizTalkDTADb database from growing too large to keep up.</span></span> <span data-ttu-id="f3db6-123">基本的概念在於確保 BizTalkDTADb 資料庫大小低於開始在 spool 和 trackingdata 資料表中備份資料的大小。</span><span class="sxs-lookup"><span data-stu-id="f3db6-123">The basic idea is to make sure that the BizTalkDTADb database size is kept below the level at which things begin to backup in the spool and trackingdata tables.</span></span> <span data-ttu-id="f3db6-124">不過，在 DTA 清除與封存 (BizTalkDTADb) SQL 工作中實作的清除與封存程序也需要資源 （CPU、 記憶體和特別 I/O） 從 BizTalkDTADb 資料庫伺服器，測量 MST 時必須列入考量追蹤。</span><span class="sxs-lookup"><span data-stu-id="f3db6-124">However, the purge and archive processes implemented in the DTA Purge and Archive (BizTalkDTADb) SQL Job also require resources (CPU, Memory, and especially I/O) from the BizTalkDTADb database server, which must be taken into account when measuring MST with tracking.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3db6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3db6-125">See Also</span></span>  
 <span data-ttu-id="f3db6-126">[測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="f3db6-126">[Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md) </span></span>  
 <span data-ttu-id="f3db6-127">[測量 DAT 追蹤 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md) </span><span class="sxs-lookup"><span data-stu-id="f3db6-127">[Test Scenarios for Measuring MST of DTA Tracking](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md) </span></span>  
 <span data-ttu-id="f3db6-128">[尋找 DTA 追蹤的 MST 的秘訣和訣竅](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md) </span><span class="sxs-lookup"><span data-stu-id="f3db6-128">[Tips and Tricks for Finding MST of DTA Tracking](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md) </span></span>  
 [<span data-ttu-id="f3db6-129">調整追蹤資料庫大小的指導方針</span><span class="sxs-lookup"><span data-stu-id="f3db6-129">Tracking Database Sizing Guidelines</span></span>](../core/tracking-database-sizing-guidelines.md)