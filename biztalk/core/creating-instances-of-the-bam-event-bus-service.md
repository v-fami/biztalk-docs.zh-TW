---
title: 建立 BAM 事件匯流排服務的執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 454bdde7-45a6-41ab-9196-f662273f0f2b
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: daf847afc8f5c1d284a8266d70006a0f43508ed9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983999"
---
# <a name="creating-instances-of-the-bam-event-bus-service"></a><span data-ttu-id="01a1f-102">建立 BAM 事件匯流排服務的執行個體</span><span class="sxs-lookup"><span data-stu-id="01a1f-102">Creating Instances of the BAM Event Bus Service</span></span>
<span data-ttu-id="01a1f-103">BAM 事件匯流排服務是在 BizTalk 應用程式主控件內執行。</span><span class="sxs-lookup"><span data-stu-id="01a1f-103">The BAM Event Bus Service runs inside a BizTalk application host.</span></span> <span data-ttu-id="01a1f-104">您可以使用預設主控件來裝載 BAM 事件匯流排服務，或自行建立新主控件。</span><span class="sxs-lookup"><span data-stu-id="01a1f-104">You can use the default host to host the BAM Event Bus Service, or you can create a new host.</span></span> <span data-ttu-id="01a1f-105">如果主控件裝載 BAM 事件匯流排服務，您爲該主控件所建立的任何新執行個體也都將裝載服務。</span><span class="sxs-lookup"><span data-stu-id="01a1f-105">If a host hosts the BAM Event Bus service, any new instances you create for that host also hosts the service.</span></span>  
  
 <span data-ttu-id="01a1f-106">如需預設主控件的資訊，請參閱[主機](../core/hosts.md)。</span><span class="sxs-lookup"><span data-stu-id="01a1f-106">For information about the default host, see [Hosts](../core/hosts.md).</span></span>  
  
 <span data-ttu-id="01a1f-107">如需建立主控件的資訊，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)。</span><span class="sxs-lookup"><span data-stu-id="01a1f-107">For information about creating hosts, see [How to Create a New Host](../core/how-to-create-a-new-host.md).</span></span>  
  
 <span data-ttu-id="01a1f-108">如需建立主控件執行個體的資訊，請參閱[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="01a1f-108">For information about creating host instances, see [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).</span></span>  
  
 <span data-ttu-id="01a1f-109">建立和設定主控件和主控件執行個體的相關資訊，請參閱[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="01a1f-109">For information about creating and configuring hosts and host instances, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).</span></span>  
  
### <a name="to-create-the-host-that-hosts-the-bam-event-bus-service"></a><span data-ttu-id="01a1f-110">若要建立裝載 BAM 事件匯流排服務的主控件</span><span class="sxs-lookup"><span data-stu-id="01a1f-110">To create the host that hosts the BAM Event Bus Service</span></span>  
  
1. <span data-ttu-id="01a1f-111">按一下 **開始**，指向**所有程式**，按一下  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-111">Click **Start**, point to **All Programs**, click **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="01a1f-112">在 BizTalk 管理主控台 視窗中，依序展開**BizTalk Server 管理**節點，展開**Biztalk 群組**節點，展開**平台設定**節點以滑鼠右鍵按一下**主機**節點中，選取**新增**，然後按一下**主機**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-112">In the BizTalk Administration Console window, expand the **BizTalk Server Administration** node, expand the **Biztalk Group** node and expand the **Platform Settings** node, right-click the **Hosts** node, select **New**, and then click **Host**.</span></span>  
  
3. <span data-ttu-id="01a1f-113">在 **主機內容**對話方塊中，於**名稱**方塊中，輸入主機的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="01a1f-113">In the **Host Properties** dialog box, in the **Name** box, type a descriptive name for the host.</span></span>  
  
4. <span data-ttu-id="01a1f-114">在 **一般**索引標籤上，選取**允許主控件追蹤**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="01a1f-114">On the **General** tab, select the **Allow Host Tracking** check box.</span></span>  
  
    <span data-ttu-id="01a1f-115">新的子節點會顯示在**主機**與新的主控件名稱的節點。</span><span class="sxs-lookup"><span data-stu-id="01a1f-115">A new child node appears under the **Hosts** node with the name of the new host.</span></span>  
  
5. <span data-ttu-id="01a1f-116">在  **Windows 群組**方塊中，輸入要指派此主控件，然後按一下 Windows 群組的名稱**確定**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-116">In the **Windows group** box, type the name of the Windows group to assign this host, and then click **OK**.</span></span>  
  
    <span data-ttu-id="01a1f-117">新的子節點會顯示在**主機**與新的主控件名稱的節點。</span><span class="sxs-lookup"><span data-stu-id="01a1f-117">A new child node appears under the **Hosts** node with the name of the new host.</span></span>  
  
### <a name="to-create-a-new-host-instance-of-the-host"></a><span data-ttu-id="01a1f-118">若要為主控件建立新的主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="01a1f-118">To create a new host instance of the host</span></span>  
  
1.  <span data-ttu-id="01a1f-119">以滑鼠右鍵按一下**主控件執行個體**節點中，選取**新增**，然後按一下**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-119">Right-click the **Host Instance** node, select **New**, and then click **Host Instance**.</span></span>  
  
2.  <span data-ttu-id="01a1f-120">選取伺服器主控件執行個體將會執行，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-120">Select a server where the host instance will run, and then click **OK**.</span></span>  
  
### <a name="to-add-hosting-tracking-to-the-host"></a><span data-ttu-id="01a1f-121">若要為主控件新增裝載追蹤</span><span class="sxs-lookup"><span data-stu-id="01a1f-121">To add hosting tracking to the host</span></span>  
  
1.  <span data-ttu-id="01a1f-122">以滑鼠右鍵按一下您想要重新設定，然後按一下 的主機**屬性**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-122">Right-click the host you want to reconfigure, and then click **Properties** .</span></span>  
  
2.  <span data-ttu-id="01a1f-123">在上**一般**索引標籤上，選取**允許主控件追蹤**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-123">On the **General** tab, select **Allow Host Tracking**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="01a1f-124">重新啟動該主控件的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="01a1f-124">Restart all instances of that host.</span></span>  
  
### <a name="to-remove-hosting-tracking-from-the-host"></a><span data-ttu-id="01a1f-125">若要從主控件移除裝載追蹤</span><span class="sxs-lookup"><span data-stu-id="01a1f-125">To remove hosting tracking from the host</span></span>  
  
1.  <span data-ttu-id="01a1f-126">以滑鼠右鍵按一下您要從中移除主控件追蹤，主應用的程式，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-126">Right-click the host from which you want to remove host tracking, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="01a1f-127">清除**允許主控件追蹤**核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="01a1f-127">Clear the **Allow Host tracking** check box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="01a1f-128">重新啟動該主控件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="01a1f-128">Restart instances of that host.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a1f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01a1f-129">See Also</span></span>  
 <span data-ttu-id="01a1f-130">[管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md) </span><span class="sxs-lookup"><span data-stu-id="01a1f-130">[Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md) </span></span>  
 <span data-ttu-id="01a1f-131">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="01a1f-131">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="01a1f-132">商務活動監控 (BAM)</span><span class="sxs-lookup"><span data-stu-id="01a1f-132">Business Activity Monitoring (BAM)</span></span>](../core/business-activity-monitoring-bam.md)