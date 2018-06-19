---
title: 如何新增 Catch 例外狀況 Block2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Catch Exception blocks
- exceptions, Catch Exception blocks
ms.assetid: 7c8b6024-e8dc-4417-83f9-bf4032644b91
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e48ce1e6f0646acdf63ed33582f382f1baed797
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246838"
---
# <a name="how-to-add-a-catch-exception-block"></a>如何新增 Catch 例外狀況區塊
**Catch 例外狀況**區塊代表例外狀況處理常式。 **攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。 您可以附加多個**Catch 例外狀況**視需要會封鎖。  
  
 您可以設定例外狀況處理常式，處理不同類型的例外狀況。 對於每個例外狀況處理常式，您必須指定例外狀況類型。 這必須是例外狀況或衍生自類別 `System` 的物件。 如果擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫例外狀況處理常式。  
  
> [!NOTE]
>  若要加入 Catch 例外狀況區塊至 「 範圍 」 圖形，「 範圍 」 圖形的交易類型屬性必須設定為**無**或**長時間執行**。  
  
### <a name="to-add-and-populate-a-catch-exception-block"></a>若要新增和填入 Catch 例外狀況區塊  
  
1.  以滑鼠右鍵按一下**範圍**您要新增的圖形**Catch 例外狀況**區塊，並再按**新例外狀況處理常式**。  
  
     A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。  
  
2.  在**屬性**視窗中，指定的屬性。  
  
     最重要的屬性是**例外狀況物件類型**; 這是將要 catch 的訊息類型。  
  
3.  在**屬性**windows，請在**例外狀況物件類型**清單中，選取**一般例外狀況**。  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |**例外狀況物件名稱**|指定例外狀況處理常式所攔截的例外狀況物件名稱。|  
    |**例外狀況物件類型**|決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。|  
  
4.  在 [Catch 例外狀況] 區塊內新增圖形，建立例外狀況的處理程序。  
  
    1.  以滑鼠右鍵按一下下面的**CatchException** ，指向 **插入圖形**，然後選取**建構訊息**。  
  
    2.  [] 內按兩下**MessageAssignment**開啟文字編輯器，然後輸入 「 訊息指派。  
  
         例如，輸入 `Message_3 = Test`。  
  
## <a name="see-also"></a>另請參閱  
 [完成例外狀況訊息](../core/completing-the-exception-message4.md)   
 [如何新增範圍圖形](../core/how-to-add-a-scope-shape4.md)   
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling4.md)