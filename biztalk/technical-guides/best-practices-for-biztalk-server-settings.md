---
title: 如需 BizTalk Server 設定的最佳做法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e62024e1-f502-45a8-932f-edd8460bcf5f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 461e2e1a4256d79112e4eec94047c25df34a4511
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001114"
---
# <a name="best-practices-for-biztalk-server-settings"></a><span data-ttu-id="30c71-102">如需 BizTalk Server 設定的最佳作法</span><span class="sxs-lookup"><span data-stu-id="30c71-102">Best Practices for BizTalk Server Settings</span></span>
<span data-ttu-id="30c71-103">本主題列出當您執行作業整備的程序，您應該遵循的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="30c71-103">This topic lists best practices that you should follow as you perform operational readiness procedures for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="30c71-104">**設定訊息批次處理以增進配接器效能**</span><span class="sxs-lookup"><span data-stu-id="30c71-104">**Configure message batching to increase adapter performance**</span></span>  
  
- <span data-ttu-id="30c71-105">由配接器藉由結合成單一批次的多個作業執行的交易數目降至最低。</span><span class="sxs-lookup"><span data-stu-id="30c71-105">Minimize the number of transactions performed by an adapter by combining more than one operation into a single batch.</span></span>  
  
- <span data-ttu-id="30c71-106">限制的總位元組數的批次中除了訊息計數為基礎的批次大小。</span><span class="sxs-lookup"><span data-stu-id="30c71-106">Limit the batch size based on the total number of bytes in the batch, in addition to message count.</span></span> <span data-ttu-id="30c71-107">如需有關限制的批次大小的詳細資訊，請參閱 <<c0> [ 設定批次處理來改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="30c71-107">For more information about limiting the batch size, see [Configuring Batching to Improve Adapter Performance](../technical-guides/configuring-batching-to-improve-adapter-performance.md).</span></span>  
  
  <span data-ttu-id="30c71-108">**調整大型訊息閾值**</span><span class="sxs-lookup"><span data-stu-id="30c71-108">**Adjust the large message threshold**</span></span>  
  
- <span data-ttu-id="30c71-109">若要改善輸送量，增加 大型訊息閾值，這麼做可降低大型會進行緩衝處理的訊息數目在對應期間的磁碟。</span><span class="sxs-lookup"><span data-stu-id="30c71-109">To improve throughput, increase the large message threshold, which lowers the number of large messages that are buffered to disk during mapping.</span></span>  
  
  <span data-ttu-id="30c71-110">**判斷您要追蹤計劃期間所需的資訊**</span><span class="sxs-lookup"><span data-stu-id="30c71-110">**Determine the information you need to track during planning**</span></span>  
  
- <span data-ttu-id="30c71-111">您需要追蹤哪些資訊，您應該決定在規劃階段中。如此一來，您部署專案之後, 您可以設定追蹤選項和限制，讓您只將所需的資訊的追蹤資料數量。</span><span class="sxs-lookup"><span data-stu-id="30c71-111">You should decide during the planning stages which information you need to track. This way, after you deploy the project, you can set the tracking options and limit the amount of tracked data to give you only the information you need.</span></span>  
  
  > [!NOTE]  
  >  <span data-ttu-id="30c71-112">如需與追蹤相關的最佳作法的詳細資訊，請參閱[規劃追蹤](../technical-guides/planning-for-tracking.md)本指南中並[健全狀況與活動追蹤](http://go.microsoft.com/fwlink/p/?LinkId=154187)(http://go.microsoft.com/fwlink/p/?LinkId=154187)。</span><span class="sxs-lookup"><span data-stu-id="30c71-112">For more information about best practices related to tracking, see [Planning for Tracking](../technical-guides/planning-for-tracking.md) in this guide and [Health and Activity Tracking](http://go.microsoft.com/fwlink/p/?LinkId=154187) (http://go.microsoft.com/fwlink/p/?LinkId=154187).</span></span>  
  
  <span data-ttu-id="30c71-113">**不會追蹤所有訊息**</span><span class="sxs-lookup"><span data-stu-id="30c71-113">**Do not track all messages**</span></span>  
  
- <span data-ttu-id="30c71-114">我們建議您不追蹤所有訊息。</span><span class="sxs-lookup"><span data-stu-id="30c71-114">We recommend that you not track all messages.</span></span> <span data-ttu-id="30c71-115">這是因為每次觸及訊息時，BizTalk Server 將訊息的另一個複本。</span><span class="sxs-lookup"><span data-stu-id="30c71-115">This is because each time a message is touched, BizTalk Server makes another copy of the message.</span></span> <span data-ttu-id="30c71-116">您可以改為縮小範圍，藉由追蹤特定連接埠。</span><span class="sxs-lookup"><span data-stu-id="30c71-116">You can instead narrow the scope by tracking only a specific port.</span></span> <span data-ttu-id="30c71-117">這有助於您系統的效能最大化，並保持資料庫的整齊。</span><span class="sxs-lookup"><span data-stu-id="30c71-117">This helps to maximize the performance of your system and to keep the databases uncluttered.</span></span>  
  
  <span data-ttu-id="30c71-118">**設定追蹤傳送埠和接收埠而不是在管線**</span><span class="sxs-lookup"><span data-stu-id="30c71-118">**Set tracking on send ports and receive ports instead of on a pipeline**</span></span>  
  
- <span data-ttu-id="30c71-119">如果您設定在管線的追蹤選項時，您也會設定每個管線所使用的連接埠的全域追蹤選項。</span><span class="sxs-lookup"><span data-stu-id="30c71-119">If you set tracking options on pipelines, you will also set the tracking options globally for every port that uses the pipeline.</span></span> <span data-ttu-id="30c71-120">這接著可能會導致更多正在追蹤資料比您想，這將會變慢系統效能。</span><span class="sxs-lookup"><span data-stu-id="30c71-120">This in turn may result in far more data being tracked than you intend, which will slow system performance.</span></span> <span data-ttu-id="30c71-121">相反地，您可以設定追蹤選項，傳送連接埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="30c71-121">Instead, you can set tracking options on send ports and receive ports.</span></span>  
  
  <span data-ttu-id="30c71-122">**調整節流根據資源使用量**</span><span class="sxs-lookup"><span data-stu-id="30c71-122">**Adjust throttling based on resource utilization**</span></span>  
  
- <span data-ttu-id="30c71-123">中的節流[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供完善的保護系統的預設設定。</span><span class="sxs-lookup"><span data-stu-id="30c71-123">Throttling in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is configured by default to provide good protection for the system.</span></span> <span data-ttu-id="30c71-124">監視效能計數器來瞭解節流狀態，看看是否正在進行節流。</span><span class="sxs-lookup"><span data-stu-id="30c71-124">Monitor the performance counters for throttling states to see if throttling is taking place.</span></span> <span data-ttu-id="30c71-125">然後自行測量節流的資源為基礎 （例如，資料庫大小或記憶體使用量） 底下或透過使用。</span><span class="sxs-lookup"><span data-stu-id="30c71-125">Then gauge for yourself if the resource on which throttling is based (for example, database size or memory usage) is under or over utilized.</span></span> <span data-ttu-id="30c71-126">接下來，調整 節流閾值增加或減少時隨之。</span><span class="sxs-lookup"><span data-stu-id="30c71-126">Next, adjust the throttling thresholds up or down accordingly.</span></span> <span data-ttu-id="30c71-127">如需詳細資訊，請參閱 <<c0> [ 調整節流閾值： 何時和為何](http://go.microsoft.com/fwlink/p/?LinkId=154188)(<http://go.microsoft.com/fwlink/p/?LinkId=154188>)。</span><span class="sxs-lookup"><span data-stu-id="30c71-127">For more information, see [Adjusting Throttling Thresholds: When and Why](http://go.microsoft.com/fwlink/p/?LinkId=154188) (<http://go.microsoft.com/fwlink/p/?LinkId=154188>).</span></span>  
  
  <span data-ttu-id="30c71-128">**如果可能，請使用 PassThruTransmit 管線**</span><span class="sxs-lookup"><span data-stu-id="30c71-128">**Use the PassThruTransmit pipeline if possible**</span></span>  
  
- <span data-ttu-id="30c71-129">如果任何文件處理不需要傳送訊息至其目的地之前，請使用 PassThruTransmit 管線，而不是 XML 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="30c71-129">If no document processing is required before sending a message to its destination, use the PassThruTransmit pipeline instead of the XML send pipeline.</span></span>  
  
  <span data-ttu-id="30c71-130">**最小化協調流程 」 圖形開始與結束 」 的使用狀況追蹤事件**</span><span class="sxs-lookup"><span data-stu-id="30c71-130">**Minimize usage of orchestration “Shape start and end” tracking events**</span></span>  
  
- <span data-ttu-id="30c71-131">雖然追蹤的協調流程圖形會有明顯的好處，協調流程偵錯，它會具有效能和延展性的影響。</span><span class="sxs-lookup"><span data-stu-id="30c71-131">While orchestration shape tracking has obvious benefits for orchestration debugging, it has performance and scalability implications.</span></span> <span data-ttu-id="30c71-132">**流程化開始與結束**追蹤事件可能會造成相當大的負擔。</span><span class="sxs-lookup"><span data-stu-id="30c71-132">The **Shape start and end** tracking event can cause significant overhead.</span></span> <span data-ttu-id="30c71-133">最好的方式是其其中高輸送量是必要的生產環境中的使用量降到最低。</span><span class="sxs-lookup"><span data-stu-id="30c71-133">It is best to minimize its usage in production environments where high throughput is necessary.</span></span>  
  
  > [!NOTE]  
  >  <span data-ttu-id="30c71-134">**圖形開始和結束**上所有的協調流程的預設會啟用追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="30c71-134">**Shape start and end** tracking events are ENABLED by default on all orchestrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c71-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30c71-135">See Also</span></span>  
 [<span data-ttu-id="30c71-136">檢查清單：設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="30c71-136">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)