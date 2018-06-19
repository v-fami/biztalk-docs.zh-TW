---
title: Siebel 配接器搭配使用自訂 Web 組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a6c04-6523-483c-bdf4-ce0ac47cda87
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ad29a3ad28fcea81b00b6b2e2dabf51f0962e79
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963956"
---
# <a name="use-a-custom-web-part-with-the-siebel-adapter"></a><span data-ttu-id="cd4d7-102">Siebel 配接器搭配使用自訂 Web 組件</span><span class="sxs-lookup"><span data-stu-id="cd4d7-102">Use a Custom Web Part with the Siebel adapter</span></span>
<span data-ttu-id="cd4d7-103">本節提供與 Microsoft Office SharePoint Server 中使用自訂的 Web 組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-103">This section provides information about using a custom Web Part with Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="cd4d7-104">若要使用自訂的 Web 組件，您必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="cd4d7-104">To use a custom Web Part, you must do the following:</span></span>  
  
1.  <span data-ttu-id="cd4d7-105">建立自訂的 Web 組件</span><span class="sxs-lookup"><span data-stu-id="cd4d7-105">Create a custom Web Part</span></span>  
  
2.  <span data-ttu-id="cd4d7-106">將自訂 Web 組件部署到 SharePoint 入口網站</span><span class="sxs-lookup"><span data-stu-id="cd4d7-106">Deploy the custom Web Part to a SharePoint portal</span></span>  
  
3.  <span data-ttu-id="cd4d7-107">設定 SharePoint 入口網站使用自訂 Web 組件</span><span class="sxs-lookup"><span data-stu-id="cd4d7-107">Configure the SharePoint portal to use the custom Web Part</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="cd4d7-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="cd4d7-108">Before You Begin</span></span>  
 <span data-ttu-id="cd4d7-109">建立自訂的 Web 組件之前：</span><span class="sxs-lookup"><span data-stu-id="cd4d7-109">Before you create a custom Web Part:</span></span>  
  
-   <span data-ttu-id="cd4d7-110">將 Siebel 成品發佈為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-110">Publish the Siebel artifacts as a  WCF service.</span></span> <span data-ttu-id="cd4d7-111">如需詳細資訊，請參閱[步驟 1： 發佈為 WCF 服務的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md)中[教學課程 1： 呈現的資料從 Siebel 系統的 SharePoint 網站上](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-111">For more information, see [Step 1: Publish the Siebel Business Component Operations as a WCF Service](../../adapters-and-accelerators/adapter-siebel/step-1-publish-the-siebel-business-component-operations-as-a-wcf-service.md) in [Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).</span></span>  
  
-   <span data-ttu-id="cd4d7-112">建立 Microsoft Office SharePoint Server 中使用商務資料目錄的 Siebel 成品的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-112">Create an application definition file for the Siebel artifacts using the Business Data Catalog in Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="cd4d7-113">如需詳細資訊，請參閱[步驟 2： 建立應用程式定義檔的 Siebel 商務元件操作](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md)中[教學課程 1： 呈現的資料從 Siebel 系統的 SharePoint 網站上](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-113">For more information, see [Step 2: Create an Application Definition File for Siebel Business Component Operations](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md) in [Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).</span></span>  
  
##  <a name="Create_a_Custom_Web_Part"></a><span data-ttu-id="cd4d7-114">步驟 1： 建立自訂的 Web 組件</span><span class="sxs-lookup"><span data-stu-id="cd4d7-114">Step 1: Create a custom Web Part</span></span>  
 <span data-ttu-id="cd4d7-115">若要建立自訂的 Web 組件，使用 Visual Studio，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="cd4d7-115">To create a custom Web Part using Visual Studio, do the following:</span></span>  
  
1.  <span data-ttu-id="cd4d7-116">啟動 Visual Studio，並再建立專案。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-116">Start Visual Studio, and then create a project.</span></span>  
  
