---
title: "加速負載測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overdrive load test
- LoadGen tool, overdrive load test
ms.assetid: 0d16d0a8-4255-4f5a-86a2-26cc11bb9a70
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54ea40d17bdb59fa3fcdc2db31a18b3286b70659
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="overdrive-load-test"></a><span data-ttu-id="e550b-102">加速負載測試</span><span class="sxs-lookup"><span data-stu-id="e550b-102">Overdrive Load Test</span></span>
<span data-ttu-id="e550b-103">本主題中的資訊是指中所說明的測試[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="e550b-103">The information in this topic refers to the tests explained in [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span></span>  
  
 <span data-ttu-id="e550b-104">「負載產生」工具 LoadGen 2007 可讓您在 BizTalk Server 系統上模擬負載過重的情形。</span><span class="sxs-lookup"><span data-stu-id="e550b-104">The Load Generation tool, LoadGen 2007, enables you to simulate heavy loads on a BizTalk Server system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e550b-105">LoadGen 2007 工具是下載[http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841)。</span><span class="sxs-lookup"><span data-stu-id="e550b-105">The LoadGen 2007 tool is available for download at [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841).</span></span> <span data-ttu-id="e550b-106">此工具的舊版，BizTalk Server 2004 負載產生工具是下載[http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999)。</span><span class="sxs-lookup"><span data-stu-id="e550b-106">The previous version of this tool, the BizTalk Server 2004 Load Generation Tool is available for download at [http://go.microsoft.com/fwlink/?linkid=108999](http://go.microsoft.com/fwlink/?linkid=108999).</span></span>  
  
 <span data-ttu-id="e550b-107">為了模擬連續超載的系統，LoadGen 2007 的傳送速度是設定為 410 msgs/sec，比已測量的最大持續輸送量多 120 msgs/sec。</span><span class="sxs-lookup"><span data-stu-id="e550b-107">To simulate a continuously overdriven system, LoadGen 2007 was configured to send about 410 msgs/sec, 120 msgs/sec more than the measured maximum sustainable throughput.</span></span>  
  
 <span data-ttu-id="e550b-108">測試的設計目的不僅是為了加速系統，也是希望瞭解從大約 2 百萬筆記錄的多工緩衝處理積存深度復原需要多少時間。</span><span class="sxs-lookup"><span data-stu-id="e550b-108">The test was designed not only to overdrive the system, but also to get an idea of how long it would take to recover from a spool backlog depth of around 2 million records.</span></span>  
  
 <span data-ttu-id="e550b-109">若要達到這個目的，系統會以增加速率運作，直到多工緩衝處理深度達到約 2 百萬筆記錄為止。</span><span class="sxs-lookup"><span data-stu-id="e550b-109">To accomplish this, the system was driven at the increased rate until the spool depth was around 2 million records.</span></span> <span data-ttu-id="e550b-110">一旦多工緩衝處理深度到達所需的程度後，就不會繼續產生負載。</span><span class="sxs-lookup"><span data-stu-id="e550b-110">Once the spool depth reached the desired level then no further load was generated.</span></span>  
  
 <span data-ttu-id="e550b-111">若要確保 BizTalk 節流機制未節流接收主控件，而這可避免多工緩衝處理表格積存累積，**訊息 DB 中的計數**的接收主控件已經從節流處理臨界值預設值 50000 調高為 2000000。</span><span class="sxs-lookup"><span data-stu-id="e550b-111">To ensure that the BizTalk throttling mechanism did not throttle the receive host, which would prevent the accumulation of a spool table backlog, the **Message count in DB** throttling threshold for the receive host was changed from the default value of 50000 to 2000000.</span></span> <span data-ttu-id="e550b-112">如需變更資訊**訊息 DB 中的計數**節流處理臨界值，請參閱[如何修改資源基礎節流設定](../core/how-to-modify-resource-based-throttling-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e550b-112">For information on changing the **Message count in DB** throttling threshold, see [How to Modify Resource Based Throttling Settings](../core/how-to-modify-resource-based-throttling-settings.md).</span></span> <span data-ttu-id="e550b-113">如需預設主控件節流設定資訊，請參閱[使用設定儀表板進行 BizTalk Server 效能微調](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="e550b-113">For information about the default host throttling settings, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span></span>  
  
 <span data-ttu-id="e550b-114">下圖顯示的指示器與上圖相同。</span><span class="sxs-lookup"><span data-stu-id="e550b-114">The following graph shows the same indicators as in the graph above.</span></span>  
  
 <span data-ttu-id="e550b-115">**加速負載測試的負載設定檔**</span><span class="sxs-lookup"><span data-stu-id="e550b-115">**Load profile of overdrive load test**</span></span>  
  
 <span data-ttu-id="e550b-116">![加速負載的效能監控顯示](../core/media/bts06-overdrive-load.gif "BTS06_Overdrive_Load")</span><span class="sxs-lookup"><span data-stu-id="e550b-116">![Performance montor display of overdrive load](../core/media/bts06-overdrive-load.gif "BTS06_Overdrive_Load")</span></span>  
  
 <span data-ttu-id="e550b-117">如圖所示，多工緩衝處理深度會立即開始累積，尖峰期大約在 2 百萬筆記錄。</span><span class="sxs-lookup"><span data-stu-id="e550b-117">As can be seen from the graph, the spool depth started building up immediately, peaking at just above 2 million records.</span></span> <span data-ttu-id="e550b-118">以這種速率，大約需要 2.5 個小時才能達到目標的 2 百萬筆記錄積存。</span><span class="sxs-lookup"><span data-stu-id="e550b-118">At this rate, it took just about 2.5 hours to get to the targeted 2 million record backlog.</span></span> <span data-ttu-id="e550b-119">負載停止後，清除工作大約需要 8 小時從積存復原。</span><span class="sxs-lookup"><span data-stu-id="e550b-119">After the load was stopped, it took around 8 hours for the cleanup jobs to recover from the backlog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e550b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e550b-120">See Also</span></span>  
 <span data-ttu-id="e550b-121">[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span><span class="sxs-lookup"><span data-stu-id="e550b-121">[Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span></span>  
 <span data-ttu-id="e550b-122">[使用設定儀表板，以便讓 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) </span><span class="sxs-lookup"><span data-stu-id="e550b-122">[Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) </span></span>  
 [<span data-ttu-id="e550b-123">持續性負載測試</span><span class="sxs-lookup"><span data-stu-id="e550b-123">Sustainable Load Test</span></span>](../core/sustainable-load-test.md)