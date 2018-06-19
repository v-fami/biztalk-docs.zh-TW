---
title: 長時間執行交易 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- long-running transactions, about long-running transactions
- atomic transactions, long-running transactions
- long-running transactions, orchestrations
- long-running transactions, nesting
- scopes, examples
- orchestrations, transactions
- compensations, long-running transactions
- compensations, customizing
- transactions, long-running
- transactions, compensation blocks
- long-running transactions
- long-running transactions, timeouts
- compensations, examples
- fault tolerance, long-running transactions
- transactions, examples
- orchestrations, long-running transactions
- transactions, atomic
- transactions, fault tolerance
- scopes, long-running transactions
- long-running transactions, fault tolerance
- transactions, nesting
- examples, scopes
ms.assetid: 4bf4d0c8-903a-411f-963b-bd4cfdfc2958
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86c419c79b9de6287a0361dfe4e2e6b9dc555153
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262774"
---
# <a name="long-running-transactions"></a>長時間執行的交易
長時間執行的交易是在 BizTalk 協調流程中重要並經常使用的建構。 這類交易提供您進行自訂範圍補償、自訂範圍例外狀況處理，以及巢狀交易能力的設備，這些全都會提供您設計健全交易架構的大量彈性。  
  
 當交易需要執行極長的時間，而且您不需要完整的 ACID 屬性時 (也就是說，您不需要保證資料與其他交易隔離)，您就會使用長時間執行的交易。 長時間執行的交易可能會有長期無活動的情況，這通常都是因為在等候外部訊息抵達。  
  
 長時間執行的交易具有一致性與持久性，不過卻沒有不可部分完成性與隔離性。 長時間執行交易內的資料不會被鎖定，因此其他處理序或應用程式都能加以修改。 由於長時間保留鎖定不切實際，因此不會維護狀態更新的隔離屬性。  
  
 長時間執行交易的認可與不可部分執行交易的認可不同。 對於結果，並沒有分散式協調的隱含假設 (長時間執行的交易只會存在於單一的協調流程執行個體中)。 而是在完成長時間執行交易的最後一個陳述式時，便會被視為已認可。 在交易中止的情況下，不會有狀態的「自動」復原。 您可以透過例外狀況和補償處理常式，以程式設計方式來達成這點。  
  
 範圍可以藉由宣告變數、訊息和 .NET 組件，來定義自己的狀態。 長時間執行的交易可存取自己範圍的狀態資訊、封閉該交易的任何範圍，以及在協調流程中全域定義的任何狀態資訊。 對於未封閉該交易的任何範圍，則是無法存取其狀態資訊。  
  
## <a name="nesting"></a>巢狀  
 長時間執行的交易可以包含不可部分完成的交易和其他長時間執行的交易。 它們也可以位於任意深度的巢狀中。 例如，您的交易可能包含兩個其他的長時間執行交易，其中每個都包含不可部分完成的交易。  
  
 當整體交易的一個或多個元件需要是不可部分完成，而整體交易則需要是長時間執行時，巢狀尤其有用。 請考量接收和履行採購單的範例。 採購單可以在任何時刻抵達，而且履行採購單的各種步驟都需要花費時間進行，不過您仍然會將整個程序視為交易。 在此情況下，整體的交易很清楚地必須是長時間執行的，不過個別的步驟 (例如，付款的通知)，則需要是不可部分完成的。  
  
> [!NOTE]
>  您無法將交易範圍放在非交易式範圍或協調流程的巢狀中。 非交易式的封閉範圍或協調流程將不會管理狀態，因為它必須適當地處理其中任何範圍的狀態管理。  
  
> [!NOTE]
>  已同步的交易不得包含其他任何交易或已同步的範圍。  
  
## <a name="compensation"></a>補償  
 長時間執行的交易可以指定補償區塊，在認可後便會呼叫該區塊以補償交易的活動。 這樣可能會在可行時使交易復原，或是執行其他功能 (例如通知)，以協助用某些方式緩和交易的效果。 如果您沒有新增自己的補償程式碼，執行階段引擎便會根據預設，以相反的順序，從最後認可的交易開始，並在第一個認可的交易結束，呼叫內部交易的補償區塊 (包括長時間執行與不可部分執行的區塊)。  
  
> [!NOTE]
>  補償只能在已經成功認可的交易上進行。  
  
## <a name="fault-tolerance"></a>容錯  
 交易支援容錯，以便從內部錯誤 (例如電腦故障和軟體錯誤) 和外部錯誤 (例如取消訊息) 復原。 發生交易失敗時，長時間執行交易的部份更新並不會自動復原，因為這些都在 ACID 交易中。  
  
 當發生錯誤時，便會呼叫長時間執行交易的例外狀況程式碼區塊。 例外狀況程式碼區塊包含一組錯誤的處理常式，讓您能夠撰寫以處理可能在執行交易期間引發的任何錯誤。 在處理錯誤時，您可以依靠訊息、變數和物件的最後已知狀態。  
  
 當例外狀況發生時，您通常會讓例外狀況處理常式評估協調流程的狀態，根據該狀態採取任何所需的動作，並呼叫任何巢狀交易的補償。  
  
 發生錯誤時，會中斷長時間執行之交易的執行。 發生錯誤後便無法繼續執行。  
  
## <a name="see-also"></a>另請參閱  
 [使用長時間執行交易的案例](../core/scenarios-using-long-running-transactions.md)   
 [不可部分完成交易](../core/atomic-transactions.md)   
 [使用交易和例外狀況處理](../core/using-transactions-and-handling-exceptions.md)