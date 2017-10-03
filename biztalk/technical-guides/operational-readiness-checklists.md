---
title: "操作的整備檢查清單 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c308a876-9872-43b3-a1fb-76e81396612f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87da295129a4cb90ecf643cd06eb18ac3e6aa18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operational-readiness-checklists"></a><span data-ttu-id="cabdc-102">操作的整備檢查清單</span><span class="sxs-lookup"><span data-stu-id="cabdc-102">Operational Readiness Checklists</span></span>
<span data-ttu-id="cabdc-103">操作的整備檢查清單包含您應該考慮的建議和部署 BizTalk 解決方案到實際執行環境之前，您應該執行的工作。</span><span class="sxs-lookup"><span data-stu-id="cabdc-103">The Operational Readiness checklists contain recommendations that you should consider and tasks that you should perform before deploying a BizTalk solution into production.</span></span> <span data-ttu-id="cabdc-104">這些檢查清單包括資訊設定必要條件軟體，進而提高可用性，監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，以及用於測試的程序。</span><span class="sxs-lookup"><span data-stu-id="cabdc-104">These checklists include information for configuring prerequisite software, increasing availability, monitoring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, and procedures for testing.</span></span>  
  
 <span data-ttu-id="cabdc-105">因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上維護相依性，因此許多其他 Microsoft 技術，您應該完成的每個相依的技術，可協助確保您的生產環境工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]順暢執行環境。</span><span class="sxs-lookup"><span data-stu-id="cabdc-105">Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] maintains dependencies on so many other Microsoft technologies, you should complete the tasks for each dependent technology to help ensure that your production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment runs smoothly.</span></span>  
  
## <a name="typical-prerequisite-software"></a><span data-ttu-id="cabdc-106">一般先決條件軟體</span><span class="sxs-lookup"><span data-stu-id="cabdc-106">Typical Prerequisite Software</span></span>  
 <span data-ttu-id="cabdc-107">先決條件軟體的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式平台通常包括下列產品：</span><span class="sxs-lookup"><span data-stu-id="cabdc-107">Prerequisite software for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform typically includes the following products:</span></span>  
  
-   <span data-ttu-id="cabdc-108">Windows 作業系統</span><span class="sxs-lookup"><span data-stu-id="cabdc-108">The Windows operating system</span></span>  
  
