---
title: "疑難排解設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 902e591a-4ff4-4053-b329-0c022f44999a
caps.latest.revision: "37"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e523c5c992ea422e6fe81f3c0d948db7007bcdb1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshooting-configuration"></a><span data-ttu-id="68461-102">組態疑難排解</span><span class="sxs-lookup"><span data-stu-id="68461-102">Troubleshooting Configuration</span></span>
<span data-ttu-id="68461-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態程式會在執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的一或多部電腦上建立資料庫、將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所使用的資料表、角色和預存程序填入資料庫中，然後將執行階段所使用的 .NET 組件部署到 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="68461-103">The Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration program creates databases on one or more computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], populates the databases with tables, roles, and stored procedures used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and deploys .NET assemblies used during runtime to the BizTalk Management database.</span></span>  
  
 <span data-ttu-id="68461-104">本章節將討論解決組態錯誤的疑難排解技術。</span><span class="sxs-lookup"><span data-stu-id="68461-104">This section discusses troubleshooting techniques to resolve configuration errors.</span></span> <span data-ttu-id="68461-105">此外，也將列出一些常見的組態問題以及解決這些問題的方式。</span><span class="sxs-lookup"><span data-stu-id="68461-105">It also lists some common configuration problems and how to resolve these problems.</span></span>  
  
