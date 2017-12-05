---
title: "新增主控件執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ba10a6-c5e7-4dec-98f1-4e6ba44c2851
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4c2e029e9599143c52577771a313d9810ca6f12
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="add-a-host-instance"></a><span data-ttu-id="a670b-102">新增主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="a670b-102">Add a Host Instance</span></span>

## <a name="overview"></a><span data-ttu-id="a670b-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a670b-103">Overview</span></span>
<span data-ttu-id="a670b-104">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或 Windows Management Instrumentation (WMI) 來新增主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a670b-104">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console or Windows Management Instrumentation (WMI) to add host instances.</span></span> <span data-ttu-id="a670b-105">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您一次只能新增一個主控件執行個體到一個伺服器。</span><span class="sxs-lookup"><span data-stu-id="a670b-105">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you can only add a host instance to one server at a time.</span></span> <span data-ttu-id="a670b-106">如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="a670b-106">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span> <span data-ttu-id="a670b-107">如需使用 WMI 新增主控件執行個體的詳細資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="a670b-107">For information about using WMI to add a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="a670b-108">新增主控件執行個體會將指定主控件的執行個體對應至 BizTalk Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a670b-108">Adding a host instance maps the instance of a given host to an instance of BizTalk Server.</span></span> <span data-ttu-id="a670b-109">如果您有必須修復的現有主控件執行個體，您可以更新主控件執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="a670b-109">If you have an existing host instance that you must repair, you can update the host instance properties.</span></span> <span data-ttu-id="a670b-110">您必須停止現有的主控件執行個體，才能再次新增它。</span><span class="sxs-lookup"><span data-stu-id="a670b-110">You must stop an existing host instance before you can add it again.</span></span> <span data-ttu-id="a670b-111">如需停止主控件執行個體的詳細資訊，請參閱[如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="a670b-111">For information about stopping a host instance, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a670b-112">如果您想要建立更多 26 主控件執行個體，您必須依照知識庫文件 184802"User32.dll 或 Kernel32.dll 無法初始化，」，可在[http://go.microsoft.com/fwlink/?LinkId=26176](http://go.microsoft.com/fwlink/?LinkId=26176)。</span><span class="sxs-lookup"><span data-stu-id="a670b-112">If you want to create more that 26 host instances, you must follow the instructions in Knowledge Base article 184802, "User32.dll or Kernel32.dll Fails to Initialize," which is available at [http://go.microsoft.com/fwlink/?LinkId=26176](http://go.microsoft.com/fwlink/?LinkId=26176).</span></span> <span data-ttu-id="a670b-113">當您套用該「知識庫」文件中的建議之後，若需要其他主控件執行個體，您可以嘗試減少 BTSNTSvc 服務的每個執行個體之可用記憶體量。</span><span class="sxs-lookup"><span data-stu-id="a670b-113">If you require additional host instances after you apply the recommendations in this Knowledge Base article, you can try reducing the amount of memory available for each instance of the BTSNTSvc service.</span></span> <span data-ttu-id="a670b-114">這將提供額外的必要記憶體，供建立更多執行個體之用。</span><span class="sxs-lookup"><span data-stu-id="a670b-114">This will provide additional memory necessary to create more instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a670b-115">服務帳戶將會在安裝主控件執行個體的伺服器上自動被授與「登入為服務」權限。</span><span class="sxs-lookup"><span data-stu-id="a670b-115">The service account will automatically be granted log on as service permissions on the server where the host instance is installed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a670b-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="a670b-116">Prerequisites</span></span>  
 <span data-ttu-id="a670b-117">若要執行此程序，您必須以「系統管理員」群組及「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="a670b-117">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="a670b-118">此外，您也必須是下列資料庫所在伺服器的 db_securityadmin SQL Server 資料庫角色及 securityadmin SQL Server 角色的成員：</span><span class="sxs-lookup"><span data-stu-id="a670b-118">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="a670b-119">BAM 主要匯入 (BAMPrimaryImport)</span><span class="sxs-lookup"><span data-stu-id="a670b-119">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="a670b-120">BizTalk 管理 (BizTalkMgmtDb)</span><span class="sxs-lookup"><span data-stu-id="a670b-120">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="a670b-121">BizTalk MessageBox (BizTalkMsgBoxDb) (全部)</span><span class="sxs-lookup"><span data-stu-id="a670b-121">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="a670b-122">BizTalk 追蹤 (BizTalk DTADb)</span><span class="sxs-lookup"><span data-stu-id="a670b-122">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="a670b-123">規則引擎 (BizTalkRuleEngineDb)</span><span class="sxs-lookup"><span data-stu-id="a670b-123">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a670b-124">建議您使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 指令碼更新主控件執行個體的帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="a670b-124">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="a670b-125">這樣可以確保 BizTalk Server 會更新 BizTalk Server 資料庫中的帳戶資訊，並且在資料庫和主控件執行個體之間維持同步的安全性組態。</span><span class="sxs-lookup"><span data-stu-id="a670b-125">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="a670b-126">步驟</span><span class="sxs-lookup"><span data-stu-id="a670b-126">Steps</span></span>
  
1.  <span data-ttu-id="a670b-127">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a670b-127">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a670b-128">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 [BizTalk 群組]，然後按一下**平台設定**。</span><span class="sxs-lookup"><span data-stu-id="a670b-128">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then click **Platform Settings**.</span></span>  
  
3.  <span data-ttu-id="a670b-129">以滑鼠右鍵按一下**主控件執行個體**，按一下 **新增**，然後按一下 **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="a670b-129">Right-click **Host Instances**, click **New**, and then click **Host Instance**.</span></span>  
  
4.  <span data-ttu-id="a670b-130">在**主控件執行個體屬性**對話方塊中，執行下列命令，，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="a670b-130">In the **Host Instance Properties** dialog box, do the following, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="a670b-131">使用</span><span class="sxs-lookup"><span data-stu-id="a670b-131">Use this</span></span>|<span data-ttu-id="a670b-132">動作</span><span class="sxs-lookup"><span data-stu-id="a670b-132">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a670b-133">**主機名稱**</span><span class="sxs-lookup"><span data-stu-id="a670b-133">**Host name**</span></span>|<span data-ttu-id="a670b-134">顯示和所選取的伺服器相關聯的主控件名稱。</span><span class="sxs-lookup"><span data-stu-id="a670b-134">Displays the name of the host associated with the selected server.</span></span>|  
    |<span data-ttu-id="a670b-135">**Server**</span><span class="sxs-lookup"><span data-stu-id="a670b-135">**Server**</span></span>|<span data-ttu-id="a670b-136">顯示與所選取的主控件相關聯的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a670b-136">Displays the server associated with the selected host.</span></span>|  
    |<span data-ttu-id="a670b-137">**登入**</span><span class="sxs-lookup"><span data-stu-id="a670b-137">**Logon**</span></span>|<span data-ttu-id="a670b-138">顯示將執行主控件執行個體的新服務帳戶之帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="a670b-138">Displays the account name of the new service account under which the host instance will run.</span></span>|  
    |<span data-ttu-id="a670b-139">**設定**</span><span class="sxs-lookup"><span data-stu-id="a670b-139">**Configure**</span></span>|<span data-ttu-id="a670b-140">按一下即可顯示**登入認證**對話方塊中，您可以在此輸入的帳戶名稱和密碼將執行主控件執行個體的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a670b-140">Click to display the **Logon Credentials** dialog box, where you can enter the account name and password of the account under which the host instance will run.</span></span>|  
    |<span data-ttu-id="a670b-141">**停用主控件執行個體無法啟動**</span><span class="sxs-lookup"><span data-stu-id="a670b-141">**Disable host instance from starting**</span></span>|<span data-ttu-id="a670b-142">選取此核取方塊將選取主控件的狀態由啟用變更為停用。</span><span class="sxs-lookup"><span data-stu-id="a670b-142">Select this check box to change the status of the selected host from enabled to disabled.</span></span> <span data-ttu-id="a670b-143">若您不要主控件執行個體啟動，但是要保留其設定時，停用主控件執行個體就非常有用。</span><span class="sxs-lookup"><span data-stu-id="a670b-143">Disabling a host instance is useful if you do not want the host instance to start, but you do want to preserve its settings.</span></span>|  
  
 <span data-ttu-id="a670b-144">在您安裝主控件執行個體之後，必須啟動它，這樣它才能將訊息路由至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a670b-144">After you install a host instance, you must start it so that it can route messages to the MessageBox databases.</span></span> <span data-ttu-id="a670b-145">如需啟動主控件執行個體的相關資訊，請參閱[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="a670b-145">For information about starting a host instance, see [How to Start a Host Instance](../core/how-to-start-a-host-instance.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="a670b-146">已知問題</span><span class="sxs-lookup"><span data-stu-id="a670b-146">Known Issues</span></span>  
  
#### <a name="a-biztalk-host-instance-is-created-with-a-status-of-uninstall-failed-if-the-designated-biztalk-server-runtime-computer-is-not-available-during-host-instance-creation"></a><span data-ttu-id="a670b-147">如果在主控件執行個體建立期間無法使用指定的 BizTalk Server 執行階段電腦，則會建立狀態為「解除安裝失敗」的 BizTalk 主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="a670b-147">A BizTalk Host instance is created with a status of "Uninstall failed" if the designated BizTalk Server runtime computer is not available during host instance creation</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="a670b-148">問題</span><span class="sxs-lookup"><span data-stu-id="a670b-148">Problem</span></span>  
 <span data-ttu-id="a670b-149">如果在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦的遠端電腦上安裝 BizTalk 管理主控台，則即使無法使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦，仍然可能會在遠端 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上嘗試建立主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a670b-149">If the BizTalk Administration Console is installed on a machine that is remote to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computer, it is possible to attempt to create a host instance on the remote [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer even if the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer is unavailable.</span></span>  
  
 <span data-ttu-id="a670b-150">如果您嘗試在無法使用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上建立 BizTalk 主控件執行個體，則會出現一個對話方塊，其中包含下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="a670b-150">If you attempt to create an instance of a BizTalk host on a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer that is unavailable, a dialog box with the following error message is displayed:</span></span>  
  
 <span data-ttu-id="a670b-151">安裝主控件 instace \<*主機名稱*\>伺服器上\<*伺服器名稱*\>失敗。</span><span class="sxs-lookup"><span data-stu-id="a670b-151">Installation of instace of host \<*host name*\> on server \<*server name*\> failed.</span></span>  
  
 <span data-ttu-id="a670b-152">其他資訊：</span><span class="sxs-lookup"><span data-stu-id="a670b-152">Additional information:</span></span>  
  
 <span data-ttu-id="a670b-153">RPC 伺服器無法使用。</span><span class="sxs-lookup"><span data-stu-id="a670b-153">The RPC server is unavailable.</span></span> <span data-ttu-id="a670b-154">(WinMgmt)</span><span class="sxs-lookup"><span data-stu-id="a670b-154">(WinMgmt)</span></span>  
  
 <span data-ttu-id="a670b-155">當您按一下 [確定] 關閉此對話方塊時，會顯示一個對話方塊，其中包含下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="a670b-155">When you click OK to dismiss the dialog box, a dialog box with the following error message is displayed:</span></span>  
  
 <span data-ttu-id="a670b-156">清除已完成中止的主機安裝\<*主機名稱*\>伺服器上\<*伺服器名稱*\>失敗。</span><span class="sxs-lookup"><span data-stu-id="a670b-156">Cleaning up aborted installation of host \<*host name*\> on server \<*server name*\> failed.</span></span>  
  
 <span data-ttu-id="a670b-157">其他資訊：</span><span class="sxs-lookup"><span data-stu-id="a670b-157">Additional information:</span></span>  
  
 <span data-ttu-id="a670b-158">發生失敗時刪除 Windows NT 服務 BTSSvc {*\<GUID\>*}。</span><span class="sxs-lookup"><span data-stu-id="a670b-158">A failure occurred when deleting the Windows NT service BTSSvc{*\<GUID\>*}.</span></span> <span data-ttu-id="a670b-159">(WinMgmt)</span><span class="sxs-lookup"><span data-stu-id="a670b-159">(WinMgmt)</span></span>  
  
 <span data-ttu-id="a670b-160">當您按一下**確定**若要關閉此對話方塊中，BizTalk 主控件執行個體便會顯示在 BizTalk 管理主控台與**狀態**的**Uninstall 失敗**.</span><span class="sxs-lookup"><span data-stu-id="a670b-160">When you click **OK** to dismiss this dialog box, the instance of the BizTalk host will be visible in the BizTalk Administration Console with a **Status** of **Uninstall failed**.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="a670b-161">原因</span><span class="sxs-lookup"><span data-stu-id="a670b-161">Cause</span></span>  
 <span data-ttu-id="a670b-162">當建立主控件執行個體時，會在 BizTalk 管理資料庫中產生一個項目，然後才會將此主控件執行個體安裝到指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上。</span><span class="sxs-lookup"><span data-stu-id="a670b-162">When a host instance is created, an entry is made in the BizTalk Management database before the host instance is installed onto the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span> <span data-ttu-id="a670b-163">如果在指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上安裝此主控件執行個體失敗，則 BizTalk 管理程式將會嘗試解除安裝此主控件執行個體，但是因為無法使用指定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦，所以解除安裝也會失敗。</span><span class="sxs-lookup"><span data-stu-id="a670b-163">If the installation of the host instance onto the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer fails, the BizTalk Administration program will attempt to uninstall the host instance but since the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer is unavailable the uninstall fails as well.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="a670b-164">解決方案</span><span class="sxs-lookup"><span data-stu-id="a670b-164">Resolution</span></span>  
 <span data-ttu-id="a670b-165">如果狀態為 「 BizTalk 管理主控台中建立 BizTalk 主控件執行個體**Uninstall 失敗**、 刪除主控件執行個體和指定的 BizTalk Server 電腦變成可用之後重新建立主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a670b-165">If a BizTalk host instance is created in the BizTalk Admininstration Console with a status of **Uninstall failed**, delete the host instance and recreate the host instance after the designated BizTalk Server computer becomes available.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a670b-166">如果使用 BizTalk 管理主控台中建立 BizTalk 主控件執行個體**狀態**的**Uninstall 失敗**主控件執行個體將無法正常運作即使指定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦再次變為無法使用。</span><span class="sxs-lookup"><span data-stu-id="a670b-166">If a BizTalk host instance is created in the BizTalk Administration Console with a **Status** of **Uninstall failed** the host instance will not be functional even after the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer becomes available again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a670b-167">請參閱</span><span class="sxs-lookup"><span data-stu-id="a670b-167">See Also</span></span>  
 <span data-ttu-id="a670b-168">[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="a670b-168">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="a670b-169">[啟動主控件執行個體](../core/how-to-start-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="a670b-169">[Start a Host Instance](../core/how-to-start-a-host-instance.md) </span></span>  
 <span data-ttu-id="a670b-170">[停止主控件執行個體](../core/how-to-stop-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="a670b-170">[Stop a Host Instance](../core/how-to-stop-a-host-instance.md) </span></span>  
 <span data-ttu-id="a670b-171">[刪除主控件執行個體](../core/how-to-delete-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="a670b-171">[Delete a Host Instance](../core/how-to-delete-a-host-instance.md) </span></span>  
 [<span data-ttu-id="a670b-172">修改主控件執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="a670b-172">Modify Host Instance Properties</span></span>](../core/how-to-modify-host-instance-properties.md)