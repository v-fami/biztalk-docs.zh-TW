---
title: "教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 來傳送資料 |Microsoft 文件"
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
ms.openlocfilehash: 63540402ca8e060d26c8398af010a81eaad0a6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data"></a><span data-ttu-id="222d4-102">教學課程：使用 BizTalk Adapter for TIBCO Rendezvous 來傳送資料</span><span class="sxs-lookup"><span data-stu-id="222d4-102">Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data</span></span>
<span data-ttu-id="222d4-103">您可以使用 BizTalk Adapter for TIBCO Rendezvous 將資料傳送至 TIBCO 系統。</span><span class="sxs-lookup"><span data-stu-id="222d4-103">You can use the BizTalk Adapter for TIBCO Rendezvous to send data to a TIBCO system.</span></span> <span data-ttu-id="222d4-104">這個逐步解說將說明示範這一點的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="222d4-104">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="222d4-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="222d4-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="222d4-106">在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。</span><span class="sxs-lookup"><span data-stu-id="222d4-106">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
-   <span data-ttu-id="222d4-107">此範例會使用包含訊息內容屬性的 DLL：Microsoft.BizTalk.Adapters.TibRV.Properties.dll。</span><span class="sxs-lookup"><span data-stu-id="222d4-107">The sample uses a DLL containing message context properties: Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span></span> <span data-ttu-id="222d4-108">您可能需要更新方案對這個程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="222d4-108">You may need to update the solution's reference to this library.</span></span> <span data-ttu-id="222d4-109">如需詳細資訊，請參閱[BizTalk Server 訊息內容屬性 （傳送處理常式）](../core/biztalk-server-message-context-properties-send-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="222d4-109">For more information, see [BizTalk Server Message Context Properties (Send Handlers)](../core/biztalk-server-message-context-properties-send-handlers.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="222d4-110">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="222d4-110">What This Sample Does</span></span>  
 <span data-ttu-id="222d4-111">此範例會從某個檔案資料夾收取某個 XML 檔案、將該檔案傳送至協調流程，然後使用 BizTalk Adapter for TIBCO Rendezvous 在 TIBCO 系統中建立一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="222d4-111">This sample picks up an XML file from a file folder, sends the file to an orchestration, and then uses the BizTalk Adapter for TIBCO Rendezvous to create a record in the TIBCO system.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="222d4-112">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="222d4-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="222d4-113">以 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 設計的這個範例，示範了將 BizTalk Adapter for TIBCO Rendezvous 與 BizTalk 協調流程搭配使用的基本功能。</span><span class="sxs-lookup"><span data-stu-id="222d4-113">This sample, designed in [!INCLUDE[vs2010](../includes/vs2010-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Rendezvous with a BizTalk orchestration.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="222d4-114">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="222d4-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="222d4-115">此範例的預設位置是</span><span class="sxs-lookup"><span data-stu-id="222d4-115">The default location for the sample is</span></span>  
  
 <span data-ttu-id="222d4-116">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend</span><span class="sxs-lookup"><span data-stu-id="222d4-116">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend</span></span>  
  
 <span data-ttu-id="222d4-117">下表列出此範例中的檔案並提供描述。</span><span class="sxs-lookup"><span data-stu-id="222d4-117">The following table lists and describes the files in the sample.</span></span>  
  
|<span data-ttu-id="222d4-118">**執行階段專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="222d4-118">**Runtime Project Filename**</span></span>|<span data-ttu-id="222d4-119">**執行階段專案檔案描述**</span><span class="sxs-lookup"><span data-stu-id="222d4-119">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="222d4-120">OneWaySend.btproj</span><span class="sxs-lookup"><span data-stu-id="222d4-120">OneWaySend.btproj</span></span><br /><br /> <span data-ttu-id="222d4-121">OneWaySend.sln</span><span class="sxs-lookup"><span data-stu-id="222d4-121">OneWaySend.sln</span></span>|<span data-ttu-id="222d4-122">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="222d4-122">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="222d4-123">Schema.xsd</span><span class="sxs-lookup"><span data-stu-id="222d4-123">Schema.xsd</span></span><br /><br /> <span data-ttu-id="222d4-124">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="222d4-124">PropertySchema.xsd</span></span>|<span data-ttu-id="222d4-125">這個應用程式的結構描述和屬性結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="222d4-125">Schema and property schema files for the application.</span></span>|  
|<span data-ttu-id="222d4-126">Orchestration.odx</span><span class="sxs-lookup"><span data-stu-id="222d4-126">Orchestration.odx</span></span>|<span data-ttu-id="222d4-127">這個應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="222d4-127">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="222d4-128">TIBCORendezvousOneWaySend.snk</span><span class="sxs-lookup"><span data-stu-id="222d4-128">TIBCORendezvousOneWaySend.snk</span></span>|<span data-ttu-id="222d4-129">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="222d4-129">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="222d4-130">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="222d4-130">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="222d4-131">建立新的 BizTalk Adapter for TIBCO Rendezvous 執行個體</span><span class="sxs-lookup"><span data-stu-id="222d4-131">Create a new instance of the BizTalk Adapter for TIBCO Rendezvous</span></span>  
  
