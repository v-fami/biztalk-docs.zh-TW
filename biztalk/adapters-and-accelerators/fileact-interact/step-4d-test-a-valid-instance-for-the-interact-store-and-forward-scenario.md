---
title: 步驟 4d： 測試有效的執行個體互動的存放區和情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6aa49df8-ccf6-455a-99ff-38879d2b7bf9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5d27b23195adffc5915d8cb2170dca9e975ec94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224278"
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-store-and-forward-scenario"></a>步驟 4d： 測試有效的執行個體互動的存放區和轉寄的案例
在開始此步驟之前，必須先完成[步驟 4c： 建立測試執行個體為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md)。  
  
### <a name="to-test-a-valid-instance"></a>若要測試的有效執行個體  
  
1.  卸除到 c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF ExchangeReqSimple.xml 檔案  
  
2.  之後立即確認、 ExchangeReqSimple.xml 檔案消失時從資料夾。  
  
3.  瀏覽至 C:\SWIFTAdapterTutorial\Interact\HandleRequest。 請確認該 Sw:HandleRequest 資料夾中。  
  
4.  在文字編輯器中，例如 [記事本] 開啟 Sw:HandleRequest 訊息，並確認裝載區段中的相同檔案 ExchangeReqSimple.xml。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 測試互動存放區和轉寄的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)   
 [步驟 4A： 啟動 SWIFTNet 服務互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md)   
 [步驟 4c： 建立測試執行個體互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md)