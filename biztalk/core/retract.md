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
# <a name="retract"></a>撤回
您可以使用**Retract**函式，從 「 商務規則引擎工作記憶體移除物件。 下列幾段描述從規則引擎的工作記憶體撤回不同類型實體的關聯行為。  
  
## <a name="net-objects"></a>.NET 物件  
 .NET 物件是否已收回原則中使用**Retract**函式。 此函式是做為 「 商務規則編輯器 」 中可用**函式**詞彙項目： 將類別 （而非從組件或方法） 拖曳到**Retract**參數。  
  
> [!NOTE]
>  如果您拖曳到方法**Retract**函式，引擎會嘗試撤回該方法所傳回的物件。  
  
 撤回 .NET 物件也會從規則引擎的工作記憶體移除它，並且有下列影響：  
  
-   在述詞中使用物件的規則，具有其已從議程移除的動作 (如果議程上存在任何動作)。  
  
-   會從議程中移除議程上使用物件的動作。  
  
    > [!NOTE]
    >  之前可能已經執行更高層議程上的其他動作**Retract**呼叫函式。  
  
-   物件已不再由引擎所評估。  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 您可以撤回原始**TypedXmlDocument** ，判斷提示到引擎，或是撤回其中一個子系**TypedXmlDocument**從父代的節點建立**XmlDocument**.  
  
 您可以使用下列 XML 做為範例，您可以撤回**TypedXmlDocument**順序或一個或多個相關聯**TypedXmlDocument**與 orderline 關聯。  
  
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
  
 若要撤回 Order 物件，您可以在 XML 描述結構事實窗格中拖曳描述結構的最上方節點。 此節點以".xsd"結束，並代表文件根節點 （不是文件項目節點）。它有"/"選取器，它是指初始**TypedXmlDocument**。 當父**TypedXmlDocument**遭到撤回時，所有**TypedXmlDocument**與相關聯的執行個體**TypedXmlDocument** (所有**TypedXmlDocument**藉由呼叫建立的 s **Assert**函式會根據原則中所使用的選取器) 會從工作記憶體移除。  
  
 若要撤回個別子系**TypedXmlDocument** (其為 orderline)，您可以將此節點從 XML 結構描述窗格，將**Retract**函式。 請務必注意，所有**TypedXmlDocument**s 相關聯的最上層**TypedXmlDocument** ，最初判斷提示，而不是使用**TypedXmlDocument**上方出現在 XML 樹狀結構階層架構中。 例如，產品是**TypedXmlDocument**低於 orderline 物件中; 因此，它會與順序相關聯**TypedXmlDocument**，而不是與 orderline **TypedXmlDocument**。 在大部分的執行個體中，這個差別並不重要。 不過，若您撤回 Order 物件，Orderline 和 Product 物件也會被撤回。 如果您撤回 Orderline 物件，則只有該物件會被撤回，而不會撤回 Product 物件。  
  
 引擎只會使用和追蹤物件的執行個體 (**TypedXmlDocument**s) 時所建立**TypedXmlDocument**最初判斷提示。 如果您建立其他節點 — 比方說，透過原則選取器選取的節點同層級節點，除非這些節點不在規則中評估**TypedXmlDocument**所建立及它們判斷提示。 判斷提示這些新、 較低層級**TypedXmlDocuments**使它們來評估規則，但最上層**TypedXmlDocument**不了解它們。 當最上層**TypedXmlDocument**遭到撤回時，新的且個別判斷提示**TypedXmlDocument**並不會自動撤回。 如此一來，如果建立新的節點，則通常更直接地撤回並重新判斷提示完整**XmlDocument**。  
  
 **TypedXmlDocument**類別支援一些有用的方法，可以在自訂.NET 成員呼叫做為動作的一部分。 這些包括能夠取得**XmlNode**聯**TypedXmlDocument**或父**TypedXmlDocument**。  
  
## <a name="typeddatatable"></a>TypedDataTable  
 您可以撤回個別**TypedDataRow**s 或整個**TypedDataTable**。 如果您撤回資料表，所有包含的資料列也會從工作記憶體中撤回。  
  
 若要撤回整個**TypedDataTable**您要使用的 helper 函式來存取**父**屬性**TypedDataRow**，例如：  
  
```  
Retract(MyHelper.GetTypedDataTable(TypedDataRow))  
```  
  
 在前一個動作中，您會拖曳資料表至**TypedDataRow**。 在**GetTypedDataTable**的值會傳回**TypedDataRow.Parent**。  
  
 如同**TypedXmlDocument**s，如果您判斷提示新增其他**TypedDataRow**同一個 s **DataTable**之後判斷提示**TypedDataTable**，則會視為個別的實體和撤銷**TypedDataTable**不會導致這些撤銷額外**TypedDataRow**s。 只有**TypedDataRow**中所包含的 s **TypedDataTable**當它已判斷提示會撤回。  
  
## <a name="dataconnection"></a>DataConnection  
 當**DataConnection**遭到撤回時，所有**TypedDataRow**擷取從資料庫所建構之查詢透過**DataConnection**會撤回從工作記憶體。 **DataConnection**本身也撤回時，表示無其他**TypedDataRow**s 會透過擷取**DataConnection** （也就是透過使用**DataConnection**其他述詞或動作中)。  
  
 當使用**DataConnection**，針對個別作業的任何撤回**TypedDataRow**引擎進入不一致的狀態。 因此，作業不允許個別**TypedDataRow**與相關聯**DataConnection**。 如果您將資料表拖曳 (使用**DataConnection**參數) 到**Retract**函式，您將會撤回**DataConnection**。  
  
## <a name="see-also"></a>另請參閱  
 [引擎控制函式](../core/engine-control-functions.md)