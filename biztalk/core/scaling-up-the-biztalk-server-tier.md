---
title: 向上擴充 BizTalk Server 層 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, examples
- scaling, scaling up
ms.assetid: 9002006a-f301-4e15-94b9-6caffd7c527c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d55176072cd33e20dd1024bf2d9d1c39bca4567a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270134"
---
# <a name="scaling-up-the-biztalk-server-tier"></a><span data-ttu-id="1461a-102">向上擴充 BizTalk Server 層</span><span class="sxs-lookup"><span data-stu-id="1461a-102">Scaling Up the BizTalk Server Tier</span></span>
<span data-ttu-id="1461a-103">若要向上擴充 BizTalk 層，您需要升級 CPU、記憶體、IO 及其他資源。</span><span class="sxs-lookup"><span data-stu-id="1461a-103">To scale up the BizTalk tier, you upgrade the CPU, memory, IO and other resources.</span></span> <span data-ttu-id="1461a-104">下圖顯示如何將 BizTalk 層從擁有兩台處理器的電腦向上擴充到擁有四台處理器之電腦的範例。</span><span class="sxs-lookup"><span data-stu-id="1461a-104">The following figure shows an example of how you might scale up the BizTalk tier from a two processor computer to a four processor computer.</span></span>  
  
 <span data-ttu-id="1461a-105">![小數位數 &#45; 向上 BTS](../core/media/scaleupbts.gif "ScaleUpBTS")</span><span class="sxs-lookup"><span data-stu-id="1461a-105">![Scale&#45;up BTS](../core/media/scaleupbts.gif "ScaleUpBTS")</span></span>  
  
 <span data-ttu-id="1461a-106">向上擴充 BizTalk 階層的實例與選擇向外擴充的時機類似：</span><span class="sxs-lookup"><span data-stu-id="1461a-106">The scenarios for scaling up your BizTalk tier are similar to when you choose to scale out:</span></span>  
  
-   <span data-ttu-id="1461a-107">BizTalk Server 成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="1461a-107">BizTalk Server becomes a bottleneck.</span></span> <span data-ttu-id="1461a-108">瓶頸本身可能是由於以下其中一個問題所造成：</span><span class="sxs-lookup"><span data-stu-id="1461a-108">The bottleneck itself may be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="1461a-109">CPU：若實例使用大量 CPU 管線、對應或協調流程，BizTalk Server 將不會有額外的 CPU 空間。</span><span class="sxs-lookup"><span data-stu-id="1461a-109">CPU: If the scenario uses CPU intensive pipelines, maps, or orchestrations, the BizTalk servers will not have any extra CPU headroom.</span></span>  
  
-   <span data-ttu-id="1461a-110">記憶體和 I/O：若是現有電腦的記憶體與 IO 已達到最大限制，則需要升級電腦。</span><span class="sxs-lookup"><span data-stu-id="1461a-110">Memory and I/O: If the existing computers have reached their maximum limit on memory and IO, and the computer needs to be upgraded.</span></span>  
  
-   <span data-ttu-id="1461a-111">向外擴充過於昂貴。</span><span class="sxs-lookup"><span data-stu-id="1461a-111">Scaling out is too expensive.</span></span>  
  
-   <span data-ttu-id="1461a-112">若向外擴充並未解決瓶頸。</span><span class="sxs-lookup"><span data-stu-id="1461a-112">If scale-out does not address the bottleneck.</span></span> <span data-ttu-id="1461a-113">例如，向外擴充不會解決下列瓶頸：</span><span class="sxs-lookup"><span data-stu-id="1461a-113">For example, scaling out does not address the following bottlenecks:</span></span>  
  
    -   <span data-ttu-id="1461a-114">大型訊息轉換</span><span class="sxs-lookup"><span data-stu-id="1461a-114">Large Message Transforms</span></span>  
  
    -   <span data-ttu-id="1461a-115">每個交換都有大量訊息</span><span class="sxs-lookup"><span data-stu-id="1461a-115">Large number of messages per interchange</span></span>  
  
    -   <span data-ttu-id="1461a-116">有些 BTS 元件 (如管線或配接器) 會耗用大量記憶體</span><span class="sxs-lookup"><span data-stu-id="1461a-116">High memory utilization by some of BTS components, such as pipelines or adapters</span></span>  
  
    -   <span data-ttu-id="1461a-117">傳輸，如 EDI</span><span class="sxs-lookup"><span data-stu-id="1461a-117">A transport, such as EDI</span></span>  
  
## <a name="when-you-cant-scale-up-the-biztalk-tier"></a><span data-ttu-id="1461a-118">無法向上擴充 BizTalk 層時</span><span class="sxs-lookup"><span data-stu-id="1461a-118">When You Can’t Scale Up the BizTalk Tier</span></span>  
  
-   <span data-ttu-id="1461a-119">MessageBox 資料庫成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="1461a-119">The MessageBox database is the bottleneck.</span></span>  
  
-   <span data-ttu-id="1461a-120">配接器成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="1461a-120">An adapter becomes the bottleneck.</span></span> <span data-ttu-id="1461a-121">比方說，如果您使用配接器之後您增加 BizTalk 接收器的數目,，則可能會增加鎖定爭用其中 BizTalk 配接器從中提取資料的後端應用程式上。</span><span class="sxs-lookup"><span data-stu-id="1461a-121">For example, if you are using an adapter, after you increase the number of BizTalk receivers, lock contention might increase on the backend application where the BizTalk adapter is pulling data from.</span></span> <span data-ttu-id="1461a-122">這樣會限制您向上擴充配接器的能力。</span><span class="sxs-lookup"><span data-stu-id="1461a-122">This limits your ability to scale up the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1461a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1461a-123">See Also</span></span>  
 <span data-ttu-id="1461a-124">[向外擴充 BizTalk Server 層](../core/scaling-out-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="1461a-124">[Scaling Out the BizTalk Server Tier](../core/scaling-out-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="1461a-125">[向上擴充 SQL Server 層](../core/scaling-up-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="1461a-125">[Scaling Up the SQL Server Tier](../core/scaling-up-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="1461a-126">[向外擴充 SQL Server 層](../core/scaling-out-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="1461a-126">[Scaling Out the SQL Server Tier](../core/scaling-out-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="1461a-127">[向外擴充接收主控件](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="1461a-127">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="1461a-128">[向外延展處理主控件](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="1461a-128">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="1461a-129">[向外延展傳送主控件](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="1461a-129">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="1461a-130">[使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="1461a-130">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="1461a-131">[向外延展資料庫](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="1461a-131">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="1461a-132">叢集 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="1461a-132">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)