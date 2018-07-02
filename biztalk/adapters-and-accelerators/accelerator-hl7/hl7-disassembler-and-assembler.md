---
title: HL7 反組譯工具和組譯工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assembler, HL7
- disassembler, HL7
ms.assetid: 54e83a04-86c8-482f-bea3-dbbdeb4584d6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d603e74defeac983b1287f16c7f562b706b8c54d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994991"
---
# <a name="hl7-disassembler-and-assembler"></a>HL7 反組譯工具和組譯工具
HL7 反組譯工具和組譯工具提供支援 HL7 編碼訊息。 由於 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]處理原生 XML 格式，Microsoft BizTalk Accelerator for HL7 的訊息 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用 HL7 解譯器和組合器將[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]HL7 整合引擎。  
  
## <a name="hl7-disassembler"></a>HL7 反組譯工具  
 HL7 反組譯工具將剖析內送 HL7 編碼的訊息處理的 XML 區段。 它會執行驗證的訊息標頭和主體的基本驗證。 它會判斷用來剖析 HL7 訊息結構描述 (請參閱[HL7 中的結構描述判斷 2.X 反組譯工具](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md))，判斷訊息的來源合作對象，並會執行額外的驗證主體的 (如果啟用合作對象）。  
  
## <a name="hl7-assembler"></a>HL7 組譯工具  
 HL7 組合器會序列化傳出的 HL7 訊息中的 XML 區段。 它會判斷用來序列化 HL7 訊息結構描述 (請參閱[HL7 中的結構描述判斷 2.X 組譯工具](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md))，判斷訊息的目的合作對象，並執行驗證的主體 （如果啟用合作對象）。  
  
 「 組合器 」 可以序列化下列通知 (ACK) 訊息：  
  
- 靜態  
  
- 原始的模式  
  
- 增強的模式  
  
  HL7 組譯工具也能夠將延後的 ACK 訊息路由傳送。  
  
## <a name="see-also"></a>另請參閱  
 [BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)   
 [BizTalk Accelerator for HL7 元件](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)