1.  <span data-ttu-id="222d4-132">啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="222d4-132">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="222d4-133">按一下**啟動**，**程式**， **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]， **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="222d4-133">Click **Start**, **Programs**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="222d4-134">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="222d4-134">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="222d4-135">以滑鼠右鍵按一下**配接器**指向**新增**，**配接器...**</span><span class="sxs-lookup"><span data-stu-id="222d4-135">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="222d4-136">若要顯示**配接器屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="222d4-136">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="222d4-137">輸入一個值**名稱**欄位，例如**TIBCO Rendezvous**。</span><span class="sxs-lookup"><span data-stu-id="222d4-137">Enter a value for the **Name** field, for example **TIBCO Rendezvous**.</span></span>  
  
5.  <span data-ttu-id="222d4-138">選取**TIBCO(r) 器**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="222d4-138">Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-send-port"></a><span data-ttu-id="222d4-139">建立 BizTalk 傳送埠</span><span class="sxs-lookup"><span data-stu-id="222d4-139">Create a BizTalk Send Port</span></span>  
  
1.  <span data-ttu-id="222d4-140">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="222d4-140">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="222d4-141">以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠...**</span><span class="sxs-lookup"><span data-stu-id="222d4-141">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…**</span></span> <span data-ttu-id="222d4-142">若要顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="222d4-142">to display the **Send Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="222d4-143">輸入一個值**名稱**欄位，例如**TIBCORndOneWaySP**。</span><span class="sxs-lookup"><span data-stu-id="222d4-143">Enter a value for the **Name** field, for example **TIBCORndOneWaySP**.</span></span>  
  
4.  <span data-ttu-id="222d4-144">從使用中的配接器清單選取 TIBCO Rendezvous 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**的傳輸屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="222d4-144">Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="222d4-145">這個值是在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中建立 TIBCO Enterprise Message System 配接器時指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="222d4-145">This value is the name that was specified when the TIBCO Enterprise Message System adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
5.  <span data-ttu-id="222d4-146">輸入的值**認證寄件者屬性**:</span><span class="sxs-lookup"><span data-stu-id="222d4-146">Enter values for the **Certified Sender Properties**:</span></span>  
  
    |<span data-ttu-id="222d4-147">**屬性**</span><span class="sxs-lookup"><span data-stu-id="222d4-147">**Property**</span></span>|<span data-ttu-id="222d4-148">**值**</span><span class="sxs-lookup"><span data-stu-id="222d4-148">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="222d4-149">分類帳檔案名稱</span><span class="sxs-lookup"><span data-stu-id="222d4-149">Ledger file name</span></span>|<span data-ttu-id="222d4-150">要用於永續性認證訊息傳遞的分類帳檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="222d4-150">Ledger file name to use for persistent certified message delivery.</span></span>|  
    |<span data-ttu-id="222d4-151">可重複使用的名稱</span><span class="sxs-lookup"><span data-stu-id="222d4-151">Reusable name</span></span>|<span data-ttu-id="222d4-152">要用於認證訊息傳遞的可重複使用對應名稱。</span><span class="sxs-lookup"><span data-stu-id="222d4-152">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="222d4-153">在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="222d4-153">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
