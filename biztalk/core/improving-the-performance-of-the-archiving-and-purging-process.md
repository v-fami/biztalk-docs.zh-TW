---
title: 提升的效能，封存和清除程序 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- archiving [Tracking database], system performance
- DTA Purge and Archive job, performance
- purging, limitations
- performance, archiving
- performance, purging
- purging, system performance
ms.assetid: d65da58d-65e0-4f6c-8b15-5d4448049b42
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3876021fec4d604960d672671cab8bf4be1dc0a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257838"
---
# <a name="improving-the-performance-of-the-archiving-and-purging-process"></a><span data-ttu-id="54364-102">改善封存及清除程序的效能</span><span class="sxs-lookup"><span data-stu-id="54364-102">Improving the Performance of the Archiving and Purging Process</span></span>
<span data-ttu-id="54364-103">視您設計 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實例的情況、[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 實例處理訊息的大小和數量以及您設定的追蹤方式而定，儲存在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫中的資料量可能會非常快速地擴增。</span><span class="sxs-lookup"><span data-stu-id="54364-103">The amount of data stored in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases can grow very quickly depending on how you have designed your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] scenario, depending on the number and size of messages processed by your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] scenario, and depending on how you have configured tracking.</span></span> <span data-ttu-id="54364-104">將資料庫大小保持在狀況良好的限度，處理起來會更有效率，而且系統中的資料量也能隨時維持正常水準。</span><span class="sxs-lookup"><span data-stu-id="54364-104">By maintaining your database size at a healthy level, processing is more efficient and the amount of data in your system is normalized at any given time.</span></span> <span data-ttu-id="54364-105">這樣就可以提供有效率且一致的效能。</span><span class="sxs-lookup"><span data-stu-id="54364-105">This provides efficient and consistent performance.</span></span> <span data-ttu-id="54364-106">將此程序自動化，可讓您省卻手動維護資料庫的負擔。</span><span class="sxs-lookup"><span data-stu-id="54364-106">By automating this process you free yourself of the burden of manually maintaining your databases.</span></span>  
  
## <a name="configuring-a-healthy-environment"></a><span data-ttu-id="54364-107">設定狀況良好的環境</span><span class="sxs-lookup"><span data-stu-id="54364-107">Configuring a healthy environment</span></span>  
 <span data-ttu-id="54364-108">您用於維護良好 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的策略，高度依賴您特定的實例及所用的硬體。</span><span class="sxs-lookup"><span data-stu-id="54364-108">Your strategy in maintaining a healthy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment is heavily dependent on your particular scenario and the hardware it is running on.</span></span> <span data-ttu-id="54364-109">要監控的主要事項為「BizTalk 追蹤」(BizTalkDTADb) 資料庫的成長率及大小。</span><span class="sxs-lookup"><span data-stu-id="54364-109">The key things to monitor are the rate of growth and the size of your BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="54364-110">追蹤資料庫的少數幾個資料表佔有資料庫大小的大部分，因此會在執行階段影響效能。</span><span class="sxs-lookup"><span data-stu-id="54364-110">A few tables of the tracking database account for bulk of the database size and hence the performance impact on runtime.</span></span>  
  
 <span data-ttu-id="54364-111">依據現有追蹤點的多寡、有多少不同的訊息在使用中、訊息大小和使用的訊息內文追蹤層級，您可以設定同樣的實例來產生大為不同的追蹤資料數量。</span><span class="sxs-lookup"><span data-stu-id="54364-111">The same scenario can be configured to produce vastly different amount of tracking data based on how many tracking points are present, how many different messages are used, size of the messages and the level of message body tracking used.</span></span> <span data-ttu-id="54364-112">以下是一些需要監控的重要因數：</span><span class="sxs-lookup"><span data-stu-id="54364-112">Following are some important factors to monitor:</span></span>  
  
-   <span data-ttu-id="54364-113">追蹤點數目 - 例如管線、協調流程和連接埠</span><span class="sxs-lookup"><span data-stu-id="54364-113">Number of tracking points - such as pipelines, orchestrations, and ports</span></span>  
  
-   <span data-ttu-id="54364-114">追蹤的訊息屬性數目</span><span class="sxs-lookup"><span data-stu-id="54364-114">Number of message properties tracked</span></span>  
  
-   <span data-ttu-id="54364-115">每個內送訊息的訊息數目</span><span class="sxs-lookup"><span data-stu-id="54364-115">Number of messages per incoming message</span></span>  
  
-   <span data-ttu-id="54364-116">訊息大小</span><span class="sxs-lookup"><span data-stu-id="54364-116">Message size</span></span>  
  
-   <span data-ttu-id="54364-117">傳輸速率 (平均與尖峰)</span><span class="sxs-lookup"><span data-stu-id="54364-117">Traffic rate (average and peak)</span></span>  
  
