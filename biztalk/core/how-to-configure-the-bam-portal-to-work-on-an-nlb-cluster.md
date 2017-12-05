---
title: "How to Configure NLB 叢集上的工作在 BAM 入口網站 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96c04fde-dc12-42fb-9193-aa74819fe880
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20693f00d536414b44a7577277cf9acd3e5af530
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster"></a><span data-ttu-id="19129-102">如何設定 BAM 入口網站在 NLB 叢集上執行</span><span class="sxs-lookup"><span data-stu-id="19129-102">How to Configure the BAM Portal to Work on an NLB Cluster</span></span>
<span data-ttu-id="19129-103">BAM 入口網站可設定為在網路負載平衡 (NLB) 叢集中使用。</span><span class="sxs-lookup"><span data-stu-id="19129-103">The BAM portal can be configured to work in a network load balancing (NLB) cluster.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="19129-104">BAM 入口網站*只*在 32 位元模式下執行。</span><span class="sxs-lookup"><span data-stu-id="19129-104">BAM Portal *only* runs in 32-bit mode.</span></span> <span data-ttu-id="19129-105">如果在 64 位元電腦上安裝 IIS，請確定在 32 位元模式下啟用 ASP.NET 2.0。</span><span class="sxs-lookup"><span data-stu-id="19129-105">If IIS is installed on a 64-bit machine, then confirm ASP.NET 2.0 is enabled in 32-bit mode.</span></span> <span data-ttu-id="19129-106">若要這樣做，請開啟 IIS 管理員中，開啟**應用程式集區**，選取應用程式集區 (BAMAppPool)，然後按**進階設定**。</span><span class="sxs-lookup"><span data-stu-id="19129-106">To do this, open IIS Manager, open **Application Pool**, select the application pool (BAMAppPool), and then click **Advanced Settings**.</span></span> <span data-ttu-id="19129-107">在 [啟用 32 位元應用程式] 中，選取 [True]。</span><span class="sxs-lookup"><span data-stu-id="19129-107">In **Enable 32-bit applications**, select **True**.</span></span>  
>   
>  <span data-ttu-id="19129-108">如需其他 BAM 入口網站的需求，請參閱[規劃 BAM 入口網站](../core/planning-for-the-bam-portal.md)。</span><span class="sxs-lookup"><span data-stu-id="19129-108">For additional BAM Portal requirements, see [Planning for the BAM Portal](../core/planning-for-the-bam-portal.md).</span></span>  
  
### <a name="to-prepare-to-configure-bam-portal-on-an-nlb-cluster"></a><span data-ttu-id="19129-109">準備在 NLB 叢集上設定 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="19129-109">To prepare to configure BAM portal on an NLB cluster</span></span>  
  
1.  <span data-ttu-id="19129-110">在第一台電腦上安裝並設定入口網站。</span><span class="sxs-lookup"><span data-stu-id="19129-110">Install and configure the portal on the first computer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-111">您只可在第一台電腦上設定入口網站。</span><span class="sxs-lookup"><span data-stu-id="19129-111">You only configure the portal on the first computer.</span></span> <span data-ttu-id="19129-112">您可選擇在叢集中的其他電腦上啟用 BAM 入口網站，但只能在第一台電腦上進行設定。</span><span class="sxs-lookup"><span data-stu-id="19129-112">You have the option of enabling the BAM portal on other the other computers in the cluster, but the configuration is done only on the first computer.</span></span>  
  
2.  <span data-ttu-id="19129-113">將入口網站元件安裝在要包含在 NLB 叢集中的所有電腦上，然後將叢集中的其他電腦加入要設定入口網站之電腦的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="19129-113">Install the portal components on all the computers to be included in the NLB cluster, and then join the other computers in the cluster to the BizTalk group of the computer on which the portal is configured.</span></span> <span data-ttu-id="19129-114">您必須啟用 BizTalk 群組，並加入適當的群組。</span><span class="sxs-lookup"><span data-stu-id="19129-114">You must enable the BizTalk groups and join the appropriate group.</span></span>  
  
