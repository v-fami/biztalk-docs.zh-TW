---
title: 執行叢集 Host1 內的配接器處理常式的考量 |Microsoft 文件
ms.custom: ''
ms.date: 2016-03-17
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high availability
- receive adapters, clustering
- clustering, POP3 adapters
- FTP adapters, clustering
- clustering, receive adapters
- NLB system
- MSMQ send handler
- MSMQ receive handler
- clustering, FTP adapters
- handlers [adapters], best practices
- hosts, clustering
- MSMQ adapters
- clustering, MSMQ adapters
- adapters, best practices
- adapters, handlers
- POP3 adapters, clustering
- MSMQ adapters, clustering
- clustering
ms.assetid: ee66663c-4f4d-4515-9df1-aacf4fc72be4
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1fc93db61cddae43023f5c25eec62ecebd46e69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238478"
---
# <a name="considerations-for-running-adapter-handlers-within-a-clustered-host"></a><span data-ttu-id="55685-102">在叢集主控件中執行配接器處理常式的考量</span><span class="sxs-lookup"><span data-stu-id="55685-102">Considerations for Running Adapter Handlers within a Clustered Host</span></span>
<span data-ttu-id="55685-103">BizTalk 主控件叢集支援可為下列整合 BizTalk 配接器提供高可用性： FTP 配接器、 SFTP 配接器、 MSMQ 配接器和 POP3 配接器。</span><span class="sxs-lookup"><span data-stu-id="55685-103">BizTalk host cluster support is available to provide high availability for the following integrated BizTalk adapters: the FTP adapter, the SFTP adapter, the MSMQ adapter, and the POP3 adapter.</span></span> <span data-ttu-id="55685-104">在執行配接器的單一執行個體時也提供主控件叢集支援，以提供高可用性，進行排序的傳遞。</span><span class="sxs-lookup"><span data-stu-id="55685-104">Host cluster support is also provided so that there is high availability for running a single instance of an adapter for purposes of ordered delivery.</span></span>  
  
 <span data-ttu-id="55685-105">所有的 BizTalk 配接器處理常式都可以在叢集主控件上執行，但是除了在下述情況之外，在叢集主控件上執行配接器處理常式並沒有任何益處。</span><span class="sxs-lookup"><span data-stu-id="55685-105">All of the BizTalk adapter handlers  can be run in a clustered host but there is no benefit derived for running adapter handlers in a clustered host except as described below.</span></span> <span data-ttu-id="55685-106">若您的處理需求不包括下列所述的任何實例，那麼您不應該在叢集主控件中執行配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="55685-106">If your processing requirements do not include any of the scenarios described below, then you should not run adapter handlers in a clustered host.</span></span>  
  
## <a name="running-the-ftp-or-sftp-adapter-receive-handler-within-a-clustered-biztalk-host"></a><span data-ttu-id="55685-107">執行的 FTP 或 SFTP 配接器接收處理常式，叢集 BizTalk 主控件中</span><span class="sxs-lookup"><span data-stu-id="55685-107">Running the FTP or SFTP adapter receive handler within a clustered BizTalk host</span></span>  
 <span data-ttu-id="55685-108">對於大部分的 BizTalk 整合配接器，只要建立多個配接器處理常式，以便在 BizTalk 群組中不同的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 伺服器的 BizTalk 主控件執行個體上執行，即可達到高可用性。</span><span class="sxs-lookup"><span data-stu-id="55685-108">For most of the BizTalk Server integrated adapters, high availability can be achieved by creating multiple adapter handlers to run on BizTalk host instances on different [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] servers within a BizTalk group.</span></span> <span data-ttu-id="55685-109">FTP 或 SFTP 配接器接收處理常式不應，不過，設定為同時執行多個 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="55685-109">FTP or SFTP adapter receive handlers should not, however, be configured to run in multiple BizTalk host instances simultaneously.</span></span> <span data-ttu-id="55685-110">此建議的理由，因為 FTP 或 SFTP 接收配接器使用 FTP 或 sftp 傳送通訊協定，從目標系統擷取檔案。</span><span class="sxs-lookup"><span data-stu-id="55685-110">This recommendation is made because the FTP or SFTP receive adapter uses the FTP or SFTP protocol to retrieve files from the target system.</span></span> <span data-ttu-id="55685-111">FTP 或 sftp 傳送的通訊協定不會鎖定檔案，以確保多份相同的檔案都不會同時的擷取時執行的 FTP 或 sftp 傳送的多個執行個體接收配接器。</span><span class="sxs-lookup"><span data-stu-id="55685-111">The FTP or SFTP protocol does not lock files to ensure that multiple copies of the same file are not retrieved simultaneously when running multiple instances of the FTP or SFTP receive adapter.</span></span>  
  
 <span data-ttu-id="55685-112">提供高可用性的 FTP 或 SFTP 接收配接器，您應該設定的 FTP 或 SFTP 接收配接器在已叢集 BizTalk 主控件執行個體中執行。</span><span class="sxs-lookup"><span data-stu-id="55685-112">To provide high availability for the FTP or SFTP receive adapter, you should configure the FTP or SFTP receive adapter to run in a BizTalk host instance that has been clustered.</span></span>  
  
