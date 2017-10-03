---
title: "判斷提示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Assert function [Business Rules Engine], .NET objects
- Assert function [Business Rules Engine], TypedXMLDocument
- Assert function [Business Rules Engine]
- Assert function [Business Rules Engine], examples
- Assert function [Business Rules Engine], TypedData table
- Assert function [Business Rules Engine], DataConnection
- .NET objects
ms.assetid: e9989214-3c10-4691-9c38-f6fe64e511ed
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2de66aab5cde0a9515f41713d3390632180fbff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="assert"></a><span data-ttu-id="475ec-102">判斷提示</span><span class="sxs-lookup"><span data-stu-id="475ec-102">Assert</span></span>
<span data-ttu-id="475ec-103">*判斷提示*會新增至商務規則引擎工作記憶體的物件執行個體的程序。</span><span class="sxs-lookup"><span data-stu-id="475ec-103">*Assertion* is the process of adding object instances into the Business Rule engine's working memory.</span></span> <span data-ttu-id="475ec-104">引擎會根據針對執行個體類型所寫入的條件與動作，使用相符-衝突解析-動作階段來處理每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="475ec-104">The engine processes each instance according to the conditions and actions that are written against the type of the instance, using the match-conflict resolution-action phases.</span></span>  
  
 <span data-ttu-id="475ec-105">下列主題將描述使用所產生的行為**Assert**函式，針對不同事實類型。</span><span class="sxs-lookup"><span data-stu-id="475ec-105">The following topics describe behaviors that result from using the **Assert** function for different fact types.</span></span>  
  
## <a name="net-objects"></a><span data-ttu-id="475ec-106">.NET 物件</span><span class="sxs-lookup"><span data-stu-id="475ec-106">.NET Objects</span></span>  
 <span data-ttu-id="475ec-107">每個物件都會判斷提示到工作記憶體中，以做為個別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="475ec-107">Each object is asserted into the working memory as a separate instance.</span></span> <span data-ttu-id="475ec-108">這表示執行個體是由參考物件類型 (例如，IF Object.Property = 1) 之每個述詞所分析的。</span><span class="sxs-lookup"><span data-stu-id="475ec-108">This means that the instance is analyzed by each predicate that references the object's type (for example, IF Object.Property = 1).</span></span> <span data-ttu-id="475ec-109">這也可以讓參考類型的規則動作使用，依照規則條件的結果而定。</span><span class="sxs-lookup"><span data-stu-id="475ec-109">It is also made available to rule actions that reference the type, dependent on the results of the rule conditions.</span></span>  
  
 <span data-ttu-id="475ec-110">請設想下列範例。</span><span class="sxs-lookup"><span data-stu-id="475ec-110">Consider the following example.</span></span>  
  
 <span data-ttu-id="475ec-111">**規則 1**</span><span class="sxs-lookup"><span data-stu-id="475ec-111">**Rule 1**</span></span>  
  
```  
IF A.Value = 1  
THEN A.Status = "good"  
```  
  
 <span data-ttu-id="475ec-112">**規則 2**</span><span class="sxs-lookup"><span data-stu-id="475ec-112">**Rule 2**</span></span>  
  
