---
title: "巢狀 XML 訊息信封 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e880cef1-4e73-4bce-a06e-8c4d23bc5a8c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46b0f505dd9ba7da71df1cb460f9c9a6610763d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="nested-xml-message-envelopes"></a>巢狀 XML 訊息信封
您可以巢狀處理 XML 信封以建立複雜文件結構。 巢狀 XML 信封有兩種格式，稱為彈性格式與標準格式。 下列範例顯示信封文件的彈性格式，其中文件和信封 (以粗體顯示) 可出現在封入信封中的相同層級。  
  
```  
<envelope1>  
    <document1/>    <envelope2>  
        <document2/>  
        <document3/>  
    </envelope2>    <document4/>  
</envelope1>  
```  
  
 下列範例類似的執行個體訊息信封文件，所有文件出現在最內層的信封中相同層級中的標準格式符合。  
  
```  
<envelope1>  
    <envelope2>  
        <document1/>  
        <document2/>  
        <document3/>  
        <document4/>  
    </envelope2>  
</envelope1>  
  
```  
  
 假定執行個體訊息為上述的其中一種格式，XML 解譯器將會產生 document1、document2、document3 及 document4。 這些文件中的每一個之訊息內容會包含從對應的文件升級之屬性，以及每個封入信封中升級的屬性。 下表顯示在每個彈性與標準格式範例之未包裝文件的訊息內容中將包含的升級屬性，這是假定在各個信封與文件的第一欄中已指定屬性升級。  
  
|指定屬性升級|彈性格式範例的結果訊息內容屬性|標準格式範例的結果訊息內容屬性|  
|-----------------------------------|---------------------------------------------------------------|----------------------------------------------------------------|  
|envelope1: p1<br /><br /> envelope2: p3<br /><br /> document1: p2<br /><br /> document2: p4 and p5<br /><br /> document3: no promotions<br /><br /> document4: no promotions|document1: p1, p2<br /><br /> document2: p1, p3, p4, p5<br /><br /> document3: p1, p3<br /><br /> document4: p1|document1: p1, p2, p3<br /><br /> document2: p1, p3, p4, p5<br /><br /> document3: p1, p3<br /><br /> document4: p1, p3|  
  
## <a name="see-also"></a>另請參閱  
 [XML 訊息信封](../core/xml-message-envelopes.md)   
 [XML 訊息的結構](../core/structure-of-an-xml-message.md)   
 [如何建立信封的結構描述](../core/how-to-create-schemas-for-envelopes.md)