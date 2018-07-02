---
title: 步驟 9： 測試 EDI 方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7a44e0f-496c-462f-bf03-1c2f842d13b6
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab6da406d2de066f9a1a7f4a99576ca9c2fa14d8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979671"
---
# <a name="step-9-test-the-edi-solution"></a><span data-ttu-id="c0c56-102">步驟 9： 測試 EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="c0c56-102">Step 9: Test the EDI Solution</span></span>
<span data-ttu-id="c0c56-103">![步驟 9 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")</span><span class="sxs-lookup"><span data-stu-id="c0c56-103">![Step 9 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")</span></span>  
  
 <span data-ttu-id="c0c56-104">在這個主題，您會測試輸入處理，並檢視處理資訊的 [EDI-交換狀態報告]。</span><span class="sxs-lookup"><span data-stu-id="c0c56-104">In this topic you test your inbound processing and view the EDI-Interchange Status Report for processing information.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c0c56-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="c0c56-105">Prerequisites</span></span>  
 <span data-ttu-id="c0c56-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="c0c56-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="testing-the-solution"></a><span data-ttu-id="c0c56-107">測試解決方案</span><span class="sxs-lookup"><span data-stu-id="c0c56-107">Testing the solution</span></span>  
  
1. <span data-ttu-id="c0c56-108">在 Windows 檔案總管中，移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations。</span><span class="sxs-lookup"><span data-stu-id="c0c56-108">In Windows Explorer, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations.</span></span> <span data-ttu-id="c0c56-109">複製**SamplePO.txt**檔案。</span><span class="sxs-lookup"><span data-stu-id="c0c56-109">Copy the **SamplePO.txt** file.</span></span>  
  
