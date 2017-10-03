---
title: "步驟 4d： 測試有效的執行個體為 FileAct 存放與轉寄 （提取） 實例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33c7aabe-206f-4b89-b739-ac1e63675451
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf6f53257ff2a9194cf85597d0806780f15c8e52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-pull-scenario"></a>步驟 4d： 測試 FileAct 存放與轉寄 （提取） 案例的有效執行個體
在開始此步驟之前，必須先完成[步驟 4c： 建立 FileAct 存放與轉寄 （提取） 案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)。  
  
### <a name="to-test-a-valid-instance"></a>若要測試的有效執行個體  
  
1.  卸除檔案 PutReqSimple.xml 到**C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**。  
  
2.  之後立即確認、 PutReqSimple.xml 檔案消失時從資料夾。  
  
3.  拖放到檔案 fileactcquirequeue.xml **C:\SWIFTAdapterTutorial\FileAct\PullRequest**。  
  
4.  確認 Sample_Put.txt 檔案從傳送**C:\SWIFTAdapterTutorial\Fileact\ClientLocation**至**C:\SWIFTAdapterTutorial\Fileact\ServerLocation**，和回應會出現在**C:\SWIFTAdapterTutorial\PullResponse**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4A： 啟動 SWIFTNet 服務為 FileAct 存放與轉寄 （提取） 實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md)   
 [步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄 （提取） 實例](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md)   
 [步驟 4c： 建立 FileAct 存放與轉寄 （提取） 案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)