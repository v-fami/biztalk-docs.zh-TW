---
title: "如何自訂 web 組件使用 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf420061-41d1-4d97-9be1-403cd101e41c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f3b2888b21c2c59b01ddaf920d55ccadb79e326
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="how-to-use-a-custom-web-part-with-oracle-e-business-suite"></a><span data-ttu-id="9496b-102">如何使用 Oracle E-business Suite 中的自訂 web 組件</span><span class="sxs-lookup"><span data-stu-id="9496b-102">How to use a custom web part with Oracle E-Business Suite</span></span>
<span data-ttu-id="9496b-103">本節提供與 Microsoft Office SharePoint Server 中使用自訂的 Web 組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9496b-103">This section provides information about using a custom Web Part with Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="9496b-104">若要使用自訂的 Web 組件，您必須執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="9496b-104">To use a custom Web Part, you must do the following:</span></span>  
  
1.  <span data-ttu-id="9496b-105">建立自訂的 Web 組件</span><span class="sxs-lookup"><span data-stu-id="9496b-105">Create a custom Web Part</span></span>  
  
2.  <span data-ttu-id="9496b-106">將自訂 Web 組件部署到 SharePoint 入口網站</span><span class="sxs-lookup"><span data-stu-id="9496b-106">Deploy the custom Web Part to a SharePoint portal</span></span>  
  
3.  <span data-ttu-id="9496b-107">設定 SharePoint 入口網站使用自訂 Web 組件</span><span class="sxs-lookup"><span data-stu-id="9496b-107">Configure the SharePoint portal to use the custom Web Part</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="9496b-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="9496b-108">Before You Begin</span></span>  
 <span data-ttu-id="9496b-109">建立自訂的 Web 組件之前：</span><span class="sxs-lookup"><span data-stu-id="9496b-109">Before you create a custom Web Part:</span></span>  
  
-   <span data-ttu-id="9496b-110">將 Oracle E-business Suite 成品發佈為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="9496b-110">Publish the Oracle E-Business Suite artifacts as a  WCF service.</span></span> <span data-ttu-id="9496b-111">如需詳細資訊，請參閱[步驟 1： 使用 Oracle E-business 配接器來建立和發佈的 WCF 服務](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md)中[教學課程： 呈現資料，從 SharePoint 網站上的 Oracle E-business Suite](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)。</span><span class="sxs-lookup"><span data-stu-id="9496b-111">For more information, see [Step 1: Use the Oracle E-Business Adapter to create and publish a WCF service](../../adapters-and-accelerators/adapter-oracle-ebs/step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service.md) in [Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).</span></span>  
  
-   <span data-ttu-id="9496b-112">建立商務資料目錄使用 Microsoft Office SharePoint Server 中的 Oracle E-business Suite 成品的應用程式定義檔。</span><span class="sxs-lookup"><span data-stu-id="9496b-112">Create an application definition file for the Oracle E-Business Suite artifacts using the Business Data Catalog in Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="9496b-113">如需詳細資訊，請參閱[步驟 2： 建立 Oracle E-business Suite 成品的應用程式定義檔](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md)中[教學課程： 呈現資料，從 SharePoint 網站上的 Oracle E-business Suite](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)。</span><span class="sxs-lookup"><span data-stu-id="9496b-113">For more information, see [Step 2: Create an application definition file for the Oracle E-Business Suite artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md) in [Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).</span></span>  
  
##  <span data-ttu-id="9496b-114"><a name="Create_a_Custom_Web_Part"></a>步驟 1： 建立自訂的 Web 組件</span><span class="sxs-lookup"><span data-stu-id="9496b-114"><a name="Create_a_Custom_Web_Part"></a> Step 1: Create a custom Web Part</span></span>  
  
1.  <span data-ttu-id="9496b-115">啟動 Visual Studio，並再建立專案。</span><span class="sxs-lookup"><span data-stu-id="9496b-115">Start Visual Studio, and then create a project.</span></span>  
  
2.  <span data-ttu-id="9496b-116">在**新專案**對話方塊中，從**專案類型**窗格中，選取**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="9496b-116">In the **New Project** dialog box, from the **Project types** pane, select **Visual C#**.</span></span> <span data-ttu-id="9496b-117">從**範本**窗格中，選取**類別庫**。</span><span class="sxs-lookup"><span data-stu-id="9496b-117">From the **Templates** pane, select **Class Library**.</span></span>  
  
