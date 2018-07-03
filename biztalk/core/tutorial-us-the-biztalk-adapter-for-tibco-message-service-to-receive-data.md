---
title: 教學課程： 使用 BizTalk Adapter for TIBCO Enterprise Message Service 來接收資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc5a63ec-1897-4c9b-b37f-cdcec151b1c9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d4f4ac08b979dfc959c6e2ea0aab68b8c07db67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977519"
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-enterprise-message-service-to-receive-data"></a><span data-ttu-id="c49e7-102">教學課程：使用 BizTalk Adapter for TIBCO Enterprise Message Service 來接收資料</span><span class="sxs-lookup"><span data-stu-id="c49e7-102">Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Receive Data</span></span>
<span data-ttu-id="c49e7-103">您可以使用 BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 接收來自 TIBCO 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="c49e7-103">You can use the BizTalk Adapter for TIBCO Enterprise Message Service (EMS) to receive data from a TIBCO system.</span></span> <span data-ttu-id="c49e7-104">這個逐步解說將說明示範這一點的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="c49e7-104">This walkthrough describes an SDK sample that illustrates this.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="c49e7-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="c49e7-105">Prerequisites</span></span>  

- <span data-ttu-id="c49e7-106">若要使用 BizTalk Adapter for TIBCO Enterprise Message Service，您必須將 TIBCO EMS C# API、TIBCO.EMS.dll 新增至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="c49e7-106">BizTalk Adapter for TIBCO Enterprise Message Service requires that you add the TIBCO EMS C# API, TIBCO.EMS.dll, to the global assembly cache (GAC).</span></span> <span data-ttu-id="c49e7-107">如需有關如何安裝組件的詳細資訊，請參閱 < [TIBCO Enterprise Message Service 需求和限制](../core/tibco-enterprise-message-service-requirements-and-limitations.md)。</span><span class="sxs-lookup"><span data-stu-id="c49e7-107">For more information about installing the assembly, see [TIBCO Enterprise Message Service Requirements and Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).</span></span>  

- <span data-ttu-id="c49e7-108">在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。</span><span class="sxs-lookup"><span data-stu-id="c49e7-108">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="c49e7-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="c49e7-109">What This Sample Does</span></span>  
 <span data-ttu-id="c49e7-110">此範例會從某個資料夾收取某個 XML 檔案、將該檔案傳送至協調流程，然後使用 BizTalk Adapter for TIBCO Enterprise Message Service 接收來自 TIBCO 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="c49e7-110">This sample picks up an XML file from a folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Enterprise Message Service to retrieve data from a TIBCO system.</span></span> <span data-ttu-id="c49e7-111">結果會寫入至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c49e7-111">The result is written to an XML file.</span></span>  

## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="c49e7-112">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="c49e7-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="c49e7-113">在 Visual Studio 中設計的這個範例說明如何使用 BizTalk Adapter for TIBCO Enterprise Message Service 與 BizTalk 協調流程的基本功能。</span><span class="sxs-lookup"><span data-stu-id="c49e7-113">This sample, designed in Visual Studio, illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.</span></span>  

> [!NOTE]
>  <span data-ttu-id="c49e7-114">此範例假設您已知道如何傳送來自 TIBCO 的訊息以讓應用程式處理。</span><span class="sxs-lookup"><span data-stu-id="c49e7-114">The sample assumes that you know how to send a message from TIBCO for the application to process.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="c49e7-115">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="c49e7-115">Where to Find This Sample</span></span>  
 <span data-ttu-id="c49e7-116">此範例的預設位置是</span><span class="sxs-lookup"><span data-stu-id="c49e7-116">The default location for the sample is</span></span>  

 <span data-ttu-id="c49e7-117">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWayReceive</span><span class="sxs-lookup"><span data-stu-id="c49e7-117">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWayReceive</span></span>  

 <span data-ttu-id="c49e7-118">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="c49e7-118">The following table shows the files in this sample and describes their purpose.</span></span>  

