---
title: "第 2 部分： 批次的批次中分析藍本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, outbound batches
- batching, inbound batches
ms.assetid: 36b9d927-f5b7-4c1a-9163-9e79d17c3e9e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56ffac38676fe6b163a39ff06be5fe0538800d2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="part-2-batch-inbatch-out-scenario"></a>第 2 部分： 中批次 / 批次出案例
在本教學課程的這個部分，接收 HL7 編碼的批次檔、 將其傳遞[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]分散的片段，而傳送保持不變的批次檔的目的地。 下圖顯示此程序，流量和下列小節描述工作流程。  
  
> [!NOTE]
>  開始本教學課程的這個部分之前, 關閉 MllpReceive 和 MllpSend 工具用於第 1 部分，關閉命令提示字元。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-batch-in-batch-out-scenario.gif "hl7_batch_in_batch_out_scenario")  
  
 **批次中的訊息流動方式中 / 批次出案例**  
  
 此案例包含下列工作流程：  
  
1.  工作流程開始的特定業務應用程式傳送訊息批次時[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Integration 引擎使用 FILE 通訊協定。 批次包含兩個版本 ADT ^ A03 訊息。 原始碼應用程式所屬的 Tutorial_BatchSource 合作對象。  
  
2.  整合引擎接收批次檔接收埠，並驗證的訊息批次。 (驗證層級取決於選取的來源合作對象中設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。)  
  
3.  根據在設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管停用批次片段的合作對象、 介面引擎不會剖析成個別的訊息批次，但會保留做為批次的批次。 它會驗證個別訊息，再根據選取的來源合作對象中設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。  
  
4.  介面引擎產生批次，根據訊息中的通知定義設定通知[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]的合作對象的組態編輯器。 在此情況下，選取原始的認可模式，如此介面引擎驗證的訊息標頭和本文之後產生的訊息批次的單一應用程式接受通知。 引擎建置 ACK_024_GLO_DEF 結構描述為基礎的通知、 通知 MSA2 欄位中輸入"AA"、 目的合作對象進入 MSH3，並進入 MSH5 來源合作對象。  
  
5.  通知批次的來源合作對象，透過檔案介面引擎路由傳送配接器設定處理通知。 在此情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將批次傳送至 \Tutorial_BatchACKDrop 資料夾。  
  
6.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會傳送到目的地的訊息批次為指定的目的合作對象，在此情況下資料夾 \Tutorial_BTAHL7Drop。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 設定批次中的合作對象資訊/出批次](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-party-information-for-batch-in-batch-out.md)  
  
-   [步驟 2： 修改或建立傳送和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)  
  
-   [步驟 3： 測試中的批次/批次出案例](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md)