2.  <span data-ttu-id="cd4d7-117">在**新專案**對話方塊中，從**專案類型**窗格中，選取**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-117">In the **New Project** dialog box, from the **Project types** pane, select **Visual C#**.</span></span> <span data-ttu-id="cd4d7-118">從**範本**窗格中，選取**類別庫**。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-118">From the **Templates** pane, select **Class Library**.</span></span>  
  
3.  <span data-ttu-id="cd4d7-119">指定的名稱和位置的方案。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-119">Specify a name and location for the solution.</span></span> <span data-ttu-id="cd4d7-120">本主題中，指定`CustomWebPart`中**名稱**和**方案名稱**方塊。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-120">For this topic, specify `CustomWebPart` in the **Name** and **Solution Name** boxes.</span></span> <span data-ttu-id="cd4d7-121">指定的位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-121">Specify a location, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="cd4d7-122">將 System.Web 元件的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-122">Add a reference to the System.Web component into the project.</span></span> <span data-ttu-id="cd4d7-123">以滑鼠右鍵按一下專案名稱中的**方案總管] 中**，然後按一下 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-123">Right-click the project name in **Solution Explorer**, and then click **Add Reference**.</span></span> <span data-ttu-id="cd4d7-124">在**加入參考**對話方塊中，選取**System.Web**中 **.NET**索引標籤，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-124">In the **Add Reference** dialog box, select **System.Web** in the **.NET** tab, and then click **OK**.</span></span> <span data-ttu-id="cd4d7-125">System.Web 元件包含 System.Web.UI.WebControls.WebParts 必要的命名的空間。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-125">The System.Web component contains the required namespace of System.Web.UI.WebControls.WebParts.</span></span>  
  
5.  <span data-ttu-id="cd4d7-126">加入必要的程式碼，根據您在專案中的問題。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-126">Add the required code based on your issue in the project.</span></span> <span data-ttu-id="cd4d7-127">有關特定問題的程式碼範例，請參閱 「 問題涉及自訂 Web 組件 」，在[搭配 SharePoint 使用 Siebel 配接器時的考量](../../adapters-and-accelerators/adapter-siebel/considerations-when-using-the-siebel-adapter-with-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-127">For the code sample that is relevant to a certain issue, see “Issues Involving Custom Web Parts” in [Considerations when using the Siebel adapter with SharePoint](../../adapters-and-accelerators/adapter-siebel/considerations-when-using-the-siebel-adapter-with-sharepoint.md).</span></span>  
  
6.  <span data-ttu-id="cd4d7-128">建置專案。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-128">Build the project.</span></span> <span data-ttu-id="cd4d7-129">專案建置成功，將產生的.dll 檔案，CustomWebPart.dll，在\<*專案資料夾* \> /bin/Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-129">On successful build of the project, a .dll file, CustomWebPart.dll, will be generated in the \<*project folder*\>/bin/Debug folder.</span></span>  
  
## <a name="step-2-deploy-the-custom-web-part-to-a-sharepoint-portal"></a><span data-ttu-id="cd4d7-130">步驟 2： 將自訂 Web 組件部署到 SharePoint 入口網站</span><span class="sxs-lookup"><span data-stu-id="cd4d7-130">Step 2: Deploy the custom Web Part to a SharePoint Portal</span></span>  
 <span data-ttu-id="cd4d7-131">您必須執行下列命令來讓 CustomWebPart.dll 檔案 （自訂的 Web 組件） 中建立 「 步驟 1： 建立自訂的 Web 組件 」 的 SharePoint 入口網站上，您可以使用本主題：</span><span class="sxs-lookup"><span data-stu-id="cd4d7-131">You must do the following to make the CustomWebPart.dll file (custom Web Part) that is created in “Step 1: Create a custom Web Part” of this topic usable on the SharePoint portal:</span></span>  
  
