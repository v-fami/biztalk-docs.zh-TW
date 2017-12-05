---
title: "如何使用 BizTalk WCF 服務發佈精靈協調流程發佈為 WCF 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tools, WCF Service Publishing Wizard
- WCF services, WCF Service Publishing Wizard
- WCF services, orchestrations
- publishing, orchestrations [WCF services]
- orchestrations, WCF services
- WCF Service Publishing Wizard
ms.assetid: db352132-2fe8-4d53-b239-45e5c3525b6c
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76e233cfdd0871b55776cdf7cbaa9ee5b2af2724
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-orchestrations-as-wcf-services"></a><span data-ttu-id="13eca-102">如何使用 BizTalk WCF 服務發佈精靈將協調流程發佈為 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="13eca-102">How to Use the BizTalk WCF Service Publishing Wizard to Publish Orchestrations as WCF Services</span></span>
<span data-ttu-id="13eca-103">您可以使用 [BizTalk WCF 服務發佈精靈] 將協調流程發佈為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="13eca-103">You use the BizTalk WCF Service Publishing Wizard to publish orchestrations as WCF services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13eca-104">您必須先建置 BizTalk 專案，然後再執行 BizTalk WCF 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="13eca-104">You must build your BizTalk projects before running the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="13eca-105">BizTalk 專案必須包括至少有一個型別修飾詞為公用之接收埠的協調流程。</span><span class="sxs-lookup"><span data-stu-id="13eca-105">The BizTalk projects must include orchestrations having at least one receive port whose type modifier is public.</span></span> <span data-ttu-id="13eca-106">當連接埠建立時，這個類型修飾詞會存在協調流程的屬性中。</span><span class="sxs-lookup"><span data-stu-id="13eca-106">This type modifier exists in the properties for the orchestration when the port is created.</span></span>  
  
### <a name="to-publish-an-orchestration-as-a-wcf-service"></a><span data-ttu-id="13eca-107">若要將協調流程發佈為 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="13eca-107">To publish an orchestration as a WCF service</span></span>  
  
1.  <span data-ttu-id="13eca-108">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，然後按一下  **BizTalk WCF 服務發佈精靈**。</span><span class="sxs-lookup"><span data-stu-id="13eca-108">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then click **BizTalk WCF Service Publishing Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-109">您可以使用 [BizTalk WCF 服務發佈精靈] 來建立 BizTalk 協調流程和結構描述，並使用 WCF 配接器將它們發佈為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="13eca-109">To create and publish BizTalk orchestrations and schemas as WCF services with the WCF adapters, you use the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="13eca-110">若要以 SOAP 配接器將協調流程和結構描述發佈成 Web 服務，您可以使用 BizTalk Web 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="13eca-110">To publish orchestrations and schemas as Web services with the SOAP adapter, you use the BizTalk Web Services Publishing Wizard.</span></span>  
  
2.  <span data-ttu-id="13eca-111">在**歡迎使用 BizTalk WCF 服務發佈精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="13eca-111">On the **Welcome to the BizTalk WCF Service Publishing Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="13eca-112">在**WCF 服務類型**頁面上，選取**服務端點**BizTalk 組件中選取 BizTalk 協調流程上發佈 WCF 服務的選項。</span><span class="sxs-lookup"><span data-stu-id="13eca-112">On the **WCF Service Type** page, select **Service endpoint** option to publish the WCF services on selected BizTalk orchestrations in a BizTalk assembly.</span></span>  
  
     <span data-ttu-id="13eca-113">![WCF 服務類型 頁面上](../core/media/959900fd-44c9-4f3a-8836-9786a2f5e707.gif "959900fd-44c9-4f3a-8836-9786a2f5e707")</span><span class="sxs-lookup"><span data-stu-id="13eca-113">![WCF Service Type page](../core/media/959900fd-44c9-4f3a-8836-9786a2f5e707.gif "959900fd-44c9-4f3a-8836-9786a2f5e707")</span></span>  
  
