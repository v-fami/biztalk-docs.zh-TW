---
title: "管理 BAM 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], databases
- databases [BAM], managing
- databases, BAM
ms.assetid: ce3c472e-2da1-4d67-816a-befe4ded20d9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dbe8cdb2c7806ab62b67db80c4741d64560fba9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-bam-databases"></a><span data-ttu-id="36467-102">管理 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-102">Managing BAM Databases</span></span>
<span data-ttu-id="36467-103">系統管理員會使用 BAM 管理公用程式 (bm.exe) 安裝、管理和更新 BAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="36467-103">Administrators use the BAM Management utility (bm.exe) to set up, manage, and update the BAM databases.</span></span> <span data-ttu-id="36467-104">本節將說明如何使用 BAM 管理公用程式，執行下表所述的一般 BAM 資料庫系統管理員工作。</span><span class="sxs-lookup"><span data-stu-id="36467-104">This section shows you how to use the BAM Management utility to perform these common administrator tasks for the BAM databases, which are described in the following table.</span></span>  
  
 <span data-ttu-id="36467-105">如需備份和還原 BAM 資料庫的資訊，請參閱[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="36467-105">For information about backing up and restoring the BAM databases, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
|<span data-ttu-id="36467-106">資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-106">Database</span></span>|<span data-ttu-id="36467-107">預設資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="36467-107">Default database name</span></span>|<span data-ttu-id="36467-108">Description</span><span class="sxs-lookup"><span data-stu-id="36467-108">Description</span></span>|  
|--------------|---------------------------|-----------------|  
|<span data-ttu-id="36467-109">BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-109">BAM Primary Import database</span></span>|<span data-ttu-id="36467-110">BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="36467-110">BAMPrimaryImport</span></span>|<span data-ttu-id="36467-111">BAM 會在其中收集原始追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="36467-111">Where BAM collects raw tracking data.</span></span>|  
|<span data-ttu-id="36467-112">BAM Notification Services 應用程式資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-112">BAM Notification Services Application database</span></span>|<span data-ttu-id="36467-113">BAMAlertsApplication</span><span class="sxs-lookup"><span data-stu-id="36467-113">BAMAlertsApplication</span></span>|<span data-ttu-id="36467-114">包含 BAM 通知的警示資訊。</span><span class="sxs-lookup"><span data-stu-id="36467-114">Contains alert information for BAM notifications.</span></span> <span data-ttu-id="36467-115">例如，當您使用 BAM 入口網站建立警示時，就會在資料庫中插入項目以指定與警示相關的條件和事件，以及警示的其他支援資料項目。</span><span class="sxs-lookup"><span data-stu-id="36467-115">For example, when you create an alert using the BAM portal, entries are inserted in the database specifying the conditions and events to which the alert pertains, as well as other supporting data items for the alert.</span></span>|  
|<span data-ttu-id="36467-116">BAM Notification Services 執行個體資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-116">BAM Notification Services Instance database</span></span>|<span data-ttu-id="36467-117">BAMAlertsNSMain</span><span class="sxs-lookup"><span data-stu-id="36467-117">BAMAlertsNSMain</span></span>|<span data-ttu-id="36467-118">包含指定通知服務如何連接至 BAM 所監控系統的執行個體資訊。</span><span class="sxs-lookup"><span data-stu-id="36467-118">Contains instance information specifying how the notification services connect to the system that BAM is monitoring.</span></span>|  
|<span data-ttu-id="36467-119">BAM 星狀結構描述資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-119">BAM Star Schema database</span></span>|<span data-ttu-id="36467-120">BAMStarSchema</span><span class="sxs-lookup"><span data-stu-id="36467-120">BAMStarSchema</span></span>|<span data-ttu-id="36467-121">包含臨時資料表以及量值和維度資料表。</span><span class="sxs-lookup"><span data-stu-id="36467-121">Contains the staging table, and the measure and dimension tables.</span></span>|  
|<span data-ttu-id="36467-122">BAM 分析資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-122">BAM Analysis database</span></span>|<span data-ttu-id="36467-123">BAMAnalysis</span><span class="sxs-lookup"><span data-stu-id="36467-123">BAMAnalysis</span></span>|<span data-ttu-id="36467-124">含有可供線上及離線分析使用的 BAM OLAP Cube。</span><span class="sxs-lookup"><span data-stu-id="36467-124">Contains BAM OLAP cubes for both online and offline analysis.</span></span>|  
|<span data-ttu-id="36467-125">BAM 封存資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-125">BAM Archive database</span></span>|<span data-ttu-id="36467-126">BAMArchive</span><span class="sxs-lookup"><span data-stu-id="36467-126">BAMArchive</span></span>|<span data-ttu-id="36467-127">封存舊的商務活動資料。</span><span class="sxs-lookup"><span data-stu-id="36467-127">Archives old business activity data.</span></span> <span data-ttu-id="36467-128">您可以建立 BAM 封存資料庫，將 BAM 主要匯入資料庫中商務活動資料的累積量降到最低。</span><span class="sxs-lookup"><span data-stu-id="36467-128">You can create a BAM Archive database to minimize the accumulation of business activity data in the BAM Primary Import database.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="36467-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="36467-129">In This Section</span></span>  
  
-   [<span data-ttu-id="36467-130">封存主要匯入資料庫資料</span><span class="sxs-lookup"><span data-stu-id="36467-130">Archiving Primary Import Database Data</span></span>](../core/archiving-primary-import-database-data.md)  
  
-   [<span data-ttu-id="36467-131">在封存資料庫中建立資料分割的檢視</span><span class="sxs-lookup"><span data-stu-id="36467-131">Creating a Partitioned View in the Archiving Database</span></span>](../core/creating-a-partitioned-view-in-the-archiving-database.md)  
  
-   [<span data-ttu-id="36467-132">排程 SQL Server Integration Services 封裝</span><span class="sxs-lookup"><span data-stu-id="36467-132">Scheduling SQL Server Integration Services Packages</span></span>](../core/scheduling-sql-server-integration-services-packages.md)  
  
-   [<span data-ttu-id="36467-133">如何設定 BAM 資料庫使用 BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="36467-133">How to Set Up the BAM Databases Using the BAM Management Utility</span></span>](../core/how-to-set-up-the-bam-databases-using-the-bam-management-utility.md)  
  
-   [<span data-ttu-id="36467-134">如何擷取 BAM 組態檔使用 BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="36467-134">How to Retrieve the BAM Configuration File Using the BAM Management Utility</span></span>](../core/how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility.md)  
  
-   [<span data-ttu-id="36467-135">如何更新 BAM 組態使用 BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="36467-135">How to Update the BAM Configuration Using the BAM Management Utility</span></span>](../core/how-to-update-the-bam-configuration-using-the-bam-management-utility.md)  
  
-   [<span data-ttu-id="36467-136">如何參考其他 BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-136">How to Reference Additional BAM Primary Import Databases</span></span>](../core/how-to-reference-additional-bam-primary-import-databases.md)  
  
-   [<span data-ttu-id="36467-137">如何停用 BAM 主要匯入資料庫參考</span><span class="sxs-lookup"><span data-stu-id="36467-137">How to Disable a BAM Primary Import Database Reference</span></span>](../core/how-to-disable-a-bam-primary-import-database-reference.md)  
  
-   [<span data-ttu-id="36467-138">如何列出所有被參考資料庫</span><span class="sxs-lookup"><span data-stu-id="36467-138">How to List All Referenced Databases</span></span>](../core/how-to-list-all-referenced-databases.md)  
  
-   [<span data-ttu-id="36467-139">如何移除未完成的活動執行個體</span><span class="sxs-lookup"><span data-stu-id="36467-139">How to Remove Incomplete Activity Instances</span></span>](../core/how-to-remove-incomplete-activity-instances.md)  
  
-   [<span data-ttu-id="36467-140">如何更新 BAM 管理公用程式組態之後備份與還原</span><span class="sxs-lookup"><span data-stu-id="36467-140">How to Update the BAM Management Utility Configuration After a Backup and Restore</span></span>](../core/update-the-bam-management-utility-configuration-after-a-backup-and-restore.md)  
  
-   [<span data-ttu-id="36467-141">如何整合 BAM 與 SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="36467-141">How to Integrate BAM with SQL Server Reporting Services</span></span>](../core/how-to-integrate-bam-with-sql-server-reporting-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="36467-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36467-142">See Also</span></span>  
 [<span data-ttu-id="36467-143">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="36467-143">Managing BAM</span></span>](../core/managing-bam.md)