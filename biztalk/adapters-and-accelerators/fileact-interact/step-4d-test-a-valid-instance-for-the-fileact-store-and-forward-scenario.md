---
title: "步驟 4d： 測試有效的執行個體為 FileAct 存放與轉寄實例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f47b1fd-a4ef-4b1d-812a-8c2fa946f98c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b2074e5360e6dfee766546f27a560208f920688
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="a37d0-102">步驟 4d： 測試有效的執行個體為 FileAct 存放與轉寄的實例</span><span class="sxs-lookup"><span data-stu-id="a37d0-102">Step 4D: Test a Valid Instance for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="a37d0-103">在開始此步驟之前，必須先完成[步驟 4c： 建立 FileAct 存放與轉寄案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="a37d0-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="a37d0-104">若要測試的有效執行個體</span><span class="sxs-lookup"><span data-stu-id="a37d0-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="a37d0-105">檔案 PutReqSimple.xml 放入 C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF。</span><span class="sxs-lookup"><span data-stu-id="a37d0-105">Drop the file PutReqSimple.xml into C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF.</span></span>  
  
2.  <span data-ttu-id="a37d0-106">之後立即確認、 PutReqSimple.xml 檔案消失時從資料夾。</span><span class="sxs-lookup"><span data-stu-id="a37d0-106">Verify that after a moment, the PutReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="a37d0-107">請確認 Sample_Put.txt 檔案從 C:\SWIFTAdapterTurorial\Fileact\ClientLocation 轉送到 C:\SWIFTAdapterTutorial\Fileact\ServerLocation，且回應出現 C:\SWIFTAdapterTutorial\ResponseServer 中。</span><span class="sxs-lookup"><span data-stu-id="a37d0-107">Verify that the Sample_Put.txt file is transferred from C:\SWIFTAdapterTurorial\Fileact\ClientLocation to C:\SWIFTAdapterTutorial\Fileact\ServerLocation, and that responses appear in C:\SWIFTAdapterTutorial\ResponseServer.</span></span>  
  
4.  <span data-ttu-id="a37d0-108">請檢查三個 HandleFileEventRequest 訊息的狀態事件 (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a37d0-108">Check status event (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) folder for three HandleFileEventRequest messages.</span></span> <span data-ttu-id="a37d0-109">這些訊息應該包含下列傳輸狀態：</span><span class="sxs-lookup"><span data-stu-id="a37d0-109">These messages should contain the following Transfer status:</span></span>  
  
     <span data-ttu-id="a37d0-110">HandleFileEventRequest 訊息\<Sw TransferStatus\>接受\</Sw-TransferStatus\></span><span class="sxs-lookup"><span data-stu-id="a37d0-110">HandleFileEventRequest message\<Sw-TransferStatus\>Accepted\</Sw-TransferStatus\></span></span>  
  
     <span data-ttu-id="a37d0-111">HandleFileEventRequest 訊息\<Sw TransferStatus\>起始\</Sw-TransferStatus\></span><span class="sxs-lookup"><span data-stu-id="a37d0-111">HandleFileEventRequest message \<Sw-TransferStatus\>Initiated\</Sw-TransferStatus\></span></span>  
  
     <span data-ttu-id="a37d0-112">HandleFileEventRequest 訊息\<Sw TransferStatus\>已完成\</Sw-TransferStatus\></span><span class="sxs-lookup"><span data-stu-id="a37d0-112">HandleFileEventRequest message \<Sw-TransferStatus\>Completed\</Sw-TransferStatus\></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a37d0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="a37d0-113">See Also</span></span>  
 <span data-ttu-id="a37d0-114">[步驟 4： 測試 FileAct 存放與轉寄的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a37d0-114">[Step 4: Test FileAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="a37d0-115">[步驟 4A： 啟動 SWIFTNet 服務為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a37d0-115">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="a37d0-116">[步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="a37d0-116">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="a37d0-117">步驟 4C：針對 FileAct 儲存和轉寄案例建立測試執行個體</span><span class="sxs-lookup"><span data-stu-id="a37d0-117">Step 4C: Create a Test Instance for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md)