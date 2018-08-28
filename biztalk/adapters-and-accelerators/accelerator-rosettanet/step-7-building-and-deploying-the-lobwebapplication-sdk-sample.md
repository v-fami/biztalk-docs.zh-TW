---
title: 步驟 7： 建置與部署 LOBWebApplication SDK 範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, building solutions
- double action tutorial, deploying solutions
ms.assetid: f61de666-ebda-4831-9669-598e9284e4c1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a0716c854c20f5ea7fa7d2ad91576cb142f6a02
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996183"
---
# <a name="step-7-building-and-deploying-the-lobwebapplication-sdk-sample"></a><span data-ttu-id="92387-102">步驟 7： 建置與部署 LOBWebApplication SDK 範例</span><span class="sxs-lookup"><span data-stu-id="92387-102">Step 7: Building and Deploying the LOBWebApplication SDK Sample</span></span>
<span data-ttu-id="92387-103">在此步驟中，您將建立 Fabrikam 用來提交夥伴介面程序 (PIP) 要求到 Contoso 的商務營運系統 (LOB) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="92387-103">In this step, you create the line-of-business (LOB) application that Fabrikam uses to submit Partner Interface Process (PIP) requests to Contoso.</span></span> <span data-ttu-id="92387-104">您可以找到 LOBWebApplication 專案中 Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 資料夾。</span><span class="sxs-lookup"><span data-stu-id="92387-104">You can find the LOBWebApplication project in the Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK folder.</span></span> <span data-ttu-id="92387-105">若要執行的 Web 應用程式，您必須建立 Microsoft Internet Information Services (IIS) 虛擬目錄，然後建置 LOBWebApplication 專案。</span><span class="sxs-lookup"><span data-stu-id="92387-105">To run the Web application, you have to create a Microsoft Internet Information Services (IIS) virtual directory, and then build the LOBWebApplication project.</span></span>  
  
### <a name="to-create-the-lobwebapplication-virtual-directory"></a><span data-ttu-id="92387-106">建立 LOBWebApplication 虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="92387-106">To create the LOBWebApplication virtual directory</span></span>  
  
1.  <span data-ttu-id="92387-107">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="92387-107">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="92387-108">在 [Internet Information Services 管理員] 視窗中，依序展開 **< 電腦名稱 > （本機電腦）**，然後展開**網站**。</span><span class="sxs-lookup"><span data-stu-id="92387-108">In the Internet Information Services Manager window, expand **<computer_name> (local computer)**, and then expand **Web Sites**.</span></span>  
  
3.  <span data-ttu-id="92387-109">以滑鼠右鍵按一下**Default Web Site**，指向**新增**，然後按一下**虛擬目錄**。</span><span class="sxs-lookup"><span data-stu-id="92387-109">Right-click **Default Web Site**, point to **New**, and then click **Virtual Directory**.</span></span>  
  
