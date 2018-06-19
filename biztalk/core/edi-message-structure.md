---
title: EDI 訊息結構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c9a0447-447f-483c-825d-547c06ad691e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9395ed5e0b03bda48e19d6413f95ca2e74a3f1e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239630"
---
# <a name="edi-message-structure"></a>EDI 訊息結構
EDI 訊息由一個信封和一系列階層式的結構元素組成。 信封中包含一組標頭和結尾；各組標頭和結尾分別描述及包含一個結構元素。 這些結構元素如下：  
  
```  
Interchange  
   Group  
      Transaction set/message  
         Segment  
            Data Element  
               Sub Element  
```  
  
 EDI 訊息的階層式結構可讓您批次處理交易集/訊息和群組。 即使交換中只包含一個交易集/訊息和一個群組，在建立該項交換的結構時，也會使用與批次處理時相同的基本結構項目，唯一的不同是這項交換的結構中不會有多個交易集/訊息或群組元素。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [EDI 標頭和結尾](../core/edi-headers-and-trailers.md)  
  
-   [EDI 交換結構元素](../core/edi-interchange-structural-element.md)  
  
-   [EDI 群組結構元素](../core/edi-group-structural-element.md)  
  
-   [EDI 交易集訊息結構元素](../core/edi-transaction-set-message-structural-element.md)  
  
-   [EDI 區段結構項目](../core/edi-segment-structural-element.md)  
  
-   [EDI 資料項目結構元素](../core/edi-data-element-structural-element.md)