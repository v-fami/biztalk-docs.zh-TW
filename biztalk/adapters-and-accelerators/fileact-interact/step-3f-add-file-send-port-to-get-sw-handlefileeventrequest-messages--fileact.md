---
title: 步驟 3F： 新增檔案傳送埠 FileAct 即時案例以擷取 Sw HandleFileEventRequest 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b7594b0-0443-41b7-ae04-55b2cc8bf90e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1d70c338696f1c4455161a88c8d2988e0ea0ccb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225526"
---
# <a name="step-3f-add-a-file-send-port-for-the-fileact-real-time-scenario-to-capture-sw-handlefileeventrequest-messages"></a><span data-ttu-id="a5e7c-102">步驟 3F： 新增 FileAct 即時案例以擷取 Sw HandleFileEventRequest 訊息的 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="a5e7c-102">Step 3F: Add a FILE Send Port for the FileAct Real-Time Scenario to Capture Sw-HandleFileEventRequest Messages</span></span>
<span data-ttu-id="a5e7c-103">在開始此步驟之前，必須先完成[步驟 3E: FileAct 即時案例中，將檔案傳送埠新增至擷取 Sw:ExchangeFileResponse 訊息](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)</span><span class="sxs-lookup"><span data-stu-id="a5e7c-103">Before you begin this step, you must complete [Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-status-events"></a><span data-ttu-id="a5e7c-104">若要新增 FILE 傳送埠來擷取狀態事件：</span><span class="sxs-lookup"><span data-stu-id="a5e7c-104">To add a FILE send port to capture Status Events:</span></span>  
  
1.  <span data-ttu-id="a5e7c-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a5e7c-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="a5e7c-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
4.  <span data-ttu-id="a5e7c-108">在**傳送埠屬性**視窗中，傳送埠，Tutorial_ GetStatusReports。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-108">In the **Send Port Properties** window, name the send port, Tutorial_ GetStatusReports.</span></span>  
  
5.  <span data-ttu-id="a5e7c-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="a5e7c-110">在**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\ StatusEvents，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ StatusEvents, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="a5e7c-111">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a5e7c-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="a5e7c-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-112">**Use this**</span></span>|<span data-ttu-id="a5e7c-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a5e7c-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-114">**Send handler**</span></span>|<span data-ttu-id="a5e7c-115">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="a5e7c-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-116">**Send pipeline**</span></span>|<span data-ttu-id="a5e7c-117">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="a5e7c-118">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a5e7c-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="a5e7c-119">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-119">**Use this**</span></span>|<span data-ttu-id="a5e7c-120">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="a5e7c-121">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-121">**Property**</span></span>|<span data-ttu-id="a5e7c-122">選取 [BTS]。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-122">Select BTS.</span></span> <span data-ttu-id="a5e7c-123">MessageType</span><span class="sxs-lookup"><span data-stu-id="a5e7c-123">MessageType</span></span>|  
    |<span data-ttu-id="a5e7c-124">**運算子**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-124">**Operator**</span></span>|<span data-ttu-id="a5e7c-125">選取 = =</span><span class="sxs-lookup"><span data-stu-id="a5e7c-125">Select ==</span></span>|  
    |<span data-ttu-id="a5e7c-126">**值**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-126">**Value**</span></span>|<span data-ttu-id="a5e7c-127">型別 Sw HandleFileEventRequest</span><span class="sxs-lookup"><span data-stu-id="a5e7c-127">Type Sw-HandleFileEventRequest</span></span>|  
    |<span data-ttu-id="a5e7c-128">**群組**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-128">**Group**</span></span>|<span data-ttu-id="a5e7c-129">或</span><span class="sxs-lookup"><span data-stu-id="a5e7c-129">Or</span></span>|  
    |<span data-ttu-id="a5e7c-130">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-130">**Property**</span></span>|<span data-ttu-id="a5e7c-131">選取 [BTS]。</span><span class="sxs-lookup"><span data-stu-id="a5e7c-131">Select BTS.</span></span> <span data-ttu-id="a5e7c-132">MessageType</span><span class="sxs-lookup"><span data-stu-id="a5e7c-132">MessageType</span></span>|  
    |<span data-ttu-id="a5e7c-133">**運算子**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-133">**Operator**</span></span>|<span data-ttu-id="a5e7c-134">選取 = =</span><span class="sxs-lookup"><span data-stu-id="a5e7c-134">Select ==</span></span>|  
    |<span data-ttu-id="a5e7c-135">**值**</span><span class="sxs-lookup"><span data-stu-id="a5e7c-135">**Value**</span></span>|<span data-ttu-id="a5e7c-136">型別 Sw ExchangeSnFResponse</span><span class="sxs-lookup"><span data-stu-id="a5e7c-136">Type Sw-ExchangeSnFResponse</span></span>|