---
title: "教學課程： 將資料寫入至 PeopleSoft Enterprise 使用 BizTalk Adapter for PeopleSoft Enterprise |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837dd4db-576d-41c1-9fe8-e1e46861270b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9c4c0714c28f426ccfaa2799bd16463124e6e52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-peoplesoft-enterprise-to-write-data-to-peoplesoft-enterprise"></a><span data-ttu-id="21da8-102">教學課程： 將資料寫入至 PeopleSoft Enterprise 使用 BizTalk Adapter for PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="21da8-102">Tutorial: Using the BizTalk Adapter for PeopleSoft Enterprise to Write Data to PeopleSoft Enterprise</span></span>
<span data-ttu-id="21da8-103">BizTalk Adapter for PeopleSoft Enterprise 可用來將資料寫入至 PeopleSoft 系統，以接收來自交易夥伴或內部應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="21da8-103">The BizTalk Adapter for PeopleSoft Enterprise can be used to write data to a PeopleSoft System with information received from a trading partner or internal application.</span></span> <span data-ttu-id="21da8-104">這個逐步解說將說明此功能的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="21da8-104">This walkthrough describes an SDK sample that illustrates this functionality.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="21da8-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="21da8-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="21da8-106">Java 2 平台上必須安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk Adapter for PeopleSoft Enterprise 上執行。</span><span class="sxs-lookup"><span data-stu-id="21da8-106">The Java 2 Platform must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.</span></span>  
  
-   <span data-ttu-id="21da8-107">PeopleSoft Java Object Adapter JAR 檔案， **psjoa.jar**應複製到可存取的資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk Adapter for PeopleSoft Enterprise 上執行。</span><span class="sxs-lookup"><span data-stu-id="21da8-107">The PeopleSoft Java Object Adapter JAR file, **psjoa.jar** should be copied to a folder that is accessible to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.</span></span>  
  
-   <span data-ttu-id="21da8-108">執行 BizTalk Adapter for PeopleSoft Enterprise 的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上必須已安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。</span><span class="sxs-lookup"><span data-stu-id="21da8-108">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="21da8-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="21da8-109">What This Sample Does</span></span>  
 <span data-ttu-id="21da8-110">此範例會收取資料夾從某個 XML 檔案、 將該檔案傳送至協調流程，並再使用 BizTalk Adapter for PeopleSoft Enterprise 從 XML 檔案中的資料在 PeopleSoft 系統中建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="21da8-110">This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for PeopleSoft Enterprise to create a record in the PeopleSoft system from the data in the XML file.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="21da8-111">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="21da8-111">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="21da8-112">以 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計的這個範例，其建立的目的在示範將 BizTalk Adapter for PeopleSoft Enterprise 與 BizTalk 協調流程搭配使用的基本功能。</span><span class="sxs-lookup"><span data-stu-id="21da8-112">This sample was designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and was created to illustrate basic functionality using the BizTalk Adapter for PeopleSoft Enterprise with a BizTalk orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="21da8-113">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="21da8-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="21da8-114">這個範例位於下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="21da8-114">The sample is located in the following folder:</span></span>  
  
 <span data-ttu-id="21da8-115">\Program Files\Microsoft BizTalk Adapters for enterprise \Sdk\PeopleSoftOneWaySend</span><span class="sxs-lookup"><span data-stu-id="21da8-115">\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftOneWaySend</span></span>  
  
 <span data-ttu-id="21da8-116">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="21da8-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="21da8-117">**執行階段專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="21da8-117">**Runtime Project Filename**</span></span>|<span data-ttu-id="21da8-118">**執行階段專案檔案描述**</span><span class="sxs-lookup"><span data-stu-id="21da8-118">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="21da8-119">OneWaySend.btproj，</span><span class="sxs-lookup"><span data-stu-id="21da8-119">OneWaySend.btproj,</span></span><br /><br /> <span data-ttu-id="21da8-120">OneWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="21da8-120">OneWaySend.sln</span></span>|<span data-ttu-id="21da8-121">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="21da8-121">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="21da8-122">LOCATIONService.xsd、</span><span class="sxs-lookup"><span data-stu-id="21da8-122">LOCATIONService.xsd,</span></span><br /><br /> <span data-ttu-id="21da8-123">LOCATIONService_1.xsd、</span><span class="sxs-lookup"><span data-stu-id="21da8-123">LOCATIONService_1.xsd,</span></span><br /><br /> <span data-ttu-id="21da8-124">LOCATIONService_2.xsd</span><span class="sxs-lookup"><span data-stu-id="21da8-124">LOCATIONService_2.xsd</span></span>|<span data-ttu-id="21da8-125">這個應用程式的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="21da8-125">Schema files for the application.</span></span> <span data-ttu-id="21da8-126">**注意：**使用原先建立在專案中的配接器結構描述檔案**新增配接器中繼資料精靈**。</span><span class="sxs-lookup"><span data-stu-id="21da8-126">**Note:**  The adapter schema files in the project were originally created using the **Add Adapter Metadata Wizard**.</span></span> <span data-ttu-id="21da8-127">如需 [新增配接器中繼資料精靈] 的詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的「如何將配接器中繼資料新增至 BizTalk 專案」主題。</span><span class="sxs-lookup"><span data-stu-id="21da8-127">For more information on the Add Adapter Metadata Wizard see the topic "How to Add Adapter Metadata to a BizTalk Project" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>|  
