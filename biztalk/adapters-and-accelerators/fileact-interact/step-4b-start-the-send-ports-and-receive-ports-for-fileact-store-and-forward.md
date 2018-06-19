---
title: 步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄實例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f8c34b1-24a5-4ac7-bb96-27834bc3c711
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb40a366a3c4952eaac9557ea04f5a84c846c81e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225406"
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="9664c-102">步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄的實例</span><span class="sxs-lookup"><span data-stu-id="9664c-102">Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="9664c-103">在開始此步驟之前，必須先完成[步驟 4A： 啟動 SWIFTNet 服務為 FileAct 存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="9664c-103">Before you begin this step, you must complete [Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a><span data-ttu-id="9664c-104">啟動傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="9664c-104">To start the send ports and receive ports</span></span>  
  
1.  <span data-ttu-id="9664c-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="9664c-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="9664c-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您用來建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9664c-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.</span></span>  
  
3.  <span data-ttu-id="9664c-107">針對下列每個傳送埠，傳送埠，以滑鼠右鍵按一下，然後按一下**啟動**:</span><span class="sxs-lookup"><span data-stu-id="9664c-107">For each of the following send ports, right-click the send port, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="9664c-108">**Tutorial_FA_SendResponseToReceiver**</span><span class="sxs-lookup"><span data-stu-id="9664c-108">**Tutorial_FA_SendResponseToReceiver**</span></span>  
  
    -   <span data-ttu-id="9664c-109">**Tutorial_FA_SendRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="9664c-109">**Tutorial_FA_SendRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="9664c-110">**Tutorial_ GetStatusReports**</span><span class="sxs-lookup"><span data-stu-id="9664c-110">**Tutorial_ GetStatusReports**</span></span>  
  
4.  <span data-ttu-id="9664c-111">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您在其中建立接收位置的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9664c-111">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.</span></span>  
  
5.  <span data-ttu-id="9664c-112">針對每個下列的接收位置，以滑鼠右鍵按一下接收位置，然後**啟用**:</span><span class="sxs-lookup"><span data-stu-id="9664c-112">For each of the following receive locations, right-click the receive location, and then click **Enable**:</span></span>  
  
    -   <span data-ttu-id="9664c-113">**Tutorial_FA_InputRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="9664c-113">**Tutorial_FA_InputRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="9664c-114">**Tutorial_FA_HandleRequestOneWay_SnF**</span><span class="sxs-lookup"><span data-stu-id="9664c-114">**Tutorial_FA_HandleRequestOneWay_SnF**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9664c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9664c-115">See Also</span></span>  
 <span data-ttu-id="9664c-116">[步驟 4： 測試 FileAct 存放與轉寄的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9664c-116">[Step 4: Test FileAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="9664c-117">[步驟 4A： 啟動 SWIFTNet 服務為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9664c-117">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="9664c-118">[步驟 4c： 建立 FileAct 存放與轉寄案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="9664c-118">[Step 4C: Create a Test Instance for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="9664c-119">步驟 4d： 測試有效的執行個體為 FileAct 存放與轉寄的實例</span><span class="sxs-lookup"><span data-stu-id="9664c-119">Step 4D: Test a Valid Instance for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-scenario.md)