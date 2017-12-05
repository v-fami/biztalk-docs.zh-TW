---
title: "監控主控件執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7c6b80-7371-46ea-bf9c-82acb22012a3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b41dd0e01aa1e28862a3e99cfc767b3dd6ddec3c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="monitoring-host-instances"></a><span data-ttu-id="70fa8-102">監控主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="70fa8-102">Monitoring Host Instances</span></span>
<span data-ttu-id="70fa8-103">本主題描述使用 Microsoft System Center Operations Manager 監視 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="70fa8-103">This topic describes monitoring BizTalk host instances using Microsoft System Center Operations Manager.</span></span>  
  
## <a name="using-threshold-rules-to-monitor-health"></a><span data-ttu-id="70fa8-104">使用監視健全狀況的臨界值規則</span><span class="sxs-lookup"><span data-stu-id="70fa8-104">Using Threshold Rules to Monitor Health</span></span>  
 <span data-ttu-id="70fa8-105">BizTalk Server 管理組件加入了效能閾值規則，提供 BizTalk 主控件的健全狀況的完整檢視。</span><span class="sxs-lookup"><span data-stu-id="70fa8-105">The BizTalk Server Management Pack incorporates performance threshold rules that provide a comprehensive view of the health of the BizTalk hosts.</span></span> <span data-ttu-id="70fa8-106">提供的閾值規則有兩個類型：</span><span class="sxs-lookup"><span data-stu-id="70fa8-106">Two different types of threshold rules are provided:</span></span>  
  
-   <span data-ttu-id="70fa8-107">以一般方式 （例如，所有的 MessageBox 資料庫以及所有 BizTalk 主控件） 套用的規則。</span><span class="sxs-lookup"><span data-stu-id="70fa8-107">Rules that apply generically (for example, to all BizTalk hosts and to all MessageBox databases).</span></span>  
  
-   <span data-ttu-id="70fa8-108">專屬於特定的 BizTalk 主控件的規則。</span><span class="sxs-lookup"><span data-stu-id="70fa8-108">Rules that are specific to a particular BizTalk host.</span></span>  
  
 <span data-ttu-id="70fa8-109">一般規則會監控所有 BizTalk 主控件根據通用閾值。</span><span class="sxs-lookup"><span data-stu-id="70fa8-109">Generic rules monitor all the BizTalk hosts based on a common threshold.</span></span> <span data-ttu-id="70fa8-110">例如，規則監控 HostQ 大小監視根據通用閾值的所有 BizTalk 主控件工作佇列。</span><span class="sxs-lookup"><span data-stu-id="70fa8-110">For example, the rule Monitor HostQ Size monitors the work queues of all BizTalk hosts based on a common threshold.</span></span> <span data-ttu-id="70fa8-111">如果有三個不同的主控件，其所有的工作佇列監視由相同的規則，並且任何主控件工作佇列超越通用閾值時，會發生的警示。</span><span class="sxs-lookup"><span data-stu-id="70fa8-111">If there are three different hosts, all their work queues are monitored by the same rule, and alerts occur when any of the host work queues cross the common threshold.</span></span>  
  
 <span data-ttu-id="70fa8-112">BizTalk 主控件專用規則可讓您針對不同的主控件設定不同的臨界值。</span><span class="sxs-lookup"><span data-stu-id="70fa8-112">BizTalk host-specific rules enable you to configure different thresholds for different hosts.</span></span> <span data-ttu-id="70fa8-113">例如，規則監控 HostQ 大小 – BizTalkServerApplication 是監視工作佇列的 biztalkserverapplication 主控件的主控件專用規則。</span><span class="sxs-lookup"><span data-stu-id="70fa8-113">For example, the rule Monitor HostQ Size – BizTalkServerApplication is a host-specific rule that monitors the work queue of the BizTalkServerApplication host.</span></span> <span data-ttu-id="70fa8-114">在此範例中，您可以定義特定效能計數器執行個體的特定 Operations Manager 提供者，並在閾值規則中使用該提供者。</span><span class="sxs-lookup"><span data-stu-id="70fa8-114">In this example you can define a specific Operations Manager provider for the particular performance counter instance and use that provider in the threshold rule.</span></span> <span data-ttu-id="70fa8-115">因為這些規則是特定的主機，您必須定義特定規則加入每個新建立的主機。</span><span class="sxs-lookup"><span data-stu-id="70fa8-115">Because these rules are host-specific, you must define rules specific to each newly created host.</span></span>  
  
 <span data-ttu-id="70fa8-116">BizTalk 主控件專用規則提供為建立規則的範本規則是適用於您的環境。</span><span class="sxs-lookup"><span data-stu-id="70fa8-116">BizTalk host-specific rules are provided as template rules for creating rules that are applicable in your environment.</span></span> <span data-ttu-id="70fa8-117">依照預設，所有的閾值監控規則會停用：</span><span class="sxs-lookup"><span data-stu-id="70fa8-117">All threshold monitoring rules are disabled by default:</span></span>  
  
