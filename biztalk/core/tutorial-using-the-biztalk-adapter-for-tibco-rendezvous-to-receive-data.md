---
title: "教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 接收資料 |Microsoft 文件"
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
ms.openlocfilehash: de436413f10cf4882b5c4e4b21af7bac6a3234c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data"></a><span data-ttu-id="d9382-102">教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 接收資料</span><span class="sxs-lookup"><span data-stu-id="d9382-102">Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Receive Data</span></span>
<span data-ttu-id="d9382-103">您可以使用 BizTalk Adapter for TIBCO Rendezvous 接收來自 TIBCO 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="d9382-103">You can use the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system.</span></span> <span data-ttu-id="d9382-104">這個逐步解說將說明示範這一點的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="d9382-104">This walkthrough describes an SDK sample that illustrates this.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d9382-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="d9382-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="d9382-106">在執行配接器的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便建置及部署範例。</span><span class="sxs-lookup"><span data-stu-id="d9382-106">Install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that the adapter is running on in order to build and deploy the sample.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="d9382-107">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="d9382-107">What This Sample Does</span></span>  
 <span data-ttu-id="d9382-108">這個範例會使用 BizTalk Adapter for TIBCO Rendezvous 接收來自 TIBCO 系統的資料。</span><span class="sxs-lookup"><span data-stu-id="d9382-108">This sample uses the BizTalk Adapter for TIBCO Rendezvous to receive data from a TIBCO system.</span></span> <span data-ttu-id="d9382-109">協調流程處理訊息，並使用 file 配接器，將資料寫入為 XML 檔案中指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d9382-109">An orchestration processes the message and, using the file adapter, writes the data as an XML file in a specified folder.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="d9382-110">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="d9382-110">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="d9382-111">以 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 設計的這個範例，示範了將 BizTalk Adapter for TIBCO Enterprise Message Service 與 BizTalk 協調流程搭配使用的基本功能。</span><span class="sxs-lookup"><span data-stu-id="d9382-111">This sample, designed in [!INCLUDE[vs2010](../includes/vs2010-md.md)], illustrates basic functionality using the BizTalk Adapter for TIBCO Enterprise Message Service with a BizTalk orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9382-112">此範例假設您已知道如何傳送來自 TIBCO 的訊息以讓應用程式處理。</span><span class="sxs-lookup"><span data-stu-id="d9382-112">The sample assumes that you know how to send a message from TIBCO for the application to process.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="d9382-113">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="d9382-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="d9382-114">此範例的預設位置是</span><span class="sxs-lookup"><span data-stu-id="d9382-114">The default location for the sample is</span></span>  
  
 <span data-ttu-id="d9382-115">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r) \Sdk\OneWayReceive</span><span class="sxs-lookup"><span data-stu-id="d9382-115">C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive</span></span>  
  
 <span data-ttu-id="d9382-116">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="d9382-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="d9382-117">**執行階段專案檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="d9382-117">**Runtime Project Filename**</span></span>|<span data-ttu-id="d9382-118">**執行階段專案檔案描述**</span><span class="sxs-lookup"><span data-stu-id="d9382-118">**Runtime Project File Description**</span></span>|  
|----------------------------------|------------------------------------------|  
|<span data-ttu-id="d9382-119">OneWayReceive.btproj、</span><span class="sxs-lookup"><span data-stu-id="d9382-119">OneWayReceive.btproj,</span></span><br /><br /> <span data-ttu-id="d9382-120">OneWayReceive.sln</span><span class="sxs-lookup"><span data-stu-id="d9382-120">OneWayReceive.sln</span></span>|<span data-ttu-id="d9382-121">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="d9382-121">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="d9382-122">PureMessage.xsd，</span><span class="sxs-lookup"><span data-stu-id="d9382-122">PureMessage.xsd,</span></span>|<span data-ttu-id="d9382-123">這個應用程式的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="d9382-123">Schema file for the application.</span></span>|  
|<span data-ttu-id="d9382-124">TIBCORvOWR.odx</span><span class="sxs-lookup"><span data-stu-id="d9382-124">TIBCORvOWR.odx</span></span>|<span data-ttu-id="d9382-125">這個應用程式使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="d9382-125">The orchestration used by the application.</span></span>|  
|<span data-ttu-id="d9382-126">TIBCORv.snk</span><span class="sxs-lookup"><span data-stu-id="d9382-126">TIBCORv.snk</span></span>|<span data-ttu-id="d9382-127">強式命名金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="d9382-127">The strong naming key file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="d9382-128">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="d9382-128">How to Use This Sample</span></span>  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="d9382-129">建立新的 BizTalk Adapter for TIBCO Rendezvous 執行個體</span><span class="sxs-lookup"><span data-stu-id="d9382-129">Create a new instance of the BizTalk Adapter for TIBCO Rendezvous</span></span>  
  
