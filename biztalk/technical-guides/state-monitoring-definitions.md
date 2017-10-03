---
title: "狀態監控定義 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa2c8247-5e25-4624-9f0d-c7fe621ffba2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97007535e67a4c3540278cee7ff82fec18d492c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="state-monitoring-definitions"></a><span data-ttu-id="7716f-102">狀態監控定義</span><span class="sxs-lookup"><span data-stu-id="7716f-102">State Monitoring Definitions</span></span>
<span data-ttu-id="7716f-103">狀態監視，可協助回答的受監視的電腦是否狀況良好從特定的應用程式的觀點來看一個給定時間問題。</span><span class="sxs-lookup"><span data-stu-id="7716f-103">State monitoring helps answer the question of whether a monitored computer is healthy at a given time from the perspective of a particular application.</span></span> <span data-ttu-id="7716f-104">System Center Operations Manager (SCOM) 更新對使用者公開的不同 managed 實體的狀態，並將狀態顯示的狀態監視檢視的一部分。</span><span class="sxs-lookup"><span data-stu-id="7716f-104">System Center Operations Manager (SCOM) updates the status of different managed entities exposed to the user and presents the status as part of the state monitoring view.</span></span>  
  
 <span data-ttu-id="7716f-105">若要了解[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]監視檢視的狀態，您必須了解 SCOM 狀態監控的基本概念。</span><span class="sxs-lookup"><span data-stu-id="7716f-105">To understand the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] State Monitoring view, you must understand the concepts behind SCOM state monitoring.</span></span> <span data-ttu-id="7716f-106">下列用語將會用來描述狀態監控的主要組成部分：</span><span class="sxs-lookup"><span data-stu-id="7716f-106">The following terminology is used to describe the key components of state monitoring:</span></span>  
  
-   <span data-ttu-id="7716f-107">**角色**-伺服器由服務探索所決定的環境中執行的角色。</span><span class="sxs-lookup"><span data-stu-id="7716f-107">**Role** - A role that a server is performing in an environment as determined by service discovery.</span></span> <span data-ttu-id="7716f-108">例如，BizTalk 執行階段角色封裝的執行階段成品和 BizTalk Server 中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7716f-108">For example, the BizTalk run-time role encapsulates the runtime artifacts and instances in BizTalk Server.</span></span>  
  
-   <span data-ttu-id="7716f-109">**元件**-子角色健全狀況彙總的一部分用於測量伺服器角色的整體健全狀況。</span><span class="sxs-lookup"><span data-stu-id="7716f-109">**Component** - A sub-role that is used as part of the health roll-up to measure the overall health of the server role.</span></span> <span data-ttu-id="7716f-110">例如，BAM 警示元件用來產生警示，以指示整體健全狀況狀態。</span><span class="sxs-lookup"><span data-stu-id="7716f-110">For example, the BAM alert component is used to generate alerts to indicate the status of overall health.</span></span>  
  
-   <span data-ttu-id="7716f-111">**執行個體**-特定電腦可能裝載伺服器角色的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7716f-111">**Instance** - A particular computer may host instance(s) of the server role.</span></span>  
  
 <span data-ttu-id="7716f-112">簡單地說，SCOM 狀態監控的重要原則如下：</span><span class="sxs-lookup"><span data-stu-id="7716f-112">In brief, the following are the important principles of SCOM state monitoring:</span></span>  
  
-   <span data-ttu-id="7716f-113">電腦群組的健全狀況被衍生自電腦群組中所含電腦的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="7716f-113">Health of a computer group is derived from the health of the computers that are contained in the computer group.</span></span>  
  
-   <span data-ttu-id="7716f-114">電腦的狀態會顯示電腦上執行的應用程式 (稱為伺服器角色) 是否狀況良好，而此狀況是由其中裝載之應用程式的狀況衍生而來。</span><span class="sxs-lookup"><span data-stu-id="7716f-114">The status of the computer shows whether applications (referred as server roles) running on the computer are healthy, and the health is derived from the health of the hosted applications.</span></span>  
  
-   <span data-ttu-id="7716f-115">在應用程式層級 (伺服器角色) 上，伺服器角色的狀態是伺服器角色之所有應用程式執行個體的整體狀態。</span><span class="sxs-lookup"><span data-stu-id="7716f-115">At the application level (server role), the status of the server role is the overall status of all application instances of that server role.</span></span> <span data-ttu-id="7716f-116">比方說，健全狀況的一個或多個成品，如協調流程、 接收位置、 接收埠和等會影響 BizTalk 應用程式的整體健全狀況與狀態。</span><span class="sxs-lookup"><span data-stu-id="7716f-116">For example, health of one or more artifacts like orchestrations, receives locations, receives ports and so on affects the status and overall health of a BizTalk application.</span></span>  
  
-   <span data-ttu-id="7716f-117">在應用程式的執行個體層級 （伺服器角色執行個體），應用程式執行個體的健全狀況被衍生自應用程式執行個體 （稱為元件） 各個不同部分的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="7716f-117">At the application instance level (server role instance), the health of the application instance is derived from the health of different areas of the application instance (known as components).</span></span>  
  
