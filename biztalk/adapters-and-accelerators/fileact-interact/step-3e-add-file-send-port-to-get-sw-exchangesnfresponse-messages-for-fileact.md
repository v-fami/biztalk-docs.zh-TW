---
title: "步驟 3E： 新增檔案傳送埠的 FileAct 存放與轉寄案例以擷取 Sw ExchangeSnFResponse 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04bad2ab-1ea4-4602-9dee-5b9af9be3b93
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44cf320f22f5acc2511d6327c36c54cda8f0dd1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-add-a-file-send-port-for-the-fileact-store-and-forward-scenario-to-capture-sw-exchangesnfresponse-messages"></a><span data-ttu-id="70338-102">步驟 3E： 新增 FileAct 存放與轉寄案例以擷取 Sw ExchangeSnFResponse 訊息 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="70338-102">Step 3E: Add a FILE Send Port for the FileAct Store and Forward Scenario to capture Sw-ExchangeSnFResponse messages</span></span>
<span data-ttu-id="70338-103">在開始此步驟之前，必須先完成[步驟 3D： 新增 FILEACT 傳送埠為 FileAct 存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="70338-103">Before you begin this step, you must complete [Step 3D: Add a FILEACT Send Port for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-status-events"></a><span data-ttu-id="70338-104">若要新增 FILE 傳送埠來擷取狀態事件：</span><span class="sxs-lookup"><span data-stu-id="70338-104">To add a FILE send port to capture Status Events:</span></span>  
  
1.  <span data-ttu-id="70338-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="70338-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="70338-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="70338-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="70338-107">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="70338-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
4.  <span data-ttu-id="70338-108">在**傳送埠屬性**視窗中，傳送埠，Tutorial_ GetStatusReports。</span><span class="sxs-lookup"><span data-stu-id="70338-108">In the **Send Port Properties** window, name the send port, Tutorial_ GetStatusReports.</span></span>  
  
5.  <span data-ttu-id="70338-109">在**傳送埠屬性**視窗中，從**傳輸類型**下拉式清單中，選取**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="70338-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="70338-110">在**FILE 傳輸屬性**對話方塊中，於**目的地資料夾**方塊、 輸入 C:\SWIFTAdapterTutorial\Fileact\ StatusEvents，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="70338-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ StatusEvents, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="70338-111">在**傳送埠屬性**視窗中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="70338-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="70338-112">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="70338-112">**Use this**</span></span>|<span data-ttu-id="70338-113">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="70338-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="70338-114">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="70338-114">**Send handler**</span></span>|<span data-ttu-id="70338-115">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="70338-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="70338-116">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="70338-116">**Send pipeline**</span></span>|<span data-ttu-id="70338-117">從下拉式清單選取**XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="70338-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="70338-118">在**傳送埠屬性**視窗，請在**篩選**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="70338-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="70338-119">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="70338-119">**Use this**</span></span>|<span data-ttu-id="70338-120">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="70338-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="70338-121">**屬性**</span><span class="sxs-lookup"><span data-stu-id="70338-121">**Property**</span></span>|<span data-ttu-id="70338-122">選取 [BTS]。訊息類型</span><span class="sxs-lookup"><span data-stu-id="70338-122">Select BTS.MessageType</span></span>|  
    |<span data-ttu-id="70338-123">**運算子**</span><span class="sxs-lookup"><span data-stu-id="70338-123">**Operator**</span></span>|<span data-ttu-id="70338-124">選取 = =</span><span class="sxs-lookup"><span data-stu-id="70338-124">Select ==</span></span>|  
    |<span data-ttu-id="70338-125">**值**</span><span class="sxs-lookup"><span data-stu-id="70338-125">**Value**</span></span>|<span data-ttu-id="70338-126">型別 Sw HandleFileEventRequest</span><span class="sxs-lookup"><span data-stu-id="70338-126">Type Sw-HandleFileEventRequest</span></span>|  
    |<span data-ttu-id="70338-127">**群組**</span><span class="sxs-lookup"><span data-stu-id="70338-127">**Group**</span></span>|<span data-ttu-id="70338-128">或</span><span class="sxs-lookup"><span data-stu-id="70338-128">Or</span></span>|  
    |<span data-ttu-id="70338-129">**屬性**</span><span class="sxs-lookup"><span data-stu-id="70338-129">**Property**</span></span>|<span data-ttu-id="70338-130">選取 [BTS]。</span><span class="sxs-lookup"><span data-stu-id="70338-130">Select BTS.</span></span> <span data-ttu-id="70338-131">MessageType</span><span class="sxs-lookup"><span data-stu-id="70338-131">MessageType</span></span>|  
    |<span data-ttu-id="70338-132">**運算子**</span><span class="sxs-lookup"><span data-stu-id="70338-132">**Operator**</span></span>|<span data-ttu-id="70338-133">選取 = =</span><span class="sxs-lookup"><span data-stu-id="70338-133">Select ==</span></span>|  
    |<span data-ttu-id="70338-134">**值**</span><span class="sxs-lookup"><span data-stu-id="70338-134">**Value**</span></span>|<span data-ttu-id="70338-135">型別 Sw ExchangeSnFResponse</span><span class="sxs-lookup"><span data-stu-id="70338-135">Type Sw-ExchangeSnFResponse</span></span>|