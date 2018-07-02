---
title: 步驟 2： 建立 Fabrikam LOBWebApplication |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOBWebApplication
- LOBWebApplication
ms.assetid: 2ff8bd20-7fbc-4e16-b177-bb4afac7f7c3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c55234d8ee9c123c9efe9e7ec66b7c0db590b54
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966623"
---
# <a name="step-2-creating-the-fabrikam-lobwebapplication"></a><span data-ttu-id="fb76c-102">步驟 2： 建立 Fabrikam LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="fb76c-102">Step 2: Creating the Fabrikam LOBWebApplication</span></span>
<span data-ttu-id="fb76c-103">在此步驟中，您將建立 LOB 應用程式，讓 Fabrikam 用來提交 3A2 PIP 要求至 Contoso。</span><span class="sxs-lookup"><span data-stu-id="fb76c-103">In this step, you create the LOB application that Fabrikam uses to submit a 3A2 PIP request to Contoso.</span></span> <span data-ttu-id="fb76c-104">LOBWebApplication 專案是安裝在 [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 中。</span><span class="sxs-lookup"><span data-stu-id="fb76c-104">The LOBWebApplication project is installed in the [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK.</span></span> <span data-ttu-id="fb76c-105">若要執行的 Web 應用程式，您必須建立 Microsoft Internet Information Services (IIS) 虛擬目錄，並建置 LOBWebApplication 專案。</span><span class="sxs-lookup"><span data-stu-id="fb76c-105">To run the Web application, you have to create a Microsoft Internet Information Services (IIS) virtual directory and build the LOBWebApplication project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb76c-106">如果您已完成「雙向動作」教學課程，則不必執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="fb76c-106">If you completed the DoubleAction tutorial, you do not need to perform this step.</span></span>  
  
### <a name="to-create-the-lobwebapplication-virtual-directory"></a><span data-ttu-id="fb76c-107">建立 LOBWebApplication 虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="fb76c-107">To create the LOBWebApplication virtual directory</span></span>  
  
1.  <span data-ttu-id="fb76c-108">按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services 管理員**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-108">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services Manager**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb76c-109">如果您已完成「雙向動作」教學課程，便已經在該教學課程中建立 LOBWebApplication 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fb76c-109">If you have already done the Double Action tutorial, you will already have created the LOBWebApplication virtual directory for that tutorial.</span></span> <span data-ttu-id="fb76c-110">若是如此，您就不必執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="fb76c-110">If so, you do not have to perform these steps.</span></span> <span data-ttu-id="fb76c-111">您將此項目，不過，必須變更的虛擬目錄的權限**執行指令碼**要**讀取**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-111">You will, however, have to change the permissions for the virtual directory from **Run scripts** to **Read**.</span></span>  
  
2.  <span data-ttu-id="fb76c-112">在 [Internet Information Services 管理員] 中展開 **< 電腦名稱 > （本機電腦）**，然後展開**網站**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-112">In Internet Information Services Manager, expand **<computer_name> (local computer)**, and then expand **Web Sites**.</span></span>  
  
3.  <span data-ttu-id="fb76c-113">以滑鼠右鍵按一下**Default Web Site**，指向**新增**，然後按一下**虛擬目錄**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-113">Right-click **Default Web Site**, point to **New**, and then click **Virtual Directory**.</span></span>  
  
4.  <span data-ttu-id="fb76c-114">在 [ **Welcometo 虛擬目錄建立精靈頁面**，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-114">On the **Welcometo the Virtual Directory Creation Wizard page**, click **Next**.</span></span>  
  
5.  <span data-ttu-id="fb76c-115">在 [**虛擬目錄別名**頁面上，於**別名**方塊中，輸入**LOBWebApplication**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-115">On the **Virtual Directory Alias** page, in the **Alias** box, type **LOBWebApplication**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="fb76c-116">在 **網站內容目錄**頁面上，按一下**瀏覽**，選取**\<磁碟機\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBWebApplication**資料夾，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-116">On the **Web Site Content Directory** page, click **Browse**, select the **\<drive\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBWebApplication** folder, and then click **OK**.</span></span> <span data-ttu-id="fb76c-117">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fb76c-117">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="fb76c-118">在 [**虛擬目錄的存取權限**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-118">On the **Virtual Directory Access Permissions** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="fb76c-119">按一下 **完成**建立虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fb76c-119">Click **Finish** to create the virtual directory.</span></span>  
  
### <a name="excluding-lobwebapplication-from-sharepoint"></a><span data-ttu-id="fb76c-120">從 SharePoint 排除 LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="fb76c-120">Excluding LOBWebApplication from SharePoint</span></span>  
  
1.  <span data-ttu-id="fb76c-121">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**SharePoint 管理中心**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-121">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb76c-122">如果您已完成「雙向動作」教學課程，便已經在該教學課程中從 SharePoint 排除 LOBWebApplication 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fb76c-122">If you have already done the Double Action tutorial, you will already have excluded the LOBWebApplication virtual directory from SharePoint for that tutorial.</span></span> <span data-ttu-id="fb76c-123">若是如此，您就不必執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="fb76c-123">If so, you do not have to perform these steps.</span></span>  
  
2.  <span data-ttu-id="fb76c-124">在 **管理中心**頁面上，於**虛擬伺服器組態**區段中，選取**擴充或升級虛擬伺服器**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-124">On the **Central Administration** page, in the **Virtual Server Configuration** section, select **Extend or upgrade virtual server**.</span></span>  
  
3.  <span data-ttu-id="fb76c-125">如果看不到電腦上設定的 URL，請按一下**完整清單**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-125">If you do not see the URL configured on the computer, click **Complete list**.</span></span>  
  
4.  <span data-ttu-id="fb76c-126">選取  **Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-126">Select **Default Web Site**.</span></span>  
  
5.  <span data-ttu-id="fb76c-127">在 **虛擬伺服器管理**區段中，按一下**定義管理的路徑**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-127">In the **Virtual Server Management** section, click **Define managed paths**.</span></span>  
  
6.  <span data-ttu-id="fb76c-128">在 **新增路徑**區段中**路徑**方塊中，輸入"/ LOBWebApplication"。</span><span class="sxs-lookup"><span data-stu-id="fb76c-128">In the **Add New Path** section, in the **Path** box, type "/LOBWebApplication".</span></span> <span data-ttu-id="fb76c-129">針對**型別**，選取**排除的路徑**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-129">For **Type**, select **Excluded Path**, and then click **OK**.</span></span>  
  
### <a name="to-build-the-lobwebapplication-project"></a><span data-ttu-id="fb76c-130">建置 LOBWebApplication 專案</span><span class="sxs-lookup"><span data-stu-id="fb76c-130">To build the LOBWebApplication project</span></span>  
  
1.  <span data-ttu-id="fb76c-131">開始**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-131">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="fb76c-132">從**檔案**功能表上，指向**開放**，然後按一下**專案 \ 方案**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-132">From the **File** menu, point to **Open**, and then click **Project\Solution**.</span></span>  
  
3.  <span data-ttu-id="fb76c-133">在開啟專案 對話方塊中，在**查詢**，移至**\<磁碟機\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\ SDK\<SDKLOBWebApplication**，選取**LOBWebApplication.sln**解決方案，，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-133">In the Open Project dialog box, in **Look In**, move to **\<drive\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\ SDK\LOBWebApplication**, select the **LOBWebApplication.sln** solution, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="fb76c-134">在 [方案總管] 中，以滑鼠右鍵按一下最上層節點 (http://localhost/LOBWebApplication)，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-134">In Solution Explorer, right-click the top node (http://localhost/LOBWebApplication), and then click **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="fb76c-135">在 [加入參考] 對話方塊中，按一下**瀏覽**並移至**\<磁碟機\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\bin**.</span><span class="sxs-lookup"><span data-stu-id="fb76c-135">In the Add Reference dialog box, click **Browse** and move to **\<drive\>:\Program Files\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\bin**.</span></span>  
  
6.  <span data-ttu-id="fb76c-136">**選取 Microsoft.Solutions.BTARN.ConfigurationManager.dll 和 Microsoft.Solutions.BTARN.Shared.dll**組件**然後按一下 [確定]。**</span><span class="sxs-lookup"><span data-stu-id="fb76c-136">**Select the Microsoft.Solutions.BTARN.ConfigurationManager.dll and Microsoft.Solutions.BTARN.Shared.dll** assemblies **and then click OK.**</span></span>  
  
7.  <span data-ttu-id="fb76c-137">在 **建置**功能表上，按一下**建置網站**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-137">On the **Build** menu, click **Build Web Site**.</span></span>  
  
### <a name="to-run-the-lobwebapplication-project"></a><span data-ttu-id="fb76c-138">執行 LOBWebApplication 專案</span><span class="sxs-lookup"><span data-stu-id="fb76c-138">To run the LOBWebApplication project</span></span>  
  
1.  <span data-ttu-id="fb76c-139">在 [方案總管] 中，以滑鼠右鍵按一下**default.aspx**，然後選取**設定為起始頁**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-139">In Solution Explorer, right-click **default.aspx**, and then select **Set As Start Page**.</span></span>  
  
2.  <span data-ttu-id="fb76c-140">在 **偵錯**功能表上，按一下**啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="fb76c-140">On the **Debug** menu, click **Start Without Debugging**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb76c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb76c-141">See Also</span></span>  
 [<span data-ttu-id="fb76c-142">測試解決方案</span><span class="sxs-lookup"><span data-stu-id="fb76c-142">Testing the Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-solution.md)