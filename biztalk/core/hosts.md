---
title: 主機 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- host instances, servers
- hosts, isolated
- host instances, relationships
- hosts, in-process hosts
- servers, hosts
- hosts, host instances
- hosts, relationships
- In-Process BizTalk Host groups
- hosts, about hosts
- hosts, untrusted
- host instances, hosts
- hosts, servers
- hosts
- servers, host instances
- Isolated Host Users group
- hosts, trusted
ms.assetid: d96537e0-e679-407a-8870-34a663acfed9
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 790c839685e71dd1a88b637e5ca7811d62809cc0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980015"
---
# <a name="hosts"></a><span data-ttu-id="04b7e-102">主控件</span><span class="sxs-lookup"><span data-stu-id="04b7e-102">Hosts</span></span>
<span data-ttu-id="04b7e-103">BizTalk 主控件物件代表零個或多個執行階段程序的一組邏輯，在此執行階段程序中您可以部署服務、管線與其他成品。</span><span class="sxs-lookup"><span data-stu-id="04b7e-103">The BizTalk Host object represents a logical set of zero or more runtime processes in which you can deploy services, pipelines, and other artifacts.</span></span> <span data-ttu-id="04b7e-104">主控件物件也代表執行階段執行個體的集合 (零個或多個)，是已部署的項目實際執行的位置。</span><span class="sxs-lookup"><span data-stu-id="04b7e-104">The Host object also represents a collection of runtime instances (zero or more) where the deployed items physically run.</span></span>  
  
 <span data-ttu-id="04b7e-105">在您建立主控件 (邏輯容器) 之後，可以將實體 BizTalk 伺服器 (主控件執行個體) 新增至主控件。</span><span class="sxs-lookup"><span data-stu-id="04b7e-105">After you create a host (a logical container), you can add physical BizTalk servers (host instances) to the host.</span></span> <span data-ttu-id="04b7e-106">您不能新增 BizTalk Server 至相同的主控件一次以上。</span><span class="sxs-lookup"><span data-stu-id="04b7e-106">You cannot add a BizTalk server to the same host more than once.</span></span> <span data-ttu-id="04b7e-107">您可以新增單一主控件執行個體至多個主控件。</span><span class="sxs-lookup"><span data-stu-id="04b7e-107">A single host instance can be added to multiple hosts.</span></span>  
  
 <span data-ttu-id="04b7e-108">包含在 BizTalk 主控件中的項目 (例如，配接器處理常式、接收位置 (包括管線) 以及協調流程) 可以執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="04b7e-108">Items—such as adapter handlers, receive locations (including pipelines), and orchestrations—contained in BizTalk hosts can perform the following functions:</span></span>  
  
- <span data-ttu-id="04b7e-109">**接收**。</span><span class="sxs-lookup"><span data-stu-id="04b7e-109">**Receiving**.</span></span> <span data-ttu-id="04b7e-110">在接收位置拾取訊息之後，這些項目會進行訊息的初始處理。</span><span class="sxs-lookup"><span data-stu-id="04b7e-110">These items do the initial processing of messages after they are picked up in a receive location.</span></span> <span data-ttu-id="04b7e-111">當主控件包含接收項目時 (例如接收位置或管線)，它將做為安全範圍，而訊息解碼和解密都發生在主控件的管線中。</span><span class="sxs-lookup"><span data-stu-id="04b7e-111">When a host contains a receiving item, such as a receive location or pipeline, it acts as a security boundary, and the message decoding and decrypting occurs in a pipeline within the host.</span></span>  
  
