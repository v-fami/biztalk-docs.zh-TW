---
title: 判斷提示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2de66aab5cde0a9515f41713d3390632180fbff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234046"
---
# <a name="assert"></a>判斷提示
*判斷提示*會新增至商務規則引擎工作記憶體的物件執行個體的程序。 引擎會根據針對執行個體類型所寫入的條件與動作，使用相符-衝突解析-動作階段來處理每個執行個體。  
  
 下列主題將描述使用所產生的行為**Assert**函式，針對不同事實類型。  
  
## <a name="net-objects"></a>.NET 物件  
 每個物件都會判斷提示到工作記憶體中，以做為個別的執行個體。 這表示執行個體是由參考物件類型 (例如，IF Object.Property = 1) 之每個述詞所分析的。 這也可以讓參考類型的規則動作使用，依照規則條件的結果而定。  
  
 請設想下列範例。  
  
 **規則 1**  
  
```  
IF A.Value = 1  
THEN A.Status = "good"  
```  
  
 **規則 2**  
  
```  
IF B.Value = 1  
THEN A.Status = "good"  
```  
  
 在規則 1 中，只有這些執行個體 A 的值為 1 會有其**狀態**更新的屬性。 在規則 2，不過，如果條件評估為**true**，所有執行個體將會更新其狀態。 事實上，如果有多個執行個體 B，A 執行個體將會更新每一次條件評估為**true** B 執行個體。  
  
 若要判斷提示.NET 物件從規則中的，您可以加入內建**Assert**函式做為規則動作。 請注意，規則引擎有**CreateObject**函式，但它不會顯示為 「 商務規則編輯器 」 中的個別函式。 建置其叫用的方式，是將您想要建立的物件建構函式方法，從 [事實總管] 之 [.NET 類別] 檢視拖曳到動作窗格中。 商務規則編輯器然後將轉譯成建構函式方法**CreateObject**呼叫中的規則定義。  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 當**TypedXmlDocument**經判斷提示，「 商務規則引擎會建立子**TypedXmlDocument**執行個體根據規則中定義的選取器。  
  
 選取器和欄位都是 XPath 運算式。 您可以將選取器視為隔離 XML 文件節點的方法，並將欄位當成在選取器中識別特定項目的方法。 引擎會將一個選取器中的所有欄位群組在一起，以做為一個物件。 當您選取的節點下**XML 結構描述**] 索引標籤 [事實總管]，[商務規則編輯器中的自動填入**XPath 選取器**屬性的所有節點，而**XPath 欄位**不包含子節點的任何節點的屬性。 或者，您可以輸入自己的 XPath 運算式為**XPath 選取器**和**XPath 欄位**如有必要。  
  
 若選取器符合 XML 文件的多個部分，則這個類型的多個物件會判斷提示到規則引擎工作記憶體，或從中撤回。 假設您有下列的 XML。  
  
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
  
 若您使用選取器 /root/order (或 //order)，則會在工作記憶體中加入兩個物件。  
  
 1\)  
  
```  
<order customer="Joe">  
   <item name="router" quantity="10" cost="550" />  
   <item name="switch" quantity="3" cost="300" />  
</order>  
```  
  
 2\)  
  