|<span data-ttu-id="c49e7-119">**執行階段專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="c49e7-119">**Runtime Project Filename**</span></span>|<span data-ttu-id="c49e7-120">**執行階段專案檔案描述**</span><span class="sxs-lookup"><span data-stu-id="c49e7-120">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="c49e7-121">OneWayReceive.btproj、</span><span class="sxs-lookup"><span data-stu-id="c49e7-121">OneWayReceive.btproj,</span></span><br /><br /> <span data-ttu-id="c49e7-122">OneWayReceive.sln</span><span class="sxs-lookup"><span data-stu-id="c49e7-122">OneWayReceive.sln</span></span>|<span data-ttu-id="c49e7-123">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="c49e7-123">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="c49e7-124">Schema.xsd、</span><span class="sxs-lookup"><span data-stu-id="c49e7-124">Schema.xsd,</span></span>|<span data-ttu-id="c49e7-125">這個應用程式的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="c49e7-125">Schema file for the application.</span></span>|  
|<span data-ttu-id="c49e7-126">Orchestration.odx</span><span class="sxs-lookup"><span data-stu-id="c49e7-126">Orchestration.odx</span></span>|<span data-ttu-id="c49e7-127">這個應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="c49e7-127">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="c49e7-128">TIBCOEMSOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="c49e7-128">TIBCOEMSOneWaySend.snk</span></span>|<span data-ttu-id="c49e7-129">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="c49e7-129">The strong naming key file.</span></span>|  

## <a name="how-to-use-this-sample"></a><span data-ttu-id="c49e7-130">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="c49e7-130">How to Use This Sample</span></span>  

#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-ems"></a><span data-ttu-id="c49e7-131">建立新的 BizTalk Adapter for TIBCO EMS 執行個體</span><span class="sxs-lookup"><span data-stu-id="c49e7-131">Create a new instance of the BizTalk Adapter for TIBCO EMS</span></span>  

1. <span data-ttu-id="c49e7-132">啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="c49e7-132">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="c49e7-133">按一下 **開始**，**程式**， **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]， **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-133">Click **Start**, **Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="c49e7-134">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理]**，展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 [ **配接器**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-134">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  

3. <span data-ttu-id="c49e7-135">以滑鼠右鍵按一下**配接器**，指向**新增**，**配接器**以顯示**配接器屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c49e7-135">Right-click **Adapters** and point to **New**, **Adapter** to display the **Adapter Properties** dialog.</span></span>  

4. <span data-ttu-id="c49e7-136">輸入的值**名稱**欄位，例如**TIBCO EMS**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-136">Enter a value for the **Name** field, for example **TIBCO EMS**.</span></span>  

5. <span data-ttu-id="c49e7-137">選取**TIBCO Enterprise Message System**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-137">Select **TIBCO Enterprise Message System** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  

#### <a name="create-a-biztalk-receive-port"></a><span data-ttu-id="c49e7-138">建立 BizTalk 接收埠</span><span class="sxs-lookup"><span data-stu-id="c49e7-138">Create a BizTalk Receive Port</span></span>  

1. <span data-ttu-id="c49e7-139">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-139">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  

2. <span data-ttu-id="c49e7-140">以滑鼠右鍵按一下接收埠 資料夾，然後按一下**的新**，**單向接收埠**以顯示 接收埠屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c49e7-140">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port** to display the Receive Port Properties dialog.</span></span>  

3. <span data-ttu-id="c49e7-141">輸入的值**名稱**欄位，例如**TIBCOEMSOneWayRP**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-141">Enter a value for the **Name** field, for example **TIBCOEMSOneWayRP**, and click **OK**.</span></span>  

#### <a name="create-a-biztalk-receive-location"></a><span data-ttu-id="c49e7-142">建立 BizTalk 接收位置</span><span class="sxs-lookup"><span data-stu-id="c49e7-142">Create a BizTalk Receive Location</span></span>  

1. <span data-ttu-id="c49e7-143">以滑鼠右鍵按一下新的接收埠，然後按一下**的新**，**接收位置**以顯示**接收位置屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c49e7-143">Right-click the new receive port and then click **New**, **Receive Location** to display the **Receive Location Properties** dialog.</span></span>  

2. <span data-ttu-id="c49e7-144">輸入的值**名稱**欄位，例如**TIBCOEMSOneWayRL**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-144">Enter a value for the **Name** field, for example **TIBCOEMSOneWayRL**.</span></span>  