4.  <span data-ttu-id="13eca-114">在**WCF 服務類型**頁面上，選取**啟用中繼資料端點**核取方塊以指出外掛式的 WCF 接收位置網際網路資訊服務 (IIS) 裝載是否發行服務中繼資料使用 HTTP/GET 要求擷取。</span><span class="sxs-lookup"><span data-stu-id="13eca-114">On the **WCF Service Type** page, select **Enable metadata endpoint** check-box to indicate whether the isolated WCF receive location hosted by Internet Information Services (IIS) publish service metadata for retrieval using an HTTP/GET request.</span></span> <span data-ttu-id="13eca-115">啟用此核取方塊，精靈便會產生 Web.config 其中**httpGetEnabled**屬性 **\<serviceMetadata\>** 元素設定為**，則為 true**.</span><span class="sxs-lookup"><span data-stu-id="13eca-115">By enabling this check-box, the wizard generates Web.config where the **httpGetEnabled** attribute of the **\<serviceMetadata\>** element is set to **true**.</span></span> <span data-ttu-id="13eca-116">您可以在開發環境中使用中繼資料匯入工具 (例如 SvcUtil.exe) 產生呼叫此服務所需的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="13eca-116">You can use a metadata import tool (such as SvcUtil.exe) to generate the client code required to call this service in the development environment.</span></span> <span data-ttu-id="13eca-117">中繼資料發行的位址是端點位址加上一個**？ wsdl**查詢字串。</span><span class="sxs-lookup"><span data-stu-id="13eca-117">The address at which the metadata is published is the endpoint address plus a **?wsdl** query string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-118">為避免不慎洩露較為機密的服務中繼資料，建議您在實際執行環境中停用此行為。</span><span class="sxs-lookup"><span data-stu-id="13eca-118">To prevent unintentional disclosure of potentially sensitive service metadata, it is recommended to disable this behavior on the production environment.</span></span> <span data-ttu-id="13eca-119">這可透過將 httpgetenabled 設為 False 或刪除 MEX 虛擬目錄來完成。</span><span class="sxs-lookup"><span data-stu-id="13eca-119">This can be done by setting httpgetenabled to false, or deleting the MEX virtual directory.</span></span>  
  
5.  <span data-ttu-id="13eca-120">在**WCF 服務類型**頁面上，於**配接器名稱 （傳輸類型）**下拉式清單中，選取要用來發佈 WCF 服務的外掛式的 WCF 配接器。</span><span class="sxs-lookup"><span data-stu-id="13eca-120">On the **WCF Service Type** page, in the **Adapter name (Transport type)** drop-down list, select the isolated WCF adapter with which the WCF services are published.</span></span> <span data-ttu-id="13eca-121">您可以選取下列任何一個配接器：</span><span class="sxs-lookup"><span data-stu-id="13eca-121">You can select any of the following adapters:</span></span>  
  
    -   <span data-ttu-id="13eca-122">**Wcf-basichttp。**</span><span class="sxs-lookup"><span data-stu-id="13eca-122">**WCF-BasicHttp.**</span></span> <span data-ttu-id="13eca-123">WCF-BasicHttp 配接器可以與 WS-I 基本設定檔 1.1 相符的 Web 服務 (例如以 ASMX 為基礎的服務) 通訊。</span><span class="sxs-lookup"><span data-stu-id="13eca-123">The WCF-BasicHttp adapter can communicate with WS-I Basic Profile 1.1-conformant Web services like ASMX-based services.</span></span>  
  
    -   <span data-ttu-id="13eca-124">**Wcf-wshttp。**</span><span class="sxs-lookup"><span data-stu-id="13eca-124">**WCF-WSHttp.**</span></span> <span data-ttu-id="13eca-125">WCF-WSHttp 配接器可以透過 HTTP 和 HTTPS 上的 WS-* 標準，與服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="13eca-125">The WCF-WSHttp adapter can communicate with a service through the WS-* standards over HTTP and HTTPS.</span></span>  
  
    -   <span data-ttu-id="13eca-126">**Wcf-customisolated。**</span><span class="sxs-lookup"><span data-stu-id="13eca-126">**WCF-CustomIsolated.**</span></span> <span data-ttu-id="13eca-127">WCF-CustomIsolated 配接器可以在 HTTP 傳輸上啟用 Windows Communication Foundation (WCF) 擴充性功能。</span><span class="sxs-lookup"><span data-stu-id="13eca-127">The WCF-CustomIsolated adapter enables the use of Windows Communication Foundation (WCF) extensibility features over the HTTP transport.</span></span>  
  
