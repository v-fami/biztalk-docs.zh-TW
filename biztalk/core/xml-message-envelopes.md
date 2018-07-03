---
title: XML 訊息信封 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d01cd85d-7bf7-49fa-aa25-322213bce066
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f4b60dfbc128baead6b0a1ad38d319ba7b6e8fc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972407"
---
# <a name="xml-message-envelopes"></a>XML 訊息信封
XML 信封在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所傳送和接收的 XML 執行個體訊息中有兩個目的：  
  
- XML 信封可以包含補充 XML 文件內資料的資料。 XML 解譯器可將此資料升級至訊息內容，以提供更容易從各種 BizTalk Server 元件存取的能力。 就輸出 XML 執行個體訊息而言，XML 組合器可以將值從訊息內容降級至信封，以供其包含在執行個體訊息傳輸中。  
  
- XML 信封可用來結合多個 XML 文件為單一、有效的 XML 執行個體訊息。 若沒有信封包裝單一根標記中的多個文件，則包含多個文件的 XML 執行個體訊息將不符合格式正確的 XML。  
  
  一般的 XML 信封 (以粗體顯示) 包含資料以及用來分隔一或多個它所包含的 XML 文件 (以一般字型顯示) 之標記。  
  
```  
  
  <envelope fieldAttrib1="..." fieldAttrib2="..." ...>     <fieldElem1>...</fieldElem1>     <fieldElem2>...</fieldElem2>     ...     <body>  
    <document1>  
        ...  
    </document1>  
    <document2>  
        ...  
    </document2>  
    ...  
</body>    ...</envelope>  
```  
  
 另一種較少見但仍為有效的 XML 信封 (以粗體顯示) 則不需包含任何資料或是用來分隔它所包含的 XML 文件 (以一般字型顯示) 之標記。  
  
```  
  
      <envelope>  
    <document1>  
        ...  
    </document1>  
    <document2>  
        ...  
    </document2>  
    ...  
</envelope>  
```  
  
 在此情況下，XML 信封僅包含開始和結束的信封標記。  
  
## <a name="see-also"></a>另請參閱  
 [巢狀的 XML 訊息信封](../core/nested-xml-message-envelopes.md)   
 [XML 訊息的結構](../core/structure-of-an-xml-message.md)   
 [如何建立信封的結構描述](../core/how-to-create-schemas-for-envelopes.md)