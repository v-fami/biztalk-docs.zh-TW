---
title: "如何移動主要密碼伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], migrating
- migrating, Master Secret server
- Master Secret server, migrating
ms.assetid: 2bc5137e-f81d-486d-bb91-7c5981896f79
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b35fae6551a95c1c2009ac9786aa791d189f338
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-master-secret-server"></a><span data-ttu-id="eea79-102">如何移動主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="eea79-102">How to Move the Master Secret Server</span></span>
<span data-ttu-id="eea79-103">您可以遵循本主題所說明的步驟，將某一部伺服器上的主要密碼移動到另一部伺服器，以及將伺服器上的主要密碼移動到「Windows 伺服器叢集」。</span><span class="sxs-lookup"><span data-stu-id="eea79-103">This topic documents the steps you can follow to move the master secret from one server to another and the steps you can follow to move the master secret from one server to a Windows Server Cluster.</span></span>  
  
### <a name="to-move-the-master-secret-from-one-server-to-another-server"></a><span data-ttu-id="eea79-104">將某一部伺服器上的主要密碼移動到另一部伺服器</span><span class="sxs-lookup"><span data-stu-id="eea79-104">To move the master secret from one server to another server</span></span>  
  
1.  <span data-ttu-id="eea79-105">若尚未在新的主要密碼伺服器上安裝「Microsoft 企業單一登入」(SSO) 伺服器，請先安裝。</span><span class="sxs-lookup"><span data-stu-id="eea79-105">Install Microsoft Enterprise Single Sign-On (SSO) Server on the new master secret server if it is not already installed.</span></span> <span data-ttu-id="eea79-106">從 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] CD 上的 \Platform\SSO\setup.exe 啟動 Microsoft 企業單一登入伺服器的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="eea79-106">Launch Microsoft Enterprise Single Sign-On Server setup from \Platform\SSO\setup.exe on the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] CD.</span></span>  
  
2.  <span data-ttu-id="eea79-107">若尚未在新的主要密碼伺服器上設定「企業單一登入」，請先設定。</span><span class="sxs-lookup"><span data-stu-id="eea79-107">Configure Enterprise SSO on the new master secret server if it is not already configured.</span></span> <span data-ttu-id="eea79-108">依照下列步驟來設定「企業單一登入」：</span><span class="sxs-lookup"><span data-stu-id="eea79-108">Follow these steps to configure Enterprise SSO:</span></span>  
  
    1.  <span data-ttu-id="eea79-109">開啟組態工具。</span><span class="sxs-lookup"><span data-stu-id="eea79-109">Open the Configuration tool.</span></span> <span data-ttu-id="eea79-110">根據預設，組態工具位於\<磁碟機 >: \Program Files\Common Files\Enterprise Single On\Configuration.exe。</span><span class="sxs-lookup"><span data-stu-id="eea79-110">By default, the configuration tool is located at \<drive>:\Program Files\Common Files\Enterprise Single Sign-On\Configuration.exe.</span></span>  
  
    2.  <span data-ttu-id="eea79-111">按一下以選取**企業單一登入**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="eea79-111">Click to select **Enterprise SSO** in the left pane.</span></span>  
  
    3.  <span data-ttu-id="eea79-112">選取此核取方塊旁的 **啟用企業單一登入此電腦上**右窗格中。</span><span class="sxs-lookup"><span data-stu-id="eea79-112">Select the check box next to **Enable Enterprise Single Sign-On on this computer** in the right pane.</span></span>  
  
    4.  <span data-ttu-id="eea79-113">按一下選項以**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="eea79-113">Click the option to **Join an existing SSO System**.</span></span>  
  
    5.  <span data-ttu-id="eea79-114">指定現有**伺服器名稱**和**資料庫名稱**為 SSO 資料庫選項。</span><span class="sxs-lookup"><span data-stu-id="eea79-114">Specify the existing **Server Name** and **Database Name** for the SSO database options.</span></span>  
  
    6.  <span data-ttu-id="eea79-115">指定現有的企業單一登入服務帳戶的**企業單一登入伺服器 Windows 服務**選項。</span><span class="sxs-lookup"><span data-stu-id="eea79-115">Specify the existing Enterprise SSO service account for the **Enterprise Single Sign-On Server for the Windows Service** option.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="eea79-116">這必須是一個網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="eea79-116">This must be a domain account.</span></span>  
  
    7.  <span data-ttu-id="eea79-117">按一下選項以**套用組態**按一下**設定**在組態精靈 對話方塊，以完成設定。</span><span class="sxs-lookup"><span data-stu-id="eea79-117">Click the option to **Apply Configuration** and click **Configure** in the Configuration Wizard dialog box to complete the configuration.</span></span>  
  
    8.  <span data-ttu-id="eea79-118">按一下**完成**並關閉 組態工具。</span><span class="sxs-lookup"><span data-stu-id="eea79-118">Click **Finish** and close the Configuration tool.</span></span>  
  
