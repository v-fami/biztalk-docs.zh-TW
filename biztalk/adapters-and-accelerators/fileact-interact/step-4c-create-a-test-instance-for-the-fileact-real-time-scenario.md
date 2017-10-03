---
title: "步驟 4c: FileAct 即時案例建立的測試執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80e0cb59-8b4f-4273-a7a4-db3446008061
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04952616f1b49eb30b4eb00462e4e5295ade0cfc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-fileact-real-time-scenario"></a><span data-ttu-id="8b661-102">步驟 4c: FileAct 即時案例建立的測試執行個體</span><span class="sxs-lookup"><span data-stu-id="8b661-102">Step 4C: Create a Test Instance for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="8b661-103">在開始此步驟之前，必須先完成[步驟 4B： 啟動傳送埠和接收埠 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="8b661-103">Before you begin this step, you must complete [Step 4B: Start the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-create-a-test-instance"></a><span data-ttu-id="8b661-104">若要建立的測試執行個體</span><span class="sxs-lookup"><span data-stu-id="8b661-104">To create a test instance</span></span>  
  
1.  <span data-ttu-id="8b661-105">在文字編輯器，例如 [記事本] 中開啟新的檔案並貼上以下內容：</span><span class="sxs-lookup"><span data-stu-id="8b661-105">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Sw-ExchangeFileRequest>  
    <Sw-FileRequest>  
    <Sw-FileOpRequest>  
    <Sw-PutFileRequest>  
    <Sw-PhysicalName>%PhysicalFolderName%\sample_put.txt</Sw-PhysicalName>  
    </Sw-PutFileRequest>  
    </Sw-FileOpRequest>  
    </Sw-FileRequest>  
    </Sw-ExchangeFileRequest>  
    ```  
  
2.  <span data-ttu-id="8b661-106">儲存檔案名稱"PutReqSimple.xml"。</span><span class="sxs-lookup"><span data-stu-id="8b661-106">Save the file with the name “PutReqSimple.xml”.</span></span>  
  
3.  <span data-ttu-id="8b661-107">請確定檔案 (Sample_put.txt) 位於用戶端位置資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8b661-107">Make sure that the file (Sample_put.txt) is placed in the Client Location folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b661-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b661-108">See Also</span></span>  
 <span data-ttu-id="8b661-109">[步驟 4： 測試 FileAct 即時的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8b661-109">[Step 4: Test FileAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="8b661-110">[步驟 4A： 啟動 SWIFTNet 服務 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8b661-110">[Step 4A: Start the SWIFTNet Service for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="8b661-111">[步驟 4B： 啟動傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8b661-111">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="8b661-112">步驟 4d: FileAct 即時案例測試有效的執行個體</span><span class="sxs-lookup"><span data-stu-id="8b661-112">Step 4D: Test a Valid Instance for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-fileact-real-time-scenario.md)