---
title: "教學課程： 使用 BizTalk Adapter for PeopleSoft Enterprise 從 PeopleSoft Enterprise 中擷取資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c173fa4c-911e-4fa3-813f-e8f36b0049a5
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 823bd5739ac58d8b63f79ee15102cf44f3d82c7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-peoplesoft-enterprise-to-retrieve-data-from-peoplesoft-enterprise"></a><span data-ttu-id="f42fa-102">教學課程：使用 BizTalk Adapter for PeopleSoft Enterprise 從 PeopleSoft Enterprise 中擷取資料</span><span class="sxs-lookup"><span data-stu-id="f42fa-102">Tutorial: Using the BizTalk Adapter for PeopleSoft Enterprise to Retrieve Data from PeopleSoft Enterprise</span></span>
<span data-ttu-id="f42fa-103">BizTalk Adapter for PeopleSoft Enterprise 可用來對 PeopleSoft 系統執行查詢，並傳回查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="f42fa-103">The BizTalk Adapter for PeopleSoft Enterprise can be used to execute a query against a PeopleSoft system and return the results of the query.</span></span> <span data-ttu-id="f42fa-104">這個逐步解說將說明此功能的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="f42fa-104">This walkthrough describes an SDK sample that illustrates this functionality.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f42fa-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="f42fa-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="f42fa-106">執行 BizTalk Adapter for PeopleSoft Enterprise Geis 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上必須已安裝 Java 2 平台。</span><span class="sxs-lookup"><span data-stu-id="f42fa-106">The Java 2 Platform must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise Geis running on.</span></span>  
  
-   <span data-ttu-id="f42fa-107">PeopleSoft Java Object Adapter JAR 檔案， **psjoa.jar**應複製到可存取的資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk Adapter for PeopleSoft Enterprise 上執行。</span><span class="sxs-lookup"><span data-stu-id="f42fa-107">The PeopleSoft Java Object Adapter JAR file, **psjoa.jar** should be copied to a folder that is accessible to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on.</span></span>  
  
-   <span data-ttu-id="f42fa-108">執行 BizTalk Adapter for PeopleSoft Enterprise 的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上必須已安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。</span><span class="sxs-lookup"><span data-stu-id="f42fa-108">[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] must be installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the BizTalk Adapter for PeopleSoft Enterprise is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="f42fa-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="f42fa-109">What This Sample Does</span></span>  
 <span data-ttu-id="f42fa-110">此範例會從某個資料夾收取某個 XML 檔案、將該檔案傳送至協調流程，然後使用 BizTalk Adapter for PeopleSoft Enterprise 對 PeopleSoft 系統執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f42fa-110">This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for PeopleSoft Enterprise to execute a query against a PeopleSoft system.</span></span> <span data-ttu-id="f42fa-111">查詢的結果會寫入至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f42fa-111">The result of the query is written to an XML file.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="f42fa-112">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="f42fa-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="f42fa-113">以 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計的這個範例，其建立的目的在示範將 BizTalk Adapter for PeopleSoft Enterprise 與 BizTalk 協調流程搭配使用的基本功能。</span><span class="sxs-lookup"><span data-stu-id="f42fa-113">This sample was designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and was created to illustrate basic functionality using the BizTalk Adapter for PeopleSoft Enterprise with a BizTalk orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="f42fa-114">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="f42fa-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="f42fa-115">這個範例位於下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="f42fa-115">The sample is located in the following folder:</span></span>  
  
 <span data-ttu-id="f42fa-116">\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftTwoWaySend</span><span class="sxs-lookup"><span data-stu-id="f42fa-116">\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\PeopleSoft Enterprise(r)\Sdk\PeopleSoftTwoWaySend</span></span>  
  
 <span data-ttu-id="f42fa-117">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="f42fa-117">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="f42fa-118">**執行階段專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="f42fa-118">**Runtime Project Filename**</span></span>|<span data-ttu-id="f42fa-119">**執行階段專案檔案描述**</span><span class="sxs-lookup"><span data-stu-id="f42fa-119">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="f42fa-120">TwoWaySend.btproj、</span><span class="sxs-lookup"><span data-stu-id="f42fa-120">TwoWaySend.btproj,</span></span><br /><br /> <span data-ttu-id="f42fa-121">TwoWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="f42fa-121">TwoWaySend.sln</span></span>|<span data-ttu-id="f42fa-122">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="f42fa-122">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="f42fa-123">LOCATIONService.xsd、</span><span class="sxs-lookup"><span data-stu-id="f42fa-123">LOCATIONService.xsd,</span></span><br /><br /> <span data-ttu-id="f42fa-124">LOCATIONService_1.xsd、</span><span class="sxs-lookup"><span data-stu-id="f42fa-124">LOCATIONService_1.xsd,</span></span><br /><br /> <span data-ttu-id="f42fa-125">LOCATIONService_2.xsd</span><span class="sxs-lookup"><span data-stu-id="f42fa-125">LOCATIONService_2.xsd</span></span>|<span data-ttu-id="f42fa-126">這個應用程式的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="f42fa-126">Schema files for the application.</span></span> <span data-ttu-id="f42fa-127">**注意：**使用原先建立在專案中的配接器結構描述檔案**新增配接器中繼資料精靈**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-127">**Note:**  The adapter schema files in the project were originally created using the **Add Adapter Metadata Wizard**.</span></span> <span data-ttu-id="f42fa-128">如需 [新增配接器中繼資料精靈] 的詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的「如何將配接器中繼資料新增至 BizTalk 專案」主題。</span><span class="sxs-lookup"><span data-stu-id="f42fa-128">For more information on the Add Adapter Metadata Wizard see the topic "How to Add Adapter Metadata to a BizTalk Project" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>|  
