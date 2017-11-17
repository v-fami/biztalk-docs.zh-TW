---
title: "教學課程： 使用 TIBCO Rendezvous 配接器接收 |Microsoft 文件"
description: "使用 BizTalk Adapter for TIBCO Rendezvous 在 BizTalk Server 中，以接收來自 TIBCO 系統資料的逐步指南"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58e7a739-701d-4085-a840-54f81c55e943
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75aaba0cc2e455676e78381c04934dda30741a85
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data"></a><span data-ttu-id="b17cd-103">教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 接收資料</span><span class="sxs-lookup"><span data-stu-id="b17cd-103">Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Receive Data</span></span>
<span data-ttu-id="b17cd-104">您可以使用 BizTalk Adapter for TIBCO Rendezvous 接收來自 TIBCO 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="b17cd-104">You can use the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system.</span></span> <span data-ttu-id="b17cd-105">這個逐步解說將說明示範這一點的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="b17cd-105">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b17cd-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="b17cd-106">Prerequisites</span></span>  
  
<span data-ttu-id="b17cd-107">在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。</span><span class="sxs-lookup"><span data-stu-id="b17cd-107">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
## <a name="about-the-sample"></a><span data-ttu-id="b17cd-108">關於範例</span><span class="sxs-lookup"><span data-stu-id="b17cd-108">About the sample</span></span> 
- <span data-ttu-id="b17cd-109">這個範例會使用 BizTalk Adapter for TIBCO Rendezvous 接收來自 TIBCO 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="b17cd-109">This sample uses the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system.</span></span> <span data-ttu-id="b17cd-110">協調流程處理訊息，並使用 file 配接器，將資料寫入為 XML 檔案中指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b17cd-110">An orchestration processes the message and, using the file adapter, writes the data as an XML file in a specified folder.</span></span>  
  
- <span data-ttu-id="b17cd-111">以 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 設計的這個範例，示範了將 BizTalk Adapter for TIBCO Enterprise Message Service 與 BizTalk 協調流程搭配使用的基本功能。</span><span class="sxs-lookup"><span data-stu-id="b17cd-111">This sample, designed in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b17cd-112">此範例假設您已知道如何傳送來自 TIBCO 的訊息以讓應用程式處理。</span><span class="sxs-lookup"><span data-stu-id="b17cd-112">The sample assumes that you know how to send a message from TIBCO for the application to process.</span></span>  
  
- <span data-ttu-id="b17cd-113">此範例的預設位置是`C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive`，並包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="b17cd-113">The default location for the sample is `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive`, and includes the following files:</span></span> 
  
    |<span data-ttu-id="b17cd-114">**執行階段專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="b17cd-114">**Runtime Project Filename**</span></span>|<span data-ttu-id="b17cd-115">**執行階段專案檔案描述**</span><span class="sxs-lookup"><span data-stu-id="b17cd-115">**Runtime Project File Description**</span></span>|  
    |---|---|  
    |<span data-ttu-id="b17cd-116">OneWayReceive.btproj、</span><span class="sxs-lookup"><span data-stu-id="b17cd-116">OneWayReceive.btproj,</span></span><br /><br /> <span data-ttu-id="b17cd-117">OneWayReceive.sln</span><span class="sxs-lookup"><span data-stu-id="b17cd-117">OneWayReceive.sln</span></span>|<span data-ttu-id="b17cd-118">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="b17cd-118">Project and solution files for the application.</span></span>|  
    |<span data-ttu-id="b17cd-119">PureMessage.xsd，</span><span class="sxs-lookup"><span data-stu-id="b17cd-119">PureMessage.xsd,</span></span>|<span data-ttu-id="b17cd-120">這個應用程式的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="b17cd-120">Schema file for the application.</span></span>|  
    |<span data-ttu-id="b17cd-121">TIBCORvOWR.odx</span><span class="sxs-lookup"><span data-stu-id="b17cd-121">TIBCORvOWR.odx</span></span>|<span data-ttu-id="b17cd-122">這個應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="b17cd-122">The orchestration used by the application.</span></span>|  
    |<span data-ttu-id="b17cd-123">TIBCORv.snk</span><span class="sxs-lookup"><span data-stu-id="b17cd-123">TIBCORv.snk</span></span>|<span data-ttu-id="b17cd-124">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="b17cd-124">The strong naming key file.</span></span>|  
  
  
## <a name="step-1-add-the-adapter-to-biztalk-administration"></a><span data-ttu-id="b17cd-125">步驟 1： 加入 BizTalk 管理配接器</span><span class="sxs-lookup"><span data-stu-id="b17cd-125">Step 1: Add the adapter to BizTalk Administration</span></span>
  
