---
title: "排程彙總 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, aggregations
- scheduling, aggregations [BAM]
- aggregations [BAM], scheduling
ms.assetid: 4e2da2eb-b1fc-4b27-98d6-564e6df719e1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cf2558b046d53deb6036553c5206beebd4d80ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scheduled-aggregations"></a><span data-ttu-id="c99c3-102">排程彙總</span><span class="sxs-lookup"><span data-stu-id="c99c3-102">Scheduled Aggregations</span></span>
<span data-ttu-id="c99c3-103">BAM 排程彙總是以動態產生的 OLAP Cube 和 Data Transformation Services (DTS) 封裝為基礎。</span><span class="sxs-lookup"><span data-stu-id="c99c3-103">BAM bases scheduled aggregations on dynamically generated OLAP cubes and Data Transformation Services (DTS) packages.</span></span> <span data-ttu-id="c99c3-104">排程彙總的資料代表商務活動在 DTS 封裝啟動時的快照。</span><span class="sxs-lookup"><span data-stu-id="c99c3-104">The data in scheduled aggregations represents a snapshot of your business activities when you start your DTS package.</span></span> <span data-ttu-id="c99c3-105">若要達成此目的，分析的 DTS 封裝的第一個步驟是預存程序的呼叫**bam_Metadata_BeginAnalysis** ，將會擷取快照集組成：</span><span class="sxs-lookup"><span data-stu-id="c99c3-105">To achieve this, the first step of the DTS package for analysis is a call to the stored procedure **bam_Metadata_BeginAnalysis** that will retrieve a snapshot consisting of:</span></span>  
  
-   <span data-ttu-id="c99c3-106">所有進行中之活動執行個體的快照複本</span><span class="sxs-lookup"><span data-stu-id="c99c3-106">A snapshot copy of all activity instances in progress</span></span>  
  
-   <span data-ttu-id="c99c3-107">檢視表，代表從上次執行 DTS 封裝到製作快照當時，將已完成的活動執行個體累加的視窗</span><span class="sxs-lookup"><span data-stu-id="c99c3-107">A view that represents an incremental window on the completed activity instances from the moment that you ran the DTS package for the last time to the moment of the snapshot</span></span>  
  
 <span data-ttu-id="c99c3-108">為此，BAM 會極短暫地獨佔鎖定活動儲存區，以免在同一時間寫入任何資料。</span><span class="sxs-lookup"><span data-stu-id="c99c3-108">BAM achieves this by taking an exclusive lock on the Activity Storage for a very short time, thus preventing any data writing at the same time.</span></span> <span data-ttu-id="c99c3-109">一旦 BAM 製作快照時，DTS 封裝可能需要花費較長的時間進行處理，而 BAM 則將會忽略處理期間所送達的任何資料。</span><span class="sxs-lookup"><span data-stu-id="c99c3-109">Once BAM takes the snapshot, the DTS package might take a long time to run, but BAM will ignore any new data that arrives during the processing.</span></span> <span data-ttu-id="c99c3-110">下圖說明這類活動：</span><span class="sxs-lookup"><span data-stu-id="c99c3-110">The following figure illustrates this activity:</span></span>  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig9.gif "ebiz_prog_bam_data_maint_fig9")  
<span data-ttu-id="c99c3-111">BAM 排程彙總</span><span class="sxs-lookup"><span data-stu-id="c99c3-111">BAM Scheduled Aggregations</span></span>  
  
 <span data-ttu-id="c99c3-112">在此圖中，BAM 將已完成的活動執行個體之相關資料，移至已完成的執行個體 OLAP Cube。</span><span class="sxs-lookup"><span data-stu-id="c99c3-112">In the figure, BAM moves data about the completed activity instances to the Completed Instances OLAP cube.</span></span> <span data-ttu-id="c99c3-113">BAM 以累加方式處理此 Cube。</span><span class="sxs-lookup"><span data-stu-id="c99c3-113">BAM incrementally processes this cube.</span></span>  
  
 <span data-ttu-id="c99c3-114">同時，BAM 也將仍在進行中之活動的相關資料移至作用中的執行個體 Cube，以交由 DTS 封裝全權處理。</span><span class="sxs-lookup"><span data-stu-id="c99c3-114">At the same time, BAM moves the data about the activities still in progress to the Active Instances cube, which the DTS package fully processes.</span></span> <span data-ttu-id="c99c3-115">這是可以接受的做法，因為 BAM 假設任何特定時段只有少數活動仍在進行中。</span><span class="sxs-lookup"><span data-stu-id="c99c3-115">This is acceptable, because BAM assumes that only a relatively small number of activities are in progress at any given moment.</span></span>  
  
 <span data-ttu-id="c99c3-116">排程彙總的資料存放於虛擬 Cube，此 Cube 隱藏了已完成活動與目前活動之間的差異。</span><span class="sxs-lookup"><span data-stu-id="c99c3-116">Data for the scheduled aggregations is available from a virtual cube that hides the difference between the completed and current activities.</span></span> <span data-ttu-id="c99c3-117">如需詳細資訊，請參閱[查詢排程的彙總資料](../core/querying-scheduled-aggregated-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c99c3-117">For more information, see [Querying Scheduled Aggregated Data](../core/querying-scheduled-aggregated-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99c3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c99c3-118">See Also</span></span>  
 [<span data-ttu-id="c99c3-119">什麼是彙總？</span><span class="sxs-lookup"><span data-stu-id="c99c3-119">What Is an Aggregation?</span></span>](../core/what-is-an-aggregation.md)