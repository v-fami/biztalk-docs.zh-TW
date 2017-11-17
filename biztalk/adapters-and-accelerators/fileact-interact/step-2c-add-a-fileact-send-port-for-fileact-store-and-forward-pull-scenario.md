---
title: "步驟 2c： 新增 FILEACT 傳送埠為 FileAct 存放與轉寄 （提取） 實例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8743a868-9625-477b-a7da-673bfa262723
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55db4fcd1a6a65ac9058a69f9c315de593181a65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2c-add-a-fileact-send-port-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="e898f-102">步驟 2c： 新增為 FileAct 存放與轉寄 （提取） 實例 FILEACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="e898f-102">Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="e898f-103">在開始此步驟之前，必須先完成[步驟 2B： 將檔案傳送埠來擷取 Sw:HandleFileRequest 和 FileAct 存放與轉寄 （提取） 案例的 Sw:HandleSnFRequest 訊息](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)。</span><span class="sxs-lookup"><span data-stu-id="e898f-103">Before you begin this step, you must complete [Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md).</span></span>  
  
### <a name="to-add-a-fileact-send-port"></a><span data-ttu-id="e898f-104">若要新增 FileACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="e898f-104">To add a FileACT send port</span></span>  
  
1.  <span data-ttu-id="e898f-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e898f-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e898f-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e898f-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="e898f-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="e898f-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
4.  <span data-ttu-id="e898f-108">在**傳送埠屬性**視窗中，傳送埠， **Tutorial_FA_SendRequest_SnF**。</span><span class="sxs-lookup"><span data-stu-id="e898f-108">In the **Send Port Properties** window, name the send port, **Tutorial_FA_SendRequest_SnF**.</span></span>  
  
5.  <span data-ttu-id="e898f-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**FILEACT**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="e898f-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILEACT**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="e898f-110">在**FILEACT 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e898f-110">In the **FILEACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="e898f-111">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="e898f-111">**Use this**</span></span>|<span data-ttu-id="e898f-112">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="e898f-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="e898f-113">**密碼**</span><span class="sxs-lookup"><span data-stu-id="e898f-113">**Password**</span></span>|<span data-ttu-id="e898f-114">視 SAG 連線設定的密碼。</span><span class="sxs-lookup"><span data-stu-id="e898f-114">Set the password as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="e898f-115">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="e898f-115">**User name**</span></span>|<span data-ttu-id="e898f-116">視 SAG 連線設定的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e898f-116">Set the user name as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="e898f-117">**配接器模式**</span><span class="sxs-lookup"><span data-stu-id="e898f-117">**Adapter Mode**</span></span>|<span data-ttu-id="e898f-118">從下拉式清單選取**存放與轉寄**。</span><span class="sxs-lookup"><span data-stu-id="e898f-118">From the drop-down list, select **Store and Forward**.</span></span>|  
    |<span data-ttu-id="e898f-119">**不可否認性指標**</span><span class="sxs-lookup"><span data-stu-id="e898f-119">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="e898f-120">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="e898f-120">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="e898f-121">**要求類型**</span><span class="sxs-lookup"><span data-stu-id="e898f-121">**Request Type**</span></span>|<span data-ttu-id="e898f-122">設定為適當\<RequestType > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="e898f-122">Set to the appropriate \<RequestType> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="e898f-123">**RequestCrypto**</span><span class="sxs-lookup"><span data-stu-id="e898f-123">**RequestCrypto**</span></span>|<span data-ttu-id="e898f-124">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="e898f-124">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="e898f-125">**要求者**</span><span class="sxs-lookup"><span data-stu-id="e898f-125">**Requestor**</span></span>|<span data-ttu-id="e898f-126">設定為適當\<要求者 > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="e898f-126">Set to the appropriate \<Requestor> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="e898f-127">**回應者**</span><span class="sxs-lookup"><span data-stu-id="e898f-127">**Responder**</span></span>|<span data-ttu-id="e898f-128">設定為適當\<回應 > 字串。</span><span class="sxs-lookup"><span data-stu-id="e898f-128">Set to the appropriate \<Responder> string.</span></span>|  
    |<span data-ttu-id="e898f-129">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="e898f-129">**Service Name**</span></span>|<span data-ttu-id="e898f-130">設定為適當**\<服務名稱 >**。</span><span class="sxs-lookup"><span data-stu-id="e898f-130">Set to the appropriate **\<service name>**.</span></span>|  
    |<span data-ttu-id="e898f-131">**通知標記**</span><span class="sxs-lookup"><span data-stu-id="e898f-131">**Acknowledgement Indicator**</span></span>|<span data-ttu-id="e898f-132">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="e898f-132">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="e898f-133">**事件端點**</span><span class="sxs-lookup"><span data-stu-id="e898f-133">**Event end-point**</span></span>|<span data-ttu-id="e898f-134">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="e898f-134">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="e898f-135">**檔案壓縮**</span><span class="sxs-lookup"><span data-stu-id="e898f-135">**File Compression**</span></span>|<span data-ttu-id="e898f-136">從下拉式清單選取**無**。</span><span class="sxs-lookup"><span data-stu-id="e898f-136">From the drop-down list, select **None**.</span></span>|  
    |<span data-ttu-id="e898f-137">**實體的資料夾名稱**</span><span class="sxs-lookup"><span data-stu-id="e898f-137">**Physical Folder Name**</span></span>|<span data-ttu-id="e898f-138">輸入 C:\SWIFTAdapterTutorial\Fileact\ClientLocation。</span><span class="sxs-lookup"><span data-stu-id="e898f-138">Type C:\SWIFTAdapterTutorial\Fileact\ClientLocation.</span></span>|  
    |<span data-ttu-id="e898f-139">**轉送端點**</span><span class="sxs-lookup"><span data-stu-id="e898f-139">**Transfer end-point**</span></span>|<span data-ttu-id="e898f-140">輸入適當的端點 SAG 路由集合。</span><span class="sxs-lookup"><span data-stu-id="e898f-140">Type the appropriate end-point for the SAG routing set.</span></span> <span data-ttu-id="e898f-141">這個值應該符合您設定在 SAG SNL 端點。</span><span class="sxs-lookup"><span data-stu-id="e898f-141">This value should match the SNL endpoint you configured in SAG.</span></span>|  
    |<span data-ttu-id="e898f-142">**ServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="e898f-142">**ServiceProfile**</span></span>|<span data-ttu-id="e898f-143">從下拉式清單選取**交易計數**。</span><span class="sxs-lookup"><span data-stu-id="e898f-143">From the drop-down list, select **Transaction Count**.</span></span>|  
    |<span data-ttu-id="e898f-144">**傳遞通知**</span><span class="sxs-lookup"><span data-stu-id="e898f-144">**Delivery notification**</span></span>|<span data-ttu-id="e898f-145">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="e898f-145">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="e898f-146">**通知佇列**</span><span class="sxs-lookup"><span data-stu-id="e898f-146">**Notify queue**</span></span>|<span data-ttu-id="e898f-147">輸入佇列的名稱，根據 SWIFT 與您佈建。</span><span class="sxs-lookup"><span data-stu-id="e898f-147">Type the queue name, based on your provisioning with SWIFT.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="e898f-148">如果要傳送訊息的交易計數，服務設定檔中設定模式以 「 交易計數 」 FileAct 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e898f-148">If message with Transaction Count is to be transferred, set the Service Profile Mode to “Transaction Count” in the FileAct send port.</span></span>  
  
