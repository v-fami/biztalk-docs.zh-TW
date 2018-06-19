---
title: 叫用一般檔案剖析引擎 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- IFFDocumentSpec interface
- pipeline components [custom], flat file documents
- pipeline components [custom], engines
ms.assetid: 9c5d325e-2fae-4291-af13-3fb06657ec0e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90108ff2ade354c51f87499a388ae54135f14c7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261838"
---
# <a name="invoking-the-flat-file-parsing-engine"></a>叫用一般檔案剖析引擎
一般檔案剖析引擎，可以藉由呼叫叫用**剖析**方法**IFFDocumentSpec**介面，接著類型轉換從`IDocumentSpec Interface`擷取自**接著此**。 因為**XmlReader**從傳回**剖析**方法可讓用戶端一次擷取一個節點，這是自訂此剖析器的好機會。  
  
## <a name="example"></a>範例  
  
```  
XmlReader xr = docspec.Parse(new DataReader());  
while (xr.Read())  
{  
   switch(xr.NodeType)  
   {  
      case XmlNodeType.Element :  
         // Customize the element  
         //   
         break;  
      case XmlNodeType.Attribute :  
         // Customize the attribute  
         //   
         break;  
      // Customize other types of nodes  
      //   
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用一般檔案剖析引擎](../core/using-the-flat-file-parsing-engine.md)