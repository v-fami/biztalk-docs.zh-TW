---
title: "第 3 部分： 建立批次案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, creating
- creating, batching
ms.assetid: 02247186-5b21-4738-9110-f0ca0304f0fd
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0949d45fc70ead14338e30b554e0cb4b9694b5d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="part-3-create-batch-scenario"></a>第 3 部分： 建立批次的案例
在案例的這個部分，您可以收到兩個內送訊息、 將它們結合於批次的訊息，和批次傳送至目的地。 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會傳回包含兩個目的地的訊息來源為產生的通知認可批次。 下圖顯示本教學課程的這個部分的處理流程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-create-batch-scenario.gif "hl7_create_batch_scenario")  
  
 **在案例中建立批次訊息流動的方式**  
  
 此案例包含下列工作流程：  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]設陷符合 MessageBox 資料庫中的批次定義的所有訊息。 您輸入在此定義**批次定義** 索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。 在本教學課程，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會設陷並分批處理所有訊息傳送至 Tutorial_BatchDest ADT 的結構描述與 ^ A03，和所有通知傳送給結果 ADT Tutorial_BatchSource ^ A03 訊息。  
  
-   排程批次傳送時間時，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送批次控制訊息觸發輸出批次交易。 您可以定義排程上**批次排程** 索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。 您也可以按一下 觸發程序**立即傳送**相同索引標籤。  
  
-   批次協調流程會形成超出受困於 MessageBox 資料庫的訊息的訊息批次。 協調流程也會包裝檔案標頭和結尾，以及批次標頭和結尾中的批次。 此協調流程是原生[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]所加入的協調流程[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝至 BizTalk 協調流程，因此它會列在 BizTalk 總管或 BizTalk Server 管理主控台中的 [協調流程] 節點下的設定。  
  
-   如果是針對來源合作對象所定義的通知 （因為它們是在此情況下為 Tutorial_BatchSource），BizTalk 會批次處理通知傳回它們的批次中 （\Tutorial_BatchACKDrop 資料夾）。 在本教學課程中，批次的通知會傳送一小段延遲之後。  
  
-   協調流程會將訊息路由至傳送埠 (Tutorial_BatchDest)，將批次的訊息傳送至目的地 （在此情況下，您的硬碟上的 \Tutorial_BatchMsgDrop 資料夾）。 在本教學課程中，一小時之後傳送批次的訊息。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 設定和啟用 BatchControlPort 接收連接埠](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-and-enable-the-batchcontrolport-receive-port.md)  
  
-   [步驟 2： 啟用批次協調流程](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md)  
  
-   [步驟 3： 建立及設定目的合作對象](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md)  
  
-   [步驟 4： 設定建立批次案例的來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md)  
  
-   [步驟 5： 建立傳送埠的訊息批次](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md)  
  
-   [步驟 6： 建立通知批次的傳送埠](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md)  
  
-   [步驟 7： 啟動協調流程，並重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md)  
  
-   [步驟 8： 測試建立批次案例](../../adapters-and-accelerators/accelerator-hl7/step-8-test-the-create-batch-scenario.md)