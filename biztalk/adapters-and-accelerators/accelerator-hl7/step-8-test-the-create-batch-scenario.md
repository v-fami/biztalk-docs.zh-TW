---
title: 步驟 8： 測試建立批次案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc7fac40-fd3e-413b-82cc-7ad08226094c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d880d1f9d586878a28803ef5060cfb770bf67a7d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007807"
---
# <a name="step-8-test-the-create-batch-scenario"></a>步驟 8： 測試建立批次案例
在此步驟中，您可以測試建立批次案例卸除的訊息要批次處理成來源 Tutorial_BTAHL7Pickup 資料夾的測試執行個體。 您將設定傳送埠拾取訊息的來源資料夾，並將它; 傳送接收埠會接收它;接收管線會處理它，並將它放入目的 Tutorial_BTAHL7Drop 資料夾。  

### <a name="to-test-the-create-batch-scenario"></a>若要測試建立批次案例  

1. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \Batching Tutorial\Instances**資料夾。  

2. 選取  **CreateBatchMessage1.txt**，並**CreateBatchMessage2.txt**，以滑鼠右鍵按一下它們，然後按一下 **複製**。  

3. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BTAHL7Pickup**資料夾。  

4. 以滑鼠右鍵按一下資料夾，然後按一下**貼上**。  

### <a name="to-verify-the-results-of-the-create-batch-scenario"></a>若要確認建立批次案例的結果  

1. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BatchACKDrop**資料夾。 稍候片刻，您應該會看到已處理的執行個體通知批次會出現在資料夾中。 如果沒有出現，請檢查[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器 」 的錯誤訊息。 檔案應具有名稱\< *Guid*\>.txt。 此批次應包含兩個一接收到兩個訊息原本傳送產生的通知。 此批次應該具有下列欄位：  

   |FHS.5|BHS.5|BTS.1|FTS.1|  
   |-----------|-----------|-----------|-----------|  
   |Tutorial_BatchSource|Tutorial_BatchSource|2|@shouldalert|  

    通知批次內應該有下列欄位：  


   |    MSH.9    | MSA.2 | MSA.1 |       MSH.3        |        MSH.5         |
   |-------------|-------|-------|--------------------|----------------------|
   | ACK ^ 將 ADT^A03 ^ 通知 | Msg01 |  AA   | Tutorial_BatchDest | Tutorial_BatchSource |
   | ACK ^ 將 ADT^A03 ^ 通知 | Msg02 |  AA   | Tutorial_BatchDest | Tutorial_BatchSource |


2. 使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BatchMsgDrop**資料夾。 小時之後，您應該會看到已處理的執行個體的訊息批次出現在資料夾中。 如果沒有出現，請檢查[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器 」 的錯誤訊息。 檔案應具有名稱\< *Guid*\>.txt。 此批次應包含兩個最初是傳送的訊息。 此批次應該具有下列欄位：  

   |FHS.5|BHS.5|BTS.1|FTS.1|  
   |-----------|-----------|-----------|-----------|  
   |Tutorial_BatchDest|Tutorial_BatchDest|2|@shouldalert|  

    批次內的訊息應該有下列欄位：  

   |MSH.9|MSH.10|MSH.3|MSH.5|  
   |-----------|------------|-----------|-----------|  
   |ADT^A03|Msg01|Tutorial_BatchSource|Tutorial_BatchDest|  
   |ADT^A03|Msg02|Tutorial_BatchSource|Tutorial_BatchDest|  

    批次會包裝在兩個集合的標頭和結尾的特定批次：  

   -   檔案標頭和結尾 （FHS 和 FTS），這用來括住的檔案，可以包含多個批次。 請注意檔案接收應用程式 (**Tutorial_BatchDest**) FHS5 欄位和檔案建立日期/時間 FHS7 中。 請注意檔案批次計數 （在檔案中的批次數目），在 FTS2 (1)。  

   -   批次標頭和結尾 （BHS 和 BTS），這用來括住每個批次。 請注意在 BTS2 接收應用程式和批次建立日期/時間，例如 FHS 和批次的訊息計數 (2) 的檔案。  

## <a name="see-also"></a>另請參閱  
 [第 1 部分： 片段化的輸入批次案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [第 3 部分：建立批次案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)