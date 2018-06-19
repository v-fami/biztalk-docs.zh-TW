---
title: 檢視 Operations Manager 主控台中的資訊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6acdf425-4c36-4d89-9493-81b33481fe6d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 687932839c379ed9589a51baae0ae8562f4af705
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302558"
---
# <a name="viewing-information-in-the-operations-manager-console"></a><span data-ttu-id="dda55-102">檢視 Operations Manager 主控台中的資訊</span><span class="sxs-lookup"><span data-stu-id="dda55-102">Viewing Information in the Operations Manager Console</span></span>
<span data-ttu-id="dda55-103">使用所提供的檢視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件以了解目前的可用性、 設定、 健全狀況，以及 BizTalk Server 環境的效能。</span><span class="sxs-lookup"><span data-stu-id="dda55-103">Use the views provided with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack to understand the current availability, configuration, health, and performance of your BizTalk Server environment.</span></span> <span data-ttu-id="dda55-104">檢視可能會包含冗長的物件清單。</span><span class="sxs-lookup"><span data-stu-id="dda55-104">A view can contain a lengthy list of objects.</span></span> <span data-ttu-id="dda55-105">若要尋找特定的物件或物件群組，可以使用 Operations Manager 工具列上的 [領域]、[搜尋] 和 [尋找] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dda55-105">To find a specific object or group of objects, you can use the Scope, Search, and Find buttons on the Operations Manager toolbar.</span></span> <span data-ttu-id="dda55-106">如需詳細資訊，請參閱 「 如何管理監視資料使用領域、 搜尋和尋找 Operations Manager 2007 R2\2012 說明中的主題。</span><span class="sxs-lookup"><span data-stu-id="dda55-106">For more information, see the How to Manage Monitoring Data Using Scope, Search, and Find topic in Operations Manager 2007 R2\2012 Help.</span></span>  
  
 <span data-ttu-id="dda55-107">下列檢視會直接列 **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**  Operations 主控台的 [監視] 窗格中的節點。</span><span class="sxs-lookup"><span data-stu-id="dda55-107">The following views are listed directly under **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]** node in the Monitoring pane of the Operations Console.</span></span>  
  
-   <span data-ttu-id="dda55-108">**應用程式檢視**: BizTalk 系統管理員是有興趣監視的狀態和健全狀況的各種 BizTalk Server 成品和應用程式，例如協調流程傳送埠、 接收位置，等等。</span><span class="sxs-lookup"><span data-stu-id="dda55-108">**Application Views**: A BizTalk administrator is interested in monitoring the state and health of various BizTalk Server artifacts and applications such as orchestrations send ports, receive locations, and so on.</span></span>  
  
-   <span data-ttu-id="dda55-109">**部署檢視**： 企業 IT 系統管理員想要監視的狀態和健全狀況的各種機器主控 SQL Server 資料庫，SSO 服務，主機執行個體上，IIS，在裝載電腦的企業部署網路服務等等。</span><span class="sxs-lookup"><span data-stu-id="dda55-109">**Deployment Views**: An enterprise IT administrator is interested in monitoring the state and health of the various enterprise deployments the machines hosting the SQL Server databases, machines hosting the SSO service, host instance machines, IIS, network services, and so on.</span></span>  
  
## <a name="application-views"></a><span data-ttu-id="dda55-110">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-110">Application Views</span></span>  
 <span data-ttu-id="dda55-111">應用程式檢視包含下表中所述的元素。</span><span class="sxs-lookup"><span data-stu-id="dda55-111">Application views contain the elements described in the following table.</span></span>  
  
### <a name="elements"></a><span data-ttu-id="dda55-112">元素</span><span class="sxs-lookup"><span data-stu-id="dda55-112">Elements</span></span>  
  
