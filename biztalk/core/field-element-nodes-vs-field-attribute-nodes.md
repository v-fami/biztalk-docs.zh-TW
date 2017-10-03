---
title: "欄位項目節點與欄位屬性節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1fffbca-8886-42c0-9214-cd0c5314850c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d90f622e20bbdbace6804b2418cb68fd2ad60da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="field-element-nodes-vs-field-attribute-nodes"></a>欄位項目節點與欄位屬性節點

## <a name="overview"></a>概觀
一般檔案解譯器可使用一般檔案結構描述，控制將輸入一般檔案執行個體訊息轉譯為其對等 XML 格式的方式；一般檔案組合器可使用一般檔案結構描述，控制將輸出 XML 訊息轉譯為其對等一般檔案執行個體訊息的方式。 建構此類結構描述，當您使用**欄位項目**節點或**欄位屬性**節點內特定位置的結構描述來控制一般檔案執行個體中的特定欄位是否訊息對應的 XML 項目或 XML 屬性中對等 XML 格式的訊息。  

## <a name="example"></a>範例  
 比方說，是靠左對齊、 星號填補的欄位值 」`red*****`「 一般檔案中執行個體訊息轉譯成其相等的 XML 表示方式有兩種根據該結構描述中的欄位是否**欄位項目**節點或**欄位屬性**節點。 當結構描述中表示該欄位**欄位項目**節點具有其**節點名稱**屬性設為 [色彩]，而且包含**記錄**節點都有其**節點名稱**屬性設定為"shirt"，對等 XML （以粗體顯示） 的一般檔案欄位。  
  
```  
<shirt>  
    <color>red</color>  
</shirt>  
```  
  
 當結構描述中表示相同的一般檔案欄位**欄位屬性**節點具有其**節點名稱**屬性設為色彩，而且包含**記錄**節點都有其**節點名稱**屬性設為 shirt，等同於一般檔案欄位時 （以粗體顯示） 的 XML:  
  
```  
<color shirt="red"/>  
```  
  
> [!NOTE]
>  一般檔案結構描述有更進階的限制，在給定**記錄**從屬節點**欄位屬性**節點必須在前面次級**記錄**節點或**欄位項目**節點。  
  
## <a name="see-also"></a>另請參閱  
-  [欄位考量](../core/field-considerations.md)
-  **節點名稱**屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]