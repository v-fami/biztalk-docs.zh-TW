---
title: "根節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2161f877-835e-434d-a8d1-2426f977d60e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2070982a6bca09e8bffb2bcc88e5997360c86851
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="root-nodes"></a><span data-ttu-id="d4ef3-102">根節點</span><span class="sxs-lookup"><span data-stu-id="d4ef3-102">Root Nodes</span></span>
<span data-ttu-id="d4ef3-103">在 BizTalk 編輯器中的子節點**結構描述**節點稱為**根**節點。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-103">In BizTalk Editor, child nodes of the **Schema** node are known as **Root** nodes.</span></span> <span data-ttu-id="d4ef3-104">**根**節點是一種特殊型別的**記錄** 節點，而且有較多的屬性，比一般**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-104">**Root** nodes are a special type of **Record** node, and have a few more properties than regular **Record** nodes.</span></span> <span data-ttu-id="d4ef3-105">**根**節點表示結構描述所描述的文件的類型，可以重新命名依適當情況。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-105">The **Root** node represents the type of document described by the schema, and can be renamed as appropriate.</span></span> <span data-ttu-id="d4ef3-106">例如，您可以重新命名**根**節點，使它描述的結構描述表示，如 purchaseOrder、 orderAcknowledgment 或 shipNotice 的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-106">For example, you can rename the **Root** node so that it describes the type of message that the schema represents, such as purchaseOrder, orderAcknowledgment, or shipNotice.</span></span>  
  
 <span data-ttu-id="d4ef3-107">當您在 「 BizTalk 編輯器 」 中，建立新的 XML 結構描述**結構描述**節點和一個**根**節點會自動建立。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-107">When you create a new XML schema in BizTalk Editor, the **Schema** node and one **Root** node are created automatically.</span></span> <span data-ttu-id="d4ef3-108">您可以建立其他**根**節點的子系**結構描述**節點; 這可讓您建立單一的 XML 結構描述定義 (XSD) 語言表示法中的結構描述的程式庫。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-108">You can create additional **Root** nodes as children of the **Schema** node; this enables you to create a library of schemas within a single XML Schema definition (XSD) language representation.</span></span> <span data-ttu-id="d4ef3-109">例如，您可以建立結構描述程式庫，以描述與傳送訂單、命名各種根節點 purchaseOrder、orderAcknowledgment 和 shipNotice 相關之訊息的各種結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-109">For example, you can create a library of schemas to describe the various schemas of messages related to sending purchase orders, naming the various root nodes purchaseOrder, orderAcknowledgment, and shipNotice.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="d4ef3-110">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="d4ef3-110">XSD representation</span></span>  
 <span data-ttu-id="d4ef3-111">下列範例會示範幾行中對應的結構描述之 XSD 表示法**根**的結構描述樹狀檢視中的節點。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-111">The following example shows the lines in the XSD representation of the schema that correspond to the **Root** node in the tree view of the schema.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="Root">  
        <xs:complexType />   
    </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="d4ef3-112">**根**節點在 [BizTalk 編輯器] 中代表該訊息的對應 XML 執行個體中的主要項目。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-112">**Root** nodes in BizTalk Editor represent the main element in a corresponding XML instance of the message in question.</span></span> <span data-ttu-id="d4ef3-113">例如，如果**根**特定結構描述中的節點已重新命名為 purchaseOrder，對應的 XSD 表示法具有下列的高階結構。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-113">For example, if the **Root** node of a particular schema is renamed to purchaseOrder, the corresponding XSD representation has the following high-level structure.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="http://BizTalk_Server_Project1.Schema2"  
    xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
    targetNamespace="http://BizTalk_Server_Project1.Schema2"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="">  
        <xs:complexType>   
            ...  
        </xs:complexType>   
    </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="d4ef3-114">對應的 XML 執行個體訊息必須具有下列的基本結構。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-114">A corresponding XML instance message must have the following basic structure.</span></span>  
  
```  
<?xml version="1.0"?>  
<purchaseOrder ...>  
    ...  
</purchaseOrder>  
```  
  
> [!NOTE]
>  <span data-ttu-id="d4ef3-115">根節點不能有**欄位**屬性。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-115">Root nodes may not have **Field** attributes.</span></span> <span data-ttu-id="d4ef3-116">**欄位**屬性附加至**根**節點不會儲存與結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4ef3-116">**Field** attributes attached to the **Root** node are not saved with the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ef3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ef3-117">See Also</span></span>  
-  [<span data-ttu-id="d4ef3-118">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="d4ef3-118">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="d4ef3-119">節點屬性</span><span class="sxs-lookup"><span data-stu-id="d4ef3-119">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="d4ef3-120">**記錄節點屬性**  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="d4ef3-120">**Record Node Properties**  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
-  [<span data-ttu-id="d4ef3-121">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="d4ef3-121">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)