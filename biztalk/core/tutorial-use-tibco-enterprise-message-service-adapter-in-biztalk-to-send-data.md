---
title: 教學課程： 使用 BizTalk Adapter for TIBCO Enterprise Message Service 來傳送資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1912d594-3839-4e04-bc40-93bd7cc0b309
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e2e2dc6fe0c1427ac959ce77d6ff4f46b4f4285
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010679"
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-enterprise-message-service-to-send-data"></a><span data-ttu-id="84335-102">教學課程： 使用 BizTalk Adapter for TIBCO Enterprise Message Service 來傳送資料</span><span class="sxs-lookup"><span data-stu-id="84335-102">Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Send Data</span></span>
<span data-ttu-id="84335-103">您可以使用 BizTalk Adapter for TIBCO Enterprise Message Service (EMS)，將資料傳送至 TIBCO 系統。</span><span class="sxs-lookup"><span data-stu-id="84335-103">You can use the BizTalk Adapter for TIBCO Enterprise Message Service (EMS) to send data to a TIBCO system.</span></span> <span data-ttu-id="84335-104">這個逐步解說將說明示範這一點的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="84335-104">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="84335-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="84335-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="84335-106">BizTalk Adapter for TIBCO EMS 會要求您加入 TIBCO EMS C# API，TIBCO。EMS.dll 至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="84335-106">BizTalk Adapter for TIBCO EMS requires that you add the TIBCO EMS C# API, TIBCO.EMS.dll, to the global assembly cache (GAC).</span></span> <span data-ttu-id="84335-107">如需安裝組件的詳細資訊，請參閱[TIBCO Enterprise Message Service 的需求和限制](../core/tibco-enterprise-message-service-requirements-and-limitations.md)。</span><span class="sxs-lookup"><span data-stu-id="84335-107">For more information about installing the assembly, see [TIBCO Enterprise Message Service Requirements and Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).</span></span>  
  
-   <span data-ttu-id="84335-108">在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。</span><span class="sxs-lookup"><span data-stu-id="84335-108">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="84335-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="84335-109">What This Sample Does</span></span>  
 <span data-ttu-id="84335-110">此範例會收取某個 XML 檔案，從檔案資料夾、 將該檔案傳送至協調流程，並再使用 BizTalk Adapter for TIBCO Enterprise Message Service 在 TIBCO 系統中建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="84335-110">This sample picks up an XML file from a file folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Enterprise Message Service to create a record in the TIBCO system.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="84335-111">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="84335-111">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="84335-112">在 Visual Studio 中設計的這個範例說明使用 BizTalk Adapter for TIBCO Enterprise Message Service 與 BizTalk 協調流程的基本功能。</span><span class="sxs-lookup"><span data-stu-id="84335-112">This sample, designed in Visual Studio, illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="84335-113">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="84335-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="84335-114">此範例的預設位置是</span><span class="sxs-lookup"><span data-stu-id="84335-114">The default location for the sample is</span></span>  
  
 <span data-ttu-id="84335-115">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) 企業訊息 Service(TM) \Sdk\OneWaySend</span><span class="sxs-lookup"><span data-stu-id="84335-115">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWaySend</span></span>  
  
 <span data-ttu-id="84335-116">下表列出此範例中的檔案並提供描述。</span><span class="sxs-lookup"><span data-stu-id="84335-116">The following table lists and describes the files in the sample.</span></span>  
  
|<span data-ttu-id="84335-117">**執行階段專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="84335-117">**Runtime Project Filename**</span></span>|<span data-ttu-id="84335-118">**執行階段專案檔案描述**</span><span class="sxs-lookup"><span data-stu-id="84335-118">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="84335-119">OneWaySend.btproj</span><span class="sxs-lookup"><span data-stu-id="84335-119">OneWaySend.btproj</span></span><br /><br /> <span data-ttu-id="84335-120">OneWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="84335-120">OneWaySend.sln</span></span>|<span data-ttu-id="84335-121">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="84335-121">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="84335-122">Schema.xsd</span><span class="sxs-lookup"><span data-stu-id="84335-122">Schema.xsd</span></span>|<span data-ttu-id="84335-123">這個應用程式的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="84335-123">Schema file for the application.</span></span>|  
|<span data-ttu-id="84335-124">Orchestration.odx</span><span class="sxs-lookup"><span data-stu-id="84335-124">Orchestration.odx</span></span>|<span data-ttu-id="84335-125">這個應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="84335-125">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="84335-126">TIBCOEMSOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="84335-126">TIBCOEMSOneWaySend.snk</span></span>|<span data-ttu-id="84335-127">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="84335-127">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="84335-128">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="84335-128">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-ems"></a><span data-ttu-id="84335-129">建立新的 BizTalk Adapter for TIBCO EMS 執行個體</span><span class="sxs-lookup"><span data-stu-id="84335-129">Create a new instance of the BizTalk Adapter for TIBCO EMS</span></span>  
  
