---
title: "監視節流 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d1d4c72-6942-4572-b27f-c58d37c94062
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d60b9f3deb77df927eb055b4504b809b421ae663
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-for-throttling"></a><span data-ttu-id="a4805-102">節流的監視</span><span class="sxs-lookup"><span data-stu-id="a4805-102">Monitoring for Throttling</span></span>
<span data-ttu-id="a4805-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件會監視效能計數器，以指出的節流狀態[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4805-103">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack monitors performance counters that indicate the throttling state of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="a4805-104">若要了解關於節流某些關鍵因素如下所示。</span><span class="sxs-lookup"><span data-stu-id="a4805-104">Some key factors to understand about throttling are listed below.</span></span>  
  
-   <span data-ttu-id="a4805-105">根據速率的節流是每個主控件和訊息的速率根據傳入與傳出訊息。</span><span class="sxs-lookup"><span data-stu-id="a4805-105">Rate-based throttling is per host and is based on the rate of messages inbound vs. outbound messages.</span></span>  
  
-   <span data-ttu-id="a4805-106">傳遞節流 」 的 (**MsgBox]-> [傳送埠或協調流程**)，輸入所從 messagebox 接收訊息的速率。</span><span class="sxs-lookup"><span data-stu-id="a4805-106">For delivery throttling (**MsgBox -> Send Port or Orchestration**), inbound rate is the rate at which messages are received from the message box.</span></span> <span data-ttu-id="a4805-107">輸出速率是在訊息成功傳送配接器透過的速率。</span><span class="sxs-lookup"><span data-stu-id="a4805-107">Outbound rate is the rate at which messages are successfully delivered via the adapters.</span></span>  
  
-   <span data-ttu-id="a4805-108">發佈節流的 (**接收配接器**或**協調流程]-> [MsgBox)，**輸入的速率是從配接器接收訊息的速率，以及輸出速率速率訊息插入 MsgBox。</span><span class="sxs-lookup"><span data-stu-id="a4805-108">For publishing throttling (**Receive adapters** or **Orchestrations -> MsgBox),** inbound rate is the rate at which messages are received from the adapters and outbound rate is the rate messages are plugged into the MsgBox.</span></span>  
  
