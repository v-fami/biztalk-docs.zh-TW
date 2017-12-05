---
title: "如何叢集化主要密碼 Server1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, second node
- Master Secret server, restoring
- clustering, Master Secret server
- Master Secret server, clustering
ms.assetid: ef817fa4-e43d-4e3d-8686-5bd675708001
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9740bb1c73dd5f416dda3c2f29bb15fbc7241a51
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-cluster-the-master-secret-server"></a><span data-ttu-id="0ff74-102">如何叢集化主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="0ff74-102">How to Cluster the Master Secret Server</span></span>
<span data-ttu-id="0ff74-103">我們建議您依照本節的指示，在主要密碼伺服器上對「企業單一登入」(SSO) 服務進行成功的叢集化處理。</span><span class="sxs-lookup"><span data-stu-id="0ff74-103">We recommended that you follow the instructions in this section to cluster the Enterprise Single Sign-On (SSO) service on the master secret server successfully.</span></span>  
  
 <span data-ttu-id="0ff74-104">當您對主要密碼伺服器進行叢集化時，「單一登入」伺服器會與主要密碼伺服器的作用中叢集執行個體通訊。</span><span class="sxs-lookup"><span data-stu-id="0ff74-104">When you cluster the master secret server, the Single Sign-On servers communicate with the active clustered instance of the master secret server.</span></span> <span data-ttu-id="0ff74-105">同樣的，主要密碼伺服器的作用中叢集執行個體也會與 SSO 資料庫通訊。</span><span class="sxs-lookup"><span data-stu-id="0ff74-105">Similarly, the active clustered instance of the master secret server communicates with the SSO database.</span></span>  
  
 <span data-ttu-id="0ff74-106">您必須是 SSO 系統管理員，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="0ff74-106">You must be an SSO administrator to perform this procedure.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="0ff74-107">您不能在「網路負載平衡」(NLB) 叢集上安裝主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="0ff74-107">You cannot install the master secret server on a Network Load Balancing (NLB) cluster.</span></span>  
  
### <a name="to-install-and-configure-enterprise-sso-on-the-cluster-nodes"></a><span data-ttu-id="0ff74-108">在叢集節點上安裝和設定企業單一登入</span><span class="sxs-lookup"><span data-stu-id="0ff74-108">To install and configure Enterprise SSO on the cluster nodes</span></span>  
  
1.  <span data-ttu-id="0ff74-109">在每個叢集節點上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0ff74-109">Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on each cluster node.</span></span> <span data-ttu-id="0ff74-110">在**元件安裝**，選取**企業單一登入管理模組**和**企業單一登入主要密碼伺服器**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-110">In **Component Installation**, select **Enterprise Single Sign-On Administration Module** and **Enterprise Single Sign-On Master Secret Server**.</span></span> <span data-ttu-id="0ff74-111">已順利完成安裝之後，請執行**不**執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。</span><span class="sxs-lookup"><span data-stu-id="0ff74-111">After installation has completed successfully, do **not** run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span></span>  
  
2.  <span data-ttu-id="0ff74-112">建立**SSO 系統管理員**和**SSO 分支機構系統管理員**網域群組。</span><span class="sxs-lookup"><span data-stu-id="0ff74-112">Create **SSO Administrators** and **SSO Affiliate Administrators** domain groups.</span></span> <span data-ttu-id="0ff74-113">若要建立企業單一登入服務的叢集執行個體，您必須建立這些群組，做為網域群組。</span><span class="sxs-lookup"><span data-stu-id="0ff74-113">To create a clustered instance of the Enterprise SSO service, you must create these groups as domain groups.</span></span>  
  
3.  <span data-ttu-id="0ff74-114">建立或指定成員的網域帳戶**SSO 系統管理員**網域群組。</span><span class="sxs-lookup"><span data-stu-id="0ff74-114">Create or designate a domain account that is a member of the **SSO Administrators** domain group.</span></span> <span data-ttu-id="0ff74-115">每個節點上的企業單一登入服務設定為以網域帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="0ff74-115">The Enterprise SSO service on each node is configured to log on as this domain account.</span></span> <span data-ttu-id="0ff74-116">此帳戶必須具有**以服務方式登入**叢集中的每個節點上的權限。</span><span class="sxs-lookup"><span data-stu-id="0ff74-116">This account must have the **Log on as a service** right on each node in the cluster.</span></span>  
  
