---
title: 型別事實 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RuleEngine library
- Business Rule Composer, typed facts
- ITypedFact interface
- DataConnection class
- facts, typed
- TypedDataTable class
- TypedDataRow class
- TypedXmlDocument class
ms.assetid: 8207bfd5-ebd2-45ac-8992-795acdf3ba4c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6041a64fcc4b3496c319a25a2ce758ed7f52a71
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22287222"
---
# <a name="typed-facts"></a><span data-ttu-id="31d01-102">型別事實</span><span class="sxs-lookup"><span data-stu-id="31d01-102">Typed Facts</span></span>
<span data-ttu-id="31d01-103">*型別事實* 是類別，實作 **ITypedFact** 介面︰ **TypedXmlDocument**, ，**DataConnection**, ，**TypedDataTable**, ，和 **TypedDataRow**。</span><span class="sxs-lookup"><span data-stu-id="31d01-103">*Typed facts* are classes that implement the **ITypedFact** interface: **TypedXmlDocument**, **DataConnection**, **TypedDataTable**, and **TypedDataRow**.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="31d01-104">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="31d01-104">TypedXmlDocument</span></span>  
 <span data-ttu-id="31d01-105">**TypedXmlDocument** 類別代表商務規則架構中的 XML 文件類型。</span><span class="sxs-lookup"><span data-stu-id="31d01-105">The **TypedXmlDocument** class represents the XML document type in the Business Rules Framework.</span></span> <span data-ttu-id="31d01-106">使用 XML 文件的節點做為規則中的引數時，會建立兩個 XPath 運算式：「選取器」和「欄位」繫結。</span><span class="sxs-lookup"><span data-stu-id="31d01-106">When you use a node of an XML document as an argument in a rule, two XPath expressions are created: the Selector and Field bindings.</span></span>  
  
 <span data-ttu-id="31d01-107">如果節點沒有子節點， *選取器繫結* （也稱為 XmlDocument 繫結） 為了節點的父節點和 *欄位繫結* （也稱為 XmlDocumentMember 繫結） 為了節點本身。</span><span class="sxs-lookup"><span data-stu-id="31d01-107">If the node has no child nodes, a *Selector binding* (also known as an XmlDocument binding) is created to the node's parent node and a *Field binding* (also known as an XmlDocumentMember binding) is created to the node itself.</span></span> <span data-ttu-id="31d01-108">此欄位繫結是相對於選取器繫結。</span><span class="sxs-lookup"><span data-stu-id="31d01-108">This Field binding is relative to the Selector binding.</span></span> <span data-ttu-id="31d01-109">若該節點有子節點，便會對該節點建立選取器繫結，而不會建立欄位繫結。</span><span class="sxs-lookup"><span data-stu-id="31d01-109">If the node has child nodes, a Selector binding is created to the node and no Field binding is created.</span></span>  
  
 <span data-ttu-id="31d01-110">假設您有下列結構描述。</span><span class="sxs-lookup"><span data-stu-id="31d01-110">Suppose that you have the following schema.</span></span>  
  
 <span data-ttu-id="31d01-111">![在 [事實總管] 中顯示的範例結構描述](../core/media/xmldocumentbrowser.gif "xmldocumentbrowser")</span><span class="sxs-lookup"><span data-stu-id="31d01-111">![Sample schema displayed in Facts Explorer](../core/media/xmldocumentbrowser.gif "xmldocumentbrowser")</span></span>  
<span data-ttu-id="31d01-112">Case.xsd</span><span class="sxs-lookup"><span data-stu-id="31d01-112">Case.xsd</span></span>  
  
 <span data-ttu-id="31d01-113">因為 Income 節點有子節點，所以若選取該節點，只會建立選取器繫結。</span><span class="sxs-lookup"><span data-stu-id="31d01-113">If the Income node is selected, only a Selector binding is created, because the node has child nodes.</span></span> <span data-ttu-id="31d01-114">中的預設 XPath 運算式 **XPath 選取器** [屬性] 窗格中的屬性包含︰</span><span class="sxs-lookup"><span data-stu-id="31d01-114">The default XPath expression in the **XPath Selector** property of the Property pane contains:</span></span>  
  
```  
/*[local-name()='Root' and namespace-uri()='http://LoansProcessor.Case']/*[local-name()='Income' and namespace-uri()='']  
```  
  
 <span data-ttu-id="31d01-115">但是若選取 Name 節點，則會建立選取器繫結和欄位繫結兩者。</span><span class="sxs-lookup"><span data-stu-id="31d01-115">However, if the Name node is selected, both a Selector binding and a Field binding are created.</span></span> <span data-ttu-id="31d01-116">繫結資訊看起來如下。</span><span class="sxs-lookup"><span data-stu-id="31d01-116">The binding information looks like.</span></span>  
  
