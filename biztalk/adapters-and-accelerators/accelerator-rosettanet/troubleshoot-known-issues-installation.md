---
title: 疑難排解和已知的問題與 BizTalk RosettaNet 加速器 (BTARN) 中安裝 BizTalk Server 上 |Microsoft 文件 」
description: 安裝 BTARN 安裝在 BizTalk Server 中的 SQL，主控件執行個體，以及已知的錯誤的服務帳戶建議
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdca89c1a7a4ed3834103776f9f28c8631c5de0a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22210838"
---
# <a name="troubleshoot-the-installation-and-see-the-known-install-issues"></a><span data-ttu-id="94ad0-103">安裝的疑難排解，並查看已知的安裝問題</span><span class="sxs-lookup"><span data-stu-id="94ad0-103">Troubleshoot the installation and see the known install issues</span></span>

  
## <a name="do-not-install-sql-server-on-the-domain-controller-computer"></a><span data-ttu-id="94ad0-104">請勿在網域控制站電腦上安裝 SQL Server</span><span class="sxs-lookup"><span data-stu-id="94ad0-104">Do not install SQL Server on the domain controller computer</span></span>  
 <span data-ttu-id="94ad0-105">如果您在與您的網域控制站電腦相同的電腦上安裝 SQL Server，它會傳回下列錯誤訊息時嘗試建立 SQL 傳送埠：</span><span class="sxs-lookup"><span data-stu-id="94ad0-105">If you install SQL Server on the same computer as your domain controller computer, it returns the following error message when it is trying to create the SQL send ports:</span></span>  
  
```
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500.  
Error: Failed updating binding information.  
BindingException: Could not validate TransportTypeData or Address properties for Primary Transport of Send Port 'SendPort1'. Exception from HRESULT: 0x80131500  

```
  
> [!IMPORTANT]
>  <span data-ttu-id="94ad0-106">請勿在網域控制站電腦上安裝 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="94ad0-106">Do not install SQL Server on the domain controller computer.</span></span>  
  
## <a name="service-account-for-the-application-pools-must-be-the-same-as-the-service-account-for-the-isolated-host-and-host-instances"></a><span data-ttu-id="94ad0-107">應用程式集區的服務帳戶必須和外掛式主控件和主控件執行個體的服務帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="94ad0-107">Service account for the application pools must be the same as the service account for the Isolated Host and Host instances</span></span>  
 <span data-ttu-id="94ad0-108">如果設定 BTARN 應用程式集區的服務帳戶與外掛式主控件帳戶不同，BTARN 不正確地處理內送訊息。</span><span class="sxs-lookup"><span data-stu-id="94ad0-108">If the service account set for the BTARN application pools is different from the Isolated Host account, BTARN does not process incoming messages correctly.</span></span> <span data-ttu-id="94ad0-109">當接收.aspx 頁面呼叫管線時，管線中沒有適當的憑證的存取權。</span><span class="sxs-lookup"><span data-stu-id="94ad0-109">When the receive .aspx page calls the pipeline, the pipeline does not have access to the appropriate certificates.</span></span> <span data-ttu-id="94ad0-110">因此，它不解密內送訊息或驗證簽章。</span><span class="sxs-lookup"><span data-stu-id="94ad0-110">Therefore, it does not decrypt the incoming message or validate the signature.</span></span> <span data-ttu-id="94ad0-111">此外，它將無法存取 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="94ad0-111">Also, it won't be able to access the MessageBox database.</span></span>  
  

## <a name="known-install-issues"></a><span data-ttu-id="94ad0-112">已知的安裝問題</span><span class="sxs-lookup"><span data-stu-id="94ad0-112">Known install issues</span></span>

  
### <a name="btarn-http-front-end-feature-configuration-fails"></a><span data-ttu-id="94ad0-113">BTARN HTTP 前端功能組態失敗</span><span class="sxs-lookup"><span data-stu-id="94ad0-113">BTARN HTTP Front End Feature configuration fails</span></span>  
 <span data-ttu-id="94ad0-114">**問題**</span><span class="sxs-lookup"><span data-stu-id="94ad0-114">**Problem**</span></span>  
  
 <span data-ttu-id="94ad0-115">如果您執行只安裝 BTARN HTTP 前端功能的自訂安裝，BTARN 組態可能會失敗，發生下列錯誤，安裝程式完成之後：</span><span class="sxs-lookup"><span data-stu-id="94ad0-115">If you perform a custom installation to install only the BTARN HTTP Front End feature, BTARN configuration may fail with the following error after setup has completed:</span></span> 

