---
title: 如何新增 Catch 例外狀況 Block1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions, adding Catch Exception block
- Catch Exception blocks, adding
- exception handling, Catch Exception blocks
ms.assetid: 8e4b264b-b3b0-4d83-81df-a14dc2ddeea2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7922a1527e0f6359427be992c4cc9963f8c7d93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247022"
---
# <a name="how-to-add-a-catch-exception-block"></a>如何新增 Catch 例外狀況區塊
**Catch 例外狀況**區塊代表例外狀況處理常式。 **攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。 您可以附加多個**Catch 例外狀況**視需要會封鎖。  
  
 您可以設定例外狀況處理常式，處理不同類型的例外狀況。 對於每個例外狀況處理常式，您必須指定本身為例外狀況或衍生自 `System` 類別之物件的例外狀況類型。 如果擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫例外狀況處理常式。  
  
> [!NOTE]
>  若要加入**Catch 例外狀況**封鎖**範圍**圖形，交易類型屬性的**範圍**圖形必須設定為**無**或**長時間執行的**。  
  
### <a name="to-add-and-populate-a-catch-exception-block"></a>若要新增和填入 Catch 例外狀況區塊  
  
1.  以滑鼠右鍵按一下**範圍**您要新增的圖形**Catch 例外狀況**區塊，並再按**新例外狀況處理常式**。  
  
     A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。  
  
2.  在**屬性**視窗中，指定的屬性。  
  
     最重要的屬性是 [例外狀況物件類型]，因為這是將會攔截的訊息類型。  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |例外狀況物件名稱|指定例外狀況處理常式所攔截的例外狀況物件名稱。|  
    |例外狀況物件類型|決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。|  
  
3.  在**屬性**視窗，請在**例外狀況物件類型**清單中，選取**一般例外狀況**。  
  
4.  內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。  
  
5.  以滑鼠右鍵按一下下面的**Catch 例外狀況**封鎖，並指向**插入圖形**，，然後選取 **建構訊息**。  
  
6.  [] 內按兩下**MessageAssignment**啟動 「 文字編輯器，並輸入 「 訊息指派。  
  
     例如，輸入 `Message_3 = Test`。  
  
## <a name="see-also"></a>另請參閱  
 [完成例外狀況訊息](../core/completing-the-exception-message5.md)   
 [如何新增範圍圖形](../core/how-to-add-a-scope-shape2.md)   
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling3.md)