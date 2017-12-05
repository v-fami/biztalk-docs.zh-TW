---
title: "HTTPRequestResponse |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: 81c66f61-d86c-49cf-8d24-21c67c68bc5a
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 549f343818464a8316246f8b6996755ce5fef136
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="httprequestresponse"></a><span data-ttu-id="335b7-102">HTTPRequestResponse</span><span class="sxs-lookup"><span data-stu-id="335b7-102">HTTPRequestResponse</span></span>
<span data-ttu-id="335b7-103">HTTPRequestResponse 範例會示範如何使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 網際網路伺服器應用程式發展介面 (Internet Server Application Programming Interface，ISAPI) 篩選器，讓 ASP.NET 應用程式與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程進行通訊。</span><span class="sxs-lookup"><span data-stu-id="335b7-103">The HTTPRequestResponse sample demonstrates how to use the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Internet Server Application Programming Interface (ISAPI) filter to allow an ASP.NET application to communicate with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="335b7-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="335b7-104">What This Sample Does</span></span>  
 <span data-ttu-id="335b7-105">在此範例中，ASP.NET 應用程式會提交要求至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ISAPI 篩選器。</span><span class="sxs-lookup"><span data-stu-id="335b7-105">In this sample, the ASP.NET application submits a request to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ISAPI filter.</span></span> <span data-ttu-id="335b7-106">協調流程接著會取用此訊息，並使用同步回應將其傳回 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="335b7-106">The orchestration then consumes this message and returns it to the ASP.NET application using a synchronous response.</span></span> <span data-ttu-id="335b7-107">達到之間的整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程與 ASP.NET 應用程式利用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ISAPI 篩選器。</span><span class="sxs-lookup"><span data-stu-id="335b7-107">You achieve the integration between the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration and the ASP.NET application by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ISAPI filter.</span></span>  
  
 <span data-ttu-id="335b7-108">在此範例中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 ASP.NET 應用程式交換訂單 (po) 和 PO 通知訊息，使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="335b7-108">In this sample, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and an ASP.NET application exchange purchase order (PO) and PO acknowledgement messages using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="335b7-109">ASP.NET 應用程式，使用 HTTP 要求，提交 XML PO 訊息到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="335b7-109">An ASP.NET application, using an HTTP request, submits an XML PO message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
2.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="335b7-110">收到 XML PO 訊息建構 XML PO 通知訊息，並再將該訊息傳送至 HTTP 回應中的 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="335b7-110"> receives the XML PO message and constructs an XML PO acknowledgement message, and then sends that message back to the ASP.NET application in the HTTP response.</span></span>  
  
 <span data-ttu-id="335b7-111">ASP.NET 應用程式收到 XML PO 通知回應後，會使用從回應中擷取的狀態資訊來重新整理 Web 表單。</span><span class="sxs-lookup"><span data-stu-id="335b7-111">The ASP.NET application receives the XML PO acknowledgement response and refreshes the Web form with status information extracted from the response.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="335b7-112">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="335b7-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="335b7-113">*\<範例路徑\>*\AdaptersUsage\HTTPRequestResponse\\</span><span class="sxs-lookup"><span data-stu-id="335b7-113">*\<Samples Path\>*\AdaptersUsage\HTTPRequestResponse\\</span></span>  
  
 <span data-ttu-id="335b7-114">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="335b7-114">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="335b7-115">檔案</span><span class="sxs-lookup"><span data-stu-id="335b7-115">File(s)</span></span>|<span data-ttu-id="335b7-116">Description</span><span class="sxs-lookup"><span data-stu-id="335b7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="335b7-117">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="335b7-117">Cleanup.bat</span></span>|<span data-ttu-id="335b7-118">從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="335b7-118">Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="335b7-119">HTTPRequestResponse.btproj、HTTPRequestResponse.sln</span><span class="sxs-lookup"><span data-stu-id="335b7-119">HTTPRequestResponse.btproj, HTTPRequestResponse.sln</span></span>|<span data-ttu-id="335b7-120">提供 BizTalk 專案的專案和原始程式檔，此專案可以接收 HTTP 要求、處理 PO 訊息，以及發出回應。</span><span class="sxs-lookup"><span data-stu-id="335b7-120">Provides project and source files for the BizTalk project that receives the HTTP request, processes the PO message, and issues the response.</span></span>|  
