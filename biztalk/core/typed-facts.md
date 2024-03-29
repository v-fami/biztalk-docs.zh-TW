---
title: 型別事實 |Microsoft Docs
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
ms.openlocfilehash: 56fd7d05f6970d8086b9180b0af867c0dcf84119
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000135"
---
# <a name="typed-facts"></a>型別事實
*型別事實*是類別實作**ITypedFact**介面： **TypedXmlDocument**， **DataConnection**， **TypedDataTable**，並**TypedDataRow**。  

## <a name="typedxmldocument"></a>TypedXmlDocument  
 **TypedXmlDocument**類別代表商務規則架構中的 XML 文件類型。 使用 XML 文件的節點做為規則中的引數時，會建立兩個 XPath 運算式：「選取器」和「欄位」繫結。  

 如果節點沒有子節點，*選取器繫結*（也稱為 XmlDocument 繫結） 會建立節點的父節點並*欄位繫結*建立 （也稱為 XmlDocumentMember 繫結）節點本身。 此欄位繫結是相對於選取器繫結。 若該節點有子節點，便會對該節點建立選取器繫結，而不會建立欄位繫結。  

 假設您有下列結構描述。  

 ![在 [事實總管] 中顯示的範例結構描述](../core/media/xmldocumentbrowser.gif "xmldocumentbrowser")  
Case.xsd  

 因為 Income 節點有子節點，所以若選取該節點，只會建立選取器繫結。 中的預設 XPath 運算式**XPath 選取器**的 [屬性] 窗格中的屬性包含：  

```  
/*[local-name()='Root' and namespace-uri()='http://LoansProcessor.Case']/*[local-name()='Income' and namespace-uri()='']  
```  

 但是若選取 Name 節點，則會建立選取器繫結和欄位繫結兩者。 繫結資訊看起來如下。  


|      屬性      |                                    ReplTest1                                    |
|--------------------|-----------------------------------------------------------------------------|
|  **XPath 欄位**   |               \*[local-name = 'Name' and namespace-uri （) = ']                |
| **XPath 選取器** | /\*[local-name = 'Root' and namespace-uri （) ='<http://LoansProcessor.Case>'] |

 在將節點拖曳至規則引數之前，您可以變更 XML 節點的預設 XPath 運算式，在原則中會放置新的繫結資訊。 不過請注意，對 XPath 運算式所做的任何編輯都必須在重新載入結構描述時，於「商務規則編輯器」中重新輸入。  

 為 XML 節點建立詞彙定義時，依據先前描述的規則，繫結的 XPath 運算式會擁有相似的預設值，但您可以在「詞彙定義精靈」中加以編輯。 對運算式所做的變更會放置在詞彙定義中，而且會反映在從定義建置的任何規則引數中。  

## <a name="dataconnection"></a>DataConnection  
 **DataConnection** .NET 類別中提供**RuleEngine**程式庫。 它包含一個.NET **SqlConnection**執行個體並**DataSet**名稱。 **資料集**名稱可讓您建立的唯一識別碼**SqlConnection** ，用於定義結果類型。  

 **DataConnection**類別會提供商務規則引擎的效能最佳化。 而不判斷提示至引擎的非常大型的資料庫資料表 (**TypedDataTable**類別) 可能包含許多的資料庫資料列 (**TypedDataRow**類別) 不相關的原則，您可以判斷提示輕量型**DataConnection**。 當引擎評估原則時，它會動態建立 SELECT 查詢，根據規則述詞/動作和查詢**DataConnection**在執行。 例如，假設您有下列規則：  

```  
IF NorthWind.Products.UnitPrice >= 0   
THEN <do something>  
```  

 該規則會產生下列 SQL 查詢：  

```  
Select * From [Product] Where [UnitPrice] >= 0  
```  

 查詢結果會做為資料列判斷提示回引擎。  

> [!NOTE]
>  善用**OleDbConnection**中**DataConnection**目前不支援。  

 當您選取資料庫資料表/資料行在規則條件或動作中使用時，您可以選擇繫結使用的物件**DataConnection**或是**TypedDataTable**藉由選取 [資料連線 」 或 「資料庫資料表/資料列 」 從**資料庫繫結型別**的 [屬性] 視窗中的下拉式清單方塊**資料庫**事實總管] 索引標籤。  

> [!NOTE]
>  預設會使用 DataConnection 繫結。  

## <a name="typeddatatable"></a>TypedDataTable  
 您可以判斷提示的 ADO.NET **DataTable**到引擎，但此物件會被視為任何其他.NET 物件。 在大部分情況下您改為想要判斷提示規則引擎類別**TypedDataTable**。  

 **TypedDataTable**是包裝函式類別，包含 ADO.NET **DataTable**。 建構函式只會接受**DataTable**。 每次使用資料表或資料表資料行做為規則引數時，會評估運算式，對個別**TypedDataRow**包裝函式，而不是針對**TypedDataTable**。  

## <a name="typeddatarow"></a>TypedDataRow  
 這是 ADO 的型別的事實包裝函式**DataRow**物件。 將資料表或資料行拖曳至規則引數，在 商務規則編輯器會導致對傳回所建立的規則**TypedDataRow**包裝函式。  

## <a name="see-also"></a>另請參閱  
 [事實](../core/facts.md)