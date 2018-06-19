---
title: 步驟 3B： 新增 FILEACT 接收位置 FileAct 存放與轉寄案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f30bb7d-1efb-4350-8809-be35f5634ea0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9357c172ff538bce73d3618739f3db4f98141814
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965228"
---
# <a name="step-3b-add-a-fileact-receive-location-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="74778-102">步驟 3B： 新增 FILEACT 接收位置 FileAct 存放與轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="74778-102">Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="74778-103">在開始此步驟之前，必須先完成[步驟 3A： 新增檔案接收位置為 FileAct 存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="74778-103">Before you begin this step, you must complete [Step 3A: Add a FILE Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-an-fileact-receive-location"></a><span data-ttu-id="74778-104">若要加入 FILEACT 接收位置</span><span class="sxs-lookup"><span data-stu-id="74778-104">To add an FILEACT receive location</span></span>  
  
1.  <span data-ttu-id="74778-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="74778-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="74778-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="74778-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="74778-107">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="74778-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="74778-108">在**接收埠屬性**視窗中，接收埠，Tutorial_FA_HandleRequestOneWay_SnF。</span><span class="sxs-lookup"><span data-stu-id="74778-108">In the **Receive Port Properties** window, name the receive port, Tutorial_FA_HandleRequestOneWay_SnF.</span></span>  
  
5.  <span data-ttu-id="74778-109">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="74778-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="74778-110">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**FILEACT**，和然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="74778-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILEACT**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="74778-111">在**FILEACT 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="74778-111">In the **FILEACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="74778-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="74778-112">**Use this**</span></span>|<span data-ttu-id="74778-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="74778-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="74778-114">**密碼**</span><span class="sxs-lookup"><span data-stu-id="74778-114">**Password**</span></span>|<span data-ttu-id="74778-115">輸入您用來連接到 SAG 的密碼。</span><span class="sxs-lookup"><span data-stu-id="74778-115">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="74778-116">如需詳細資訊，請參閱 SAG 說明。</span><span class="sxs-lookup"><span data-stu-id="74778-116">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="74778-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="74778-117">**User name**</span></span>|<span data-ttu-id="74778-118">輸入您用來連接到 SAG 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="74778-118">Type the user name you use to connect to SAG.</span></span>|  
    |<span data-ttu-id="74778-119">**應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="74778-119">**Application name**</span></span>|<span data-ttu-id="74778-120">輸入伺服器\<應用程式的介面名稱\>SAG 的方塊路由的集合。</span><span class="sxs-lookup"><span data-stu-id="74778-120">Type the Server \<Application Interface Name\> for the SAG box routing set.</span></span>|  
    |<span data-ttu-id="74778-121">**密碼編譯模式**</span><span class="sxs-lookup"><span data-stu-id="74778-121">**Crypto Mode**</span></span>|<span data-ttu-id="74778-122">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="74778-122">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="74778-123">**FACrypto 模式**</span><span class="sxs-lookup"><span data-stu-id="74778-123">**FACrypto Mode**</span></span>|<span data-ttu-id="74778-124">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="74778-124">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="74778-125">**記錄訊息**</span><span class="sxs-lookup"><span data-stu-id="74778-125">**LogMessages**</span></span>|<span data-ttu-id="74778-126">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="74778-126">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="74778-127">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="74778-127">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="74778-128">**MemberRef**</span><span class="sxs-lookup"><span data-stu-id="74778-128">**MemberRef**</span></span>|<span data-ttu-id="74778-129">從下拉式清單選取**ResponsePayload**。</span><span class="sxs-lookup"><span data-stu-id="74778-129">From the drop-down list, select **ResponsePayload**.</span></span>|  
    |<span data-ttu-id="74778-130">**不可否認性指標**</span><span class="sxs-lookup"><span data-stu-id="74778-130">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="74778-131">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="74778-131">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="74778-132">**回應者**</span><span class="sxs-lookup"><span data-stu-id="74778-132">**Responder**</span></span>|<span data-ttu-id="74778-133">輸入適當\<回應\>SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="74778-133">Type the appropriate \<Responder\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="74778-134">**ResponseCrypto**</span><span class="sxs-lookup"><span data-stu-id="74778-134">**ResponseCrypto**</span></span>|<span data-ttu-id="74778-135">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="74778-135">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="74778-136">**通知標記**</span><span class="sxs-lookup"><span data-stu-id="74778-136">**Acknowledgement Indicator**</span></span>|<span data-ttu-id="74778-137">從下拉式清單選取**ResponsePayload**。</span><span class="sxs-lookup"><span data-stu-id="74778-137">From the drop-down list, select **ResponsePayload**.</span></span>|  
    |<span data-ttu-id="74778-138">**FileCompression**</span><span class="sxs-lookup"><span data-stu-id="74778-138">**FileCompression**</span></span>|<span data-ttu-id="74778-139">從下拉式清單中，選取 [無]。</span><span class="sxs-lookup"><span data-stu-id="74778-139">From the drop-down list, select None.</span></span>|  
    |<span data-ttu-id="74778-140">**PhysicalFolderName**</span><span class="sxs-lookup"><span data-stu-id="74778-140">**PhysicalFolderName**</span></span>|<span data-ttu-id="74778-141">在伺服器上，輸入資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="74778-141">Type the name of the folder on the server.</span></span> <span data-ttu-id="74778-142">例如，C:\Fileact\ServerLocation。</span><span class="sxs-lookup"><span data-stu-id="74778-142">For example, C:\Fileact\ServerLocation.</span></span>|  
    |<span data-ttu-id="74778-143">**SubscribeFileEvents**</span><span class="sxs-lookup"><span data-stu-id="74778-143">**SubscribeFileEvents**</span></span>|<span data-ttu-id="74778-144">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="74778-144">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="74778-145">**TransferAnswer**</span><span class="sxs-lookup"><span data-stu-id="74778-145">**TransferAnswer**</span></span>|<span data-ttu-id="74778-146">從下拉式清單選取**接受**。</span><span class="sxs-lookup"><span data-stu-id="74778-146">From the drop-down list, select **Accepted**.</span></span>|  
    |<span data-ttu-id="74778-147">**AllFileEvents**</span><span class="sxs-lookup"><span data-stu-id="74778-147">**AllFileEvents**</span></span>|<span data-ttu-id="74778-148">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="74778-148">From the drop-down list, select **TRUE**.</span></span>|  
    |<span data-ttu-id="74778-149">**事件端點**</span><span class="sxs-lookup"><span data-stu-id="74778-149">**Event end-point**</span></span>|<span data-ttu-id="74778-150">輸入適當的 SAG 端點。</span><span class="sxs-lookup"><span data-stu-id="74778-150">Type the appropriate SAG end-point.</span></span>|  
    |<span data-ttu-id="74778-151">**FullFileStatus**</span><span class="sxs-lookup"><span data-stu-id="74778-151">**FullFileStatus**</span></span>|<span data-ttu-id="74778-152">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="74778-152">From the drop-down list, select **TRUE**.</span></span>|  
    |<span data-ttu-id="74778-153">**逾時**</span><span class="sxs-lookup"><span data-stu-id="74778-153">**Timeout**</span></span>|<span data-ttu-id="74778-154">輸入適當應該發生逾時之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="74778-154">Type an appropriate number of seconds before timeout should occur.</span></span>|  
    |<span data-ttu-id="74778-155">**取得佇列**</span><span class="sxs-lookup"><span data-stu-id="74778-155">**Acquire queue**</span></span>|<span data-ttu-id="74778-156">輸入佇列的名稱，根據 SWIFT 與您佈建。</span><span class="sxs-lookup"><span data-stu-id="74778-156">Type the queue name, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="74778-157">**ForceAcquire**</span><span class="sxs-lookup"><span data-stu-id="74778-157">**ForceAcquire**</span></span>|<span data-ttu-id="74778-158">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="74778-158">From the drop-down list, select **TRUE**.</span></span>|  
    |<span data-ttu-id="74778-159">**排序依據**</span><span class="sxs-lookup"><span data-stu-id="74778-159">**Order by**</span></span>|<span data-ttu-id="74778-160">從下拉式清單選取**FileAct**。</span><span class="sxs-lookup"><span data-stu-id="74778-160">From the drop-down list, select **FileAct**.</span></span>|  
    |<span data-ttu-id="74778-161">**推入工作階段**</span><span class="sxs-lookup"><span data-stu-id="74778-161">**Push session**</span></span>|<span data-ttu-id="74778-162">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="74778-162">From the drop-down list, select **TRUE**.</span></span>|  
    |<span data-ttu-id="74778-163">**復原模式**</span><span class="sxs-lookup"><span data-stu-id="74778-163">**Recovery mode**</span></span>|<span data-ttu-id="74778-164">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="74778-164">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="74778-165">**SNL 端點**</span><span class="sxs-lookup"><span data-stu-id="74778-165">**SNL end-point**</span></span>|<span data-ttu-id="74778-166">輸入適當的端點 SAG 路由集合。</span><span class="sxs-lookup"><span data-stu-id="74778-166">Type the appropriate end-point for the SAG routing set.</span></span> <span data-ttu-id="74778-167">這個值應該符合您設定在 SAG SnL 端點。</span><span class="sxs-lookup"><span data-stu-id="74778-167">This value should match the SnL endpoint you configured in SAG.</span></span>|  
  
