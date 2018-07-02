---
title: 新增 BizTalk Adapter for JD Edwards OneWorld |Microsoft Docs
description: 將 JD Edwards OneWorld 新增至 BizTalk 管理、 建立傳送埠、 設定傳輸屬性中，和 BizTalk Server 中使用 JD Edwards OneWorld 配接器時，使用 XMLReceive 和 XMLTransmit 管線
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03126f4e-9156-4c0c-ab5c-0627f0c05263
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decababef3ece92c99687a4019b15625b1b4c6b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981391"
---
# <a name="configure-jd-edwards-enterpriseone-artifacts-in-biztalk-administration"></a><span data-ttu-id="e7532-103">在 BizTalk 管理中設定 JD Edwards EnterpriseOne 成品</span><span class="sxs-lookup"><span data-stu-id="e7532-103">Configure JD Edwards EnterpriseOne artifacts in BizTalk Administration</span></span>
<span data-ttu-id="e7532-104">Microsoft BizTalk Adapter for JD Edwards OneWorld 包含 [接收處理常式] 和 [傳送處理常式] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e7532-104">Microsoft BizTalk Adapter for JD Edwards OneWorld contains both the Receive Handler and Send Handler folders.</span></span> <span data-ttu-id="e7532-105">[傳送處理常式] 資料夾包含 BizTalkServerApplication。</span><span class="sxs-lookup"><span data-stu-id="e7532-105">The Send Handler folder contains BizTalkServerApplication.</span></span> <span data-ttu-id="e7532-106">BizTalk Adapter for JD Edwards OneWorld 是可建立的；它會在與 BizTalk Server 相同的程序中執行，而且不會在外掛式主控件程序中執行。</span><span class="sxs-lookup"><span data-stu-id="e7532-106">BizTalk Adapter for JD Edwards OneWorld is creatable; it runs in-process with BizTalk Server and does not run in an isolated host process.</span></span>  

## <a name="add-the-adapter-to-biztalk-administration"></a><span data-ttu-id="e7532-107">將配接器新增至 BizTalk 管理</span><span class="sxs-lookup"><span data-stu-id="e7532-107">Add the adapter to BizTalk Administration</span></span> 

1.  <span data-ttu-id="e7532-108">開啟**BizTalk Server 管理**，展開**BizTalk Server 管理**，展開**BizTalk 群組**，然後展開**平台設定**.</span><span class="sxs-lookup"><span data-stu-id="e7532-108">Open **BizTalk Server Administration**, expand **BizTalk Server Administration**, expand **BizTalk Group**, and then expand **Platform Settings**.</span></span>  
  
2.  <span data-ttu-id="e7532-109">以滑鼠右鍵按一下**配接器**，選取**新增**，然後選取**配接器**。</span><span class="sxs-lookup"><span data-stu-id="e7532-109">Right-click **Adapters**, select **New**, and select **Adapter**.</span></span>  
  
3.  <span data-ttu-id="e7532-110">輸入配接器的名稱。</span><span class="sxs-lookup"><span data-stu-id="e7532-110">Enter a name for the adapter.</span></span> <span data-ttu-id="e7532-111">例如，輸入`JDEOneWorld`。</span><span class="sxs-lookup"><span data-stu-id="e7532-111">For example, enter`JDEOneWorld`.</span></span>  
  
4.  <span data-ttu-id="e7532-112">選取  **jdeoneworld**從**配接器**清單，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="e7532-112">Select **JDEOneWorld** from the **Adapter** list, and select **OK**.</span></span>  

  
### <a name="check-if-the-adapter-is-working"></a><span data-ttu-id="e7532-113">檢查配接器是否正常運作</span><span class="sxs-lookup"><span data-stu-id="e7532-113">Check if the adapter is working</span></span> 
 <span data-ttu-id="e7532-114">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以確認配接器藉由查看正確運作**邏輯系統**視窗。</span><span class="sxs-lookup"><span data-stu-id="e7532-114">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, you can verify that the adapter is functioning correctly by looking at the **Logical System** window.</span></span> <span data-ttu-id="e7532-115">在初次安裝時，因為您尚未建立與伺服器系統的連線，也尚未建立任何邏輯系統，所以這個視窗會是空的。</span><span class="sxs-lookup"><span data-stu-id="e7532-115">On initial installation, this window is empty because you have not yet established a connection to the server system, nor have you created any logical systems.</span></span>  
  
 