## <a name="running-msmq-adapter-handlers-within-a-clustered-biztalk-host"></a><span data-ttu-id="55685-113">在叢集 BizTalk 主控件中執行 MSMQ 配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="55685-113">Running MSMQ adapter handlers within a clustered BizTalk host</span></span>  
 <span data-ttu-id="55685-114">若要確保能為 MSMQ 配接器提供高可用性，並確保能為 MSMQ 配接器所傳送或接收的訊息提供交易一致性，應執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="55685-114">To ensure high availability for the MSMQ adapter and to ensure transactional consistency for messages sent or received by the MSMQ adapter, you should do the following:</span></span>  
  
1.  <span data-ttu-id="55685-115">設定為叢集資源的 Windows 叢集群組中的訊息佇列 (MSMQ) 上您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="55685-115">Configure Message Queuing (MSMQ) as a clustered resource in a Windows cluster group on your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers.</span></span>  
  
2.  <span data-ttu-id="55685-116">為叢集 BizTalk 主控件將叢集 MSMQ 服務新增至資源依存性清單。</span><span class="sxs-lookup"><span data-stu-id="55685-116">Add the clustered MSMQ service to the list of Resource dependencies for the clustered BizTalk host.</span></span> <span data-ttu-id="55685-117">這可確保叢集的 BizTalk 主控件永遠在容錯移轉案例在叢集 MSMQ 服務之後啟動。</span><span class="sxs-lookup"><span data-stu-id="55685-117">This ensures that the clustered BizTalk host always starts after the clustered MSMQ service in failover scenarios.</span></span>  
  
3.  <span data-ttu-id="55685-118">在已設定為叢集資源，並和叢集 MSMQ 資源屬於同一個叢集群組的 BizTalk 主控件執行個體中設定 MSMQ 配接器傳送與接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="55685-118">Configure the MSMQ adapter send and receive handlers in a BizTalk host instance that has been configured as a cluster resource in the same cluster group as the clustered MSMQ resource.</span></span>  
  
 <span data-ttu-id="55685-119">建議這些步驟是基於下列理由：</span><span class="sxs-lookup"><span data-stu-id="55685-119">These steps are recommended for the following reasons:</span></span>  
  
 <span data-ttu-id="55685-120">**MSMQ 配接器接收處理常式**– MSMQ 4.0 (Windows Server 2008) 之前的 MSMQ 版本不支援遠端交易讀取，則為支援只有本機交易式讀取。</span><span class="sxs-lookup"><span data-stu-id="55685-120">**MSMQ adapter receive handler** – MSMQ versions prior to MSMQ 4.0 (Windows Server 2008) do not support remote transactional reads; only local transactional reads are supported.</span></span> <span data-ttu-id="55685-121">在此情況下，MSMQ 配接器接收處理常式必須完成與 MSMQ 配接器的本機交易式讀取叢集訊息佇列服務的本機主控件執行個體中執行。</span><span class="sxs-lookup"><span data-stu-id="55685-121">In this case, the MSMQ adapter receive handler must run in a host instance that is local to the clustered Message Queuing service to complete local transactional reads with the MSMQ adapter.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55685-122">MSMQ 配接器接收處理常式需要「訊息佇列」服務的本機非叢集執行個體在執行接收處理常式主控件執行個體的同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="55685-122">The MSMQ adapter receive handler requires that a local non-clustered instance of the Message Queuing service is running on the same computer that the receive handler host instance is running on.</span></span>  
  
 <span data-ttu-id="55685-123">**MSMQ 配接器傳送處理常式**-為了確保 MSMQ 配接器，MSMQ 配接器傳送處理常式所使用的外寄佇列所做的交易式傳送的一致性必須提供高可用性，以便可如果 MSMQ 服務，針對外寄佇列失敗繼續執行。</span><span class="sxs-lookup"><span data-stu-id="55685-123">**MSMQ adapter send handler** - To ensure the consistency of transactional sends made by the MSMQ adapter, the outgoing queue used by the MSMQ adapter send handler should be highly available so that if the MSMQ service for the outgoing queue fails it can be resumed.</span></span> <span data-ttu-id="55685-124">在 叢集群組中設定叢集的訊息 Queuingresource 和 MSMQ 配接器處理常式，可確保 MSMQ 配接器傳送處理常式所使用的外寄佇列仍有高可用性。</span><span class="sxs-lookup"><span data-stu-id="55685-124">Configuring a clustered Message Queuingresource and the MSMQ adapter handlers in a cluster group will ensure that the outgoing queue used by the MSMQ adapter send handler will be highly available.</span></span> <span data-ttu-id="55685-125">這將可在「訊息佇列」服務失敗時降低訊息遺失的可能性。</span><span class="sxs-lookup"><span data-stu-id="55685-125">This will mitigate the possibility of message loss in the event that the Message Queuing service fails.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55685-126">如果 MSMQ 接收位置是**只**接收來自遠端 MSMQ 伺服器上的 MSMQ 佇列，則可以透過執行 MSMQ 達成高可用性 BizTalk 群組中接收多個 BizTalk 電腦上的主機。</span><span class="sxs-lookup"><span data-stu-id="55685-126">If the MSMQ receive location is **only** receiving from MSMQ queues on a remote MSMQ server, then high availability can be achieved by running the MSMQ receive host on multiple BizTalk computers in the BizTalk group.</span></span>  <span data-ttu-id="55685-127">若要 MSMQ 提供高可用性，您必須確定遠端 MSMQ 伺服器正在使用容錯移轉叢集的 Windows。</span><span class="sxs-lookup"><span data-stu-id="55685-127">To provide high availability for MSMQ, you must ensure the remote MSMQ server is using failover clustering in Windows.</span></span>  <span data-ttu-id="55685-128">遠端 MSMQ 伺服器使用交易式佇列，如果必須執行 MSMQ 4.0 (Windows Server 2008) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="55685-128">If using transactional queues, the remote MSMQ server must be running MSMQ 4.0 (Windows Server 2008) or above.</span></span>  
  
