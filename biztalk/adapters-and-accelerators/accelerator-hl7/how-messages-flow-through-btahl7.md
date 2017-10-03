---
title: "訊息如何流經 BTAHL7 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message processing
- messages, message flow
- BTAHL7, message flow
ms.assetid: dd4599af-500d-4e52-85b2-8b6a28fd3f0a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40ac6defd3b0cf99d2f0e53b3173b32e09efa0c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-messages-flow-through-btahl7"></a>訊息如何流經 BTAHL7
當您安裝[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 上方的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，您將加入[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]架構。 下圖顯示合併的系統提供的架構概觀[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/bcd-hl7-sys-archc.gif "bcd_hl7_sys_archc")  
  
## <a name="message-processing-flow"></a>訊息處理流程  
 當特定業務應用程式傳送訊息給[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]系統，則發生下列情況：  
  
1.  如果訊息是 HL7 訊息，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收透過介面卡 （通常 MLLP 配接器）。 如果是 XML 訊息，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收透過介面卡 （通常是 HTTP 配接器）。  
  
    > [!NOTE]
    >  您可以透過任何配接器; 傳輸 2.X 和 2.XML 訊息不過，您通常會傳輸 V2。透過 MLLP 配接器，而且您的 X 訊息通常會透過 HTTP 配接器傳輸 2.XML 訊息。  
  
2.  透過解譯器和驗證所剖析的接收管線會將郵件路由傳送。  
  
    1.  如果內送訊息的 HL7 訊息，則一般檔案解譯器 (DASM) 會將它解譯成 XML。 如果內送訊息的 XML 訊息，XML DASM 反組譯它。  
  
    2.  如果內送訊息批次訊息，解譯器將解譯成個別的訊息中。 (如需詳細資訊，請參閱[批次訊息處理](../../adapters-and-accelerators/accelerator-hl7/batch-message-processing.md)和[訊息批次處理](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)。)  
  
    3.  DASM 接著會驗證訊息。  
  
    4.  如果您使用雙向 MLLP 接收配接器，而且如果解譯器已驗證訊息，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]來將訊息傳遞相同的配接器接收原始訊息的原始傳送者傳送通知 (ACK)。 如果沒有，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將負值通知 (NAK)。 （如何完成此步驟取決於通知設定。 如需詳細資訊，請參閱[ACK 訊息模式](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)。)  
  
    5.  如果您未使用雙向 MLLP 接收配接器，然後[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生 ACK 或認可 （或 NAK 或 NAKs），並將 MessageBox 資料庫。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]然後將其路由至適當的合作對象傳送埠組態，可以使用任何其他配接器 （除了 MLLP) 為基礎。  
  
     在一般檔案和 XML 解譯器中，執行的處理程序的更完整清單，請參閱[BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)。  
  
3.  訊息通過配接器和接收管線中之後,[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將訊息傳遞至 MessageBox 資料庫。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]然後會判斷傳送訊息接下來的位置。 如果訊息是協調流程的一部分，它會傳送訊息至協調流程引擎。  
  
4.  協調流程引擎處理的訊息。  
  
    1.  如果對應會影響訊息，對應會將訊息根據其規則來轉換。  
  
    2.  如果您已設定商務規則，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用外部管線、 協調流程引擎可能在商務規則引擎 (BRE)。  
  
    3.  協調流程引擎將訊息傳送至 MessageBox 資料庫，然後再繼續執行處理協調流程。  
  
5.  根據訂閱[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會將訊息路由至傳送埠。  
  
6.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會透過下列的處理 （如果適用） 的傳送管線將訊息路由： 組件和驗證。  
  
    1.  如果訊息將 HL7 2.X 訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會從 XML 的訊息組合成 HL7 一般檔案組合器 (ASM)。 如果內送訊息將 XML 訊息，XML DASM 將其組合。  
  
    2.  若訊息批次訊息的一部份[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會將每個訊息組合成批次訊息。 (如需詳細資訊，請參閱[批次訊息處理](../../adapters-and-accelerators/accelerator-hl7/batch-message-processing.md)和[訊息批次處理](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)。)  
  
    3.  ASM 驗證訊息 （如果啟用透過傳送合作對象組態設定）。  
  
     在一般檔案和 XML 組合器中，執行的處理程序的更完整清單，請參閱[BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)。  
  
7.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]傳送訊息到配接器。  
  
    > [!NOTE]
    >  您可以針對數目的介面卡; 傳輸 2.X 訊息和 2.XML 訊息不過，大部分系統傳輸 2.X 訊息透過 MLLP 配接器和 2.XML 訊息透過 HTTP 配接器。  
  
## <a name="see-also"></a>另請參閱  
 [BTAHL7 將訊息路由](../../adapters-and-accelerators/accelerator-hl7/how-btahl7-routes-messages.md)