---
title: "XML 解譯器和組合器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler, XML
- assembler, XML
ms.assetid: 242a7a96-2342-4ab5-9d3f-1acbcc7ffd14
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4978484f888290377986ee4ae8bf049c14a1b31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xml-disassembler-and-assembler"></a>XML 解譯器和組合器
XML 解譯器和組合器確定[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 不只支援 HL7 編碼訊息，但是也支援傳入和/或傳出 XML 訊息。  
  
## <a name="xml-disassembler"></a>XML 解譯器  
 XML 解譯器會將內送 XML 訊息剖析為 XML 區段進行處理。 因為它會剖析訊息，解譯器會執行下列工作：  
  
-   控制代碼逸出序列  
  
-   處理必要/選用的屬性的檢查  
  
-   控制代碼宣告 Z 區段  
  
 因為它會剖析訊息，解譯器會執行下列：  
  
-   語法驗證  
  
-   結構描述驗證 （如果啟用）  
  
## <a name="xml-assembler"></a>XML 組合器  
 XML 組合器序列化傳出 XML 訊息的 XML 區段。 「 XML 組合器 」 支援，並建立下列通知 (ACK) 訊息：  
  
-   靜態  
  
-   原始模式  
  
-   增強的模式  
  
 「 XML 組合器 」 也能夠將延後的 ACK 訊息路由傳送。  
  
## <a name="see-also"></a>另請參閱  
 [BTAHL72XML 處理](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)   
 [BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)