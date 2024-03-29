---
title: 步驟 4d： 測試有效的執行個體為 FileAct 存放與轉寄實例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f47b1fd-a4ef-4b1d-812a-8c2fa946f98c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b2074e5360e6dfee766546f27a560208f920688
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964732"
---
# <a name="step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-scenario"></a>步驟 4d： 測試有效的執行個體為 FileAct 存放與轉寄的實例
在開始此步驟之前，必須先完成[步驟 4c： 建立 FileAct 存放與轉寄案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md)。  
  
### <a name="to-test-a-valid-instance"></a>若要測試的有效執行個體  
  
1.  檔案 PutReqSimple.xml 放入 C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF。  
  
2.  之後立即確認、 PutReqSimple.xml 檔案消失時從資料夾。  
  
3.  請確認 Sample_Put.txt 檔案從 C:\SWIFTAdapterTurorial\Fileact\ClientLocation 轉送到 C:\SWIFTAdapterTutorial\Fileact\ServerLocation，且回應出現 C:\SWIFTAdapterTutorial\ResponseServer 中。  
  
4.  請檢查三個 HandleFileEventRequest 訊息的狀態事件 (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) 資料夾。 這些訊息應該包含下列傳輸狀態：  
  
     HandleFileEventRequest 訊息\<Sw TransferStatus\>接受\</Sw-TransferStatus\>  
  
     HandleFileEventRequest 訊息\<Sw TransferStatus\>起始\</Sw-TransferStatus\>  
  
     HandleFileEventRequest 訊息\<Sw TransferStatus\>已完成\</Sw-TransferStatus\>  
  
## <a name="see-also"></a>請參閱  
 [步驟 4： 測試 FileAct 存放與轉寄的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)   
 [步驟 4A： 啟動 SWIFTNet 服務為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md)   
 [步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md)   
 [步驟 4C：針對 FileAct 儲存和轉寄案例建立測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md)