3.  <span data-ttu-id="eea79-119">備份現有的主要密碼中的步驟[如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="eea79-119">Back up the existing master secret following the steps in [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span></span>  
  
4.  <span data-ttu-id="eea79-120">將 SSO 資料庫中的主要密碼伺服器變更為參照新的主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="eea79-120">Change the master secret server name in the SSO database to reference the new master secret server.</span></span> <span data-ttu-id="eea79-121">例如，新的主要密碼伺服器的名稱可能**NewMSSServer**。</span><span class="sxs-lookup"><span data-stu-id="eea79-121">For example, the name of the new master secret server may be **NewMSSServer**.</span></span> <span data-ttu-id="eea79-122">若要這樣做，請在原始主要密碼伺服器上遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="eea79-122">To do this, follow these steps on the original master secret server:</span></span>  
  
    1.  <span data-ttu-id="eea79-123">將下列程式碼貼在文字編輯器 (如 notepad.exe) 中：</span><span class="sxs-lookup"><span data-stu-id="eea79-123">Paste the following code in a text editor such as notepad.exe:</span></span>  
  
        ```  
        <sso>  
        <globalInfo>  
        <secretServer>NewMSSServer</secretServer>  
        </globalInfo>  
        </sso>  
        ```  
  
    2.  <span data-ttu-id="eea79-124">將檔案儲存為 .xml 檔。</span><span class="sxs-lookup"><span data-stu-id="eea79-124">Save the file as .xml file.</span></span> <span data-ttu-id="eea79-125">例如，將檔案儲存為**NewMSSServer.xml**。</span><span class="sxs-lookup"><span data-stu-id="eea79-125">For example, save the file as **NewMSSServer.xml**.</span></span>  
  
    3.  <span data-ttu-id="eea79-126">在命令提示字元，變更為「企業單一登入」安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="eea79-126">At a command prompt, change to the Enterprise SSO installation folder.</span></span> <span data-ttu-id="eea79-127">根據預設，安裝資料夾是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="eea79-127">By default, the installation folder is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
    4.  <span data-ttu-id="eea79-128">型別**ssomanage-updatedb** *XMLFile*來更新資料庫中的主要密碼伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="eea79-128">Type **ssomanage -updatedb** *XMLFile* to update the master secret server name in the database.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="eea79-129">取代*XMLFile*您儲存的.xml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="eea79-129">Replace *XMLFile* with the name of the .xml file that you saved.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="eea79-130">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="eea79-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="eea79-131">在新的主要密碼伺服器上重新啟動「企業單一登入」服務。</span><span class="sxs-lookup"><span data-stu-id="eea79-131">Restart the Enterprise Single Sign-On service on the new master secret server.</span></span>  
  
6.  <span data-ttu-id="eea79-132">請依照下列中的步驟還原到新的主要密碼伺服器上備份主要密碼[如何還原主要密碼](../core/how-to-restore-the-master-secret.md)新的主要密碼伺服器上。</span><span class="sxs-lookup"><span data-stu-id="eea79-132">Restore the backed-up master secret onto the new master secret server by following the steps in [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md) on the new master secret server.</span></span>  
  
### <a name="to-move-the-master-secret-from-one-server-to-a-windows-server-cluster"></a><span data-ttu-id="eea79-133">將伺服器上的主要密碼移動到 Windows 伺服器叢集</span><span class="sxs-lookup"><span data-stu-id="eea79-133">To move the master secret from one server to a Windows Server Cluster</span></span>  
  
1.  <span data-ttu-id="eea79-134">安裝和設定 Windows Server 叢集上的企業單一登入服務的中的步驟[如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)。</span><span class="sxs-lookup"><span data-stu-id="eea79-134">Install and configure the Enterprise SSO service on a Windows Server cluster by following the steps in [How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md).</span></span> <span data-ttu-id="eea79-135">完成所有步驟，本主題中所述的步驟除了**還原第二個叢集節點上的主要密碼**> 一節。</span><span class="sxs-lookup"><span data-stu-id="eea79-135">Complete all of the steps in this topic except for the steps described in the **Restore the master secret on the second cluster node** section.</span></span> <span data-ttu-id="eea79-136">您將會移動現有的主要密碼伺服器叢集因為未選擇選項以**建立新的 SSO 系統**設定企業單一登入叢集節點上時。</span><span class="sxs-lookup"><span data-stu-id="eea79-136">Since you will be moving the existing master secret server to the cluster do not choose the option to **Create a new SSO system** when configuring Enterprise SSO on the cluster nodes.</span></span> <span data-ttu-id="eea79-137">在設定每個叢集節點時，請在 BizTalk Server 組態程式中設定下列企業 SSO 功能的選項：</span><span class="sxs-lookup"><span data-stu-id="eea79-137">When configuring each cluster node, set the following options for the Enterprise SSO feature in the BizTalk Server Configuration program:</span></span>  
  
    1.  <span data-ttu-id="eea79-138">核取方塊旁的 **啟用企業單一登入此電腦上**。</span><span class="sxs-lookup"><span data-stu-id="eea79-138">Check the box next to **Enable Enterprise Single Sign-On on this computer**.</span></span>  
  
    2.  <span data-ttu-id="eea79-139">按一下選項以**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="eea79-139">Click the option to **Join an existing SSO system**.</span></span>  
  
    3.  <span data-ttu-id="eea79-140">為現有的 SSO 資料庫伺服器名稱和資料庫名稱輸入值。</span><span class="sxs-lookup"><span data-stu-id="eea79-140">Enter values for the existing SSO Database Server Name and Database Name.</span></span>  
  
    4.  <span data-ttu-id="eea79-141">在指定「企業單一登入」服務使用的帳戶時，輸入現有的 SSO 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="eea79-141">Enter the existing SSO Service account when specifying the account to use for the Enterprise Single Sign-On Service.</span></span>  
  
2.  <span data-ttu-id="eea79-142">將現有的主要密碼備份檔案複製到每個叢集節點上的 \Enterprise Single Sign-On 資料夾。</span><span class="sxs-lookup"><span data-stu-id="eea79-142">Copy the existing master secret backup file to the \Enterprise Single Sign-On folder on each cluster node.</span></span>  
  
3.  <span data-ttu-id="eea79-143">如果此 Windows Server 叢集將裝載一或多個叢集 BizTalk 主控件，請使用 ssomanage 命令列公用程式，將所有使用者的 SSO 伺服器名稱設定為叢集的主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="eea79-143">If this Windows Server Cluster will host one or more clustered BizTalk hosts, set the SSO Server name for all users to the clustered master secret server with the ssomanage command line utility.</span></span> <span data-ttu-id="eea79-144">此命令應該會從群組中每個 BizTalk Server 的企業 SSO 安裝資料夾執行。</span><span class="sxs-lookup"><span data-stu-id="eea79-144">This command should be run from the Enterprise SSO installation folder on each BizTalk Server in the group.</span></span> <span data-ttu-id="eea79-145">例如，以下的命令列會將所有使用者的 SSO 伺服器名稱設定為叢集式的主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="eea79-145">For example, the following command line will set the SSO Server name for all users to the clustered master secret server:</span></span>  
  
    ```  
    ssomanage -serverall SSOCLUSTER  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="eea79-146">*SSOCLUSTER*實際網路名稱資源的預留位置，在含有叢集主要密碼伺服器資源的叢集群組中建立這種情況下，所有 BizTalk 主控件必須都建立為在相同的叢集資源叢集 「 企業單一登入 」 服務資源的叢集群組。</span><span class="sxs-lookup"><span data-stu-id="eea79-146">*SSOCLUSTER* is a placeholder for the actual network name resource that is created in the cluster group that contains the clustered master secret server resourceIn this scenario, all BizTalk hosts must be created as cluster resources in the same cluster group as the clustered Enterprise SSO service resource.</span></span> <span data-ttu-id="eea79-147">在已叢集化「企業單一登入」服務的 Windows Server 叢集節點上執行非叢集 BizTalk 主控件執行個體，並不是支援的組態。</span><span class="sxs-lookup"><span data-stu-id="eea79-147">Running a non-clustered BizTalk host instance on a Windows Server Cluster node where the Enterprise SSO service is clustered is not a supported configuration.</span></span> <span data-ttu-id="eea79-148">這是因為非叢集 BizTalk 主控件執行個體將在已叢集化的「企業單一登入」服務容錯移轉至另一個節點時，因為 BizTalk 主控件執行個體對單一登入服務的相依性而失敗。</span><span class="sxs-lookup"><span data-stu-id="eea79-148">This is because the non-clustered BizTalk host instance will fail when the clustered Enterprise SSO service is failed over to another node due to the dependency of a BizTalk host instance on the SSO service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eea79-149">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="eea79-149">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="eea79-150">在 叢集系統管理員，以滑鼠右鍵按一下包含叢集 「 企業單一登入服務資源，叢集群組，然後按一下**上線**以啟動叢集群組中所有的資源。</span><span class="sxs-lookup"><span data-stu-id="eea79-150">In Cluster Administrator, right-click the cluster group that contains the clustered Enterprise SSO service resource, and click **Bring Online** to start all of the resources in the cluster group.</span></span>  
  
5.  <span data-ttu-id="eea79-151">如果此 Windows Server 叢集將裝載一或多個叢集 BizTalk 主控件，更新 SSO 伺服器名稱存取**BizTalk 群組屬性**頁面，即可參考叢集的主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="eea79-151">If this Windows Server Cluster will host one or more clustered BizTalk hosts, update the SSO Server name accessible in the **BizTalk Group Properties** page to reference the clustered master secret server.</span></span> <span data-ttu-id="eea79-152">啟動**BizTalk Server 管理**，以滑鼠右鍵按一下 BizTalk 群組，然後選取**屬性**功能表項目，然後更新的項目**SSO 伺服器名稱**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="eea79-152">Launch **BizTalk Server Administration**, right-click the BizTalk Group and select the **Properties** menu item, then update the entry for **SSO Server name** and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eea79-153">在此實例中，所有 BizTalk 主控件都必須建立為與叢集化「企業單一登入」服務資源位於相同叢集群組中的叢集資源。</span><span class="sxs-lookup"><span data-stu-id="eea79-153">In this scenario, all BizTalk hosts must be created as cluster resources in the same cluster group as the clustered Enterprise SSO service resource.</span></span> <span data-ttu-id="eea79-154">在已叢集化「企業單一登入」服務的 Windows Server 叢集節點上執行非叢集 BizTalk 主控件執行個體，並不是支援的組態。</span><span class="sxs-lookup"><span data-stu-id="eea79-154">Running a non-clustered BizTalk host instance on a Windows Server Cluster node where the Enterprise SSO service is clustered is not a supported configuration.</span></span> <span data-ttu-id="eea79-155">這是因為非叢集 BizTalk 主控件執行個體將在已叢集化的「企業單一登入」服務容錯移轉至另一個節點時，因為 BizTalk 主控件執行個體對單一登入服務的相依性而失敗。</span><span class="sxs-lookup"><span data-stu-id="eea79-155">This is because the non-clustered BizTalk host instance will fail when the clustered Enterprise SSO service is failed over to another node due to the dependency of a BizTalk host instance on the SSO service.</span></span>  
  
6.  <span data-ttu-id="eea79-156">以滑鼠右鍵按一下企業 SSO 服務的叢集執行個體，然後按一下**離線**、 以滑鼠右鍵按一下企業 SSO 服務的叢集執行個體，然後按一下 **上線**。</span><span class="sxs-lookup"><span data-stu-id="eea79-156">Right-click the clustered instance of the Enterprise SSO service and click **Take Offline**, then right-click the clustered instance of the Enterprise SSO service and click **Bring Online**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eea79-157">如果此步驟未完成，嘗試還原主要密碼可能不會成功。</span><span class="sxs-lookup"><span data-stu-id="eea79-157">If this step is not completed, attempts to restore the master secret may not succeed.</span></span>  
  
7.  <span data-ttu-id="eea79-158">在含有叢集式主要密碼伺服器之 Windows 叢集的各個節點上復原備份的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="eea79-158">Restore the backed-up master secret on each node of the Windows cluster that houses the clustered master secret server.</span></span> <span data-ttu-id="eea79-159">請依照[如何還原主要密碼](../core/how-to-restore-the-master-secret.md)含有叢集主要密碼伺服器的 Windows 叢集的每個節點上。</span><span class="sxs-lookup"><span data-stu-id="eea79-159">Follow the steps in [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md) on each node of the Windows cluster that houses the clustered master secret server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea79-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eea79-160">See Also</span></span>  
 [<span data-ttu-id="eea79-161">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="eea79-161">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)