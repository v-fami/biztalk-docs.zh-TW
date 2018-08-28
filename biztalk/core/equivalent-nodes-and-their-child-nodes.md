---
title: 對等節點和其子節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a85c6a1-6121-4849-b958-7c4bd1c7c552
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82c58b477130431ce2b115cb141af759b6614b57
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012047"
---
# <a name="equivalent-nodes-and-their-child-nodes"></a><span data-ttu-id="4234f-102">對等節點和其子節點</span><span class="sxs-lookup"><span data-stu-id="4234f-102">Equivalent Nodes and Their Child Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="4234f-103">概觀</span><span class="sxs-lookup"><span data-stu-id="4234f-103">Overview</span></span>
<span data-ttu-id="4234f-104">**\<相等\>** 節點及其子節點用於結構描述樹狀結構顯示出現的複雜資料型別多型。</span><span class="sxs-lookup"><span data-stu-id="4234f-104">The **\<Equivalent\>** node and its children are used in the schema tree to display occurrences of complex data type polymorphism.</span></span> <span data-ttu-id="4234f-105">當您從其他複雜資料型別衍生一個複雜資料型別時，在 XSD 中的多型可以讓這些資料型別中的任何一個發生在已指定基底複雜資料型別之位置的執行個體訊息中。</span><span class="sxs-lookup"><span data-stu-id="4234f-105">When you derive one complex data type from another complex data type, polymorphism within XSD allows either of these data types to occur in instance messages in locations for which the base complex data type has been specified.</span></span> <span data-ttu-id="4234f-106">結構描述驗證期間的多個可能的複雜資料型別其中一個允許在特定位置的事實會隱含地表示相關聯的基底複雜資料型別名稱**基底**屬性**延伸模組**或是**限制**衍生的複雜資料類型的項目。</span><span class="sxs-lookup"><span data-stu-id="4234f-106">During schema validation, the fact that one of multiple possible complex data types is allowed at a particular location is represented implicitly by the base complex data type name associated with the **base** attribute of the **extension** or **restriction** elements of the derived complex data types.</span></span> <span data-ttu-id="4234f-107">若要讓此多型結構描述樹狀結構中較明顯**\<相等\>** 節點及其子節點會明確地顯示。</span><span class="sxs-lookup"><span data-stu-id="4234f-107">To make this polymorphism more obvious in the schema tree, the **\<Equivalent\>** node and its child nodes are displayed explicitly.</span></span>  

 <span data-ttu-id="4234f-108">**\<相等\>** 節點會顯示為子節點的項目之基底複雜資料型別，指出有可能會在該位置執行個體中發生的多個複雜資料型別訊息。</span><span class="sxs-lookup"><span data-stu-id="4234f-108">The **\<Equivalent\>** node is displayed as a child node of occurrences of the base complex data type, indicating that there are multiple complex data types that could occur at that position in an instance message.</span></span> <span data-ttu-id="4234f-109">子節點**\<相等\>** 節點會顯示的值為**名稱**屬性的對應**complexType**多型，並顯示在角括弧內之 XSD 表示法中的項目 (\<名稱\>)。</span><span class="sxs-lookup"><span data-stu-id="4234f-109">The child nodes of the **\<Equivalent\>** node are displayed as the value of the **name** attribute of the corresponding **complexType** element in the XSD representation of the polymorphism, displayed within angle brackets (\<name\>).</span></span>  

 <span data-ttu-id="4234f-110">**\<相等\>** 節點和其子系各有與其相關聯的只有兩個屬性：</span><span class="sxs-lookup"><span data-stu-id="4234f-110">The **\<Equivalent\>** node and its children each have only two properties associated with them:</span></span>  

-   <span data-ttu-id="4234f-111">**\<對等\>** 節點：**節點名稱**和**基底型別**</span><span class="sxs-lookup"><span data-stu-id="4234f-111">**\<Equivalent\>** node: **Node Name** and **Base Type**</span></span>

-   <span data-ttu-id="4234f-112">子節點：**節點名稱**和**衍生型別**</span><span class="sxs-lookup"><span data-stu-id="4234f-112">Child nodes: **Node Name** and **Derivation Type**</span></span>

<span data-ttu-id="4234f-113">這些屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="4234f-113">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="xsd-representation"></a><span data-ttu-id="4234f-114">XSD 表示法</span><span class="sxs-lookup"><span data-stu-id="4234f-114">XSD representation</span></span>  
 <span data-ttu-id="4234f-115">沒有任何直接的 XSD 表示法**\<相等\>** 節點及其子系。</span><span class="sxs-lookup"><span data-stu-id="4234f-115">There is no direct XSD representation of the **\<Equivalent\>** node and its children.</span></span> <span data-ttu-id="4234f-116">此節點用於結構描述樹狀結構中，使複雜資料型別多型更容易觀察。</span><span class="sxs-lookup"><span data-stu-id="4234f-116">This node is used within the schema tree to make complex data type polymorphism more visible and obvious.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4234f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4234f-117">See Also</span></span>  
- [<span data-ttu-id="4234f-118">BizTalk 結構描述表示法</span><span class="sxs-lookup"><span data-stu-id="4234f-118">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
- [<span data-ttu-id="4234f-119">節點屬性</span><span class="sxs-lookup"><span data-stu-id="4234f-119">Node Properties</span></span>](../core/node-properties.md)   
- <span data-ttu-id="4234f-120">**Sequence 群組節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="4234f-120">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
- [<span data-ttu-id="4234f-121">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="4234f-121">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)
