---
title: 步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和轉送 （提取） 案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00ab119d-ed44-4f4a-84ea-20f2c41e5a92
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b747c76b30b9f7d04bef379be9eaccaaeca063ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223638"
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="cd91b-102">步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和轉送 （提取） 案例</span><span class="sxs-lookup"><span data-stu-id="cd91b-102">Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="cd91b-103">在開始此步驟之前，必須先完成[步驟 4： 測試互動存放區和轉寄端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="cd91b-103">Before you begin this step, you must complete[Step 4: Test the InterAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md).</span></span>  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a><span data-ttu-id="cd91b-104">啟動傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="cd91b-104">To start the send ports and receive ports</span></span>  
  
1.  <span data-ttu-id="cd91b-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="cd91b-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="cd91b-106">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您用來建立傳送埠的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd91b-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.</span></span>  
  
3.  <span data-ttu-id="cd91b-107">針對下列每個傳送埠，傳送埠，以滑鼠右鍵按一下，然後按一下**啟動**:</span><span class="sxs-lookup"><span data-stu-id="cd91b-107">For each of the following send ports, right-click the send port, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="cd91b-108">**Tutorial_ IA_SendPullResponseToReceiver**</span><span class="sxs-lookup"><span data-stu-id="cd91b-108">**Tutorial_ IA_SendPullResponseToReceiver**</span></span>  
  
    -   <span data-ttu-id="cd91b-109">**Tutorial_IA_SendRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="cd91b-109">**Tutorial_IA_SendRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="cd91b-110">**Tutorial_IA_DynamicSendPort**</span><span class="sxs-lookup"><span data-stu-id="cd91b-110">**Tutorial_IA_DynamicSendPort**</span></span>  
  
4.  <span data-ttu-id="cd91b-111">在主控台樹狀目錄中，展開 [BizTalk 群組]，然後展開您在其中建立接收位置的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd91b-111">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.</span></span>  
  
5.  <span data-ttu-id="cd91b-112">針對每個下列的接收位置，以滑鼠右鍵按一下接收位置，然後**啟用**:</span><span class="sxs-lookup"><span data-stu-id="cd91b-112">For each of the following receive locations, right-click the receive location, and then click **Enable**:</span></span>  
  
    -   <span data-ttu-id="cd91b-113">**Tutorial_IA_InputRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="cd91b-113">**Tutorial_IA_InputRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="cd91b-114">**Tutorial_ IA_InputRequest_PullMode**</span><span class="sxs-lookup"><span data-stu-id="cd91b-114">**Tutorial_ IA_InputRequest_PullMode**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd91b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd91b-115">See Also</span></span>  
 <span data-ttu-id="cd91b-116">[步驟 4A： 啟動 SWIFTNet 服務互動的存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cd91b-116">[Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="cd91b-117">[步驟 4c： 建立測試執行個體互動的存放區和轉送 （提取） 案例的](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cd91b-117">[Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md) </span></span>  
 [<span data-ttu-id="cd91b-118">步驟 4d: 互動存放區和轉送 （提取） 案例測試有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="cd91b-118">Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-interact-store-and-forward-pull-scenario.md)