|<span data-ttu-id="f42fa-129">PeopleSoftTwoWaySend.odx</span><span class="sxs-lookup"><span data-stu-id="f42fa-129">PeopleSoftTwoWaySend.odx</span></span>|<span data-ttu-id="f42fa-130">這個應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="f42fa-130">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="f42fa-131">PeopleSoftTwoWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="f42fa-131">PeopleSoftTwoWaySend.snk</span></span>|<span data-ttu-id="f42fa-132">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="f42fa-132">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="f42fa-133">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="f42fa-133">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-peoplesoft-enterprise-adapter"></a><span data-ttu-id="f42fa-134">建立 PeopleSoft Enterprise 配接器的新執行個體</span><span class="sxs-lookup"><span data-stu-id="f42fa-134">Create a new instance of the PeopleSoft Enterprise adapter</span></span>  
  
1.  <span data-ttu-id="f42fa-135">啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f42fa-135">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="f42fa-136">按一下**啟動**，**程式**， **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]， **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-136">Click **Start**, **Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f42fa-137">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-137">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="f42fa-138">以滑鼠右鍵按一下**配接器**指向**新增**，**配接器**顯示**配接器屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-138">Right-click **Adapters** and point to **New**, **Adapter** to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="f42fa-139">輸入一個值**名稱**欄位，例如**PeopleSoft**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-139">Enter a value for the **Name** field, for example **PeopleSoft**.</span></span>  
  
5.  <span data-ttu-id="f42fa-140">選取**PeopleSoft enterprise （)**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-140">Select **PeopleSoft Enterprise(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-solicit-response-biztalk-send-port"></a><span data-ttu-id="f42fa-141">建立請求-回應 BizTalk 傳送埠</span><span class="sxs-lookup"><span data-stu-id="f42fa-141">Create a Solicit-Response BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="f42fa-142">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-142">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="f42fa-143">以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態請求-回應傳送埠**顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-143">Right-click **Send Ports** and point to **New**, **Static Solicit-Response Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="f42fa-144">輸入一個值**名稱**欄位，例如**PeopleSoftTwoWaySP**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-144">Enter a value for the **Name** field, for example **PeopleSoftTwoWaySP**.</span></span>  
  
4.  <span data-ttu-id="f42fa-145">從使用中的配接器清單中選取 PeopleSoft 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-145">Select the PeopleSoft adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f42fa-146">這個值是在管理主控台中建立 PeopleSoft Enterprise 配接器時指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="f42fa-146">This value is the name that was specified when the PeopleSoft Enterprise adapter was created in the Administration Console.</span></span>  
  
