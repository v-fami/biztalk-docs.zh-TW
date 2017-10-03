---
title: "如何新增 Catch 例外狀況 Block5 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding Catch Exception block
- Catch Exception blocks, adding
ms.assetid: 4875060c-976c-40e7-830a-ffd1a47ba68a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c045677fb2d177377725a3f11e81a5c5c70f9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>如何新增 Catch 例外狀況區塊
若要加入**Catch 例外狀況**封鎖**範圍**圖形，**交易類型**屬性**範圍**圖形必須設定為**無**或**長時間執行的**。  
  
### <a name="to-add-a-catch-exception-block"></a>新增 Catch 例外狀況區塊  
  
1.  以滑鼠右鍵按一下**範圍**圖形，，然後按一下**新例外狀況處理常式**。  
  
     A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。  
  
2.  在**屬性**視窗中，指定的屬性。  
  
     最重要的屬性是**例外狀況物件類型**; 這是將要 catch 的訊息類型。  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |**例外狀況物件名稱**|指定例外狀況處理常式所攔截的例外狀況物件名稱。|  
    |**例外狀況物件類型**|決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。|  
  
3.  在**屬性**視窗，請在**例外狀況物件類型**清單中，選取**一般例外狀況**。  
  
4.  內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。  
  
    1.  以滑鼠右鍵按一下下面的**CatchException** ，指向 **插入圖形**，然後選取**建構訊息**。  
  
    2.  [] 內按兩下**MessageAssignment**開啟文字編輯器，然後輸入 「 訊息指派。  
  
         例如，輸入 `Message_3 = Test`。  
  
## <a name="see-also"></a>另請參閱  
 [完成例外狀況訊息](../core/completing-the-exception-message1.md)   
 [如何新增範圍圖形](../core/how-to-add-a-scope-shape5.md)   
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling5.md)