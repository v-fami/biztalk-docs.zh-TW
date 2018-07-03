---
title: 建立前置或後置處理指令碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts, post-processing
- scripts, pre-processing
- scripts, warnings
- scripts, applications
- applications, scripts
- scripts, deploying
- deploying, scripts
ms.assetid: d5fbaec8-fbfe-4ceb-8ba8-0933baa37a1f
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6993ab2786cc33e40f00bab7910353170e318db0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006471"
---
# <a name="creating-a-pre--or-post-processing-script"></a><span data-ttu-id="a2d32-102">建立前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="a2d32-102">Creating a Pre- or Post-processing Script</span></span>
<span data-ttu-id="a2d32-103">您可以在部署應用程式時建立指令碼來執行動作，然後定義該指定碼在部署階段的執行時機。</span><span class="sxs-lookup"><span data-stu-id="a2d32-103">You can create a script to perform actions when an application is deployed, and then define when it will run during the deployment process.</span></span> <span data-ttu-id="a2d32-104">您可以利用環境變數來分隔程式碼，以便在同一個指令碼中同時包含安裝與清除程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2d32-104">You can include both installation and cleanup code in the same script, using environment variables to delimit the code.</span></span> <span data-ttu-id="a2d32-105">您也可以將命令列引數傳送至指令碼中。</span><span class="sxs-lookup"><span data-stu-id="a2d32-105">You can also pass command-line arguments into the script.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a2d32-106">當您編寫生產系統所使用的指令碼時，應該永遠採用無訊息模式。</span><span class="sxs-lookup"><span data-stu-id="a2d32-106">You should always write scripts intended for production systems in silent mode.</span></span> <span data-ttu-id="a2d32-107">那是因為等候使用者輸入動作的指令碼將會造成 BizTalk 資料庫在接收到使用者的輸入之前呈現鎖定而無法存取的狀態。</span><span class="sxs-lookup"><span data-stu-id="a2d32-107">This is because a script waiting for user input will cause the BizTalk databases to become locked and inaccessible until the input is received.</span></span>  
  
## <a name="specifying-when-a-script-will-run-during-deployment"></a><span data-ttu-id="a2d32-108">指定指令碼在部署時的執行時機</span><span class="sxs-lookup"><span data-stu-id="a2d32-108">Specifying when a script will run during deployment</span></span>  
 <span data-ttu-id="a2d32-109">當您將指令碼當作 System.BizTalk:PreProcessingScript (前置處理指令碼) 或者 System.BizTalk:PostProcessingScript (後置處理指令碼) 新增到應用程式時，即指定了指令碼的執行時機。</span><span class="sxs-lookup"><span data-stu-id="a2d32-109">You specify when a script will run when you add the script to an application by adding it as either a System.BizTalk:PreProcessingScript (pre-processing script) or a System.BizTalk:PostProcessingScript (post-processing script).</span></span>  
  
 <span data-ttu-id="a2d32-110">前置與後置處理指令碼執行時機如下：</span><span class="sxs-lookup"><span data-stu-id="a2d32-110">Pre- and post-processing scripts run as follows:</span></span>  
  
- <span data-ttu-id="a2d32-111">前置處理指令碼會在匯入或者安裝階段開始時執行。</span><span class="sxs-lookup"><span data-stu-id="a2d32-111">Pre-processing scripts run at the beginning of the import or installation process.</span></span>  
  
- <span data-ttu-id="a2d32-112">後置處理指令碼會在匯入或者安裝階段結束時執行。</span><span class="sxs-lookup"><span data-stu-id="a2d32-112">Post-processing scripts run at the end of the import or installation process.</span></span>  
  
- <span data-ttu-id="a2d32-113">在解除安裝階段，所有的指令碼都會依據安裝時的程序順序倒退執行。</span><span class="sxs-lookup"><span data-stu-id="a2d32-113">During uninstallation, all scripts run in the opposite order that they run during installation.</span></span> <span data-ttu-id="a2d32-114">因此，後置處理指令碼會在開始解除安裝時執行，而前置處理指令碼則是在解除安裝結束時執行。</span><span class="sxs-lookup"><span data-stu-id="a2d32-114">Therefore, post-processing scripts run at the beginning of uninstallation and pre-processing scripts at the end of uninstallation.</span></span>  
  
