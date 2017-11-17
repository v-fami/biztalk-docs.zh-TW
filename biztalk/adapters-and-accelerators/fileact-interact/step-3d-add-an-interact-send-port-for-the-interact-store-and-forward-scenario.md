---
title: "步驟 3D: 互動存放區和轉寄的案例中加入互動的傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd126d9a-f4e4-429e-bab0-8b4c9c555e36
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ac1d379f2e68431f197f2db339cd0ac9f50c92e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="a0b49-102">步驟 3D: 互動存放區和轉寄的案例中加入互動的傳送埠</span><span class="sxs-lookup"><span data-stu-id="a0b49-102">Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="a0b49-103">完成[步驟 3c： 加入擷取為互動存放與轉寄實例 Sw:HandleRequest 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="a0b49-103">Complete [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md) before you begin this step.</span></span>
  
## <a name="add-an-interact-send-port"></a><span data-ttu-id="a0b49-104">加入互動的傳送埠</span><span class="sxs-lookup"><span data-stu-id="a0b49-104">Add an INTERACT send port</span></span>  
  
1.  <span data-ttu-id="a0b49-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a0b49-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b49-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="a0b49-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
4.  <span data-ttu-id="a0b49-108">在**傳送埠屬性**視窗中，傳送埠，Tutorial_IA_SendRequest_SnF。</span><span class="sxs-lookup"><span data-stu-id="a0b49-108">In the **Send Port Properties** window, name the send port, Tutorial_IA_SendRequest_SnF.</span></span>  
  
5.  <span data-ttu-id="a0b49-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**互動**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="a0b49-110">在**互動傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a0b49-110">In the **INTERACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a0b49-111">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a0b49-111">**Use this**</span></span>|<span data-ttu-id="a0b49-112">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a0b49-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a0b49-113">**密碼**</span><span class="sxs-lookup"><span data-stu-id="a0b49-113">**Password**</span></span>|<span data-ttu-id="a0b49-114">視 SAG 連線設定的密碼。</span><span class="sxs-lookup"><span data-stu-id="a0b49-114">Set the password as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="a0b49-115">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="a0b49-115">**User name**</span></span>|<span data-ttu-id="a0b49-116">視 SAG 連線設定的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a0b49-116">Set the user name as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="a0b49-117">**訊息格式**</span><span class="sxs-lookup"><span data-stu-id="a0b49-117">**Message format**</span></span>|<span data-ttu-id="a0b49-118">**InteractMessage**</span><span class="sxs-lookup"><span data-stu-id="a0b49-118">**InteractMessage**</span></span>|  
    |<span data-ttu-id="a0b49-119">**不可否認性指標**</span><span class="sxs-lookup"><span data-stu-id="a0b49-119">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="a0b49-120">**FALSE**</span><span class="sxs-lookup"><span data-stu-id="a0b49-120">**FALSE**</span></span>|  
    |<span data-ttu-id="a0b49-121">**要求類型**</span><span class="sxs-lookup"><span data-stu-id="a0b49-121">**Request Type**</span></span>|<span data-ttu-id="a0b49-122">輸入適當\<RequestType > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="a0b49-122">Type the appropriate \<RequestType> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="a0b49-123">**ResponseCrypto**</span><span class="sxs-lookup"><span data-stu-id="a0b49-123">**ResponseCrypto**</span></span>|<span data-ttu-id="a0b49-124">**FALSE**</span><span class="sxs-lookup"><span data-stu-id="a0b49-124">**FALSE**</span></span>|  
    |<span data-ttu-id="a0b49-125">**要求者**</span><span class="sxs-lookup"><span data-stu-id="a0b49-125">**Requestor**</span></span>|<span data-ttu-id="a0b49-126">輸入適當\<RequestorDN > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="a0b49-126">Type the appropriate \<RequestorDN> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="a0b49-127">**回應者**</span><span class="sxs-lookup"><span data-stu-id="a0b49-127">**Responder**</span></span>|<span data-ttu-id="a0b49-128">輸入適當\<ResponderDN > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="a0b49-128">Type the appropriate \<ResponderDN> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="a0b49-129">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="a0b49-129">**Service Name**</span></span>|<span data-ttu-id="a0b49-130">輸入適當\<服務名稱 >，根據 SWIFT 與您佈建。</span><span class="sxs-lookup"><span data-stu-id="a0b49-130">Type the appropriate \<service name>, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="a0b49-131">**傳遞通知**</span><span class="sxs-lookup"><span data-stu-id="a0b49-131">**Delivery Notification**</span></span>|<span data-ttu-id="a0b49-132">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-132">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="a0b49-133">**通知佇列**</span><span class="sxs-lookup"><span data-stu-id="a0b49-133">**Notify queue**</span></span>|<span data-ttu-id="a0b49-134">輸入適當的佇列名稱，根據 SWIFT 與您佈建。</span><span class="sxs-lookup"><span data-stu-id="a0b49-134">Type the appropriate queue name, based on your provisioning with SWIFT.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="a0b49-135">如果只裝載為傳輸時，設定 「 內容 」 中的互動 MessageFormat 接收連接埠和互動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a0b49-135">If only payload is to be transferred, set the MessageFormat to “Payload” in the INTERACT receive port and INTERACT send port.</span></span> <span data-ttu-id="a0b49-136">將接收和傳送管線設定為 PassThru。</span><span class="sxs-lookup"><span data-stu-id="a0b49-136">Set the Receive and Send pipelines to PassThru.</span></span>  
  
7.  <span data-ttu-id="a0b49-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-137">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="a0b49-138">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a0b49-138">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="a0b49-139">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a0b49-139">**Use this**</span></span>|<span data-ttu-id="a0b49-140">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a0b49-140">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a0b49-141">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="a0b49-141">**Send handler**</span></span>|<span data-ttu-id="a0b49-142">從下拉式清單中，選取主機互動。</span><span class="sxs-lookup"><span data-stu-id="a0b49-142">From the drop-down list, select the Interact host.</span></span>|  
    |<span data-ttu-id="a0b49-143">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="a0b49-143">**Send pipeline**</span></span>|<span data-ttu-id="a0b49-144">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-144">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="a0b49-145">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="a0b49-145">**Receive pipeline**</span></span>|<span data-ttu-id="a0b49-146">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-146">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="a0b49-147">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a0b49-147">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="a0b49-148">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a0b49-148">**Use this**</span></span>|<span data-ttu-id="a0b49-149">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a0b49-149">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a0b49-150">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a0b49-150">**Property**</span></span>|<span data-ttu-id="a0b49-151">從下拉式清單選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-151">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="a0b49-152">**運算子**</span><span class="sxs-lookup"><span data-stu-id="a0b49-152">**Operator**</span></span>|<span data-ttu-id="a0b49-153">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="a0b49-153">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="a0b49-154">**值**</span><span class="sxs-lookup"><span data-stu-id="a0b49-154">**Value**</span></span>|<span data-ttu-id="a0b49-155">型別 Tutorial_IA_InputRequest_SnF。</span><span class="sxs-lookup"><span data-stu-id="a0b49-155">Type Tutorial_IA_InputRequest_SnF.</span></span>|  
    |<span data-ttu-id="a0b49-156">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="a0b49-156">**Group by**</span></span>|<span data-ttu-id="a0b49-157">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="a0b49-157">Leave the default value.</span></span>|  
  
10. <span data-ttu-id="a0b49-158">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a0b49-158">Click **OK**.</span></span>  
  
## <a name="complete-steps"></a><span data-ttu-id="a0b49-159">完成步驟</span><span class="sxs-lookup"><span data-stu-id="a0b49-159">Complete steps</span></span>
 <span data-ttu-id="a0b49-160">[步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a0b49-160">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="a0b49-161">[步驟 3A： 新增 FILE 接收位置為互動存放區與正向的實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a0b49-161">[Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="a0b49-162">[步驟 3B： 加入互動接收位置的互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a0b49-162">[Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="a0b49-163">步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動存放區和轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="a0b49-163">Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  