8.  <span data-ttu-id="74778-168">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="74778-168">Click **OK**.</span></span>  
  
9. <span data-ttu-id="74778-169">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="74778-169">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="74778-170">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="74778-170">**Use this**</span></span>|<span data-ttu-id="74778-171">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="74778-171">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="74778-172">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="74778-172">**Receive handler**</span></span>|<span data-ttu-id="74778-173">從下拉式清單選取**BizTalkServerIsolatedHost**。</span><span class="sxs-lookup"><span data-stu-id="74778-173">From the drop-down list, select **BizTalkServerIsolatedHost**.</span></span>|  
    |<span data-ttu-id="74778-174">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="74778-174">**Receive pipeline**</span></span>|<span data-ttu-id="74778-175">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="74778-175">From the drop-down list, select **XMLReceive**.</span></span>|  
  
10. <span data-ttu-id="74778-176">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="74778-176">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74778-177">請參閱</span><span class="sxs-lookup"><span data-stu-id="74778-177">See Also</span></span>  
 <span data-ttu-id="74778-178">[步驟 3： 建立傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="74778-178">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 <span data-ttu-id="74778-179">[步驟 3A： 新增 FILE 接收位置為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="74778-179">[Step 3A: Add a FILE Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="74778-180">[步驟 3c： 加入擷取 FileAct 存放與轉寄案例的 Sw:HandleFileRequest 和 Sw:HandleSnFRequest 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md) </span><span class="sxs-lookup"><span data-stu-id="74778-180">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md) </span></span>  
 [<span data-ttu-id="74778-181">步驟 3D：針對 FileAct 儲存和轉寄案例新增 FILEACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="74778-181">Step 3D: Add a FILEACT Send Port for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)