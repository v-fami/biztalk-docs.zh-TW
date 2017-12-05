---
title: "控制執行個體的節點訊息結構和變化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af8e6ce-282d-4318-a538-046b423ef033
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baa82def3f62c6a603ef67e098e53b48a49013a3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="nodes-that-control-instance-message-structure-and-variations"></a><span data-ttu-id="2196a-102">控制執行個體訊息結構與變化的節點</span><span class="sxs-lookup"><span data-stu-id="2196a-102">Nodes That Control Instance Message Structure and Variations</span></span>
<span data-ttu-id="2196a-103">您用來在 [BizTalk 編輯器] 中建立結構描述之部分類型的節點可以控制執行個體訊息的結構和其中的變化。</span><span class="sxs-lookup"><span data-stu-id="2196a-103">Some of the node types that you use to create schemas in BizTalk Editor control the structure of, and variations within, instance messages.</span></span> <span data-ttu-id="2196a-104">您使用**Sequence 群組**節點，以指定的項目序列必須發生在執行個體訊息中的對應位置的特定順序。</span><span class="sxs-lookup"><span data-stu-id="2196a-104">You use **Sequence Group** nodes to specify that a sequence of elements must occur in a specific order in the corresponding location in an instance message.</span></span> <span data-ttu-id="2196a-105">您使用**Choice 群組**節點，以指定的項目集合中的一個項目可能會發生在執行個體訊息中對應的位置。</span><span class="sxs-lookup"><span data-stu-id="2196a-105">You use **Choice Group** nodes to specify that one element from a collection of elements can occur in the corresponding location in an instance message.</span></span> <span data-ttu-id="2196a-106">您使用**All 群組**節點，以指定的所有指定的項目可以發生在任何順序，但是只能出現一次，在執行個體訊息中對應的位置。</span><span class="sxs-lookup"><span data-stu-id="2196a-106">You use **All Group** nodes to specify that all of the specified elements can occur in any order, but only once, at the corresponding location in an instance message.</span></span> <span data-ttu-id="2196a-107">**\<對等\>**節點和及其子節點會顯示在結構描述樹狀結構，表示執行個體訊息中以衍生為基礎的多型的位置生效，允許其中許多相關的複雜資料類型會出現在執行個體訊息中對應的位置。</span><span class="sxs-lookup"><span data-stu-id="2196a-107">**\<Equivalent\>** nodes and their child nodes are displayed in the schema tree to indicate locations in instance messages where derivation-based polymorphism is in effect, allowing one of many related complex data types to occur in the corresponding location in an instance message.</span></span>  
  
 <span data-ttu-id="2196a-108">本節其餘部分提供此節點類別的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2196a-108">The remainder of this section provides additional information about this class of nodes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2196a-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="2196a-109">In This Section</span></span>  
  
-   [<span data-ttu-id="2196a-110">Sequence 群組節點</span><span class="sxs-lookup"><span data-stu-id="2196a-110">Sequence Group Nodes</span></span>](../core/sequence-group-nodes.md)  
  
-   [<span data-ttu-id="2196a-111">Choice 群組節點</span><span class="sxs-lookup"><span data-stu-id="2196a-111">Choice Group Nodes</span></span>](../core/choice-group-nodes.md)  
  
-   [<span data-ttu-id="2196a-112">All 群組節點</span><span class="sxs-lookup"><span data-stu-id="2196a-112">All Group Nodes</span></span>](../core/all-group-nodes.md)  
  
-   [<span data-ttu-id="2196a-113">\<對等\>節點和及其子節點</span><span class="sxs-lookup"><span data-stu-id="2196a-113">\<Equivalent\> Nodes and Their Child Nodes</span></span>](../core/equivalent-nodes-and-their-child-nodes.md)