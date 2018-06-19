---
title: 步驟 4d： 測試有效的執行個體互動的存放區和轉送 （提取） 案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c2933d0-bbe3-4486-832e-5009b2d760ac
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9c8ea24eeb5541cf84448363ca91fcb8171f19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223942"
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-store-and-forward-pull-scenario"></a>步驟 4d: 互動存放區和轉送 （提取） 案例測試有效的執行個體
在開始此步驟之前，必須先完成[步驟 4c： 建立互動商店] 和 [正向 （提取） 案例的測試執行個體](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md)。  
  
### <a name="to-test-a-valid-instance"></a>若要測試的有效執行個體  
  
1.  卸除到 c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF ExchangeReqSimple.xml 檔案。  
  
2.  之後立即確認、 ExchangeReqSimple.xml 檔案消失時從資料夾。  
  
3.  檔案 acquirequeue.xml 放入 c:\SWIFTAdapterTutorial\Interact\PullRequest。  
  
4.  瀏覽至 C:\SWIFTAdapterTutorial\Interact\PullResponse 確認 Sw:HandleRequest 位於資料夾中。  
  
5.  在文字編輯器中，例如 [記事本] 開啟 Sw:HandleRequest 訊息，並確認裝載區段中的相同檔案 ExchangeReqSimple.xml。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 4A： 啟動 SWIFTNet 服務互動的存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [步驟 4B： 啟動傳送埠和接收埠以進行互動的存放區和轉送 （提取） 案例](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [步驟 4c： 建立測試執行個體互動的存放區和轉送 （提取） 案例的](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md)