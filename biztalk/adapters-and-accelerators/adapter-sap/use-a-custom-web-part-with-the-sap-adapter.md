---
title: SAP 配接器搭配使用自訂 Web 組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b7fecd2-a385-4b2d-a01b-3bfd65ecff3a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dce6bef0cecf847d10bee1897f417e63922659e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980031"
---
# <a name="use-a-custom-web-part-with-the-sap-adapter"></a><span data-ttu-id="d5e2c-102">SAP 配接器搭配使用自訂 Web 組件</span><span class="sxs-lookup"><span data-stu-id="d5e2c-102">Use a Custom Web Part with the SAP adapter</span></span>
<span data-ttu-id="d5e2c-103">本節提供使用 Microsoft Office SharePoint Server 中使用自訂的 Web 組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-103">This section provides information about using a custom Web Part with Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="d5e2c-104">若要使用自訂的 Web 組件，您必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d5e2c-104">To use a custom Web Part, you must do the following:</span></span>  
  
1.  <span data-ttu-id="d5e2c-105">建立自訂的 Web 組件</span><span class="sxs-lookup"><span data-stu-id="d5e2c-105">Create a custom Web Part</span></span>  
  
2.  <span data-ttu-id="d5e2c-106">將自訂的 Web 組件部署到 SharePoint 入口網站</span><span class="sxs-lookup"><span data-stu-id="d5e2c-106">Deploy the custom Web Part to a SharePoint portal</span></span>  
  
3.  <span data-ttu-id="d5e2c-107">設定 SharePoint 入口網站使用自訂的 Web 組件</span><span class="sxs-lookup"><span data-stu-id="d5e2c-107">Configure the SharePoint portal to use the custom Web Part</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="d5e2c-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="d5e2c-108">Before You Begin</span></span>  
 <span data-ttu-id="d5e2c-109">建立自訂的 Web 組件之前：</span><span class="sxs-lookup"><span data-stu-id="d5e2c-109">Before you create a custom Web Part:</span></span>  
  
-   <span data-ttu-id="d5e2c-110">將 SAP 成品發佈為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-110">Publish the SAP artifacts as a  WCF service.</span></span> <span data-ttu-id="d5e2c-111">如需詳細資訊，請參閱 <<c0> [ 步驟 1： 將 SAP 成品，做為 WCF 服務發佈](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md)中[教學課程 1： 將資料呈現在 SharePoint 網站上的 SAP 系統從](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-111">For more information, see [Step 1: Publish the SAP Artifacts as a WCF Service](../../adapters-and-accelerators/adapter-sap/step-1-publish-the-sap-artifacts-as-a-wcf-service.md) in [Tutorial 1: Presenting Data from an SAP System on a SharePoint Site](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md).</span></span>  
  
-   <span data-ttu-id="d5e2c-112">建立 Microsoft Office SharePoint Server 中使用商務資料目錄將 SAP 成品的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-112">Create an application definition file for the SAP artifacts using the Business Data Catalog in Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="d5e2c-113">如需詳細資訊，請參閱[步驟 2： 建立 SAP 成品的應用程式定義檔](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md)中[教學課程 1： 將資料呈現在 SharePoint 網站上的 SAP 系統從](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-113">For more information, see [Step 2: Create an Application Definition File for the SAP Artifacts](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md) in [Tutorial 1: Presenting Data from an SAP System on a SharePoint Site](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md).</span></span>  
  
##  <a name="Create_a_Custom_Web_Part"></a> <span data-ttu-id="d5e2c-114">步驟 1： 建立自訂的 Web 組件</span><span class="sxs-lookup"><span data-stu-id="d5e2c-114">Step 1: Create a custom Web Part</span></span>  
 <span data-ttu-id="d5e2c-115">若要建立自訂的 Web 組件，使用 Visual Studio，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="d5e2c-115">To create a custom Web Part using Visual Studio, do the following:</span></span>  
  
1.  <span data-ttu-id="d5e2c-116">啟動 Visual Studio，並再建立專案。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-116">Start Visual Studio, and then create a project.</span></span>  
  
2.  <span data-ttu-id="d5e2c-117">在 [**新的專案**] 對話方塊中，從**專案類型**窗格中，選取**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-117">In the **New Project** dialog box, from the **Project types** pane, select **Visual C#**.</span></span> <span data-ttu-id="d5e2c-118">從**範本**窗格中，選取**類別庫**。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-118">From the **Templates** pane, select **Class Library**.</span></span>  
  