1.  <span data-ttu-id="84335-130">啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="84335-130">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="84335-131">按一下**啟動**，**所有程式**， **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]， **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="84335-131">Click **Start**, **All Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="84335-132">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="84335-132">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="84335-133">以滑鼠右鍵按一下**配接器**指向**新增**，**配接器**顯示**配接器屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84335-133">Right-click **Adapters** and point to **New**, **Adapter** to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="84335-134">輸入一個值**名稱**欄位，例如**TIBCO EMS**。</span><span class="sxs-lookup"><span data-stu-id="84335-134">Enter a value for the **Name** field, for example **TIBCO EMS**.</span></span>  
  
5.  <span data-ttu-id="84335-135">選取**TIBCO Enterprise Message System**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="84335-135">Select **TIBCO Enterprise Message System** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-send-port"></a><span data-ttu-id="84335-136">建立 BizTalk 傳送埠</span><span class="sxs-lookup"><span data-stu-id="84335-136">Create a BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="84335-137">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="84335-137">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="84335-138">以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠**顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84335-138">Right-click **Send Ports** and point to **New**, **Static One-way Send Port** to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="84335-139">輸入一個值**名稱**欄位，例如**TIBCOEMSOneWaySP**。</span><span class="sxs-lookup"><span data-stu-id="84335-139">Enter a value for the **Name** field, for example **TIBCOEMSOneWaySP**.</span></span>  
  
4.  <span data-ttu-id="84335-140">從使用中的配接器清單選取 TIBCO EMS 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84335-140">Select the TIBCO EMS adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="84335-141">這個值是在建立 TIBCO Enterprise Message System 配接器時指定了名稱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="84335-141">This value is the name that was specified when the TIBCO Enterprise Message System adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
5.  <span data-ttu-id="84335-142">輸入的值**伺服器連線定義**:</span><span class="sxs-lookup"><span data-stu-id="84335-142">Enter values for the **Server Connection definition**:</span></span>  
  
    |<span data-ttu-id="84335-143">**屬性**</span><span class="sxs-lookup"><span data-stu-id="84335-143">**Property**</span></span>|<span data-ttu-id="84335-144">**值**</span><span class="sxs-lookup"><span data-stu-id="84335-144">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="84335-145">目的地</span><span class="sxs-lookup"><span data-stu-id="84335-145">Destination</span></span>|<span data-ttu-id="84335-146">伺服器目的地佇列或主題名稱。</span><span class="sxs-lookup"><span data-stu-id="84335-146">The server destination queue or topic name.</span></span>|  
    |<span data-ttu-id="84335-147">通訊埠編號</span><span class="sxs-lookup"><span data-stu-id="84335-147">Port number</span></span>|<span data-ttu-id="84335-148">TIBCO 伺服器接聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="84335-148">The port on which the TIBCO server is listening.</span></span> <span data-ttu-id="84335-149">預設值為 7222。</span><span class="sxs-lookup"><span data-stu-id="84335-149">Default value is 7222.</span></span>|  
    |<span data-ttu-id="84335-150">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="84335-150">Server Name</span></span>|<span data-ttu-id="84335-151">TIBCO EMS 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="84335-151">The name of the TIBCO EMS server.</span></span>|  
  