-   <span data-ttu-id="70fa8-118">您應該在您的環境特有的閾值設定一般規則。</span><span class="sxs-lookup"><span data-stu-id="70fa8-118">You should configure generic rules with threshold values specific to your environment.</span></span>  
  
-   <span data-ttu-id="70fa8-119">您應該建立 BizTalk 主控件專用規則根據範本規則和適當的臨界值。</span><span class="sxs-lookup"><span data-stu-id="70fa8-119">You should create BizTalk host-specific rules based on the template rules and appropriate thresholds.</span></span>  
  
## <a name="monitoring-biztalk-host-instances"></a><span data-ttu-id="70fa8-120">監控 BizTalk 主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="70fa8-120">Monitoring BizTalk Host Instances</span></span>  
 <span data-ttu-id="70fa8-121">以特定 BizTalk 主控件為目標的規則是從監視的觀點來看更有彈性。</span><span class="sxs-lookup"><span data-stu-id="70fa8-121">Rules that target specific BizTalk hosts are more flexible from a monitoring perspective.</span></span> <span data-ttu-id="70fa8-122">BizTalk Server 管理組件中提供的 biztalkserverapplication 主控件的閾值監控規則都是範本規則。</span><span class="sxs-lookup"><span data-stu-id="70fa8-122">All threshold monitoring rules for the BizTalkServerApplication host provided in the BizTalk Server Management pack are template rules.</span></span> <span data-ttu-id="70fa8-123">若要使用這些規則，您應該使用在 Operations Manager 系統管理員主控台：</span><span class="sxs-lookup"><span data-stu-id="70fa8-123">In order to use these rules, you should use the Operations Manager Administrator console to:</span></span>  
  
-   <span data-ttu-id="70fa8-124">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 規則群組中建立範本規則的複本，然後將它重新命名。</span><span class="sxs-lookup"><span data-stu-id="70fa8-124">Create a copy of the template rule in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] rule group and rename it.</span></span>  
  
-   <span data-ttu-id="70fa8-125">建立新的 Operations Manager 提供者的 BizTalk 主控件特定的效能計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="70fa8-125">Create a new Operations Manager provider for the BizTalk host-specific performance counter instance.</span></span>  
  
-   <span data-ttu-id="70fa8-126">修改規則所用的 Operations Manager 提供者，並指向新的專案。</span><span class="sxs-lookup"><span data-stu-id="70fa8-126">Modify the Operations Manager provider used by the rule and point it to the new one.</span></span>  
  
 <span data-ttu-id="70fa8-127">假設您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝 BizTalk 主控件 ReceiveHost，您想要監視為此主控件的主控件佇列大小。</span><span class="sxs-lookup"><span data-stu-id="70fa8-127">Suppose your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation has a BizTalk host ReceiveHost and you want to monitor the Host Queue size for this host.</span></span> <span data-ttu-id="70fa8-128">在此情況下，您應該建立 Operations Manager 提供者，根據 BizTalk 主控件佇列大小的效能計數器的 ReceiveHost 執行個體。</span><span class="sxs-lookup"><span data-stu-id="70fa8-128">In this case, you should create a Operations Manager provider based on the ReceiveHost instance of the performance counter for the queue size for the BizTalk host.</span></span> <span data-ttu-id="70fa8-129">您也應該針對您的環境適當調整規則中的閾值。</span><span class="sxs-lookup"><span data-stu-id="70fa8-129">You should also set the threshold value in the rule appropriately for your environment.</span></span>  
  
 <span data-ttu-id="70fa8-130">如果您使用特定主機的閾值監控規則，您應該停用一般監控規則。</span><span class="sxs-lookup"><span data-stu-id="70fa8-130">If you are using host-specific threshold monitoring rules, you should disable generic monitoring rules.</span></span> <span data-ttu-id="70fa8-131">這可以避免多餘的警示。</span><span class="sxs-lookup"><span data-stu-id="70fa8-131">This prevents redundant alerts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70fa8-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="70fa8-132">See Also</span></span>  
 [<span data-ttu-id="70fa8-133">使用 System Center Operations Manager 2007 監視 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="70fa8-133">Monitoring BizTalk Server with System Center Operations Manager 2007</span></span>](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)