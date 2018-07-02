---
title: 欄位項目節點與欄位屬性節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1fffbca-8886-42c0-9214-cd0c5314850c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6c56aae4e681632ef056a7ed3b85aa5c4f88f89
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974159"
---
# <a name="field-element-nodes-vs-field-attribute-nodes"></a>欄位項目節點與欄位屬性節點

## <a name="overview"></a>概觀
一般檔案解譯器可使用一般檔案結構描述，控制將輸入一般檔案執行個體訊息轉譯為其對等 XML 格式的方式；一般檔案組合器可使用一般檔案結構描述，控制將輸出 XML 訊息轉譯為其對等一般檔案執行個體訊息的方式。 建構這類結構描述，當您使用**欄位項目** 節點或**Field 屬性**節點內特定位置來控制結構描述是否在一般檔案執行個體中的特定欄位訊息對應的 XML 項目，或到對等 XML 格式的訊息中的 XML 屬性。  

## <a name="example"></a>範例  
 例如，靠左對齊，星號填補的欄位值 」`red*****`"中的一般檔案執行個體訊息，可以轉譯為其對等的 XML 表示中兩個不同的方式，根據該結構描述中的欄位是否**欄位項目**節點或**Field 屬性**節點。 當結構描述中表示該欄位**欄位項目**節點及其**節點名稱**屬性設定為 「 色彩 」，而且包含**記錄**節點都有其**節點名稱**屬性設定為"shirt"，對等的 XML （以粗體顯示） 的一般檔案欄位。  

```  
<shirt>  
    <color>red</color>  
</shirt>  
```  

 當結構描述中表示相同的一般檔案欄位**欄位屬性**節點及其**節點名稱**屬性設定為 色彩和包含**記錄**節點有其**節點名稱**屬性設為 shirt，等同於時 （以粗體顯示） 的一般檔案欄位的 XML:  

```  
<color shirt="red"/>  
```  

> [!NOTE]
>  一般檔案結構描述有更進階的限制，在給定**記錄**節點，次級**Field 屬性**節點必須在前面次級**記錄**節點或**欄位項目**節點。  

## <a name="see-also"></a>另請參閱  
- [欄位考量](../core/field-considerations.md)
- **節點名稱**屬性 [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
