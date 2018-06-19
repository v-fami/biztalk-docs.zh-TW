---
title: 步驟 4d： 測試有效的執行個體互動的存放區和轉送 （提取） 案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c2933d0-bbe3-4486-832e-5009b2d760ac
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9c8ea24eeb5541cf84448363ca91fcb8171f19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223942"
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="a5fe0-102">步驟 4d: 互動存放區和轉送 （提取） 案例測試有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="a5fe0-102">Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="a5fe0-103">在開始此步驟之前，必須先完成[步驟 4c： 建立互動商店] 和 [正向 （提取） 案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="a5fe0-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="a5fe0-104">若要測試的有效執行個體</span><span class="sxs-lookup"><span data-stu-id="a5fe0-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="a5fe0-105">卸除到 c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF ExchangeReqSimple.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="a5fe0-105">Drop the file ExchangeReqSimple.xml into c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF.</span></span>  
  
2.  <span data-ttu-id="a5fe0-106">之後立即確認、 ExchangeReqSimple.xml 檔案消失時從資料夾。</span><span class="sxs-lookup"><span data-stu-id="a5fe0-106">Verify that after a moment, the ExchangeReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="a5fe0-107">檔案 acquirequeue.xml 放入 c:\SWIFTAdapterTutorial\Interact\PullRequest。</span><span class="sxs-lookup"><span data-stu-id="a5fe0-107">Drop the file acquirequeue.xml into c:\SWIFTAdapterTutorial\Interact\PullRequest.</span></span>  
  
4.  <span data-ttu-id="a5fe0-108">瀏覽至 C:\SWIFTAdapterTutorial\Interact\PullResponse 確認 Sw:HandleRequest 位於資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a5fe0-108">Browse to C:\SWIFTAdapterTutorial\Interact\PullResponse Verify that Sw:HandleRequest is in the folder.</span></span>  
  
5.  <span data-ttu-id="a5fe0-109">在文字編輯器中，例如 [記事本] 開啟 Sw:HandleRequest 訊息，並確認裝載區段中的相同檔案 ExchangeReqSimple.xml。</span><span class="sxs-lookup"><span data-stu-id="a5fe0-109">Open the Sw:HandleRequest message in a text editor, such as Notepad, and verify that the payload section is the same as in the file ExchangeReqSimple.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fe0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5fe0-110">See Also</span></span>  
 <span data-ttu-id="a5fe0-111">[步驟 4A： 啟動 SWIFTNet 服務互動的存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a5fe0-111">[Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="a5fe0-112">[步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a5fe0-112">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="a5fe0-113">步驟 4c： 建立測試執行個體互動的存放區和轉送 （提取） 案例的</span><span class="sxs-lookup"><span data-stu-id="a5fe0-113">Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md)