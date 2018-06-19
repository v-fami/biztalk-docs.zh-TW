---
title: 步驟 4d： 測試的有效執行個體互動即時案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e163c3ac-a00d-40cf-b1b8-4a38f74ab0e8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94bdb2acd8147ec5041df7d6a1c4324ca833d9e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223766"
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-real-time-scenario"></a><span data-ttu-id="94777-102">步驟 4d： 測試的有效執行個體互動即時案例</span><span class="sxs-lookup"><span data-stu-id="94777-102">Step 4D: Test a Valid Instance for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="94777-103">在開始此步驟之前，必須先完成[步驟 4c： 建立測試執行個體互動的即時案例](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="94777-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="94777-104">若要測試的有效執行個體</span><span class="sxs-lookup"><span data-stu-id="94777-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="94777-105">檔案 ExchangeReqSimple.xml 放入 C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime。</span><span class="sxs-lookup"><span data-stu-id="94777-105">Drop the file ExchangeReqSimple.xml into C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime.</span></span>  
  
2.  <span data-ttu-id="94777-106">之後立即確認、 ExchangeReqSimple.xml 檔案消失時從資料夾。</span><span class="sxs-lookup"><span data-stu-id="94777-106">Verify that after a moment, the ExchangeReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="94777-107">瀏覽至 可檢視控制代碼的要求訊息，Sw:HandleRequest C:\SWIFTAdapterTutorial\Interact\HandleRequest。</span><span class="sxs-lookup"><span data-stu-id="94777-107">Browse to C:\SWIFTAdapterTutorial\Interact\HandleRequest to view the handle request message, Sw:HandleRequest.</span></span>  
  
4.  <span data-ttu-id="94777-108">瀏覽至 檢視控制代碼的回應訊息，Sw:HandleResponse C:\SWIFTAdapterTutorial\Interact\Response。</span><span class="sxs-lookup"><span data-stu-id="94777-108">Browse to C:\SWIFTAdapterTutorial\Interact\Response to view the handle response message, Sw:HandleResponse.</span></span>  
  
5.  <span data-ttu-id="94777-109">在文字編輯器中，例如 [記事本] 開啟 Sw:HandleRequest 訊息，並確認裝載區段中的相同檔案 ExchangeReqSimple.xml。</span><span class="sxs-lookup"><span data-stu-id="94777-109">Open the Sw:HandleRequest message in a text editor, such as Notepad, and verify that the payload section is the same as in the file ExchangeReqSimple.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94777-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94777-110">See Also</span></span>  
 <span data-ttu-id="94777-111">[步驟 4： 測試互動即時的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="94777-111">[Step 4: Test the InterAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="94777-112">[步驟 4A： 啟動 SWIFTNet 服務](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span><span class="sxs-lookup"><span data-stu-id="94777-112">[Step 4A: Start the SWIFTNet Service](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span></span>  
 <span data-ttu-id="94777-113">[步驟 4B： 啟動傳送埠和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="94777-113">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="94777-114">步驟 4c： 建立的測試執行個體互動即時案例</span><span class="sxs-lookup"><span data-stu-id="94777-114">Step 4C: Create a Test Instance for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md)