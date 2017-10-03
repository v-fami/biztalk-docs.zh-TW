---
title: "步驟 4c： 建立的測試執行個體互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3557acdc-eb3f-4c70-b64a-3f523a1ba650
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c0035074eba0eec6994aa7ab024afbcec10984
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-interact-real-time-scenario"></a>步驟 4c： 建立的測試執行個體互動即時案例
在開始此步驟之前，必須先完成[步驟 4B： 啟動傳送埠和接收埠的互動即時實例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md)。  
  
### <a name="to-create-a-test-instance"></a>若要建立的測試執行個體  
  
1.  在文字編輯器，例如 [記事本] 中開啟新的檔案並貼上以下內容：  
  
    ```  
    <SwInt-ExchangeRequest>  
    <SwInt-Request>  
    <SwInt-RequestPayload>  
    Get Well soon  
    </SwInt-RequestPayload>  
    </SwInt-Request>  
    </SwInt-ExchangeRequest>  
    ```  
  
2.  名稱儲存檔案**ExchangeReqSimple.xml**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 測試互動即時的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)   
 [步驟 4A： 啟動 SWIFTNet 服務](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md)   
 [步驟 4B： 啟動傳送埠和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md)   
 [步驟 4d： 測試的有效執行個體互動即時案例](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-real-time-scenario.md)