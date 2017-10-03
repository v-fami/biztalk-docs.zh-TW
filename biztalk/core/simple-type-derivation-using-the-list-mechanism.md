---
title: "使用清單機制衍生簡單型別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f3c7b7-7585-4297-9177-2deaef8355f0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aafc6a540e9595f426858bc16fedfb1f8fe0bc8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="simple-type-derivation-using-the-list-mechanism"></a>使用清單機制的簡單型別衍生
當您使用清單機制從現有的簡單型別衍生新的簡單型別時，即是指定此屬性或項目的值做為指定型別之以空格分隔的值清單。 例如，您可以指定屬性或項目值為以空格分隔的整數清單。  
  
 如需使用清單機制衍生新簡單型別的完整資訊，請參閱 W3C 網站。 這個資料庫和其他網站的各種連結，請參閱[在網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。  
  
 若要衍生簡單型別做為該類型的清單，選取 相關**欄位項目**節點或**欄位屬性**節點在結構描述樹狀目錄中，然後在 屬性 視窗中，從下拉式清單選取簡單型別列出**基底資料型別**屬性。 您選取的值，這個屬性，如**Derived By**屬性會自動從其預設值變更為**限制**，做為型別衍生的預設值。 您必須變更**Derived By**屬性從**限制**至**清單**，這會導致**基底資料型別**做為要重新命名屬性**項目類型**屬性 （附帶一提，重新命名的屬性將移至由於屬性的字母順序排序的屬性清單中的不同位置）。  
  
> [!NOTE]
>  您可以一起使用限制及清單機制、使用限制機制來建立具名的簡單型別衍生，接著透過清單機制，使用該衍生項目做為另一個簡單型別衍生中的項目類型。 舉例來說，這種方式所產生的值會受限為以空格分隔的字串清單，而其會隸屬於特定列舉字串集。  
  
> [!CAUTION]
>  使用清單機制來衍生簡單型別，在所選擇的項目類型本身可加入空格 (如字串) 時，就會變得相當複雜。 這是因為清單機制是利用空格來分隔清單中允許類型的值。  
  
 當您第一次變更**欄位項目**節點或**欄位屬性**節點從具有資料類型具有基底資料型別 （因此開始簡單型別衍生的程序），然後設定  **Derived By**屬性**清單**，您可以觀察 XSD 檢視中的對應片段中的下列變更：  
  
-   之前，是使用新插入**欄位項目**節點名為**ZipCodeList**。  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList" type="xs:string" />  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
-   設定之後**基底資料型別**屬性設為 xs: integer，並設定**Derived By**屬性**清單**(其後**基底資料型別**屬性重新命名為**項目類型**屬性)。  
  
    ```  
    <xs:element name="ContainingRecord">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element name="ZipCodeList">  
                    <xs:simpleType>  
               <xs:list itemType="xs:integer" />   
                       </xs:simpleType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
  
    ```  
  
> [!NOTE]
>  在實際的結構描述中，最好是先定義及命名簡單型別衍生的整數，會將整數限制為五位數，然後再衍生**ZipCodeList**自該型別，有效地限制的清單項目具有五位數的整數。  
  
## <a name="see-also"></a>另請參閱  
 [簡單型別衍生](../core/simple-type-derivation.md)