|<span data-ttu-id="dda55-113">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="dda55-113">View Name</span></span>|<span data-ttu-id="dda55-114">Description</span><span class="sxs-lookup"><span data-stu-id="dda55-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dda55-115">應用程式狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-115">Application State View</span></span>|<span data-ttu-id="dda55-116">這是顯示的 BizTalk 應用程式的健全狀況儀表板檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-116">This is a dashboard view that displays the health of a BizTalk application.</span></span> <span data-ttu-id="dda55-117">BizTalk 應用程式的健全狀況取決於其構成成品，例如協調流程、 傳送埠群組、 傳送埠、 接收埠和接收位置的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="dda55-117">The health of BizTalk application depends on the health of its constituent artifacts such as Orchestrations, Send Port Group, Send Port, Receive Port, and Receive Location.</span></span> <span data-ttu-id="dda55-118">[詳細資料檢視] 窗格會提供裝載 BizTalk 應用程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="dda55-118">The Details View pane provides the properties of the hosted BizTalk application.</span></span>|  
|<span data-ttu-id="dda55-119">群組狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-119">Group State View</span></span>|<span data-ttu-id="dda55-120">這是顯示的 BizTalk 群組的健全狀況儀表板檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-120">This is a dashboard view that displays the health of a BizTalk group.</span></span> <span data-ttu-id="dda55-121">BizTalk 群組的健全狀況取決於 BizTalk 主控件和 BizTalk 應用程式的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="dda55-121">The health of a BizTalk group depends on the health of BizTalk host and BizTalk applications.</span></span> <span data-ttu-id="dda55-122">[詳細資料檢視] 窗格會提供 BizTalk 群組的內容。</span><span class="sxs-lookup"><span data-stu-id="dda55-122">The Details View pane provides the properties of the BizTalk group.</span></span>|  
|<span data-ttu-id="dda55-123">主機狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-123">Host State View</span></span>|<span data-ttu-id="dda55-124">這是顯示的 BizTalk 主控件的健全狀況儀表板檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-124">This is a dashboard view that displays the health of a BizTalk host.</span></span> <span data-ttu-id="dda55-125">BizTalk 主控件的健全狀況取決於裝載 BizTalk 應用程式的執行個體的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="dda55-125">The health of a BizTalk host depends on the health of the instances of the hosted BizTalk applications.</span></span> <span data-ttu-id="dda55-126">[詳細資料檢視] 窗格會提供 BizTalk 主控件的屬性。</span><span class="sxs-lookup"><span data-stu-id="dda55-126">The Details View pane provides the properties of the BizTalk host.</span></span>|  
  
#### <a name="application-artifacts-views"></a><span data-ttu-id="dda55-127">應用程式成品檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-127">Application Artifacts Views</span></span>  
 <span data-ttu-id="dda55-128">應用程式成品檢視包含下表中所述的元素。</span><span class="sxs-lookup"><span data-stu-id="dda55-128">Application artifacts views contain the elements described in the following table.</span></span>  
  
### <a name="elements"></a><span data-ttu-id="dda55-129">元素</span><span class="sxs-lookup"><span data-stu-id="dda55-129">Elements</span></span>  
  
|<span data-ttu-id="dda55-130">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="dda55-130">View Name</span></span>|<span data-ttu-id="dda55-131">Description</span><span class="sxs-lookup"><span data-stu-id="dda55-131">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dda55-132">協調流程狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-132">Orchestrations State View</span></span>|<span data-ttu-id="dda55-133">顯示裝載的應用程式的協調流程的組態和執行階段狀態。</span><span class="sxs-lookup"><span data-stu-id="dda55-133">Displays the configuration and runtime state of Orchestration for the hosted application.</span></span>|  
|<span data-ttu-id="dda55-134">接收位置的狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-134">Receive Location State View</span></span>|<span data-ttu-id="dda55-135">顯示裝載的應用程式的接收位置的組態和執行階段狀態。</span><span class="sxs-lookup"><span data-stu-id="dda55-135">Displays the configuration and runtime state of Receive Location for the hosted application.</span></span>|  
|<span data-ttu-id="dda55-136">接收連接埠狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-136">Receive Ports State View</span></span>|<span data-ttu-id="dda55-137">顯示裝載的應用程式的接收埠的組態和執行階段狀態。</span><span class="sxs-lookup"><span data-stu-id="dda55-137">Displays the configuration and runtime state of Receive Ports for the hosted application.</span></span>|  
|<span data-ttu-id="dda55-138">傳送埠群組狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-138">Send Port Groups State View</span></span>|<span data-ttu-id="dda55-139">顯示裝載的應用程式的傳送埠群組的組態和執行階段狀態。</span><span class="sxs-lookup"><span data-stu-id="dda55-139">Displays the configuration and runtime state of Send Port Group for the hosted application.</span></span>|  
|<span data-ttu-id="dda55-140">傳送連接埠狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-140">Send Port State View</span></span>|<span data-ttu-id="dda55-141">顯示裝載的應用程式的傳送埠的組態和執行階段狀態。</span><span class="sxs-lookup"><span data-stu-id="dda55-141">Displays the configuration and runtime state of Send Port for the hosted application.</span></span>|  
  