6.  <span data-ttu-id="84335-152">輸入的值**使用者認證**:</span><span class="sxs-lookup"><span data-stu-id="84335-152">Enter values for the **User Credentials**:</span></span>  
  
    |<span data-ttu-id="84335-153">**屬性**</span><span class="sxs-lookup"><span data-stu-id="84335-153">**Property**</span></span>|<span data-ttu-id="84335-154">**值**</span><span class="sxs-lookup"><span data-stu-id="84335-154">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="84335-155">密碼</span><span class="sxs-lookup"><span data-stu-id="84335-155">Password</span></span>|<span data-ttu-id="84335-156">TIBCO EMS 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="84335-156">The password for the TIBCO EMS server.</span></span>|  
    |<span data-ttu-id="84335-157">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="84335-157">User name</span></span>|<span data-ttu-id="84335-158">TIBCO EMS 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="84335-158">The user name for the TIBCO EMS server.</span></span>|  
  
     <span data-ttu-id="84335-159">如需屬性的詳細資訊，請參閱[建立 TIBCO 企業訊息服務傳送處理常式](../core/creating-tibco-enterprise-message-service-send-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="84335-159">For more information about the properties, see [Creating  TIBCO Enterprise Message Service Send Handlers](../core/creating-tibco-enterprise-message-service-send-handlers.md).</span></span>  
  
7.  <span data-ttu-id="84335-160">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="84335-160">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="84335-161">選取**XML 傳輸**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="84335-161">Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
9. <span data-ttu-id="84335-162">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="84335-162">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-file-receive-port"></a><span data-ttu-id="84335-163">建立檔案接收埠</span><span class="sxs-lookup"><span data-stu-id="84335-163">Create a file receive port</span></span>  
  
1.  <span data-ttu-id="84335-164">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="84335-164">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="84335-165">以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠**以顯示 [接收埠屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84335-165">Right-click the Receive Ports folder and then click **New**, **One-way Receive Port** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="84335-166">輸入一個值**名稱**欄位，例如**TIBCOEMSOneWayFileRP**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="84335-166">Enter a value for the **Name** field, for example **TIBCOEMSOneWayFileRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-file-receive-location"></a><span data-ttu-id="84335-167">建立檔案接收位置</span><span class="sxs-lookup"><span data-stu-id="84335-167">Create a file receive location</span></span>  
  
1.  <span data-ttu-id="84335-168">為檔案接收位置建立一個資料夾來監視，例如 C:\Filesource。</span><span class="sxs-lookup"><span data-stu-id="84335-168">Create a folder for the file receive location to monitor, for example C:\Filesource.</span></span>  
  
2.  <span data-ttu-id="84335-169">以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置**顯示**接收位置屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84335-169">Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="84335-170">輸入一個值**名稱**欄位，例如**TIBCOEMSOneWayFileRL**。</span><span class="sxs-lookup"><span data-stu-id="84335-170">Enter a value for the **Name** field, for example **TIBCOEMSOneWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="84335-171">選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84335-171">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="84335-172">輸入您稍早建立的資料夾位置**接收資料夾**屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="84335-172">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="84335-173">選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="84335-173">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="84335-174">以滑鼠右鍵按一下接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="84335-174">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a><span data-ttu-id="84335-175">從配接器結構描述產生文件執行個體</span><span class="sxs-lookup"><span data-stu-id="84335-175">Generate a document instance from the Adapter schema</span></span>  
  
1.  <span data-ttu-id="84335-176">以滑鼠右鍵按一下方案總管 中的 Schema.xsd，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="84335-176">Right-click Schema.xsd in Solution Explorer and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="84335-177">在 [屬性] 視窗中，按一下以選取**輸出執行個體檔案名稱**選項在**一般**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="84335-177">In the Properties window, click to select the **Output Instance Filename** option under the **General** category.</span></span>  
  
3.  <span data-ttu-id="84335-178">按一下省略符號按鈕 （…） 以顯示**選取輸出檔案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84335-178">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
4.  <span data-ttu-id="84335-179">指定的資料夾和輸出檔案執行個體名稱，例如**C:\instance.xml**按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="84335-179">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="84335-180">請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="84335-180">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
5.  <span data-ttu-id="84335-181">以滑鼠右鍵按一下方案總管 中的 Schema.xsd，然後按一下**產生執行個體**產生文件執行個體中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="84335-181">Right-click Schema.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
#### <a name="modify-the-generated-document-instance"></a><span data-ttu-id="84335-182">修改產生的文件執行個體</span><span class="sxs-lookup"><span data-stu-id="84335-182">Modify the generated document instance</span></span>  
  
1.  <span data-ttu-id="84335-183">在文字編輯器 (如 [記事本]) 中開啟產生的文件執行個體，然後編輯文件執行個體的內容，以確保資料會在 TIBCO 系統中產生唯一的記錄。</span><span class="sxs-lookup"><span data-stu-id="84335-183">Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data will generate a unique record in the TIBCO system.</span></span> <span data-ttu-id="84335-184">例如，下列程式碼顯示這個資料檔案的第一個部分：</span><span class="sxs-lookup"><span data-stu-id="84335-184">For example the code below shows the first part of the data file:</span></span>  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoEMSOne_WaySend.TibcoEMSOneWaySendSchema">  
      <Name>Punya Palit</Name>  
      <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  <span data-ttu-id="84335-185">儲存已修改的文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="84335-185">Save the modified document instance.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="84335-186">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="84335-186">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="84335-187">以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**屬性**啟動專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="84335-187">Right-click the OneWaySend project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="84335-188">按一下**部署** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="84335-188">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="84335-189">輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="84335-189">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.</span></span>  
  
4.  <span data-ttu-id="84335-190">以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="84335-190">Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="84335-191">繫結和登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="84335-191">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="84335-192">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="84335-192">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="84335-193">按一下**重新整理**中 MMC 工具列或按下按鈕**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。</span><span class="sxs-lookup"><span data-stu-id="84335-193">Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="84335-194">按兩下協調流程以顯示**協調流程屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="84335-194">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="84335-195">按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="84335-195">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="84335-196">指定適當的繫結選項值，例如：</span><span class="sxs-lookup"><span data-stu-id="84335-196">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="84335-197">**參數**</span><span class="sxs-lookup"><span data-stu-id="84335-197">**Parameter**</span></span>|<span data-ttu-id="84335-198">**值**</span><span class="sxs-lookup"><span data-stu-id="84335-198">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="84335-199">Host</span><span class="sxs-lookup"><span data-stu-id="84335-199">Host</span></span>|<span data-ttu-id="84335-200">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="84335-200">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="84335-201">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="84335-201">FileReceivePort</span></span>|<span data-ttu-id="84335-202">TIBCOEMSOneWayFileRP</span><span class="sxs-lookup"><span data-stu-id="84335-202">TIBCOEMSOneWayFileRP</span></span>|  
    |<span data-ttu-id="84335-203">TibcoEMSOneWaySendPort</span><span class="sxs-lookup"><span data-stu-id="84335-203">TibcoEMSOneWaySendPort</span></span>|<span data-ttu-id="84335-204">TIBCOEMSOneWaySP</span><span class="sxs-lookup"><span data-stu-id="84335-204">TIBCOEMSOneWaySP</span></span>|  
  
6.  <span data-ttu-id="84335-205">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="84335-205">Click OK.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="84335-206">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="84335-206">Start the orchestration</span></span>  
  
-   <span data-ttu-id="84335-207">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="84335-207">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a><span data-ttu-id="84335-208">將文件執行個體拖放到檔案接收位置所監視的資料夾</span><span class="sxs-lookup"><span data-stu-id="84335-208">Drop a document instance into the folder monitored by the file receive location</span></span>  
  
-   <span data-ttu-id="84335-209">將稍早建立的文件執行個體複製到應用程式所監視的檔案接收資料夾。</span><span class="sxs-lookup"><span data-stu-id="84335-209">Copy the document instance that was created earlier to the file receive folder the application monitors.</span></span>  
  
#### <a name="verify-that-the-tibco-system-is-updated"></a><span data-ttu-id="84335-210">確認 TIBCO 系統已更新</span><span class="sxs-lookup"><span data-stu-id="84335-210">Verify that the TIBCO system is updated</span></span>  
  
-   <span data-ttu-id="84335-211">使用 TIBCO Web 介面，確認已從 XML 檔案中的資料建立記錄。</span><span class="sxs-lookup"><span data-stu-id="84335-211">Use the TIBCO web interface to verify that the record was created from the data in the XML file.</span></span>  
  
 <span data-ttu-id="84335-212">如果文件執行個體處理成功，則會發生以下一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="84335-212">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="84335-213">檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="84335-213">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="84335-214">協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程執行個體，然後將訊息傳送至這個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="84335-214">The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="84335-215">協調流程執行個體使用指定的協調流程中的邏輯處理訊息，並將訊息發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="84335-215">The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="84335-216">TIBCO 傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會將訊息傳送至 TIBCO 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="84335-216">The TIBCO send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the TIBCO send port.</span></span>  
  
5.  <span data-ttu-id="84335-217">傳送埠將訊息交給 BizTalk Adapter for TIBCO Enterprise Message Service。</span><span class="sxs-lookup"><span data-stu-id="84335-217">The send port hands the message to the BizTalk Adapter for TIBCO Enterprise Message Service.</span></span>  
  
6.  <span data-ttu-id="84335-218">BizTalk Adapter for TIBCO Enterprise Message Service 將訊息傳送至 TIBCO 系統。</span><span class="sxs-lookup"><span data-stu-id="84335-218">The BizTalk Adapter for TIBCO Enterprise Message Service sends the message to the TIBCO system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84335-219">請參閱</span><span class="sxs-lookup"><span data-stu-id="84335-219">See Also</span></span>  
 <span data-ttu-id="84335-220">[教學課程： 使用 BizTalk Adapter for TIBCO Enterprise Message Service 來接收資料](../core/tutorial-us-the-biztalk-adapter-for-tibco-message-service-to-receive-data.md) </span><span class="sxs-lookup"><span data-stu-id="84335-220">[Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Receive Data](../core/tutorial-us-the-biztalk-adapter-for-tibco-message-service-to-receive-data.md) </span></span>  
 <span data-ttu-id="84335-221">[教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md) </span><span class="sxs-lookup"><span data-stu-id="84335-221">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md) </span></span>  
 [<span data-ttu-id="84335-222">快速入門</span><span class="sxs-lookup"><span data-stu-id="84335-222">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)