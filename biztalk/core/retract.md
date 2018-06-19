---
title: 撤銷 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], TypedData table
- Retract function [Business Rules Engine], TypedXMLDocument
- Retract function [Business Rules Engine]
- Retract function [Business Rules Engine], DataConnection
- Retract function [Business Rules Engine], .NET objects
- .NET objects
ms.assetid: 24b6b894-6810-4497-a122-8c91f0b2e816
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17eb4739412d310d2a69b53c8470abc7461ce3ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270110"
---
# <a name="retract"></a><span data-ttu-id="3d361-102">撤回</span><span class="sxs-lookup"><span data-stu-id="3d361-102">Retract</span></span>
<span data-ttu-id="3d361-103">您可以使用**Retract**函式，從 「 商務規則引擎工作記憶體移除物件。</span><span class="sxs-lookup"><span data-stu-id="3d361-103">You can use the **Retract** function to remove objects from the Business Rule Engine's working memory.</span></span> <span data-ttu-id="3d361-104">下列幾段描述從規則引擎的工作記憶體撤回不同類型實體的關聯行為。</span><span class="sxs-lookup"><span data-stu-id="3d361-104">The following paragraphs describe the behavior associated with retracting entities of different types from the rule engine's working memory.</span></span>  
  
## <a name="net-objects"></a><span data-ttu-id="3d361-105">.NET 物件</span><span class="sxs-lookup"><span data-stu-id="3d361-105">.NET Objects</span></span>  
 <span data-ttu-id="3d361-106">.NET 物件是否已收回原則中使用**Retract**函式。</span><span class="sxs-lookup"><span data-stu-id="3d361-106">A .NET object is retracted in a policy by using the **Retract** function.</span></span> <span data-ttu-id="3d361-107">此函式是做為 「 商務規則編輯器 」 中可用**函式**詞彙項目： 將類別 （而非從組件或方法） 拖曳到**Retract**參數。</span><span class="sxs-lookup"><span data-stu-id="3d361-107">This function is available in the Business Rule Composer as a **Functions** vocabulary item: drag the class (not the assembly or method) into the **Retract** parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d361-108">如果您拖曳到方法**Retract**函式，引擎會嘗試撤回該方法所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="3d361-108">If you drag a method into the **Retract** function, the engine attempts to retract the object returned by the method.</span></span>  
  
 <span data-ttu-id="3d361-109">撤回 .NET 物件也會從規則引擎的工作記憶體移除它，並且有下列影響：</span><span class="sxs-lookup"><span data-stu-id="3d361-109">Retracting a .NET object removes it from the rule engine's working memory and has the following impact:</span></span>  
  
-   <span data-ttu-id="3d361-110">在述詞中使用物件的規則，具有其已從議程移除的動作 (如果議程上存在任何動作)。</span><span class="sxs-lookup"><span data-stu-id="3d361-110">Rules that use the object in a predicate have their actions removed from the agenda (if any exist on the agenda).</span></span>  
  
-   <span data-ttu-id="3d361-111">會從議程中移除議程上使用物件的動作。</span><span class="sxs-lookup"><span data-stu-id="3d361-111">Actions on the agenda that use the objects are removed from the agenda.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3d361-112">之前可能已經執行更高層議程上的其他動作**Retract**呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="3d361-112">Other actions higher up on the agenda may have already executed before the **Retract** function was called.</span></span>  
  
