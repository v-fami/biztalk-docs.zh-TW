---
title: "步驟 1： 設定 FileAct 存放與轉寄提取實例 SWIFT 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc271544-6bc8-4d62-aba0-3fe3295f2a2a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41e57df0f77718e3e36b5d0d68896def6a768be7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-configure-the-swift-adapter-for-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="43c16-102">步驟 1： 設定 FileAct 存放與轉寄提取實例 SWIFT 配接器</span><span class="sxs-lookup"><span data-stu-id="43c16-102">Step 1: Configure the SWIFT Adapter for FileAct Store and Forward pull scenario</span></span>
<span data-ttu-id="43c16-103">完成[準備使用本教學課程](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="43c16-103">Complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md) before you begin this step.</span></span>
  
## <a name="configure-the-swift-adapter"></a><span data-ttu-id="43c16-104">設定 SWIFT 配接器</span><span class="sxs-lookup"><span data-stu-id="43c16-104">Configure the SWIFT adapter</span></span>  
  
1.  <span data-ttu-id="43c16-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="43c16-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="43c16-106">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**平台設定**，依序展開**配接器**，以滑鼠右鍵按一下**FILEACT**，指向 **新增**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="43c16-106">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **FILEACT**, point to **New**, and then click **Send Handler**.</span></span>  
  
3.  <span data-ttu-id="43c16-107">在**FILEACT – 介面卡 HandlerProperties**對話方塊**一般**索引標籤上，從**主機名稱**下拉式清單中，選取**FileActHost**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="43c16-107">In the **FILEACT – Adapter HandlerProperties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **FileActHost**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="43c16-108">在**FILEACT 傳輸屬性**對話方塊**屬性**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="43c16-108">In the **FILEACT Transport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="43c16-109">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="43c16-109">**Use this**</span></span>|<span data-ttu-id="43c16-110">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="43c16-110">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="43c16-111">**引數**</span><span class="sxs-lookup"><span data-stu-id="43c16-111">**Arguments**</span></span>|<span data-ttu-id="43c16-112">輸入下列引數:-SagMessagePartner \<Fileact 用戶端訊息的夥伴建立 SAG\> **附註：**引數中的用戶端是 MessagePartner SAG 中進行設定。</span><span class="sxs-lookup"><span data-stu-id="43c16-112">Type the following argument: -SagMessagePartner \<Fileact Client Message Partner created in SAG\> **Note:**  The client in the argument is the MessagePartner you configured in SAG.</span></span>|  
    |<span data-ttu-id="43c16-113">**密碼編譯模式**</span><span class="sxs-lookup"><span data-stu-id="43c16-113">**Crypto Mode**</span></span>|<span data-ttu-id="43c16-114">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="43c16-114">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="43c16-115">**FACryptoMode**</span><span class="sxs-lookup"><span data-stu-id="43c16-115">**FACryptoMode**</span></span>|<span data-ttu-id="43c16-116">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="43c16-116">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="43c16-117">**記錄訊息**</span><span class="sxs-lookup"><span data-stu-id="43c16-117">**LogMessages**</span></span>|<span data-ttu-id="43c16-118">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="43c16-118">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="43c16-119">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="43c16-119">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="43c16-120">**啟用**</span><span class="sxs-lookup"><span data-stu-id="43c16-120">**Enable**</span></span>|<span data-ttu-id="43c16-121">False</span><span class="sxs-lookup"><span data-stu-id="43c16-121">False</span></span>|  
    |<span data-ttu-id="43c16-122">**事件端點**</span><span class="sxs-lookup"><span data-stu-id="43c16-122">**Event end-point**</span></span>|<span data-ttu-id="43c16-123">輸入適當的 SAG 端點。</span><span class="sxs-lookup"><span data-stu-id="43c16-123">Type the appropriate SAG end-point.</span></span>|  
    |<span data-ttu-id="43c16-124">**PhysicalFolderName**</span><span class="sxs-lookup"><span data-stu-id="43c16-124">**PhysicalFolderName**</span></span>|<span data-ttu-id="43c16-125">在伺服器上，輸入資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="43c16-125">Type the name of the folder on the server.</span></span> <span data-ttu-id="43c16-126">例如，C:\Fileact\ServerLocation。</span><span class="sxs-lookup"><span data-stu-id="43c16-126">For example, C:\Fileact\ServerLocation.</span></span>|  
    |<span data-ttu-id="43c16-127">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="43c16-127">**PollingInterval**</span></span>|<span data-ttu-id="43c16-128">PollingInterval 輸入適當的值。</span><span class="sxs-lookup"><span data-stu-id="43c16-128">Type the appropriate value for PollingInterval.</span></span> <span data-ttu-id="43c16-129">例如，5。</span><span class="sxs-lookup"><span data-stu-id="43c16-129">For example, 5.</span></span> <span data-ttu-id="43c16-130">這表示檢查的間隔 （以秒為單位） 之後，配接器的檔案傳輸的狀態。</span><span class="sxs-lookup"><span data-stu-id="43c16-130">This indicates the interval (in seconds) after which the adapter checks for the status of file transfer.</span></span>|  
    |<span data-ttu-id="43c16-131">**密碼**</span><span class="sxs-lookup"><span data-stu-id="43c16-131">**Password**</span></span>|<span data-ttu-id="43c16-132">輸入您用來連接到 SAG 的密碼。</span><span class="sxs-lookup"><span data-stu-id="43c16-132">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="43c16-133">如需詳細資訊，請參閱 SAG 說明。</span><span class="sxs-lookup"><span data-stu-id="43c16-133">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="43c16-134">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="43c16-134">**User Name**</span></span>|<span data-ttu-id="43c16-135">輸入您用來連接到 SAG 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="43c16-135">Type the user name you use to connect to SAG.</span></span>|  
  
