---
title: "疑難排解 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f6707c5-7c6e-4375-bfa6-9b1a86ec5e81
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66d6d35ac668a324ed28f7c9519b32812e10cb3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-sql-server"></a><span data-ttu-id="a302d-102">疑難排解 SQL Server</span><span class="sxs-lookup"><span data-stu-id="a302d-102">Troubleshooting SQL Server</span></span>
<span data-ttu-id="a302d-103">大多數會影響 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 問題分為下列類別：</span><span class="sxs-lookup"><span data-stu-id="a302d-103">The majority of Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] issues that affect Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fall into one of the following categories:</span></span>  
  
-   <span data-ttu-id="a302d-104">連線相關問題</span><span class="sxs-lookup"><span data-stu-id="a302d-104">Connectivity-related problems</span></span>  
  
-   <span data-ttu-id="a302d-105">權限相關問題</span><span class="sxs-lookup"><span data-stu-id="a302d-105">Permissions-related problems</span></span>  
  
-   <span data-ttu-id="a302d-106">資料庫大小問題</span><span class="sxs-lookup"><span data-stu-id="a302d-106">Database-sizing problems</span></span>  
  
 <span data-ttu-id="a302d-107">本主題說明各個類別，以及您可以用於解決相關問題的步驟。</span><span class="sxs-lookup"><span data-stu-id="a302d-107">This topic discusses each of these categories and steps that you can take to resolve the associated problems.</span></span>  
  
## <a name="connectivity-related-problems"></a><span data-ttu-id="a302d-108">連線相關問題</span><span class="sxs-lookup"><span data-stu-id="a302d-108">Connectivity-Related Problems</span></span>  
 <span data-ttu-id="a302d-109">下列問題最常與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦和裝載 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦之間的連線問題相關聯。</span><span class="sxs-lookup"><span data-stu-id="a302d-109">The following issues are most commonly associated with connectivity problems between the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer that houses the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
#### <a name="errors-related-to-failed-transactions-or-communication-with-the-underlying-transaction-manager-errors-are-written-to-the-biztalk-server-application-log"></a><span data-ttu-id="a302d-110">與失敗交易相關的錯誤或與基礎交易管理員通訊錯誤會記錄在 BizTalk Server 應用程式記錄檔中</span><span class="sxs-lookup"><span data-stu-id="a302d-110">Errors related to failed transactions or "Communication with the underlying transaction manager" errors are written to the BizTalk Server Application log</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="a302d-111">問題</span><span class="sxs-lookup"><span data-stu-id="a302d-111">Problem</span></span>  
 <span data-ttu-id="a302d-112">表示 MSDTC 交易失敗的錯誤或無法與基礎交易管理員通訊的失敗會記錄在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="a302d-112">Errors indicating an MSDTC transaction failure or a failure to communicate with the underlying transaction manager are written to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application log.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="a302d-113">原因</span><span class="sxs-lookup"><span data-stu-id="a302d-113">Cause</span></span>  
 <span data-ttu-id="a302d-114">之間的 MSDTC 連線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]失敗。</span><span class="sxs-lookup"><span data-stu-id="a302d-114">MSDTC connectivity between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]and[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] has failed.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="a302d-115">解決方案</span><span class="sxs-lookup"><span data-stu-id="a302d-115">Resolution</span></span>  
 <span data-ttu-id="a302d-116">如需之間 MSDTC 連線疑難排解[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[疑難排解 MSDTC 問題的](../core/troubleshooting-problems-with-msdtc.md)。</span><span class="sxs-lookup"><span data-stu-id="a302d-116">For information about troubleshooting MSDTC connectivity between the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer that houses the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>  
  
#### <a name="error-a-connection-was-successfully-established-with-the-server-but-then-an-error-occurred-during-the-pre-login-handshake-occurs-when-connecting-to-remote-sql-server-databases-on-sql-server-2008"></a><span data-ttu-id="a302d-117">在連接到 SQL Server 2008 上的遠端 SQL Server 資料庫時發生錯誤，指出成功建立與伺服器的連線，但在登入前交握期間發生錯誤</span><span class="sxs-lookup"><span data-stu-id="a302d-117">Error "A connection was successfully established with the server, but then an error occurred during the pre-login handshake" occurs when connecting to remote SQL Server databases on SQL Server 2008</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="a302d-118">問題</span><span class="sxs-lookup"><span data-stu-id="a302d-118">Problem</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a302d-119"> 失去與裝載 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫之遠端 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的連線，並且產生錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="a302d-119"> loses connectivity with a remote [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer that houses the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and an error message is generated:</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="a302d-120">原因</span><span class="sxs-lookup"><span data-stu-id="a302d-120">Cause</span></span>  
 <span data-ttu-id="a302d-121">如果下列一或多個狀況成立，可能就會發生這個問題：</span><span class="sxs-lookup"><span data-stu-id="a302d-121">This problem may occur if one or more of the following conditions is true:</span></span>  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]<span data-ttu-id="a302d-122"> 未設定為接受遠端連線。</span><span class="sxs-lookup"><span data-stu-id="a302d-122"> is not configured to accept remote connections.</span></span>  
  