-   [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]<span data-ttu-id="cabdc-109">SP1 或[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cabdc-109"> SP1 or [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]<span data-ttu-id="cabdc-110">（適用於開發用途，不在執行階段）</span><span class="sxs-lookup"><span data-stu-id="cabdc-110"> (for development purposes, not at run time)</span></span>  
  
## <a name="additional-components"></a><span data-ttu-id="cabdc-111">其他元件</span><span class="sxs-lookup"><span data-stu-id="cabdc-111">Additional Components</span></span>  
 <span data-ttu-id="cabdc-112">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式平台也可能需要數個下列軟體元件：</span><span class="sxs-lookup"><span data-stu-id="cabdc-112">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform may also require several of the following software components:</span></span>  
  
-   <span data-ttu-id="cabdc-113">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="cabdc-113">Internet Information Services (IIS)</span></span>  
  
-   <span data-ttu-id="cabdc-114">Windows SharePoint® Services 2010</span><span class="sxs-lookup"><span data-stu-id="cabdc-114">Windows SharePoint® Services 2010</span></span>  
  
-   <span data-ttu-id="cabdc-115">SharePoint Foundation 2010</span><span class="sxs-lookup"><span data-stu-id="cabdc-115">SharePoint Foundation 2010</span></span>  
  
-   <span data-ttu-id="cabdc-116">Microsoft Office SharePoint Server 2007 Service Pack 1 (SP1) (MOSS)</span><span class="sxs-lookup"><span data-stu-id="cabdc-116">Microsoft Office SharePoint Server 2007 Service Pack 1 (SP1) (MOSS)</span></span>  
  
-   <span data-ttu-id="cabdc-117">SP1 或 SP2 的 Windows SharePoint Services 3.0</span><span class="sxs-lookup"><span data-stu-id="cabdc-117">Windows SharePoint Services 3.0 with SP1 or SP2</span></span>  
  
-   <span data-ttu-id="cabdc-118">Microsoft Office Excel 2010 或 2007</span><span class="sxs-lookup"><span data-stu-id="cabdc-118">Microsoft Office Excel 2010 or 2007</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="cabdc-119">支援僅 32 位元版本的 Microsoft Office 2010。</span><span class="sxs-lookup"><span data-stu-id="cabdc-119"> supports only the 32-bit version of Microsoft Office 2010.</span></span>  
  
-   <span data-ttu-id="cabdc-120">SQL Server 2005 Notification Services</span><span class="sxs-lookup"><span data-stu-id="cabdc-120">SQL Server 2005 Notification Services</span></span>  
  
-   <span data-ttu-id="cabdc-121">SQLXML 4.0 搭配 Service Pack 1</span><span class="sxs-lookup"><span data-stu-id="cabdc-121">SQLXML 4.0 with Service Pack 1</span></span>  
  
-   <span data-ttu-id="cabdc-122">.NET framework 1.0</span><span class="sxs-lookup"><span data-stu-id="cabdc-122">.NET Framework 1.0</span></span>  
  
-   <span data-ttu-id="cabdc-123">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="cabdc-123">.NET Framework 2.0</span></span>  
  
-   <span data-ttu-id="cabdc-124">.NET framework 3.0</span><span class="sxs-lookup"><span data-stu-id="cabdc-124">.NET Framework 3.0</span></span>  
  
-   <span data-ttu-id="cabdc-125">Microsoft.NET Framework 4 和.Net Framework 3.5 Service pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="cabdc-125">Microsoft .NET Framework 4 and .Net Framework 3.5 with Service Pack 1 (SP1)</span></span>  
  
-   <span data-ttu-id="cabdc-126">若要啟用功能特定的非 Microsoft 元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。</span><span class="sxs-lookup"><span data-stu-id="cabdc-126">Non-Microsoft components to enable functionality for certain [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.</span></span>  
  
 <span data-ttu-id="cabdc-127">如需各種 Windows 作業系統版本的 BizTalk 應用程式平台的特定功能需要的相依性軟體的詳細資訊，請參閱中的 「 功能相依性矩陣 」 一節[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝和升級為特定的 Windows 作業系統版本的指南。</span><span class="sxs-lookup"><span data-stu-id="cabdc-127">For more information about the dependency software that is required for specific features of the BizTalk application platform for various Windows operating system versions, see the "Feature Dependency Matrix" section in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installation and upgrade guide for the specific Windows operating system version.</span></span> <span data-ttu-id="cabdc-128">[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝與升級指南位於[http://go.microsoft.com/fwlink/?LinkID=152913](http://go.microsoft.com/fwlink/?LinkID=152913)。</span><span class="sxs-lookup"><span data-stu-id="cabdc-128">The [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installation and upgrade guides are available at [http://go.microsoft.com/fwlink/?LinkID=152913](http://go.microsoft.com/fwlink/?LinkID=152913).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cabdc-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="cabdc-129">In This Section</span></span>  
  
-   [<span data-ttu-id="cabdc-130">檢查清單： 開始使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cabdc-130">Checklist: Getting Started with BizTalk Server</span></span>](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [<span data-ttu-id="cabdc-131">檢查清單： 設定 Windows Server</span><span class="sxs-lookup"><span data-stu-id="cabdc-131">Checklist: Configuring Windows Server</span></span>](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [<span data-ttu-id="cabdc-132">檢查清單： 設定 Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="cabdc-132">Checklist: Configuring Internet Information Services</span></span>](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [<span data-ttu-id="cabdc-133">檢查清單： 設定 SQL Server</span><span class="sxs-lookup"><span data-stu-id="cabdc-133">Checklist: Configuring SQL Server</span></span>](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [<span data-ttu-id="cabdc-134">檢查清單： 設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cabdc-134">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [<span data-ttu-id="cabdc-135">檢查清單： 提供高可用性與容錯或負載平衡</span><span class="sxs-lookup"><span data-stu-id="cabdc-135">Checklist: Providing High Availability with Fault Tolerance or Load Balancing</span></span>](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [<span data-ttu-id="cabdc-136">檢查清單： 提高可用性與災害復原</span><span class="sxs-lookup"><span data-stu-id="cabdc-136">Checklist: Increasing Availability with Disaster Recovery</span></span>](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [<span data-ttu-id="cabdc-137">檢查清單： 監視操作整備</span><span class="sxs-lookup"><span data-stu-id="cabdc-137">Checklist: Monitoring Operational Readiness</span></span>](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [<span data-ttu-id="cabdc-138">檢查清單： 維護和疑難排解 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="cabdc-138">Checklist: Maintaining and Troubleshooting BizTalk Server Databases</span></span>](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="cabdc-139">檢查清單： 測試操作整備</span><span class="sxs-lookup"><span data-stu-id="cabdc-139">Checklist: Testing Operational Readiness</span></span>](../technical-guides/checklist-testing-operational-readiness.md)