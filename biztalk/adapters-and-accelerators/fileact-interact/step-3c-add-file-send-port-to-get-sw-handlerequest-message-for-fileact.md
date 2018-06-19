---
title: 步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息 FileAct 即時案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc0a9173-20df-4c73-80ee-755987d639d2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3705f0b649e7f8d1c85898677ddc0301851dd302
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224870"
---
# <a name="step-3c-add-a-file-send-port-to-capture-swhandlerequest-message-for-the-fileact-real-time-scenario"></a><span data-ttu-id="4deab-102">步驟 3c： 加入擷取 FileAct 即時案例 Sw:HandleRequest 訊息的 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="4deab-102">Step 3C: Add a FILE Send Port to Capture Sw:HandleRequest Message for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="4deab-103">在開始此步驟之前，必須先完成[步驟 3B： 將 FILEACT 接收位置新增 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="4deab-103">Before you begin this step, you must complete [Step 3B: Add a FILEACT Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-swhandlefilerequest-message"></a><span data-ttu-id="4deab-104">若要加入檔案傳送埠以擷取 Sw:HandleFileRequest 訊息</span><span class="sxs-lookup"><span data-stu-id="4deab-104">To add a FILE send port to capture Sw:HandleFileRequest message</span></span>  
  
1.  <span data-ttu-id="4deab-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="4deab-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="4deab-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4deab-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="4deab-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="4deab-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="4deab-108">在**傳送埠屬性**視窗中，傳送埠，Tutorial_FA_SendResponseToReceiver。</span><span class="sxs-lookup"><span data-stu-id="4deab-108">In the **Send Port Properties** window, name the send port, Tutorial_FA_SendResponseToReceiver.</span></span>  
  
5.  <span data-ttu-id="4deab-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="4deab-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="4deab-110">中**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\ResponseServer，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4deab-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ResponseServer, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="4deab-111">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4deab-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="4deab-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="4deab-112">**Use this**</span></span>|<span data-ttu-id="4deab-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="4deab-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="4deab-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="4deab-114">**Send handler**</span></span>|<span data-ttu-id="4deab-115">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="4deab-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="4deab-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="4deab-116">**Send pipeline**</span></span>|<span data-ttu-id="4deab-117">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="4deab-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="4deab-118">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4deab-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="4deab-119">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="4deab-119">**Use this**</span></span>|<span data-ttu-id="4deab-120">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="4deab-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="4deab-121">**屬性**</span><span class="sxs-lookup"><span data-stu-id="4deab-121">**Property**</span></span>|<span data-ttu-id="4deab-122">從下拉式清單選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="4deab-122">From the drop-down list, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="4deab-123">**運算子**</span><span class="sxs-lookup"><span data-stu-id="4deab-123">**Operator**</span></span>|<span data-ttu-id="4deab-124">從下拉式清單選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="4deab-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="4deab-125">**值**</span><span class="sxs-lookup"><span data-stu-id="4deab-125">**Value**</span></span>|<span data-ttu-id="4deab-126">型別**Sw HandleFileRequest**。</span><span class="sxs-lookup"><span data-stu-id="4deab-126">Type **Sw-HandleFileRequest**.</span></span>|  
    |<span data-ttu-id="4deab-127">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="4deab-127">**Group by**</span></span>|<span data-ttu-id="4deab-128">保留預設值</span><span class="sxs-lookup"><span data-stu-id="4deab-128">Leave the default value</span></span>|  
  
9. <span data-ttu-id="4deab-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4deab-129">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4deab-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4deab-130">See Also</span></span>  
 <span data-ttu-id="4deab-131">[步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="4deab-131">[Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="4deab-132">[步驟 3A： 新增 FILE 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="4deab-132">[Step 3A: Add a FILE Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="4deab-133">[步驟 3B： 新增 FILEACT 接收位置 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="4deab-133">[Step 3B: Add a FILEACT Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="4deab-134">[步驟 3D: FileAct 即時案例新增 FILEACT 傳送埠](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="4deab-134">[Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="4deab-135">步驟 3E： 加入擷取 FileAct 即時案例 Sw:ExchangeFileResponse 訊息的 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="4deab-135">Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)