---
title: HTTP 配接器 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: f3bd8172-15c4-42fa-aa17-e4bed9d4aba4
caps.latest.revision: 32
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4002fa7c1b310f5b77806eb0f1b222c015cd989
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023204"
---
# <a name="http-adapter-biztalk-server-sample"></a><span data-ttu-id="f1549-102">HTTP 配接器 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="f1549-102">HTTP Adapter (BizTalk Server Sample)</span></span>
<span data-ttu-id="f1549-103">HTTP 配接器範例會示範如何實作用於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的「要求/回應」和「請求/回應」範例。</span><span class="sxs-lookup"><span data-stu-id="f1549-103">The HTTP Adapter sample demonstrates how to implement the request/response and solicit/response communication paradigms used in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="f1549-104">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="f1549-104">Where to Find This Sample</span></span>  
 <span data-ttu-id="f1549-105">*\<範例路徑\>* \AdaptersDevelopment\HttpAdapter\\</span><span class="sxs-lookup"><span data-stu-id="f1549-105">*\<Samples Path\>* \AdaptersDevelopment\HttpAdapter\\</span></span>  

 <span data-ttu-id="f1549-106">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="f1549-106">The following table shows the files in this sample and describes their purpose.</span></span>  

|<span data-ttu-id="f1549-107">檔案</span><span class="sxs-lookup"><span data-stu-id="f1549-107">File(s)</span></span>|<span data-ttu-id="f1549-108">描述</span><span class="sxs-lookup"><span data-stu-id="f1549-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1549-109">\Design-Time\Adapter Management</span><span class="sxs-lookup"><span data-stu-id="f1549-109">\Design-Time\Adapter Management</span></span>|<span data-ttu-id="f1549-110">包含實作此配接器之設計階段部分的專案。</span><span class="sxs-lookup"><span data-stu-id="f1549-110">Contains the project that implements the design time portion of this adapter.</span></span>|  
|<span data-ttu-id="f1549-111">\Run-Time\HttpReceive</span><span class="sxs-lookup"><span data-stu-id="f1549-111">\Run-Time\HttpReceive</span></span>|<span data-ttu-id="f1549-112">包含實作要求/回應配接器通訊模式的專案。</span><span class="sxs-lookup"><span data-stu-id="f1549-112">Contains the project that implements the request/response adapter communication pattern.</span></span> <span data-ttu-id="f1549-113">這是外掛式接收器。</span><span class="sxs-lookup"><span data-stu-id="f1549-113">This is an isolated receiver.</span></span>|  
|<span data-ttu-id="f1549-114">\Run-Time\HttpSend</span><span class="sxs-lookup"><span data-stu-id="f1549-114">\Run-Time\HttpSend</span></span>|<span data-ttu-id="f1549-115">包含實作請求/回應配接器通訊模式的專案。</span><span class="sxs-lookup"><span data-stu-id="f1549-115">Contains the project that implements the solicit/response adapter communication pattern.</span></span>|  