6.  <span data-ttu-id="13eca-128">在**WCF 服務類型**頁面上，選取**下列應用程式中的建立 BizTalk 接收位置**核取方塊來建立接收埠與對應於每個產生的.svc 檔案的位置您在選取的 WCF 配接器**配接器名稱**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="13eca-128">On the **WCF Service Type** page, select the **Create BizTalk receive locations in the following application** check-box to create the receive ports and locations corresponding to each generated .svc file for the WCF adapter that you selected in the **Adapter name** drop-down list.</span></span> <span data-ttu-id="13eca-129">如果接收位置已經存在，則不會取代該接收位置。</span><span class="sxs-lookup"><span data-stu-id="13eca-129">If a receive location already exists, it is not replaced.</span></span> <span data-ttu-id="13eca-130">選取此選項之後，選擇 應用程式，其中的接收埠和位置將會產生在**BizTalk 應用程式名稱**下拉式清單，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="13eca-130">After selecting this option, choose the application where the receive ports and locations will be generated in the **BizTalk application name** drop-down list, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="13eca-131">在**建立 WCF 服務**頁面上，選取**BizTalk 協調流程發佈為 WCF 服務**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="13eca-131">On the **Create WCF Service** page, select **Publish BizTalk orchestrations as WCF service**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="13eca-132">![建立 WCF 服務頁面](../core/media/86cb66b5-6842-4330-8942-20afa68ec5fa.gif "86cb66b5-6842-4330-8942-20afa68ec5fa")</span><span class="sxs-lookup"><span data-stu-id="13eca-132">![Create WCF Service page](../core/media/86cb66b5-6842-4330-8942-20afa68ec5fa.gif "86cb66b5-6842-4330-8942-20afa68ec5fa")</span></span>  
  
8.  <span data-ttu-id="13eca-133">在**BizTalk 組件**頁面上，於**BizTalk 組件檔案 (\*.dll)**文字方塊中，輸入 BizTalk 組件檔案的名稱，或按一下**瀏覽**瀏覽至包含的組件協調流程來發行，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="13eca-133">On the **BizTalk Assembly** page, in the **BizTalk assembly file (\*.dll)** text box, type the name of the BizTalk assembly file or click **Browse** to browse to the assembly containing the orchestration(s) to publish, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-134">選擇 BizTalk 組件檔案之前，請將所有相依的組件複製到與 BizTalk 組件相同的資料夾中，或將這些相依組件安裝至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="13eca-134">Before choosing a BizTalk assembly file, copy all of the dependent assemblies into the same folder with the BizTalk assembly or install the dependent assemblies to the global assembly cache (GAC).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-135">如果您安裝到 GAC 的 BizTalk 組件檔案，請確定您會在選取的組件，已更新組件在 GAC 中的**BizTalk 組件** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="13eca-135">If you installed the BizTalk assembly file into the GAC, make sure that the assembly in the GAC has been updated with the assembly that you will select in the **BizTalk Assembly** dialog box.</span></span> <span data-ttu-id="13eca-136">如果 GAC 中的組件具有相同的完整格式名稱，BizTalk WCF 服務發佈精靈就會使用 GAC 中的組件檔案，而非您所選取的組件檔案。</span><span class="sxs-lookup"><span data-stu-id="13eca-136">If the assembly in the GAC has the same fully qualified name, the BizTalk WCF Service Publishing Wizard uses the assembly file in the GAC instead of the one you selected.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-137">長度超過 260 個字元的路徑可能會導致路徑太長的錯誤訊息出現。</span><span class="sxs-lookup"><span data-stu-id="13eca-137">Paths over 260 characters long may cause an error message that the path is too long.</span></span>  
  
     <span data-ttu-id="13eca-138">![BizTalk 組件頁面](../core/media/d34a027e-ea82-4048-8b15-d97df795b0d4.gif "d34a027e-ea82-4048-8b15-d97df795b0d4")</span><span class="sxs-lookup"><span data-stu-id="13eca-138">![BizTalk Assembly page](../core/media/d34a027e-ea82-4048-8b15-d97df795b0d4.gif "d34a027e-ea82-4048-8b15-d97df795b0d4")</span></span>  
  
