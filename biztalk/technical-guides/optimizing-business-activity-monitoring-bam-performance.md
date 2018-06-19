---
title: 最佳化商務活動監控 (BAM) 效能 |Microsoft 文件
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
ms.openlocfilehash: 83801a4e147b3e1eaf34c5e264d6adecfbdf8f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298950"
---
# <a name="optimizing-business-activity-monitoring-bam-performance"></a><span data-ttu-id="3073e-102">最佳化商務活動監控 (BAM) 效能</span><span class="sxs-lookup"><span data-stu-id="3073e-102">Optimizing Business Activity Monitoring (BAM) Performance</span></span>
<span data-ttu-id="3073e-103">本主題說明商務活動監控 (BAM) 效能的因素。</span><span class="sxs-lookup"><span data-stu-id="3073e-103">This topic describes Business Activity Monitoring (BAM) performance factors.</span></span>  
  
## <a name="bam-disk-usage-configuration"></a><span data-ttu-id="3073e-104">磁碟使用量的 BAM 組態</span><span class="sxs-lookup"><span data-stu-id="3073e-104">BAM disk usage configuration</span></span>  
 <span data-ttu-id="3073e-105">BizTalk 系統負載下因為大量保存至 BAM 資料庫的資料時，BAM 會帶來大量負擔。</span><span class="sxs-lookup"><span data-stu-id="3073e-105">BAM incurs significant overhead when a BizTalk system is under load because of the significant amount of data that is persisted to the BAM database.</span></span> <span data-ttu-id="3073e-106">因此，審慎使用 BAM 資料庫的磁碟 I/O 技術是非常重要。</span><span class="sxs-lookup"><span data-stu-id="3073e-106">Therefore, judicious use of disk I/O techniques for the BAM database is critically important.</span></span>  
  
## <a name="bam-eventstream-apis"></a><span data-ttu-id="3073e-107">BAM 的 EventStream Api</span><span class="sxs-lookup"><span data-stu-id="3073e-107">BAM EventStream APIs</span></span>  
 <span data-ttu-id="3073e-108">可在 BizTalk BAM 實例中使用四種類型的 EventStreams︰</span><span class="sxs-lookup"><span data-stu-id="3073e-108">Four types of EventStreams are available for use in a BizTalk BAM scenario:</span></span>  
  
-   <span data-ttu-id="3073e-109">DirectEventStream (DES)</span><span class="sxs-lookup"><span data-stu-id="3073e-109">DirectEventStream (DES)</span></span>  
  
-   <span data-ttu-id="3073e-110">BufferedEventStream (BES)</span><span class="sxs-lookup"><span data-stu-id="3073e-110">BufferedEventStream (BES)</span></span>  
  
-   <span data-ttu-id="3073e-111">OrchestrationEventStream (OES)</span><span class="sxs-lookup"><span data-stu-id="3073e-111">OrchestrationEventStream (OES)</span></span>  
  
-   <span data-ttu-id="3073e-112">MessageEventStream (MES)</span><span class="sxs-lookup"><span data-stu-id="3073e-112">MessageEventStream (MES)</span></span>  
  
 <span data-ttu-id="3073e-113">您應該選擇其中一個這些應用程式開發介面，根據下列因素：</span><span class="sxs-lookup"><span data-stu-id="3073e-113">You should choose one of these APIs based on the following factors:</span></span>  
  
-   <span data-ttu-id="3073e-114">如果您擔心延遲，請選擇 DES，此時會使用與 BAM 主要匯入資料庫同步的方式來保存資料。</span><span class="sxs-lookup"><span data-stu-id="3073e-114">If your concern is latency, choose DES, where data is persisted synchronously to the BAM Primary Import database.</span></span>  
  
-   <span data-ttu-id="3073e-115">如果您擔心事件插入的效能和輸送量，請選擇非同步 API （BES、 OES 或 MES）。</span><span class="sxs-lookup"><span data-stu-id="3073e-115">If your concern is performance and throughput of event insertion, choose an asynchronous API (BES, OES or MES).</span></span>  
  