## <a name="configuration-logging"></a><span data-ttu-id="68461-106">組態記錄</span><span class="sxs-lookup"><span data-stu-id="68461-106">Configuration Logging</span></span>  
 <span data-ttu-id="68461-107">組態程式會將詳細資訊寫入組態記錄檔中，此記錄檔預設是位於執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之電腦的暫存目錄中。</span><span class="sxs-lookup"><span data-stu-id="68461-107">The configuration program writes detailed information to a configuration log file which by default is located in the temp directory of the computer running[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="68461-108">若要判斷 TEMP 環境變數所指定的資料夾，請在這部電腦上開啟命令提示，並輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="68461-108">To determine the folder that is specified by the TEMP environment variable open a command prompt on this computer, type the following command, and then press ENTER:</span></span>  
  
 <span data-ttu-id="68461-109">**echo %TEMP%**</span><span class="sxs-lookup"><span data-stu-id="68461-109">**echo %TEMP%**</span></span>  
  
 <span data-ttu-id="68461-110">此組態記錄檔含有已執行之組態步驟的摘要，以及組態程序中可能發生之任何失敗的相關診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="68461-110">The configuration log file contains a summary of the configuration steps performed, as well as diagnostic information about any failures that may occur during the configuration process.</span></span> <span data-ttu-id="68461-111">如果發生組態錯誤，請在文字編輯器 (如 [記事本]) 中開啟此組態記錄檔，然後檢查此記錄檔，找出錯誤的可能原因。</span><span class="sxs-lookup"><span data-stu-id="68461-111">If a configuration error occurs, open the configuration log in a text editor such as Notepad and check the log file for possible causes of the error.</span></span>  
  
## <a name="troubleshooting-tools"></a><span data-ttu-id="68461-112">疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="68461-112">Troubleshooting Tools</span></span>  
 <span data-ttu-id="68461-113">使用 SQL Server Profiler、Filemon 或 Regmon 可蒐集有關組態失敗的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="68461-113">Use SQL Server Profiler, Filemon, or Regmon to gather additional information about configuration failures.</span></span> <span data-ttu-id="68461-114">如需有關這些工具的詳細資訊，請參閱[工具和公用程式，以供疑難排解使用](../core/tools-and-utilities-to-use-for-troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="68461-114">For more information about these tools, see [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md).</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="68461-115">已知問題</span><span class="sxs-lookup"><span data-stu-id="68461-115">Known Issues</span></span>  
  
#### <a name="configuration-fails-when-biztalk-server-and-sql-server-are-installed-on-separate-computers"></a><span data-ttu-id="68461-116">當 BizTalk Server 和 SQL Server 安裝在不同電腦上時，會發生組態失敗</span><span class="sxs-lookup"><span data-stu-id="68461-116">Configuration fails when BizTalk Server and SQL Server are installed on separate computers</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-117">問題</span><span class="sxs-lookup"><span data-stu-id="68461-117">Problem</span></span>  
 <span data-ttu-id="68461-118">當您嘗試設定企業單一登入 (SSO) 元件時，組態會發生失敗，其錯誤與底下類似：</span><span class="sxs-lookup"><span data-stu-id="68461-118">Configuration fails with errors similar to the following when attempting to configure the Enterprise Single Sign-On (SSO) component:</span></span>  
  
 <span data-ttu-id="68461-119">嘗試存取 SSO 資料庫時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="68461-119">An error occurred while attempting to access the SSO database.</span></span>  
  
 <span data-ttu-id="68461-120">函式： FieldInfoCreate</span><span class="sxs-lookup"><span data-stu-id="68461-120">Function: FieldInfoCreate</span></span>  
  
 <span data-ttu-id="68461-121">-或-</span><span class="sxs-lookup"><span data-stu-id="68461-121">-or-</span></span>  
  
 <span data-ttu-id="68461-122">無法啟用單一登入 (SSO) 服務 （錯誤碼 0X800706BA）</span><span class="sxs-lookup"><span data-stu-id="68461-122">Failed to enable the Single Sign-On (SSO) Service (error code 0X800706BA)</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-123">原因</span><span class="sxs-lookup"><span data-stu-id="68461-123">Cause</span></span>  
 <span data-ttu-id="68461-124">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同電腦上，則會在「分散式交易協調器」(MSDTC) 交易的內容底下執行組態作業，而且這兩部電腦之間必須可透過網路使用 MSDTC 功能。</span><span class="sxs-lookup"><span data-stu-id="68461-124">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on different computers then the configuration operations are performed under the context of a Distributed Transaction Coordinator (MSDTC) transaction and MSDTC functionality must be available over the network between these computers.</span></span> <span data-ttu-id="68461-125">如果無法在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的電腦之間透過網路使用 MSDTC 功能，則可能會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="68461-125">If MSDTC functionality is not available over the network between the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] then this error can occur.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-126">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-126">Resolution</span></span>  
 <span data-ttu-id="68461-127">請依照[疑難排解 MSDTC 問題的](../core/troubleshooting-problems-with-msdtc.md)以確保能透過網路執行的電腦之間的 MSDTC 功能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="68461-127">Follow the steps in [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md) to ensure MSDTC functionality over the network between the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
#### <a name="antivirus-software-interferes-with-configuration-and-causes-configuration-failures"></a><span data-ttu-id="68461-128">防毒軟體干擾組態，並造成組態失敗</span><span class="sxs-lookup"><span data-stu-id="68461-128">Antivirus software interferes with configuration and causes configuration failures</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-129">問題</span><span class="sxs-lookup"><span data-stu-id="68461-129">Problem</span></span>  
 <span data-ttu-id="68461-130">當防毒軟體錯誤判斷出組態程式為病毒時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態會發生失敗。</span><span class="sxs-lookup"><span data-stu-id="68461-130">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration fails when antivirus software incorrectly determines that the configuration program is a virus.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-131">原因</span><span class="sxs-lookup"><span data-stu-id="68461-131">Cause</span></span>  
 <span data-ttu-id="68461-132">防毒軟體沒有更新成包含[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態程式當做合法 （非病毒） 程式。</span><span class="sxs-lookup"><span data-stu-id="68461-132">The antivirus software has not been updated to include the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration program as a legitimate (non-virus) program.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-133">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-133">Resolution</span></span>  
 <span data-ttu-id="68461-134">設定此防毒程式，使其將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態程式辨識為合法 (非病毒) 程式，或是在組態程式執行時，暫時停用此防毒軟體。</span><span class="sxs-lookup"><span data-stu-id="68461-134">Configure the antivirus program to recognize the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration program as a legitimate (non-virus) program or else temporarily disable the antivirus software while the configuration program is running.</span></span>  
  
#### <a name="configuration-fails-with-a-file-or-assembly-name-filenamedll-or-one-of-its-dependencies-was-not-found-error"></a><span data-ttu-id="68461-135">組態失敗，其錯誤為「找不到檔案或組件名稱 FileName.dll 或其相依性的其中之一」。</span><span class="sxs-lookup"><span data-stu-id="68461-135">Configuration fails with a "File or assembly name FileName.dll, or one of its dependencies, was not found" error</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-136">問題</span><span class="sxs-lookup"><span data-stu-id="68461-136">Problem</span></span>  
 <span data-ttu-id="68461-137">在組態程序期間，出現了類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="68461-137">An error similar to the following is displayed during the configuration process:</span></span>  
  
 <span data-ttu-id="68461-138">無法部署 BizTalk 系統組件 "C:\Program Files\Microsoft\\</span><span class="sxs-lookup"><span data-stu-id="68461-138">Failed to deploy BizTalk system assembly "C:\Program Files\Microsoft\\</span></span>  
  
 <span data-ttu-id="68461-139">BizTalk Server 2009\Microsoft.BizTalk.DefaultPipelines.dll。</span><span class="sxs-lookup"><span data-stu-id="68461-139">BizTalk Server 2009\Microsoft.BizTalk.DefaultPipelines.dll.</span></span> <span data-ttu-id="68461-140">[未指定]</span><span class="sxs-lookup"><span data-stu-id="68461-140">Unspecified</span></span>  
  
 <span data-ttu-id="68461-141">例外狀況： 檔案或組件名稱 FileName.dll，或其中一個它</span><span class="sxs-lookup"><span data-stu-id="68461-141">exception: File or assembly name FileName .dll, or one of its</span></span>  
  
 <span data-ttu-id="68461-142">相依性，找不到。</span><span class="sxs-lookup"><span data-stu-id="68461-142">dependencies, was not found.</span></span> <span data-ttu-id="68461-143">檔案或組件名稱 FileName.dll，或</span><span class="sxs-lookup"><span data-stu-id="68461-143">File or assembly name FileName .dll, or</span></span>  
  
 <span data-ttu-id="68461-144">其中一個相依性，找不到。 」</span><span class="sxs-lookup"><span data-stu-id="68461-144">one of its dependencies, was not found."</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-145">原因</span><span class="sxs-lookup"><span data-stu-id="68461-145">Cause</span></span>  
 <span data-ttu-id="68461-146">如果 Network Service 帳戶在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦上沒有暫存資料夾的寫入權限，可能會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="68461-146">This error can occur if the Network Service account does not have write permissions to the temp folder on the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="68461-147">在組態進行期間，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態會使用 Windows Management Instrumentation (WMI)，將 .NET 組件部署到 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="68461-147">During configuration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration uses Windows Management Instrumentation (WMI) to deploy .NET assemblies to the BizTalk Management database.</span></span> <span data-ttu-id="68461-148">WMI 在將這些組件部署到 BizTalk 管理資料庫時，會模擬 Network Service 帳戶，因此，Network Service 帳戶在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的電腦上必須有暫存資料夾的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="68461-148">WMI impersonates the Network Service account while deploying these assemblies to the BizTalk Management database and so the Network Service account must have write access to the temp folder on the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-149">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-149">Resolution</span></span>  
 <span data-ttu-id="68461-150">將執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之電腦上的暫存資料夾寫入權限授與給 Network Service 帳戶，然後再次執行組態程式。</span><span class="sxs-lookup"><span data-stu-id="68461-150">Grant the Network Service account write access to the temp folder on the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and run the configuration program again.</span></span> <span data-ttu-id="68461-151">若要判斷 TEMP 環境變數所指定的資料夾，請在這部電腦上開啟命令提示，並輸入下列命令，然後按 ENTER：</span><span class="sxs-lookup"><span data-stu-id="68461-151">To determine the folder that is specified by the TEMP environment variable, open a command prompt on the computer, type the following command, and then press ENTER:</span></span>  
  
```  
echo %TEMP%  
```  
  
#### <a name="configuration-of-the-group-fails-if-the-netbios-name-of-the-computer-running-sql-server-exceeds-15-characters"></a><span data-ttu-id="68461-152">如果執行 SQL Server 之電腦的 NetBIOS 名稱超過 15 個字元，群組的組態會失敗</span><span class="sxs-lookup"><span data-stu-id="68461-152">Configuration of the group fails if the NetBIOS name of the computer running SQL Server exceeds 15 characters</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-153">問題</span><span class="sxs-lookup"><span data-stu-id="68461-153">Problem</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="68461-154"> 群組組態失敗，而且在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態記錄檔中出現與下列類似的錯誤：</span><span class="sxs-lookup"><span data-stu-id="68461-154"> group configuration fails and an error similar to the following is displayed in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration log:</span></span>  
  
 <span data-ttu-id="68461-155">2006-08-29 23:54:00:0902 [警告] AdminLib GetBTSMessage: hrErr = 80070547;</span><span class="sxs-lookup"><span data-stu-id="68461-155">2006-08-29 23:54:00:0902 [WARN] AdminLib GetBTSMessage: hrErr=80070547;</span></span>  
  
 <span data-ttu-id="68461-156">Msg = 無法從網域讀取資訊的組態</span><span class="sxs-lookup"><span data-stu-id="68461-156">Msg=Configuration information could not be read from the domain</span></span>  
  
 <span data-ttu-id="68461-157">控制站，可能是因為該機器已無法使用，或存取有</span><span class="sxs-lookup"><span data-stu-id="68461-157">controller, either because the machine is unavailable, or access has</span></span>  
  
 <span data-ttu-id="68461-158">已拒絕。;</span><span class="sxs-lookup"><span data-stu-id="68461-158">been denied.;</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-159">原因</span><span class="sxs-lookup"><span data-stu-id="68461-159">Cause</span></span>  
 <span data-ttu-id="68461-160">如果執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 之電腦的 NetBIOS 名稱長度超過 15 個字元，會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="68461-160">This problem occurs if the length of the NetBIOS name for the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] exceeds 15 characters.</span></span> <span data-ttu-id="68461-161">如果 NetBIOS 名稱超過 15 個字元，Windows 就會將此 NetBIOS 名稱截斷為 15 個字元，而此 NetBIOS 名稱就不再符合這部電腦的完整格式網域名稱 (FQDN) 或 DNS 名稱的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="68461-161">If the NetBIOS name exceeds 15 characters then Windows truncates the NetBIOS name to 15 characters and the NetBIOS name will no longer match the first part of the fully qualified domain name (FQDN) or DNS name of this computer.</span></span> <span data-ttu-id="68461-162">如果此 NetBIOS 名稱不符合電腦 FQDN 的第一個部分，群組組態將會失敗。</span><span class="sxs-lookup"><span data-stu-id="68461-162">If the NetBIOS name does not match the first part of the FQDN of the computer, group configuration will fail.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-163">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-163">Resolution</span></span>  
 <span data-ttu-id="68461-164">變更執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 之電腦的 NetBIOS 名稱，使其不超過 15 個字元，然後再次執行組態。</span><span class="sxs-lookup"><span data-stu-id="68461-164">Change the NetBIOS name of the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to a name with no more than 15 characters and run configuration again.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68461-165">如果您為電腦重新命名，則必須重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="68461-165">You must restart the computer if you rename it.</span></span>  
  
#### <a name="configuration-fails-if-a-sql-server-database-file-that-has-the-same-name-as-the-specified-database-already-exists-in-the-sql-server-data-folder"></a><span data-ttu-id="68461-166">如果 SQL Server 資料庫檔案與 SQL Server 資料夾中已經存在的指定資料庫同名，組態會發生失敗</span><span class="sxs-lookup"><span data-stu-id="68461-166">Configuration fails if a SQL Server database file that has the same name as the specified database already exists in the SQL Server data folder</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-167">問題</span><span class="sxs-lookup"><span data-stu-id="68461-167">Problem</span></span>  
 <span data-ttu-id="68461-168">組態發生失敗，其錯誤與以下類似：</span><span class="sxs-lookup"><span data-stu-id="68461-168">Configuration fails with an error similar to the following:</span></span>  
  
 <span data-ttu-id="68461-169">無法安裝 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="68461-169">Failed to set up BAM database(s)</span></span>  
  
 <span data-ttu-id="68461-170">無法開啟登入 'BAMPrimaryImport' 中要求的資料庫</span><span class="sxs-lookup"><span data-stu-id="68461-170">Cannot open database requested in login 'BAMPrimaryImport'</span></span>  
  
 <span data-ttu-id="68461-171">登入失敗。</span><span class="sxs-lookup"><span data-stu-id="68461-171">Logon fails.</span></span> <span data-ttu-id="68461-172">使用者登入失敗 '*BizTalk\BizTalkUser*'</span><span class="sxs-lookup"><span data-stu-id="68461-172">Logon failed for user '*BizTalk\BizTalkUser*'</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-173">原因</span><span class="sxs-lookup"><span data-stu-id="68461-173">Cause</span></span>  
 <span data-ttu-id="68461-174">如果執行 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 之電腦的 \MSSQL\data 資料夾中已經有 .mdf 檔案或 .ldf 檔案與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態程式嘗試建立的 .mdf 檔案或 .ldf 檔案同名，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="68461-174">This error can occur if an .mdf file or an .ldf file already exists in the \MSSQL\data folder of the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that has the same name as the .mdf file or the .ldf file that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration program is trying to create.</span></span> <span data-ttu-id="68461-175">針對資料庫建立的 .mdf 檔案和 .ldf 檔案名稱是衍生自 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態程式中所指定的資料庫名稱，但是附加了 .mdf 和 .ldf 副檔名。</span><span class="sxs-lookup"><span data-stu-id="68461-175">The names of the .mdf file and the .ldf file that are created for the databases are derived from the name of the database that is specified in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration program with an .mdf and an .ldf extension appended.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-176">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-176">Resolution</span></span>  
 <span data-ttu-id="68461-177">若要解決這個行為，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="68461-177">To resolve this behavior, use one of the following methods:</span></span>  
  
-   <span data-ttu-id="68461-178">刪除與您要建立之任何資料庫名稱同名的任何 .mdf 檔案或 .ldf 檔案。</span><span class="sxs-lookup"><span data-stu-id="68461-178">Delete any .mdf files or .ldf files that have names that match the names of any databases that you are creating.</span></span>  
  
-   <span data-ttu-id="68461-179">選擇使用與 SQL Server 之 \Program Files\Microsoft SQL Server\MSSQL\data 資料夾中已經存在的任何 .mdf 檔案或 .ldf 檔案不同名的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="68461-179">Choose database names that do not match the names of any .mdf files or .ldf files that already exist in the \Program Files\Microsoft SQL Server\MSSQL\data folder of your SQL server.</span></span>  
  
#### <a name="configuration-fails-on-a-domain-controller-when-specifying-local-accounts"></a><span data-ttu-id="68461-180">指定本機帳戶時，網域控制站上的組態發生失敗</span><span class="sxs-lookup"><span data-stu-id="68461-180">Configuration fails on a domain controller when specifying local accounts</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-181">問題</span><span class="sxs-lookup"><span data-stu-id="68461-181">Problem</span></span>  
 <span data-ttu-id="68461-182">當執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態程式的網域控制站，如果您指定的 biztalkserverapplication 主控件或 BizTalkIsolatedHost 主機的本機群組 （例如，BizTalk 主控件使用者群組） 的組態會失敗。</span><span class="sxs-lookup"><span data-stu-id="68461-182">When running the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration program on a domain controller, configuration fails if you specified a local group (for example, BizTalk Host Users Group) for either the BizTalkServerApplication host or the BizTalkIsolatedHost host.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-183">原因</span><span class="sxs-lookup"><span data-stu-id="68461-183">Cause</span></span>  
 <span data-ttu-id="68461-184">網域控制站會自動將本機 Windows 群組視為網域 Windows 群組 (也就是說，網域控制站上不會有本機 Windows 群組)。</span><span class="sxs-lookup"><span data-stu-id="68461-184">A domain controller automatically treats a local Windows group as a domain Windows group (there is no such thing as local Windows group on a domain controller).</span></span> <span data-ttu-id="68461-185">如果您在執行組態程式時，為主控件指定了本機 Windows 群組，則當您嘗試為此群組建立 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 登入時，組態會發生失敗。</span><span class="sxs-lookup"><span data-stu-id="68461-185">If you specified a local Windows group for the host while running the configuration program, configuration will fail when trying to create a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] logon for the group.</span></span> <span data-ttu-id="68461-186">當伺服器是網域控制站時，組態程式不會停用本機 Windows 群組選項。</span><span class="sxs-lookup"><span data-stu-id="68461-186">The configuration program does not disable the local Windows group option when the server is a domain controller.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-187">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-187">Resolution</span></span>  
 <span data-ttu-id="68461-188">針對組態進行期間建立的主控件指定網域群組。</span><span class="sxs-lookup"><span data-stu-id="68461-188">Specify domain groups for the hosts that are created during configuration.</span></span>  
  
