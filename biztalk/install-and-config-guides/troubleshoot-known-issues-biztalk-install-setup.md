---
title: "已知的安裝問題 |Microsoft 文件"
description: "已知的問題和常見問題與安裝和設定 BizTalk Server 時的解決方式"
ms.custom: 
ms.date: 11/30/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d0e707-6b9e-49e1-9f17-19b3bac1229e
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90217a4e80df6f017b451dd7c40f6a1dfe3898ac
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshoot-biztalk-server-setup"></a><span data-ttu-id="e9cec-103">疑難排解 BizTalk Server 安裝程式</span><span class="sxs-lookup"><span data-stu-id="e9cec-103">Troubleshoot BizTalk Server Setup</span></span>

## <a name="introduction"></a><span data-ttu-id="e9cec-104">簡介</span><span class="sxs-lookup"><span data-stu-id="e9cec-104">Introduction</span></span>  
 <span data-ttu-id="e9cec-105">此疑難排解指南 》 列出已知的問題，以及最常見的問題，您可能會遇到安裝 BizTalk Server 時。</span><span class="sxs-lookup"><span data-stu-id="e9cec-105">This Troubleshooting Guide lists  known issues as well as the most common problems you may encounter while installing BizTalk Server.</span></span> <span data-ttu-id="e9cec-106">本指南還包括自訂動作來提供有關 Windows Server logo program BizTalk 伺服器憑證的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e9cec-106">This guide also includes Custom actions which provides details about BizTalk Server certification for the Windows Server logo program.</span></span>  <span data-ttu-id="e9cec-107">它提供安裝 BizTalk Server 期間可能會執行的自訂動作清單。</span><span class="sxs-lookup"><span data-stu-id="e9cec-107">It provides you a list of custom actions that might be performed during BizTalk Server Setup operation.</span></span>  
  
## <a name="review-install-steps"></a><span data-ttu-id="e9cec-108">檢閱安裝步驟</span><span class="sxs-lookup"><span data-stu-id="e9cec-108">Review install steps</span></span>  
<span data-ttu-id="e9cec-109">大部分 BizTalk Server 安裝程式問題的發生是因為 BizTalk Server 的電腦未正確地準備之前已安裝 BizTalk Server，或先前安裝的 BizTalk Server 未完全解除安裝之前嘗試新的安裝。</span><span class="sxs-lookup"><span data-stu-id="e9cec-109">The majority of BizTalk Server setup problems occur because the BizTalk Server computer was not properly prepared before BizTalk Server was installed, or a previous installation of BizTalk Server was not fully uninstalled before a new installation was attempted.</span></span>  
  
<span data-ttu-id="e9cec-110">檢閱兩個檢查清單，您也可以在 BizTalk Server 安裝指南，以確保您的電腦上已正確設定以支援 BizTalk Server 中找到。</span><span class="sxs-lookup"><span data-stu-id="e9cec-110">Review the two checklists below, which you can also find in the BizTalk Server Installation Guides, to ensure that your computer(s) are properly configured to support BizTalk Server.</span></span> <span data-ttu-id="e9cec-111">如果檢閱此資訊之後，您的設定仍不成功，則這份文件的其餘部分中的疑難排解提示可能很有用。</span><span class="sxs-lookup"><span data-stu-id="e9cec-111">If, after reviewing this information, your setup still does not succeed, the troubleshooting tips in the rest of this document may be useful.</span></span>  
  
1. <span data-ttu-id="e9cec-112">安裝先決條件軟體和程式：</span><span class="sxs-lookup"><span data-stu-id="e9cec-112">Install prerequisite software and programs:</span></span>

    * [<span data-ttu-id="e9cec-113">BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="e9cec-113">BizTalk Server 2016</span></span>](set-up-and-install-prerequisites-for-biztalk-server-2016.md)
    * [<span data-ttu-id="e9cec-114">BizTalk Server 2013 R2 與 2013</span><span class="sxs-lookup"><span data-stu-id="e9cec-114">BizTalk Server 2013 R2 & 2013</span></span>](prepare-your-computer-for-installation.md)

2. <span data-ttu-id="e9cec-115">安裝和設定 BizTalk Server:</span><span class="sxs-lookup"><span data-stu-id="e9cec-115">Install and configure BizTalk Server:</span></span>  

    1. <span data-ttu-id="e9cec-116">安裝 BizTalk Server: [BizTalk 2016](install-biztalk-server-2016.md) ， [BizTalk 2013 R2 / 2013年](install-biztalk-server-2013-and-2013-r2.md)</span><span class="sxs-lookup"><span data-stu-id="e9cec-116">Install BizTalk Server: [BizTalk 2016](install-biztalk-server-2016.md) , [BizTalk 2013 R2 / 2013](install-biztalk-server-2013-and-2013-r2.md)</span></span>  
    2. <span data-ttu-id="e9cec-117">[設定](configure-biztalk-server.md)BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e9cec-117">[Configure](configure-biztalk-server.md) BizTalk Server</span></span>
    3. [<span data-ttu-id="e9cec-118">組態後步驟</span><span class="sxs-lookup"><span data-stu-id="e9cec-118">Post-configuration steps</span></span>](post-configuration-steps-to-optimize-your-environment.md)
  
## <a name="some-edias2-artifacts-are-still-active-after-unconfiguring"></a><span data-ttu-id="e9cec-119">取消設定後一些 EDI/AS2 成品仍然使用中</span><span class="sxs-lookup"><span data-stu-id="e9cec-119">Some EDI/AS2 artifacts are still active after unconfiguring</span></span>  
  
<span data-ttu-id="e9cec-120">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-120">**Problem**</span></span>  
 <span data-ttu-id="e9cec-121">之後您取消設定 BizTalk Server 中，某些與 EDI 的 BizTalk Server 成品的 BizTalk EDI/AS2 功能和 AS2 處理，仍然可以在 BizTalk 群組組態的內容中。</span><span class="sxs-lookup"><span data-stu-id="e9cec-121">After you unconfigure the BizTalk EDI/AS2 feature of BizTalk Server, some BizTalk Server artifacts related to EDI and AS2 processing will still be active in the context of the BizTalk group configuration.</span></span> <span data-ttu-id="e9cec-122">這些成品將會包括 EDI 和 AS2 管線，以及批次協調流程。</span><span class="sxs-lookup"><span data-stu-id="e9cec-122">These artifacts will include EDI and AS2 pipelines and the batching orchestration.</span></span> <span data-ttu-id="e9cec-123">因此，即使取消設定 BizTalk EDI/AS2 功能，您仍然可以執行基本的 EDI 和 AS2 處理。</span><span class="sxs-lookup"><span data-stu-id="e9cec-123">As a result, you will still be able to perform basic EDI and AS2 processing even after unconfiguring the BizTalk EDI/AS2 feature.</span></span>  
  
<span data-ttu-id="e9cec-124">**可能的原因** </span><span class="sxs-lookup"><span data-stu-id="e9cec-124">**Cause** </span></span>  
 <span data-ttu-id="e9cec-125">這時有存在與 EDI 和 AS2 處理相關聯的使用中連接埠。</span><span class="sxs-lookup"><span data-stu-id="e9cec-125">There are active ports associated with EDI and AS2 processing.</span></span> <span data-ttu-id="e9cec-126">有些成品會在這些連接埠保持使用狀態時繼續運作。</span><span class="sxs-lookup"><span data-stu-id="e9cec-126">Some artifacts will continue to function while these ports remain active.</span></span>  
  
<span data-ttu-id="e9cec-127">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-127">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-128">若要停用所有的 EDI/AS2 成品，您應該停用、停止或刪除與 EDI 和 AS2 處理相關聯的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e9cec-128">To disable all EDI/AS2 artifacts, you should disable, stop, or delete the ports associated with EDI and AS2 processing.</span></span>  
  
## <a name="after-renaming-biztalk-or-sql-server-computer-the-configuration-wizard-fails"></a><span data-ttu-id="e9cec-129">在之後重新命名 BizTalk 或 SQL Server 的電腦，設定精靈會失敗</span><span class="sxs-lookup"><span data-stu-id="e9cec-129">After renaming BizTalk or SQL Server computer, the Configuration Wizard fails</span></span>  
  
<span data-ttu-id="e9cec-130">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-130">**Problem**</span></span>  
 <span data-ttu-id="e9cec-131">這個問題可能會以數種方式出現：</span><span class="sxs-lookup"><span data-stu-id="e9cec-131">This problem may manifest itself in several ways:</span></span>  
  
-   <span data-ttu-id="e9cec-132">Configuration manager 正確地載入 [概觀] 頁面，但是當嘗試設定某項功能，功能選項並未出現在螢幕上。</span><span class="sxs-lookup"><span data-stu-id="e9cec-132">The configuration manager will load the Overview page correctly, but when attempting to configure a feature, the feature options do not display on the screen.</span></span>  
  
-   <span data-ttu-id="e9cec-133">組態精靈無法連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e9cec-133">The configuration wizard cannot connect to the SQL Server.</span></span>  
  
-   <span data-ttu-id="e9cec-134">嘗試取消設定所有功能會取消設定部分功能，而非全部功能。</span><span class="sxs-lookup"><span data-stu-id="e9cec-134">Attempting to Unconfigure All unconfigures some features, but not all.</span></span>  
  
<span data-ttu-id="e9cec-135">**可能的原因** </span><span class="sxs-lookup"><span data-stu-id="e9cec-135">**Cause** </span></span>  
 <span data-ttu-id="e9cec-136">BizTalk Server 組態會儲存電腦網路名稱。</span><span class="sxs-lookup"><span data-stu-id="e9cec-136">The BizTalk Server configuration stores the computer network name.</span></span> <span data-ttu-id="e9cec-137">重新命名電腦時，組態管理員 」 和 「 組態精靈找不到 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="e9cec-137">When the computer is renamed, the configuration manager and configuration wizard cannot locate the BizTalk Server.</span></span> <span data-ttu-id="e9cec-138">如果在設定 BizTalk Server 後重新命名 SQL Server 電腦，也會發生相似的問題。</span><span class="sxs-lookup"><span data-stu-id="e9cec-138">A similar problem will occur if the SQL Server computer is renamed after BizTalk Server is configured.</span></span>  
  
<span data-ttu-id="e9cec-139">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-139">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-140">請勿重新命名 BizTalk Server 電腦或 SQL Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="e9cec-140">Do not rename the BizTalk Server computer or the SQL Server computer.</span></span> <span data-ttu-id="e9cec-141">如果您必須重新命名伺服器，取消設定所有 BizTalk 功能，然後再重新命名電腦。</span><span class="sxs-lookup"><span data-stu-id="e9cec-141">If a server must be renamed, unconfigure all BizTalk features before renaming the computer.</span></span> <span data-ttu-id="e9cec-142">接著，在重新命名電腦後，重新設定 BizTalk Server 功能。</span><span class="sxs-lookup"><span data-stu-id="e9cec-142">After renaming the computer, reconfigure BizTalk Server features.</span></span>  
  
## <a name="business-rules-configuration-wizard-fails"></a><span data-ttu-id="e9cec-143">商務規則組態精靈失敗</span><span class="sxs-lookup"><span data-stu-id="e9cec-143">Business Rules Configuration Wizard fails</span></span>  
  
<span data-ttu-id="e9cec-144">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-144">**Problem**</span></span>  
  
-   <span data-ttu-id="e9cec-145">商務規則組態精靈失敗，發生錯誤 「 一些元件的組態失敗和不套用任何設定到那些元件 」。</span><span class="sxs-lookup"><span data-stu-id="e9cec-145">The Business Rules Configuration Wizard fails with the error “Configuration failed for some components and no settings were applied for those components.”</span></span>  
  
-   <span data-ttu-id="e9cec-146">在已順利設定商務規則引擎的 BizTalk Server 電腦上，無法啟動並且無法手動啟動規則引擎更新服務。</span><span class="sxs-lookup"><span data-stu-id="e9cec-146">On BizTalk Server computers for which the Business Rules Engine has already been successfully configured, the Rules Engine Update service fails to start and cannot be started manually.</span></span>  
  
<span data-ttu-id="e9cec-147">發生這個問題時，BizTalk Server 電腦應用程式記錄檔中可能會產生與下例類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="e9cec-147">When this problem occurs, an error similar to the following may be generated in the BizTalk Server computer Application log:</span></span>  
  
```  
Service could not be started. : System.Net.Sockets.SocketException (10061): No connection could be made because the target machine actively refused it ::1:3132  
  
```  
  
