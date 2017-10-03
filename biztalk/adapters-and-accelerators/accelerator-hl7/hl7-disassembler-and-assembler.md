---
title: "HL7 解譯器和組合器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, HL7
- disassembler, HL7
ms.assetid: 54e83a04-86c8-482f-bea3-dbbdeb4584d6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e81d621656fc678196f7f6fb709b29de87a3aaf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-disassembler-and-assembler"></a>HL7 解譯器和組合器
HL7 解譯器和組合器支援 HL7 編碼訊息。 因為[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]處理 XML 格式中的原生訊息[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用 HL7 解譯器和組合器將[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]HL7 integration 引擎。  
  
## <a name="hl7-disassembler"></a>HL7 反組譯工具  
 HL7 解譯器會將傳入 HL7 編碼訊息剖析為處理的 XML 區段。 它會執行驗證的訊息標頭和主體的基本驗證。 它會判斷它會使用來剖析 HL7 訊息結構描述 (請參閱[中 HL7 結構描述判斷 2.X 解譯器](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md))，判斷訊息的來源合作對象，並執行其他主體的驗證 (如果啟用合作對象）。  
  
## <a name="hl7-assembler"></a>HL7 組譯工具  
 HL7 組合器序列化傳出的 HL7 訊息的 XML 區段。 它會判斷它用來序列化 HL7 訊息結構描述 (請參閱[中 HL7 結構描述判斷 2.X 組譯工具](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md))，判斷訊息的目的合作對象，並執行驗證的主體，（如果啟用合作對象）。  
  
 組譯工具可以序列化下列通知 (ACK) 訊息：  
  
-   靜態  
  
-   原始模式  
  
-   增強的模式  
  
 HL7 組譯工具也能夠將延後的 ACK 訊息路由傳送。  
  
## <a name="see-also"></a>另請參閱  
 [BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)   
 [BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)