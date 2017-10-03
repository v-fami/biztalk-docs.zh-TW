---
title: "如何編碼節點名稱字元 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6462856b-7a52-40c9-9aff-c0579130eec9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d2c9410e56b2b50a32ec73ce5f49ae59909f59a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-node-name-characters-get-encoded"></a>如何編碼節點名稱字元
如果您使用節點名稱中不允許的字元，BizTalk 編輯器會提示您，詢問您是否要繼續進行，不允許的字元編碼 (**確定**或**取消**)。 若您繼續進行，每個不被允許的字元將編碼如下：  
  
-   不允許的字元都會編碼為"_xDDDD\_"其中"DDDD"是 4 位數十六進位 Unicode 字元表示法。 例如，空白字元 (0x0020) 會編碼為"_x0020\_"。  
  
-   若編碼兩個或更多相鄰的不被允許字元，只會在它們之間使用單一底線字元。 例如，三個空格會編碼為"_x0020_x0020_x0020\_"而非"_x0020\__x0020\__x0020\_"。  
  
> [!NOTE]
>  您可以停用提示您輸入設定的節點名稱編碼**顯示編碼警告對話方塊**屬性**False**的 [BizTalk 編輯器] 資料夾中**選項**對話方塊中，用於**工具**功能表上，或選取**將來不要顯示此對話方塊**節點名稱編碼對話方塊中的核取方塊。 如需有關此對話方塊中選項的詳細資訊，請參閱[管理結構描述樹狀結構檢視](../core/how-to-manage-the-schema-tree-view.md)。  
  
 「BizTalk 編輯器」中的結構描述樹狀結構檢視會使用您輸入的字元顯示節點名稱。 「BizTalk 對應工具」也會顯示您已輸入的字元，而不顯示已編碼的版本。 在 [BizTalk 編輯器] 的 XSD 檢視中與 XSD 檔案本身，會使用已編碼的節點名稱。 例如，若您將節點命名為 Purchase Order，則在「BizTalk 編輯器」與「BizTalk 對應工具」的結構描述樹狀結構中，均會顯示為 Purchase Order。 在 [BizTalk 編輯器] 的 XSD 檢視中，當您首次插入對應的項目節點時，它會顯示如下。  
  
```  
<element name="Purchase_x0020_Order" type="xs:string />  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [節點名稱屬性](../core/node-name-property.md)   
 [哪些節點名稱字元會進行編碼](../core/which-node-name-characters-get-encoded.md)