```  
<order customer="Jane">  
   <item name="switch" quantity="1" cost="300" />  
   <item name="cable" quantity="23" cost="9.99" />  
</order>  
```  
  
 在每個選取器中，XPaths 會參考個別的欄位。  
  
 若您使用選取器 /root/order/item (或 (//order/item 或 //item)，則會在規則引擎工作記憶體中加入四個物件，其中兩個項目是 Joe 的，兩個項目是 Jane 的。  
  
```  
<root>  
   <order customer="Joe">  
  
   </order>  
   <order customer="Jane">  
  
   </order>  
</root>  
```  
  
 每個物件都可存取三個欄位 —@name， @quantity，和@cost。 因為物件是原始文件的參考，您可以參考父欄位 (例如，"../@customer")。  
  
 您可以在相同文件中使用多個選取器。 這可讓您檢視文件的不同部分 (例如，若一個區段是訂單，而另一個區段包含送貨地址)。 不過，請記住，建立的物件是由建立它們的 XPath 字串所定義。 使用不同的 XPath 運算式，即使它解析成相同的節點，產生唯一**TypedXmlDocument**。  
  
 規則引擎本質上支援基本的 .NET 純量類型，以及參照類型的物件。 XML 文件基本上是文字，但根據建立規則時所指定的類型，欄位值可能是任何類型。 此外，因為欄位是 XPath 運算式，它們可能會傳回節點集，在此情況下，此集中的第一個項目會當成值來使用。  
  
 在幕後，規則引擎可以文字欄位將值轉換成任何一種支援的型別，透過**XmlConvert**函式。 您可以藉由在「商務規則編輯器」中設定類型來加以指定。 若無法轉換，則會擲出一個例外狀況。 型別**bool**和**double**可以擷取只做為其個別的型別、 字串或物件。  
  
## <a name="typeddatatable"></a>TypedDataTable  
 當**TypedDataTable**經判斷提示，所有**Datarow**中包含**DataTable**自動判斷提示到引擎，作為**TypedDataRows**. 每次使用資料表或資料表資料行做為規則引數時，會評估運算式，對個別**TypedDataRows**，而不是針對**TypedDataTable**。  
  
 例如，假設您為「客戶」資料表建立了下列規則：  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
> [!NOTE]
>  若要建置規則所依據的資料庫資料表，您必須使用**資料表 / 資料列**做為資料庫繫結類型。  
  
 假設您判斷提示下列**DataTable**三個**Datarow**到引擎 (做為**TypedDataTable**)。  
  
|CustomerID|ContactTitle|  
|----------------|------------------|  
|001|供應職員|  
|002|供應職員|  
|003|供應職員|  
  
 引擎插入三個**TypedDataRows**: 001、 002 及 003。  
  
 每個**TypedDataRow**依規則獨立進行評估。 第一個**TypedDataRow**符合規則條件和其次的兩個失敗。 結果如下所示。  
  
|CustomerID|ContactTitle|  
|----------------|------------------|  
|001|採購經理|  
|002|供應職員|  
|003|供應職員|  
  
> [!NOTE]
>  TypedDataRows 也可以直接判斷提示到引擎。 會以稍早所述的相同方式來處理這些項目。  
  
 **DataSetName.DataTableName**會被視為唯一的識別項。 因此，如果第二個**TypedDataTable**判斷提示具有相同**資料集**名稱和**DataTable**名稱，它會取代第一個**TypedDataTable**. 所有**TypedDataRow**相關聯的第一個**TypedDataTable**會撤回，而第二個**TypedDataTable**判斷提示。  
  
## <a name="dataconnection"></a>DataConnection  
 如同**TypedDataTable**，拖曳資料表或資料行做為規則引數，在商務規則編輯器會針對傳回所建立的規則導致**TypedDataRow**相反**DataConnection**本身。  
  
 假設已建立下列規則和**DataConnection**判斷提示，其中包含**SqlConnection**到 Northwind.Customers:  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
 當引擎評估中所使用的規則**TypedDataTable**  區段中，它會動態建立查詢所示：  
  
```  
SELECT *  
FROM Northwind.Customers  
WHERE CustomerID = 1  
```  
  
 因為在資料庫中的只有一個資料列符合這個準則，只有一個**TypedDataRow**建立和判斷提示到引擎以便進一步處理。  
  
## <a name="summary-of-asserted-entities-and-instance-types"></a>判斷提示實體和執行個體型別的摘要  
 下表概述各種型別的判斷提示行為、顯示在引擎中對每個判斷提示實體建立的結果執行個體數目，以及套用至那些執行個體以識別它們的型別。  
  
|實體|判斷提示的執行個體數目|執行個體類型|  
|------------|----------------------------------|-------------------|  
|.NET 物件|1 (物件本身)|完整格式 .NET 類別|  
|TypedXmlDocument|1-N TypedXmlDocument：根據已建立的選取器繫結和文件內容|DocumentType.Selector|  
|TypedDataTable|1-N TypedDataRow：<br /><br /> DataTable 中每個 DataRow 都有一個|DataSetName.DataTableName|  
|TypedDataRow|1 (判斷提示的 TypedDataRow)|DataSetName.DataTableName|  
|DataConnection|1-N (由查詢 DataConnection 傳回的每個 TypedDataRow 都有一個)|DataSetName.DataTableName|  
  
## <a name="see-also"></a>另請參閱  
 [引擎控制函式](../core/engine-control-functions.md)