1. <span data-ttu-id="e7532-116">在 [ **BizTalk Server 管理]**，展開**平台設定**，展開**配接器**，然後選取 **[jdeoneworld]**。</span><span class="sxs-lookup"><span data-stu-id="e7532-116">In **BizTalk Server Administration**, expand **Platform Settings**, expand **Adapters**, and then select **JDEOneWorld**.</span></span>  
  
2. <span data-ttu-id="e7532-117">在 [詳細資料] 窗格中，以滑鼠右鍵按一下**BizTalkServerApplication**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e7532-117">In the details pane, right-click **BizTalkServerApplication**, and select **Properties**.</span></span>  
  
3. <span data-ttu-id="e7532-118">選取 [**屬性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e7532-118">Select the **Properties** tab.</span></span>  
  
4. <span data-ttu-id="e7532-119">設定 SQL 連線參數。</span><span class="sxs-lookup"><span data-stu-id="e7532-119">Set the SQL Connection parameters.</span></span>  
  
   -   <span data-ttu-id="e7532-120">**定義 SQL 資料庫參數-** 的 SQL Server 名稱和資料庫是您在安裝期間設定。</span><span class="sxs-lookup"><span data-stu-id="e7532-120">**Define SQL Database Parameters -** The SQL Server Name and Database are those you set at installation.</span></span> <span data-ttu-id="e7532-121">您可以在這個文字區域中重新定義此配接器的伺服器與資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7532-121">This is the text area that you can redefine the server and database for this adapter.</span></span>  
  
5. <span data-ttu-id="e7532-122">選取 **關閉**以結束**邏輯系統**視窗。</span><span class="sxs-lookup"><span data-stu-id="e7532-122">Select **Close** to exit the **Logical System** window.</span></span>  
  
    <span data-ttu-id="e7532-123">下一個步驟是要使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 來新增邏輯系統。</span><span class="sxs-lookup"><span data-stu-id="e7532-123">Your next step is to add a logical system using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  

## <a name="create-the-send-port"></a><span data-ttu-id="e7532-124">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="e7532-124">Create the send port</span></span>  
  
1.  <span data-ttu-id="e7532-125">在 [ **BizTalk Server 管理]**，展開**BizTalk 群組**，展開**應用程式**，然後展開您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7532-125">In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand your application.</span></span>  
  
2.  <span data-ttu-id="e7532-126">以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="e7532-126">Right-click **Send Ports**, select **New**, and then select **Static Solicit-Response Send Port**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7532-127">您也可以使用**靜態單向連接埠**。</span><span class="sxs-lookup"><span data-stu-id="e7532-127">You can also use **Static One-Way Port**.</span></span>  
  
3.  <span data-ttu-id="e7532-128">在 **傳送埠屬性**，選取**名稱**欄位，並輸入傳送埠名稱。</span><span class="sxs-lookup"><span data-stu-id="e7532-128">In the **Send Port Properties**, select the **Name** field, and enter a send port name.</span></span> <span data-ttu-id="e7532-129">例如，輸入**SendToJDE**。</span><span class="sxs-lookup"><span data-stu-id="e7532-129">For example, enter **SendToJDE**.</span></span>  
  
4.  <span data-ttu-id="e7532-130">在 **型別**下拉式清單中，選取**jdeoneworld**。</span><span class="sxs-lookup"><span data-stu-id="e7532-130">In the **Type** drop-down list, select **JDEOneWorld**.</span></span>  
  
5.  <span data-ttu-id="e7532-131">在  **URI**下拉式清單中，選取 傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="e7532-131">In the **URI** drop-down list, select the send handler.</span></span>  
  
6.  <span data-ttu-id="e7532-132">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e7532-132">Select **OK**.</span></span> 

## <a name="configure-the-transport-properties"></a><span data-ttu-id="e7532-133">設定傳輸屬性</span><span class="sxs-lookup"><span data-stu-id="e7532-133">Configure the transport properties</span></span>
<span data-ttu-id="e7532-134">「JD Edwards OneWorld 傳輸屬性系統定義」用於設計和執行階段登入。</span><span class="sxs-lookup"><span data-stu-id="e7532-134">The JD Edwards OneWorld Transport Property System Definition is used for design and run-time logon.</span></span> <span data-ttu-id="e7532-135">您要設定這些認證以在設計階段瀏覽 JD Edwards OneWorld 商務功能，並在執行階段進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="e7532-135">You set these credentials to browse JD Edwards OneWorld business functions at design time and make calls at run time.</span></span>  
  
 <span data-ttu-id="e7532-136">當與 JD Edwards OneWorld 建立連線時，參數會傳送到連線物件 (使用者、密碼、環境)。</span><span class="sxs-lookup"><span data-stu-id="e7532-136">When a connection is made to JD Edwards OneWorld, parameters are passed to the connection object (User, Password, Environment).</span></span> <span data-ttu-id="e7532-137">它會傳回一個 JD Edwards OneWorld 應用程式商務函數。</span><span class="sxs-lookup"><span data-stu-id="e7532-137">It returns an instance of the JD Edwards OneWorld aApplication business function.</span></span> <span data-ttu-id="e7532-138">企業/應用程式伺服器名稱與服務接聽的已定義 TCP/IP 連接埠會進一步定義認證。</span><span class="sxs-lookup"><span data-stu-id="e7532-138">The credentials are further defined by the name of the enterprise/application server, and the defined TCP/IP port on which the service listens.</span></span>  
  
 <span data-ttu-id="e7532-139">企業伺服器名稱和連接埠會讀取名為 jdeinterop.ini 的檔案。</span><span class="sxs-lookup"><span data-stu-id="e7532-139">The enterprise server name and port are read from a file that is named jdeinterop.ini.</span></span> <span data-ttu-id="e7532-140">這些值必須是相同的系統定義的設定中。</span><span class="sxs-lookup"><span data-stu-id="e7532-140">These values must be the same as those that are in the System Definition settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7532-141">所有項目均區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e7532-141">All entries are case sensitive.</span></span>  
  
### <a name="set-the-properties"></a><span data-ttu-id="e7532-142">設定屬性</span><span class="sxs-lookup"><span data-stu-id="e7532-142">Set the properties</span></span>  
 <span data-ttu-id="e7532-143">在 [**傳輸屬性**] 對話方塊中，您設定專屬於伺服器系統與您嘗試存取之物件的連接和認證參數。</span><span class="sxs-lookup"><span data-stu-id="e7532-143">In the **Transport Properties** dialog box, you set the connection and credential parameters that are specific to the server system and the objects you are trying to access.</span></span>  
  
1.  <span data-ttu-id="e7532-144">提供認證。</span><span class="sxs-lookup"><span data-stu-id="e7532-144">Provide credentials.</span></span> <span data-ttu-id="e7532-145">您可以使用下列其中一種方法來存取 JD Edwards OneWorld 系統：</span><span class="sxs-lookup"><span data-stu-id="e7532-145">You can access the JD Edwards OneWorld system using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="e7532-146">登入認證 （密碼、 使用者名稱）： 如果您使用這個方法時，請移至步驟 5。</span><span class="sxs-lookup"><span data-stu-id="e7532-146">Logon credentials (Password, User name): If you use this method, go to step 5.</span></span>  
  
    -   <span data-ttu-id="e7532-147">單一登入。</span><span class="sxs-lookup"><span data-stu-id="e7532-147">Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="e7532-148">若要使用單一登入 (SSO)，請選取 **[是]** 中**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="e7532-148">To use Single Sign-On (SSO), select **Yes** in the **Use SSO**.</span></span>  
  
     <span data-ttu-id="e7532-149">如需如何設定 SSO 的詳細資訊，請參閱[配接器中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)</span><span class="sxs-lookup"><span data-stu-id="e7532-149">For more information about how to set up SSO, see [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)</span></span>  
  
3.  <span data-ttu-id="e7532-150">在清單中選取分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7532-150">Select an affiliate application in the list.</span></span>  
  
     <span data-ttu-id="e7532-151">企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 JD Edwards OneWorld)。</span><span class="sxs-lookup"><span data-stu-id="e7532-151">An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as JD Edwards OneWorld.</span></span> <span data-ttu-id="e7532-152">Microsoft BizTalk Adapter for JD Edwards OneWorld 會使用應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="e7532-152">Microsoft BizTalk Adapter for JD Edwards OneWorld uses the credentials of an application user.</span></span> <span data-ttu-id="e7532-153">這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 認證資料庫中擷取所得。</span><span class="sxs-lookup"><span data-stu-id="e7532-153">These credentials are retrieved from the SSO Credentials database for the server system for a specified affiliate application.</span></span> <span data-ttu-id="e7532-154">這些認證就是啟動 BizTalk Server 專案之應用程式使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="e7532-154">The credentials are those of the application user who launched the BizTalk Server project.</span></span>  
  
     <span data-ttu-id="e7532-155">如需詳細資訊，請參閱 <<c0> [ 建立分支機構應用程式](../core/creating-affiliate-applications3.md)。</span><span class="sxs-lookup"><span data-stu-id="e7532-155">For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications3.md).</span></span>  
  
