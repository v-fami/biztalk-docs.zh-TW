---
title: BizTalk 結構描述表示法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0460a37-1f4f-4c0b-91db-bb457f434fe9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3641e2728c29eaed0733839dcb577ae7f2aad2a9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966532"
---
# <a name="biztalk-representation-of-schemas"></a>BizTalk 結構描述表示法

## <a name="overview"></a>概觀
雖然 BizTalk 結構描述最後是以 XML 結構描述定義 (XSD) 語言來表示和保存，不過，在 BizTalk 編輯器中工作時，會以圖形化的節點階層來表示。 一定是階層的頂層**\<結構描述\>**  節點和剩餘的節點類型用來建置結構描述，使其表示使用 BizTalk 交換的特定訊息。  

## <a name="insert-schema-node-options"></a>插入結構描述節點選項  
 BizTalk 編輯器提供一種方式，讓您不需要學習所有複雜的 XSD 語法就可以建構 XSD 結構描述。 當使用**插入結構描述節點**命令**BizTalk**功能表或快速鍵功能表中要插入的節點的下列選項位於串聯功能表。  
  
|插入結構描述節點功能表選項|Description|  
|------------------------------------|-----------------|  
|**子記錄**|插入**記錄**節點中選取的節點順序的結尾。 如需有關**記錄**節點，請參閱[[記錄] 節點](../core/record-nodes.md)。|  
|**子欄位屬性**|插入**欄位屬性**端的所選節點**記錄**或**屬性群組**節點。 如需有關**欄位屬性**節點，請參閱[欄位屬性節點](../core/field-attribute-nodes.md)。|  
|**子欄位項目**|插入**欄位項目**選取的節點中的節點。 如需有關**欄位項目**節點，請參閱[欄位項目節點](../core/field-element-nodes.md)。|  
|**同層級記錄**|插入**記錄**包含所選取的節點的序列結尾處的節點。 如需有關**記錄**節點，請參閱[[記錄] 節點](../core/record-nodes.md)。|  
|**同層級欄位屬性**|插入**欄位屬性**節點結尾處**記錄**或**屬性群組**包含所選取的節點的節點。 如需有關**欄位屬性**節點，請參閱[欄位屬性節點](../core/field-attribute-nodes.md)。|  
|**同層級欄位項目**|插入**欄位項目**包含所選取的節點的序列結尾處的節點。 如需有關**欄位項目**節點，請參閱[欄位項目節點](../core/field-element-nodes.md)。|  
|**Sequence 群組**|插入**Sequence 群組**節點 (\<順序\>樹狀檢視中) 選取的節點中順序的結尾。 如需有關**Sequence 群組**節點，請參閱[Sequence 群組節點](../core/sequence-group-nodes.md)。|  
|**Choice 群組**|插入**Choice 群組**節點 (\<選擇\>樹狀檢視中) 選取的節點中順序的結尾。 如需有關**Choice 群組**節點，請參閱[Choice 群組節點](../core/choice-group-nodes.md)。|  
|**所有群組**|插入**All 群組**節點 (\<所有\>樹狀檢視中) 的非屬性子節點的**記錄**節點，取代預設使用的**順序**內的項目**記錄**節點與使用**所有**項目。 您可以插入之前**All 群組** 節點，您必須變更**內容類型**屬性包含**記錄**節點**ComplexContent**. 如需有關**All 群組**節點，請參閱[All 群組 節點](../core/all-group-nodes.md)。|  
|**屬性群組**|插入**屬性群組**節點 (\<AttrGroup:attrGroup*N* \>在樹狀結構檢視中，其中*N*是單純遞增的數字) 在所選的結尾**記錄**或**屬性群組**節點。 如需有關**屬性群組**節點，請參閱[屬性群組節點](../core/attribute-group-nodes.md)。|  
|**任何項目**|插入**Any 項目**節點 (**\<** 任何**\>** 樹狀檢視中) 中所選取順序的結尾**記錄**， **sequence 群組**， **Choice 群組**，或**All 群組**節點。 如需有關**Any 項目**節點，請參閱[Any 項目節點](../core/any-element-nodes.md)。|  
|**任何屬性**|插入**Any 屬性**節點 (**\<** AnyAttribute **\>** 樹狀檢視中) 中選取順序的結尾**記錄**或**屬性群組**節點。 如需有關**Any 屬性**節點，請參閱[Any 屬性節點](../core/any-attribute-nodes.md)。|  
  
 在許多情況下，在「BizTalk 編輯器」中新增單一節點會造成在結構描述的對應 XSD 表示法中新增多個巢狀項目。 由於這些巢狀項目有可能包含複雜的語法，因此，使用「BizTalk 編輯器」以圖形方式排列節點是一種比手動編輯 XSD 以建構 XSD 結構描述的方式較少發生錯誤的方法。 另一個要考慮的因素是，若總是使用「BizTalk 編輯器」來建構 XSD 結構描述，則可以讓更多受控制的 XSD 子集使用在結構描述的描述中。  
  
 整體來說，BizTalk 編輯器結合了簡單的方法來建構 XSD 結構描述使用泛型的概念的記錄和欄位與更明確的控制特定 xsd 建構，例如**順序**， **選擇**，**任何**，和**anyattribute**項目。  
  
 每個節點類型都有一組獨特的屬性，這組屬性可以在 [Visual Studio 屬性] 視窗中設定。 一般而言，這些屬性會對應到結構描述之對應 XSD 表示法中的 XSD 項目之屬性。 如需有關節點屬性的詳細資訊，請參閱**節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 本節描述在 BizTalk 編輯器中使用的節點類型，簡短討論其屬性，並提供其屬性的參考資訊連結。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [直接對應到訊息執行個體資料與結構的節點](../core/nodes-that-correspond-directly-to-message-instance-data-and-structure.md)  
  
-   [控制執行個體訊息結構與變化的節點](../core/nodes-that-control-instance-message-structure-and-variations.md)  
  
-   [簡化結構描述建立的節點](../core/nodes-that-simplify-schema-creation.md)  
  
-   [提供萬用字元功能的節點](../core/nodes-that-provide-wildcard-capabilities.md)  
  
-   [節點屬性](../core/node-properties.md)