|<span data-ttu-id="21da8-128">PeopleSoftOneWaySend.odx</span><span class="sxs-lookup"><span data-stu-id="21da8-128">PeopleSoftOneWaySend.odx</span></span>|<span data-ttu-id="21da8-129">這個應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="21da8-129">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="21da8-130">PeopleSoftOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="21da8-130">PeopleSoftOneWaySend.snk</span></span>|<span data-ttu-id="21da8-131">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="21da8-131">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="21da8-132">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="21da8-132">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-peoplesoft-enterprise-adapter"></a><span data-ttu-id="21da8-133">建立 PeopleSoft Enterprise 配接器的新執行個體</span><span class="sxs-lookup"><span data-stu-id="21da8-133">Create a new instance of the PeopleSoft Enterprise adapter</span></span>  
  
1.  <span data-ttu-id="21da8-134">啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="21da8-134">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="21da8-135">按一下**啟動**，**所有程式**， [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]， **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="21da8-135">Click **Start**, **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="21da8-136">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="21da8-136">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="21da8-137">以滑鼠右鍵按一下**配接器**指向**新增**，**配接器...**</span><span class="sxs-lookup"><span data-stu-id="21da8-137">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="21da8-138">若要顯示**配接器屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-138">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="21da8-139">輸入一個值**名稱**欄位，例如**PeopleSoft**。</span><span class="sxs-lookup"><span data-stu-id="21da8-139">Enter a value for the **Name** field, for example **PeopleSoft**.</span></span>  
  
