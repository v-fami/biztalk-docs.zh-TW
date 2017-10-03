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
# <a name="field-element-nodes-vs-field-attribute-nodes"></a><span data-ttu-id="a7263-102">欄位項目節點與欄位屬性節點</span><span class="sxs-lookup"><span data-stu-id="a7263-102">Field Element Nodes vs. Field Attribute Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="a7263-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a7263-103">Overview</span></span>
<span data-ttu-id="a7263-104">一般檔案解譯器可使用一般檔案結構描述，控制將輸入一般檔案執行個體訊息轉譯為其對等 XML 格式的方式；一般檔案組合器可使用一般檔案結構描述，控制將輸出 XML 訊息轉譯為其對等一般檔案執行個體訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="a7263-104">Flat file schemas are used by the flat file disassembler to control how inbound flat file instance messages are translated into their equivalent XML form, and are used by the flat file assembler to control how outbound XML messages are translated into their equivalent flat file instance messages.</span></span> <span data-ttu-id="a7263-105">建構此類結構描述，當您使用**欄位項目**節點或**欄位屬性**節點內特定位置的結構描述來控制一般檔案執行個體中的特定欄位是否訊息對應的 XML 項目或 XML 屬性中對等 XML 格式的訊息。</span><span class="sxs-lookup"><span data-stu-id="a7263-105">When constructing such schemas, you use either a **Field Element** node or a **Field Attribute** node in particular positions within the schema to control whether a particular field in the flat file instance message corresponds to an XML element or to an XML attribute in the equivalent XML form of the message.</span></span>  

## <a name="example"></a><span data-ttu-id="a7263-106">範例</span><span class="sxs-lookup"><span data-stu-id="a7263-106">Example</span></span>  
 <span data-ttu-id="a7263-107">比方說，是靠左對齊、 星號填補的欄位值 」`red*****`「 一般檔案中執行個體訊息轉譯成其相等的 XML 表示方式有兩種根據該結構描述中的欄位是否**欄位項目**節點或**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="a7263-107">For example, the left-aligned, asterisk-padded field value "`red*****`" in a flat file instance message can be translated into its equivalent XML representation in two different ways depending upon whether that field in the schema is a **Field Element** node or a **Field Attribute** node.</span></span> <span data-ttu-id="a7263-108">當結構描述中表示該欄位**欄位項目**節點具有其**節點名稱**屬性設為 [色彩]，而且包含**記錄**節點都有其**節點名稱**屬性設定為"shirt"，對等 XML （以粗體顯示） 的一般檔案欄位。</span><span class="sxs-lookup"><span data-stu-id="a7263-108">When that field is represented in the schema by a **Field Element** node with its **Node Name** property set to "color", and the containing **Record** node has its **Node Name** property set to "shirt", the XML equivalent of the flat file field is (shown in bold type).</span></span>  
  
```  
<shirt>  
    <color>red</color>  
</shirt>  
```  
  
 <span data-ttu-id="a7263-109">當結構描述中表示相同的一般檔案欄位**欄位屬性**節點具有其**節點名稱**屬性設為色彩，而且包含**記錄**節點都有其**節點名稱**屬性設為 shirt，等同於一般檔案欄位時 （以粗體顯示） 的 XML:</span><span class="sxs-lookup"><span data-stu-id="a7263-109">When that same flat file field is represented in the schema by a **Field Attribute** node with its **Node Name** property set to color, and the containing **Record** node has its **Node Name** property set to shirt, the XML equivalent of the flat file field is (shown in bold type):</span></span>  
  
```  
<color shirt="red"/>  
```  
  
> [!NOTE]
>  <span data-ttu-id="a7263-110">一般檔案結構描述有更進階的限制，在給定**記錄**從屬節點**欄位屬性**節點必須在前面次級**記錄**節點或**欄位項目**節點。</span><span class="sxs-lookup"><span data-stu-id="a7263-110">Flat file schemas have a further restriction that within a given **Record** node, subordinate **Field Attribute** nodes must come before subordinate **Record** nodes or **Field Element** nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7263-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7263-111">See Also</span></span>  
-  [<span data-ttu-id="a7263-112">欄位考量</span><span class="sxs-lookup"><span data-stu-id="a7263-112">Field Considerations</span></span>](../core/field-considerations.md)
-  <span data-ttu-id="a7263-113">**節點名稱**屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a7263-113">**Node Name** property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>