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
# <a name="step-4d-test-a-valid-instance-for-the-fileact-real-time-scenario"></a>步驟 4d: FileAct 即時案例測試有效的執行個體
在開始此步驟之前，必須先完成[步驟 4c: FileAct 即時案例建立測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md)。  
  
### <a name="to-test-a-valid-instance"></a>若要測試的有效執行個體  
  
1.  檔案 PutReqSimple.xml 放入 C:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime。  
  
2.  之後立即確認、 PutReqSimple.xml 檔案消失時從資料夾。  
  
3.  確認 Sample_Put.txt 檔案從傳送： C:\SWIFTAdapterTutorial\Fileact\ClientLocation C:\SWIFTAdapterTutorial\Fileact\ServerLocation，來和回應會出現在 C:\SWIFTAdapterTutorial\Fileact\ResponseClient 和 C:\SWIFTAdapterTutorial\Fileact\ResponseServer。  
  
4.  請檢查三個 HandleFileEventRequest 訊息的狀態事件 (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) 資料夾。 這些訊息應該包含下列傳輸狀態：  
  
     HandleFileEventRequest 訊息\<Sw TransferStatus\>接受\</Sw-TransferStatus\>  
  
     HandleFileEventRequest 訊息\<Sw TransferStatus\>起始\</Sw-TransferStatus\>  
  
     HandleFileEventRequest 訊息\<Sw TransferStatus\>已完成\</Sw-TransferStatus\>  
  
## <a name="see-also"></a>請參閱  
 [步驟 4： 測試 FileAct 即時的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)   
 [步驟 4A： 啟動 SWIFTNet 服務 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md)   
 [步驟 4B： 啟動傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md)   
 [步驟 4C：針對 FileAct 即時案例建立測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md)