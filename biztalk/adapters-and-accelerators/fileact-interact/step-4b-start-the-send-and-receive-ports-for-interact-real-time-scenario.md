---
title: "步驟 4B： 啟動傳送埠和接收埠互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dffee9a6-5877-4744-9b46-12ca4f8fa959
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3391f966fb1033ec1886f44b62158f910179d72f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-interact-real-time-scenario"></a><span data-ttu-id="547ec-102">步驟 4B： 啟動傳送埠和接收埠互動即時案例</span><span class="sxs-lookup"><span data-stu-id="547ec-102">Step 4B: Start the Send Ports and Receive Ports for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="547ec-103">在開始此步驟之前，必須先完成[步驟 4A： 啟動 SWIFTNet 服務](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md)。</span><span class="sxs-lookup"><span data-stu-id="547ec-103">Before you begin this step, you must complete [Step 4A: Start the SWIFTNet Service](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md).</span></span>  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a><span data-ttu-id="547ec-104">啟動傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="547ec-104">To start the send ports and receive ports</span></span>  
  
1.  <span data-ttu-id="547ec-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="547ec-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="547ec-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您用來建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="547ec-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.</span></span>  
  
3.  <span data-ttu-id="547ec-107">針對下列每個傳送埠，傳送埠，以滑鼠右鍵按一下，然後按一下**啟動**:</span><span class="sxs-lookup"><span data-stu-id="547ec-107">For each of the following send ports, right-click the send port, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="547ec-108">**Tutorial_IA_SendResponseToReceiver**</span><span class="sxs-lookup"><span data-stu-id="547ec-108">**Tutorial_IA_SendResponseToReceiver**</span></span>  
  
    -   <span data-ttu-id="547ec-109">**Tutorial_IA_SendResponseToSender**</span><span class="sxs-lookup"><span data-stu-id="547ec-109">**Tutorial_IA_SendResponseToSender**</span></span>  
  
    -   <span data-ttu-id="547ec-110">**Tutorial_IA_SendRequest_RealTime**</span><span class="sxs-lookup"><span data-stu-id="547ec-110">**Tutorial_IA_SendRequest_RealTime**</span></span>  
  
4.  <span data-ttu-id="547ec-111">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您在其中建立接收位置的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="547ec-111">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.</span></span>  
  
5.  <span data-ttu-id="547ec-112">針對每個下列的接收位置，以滑鼠右鍵按一下接收位置，然後**啟用**:</span><span class="sxs-lookup"><span data-stu-id="547ec-112">For each of the following receive locations, right-click the receive location, and then click **Enable**:</span></span>  
  
    -   <span data-ttu-id="547ec-113">**Tutorial_IA_InputRequest_RealTime**</span><span class="sxs-lookup"><span data-stu-id="547ec-113">**Tutorial_IA_InputRequest_RealTime**</span></span>  
  
    -   <span data-ttu-id="547ec-114">**Tutorial_IA_HandleRequestOneWay_RealTime**</span><span class="sxs-lookup"><span data-stu-id="547ec-114">**Tutorial_IA_HandleRequestOneWay_RealTime**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="547ec-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="547ec-115">See Also</span></span>  
 <span data-ttu-id="547ec-116">[步驟 4： 測試互動即時的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="547ec-116">[Step 4: Test the InterAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="547ec-117">[步驟 4A： 啟動 SWIFTNet 服務](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span><span class="sxs-lookup"><span data-stu-id="547ec-117">[Step 4A: Start the SWIFTNet Service](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span></span>  
 <span data-ttu-id="547ec-118">[步驟 4c： 建立的測試執行個體互動即時案例](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="547ec-118">[Step 4C: Create a Test Instance for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="547ec-119">步驟 4d： 測試的有效執行個體互動即時案例</span><span class="sxs-lookup"><span data-stu-id="547ec-119">Step 4D: Test a Valid Instance for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-real-time-scenario.md)