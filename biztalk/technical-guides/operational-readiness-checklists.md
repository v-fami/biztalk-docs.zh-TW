---
title: 作業整備檢查清單 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c308a876-9872-43b3-a1fb-76e81396612f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76cab24c2ba0d47baa22dbe694a1d929e98c8f9d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002751"
---
# <a name="operational-readiness-checklists"></a><span data-ttu-id="be9b1-102">作業整備檢查清單</span><span class="sxs-lookup"><span data-stu-id="be9b1-102">Operational Readiness Checklists</span></span>
<span data-ttu-id="be9b1-103">作業整備檢查清單包含您應該考慮的建議和部署 BizTalk 解決方案到生產環境之前，您應該執行的工作。</span><span class="sxs-lookup"><span data-stu-id="be9b1-103">The Operational Readiness checklists contain recommendations that you should consider and tasks that you should perform before deploying a BizTalk solution into production.</span></span> <span data-ttu-id="be9b1-104">這些檢查清單包含資訊來設定必要的軟體，進而提高可用性，監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境和測試的程序。</span><span class="sxs-lookup"><span data-stu-id="be9b1-104">These checklists include information for configuring prerequisite software, increasing availability, monitoring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, and procedures for testing.</span></span>  
  
 <span data-ttu-id="be9b1-105">因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上維護相依性，因此許多其他 Microsoft 技術，您應該完成工作的每個相依的技術，可協助確保您的生產環境[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境能順利執行。</span><span class="sxs-lookup"><span data-stu-id="be9b1-105">Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] maintains dependencies on so many other Microsoft technologies, you should complete the tasks for each dependent technology to help ensure that your production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment runs smoothly.</span></span>  
  
## <a name="typical-prerequisite-software"></a><span data-ttu-id="be9b1-106">典型的先決條件軟體</span><span class="sxs-lookup"><span data-stu-id="be9b1-106">Typical Prerequisite Software</span></span>  
 <span data-ttu-id="be9b1-107">必要軟體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式平台通常會包含下列產品：</span><span class="sxs-lookup"><span data-stu-id="be9b1-107">Prerequisite software for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform typically includes the following products:</span></span>  
  
- <span data-ttu-id="be9b1-108">Windows 作業系統</span><span class="sxs-lookup"><span data-stu-id="be9b1-108">The Windows operating system</span></span>  
  
- <span data-ttu-id="be9b1-109">[SQL Server]</span><span class="sxs-lookup"><span data-stu-id="be9b1-109">SQL Server</span></span> 
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- <span data-ttu-id="be9b1-110">Visual Studio （適用於開發用途，不是在執行階段）</span><span class="sxs-lookup"><span data-stu-id="be9b1-110">Visual Studio (for development purposes, not at run time)</span></span>  
  
## <a name="additional-components"></a><span data-ttu-id="be9b1-111">其他元件</span><span class="sxs-lookup"><span data-stu-id="be9b1-111">Additional Components</span></span>  
 <span data-ttu-id="be9b1-112">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式平台也可能需要數個下列軟體元件：</span><span class="sxs-lookup"><span data-stu-id="be9b1-112">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform may also require several of the following software components:</span></span>  
  
- <span data-ttu-id="be9b1-113">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="be9b1-113">Internet Information Services (IIS)</span></span>  
  
- <span data-ttu-id="be9b1-114">SharePoint</span><span class="sxs-lookup"><span data-stu-id="be9b1-114">SharePoint</span></span>
  
- <span data-ttu-id="be9b1-115">Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="be9b1-115">Microsoft Office Excel</span></span> 
  
  > [!NOTE]  
  >  <span data-ttu-id="be9b1-116">BizTalk Server 支援僅 32 位元版本的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="be9b1-116">BizTalk Server supports only the 32-bit version of Microsoft Office.</span></span>  
  
- <span data-ttu-id="be9b1-117">[SQL Server]</span><span class="sxs-lookup"><span data-stu-id="be9b1-117">SQL Server</span></span>
  
- <span data-ttu-id="be9b1-118">SQLXML</span><span class="sxs-lookup"><span data-stu-id="be9b1-118">SQLXML</span></span> 
  
- <span data-ttu-id="be9b1-119">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="be9b1-119">.NET Framework</span></span> 
  
- <span data-ttu-id="be9b1-120">若要針對特定啟用功能的非 Microsoft 元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。</span><span class="sxs-lookup"><span data-stu-id="be9b1-120">Non-Microsoft components to enable functionality for certain [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.</span></span>  
  
  <span data-ttu-id="be9b1-121">如需相依性軟體所需的各種 Windows 作業系統版本的 BizTalk 應用程式平台特定功能的詳細資訊，請參閱[什麼是新、 安裝、 設定和升級](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span><span class="sxs-lookup"><span data-stu-id="be9b1-121">For more information about the dependency software that is required for specific features of the BizTalk application platform for various Windows operating system versions, see [What's New, Installation, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>
- 
  
## <a name="next-steps"></a><span data-ttu-id="be9b1-122">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="be9b1-122">Next steps</span></span>
  
-   [<span data-ttu-id="be9b1-123">檢查清單：開始使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="be9b1-123">Checklist: Getting Started with BizTalk Server</span></span>](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [<span data-ttu-id="be9b1-124">檢查清單：設定 Windows Server</span><span class="sxs-lookup"><span data-stu-id="be9b1-124">Checklist: Configuring Windows Server</span></span>](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [<span data-ttu-id="be9b1-125">檢查清單：設定 Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="be9b1-125">Checklist: Configuring Internet Information Services</span></span>](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [<span data-ttu-id="be9b1-126">檢查清單：設定 SQL Server</span><span class="sxs-lookup"><span data-stu-id="be9b1-126">Checklist: Configuring SQL Server</span></span>](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [<span data-ttu-id="be9b1-127">檢查清單：設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="be9b1-127">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [<span data-ttu-id="be9b1-128">檢查清單：提供高可用性與容錯或負載平衡</span><span class="sxs-lookup"><span data-stu-id="be9b1-128">Checklist: Providing High Availability with Fault Tolerance or Load Balancing</span></span>](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [<span data-ttu-id="be9b1-129">檢查清單：利用災害復原功能提高可用性</span><span class="sxs-lookup"><span data-stu-id="be9b1-129">Checklist: Increasing Availability with Disaster Recovery</span></span>](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [<span data-ttu-id="be9b1-130">檢查清單：監視作業整備</span><span class="sxs-lookup"><span data-stu-id="be9b1-130">Checklist: Monitoring Operational Readiness</span></span>](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [<span data-ttu-id="be9b1-131">檢查清單：維護和疑難排解 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="be9b1-131">Checklist: Maintaining and Troubleshooting BizTalk Server Databases</span></span>](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="be9b1-132">檢查清單：測試作業整備</span><span class="sxs-lookup"><span data-stu-id="be9b1-132">Checklist: Testing Operational Readiness</span></span>](../technical-guides/checklist-testing-operational-readiness.md)