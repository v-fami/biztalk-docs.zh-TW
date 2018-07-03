---
title: 設定 HTTP 接收位置的 IIS |Microsoft Docs
description: 在 IIS 中，建立 BTS HTTP 接收應用程式和測試 BizTalk Server 中的應用程式集區設定
ms.custom: ''
ms.date: 10/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfc616fa9834071c2ee8d2b4d63f486ff0abbeab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004821"
---
# <a name="configure-iis-for-an-http-receive-location"></a><span data-ttu-id="a5067-103">設定 HTTP 接收位置的 IIS</span><span class="sxs-lookup"><span data-stu-id="a5067-103">Configure IIS for an HTTP Receive Location</span></span>
<span data-ttu-id="a5067-104">HTTP 接收位置所使用的應用程式在網際網路資訊服務 (IIS)。</span><span class="sxs-lookup"><span data-stu-id="a5067-104">The HTTP receive location uses an application within Internet Information Services (IIS).</span></span> <span data-ttu-id="a5067-105">本主題列出的步驟來啟用 HTTP 接收在 IIS 中的位置。</span><span class="sxs-lookup"><span data-stu-id="a5067-105">This topic lists the steps to enable the HTTP receive location within IIS.</span></span> 

<span data-ttu-id="a5067-106">根據您的作業系統，設定 IIS 應用程式的步驟可能會不同。</span><span class="sxs-lookup"><span data-stu-id="a5067-106">Depending on your operating system, the steps to configure the IIS application may vary.</span></span> <span data-ttu-id="a5067-107">做為指南，使用下列步驟，因為其使用者介面可能會在您的作業系統上不同。</span><span class="sxs-lookup"><span data-stu-id="a5067-107">Use these steps as a guide, as the user interface may be different on your OS.</span></span>
  
## <a name="32-bit-vs-64-bit"></a><span data-ttu-id="a5067-108">32 位元與 64 位元</span><span class="sxs-lookup"><span data-stu-id="a5067-108">32-bit vs 64-bit</span></span>

<span data-ttu-id="a5067-109">HTTP 接收位置會使用 BTSHTTPReceive.dll。</span><span class="sxs-lookup"><span data-stu-id="a5067-109">An HTTP receive location uses the BTSHTTPReceive.dll.</span></span> <span data-ttu-id="a5067-110">沒有 32 位元和 64 位元版本的 dll。</span><span class="sxs-lookup"><span data-stu-id="a5067-110">There is a 32-bit and a 64-bit version of the DLL.</span></span> <span data-ttu-id="a5067-111">您選擇您想要使用哪一個的版本。</span><span class="sxs-lookup"><span data-stu-id="a5067-111">You choose which version you want to use.</span></span> <span data-ttu-id="a5067-112">64 位元處理序會有更多可用的記憶體，因此如果您處理較大的訊息，則可能最佳的 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="a5067-112">64-bit processes have more available memory, so if you process larger messages, then the 64-bit version may be best.</span></span> 

<span data-ttu-id="a5067-113">**32 位元的安裝位置**: *Program Files (x86) \Microsoft BizTalk Server\HttpReceive*。</span><span class="sxs-lookup"><span data-stu-id="a5067-113">**32-bit install location**: *Program Files (x86)\Microsoft BizTalk Server\HttpReceive*.</span></span>
<span data-ttu-id="a5067-114">**64 位元的安裝位置**: *Program Files (x86) \Microsoft BizTalk Server\HttpReceive64*</span><span class="sxs-lookup"><span data-stu-id="a5067-114">**64-bit install location**: *Program Files (x86)\Microsoft BizTalk Server\HttpReceive64*</span></span>

<span data-ttu-id="a5067-115">若要執行 64 位元版本的 HTTP 接收配接器在 64 位元原生模式中，開啟命令提示字元中，並執行下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="a5067-115">To run the 64-bit version of the HTTP receive adapter in 64-bit native mode,  open a command prompt, and execute the following scripts:</span></span>  

1. <span data-ttu-id="a5067-116">類型： `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`</span><span class="sxs-lookup"><span data-stu-id="a5067-116">Type: `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`</span></span>  

