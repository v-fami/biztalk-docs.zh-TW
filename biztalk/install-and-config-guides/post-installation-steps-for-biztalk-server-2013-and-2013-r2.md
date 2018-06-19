---
title: 後續安裝步驟，BizTalk Server 2013 和 2013 R2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3b47843-9da5-4144-8b84-135494b8ab43
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b86d8c4c1e1a22dad349c2cc8c2be5ca4b206b2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299902"
---
# <a name="post-installation-steps-for-biztalk-server-2013-and-2013-r2"></a><span data-ttu-id="e42a6-102">BizTalk Server 2013 和 2013 R2 的後續安裝步驟</span><span class="sxs-lookup"><span data-stu-id="e42a6-102">Post-installation Steps for BizTalk Server 2013 and 2013 R2</span></span>
  
##  <a name="BKMK_NamedPipes"></a> <span data-ttu-id="e42a6-103">啟用 TCP/IP 和具名管道</span><span class="sxs-lookup"><span data-stu-id="e42a6-103">Enable TCP/IP and Named Pipes</span></span>  
  
1.  <span data-ttu-id="e42a6-104">開啟 **SQL Server 組態管理員**。</span><span class="sxs-lookup"><span data-stu-id="e42a6-104">Open **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="e42a6-105">展開 [SQL Server 網路組態]，然後選取 [MSSQLSERVER 的通訊協定]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-105">Expand **SQL Server Network Configuration**, and select **Protocols for MSSQLSERVER**.</span></span>  
  
4.  <span data-ttu-id="e42a6-106">確認同時啟用 [TCP/IP] 和 [具名管道]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-106">Verify that both **TCP/IP** and **Named Pipes** are enabled.</span></span> <span data-ttu-id="e42a6-107">如果啟用，請繼續下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="e42a6-107">If enabled, proceed to the next step.</span></span>  
  
     <span data-ttu-id="e42a6-108">如果未啟用：</span><span class="sxs-lookup"><span data-stu-id="e42a6-108">If not enabled:</span></span>  
  
    -   <span data-ttu-id="e42a6-109">以滑鼠右鍵按一下通訊協定，然後按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-109">Right-click the protocol, and then click **Enable**.</span></span>  
  
    -   <span data-ttu-id="e42a6-110">必要時，重複執行以啟用其他通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e42a6-110">Repeat to enable the other protocol if necessary.</span></span>  
  
    -   <span data-ttu-id="e42a6-111">在左窗格中，按一下 [SQL Server 服務]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-111">In the left-hand pane, click **SQL Server Services**.</span></span>  
  
    -   <span data-ttu-id="e42a6-112">在右窗格中，以滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後按一下 [停止]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-112">In the right-hand pane, right-click **SQL Server (MSSQLSERVER)**, and click **Stop**.</span></span>  
  
    -   <span data-ttu-id="e42a6-113">停止服務時，以滑鼠右鍵按一下 [SQL Server (MSSQLSERVER)]，然後按一下 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-113">When the service has stopped, right-click **SQL Server (MSSQLSERVER)**, and click **Start**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e42a6-114">如果您要使用 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]，可能會停止 **NS$BAMAlerts** 服務。</span><span class="sxs-lookup"><span data-stu-id="e42a6-114">If you are using [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], the **NS$BAMAlerts** service may be stopped.</span></span> <span data-ttu-id="e42a6-115">重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="e42a6-115">Restart the service.</span></span>  
  
5.  <span data-ttu-id="e42a6-116">關閉 [組態管理員]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-116">Close the **Configuration Manager**.</span></span>  
  
##  <a name="BKMK_DTC"></a> <span data-ttu-id="e42a6-117">在本機主機伺服器上啟用 DTC</span><span class="sxs-lookup"><span data-stu-id="e42a6-117">Enable DTC on the Local Host Server</span></span>  
  