-   <span data-ttu-id="a302d-123">[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦或執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 用戶端電腦上未啟用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的必要通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a302d-123">The necessary protocols for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are not enabled on either the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer or the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] client computer that is running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="a302d-124">解決方案</span><span class="sxs-lookup"><span data-stu-id="a302d-124">Resolution</span></span>  
 <span data-ttu-id="a302d-125">請依照下列步驟解決這個問題：</span><span class="sxs-lookup"><span data-stu-id="a302d-125">Follow these steps to resolve this problem:</span></span>  
  
-   <span data-ttu-id="a302d-126">**SQL Server 介面區組態**工具並不適用於 SQL Server 2008。</span><span class="sxs-lookup"><span data-stu-id="a302d-126">The **SQL Server Surface Area Configuration** tool is not available on SQL Server 2008.</span></span> <span data-ttu-id="a302d-127">若要啟用 SQL Server 2008 電腦上的 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 遠端連線，請依照 SQL Server 2008 線上說明中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="a302d-127">To enable remote connections for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] on a SQL Server 2008 computer follow the instructions in the SQL Server 2008 online help.</span></span>  
  
-   <span data-ttu-id="a302d-128">使用**SQL Server 組態管理員**工具，可讓**TCP/IP**及/或**具名管道**通訊協定上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。</span><span class="sxs-lookup"><span data-stu-id="a302d-128">Use the **SQL Server Configuration Manager** tool to enable the **TCP/IP** and/or the **Named Pipes** protocols on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
    1.  <span data-ttu-id="a302d-129">按一下**啟動**，指向 **所有程式**，然後按一下**SQL Server 組態管理員**。</span><span class="sxs-lookup"><span data-stu-id="a302d-129">Click **Start**, point to **All Programs**, and click **SQL Server Configuration Manager**.</span></span>  
  
    2.  <span data-ttu-id="a302d-130">按一下以展開**SQL Server 網路組態**，然後按一下  **MSSQLSERVER 的通訊協定**。</span><span class="sxs-lookup"><span data-stu-id="a302d-130">Click to expand **SQL Server Network Configuration** and then click **Protocols for MSSQLSERVER**.</span></span>  
  
    3.  <span data-ttu-id="a302d-131">以滑鼠右鍵按一下**TCP/IP**通訊協定，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="a302d-131">Right-click the **TCP/IP** protocol and then click **Enable**.</span></span>  
  
    4.  <span data-ttu-id="a302d-132">以滑鼠右鍵按一下**具名管道**通訊協定，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="a302d-132">Right-click the **Named Pipes** protocol and then click **Enable**.</span></span>  
  
    5.  <span data-ttu-id="a302d-133">關閉**SQL Server 組態管理員**工具。</span><span class="sxs-lookup"><span data-stu-id="a302d-133">Close the **SQL Server Configuration Manager** tool.</span></span>  
  
-   <span data-ttu-id="a302d-134">使用**SQL Server 組態管理員**工具，可讓**TCP/IP**及/或**具名管道**通訊協定上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行的用戶端電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a302d-134">Use the **SQL Server Configuration Manager** tool to enable the **TCP/IP** and/or the **Named Pipes** protocols on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] client computer that is running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    1.  <span data-ttu-id="a302d-135">按一下**啟動**，指向 **所有程式**，然後按一下**SQL Server 組態管理員**。</span><span class="sxs-lookup"><span data-stu-id="a302d-135">Click **Start**, point to **All Programs**, and click **SQL Server Configuration Manager**.</span></span>  
  
    2.  <span data-ttu-id="a302d-136">按一下以展開**SQL Server 網路組態**，然後按一下 **儲存的.reg**。</span><span class="sxs-lookup"><span data-stu-id="a302d-136">Click to expand **SQL Server Network Configuration** and then click **ClientProtocols**.</span></span>  
  
    3.  <span data-ttu-id="a302d-137">以滑鼠右鍵按一下**TCP/IP**通訊協定，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="a302d-137">Right-click the **TCP/IP** protocol and then click **Enable**.</span></span>  
  
    4.  <span data-ttu-id="a302d-138">以滑鼠右鍵按一下**具名管道**通訊協定，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="a302d-138">Right-click the **Named Pipes** protocol and then click **Enable**.</span></span>  
  
    5.  <span data-ttu-id="a302d-139">關閉**SQL Server 組態管理員**工具。</span><span class="sxs-lookup"><span data-stu-id="a302d-139">Close the **SQL Server Configuration Manager** tool.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a302d-140">確定執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用戶端電腦至少有一個通訊協定符合 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦上啟用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a302d-140">Ensure that at least one of the protocols on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] client computer that is running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] matches the protocols enabled on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