- <span data-ttu-id="a2d32-115">如果安裝程序失敗，所有的指令碼將會按照適當的回復動作，進行反向呼叫。</span><span class="sxs-lookup"><span data-stu-id="a2d32-115">If an installation fails, scripts are called in reverse order with the appropriate rollback action.</span></span>  
  
  <span data-ttu-id="a2d32-116">一旦叫用，前置或後置處理指令碼會判斷的部署狀態 （安裝、 匯入、 刪除、 解除安裝、 匯入回復或安裝回復） 在執行檢查環境變數 BTAD_ChangeRequestAction、 BTAD_InstallMode與 BTAD_HostClass 中所述[如何環境變數指出部署狀態](../core/how-environment-variables-indicate-deployment-state.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d32-116">Once invoked, a pre- or post-processing script determines which deployment state (install, import, delete, uninstall, import rollback, or install rollback) it is running in by checking the environment variables BTAD_ChangeRequestAction, BTAD_InstallMode, and BTAD_HostClass, as described in [How Environment Variables Indicate Deployment State](../core/how-environment-variables-indicate-deployment-state.md).</span></span> <span data-ttu-id="a2d32-117">如需變數的參考資訊，請參閱 <<c0> [ 前置和後置處理指令碼環境變數](../core/pre-and-post-processing-script-environment-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d32-117">For reference information about the variables, see [Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md).</span></span>  
  
  <span data-ttu-id="a2d32-118">如需應用程式中加入指令碼的指示，請參閱 <<c0> [ 如何新增前置或後置處理指令碼至應用程式](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d32-118">For instructions on adding a script to an application, see [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2d32-119">如果您想要將命令列引數包含在指令碼中，必須使用 AddResource 命令來新增指令碼，本文稍後將會討論。</span><span class="sxs-lookup"><span data-stu-id="a2d32-119">If you want to include command-line arguments in a script, as discussed later in this topic, you must use the AddResource command to add the script.</span></span>  
  
## <a name="supported-script-file-extensions"></a><span data-ttu-id="a2d32-120">支援的指令碼檔案副檔名</span><span class="sxs-lookup"><span data-stu-id="a2d32-120">Supported script file extensions</span></span>  
 <span data-ttu-id="a2d32-121">支援的指令碼檔案副檔名如下：.com、.exe、.bat、.cmd、.vbs、.vbe、.js、.jse、.wsf 以及 .wsh。</span><span class="sxs-lookup"><span data-stu-id="a2d32-121">The following script file extensions are supported: .com, .exe, .bat, .cmd, .vbs, .vbe, .js, .jse, .wsf, and .wsh.</span></span> <span data-ttu-id="a2d32-122">此副檔名集合是在 PATHEXT 環境變數中定義。</span><span class="sxs-lookup"><span data-stu-id="a2d32-122">This set of extensions is defined in the PATHEXT environment variable.</span></span>  
  
## <a name="logging-errors"></a><span data-ttu-id="a2d32-123">記錄錯誤</span><span class="sxs-lookup"><span data-stu-id="a2d32-123">Logging errors</span></span>  
 <span data-ttu-id="a2d32-124">您應該採用的最佳作法是，設定每個指令碼將錯誤記錄到檔案中。</span><span class="sxs-lookup"><span data-stu-id="a2d32-124">As a best practice, you should configure each script to log errors to a file.</span></span> <span data-ttu-id="a2d32-125">這是因為 Windows Installer 無法將指令碼產生的錯誤記錄起來。</span><span class="sxs-lookup"><span data-stu-id="a2d32-125">This is because Windows Installer does not log errors generated in the scripts.</span></span> <span data-ttu-id="a2d32-126">在指令碼執行完畢之後，您應該檢查這些日誌，看看是否有任何需要修正的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2d32-126">You should check these logs after the script runs for any errors that need to be addressed.</span></span>  
  
 <span data-ttu-id="a2d32-127">為了協助您判斷錯誤發生的時間，您可以在日誌檔案中加入日期與時間欄位。</span><span class="sxs-lookup"><span data-stu-id="a2d32-127">To help you determine when the error occurred, you can include the date and time in the log file.</span></span>  
  
 <span data-ttu-id="a2d32-128">使用下列程式碼來指定日誌檔案，然後記錄一個錯誤到該日誌。</span><span class="sxs-lookup"><span data-stu-id="a2d32-128">Use the following code to specify a log file and then log an error to it.</span></span>  
  
 `Set LogFile=<full path of log file>`  
  
 `…`  
  
 `echo %DATE% %TIME% <text> >> %LogFile%`  
  
 <span data-ttu-id="a2d32-129">在下列範例中，如果沒有定義公開金鑰 Token，則會在指定的日誌檔案中加入一個項目。</span><span class="sxs-lookup"><span data-stu-id="a2d32-129">In the following example, when the public key token is not defined, an entry is made in the specified log file.</span></span> <span data-ttu-id="a2d32-130">在日誌檔案中，資料與時間會與 "Public key should be set in script" 文字寫在同一行中。</span><span class="sxs-lookup"><span data-stu-id="a2d32-130">In the log file, the date and time is written in the same line as the text, "Public key should be set in script."</span></span>  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 <span data-ttu-id="a2d32-131">您也可以將 `exit /b 1` 新增到指令碼以便為 Windows Installer 產生錯誤程式碼，如此一來 Windows Installer 就會進行回復動作。</span><span class="sxs-lookup"><span data-stu-id="a2d32-131">You can also add the line `exit /b 1` to a script to generate an error code for Windows Installer, which will cause it to roll back.</span></span>  
  
 <span data-ttu-id="a2d32-132">在下列範例中，如果沒有定義公開金鑰 Token，則指令碼會將錯誤傳回至 Windows Installer，導致 Windows Installer 進行回復動作。</span><span class="sxs-lookup"><span data-stu-id="a2d32-132">In the following example, if the public key token has not been defined, the script will return an error to Windows Installer, and the installer will roll back.</span></span>  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 `exit /b 1`  
  
## <a name="including-installation-and-cleanup-code-in-the-same-script"></a><span data-ttu-id="a2d32-133">同一個指令碼中同時包含安裝與清除程式碼</span><span class="sxs-lookup"><span data-stu-id="a2d32-133">Including installation and cleanup code in the same script</span></span>  
 <span data-ttu-id="a2d32-134">因為指令碼在安裝與解除安裝階段會以完全相反的順序執行，您可以將安裝與清除程式碼納入相同指令碼中的條件陳述式裡。</span><span class="sxs-lookup"><span data-stu-id="a2d32-134">Because scripts run in the opposite order during installation and uninstallation, you can include installation and cleanup code in the same script, inside a conditional statement.</span></span> <span data-ttu-id="a2d32-135">例如，您可以將安裝程式碼置於用來檢查安裝模式的條件陳述式裡，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2d32-135">For example, you can place the installation code within a conditional statement that checks for the installation mode, as follows:</span></span>  
  
```  
  
%BTAD_ChangeRequestAction%=Update AND %BTAD_InstallMode%=Install  
  
```  
  
 <span data-ttu-id="a2d32-136">您可以在用來檢查安裝模式的條件陳述式中限定其清除程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2d32-136">You can qualify cleanup code within a conditional statement that checks for the installation mode, as follows:</span></span>  
  
```  
  
%BTAD_ChangeRequestAction%=Delete AND %BTAD_InstallMode%=Uninstall  
  
```  
  
## <a name="passing-in-command-line-arguments"></a><span data-ttu-id="a2d32-137">傳送命令列引數</span><span class="sxs-lookup"><span data-stu-id="a2d32-137">Passing in command-line arguments</span></span>  
 <span data-ttu-id="a2d32-138">當您使用 BTSTask AddResource 命令將指令碼新增到應用程式時，可以指定下列參數將命令列引數傳送至指令碼中。</span><span class="sxs-lookup"><span data-stu-id="a2d32-138">You can pass command-line arguments into the script by specifying the following parameter when you use the BTSTask AddResource command to add the script to the application.</span></span> <span data-ttu-id="a2d32-139">如果您這麼做，當叫用指令碼時，引數就會傳送至指令碼中。</span><span class="sxs-lookup"><span data-stu-id="a2d32-139">When you do this, the arguments are passed to the script when the script is invoked.</span></span>  
  
 <span data-ttu-id="a2d32-140">**/Property:Args =**」*引數清單*"</span><span class="sxs-lookup"><span data-stu-id="a2d32-140">**/Property:Args=**"*argument list*"</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2d32-141">如果您的應用程式中有多個前置或後置處理指令碼，則這些指令碼沒有特定的執行順序。</span><span class="sxs-lookup"><span data-stu-id="a2d32-141">If you have multiple pre- or post-processing scripts in and application, they are run in no particular order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a2d32-142">您應該避免在指令碼中使用 BTSTask 命令 (特別是那些會在匯入時執行的指令碼)，因為在同一個交易中，不同的指令碼不會被登記成匯入動作來處理。</span><span class="sxs-lookup"><span data-stu-id="a2d32-142">You should not use BTSTask commands in scripts, especially those that run during import, because scripts are not enlisted in the same transaction as an import.</span></span>  
  
 <span data-ttu-id="a2d32-143">如需使用 AddResource 命令將指令碼新增至應用程式的指示，請參閱 < [AddResource 命令： 前置處理指令碼](../core/addresource-command-preprocessing-script.md)。</span><span class="sxs-lookup"><span data-stu-id="a2d32-143">For instructions on using the AddResource command to add a script to an application, see [AddResource Command: Preprocessing Script](../core/addresource-command-preprocessing-script.md).</span></span> <span data-ttu-id="a2d32-144">另請參閱[AddResource 命令： 後置處理指令碼](../core/addresource-command-postprocessing-script.md)</span><span class="sxs-lookup"><span data-stu-id="a2d32-144">Also see [AddResource Command: Postprocessing Script](../core/addresource-command-postprocessing-script.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d32-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2d32-145">See Also</span></span>  
 <span data-ttu-id="a2d32-146">[使用前置和後置處理指令碼自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="a2d32-146">[Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md) </span></span>  
 [<span data-ttu-id="a2d32-147">Template (應用程式部署範例)</span><span class="sxs-lookup"><span data-stu-id="a2d32-147">Template (Application Deployment Sample)</span></span>](../core/template-application-deployment-sample.md)