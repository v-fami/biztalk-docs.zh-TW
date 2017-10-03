---
title: "叢集接收主控件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93544f39-836f-4a4f-9587-230bfa3a9d4e
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 876cdb5f3740e5f06d00a536e1459c64ac886d89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="clustering-receiving-hosts"></a><span data-ttu-id="0f32e-102">叢集接收主控件</span><span class="sxs-lookup"><span data-stu-id="0f32e-102">Clustering Receiving Hosts</span></span>
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="0f32e-103">提供功能，可讓您將 BizTalk 主控件設定為叢集資源內[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集群組。</span><span class="sxs-lookup"><span data-stu-id="0f32e-103"> provides functionality that allows you to configure a BizTalk Host as a clustered resource within a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster group.</span></span> <span data-ttu-id="0f32e-104">主控件叢集支援可為以支援高可用性的整合式 BizTalk 接收配接器應該不會在多個主控件執行個體中同時執行，例如 FTP 接收處理常式，或在某些情況下，POP3 接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="0f32e-104">Host cluster support is provided to support high availability for integrated BizTalk receive adapters that should not be run in multiple host instances simultaneously, such as the FTP receive handler or, under certain circumstances, the POP3 receive handler.</span></span> <span data-ttu-id="0f32e-105">在需要叢集 MSMQ 服務的實例中，主控件叢集支援也可確保 MSMQ 配接器所傳送或所接收訊息的交易一致性。</span><span class="sxs-lookup"><span data-stu-id="0f32e-105">Host cluster support is also provided to ensure transactional consistency for messages sent or received by the MSMQ adapter in scenarios that require that the MSMQ service is clustered.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f32e-106">主機叢集是只能搭配[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Enterprise Edition。</span><span class="sxs-lookup"><span data-stu-id="0f32e-106">Host clustering is available only with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Enterprise Edition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f32e-107">您可以叢集化 BizTalk 主控件之前，您必須設定至少兩個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk 群組中的電腦做為成員的[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集。</span><span class="sxs-lookup"><span data-stu-id="0f32e-107">Before you can cluster a BizTalk Host you must have configured at least two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in a BizTalk group as members of a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster.</span></span> <span data-ttu-id="0f32e-108">如需有關設定[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集，請參閱[Windows Server 2008 叢集文件、 白皮書、 網路廣播、 群組](http://go.microsoft.com/fwlink/?LinkId=156818)(http://go.microsoft.com/fwlink/?LinkId=156818)。</span><span class="sxs-lookup"><span data-stu-id="0f32e-108">For more information about configuring a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] cluster, see [Windows Server 2008 Clustering Documents, Whitepapers, Webcasts, Groups](http://go.microsoft.com/fwlink/?LinkId=156818) (http://go.microsoft.com/fwlink/?LinkId=156818).</span></span>  
  
 <span data-ttu-id="0f32e-109">BizTalk 主控件叢集支援可為五個整合式 BizTalk 配接器提供高可用性： FTP 配接器、 MSMQ 配接器、 POP3 配接器、 SQL 配接器和 SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="0f32e-109">BizTalk Host cluster support is available to provide high availability for five of the integrated BizTalk adapters: the FTP adapter, the MSMQ adapter, the POP3 adapter, the SQL adapter, and the SAP adapter.</span></span> <span data-ttu-id="0f32e-110">在執行配接器的單一執行個體時也提供主控件叢集支援，以提供高可用性，進行排序的傳遞。</span><span class="sxs-lookup"><span data-stu-id="0f32e-110">Host cluster support is also provided so that there is high availability for running a single instance of an adapter for purposes of ordered delivery.</span></span>  
  
 <span data-ttu-id="0f32e-111">所有的 BizTalk 配接器處理常式可以執行在叢集主控件，但沒有任何好處，如下所述但在叢集主控件執行配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="0f32e-111">All of the BizTalk adapter handlers can be run in a clustered host, but there is no benefit from running adapter handlers in a clustered host except as described below.</span></span> <span data-ttu-id="0f32e-112">如果您的處理需求包含任何下一節中所述的案例，您應該在叢集主控件執行配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="0f32e-112">If your processing requirements include any of the scenarios described in the section below, then you should run adapter handlers in a clustered host.</span></span> <span data-ttu-id="0f32e-113">如需詳細步驟，設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]叢集，請參閱[改善在 BizTalk Server 中使用 Windows Server 2008 容錯移轉叢集或 Windows Server 2003 伺服器叢集的容錯功能](http://go.microsoft.com/fwlink/?LinkId=156819)(http://go.microsoft.com/fwlink/?LinkId=156819)。</span><span class="sxs-lookup"><span data-stu-id="0f32e-113">For detailed steps of setting up [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] clusters, see [Improving Fault Tolerance in BizTalk Server by Using a Windows Server 2008 Failover Cluster or Windows Server 2003 Server Cluster](http://go.microsoft.com/fwlink/?LinkId=156819) (http://go.microsoft.com/fwlink/?LinkId=156819).</span></span>  
  
## <a name="scenarios-for-running-adapter-handlers-in-clustered-hosts"></a><span data-ttu-id="0f32e-114">在叢集主機中執行配接器處理常式的案例</span><span class="sxs-lookup"><span data-stu-id="0f32e-114">Scenarios for Running Adapter Handlers in Clustered Hosts</span></span>  
 <span data-ttu-id="0f32e-115">如果您的處理需求包含任何下列案例，您應該在叢集主控件執行配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="0f32e-115">If your processing requirements include any of the scenarios listed below, then you should run adapter handlers in a clustered host.</span></span>  
  
-   <span data-ttu-id="0f32e-116">在叢集 BizTalk 主控件中執行 FTP 配接器接收處理常式</span><span class="sxs-lookup"><span data-stu-id="0f32e-116">Running the FTP adapter receive handler within a clustered BizTalk host</span></span>  
  
-   <span data-ttu-id="0f32e-117">在叢集 BizTalk 主控件中執行 MSMQ 配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="0f32e-117">Running MSMQ adapter handlers within a clustered BizTalk host</span></span>  
  
-   <span data-ttu-id="0f32e-118">在叢集 BizTalk 主控件中執行 POP3 配接器接收處理常式</span><span class="sxs-lookup"><span data-stu-id="0f32e-118">Running the POP3 adapter receive handler within a clustered BizTalk host</span></span>  
  
-   <span data-ttu-id="0f32e-119">執行支援以叢集 BizTalk 主控件執行排序傳遞的接收配接器</span><span class="sxs-lookup"><span data-stu-id="0f32e-119">Running a receive adapter that supports ordered delivery with a clustered BizTalk host</span></span>  
  
 <span data-ttu-id="0f32e-120">如需有關這些案例的詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](http://go.microsoft.com/fwlink/?LinkId=151284)(http://go.microsoft.com/fwlink/?LinkId=151284)。</span><span class="sxs-lookup"><span data-stu-id="0f32e-120">For more information about these scenarios, see [Considerations for Running Adapter Handlers within a Clustered Host](http://go.microsoft.com/fwlink/?LinkId=151284) (http://go.microsoft.com/fwlink/?LinkId=151284).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f32e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f32e-121">See Also</span></span>  
 <span data-ttu-id="0f32e-122">[向外擴充接收主控件](../technical-guides/scaling-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="0f32e-122">[Scaling Out Receiving Hosts](../technical-guides/scaling-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="0f32e-123">[向外延展處理主控件](../technical-guides/scaling-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="0f32e-123">[Scaling Out Processing Hosts](../technical-guides/scaling-out-processing-hosts.md) </span></span>  
 [<span data-ttu-id="0f32e-124">向外延展傳送主控件</span><span class="sxs-lookup"><span data-stu-id="0f32e-124">Scaling Out Sending Hosts</span></span>](../technical-guides/scaling-out-sending-hosts.md)