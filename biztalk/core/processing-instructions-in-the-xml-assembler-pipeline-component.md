---
title: XML 組合器管線元件中的處理指示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XMLNorm.ProcessingInstructionOption property
- envelopes, processing instructions
- XML Assembler [pipeline component], processing instructions
- Processing instruction scope property
- XMLNorm.ProcessingInstruction property
- envelopes, XML Assembler [pipeline component]
- pipeline components, XML Assembler
ms.assetid: d8ea453e-3b20-417d-bf25-9d424b0150fd
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85ac6045084c0aea672b0c1e9d6dfb1b4a742d55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265150"
---
# <a name="processing-instructions-in-the-xml-assembler-pipeline-component"></a>XML 組合器管線元件中的處理指示
處理指示提供處理 XML 文件之應用程式的資訊。 這類資訊可能包含如何處理文件、如何顯示文件等等的指示。  
  
 處理指示會加入至 XML 文件由**新增處理指示**屬性 (或同等權限**XMLNorm.ProcessingInstructionOption**在訊息內容屬性)。 處理指示文字指定**新增處理指示文字**屬性 (或同等權限**XMLNorm.ProcessingInstruction**在訊息內容屬性)。  
  
 **新增處理指示**屬性 (或**XMLNorm.ProcessingInstructionOption**屬性) 具有三個可能的值下, 表所述。  
  
|值|值|Description|  
|-----------|-----------|-----------------|  
|附加|0|來自 XML 組合器的新處理指示會附加至文件開頭的處理指示。|  
|建立新物件|1|來自 XML 組合器的新處理指示會覆寫文件開頭的現有處理指示。|  
|Ignore|2|會移除文件開頭的處理指示。|  
  
 在訊息內容上指定之這組處理指示 (或訊息內容屬性) 的優先順序高於在管線設計師中所指定的屬性組。 例如，如果**XMLNorm.ProcessingInstructionOption**指定為**建立新**(1) 和**XMLNorm.ProcessingInstruction**未指定，則空白處理指示會取代現有的處理指示。  
  
 另舉一例，如果**XMLNorm.ProcessingInstruction**指定但**XMLNorm.ProcessingInstructionOption**不是，會使用任何來自訊息內容屬性。 在此種情況下，會使用來自管線設計師的處理指示。  
  
 根據預設，**新增處理指示**設**附加**，和**新增處理指示文字**是空的。  
  
## <a name="processing-properties-and-envelopes"></a>處理屬性和信封  
 因為處理指示並非保留供信封所使用，所以下列一般檔案組合器設定的組合只會導致具有處理指示的最外層信封：  
  
-   **處理指示範圍**屬性設定為"Envelope"。  
  
-   **新增處理指示**屬性設定為"Append"。  
  
 信封將會使用 「 組合器 」 中指定的處理指示**新增處理指示文字**屬性。  
  
 任何在外部或內部信封中的現有處理指示 (如指定在內送訊息中) 都不會出現在輸出訊息中。  
  
## <a name="see-also"></a>另請參閱  
 [XML 組合器管線元件](../core/xml-assembler-pipeline-component.md)   
 [如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)