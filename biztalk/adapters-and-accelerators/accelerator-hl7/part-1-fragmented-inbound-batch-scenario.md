---
title: 第 1 部分： 片段化的輸入批次案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, fragmenting messages
- batching tutorial, fragmenting messages
- fragmenting messages
ms.assetid: 8adf2c17-5f66-408d-b30b-51b22d8e71fa
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c5cf6f38daca7b1773798e4bc8ed2e40ad143bd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970503"
---
# <a name="part-1-fragmented-inbound-batch-scenario"></a>第 1 部分： 片段化的輸入批次案例
在這個部分的教學課程中，您會接收 HL7 編碼的批次、 分割成個別的訊息，及個別的訊息傳送至目的地。 下圖顯示此程序的流程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-fragmented-inbound-batching-scenario.gif "hl7_fragmented_inbound_batching_scenario")  
  
 此案例包含下列工作流程：  
  
1. 在工作流程開始，當特定業務應用程式將訊息批次傳送至 Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Integration 引擎使用的最小的較低層通訊協定 (MLLP) 通訊協定。 批次包含兩個版本 ADT ^ 將 adt^a03 訊息。 原始碼應用程式所屬的 Tutorial_BatchSource 合作對象。  
  
2. 介面引擎接收的批次上的 MLLP 接收埠，並驗證的訊息批次。 （驗證層級取決於所選 BTAHL7 設定總管中的來源合作對象的設定）。  
  
3. 根據 BTAHL7 設定總管，可讓批次片段中的設定、 介面引擎剖析的批次到兩個個別 ADT ^ adt^a03 訊息。 它會驗證個別的訊息，再根據 BTAHL7 設定總管中的來源合作對象為選取的設定。  
  
4. 介面引擎產生每則訊息，取決於 BTAHL7 設定總管中的通知定義設定的通知。 本教學課程中，您將選取原始通知模式讓介面引擎之後驗證訊息標頭和主體產生單一應用程式接受通知，每個訊息。 引擎建置 ACK_024_GLO_DEF 結構描述為基礎的通知、 通知 MSA2 欄位中輸入"AA"、 在 MSH3，輸入目的合作對象和 MSH5 中輸入的來源合作對象。  
  
5. 介面引擎將 MLLP 包裝每個通知，並透過 MLLP 傳送配接器的通知到來源合作對象的路由設定以處理通知。  
  
6. 介面引擎會放置 MLLP 包裝每個訊息，以及每個個別訊息 MLLP 傳送連接埠設定來處理非通知訊息的路由。  
  
7. BTAHL7 會將每個訊息透過另一個 MLLP 傳送埠傳送至其 MSH5 欄位中指定的目的地。  
  
8. 目的合作對象會傳送至 BTAHL7 應用程式接受它接收的每個訊息的通知。  
  
9. 介面引擎接收的每個通知。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：新增標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md)  
  
-   [步驟 2：新增 v2.3.1 通用結構描述](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md)  
  
-   [步驟 3：新增觸發程序事件 (訊息) 結構描述](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)  
  
-   [步驟 4：建立接收埠，以接受批次訊息](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)  
  
-   [步驟 5：建立傳送埠以傳遞訊息](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md)  
  
-   [步驟 6：建立傳送埠以傳遞通知](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md)  
  
-   [步驟 7：建立和設定來源合作對象](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)  
  
-   [步驟 8：重新啟動 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md)  
  
-   [步驟 9：驗證片段化的輸入批次案例](../../adapters-and-accelerators/accelerator-hl7/step-9-verify-the-fragmented-inbound-batch-scenario.md)