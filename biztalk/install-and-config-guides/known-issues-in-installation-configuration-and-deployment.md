---
title: "安裝、 設定及部署中的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1c08eb-d647-4a4a-b9a3-c4d84e8d4b82
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cda1bd5c8167bbf9f6049b3620c0c949950b1e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-in-installation-configuration-and-deployment"></a><span data-ttu-id="c1123-102">安裝、組態和部署中的已知問題</span><span class="sxs-lookup"><span data-stu-id="c1123-102">Known Issues in Installation, Configuration, and Deployment</span></span>
## <a name="some-biztalk-edias2-artifacts-are-still-active-after-unconfiguring"></a><span data-ttu-id="c1123-103">有些 BizTalk EDI/AS2 成品在取消設定後依然在作用中</span><span class="sxs-lookup"><span data-stu-id="c1123-103">Some BizTalk EDI/AS2 Artifacts Are Still Active After Unconfiguring</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="c1123-104">問題</span><span class="sxs-lookup"><span data-stu-id="c1123-104">Problem</span></span>  
 <span data-ttu-id="c1123-105">在您取消設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 BizTalk EDI/AS2 功能之後，有些與 EDI 和 AS2 處理有關的 BizTalk Server 成品，仍然可以在 BizTalk 群組組態的內容中運作。</span><span class="sxs-lookup"><span data-stu-id="c1123-105">After you unconfigure the BizTalk EDI/AS2 feature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some BizTalk Server artifacts related to EDI and AS2 processing will still be active in the context of the BizTalk group configuration.</span></span> <span data-ttu-id="c1123-106">這些成品將會包括 EDI 和 AS2 管線，以及批次協調流程。</span><span class="sxs-lookup"><span data-stu-id="c1123-106">These artifacts will include EDI and AS2 pipelines and the batching orchestration.</span></span> <span data-ttu-id="c1123-107">因此，即使取消設定 BizTalk EDI/AS2 功能，您仍然可以執行基本的 EDI 和 AS2 處理。</span><span class="sxs-lookup"><span data-stu-id="c1123-107">As a result, you will still be able to perform basic EDI and AS2 processing even after unconfiguring the BizTalk EDI/AS2 feature.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="c1123-108">原因</span><span class="sxs-lookup"><span data-stu-id="c1123-108">Cause</span></span>  
 <span data-ttu-id="c1123-109">這時有存在與 EDI 和 AS2 處理相關聯的使用中連接埠。</span><span class="sxs-lookup"><span data-stu-id="c1123-109">There are active ports associated with EDI and AS2 processing.</span></span> <span data-ttu-id="c1123-110">有些成品會在這些連接埠保持使用狀態時繼續運作。</span><span class="sxs-lookup"><span data-stu-id="c1123-110">Some artifacts will continue to function while these ports remain active.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="c1123-111">解決方案</span><span class="sxs-lookup"><span data-stu-id="c1123-111">Resolution</span></span>  
 <span data-ttu-id="c1123-112">若要停用所有的 EDI/AS2 成品，您應該停用、停止或刪除與 EDI 和 AS2 處理相關聯的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c1123-112">To disable all EDI/AS2 artifacts, you should disable, stop, or delete the ports associated with EDI and AS2 processing.</span></span>  
  
## <a name="if-the-biztalk-server-computer-or-sql-server-computer-is-renamed-after-biztalk-server-configuration-the-configuration-wizard-will-fail"></a><span data-ttu-id="c1123-113">如果 BizTalk Server 電腦或 SQL Server 電腦在 BizTalk Server 組態之後重新命名，組態精靈將會失敗</span><span class="sxs-lookup"><span data-stu-id="c1123-113">If the BizTalk Server Computer or SQL Server Computer Is Renamed After BizTalk Server Configuration, the Configuration Wizard Will Fail</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="c1123-114">問題</span><span class="sxs-lookup"><span data-stu-id="c1123-114">Problem</span></span>  
 <span data-ttu-id="c1123-115">這個問題可能會以數種方式出現：</span><span class="sxs-lookup"><span data-stu-id="c1123-115">This problem may manifest itself in several ways:</span></span>  
  
-   <span data-ttu-id="c1123-116">BizTalk Server 組態將會正確載入 [概觀] 頁面，不過當嘗試設定某項功能時，功能選項並未出現在畫面上。</span><span class="sxs-lookup"><span data-stu-id="c1123-116">The BizTalk Server Configuration will load the Overview page correctly, but when attempting to configure a feature the feature options do not display on the screen.</span></span>  
  
-   <span data-ttu-id="c1123-117">組態精靈無法連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="c1123-117">The configuration wizard cannot connect to the SQL Server.</span></span>  
  