3. <span data-ttu-id="c49e7-145">從使用中的配接器清單中選取 TIBCO EMS 配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c49e7-145">Select the TIBCO EMS adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="c49e7-146">這個值是在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中建立 TIBCO 配接器時指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="c49e7-146">This value is the name that was specified when the TIBCO adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  

4. <span data-ttu-id="c49e7-147">輸入的值**伺服器連線定義**:</span><span class="sxs-lookup"><span data-stu-id="c49e7-147">Enter values for the **Server Connection definition**:</span></span>  


   | <span data-ttu-id="c49e7-148">**屬性**</span><span class="sxs-lookup"><span data-stu-id="c49e7-148">**Property**</span></span> |                                <span data-ttu-id="c49e7-149">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="c49e7-149">**Value**</span></span>                                |
   |--------------|-------------------------------------------------------------------------|
   | <span data-ttu-id="c49e7-150">目的地</span><span class="sxs-lookup"><span data-stu-id="c49e7-150">Destination</span></span>  |               <span data-ttu-id="c49e7-151">伺服器目的地佇列或主題名稱。</span><span class="sxs-lookup"><span data-stu-id="c49e7-151">The server destination queue or topic name.</span></span>               |
   | <span data-ttu-id="c49e7-152">通訊埠編號</span><span class="sxs-lookup"><span data-stu-id="c49e7-152">Port number</span></span>  | <span data-ttu-id="c49e7-153">TIBCO 伺服器接聽的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c49e7-153">The port on which the TIBCO server is listening.</span></span> <span data-ttu-id="c49e7-154">預設值為 7222。</span><span class="sxs-lookup"><span data-stu-id="c49e7-154">Default value is 7222.</span></span> |
   | <span data-ttu-id="c49e7-155">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="c49e7-155">Server Name</span></span>  |                    <span data-ttu-id="c49e7-156">TIBCO EMS 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="c49e7-156">The name of the TIBCO EMS server.</span></span>                    |