## <a name="deployment-views"></a><span data-ttu-id="dda55-142">部署檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-142">Deployment Views</span></span>  
 <span data-ttu-id="dda55-143">部署檢視包含下表中所述的元素。</span><span class="sxs-lookup"><span data-stu-id="dda55-143">Deployment views contain the elements described in the following table.</span></span>  
  
### <a name="elements"></a><span data-ttu-id="dda55-144">元素</span><span class="sxs-lookup"><span data-stu-id="dda55-144">Elements</span></span>  
  
|<span data-ttu-id="dda55-145">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="dda55-145">View Name</span></span>|<span data-ttu-id="dda55-146">Description</span><span class="sxs-lookup"><span data-stu-id="dda55-146">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dda55-147">部署狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-147">Deployment State View</span></span>|<span data-ttu-id="dda55-148">這是會顯示 BizTalk 部署群組的健全狀況儀表板檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-148">This is a dashboard view that displays the health of a BizTalk deployment group.</span></span> <span data-ttu-id="dda55-149">BizTalk 部署群組的健全狀況取決於其構成的執行階段伺服器元件，例如 BAM 角色、 規則引擎的角色，BizTalk 執行階段角色和 BizTalk 主控件的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="dda55-149">The health of the BizTalk deployment group depends on the health of its constituent runtime server components such as BAM Role, Rule Engine Role, BizTalk Run-time Role and BizTalk Host.</span></span> <span data-ttu-id="dda55-150">[詳細資料檢視] 窗格會提供 BizTalk 部署群組的內容。</span><span class="sxs-lookup"><span data-stu-id="dda55-150">The Details View pane provides the properties of the BizTalk deployment group.</span></span>|  
|<span data-ttu-id="dda55-151">主機狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-151">Hosts State View</span></span>|<span data-ttu-id="dda55-152">這是顯示的 BizTalk 主控件的健全狀況儀表板檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-152">This is a dashboard view that displays the health of a BizTalk host.</span></span> <span data-ttu-id="dda55-153">BizTalk 主控件的健全狀況取決於裝載 BizTalk 應用程式的執行個體的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="dda55-153">The health of a BizTalk host depends on the health of the instances of the hosted BizTalk applications.</span></span> <span data-ttu-id="dda55-154">[詳細資料檢視] 窗格會提供 BizTalk 主控件的屬性。</span><span class="sxs-lookup"><span data-stu-id="dda55-154">The Details View pane provides the properties of the BizTalk host.</span></span>|  
|<span data-ttu-id="dda55-155">規則引擎的角色狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-155">Rule Engine Role State View</span></span>|<span data-ttu-id="dda55-156">這是顯示在執行階段伺服器正在執行規則引擎服務的健全狀況儀表板檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-156">This is a dashboard view that displays the health of a Rule Engine service that is running on the runtime servers.</span></span> <span data-ttu-id="dda55-157">[詳細資料檢視] 窗格會提供已安裝的規則引擎服務的執行階段伺服器的屬性。</span><span class="sxs-lookup"><span data-stu-id="dda55-157">The Details View pane provides the properties of the runtime servers that have Rule Engine service installed.</span></span>|  
|<span data-ttu-id="dda55-158">執行階段角色狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-158">Runtime Role State View</span></span>|<span data-ttu-id="dda55-159">這是會顯示已安裝執行階段規則引擎服務的執行階段伺服器的健全狀況儀表板檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-159">This is a dashboard view that displays the health of the runtime servers that have runtime rule engine service installed.</span></span> <span data-ttu-id="dda55-160">BizTalk 執行階段角色的健全狀況取決於其元件，例如 SSO 服務、 管理資料庫、 messagebox 資料庫、 SSO 資料庫和追蹤資料庫的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="dda55-160">The health of a BizTalk Run-time Role depends on the health of its components such as SSO Service, management database, message box database, SSO database and tracking database.</span></span> <span data-ttu-id="dda55-161">[詳細資料檢視] 窗格會提供執行階段伺服器的內容。</span><span class="sxs-lookup"><span data-stu-id="dda55-161">The Details View pane provides the properties of the runtime servers.</span></span>|  
  