#### <a name="configuration-fails-to-create-sql-server-analysis-database-if-the-sql-server-has-been-renamed"></a><span data-ttu-id="68461-189">如果 SQL Server 已經重新命名，則組態程式將無法建立 SQL Server 分析資料庫</span><span class="sxs-lookup"><span data-stu-id="68461-189">Configuration fails to create SQL Server Analysis database if the SQL server has been renamed</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-190">問題</span><span class="sxs-lookup"><span data-stu-id="68461-190">Problem</span></span>  
 <span data-ttu-id="68461-191">若您將安裝 SQL Server Analysis Server 的電腦重新命名，組態程式就無法建立新的 SQL Server 分析資料庫，而且會產生類似以下的錯誤：</span><span class="sxs-lookup"><span data-stu-id="68461-191">If you have renamed the computer on which you installed SQL Server Analysis Server, the configuration program fails when it tries to create the new SQL Server Analysis database and an error similar to the following is generated:</span></span>  
  
 <span data-ttu-id="68461-192">無法連線到儲存機制。</span><span class="sxs-lookup"><span data-stu-id="68461-192">Cannot connect to the repository.</span></span>  
  
 <span data-ttu-id="68461-193">Analysis server:\<機器名稱\></span><span class="sxs-lookup"><span data-stu-id="68461-193">Analysis server: \<machine name\></span></span>  
  
 <span data-ttu-id="68461-194">Error:</span><span class="sxs-lookup"><span data-stu-id="68461-194">Error:</span></span>  
  
 <span data-ttu-id="68461-195">'\\\\< 機器名稱\>\MsOLAPRepository$\msmdrep.mdb' 不是有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="68461-195">'\\\\<machine name\>\MsOLAPRepository$\msmdrep.mdb' is not a valid path.</span></span>  
  
 <span data-ttu-id="68461-196">請確定您正確拼寫的路徑名稱，而且是</span><span class="sxs-lookup"><span data-stu-id="68461-196">Make sure that you correctly spell the path name and that you are</span></span>  
  
 <span data-ttu-id="68461-197">連接到檔案所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="68461-197">connected to the server on which the file resides.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-198">原因</span><span class="sxs-lookup"><span data-stu-id="68461-198">Cause</span></span>  
 <span data-ttu-id="68461-199">組態程式無法判斷安裝 SQL Server Analysis Server 之電腦的新名稱。</span><span class="sxs-lookup"><span data-stu-id="68461-199">The configuration program is unable to determine the new name of the computer on which you installed SQL Server Analysis Server.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-200">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-200">Resolution</span></span>  
 <span data-ttu-id="68461-201">請以手動方式執行以下步驟，將 Analysis Server 更新為新的電腦名稱：</span><span class="sxs-lookup"><span data-stu-id="68461-201">Perform the following manual steps to update Analysis Server with the new computer name:</span></span>  
  