5.  <span data-ttu-id="43c16-136">按一下**確定**關閉 FILEACT 傳輸屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="43c16-136">Click **OK** to close the FILEACT Transport Properties dialog box.</span></span>  
  
6.  <span data-ttu-id="43c16-137">按一下**確定**關閉 FILEACT – 配接器處理常式屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="43c16-137">Click **OK** to close the FILEACT – Adapter Handler Properties dialog box.</span></span>  
  
7.  <span data-ttu-id="43c16-138">在訊息方塊中，按一下**確定**，然後重新啟動 FileAct 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="43c16-138">In the Message box, click **OK**, and then restart the FileAct host instance.</span></span>  
  
8.  <span data-ttu-id="43c16-139">重複步驟 1。</span><span class="sxs-lookup"><span data-stu-id="43c16-139">Repeat step 1.</span></span>  
  
9. <span data-ttu-id="43c16-140">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，依序展開**BizTalk**群組中，展開**平台設定**，依序展開**配接器**，選取**FILEACT**，開啟**BizTalkServerApplication** ，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="43c16-140">In the console tree, expand **BizTalk Server Administration**, expand the **BizTalk** group, expand **Platform Settings**, expand **Adapter**, select **FILEACT**, open **BizTalkServerApplication** and then, click **Properties**.</span></span>  
  