9. <span data-ttu-id="13eca-139">在**協調流程和連接埠**頁面上，按一下加號 （+） 展開每個組件和協調流程的樹狀節點。</span><span class="sxs-lookup"><span data-stu-id="13eca-139">On the **Orchestrations and Ports** page, expand the tree nodes for each assembly and orchestration by clicking the plus sign (+).</span></span> <span data-ttu-id="13eca-140">透過選取對應樹狀節點的核取方塊，選取要發佈的協調流程和連接埠。</span><span class="sxs-lookup"><span data-stu-id="13eca-140">Select orchestrations and ports to publish by selecting the corresponding tree node check boxes.</span></span> <span data-ttu-id="13eca-141">如果您想要建立一個 WCF 服務 （.svc 檔案） 的所有選取的接收埠，而不是一個 WCF 服務，每個接收埠，請選取**所有選取的連接埠合併成單一 WCF 服務**選項，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="13eca-141">If you want to create one WCF service (.svc file) for all of the selected receive ports instead of one WCF service for each receive port, select the **Merge all selected ports into a single WCF service** option, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-142">當您將所有選取的連接埠合併成單一 WCF 服務時，所有選取的連接埠都會具有相同的連接埠類型，而且這些連接埠中的作業名稱都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="13eca-142">When you merge all selected ports into a single WCF service, all of the selected ports have the same port type, and the operation names in the ports are unique.</span></span>  
  
     <span data-ttu-id="13eca-143">![作業和連接埠頁面](../core/media/97112744-ddd4-4512-ac56-41317ba9412b.gif "97112744-ddd4-4512-ac56-41317ba9412b")</span><span class="sxs-lookup"><span data-stu-id="13eca-143">![Operations and Ports page](../core/media/97112744-ddd4-4512-ac56-41317ba9412b.gif "97112744-ddd4-4512-ac56-41317ba9412b")</span></span>  
  
10. <span data-ttu-id="13eca-144">在**WCF 服務屬性**頁面上，於**WCF 服務的 Targetnamespace**  文字方塊中，輸入 WCF 服務的目標命名空間，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="13eca-144">On the **WCF Service Properties** page, in the **Targetnamespace of the WCF service** text box, type a target namespace for the WCF services, and then click **Next**.</span></span>  
  
     <span data-ttu-id="13eca-145">![WCF 服務屬性頁面](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")</span><span class="sxs-lookup"><span data-stu-id="13eca-145">![WCF Service Properties page](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")</span></span>  
  
