---
title: 步驟 2c： 新增 FILEACT 傳送埠為 FileAct 存放與轉寄 （提取） 實例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8743a868-9625-477b-a7da-673bfa262723
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 803a8c671081afd3ba18b81d4770b80b26205eaf
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964044"
---
# <a name="step-2c-add-a-fileact-send-port-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="38c36-102">步驟 2c： 新增為 FileAct 存放與轉寄 （提取） 實例 FILEACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="38c36-102">Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="38c36-103">在開始此步驟之前，必須先完成[步驟 2B： 將檔案傳送埠來擷取 Sw:HandleFileRequest 和 FileAct 存放與轉寄 （提取） 案例的 Sw:HandleSnFRequest 訊息](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)。</span><span class="sxs-lookup"><span data-stu-id="38c36-103">Before you begin this step, you must complete [Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md).</span></span>  
  
### <a name="to-add-a-fileact-send-port"></a><span data-ttu-id="38c36-104">若要新增 FileACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="38c36-104">To add a FileACT send port</span></span>  
  
1.  <span data-ttu-id="38c36-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="38c36-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="38c36-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="38c36-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="38c36-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="38c36-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
4.  <span data-ttu-id="38c36-108">在**傳送埠屬性**視窗中，傳送埠， **Tutorial_FA_SendRequest_SnF**。</span><span class="sxs-lookup"><span data-stu-id="38c36-108">In the **Send Port Properties** window, name the send port, **Tutorial_FA_SendRequest_SnF**.</span></span>  
  
5.  <span data-ttu-id="38c36-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**FILEACT**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="38c36-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILEACT**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="38c36-110">在**FILEACT 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="38c36-110">In the **FILEACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="38c36-111">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="38c36-111">**Use this**</span></span>|<span data-ttu-id="38c36-112">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="38c36-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="38c36-113">**密碼**</span><span class="sxs-lookup"><span data-stu-id="38c36-113">**Password**</span></span>|<span data-ttu-id="38c36-114">視 SAG 連線設定的密碼。</span><span class="sxs-lookup"><span data-stu-id="38c36-114">Set the password as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="38c36-115">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="38c36-115">**User name**</span></span>|<span data-ttu-id="38c36-116">視 SAG 連線設定的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="38c36-116">Set the user name as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="38c36-117">**配接器模式**</span><span class="sxs-lookup"><span data-stu-id="38c36-117">**Adapter Mode**</span></span>|<span data-ttu-id="38c36-118">從下拉式清單選取**存放與轉寄**。</span><span class="sxs-lookup"><span data-stu-id="38c36-118">From the drop-down list, select **Store and Forward**.</span></span>|  
    |<span data-ttu-id="38c36-119">**不可否認性指標**</span><span class="sxs-lookup"><span data-stu-id="38c36-119">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="38c36-120">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="38c36-120">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="38c36-121">**要求類型**</span><span class="sxs-lookup"><span data-stu-id="38c36-121">**Request Type**</span></span>|<span data-ttu-id="38c36-122">設定為適當\<RequestType\> SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="38c36-122">Set to the appropriate \<RequestType\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="38c36-123">**RequestCrypto**</span><span class="sxs-lookup"><span data-stu-id="38c36-123">**RequestCrypto**</span></span>|<span data-ttu-id="38c36-124">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="38c36-124">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="38c36-125">**要求者**</span><span class="sxs-lookup"><span data-stu-id="38c36-125">**Requestor**</span></span>|<span data-ttu-id="38c36-126">設定為適當\<要求者\>SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="38c36-126">Set to the appropriate \<Requestor\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="38c36-127">**回應者**</span><span class="sxs-lookup"><span data-stu-id="38c36-127">**Responder**</span></span>|<span data-ttu-id="38c36-128">設定為適當\<回應\>字串。</span><span class="sxs-lookup"><span data-stu-id="38c36-128">Set to the appropriate \<Responder\> string.</span></span>|  
    |<span data-ttu-id="38c36-129">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="38c36-129">**Service Name**</span></span>|<span data-ttu-id="38c36-130">設定為適當**\<服務名稱\>**。</span><span class="sxs-lookup"><span data-stu-id="38c36-130">Set to the appropriate **\<service name\>**.</span></span>|  
    |<span data-ttu-id="38c36-131">**通知標記**</span><span class="sxs-lookup"><span data-stu-id="38c36-131">**Acknowledgement Indicator**</span></span>|<span data-ttu-id="38c36-132">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="38c36-132">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="38c36-133">**事件端點**</span><span class="sxs-lookup"><span data-stu-id="38c36-133">**Event end-point**</span></span>|<span data-ttu-id="38c36-134">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="38c36-134">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="38c36-135">**檔案壓縮**</span><span class="sxs-lookup"><span data-stu-id="38c36-135">**File Compression**</span></span>|<span data-ttu-id="38c36-136">從下拉式清單選取**無**。</span><span class="sxs-lookup"><span data-stu-id="38c36-136">From the drop-down list, select **None**.</span></span>|  
    |<span data-ttu-id="38c36-137">**實體的資料夾名稱**</span><span class="sxs-lookup"><span data-stu-id="38c36-137">**Physical Folder Name**</span></span>|<span data-ttu-id="38c36-138">輸入 C:\SWIFTAdapterTutorial\Fileact\ClientLocation。</span><span class="sxs-lookup"><span data-stu-id="38c36-138">Type C:\SWIFTAdapterTutorial\Fileact\ClientLocation.</span></span>|  
    |<span data-ttu-id="38c36-139">**轉送端點**</span><span class="sxs-lookup"><span data-stu-id="38c36-139">**Transfer end-point**</span></span>|<span data-ttu-id="38c36-140">輸入適當的端點 SAG 路由集合。</span><span class="sxs-lookup"><span data-stu-id="38c36-140">Type the appropriate end-point for the SAG routing set.</span></span> <span data-ttu-id="38c36-141">這個值應該符合您設定在 SAG SNL 端點。</span><span class="sxs-lookup"><span data-stu-id="38c36-141">This value should match the SNL endpoint you configured in SAG.</span></span>|  
    |<span data-ttu-id="38c36-142">**ServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="38c36-142">**ServiceProfile**</span></span>|<span data-ttu-id="38c36-143">從下拉式清單選取**交易計數**。</span><span class="sxs-lookup"><span data-stu-id="38c36-143">From the drop-down list, select **Transaction Count**.</span></span>|  
    |<span data-ttu-id="38c36-144">**傳遞通知**</span><span class="sxs-lookup"><span data-stu-id="38c36-144">**Delivery notification**</span></span>|<span data-ttu-id="38c36-145">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="38c36-145">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="38c36-146">**通知佇列**</span><span class="sxs-lookup"><span data-stu-id="38c36-146">**Notify queue**</span></span>|<span data-ttu-id="38c36-147">輸入佇列的名稱，根據 SWIFT 與您佈建。</span><span class="sxs-lookup"><span data-stu-id="38c36-147">Type the queue name, based on your provisioning with SWIFT.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="38c36-148">如果要傳送訊息的交易計數，服務設定檔中設定模式以 「 交易計數 」 FileAct 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="38c36-148">If message with Transaction Count is to be transferred, set the Service Profile Mode to “Transaction Count” in the FileAct send port.</span></span>  
  
