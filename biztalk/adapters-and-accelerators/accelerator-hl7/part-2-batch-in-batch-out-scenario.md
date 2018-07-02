---
title: 第 2 部分： 批次中批次出案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, outbound batches
- batching, inbound batches
ms.assetid: 36b9d927-f5b7-4c1a-9163-9e79d17c3e9e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 593f1e57b12eb30f47db65bfacd34a988f701f07
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975415"
---
# <a name="part-2-batch-inbatch-out-scenario"></a>第 2 部分： 中批次 / 批次出案例
在本教學課程的這個部分，接收 HL7 編碼的批次檔、 將其傳遞[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]片段，並傳送到目的地的不變的批次檔。 下圖顯示這項程序流程，並以下小節說明工作流程。  
  
> [!NOTE]
>  開始本教學課程的這個部分之前, 關閉 MllpReceive 和 MllpSend 工具用於第 1 部分，藉由關閉命令提示字元。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-batch-in-batch-out-scenario.gif "hl7_batch_in_batch_out_scenario")  
  
 **如何將訊息傳送批次中在 / 批次出案例**  
  
 此案例包含下列工作流程：  
  
1. 在工作流程開始時的特定業務應用程式將訊息批次傳送至 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 整合引擎使用 FILE 通訊協定。 批次包含兩個版本 ADT ^ 將 adt^a03 訊息。 原始碼應用程式所屬的 Tutorial_BatchSource 合作對象。  
  
2. 整合引擎接收的批次檔案接收埠，並驗證的訊息批次。 (取決於選取中的來源合作對象設定的驗證層級[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。)  
  
3. 根據設定，以在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管來停用 合作對象、 介面引擎的批次片段不會剖析成個別的訊息批次，但會保留做為批次的批次。 它會驗證個別的訊息，再根據設定中的來源合作對象選取[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。  
  
4. 介面引擎產生的批次訊息中的通知定義設定為基礎的通知[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]的合作對象的組態編輯器。 在此情況下，選取原始通知模式讓介面引擎產生的訊息批次的單一應用程式接受通知之後驗證訊息標頭和主體。 引擎建置 ACK_024_GLO_DEF 結構描述為基礎的通知、 通知 MSA2 欄位中輸入"AA"、 在 MSH3，輸入目的合作對象和 MSH5 中輸入的來源合作對象。  
  
5. 通知批次的來源合作對象，透過檔案介面引擎路由傳送配接器設定來處理通知。 在此情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將批次傳送至 \Tutorial_BatchACKDrop 資料夾。  
  
6. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 會傳送到目的地的訊息批次指定目的合作對象，在此情況下資料夾 \Tutorial_BTAHL7Drop。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：設定批次進/批次出的合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-party-information-for-batch-in-batch-out.md)  
  
-   [步驟 2：修改或建立傳送埠和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)  
  
-   [步驟 3：測試批次進/批次出案例](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md)