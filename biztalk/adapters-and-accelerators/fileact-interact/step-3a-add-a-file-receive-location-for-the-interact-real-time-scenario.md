---
title: "步驟 3A： 新增 FILE 接收位置的互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5579375-8c05-4583-bcaa-b483ac275d8a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c29b3eb291b1b36daab5d77aae74f6055a3c738
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario"></a><span data-ttu-id="2b88d-102">步驟 3A： 新增 FILE 接收位置的互動即時案例</span><span class="sxs-lookup"><span data-stu-id="2b88d-102">Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="2b88d-103">設定接收位置，可讓您輕鬆地卸除的驗證測試檔案。</span><span class="sxs-lookup"><span data-stu-id="2b88d-103">Set up a receive location that enables you to easily drop test files for validation.</span></span> <span data-ttu-id="2b88d-104">您可以使用這個位置來測試案例。</span><span class="sxs-lookup"><span data-stu-id="2b88d-104">You use this location to test the scenario.</span></span>  
  
## <a name="add-a-file-receive-location"></a><span data-ttu-id="2b88d-105">新增 FILE 接收位置</span><span class="sxs-lookup"><span data-stu-id="2b88d-105">Add a FILE receive location</span></span>  
  
1.  <span data-ttu-id="2b88d-106">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="2b88d-106">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="2b88d-107">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您要建立接收埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b88d-107">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="2b88d-108">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="2b88d-108">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="2b88d-109">在**接收埠屬性**視窗中，接收埠， **Tutorial_IA_InputRequest_RealTime**。</span><span class="sxs-lookup"><span data-stu-id="2b88d-109">In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_InputRequest_RealTime**.</span></span>  
  
5.  <span data-ttu-id="2b88d-110">在**接收埠屬性**視窗，請在**接收位置**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="2b88d-110">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="2b88d-111">在**接收位置屬性**視窗，請在**一般**索引標籤上，從**傳輸類型**下拉式清單中，選取**檔案**，和然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="2b88d-111">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="2b88d-112">在**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="2b88d-112">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="2b88d-113">在**接收位置屬性**視窗，請在**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2b88d-113">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="2b88d-114">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="2b88d-114">**Use this**</span></span>|<span data-ttu-id="2b88d-115">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="2b88d-115">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="2b88d-116">**接收處理常式**</span><span class="sxs-lookup"><span data-stu-id="2b88d-116">**Receive handler**</span></span>|<span data-ttu-id="2b88d-117">從下拉式清單選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="2b88d-117">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="2b88d-118">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="2b88d-118">**Receive pipeline**</span></span>|<span data-ttu-id="2b88d-119">從下拉式清單選取**XMLReceive**。</span><span class="sxs-lookup"><span data-stu-id="2b88d-119">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="2b88d-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2b88d-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b88d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b88d-121">See Also</span></span>  
 <span data-ttu-id="2b88d-122">[步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2b88d-122">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="2b88d-123">[步驟 3B： 加入互動接收位置互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2b88d-123">[Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="2b88d-124">[步驟 3c： 新增檔案傳送埠，以便擷取 Sw:HandleRequest 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2b88d-124">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="2b88d-125">[步驟 3D： 新增檔案傳送埠，以便擷取 Sw:HandleResponse 訊息互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span><span class="sxs-lookup"><span data-stu-id="2b88d-125">[Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span></span>  
 [<span data-ttu-id="2b88d-126">步驟 3E： 加入互動的傳送埠互動即時案例</span><span class="sxs-lookup"><span data-stu-id="2b88d-126">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)