3.  <span data-ttu-id="19129-115">選取為安裝入口網站之電腦所設定的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="19129-115">Select the BizTalk Management database configured for the computer on which the portal is installed.</span></span>  
  
4.  <span data-ttu-id="19129-116">建立 NLB 叢集。</span><span class="sxs-lookup"><span data-stu-id="19129-116">Create the NLB cluster.</span></span> <span data-ttu-id="19129-117">如需如何建立和管理網路負載平衡叢集的詳細資訊，請參閱 「 建立和管理網路負載平衡叢集 」 在[http://go.microsoft.com/fwlink/?LinkId=56206](http://go.microsoft.com/fwlink/?LinkId=56206)。</span><span class="sxs-lookup"><span data-stu-id="19129-117">For more information about how to create and manage network load balancing clusters, see "Create and Manage Network Load Balancing Clusters" at [http://go.microsoft.com/fwlink/?LinkId=56206](http://go.microsoft.com/fwlink/?LinkId=56206).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-118">在繼續進行之前，您應確定 NLB 叢集在 BizTalk Server 環境之外運作良好。</span><span class="sxs-lookup"><span data-stu-id="19129-118">You should confirm that your NLB cluster is working properly outside of the BizTalk Server context before continuing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-119">若要設定硬體式 NLB，請參閱硬體供應商的文件。</span><span class="sxs-lookup"><span data-stu-id="19129-119">To set up hardware-based NLB, refer to your hardware provider's documentation.</span></span>  
  
### <a name="to-update-the-bam-configuration-to-reflect-the-location-of-the-cluster"></a><span data-ttu-id="19129-120">更新 BAM 組態以反映叢集位置</span><span class="sxs-lookup"><span data-stu-id="19129-120">To update the BAM configuration to reflect the location of the cluster</span></span>  
  
1.  <span data-ttu-id="19129-121">如何使用 BAM 管理公用程式取得目前的 BAM 組態</span><span class="sxs-lookup"><span data-stu-id="19129-121">Use the BAM Management Utility to get the current BAM configuration.</span></span> <span data-ttu-id="19129-122">若要這樣做，請按一下**啟動**，按一下 **執行**，然後輸入[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm get-config-filename: Myconfig.xml。</span><span class="sxs-lookup"><span data-stu-id="19129-122">To do this, click **Start**, click **Run**, and type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm get-config -FileName:MyConfig.xml.</span></span>  
  
2.  <span data-ttu-id="19129-123">使用 NLB 叢集的名稱取代本機主機名稱。</span><span class="sxs-lookup"><span data-stu-id="19129-123">Replace the local host name with the name of the NLB cluster.</span></span> <span data-ttu-id="19129-124">若要這樣做，請按一下**啟動**，按一下 **執行**，然後輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\MyConfig.xml。</span><span class="sxs-lookup"><span data-stu-id="19129-124">To do this, click **Start**, click **Run**, and type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\MyConfig.xml.</span></span>  
  
3.  <span data-ttu-id="19129-125">(僅限硬體式 NLB) 確認組態檔含有下列項目：</span><span class="sxs-lookup"><span data-stu-id="19129-125">For hardware-based NLB only, verify the configuration file has the following:</span></span>  
  
    ```  
    <GlobalProperty Name="BAMVRoot">  
    http://<NLB IP Address>:portname/BAM</GlobalProperty>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-126">在硬體式 NLB 上更新 BAM 組態時，不需要執行步驟 4 和 5。</span><span class="sxs-lookup"><span data-stu-id="19129-126">Steps 4 and 5 are not necessary when updating the BAM configuration on hardware-based NLB.</span></span>  
  
4.  <span data-ttu-id="19129-127">使用叢集名稱取代電腦名稱 (machinename)，藉以修改下列行以指向 NLB 叢集：</span><span class="sxs-lookup"><span data-stu-id="19129-127">Modify the following line to point to the NLB cluster by replacing the computer name (machinename) with the cluster name:</span></span>  
  
    ```  
    <GlobalProperty Name=" BAMVRoot">  http://machinename:portname/BAM  
    </GlobalProperty>   
    ```  
  
5.  <span data-ttu-id="19129-128">儲存新組態。</span><span class="sxs-lookup"><span data-stu-id="19129-128">Save the new configuration.</span></span> <span data-ttu-id="19129-129">若要這樣做，請按一下**啟動**，按一下**執行**，然後輸入[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm 更新-config-filename: Myconfig.xml。</span><span class="sxs-lookup"><span data-stu-id="19129-129">To do this, click **Start**, click **Run**, and type [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm update-config -FileName:MyConfig.xml.</span></span>  
  
### <a name="to-edit-the-bam-portal-webconfig-file-to-change-the-bammanagementservice-and-queryservice-urls-to-point-to-the-nlb-server-name-note-this-procedure-is-not-necessary-for-hardware-based-nlb"></a><span data-ttu-id="19129-130">編輯 BAM 入口網站的 web.config 檔案，將 BAMmanagementService 和 QueryService 的 URL 變更為指向 NLB 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="19129-130">To edit the BAM portal web.config file to change the BAMmanagementService and QueryService URLs to point to the NLB server name.</span></span> <span data-ttu-id="19129-131">注意： 此程序不需要硬體式 nlb。</span><span class="sxs-lookup"><span data-stu-id="19129-131">Note: This procedure is not necessary for hardware-based NLB.</span></span>  
  
1.  <span data-ttu-id="19129-132">開啟 web.config 檔案，即可使用 [記事本]**啟動**，然後按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="19129-132">Open the web.config file using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="19129-133">修改下列兩行中的電腦名稱 (machinename) 和連接埠名稱，使其指向叢集的名稱：</span><span class="sxs-lookup"><span data-stu-id="19129-133">Modify the following computer name (machinename) and the port name in the following two lines to point to the name of name of the cluster:</span></span>  
  
    ```  
    <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
    <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />   
    ```  
  
3.  <span data-ttu-id="19129-134">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="19129-134">Save the file.</span></span> <span data-ttu-id="19129-135">若要這樣做，請按一下**檔案**，然後按一下 **儲存**記事本 功能表列上。</span><span class="sxs-lookup"><span data-stu-id="19129-135">To do this, click **File**, and then click **Save** on the Notepad menu bar.</span></span>  
  
### <a name="to-configure-each-additional-computer-in-the-cluster"></a><span data-ttu-id="19129-136">設定叢集中的其他電腦</span><span class="sxs-lookup"><span data-stu-id="19129-136">To configure each additional computer in the cluster</span></span>  
  
1.  <span data-ttu-id="19129-137">將 web.config 檔案複製到叢集中其他每台電腦上的 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal 資料夾。</span><span class="sxs-lookup"><span data-stu-id="19129-137">Copy the web.config file to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal folder on each additional computer in the cluster.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-138">在下列步驟中的所有參考**Program Files**資料夾將會是**Program Files (x86)** 64 位元電腦。</span><span class="sxs-lookup"><span data-stu-id="19129-138">In the following steps all references to the **Program Files** folder will be **Program Files (x86)** for 64 bit computers.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="19129-139">在下列步驟中，當您建立虛擬目錄時，請檢查並確定其設定與第一台電腦上 BizTalk Server 組態所建立的三個 BAM 虛擬目錄完全相同。</span><span class="sxs-lookup"><span data-stu-id="19129-139">In the following steps, when you are creating the virtual directories, check to make sure they have the exact settings as the three BAM virtual directories created by the BizTalk Server Configuration on first computer.</span></span> <span data-ttu-id="19129-140">請確認您的檔案路徑、ASP.NET 版本、目錄權限以及應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="19129-140">Confirm your file paths, the ASP.NET version, your directory permissions, and application pool.</span></span>  <span data-ttu-id="19129-141">請使用與您設定第一台電腦時所使用的相同網域服務帳戶，在您正在設定的電腦上執行 BAMAppPool。</span><span class="sxs-lookup"><span data-stu-id="19129-141">Use the same domain service account to run the BAMAppPool on the computer you are setting up as you used when setting up the first computer.</span></span> <span data-ttu-id="19129-142">請確定 BAMAppPool 在所有的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="19129-142">Make sure the BAMAppPool is running on all of the computers.</span></span> <span data-ttu-id="19129-143">有兩個 web.config 檔案您必須複製。</span><span class="sxs-lookup"><span data-stu-id="19129-143">There are two web.config files you must copy.</span></span>  
    >   
    >  <span data-ttu-id="19129-144">除了 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal 中的 web.config 檔案以外，您還必須將 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService 與 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMQueryService 中的 web.config 檔案複製到這部電腦上的相同資料夾。</span><span class="sxs-lookup"><span data-stu-id="19129-144">In addition to the web.config file [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal, you must copy the web.config file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService and [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMQueryService to the same folders on this computer.</span></span>  
  
2.  <span data-ttu-id="19129-145">(僅限硬體式 NLB) 修改下列兩行中的電腦名稱 (machinename) 和連接埠名稱，使其指向叢集的名稱：</span><span class="sxs-lookup"><span data-stu-id="19129-145">For hardware-based NLB only, modify the following computer name (machinename) and the port name in the following two lines to point to the name of name of the cluster:</span></span>  
  
    ```  
    <add key="BamQueryWSUrl" value="http://machinename:portname /BAM/BAMQueryService/BamQueryService.asmx" />  
    <add key="BamManagementWSUrl" value=" http://machinename:portname/BAM/BAMManagementService/BamManagementService.asmx" />  
    ```  
  
3.  <span data-ttu-id="19129-146">建立名為 BAMAppPool 的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="19129-146">Create an application pool called BAMAppPool.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-147">虛擬目錄的目錄路徑應為 %InstallationFolder%/BamPortal、%InstallationFolder%/BamPortal/BAMManagementService 及 %InstallationFolder%/BamPortal/BAMQueryService。</span><span class="sxs-lookup"><span data-stu-id="19129-147">The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService, and %InstallationFolder%/BamPortal/BAMQueryService.</span></span>  
  
4.  <span data-ttu-id="19129-148">在名為 BAM 的預設網站下建立虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="19129-148">Create a virtual directory under the Default Website called BAM.</span></span>  
  
5.  <span data-ttu-id="19129-149">將 BAM 虛擬目錄的應用程式集區變更為 BAMAppPool。</span><span class="sxs-lookup"><span data-stu-id="19129-149">Change the application pool of BAM virtual directory to BAMAppPool.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-150">虛擬目錄的目錄路徑應為 %InstallationFolder%/BamPortal、%InstallationFolder%/BamPortal/BAMManagementService 及 %InstallationFolder%/BamPortal/BAMQueryService。</span><span class="sxs-lookup"><span data-stu-id="19129-150">The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService and %InstallationFolder%/BamPortal/BAMQueryService.</span></span>  
  
6.  <span data-ttu-id="19129-151">在 BAM 下建立名為 BAMManagementService 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="19129-151">Create a virtual directory called BAMManagementService under BAM.</span></span>  
  
7.  <span data-ttu-id="19129-152">將 BAMManagementService 的應用程式集區變更為 BAMAppPool。</span><span class="sxs-lookup"><span data-stu-id="19129-152">Change the application pool of BAMManagementService to BAMAppPool.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-153">虛擬目錄的目錄路徑應為 %InstallationFolder%/BamPortal、%InstallationFolder%/BamPortal/BAMManagementService 及 %InstallationFolder%/BamPortal/BAMQueryService。</span><span class="sxs-lookup"><span data-stu-id="19129-153">The directory path for the virtual directories should be %InstallationFolder%/BamPortal, %InstallationFolder%/BamPortal/BAMManagementService, and %InstallationFolder%/BamPortal/BAMQueryService.</span></span>  
  
8.  <span data-ttu-id="19129-154">在 BAM 下建立名為 BAMQueryService 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="19129-154">Create a virtual directory called BAMQueryService under BAM.</span></span>  
  
9. <span data-ttu-id="19129-155">將 BAMQueryService 的應用程式集區變更為 BAMAppPool。</span><span class="sxs-lookup"><span data-stu-id="19129-155">Change the application pool of BAMQueryService to BAMAppPool.</span></span>  
  
10. <span data-ttu-id="19129-156">使用位於虛擬目錄屬性 ASP NET 索引標籤的 INETMGR 變更 BAM、BAMMANAGEMENTSERVICE 和 BAMQUERYSERVICE 的版本，以設定應用程式版本為 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="19129-156">Use the INETMGR, located on the virtual directory Properites ASP NET Tab, to change the version for BAM, BAMMANAGEMENTSERVICE, and BAMQUERYSERVICE to set the version of the Applications to .NET Framework 4.</span></span>  
  
11. <span data-ttu-id="19129-157">Run aspnet_setreg.exe -k:"SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\identity" -u:BAMWebServiceAccount  -p:Password。</span><span class="sxs-lookup"><span data-stu-id="19129-157">Run aspnet_setreg.exe -k:"SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\identity" -u:BAMWebServiceAccount  -p:Password.</span></span>  <span data-ttu-id="19129-158">這裡所指定的帳戶為 BAM 管理 Web 服務使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="19129-158">The account specified here is the BAM Management Web Service User account.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="19129-159">BAM 入口網站*只*在 32 位元模式下執行。</span><span class="sxs-lookup"><span data-stu-id="19129-159">BAM Portal *only* runs in 32-bit mode.</span></span> <span data-ttu-id="19129-160">如果在 64 位元電腦上安裝 IIS，必須在 32 位元模式下啟用 ASP.NET 2.0。</span><span class="sxs-lookup"><span data-stu-id="19129-160">If IIS is installed on a 64-bit machine, ASP.NET 2.0 must be enabled in 32-bit mode.</span></span> <span data-ttu-id="19129-161">若要這樣做，請開啟 IIS 管理員中，開啟**應用程式集區**，選取應用程式集區 (BAMAppPool)，然後按**進階設定**。</span><span class="sxs-lookup"><span data-stu-id="19129-161">To do this, open IIS Manager, open **Application Pool**, select the application pool (BAMAppPool), and then click **Advanced Settings**.</span></span> <span data-ttu-id="19129-162">在 [啟用 32 位元應用程式] 中，選取 [True]。</span><span class="sxs-lookup"><span data-stu-id="19129-162">In **Enable 32-bit applications**, select **True**.</span></span>  
    >   
    >  <span data-ttu-id="19129-163">[規劃 BAM 入口網站](../core/planning-for-the-bam-portal.md)列出其他需求。</span><span class="sxs-lookup"><span data-stu-id="19129-163">[Planning for the BAM Portal](../core/planning-for-the-bam-portal.md) lists additional requirements.</span></span>  
  
12. <span data-ttu-id="19129-164">執行 SubInACL，此命令列工具可以讓系統管理員取得檔案、登錄機碼和服務的安全性資訊，並且在使用者間、本機或全域群組間以及網域間傳輸此資訊，以便在 WebServices 上設定 AppPool 的讀取 ACL。</span><span class="sxs-lookup"><span data-stu-id="19129-164">Set the read ACLs for the AppPool user on WebServices by running SubInACL, a command-line tool that enables administrators to obtain security information about files, registry keys, and services, and to transfer this information from user to user, from local or global group to group, and from domain to domain.</span></span>  
  
13. <span data-ttu-id="19129-165">下載 SubInAcl [http://go.microsoft.com/fwlink/?LinkId=61990](http://go.microsoft.com/fwlink/?LinkId=61990)。</span><span class="sxs-lookup"><span data-stu-id="19129-165">Download SubInAcl from [http://go.microsoft.com/fwlink/?LinkId=61990](http://go.microsoft.com/fwlink/?LinkId=61990).</span></span>  
  
14. <span data-ttu-id="19129-166">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="19129-166">Open a command prompt.</span></span> <span data-ttu-id="19129-167">若要這樣做，請按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="19129-167">To do this, click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
15. <span data-ttu-id="19129-168">在命令提示字元輸入下列命令： subinacl.exe /subkeyreg"HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices""/ 授與 = Network Service = R"</span><span class="sxs-lookup"><span data-stu-id="19129-168">Type the following at the command prompt: subinacl.exe /subkeyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices" "/grant=Network Service=R"</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-169">此命令的目的是要授與 BAM 應用程式集區使用者讀取 SOFTWAREMicrosoftBizTalk Server3.0BAMWebServicesidentity 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="19129-169">The purpose of this command is to grant the BAM Application Pool user read access to the SOFTWAREMicrosoftBizTalk Server3.0BAMWebServicesidentity registry key.</span></span> <span data-ttu-id="19129-170">此範例使用網路服務，因為這是 IIS 使用的應用程式集區預設值。</span><span class="sxs-lookup"><span data-stu-id="19129-170">The example uses Network Service since it is the default used by IIS for Application Pool.</span></span> <span data-ttu-id="19129-171">如果您未使用預設的 IIS 設定，則應該取代部署使用的應用程式集區使用者。</span><span class="sxs-lookup"><span data-stu-id="19129-171">If you do not use the default IIS settings, you should substitute the application pool user that your deployment uses.</span></span>  
  
16. <span data-ttu-id="19129-172">在命令提示字元輸入下列命令： subinacl.exe /keyreg"HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk server\3.0""/ 授與 =\<BAM web 服務帳戶\>"</span><span class="sxs-lookup"><span data-stu-id="19129-172">Type the following at the command prompt: subinacl.exe /keyreg "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0" "/grant=\<BAM WebService Account\>”</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-173">這個命令的目的，是要授與 BAM 管理 Web 服務使用者帳戶讀取 SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\Identity 登錄機碼的權限。</span><span class="sxs-lookup"><span data-stu-id="19129-173">The purpose of this command is to grant the BAM Management Web Service User account read access to the SOFTWARE\Microsoft\BizTalk Server\3.0\BAM\WebServices\Identity registry key.</span></span>  
  
17. <span data-ttu-id="19129-174">確認用來執行 BAMManagement Web 服務的識別身分具有 ASPNET_SETREG 機碼的存取權。</span><span class="sxs-lookup"><span data-stu-id="19129-174">Verify that the identity that the application pool that the BAMManagement Web service runs under has read access to the ASPNET_SETREG key.</span></span>  
  
18. <span data-ttu-id="19129-175">請使用電腦管理系統管理員工具，將 BAM 管理 Web 服務使用者及 BAM 應用程式集區使用者帳戶新增至 IIS 工作者處理序群組 (IIS_WPG) 及 SharePoint 服務群組 (STS_WPG)。</span><span class="sxs-lookup"><span data-stu-id="19129-175">Use the Computer Management administrator tool to add the BAM Management Web service user and the BAM application pool user account to the IIS Worker Process Group (IIS_WPG) and SharePoint services group (STS_WPG).</span></span>  
  
19. <span data-ttu-id="19129-176">設定應用程式集區和 Web 服務使用者的暫存 ASP.NET 資料夾的權限： c:\windows\system32\cacls"%windir%\Microsoft.NET\Framework\ v2.0。\<最小版本號碼\>\Temporary ASP.NET Files"/T /E /G \<BAM web 服務帳戶\>: F</span><span class="sxs-lookup"><span data-stu-id="19129-176">Set the permissions on the temporary ASP.NET folders for the applications pool and Web service users: c:\windows\system32\cacls "%windir%\Microsoft.NET\Framework\ v2.0.\<min version number\>\Temporary ASP.NET Files" /T /E /G \<BAM WebService Account\>:F</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19129-177">您會同時授與 BAM 管理 Web 服務使用者帳戶及 BAM 應用程式集區使用者帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="19129-177">You grant access to both the BAM Management Web Service User account and the BAM App Pool User account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19129-178">請參閱</span><span class="sxs-lookup"><span data-stu-id="19129-178">See Also</span></span>  
 [<span data-ttu-id="19129-179">管理 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="19129-179">Managing the BAM Portal</span></span>](../core/managing-the-bam-portal.md)