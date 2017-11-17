---
title: "教學課程： 使用 TIBCO Rendezvous 配接器傳送 |Microsoft 文件"
description: "使用 BizTalk Adapter for TIBCO Rendezvous 在 BizTalk Server 中，將資料傳送至 TIBCO 系統的逐步指南"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b761ce2d-3465-43e0-bd8d-4d68b523226a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a08987e92465358276df7936f39cfa7c449c0503
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data"></a><span data-ttu-id="d2f4c-103">教學課程：使用 BizTalk Adapter for TIBCO Rendezvous 來傳送資料</span><span class="sxs-lookup"><span data-stu-id="d2f4c-103">Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data</span></span>
<span data-ttu-id="d2f4c-104">您可以使用 BizTalk Adapter for TIBCO Rendezvous 將資料傳送至 TIBCO 系統。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-104">You can use the BizTalk Adapter for TIBCO Rendezvous to send data to a TIBCO system.</span></span> <span data-ttu-id="d2f4c-105">這個逐步解說將說明示範這一點的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-105">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d2f4c-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="d2f4c-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="d2f4c-107">在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-107">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
-   <span data-ttu-id="d2f4c-108">此範例會使用包含訊息內容屬性的 DLL：Microsoft.BizTalk.Adapters.TibRV.Properties.dll。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-108">The sample uses a DLL containing message context properties: Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span></span> <span data-ttu-id="d2f4c-109">您可能需要更新方案對這個程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-109">You may need to update the solution's reference to this library.</span></span> <span data-ttu-id="d2f4c-110">如需詳細資訊，請參閱[BizTalk Server 訊息內容屬性 （傳送處理常式）](../core/biztalk-server-message-context-properties-send-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-110">For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md).</span></span>  
  
## <a name="about-the-sample"></a><span data-ttu-id="d2f4c-111">關於範例</span><span class="sxs-lookup"><span data-stu-id="d2f4c-111">About the sample</span></span> 

- <span data-ttu-id="d2f4c-112">此範例會從某個檔案資料夾收取某個 XML 檔案、將該檔案傳送至協調流程，然後使用 BizTalk Adapter for TIBCO Rendezvous 在 TIBCO 系統中建立一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-112">This sample picks up an XML file from a file folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Rendezvous to create a record in the TIBCO system.</span></span>  
  
- <span data-ttu-id="d2f4c-113">以 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計的這個範例，示範了將 BizTalk Adapter for TIBCO Rendezvous 與 BizTalk 協調流程搭配使用的基本功能。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-113">This sample, designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Rendezvous with a BizTalk orchestration.</span></span>  
  
- <span data-ttu-id="d2f4c-114">此範例的預設位置是`C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend`，並包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="d2f4c-114">The default location for the sample is `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend`, and includes the following files:</span></span> 
    
    |<span data-ttu-id="d2f4c-115">**執行階段專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-115">**Runtime Project Filename**</span></span>|<span data-ttu-id="d2f4c-116">**執行階段專案檔案描述**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-116">**Runtime Project File Description**</span></span>|  
    |---|---|  
    |<span data-ttu-id="d2f4c-117">OneWaySend.btproj</span><span class="sxs-lookup"><span data-stu-id="d2f4c-117">OneWaySend.btproj</span></span><br /><br /> <span data-ttu-id="d2f4c-118">OneWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="d2f4c-118">OneWaySend.sln</span></span>|<span data-ttu-id="d2f4c-119">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-119">Project and solution files for the application.</span></span>|  
    |<span data-ttu-id="d2f4c-120">Schema.xsd</span><span class="sxs-lookup"><span data-stu-id="d2f4c-120">Schema.xsd</span></span><br /><br /> <span data-ttu-id="d2f4c-121">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="d2f4c-121">PropertySchema.xsd</span></span>|<span data-ttu-id="d2f4c-122">這個應用程式的結構描述和屬性結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-122">Schema and property schema files for the application.</span></span>|  
    |<span data-ttu-id="d2f4c-123">Orchestration.odx</span><span class="sxs-lookup"><span data-stu-id="d2f4c-123">Orchestration.odx</span></span>|<span data-ttu-id="d2f4c-124">這個應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-124">The orchestration used by the application.</span></span>|  
    |<span data-ttu-id="d2f4c-125">TIBCORendezvousOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="d2f4c-125">TIBCORendezvousOneWaySend.snk</span></span>|<span data-ttu-id="d2f4c-126">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-126">The strong naming key file.</span></span>|  
  
## <a name="step-1-add-the-adapter-to-biztalk-administration"></a><span data-ttu-id="d2f4c-127">步驟 1： 加入 BizTalk 管理配接器</span><span class="sxs-lookup"><span data-stu-id="d2f4c-127">Step 1: Add the adapter to BizTalk Administration</span></span>
  
