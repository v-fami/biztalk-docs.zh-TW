---
title: "步驟 3E： 加入互動的傳送埠互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9522386-e980-4ab1-b65a-939ca7936ad9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcb78fd556e72e4ca19e1d5172826a813f23eb24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario"></a><span data-ttu-id="9e6e8-102">步驟 3E： 加入互動的傳送埠互動即時案例</span><span class="sxs-lookup"><span data-stu-id="9e6e8-102">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="9e6e8-103">完成[步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-103">Complete [Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) before you begin this step.</span></span>
  
## <a name="add-an-interact-send-port"></a><span data-ttu-id="9e6e8-104">加入互動的傳送埠</span><span class="sxs-lookup"><span data-stu-id="9e6e8-104">Add an INTERACT send port</span></span>  
  
1.  <span data-ttu-id="9e6e8-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="9e6e8-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="9e6e8-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
4.  <span data-ttu-id="9e6e8-108">在**傳送埠屬性**視窗中，傳送埠**Tutorial_IA_SendRequest_RealTime**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-108">In the **Send Port Properties** window, name the send port **Tutorial_IA_SendRequest_RealTime**.</span></span>  
  
5.  <span data-ttu-id="9e6e8-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**互動**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="9e6e8-110">在**互動傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9e6e8-110">In the **INTERACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="9e6e8-111">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-111">**Use this**</span></span>|<span data-ttu-id="9e6e8-112">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="9e6e8-113">**密碼**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-113">**Password**</span></span>|<span data-ttu-id="9e6e8-114">視 SAG 連線設定的密碼。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-114">Set the password as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="9e6e8-115">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-115">**User name**</span></span>|<span data-ttu-id="9e6e8-116">視 SAG 連線設定的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-116">Set the user name as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="9e6e8-117">**配接器模式**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-117">**Adapter Mode**</span></span>|<span data-ttu-id="9e6e8-118">從下拉式清單選取**即時**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-118">From the drop-down list, select **RealTime**.</span></span>|  
    |<span data-ttu-id="9e6e8-119">**訊息格式**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-119">**Message format**</span></span>|<span data-ttu-id="9e6e8-120">**InteractMessage**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-120">**InteractMessage**.</span></span>|  
    |<span data-ttu-id="9e6e8-121">**不可否認性指標**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-121">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="9e6e8-122">**FALSE**：</span><span class="sxs-lookup"><span data-stu-id="9e6e8-122">**FALSE**.</span></span>|  
    |<span data-ttu-id="9e6e8-123">**要求類型**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-123">**Request Type**</span></span>|<span data-ttu-id="9e6e8-124">輸入適當\<RequestType > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-124">Type the appropriate \<RequestType> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="9e6e8-125">**ResponseCrypto**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-125">**ResponseCrypto**</span></span>|<span data-ttu-id="9e6e8-126">**FALSE**：</span><span class="sxs-lookup"><span data-stu-id="9e6e8-126">**FALSE**.</span></span>|  
    |<span data-ttu-id="9e6e8-127">**要求者**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-127">**Requestor**</span></span>|<span data-ttu-id="9e6e8-128">將它設定為適當\<要求者 > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-128">Set it to the appropriate \<Requestor> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="9e6e8-129">**回應者**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-129">**Responder**</span></span>|<span data-ttu-id="9e6e8-130">將它設定為適當\<回應 > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-130">Set it to the appropriate \<Responder> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="9e6e8-131">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-131">**Service Name**</span></span>|<span data-ttu-id="9e6e8-132">將它設定為適當\<服務名稱 >，根據 SWIFT 與您佈建。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-132">Set it to the appropriate \<service name>, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="9e6e8-133">**傳遞通知**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-133">**Delivery Notification**</span></span>|<span data-ttu-id="9e6e8-134">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-134">From the drop-down list, select  **FALSE**.</span></span>|  
    |<span data-ttu-id="9e6e8-135">**通知佇列**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-135">**Notify queue**</span></span>|<span data-ttu-id="9e6e8-136">輸入適當的佇列名稱，根據 SWIFT 與您佈建。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-136">Type the appropriate queue name, based on your provisioning with SWIFT.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="9e6e8-137">如果只傳送內容，則組"Payloadonly 」 中的互動來 MessageFormat 接收連接埠和互動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-137">If only payload is to be transferred, set the MessageFormat to “Payloadonly” in the INTERACT receive port and INTERACT send port.</span></span> <span data-ttu-id="9e6e8-138">設定接收和傳送管線來 PassThru。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-138">Set the receive and send pipelines to PassThru.</span></span>  
  
7.  <span data-ttu-id="9e6e8-139">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-139">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="9e6e8-140">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9e6e8-140">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="9e6e8-141">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-141">**Use this**</span></span>|<span data-ttu-id="9e6e8-142">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-142">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="9e6e8-143">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-143">**Send handler**</span></span>|<span data-ttu-id="9e6e8-144">從下拉式清單中，選取主機互動。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-144">From the drop-down list, select the Interact host.</span></span>|  
    |<span data-ttu-id="9e6e8-145">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-145">**Send pipeline**</span></span>|<span data-ttu-id="9e6e8-146">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-146">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="9e6e8-147">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-147">**Receive pipeline**</span></span>|<span data-ttu-id="9e6e8-148">**[Xmlreceive]**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-148">**XMLReceive**</span></span>|  
  
9. <span data-ttu-id="9e6e8-149">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9e6e8-149">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="9e6e8-150">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-150">**Use this**</span></span>|<span data-ttu-id="9e6e8-151">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-151">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="9e6e8-152">**屬性**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-152">**Property**</span></span>|<span data-ttu-id="9e6e8-153">從下拉式清單選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-153">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="9e6e8-154">**運算子**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-154">**Operator**</span></span>|<span data-ttu-id="9e6e8-155">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-155">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="9e6e8-156">**值**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-156">**Value**</span></span>|<span data-ttu-id="9e6e8-157">型別**Tutorial_IA_InputRequest_RealTime**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-157">Type **Tutorial_IA_InputRequest_RealTime**.</span></span>|  
    |<span data-ttu-id="9e6e8-158">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="9e6e8-158">**Group by**</span></span>|<span data-ttu-id="9e6e8-159">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-159">Leave the default value.</span></span>|  
  
10. <span data-ttu-id="9e6e8-160">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9e6e8-160">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e6e8-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e6e8-161">See Also</span></span>  
 <span data-ttu-id="9e6e8-162">[步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9e6e8-162">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="9e6e8-163">[步驟 3A： 新增 FILE 接收位置的互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9e6e8-163">[Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="9e6e8-164">[步驟 3B： 加入互動接收位置互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9e6e8-164">[Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="9e6e8-165">[步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9e6e8-165">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="9e6e8-166">步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例</span><span class="sxs-lookup"><span data-stu-id="9e6e8-166">Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)