-   <span data-ttu-id="a4805-109">任何節流機制存不在於資料庫中的郵件總數以外的主機之間。</span><span class="sxs-lookup"><span data-stu-id="a4805-109">No throttling mechanism exists between hosts other than total messages in the database.</span></span>  
  
 <span data-ttu-id="a4805-110">其他的背景資訊，請參閱主題[如何 BizTalk Server 實作主控件節流](http://go.microsoft.com/fwlink/?LinkID=155286)(http://go.microsoft.com/fwlink/?LinkID=155286) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="a4805-110">For additional background information, refer to the topic [How BizTalk Server Implements Host Throttling](http://go.microsoft.com/fwlink/?LinkID=155286) (http://go.microsoft.com/fwlink/?LinkID=155286) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a4805-111"> 整合了自我節流功能，可根據多個參數來協助防止伺服器負載過重。</span><span class="sxs-lookup"><span data-stu-id="a4805-111"> incorporates self-throttling, which helps to prevent overloading of the server based on various parameters.</span></span> <span data-ttu-id="a4805-112">導致節流發生的暫時負載過重並非重大的作業事件。</span><span class="sxs-lookup"><span data-stu-id="a4805-112">A temporary overload that causes throttling to occur is not an operationally significant event.</span></span> <span data-ttu-id="a4805-113">但是，在穩定的環境中不應該持續發生節流事件，這可能表示基礎結構層級有根本的問題。</span><span class="sxs-lookup"><span data-stu-id="a4805-113">Persistent throttling, however, is not expected in a stable environment and could indicate underlying problems at the infrastructure level.</span></span> <span data-ttu-id="a4805-114">管理組件提供主動式監視的效能臨界值規則與這類持續節流狀況。</span><span class="sxs-lookup"><span data-stu-id="a4805-114">The management pack provides proactive monitoring of such persistent throttling conditions with performance threshold rules.</span></span>  
  
 <span data-ttu-id="a4805-115">四個規則監視的使用情況/效能追蹤擴充下降的節流設定下表所示，四個不同狀況所造成。</span><span class="sxs-lookup"><span data-stu-id="a4805-115">Four utilization/performance tracking rules monitor for extended periods of throttling caused by four different conditions as indicated in the following table.</span></span>  
  
|<span data-ttu-id="a4805-116">條件</span><span class="sxs-lookup"><span data-stu-id="a4805-116">Condition</span></span>|<span data-ttu-id="a4805-117">規則</span><span class="sxs-lookup"><span data-stu-id="a4805-117">Rule</span></span>|  
|---------------|----------|  
|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a4805-118">服務處理序記憶體</span><span class="sxs-lookup"><span data-stu-id="a4805-118"> service process memory</span></span>|<span data-ttu-id="a4805-119">警告： BizTalk 針對節流，已高一段很長的處理序記憶體</span><span class="sxs-lookup"><span data-stu-id="a4805-119">Warning: BizTalk Throttled on High Process Memory for a significant period</span></span>|  
|<span data-ttu-id="a4805-120">正在處理的訊息數目</span><span class="sxs-lookup"><span data-stu-id="a4805-120">Number of messages being processed</span></span>|<span data-ttu-id="a4805-121">警告： BizTalk 節流，已在同處理序訊息計數高一段很長</span><span class="sxs-lookup"><span data-stu-id="a4805-121">Warning: BizTalk Throttled on High Inprocess Message Count for a significant period</span></span>|  
|<span data-ttu-id="a4805-122">中的執行緒數目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]程序</span><span class="sxs-lookup"><span data-stu-id="a4805-122">Number of threads in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process</span></span>|<span data-ttu-id="a4805-123">警告: BizTalk 針對高執行緒計數進行節流，已有一段很長的時間</span><span class="sxs-lookup"><span data-stu-id="a4805-123">Warning: BizTalk Throttled on High Thread Count for a significant period</span></span>|  
|<span data-ttu-id="a4805-124">大小[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫佇列</span><span class="sxs-lookup"><span data-stu-id="a4805-124">Size of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database queues</span></span>|<span data-ttu-id="a4805-125">警告: BizTalk 針對高資料庫大小進行節流，已有一段很長的時間</span><span class="sxs-lookup"><span data-stu-id="a4805-125">Warning: BizTalk Throttled on High Database Size for a significant period</span></span>|  
  
 <span data-ttu-id="a4805-126">這些閾值規則會使用根據節流狀態指示器效能計數器的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="a4805-126">These threshold rules use data providers based on throttling state indicator performance counters.</span></span> <span data-ttu-id="a4805-127">如需這些效能計數器的詳細資訊，請參閱章節[效能計數器](http://go.microsoft.com/fwlink/?LinkId=157269)(http://go.microsoft.com/fwlink/?LinkId=157269) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="a4805-127">For more information about these performance counters, refer to the section [Performance Counters](http://go.microsoft.com/fwlink/?LinkId=157269) (http://go.microsoft.com/fwlink/?LinkId=157269) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="a4805-128">這些規則都設定為特定數目的取樣的平均值超過特定的閾值時發出警示 （預設值是 30）。</span><span class="sxs-lookup"><span data-stu-id="a4805-128">These rules are configured to raise an alert if the average of over a certain number of samples crosses a particular threshold (default is 30).</span></span> <span data-ttu-id="a4805-129">比方說，「 警告： BizTalk 節流，已針對一段很長的高資料庫大小 」 是監視所有的節流狀態規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理程序中指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="a4805-129">For example, “Warning: BizTalk Throttled on High Database Size for a significant period” is a rule monitoring the throttling state of all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes in a given computer.</span></span> <span data-ttu-id="a4805-130">此規則使用的資料提供者，根據節流狀態指示器效能計數器 「 biztalk： 訊息代理程式-高資料庫大小。 」</span><span class="sxs-lookup"><span data-stu-id="a4805-130">This rule uses a data provider based on the throttling state indicator performance counter “BizTalk:Message Agent-High database size.”</span></span> <span data-ttu-id="a4805-131">如果這個效能計數器的值是 1，則關聯的程序會因為高資料庫大小而進行節流。</span><span class="sxs-lookup"><span data-stu-id="a4805-131">If this performance counter value is 1, then the associated process is throttling because of high database size.</span></span>  
  
 <span data-ttu-id="a4805-132">前述規則被設定為 30 的取樣的平均值和取樣的平均值高於 0.6 時發出警示。</span><span class="sxs-lookup"><span data-stu-id="a4805-132">The preceding rule is configured to take an average of 30 samples and raise an alert if the average of the samples is more than 0.6.</span></span> <span data-ttu-id="a4805-133">因為每個範例會在一分鐘的間隔內，這表示在過去 30 分鐘，節流該電腦中的至少一個或多個 BizTalk Server 處理序已因為高資料庫大小，60%的時間。</span><span class="sxs-lookup"><span data-stu-id="a4805-133">Since each sample is taken at an interval of one minute, this implies that over the past 30 minutes, at least one or more BizTalk Server processes in that computer were throttling because of high database size, 60 percent of the time.</span></span>  
  
 <span data-ttu-id="a4805-134">這個試誤可能不適合您的特定應用程式實例。</span><span class="sxs-lookup"><span data-stu-id="a4805-134">This heuristic may not suit your particular application scenario.</span></span> <span data-ttu-id="a4805-135">根據您的環境中的歷史行為，如之前所述，您應該設定這些規則以正確的值是：</span><span class="sxs-lookup"><span data-stu-id="a4805-135">Based on the historical behavior in your environment as described before, you should configure these rules with the correct values by either:</span></span>  
  
-   <span data-ttu-id="a4805-136">調整取樣。</span><span class="sxs-lookup"><span data-stu-id="a4805-136">Adjusting the samples.</span></span>  
  
-   <span data-ttu-id="a4805-137">調整臨界值。</span><span class="sxs-lookup"><span data-stu-id="a4805-137">Adjusting the threshold value.</span></span>  
  
-   <span data-ttu-id="a4805-138">如有必要，修改的提供者的取樣間隔。</span><span class="sxs-lookup"><span data-stu-id="a4805-138">If necessary, modifying the interval of sampling for the provider.</span></span>