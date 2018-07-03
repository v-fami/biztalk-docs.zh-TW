---
title: 使用 Operations Manager 2007 監視的最佳作法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a5026c-ef59-498b-9bef-ea0f1c932eae
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d099ba9ea60fd8f553d4eaf2011e93a054f59e68
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018698"
---
# <a name="best-practices-for-monitoring-with-operations-manager-2007"></a><span data-ttu-id="8d8e3-102">使用 Operations Manager 2007 監視的最佳做法</span><span class="sxs-lookup"><span data-stu-id="8d8e3-102">Best Practices for Monitoring with Operations Manager 2007</span></span>
<span data-ttu-id="8d8e3-103">遵循本主題，有效地監視您的應用程式使用 Operations Manager 2007 中列出的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-103">Adhere to the best practices listed in this topic to effectively monitor your applications using Operations Manager 2007.</span></span>  
  
 <span data-ttu-id="8d8e3-104">**安裝其他管理組件，如需更完整的涵蓋範圍**</span><span class="sxs-lookup"><span data-stu-id="8d8e3-104">**Install additional management packs for more complete coverage**</span></span>  
  
- <span data-ttu-id="8d8e3-105">為了協助確保 Operations Manager 2007 監視重要的應用程式，在您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，您應該安裝下列管理組件：</span><span class="sxs-lookup"><span data-stu-id="8d8e3-105">To help ensure that Operations Manager 2007 monitors the key applications in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, you should install the following management packs:</span></span>  
  
  - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8d8e3-106"> （必要）</span><span class="sxs-lookup"><span data-stu-id="8d8e3-106"> (required)</span></span>  
  
  - <span data-ttu-id="8d8e3-107">Windows Server 作業系統 （選擇性）</span><span class="sxs-lookup"><span data-stu-id="8d8e3-107">Windows Server Operating System (optional)</span></span>  
  
  - <span data-ttu-id="8d8e3-108">Microsoft Windows Server 容錯移轉叢集 （如果叢集使用的選擇性）</span><span class="sxs-lookup"><span data-stu-id="8d8e3-108">Microsoft Windows Server Failover Cluster (if clusters are used, optional)</span></span>  
  
  - <span data-ttu-id="8d8e3-109">SQL Server 監視</span><span class="sxs-lookup"><span data-stu-id="8d8e3-109">SQL Server Monitoring</span></span>  
  
  - <span data-ttu-id="8d8e3-110">Internet Information Services 7</span><span class="sxs-lookup"><span data-stu-id="8d8e3-110">Internet Information Services 7</span></span>  
  
  - <span data-ttu-id="8d8e3-111">訊息佇列 (MSMQ) 5.0 （選擇性）</span><span class="sxs-lookup"><span data-stu-id="8d8e3-111">Message Queuing (MSMQ) 5.0 (optional)</span></span>  
  
  <span data-ttu-id="8d8e3-112">**檢閱並設定每日警示優先順序**</span><span class="sxs-lookup"><span data-stu-id="8d8e3-112">**Review and prioritize alerts on a daily basis**</span></span>  
  
