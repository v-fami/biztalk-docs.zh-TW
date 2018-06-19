---
title: 步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e05e4d20-4cf2-402f-aaea-66987cb6515a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a0c8c8721d9f7de7b1cd1e57537aa02d2ed8fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225886"
---
# <a name="step-3d-add-a-file-send-port-to-capture-the-swhandleresponse-message-for-the-interact-real-time-scenario"></a><span data-ttu-id="87117-102">步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例</span><span class="sxs-lookup"><span data-stu-id="87117-102">Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="87117-103">完成[步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="87117-103">Complete [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) before you begin this step.</span></span>
  
## <a name="add-a-file-send-port-to-capture-swhandleresponse-message"></a><span data-ttu-id="87117-104">將檔案傳送埠以擷取 Sw:HandleResponse 訊息</span><span class="sxs-lookup"><span data-stu-id="87117-104">Add a FILE send port to capture Sw:HandleResponse message</span></span>  
  
1.  <span data-ttu-id="87117-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="87117-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="87117-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="87117-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="87117-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="87117-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="87117-108">在**傳送埠屬性**視窗中，傳送埠**Tutorial_IA_SendResponseToSender**。</span><span class="sxs-lookup"><span data-stu-id="87117-108">In the **Send Port Properties** window, name the send port **Tutorial_IA_SendResponseToSender**.</span></span>  
  
5.  <span data-ttu-id="87117-109">在**傳送埠屬性**視窗中，從**Transporttype**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="87117-109">In the **Send Port Properties** window, from the **Transporttype** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="87117-110">在**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\Response**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="87117-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type **C:\SWIFTAdapterTutorial\Interact\Response**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="87117-111">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="87117-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="87117-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="87117-112">**Use this**</span></span>|<span data-ttu-id="87117-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="87117-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="87117-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="87117-114">**Send handler**</span></span>|<span data-ttu-id="87117-115">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="87117-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="87117-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="87117-116">**Send pipeline**</span></span>|<span data-ttu-id="87117-117">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="87117-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="87117-118">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="87117-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="87117-119">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="87117-119">**Use this**</span></span>|<span data-ttu-id="87117-120">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="87117-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="87117-121">第一次資料列：**屬性**</span><span class="sxs-lookup"><span data-stu-id="87117-121">First row: **Property**</span></span>|<span data-ttu-id="87117-122">從下拉式清單選取**BTS。SPName**。</span><span class="sxs-lookup"><span data-stu-id="87117-122">From the drop-down list, select **BTS.SPName**.</span></span>|  
    |<span data-ttu-id="87117-123">第一次資料列：**運算子**</span><span class="sxs-lookup"><span data-stu-id="87117-123">First row: **Operator**</span></span>|<span data-ttu-id="87117-124">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="87117-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="87117-125">第一次資料列：**值**</span><span class="sxs-lookup"><span data-stu-id="87117-125">First row: **Value**</span></span>|<span data-ttu-id="87117-126">型別**Tutorial_IA_HandleRequest_RealTime**。</span><span class="sxs-lookup"><span data-stu-id="87117-126">Type **Tutorial_IA_HandleRequest_RealTime**.</span></span>|  
    |<span data-ttu-id="87117-127">第一次資料列：**分組**</span><span class="sxs-lookup"><span data-stu-id="87117-127">First row: **Group by**</span></span>|<span data-ttu-id="87117-128">從下拉式清單選取**或**。</span><span class="sxs-lookup"><span data-stu-id="87117-128">From the drop-down list, select **OR**.</span></span>|  
    |<span data-ttu-id="87117-129">第二個資料列：**屬性**</span><span class="sxs-lookup"><span data-stu-id="87117-129">Second row: **Property**</span></span>|<span data-ttu-id="87117-130">從下拉式清單選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="87117-130">From the drop-down list, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="87117-131">第二個資料列：**運算子**</span><span class="sxs-lookup"><span data-stu-id="87117-131">Second row: **Operator**</span></span>|<span data-ttu-id="87117-132">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="87117-132">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="87117-133">第二個資料列：**值**</span><span class="sxs-lookup"><span data-stu-id="87117-133">Second row: **Value**</span></span>|<span data-ttu-id="87117-134">型別**SwInt ExchangeResponse**。</span><span class="sxs-lookup"><span data-stu-id="87117-134">Type **SwInt-ExchangeResponse**.</span></span>|  
    |<span data-ttu-id="87117-135">第二個資料列：**分組**</span><span class="sxs-lookup"><span data-stu-id="87117-135">Second row: **Group by**</span></span>|<span data-ttu-id="87117-136">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="87117-136">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="87117-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="87117-137">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87117-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87117-138">See Also</span></span>  
 <span data-ttu-id="87117-139">[步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="87117-139">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="87117-140">[步驟 3A： 新增 FILE 接收位置的互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="87117-140">[Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="87117-141">[步驟 3B： 加入互動接收位置互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="87117-141">[Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="87117-142">[步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="87117-142">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="87117-143">步驟 3E： 加入互動的傳送埠互動即時案例</span><span class="sxs-lookup"><span data-stu-id="87117-143">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)