3.  <span data-ttu-id="d5e2c-119">指定的名稱和解決方案的位置。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-119">Specify a name and location for the solution.</span></span> <span data-ttu-id="d5e2c-120">本主題中，指定`CustomWebPart`中**名稱**並**方案名稱**方塊。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-120">For this topic, specify `CustomWebPart` in the **Name** and **Solution Name** boxes.</span></span> <span data-ttu-id="d5e2c-121">指定的位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-121">Specify a location, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="d5e2c-122">專案中加入 System.Web 元件的參考。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-122">Add a reference to the System.Web component into the project.</span></span> <span data-ttu-id="d5e2c-123">中的專案名稱上按一下滑鼠右鍵**方案總管**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-123">Right-click the project name in **Solution Explorer**, and then click **Add Reference**.</span></span> <span data-ttu-id="d5e2c-124">在 **加入參考**對話方塊中，選取**System.Web**中 **.NET**索引標籤，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-124">In the **Add Reference** dialog box, select **System.Web** in the **.NET** tab, and then click **OK**.</span></span> <span data-ttu-id="d5e2c-125">System.Web 元件包含必要的命名空間的 System.Web.UI.WebControls.WebParts。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-125">The System.Web component contains the required namespace of System.Web.UI.WebControls.WebParts.</span></span>  
  
5.  <span data-ttu-id="d5e2c-126">新增必要的程式碼，根據您專案中的問題。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-126">Add the required code based on your issue in the project.</span></span> <span data-ttu-id="d5e2c-127">相關的特定問題的程式碼範例，請參閱 「 問題涉及自訂 Web 組件 」，在[使用 SharePoint 與 SAP 配接器的考量](../../adapters-and-accelerators/adapter-sap/considerations-when-using-the-sap-adapter-with-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-127">For the code sample that is relevant to a certain issue, see “Issues Involving Custom Web Parts” in [Considerations when using the SAP adapter with SharePoint](../../adapters-and-accelerators/adapter-sap/considerations-when-using-the-sap-adapter-with-sharepoint.md).</span></span>  
  
6.  <span data-ttu-id="d5e2c-128">建置專案。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-128">Build the project.</span></span> <span data-ttu-id="d5e2c-129">專案建置成功，將產生的.dll 檔案，CustomWebPart.dll，在\<專案資料夾 \> /bin/Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-129">On successful build of the project, a .dll file, CustomWebPart.dll, will be generated in the \<project folder\>/bin/Debug folder.</span></span>  
  
