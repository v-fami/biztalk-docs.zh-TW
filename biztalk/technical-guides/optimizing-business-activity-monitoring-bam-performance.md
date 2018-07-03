---
title: 最佳化商務活動監控 (BAM) 效能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9ed29b2-0be6-4a37-be68-9476832fd49f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f28771f2611a8b5f7c2522b7cd45e875897645e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996199"
---
# <a name="optimizing-business-activity-monitoring-bam-performance"></a><span data-ttu-id="289d8-102">最佳化商務活動監控 (BAM) 效能</span><span class="sxs-lookup"><span data-stu-id="289d8-102">Optimizing Business Activity Monitoring (BAM) Performance</span></span>
<span data-ttu-id="289d8-103">本主題說明商務活動監控 (BAM) 效能的因素。</span><span class="sxs-lookup"><span data-stu-id="289d8-103">This topic describes Business Activity Monitoring (BAM) performance factors.</span></span>  
  
## <a name="bam-disk-usage-configuration"></a><span data-ttu-id="289d8-104">BAM 磁碟使用量組態</span><span class="sxs-lookup"><span data-stu-id="289d8-104">BAM disk usage configuration</span></span>  
 <span data-ttu-id="289d8-105">當 BizTalk 系統因為大量的資料會保存至 BAM 資料庫，而低於負載時，BAM 就會產生相當大的負擔。</span><span class="sxs-lookup"><span data-stu-id="289d8-105">BAM incurs significant overhead when a BizTalk system is under load because of the significant amount of data that is persisted to the BAM database.</span></span> <span data-ttu-id="289d8-106">因此，審慎使用 BAM 資料庫的磁碟 I/O 技術是非常重要。</span><span class="sxs-lookup"><span data-stu-id="289d8-106">Therefore, judicious use of disk I/O techniques for the BAM database is critically important.</span></span>  
  
## <a name="bam-eventstream-apis"></a><span data-ttu-id="289d8-107">BAM 的 EventStream Api</span><span class="sxs-lookup"><span data-stu-id="289d8-107">BAM EventStream APIs</span></span>  
 <span data-ttu-id="289d8-108">EventStreams 的四種可供在 BizTalk BAM 實例中使用：</span><span class="sxs-lookup"><span data-stu-id="289d8-108">Four types of EventStreams are available for use in a BizTalk BAM scenario:</span></span>  
  
- <span data-ttu-id="289d8-109">DirectEventStream (DES)</span><span class="sxs-lookup"><span data-stu-id="289d8-109">DirectEventStream (DES)</span></span>  
  
- <span data-ttu-id="289d8-110">BufferedEventStream (BES)</span><span class="sxs-lookup"><span data-stu-id="289d8-110">BufferedEventStream (BES)</span></span>  
  
- <span data-ttu-id="289d8-111">OrchestrationEventStream (OES)</span><span class="sxs-lookup"><span data-stu-id="289d8-111">OrchestrationEventStream (OES)</span></span>  
  
- <span data-ttu-id="289d8-112">MessageEventStream (MES)</span><span class="sxs-lookup"><span data-stu-id="289d8-112">MessageEventStream (MES)</span></span>  
  
  <span data-ttu-id="289d8-113">您應該選擇其中一個這些 Api，根據下列因素：</span><span class="sxs-lookup"><span data-stu-id="289d8-113">You should choose one of these APIs based on the following factors:</span></span>  
  
- <span data-ttu-id="289d8-114">如果您擔心延遲，請選擇 DES，此時會使用與 BAM 主要匯入資料庫同步的方式來保存資料。</span><span class="sxs-lookup"><span data-stu-id="289d8-114">If your concern is latency, choose DES, where data is persisted synchronously to the BAM Primary Import database.</span></span>  
  
- <span data-ttu-id="289d8-115">如果您擔心事件插入的效能和輸送量，請選擇非同步 API （BES、 OES 或 MES）。</span><span class="sxs-lookup"><span data-stu-id="289d8-115">If your concern is performance and throughput of event insertion, choose an asynchronous API (BES, OES or MES).</span></span>  
  