## <a name="running-the-pop3-adapter-receive-handler-within-a-clustered-biztalk-host"></a><span data-ttu-id="55685-129">在叢集 BizTalk 主控件中執行 POP3 配接器接收處理常式</span><span class="sxs-lookup"><span data-stu-id="55685-129">Running the POP3 adapter receive handler within a clustered BizTalk host</span></span>  
 <span data-ttu-id="55685-130">POP3 配接器接收處理常式不需設定為在叢集 BizTalk 主控件中執行，除非配接器正在讀取的 POP3 伺服器允許多個並行連線同時連接到相同信箱。</span><span class="sxs-lookup"><span data-stu-id="55685-130">The POP3 adapter receive handler does not need to be configured to run in a clustered BizTalk host unless the POP3 server that the adapter is reading from allows multiple concurrent connections to be made to the same mailbox.</span></span> <span data-ttu-id="55685-131">如果 POP3 配接器所連接的 POP3 伺服器允許其郵件信箱有多個並行連線，則建議您將單一 POP3 配接器接收處理常式設定為在叢集的 BizTalk 主控件執行個體上執行，以確保 POP3 配接器的高可用性。</span><span class="sxs-lookup"><span data-stu-id="55685-131">If the POP3 server that the POP3 adapter is connected to permits multiple concurrent connections to its mailboxes, then we recommend that you ensure high availability for the POP3 adapter by configuring a single POP3 adapter receive handler to run in a BizTalk host instance that has been clustered.</span></span> <span data-ttu-id="55685-132">此建議的理由是，如此一來可以確保在執行 POP3 接收配接器的多個執行個體時，不會同時擷取相同電子郵件訊息的多個副本。</span><span class="sxs-lookup"><span data-stu-id="55685-132">This recommendation is made to ensure that multiple copies of the same e-mail message are not retrieved simultaneously when running multiple instances of the POP3 receive adapter.</span></span>  
  
## <a name="running-a-receive-adapter-that-supports-ordered-delivery-with-a-clustered-biztalk-host"></a><span data-ttu-id="55685-133">執行支援以叢集 BizTalk 主控件執行排序傳遞的接收配接器</span><span class="sxs-lookup"><span data-stu-id="55685-133">Running a receive adapter that supports ordered delivery with a clustered BizTalk host</span></span>  
 <span data-ttu-id="55685-134">MSMQ 與 MQSeries 整合配接器將能讓您依接收的順序將文件提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="55685-134">The MSMQ and MQSeries integrated adapters provide the ability to submit documents to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the order that they were received.</span></span> <span data-ttu-id="55685-135">只要讓這些接收配接器的單一執行個體能在任何指定的時間執行，即可正確地實作此功能。</span><span class="sxs-lookup"><span data-stu-id="55685-135">Correct implementation of this functionality requires that only a single instance of these receive adapters be running at any given time.</span></span> <span data-ttu-id="55685-136">若要為這些配接器的單一執行個體提供高可用性，應將它們設定為在叢集 BizTalk 主控件執行個體中執行。</span><span class="sxs-lookup"><span data-stu-id="55685-136">To provide high availability for a single instance of these adapters, they should be configured to run in a clustered BizTalk host instance.</span></span>