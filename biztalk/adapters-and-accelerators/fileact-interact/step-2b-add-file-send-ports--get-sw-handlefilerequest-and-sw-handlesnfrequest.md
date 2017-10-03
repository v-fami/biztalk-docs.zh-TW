---
title: "步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleFileRequest 和 Sw:HandleSnFRequest FileAct 存放與轉寄的訊息 （提取） 案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21d055e9-ff7c-4af1-983b-d03e8d4a94f6
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c2eb55cd6aca9b26b8a8ac47ab6dbe192f174d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2b-add-file-send-ports-to-capture-the-swhandlefilerequest-and-swhandlesnfrequest-messages-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="fa29e-102">步驟 2B： 將檔案傳送埠，以擷取 Sw:HandleFileRequest 和 Sw:HandleSnFRequest FileAct 存放與轉寄的訊息 （提取） 案例</span><span class="sxs-lookup"><span data-stu-id="fa29e-102">Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="fa29e-103">在開始此步驟之前，必須先完成[步驟 2A： 新增檔案接收位置 FileAct 存放與轉寄 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md)> 一節。</span><span class="sxs-lookup"><span data-stu-id="fa29e-103">Before you begin this step, you must complete the [Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) section.</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-the-sw-handlefilerequest-message"></a><span data-ttu-id="fa29e-104">若要加入檔案傳送埠以擷取 Sw: HandleFileRequest 訊息</span><span class="sxs-lookup"><span data-stu-id="fa29e-104">To add a FILE send port to capture the Sw: HandleFileRequest message</span></span>  
  
1.  <span data-ttu-id="fa29e-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fa29e-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fa29e-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="fa29e-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="fa29e-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="fa29e-108">在**傳送埠屬性**視窗中，傳送埠， **Tutorial_FA_SendPullResponsetoReceiver**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-108">In the **Send Port Properties** window, name the send port, **Tutorial_FA_SendPullResponsetoReceiver**.</span></span>  
  
5.  <span data-ttu-id="fa29e-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="fa29e-110">在**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\FileAct\PullResponse**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type **C:\SWIFTAdapterTutorial\FileAct\PullResponse**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="fa29e-111">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fa29e-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="fa29e-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="fa29e-112">**Use this**</span></span>|<span data-ttu-id="fa29e-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="fa29e-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="fa29e-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="fa29e-114">**Send handler**</span></span>|<span data-ttu-id="fa29e-115">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="fa29e-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="fa29e-116">**Send pipeline**</span></span>|<span data-ttu-id="fa29e-117">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="fa29e-118">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="fa29e-119">重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="fa29e-119">Repeat step 1 and 2.</span></span>  
  
10. <span data-ttu-id="fa29e-120">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **動態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-120">Right-click **Send Ports**, point to **New**, and then click **Dynamic Solicit-Response Send Port**.</span></span>  
  
11. <span data-ttu-id="fa29e-121">在**傳送埠屬性**視窗中，傳送埠**，Tutorial_IA_DynamicSendPort**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-121">In the **Send Port Properties** window, name the send port**, Tutorial_IA_DynamicSendPort**.</span></span>  
  
12. <span data-ttu-id="fa29e-122">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fa29e-122">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="fa29e-123">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="fa29e-123">**Use this**</span></span>|<span data-ttu-id="fa29e-124">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="fa29e-124">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="fa29e-125">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="fa29e-125">**Send pipeline**</span></span>|<span data-ttu-id="fa29e-126">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-126">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="fa29e-127">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="fa29e-127">**Receive pipeline**</span></span>|<span data-ttu-id="fa29e-128">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-128">From the drop-down list, select **XMLReceive**.</span></span>|  
  
13. <span data-ttu-id="fa29e-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="fa29e-129">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa29e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa29e-130">See Also</span></span>  
 <span data-ttu-id="fa29e-131">[步驟 2A： 新增檔案接收位置的 FileAct 存放與轉寄 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="fa29e-131">[Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="fa29e-132">步驟 2c： 新增為 FileAct 存放與轉寄 （提取） 實例 FILEACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="fa29e-132">Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md)