|<span data-ttu-id="335b7-121">HTTPRequestResponseBinding.xml</span><span class="sxs-lookup"><span data-stu-id="335b7-121">HTTPRequestResponseBinding.xml</span></span>|<span data-ttu-id="335b7-122">提供例如連接埠繫結等自動設定的功能。</span><span class="sxs-lookup"><span data-stu-id="335b7-122">Provides automated setup such as port binding.</span></span>|  
|<span data-ttu-id="335b7-123">POAck.xsd、POSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="335b7-123">POAck.xsd, POSchema.xsd</span></span>|<span data-ttu-id="335b7-124">分別提供 PO 通知和 PO .xml 檔案的結構描述。</span><span class="sxs-lookup"><span data-stu-id="335b7-124">Provides schemas for the PO acknowledgement and PO .xml files, respectively.</span></span>|  
|<span data-ttu-id="335b7-125">POReceiveOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="335b7-125">POReceiveOrchestration.odx</span></span>|<span data-ttu-id="335b7-126">提供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收 PO 的協調流程加以處理，以及發出 PO 通知。</span><span class="sxs-lookup"><span data-stu-id="335b7-126">Provides a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that receives the PO, processes it, and issues the PO acknowledgement.</span></span>|  
|<span data-ttu-id="335b7-127">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="335b7-127">Setup.bat</span></span>|<span data-ttu-id="335b7-128">建置並初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="335b7-128">Builds and initializes this sample.</span></span>|  
|<span data-ttu-id="335b7-129">在 \RequestResponse 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="335b7-129">In the \RequestResponse folder:</span></span><br /><br /> <span data-ttu-id="335b7-130">AssemblyInfo.cs、default.aspx、default.aspx.cs、Global.asax、Global.asax.cs、RequestResponse.csproj、RequestResponse.csproj.webinfo、RequestResponse.sln、Web.config</span><span class="sxs-lookup"><span data-stu-id="335b7-130">AssemblyInfo.cs, default.aspx, default.aspx.cs, Global.asax, Global.asax.cs, RequestResponse.csproj, RequestResponse.csproj.webinfo, RequestResponse.sln, Web.config</span></span>|<span data-ttu-id="335b7-131">所包含的檔案，構成在本範例中當做驅動程式使用的 ASP.NET 應用程式，其中包括專案和方案檔案、ASPX 檔案、Microsoft Visual C# .NET 原始程式檔等等。</span><span class="sxs-lookup"><span data-stu-id="335b7-131">Contains files that constitute the ASP.NET application that serves as a driver for this sample, including project and solution files, ASPX files, Microsoft Visual C# .NET source files, and so on.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="335b7-132">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="335b7-132">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="335b7-133">請使用下列程序，建置和初始化 HTTPRequestResponse 範例。</span><span class="sxs-lookup"><span data-stu-id="335b7-133">Use the following procedure to build and initialize the HTTPRequestResponse sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="335b7-134">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="335b7-134">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="335b7-135">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="335b7-135">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="335b7-136">\<*範例路徑*\>\AdaptersUsage\HTTPRequestResponse</span><span class="sxs-lookup"><span data-stu-id="335b7-136">\<*Samples Path*\>\AdaptersUsage\HTTPRequestResponse</span></span>  
  