`Failed to create object for feature: WebApp`  
  
 <span data-ttu-id="94ad0-116">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="94ad0-116">**Resolution**</span></span>  
  
<span data-ttu-id="94ad0-117">手動複製檔案，並重新設定：</span><span class="sxs-lookup"><span data-stu-id="94ad0-117">Manually copy files and reconfigure:</span></span> 
  
1.  <span data-ttu-id="94ad0-118">BizTalk Server 電腦的下列兩個檔案複製到您安裝 BTARN HTTP 前端功能的電腦：</span><span class="sxs-lookup"><span data-stu-id="94ad0-118">Copy the following two files from an BizTalk Server computer to the computer on which you installed the BTARN HTTP Front End feature:</span></span>
  
    -   <span data-ttu-id="94ad0-119">Microsoft.VC80.ATL.manifest</span><span class="sxs-lookup"><span data-stu-id="94ad0-119">Microsoft.VC80.ATL.manifest</span></span>  
  
    -   <span data-ttu-id="94ad0-120">atl80.dll</span><span class="sxs-lookup"><span data-stu-id="94ad0-120">atl80.dll</span></span>  
  
     <span data-ttu-id="94ad0-121">如果與 BizTalk Server 在相同電腦上安裝 Visual Studio，兩個檔案的來源資料夾是 <*磁碟機*>: \Program Files\Microsoft Visual Studio < 版本\>\VC\redist\x86\Microsoft.VC100.ATL.</span><span class="sxs-lookup"><span data-stu-id="94ad0-121">If Visual Studio is installed on the same computer as BizTalk Server, the source folder for the two files is <*drive*>:\Program Files\Microsoft Visual Studio <version\>\VC\redist\x86\Microsoft.VC100.ATL.</span></span>  
  
     <span data-ttu-id="94ad0-122">在相同的 BizTalk Server 電腦上未安裝 Visual Studio，將兩個檔案的來源資料夾是否低於 <*磁碟機*>: \WINDOWS\WinSxS。</span><span class="sxs-lookup"><span data-stu-id="94ad0-122">If Visual Studio is not installed on the same BizTalk Server computer, the source folder for the two files is under <*drive*>:\WINDOWS\WinSxS.</span></span>  
  
2.  <span data-ttu-id="94ad0-123">將複製的檔案新增到您安裝 BTARN HTTP 前端功能的電腦上。</span><span class="sxs-lookup"><span data-stu-id="94ad0-123">Add the copied files to the computer on which you installed BTARN HTTP Front End feature.</span></span> <span data-ttu-id="94ad0-124">根據預設，將檔案複製到 <*磁碟機*>: \Program Files\Microsoft BizTalk Accelerator for RosettaNet。</span><span class="sxs-lookup"><span data-stu-id="94ad0-124">By default, copy the files to <*drive*>:\Program Files\Microsoft BizTalk Accelerator for RosettaNet.</span></span>  
  
3.  <span data-ttu-id="94ad0-125">將檔案複製到 HTTP 前端電腦之後，執行**Configuration.exe**一次。</span><span class="sxs-lookup"><span data-stu-id="94ad0-125">After you have copied the files to the HTTP Front End computer, run **Configuration.exe** again.</span></span>  
  