- <span data-ttu-id="289d8-116">如果您正在撰寫的應用程式，並沒有在電腦上執行 BizTalk Server 安裝，請使用 DES 和 BES;這些 Api 可以用於非 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="289d8-116">If you are writing an application that runs on a computer that does not have BizTalk Server installed, use DES and BES; these APIs can be used in non-BizTalk applications.</span></span>  
  
  > [!NOTE]  
  >  <span data-ttu-id="289d8-117">您可能會在一些情況下想要混合 EventStream 類型。</span><span class="sxs-lookup"><span data-stu-id="289d8-117">There are scenarios in which you may want to mix EventStream types.</span></span> <span data-ttu-id="289d8-118">比方說，管線處理，您可能想要擷取 BAM 中的特定資料不論是否管線是否回復其交易。</span><span class="sxs-lookup"><span data-stu-id="289d8-118">For example, for pipeline processing, you may want to capture the particular data in BAM regardless of whether the pipeline is rolling back its transaction.</span></span> <span data-ttu-id="289d8-119">特別是，您可能想要擷取資料的相關失敗的訊息數目或管線處理期間發生的次數。</span><span class="sxs-lookup"><span data-stu-id="289d8-119">In particular, you may want capture data about how many messages failed or how many retries occurred during pipeline processing.</span></span> <span data-ttu-id="289d8-120">若要在這種情況下擷取資料，您應該使用 BES。</span><span class="sxs-lookup"><span data-stu-id="289d8-120">To capture the data in this situation you should use BES.</span></span>  
  
- <span data-ttu-id="289d8-121">如果您的應用程式要在已安裝 BizTalk Server 的電腦上執行，請使用 MES 和 OES</span><span class="sxs-lookup"><span data-stu-id="289d8-121">If your application runs on a computer on which BizTalk Server is installed, use MES and OES.</span></span> <span data-ttu-id="289d8-122">(這些 API 只能從 BizTalk 應用程式使用)。</span><span class="sxs-lookup"><span data-stu-id="289d8-122">(These APIs are available only from BizTalk applications.)</span></span>  
  
  > [!NOTE]  
  >  <span data-ttu-id="289d8-123">OES 相當於 MES，但它適用於 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="289d8-123">OES is the equivalent of MES but for BizTalk orchestrations.</span></span>  
  
- <span data-ttu-id="289d8-124">如果您想要與管線交易同步的 BAM 事件持續性，您應該使用訊息事件 Stream (MES)。</span><span class="sxs-lookup"><span data-stu-id="289d8-124">If you want BAM event persistence to be in sync with pipeline transaction, you should use a Messaging Event Stream (MES).</span></span>  
  
  <span data-ttu-id="289d8-125">所有非同步 EventStreams （BES、 MES 和 OES） 先將資料保存到 BizTalk MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="289d8-125">All the asynchronous EventStreams (BES, MES, and OES) persist data first to the BizTalk MessageBox database.</span></span> <span data-ttu-id="289d8-126">然後再由 Tracking Data Decode Service (TDDS) 定期處理資料，並將資料保存到 BAM 主要匯入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="289d8-126">Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).</span></span>  
  
  <span data-ttu-id="289d8-127">如需有關 BAM 的 EventStream Api 的詳細資訊，請參閱 < [EventStream 類別](http://go.microsoft.com/fwlink/?LinkId=158046)(http://go.microsoft.com/fwlink/?LinkId=158046) BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="289d8-127">For more information about the BAM EventStream APIs, see [EventStream Classes](http://go.microsoft.com/fwlink/?LinkId=158046) (http://go.microsoft.com/fwlink/?LinkId=158046) in the BizTalk Server documentation.</span></span>  
  
## <a name="bam-performance-counters"></a><span data-ttu-id="289d8-128">BAM 效能計數器</span><span class="sxs-lookup"><span data-stu-id="289d8-128">BAM performance counters</span></span>  
 <span data-ttu-id="289d8-129">如需 BAM 的效能計數器的詳細清單，請參閱[BAM 效能計數器](http://go.microsoft.com/fwlink/?LinkId=158048)(http://go.microsoft.com/fwlink/?LinkId=158048) BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="289d8-129">For a detailed list of the performance counters for BAM, see [BAM Performance Counters](http://go.microsoft.com/fwlink/?LinkId=158048) (http://go.microsoft.com/fwlink/?LinkId=158048) in the BizTalk Server documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289d8-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="289d8-130">See Also</span></span>  
 [<span data-ttu-id="289d8-131">最佳化 BizTalk Server 效能</span><span class="sxs-lookup"><span data-stu-id="289d8-131">Optimizing BizTalk Server Performance</span></span>](../technical-guides/optimizing-biztalk-server-performance.md)