1.  <span data-ttu-id="d9382-130">啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="d9382-130">Launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="d9382-131">按一下**啟動**，**所有程式**， [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]， [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d9382-131">Click **Start**, **All Programs**, [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="d9382-132">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **配接器**。</span><span class="sxs-lookup"><span data-stu-id="d9382-132">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="d9382-133">以滑鼠右鍵按一下**配接器**指向**新增**，**配接器...**</span><span class="sxs-lookup"><span data-stu-id="d9382-133">Right-click **Adapters** and point to **New**, **Adapter…**</span></span> <span data-ttu-id="d9382-134">若要顯示**配接器屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9382-134">to display the **Adapter Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="d9382-135">輸入一個值**名稱**欄位，例如**TIBCO Rendezvous**。</span><span class="sxs-lookup"><span data-stu-id="d9382-135">Enter a value for the **Name** field, for example **TIBCO Rendezvous**.</span></span>  
  
5.  <span data-ttu-id="d9382-136">選取**TIBCO(r) 器**從清單中可用的介面卡**配接器**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d9382-136">Select **TIBCO(r) Rendezvous(r)** from the list of adapters available in the **Adapter** dropdown and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-receive-port"></a><span data-ttu-id="d9382-137">建立 BizTalk 接收埠</span><span class="sxs-lookup"><span data-stu-id="d9382-137">Create a BizTalk Receive Port</span></span>  
  
1.  <span data-ttu-id="d9382-138">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="d9382-138">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="d9382-139">以滑鼠右鍵按一下接收埠] 資料夾，然後按一下 [**新增**，**單向接收埠...**顯示**接收埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9382-139">Right-click the Receive Ports folder and then click **New**, **One-Way Receive Port...** to display the **Receive Port Properties** dialog.</span></span>  
  
3.  <span data-ttu-id="d9382-140">輸入一個值**名稱**欄位，例如**TIBCORvOneWayRP**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9382-140">Enter a value for the **Name** field, for example **TIBCORvOneWayRP**, and click **OK**.</span></span>  
  
#### <a name="create-a-biztalk-receive-location"></a><span data-ttu-id="d9382-141">建立 BizTalk 接收位置</span><span class="sxs-lookup"><span data-stu-id="d9382-141">Create a BizTalk Receive Location</span></span>  
  
1.  <span data-ttu-id="d9382-142">以滑鼠右鍵按一下新的接收埠，然後按一下 **新增**，**接收位置...**</span><span class="sxs-lookup"><span data-stu-id="d9382-142">Right-click the new receive port and then click **New**, **Receive Location…**</span></span> <span data-ttu-id="d9382-143">若要顯示**接收位置屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9382-143">to display the **Receive Location Properties** dialog.</span></span>  
  
2.  <span data-ttu-id="d9382-144">輸入一個值**名稱**欄位，例如**TIBCORvOneWayRL**。</span><span class="sxs-lookup"><span data-stu-id="d9382-144">Enter a value for the **Name** field, for example **TIBCORvOneWayRL**.</span></span>  
  
3.  <span data-ttu-id="d9382-145">從使用中的配接器清單選取 TIBCO Rendezvous 配接器**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**的傳輸屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9382-145">Select the TIBCO Rendezvous adapter from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9382-146">這個值是在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中建立 TIBCO 配接器時指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="d9382-146">This value is the name that was specified when the TIBCO adapter was created in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="d9382-147">輸入一個值**RendezvousSubjectName**下**AdapterRequiredProperties**。</span><span class="sxs-lookup"><span data-stu-id="d9382-147">Enter a value for the **RendezvousSubjectName** under the **AdapterRequiredProperties**.</span></span>  
  
5.  <span data-ttu-id="d9382-148">輸入的值**認證接聽程式屬性**:</span><span class="sxs-lookup"><span data-stu-id="d9382-148">Enter values for the **Certified Listener Properties**:</span></span>  
  
    |<span data-ttu-id="d9382-149">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d9382-149">**Property**</span></span>|<span data-ttu-id="d9382-150">**值**</span><span class="sxs-lookup"><span data-stu-id="d9382-150">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="d9382-151">分類帳檔案名稱</span><span class="sxs-lookup"><span data-stu-id="d9382-151">Ledger file name</span></span>|<span data-ttu-id="d9382-152">要用於永續性認證訊息傳遞的分類帳檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d9382-152">Ledger file name to use for persistent certified message delivery.</span></span>|  
    |<span data-ttu-id="d9382-153">可重複使用的名稱</span><span class="sxs-lookup"><span data-stu-id="d9382-153">Reusable name</span></span>|<span data-ttu-id="d9382-154">要用於認證訊息傳遞的可重複使用對應名稱。</span><span class="sxs-lookup"><span data-stu-id="d9382-154">Reusable correspondent name to use for certified message delivery.</span></span> <span data-ttu-id="d9382-155">在網路上所有認證訊息通訊人名稱當中，這必須是唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="d9382-155">The name must be unique among all certified message correspondent names on the network.</span></span>|  
  
6.  <span data-ttu-id="d9382-156">輸入的值**認證**:</span><span class="sxs-lookup"><span data-stu-id="d9382-156">Enter values for the **Credentials**:</span></span>  
  
    |<span data-ttu-id="d9382-157">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d9382-157">**Property**</span></span>|<span data-ttu-id="d9382-158">**值**</span><span class="sxs-lookup"><span data-stu-id="d9382-158">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="d9382-159">密碼</span><span class="sxs-lookup"><span data-stu-id="d9382-159">Password</span></span>|<span data-ttu-id="d9382-160">TIBCO Rendezvous 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="d9382-160">The password for the TIBCO Rendezvous server.</span></span>|  
    |<span data-ttu-id="d9382-161">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="d9382-161">User name</span></span>|<span data-ttu-id="d9382-162">TIBCO Rendezvous 伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d9382-162">The user name for the TIBCO Rendezvous server.</span></span>|  
  
7.  <span data-ttu-id="d9382-163">輸入的值**RendezvousTransport**:</span><span class="sxs-lookup"><span data-stu-id="d9382-163">Enter values for the **RendezvousTransport**:</span></span>  
  
    |<span data-ttu-id="d9382-164">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d9382-164">**Property**</span></span>|<span data-ttu-id="d9382-165">**值**</span><span class="sxs-lookup"><span data-stu-id="d9382-165">**Value**</span></span>|  
    |------------------|---------------|  
    |<span data-ttu-id="d9382-166">精靈</span><span class="sxs-lookup"><span data-stu-id="d9382-166">Daemon</span></span>|<span data-ttu-id="d9382-167">Rendezvous 傳輸精靈參數。</span><span class="sxs-lookup"><span data-stu-id="d9382-167">Rendezvous Transport Daemon parameter.</span></span>|  
    |<span data-ttu-id="d9382-168">網路</span><span class="sxs-lookup"><span data-stu-id="d9382-168">Network</span></span>|<span data-ttu-id="d9382-169">Rendezvous 傳輸網路參數。</span><span class="sxs-lookup"><span data-stu-id="d9382-169">Rendezvous Transport Network parameter.</span></span>|  
    |<span data-ttu-id="d9382-170">服務</span><span class="sxs-lookup"><span data-stu-id="d9382-170">Service</span></span>|<span data-ttu-id="d9382-171">Rendezvous 傳輸服務參數。</span><span class="sxs-lookup"><span data-stu-id="d9382-171">Rendezvous Transport Service parameter.</span></span>|  
  
     <span data-ttu-id="d9382-172">如需屬性的詳細資訊，請參閱[設定 TIBCO Rendezvous 接收傳輸屬性](../core/setting-tibco-rendezvous-receive-transport-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d9382-172">For more information about the properties, see [Setting TIBCO Rendezvous Receive Transport Properties](../core/setting-tibco-rendezvous-receive-transport-properties.md).</span></span>  
  
8.  <span data-ttu-id="d9382-173">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d9382-173">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d9382-174">選取**XMLReceive**從清單中的可用管線**接收管線**下拉式清單方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9382-174">Select **XMLReceive** from the list of available pipelines in the **Receive pipeline** dropdown box and click **OK**.</span></span>  
  
10. <span data-ttu-id="d9382-175">以滑鼠右鍵按一下接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="d9382-175">Right-click the receive location and click **Enable**.</span></span>  
  
#### <a name="create-a-one-way-file-send-port"></a><span data-ttu-id="d9382-176">建立單向檔案傳送埠</span><span class="sxs-lookup"><span data-stu-id="d9382-176">Create a one-way file send port</span></span>  
  
1.  <span data-ttu-id="d9382-177">建立傳送埠所要使用的目標資料夾，例如 C:\FilesOut。</span><span class="sxs-lookup"><span data-stu-id="d9382-177">Create a target folder to be used by the send port, for example C:\FilesOut.</span></span>  
  
2.  <span data-ttu-id="d9382-178">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d9382-178">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Send Ports**.</span></span>  
  
3.  <span data-ttu-id="d9382-179">以滑鼠右鍵按一下**傳送埠**指向**新增**，**靜態單向傳送埠...**</span><span class="sxs-lookup"><span data-stu-id="d9382-179">Right-click **Send Ports** and point to **New**, **Static One-Way Send Port…**</span></span> <span data-ttu-id="d9382-180">若要顯示**傳送埠屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9382-180">to display the **Send Port Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="d9382-181">輸入一個值**名稱**欄位，例如**TIBCORvOneWayFileSP**。</span><span class="sxs-lookup"><span data-stu-id="d9382-181">Enter a value for the **Name** field, for example **TIBCORvOneWayFileSP**.</span></span>  
  
5.  <span data-ttu-id="d9382-182">選取**檔案**從清單中的可用配接器的**類型**下拉式清單方塊，然後按一下**設定**按鈕以顯示配接器**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9382-182">Select **FILE** from the list of available adapters in the **Type** dropdown box and click the **Configure** button to display the adapter **Transport Properties** dialog box.</span></span>  
  
6.  <span data-ttu-id="d9382-183">如**目的地資料夾**屬性中，輸入您稍早建立的資料夾位置，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9382-183">For the **Destination Folder** property, enter the location of the folder that you created earlier and click **OK**.</span></span>  
  
7.  <span data-ttu-id="d9382-184">選取**XMLTransmit**管線就會從管線中可用的清單**傳送管線**下拉式清單中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d9382-184">Select the **XMLTransmit** pipeline from the list of pipelines available in the **Send pipeline** dropdown and click **OK**.</span></span>  
  
8.  <span data-ttu-id="d9382-185">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**登錄並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d9382-185">Right-click the send port and click **Start** to enlist and start the send port.</span></span>  
  
#### <a name="build-and-deploy-the-project"></a><span data-ttu-id="d9382-186">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="d9382-186">Build and deploy the project</span></span>  
  
1.  <span data-ttu-id="d9382-187">以滑鼠右鍵按一下方案總管 中的 Onewaysend 專案，然後按一下**屬性**啟動專案的專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="d9382-187">Right-click the OneWayReceive project in Solution Explorer and click **Properties** to launch the Project Designer for the project.</span></span>  
  
2.  <span data-ttu-id="d9382-188">按一下**部署** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d9382-188">Click the **Deployment** tab.</span></span>  
  
3.  <span data-ttu-id="d9382-189">輸入適當的值**伺服器**屬性和**組態資料庫**下的屬性**BizTalk 群組**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="d9382-189">Enter the appropriate values for the **Server** property and the **Configuration Database** property under **BizTalk Group** category.</span></span>  
  
4.  <span data-ttu-id="d9382-190">以滑鼠右鍵按一下方案總管 中的 Onewaysend 專案，然後按一下**部署**建置專案並部署組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="d9382-190">Right-click the OneWayReceive project in Solution Explorer and click **Deploy** to build the project and deploy the assembly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration database.</span></span>  
  
#### <a name="bind-and-enlist-the-orchestration"></a><span data-ttu-id="d9382-191">繫結和登錄協調流程</span><span class="sxs-lookup"><span data-stu-id="d9382-191">Bind and Enlist the orchestration</span></span>  
  
1.  <span data-ttu-id="d9382-192">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，展開**BizTalk Application 1**，然後按一下**協調流程**。</span><span class="sxs-lookup"><span data-stu-id="d9382-192">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="d9382-193">按一下**重新整理**按鈕[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台工具列或按**F5**重新整理鍵盤上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台檢視。</span><span class="sxs-lookup"><span data-stu-id="d9382-193">Click the **Refresh** button in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console toolbar or press the **F5** key on your keyboard to refresh the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console view.</span></span>  
  
3.  <span data-ttu-id="d9382-194">按兩下協調流程以顯示**協調流程屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9382-194">Double-click the orchestration to display the **Orchestration Properties** dialog.</span></span>  
  
4.  <span data-ttu-id="d9382-195">按一下**繫結**以顯示協調流程繫結選項 對話方塊的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="d9382-195">Click **Bindings** in the left pane of the dialog to display the Bindings options for the orchestration.</span></span>  
  
5.  <span data-ttu-id="d9382-196">指定適當的繫結選項值，例如：</span><span class="sxs-lookup"><span data-stu-id="d9382-196">Specify the appropriate values for the binding options, for example:</span></span>  
  
    |<span data-ttu-id="d9382-197">**參數**</span><span class="sxs-lookup"><span data-stu-id="d9382-197">**Parameter**</span></span>|<span data-ttu-id="d9382-198">**值**</span><span class="sxs-lookup"><span data-stu-id="d9382-198">**Value**</span></span>|  
    |-------------------|---------------|  
    |<span data-ttu-id="d9382-199">Host</span><span class="sxs-lookup"><span data-stu-id="d9382-199">Host</span></span>|<span data-ttu-id="d9382-200">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="d9382-200">BizTalkServerApplication</span></span>|  
    |<span data-ttu-id="d9382-201">SendPort</span><span class="sxs-lookup"><span data-stu-id="d9382-201">SendPort</span></span>|<span data-ttu-id="d9382-202">TIBCORvOneWayFileSP</span><span class="sxs-lookup"><span data-stu-id="d9382-202">TIBCORvOneWayFileSP</span></span>|  
    |<span data-ttu-id="d9382-203">ReceivePort</span><span class="sxs-lookup"><span data-stu-id="d9382-203">ReceivePort</span></span>|<span data-ttu-id="d9382-204">TIBCORvOneWayRP</span><span class="sxs-lookup"><span data-stu-id="d9382-204">TIBCORvOneWayRP</span></span>|  
  
6.  <span data-ttu-id="d9382-205">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d9382-205">Click **OK**.</span></span>  
  
#### <a name="start-the-orchestration"></a><span data-ttu-id="d9382-206">啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="d9382-206">Start the orchestration</span></span>  
  
-   <span data-ttu-id="d9382-207">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下協調流程，然後按一下**啟動**登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="d9382-207">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click the orchestration and click **Start** to enlist and start the orchestration.</span></span>  
  
#### <a name="verify-that-the-application-receives-a-message"></a><span data-ttu-id="d9382-208">確認應用程式收到訊息</span><span class="sxs-lookup"><span data-stu-id="d9382-208">Verify that the application receives a message</span></span>  
  
-   <span data-ttu-id="d9382-209">開啟檔案傳送埠進行傳送時依設定要使用的目標資料夾，然後確認已產生輸出文件。</span><span class="sxs-lookup"><span data-stu-id="d9382-209">Open the folder that the file send port is configured to send to and verify that an output document was generated.</span></span>  
  
 <span data-ttu-id="d9382-210">如果文件執行個體處理成功，則會發生以下一系列的事件：</span><span class="sxs-lookup"><span data-stu-id="d9382-210">The following sequence of events occurs if the document instance is processed successfully:</span></span>  
  
1.  <span data-ttu-id="d9382-211">TIBCO Rendezvous 配接器接收來自 TIBCO 系統的訊息，並以 BizTalk 訊息的形式將其發佈至 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="d9382-211">The TIBCO Rendezvous adapter receives a message from TIBCO system and publishes it to the MessageBox as a BizTalk message.</span></span>  
  
2.  <span data-ttu-id="d9382-212">協調流程訂閱這個發佈訊息，因此 BizTalk 傳訊引擎會啟動協調流程的執行個體，然後將訊息傳送至這個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="d9382-212">The orchestration subscribes to this published message so the BizTalk Messaging Engine activates an instance of the orchestration and sends the message to the orchestration instance.</span></span>  
  
3.  <span data-ttu-id="d9382-213">協調流程執行個體將訊息發佈回 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="d9382-213">The orchestration instance publishes the message back to the MessageBox.</span></span>  
  
4.  <span data-ttu-id="d9382-214">檔案傳送埠訂閱這個訊息，因此 BizTalk 會將訊息傳送至檔案配接器。</span><span class="sxs-lookup"><span data-stu-id="d9382-214">The File send port subscribes to this message so BizTalk sends the message to the File adapter.</span></span>  
  
5.  <span data-ttu-id="d9382-215">檔案配接器將包含結果集的訊息寫入至指定的輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="d9382-215">The File adapter writes the message containing the result set to the designated output folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9382-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9382-216">See Also</span></span>  
 <span data-ttu-id="d9382-217">[教學課程： 使用 BizTalk Adapter for TIBCO Rendezvous 來傳送資料](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md) </span><span class="sxs-lookup"><span data-stu-id="d9382-217">[Tutorial: Using the BizTalk Adapter for TIBCO Rendezvous to Send Data](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md) </span></span>  
 <span data-ttu-id="d9382-218">[教學課程： 使用 Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="d9382-218">[Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="d9382-219">快速入門</span><span class="sxs-lookup"><span data-stu-id="d9382-219">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)