|<span data-ttu-id="31d01-117">屬性</span><span class="sxs-lookup"><span data-stu-id="31d01-117">Property</span></span>|<span data-ttu-id="31d01-118">Value</span><span class="sxs-lookup"><span data-stu-id="31d01-118">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="31d01-119">**XPath 欄位**</span><span class="sxs-lookup"><span data-stu-id="31d01-119">**XPath Field**</span></span>|<span data-ttu-id="31d01-120">\*[local-name()='Name' and namespace-uri()='']</span><span class="sxs-lookup"><span data-stu-id="31d01-120">\*[local-name()='Name' and namespace-uri()='']</span></span>|  
|<span data-ttu-id="31d01-121">**XPath 選取器**</span><span class="sxs-lookup"><span data-stu-id="31d01-121">**XPath Selector**</span></span>|<span data-ttu-id="31d01-122">/ \* [local-name = 'Root' and namespace-uri （) ='http://LoansProcessor.Case']</span><span class="sxs-lookup"><span data-stu-id="31d01-122">/\*[local-name()='Root' and namespace-uri()='http://LoansProcessor.Case']</span></span>|  
  
 <span data-ttu-id="31d01-123">在將節點拖曳至規則引數之前，您可以變更 XML 節點的預設 XPath 運算式，在原則中會放置新的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="31d01-123">You can change the default XPath expressions for the XML nodes before you drag the node into a rule argument, and the new binding information is placed in the policy.</span></span> <span data-ttu-id="31d01-124">不過請注意，對 XPath 運算式所做的任何編輯都必須在重新載入結構描述時，於「商務規則編輯器」中重新輸入。</span><span class="sxs-lookup"><span data-stu-id="31d01-124">Note, however, that any edits that are made to the XPath expressions must be re-entered in the Business Rule Composer when the schema is reloaded.</span></span>  
  
 <span data-ttu-id="31d01-125">為 XML 節點建立詞彙定義時，依據先前描述的規則，繫結的 XPath 運算式會擁有相似的預設值，但您可以在「詞彙定義精靈」中加以編輯。</span><span class="sxs-lookup"><span data-stu-id="31d01-125">When vocabulary definitions are created for XML nodes, the XPath expressions for the bindings have similar defaults based on the rules described earlier, but can be edited in the Vocabulary Definition Wizard.</span></span> <span data-ttu-id="31d01-126">對運算式所做的變更會放置在詞彙定義中，而且會反映在從定義建置的任何規則引數中。</span><span class="sxs-lookup"><span data-stu-id="31d01-126">Changes to the expressions are placed in the vocabulary definition and are reflected in any rule arguments built from the definitions.</span></span>  
  
## <a name="dataconnection"></a><span data-ttu-id="31d01-127">DataConnection</span><span class="sxs-lookup"><span data-stu-id="31d01-127">DataConnection</span></span>  
 <span data-ttu-id="31d01-128">**DataConnection** .NET 類別提供 **RuleEngine** 程式庫。</span><span class="sxs-lookup"><span data-stu-id="31d01-128">**DataConnection** is a .NET class provided in the **RuleEngine** library.</span></span> <span data-ttu-id="31d01-129">它包含一個.NET **SqlConnection** 執行個體和 **資料集** 名稱。</span><span class="sxs-lookup"><span data-stu-id="31d01-129">It contains a .NET **SqlConnection** instance and a **DataSet** name.</span></span> <span data-ttu-id="31d01-130">**資料集** 名稱可讓您建立的唯一識別項 **SqlConnection** ，用於將產生的型別定義。</span><span class="sxs-lookup"><span data-stu-id="31d01-130">The **DataSet** name enables you to create a unique identifier for the **SqlConnection** and is used in defining the resulting type.</span></span>  
  
 <span data-ttu-id="31d01-131">**DataConnection** 類別會提供商務規則引擎的效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="31d01-131">The **DataConnection** class provides a performance optimization to the Business Rule engine.</span></span> <span data-ttu-id="31d01-132">而不判斷提示到引擎非常大型的資料庫資料表 (**TypedDataTable** 類別) 可能包含多個資料庫資料列 (**TypedDataRow** 類別) 並非與原則相關，您可以判斷提示輕量型 **DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="31d01-132">Rather than asserting into the engine very large database tables (**TypedDataTable** class) that may contain many database rows (**TypedDataRow** class) that are not relevant to the policy, you can assert a lightweight **DataConnection**.</span></span> <span data-ttu-id="31d01-133">當引擎評估原則時，它會動態建立根據規則述詞/動作及查詢的 SELECT 查詢 **DataConnection** 在執行。</span><span class="sxs-lookup"><span data-stu-id="31d01-133">When the engine evaluates a policy, it dynamically builds a SELECT query based on the rule predicates/actions and queries the **DataConnection** at execution.</span></span> <span data-ttu-id="31d01-134">例如，假設您有下列規則：</span><span class="sxs-lookup"><span data-stu-id="31d01-134">For example, suppose you have the following rule:</span></span>  
  