- <span data-ttu-id="8d8e3-113">每日檢視警示並排定其優先順序有助於確保適時解決問題。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-113">Reviewing and prioritizing alerts on a daily basis helps to ensure that issues are resolved in a timely manner.</span></span>  
  
  <span data-ttu-id="8d8e3-114">**確認[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與 Operations Manager 2007 伺服器進行通訊。**</span><span class="sxs-lookup"><span data-stu-id="8d8e3-114">**Verify that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is communicating with the Operations Manager 2007 server.**</span></span>  
  
- <span data-ttu-id="8d8e3-115">如果執行的伺服器間的通訊失敗[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]及監視基礎結構中，您將不會收到警示。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-115">If communication fails between the servers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the monitoring infrastructure, you will not receive alerts.</span></span>  
  
  <span data-ttu-id="8d8e3-116">**啟用和停用規則視**</span><span class="sxs-lookup"><span data-stu-id="8d8e3-116">**Enable and disable rules as necessary**</span></span>  
  
- <span data-ttu-id="8d8e3-117">依照預設，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理封包中的部分規則會停用。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-117">By default, some of the rules in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack are disabled.</span></span> <span data-ttu-id="8d8e3-118">這些已停用的規則屬於下列類型： 需要自訂、 做為範本的規則和規則，以便監視其他規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]事件。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-118">These disabled rules are of the following types: rules needing customization, rules that serve as templates, and rules for monitoring additional [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] events.</span></span> <span data-ttu-id="8d8e3-119">請確定相關規則程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境會啟用。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-119">Make sure the relevant rules for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment are enabled.</span></span>  
  
  <span data-ttu-id="8d8e3-120">**自訂規則，視您的環境**</span><span class="sxs-lookup"><span data-stu-id="8d8e3-120">**Customize rules as necessary for your environment**</span></span>  
  
- <span data-ttu-id="8d8e3-121">您應該自訂中的規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件，以符合您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-121">You should customize the rules in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack to suit your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span> <span data-ttu-id="8d8e3-122">某些規則需要監視的閾值或時間精心定義的臨界值會根據您的特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-122">Some rules require monitoring thresholds or time thresholds that are best defined based on your specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span>  
  
  <span data-ttu-id="8d8e3-123">**建立額外的規則，必要時，根據規則中包含[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件**</span><span class="sxs-lookup"><span data-stu-id="8d8e3-123">**Create additional rules as necessary, based on the rules included in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack**</span></span>  
  
- <span data-ttu-id="8d8e3-124">規則可做為您建立成品，例如範本提供使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主機。</span><span class="sxs-lookup"><span data-stu-id="8d8e3-124">Rules are provided for use as templates for artifacts that you create, such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hosts.</span></span> <span data-ttu-id="8d8e3-125">建立下列成品專用規則時，您應該使用這些範本規則做為參考：</span><span class="sxs-lookup"><span data-stu-id="8d8e3-125">You should use these template rules as a reference when creating artifact-specific rules such as:</span></span>  
  
  -   <span data-ttu-id="8d8e3-126">主應用程式特定的規則，例如，裝載佇列監控 」，而裝載節流監視</span><span class="sxs-lookup"><span data-stu-id="8d8e3-126">Host-specific rules, for example, host queue monitoring, and host throttling monitoring</span></span>  
  
  -   <span data-ttu-id="8d8e3-127">MessageBox 專用規則</span><span class="sxs-lookup"><span data-stu-id="8d8e3-127">MessageBox-specific rules</span></span>  
  
  -   <span data-ttu-id="8d8e3-128">其他協力廠商元件的規則，例如 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="8d8e3-128">Rules for additional third party components, for example, MQSeries adapter</span></span>  
  
  <span data-ttu-id="8d8e3-129">**監視所有 BizTalk Server 相關元件**</span><span class="sxs-lookup"><span data-stu-id="8d8e3-129">**Monitor all the BizTalk Server related components**</span></span>  
  
  <span data-ttu-id="8d8e3-130">組成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]確定它們都在執行時，您應監視的環境包括但不是一定是限制為：</span><span class="sxs-lookup"><span data-stu-id="8d8e3-130">The components of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment that you should monitor to ensure that they are running include, but are not necessarily limited to:</span></span>  
  
- <span data-ttu-id="8d8e3-131">BizTalk 主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="8d8e3-131">BizTalk Host instances</span></span>  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]<span data-ttu-id="8d8e3-132"> 使用安裝的代理程式作業 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d8e3-132"> Agent jobs installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
- <span data-ttu-id="8d8e3-133">開發 BizTalk 解決方案的任何自訂服務</span><span class="sxs-lookup"><span data-stu-id="8d8e3-133">Any custom services developed for the BizTalk solution</span></span>  
  
- <span data-ttu-id="8d8e3-134">開發 BizTalk 解決方案的任何自訂資料庫的狀態</span><span class="sxs-lookup"><span data-stu-id="8d8e3-134">Status of any custom databases developed for the BizTalk solution</span></span>  
  
- <span data-ttu-id="8d8e3-135">任何自訂事件記錄檔項目與相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境</span><span class="sxs-lookup"><span data-stu-id="8d8e3-135">Any custom event log entries relevant to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8e3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d8e3-136">See Also</span></span>  
 [<span data-ttu-id="8d8e3-137">使用 System Center Operations Manager 2007 監視 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8d8e3-137">Monitoring BizTalk Server with System Center Operations Manager 2007</span></span>](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)