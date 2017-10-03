---
title: "BAM 攔截器效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9b64ae1-4d94-4c3c-add1-fa020713be5c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 989316edff34463905c7547db815b3daaf4d4a46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-interceptor-performance-counters"></a><span data-ttu-id="a4039-102">BAM 攔截器效能計數器</span><span class="sxs-lookup"><span data-stu-id="a4039-102">BAM Interceptor Performance Counters</span></span>
<span data-ttu-id="a4039-103">效能計數器可以讓您針對 BAM 攔截器所執行的工作在特定方面進行監控。</span><span class="sxs-lookup"><span data-stu-id="a4039-103">Performance counters allow you to monitor specific aspects of work performed by the BAM interceptors.</span></span> <span data-ttu-id="a4039-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="a4039-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="a4039-105">下表列出 BAM 攔截器可用的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="a4039-105">The following table lists the performance counters available for the BAM interceptors.</span></span> <span data-ttu-id="a4039-106">這些效能計數器的類別為「BAM 攔截器」。</span><span class="sxs-lookup"><span data-stu-id="a4039-106">The performance counters category is “BAM Interceptor.”</span></span>  
  
|<span data-ttu-id="a4039-107">計數器</span><span class="sxs-lookup"><span data-stu-id="a4039-107">Counter</span></span>|<span data-ttu-id="a4039-108">說明</span><span class="sxs-lookup"><span data-stu-id="a4039-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4039-109">Avg.失敗 BAM 事件/排清平均</span><span class="sxs-lookup"><span data-stu-id="a4039-109">Avg. Failed BAM Events/Flush Avg</span></span>|<span data-ttu-id="a4039-110">在排清資料到主要匯入資料庫期間，失敗 BAM 事件的平均次數。</span><span class="sxs-lookup"><span data-stu-id="a4039-110">The average number of failed BAM events that occurred during a flush of data to the Primary Import database.</span></span>|  
|<span data-ttu-id="a4039-111">成功 BAM 事件/排清</span><span class="sxs-lookup"><span data-stu-id="a4039-111">Successful BAM Events/Flush</span></span>|<span data-ttu-id="a4039-112">在資料排清到主要匯入資料庫期間，成功 BAM 事件的平均次數。</span><span class="sxs-lookup"><span data-stu-id="a4039-112">The average number of successful BAM events that occurred during a data flush to the Primary Import database.</span></span> <span data-ttu-id="a4039-113">如果交易已回復，事件可能不會保存到資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a4039-113">The events may not be persisted to the database if the transaction is rolled back.</span></span>|  
|<span data-ttu-id="a4039-114">Avg.擷取秒數/BAM 事件</span><span class="sxs-lookup"><span data-stu-id="a4039-114">Avg. Extraction sec/BAM Event</span></span>|<span data-ttu-id="a4039-115">用於擷取 BAM 事件的平均時間。</span><span class="sxs-lookup"><span data-stu-id="a4039-115">The average amount of time spent extracting BAM events.</span></span>|  
|<span data-ttu-id="a4039-116">Avg.排清秒數/BAM 事件</span><span class="sxs-lookup"><span data-stu-id="a4039-116">Avg. Flush sec/BAM Event</span></span>|<span data-ttu-id="a4039-117">用於排清 BAM 事件的平均時間。</span><span class="sxs-lookup"><span data-stu-id="a4039-117">The average amount of time spent flushing BAM events.</span></span>|  
|<span data-ttu-id="a4039-118">排清期間失敗的 BAM 事件總數</span><span class="sxs-lookup"><span data-stu-id="a4039-118">Total Failed BAM Events During Flush</span></span>|<span data-ttu-id="a4039-119">在資料排清期間，失敗的 BAM 事件總數。</span><span class="sxs-lookup"><span data-stu-id="a4039-119">The total number of failed BAM events that occurred during the data flush</span></span>|  
|<span data-ttu-id="a4039-120">排清期間成功的 BAM 事件總數</span><span class="sxs-lookup"><span data-stu-id="a4039-120">Total Successful BAM Events During Flush</span></span>|<span data-ttu-id="a4039-121">在排清到主要匯入資料庫期間，成功的 BAM 事件總數。</span><span class="sxs-lookup"><span data-stu-id="a4039-121">The total number of successful BAM events flushed to the Primary Import database.</span></span> <span data-ttu-id="a4039-122">如果交易已回復，事件可能不會保存到資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a4039-122">The events may not be persisted to the database if the transaction is rolled back.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4039-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4039-123">See Also</span></span>  
 [<span data-ttu-id="a4039-124">BAM 效能計數器</span><span class="sxs-lookup"><span data-stu-id="a4039-124">BAM Performance Counters</span></span>](../core/bam-performance-counters.md)