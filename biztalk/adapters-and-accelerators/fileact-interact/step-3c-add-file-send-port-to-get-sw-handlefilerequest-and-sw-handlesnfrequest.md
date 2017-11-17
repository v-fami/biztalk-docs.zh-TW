---
title: "步驟 3c： 新增檔案傳送埠，以便擷取 FileAct 存放與轉寄案例的 Sw:HandleFileRequest 和 Sw:HandleSnFRequest 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc41e352-acc5-47eb-bb87-38990f0e76a7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae6858164ee82f935c607246e7e93ffd86908f93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-add-a-file-send-port-to-capture-the-swhandlefilerequest-and-swhandlesnfrequest-messages-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="1beeb-102">步驟 3c： 加入擷取 FileAct 存放與轉寄案例的 Sw:HandleFileRequest 和 Sw:HandleSnFRequest 訊息的 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="1beeb-102">Step 3C: Add a FILE Send Port to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="1beeb-103">在開始此步驟之前，必須先完成[步驟 3B： 新增 FILEACT 接收位置為 FileAct 存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="1beeb-103">Before you begin this step, you must complete [Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-swresponseserver-message"></a><span data-ttu-id="1beeb-104">若要加入檔案傳送埠以擷取 Sw:ResponseServer 訊息</span><span class="sxs-lookup"><span data-stu-id="1beeb-104">To add a FILE send port to capture Sw:ResponseServer message</span></span>  
  
1.  <span data-ttu-id="1beeb-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="1beeb-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1beeb-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="1beeb-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="1beeb-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="1beeb-108">在**傳送埠屬性**視窗中，傳送埠，Tutorial_FA_SendResponseToReceiver。</span><span class="sxs-lookup"><span data-stu-id="1beeb-108">In the **Send Port Properties** window, name the send port, Tutorial_FA_SendResponseToReceiver.</span></span>  
  
5.  <span data-ttu-id="1beeb-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="1beeb-110">中**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\ResponseServer，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ResponseServer, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="1beeb-111">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1beeb-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="1beeb-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="1beeb-112">**Use this**</span></span>|<span data-ttu-id="1beeb-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="1beeb-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="1beeb-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="1beeb-114">**Send handler**</span></span>|<span data-ttu-id="1beeb-115">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="1beeb-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="1beeb-116">**Send pipeline**</span></span>|<span data-ttu-id="1beeb-117">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="1beeb-118">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1beeb-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="1beeb-119">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="1beeb-119">**Use this**</span></span>|<span data-ttu-id="1beeb-120">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="1beeb-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="1beeb-121">**第一次資料列： 屬性**</span><span class="sxs-lookup"><span data-stu-id="1beeb-121">**First row: Property**</span></span>|<span data-ttu-id="1beeb-122">從下拉式清單選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-122">From the drop-down list, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="1beeb-123">**第一次資料列： 運算子**</span><span class="sxs-lookup"><span data-stu-id="1beeb-123">**First row: Operator**</span></span>|<span data-ttu-id="1beeb-124">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="1beeb-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="1beeb-125">**第一次資料列： 值**</span><span class="sxs-lookup"><span data-stu-id="1beeb-125">**First row: Value**</span></span>|<span data-ttu-id="1beeb-126">型別**Sw HandleFileRequest**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-126">Type **Sw-HandleFileRequest**.</span></span>|  
    |<span data-ttu-id="1beeb-127">**第一次資料列： Group by**</span><span class="sxs-lookup"><span data-stu-id="1beeb-127">**First row: Group by**</span></span>|<span data-ttu-id="1beeb-128">從下拉式清單選取**或**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-128">From the drop-down list, select **OR**.</span></span>|  
    |<span data-ttu-id="1beeb-129">**第二個資料列： 屬性**</span><span class="sxs-lookup"><span data-stu-id="1beeb-129">**Second row: Property**</span></span>|<span data-ttu-id="1beeb-130">從下拉式清單選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-130">From the drop-down list, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="1beeb-131">**第二個資料列： 運算子**</span><span class="sxs-lookup"><span data-stu-id="1beeb-131">**Second row: Operator**</span></span>|<span data-ttu-id="1beeb-132">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="1beeb-132">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="1beeb-133">**第二個資料列： 值**</span><span class="sxs-lookup"><span data-stu-id="1beeb-133">**Second row: Value**</span></span>|<span data-ttu-id="1beeb-134">型別**Sw HandleSnFRequest**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-134">Type **Sw-HandleSnFRequest**.</span></span>|  
    |<span data-ttu-id="1beeb-135">**第二個資料列： Group by**</span><span class="sxs-lookup"><span data-stu-id="1beeb-135">**Second row: Group by**</span></span>|<span data-ttu-id="1beeb-136">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="1beeb-136">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="1beeb-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1beeb-137">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1beeb-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1beeb-138">See Also</span></span>  
 <span data-ttu-id="1beeb-139">[步驟 3： 建立傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="1beeb-139">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 <span data-ttu-id="1beeb-140">[步驟 3A： 新增 FILE 接收位置為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1beeb-140">[Step 3A: Add a FILE Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="1beeb-141">[步驟 3B： 新增 FILEACT 接收位置 FileAct 存放與轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1beeb-141">[Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="1beeb-142">步驟 3D： 新增為 FileAct 存放與轉寄實例 FILEACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="1beeb-142">Step 3D: Add a FILEACT Send Port for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)