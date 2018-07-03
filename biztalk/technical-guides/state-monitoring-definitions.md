---
title: 狀態監控定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2c8247-5e25-4624-9f0d-c7fe621ffba2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95a15bc55bce7c39bdae67e04ff0a323776a180a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011679"
---
# <a name="state-monitoring-definitions"></a><span data-ttu-id="972fd-102">狀態監控定義</span><span class="sxs-lookup"><span data-stu-id="972fd-102">State Monitoring Definitions</span></span>
<span data-ttu-id="972fd-103">狀態監視，可協助回答問題的受監視的電腦在指定的時間，從特定的應用程式的觀點來看中是否狀況良好。</span><span class="sxs-lookup"><span data-stu-id="972fd-103">State monitoring helps answer the question of whether a monitored computer is healthy at a given time from the perspective of a particular application.</span></span> <span data-ttu-id="972fd-104">System Center Operations Manager (SCOM) 更新不同受管理的實體公開給使用者的狀態，並將狀態顯示為狀態監視檢視的一部分。</span><span class="sxs-lookup"><span data-stu-id="972fd-104">System Center Operations Manager (SCOM) updates the status of different managed entities exposed to the user and presents the status as part of the state monitoring view.</span></span>  
  
 <span data-ttu-id="972fd-105">若要了解[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]狀態監視檢視，您必須瞭解 SCOM 狀態監控的基本概念。</span><span class="sxs-lookup"><span data-stu-id="972fd-105">To understand the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] State Monitoring view, you must understand the concepts behind SCOM state monitoring.</span></span> <span data-ttu-id="972fd-106">下列用語將會用來描述狀態監控的主要組成部分：</span><span class="sxs-lookup"><span data-stu-id="972fd-106">The following terminology is used to describe the key components of state monitoring:</span></span>  
  
- <span data-ttu-id="972fd-107">**角色**-伺服器由服務探索所決定的環境中執行的角色。</span><span class="sxs-lookup"><span data-stu-id="972fd-107">**Role** - A role that a server is performing in an environment as determined by service discovery.</span></span> <span data-ttu-id="972fd-108">例如，BizTalk 執行階段角色封裝的執行階段成品和 BizTalk Server 中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="972fd-108">For example, the BizTalk run-time role encapsulates the runtime artifacts and instances in BizTalk Server.</span></span>  
  
- <span data-ttu-id="972fd-109">**元件**-健全狀況彙總的一部分來評量伺服器角色的整體健全狀況的子角色。</span><span class="sxs-lookup"><span data-stu-id="972fd-109">**Component** - A sub-role that is used as part of the health roll-up to measure the overall health of the server role.</span></span> <span data-ttu-id="972fd-110">例如，BAM 警示元件用來產生警示，以指示整體健全狀況狀態。</span><span class="sxs-lookup"><span data-stu-id="972fd-110">For example, the BAM alert component is used to generate alerts to indicate the status of overall health.</span></span>  
  
- <span data-ttu-id="972fd-111">**執行個體**-特定電腦可能裝載伺服器角色的執行個體。</span><span class="sxs-lookup"><span data-stu-id="972fd-111">**Instance** - A particular computer may host instance(s) of the server role.</span></span>  
  
  <span data-ttu-id="972fd-112">簡單地說，SCOM 狀態監控的重要原則如下：</span><span class="sxs-lookup"><span data-stu-id="972fd-112">In brief, the following are the important principles of SCOM state monitoring:</span></span>  
  
- <span data-ttu-id="972fd-113">電腦群組的健全狀況被衍生自電腦群組中所含的電腦的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="972fd-113">Health of a computer group is derived from the health of the computers that are contained in the computer group.</span></span>  
  
- <span data-ttu-id="972fd-114">電腦的狀態會顯示電腦上執行的應用程式 (稱為伺服器角色) 是否狀況良好，而此狀況是由其中裝載之應用程式的狀況衍生而來。</span><span class="sxs-lookup"><span data-stu-id="972fd-114">The status of the computer shows whether applications (referred as server roles) running on the computer are healthy, and the health is derived from the health of the hosted applications.</span></span>  
  
- <span data-ttu-id="972fd-115">在應用程式層級 (伺服器角色) 上，伺服器角色的狀態是伺服器角色之所有應用程式執行個體的整體狀態。</span><span class="sxs-lookup"><span data-stu-id="972fd-115">At the application level (server role), the status of the server role is the overall status of all application instances of that server role.</span></span> <span data-ttu-id="972fd-116">比方說，健全狀況的一或多個成品，如協調流程、 接收位置、 接收埠和等會影響的 BizTalk 應用程式的整體健全狀況與狀態。</span><span class="sxs-lookup"><span data-stu-id="972fd-116">For example, health of one or more artifacts like orchestrations, receives locations, receives ports and so on affects the status and overall health of a BizTalk application.</span></span>  
  
- <span data-ttu-id="972fd-117">在應用程式的執行個體層級 （伺服器角色執行個體） 中，應用程式執行個體的健全狀況被衍生自應用程式執行個體 （稱為元件） 各個不同部分的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="972fd-117">At the application instance level (server role instance), the health of the application instance is derived from the health of different areas of the application instance (known as components).</span></span>  
  