-   <span data-ttu-id="cd4d7-132">**CustomWebPart.dll 檔案複製到 SharePoint 入口網站的 bin 資料夾**: Microsoft Office SharePoint Server 建立入口網站下的\<*根磁碟機*\>: \Inetpub\wwwroot\wss\VirtualDirectories 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-132">**Copy the CustomWebPart.dll file to the bin folder of the SharePoint Portal**: Microsoft Office SharePoint Server creates portals under the \<*root drive*\>:\Inetpub\wwwroot\wss\VirtualDirectories folder.</span></span> <span data-ttu-id="cd4d7-133">資料夾會針對每個入口網站中，建立，而且可以識別的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-133">A folder is created for each portal, and can be identified with the port number.</span></span> <span data-ttu-id="cd4d7-134">您必須複製 CustomWebPart.dll 檔案建立在 「 步驟 1： 建立自訂的 Web 組件 」 本主題的\<*根磁碟機*\>: \Inetpub\wwwroot\wss\VirtualDirectories\\ <*Port_Number*\>\bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-134">You must copy the CustomWebPart.dll file created in “Step 1: Create a custom Web Part” of this topic to the \<*root drive*\>:\Inetpub\wwwroot\wss\VirtualDirectories\\<*Port_Number*\>\bin folder.</span></span> <span data-ttu-id="cd4d7-135">例如，如果您的 SharePoint 入口網站的通訊埠編號是 13614，您必須複製 CustomWebPart.dll 檔案\<*根磁碟機*\>: \Inetpub\wwwroot\wss\VirtualDirectories\13614\bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-135">For example, if the port number of your SharePoint portal is 13614, you must copy the CustomWebPart.dll file to the \<*root drive*\>:\Inetpub\wwwroot\wss\VirtualDirectories\13614\bin folder.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="cd4d7-136">若要尋找您的 SharePoint 入口網站的資料夾位置的另一個方法是使用**網際網路資訊服務 (IIS) 管理員**視窗 (**啟動** > **執行** >  **inetmgr**)。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-136">Another way to find the folder location of your SharePoint portal is by using the **Internet Information Services (IIS) Manager** window (**Start** > **Run** > **inetmgr**).</span></span> <span data-ttu-id="cd4d7-137">找出您的 SharePoint 入口網站中**網際網路資訊服務 (IIS) 管理員**視窗 ([*computer_name*] > 網站 > [*入口網站名稱*])，以滑鼠右鍵按一下，並然後按一下 **屬性**快顯功能表中。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-137">Locate your SharePoint portal in the **Internet Information Services (IIS) Manager** window ([*computer_name*] > Web Sites > [*Portal-Name*]), right-click, and then click **Properties** in the shortcut menu.</span></span> <span data-ttu-id="cd4d7-138">在 屬性 對話方塊中的 SharePoint 入口網站，按一下 **主目錄**索引標籤，然後選取**本機路徑**方塊。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-138">In the properties dialog box of the SharePoint portal, click the **Home Directory** tab, and then select the **Local path** box.</span></span>  
  
-   <span data-ttu-id="cd4d7-139">**在 web.config 檔案中加入安全控制項項目**： 因為 CustomWebPart.dll 檔案將用於不同的電腦上並由多個使用者，您必須宣告為 「 安全 」。 檔案</span><span class="sxs-lookup"><span data-stu-id="cd4d7-139">**Add the Safe Control Entry in the web.config File**: Because the CustomWebPart.dll file will be used on different computers and by multiple users, you must declare the file as “safe.”</span></span> <span data-ttu-id="cd4d7-140">若要這樣做，開啟 web.config 檔案位於位於入口網站的 SharePoint 資料夾\<*根磁碟機*\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< Port_Number\>。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-140">To do so, open the web.config file located in the SharePoint portal folder at \<*root drive*\>:\Inetpub\wwwroot\wss\VirtualDirectories\\<Port_Number\>.</span></span> <span data-ttu-id="cd4d7-141">在下`<SafeControls>`> 一節的 web.config 檔案中，加入下列安全控制項項目：</span><span class="sxs-lookup"><span data-stu-id="cd4d7-141">Under the `<SafeControls>` section of the web.config file, add the following safe control entry:</span></span>  
  
    ```  
    <SafeControl Assembly="CustomWebPart" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
    ```  
  
     <span data-ttu-id="cd4d7-142">儲存 web.config 檔案中，，然後關閉它。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-142">Save the web.config file, and then close it.</span></span>  
  