```  
IF B.Value = 1  
THEN A.Status = "good"  
```  
  
 <span data-ttu-id="475ec-113">在規則 1 中，只有這些執行個體 A 的值為 1 會有其**狀態**更新的屬性。</span><span class="sxs-lookup"><span data-stu-id="475ec-113">In Rule 1, only those instances of A that have a Value of 1 will have their **Status** property updated.</span></span> <span data-ttu-id="475ec-114">在規則 2，不過，如果條件評估為**true**，所有執行個體將會更新其狀態。</span><span class="sxs-lookup"><span data-stu-id="475ec-114">In Rule 2, however, if the condition evaluates to **true**, all instances of A will have their status updated.</span></span> <span data-ttu-id="475ec-115">事實上，如果有多個執行個體 B，A 執行個體將會更新每一次條件評估為**true** B 執行個體。</span><span class="sxs-lookup"><span data-stu-id="475ec-115">In fact, if there are multiple instances of B, the A instances will be updated each time the condition evaluates to **true** for a B instance.</span></span>  
  
 <span data-ttu-id="475ec-116">若要判斷提示.NET 物件從規則中的，您可以加入內建**Assert**函式做為規則動作。</span><span class="sxs-lookup"><span data-stu-id="475ec-116">To assert a .NET object from within a rule, you can add the built-in **Assert** function as a rule action.</span></span> <span data-ttu-id="475ec-117">請注意，規則引擎有**CreateObject**函式，但它不會顯示為 「 商務規則編輯器 」 中的個別函式。</span><span class="sxs-lookup"><span data-stu-id="475ec-117">Note that the rule engine has a **CreateObject** function, but it is not displayed as a separate function in the Business Rule Composer.</span></span> <span data-ttu-id="475ec-118">建置其叫用的方式，是將您想要建立的物件建構函式方法，從 [事實總管] 之 [.NET 類別] 檢視拖曳到動作窗格中。</span><span class="sxs-lookup"><span data-stu-id="475ec-118">Its invocation is built by dragging the constructor method of the object you wish to create from the .NET Class view of the Facts Explorer to the action pane.</span></span> <span data-ttu-id="475ec-119">商務規則編輯器然後將轉譯成建構函式方法**CreateObject**呼叫中的規則定義。</span><span class="sxs-lookup"><span data-stu-id="475ec-119">The Business Rule Composer then translates the constructor method into a **CreateObject** call in the rule definition.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="475ec-120">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="475ec-120">TypedXmlDocument</span></span>  
 <span data-ttu-id="475ec-121">當**TypedXmlDocument**經判斷提示，「 商務規則引擎會建立子**TypedXmlDocument**執行個體根據規則中定義的選取器。</span><span class="sxs-lookup"><span data-stu-id="475ec-121">When a **TypedXmlDocument** is asserted, the Business Rule Engine creates child **TypedXmlDocument** instances based on the selectors defined in the rule.</span></span>  
  
 <span data-ttu-id="475ec-122">選取器和欄位都是 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="475ec-122">Selectors and fields are both XPath expressions.</span></span> <span data-ttu-id="475ec-123">您可以將選取器視為隔離 XML 文件節點的方法，並將欄位當成在選取器中識別特定項目的方法。</span><span class="sxs-lookup"><span data-stu-id="475ec-123">You can think of selectors as a way to isolate nodes of an XML document, and fields as identifying specific items within the selector.</span></span> <span data-ttu-id="475ec-124">引擎會將一個選取器中的所有欄位群組在一起，以做為一個物件。</span><span class="sxs-lookup"><span data-stu-id="475ec-124">All the fields inside one selector are grouped together as an object by the engine.</span></span> <span data-ttu-id="475ec-125">當您選取的節點下**XML 結構描述**] 索引標籤 [事實總管]，[商務規則編輯器中的自動填入**XPath 選取器**屬性的所有節點，而**XPath 欄位**不包含子節點的任何節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="475ec-125">When you select a node under the **XML Schemas** tab in the Facts Explorer, the Business Rule Composer automatically fills in the **XPath Selector** property for all nodes, and the **XPath Field** property for any node that does not contain child nodes.</span></span> <span data-ttu-id="475ec-126">或者，您可以輸入自己的 XPath 運算式為**XPath 選取器**和**XPath 欄位**如有必要。</span><span class="sxs-lookup"><span data-stu-id="475ec-126">Alternatively, you can enter your own XPath expressions for **XPath Selector** and **XPath Field** if necessary.</span></span>  
  
 <span data-ttu-id="475ec-127">若選取器符合 XML 文件的多個部分，則這個類型的多個物件會判斷提示到規則引擎工作記憶體，或從中撤回。</span><span class="sxs-lookup"><span data-stu-id="475ec-127">If the selector matches multiple portions of the XML document, multiple objects of this type are asserted into or retracted from the rule engine working memory.</span></span> <span data-ttu-id="475ec-128">假設您有下列的 XML。</span><span class="sxs-lookup"><span data-stu-id="475ec-128">Assume you have the following XML.</span></span>  
  
```  
<root>  
   <order customer="Joe">  
      <item name="router" quantity="10" cost="550" />  
      <item name="switch" quantity="3" cost="300" />  
   </order>  
   <order customer="Jane">  
      <item name="switch" quantity="1" cost="300" />  
      <item name="cable" quantity="23" cost="9.99" />  
   </order>  
</root>  
```  
  
 <span data-ttu-id="475ec-129">若您使用選取器 /root/order (或 //order)，則會在工作記憶體中加入兩個物件。</span><span class="sxs-lookup"><span data-stu-id="475ec-129">If you use the selector /root/order (or //order), two objects are added to the working memory.</span></span>  
  
 <span data-ttu-id="475ec-130">1\)</span><span class="sxs-lookup"><span data-stu-id="475ec-130">1\)</span></span>  
  