-   <span data-ttu-id="3d361-113">物件已不再由引擎所評估。</span><span class="sxs-lookup"><span data-stu-id="3d361-113">The object is no longer evaluated by the engine.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="3d361-114">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="3d361-114">TypedXmlDocument</span></span>  
 <span data-ttu-id="3d361-115">您可以撤回原始**TypedXmlDocument** ，判斷提示到引擎，或是撤回其中一個子系**TypedXmlDocument**從父代的節點建立**XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="3d361-115">You can either retract the original **TypedXmlDocument** that was asserted into the engine or retract one of the child **TypedXmlDocument**s created from a node of the parent **XmlDocument**.</span></span>  
  
 <span data-ttu-id="3d361-116">您可以使用下列 XML 做為範例，您可以撤回**TypedXmlDocument**順序或一個或多個相關聯**TypedXmlDocument**與 orderline 關聯。</span><span class="sxs-lookup"><span data-stu-id="3d361-116">Using the following XML as an example, you can either retract the **TypedXmlDocument** associated with order or one or both of the **TypedXmlDocument**s associated with orderline.</span></span>  
  
```  
<order>  
   <orderline customer="Joe" linenumber="001">  
      <product name="router" quantity="10" cost="550" />  
   </orderline>  
   <orderline customer="Jane" linenumber="002">  
      <product name="switch" quantity="1" cost="300" />  
   </orderline>  
</order>  
```  
  
 <span data-ttu-id="3d361-117">若要撤回 Order 物件，您可以在 XML 描述結構事實窗格中拖曳描述結構的最上方節點。</span><span class="sxs-lookup"><span data-stu-id="3d361-117">To retract the order object, you would drag the top node for the schema in the XML Schemas fact pane.</span></span> <span data-ttu-id="3d361-118">此節點以".xsd"結束，並代表文件根節點 （不是文件項目節點）。它有"/"選取器，它是指初始**TypedXmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="3d361-118">This node ends in ".xsd" and represents the document root node (not the document element node); it has a "/" selector that refers to the initial **TypedXmlDocument**.</span></span> <span data-ttu-id="3d361-119">當父**TypedXmlDocument**遭到撤回時，所有**TypedXmlDocument**與相關聯的執行個體**TypedXmlDocument** (所有**TypedXmlDocument**藉由呼叫建立的 s **Assert**函式會根據原則中所使用的選取器) 會從工作記憶體移除。</span><span class="sxs-lookup"><span data-stu-id="3d361-119">When the parent **TypedXmlDocument** is retracted, all **TypedXmlDocument** instances associated with the **TypedXmlDocument** (all **TypedXmlDocument**s created by calling the **Assert** function based on selectors used in the policy) are removed from working memory.</span></span>  
  
 <span data-ttu-id="3d361-120">若要撤回個別子系**TypedXmlDocument** (其為 orderline)，您可以將此節點從 XML 結構描述窗格，將**Retract**函式。</span><span class="sxs-lookup"><span data-stu-id="3d361-120">To retract only an individual child **TypedXmlDocument** (that is an orderline), you can drag this node from the XML Schemas pane into the **Retract** function.</span></span> <span data-ttu-id="3d361-121">請務必注意，所有**TypedXmlDocument**s 相關聯的最上層**TypedXmlDocument** ，最初判斷提示，而不是使用**TypedXmlDocument**上方出現在 XML 樹狀結構階層架構中。</span><span class="sxs-lookup"><span data-stu-id="3d361-121">It is important to note that all **TypedXmlDocument**s are associated with the top-level **TypedXmlDocument** that was originally asserted, and not with the **TypedXmlDocument** that appears above it in the XML tree hierarchy.</span></span> <span data-ttu-id="3d361-122">例如，產品是**TypedXmlDocument**低於 orderline 物件中; 因此，它會與順序相關聯**TypedXmlDocument**，而不是與 orderline **TypedXmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="3d361-122">For example, product is a **TypedXmlDocument** below the orderline object; therefore, it would be associated with the order **TypedXmlDocument**, and not with the orderline **TypedXmlDocument**.</span></span> <span data-ttu-id="3d361-123">在大部分的執行個體中，這個差別並不重要。</span><span class="sxs-lookup"><span data-stu-id="3d361-123">In most instances, this distinction is not important.</span></span> <span data-ttu-id="3d361-124">不過，若您撤回 Order 物件，Orderline 和 Product 物件也會被撤回。</span><span class="sxs-lookup"><span data-stu-id="3d361-124">However, if you retract the order object, the orderline and product objects are also retracted.</span></span> <span data-ttu-id="3d361-125">如果您撤回 Orderline 物件，則只有該物件會被撤回，而不會撤回 Product 物件。</span><span class="sxs-lookup"><span data-stu-id="3d361-125">If you retract the orderline object, only that object is retracted, and not the product object.</span></span>  
  
 <span data-ttu-id="3d361-126">引擎只會使用和追蹤物件的執行個體 (**TypedXmlDocument**s) 時所建立**TypedXmlDocument**最初判斷提示。</span><span class="sxs-lookup"><span data-stu-id="3d361-126">The engine only works with and tracks object instances (**TypedXmlDocument**s) that it created when the **TypedXmlDocument** was initially asserted.</span></span> <span data-ttu-id="3d361-127">如果您建立其他節點 — 比方說，透過原則選取器選取的節點同層級節點，除非這些節點不在規則中評估**TypedXmlDocument**所建立及它們判斷提示。</span><span class="sxs-lookup"><span data-stu-id="3d361-127">If you create additional nodes—for example, sibling nodes to a node that was selected through a selector in the policy—these nodes are not evaluated in rules unless **TypedXmlDocument**s are created and asserted for them.</span></span> <span data-ttu-id="3d361-128">判斷提示這些新、 較低層級**TypedXmlDocuments**使它們來評估規則，但最上層**TypedXmlDocument**不了解它們。</span><span class="sxs-lookup"><span data-stu-id="3d361-128">Asserting these new, lower-level **TypedXmlDocuments** causes them to be evaluated in rules, but the top-level **TypedXmlDocument** does not have knowledge of them.</span></span> <span data-ttu-id="3d361-129">當最上層**TypedXmlDocument**遭到撤回時，新的且個別判斷提示**TypedXmlDocument**並不會自動撤回。</span><span class="sxs-lookup"><span data-stu-id="3d361-129">When the top-level **TypedXmlDocument** is retracted, the new, independently asserted **TypedXmlDocument**s isl not automatically retracted.</span></span> <span data-ttu-id="3d361-130">如此一來，如果建立新的節點，則通常更直接地撤回並重新判斷提示完整**XmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="3d361-130">As a result, if new nodes are created, it is typically most straightforward to retract and reassert the full **XmlDocument**.</span></span>  
  
 <span data-ttu-id="3d361-131">**TypedXmlDocument**類別支援一些有用的方法，可以在自訂.NET 成員呼叫做為動作的一部分。</span><span class="sxs-lookup"><span data-stu-id="3d361-131">The **TypedXmlDocument** class supports a number of useful methods that can be called within a custom .NET member as part of an action.</span></span> <span data-ttu-id="3d361-132">這些包括能夠取得**XmlNode**聯**TypedXmlDocument**或父**TypedXmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="3d361-132">These include the ability to get the **XmlNode** associated with the **TypedXmlDocument** or the parent **TypedXmlDocument**.</span></span>  
  