### <a name="some-btarn-assemblies-stay-in-gac-after-uninstalling"></a><span data-ttu-id="94ad0-126">部分 BTARN 組件停留在 GAC 中解除安裝之後</span><span class="sxs-lookup"><span data-stu-id="94ad0-126">Some BTARN Assemblies stay in GAC after uninstalling</span></span>  
 <span data-ttu-id="94ad0-127">**問題**</span><span class="sxs-lookup"><span data-stu-id="94ad0-127">**Problem**</span></span>  
  
 <span data-ttu-id="94ad0-128">當您解除安裝 BTARN 時，某些組件仍保留在全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="94ad0-128">When you uninstall BTARN, some assemblies remain in the global assembly cache (GAC).</span></span>  
  
 <span data-ttu-id="94ad0-129">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="94ad0-129">**Resolution**</span></span>  
  
 <span data-ttu-id="94ad0-130">先從 GAC 移除組件，再重新安裝 BTARN。</span><span class="sxs-lookup"><span data-stu-id="94ad0-130">Remove the assemblies from the GAC before reinstalling BTARN.</span></span>  
  
 <span data-ttu-id="94ad0-131">使用**BtarnClean**公用程式的 SDK，以移除組件。</span><span class="sxs-lookup"><span data-stu-id="94ad0-131">Use the **BtarnClean** utility from the SDK to remove the assemblies.</span></span> <span data-ttu-id="94ad0-132">公用程式會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="94ad0-132">The utility performs the following actions:</span></span>  
  
-   <span data-ttu-id="94ad0-133">停止和取消登錄所有的 BTARN 協調流程。</span><span class="sxs-lookup"><span data-stu-id="94ad0-133">Stops and unenlists all the BTARN orchestrations.</span></span>  
  
-   <span data-ttu-id="94ad0-134">停止和刪除所有關聯的連接埠。</span><span class="sxs-lookup"><span data-stu-id="94ad0-134">Stops and deletes all the associated ports.</span></span>  
  
-   <span data-ttu-id="94ad0-135">解除部署所有的 Microsoft.Solutions.BTARN.\* 組件。</span><span class="sxs-lookup"><span data-stu-id="94ad0-135">Undeploys all the Microsoft.Solutions.BTARN.\* assemblies.</span></span>  
  
 <span data-ttu-id="94ad0-136">執行公用程式後，如果 GAC 中仍存在組件，請開啟 [檔案總管]，移至 "C:\Windows\Assembly" 資料夾，手動刪除所有開頭為 Microsoft.Solutions.BTARN 的組件。</span><span class="sxs-lookup"><span data-stu-id="94ad0-136">After running the utility, if there are assemblies remaining in the GAC, open Windows Explorer, go to the "C:\Windows\Assembly" folder, and then manually delete all assemblies starting with Microsoft.Solutions.BTARN.</span></span>  
  
### <a name="service-unavailable-error-on-64-bit-os"></a><span data-ttu-id="94ad0-137">64 位元作業系統上的服務無法使用錯誤</span><span class="sxs-lookup"><span data-stu-id="94ad0-137">Service Unavailable error on 64-bit OS</span></span>
 <span data-ttu-id="94ad0-138">**問題**</span><span class="sxs-lookup"><span data-stu-id="94ad0-138">**Problem**</span></span>  
  
 <span data-ttu-id="94ad0-139">您可能會收到`Service Unavailable`錯誤時嘗試存取 BTARN HTTP 接收位置在 64 位元 Windows 作業系統上的。</span><span class="sxs-lookup"><span data-stu-id="94ad0-139">You may get a `Service Unavailable` error when trying to access the BTARN HTTP receive location on 64-bit Windows operating systems.</span></span>  
  
 <span data-ttu-id="94ad0-140">**原因**</span><span class="sxs-lookup"><span data-stu-id="94ad0-140">**Cause**</span></span>  
  
 <span data-ttu-id="94ad0-141">這個問題可能是由 "RPCProxy.dll" ISAPI 篩選器所造成。</span><span class="sxs-lookup"><span data-stu-id="94ad0-141">This issue can be caused by the "RPCProxy.dll" ISAPI filter.</span></span>  
  
 <span data-ttu-id="94ad0-142">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="94ad0-142">**Resolution**</span></span>  
  
<span data-ttu-id="94ad0-143">移除 RPC proxy ISAPI 篩選器的參考，並重新啟動 IIS:</span><span class="sxs-lookup"><span data-stu-id="94ad0-143">Remove references to the RPC proxy ISAPI filter and restart IIS:</span></span>
  