2.  <span data-ttu-id="335b7-137">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="335b7-137">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="335b7-138">編譯及設定用來驅動此範例的 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="335b7-138">Compiles and configures the ASP.NET application used to drive this sample.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="335b7-139">在 IIS 管理員中建立應用程式集區，設定**DefaultAppPool**以.NET Framework 版本**.Net Framework v4.0**。</span><span class="sxs-lookup"><span data-stu-id="335b7-139">While creating application pool in IIS Manager, set the **DefaultAppPool** .NET Framework version to **.Net Framework v4.0**.</span></span>  
  
    -   <span data-ttu-id="335b7-140">編譯及部署此範例中所使用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="335b7-140">Compiles and deploys the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration used in this sample.</span></span>  
  
    -   <span data-ttu-id="335b7-141">為這個範例編譯和部署 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="335b7-141">Compiles and deploys the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  
  
    -   <span data-ttu-id="335b7-142">建立並繫結必要[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]連接埠。</span><span class="sxs-lookup"><span data-stu-id="335b7-142">Creates and binds the necessary [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ports.</span></span>  
  
    -   <span data-ttu-id="335b7-143">啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。</span><span class="sxs-lookup"><span data-stu-id="335b7-143">Starts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="335b7-144">您必須變更實作 Web 應用程式的範例程式碼 (Default.aspx.cs) 以反映您的環境：</span><span class="sxs-lookup"><span data-stu-id="335b7-144">You must change the sample code that implements the Web application (Default.aspx.cs) to reflect your environment:</span></span>  
        >   
        >  <span data-ttu-id="335b7-145">http://\<*伺服器名稱*\>/\<*虛擬 dir*\>/BTSHTTPReceive.dll 其中`<servername>`的網站名稱您張貼至伺服器和`<`*虛擬 dir* `>`是這個檔案所在的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="335b7-145">http://\<*server name*\>/\<*virtual dir*\>/BTSHTTPReceive.dll where `<servername>` is the name of the Web server you are posting to, and `<`*virtual dir*`>` is the virtual directory where this file resides.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="335b7-146">在嘗試執行此範例之前，您必須確認 BizTalk 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="335b7-146">You should confirm that BizTalk did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="335b7-147">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="335b7-147">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="335b7-148">使用此金鑰組簽署所產生的組件。</span><span class="sxs-lookup"><span data-stu-id="335b7-148">Use this key pair to sign the resulting assemblies.</span></span> <span data-ttu-id="335b7-149">在嘗試建置專案前，您還必須從 RequestResponse.csproj 檔案中手動移除 default.aspx.resx 和 Global.asax.resx 的參考。</span><span class="sxs-lookup"><span data-stu-id="335b7-149">You must also manually remove the references to default.aspx.resx and Global.asax.resx from the file RequestResponse.csproj before attempting to build that project.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="335b7-150">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="335b7-150">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="335b7-151">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="335b7-151">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="335b7-152">您必須設定和啟用 IIS 才能使用 HTTP 接收配接器。</span><span class="sxs-lookup"><span data-stu-id="335b7-152">You must configure and enable IIS to use the HTTP receive adapter.</span></span> <span data-ttu-id="335b7-153">如需詳細資訊，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="335b7-153">For more information, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).</span></span>  
  
3.  <span data-ttu-id="335b7-154">setup.bat 檔會設定此範例的虛擬目錄，以在與預設網站關聯的 IIS 應用程式集區中執行。</span><span class="sxs-lookup"><span data-stu-id="335b7-154">The setup.bat file configures the virtual directory for this sample to run in the IIS application pool associated with the default web site.</span></span>  <span data-ttu-id="335b7-155">若要設定讓此範例中的使用者內容下執行的虛擬目錄**BizTalk Isolated Host Users**和**「 iis_iurs 」**使用者群組，您應該設定執行新的虛擬目錄IIS 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="335b7-155">To configure the virtual directory for this sample to run under the context of a user in the **BizTalk Isolated Host Users** and **IIS_IURS** user groups, you should configure the virtual directory to run in a new IIS application pool.</span></span> <span data-ttu-id="335b7-156">請依照下列步驟執行，將虛擬目錄設定為在新的 IIS 應用程式集區中執行：</span><span class="sxs-lookup"><span data-stu-id="335b7-156">Configure the virtual directory to run in a new IIS application pool by completing the following steps:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="335b7-157">如果您已經為其他 SDK 範例建立新的應用程式集區，則可以繼續執行下面最後一項步驟。</span><span class="sxs-lookup"><span data-stu-id="335b7-157">If you have already created a new application pool for another SDK sample then you can proceed to the last step below.</span></span>  
  
    1.  <span data-ttu-id="335b7-158">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.</span><span class="sxs-lookup"><span data-stu-id="335b7-158">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
    2.  <span data-ttu-id="335b7-159">在**網際網路資訊服務 (IIS) 管理員**，瀏覽至**應用程式集區**資料夾。</span><span class="sxs-lookup"><span data-stu-id="335b7-159">In the **Internet Information Services (IIS) Manager**, navigate to the **Application Pools** folder.</span></span>  
  
    3.  <span data-ttu-id="335b7-160">以滑鼠右鍵按一下**應用程式集區**資料夾，然後按一下**新增**，**應用程式集區...**</span><span class="sxs-lookup"><span data-stu-id="335b7-160">Right-click the **Application Pools** folder and click **New**, **Application Pool...**</span></span>  
  
    4.  <span data-ttu-id="335b7-161">輸入的名稱**應用程式集區識別碼：** （例如 biztalksdksamples），確認**新應用程式集區使用預設設定**選項已選取，然後按一下**確定**至建立新的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="335b7-161">Enter a name for the **Application Pool ID:** such as BizTalkSDKSamples, verify that the **Use default settings for new application pool** option is selected and click **OK** to create the new application pool.</span></span>  
  
    5.  <span data-ttu-id="335b7-162">以滑鼠右鍵按一下新的應用程式集區，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="335b7-162">Right-click the new application pool and then click **Properties**.</span></span>  
  
    6.  <span data-ttu-id="335b7-163">按一下**識別** 索引標籤的 屬性 對話方塊並變更這個應用程式集區執行使用者為成員的身分識別**BizTalk Isolated Host Users**使用者群組。</span><span class="sxs-lookup"><span data-stu-id="335b7-163">Click the **Identity** tab of the properties dialog box and change the identity under which this application pool runs to a user that is a member of the **BizTalk Isolated Host Users** user group.</span></span>  <span data-ttu-id="335b7-164">此使用者也應該屬於本機**「 iis_iurs 」**使用者群組。</span><span class="sxs-lookup"><span data-stu-id="335b7-164">This user should also be a member of the local **IIS_IURS** user group.</span></span>  
  
    7.  <span data-ttu-id="335b7-165">設定這個 SDK 範例的虛擬目錄為在新的應用程式集區下執行。</span><span class="sxs-lookup"><span data-stu-id="335b7-165">Configure the virtual directory for this SDK sample to run under the new application pool.</span></span> <span data-ttu-id="335b7-166">**應用程式集區**設定位在**虛擬目錄**] 索引標籤的 [虛擬目錄的 [內容] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="335b7-166">The **Application pool** setting is available on the **Virtual Directory** tab of the Virtual Directory properties dialog box.</span></span> <span data-ttu-id="335b7-167">為此範例所建立的虛擬目錄為 HttpRequestResponseSample。</span><span class="sxs-lookup"><span data-stu-id="335b7-167">The virtual directory created for this sample is HttpRequestResponseSample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="335b7-168">執行此範例</span><span class="sxs-lookup"><span data-stu-id="335b7-168">Running This Sample</span></span>  
 <span data-ttu-id="335b7-169">請使用下列程序執行 HTTPRequestResponse 範例。</span><span class="sxs-lookup"><span data-stu-id="335b7-169">Use the following procedure to run the HTTPRequestResponse sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="335b7-170">執行此範例</span><span class="sxs-lookup"><span data-stu-id="335b7-170">To run this sample</span></span>  
  
1.  <span data-ttu-id="335b7-171">在 Internet Explorer 中瀏覽至 http://localhost/RequestResponse/。</span><span class="sxs-lookup"><span data-stu-id="335b7-171">In Internet Explorer, navigate to http://localhost/RequestResponse/.</span></span>  
  
2.  <span data-ttu-id="335b7-172">完成 Web 表單中的必要欄位，然後按一下**訂購**提交訂單。</span><span class="sxs-lookup"><span data-stu-id="335b7-172">Complete the necessary fields in the Web form, and then click **Place Order** to submit your order.</span></span>  
  
3.  <span data-ttu-id="335b7-173">在收到回應後重新整理 Web 表單時，觀察您的訂單狀態。</span><span class="sxs-lookup"><span data-stu-id="335b7-173">Observe the status of your order when the Web form refreshes after receiving a response.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="335b7-174">註解</span><span class="sxs-lookup"><span data-stu-id="335b7-174">Comments</span></span>  
 <span data-ttu-id="335b7-175">**BTSHTTPReceiveISAPI**延伸此範例中使用設定為在單一電腦預設安裝上運作。</span><span class="sxs-lookup"><span data-stu-id="335b7-175">The **BTSHTTPReceiveISAPI** extension used in this sample is configured to work on a single computer default installation.</span></span> <span data-ttu-id="335b7-176">若要擴充此範例以額外的組態，請參閱[HTTP 配接器](../core/http-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="335b7-176">To extend this sample for additional configurations, see [HTTP Adapter](../core/http-adapter.md).</span></span>  
  
 <span data-ttu-id="335b7-177">您可將此範例擴充至一般需透過 Web 表單或 HTTP 提交資料給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="335b7-177">You can extend this sample to applications that are required to submit data to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] through a Web form, or through HTTP in general.</span></span> <span data-ttu-id="335b7-178">透過擴充此範例的 ASP.NET 應用程式部分，您可以查詢更多資訊，以及在提交資料給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 前先執行其他前置處理。</span><span class="sxs-lookup"><span data-stu-id="335b7-178">By extending the ASP.NET application portion of this sample, you can query for more information and perform other preprocessing before submitting the data to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="335b7-179">請參閱</span><span class="sxs-lookup"><span data-stu-id="335b7-179">See Also</span></span>  
 [<span data-ttu-id="335b7-180">HTTP 配接器範例</span><span class="sxs-lookup"><span data-stu-id="335b7-180">HTTP Adapter Samples</span></span>](../core/http-adapter-samples.md)