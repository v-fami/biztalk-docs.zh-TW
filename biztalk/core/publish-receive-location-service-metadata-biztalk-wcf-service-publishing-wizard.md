---
title: 如何使用 BizTalk WCF 服務發佈精靈發佈之 WCF 接收位置的服務中繼資料繫結至協調流程連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF Service Publishing Wizard, publishing metadata
- WCF services, orchestration ports
- WCF services, metadata
- orchestrations, WCF services
ms.assetid: 04ccce9f-8d18-433a-8299-d06fa155db06
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7055531629ec3eadded9562d043fb8a31d7fe11e
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752455"
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-service-metadata-for-a-wcf-receive-location-bound-to-an-orchestration-port"></a><span data-ttu-id="050ba-102">如何使用 BizTalk WCF 服務發佈精靈來發佈繫結至協調流程連接埠之 WCF 接收位置的服務中繼資料</span><span class="sxs-lookup"><span data-stu-id="050ba-102">How to Use the BizTalk WCF Service Publishing Wizard to Publish Service Metadata for a WCF Receive Location Bound to an Orchestration Port</span></span>
<span data-ttu-id="050ba-103">您可以使用 BizTalk WCF 服務發佈精靈來建立 WCF 服務，以便發佈繫結至協調流程連接埠之現有 WCF 接收位置的服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="050ba-103">You use the BizTalk WCF Service Publishing Wizard to create a WCF service to publish service metadata for existing WCF receive locations bound to orchestration ports.</span></span>  