4.  <span data-ttu-id="e7532-156">依序展開**JD Edwards OneWorld 系統**節點，然後輸入所有必要的連接資訊至 JD Edwards OneWorld 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e7532-156">Expand the **JD Edwards OneWorld system** node and enter all required information for connection to the JD Edwards OneWorld server.</span></span>  
  
     <span data-ttu-id="e7532-157">![](../core/media/jdedadapter-02-jdesystem.gif "JDEdAdapter_02_JDESystem")</span><span class="sxs-lookup"><span data-stu-id="e7532-157">![](../core/media/jdedadapter-02-jdesystem.gif "JDEdAdapter_02_JDESystem")</span></span>  
  
     <span data-ttu-id="e7532-158">在設定連線參數後，您可以瀏覽 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="e7532-158">After you set the connection parameters, you can browse a JD Edwards OneWorld system.</span></span> <span data-ttu-id="e7532-159">如需詳細資訊，請參閱 <<c0> [ 匯入 JD Edwards OneWorld 結構描述至 BizTalk Server 專案](../core/importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="e7532-159">For more information, see [Importing JD Edwards OneWorld Schemas into BizTalk Server Projects](../core/importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md).</span></span>  
  
5.  <span data-ttu-id="e7532-160">輸入值，在表示的呼叫，例如 200，數目**同時呼叫數目上限**它是否必要。</span><span class="sxs-lookup"><span data-stu-id="e7532-160">Enter a value representing the number of calls, for example 200, in **Max Concurrent Calls** if it is required.</span></span>  
  
     <span data-ttu-id="e7532-161">`Max Concurrent Calls`參數可讓您最佳化組態。</span><span class="sxs-lookup"><span data-stu-id="e7532-161">The `Max Concurrent Calls` parameter lets you optimize your configuration.</span></span> <span data-ttu-id="e7532-162">在輸送量超過後端處理能力時，可以使用這個參數來啟動訊息多載保護。</span><span class="sxs-lookup"><span data-stu-id="e7532-162">You use this parameter in instances where the throughput exceeds back-end processing capabilities, to activate message-overload protection.</span></span> <span data-ttu-id="e7532-163">預設值為 -1，表示呼叫沒有上限。</span><span class="sxs-lookup"><span data-stu-id="e7532-163">The default is -1, which means that the calls are unlimited.</span></span>  
  
     <span data-ttu-id="e7532-164">當 BizTalk Server 將訊息提交到傳輸配接器時，會先收到來自配接器的批次。</span><span class="sxs-lookup"><span data-stu-id="e7532-164">When BizTalk Server submits messages to the transmit adapter, it first receives a batch from the adapter.</span></span> <span data-ttu-id="e7532-165">它會在批次上叫用 `TransmitMessage` 以傳輸每個訊息。</span><span class="sxs-lookup"><span data-stu-id="e7532-165">It invokes `TransmitMessage` on the batch to transmit each message.</span></span> <span data-ttu-id="e7532-166">完成傳輸時，BizTalk Server 會在批次上叫用 `Done`，這時配接器就會開始將訊息傳輸至後端。</span><span class="sxs-lookup"><span data-stu-id="e7532-166">When done, BizTalk Server invokes `Done` on the batch, and the adapter starts transmitting the messages to the back-end.</span></span> <span data-ttu-id="e7532-167">如果 BizTalk Server 在叫用 `Done` 之前取得多個批次，可能永遠不會叫用。</span><span class="sxs-lookup"><span data-stu-id="e7532-167">If BizTalk Server obtains multiple batches before invoking `Done`, it might never occur.</span></span> <span data-ttu-id="e7532-168">藉由設定批次中的訊息數目上限，您便可以控制送到後端的訊息。</span><span class="sxs-lookup"><span data-stu-id="e7532-168">By setting the maximum number of messages in a batch, you can control messages to the back-end.</span></span>  
  
     <span data-ttu-id="e7532-169">此參數的變更會在 1 分鐘內生效；BizTalk Server 必須擷取儲存在 SQL 資料庫中的配接器組態變更。</span><span class="sxs-lookup"><span data-stu-id="e7532-169">Changing this parameter takes effect within one minute; BizTalk Server must retrieve the changes to the adapter configuration saved in the SQL database.</span></span>  
  
6.  <span data-ttu-id="e7532-170">選取  **是** for**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="e7532-170">Select **Yes** for **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.</span></span>  
  
     <span data-ttu-id="e7532-171">例如，您希望處理程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在 Microsoft 配接器精靈的選項中。</span><span class="sxs-lookup"><span data-stu-id="e7532-171">For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7532-172">這個 browsingagent.exe 要等到您結束目前的瀏覽工作階段才會重新整理。</span><span class="sxs-lookup"><span data-stu-id="e7532-172">The browsingagent.exe does not refresh until you exit the current browsing session.</span></span> <span data-ttu-id="e7532-173">例如，您必須先結束**產生的新增項目**瀏覽工作階段並重新進入，才能更新 browsingagent.exe。</span><span class="sxs-lookup"><span data-stu-id="e7532-173">For example, you must exit the **Add generated item** browsing session and reenter to update the browsingagent.exe.</span></span>  
  
7.  <span data-ttu-id="e7532-174">提供所有必要的資訊後，按一下**套用**，然後按一下**確定**以採用連線資訊。</span><span class="sxs-lookup"><span data-stu-id="e7532-174">After providing all required information, click **Apply**, and then click **OK** to accept the connection information.</span></span>  
  
     <span data-ttu-id="e7532-175">您必須為 BizTalk Adapter for JD Edwards OneWorld 設定連線參數，才能存取 JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="e7532-175">You must set connection parameters for BizTalk Adapter for JD Edwards OneWorld to access JD Edwards OneWorld.</span></span>  
  
### <a name="adapter-required-properties"></a><span data-ttu-id="e7532-176">配接器必要屬性</span><span class="sxs-lookup"><span data-stu-id="e7532-176">Adapter required properties</span></span>  
 <span data-ttu-id="e7532-177">如果沒有在 [控制台] 中設定全域環境變數，您可以在此區段中設定。</span><span class="sxs-lookup"><span data-stu-id="e7532-177">If you did not set global environment variables in Control Panel, you can do so in this section.</span></span>  
  
|<span data-ttu-id="e7532-178">參數</span><span class="sxs-lookup"><span data-stu-id="e7532-178">Parameter</span></span>|<span data-ttu-id="e7532-179">描述</span><span class="sxs-lookup"><span data-stu-id="e7532-179">Description</span></span>|  
|---------------|-----------------|  
|`Host`|<span data-ttu-id="e7532-180">輸入主控件伺服器電腦名稱的名稱 (例如`actsvr1`); 或電腦的 IP 位址 (例如`123.456.0.789`)。</span><span class="sxs-lookup"><span data-stu-id="e7532-180">Type the name of the host server computer name (for example, `actsvr1`); or the IP address of the computer (for example, `123.456.0.789`).</span></span>|  
|<span data-ttu-id="e7532-181">JAVA_HOME</span><span class="sxs-lookup"><span data-stu-id="e7532-181">JAVA_HOME</span></span>|<span data-ttu-id="e7532-182">輸入 JDK 安裝的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="e7532-182">Type the complete path of your JDK installation.</span></span>|  
|<span data-ttu-id="e7532-183">JDE Edwards 環境</span><span class="sxs-lookup"><span data-stu-id="e7532-183">JDE Edwards Environment</span></span>|<span data-ttu-id="e7532-184">在 JD Edwards OneWorld 中，輸入環境的名稱，例如`DV7333`。</span><span class="sxs-lookup"><span data-stu-id="e7532-184">Type the name of an environment in JD Edwards OneWorld, for example, `DV7333`.</span></span><br /><br /> <span data-ttu-id="e7532-185">DV7333 是開發環境的一般名稱，PY7333 常見於原型環境，PD7333 常見於實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="e7532-185">DV7333 is a common name for the development environment, PY7333 is common for the prototype environment, and PD7333 is common for the production environment.</span></span>|  
|<span data-ttu-id="e7532-186">JDEdwards JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="e7532-186">JDEdwards JAR Files</span></span>|<span data-ttu-id="e7532-187">輸入每個 JAR 檔案的完整路徑與檔案名稱：</span><span class="sxs-lookup"><span data-stu-id="e7532-187">Enter the complete path and file name for each JAR file:</span></span><br /><br /> <span data-ttu-id="e7532-188">-Connector.jar</span><span class="sxs-lookup"><span data-stu-id="e7532-188">-   Connector.jar</span></span><br /><span data-ttu-id="e7532-189">-Kernel.jar</span><span class="sxs-lookup"><span data-stu-id="e7532-189">-   Kernel.jar</span></span><br /><span data-ttu-id="e7532-190">-JDEJAccess.jar</span><span class="sxs-lookup"><span data-stu-id="e7532-190">-   JDEJAccess.jar</span></span><br /><span data-ttu-id="e7532-191">-JDEActionalInterop.jar</span><span class="sxs-lookup"><span data-stu-id="e7532-191">-   JDEActionalInterop.jar</span></span><br /><br /> <span data-ttu-id="e7532-192">每個 JAR 檔案都必須以分號 (;) 分隔，且不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="e7532-192">Each jar file must be separated with a semi-colon (;) and no space.</span></span> <span data-ttu-id="e7532-193">例如：</span><span class="sxs-lookup"><span data-stu-id="e7532-193">For example:</span></span><br /><br /> `<drive>\Connector.jar;<drive>\Kernel.jar;`|  
|<span data-ttu-id="e7532-194">[密碼]</span><span class="sxs-lookup"><span data-stu-id="e7532-194">Password</span></span>|<span data-ttu-id="e7532-195">輸入指定使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="e7532-195">Type the password of the specified user.</span></span>|  
|<span data-ttu-id="e7532-196">通訊埠</span><span class="sxs-lookup"><span data-stu-id="e7532-196">Port</span></span>|<span data-ttu-id="e7532-197">輸入會交換資料的連接埠號碼 (例如`6009`)。</span><span class="sxs-lookup"><span data-stu-id="e7532-197">Type the port number that will exchange data (for example, `6009`).</span></span>|  
|<span data-ttu-id="e7532-198">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="e7532-198">User Name</span></span>|<span data-ttu-id="e7532-199">輸入將用來登入 JD Edwards OneWorld 系統的 JD Edwards OneWorld 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e7532-199">Type a JD Edwards OneWorld user name that will be used to log on to the JD Edwards OneWorld system.</span></span>|  

## <a name="use-the-xmltransmit-and-xmlreceive-pipelines"></a><span data-ttu-id="e7532-200">使用 XMLTransmit 和 XMLReceive 管線</span><span class="sxs-lookup"><span data-stu-id="e7532-200">Use the XMLTransmit and XMLReceive pipelines</span></span>
<span data-ttu-id="e7532-201">Microsoft BizTalk Adapter for JD Edwards OneWorld 要求您選取 XMLTransmit 和 XMLReceive 傳送與接收管線。</span><span class="sxs-lookup"><span data-stu-id="e7532-201">Microsoft BizTalk Adapter for JD Edwards OneWorld requires that you select XMLTransmit and XMLReceive for the send and receive pipelines.</span></span>  
  
1.  <span data-ttu-id="e7532-202">在 [ **BizTalk Server 管理]**，展開**應用程式**，然後展開您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7532-202">In **BizTalk Server Administration**, expand **Applications**, and then expand your application.</span></span>  
  
2.  <span data-ttu-id="e7532-203">選取 **傳送埠**，以滑鼠右鍵按一下您的傳送埠，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e7532-203">Select **Send Ports**, right-click your send port, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="e7532-204">在 **傳送埠屬性**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e7532-204">In the **Send Ports Properties**, do the following:</span></span>  
  
    1.  <span data-ttu-id="e7532-205">選取傳送管線，從**傳送管線**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e7532-205">Select the send pipeline from the **Send Pipeline** drop-down list.</span></span>  
  
    2.  <span data-ttu-id="e7532-206">選取接收管線，從**接收管線**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e7532-206">Select the Receive pipeline from the **Receive Pipeline** drop-down list.</span></span>  
  
4.  <span data-ttu-id="e7532-207">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e7532-207">Select **OK**.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="e7532-208">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="e7532-208">Next steps</span></span>
[<span data-ttu-id="e7532-209">將配接器結構描述匯入 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e7532-209">Import adapter schemas into Visual Studio</span></span>](importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md)  
[<span data-ttu-id="e7532-210">使用訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="e7532-210">Use Message Context Properties</span></span>](using-message-context-properties2.md)