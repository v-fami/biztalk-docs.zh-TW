---
title: ACK 訊息結構描述型別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, ACK schemas
- acknowledgements, ACK schema types
- ACK messages
ms.assetid: da6981a0-a70a-481e-8db4-4a6851f205f1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a556155e364fe56b66f7938fd49036b47085aeac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967464"
---
# <a name="ack-message-schema-types"></a>ACK 訊息結構描述類型
通知訊息結構描述有兩種形式：  

- **一般通知 (ACK)**。 應用程式不會定義特殊的特定業務應用程式層級的通知訊息或發生錯誤，防止應用程式處理，您可以使用一般的通知 (ACK)。 您也可以使用它針對接受的層級的通知。 下表列出的 ACK 訊息結構。  


  | ACK ^ 而異 ^ 通知 | 一般通知 | 章節 |
  |----------------|------------------------|---------|
  |      MSH       |     訊息標頭     |    2    |
  |      MSA       | 訊息通知 |    2    |
  |    [錯誤]     |         錯誤          |    2    |


- **延遲的通知 (MCF)**。 此訊息僅存在於 HL7 2.1 版的回溯相容性。 您可以使用它做為建立一般表單的非同步應用程式層級的通知，mom 連接器架構訊息通訊協定的一部分。 下表列出 MCF 訊息結構。  

  |Mom 連接器架構 ^ 而異 ^ 通知|延遲的通知|章節|  
  |--------------------|----------------------------|-------------|  
  |MSH|訊息標頭|2|  
  |MSA|訊息通知|2|  
  |[錯誤]|錯誤|2|  

  認可訊息有 MSH9 欄位設定為**ACK ^\<**<em>觸發程序事件</em>**\>^ ACK**或**MCF ^\<** <em>觸發程序事件</em>**\>^ ACK**。 如此一來，MSH9 的第一個部分就足以判斷通知的結構描述。 Microsoft BizTalk Accelerator for HL7 文件命名 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 管線會使用一定會包含 HL7 為命名空間。 型別名稱是 MSH9_1 欄位中，因為這是通知或 mom 連接器架構的內容。 如此一來，如上述範例所示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]管線會尋找名稱 HL7 結構描述。ACK 或 HL7。MCF MSH9_1 欄位的值而定。 訊息內文結構描述是相同的 2.X 版的所有訊息。  

> [!NOTE]
>  在批次中 / 批次出通知案例中，通知標頭的內容如下所示：  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 設定 MSH1、 2、 8 和 15 到您的使用者介面中的設定。  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 將 MSH7 設定系統時間。  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] MSH9 設通知。  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 設定 MSH12 2.4 或 2.5。  

## <a name="see-also"></a>另請參閱  
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [設定傳送埠來接收 Ack](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)   
 [通知錯誤狀況](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)