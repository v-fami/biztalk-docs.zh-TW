---
title: 如何備份自訂資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom databases
- customizing, custom databases
- backing up, custom databases
ms.assetid: 86bebf3c-968e-4fad-9dab-ced1b04aaac7
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2993de90de3f7b768cc5368012d1f27f8940a99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247334"
---
# <a name="how-to-back-up-custom-databases"></a><span data-ttu-id="76d46-102">如何備份自訂資料庫</span><span class="sxs-lookup"><span data-stu-id="76d46-102">How to Back Up Custom Databases</span></span>
<span data-ttu-id="76d46-103">由於自訂資料庫不會隨 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一起安裝，因此沒有包括在可供「備份 BizTalk Server」作業標示及備份的預設資料庫清單中。</span><span class="sxs-lookup"><span data-stu-id="76d46-103">Because your custom databases are not installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], they are not included in the default list of databases to be marked and backed up by the Backup BizTalk Server job.</span></span> <span data-ttu-id="76d46-104">如果要讓「備份 BizTalk Server」工作備份自訂資料庫，您必須手動將該資料庫加入「備份 BizTalk Server」工作。</span><span class="sxs-lookup"><span data-stu-id="76d46-104">If you want the Backup BizTalk Server job to back up your custom databases, you must manually add the databases to the Backup BizTalk Server job.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="76d46-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="76d46-105">Prerequisites</span></span>  
  
1.  <span data-ttu-id="76d46-106">SQL Server 必須設定為使用完整復原模式，以確保資料完整性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份集。</span><span class="sxs-lookup"><span data-stu-id="76d46-106">SQL Server must be configured to use the full recovery model to ensure the integrity of data in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backup sets.</span></span>  <span data-ttu-id="76d46-107">如需詳細資訊，請參閱[記錄傳送](../core/log-shipping.md)。</span><span class="sxs-lookup"><span data-stu-id="76d46-107">For more information see [Log Shipping](../core/log-shipping.md).</span></span>  
  
2.  <span data-ttu-id="76d46-108">若要備份自訂資料庫，您必須透過有權存取待備份之各個資料庫的使用者帳戶進行登入。</span><span class="sxs-lookup"><span data-stu-id="76d46-108">To back up your custom databases, you must be logged on with a user account that has access to each of the databases you are backing up.</span></span>  
  
     <span data-ttu-id="76d46-109">BizTalk Server 包含名為 BTS_BACKUP_USERS 的 SQL Server 角色；如此一來，除非是在控制備份程序的主要伺服器中，否則您用來備份資料庫的使用者帳戶並不需要 SQL Server 中的「系統管理員」權限。</span><span class="sxs-lookup"><span data-stu-id="76d46-109">BizTalk Server includes a SQL Server role named BTS_BACKUP_USERS so that the user account you use to back up your databases does not require System Administrator permissions within SQL Server, except for the primary server controlling the backup process.</span></span>  
  
     <span data-ttu-id="76d46-110">設定用來備份資料庫的使用者帳戶時，要注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="76d46-110">When setting up the user account that you are using to back up your databases, note the following:</span></span>  
  
    -   <span data-ttu-id="76d46-111">您必須為此使用者建立 SQL Server 登入帳戶，並且在每部伺服器上將該使用者指派給 BizTalk BTS_BACKUP_USERS 角色。</span><span class="sxs-lookup"><span data-stu-id="76d46-111">You must create a SQL Server logon account for this user, and assign this user to the BizTalk BTS_BACKUP_USERS role on each server.</span></span>  
  
    -   <span data-ttu-id="76d46-112">BizTalk Server 的備份工作可以設定為在不同的 SQL Server Agent 服務所使用的使用者帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="76d46-112">The BizTalk Server backup jobs can be configured to run under a user account that is different than the one used for the SQL Server Agent service.</span></span>  
  
    -   <span data-ttu-id="76d46-113">您必須設定 SQL Server 代理程式服務，才能以網域帳戶來執行。</span><span class="sxs-lookup"><span data-stu-id="76d46-113">You must configure the SQL Server Agent service to run under a domain account.</span></span> <span data-ttu-id="76d46-114">如果所有資料庫都在同一台電腦，您可以設定 SQL Server 代理程式使用本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="76d46-114">If all databases are on the same computer, you can configure SQL Server Agent to use a local account.</span></span>  
  
### <a name="to-back-up-custom-databases"></a><span data-ttu-id="76d46-115">備份自訂資料庫</span><span class="sxs-lookup"><span data-stu-id="76d46-115">To back up custom databases</span></span>  
  
1.  <span data-ttu-id="76d46-116">在新資料庫中建置物件：</span><span class="sxs-lookup"><span data-stu-id="76d46-116">Build the objects in the new database:</span></span>  
  
    -   <span data-ttu-id="76d46-117">瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]結構描述目錄，並針對所有想要備份您自訂資料庫執行 Backup_Setup_All_Procs.sql 和 Backup_Setup_All_Tables.sql。</span><span class="sxs-lookup"><span data-stu-id="76d46-117">Browse to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema directory, and then run Backup_Setup_All_Procs.sql and Backup_Setup_All_Tables.sql against all your custom databases that you want to back up.</span></span> <span data-ttu-id="76d46-118">這會建立必要的程序、資料表和角色，並將權限指派給預存程序。</span><span class="sxs-lookup"><span data-stu-id="76d46-118">This creates the necessary procedures, table, and role and assigns permissions to the stored procedures.</span></span>  
  