4.  <span data-ttu-id="0ff74-117">新增的帳戶，您用來登入加入網域的設定程序期間**SSO 系統管理員**群組。</span><span class="sxs-lookup"><span data-stu-id="0ff74-117">Add the account that you are using to log on during the configuration process to the domain **SSO Administrators** group.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0ff74-118">如果未完成步驟 3 和 4，企業單一登入服務的組態將會失敗。</span><span class="sxs-lookup"><span data-stu-id="0ff74-118">Configuration of the Enterprise SSO service fails if steps 3 and 4 are not completed.</span></span>  
  
5.  <span data-ttu-id="0ff74-119">啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。</span><span class="sxs-lookup"><span data-stu-id="0ff74-119">Start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span></span>  
  
6.  <span data-ttu-id="0ff74-120">選取**自訂組態**選項，然後輸入**資料庫伺服器名稱**，**使用者名**，和**密碼**值。</span><span class="sxs-lookup"><span data-stu-id="0ff74-120">Select **Custom Configuration** option and enter the **Database server name**, **User name**, and **Password** values.</span></span> <span data-ttu-id="0ff74-121">選取**設定**才能繼續。</span><span class="sxs-lookup"><span data-stu-id="0ff74-121">Select **Configure** to continue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0ff74-122">因為您只會設定企業單一登入服務，此時，您只需輸入您稍早在此建立的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="0ff74-122">Since you are only be configuring the Enterprise SSO service at this time, you can just enter the domain account that you created earlier here.</span></span>  
  
7.  <span data-ttu-id="0ff74-123">選取**企業單一登入**從左窗格的選項，以及設定 「 企業單一登入 」 功能的下列選項：</span><span class="sxs-lookup"><span data-stu-id="0ff74-123">Select the **Enterprise SSO** option from the left pane and set the following options for the Enterprise SSO feature:</span></span>  
  
    1.  <span data-ttu-id="0ff74-124">選取**啟用企業單一登入此電腦上**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0ff74-124">Select the **Enable Enterprise Single Sign-On on this computer** check box.</span></span>  
  
    2.  <span data-ttu-id="0ff74-125">選取**建立新的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-125">Select **Create a new SSO system**.</span></span>  
  
    3.  <span data-ttu-id="0ff74-126">輸入**資料存放區**如**伺服器名稱**和**資料庫名稱**值。</span><span class="sxs-lookup"><span data-stu-id="0ff74-126">Enter the **Data stores** for **Server Name** and **Database Name** values.</span></span>  
  
    4.  <span data-ttu-id="0ff74-127">確認您稍早建立的網域帳戶是與「企業單一登入」服務相關聯的帳戶。</span><span class="sxs-lookup"><span data-stu-id="0ff74-127">Verify that the domain account that you created earlier is the account that is associated with the Enterprise SSO service.</span></span>  
  
    5.  <span data-ttu-id="0ff74-128">輸入您稍早為 SSO 系統管理員 」 角色相關聯的群組建立的網域 SSO 系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="0ff74-128">Enter the domain SSO Administrators group that you created earlier as the group associated with the SSO Administrator(s) role.</span></span>  
  
    6.  <span data-ttu-id="0ff74-129">輸入您稍早為 SSO 分支機構系統管理員 」 角色相關聯的群組建立的網域 SSO 分支機構系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="0ff74-129">Enter the domain SSO Affiliate Administrators group that you created earlier as the group associated with the SSO Affiliate Administrator(s) role.</span></span>  
  