- <span data-ttu-id="04b7e-112">**傳送**。</span><span class="sxs-lookup"><span data-stu-id="04b7e-112">**Sending**.</span></span> <span data-ttu-id="04b7e-113">這些項目會在訊息傳送到傳送埠之前，進行訊息的最後處理。</span><span class="sxs-lookup"><span data-stu-id="04b7e-113">These items do the final processing of messages before they are sent out to the send port.</span></span> <span data-ttu-id="04b7e-114">當主控件包含傳送項目時 (例如，傳送埠或管線)，主控件將做為安全範圍，而訊息簽章和加密都發生在主控件的管線中。</span><span class="sxs-lookup"><span data-stu-id="04b7e-114">When a host contains a sending item, such as a send port or pipeline, the host acts as a security boundary, and the message signing and encryption occurs in a pipeline within the host.</span></span>  
  
- <span data-ttu-id="04b7e-115">**處理**。</span><span class="sxs-lookup"><span data-stu-id="04b7e-115">**Processing**.</span></span> <span data-ttu-id="04b7e-116">這些項目會處理以協調流程中指示為基礎的訊息。</span><span class="sxs-lookup"><span data-stu-id="04b7e-116">These items process messages based on the instructions in an orchestration.</span></span>  
  
  <span data-ttu-id="04b7e-117">一個 BizTalk 主控件可以包含接收、傳送和處理訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="04b7e-117">One BizTalk Host can contain items that receive, send, and process messages.</span></span> <span data-ttu-id="04b7e-118">建議您為每個功能建立不同的主控件，以建立安全範圍並協助管理。</span><span class="sxs-lookup"><span data-stu-id="04b7e-118">It is recommended that you create different hosts for each function to create security boundaries and facilitate management.</span></span> <span data-ttu-id="04b7e-119">尤其，建議您使用不同的主控件來進行處理、接收/傳送，並將信任和非信任的項目分開。</span><span class="sxs-lookup"><span data-stu-id="04b7e-119">In particular, it is recommended that you use different hosts for processing and for receive/send, and that you separate trusted and non-trusted items.</span></span>  
  
  <span data-ttu-id="04b7e-120">下圖顯示伺服器、主控件與主控件執行個體之間的關係。</span><span class="sxs-lookup"><span data-stu-id="04b7e-120">The following figure shows the relationship between servers, hosts, and host instances.</span></span>  
  
  <span data-ttu-id="04b7e-121">![主控件、 主控件執行個體和伺服器關係](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")</span><span class="sxs-lookup"><span data-stu-id="04b7e-121">![Hosts, host instances, and server relationships](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")</span></span>  
  <span data-ttu-id="04b7e-122">主控件、主控件執行個體與伺服器之間的關係</span><span class="sxs-lookup"><span data-stu-id="04b7e-122">Relationship between hosts, host instances, and servers</span></span>  
  
  <span data-ttu-id="04b7e-123">如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="04b7e-123">For more information about Host Instances, see [Host Instances](../core/host-instances.md).</span></span>  
  
  <span data-ttu-id="04b7e-124">根據裝載的實體組態與配接器類型，共有兩種類型的主控件：內含式主控件與外掛式主控件。</span><span class="sxs-lookup"><span data-stu-id="04b7e-124">Based on the physical configuration and type of adapter hosted, there are two types of hosts: in-process hosts and isolated hosts.</span></span>  
  
## <a name="in-process-hosts"></a><span data-ttu-id="04b7e-125">內含式主控件</span><span class="sxs-lookup"><span data-stu-id="04b7e-125">In-process Hosts</span></span>  
 <span data-ttu-id="04b7e-126">內含式主控件代表系統管理員建立、 刪除和完全控制 Windows Management Instrumentation (WMI) 與 BizTalk 管理主控台中的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="04b7e-126">In-process hosts represent service instances that an administrator creates, deletes, and fully controls with Windows Management Instrumentation (WMI) and the BizTalk Administration Console.</span></span>  
  
 <span data-ttu-id="04b7e-127">內含式主控件具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="04b7e-127">In-process hosts have the following characteristics:</span></span>  
  
- <span data-ttu-id="04b7e-128">您可以將任何協調流程登錄到內含式主控件。</span><span class="sxs-lookup"><span data-stu-id="04b7e-128">You can enlist any orchestration into an in-process host.</span></span>  
  
