---
title: "XML 組合器和解譯器管線元件中的使用信封 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XMLNorm.EnvelopeSpecNames property
- XML Disassembler [pipeline component], envelopes
- envelopes, nesting
- envelopes, XML Disassembler [pipeline component]
- envelopes, XML Assembler [pipeline component]
- XML Assembler [pipeline component], envelopes
- Envelope Specification Names property
ms.assetid: ccffd2f7-c7b1-4103-a914-ae9b4b19bee3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0ae57a65bad84f3d46ceb27e9b5415dc3d1bc31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components"></a>XML 組合器和解譯器管線元件中使用的信封
XML 訊息可以包含零或更多信封。 下列範例顯示包裝 XML 文件的信封 (粗體)。  
  
```  
<ns1:document xmlns:ns1="http://myDocumentNamespaceURI.org">  
   <message>Hello</message>  
</ns1:document>  
  
```  
  
 信封有兩個用途：  
  
-   它們包含用於屬性升級和降級的欄位值。  
  
     XML 解譯器元件會升級屬性，而 XML 組合器元件則會降級屬性。 屬性升級和降級也可發生在 XML 文件中。  
  
-   它們可以將數個 XML 文件併入單一交換中。  
  
     因為格式正確的 XML 文件只能有一個根項目，所以信封可讓您結合多個 XML 文件以共用一個根項目。  
  
 您可以使用來指定信封順序，以強制的標準格式**結構描述集合屬性編輯器**的省略符號，即可存取此對話方塊**信封結構描述**「 XML 組合器 」 中的設計階段屬性。 您也可以使用**XMLNORM。EnvelopeSpecNames**執行 XML 組合器之前，訊息內容屬性。 XML 組合器會在標準形式中產生信封文件。  
  
## <a name="nesting-envelopes"></a>巢狀信封  
 您可以巢狀處理信封以形成複雜的結構，而在此結構中，可將數個信封 XML 文件併入一個更大的交換。 下列範例顯示由兩個信封所包裝的交換。  
  
```  
<envelope1>  
   <document1/>  
   <envelope2>  
      <document2/>  
      <document3/>  
   </envelope2>  
   <document4/>  
</envelope1>  
```  
  
 前述範例說明一個具彈性的形式，這表示文件可以與信封位在相同的階層層次。 在解譯信封文件之後，會建立四個分開的文件 (文件1、文件2，以此類推)。  
  
## <a name="see-also"></a>另請參閱  
 [管線元件](../core/pipeline-components.md)