1.  <span data-ttu-id="e42a6-118">開啟 [元件服務]：</span><span class="sxs-lookup"><span data-stu-id="e42a6-118">Open Component Services:</span></span>  
  
     <span data-ttu-id="e42a6-119">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]**︰選取 [Windows] 按鈕，然後輸入**元件服務**。</span><span class="sxs-lookup"><span data-stu-id="e42a6-119">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Select the Windows button, and type **Component Services**.</span></span> <span data-ttu-id="e42a6-120">在 [結果] 視窗中，選取 [元件服務]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-120">In the Results window, select **Component Services**.</span></span>  
  
     <span data-ttu-id="e42a6-121">**Windows 8.1**︰選取 [Windows] 按鈕，然後輸入**系統管理工具**。</span><span class="sxs-lookup"><span data-stu-id="e42a6-121">**Windows 8.1**: Select the Windows button, and type **Administrative Tools**.</span></span> <span data-ttu-id="e42a6-122">在 [搜尋] 視窗中，選取 [設定]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-122">In the Search window, select **Settings**.</span></span> <span data-ttu-id="e42a6-123">在 [結果] 視窗中，按一下 [系統管理工具]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-123">In the Results window, click **Administrative Tools**.</span></span> <span data-ttu-id="e42a6-124">按兩下 [元件服務]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-124">Double-click **Component Services**.</span></span>  
  
     <span data-ttu-id="e42a6-125">**Windows 7 SP1**︰選取 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-125">**Windows 7 SP1**: Select **Start**.</span></span> <span data-ttu-id="e42a6-126">在 [搜尋] 文字方塊中，輸入**元件服務**，然後按一下以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="e42a6-126">In the **Search** text box, type **Component Services**, and click it to open.</span></span>  
  
2.  <span data-ttu-id="e42a6-127">在主控台樹狀目錄中，依序展開 [元件服務]、[電腦]、[我的電腦]和 [分散式交易協調器]，然後按一下 [本機 DTC]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-127">In the console tree, expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, and then click **Local DTC**.</span></span>  
  
3.  <span data-ttu-id="e42a6-128">以滑鼠右鍵按一下 [本機 DTC]，然後選取 [內容] 以開啟 [本機 DTC 內容]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-128">Right-click **Local DTC** and select **Properties** to open the **Local DTC Properties**.</span></span>  
  
4.  <span data-ttu-id="e42a6-129">選取 [安全性] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e42a6-129">Select the **Security** tab.</span></span>  
  
5.  <span data-ttu-id="e42a6-130">確認已核取下列選項：</span><span class="sxs-lookup"><span data-stu-id="e42a6-130">Confirm the following options are checked:</span></span>  
  
    -   <span data-ttu-id="e42a6-131">**網路 DTC 存取**</span><span class="sxs-lookup"><span data-stu-id="e42a6-131">**Network DTC Access**</span></span>  
  
    -   <span data-ttu-id="e42a6-132">**允許輸入**</span><span class="sxs-lookup"><span data-stu-id="e42a6-132">**Allow Inbound**</span></span>  
  
    -   <span data-ttu-id="e42a6-133">**允許輸出**</span><span class="sxs-lookup"><span data-stu-id="e42a6-133">**Allow Outbound**</span></span>  
  
    -   <span data-ttu-id="e42a6-134">**不需要驗證**</span><span class="sxs-lookup"><span data-stu-id="e42a6-134">**No Authentication Required**</span></span>  
  
     <span data-ttu-id="e42a6-135">如需可能需要的其他設定，請參閱 [MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。</span><span class="sxs-lookup"><span data-stu-id="e42a6-135">For additional settings that may be needed, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>  
  
6.  <span data-ttu-id="e42a6-136">選取 [確定]，關閉 [本機 DTC 內容] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e42a6-136">Select **OK** to close the **Local DTC Properties** dialog box.</span></span> <span data-ttu-id="e42a6-137">系統提示時，請重新啟動 MSDTC 服務。</span><span class="sxs-lookup"><span data-stu-id="e42a6-137">Restart the MSDTC service if prompted.</span></span>  
  
7.  <span data-ttu-id="e42a6-138">關閉 [元件服務]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-138">Close **Component Services**.</span></span>  
  
##  <a name="BKMK_Firewall"></a> <span data-ttu-id="e42a6-139">設定 Windows 防火牆啟用 DTC</span><span class="sxs-lookup"><span data-stu-id="e42a6-139">Configure Windows Firewall to Enable DTC</span></span>  
  
1.  <span data-ttu-id="e42a6-140">開啟 [Windows 防火牆]：</span><span class="sxs-lookup"><span data-stu-id="e42a6-140">Open **Windows Firewall**:</span></span>  
  
     <span data-ttu-id="e42a6-141">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]**：按一下 [Windows] 按鈕，然後輸入 **Windows 防火牆**。</span><span class="sxs-lookup"><span data-stu-id="e42a6-141">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Click the Windows button, and type **Windows Firewall**.</span></span> <span data-ttu-id="e42a6-142">在 [結果] 視窗中，按一下 [Windows 防火牆]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-142">In the Results window, click **Windows Firewall**.</span></span>  
  
     <span data-ttu-id="e42a6-143">**Windows 8.1**：按一下 [Windows] 按鈕，然後輸入 **Windows 防火牆**。</span><span class="sxs-lookup"><span data-stu-id="e42a6-143">**Windows 8.1**: Click the Windows button, and type **Windows Firewall**.</span></span> <span data-ttu-id="e42a6-144">在 [搜尋] 視窗中，按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-144">In the Search window, click **Settings**.</span></span> <span data-ttu-id="e42a6-145">在 [結果] 視窗中，按一下 [Windows 防火牆]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-145">In the Results window, click **Windows Firewall**.</span></span>  
  
     <span data-ttu-id="e42a6-146">**Windows 7 SP1**：按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-146">**Windows 7 SP1**: Click **Start**.</span></span> <span data-ttu-id="e42a6-147">在 [搜尋] 文字方塊中，輸入 **Windows 防火牆**，然後按一下以開啟該項目。</span><span class="sxs-lookup"><span data-stu-id="e42a6-147">In the **Search** text box, type **Windows Firewall**, and click it to open.</span></span>  
  