### <a name="bam-component-views"></a><span data-ttu-id="dda55-162">BAM 元件檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-162">BAM Component Views</span></span>  
  
### <a name="elements"></a><span data-ttu-id="dda55-163">元素</span><span class="sxs-lookup"><span data-stu-id="dda55-163">Elements</span></span>  
  
|<span data-ttu-id="dda55-164">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="dda55-164">View Name</span></span>|<span data-ttu-id="dda55-165">Description</span><span class="sxs-lookup"><span data-stu-id="dda55-165">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dda55-166">BAM 警示的狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-166">BAM Alerts State View</span></span>|<span data-ttu-id="dda55-167">顯示 BizTalk BAM 警示元件的狀態檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-167">Displays the state view of BizTalk BAM alerts component.</span></span>|  
|<span data-ttu-id="dda55-168">BAM 分析狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-168">BAM Analysis State View</span></span>|<span data-ttu-id="dda55-169">顯示 BizTalk BAM 分析元件的狀態檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-169">Displays the state view of BizTalk BAM analysis component.</span></span>|  
|<span data-ttu-id="dda55-170">BAM 效能檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-170">BAM Performance View</span></span>|<span data-ttu-id="dda55-171">[圖例] 窗格會顯示 BAM 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="dda55-171">The Legend pane displays the performance counter for BAM.</span></span>|  
|<span data-ttu-id="dda55-172">BAM 入口網站狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-172">BAM Portal State View</span></span>|<span data-ttu-id="dda55-173">顯示 BAM 入口網站的狀態檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-173">Displays the state view of BAM portal.</span></span>|  
|<span data-ttu-id="dda55-174">BAM 執行階段狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-174">BAM Run-time State View</span></span>|<span data-ttu-id="dda55-175">顯示 BAM 執行階段的狀態檢視。</span><span class="sxs-lookup"><span data-stu-id="dda55-175">Displays the state view of BAM run-time.</span></span>|  
  
#### <a name="bam-alerts"></a><span data-ttu-id="dda55-176">BAM 警示</span><span class="sxs-lookup"><span data-stu-id="dda55-176">BAM Alerts</span></span>  
  
### <a name="elements"></a><span data-ttu-id="dda55-177">元素</span><span class="sxs-lookup"><span data-stu-id="dda55-177">Elements</span></span>  
  
|<span data-ttu-id="dda55-178">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="dda55-178">View Name</span></span>|<span data-ttu-id="dda55-179">Description</span><span class="sxs-lookup"><span data-stu-id="dda55-179">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dda55-180">BAM 警示的狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-180">BAM Alerts State View</span></span>|<span data-ttu-id="dda55-181">顯示其通知服務，並產生任何重要的服務時無法使用 BizTalk BAM 警示的清單。</span><span class="sxs-lookup"><span data-stu-id="dda55-181">Displays a list of BizTalk BAM alerts which is a notification service and generated when any of the critical services are unavailable.</span></span>|  
  