1.  <span data-ttu-id="b17cd-126">在**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-126">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="b17cd-127">以滑鼠右鍵按一下**配接器**指向**新增**，**配接器...**</span><span class="sxs-lookup"><span data-stu-id="b17cd-127">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="b17cd-128">若要顯示**配接器屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b17cd-128">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="b17cd-129">輸入一個值**名稱**欄位，例如**TIBCO Rendezvous**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-129">Enter a value for the **Name** field, for example **TIBCO Rendezvous**.</span></span>  
  
5.  <span data-ttu-id="b17cd-130">選取**TIBCO(r) 器**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-130">Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
## <a name="step-2-create-a-receive-port"></a><span data-ttu-id="b17cd-131">步驟 2： 建立接收埠</span><span class="sxs-lookup"><span data-stu-id="b17cd-131">Step 2: Create a Receive Port</span></span>  
  
1.  <span data-ttu-id="b17cd-132">在**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，依序展開**BizTalk Application 1**，然後按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-132">In  **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="b17cd-133">以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠...**顯示**接收埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b17cd-133">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the **Receive Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="b17cd-134">輸入一個值**名稱**欄位，例如**TIBCORvOneWayRP**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-134">Enter a value for the **Name** field, for example **TIBCORvOneWayRP**, and click **OK**.</span></span>  
  
## <a name="step-3-create-a-receive-location"></a><span data-ttu-id="b17cd-135">步驟 3： 建立接收位置</span><span class="sxs-lookup"><span data-stu-id="b17cd-135">Step 3: Create a Receive Location</span></span>  
  
1.  <span data-ttu-id="b17cd-136">以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置...**</span><span class="sxs-lookup"><span data-stu-id="b17cd-136">Right-click the new receive port and then click **New**, **Receive Location…**</span></span> <span data-ttu-id="b17cd-137">若要顯示**接收位置屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b17cd-137">to display the **Receive Location Properties** dialog.</span></span>  
  
2.  <span data-ttu-id="b17cd-138">輸入一個值**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="b17cd-138">Enter a value for the **Name** field.</span></span> <span data-ttu-id="b17cd-139">例如，輸入**TIBCORvOneWayRL**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-139">For example, enter **TIBCORvOneWayRL**.</span></span>  
  
3.  <span data-ttu-id="b17cd-140">從使用中的配接器清單選取 TIBCO Rendezvous 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**的傳輸屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b17cd-140">Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b17cd-141">這個值是在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中建立 TIBCO 配接器時指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="b17cd-141">This value is the name that was specified when the TIBCO adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="b17cd-142">輸入一個值**RendezvousSubjectName**下**AdapterRequiredProperties**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-142">Enter a value for the **RendezvousSubjectName** under the **AdapterRequiredProperties**.</span></span>  
  
5.  <span data-ttu-id="b17cd-143">輸入的值**認證接聽程式屬性**:</span><span class="sxs-lookup"><span data-stu-id="b17cd-143">Enter values for the **Certified Listener Properties**:</span></span>  
  
    |<span data-ttu-id="b17cd-144">**屬性**</span><span class="sxs-lookup"><span data-stu-id="b17cd-144">**Property**</span></span>|<span data-ttu-id="b17cd-145">**值**</span><span class="sxs-lookup"><span data-stu-id="b17cd-145">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="b17cd-146">分類帳檔案名稱</span><span class="sxs-lookup"><span data-stu-id="b17cd-146">Ledger file name</span></span>|<span data-ttu-id="b17cd-147">要用於永續性認證訊息傳遞的分類帳檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b17cd-147">Ledger file name to use for persistent certified message delivery.</span></span>|  
    |<span data-ttu-id="b17cd-148">可重複使用的名稱</span><span class="sxs-lookup"><span data-stu-id="b17cd-148">Reusable name</span></span>|<span data-ttu-id="b17cd-149">要用於認證訊息傳遞的可重複使用對應名稱。</span><span class="sxs-lookup"><span data-stu-id="b17cd-149">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="b17cd-150">在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="b17cd-150">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