6.  <span data-ttu-id="222d4-154">輸入的值**認證**:</span><span class="sxs-lookup"><span data-stu-id="222d4-154">Enter values for the **Credentials**:</span></span>  
  
    |<span data-ttu-id="222d4-155">**屬性**</span><span class="sxs-lookup"><span data-stu-id="222d4-155">**Property**</span></span>|<span data-ttu-id="222d4-156">**值**</span><span class="sxs-lookup"><span data-stu-id="222d4-156">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="222d4-157">密碼</span><span class="sxs-lookup"><span data-stu-id="222d4-157">Password</span></span>|<span data-ttu-id="222d4-158">TIBCO Rendezvous 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="222d4-158">The password for the TIBCO Rendezvous server.</span></span>|  
    |<span data-ttu-id="222d4-159">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="222d4-159">User name</span></span>|<span data-ttu-id="222d4-160">TIBCO Rendezvous 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="222d4-160">The user name for the TIBCO Rendezvous server.</span></span>|  
  
7.  <span data-ttu-id="222d4-161">輸入的值**RendezvousTransport**:</span><span class="sxs-lookup"><span data-stu-id="222d4-161">Enter values for the **RendezvousTransport**:</span></span>  
  
    |<span data-ttu-id="222d4-162">**屬性**</span><span class="sxs-lookup"><span data-stu-id="222d4-162">**Property**</span></span>|<span data-ttu-id="222d4-163">**值**</span><span class="sxs-lookup"><span data-stu-id="222d4-163">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="222d4-164">精靈</span><span class="sxs-lookup"><span data-stu-id="222d4-164">Daemon</span></span>|<span data-ttu-id="222d4-165">Rendezvous 傳輸精靈參數。</span><span class="sxs-lookup"><span data-stu-id="222d4-165">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="222d4-166">網路</span><span class="sxs-lookup"><span data-stu-id="222d4-166">Network</span></span>|<span data-ttu-id="222d4-167">Rendezvous 傳輸網路參數。</span><span class="sxs-lookup"><span data-stu-id="222d4-167">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="222d4-168">服務</span><span class="sxs-lookup"><span data-stu-id="222d4-168">Service</span></span>|<span data-ttu-id="222d4-169">Rendezvous 傳輸服務參數。</span><span class="sxs-lookup"><span data-stu-id="222d4-169">Rendezvous Transport Service parameter.</span></span>|  
  
     <span data-ttu-id="222d4-170">如需屬性的詳細資訊，請參閱[如何設定 TIBCO Rendezvous 傳輸屬性](../core/how-to-set-tibco-rendezvous-transport-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="222d4-170">For more information about the properties, see [How to Set TIBCO Rendezvous Transport Properties](../core/how-to-set-tibco-rendezvous-transport-properties.md).</span></span>  
  
8.  <span data-ttu-id="222d4-171">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="222d4-171">Click **OK**.</span></span>  
  
9. <span data-ttu-id="222d4-172">選取**XML 傳輸**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="222d4-172">Select the **XML Transmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
10. <span data-ttu-id="222d4-173">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="222d4-173">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="create-a-file-receive-port"></a><span data-ttu-id="222d4-174">建立檔案接收埠</span><span class="sxs-lookup"><span data-stu-id="222d4-174">Create a file receive port</span></span>  
  
1.  <span data-ttu-id="222d4-175">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="222d4-175">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="222d4-176">以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠...**以顯示 [接收埠屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="222d4-176">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the Receive Port Properties dialog.</span></span>  
  
3.  <span data-ttu-id="222d4-177">輸入一個值**名稱**欄位，例如**TIBCORndOneWayFileRP**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="222d4-177">Enter a value for the **Name** field, for example **TIBCORndOneWayFileRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-file-receive-location"></a><span data-ttu-id="222d4-178">建立檔案接收位置</span><span class="sxs-lookup"><span data-stu-id="222d4-178">Create a file receive location</span></span>  
  
1.  <span data-ttu-id="222d4-179">為檔案接收位置建立一個資料夾來監視，例如 C:\Filesource。</span><span class="sxs-lookup"><span data-stu-id="222d4-179">Create a folder for the file receive location to monitor, for example C:\Filesource.</span></span>  
  
2.  <span data-ttu-id="222d4-180">以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置...**</span><span class="sxs-lookup"><span data-stu-id="222d4-180">Right-click the new receive port and then click **New**, **Receive Location…**</span></span> <span data-ttu-id="222d4-181">若要顯示**接收位置屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="222d4-181">to display the **Receive Location Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="222d4-182">輸入一個值**名稱**欄位，例如**TIBCORndOneWayFileRL**。</span><span class="sxs-lookup"><span data-stu-id="222d4-182">Enter a value for the **Name** field, for example **TIBCORndOneWayFileRL**.</span></span>  
  
4.  <span data-ttu-id="222d4-183">選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="222d4-183">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="222d4-184">輸入您稍早建立的資料夾位置**接收資料夾**屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="222d4-184">Enter the location of the folder that you created earlier for the **Receive Folder** property and click **OK**.</span></span>  
  
6.  <span data-ttu-id="222d4-185">選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="222d4-185">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="222d4-186">以滑鼠右鍵按一下接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="222d4-186">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="generate-a-document-instance-from-the-schema"></a><span data-ttu-id="222d4-187">從結構描述產生文件執行個體</span><span class="sxs-lookup"><span data-stu-id="222d4-187">Generate a document instance from the schema</span></span>  
  
1.  <span data-ttu-id="222d4-188">以滑鼠右鍵按一下方案總管 中的 Schema.xsd，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="222d4-188">Right-click Schema.xsd in Solution Explorer and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="222d4-189">在 [屬性] 視窗中，按一下以選取**輸出執行個體檔案名稱**選項在**一般**> 一節。</span><span class="sxs-lookup"><span data-stu-id="222d4-189">In the Properties window, click to select the **Output Instance Filename** option under the **General** section.</span></span>  
  
3.  <span data-ttu-id="222d4-190">按一下省略符號按鈕 （…） 以顯示**選取輸出檔案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="222d4-190">Click the ellipses button (…) to display the **Select Output File** dialog.</span></span>  
  
4.  <span data-ttu-id="222d4-191">指定的資料夾和輸出檔案執行個體名稱，例如**C:\instance.xml**按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="222d4-191">Specify a folder and name for the output file instance, for example **C:\instance.xml** and click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="222d4-192">請勿在這裡指定剛才針對檔案接收位置指定的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="222d4-192">Do not specify the location of the folder that was specified for the file receive location here.</span></span>  
  
5.  <span data-ttu-id="222d4-193">以滑鼠右鍵按一下方案總管 中的 Schema.xsd，然後按一下**產生執行個體**產生文件執行個體中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="222d4-193">Right-click Schema.xsd in Solution Explorer and click **Generate Instance** to generate a document instance in the specified location.</span></span>  
  
#### <a name="modify-the-generated-document-instance"></a><span data-ttu-id="222d4-194">修改產生的文件執行個體</span><span class="sxs-lookup"><span data-stu-id="222d4-194">Modify the generated document instance</span></span>  
  
1.  <span data-ttu-id="222d4-195">在文字編輯器 (如 [記事本]) 中開啟產生的文件執行個體，然後編輯文件執行個體的內容，以確保資料會在 TIBCO 系統中產生唯一的記錄。</span><span class="sxs-lookup"><span data-stu-id="222d4-195">Open the generated document instance in a text editor such as Notepad and edit the contents of the document instance to ensure that the data will generate a unique record in the TIBCO system.</span></span> <span data-ttu-id="222d4-196">例如，下列程式碼顯示這個資料檔案的第一個部分：</span><span class="sxs-lookup"><span data-stu-id="222d4-196">For example the code below shows the first part of the data file:</span></span>  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoRendezvousOneWaySend.TibcoRendezvousOneWaySendSchema">  
        <Name>Punya Palit</Name>  
        <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  <span data-ttu-id="222d4-197">儲存已修改的文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="222d4-197">Save the modified document instance.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="222d4-198">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="222d4-198">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="222d4-199">以滑鼠右鍵按一下**OneWaySend**專案在 [方案總管]，然後按一下**屬性**啟動專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="222d4-199">Right-click the **OneWaySend** project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="222d4-200">按一下**部署** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="222d4-200">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="222d4-201">輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="222d4-201">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="222d4-202">以滑鼠右鍵按一下方案總管 中的 OneWaySend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="222d4-202">Right-click the OneWaySend project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="222d4-203">繫結和登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="222d4-203">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="222d4-204">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="222d4-204">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="222d4-205">按一下**重新整理**中 MMC 工具列或按下按鈕**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。</span><span class="sxs-lookup"><span data-stu-id="222d4-205">Click the **Refresh** button in the MMC toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="222d4-206">按兩下協調流程以顯示**協調流程屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="222d4-206">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="222d4-207">按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="222d4-207">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="222d4-208">指定適當的繫結選項值，例如：</span><span class="sxs-lookup"><span data-stu-id="222d4-208">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="222d4-209">**參數**</span><span class="sxs-lookup"><span data-stu-id="222d4-209">**Parameter**</span></span>|<span data-ttu-id="222d4-210">**值**</span><span class="sxs-lookup"><span data-stu-id="222d4-210">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="222d4-211">Host</span><span class="sxs-lookup"><span data-stu-id="222d4-211">Host</span></span>|<span data-ttu-id="222d4-212">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="222d4-212">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="222d4-213">FileReceivePort</span><span class="sxs-lookup"><span data-stu-id="222d4-213">FileReceivePort</span></span>|<span data-ttu-id="222d4-214">TIBCORndOneWayFileRP</span><span class="sxs-lookup"><span data-stu-id="222d4-214">TIBCORndOneWayFileRP</span></span>|  
    |<span data-ttu-id="222d4-215">TibcoRendezvousSend</span><span class="sxs-lookup"><span data-stu-id="222d4-215">TibcoRendezvousSend</span></span>|<span data-ttu-id="222d4-216">TIBCORndOneWaySP</span><span class="sxs-lookup"><span data-stu-id="222d4-216">TIBCORndOneWaySP</span></span>|  
  
6.  <span data-ttu-id="222d4-217">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="222d4-217">Click OK.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="222d4-218">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="222d4-218">Start the orchestration</span></span>  
  
-   <span data-ttu-id="222d4-219">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="222d4-219">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a><span data-ttu-id="222d4-220">將文件執行個體拖放到檔案接收位置所監視的資料夾</span><span class="sxs-lookup"><span data-stu-id="222d4-220">Drop a document instance into the folder monitored by the file receive location</span></span>  
  
-   <span data-ttu-id="222d4-221">將稍早建立的文件執行個體複製到應用程式所監視的檔案接收資料夾。</span><span class="sxs-lookup"><span data-stu-id="222d4-221">Copy the document instance that was created earlier to the file receive folder the application monitors.</span></span>  
  
#### <a name="verify-that-the-tibco-system-is-updated"></a><span data-ttu-id="222d4-222">確認 TIBCO 系統已更新</span><span class="sxs-lookup"><span data-stu-id="222d4-222">Verify that the TIBCO system is updated</span></span>  
  
-   <span data-ttu-id="222d4-223">使用 TIBCO Web 介面，確認已從 XML 檔案中的資料建立記錄。</span><span class="sxs-lookup"><span data-stu-id="222d4-223">Use the TIBCO web interface to verify that the record was created from the data in the XML file.</span></span>  
  
 <span data-ttu-id="222d4-224">如果文件執行個體處理成功，則會發生以下一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="222d4-224">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="222d4-225">檔案配接器從資料夾擷取到檔案，並將其發佈到 MessageBox 做為 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="222d4-225">The File adapter retrieves the file from the folder and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="222d4-226">協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程執行個體，然後將訊息傳送至這個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="222d4-226">The orchestration subscribes to this published message so the BizTalk Messaging Engine will activate an instance of the orchestration and send the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="222d4-227">協調流程執行個體使用指定的協調流程中的邏輯處理訊息，並將訊息發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="222d4-227">The orchestration instance processes the message using the logic specified in the orchestration and publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="222d4-228">TIBCO 傳送埠訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會將訊息傳送至 TIBCO 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="222d4-228">The TIBCO send port subscribes to this published message and so the BizTalk Messaging Engine sends the message to the TIBCO send port.</span></span>  
  
5.  <span data-ttu-id="222d4-229">傳送埠將訊息交給 BizTalk Adapter for TIBCO Rendezvous。</span><span class="sxs-lookup"><span data-stu-id="222d4-229">The send port hands the message to the BizTalk Adapter for TIBCO Rendezvous.</span></span>  
  
6.  <span data-ttu-id="222d4-230">BizTalk Adapter for TIBCO Rendezvous 將訊息傳送至 TIBCO 系統。</span><span class="sxs-lookup"><span data-stu-id="222d4-230">The BizTalk Adapter for TIBCO Rendezvous sends the message to the TIBCO system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222d4-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="222d4-231">See Also</span></span>  
 <span data-ttu-id="222d4-232">[教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 接收資料](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md) </span><span class="sxs-lookup"><span data-stu-id="222d4-232">[Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Receive Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md) </span></span>  
 <span data-ttu-id="222d4-233">[教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="222d4-233">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="222d4-234">快速入門</span><span class="sxs-lookup"><span data-stu-id="222d4-234">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)