1.  <span data-ttu-id="68461-202">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server**，指向  **Analysis Services**，然後按一下  **Analysis Manager**。</span><span class="sxs-lookup"><span data-stu-id="68461-202">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Analysis Services**, and then click **Analysis Manager**.</span></span>  
  
2.  <span data-ttu-id="68461-203">在**Analysis Manager**導覽面板中按兩下**Analysis Servers**節點來展開它。</span><span class="sxs-lookup"><span data-stu-id="68461-203">In the **Analysis Manager** navigation panel, double-click the **Analysis Servers** node to expand it.</span></span>  
  
3.  <span data-ttu-id="68461-204">以滑鼠右鍵按一下您想要編輯，然後選取 儲存機制連線字串伺服器**編輯儲存機制連線字串**。</span><span class="sxs-lookup"><span data-stu-id="68461-204">Right-click the server with the repository connection string you want to edit, and then select **Edit Repository Connection String**.</span></span>  
  
4.  <span data-ttu-id="68461-205">在**編輯儲存機制連線字串**對話方塊，確認伺服器名稱，這個字串中的，將其更新為新的電腦名稱是否正確。</span><span class="sxs-lookup"><span data-stu-id="68461-205">In the **Edit Repository Connection String** dialog box, verify the server name in this string and update it to the new computer name if it is incorrect.</span></span>  
  