3.  <span data-ttu-id="9496b-118">指定的名稱和位置的方案。</span><span class="sxs-lookup"><span data-stu-id="9496b-118">Specify a name and location for the solution.</span></span> <span data-ttu-id="9496b-119">本主題中，指定`CustomWebPart`中**名稱**和**方案名稱**方塊。</span><span class="sxs-lookup"><span data-stu-id="9496b-119">For this topic, specify `CustomWebPart` in the **Name** and **Solution Name** boxes.</span></span> <span data-ttu-id="9496b-120">指定的位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9496b-120">Specify a location, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="9496b-121">將 System.Web 元件的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="9496b-121">Add a reference to the System.Web component into the project.</span></span> <span data-ttu-id="9496b-122">以滑鼠右鍵按一下專案名稱中的**方案總管 中**，然後按一下**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="9496b-122">Right-click the project name in **Solution Explorer**, and then click **Add Reference**.</span></span> <span data-ttu-id="9496b-123">在**加入參考**對話方塊中，選取**System.Web**中**.NET**索引標籤，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9496b-123">In the **Add Reference** dialog box, select **System.Web** in the **.NET** tab, and then click **OK**.</span></span> <span data-ttu-id="9496b-124">System.Web 元件包含 System.Web.UI.WebControls.WebParts 必要的命名的空間。</span><span class="sxs-lookup"><span data-stu-id="9496b-124">The System.Web component contains the required namespace of System.Web.UI.WebControls.WebParts.</span></span>  
  
