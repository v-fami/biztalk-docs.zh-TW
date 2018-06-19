---
title: 步驟 4d： 測試的有效執行個體互動即時案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e163c3ac-a00d-40cf-b1b8-4a38f74ab0e8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94bdb2acd8147ec5041df7d6a1c4324ca833d9e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223766"
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-real-time-scenario"></a>步驟 4d： 測試的有效執行個體互動即時案例
在開始此步驟之前，必須先完成[步驟 4c： 建立測試執行個體互動的即時案例](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md)。  
  
### <a name="to-test-a-valid-instance"></a>若要測試的有效執行個體  
  
1.  檔案 ExchangeReqSimple.xml 放入 C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime。  
  
2.  之後立即確認、 ExchangeReqSimple.xml 檔案消失時從資料夾。  
  
3.  瀏覽至 可檢視控制代碼的要求訊息，Sw:HandleRequest C:\SWIFTAdapterTutorial\Interact\HandleRequest。  
  
4.  瀏覽至 檢視控制代碼的回應訊息，Sw:HandleResponse C:\SWIFTAdapterTutorial\Interact\Response。  
  
5.  在文字編輯器中，例如 [記事本] 開啟 Sw:HandleRequest 訊息，並確認裝載區段中的相同檔案 ExchangeReqSimple.xml。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4： 測試互動即時的端對端案例](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)   
 [步驟 4A： 啟動 SWIFTNet 服務](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md)   
 [步驟 4B： 啟動傳送埠和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md)   
 [步驟 4c： 建立的測試執行個體互動即時案例](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md)