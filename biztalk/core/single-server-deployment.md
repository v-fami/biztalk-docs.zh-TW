---
title: "單一伺服器部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, deploying
- configuring [Windows SharePoint Services adapters], customizing
- deploying, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, installing
- Windows SharePoint Services adapters, configuring
- configuring [Windows SharePoint Services adapters], single-server deployment
- Windows SharePoint Services adapters, single-server deployment
ms.assetid: 94ba8241-9a30-46ca-b962-721e2d00f420
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6796bbbad4722e959962ea88e9854bce82476be4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="single-server-deployment"></a><span data-ttu-id="8bbc6-102">單一伺服器部署</span><span class="sxs-lookup"><span data-stu-id="8bbc6-102">Single-Server Deployment</span></span>
<span data-ttu-id="8bbc6-103">這個主題針對 Windows SharePoint Services 討論其 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器的單一伺服器安裝及部署考量。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-103">This topic discusses single-server setup and deployment considerations for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter for Windows SharePoint Services.</span></span>  
  
## <a name="installing-the-windows-sharepoint-services-adapter-in-a-single-server-deployment"></a><span data-ttu-id="8bbc6-104">在單一伺服器部署中安裝 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="8bbc6-104">Installing the Windows SharePoint Services adapter in a single-server deployment</span></span>  
 <span data-ttu-id="8bbc6-105">選取為 Windows SharePoint Services 配接器安裝必要軟體的「Windows SharePoint Service 配接器 Web 服務」元件，以透過 Windows SharePoint Services 處理內送和外寄文件。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-105">Selecting the Windows SharePoint Service adapter Web service component installs the necessary software for the Windows SharePoint Services adapter to process incoming and outgoing documents through Windows SharePoint Services.</span></span> <span data-ttu-id="8bbc6-106">此 Web 服務必須安裝在安裝 Windows SharePoint Services 的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-106">This Web service must be installed on the server where Windows SharePoint Services is installed.</span></span> <span data-ttu-id="8bbc6-107">不論不同的 SharePoint 網站是在相同的 IIS 站台或是在不同的 IIS 站台上，配接器 Web 服務都可以處理多個 SharePoint 網站，包括裝載「商務活動服務」(BAS) 的網站。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-107">The adapter Web service can handle multiple SharePoint sites including the Web site that hosts Business Activity Services (BAS), regardless of whether they are on the same IIS site or on different IIS sites.</span></span>  
  
 <span data-ttu-id="8bbc6-108">Windows SharePoint Services 配接器有三個元件：</span><span class="sxs-lookup"><span data-stu-id="8bbc6-108">The Windows SharePoint Services adapter has three components:</span></span>  
  
-   <span data-ttu-id="8bbc6-109">執行階段元件</span><span class="sxs-lookup"><span data-stu-id="8bbc6-109">Runtime components</span></span>  
  
-   <span data-ttu-id="8bbc6-110">設計階段元件</span><span class="sxs-lookup"><span data-stu-id="8bbc6-110">Design time components</span></span>  
  
-   <span data-ttu-id="8bbc6-111">配接器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="8bbc6-111">Adapter Web service</span></span>  
  
 <span data-ttu-id="8bbc6-112">配接器執行階段已安裝並設定自動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段功能。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-112">The adapter runtime is installed and configured automatically by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime feature.</span></span> <span data-ttu-id="8bbc6-113">配接器設計階段元件會安裝並設定與其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-113">The adapter design time components are installed and configured with the other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features.</span></span> <span data-ttu-id="8bbc6-114">設計階段元件互動藉由建立 Windows SharePoint Services 連接埠，透過系統管理工具、 開發人員工具和 SDK 中隨附的工具或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段功能。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-114">You interact with the design time components by creating Windows SharePoint Services ports through tools that are included in the Administration Tools, Developer Tools, and SDK or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime features.</span></span> <span data-ttu-id="8bbc6-115">您無法為執行階段和設計階段元件自訂任何組態選項。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-115">You cannot customize any configuration options for runtime and design time components.</span></span> <span data-ttu-id="8bbc6-116">您只能自訂 Windows SharePoint Services 配接器 Web 服務選項。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-116">You can customize only the Windows SharePoint Service adapter Web service options.</span></span>  
  
 <span data-ttu-id="8bbc6-117">只有「啟用 SharePoint 的主控件」群組擁有叫用配接器 Web 服務的權限。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-117">Only members of the SharePoint Enabled Hosts group have permissions to invoke the adapter Web service.</span></span> <span data-ttu-id="8bbc6-118">如需 Windows SharePoint Services 配接器執行階段所需的 Windows SharePoint Services 權限的詳細資訊，請參閱 < 安全性 > 一節中的[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-118">For more information about the Windows SharePoint Services permissions needed by the Windows SharePoint Services adapter runtime, see the security section in [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bbc6-119">若您選擇安裝 BAS，將會自動選取 Windows SharePoint Services 配接器 Web 服務元件。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-119">The Windows SharePoint Services adapter Web service component will be automatically selected if you choose to install BAS.</span></span>  
  
#### <a name="to-install-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="8bbc6-120">安裝 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="8bbc6-120">To install the Windows SharePoint Services adapter</span></span>  
  
1.  <span data-ttu-id="8bbc6-121">安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-121">Install BizTalk Server.</span></span> <span data-ttu-id="8bbc6-122">如需詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-122">For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).</span></span>  
  
