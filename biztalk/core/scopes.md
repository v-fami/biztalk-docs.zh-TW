---
title: 範圍 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scopes, exception handling
- Scope shape [Orchestration Designer], nesting
- scopes, variables
- scopes, Scope shape [Orchestration Designer]
- Scope shape [Orchestration Designer], exception handling
- scopes, transactions
- scopes, synchronization
- scopes, nesting
- Scope shape [Orchestration Designer], transactions
ms.assetid: 51d81ce4-0034-4415-b6ab-4c952737c1bd
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bc4d1b5d926540477293591ade8123126be1b84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269774"
---
# <a name="scopes"></a>範圍
範圍是群組動作的架構。 範圍主要用於交易式執行和例外狀況處理。  
  
 範圍可以包含一個或多個區塊。 範圍具有一個本文，並且可以選擇性地附加任何數目的例外狀況處理區塊。 取決於範圍的本質，範圍也可以具有選擇性的補償區塊。 有些範圍會單純用於例外狀況處理，而不需要任何的補償。 其他的範圍則是明確交易式的，而且永遠會有預設的補償處理常式，以及您可以為其建立的選擇性補償處理常式。 交易式範圍也有一個預設的例外狀況處理常式，以及由您為其建立之任何數目的其他例外狀況處理常式。  
  
## <a name="synchronized-scopes"></a>同步處理的範圍  
 您可以將範圍指定為同步處理或非同步處理。 藉由同步處理某個範圍，您可以確保在其中存取的任何共用資料，都不會寫入協調流程中的一個或多個平行動作，或是在由其他動作讀取時寫入。  
  
 不可部分完成的交易範圍永遠都會是同步處理的。 同步處理之範圍內的所有動作，以及在其任何例外狀況處理常式中的所有動作，都會被視為已同步。 交易式範圍之補償處理常式中的動作，則不會同步。  
  
> [!CAUTION]
>  請注意，如果沒有小心設計您的處理序，您依然可能會碰到鎖死的狀況。 例如：協調流程 A 中的兩個平行分支存取相同的訊息，一個傳送該訊息，另一個則接收該訊息，兩者都需要同步處理的範圍。 第二個協調流程則會接收該訊息，並且將其傳回。 這樣在協調流程 A 中的傳送分支，就有可能會在接收分支之前收到鎖定，而您將會面臨鎖死的狀況。  
  
## <a name="nesting-of-scopes"></a>巢狀範圍  
 您可以巢狀**範圍**圖形內部其他**範圍**圖形。 巢狀範圍的規則如下：  
  
-   交易式和 (或) 同步處理的範圍，都不能放在同步處理範圍 (包括同步處理範圍的例外狀況處理常式) 的巢狀內。  
  
-   不可部分完成的交易範圍無法在其中具有其他任何巢狀的交易式範圍。  
  
-   交易式範圍不能位於非交易式範圍或協調流程內的巢狀。  
  
-   您可以巢狀範圍最多 21 個層級深度。  
  
-   **呼叫協調流程**圖形可以包含在範圍內，但呼叫的協調流程會被視為與任何其他相同巢狀交易，並套用相同的規則。  
  
-   **啟動協調流程**圖形可以包含在範圍內。 巢狀限制並不適用於啟動的協調流程。  
  
## <a name="scope-variables"></a>範圍變數  
 您可以在範圍層級宣告如訊息和相互關聯集合一類的變數。 您不能對範圍變數使用與協調流程變數相同的名稱，而且，也不允許隱藏名稱。  
  
## <a name="see-also"></a>另請參閱  
 [使用交易和例外狀況處理](../core/using-transactions-and-handling-exceptions.md)   
 [不可部分完成交易](../core/atomic-transactions.md)