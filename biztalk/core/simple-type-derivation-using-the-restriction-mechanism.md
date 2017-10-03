---
title: "使用限制機制的簡單型別衍生 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ca712e-9563-4917-9bfc-1033a36773e8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dda4b8ad64f1edf262446f1633eda109ba7074ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation-using-the-restriction-mechanism"></a>使用限制機制的簡單型別衍生

## <a name="overview"></a>概觀
當您使用限制機制從現有的簡單型別衍生新簡單型別時，通常會將在該屬性或項目值的執行個體訊息中所允許的值限制為基底簡單型別所允許的值之子集。 例如，您可以限制字串類型為數個列舉字串的其中一個。  
  
 如需有關使用限制機制來衍生新簡單型別的完整資訊，請參閱 W3C 網站。 如需各種與其他網站連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。  
  
## <a name="field-element-and-field-attribute"></a>欄位項目及欄位屬性
 若要藉由限制衍生簡單類型，選取 相關**欄位項目**節點或**欄位屬性**節點在結構描述樹狀目錄中，然後在 屬性 視窗中，從下拉式清單選取簡單型別列出**基底資料型別**屬性。 您已選取值，這個屬性，如**Derived By**屬性會自動從其預設值變更為**限制**，做為型別衍生的預設值。 此外，整個新類別的屬性，稱為**限制**，在 [屬性] 視窗中變成可用。  
  
 依照您選取的不同基底資料型別，您可以在此新類別中設定不同的屬性。 比方說，如果基底資料類型是數值，屬性**MaxFacet Type** (當**MaxFacet Value**設定)， **MaxFacet Value**， **MinFacet Type**(當**MinFacet Value**設定)，和**MinFacet Value**可用來定義允許的值內含或排除範圍。 如果基底資料類型是字串類型，**長度**，**最大長度**，和**最小長度**屬性可供條件約束字串的長度。  
  
 如需有關欄位節點的各種限制屬性的詳細資訊，請參閱**欄位項目節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 當您第一次變更**欄位項目**節點或**欄位屬性**節點從具有資料類型具有基底資料型別 （因此開始簡單型別衍生的程序），將保留**衍生的**屬性設定為**限制**，而且提供列舉型別為根據的限制的允許的字串值，您可以觀察 XSD 檢視中的對應片段中的下列變更：  
  
-   之前，是使用新插入**欄位項目**節點名為**WestCoastStates**。  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
-   設定之後**基底資料型別**屬性設為"xs: string"，並保留衍生預設值是**限制**如**Derived By**屬性。  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates" >  
                    <xs:simpleType>  
                        <xs:restriction base="xs:string" />  
                    </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
-   設定之後**列舉**美國大陸西岸三種狀態的名稱將限制類別中的屬性。  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="WestCoastStates">  
                    <xs:simpleType>  
                        <xs:restriction base="xs:string" />  
                            <xs:enumeration value="Washington" />  
                            <xs:enumeration value="Oregon" />  
                            <xs:enumeration value="California" />  
                        </xs:restriction>  
                    </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [簡單型別衍生](../core/simple-type-derivation.md)