> [!NOTE]
>  <span data-ttu-id="050ba-104">您必須先建置 BizTalk 專案，然後再執行 BizTalk WCF 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="050ba-104">You must build your BizTalk projects before running the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="050ba-105">BizTalk 專案必須包括至少有一個型別修飾詞為公用之接收埠的協調流程。</span><span class="sxs-lookup"><span data-stu-id="050ba-105">The BizTalk projects must include orchestrations having at least one receive port whose type modifier is public.</span></span> <span data-ttu-id="050ba-106">發佈 WCF 配接器的服務中繼資料之前，您也必須使用 BizTalk 管理主控台或 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的 BTSTask 命令列工具來建立 WCF 接收位置。</span><span class="sxs-lookup"><span data-stu-id="050ba-106">Before you publish service metadata for the WCF adapters, you must also create the WCF receive locations by using the BizTalk Administration console or the BTSTask command-line tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="050ba-107">如需有關如何建立 WCF 接收位置，請參閱中的每個 WCF 配接器的適當主題[WCF 配接器](../core/wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="050ba-107">For more information about how to create a WCF receive location, see the appropriate topic for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>  

### <a name="to-publish-service-metadata-for-an-existing-wcf-receive-location-bound-to-an-orchestration-port"></a><span data-ttu-id="050ba-108">若要發佈繫結至協調流程連接埠之現有 WCF 接收位置的服務中繼資料</span><span class="sxs-lookup"><span data-stu-id="050ba-108">To publish service metadata for an existing WCF receive location bound to an orchestration port</span></span>  

1. <span data-ttu-id="050ba-109">按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk WCF 服務發佈精靈**。</span><span class="sxs-lookup"><span data-stu-id="050ba-109">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk WCF Service Publishing Wizard**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="050ba-110">若要建立並發佈 BizTalk 協調流程和結構描述的 WCF 服務中繼資料，您可以使用 BizTalk WCF 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="050ba-110">To create and publish WCF serve metadata for BizTalk orchestrations and schemas, you use the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="050ba-111">若要以 SOAP 配接器將協調流程和結構描述發佈成 Web 服務，您可以使用 BizTalk Web 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="050ba-111">To publish orchestrations and schemas as Web services with the SOAP adapter, you use the BizTalk Web Services Publishing Wizard.</span></span>  

2. <span data-ttu-id="050ba-112">在 [**歡迎使用 BizTalk WCF 服務發佈精靈**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="050ba-112">On the **Welcome to the BizTalk WCF Service Publishing Wizard** page, click **Next**.</span></span>  

3. <span data-ttu-id="050ba-113">在  **WCF 服務類型**頁面上，選取**中繼資料唯一端點 (MEX)** 來發佈 WCF 服務，以提供 WCF 服務中繼資料的選項接收下一個步驟中，您將選取的位置。</span><span class="sxs-lookup"><span data-stu-id="050ba-113">On the **WCF Service Type** page, select the **Metdata only endpoint (MEX)** option to publish the WCF services to provide service metadata for the WCF receive location that you will select in the next step.</span></span>  

    <span data-ttu-id="050ba-114">![WCF 服務類型 頁面](../core/media/794a85b5-6454-4cce-8c15-382b5583b0f2.gif "794a85b5-6454-4cce-8c15-382b5583b0f2")</span><span class="sxs-lookup"><span data-stu-id="050ba-114">![WCF Service Type page](../core/media/794a85b5-6454-4cce-8c15-382b5583b0f2.gif "794a85b5-6454-4cce-8c15-382b5583b0f2")</span></span>  

4. <span data-ttu-id="050ba-115">在上**WCF 服務類型**頁面上，於**發行中繼資料的接收位置**下拉式清單中，選取之 WCF 接收位置來發佈服務中繼資料，然後按一下 **下一步**.</span><span class="sxs-lookup"><span data-stu-id="050ba-115">On the **WCF Service Type** page, in the **Publish metadata for receive location** drop-down list, select a WCF receive location to publish service metadata for, and then click **Next**.</span></span>  

5. <span data-ttu-id="050ba-116">在 [**建立 WCF 服務**頁面上，選取**BizTalk 協調流程發佈為 WCF 服務**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="050ba-116">On the **Create WCF Service** page, select **Publish BizTalk orchestrations as WCF service**, and then click **Next**.</span></span>  

    <span data-ttu-id="050ba-117">![建立 WCF 服務頁面](../core/media/86cb66b5-6842-4330-8942-20afa68ec5fa.gif "86cb66b5-6842-4330-8942-20afa68ec5fa")</span><span class="sxs-lookup"><span data-stu-id="050ba-117">![Create WCF Service page](../core/media/86cb66b5-6842-4330-8942-20afa68ec5fa.gif "86cb66b5-6842-4330-8942-20afa68ec5fa")</span></span>  

6. <span data-ttu-id="050ba-118">在上**BizTalk 組件**頁面上，於**BizTalk 組件檔案 (\*.dll)** 文字方塊中，輸入 BizTalk 組件檔案的名稱，或按一下**瀏覽**瀏覽至包含的組件的協調流程以發佈服務中繼資料，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="050ba-118">On the **BizTalk Assembly** page, in the **BizTalk assembly file (\*.dll)** text box, type the name of the BizTalk assembly file or click **Browse** to browse to the assembly containing the orchestration(s) to publish service metadata for, and then click **Next**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="050ba-119">選取 BizTalk 組件檔案之前，請將所有相依組件與 BizTalk 組件複製到相同的資料夾中，或將這些相依組件安裝至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="050ba-119">Before selecting a BizTalk assembly file, copy all of the dependent assemblies into the same folder with the BizTalk assembly or install the dependent assemblies to the global assembly cache (GAC).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="050ba-120">如果您在 gac 中安裝 BizTalk 組件檔案，請確定 GAC 中的組件，已更新的組件中選取**BizTalk 組件** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="050ba-120">If you installed the BizTalk assembly file into the GAC, make sure that the assembly in the GAC has been updated with the assembly that you will select in the **BizTalk Assembly** dialog box.</span></span> <span data-ttu-id="050ba-121">如果 GAC 中的組件具有相同的完整格式名稱，BizTalk WCF 服務發佈精靈就會使用 GAC 中的組件檔案，而非您所選取的組件檔案。</span><span class="sxs-lookup"><span data-stu-id="050ba-121">If the assembly in the GAC has the same fully qualified name, the BizTalk WCF Service Publishing Wizard uses the assembly file in the GAC instead of the one you selected.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="050ba-122">長度超過 260 個字元的路徑可能會導致路徑太長的錯誤訊息出現。</span><span class="sxs-lookup"><span data-stu-id="050ba-122">Paths over 260 characters long may cause an error message that the path is too long.</span></span>  

    <span data-ttu-id="050ba-123">![BizTalk 組件頁面](../core/media/d34a027e-ea82-4048-8b15-d97df795b0d4.gif "d34a027e-ea82-4048-8b15-d97df795b0d4")</span><span class="sxs-lookup"><span data-stu-id="050ba-123">![BizTalk Assembly page](../core/media/d34a027e-ea82-4048-8b15-d97df795b0d4.gif "d34a027e-ea82-4048-8b15-d97df795b0d4")</span></span>  

7. <span data-ttu-id="050ba-124">在 **協調流程和連接埠**頁面上，依序按一下加號 （+） 展開每個組件和協調流程的樹狀節點。</span><span class="sxs-lookup"><span data-stu-id="050ba-124">On the **Orchestrations and Ports** page, expand the tree nodes for each assembly and orchestration by clicking the plus sign (+).</span></span> <span data-ttu-id="050ba-125">透過選取對應樹狀節點的核取方塊，選取要發佈中繼資料的協調流程和連接埠。</span><span class="sxs-lookup"><span data-stu-id="050ba-125">Select orchestrations and ports to publish metadata for by selecting the corresponding tree node check boxes.</span></span> <span data-ttu-id="050ba-126">如果您想要建立一個 WCF 服務 （.svc 檔案） 的所有選取的接收埠，而不是一個 WCF 服務，每個接收埠，請選取**所有選取的連接埠合併成單一 WCF 服務**選項，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="050ba-126">If you want to create one WCF service (.svc file) for all of the selected receive ports instead of one WCF service for each receive port, select the **Merge all selected ports into a single WCF service** option, and then click **Next**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="050ba-127">當您將所有選取的連接埠合併成單一 WCF 服務時，所有選取的連接埠都會具有相同的連接埠類型，而且這些連接埠中的作業名稱都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="050ba-127">When you merge all selected ports into a single WCF service, all of the selected ports have the same port type, and the operation names in the ports are unique.</span></span>  

    <span data-ttu-id="050ba-128">![作業和連接埠 頁面](../core/media/97112744-ddd4-4512-ac56-41317ba9412b.gif "97112744-ddd4-4512-ac56-41317ba9412b")</span><span class="sxs-lookup"><span data-stu-id="050ba-128">![Operations and Ports page](../core/media/97112744-ddd4-4512-ac56-41317ba9412b.gif "97112744-ddd4-4512-ac56-41317ba9412b")</span></span>  

8. <span data-ttu-id="050ba-129">在上**WCF 服務屬性**頁面上，於**的 WCF 服務的 Targetnamespace**文字方塊中輸入 WCF 服務的目標命名空間，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="050ba-129">On the **WCF Service Properties** page, in the **Targetnamespace of the WCF service** text box, type a target namespace for the WCF services, and then click **Next**.</span></span>  

    <span data-ttu-id="050ba-130">![WCF 服務屬性頁](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")</span><span class="sxs-lookup"><span data-stu-id="050ba-130">![WCF Service Properties page](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")</span></span>  

9. <span data-ttu-id="050ba-131">在  **WCF 服務位置**頁面上，於**位置**文字方塊中，輸入產生 WCF 服務位置的 Web 目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="050ba-131">On the **WCF Service Location** page, in the **Location** text box, type the Web directory name where the WCF services are generated.</span></span> <span data-ttu-id="050ba-132">您可以接受預設位置 (`http://localhost/<BizTalk Assembly Name>`)，輸入中的 WCF 服務的位置**位置**文字方塊中或按一下 **瀏覽**並選取 Web 目錄。</span><span class="sxs-lookup"><span data-stu-id="050ba-132">You can accept the default location (`http://localhost/<BizTalk Assembly Name>`), type a location for the WCF services in the **Location** text box, or click **Browse** and select a Web directory.</span></span> <span data-ttu-id="050ba-133">接著，選取下列任何一個選項：</span><span class="sxs-lookup"><span data-stu-id="050ba-133">Select any of the following options:</span></span>  

   - <span data-ttu-id="050ba-134">**覆寫現有的專案。**</span><span class="sxs-lookup"><span data-stu-id="050ba-134">**Overwrite existing project.**</span></span> <span data-ttu-id="050ba-135">此選項只有在 Web 目錄已存在時才能使用。</span><span class="sxs-lookup"><span data-stu-id="050ba-135">This option is available only if the Web directory already exists.</span></span> <span data-ttu-id="050ba-136">只有當您選取了這個選項時，才能夠發佈至相同的位置。</span><span class="sxs-lookup"><span data-stu-id="050ba-136">You will be able to publish to the same location only if you select this option.</span></span> <span data-ttu-id="050ba-137">否則，您必須輸入不同的專案位置。</span><span class="sxs-lookup"><span data-stu-id="050ba-137">Otherwise, you must enter a different project location.</span></span>  

   - <span data-ttu-id="050ba-138">**允許匿名存取 WCF 服務。**</span><span class="sxs-lookup"><span data-stu-id="050ba-138">**Allow anonymous access to WCF service.**</span></span> <span data-ttu-id="050ba-139">這個選項會新增已建立之虛擬目錄的匿名存取。</span><span class="sxs-lookup"><span data-stu-id="050ba-139">This option adds anonymous access to the created virtual directory.</span></span> <span data-ttu-id="050ba-140">根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。</span><span class="sxs-lookup"><span data-stu-id="050ba-140">By default, the virtual directory inherits the access privileges from its parent virtual directory or the Web site (if it is a top-level virtual directory).</span></span>  

     <span data-ttu-id="050ba-141">當您完成這個頁面上時，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="050ba-141">When you finish this page, click **Next**.</span></span>  

     <span data-ttu-id="050ba-142">![WCF 服務位置頁面](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")</span><span class="sxs-lookup"><span data-stu-id="050ba-142">![WCF Service location page](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")</span></span>  

     > [!NOTE]
     >  <span data-ttu-id="050ba-143">專案位置可以存在不同的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="050ba-143">The project location can exist on a different server.</span></span> <span data-ttu-id="050ba-144">若要將 WCF 服務發佈到另一部伺服器中，輸入 專案名稱，做為`http://<servername>/<WCF service location>`。</span><span class="sxs-lookup"><span data-stu-id="050ba-144">To publish the WCF services to a different server, type the project name as `http://<servername>/<WCF service location>`.</span></span>  

     > [!NOTE]
     >  <span data-ttu-id="050ba-145">專案位置可以存在非預設的網站上。</span><span class="sxs-lookup"><span data-stu-id="050ba-145">The project location can exist on a non-default Web site.</span></span> <span data-ttu-id="050ba-146">發佈至非預設的網站時，請在 URL 中加入網站的連接埠編號。</span><span class="sxs-lookup"><span data-stu-id="050ba-146">When publishing to a non-default Web site, include the port number of the Web site in the URL.</span></span> <span data-ttu-id="050ba-147">例如， `http://<servername>:8080/<WCF service location>` 。</span><span class="sxs-lookup"><span data-stu-id="050ba-147">For example, `http://<servername>:8080/<WCF service location>`.</span></span>  

     > [!NOTE]
     >  <span data-ttu-id="050ba-148">App_DataTemp 資料夾中的 Web 應用程式精靈所建立的 BindingInfo.xml 檔案會用於管線中的預設值。</span><span class="sxs-lookup"><span data-stu-id="050ba-148">The BindingInfo.xml file that the wizard creates in the App_DataTemp folder of the Web application uses the default values for the pipelines.</span></span> <span data-ttu-id="050ba-149">接收管線的預設值是**Microsoft.BizTalk.DefaultPipelines.XMLReceive**管線，而且預設值的傳送管線是**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**管線。</span><span class="sxs-lookup"><span data-stu-id="050ba-149">The default value for the receive pipeline is the **Microsoft.BizTalk.DefaultPipelines.XMLReceive** pipeline, and the default value for the send pipeline is the **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit** pipeline.</span></span>  

10. <span data-ttu-id="050ba-150">在  **WCF 服務摘要**頁面上，檢閱您的 WCF 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="050ba-150">On the **WCF Service Summary** page, review your settings for the WCF services.</span></span>  

11. <span data-ttu-id="050ba-151">按一下 **建立**以建立 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="050ba-151">Click **Create** to create the WCF services.</span></span>  

12. <span data-ttu-id="050ba-152">按一下 **完成**完成 BizTalk WCF 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="050ba-152">Click **Finish** to complete the BizTalk WCF Service Publishing Wizard.</span></span>  

### <a name="to-configure-the-web-application-for-publishing-service-metadata"></a><span data-ttu-id="050ba-153">若要設定發佈服務中繼資料的 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="050ba-153">To configure the Web application for publishing service metadata</span></span>  

1. <span data-ttu-id="050ba-154">針對 BizTalk WCF 服務發佈精靈所建立的 Web 應用程式啟用 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="050ba-154">Enable ASP.NET for the Web application that the BizTalk WCF Service Publishing Wizard created.</span></span> <span data-ttu-id="050ba-155">如需詳細資訊，請參閱 <<c0> [ 啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="050ba-155">For more information, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="050ba-156">如果您正使用 Windows Server 2008 或 Windows Vista，就必須將應用程式集區的識別帳戶新增至 BizTalk Server Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="050ba-156">If you are using Windows Server 2008 or Windows Vista, you must add the Identity Account of the Application Pool to the BizTalk Server Administrators group.</span></span> <span data-ttu-id="050ba-157">將適當的帳戶新增至 BizTalk Server 系統管理員群組之後，您必須重新啟動 IIS 服務，才能讓設定生效。</span><span class="sxs-lookup"><span data-stu-id="050ba-157">After you add the appropriate account to the BizTalk Server Administrators group, you need to restart the IIS service fro the setting to take effect.</span></span>  

2. <span data-ttu-id="050ba-158">開啟命令提示字元，請移至 BizTalk WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 資料夾\\，然後開啟 Web.config 檔案，使用 記事本。</span><span class="sxs-lookup"><span data-stu-id="050ba-158">Open a command prompt, go to the folder where the BizTalk WCF Service Publishing Wizard created the WCF services in %SystemDrive%\InetPub\\, and then open the Web.config file using Notepad.</span></span>  

3. <span data-ttu-id="050ba-159">在記事本中，加入下的面這一行內**\<system.web\>** 項目：</span><span class="sxs-lookup"><span data-stu-id="050ba-159">In Notepad, add the following line inside the **\<system.web\>** element:</span></span>  

   ```  
   <trust level="Full" originUrl="" />  
   ```  

   > [!NOTE]
   >  <span data-ttu-id="050ba-160">這項設定是選擇性的，而且它會將受限於作業系統安全性之任何資源的存取權授與主控已發佈之 WCF 服務的 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="050ba-160">This setting is optional and it grants the ASP.NET application hosting the published WCF service access to any resource that is subject to operating system security.</span></span> <span data-ttu-id="050ba-161">當您在同一部電腦上安裝和執行 Windows SharePoint Services 以及已發佈的 WCF 服務時，這就是 WCF 所需的信任層級。</span><span class="sxs-lookup"><span data-stu-id="050ba-161">This is the trust level that WCF requires when you have Windows SharePoint Services installed and running on the same machine with the published WCF services.</span></span>  

4. <span data-ttu-id="050ba-162">在 Internet Explorer 中**地址**方塊中，輸入 WCF 服務使用格式 http:// URL<em>主控件 [: 連接埠]</em>/*apppath* /*wcfservicename.svc*來測試已發佈的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="050ba-162">In Internet Explorer, in the **Address** box, type the URL for the WCF service using the format http://<em>host[:port]</em>/*apppath*/*wcfservicename.svc* to test the published WCF service.</span></span> <span data-ttu-id="050ba-163">下表將描述這些參數。</span><span class="sxs-lookup"><span data-stu-id="050ba-163">The parameters are described in the following table.</span></span>  


   |      <span data-ttu-id="050ba-164">參數</span><span class="sxs-lookup"><span data-stu-id="050ba-164">Parameter</span></span>       |                                                            <span data-ttu-id="050ba-165">值</span><span class="sxs-lookup"><span data-stu-id="050ba-165">Value</span></span>                                                            |
   |----------------------|-----------------------------------------------------------------------------------------------------------------------------|
   |    <span data-ttu-id="050ba-166">*主控件 [: 連接埠]*</span><span class="sxs-lookup"><span data-stu-id="050ba-166">*host[:port]*</span></span>     | <span data-ttu-id="050ba-167">您已部署 WCF 服務之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="050ba-167">The name of the computer where you have deployed your WCF service.</span></span> <span data-ttu-id="050ba-168">冒號和連接埠編號可以接在這個伺服器名稱後面。</span><span class="sxs-lookup"><span data-stu-id="050ba-168">A colon and the port number can follow this server name.</span></span> |
   |      <span data-ttu-id="050ba-169">*apppath*</span><span class="sxs-lookup"><span data-stu-id="050ba-169">*apppath*</span></span>       |                              <span data-ttu-id="050ba-170">虛擬目錄的名稱和 Web 應用程式路徑。</span><span class="sxs-lookup"><span data-stu-id="050ba-170">The name of your virtual directory and the Web application path.</span></span>                               |
   | <span data-ttu-id="050ba-171">*wcfservicename.svc*</span><span class="sxs-lookup"><span data-stu-id="050ba-171">*wcfservicename.svc*</span></span> |                                           <span data-ttu-id="050ba-172">WCF 服務 .svc 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="050ba-172">The name of the WCF service .svc file.</span></span>                                            |


5. <span data-ttu-id="050ba-173">為了避免不小心洩露可能含有機密的服務中繼資料，我們建議您透過執行下列工作，在實際執行環境中停用這種行為：</span><span class="sxs-lookup"><span data-stu-id="050ba-173">To prevent unintentional disclosure of potentially sensitive service metadata, we recommend that you disable this behavior in the production environment by performing the following tasks:</span></span>  

   1.  <span data-ttu-id="050ba-174">在 記事本 開啟 BizTalk WCF 服務發佈精靈建立 WCF 服務中 %SystemDrive%\InetPub 的資料夾中的 Web.config\\。</span><span class="sxs-lookup"><span data-stu-id="050ba-174">In Notepad, open Web.config in the folder where the BizTalk WCF Service Publishing Wizard created the WCF service in %SystemDrive%\InetPub\\.</span></span>  

   2.  <span data-ttu-id="050ba-175">在記事本中，設定**httpGetEnabled**屬性中**\<serviceMetadata\>** 設為 false，如同下面這一行的項目：</span><span class="sxs-lookup"><span data-stu-id="050ba-175">In Notepad, set the **httpGetEnabled** attribute in the  **\<serviceMetadata\>** element to false as in the following line:</span></span>  

       ```  
       <serviceMetadata httpGetEnabled="false" httpsGetEnabled="false" />  
       ```  

## <a name="see-also"></a><span data-ttu-id="050ba-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="050ba-176">See Also</span></span>  
 <span data-ttu-id="050ba-177">[如何使用 BizTalk WCF 服務發佈精靈發佈之 WCF 接收位置的內容型路由的服務中繼資料](../core/publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing.md) </span><span class="sxs-lookup"><span data-stu-id="050ba-177">[How to Use the BizTalk WCF Service Publishing Wizard to Publish Service Metadata for a WCF Receive Location for Content-Based Routing](../core/publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing.md) </span></span>  
 [<span data-ttu-id="050ba-178">逐步解說：使用 WCF-NetMsmq 配接器發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="050ba-178">Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter</span></span>](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)