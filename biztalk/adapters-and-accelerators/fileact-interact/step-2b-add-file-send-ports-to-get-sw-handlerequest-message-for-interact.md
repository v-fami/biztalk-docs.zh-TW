---
title: '步驟 2B： 新增 FILE 傳送埠以擷取 sw: handlerequest 訊息針對 InterAct 儲存和轉寄 （提取） 案例 |Microsoft Docs'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa22d6e7-f1bd-43ad-9a0e-0b287057d20f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56cee834f5974d993dfeaa8fbfee8313eeb74064
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004439"
---
# <a name="step-2b-add-file-send-ports-to-capture-the-swhandlerequest-message-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="dc4cd-102">步驟 2B： 新增 FILE 傳送埠以擷取 InterAct 儲存和轉寄 （提取） 案例的 sw: handlerequest 訊息</span><span class="sxs-lookup"><span data-stu-id="dc4cd-102">Step 2B: Add FILE Send Ports to Capture the Sw:HandleRequest Message for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="dc4cd-103">在開始此步驟之前，必須先完成[步驟 2A： 新增檔案接收位置針對 InterAct 儲存和轉寄 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-103">Before you begin this step, you must complete [Step 2A: Add FILE Receive Locations for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md).</span></span>  

### <a name="to-add-a-file-send-port-to-capture-the-swhandlerequest-message"></a><span data-ttu-id="dc4cd-104">若要新增 FILE 傳送埠以擷取 sw: handlerequest 訊息</span><span class="sxs-lookup"><span data-stu-id="dc4cd-104">To add a FILE send port to capture the Sw:HandleRequest message</span></span>  

1. <span data-ttu-id="dc4cd-105">開始**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-105">Start **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="dc4cd-106">在主控台樹狀目錄中，展開 BizTalk 群組，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  

3. <span data-ttu-id="dc4cd-107">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  

4. <span data-ttu-id="dc4cd-108">在 **傳送埠屬性**視窗中，傳送埠，命名**Tutorial_IA_SendPullResponsetoReceiver**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-108">In the **Send Port Properties** window, name the send port, **Tutorial_IA_SendPullResponsetoReceiver**.</span></span>  

5. <span data-ttu-id="dc4cd-109">在 [**傳送埠屬性**] 視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  

6. <span data-ttu-id="dc4cd-110">在  **FILE 傳輸屬性**對話方塊的 **目的地資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\PullResponse**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type **C:\SWIFTAdapterTutorial\Interact\PullResponse**, and then click **OK**.</span></span>  

7. <span data-ttu-id="dc4cd-111">在 [**傳送埠屬性**] 視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dc4cd-111">In the **Send Port Properties** window, do the following:</span></span>  


   |   <span data-ttu-id="dc4cd-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-112">**Use this**</span></span>    |                        <span data-ttu-id="dc4cd-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-113">**To do this**</span></span>                         |
   |-------------------|---------------------------------------------------------------|
   | <span data-ttu-id="dc4cd-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-114">**Send handler**</span></span>  | <span data-ttu-id="dc4cd-115">從下拉式清單中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-115">From the drop-down list, select **BizTalkServerApplication**.</span></span> |
   | <span data-ttu-id="dc4cd-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-116">**Send pipeline**</span></span> |       <span data-ttu-id="dc4cd-117">從下拉式清單中，選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-117">From the drop-down list, select **XMLTransmit**.</span></span>        |


8. <span data-ttu-id="dc4cd-118">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-118">Click **OK**.</span></span>  

9. <span data-ttu-id="dc4cd-119">重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-119">Repeat step 1 and 2.</span></span>  

10. <span data-ttu-id="dc4cd-120">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**動態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-120">Right-click **Send Ports**, point to **New**, and then click **Dynamic Solicit-Response Send Port**.</span></span>  

11. <span data-ttu-id="dc4cd-121">在 **傳送埠屬性**視窗中，傳送埠命名<strong>，Tutorial_IA_DynamicSendPort</strong>。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-121">In the **Send Port Properties** window, name the send port<strong>, Tutorial_IA_DynamicSendPort</strong>.</span></span>  

12. <span data-ttu-id="dc4cd-122">在 [**傳送埠屬性**] 視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dc4cd-122">In the **Send Port Properties** window, do the following:</span></span>  


    |     <span data-ttu-id="dc4cd-123">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-123">**Use this**</span></span>     |                  <span data-ttu-id="dc4cd-124">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-124">**To do this**</span></span>                  |
    |----------------------|--------------------------------------------------|
    |  <span data-ttu-id="dc4cd-125">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-125">**Send pipeline**</span></span>   | <span data-ttu-id="dc4cd-126">從下拉式清單中，選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-126">From the drop-down list, select **XMLTransmit**.</span></span> |
    | <span data-ttu-id="dc4cd-127">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="dc4cd-127">**Receive pipeline**</span></span> | <span data-ttu-id="dc4cd-128">從下拉式清單中，選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-128">From the drop-down list, select **XMLReceive**.</span></span>  |


13. <span data-ttu-id="dc4cd-129">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="dc4cd-129">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="dc4cd-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4cd-130">See Also</span></span>  
 <span data-ttu-id="dc4cd-131">[步驟 2A： 針對 InterAct 儲存和轉寄 （提取） 案例新增檔案接收位置](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="dc4cd-131">[Step 2A: Add FILE Receive Locations for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="dc4cd-132">步驟 2C：針對 InterAct 儲存和轉寄 (提取) 案例新增 INTERACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="dc4cd-132">Step 2C: Add an INTERACT Send Port for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md)