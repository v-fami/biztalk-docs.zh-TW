---
title: 使用聯集機制的簡單型別衍生 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e51ae390-78f5-4fb9-9163-2a8023aea1ec
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1414fa506f824415de8e8449e8b2b27befd2fc76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270374"
---
# <a name="simple-type-derivation-using-the-union-mechanism"></a>使用聯集機制的簡單型別衍生
當您使用聯集機制從現有簡單型別衍生新的簡單型別時，是根據您指定的型別清單指定此屬性或項目的值可為一個以上的型別。 例如，您可以指定屬性或項目值為 [日期]、[時間] 或 [日期/時間] 值。  
  
 如需有關使用聯集機制來衍生新簡單型別的完整資訊，請參閱 W3C 網站。 如需各種與其他網站連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。  
  
 若要衍生簡單型別於數個可能的類型聯集，選取 相關**欄位項目**節點或**欄位屬性**節點在結構描述樹狀目錄中，然後在 屬性 視窗中選取簡單型別從下拉式清單，如**基底資料型別**屬性。 您已選取值，這個屬性，如**Derived By**屬性會自動從其預設值變更為**限制**，做為型別衍生的預設值。 您必須變更**Derived By**屬性從**限制**至**Union**，這會導致**基底資料型別**屬性來重新命名為**成員型別**屬性 （附帶一提，重新命名的屬性將移至由於屬性的字母順序排序的屬性清單中的不同位置）。  
  
 最後，您可以使用中的核取方塊**成員型別**下拉式檢查清單來選取其他的型別，以供執行個體訊息中對應值。  
  
 當您第一次變更**欄位項目**節點或**欄位屬性**節點從具有資料類型具有基底資料型別 （因此開始簡單型別衍生的程序），然後設定  **Derived By**屬性**Union**，您可以觀察下列變更 XSD 檢視中的對應片段中。  
  
-   之前，是使用新插入**欄位項目**節點名為**DatesAndOrTimes**。  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   設定之後**基底資料型別**屬性**xs: date**，和設定**Derived By**屬性**聯集**(其後**基底資料型別**屬性重新命名為**成員型別**屬性)，然後也選取**xs: datetime**和**xs: time**為其他允許的類型中的**成員型別**下拉式檢查清單。  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [簡單型別衍生](../core/simple-type-derivation.md)