---
title: 步驟 4d： 測試有效的執行個體為 FileAct 存放與轉寄 （提取） 實例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7aabe-206f-4b89-b739-ac1e63675451
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf6f53257ff2a9194cf85597d0806780f15c8e52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223694"
---
# <a name="step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="fa224-102">步驟 4d： 測試 FileAct 存放與轉寄 （提取） 案例的有效執行個體</span><span class="sxs-lookup"><span data-stu-id="fa224-102">Step 4D: Test a Valid Instance for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="fa224-103">在開始此步驟之前，必須先完成[步驟 4c： 建立 FileAct 存放與轉寄 （提取） 案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="fa224-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="fa224-104">若要測試的有效執行個體</span><span class="sxs-lookup"><span data-stu-id="fa224-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="fa224-105">卸除檔案 PutReqSimple.xml 到**C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**。</span><span class="sxs-lookup"><span data-stu-id="fa224-105">Drop the file PutReqSimple.xml into **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**.</span></span>  
  
2.  <span data-ttu-id="fa224-106">之後立即確認、 PutReqSimple.xml 檔案消失時從資料夾。</span><span class="sxs-lookup"><span data-stu-id="fa224-106">Verify that after a moment, the PutReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="fa224-107">拖放到檔案 fileactcquirequeue.xml **C:\SWIFTAdapterTutorial\FileAct\PullRequest**。</span><span class="sxs-lookup"><span data-stu-id="fa224-107">Drop the file fileactcquirequeue.xml into **C:\SWIFTAdapterTutorial\FileAct\PullRequest**.</span></span>  
  
4.  <span data-ttu-id="fa224-108">確認 Sample_Put.txt 檔案從傳送**C:\SWIFTAdapterTutorial\Fileact\ClientLocation**至**C:\SWIFTAdapterTutorial\Fileact\ServerLocation**，和回應會出現在**C:\SWIFTAdapterTutorial\PullResponse**。</span><span class="sxs-lookup"><span data-stu-id="fa224-108">Verify that the Sample_Put.txt file is transferred from **C:\SWIFTAdapterTutorial\Fileact\ClientLocation** to **C:\SWIFTAdapterTutorial\Fileact\ServerLocation**, and that responses appear in **C:\SWIFTAdapterTutorial\PullResponse**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa224-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa224-109">See Also</span></span>  
 <span data-ttu-id="fa224-110">[步驟 4A： 啟動 SWIFTNet 服務為 FileAct 存放與轉寄 （提取） 實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="fa224-110">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md) </span></span>  
 <span data-ttu-id="fa224-111">[步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄 （提取） 實例](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="fa224-111">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="fa224-112">步驟 4c： 建立 FileAct 存放與轉寄 （提取） 案例的測試執行個體</span><span class="sxs-lookup"><span data-stu-id="fa224-112">Step 4C: Create a Test Instance for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)