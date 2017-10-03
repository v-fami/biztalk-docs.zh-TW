---
title: "節點屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 366080f0-c21a-467d-8051-fd280264c5c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d41f0f3b0fe0b302a763629b8777669b54f6cc86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="node-properties"></a>節點屬性

## <a name="overview"></a>概觀
在 [BizTalk 編輯器] 中，您可以在 [Visual Studio 屬性] 視窗中檢查和設定節點屬性。 當您在結構描述樹狀結構檢視中選取不同的節點類型時，[屬性] 視窗中會顯示不同的屬性集合。 因為是 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的標準，這些屬性可以依照類別顯示，或依字母順序而不指示其類別的方式顯示。 使用靠近 [屬性] 視窗上方的標準按鈕，以切換此設定。  
  
 節點屬性，特別在不是設定為預設值時，通常都會以 XML 結構描述定義 (XSD) 語言表示為屬性和與對應項目相關聯的屬性值。 例如，當設定的屬性**Min Occurs**和**Max Occurs**屬性，可供數個不同節點型別，所設定的值會用做值**minOccurs**和**maxOccurs**屬性，分別代表節點的項目與相關**Min Occurs**和**最大值發生**設定屬性。  

## <a name="property-types"></a>屬性類型
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發人員參考包含內容的各種節點類型，依照類別和依字母順序參考區段。 以下摘要說明每個節點類型相關聯的屬性：  
  
-   結構描述節點屬性
  
-   記錄節點屬性
  
-   欄位項目節點屬性
  
-   欄位屬性節點屬性
  
-   Sequence 群組節點屬性
  
-   Choice 群組節點屬性 
  
-   All 群組節點屬性
  
-   Attribute 群組節點屬性
  
-   Any 項目節點屬性
  
-   Any 屬性節點屬性
  
-   相等節點屬性
  
-   相等子節點屬性

這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 **節點屬性-字母順序清單**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]包含的所有個別參考主題每個節點的屬性，其中部分適用於各種類型的節點。 個別參考主題的分類是根據它們屬於可適用於所有結構描述類型的基本屬性，還是屬於與結構描述編輯器延伸模組 (如一般檔案延伸模組) 相關聯的特殊屬性。 在這些類別中，這些屬性是依照字母順序列出。  
  
 「BizTalk 編輯器」使用 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗，讓您檢查和設定結構描述樹狀結構中的節點屬性。 本章節描述使用在 [屬性] 視窗中，包括的特殊考量屬性的某些特性**節點名稱**屬性，屬性之間的相依性的說明和資訊的最大長度都允許特定屬性的型別。  
  
 本節的其餘部分提供有關特定和特殊節點屬性的其他資訊，以及一般適用於節點屬性的其他資訊。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [節點名稱屬性](../core/node-name-property.md)  
  
-   [屬性相互依存性](../core/property-interdependencies.md)  
  
-   [其他一般檔案屬性](../core/additional-flat-file-properties.md)