5.  <span data-ttu-id="68461-206">瀏覽至下列位置： \<*安裝目錄*\>\Program Files\Microsoft Analysis Services\Bin。</span><span class="sxs-lookup"><span data-stu-id="68461-206">Navigate to the following location: \<*installation directory*\>\Program Files\Microsoft Analysis Services\Bin.</span></span>  
  
6.  <span data-ttu-id="68461-207">以滑鼠右鍵按一下**Bin**資料夾，然後再按一下**共用和安全性**。</span><span class="sxs-lookup"><span data-stu-id="68461-207">Right-click the **Bin** folder, and then click **Sharing and Security**.</span></span> <span data-ttu-id="68461-208">**Bin 屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="68461-208">The **Bin Properties** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="68461-209">在**Bin 屬性**對話方塊中，按一下 **共用**索引標籤，以確認所有的線上分析處理 (OLAP) 系統管理員具有完整權限，此資料夾。</span><span class="sxs-lookup"><span data-stu-id="68461-209">In the **Bin Properties** dialog box, click the **Sharing** tab to verify that all Online Analytical Processing (OLAP) administrators have full permissions to this folder.</span></span>  
  
#### <a name="artifacts-disappear-from-configuration-database-on-redeployment-of-assemblies-from-visual-studio"></a><span data-ttu-id="68461-210">從 Visual Studio 重新部署組件時，成品從組態資料庫中消失</span><span class="sxs-lookup"><span data-stu-id="68461-210">Artifacts Disappear from Configuration Database on Redeployment of Assemblies from Visual Studio</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-211">問題</span><span class="sxs-lookup"><span data-stu-id="68461-211">Problem</span></span>  
 <span data-ttu-id="68461-212">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 內的專案層級上重新部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案時，此專案中參考重新部署之專案的所有成品似乎會在重新整理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MMC 後消失。</span><span class="sxs-lookup"><span data-stu-id="68461-212">When a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project is redeployed at the project level within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], all artifacts contained within the project that reference the project being redeployed will appear to vanish when the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MMC is refreshed.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-213">原因</span><span class="sxs-lookup"><span data-stu-id="68461-213">Cause</span></span>  
 <span data-ttu-id="68461-214">為了說明這個問題的原因，假設以下範例是根據範例 BizTalk Server 解決方案，而使用者想要在其中重新部署 Maps 專案。</span><span class="sxs-lookup"><span data-stu-id="68461-214">To illustrate the cause of this problem, consider the following example based on a sample BizTalk Server solution where a user wants to redeploy the Maps project.</span></span> <span data-ttu-id="68461-215">請注意，編譯專案會產生個別的組件。</span><span class="sxs-lookup"><span data-stu-id="68461-215">Note that compiling projects yields individual assemblies.</span></span> <span data-ttu-id="68461-216">下圖指示使用者執行重新部署之前的解決方案狀態，</span><span class="sxs-lookup"><span data-stu-id="68461-216">The following figure indicates the state of the solution before the user does a redeployment.</span></span> <span data-ttu-id="68461-217">成品之間的關係如下：</span><span class="sxs-lookup"><span data-stu-id="68461-217">The relationships among the artifacts are as follows:</span></span>  
  
