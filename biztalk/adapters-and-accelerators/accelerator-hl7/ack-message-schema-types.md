---
title: "ACK 訊息結構描述類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, ACK schemas
- acknowledgements, ACK schema types
- ACK messages
ms.assetid: da6981a0-a70a-481e-8db4-4a6851f205f1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c29657226c993a68b8cd557a39a7837717e2c66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ack-message-schema-types"></a>ACK 訊息結構描述類型
通知訊息結構描述有兩種形式：  
  
-   **一般通知 (ACK)**。 您可以使用一般通知 (ACK) 的應用程式不會定義特殊的特定業務應用程式層級的通知訊息或發生錯誤，使應用程式處理的地方。 您也可以使用它針對接受的層級的通知。 下表列出的 ACK 訊息結構。  
  
    |ACK ^ 變化 ^ 通知|一般通知|章節|  
    |--------------------|----------------------------|-------------|  
    |MSH|訊息標頭|2|  
    |MSA|通知訊息|2|  
    |[錯誤]|錯誤|2|  
  
-   **延遲認可 (MCF)**。 此訊息存在只為了回溯相容性 HL7 版本 2.1。 您可以使用它做為建立泛型表單的非同步應用程式層級的通知，mom 連接器架構訊息的通訊協定的一部分。 下表列出 mom 連接器架構訊息結構。  
  
    |Mom 連接器架構 ^ 變化 ^ 通知|延遲的認可|章節|  
    |--------------------|----------------------------|-------------|  
    |MSH|訊息標頭|2|  
    |MSA|通知訊息|2|  
    |[錯誤]|錯誤|2|  
  
 認可訊息有 MSH9 欄位設定為**ACK ^\<***觸發程序事件***> ^ ACK**或**MCF ^\<** *觸發程序事件***> ^ ACK**。 如此一來，第 1 個元件 MSH9 就足以判斷通知結構描述。 文件名稱[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 管線會使用一定會包含 HL7 為命名空間。 型別名稱是 MSH9_1 欄位中，這是通知或 mom 連接器架構的內容。 如此一來，如上述範例所示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]管線會尋找名稱 HL7 結構描述。ACK 或 HL7。MCF MSH9_1 欄位的值而定。 針對訊息內文結構描述是相同的 2.X 版的所有訊息。  
  
> [!NOTE]
>  在批次中 / 出通知案例中，通知標頭內容的批次如下所示：  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]設定 MSH1 2、 8 與 15 到您的使用者介面中的設定。  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]設定 MSH7 系統時間。  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]MSH9 所設的通知。  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]設定 MSH12 2.4 或 2.5。  
  
## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [設定傳送埠來接收通知](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)   
 [通知錯誤狀況](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)