1.  <span data-ttu-id="d2f4c-128">在**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-128">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="d2f4c-129">以滑鼠右鍵按一下**配接器**指向**新增**，**配接器...**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-129">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="d2f4c-130">若要顯示**配接器屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-130">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="d2f4c-131">輸入一個值**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-131">Enter a value for the **Name** field.</span></span> <span data-ttu-id="d2f4c-132">例如，輸入**TIBCO Rendezvous**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-132">For example, enter **TIBCO Rendezvous**.</span></span>  
  
5.  <span data-ttu-id="d2f4c-133">選取**TIBCO(r) 器**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-133">Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
## <a name="step-2-create-a-send-port"></a><span data-ttu-id="d2f4c-134">步驟 2： 建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="d2f4c-134">Step 2: Create a Send Port</span></span>  
  
1.  <span data-ttu-id="d2f4c-135">在**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，依序展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-135">In  **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="d2f4c-136">以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠...**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-136">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…**</span></span> <span data-ttu-id="d2f4c-137">若要顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-137">to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="d2f4c-138">輸入一個值**名稱**欄位，例如**TIBCORndOneWaySP**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-138">Enter a value for the **Name** field, for example **TIBCORndOneWaySP**.</span></span>  
  
4.  <span data-ttu-id="d2f4c-139">從使用中的配接器清單選取 TIBCO Rendezvous 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**的傳輸屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-139">Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2f4c-140">這個值是在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中建立 TIBCO Enterprise Message System 配接器時指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-140">This value is the name that was specified when the TIBCO Enterprise Message System adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
5.  <span data-ttu-id="d2f4c-141">輸入的值**認證寄件者屬性**:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-141">Enter values for the **Certified Sender Properties**:</span></span>  
  
    |<span data-ttu-id="d2f4c-142">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-142">**Property**</span></span>|<span data-ttu-id="d2f4c-143">**值**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-143">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="d2f4c-144">分類帳檔案名稱</span><span class="sxs-lookup"><span data-stu-id="d2f4c-144">Ledger file name</span></span>|<span data-ttu-id="d2f4c-145">要用於永續性認證訊息傳遞的分類帳檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-145">Ledger file name to use for persistent certified message delivery.</span></span>|  
    |<span data-ttu-id="d2f4c-146">可重複使用的名稱</span><span class="sxs-lookup"><span data-stu-id="d2f4c-146">Reusable name</span></span>|<span data-ttu-id="d2f4c-147">要用於認證訊息傳遞的可重複使用對應名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-147">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="d2f4c-148">在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-148">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
6.  <span data-ttu-id="d2f4c-149">輸入的值**認證**:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-149">Enter values for the **Credentials**:</span></span>  
  
    |<span data-ttu-id="d2f4c-150">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-150">**Property**</span></span>|<span data-ttu-id="d2f4c-151">**值**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-151">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="d2f4c-152">密碼</span><span class="sxs-lookup"><span data-stu-id="d2f4c-152">Password</span></span>|<span data-ttu-id="d2f4c-153">TIBCO Rendezvous 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-153">The password for the TIBCO Rendezvous server.</span></span>|  
    |<span data-ttu-id="d2f4c-154">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="d2f4c-154">User name</span></span>|<span data-ttu-id="d2f4c-155">TIBCO Rendezvous 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-155">The user name for the TIBCO Rendezvous server.</span></span>|  
  
