---
title: "使用複雜全域型別的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddea1c7b-eb0e-4521-8576-0ea6f9460847
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f84b8b872d047a62a913514a695b4bba2d482c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-use-complex-global-types"></a>使用複雜全域型別的方式
在您將複雜型別轉換為全域複雜型別之後，它就可以在結構描述的其他位置中重複使用。 如需有關定義複雜類型，而且再將它轉換成全域複雜類型的詳細資訊，請參閱[複雜全域型別定義和命名](../core/complex-global-type-definition-and-naming.md)。  
  
 首先，插入新**記錄**節點。 接著選取插入的節點，並在 [屬性] 視窗中設定下列兩個節點屬性的其中之一，每個屬性都有不同的效果：  
  
-   **資料結構型別屬性**。 若您想要使用複雜全域型別且完全不修改，請將此屬性設定成您為複雜全域型別指定的型別名稱，它可以在下拉式清單中做為選項使用。 在結構描述樹狀結構中，選擇的全域節點結構將會在新位置中以圖形化的方式複製，而且在結構描述樹狀結構的任何位置中，對節點結構的任何後續變更，會自動套用到使用該複雜全域型別的所有位置。  
  
-   **基底資料型別屬性**。 如果您想要使用複雜全域型別上的一種，將它擴充或限制在某些方面，請您為複雜全域型別，也就是可從下拉式清單中選擇的型別名稱來設定此屬性。 當您設定此屬性， **Derived By**節點屬性變更為**延伸**(和**內容類型**屬性變更為**ComplexContent**)，表示延伸複雜全域型別是預設的衍生類型。 您可以將它變更為**限制**如果您的修改屬於該本質。 在您進行衍生的基底複雜全域型別中的變更，會自動反映在衍生的型別中，但是在衍生型別中的變更永遠不會反映在基底型別中。  
  
> [!NOTE]
>  設定這些屬性的其中一個會自動造成其他屬性移除任何現有的設定。 此外，您會注意到其他的之間的關聯的屬性，例如設定自動互動**Derived By**屬性**（預設）**移除任何現有的設定，從**基底資料型別**屬性。  
  
> [!NOTE]
>  您可以建立測試結構描述並使用這些屬性的不同值，以觀察 XSD 檢視中的變更。  
  
 本節描述如何藉由延伸和限制方式使用複雜全域型別，而這兩種方式都是由本主題中描述的屬性設定來控制。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [複雜全域型別重複使用](../core/complex-global-type-re-use.md)  
  
-   [複雜全域型別衍生](../core/complex-global-type-derivation.md)