---
title: "如何設定 IIS，HTTP 接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 64-bit support, HTTP adapters
- HTTP adapters, IIS
- configuring [HTTP adapters], IIS
- receive locations, IIS
- IIS, receive locations
- HTTP adapters, 64-bit support
- IIS, HTTP adapters
ms.assetid: 1c420f46-01f1-4c9c-9144-d8d2acc8b0c4
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1daa535c546bef0b390f0f7f84c45d546ac0005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-iis-for-an-http-receive-location"></a><span data-ttu-id="3cf9c-102">如何設定 HTTP 接收位置的 IIS</span><span class="sxs-lookup"><span data-stu-id="3cf9c-102">How to Configure IIS for an HTTP Receive Location</span></span>
<span data-ttu-id="3cf9c-103">視您使用的 Microsoft Windows 版本而定，您必須以不同方式設定 Microsoft Internet Information Services (IIS) 來搭配使用 HTTP 配接器接收位置。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-103">Depending on which version of Microsoft Windows you are using, you will have to configure Microsoft Internet Information Services (IIS) differently to work with the HTTP adapter receive location.</span></span>  
  
 <span data-ttu-id="3cf9c-104">如果您的作業系統是[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，IIS 7.0 提供兩種不同的應用程式隔離模式來保護 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-104">If your operating system is [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], IIS 7.0 provides two different application isolation modes to protect Web applications.</span></span> <span data-ttu-id="3cf9c-105">背景工作處理序隔離模式是預設模式。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-105">Worker process isolation mode is the default mode.</span></span> <span data-ttu-id="3cf9c-106">您可以設定 HTTP 配接器接收位置使用任一種模式，但建議使用工作者處理序隔離模式，因為它具有改善的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-106">You can configure the HTTP adapter receive location to work with either mode, but worker process isolation mode is recommended for its improved security functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cf9c-107">如果您的作業系統是 x64 版本的[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]，64 位元版本的 HTTP 接收配接器安裝到*\<磁碟機 >***\Program Files (x86) \Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\HttpReceive64**目錄您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]預設。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-107">If your operating system is the x64 edition of [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], the 64-bit version of the HTTP receive adapter is installed to the *\<drive>***\Program Files (x86)\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**\HttpReceive64** directory of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by default.</span></span> <span data-ttu-id="3cf9c-108">若要在 64 位元原生模式中執行 64 位元版本的 HTTP 接收配接器，您必須從命令列執行下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="3cf9c-108">To run the 64-bit version of the HTTP receive adapter in 64-bit native mode you must execute the following script from a command line:</span></span>  
>   
>  `cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 0`  
>   
>  `C:\WINDOWS\Microsoft.NET\Framework64\vX.X.XXXXX>aspnet_regiis.exe -i`  
  
> [!NOTE]
>  <span data-ttu-id="3cf9c-109">任何導致 SOAP 與 HTTP 共用相同程序的 IIS 組態都無效。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-109">Any IIS configuration that leads to SOAP and HTTP sharing the same process is not valid.</span></span> <span data-ttu-id="3cf9c-110">每個程序只能有一個隔離的接收器。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-110">You can have only one isolated receiver per process.</span></span>  
  
### <a name="to-configure-the-iis-70-worker-process-isolation-mode-to-work-with-the-http-adapter-receive-location"></a><span data-ttu-id="3cf9c-111">若要設定 IIS 7.0 背景工作處理序隔離模式，才能使用 HTTP 配接器接收位置</span><span class="sxs-lookup"><span data-stu-id="3cf9c-111">To configure the IIS 7.0 worker process isolation mode to work with the HTTP adapter receive location</span></span>  
  
1.  <span data-ttu-id="3cf9c-112">按一下**啟動**，指向 **設定**，然後按一下 **控制台**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-112">Click **Start**, point to **Settings**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="3cf9c-113">在控制台中，按兩下**系統管理工具**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-113">In Control Panel, double-click **Administrative Tools**.</span></span>  
  
3.  <span data-ttu-id="3cf9c-114">在 [系統管理工具] 中按兩下**Internet Information Services**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-114">In Administrative Tools, double-click **Internet Information Services**.</span></span>  
  
4.  <span data-ttu-id="3cf9c-115">在 [Internet Information Services] 中，選取根 Web 伺服器項目。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-115">In Internet Information Services, select the root Web server entry.</span></span> <span data-ttu-id="3cf9c-116">在**功能檢視**，連按兩下**處理常式對應**，然後在 動作 窗格中，按一下 **新增指令碼對應**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-116">In the **Features View**, double-click **Handler Mappings**, and then in the Actions pane, click **Add Script Map**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3cf9c-117">在 Web 伺服器層級設定指令碼對應會使得此對應套用至所有子網站。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-117">Configuring the script mapping at the Web server level will cause this mapping to apply to all child Web sites.</span></span> <span data-ttu-id="3cf9c-118">若要限制對應至特定網站或虛擬資料夾，請選取目標網站或資料夾，而不要選取 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-118">If you want to restrict the mapping to a specific Web site or virtual folder, select the target site or folder instead of the Web server.</span></span>  
  
5.  <span data-ttu-id="3cf9c-119">在**新增指令碼對應**對話方塊中，於**要求路徑**欄位中，輸入`BtsHttpReceive.dll`。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-119">In the **Add Script Map** dialog box, in the **Request path** field, type `BtsHttpReceive.dll`.</span></span>  
  