## <a name="how-to-use-this-sample"></a><span data-ttu-id="f1549-116">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="f1549-116">How to Use This Sample</span></span>  
 <span data-ttu-id="f1549-117">這個範例是要做為您用來開發自訂配接器的架構。</span><span class="sxs-lookup"><span data-stu-id="f1549-117">This sample is meant as a framework for you to use in developing custom adapters.</span></span> <span data-ttu-id="f1549-118">在某些情況下，BizTalk Server 可能需要訊息傳輸到特定的自訂應用程式，或使用的通訊協定的原生的配接器不存在。</span><span class="sxs-lookup"><span data-stu-id="f1549-118">In some cases BizTalk Server may need to transport messages to a specific custom application or use a protocol for which a native adapter that does not exist.</span></span> <span data-ttu-id="f1549-119">有些協力廠商有撰寫配接器以支援其他的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f1549-119">Third-party companies have written adapters to support additional protocols.</span></span> <span data-ttu-id="f1549-120">在決定要撰寫自訂配接器之前，您必須判斷是否有適用於通訊協定的配接器。</span><span class="sxs-lookup"><span data-stu-id="f1549-120">You may want to determine if there is an adapter for your protocol before deciding to write a custom adapter.</span></span> <span data-ttu-id="f1549-121">如果您找不到支援您通訊需求的配接器，即可開發自己的自訂配接器。</span><span class="sxs-lookup"><span data-stu-id="f1549-121">If you are unable to locate an adapter to support your communication requirements, you can develop your own custom adapter.</span></span>  

 <span data-ttu-id="f1549-122">撰寫自訂配接器可能會是具有挑戰性的工作。</span><span class="sxs-lookup"><span data-stu-id="f1549-122">Writing a custom adapter can be a challenging exercise.</span></span> <span data-ttu-id="f1549-123">為了簡化這項程序，Microsoft 開發了稱為「配接器架構」的基礎。</span><span class="sxs-lookup"><span data-stu-id="f1549-123">To simplify this process Microsoft has developed a foundation called the Adapter Framework.</span></span> <span data-ttu-id="f1549-124">您可以使用此架構為基礎，您的開發，以及 BizTalk Server SDK 中的範例配接器程式碼。</span><span class="sxs-lookup"><span data-stu-id="f1549-124">You can use this framework as a basis for your development along with sample adapter source code in the BizTalk Server SDK.</span></span>  <span data-ttu-id="f1549-125">如需有關自訂配接器以及配接器架構的詳細資訊，請參閱**另請參閱**這份文件結尾的區段。</span><span class="sxs-lookup"><span data-stu-id="f1549-125">For more information on custom adapters, and the Adapter Framework, please refer to the **See Also** section at the end of this document.</span></span>  

## <a name="building-and-initializing-the-sample-adapter"></a><span data-ttu-id="f1549-126">建置和初始化範例配接器</span><span class="sxs-lookup"><span data-stu-id="f1549-126">Building and Initializing the Sample Adapter</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="f1549-127">如果 BizTalk 安裝是 64 位元，或安裝位置已有修改，則需要隨之變更 OutboundAssemblyPath、InboundAssemblyPath、AdapterMgmtAssemblyPath。</span><span class="sxs-lookup"><span data-stu-id="f1549-127">If the BizTalk installation is 64-bit or the location of installation is modified, OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath would need to be changed accordingly.</span></span>  

#### <a name="to-build-and-initialize-the-http-adapter-sample"></a><span data-ttu-id="f1549-128">若要建置和初始化 HTTP 配接器範例</span><span class="sxs-lookup"><span data-stu-id="f1549-128">To build and initialize the HTTP Adapter sample</span></span>  

1. <span data-ttu-id="f1549-129">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="f1549-129">In a command window, navigate to the following folder:</span></span>  

    <span data-ttu-id="f1549-130">\<*範例路徑*\>\AdaptersDevelopment\HttpAdapter</span><span class="sxs-lookup"><span data-stu-id="f1549-130">\<*Samples Path*\>\AdaptersDevelopment\HttpAdapter</span></span>  

2. <span data-ttu-id="f1549-131">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f1549-131">Run the file Setup.bat, which performs the following actions:</span></span>  

   -   <span data-ttu-id="f1549-132">編譯 HTTP 配接器及其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="f1549-132">Compiles the HTTPAdapter and all of its dependencies.</span></span>  

   -   <span data-ttu-id="f1549-133">建立由配接器的接收者端所使用 Internet Information Services (IIS) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f1549-133">Creates an Internet Information Services (IIS) application used by the receiver side of the adapter.</span></span>  

   <span data-ttu-id="f1549-134">在 IIS 7.0 上，您必須確定正在執行此 IIS 應用程式之應用程式集區的識別屬於下列群組的成員：</span><span class="sxs-lookup"><span data-stu-id="f1549-134">On IIS 7.0, you must ensure the identity of the application pool running this IIS application is a member of the following groups:</span></span>  

-   <span data-ttu-id="f1549-135">BizTalk 外掛式主控件使用者群組。</span><span class="sxs-lookup"><span data-stu-id="f1549-135">BizTalk Isolated Host Users group.</span></span>  

-   <span data-ttu-id="f1549-136">IIS_WPG 群組。</span><span class="sxs-lookup"><span data-stu-id="f1549-136">IIS_WPG group.</span></span>  