5.  <span data-ttu-id="f42fa-147">輸入下列值**配接器必要屬性**:</span><span class="sxs-lookup"><span data-stu-id="f42fa-147">Enter the following values for the **Adapter Required Properties**:</span></span>  
  
    |<span data-ttu-id="f42fa-148">**屬性**</span><span class="sxs-lookup"><span data-stu-id="f42fa-148">**Property**</span></span>|<span data-ttu-id="f42fa-149">**值**</span><span class="sxs-lookup"><span data-stu-id="f42fa-149">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="f42fa-150">應用程式伺服器路徑</span><span class="sxs-lookup"><span data-stu-id="f42fa-150">Application server path</span></span>|<span data-ttu-id="f42fa-151">PeopleSoft 伺服器的機器與連接埠位置，例如 //PSServer:8888。</span><span class="sxs-lookup"><span data-stu-id="f42fa-151">PeopleSoft Server's machine and port location, for example //PSServer:8888.</span></span> <span data-ttu-id="f42fa-152">**注意：**如果未指定連接埠號碼，會使用預設連接埠 9000，因此在您上面的範例可以輸入 //PSServer 值如果 PeopleSoft 伺服器使用預設的連接埠值 9000。</span><span class="sxs-lookup"><span data-stu-id="f42fa-152">**Note:**  If you do not specify a port number, the default port of 9000 is used so in the example above you could enter a value of //PSServer if the PeopleSoft Server uses the default port value of 9000.</span></span>|  
    |<span data-ttu-id="f42fa-153">JAVA_HOME</span><span class="sxs-lookup"><span data-stu-id="f42fa-153">JAVA_HOME</span></span>|<span data-ttu-id="f42fa-154">與 Java 2 平台 SDK 檔案相關聯之主目錄的路徑，例如 C:\j2sdk1.4.2_08</span><span class="sxs-lookup"><span data-stu-id="f42fa-154">Path to the home directory associated with the Java 2 Platform SDK files, for example C:\j2sdk1.4.2_08</span></span>|  
    |<span data-ttu-id="f42fa-155">密碼</span><span class="sxs-lookup"><span data-stu-id="f42fa-155">Password</span></span>|<span data-ttu-id="f42fa-156">連接至 PeopleSoft 系統時使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="f42fa-156">Password used when connecting to the PeopleSoft system.</span></span>|  
    |<span data-ttu-id="f42fa-157">PeopleSoft 8.x JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="f42fa-157">PeopleSoft 8.x JAR files</span></span>|<span data-ttu-id="f42fa-158">PeopleSoft Java Object Adapter JAR 檔案位置， **psjoa.jar**，例如 C:\JARS\psjoa.jar。</span><span class="sxs-lookup"><span data-stu-id="f42fa-158">Location of the PeopleSoft Java Object Adapter JAR file, **psjoa.jar**, for example C:\JARS\psjoa.jar.</span></span>|  
    |<span data-ttu-id="f42fa-159">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="f42fa-159">User name</span></span>|<span data-ttu-id="f42fa-160">用於連接至 PeopleSoft 系統的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f42fa-160">Username for connecting to the PeopleSoft system.</span></span>|  
  
6.  <span data-ttu-id="f42fa-161">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-161">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="f42fa-162">選取**XMLTransmit**管線就會從管線中可用的清單**傳送管線**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f42fa-162">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown.</span></span>  
  
8.  <span data-ttu-id="f42fa-163">選取**XMLReceive**管線就會從管線中可用的清單**接收管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-163">Select the **XMLReceive** pipeline from the list of pipelines available in the **Receive pipeline** dropdown and click **OK**.</span></span>  
  
9. <span data-ttu-id="f42fa-164">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f42fa-164">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-one-way-biztalk-send-port"></a><span data-ttu-id="f42fa-165">建立單向 BizTalk 傳送埠</span><span class="sxs-lookup"><span data-stu-id="f42fa-165">Create a One-Way BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="f42fa-166">建立傳送埠所要使用的目標資料夾，例如 C:\Files\Out。</span><span class="sxs-lookup"><span data-stu-id="f42fa-166">Create a target folder to be used by the send port, for example C:\Files\Out.</span></span>  
  
2.  <span data-ttu-id="f42fa-167">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-167">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="f42fa-168">以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠**顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-168">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="f42fa-169">輸入一個值**名稱**欄位，例如**PeopleSoftTwoWayFileSP**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-169">Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileSP**.</span></span>  
  