```  
<order customer="Joe">  
   <item name="router" quantity="10" cost="550" />  
   <item name="switch" quantity="3" cost="300" />  
</order>  
```  
  
 <span data-ttu-id="475ec-131">2\)</span><span class="sxs-lookup"><span data-stu-id="475ec-131">2\)</span></span>  
  
```  
<order customer="Jane">  
   <item name="switch" quantity="1" cost="300" />  
   <item name="cable" quantity="23" cost="9.99" />  
</order>  
```  
  
 <span data-ttu-id="475ec-132">在每個選取器中，XPaths 會參考個別的欄位。</span><span class="sxs-lookup"><span data-stu-id="475ec-132">Within each selector, the individual fields are referred to by XPaths.</span></span>  
  
 <span data-ttu-id="475ec-133">若您使用選取器 /root/order/item (或 (//order/item 或 //item)，則會在規則引擎工作記憶體中加入四個物件，其中兩個項目是 Joe 的，兩個項目是 Jane 的。</span><span class="sxs-lookup"><span data-stu-id="475ec-133">If you use the selector /root/order/item (or (//order/item or //item), four objects  are added to the rule engine working memory, the two items for Joe and the two items for Jane.</span></span>  
  
```  
<root>  
   <order customer="Joe">  
  
   </order>  
   <order customer="Jane">  
  
   </order>  
</root>  
```  
  
 <span data-ttu-id="475ec-134">每個物件都可存取三個欄位 —@name， @quantity，和@cost。</span><span class="sxs-lookup"><span data-stu-id="475ec-134">Each object has access to three fields—@name, @quantity, and @cost.</span></span> <span data-ttu-id="475ec-135">因為物件是原始文件的參考，您可以參考父欄位 (例如，"../@customer")。</span><span class="sxs-lookup"><span data-stu-id="475ec-135">Because the object is a reference into the original document, you can refer to parent fields (for example, "../@customer").</span></span>  
  
 <span data-ttu-id="475ec-136">您可以在相同文件中使用多個選取器。</span><span class="sxs-lookup"><span data-stu-id="475ec-136">You can use multiple selectors within the same document.</span></span> <span data-ttu-id="475ec-137">這可讓您檢視文件的不同部分 (例如，若一個區段是訂單，而另一個區段包含送貨地址)。</span><span class="sxs-lookup"><span data-stu-id="475ec-137">This enables you to view different parts of the document (for example, if one section is the order and another section contains the shipping address).</span></span> <span data-ttu-id="475ec-138">不過，請記住，建立的物件是由建立它們的 XPath 字串所定義。</span><span class="sxs-lookup"><span data-stu-id="475ec-138">However, keep in mind that the objects that are created are defined by the XPath string that created them.</span></span> <span data-ttu-id="475ec-139">使用不同的 XPath 運算式，即使它解析成相同的節點，產生唯一**TypedXmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="475ec-139">Using a different XPath expression, even if it resolves to the same node, results in a unique **TypedXmlDocument**.</span></span>  
  
 <span data-ttu-id="475ec-140">規則引擎本質上支援基本的 .NET 純量類型，以及參照類型的物件。</span><span class="sxs-lookup"><span data-stu-id="475ec-140">The rule engine supports basic .NET scalar types natively, as well as objects for reference types.</span></span> <span data-ttu-id="475ec-141">XML 文件基本上是文字，但根據建立規則時所指定的類型，欄位值可能是任何類型。</span><span class="sxs-lookup"><span data-stu-id="475ec-141">XML documents are basically text, but based on the type that was specified when the rule was built, the field value may be of any type.</span></span> <span data-ttu-id="475ec-142">此外，因為欄位是 XPath 運算式，它們可能會傳回節點集，在此情況下，此集中的第一個項目會當成值來使用。</span><span class="sxs-lookup"><span data-stu-id="475ec-142">Also, because fields are XPath expressions, they may return a nodeset, in which case the first item in the set is used as the value.</span></span>  
  
 <span data-ttu-id="475ec-143">在幕後，規則引擎可以文字欄位將值轉換成任何一種支援的型別，透過**XmlConvert**函式。</span><span class="sxs-lookup"><span data-stu-id="475ec-143">Behind the scenes, the rule engine can convert a text field value to any one of the supported types through the **XmlConvert** function.</span></span> <span data-ttu-id="475ec-144">您可以藉由在「商務規則編輯器」中設定類型來加以指定。</span><span class="sxs-lookup"><span data-stu-id="475ec-144">You can specify this by setting the type in the Business Rule Composer.</span></span> <span data-ttu-id="475ec-145">若無法轉換，則會擲出一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="475ec-145">An exception is thrown if a conversion is not possible.</span></span> <span data-ttu-id="475ec-146">型別**bool**和**double**可以擷取只做為其個別的型別、 字串或物件。</span><span class="sxs-lookup"><span data-stu-id="475ec-146">The types **bool** and **double** can be retrieved only as their respective type, strings, or objects.</span></span>  
  
## <a name="typeddatatable"></a><span data-ttu-id="475ec-147">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="475ec-147">TypedDataTable</span></span>  
 <span data-ttu-id="475ec-148">當**TypedDataTable**經判斷提示，所有**Datarow**中包含**DataTable**自動判斷提示到引擎，作為**TypedDataRows**.</span><span class="sxs-lookup"><span data-stu-id="475ec-148">When a **TypedDataTable** is asserted, all **DataRows** contained in the **DataTable** are automatically asserted into the engine as **TypedDataRows**.</span></span> <span data-ttu-id="475ec-149">每次使用資料表或資料表資料行做為規則引數時，會評估運算式，對個別**TypedDataRows**，而不是針對**TypedDataTable**。</span><span class="sxs-lookup"><span data-stu-id="475ec-149">Any time a table or table column is used as a rule argument, the expression is evaluated against the individual **TypedDataRows**, and not against the **TypedDataTable**.</span></span>  
  
 <span data-ttu-id="475ec-150">例如，假設您為「客戶」資料表建立了下列規則：</span><span class="sxs-lookup"><span data-stu-id="475ec-150">For example, suppose that you have the following rule built against a "Customers" table:</span></span>  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
> [!NOTE]
>  <span data-ttu-id="475ec-151">若要建置規則所依據的資料庫資料表，您必須使用**資料表 / 資料列**做為資料庫繫結類型。</span><span class="sxs-lookup"><span data-stu-id="475ec-151">To build a rule against a database table, you must use **Data table / row** as the database binding type.</span></span>  
  
 <span data-ttu-id="475ec-152">假設您判斷提示下列**DataTable**三個**Datarow**到引擎 (做為**TypedDataTable**)。</span><span class="sxs-lookup"><span data-stu-id="475ec-152">Suppose that you assert the following **DataTable** with three **DataRows** into the engine (as a **TypedDataTable**).</span></span>  
  
|<span data-ttu-id="475ec-153">CustomerID</span><span class="sxs-lookup"><span data-stu-id="475ec-153">CustomerID</span></span>|<span data-ttu-id="475ec-154">ContactTitle</span><span class="sxs-lookup"><span data-stu-id="475ec-154">ContactTitle</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="475ec-155">001</span><span class="sxs-lookup"><span data-stu-id="475ec-155">001</span></span>|<span data-ttu-id="475ec-156">供應職員</span><span class="sxs-lookup"><span data-stu-id="475ec-156">Supply Clerk</span></span>|  
|<span data-ttu-id="475ec-157">002</span><span class="sxs-lookup"><span data-stu-id="475ec-157">002</span></span>|<span data-ttu-id="475ec-158">供應職員</span><span class="sxs-lookup"><span data-stu-id="475ec-158">Supply Clerk</span></span>|  
|<span data-ttu-id="475ec-159">003</span><span class="sxs-lookup"><span data-stu-id="475ec-159">003</span></span>|<span data-ttu-id="475ec-160">供應職員</span><span class="sxs-lookup"><span data-stu-id="475ec-160">Supply Clerk</span></span>|  
  
 <span data-ttu-id="475ec-161">引擎插入三個**TypedDataRows**: 001、 002 及 003。</span><span class="sxs-lookup"><span data-stu-id="475ec-161">The engine inserts three **TypedDataRows**: 001, 002, and 003.</span></span>  
  
 <span data-ttu-id="475ec-162">每個**TypedDataRow**依規則獨立進行評估。</span><span class="sxs-lookup"><span data-stu-id="475ec-162">Each **TypedDataRow** is evaluated independently against the rule.</span></span> <span data-ttu-id="475ec-163">第一個**TypedDataRow**符合規則條件和其次的兩個失敗。</span><span class="sxs-lookup"><span data-stu-id="475ec-163">The first **TypedDataRow** meets the rule condition and the second two fail.</span></span> <span data-ttu-id="475ec-164">結果如下所示。</span><span class="sxs-lookup"><span data-stu-id="475ec-164">The results appear as follows.</span></span>  
  
|<span data-ttu-id="475ec-165">CustomerID</span><span class="sxs-lookup"><span data-stu-id="475ec-165">CustomerID</span></span>|<span data-ttu-id="475ec-166">ContactTitle</span><span class="sxs-lookup"><span data-stu-id="475ec-166">ContactTitle</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="475ec-167">001</span><span class="sxs-lookup"><span data-stu-id="475ec-167">001</span></span>|<span data-ttu-id="475ec-168">採購經理</span><span class="sxs-lookup"><span data-stu-id="475ec-168">Purchasing Manager</span></span>|  
|<span data-ttu-id="475ec-169">002</span><span class="sxs-lookup"><span data-stu-id="475ec-169">002</span></span>|<span data-ttu-id="475ec-170">供應職員</span><span class="sxs-lookup"><span data-stu-id="475ec-170">Supply Clerk</span></span>|  
|<span data-ttu-id="475ec-171">003</span><span class="sxs-lookup"><span data-stu-id="475ec-171">003</span></span>|<span data-ttu-id="475ec-172">供應職員</span><span class="sxs-lookup"><span data-stu-id="475ec-172">Supply Clerk</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="475ec-173">TypedDataRows 也可以直接判斷提示到引擎。</span><span class="sxs-lookup"><span data-stu-id="475ec-173">TypedDataRows can also be directly asserted into the engine.</span></span> <span data-ttu-id="475ec-174">會以稍早所述的相同方式來處理這些項目。</span><span class="sxs-lookup"><span data-stu-id="475ec-174">These are processed in the same way as described earlier.</span></span>  
  
 <span data-ttu-id="475ec-175">**DataSetName.DataTableName**會被視為唯一的識別項。</span><span class="sxs-lookup"><span data-stu-id="475ec-175">The **DataSetName.DataTableName** is considered to be a unique identifier.</span></span> <span data-ttu-id="475ec-176">因此，如果第二個**TypedDataTable**判斷提示具有相同**資料集**名稱和**DataTable**名稱，它會取代第一個**TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="475ec-176">Therefore, if a second **TypedDataTable** is asserted with the same **DataSet** name and **DataTable** name, it supersedes the first **TypedDataTable**.</span></span> <span data-ttu-id="475ec-177">所有**TypedDataRow**相關聯的第一個**TypedDataTable**會撤回，而第二個**TypedDataTable**判斷提示。</span><span class="sxs-lookup"><span data-stu-id="475ec-177">All **TypedDataRow**s associated with the first **TypedDataTable** are retracted, and the second **TypedDataTable** is asserted.</span></span>  
  
## <a name="dataconnection"></a><span data-ttu-id="475ec-178">DataConnection</span><span class="sxs-lookup"><span data-stu-id="475ec-178">DataConnection</span></span>  
 <span data-ttu-id="475ec-179">如同**TypedDataTable**，拖曳資料表或資料行做為規則引數，在商務規則編輯器會針對傳回所建立的規則導致**TypedDataRow**相反**DataConnection**本身。</span><span class="sxs-lookup"><span data-stu-id="475ec-179">As with a **TypedDataTable**, dragging a table or column as a rule argument in the Business Rule Composer results in rules built against the returned **TypedDataRow**s as opposed to the **DataConnection** itself.</span></span>  
  
 <span data-ttu-id="475ec-180">假設已建立下列規則和**DataConnection**判斷提示，其中包含**SqlConnection**到 Northwind.Customers:</span><span class="sxs-lookup"><span data-stu-id="475ec-180">Suppose that the following rule is created and a **DataConnection** is asserted that contains a **SqlConnection** to Northwind.Customers:</span></span>  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
 <span data-ttu-id="475ec-181">當引擎評估中所使用的規則**TypedDataTable**  區段中，它會動態建立查詢所示：</span><span class="sxs-lookup"><span data-stu-id="475ec-181">When the engine evaluates the rule used in the **TypedDataTable** section, it dynamically builds a query that looks like:</span></span>  
  
```  
SELECT *  
FROM Northwind.Customers  
WHERE CustomerID = 1  
```  
  
 <span data-ttu-id="475ec-182">因為在資料庫中的只有一個資料列符合這個準則，只有一個**TypedDataRow**建立和判斷提示到引擎以便進一步處理。</span><span class="sxs-lookup"><span data-stu-id="475ec-182">Because only one row in the database meets this criterion, only one **TypedDataRow** is created and asserted into the engine for further processing.</span></span>  
  
## <a name="summary-of-asserted-entities-and-instance-types"></a><span data-ttu-id="475ec-183">判斷提示實體和執行個體型別的摘要</span><span class="sxs-lookup"><span data-stu-id="475ec-183">Summary of Asserted Entities and Instance Types</span></span>  
 <span data-ttu-id="475ec-184">下表概述各種型別的判斷提示行為、顯示在引擎中對每個判斷提示實體建立的結果執行個體數目，以及套用至那些執行個體以識別它們的型別。</span><span class="sxs-lookup"><span data-stu-id="475ec-184">The following table summarizes the assert behavior for the various types, showing the number of resulting instances created in the engine for each asserted entity, as well as the type that is applied to each of those instances to identify them.</span></span>  
  
|<span data-ttu-id="475ec-185">實體</span><span class="sxs-lookup"><span data-stu-id="475ec-185">Entity</span></span>|<span data-ttu-id="475ec-186">判斷提示的執行個體數目</span><span class="sxs-lookup"><span data-stu-id="475ec-186">Number of instances asserted</span></span>|<span data-ttu-id="475ec-187">執行個體類型</span><span class="sxs-lookup"><span data-stu-id="475ec-187">Instance type</span></span>|  
|------------|----------------------------------|-------------------|  
|<span data-ttu-id="475ec-188">.NET 物件</span><span class="sxs-lookup"><span data-stu-id="475ec-188">.NET object</span></span>|<span data-ttu-id="475ec-189">1 (物件本身)</span><span class="sxs-lookup"><span data-stu-id="475ec-189">1 (the object itself)</span></span>|<span data-ttu-id="475ec-190">完整格式 .NET 類別</span><span class="sxs-lookup"><span data-stu-id="475ec-190">Fully Qualified .NET Class</span></span>|  
|<span data-ttu-id="475ec-191">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="475ec-191">TypedXmlDocument</span></span>|<span data-ttu-id="475ec-192">1-N TypedXmlDocument：根據已建立的選取器繫結和文件內容</span><span class="sxs-lookup"><span data-stu-id="475ec-192">1-N TypedXmlDocument(s): Based on Selector bindings created and document content</span></span>|<span data-ttu-id="475ec-193">DocumentType.Selector</span><span class="sxs-lookup"><span data-stu-id="475ec-193">DocumentType.Selector</span></span>|  
|<span data-ttu-id="475ec-194">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="475ec-194">TypedDataTable</span></span>|<span data-ttu-id="475ec-195">1-N TypedDataRow：</span><span class="sxs-lookup"><span data-stu-id="475ec-195">1-N TypedDataRow(s):</span></span><br /><br /> <span data-ttu-id="475ec-196">DataTable 中每個 DataRow 都有一個</span><span class="sxs-lookup"><span data-stu-id="475ec-196">One for each DataRow in the DataTable</span></span>|<span data-ttu-id="475ec-197">DataSetName.DataTableName</span><span class="sxs-lookup"><span data-stu-id="475ec-197">DataSetName.DataTableName</span></span>|  
|<span data-ttu-id="475ec-198">TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="475ec-198">TypedDataRow</span></span>|<span data-ttu-id="475ec-199">1 (判斷提示的 TypedDataRow)</span><span class="sxs-lookup"><span data-stu-id="475ec-199">1 (the TypedDataRow asserted)</span></span>|<span data-ttu-id="475ec-200">DataSetName.DataTableName</span><span class="sxs-lookup"><span data-stu-id="475ec-200">DataSetName.DataTableName</span></span>|  
|<span data-ttu-id="475ec-201">DataConnection</span><span class="sxs-lookup"><span data-stu-id="475ec-201">DataConnection</span></span>|<span data-ttu-id="475ec-202">1-N (由查詢 DataConnection 傳回的每個 TypedDataRow 都有一個)</span><span class="sxs-lookup"><span data-stu-id="475ec-202">1-N (one for each TypedDataRow returned by querying the DataConnection)</span></span>|<span data-ttu-id="475ec-203">DataSetName.DataTableName</span><span class="sxs-lookup"><span data-stu-id="475ec-203">DataSetName.DataTableName</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="475ec-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="475ec-204">See Also</span></span>  
 [<span data-ttu-id="475ec-205">引擎控制函式</span><span class="sxs-lookup"><span data-stu-id="475ec-205">Engine Control Functions</span></span>](../core/engine-control-functions.md)