6.  <span data-ttu-id="b17cd-151">輸入的值**認證**:</span><span class="sxs-lookup"><span data-stu-id="b17cd-151">Enter values for the **Credentials**:</span></span>  
  
    |<span data-ttu-id="b17cd-152">**屬性**</span><span class="sxs-lookup"><span data-stu-id="b17cd-152">**Property**</span></span>|<span data-ttu-id="b17cd-153">**值**</span><span class="sxs-lookup"><span data-stu-id="b17cd-153">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="b17cd-154">密碼</span><span class="sxs-lookup"><span data-stu-id="b17cd-154">Password</span></span>|<span data-ttu-id="b17cd-155">TIBCO Rendezvous 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="b17cd-155">The password for the TIBCO Rendezvous server.</span></span>|  
    |<span data-ttu-id="b17cd-156">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="b17cd-156">User name</span></span>|<span data-ttu-id="b17cd-157">TIBCO Rendezvous 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b17cd-157">The user name for the TIBCO Rendezvous server.</span></span>|  
  
7.  <span data-ttu-id="b17cd-158">輸入的值**RendezvousTransport**:</span><span class="sxs-lookup"><span data-stu-id="b17cd-158">Enter values for the **RendezvousTransport**:</span></span>  
  
    |<span data-ttu-id="b17cd-159">**屬性**</span><span class="sxs-lookup"><span data-stu-id="b17cd-159">**Property**</span></span>|<span data-ttu-id="b17cd-160">**值**</span><span class="sxs-lookup"><span data-stu-id="b17cd-160">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="b17cd-161">精靈</span><span class="sxs-lookup"><span data-stu-id="b17cd-161">Daemon</span></span>|<span data-ttu-id="b17cd-162">Rendezvous 傳輸精靈參數。</span><span class="sxs-lookup"><span data-stu-id="b17cd-162">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="b17cd-163">網路</span><span class="sxs-lookup"><span data-stu-id="b17cd-163">Network</span></span>|<span data-ttu-id="b17cd-164">Rendezvous 傳輸網路參數。</span><span class="sxs-lookup"><span data-stu-id="b17cd-164">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="b17cd-165">服務</span><span class="sxs-lookup"><span data-stu-id="b17cd-165">Service</span></span>|<span data-ttu-id="b17cd-166">Rendezvous 傳輸服務參數。</span><span class="sxs-lookup"><span data-stu-id="b17cd-166">Rendezvous Transport Service parameter.</span></span>|  
  
     <span data-ttu-id="b17cd-167">如需屬性的詳細資訊，請參閱[建立接收成品](../core/creating-tibco-rendezvous-receive-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="b17cd-167">For more information about the properties, see [Create Receive artifacts](../core/creating-tibco-rendezvous-receive-handlers.md).</span></span>  
  
8.  <span data-ttu-id="b17cd-168">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-168">Click **OK**.</span></span>  
  
9. <span data-ttu-id="b17cd-169">選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-169">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
10. <span data-ttu-id="b17cd-170">以滑鼠右鍵按一下接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-170">Right-click the receive location and click **Enable**.</span></span>  
  
## <a name="step-4-create-a-one-way-send-port"></a><span data-ttu-id="b17cd-171">步驟 4： 建立單向傳送埠</span><span class="sxs-lookup"><span data-stu-id="b17cd-171">Step 4: Create a one-way send port</span></span>  
  
1.  <span data-ttu-id="b17cd-172">建立傳送埠所要使用的目標資料夾，例如 C:\FilesOut。</span><span class="sxs-lookup"><span data-stu-id="b17cd-172">Create a target folder to be used by the send port, for example C:\FilesOut.</span></span>  
  
2.  <span data-ttu-id="b17cd-173">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-173">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="b17cd-174">以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠...**</span><span class="sxs-lookup"><span data-stu-id="b17cd-174">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…**</span></span> <span data-ttu-id="b17cd-175">若要顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b17cd-175">to display the **Send Port Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="b17cd-176">輸入一個值**名稱**欄位，例如**TIBCORvOneWayFileSP**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-176">Enter a value for the **Name** field, for example **TIBCORvOneWayFileSP**.</span></span>  
  
5.  <span data-ttu-id="b17cd-177">選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b17cd-177">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
6.  <span data-ttu-id="b17cd-178">如**目的地資料夾**屬性中，輸入您稍早建立的資料夾位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-178">For the **Destination Folder** property, enter the location of the folder that you created earlier and click **OK**.</span></span>  
  
7.  <span data-ttu-id="b17cd-179">選取**XMLTransmit**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-179">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="b17cd-180">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b17cd-180">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
## <a name="step-5-build-and-deploy-the-project"></a><span data-ttu-id="b17cd-181">步驟 5： 建立和部署專案</span><span class="sxs-lookup"><span data-stu-id="b17cd-181">Step 5: Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="b17cd-182">以滑鼠右鍵按一下方案總管 中的 Onewaysend 專案，然後按一下**屬性**啟動專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="b17cd-182">Right-click the OneWayReceive project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="b17cd-183">按一下**部署** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b17cd-183">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="b17cd-184">輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b17cd-184">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.</span></span>  
  
4.  <span data-ttu-id="b17cd-185">以滑鼠右鍵按一下方案總管 中的 Onewaysend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="b17cd-185">Right-click the OneWayReceive project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
## <a name="step-6-bind-enlist-and-start-the-orchestration"></a><span data-ttu-id="b17cd-186">步驟 6： 繫結、 登錄，並啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="b17cd-186">Step 6: Bind, Enlist, and start the orchestration</span></span>  
  
1.  <span data-ttu-id="b17cd-187">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-187">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="b17cd-188">按一下**重新整理**按鈕[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台工具列或按**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。</span><span class="sxs-lookup"><span data-stu-id="b17cd-188">Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="b17cd-189">按兩下協調流程以顯示**協調流程屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b17cd-189">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="b17cd-190">按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="b17cd-190">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="b17cd-191">指定適當的繫結選項值，例如：</span><span class="sxs-lookup"><span data-stu-id="b17cd-191">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="b17cd-192">**參數**</span><span class="sxs-lookup"><span data-stu-id="b17cd-192">**Parameter**</span></span>|<span data-ttu-id="b17cd-193">**值**</span><span class="sxs-lookup"><span data-stu-id="b17cd-193">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="b17cd-194">Host</span><span class="sxs-lookup"><span data-stu-id="b17cd-194">Host</span></span>|<span data-ttu-id="b17cd-195">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="b17cd-195">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="b17cd-196">SendPort</span><span class="sxs-lookup"><span data-stu-id="b17cd-196">SendPort</span></span>|<span data-ttu-id="b17cd-197">TIBCORvOneWayFileSP</span><span class="sxs-lookup"><span data-stu-id="b17cd-197">TIBCORvOneWayFileSP</span></span>|  
    |<span data-ttu-id="b17cd-198">ReceivePort</span><span class="sxs-lookup"><span data-stu-id="b17cd-198">ReceivePort</span></span>|<span data-ttu-id="b17cd-199">TIBCORvOneWayRP</span><span class="sxs-lookup"><span data-stu-id="b17cd-199">TIBCORvOneWayRP</span></span>|  
  
6.  <span data-ttu-id="b17cd-200">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b17cd-200">Click **OK**.</span></span>  
  
7. <span data-ttu-id="b17cd-201">以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="b17cd-201">Right-click the orchestration, and click **Start** to enlist and start the orchestration.</span></span>  
  
## <a name="step-7-confirm-the-application-receives-a-message"></a><span data-ttu-id="b17cd-202">步驟 7： 確認應用程式收到的訊息</span><span class="sxs-lookup"><span data-stu-id="b17cd-202">Step 7: Confirm the application receives a message</span></span>  
  
-   <span data-ttu-id="b17cd-203">開啟檔案傳送埠會設定傳送至，並確認已產生輸出文件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b17cd-203">Open the folder that the file send port is configured to send to, and verify that an output document was generated.</span></span>  
  
 <span data-ttu-id="b17cd-204">如果文件執行個體處理成功，則會發生以下一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="b17cd-204">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="b17cd-205">TIBCO Rendezvous 配接器接收來自 TIBCO 系統的訊息，並以 BizTalk 訊息的形式將其發佈至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="b17cd-205">The TIBCO Rendezvous adapter receives a message from TIBCO system and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="b17cd-206">協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程的執行個體，然後將訊息傳送至這個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="b17cd-206">The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="b17cd-207">協調流程執行個體將訊息發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="b17cd-207">The orchestration instance publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="b17cd-208">檔案傳送埠訂閱這個訊息，因此 BizTalk 會將訊息傳送至檔案配接器。</span><span class="sxs-lookup"><span data-stu-id="b17cd-208">The File send port subscribes to this message so BizTalk sends the message to the File adapter.</span></span>  
  
5.  <span data-ttu-id="b17cd-209">檔案配接器將包含結果集的訊息寫入至指定的輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="b17cd-209">The File adapter writes the message containing the result set to the designated output folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17cd-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b17cd-210">See Also</span></span>  
 <span data-ttu-id="b17cd-211">[教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 來傳送資料](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md) </span><span class="sxs-lookup"><span data-stu-id="b17cd-211">[Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md) </span></span>  
 <span data-ttu-id="b17cd-212">[教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="b17cd-212">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="b17cd-213">快速入門</span><span class="sxs-lookup"><span data-stu-id="b17cd-213">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)