4.  <span data-ttu-id="92387-110">在 [ **Welcometo 虛擬目錄建立精靈**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="92387-110">On the **Welcometo the Virtual Directory Creation Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="92387-111">在 [**虛擬目錄別名**頁面上，於**別名**方塊中，輸入**LOBWebApplication**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="92387-111">On the **Virtual Directory Alias** page, in the **Alias** box, type **LOBWebApplication**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="92387-112">在 **網站內容目錄**頁面上，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="92387-112">On the **Web Site Content Directory** page, click **Browse**.</span></span> <span data-ttu-id="92387-113">在 瀏覽資料夾 對話方塊中，移至 ***\<磁碟機\>*:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBWebApplication**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="92387-113">In the Browse For Folder dialog box, move to ***\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication**, and then click **OK**.</span></span> <span data-ttu-id="92387-114">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="92387-114">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="92387-115">在上**虛擬目錄的存取權限**頁面上，取消選取**讀取**，選取**執行指令碼 （例如 ASP)**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="92387-115">On the **Virtual Directory Access Permissions** page, deselect **Read**, select **Run scripts (such as ASP)**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="92387-116">在 **您已成功完成虛擬目錄建立精靈**頁面上，按一下**完成**建立虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="92387-116">On the **You have successfully completed the Virtual Directory Creation Wizard** page, click **Finish** to create the virtual directory.</span></span>  
  
### <a name="to-exclude-the-lobwebapplication-web-site-from-the-sharepoint-configuration"></a><span data-ttu-id="92387-117">從 SharePoint 組態排除 LOBWebApplication 網站</span><span class="sxs-lookup"><span data-stu-id="92387-117">To exclude the LOBWebApplication Web site from the SharePoint configuration</span></span>  
  
1.  <span data-ttu-id="92387-118">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**SharePoint 管理中心**。</span><span class="sxs-lookup"><span data-stu-id="92387-118">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
2.  <span data-ttu-id="92387-119">在 **管理中心**網頁上**虛擬伺服器組態**區段中，選取**擴充或升級虛擬伺服器**。</span><span class="sxs-lookup"><span data-stu-id="92387-119">On the **Central Administration** Web page, in the **Virtual Server Configuration** section, select **Extend or upgrade virtual server**.</span></span>  
  
3.  <span data-ttu-id="92387-120">如果看不到電腦上設定的 URL，請按一下**完整清單**。</span><span class="sxs-lookup"><span data-stu-id="92387-120">If you do not see the URL configured on the computer, click **Complete list**.</span></span>  
  
4.  <span data-ttu-id="92387-121">在 **虛擬伺服器清單**頁面上，選取**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="92387-121">On the **Virtual Server List** page, select **Default Web Site**.</span></span>  
  
5.  <span data-ttu-id="92387-122">在 **虛擬伺服器管理**區段中，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="92387-122">In the **Virtual Server Management** section, click **Define managed paths**.</span></span>  
  
6.  <span data-ttu-id="92387-123">在 **加入新的路徑**區段中**路徑**方塊中，輸入 **/LOBWebApplication**。</span><span class="sxs-lookup"><span data-stu-id="92387-123">In the **Add New Path** section, in the **Path** box, type **/LOBWebApplication**.</span></span>  
  
7.  <span data-ttu-id="92387-124">針對**型別**，選取**排除的路徑**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="92387-124">For **Type**, select **Excluded Path**, and then click **OK**.</span></span>  
  
### <a name="to-build-the-lobwebapplication-project"></a><span data-ttu-id="92387-125">建置 LOBWebApplication 專案</span><span class="sxs-lookup"><span data-stu-id="92387-125">To build the LOBWebApplication project</span></span>  
  
1.  <span data-ttu-id="92387-126">按一下 **開始**，指向**所有程式**，指向**Microsoft Visual Studio 2008**，然後按一下**Microsoft Visual Studio 2008**。</span><span class="sxs-lookup"><span data-stu-id="92387-126">Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2008**, and then click **Microsoft Visual Studio 2008**.</span></span>  
  
2.  <span data-ttu-id="92387-127">在 [檔案] 功能表上，指向 [開啟舊檔]，再按一下 [專案/方案]。</span><span class="sxs-lookup"><span data-stu-id="92387-127">On the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="92387-128">在 [開啟專案] 對話方塊中，移至 ***\<磁碟機\>*:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBWebApplication**，選取**LOBWebApplication.sln**解決方案檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="92387-128">In the Open Project dialog box, move to ***\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication**, select the **LOBWebApplication.sln** solution file, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="92387-129">在 [方案總管] 中，以滑鼠右鍵按一下**http://localhost/LOBWebApplication**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="92387-129">In Solution Explorer, right-click **http://localhost/LOBWebApplication**, and then click **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="92387-130">在 [加入參考] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="92387-130">In the Add Reference dialog box, click **Browse**.</span></span> <span data-ttu-id="92387-131">在 [加入參考] 對話方塊中，移至 ***\<磁碟機\>*:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\Bin**資料夾。</span><span class="sxs-lookup"><span data-stu-id="92387-131">In the Add Reference dialog box, move to ***\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin** folder.</span></span>  
  
6.  <span data-ttu-id="92387-132">從 [Bin] 資料夾中，選取**Microsoft.Solutions.BTARN.ConfigurationManager.dll**並**Microsoft.Solutions.BTARN.Shared.dll**組件，然後再按一下**開啟。**</span><span class="sxs-lookup"><span data-stu-id="92387-132">From the Bin folder, select the **Microsoft.Solutions.BTARN.ConfigurationManager.dll** and **Microsoft.Solutions.BTARN.Shared.dll** assemblies, and then click **Open.**</span></span>  
  
7.  <span data-ttu-id="92387-133">按一下 [ **[確定]** 以關閉**加入參考**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="92387-133">Click **OK** to close the **Add Reference** dialog box.</span></span>  
  
8.  <span data-ttu-id="92387-134">在 [方案總管] 中，以滑鼠右鍵按一下**解決方案 'LOBWebApplication'** ，然後按一下**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="92387-134">In Solution Explorer, right-click **Solution 'LOBWebApplication'** and then click **Build Solution**.</span></span>  
  
9. <span data-ttu-id="92387-135">以滑鼠右鍵按一下**default.aspx**，然後按一下**設定為起始頁**。</span><span class="sxs-lookup"><span data-stu-id="92387-135">Right-click **default.aspx**, and then click **Set as Start Page**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92387-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92387-136">See Also</span></span>  
 [<span data-ttu-id="92387-137">測試雙向動作教學課程</span><span class="sxs-lookup"><span data-stu-id="92387-137">Testing the Double Action Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-double-action-tutorial.md)