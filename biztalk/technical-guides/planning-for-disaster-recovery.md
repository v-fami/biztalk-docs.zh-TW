---
title: 規劃災害復原 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a33e8875-cfde-4a60-9dab-fc6bb3ac4f1c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43f90723634a7192d6b8908a37f5d62fa2476997
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006119"
---
# <a name="planning-for-disaster-recovery"></a><span data-ttu-id="e197c-102">規劃損毀復原</span><span class="sxs-lookup"><span data-stu-id="e197c-102">Planning for Disaster Recovery</span></span>
<span data-ttu-id="e197c-103">本主題提供災害復原需求的應用程式小組和 BizTalk server 的程序的指導方針。</span><span class="sxs-lookup"><span data-stu-id="e197c-103">This topic provides guidance to application teams for disaster recovery requirements and procedures for BizTalk Server.</span></span> <span data-ttu-id="e197c-104">Microsoft BizTalk Server 會儲存在組態和處理資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e197c-104">Microsoft BizTalk Server stores configuration and processing information in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="e197c-105">BizTalk Server 高可用性和災害復原可透過高可用性和災害復原功能的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e197c-105">BizTalk Server high availability and disaster recovery is achieved through the high availability and disaster recovery capabilities of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e197c-106">BizTalk 群組由一組資料庫裝載於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e197c-106">A BizTalk group is defined by a set of databases hosted in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="e197c-107">一組資料庫裝載於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可以成為高可用性使用 Windows Server 叢集。</span><span class="sxs-lookup"><span data-stu-id="e197c-107">The set of databases hosted in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] can be made highly available through the use of a Windows Server cluster.</span></span> <span data-ttu-id="e197c-108">在 BizTalk 環境中，執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供執行的電腦上的 「 執行階段環境 」 和資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供環境的持續性存放區。</span><span class="sxs-lookup"><span data-stu-id="e197c-108">In a BizTalk environment, the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provide the “run-time environment” and the databases on the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provide the persistent store for the environment.</span></span> <span data-ttu-id="e197c-109">因此，BizTalk Server 備份、 還原及災害復原的程序大量著重於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e197c-109">Therefore, BizTalk Server backup, restore, and disaster recovery procedures are heavily focused on [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="e197c-110">目的</span><span class="sxs-lookup"><span data-stu-id="e197c-110">Purpose</span></span>  
 <span data-ttu-id="e197c-111">本主題彙總[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]災害復原的資訊的核心文件、 各大 Microsoft 網站和來自[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]定義的嚴重損壞修復程序的產品小組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="e197c-111">This topic consolidates [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] disaster recovery information from the core documentation, various Microsoft Web sites, and information from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product team to define disaster recovery procedures for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environments.</span></span>  
  
 <span data-ttu-id="e197c-112">應用程式小組應該徹底測試備份、 還原及災害復原程序。</span><span class="sxs-lookup"><span data-stu-id="e197c-112">Application teams should thoroughly test backup, restore, and disaster recovery procedures.</span></span> <span data-ttu-id="e197c-113">您也應該確定程序需求量身訂做應用程式需求後，再進入生產環境。</span><span class="sxs-lookup"><span data-stu-id="e197c-113">You should also ensure the procedures are tailored to meet application requirements before entering production.</span></span>  
  
## <a name="scope"></a><span data-ttu-id="e197c-114">範圍。</span><span class="sxs-lookup"><span data-stu-id="e197c-114">Scope</span></span>  
 <span data-ttu-id="e197c-115">本節著重於災害復原程序適用於 BizTalk Server 和相關的程序[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e197c-115">This section focuses on disaster recovery procedures for BizTalk Server and related procedures for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="e197c-116">本指南是根據有關如何備份和還原 BizTalk Server 的相關文件。</span><span class="sxs-lookup"><span data-stu-id="e197c-116">This guide builds on related documentation about how to back up and restore BizTalk Server.</span></span>  
  
 <span data-ttu-id="e197c-117">如需有關備份和還原的詳細資訊，請參閱這份文件，並查看[備份和還原 BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154071) (http://go.microsoft.com/fwlink/?LinkID=154071)在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="e197c-117">For more information about backup and restore, see this documentation and see [Backing Up and Restoring BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154071) (http://go.microsoft.com/fwlink/?LinkID=154071) in BizTalk Server Help.</span></span> <span data-ttu-id="e197c-118">每個應用程式小組必須加強環境，例如文件的電腦名稱、 磁碟機代號，特定的其他程序與本主題中的資訊和相關的叢集組態中，以及嚴重損壞修復程序為解決方案一部分的非 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e197c-118">Each application team must augment the information in this topic with additional procedures specific to their environment, such as document computer names, drive letters, and cluster configuration, as well as disaster recovery procedures for related non-BizTalk applications that are part of the solution.</span></span>  
  
 <span data-ttu-id="e197c-119">本主題不提供詳細的嚴重損壞修復程序的下列區域：</span><span class="sxs-lookup"><span data-stu-id="e197c-119">This topic does not provide detailed disaster recovery procedures for the following areas:</span></span>  
  
- <span data-ttu-id="e197c-120">非 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="e197c-120">Non-BizTalk applications</span></span>  
  
- <span data-ttu-id="e197c-121">應用程式來源程式碼</span><span class="sxs-lookup"><span data-stu-id="e197c-121">Application source code</span></span>  
  
- <span data-ttu-id="e197c-122">憑證</span><span class="sxs-lookup"><span data-stu-id="e197c-122">Certificates</span></span>  
  
- <span data-ttu-id="e197c-123">應用程式作業</span><span class="sxs-lookup"><span data-stu-id="e197c-123">Application operations</span></span>  
  
  <span data-ttu-id="e197c-124">可能需要在其上方未列出的應用程式的災害復原計劃中的文件必須解決每個應用程式小組的其他區域。</span><span class="sxs-lookup"><span data-stu-id="e197c-124">There may be additional areas that require documentation in an application’s disaster recovery plan not listed above that must be addressed by each application team.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e197c-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="e197c-125">In This Section</span></span>  
  
-   [<span data-ttu-id="e197c-126">災害復原的最佳做法</span><span class="sxs-lookup"><span data-stu-id="e197c-126">Best Practices for Disaster Recovery</span></span>](../technical-guides/best-practices-for-disaster-recovery.md)  
  
-   [<span data-ttu-id="e197c-127">什麼是 BizTalk Server 記錄傳送？</span><span class="sxs-lookup"><span data-stu-id="e197c-127">What Is BizTalk Server Log Shipping?</span></span>](../technical-guides/what-is-biztalk-server-log-shipping.md)