8.  <span data-ttu-id="0ff74-130">選取**企業單一登入密碼備份**選項從左窗格，並提供適當的參數來備份企業單一登入密碼。</span><span class="sxs-lookup"><span data-stu-id="0ff74-130">Select the **Enterprise SSO Secret Backup** option from the left pane and provide the appropriate parameters for backing up the Enterprise SSO secret.</span></span> <span data-ttu-id="0ff74-131">根據預設，企業單一登入密碼備份至*\<磁碟機\>*: Files\Enterprise Single Sign-on \Program Files\Common\\*SSOxxxx*.bak。</span><span class="sxs-lookup"><span data-stu-id="0ff74-131">By default, the Enterprise SSO secret is backed up to *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On\\*SSOxxxx*.bak.</span></span>  
  
9. <span data-ttu-id="0ff74-132">按一下**套用組態**和檢閱摘要。</span><span class="sxs-lookup"><span data-stu-id="0ff74-132">Click the **Apply Configuration** and review the Summary.</span></span>  
  
10. <span data-ttu-id="0ff74-133">按一下**下一步**套用設定。</span><span class="sxs-lookup"><span data-stu-id="0ff74-133">Click **Next** to apply the configuration.</span></span>  
  
11. <span data-ttu-id="0ff74-134">按一下**完成**以關閉 組態精靈。</span><span class="sxs-lookup"><span data-stu-id="0ff74-134">Click **Finish** to close the Configuration wizard.</span></span>  
  
12. <span data-ttu-id="0ff74-135">關閉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。</span><span class="sxs-lookup"><span data-stu-id="0ff74-135">Close the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration.</span></span>  
  
