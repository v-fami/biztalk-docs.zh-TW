---
title: "使用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- pipeline components [custom], code samples
- pipeline components [custom], schemas
ms.assetid: 07e60532-1032-422d-865e-0bd65c45dab6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a7cb71319fef61d3b6cb854b04b41e3815a6129
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-schemas"></a>使用結構描述
本節包含與使用結構描述有關之一般工作的程式碼範例。  
  
## <a name="using-xsd-schemas"></a>使用 XSD 結構描述  
 `IDocumentSpec Interface`介面代表 XML 結構描述定義語言 (XSD) 結構描述所定義的文件圖形; XSD 的最上層元素的圖形的根項目。 結構描述會安裝之後，可以擷取由呼叫`IPipelineContext.GetDocumentSpecByType Method`或`IPipelineContext.GetDocumentSpecByName Method`方法**IPipelineContext**介面。  
  
```  
IDocumentSpec docspec = pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## <a name="using-xsd-flat-file-schemas"></a>使用 XSD 一般檔案結構描述  
 這兩個**GetDocumentSpecByType**和**GetDocumentSpecByName**方法會傳回**IDocumentSpec**介面。 如果結構描述是實際的一般檔案結構描述 （一個具有其他一般檔案專屬附註），您可以類型轉換**IDocumentSpec**到**IFFDocumentSpec**和初始化剖析和序列化從該處的順序。  
  
```  
IFFDocumentSpec docspec = (IFFDocumentSpec) pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## <a name="see-also"></a>另請參閱  

[使用剖析和序列化引擎](../core/using-the-parsing-and-serializing-engines.md)