7.  <span data-ttu-id="d5e2c-130">**僅針對 64 位元電腦**： 簽署 CustomWebPart.dll 檔案以強式名稱，才能執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-130">**Only for 64-bit computer**: Sign the CustomWebPart.dll file with a strong name before performing the following steps.</span></span> <span data-ttu-id="d5e2c-131">否則，您將無法匯入，並因此使用中的 SharePoint 入口網站中的 CustomWebPart.dll 「 步驟 3： 設定 SharePoint 入口網站使用自訂的 Web 組件。 」</span><span class="sxs-lookup"><span data-stu-id="d5e2c-131">Otherwise, you will not be able to import, and hence use the CustomWebPart.dll in the SharePoint portal in “Step 3: Configure the SharePoint Portal to use the custom Web Part.”</span></span> <span data-ttu-id="d5e2c-132">請參閱[如何： 使用強式名稱簽署組](https://msdn.microsoft.com/library/xc31ft41.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-132">See [How to: Sign an Assembly with a Strong Name](https://msdn.microsoft.com/library/xc31ft41.aspx).</span></span>
  
## <a name="step-2-deploy-the-custom-web-part-to-a-sharepoint-portal"></a><span data-ttu-id="d5e2c-133">步驟 2： 將自訂的 Web 組件部署到 SharePoint 入口網站</span><span class="sxs-lookup"><span data-stu-id="d5e2c-133">Step 2: Deploy the custom Web Part to a SharePoint Portal</span></span>  
 <span data-ttu-id="d5e2c-134">您必須執行下列命令來讓 CustomWebPart.dll 檔案 （自訂的 Web 組件） 中建立 「 步驟 1： 建立自訂的 Web 組件 」 的 SharePoint 入口網站上可使用本主題：</span><span class="sxs-lookup"><span data-stu-id="d5e2c-134">You must do the following to make the CustomWebPart.dll file (custom Web Part) that is created in “Step 1: Create a custom Web Part” of this topic usable on the SharePoint portal:</span></span>  
  
- <span data-ttu-id="d5e2c-135">**將 CustomWebPart.dll 檔案複製到 SharePoint 入口網站的 bin 資料夾**: Microsoft Office SharePoint Server 建立在入口網站\<根磁碟機\>: \Inetpub\wwwroot\wss\VirtualDirectories 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-135">**Copy the CustomWebPart.dll file to the bin folder of the SharePoint Portal**: Microsoft Office SharePoint Server creates portals under the \<root drive\>:\Inetpub\wwwroot\wss\VirtualDirectories folder.</span></span> <span data-ttu-id="d5e2c-136">資料夾會為每個入口網站中，建立，而且可以識別的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-136">A folder is created for each portal, and can be identified with the port number.</span></span> <span data-ttu-id="d5e2c-137">您必須複製 CustomWebPart.dll 檔案中建立 「 步驟 1： 建立自訂的 Web 組件 」 這個主題中的\<根磁碟機\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< Port_Number\>\bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-137">You must copy the CustomWebPart.dll file created in “Step 1: Create a custom Web Part” of this topic to the \<root drive\>:\Inetpub\wwwroot\wss\VirtualDirectories\\<Port_Number\>\bin folder.</span></span> <span data-ttu-id="d5e2c-138">例如，如果您的 SharePoint 入口網站的連接埠號碼是 13614，您必須 CustomWebPart.dll 檔案複製到\<根磁碟機\>: \Inetpub\wwwroot\wss\VirtualDirectories\13614\bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-138">For example, if the port number of your SharePoint portal is 13614, you must copy the CustomWebPart.dll file to the \<root drive\>:\Inetpub\wwwroot\wss\VirtualDirectories\13614\bin folder.</span></span>  
  
  > [!TIP]
  >  <span data-ttu-id="d5e2c-139">若要尋找您的 SharePoint 入口網站的資料夾位置的另一個方法是使用**Internet Information Services (IIS) 管理員** 視窗 (**開始** > **執行** >  **inetmgr**)。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-139">Another way to find the folder location of your SharePoint portal is by using the **Internet Information Services (IIS) Manager** window (**Start** > **Run** > **inetmgr**).</span></span> <span data-ttu-id="d5e2c-140">找出您的 SharePoint 入口網站中**Internet Information Services (IIS) 管理員**] 視窗 ([電腦名稱] > 網站 > [入口網站名稱])，以滑鼠右鍵按一下，然後再按一下**屬性**中快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-140">Locate your SharePoint portal in the **Internet Information Services (IIS) Manager** window ([computer_name] > Web Sites > [Portal-Name]), right-click, and then click **Properties** in the shortcut menu.</span></span> <span data-ttu-id="d5e2c-141">在 SharePoint 入口網站的 屬性 對話方塊中，按一下**主目錄**索引標籤，然後按**本機路徑** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-141">In the properties dialog box of the SharePoint portal, click the **Home Directory** tab, and then select the **Local path** box.</span></span>  
  
- <span data-ttu-id="d5e2c-142">**將安全控制項項目加入 web.config 檔案中**： 因為 CustomWebPart.dll 檔案將用於不同的電腦上，並由多個使用者，您必須宣告檔案為 「 安全 」。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-142">**Add the Safe Control Entry in the web.config File**: Because the CustomWebPart.dll file will be used on different computers and by multiple users, you must declare the file as “safe.”</span></span> <span data-ttu-id="d5e2c-143">若要這樣做，請開啟 位於在入口網站的 SharePoint 資料夾中的 web.config 檔案\<根磁碟機\>: \Inetpub\wwwroot\wss\VirtualDirectories\\< Port_Number\>。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-143">To do so, open the web.config file located in the SharePoint portal folder at \<root drive\>:\Inetpub\wwwroot\wss\VirtualDirectories\\<Port_Number\>.</span></span> <span data-ttu-id="d5e2c-144">在下`<SafeControls>`區段的 web.config 檔案中，加入下列的安全控制項項目：</span><span class="sxs-lookup"><span data-stu-id="d5e2c-144">Under the `<SafeControls>` section of the web.config file, add the following safe control entry:</span></span>  
  
  - <span data-ttu-id="d5e2c-145">**在 32 位元電腦：**</span><span class="sxs-lookup"><span data-stu-id="d5e2c-145">**On 32-bit computer:**</span></span>  
  
    ```  
    <SafeControl Assembly="CustomWebPart" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
    ```  
  
  - <span data-ttu-id="d5e2c-146">**在 64 位元電腦：**</span><span class="sxs-lookup"><span data-stu-id="d5e2c-146">**On 64-bit computer:**</span></span>  
  
    ```  
    <SafeControl Assembly="CustomWebPart, Version=1.0.0.0, Culture=neutral, PublicKeyToken=<PUBLICKKEYTOKEN_OF_CustomWebPart.dll>" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
    ```  
  
    <span data-ttu-id="d5e2c-147">儲存 web.config 檔案中，然後關閉它。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-147">Save the web.config file, and then close it.</span></span>  
  
## <a name="step-3-configure-the-sharepoint-portal-to-use-the-custom-web-part"></a><span data-ttu-id="d5e2c-148">步驟 3： 設定 SharePoint 入口網站，以使用自訂的 Web 組件</span><span class="sxs-lookup"><span data-stu-id="d5e2c-148">Step 3: Configure the SharePoint portal to use the custom Web Part</span></span>  
 <span data-ttu-id="d5e2c-149">您需要將自訂的 Web 組件新增至 Microsoft Office SharePoint Server Web 組件庫，以便您可以將其用於您的 SharePoint 入口網站。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-149">You need to add the custom Web Part to the Microsoft Office SharePoint Server Web Part Gallery, so that you can use it on your SharePoint portal.</span></span> <span data-ttu-id="d5e2c-150">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="d5e2c-150">To do so:</span></span>  
  
1. <span data-ttu-id="d5e2c-151">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-151">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="d5e2c-152">按一下 **開始**，指向**所有程式**，指向**Microsoft Office Server**，然後按一下  **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="d5e2c-152">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2. <span data-ttu-id="d5e2c-153">在左側的導覽窗格中，按一下名稱的共用服務提供者 (SSP) 您要加入自訂的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-153">In the left navigation pane, click the name of the Shared Service Provider (SSP) to which you want to add the custom Web Part.</span></span>  
  
3. <span data-ttu-id="d5e2c-154">在 共用服務管理頁面上，在右上角，按一下 **站台動作**，然後按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-154">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Create**.</span></span>  
  
4. <span data-ttu-id="d5e2c-155">在 站台設定 頁面中，按一下  **Web 組件**下方**組件庫**資料行。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-155">On the Site Settings page, click **Web Parts** under the **Galleries** column.</span></span>  
  
5. <span data-ttu-id="d5e2c-156">在網頁組件庫 頁面上，若要將自訂的 Web 組件新增至資源庫中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-156">On the Web Part Gallery page, to add the custom Web Part to the gallery,  click **New**.</span></span> <span data-ttu-id="d5e2c-157">此時不網頁組件庫頁面中，您可以使用自訂的 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-157">At this point the custom Web Part is not available in the Web Part Gallery page.</span></span>  
  
6. <span data-ttu-id="d5e2c-158">在新的 Web 組件 頁面上，找出**CustomWebPart** （自訂的 Web 組件的名稱） 在清單中，選取左邊的核取方塊，然後再按一下**擴展組件庫**頁面頂端。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-158">On the New Web Parts page, locate **CustomWebPart** (name of the custom Web Part) in the list, select the check box on the left, and then click **Populate Gallery** on the top of the page.</span></span> <span data-ttu-id="d5e2c-159">這會新增**CustomWebPart**網頁組件庫頁面中的項目。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-159">This will add the **CustomWebPart** entry in the Web Part Gallery page.</span></span>  
  
   <span data-ttu-id="d5e2c-160">現在您可以使用自訂的 Web 組件 (**CustomWebPart**) 在 您的 SharePoint 入口網站中建立 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-160">Now you can use the custom Web Part (**CustomWebPart**) to create Web Parts in your SharePoint portal.</span></span> <span data-ttu-id="d5e2c-161">自訂的 Web 組件 (**CustomWebPart**) 會出現在**其他**新增網頁組件頁面上的一節。</span><span class="sxs-lookup"><span data-stu-id="d5e2c-161">The custom Web Part (**CustomWebPart**) will appear under the **Miscellaneous** section in the Add Web Parts page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e2c-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5e2c-162">See Also</span></span>  
[<span data-ttu-id="d5e2c-163">搭配使用 SharePoint 與 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="d5e2c-163">Use the SAP adapter with SharePoint</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md)