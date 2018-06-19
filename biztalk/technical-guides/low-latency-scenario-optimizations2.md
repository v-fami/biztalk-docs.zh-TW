---
title: 低延遲案例 Optimizations2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19cd78ce-ad7d-4e4b-8188-a63d707905d5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 009b1298e90b586830f062c8e884b88995f9e33f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297990"
---
# <a name="low-latency-scenario-optimizations"></a><span data-ttu-id="5596d-102">低延遲案例最佳化</span><span class="sxs-lookup"><span data-stu-id="5596d-102">Low-Latency Scenario Optimizations</span></span>
<span data-ttu-id="5596d-103">根據預設，BizTalk Server 已最佳化輸送量，而不是低度延遲。</span><span class="sxs-lookup"><span data-stu-id="5596d-103">By default, BizTalk Server is optimized for throughput rather than low-latency.</span></span> <span data-ttu-id="5596d-104">下列最佳化可以套用至 BizTalk Server 中，在案例中需要減少的延遲的地方。</span><span class="sxs-lookup"><span data-stu-id="5596d-104">The following optimizations can be applied to BizTalk Server in scenarios where reduced latency is required.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5596d-105">這些最佳化將會改善延遲，但可能在某些整體輸送量成本。</span><span class="sxs-lookup"><span data-stu-id="5596d-105">These optimizations will improve latency, but may do so at some cost to overall throughput.</span></span>  
  