## <a name="step-3-configure-the-sharepoint-portal-to-use-the-custom-web-part"></a><span data-ttu-id="cd4d7-143">步驟 3： 設定 SharePoint 入口網站使用自訂 Web 組件</span><span class="sxs-lookup"><span data-stu-id="cd4d7-143">Step 3: Configure the SharePoint Portal to use the custom Web Part</span></span>  
 <span data-ttu-id="cd4d7-144">您需要將自訂 Web 組件新增至 Microsoft Office SharePoint Server Web 組件庫，以便您可以使用它在您的 SharePoint 入口網站上。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-144">You need to add the custom Web Part to the Microsoft Office SharePoint Server Web Part Gallery, so that you can use it on your SharePoint portal.</span></span> <span data-ttu-id="cd4d7-145">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="cd4d7-145">To do so:</span></span>  
  
1.  <span data-ttu-id="cd4d7-146">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-146">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="cd4d7-147">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-147">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="cd4d7-148">在左側瀏覽窗格中，按一下 共用服務提供者 (SSP) 的您要加入自訂 Web 組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-148">In the left navigation pane, click the name of the Shared Services Provider (SSP) to which you want to add the custom Web Part.</span></span>  
  
3.  <span data-ttu-id="cd4d7-149">在**共用服務管理**頁面上，在右上角，按一下**網站動作**，然後按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-149">On the **Shared Services Administration** page, in the upper-right corner, click **Site Actions**, and then click **Create**.</span></span>  
  
4.  <span data-ttu-id="cd4d7-150">在**站台設定**頁面上，按一下**Web 組件**下**圖庫**資料行。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-150">On the **Site Settings** page, click **Web Parts** under the **Galleries** column.</span></span>  
  
5.  <span data-ttu-id="cd4d7-151">在**網頁組件庫**頁面上，將自訂 Web 組件新增至組件庫中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-151">On the **Web Part Gallery** page, to add the custom Web Part to the gallery,  click **New**.</span></span> <span data-ttu-id="cd4d7-152">此時不提供自訂的 Web 組件**網頁組件庫**頁面。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-152">At this point the custom Web Part is not available in the **Web Part Gallery** page.</span></span>  
  
6.  <span data-ttu-id="cd4d7-153">在**新的 Web 組件**頁面上，尋找**CustomWebPart** （自訂的 Web 組件的名稱） 在清單中，選取左邊的核取方塊，然後按一下 **擴展組件庫**頂端頁面。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-153">On the **New Web Parts** page, locate **CustomWebPart** (name of the custom Web Part) in the list, select the check box on the left, and then click **Populate Gallery** on the top of the page.</span></span> <span data-ttu-id="cd4d7-154">這會新增**CustomWebPart**中的項目**網頁組件庫**頁面。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-154">This will add the **CustomWebPart** entry in the **Web Part Gallery** page.</span></span>  
  
 <span data-ttu-id="cd4d7-155">現在您可以使用自訂 Web 組件 (**CustomWebPart**) 在您的 SharePoint 入口網站中建立 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-155">Now you can use the custom Web Part (**CustomWebPart**) to create Web Parts in your SharePoint portal.</span></span> <span data-ttu-id="cd4d7-156">自訂的 Web 組件 (**CustomWebPart**) 會出現在**其他**一節中**新增網頁組件**頁面。</span><span class="sxs-lookup"><span data-stu-id="cd4d7-156">The custom Web Part (**CustomWebPart**) will appear under the **Miscellaneous** section in the **Add Web Parts** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd4d7-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd4d7-157">See Also</span></span>  
 [<span data-ttu-id="cd4d7-158">搭配使用 SharePoint 與 Siebel 配接器</span><span class="sxs-lookup"><span data-stu-id="cd4d7-158">Use the Siebel Adapter with SharePoint</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)