<span data-ttu-id="e9cec-148">**可能的原因** </span><span class="sxs-lookup"><span data-stu-id="e9cec-148">**Cause** </span></span>  
 <span data-ttu-id="e9cec-149">從 Microsoft 惡意程式碼防護中心發行更新的簽章檔案，在 2010 年 3 月 9 日解決潛在威脅從 SettingsModifier:Win32 / PossibleHostsFileHijack。</span><span class="sxs-lookup"><span data-stu-id="e9cec-149">The Microsoft Malware Protection Center released an updated signature file on March 9th, 2010 to address a possible threat from SettingsModifier:Win32/PossibleHostsFileHijack.</span></span> <span data-ttu-id="e9cec-150">這個更新過的簽章檔案可能會讓 Microsoft 惡意程式碼偵測軟體 (例如 Windows Defender) 更新本機 HOSTS 檔案，以減輕來自 SettingsModifier:Win32/PossibleHostsFileHijack 的威脅。</span><span class="sxs-lookup"><span data-stu-id="e9cec-150">This updated signature file can cause Microsoft Malware Detection software such as Windows Defender to update the local HOSTS file to mitigate threats from SettingsModifier:Win32/PossibleHostsFileHijack.</span></span> <span data-ttu-id="e9cec-151">基於這些變更，可能無法啟動 BizTalk Server 規則引擎更新服務。</span><span class="sxs-lookup"><span data-stu-id="e9cec-151">As a result of these changes, the BizTalk Server Rules Engine Update service may fail to start.</span></span>  
  
<span data-ttu-id="e9cec-152">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-152">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-153">更新本機 HOSTS 檔案，以加入下行︰</span><span class="sxs-lookup"><span data-stu-id="e9cec-153">Update the local HOSTS file to include the following line:</span></span>  
  
```  
127.0.0.1         localhost  
```  
  
 <span data-ttu-id="e9cec-154">HOSTS 檔案位於 %systemroot%\drivers\etc\ 目錄中。</span><span class="sxs-lookup"><span data-stu-id="e9cec-154">The HOSTS file is located in the %systemroot%\drivers\etc\ directory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9cec-155">請參閱 Microsoft 惡意程式碼防護中心簽章更新的位址可能威脅從[SettingsModifier:Win32 / PossibleHostsFileHijack](http://go.microsoft.com/fwlink/?LinkId=146221)。</span><span class="sxs-lookup"><span data-stu-id="e9cec-155">See the Microsoft Malware Protection Center signature update that addresses a possible threat from [SettingsModifier:Win32/PossibleHostsFileHijack](http://go.microsoft.com/fwlink/?LinkId=146221).</span></span>  
  
## <a name="configuration-logging"></a><span data-ttu-id="e9cec-156">組態記錄</span><span class="sxs-lookup"><span data-stu-id="e9cec-156">Configuration Logging</span></span>  
 <span data-ttu-id="e9cec-157">「 組態 」 程式寫入組態記錄檔中的預設位於執行 BizTalk Server 之電腦的暫存目錄的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="e9cec-157">The configuration program writes detailed information to a configuration log file which by default is located in the temp directory of the computer running BizTalk Server.</span></span> <span data-ttu-id="e9cec-158">若要判斷 TEMP 環境變數所指定的資料夾，請在這部電腦上開啟命令提示，並輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="e9cec-158">To determine the folder that is specified by the TEMP environment variable open a command prompt on this computer, type the following command, and then press ENTER:</span></span>  
  
 <span data-ttu-id="e9cec-159">**echo %TEMP%**</span><span class="sxs-lookup"><span data-stu-id="e9cec-159">**echo %TEMP%**</span></span>  
  
 <span data-ttu-id="e9cec-160">此組態記錄檔含有已執行之組態步驟的摘要，以及組態程序中可能發生之任何失敗的相關診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="e9cec-160">The configuration log file contains a summary of the configuration steps performed, as well as diagnostic information about any failures that may occur during the configuration process.</span></span> <span data-ttu-id="e9cec-161">如果發生組態錯誤，請在文字編輯器 (如 [記事本]) 中開啟此組態記錄檔，然後檢查此記錄檔，找出錯誤的可能原因。</span><span class="sxs-lookup"><span data-stu-id="e9cec-161">If a configuration error occurs, open the configuration log in a text editor such as Notepad and check the log file for possible causes of the error.</span></span>  
  