## <a name="typeddatatable"></a><span data-ttu-id="3d361-133">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="3d361-133">TypedDataTable</span></span>  
 <span data-ttu-id="3d361-134">您可以撤回個別**TypedDataRow**s 或整個**TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="3d361-134">You can retract either individual **TypedDataRow**s or the entire **TypedDataTable**.</span></span> <span data-ttu-id="3d361-135">如果您撤回資料表，所有包含的資料列也會從工作記憶體中撤回。</span><span class="sxs-lookup"><span data-stu-id="3d361-135">If you retract a table, all the containing rows are retracted from working memory.</span></span>  
  
 <span data-ttu-id="3d361-136">若要撤回整個**TypedDataTable**您要使用的 helper 函式來存取**父**屬性**TypedDataRow**，例如：</span><span class="sxs-lookup"><span data-stu-id="3d361-136">To retract the entire **TypedDataTable** you need to use a helper function to access the **Parent** property on **TypedDataRow**, for example:</span></span>  
  
```  
Retract(MyHelper.GetTypedDataTable(TypedDataRow))  
```  
  
 <span data-ttu-id="3d361-137">在前一個動作中，您會拖曳資料表至**TypedDataRow**。</span><span class="sxs-lookup"><span data-stu-id="3d361-137">In the preceding action, you would drag the table into **TypedDataRow**.</span></span> <span data-ttu-id="3d361-138">在**GetTypedDataTable**的值會傳回**TypedDataRow.Parent**。</span><span class="sxs-lookup"><span data-stu-id="3d361-138">In **GetTypedDataTable** you would return the value of **TypedDataRow.Parent**.</span></span>  
  
 <span data-ttu-id="3d361-139">如同**TypedXmlDocument**s，如果您判斷提示新增其他**TypedDataRow**同一個 s **DataTable**之後判斷提示**TypedDataTable**，則會視為個別的實體和撤銷**TypedDataTable**不會導致這些撤銷額外**TypedDataRow**s。</span><span class="sxs-lookup"><span data-stu-id="3d361-139">As with **TypedXmlDocument**s, if you assert additional, new **TypedDataRow**s for the same **DataTable** after asserting the **TypedDataTable**, they are treated as individual entities and retracting the **TypedDataTable** does not result in the retraction of these extra **TypedDataRow**s.</span></span> <span data-ttu-id="3d361-140">只有**TypedDataRow**中所包含的 s **TypedDataTable**當它已判斷提示會撤回。</span><span class="sxs-lookup"><span data-stu-id="3d361-140">Only the **TypedDataRow**s contained in the **TypedDataTable** when it was asserted are retracted.</span></span>  
  