-   <span data-ttu-id="f1549-137">在 IIS 7.0 上，您必須移轉應用程式，才能使其在整合式 .NET 模式下運作。</span><span class="sxs-lookup"><span data-stu-id="f1549-137">On IIS 7.0, you must migrate the application to work with the Integrated .NET mode.</span></span> <span data-ttu-id="f1549-138">您可以移轉應用程式組態，包括的內容\<httpHandlers\>組態 區段中的，使用下列從命令列視窗 （視窗必須以系統管理員身分執行）：</span><span class="sxs-lookup"><span data-stu-id="f1549-138">You can migrate the application configuration, including the contents of the \<httpHandlers\> configuration section, by using the following from a command line window (the window must be running as Administrator):</span></span>  

    ```  
    %systemroot%\system32\inetsrv\APPCMD.EXE migrate config "Default Web Site/HttpReceive"  
    ```  

-   <span data-ttu-id="f1549-139">在移轉應用程式之後，該應用程式便會在「一般」與「整合式 .NET」兩種模式下執行，而且也會在下層的平台上執行。</span><span class="sxs-lookup"><span data-stu-id="f1549-139">After you migrate your application, it will run in both Classic and Integrated .NET modes, as well as on downlevel platforms.</span></span>  

> [!NOTE]
>  <span data-ttu-id="f1549-140">在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1549-140">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  

> [!NOTE]
>  <span data-ttu-id="f1549-141">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="f1549-141">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="f1549-142">使用此金鑰組簽署所產生的組件。</span><span class="sxs-lookup"><span data-stu-id="f1549-142">Use this key pair to sign the resulting assemblies.</span></span>  

> [!NOTE]
>  <span data-ttu-id="f1549-143">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="f1549-143">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="f1549-144">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="f1549-144">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  

## <a name="registering-the-sample-adapter"></a><span data-ttu-id="f1549-145">註冊範例配接器</span><span class="sxs-lookup"><span data-stu-id="f1549-145">Registering the Sample Adapter</span></span>  

#### <a name="to-register-the-http-adapter-sample"></a><span data-ttu-id="f1549-146">若要註冊此 HTTP 配接器範例</span><span class="sxs-lookup"><span data-stu-id="f1549-146">To register the HTTP Adapter sample</span></span>  

1. <span data-ttu-id="f1549-147">在 Windows 檔案總管中，瀏覽至安裝磁碟機[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，然後瀏覽至\<範例路徑\>\AdaptersDevelopment\HTTPAdapter。</span><span class="sxs-lookup"><span data-stu-id="f1549-147">In Windows Explorer, navigate to the installation drive for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then navigate to \<Samples Path\>\AdaptersDevelopment\HTTPAdapter.</span></span>  

2. <span data-ttu-id="f1549-148">若要將範例配接器新增至登錄中，按兩下**HTTP.NET.reg**。</span><span class="sxs-lookup"><span data-stu-id="f1549-148">To add the sample adapter to the registry, double-click **HTTP.NET.reg**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="f1549-149">HTTP.NET.reg 包含硬式編碼路徑[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f1549-149">HTTP.NET.reg includes hard-coded paths to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation directory.</span></span> <span data-ttu-id="f1549-150">如果您未安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在預設位置或升級您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來自舊版本的安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須修改檔案 HTTP.NET.reg 適當的路徑。</span><span class="sxs-lookup"><span data-stu-id="f1549-150">If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the default location or if you upgraded your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation from a previous version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must modify the file HTTP.NET.reg with the appropriate paths.</span></span> <span data-ttu-id="f1549-151">更新與 "OutboundAssemblyPath" 和 "AdapterMgmtAssemblyPath" 值關聯的路徑，使它們指向特定檔案的正確位置。</span><span class="sxs-lookup"><span data-stu-id="f1549-151">Update the paths associated with the "OutboundAssemblyPath" and "AdapterMgmtAssemblyPath" values to point to the correct location of the specified files.</span></span>  
   > 
   > [!IMPORTANT]
   >  <span data-ttu-id="f1549-152">如果您在 64 位元電腦上安裝 BizTalk，可將所有 HKEY_CLASSES_ROOT\CLSID\ 登錄項目執行個體都變更為 hkey_classes_root\wow6432node\clsid \ 中**HTTP.NET.reg**登錄檔。</span><span class="sxs-lookup"><span data-stu-id="f1549-152">If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **HTTP.NET.reg** registry file.</span></span>  

3. <span data-ttu-id="f1549-153">在 **登錄編輯程式**  對話方塊中，按一下**是**以將範例配接器新增至登錄，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f1549-153">In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK**.</span></span>  

4. <span data-ttu-id="f1549-154">若要在關閉 Windows 檔案總管中，**檔案**功能表上，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="f1549-154">To close Windows Explorer, on the **File** menu, click **Close**.</span></span>  

## <a name="installing-the-sample-adapter"></a><span data-ttu-id="f1549-155">安裝範例配接器</span><span class="sxs-lookup"><span data-stu-id="f1549-155">Installing the Sample Adapter</span></span>  

#### <a name="to-install-the-http-adapter-sample"></a><span data-ttu-id="f1549-156">若要安裝此 HTTP 配接器範例</span><span class="sxs-lookup"><span data-stu-id="f1549-156">To install the HTTP Adapter sample</span></span>  

1. <span data-ttu-id="f1549-157">按一下 **開始**功能表上，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="f1549-157">Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then select **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="f1549-158">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]樹狀結構，然後展開**BizTalk 群組**樹狀結構，然後展開**平台設定**樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="f1549-158">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] tree, then expand the **BizTalk Group** tree, then expand the **Platform Settings** tree.</span></span>  

