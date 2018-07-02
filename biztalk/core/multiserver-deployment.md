---
title: 多伺服器部署 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], multi-server deployment
- planning, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, deploying
- Windows SharePoint Services adapters, multi-server deployment
- deploying, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, installing
ms.assetid: 0c6e2aa0-e873-461b-8101-9b0988019597
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e857aece2911aa9f1b3551f339524d2262cc0bf4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979759"
---
# <a name="multiserver-deployment"></a><span data-ttu-id="856dd-102">多伺服器部署</span><span class="sxs-lookup"><span data-stu-id="856dd-102">Multiserver Deployment</span></span>
<span data-ttu-id="856dd-103">本主題討論 Windows SharePoint Services 之 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器的多伺服器安裝和部署考量。</span><span class="sxs-lookup"><span data-stu-id="856dd-103">This topic discusses multiserver setup and deployment considerations for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter for Windows SharePoint Services.</span></span>  
  
## <a name="installing-the-windows-sharepoint-services-adapter-in-a-multiserver-deployment"></a><span data-ttu-id="856dd-104">在多伺服器部署中安裝 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="856dd-104">Installing the Windows SharePoint Services adapter in a multiserver deployment</span></span>  
 <span data-ttu-id="856dd-105">選取為 Windows SharePoint Services 配接器安裝必要軟體的「Windows SharePoint Service 配接器 Web 服務」元件，以透過 Windows SharePoint Services 處理內送和外寄文件。</span><span class="sxs-lookup"><span data-stu-id="856dd-105">Selecting the Windows SharePoint Service Adapter Web Service component installs the necessary software for the Windows SharePoint Services adapter to process incoming and outgoing documents through Windows SharePoint Services.</span></span> <span data-ttu-id="856dd-106">此 Web 服務必須安裝在安裝 Windows SharePoint Services 的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="856dd-106">This Web service must be installed on the server where Windows SharePoint Services is installed.</span></span>  
  
 <span data-ttu-id="856dd-107">配接器 Web 服務可以處理多個 SharePoint 網站，不論它們是相同的 IIS 站台或不同的 IIS 站台上。</span><span class="sxs-lookup"><span data-stu-id="856dd-107">The adapter Web service can handle multiple SharePoint sites regardless of whether they are on the same IIS site or on different IIS sites.</span></span>  
  
 <span data-ttu-id="856dd-108">Windows SharePoint Services 配接器有三個元件：</span><span class="sxs-lookup"><span data-stu-id="856dd-108">The Windows SharePoint Services Adapter has three components:</span></span>  
  
- <span data-ttu-id="856dd-109">執行階段元件</span><span class="sxs-lookup"><span data-stu-id="856dd-109">Runtime components</span></span>  
  
- <span data-ttu-id="856dd-110">設計階段元件</span><span class="sxs-lookup"><span data-stu-id="856dd-110">Design time components</span></span>  
  