7.  <span data-ttu-id="e898f-149">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e898f-149">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="e898f-150">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e898f-150">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="e898f-151">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="e898f-151">**Use this**</span></span>|<span data-ttu-id="e898f-152">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="e898f-152">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="e898f-153">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="e898f-153">**Send handler**</span></span>|<span data-ttu-id="e898f-154">從下拉式清單選取**FileActHost**。</span><span class="sxs-lookup"><span data-stu-id="e898f-154">From the drop-down list, select the **FileActHost**.</span></span>|  
    |<span data-ttu-id="e898f-155">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="e898f-155">**Send pipeline**</span></span>|<span data-ttu-id="e898f-156">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="e898f-156">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="e898f-157">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="e898f-157">**Receive pipeline**</span></span>|<span data-ttu-id="e898f-158">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="e898f-158">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="e898f-159">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e898f-159">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="e898f-160">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="e898f-160">**Use this**</span></span>|<span data-ttu-id="e898f-161">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="e898f-161">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="e898f-162">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e898f-162">**Property**</span></span>|<span data-ttu-id="e898f-163">從下拉式清單選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="e898f-163">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="e898f-164">**運算子**</span><span class="sxs-lookup"><span data-stu-id="e898f-164">**Operator**</span></span>|<span data-ttu-id="e898f-165">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="e898f-165">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="e898f-166">**值**</span><span class="sxs-lookup"><span data-stu-id="e898f-166">**Value**</span></span>|<span data-ttu-id="e898f-167">型別**Tutorial_IA_InputRequest_SnF**。</span><span class="sxs-lookup"><span data-stu-id="e898f-167">Type **Tutorial_IA_InputRequest_SnF**.</span></span>|  
    |<span data-ttu-id="e898f-168">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="e898f-168">**Group by**</span></span>|<span data-ttu-id="e898f-169">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="e898f-169">Leave the default value.</span></span>|  
  
10. <span data-ttu-id="e898f-170">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e898f-170">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e898f-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e898f-171">See Also</span></span>  
 <span data-ttu-id="e898f-172">[步驟 2A： 新增檔案接收位置的 FileAct 存放與轉寄 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="e898f-172">[Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="e898f-173">步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleFileRequest 和 Sw:HandleSnFRequest FileAct 存放與轉寄的訊息 （提取） 案例</span><span class="sxs-lookup"><span data-stu-id="e898f-173">Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)