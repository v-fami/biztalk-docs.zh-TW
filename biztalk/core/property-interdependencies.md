---
title: 屬性相互依存性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ed5b75e-db1c-43d4-a287-fc4cd1c529f5
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15e1a02d82d294c63a33c0682e77585a7934b8ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268454"
---
# <a name="property-interdependencies"></a>屬性相互依存性

## <a name="overview"></a>概觀
當您使用「BizTalk 編輯器」，尤其是使用 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗變更屬性值時，會發現屬性之間有相當多的相互依存性。 有時，某個屬性的特定設定會造成其他屬性自動清除、啟用或停用，甚至從 [屬性] 視窗完全顯示或消失。 這些相互依存性為數眾多，無法完全涵蓋。 

不過，下列清單提供了部分常見的範例，讓您對這些相互依存性的運作方式有所瞭解：  
  
-   設定的屬性時**欄位項目**節點或**欄位屬性**節點的資料類型衍生自簡單型別使用限制機制的整個新類別屬性會變成可用：**限制**。 另外，此新類別中的屬性會根據基底資料型別為字串型別或數字型別而啟用或停用。 如需這種形式的簡單型別衍生的詳細資訊，請參閱[簡單類型衍生使用限制機制](../core/simple-type-derivation-using-the-restriction-mechanism.md)。  
  
-   設定的屬性時**欄位項目**節點或**欄位屬性**節點的資料類型衍生自簡單型別使用清單或聯集機制，**基底資料型別**屬性變更為**項目類型**屬性或**成員型別**屬性，分別。 在後者情況下，對應的下拉式清單會修改為包含核取方塊，允許選取多個型別。 如需有關這些簡單型別衍生的表單的詳細資訊，請參閱[簡單類型衍生使用清單機制](../core/simple-type-derivation-using-the-list-mechanism.md)和[簡單類型衍生使用聯集機制](../core/simple-type-derivation-using-the-union-mechanism.md)。  
  
-   若要公開與一般檔案結構描述相關聯的屬性，您必須設定**Schema Editor Extensions**屬性**結構描述**要包含的節點**一般檔案延伸模組**. 與其他編輯器延伸模組，例如 EDI 延伸模組相關聯的自訂屬性會公開相同的方式： 選擇對應的延伸模組使用**Schema Editor Extensions**屬性。  
  
 此清單所包含的範例是為了說明您在 [屬性] 視窗中會看到的屬性相互依存性類型，但並非這類相互依存性的詳細清單。  
  
## <a name="see-also"></a>另請參閱  
-  [節點屬性](../core/node-properties.md)   
-  下列屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
    -  節點屬性的字母順序清單
    -  所有結構描述的節點屬性 
    -  結構描述編輯器延伸模組