2.  <span data-ttu-id="8bbc6-123">在**元件安裝**畫面上，於**可用元件**下**其他軟體**，選取**Windows SharePoint Services 配接器Web 服務**。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-123">On the **Component Installation** screen, under **Available Components**, under **Additional Software**, select **Windows SharePoint Services Adapter Web service**.</span></span>  
  
## <a name="configuring-the-windows-sharepoint-services-adapter-web-service-in-a-single-server-deployment"></a><span data-ttu-id="8bbc6-124">在單一伺服器部署中設定 Windows SharePoint Services 配接器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="8bbc6-124">Configuring the Windows SharePoint Services adapter Web service in a single-server deployment</span></span>  
 <span data-ttu-id="8bbc6-125">您可以使用基本組態或自訂組態，來設定 Windows SharePoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-125">You can configure the Windows SharePoint Services adapter using either a basic configuration or a custom configuration.</span></span> <span data-ttu-id="8bbc6-126">如需有關這些工具的詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的組態概觀](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72)。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-126">For more information about these tools, see [Configuration Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).</span></span>  
  
### <a name="using-a-basic-configuration"></a><span data-ttu-id="8bbc6-127">使用基本組態</span><span class="sxs-lookup"><span data-stu-id="8bbc6-127">Using a basic configuration</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8bbc6-128"> 允許您使用預設設定來設定伺服器。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-128"> allows you to configure the server by using default settings.</span></span> <span data-ttu-id="8bbc6-129">伺服器的預設設定是使用您輸入組態精靈中的資料庫伺服器名稱、使用者名稱和密碼所設定。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-129">The default settings for the server are configured using the database server name, user name, and password that you enter into the configuration wizard.</span></span> <span data-ttu-id="8bbc6-130">當您使用基本組態來設定 Windows SharePoint Services 配接器時，會發生以下狀況：</span><span class="sxs-lookup"><span data-stu-id="8bbc6-130">When you configure the Windows SharePoint Services adapter Web service using a basic configuration, the following happens:</span></span>  
  
-   <span data-ttu-id="8bbc6-131">會建立「啟用 SharePoint 的主控件」Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-131">The SharePoint Enabled Hosts Windows group is created.</span></span>  
  
-   <span data-ttu-id="8bbc6-132">會使用「預設的網站」來裝載 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="8bbc6-132">The Default Web Site is used to host the Windows SharePoint Services Adapter</span></span>  
  
-   <span data-ttu-id="8bbc6-133">會建立和設定 BTSSharePointAdapterWSAppPool 應用程式集區，以也是用來執行 Windows SharePoint Services 應用程式集區的帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-133">The BTSSharePointAdapterWSAppPool application pool is created and configured to run under the account that is also used to run the Windows SharePoint Services application pool.</span></span>  
  
-   <span data-ttu-id="8bbc6-134">會建立和設定 BTSharePointAdapterWS 虛擬應用程式，以便在 BTSSharePointAdapterWSAppPool 應用程式集區中執行</span><span class="sxs-lookup"><span data-stu-id="8bbc6-134">The BTSharePointAdapterWS virtual application is created and configured to run in the BTSSharePointAdapterWSAppPool application pool</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bbc6-135">若此虛擬目錄已經存在，組態將不會更新 Metabase 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-135">If this virtual directory already exists, configuration will not update the properties in the metabase.</span></span> <span data-ttu-id="8bbc6-136">您必須刪除虛擬目錄並再次執行組態。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-136">You must delete the virtual directory, and run configuration again.</span></span>  
  
