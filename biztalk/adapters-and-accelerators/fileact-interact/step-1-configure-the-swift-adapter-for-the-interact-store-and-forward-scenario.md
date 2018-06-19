---
title: 步驟 1： 設定 SWIFT 配接器互動存放區和情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03b81599-bd26-44dc-9cf3-73868248764c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f54effeeeb83d7a863298dcac4118ab1495ce3c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966078"
---
# <a name="step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="029dc-102">步驟 1： 設定 SWIFT 配接器互動存放區和轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="029dc-102">Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="029dc-103">在開始此步驟之前，必須先完成[準備使用本教學課程](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)。</span><span class="sxs-lookup"><span data-stu-id="029dc-103">Before you begin this step, you must complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).</span></span>  
  
### <a name="to-configure-the-swift-adapter"></a><span data-ttu-id="029dc-104">若要設定 SWIFT 配接器</span><span class="sxs-lookup"><span data-stu-id="029dc-104">To configure the SWIFT adapter</span></span>  
  
1.  <span data-ttu-id="029dc-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="029dc-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="029dc-106">在主控台樹狀目錄中，展開 BizTalk Server 管理、 BizTalk 群組、 展開**平台設定**，依序展開**配接器**，以滑鼠右鍵按一下**互動**，指向**新增**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="029dc-106">In the console tree, expand BizTalk Server Administration, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **INTERACT**, point to **New**, and then click **Send Handler**.</span></span>  
  
3.  <span data-ttu-id="029dc-107">在**互動 – 配接器處理常式屬性**對話方塊**一般**索引標籤上，從**主機名稱**下拉式清單中，選取**interacthost**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="029dc-107">In the **INTERACT – Adapter Handler Properties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **interacthost**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="029dc-108">在**互動傳輸屬性**對話方塊**屬性**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="029dc-108">In the **INTERACT Transport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="029dc-109">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="029dc-109">**Use this**</span></span>|<span data-ttu-id="029dc-110">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="029dc-110">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="029dc-111">**引數**</span><span class="sxs-lookup"><span data-stu-id="029dc-111">**Arguments**</span></span>|<span data-ttu-id="029dc-112">輸入下列引數: – SagMessagePartner\<互動的用戶端訊息夥伴建立 SAG\> **附註：** 引數中的用戶端是 MessagePartner SAG 中進行設定。</span><span class="sxs-lookup"><span data-stu-id="029dc-112">Type the following argument: –SagMessagePartner \<Interact Client Message Partner created in SAG\> **Note:**  The client in the argument is the MessagePartner you configured in SAG.</span></span>|  
    |<span data-ttu-id="029dc-113">**密碼編譯模式**</span><span class="sxs-lookup"><span data-stu-id="029dc-113">**Crypto Mode**</span></span>|<span data-ttu-id="029dc-114">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="029dc-114">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="029dc-115">**LogMessageBody**</span><span class="sxs-lookup"><span data-stu-id="029dc-115">**LogMessageBody**</span></span>|<span data-ttu-id="029dc-116">從下拉式清單選取**FALSE**。</span><span class="sxs-lookup"><span data-stu-id="029dc-116">From the drop-down list, select **FALSE**.</span></span> <span data-ttu-id="029dc-117">**注意：** 如果設為 TRUE 時，它會保留的訊息本文的 「 BizTalk 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="029dc-117">**Note:**  If you set to TRUE, it preserves the message body in the BizTalk Tracking database.</span></span> <span data-ttu-id="029dc-118">不過，基於安全性理由，訊息本文可以永遠不會在檢視 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="029dc-118">However, for security reasons, the message body can never be viewed in the BAM portal.</span></span>|  
    |<span data-ttu-id="029dc-119">**記錄訊息**</span><span class="sxs-lookup"><span data-stu-id="029dc-119">**LogMessages**</span></span>|<span data-ttu-id="029dc-120">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="029dc-120">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="029dc-121">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="029dc-121">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="029dc-122">**啟用**</span><span class="sxs-lookup"><span data-stu-id="029dc-122">**Enable**</span></span>|<span data-ttu-id="029dc-123">False。</span><span class="sxs-lookup"><span data-stu-id="029dc-123">False.</span></span>|  
    |<span data-ttu-id="029dc-124">**密碼**</span><span class="sxs-lookup"><span data-stu-id="029dc-124">**Password**</span></span>|<span data-ttu-id="029dc-125">輸入您用來連接到 SAG 的密碼。</span><span class="sxs-lookup"><span data-stu-id="029dc-125">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="029dc-126">如需詳細資訊，請參閱 SAG 說明。</span><span class="sxs-lookup"><span data-stu-id="029dc-126">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="029dc-127">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="029dc-127">**Username**</span></span>|<span data-ttu-id="029dc-128">輸入您用來連接到 SAG 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="029dc-128">Type the user name you use to connect to SAG.</span></span>|  
  
5.  <span data-ttu-id="029dc-129">按一下**確定**關閉互動傳輸屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="029dc-129">Click **OK** to close the INTERACT Transport Properties dialog box.</span></span>  
  
6.  <span data-ttu-id="029dc-130">按一下**確定**關閉互動 – 配接器處理常式屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="029dc-130">Click **OK** to close the INTERACT – Adapter Handler Properties dialog box.</span></span>  
  
7.  <span data-ttu-id="029dc-131">在訊息方塊中，按一下**確定**，然後重新啟動互動的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="029dc-131">In the message box, click **OK**, and then restart the InterAct host instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029dc-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="029dc-132">See Also</span></span>  
 <span data-ttu-id="029dc-133">[儲存和轉送 (Push) 的案例進行互動](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="029dc-133">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="029dc-134">[步驟 2： 將 SWIFTNet 組態新增至 Paramfile 互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="029dc-134">[Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md) </span></span>  
 <span data-ttu-id="029dc-135">[步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="029dc-135">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="029dc-136">步驟 4：測試 InterAct 儲存和轉寄端對端案例</span><span class="sxs-lookup"><span data-stu-id="029dc-136">Step 4: Test the InterAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)