10. <span data-ttu-id="43c16-141">在**FILEACT 傳輸屬性**對話方塊**屬性**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="43c16-141">In the **FILEACT Transport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="43c16-142">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="43c16-142">**Use this**</span></span>|<span data-ttu-id="43c16-143">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="43c16-143">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="43c16-144">**引數**</span><span class="sxs-lookup"><span data-stu-id="43c16-144">**Arguments**</span></span>|<span data-ttu-id="43c16-145">輸入下列引數: – SagMessagePartner \<Fileact 用戶端訊息的夥伴建立 SAG\> **附註：**引數中的用戶端是 MessagePartner SAG 中進行設定。</span><span class="sxs-lookup"><span data-stu-id="43c16-145">Type the following argument: –SagMessagePartner \<Fileact Client Message Partner created in SAG\> **Note:**  The client in the argument is the MessagePartner you configured in SAG.</span></span>|  
    |<span data-ttu-id="43c16-146">**密碼編譯模式**</span><span class="sxs-lookup"><span data-stu-id="43c16-146">**Crypto Mode**</span></span>|<span data-ttu-id="43c16-147">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="43c16-147">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="43c16-148">**LogMessageBody**</span><span class="sxs-lookup"><span data-stu-id="43c16-148">**LogMessageBody**</span></span>|<span data-ttu-id="43c16-149">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="43c16-149">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="43c16-150">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="43c16-150">This enables the message events to be captured and tracked in the BAM portal.</span></span> <span data-ttu-id="43c16-151">**注意：**如果設為 TRUE 時，它會保留的訊息本文的 「 BizTalk 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="43c16-151">**Note:**  If you set to TRUE, it preserves the message body in the BizTalk Tracking database.</span></span> <span data-ttu-id="43c16-152">不過，基於安全性理由，訊息本文可以永遠不會在檢視 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="43c16-152">However, for security reasons, the message body can never be viewed in the BAM portal.</span></span>|  
    |<span data-ttu-id="43c16-153">**記錄訊息**</span><span class="sxs-lookup"><span data-stu-id="43c16-153">**LogMessages**</span></span>|<span data-ttu-id="43c16-154">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="43c16-154">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="43c16-155">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="43c16-155">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="43c16-156">**啟用**</span><span class="sxs-lookup"><span data-stu-id="43c16-156">**Enable**</span></span>|<span data-ttu-id="43c16-157">**True**</span><span class="sxs-lookup"><span data-stu-id="43c16-157">**True**</span></span>|  
    |<span data-ttu-id="43c16-158">**事件端點**</span><span class="sxs-lookup"><span data-stu-id="43c16-158">**Event end-point**</span></span>|<span data-ttu-id="43c16-159">輸入適當的 SAG 端點。</span><span class="sxs-lookup"><span data-stu-id="43c16-159">Type the appropriate SAG end-point.</span></span>|  
    |<span data-ttu-id="43c16-160">**PhysicalFolderName**</span><span class="sxs-lookup"><span data-stu-id="43c16-160">**PhysicalFolderName**</span></span>|<span data-ttu-id="43c16-161">在伺服器上，輸入資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="43c16-161">Type the name of the folder on the server.</span></span> <span data-ttu-id="43c16-162">例如，C:\Fileact\ServerLocation。</span><span class="sxs-lookup"><span data-stu-id="43c16-162">For example, C:\Fileact\ServerLocation.</span></span>|  
    |<span data-ttu-id="43c16-163">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="43c16-163">**PollingInterval**</span></span>|<span data-ttu-id="43c16-164">PollingInterval 輸入適當的值。</span><span class="sxs-lookup"><span data-stu-id="43c16-164">Type the appropriate value for PollingInterval.</span></span> <span data-ttu-id="43c16-165">例如，5。</span><span class="sxs-lookup"><span data-stu-id="43c16-165">For example, 5.</span></span> <span data-ttu-id="43c16-166">這表示檢查的間隔 （以秒為單位） 之後，配接器的檔案傳輸的狀態。</span><span class="sxs-lookup"><span data-stu-id="43c16-166">This indicates the interval (in seconds) after which the adapter checks for the status of file transfer.</span></span>|  
    |<span data-ttu-id="43c16-167">**密碼**</span><span class="sxs-lookup"><span data-stu-id="43c16-167">**Password**</span></span>|<span data-ttu-id="43c16-168">輸入您用來連接到 SAG 的密碼。</span><span class="sxs-lookup"><span data-stu-id="43c16-168">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="43c16-169">如需詳細資訊，請參閱 SAG 說明。</span><span class="sxs-lookup"><span data-stu-id="43c16-169">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="43c16-170">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="43c16-170">**Username**</span></span>|<span data-ttu-id="43c16-171">輸入您用來連接到 SAG 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="43c16-171">Type the user name you use to connect to SAG.</span></span>|  
  
11. <span data-ttu-id="43c16-172">按一下 [確定] 關閉 [FILEACT 傳輸屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="43c16-172">Click OK to close the FILEACT Transport Properties dialog box.</span></span>  
  
12. <span data-ttu-id="43c16-173">選取 設定此預設處理常式選項。</span><span class="sxs-lookup"><span data-stu-id="43c16-173">Select make this the default handler option.</span></span>  
  
13. <span data-ttu-id="43c16-174">按一下 確定 關閉 FILEACT – 配接器處理常式屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="43c16-174">Click OK to close the FILEACT – Adapter Handler Properties dialog box.</span></span>  
  
14. <span data-ttu-id="43c16-175">在訊息方塊中，按一下 [確定]，然後重新啟動 BizTalkServerApplication 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="43c16-175">In the Message box, click OK, and then restart the BizTalkServerApplication host instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c16-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="43c16-176">See Also</span></span>  
 <span data-ttu-id="43c16-177">[步驟 2： 建立傳送埠和接收埠為 FileAct 存放與轉寄 （提取） 實例](../../adapters-and-accelerators/fileact-interact/step-2-create-send-and-receive-ports-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="43c16-177">[Step 2: Create Send Ports and Receive Ports for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2-create-send-and-receive-ports-for-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="43c16-178">[步驟 3： 建立和繫結檔案 Act 存放區和轉送 （提取） 案例的動態傳送埠與協調流程](../../adapters-and-accelerators/fileact-interact/step-3-create-and-bind-an-orchestration-with-dynamic-send-port-for-file-act.md) </span><span class="sxs-lookup"><span data-stu-id="43c16-178">[Step 3: Create and bind an orchestration with dynamic send port  for the File Act Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-and-bind-an-orchestration-with-dynamic-send-port-for-file-act.md) </span></span>  
 [<span data-ttu-id="43c16-179">步驟 4：測試 FileAct 儲存和轉寄 (提取) 端對端案例</span><span class="sxs-lookup"><span data-stu-id="43c16-179">Step 4: Test FileAct Store and Forward (Pull) End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-pull-end-to-end-scenario.md)