---
title: "BizTalk Server 管理疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dfb56b0-352f-4012-b030-087bbcfe09d4
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 573e7a2509741748b0f95837f310e2e651b255c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshooting-biztalk-server-administration"></a><span data-ttu-id="23861-102">BizTalk Server 管理疑難排解</span><span class="sxs-lookup"><span data-stu-id="23861-102">Troubleshooting BizTalk Server Administration</span></span>
<span data-ttu-id="23861-103">本章節提供一個集中的位置來保存使用 BizTalk Server 管理主控台時經常遇到之問題的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="23861-103">This section provides a centralized location for information about common problems encountered while using the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="23861-104">除了下列的已知問題，[常見的問題和解決方式與 BizTalk Server 管理主控台](http://social.technet.microsoft.com/wiki/contents/articles/common-issues-and-resolutions-with-the-biztalk-server-administration-console.aspx)提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="23861-104">In addition to the following Known Issues, [Common Issues and Resolutions With the BizTalk Server Administration Console](http://social.technet.microsoft.com/wiki/contents/articles/common-issues-and-resolutions-with-the-biztalk-server-administration-console.aspx) provides additional information.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="23861-105">已知問題</span><span class="sxs-lookup"><span data-stu-id="23861-105">Known Issues</span></span>  
  
#### <a name="delay-in-entsso-service-prevents-biztalk-server-service-from-starting"></a><span data-ttu-id="23861-106">ENTSSO 服務中的延遲會使 BizTalk Server 服務無法啟動</span><span class="sxs-lookup"><span data-stu-id="23861-106">Delay in ENTSSO Service prevents BizTalk Server service from starting</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-107">問題</span><span class="sxs-lookup"><span data-stu-id="23861-107">Problem</span></span>  
 <span data-ttu-id="23861-108">未設定為自動啟動 dtc，重新啟動電腦可能會禁止 BizTalk Server 服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="23861-108">Rebooting your computer with DTC not set to automatic start-up may prevent the BizTalk Server service from starting.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-109">原因</span><span class="sxs-lookup"><span data-stu-id="23861-109">Cause</span></span>  
 <span data-ttu-id="23861-110">這是因為 ENTSSO 服務可能需要更多的時間才能啟動超過所允許的 BizTalk Server 服務逾時持續期間。</span><span class="sxs-lookup"><span data-stu-id="23861-110">This is because the ENTSSO service can take more time to start than is allowed by the BizTalk Server service timeout duration.</span></span>  
  
##### <a name="solution"></a><span data-ttu-id="23861-111">方案</span><span class="sxs-lookup"><span data-stu-id="23861-111">Solution</span></span>  
 <span data-ttu-id="23861-112">若要解決此問題，請將 DTC 設定為自動。</span><span class="sxs-lookup"><span data-stu-id="23861-112">To resolve this issue, set DTC to automatic.</span></span>  
  
#### <a name="sql-resources-may-become-locked"></a><span data-ttu-id="23861-113">SQL 資源可能會變成鎖定</span><span class="sxs-lookup"><span data-stu-id="23861-113">SQL resources may become locked</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-114">問題</span><span class="sxs-lookup"><span data-stu-id="23861-114">Problem</span></span>  
 <span data-ttu-id="23861-115">可能會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="23861-115">The following error may occur:</span></span>  
  
 <span data-ttu-id="23861-116">**交易 (處理序識別碼 95) 另一個處理序的鎖定資源上發生死結，而且已被選為死結的犧牲者。請重新執行交易。**</span><span class="sxs-lookup"><span data-stu-id="23861-116">**Transaction (Process ID 95) was deadlocked on lock resources with another process and has been chosen as the deadlock victim. Rerun the transaction.**</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-117">原因</span><span class="sxs-lookup"><span data-stu-id="23861-117">Cause</span></span>  
 <span data-ttu-id="23861-118">這是非常罕見的情況下，由一位使用者中被鎖定的資料庫管理的另一位使用者的結果執行的系統管理作業中。</span><span class="sxs-lookup"><span data-stu-id="23861-118">This is a very rare situation in which administrative operations performed by one user result in another user being locked out of database administration.</span></span>  
  
##### <a name="solution"></a><span data-ttu-id="23861-119">方案</span><span class="sxs-lookup"><span data-stu-id="23861-119">Solution</span></span>  
 <span data-ttu-id="23861-120">問題應補救本身很快。</span><span class="sxs-lookup"><span data-stu-id="23861-120">The problem should remedy itself shortly.</span></span> <span data-ttu-id="23861-121">再試一次在幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="23861-121">Try the operation again in a few minutes.</span></span>  
  
#### <a name="sql-database-may-become-locked"></a><span data-ttu-id="23861-122">SQL 資料庫可能會變成鎖定</span><span class="sxs-lookup"><span data-stu-id="23861-122">SQL database may become locked</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-123">問題</span><span class="sxs-lookup"><span data-stu-id="23861-123">Problem</span></span>  
 <span data-ttu-id="23861-124">使用者可能會被鎖定之外的 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="23861-124">Users may be locked out of the SQL database.</span></span> <span data-ttu-id="23861-125">可能傳回不同的錯誤訊息的數目。</span><span class="sxs-lookup"><span data-stu-id="23861-125">A number of different error messages may be returned.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-126">原因</span><span class="sxs-lookup"><span data-stu-id="23861-126">Cause</span></span>  
 <span data-ttu-id="23861-127">在某些情況下寫入資料庫的一位使用者將會有效地鎖定移出資料庫的另一位使用者。</span><span class="sxs-lookup"><span data-stu-id="23861-127">In some cases one user writing to the database will effectively lock another user out of the database.</span></span>  
  
##### <a name="solution"></a><span data-ttu-id="23861-128">方案</span><span class="sxs-lookup"><span data-stu-id="23861-128">Solution</span></span>  
 <span data-ttu-id="23861-129">問題應補救本身很快。</span><span class="sxs-lookup"><span data-stu-id="23861-129">The problem should remedy itself shortly.</span></span> <span data-ttu-id="23861-130">再試一次在幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="23861-130">Try the operation again in a few minutes.</span></span>  
  
#### <a name="termination-of-multiple-service-instances-in-a-multiple-messagebox-environment-fails-with-an-error"></a><span data-ttu-id="23861-131">在多個 messagebox 環境中的多個服務執行個體的終止失敗並發生錯誤</span><span class="sxs-lookup"><span data-stu-id="23861-131">Termination of multiple service instances in a multiple messagebox environment fails with an error</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-132">問題</span><span class="sxs-lookup"><span data-stu-id="23861-132">Problem</span></span>  
 <span data-ttu-id="23861-133">若要從 BizTalk Server 管理主控台的多個服務執行個體的嘗試失敗，並顯示類似下列的錯誤：</span><span class="sxs-lookup"><span data-stu-id="23861-133">Attempts to terminate multiple service instances from the BizTalk Server Administration console fail and an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="23861-134">SQL Server 已封鎖存取程序的元件 'Agent XPs' 的' sys.xp_sqlagent_enum_jobs'，因為此元件關閉這部伺服器的安全性組態的一部分。</span><span class="sxs-lookup"><span data-stu-id="23861-134">SQL Server blocked access to procedure 'sys.xp_sqlagent_enum_jobs' of component 'Agent XPs' because this component is turned off as part of the security configuration for this server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23861-135">在多個 messagebox 環境中，會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="23861-135">This problem occurs in a multiple messagebox environment.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-136">原因</span><span class="sxs-lookup"><span data-stu-id="23861-136">Cause</span></span>  
 <span data-ttu-id="23861-137">在多個 messagebox 環境中會發生此問題，如果 SQL 代理程式工作 'Operations_OperateOnInstances_OnMaster_\<*dbName*\>' 次要 messagebox 資料庫上未執行。</span><span class="sxs-lookup"><span data-stu-id="23861-137">This problem can occur in a multiple messagebox environment if the SQL agent job 'Operations_OperateOnInstances_OnMaster_\<*dbName*\>' is not running on the secondary messagebox databases.</span></span> <span data-ttu-id="23861-138">必須執行此作業，才能傳播到主要 messagebox 資料庫的次要 messagebox 資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="23861-138">This job must be running in order to propagate information from the secondary messagebox databases to the primary messagebox database.</span></span> <span data-ttu-id="23861-139">這項作業將無法執行，如果未啟用，或發生登入失敗。</span><span class="sxs-lookup"><span data-stu-id="23861-139">This job will fail to run if it is not enabled or if a logon failure occurs.</span></span>  
  
##### <a name="solution"></a><span data-ttu-id="23861-140">方案</span><span class="sxs-lookup"><span data-stu-id="23861-140">Solution</span></span>  
 <span data-ttu-id="23861-141">如果您使用 BizTalk 管理主控台中同時執行多個服務執行個體上的作業，而且您的 BizTalk Server 環境具有多個 messagebox 資料庫設定，請確認 SQL Server Agent 作業名稱為 ' Operations_OperateOnInstances_OnMaster_\<*dbName*\>' 所有的次要 （非主要） messagebox 資料庫上啟用。</span><span class="sxs-lookup"><span data-stu-id="23861-141">If you are using the BizTalk Administration console to perform operations on multiple service instances simultaneously and your BizTalk Server environment is configured with multiple messagebox databases, verify that the SQL Server Agent job named 'Operations_OperateOnInstances_OnMaster_\<*dbName*\>' is enabled on all secondary (non-master) messagebox databases.</span></span> <span data-ttu-id="23861-142">此外，在裝載次要 messagebox 資料庫的 SQL Server 電腦上的 SQL Server Agent 服務必須執行包含 BTS_SQLAGENT_USER 資料庫角色的次要 messagebox 資料庫中的帳戶。</span><span class="sxs-lookup"><span data-stu-id="23861-142">Additionally, the SQL Server Agent service on the SQL Server computer that hosts the secondary messagebox databases must run as an account that is included in the BTS_SQLAGENT_USER database role of the secondary messagebox database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23861-143">\<*dbname* \>是 BizTalk messagebox 資料庫的實際名稱的預留位置。</span><span class="sxs-lookup"><span data-stu-id="23861-143">\<*dbname*\> is a placeholder for the actual name of the BizTalk messagebox database.</span></span>  
  
 <span data-ttu-id="23861-144">請遵循下列步驟以加入次要 messagebox 資料庫的 BTS_SQLAGENT_USER 資料庫角色中的 SQL Server Agent 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="23861-144">Follow these steps to add the SQL Server Agent service account to the BTS_SQLAGENT_USER database role of the secondary messagebox database</span></span>  
  
 <span data-ttu-id="23861-145">**SQL Server 2008 上**</span><span class="sxs-lookup"><span data-stu-id="23861-145">**On SQL Server 2008**</span></span>  
  
1.  <span data-ttu-id="23861-146">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="23861-146">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="23861-147">出現提示時選擇**伺服器類型**的**Database Engine**然後輸入或選取**伺服器名稱**裝載的次要 messagebox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="23861-147">When prompted choose the **Server type** of **Database Engine** and enter or select the **Server name** that hosts the secondary messagebox database.</span></span>  
  
3.  <span data-ttu-id="23861-148">按一下以展開**資料庫**，按一下以展開次要 messagebox 資料庫，按一下以展開**安全性**，按一下以展開**角色**，按一下以展開**資料庫角色**，然後按兩下 BTS_SQLAGENT_USER 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="23861-148">Click to expand **Databases**, click to expand the secondary messagebox database, click to expand **Security**, click to expand **Roles**, click to expand **Database Roles**, and then double-click the BTS_SQLAGENT_USER database role.</span></span>  
  
4.  <span data-ttu-id="23861-149">按一下 **[加入]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="23861-149">Click the **Add** button.</span></span>  
  
5.  <span data-ttu-id="23861-150">按一下**瀏覽**選取 SQL Server Agent 服務帳戶是的成員的群組，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="23861-150">Click **Browse**, select a group that the SQL Server Agent service account is a member of, and then click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23861-151">如果 SQL Server Agent 服務帳戶不是指定群組的成員將會需要將它新增至群組。</span><span class="sxs-lookup"><span data-stu-id="23861-151">If the SQL Server Agent service account is not a member of the specified group then you will need to add it to the group.</span></span>  
  
#### <a name="changes-applied-in-one-instance-of-the-biztalk-administration-console-are-not-automatically-updated-in-other-instances-of-the-biztalk-administration-console"></a><span data-ttu-id="23861-152">套用到 BizTalk 管理主控台之一個執行個體的變更不會自動更新到 BizTalk 管理主控台的其他執行個體</span><span class="sxs-lookup"><span data-stu-id="23861-152">Changes applied in one instance of the BizTalk Administration console are not automatically updated in other instances of the BizTalk Administration console</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-153">問題</span><span class="sxs-lookup"><span data-stu-id="23861-153">Problem</span></span>  
 <span data-ttu-id="23861-154">如果有多個 BizTalk 管理主控台的執行個體同時連接到相同的 BizTalk Server 群組，則在 BizTalk 管理主控台的一個執行個體中所做的變更不會自動反映到 BizTalk 管理主控台的其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="23861-154">If multiple instances of the BizTalk Administration console are simultaneously connected to the same BizTalk Server group, changes made in one instance of the BizTalk Administration console are not automatically reflected in the other instance(s) of the BizTalk Administration console.</span></span> <span data-ttu-id="23861-155">當您嘗試修改顯示於 BizTalk 管理主控台的執行個體內的成品，而該成品的狀態不符合 BizTalk 管理資料庫中儲存之成品的實際狀態時，這樣會造成並行違規錯誤。</span><span class="sxs-lookup"><span data-stu-id="23861-155">This can cause concurrency violation errors when attempting to modify an artifact displayed in an instance of the BizTalk Administration console if the state of the artifact does not match the actual state of the artifact as stored in the BizTalk management database.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-156">原因</span><span class="sxs-lookup"><span data-stu-id="23861-156">Cause</span></span>  
 <span data-ttu-id="23861-157">BizTalk 管理主控台的每一個執行個體都會維護其自身的 BizTalk 群組組態快取，而且只會在快取中反映變更。</span><span class="sxs-lookup"><span data-stu-id="23861-157">Each instance of the BizTalk Administration console maintains its own cache of the BizTalk group configuration and only reflects changes in the cache.</span></span> <span data-ttu-id="23861-158">只有當重新整理 BizTalk 管理主控台檢視時，才會更新此快取。</span><span class="sxs-lookup"><span data-stu-id="23861-158">The cache is only updated when the BizTalk Administration console view is refreshed.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="23861-159">解決方案</span><span class="sxs-lookup"><span data-stu-id="23861-159">Resolution</span></span>  
 <span data-ttu-id="23861-160">如果您在 BizTalk 管理主控台中收到並行違規錯誤，請依序按一下更新 BizTalk 管理主控台的執行個體的快取**重新整理**BizTalk 管理主控台上的按鈕工具列或按**F5**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="23861-160">If you receive concurrency violation errors in the BizTalk Administration console, update the cache for the instance of the BizTalk Administration console by clicking the **Refresh** button on the BizTalk Administration console toolbar or by pressing the **F5** key.</span></span>  
  
#### <a name="failed-to-execute-action-stop-error-occurs-when-you-attempt-to-stop-an-orchestration-with-the-biztalk-administration-console"></a><span data-ttu-id="23861-161">當嘗試使用 BizTalk 管理主控台停止協調流程時，發生無法執行動作 '停止' 錯誤</span><span class="sxs-lookup"><span data-stu-id="23861-161">Failed to execute action 'Stop' error occurs when you attempt to stop an Orchestration with the BizTalk Administration console</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-162">問題</span><span class="sxs-lookup"><span data-stu-id="23861-162">Problem</span></span>  
 <span data-ttu-id="23861-163">當您嘗試使用 BizTalk 管理主控台停止協調流程時，會產生類似以下的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="23861-163">When you attempt to stop an Orchestration in the BizTalk Administration console, an error message similar to the following is generated:</span></span>  
  
```  
Failed to execute action 'Stop'.  
------------------------------  
ADDITIONAL INFORMATION:  
A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.) (Microsoft SQL Server, Error: 10054)  
```  
  
 <span data-ttu-id="23861-164">如果下列條件成立，可能就會發生這個問題：</span><span class="sxs-lookup"><span data-stu-id="23861-164">This problem may occur if the following conditions are true:</span></span>  
  
-   <span data-ttu-id="23861-165">BizTalk 管理主控台已開啟。</span><span class="sxs-lookup"><span data-stu-id="23861-165">The BizTalk Administration console is open.</span></span>  
  
-   <span data-ttu-id="23861-166">在叢集的 SQL Server 執行個體上安裝 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="23861-166">The BizTalk management database is installed on a clustered instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="23861-167">容錯移轉叢集的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="23861-167">The clustered instance of SQL Server is failed over.</span></span>  
  
-   <span data-ttu-id="23861-168">在完成容錯移轉之後，您嘗試使用 BizTalk 管理主控台來停止執行中的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="23861-168">After the failover is complete, you attempt to stop a running instance of an orchestration using the BizTalk Administration console.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-169">原因</span><span class="sxs-lookup"><span data-stu-id="23861-169">Cause</span></span>  
 <span data-ttu-id="23861-170">BizTalk 管理主控台就會維持連接[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="23861-170">The BizTalk Administration console maintains a connection to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management database.</span></span> <span data-ttu-id="23861-171">當連接[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫的容錯移轉期間已中斷，某些管理工作可能會傳回 「 無法連線 」 或 「 無法執行 」 錯誤，直到已關閉並重新開啟 BizTalk 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="23861-171">When the connection to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management database has been broken during the failover, some management tasks may return a "Failed to connect" or "Failed to execute" error until the BizTalk Administration console has been closed and reopened.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="23861-172">解決方案</span><span class="sxs-lookup"><span data-stu-id="23861-172">Resolution</span></span>  
 <span data-ttu-id="23861-173">關閉 BizTalk 管理主控台，並將它重新開啟。</span><span class="sxs-lookup"><span data-stu-id="23861-173">Close and reopen the BizTalk Administration console.</span></span> <span data-ttu-id="23861-174">重新開啟 BizTalk 管理主控台時它會建立新連接，以便指定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="23861-174">When the BizTalk Administration console is reopened it creates a new connection to the specified [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management database.</span></span>  
  
#### <a name="windows-group-names-that-were-previously-deleted-do-not-have-access-to-the-biztalk-server-databases"></a><span data-ttu-id="23861-175">之前已刪除的 Windows 群組名稱無法存取 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="23861-175">Windows group names that were previously deleted do not have access to the BizTalk Server databases</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-176">問題</span><span class="sxs-lookup"><span data-stu-id="23861-176">Problem</span></span>  
 <span data-ttu-id="23861-177">如果您在重新安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，使用了之前已刪除的 Windows 群組名稱，該 Windows 群組將無法存取 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="23861-177">If, when reinstalling [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you use a Windows group name that was previously deleted, the Windows group will not have access to the BizTalk Server databases.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-178">原因</span><span class="sxs-lookup"><span data-stu-id="23861-178">Cause</span></span>  
 <span data-ttu-id="23861-179">刪除某個 Windows 群組，然後建立相同名稱的 Windows 群組時，會針對該 Windows 群組產生新的安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="23861-179">Deleting a Windows group and then creating a Windows group with the same name produces a new Security Identifier (SID) for the Windows group.</span></span> <span data-ttu-id="23861-180">但是，舊的 SID 仍然會在 SQL Server 中快取，所以新的 Windows 群組無法登入 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="23861-180">However the old SID is still cached in SQL Server, so the new Windows group cannot log on to SQL Server.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="23861-181">解決方案</span><span class="sxs-lookup"><span data-stu-id="23861-181">Resolution</span></span>  
 <span data-ttu-id="23861-182">當您刪除 Windows 群組時，也必須一併移除此 Windows 群組的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="23861-182">When you delete the Windows group, you must also remove the SQL Server login for the Windows group.</span></span>  
  
#### <a name="biztalk-administrator-cannot-start-the-biztalk-server-administration-console"></a><span data-ttu-id="23861-183">BizTalk 系統管理員無法啟動 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="23861-183">BizTalk Administrator cannot start the BizTalk Server Administration console</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-184">問題</span><span class="sxs-lookup"><span data-stu-id="23861-184">Problem</span></span>  
 <span data-ttu-id="23861-185">BizTalk 系統管理員 (BizTalk 系統管理員 Windows 群組的成員) 如果不是本機電腦上 Windows 系統管理員群組的成員，則可能無法開啟 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="23861-185">A BizTalk Administrator (member of the BizTalk Administrators Windows group) may not be able to open the BizTalk Server Administration console if that user is not a member of the Windows Administrators group on the local computer.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-186">原因</span><span class="sxs-lookup"><span data-stu-id="23861-186">Cause</span></span>  
 <span data-ttu-id="23861-187">如果您已經重新安裝或重新設定 BizTalk Server，可能會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="23861-187">This problem can occur if you have reinstalled or reconfigured BizTalk Server.</span></span> <span data-ttu-id="23861-188">這是因為 SQL Server 使用了快取的安全性識別碼。</span><span class="sxs-lookup"><span data-stu-id="23861-188">This is because SQL Server used cached security IDs.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="23861-189">解決方案</span><span class="sxs-lookup"><span data-stu-id="23861-189">Resolution</span></span>  
 <span data-ttu-id="23861-190">暫時將 BizTalk 系統管理員加入本機電腦上的 Windows 系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="23861-190">Temporarily add the BizTalk Administrator to the local Windows Administrators group on the local computer.</span></span> <span data-ttu-id="23861-191">當成功開啟 BizTalk Server 管理主控台時，請從本機電腦上的本機 Windows 系統管理員群組中移除 BizTalk 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="23861-191">After successfully opening the BizTalk Server Administration console, remove the BizTalk Administrator from the local Windows Administrators group on the local computer.</span></span>  
  
#### <a name="cannot-start-a-host-instance-on-a-remote-computer"></a><span data-ttu-id="23861-192">無法在遠端電腦上啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="23861-192">Cannot start a host instance on a remote computer</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-193">問題</span><span class="sxs-lookup"><span data-stu-id="23861-193">Problem</span></span>  
 <span data-ttu-id="23861-194">當您在遠端電腦上建立的 BizTalk 主控件執行個體時，啟動 BizTalk 主控件執行個體時，您可能會看到下列錯誤: 「 無法啟動，因為發生登入失敗。 」</span><span class="sxs-lookup"><span data-stu-id="23861-194">When you create a BizTalk Host instance on a remote computer, you may see the following error when you start the BizTalk Host instance: "Failed to start due to logon failure."</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-195">原因</span><span class="sxs-lookup"><span data-stu-id="23861-195">Cause</span></span>  
 <span data-ttu-id="23861-196">如果您已經針對執行 BizTalk 主控件執行個體所用的服務帳戶輸入了無效的認證，或是此服務帳戶沒有具備服務權限的登入，則可能會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="23861-196">This error can occur if you entered invalid credentials for the service account under which the BizTalk Host instance is running, or the service account does not have logon as service rights.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="23861-197">解決方案</span><span class="sxs-lookup"><span data-stu-id="23861-197">Resolution</span></span>  
 <span data-ttu-id="23861-198">將具有服務權限的登入指派給遠端電腦中的服務帳戶，然後再啟動 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="23861-198">Assign logon as a service right to the service account in the remote computer before you start the BizTalk Host instance.</span></span> <span data-ttu-id="23861-199">這會自動在本機電腦上執行，但是遠端電腦上則必須以手動方式執行。</span><span class="sxs-lookup"><span data-stu-id="23861-199">This is done automatically on a local computer, but must be done manually on a remote computer.</span></span>  
  
#### <a name="creating-or-configuring-a-host-instance-on-an-x64-computer-with-the-32-bit-only-option-selected-fails"></a><span data-ttu-id="23861-200">選取僅 32 位元選項在 X64 電腦上建立或設定主控件執行個體會失敗</span><span class="sxs-lookup"><span data-stu-id="23861-200">Creating or configuring a host instance on an X64 computer with the 32-bit only option selected fails</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-201">問題</span><span class="sxs-lookup"><span data-stu-id="23861-201">Problem</span></span>  
 <span data-ttu-id="23861-202">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，建立具有 32 位元唯一選取的選項 （預設值） 的電腦可能無法在 X64 上的 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="23861-202">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, creating a BizTalk Host instance on an X64 computer with the 32-bit only option selected (default) may fail.</span></span>  
  
 <span data-ttu-id="23861-203">在 BizTalk Server 組態管理員中，選取 [僅 32 位元] 選項在 X64 電腦上設定 BizTalk Server 執行階段、建立內含式或外掛式主控件執行個體時，會導致服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="23861-203">In BizTalk Server Configuration Manager, when configuring the BizTalk Server Runtime on an X64 computer, creating an in-process or isolated host instance with the 32-bit only option selected can cause the service to fail to start.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-204">原因</span><span class="sxs-lookup"><span data-stu-id="23861-204">Cause</span></span>  
 <span data-ttu-id="23861-205">Unknown</span><span class="sxs-lookup"><span data-stu-id="23861-205">Unknown</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="23861-206">解決方案</span><span class="sxs-lookup"><span data-stu-id="23861-206">Resolution</span></span>  
 <span data-ttu-id="23861-207">這個問題會斷續發生。</span><span class="sxs-lookup"><span data-stu-id="23861-207">This issue is intermittent.</span></span> <span data-ttu-id="23861-208">嘗試再次建立或設定主控件，或者取消選取 [僅 32 位元] 選項。</span><span class="sxs-lookup"><span data-stu-id="23861-208">Attempt to create or configure the host again or deselect the 32-bit only option.</span></span>  
  
#### <a name="host-instance-deletion-does-not-clear-registry-information"></a><span data-ttu-id="23861-209">刪除主控件執行個體未清除登錄資訊</span><span class="sxs-lookup"><span data-stu-id="23861-209">Host instance deletion does not clear registry information</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-210">問題</span><span class="sxs-lookup"><span data-stu-id="23861-210">Problem</span></span>  
 <span data-ttu-id="23861-211">如果您不是本機電腦上的系統管理員，當您刪除內含式或外掛式主控件時，會出現拒絕存取錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="23861-211">If you are not an administrator on the local computer, when you delete an in-process or isolated host, an access denied error message appears.</span></span> <span data-ttu-id="23861-212">您可以強制刪除此主控件；</span><span class="sxs-lookup"><span data-stu-id="23861-212">You can forcibly delete the host.</span></span> <span data-ttu-id="23861-213">但是，以這種方式刪除主控件不會清除所有相關的登錄資訊。</span><span class="sxs-lookup"><span data-stu-id="23861-213">However, deleting the host in this manner does not clear all of the related registry information.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-214">原因</span><span class="sxs-lookup"><span data-stu-id="23861-214">Cause</span></span>  
 <span data-ttu-id="23861-215">刪除與主控件執行個體有關的登錄資訊需要系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="23861-215">Deletion of the registry information related to a host instance requires Administrator privileges.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="23861-216">解決方案</span><span class="sxs-lookup"><span data-stu-id="23861-216">Resolution</span></span>  
 <span data-ttu-id="23861-217">以本機系統管理員帳戶登入，然後再刪除主控件，如此也會一併移除相關的登錄資訊。</span><span class="sxs-lookup"><span data-stu-id="23861-217">Log on as a local Administrator account before deleting the host so that the related registry information is also removed.</span></span>  
  
#### <a name="cannot-delete-a-messagebox-database"></a><span data-ttu-id="23861-218">無法刪除 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="23861-218">Cannot delete a MessageBox database</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="23861-219">問題</span><span class="sxs-lookup"><span data-stu-id="23861-219">Problem</span></span>  
 <span data-ttu-id="23861-220">您可能無法刪除 MessageBox 資料庫；</span><span class="sxs-lookup"><span data-stu-id="23861-220">You may not be able to delete a MessageBox database.</span></span> <span data-ttu-id="23861-221">如果刪除失敗，則可能是以下其中一個問題所造成：</span><span class="sxs-lookup"><span data-stu-id="23861-221">If the deletion fails, one of the following issues may be responsible:</span></span>  
  
-   <span data-ttu-id="23861-222">快取重新整理間隔尚未過期。</span><span class="sxs-lookup"><span data-stu-id="23861-222">The cache refresh interval has not expired.</span></span>  
  
-   <span data-ttu-id="23861-223">MessageBox 資料庫包含未完成的執行個體。</span><span class="sxs-lookup"><span data-stu-id="23861-223">The MessageBox database contains incomplete instances.</span></span>  
  
 <span data-ttu-id="23861-224">刪除失敗時，如果快取重新整理間隔尚未過期，會出現下列錯誤訊息: 「 由於仍包含未完成工作在 MessageBox 中的，無法刪除 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="23861-224">If the cache refresh interval has not yet expired, the following error message appears when the deletion fails: "MessageBox cannot be deleted since there could be remaining work in the MessageBox.</span></span> <span data-ttu-id="23861-225">請確定 MessageBox 沒有未完成的執行個體，然後再試一次。"</span><span class="sxs-lookup"><span data-stu-id="23861-225">Please ensure that there are no more incomplete instances in the MessageBox, and try again."</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="23861-226">原因</span><span class="sxs-lookup"><span data-stu-id="23861-226">Cause</span></span>  
 <span data-ttu-id="23861-227">在您於 MessageBox 資料庫中停用新的訊息發佈與刪除此資料庫的兩段時間之間，快取重新整理間隔必須過期。</span><span class="sxs-lookup"><span data-stu-id="23861-227">The cache refresh interval must expire between the time you disable new message publication in the MessageBox database and the time you delete the database.</span></span> <span data-ttu-id="23861-228">根據預設，快取重新整理間隔為 60 秒。</span><span class="sxs-lookup"><span data-stu-id="23861-228">By default, the cache refresh interval is 60 seconds.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="23861-229">解決方案</span><span class="sxs-lookup"><span data-stu-id="23861-229">Resolution</span></span>  
 <span data-ttu-id="23861-230">若要刪除 MessageBox 資料庫，您必須先停用該 MessageBox 資料庫的新訊息發佈，然後等候快取重新整理間隔過期，再刪除 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="23861-230">To delete a MessageBox database, you must first disable new message publication for that MessageBox database, and then wait until the cache refresh interval expires, before you delete the MessageBox database.</span></span>  
  
 <span data-ttu-id="23861-231">如果 MessageBox 資料庫包含未完成的服務執行個體，就會出現下列錯誤訊息: 「 MessageBox 無法刪除，因為它可能仍然會包含不完整的執行個體。</span><span class="sxs-lookup"><span data-stu-id="23861-231">If the MessageBox database contains incomplete service instances, the following error message appears: "The MessageBox cannot be deleted because it may still contain incomplete instances.</span></span> <span data-ttu-id="23861-232">請確定 MessageBox 沒有未完成的執行個體，然後再試一次。"</span><span class="sxs-lookup"><span data-stu-id="23861-232">Ensure that there are no incomplete instances in the MessageBox, and try again".</span></span>  
  
 <span data-ttu-id="23861-233">您可以使用 BizTalk Server 管理主控台中的 [群組中樞] 頁面，檢視 MessageBox 資料庫中未完成的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="23861-233">You can view incomplete service instances in the MessageBox database using the Group Hub page in the BizTalk Server Administration Console.</span></span> <span data-ttu-id="23861-234">如需在 [群組中樞] 頁面中檢視服務執行個體的狀態資訊，請參閱[如何搜尋追蹤服務執行個體](../core/how-to-search-for-tracked-service-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="23861-234">For information about viewing the status of service instances in the Group Hub page, see [How to Search for Tracked Service Instances](../core/how-to-search-for-tracked-service-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23861-235">請參閱</span><span class="sxs-lookup"><span data-stu-id="23861-235">See Also</span></span>  
 [<span data-ttu-id="23861-236">疑難排解</span><span class="sxs-lookup"><span data-stu-id="23861-236">Troubleshooting</span></span>](../core/troubleshooting.md)