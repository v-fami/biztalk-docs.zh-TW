---
title: 逐步解說： 模組 1-傳送和接收訊息與 Windows SharePoint Services 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services, creating sites
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapter tutorials, receiving messages
- security, Windows SharePoint Services
- creating, Windows SharePoint Services site
- Windows SharePoint Services, security
- Windows SharePoint Services, document libraries
- Windows SharePoint Services adapters, security
- Windows SharePoint Services
- Windows SharePoint Services adapter tutorials, sending messages
ms.assetid: 6494aef5-bb1d-4a41-8186-1d49625a1013
caps.latest.revision: 41
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8e83297233c4f8ac51ad90f488437a6c259691a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010503"
---
# <a name="walkthrough-module-1---sending-and-receiving-messages-with-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="8172f-102">逐步解說： 模組 1-傳送和接收訊息，Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="8172f-102">Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter</span></span>
<span data-ttu-id="8172f-103">本逐步解說會示範如何設定 Windows SharePoint Services 和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讓您可以傳送和接收訊息，使用 Windows SharePoint Services 配接器和以內容為基礎的路由 (CBR)。</span><span class="sxs-lookup"><span data-stu-id="8172f-103">This walkthrough shows you how to configure Windows SharePoint Services and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] so you can send and receive a message using the Windows SharePoint Services Adapter and content-based routing (CBR).</span></span> <span data-ttu-id="8172f-104">對於繫結至特定連接埠的訊息，以內容為基礎的路由可免除訊息訂閱之需求。</span><span class="sxs-lookup"><span data-stu-id="8172f-104">Content-based routing eliminates the need for message subscription for messages that are deterministically bound to specific ports.</span></span> <span data-ttu-id="8172f-105">它也提供額外的彈性，讓使用者可傳遞以信封屬性為基礎的訊息，或僅以接收埠組態屬性為基礎的訊息。</span><span class="sxs-lookup"><span data-stu-id="8172f-105">It also provides additional flexibility for users who want to route messages based on envelope properties or simply based on receive port configuration properties.</span></span> <span data-ttu-id="8172f-106">如需 Windows SharePoint Services 配接器的簡介，請參閱[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="8172f-106">For an introduction to the Windows SharePoint Services adapter, see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8172f-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="8172f-107">Prerequisites</span></span>  
 <span data-ttu-id="8172f-108">下列是執行本主題所述程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="8172f-108">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="8172f-109">您必須已完整安裝上執行的 BizTalk Server 的單一伺服器部署[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]或[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8172f-109">You must have a single-server deployment with a complete installation of BizTalk Server running on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span></span>  
  
 <span data-ttu-id="8172f-110">在多重伺服器部署中使用的 Windows SharePoint Services 配接器的相關資訊，請參閱[設定和部署 Windows SharePoint Services 配接器](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="8172f-110">For information about using the Windows SharePoint Services adapter in a multiserver deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="configure-windows-sharepoint-services"></a><span data-ttu-id="8172f-111">設定 Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="8172f-111">Configure Windows SharePoint Services</span></span>  
 <span data-ttu-id="8172f-112">在此程序中，您會建立 1 個包含 3 個文件庫的 SharePoint 頂層網站。</span><span class="sxs-lookup"><span data-stu-id="8172f-112">In this procedure you create a SharePoint top-level Web site that contains three document libraries.</span></span> <span data-ttu-id="8172f-113">Windows SharePoint Services 配接器使用這些文件庫，從來源程式庫將訊息移至目的地文件庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-113">The Windows SharePoint Services adapter uses these libraries to move a message from a source library to a destination library.</span></span> <span data-ttu-id="8172f-114">此訊息也會封存於文件庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-114">This message is also archived in a document library.</span></span> <span data-ttu-id="8172f-115">必須執行本程序，才可讓 Windows Sharepoint Services 網站供這個逐步解說中的 Windows Sharepoint Services 配接器存取，以及設定啟用存取該網站的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="8172f-115">This procedure must be done to provide the Windows Sharepoint Services site that is accessed by the Windows Sharepoint Services adapter in this walkthrough and to set user rights to enable access to this site.</span></span>  
  
#### <a name="create-a-windows-sharepoint-services-site"></a><span data-ttu-id="8172f-116">建立 Windows SharePoint Services 網站</span><span class="sxs-lookup"><span data-stu-id="8172f-116">Create a Windows SharePoint Services site</span></span>  
  
1.  <span data-ttu-id="8172f-117">按一下**啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **SharePoint 管理中心。**</span><span class="sxs-lookup"><span data-stu-id="8172f-117">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration.**</span></span>  
  
2.  <span data-ttu-id="8172f-118">在下**虛擬伺服器設定**，按一下 **建立頂層網站**。</span><span class="sxs-lookup"><span data-stu-id="8172f-118">Under **Virtual Server Configuration**, click **Create a top-level Web site**.</span></span>  
  
3.  <span data-ttu-id="8172f-119">在下**虛擬伺服器清單**，選取您在安裝 Windows SharePoint Services 配接器的網站。</span><span class="sxs-lookup"><span data-stu-id="8172f-119">Under **Virtual Server List**, select the Web site that you installed the Windows SharePoint Services Adapter on.</span></span> <span data-ttu-id="8172f-120">例如， `Default Web Site`。</span><span class="sxs-lookup"><span data-stu-id="8172f-120">For example, `Default Web Site`.</span></span>  
  
4.  <span data-ttu-id="8172f-121">在**網站位址**區段的**URL 名稱**欄位中，輸入`WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="8172f-121">In the **Web Site Address** section, in the **URL name** field, type `WSSAdapterWalkthrough`.</span></span>  
  
5.  <span data-ttu-id="8172f-122">在**網站集合擁有者**區段的**使用者名稱 欄位，** 輸入使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="8172f-122">In the **Site Collection Owner** section, in the **User name field,** type a user name.</span></span> <span data-ttu-id="8172f-123">此使用者是網站擁有者，而且不需要特殊權限中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8172f-123">This user will be the owner for the Web site and does not need special permissions in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
6.  <span data-ttu-id="8172f-124">在**網站集合擁有者**區段的**電子郵件**欄位中，輸入電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="8172f-124">In the **Site Collection Owner** section, in the **E-mail** field, type in an e-mail address.</span></span>  
  
7.  <span data-ttu-id="8172f-125">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-125">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="8172f-126">在**成功建立頂層網站**頁面上，按一下您剛建立新最上層的網站。</span><span class="sxs-lookup"><span data-stu-id="8172f-126">On the **Top-Level Site Successfully Created** page, click the new top-level Web site you just created.</span></span> <span data-ttu-id="8172f-127">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="8172f-127">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
9. <span data-ttu-id="8172f-128">選取**小組網站**範本，然後再按一下清單中的範本**確定**。</span><span class="sxs-lookup"><span data-stu-id="8172f-128">Select the **Team Site** template from the list of templates, and then click **OK**.</span></span> <span data-ttu-id="8172f-129">這樣會開啟「小組網站」首頁。</span><span class="sxs-lookup"><span data-stu-id="8172f-129">This will open the Team Web Site Home page.</span></span>  
  
#### <a name="create-a-source-document-library"></a><span data-ttu-id="8172f-130">建立來源文件庫</span><span class="sxs-lookup"><span data-stu-id="8172f-130">Create a "Source" document library</span></span>  
  
1.  <span data-ttu-id="8172f-131">在 「 小組網站首頁 」 的上方導覽列上，按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="8172f-131">On the Team Web Site Home page, on the top navigation bar, click **Create**.</span></span>  
  
2.  <span data-ttu-id="8172f-132">在下**文件庫**，按一下 **文件庫**。</span><span class="sxs-lookup"><span data-stu-id="8172f-132">Under **Document Libraries**, click **Document Library**.</span></span>  
  
3.  <span data-ttu-id="8172f-133">在**名稱和描述**區段的**名稱 欄位中，** 類型`Source`。</span><span class="sxs-lookup"><span data-stu-id="8172f-133">In the **Name and Description** section, in the **Name field,** type `Source`.</span></span>  
  
4.  <span data-ttu-id="8172f-134">在**瀏覽**區段中，選取**是**快速啟動 列上顯示此表單庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-134">In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.</span></span>  
  
5.  <span data-ttu-id="8172f-135">在**文件範本**區段的**文件範本**下拉式清單中，選取`None`。</span><span class="sxs-lookup"><span data-stu-id="8172f-135">In the **Document Template** section, in the **Document Template** drop-down list, select `None`.</span></span>  
  
6.  <span data-ttu-id="8172f-136">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-136">Click **Create**.</span></span> <span data-ttu-id="8172f-137">會建立文件庫，然後將您重新導向至空白文件庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-137">The document library will be created and you will be redirected to the empty library.</span></span>  
  
#### <a name="create-a-destination-document-library"></a><span data-ttu-id="8172f-138">建立目的地文件庫</span><span class="sxs-lookup"><span data-stu-id="8172f-138">Create a "Destination" document library</span></span>  
  
1.  <span data-ttu-id="8172f-139">在 「 小組網站首頁 」 的上方導覽列上，按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="8172f-139">On the Team Web Site Home page, on the top navigation bar, click **Create**.</span></span>  
  
2.  <span data-ttu-id="8172f-140">在下**文件庫**，按一下 **文件庫**。</span><span class="sxs-lookup"><span data-stu-id="8172f-140">Under **Document Libraries**, click **Document Library**.</span></span>  
  
3.  <span data-ttu-id="8172f-141">在**名稱和描述**區段的**名稱 欄位**，型別`Destination`。</span><span class="sxs-lookup"><span data-stu-id="8172f-141">In the **Name and Description** section, in the **Name field**, type `Destination`.</span></span>  
  
4.  <span data-ttu-id="8172f-142">在**瀏覽**區段中，選取**是**快速啟動 列上顯示此表單庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-142">In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.</span></span>  
  
5.  <span data-ttu-id="8172f-143">在**文件範本**區段的**文件範本**下拉式清單中，選取`None`。</span><span class="sxs-lookup"><span data-stu-id="8172f-143">In the **Document Template** section, in the **Document Template** drop-down list, select `None`.</span></span>  
  
6.  <span data-ttu-id="8172f-144">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-144">Click **Create**.</span></span> <span data-ttu-id="8172f-145">會建立文件庫，然後將您重新導向至空白文件庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-145">The document library will be created and you will be redirected to the empty library.</span></span>  
  
#### <a name="create-an-archive-document-library"></a><span data-ttu-id="8172f-146">建立封存文件庫</span><span class="sxs-lookup"><span data-stu-id="8172f-146">Create an "Archive" document library</span></span>  
  
1.  <span data-ttu-id="8172f-147">在 「 小組網站首頁 」 的上方導覽列上，按一下 **建立**。</span><span class="sxs-lookup"><span data-stu-id="8172f-147">On the Team Web Site Home page, on the top navigation bar, click **Create**.</span></span>  
  
2.  <span data-ttu-id="8172f-148">在下**文件庫**，按一下 **文件庫**。</span><span class="sxs-lookup"><span data-stu-id="8172f-148">Under **Document Libraries**, click **Document Library**.</span></span>  
  
3.  <span data-ttu-id="8172f-149">在**名稱**和 描述 部分中**名稱 欄位**，型別`Archive`。</span><span class="sxs-lookup"><span data-stu-id="8172f-149">In the **Name** and Description section, in the **Name field**, type `Archive`.</span></span>  
  
4.  <span data-ttu-id="8172f-150">在**瀏覽**區段中，選取**是**快速啟動 列上顯示此表單庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-150">In the **Navigation** section, select **Yes** to display this form library on the Quick Launch bar.</span></span>  
  
5.  <span data-ttu-id="8172f-151">在**文件範本**區段的**文件範本**下拉式清單中，選取`None`。</span><span class="sxs-lookup"><span data-stu-id="8172f-151">In the **Document Template** section, in the **Document Template** drop-down list, select `None`.</span></span>  
  
6.  <span data-ttu-id="8172f-152">按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-152">Click **Create**.</span></span> <span data-ttu-id="8172f-153">會建立文件庫，然後將您重新導向至空白文件庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-153">The document library will be created and you will be redirected to the empty library.</span></span>  
  
7.  <span data-ttu-id="8172f-154">關閉 `WSSAdapterWalkthrough` 網站。</span><span class="sxs-lookup"><span data-stu-id="8172f-154">Close the `WSSAdapterWalkthrough` Web site.</span></span>  
  
8.  <span data-ttu-id="8172f-155">關閉**SharePoint 管理中心內**網站。</span><span class="sxs-lookup"><span data-stu-id="8172f-155">Close the **SharePoint Central Administration** Web site.</span></span>  
  
#### <a name="configure-windows-security"></a><span data-ttu-id="8172f-156">設定 Windows 安全性</span><span class="sxs-lookup"><span data-stu-id="8172f-156">Configure Windows security</span></span>  
  
1.  <span data-ttu-id="8172f-157">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下 **電腦管理**。</span><span class="sxs-lookup"><span data-stu-id="8172f-157">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="8172f-158">在主控台樹狀目錄中，依序展開**本機使用者和群組**，然後按一下 **群組**。</span><span class="sxs-lookup"><span data-stu-id="8172f-158">In the console tree, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
3.  <span data-ttu-id="8172f-159">以滑鼠右鍵按一下**SharePoint 啟用的主控件**群組中，按一下**新增到群組**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="8172f-159">Right-click the **SharePoint Enabled Hosts** group, click **Add to Group**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="8172f-160">在**選取使用者、 電腦或群組對話方塊**下**輸入物件名稱來選取**，輸入您設定 BizTalk Server 主控件執行個體來執行，然後按一下帳戶名稱**確定**。</span><span class="sxs-lookup"><span data-stu-id="8172f-160">In the **Select Users, Computers, or Groups dialog box**, under **Enter the object names to select**, type the name of the account that you configured the BizTalk Server Host Instance to run under, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="8172f-161">在主控台樹狀目錄中，依序展開**服務和應用程式**，然後按一下 **服務**。</span><span class="sxs-lookup"><span data-stu-id="8172f-161">In the console tree, expand **Services and Applications**, and then click **Services**.</span></span>  
  
6.  <span data-ttu-id="8172f-162">以滑鼠右鍵按一下**BizTalk Service BizTalk Group: < BizTalk_Host_Name >**，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="8172f-162">Right-click **BizTalk Service BizTalk Group: <BizTalk_Host_Name>**, and then click **Restart**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8172f-163"><BizTalk_Host_Name> 是主控件的名稱。</span><span class="sxs-lookup"><span data-stu-id="8172f-163"><BizTalk_Host_Name> is the name of your host.</span></span> <span data-ttu-id="8172f-164">根據預設，此名稱為 `BizTalkServerApplication`。</span><span class="sxs-lookup"><span data-stu-id="8172f-164">By Default, this is `BizTalkServerApplication`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8172f-165">在重新啟動服務的成員資格才會生效。</span><span class="sxs-lookup"><span data-stu-id="8172f-165">Membership does not take effect until the service is restarted.</span></span>  
  
7.  <span data-ttu-id="8172f-166">關閉**電腦管理**。</span><span class="sxs-lookup"><span data-stu-id="8172f-166">Close **Computer Management**.</span></span>  
  
#### <a name="configure-sharepoint-security"></a><span data-ttu-id="8172f-167">設定 SharePoint 安全性</span><span class="sxs-lookup"><span data-stu-id="8172f-167">Configure SharePoint security</span></span>  
  
1.  <span data-ttu-id="8172f-168">開啟 Web 瀏覽器，巡覽至您所建立的網站 URL。</span><span class="sxs-lookup"><span data-stu-id="8172f-168">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="8172f-169">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="8172f-169">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="8172f-170">在 「 小組網站首頁 」 的上方導覽列上，按一下 **站台設定**。</span><span class="sxs-lookup"><span data-stu-id="8172f-170">On the Team Web Site Home page, on the top navigation bar, click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="8172f-171">在下**管理**，按一下 **管理使用者**。</span><span class="sxs-lookup"><span data-stu-id="8172f-171">Under **Administration**, click **Manage users**.</span></span>  
  
4.  <span data-ttu-id="8172f-172">按一下 **[加入使用者]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-172">Click **Add Users**.</span></span>  
  
5.  <span data-ttu-id="8172f-173">在**步驟 1： 選擇使用者**，輸入帳戶的名稱，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]下執行主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8172f-173">In **Step 1: Choose Users**, type the name of the account that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host Instance is running under.</span></span>  
  
6.  <span data-ttu-id="8172f-174">在**步驟 2： 選擇網站群組**，選取**讀取器**和**參與者**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8172f-174">In **Step 2: Choose Site Groups**, select the **Reader** and **Contributor** check boxes.</span></span>  
  
7.  <span data-ttu-id="8172f-175">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-175">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="8172f-176">清除**傳送下列電子郵件，讓這些使用者現在已被新增**核取方塊，然後**完成**。</span><span class="sxs-lookup"><span data-stu-id="8172f-176">Clear the **Send the following e-mail to let these users now they've been added** check box, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="8172f-177">關閉 `WSSAdapterWalkthrough` 網站。</span><span class="sxs-lookup"><span data-stu-id="8172f-177">Close the `WSSAdapterWalkthrough` Web site.</span></span>  
  
## <a name="create-and-configure-the-biztalk-server-ports"></a><span data-ttu-id="8172f-178">建立和設定 BizTalk Server 連接埠</span><span class="sxs-lookup"><span data-stu-id="8172f-178">Create and configure the BizTalk Server ports</span></span>  
 <span data-ttu-id="8172f-179">您會在此程序建立和設定 Windows SharePoint Services 配接器的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收埠、接收位置以及傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8172f-179">In this procedure you will create and configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive ports, receive locations, and send ports for the Windows SharePoint Services adapter.</span></span> <span data-ttu-id="8172f-180">這些連接埠是 Windows Sharepoint Services 配接器接收和傳送文件的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 進出點。</span><span class="sxs-lookup"><span data-stu-id="8172f-180">These ports are points of entry into and out of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for documents received and sent by the Windows Sharepoint Services adapter.</span></span>  
  
#### <a name="create-the-receive-port"></a><span data-ttu-id="8172f-181">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="8172f-181">Create the receive port</span></span>  
  
1.  <span data-ttu-id="8172f-182">按一下**啟動**，**所有程式**， [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 [ **BizTalk Server 管理]。**</span><span class="sxs-lookup"><span data-stu-id="8172f-182">Click **Start**, **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="8172f-183">展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，依序展開**應用程式**，依序展開**BizTalk Application 1**，以滑鼠右鍵按一下**接收埠**，按一下 **新增**，然後按一下 **單向接收埠...**</span><span class="sxs-lookup"><span data-stu-id="8172f-183">Expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, right-click **Receive Ports**, click **New**, and then click **One-way Receive Port…**</span></span>  
  
3.  <span data-ttu-id="8172f-184">在**接收埠屬性**對話方塊的 **一般**，型別`FromSource`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="8172f-184">In the **Receive Port Properties** dialog box, under **General**, type `FromSource` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="8172f-185">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-185">Click **OK**.</span></span>  
  
#### <a name="create-the-receive-location"></a><span data-ttu-id="8172f-186">建立接收位置</span><span class="sxs-lookup"><span data-stu-id="8172f-186">Create the receive location</span></span>  
  
1.  <span data-ttu-id="8172f-187">在**BizTalk 管理主控台**，以滑鼠右鍵按一下**接收位置** 節點，按一下 **新增**，然後按一下 **單向接收位置**.</span><span class="sxs-lookup"><span data-stu-id="8172f-187">In the **BizTalk Administration Console**, right-click the **Receive Locations** node, click **New**, and then click **One-way Receive Location**.</span></span>  
  
2.  <span data-ttu-id="8172f-188">在**選取接收埠**對話方塊中，選取`FromSource`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="8172f-188">In the **Select a Receive Port** dialog box, select `FromSource`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="8172f-189">在**接收位置屬性**對話方塊的 **一般**，型別`SourceLocation`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="8172f-189">In the **Receive Location Properties** dialog box, under **General**, type `SourceLocation` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="8172f-190">在**傳輸**區段的**類型**下拉式清單中，選取`Windows``SharePoint``Services`。</span><span class="sxs-lookup"><span data-stu-id="8172f-190">In the **Transport** section, in the **Type** drop-down list, select `Windows``SharePoint``Services`.</span></span>  
  
5.  <span data-ttu-id="8172f-191">按一下**設定**來設定 Windows SharePoint Services 配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-191">Click **Configure** to configure the Windows SharePoint Services adapter properties.</span></span>  
  
6.  <span data-ttu-id="8172f-192">在**配接器 Web 服務連接埠**屬性中，輸入已安裝 Windows SharePoint Services 配接器 Web 服務的虛擬伺服器的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="8172f-192">In the **Adapter Web Service Port** property, type the port number of the virtual server where the Windows SharePoint Services adapter Web service was installed.</span></span> <span data-ttu-id="8172f-193">預設號碼是連接埠 80。</span><span class="sxs-lookup"><span data-stu-id="8172f-193">By default, this is port 80.</span></span>  
  
7.  <span data-ttu-id="8172f-194">型別`Archive`中**封存位置**屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-194">Type `Archive` in the **Archive Location** property.</span></span>  
  
8.  <span data-ttu-id="8172f-195">型別`10`中**輪詢間隔**屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-195">Type `10` in the **Polling Interval** property.</span></span>  
  
9. <span data-ttu-id="8172f-196">輸入您的 SharePoint 網站中的 URL **ShareP**sharepoint 網站 Url 屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-196">Type the URL to your SharePoint site in the **ShareP**oint Site Url property.</span></span> <span data-ttu-id="8172f-197">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="8172f-197">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
10. <span data-ttu-id="8172f-198">型別`Source`如**來源文件庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-198">Type `Source` for the **Source Document Library** property.</span></span>  
  
11. <span data-ttu-id="8172f-199">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-199">Click **OK**.</span></span>  
  
12. <span data-ttu-id="8172f-200">在**接收位置屬性**對話方塊中，選取`BizTalkServerApplication`為**接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="8172f-200">In the **Receive Location Properties** dialog box, select `BizTalkServerApplication` as the **Receive handler**.</span></span>  
  
13. <span data-ttu-id="8172f-201">在**接收管線**下拉式清單中，選取`PassThruReceive`。</span><span class="sxs-lookup"><span data-stu-id="8172f-201">In the **Receive pipeline** drop-down list, select `PassThruReceive`.</span></span>  
  
14. <span data-ttu-id="8172f-202">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-202">Click **OK**.</span></span>  
  
#### <a name="create-the-send-port"></a><span data-ttu-id="8172f-203">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="8172f-203">Create the send port</span></span>  
  
1.  <span data-ttu-id="8172f-204">在**BizTalk 管理主控台**，以滑鼠右鍵按一下**傳送埠** 節點，按一下 **新增**，然後按一下 **靜態單向傳送埠**.</span><span class="sxs-lookup"><span data-stu-id="8172f-204">In the **BizTalk Administration Console**, right-click the **Send Ports** node, click **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="8172f-205">在**傳送埠屬性**對話方塊的 **一般**，型別`SendToDestination`中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="8172f-205">In the **Send Port Properties** dialog box, under **General**, type `SendToDestination` in the **Name** field.</span></span>  
  
3.  <span data-ttu-id="8172f-206">在**傳輸**區段中，選取`Windows SharePoint Services`類型。</span><span class="sxs-lookup"><span data-stu-id="8172f-206">In the **Transport** section, select `Windows SharePoint Services` for the type.</span></span>  
  
4.  <span data-ttu-id="8172f-207">按一下**設定**來設定 Windows SharePoint Services 配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-207">Click **Configure** to configure the Windows SharePoint Services adapter properties.</span></span>  
  
5.  <span data-ttu-id="8172f-208">在**配接器 Web 服務連接埠**屬性中，輸入已安裝 Windows SharePoint Services 配接器 Web 服務的虛擬伺服器的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="8172f-208">In the **Adapter Web Service Port** property, type the port number of the virtual server where the Windows SharePoint Services adapter Web service was installed.</span></span> <span data-ttu-id="8172f-209">預設號碼是連接埠 80。</span><span class="sxs-lookup"><span data-stu-id="8172f-209">By default, this is port 80.</span></span>  
  
6.  <span data-ttu-id="8172f-210">在中輸入`Destination`如**目的地資料夾**屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-210">Type in `Destination` for the **Destination Folder** property.</span></span>  
  
7.  <span data-ttu-id="8172f-211">在中輸入`PurchaseOrder1-%MessageID%.xml`如**Filename**屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-211">Type in `PurchaseOrder1-%MessageID%.xml` for the **Filename** property.</span></span>  
  
8.  <span data-ttu-id="8172f-212">設定**覆寫**屬性`Yes`。</span><span class="sxs-lookup"><span data-stu-id="8172f-212">Set the **Overwrite** property to `Yes`.</span></span>  
  
9. <span data-ttu-id="8172f-213">在 SharePoint 網站 URL 中的型別**SharePoint 網站 Url**屬性。</span><span class="sxs-lookup"><span data-stu-id="8172f-213">Type in the URL to your SharePoint site in the **SharePoint Site Url** property.</span></span> <span data-ttu-id="8172f-214">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="8172f-214">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
10. <span data-ttu-id="8172f-215">設定**Microsoft Office 整合**屬性`No`。</span><span class="sxs-lookup"><span data-stu-id="8172f-215">Set the **Microsoft Office Integration** property to `No`.</span></span>  
  
11. <span data-ttu-id="8172f-216">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-216">Click **OK**.</span></span>  
  
12. <span data-ttu-id="8172f-217">在**傳送埠屬性 對話方塊**，請在**傳送處理常式**下拉式清單中，選取`BizTalkServerApplication`。</span><span class="sxs-lookup"><span data-stu-id="8172f-217">In the **Send Port Properties dialog box**, in the **Send handler** drop-down list, select `BizTalkServerApplication`.</span></span>  
  
13. <span data-ttu-id="8172f-218">在**傳送管線**下拉式清單中，選取`PassThruTransmit`。</span><span class="sxs-lookup"><span data-stu-id="8172f-218">In the **Send pipeline** drop-down list, select `PassThruTransmit`.</span></span>  
  
14. <span data-ttu-id="8172f-219">按一下**篩選** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8172f-219">Click the **Filters** tab.</span></span>  
  
15. <span data-ttu-id="8172f-220">選取`WSS.InListName`中**屬性**欄位。</span><span class="sxs-lookup"><span data-stu-id="8172f-220">Select `WSS.InListName` in the **Property** field.</span></span>  
  
16. <span data-ttu-id="8172f-221">選取`==`中**運算子**欄位。</span><span class="sxs-lookup"><span data-stu-id="8172f-221">Select `==` in the **Operator** field.</span></span>  
  
17. <span data-ttu-id="8172f-222">型別`Source`中**值**欄位。</span><span class="sxs-lookup"><span data-stu-id="8172f-222">Type `Source` in the **Value** field.</span></span>  
  
18. <span data-ttu-id="8172f-223">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8172f-223">Click **OK**.</span></span>  
  
## <a name="enable-and-start-the-receive-location-and-receive-port"></a><span data-ttu-id="8172f-224">啟用和啟動接收位置和接收埠</span><span class="sxs-lookup"><span data-stu-id="8172f-224">Enable and start the receive location and receive port</span></span>  
 <span data-ttu-id="8172f-225">您可在這些程序啟用接收位置和啟動接收埠。</span><span class="sxs-lookup"><span data-stu-id="8172f-225">In these procedures you enable the receive location and start the receive port.</span></span> <span data-ttu-id="8172f-226">必須完成本程序，Windows Sharepoint Services 配接器才可透過指定的傳送埠和接收位置傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="8172f-226">This procedure must be completed to allow the Windows Sharepoint Services adapter to send and receive messages through the specified send port and receive location.</span></span>  
  
#### <a name="enable-the-receive-location"></a><span data-ttu-id="8172f-227">啟用接收位置</span><span class="sxs-lookup"><span data-stu-id="8172f-227">Enable the receive location</span></span>  
  
1.  <span data-ttu-id="8172f-228">在**BizTalk 管理主控台**，按一下 **接收位置**節點。</span><span class="sxs-lookup"><span data-stu-id="8172f-228">In the **BizTalk Administration Console**, click the **Receive Locations** node.</span></span>  
  
2.  <span data-ttu-id="8172f-229">以滑鼠右鍵按一下`SourceLocation`，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="8172f-229">Right-click `SourceLocation`, and then click **Enable**.</span></span>  
  
#### <a name="start-the-send-port"></a><span data-ttu-id="8172f-230">啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="8172f-230">Start the send port</span></span>  
  
1.  <span data-ttu-id="8172f-231">在**BizTalk 管理主控台**，按一下 **傳送埠**節點。</span><span class="sxs-lookup"><span data-stu-id="8172f-231">In the **BizTalk Administration Console**, click the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="8172f-232">以滑鼠右鍵按一下`SendToDestination`，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="8172f-232">Right-click `SendToDestination`, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="8172f-233">關閉**BizTalk 管理主控台**。</span><span class="sxs-lookup"><span data-stu-id="8172f-233">Close the **BizTalk Administration Console**.</span></span>  
  
## <a name="sending-a-message-through-the-system"></a><span data-ttu-id="8172f-234">透過系統傳送訊息</span><span class="sxs-lookup"><span data-stu-id="8172f-234">Sending a message through the system</span></span>  
 <span data-ttu-id="8172f-235">您會在此程序建立 XML 文件並上載至 Windows SharePoint Services 網站。</span><span class="sxs-lookup"><span data-stu-id="8172f-235">In this procedure you create an XML document and upload it to the Windows SharePoint Services Web site.</span></span> <span data-ttu-id="8172f-236">Windows SharePoint Services 配接器會取得該訊息、封存至「封存」文件庫，然後傳送至「目的地」文件庫。</span><span class="sxs-lookup"><span data-stu-id="8172f-236">The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library.</span></span> <span data-ttu-id="8172f-237">此程序示範如何在文件流經從 Sharepoint 網站， [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以及 Sharepoint Services 網站使用 Windows Sharepoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="8172f-237">This procedure demonstrates how a document flows from a Sharepoint web site, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and to a Sharepoint Services Web site using the Windows Sharepoint Services adapter.</span></span>  
  
#### <a name="create-a-working-directory"></a><span data-ttu-id="8172f-238">建立工作目錄</span><span class="sxs-lookup"><span data-stu-id="8172f-238">Create a working directory</span></span>  
  
-   <span data-ttu-id="8172f-239">呼叫您的電腦上建立目錄**WSSAdapterWalkthrough**。</span><span class="sxs-lookup"><span data-stu-id="8172f-239">Create a directory on your computer called **WSSAdapterWalkthrough**.</span></span> <span data-ttu-id="8172f-240">例如， `C:\WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="8172f-240">For example, `C:\WSSAdapterWalkthrough`.</span></span>  
  
#### <a name="create-an-xml-file"></a><span data-ttu-id="8172f-241">建立 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="8172f-241">Create an XML file</span></span>  
  
1.  <span data-ttu-id="8172f-242">按一下**啟動**，指向 **所有程式**，指向 **附屬應用程式**，然後按一下  **記事本。**</span><span class="sxs-lookup"><span data-stu-id="8172f-242">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Notepad.**</span></span>  
  
2.  <span data-ttu-id="8172f-243">輸入以下內容：</span><span class="sxs-lookup"><span data-stu-id="8172f-243">Type the following:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <PurchaseOrder>  
        <ID>1001</ID>  
        <FirstName>John</FirstName>  
        <LastName>Doe</LastName>  
        <Amount>750</Amount>  
    </PurchaseOrder>  
    ```  
  
3.  <span data-ttu-id="8172f-244">在工作目錄中，將檔案另存為 `PurchaseOrder1.xml`。</span><span class="sxs-lookup"><span data-stu-id="8172f-244">Save the file in your working directory as `PurchaseOrder1.xml`.</span></span> <span data-ttu-id="8172f-245">例如， `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`。</span><span class="sxs-lookup"><span data-stu-id="8172f-245">For example, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`.</span></span>  
  
#### <a name="upload-the-xml-file"></a><span data-ttu-id="8172f-246">上載 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="8172f-246">Upload the XML file</span></span>  
  
1.  <span data-ttu-id="8172f-247">開啟網頁瀏覽器，然後移至您在上一個工作建立的網站之 URL。</span><span class="sxs-lookup"><span data-stu-id="8172f-247">Open a Web browser and navigate to the URL of the site you created in the last task.</span></span> <span data-ttu-id="8172f-248">例如， `http://<server_name>/sites/WSSAdapterWalkthrough`。</span><span class="sxs-lookup"><span data-stu-id="8172f-248">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="8172f-249">在左邊，底下**文件**，按一下 **來源**。</span><span class="sxs-lookup"><span data-stu-id="8172f-249">On the left side, under **Documents**, click **Source**.</span></span>  
  
3.  <span data-ttu-id="8172f-250">按一下**上傳文件**。</span><span class="sxs-lookup"><span data-stu-id="8172f-250">Click **Upload Document**.</span></span>  
  
4.  <span data-ttu-id="8172f-251">在**名稱**方塊中，輸入或瀏覽至 XML 檔案您在上面建立。</span><span class="sxs-lookup"><span data-stu-id="8172f-251">In the **Name** box, type or browse to the XML file you created above.</span></span> <span data-ttu-id="8172f-252">例如， `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`，然後按一下 **儲存並關閉**。</span><span class="sxs-lookup"><span data-stu-id="8172f-252">For example, `C:\WSSAdapterWalkthrough\PurchaseOrder1.xml`, and then click **Save and Close**.</span></span> <span data-ttu-id="8172f-253">您現在應該可以在清單中看到檔案。</span><span class="sxs-lookup"><span data-stu-id="8172f-253">You should now be able to see the file in the list.</span></span>  
  
5.  <span data-ttu-id="8172f-254">重新整理瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="8172f-254">Refresh the browser window.</span></span> <span data-ttu-id="8172f-255">此文件庫將不會再列出 `PurchaseOrder1.xml` 檔案。</span><span class="sxs-lookup"><span data-stu-id="8172f-255">The `PurchaseOrder1.xml` file will no longer be listed in this library.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8172f-256">您可能需要重新整理瀏覽器幾次，因為輪詢間隔設定為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="8172f-256">You may have to refresh the browser a few times since the polling interval is set at 10 seconds.</span></span>  
  
6.  <span data-ttu-id="8172f-257">在上方導覽列中，按一下 **文件，並列出**。</span><span class="sxs-lookup"><span data-stu-id="8172f-257">On the top navigation bar, click **Documents and Lists**.</span></span>  
  
7.  <span data-ttu-id="8172f-258">在下**文件庫**，按一下 **目的地**。</span><span class="sxs-lookup"><span data-stu-id="8172f-258">Under **Document Libraries**, click **Destination**.</span></span>  
  
8.  <span data-ttu-id="8172f-259">在 [目的地] 文件庫中，您現在會看見已列出您的訊息。</span><span class="sxs-lookup"><span data-stu-id="8172f-259">In the Destination Document Library, you will now see your message listed.</span></span> <span data-ttu-id="8172f-260">您也可以在 [封存] 文件庫中找到封存的複本。</span><span class="sxs-lookup"><span data-stu-id="8172f-260">You will also find a copy archived in the Archive Document Library.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8172f-261">如果訊息不會出現在 [目的地] 文件庫中，請參閱 「 疑難排解 Windows SharePoint Services 配接器 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="8172f-261">If the message does not appear in the Destination Document Library, refer to "Troubleshooting the Windows SharePoint Services Adapter" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="8172f-262">摘要</span><span class="sxs-lookup"><span data-stu-id="8172f-262">Summary</span></span>  
 <span data-ttu-id="8172f-263">在本逐步解說中，您已經瞭解如何設定 Windows SharePoint Services 和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讓您可以傳送和接收訊息，使用 Windows SharePoint Services 配接器和以內容為基礎的路由 (CBR)。</span><span class="sxs-lookup"><span data-stu-id="8172f-263">In this walkthrough you have seen how to configure Windows SharePoint Services and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] so you can send and receive a message using the Windows SharePoint Services adapter and content-based routing (CBR).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8172f-264">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8172f-264">Next Steps</span></span>  
 <span data-ttu-id="8172f-265">現在您已完成此逐步解說中，執行[逐步解說： 模組 2-整合 Office 與 Windows SharePoint Services 配接器](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)逐步解說，它會展開，您完成此逐步解說並顯示與工作您如何整合 Office 與 Windows SharePoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="8172f-265">Now that you have completed this walkthrough, perform the [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) walkthrough, which expands on the work you have done with this walkthrough and shows you how to integrate Office with the Windows SharePoint Services adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8172f-266">請參閱</span><span class="sxs-lookup"><span data-stu-id="8172f-266">See Also</span></span>  
 <span data-ttu-id="8172f-267">[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="8172f-267">[What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="8172f-268">Windows SharePoint Services 配接器逐步解說</span><span class="sxs-lookup"><span data-stu-id="8172f-268">Windows SharePoint Services Adapter Walkthroughs</span></span>](../core/windows-sharepoint-services-adapter-walkthroughs.md)