7.  <span data-ttu-id="38c36-149">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="38c36-149">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="38c36-150">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="38c36-150">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="38c36-151">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="38c36-151">**Use this**</span></span>|<span data-ttu-id="38c36-152">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="38c36-152">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="38c36-153">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="38c36-153">**Send handler**</span></span>|<span data-ttu-id="38c36-154">從下拉式清單選取**FileActHost**。</span><span class="sxs-lookup"><span data-stu-id="38c36-154">From the drop-down list, select the **FileActHost**.</span></span>|  
    |<span data-ttu-id="38c36-155">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="38c36-155">**Send pipeline**</span></span>|<span data-ttu-id="38c36-156">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="38c36-156">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="38c36-157">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="38c36-157">**Receive pipeline**</span></span>|<span data-ttu-id="38c36-158">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="38c36-158">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="38c36-159">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="38c36-159">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="38c36-160">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="38c36-160">**Use this**</span></span>|<span data-ttu-id="38c36-161">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="38c36-161">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="38c36-162">**屬性**</span><span class="sxs-lookup"><span data-stu-id="38c36-162">**Property**</span></span>|<span data-ttu-id="38c36-163">從下拉式清單選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="38c36-163">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="38c36-164">**運算子**</span><span class="sxs-lookup"><span data-stu-id="38c36-164">**Operator**</span></span>|<span data-ttu-id="38c36-165">從下拉式清單選取**==**。</span><span class="sxs-lookup"><span data-stu-id="38c36-165">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="38c36-166">**值**</span><span class="sxs-lookup"><span data-stu-id="38c36-166">**Value**</span></span>|<span data-ttu-id="38c36-167">型別**Tutorial_IA_InputRequest_SnF**。</span><span class="sxs-lookup"><span data-stu-id="38c36-167">Type **Tutorial_IA_InputRequest_SnF**.</span></span>|  
    |<span data-ttu-id="38c36-168">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="38c36-168">**Group by**</span></span>|<span data-ttu-id="38c36-169">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="38c36-169">Leave the default value.</span></span>|  
  
10. <span data-ttu-id="38c36-170">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="38c36-170">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c36-171">請參閱</span><span class="sxs-lookup"><span data-stu-id="38c36-171">See Also</span></span>  
 <span data-ttu-id="38c36-172">[步驟 2A： 新增檔案接收位置的 FileAct 存放與轉寄 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="38c36-172">[Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="38c36-173">步驟 2B：針對 FileAct 儲存和轉寄 (提取) 案例新增 FILE 傳送埠以擷取 Sw:HandleFileRequest 和 Sw:HandleSnFRequest 訊息</span><span class="sxs-lookup"><span data-stu-id="38c36-173">Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)