7.  <span data-ttu-id="d2f4c-156">輸入的值**RendezvousTransport**:</span><span class="sxs-lookup"><span data-stu-id="d2f4c-156">Enter values for the **RendezvousTransport**:</span></span>  
  
    |<span data-ttu-id="d2f4c-157">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-157">**Property**</span></span>|<span data-ttu-id="d2f4c-158">**值**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-158">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="d2f4c-159">精靈</span><span class="sxs-lookup"><span data-stu-id="d2f4c-159">Daemon</span></span>|<span data-ttu-id="d2f4c-160">Rendezvous 傳輸精靈參數。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-160">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="d2f4c-161">網路</span><span class="sxs-lookup"><span data-stu-id="d2f4c-161">Network</span></span>|<span data-ttu-id="d2f4c-162">Rendezvous 傳輸網路參數。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-162">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="d2f4c-163">服務</span><span class="sxs-lookup"><span data-stu-id="d2f4c-163">Service</span></span>|<span data-ttu-id="d2f4c-164">Rendezvous 傳輸服務參數。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-164">Rendezvous Transport Service parameter.</span></span>|  
  
     <span data-ttu-id="d2f4c-165">如需屬性的詳細資訊，請參閱[建立傳送成品](../core/creating-tibco-rendezvous-send-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-165">For more information about the properties, see [Create the send artifacts](../core/creating-tibco-rendezvous-send-handlers.md).</span></span>  
  
8.  <span data-ttu-id="d2f4c-166">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-166">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d2f4c-167">選取**XML 傳輸**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-167">Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
10. <span data-ttu-id="d2f4c-168">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-168">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
## <a name="step-3-create-a-receive-port"></a><span data-ttu-id="d2f4c-169">步驟 3： 建立接收埠</span><span class="sxs-lookup"><span data-stu-id="d2f4c-169">Step 3: Create a receive port</span></span>  
  
1.  <span data-ttu-id="d2f4c-170">在**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，依序展開**BizTalk Application 1**，然後按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-170">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="d2f4c-171">以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠...**以顯示 [接收埠屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-171">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="d2f4c-172">輸入一個值**名稱**欄位，例如**TIBCORndOneWayFileRP**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-172">Enter a value for the **Name** field, for example **TIBCORndOneWayFileRP**, and click **OK**.</span></span>  
  
## <a name="step-4-create-a-receive-location"></a><span data-ttu-id="d2f4c-173">步驟 4： 建立接收位置</span><span class="sxs-lookup"><span data-stu-id="d2f4c-173">Step 4: Create a receive location</span></span>  
  
1.  <span data-ttu-id="d2f4c-174">為檔案接收位置建立一個資料夾來監視，例如 C:\Filesource。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-174">Create a folder for the file receive location to monitor, for example C:\Filesource.</span></span>  
  
2.  <span data-ttu-id="d2f4c-175">以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置...**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-175">Right-click the new receive port and then click **New**, **Receive Location…**</span></span> <span data-ttu-id="d2f4c-176">若要顯示**接收位置屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-176">to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="d2f4c-177">輸入一個值**名稱**欄位，例如**TIBCORndOneWayFileRL**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-177">Enter a value for the **Name** field, for example **TIBCORndOneWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="d2f4c-178">選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-178">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="d2f4c-179">輸入您稍早建立的資料夾位置**接收資料夾**屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-179">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="d2f4c-180">選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-180">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="d2f4c-181">以滑鼠右鍵按一下接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-181">Right-click the receive location and click **Enable**.</span></span>  
  
## <a name="step-5-generate-a-document-instance-from-the-schema"></a><span data-ttu-id="d2f4c-182">步驟 5： 從結構描述產生文件執行個體</span><span class="sxs-lookup"><span data-stu-id="d2f4c-182">Step 5: Generate a document instance from the schema</span></span>  
  
1.  <span data-ttu-id="d2f4c-183">在 Visual Studio 中，按一下滑鼠右鍵在 方案總管 中的 Schema.xsd，按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-183">In Visual Studio,right-click Schema.xsd in Solution Explorer, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d2f4c-184">在 [屬性] 視窗中，按一下以選取**輸出執行個體檔案名稱**選項在**一般**> 一節。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-184">In the Properties window, click to select the **Output Instance Filename** option under the **General** section.</span></span>  
  
3.  <span data-ttu-id="d2f4c-185">按一下省略符號按鈕 （…） 以顯示**選取輸出檔案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-185">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
4.  <span data-ttu-id="d2f4c-186">指定的資料夾和輸出檔案執行個體名稱，例如**C:\instance.xml**按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-186">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2f4c-187">請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-187">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
5.  <span data-ttu-id="d2f4c-188">以滑鼠右鍵按一下方案總管 中的 Schema.xsd，然後按一下**產生執行個體**產生文件執行個體中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-188">Right-click Schema.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
## <a name="step-6-update-the-generated-document-instance"></a><span data-ttu-id="d2f4c-189">步驟 6： 更新產生的文件執行個體</span><span class="sxs-lookup"><span data-stu-id="d2f4c-189">Step 6: Update the generated document instance</span></span>  
  
1.  <span data-ttu-id="d2f4c-190">（運作方式 [記事本]），在文字編輯器中開啟產生的文件執行個體，然後編輯文件執行個體，以確保資料會在 TIBCO 系統中產生唯一的記錄內容。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-190">Open the generated document instance in a text editor(Notepad works), and edit the contents of the document instance to ensure that the data will generate a unique record in the TIBCO system.</span></span> <span data-ttu-id="d2f4c-191">例如，下列程式碼會顯示資料檔案的第一個部分：</span><span class="sxs-lookup"><span data-stu-id="d2f4c-191">For example, the follow code shows the first part of the data file:</span></span>  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoRendezvousOneWaySend.TibcoRendezvousOneWaySendSchema">  
        <Name>Punya Palit</Name>  
        <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  <span data-ttu-id="d2f4c-192">儲存已修改的文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-192">Save the modified document instance.</span></span>  
  
## <a name="step-7-build-and-deploy-the-project"></a><span data-ttu-id="d2f4c-193">步驟 7： 建置並部署專案</span><span class="sxs-lookup"><span data-stu-id="d2f4c-193">Step 7: Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="d2f4c-194">以滑鼠右鍵按一下**OneWaySend**專案在 [方案總管]，然後按一下**屬性**啟動專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-194">Right-click the **OneWaySend** project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="d2f4c-195">按一下**部署** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-195">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="d2f4c-196">輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-196">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="d2f4c-197">以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-197">Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
## <a name="step-8-bind-enlist-and-start-the-orchestration"></a><span data-ttu-id="d2f4c-198">步驟 8： 繫結、 登錄和啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="d2f4c-198">Step 8: Bind, enlist, and start the orchestration</span></span>  
  
1.  <span data-ttu-id="d2f4c-199">在**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，依序展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-199">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="d2f4c-200">按一下**重新整理**中 MMC 工具列或按下按鈕**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-200">Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="d2f4c-201">按兩下協調流程以顯示**協調流程屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-201">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="d2f4c-202">按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-202">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="d2f4c-203">指定適當的繫結選項值，例如：</span><span class="sxs-lookup"><span data-stu-id="d2f4c-203">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="d2f4c-204">**參數**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-204">**Parameter**</span></span>|<span data-ttu-id="d2f4c-205">**值**</span><span class="sxs-lookup"><span data-stu-id="d2f4c-205">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="d2f4c-206">Host</span><span class="sxs-lookup"><span data-stu-id="d2f4c-206">Host</span></span>|<span data-ttu-id="d2f4c-207">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="d2f4c-207">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="d2f4c-208">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="d2f4c-208">FileReceivePort</span></span>|<span data-ttu-id="d2f4c-209">TIBCORndOneWayFileRP</span><span class="sxs-lookup"><span data-stu-id="d2f4c-209">TIBCORndOneWayFileRP</span></span>|  
    |<span data-ttu-id="d2f4c-210">TibcoRendezvousSend</span><span class="sxs-lookup"><span data-stu-id="d2f4c-210">TibcoRendezvousSend</span></span>|<span data-ttu-id="d2f4c-211">TIBCORndOneWaySP</span><span class="sxs-lookup"><span data-stu-id="d2f4c-211">TIBCORndOneWaySP</span></span>|  
  
6.  <span data-ttu-id="d2f4c-212">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-212">Click OK.</span></span>  
  
7. <span data-ttu-id="d2f4c-213">以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-213">Right-click the orchestration, and click **Start** to enlist and start the orchestration.</span></span>  
  
## <a name="step-9-drop-a-document-and-check-the-tibco-system"></a><span data-ttu-id="d2f4c-214">步驟 9： 卸除文件，並檢查 TIBCO 系統</span><span class="sxs-lookup"><span data-stu-id="d2f4c-214">Step 9: Drop a document, and check the TIBCO system</span></span>
  
-   <span data-ttu-id="d2f4c-215">將稍早建立的文件執行個體複製到應用程式所監視的檔案接收資料夾。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-215">Copy the document instance that was created earlier to the file receive folder the application monitors.</span></span>  
  
-   <span data-ttu-id="d2f4c-216">使用 TIBCO Web 介面，確認已從 XML 檔案中的資料建立記錄。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-216">Use the TIBCO web interface to verify that the record was created from the data in the XML file.</span></span>  
  

<span data-ttu-id="d2f4c-217">如果文件執行個體處理成功，則會發生以下一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="d2f4c-217">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="d2f4c-218">檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-218">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="d2f4c-219">協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程執行個體，然後將訊息傳送至這個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-219">The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="d2f4c-220">協調流程執行個體使用指定的協調流程中的邏輯處理訊息，並將訊息發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-220">The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="d2f4c-221">TIBCO 傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會將訊息傳送至 TIBCO 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-221">The TIBCO send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the TIBCO send port.</span></span>  
  
5.  <span data-ttu-id="d2f4c-222">傳送埠將訊息交給 BizTalk Adapter for TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-222">The send port hands the message to the BizTalk Adapter for TIBCO Rendezvous.</span></span>  
  
6.  <span data-ttu-id="d2f4c-223">BizTalk Adapter for TIBCO Rendezvous 將訊息傳送至 TIBCO 系統。</span><span class="sxs-lookup"><span data-stu-id="d2f4c-223">The BizTalk Adapter for TIBCO Rendezvous sends the message to the TIBCO system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f4c-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f4c-224">See Also</span></span>  
 <span data-ttu-id="d2f4c-225">[教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 接收資料](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md) </span><span class="sxs-lookup"><span data-stu-id="d2f4c-225">[Tutorial: Use the BizTalk Adapter for TIBCO Rendezvous to Receive Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md) </span></span>  
 <span data-ttu-id="d2f4c-226">[教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="d2f4c-226">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="d2f4c-227">快速入門</span><span class="sxs-lookup"><span data-stu-id="d2f4c-227">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)