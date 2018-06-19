---
title: 步驟 3B： 加入互動接收位置互動即時案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59780635-e1b6-4e74-a89a-73ec26d6c670
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1a98f97cba9f46b43b92128a6585ad18afb894
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966300"
---
# <a name="step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario"></a><span data-ttu-id="fed98-102">步驟 3B： 加入互動接收位置互動即時案例</span><span class="sxs-lookup"><span data-stu-id="fed98-102">Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="fed98-103">完成[步驟 3A: FILE 接收位置新增互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="fed98-103">Complete [Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) before you begin this step.</span></span>
  
## <a name="add-an-interact-receive-location"></a><span data-ttu-id="fed98-104">加入互動接收位置</span><span class="sxs-lookup"><span data-stu-id="fed98-104">Add an INTERACT receive location</span></span>  
  
1.  <span data-ttu-id="fed98-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="fed98-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fed98-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fed98-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="fed98-107">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="fed98-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="fed98-108">在**接收埠屬性**視窗中，接收埠， **Tutorial_IA_HandleRequestOneWay_RealTime**。</span><span class="sxs-lookup"><span data-stu-id="fed98-108">In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_HandleRequestOneWay_RealTime**.</span></span>  
  
5.  <span data-ttu-id="fed98-109">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="fed98-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="fed98-110">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**互動**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="fed98-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="fed98-111">在**互動傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fed98-111">In the **INTERACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="fed98-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="fed98-112">**Use this**</span></span>|<span data-ttu-id="fed98-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="fed98-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="fed98-114">**密碼**</span><span class="sxs-lookup"><span data-stu-id="fed98-114">**Password**</span></span>|<span data-ttu-id="fed98-115">輸入您用來連接到 SAG 的密碼。</span><span class="sxs-lookup"><span data-stu-id="fed98-115">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="fed98-116">如需詳細資訊，請參閱 SAG 說明。</span><span class="sxs-lookup"><span data-stu-id="fed98-116">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="fed98-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="fed98-117">**User name**</span></span>|<span data-ttu-id="fed98-118">輸入您用來連接到 SAG 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="fed98-118">Type the user name you use to connect to SAG.</span></span>|  
    |<span data-ttu-id="fed98-119">**應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="fed98-119">**Application name**</span></span>|<span data-ttu-id="fed98-120">輸入伺服器\<*應用程式的介面名稱*\>如 SAG 方塊路由的集合。</span><span class="sxs-lookup"><span data-stu-id="fed98-120">Type the Server \<*Application Interface Name*\> for the SAG box routing set.</span></span>|  
    |<span data-ttu-id="fed98-121">**密碼編譯模式**</span><span class="sxs-lookup"><span data-stu-id="fed98-121">**Crypto Mode**</span></span>|<span data-ttu-id="fed98-122">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="fed98-122">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="fed98-123">**LogMessageBody**</span><span class="sxs-lookup"><span data-stu-id="fed98-123">**LogMessageBody**</span></span>|<span data-ttu-id="fed98-124">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="fed98-124">From the drop-down list, select **FALSE**.</span></span> <span data-ttu-id="fed98-125">**注意：** 如果設為 TRUE 時，它會保留的訊息本文的 「 追蹤 」 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fed98-125">**Note:**  If you set to TRUE, it preserves the message body in the tracking database.</span></span> <span data-ttu-id="fed98-126">不過，基於安全性理由，訊息本文可以永遠不會在檢視 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="fed98-126">However, for security reasons, the message body can never be viewed in the BAM portal.</span></span>|  
    |<span data-ttu-id="fed98-127">**記錄訊息**</span><span class="sxs-lookup"><span data-stu-id="fed98-127">**LogMessages**</span></span>|<span data-ttu-id="fed98-128">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="fed98-128">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="fed98-129">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="fed98-129">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="fed98-130">**訊息格式**</span><span class="sxs-lookup"><span data-stu-id="fed98-130">**Message format**</span></span>|<span data-ttu-id="fed98-131">從下拉式清單選取**InterActMessage**。</span><span class="sxs-lookup"><span data-stu-id="fed98-131">From the drop-down list, select **InterActMessage**.</span></span>|  
    |<span data-ttu-id="fed98-132">**MemberRef**</span><span class="sxs-lookup"><span data-stu-id="fed98-132">**MemberRef**</span></span>|<span data-ttu-id="fed98-133">從下拉式清單選取**ResponseHeader**。</span><span class="sxs-lookup"><span data-stu-id="fed98-133">From the drop-down list, select **ResponseHeader**.</span></span>|  
    |<span data-ttu-id="fed98-134">**不可否認性指標**</span><span class="sxs-lookup"><span data-stu-id="fed98-134">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="fed98-135">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="fed98-135">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="fed98-136">**回應者**</span><span class="sxs-lookup"><span data-stu-id="fed98-136">**Responder**</span></span>|<span data-ttu-id="fed98-137">輸入適當\< *ResponderDN* \> SWIFT 與您佈建為基礎的字串。</span><span class="sxs-lookup"><span data-stu-id="fed98-137">Type the appropriate \<*ResponderDN*\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="fed98-138">**ResponseCrypto**</span><span class="sxs-lookup"><span data-stu-id="fed98-138">**ResponseCrypto**</span></span>|<span data-ttu-id="fed98-139">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="fed98-139">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="fed98-140">**逾時**</span><span class="sxs-lookup"><span data-stu-id="fed98-140">**Timeout**</span></span>|<span data-ttu-id="fed98-141">發生連接逾時之前的秒數的類型。</span><span class="sxs-lookup"><span data-stu-id="fed98-141">Type an appropriate number of seconds before connection timeout should occur.</span></span>|  
    |<span data-ttu-id="fed98-142">**取得佇列**</span><span class="sxs-lookup"><span data-stu-id="fed98-142">**Acquire queue**</span></span>|<span data-ttu-id="fed98-143">保留預設值，這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fed98-143">Leave the default value for this property.</span></span> <span data-ttu-id="fed98-144">這個屬性用於儲存和轉送案例。</span><span class="sxs-lookup"><span data-stu-id="fed98-144">This property is used for Store-and-Forward scenarios.</span></span>|  
    |<span data-ttu-id="fed98-145">**ForceAcquire**</span><span class="sxs-lookup"><span data-stu-id="fed98-145">**ForceAcquire**</span></span>|<span data-ttu-id="fed98-146">保留預設值，這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fed98-146">Leave the default value for this property.</span></span> <span data-ttu-id="fed98-147">這個屬性用於儲存和轉送案例。</span><span class="sxs-lookup"><span data-stu-id="fed98-147">This property is used for Store-and-Forward scenarios.</span></span>|  
    |<span data-ttu-id="fed98-148">**排序依據**</span><span class="sxs-lookup"><span data-stu-id="fed98-148">**Order by**</span></span>|<span data-ttu-id="fed98-149">保留預設值，這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fed98-149">Leave the default value for this property.</span></span> <span data-ttu-id="fed98-150">這個屬性用於儲存和轉送案例。</span><span class="sxs-lookup"><span data-stu-id="fed98-150">This property is used for Store-and-Forward scenarios.</span></span>|  
    |<span data-ttu-id="fed98-151">**推入工作階段**</span><span class="sxs-lookup"><span data-stu-id="fed98-151">**Push session**</span></span>|<span data-ttu-id="fed98-152">保留預設值，這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fed98-152">Leave the default value for this property.</span></span> <span data-ttu-id="fed98-153">這個屬性用於儲存和轉送案例。</span><span class="sxs-lookup"><span data-stu-id="fed98-153">This property is used for Store-and-Forward scenarios.</span></span>|  
    |<span data-ttu-id="fed98-154">**復原模式**</span><span class="sxs-lookup"><span data-stu-id="fed98-154">**Recovery mode**</span></span>|<span data-ttu-id="fed98-155">保留預設值，這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fed98-155">Leave the default value for this property.</span></span> <span data-ttu-id="fed98-156">這個屬性用於儲存和轉送案例。</span><span class="sxs-lookup"><span data-stu-id="fed98-156">This property is used for Store-and-Forward scenarios.</span></span>|  
    |<span data-ttu-id="fed98-157">**SNL 端點**</span><span class="sxs-lookup"><span data-stu-id="fed98-157">**SNL end-point**</span></span>|<span data-ttu-id="fed98-158">保留預設值，這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fed98-158">Leave the default value for this property.</span></span> <span data-ttu-id="fed98-159">這個屬性用於儲存和轉送案例。</span><span class="sxs-lookup"><span data-stu-id="fed98-159">This property is used for Store-and-Forward scenarios.</span></span>|  
  
