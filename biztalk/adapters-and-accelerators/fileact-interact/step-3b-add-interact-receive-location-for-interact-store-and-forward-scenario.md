---
title: "步驟 3B： 加入互動接收位置的互動存放區和情況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da077518-b2ee-4b5f-88d0-fe73af2baa7a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f6f0ffd20dba192a038981469164f63cdd7593f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-add-an-interact-receive-location-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="a59b0-102">步驟 3B： 加入互動接收位置的互動存放區和轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="a59b0-102">Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="a59b0-103">完成[步驟 3A： 新增檔案接收位置為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="a59b0-103">Complete [Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) before you begin this step.</span></span>
  
## <a name="add-an-interact-receive-location"></a><span data-ttu-id="a59b0-104">加入互動接收位置</span><span class="sxs-lookup"><span data-stu-id="a59b0-104">Add an INTERACT receive location</span></span>  
  
1.  <span data-ttu-id="a59b0-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a59b0-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a59b0-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="a59b0-107">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="a59b0-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="a59b0-108">在**接收埠屬性**視窗中，接收埠，Tutorial_IA_HandleRequestOneWay_SnF。</span><span class="sxs-lookup"><span data-stu-id="a59b0-108">In the **Receive Port Properties** window, name the receive port, Tutorial_IA_HandleRequestOneWay_SnF.</span></span>  
  
5.  <span data-ttu-id="a59b0-109">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="a59b0-110">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**互動**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="a59b0-111">在**互動傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a59b0-111">In the **INTERACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="a59b0-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a59b0-112">**Use this**</span></span>|<span data-ttu-id="a59b0-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a59b0-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a59b0-114">**密碼**</span><span class="sxs-lookup"><span data-stu-id="a59b0-114">**Password**</span></span>|<span data-ttu-id="a59b0-115">輸入您用來連接到 SAG 的密碼。</span><span class="sxs-lookup"><span data-stu-id="a59b0-115">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="a59b0-116">如需詳細資訊，請參閱 SAG 說明。</span><span class="sxs-lookup"><span data-stu-id="a59b0-116">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="a59b0-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="a59b0-117">**User name**</span></span>|<span data-ttu-id="a59b0-118">輸入您用來連接到 SAG 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a59b0-118">Type the user name you use to connect to SAG.</span></span>|  
    |<span data-ttu-id="a59b0-119">**應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="a59b0-119">**Application name**</span></span>|<span data-ttu-id="a59b0-120">輸入伺服器\<應用程式的介面名稱 > 的 SAG 方塊路由的集合。</span><span class="sxs-lookup"><span data-stu-id="a59b0-120">Type the Server \<Application Interface Name> for the SAG box routing set.</span></span>|  
    |<span data-ttu-id="a59b0-121">**密碼編譯模式**</span><span class="sxs-lookup"><span data-stu-id="a59b0-121">**Crypto Mode**</span></span>|<span data-ttu-id="a59b0-122">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-122">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="a59b0-123">**LogMessageBody**</span><span class="sxs-lookup"><span data-stu-id="a59b0-123">**LogMessageBody**</span></span>|<span data-ttu-id="a59b0-124">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-124">From the drop-down list, select **FALSE**.</span></span> <span data-ttu-id="a59b0-125">**注意：**如果設為 TRUE 時，它會保留的訊息本文的 「 BizTalk 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="a59b0-125">**Note:**  If you set to TRUE, it preserves the message body in the BizTalk Tracking database.</span></span> <span data-ttu-id="a59b0-126">不過，基於安全性理由，訊息本文可以永遠不會在檢視 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="a59b0-126">However, for security reasons, the message body can never be viewed in the BAM portal.</span></span>|  
    |<span data-ttu-id="a59b0-127">**記錄訊息**</span><span class="sxs-lookup"><span data-stu-id="a59b0-127">**LogMessages**</span></span>|<span data-ttu-id="a59b0-128">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-128">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="a59b0-129">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="a59b0-129">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="a59b0-130">**訊息格式**</span><span class="sxs-lookup"><span data-stu-id="a59b0-130">**Message format**</span></span>|<span data-ttu-id="a59b0-131">從下拉式清單選取**InterActMessage**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-131">From the drop-down list, select **InterActMessage**.</span></span>|  
    |<span data-ttu-id="a59b0-132">**MemberRef**</span><span class="sxs-lookup"><span data-stu-id="a59b0-132">**MemberRef**</span></span>|<span data-ttu-id="a59b0-133">從下拉式清單選取**ResponseHeader**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-133">From the drop-down list, select **ResponseHeader**.</span></span>|  
    |<span data-ttu-id="a59b0-134">**不可否認性指標**</span><span class="sxs-lookup"><span data-stu-id="a59b0-134">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="a59b0-135">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-135">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="a59b0-136">**回應者**</span><span class="sxs-lookup"><span data-stu-id="a59b0-136">**Responder**</span></span>|<span data-ttu-id="a59b0-137">輸入適當\<回應 > SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="a59b0-137">Type the appropriate \<Responder> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="a59b0-138">**ResponseCrypto**</span><span class="sxs-lookup"><span data-stu-id="a59b0-138">**ResponseCrypto**</span></span>|<span data-ttu-id="a59b0-139">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-139">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="a59b0-140">**逾時**</span><span class="sxs-lookup"><span data-stu-id="a59b0-140">**Timeout**</span></span>|<span data-ttu-id="a59b0-141">輸入適當應該發生逾時之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="a59b0-141">Type an appropriate number of seconds before timeout should occur.</span></span>|  
    |<span data-ttu-id="a59b0-142">**取得佇列**</span><span class="sxs-lookup"><span data-stu-id="a59b0-142">**Acquire queue**</span></span>|<span data-ttu-id="a59b0-143">輸入佇列的名稱，根據 SWIFT 與您佈建。</span><span class="sxs-lookup"><span data-stu-id="a59b0-143">Type the queue name, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="a59b0-144">**ForceAcquire**</span><span class="sxs-lookup"><span data-stu-id="a59b0-144">**ForceAcquire**</span></span>|<span data-ttu-id="a59b0-145">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-145">From the drop-down list, select **TRUE**.</span></span>|  
    |<span data-ttu-id="a59b0-146">**排序依據**</span><span class="sxs-lookup"><span data-stu-id="a59b0-146">**Order by**</span></span>|<span data-ttu-id="a59b0-147">從下拉式清單選取**互動**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-147">From the drop-down list, select **Interact**.</span></span>|  
    |<span data-ttu-id="a59b0-148">**推入工作階段**</span><span class="sxs-lookup"><span data-stu-id="a59b0-148">**Push session**</span></span>|<span data-ttu-id="a59b0-149">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-149">From the drop-down list, select **TRUE**.</span></span>|  
    |<span data-ttu-id="a59b0-150">**復原模式**</span><span class="sxs-lookup"><span data-stu-id="a59b0-150">**Recovery mode**</span></span>|<span data-ttu-id="a59b0-151">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-151">From the drop-down list, select **TRUE**.</span></span>|  
    |<span data-ttu-id="a59b0-152">**SNL 端點**</span><span class="sxs-lookup"><span data-stu-id="a59b0-152">**SNL end-point**</span></span>|<span data-ttu-id="a59b0-153">輸入適當的端點 SAG 路由集合。</span><span class="sxs-lookup"><span data-stu-id="a59b0-153">Type the appropriate end-point for the SAG routing set.</span></span> <span data-ttu-id="a59b0-154">這個值應該符合您設定在 SAG SnL 端點。</span><span class="sxs-lookup"><span data-stu-id="a59b0-154">This value should match the SnL endpoint you configured in SAG.</span></span>|  
  