11. <span data-ttu-id="13eca-146">在**WCF 服務位置**頁面上，於**位置**文字方塊中，輸入產生 WCF 服務位置的 Web 目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="13eca-146">On the **WCF Service Location** page, in the **Location** text box, type the Web directory name where the WCF services are generated.</span></span> <span data-ttu-id="13eca-147">您可以接受預設位置 (http://localhost/ <*BizTalk 組件名稱*>)，輸入中的 WCF 服務的位置**位置**文字方塊中或按一下**瀏覽**，並選取 Web 目錄。</span><span class="sxs-lookup"><span data-stu-id="13eca-147">You can accept the default location (http://localhost/<*BizTalk Assembly Name*>), type a location for the WCF services in the **Location** text box, or click **Browse** and select a Web directory.</span></span> <span data-ttu-id="13eca-148">接著，選取下列任何一個選項：</span><span class="sxs-lookup"><span data-stu-id="13eca-148">Select any of the following options:</span></span>  
  
    -   <span data-ttu-id="13eca-149">**覆寫現有的專案。**</span><span class="sxs-lookup"><span data-stu-id="13eca-149">**Overwrite existing project.**</span></span> <span data-ttu-id="13eca-150">這個選項只有在 Web 目錄已經存在時才能使用。</span><span class="sxs-lookup"><span data-stu-id="13eca-150">This option is only available if the Web directory already exists.</span></span> <span data-ttu-id="13eca-151">只有當您選取了這個選項時，才能夠發佈至相同的位置。</span><span class="sxs-lookup"><span data-stu-id="13eca-151">You will be able to publish to the same location only if you select this option.</span></span> <span data-ttu-id="13eca-152">否則，您必須輸入不同的專案位置。</span><span class="sxs-lookup"><span data-stu-id="13eca-152">Otherwise, you must enter a different project location.</span></span>  
  
    -   <span data-ttu-id="13eca-153">**允許匿名存取 WCF 服務。**</span><span class="sxs-lookup"><span data-stu-id="13eca-153">**Allow anonymous access to WCF service.**</span></span> <span data-ttu-id="13eca-154">這個選項會新增已建立之虛擬目錄的匿名存取。</span><span class="sxs-lookup"><span data-stu-id="13eca-154">This option adds anonymous access to the created virtual directory.</span></span> <span data-ttu-id="13eca-155">根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。</span><span class="sxs-lookup"><span data-stu-id="13eca-155">By default, the virtual directory inherits the access privileges from its parent virtual directory or the Web site (if it is a top-level virtual directory).</span></span>  
  
     <span data-ttu-id="13eca-156">當您完成這個頁面上時，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="13eca-156">When you finish this page, click **Next**.</span></span>  
  
     <span data-ttu-id="13eca-157">![WCF 服務位置頁面](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")</span><span class="sxs-lookup"><span data-stu-id="13eca-157">![WCF Service location page](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-158">專案位置可以存在不同的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="13eca-158">The project location can exist on a different server.</span></span> <span data-ttu-id="13eca-159">若要將 WCF 服務發佈到另一部伺服器中，輸入專案名稱做為 http://&lt*servername*>/<*WCF 服務位置*>。</span><span class="sxs-lookup"><span data-stu-id="13eca-159">To publish the WCF services to a different server, type the project name as http://<*servername*>/<*WCF service location*>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-160">專案位置可以存在非預設的網站上。</span><span class="sxs-lookup"><span data-stu-id="13eca-160">The project location can exist on a non-default Web site.</span></span> <span data-ttu-id="13eca-161">發佈至非預設的網站時，請在 URL 中加入網站的連接埠編號。</span><span class="sxs-lookup"><span data-stu-id="13eca-161">When publishing to a non-default Web site, include the port number of the Web site in the URL.</span></span> <span data-ttu-id="13eca-162">例如，http://&lt*servername*>: 8080 / <*WCF 服務位置*>。</span><span class="sxs-lookup"><span data-stu-id="13eca-162">For example, http://<*servername*>:8080/<*WCF service location*>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-163">在使用精靈建立接收位置時，精靈會使用預設值來建立接收位置。</span><span class="sxs-lookup"><span data-stu-id="13eca-163">When using the wizard to create receive locations, the wizard creates the receive locations using the default values.</span></span> <span data-ttu-id="13eca-164">接收管線的預設值是**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**管線。</span><span class="sxs-lookup"><span data-stu-id="13eca-164">The default value for the receive pipeline is the **Microsoft.BizTalk.DefaultPipelines.PassThruReceive** pipeline.</span></span> <span data-ttu-id="13eca-165">如果透過已發佈的 WCF 服務收到的訊息需要任何特殊管線處理 （例如，驗證、 相互關聯/屬性升級或輸入/輸出對應），則您應該設定接收管線**Microsoft.BizTalk.DefaultPipelines.XMLReceive**，或自訂管線，使用 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="13eca-165">If messages received through the published WCF services require any special pipeline processing (for example, validation, correlation/property promotion, or inbound/outbound maps) then you should set the receive pipeline to **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, or to a custom pipeline, using the BizTalk Server Administration console.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13eca-166">如果您決定不要使用**協調流程發佈為 WCF 服務**選項之後，您在到達此頁面上，**建立 WCF 服務**頁面上，您可能會看到的**Web 服務描述** BizTalk 組件之前您所選取的服務和方法名稱的顯示變更發佈選項。</span><span class="sxs-lookup"><span data-stu-id="13eca-166">If you decide not to use the **Publishing orchestration as WCF service** option after you reach this page, on the **Create WCF Service** page, you may see that the **Web service description** displays the service and method names from the BizTalk assembly that you selected before you changed the publishing option.</span></span> <span data-ttu-id="13eca-167">這是因為發佈方法變更時，記憶體中的 Web 服務描述並未清除。</span><span class="sxs-lookup"><span data-stu-id="13eca-167">This is because the in-memory Web service description is not cleared when the publishing method is changed.</span></span>  
  
12. <span data-ttu-id="13eca-168">在**WCF 服務摘要**頁面上，檢閱您的 WCF 服務的設定。</span><span class="sxs-lookup"><span data-stu-id="13eca-168">On the **WCF Service Summary** page, review your settings for the WCF services.</span></span>  
  
13. <span data-ttu-id="13eca-169">按一下**建立**建立 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="13eca-169">Click **Create** to create the WCF services.</span></span>  
  
14. <span data-ttu-id="13eca-170">按一下**完成**完成 BizTalk WCF 服務發佈精靈。</span><span class="sxs-lookup"><span data-stu-id="13eca-170">Click **Finish** to complete the BizTalk WCF Service Publishing Wizard.</span></span>  
  
15. <span data-ttu-id="13eca-171">在使用 [BizTalk WCF 服務發佈精靈] 發佈 WCF 服務之後，您還必須適當設定這些服務。</span><span class="sxs-lookup"><span data-stu-id="13eca-171">After publishing WCF services with the BizTalk WCF Service Publishing Wizard, you must configure them properly.</span></span> <span data-ttu-id="13eca-172">如需有關如何設定外掛式的 WCF 接收配接器，請參閱[如何使用 BizTalk WCF 服務發佈精靈設定 WCF 服務發佈](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="13eca-172">For information about how to configure the isolated WCF receive adapter, see [How to Configure WCF Services Published with the BizTalk WCF Service Publishing Wizard](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13eca-173">請參閱</span><span class="sxs-lookup"><span data-stu-id="13eca-173">See Also</span></span>  
 <span data-ttu-id="13eca-174">[如何設定使用 BizTalk WCF 服務發佈精靈發佈的 WCF 服務](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="13eca-174">[How to Configure WCF Services Published with the BizTalk WCF Service Publishing Wizard](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md) </span></span>  
 <span data-ttu-id="13eca-175">[逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="13eca-175">[Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md) </span></span>  
 [<span data-ttu-id="13eca-176">如何使用 BizTalk WCF 服務發佈精靈結構描述發佈為 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="13eca-176">How to Use the BizTalk WCF Service Publishing Wizard to Publish Schemas as WCF Services</span></span>](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)