5.  <span data-ttu-id="f42fa-170">選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-170">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
6.  <span data-ttu-id="f42fa-171">輸入您稍早建立的資料夾位置**目的地資料夾**屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-171">Enter the location of the folder that you created earlier for the **Destination Folder** property and click **OK**.</span></span>  
  
7.  <span data-ttu-id="f42fa-172">選取**XMLTransmit**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-172">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="f42fa-173">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f42fa-173">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-file-receive-port"></a><span data-ttu-id="f42fa-174">建立檔案接收埠</span><span class="sxs-lookup"><span data-stu-id="f42fa-174">Create a file receive port</span></span>  
  
1.  <span data-ttu-id="f42fa-175">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-175">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="f42fa-176">以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠**以顯示 [接收埠屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-176">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="f42fa-177">輸入一個值**名稱**欄位，例如**PeopleSoftTwoWayFileRP**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-177">Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-file-receive-location"></a><span data-ttu-id="f42fa-178">建立檔案接收位置</span><span class="sxs-lookup"><span data-stu-id="f42fa-178">Create a file receive location</span></span>  
  
1.  <span data-ttu-id="f42fa-179">建立要由檔案接收位置監視的資料夾，例如 C:\Files\In。</span><span class="sxs-lookup"><span data-stu-id="f42fa-179">Create a folder to be monitored by the file receive location, for example C:\Files\In.</span></span>  
  
2.  <span data-ttu-id="f42fa-180">以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置**顯示**接收位置屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-180">Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="f42fa-181">輸入一個值**名稱**欄位，例如**PeopleSoftTwoWayFileRL**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-181">Enter a value for the **Name** field, for example **PeopleSoftTwoWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="f42fa-182">選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-182">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="f42fa-183">輸入您稍早建立的資料夾位置**接收資料夾**屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-183">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="f42fa-184">選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-184">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="f42fa-185">以滑鼠右鍵按一下接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-185">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="modify-the-adapter-schema-target-namespace-property"></a><span data-ttu-id="f42fa-186">修改配接器結構描述目標命名空間屬性</span><span class="sxs-lookup"><span data-stu-id="f42fa-186">Modify the Adapter schema target namespace property</span></span>  
  
