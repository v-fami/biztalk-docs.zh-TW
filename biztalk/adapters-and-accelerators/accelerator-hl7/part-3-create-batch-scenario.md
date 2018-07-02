---
title: 第 3 部分： 建立批次案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, creating
- creating, batching
ms.assetid: 02247186-5b21-4738-9110-f0ca0304f0fd
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e487bfbe29ee2a34f2e50affa502d7f20592fe0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975951"
---
# <a name="part-3-create-batch-scenario"></a>第 3 部分： 建立批次案例
在案例的這個部分，您可以收到兩個內送訊息、 將它們結合為批次的訊息，和批次傳送至目的地。 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會傳回包含兩個通知產生來源來自目的地的訊息通知批次。 下圖顯示本教學課程的這個部分的處理流程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-create-batch-scenario.gif "hl7_create_batch_scenario")  
  
 **在建立批次的案例中的訊息如何流動**  
  
 此案例包含下列工作流程：  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 設陷符合 MessageBox 資料庫中的批次定義的所有訊息。 您輸入在此定義**批次定義**索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。 在本教學課程中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會設陷，並會批次處理所有訊息傳送至 Tutorial_BatchDest ADT 的結構描述與 ^ 將 adt^a03，和所有通知傳送到 ADT 由於 Tutorial_BatchSource ^ adt^a03 訊息。  
  
- 排程批次傳送時間時，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送批次的控制訊息觸發輸出批次交易。 您定義排程**批次排程**索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。 您也可以按一下 觸發程序**立即傳送**相同的索引標籤上。  
  
- 批次協調流程會形成超出受困於 MessageBox 資料庫的訊息的訊息批次。 協調流程也會包裝檔案標頭和結尾和批次標頭和結尾中的批次。 此協調流程就是原生[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]協調流程加入[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]到 BizTalk 協調流程，因此它會列在 [BizTalk 總管或 BizTalk Server 管理主控台中的協調流程] 節點下的安裝程式。  
  
- 如果是針對來源合作對象所定義的通知 （如它們在此情況下是針對 Tutorial_BatchSource），BizTalk 會批次處理通知 （至 \Tutorial_BatchACKDrop 資料夾中） 將它們傳回批次中。 在本教學課程中，批次的通知會傳送在短暫延遲之後。  
  
- 協調流程會將訊息路由至傳送埠 (Tutorial_BatchDest)，以將批次的訊息傳送到目的地 （在此情況下，您硬碟機上的 [\Tutorial_BatchMsgDrop] 資料夾）。 在本教學課程中，會在一小時後傳送批次的訊息。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：設定和啟用 BatchControlPort 接收埠](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-and-enable-the-batchcontrolport-receive-port.md)  
  
-   [步驟 2：啟用批次協調流程](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md)  
  
-   [步驟 3：建立和設定目的合作對象](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md)  
  
-   [步驟 4：設定建立批次案例的來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md)  
  
-   [步驟 5：建立訊息批次的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md)  
  
-   [步驟 6：建立通知批次的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md)  
  
-   [步驟 7：啟動協調流程，並重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md)  
  
-   [步驟 8：測試建立批次案例](../../adapters-and-accelerators/accelerator-hl7/step-8-test-the-create-batch-scenario.md)