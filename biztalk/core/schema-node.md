---
title: "結構描述節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ea02c2a-ee00-4f44-9086-83d7ac4a8832
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dee662cb9cb6e86b85a7760daf45af832a447b5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-node"></a><span data-ttu-id="520c2-102">結構描述節點</span><span class="sxs-lookup"><span data-stu-id="520c2-102">Schema Node</span></span>

## <a name="overview"></a><span data-ttu-id="520c2-103">概觀</span><span class="sxs-lookup"><span data-stu-id="520c2-103">Overview</span></span>
<span data-ttu-id="520c2-104">在 [BizTalk 編輯器] 中，結構描述階層的頂層永遠是**結構描述**節點，無法重新命名。</span><span class="sxs-lookup"><span data-stu-id="520c2-104">In BizTalk Editor, the top of the schema hierarchy is always the **Schema** node, which cannot be renamed.</span></span> <span data-ttu-id="520c2-105">**結構描述**節點對應至**結構描述**結構描述的 XML 結構描述定義 (XSD) 語言表示法中的項目。</span><span class="sxs-lookup"><span data-stu-id="520c2-105">The **Schema** node corresponds to the **schema** element in the XML Schema definition (XSD) language representation of the schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="520c2-106">在 [BizTalk 編輯器] 中，**結構描述**節點以字串表示\<結構描述 > 結構描述樹狀結構檢視中。</span><span class="sxs-lookup"><span data-stu-id="520c2-106">In BizTalk Editor, the **Schema** node is represented with the string \<Schema> in the schema tree view.</span></span>  
  
 <span data-ttu-id="520c2-107">一般而言，屬性**結構描述**節點對應屬性的**結構描述**結構描述之 XSD 表示法中的項目。</span><span class="sxs-lookup"><span data-stu-id="520c2-107">In general, the properties of the **Schema** node correspond to the attributes of the **schema** element in the XSD representation of the schema.</span></span> <span data-ttu-id="520c2-108">如需節點屬性的一般資訊，請參閱[節點屬性](../core/node-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="520c2-108">For general information about node properties, see [Node Properties](../core/node-properties.md).</span></span> <span data-ttu-id="520c2-109">如需屬性的參考資訊**結構描述** 節點，請參閱**結構描述節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="520c2-109">For reference information about the properties of the **Schema** node, see the **Schema Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="520c2-110">當您在 「 BizTalk 編輯器 」 中，建立新的 XML 結構描述**結構描述**節點和一個**根**節點會自動建立。</span><span class="sxs-lookup"><span data-stu-id="520c2-110">When you create a new XML schema in BizTalk Editor, the **Schema** node and one **Root** node are created automatically.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="520c2-111">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="520c2-111">XSD representation</span></span>  
 <span data-ttu-id="520c2-112">下列範例所示，以粗體類型，對應至結構描述之 XSD 表示法中的線條**\<結構描述 >**的結構描述樹狀檢視中的節點。</span><span class="sxs-lookup"><span data-stu-id="520c2-112">The following example shows, in bold type, the lines in the XSD representation of the schema that correspond to the **\<Schema>** node in the tree view of the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="520c2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="520c2-113">See Also</span></span>  
 <span data-ttu-id="520c2-114">[BizTalk 結構描述表示法](../core/biztalk-representation-of-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="520c2-114">[BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md) </span></span>  
 <span data-ttu-id="520c2-115">[節點屬性](../core/node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="520c2-115">[Node Properties](../core/node-properties.md) </span></span>  
 [<span data-ttu-id="520c2-116">設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="520c2-116">Set Node Properties</span></span>](../core/how-to-set-node-properties.md)