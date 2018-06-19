---
title: 步驟 4c： 建立 FileAct 存放與轉寄 （提取） 案例的測試執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50fc72f0-ec00-46f9-b24b-fe8d5e5079ee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c991dd980df9e19f036b3872289f9d0d8aa82d6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223854"
---
# <a name="step-4c-create-a-test-instance-for-the-fileact-store-and-forward-pull-scenario"></a>步驟 4c： 建立 FileAct 存放與轉寄 （提取） 案例的測試執行個體
在開始此步驟之前，必須先完成[步驟 4B： 啟動傳送埠和接收埠 FileAct 儲存和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md)。  
  
### <a name="to-create-a-test-instance"></a>若要建立的測試執行個體  
  
1.  在文字編輯器，例如 [記事本] 中開啟新的檔案並貼上以下內容：  
  
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
  
    > [!NOTE]
    >  您必須取代 *%physicalfoldername*實際的資料夾名稱中 FILEACT 您設定接收位置。  
  
2.  ExchangeReqSimple.xml 的名稱儲存檔案。  
  
3.  在文字編輯器，例如 [記事本] 中開啟新的檔案並貼上以下內容：  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Sw-ExchangeSnFRequest>  
    <Sw-SnFRequest>  
    <Sw-SnFOpRequest>  
    <Sw-AcquireSnFRequest>  
    <SwInt-Queue Type the queue name, based on your provisioning with SWIFT </SwInt-Queue>  
    <Sw-SessionMode>Pull</Sw-SessionMode>  
    <Sw-ForceAcquire>TRUE</Sw-ForceAcquire>  
    <Sw-OrderBy>InterAct</Sw-OrderBy>  
    <Sw-RecoveryMode>TRUE</Sw-RecoveryMode>  
    </Sw-AcquireSnFRequest>  
    </Sw-SnFOpRequest>  
    </Sw-SnFRequest>  
    </Sw-ExchangeSnFRequest>  
  
    ```  
  
4.  名稱 acquirequeue.xml 儲存檔案。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4A： 啟動 SWIFTNet 服務為 FileAct 存放與轉寄 （提取） 實例](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md)   
 [步驟 4B： 啟動傳送埠和接收埠為 FileAct 存放與轉寄 （提取） 實例](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md)   
 [步驟 4d： 測試 FileAct 存放與轉寄 （提取） 案例的有效執行個體](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-fileact-store-and-forward-pull-scenario.md)