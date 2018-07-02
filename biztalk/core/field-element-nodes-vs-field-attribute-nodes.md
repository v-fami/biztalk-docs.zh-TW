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
# <a name="field-element-nodes-vs-field-attribute-nodes"></a><span data-ttu-id="4e469-102">欄位項目節點與欄位屬性節點</span><span class="sxs-lookup"><span data-stu-id="4e469-102">Field Element Nodes vs. Field Attribute Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="4e469-103">概觀</span><span class="sxs-lookup"><span data-stu-id="4e469-103">Overview</span></span>
<span data-ttu-id="4e469-104">一般檔案解譯器可使用一般檔案結構描述，控制將輸入一般檔案執行個體訊息轉譯為其對等 XML 格式的方式；一般檔案組合器可使用一般檔案結構描述，控制將輸出 XML 訊息轉譯為其對等一般檔案執行個體訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="4e469-104">Flat file schemas are used by the flat file disassembler to control how inbound flat file instance messages are translated into their equivalent XML form, and are used by the flat file assembler to control how outbound XML messages are translated into their equivalent flat file instance messages.</span></span> <span data-ttu-id="4e469-105">建構這類結構描述，當您使用**欄位項目** 節點或**Field 屬性**節點內特定位置來控制結構描述是否在一般檔案執行個體中的特定欄位訊息對應的 XML 項目，或到對等 XML 格式的訊息中的 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="4e469-105">When constructing such schemas, you use either a **Field Element** node or a **Field Attribute** node in particular positions within the schema to control whether a particular field in the flat file instance message corresponds to an XML element or to an XML attribute in the equivalent XML form of the message.</span></span>  

## <a name="example"></a><span data-ttu-id="4e469-106">範例</span><span class="sxs-lookup"><span data-stu-id="4e469-106">Example</span></span>  
 <span data-ttu-id="4e469-107">例如，靠左對齊，星號填補的欄位值 」`red*****`"中的一般檔案執行個體訊息，可以轉譯為其對等的 XML 表示中兩個不同的方式，根據該結構描述中的欄位是否**欄位項目**節點或**Field 屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="4e469-107">For example, the left-aligned, asterisk-padded field value "`red*****`" in a flat file instance message can be translated into its equivalent XML representation in two different ways depending upon whether that field in the schema is a **Field Element** node or a **Field Attribute** node.</span></span> <span data-ttu-id="4e469-108">當結構描述中表示該欄位**欄位項目**節點及其**節點名稱**屬性設定為 「 色彩 」，而且包含**記錄**節點都有其**節點名稱**屬性設定為"shirt"，對等的 XML （以粗體顯示） 的一般檔案欄位。</span><span class="sxs-lookup"><span data-stu-id="4e469-108">When that field is represented in the schema by a **Field Element** node with its **Node Name** property set to "color", and the containing **Record** node has its **Node Name** property set to "shirt", the XML equivalent of the flat file field is (shown in bold type).</span></span>  

```  
<shirt>  
    <color>red</color>  
</shirt>  
```  

 <span data-ttu-id="4e469-109">當結構描述中表示相同的一般檔案欄位**欄位屬性**節點及其**節點名稱**屬性設定為 色彩和包含**記錄**節點有其**節點名稱**屬性設為 shirt，等同於時 （以粗體顯示） 的一般檔案欄位的 XML:</span><span class="sxs-lookup"><span data-stu-id="4e469-109">When that same flat file field is represented in the schema by a **Field Attribute** node with its **Node Name** property set to color, and the containing **Record** node has its **Node Name** property set to shirt, the XML equivalent of the flat file field is (shown in bold type):</span></span>  

```  
<color shirt="red"/>  
```  

> [!NOTE]
>  <span data-ttu-id="4e469-110">一般檔案結構描述有更進階的限制，在給定**記錄**節點，次級**Field 屬性**節點必須在前面次級**記錄**節點或**欄位項目**節點。</span><span class="sxs-lookup"><span data-stu-id="4e469-110">Flat file schemas have a further restriction that within a given **Record** node, subordinate **Field Attribute** nodes must come before subordinate **Record** nodes or **Field Element** nodes.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4e469-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e469-111">See Also</span></span>  
- [<span data-ttu-id="4e469-112">欄位考量</span><span class="sxs-lookup"><span data-stu-id="4e469-112">Field Considerations</span></span>](../core/field-considerations.md)
- <span data-ttu-id="4e469-113">**節點名稱**屬性 [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="4e469-113">**Node Name** property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