## <a name="troubleshooting-tools"></a><span data-ttu-id="e9cec-162">疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="e9cec-162">Troubleshooting Tools</span></span>  
 <span data-ttu-id="e9cec-163">使用 SQL Server Profiler、Filemon 或 Regmon 可蒐集有關組態失敗的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="e9cec-163">Use SQL Server Profiler, Filemon, or Regmon to gather additional information about configuration failures.</span></span> <span data-ttu-id="e9cec-164">請參閱[用於疑難排解的工具和公用程式](../core/tools-and-utilities-to-use-for-troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="e9cec-164">See [Tools and Utilities to use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md).</span></span>  
  
### <a name="configuration-fails-when-biztalk-and-sql-are-installed-on-separate-computers"></a><span data-ttu-id="e9cec-165">BizTalk 和 SQL 安裝在不同電腦時，設定失敗</span><span class="sxs-lookup"><span data-stu-id="e9cec-165">Configuration fails when BizTalk and SQL are installed on separate computers</span></span>  
  
<span data-ttu-id="e9cec-166">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-166">**Problem**</span></span>  
 <span data-ttu-id="e9cec-167">當您嘗試設定企業單一登入 (SSO) 元件時，組態會發生失敗，其錯誤與底下類似：</span><span class="sxs-lookup"><span data-stu-id="e9cec-167">Configuration fails with errors similar to the following when attempting to configure the Enterprise Single Sign-On (SSO) component:</span></span>  
  
```
An error occurred while attempting to access the SSO database.  
Function: FieldInfoCreate  
```
  
 <span data-ttu-id="e9cec-168">-或-</span><span class="sxs-lookup"><span data-stu-id="e9cec-168">-or-</span></span>  
  
```Failed to enable the Single Sign-On (SSO) Service (error code 0X800706BA)```  
  
<span data-ttu-id="e9cec-169">**可能的原因**  </span><span class="sxs-lookup"><span data-stu-id="e9cec-169">**Cause**  </span></span>  
 <span data-ttu-id="e9cec-170">如果不同的電腦上安裝 BizTalk Server 和 SQL Server 則組態作業將會在 Microsoft Distributed Transaction Coordinator (MSDTC) 交易的內容下，而且必須透過使用 MSDTC 功能這些電腦之間的網路。</span><span class="sxs-lookup"><span data-stu-id="e9cec-170">If BizTalk Server and SQL Server are installed on different computers, then the configuration operations are performed under the context of a Microsoft Distributed Transaction Coordinator (MSDTC) transaction and MSDTC functionality must be available over the network between these computers.</span></span> <span data-ttu-id="e9cec-171">如果無法透過執行 BizTalk Server 和 SQL Server 的電腦之間網路使用 MSDTC 功能，會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9cec-171">If MSDTC functionality is not available over the network between the computers running BizTalk Server and SQL Server, then this error can occur.</span></span>  
  
<span data-ttu-id="e9cec-172">**解決方式**  </span><span class="sxs-lookup"><span data-stu-id="e9cec-172">**Resolution**  </span></span>  
<span data-ttu-id="e9cec-173">使用[疑難排解 MSDTC 問題的](https://support.microsoft.com/help/306843/how-to-troubleshoot-ms-dtc-firewall-issues)以確保執行 BizTalk Server 和 SQL Server 的電腦之間網路上的 MSDTC 功能。</span><span class="sxs-lookup"><span data-stu-id="e9cec-173">Use [Troubleshooting Problems with MSDTC](https://support.microsoft.com/help/306843/how-to-troubleshoot-ms-dtc-firewall-issues) to ensure MSDTC functionality over the network between the computers running BizTalk Server and SQL Server.</span></span>  
  
### <a name="antivirus-software-interferes-with-configuration-and-causes-configuration-failures"></a><span data-ttu-id="e9cec-174">防毒軟體干擾組態，並造成組態失敗</span><span class="sxs-lookup"><span data-stu-id="e9cec-174">Antivirus software interferes with configuration and causes configuration failures</span></span>  
  
<span data-ttu-id="e9cec-175">**問題** </span><span class="sxs-lookup"><span data-stu-id="e9cec-175">**Problem** </span></span>  
 <span data-ttu-id="e9cec-176">當防毒軟體錯誤判斷組態程式為病毒時，BizTalk Server 組態就會失敗。</span><span class="sxs-lookup"><span data-stu-id="e9cec-176">BizTalk Server configuration fails when antivirus software incorrectly determines that the configuration program is a virus.</span></span>  
  
<span data-ttu-id="e9cec-177">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-177">**Cause**</span></span>  
 <span data-ttu-id="e9cec-178">包含 BizTalk Server 組態程式當做合法 （非病毒） 程式尚未更新防毒軟體。</span><span class="sxs-lookup"><span data-stu-id="e9cec-178">The antivirus software has not been updated to include the BizTalk Server configuration program as a legitimate (non-virus) program.</span></span>  
  
<span data-ttu-id="e9cec-179">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-179">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-180">設定防毒程式將 BizTalk Server 組態程式辨識為合法 （非病毒） 程式，否則執行組態程式時，暫時停用防毒軟體。</span><span class="sxs-lookup"><span data-stu-id="e9cec-180">Configure the antivirus program to recognize the BizTalk Server configuration program as a legitimate (non-virus) program or else temporarily disable the antivirus software while the configuration program is running.</span></span>  
  
### <a name="configuration-fails-with-a-file-or-assembly-name-filenamedll-or-one-of-its-dependencies-was-not-found-error"></a><span data-ttu-id="e9cec-181">組態失敗，其錯誤為「找不到檔案或組件名稱 FileName.dll 或其相依性的其中之一」。</span><span class="sxs-lookup"><span data-stu-id="e9cec-181">Configuration fails with a "File or assembly name FileName.dll, or one of its dependencies, was not found" error</span></span>  
  
<span data-ttu-id="e9cec-182">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-182">**Problem**</span></span>  
 <span data-ttu-id="e9cec-183">在組態程序期間，出現了類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="e9cec-183">An error similar to the following is displayed during the configuration process:</span></span>  
  
 <span data-ttu-id="e9cec-184">無法部署 BizTalk 系統組件"C:\Program Files\Microsoft\BizTalk Server 20xx\Microsoft.BizTalk.DefaultPipelines.dll。</span><span class="sxs-lookup"><span data-stu-id="e9cec-184">Failed to deploy BizTalk system assembly "C:\Program Files\Microsoft\BizTalk Server 20xx\Microsoft.BizTalk.DefaultPipelines.dll.</span></span> <span data-ttu-id="e9cec-185">未指定例外狀況： 找不到檔案或組件名稱 FileName.dll，或其相依性的其中一個。 」</span><span class="sxs-lookup"><span data-stu-id="e9cec-185">Unspecified exception: File or assembly name FileName .dll, or one of its dependencies, was not found."</span></span>  
  
<span data-ttu-id="e9cec-186">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-186">**Cause**</span></span>  
 <span data-ttu-id="e9cec-187">如果網路服務帳戶未具備執行 BizTalk Server 的電腦上的暫存資料夾寫入權限，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9cec-187">This error can occur if the Network Service account does not have write permissions to the temp folder on the computer running BizTalk Server.</span></span> <span data-ttu-id="e9cec-188">在設定期間，BizTalk Server 組態會使用 Windows Management Instrumentation (WMI)，將.NET 組件部署至 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="e9cec-188">During configuration, BizTalk Server configuration uses Windows Management Instrumentation (WMI) to deploy .NET assemblies to the BizTalk Management database.</span></span> <span data-ttu-id="e9cec-189">WMI 會模擬 Network Service 帳戶同時將這些組件部署到 BizTalk 管理資料庫，因此網路服務帳戶必須具有寫入存取權執行 BizTalk Server 的電腦上的暫存資料夾。</span><span class="sxs-lookup"><span data-stu-id="e9cec-189">WMI impersonates the Network Service account while deploying these assemblies to the BizTalk Management database and so the Network Service account must have write access to the temp folder on the computer running BizTalk Server.</span></span>  
  
<span data-ttu-id="e9cec-190">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-190">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-191">授與 Network Service 帳戶寫入到暫存資料夾執行 BizTalk Server 的電腦上，然後再次執行組態程式。</span><span class="sxs-lookup"><span data-stu-id="e9cec-191">Grant the Network Service account write access to the temp folder on the computer running BizTalk Server and run the configuration program again.</span></span> <span data-ttu-id="e9cec-192">若要判斷 TEMP 環境變數所指定的資料夾，請在這部電腦上開啟命令提示，並輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="e9cec-192">To determine the folder that is specified by the TEMP environment variable, open a command prompt on the computer, type the following command, and then press ENTER:</span></span>  
  
```  
echo %TEMP%  
```  
  
### <a name="configuration-fails-if-a-sql-server-database-file-that-has-the-same-name-as-the-specified-database-already-exists-in-the-sql-server-data-folder"></a><span data-ttu-id="e9cec-193">如果 SQL Server 資料庫檔案與 SQL Server 資料夾中已經存在的指定資料庫同名，組態會發生失敗</span><span class="sxs-lookup"><span data-stu-id="e9cec-193">Configuration fails if a SQL Server database file that has the same name as the specified database already exists in the SQL Server data folder</span></span>  
  
#### <a name="problem"></a><span data-ttu-id="e9cec-194">問題</span><span class="sxs-lookup"><span data-stu-id="e9cec-194">Problem</span></span>  
 <span data-ttu-id="e9cec-195">組態發生失敗，其錯誤與以下類似：</span><span class="sxs-lookup"><span data-stu-id="e9cec-195">Configuration fails with an error similar to the following:</span></span>  
  
```
Failed to set up BAM database(s)  
  
Cannot open database requested in login 'BAMPrimaryImport'  
  
Logon fails. Logon failed for user '*BizTalk\BizTalkUser*'  
```
  
<span data-ttu-id="e9cec-196">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-196">**Cause**</span></span>  
 <span data-ttu-id="e9cec-197">會發生此錯誤，如果.mdf 檔案或.ldf 檔案已經存在具有相同名稱的.mdf 檔案或.ldf 檔案的 BizTalk Server 組態程式嘗試建立的 SQL Server 執行電腦的 \MSSQL\data 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e9cec-197">This error can occur if an .mdf file or an .ldf file already exists in the \MSSQL\data folder of the computer running SQL Server that has the same name as the .mdf file or the .ldf file that the BizTalk Server configuration program is trying to create.</span></span> <span data-ttu-id="e9cec-198">針對資料庫所建立的.mdf 檔案和.ldf 檔案的名稱被衍生自指定了.mdf 和.ldf 副檔名附加 「 BizTalk Server 組態 」 程式中的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="e9cec-198">The names of the .mdf file and the .ldf file that are created for the databases are derived from the name of the database that is specified in the BizTalk Server configuration program with an .mdf and an .ldf extension appended.</span></span>  
  
<span data-ttu-id="e9cec-199">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-199">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-200">若要解決這個行為，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="e9cec-200">To resolve this behavior, use one of the following methods:</span></span>  
  
-   <span data-ttu-id="e9cec-201">刪除與您要建立之任何資料庫名稱同名的任何 .mdf 檔案或 .ldf 檔案。</span><span class="sxs-lookup"><span data-stu-id="e9cec-201">Delete any .mdf files or .ldf files that have names that match the names of any databases that you are creating.</span></span>  
  
-   <span data-ttu-id="e9cec-202">選擇使用與 SQL Server 之 \Program Files\Microsoft SQL Server\MSSQL\data 資料夾中已經存在的任何 .mdf 檔案或 .ldf 檔案不同名的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="e9cec-202">Choose database names that do not match the names of any .mdf files or .ldf files that already exist in the \Program Files\Microsoft SQL Server\MSSQL\data folder of your SQL server.</span></span>  
  
### <a name="configuration-fails-on-a-domain-controller-when-specifying-local-accounts"></a><span data-ttu-id="e9cec-203">指定本機帳戶時，網域控制站上的組態發生失敗</span><span class="sxs-lookup"><span data-stu-id="e9cec-203">Configuration fails on a domain controller when specifying local accounts</span></span>  
  
<span data-ttu-id="e9cec-204">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-204">**Problem**</span></span>  
 <span data-ttu-id="e9cec-205">當網域控制站上執行 BizTalk Server 組態程式，組態就會失敗 biztalkserverapplication 主控件或 BizTalkIsolatedHost 主機如果指定的本機群組 （例如，BizTalk 主控件使用者群組）。</span><span class="sxs-lookup"><span data-stu-id="e9cec-205">When running the BizTalk Server configuration program on a domain controller, configuration fails if you specified a local group (for example, BizTalk Host Users Group) for either the BizTalkServerApplication host or the BizTalkIsolatedHost host.</span></span>  
  
<span data-ttu-id="e9cec-206">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-206">**Cause**</span></span>  
 <span data-ttu-id="e9cec-207">網域控制站會自動將本機 Windows 群組視為網域 Windows 群組 (也就是說，網域控制站上不會有本機 Windows 群組)。</span><span class="sxs-lookup"><span data-stu-id="e9cec-207">A domain controller automatically treats a local Windows group as a domain Windows group (there is no such thing as local Windows group on a domain controller).</span></span> <span data-ttu-id="e9cec-208">如果您指定主機的本機 Windows 群組組態程式執行時，設定會在嘗試建立 SQL Server 登入群組時失敗。</span><span class="sxs-lookup"><span data-stu-id="e9cec-208">If you specified a local Windows group for the host while running the configuration program, configuration will fail when trying to create a SQL Server logon for the group.</span></span> <span data-ttu-id="e9cec-209">當伺服器是網域控制站時，組態程式不會停用本機 Windows 群組選項。</span><span class="sxs-lookup"><span data-stu-id="e9cec-209">The configuration program does not disable the local Windows group option when the server is a domain controller.</span></span>  
  
<span data-ttu-id="e9cec-210">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-210">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-211">針對組態進行期間建立的主控件指定網域群組。</span><span class="sxs-lookup"><span data-stu-id="e9cec-211">Specify domain groups for the hosts that are created during configuration.</span></span>  
  
### <a name="configuration-fails-to-create-sql-server-analysis-database-if-the-sql-server-has-been-renamed"></a><span data-ttu-id="e9cec-212">如果 SQL Server 已經重新命名，則組態程式將無法建立 SQL Server 分析資料庫</span><span class="sxs-lookup"><span data-stu-id="e9cec-212">Configuration fails to create SQL Server Analysis database if the SQL server has been renamed</span></span>  
  
<span data-ttu-id="e9cec-213">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-213">**Problem**</span></span>  
 <span data-ttu-id="e9cec-214">若您將安裝 SQL Server Analysis Server 的電腦重新命名，組態程式就無法建立新的 SQL Server 分析資料庫，而且會產生類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="e9cec-214">If you have renamed the computer on which you installed SQL Server Analysis Server, the configuration program fails when it tries to create the new SQL Server Analysis database and an error similar to the following is generated:</span></span>  

```  
 Cannot connect to the repository.  
  
 Analysis server: <machine name\>  
  
 Error:  
  
 '\\\\<machine name\>\MsOLAPRepository$\msmdrep.mdb' is not a valid path.  
  
 Make sure that you correctly spell the path name and that you are  
  
 connected to the server on which the file resides.  
```
  
<span data-ttu-id="e9cec-215">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-215">**Cause**</span></span>  
 <span data-ttu-id="e9cec-216">組態程式無法判斷安裝 SQL Server Analysis Server 之電腦的新名稱。</span><span class="sxs-lookup"><span data-stu-id="e9cec-216">The configuration program is unable to determine the new name of the computer on which you installed SQL Server Analysis Server.</span></span>  
  
<span data-ttu-id="e9cec-217">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-217">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-218">請以手動方式執行以下步驟，將 Analysis Server 更新為新的電腦名稱：</span><span class="sxs-lookup"><span data-stu-id="e9cec-218">Perform the following manual steps to update Analysis Server with the new computer name:</span></span>  
  
1.  <span data-ttu-id="e9cec-219">SQL Server 上開啟**Microsoft SQL Server**，選取**Analysis Services**，然後按一下  **Analysis Manager**。</span><span class="sxs-lookup"><span data-stu-id="e9cec-219">On the SQL Server, open **Microsoft SQL Server**, select **Analysis Services**, and then click **Analysis Manager**.</span></span>  
  
2.  <span data-ttu-id="e9cec-220">在**Analysis Manager**導覽面板中按兩下**Analysis Servers**節點來展開它。</span><span class="sxs-lookup"><span data-stu-id="e9cec-220">In the **Analysis Manager** navigation panel, double-click the **Analysis Servers** node to expand it.</span></span>  
  
3.  <span data-ttu-id="e9cec-221">以滑鼠右鍵按一下您想要編輯，然後選取 儲存機制連線字串伺服器**編輯儲存機制連線字串**。</span><span class="sxs-lookup"><span data-stu-id="e9cec-221">Right-click the server with the repository connection string you want to edit, and then select **Edit Repository Connection String**.</span></span>  
  
4.  <span data-ttu-id="e9cec-222">在**編輯儲存機制連線字串**對話方塊，確認伺服器名稱，這個字串中的，將其更新為新的電腦名稱是否正確。</span><span class="sxs-lookup"><span data-stu-id="e9cec-222">In the **Edit Repository Connection String** dialog box, verify the server name in this string and update it to the new computer name if it is incorrect.</span></span>  
  
5.  <span data-ttu-id="e9cec-223">瀏覽至下列位置： <*安裝目錄*> \Program Files\Microsoft Analysis Services\Bin。</span><span class="sxs-lookup"><span data-stu-id="e9cec-223">Navigate to the following location: <*installation directory*>\Program Files\Microsoft Analysis Services\Bin.</span></span>  
  
6.  <span data-ttu-id="e9cec-224">以滑鼠右鍵按一下**Bin**資料夾，然後再按一下**共用和安全性**。</span><span class="sxs-lookup"><span data-stu-id="e9cec-224">Right-click the **Bin** folder, and then click **Sharing and Security**.</span></span> <span data-ttu-id="e9cec-225">**Bin 屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e9cec-225">The **Bin Properties** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="e9cec-226">在**Bin 屬性**對話方塊中，按一下 **共用**索引標籤，以確認所有的線上分析處理 (OLAP) 系統管理員具有完整權限，此資料夾。</span><span class="sxs-lookup"><span data-stu-id="e9cec-226">In the **Bin Properties** dialog box, click the **Sharing** tab to verify that all Online Analytical Processing (OLAP) administrators have full permissions to this folder.</span></span>  
  
### <a name="artifacts-disappear-from-configuration-database-on-redeployment-of-assemblies-from-visual-studio"></a><span data-ttu-id="e9cec-227">重新部署組件從 Visual Studio 的成品會消失從組態資料庫</span><span class="sxs-lookup"><span data-stu-id="e9cec-227">Artifacts disappear from Configuration Database on redeployment of assemblies from Visual Studio</span></span>  
  
<span data-ttu-id="e9cec-228">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-228">**Problem**</span></span>  
 <span data-ttu-id="e9cec-229">當 BizTalk Server 專案上重新部署專案內的層級 Visual Studio 中，參考重新部署專案，將會消失，重新整理 BizTalk Server MMC 時出現在專案內所包含的所有成品。</span><span class="sxs-lookup"><span data-stu-id="e9cec-229">When a BizTalk Server project is redeployed at the project level within Visual Studio, all artifacts contained within the project that reference the project being redeployed will appear to vanish when the BizTalk Server MMC is refreshed.</span></span>  
  
<span data-ttu-id="e9cec-230">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-230">**Cause**</span></span>  
 <span data-ttu-id="e9cec-231">為了說明這個問題的原因，假設以下範例是根據範例 BizTalk Server 解決方案，而使用者想要在其中重新部署 Maps 專案。</span><span class="sxs-lookup"><span data-stu-id="e9cec-231">To illustrate the cause of this problem, consider the following example based on a sample BizTalk Server solution where a user wants to redeploy the Maps project.</span></span> <span data-ttu-id="e9cec-232">請注意，編譯專案會產生個別的組件。</span><span class="sxs-lookup"><span data-stu-id="e9cec-232">Note that compiling projects yields individual assemblies.</span></span> <span data-ttu-id="e9cec-233">下圖指示使用者執行重新部署之前的解決方案狀態，</span><span class="sxs-lookup"><span data-stu-id="e9cec-233">The following figure indicates the state of the solution before the user does a redeployment.</span></span> <span data-ttu-id="e9cec-234">成品之間的關係如下：</span><span class="sxs-lookup"><span data-stu-id="e9cec-234">The relationships among the artifacts are as follows:</span></span>  
  
-   <span data-ttu-id="e9cec-235">Orch1、Orch2、Maps、Pipelines 和 Schemas 都是專案。</span><span class="sxs-lookup"><span data-stu-id="e9cec-235">Orch1, Orch2, Maps, Pipelines, and Schemas are projects.</span></span>  
  
-   <span data-ttu-id="e9cec-236">Orch1 參考 Maps，而 Maps 則參考 Schemas。</span><span class="sxs-lookup"><span data-stu-id="e9cec-236">Orch1 references Maps, which in turn references Schemas.</span></span>  
  
-   <span data-ttu-id="e9cec-237">Orch2 參考 Schemas。</span><span class="sxs-lookup"><span data-stu-id="e9cec-237">Orch2 references Schemas.</span></span>  
  
-   <span data-ttu-id="e9cec-238">Pipelines 參考 Schemas。</span><span class="sxs-lookup"><span data-stu-id="e9cec-238">Pipelines references Schemas.</span></span>  
  
![bcd_ExistingBizTalkServerSolutionc](../install-and-config-guides/media/bcd_ExistingBizTalkServerSolutionc.gif)  
  
<span data-ttu-id="e9cec-240">如果使用者使用預設 Visual Studio 專案設定來重新部署 Maps 專案，則 Orch1、Orch2 和 Pipeline 成品會消失，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e9cec-240">If the user redeploys the Maps project using the default Visual Studio project settings, the Orch1, Orch2, and Pipeline artifacts vanish, as shown in the following figure.</span></span>  
  
![bcd_BizTalkSolutionWLostArtifactsc](../install-and-config-guides/media/bcd_BizTalkSolutionWLostArtifactsc.gif)  
  
 <span data-ttu-id="e9cec-242">重新部署 Maps 是一個兩個步驟的程序，要先解除部署目前已部署的 Maps.dll 組件，然後部署新的 Maps.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="e9cec-242">Redeploying Maps is a two-step process of undeploying the currently deployed Maps.dll assembly, and then deploying the new Maps.dll file.</span></span> <span data-ttu-id="e9cec-243">Visual Studio 重新部署程序的一部分，請以自動執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="e9cec-243">Visual Studio performs these steps automatically as part of the redeployment process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9cec-244">上一個句子嚴格來說並不正確，因為 Visual Studio 一定會執行這些步驟，所以它不會意識到這是適當的作法。</span><span class="sxs-lookup"><span data-stu-id="e9cec-244">The preceding sentence is not strictly correct because these are steps that Visual Studio always does so there is no notion of it being the proper way.</span></span>  
  
 <span data-ttu-id="e9cec-245">重點，是為了要解除部署 BizTalk Server 組件，Visual Studio 解除部署所有組件相依於該組件包含設定部署旗標。</span><span class="sxs-lookup"><span data-stu-id="e9cec-245">The key point is that in order to undeploy a BizTalk Server assembly, Visual Studio has to undeploy all assemblies that are dependent upon that assembly that have the deploy flag set.</span></span> <span data-ttu-id="e9cec-246">在這個範例中，若要執行重新部署的第一個解除部署步驟，BizTalk Server 需要解除部署 Orch1.dll (它相依於 Maps.dll)。</span><span class="sxs-lookup"><span data-stu-id="e9cec-246">In our example, to perform the first undeployment step of the redeployment, BizTalk Server needs to undeploy Orch1.dll (which depends on Maps.dll).</span></span> <span data-ttu-id="e9cec-247">在 解除部署 maps.dll 時，Visual Studio 也會解除部署 Schemas.dll （假設它已設定部署旗標）。</span><span class="sxs-lookup"><span data-stu-id="e9cec-247">During the undeployment of Maps.dll, Visual Studio also undeploys Schemas.dll (assuming it has the deploy flag set).</span></span> <span data-ttu-id="e9cec-248">為了要解除部署 Schemas.dll，Visual Studio 需要解除部署 Orch2.dll 和 Pipelines.dll (這兩者都相依於 Schemas.dll)。</span><span class="sxs-lookup"><span data-stu-id="e9cec-248">In order to undeploy Schemas.dll, Visual Studio needs to undeploy Orch2.dll and Pipelines.dll (both of which depend on Schemas.dll).</span></span>  
  
 <span data-ttu-id="e9cec-249">有問題存在，Visual Studio 重新部署，只有 Maps.dll 和它所依據的組件： 在此情況下，Schemas.dll。</span><span class="sxs-lookup"><span data-stu-id="e9cec-249">A problem exists in that Visual Studio redeploys only Maps.dll and the assemblies that it depends upon: in this case, Schemas.dll.</span></span> <span data-ttu-id="e9cec-250">讓使用者重新整理 BizTalk Server MMC 時，Orch1、 Orch2 和 Pipeline 組件似乎已消失，但是 Maps.dll 和 Schemas.dll 仍然可見。</span><span class="sxs-lookup"><span data-stu-id="e9cec-250">So when the user refreshes the BizTalk Server MMC, the Orch1, Orch2, and Pipeline assemblies seem to have vanished, but Maps.dll and Schemas.dll are still visible.</span></span>  
  
<span data-ttu-id="e9cec-251">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-251">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-252">如果是主要專案 (它會參考其他專案)，請執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="e9cec-252">For the main project (that references other projects) do the following:</span></span>  
  
1.  <span data-ttu-id="e9cec-253">在 [方案總管] 中，以滑鼠右鍵按一下方案節點。</span><span class="sxs-lookup"><span data-stu-id="e9cec-253">In Solution Explorer, right-click the solution node.</span></span>  
  
2.  <span data-ttu-id="e9cec-254">按一下**屬性**開啟**方案屬性頁** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e9cec-254">Click **Properties** to open the **Solution Property Pages** dialog box.</span></span>  
  
3.  <span data-ttu-id="e9cec-255">按一下**組態屬性**，然後按一下 **組態**。</span><span class="sxs-lookup"><span data-stu-id="e9cec-255">Click **Configuration Properties**, and then click **Configuration**.</span></span>  
  
4.  <span data-ttu-id="e9cec-256">清除**部署**參考之專案的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e9cec-256">Clear the **Deploy** check box for the referenced project.</span></span>  
  
5.  <span data-ttu-id="e9cec-257">在 [方案總管] 中，執行新的方案層級部署。</span><span class="sxs-lookup"><span data-stu-id="e9cec-257">In Solution Explorer, execute a new solution-level deployment.</span></span> <span data-ttu-id="e9cec-258">若要這樣做，以滑鼠右鍵按一下方案節點，然後按一下 **部署方案**。</span><span class="sxs-lookup"><span data-stu-id="e9cec-258">To do this, right-click the solution node and then click **Deploy Solution**.</span></span>  
  
### <a name="supported-virtual-directory-types"></a><span data-ttu-id="e9cec-259">支援的虛擬目錄類型</span><span class="sxs-lookup"><span data-stu-id="e9cec-259">Supported Virtual Directory Types</span></span>  
 <span data-ttu-id="e9cec-260">匯出作業時參考 Web 服務從協調流程，並嘗試進行 MSI 匯出，將會成功，相關聯的虛擬目錄為型別時，才**IIsWebVirtualDir**或**IIsWebDirectory**.</span><span class="sxs-lookup"><span data-stu-id="e9cec-260">When referencing Web services from an orchestration and attempting to do an MSI export, the export operation will succeed only if the associated virtual directories are of type **IIsWebVirtualDir** or **IIsWebDirectory**.</span></span> <span data-ttu-id="e9cec-261">**IIsWebVirtualDir**和**IIsWebDirectory**會出現在 IIS metabase 中的節點型別。</span><span class="sxs-lookup"><span data-stu-id="e9cec-261">**IIsWebVirtualDir** and **IIsWebDirectory** are the node types that appear in the IIS metabase.</span></span> <span data-ttu-id="e9cec-262">**IIsWebVirtualDir**是使用的虛擬目錄**路徑**指向絕對檔案資料夾的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9cec-262">**IIsWebVirtualDir** is a virtual directory with a **Path** property that points to an absolute file folder.</span></span> <span data-ttu-id="e9cec-263">**IIsWebDirectory**而不是虛擬目錄**路徑**屬性，因此是指相對檔案資料夾，通常是另一個子資料夾**IIsWebVirtualDir**或**IIsWebDirectory**節點。</span><span class="sxs-lookup"><span data-stu-id="e9cec-263">**IIsWebDirectory** is a virtual directory without a **Path** property and thus refers to a relative file folder, typically a subfolder of another **IIsWebVirtualDir** or **IIsWebDirectory** node.</span></span> <span data-ttu-id="e9cec-264">在 Metabase 階層中，經常會看到用來描述資料夾的這兩個類型。</span><span class="sxs-lookup"><span data-stu-id="e9cec-264">These two types are the ones typically seen in the metabase hierarchy to describe folders.</span></span>  
  
 <span data-ttu-id="e9cec-265">類型的虛擬目錄**IIsConfigObject**不支援 MSI 匯出會在此情況下失敗。</span><span class="sxs-lookup"><span data-stu-id="e9cec-265">Virtual directories of type **IIsConfigObject** are not supported and the MSI export will fail in this case.</span></span> <span data-ttu-id="e9cec-266">**IIsConfigObject**非預期的 metabase 節點類型可以是 BizTalk Server 未適當處理的有效節點類型，或未適當建立的 （並因此它是無效的） metabase 項目的指示。</span><span class="sxs-lookup"><span data-stu-id="e9cec-266">**IIsConfigObject** is an unexpected metabase node type that is either a valid node type that BizTalk Server is not handling properly or an indication of an improperly created (and thus invalid) metabase entry.</span></span> <span data-ttu-id="e9cec-267">在此情況下，BizTalk Server 將會顯示類似下列的錯誤訊息： 類型 IIsConfigObject 的未預期的目錄項目"Iis: //lm/w3svc/1/root/badvdir/"。</span><span class="sxs-lookup"><span data-stu-id="e9cec-267">In this situation BizTalk Server will display an error message something like the following: Unexpected directory entry " IIS://LM/W3SVC/1/ROOT/BadVdir/" of type IIsConfigObject.</span></span>  
  
### <a name="unable-to-view-group-information-after-removing-stale-logons"></a><span data-ttu-id="e9cec-268">在移除過時的登入之後，無法檢視群組資訊</span><span class="sxs-lookup"><span data-stu-id="e9cec-268">Unable to view Group information after removing stale logons</span></span>  
  
<span data-ttu-id="e9cec-269">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-269">**Problem**</span></span>  
 <span data-ttu-id="e9cec-270">如果在組態進行期間，您發現了過時的登入並將它刪除，您可能就無法檢視群組資訊。</span><span class="sxs-lookup"><span data-stu-id="e9cec-270">If, during configuration, you encounter and delete stale logons, you may not be able to view Group information.</span></span>  
  
<span data-ttu-id="e9cec-271">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-271">**Cause**</span></span>  
 <span data-ttu-id="e9cec-272">這是已知的組態問題。</span><span class="sxs-lookup"><span data-stu-id="e9cec-272">This is a known configuration issue.</span></span>  
  
<span data-ttu-id="e9cec-273">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-273">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-274">刪除主控件 Windows 群組登入，然後再重新設定可能會有幫助。</span><span class="sxs-lookup"><span data-stu-id="e9cec-274">It may help to delete the Host Windows group logons and then reconfigure.</span></span> <span data-ttu-id="e9cec-275">如果仍然無法使用群組資訊，請連絡 Microsoft 產品支援中心。</span><span class="sxs-lookup"><span data-stu-id="e9cec-275">If the Group information is still not available, contact Microsoft Product Support.</span></span>  
  
### <a name="cannot-change-computer-name-after-biztalk-server-is-installed"></a><span data-ttu-id="e9cec-276">BizTalk Server 安裝之後，無法變更電腦名稱</span><span class="sxs-lookup"><span data-stu-id="e9cec-276">Cannot change computer name after BizTalk Server is installed</span></span>  
  
<span data-ttu-id="e9cec-277">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-277">**Problem**</span></span>  
 <span data-ttu-id="e9cec-278">當您變更執行 BizTalk Server 的電腦上的電腦名稱，而且您重新啟動 （） 將電腦重新開機，錯誤訊息可能會發生。</span><span class="sxs-lookup"><span data-stu-id="e9cec-278">When you change the computer name on a computer running BizTalk Server, and you restart (reboot) the computer, error messages may occur.</span></span>  
  
<span data-ttu-id="e9cec-279">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-279">**Cause**</span></span>  
 <span data-ttu-id="e9cec-280">SQL Server 不支援變更電腦名稱，因此 BizTalk Server 不支援 BizTalk Server 會安裝和設定後變更電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="e9cec-280">SQL Server does not support changing the computer name, so BizTalk Server does not support changing the computer name once BizTalk Server is installed and configured.</span></span>  
  
<span data-ttu-id="e9cec-281">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-281">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-282">我們建議您不要變更電腦名稱之後您安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="e9cec-282">We recommend that you do not change computer names after you install BizTalk Server.</span></span>  
  
### <a name="known-issues-with-enterprise-single-sign-on"></a><span data-ttu-id="e9cec-283">企業單一登入的已知的問題</span><span class="sxs-lookup"><span data-stu-id="e9cec-283">Known Issues with Enterprise Single Sign-On</span></span>  
 <span data-ttu-id="e9cec-284">本章節描述可能相關以企業單一登入 (SSO) 的安裝和組態問題。</span><span class="sxs-lookup"><span data-stu-id="e9cec-284">This section describes setup and configuration problems that may be related to Enterprise Single Sign-On (SSO).</span></span>  
  
##### <a name="entsso-service-fails-to-start"></a><span data-ttu-id="e9cec-285">ENTSSO 服務無法啟動</span><span class="sxs-lookup"><span data-stu-id="e9cec-285">ENTSSO Service fails to start</span></span>  
  
<span data-ttu-id="e9cec-286">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-286">**Problem**</span></span>  
 <span data-ttu-id="e9cec-287">ENTSSO 服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="e9cec-287">The ENTSSO service fails to start.</span></span>  
  
<span data-ttu-id="e9cec-288">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-288">**Cause**</span></span>  
 <span data-ttu-id="e9cec-289">如果 ENTSSO 服務不是以有效的 SSO 系統管理員帳戶執行，便無法啟動。</span><span class="sxs-lookup"><span data-stu-id="e9cec-289">If the ENTSSO service is not running under a valid SSO Administrator account, it will fail to start.</span></span>  
  
<span data-ttu-id="e9cec-290">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-290">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-291">為 ENTSSO 服務指定有效的 SSO 系統管理員帳戶，並從服務控制管理員 (SCM) 嵌入式管理單元重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="e9cec-291">Specify a valid SSO administrator account for the ENTSSO Service and restart the service from Services Control Manager (SCM) snap-in.</span></span>  
  
##### <a name="biztalk-services-dependent-on-the-enterprise-single-sign-on-service-entsso-fail-to-start-after-a-reboot"></a><span data-ttu-id="e9cec-292">BizTalk 服務相依於企業單一登入服務 (ENTSSO) 無法在重新開機後啟動</span><span class="sxs-lookup"><span data-stu-id="e9cec-292">BizTalk Services dependent on the Enterprise Single Sign-On Service (ENTSSO) fail to start after a reboot</span></span>  
  
<span data-ttu-id="e9cec-293">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-293">**Problem**</span></span>  
 <span data-ttu-id="e9cec-294">BTSSvc$BizTalkServerApplication 相依於企業單一登入服務 (ENTSSO)，重新開機後可能會在啟動時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="e9cec-294">BTSSvc$BizTalkServerApplication has a dependency on the Enterprise Single Sign-On Service (ENTSSO) and may timeout during start up after a reboot.</span></span>  
  
<span data-ttu-id="e9cec-295">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-295">**Cause**</span></span>  
 <span data-ttu-id="e9cec-296">企業單一登入服務可能需要約 3 分鐘的時間才能啟動。</span><span class="sxs-lookup"><span data-stu-id="e9cec-296">The Enterprise Single Sign-On Service may take around 3 minutes to start.</span></span>  
  
<span data-ttu-id="e9cec-297">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-297">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-298">將 “BizTalk Service BizTalk Group：BizTalkServerApplication” 服務的啟動類型選項設定為 [自動 (延遲開始)]。</span><span class="sxs-lookup"><span data-stu-id="e9cec-298">Configure the “BizTalk Service BizTalk Group: BizTalkServerApplication” service with the Automatic (Delayed Start) startup type option.</span></span> <span data-ttu-id="e9cec-299">這會在所有自動服務皆完成啟動程序後，再啟動該服務。</span><span class="sxs-lookup"><span data-stu-id="e9cec-299">This will initiate the start of the service after all Automatic services have completed their startup routines.</span></span>  
  
##### <a name="cannot-access-an-affiliate-application"></a><span data-ttu-id="e9cec-300">無法存取分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="e9cec-300">Cannot access an affiliate application</span></span>  
  
<span data-ttu-id="e9cec-301">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-301">**Problem**</span></span>  
 <span data-ttu-id="e9cec-302">如果與分支機構應用程式相關聯的應用程式系統管理員帳戶無效，企業單一登入服務就會停用該分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9cec-302">The Enterprise Single Sign-On service disables an affiliate application if the application administrator account associated with it is not valid.</span></span>  
  
<span data-ttu-id="e9cec-303">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-303">**Cause**</span></span>  
 <span data-ttu-id="e9cec-304">SSO 應用程式系統管理員帳戶無效。</span><span class="sxs-lookup"><span data-stu-id="e9cec-304">The SSO application administrator account is not valid.</span></span>  
  
<span data-ttu-id="e9cec-305">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-305">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-306">建立分支機構應用程式之前，請先確定 SSO 應用程式系統管理員帳戶是否有效。</span><span class="sxs-lookup"><span data-stu-id="e9cec-306">Ensure that the SSO application administrator account is valid before you create an affiliate application.</span></span> <span data-ttu-id="e9cec-307">接著，您必須啟用分支機構應用程式，才能使用該應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9cec-307">You must then enable the affiliate application to use the application.</span></span>  
  
##### <a name="rpc-error-occurs-when-connecting-to-a-client-computer"></a><span data-ttu-id="e9cec-308">連接到用戶端電腦時，就會發生 RPC 錯誤</span><span class="sxs-lookup"><span data-stu-id="e9cec-308">RPC error occurs when connecting to a client computer</span></span>  
  
<span data-ttu-id="e9cec-309">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-309">**Problem**</span></span>  
 <span data-ttu-id="e9cec-310">當您執行命令，例如**ssomanage-displayapp** *< applicationname\>*，其中電腦嘗試連線到遠端 SSO 伺服器以擷取資訊，您會收到下列錯誤： 錯誤： 0x800706BA: RPC 伺服器不存在。</span><span class="sxs-lookup"><span data-stu-id="e9cec-310">When you run a command such as **ssomanage -displayapp** *<applicationname\>*, where the computer attempt to connect to a remote SSO Server to retrieve the information, you receive the following error: ERROR: 0x800706BA: The RPC server is unavailable.</span></span>  
  
<span data-ttu-id="e9cec-311">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-311">**Cause**</span></span>  
 <span data-ttu-id="e9cec-312">當您指定錯誤的伺服器資訊，或無法使用遠端伺服器上的 SSO 服務時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9cec-312">This error occurs when you specify the wrong server information, or when the SSO Service is not available on the remote server.</span></span>  
  
<span data-ttu-id="e9cec-313">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-313">**Resolution**</span></span>  
  
-   <span data-ttu-id="e9cec-314">請依照[設定 SSO 伺服器](../core/how-to-set-the-sso-server.md)來確認您已連接到正確的 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e9cec-314">Follow the steps in [Set the SSO Server](../core/how-to-set-the-sso-server.md) to make sure you are connected to the correct SSO Server.</span></span>  
  
-   <span data-ttu-id="e9cec-315">確定 SSO 服務已在您所連接的 SSO 伺服器上啟用及執行。</span><span class="sxs-lookup"><span data-stu-id="e9cec-315">Make sure the SSO Service is enabled and running in the SSO Server to which you are connecting.</span></span>  
  
##### <a name="master-secret-is-missing-or-corrupt"></a><span data-ttu-id="e9cec-316">主要密碼已遺失或損毀</span><span class="sxs-lookup"><span data-stu-id="e9cec-316">Master Secret is missing or corrupt</span></span>  
  
<span data-ttu-id="e9cec-317">**問題**</span><span class="sxs-lookup"><span data-stu-id="e9cec-317">**Problem**</span></span>  
 <span data-ttu-id="e9cec-318">主要密碼遺漏或損毀。</span><span class="sxs-lookup"><span data-stu-id="e9cec-318">The master secret is missing or corrupt.</span></span> <span data-ttu-id="e9cec-319">這個密碼通常會在設定組態時產生。</span><span class="sxs-lookup"><span data-stu-id="e9cec-319">It normally generates during configuration.</span></span> <span data-ttu-id="e9cec-320">若遺漏此密碼，則企業單一登入服務啟動時，事件記錄中就會出現下列其中一則訊息。</span><span class="sxs-lookup"><span data-stu-id="e9cec-320">If the secret is missing, one of the following messages will display in the event log as the Enterprise Single Sign-On service starts.</span></span>  
  
```
MessageId=10520  
Severity=Warning  
SSO_WARN_NO_SECRETS  
MessageId=10565  
Severity=Error  
SSO_ERROR_SECRET_VALIDATE_FAILED  
MessageId=10521  
Severity=Error  
SSO_ERROR_SECRETS_NOT_LOADED  
```

<span data-ttu-id="e9cec-321">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="e9cec-321">**Cause**</span></span>  
 <span data-ttu-id="e9cec-322">如果密碼是在企業單一登入服務 (SSO) 使用某個服務帳戶執行時產生，但後來服務帳戶發生變更，就有可能發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="e9cec-322">This problem can occur if a secret is generated while the Enterprise Single Sign-On service (SSO) was running under one service account, and then the service account was changed.</span></span> <span data-ttu-id="e9cec-323">此密碼是以加密的形式儲存在登錄中，加密時則是使用依據服務帳戶 (用來執行 ENTSSO 者) 的識別所產生的金鑰。</span><span class="sxs-lookup"><span data-stu-id="e9cec-323">The secret is stored in the registry in encrypted form, and is encrypted using a key based on the identity of the service account (which ENTSSO runs under).</span></span>  
  
<span data-ttu-id="e9cec-324">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="e9cec-324">**Resolution**</span></span>  
 <span data-ttu-id="e9cec-325">將 ENTSSO 執行時所用的服務帳戶變更為建立主要密碼時的原始服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="e9cec-325">Change the service account ENTSSO is running under to the original service account when the master secret was created.</span></span>  
  
1.  <span data-ttu-id="e9cec-326">備份主要密碼。</span><span class="sxs-lookup"><span data-stu-id="e9cec-326">Back up the master secret.</span></span> <span data-ttu-id="e9cec-327">請參閱[備份主要密碼](../core/how-to-back-up-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="e9cec-327">See [Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span></span>  
  
2.  <span data-ttu-id="e9cec-328">停止企業單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="e9cec-328">Stop Enterprise Single Sign-On Services.</span></span>  
  
3.  <span data-ttu-id="e9cec-329">變更服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="e9cec-329">Change the service account.</span></span>  
  
4.  <span data-ttu-id="e9cec-330">重新啟動 SSO，並忽略任何與密碼損毀有關的事件記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9cec-330">Restart SSO and ignore any event log errors about a corrupted secret.</span></span>  
  
5.  <span data-ttu-id="e9cec-331">還原主要密碼。</span><span class="sxs-lookup"><span data-stu-id="e9cec-331">Restore the master secret.</span></span> <span data-ttu-id="e9cec-332">請參閱[還原主要密碼](../core/how-to-restore-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="e9cec-332">See [Restore the Master Secret](../core/how-to-restore-the-master-secret.md).</span></span>  
  
### <a name="custom-action"></a><span data-ttu-id="e9cec-333">自訂動作</span><span class="sxs-lookup"><span data-stu-id="e9cec-333">Custom Action</span></span>  
 <span data-ttu-id="e9cec-334">本主題提供有關 Windows Server logo program BizTalk 伺服器憑證的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e9cec-334">This topic provides details about BizTalk Server certification for the Windows Server logo program.</span></span> <span data-ttu-id="e9cec-335">BizTalk Server 安裝程式作業期間，可能會執行下列自訂動作。</span><span class="sxs-lookup"><span data-stu-id="e9cec-335">The following custom actions might be performed during BizTalk Server Setup operations.</span></span>  
  
|<span data-ttu-id="e9cec-336">自訂動作</span><span class="sxs-lookup"><span data-stu-id="e9cec-336">Custom action</span></span>|<span data-ttu-id="e9cec-337">Description</span><span class="sxs-lookup"><span data-stu-id="e9cec-337">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="e9cec-338">ReadComplusData</span><span class="sxs-lookup"><span data-stu-id="e9cec-338">ReadComplusData</span></span>|<span data-ttu-id="e9cec-339">讀取自訂 COM + 資料表，建立 XML 文件，並將它儲存在 Complus_XML_Data 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9cec-339">Reads custom COM+ tables, creates XML document, and saves it in the Complus_XML_Data property.</span></span>|  
|<span data-ttu-id="e9cec-340">SchedXmlConfig</span><span class="sxs-lookup"><span data-stu-id="e9cec-340">SchedXmlConfig</span></span>|<span data-ttu-id="e9cec-341">用於設定 RFID 資料的電腦。</span><span class="sxs-lookup"><span data-stu-id="e9cec-341">Used for configuring machines having RFID data.</span></span>|  
|<span data-ttu-id="e9cec-342">CheckBaseEDI</span><span class="sxs-lookup"><span data-stu-id="e9cec-342">CheckBaseEDI</span></span>|<span data-ttu-id="e9cec-343">檢查是否有舊版 EDI 存在</span><span class="sxs-lookup"><span data-stu-id="e9cec-343">Checks the presence of an old version of EDI</span></span>|  
|<span data-ttu-id="e9cec-344">CheckMQSeries</span><span class="sxs-lookup"><span data-stu-id="e9cec-344">CheckMQSeries</span></span>|<span data-ttu-id="e9cec-345">檢查是否有 MQSeries 存在</span><span class="sxs-lookup"><span data-stu-id="e9cec-345">Checks the presence of MQSeries</span></span>|  
|<span data-ttu-id="e9cec-346">CheckNET30Vista</span><span class="sxs-lookup"><span data-stu-id="e9cec-346">CheckNET30Vista</span></span>|<span data-ttu-id="e9cec-347">檢查是否有 WCF 存在</span><span class="sxs-lookup"><span data-stu-id="e9cec-347">Checks the presence of WCF</span></span>|  
|<span data-ttu-id="e9cec-348">CheckWSSV3SP1</span><span class="sxs-lookup"><span data-stu-id="e9cec-348">CheckWSSV3SP1</span></span>|<span data-ttu-id="e9cec-349">檢查是否有 Windows SharePoint Services 3.0 SP1 存在。</span><span class="sxs-lookup"><span data-stu-id="e9cec-349">Checks the presence of Windows SharePoint Services 3.0 SP1.</span></span>|  
|<span data-ttu-id="e9cec-350">CheckWSSV4</span><span class="sxs-lookup"><span data-stu-id="e9cec-350">CheckWSSV4</span></span>|<span data-ttu-id="e9cec-351">檢查 Windows SharePoint Services 4 存在</span><span class="sxs-lookup"><span data-stu-id="e9cec-351">Checks the presence of Windows SharePoint Services 4</span></span>|  
|<span data-ttu-id="e9cec-352">GetFrameworkPath</span><span class="sxs-lookup"><span data-stu-id="e9cec-352">GetFrameworkPath</span></span>|<span data-ttu-id="e9cec-353">Microsoft.Net framework 4 和 2.0 會保留安裝路徑，安裝程式在設定安裝程式屬性。</span><span class="sxs-lookup"><span data-stu-id="e9cec-353">Sets installer properties in the installer that holds installation path to Microsoft .Net framework 4 and 2.0.</span></span>|  
|<span data-ttu-id="e9cec-354">Set_BAMClientExcelDir</span><span class="sxs-lookup"><span data-stu-id="e9cec-354">Set_BAMClientExcelDir</span></span>|<span data-ttu-id="e9cec-355">建立 Excel 應用程式物件的屬性設定為在安裝程式中保留的 Microsoft Office 文件庫的路徑。</span><span class="sxs-lookup"><span data-stu-id="e9cec-355">Creates an Excel application object for setting a property to hold the Microsoft Office library path in the installer.</span></span>|  
|<span data-ttu-id="e9cec-356">Set_CurrentUser</span><span class="sxs-lookup"><span data-stu-id="e9cec-356">Set_CurrentUser</span></span>|<span data-ttu-id="e9cec-357">設定目前使用者的網域 \ 使用者名稱資訊</span><span class="sxs-lookup"><span data-stu-id="e9cec-357">Sets domain\username information of the current user</span></span>|  
|<span data-ttu-id="e9cec-358">ViewInstallGuide</span><span class="sxs-lookup"><span data-stu-id="e9cec-358">ViewInstallGuide</span></span>|<span data-ttu-id="e9cec-359">啟動 BizTalk Server 安裝指南，從安裝來源目錄。</span><span class="sxs-lookup"><span data-stu-id="e9cec-359">Launches the BizTalk Server installation guide from the installation source directory.</span></span>|  
|<span data-ttu-id="e9cec-360">CA_CheckSTSLanguage</span><span class="sxs-lookup"><span data-stu-id="e9cec-360">CA_CheckSTSLanguage</span></span>|<span data-ttu-id="e9cec-361">WSS 和 BizTalk 設定的語言相同時，請設定 STS_Language_Property 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9cec-361">Sets STS_Language_Property property when the language set for WSS and BizTalk are same.</span></span>|  
|<span data-ttu-id="e9cec-362">CA_CleanupRegistry</span><span class="sxs-lookup"><span data-stu-id="e9cec-362">CA_CleanupRegistry</span></span>|<span data-ttu-id="e9cec-363">當您解除安裝 BizTalk Server 時，它會清除 BizTalk Server 組態期間所建立的登錄項目。</span><span class="sxs-lookup"><span data-stu-id="e9cec-363">When you uninstall BizTalk Server, it cleans the registry entries that were created during BizTalk Server configuration.</span></span>|  
|<span data-ttu-id="e9cec-364">CA_CleanupRegistry_OldProducts</span><span class="sxs-lookup"><span data-stu-id="e9cec-364">CA_CleanupRegistry_OldProducts</span></span>|<span data-ttu-id="e9cec-365">會清除屬於較舊版本的 BizTalk Server，而且不需要的 BizTalk Server 的全新安裝的登錄項目。</span><span class="sxs-lookup"><span data-stu-id="e9cec-365">Cleans the registry entries that belong to an older version of BizTalk Server and are not required for a fresh installation of BizTalk Server.</span></span>|  
|<span data-ttu-id="e9cec-366">CA_RemovePatches</span><span class="sxs-lookup"><span data-stu-id="e9cec-366">CA_RemovePatches</span></span>|<span data-ttu-id="e9cec-367">當您解除安裝 BizTalk Server 時，請移除 Microsoft BizTalk Server 更新。</span><span class="sxs-lookup"><span data-stu-id="e9cec-367">Removes Microsoft BizTalk Server updates when you uninstall BizTalk Server.</span></span>|  
|<span data-ttu-id="e9cec-368">CA_ResolveWellKnownNames</span><span class="sxs-lookup"><span data-stu-id="e9cec-368">CA_ResolveWellKnownNames</span></span>|<span data-ttu-id="e9cec-369">建立安裝程式的屬性與已知的名稱，並將它們指派對應 SID。</span><span class="sxs-lookup"><span data-stu-id="e9cec-369">Creates installer properties with well-known names and assigns them their corresponding SID.</span></span>|  
|<span data-ttu-id="e9cec-370">CA_SaveTargetVSVersionToRegistry</span><span class="sxs-lookup"><span data-stu-id="e9cec-370">CA_SaveTargetVSVersionToRegistry</span></span>|<span data-ttu-id="e9cec-371">將 TargetVSVersion_Property 屬性設定為支援的 Visual Studio 版本的值。</span><span class="sxs-lookup"><span data-stu-id="e9cec-371">Sets a TargetVSVersion_Property property to the value of a supported version of Visual Studio.</span></span>|  
|<span data-ttu-id="e9cec-372">CA_StopServices</span><span class="sxs-lookup"><span data-stu-id="e9cec-372">CA_StopServices</span></span>|<span data-ttu-id="e9cec-373">停止 IISAdmin、 規則引擎更新，以及 EDI 子系統服務。</span><span class="sxs-lookup"><span data-stu-id="e9cec-373">Stops IISAdmin, Rules Engine Update and EDI Subsystem services.</span></span>|  
|<span data-ttu-id="e9cec-374">CleanupUsersKeys</span><span class="sxs-lookup"><span data-stu-id="e9cec-374">CleanupUsersKeys</span></span>|<span data-ttu-id="e9cec-375">移除 BizTalk Server 從 HKEY_CURRENT_USER 登錄機碼相關項目。</span><span class="sxs-lookup"><span data-stu-id="e9cec-375">Removes BizTalk Server related entries from the HKEY_CURRENT_USER registry key.</span></span>|  
|<span data-ttu-id="e9cec-376">DevEnvRunning</span><span class="sxs-lookup"><span data-stu-id="e9cec-376">DevEnvRunning</span></span>|<span data-ttu-id="e9cec-377">檢查是否正在執行 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e9cec-377">Checks whether Visual Studio is running</span></span>|  
|<span data-ttu-id="e9cec-378">ValidateINSTALLDIR</span><span class="sxs-lookup"><span data-stu-id="e9cec-378">ValidateINSTALLDIR</span></span>|<span data-ttu-id="e9cec-379">驗證 BizTalk Server 安裝目錄的格式</span><span class="sxs-lookup"><span data-stu-id="e9cec-379">Validates BizTalk Server installation directory format</span></span>|  
|<span data-ttu-id="e9cec-380">StartHostInstances</span><span class="sxs-lookup"><span data-stu-id="e9cec-380">StartHostInstances</span></span>|<span data-ttu-id="e9cec-381">啟動 BizTalk Server 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e9cec-381">Starts BizTalk Server Host Instances.</span></span>|  
|<span data-ttu-id="e9cec-382">StopHostInstances</span><span class="sxs-lookup"><span data-stu-id="e9cec-382">StopHostInstances</span></span>|<span data-ttu-id="e9cec-383">停止 BizTalk Server 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e9cec-383">Stops BizTalk Server Host Instances.</span></span>|  
|<span data-ttu-id="e9cec-384">MQSUnConfig</span><span class="sxs-lookup"><span data-stu-id="e9cec-384">MQSUnConfig</span></span>|<span data-ttu-id="e9cec-385">啟動 MQSeries 組態精靈，如未設定 MQSeries 代理程式。</span><span class="sxs-lookup"><span data-stu-id="e9cec-385">Launches MQSeries Configuration wizard for un-configuring MQSeries agent.</span></span>|  
|<span data-ttu-id="e9cec-386">LaunchConfigFmk</span><span class="sxs-lookup"><span data-stu-id="e9cec-386">LaunchConfigFmk</span></span>|<span data-ttu-id="e9cec-387">啟動 BizTalk Server 組態精靈</span><span class="sxs-lookup"><span data-stu-id="e9cec-387">Launches BizTalk Server Configuration Wizard</span></span>|  
|<span data-ttu-id="e9cec-388">CHKASPNET</span><span class="sxs-lookup"><span data-stu-id="e9cec-388">CHKASPNET</span></span>|<span data-ttu-id="e9cec-389">會檢查 ASP.NET 的安裝狀態</span><span class="sxs-lookup"><span data-stu-id="e9cec-389">Checks the install state of ASP.NET</span></span>|  
|<span data-ttu-id="e9cec-390">CHKIIS</span><span class="sxs-lookup"><span data-stu-id="e9cec-390">CHKIIS</span></span>|<span data-ttu-id="e9cec-391">檢查 IIS 的安裝狀態</span><span class="sxs-lookup"><span data-stu-id="e9cec-391">Checks the install state of IIS</span></span>|  
|<span data-ttu-id="e9cec-392">TBExpired</span><span class="sxs-lookup"><span data-stu-id="e9cec-392">TBExpired</span></span>|<span data-ttu-id="e9cec-393">檢查是否已過期 BizTalk Server 使用期限時發生</span><span class="sxs-lookup"><span data-stu-id="e9cec-393">Checks if the BizTalk Server TimeBomb has expired</span></span>|  
|<span data-ttu-id="e9cec-394">BrandSKU</span><span class="sxs-lookup"><span data-stu-id="e9cec-394">BrandSKU</span></span>|<span data-ttu-id="e9cec-395">更新 BizTalk Server 使用期限時發生的 SKU 安裝而定的值。</span><span class="sxs-lookup"><span data-stu-id="e9cec-395">Updates the value of BizTalk Server timebomb which depends on SKU installation.</span></span>|  
|<span data-ttu-id="e9cec-396">CA_ERROR</span><span class="sxs-lookup"><span data-stu-id="e9cec-396">CA_ERROR</span></span>|<span data-ttu-id="e9cec-397">傳回安裝失敗</span><span class="sxs-lookup"><span data-stu-id="e9cec-397">Returns installation failure</span></span>|  
|<span data-ttu-id="e9cec-398">InstallComplus</span><span class="sxs-lookup"><span data-stu-id="e9cec-398">InstallComplus</span></span>|<span data-ttu-id="e9cec-399">安裝 Complus 應用程式和元件。</span><span class="sxs-lookup"><span data-stu-id="e9cec-399">Installs Complus applications and components.</span></span>|  
|<span data-ttu-id="e9cec-400">BAM_Add_Perf_Silent</span><span class="sxs-lookup"><span data-stu-id="e9cec-400">BAM_Add_Perf_Silent</span></span>|<span data-ttu-id="e9cec-401">安裝 BAM 的效能計數器</span><span class="sxs-lookup"><span data-stu-id="e9cec-401">Installs performance counters for BAM</span></span>|  
|<span data-ttu-id="e9cec-402">RegsvcsApplicationDeployment</span><span class="sxs-lookup"><span data-stu-id="e9cec-402">RegsvcsApplicationDeployment</span></span>|<span data-ttu-id="e9cec-403">在 BizTalk 部署 COM + 應用程式 Dll 上執行 Regsvcs.exe （.NET 服務安裝工具）</span><span class="sxs-lookup"><span data-stu-id="e9cec-403">Runs Regsvcs.exe (.NET Services Installation Tool) on BizTalk Deployment COM+ application DLLs</span></span>|  
|<span data-ttu-id="e9cec-404">RegsvcsDeployment</span><span class="sxs-lookup"><span data-stu-id="e9cec-404">RegsvcsDeployment</span></span>|<span data-ttu-id="e9cec-405">在 Dll 上執行 Regsvcs.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-405">Runs Regsvcs.exe on DLLs</span></span>|  
|<span data-ttu-id="e9cec-406">RegsvcsMQSAdapter</span><span class="sxs-lookup"><span data-stu-id="e9cec-406">RegsvcsMQSAdapter</span></span>|<span data-ttu-id="e9cec-407">在 Dll 上執行 Regsvcs.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-407">Runs Regsvcs.exe on DLLs</span></span>|  
|<span data-ttu-id="e9cec-408">RegsvcsSQLAdapter</span><span class="sxs-lookup"><span data-stu-id="e9cec-408">RegsvcsSQLAdapter</span></span>|<span data-ttu-id="e9cec-409">在 Dll 上執行 Regsvcs.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-409">Runs Regsvcs.exe on DLLs</span></span>|  
|<span data-ttu-id="e9cec-410">WMI_Add_MSBTS_Silent</span><span class="sxs-lookup"><span data-stu-id="e9cec-410">WMI_Add_MSBTS_Silent</span></span>|<span data-ttu-id="e9cec-411">註冊 BizTalk 伺服器命名空間和 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="e9cec-411">Registers BizTalk Server namespace and classes to WMI.</span></span>|  
|<span data-ttu-id="e9cec-412">LaunchConfigFmk_SlashUP</span><span class="sxs-lookup"><span data-stu-id="e9cec-412">LaunchConfigFmk_SlashUP</span></span>|<span data-ttu-id="e9cec-413">取消設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e9cec-413">Un-configures BizTalk Server</span></span>|  
|<span data-ttu-id="e9cec-414">CleanupComplus</span><span class="sxs-lookup"><span data-stu-id="e9cec-414">CleanupComplus</span></span>|<span data-ttu-id="e9cec-415">Complus 應用程式和元件，會解除安裝。</span><span class="sxs-lookup"><span data-stu-id="e9cec-415">Uninstalls Complus Applications and components.</span></span>|  
|<span data-ttu-id="e9cec-416">RemoveSKU</span><span class="sxs-lookup"><span data-stu-id="e9cec-416">RemoveSKU</span></span>|<span data-ttu-id="e9cec-417">移除 BizTalk Server 使用期限時發生資料。</span><span class="sxs-lookup"><span data-stu-id="e9cec-417">Removes BizTalk Server TimeBomb data.</span></span>|  
|<span data-ttu-id="e9cec-418">BAM_Remove_Perf</span><span class="sxs-lookup"><span data-stu-id="e9cec-418">BAM_Remove_Perf</span></span>|<span data-ttu-id="e9cec-419">Bam 會解除安裝效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e9cec-419">Uninstalls performance counters for BAM.</span></span>|  
|<span data-ttu-id="e9cec-420">LoadBTSCounters</span><span class="sxs-lookup"><span data-stu-id="e9cec-420">LoadBTSCounters</span></span>|<span data-ttu-id="e9cec-421">載入 BizTalk Server 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e9cec-421">Loads BizTalk Server performance counters.</span></span>|  
|<span data-ttu-id="e9cec-422">RegisterBtprojExtn</span><span class="sxs-lookup"><span data-stu-id="e9cec-422">RegisterBtprojExtn</span></span>|<span data-ttu-id="e9cec-423">註冊 BizTalk 專案檔 (.btproj) 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e9cec-423">Registers BizTalk project file (.btproj) extension.</span></span>|  
|<span data-ttu-id="e9cec-424">UnRegisterBtprojExtn</span><span class="sxs-lookup"><span data-stu-id="e9cec-424">UnRegisterBtprojExtn</span></span>|<span data-ttu-id="e9cec-425">取消註冊 BizTalk 專案檔 (.btproj) 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="e9cec-425">Un-registers BizTalk project file (.btproj) extension.</span></span>|  
|<span data-ttu-id="e9cec-426">UnRegsvcsApplicationDeployment</span><span class="sxs-lookup"><span data-stu-id="e9cec-426">UnRegsvcsApplicationDeployment</span></span>|<span data-ttu-id="e9cec-427">當您解除安裝 BizTalk Server 時，執行 Regsvcs.exe 特定 dll</span><span class="sxs-lookup"><span data-stu-id="e9cec-427">Runs Regsvcs.exe on certain DLLs when you uninstall BizTalk Server</span></span>|  
|<span data-ttu-id="e9cec-428">UnRegsvcsDeployment</span><span class="sxs-lookup"><span data-stu-id="e9cec-428">UnRegsvcsDeployment</span></span>|<span data-ttu-id="e9cec-429">當您解除安裝 BizTalk Server 時，執行 Regsvcs.exe 特定 dll</span><span class="sxs-lookup"><span data-stu-id="e9cec-429">Runs Regsvcs.exe on certain DLLs when you uninstall BizTalk Server</span></span>|  
|<span data-ttu-id="e9cec-430">UnRegsvcsMQSAdapter</span><span class="sxs-lookup"><span data-stu-id="e9cec-430">UnRegsvcsMQSAdapter</span></span>|<span data-ttu-id="e9cec-431">當您解除安裝 BizTalk Server 時，執行 Regsvcs.exe 特定 dll</span><span class="sxs-lookup"><span data-stu-id="e9cec-431">Runs Regsvcs.exe on certain DLLs when you uninstall BizTalk Server</span></span>|  
|<span data-ttu-id="e9cec-432">UnRegsvcsSQLAdapter</span><span class="sxs-lookup"><span data-stu-id="e9cec-432">UnRegsvcsSQLAdapter</span></span>|<span data-ttu-id="e9cec-433">當您解除安裝 BizTalk Server 時，執行 Regsvcs.exe 特定 dll</span><span class="sxs-lookup"><span data-stu-id="e9cec-433">Runs Regsvcs.exe on certain DLLs when you uninstall BizTalk Server</span></span>|  
|<span data-ttu-id="e9cec-434">UnloadBTSCounters</span><span class="sxs-lookup"><span data-stu-id="e9cec-434">UnloadBTSCounters</span></span>|<span data-ttu-id="e9cec-435">卸載 BizTalk Server 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="e9cec-435">Unloads BizTalk Server performance counters.</span></span>|  
|<span data-ttu-id="e9cec-436">WMI_Remove_MSBTS</span><span class="sxs-lookup"><span data-stu-id="e9cec-436">WMI_Remove_MSBTS</span></span>|<span data-ttu-id="e9cec-437">從 WMI 移除 BizTalk Server 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e9cec-437">Removes BizTalk Server namespace from WMI.</span></span>|  
|<span data-ttu-id="e9cec-438">RegisterComsvcs</span><span class="sxs-lookup"><span data-stu-id="e9cec-438">RegisterComsvcs</span></span>|<span data-ttu-id="e9cec-439">以無訊息模式執行 regsvr32.exe comsvcs.dll 上。</span><span class="sxs-lookup"><span data-stu-id="e9cec-439">Runs regsvr32.exe on comsvcs.dll silently.</span></span>|  
|<span data-ttu-id="e9cec-440">DevenvSetupUninstall</span><span class="sxs-lookup"><span data-stu-id="e9cec-440">DevenvSetupUninstall</span></span>|<span data-ttu-id="e9cec-441">執行 DevEnv.exe/安裝//resetskippkgs。</span><span class="sxs-lookup"><span data-stu-id="e9cec-441">Runs DevEnv.exe /Setup/resetskippkgs.</span></span>|  
|<span data-ttu-id="e9cec-442">RollbackComplus</span><span class="sxs-lookup"><span data-stu-id="e9cec-442">RollbackComplus</span></span>|<span data-ttu-id="e9cec-443">回復 Complus 應用程式和元件的安裝。</span><span class="sxs-lookup"><span data-stu-id="e9cec-443">Rollbacks the installation of Complus applications and components.</span></span>|  
|<span data-ttu-id="e9cec-444">ResRegsvcsMQSAdapter</span><span class="sxs-lookup"><span data-stu-id="e9cec-444">ResRegsvcsMQSAdapter</span></span>|<span data-ttu-id="e9cec-445">在指定的二進位檔上執行 regsvcs.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-445">Runs regsvcs.exe on a given binary</span></span>|  
|<span data-ttu-id="e9cec-446">ResRegsvcsSQLAdapter</span><span class="sxs-lookup"><span data-stu-id="e9cec-446">ResRegsvcsSQLAdapter</span></span>|<span data-ttu-id="e9cec-447">在指定的二進位檔上執行 regsvcs.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-447">Runs regsvcs.exe on a given binary</span></span>|  
|<span data-ttu-id="e9cec-448">RestoreRegsvcsApplicationDeployment</span><span class="sxs-lookup"><span data-stu-id="e9cec-448">RestoreRegsvcsApplicationDeployment</span></span>|<span data-ttu-id="e9cec-449">將附加 framework Microsoft.BizTalk.ApplicationDeployment.Engine.dll 的路徑。</span><span class="sxs-lookup"><span data-stu-id="e9cec-449">Appends the path of framework with Microsoft.BizTalk.ApplicationDeployment.Engine.dll.</span></span>|  
|<span data-ttu-id="e9cec-450">RestoreRegsvcsDeployment</span><span class="sxs-lookup"><span data-stu-id="e9cec-450">RestoreRegsvcsDeployment</span></span>|<span data-ttu-id="e9cec-451">將附加 framework Microsoft.BizTalk.ApplicationDeployment.Engine.dll 的路徑。</span><span class="sxs-lookup"><span data-stu-id="e9cec-451">Appends the path of framework with Microsoft.BizTalk.ApplicationDeployment.Engine.dll.</span></span>|  
|<span data-ttu-id="e9cec-452">BrandSKURollback</span><span class="sxs-lookup"><span data-stu-id="e9cec-452">BrandSKURollback</span></span>|<span data-ttu-id="e9cec-453">如果發生安裝失敗，復原會註冊 SKU 資訊。</span><span class="sxs-lookup"><span data-stu-id="e9cec-453">Rollbacks registered SKU information if installation failure occurs.</span></span>|  
|<span data-ttu-id="e9cec-454">CA_RestartServices_rollback</span><span class="sxs-lookup"><span data-stu-id="e9cec-454">CA_RestartServices_rollback</span></span>|<span data-ttu-id="e9cec-455">重新啟動已停止的服務。</span><span class="sxs-lookup"><span data-stu-id="e9cec-455">Restarts the stopped services.</span></span>|  
|<span data-ttu-id="e9cec-456">RemoveSKURollback</span><span class="sxs-lookup"><span data-stu-id="e9cec-456">RemoveSKURollback</span></span>|<span data-ttu-id="e9cec-457">更新登錄中的 SKU 值。</span><span class="sxs-lookup"><span data-stu-id="e9cec-457">Updates the SKU values from the registry.</span></span>|  
|<span data-ttu-id="e9cec-458">BAM_Res_Perf_Silent</span><span class="sxs-lookup"><span data-stu-id="e9cec-458">BAM_Res_Perf_Silent</span></span>|<span data-ttu-id="e9cec-459">在無訊息安裝期間，以做為 BAM 效能計數器的 Dll 註冊 Microsoft.BizTalk.Bam.EventObservation.dll。</span><span class="sxs-lookup"><span data-stu-id="e9cec-459">Registers Microsoft.BizTalk.Bam.EventObservation.dll as the BAM performance counter DLLs during silent installation.</span></span>|  
|<span data-ttu-id="e9cec-460">BAM_Rollback_Perf</span><span class="sxs-lookup"><span data-stu-id="e9cec-460">BAM_Rollback_Perf</span></span>|<span data-ttu-id="e9cec-461">取消 Microsoft.BizTalk.Bam.EventObservation.dll 登錄做 BAM 效能計數器 DLL</span><span class="sxs-lookup"><span data-stu-id="e9cec-461">Unregisters  Microsoft.BizTalk.Bam.EventObservation.dll as the BAM performance counter DLL</span></span>|  
|<span data-ttu-id="e9cec-462">RBKRegsvcsMQSAdapter</span><span class="sxs-lookup"><span data-stu-id="e9cec-462">RBKRegsvcsMQSAdapter</span></span>|<span data-ttu-id="e9cec-463">執行給定二進位 regsvcs.exe。</span><span class="sxs-lookup"><span data-stu-id="e9cec-463">Runs regsvcs.exe on a given binary.</span></span>|  
|<span data-ttu-id="e9cec-464">RBKRegsvcsSQLAdapter</span><span class="sxs-lookup"><span data-stu-id="e9cec-464">RBKRegsvcsSQLAdapter</span></span>|<span data-ttu-id="e9cec-465">執行給定二進位 regsvcs.exe。</span><span class="sxs-lookup"><span data-stu-id="e9cec-465">Runs regsvcs.exe on a given binary.</span></span>|  
|<span data-ttu-id="e9cec-466">RestoreBTSCounters</span><span class="sxs-lookup"><span data-stu-id="e9cec-466">RestoreBTSCounters</span></span>|<span data-ttu-id="e9cec-467">還原效能計數器.ini 檔案名稱與屬性。</span><span class="sxs-lookup"><span data-stu-id="e9cec-467">Restores the property with the performance counter .ini file name.</span></span>|  
|<span data-ttu-id="e9cec-468">RollbackBTSCounters</span><span class="sxs-lookup"><span data-stu-id="e9cec-468">RollbackBTSCounters</span></span>|<span data-ttu-id="e9cec-469">執行命令 unlodctr BTSSvc.3.0。</span><span class="sxs-lookup"><span data-stu-id="e9cec-469">Runs command unlodctr BTSSvc.3.0.</span></span>|  
|<span data-ttu-id="e9cec-470">RollbackRegsvcsApplicationDeployment</span><span class="sxs-lookup"><span data-stu-id="e9cec-470">RollbackRegsvcsApplicationDeployment</span></span>|<span data-ttu-id="e9cec-471">設定 [FrameworkPath] &#124;[INSTALLDIR]Microsoft.BizTalk.ApplicationDeployment.Engine.dll 失敗的安裝案例。</span><span class="sxs-lookup"><span data-stu-id="e9cec-471">Sets up [FrameworkPath]&#124;[INSTALLDIR]Microsoft.BizTalk.ApplicationDeployment.Engine.dll for the failed installation scenarios.</span></span>|  
|<span data-ttu-id="e9cec-472">RollbackRegsvcsDeployment</span><span class="sxs-lookup"><span data-stu-id="e9cec-472">RollbackRegsvcsDeployment</span></span>|<span data-ttu-id="e9cec-473">在解除安裝/rollback 案例來叫用 regsvcs.exe。</span><span class="sxs-lookup"><span data-stu-id="e9cec-473">Invokes regsvcs.exe during uninstall/rollback scenarios.</span></span>|  
|<span data-ttu-id="e9cec-474">WMI_Restore_MSBTS_Silent</span><span class="sxs-lookup"><span data-stu-id="e9cec-474">WMI_Restore_MSBTS_Silent</span></span>|<span data-ttu-id="e9cec-475">呼叫 mofcomp 註冊 WMI 結構描述</span><span class="sxs-lookup"><span data-stu-id="e9cec-475">Calls mofcomp to register WMI schemas</span></span>|  
|<span data-ttu-id="e9cec-476">WMI_Rollback_MSBTS</span><span class="sxs-lookup"><span data-stu-id="e9cec-476">WMI_Rollback_MSBTS</span></span>|<span data-ttu-id="e9cec-477">從 WMI 移除 BizTalk Server 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e9cec-477">Removes BizTalk Server namespace from WMI.</span></span>|  
|<span data-ttu-id="e9cec-478">CA_RestartServices_commit</span><span class="sxs-lookup"><span data-stu-id="e9cec-478">CA_RestartServices_commit</span></span>|<span data-ttu-id="e9cec-479">重新啟動已停止的服務</span><span class="sxs-lookup"><span data-stu-id="e9cec-479">Restarts the stopped services</span></span>|  
|<span data-ttu-id="e9cec-480">DevenvSetup</span><span class="sxs-lookup"><span data-stu-id="e9cec-480">DevenvSetup</span></span>|<span data-ttu-id="e9cec-481">執行 DevEnv.exe /Setup /resetskippkgs 期間 BizTalk Server 安裝/解除安裝程序。</span><span class="sxs-lookup"><span data-stu-id="e9cec-481">Runs DevEnv.exe /Setup /resetskippkgs both during BizTalk Server install/uninstall process.</span></span>|  
|<span data-ttu-id="e9cec-482">ExecXmlConfig</span><span class="sxs-lookup"><span data-stu-id="e9cec-482">ExecXmlConfig</span></span>|<span data-ttu-id="e9cec-483">用來進行組態變更 machine.config RFID 相關資料。</span><span class="sxs-lookup"><span data-stu-id="e9cec-483">Used to make configuration changes to machine.config for RFID related data.</span></span>|  
|<span data-ttu-id="e9cec-484">ExecXmlConfigRollback</span><span class="sxs-lookup"><span data-stu-id="e9cec-484">ExecXmlConfigRollback</span></span>|<span data-ttu-id="e9cec-485">用來進行組態變更 machine.config RFID 相關資料。</span><span class="sxs-lookup"><span data-stu-id="e9cec-485">Used to make configuration changes to machine.config for RFID related data.</span></span>|  
  
#### <a name="running-biztalk-components"></a><span data-ttu-id="e9cec-486">執行 BizTalk 元件</span><span class="sxs-lookup"><span data-stu-id="e9cec-486">Running BizTalk Components</span></span>  
 <span data-ttu-id="e9cec-487">下表列出必須使用系統管理權限或最高可用權限執行的 BizTalk 元件。</span><span class="sxs-lookup"><span data-stu-id="e9cec-487">The following table lists BizTalk components that must be run using administrative privileges or with highest available privilege.</span></span>  
  
|<span data-ttu-id="e9cec-488">資料夾路徑</span><span class="sxs-lookup"><span data-stu-id="e9cec-488">Folder path</span></span>|<span data-ttu-id="e9cec-489">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="e9cec-489">File name</span></span>|<span data-ttu-id="e9cec-490">使用者權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-490">User privileges</span></span>|  
|-----------------|---------------|---------------------|  
|<span data-ttu-id="e9cec-491">\Program 檔案 (x86) \common shared\Help 9\Microsoft Document Explorer 2008</span><span class="sxs-lookup"><span data-stu-id="e9cec-491">\Program Files (x86)\Common Files\Microsoft shared\Help 9\Microsoft Document Explorer 2008</span></span>|<span data-ttu-id="e9cec-492">Install.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-492">Install.exe</span></span>|<span data-ttu-id="e9cec-493">高可用權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-493">Highest available privilege</span></span>|  
|<span data-ttu-id="e9cec-494">\Program files (x86) \Microsoft BizTalk Server*您的版本*</span><span class="sxs-lookup"><span data-stu-id="e9cec-494">\Program Files (x86)\Microsoft BizTalk Server *your version*</span></span>|<span data-ttu-id="e9cec-495">BTSHatApp.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-495">BTSHatApp.exe</span></span>|<span data-ttu-id="e9cec-496">高可用權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-496">Highest available privilege</span></span>|  
|<span data-ttu-id="e9cec-497">\Program files (x86) \Microsoft BizTalk Server*您的版本*</span><span class="sxs-lookup"><span data-stu-id="e9cec-497">\Program Files (x86)\Microsoft BizTalk Server *your version*</span></span>|<span data-ttu-id="e9cec-498">BTSMMCLauncher.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-498">BTSMMCLauncher.exe</span></span>|<span data-ttu-id="e9cec-499">高可用權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-499">Highest available privilege</span></span>|  
|<span data-ttu-id="e9cec-500">\Program files (x86) \Microsoft BizTalk Server*您的版本*</span><span class="sxs-lookup"><span data-stu-id="e9cec-500">\Program Files (x86)\Microsoft BizTalk Server *your version*</span></span>|<span data-ttu-id="e9cec-501">BtsWcfServicePublishingWizard.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-501">BtsWcfServicePublishingWizard.exe</span></span>|<span data-ttu-id="e9cec-502">高可用權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-502">Highest available privilege</span></span>|  
|<span data-ttu-id="e9cec-503">\Program files (x86) \Microsoft BizTalk Server*您的版本*</span><span class="sxs-lookup"><span data-stu-id="e9cec-503">\Program Files (x86)\Microsoft BizTalk Server *your version*</span></span>|<span data-ttu-id="e9cec-504">BTSWebSvcWiz.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-504">BTSWebSvcWiz.exe</span></span>|<span data-ttu-id="e9cec-505">高可用權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-505">Highest available privilege</span></span>|  
|<span data-ttu-id="e9cec-506">\Program files (x86) \Microsoft BizTalk Server*您的版本*</span><span class="sxs-lookup"><span data-stu-id="e9cec-506">\Program Files (x86)\Microsoft BizTalk Server *your version*</span></span>|<span data-ttu-id="e9cec-507">Configuration.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-507">Configuration.exe</span></span>|<span data-ttu-id="e9cec-508">高可用權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-508">Highest available privilege</span></span>|  
|<span data-ttu-id="e9cec-509">\Program files (x86) \Microsoft BizTalk Server*您的版本*</span><span class="sxs-lookup"><span data-stu-id="e9cec-509">\Program Files (x86)\Microsoft BizTalk Server *your version*</span></span>|<span data-ttu-id="e9cec-510">REDeployWiz.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-510">REDeployWiz.exe</span></span>|<span data-ttu-id="e9cec-511">高可用權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-511">Highest available privilege</span></span>|  
|<span data-ttu-id="e9cec-512">\Program files (x86) \Microsoft BizTalk Server*您的版本*</span><span class="sxs-lookup"><span data-stu-id="e9cec-512">\Program Files (x86)\Microsoft BizTalk Server *your version*</span></span>|<span data-ttu-id="e9cec-513">Setup.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-513">Setup.exe</span></span>|<span data-ttu-id="e9cec-514">系統管理權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-514">Administrative privilege</span></span>|  
|<span data-ttu-id="e9cec-515">\Program files (x86) \Microsoft BizTalk Server*版本*\XSD Schema\EDI</span><span class="sxs-lookup"><span data-stu-id="e9cec-515">\Program Files (x86)\Microsoft BizTalk Server *your version*\XSD Schema\EDI</span></span>|<span data-ttu-id="e9cec-516">MicrosoftEdiXSDTemplates.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-516">MicrosoftEdiXSDTemplates.exe</span></span>|<span data-ttu-id="e9cec-517">自我解壓縮 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="e9cec-517">Self-extracting .exe file.</span></span>|  
|<span data-ttu-id="e9cec-518">\Program 檔案 (x86) \Microsoft UDDI Services\config</span><span class="sxs-lookup"><span data-stu-id="e9cec-518">\Program Files (x86)\Microsoft UDDI Services\config</span></span>|<span data-ttu-id="e9cec-519">組態 .exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-519">Configuration .exe</span></span>|<span data-ttu-id="e9cec-520">系統管理權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-520">Administrative privilege</span></span>|  
|<span data-ttu-id="e9cec-521">Files\ Microsoft BizTalk RFID\bin</span><span class="sxs-lookup"><span data-stu-id="e9cec-521">\Program Files\ Microsoft BizTalk RFID\bin</span></span>|<span data-ttu-id="e9cec-522">BTSMMCLauncher.exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-522">BTSMMCLauncher.exe</span></span>|<span data-ttu-id="e9cec-523">高可用權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-523">Highest available privilege</span></span>|  
|<span data-ttu-id="e9cec-524">\Program Files\Microsoft BizTalk rfid\breconfiguration</span><span class="sxs-lookup"><span data-stu-id="e9cec-524">\Program Files\Microsoft BizTalk RFID\BREConfi guration</span></span>|<span data-ttu-id="e9cec-525">組態 .exe</span><span class="sxs-lookup"><span data-stu-id="e9cec-525">Configuration .exe</span></span>|<span data-ttu-id="e9cec-526">系統管理權限</span><span class="sxs-lookup"><span data-stu-id="e9cec-526">Administrative privilege</span></span>|  
