---
title: "如何執行商務程序管理解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, validating
- process management solution tutorial, submitting orders
- process management solution tutorial, stopping orders
- process management solution tutorial, updating orders
ms.assetid: cb77651e-e16c-49dc-9f8a-88584cd68a8b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3997fb18e7498ab2bc5f8c77b53740fb87ab6f93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-run-the-business-process-management-solution"></a><span data-ttu-id="29924-102">如何執行商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="29924-102">How to Run the Business Process Management Solution</span></span>
<span data-ttu-id="29924-103">下列步驟描述如何在單一電腦上執行和驗證商務程序管理解決方案。</span><span class="sxs-lookup"><span data-stu-id="29924-103">The following steps describe how to run and validate the Business Process Management solution on a single computer.</span></span>  
  
-   [<span data-ttu-id="29924-104">啟動商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="29924-104">Start the Business Process Management Solution</span></span>](#step1)  
  
-   [<span data-ttu-id="29924-105">執行和驗證商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="29924-105">Run and validate the Business Process Management Solution</span></span>](#step3)  
  
## <a name="prerequisites"></a><span data-ttu-id="29924-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="29924-106">Prerequisites</span></span>  
 <span data-ttu-id="29924-107">執行 BPM 解決方案之前, 您必須執行中的步驟[如何安裝商務程序管理解決方案](../core/how-to-install-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="29924-107">Before running the BPM solution, you must perform the steps in [How to Install the Business Process Management Solution](../core/how-to-install-the-business-process-management-solution.md).</span></span>  
  
##  <a name="step1"></a><span data-ttu-id="29924-108">啟動商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="29924-108">Start the Business Process Management Solution</span></span>  
  
#### <a name="to-start-the-business-process-management-solution"></a><span data-ttu-id="29924-109">啟動商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="29924-109">To start the Business Process Management Solution</span></span>  
  
1.  <span data-ttu-id="29924-110">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="29924-110">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="29924-111">在**BizTalk Server 管理主控台**，依序展開**BizTalk 群組**，依序展開**平台設定**，依序展開**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="29924-111">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Platform Settings**, expand **Host Instances**, right-click **BizTalkServerApplication**, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="29924-112">在**BizTalk Server 管理主控台**，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="29924-112">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
    1.  <span data-ttu-id="29924-113">以滑鼠右鍵按一下 BTSScn.BPM.MessagingApp，按一下**啟動**，然後按一下 [**啟動**上**啟動應用程式**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="29924-113">Right-click BTSScn.BPM.MessagingApp, click **Start**, and then click **Start** on the **Start Application** dialog box.</span></span>  
  
    2.  <span data-ttu-id="29924-114">以滑鼠右鍵按一下 BTSScn.BPM.OrderBrokerApp，按一下**啟動**，然後按一下 [**啟動**上**啟動應用程式**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="29924-114">Right-click BTSScn.BPM.OrderBrokerApp, click **Start**, and then click **Start** on the **Start Application** dialog box.</span></span>  
  
    3.  <span data-ttu-id="29924-115">以滑鼠右鍵按一下 BTSScn.BPM.CableOrderApp，按一下**啟動**，然後按一下 [**啟動**上**啟動應用程式**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="29924-115">Right-click BTSScn.BPM.CableOrderApp, click **Start**, and then click **Start** on the **Start Application** dialog box.</span></span>  
  
    4.  <span data-ttu-id="29924-116">以滑鼠右鍵按一下 BTSScn.BPM.OrderBrokerApp.Test，然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="29924-116">Right-click BTSScn.BPM.OrderBrokerApp.Test, and click **Stop**.</span></span> <span data-ttu-id="29924-117">在**停止應用程式**對話方塊中，選取**完全停止-終止執行個體**，然後按一下 **停止**。</span><span class="sxs-lookup"><span data-stu-id="29924-117">In the **Stop Application** dialog box, select **Full Stop - Terminate instance**, and then click **Stop**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29924-118">將資訊插入歷程記錄資料庫。</span><span class="sxs-lookup"><span data-stu-id="29924-118">To insert information in the history database.</span></span> <span data-ttu-id="29924-119">OrderBroker 協調流程會使用其中的 HistoryPort 傳送埠**傳遞通知**屬性設定**Transmitted**。</span><span class="sxs-lookup"><span data-stu-id="29924-119">the OrderBroker orchestration uses the HistoryPort send port of which the **Delivery Notification** property is set **Transmitted**.</span></span> <span data-ttu-id="29924-120">傳送埠會與 HistoryInsert-SPG 傳送埠群組繫結，此群組包含 HistoryInsert-SP 與 HistoryInsert-Test-SP 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="29924-120">The send port is bounded to the HistoryInsert-SPG send group which includes the HistoryInsert-SP and HistoryInsert-Test-SP send ports.</span></span> <span data-ttu-id="29924-121">對於這兩個傳送埠，訊息引擎會發佈兩個通知訊息到 OrderBroker 協調流程。</span><span class="sxs-lookup"><span data-stu-id="29924-121">For these two send ports the message engine will publish two acknowledgment messages to the OrderBroker orchestration.</span></span> <span data-ttu-id="29924-122">它會因為未使用訊息而擱置協調流程。</span><span class="sxs-lookup"><span data-stu-id="29924-122">It makes the orchestration suspended due to unconsumed messages.</span></span> <span data-ttu-id="29924-123">若要避免此情況，您必須取消登錄其中一個傳送埠。</span><span class="sxs-lookup"><span data-stu-id="29924-123">To avoid this situation, you must unenlist one of the send ports.</span></span> <span data-ttu-id="29924-124">在此逐步解說中，會透過完全停止 BTSScn.BPM.OrderBrokerApp.Test 應用程式以取消登錄 HistoryInsert-Test-SP 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="29924-124">In this walkthrough, unenlist HistoryInsert-Test-SP send port by fully stopping the BTSScn.BPM.OrderBrokerApp.Test application.</span></span> <span data-ttu-id="29924-125">如需 OrderBroker 協調流程的詳細資訊，請參閱[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="29924-125">For more information about the OrderBroker orchestration, see [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).</span></span> <span data-ttu-id="29924-126">如需有關**傳遞通知**屬性，請參閱[使用通知](../core/using-acknowledgments.md)。</span><span class="sxs-lookup"><span data-stu-id="29924-126">For more information about **Delivery Notification** property, see [Using Acknowledgments](../core/using-acknowledgments.md).</span></span>  
  
4.  <span data-ttu-id="29924-127">執行 Facilities Simulator，方式如下：</span><span class="sxs-lookup"><span data-stu-id="29924-127">Run the Facilities Simulator as follows:</span></span>  
  
    1.  <span data-ttu-id="29924-128">開啟命令提示字元，將目錄變更為 %BTSSolutionsPath%\BPM\FacilitiesSimulator\bin\debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29924-128">Open a command prompt, change the directory to the %BTSSolutionsPath%\BPM\FacilitiesSimulator\bin\debug folder.</span></span>  
  
    2.  <span data-ttu-id="29924-129">輸入 `BTSScnBPMFacilities.exe`，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="29924-129">Type `BTSScnBPMFacilities.exe`, and then press ENTER.</span></span> <span data-ttu-id="29924-130">讓 FacilitiesSimulator 繼續執行。</span><span class="sxs-lookup"><span data-stu-id="29924-130">Keep the FacilitiesSimulator running.</span></span> <span data-ttu-id="29924-131">此應用程式模擬在 Southridge Video 處理後端系統的設備。</span><span class="sxs-lookup"><span data-stu-id="29924-131">This application simulates the facilities processing back-end systems at Southridge Video.</span></span>  
  
    3.  <span data-ttu-id="29924-132">在 FacilitiesSimulator 中，輸入下列接收和傳輸佇列：</span><span class="sxs-lookup"><span data-stu-id="29924-132">In the FacilitiesSimulator, type the following receive and transmit queues:</span></span>  
  
        |<span data-ttu-id="29924-133">名稱</span><span class="sxs-lookup"><span data-stu-id="29924-133">Name</span></span>|<span data-ttu-id="29924-134">值</span><span class="sxs-lookup"><span data-stu-id="29924-134">Value</span></span>|  
        |----------|-----------|  
        |<span data-ttu-id="29924-135">**接收佇列**</span><span class="sxs-lookup"><span data-stu-id="29924-135">**Receive Queue**</span></span>|`.\private$\ToFacilitiesQ`|  
        |<span data-ttu-id="29924-136">**傳輸佇列**</span><span class="sxs-lookup"><span data-stu-id="29924-136">**Transmit Queue**</span></span>|`.\private$\FromFacilitiesQ`|  
  
    4.  <span data-ttu-id="29924-137">在 FacilitiesSimulator 中按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="29924-137">In the FacilitiesSimulator, Click **Start**.</span></span>  
  
5.  <span data-ttu-id="29924-138">執行 Operation Server，方式如下：</span><span class="sxs-lookup"><span data-stu-id="29924-138">Run the Operation Server as follows:</span></span>  
  
    1.  <span data-ttu-id="29924-139">開啟新的命令提示字元，將目前的目錄變更為 %BTSSolutionsPath%\BPM\OperationsServer\bin\debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29924-139">Open a new command prompt, change the current directory to the %BTSSolutionsPath%\BPM\OperationsServer\bin\debug folder.</span></span>  
  
    2.  <span data-ttu-id="29924-140">型別`BTSScnBPMOperations.exe 8881`在命令提示字元中，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="29924-140">Type `BTSScnBPMOperations.exe 8881` at the command prompt, and then press ENTER.</span></span> <span data-ttu-id="29924-141">讓 Operation Server 繼續執行。</span><span class="sxs-lookup"><span data-stu-id="29924-141">Keep the Operation Server running.</span></span> <span data-ttu-id="29924-142">Operation Server 會監聽 TCP 連接埠 8881，以接收來自 Ops 配接器的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-142">The Operation Server listens on the TCP port, 8881, to receive error messages from the Ops Adapter.</span></span> <span data-ttu-id="29924-143">它會顯示 Ops 配接器接收的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-143">It displays the error messages received by the Ops Adapter.</span></span>  
  
6.  <span data-ttu-id="29924-144">執行 Cable Provisioning System，方式如下：</span><span class="sxs-lookup"><span data-stu-id="29924-144">Run the Cable Provisioning System as follows:</span></span>  
  
    1.  <span data-ttu-id="29924-145">開啟新的命令提示字元，將目前目錄變更到 %BTSSolutionsPath%\BPM\CableProvisioningSystemServer\bin\debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29924-145">Open a new command prompt, change the current directory to the %BTSSolutionsPath%\BPM\CableProvisioningSystemServer\bin\debug folder.</span></span>  
  
    2.  <span data-ttu-id="29924-146">輸入 `BTSScnBPMProvisioning.exe 8880`，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="29924-146">Type `BTSScnBPMProvisioning.exe 8880`, and then press ENTER.</span></span> <span data-ttu-id="29924-147">然後，讓 Cable Provisioning System 繼續執行。</span><span class="sxs-lookup"><span data-stu-id="29924-147">Then, keep the Cable Provisioning System running.</span></span> <span data-ttu-id="29924-148">Cable Provisioning System 會接聽 TCP 連接埠 8880。</span><span class="sxs-lookup"><span data-stu-id="29924-148">The Cable Provisioning System listens on the TCP port, 8880.</span></span> <span data-ttu-id="29924-149">此應用程式會模擬後端訂單系統，並顯示最終的訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-149">This application simulates a back-end order system, and displays the final orders.</span></span>  
  
##  <a name="step3"></a><span data-ttu-id="29924-150">執行和驗證商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="29924-150">Run and validate the Business Process Management Solution</span></span>  
  
#### <a name="to-submit-a-new-order-and-validate-the-solution"></a><span data-ttu-id="29924-151">提交新訂單和驗證解決方案</span><span class="sxs-lookup"><span data-stu-id="29924-151">To submit a new order and validate the solution</span></span>  
  
1.  <span data-ttu-id="29924-152">在 Internet Explorer 中**位址**方塊中，輸入客戶服務 Web 應用程式的 URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-152">In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:</span></span>  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  <span data-ttu-id="29924-153">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，輸入下表中的新訂單，然後按一下**提交訂單。**</span><span class="sxs-lookup"><span data-stu-id="29924-153">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order.**</span></span>  
  
    |<span data-ttu-id="29924-154">項目</span><span class="sxs-lookup"><span data-stu-id="29924-154">Entry</span></span>|<span data-ttu-id="29924-155">值</span><span class="sxs-lookup"><span data-stu-id="29924-155">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="29924-156">客戶識別碼</span><span class="sxs-lookup"><span data-stu-id="29924-156">Customer ID</span></span>|<span data-ttu-id="29924-157">1</span><span class="sxs-lookup"><span data-stu-id="29924-157">1</span></span>|  
    |<span data-ttu-id="29924-158">Order ID</span><span class="sxs-lookup"><span data-stu-id="29924-158">Order ID</span></span>|<span data-ttu-id="29924-159">1</span><span class="sxs-lookup"><span data-stu-id="29924-159">1</span></span>|  
    |<span data-ttu-id="29924-160">序號</span><span class="sxs-lookup"><span data-stu-id="29924-160">Sequence Number</span></span>|<span data-ttu-id="29924-161">1</span><span class="sxs-lookup"><span data-stu-id="29924-161">1</span></span>|  
    |<span data-ttu-id="29924-162">服務類型碼</span><span class="sxs-lookup"><span data-stu-id="29924-162">Service Type Code</span></span>|<span data-ttu-id="29924-163">新標準服務</span><span class="sxs-lookup"><span data-stu-id="29924-163">New Standard Service</span></span>|  
  
3.  <span data-ttu-id="29924-164">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-164">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="29924-165">**客戶識別碼 1 訂單識別碼 1 序號 1**</span><span class="sxs-lookup"><span data-stu-id="29924-165">**Customer ID 1 Order ID 1 Sequence Number 1**</span></span>  
  
4.  <span data-ttu-id="29924-166">在執行 Cable Provisioning System 的命令提示字元驗證提出的訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-166">Validate that the placed order at the command prompt running the Cable Provisioning System.</span></span> <span data-ttu-id="29924-167">應用程式會顯示提交的訂單已分析、啟動並完成的訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-167">The application display the messages that the submitted order is analyzed, activated, and then completed.</span></span>  
  
5.  <span data-ttu-id="29924-168">確認在 Facilities Simulator 上的總訊息數目是否增加 1。</span><span class="sxs-lookup"><span data-stu-id="29924-168">Validate that the number of the total messages is incremented by one on the Facilities Simulator.</span></span>  
  
#### <a name="to-submit-a-duplicate-while-the-biztalk-server-is-processing-the-original-order"></a><span data-ttu-id="29924-169">在 BizTalk Server 處理原始訂單時提交重複的訂單</span><span class="sxs-lookup"><span data-stu-id="29924-169">To submit a duplicate while the BizTalk Server is processing the original order</span></span>  
  
1.  <span data-ttu-id="29924-170">在 Internet Explorer 中**位址**方塊中，輸入客戶服務 Web 應用程式的 URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-170">In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:</span></span>  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  <span data-ttu-id="29924-171">在 FacilitiesSimulator 中按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="29924-171">In the FacilitiesSimulator, click **Stop**.</span></span> <span data-ttu-id="29924-172">可防止進一步處理提交的訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-172">It prevents submitted orders from being processed further.</span></span>  
  
3.  <span data-ttu-id="29924-173">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，輸入下表中的新訂單，然後按一下**提交訂單**兩次，以模擬重複的訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-173">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order** twice to simulate duplicated orders.</span></span>  
  
    |<span data-ttu-id="29924-174">項目</span><span class="sxs-lookup"><span data-stu-id="29924-174">Entry</span></span>|<span data-ttu-id="29924-175">值</span><span class="sxs-lookup"><span data-stu-id="29924-175">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="29924-176">客戶識別碼</span><span class="sxs-lookup"><span data-stu-id="29924-176">Customer ID</span></span>|<span data-ttu-id="29924-177">2</span><span class="sxs-lookup"><span data-stu-id="29924-177">2</span></span>|  
    |<span data-ttu-id="29924-178">Order ID</span><span class="sxs-lookup"><span data-stu-id="29924-178">Order ID</span></span>|<span data-ttu-id="29924-179">1</span><span class="sxs-lookup"><span data-stu-id="29924-179">1</span></span>|  
    |<span data-ttu-id="29924-180">序號</span><span class="sxs-lookup"><span data-stu-id="29924-180">Sequence Number</span></span>|<span data-ttu-id="29924-181">1</span><span class="sxs-lookup"><span data-stu-id="29924-181">1</span></span>|  
    |<span data-ttu-id="29924-182">服務類型碼</span><span class="sxs-lookup"><span data-stu-id="29924-182">Service Type Code</span></span>|<span data-ttu-id="29924-183">新標準服務</span><span class="sxs-lookup"><span data-stu-id="29924-183">New Standard Service</span></span>|  
  
4.  <span data-ttu-id="29924-184">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-184">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="29924-185">**客戶識別碼 2 訂單識別碼 1 序號 1**</span><span class="sxs-lookup"><span data-stu-id="29924-185">**Customer ID 2 Order ID 1 Sequence Number 1**</span></span>  
  
5.  <span data-ttu-id="29924-186">在 FacilitiesSimulator 中按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="29924-186">In the FacilitiesSimulator, click **Start**.</span></span> <span data-ttu-id="29924-187">等待 Facilities Simulator 回應的協調流程將會繼續。</span><span class="sxs-lookup"><span data-stu-id="29924-187">The orchestrations waiting for the responses from the Facilities Simulator will resume.</span></span> <span data-ttu-id="29924-188">它會模擬在處理第一個訂單時提交重複的訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-188">It simulates that a duplicate order is submitted while the first order is being processed.</span></span>  
  
6.  <span data-ttu-id="29924-189">在執行 Cable Provisioning System 的命令提示字元檢查提出的訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-189">Check the placed orders at the command prompt running the Cable Provisioning System.</span></span> <span data-ttu-id="29924-190">應用程式會顯示只有第一個訂單已分析、啟動並完成的訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-190">The application displays the messages that only the first order is analyzed, activated, and then completed.</span></span>  
  
7.  <span data-ttu-id="29924-191">在執行 Operation Server 的命令提示字元檢查重複訂單的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-191">Check the error message for the duplicated orders at the command prompt running the Operation Server.</span></span>  
  
#### <a name="to-update-an-order-while-the-biztalk-server-is-processing-the-order"></a><span data-ttu-id="29924-192">在 BizTalk Server 處理訂單時更新訂單</span><span class="sxs-lookup"><span data-stu-id="29924-192">To update an order while the BizTalk Server is processing the order</span></span>  
  
1.  <span data-ttu-id="29924-193">在 Internet Explorer 中**位址**方塊中，輸入客戶服務 Web 應用程式的 URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-193">In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:</span></span>  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  <span data-ttu-id="29924-194">在 FacilitiesSimulator 中按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="29924-194">In the FacilitiesSimulator, click **Stop**.</span></span>  
  
3.  <span data-ttu-id="29924-195">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，輸入下表中的新訂單，然後按一下**提交訂單**。</span><span class="sxs-lookup"><span data-stu-id="29924-195">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order**.</span></span>  
  
    |<span data-ttu-id="29924-196">項目</span><span class="sxs-lookup"><span data-stu-id="29924-196">Entry</span></span>|<span data-ttu-id="29924-197">值</span><span class="sxs-lookup"><span data-stu-id="29924-197">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="29924-198">客戶識別碼</span><span class="sxs-lookup"><span data-stu-id="29924-198">Customer ID</span></span>|<span data-ttu-id="29924-199">3</span><span class="sxs-lookup"><span data-stu-id="29924-199">3</span></span>|  
    |<span data-ttu-id="29924-200">Order ID</span><span class="sxs-lookup"><span data-stu-id="29924-200">Order ID</span></span>|<span data-ttu-id="29924-201">1</span><span class="sxs-lookup"><span data-stu-id="29924-201">1</span></span>|  
    |<span data-ttu-id="29924-202">序號</span><span class="sxs-lookup"><span data-stu-id="29924-202">Sequence Number</span></span>|<span data-ttu-id="29924-203">1</span><span class="sxs-lookup"><span data-stu-id="29924-203">1</span></span>|  
    |<span data-ttu-id="29924-204">服務類型碼</span><span class="sxs-lookup"><span data-stu-id="29924-204">Service Type Code</span></span>|<span data-ttu-id="29924-205">新標準服務</span><span class="sxs-lookup"><span data-stu-id="29924-205">New Standard Service</span></span>|  
  
4.  <span data-ttu-id="29924-206">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-206">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="29924-207">**客戶識別碼 3 訂單識別碼 1 序號 1**</span><span class="sxs-lookup"><span data-stu-id="29924-207">**Customer ID 3 Order ID 1 Sequence Number 1**</span></span>  
  
5.  <span data-ttu-id="29924-208">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，輸入下表中更新的訂單，然後按一下**提交訂單**。</span><span class="sxs-lookup"><span data-stu-id="29924-208">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter an updated order in the following table, and then click **Submit Order**.</span></span>  
  
    |<span data-ttu-id="29924-209">項目</span><span class="sxs-lookup"><span data-stu-id="29924-209">Entry</span></span>|<span data-ttu-id="29924-210">值</span><span class="sxs-lookup"><span data-stu-id="29924-210">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="29924-211">客戶識別碼</span><span class="sxs-lookup"><span data-stu-id="29924-211">Customer ID</span></span>|<span data-ttu-id="29924-212">3</span><span class="sxs-lookup"><span data-stu-id="29924-212">3</span></span>|  
    |<span data-ttu-id="29924-213">Order ID</span><span class="sxs-lookup"><span data-stu-id="29924-213">Order ID</span></span>|<span data-ttu-id="29924-214">1</span><span class="sxs-lookup"><span data-stu-id="29924-214">1</span></span>|  
    |<span data-ttu-id="29924-215">序號</span><span class="sxs-lookup"><span data-stu-id="29924-215">Sequence Number</span></span>|<span data-ttu-id="29924-216">2</span><span class="sxs-lookup"><span data-stu-id="29924-216">2</span></span>|  
    |<span data-ttu-id="29924-217">服務類型碼</span><span class="sxs-lookup"><span data-stu-id="29924-217">Service Type Code</span></span>|<span data-ttu-id="29924-218">新個性化服務</span><span class="sxs-lookup"><span data-stu-id="29924-218">New Deluxe Service</span></span>|  
  
6.  <span data-ttu-id="29924-219">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-219">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="29924-220">**客戶識別碼 3 訂單識別碼 1 序號 2**</span><span class="sxs-lookup"><span data-stu-id="29924-220">**Customer ID 3 Order ID 1 Sequence Number 2**</span></span>  
  
7.  <span data-ttu-id="29924-221">在 FacilitiesSimulator 中按一下**開始**</span><span class="sxs-lookup"><span data-stu-id="29924-221">In the FacilitiesSimulator, click **Start**</span></span>  
  
8.  <span data-ttu-id="29924-222">檢查結果訊息**Southridge Video 客戶服務代表訂單項目表單**頁面。</span><span class="sxs-lookup"><span data-stu-id="29924-222">Check the result message on the **Southridge Video Customer Service Rep Order Entry Form** page.</span></span>  
  
9. <span data-ttu-id="29924-223">在執行 Cable Provisioning System 的命令提示字元檢查提出的訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-223">Check the placed orders at the command prompt running the Cable Provisioning System.</span></span> <span data-ttu-id="29924-224">應用程式會顯示已經分析兩個訂單，但僅啟動和完成更新訂單的訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-224">The application displays the messages that two orders are analyzed, but only the updated order is activated and completed.</span></span>  
  
10. <span data-ttu-id="29924-225">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，按一下**事件檢視器**，則會有新的警告，然後核取原始訂單已中斷。</span><span class="sxs-lookup"><span data-stu-id="29924-225">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Event Viewer**, and then check a new warning that the original order was interrupted.</span></span>  
  
11. <span data-ttu-id="29924-226">在執行 Operation Server 的命令提示字元檢查路由失敗錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-226">Checked the routing failure error message at the command prompt running the Operation Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29924-227">事件日誌和 Operation Server 中將會有錯誤。</span><span class="sxs-lookup"><span data-stu-id="29924-227">There will be an error in the event log and in the operations server.</span></span> <span data-ttu-id="29924-228">Facilities System 的回應訊息與商務程序的執行個體不再相互關聯，因為序號較高的新訂單造成中斷而使它終止。</span><span class="sxs-lookup"><span data-stu-id="29924-228">The response message from the Facilities System no longer correlates back to an instance of the business process as it was terminated by the interruption caused by the new order with a higher sequence number.</span></span> <span data-ttu-id="29924-229">因此，回應訊息便被遺棄，將會路由至 Operation Server。</span><span class="sxs-lookup"><span data-stu-id="29924-229">Therefore response message is orphaned and will get routed to the operations server.</span></span> <span data-ttu-id="29924-230">如需訂單更新的詳細資訊，請參閱[訂單流程的程序管理員透過](../core/order-flow-through-the-process-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="29924-230">For more information about order updates, see [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).</span></span>  
  
12. <span data-ttu-id="29924-231">使用「記事本」開啟 %SystemDrive%:\BPMTest\HistoryUpdate-SP 資料夾中的最新訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-231">Open the latest message in the %SystemDrive%:\BPMTest\HistoryUpdate-SP folder with Notepad.</span></span> <span data-ttu-id="29924-232">請檢查**CustName**， **OrderNum**， **OrderSeqNum**，和**狀態**欄位，以查看是否已經建立新的訂單訊息，**狀態**欄位是**已完成**。</span><span class="sxs-lookup"><span data-stu-id="29924-232">Check **CustName**, **OrderNum**, **OrderSeqNum**, and **Status** fields to see if the message has been created for the new order and the **Status** field is **COMPLETED**.</span></span>  
  
#### <a name="to-terminate-an-order-while-the-biztalk-server-is-processing-the-order"></a><span data-ttu-id="29924-233">在 BizTalk Server 處理訂單時終止訂單</span><span class="sxs-lookup"><span data-stu-id="29924-233">To terminate an order while the BizTalk Server is processing the order</span></span>  
  
1.  <span data-ttu-id="29924-234">在 Internet Explorer 中**位址**方塊中，輸入客戶服務 Web 應用程式的 URL 如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-234">In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:</span></span>  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  <span data-ttu-id="29924-235">在 FacilitiesSimulator 中按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="29924-235">In the FacilitiesSimulator, click **Stop**.</span></span>  
  
3.  <span data-ttu-id="29924-236">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，輸入下表中的新訂單，然後按一下**提交訂單**。</span><span class="sxs-lookup"><span data-stu-id="29924-236">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order**.</span></span>  
  
    |<span data-ttu-id="29924-237">項目</span><span class="sxs-lookup"><span data-stu-id="29924-237">Entry</span></span>|<span data-ttu-id="29924-238">值</span><span class="sxs-lookup"><span data-stu-id="29924-238">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="29924-239">客戶識別碼</span><span class="sxs-lookup"><span data-stu-id="29924-239">Customer ID</span></span>|<span data-ttu-id="29924-240">4</span><span class="sxs-lookup"><span data-stu-id="29924-240">4</span></span>|  
    |<span data-ttu-id="29924-241">Order ID</span><span class="sxs-lookup"><span data-stu-id="29924-241">Order ID</span></span>|<span data-ttu-id="29924-242">1</span><span class="sxs-lookup"><span data-stu-id="29924-242">1</span></span>|  
    |<span data-ttu-id="29924-243">序號</span><span class="sxs-lookup"><span data-stu-id="29924-243">Sequence Number</span></span>|<span data-ttu-id="29924-244">1</span><span class="sxs-lookup"><span data-stu-id="29924-244">1</span></span>|  
    |<span data-ttu-id="29924-245">服務類型碼</span><span class="sxs-lookup"><span data-stu-id="29924-245">Service Type Code</span></span>|<span data-ttu-id="29924-246">新標準服務</span><span class="sxs-lookup"><span data-stu-id="29924-246">New Standard Service</span></span>|  
  
4.  <span data-ttu-id="29924-247">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-247">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="29924-248">**客戶識別碼 4 訂單識別碼 1 序號 1**</span><span class="sxs-lookup"><span data-stu-id="29924-248">**Customer ID 4 Order ID 1 Sequence Number 1**</span></span>  
  
5.  <span data-ttu-id="29924-249">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，按一下**終止訂單**。</span><span class="sxs-lookup"><span data-stu-id="29924-249">On the **Southridge Video Customer Service Rep Order Entry Form** page, click **Terminate Order**.</span></span>  
  
6.  <span data-ttu-id="29924-250">在**Southridge Video 客戶服務代表訂單項目表單**頁面上，結果訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="29924-250">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="29924-251">**客戶識別碼 4 訂單識別碼 1 序號 1**</span><span class="sxs-lookup"><span data-stu-id="29924-251">**Customer ID 4 Order ID 1 Sequence Number 1**</span></span>  
  
7.  <span data-ttu-id="29924-252">在 FacilitiesSimulator 中按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="29924-252">In the FacilitiesSimulator, click **Start**.</span></span>  
  
8.  <span data-ttu-id="29924-253">在執行 Cable Provisioning System 的命令提示字元檢查提出的訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-253">Check the placed orders at the command prompt running the Cable Provisioning System.</span></span> <span data-ttu-id="29924-254">應用程式會顯示僅分析和啟動訂單的訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-254">The application displays the messages that order is only analyzed and activated.</span></span>  
  
9. <span data-ttu-id="29924-255">按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，按一下**事件檢視器**，則會有新的警告，然後核取使用者已終止訂單。</span><span class="sxs-lookup"><span data-stu-id="29924-255">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Event Viewer**, and then check a new warning that the order was terminated by user.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29924-256">如需終止訂單的詳細資訊，請參閱[訂單流程的程序管理員透過](../core/order-flow-through-the-process-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="29924-256">For more information about terminating orders, see [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).</span></span>  
  
10. <span data-ttu-id="29924-257">在執行 Operation Server 的命令提示字元檢查路由失敗錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="29924-257">Checked the routing failure error message at the command prompt running the Operation Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29924-258">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29924-258">See Also</span></span>  
 <span data-ttu-id="29924-259">[安裝商務程序管理解決方案之前](../core/before-installing-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="29924-259">[Before Installing the Business Process Management Solution](../core/before-installing-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="29924-260">商務程序管理解決方案的開發人員電腦設定</span><span class="sxs-lookup"><span data-stu-id="29924-260">Developer Machine Setup for the Business Process Management Solution</span></span>](../core/developer-machine-setup-for-the-business-process-management-solution.md)