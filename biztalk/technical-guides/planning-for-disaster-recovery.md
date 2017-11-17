---
title: "規劃災害復原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a33e8875-cfde-4a60-9dab-fc6bb3ac4f1c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f342030cd016dc0b1ea015a463e8777d498f860
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-disaster-recovery"></a><span data-ttu-id="42b01-102">規劃損毀復原</span><span class="sxs-lookup"><span data-stu-id="42b01-102">Planning for Disaster Recovery</span></span>
<span data-ttu-id="42b01-103">本主題提供災害復原需求的應用程式小組和程序指引[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42b01-103">This topic provides guidance to application teams for disaster recovery requirements and procedures for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="42b01-104">Microsoft[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]會儲存在組態和處理資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42b01-104">Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] stores configuration and processing information in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="42b01-105">高可用性和災害復原透過的高可用性和災害復原功能來達成[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42b01-105"> high availability and disaster recovery is achieved through the high availability and disaster recovery capabilities of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="42b01-106">BizTalk 群組由一組資料庫裝載於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42b01-106">A BizTalk group is defined by a set of databases hosted in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="42b01-107">一組資料庫裝載於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可以成為高可用性，透過使用 Windows Server 叢集。</span><span class="sxs-lookup"><span data-stu-id="42b01-107">The set of databases hosted in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] can be made highly available through the use of a Windows Server cluster.</span></span> <span data-ttu-id="42b01-108">在 BizTalk 環境中，執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供執行的電腦上的 [執行階段環境] 及資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供環境的持續性存放區。</span><span class="sxs-lookup"><span data-stu-id="42b01-108">In a BizTalk environment, the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provide the “run-time environment” and the databases on the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provide the persistent store for the environment.</span></span> <span data-ttu-id="42b01-109">因此，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]備份、 還原和災害復原程序有很大將焦點放在[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42b01-109">Therefore, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] backup, restore, and disaster recovery procedures are heavily focused on [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="42b01-110">目的</span><span class="sxs-lookup"><span data-stu-id="42b01-110">Purpose</span></span>  
 <span data-ttu-id="42b01-111">本主題彙總[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]嚴重損壞修復資訊的核心文件、 各種 Microsoft 網站，而且從資訊從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]定義嚴重損壞修復程序的產品小組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="42b01-111">This topic consolidates [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] disaster recovery information from the core documentation, various Microsoft Web sites, and information from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product team to define disaster recovery procedures for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environments.</span></span>  
  
 <span data-ttu-id="42b01-112">應用程式小組應徹底測試備份、 還原和災害復原程序。</span><span class="sxs-lookup"><span data-stu-id="42b01-112">Application teams should thoroughly test backup, restore, and disaster recovery procedures.</span></span> <span data-ttu-id="42b01-113">您也應該確定程序會調整以符合再進入實際執行的應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="42b01-113">You should also ensure the procedures are tailored to meet application requirements before entering production.</span></span>  
  
## <a name="scope"></a><span data-ttu-id="42b01-114">範圍。</span><span class="sxs-lookup"><span data-stu-id="42b01-114">Scope</span></span>  
 <span data-ttu-id="42b01-115">本節著重於嚴重損壞修復程序[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]和相關的程序[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42b01-115">This section focuses on disaster recovery procedures for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and related procedures for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="42b01-116">本指南是根據有關如何備份和還原 BizTalk Server 的相關文件。</span><span class="sxs-lookup"><span data-stu-id="42b01-116">This guide builds on related documentation about how to back up and restore BizTalk Server.</span></span>  
  
 <span data-ttu-id="42b01-117">如需有關備份和還原的詳細資訊，請參閱這份文件，請參閱[備份和還原 BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154071) (http://go.microsoft.com/fwlink/?LinkID=154071) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="42b01-117">For more information about backup and restore, see this documentation and see [Backing Up and Restoring BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154071) (http://go.microsoft.com/fwlink/?LinkID=154071) in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span> <span data-ttu-id="42b01-118">每個應用程式的小組必須擴充文件的電腦名稱、 磁碟機代號，例如其環境特有的其他程序與本主題中的資訊和相關的叢集設定，以及嚴重損壞修復程序這些方案的一部分的非 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="42b01-118">Each application team must augment the information in this topic with additional procedures specific to their environment, such as document computer names, drive letters, and cluster configuration, as well as disaster recovery procedures for related non-BizTalk applications that are part of the solution.</span></span>  
  
 <span data-ttu-id="42b01-119">本主題不提供詳細的嚴重損壞修復程序的下列區域：</span><span class="sxs-lookup"><span data-stu-id="42b01-119">This topic does not provide detailed disaster recovery procedures for the following areas:</span></span>  
  
-   <span data-ttu-id="42b01-120">非 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="42b01-120">Non-BizTalk applications</span></span>  
  
-   <span data-ttu-id="42b01-121">應用程式的原始程式碼</span><span class="sxs-lookup"><span data-stu-id="42b01-121">Application source code</span></span>  
  
-   <span data-ttu-id="42b01-122">憑證</span><span class="sxs-lookup"><span data-stu-id="42b01-122">Certificates</span></span>  
  
-   <span data-ttu-id="42b01-123">應用程式作業</span><span class="sxs-lookup"><span data-stu-id="42b01-123">Application operations</span></span>  
  
 <span data-ttu-id="42b01-124">可能有需要，以上未列出的應用程式的災害復原方案中的文件必須處理的每個應用程式小組的其他區域。</span><span class="sxs-lookup"><span data-stu-id="42b01-124">There may be additional areas that require documentation in an application’s disaster recovery plan not listed above that must be addressed by each application team.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42b01-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="42b01-125">In This Section</span></span>  
  
-   [<span data-ttu-id="42b01-126">災害復原的最佳作法</span><span class="sxs-lookup"><span data-stu-id="42b01-126">Best Practices for Disaster Recovery</span></span>](../technical-guides/best-practices-for-disaster-recovery.md)  
  
-   [<span data-ttu-id="42b01-127">什麼是 BizTalk Server 記錄傳送？</span><span class="sxs-lookup"><span data-stu-id="42b01-127">What Is BizTalk Server Log Shipping?</span></span>](../technical-guides/what-is-biztalk-server-log-shipping.md)