2.  <span data-ttu-id="e42a6-148">按一下 [進階設定]，然後按一下 [輸入規則]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-148">Click **Advanced Settings** and click **Inbound Rules**.</span></span>  
  
3.  <span data-ttu-id="e42a6-149">在 [輸入規則] 窗格中，以滑鼠右鍵按一下 [分散式交易協調器] \* (適合的話)，然後按一下 [啟用規則]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-149">In the **Inbound Rules** pane, right-click **Distributed Transaction Coordinator** \* (as appropriate), and then click **Enable Rule**.</span></span>  
  
4.  <span data-ttu-id="e42a6-150">按一下 [輸出規則]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-150">Click **Outbound Rules**.</span></span>  
  
5.  <span data-ttu-id="e42a6-151">在 [輸出規則] 窗格中，以滑鼠右鍵按一下 [分散式交易協調器] \* (適合的話)，然後按一下 [啟用規則]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-151">In the **Outbound Rules** pane, right-click **Distributed Transaction Coordinator** \* (as appropriate), and then click **Enable Rule**.</span></span>  
  
6.  <span data-ttu-id="e42a6-152">在 [控制台] 上，將檢視變更為依圖示列出，然後按兩下 [系統管理工具]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-152">On the **Control Panel**, change the view to list by icons, and then double-click **Administrative Tools**.</span></span>  
  
7.  <span data-ttu-id="e42a6-153">按兩下 [服務]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-153">Double-click **Services**.</span></span>  
  
8.  <span data-ttu-id="e42a6-154">以滑鼠右鍵按一下 [COM + 系統應用程式]，並按一下 [重新啟動]，然後等待服務重新啟動。</span><span class="sxs-lookup"><span data-stu-id="e42a6-154">Right-click **COM+ System Application**, click **Restart**, and wait for the service to restart.</span></span>  
  
9. <span data-ttu-id="e42a6-155">以滑鼠右鍵按一下**分散式交易協調器**服務，再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="e42a6-155">Right-click and restart the **Distributed Transaction Coordinator** service.</span></span>  
  
10. <span data-ttu-id="e42a6-156">以滑鼠右鍵按一下 **SQL Server (MSSQLSERVER)** 服務，再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="e42a6-156">Right-click and restart the **SQL Server (MSSQLSERVER)** service.</span></span>  
  
11. <span data-ttu-id="e42a6-157">關閉 [服務 (本機)]，然後關閉 [系統管理工具]。</span><span class="sxs-lookup"><span data-stu-id="e42a6-157">Close **Services (Local)**, and then close **Administrative Tools**.</span></span>  
  
##  <a name="BKMK_SQLAgent"></a> <span data-ttu-id="e42a6-158">設定 SQL Agent 作業</span><span class="sxs-lookup"><span data-stu-id="e42a6-158">Configure SQL Agent Jobs</span></span>  
  