13. <span data-ttu-id="0ff74-136">登入被動叢集節點並開始[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。</span><span class="sxs-lookup"><span data-stu-id="0ff74-136">Log on to the passive cluster node and start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span></span>  
  
14. <span data-ttu-id="0ff74-137">選擇**自訂組態**選項，然後輸入相同的值**資料庫伺服器名稱**，**使用者名**，和**密碼**，您輸入時設定第一個叢集節點。</span><span class="sxs-lookup"><span data-stu-id="0ff74-137">Choose the **Custom Configuration** option and enter the same values for the **Database server name**, **User name**, and **Password** that you entered when configuring the first cluster node.</span></span> <span data-ttu-id="0ff74-138">輸入這些值後, 按一下**設定**才能繼續。</span><span class="sxs-lookup"><span data-stu-id="0ff74-138">After entering these values, click **Configure** to continue.</span></span>  
  
15. <span data-ttu-id="0ff74-139">選取**企業單一登入**從左窗格的選項，以及設定 「 企業單一登入 」 功能的下列選項：</span><span class="sxs-lookup"><span data-stu-id="0ff74-139">Select the **Enterprise SSO** option from the left pane and set the following options for the Enterprise SSO feature:</span></span>  
  
    1.  <span data-ttu-id="0ff74-140">選取**啟用企業單一登入此電腦上**選項。</span><span class="sxs-lookup"><span data-stu-id="0ff74-140">Select the **Enable Enterprise Single Sign-On on this computer** option.</span></span>  
  
    2.  <span data-ttu-id="0ff74-141">選取**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-141">Select **Join an existing SSO system**.</span></span>  
  
    3.  <span data-ttu-id="0ff74-142">輸入的相同值的 SSO 資料庫**伺服器名稱**和**資料庫名稱**您輸入時設定第一個叢集節點。</span><span class="sxs-lookup"><span data-stu-id="0ff74-142">Enter the same values for the SSO Database **Server Name** and **Database Name** that you entered when configuring the first cluster node.</span></span>  
  
    4.  <span data-ttu-id="0ff74-143">為網域帳戶輸入您在設定第一個叢集節點時所輸入的相同值。</span><span class="sxs-lookup"><span data-stu-id="0ff74-143">Enter the same value for the domain account that you entered when configuring the first cluster node.</span></span>  
  
16. <span data-ttu-id="0ff74-144">選取**套用組態**顯示摘要。</span><span class="sxs-lookup"><span data-stu-id="0ff74-144">Select **Apply Configuration** to display the Summary.</span></span>  
  
17. <span data-ttu-id="0ff74-145">選取**下一步**套用設定。</span><span class="sxs-lookup"><span data-stu-id="0ff74-145">Select **Next** to apply the configuration.</span></span>  
  
18. <span data-ttu-id="0ff74-146">選取**完成**以關閉 組態精靈。</span><span class="sxs-lookup"><span data-stu-id="0ff74-146">Select **Finish** to close the Configuration wizard.</span></span>  
  
19. <span data-ttu-id="0ff74-147">關閉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。</span><span class="sxs-lookup"><span data-stu-id="0ff74-147">Close the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.</span></span>  
  
### <a name="to-update-the-master-secret-server-name-in-the-sso-database"></a><span data-ttu-id="0ff74-148">若要更新在 SSO 資料庫中的主要密碼伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="0ff74-148">To update the master secret server name in the SSO database</span></span>  
  
1.  <span data-ttu-id="0ff74-149">從命令提示字元，對主動叢集節點輸入下列命令，以停止和重新啟動「企業單一登入」服務：</span><span class="sxs-lookup"><span data-stu-id="0ff74-149">Type the following commands from a command prompt on the active cluster node to stop and restart the Enterprise SSO service:</span></span>  
  
    ```  
    net stop entsso  
    ```  
  
     <span data-ttu-id="0ff74-150">和</span><span class="sxs-lookup"><span data-stu-id="0ff74-150">and</span></span>  
  
    ```  
    net start entsso  
    ```  
  
2.  <span data-ttu-id="0ff74-151">請依照以下步驟執行，將 SSO 資料庫中的主要密碼伺服器名稱變更為叢集名稱：</span><span class="sxs-lookup"><span data-stu-id="0ff74-151">Change the master secret server name in the SSO database to the cluster name by following these steps:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0ff74-152">叢集名稱是定義您要建立叢集的網路名稱資源的名稱群組 / 叢集服務或將包含叢集 「 企業單一登入 」 服務的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ff74-152">The cluster name is the name defined for the network name resource that you have created in the cluster group / clustered service or application that will contain the clustered Enterprise SSO service.</span></span> <span data-ttu-id="0ff74-153">例如，此名稱可能是*BIZTALKCLUSTER*。</span><span class="sxs-lookup"><span data-stu-id="0ff74-153">For example, the name may be *BIZTALKCLUSTER*.</span></span>  
  
    1.  <span data-ttu-id="0ff74-154">將下列程式碼貼在文字編輯器中：</span><span class="sxs-lookup"><span data-stu-id="0ff74-154">Paste the following code in a text editor:</span></span>  
  
        ```  
        <sso>  
          <globalInfo>  
            <secretServer>BIZTALKCLUSTER</secretServer>  
          </globalInfo>  
        </sso>  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="0ff74-155">*BIZTALKCLUSTER*是叢集中建立實際網路名稱資源的預留位置群組 / 叢集服務或應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ff74-155">*BIZTALKCLUSTER* is a placeholder for the actual network name resource that is created in the cluster group / clustered service or application.</span></span>  
  
    2.  <span data-ttu-id="0ff74-156">將檔案儲存為.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="0ff74-156">Save the file as an .xml file.</span></span> <span data-ttu-id="0ff74-157">例如，將檔案儲存為 SSOCLUSTER.xml。</span><span class="sxs-lookup"><span data-stu-id="0ff74-157">For example, save the file as SSOCLUSTER.xml.</span></span>  
  
    3.  <span data-ttu-id="0ff74-158">在命令提示字元，變更為「企業單一登入」安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="0ff74-158">At a command prompt, change to the Enterprise SSO installation folder.</span></span> <span data-ttu-id="0ff74-159">根據預設，安裝資料夾是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="0ff74-159">By default, the installation folder is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
    4.  <span data-ttu-id="0ff74-160">在命令提示字元輸入下列命令，以更新資料庫中的主要密碼伺服器名稱：</span><span class="sxs-lookup"><span data-stu-id="0ff74-160">Type the following command at the command prompt to update the master secret server name in the database:</span></span>  
  
        ```  
        ssomanage -updatedb XMLFile  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="0ff74-161">*XMLFile*是您稍早儲存的.xml 檔案名稱的預留位置。</span><span class="sxs-lookup"><span data-stu-id="0ff74-161">*XMLFile* is a placeholder for the name of the .xml file that you saved earlier.</span></span>  
  
### <a name="to-create-the-clustered-enterprise-sso-resource"></a><span data-ttu-id="0ff74-162">建立叢集化企業單一登入資源</span><span class="sxs-lookup"><span data-stu-id="0ff74-162">To create the clustered Enterprise SSO resource</span></span>  
  
1.  <span data-ttu-id="0ff74-163">如果未設定叢集與叢集的分散式交易協調器 (MSDTC) 資源遵循 「 改善錯誤中 BizTalk Server 所使用 Windows 伺服器叢集容錯 」 白皮書中的步驟[http://go.microsoft.com/fwlink/ 嗎？LinkId = 69207](http://go.microsoft.com/fwlink/?LinkId=69207)建立叢集的 MSDTC 資源。</span><span class="sxs-lookup"><span data-stu-id="0ff74-163">If the cluster is not configured with a clustered Distributed Transaction Coordinator (MSDTC) resource then follow the steps in the "Improving Fault Tolerance in BizTalk Server by Using a Windows Server Cluster" white paper at [http://go.microsoft.com/fwlink/?LinkId=69207](http://go.microsoft.com/fwlink/?LinkId=69207) to create a clustered MSDTC resource.</span></span>  
  
2.  <span data-ttu-id="0ff74-164">按一下**啟動**，**程式**，**系統管理工具**，然後**容錯移轉叢集管理**啟動容錯移轉叢集管理程式。</span><span class="sxs-lookup"><span data-stu-id="0ff74-164">Click **Start**, **Programs**, **Administrative Tools**, and then **Failover Cluster Management** to start the Failover Cluster Management program.</span></span>  
  
3.  <span data-ttu-id="0ff74-165">在左窗格中，以滑鼠右鍵按一下**容錯移轉叢集管理**按一下**管理叢集**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-165">In the left hand pane, right-click **Failover Cluster Management** and click **Manage a Cluster**.</span></span>  
  
4.  <span data-ttu-id="0ff74-166">在**選取以管理叢集**對話方塊方塊中，輸入叢集，以進行管理，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-166">On the **Select a cluster to manage** dialog box, enter the cluster to be managed and click **OK**.</span></span>  
  
5.  <span data-ttu-id="0ff74-167">在左窗格中，按一下以選取叢集的服務或應用程式中包含 IP 位址與網路名稱資源。</span><span class="sxs-lookup"><span data-stu-id="0ff74-167">In the left hand pane click to select a clustered service or application that contains an IP Address and Network Name resource.</span></span> <span data-ttu-id="0ff74-168">請依照[如何建立使用磁碟、 IP 位址和名稱資源的叢集群組](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md)與 IP 位址和網路名稱資源建立群組，如果不存在。</span><span class="sxs-lookup"><span data-stu-id="0ff74-168">Follow the steps in [How to Create a Cluster Group with a Disk, IP Address, and Name Resource](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md) to create a group with an IP Address and Network Name resource if one does not already exist.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0ff74-169">叢集「企業單一登入」服務不會明確要求在相同群組中使用實體叢集磁碟資源。</span><span class="sxs-lookup"><span data-stu-id="0ff74-169">A clustered Enterprise SSO service does not explicitly require the use of a clustered Physical Disk resource in the same group.</span></span>  
  
6.  <span data-ttu-id="0ff74-170">叢集的服務或應用程式上按一下滑鼠右鍵，指向**將資源加入**，然後按一下**泛型服務**顯示**新增資源精靈**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0ff74-170">Right-click the clustered service or application, point to **Add a resource**, and click **Generic Service** to display the **New Resource Wizard** dialog.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0ff74-171">在**一般服務參數**對話方塊中，如果您沒有按一下以選取**網路名稱作為電腦名稱**核取方塊，SSO 用戶端電腦將會產生類似下列的錯誤時它們請嘗試連絡企業單一登入服務的這個叢集執行個體：</span><span class="sxs-lookup"><span data-stu-id="0ff74-171">In the **Generic Service Parameters** dialog box, if you do not click to select the **Use Network Name for computer name** check box, SSO client computers will generate an error similar to the following when they try to contact this clustered instance of the Enterprise SSO service:</span></span>  
    >   
    >  <span data-ttu-id="0ff74-172">無法擷取主要密碼。</span><span class="sxs-lookup"><span data-stu-id="0ff74-172">Failed to retrieve master secrets.</span></span>  
    >   
    >  <span data-ttu-id="0ff74-173">確認主要密碼伺服器名稱是否正確以及是否可用。</span><span class="sxs-lookup"><span data-stu-id="0ff74-173">Verify that the master secret server name is correct and that it is available.</span></span> <span data-ttu-id="0ff74-174">密碼伺服器名稱： ENTSSO 錯誤碼： 0x800706D9，沒有可從端點對應程式的多個端點。</span><span class="sxs-lookup"><span data-stu-id="0ff74-174">Secret Server Name: ENTSSO Error Code: 0x800706D9, there are no more endpoints available from the endpoint mapper.</span></span>  
  
7.  <span data-ttu-id="0ff74-175">在**選取服務**頁面**新增資源精靈**，按一下以選取**企業單一登入服務**按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-175">On the **Select Service** page of the **New Resource Wizard**, click to select **Enterprise Single Sign-On Service** and click **Next**.</span></span>  
  
8.  <span data-ttu-id="0ff74-176">在**確認**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-176">On the **Confirmation** page click **Next**.</span></span>  
  
9. <span data-ttu-id="0ff74-177">在**摘要**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-177">On the **Summary** page click **Finish**.</span></span> <span data-ttu-id="0ff74-178">「 企業單一登入服務的叢集執行個體將會出現在**其他資源**在中央窗格中**容錯移轉叢集管理**介面。</span><span class="sxs-lookup"><span data-stu-id="0ff74-178">A clustered instance of the Enterprise Single Sign-On Service will appear under **Other Resources** in the center pane of the **Failover Cluster Management** interface.</span></span>  
  
10. <span data-ttu-id="0ff74-179">以滑鼠右鍵按一下 「 企業單一登入服務的叢集執行個體，然後選取**屬性**顯示**企業單一登入服務內容** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0ff74-179">Right-click the clustered instance of the Enterprise Single Sign-On Service and select **Properties** to display the **Enterprise Single Sign-On Service Properties** dialog box.</span></span>  
  
11. <span data-ttu-id="0ff74-180">按一下**相依性** 索引標籤的內容 對話方塊中，然後按一下**插入**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-180">Click the **Dependencies** tab of the properties dialog box and click **Insert**.</span></span>  
  
12. <span data-ttu-id="0ff74-181">按一下下拉式方塊底下**資源**，選取**名稱：**資源，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-181">Click the drop down box under **Resource**, select the **Name:** resource and click **OK**.</span></span>  
  
### <a name="to-restore-the-master-secret-on-the-second-cluster-node"></a><span data-ttu-id="0ff74-182">還原第二個叢集節點上的主要密碼</span><span class="sxs-lookup"><span data-stu-id="0ff74-182">To restore the master secret on the second cluster node</span></span>  
  
1.  <span data-ttu-id="0ff74-183">在容錯移轉叢集管理，以滑鼠右鍵按一下叢集的服務或應用程式中包含叢集 「 企業單一登入 」 服務，然後按一下**將此服務或應用程式上線**以啟動所有中的資源叢集的服務或應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ff74-183">In Failover Cluster Management, right click the clustered service or application that contains the clustered Enterprise Single Sign-On service and then click **Bring this service or application online** to start all of the resources in the clustered service or application.</span></span>  
  
2.  <span data-ttu-id="0ff74-184">叢集的服務或應用程式上按一下滑鼠右鍵，指向**將此服務或應用程式到另一個節點移動**，然後按一下第二個節點。</span><span class="sxs-lookup"><span data-stu-id="0ff74-184">Right-click the clustered service or application, point to **Move this service or application to another node**, and click the second node.</span></span> <span data-ttu-id="0ff74-185">這個步驟會將移動叢集的服務或應用程式中包含叢集的企業單一登入服務的第一個節點從第二個節點。</span><span class="sxs-lookup"><span data-stu-id="0ff74-185">This step moves the clustered service or application that contains the clustered Enterprise Single Sign-On service from the first node to the second node.</span></span>  
  
3.  <span data-ttu-id="0ff74-186">以滑鼠右鍵按一下叢集 「 企業單一登入 」 服務，然後按一下**讓此服務或應用程式離線**、 以滑鼠右鍵按一下企業 SSO 服務的叢集執行個體，然後按一下 **讓此服務或應用程式上線**。</span><span class="sxs-lookup"><span data-stu-id="0ff74-186">Right-click the clustered Enterprise Single Sign-On service and click **Take this service or application offline**, then right-click the clustered instance of the Enterprise SSO service and click **Bring this service or application online**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0ff74-187">如果沒有完成這個步驟，嘗試還原主要密碼可能就無法成功。</span><span class="sxs-lookup"><span data-stu-id="0ff74-187">If this step is not completed the attempt to restore the master secret may not succeed.</span></span>  
  
4.  <span data-ttu-id="0ff74-188">將主要密碼備份檔案從第一個節點複製到第二個節點上的 \Enterprise Single Sign-On 安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="0ff74-188">Copy the master secret backup file from the first node to the \Enterprise Single Sign-On installation folder on the second node.</span></span> <span data-ttu-id="0ff74-189">根據預設，安裝資料夾是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="0ff74-189">By default, the installation folder is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
5.  <span data-ttu-id="0ff74-190">登入第二個節點，然後在命令提示中變更至「企業單一登入」安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="0ff74-190">Log on to the second node and at a command prompt, change to the Enterprise SSO installation folder.</span></span>  
  
6.  <span data-ttu-id="0ff74-191">從命令提示字元輸入下列命令，以還原主要密碼至第二個節點：</span><span class="sxs-lookup"><span data-stu-id="0ff74-191">Type the following command from the command prompt to restore the master secret to the second node:</span></span>  
  
    ```  
    ssoconfig -restoresecret RestoreFile  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0ff74-192">取代*RestoreFile*使用的路徑以及包含主要密碼備份檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ff74-192">Replace *RestoreFile* with the path of and the name of the backup file that contains the master secret.</span></span>  
  
     <span data-ttu-id="0ff74-193">主要密碼儲存在下列位置的登錄中：</span><span class="sxs-lookup"><span data-stu-id="0ff74-193">The master secret is stored in the registry at the following location:</span></span>  
  
     <span data-ttu-id="0ff74-194">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS</span><span class="sxs-lookup"><span data-stu-id="0ff74-194">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS</span></span>  
  
7.  <span data-ttu-id="0ff74-195">將包含叢集化「企業單一登入」服務的叢集化服務或應用程式從此叢集節點移至其他叢集節點，以確保容錯移轉功能運作正常。</span><span class="sxs-lookup"><span data-stu-id="0ff74-195">Move the clustered service or application that contains the clustered Enterprise Single Sign-On service from this cluster node to other cluster node to ensure failover functionality.</span></span> <span data-ttu-id="0ff74-196">接著將叢集群組移回，以確認容錯移轉回復功能也運作正常。</span><span class="sxs-lookup"><span data-stu-id="0ff74-196">Then move the cluster group back to verify fail-back functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff74-197">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ff74-197">See Also</span></span>  
 [<span data-ttu-id="0ff74-198">如何建立使用磁碟、 IP 位址和名稱資源的叢集群組</span><span class="sxs-lookup"><span data-stu-id="0ff74-198">How to Create a Cluster Group with a Disk, IP Address, and Name Resource</span></span>](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md)
