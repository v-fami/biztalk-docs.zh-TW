---
title: 低延遲案例 Optimizations1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd2a891a-ee4b-4542-b3ce-434e2a6474be
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed309a8ea9d6728dc4e0e653969f456e69f6eb34
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986055"
---
# <a name="low-latency-scenario-optimizations"></a><span data-ttu-id="b2cb9-102">低延遲案例最佳化</span><span class="sxs-lookup"><span data-stu-id="b2cb9-102">Low-Latency Scenario Optimizations</span></span>
<span data-ttu-id="b2cb9-103">根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]最佳化輸送量，而不是低延遲。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-103">By default, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is optimized for throughput rather than low-latency.</span></span> <span data-ttu-id="b2cb9-104">下列最佳化已套用至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用本指南中的測試案例。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-104">The following optimizations were applied to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for the test scenario used for this guide.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2cb9-105">這些最佳化會改善延遲，但貴用戶得於某些整體輸送量成本。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-105">These optimizations will improve latency but may do so at some cost to overall throughput.</span></span>  
  
## <a name="increase-the-biztalk-server-host-internal-message-queue-size"></a><span data-ttu-id="b2cb9-106">增加 BizTalk Server 主控件的內部訊息佇列大小</span><span class="sxs-lookup"><span data-stu-id="b2cb9-106">Increase the BizTalk Server host internal message queue size</span></span>  
 <span data-ttu-id="b2cb9-107">每個 BizTalk 主控件都有它自己內部的記憶體中佇列。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-107">Each BizTalk host has its own internal in-memory queue.</span></span> <span data-ttu-id="b2cb9-108">增加此佇列從 100 到 1000 之間以提升效能的低延遲案例的預設值的大小。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-108">Increase the size of this queue from the default value of 100 to 1000 to improve performance for a low-latency scenario.</span></span> <span data-ttu-id="b2cb9-109">如需有關如何修改的內部訊息佇列大小值的詳細資訊，請參閱 < 如何以修改預設主控件節流設定的"BizTalk Server 說明中在[ http://go.microsoft.com/fwlink/?LinkID=120225 ](http://go.microsoft.com/fwlink/?LinkID=120225)。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-109">For more information about modifying the value of the internal message queue size, see “How to Modify the Default Host Throttling Settings” in the BizTalk Server help at [http://go.microsoft.com/fwlink/?LinkID=120225](http://go.microsoft.com/fwlink/?LinkID=120225).</span></span>  
  
## <a name="reduce-the-maxreceiveinterval-value-in-the-admserviceclass-table-of-the-biztalk-server-management-database"></a><span data-ttu-id="b2cb9-110">減少 「 BizTalk Server 管理 」 資料庫的 adm_ServiceClass 資料表中的 MaxReceiveInterval 值</span><span class="sxs-lookup"><span data-stu-id="b2cb9-110">Reduce the MaxReceiveInterval value in the adm_ServiceClass table of the BizTalk Server management database</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b2cb9-111"> 使用輪詢機制，以從其在 Messagebox 中的主控件佇列接收訊息。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-111"> uses a polling mechanism to receive messages from its host queues in the Messagebox.</span></span> <span data-ttu-id="b2cb9-112">**MaxReceiveInterval** BizTalk 管理 (BizTalkMgmtDb) 資料庫的 adm_ServiceClass 資料表中的值是以毫秒為單位，每個 BizTalk 主控件執行個體將等候的最大值之前它會輪詢 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-112">The **MaxReceiveInterval** value in the adm_ServiceClass table of the BizTalk Management (BizTalkMgmtDb) database is the maximum value in milliseconds that each BizTalk host instance will wait until it polls the MessageBox.</span></span> <span data-ttu-id="b2cb9-113">Adm_ServiceClass 資料表包含下列服務類型的記錄：</span><span class="sxs-lookup"><span data-stu-id="b2cb9-113">The adm_ServiceClass table contains a record for the following service types:</span></span>  
  
- <span data-ttu-id="b2cb9-114">**XLANG/S** – BizTalk 協調流程主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="b2cb9-114">**XLANG/S** – for BizTalk orchestration host instances</span></span>  
  
- <span data-ttu-id="b2cb9-115">**Messaging InProcess** – 內含式主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="b2cb9-115">**Messaging InProcess** – for in-process host instances</span></span>  
  
- <span data-ttu-id="b2cb9-116">**MSMQT** – MSMQT 配接器主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="b2cb9-116">**MSMQT** – for MSMQT adapter host instances</span></span>  
  
- <span data-ttu-id="b2cb9-117">**Messaging Isolated** – 從處理序主控件執行個體，使用 HTTP、 SOAP 和特定 WCF 接收配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="b2cb9-117">**Messaging Isolated** – for out of process host instances, used by the HTTP, SOAP, and certain WCF receive adapter handlers</span></span>  
  
  <span data-ttu-id="b2cb9-118">根據預設，這個值會設定為 500 毫秒，這最適合輸送量，而不是低延遲。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-118">By default, this value is set to 500 milliseconds, which is optimized for throughput rather than low-latency.</span></span> <span data-ttu-id="b2cb9-119">在某些情況下，降低此值可以改善延遲。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-119">In certain scenarios, latency can be improved by reducing this value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2cb9-120">此值的變更會影響所有類型的執行個體相關聯的服務，因此，請務必先評估對所有的主控件執行個體的影響，再變更此值。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-120">Changes to this value impact all instances of the associated service type, therefore, take care to evaluate the impact on all host instances before changing this value.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="b2cb9-121">只有將 Messagebox 會有任何剩餘的未處理的訊息時，才會使用此值。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-121">This value is only used if the Messagebox has no remaining unprocessed messages.</span></span> <span data-ttu-id="b2cb9-122">如果沒有未處理的訊息在 Messagebox 中的常數待處理項目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會嘗試處理訊息，而不需等到輪詢延遲。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-122">If there is a constant backlog of unprocessed messages in the Messagebox, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will attempt to process the messages without waiting on the polling delay.</span></span> <span data-ttu-id="b2cb9-123">處理所有訊息之後，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]就會開始輪詢使用 MaxReceiveInterval 為指定的值。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-123">After all messages are processed, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will begin polling using the value specified for MaxReceiveInterval.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="b2cb9-124">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件執行個體到 Messagebox 資料庫執行個體，如 MaxReceiveInterval 可能造成裝載 Messagebox 資料庫執行個體的 SQL Server 電腦上的 CPU 使用率過高的值會減少的比率較高的環境。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-124">In a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment with a high ratio of host instances to Messagebox database instances, decreasing the value for MaxReceiveInterval may cause excessive CPU utilization on the SQL Server computer that houses the Messagebox database instance.</span></span> <span data-ttu-id="b2cb9-125">例如，如果 MaxReceiveInterval 會減少到較低的值 (\< 100) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中使用的單一 Messagebox 和 > 50 主控件執行個體，在 SQL Server 上的 CPU 使用率可能會高於 50%爬。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-125">For example, if the MaxReceiveInterval is decreased to a low value (\< 100) in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment with a single Messagebox and > 50 host instances, CPU utilization on the SQL Server may climb above 50%.</span></span> <span data-ttu-id="b2cb9-126">這種現象可能是因為持續輪詢的主控件佇列相關聯的額外負荷很重要。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-126">This phenomenon can occur because the overhead associated with continually polling host queues is significant.</span></span> <span data-ttu-id="b2cb9-127">如果您降低 MaxReceiveInterval 小於 100 的值時，您也應該評估這對您的 SQL Server 電腦的 CPU 使用率的影響。</span><span class="sxs-lookup"><span data-stu-id="b2cb9-127">If you reduce MaxReceiveInterval to a value less than 100, you should also evaluate the impact that this has on your SQL Server computer’s CPU utilization.</span></span>