5. <span data-ttu-id="c49e7-157">輸入的值**使用者認證**:</span><span class="sxs-lookup"><span data-stu-id="c49e7-157">Enter values for the **User Credentials**:</span></span>  

   |<span data-ttu-id="c49e7-158">**屬性**</span><span class="sxs-lookup"><span data-stu-id="c49e7-158">**Property**</span></span>|<span data-ttu-id="c49e7-159">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="c49e7-159">**Value**</span></span>|  
   |------------------|---------------|  
   |<span data-ttu-id="c49e7-160">[密碼]</span><span class="sxs-lookup"><span data-stu-id="c49e7-160">Password</span></span>|<span data-ttu-id="c49e7-161">TIBCO EMS 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="c49e7-161">The password for the TIBCO EMS server.</span></span>|  
   |<span data-ttu-id="c49e7-162">[使用者名稱]</span><span class="sxs-lookup"><span data-stu-id="c49e7-162">User name</span></span>|<span data-ttu-id="c49e7-163">TIBCO EMS 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="c49e7-163">The user name for the TIBCO EMS server.</span></span>|  

    <span data-ttu-id="c49e7-164">如需有關屬性的詳細資訊，請參閱[建立 TIBCO Enterprise Message Service 接收處理常式](../core/creating-tibco-enterprise-message-service-receive-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="c49e7-164">For more information about the properties, see [Creating TIBCO Enterprise Message Service Receive Handlers](../core/creating-tibco-enterprise-message-service-receive-handlers.md).</span></span>  

6. <span data-ttu-id="c49e7-165">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c49e7-165">Click **OK**.</span></span>  

7. <span data-ttu-id="c49e7-166">選取  **XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-166">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  

8. <span data-ttu-id="c49e7-167">以滑鼠右鍵按一下接收位置，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-167">Right-click the receive location and click **Enable**.</span></span>  

#### <a name="create-a-one-way-file-send-port"></a><span data-ttu-id="c49e7-168">建立單向檔案傳送埠</span><span class="sxs-lookup"><span data-stu-id="c49e7-168">Create a one-way file send port</span></span>  

1. <span data-ttu-id="c49e7-169">建立傳送埠所要使用的目標資料夾，例如 C:\FilesOut。</span><span class="sxs-lookup"><span data-stu-id="c49e7-169">Create a target folder to be used by the send port, for example C:\FilesOut.</span></span>  

2. <span data-ttu-id="c49e7-170">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-170">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  

3. <span data-ttu-id="c49e7-171">以滑鼠右鍵按一下**傳送埠**，指向**新增**，**靜態單向傳送埠**以顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c49e7-171">Right-click **Send Ports** and point to **New**, **Static One-way Send Port** to display the **Send Port Properties** dialog.</span></span>  

4. <span data-ttu-id="c49e7-172">輸入的值**名稱**欄位，例如**TIBCOEMSOneWayFileSP**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-172">Enter a value for the **Name** field, for example **TIBCOEMSOneWayFileSP**.</span></span>  

5. <span data-ttu-id="c49e7-173">選取 **檔案**從清單中的可用配接器**型別**下拉式清單方塊，然後按一下**設定** 按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c49e7-173">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  

6. <span data-ttu-id="c49e7-174">針對**目的地資料夾** 屬性中，輸入您稍早建立之資料夾的位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-174">For the **Destination Folder** property, enter the location of the folder that you created earlier and click **OK**.</span></span>  

7. <span data-ttu-id="c49e7-175">選取  **XMLTransmit**從清單中可用的管線的管線**傳送管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-175">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  

8. <span data-ttu-id="c49e7-176">以滑鼠右鍵按一下傳送埠，然後按一下 **啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c49e7-176">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  

#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="c49e7-177">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="c49e7-177">Build and deploy the project</span></span>  

1. <span data-ttu-id="c49e7-178">以滑鼠右鍵按一下方案總管] 中的 Onewaysend 專案，然後按一下 [**屬性**啟動專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="c49e7-178">Right-click the OneWayReceive project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  

2. <span data-ttu-id="c49e7-179">按一下 [**部署**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c49e7-179">Click the **Deployment** tab.</span></span>  

3. <span data-ttu-id="c49e7-180">輸入適當的值，如**伺服器**屬性並**組態資料庫**下的屬性**BizTalk 群組**類別。</span><span class="sxs-lookup"><span data-stu-id="c49e7-180">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.</span></span>  

4. <span data-ttu-id="c49e7-181">以滑鼠右鍵按一下方案總管] 中的 Onewaysend 專案，然後按一下 [ **Deploy**以建置專案並部署組件，以[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="c49e7-181">Right-click the OneWayReceive project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  

#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="c49e7-182">繫結和登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="c49e7-182">Bind and Enlist the orchestration</span></span>  

1. <span data-ttu-id="c49e7-183">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="c49e7-183">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  

2. <span data-ttu-id="c49e7-184">按一下 **重新整理**按鈕[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台工具列或按下**F5**若要重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。</span><span class="sxs-lookup"><span data-stu-id="c49e7-184">Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  

3. <span data-ttu-id="c49e7-185">按兩下協調流程，以顯示**協調流程屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c49e7-185">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  

4. <span data-ttu-id="c49e7-186">按一下 [**繫結**以顯示協調流程繫結選項] 對話方塊的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="c49e7-186">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  

5. <span data-ttu-id="c49e7-187">指定適當的繫結選項值，例如：</span><span class="sxs-lookup"><span data-stu-id="c49e7-187">Specify the appropriate values for the binding options, for example:</span></span>  


   |         <span data-ttu-id="c49e7-188">**參數**</span><span class="sxs-lookup"><span data-stu-id="c49e7-188">**Parameter**</span></span>          |        <span data-ttu-id="c49e7-189">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="c49e7-189">**Value**</span></span>         |
   |--------------------------------|--------------------------|
   |              <span data-ttu-id="c49e7-190">Host</span><span class="sxs-lookup"><span data-stu-id="c49e7-190">Host</span></span>              | <span data-ttu-id="c49e7-191">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="c49e7-191">BizTalkServerApplication</span></span> |
   |          <span data-ttu-id="c49e7-192">FileSendPort</span><span class="sxs-lookup"><span data-stu-id="c49e7-192">FileSendPort</span></span>          |   <span data-ttu-id="c49e7-193">TIBCOEMSOneWayFileSP</span><span class="sxs-lookup"><span data-stu-id="c49e7-193">TIBCOEMSOneWayFileSP</span></span>   |
   | <span data-ttu-id="c49e7-194">TibcoEMSOneWayReceiveOperation</span><span class="sxs-lookup"><span data-stu-id="c49e7-194">TibcoEMSOneWayReceiveOperation</span></span> |     <span data-ttu-id="c49e7-195">TIBCOEMSOneWayRP</span><span class="sxs-lookup"><span data-stu-id="c49e7-195">TIBCOEMSOneWayRP</span></span>     |


6. <span data-ttu-id="c49e7-196">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="c49e7-196">Click **OK**.</span></span>  

#### <a name="start-the-orchestration"></a><span data-ttu-id="c49e7-197">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="c49e7-197">Start the orchestration</span></span>  

- <span data-ttu-id="c49e7-198">在 [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]管理主控台中，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="c49e7-198">In the [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  

#### <a name="verify-that-the-application-receives-a-message"></a><span data-ttu-id="c49e7-199">確認應用程式收到訊息</span><span class="sxs-lookup"><span data-stu-id="c49e7-199">Verify that the application receives a message</span></span>  

- <span data-ttu-id="c49e7-200">開啟檔案傳送埠進行傳送時依設定要使用的目標資料夾，然後確認已產生輸出文件。</span><span class="sxs-lookup"><span data-stu-id="c49e7-200">Open the folder that the file send port is configured to send to and verify that an output document was generated.</span></span> <span data-ttu-id="c49e7-201">此檔案應包含 BizTalk Adapter for TIBCO Enterprise Message Service 處理查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="c49e7-201">This file should contain the results of the query that was processed by the BizTalk Adapter for TIBCO Enterprise Message Service.</span></span>  

  <span data-ttu-id="c49e7-202">如果文件執行個體處理成功，則會發生以下一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="c49e7-202">The following sequence of events occurs if the document instance is processed successfully:</span></span>  

1.  <span data-ttu-id="c49e7-203">TIBCO EMS 配接器接收來自 TIBCO 系統的訊息，並以 BizTalk 訊息的形式將其發佈至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="c49e7-203">The TIBCO EMS adapter receives a message from TIBCO system and publishes it to the MessageBox as a BizTalk message.</span></span>  

2.  <span data-ttu-id="c49e7-204">協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程的執行個體，然後將訊息傳送至這個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="c49e7-204">The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.</span></span>  

3.  <span data-ttu-id="c49e7-205">協調流程執行個體將訊息發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="c49e7-205">The orchestration instance publishes the message back to the MessageBox.</span></span>  

4.  <span data-ttu-id="c49e7-206">檔案傳送埠訂閱這個訊息，因此 BizTalk 會將訊息傳送至檔案配接器。</span><span class="sxs-lookup"><span data-stu-id="c49e7-206">The File send port subscribes to this message so BizTalk sends the message to the File adapter.</span></span>  

5.  <span data-ttu-id="c49e7-207">檔案配接器將包含結果集的訊息寫入至指定的輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="c49e7-207">The File adapter writes the message containing the result set to the designated output folder.</span></span>  

## <a name="see-also"></a><span data-ttu-id="c49e7-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c49e7-208">See Also</span></span>  
 <span data-ttu-id="c49e7-209">[教學課程： 使用 BizTalk Adapter for TIBCO Enterprise Message Service 來傳送資料](../core/tutorial-use-tibco-enterprise-message-service-adapter-in-biztalk-to-send-data.md) </span><span class="sxs-lookup"><span data-stu-id="c49e7-209">[Tutorial: Using the BizTalk Adapter for TIBCO Enterprise Message Service to Send Data](../core/tutorial-use-tibco-enterprise-message-service-adapter-in-biztalk-to-send-data.md) </span></span>  
 <span data-ttu-id="c49e7-210">[教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md) </span><span class="sxs-lookup"><span data-stu-id="c49e7-210">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md) </span></span>  
 [<span data-ttu-id="c49e7-211">快速入門</span><span class="sxs-lookup"><span data-stu-id="c49e7-211">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)