## <a name="increase-the-biztalk-server-host-internal-message-queue-size"></a><span data-ttu-id="5596d-106">增加 BizTalk Server 主控件的內部訊息佇列大小</span><span class="sxs-lookup"><span data-stu-id="5596d-106">Increase the BizTalk Server host internal message queue size</span></span>  
 <span data-ttu-id="5596d-107">每個 BizTalk 主控件都有它自己內部記憶體中佇列。</span><span class="sxs-lookup"><span data-stu-id="5596d-107">Each BizTalk host has its own internal in-memory queue.</span></span> <span data-ttu-id="5596d-108">增加此佇列，從 100 到 10000 來改善低延遲案例的效能的預設值的大小。</span><span class="sxs-lookup"><span data-stu-id="5596d-108">Increase the size of this queue from the default value of 100 to 10000 to improve performance for a low-latency scenario.</span></span> <span data-ttu-id="5596d-109">如需修改內部訊息佇列大小值的詳細資訊，請參閱[如何修改資源基礎節流設定](http://go.microsoft.com/fwlink/?LinkID=208366)(http://go.microsoft.com/fwlink/?LinkID=208366) 中的 BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="5596d-109">For more information about modifying the value of the internal message queue size, see [How to Modify Resource Based Throttling Settings](http://go.microsoft.com/fwlink/?LinkID=208366) (http://go.microsoft.com/fwlink/?LinkID=208366) in the BizTalk Server documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5596d-110">增加內部訊息佇列大小值會增加主控件執行個體所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5596d-110">Increasing the internal message queue size value will increase the memory used by the host instance.</span></span>  
  
## <a name="increase-the-biztalk-server-host-in-process-messages"></a><span data-ttu-id="5596d-111">增加 BizTalk Server 主控件的內含式訊息</span><span class="sxs-lookup"><span data-stu-id="5596d-111">Increase the BizTalk Server host in-process messages</span></span>  
 <span data-ttu-id="5596d-112">增加 1000年到 10000 的預設值的內含式訊息來改善效能。</span><span class="sxs-lookup"><span data-stu-id="5596d-112">Increase the in-process messages from the default value of 1000 to 10,000 to improve performance.</span></span> <span data-ttu-id="5596d-113">如需修改內含式訊息的值的詳細資訊，請參閱[如何修改預設主控件節流設定](http://go.microsoft.com/fwlink/?LinkID=208366)(http://go.microsoft.com/fwlink/?LinkID=208366) 中的 BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="5596d-113">For more information about modifying the value of the in-process messages, see [How to Modify the Default Host Throttling Settings](http://go.microsoft.com/fwlink/?LinkID=208366) (http://go.microsoft.com/fwlink/?LinkID=208366) in the BizTalk Server documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5596d-114">增加內部訊息佇列大小值會增加主控件執行個體所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5596d-114">Increasing the internal message queue size value will increase the memory used by the host instance.</span></span>  
  
## <a name="optimize-orchestrations-for-low-latency"></a><span data-ttu-id="5596d-115">最佳化低延遲的協調的流程</span><span class="sxs-lookup"><span data-stu-id="5596d-115">Optimize orchestrations for low latency</span></span>  
 <span data-ttu-id="5596d-116">請遵循 < 最佳化的低延遲案例的協調流程的建議 > 一節中的建議[最佳化協調流程效能](../technical-guides/optimizing-orchestration-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="5596d-116">Follow the recommendations in the “Recommendations for optimizing orchestrations for low latency scenarios” section of [Optimizing Orchestration Performance](../technical-guides/optimizing-orchestration-performance.md).</span></span>  
  
## <a name="configure-polling-intervals"></a><span data-ttu-id="5596d-117">設定輪詢間隔</span><span class="sxs-lookup"><span data-stu-id="5596d-117">Configure polling intervals</span></span>  
 <span data-ttu-id="5596d-118">使用設定儀表板地在整個 BizTalk 群組中設定某個主控件的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="5596d-118">Use the Settings Dashboard to configure the polling intervals of a given host, across the BizTalk Group.</span></span> <span data-ttu-id="5596d-119">若要變更輪詢間隔：</span><span class="sxs-lookup"><span data-stu-id="5596d-119">To change Polling Intervals:</span></span>  
  
1.  <span data-ttu-id="5596d-120">在**BizTalk Server 管理主控台**，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**.</span><span class="sxs-lookup"><span data-stu-id="5596d-120">In the **BizTalk Server Administration Console**, expand **BizTalk Server Administration**, right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
2.  <span data-ttu-id="5596d-121">在**BizTalk 設定儀表板**對話方塊**主機**頁面上**一般**索引標籤，下方**輪詢間隔**，您會發現**傳訊**和**協調流程**值。</span><span class="sxs-lookup"><span data-stu-id="5596d-121">In the **BizTalk Settings Dashboard** dialog box, on the **Hosts** page, on the **General** tab, under **Polling Intervals**, you will find the **Messaging** and **Orchestration** values.</span></span> <span data-ttu-id="5596d-122">根據預設，這兩個值會設定為 500 毫秒。</span><span class="sxs-lookup"><span data-stu-id="5596d-122">By default, both these values are set to 500 milliseconds.</span></span>  
  
 <span data-ttu-id="5596d-123">下表列出我們用於測試 BizTalk 內含式 64 位元主控件 （RxHost、 TxHost 和 PxHost） 上的輪詢值。</span><span class="sxs-lookup"><span data-stu-id="5596d-123">The following table lists the polling values that we used for testing on the BizTalk in-process 64-bit Hosts (RxHost, TxHost and PxHost).</span></span> <span data-ttu-id="5596d-124">若要停用輪詢，您可以設定的輪詢間隔非常大的數字，做為資料表中列出。</span><span class="sxs-lookup"><span data-stu-id="5596d-124">To disable polling, you can set the polling interval to a very big number as listed in the table.</span></span>  
  
|<span data-ttu-id="5596d-125">伺服器主機</span><span class="sxs-lookup"><span data-stu-id="5596d-125">Server Hosts</span></span>|<span data-ttu-id="5596d-126">Messaging (傳訊)</span><span class="sxs-lookup"><span data-stu-id="5596d-126">Messaging</span></span>|<span data-ttu-id="5596d-127">協調流程</span><span class="sxs-lookup"><span data-stu-id="5596d-127">Orchestration</span></span>|  
|------------------|---------------|-------------------|  
|<span data-ttu-id="5596d-128">**RxHost**</span><span class="sxs-lookup"><span data-stu-id="5596d-128">**RxHost**</span></span><br /><br /> <span data-ttu-id="5596d-129">因為我們只會發佈內送訊息，BizTalk 訊息方塊，透過單向接收位置、 RxHost 不需要輪詢 （接收主控件）。</span><span class="sxs-lookup"><span data-stu-id="5596d-129">Because we are only publishing incoming messages to the BizTalk message box through a one-way receive location, polling is not required on the RxHost (receive host).</span></span>|<span data-ttu-id="5596d-130">200000</span><span class="sxs-lookup"><span data-stu-id="5596d-130">200000</span></span>|<span data-ttu-id="5596d-131">200000</span><span class="sxs-lookup"><span data-stu-id="5596d-131">200000</span></span>|  
|<span data-ttu-id="5596d-132">**TxHost**</span><span class="sxs-lookup"><span data-stu-id="5596d-132">**TxHost**</span></span><br /><br /> <span data-ttu-id="5596d-133">因為我們只會從 BizTalk messagebox 收到傳訊執行個體，並沒有協調流程輪詢要求 TxHost （傳送主控件）。</span><span class="sxs-lookup"><span data-stu-id="5596d-133">Because we are only receiving messaging instances from the BizTalk message box, orchestration polling is not required on the TxHost (send host).</span></span>|<span data-ttu-id="5596d-134">50</span><span class="sxs-lookup"><span data-stu-id="5596d-134">50</span></span>|<span data-ttu-id="5596d-135">200000</span><span class="sxs-lookup"><span data-stu-id="5596d-135">200000</span></span>|  
|<span data-ttu-id="5596d-136">**PxHost**</span><span class="sxs-lookup"><span data-stu-id="5596d-136">**PxHost**</span></span><br /><br /> <span data-ttu-id="5596d-137">因為我們只會從 BizTalk messagebox 接收協調流程執行個體，傳訊輪詢上並不需要 PxHost （處理主控件）。</span><span class="sxs-lookup"><span data-stu-id="5596d-137">Because we are only receiving orchestration instances from the BizTalk message box, messaging polling is not required on the PxHost (Processing host).</span></span>|<span data-ttu-id="5596d-138">200000</span><span class="sxs-lookup"><span data-stu-id="5596d-138">200000</span></span>|<span data-ttu-id="5596d-139">50</span><span class="sxs-lookup"><span data-stu-id="5596d-139">50</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5596d-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5596d-140">See Also</span></span>  
 [<span data-ttu-id="5596d-141">BizTalk Server 效能最佳化</span><span class="sxs-lookup"><span data-stu-id="5596d-141">Optimizing BizTalk Server Performance</span></span>](../technical-guides/optimizing-biztalk-server-performance.md)