8.  <span data-ttu-id="a59b0-155">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-155">Click **OK**.</span></span>  
  
9. <span data-ttu-id="a59b0-156">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a59b0-156">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="a59b0-157">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a59b0-157">**Use this**</span></span>|<span data-ttu-id="a59b0-158">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a59b0-158">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a59b0-159">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="a59b0-159">**Receive handler**</span></span>|<span data-ttu-id="a59b0-160">從下拉式清單選取**BizTalkServerIsolatedHost**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-160">From the drop-down list, select **BizTalkServerIsolatedHost**.</span></span>|  
    |<span data-ttu-id="a59b0-161">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="a59b0-161">**Receive pipeline**</span></span>|<span data-ttu-id="a59b0-162">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-162">From the drop-down list, select **XMLReceive**.</span></span>|  
  
10. <span data-ttu-id="a59b0-163">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a59b0-163">Click **OK**.</span></span>  
  
## <a name="complete-steps"></a><span data-ttu-id="a59b0-164">完成步驟</span><span class="sxs-lookup"><span data-stu-id="a59b0-164">Complete steps</span></span>
 <span data-ttu-id="a59b0-165">[步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a59b0-165">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="a59b0-166">[步驟 3A： 新增 FILE 接收位置為互動存放區與正向的實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a59b0-166">[Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="a59b0-167">步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動存放區和轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="a59b0-167">Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  
 [<span data-ttu-id="a59b0-168">步驟 3D: 互動存放區和轉寄的案例中加入互動的傳送埠</span><span class="sxs-lookup"><span data-stu-id="a59b0-168">Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)