- <span data-ttu-id="856dd-111">配接器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="856dd-111">Adapter Web service</span></span>  
  
  <span data-ttu-id="856dd-112">配接器執行階段已安裝並設定自動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段功能。</span><span class="sxs-lookup"><span data-stu-id="856dd-112">The adapter runtime is installed and configured automatically by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime feature.</span></span> <span data-ttu-id="856dd-113">配接器設計階段元件會安裝並設定其他[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="856dd-113">The adapter design time components are installed and configured with other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features.</span></span> <span data-ttu-id="856dd-114">設計階段元件互動藉由建立 Windows SharePoint Services 連接埠，透過管理工具、 開發人員工具和 SDK 中包含的工具或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段功能。</span><span class="sxs-lookup"><span data-stu-id="856dd-114">You interact with the design time components by creating Windows SharePoint Services ports through tools that are included in the Administration Tools, Developer Tools, and SDK or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime features.</span></span> <span data-ttu-id="856dd-115">您無法為執行階段和設計階段元件自訂任何組態選項。</span><span class="sxs-lookup"><span data-stu-id="856dd-115">You cannot customize any configuration options for runtime and design time components.</span></span> <span data-ttu-id="856dd-116">您只能自訂 Windows SharePoint Services 配接器 Web 服務選項。</span><span class="sxs-lookup"><span data-stu-id="856dd-116">You can customize only the Windows SharePoint Services adapter Web Service options.</span></span>  
  
  <span data-ttu-id="856dd-117">只有「啟用 SharePoint 的主控件」群組的成員具備叫用配接器 Web 服務的權限。</span><span class="sxs-lookup"><span data-stu-id="856dd-117">Only members of the SharePoint Enabled Hosts group will have permissions to invoke the adapter Web service.</span></span> <span data-ttu-id="856dd-118">如需有關 Windows SharePoint Services 配接器執行階段所需的 Windows SharePoint Services 權限的詳細資訊，請參閱中的 [安全性] 區段[什麼是 Windows SharePoint Services 配接器？](../core/what-is-the-windows-sharepoint-services-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="856dd-118">For more information about the Windows SharePoint Services permissions needed by the Windows SharePoint Services adapter runtime, see the security section in [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="856dd-119">若您選擇安裝 BAS，將會自動選取 Windows SharePoint Services 配接器 Web 服務元件。</span><span class="sxs-lookup"><span data-stu-id="856dd-119">The Windows SharePoint Services adapter Web service component will be automatically selected if you choose to install BAS.</span></span>  
  
#### <a name="to-install-the-windows-sharepoint-services-adapter"></a><span data-ttu-id="856dd-120">安裝 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="856dd-120">To install the Windows SharePoint Services adapter</span></span>  
  
1. <span data-ttu-id="856dd-121">安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="856dd-121">Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="856dd-122">如需詳細資訊，請參閱 < [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。</span><span class="sxs-lookup"><span data-stu-id="856dd-122">For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).</span></span>  
  
2. <span data-ttu-id="856dd-123">在上**元件安裝**畫面上，於**可用的元件**下方**其他軟體**，選取**Windows SharePoint Services 配接器Web 服務**。</span><span class="sxs-lookup"><span data-stu-id="856dd-123">On the **Component Installation** screen, under **Available Components**, under **Additional Software**, select **Windows SharePoint Services Adapter Web service**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="856dd-124">您必須安裝和設定在電腦上執行該主控件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行 Windows SharePoint Services 的執行階段和電腦。</span><span class="sxs-lookup"><span data-stu-id="856dd-124">You must run setup and configuration on the computer that hosts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime and the computer running Windows SharePoint Services.</span></span>  
  
## <a name="configuring-the-windows-sharepoint-services-adapter-web-service-in-a-multiserver-deployment"></a><span data-ttu-id="856dd-125">在多伺服器部署中設定 Windows SharePoint Services 配接器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="856dd-125">Configuring the Windows SharePoint Services adapter Web service in a multiserver deployment</span></span>  
 <span data-ttu-id="856dd-126">您可以使用 [BizTalk Server 組態] 來設定 Windows SharePoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="856dd-126">You configure the Windows SharePoint Services adapter using the BizTalk Server Configuration.</span></span> <span data-ttu-id="856dd-127">如需有關這些工具的詳細資訊，請參閱 < [BizTalk Server 2013 和 2013 R2 的設定概觀](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72)。</span><span class="sxs-lookup"><span data-stu-id="856dd-127">For more information about these tools, see [Configuration Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).</span></span>  
  
### <a name="using-a-custom-configuration"></a><span data-ttu-id="856dd-128">使用自訂組態</span><span class="sxs-lookup"><span data-stu-id="856dd-128">Using a custom configuration</span></span>  
 <span data-ttu-id="856dd-129">BizTalk Server 組態可提供本機電腦上所安裝之功能的組態狀態高層級分析。</span><span class="sxs-lookup"><span data-stu-id="856dd-129">The BizTalk Server Configuration provides a high-level analysis of the configuration state of the features you have installed on the local computer.</span></span> <span data-ttu-id="856dd-130">此工具可讓您設定與取消設定功能、設定安全性設定，以及從其他電腦匯入和匯出組態。</span><span class="sxs-lookup"><span data-stu-id="856dd-130">The tool allows you to configure and unconfigure features, configure security settings, and import and export configurations from other computers.</span></span>  
  
 <span data-ttu-id="856dd-131">使用**Windows SharePoint Services**這台電腦上設定 Windows SharePoint Services 配接器的頁面。</span><span class="sxs-lookup"><span data-stu-id="856dd-131">Use the **Windows SharePoint Services** page to configure the Windows SharePoint Services adapter on this computer.</span></span> <span data-ttu-id="856dd-132">下表列出組態選項。</span><span class="sxs-lookup"><span data-stu-id="856dd-132">The following table lists the configuration options.</span></span>  
  
|<span data-ttu-id="856dd-133">使用</span><span class="sxs-lookup"><span data-stu-id="856dd-133">Use this</span></span>|<span data-ttu-id="856dd-134">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="856dd-134">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="856dd-135">**此電腦上啟用 Windows SharePoint Services 配接器**</span><span class="sxs-lookup"><span data-stu-id="856dd-135">**Enable Windows SharePoint Services Adapter on this computer**</span></span>|<span data-ttu-id="856dd-136">選取 **啟用 Windows SharePoint Services 配接器在此電腦上**若要啟用這台電腦上的介面卡。</span><span class="sxs-lookup"><span data-stu-id="856dd-136">Select **Enable Windows SharePoint Services Adapter on this computer** to enable the adapter on this computer.</span></span>|  
|<span data-ttu-id="856dd-137">**Windows 群組**</span><span class="sxs-lookup"><span data-stu-id="856dd-137">**Windows group**</span></span>|<span data-ttu-id="856dd-138">**Windows 群組**清單所提供的檢視，您可以編輯的 BizTalk SharePoint 配接器啟用主控件 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="856dd-138">The **Windows group** list provides a view that you can edit of the BizTalk SharePoint Adapter Enabled Hosts Windows group.</span></span>|  
|<span data-ttu-id="856dd-139">**Windows SharePoint Services 配接器網站**</span><span class="sxs-lookup"><span data-stu-id="856dd-139">**Windows SharePoint Services Adapter Web site**</span></span>|<span data-ttu-id="856dd-140">選取要用來裝載 Windows SharePoint Services 配接器 Web 服務的網站。</span><span class="sxs-lookup"><span data-stu-id="856dd-140">Select the Web site that will host the Windows SharePoint Services adapter Web service.</span></span>|  
  
 <span data-ttu-id="856dd-141">當您使用自訂組態設定 Windows SharePoint Services 配接器時，會發生以下狀況：</span><span class="sxs-lookup"><span data-stu-id="856dd-141">When you configure the Windows SharePoint Services adapter using custom configuration, the following happens:</span></span>  
  
-   <span data-ttu-id="856dd-142">除非您指定另一個 Windows 群組，否則預設會建立「啟用 SharePoint 的主控件」Windows 群組</span><span class="sxs-lookup"><span data-stu-id="856dd-142">The SharePoint Enabled Hosts Windows group is created by default unless you specify another Windows group</span></span>  
  
-   <span data-ttu-id="856dd-143">除非您指定另一個網站，否則會使用「預設網站」來裝載 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="856dd-143">The Default Web Site is used to host the Windows SharePoint Services adapter unless you specify another Web site</span></span>  
  
-   <span data-ttu-id="856dd-144">會建立和設定 BTSSharePointAdapterWSAppPool 應用程式集區，以也是用來執行 Windows SharePoint Services 應用程式集區的帳戶執行</span><span class="sxs-lookup"><span data-stu-id="856dd-144">The BTSSharePointAdapterWSAppPool application pool is created and configured to run under the account that is also used to run the Windows SharePoint Services application pool</span></span>  
  
-   <span data-ttu-id="856dd-145">會建立和設定 BTSharePointAdapterWS 虛擬應用程式，以便在 BTSSharePointAdapterWSAppPool 應用程式集區中執行</span><span class="sxs-lookup"><span data-stu-id="856dd-145">The BTSharePointAdapterWS virtual application is created and configured to run in the BTSSharePointAdapterWSAppPool application pool</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="856dd-146">若此虛擬目錄已經存在，組態將不會更新 Metabase 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="856dd-146">If this virtual directory already exists, configuration will not update the properties in the metabase.</span></span> <span data-ttu-id="856dd-147">您必須刪除虛擬目錄並再次執行組態。</span><span class="sxs-lookup"><span data-stu-id="856dd-147">You must delete the virtual directory and run configuration again.</span></span>  
  
- <span data-ttu-id="856dd-148">BTSharePointAdapterWS 虛擬應用程式包含 Web 服務</span><span class="sxs-lookup"><span data-stu-id="856dd-148">The BTSharePointAdapterWS virtual application contains the Web service</span></span>  
  
  <span data-ttu-id="856dd-149">如需有關 BizTalk Server 組態的詳細資訊，請參閱 <<c0> [ 匯入和匯出 BizTalk Server 組態](../install-and-config-guides/import-and-export-biztalk-server-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="856dd-149">For more information about the BizTalk Server Configuration, see [Import and Export BizTalk Server Configuration](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).</span></span>  
  
##### <a name="to-configure-the-windows-sharepoint-services-adapter-by-using-custom-configuration"></a><span data-ttu-id="856dd-150">使用自訂組態設定 Windows SharePoint Services 配接器</span><span class="sxs-lookup"><span data-stu-id="856dd-150">To configure the Windows SharePoint Services adapter by using custom configuration</span></span>  
  
1. <span data-ttu-id="856dd-151">在  **BizTalk Server 組態**，選取**SharePoint 配接器**節點。</span><span class="sxs-lookup"><span data-stu-id="856dd-151">In the **BizTalk Server Configuration**, select the **SharePoint adapter** node.</span></span>  
  
2. <span data-ttu-id="856dd-152">選取 **啟用 Windows SharePoint Services 配接器在此電腦上**。</span><span class="sxs-lookup"><span data-stu-id="856dd-152">Select **Enable Windows SharePoint Services Adapter on this computer**.</span></span>  
  
3. <span data-ttu-id="856dd-153">底下**Windows 群組**，選取您要將 Windows SharePoint Services 配接器的 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="856dd-153">Under **Windows Group**, select the Windows group you will be using for the Windows SharePoint Services adapter.</span></span> <span data-ttu-id="856dd-154">依照預設，這個群組是「啟用 SharePoint 的主控件」。</span><span class="sxs-lookup"><span data-stu-id="856dd-154">By default, this is SharePoint Enabled Hosts.</span></span>  
  
4. <span data-ttu-id="856dd-155">在  **Windows SharePoint Services 配接器網站**下拉式清單方塊中，選取網站將會安裝配接器元件。</span><span class="sxs-lookup"><span data-stu-id="856dd-155">In the **Windows SharePoint Services Adapter Web Site** drop-down box, select the Web site where the adapter components will be installed.</span></span> <span data-ttu-id="856dd-156">依照預設，這是「預設的網站」。</span><span class="sxs-lookup"><span data-stu-id="856dd-156">By default, this is the Default Web Site.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="856dd-157">在沒有安裝任何其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件的遠端 SharePoint Server 電腦上安裝 Windows SharePoint Services 配接器網站是一種完全支援的組態。</span><span class="sxs-lookup"><span data-stu-id="856dd-157">The installation of the Windows SharePoint Services Adapter Web site on a remote SharePoint Server computer that does not have any other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components installed is a fully supported configuration.</span></span>  
  
5. <span data-ttu-id="856dd-158">按一下 [套用組態]。</span><span class="sxs-lookup"><span data-stu-id="856dd-158">Click **Apply Configuration**.</span></span>  
  
## <a name="considerations-for-a-multiserver-deployment"></a><span data-ttu-id="856dd-159">多伺服器部署的考量</span><span class="sxs-lookup"><span data-stu-id="856dd-159">Considerations for a multiserver deployment</span></span>  
 <span data-ttu-id="856dd-160">![](../core/media/adapters-wss-multiserver-screenshot01.gif "Adapters_WSS_Multiserver_Screenshot01")</span><span class="sxs-lookup"><span data-stu-id="856dd-160">![](../core/media/adapters-wss-multiserver-screenshot01.gif "Adapters_WSS_Multiserver_Screenshot01")</span></span>  
  
### <a name="general-considerations"></a><span data-ttu-id="856dd-161">一般考量</span><span class="sxs-lookup"><span data-stu-id="856dd-161">General considerations</span></span>  
 <span data-ttu-id="856dd-162">當您在多伺服器環境中安裝和部署 Windows SharePoint Services 配接器時，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="856dd-162">When you set up and deploy the Windows SharePoint Services adapter in a multiserver environment, consider the following:</span></span>  
  
- <span data-ttu-id="856dd-163">新增 BizTalk Service 帳戶到每部伺服器的「啟用 SharePoint 的主控件」Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="856dd-163">Add the BizTalk Service account to the SharePoint Enabled Hosts Windows group on each server.</span></span>  
  
- <span data-ttu-id="856dd-164">使用 SharePoint [管理中心] 工具，將「啟用 SharePoint 的主控件」群組加入「SharePoint 投稿人」角色。</span><span class="sxs-lookup"><span data-stu-id="856dd-164">Add the SharePoint Enabled Hosts group to the SharePoint Contributors role using the SharePoint Central Administration tool.</span></span>  
  
- <span data-ttu-id="856dd-165">在 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上，執行 SharePoint 配接器 Web 服務所使用的識別需要以下權限：</span><span class="sxs-lookup"><span data-stu-id="856dd-165">On [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], the identity under which the SharePoint Adapter Web Service runs needs the following permissions:</span></span>  
  
   <span data-ttu-id="856dd-166">**讀取**權限**Program Files\Microsoft BizTalk Server\<版本\>\Business Activity Services\BTSharePointV3AdapterWS**資料夾。</span><span class="sxs-lookup"><span data-stu-id="856dd-166">**Read** permissions on the **Program Files\Microsoft BizTalk Server \<version\>\Business Activity Services\BTSharePointV3AdapterWS** folder.</span></span> <span data-ttu-id="856dd-167">如果使用 64 位元版本的 Windows 和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，要在設定需要的權限**Program Files (x86) \Microsoft BizTalk Server\<版本\>\Business Activity Services\BTSharePointV3AdapterWS**</span><span class="sxs-lookup"><span data-stu-id="856dd-167">If using a 64-bit version of Windows and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], permissions need to be set on the **Program Files (x86)\Microsoft BizTalk Server \<version\>\Business Activity Services\BTSharePointV3AdapterWS**</span></span>  
  
   <span data-ttu-id="856dd-168">**讀取**上的下列登錄機碼的權限： **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**。</span><span class="sxs-lookup"><span data-stu-id="856dd-168">**Read** permission on the following registry key: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**.</span></span>  
  
   <span data-ttu-id="856dd-169">在包含 Sharepoint 資料庫的 SQL Server 上的登入權限。</span><span class="sxs-lookup"><span data-stu-id="856dd-169">Logon permissions on the SQL Server that contains the Sharepoint databases.</span></span>  
  
   <span data-ttu-id="856dd-170">成員**公開金鑰**並**WSS_Content_Application_Pools** SharePoint 組態資料庫中的角色。</span><span class="sxs-lookup"><span data-stu-id="856dd-170">A member of the **Public** and **WSS_Content_Application_Pools** roles within the SharePoint configuration database.</span></span>  
  
   <span data-ttu-id="856dd-171">成員**公開金鑰**並**db 擁有者**SharePoint 內容資料庫中的角色。</span><span class="sxs-lookup"><span data-stu-id="856dd-171">A member of the **Public** and **db owner** roles within the SharePoint content database.</span></span>  
  
- <span data-ttu-id="856dd-172">您安裝 Web 服務的網站必須擴充為 SharePoint Services 網站。</span><span class="sxs-lookup"><span data-stu-id="856dd-172">The Web site that you install the Web service on must be extended as a SharePoint Services Web site.</span></span>  
  
- <span data-ttu-id="856dd-173">您可以使用無訊息安裝來安裝和設定 Windows SharePoint Services 配接器。</span><span class="sxs-lookup"><span data-stu-id="856dd-173">You can install and configure the Windows SharePoint Services adapter using a silent installation.</span></span> <span data-ttu-id="856dd-174">如需詳細資訊，請參閱 <<c0> [ 附錄 a： 無訊息安裝](../install-and-config-guides/appendix-a-silent-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="856dd-174">For more information, see [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md).</span></span>  
  
### <a name="considerations-for-network-load-balancing-nlb"></a><span data-ttu-id="856dd-175">網路負載平衡 (NLB) 的考量</span><span class="sxs-lookup"><span data-stu-id="856dd-175">Considerations for network load balancing (NLB)</span></span>  
 <span data-ttu-id="856dd-176">Windows SharePoint Services 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 配接器可支援 Windows SharePoint Services 伺服器的 NLB 叢集，並支援在相同群組中設定的多個 BizTalk 伺服器。</span><span class="sxs-lookup"><span data-stu-id="856dd-176">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter for Windows SharePoint Services supports NLB clustering of the Windows SharePoint Services servers along with multiple BizTalk servers that are configured in the same group.</span></span> <span data-ttu-id="856dd-177">所以，依照 SharePoint 文件的建議，Windows SharePoint Services 必須安裝在 NLB 叢集上。</span><span class="sxs-lookup"><span data-stu-id="856dd-177">For this, Windows SharePoint Services must be installed on the NLB cluster as recommended by SharePoint documentation.</span></span>  
  
 <span data-ttu-id="856dd-178">當您在使用 NLB 的多伺服器環境中安裝和部署 Windows SharePoint Services 配接器時，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="856dd-178">When you set up and deploy the Windows SharePoint Services adapter in a multiserver environment with NLB, consider the following:</span></span>  
  
-   <span data-ttu-id="856dd-179">選取選項以指向現有的「BizTalk 管理」資料庫來設定 Windows SharePoint Services。</span><span class="sxs-lookup"><span data-stu-id="856dd-179">Configure Windows SharePoint Services by selecting the option to point to an existing BizTalk Management database.</span></span> <span data-ttu-id="856dd-180">指向在第一部電腦上建立的「BizTalk 管理」資料庫。</span><span class="sxs-lookup"><span data-stu-id="856dd-180">Point to the BizTalk Management database created on the first computer.</span></span> <span data-ttu-id="856dd-181">這代表您想要有 Web 伺服器環境的 Windows SharePoint Services。</span><span class="sxs-lookup"><span data-stu-id="856dd-181">This indicates to Windows SharePoint Services that you intend to have a Web server environment.</span></span> <span data-ttu-id="856dd-182">指向現有內容資料庫以擴充網站。</span><span class="sxs-lookup"><span data-stu-id="856dd-182">Extend the Web site by pointing to the existing content database.</span></span>  
  
-   <span data-ttu-id="856dd-183">您必須在 Web 伺服器環境中的每部 Windows SharePoint Services 電腦上擴充相同的網站 (例如，預設網站在連接埠 80)。</span><span class="sxs-lookup"><span data-stu-id="856dd-183">You must extend the same Web site (for example, the default Web site on port 80) on each Windows SharePoint Services computer in the Web server environment.</span></span>  
  
-   <span data-ttu-id="856dd-184">在每部 NLB 主控件上必須以相同方式安裝和設定 BTSharePointAdapterWS。</span><span class="sxs-lookup"><span data-stu-id="856dd-184">The BTSharePointAdapterWS must be installed and configured the same way on each of the NLB hosts.</span></span> <span data-ttu-id="856dd-185">您必須設定下列 NLB 設定：</span><span class="sxs-lookup"><span data-stu-id="856dd-185">You must configure the following NLB settings:</span></span>  
  
    -   <span data-ttu-id="856dd-186">通訊協定：TCP</span><span class="sxs-lookup"><span data-stu-id="856dd-186">Protocol: TCP</span></span>  
  
    -   <span data-ttu-id="856dd-187">連接埠：80 (已經安裝及設定 Windows SharePoint Services 配接器 Web 服務的 IIS 網站的 HTTP 連接埠)。</span><span class="sxs-lookup"><span data-stu-id="856dd-187">Ports: 80 (The HTTP Port of the IIS Web site where the Windows SharePoint Services adapter Web service has been installed and configured)</span></span>  
  
    -   <span data-ttu-id="856dd-188">篩選模式：多個主控件</span><span class="sxs-lookup"><span data-stu-id="856dd-188">Filtering mode: Multiple host</span></span>  
  
    -   <span data-ttu-id="856dd-189">相似性：無</span><span class="sxs-lookup"><span data-stu-id="856dd-189">Affinity: None</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="856dd-190">此設定只能用於不是為 HTTPS 設定的網站。</span><span class="sxs-lookup"><span data-stu-id="856dd-190">This setting can be used only if the site is not configured for HTTPS.</span></span> <span data-ttu-id="856dd-191">若 BTSharePointAdapterWS Web 服務是安裝在 HTTPS 的網站上，就必須使用單一用戶端相似性。</span><span class="sxs-lookup"><span data-stu-id="856dd-191">If the BTSharePointAdapterWS Web service is installed on a site with HTTPS, then you must use Single-client affinity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="856dd-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="856dd-192">See Also</span></span>  
 <span data-ttu-id="856dd-193">[Windows SharePoint Services 配接器](../core/windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="856dd-193">[Windows SharePoint Services Adapter](../core/windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="856dd-194">單一伺服器部署</span><span class="sxs-lookup"><span data-stu-id="856dd-194">Single-Server Deployment</span></span>](../core/single-server-deployment.md)