-   <span data-ttu-id="68461-218">Orch1、Orch2、Maps、Pipelines 和 Schemas 都是專案。</span><span class="sxs-lookup"><span data-stu-id="68461-218">Orch1, Orch2, Maps, Pipelines, and Schemas are projects.</span></span>  
  
-   <span data-ttu-id="68461-219">Orch1 參考 Maps，而 Maps 則參考 Schemas。</span><span class="sxs-lookup"><span data-stu-id="68461-219">Orch1 references Maps, which in turn references Schemas.</span></span>  
  
-   <span data-ttu-id="68461-220">Orch2 參考 Schemas。</span><span class="sxs-lookup"><span data-stu-id="68461-220">Orch2 references Schemas.</span></span>  
  
-   <span data-ttu-id="68461-221">Pipelines 參考 Schemas。</span><span class="sxs-lookup"><span data-stu-id="68461-221">Pipelines references Schemas.</span></span>  
  
 <span data-ttu-id="68461-222">![](../core/media/bcd-existingbiztalkserversolutionc.gif "bcd_ExistingBizTalkServerSolutionc")</span><span class="sxs-lookup"><span data-stu-id="68461-222">![](../core/media/bcd-existingbiztalkserversolutionc.gif "bcd_ExistingBizTalkServerSolutionc")</span></span>  
  
 <span data-ttu-id="68461-223">如果使用者使用預設 Visual Studio 專案設定來重新部署 Maps 專案，則 Orch1、Orch2 和 Pipeline 成品會消失，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="68461-223">If the user redeploys the Maps project using the default Visual Studio project settings, the Orch1, Orch2, and Pipeline artifacts vanish, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="68461-224">![](../core/media/bcd-biztalksolutionwlostartifactsc.gif "bcd_BizTalkSolutionWLostArtifactsc")</span><span class="sxs-lookup"><span data-stu-id="68461-224">![](../core/media/bcd-biztalksolutionwlostartifactsc.gif "bcd_BizTalkSolutionWLostArtifactsc")</span></span>  
  
 <span data-ttu-id="68461-225">重新部署 Maps 是一個兩個步驟的程序，要先解除部署目前已部署的 Maps.dll 組件，然後部署新的 Maps.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="68461-225">Redeploying Maps is a two-step process of undeploying the currently deployed Maps.dll assembly, and then deploying the new Maps.dll file.</span></span> <span data-ttu-id="68461-226">Visual Studio 重新部署程序的一部分，請以自動執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="68461-226">Visual Studio performs these steps automatically as part of the redeployment process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68461-227">上一個句子嚴格來說並不正確，因為 Visual Studio 一定會執行這些步驟，所以它不會意識到這是適當的作法。</span><span class="sxs-lookup"><span data-stu-id="68461-227">The preceding sentence is not strictly correct because these are steps that Visual Studio always does so there is no notion of it being the proper way.</span></span>  
  
 <span data-ttu-id="68461-228">關鍵的地方是，為了要解除部署 BizTalk Server 組件，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 也必須解除部署相依於該組件 (已設定部署旗標) 的所有組件。</span><span class="sxs-lookup"><span data-stu-id="68461-228">The key point is that in order to undeploy a BizTalk Server assembly, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] has to undeploy all assemblies that are dependent upon that assembly that have the deploy flag set.</span></span> <span data-ttu-id="68461-229">在這個範例中，若要執行重新部署的第一個解除部署步驟，BizTalk Server 需要解除部署 Orch1.dll (它相依於 Maps.dll)。</span><span class="sxs-lookup"><span data-stu-id="68461-229">In our example, to perform the first undeployment step of the redeployment, BizTalk Server needs to undeploy Orch1.dll (which depends on Maps.dll).</span></span> <span data-ttu-id="68461-230">在解除部署 Maps.dll 時，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 也會解除部署 Schemas.dll (假設它已設定部署旗標)。</span><span class="sxs-lookup"><span data-stu-id="68461-230">During the undeployment of Maps.dll, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] also undeploys Schemas.dll (assuming it has the deploy flag set).</span></span> <span data-ttu-id="68461-231">為了要解除部署 Schemas.dll，Visual Studio 需要解除部署 Orch2.dll 和 Pipelines.dll (這兩者都相依於 Schemas.dll)。</span><span class="sxs-lookup"><span data-stu-id="68461-231">In order to undeploy Schemas.dll, Visual Studio needs to undeploy Orch2.dll and Pipelines.dll (both of which depend on Schemas.dll).</span></span>  
  
 <span data-ttu-id="68461-232">問題在於，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]甲重新部署只有 Maps.dll 和它所依據的組件： 在此情況下，Schemas.dll。</span><span class="sxs-lookup"><span data-stu-id="68461-232">A problem exists in that [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] redeploys only Maps.dll and the assemblies that it depends upon: in this case, Schemas.dll.</span></span> <span data-ttu-id="68461-233">讓使用者重新整理 BizTalk Server MMC 時，Orch1、 Orch2 和 Pipeline 組件似乎已消失，但是 Maps.dll 和 Schemas.dll 仍然可見。</span><span class="sxs-lookup"><span data-stu-id="68461-233">So when the user refreshes the BizTalk Server MMC, the Orch1, Orch2, and Pipeline assemblies seem to have vanished, but Maps.dll and Schemas.dll are still visible.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-234">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-234">Resolution</span></span>  
 <span data-ttu-id="68461-235">如果是主要專案 (它會參考其他專案)，請執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="68461-235">For the main project (that references other projects) do the following:</span></span>  
  
