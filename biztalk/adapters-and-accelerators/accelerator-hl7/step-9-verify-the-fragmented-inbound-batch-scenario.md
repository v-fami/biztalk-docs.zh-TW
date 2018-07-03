---
title: 步驟 9： 驗證片段化的輸入批次案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ba61866-2e1b-49e2-be57-ef281407d0a5
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dce0f283695af423b96c07103a1c2f5837cf4b6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970671"
---
# <a name="step-9-verify-the-fragmented-inbound-batch-scenario"></a>步驟 9： 驗證片段化的輸入批次案例
在此步驟中，您可以驗證分散輸入批次案例。  
  
 正在驗證此案例牽涉到使用下列工具：  
  
- **MllpSend 工具**，供您從命令列批次訊息傳送至接收埠。  
  
- **MllpReceive 工具**，供您從命令列確認個別訊息 （做為包含在批次） 從傳送埠的接收。 MllpReceive 工具的這個執行個體做為模擬的特定業務應用程式。 在訊息的接收，它也會產生通知傳回給[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]integration 引擎。  
  
- MllpReceive 工具，可用來確認接收通知的傳送埠從第二個執行個體。  
  
### <a name="to-test-the-fragmented-inbound-batch-scenario"></a>若要測試分割輸入批次案例  
  
1. 按一下 **開始**，指向**所有程式**，指向**附屬應用程式**，然後按一下**命令提示字元**。  
  
2. 在命令提示字元中，移至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\MLLP 公用程式的加速器**。  
  
3. 在命令提示字元中，輸入**mllpreceive/p 41000 /sb 11 /eb 28 /cr 13 /hl7ack 」\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator forHL7\Samples\Sample 應用程式接受 ACK.txt**，然後按下**Enter**。 [命令提示字元] 視窗會進入等候狀態，直到您執行步驟 5 和系統收到的輸入。  
  
   > [!NOTE]
   >  步驟 3 中的命令執行會接聽通訊埠 41000 MLLP 接聽端應用程式。 此連接埠是傳遞訊息的傳送埠相關聯 (在中建立[步驟 5： 建立傳送埠以傳遞訊息](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md))。 MllpReceive 工具做為接收訊息，並回到 BTAHL7 （如有包含在範例檔案範例應用程式接受 ACK.txt） 傳送通知 (ACK) 的特定業務應用程式。 此工具會顯示在命令提示字元 視窗中傳回給它的任何訊息。 步驟 3 中的命令會指定 MLLP 訊息的預設 EB、 SB 和 CR 字元。  
  
4. 重複步驟 1 和 2 來開啟另一個 [命令提示字元] 視窗並瀏覽至 MLLP 公用程式目錄。 在命令提示字元中，輸入**mllpreceive/p 41002**，然後按**Enter**。 [命令提示字元] 視窗會進入等候狀態，直到您執行步驟 5 和系統接收輸出。  
  
   > [!NOTE]
   >  步驟 4 中的命令會執行接聽連接埠 41002 MLLP 接聽端應用程式。 此連接埠是回復到的批次訊息的來源提供通知的傳送埠相關聯 (在中建立[步驟 6： 建立傳送埠以傳遞通知](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md))。 MllpReceive 工具做為傳送原始批次的特定業務應用程式。 此工具會顯示任何通知傳回給它，在命令提示字元 視窗中。 步驟 4 中的命令會指定 MLLP 訊息的預設 EB、 SB 和 CR 字元。  
  
5. 重複步驟 1 和 2 來開啟另一個 [命令提示字元] 視窗並瀏覽至 MLLP 公用程式目錄。 在命令提示字元中，輸入**mllpsend /twoway /sb 11 /eb 28 /cr 13 /f 」\<*磁碟機*\>: \Batching Tutorial\Instances\FragmentedInboundBatch.txt"/ p 21000**，其中\<*磁碟機*\>是您的安裝磁碟機代號，然後按下**Enter**。  
  
   > [!NOTE]
   >  步驟 5 中的命令會模擬原始批次訊息至接收埠的傳送。 主控台應該會顯示 「 已傳送訊息： 1"，指出 MllpSend 工具傳送單一批次訊息。 如果它不會顯示 「 已傳送訊息： 1"，檢查事件檢視器。 確認您在步驟 5 中，輸入命令的文字，然後傳送的組態進行疑難排解並接收埠的狀態[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和 BTAHL7。  
  
### <a name="to-verify-the-results-of-the-fragmented-inbound-batch-tutorial"></a>若要確認的分散輸入 Batch 教學課程結果  
  
1.  確認在短暫延遲之後，接聽連接埠 41000 訊息 MllpReceive 工具會顯示個別的訊息片段從批次並傳送至 Tutorial_BatchSource 合作對象的內容。 兩個訊息的內容應該如下所示：  
  
    |MSH.9|MSH.10|MSH.3|MSH.5|  
    |-----------|------------|-----------|-----------|  
    |ADT^A03|000001|Tutorial_BatchSource|MESA_IS|  
    |ADT^A03|000002|Tutorial_BatchSource|MESA_IS|  
  
2.  確認在短暫延遲之後，接聽連接埠 41002 通知 MllpReceive 工具會顯示從 BTAHL7 整合引擎會傳回批次的來源的兩個通知的內容。 兩個通知的內容應該如下所示：  
  
    |MSH.9|MSH.3|MSH.5|MSA.2|MSA.1|  
    |-----------|-----------|-----------|-----------|-----------|  
    |ACK ^ 將 ADT^A03 ^ 通知|MESA_IS|Tutorial_BatchSource|000001|AA|  
    |ACK ^ 將 ADT^A03 ^ 通知|MESA_IS|Tutorial_BatchSource|000002|AA|  
  
## <a name="see-also"></a>另請參閱  
 [第 2 部分： 中批次 / 批次出案例](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)   
 [第 3 部分：建立批次案例](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)