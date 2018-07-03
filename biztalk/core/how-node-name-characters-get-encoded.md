---
title: 如何編碼節點名稱字元 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6462856b-7a52-40c9-9aff-c0579130eec9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f374f9ebdfabfff1cc123fe2ad2f9d05a2b3c63
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994055"
---
# <a name="how-node-name-characters-get-encoded"></a>如何編碼節點名稱字元
如果您使用節點名稱中不允許的字元，BizTalk 編輯器會提示您，詢問您是否要繼續進行編碼的不允許的字元 (**[確定]** 或是**取消**)。 若您繼續進行，每個不被允許的字元將編碼如下：  
  
- 不允許的字元都會編碼為"*xDDDD\\*"其中"DDDD"是 4 位數十六進位 Unicode 字元表示法。 例如，空白字元 (0x0020) 會編碼為"*x0020\\*"。  
  
- 若編碼兩個或更多相鄰的不被允許字元，只會在它們之間使用單一底線字元。 例如，三個空格會編碼為"*x0020_x0020_x0020\\*"而非"*x0020\__x0020\__x0020\\*"。  
  
> [!NOTE]
>  您可以停用提示所設定的節點名稱編碼**顯示編碼警告對話方塊**屬性設**False**中的 BizTalk 編輯器 資料夾**選項** 對話方塊中，用於**工具**功能表上，或選取**以後不要顯示此對話方塊**節點名稱編碼對話方塊中的核取方塊。 如需在此對話方塊中選項的詳細資訊，請參閱[管理結構描述樹狀結構檢視](../core/how-to-manage-the-schema-tree-view.md)。  
  
 「BizTalk 編輯器」中的結構描述樹狀結構檢視會使用您輸入的字元顯示節點名稱。 「BizTalk 對應工具」也會顯示您已輸入的字元，而不顯示已編碼的版本。 在 [BizTalk 編輯器] 的 XSD 檢視中與 XSD 檔案本身，會使用已編碼的節點名稱。 例如，若您將節點命名為 Purchase Order，則在「BizTalk 編輯器」與「BizTalk 對應工具」的結構描述樹狀結構中，均會顯示為 Purchase Order。 在 [BizTalk 編輯器] 的 XSD 檢視中，當您首次插入對應的項目節點時，它會顯示如下。  
  
```  
<element name="Purchase_x0020_Order" type="xs:string />  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [節點名稱屬性](../core/node-name-property.md)   
 [編碼哪些節點名稱字元](../core/which-node-name-characters-get-encoded.md)