2. <span data-ttu-id="c0c56-110">貼上**SamplePO.txt**檔案載入[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0c56-110">Paste the **SamplePO.txt** file into the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM folder.</span></span>  
  
3. <span data-ttu-id="c0c56-111">移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0c56-111">Move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem folder.</span></span> <span data-ttu-id="c0c56-112">確認該資料夾包含輸出 txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0c56-112">Confirm that the folder contains an output txt file.</span></span>  
  
4. <span data-ttu-id="c0c56-113">開啟 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem 中的輸出檔以及 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations 中的 SamplePO.txt 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="c0c56-113">Open the output file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem and the SamplePO.txt input file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations.</span></span> <span data-ttu-id="c0c56-114">確認輸出訊息中的資料對應至原始中的資料**SamplePO.txt**檔案。</span><span class="sxs-lookup"><span data-stu-id="c0c56-114">Verify that the data in the output message corresponds to the data in the original **SamplePO.txt** file.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="c0c56-115">開啟 Visual Studio 中的 Inbound4010850_to_OrderFile.btm 檔案及檢查對應，即可驗證輸出檔中的資料是否已從輸入檔中的資料轉換過來。</span><span class="sxs-lookup"><span data-stu-id="c0c56-115">You can verify that the data in the output file has been transformed from the data in the input file by opening the Inbound4010850_to_OrderFile.btm file in Visual Studio, and checking the mappings.</span></span>  
  
5. <span data-ttu-id="c0c56-116">移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toTHEM_997 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0c56-116">Move to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toTHEM_997 folder.</span></span> <span data-ttu-id="c0c56-117">確認該資料夾包含輸出 997 通知 txt 檔案，且檔案中的 ST01 資料元素為 "997"。</span><span class="sxs-lookup"><span data-stu-id="c0c56-117">Confirm that the folder contains an output 997 acknowledgment txt file in which the ST01 data element is "997".</span></span>  
  
6. <span data-ttu-id="c0c56-118">在主控台樹狀目錄中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="c0c56-118">In the console tree of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **BizTalk Group**.</span></span> <span data-ttu-id="c0c56-119">在右窗格的底部，按一下**EDI 交換和相互關聯的 ACK 狀態**。</span><span class="sxs-lookup"><span data-stu-id="c0c56-119">At the bottom of the right pane, click **EDI Interchange and Correlated ACK Status**.</span></span>  
  
7. <span data-ttu-id="c0c56-120">在查詢運算式中，變更的運算子**狀態**欄位設為**等於**並變更**值**欄位**狀態**欄位**所有**。</span><span class="sxs-lookup"><span data-stu-id="c0c56-120">In the query expression, change the operator for the **Status** field to **Equals** and change the **Value** field for the **Status** field to **All**.</span></span> <span data-ttu-id="c0c56-121">刪除**交換日期時間欄位**（選取的資料列和索引鍵的面板上按下 DELETE 鍵）。</span><span class="sxs-lookup"><span data-stu-id="c0c56-121">Delete the **Interchange Date Time field** (select the row and press DELETE on the key board).</span></span>  
  
8. <span data-ttu-id="c0c56-122">按一下 **執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="c0c56-122">Click **Run Query**.</span></span>  
  
9. <span data-ttu-id="c0c56-123">確認兩則訊息都顯示在狀態報告中，一則的接收方向是從 THEM (Fabrikam) 至 US (OrderSystem) (850 訊息)，另一則的傳送方向是從 US (OrderSystem) 至 THEM (Fabrikam) (997 通知)。</span><span class="sxs-lookup"><span data-stu-id="c0c56-123">Verify that two messages are displayed in the status report, one in the receive direction from THEM (Fabrikam) to US (OrderSystem) (the 850 message), the other in the send direction from the US (OrderSystem) to THEM (Fabrikam) (the 997 acknowledgment).</span></span>  
  
10. <span data-ttu-id="c0c56-124">按兩下從 THEM 至 US 的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0c56-124">Double-click the message from THEM to US.</span></span> <span data-ttu-id="c0c56-125">在 **交換狀態和通知詳細資料**對話方塊方塊中，確認該交換的詳細資料會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="c0c56-125">In the **Interchange status and ACK  details** dialog box, verify that details of the interchange are displayed in the right pane.</span></span>  
  
11. <span data-ttu-id="c0c56-126">按一下 **功能通知**。</span><span class="sxs-lookup"><span data-stu-id="c0c56-126">Click **Functional ACK(s)**.</span></span> <span data-ttu-id="c0c56-127">確認右窗格中是否顯示通知的報告詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c0c56-127">Verify that the report details of the acknowledgment are displayed in the right pane.</span></span>  
  
12. <span data-ttu-id="c0c56-128">關閉 [交換狀態和通知詳細資料] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0c56-128">Close the Interchange status and ack details dialog box.</span></span>  
  
13. <span data-ttu-id="c0c56-129">在 **交換/通知狀態**窗格中，以滑鼠右鍵按一下從 THEM 至 US 的訊息，並按一下**交易集詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="c0c56-129">In the **Interchange/ACK Status** pane, right-click the message from THEM to US, and then click **Transaction Set Details**.</span></span> <span data-ttu-id="c0c56-130">中的項目上按一下滑鼠右鍵**查詢結果**窗格中，然後再按一下**檢視交易集內容**。</span><span class="sxs-lookup"><span data-stu-id="c0c56-130">Right-click the entry in the **Query results** pane, and then click **View Transaction Set Content**.</span></span> <span data-ttu-id="c0c56-131">確認交易集資料會顯示在**訊息的詳細資料** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0c56-131">Verify that the transaction set data is displayed in the **Message Details** dialog box.</span></span> <span data-ttu-id="c0c56-132">在 Windows 檔案總管中，開啟 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations 中的 SamplePO.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0c56-132">In Windows Explorer, open the SamplePO.txt file in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations.</span></span> <span data-ttu-id="c0c56-133">確認交易集顯示在**訊息的詳細資料**對話方塊則會在輸入訊息中，不含交換和群組標頭和結尾是相同。</span><span class="sxs-lookup"><span data-stu-id="c0c56-133">Verify that the transaction set displayed in the **Message Details** dialog box is the same as that in the input message, without the interchange and group headers and trailers.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c0c56-134">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c0c56-134">Next Steps</span></span>  
 <span data-ttu-id="c0c56-135">您已經完成了「EDI 介面開發人員教學課程」。</span><span class="sxs-lookup"><span data-stu-id="c0c56-135">You have completed the EDI Interface Developer Tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c56-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0c56-136">See Also</span></span>  
 <span data-ttu-id="c0c56-137">[教學課程 2: EDI 介面開發人員教學課程](../core/tutorial-2-edi-interface-developer-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="c0c56-137">[Tutorial 2: EDI Interface Developer Tutorial](../core/tutorial-2-edi-interface-developer-tutorial.md) </span></span>  
 [<span data-ttu-id="c0c56-138">步驟 1：準備 EDI 介面開發人員教學課程</span><span class="sxs-lookup"><span data-stu-id="c0c56-138">Step 1: Prepare for the EDI Interface Developer Tutorial</span></span>](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)