-   <span data-ttu-id="3073e-116">如果您要撰寫沒有的電腦執行的應用程式安裝 BizTalk Server，請使用 DES 和 BES;這些 Api 可用於非 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3073e-116">If you are writing an application that runs on a computer that does not have BizTalk Server installed, use DES and BES; these APIs can be used in non-BizTalk applications.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3073e-117">您可能會在一些情況下想要混合 EventStream 類型。</span><span class="sxs-lookup"><span data-stu-id="3073e-117">There are scenarios in which you may want to mix EventStream types.</span></span> <span data-ttu-id="3073e-118">比方說，管線處理，您可能想要擷取 BAM 中的特定資料不論是否在管線正在回復交易。</span><span class="sxs-lookup"><span data-stu-id="3073e-118">For example, for pipeline processing, you may want to capture the particular data in BAM regardless of whether the pipeline is rolling back its transaction.</span></span> <span data-ttu-id="3073e-119">特別是，您可能想要擷取資料的相關失敗的訊息數目或管線處理期間發生多少重試次數。</span><span class="sxs-lookup"><span data-stu-id="3073e-119">In particular, you may want capture data about how many messages failed or how many retries occurred during pipeline processing.</span></span> <span data-ttu-id="3073e-120">若要在這種情況下擷取資料，您應該使用 BES。</span><span class="sxs-lookup"><span data-stu-id="3073e-120">To capture the data in this situation you should use BES.</span></span>  
  
-   <span data-ttu-id="3073e-121">如果您的應用程式要在已安裝 BizTalk Server 的電腦上執行，請使用 MES 和 OES</span><span class="sxs-lookup"><span data-stu-id="3073e-121">If your application runs on a computer on which BizTalk Server is installed, use MES and OES.</span></span> <span data-ttu-id="3073e-122">(這些 API 只能從 BizTalk 應用程式使用)。</span><span class="sxs-lookup"><span data-stu-id="3073e-122">(These APIs are available only from BizTalk applications.)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3073e-123">OES 相當於 MES，但它適用於 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="3073e-123">OES is the equivalent of MES but for BizTalk orchestrations.</span></span>  
  
-   <span data-ttu-id="3073e-124">如果您想要與管線交易同步的 BAM 事件持續性，您應該使用訊息事件資料流 (MES)。</span><span class="sxs-lookup"><span data-stu-id="3073e-124">If you want BAM event persistence to be in sync with pipeline transaction, you should use a Messaging Event Stream (MES).</span></span>  
  
 <span data-ttu-id="3073e-125">所有非同步 EventStreams （BES、 MES 和 OES） 先將資料保存到 BizTalk MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3073e-125">All the asynchronous EventStreams (BES, MES, and OES) persist data first to the BizTalk MessageBox database.</span></span> <span data-ttu-id="3073e-126">然後再由 Tracking Data Decode Service (TDDS) 定期處理資料，並將資料保存到 BAM 主要匯入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="3073e-126">Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).</span></span>  
  
 <span data-ttu-id="3073e-127">如需有關 BAM 的 EventStream Api 的詳細資訊，請參閱[EventStream 類別](http://go.microsoft.com/fwlink/?LinkId=158046)(http://go.microsoft.com/fwlink/?LinkId=158046) 中的 BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="3073e-127">For more information about the BAM EventStream APIs, see [EventStream Classes](http://go.microsoft.com/fwlink/?LinkId=158046) (http://go.microsoft.com/fwlink/?LinkId=158046) in the BizTalk Server documentation.</span></span>  
  
## <a name="bam-performance-counters"></a><span data-ttu-id="3073e-128">BAM 效能計數器</span><span class="sxs-lookup"><span data-stu-id="3073e-128">BAM performance counters</span></span>  
 <span data-ttu-id="3073e-129">如需 BAM 的效能計數器的詳細清單，請參閱[BAM 效能計數器](http://go.microsoft.com/fwlink/?LinkId=158048)(http://go.microsoft.com/fwlink/?LinkId=158048) 中的 BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="3073e-129">For a detailed list of the performance counters for BAM, see [BAM Performance Counters](http://go.microsoft.com/fwlink/?LinkId=158048) (http://go.microsoft.com/fwlink/?LinkId=158048) in the BizTalk Server documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3073e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3073e-130">See Also</span></span>  
 [<span data-ttu-id="3073e-131">BizTalk Server 效能最佳化</span><span class="sxs-lookup"><span data-stu-id="3073e-131">Optimizing BizTalk Server Performance</span></span>](../technical-guides/optimizing-biztalk-server-performance.md)