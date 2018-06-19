---
title: 步驟 3： 測試批次中的批次出案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c487d39d-b2be-41d4-963e-d0ee9ba169fb
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d84c34eb3019f83ecd28f30425a93708affcecb2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "25960796"
---
# <a name="step-3-test-the-batch-inbatch-out-scenario"></a>步驟 3： 測試中的批次/批次出案例
在此步驟中，您將測試批次中 / 批次出教學課程藉由卸除批次中的測試執行個體 / 批次訊息的資料夾。 您設定的傳送埠會將訊息傳送、 接收埠會接收該和接收管線會處理它並拖放到目的資料夾。  
  
### <a name="to-test-the-batch-inbatch-out-scenario"></a>若要測試批次中 / 批次出案例  
  
1.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \Batching Tutorial\Instances**資料夾。  
  
2.  以滑鼠右鍵按一下**BatchInBatchOut.txt**，然後按一下 **複製**。  
  
3.  瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7PickUp**資料夾。  
  
4.  以滑鼠右鍵按一下資料夾，然後按一下**貼上**。  
  
### <a name="to-verify-the-results-of-the-batch-inbatch-out-tutorial"></a>若要確認批次的結果中 / 批次出教學課程  
  
-   使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BTAHL7Drop**資料夾。 短時間，您應該看到的批次訊息和通知處理的執行個體，出現在資料夾中。 如果它們沒有出現，請檢查[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器的錯誤訊息。 每個檔案應該有不同的名稱形式\< *Guid*\>.txt。  
  
     第一個訊息應該是兩則訊息所組成的批次。 BizTalk Accelerator for HL7 (BTAHL7) 具有循序包含這兩則訊息，在.txt 檔案中。 這個批次不包含 FHS/FTS 和 BHS/BTS 標記。 在批次必須包含可能是所有 FHS/FTS 與 BHS/BTS 標記，或此批次訊息、 沒有 FHS/FTS 及無 BHS/BTS 標記等。  
  
    |MSH.9|MSH.10|MSH.3|MSH.5|  
    |-----------|------------|-----------|-----------|  
    |ADT^A03|000001|Tutorial_BatchSource|MESA_IS|  
    |ADT^A03|000002|Tutorial_BatchSource|MESA_IS|  
  
     第二個訊息應傳送批次訊息，但是有下列欄位來回應單一應用程式通知：  
  
    |MSH.9|MSH.3|MSH.5|MSA.1|MSA.2|  
    |-----------|-----------|-----------|-----------|-----------|  
    |ACK^A03^ACK|MESA_IS|Tutorial_BatchSource|AA|000001|  
  
## <a name="see-also"></a>另請參閱  
 [第 1 部分： 分散的傳入批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [第 3 部分：建立批次案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)