1.  <span data-ttu-id="f42fa-187">啟動 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 並開啟 TwoWaySend.sln。</span><span class="sxs-lookup"><span data-stu-id="f42fa-187">Launch [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and open TwoWaySend.sln.</span></span> <span data-ttu-id="f42fa-188">按一下**檔案**，**開啟**，**專案/方案**顯示**開啟專案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-188">Click **File**, **Open**, **Project/Solution** to display the **Open Project** dialog.</span></span>  
  
2.  <span data-ttu-id="f42fa-189">瀏覽到 TwoWaySend.sln 檔案，請按一下以選取此檔案，然後按一下**開啟**來開啟包含範例專案的方案。</span><span class="sxs-lookup"><span data-stu-id="f42fa-189">Browse to the TwoWaySend.sln file, click to select this file and click **Open** to open the solution that contains the sample project.</span></span>  
  
3.  <span data-ttu-id="f42fa-190">按一下**檢視**功能表，然後選取**方案總管 中**以顯示 方案總管。</span><span class="sxs-lookup"><span data-stu-id="f42fa-190">Click the **View** menu and select **Solution Explorer** to display the Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="f42fa-191">按兩下 [方案總管] 中的 LOCATIONService_1.xsd 檔案加以開啟。</span><span class="sxs-lookup"><span data-stu-id="f42fa-191">Double-click the LOCATIONService_1.xsd file in the Solution Explorer to open it.</span></span>  
  
5.  <span data-ttu-id="f42fa-192">以滑鼠右鍵按一下**結構描述**的 LOCATIONService_1.xsd，然後選取節點**屬性**功能表選項以顯示結構描述的屬性。</span><span class="sxs-lookup"><span data-stu-id="f42fa-192">Right-click the **Schema** node of LOCATIONService_1.xsd and select the **Properties** menu option to display the properties for the schema.</span></span>  
  
6.  <span data-ttu-id="f42fa-193">編輯**目標命名空間**屬性，以使用適當的值做為配接器名稱，例如**目標命名空間**屬性應該讀取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f42fa-193">Edit the **Target Namespace** property to use the appropriate values for the adapter name, for example the **Target Namespace** property should read as follows:</span></span>  
  
    ```  
    http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]  
    ```  
  
     <span data-ttu-id="f42fa-194">其中*PeopleSoft*是 PeopleSoft 配接器的名稱，如中所示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f42fa-194">Where *PeopleSoft* is the name of the PeopleSoft adapter as viewed in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f42fa-195">如果設定的值為**目標命名空間**不符合輸入文件執行個體處理時，會發生路由失敗，然後輸入文件執行個體中指定的命名空間[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f42fa-195">If the configured value for **Target Namespace** does not match the namespace specified in the input document instance then a routing failure will occur when the input document instance is processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a><span data-ttu-id="f42fa-196">從配接器結構描述產生文件執行個體</span><span class="sxs-lookup"><span data-stu-id="f42fa-196">Generate a document instance from the Adapter schema</span></span>  
  
1.  <span data-ttu-id="f42fa-197">按兩下**LOCATIONService_1.xsd**方案總管 中結構描述編輯器中開啟該檔案中。</span><span class="sxs-lookup"><span data-stu-id="f42fa-197">Double-click **LOCATIONService_1.xsd** in Solution Explorer to open the file in Schema Editor.</span></span>  
  
2.  <span data-ttu-id="f42fa-198">以滑鼠右鍵按一下**\<結構描述 >**節點在結構描述編輯器，然後按一下**屬性**顯示節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="f42fa-198">Right-click the **\<Schema>** node in Schema Editor and click **Properties** to display properties for the node.</span></span>  
  
3.  <span data-ttu-id="f42fa-199">選取**取得**從清單中的可用節點**根參考**下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-199">Select **Get** from the list of available nodes in the **Root Reference** dropdown box.</span></span> <span data-ttu-id="f42fa-200">這應完成，以便在產生範例文件執行個體時將會產生從**取得**結構描述節點。</span><span class="sxs-lookup"><span data-stu-id="f42fa-200">This should be done so that when you generate a sample document instance it will be generated from the **Get** node of the schema.</span></span>  
  
4.  <span data-ttu-id="f42fa-201">以滑鼠右鍵按一下**LOCATIONService_1.xsd**在方案總管 中按一下**屬性**屬性 視窗中顯示內容。</span><span class="sxs-lookup"><span data-stu-id="f42fa-201">Right-click **LOCATIONService_1.xsd** in Solution Explorer and click **Properties** to display properties in the Properties window.</span></span>  
  
5.  <span data-ttu-id="f42fa-202">在 [屬性] 視窗中，按一下以選取**輸出執行個體檔案名稱**選項。</span><span class="sxs-lookup"><span data-stu-id="f42fa-202">In the Properties window, click to select the **Output Instance Filename** option.</span></span>  
  
6.  <span data-ttu-id="f42fa-203">按一下省略符號按鈕 （…） 以顯示**選取輸出檔案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-203">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
7.  <span data-ttu-id="f42fa-204">指定的資料夾和輸出檔案執行個體名稱，例如**C:\instance.xml**按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-204">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f42fa-205">請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="f42fa-205">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
8.  <span data-ttu-id="f42fa-206">以滑鼠右鍵按一下 [方案總管] 中的 LOCATIONService_1.xsd，然後按一下**產生執行個體**產生文件執行個體中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="f42fa-206">Right-click LOCATIONService_1.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
9. <span data-ttu-id="f42fa-207">以滑鼠右鍵按一下**\<結構描述 >**節點在結構描述編輯器，然後按一下**屬性**顯示節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="f42fa-207">Right-click the **\<Schema>** node in Schema Editor and click **Properties** to display the properties for the node.</span></span>  
  
10. <span data-ttu-id="f42fa-208">選取 (**預設)**從清單中的可用節點**根參考**下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-208">Select (**Default)** from the list of available nodes in the **Root Reference** dropdown box.</span></span>  
  
#### <a name="modify-the-generated-document-instance"></a><span data-ttu-id="f42fa-209">修改產生的文件執行個體</span><span class="sxs-lookup"><span data-stu-id="f42fa-209">Modify the generated document instance</span></span>  
  
1.  <span data-ttu-id="f42fa-210">在文字編輯器 (如 [記事本]) 中開啟產生的文件執行個體，然後編輯文件執行個體的內容，以確保這些欄位中的資料會傳回現有的記錄：</span><span class="sxs-lookup"><span data-stu-id="f42fa-210">Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data in these fields will return an existing record:</span></span>  
  
    ```  
    <ns0:Get xmlns:ns0="http://schemas.microsoft.com/[PeopleSoft://CI/LOCATION]">  
    <ns0:SETID>SHARE</ns0:SETID>  
    <ns0:LOCATION>WFKLOC</ns0:LOCATION>  
    <ns0:getHistory>true</ns0:getHistory>  
    </ns0:Get>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f42fa-211">在上述範例*PeopleSoft*是配接器的實際名稱的預留位置，如 BizTalk 管理主控台中所示。</span><span class="sxs-lookup"><span data-stu-id="f42fa-211">In the example above, *PeopleSoft* is a placeholder for the actual name of the adapter as viewed in the BizTalk Administration Console.</span></span> <span data-ttu-id="f42fa-212">*共用*和*WFKLOC*都是用來識別特定資料錄 PeopleSoft 系統中的值的預留位置。</span><span class="sxs-lookup"><span data-stu-id="f42fa-212">*SHARE* and *WFKLOC* are placeholders for values used to identify a particular record in the PeopleSoft system.</span></span>  
  
2.  <span data-ttu-id="f42fa-213">儲存已修改的文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="f42fa-213">Save the modified document instance.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="f42fa-214">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="f42fa-214">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="f42fa-215">以滑鼠右鍵按一下方案總管 中的 TwoWaySend 專案，然後按一下**屬性**顯示專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="f42fa-215">Right-click the TwoWaySend project in Solution Explorer and click **Properties** to display the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="f42fa-216">按一下**部署**專案設計工具中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f42fa-216">Click the **Deployment** tab in the Project Designer.</span></span>  
  
3.  <span data-ttu-id="f42fa-217">輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-217">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="f42fa-218">以滑鼠右鍵按一下方案總管 中的 TwoWaySend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="f42fa-218">Right-click the TwoWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="f42fa-219">繫結和登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="f42fa-219">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="f42fa-220">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="f42fa-220">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="f42fa-221">按一下**重新整理**按鈕[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台工具列或按**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。</span><span class="sxs-lookup"><span data-stu-id="f42fa-221">Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console view.</span></span>  
  
3.  <span data-ttu-id="f42fa-222">按兩下協調流程以顯示**協調流程屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f42fa-222">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="f42fa-223">按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="f42fa-223">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="f42fa-224">指定適當的繫結選項值，例如：</span><span class="sxs-lookup"><span data-stu-id="f42fa-224">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="f42fa-225">**參數**</span><span class="sxs-lookup"><span data-stu-id="f42fa-225">**Parameter**</span></span>|<span data-ttu-id="f42fa-226">**值**</span><span class="sxs-lookup"><span data-stu-id="f42fa-226">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="f42fa-227">Host</span><span class="sxs-lookup"><span data-stu-id="f42fa-227">Host</span></span>|<span data-ttu-id="f42fa-228">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="f42fa-228">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="f42fa-229">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="f42fa-229">FileReceivePort</span></span>|<span data-ttu-id="f42fa-230">PeopleSoftTwoWayFileRP</span><span class="sxs-lookup"><span data-stu-id="f42fa-230">PeopleSoftTwoWayFileRP</span></span>|  
    |<span data-ttu-id="f42fa-231">PeopleSoftTwoWaySend678</span><span class="sxs-lookup"><span data-stu-id="f42fa-231">PeopleSoftTwoWaySend678</span></span>|<span data-ttu-id="f42fa-232">PeopleSoftTwoWaySP</span><span class="sxs-lookup"><span data-stu-id="f42fa-232">PeopleSoftTwoWaySP</span></span>|  
    |<span data-ttu-id="f42fa-233">ResponsePort</span><span class="sxs-lookup"><span data-stu-id="f42fa-233">ResponsePort</span></span>|<span data-ttu-id="f42fa-234">PeopleSoftTwoWayFileSP</span><span class="sxs-lookup"><span data-stu-id="f42fa-234">PeopleSoftTwoWayFileSP</span></span>|  
  
6.  <span data-ttu-id="f42fa-235">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="f42fa-235">Click OK.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="f42fa-236">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="f42fa-236">Start the orchestration</span></span>  
  
-   <span data-ttu-id="f42fa-237">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="f42fa-237">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a><span data-ttu-id="f42fa-238">將文件執行個體拖放到檔案接收位置所監視的資料夾</span><span class="sxs-lookup"><span data-stu-id="f42fa-238">Drop a document instance into the folder monitored by the file receive location</span></span>  
  
-   <span data-ttu-id="f42fa-239">將稍早建立的文件執行個體複製到檔案接收位置依設定要監視的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f42fa-239">Copy the document instance that was created earlier to the folder that the file receive location is configured to monitor.</span></span>  
  
#### <a name="verify-that-the-document-instance-was-processed-by-the-biztalk-adapter-for-peoplesoft-enterprise"></a><span data-ttu-id="f42fa-240">確認文件執行個體已由 BizTalk Adapter for PeopleSoft Enterprise 進行處理</span><span class="sxs-lookup"><span data-stu-id="f42fa-240">Verify that the document instance was processed by the BizTalk Adapter for PeopleSoft Enterprise</span></span>  
  
-   <span data-ttu-id="f42fa-241">開啟檔案傳送埠進行傳送時依設定要使用的目標資料夾，然後確認已產生輸出文件。</span><span class="sxs-lookup"><span data-stu-id="f42fa-241">Open the folder that the file send port is configured to send to and verify that an output document was generated.</span></span> <span data-ttu-id="f42fa-242">此檔案應包含 BizTalk Adapter for PeopleSoft Enterprise 處理查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="f42fa-242">This file should contain the results of the query that was processed by the BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
 <span data-ttu-id="f42fa-243">如果文件執行個體處理成功，則會發生以下一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="f42fa-243">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="f42fa-244">檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="f42fa-244">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="f42fa-245">協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程的執行個體，然後將訊息傳送至這個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="f42fa-245">The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="f42fa-246">協調流程執行個體將訊息發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="f42fa-246">The orchestration instance publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="f42fa-247">請求-回應傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會將訊息傳送至 PeopleSoft 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f42fa-247">The solicit-response send port subscribes to this published message so the BizTalk Messaging Engine sends the message to the PeopleSoft send port.</span></span>  
  
5.  <span data-ttu-id="f42fa-248">傳送埠將訊息交給 BizTalk Adapter for PeopleSoft Enterprise。</span><span class="sxs-lookup"><span data-stu-id="f42fa-248">The send port hands the message to the BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
6.  <span data-ttu-id="f42fa-249">BizTalk Adapter for PeopleSoft Enterprise 使用輸入檔中定義的參數，對 PeopleSoft 系統執行 Get 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f42fa-249">The BizTalk Adapter for PeopleSoft Enterprise executes a Get statement against the PeopleSoft system using the parameters defined in the input file.</span></span>  
  
7.  <span data-ttu-id="f42fa-250">BizTalk Adapter for PeopleSoft Enterprise 傳回 Get 陳述式的結果，做為協調流程中「請求-回應」連接埠的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="f42fa-250">The BizTalk Adapter for PeopleSoft Enterprise returns the results of the Get statement as the response message for the solicit-response port in the orchestration.</span></span>  
  
8.  <span data-ttu-id="f42fa-251">協調流程將結果集發佈至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="f42fa-251">The orchestration publishes the result set to the MessageBox.</span></span>  
  
9. <span data-ttu-id="f42fa-252">檔案傳送埠訂閱這個訊息，因此 BizTalk 會將訊息傳送至檔案配接器。</span><span class="sxs-lookup"><span data-stu-id="f42fa-252">The File send port subscribes to this message so BizTalk sends the message to the File adapter.</span></span>  
  
10. <span data-ttu-id="f42fa-253">檔案配接器將包含結果集的訊息寫入至指定的輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="f42fa-253">The File adapter writes the message containing the result set to the designated output folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f42fa-254">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f42fa-254">See Also</span></span>  
 [<span data-ttu-id="f42fa-255">教學課程： 使用 BizTalk Adapter for PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="f42fa-255">Tutorials: Using BizTalk Adapter for PeopleSoft Enterprise</span></span>](../core/tutorials-using-biztalk-adapter-for-peoplesoft-enterprise.md)