```  
IF NorthWind.Products.UnitPrice >= 0   
THEN <do something>  
```  
  
 <span data-ttu-id="31d01-135">該規則會產生下列 SQL 查詢：</span><span class="sxs-lookup"><span data-stu-id="31d01-135">The following SQL query is generated by from the rule:</span></span>  
  
```  
Select * From [Product] Where [UnitPrice] >= 0  
```  
  
 <span data-ttu-id="31d01-136">查詢結果會做為資料列判斷提示回引擎。</span><span class="sxs-lookup"><span data-stu-id="31d01-136">The results of the query are asserted back into the engine as data rows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31d01-137">使用 **OleDbConnection** 中 **DataConnection** 目前不支援。</span><span class="sxs-lookup"><span data-stu-id="31d01-137">The use of an **OleDbConnection** in a **DataConnection** is not currently supported.</span></span>  
  
 <span data-ttu-id="31d01-138">當您選取資料庫資料表/資料行在規則條件或動作中使用時，您可以選擇繫結物件使用 **DataConnection** 或 **TypedDataTable** 藉由選取 [資料連線] 或 [資料庫資料表/資料列 」 從 **資料庫繫結型別**下拉式清單方塊中的 [屬性] 視窗 **資料庫** 事實總管] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="31d01-138">When you select a database table/column to use in a rule condition or action, you can choose to bind to the object using either **DataConnection** or **TypedDataTable** by selecting "Data connection" or "Database table/row" from the **Database binding type**drop-down box in the Property Window for the **Databases** tab of Fact Explorer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31d01-139">預設會使用 DataConnection 繫結。</span><span class="sxs-lookup"><span data-stu-id="31d01-139">The DataConnection binding is used by default.</span></span>  
  
## <a name="typeddatatable"></a><span data-ttu-id="31d01-140">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="31d01-140">TypedDataTable</span></span>  
 <span data-ttu-id="31d01-141">您可以判斷提示 ADO.NET **DataTable** 成為引擎，但此物件會被視為任何其他.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="31d01-141">You can assert an ADO.NET **DataTable** object into the engine, but it will be treated like any other .NET object.</span></span> <span data-ttu-id="31d01-142">在大部分情況下您改為想要判斷提示規則引擎類別 **TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="31d01-142">In most cases you will instead want to assert the rule engine class **TypedDataTable**.</span></span>  
  
 <span data-ttu-id="31d01-143">**TypedDataTable** 是包裝函式類別包含 ADO.NET **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="31d01-143">**TypedDataTable** is a wrapper class that contains an ADO.NET **DataTable**.</span></span> <span data-ttu-id="31d01-144">建構函式只接受 **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="31d01-144">The constructor simply takes a **DataTable**.</span></span> <span data-ttu-id="31d01-145">每次使用資料表或資料表資料行做為規則引數時，對個別評估運算式 **TypedDataRow** 包裝函式，而不是針對 **TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="31d01-145">Any time a table or table column is used as a rule argument, the expression is evaluated against the individual **TypedDataRow** wrappers, and not against the **TypedDataTable**.</span></span>  
  
## <a name="typeddatarow"></a><span data-ttu-id="31d01-146">TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="31d01-146">TypedDataRow</span></span>  
 <span data-ttu-id="31d01-147">這是 ADO 的型別的事實包裝函式 **DataRow** 物件。</span><span class="sxs-lookup"><span data-stu-id="31d01-147">This is a typed fact wrapper for an ADO **DataRow** object.</span></span> <span data-ttu-id="31d01-148">將資料表或資料行拖曳至規則引數，在商務規則編輯器會導致對傳回所建立的規則 **TypedDataRow** 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="31d01-148">Dragging a table or column to a rule argument in the Business Rule Composer results in rules built against the returned **TypedDataRow** wrappers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d01-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31d01-149">See Also</span></span>  
 [<span data-ttu-id="31d01-150">事實</span><span class="sxs-lookup"><span data-stu-id="31d01-150">Facts</span></span>](../core/facts.md)