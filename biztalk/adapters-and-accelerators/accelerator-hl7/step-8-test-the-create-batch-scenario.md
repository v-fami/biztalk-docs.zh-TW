---
title: "步驟 8： 測試建立批次案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc7fac40-fd3e-413b-82cc-7ad08226094c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b7a77276e6246bb8fc525784309fded4bdf83f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-test-the-create-batch-scenario"></a>步驟 8： 測試建立批次案例
在此步驟中，您可以測試建立批次案例卸除的訊息要批次處理成來源 Tutorial_BTAHL7Pickup 資料夾的測試執行個體。 您設定的傳送埠拾取訊息的來源資料夾，並將它; 傳送接收埠會接收。與接收管線處理它，並將它放置到目的 Tutorial_BTAHL7Drop 資料夾。  
  
### <a name="to-test-the-create-batch-scenario"></a>若要測試建立批次案例  
  
1.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至  **\<*磁碟機*>: \Batching Tutorial\Instances** 資料夾。  
  
2.  選取**CreateBatchMessage1.txt**，和**CreateBatchMessage2.txt**，它們，以滑鼠右鍵按一下，然後按一下**複製**。  
  
3.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至  **\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7Pickup * * 資料夾。  
  
4.  以滑鼠右鍵按一下資料夾，然後按一下**貼上**。  
  
### <a name="to-verify-the-results-of-the-create-batch-scenario"></a>若要確認 「 建立批次案例結果  
  
1.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至  **\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BatchACKDrop * * 資料夾。 短時間，您應該會看到已處理的執行個體認可批次出現在資料夾中。 如果沒有出現，請檢查[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器的錯誤訊息。 這個檔案具有名稱\< *Guid*>.txt。 這個批次應該會包含兩個收到的兩個訊息原本傳送產生的通知。 這個批次應該具有下列欄位：  
  
    |FHS.5|BHS.5|BTS.1|FTS.1|  
    |-----------|-----------|-----------|-----------|  
    |Tutorial_BatchSource|Tutorial_BatchSource|2|1|  
  
     批次中的通知應該具有下列欄位：  
  
    |MSH.9|MSA.2|MSA.1|MSH.3|MSH.5|  
    |-----------|-----------|-----------|-----------|-----------|  
    |ACK ^ A03 ^ 通知|Msg01|AA|Tutorial_BatchDest|Tutorial_BatchSource|  
    |ACK ^ A03 ^ 通知|Msg02|AA|Tutorial_BatchDest|Tutorial_BatchSource|  
  
2.  使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至  **\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BatchMsgDrop * * 資料夾。 小時後，您應該會看到已處理的執行個體的訊息批次出現在資料夾中。 如果沒有出現，請檢查[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器的錯誤訊息。 這個檔案具有名稱\< *Guid*>.txt。 這個批次應該包含兩個訊息原本傳送。 這個批次應該具有下列欄位：  
  
    |FHS.5|BHS.5|BTS.1|FTS.1|  
    |-----------|-----------|-----------|-----------|  
    |Tutorial_BatchDest|Tutorial_BatchDest|2|1|  
  
     批次內的訊息應該具有下列欄位：  
  
    |MSH.9|MSH.10|MSH.3|MSH.5|  
    |-----------|------------|-----------|-----------|  
    |ADT ^ A03|Msg01|Tutorial_BatchSource|Tutorial_BatchDest|  
    |ADT ^ A03|Msg02|Tutorial_BatchSource|Tutorial_BatchDest|  
  
     批次會包裝在兩個集合的標頭和結尾的特定批次：  
  
    -   檔案標頭和結尾 （FHS 和 FT），這用來括住的檔案，可以包含多個批次。 請注意檔案接收應用程式 (**Tutorial_BatchDest**) FHS5 欄位和檔案建立日期/時間 FHS7 中。 請注意檔案批次計數 （在檔案中的批次數目），在 FTS2 (1)。  
  
    -   批次標頭和結尾 （BHS 和 BTS），這用來括住每個批次。 請注意 BTS2 中接收應用程式和批次建立日期/時間，如同 FHS 和批次訊息計數 (2) 的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [第 1 部分： 分散的傳入批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [第 3 部分： 建立批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)