2. <span data-ttu-id="a5067-117">類型： `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`</span><span class="sxs-lookup"><span data-stu-id="a5067-117">Type: `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5067-118">任何導致 SOAP 與 HTTP 共用相同程序的 IIS 組態都無效。</span><span class="sxs-lookup"><span data-stu-id="a5067-118">Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid.</span></span> <span data-ttu-id="a5067-119">每個程序只能有一個隔離的接收器。</span><span class="sxs-lookup"><span data-stu-id="a5067-119">You can have only one isolated receiver per process.</span></span>  
  
##  <a name="configure-the-iis-application"></a><span data-ttu-id="a5067-120">設定 IIS 應用程式</span><span class="sxs-lookup"><span data-stu-id="a5067-120">Configure the IIS application</span></span>
  
1. <span data-ttu-id="a5067-121">開啟**Internet Information Services** (開啟**Server Manager**，選取**工具**，然後選取**Internet Information Services 管理員**).</span><span class="sxs-lookup"><span data-stu-id="a5067-121">Open **Internet Information Services** (open **Server Manager**, select **Tools**, and select **Internet Information Services Manager**).</span></span> 
  
2. <span data-ttu-id="a5067-122">在 IIS 中，選取您的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="a5067-122">In IIS, select your server name.</span></span> <span data-ttu-id="a5067-123">在 **功能檢視**，按兩下**處理常式對應**。</span><span class="sxs-lookup"><span data-stu-id="a5067-123">In the **Features View**, double-click **Handler Mappings**.</span></span> <span data-ttu-id="a5067-124">在 [動作] 窗格中，選取**新增指令碼對應**。</span><span class="sxs-lookup"><span data-stu-id="a5067-124">In the Actions pane, select **Add Script Map**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="a5067-125">當您在 web 伺服器層級設定指令碼對應時，對應所套用的所有網站。</span><span class="sxs-lookup"><span data-stu-id="a5067-125">When you configure the script mapping at the web server-level, the mapping applies to all web sites.</span></span> <span data-ttu-id="a5067-126">如果您想要限制對應至特定網站或虛擬資料夾，請選取該網站或資料夾，然後再加入 指令碼對應。</span><span class="sxs-lookup"><span data-stu-id="a5067-126">If you want to restrict the mapping to a specific Web site or virtual folder, select that web site or folder, and then add the script map.</span></span>  
  
3. <span data-ttu-id="a5067-127">在 **新增指令碼對應**，選取**要求路徑**，並輸入`BtsHttpReceive.dll`。</span><span class="sxs-lookup"><span data-stu-id="a5067-127">In **Add Script Map**, select **Request path**, and type `BtsHttpReceive.dll`.</span></span>  
  
4. <span data-ttu-id="a5067-128">在 **可執行檔**，選取省略符號 (**...**)，並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive。</span><span class="sxs-lookup"><span data-stu-id="a5067-128">In **Executable**, select the ellipsis (**…**), and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span></span> <span data-ttu-id="a5067-129">選取  **BtsHttpReceive.dll**，然後選取**開啟**。</span><span class="sxs-lookup"><span data-stu-id="a5067-129">Select **BtsHttpReceive.dll**, and then select **Open**.</span></span>  
  
5. <span data-ttu-id="a5067-130">在 **名稱**，輸入`BizTalk HTTP Receive`，然後選取**要求限制**。</span><span class="sxs-lookup"><span data-stu-id="a5067-130">In **Name**, enter `BizTalk HTTP Receive`, and then select **Request Restrictions**.</span></span> <span data-ttu-id="a5067-131">在此視窗中：</span><span class="sxs-lookup"><span data-stu-id="a5067-131">In this window:</span></span>
  
   1. <span data-ttu-id="a5067-132">在 **動詞**，選取**其中一個下列的指令動詞**，並輸入`POST`。</span><span class="sxs-lookup"><span data-stu-id="a5067-132">In **Verbs**, select **One of the following verbs**, and enter `POST`.</span></span>  
  
   2. <span data-ttu-id="a5067-133">在 **存取**，選取**指令碼**，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="a5067-133">In **Access**, select **Script**, and then select **OK**.</span></span>  
  
   3. <span data-ttu-id="a5067-134">當系統提示您允許 ISAPI 延伸模組，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="a5067-134">When prompted to allow the ISAPI extension, select **Yes**.</span></span>  
  
6. <span data-ttu-id="a5067-135">建立新的應用程式集區 (以滑鼠右鍵按一下**應用程式集區**，選取**新增應用程式集區**)。</span><span class="sxs-lookup"><span data-stu-id="a5067-135">Create a new application pool (right-click **Application Pools**, select **Add application pool**).</span></span> <span data-ttu-id="a5067-136">**名稱**應用程式集區 (例如`BTSHTTPReceive`)，選取**NET Framework v4.0.30319**，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="a5067-136">**Name** your application pool (such as `BTSHTTPReceive`), select **NET Framework v4.0.30319**, and select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a5067-137">.NET 版本號碼可能有所不同的電腦上安裝的.NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a5067-137">The .NET version number may vary depending on the version of .NET Framework installed on the computer.</span></span>  
  
     <span data-ttu-id="a5067-138">新的應用程式集區會列出。</span><span class="sxs-lookup"><span data-stu-id="a5067-138">The new application pool is listed.</span></span>  
  
7. <span data-ttu-id="a5067-139">選取新的應用程式集區，並開啟**進階設定** (**動作**窗格)。</span><span class="sxs-lookup"><span data-stu-id="a5067-139">Select your new application pool, and open the **Advanced Settings** (**Actions** pane).</span></span> <span data-ttu-id="a5067-140">在此視窗中：</span><span class="sxs-lookup"><span data-stu-id="a5067-140">In this window:</span></span>

    - <span data-ttu-id="a5067-141">**啟用 32 位元應用程式**： 設為 **，則為 True**如果您選擇 32 位元**BtsHttpReceive.dll**</span><span class="sxs-lookup"><span data-stu-id="a5067-141">**Enable 32-Bit Application**: Set to **True** if you chose the 32-bit **BtsHttpReceive.dll**</span></span>
    - <span data-ttu-id="a5067-142">**處理模型**區段中，**身分識別**： 選取省略符號 (**...**)，選取**自訂帳戶**，然後**設定**其成員的帳戶**BizTalk Isolated Host Users**和**IIS_WPG**群組。</span><span class="sxs-lookup"><span data-stu-id="a5067-142">**Process Model** section, **Identity**: Select the ellipsis (**…**), select **Custom account**, and then **Set** it to an account that is a member of the **BizTalk Isolated Host Users** and **IIS_WPG** groups.</span></span> <span data-ttu-id="a5067-143">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a5067-143">Select **OK**.</span></span> 
  
8. <span data-ttu-id="a5067-144">加入新的應用程式的網站 (以滑鼠右鍵按一下**Default Web Site**，選取**新增應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="a5067-144">Add a new application to the web site (right-click the **Default Web Site**, select **Add Application**).</span></span> <span data-ttu-id="a5067-145">在此視窗中：</span><span class="sxs-lookup"><span data-stu-id="a5067-145">In this window:</span></span>
  
   1. <span data-ttu-id="a5067-146">**別名**： 輸入您的應用程式相關聯的別名 (例如`BTS HTTP Receive`，然後**選取**。</span><span class="sxs-lookup"><span data-stu-id="a5067-146">**Alias** : Enter an alias that you associate with the application (such as `BTS HTTP Receive`, and then **Select**.</span></span>  
   2. <span data-ttu-id="a5067-147">選取您剛才新增的應用程式集區建立，然後再選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="a5067-147">Select the new application pool you just created, and then select **OK**.</span></span>  
   3. <span data-ttu-id="a5067-148">**實體路徑**： 選取省略符號 (**...**)，並瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive。</span><span class="sxs-lookup"><span data-stu-id="a5067-148">**Physical path**: Select the ellipsis (**…**), and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\HttpReceive.</span></span>  
   4. <span data-ttu-id="a5067-149">**測試設定**以確認沒有任何錯誤，在**測試連接** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a5067-149">**Test Settings** to verify there are no errors in the **Test Connection** dialog box.</span></span> <span data-ttu-id="a5067-150">**關閉**，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a5067-150">**Close**, and then select **OK**.</span></span>  
  
      > [!TIP]
      > <span data-ttu-id="a5067-151">如果測試設定會傳回一則警告，權限給資料夾或群組存取權，可能會遺失的應用程式集區身分識別。</span><span class="sxs-lookup"><span data-stu-id="a5067-151">If Test Settings returns a warning, the identity of the application pool may be missing permissions to a folder, or access to a group.</span></span> <span data-ttu-id="a5067-152">疑難排解的步驟中，選取**連接身分**，輸入**使用者名稱**並**密碼**是 Administrators 群組的成員使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a5067-152">As a troubleshooting step, select **Connect As**, enter the **User name** and **Password** for a user account that is a member of the Administrators group.</span></span> 

9. <span data-ttu-id="a5067-153">新的應用程式看起來就列在**預設的網站**。</span><span class="sxs-lookup"><span data-stu-id="a5067-153">The new application appears is listed under **Default Web Sites**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5067-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5067-154">See Also</span></span>  
 [<span data-ttu-id="a5067-155">如何設定 HTTP 接收位置</span><span class="sxs-lookup"><span data-stu-id="a5067-155">How to Configure an HTTP Receive Location</span></span>](../core/how-to-configure-an-http-receive-location.md)
