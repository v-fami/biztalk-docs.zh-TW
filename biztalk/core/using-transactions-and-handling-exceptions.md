---
title: "使用交易及處理例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions, orchestrations
- orchestrations, transactions
- orchestrations, errors
- transactions
- errors, orchestrations
- transactions, BizTalk Server Orchestration Engine
- errors, Scope shape [Orchestration Designer]
- Scope shape [Orchestration Designer], errors
- Scope shape [Orchestration Designer], transactions
ms.assetid: bb38f5eb-6641-4e7c-8e2a-c474fc739999
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab32729aa6b4f12aada623587f52728c6bd23240
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-transactions-and-handling-exceptions"></a>使用交易和例外狀況處理
設計協調流程時，您應該仔細思考可能發生問題的地方，以及處理問題的最佳方式。 許多協調流程都有多個潛在的失敗點。 問題可能是由其他原因所引起；例如，伺服器可能當機，或是訊息格式不正確。  
  
 對於長時間執行或複雜的協調流程而言，持續追蹤狀態與即時報告錯誤尤其重要，因為這樣您才能夠以最少的精力正確解決問題。 對於協調流程來說，維持一組關係緊密的動作保持完整也一樣重要，如此在執行交易的某一部分，而其他部分未執行的情況下，才能回復完整的交易 (即使該交易從未執行也一樣)。  
  
 即使有外部系統參與交易過程，BizTalk 協調流程也可讓您確保工作不可部分完成的特性，也就是相關動作的完整性。 它提供多項工具，供您處理錯誤、維護協調流程的狀態，以及透過交易、補償和例外狀況處理即時修正問題。  
  
 做為交易和例外狀況處理的架構，協調流程設計師 」 提供**範圍**圖形。 範圍可以包含交易類型、補償和任何數目的例外狀況處理常式。  
  
 設定交易和例外狀況處理的步驟如下：  
  
-   建立範圍。  
  
-   識別您需要的交易種類。  
  
-   判斷需要補償的部分。  
  
-   識別潛在的錯誤。  
  
-   新增適當的例外狀況處理常式和補償程式碼。  
  
## <a name="examples-of-using-transactions-exception-handlings-and-compensations"></a>使用交易、例外狀況處理和補償的範例  
  
-   [錯誤處理 （BizTalk Server 範例資料夾）](../core/error-handling-biztalk-server-samples-folder.md)  
  
-   [補償 （BizTalk Server 範例）](../core/compensation-biztalk-server-sample.md)  
  
-   下載 SDK 範例 「 不可部分完成交易與 COM + Serviced 元件中協調流程 」 從[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
-   下載 SDK 範例 「 使用 SQL 配接器使用不可部分完成交易中協調流程 」 從[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
-   下載 SDK 範例 「 使用長時間執行交易的協調流程 」 從[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
-   下載 SDK 範例 「 例外狀況處理中協調流程 」 從[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [範圍](../core/scopes.md)  
  
-   [如何設定 「 範圍 」 圖形](../core/how-to-configure-the-scope-shape.md)  
  
-   [建立交易式協調流程](../core/making-orchestrations-transactional.md)  
  
-   [例外狀況](../core/exceptions.md)  
  
-   [補償](../core/compensation.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用 「 BizTalk 傳訊引擎](../core/using-the-biztalk-messaging-engine.md)