---
title: "使用運算質建立更複雜的對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d53e3a3-5ccd-4733-8c2f-3101e41fca61
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736b6fa99844182c59db582182056faea1d3f322
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-functoids-to-create-more-complex-mappings"></a>使用運算質建立更多複雜的對應

## <a name="overview"></a>概觀
運算質在許多對應實例中扮演重要的角色。 若沒有運算質，您仍可以複製項目和屬性資料，但最嚴重的是，您無法操控這些值。 使用運算質，可讓您進行幾乎所有的轉換。 例如，您可以使用運算質從完全不同的位置取得兩個值、將它們相加，並將總和放置在目的結構描述中。  
  
 當您編輯 BizTalk 對應時，運算質會出現在「[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱」中 (每個類別都有一個工具箱索引標籤)。 在您按一下對應的索引標籤以開啟「工具箱」並選擇運算質類別之後，將運算質拖曳至格線頁。 然後您可以建立運算質之間的輸入和輸出連結，可以是結構描述節點，或是另一個運算質。 輸入連結對應到輸入參數，並從左邊帶出運算質；輸出連結對應到輸入參數，並將運算質留在右邊。  
  
 如同其他對應項目，運算質也具有屬性。 運算質最重要的屬性之一是其輸入參數集。 如需詳細資訊，請參閱[如何新增基本運算質加入至地圖](../core/how-to-add-basic-functoids-to-a-map.md)。  
  
 本節提供在 BizTalk 對應中使用運算質的逐步指示。 如需運算質的參考資訊，請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟 
  
-   [如何開啟運算質工具箱](../core/how-to-open-the-functoid-toolbox.md)  
  
-   [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)  
  
-   [新增進階運算質至對應](../core/adding-advanced-functoids-to-a-map.md)  
  
-   [編輯運算質屬性和輸入的參數](../core/editing-functoid-properties-and-input-parameters.md)  
  
-   [如何選取多個運算質](../core/how-to-select-multiple-functoids.md)  
  
-   [如何刪除運算質](../core/how-to-delete-functoids.md)  
  
-   [如何複製、 剪下和貼上運算質](../core/how-to-copy-cut-and-paste-a-functoid.md)