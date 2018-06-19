---
title: 步驟 3E： 新增檔案傳送埠，以便擷取 Sw:ExchangeFileResponse 訊息 FileAct 即時案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9314f86-a2c9-4ef3-8474-b7e2e2f8bf66
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18e26d13196a46045191b9e5767040e2216ceba2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224934"
---
# <a name="step-3e-add-a-file-send-port-to-capture-swexchangefileresponse-message-for-the-fileact-real-time-scenario"></a><span data-ttu-id="a3f3b-102">步驟 3E： 加入擷取 FileAct 即時案例 Sw:ExchangeFileResponse 訊息的 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="a3f3b-102">Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="a3f3b-103">在開始此步驟之前，必須先完成[步驟 3D： 新增 FILEACT 傳送埠 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-103">Before you begin this step, you must complete [Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-swexchangefileresponse-message"></a><span data-ttu-id="a3f3b-104">若要加入檔案傳送埠以擷取 Sw:ExchangeFileResponse 訊息</span><span class="sxs-lookup"><span data-stu-id="a3f3b-104">To add a FILE send port to capture Sw:ExchangeFileResponse message</span></span>  
  
1.  <span data-ttu-id="a3f3b-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a3f3b-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="a3f3b-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="a3f3b-108">在**傳送埠屬性**視窗中，傳送埠，Tutorial_FA_SendResponseToSender。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-108">In the **Send Port Properties** window, name the send port, Tutorial_FA_SendResponseToSender.</span></span>  
  
5.  <span data-ttu-id="a3f3b-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="a3f3b-110">中**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\ResponseClient，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ResponseClient, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="a3f3b-111">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a3f3b-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="a3f3b-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-112">**Use this**</span></span>|<span data-ttu-id="a3f3b-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a3f3b-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-114">**Send handler**</span></span>|<span data-ttu-id="a3f3b-115">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="a3f3b-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-116">**Send pipeline**</span></span>|<span data-ttu-id="a3f3b-117">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="a3f3b-118">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a3f3b-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="a3f3b-119">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-119">**Use this**</span></span>|<span data-ttu-id="a3f3b-120">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a3f3b-121">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-121">**Property**</span></span>|<span data-ttu-id="a3f3b-122">從下拉式清單選取**BTS。SPName**。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-122">From the drop-down list, select **BTS.SPName**.</span></span>|  
    |<span data-ttu-id="a3f3b-123">**運算子**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-123">**Operator**</span></span>|<span data-ttu-id="a3f3b-124">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="a3f3b-125">**值**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-125">**Value**</span></span>|<span data-ttu-id="a3f3b-126">型別 Tutorial_FA_SendRequest_RealTime。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-126">Type Tutorial_FA_SendRequest_RealTime.</span></span>|  
    |<span data-ttu-id="a3f3b-127">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="a3f3b-127">**Group by**</span></span>|<span data-ttu-id="a3f3b-128">保留預設值。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-128">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="a3f3b-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a3f3b-129">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f3b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f3b-130">See Also</span></span>  
 <span data-ttu-id="a3f3b-131">[步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a3f3b-131">[Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="a3f3b-132">[步驟 3A： 新增 FILE 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a3f3b-132">[Step 3A: Add a FILE Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="a3f3b-133">[步驟 3B： 新增 FILEACT 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a3f3b-133">[Step 3B: Add a FILEACT Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="a3f3b-134">[步驟 3c： 加入擷取 FileAct 即時案例 Sw:HandleRequest 訊息的 FILE 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md) </span><span class="sxs-lookup"><span data-stu-id="a3f3b-134">[Step 3C: Add a FILE Send Port to Capture Sw:HandleRequest Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md) </span></span>  
 [<span data-ttu-id="a3f3b-135">步驟 3D: FileAct 即時案例新增 FILEACT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="a3f3b-135">Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)