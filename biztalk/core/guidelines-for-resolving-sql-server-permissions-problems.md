---
title: "解決 SQL Server 權限問題的指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c24512-5f65-4363-b806-8dd52b22f179
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db02fd2a981d3f1dc34924e680caf5926f67871a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-resolving-sql-server-permissions-problems"></a><span data-ttu-id="25653-102">解決 SQL Server 權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="25653-102">Guidelines for Resolving SQL Server Permissions Problems</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="25653-103"> 會密集使用 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫進行執行階段作業，因此正確設定 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 權限非常重要。</span><span class="sxs-lookup"><span data-stu-id="25653-103"> makes extensive use of Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases for run-time operations and as such, it is important that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permissions are set correctly.</span></span> <span data-ttu-id="25653-104">本主題包含一些一般指導方針，可用來排除大多數的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的權限問題，另外也包含疑難排解步驟，您可以遵循這些步驟，解決對 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 造成影響的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 權限問題。</span><span class="sxs-lookup"><span data-stu-id="25653-104">This topic provides some general guidelines for minimizing [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permissions problems and steps that you can follow to troubleshoot [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permissions problems that affect [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="general-guidelines"></a><span data-ttu-id="25653-105">一般指導方針</span><span class="sxs-lookup"><span data-stu-id="25653-105">General Guidelines</span></span>  
  
