---
title: XML 組合器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component]
- pipeline components, XML Assembler
ms.assetid: 3adfd603-0577-49c2-ae9d-445d62fed385
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22348b61ca32567190fa99e103fe536f5199af58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289486"
---
# <a name="xml-assembler-pipeline-component"></a>XML 組合器管線元件
XML 組合器管線元件將 XML 序列化及組合的功能結合成一個元件。 其主要功能是將訊息內容的屬性傳回信封和文件。  
  
 接收一批訊息之後形成交換時，在 XML 組合器元件中會發生以下動作：  
  
1.  組合器使用指定的信封規格建立信封。  
  
2.  元件藉由使用與訊息關聯的 XSD 結構描述中編碼為註解的預先定義 XPath，將內容屬性放置在訊息執行個體上。  
  
3.  元件將訊息附加到信封。  
  
4.  元件使用與信封關聯的 XSD 結構描述中編碼為註解的預先定義 XPath，將內容屬性放置在信封上。  
  
> [!NOTE]
>  XML 組合器管線元件不會填入空缺的屬性欄位，不過，當欄位是選擇性但沒有預設或固定值時，則會填入空的項目欄位。  
  
 如需設定 XML 組合器管線元件的資訊，請參閱[如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [XML 組合器管線元件中的字元編碼](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)  
  
-   [XML 組合器管線元件中的處理指示](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)  
  
-   [XML 組合器管線元件中無法辨識的訊息](../core/unrecognized-messages-in-the-xml-assembler-pipeline-component.md)  
  
-   [XML 組合器管線元件中的 XML 資訊集項目](../core/xml-information-set-elements-in-the-xml-assembler-pipeline-component.md)  
  
-   [XML 組合器管線元件中的文件結構強化](../core/document-structure-enforcement-in-the-xml-assembler-pipeline-component.md)