- <span data-ttu-id="04b7e-129">內含式主控件可以裝載任何傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="04b7e-129">An in-process host can host any send handler.</span></span>  
  
- <span data-ttu-id="04b7e-130">內含式主控件可以裝載 SOAP 和 HTTP 以外的任何接收處理常式：</span><span class="sxs-lookup"><span data-stu-id="04b7e-130">An in-process host can host any of the receive handlers except for SOAP and HTTP:</span></span>  
  
  -   <span data-ttu-id="04b7e-131">FILE</span><span class="sxs-lookup"><span data-stu-id="04b7e-131">FILE</span></span>  
  
  -   <span data-ttu-id="04b7e-132">FTP</span><span class="sxs-lookup"><span data-stu-id="04b7e-132">FTP</span></span>  
  
  -   <span data-ttu-id="04b7e-133">MQSeries</span><span class="sxs-lookup"><span data-stu-id="04b7e-133">MQSeries</span></span>  
  
  -   <span data-ttu-id="04b7e-134">MSMQ</span><span class="sxs-lookup"><span data-stu-id="04b7e-134">MSMQ</span></span>  
  
  -   <span data-ttu-id="04b7e-135">POP3</span><span class="sxs-lookup"><span data-stu-id="04b7e-135">POP3</span></span>  
  
  -   <span data-ttu-id="04b7e-136">SQL</span><span class="sxs-lookup"><span data-stu-id="04b7e-136">SQL</span></span>  
  
  -   <span data-ttu-id="04b7e-137">Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="04b7e-137">Windows SharePoint Services</span></span>  
  
- <span data-ttu-id="04b7e-138">您在中建立第一個 「 內含式主控件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署**預設主控件**和就無法予以刪除。</span><span class="sxs-lookup"><span data-stu-id="04b7e-138">The first in-process host you create in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment is the **default host** and you cannot delete it.</span></span> <span data-ttu-id="04b7e-139">「BizTalk 訊息佇列」配接器為靜態處理常式組態使用預設主控件。</span><span class="sxs-lookup"><span data-stu-id="04b7e-139">The BizTalk Message Queuing adapter uses the default host for static handler configuration.</span></span> <span data-ttu-id="04b7e-140">加入配接器可以為預設主控件自動建立接收埠和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="04b7e-140">Adding an adapter automatically creates receive and send ports for the default host.</span></span>  
  
## <a name="isolated-hosts"></a><span data-ttu-id="04b7e-141">外掛式主控件</span><span class="sxs-lookup"><span data-stu-id="04b7e-141">Isolated Hosts</span></span>  
 <span data-ttu-id="04b7e-142">外掛式主控件代表解決方案開發人員可用程式設計方式來建立、刪除和控制的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="04b7e-142">Isolated hosts represent service instances that a solutions developer programmatically creates, deletes, and controls.</span></span> <span data-ttu-id="04b7e-143">系統管理員會使用 WMI 與 BizTalk 管理主控台來設定這些主控件 (例如，設定主控件服務帳戶與驗證信任)。</span><span class="sxs-lookup"><span data-stu-id="04b7e-143">An administrator uses WMI and the BizTalk Administration Console to configure these hosts (for example, to configure the host service account and authentication trust).</span></span>  
  
 <span data-ttu-id="04b7e-144">外掛式主控件主要裝載必須在一般 BizTalk Server 執行階段程序之外執行的配接器。</span><span class="sxs-lookup"><span data-stu-id="04b7e-144">Isolated hosts primarily host adapters that must run outside of the normal BizTalk Server runtime process.</span></span> <span data-ttu-id="04b7e-145">例如，您可以使用外掛式主控件為外部程序 (例如 ISAPI 延伸模組與 ASP.NET) 裝載配接器。</span><span class="sxs-lookup"><span data-stu-id="04b7e-145">For example, you use isolated hosts to host adapters for external processes such as ISAPI extensions and ASP.NET.</span></span>  
  
 <span data-ttu-id="04b7e-146">外掛式主控件具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="04b7e-146">Isolated hosts have the following characteristics:</span></span>  
  
