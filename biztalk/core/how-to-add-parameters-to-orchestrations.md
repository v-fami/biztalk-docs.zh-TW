---
title: "如何新增參數至協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, parameters
ms.assetid: 35c731ed-6327-4de7-8d2e-4d14024bda77
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8328a97631efb2b8454e0a2679b257d35402cf4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-parameters-to-orchestrations"></a>如何新增參數至協調流程
您可以在 [協調流程檢視] 視窗中指定協調流程應該採用何種參數。 協調流程可以採用下列項目做為參數：  
  
-   訊息  
  
-   變數 (包括物件)  
  
-   相互關聯集合  
  
-   角色連結  
  
-   連接埠  
  
 參數可以在協調流程之間以 in 參數或 out 參數的形式傳遞。 In 參數可以用傳值或傳址方式來傳遞。 Out 參數則能只用傳址方式來傳遞。 參數可以包含變數、訊息、相互關聯集合、角色連結和連接埠。  
  
### <a name="to-set-orchestration-parameters"></a>若要設定協調流程參數  
  
1.  在 [協調流程檢視] 視窗中，使用**協調流程參數**来加入的變數、 訊息和連接埠資料夾。  
  
2.  每個項目加入至**協調流程參數**資料夾中，使用 [屬性] 視窗來指定**方向**屬性：  
  
    -   In，以傳值方式傳入的參數。  
  
    -   Ref，以傳址方式傳入的參數。  
  
    -   Out，以傳址方式傳出的參數。  
  
### <a name="to-add-a-parameter-to-an-orchestration"></a>若要將參數新增至協調流程  
  
1.  在協調流程檢視 視窗中，以滑鼠右鍵按一下**協調流程參數**資料夾，然後按一下您想要的參數類型。  
  
2.  對於已設定的連接埠和角色連結，請使用精靈設定參數。  
  
     -或者-  
  
     對於其他參數類型，請使用屬性頁設定參數。  
  
 **參數型別**  
  
 參數可以依傳值、傳址方式或以 out 參數的形式傳遞。 當值傳遞至協調流程的參數時，資料的複本製作，並由協調流程使用。  
  
 當您使用參考參數時，則不會製作任何複本。 包含資料的記憶體位置會在呼叫的程式與協調流程之間共用，此記憶體位置的內容可由協調流程修改。 這類修改表示參數的值不僅在協調流程中變更，也會在呼叫的程式中變更。  
  
 Out 參數類似於參考參數，不過協調流程無法假設它在傳入時會包含有效資料，而是呼叫的程式可以預期協調流程會對此參數指派值。  
  
 **協調流程參數的規則**  
  
-   您只能傳遞訊息和變數 (包括物件) 做為 out 參數或參考參數。  
  
-   您無法傳遞出或參考中的協調流程參數**啟動協調流程**圖形。  
  
-   在參數中，包括任何角色連結和動態連接埠，都一定得在傳遞至協調流程之前獲得指派。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程圖形](../core/orchestration-shapes.md)   
 [如何新增圖形至協調流程](../core/how-to-add-shapes-to-orchestrations.md)   
 [如何使用選取成品類型對話方塊](../core/how-to-use-the-select-artifact-type-dialog-box.md)