1.  <span data-ttu-id="68461-236">在 [方案總管] 中，以滑鼠右鍵按一下方案節點。</span><span class="sxs-lookup"><span data-stu-id="68461-236">In Solution Explorer, right-click the solution node.</span></span>  
  
2.  <span data-ttu-id="68461-237">按一下**屬性**開啟**方案屬性頁** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="68461-237">Click **Properties** to open the **Solution Property Pages** dialog box.</span></span>  
  
3.  <span data-ttu-id="68461-238">按一下**組態屬性**，然後按一下 **組態**。</span><span class="sxs-lookup"><span data-stu-id="68461-238">Click **Configuration Properties**, and then click **Configuration**.</span></span>  
  
4.  <span data-ttu-id="68461-239">清除**部署**參考之專案的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="68461-239">Clear the **Deploy** check box for the referenced project.</span></span>  
  
5.  <span data-ttu-id="68461-240">在 [方案總管] 中，執行新的方案層級部署。</span><span class="sxs-lookup"><span data-stu-id="68461-240">In Solution Explorer, execute a new solution-level deployment.</span></span> <span data-ttu-id="68461-241">若要這樣做，以滑鼠右鍵按一下方案節點，然後按一下 **部署方案**。</span><span class="sxs-lookup"><span data-stu-id="68461-241">To do this, right-click the solution node and then click **Deploy Solution**.</span></span>  
  