6.  <span data-ttu-id="3cf9c-120">在**可執行檔**欄位中，按一下省略符號 (**...**) 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-120">In the **Executable** field, click the ellipsis (**…**) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive.</span></span> <span data-ttu-id="3cf9c-121">選取**BtsHttpReceive.dll** ，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-121">Select **BtsHttpReceive.dll** and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="3cf9c-122">在**名稱**欄位中，輸入`BizTalk HTTP Receive`，然後按一下 **要求限制**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-122">In the **Name** field, type `BizTalk HTTP Receive`, and then click **Request Restrictions**.</span></span>  
  
8.  <span data-ttu-id="3cf9c-123">在**要求限制**對話方塊中，按一下 **動詞**索引標籤，然後選取 **下列動詞命令的其中一個**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-123">In the **Request Restrictions** dialog box, click the **Verbs** tab and then select **One of the following verbs**.</span></span> <span data-ttu-id="3cf9c-124">輸入`POST`為動詞命令。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-124">Enter `POST` as the verb.</span></span>  
  
9. <span data-ttu-id="3cf9c-125">在**存取**索引標籤上，選取**指令碼**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-125">On the **Access** tab, select **Script**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="3cf9c-126">當畫面上出現允許 ISAPI 擴充程式的提示時，請按一下 [是]。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-126">When prompted to allow the ISAPI extension, click **Yes**.</span></span>  
  
11. <span data-ttu-id="3cf9c-127">以滑鼠右鍵按一下**應用程式集區**，指向 **新增**，然後按一下 **應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-127">Right-click **Application Pools**, point to **New**, and then click **Application pool**.</span></span>  
  
12. <span data-ttu-id="3cf9c-128">在**新增應用程式集區**對話方塊中，於**名稱**方塊中，輸入應用程式集區的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-128">In the **Add Application Pool** dialog box, in the **Name** box, type a name for the application pool.</span></span> <span data-ttu-id="3cf9c-129">選取**NET Framework v4.0.30319** ，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-129">Select **NET Framework v4.0.30319** and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3cf9c-130">版本號碼會根據電腦上安裝的.NET framework 版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-130">The version number may vary depending on the version of .NET Framework installed on the computer.</span></span>  
  
     <span data-ttu-id="3cf9c-131">新的應用程式集區會出現在清單中**應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-131">The new application pool appears in the list of **Application Pools**.</span></span>  
  
13. <span data-ttu-id="3cf9c-132">在**應用程式集區**，請在**功能檢視**選取新的應用程式集區，然後按一下 [**進階設定**動作] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-132">In **Application Pools**, in the **Features View**, select the new application pool, and then click **Advanced Settings** in the Actions pane.</span></span>  
  
14. <span data-ttu-id="3cf9c-133">在**進階設定**對話方塊中，於**處理序模型**區段的**識別**欄位中，按一下省略符號 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-133">In the **Advanced Settings** dialog box, in the **Process Model** section, in the **Identity** field, click the ellipsis (**…**) button.</span></span>  
  
15. <span data-ttu-id="3cf9c-134">在**應用程式集區識別**對話方塊中，選取**自訂帳戶**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-134">In the **Application Pool Identity** dialog box, select **Custom account**, and then click **Set**.</span></span> <span data-ttu-id="3cf9c-135">按一下 **[確定]** 以關閉 **[進階設定]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-135">Click **OK** to close the **Advanced Settings** dialog box.</span></span>  
  
16. <span data-ttu-id="3cf9c-136">在 [IIS 管理員] 中，開啟**網站**資料夾。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-136">In IIS Manager, open the **Sites** folder.</span></span> <span data-ttu-id="3cf9c-137">以滑鼠右鍵按一下**Default Web Site** ，然後按一下 **新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-137">Right-click the **Default Web Site** and then click **Add Application**.</span></span>  
  
17. <span data-ttu-id="3cf9c-138">在**新增應用程式**對話方塊中，於**別名**，輸入別名，應用程式時，產生關聯，然後按一下 **選取**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-138">In the **Add Application** dialog box, in **Alias**, enter an alias to associate with the application, and then click **Select**.</span></span>  
  
18. <span data-ttu-id="3cf9c-139">在**選取應用程式集區**對話方塊中，選取您稍早建立的新應用程式集區，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-139">In the **Select Application Pool** dialog box, select the new application pool you created earlier, and then click **OK**.</span></span>  
  
19. <span data-ttu-id="3cf9c-140">按一下省略符號 (**...**) 按鈕，然後瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive 的**實體路徑**。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-140">Click the ellipsis (**…**) button and browse to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive for the **Physical path**.</span></span>  
  
20. <span data-ttu-id="3cf9c-141">按一下**連接身分**並輸入**使用者名**和**密碼**使用者帳戶是 Administrators 群組的成員，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="3cf9c-141">Click **Connect As** and enter the **User name** and **Password** for a user account that is a member of the Administrators group, and then click **OK**.</span></span>  
  
21. <span data-ttu-id="3cf9c-142">按一下**測試設定**並確認沒有錯誤，會顯示在**測試連接** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-142">Click **Test Settings** and verify that no errors are displayed in the **Test Connection** dialog box.</span></span> <span data-ttu-id="3cf9c-143">按一下 [關閉]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-143">Click **Close**, and then click **OK**.</span></span>  
  
22. <span data-ttu-id="3cf9c-144">新的應用程式會出現在清單中**預設的網站**在網際網路資訊服務 (IIS) 管理員 中。</span><span class="sxs-lookup"><span data-stu-id="3cf9c-144">The new application appears in the list of **Default Web Sites** in Internet Information Services (IIS) Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf9c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cf9c-145">See Also</span></span>  
 [<span data-ttu-id="3cf9c-146">如何設定 HTTP 接收位置</span><span class="sxs-lookup"><span data-stu-id="3cf9c-146">How to Configure an HTTP Receive Location</span></span>](../core/how-to-configure-an-http-receive-location.md)