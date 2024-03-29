---
title: 運算質輸入參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cca24f93-74a8-460c-b9ab-9aa2c767fe2f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a4a93d827a5f58401bb9b8fcdf9727c2a61767e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008095"
---
# <a name="functoid-input-parameters"></a>運算質輸入參數
在您的對應中使用運算質的重要層面可能會正確設定運算質的輸入參數。 雖然輸入參數的順序不重要的所有運算質 (例如**加法**運算質，它會顯示相同關聯預期從加法的屬性)，許多運算質必須有其輸入的參數指定正確的順序。  
  
## <a name="create-input-paramaters"></a>建立輸入的參數
 有兩種方式可以建立運算質的輸入參數：  
  
- 在所顯示之格線頁的運算質左邊建立連結。 您用來建立連結的順序就是將關聯輸入參數傳遞給運算質的順序。  
  
- 藉由開啟**設定\<運算質\>運算質**對話方塊，並加入新的輸入參數。 因為此對話方塊可讓您重新排序運算質的輸入參數，使其以正確的順序排列，所以此對話方塊也十分重要。 例如，如果您是以錯誤的順序建立運算質的連結，則可移至此對話方塊，並進行必要的修正。 如需設定運算質的輸入的參數的逐步指示，請參閱 <<c0> [ 如何設定運算質輸入參數](../core/how-to-configure-functoid-input-parameters.md)。  
  
  您必須使用**設定\<運算質\>運算質**對話方塊來建立本身為常數輸入的參數。  
  
  當您連結或運算質使用提供的標籤時**標籤**時選取連結或運算質中的 屬性 視窗中的屬性，該標籤會顯示在**設定\<運算質\>運算質** 對話方塊中，而非對應的結構描述 節點中，XPath 或做為輸入參數的運算質的名稱。 有了標籤後，會比較容易分辨參數，並且可用正確順序排列參數。  
  
  可靠的運算質輸入參數的正確順序的詳細資訊，請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="see-also"></a>另請參閱  
 [設定運算質輸入參數](../core/how-to-configure-functoid-input-parameters.md)   
 [設定指令碼處理運算質](../core/how-to-configure-the-scripting-functoid.md)   
 [設定表格迴圈和表格擷取程式運算質](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md)