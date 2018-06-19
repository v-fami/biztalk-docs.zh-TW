---
title: 設定原生管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, pipeline components
- pipeline components, configuring
- Pipeline Designer, code sample
- IPersistPropertyBag interface
ms.assetid: a3332a60-8cd6-43fa-9ecf-e1e54e71fef7
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94475334395f8c360bbb636cfa9cbadcf3bf4fe3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233174"
---
# <a name="configuring-native-pipeline-components"></a>設定原生管線元件
管線元件能在設計階段時顯示其自訂屬性。 任何在元件中定義的公用屬性將於「管線設計師」中呈現，只要該屬性的讀取和寫入存取子已經實作即可。 「管線設計師」將根據它們的宣告來顯示元件屬性；例如，若屬性宣告為唯讀，在「管線設計師」中也會如此顯示。  
  
 自訂管線元件必須實作**IPersistPropertyBag**介面，讓建立這些自訂屬性。 建立具有屬性**IPersistPropertyBag**介面可以在 Microsoft [屬性] 視窗中設定[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，就和原生管線元件的所有屬性一樣。 在本節中包含各管線元件的設定程序。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何設定原生管線元件](../core/how-to-configure-native-pipeline-components.md)  
  
-   [如何設定 BizTalk Framework 組合器管線元件](../core/how-to-configure-the-biztalk-framework-assembler-pipeline-component.md)  
  
-   [如何設定 BizTalk Framework 解譯器管線元件](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)  
  
-   [BizTalk Framework 結構描述和屬性](../core/biztalk-framework-schema-and-properties.md)  
  
-   [如何設定一般檔案組合器管線元件](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)  
  
-   [如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)  
  
-   [如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)  
  
-   [如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)  
  
-   [MIME SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md)  
  
-   [如何設定合作對象解析管線元件](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
  
-   [如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md)  
  
-   [如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)  
  
-   [XML 和一般檔案屬性結構描述與屬性](../core/xml-and-flat-file-property-schema-and-properties.md)  
  
-   [如何設定 XML 驗證器管線元件](../core/how-to-configure-the-xml-validator-pipeline-component.md)