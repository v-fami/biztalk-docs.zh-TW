---
title: "如何新增 Catch 例外狀況 Block6 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exception handling, Catch Exception block
- Catch Exception blocks
- exceptions, Catch Exception block
ms.assetid: 404312dd-773b-44fe-8b65-7de3d0af2f79
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4be60ddbe45ef4b4f293d7959dc774254e7cd3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>如何新增 Catch 例外狀況區塊
**Catch 例外狀況**區塊代表例外狀況處理常式。 **攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。 在 BizTalk Server 中，您可以附加多個**Catch 例外狀況**視需要會封鎖。  
  
 您可以設定例外狀況處理常式，處理不同類型的例外狀況。 對於每個例外狀況處理常式，您必須指定本身為錯誤訊息或衍生自 `System.Exception` 類別之物件的例外狀況類型。 如果未指定例外狀況類型，例外狀況區塊會被視為一般例外狀況處理常式，而且可以攔截非衍生自 `System.Exception` 的例外狀況。  
  
 若擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫該例外狀況處理常式。 其他例外狀況則交由預設的例外狀況處理常式處理。  
  
> [!NOTE]
>  若要加入**Catch 例外狀況**封鎖**範圍**圖形，**交易類型**屬性**範圍**圖形必須設定為 None 或長在執行中。  
  
## <a name="adding-and-populating-a-catch-exception-block"></a>新增和填入 Catch 例外狀況區塊  
  
#### <a name="to-add-and-populate-a-catch-exception-block"></a>新增和填入 Catch 例外狀況區塊  
  
1.  以滑鼠右鍵按一下**範圍**您想要新增的圖形**Catch 例外狀況**區塊，然後按一下 **新例外狀況處理常式**。  
  
     A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。  
  
2.  在**屬性**視窗中，指定的屬性。 最重要的屬性是**例外狀況物件類型**因為這是將要 catch 的訊息類型。  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |例外狀況物件名稱|指定例外狀況處理常式所攔截的例外狀況物件名稱。|  
    |例外狀況物件類型|決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。|  
  
3.  在**屬性**視窗中，按一下 **例外狀況物件類型**清單。 此清單包含配接器擲回的一般例外狀況。  
  
     名稱會出現為您在後端系統的連接埠中設定的錯誤，例如 PS.SQLExecute.Fault。  
  
4.  加入名稱**例外狀況物件名稱**，例如 Test。  
  
     內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。  
  
    1.  以滑鼠右鍵按一下下面的**Catch 例外狀況**，指向**插入圖形**，然後選取**建構訊息**。  
  
         ![](../core/media/siebeladapter-20-exceptionhandling-constructmessage.gif "SiebelAdapter_20_ExceptionHandling_ConstructMessage")  
  
    2.  [] 內按兩下**MessageAssignment**開啟文字編輯器，然後輸入 「 訊息指派。  
  
         輸入您在設定的名稱**例外狀況物件名稱**從**Catch 例外狀況**，以及您建立之錯誤的新訊息。  
  
         例如，輸入 `Message_3 = Test`。  
  
         ![](../core/media/siebeladapter-21-exceptionhandling-message3test.gif "SiebelAdapter_21_ExceptionHandling_Message3Test")  
  
## <a name="see-also"></a>另請參閱  
 [如何新增範圍圖形](../core/how-to-add-a-scope-shape1.md)   
 [完成例外狀況訊息](../core/completing-the-exception-message3.md)   
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling2.md)