5.  <span data-ttu-id="21da8-140">選取**PeopleSoft enterprise （)**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="21da8-140">Select **PeopleSoft Enterprise(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-send-port"></a><span data-ttu-id="21da8-141">建立 BizTalk 傳送埠</span><span class="sxs-lookup"><span data-stu-id="21da8-141">Create a BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="21da8-142">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="21da8-142">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="21da8-143">以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠**顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-143">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="21da8-144">輸入一個值**名稱**欄位，例如**PeopleSoftOneWaySP**。</span><span class="sxs-lookup"><span data-stu-id="21da8-144">Enter a value for the **Name** field, for example **PeopleSoftOneWaySP**.</span></span>  
  
4.  <span data-ttu-id="21da8-145">從使用中的配接器清單中選取 PeopleSoft 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-145">Select the PeopleSoft adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="21da8-146">這個值是在建立 PeopleSoft Enterprise 配接器時指定了名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="21da8-146">This value is the name that was specified when the PeopleSoft Enterprise adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
5.  <span data-ttu-id="21da8-147">輸入下列值**配接器必要屬性**:</span><span class="sxs-lookup"><span data-stu-id="21da8-147">Enter the following values for the **Adapter Required Properties**:</span></span>  
  
    |<span data-ttu-id="21da8-148">**屬性**</span><span class="sxs-lookup"><span data-stu-id="21da8-148">**Property**</span></span>|<span data-ttu-id="21da8-149">**值**</span><span class="sxs-lookup"><span data-stu-id="21da8-149">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="21da8-150">應用程式伺服器路徑</span><span class="sxs-lookup"><span data-stu-id="21da8-150">Application server path</span></span>|<span data-ttu-id="21da8-151">PeopleSoft 伺服器的機器與連接埠位置，例如 //PSServer:8888。</span><span class="sxs-lookup"><span data-stu-id="21da8-151">PeopleSoft Server's machine and port location, for example //PSServer:8888.</span></span> <span data-ttu-id="21da8-152">**注意：**如果未指定連接埠號碼，會使用預設連接埠 9000，因此在您上面的範例可以輸入 //PSServer 值如果 PeopleSoft 伺服器使用預設的連接埠值 9000。</span><span class="sxs-lookup"><span data-stu-id="21da8-152">**Note:**  If you do not specify a port number, the default port of 9000 is used so in the example above you could enter a value of //PSServer if the PeopleSoft Server uses the default port value of 9000.</span></span>|  
    |<span data-ttu-id="21da8-153">JAVA_HOME</span><span class="sxs-lookup"><span data-stu-id="21da8-153">JAVA_HOME</span></span>|<span data-ttu-id="21da8-154">與 Java 2 平台 SDK 檔案相關聯之主目錄的路徑，例如 C:\j2sdk1.4.2_08</span><span class="sxs-lookup"><span data-stu-id="21da8-154">Path to the home directory associated with the Java 2 Platform SDK files, for example C:\j2sdk1.4.2_08</span></span>|  
    |<span data-ttu-id="21da8-155">密碼</span><span class="sxs-lookup"><span data-stu-id="21da8-155">Password</span></span>|<span data-ttu-id="21da8-156">連接至 PeopleSoft 系統時使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="21da8-156">Password used when connecting to the PeopleSoft system.</span></span>|  
    |<span data-ttu-id="21da8-157">PeopleSoft 8.x JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="21da8-157">PeopleSoft 8.x JAR files</span></span>|<span data-ttu-id="21da8-158">PeopleSoft Java Object Adapter JAR 檔案位置， **psjoa.jar**，例如 C:\JARS\psjoa.jar。</span><span class="sxs-lookup"><span data-stu-id="21da8-158">Location of the PeopleSoft Java Object Adapter JAR file, **psjoa.jar**, for example C:\JARS\psjoa.jar.</span></span>|  
    |<span data-ttu-id="21da8-159">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="21da8-159">User name</span></span>|<span data-ttu-id="21da8-160">用於連接至 PeopleSoft 系統的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="21da8-160">Username for connecting to the PeopleSoft system.</span></span>|  
  
6.  <span data-ttu-id="21da8-161">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="21da8-161">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="21da8-162">選取**XML 傳輸**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="21da8-162">Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="21da8-163">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="21da8-163">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-file-receive-port"></a><span data-ttu-id="21da8-164">建立檔案接收埠</span><span class="sxs-lookup"><span data-stu-id="21da8-164">Create a file receive port</span></span>  
  
1.  <span data-ttu-id="21da8-165">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="21da8-165">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="21da8-166">以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠**以顯示 [接收埠屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-166">Right-click the Receive Ports folder and then click **New**, **One-way Receive Port** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="21da8-167">輸入一個值**名稱**欄位，例如**PeopleSoftOneWayFileRP**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="21da8-167">Enter a value for the **Name** field, for example **PeopleSoftOneWayFileRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-file-receive-location"></a><span data-ttu-id="21da8-168">建立檔案接收位置</span><span class="sxs-lookup"><span data-stu-id="21da8-168">Create a file receive location</span></span>  
  
1.  <span data-ttu-id="21da8-169">建立要由檔案接收位置監視的資料夾，例如 C:\Filesource。</span><span class="sxs-lookup"><span data-stu-id="21da8-169">Create a folder to be monitored by the file receive location, for example C:\Filesource.</span></span>  
  
2.  <span data-ttu-id="21da8-170">以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置**顯示**接收位置屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-170">Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="21da8-171">輸入一個值**名稱**欄位，例如**PeopleSoftOneWayFileRL**。</span><span class="sxs-lookup"><span data-stu-id="21da8-171">Enter a value for the **Name** field, for example **PeopleSoftOneWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="21da8-172">選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-172">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="21da8-173">輸入您稍早建立的資料夾位置**接收資料夾**屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="21da8-173">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="21da8-174">選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="21da8-174">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="21da8-175">以滑鼠右鍵按一下接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="21da8-175">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="modify-the-adapter-schema-target-namespace-property"></a><span data-ttu-id="21da8-176">修改配接器結構描述目標命名空間屬性</span><span class="sxs-lookup"><span data-stu-id="21da8-176">Modify the Adapter schema target namespace property</span></span>  
  
1.  <span data-ttu-id="21da8-177">啟動 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 並開啟 OneWaySend.sln。</span><span class="sxs-lookup"><span data-stu-id="21da8-177">Launch [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and open OneWaySend.sln.</span></span> <span data-ttu-id="21da8-178">按一下**檔案**，**開啟**，**專案/方案...**</span><span class="sxs-lookup"><span data-stu-id="21da8-178">Click **File**, **Open**, **Project/Solution…**</span></span> <span data-ttu-id="21da8-179">若要顯示**開啟專案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-179">to display the **Open Project** dialog.</span></span>  
  
2.  <span data-ttu-id="21da8-180">瀏覽到 OneWaySend.sln 檔案，請按一下以選取此檔案，然後按一下**開啟**來開啟包含範例專案的方案。</span><span class="sxs-lookup"><span data-stu-id="21da8-180">Browse to the OneWaySend.sln file, click to select this file and click **Open** to open the solution that contains the sample project.</span></span>  
  
3.  <span data-ttu-id="21da8-181">按一下**檢視**功能表，然後選取**方案總管 中**以顯示 方案總管。</span><span class="sxs-lookup"><span data-stu-id="21da8-181">Click the **View** menu and select **Solution Explorer** to display the Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="21da8-182">按兩下 [方案總管] 中的 LOCATIONService_1.xsd 檔案加以開啟。</span><span class="sxs-lookup"><span data-stu-id="21da8-182">Double-click the LOCATIONService_1.xsd file in the Solution Explorer to open it.</span></span>  
  
5.  <span data-ttu-id="21da8-183">以滑鼠右鍵按一下**結構描述**的 LOCATIONService_1.xsd，然後選取節點**屬性**功能表選項以顯示結構描述的屬性。</span><span class="sxs-lookup"><span data-stu-id="21da8-183">Right-click the **Schema** node of LOCATIONService_1.xsd and select the **Properties** menu option to display the properties for the schema.</span></span>  
  
6.  <span data-ttu-id="21da8-184">編輯**目標命名空間**屬性，以使用適當的值做為配接器名稱，例如**目標命名空間**屬性應該讀取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="21da8-184">Edit the **Target Namespace** property to use the appropriate values for the adapter name, for example the **Target Namespace** property should read as follows:</span></span>  
  
    ```  
    http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
    ```  
  
     <span data-ttu-id="21da8-185">其中*PeopleSoft*是 PeopleSoft 配接器的名稱，如 BizTalk 管理主控台中所示。</span><span class="sxs-lookup"><span data-stu-id="21da8-185">Where *PeopleSoft* is the name of the PeopleSoft adapter as viewed in the BizTalk Administration Console.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="21da8-186">如果設定的值為**目標命名空間**不符合輸入文件執行個體處理時，會發生路由失敗，然後輸入文件執行個體中指定的命名空間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="21da8-186">If the configured value for **Target Namespace** does not match the namespace specified in the input document instance then a routing failure will occur when the input document instance is processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a><span data-ttu-id="21da8-187">從配接器結構描述產生文件執行個體</span><span class="sxs-lookup"><span data-stu-id="21da8-187">Generate a document instance from the Adapter schema</span></span>  
  
1.  <span data-ttu-id="21da8-188">按兩下**LOCATIONService_1.xsd**結構描述編輯器中開啟該檔案 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="21da8-188">Double-click **LOCATIONService_1.xsd** in the Solution Explorer to open the file in the Schema Editor.</span></span>  
  
2.  <span data-ttu-id="21da8-189">以滑鼠右鍵按一下**\<結構描述 >**節點在結構描述編輯器 中，按一下**屬性**顯示節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="21da8-189">Right-click the **\<Schema>** node in the Schema Editor, and click **Properties** to display the properties for the node.</span></span>  
  
3.  <span data-ttu-id="21da8-190">選取**CreateEx**從清單中的可用節點**根參考**下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-190">Select **CreateEx** from the list of available nodes in the **Root Reference** dropdown box.</span></span> <span data-ttu-id="21da8-191">這應完成，以便在產生範例文件執行個體時將會產生從**CreateEx**結構描述節點。</span><span class="sxs-lookup"><span data-stu-id="21da8-191">This should be done so that when you generate a sample document instance it will be generated from the **CreateEx** node of the schema.</span></span>  
  
4.  <span data-ttu-id="21da8-192">以滑鼠右鍵按一下 [方案總管] 中的 LOCATIONService_1.xsd，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="21da8-192">Right-click LOCATIONService_1.xsd in Solution Explorer and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="21da8-193">在 [屬性] 視窗中，按一下以選取**輸出執行個體檔案名稱**選項在**一般**> 一節。</span><span class="sxs-lookup"><span data-stu-id="21da8-193">In the Properties window, click to select the **Output Instance Filename** option under the **General** section.</span></span>  
  
6.  <span data-ttu-id="21da8-194">按一下省略符號按鈕 （…） 以顯示**選取輸出檔案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-194">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
7.  <span data-ttu-id="21da8-195">指定的資料夾和輸出檔案執行個體名稱，例如**C:\instance.xml**按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="21da8-195">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="21da8-196">請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="21da8-196">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
8.  <span data-ttu-id="21da8-197">以滑鼠右鍵按一下 [方案總管] 中的 LOCATIONService_1.xsd，然後按一下**產生執行個體**產生文件執行個體中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="21da8-197">Right-click LOCATIONService_1.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
9. <span data-ttu-id="21da8-198">以滑鼠右鍵按一下**\<結構描述 >**節點在結構描述編輯器 中，按一下**屬性**顯示節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="21da8-198">Right-click the **\<Schema>** node in the Schema Editor, and click **Properties** to display the properties for the node.</span></span>  
  
10. <span data-ttu-id="21da8-199">選取 (**預設)**從清單中的可用節點**根參考**下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-199">Select (**Default)** from the list of available nodes in the **Root Reference** dropdown box.</span></span>  
  
#### <a name="modify-the-generated-document-instance"></a><span data-ttu-id="21da8-200">修改產生的文件執行個體</span><span class="sxs-lookup"><span data-stu-id="21da8-200">Modify the generated document instance</span></span>  
  
1.  <span data-ttu-id="21da8-201">在文字編輯器 (如 [記事本]) 中開啟產生的文件執行個體，然後編輯文件執行個體的內容，以確保這些欄位中的資料會在 PeopleSoft 系統中產生唯一的記錄，例如，底下的 XML 檔案描述記錄中定義位置的欄位：</span><span class="sxs-lookup"><span data-stu-id="21da8-201">Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data in these fields will generate a unique record in the PeopleSoft system, for example the XML file below describes the fields in a record that define a location:</span></span>  
  
    ```  
    <ns0:CreateEx xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
      <ns0:SETID>SHARE</ns0:SETID>  
      <ns0:LOCATION>9991</ns0:LOCATION>  
      <ns0:interactiveMode>true</ns0:interactiveMode>  
       <ns0:properties>  
        <ns0:LOCATION_TBL_sequence>  
          <ns0:LOCATION_TBL>  
            <ns0:COUNTRY>USA</ns0:COUNTRY>  
            <ns0:DESCR>Adapter Test</ns0:DESCR>  
            <ns0:EFFDT>2006-05-31</ns0:EFFDT>  
            <ns0:EFF_STATUS>A</ns0:EFF_STATUS>  
            <ns0:SETID>SHARE</ns0:SETID>  
          </ns0:LOCATION_TBL>  
        </ns0:LOCATION_TBL_sequence>  
      </ns0:properties>  
    </ns0:CreateEx>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="21da8-202">在上述範例*PeopleSoft*是配接器的實際名稱的預留位置，如 BizTalk 管理主控台中所示。</span><span class="sxs-lookup"><span data-stu-id="21da8-202">In the example above, *PeopleSoft* is a placeholder for the actual name of the adapter as viewed in the BizTalk Administration Console.</span></span>  
  
2.  <span data-ttu-id="21da8-203">儲存已修改的文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="21da8-203">Save the modified document instance.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="21da8-204">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="21da8-204">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="21da8-205">以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**屬性**為啟動專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="21da8-205">Right-click the OneWaySend project in Solution Explorer and click **Properties** to launch the Project Designer.</span></span>  
  
2.  <span data-ttu-id="21da8-206">按一下**部署** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="21da8-206">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="21da8-207">輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="21da8-207">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="21da8-208">以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="21da8-208">Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="21da8-209">繫結和登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="21da8-209">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="21da8-210">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="21da8-210">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="21da8-211">按一下**重新整理**中 MMC 工具列或按下按鈕**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。</span><span class="sxs-lookup"><span data-stu-id="21da8-211">Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console view.</span></span>  
  
3.  <span data-ttu-id="21da8-212">按兩下協調流程以顯示**協調流程屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21da8-212">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="21da8-213">按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="21da8-213">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="21da8-214">指定適當的繫結選項值，例如：</span><span class="sxs-lookup"><span data-stu-id="21da8-214">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="21da8-215">**參數**</span><span class="sxs-lookup"><span data-stu-id="21da8-215">**Parameter**</span></span>|<span data-ttu-id="21da8-216">**值**</span><span class="sxs-lookup"><span data-stu-id="21da8-216">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="21da8-217">Host</span><span class="sxs-lookup"><span data-stu-id="21da8-217">Host</span></span>|<span data-ttu-id="21da8-218">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="21da8-218">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="21da8-219">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="21da8-219">FileReceivePort</span></span>|<span data-ttu-id="21da8-220">PeopleSoftOneWayFileRP</span><span class="sxs-lookup"><span data-stu-id="21da8-220">PeopleSoftOneWayFileRP</span></span>|  
    |<span data-ttu-id="21da8-221">PeopleSoftOneWaySendPort</span><span class="sxs-lookup"><span data-stu-id="21da8-221">PeopleSoftOneWaySendPort</span></span>|<span data-ttu-id="21da8-222">PeopleSoftOneWaySP</span><span class="sxs-lookup"><span data-stu-id="21da8-222">PeopleSoftOneWaySP</span></span>|  
  
6.  <span data-ttu-id="21da8-223">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="21da8-223">Click OK.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="21da8-224">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="21da8-224">Start the orchestration</span></span>  
  
-   <span data-ttu-id="21da8-225">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="21da8-225">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a><span data-ttu-id="21da8-226">將文件執行個體拖放到檔案接收位置所監視的資料夾</span><span class="sxs-lookup"><span data-stu-id="21da8-226">Drop a document instance into the folder monitored by the file receive location</span></span>  
  
-   <span data-ttu-id="21da8-227">將稍早建立的文件執行個體複製到檔案接收位置依設定要監視的資料夾。</span><span class="sxs-lookup"><span data-stu-id="21da8-227">Copy the document instance that was created earlier to the folder that the file receive location is configured to monitor.</span></span>  
  
#### <a name="verify-that-the-peoplesoft-system-is-updated"></a><span data-ttu-id="21da8-228">確認 PeopleSoft 系統更新</span><span class="sxs-lookup"><span data-stu-id="21da8-228">Verify that the PeopleSoft system is updated</span></span>  
  
-   <span data-ttu-id="21da8-229">若要確認記錄已經建立的 XML 檔案中的資料使用 PeopleSoft web 介面。</span><span class="sxs-lookup"><span data-stu-id="21da8-229">Use the PeopleSoft web interface to verify that the record was created from the data in the XML file.</span></span>  
  
 <span data-ttu-id="21da8-230">如果文件執行個體處理成功，則會發生以下一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="21da8-230">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="21da8-231">檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="21da8-231">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="21da8-232">協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程執行個體，然後將訊息傳送至這個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="21da8-232">The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="21da8-233">協調流程執行個體使用指定的協調流程中的邏輯處理訊息，並將訊息發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="21da8-233">The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="21da8-234">PeopleSoft 傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎將訊息傳送至 PeopleSoft 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="21da8-234">The PeopleSoft send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the PeopleSoft send port.</span></span>  
  
5.  <span data-ttu-id="21da8-235">傳送埠將訊息交給 BizTalk Adapter for PeopleSoft Enterprise。</span><span class="sxs-lookup"><span data-stu-id="21da8-235">The send port hands the message to the BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
6.  <span data-ttu-id="21da8-236">BizTalk Adapter for PeopleSoft Enterprise 會叫用 CreateEx 方法，以建立使用 XML 檔案中的資料記錄。</span><span class="sxs-lookup"><span data-stu-id="21da8-236">The BizTalk Adapter for PeopleSoft Enterprise invokes the CreateEx method to create a record using the data in the XML file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21da8-237">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21da8-237">See Also</span></span>  
 [<span data-ttu-id="21da8-238">教學課程： 使用 BizTalk Adapter for PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="21da8-238">Tutorials: Using BizTalk Adapter for PeopleSoft Enterprise</span></span>](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)