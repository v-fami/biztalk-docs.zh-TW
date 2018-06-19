---
title: MessageBox 延遲問題疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9eb5789-80bd-40d4-8c27-7ae117fd9232
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e37fc970230bf218bcfd820611fb6b87322e535
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279870"
---
# <a name="troubleshooting-messagebox-latency-issues"></a><span data-ttu-id="32836-102">MessageBox 延遲問題疑難排解</span><span class="sxs-lookup"><span data-stu-id="32836-102">Troubleshooting MessageBox Latency Issues</span></span>
<span data-ttu-id="32836-103">在理想的世界裡，所有的訊息都應該在發佈到 MessageBox 資料庫時就進行處理和傳遞，這樣 MessageBox 資料庫的大小永遠都不會過度膨脹。</span><span class="sxs-lookup"><span data-stu-id="32836-103">In a perfect world, all messages would be processed and delivered as soon as they were published to the MessageBox database and the MessageBox database would never grow to an excessive size.</span></span> <span data-ttu-id="32836-104">負責定期清除 MessageBox 資料庫資料表的 SQL 代理程式工作，會將 MessageBox 中不再受到參考的訊息立即移除。</span><span class="sxs-lookup"><span data-stu-id="32836-104">Any messages in the MessageBox that were no longer referenced would immediately be removed by the SQL agent jobs that periodically clean up the MessageBox database tables.</span></span>  
  
 <span data-ttu-id="32836-105">不過，在真實世界的案例中，通常不是以可預期的線性方式接收訊息，所以 SQL 代理程式工作需要時間來清除 MessageBox 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="32836-105">In real world scenarios, however, messages are not typically received in a predictable, linear fashion and the SQL agent jobs require time to clean up the MessageBox database tables.</span></span>  
  
 <span data-ttu-id="32836-106">因此，在某些案例中，MessageBox 可能會膨脹地相當快速。</span><span class="sxs-lookup"><span data-stu-id="32836-106">Therefore, in some scenarios; the MessageBox can grow fairly large very quickly.</span></span>  
  
 <span data-ttu-id="32836-107">下列情況可能會導致 MessageBox 過度膨脹而妨礙了整體效能：</span><span class="sxs-lookup"><span data-stu-id="32836-107">The following items can cause the MessageBox to grow excessively large and hinder overall performance:</span></span>  
  
-   <span data-ttu-id="32836-108">**具有 「 允許主控件追蹤 」 設定選項的 Biztalk 主控件執行個體已停止**。</span><span class="sxs-lookup"><span data-stu-id="32836-108">**The Biztalk Host instance that has the "allow Host tracking" option set is stopped**.</span></span> <span data-ttu-id="32836-109">這是負責將追蹤資料從 MessageBox 資料庫移至 BizTalk 追蹤資料庫 (BizTalkDTADb) 的主控件。</span><span class="sxs-lookup"><span data-stu-id="32836-109">This is the host that is responsible for moving the tracking data from the MessageBox database to the Biztalk Tracking database(BizTalkDTADb).</span></span>  
  
-   <span data-ttu-id="32836-110">**SQL Server 代理程式未執行**這種情況不執行 SQL 工作負責將資料從 MessageBox 資料庫移到 BizTalkDTADb 資料庫 [並且之後會清除在 MessageBox 中移動的資料]。</span><span class="sxs-lookup"><span data-stu-id="32836-110">**SQL Server Agent is not running** This can happen if the SQL jobs responsible for moving data from the MessageBox database to the BizTalkDTADb database [subsequently purging the moved data in the MessageBox] are not running.</span></span> <span data-ttu-id="32836-111">SQL 代理程式服務必須隨時都在執行，才能避免這種問題。</span><span class="sxs-lookup"><span data-stu-id="32836-111">It is imperative the SQL Agent Service be running all the time to avoid this problem.</span></span>  
  
-   <span data-ttu-id="32836-112">**SQL Server 作業已停用**即使 SQL Server Agent 正在執行，請務必無預設 SQL Server 工作停用。</span><span class="sxs-lookup"><span data-stu-id="32836-112">**SQL Server Jobs are disabled** Even if the SQL Server Agent is running, it is imperative that none of the default SQL Server jobs be disabled.</span></span>  
  