3. <span data-ttu-id="f1549-159">以滑鼠右鍵按一下**配接器**，按一下**新增**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="f1549-159">Right-click **Adapters**, click **New**, and then click **Adapter**.</span></span>  

4. <span data-ttu-id="f1549-160">在 **配接器屬性**對話方塊方塊中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="f1549-160">In the **Adapter Properties** dialog box, do the following.</span></span>  


   |  <span data-ttu-id="f1549-161">使用</span><span class="sxs-lookup"><span data-stu-id="f1549-161">Use this</span></span>   |                  <span data-ttu-id="f1549-162">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="f1549-162">To do this</span></span>                  |
   |-------------|----------------------------------------------|
   |    <span data-ttu-id="f1549-163">[屬性]</span><span class="sxs-lookup"><span data-stu-id="f1549-163">Name</span></span>     |              <span data-ttu-id="f1549-164">型別**HTTP.NET**。</span><span class="sxs-lookup"><span data-stu-id="f1549-164">Type **HTTP.NET**.</span></span>              |
   |   <span data-ttu-id="f1549-165">配接器</span><span class="sxs-lookup"><span data-stu-id="f1549-165">Adapter</span></span>   | <span data-ttu-id="f1549-166">選取  **HTTP.NET**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f1549-166">Select **HTTP.NET** from the drop-down list.</span></span> |
   | <span data-ttu-id="f1549-167">描述</span><span class="sxs-lookup"><span data-stu-id="f1549-167">Description</span></span> |      <span data-ttu-id="f1549-168">型別**範例 HTTP.NET 配接器**。</span><span class="sxs-lookup"><span data-stu-id="f1549-168">Type **Sample HTTP.NET Adapter**.</span></span>       |


5. <span data-ttu-id="f1549-169">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f1549-169">Click **OK**.</span></span>  

6. <span data-ttu-id="f1549-170">配接器隨即會出現在 BizTalk 管理主控台右側視窗的配接器清單中。</span><span class="sxs-lookup"><span data-stu-id="f1549-170">The adapter now appears in the list of adapters in the right window of the BizTalk Administration console.</span></span>  

## <a name="stopping-and-restarting-the-host-instance"></a><span data-ttu-id="f1549-171">停止並重新啟動主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="f1549-171">Stopping and Restarting the Host Instance</span></span>  

#### <a name="to-stop-and-restart-the-host-instance-for-the-http-adapter-sample"></a><span data-ttu-id="f1549-172">若要停止並重新啟動 HTTP 配接器範例的主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="f1549-172">To stop and restart the host instance for the HTTP Adapter sample</span></span>  

1. <span data-ttu-id="f1549-173">按一下 **開始**功能表上，選取**所有程式**，選取[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後選取[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f1549-173">Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and select [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  

2. <span data-ttu-id="f1549-174">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]樹狀結構，然後展開**平台設定**，然後按一下**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="f1549-174">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] tree, then expand **Platform Settings**, and click **Host Instances**.</span></span>  