-   <span data-ttu-id="54364-118">訊息內文追蹤組態</span><span class="sxs-lookup"><span data-stu-id="54364-118">Message body tracking configuration</span></span>  
  
 <span data-ttu-id="54364-119">在考慮自動封存和清除資料時，請考慮您需要在追蹤資料庫中保留多少即時資料。</span><span class="sxs-lookup"><span data-stu-id="54364-119">When considering automatic archiving and purging of data consider how much live data you need to keep in your tracking database.</span></span> <span data-ttu-id="54364-120">您必須視環境需要微調「DTA 清除與封存」工作參數，讓清除效能可以支援即時資料的目標數量，而不致降低效能。</span><span class="sxs-lookup"><span data-stu-id="54364-120">You need to tune the DTA Purge and Archive job parameters as appropriate for your environment so that the targeted amount of live data can be supported by the purging performance without degradation.</span></span>  
  
 <span data-ttu-id="54364-121">「DTA 清除與封存」工作可以在指定的時間間隔內清除特定的資料量。</span><span class="sxs-lookup"><span data-stu-id="54364-121">The DTA Purge and Archive job can purge a certain amount of data within a given time interval.</span></span> <span data-ttu-id="54364-122">工作的容量取決於執行的實例、目前的資料庫大小和硬體。</span><span class="sxs-lookup"><span data-stu-id="54364-122">The capacity of the job depends on the scenarios running, the current database size, and the hardware.</span></span> <span data-ttu-id="54364-123">若要擁有穩定的環境，您必須在內送追蹤資料的產生與清除之間取得平衡。</span><span class="sxs-lookup"><span data-stu-id="54364-123">In order to have a stable environment, you must have a balance between the incoming tracking data generation and purging.</span></span> <span data-ttu-id="54364-124">在測試環境中，您可以變動資料的存留窗期和清除工作的頻率來找到平衡。</span><span class="sxs-lookup"><span data-stu-id="54364-124">In your test environment, you can find the balance by varying the live window of data and the frequency of the purging job.</span></span> <span data-ttu-id="54364-125">在平衡狀態中，系統將會傳送持續性輸送量。</span><span class="sxs-lookup"><span data-stu-id="54364-125">In a balanced state, your system will deliver sustainable throughput.</span></span> <span data-ttu-id="54364-126">您的目標就是要在 BizTalk 追蹤資料庫資料表大小會造成持續的重大效能問題之前，提供足夠的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="54364-126">Your goal is to have enough of a buffer before the BizTalk Tracking database table size causes sustained, significant performance issues.</span></span>  
  
## <a name="performance-limitations"></a><span data-ttu-id="54364-127">效能限制</span><span class="sxs-lookup"><span data-stu-id="54364-127">Performance limitations</span></span>  
 <span data-ttu-id="54364-128">不是所有的實例都會相應調整清除效能。</span><span class="sxs-lookup"><span data-stu-id="54364-128">Purging performance will not scale for all scenarios.</span></span> <span data-ttu-id="54364-129">任何實例都可能產生不斷增加的追蹤資料數量。</span><span class="sxs-lookup"><span data-stu-id="54364-129">For any scenario, it is possible to generate increasing amounts of tracking data.</span></span> <span data-ttu-id="54364-130">一貫以較低的速率清除追蹤資料時，追蹤資料庫大小會增長，並且進一步讓清除效能變得更糟。</span><span class="sxs-lookup"><span data-stu-id="54364-130">When tracking data is purged at a consistently slower rate, there is a buildup of the tracking database size, which worsens the purging performance further.</span></span>  
  
 <span data-ttu-id="54364-131">在無法維持負載的情況下，複製訊息內文的動作也會變得更慢，並且還可能在 MessageBox 資料庫造成積存現象。</span><span class="sxs-lookup"><span data-stu-id="54364-131">Under unsustainable load conditions, the copying of message bodies may also become slower and there may become a backlog in the MessageBox database.</span></span> <span data-ttu-id="54364-132">就極端的情況而論，每日的訊息內文複製和追蹤可能會產生即使其中包含相關的執行個體資訊、卻沒有訊息內文的封存。</span><span class="sxs-lookup"><span data-stu-id="54364-132">Under extreme conditions, the daily message body copying and tracking may lead to archives where the message body is not available even though it contains related instance information.</span></span> <span data-ttu-id="54364-133">基本上，高負載期間會和低負載期間交替出現，讓工作可以在低負載期間跟上進度。</span><span class="sxs-lookup"><span data-stu-id="54364-133">Typically, periods of high loads alternate with periods of low load and enable the job to catch up during periods of low load.</span></span>  
  
 <span data-ttu-id="54364-134">由於持續清除資料庫並壓縮儲存的追蹤資料，封存和清除 BizTalk 追蹤資料庫應該會大幅降低發生無法維持負載之情況的可能性。</span><span class="sxs-lookup"><span data-stu-id="54364-134">Archiving and purging the BizTalk Tracking database should considerably reduce the possibility of unsustainable load conditions because of the continuous pruning of the database and the compaction of stored tracking data.</span></span> <span data-ttu-id="54364-135">這些程序將大幅減少手動介入的需要。</span><span class="sxs-lookup"><span data-stu-id="54364-135">These processes greatly reduce the need for manual intervention.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54364-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54364-136">See Also</span></span>  
 [<span data-ttu-id="54364-137">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="54364-137">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)