## <a name="dataconnection"></a><span data-ttu-id="3d361-141">DataConnection</span><span class="sxs-lookup"><span data-stu-id="3d361-141">DataConnection</span></span>  
 <span data-ttu-id="3d361-142">當**DataConnection**遭到撤回時，所有**TypedDataRow**擷取從資料庫所建構之查詢透過**DataConnection**會撤回從工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="3d361-142">When a **DataConnection** is retracted, all **TypedDataRow**s retrieved from the database through the query constructed by the **DataConnection** are retracted from working memory.</span></span> <span data-ttu-id="3d361-143">**DataConnection**本身也撤回時，表示無其他**TypedDataRow**s 會透過擷取**DataConnection** （也就是透過使用**DataConnection**其他述詞或動作中)。</span><span class="sxs-lookup"><span data-stu-id="3d361-143">The **DataConnection** itself is also retracted, meaning that no more **TypedDataRow**s will be retrieved through the **DataConnection** (that is, through use of the **DataConnection** in other predicates or actions).</span></span>  
  
 <span data-ttu-id="3d361-144">當使用**DataConnection**，針對個別作業的任何撤回**TypedDataRow**引擎進入不一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="3d361-144">When using a **DataConnection**, any retract operation on an individual **TypedDataRow** puts the engine into an inconsistent state.</span></span> <span data-ttu-id="3d361-145">因此，作業不允許個別**TypedDataRow**與相關聯**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="3d361-145">Therefore, operations are not allowed on individual **TypedDataRow**s associated with a **DataConnection**.</span></span> <span data-ttu-id="3d361-146">如果您將資料表拖曳 (使用**DataConnection**參數) 到**Retract**函式，您將會撤回**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="3d361-146">If you drag the table (using the **DataConnection** parameter) into the **Retract** function, you will be retracting the **DataConnection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d361-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d361-147">See Also</span></span>  
 [<span data-ttu-id="3d361-148">引擎控制函式</span><span class="sxs-lookup"><span data-stu-id="3d361-148">Engine Control Functions</span></span>](../core/engine-control-functions.md)