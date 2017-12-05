---
title: "步驟 1： 設定的 SWIFT 配接器互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f4d3e08-611a-4af1-a3e3-957ace3b74e6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab603f12e1f2c431f83af00dc79b57a9e416c251
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario"></a><span data-ttu-id="1106c-102">步驟 1： 設定的 SWIFT 配接器互動即時案例</span><span class="sxs-lookup"><span data-stu-id="1106c-102">Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="1106c-103">下列步驟說明如何設定 Interact 配接器的傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="1106c-103">The following steps explain how to configure the send handler for the Interact adapter.</span></span> <span data-ttu-id="1106c-104">在開始此程序之前，您必須完成中列出的需求[準備使用本教學課程](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)。</span><span class="sxs-lookup"><span data-stu-id="1106c-104">Before you begin the procedure, you must complete the requirements listed in [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).</span></span>  
  
### <a name="to-configure-the-swift-adapter"></a><span data-ttu-id="1106c-105">若要設定 SWIFT 配接器</span><span class="sxs-lookup"><span data-stu-id="1106c-105">To configure the SWIFT adapter</span></span>  
  
1.  <span data-ttu-id="1106c-106">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="1106c-106">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="1106c-107">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**平台設定**，依序展開**配接器**，以滑鼠右鍵按一下**INTERACT**，指向 **新增**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="1106c-107">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **INTERACT**, point to **New**, and then click **Send Handler**.</span></span>  
  
3.  <span data-ttu-id="1106c-108">在**互動 – 配接器處理常式屬性**對話方塊**一般**索引標籤上，從**主機名稱**下拉式清單中，選取**interacthost**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="1106c-108">In the **INTERACT – Adapter Handler Properties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **interacthost**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1106c-109">在**INTERACTTransport 屬性**對話方塊**屬性**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1106c-109">In the **INTERACTTransport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="1106c-110">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="1106c-110">**Use this**</span></span>|<span data-ttu-id="1106c-111">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="1106c-111">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="1106c-112">**引數**</span><span class="sxs-lookup"><span data-stu-id="1106c-112">**Arguments**</span></span>|<span data-ttu-id="1106c-113">輸入下列引數： **SagMessagePartner**\<互動的用戶端訊息夥伴建立 SAG\> **附註：**引數中的用戶端是 MessagePartner 您在 SAG 中設定。</span><span class="sxs-lookup"><span data-stu-id="1106c-113">Type the following argument: **SagMessagePartner**\<Interact Client Message Partner created in SAG\> **Note:**  The client in the argument is the MessagePartner you configured in SAG.</span></span>|  
    |<span data-ttu-id="1106c-114">**密碼編譯模式**</span><span class="sxs-lookup"><span data-stu-id="1106c-114">**Crypto Mode**</span></span>|<span data-ttu-id="1106c-115">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="1106c-115">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="1106c-116">**LogMessageBody**</span><span class="sxs-lookup"><span data-stu-id="1106c-116">**LogMessageBody**</span></span>|<span data-ttu-id="1106c-117">從下拉式清單選取`FALSE`。</span><span class="sxs-lookup"><span data-stu-id="1106c-117">From the drop-down list, select `FALSE`.</span></span> <span data-ttu-id="1106c-118">**注意：**如果設定為`TRUE`，它會保留的訊息本文的 「 追蹤 」 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1106c-118">**Note:**  If you set to `TRUE`, it preserves the message body in the tracking database.</span></span> <span data-ttu-id="1106c-119">不過，基於安全性理由，訊息本文可以永遠不會在檢視 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="1106c-119">However, for security reasons, the message body can never be viewed in the BAM portal.</span></span>|  
    |<span data-ttu-id="1106c-120">**記錄訊息**</span><span class="sxs-lookup"><span data-stu-id="1106c-120">**LogMessages**</span></span>|<span data-ttu-id="1106c-121">從下拉式清單選取`TRUE`。</span><span class="sxs-lookup"><span data-stu-id="1106c-121">From the drop-down list, select `TRUE`.</span></span> <span data-ttu-id="1106c-122">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="1106c-122">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="1106c-123">**啟用**</span><span class="sxs-lookup"><span data-stu-id="1106c-123">**Enable**</span></span>|<span data-ttu-id="1106c-124">False</span><span class="sxs-lookup"><span data-stu-id="1106c-124">False</span></span>|  
    |<span data-ttu-id="1106c-125">**密碼**</span><span class="sxs-lookup"><span data-stu-id="1106c-125">**Password**</span></span>|<span data-ttu-id="1106c-126">輸入您用來連接到 SAG 的密碼。</span><span class="sxs-lookup"><span data-stu-id="1106c-126">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="1106c-127">如需詳細資訊，請參閱 SAG 說明。</span><span class="sxs-lookup"><span data-stu-id="1106c-127">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="1106c-128">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="1106c-128">**User Name**</span></span>|<span data-ttu-id="1106c-129">輸入您用來連接到 SAG 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="1106c-129">Type the user name you use to connect to SAG.</span></span>|  
  
5.  <span data-ttu-id="1106c-130">按一下**確定**關閉互動傳輸屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1106c-130">Click **OK** to close the INTERACT Transport Properties dialog box.</span></span>  
  
6.  <span data-ttu-id="1106c-131">按一下**確定**關閉互動 – 配接器處理常式屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1106c-131">Click **OK** to close the INTERACT – Adapter Handler Properties dialog box.</span></span>  
  
7.  <span data-ttu-id="1106c-132">在訊息方塊中，按一下**確定**，然後重新啟動互動的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1106c-132">In the message box, click **OK**, and then restart the Interact host instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1106c-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="1106c-133">See Also</span></span>  
 <span data-ttu-id="1106c-134">[互動即時案例](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1106c-134">[InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="1106c-135">[步驟 1： 設定的 SWIFT 配接器互動即時案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1106c-135">[Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="1106c-136">[步驟 2： 將 SWIFTNet 組態新增至為 Paramfile 互動即時案例](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1106c-136">[Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="1106c-137">[步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1106c-137">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="1106c-138">步驟 4：測試 InterAct 即時端對端案例</span><span class="sxs-lookup"><span data-stu-id="1106c-138">Step 4: Test the InterAct Real-Time End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)