-   <span data-ttu-id="04b7e-147">您不能將協調流程登錄到外掛式主控件。</span><span class="sxs-lookup"><span data-stu-id="04b7e-147">You cannot enlist orchestrations into an isolated host.</span></span>  
  
-   <span data-ttu-id="04b7e-148">外掛式主控件不能裝載傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="04b7e-148">An isolated host cannot host send handlers.</span></span>  
  
-   <span data-ttu-id="04b7e-149">外掛式主控件只能裝載與 HTTP/S 及 SOAP 配接器 (外掛式類型配接器) 關聯的接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="04b7e-149">An isolated host can host only the receive handlers associated with HTTP/S and SOAP adapters (the isolated-type adapters).</span></span>  
  
-   <span data-ttu-id="04b7e-150">外掛式主控件不能裝載追蹤。</span><span class="sxs-lookup"><span data-stu-id="04b7e-150">An isolated host cannot host tracking.</span></span>  
  
-   <span data-ttu-id="04b7e-151">外掛式主控件不能做為預設主控件。</span><span class="sxs-lookup"><span data-stu-id="04b7e-151">An isolated host cannot be the default host.</span></span>  
  
-   <span data-ttu-id="04b7e-152">外掛式主控件的狀態總是**狀態無法使用**。</span><span class="sxs-lookup"><span data-stu-id="04b7e-152">The status of an isolated host is always **Status Unavailable**.</span></span> <span data-ttu-id="04b7e-153">BizTalk Server 不會存取外部程序的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="04b7e-153">BizTalk Server does not access the status information for external processes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04b7e-154">只要主控件執行個體共用相同的安全性組態 (驗證信任)，它們就可以共用相同的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="04b7e-154">Host instances can share the same service account as long as they share the same security configuration (authentication trust).</span></span>  
  
## <a name="trusted-and-untrusted-hosts"></a><span data-ttu-id="04b7e-155">信任與非信任的主控件</span><span class="sxs-lookup"><span data-stu-id="04b7e-155">Trusted and Untrusted Hosts</span></span>  
 <span data-ttu-id="04b7e-156">BizTalk Server 可讓識別為驗證信任的主控件指出信任的主控件佇列至 MessageBox 資料庫的訊息傳送者為實體，而不是信任的主控件本身。</span><span class="sxs-lookup"><span data-stu-id="04b7e-156">BizTalk Server enables hosts identified as authentication trusted to indicate that the sender of a message that the trusted host is queuing to the MessageBox database is an entity other than the trusted host itself.</span></span> <span data-ttu-id="04b7e-157">驗證信任的主要目的是要讓管線解析為「產品識別碼」(PID)，並將該 PID 傳遞至取用的服務，以供授權和輸出合作對象解析使用，並讓傳送者的「Windows 安全性識別碼」(SSID) 傳輸到取用的服務，以供協調流程動作授權使用。</span><span class="sxs-lookup"><span data-stu-id="04b7e-157">The primary purposes of authentication trust are to enable pipelines to resolve to a Product ID (PID) and pass that PID along to consuming services for use in authorization and outbound party resolution, and to enable the transmission of the sender Windows Security ID (SSID) along to consuming services for use in orchestration action authorization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b7e-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04b7e-158">See Also</span></span>  
 <span data-ttu-id="04b7e-159">[主控件執行個體](../core/host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="04b7e-159">[Host Instances](../core/host-instances.md) </span></span>  
 [<span data-ttu-id="04b7e-160">管理 BizTalk 主控件和主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="04b7e-160">Managing BizTalk Hosts and Host Instances</span></span>](../core/managing-biztalk-hosts-and-host-instances.md)  
 [<span data-ttu-id="04b7e-161">實體</span><span class="sxs-lookup"><span data-stu-id="04b7e-161">Entities</span></span>](../core/entities.md)