5.  <span data-ttu-id="9496b-125">加入必要的程式碼，根據您在專案中的問題。</span><span class="sxs-lookup"><span data-stu-id="9496b-125">Add the required code based on your issue in the project.</span></span> <span data-ttu-id="9496b-126">有關特定問題的程式碼範例，請參閱 「 問題涉及自訂 Web 組件 」，在[搭配 SharePoint 使用 Oracle Business Suite 介面卡的考量](../../adapters-and-accelerators/adapter-oracle-ebs/considerations-using-the-oracle-business-suite-adapter-with-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="9496b-126">For the code sample that is relevant to a certain issue, see “Issues Involving Custom Web Parts” in [Considerations using the Oracle-Business Suite adapter with SharePoint](../../adapters-and-accelerators/adapter-oracle-ebs/considerations-using-the-oracle-business-suite-adapter-with-sharepoint.md).</span></span>  
  
6.  <span data-ttu-id="9496b-127">建置專案。</span><span class="sxs-lookup"><span data-stu-id="9496b-127">Build the project.</span></span> <span data-ttu-id="9496b-128">專案建置成功，將產生的.dll 檔案，CustomWebPart.dll，在\<專案資料夾 >/bin/Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9496b-128">On successful build of the project, a .dll file, CustomWebPart.dll, will be generated in the \<project folder>/bin/Debug folder.</span></span>  
  
7.  <span data-ttu-id="9496b-129">**僅適用於 64 位元電腦**： 之前執行下列步驟簽署為強式名稱的 CustomWebPart.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="9496b-129">**Only for 64-bit computer**: Sign the CustomWebPart.dll file with a strong name before performing the following steps.</span></span> <span data-ttu-id="9496b-130">否則，您將無法匯入，並因此使用中的 SharePoint 入口網站中的 CustomWebPart.dll 「 步驟 3： 設定 SharePoint 入口網站使用自訂 Web 組件。 」</span><span class="sxs-lookup"><span data-stu-id="9496b-130">Otherwise, you will not be able to import, and hence use the CustomWebPart.dll in the SharePoint portal in “Step 3: Configure the SharePoint Portal to use the custom Web Part.”</span></span> <span data-ttu-id="9496b-131">如需如何簽署為強式名稱組件資訊，請參閱[How to： 將組件強式名稱簽署](https://msdn.microsoft.com/library/xc31ft41.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9496b-131">For information about how to sign an assembly with a strong name, see [How to: Sign an Assembly with a Strong Name](https://msdn.microsoft.com/library/xc31ft41.aspx).</span></span>
  
## <a name="step-2-deploy-the-custom-web-part-to-a-sharepoint-portal"></a><span data-ttu-id="9496b-132">步驟 2： 將自訂 Web 組件部署到 SharePoint 入口網站</span><span class="sxs-lookup"><span data-stu-id="9496b-132">Step 2: Deploy the custom Web Part to a SharePoint Portal</span></span>  
 <span data-ttu-id="9496b-133">您必須執行下列命令來讓 CustomWebPart.dll 檔案 （自訂的 Web 組件） 中建立 「 步驟 1： 建立自訂的 Web 組件 」 的 SharePoint 入口網站上，您可以使用本主題：</span><span class="sxs-lookup"><span data-stu-id="9496b-133">You must do the following to make the CustomWebPart.dll file (custom Web Part) that is created in “Step 1: Create a custom Web Part” of this topic usable on the SharePoint portal:</span></span>  
  
-   <span data-ttu-id="9496b-134">**CustomWebPart.dll 檔案複製到 SharePoint 入口網站的 bin 資料夾**: Microsoft Office SharePoint Server 建立入口網站下的\<根磁碟機 >: \Inetpub\wwwroot\wss\VirtualDirectories 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9496b-134">**Copy the CustomWebPart.dll file to the bin folder of the SharePoint Portal**: Microsoft Office SharePoint Server creates portals under the \<root drive>:\Inetpub\wwwroot\wss\VirtualDirectories folder.</span></span> <span data-ttu-id="9496b-135">資料夾會針對每個入口網站中，建立，而且可以識別的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="9496b-135">A folder is created for each portal, and can be identified with the port number.</span></span> <span data-ttu-id="9496b-136">您必須複製 CustomWebPart.dll 檔案建立在 「 步驟 1： 建立自訂的 Web 組件 」 本主題的\<根磁碟機 >: \Inetpub\wwwroot\wss\VirtualDirectories\\< Port_Number > \bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9496b-136">You must copy the CustomWebPart.dll file created in “Step 1: Create a custom Web Part” of this topic to the \<root drive>:\Inetpub\wwwroot\wss\VirtualDirectories\\<Port_Number>\bin folder.</span></span> <span data-ttu-id="9496b-137">例如，如果您的 SharePoint 入口網站的通訊埠編號是 13614，您必須複製 CustomWebPart.dll 檔案\<根磁碟機 >: \Inetpub\wwwroot\wss\VirtualDirectories\13614\bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9496b-137">For example, if the port number of your SharePoint portal is 13614, you must copy the CustomWebPart.dll file to the \<root drive>:\Inetpub\wwwroot\wss\VirtualDirectories\13614\bin folder.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="9496b-138">若要尋找您的 SharePoint 入口網站的資料夾位置的另一個方法是使用**網際網路資訊服務 (IIS) 管理員**視窗 (**啟動** > **執行** >  **inetmgr**)。</span><span class="sxs-lookup"><span data-stu-id="9496b-138">Another way to find the folder location of your SharePoint portal is by using the **Internet Information Services (IIS) Manager** window (**Start** > **Run** > **inetmgr**).</span></span> <span data-ttu-id="9496b-139">找出您的 SharePoint 入口網站中**網際網路資訊服務 (IIS) 管理員**視窗 ([電腦名稱] > 網站 > [入口網站名稱])，按一下滑鼠右鍵，然後再按一下**屬性**中快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="9496b-139">Locate your SharePoint portal in the **Internet Information Services (IIS) Manager** window ([computer_name] > Web Sites > [Portal-Name]), right-click, and then click **Properties** in the shortcut menu.</span></span> <span data-ttu-id="9496b-140">在 屬性 對話方塊中的 SharePoint 入口網站，按一下 **主目錄**索引標籤，然後選取**本機路徑**方塊。</span><span class="sxs-lookup"><span data-stu-id="9496b-140">In the properties dialog box of the SharePoint portal, click the **Home Directory** tab, and then select the **Local path** box.</span></span>  
  
-   <span data-ttu-id="9496b-141">**在 web.config 檔案中加入安全控制項項目**： 因為 CustomWebPart.dll 檔案將用於不同的電腦上並由多個使用者，您必須宣告為 「 安全 」。 檔案</span><span class="sxs-lookup"><span data-stu-id="9496b-141">**Add the Safe Control Entry in the web.config File**: Because the CustomWebPart.dll file will be used on different computers and by multiple users, you must declare the file as “safe.”</span></span> <span data-ttu-id="9496b-142">若要這樣做，開啟 web.config 檔案位於位於入口網站的 SharePoint 資料夾\<根磁碟機 >: \Inetpub\wwwroot\wss\VirtualDirectories\\< Port_Number >。</span><span class="sxs-lookup"><span data-stu-id="9496b-142">To do so, open the web.config file located in the SharePoint portal folder at \<root drive>:\Inetpub\wwwroot\wss\VirtualDirectories\\<Port_Number>.</span></span> <span data-ttu-id="9496b-143">在下`<SafeControls>`> 一節的 web.config 檔案中，加入下列安全控制項項目：</span><span class="sxs-lookup"><span data-stu-id="9496b-143">Under the `<SafeControls>` section of the web.config file, add the following safe control entry:</span></span>  
  
    -   <span data-ttu-id="9496b-144">**在 32 位元電腦：**</span><span class="sxs-lookup"><span data-stu-id="9496b-144">**On 32-bit computer:**</span></span>  
  
        ```  
        <SafeControl Assembly="CustomWebPart" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
        ```  
  
    -   <span data-ttu-id="9496b-145">**在 64 位元電腦：**</span><span class="sxs-lookup"><span data-stu-id="9496b-145">**On 64-bit computer:**</span></span>  
  
        ```  
        <SafeControl Assembly="CustomWebPart, Version=1.0.0.0, Culture=neutral, PublicKeyToken=<PUBLICKKEYTOKEN_OF_CustomWebPart.dll>" Namespace="CustomWebPart" TypeName="*" Safe="True" />  
        ```  
  
     <span data-ttu-id="9496b-146">儲存 web.config 檔案中，，然後關閉它。</span><span class="sxs-lookup"><span data-stu-id="9496b-146">Save the web.config file, and then close it.</span></span>  
  
## <a name="step-3-configure-the-sharepoint-portal-to-use-the-custom-web-part"></a><span data-ttu-id="9496b-147">步驟 3： 設定 SharePoint 入口網站使用自訂 Web 組件</span><span class="sxs-lookup"><span data-stu-id="9496b-147">Step 3: Configure the SharePoint portal to use the custom Web Part</span></span>  
 <span data-ttu-id="9496b-148">您需要將自訂 Web 組件新增至 Microsoft Office SharePoint Server Web 組件庫，以便您可以使用它在您的 SharePoint 入口網站上。</span><span class="sxs-lookup"><span data-stu-id="9496b-148">You need to add the custom Web Part to the Microsoft Office SharePoint Server Web Part Gallery, so that you can use it on your SharePoint portal.</span></span> <span data-ttu-id="9496b-149">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="9496b-149">To do so:</span></span>  
  
1.  <span data-ttu-id="9496b-150">啟動 SharePoint 3.0 管理中心。</span><span class="sxs-lookup"><span data-stu-id="9496b-150">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="9496b-151">按一下**啟動**，指向 **所有程式**，指向  **Microsoft Office Server**，然後按一下 **SharePoint 3.0 管理中心**.</span><span class="sxs-lookup"><span data-stu-id="9496b-151">Click **Start**, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="9496b-152">在左側瀏覽窗格中，按一下 共用服務提供者 (SSP) 的您要加入自訂 Web 組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="9496b-152">In the left navigation pane, click the name of the Shared Service Provider (SSP) to which you want to add the custom Web Part.</span></span>  
  
3.  <span data-ttu-id="9496b-153">在右上角的 共用服務管理 頁面上，按一下 **網站動作**，然後按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="9496b-153">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Create**.</span></span>  
  
4.  <span data-ttu-id="9496b-154">在站台設定] 頁面上，按一下 [ **Web 組件**下**圖庫**資料行。</span><span class="sxs-lookup"><span data-stu-id="9496b-154">On the Site Settings page, click **Web Parts** under the **Galleries** column.</span></span>  
  
5.  <span data-ttu-id="9496b-155">在網頁組件庫 頁面上，若要將自訂 Web 組件新增至圖庫中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="9496b-155">On the Web Part Gallery page, to add the custom Web Part to the gallery,  click **New**.</span></span> <span data-ttu-id="9496b-156">此時不網頁組件庫頁面中，您可以使用自訂 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="9496b-156">At this point the custom Web Part is not available in the Web Part Gallery page.</span></span>  
  
6.  <span data-ttu-id="9496b-157">在新的 Web 組件 頁面上，找出**CustomWebPart** （自訂的 Web 組件的名稱） 在清單中，選取左邊的核取方塊，然後按一下**擴展組件庫**的頁面頂端。</span><span class="sxs-lookup"><span data-stu-id="9496b-157">On the New Web Parts page, locate **CustomWebPart** (name of the custom Web Part) in the list, select the check box on the left, and then click **Populate Gallery** on the top of the page.</span></span> <span data-ttu-id="9496b-158">這會新增**CustomWebPart**網頁組件庫頁面中的項目。</span><span class="sxs-lookup"><span data-stu-id="9496b-158">This will add the **CustomWebPart** entry in the Web Part Gallery page.</span></span>  
  
 <span data-ttu-id="9496b-159">現在您可以使用自訂 Web 組件 (**CustomWebPart**) 在您的 SharePoint 入口網站中建立 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="9496b-159">Now you can use the custom Web Part (**CustomWebPart**) to create Web Parts in your SharePoint portal.</span></span> <span data-ttu-id="9496b-160">自訂的 Web 組件 (**CustomWebPart**) 會出現在**其他**新增網頁組件頁面 區段中的。</span><span class="sxs-lookup"><span data-stu-id="9496b-160">The custom Web Part (**CustomWebPart**) will appear under the **Miscellaneous** section in the Add Web Parts page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9496b-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9496b-161">See Also</span></span>  
[<span data-ttu-id="9496b-162">搭配 SharePoint 使用 Oracle E-business Suite 介面卡</span><span class="sxs-lookup"><span data-stu-id="9496b-162">Use the Oracle E-Business Suite adapter with SharePoint</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md)