-   <span data-ttu-id="c1123-118">嘗試取消設定所有功能會取消設定部分功能，而非全部功能。</span><span class="sxs-lookup"><span data-stu-id="c1123-118">Attempting to Unconfigure All unconfigures some features, but not all.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="c1123-119">原因</span><span class="sxs-lookup"><span data-stu-id="c1123-119">Cause</span></span>  
 <span data-ttu-id="c1123-120">BizTalk Server 組態會儲存電腦網路名稱。</span><span class="sxs-lookup"><span data-stu-id="c1123-120">The BizTalk Server configuration stores the computer network name.</span></span> <span data-ttu-id="c1123-121">當電腦重新命名後，BizTalk Server 組態與組態精靈找不到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="c1123-121">When the computer is renamed the BizTalk Server Configuration and configuration wizard cannot locate the BizTalk Server.</span></span> <span data-ttu-id="c1123-122">如果在設定 BizTalk Server 後重新命名 SQL Server 電腦，也會發生相似的問題。</span><span class="sxs-lookup"><span data-stu-id="c1123-122">A similar problem will occur if the SQL Server computer is renamed after BizTalk Server is configured.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="c1123-123">解決方案</span><span class="sxs-lookup"><span data-stu-id="c1123-123">Resolution</span></span>  
 <span data-ttu-id="c1123-124">請勿重新命名 BizTalk Server 電腦或 SQL Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="c1123-124">Do not rename the BizTalk Server computer or the SQL Server computer.</span></span> <span data-ttu-id="c1123-125">如果必須重新命名伺服器，請在重新命名電腦之前取消設定所有 BizTalk 功能。</span><span class="sxs-lookup"><span data-stu-id="c1123-125">If a server must be renamed, unconfigure all BizTalk Features before renaming the computer.</span></span> <span data-ttu-id="c1123-126">接著，在重新命名電腦後，重新設定 BizTalk Server 功能。</span><span class="sxs-lookup"><span data-stu-id="c1123-126">After renaming the computer, reconfigure BizTalk Server features.</span></span>  
  
## <a name="the-biztalk-server-business-rules-configuration-wizard-fails"></a><span data-ttu-id="c1123-127">BizTalk Server 商務規則組態精靈失敗</span><span class="sxs-lookup"><span data-stu-id="c1123-127">The BizTalk Server Business Rules Configuration Wizard Fails</span></span>  
  
### <a name="problem"></a><span data-ttu-id="c1123-128">問題</span><span class="sxs-lookup"><span data-stu-id="c1123-128">Problem</span></span>  
  
-   <span data-ttu-id="c1123-129">BizTalk Server 商務規則組態精靈失敗，並出現「一些元件的組態已經失敗，而且沒有套用任何設定到那些元件」錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1123-129">The Business Rules Configuration Wizard fails with the error “Configuration failed for some components and no settings were applied for those components”.</span></span>  
  
-   <span data-ttu-id="c1123-130">在已順利設定商務規則引擎的 BizTalk Server 電腦上，無法啟動並且無法手動啟動規則引擎更新服務。</span><span class="sxs-lookup"><span data-stu-id="c1123-130">On BizTalk Server computers for which the Business Rules Engine has already been successfully configured, the Rules Engine Update service fails to start and cannot be started manually.</span></span>  
  
 <span data-ttu-id="c1123-131">發生這個問題時，BizTalk Server 電腦應用程式記錄檔中可能會產生與下例類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="c1123-131">When this problem occurs, an error similar to the following may be generated in the BizTalk Server computer Application log:</span></span>  
  
```  
Service could not be started. : System.Net.Sockets.SocketException (10061): No connection could be made because the target machine actively refused it ::1:3132  
  
```  
  
### <a name="cause"></a><span data-ttu-id="c1123-132">原因</span><span class="sxs-lookup"><span data-stu-id="c1123-132">Cause</span></span>  
 <span data-ttu-id="c1123-133">Microsoft 惡意程式碼防護中心已發行更新過的簽章檔案，以解決來自 SettingsModifier:Win32/PossibleHostsFileHijack 的潛在威脅。</span><span class="sxs-lookup"><span data-stu-id="c1123-133">The Microsoft Malware Protection Center released an updated signature file to address a possible threat from SettingsModifier:Win32/PossibleHostsFileHijack.</span></span> <span data-ttu-id="c1123-134">這個更新過的簽章檔案可能會讓 Microsoft 惡意程式碼偵測軟體 (例如 Windows Defender) 更新本機 HOSTS 檔案，以減輕來自 SettingsModifier:Win32/PossibleHostsFileHijack 的威脅。</span><span class="sxs-lookup"><span data-stu-id="c1123-134">This updated signature file can cause Microsoft Malware Detection software such as Windows Defender to update the local HOSTS file to mitigate threats from SettingsModifier:Win32/PossibleHostsFileHijack.</span></span> <span data-ttu-id="c1123-135">基於這些變更，可能無法啟動 BizTalk Server 規則引擎更新服務。</span><span class="sxs-lookup"><span data-stu-id="c1123-135">As a result of these changes, the BizTalk Server Rules Engine Update service may fail to start.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="c1123-136">解決方案</span><span class="sxs-lookup"><span data-stu-id="c1123-136">Resolution</span></span>  
 <span data-ttu-id="c1123-137">更新本機 HOSTS 檔案，以加入下行︰</span><span class="sxs-lookup"><span data-stu-id="c1123-137">Update the local HOSTS file to include the following line:</span></span>  
  