8.  <span data-ttu-id="fed98-160">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fed98-160">Click **OK**.</span></span>  
  
9. <span data-ttu-id="fed98-161">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fed98-161">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="fed98-162">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="fed98-162">**Use this**</span></span>|<span data-ttu-id="fed98-163">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="fed98-163">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="fed98-164">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="fed98-164">**Receive handler**</span></span>|<span data-ttu-id="fed98-165">從下拉式清單選取**BizTalkServerIsolatedHost**。</span><span class="sxs-lookup"><span data-stu-id="fed98-165">From the drop-down list, select **BizTalkServerIsolatedHost**.</span></span>|  
    |<span data-ttu-id="fed98-166">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="fed98-166">**Receive pipeline**</span></span>|<span data-ttu-id="fed98-167">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="fed98-167">From the drop-down list, select **XMLReceive**.</span></span>|  
  
10. <span data-ttu-id="fed98-168">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fed98-168">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed98-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="fed98-169">See Also</span></span>  
 <span data-ttu-id="fed98-170">[步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="fed98-170">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="fed98-171">[步驟 3A： 新增 FILE 接收位置的互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="fed98-171">[Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="fed98-172">[步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="fed98-172">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="fed98-173">[步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span><span class="sxs-lookup"><span data-stu-id="fed98-173">[Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span></span>  
 [<span data-ttu-id="fed98-174">步驟 3E：針對 InterAct 即時案例新增 INTERACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="fed98-174">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)