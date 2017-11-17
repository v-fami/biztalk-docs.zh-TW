---
title: "BAM 效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], performance counters
- performance, counters [BAM]
ms.assetid: e23f7038-36a5-4957-bc73-47011763d109
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4307f72f149405fbc04e4e6cc51efe87229c2bff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-performance-counters"></a><span data-ttu-id="f7dfd-102">BAM 效能計數器</span><span class="sxs-lookup"><span data-stu-id="f7dfd-102">BAM Performance Counters</span></span>
<span data-ttu-id="f7dfd-103">效能計數器可以讓您針對 BAM 事件匯流排服務所執行的特定工作進行監控。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-103">Performance counters allow you to monitor specific aspects of work performed by the BAM Event Bus Service.</span></span> <span data-ttu-id="f7dfd-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="f7dfd-105">下表列出「商務活動監控」的可用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-105">The following table lists the performance counters available in Business Activity Monitoring.</span></span>  
  
|<span data-ttu-id="f7dfd-106">計數器</span><span class="sxs-lookup"><span data-stu-id="f7dfd-106">Counter</span></span>|<span data-ttu-id="f7dfd-107">說明</span><span class="sxs-lookup"><span data-stu-id="f7dfd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7dfd-108">正在處理的事件</span><span class="sxs-lookup"><span data-stu-id="f7dfd-108">Events being processed</span></span>|<span data-ttu-id="f7dfd-109">目前 BAM 事件匯流排服務正在處理的事件數</span><span class="sxs-lookup"><span data-stu-id="f7dfd-109">The number of events the BAM Event Bus Service is currently processing</span></span>|  
|<span data-ttu-id="f7dfd-110">正在處理的批次</span><span class="sxs-lookup"><span data-stu-id="f7dfd-110">Batches being processed</span></span>|<span data-ttu-id="f7dfd-111">目前 BAM 事件匯流排服務正在處理的批次數</span><span class="sxs-lookup"><span data-stu-id="f7dfd-111">The number of batches the BAM Event Bus Service is currently processing</span></span>|  
|<span data-ttu-id="f7dfd-112">認可的事件</span><span class="sxs-lookup"><span data-stu-id="f7dfd-112">Events Committed</span></span>|<span data-ttu-id="f7dfd-113">在上一秒內 BAM 事件匯流排服務對 SQL Server 認可的事件數。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-113">The number of events the BAM Event Bus Service has committed to SQL Server in the last second.</span></span>|  
|<span data-ttu-id="f7dfd-114">認可的記錄</span><span class="sxs-lookup"><span data-stu-id="f7dfd-114">Records Committed</span></span>|<span data-ttu-id="f7dfd-115">在上一秒內 BAM 事件匯流排服務對 SQL Server 認可的記錄數。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-115">The number of records the BAM Event Bus Service has committed to SQL Server in the last second.</span></span>|  
|<span data-ttu-id="f7dfd-116">認可的批次</span><span class="sxs-lookup"><span data-stu-id="f7dfd-116">Batches Committed</span></span>|<span data-ttu-id="f7dfd-117">在上一秒內 BAM 事件匯流排服務對 SQL Server 認可的批次數。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-117">The number of batches the BAM Event Bus Service has committed to SQL Server in the last second.</span></span>|  
|<span data-ttu-id="f7dfd-118">事件總數</span><span class="sxs-lookup"><span data-stu-id="f7dfd-118">Total Events</span></span>|<span data-ttu-id="f7dfd-119">從啟動到現在 BAM 事件匯流排服務已經處理的事件數。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-119">The number of events the BAM Event Bus Service has processed since you started it.</span></span>|  
|<span data-ttu-id="f7dfd-120">記錄總數</span><span class="sxs-lookup"><span data-stu-id="f7dfd-120">Total Records</span></span>|<span data-ttu-id="f7dfd-121">從啟動到現在 BAM 事件匯流排服務已經處理的記錄數。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-121">Then number of records the BAM Event Bus Service has processed since you started it.</span></span>|  
|<span data-ttu-id="f7dfd-122">批次總數</span><span class="sxs-lookup"><span data-stu-id="f7dfd-122">Total Batches</span></span>|<span data-ttu-id="f7dfd-123">從啟動到現在 BAM 事件匯流排服務已經處理的批次數。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-123">Then number of batches the BAM Event Bus Service has processed since you started it.</span></span>|  
|<span data-ttu-id="f7dfd-124">失敗的批次總數</span><span class="sxs-lookup"><span data-stu-id="f7dfd-124">Total Failed Batches</span></span>|<span data-ttu-id="f7dfd-125">從啟動到現在 BAM 事件匯流排服務無法處理的批次數。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-125">Then number of batches the BAM Event Bus Service has failed to process since you started it.</span></span>|  
|<span data-ttu-id="f7dfd-126">失敗的事件總數</span><span class="sxs-lookup"><span data-stu-id="f7dfd-126">Total Failed Events</span></span>|<span data-ttu-id="f7dfd-127">從啟動到現在 BAM 事件匯流排服務無法處理的事件數。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-127">Then number of events the BAM Event Bus Service has failed to process since you started it.</span></span>|  
  
 <span data-ttu-id="f7dfd-128">在「效能監視器」(perfmon) 中，效能計數器位於 BizTalk:TDDS 效能物件下。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-128">The performance counters are located in the Performance Monitor (perfmon) under the BizTalk:TDDS performance object.</span></span> <span data-ttu-id="f7dfd-129">效能計數器的執行個體名稱是來源伺服器名稱和來源資料庫名稱的組合。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-129">The instance name of the performance counters are a combination of the source server name and the name of the source database.</span></span> <span data-ttu-id="f7dfd-130">如果同一台電腦上有兩個 BAM 事件匯流排服務在兩個不同的來源資料庫上執行，您將會看見兩個 BAM 事件匯流排服務計數器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f7dfd-130">If two of the BAM Event Bus Services are running on the same computer against two different source databases, you will see two instances of the BAM Event Bus Service counters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7dfd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7dfd-131">See Also</span></span>  
 <span data-ttu-id="f7dfd-132">[管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md) </span><span class="sxs-lookup"><span data-stu-id="f7dfd-132">[Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md) </span></span>  
 <span data-ttu-id="f7dfd-133">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="f7dfd-133">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="f7dfd-134">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="f7dfd-134">Managing BAM</span></span>](../core/managing-bam.md)