-   <span data-ttu-id="25653-106">**使用 BizTalk Server 的多重電腦安裝的網域使用者和群組**</span><span class="sxs-lookup"><span data-stu-id="25653-106">**Use domain users and groups for a multicomputer installation of BizTalk Server**</span></span>  
  
     <span data-ttu-id="25653-107">在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 以執行於多電腦實例時 (例如，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同電腦上)，您必須使用網域使用者群組和帳戶。</span><span class="sxs-lookup"><span data-stu-id="25653-107">You must use domain user groups and accounts when configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to run in a multicomputer scenario, for example, where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on separate computers.</span></span> <span data-ttu-id="25653-108">請勿嘗試設定或執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中*傳遞*藉此避免使用網域群組和帳戶的每一部電腦建立成對的使用者名稱和密碼的驗證案例。</span><span class="sxs-lookup"><span data-stu-id="25653-108">Do not attempt to configure or run [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a *pass-through* authentication scenario whereby matching pairs of usernames and passwords are created on each computer to avoid using domain groups and accounts.</span></span> <span data-ttu-id="25653-109">在有些實例中這種通過實例可能會正常運作，但在其他實例中這會造成 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 失敗，因此是不受支援的組態。</span><span class="sxs-lookup"><span data-stu-id="25653-109">While such a pass-through scenario may appear to function correctly in some scenarios, this will cause [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to fail in other scenarios and is not a supported configuration.</span></span>  
  
     <span data-ttu-id="25653-110">如需有關安裝和設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在多重電腦組態中，下載安裝指南 》，網址[安裝指南相關的 BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582)。</span><span class="sxs-lookup"><span data-stu-id="25653-110">For more information about installing and configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a multicomputer configuration, download the Installation Guide at [Installation Guides Related to BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582).</span></span>  
  
-   <span data-ttu-id="25653-111">**請確定適當的 Windows 使用者和群組已在適當的 SQL Server 角色定義**</span><span class="sxs-lookup"><span data-stu-id="25653-111">**Ensure that the appropriate Windows users and groups are defined in the appropriate SQL Server roles**</span></span>  
  
     <span data-ttu-id="25653-112">請確認正確[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]主題中的資料表所列出的角色成員資格[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="25653-112">Verify correct [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] role membership as listed in the table in the topic [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="25653-113">**使用 SQL Server Profiler 診斷權限問題**</span><span class="sxs-lookup"><span data-stu-id="25653-113">**User SQL Server Profiler to diagnose permissions problems**</span></span>  
  
     <span data-ttu-id="25653-114">設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Profiler 追蹤來監視**稽核登入失敗事件**來收集有關權限失敗的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="25653-114">Set up a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler trace to monitor the **Audit Login Failed Event** to gather detailed information about permissions failures.</span></span> <span data-ttu-id="25653-115">如需有關如何使用資訊[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]程式碼剖析工具，請參閱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="25653-115">For information about how to use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, see the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="25653-116">已知問題</span><span class="sxs-lookup"><span data-stu-id="25653-116">Known Issues</span></span>  
  
#### <a name="the-sql-server-jobs-that-are-installed-with-biztalk-server-fail-to-execute"></a><span data-ttu-id="25653-117">與 BizTalk Server 一起安裝的 SQL Server 作業無法執行</span><span class="sxs-lookup"><span data-stu-id="25653-117">The SQL Server jobs that are installed with BizTalk Server fail to execute</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="25653-118">問題</span><span class="sxs-lookup"><span data-stu-id="25653-118">Problem</span></span>  
 <span data-ttu-id="25653-119">隨 SQL Server 工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]失敗，而且類似下列的錯誤會產生[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]應用程式記錄檔：</span><span class="sxs-lookup"><span data-stu-id="25653-119">The SQL Server jobs that are installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fail and errors similar to the following are generated in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Application log:</span></span>  
  
 <span data-ttu-id="25653-120">事件類型: 警告</span><span class="sxs-lookup"><span data-stu-id="25653-120">Event Type: Warning</span></span>  
  
 <span data-ttu-id="25653-121">事件來源: SQLSERVERAGENT</span><span class="sxs-lookup"><span data-stu-id="25653-121">Event Source: SQLSERVERAGENT</span></span>  
  
 <span data-ttu-id="25653-122">事件類別目錄: 工作引擎</span><span class="sxs-lookup"><span data-stu-id="25653-122">Event Category: Job Engine</span></span>  
  
 <span data-ttu-id="25653-123">事件識別碼: 208</span><span class="sxs-lookup"><span data-stu-id="25653-123">Event ID: 208</span></span>  
  
 <span data-ttu-id="25653-124">日期: 6/29/2008</span><span class="sxs-lookup"><span data-stu-id="25653-124">Date: 6/29/2008</span></span>  
  
 <span data-ttu-id="25653-125">時間: 4:45:01 PM</span><span class="sxs-lookup"><span data-stu-id="25653-125">Time: 4:45:01 PM</span></span>  
  
 <span data-ttu-id="25653-126">使用者: N/A</span><span class="sxs-lookup"><span data-stu-id="25653-126">User: N/A</span></span>  
  
 <span data-ttu-id="25653-127">電腦： *SQLServer*</span><span class="sxs-lookup"><span data-stu-id="25653-127">Computer: *SQLServer*</span></span>  
  
 <span data-ttu-id="25653-128">描述：</span><span class="sxs-lookup"><span data-stu-id="25653-128">Description:</span></span>  
  
 <span data-ttu-id="25653-129">SQL Server 排程作業 '備份 BizTalk Server'</span><span class="sxs-lookup"><span data-stu-id="25653-129">SQL Server Scheduled Job 'Backup BizTalk Server'</span></span>  
  
 <span data-ttu-id="25653-130">(0x4AC7C44A48541443927A56C5C6699ECF)-狀態： 失敗-在上叫用： 2008年-6-29 13:45:01-訊息： 工作失敗。</span><span class="sxs-lookup"><span data-stu-id="25653-130">(0x4AC7C44A48541443927A56C5C6699ECF) - Status: Failed - Invoked on: 2008-6-29 13:45:01 - Message: The job failed.</span></span>  <span data-ttu-id="25653-131">工作由排程 305 (MarkAndBackupLogSched) 叫用。</span><span class="sxs-lookup"><span data-stu-id="25653-131">The Job was invoked by Schedule 305 (MarkAndBackupLogSched).</span></span> <span data-ttu-id="25653-132">要執行的最後一個步驟是步驟 1 (BackupFull)。</span><span class="sxs-lookup"><span data-stu-id="25653-132">The last step to run was step 1 (BackupFull).</span></span>  
  
 <span data-ttu-id="25653-133">**-和-**</span><span class="sxs-lookup"><span data-stu-id="25653-133">**- and -**</span></span>  
  
 <span data-ttu-id="25653-134">事件類型： 資訊</span><span class="sxs-lookup"><span data-stu-id="25653-134">Event Type: Information</span></span>  
  
 <span data-ttu-id="25653-135">事件來源: MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="25653-135">Event Source: MSSQLSERVER</span></span>  
  
 <span data-ttu-id="25653-136">事件類別目錄: (4)</span><span class="sxs-lookup"><span data-stu-id="25653-136">Event Category: (4)</span></span>  
  
 <span data-ttu-id="25653-137">事件識別碼： 17055</span><span class="sxs-lookup"><span data-stu-id="25653-137">Event ID: 17055</span></span>  
  
 <span data-ttu-id="25653-138">日期: 6/29/2008</span><span class="sxs-lookup"><span data-stu-id="25653-138">Date: 6/29/2008</span></span>  
  
 <span data-ttu-id="25653-139">時間: 4:45:01 PM</span><span class="sxs-lookup"><span data-stu-id="25653-139">Time: 4:45:01 PM</span></span>  
  
 <span data-ttu-id="25653-140">使用者: N/A</span><span class="sxs-lookup"><span data-stu-id="25653-140">User: N/A</span></span>  
  
 <span data-ttu-id="25653-141">電腦： *SQLServer*</span><span class="sxs-lookup"><span data-stu-id="25653-141">Computer: *SQLServer*</span></span>  
  
 <span data-ttu-id="25653-142">描述：</span><span class="sxs-lookup"><span data-stu-id="25653-142">Description:</span></span>  
  
 <span data-ttu-id="25653-143">18456: 使用者 'NT AUTHORITY\SYSTEM' 登入失敗。</span><span class="sxs-lookup"><span data-stu-id="25653-143">18456: Login failed for user 'NT AUTHORITY\SYSTEM'.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="25653-144">原因</span><span class="sxs-lookup"><span data-stu-id="25653-144">Cause</span></span>  
 <span data-ttu-id="25653-145">如果已從 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 刪除 BUILTIN\Administrators 登入，便會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="25653-145">This error can occur if the BUILTIN\Administrators login has been removed from [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="25653-146">如果已刪除 BUILTIN\Administrators 登入，sqlmaint.exe 就無法登入 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，而導致 SQL 工作無法執行。</span><span class="sxs-lookup"><span data-stu-id="25653-146">If the BUILTIN\Administrators login is deleted, sqlmaint.exe will be unable to logon to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] which will prevent SQL jobs from running.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="25653-147">解決方案</span><span class="sxs-lookup"><span data-stu-id="25653-147">Resolution</span></span>  
 <span data-ttu-id="25653-148">若要解決這個錯誤，請重建 BUILTIN\Administrators 登入，並將其加入至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫和 Master 資料庫的 db_owner 角色中。</span><span class="sxs-lookup"><span data-stu-id="25653-148">To resolve this issue, re-create the BUILTIN\Administrators Login and add it to the db_owner role for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and the Master database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25653-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25653-149">See Also</span></span>  
 <span data-ttu-id="25653-150">[疑難排解 SQL Server](../core/troubleshooting-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="25653-150">[Troubleshooting SQL Server](../core/troubleshooting-sql-server.md) </span></span>  
 [<span data-ttu-id="25653-151">疑難排解 BizTalk Server 權限</span><span class="sxs-lookup"><span data-stu-id="25653-151">Troubleshooting BizTalk Server Permissions</span></span>](../core/troubleshooting-biztalk-server-permissions.md)