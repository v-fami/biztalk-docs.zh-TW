---
title: 步驟 4c： 建立測試執行個體互動的存放區和轉送 （提取） 案例的 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c937edd-9524-4f8f-9bd1-68e24f2eebdc
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5d0908593110b04f6e5cd0f5912b66264dc7a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223934"
---
# <a name="step-4c-create-a-test-instance-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="cf186-102">步驟 4c： 建立測試執行個體互動的存放區和轉送 （提取） 案例的</span><span class="sxs-lookup"><span data-stu-id="cf186-102">Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="cf186-103">在開始此步驟之前，必須先完成[步驟 3B： 互動存放區和轉送 （提取） 案例的動態傳送埠與協調流程繫結](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-port-for-interact-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="cf186-103">Before you begin this step, you must complete [Step 3B: Bind the orchestration with dynamic send port for InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-port-for-interact-scenario.md).</span></span>  
  
### <a name="to-create-a-test-instance"></a><span data-ttu-id="cf186-104">若要建立的測試執行個體</span><span class="sxs-lookup"><span data-stu-id="cf186-104">To create a test instance</span></span>  
  
1.  <span data-ttu-id="cf186-105">在文字編輯器，例如 [記事本] 中開啟新的檔案並貼上以下內容：</span><span class="sxs-lookup"><span data-stu-id="cf186-105">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    SwInt-ExchangeRequest>  
    <SwInt-Request>  
    <SwInt-RequestPayload>  
    Get Well soon  
    </SwInt-RequestPayload>  
    </SwInt-Request>  
    </SwInt-ExchangeRequest>  
  
    ```  
  
2.  <span data-ttu-id="cf186-106">ExchangeReqSimple.xml 的名稱儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="cf186-106">Save the File with the name ExchangeReqSimple.xml.</span></span>  
  
3.  <span data-ttu-id="cf186-107">在文字編輯器，例如 [記事本] 中開啟新的檔案並貼上以下內容：</span><span class="sxs-lookup"><span data-stu-id="cf186-107">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Sw-ExchangeSnFRequest>  
    <Sw-SnFRequest>  
    <Sw-SnFOpRequest>  
    <Sw-AcquireSnFRequest>  
    <SwInt-Queue>ptsguspp_genericfa!x</SwInt-Queue>  
    <Sw-SessionMode>Pull</Sw-SessionMode>  
    <Sw-ForceAcquire>TRUE</Sw-ForceAcquire>  
    <Sw-OrderBy>FileAct</Sw-OrderBy>  
    <Sw-RecoveryMode>TRUE</Sw-RecoveryMode>  
    </Sw-AcquireSnFRequest>  
    </Sw-SnFOpRequest>  
    </Sw-SnFRequest>  
    </Sw-ExchangeSnFRequest>  
  
    ```  
  
4.  <span data-ttu-id="cf186-108">名稱 acquirequeue.xml 儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="cf186-108">Save the File with the name acquirequeue.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf186-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf186-109">See Also</span></span>  
 <span data-ttu-id="cf186-110">[步驟 4A： 啟動 SWIFTNet 服務互動的存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cf186-110">[Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="cf186-111">[步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cf186-111">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="cf186-112">步驟 4d: 互動存放區和轉送 （提取） 案例測試有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="cf186-112">Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-interact-store-and-forward-pull-scenario.md)