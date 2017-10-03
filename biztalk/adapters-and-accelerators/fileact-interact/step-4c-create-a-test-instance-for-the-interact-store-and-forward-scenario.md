---
title: "步驟 4c： 建立測試執行個體互動的存放區和情況的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64a69dcc-d307-47c0-87e8-b0cb2a4d655b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44addc30191dd9541d7f5964a3de0eec244c9993
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario"></a>步驟 4c： 建立測試執行個體互動的存放區和轉寄的案例
在開始此步驟之前，必須先完成[步驟 4B： 啟動傳送埠和接收埠為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md)。  
  
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
  
2.  ExchangeReqSimple.xml 的名稱儲存檔案。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 測試互動存放區和轉寄的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)   
 [步驟 4A： 啟動 SWIFTNet 服務互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md)   
 [步驟 4d： 測試有效的執行個體互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-store-and-forward-scenario.md)