#### <a name="a-biztalk-host-instance-fails-and-a-general-network-error-is-written-to-the-application-log-when-the-biztalk-server-based-server-processes-a-high-volume-of-documents"></a><span data-ttu-id="a302d-141">BizTalk 主控件執行個體失敗，而且 BizTalk Server 為基礎的伺服器處理大量文件時，「 一般網路 」 錯誤會寫入應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="a302d-141">A BizTalk host instance fails and a "General Network" error is written to the Application log when the BizTalk Server-based server processes a high volume of documents</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="a302d-142">問題</span><span class="sxs-lookup"><span data-stu-id="a302d-142">Problem</span></span>  
 <span data-ttu-id="a302d-143">在處理大量文件時，BizTalk 主控件執行個體將會失敗，並將 「 一般網路 」 錯誤寫入應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a302d-143">When processing a high volume of documents, a BizTalk host instance fails, and a "General Network" error is written to the Application log.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="a302d-144">原因</span><span class="sxs-lookup"><span data-stu-id="a302d-144">Cause</span></span>  
 <span data-ttu-id="a302d-145">會發生此問題是因為 Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 實作的安全性功能會減少伺服器的並行 TCP/IP 連線之佇列大小。</span><span class="sxs-lookup"><span data-stu-id="a302d-145">This issue occurs because Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] implements a security feature that reduces the size of the queue for concurrent TCP/IP connections to the server.</span></span> <span data-ttu-id="a302d-146">此功能可防止阻絕服務的攻擊。</span><span class="sxs-lookup"><span data-stu-id="a302d-146">This feature helps prevent denial of service attacks.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="a302d-147">解決方案</span><span class="sxs-lookup"><span data-stu-id="a302d-147">Resolution</span></span>  
 <span data-ttu-id="a302d-148">如需有關如何解決此問題的詳細資訊，請參閱[避免 DBNETLIB 例外狀況](../core/avoiding-dbnetlib-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="a302d-148">For more information about resolving this issue, see [Avoiding DBNETLIB Exceptions](../core/avoiding-dbnetlib-exceptions.md).</span></span>  
  
## <a name="permissions-related-problems"></a><span data-ttu-id="a302d-149">權限相關問題</span><span class="sxs-lookup"><span data-stu-id="a302d-149">Permissions-Related Problems</span></span>  
  
#### <a name="biztalk-server-run-time-or-design-time-operations-fail-and-a-cannot-open-database-requested-in-login-database-error-is-written-to-the-application-log-of-the-biztalk-server-or-sql-server-computer"></a><span data-ttu-id="a302d-150">BizTalk Server 執行階段或設計階段作業失敗與 「 無法開啟資料庫中登入要求\<資料庫 > 」 錯誤寫入 BizTalk Server 或 SQL Server 電腦的應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="a302d-150">BizTalk Server run-time or design-time operations fail and a "cannot open database requested in login \<database>" error is written to the Application log of the BizTalk Server or SQL Server computer</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="a302d-151">問題</span><span class="sxs-lookup"><span data-stu-id="a302d-151">Problem</span></span>  
 <span data-ttu-id="a302d-152">執行階段或設計階段作業失敗，而且類似如下的錯誤會寫入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 電腦的應用程式記錄檔：</span><span class="sxs-lookup"><span data-stu-id="a302d-152">A run-time or design-time operation fails and an error similar to the following is written to the application log of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer:</span></span>  
  
 <span data-ttu-id="a302d-153">無法開啟資料庫中登入要求\<*資料庫*>。</span><span class="sxs-lookup"><span data-stu-id="a302d-153">Cannot open database requested in login \<*database*>.</span></span> <span data-ttu-id="a302d-154">登入失敗。</span><span class="sxs-lookup"><span data-stu-id="a302d-154">Login fails.</span></span>   
<span data-ttu-id="a302d-155">使用者登入失敗\< *username*>。</span><span class="sxs-lookup"><span data-stu-id="a302d-155">Login failed for user \<*username*>.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="a302d-156">原因</span><span class="sxs-lookup"><span data-stu-id="a302d-156">Cause</span></span>  
 <span data-ttu-id="a302d-157">如果指定的帳戶不屬於適當的 Windows 群組或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 角色，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="a302d-157">This error can occur if the specified account does not belong to the appropriate Windows group or [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] role.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="a302d-158">解決方案</span><span class="sxs-lookup"><span data-stu-id="a302d-158">Resolution</span></span>  
 <span data-ttu-id="a302d-159">確定指定的帳戶是適當 Windows 群組的成員或 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 角色。</span><span class="sxs-lookup"><span data-stu-id="a302d-159">Ensure that the specified account is a member of the appropriate Windows group or [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] role.</span></span> <span data-ttu-id="a302d-160">如需有關適當的成員資格的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a302d-160">For more information about the appropriate memberships, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
## <a name="database-sizing-problems"></a><span data-ttu-id="a302d-161">資料庫大小問題</span><span class="sxs-lookup"><span data-stu-id="a302d-161">Database-Sizing Problems</span></span>  
 <span data-ttu-id="a302d-162">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫不受抑制地成長，這會嚴重影響 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的效能。</span><span class="sxs-lookup"><span data-stu-id="a302d-162">If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases grow unchecked then the performance of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment will be adversely affected.</span></span> <span data-ttu-id="a302d-163">請依照下列步驟來管理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的成長。</span><span class="sxs-lookup"><span data-stu-id="a302d-163">Follow the steps below to manage the growth of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
#### <a name="the-biztalk-server-messagebox-database-is-growing-unchecked-and-impacting-overall-performance"></a><span data-ttu-id="a302d-164">BizTalk Server MessageBox 資料庫不受抑制地成長，因此影響整體效能</span><span class="sxs-lookup"><span data-stu-id="a302d-164">The BizTalk Server MessageBox database is growing unchecked and impacting overall performance</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="a302d-165">問題</span><span class="sxs-lookup"><span data-stu-id="a302d-165">Problem</span></span>  
 <span data-ttu-id="a302d-166">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox 資料庫的成長會嚴重影響 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的效能。</span><span class="sxs-lookup"><span data-stu-id="a302d-166">Growth of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database is adversely affecting performance of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="a302d-167">原因</span><span class="sxs-lookup"><span data-stu-id="a302d-167">Cause</span></span>  
 <span data-ttu-id="a302d-168">如果維護 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的「SQL 代理程式」工作未執行，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="a302d-168">This problem can occur if the SQL Agent jobs that maintain the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are not running.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="a302d-169">解決方案</span><span class="sxs-lookup"><span data-stu-id="a302d-169">Resolution</span></span>  
 <span data-ttu-id="a302d-170">確定維護 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的「SQL 代理程式」工作執行中。</span><span class="sxs-lookup"><span data-stu-id="a302d-170">Ensure that the SQL Agent jobs that maintain the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are running.</span></span> <span data-ttu-id="a302d-171">請參閱[資料庫結構與工作](../core/database-structure-and-jobs.md)如需完整清單，以安裝的 SQL 代理程式作業[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a302d-171">See [Database Structure and Jobs](../core/database-structure-and-jobs.md) for a complete list of the SQL Agent jobs that are installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
#### <a name="the-biztalk-server-tracking-database-is-growing-unchecked-and-impacting-overall-performance"></a><span data-ttu-id="a302d-172">BizTalk Server 追蹤資料庫不受抑制地成長，因此影響整體效能</span><span class="sxs-lookup"><span data-stu-id="a302d-172">The BizTalk Server tracking database is growing unchecked and impacting overall performance</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="a302d-173">問題</span><span class="sxs-lookup"><span data-stu-id="a302d-173">Problem</span></span>  
 <span data-ttu-id="a302d-174">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤資料庫不受抑制地成長，而且嚴重影響 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的整體效能。</span><span class="sxs-lookup"><span data-stu-id="a302d-174">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tracking database is growing unchecked and is adversely affecting the overall performance of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="a302d-175">原因</span><span class="sxs-lookup"><span data-stu-id="a302d-175">Cause</span></span>  
 <span data-ttu-id="a302d-176">如果未執行步驟來清除和封存 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤資料庫，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="a302d-176">This problem can occur if steps are not taken to purge and archive the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tracking database.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="a302d-177">解決方案</span><span class="sxs-lookup"><span data-stu-id="a302d-177">Resolution</span></span>  
 <span data-ttu-id="a302d-178">應該執行步驟來清除和封存 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="a302d-178">Steps should be taken to purge and archive the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tracking database.</span></span> <span data-ttu-id="a302d-179">請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a302d-179">See [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a302d-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a302d-180">See Also</span></span>  
 [<span data-ttu-id="a302d-181">解決 SQL Server 權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="a302d-181">Guidelines for Resolving SQL Server Permissions Problems</span></span>](../core/guidelines-for-resolving-sql-server-permissions-problems.md)