##### <a name="runtime-component-views"></a><span data-ttu-id="dda55-182">執行階段元件檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-182">Runtime Component Views</span></span>  
  
### <a name="elements"></a><span data-ttu-id="dda55-183">元素</span><span class="sxs-lookup"><span data-stu-id="dda55-183">Elements</span></span>  
  
|<span data-ttu-id="dda55-184">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="dda55-184">View Name</span></span>|<span data-ttu-id="dda55-185">Description</span><span class="sxs-lookup"><span data-stu-id="dda55-185">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dda55-186">應用程式服務狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-186">Application Service State View</span></span>|<span data-ttu-id="dda55-187">顯示在 BizTalk 群組中的所有主控件執行個體的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="dda55-187">Displays the health of all host instances in a BizTalk group.</span></span>|  
|<span data-ttu-id="dda55-188">訊息方塊效能狀態檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-188">Message Box Performance State View</span></span>|<span data-ttu-id="dda55-189">[圖例] 窗格會顯示訊息方塊追蹤資料大小的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="dda55-189">The Legend pane displays the performance counter for Message Box Tracking Data Size.</span></span>|  
|<span data-ttu-id="dda55-190">傳訊配接器效能檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-190">Messaging Adapters Performance View</span></span>|<span data-ttu-id="dda55-191">[圖例] 窗格顯示的效能計數器的 MSMQ 接收配接器接收的位元組。</span><span class="sxs-lookup"><span data-stu-id="dda55-191">The Legend pane displays the performance counter for MSMQ Receive Adapter Bytes Received.</span></span>|  
|<span data-ttu-id="dda55-192">傳訊效能檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-192">Messaging Performance View</span></span>|<span data-ttu-id="dda55-193">[圖例] 窗格會顯示使用中的接收位置的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="dda55-193">The Legend pane displays the performance counter for Active Receive Locations.</span></span>|  
|<span data-ttu-id="dda55-194">協調流程效能檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-194">Orchestration Performance View</span></span>|<span data-ttu-id="dda55-195">[圖例] 窗格會顯示為可執行的協調流程的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="dda55-195">The Legend pane displays the performance counter for Runnable Orchestrations.</span></span>|  
|<span data-ttu-id="dda55-196">伺服器資源使用狀況 檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-196">Server Resource Usage View</span></span>|<span data-ttu-id="dda55-197">[圖例] 窗格顯示的效能計數器的實體磁碟閒置時間百分比。</span><span class="sxs-lookup"><span data-stu-id="dda55-197">The Legend pane displays the performance counter for Physical Disk Percentage Idle Time.</span></span>|  
  
###### <a name="runtime-alerts"></a><span data-ttu-id="dda55-198">執行階段警示</span><span class="sxs-lookup"><span data-stu-id="dda55-198">Runtime Alerts</span></span>  
  
### <a name="elements"></a><span data-ttu-id="dda55-199">元素</span><span class="sxs-lookup"><span data-stu-id="dda55-199">Elements</span></span>  
  
|<span data-ttu-id="dda55-200">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="dda55-200">View Name</span></span>|<span data-ttu-id="dda55-201">Description</span><span class="sxs-lookup"><span data-stu-id="dda55-201">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dda55-202">核心警示檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-202">Core Alerts View</span></span>|<span data-ttu-id="dda55-203">顯示 BizTalk 核心警示。</span><span class="sxs-lookup"><span data-stu-id="dda55-203">Displays BizTalk core alerts.</span></span>|  
|<span data-ttu-id="dda55-204">訊息的警示檢視</span><span class="sxs-lookup"><span data-stu-id="dda55-204">Messaging Alerts View</span></span>|<span data-ttu-id="dda55-205">顯示 BizTalk 訊息的警示。</span><span class="sxs-lookup"><span data-stu-id="dda55-205">Displays BizTalk messaging alerts.</span></span>|