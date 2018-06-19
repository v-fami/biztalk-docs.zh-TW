---
title: 節點名稱屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95d9e5bf-7439-4ef4-ad14-e8d3e8eff911
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1d39c71a425e20c5a9228e418cfa86acb579fa5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972796"
---
# <a name="node-name-property"></a>節點名稱屬性
使用「BizTalk 編輯器」將節點插入結構描述樹狀結構時，有些節點必須重新命名，有些則不用。 基本上，您可以也應該重新命名**記錄**節點**欄位項目**節點，和**欄位屬性**節點。 您提供給這些節點的名稱會成為結構描述定義的訊息中，XML 項目及屬性的名稱。  
  
 在結構描述樹狀目錄中，您無法重新命名的節點會顯示 XML 標記; 表單中也就是說，小於比 (\<) 和大於 (\>) 符號。 例如，**結構描述** 節點， **Choice 群組**節點**Any 項目**節點，和**Any 屬性**節點表示結構描述中樹狀目錄的名稱\<結構描述\>，\<選擇\>，\<任何\>，和\<AnyAttribute\>分別。 **節點名稱**這類節點的屬性是唯讀的。  
  
 內給定**記錄** 節點，您不能有兩個**欄位屬性**具有相同名稱的節點。 不過，您可以擁有多個**欄位項目**節點或**記錄**具有相同名稱做為子節點的相同節點**記錄**節點，只要它們都有相同的資料類型(依指定其**資料型別**屬性**欄位項目**節點或其**資料結構型別**如**記錄**節點）。  
  
 當您提供名稱，以**記錄**節點**欄位項目**節點，和**欄位屬性**節點，使用描述性的該項目的角色或是屬性內的名稱結構描述所定義之訊息。 例如，FirstName 可能是不錯的選擇的名稱**欄位項目**節點會用來儲存地址結構中某人的名字。 在 XML 執行個體訊息中，若名字為 James，則對應的項目看起來如下。  
  
```  
    <FirstName>James</FirstName>  
```  
  
 當您要重新命名**記錄**節點**欄位項目**節點，和**欄位屬性**節點，您應該知道並非所有的字元可在節點名稱。 如需有關這些不允許的字元資訊，請參閱[的節點名稱字元會進行編碼](../core/which-node-name-characters-get-encoded.md)。 雖然「BizTalk 編輯器」可讓您將不允許的字元加以編碼來使用，但避免使用這些字元通常是較簡單的作法。 如需有關資訊不被允許的字元編碼，請參閱[如何節點名稱字元編碼](../core/how-node-name-characters-get-encoded.md)。  
  
 除了節點名稱中不允許的字元編碼結構描述之 XSD 表示法中，除非您不應該使用 C# 保留字當作結構描述樹狀結構中任何根節點的名稱 (除非您提供有效**根節點TypeName**屬性值) 或結構描述檔案名稱。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [編碼哪些節點名稱字元](../core/which-node-name-characters-get-encoded.md)  
  
-   [如何編碼節點名稱字元](../core/how-node-name-characters-get-encoded.md)