```  
127.0.0.1         localhost  
```  
  
 <span data-ttu-id="c1123-138">HOSTS 檔案位於 %systemroot%\drivers\etc\ 目錄中。</span><span class="sxs-lookup"><span data-stu-id="c1123-138">The HOSTS file is located in the %systemroot%\drivers\etc\ directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1123-139">如需解決 SettingsModifier:Win32/PossibleHostsFileHijack 潛在威脅的 Microsoft 惡意程式碼防護中心簽章更新的詳細資訊，請瀏覽 [http://go.microsoft.com/fwlink/?LinkId=146221](http://go.microsoft.com/fwlink/?LinkId=146221)。</span><span class="sxs-lookup"><span data-stu-id="c1123-139">For more information about the Microsoft Malware Protection Center signature update that addresses a possible threat from SettingsModifier:Win32/PossibleHostsFileHijack, go to [http://go.microsoft.com/fwlink/?LinkId=146221](http://go.microsoft.com/fwlink/?LinkId=146221).</span></span>  
  
## <a name="enlistment-of-an-orchestration-fails-if-referenced-assemblies-are-missing-from-the-gacmgmt-db"></a><span data-ttu-id="c1123-140">如果 GAC/管理資料庫中的參考組件遺失，則登錄協調流程會失敗</span><span class="sxs-lookup"><span data-stu-id="c1123-140">Enlistment of an Orchestration Fails if Referenced Assemblies are Missing from the GAC/Mgmt DB</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="c1123-141">問題</span><span class="sxs-lookup"><span data-stu-id="c1123-141">Problem</span></span>  
 <span data-ttu-id="c1123-142">如果 GAC/管理資料庫中的參考 (參考為協調流程的 C# 組件) 遺失，則登錄協調流程會失敗。</span><span class="sxs-lookup"><span data-stu-id="c1123-142">Enlistment of an orchestration fails if references (C# assemblies which are referenced to orchestrations) are missing from the GAC/Mgmt db.</span></span> <span data-ttu-id="c1123-143">重新部署的過程中，可能需要根據現有狀態登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="c1123-143">During re-deployment, there may be a need to enlist the orchestration based on its existing state.</span></span> <span data-ttu-id="c1123-144">如果參考遺失，則部署也會失敗。</span><span class="sxs-lookup"><span data-stu-id="c1123-144">If references are missing then the deployment also fails.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="c1123-145">原因</span><span class="sxs-lookup"><span data-stu-id="c1123-145">Cause</span></span>  
 <span data-ttu-id="c1123-146">GAC/管理資料庫中參考的組件遺失。</span><span class="sxs-lookup"><span data-stu-id="c1123-146">Referenced assemblies are missing from GAC/Mgmt db.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="c1123-147">解決方案</span><span class="sxs-lookup"><span data-stu-id="c1123-147">Resolution</span></span>  
 <span data-ttu-id="c1123-148">將參考的組件加入 GAC 中或加入做為資源，如此就能儲存在管理資料庫中，並且可在登錄協調流程時存取。</span><span class="sxs-lookup"><span data-stu-id="c1123-148">Add the referenced assemblies in GAC or add them as resources, so that they are stored in Mgmt db and are accessible during enlistment of orchestration.</span></span>  

## <a name="community-blog-biztalk-2013-r2-bugs-issues--quirks"></a><span data-ttu-id="c1123-149">社群部落格︰BizTalk 2013 R2 Bug、問題和缺點</span><span class="sxs-lookup"><span data-stu-id="c1123-149">Community blog: BizTalk 2013 R2 bugs, issues & quirks</span></span>

[<span data-ttu-id="c1123-150">BizTalk Server 2013 R2 已知 Bug、問題和缺點</span><span class="sxs-lookup"><span data-stu-id="c1123-150">BizTalk Server 2013 R2 known bugs, issues, quirks</span></span>](https://cdijkgraaf.wordpress.com/2016/08/12/biztalk-2013-r2-known-bugs-issues-quirks/)
  
## <a name="additional-configuration-topics"></a><span data-ttu-id="c1123-151">其他組態主題</span><span class="sxs-lookup"><span data-stu-id="c1123-151">Additional Configuration Topics</span></span>  
  
 [<span data-ttu-id="c1123-152">設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c1123-152">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)  
  
 [<span data-ttu-id="c1123-153">在 Azure VM 上設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c1123-153">Configuring BizTalk Server on an Azure VM</span></span>](http://msdn.microsoft.com/library/azure/jj248689.aspx)  
  
  [<span data-ttu-id="c1123-154">設定叢集中的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c1123-154">Configure BizTalk Server in a Cluster</span></span>](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)
  
 [<span data-ttu-id="c1123-155">保護 BizTalk Server 部署安全</span><span class="sxs-lookup"><span data-stu-id="c1123-155">Securing Your BizTalk Server Deployment</span></span>](../install-and-config-guides/securing-your-biztalk-server-deployment.md)  
  