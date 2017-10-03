---
title: "如何新增 Catch 例外狀況 Block3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer]
- Catch Exception block [Orchestration Designer], creating
- Catch Exception block [Orchestration Designer], exception handler
- Catch Exception block [Orchestration Designer], about Catch Exception blocks
- Orchestration Designer, errors
ms.assetid: 63ca4a60-b657-452a-86fd-78968ccf2933
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1040a27a5e1273d2ad80a722deb421878de36c12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a>如何新增 Catch 例外狀況區塊
**Catch 例外狀況**區塊代表例外狀況處理常式。 **攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。 您可以附加多個**Catch 例外狀況**視需要會封鎖。  
  
 您可以設定例外狀況處理常式，處理不同類型的例外狀況。 對於每個例外狀況處理常式中，您可以指定例外狀況類型的錯誤訊息或衍生自類別的物件必須是**System.Exception**。 如果您未指定的例外狀況類型，例外狀況區塊會被視為一般例外狀況處理常式中，而且可以攔截例外狀況不是衍生自**System.Exception**。  
  
 如果擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫例外狀況處理常式。 其他例外狀況則交由預設的例外狀況處理常式處理。  
  
> [!NOTE]
>  若要加入**Catch 例外狀況**封鎖**範圍**圖形，**交易類型**屬性**範圍**圖形必須設定為**無**或**長時間執行的**。  
  
### <a name="to-add-a-catch-exception-block"></a>若要新增 Catch 例外狀況區塊  
  
1.  以滑鼠右鍵按一下**範圍**您要新增的圖形**Catch 例外狀況**區塊，並再按**新例外狀況處理常式**。  
  
     A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。  
  
2.  在 [屬性] 視窗中，指定以下屬性：  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |例外狀況物件名稱|指定例外狀況處理常式所攔截的例外狀況物件名稱。|  
    |例外狀況物件類型|決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。|  
  
3.  內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。  
  
> [!NOTE]
>  如果您指定做為一般例外狀況**例外狀況**物件類型， **Catch 例外狀況**區塊就會攔截任何例外狀況，包括非衍生自**System.Exception**. 在此狀況下，您無法存取例外狀況物件。 這在區塊內，如果您使用**擲回的例外狀況**圖形與一般例外狀況類型，您將能有效地重新擲回攔截的例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況](../core/exceptions.md)