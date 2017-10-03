---
title: "步驟 3c： 新增 FILE 傳送埠，以取得 Sw:HandleRequest-互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31e9c942-ba74-4ae2-b6e1-5266d0fbcb14
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ddc38913b8bf9ea5c9450334e58dfaeb5ff4ad3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-add-file-send-port-to-get-swhandlerequest-interact-real-time-scenario"></a><span data-ttu-id="d4e24-102">步驟 3c： 新增 FILE 傳送埠，以取得 Sw:HandleRequest-互動即時案例</span><span class="sxs-lookup"><span data-stu-id="d4e24-102">Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct real-time scenario</span></span>
<span data-ttu-id="d4e24-103">當您傳送訊息給夥伴時，SWIFT 轉換訊息標頭，並將訊息轉寄給您的夥伴為 Sw:HandleRequest 訊息。</span><span class="sxs-lookup"><span data-stu-id="d4e24-103">When you send a message to your partner, SWIFT transforms the message header and forwards the message to your partner as a Sw:HandleRequest message.</span></span> <span data-ttu-id="d4e24-104">在開始此步驟之前，必須先完成[步驟 3B： 互動即時案例中加入互動的接收位置](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="d4e24-104">Before you begin this step, you must complete [Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-swhandlerequest-message"></a><span data-ttu-id="d4e24-105">若要加入檔案傳送埠以擷取 Sw:HandleRequest 訊息</span><span class="sxs-lookup"><span data-stu-id="d4e24-105">To add a FILE send port to capture Sw:HandleRequest message</span></span>  
  
1.  <span data-ttu-id="d4e24-106">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d4e24-106">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d4e24-107">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4e24-107">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="d4e24-108">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="d4e24-108">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="d4e24-109">在**傳送埠屬性**視窗中，傳送埠**Tutorial_IA_SendResponseToReceiver**。</span><span class="sxs-lookup"><span data-stu-id="d4e24-109">In the **Send Port Properties** window, name the send port **Tutorial_IA_SendResponseToReceiver**.</span></span>  
  
5.  <span data-ttu-id="d4e24-110">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d4e24-110">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="d4e24-111">中**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Interact\HandleRequest，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d4e24-111">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Interact\HandleRequest, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="d4e24-112">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d4e24-112">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="d4e24-113">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="d4e24-113">**Use this**</span></span>|<span data-ttu-id="d4e24-114">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="d4e24-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="d4e24-115">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="d4e24-115">**Send handler**</span></span>|<span data-ttu-id="d4e24-116">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="d4e24-116">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="d4e24-117">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="d4e24-117">**Send pipeline**</span></span>|<span data-ttu-id="d4e24-118">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="d4e24-118">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="d4e24-119">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d4e24-119">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="d4e24-120">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="d4e24-120">**Use this**</span></span>|<span data-ttu-id="d4e24-121">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="d4e24-121">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="d4e24-122">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d4e24-122">**Property**</span></span>|<span data-ttu-id="d4e24-123">從下拉式清單選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="d4e24-123">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="d4e24-124">**運算子**</span><span class="sxs-lookup"><span data-stu-id="d4e24-124">**Operator**</span></span>|<span data-ttu-id="d4e24-125">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="d4e24-125">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="d4e24-126">**值**</span><span class="sxs-lookup"><span data-stu-id="d4e24-126">**Value**</span></span>|<span data-ttu-id="d4e24-127">型別**Tutorial_IA_HandleRequestOneWay_RealTime。**</span><span class="sxs-lookup"><span data-stu-id="d4e24-127">Type **Tutorial_IA_HandleRequestOneWay_RealTime.**</span></span>|  
    |<span data-ttu-id="d4e24-128">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="d4e24-128">**Group by**</span></span>|<span data-ttu-id="d4e24-129">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="d4e24-129">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="d4e24-130">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d4e24-130">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e24-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4e24-131">See Also</span></span>  
 <span data-ttu-id="d4e24-132">[步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="d4e24-132">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="d4e24-133">[步驟 3A： 新增 FILE 接收位置的互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="d4e24-133">[Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="d4e24-134">[步驟 3B： 加入互動接收位置互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="d4e24-134">[Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="d4e24-135">[步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span><span class="sxs-lookup"><span data-stu-id="d4e24-135">[Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span></span>  
 [<span data-ttu-id="d4e24-136">步驟 3E： 加入互動的傳送埠互動即時案例</span><span class="sxs-lookup"><span data-stu-id="d4e24-136">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)