-   <span data-ttu-id="32836-113">**BizTalkDTADb 資料庫過度膨脹**這種情況，BizTalkDTADb 資料庫變得十分龐大，而導致插入 BizTalkDTADb 資料庫需要更長時間。</span><span class="sxs-lookup"><span data-stu-id="32836-113">**BizTalkDTADb database grows excessively** This can happen if the BizTalkDTADb database grows very large, causing inserts into the BizTalkDTADb database to take longer.</span></span> <span data-ttu-id="32836-114">發生這種情況時，「追蹤資料傳遞服務」(Tracking Data Delivery Service，TDDS) 速度會變慢，導致 MessageBox 資料庫的待處理項目增多。</span><span class="sxs-lookup"><span data-stu-id="32836-114">When this happens the movement of data by Tracking Data Delivery Service (TDDS) slows down, causing a backlog build up in the MessageBox database.</span></span> <span data-ttu-id="32836-115">為了避免這個問題，您必須定期在 BizTalkDTADb 資料庫上執行 SQL 伺服器封存並將工作清除。</span><span class="sxs-lookup"><span data-stu-id="32836-115">To avoid this problem it is important to run the SQL server archive and purge jobs periodically on the BizTalkDTADb databases.</span></span>  
  
-   <span data-ttu-id="32836-116">**磁碟 I/O 過度延遲**如果 MessageBox 資料庫的資料的傳入速度會比系統能夠處理更快，並將資料移到 BizTalkDTADb 資料庫中，待處理項目可以建置在 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="32836-116">**Excessive Disk I/O Latency** If the incoming rate of data into the MessageBox database is faster than which the system can process and move the data to the BizTalkDTADb database, backlog can build up in the MessageBox database.</span></span> <span data-ttu-id="32836-117">如果待處理的項目持續增多而無緩解，就會造成嚴重的問題，系統效能可能隨時間增長而每況愈下。</span><span class="sxs-lookup"><span data-stu-id="32836-117">If the backlog continues to grow unabated, this is a very serious problem and system performance will degrade over time.</span></span> <span data-ttu-id="32836-118">一種紓解這個問題的方式，是安裝速度更快的磁碟及 (或) 升級硬體，以協助確保系統可以從訊息積存的情況復原。</span><span class="sxs-lookup"><span data-stu-id="32836-118">One way to alleviate this problem is to install faster disks and/or upgrade the hardware to help ensure that the system is capable of recovering from any message backlogs experienced over time.</span></span>  
  
## <a name="plan-for-the-future"></a><span data-ttu-id="32836-119">計畫未來</span><span class="sxs-lookup"><span data-stu-id="32836-119">Plan for the Future</span></span>  
 <span data-ttu-id="32836-120">即使遵守了上述所有的最佳作法，隨著時間增長，移到 BizTalkDTADb 資料庫的追蹤資料量仍會累積成很大的量。</span><span class="sxs-lookup"><span data-stu-id="32836-120">Even though all the best practices above are followed, over time the volume of tracking data moved to the BizTalkDTADb database will grow very large.</span></span> <span data-ttu-id="32836-121">您必須實作資料庫維護計畫，以定期封存追蹤資料，使系統仍可保持最佳效能。</span><span class="sxs-lookup"><span data-stu-id="32836-121">It is important to implement a database maintenance plan to periodically archive tracking data so that the system can continue to perform optimally.</span></span>  
  
 <span data-ttu-id="32836-122">可保留在 BizTalkDTADb 資料庫中的歷程資料量，是依照系統所處理的訊息量而定。</span><span class="sxs-lookup"><span data-stu-id="32836-122">The amount of historical data that can be retained in the BizTalkDTADb database depends on the volume of messages pushed through the system.</span></span> <span data-ttu-id="32836-123">對於工作量及輸送量不會暴增的系統而言，這個資料庫膨脹的速度較慢，可在 BizTalkDTADb 資料庫中保留較多的歷程資料。</span><span class="sxs-lookup"><span data-stu-id="32836-123">For systems that are not subjected to high stress and throughput this database will grow at a slower rate and it will be possible to retain more historical data in the BizTalkDTADb database.</span></span>  
  
 <span data-ttu-id="32836-124">建議您在 BizTalkDTADb 資料庫中保留最少量的資料，如此就不會影響執行階段的效能。</span><span class="sxs-lookup"><span data-stu-id="32836-124">It is recommended to retain minimal data in the BizTalkDTADb database so that runtime performance is not sacrificed.</span></span>