- <span data-ttu-id="972fd-118">SCOM 警示與元件的健康狀況有關聯。</span><span class="sxs-lookup"><span data-stu-id="972fd-118">SCOM alerts are associated with the health of a component.</span></span> <span data-ttu-id="972fd-119">當觸發警示以指示整體狀況時，元件狀態會設定為紅色、黃色或綠色。</span><span class="sxs-lookup"><span data-stu-id="972fd-119">Status of a component is set to red, yellow, or green when alerts are triggered to indicate overall health.</span></span>  
  
- <span data-ttu-id="972fd-120">元件的狀況對伺服器角色的狀況會產生一定程度的影響。</span><span class="sxs-lookup"><span data-stu-id="972fd-120">Health of a component contributes to the health of the server role.</span></span>  
  
  <span data-ttu-id="972fd-121">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中：</span><span class="sxs-lookup"><span data-stu-id="972fd-121">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:</span></span>  
  
- <span data-ttu-id="972fd-122">每個 BizTalk Server 會被視為 BizTalk Server 角色的執行個體。</span><span class="sxs-lookup"><span data-stu-id="972fd-122">Each BizTalk Server is considered an instance of the BizTalk Server role.</span></span>  
  
- <span data-ttu-id="972fd-123">因此，電腦中的 BizTalk Server 角色經過計算之後，其結果所代表的會是該電腦中所有 BizTalk Server 處理序的所有事件/活動。</span><span class="sxs-lookup"><span data-stu-id="972fd-123">The BizTalk Server role in a computer will therefore be computed as a result of all events/activities of all the BizTalk Server processes in that computer.</span></span>  
  
  <span data-ttu-id="972fd-124">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件提供 BizTalk Server 成品，包括監視狀態</span><span class="sxs-lookup"><span data-stu-id="972fd-124">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack provides state monitoring for BizTalk Server artifacts which includes</span></span>  
  
- <span data-ttu-id="972fd-125">應用程式成品，例如協調流程。</span><span class="sxs-lookup"><span data-stu-id="972fd-125">Application artifacts such as orchestrations.</span></span> <span data-ttu-id="972fd-126">這類訊息元件的接收埠、 接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="972fd-126">Messaging components such as receive ports, receive locations, and send ports.</span></span>  
  
- <span data-ttu-id="972fd-127">部署成品，例如伺服器、 主控件執行個體，SSO，依此類推。</span><span class="sxs-lookup"><span data-stu-id="972fd-127">Deployment artifacts such as servers, host instances, SSO and so on.</span></span>  
  
  <span data-ttu-id="972fd-128">下表列出以視覺方式呈現所有 BizTalk Server 平台和應用程式層級成品的健全狀況狀態的三種狀態。</span><span class="sxs-lookup"><span data-stu-id="972fd-128">The following table lists the three states that visually represent the health status of all BizTalk Server platform and application level artifacts.</span></span> <span data-ttu-id="972fd-129">這種方式可以在多伺服器部署中，為 SCOM 操作員提供高層次的檢視，以便快速專注於重要的問題。</span><span class="sxs-lookup"><span data-stu-id="972fd-129">This provides the SCOM operator a high-level view of a multi-server deployment in order to focus on important problems quickly.</span></span>  
  
|<span data-ttu-id="972fd-130">成品</span><span class="sxs-lookup"><span data-stu-id="972fd-130">Artifacts</span></span>|<span data-ttu-id="972fd-131">綠色</span><span class="sxs-lookup"><span data-stu-id="972fd-131">Green</span></span>|<span data-ttu-id="972fd-132">黃色</span><span class="sxs-lookup"><span data-stu-id="972fd-132">Yellow</span></span>|<span data-ttu-id="972fd-133">紅色</span><span class="sxs-lookup"><span data-stu-id="972fd-133">Red</span></span>|  
|---------------|-----------|------------|---------|  
|<span data-ttu-id="972fd-134">應用程式層級成品</span><span class="sxs-lookup"><span data-stu-id="972fd-134">Application level artifacts</span></span>|<span data-ttu-id="972fd-135">處於執行狀態。</span><span class="sxs-lookup"><span data-stu-id="972fd-135">Are in a running state.</span></span>|<span data-ttu-id="972fd-136">錯誤不超過 70%的執行個體。</span><span class="sxs-lookup"><span data-stu-id="972fd-136">Less than 70% of the   instances are faulted.</span></span>|<span data-ttu-id="972fd-137">超過 70%的執行個體將會發生錯誤，或是導致嚴重的錯誤。</span><span class="sxs-lookup"><span data-stu-id="972fd-137">More than 70% of the instances are faulted or have resulted in critical errors.</span></span>|  
|<span data-ttu-id="972fd-138">部署層級成品</span><span class="sxs-lookup"><span data-stu-id="972fd-138">Deployment level artifacts</span></span>|<span data-ttu-id="972fd-139">處於執行狀態。</span><span class="sxs-lookup"><span data-stu-id="972fd-139">Are in a running state.</span></span>|<span data-ttu-id="972fd-140">不適用</span><span class="sxs-lookup"><span data-stu-id="972fd-140">Not applicable</span></span>|<span data-ttu-id="972fd-141">不在執行中狀態或已停止。</span><span class="sxs-lookup"><span data-stu-id="972fd-141">Are not in a running state or have stopped.</span></span>|