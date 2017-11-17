---
title: "檢視即時 BAM 資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data, real-time data [BAM]
- BAM, real-time data
ms.assetid: 23e6561e-b570-49f4-bc4c-f4fbfde6fc81
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37610fee118d2bf6392189dddccdccd912c055b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="viewing-live-bam-data"></a><span data-ttu-id="cbbd8-102">檢視即時 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="cbbd8-102">Viewing Live BAM Data</span></span>
<span data-ttu-id="cbbd8-103">以下是可用來檢視即時 BAM 資料的各種方式。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-103">Following are the different ways you can view live BAM data.</span></span>  
  
-   <span data-ttu-id="cbbd8-104">檢視即時形成的或是從歷史 (封存) 記錄中發展出來的單一活動執行個體 (例如，「訂單」或「貸款程序」)。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-104">View a single activity instance (for example, Purchase Order or Loan Process) as it evolves in real-time or from the historical (archived) records.</span></span> <span data-ttu-id="cbbd8-105">這個檢視僅顯示與商務層級相關的資料，而隱藏不同實作的複雜性。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-105">This view shows only the data relevant at the business level and hides complexity of the diverse implementation.</span></span> <span data-ttu-id="cbbd8-106">如需檢視單一活動的執行個體的詳細資訊，請參閱[如何檢視個別活動](../core/how-to-view-an-individual-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-106">For more information about viewing a single activity instance, see [How to View an Individual Activity](../core/how-to-view-an-individual-activity.md).</span></span>  
  
-   <span data-ttu-id="cbbd8-107">巡覽至相關活動執行個體；例如，與指定「訂單」或一併附上的「發票」有關聯的「出貨」。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-107">Navigate to the related activity instances, for example, Shipments associated with given Purchase Order, or the Invoice in which it is included.</span></span> <span data-ttu-id="cbbd8-108">如需巡覽到相關的活動執行個體的詳細資訊，請參閱[如何檢視相關活動和相關文件](../core/how-to-view-related-activities-and-related-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-108">For more information about navigating to related activity instances, see [How to View Related Activities and Related Documents](../core/how-to-view-related-activities-and-related-documents.md).</span></span>  
  
-   <span data-ttu-id="cbbd8-109">瀏覽目前正在處理的或已經發生的所有商務活動的相關彙總 (關鍵效能指標)。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-109">Browse Aggregations (Key Performance Indicators) around all the Business Activities that are currently being processed or have already happened.</span></span> <span data-ttu-id="cbbd8-110">「彙總」可以「即時」執行，或是根據特定時間所進行活動的快照集來完成。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-110">The Aggregations can be done in Real-Time or can be based on a snapshot of the Activities taken at specific time.</span></span> <span data-ttu-id="cbbd8-111">如需有關如何瀏覽彙總的詳細資訊，請參閱[如何檢視 BAM 彙總](../core/how-to-view-bam-aggregations.md)。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-111">For more information about browsing aggregations, see [How to View BAM Aggregations](../core/how-to-view-bam-aggregations.md).</span></span>  
  
-   <span data-ttu-id="cbbd8-112">使用進度維度，BAM 中的一項新功能。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-112">Use Progress Dimensions, one of the new features in BAM.</span></span> <span data-ttu-id="cbbd8-113">這些維度允許對指定完成階段的活動進行篩選或分組。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-113">These dimensions allow filtering or grouping of the Activities at a given stage of completion.</span></span> <span data-ttu-id="cbbd8-114">如需進度維度的詳細資訊，請參閱[進度維度](../core/progress-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-114">For more information about Progress Dimensions, see [Progress Dimension](../core/progress-dimension.md).</span></span>  
  
-   <span data-ttu-id="cbbd8-115">根據進度或商務資料搜尋活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-115">Search for activity instances based on their progress or business data.</span></span> <span data-ttu-id="cbbd8-116">例如，您可以搜尋尚待客戶簽章的貸款和大於指定值的金額。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-116">For example, you can search for loans that are waiting for customer signature and the dollar amount is greater than a given value.</span></span> <span data-ttu-id="cbbd8-117">如需有關如何在 BAM 中搜尋活動的詳細資訊，請參閱[如何搜尋活動](../core/how-to-search-for-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="cbbd8-117">For more information about searching activities in BAM, see [How to Search for Activities](../core/how-to-search-for-activities.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cbbd8-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="cbbd8-118">In This Section</span></span>  
  
-   [<span data-ttu-id="cbbd8-119">如何檢視 BAM 彙總</span><span class="sxs-lookup"><span data-stu-id="cbbd8-119">How to View BAM Aggregations</span></span>](../core/how-to-view-bam-aggregations.md)  
  
-   [<span data-ttu-id="cbbd8-120">如何搜尋活動</span><span class="sxs-lookup"><span data-stu-id="cbbd8-120">How to Search for Activities</span></span>](../core/how-to-search-for-activities.md)  
  
## <a name="see-also"></a><span data-ttu-id="cbbd8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbbd8-121">See Also</span></span>  
 [<span data-ttu-id="cbbd8-122">使用 BAM 監控商務活動</span><span class="sxs-lookup"><span data-stu-id="cbbd8-122">Monitoring Business Activities with BAM</span></span>](../core/monitoring-business-activities-with-bam.md)