-   <span data-ttu-id="7716f-118">SCOM 警示與元件的健康狀況有關聯。</span><span class="sxs-lookup"><span data-stu-id="7716f-118">SCOM alerts are associated with the health of a component.</span></span> <span data-ttu-id="7716f-119">當觸發警示以指示整體狀況時，元件狀態會設定為紅色、黃色或綠色。</span><span class="sxs-lookup"><span data-stu-id="7716f-119">Status of a component is set to red, yellow, or green when alerts are triggered to indicate overall health.</span></span>  
  
-   <span data-ttu-id="7716f-120">元件的狀況對伺服器角色的狀況會產生一定程度的影響。</span><span class="sxs-lookup"><span data-stu-id="7716f-120">Health of a component contributes to the health of the server role.</span></span>  
  
 <span data-ttu-id="7716f-121">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中：</span><span class="sxs-lookup"><span data-stu-id="7716f-121">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="7716f-122">每個 BizTalk Server 會視為 BizTalk 伺服器角色的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7716f-122">Each BizTalk Server is considered an instance of the BizTalk Server role.</span></span>  
  
-   <span data-ttu-id="7716f-123">因此，電腦中的 BizTalk Server 角色經過計算之後，其結果所代表的會是該電腦中所有 BizTalk Server 處理序的所有事件/活動。</span><span class="sxs-lookup"><span data-stu-id="7716f-123">The BizTalk Server role in a computer will therefore be computed as a result of all events/activities of all the BizTalk Server processes in that computer.</span></span>  
  
 <span data-ttu-id="7716f-124">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件會提供狀態的監視包括 BizTalk Server 成品</span><span class="sxs-lookup"><span data-stu-id="7716f-124">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack provides state monitoring for BizTalk Server artifacts which includes</span></span>  
  
-   <span data-ttu-id="7716f-125">應用程式的成品，例如協調流程。</span><span class="sxs-lookup"><span data-stu-id="7716f-125">Application artifacts such as orchestrations.</span></span> <span data-ttu-id="7716f-126">訊息元件，例如接收埠、 接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="7716f-126">Messaging components such as receive ports, receive locations, and send ports.</span></span>  
  
-   <span data-ttu-id="7716f-127">部署的成品，例如伺服器、 主控件執行個體，SSO，依此類推。</span><span class="sxs-lookup"><span data-stu-id="7716f-127">Deployment artifacts such as servers, host instances, SSO and so on.</span></span>  
  
 <span data-ttu-id="7716f-128">下表列出以視覺方式表示所有 BizTalk Server 平台和應用程式層級成品的健全狀況狀態的 3 種狀態。</span><span class="sxs-lookup"><span data-stu-id="7716f-128">The following table lists the three states that visually represent the health status of all BizTalk Server platform and application level artifacts.</span></span> <span data-ttu-id="7716f-129">這種方式可以在多伺服器部署中，為 SCOM 操作員提供高層次的檢視，以便快速專注於重要的問題。</span><span class="sxs-lookup"><span data-stu-id="7716f-129">This provides the SCOM operator a high-level view of a multi-server deployment in order to focus on important problems quickly.</span></span>  
  
|<span data-ttu-id="7716f-130">成品</span><span class="sxs-lookup"><span data-stu-id="7716f-130">Artifacts</span></span>|<span data-ttu-id="7716f-131">綠色</span><span class="sxs-lookup"><span data-stu-id="7716f-131">Green</span></span>|<span data-ttu-id="7716f-132">黃色</span><span class="sxs-lookup"><span data-stu-id="7716f-132">Yellow</span></span>|<span data-ttu-id="7716f-133">紅色</span><span class="sxs-lookup"><span data-stu-id="7716f-133">Red</span></span>|  
|---------------|-----------|------------|---------|  
|<span data-ttu-id="7716f-134">應用程式層級成品</span><span class="sxs-lookup"><span data-stu-id="7716f-134">Application level artifacts</span></span>|<span data-ttu-id="7716f-135">處於執行狀態。</span><span class="sxs-lookup"><span data-stu-id="7716f-135">Are in a running state.</span></span>|<span data-ttu-id="7716f-136">不超過 70%的執行個體將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7716f-136">Less than 70% of the   instances are faulted.</span></span>|<span data-ttu-id="7716f-137">多個執行個體的 70%會發生錯誤，或是可能導致嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="7716f-137">More than 70% of the instances are faulted or have resulted in critical errors.</span></span>|  
|<span data-ttu-id="7716f-138">部署層級成品</span><span class="sxs-lookup"><span data-stu-id="7716f-138">Deployment level artifacts</span></span>|<span data-ttu-id="7716f-139">處於執行狀態。</span><span class="sxs-lookup"><span data-stu-id="7716f-139">Are in a running state.</span></span>|<span data-ttu-id="7716f-140">不適用</span><span class="sxs-lookup"><span data-stu-id="7716f-140">Not applicable</span></span>|<span data-ttu-id="7716f-141">不在執行中狀態或已停止。</span><span class="sxs-lookup"><span data-stu-id="7716f-141">Are not in a running state or have stopped.</span></span>|