|<span data-ttu-id="e42a6-159">作業</span><span class="sxs-lookup"><span data-stu-id="e42a6-159">Job</span></span>|<span data-ttu-id="e42a6-160">描述</span><span class="sxs-lookup"><span data-stu-id="e42a6-160">Description</span></span>|<span data-ttu-id="e42a6-161">設定原因</span><span class="sxs-lookup"><span data-stu-id="e42a6-161">Why configure</span></span>|  
|---------|-----------------|-------------------|  
|<span data-ttu-id="e42a6-162">**備份 BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="e42a6-162">**Backup BizTalk Server**</span></span>|<span data-ttu-id="e42a6-163">這個 SQL Agent 作業會備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e42a6-163">This SQL Agent job backs up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and the log files.</span></span> <span data-ttu-id="e42a6-164">設定作業時，您可以決定頻率和檔案位置等參數。</span><span class="sxs-lookup"><span data-stu-id="e42a6-164">When configuring the job, you determine parameters like frequency and file location.</span></span><br /><br /> <span data-ttu-id="e42a6-165">下列連結會說明 SQL Agent 作業和其參數︰</span><span class="sxs-lookup"><span data-stu-id="e42a6-165">The following links describe the SQL Agent job and its parameters:</span></span><br /><br /> <span data-ttu-id="e42a6-166">[備份和還原 BizTalk Server 資料庫](http://msdn.microsoft.com/library/aa561125\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e42a6-166">[Backing Up and Restoring BizTalk Server Databases](http://msdn.microsoft.com/library/aa561125\(v=bts.80\).aspx)</span></span><br /><br /> <span data-ttu-id="e42a6-167">[如何設定備份 BizTalk Server 作業](http://msdn.microsoft.com/library/aa546765\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e42a6-167">[How to Configure the Backup BizTalk Server Job](http://msdn.microsoft.com/library/aa546765\(v=bts.80\).aspx)</span></span>|<span data-ttu-id="e42a6-168">這個 SQL Agent 作業也會截斷交易記錄檔，有利改善效能。</span><span class="sxs-lookup"><span data-stu-id="e42a6-168">This SQL Agent job also truncates the transaction logs, which helps improve performance.</span></span><br /><br /> <span data-ttu-id="e42a6-169">**備份 BizTalk Server** 作業不會移除或刪除備份檔案，包括較舊的檔案。</span><span class="sxs-lookup"><span data-stu-id="e42a6-169">The **Backup BizTalk Server** job does not remove or delete backup files, including older files.</span></span> <span data-ttu-id="e42a6-170">若要刪除備份檔案，請參閱 [Microsoft BizTalk Server 資料庫伺服器與時俱增的備份檔案中失敗的「備份 BizTalk Server」作業](http://support.microsoft.com/kb/982546)。</span><span class="sxs-lookup"><span data-stu-id="e42a6-170">To delete backup files, refer to [The "Backup BizTalk Server" job fails when backup files accumulate over time in the Microsoft BizTalk Server database server](http://support.microsoft.com/kb/982546).</span></span>|  
|<span data-ttu-id="e42a6-171">**DTA 清除與封存**</span><span class="sxs-lookup"><span data-stu-id="e42a6-171">**DTA Purge and Archive**</span></span>|<span data-ttu-id="e42a6-172">這個 SQL Agent 作業會截斷和封存 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤資料庫 (BizTalkDTADb)。</span><span class="sxs-lookup"><span data-stu-id="e42a6-172">This SQL Agent job truncates and archives the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Tracking database (BizTalkDTADb).</span></span> <span data-ttu-id="e42a6-173">設定作業時，您可以決定已完成執行個體的保留天數以及所有資料的保留天數等參數。</span><span class="sxs-lookup"><span data-stu-id="e42a6-173">When configuring the job, you determine parameters like how many days to keep completed instances and how many to days to keep all data.</span></span><br /><br /> <span data-ttu-id="e42a6-174">下列連結會說明 SQL Agent 作業和其參數︰</span><span class="sxs-lookup"><span data-stu-id="e42a6-174">The following links describe the SQL Agent job and its parameters:</span></span><br /><br /> <span data-ttu-id="e42a6-175">[封存和清除 BizTalk 追蹤資料庫](http://msdn.microsoft.com/library/aa560754\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e42a6-175">[Archiving and Purging the BizTalk Tracking Database](http://msdn.microsoft.com/library/aa560754\(v=bts.80\).aspx)</span></span><br /><br /> <span data-ttu-id="e42a6-176">[如何設定 DTA 清除與封存作業](http://msdn.microsoft.com/library/aa558715\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e42a6-176">[How to Configure the DTA Purge and Archive Job](http://msdn.microsoft.com/library/aa558715\(v=bts.80\).aspx)</span></span>|<span data-ttu-id="e42a6-177">此 SQL Agent 工作維護追蹤主機以及清除追蹤事件，而直接影響效能。</span><span class="sxs-lookup"><span data-stu-id="e42a6-177">This SQL Agent job directly impacts performance by maintaining the Tracking host and purging tracking events.</span></span><br /><br /> <span data-ttu-id="e42a6-178">效能主題包括：</span><span class="sxs-lookup"><span data-stu-id="e42a6-178">Performance topics include:</span></span><br /><br /> [<span data-ttu-id="e42a6-179">如何維護和疑難排解 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="e42a6-179">How to maintain and troubleshoot BizTalk Server databases</span></span>](http://support.microsoft.com/kb/952555)<br /><br /> <span data-ttu-id="e42a6-180">[調整追蹤資料庫大小的指導方針](http://msdn.microsoft.com/library/aa559162\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e42a6-180">[Tracking Database Sizing Guidelines](http://msdn.microsoft.com/library/aa559162\(v=bts.80\).aspx)</span></span>|  
  
 <span data-ttu-id="e42a6-181">**其他**</span><span class="sxs-lookup"><span data-stu-id="e42a6-181">**Additional**</span></span>  
  
-   <span data-ttu-id="e42a6-182">安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，會自動建立數個 SQL Agent 作業 (如下列連結所述)：</span><span class="sxs-lookup"><span data-stu-id="e42a6-182">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed, several SQL Agent jobs are automatically created, as described in the following links:</span></span>  
  
     [<span data-ttu-id="e42a6-183">BizTalk Server 中的 SQL Server Agent 作業描述</span><span class="sxs-lookup"><span data-stu-id="e42a6-183">Description of the SQL Server Agent jobs in BizTalk Server</span></span>](http://support.microsoft.com/kb/919776)  
  
     <span data-ttu-id="e42a6-184">[資料庫結構和作業](http://msdn.microsoft.com/library/aa561960\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e42a6-184">[Database Structure and Jobs](http://msdn.microsoft.com/library/aa561960\(v=bts.80\).aspx)</span></span>  
  
##  <a name="BKMK_InstallCU"></a> <span data-ttu-id="e42a6-185">安裝累積更新</span><span class="sxs-lookup"><span data-stu-id="e42a6-185">Install Cumulative Updates</span></span>  
 <span data-ttu-id="e42a6-186">安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之後，請安裝 Windows Updates 中列出的任何 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 累積更新。</span><span class="sxs-lookup"><span data-stu-id="e42a6-186">After you install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], install any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cumulative updates listed in Windows Update.</span></span> <span data-ttu-id="e42a6-187">[知識庫文章 2555976](http://support.microsoft.com/kb/2555976) 列出可用的 Service Pack 和累積更新。</span><span class="sxs-lookup"><span data-stu-id="e42a6-187">[KB article 2555976](http://support.microsoft.com/kb/2555976) lists available service packs and cumulative updates.</span></span>  
  
## <a name="next"></a><span data-ttu-id="e42a6-188">下一個</span><span class="sxs-lookup"><span data-stu-id="e42a6-188">Next</span></span>  
[<span data-ttu-id="e42a6-189">設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e42a6-189">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)
  
## <a name="see-also"></a><span data-ttu-id="e42a6-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e42a6-190">See Also</span></span>  
 [<span data-ttu-id="e42a6-191">附錄 A：無訊息安裝</span><span class="sxs-lookup"><span data-stu-id="e42a6-191">Appendix A: Silent Installation</span></span>](../install-and-config-guides/appendix-a-silent-installation.md) 
 
[<span data-ttu-id="e42a6-192">附錄 B：安裝 Microsoft SharePoint 配接器</span><span class="sxs-lookup"><span data-stu-id="e42a6-192">Appendix B: Install the Microsoft SharePoint Adapter</span></span>](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)  

[<span data-ttu-id="e42a6-193">附錄 C：可轉散發封包檔</span><span class="sxs-lookup"><span data-stu-id="e42a6-193">Appendix C: Redistributable CAB Files</span></span>](../install-and-config-guides/appendix-c-redistributable-cab-files.md)  

[<span data-ttu-id="e42a6-194">附錄 D︰建立 SMTP 伺服器</span><span class="sxs-lookup"><span data-stu-id="e42a6-194">Appendix D: Create the SMTP Server</span></span>](../install-and-config-guides/appendix-d-create-the-smtp-server.md)

[<span data-ttu-id="e42a6-195">將 BizTalk Server 解除安裝並取消設定以將其移除</span><span class="sxs-lookup"><span data-stu-id="e42a6-195">Uninstall and unconfigure BizTalk Server to remove it</span></span>](../install-and-config-guides/uninstall-and-unconfigure-biztalk-server-to-remove-it.md)
