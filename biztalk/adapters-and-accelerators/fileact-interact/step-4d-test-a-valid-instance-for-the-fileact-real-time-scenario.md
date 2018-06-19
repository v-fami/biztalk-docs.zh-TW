---
title: '步驟 4d: FileAct 即時案例測試有效的執行個體 |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8975c90-462b-4c9b-8766-1272ab7ceaba
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 906a7eb08dc7542d7fa383aeb9035c0a5536cff3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963772"
---
# <a name="step-4d-test-a-valid-instance-for-the-fileact-real-time-scenario"></a><span data-ttu-id="5a87d-102">步驟 4d: FileAct 即時案例測試有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="5a87d-102">Step 4D: Test a Valid Instance for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="5a87d-103">在開始此步驟之前，必須先完成[步驟 4c: FileAct 即時案例建立測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="5a87d-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="5a87d-104">若要測試的有效執行個體</span><span class="sxs-lookup"><span data-stu-id="5a87d-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="5a87d-105">檔案 PutReqSimple.xml 放入 C:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime。</span><span class="sxs-lookup"><span data-stu-id="5a87d-105">Drop the file PutReqSimple.xml into C:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime.</span></span>  
  
2.  <span data-ttu-id="5a87d-106">之後立即確認、 PutReqSimple.xml 檔案消失時從資料夾。</span><span class="sxs-lookup"><span data-stu-id="5a87d-106">Verify that after a moment, the PutReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="5a87d-107">確認 Sample_Put.txt 檔案從傳送： C:\SWIFTAdapterTutorial\Fileact\ClientLocation C:\SWIFTAdapterTutorial\Fileact\ServerLocation，來和回應會出現在 C:\SWIFTAdapterTutorial\Fileact\ResponseClient 和 C:\SWIFTAdapterTutorial\Fileact\ResponseServer。</span><span class="sxs-lookup"><span data-stu-id="5a87d-107">Verify that the Sample_Put.txt file is transferred from: C:\SWIFTAdapterTutorial\Fileact\ClientLocation to C:\SWIFTAdapterTutorial\Fileact\ServerLocation, and that responses appear in C:\SWIFTAdapterTutorial\Fileact\ResponseClient and C:\SWIFTAdapterTutorial\Fileact\ResponseServer.</span></span>  
  
4.  <span data-ttu-id="5a87d-108">請檢查三個 HandleFileEventRequest 訊息的狀態事件 (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5a87d-108">Check status event (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) folder for three HandleFileEventRequest messages.</span></span> <span data-ttu-id="5a87d-109">這些訊息應該包含下列傳輸狀態：</span><span class="sxs-lookup"><span data-stu-id="5a87d-109">These messages should contain the following Transfer status:</span></span>  
  
     <span data-ttu-id="5a87d-110">HandleFileEventRequest 訊息\<Sw TransferStatus\>接受\</Sw-TransferStatus\></span><span class="sxs-lookup"><span data-stu-id="5a87d-110">HandleFileEventRequest message\<Sw-TransferStatus\>Accepted\</Sw-TransferStatus\></span></span>  
  
     <span data-ttu-id="5a87d-111">HandleFileEventRequest 訊息\<Sw TransferStatus\>起始\</Sw-TransferStatus\></span><span class="sxs-lookup"><span data-stu-id="5a87d-111">HandleFileEventRequest message \<Sw-TransferStatus\>Initiated\</Sw-TransferStatus\></span></span>  
  
     <span data-ttu-id="5a87d-112">HandleFileEventRequest 訊息\<Sw TransferStatus\>已完成\</Sw-TransferStatus\></span><span class="sxs-lookup"><span data-stu-id="5a87d-112">HandleFileEventRequest message \<Sw-TransferStatus\>Completed\</Sw-TransferStatus\></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a87d-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="5a87d-113">See Also</span></span>  
 <span data-ttu-id="5a87d-114">[步驟 4： 測試 FileAct 即時的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="5a87d-114">[Step 4: Test FileAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="5a87d-115">[步驟 4A： 啟動 SWIFTNet 服務 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="5a87d-115">[Step 4A: Start the SWIFTNet Service for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="5a87d-116">[步驟 4B： 啟動傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="5a87d-116">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="5a87d-117">步驟 4C：針對 FileAct 即時案例建立測試執行個體</span><span class="sxs-lookup"><span data-stu-id="5a87d-117">Step 4C: Create a Test Instance for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md)