#### <a name="supported-virtual-directory-types"></a><span data-ttu-id="68461-242">支援的虛擬目錄類型</span><span class="sxs-lookup"><span data-stu-id="68461-242">Supported Virtual Directory Types</span></span>  
 <span data-ttu-id="68461-243">匯出作業時參考 Web 服務從協調流程，並嘗試進行 MSI 匯出，將會成功，相關聯的虛擬目錄為型別時，才**IIsWebVirtualDir**或**IIsWebDirectory**.</span><span class="sxs-lookup"><span data-stu-id="68461-243">When referencing Web services from an orchestration and attempting to do an MSI export, the export operation will succeed only if the associated virtual directories are of type **IIsWebVirtualDir** or **IIsWebDirectory**.</span></span> <span data-ttu-id="68461-244">**IIsWebVirtualDir**和**IIsWebDirectory**會出現在 IIS metabase 中的節點型別。</span><span class="sxs-lookup"><span data-stu-id="68461-244">**IIsWebVirtualDir** and **IIsWebDirectory** are the node types that appear in the IIS metabase.</span></span> <span data-ttu-id="68461-245">**IIsWebVirtualDir**是使用的虛擬目錄**路徑**指向絕對檔案資料夾的屬性。</span><span class="sxs-lookup"><span data-stu-id="68461-245">**IIsWebVirtualDir** is a virtual directory with a **Path** property that points to an absolute file folder.</span></span> <span data-ttu-id="68461-246">**IIsWebDirectory**而不是虛擬目錄**路徑**屬性，因此是指相對檔案資料夾，通常是另一個子資料夾**IIsWebVirtualDir**或**IIsWebDirectory**節點。</span><span class="sxs-lookup"><span data-stu-id="68461-246">**IIsWebDirectory** is a virtual directory without a **Path** property and thus refers to a relative file folder, typically a subfolder of another **IIsWebVirtualDir** or **IIsWebDirectory** node.</span></span> <span data-ttu-id="68461-247">在 Metabase 階層中，經常會看到用來描述資料夾的這兩個類型。</span><span class="sxs-lookup"><span data-stu-id="68461-247">These two types are the ones typically seen in the metabase hierarchy to describe folders.</span></span>  
  
 <span data-ttu-id="68461-248">類型的虛擬目錄**IIsConfigObject**不支援 MSI 匯出會在此情況下失敗。</span><span class="sxs-lookup"><span data-stu-id="68461-248">Virtual directories of type **IIsConfigObject** are not supported and the MSI export will fail in this case.</span></span> <span data-ttu-id="68461-249">**IIsConfigObject**非預期的 metabase 節點類型可以是 BizTalk Server 未適當處理的有效節點類型，或未適當建立的 （並因此它是無效的） metabase 項目的指示。</span><span class="sxs-lookup"><span data-stu-id="68461-249">**IIsConfigObject** is an unexpected metabase node type that is either a valid node type that BizTalk Server is not handling properly or an indication of an improperly created (and thus invalid) metabase entry.</span></span> <span data-ttu-id="68461-250">在此情況下，BizTalk Server 將會顯示類似下列的錯誤訊息： 類型 IIsConfigObject 的未預期的目錄項目"Iis: //lm/w3svc/1/root/badvdir/"。</span><span class="sxs-lookup"><span data-stu-id="68461-250">In this situation BizTalk Server will display an error message something like the following: Unexpected directory entry " IIS://LM/W3SVC/1/ROOT/BadVdir/" of type IIsConfigObject.</span></span>  
  
#### <a name="unable-to-view-group-information-after-removing-stale-logons"></a><span data-ttu-id="68461-251">在移除過時的登入之後，無法檢視群組資訊</span><span class="sxs-lookup"><span data-stu-id="68461-251">Unable to view Group information after removing stale logons</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="68461-252">問題</span><span class="sxs-lookup"><span data-stu-id="68461-252">Problem</span></span>  
 <span data-ttu-id="68461-253">如果在組態進行期間，您發現了過時的登入並將它刪除，您可能就無法檢視群組資訊。</span><span class="sxs-lookup"><span data-stu-id="68461-253">If, during configuration, you encounter and delete stale logons, you may not be able to view Group information.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="68461-254">原因</span><span class="sxs-lookup"><span data-stu-id="68461-254">Cause</span></span>  
 <span data-ttu-id="68461-255">這是已知的組態問題。</span><span class="sxs-lookup"><span data-stu-id="68461-255">This is a known configuration issue.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="68461-256">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-256">Resolution</span></span>  
 <span data-ttu-id="68461-257">刪除主控件 Windows 群組登入，然後再重新設定可能會有幫助。</span><span class="sxs-lookup"><span data-stu-id="68461-257">It may help to delete the Host Windows group logons and then reconfigure.</span></span> <span data-ttu-id="68461-258">如果仍然無法使用群組資訊，請連絡 Microsoft 產品支援中心。</span><span class="sxs-lookup"><span data-stu-id="68461-258">If the Group information is still not available, contact Microsoft Product Support.</span></span>  
  
##### <a name="cannot-change-computer-name-after-biztalk-server-is-installed"></a><span data-ttu-id="68461-259">BizTalk Server 安裝之後，無法變更電腦名稱</span><span class="sxs-lookup"><span data-stu-id="68461-259">Cannot change computer name after BizTalk Server is installed</span></span>  
  
###### <a name="problem"></a><span data-ttu-id="68461-260">問題</span><span class="sxs-lookup"><span data-stu-id="68461-260">Problem</span></span>  
 <span data-ttu-id="68461-261">當您變更執行的電腦上的電腦名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，而且您重新啟動 （重新開機） 的電腦，錯誤訊息可能會發生。</span><span class="sxs-lookup"><span data-stu-id="68461-261">When you change the computer name on a computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and you restart (reboot) the computer, error messages may occur.</span></span>  
  
###### <a name="cause"></a><span data-ttu-id="68461-262">原因</span><span class="sxs-lookup"><span data-stu-id="68461-262">Cause</span></span>  
 <span data-ttu-id="68461-263">SQL Server 不支援變更電腦名稱，因此[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援一次變更電腦名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝和設定。</span><span class="sxs-lookup"><span data-stu-id="68461-263">SQL Server does not support changing the computer name, so [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not support changing the computer name once [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed and configured.</span></span>  
  
###### <a name="resolution"></a><span data-ttu-id="68461-264">解決方案</span><span class="sxs-lookup"><span data-stu-id="68461-264">Resolution</span></span>  
 <span data-ttu-id="68461-265">我們建議您不要變更電腦名稱之後您安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="68461-265">We recommend that you do not change computer names after you install BizTalk Server.</span></span>