-   <span data-ttu-id="8bbc6-137">BTSharePointAdapterWS 虛擬應用程式包含 Web 服務</span><span class="sxs-lookup"><span data-stu-id="8bbc6-137">The BTSharePointAdapterWS virtual application contains the Web service</span></span>  
  
 <span data-ttu-id="8bbc6-138">如需有關基本組態的詳細資訊，請參閱[基本組態](http://msdn.microsoft.com/library/abdf3eb5-9779-47ff-bc97-2209eb4b12f5)。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-138">For more information about basic configuration, see [Basic Configuration](http://msdn.microsoft.com/library/abdf3eb5-9779-47ff-bc97-2209eb4b12f5).</span></span>  
  
### <a name="using-a-custom-configuration"></a><span data-ttu-id="8bbc6-139">使用自訂組態</span><span class="sxs-lookup"><span data-stu-id="8bbc6-139">Using a custom configuration</span></span>  
 <span data-ttu-id="8bbc6-140">BizTalk Server 組態可提供本機電腦上所安裝之功能的組態狀態高層級分析。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-140">The BizTalk Server Configuration provides a high-level analysis of the configuration state of the features you have installed on the local computer.</span></span> <span data-ttu-id="8bbc6-141">此工具可讓您設定與取消設定功能、設定安全性設定，以及從其他電腦匯入和匯出組態。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-141">The tool allows you to configure and unconfigure features, configure security settings, and import and export configurations from other computers.</span></span>  
  
 <span data-ttu-id="8bbc6-142">使用**Windows SharePoint Services 配接器 Web 服務**頁面，即可在此電腦上設定 Windows SharePoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-142">Use the **Windows SharePoint Services Adapter Web Service** page to configure the Windows SharePoint Services adapter on this computer.</span></span> <span data-ttu-id="8bbc6-143">下表列出組態選項。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-143">The following table lists the configuration options.</span></span>  
  
|<span data-ttu-id="8bbc6-144">使用</span><span class="sxs-lookup"><span data-stu-id="8bbc6-144">Use this</span></span>|<span data-ttu-id="8bbc6-145">動作</span><span class="sxs-lookup"><span data-stu-id="8bbc6-145">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="8bbc6-146">**此電腦上啟用 Windows SharePoint Services 配接器**</span><span class="sxs-lookup"><span data-stu-id="8bbc6-146">**Enable Windows SharePoint Services Adapter on this computer**</span></span>|<span data-ttu-id="8bbc6-147">選取**啟用 Windows SharePoint Services 配接器在此電腦上**若要啟用這台電腦上的介面卡。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-147">Select **Enable Windows SharePoint Services Adapter on this computer** to enable the adapter on this computer.</span></span>|  
|<span data-ttu-id="8bbc6-148">**Windows 群組**</span><span class="sxs-lookup"><span data-stu-id="8bbc6-148">**Windows group**</span></span>|<span data-ttu-id="8bbc6-149">**Windows 群組**清單所提供的檢視，您可以編輯的 BizTalk SharePoint 配接器啟用主控件 」 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-149">The **Windows group** list provides a view that you can edit of the BizTalk SharePoint Adapter Enabled Hosts Windows group.</span></span>|  
|<span data-ttu-id="8bbc6-150">**Windows SharePoint Services 配接器網站**</span><span class="sxs-lookup"><span data-stu-id="8bbc6-150">**Windows SharePoint Services Adapter Web site**</span></span>|<span data-ttu-id="8bbc6-151">選取要用來裝載 Windows SharePoint Services 配接器 Web 服務的網站。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-151">Select the Web site that will host the Windows SharePoint Service adapter Web service.</span></span>|  
  
 <span data-ttu-id="8bbc6-152">當您使用自訂組態設定 Windows SharePoint Services 配接器時，會發生以下狀況：</span><span class="sxs-lookup"><span data-stu-id="8bbc6-152">When you configure the Windows SharePoint Services adapter using a custom configuration, the following happens:</span></span>  
  
-   <span data-ttu-id="8bbc6-153">除非您指定另一個 Windows 群組，否則預設會建立「啟用 SharePoint 的主控件」Windows 群組</span><span class="sxs-lookup"><span data-stu-id="8bbc6-153">The SharePoint Enabled Hosts Windows group is created by default unless you specify another Windows group</span></span>  
  
-   <span data-ttu-id="8bbc6-154">除非您指定另一個網站，否則會使用「預設網站」來裝載 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="8bbc6-154">The Default Web Site is used to host the Windows SharePoint Services adapter unless you specify another Web site</span></span>  
  
-   <span data-ttu-id="8bbc6-155">會建立和設定 BTSSharePointAdapterWSAppPool 應用程式集區，以也是用來執行 Windows SharePoint Services 應用程式集區的帳戶執行</span><span class="sxs-lookup"><span data-stu-id="8bbc6-155">The BTSSharePointAdapterWSAppPool application pool is created and configured to run under the account that is also used to run the Windows SharePoint Services application pool</span></span>  
  
-   <span data-ttu-id="8bbc6-156">會建立和設定 BTSharePointAdapterWS 虛擬應用程式，以便在 BTSSharePointAdapterWSAppPool 應用程式集區中執行</span><span class="sxs-lookup"><span data-stu-id="8bbc6-156">The BTSharePointAdapterWS virtual application is created and configured to run in the BTSSharePointAdapterWSAppPool application pool</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bbc6-157">若此虛擬目錄已經存在，組態將不會更新 Metabase 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-157">If this virtual directory already exists, configuration will not update the properties in the metabase.</span></span> <span data-ttu-id="8bbc6-158">您必須刪除虛擬目錄並再次執行組態。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-158">You must delete the virtual directory, and run configuration again.</span></span>  
  
-   <span data-ttu-id="8bbc6-159">BTSharePointAdapterWS 虛擬應用程式包含 Web 服務</span><span class="sxs-lookup"><span data-stu-id="8bbc6-159">The BTSharePointAdapterWS virtual application contains the Web service</span></span>  
  
 <span data-ttu-id="8bbc6-160">如需有關自訂組態管理員的詳細資訊，請參閱[匯入和匯出 BizTalk Server 組態](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-160">For more information about the custom configuration manager, see [Import and Export BizTalk Server Configuration](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).</span></span>  
  
##### <a name="to-configure-the-windows-sharepoint-services-adapter-by-using-a-custom-configuration"></a><span data-ttu-id="8bbc6-161">使用自訂組態設定 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="8bbc6-161">To configure the Windows SharePoint Services adapter by using a custom configuration</span></span>  
  
1.  <span data-ttu-id="8bbc6-162">在**BizTalk Server 組態**，選取**SharePoint 配接器**節點。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-162">In the **BizTalk Server Configuration**, select the **SharePoint adapter** node.</span></span>  
  
2.  <span data-ttu-id="8bbc6-163">選取**啟用 Windows SharePoint Services 配接器在此電腦上**。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-163">Select **Enable Windows SharePoint Services Adapter on this computer**.</span></span>  
  
3.  <span data-ttu-id="8bbc6-164">在下**Windows 群組**，選取您要將 Windows SharePoint Services 配接器的 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-164">Under **Windows Group**, select the Windows group you will be using for the Windows SharePoint Services adapter.</span></span> <span data-ttu-id="8bbc6-165">依照預設，這個群組是「啟用 SharePoint 的主控件」。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-165">By default, this is SharePoint Enabled Hosts.</span></span>  
  
4.  <span data-ttu-id="8bbc6-166">在**Windows SharePoint Services 配接器網站**下拉式清單方塊中，選取網站將會安裝配接器元件。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-166">In the **Windows SharePoint Services Adapter Web Site** drop-down box, select the Web site where the adapter components will be installed.</span></span> <span data-ttu-id="8bbc6-167">依照預設，這是「預設的網站」。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-167">By default, this is the Default Web Site.</span></span>  
  
5.  <span data-ttu-id="8bbc6-168">按一下 [套用組態]。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-168">Click **Apply Configuration**.</span></span>  
  
## <a name="considerations-for-a-single-server-deployment"></a><span data-ttu-id="8bbc6-169">單一伺服器部署的考量</span><span class="sxs-lookup"><span data-stu-id="8bbc6-169">Considerations for a single-server deployment</span></span>  
 <span data-ttu-id="8bbc6-170">當您在單一伺服器環境中安裝和部署 Windows SharePoint Services 配接器時，請考慮下列項目：</span><span class="sxs-lookup"><span data-stu-id="8bbc6-170">When you set up and deploy the Windows SharePoint Services adapter in a single-server environment, consider the following:</span></span>  
  
-   <span data-ttu-id="8bbc6-171">新增 BizTalk Service 帳戶到該伺服器的「啟用 SharePoint 的主控件」Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-171">Add the BizTalk Service account to the SharePoint Enabled Hosts Windows group on that server.</span></span>  
  
-   <span data-ttu-id="8bbc6-172">使用 SharePoint [管理中心] 工具，將「啟用 SharePoint 的主控件」群組加入「SharePoint 投稿人」角色。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-172">Add the SharePoint Enabled Hosts group to the SharePoint Contributors role using the SharePoint Central Administration tool.</span></span>  
  
-   <span data-ttu-id="8bbc6-173">在 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上，執行 SharePoint 配接器 Web 服務所使用的識別需要以下權限：</span><span class="sxs-lookup"><span data-stu-id="8bbc6-173">On [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], the identity under which the SharePoint Adapter Web Service runs needs the following permissions:</span></span>  
  
     <span data-ttu-id="8bbc6-174">**讀取**權限**Program Files\Microsoft BizTalk Server\<版本\>\Business Activity Services\BTSharePointV3AdapterWS**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-174">**Read** permissions on the **Program Files\Microsoft BizTalk Server \<version\>\Business Activity Services\BTSharePointV3AdapterWS** folder.</span></span> <span data-ttu-id="8bbc6-175">如果使用 64 位元版本的 Windows 和 BizTalk Server，需要設定權限**Program Files (x86) \Microsoft BizTalk Server\<版本\>\Business Activity Services\BTSharePointV3AdapterWS**</span><span class="sxs-lookup"><span data-stu-id="8bbc6-175">If using a 64-bit version of Windows and BizTalk Server, permissions need to be set on the **Program Files (x86)\Microsoft BizTalk Server \<version\>\Business Activity Services\BTSharePointV3AdapterWS**</span></span>  
  
     <span data-ttu-id="8bbc6-176">**讀取**下列登錄機碼的權限： **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-176">**Read** permission on the following registry key: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**.</span></span>  
  
     <span data-ttu-id="8bbc6-177">在包含 Sharepoint 資料庫的 SQL Server 上的登入權限。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-177">Logon permissions on the SQL Server that contains the Sharepoint databases.</span></span>  
  
     <span data-ttu-id="8bbc6-178">成員**公用**和**WSS_Content_Application_Pools** SharePoint 組態資料庫中的角色。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-178">A member of the **Public** and **WSS_Content_Application_Pools** roles within the SharePoint configuration database.</span></span>  
  
     <span data-ttu-id="8bbc6-179">成員**公用**和**db 擁有者**SharePoint 內容資料庫中的角色。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-179">A member of the **Public** and **db owner** roles within the SharePoint content database.</span></span>  
  
-   <span data-ttu-id="8bbc6-180">您安裝 Web 服務的網站必須擴充為 SharePoint Services 網站。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-180">The Web site that you install the Web service on must be extended as a SharePoint Services Web site.</span></span>  
  
-   <span data-ttu-id="8bbc6-181">您可以使用無訊息安裝，來安裝和設定 Windows SharePoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-181">You can install and configure the Windows SharePoint Services adapter using silent installation.</span></span> <span data-ttu-id="8bbc6-182">如需詳細資訊，請參閱[附錄 a： 無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="8bbc6-182">For more information, see [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bbc6-183">請參閱</span><span class="sxs-lookup"><span data-stu-id="8bbc6-183">See Also</span></span>  
 <span data-ttu-id="8bbc6-184">[Windows SharePoint Services 配接器](../core/windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="8bbc6-184">[Windows SharePoint Services Adapter](../core/windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="8bbc6-185">多伺服器部署</span><span class="sxs-lookup"><span data-stu-id="8bbc6-185">Multiserver Deployment</span></span>](../core/multiserver-deployment.md)