2.  <span data-ttu-id="76d46-119">執行下列組態：</span><span class="sxs-lookup"><span data-stu-id="76d46-119">Perform the following configurations:</span></span>  
  
    -   <span data-ttu-id="76d46-120">將裝載 BizTalk 管理資料庫的 SQL Server 連結至裝載新資料庫的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="76d46-120">Link the SQL server that is hosting the BizTalk Management database to the SQL server hosting the new database.</span></span> <span data-ttu-id="76d46-121">在管理 SQL Server 上用來執行 SQL Server 代理程式服務的帳戶必須是對應到每一台儲存待備份資料庫之電腦的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="76d46-121">The account used to run the SQL Server Agent service on the management SQL Server must be a domain account that is mapped to each computer holding a database to be backed up.</span></span> <span data-ttu-id="76d46-122">如果資料庫是在同一台電腦上，您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="76d46-122">If the databases are on the same computer you can skip this step.</span></span> <span data-ttu-id="76d46-123">步驟會自動完成。</span><span class="sxs-lookup"><span data-stu-id="76d46-123">This is done automatically.</span></span>  
  
    -   <span data-ttu-id="76d46-124">為在管理 SQL Server 上執行 SQL Server 代理程式服務的帳戶在裝載新資料庫的 SQL Server 中新增登入。</span><span class="sxs-lookup"><span data-stu-id="76d46-124">Add a login on the SQL server hosting the new database for the account running the SQL Server Agent service on the Mgmt SQL Server.</span></span> <span data-ttu-id="76d46-125">如果資料庫是在同一台電腦上，您可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="76d46-125">If the databases are on the same computer you can skip this step.</span></span>  
  
    -   <span data-ttu-id="76d46-126">在新資料庫中為上一個步驟建立的登入新增使用者，並將他們新增至 BTS_BACKUP_USERS 角色。</span><span class="sxs-lookup"><span data-stu-id="76d46-126">Add a user in the new database for the login created in the previous step and add them to the BTS_BACKUP_USERS role.</span></span> <span data-ttu-id="76d46-127">這個角色是由步驟 1 的指令碼建立並授與必要程序的「執行」權限。</span><span class="sxs-lookup"><span data-stu-id="76d46-127">This role is created and granted Execute permissions on the necessary procedures by the scripts in step 1.</span></span>  
  
3.  <span data-ttu-id="76d46-128">在 BizTalk 管理 (BizTalkMgmtDb) 資料庫中，使用 SQL Server Enterprise Manager 或 SQL Server Management Studio，來修改**adm_OtherBackupDatabases**包含自訂資料庫的每個資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="76d46-128">Using SQL Server Enterprise Manager or SQL Server Management Studio, in the BizTalk Management (BizTalkMgmtDb) database, modify the **adm_OtherBackupDatabases** table to include a row for each of your custom databases.</span></span>  
  
4.  <span data-ttu-id="76d46-129">請在對應欄位中輸入新的伺服器及資料庫名稱，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="76d46-129">Type the new server and database names in the corresponding columns, as shown in the following table.</span></span>  
  
    |<span data-ttu-id="76d46-130">資料行</span><span class="sxs-lookup"><span data-stu-id="76d46-130">Column</span></span>|<span data-ttu-id="76d46-131">值</span><span class="sxs-lookup"><span data-stu-id="76d46-131">Value</span></span>|  
    |------------|-----------|  
    |<span data-ttu-id="76d46-132">DefaultDatabaseName</span><span class="sxs-lookup"><span data-stu-id="76d46-132">DefaultDatabaseName</span></span>|<span data-ttu-id="76d46-133">自訂資料庫的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="76d46-133">The friendly name of your custom database.</span></span>|  
    |<span data-ttu-id="76d46-134">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="76d46-134">DatabaseName</span></span>|<span data-ttu-id="76d46-135">自訂資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="76d46-135">The name of your custom database.</span></span>|  
    |<span data-ttu-id="76d46-136">ServerName</span><span class="sxs-lookup"><span data-stu-id="76d46-136">ServerName</span></span>|<span data-ttu-id="76d46-137">執行 SQL Server 的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="76d46-137">The name of the computer running SQL Server.</span></span>|  
    |<span data-ttu-id="76d46-138">BTSServerName</span><span class="sxs-lookup"><span data-stu-id="76d46-138">BTSServerName</span></span>|<span data-ttu-id="76d46-139">BizTalk Server 的名稱。</span><span class="sxs-lookup"><span data-stu-id="76d46-139">The name of the BizTalk Server.</span></span> <span data-ttu-id="76d46-140">雖然用不到這個值，但還是必須含有一個值。</span><span class="sxs-lookup"><span data-stu-id="76d46-140">This value is not used, but it must contain a value nonetheless.</span></span>|  
  
 <span data-ttu-id="76d46-141">下次執行「備份 BizTalk Server」工作時，此工作便會備份自訂資料庫。</span><span class="sxs-lookup"><span data-stu-id="76d46-141">The next time you run the Backup BizTalk Server job, it will back up your custom databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d46-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76d46-142">See Also</span></span>  
 <span data-ttu-id="76d46-143">[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="76d46-143">[Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md) </span></span>  
 [<span data-ttu-id="76d46-144">備份和還原的相關進階的資訊</span><span class="sxs-lookup"><span data-stu-id="76d46-144">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)