1.  <span data-ttu-id="94ad0-144">在網際網路資訊服務 (IIS) 管理員中，以滑鼠右鍵按一下**網站**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="94ad0-144">In Internet Information Services (IIS) Manager, right-click **Web Sites**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="94ad0-145">在**網站內容**對話方塊中，按一下  **ISAPI 篩選器**索引標籤上，移除**RPC Proxy**篩選，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="94ad0-145">In the **Web Site Properties** dialog box, click the **ISAPI filters** tab, remove **RPC Proxy** filter, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="94ad0-146">重新啟動 IIS。</span><span class="sxs-lookup"><span data-stu-id="94ad0-146">Restart IIS.</span></span>  
  
4.  <span data-ttu-id="94ad0-147">在您重新啟動 IIS 後，請再次嘗試存取http://localhost。</span><span class="sxs-lookup"><span data-stu-id="94ad0-147">After you have restarted IIS, try accessing http://localhost.</span></span> <span data-ttu-id="94ad0-148">您應該會從網際網路瀏覽器收到 400 訊息。</span><span class="sxs-lookup"><span data-stu-id="94ad0-148">You should get the 400 message back from the Internet browser.</span></span>  
  
### <a name="sql-server-mixed-mode-not-supported"></a><span data-ttu-id="94ad0-149">不支援的 SQL Server 混合模式</span><span class="sxs-lookup"><span data-stu-id="94ad0-149">SQL Server Mixed Mode not supported</span></span>  
<span data-ttu-id="94ad0-150">BTARN 不支援 SQL Server 混合模式中。</span><span class="sxs-lookup"><span data-stu-id="94ad0-150">BTARN does not support SQL Server in mixed mode.</span></span>  
  
### <a name="run-setupx64bat-to-set-up-the-double-action-pipautomation-orchestration-sample"></a><span data-ttu-id="94ad0-151">執行 setupx64.bat，以設定雙向動作 PIPAutomation 協調流程範例</span><span class="sxs-lookup"><span data-stu-id="94ad0-151">Run setupx64.bat to set up the double action PIPAutomation orchestration sample</span></span> 

<span data-ttu-id="94ad0-152">執行中的 setupx64.bat \Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction 資料夾以安裝雙向動作 PIPAutomation 協調流程範例。</span><span class="sxs-lookup"><span data-stu-id="94ad0-152">Run setupx64.bat in \Program Files\Microsoft BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction folder to set up the Double Action PIPAutomation Orchestration sample.</span></span>
  
### <a name="download-the-btarn-setup-file-from-the-web-to-a-temp-folder"></a><span data-ttu-id="94ad0-153">將 BTARN 安裝程式檔案從 Web 下載到 Temp 資料夾</span><span class="sxs-lookup"><span data-stu-id="94ad0-153">Download the BTARN Setup File from the Web to a Temp Folder</span></span>  
 <span data-ttu-id="94ad0-154">**問題**</span><span class="sxs-lookup"><span data-stu-id="94ad0-154">**Problem**</span></span>  
  
 <span data-ttu-id="94ad0-155">如果您下載 BTARN 自動解壓縮可執行檔，從網站，並將它儲存到 BizTalk 伺服器根資料夾中，當您嘗試執行可執行檔，BizTalk**安裝精靈**執行，而不是 BTARN 安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="94ad0-155">If you download the BTARN self-extracting executable file from the Web, and save it to the BizTalk Server root folder, when you attempt to run the executable, the BizTalk **Setup Wizard** runs, instead of the BTARN Setup wizard.</span></span>  
  
 <span data-ttu-id="94ad0-156">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="94ad0-156">**Resolution**</span></span>  
  
 <span data-ttu-id="94ad0-157">下載 BTARN 自動解壓縮可執行檔，並將檔案儲存到暫存資料夾。</span><span class="sxs-lookup"><span data-stu-id="94ad0-157">Download the BTARN self-extracting executable, and save the file to a temp folder.</span></span>