3. <span data-ttu-id="f1549-175">在 [結果] 窗格中，以滑鼠右鍵按一下主控件執行個體 （通常是電腦名稱），，然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="f1549-175">In the results pane, right-click the host instance (typically, the computer name), and then click **Stop**.</span></span>  

    <span data-ttu-id="f1549-176">主控件執行個體狀態會變更為**已停止**。</span><span class="sxs-lookup"><span data-stu-id="f1549-176">The status of the host instance changes to **Stopped**.</span></span>  

4. <span data-ttu-id="f1549-177">在 [結果] 窗格中，以滑鼠右鍵按一下主控件執行個體，然後**啟動**。</span><span class="sxs-lookup"><span data-stu-id="f1549-177">In the results pane, right-click the host instance, and then click **Start**.</span></span>  

   <span data-ttu-id="f1549-178">現在，您的應用程式可開始使用 HTTP.NET 配接器。</span><span class="sxs-lookup"><span data-stu-id="f1549-178">The HTTP.NET adapter is now ready to be used by your application.</span></span> <span data-ttu-id="f1549-179">設定配接器，格式**虛擬目錄**傳輸屬性屬於表單： /httpreceive/httpreceive.aspx?optionalQueryString。</span><span class="sxs-lookup"><span data-stu-id="f1549-179">When configuring the adapter, the format for the **Virtual Directory** transport property is of the form: /httpreceive/httpreceive.aspx?optionalQueryString.</span></span>  

## <a name="comments"></a><span data-ttu-id="f1549-180">註解</span><span class="sxs-lookup"><span data-stu-id="f1549-180">Comments</span></span>  
 <span data-ttu-id="f1549-181">中提供的 BaseAdapter 類別使用 HTTP.NET 配接器可讓*\<範例路徑\>* \AdaptersDevelopment\BaseAdapter\v1.0...2\\。</span><span class="sxs-lookup"><span data-stu-id="f1549-181">The HTTP.NET adapter makes use of the BaseAdapter classes provided in *\<Samples Path\>* \AdaptersDevelopment\BaseAdapter\v1.0..2\\.</span></span> <span data-ttu-id="f1549-182">這些提供於 BaseAdapter 專案中的類別是為了加速配接器的開發。</span><span class="sxs-lookup"><span data-stu-id="f1549-182">The classes provided in the BaseAdapter project are intended to accelerate adapter development.</span></span> <span data-ttu-id="f1549-183">如需所提供類別的詳細資料，請參閱 BaseAdapter 程式碼註解。</span><span class="sxs-lookup"><span data-stu-id="f1549-183">Refer to the BaseAdapter code comments for details about the classes provided.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f1549-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1549-184">See Also</span></span>  
 <span data-ttu-id="f1549-185">[註冊配接器](../core/registering-an-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-185">[Registering an Adapter](../core/registering-an-adapter.md) </span></span>  
 <span data-ttu-id="f1549-186">[配接器範例-用法](../core/adapter-samples-usage.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-186">[Adapter Samples - Usage](../core/adapter-samples-usage.md) </span></span>  
 <span data-ttu-id="f1549-187">[開發自訂配接器](../core/developing-custom-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-187">[Developing Custom Adapters](../core/developing-custom-adapters.md) </span></span>  
 <span data-ttu-id="f1549-188">[什麼是配接器架構？](../core/what-is-the-adapter-framework.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-188">[What Is the Adapter Framework?](../core/what-is-the-adapter-framework.md) </span></span>  
 <span data-ttu-id="f1549-189">[使用配接器架構工具](../core/using-the-adapter-framework-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-189">[Using the Adapter Framework Tools](../core/using-the-adapter-framework-tools.md) </span></span>  
 <span data-ttu-id="f1549-190">[開發接收配接器](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-190">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="f1549-191">[開發傳送配接器](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-191">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="f1549-192">[如何部署自訂配接器](../core/how-to-deploy-a-custom-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-192">[How to Deploy a Custom Adapter](../core/how-to-deploy-a-custom-adapter.md) </span></span>  
 <span data-ttu-id="f1549-193">[設計您的配接器的秘訣](../core/tips-for-designing-your-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="f1549-193">[Tips for Designing Your Adapter](../core/tips-for-designing-your-adapter.md) </span></span>  
 [<span data-ttu-id="f1549-194">配接器設計階段設定</span><span class="sxs-lookup"><span data-stu-id="f1549-194">Adapter Design-Time Configuration</span></span>](../core/adapter-design-time-configuration.md)