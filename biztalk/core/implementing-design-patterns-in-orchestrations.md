---
title: "在協調流程中實作的設計模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Aggregator pattern, orchestrations
- Error Handling pattern [orchestrations]
- patterns, orchestrations
- designing, orchestrations
- orchestrations, designing
- Exception Handling and Compensation pattern [orchestrations]
- Parallel Convoy pattern [orchestrations]
- Dynamic Router pattern [orchestrations]
- orchestrations, patterns
- patterns
- Composed Message Processor pattern [orchestrations]
- Suspend with Retry pattern, orchestrations
- Calling Pipelines from Orchestration pattern [orchestrations]
- Message Filter pattern [orchestrations]
- Message Broker pattern [orchestrations]
- Content-Based Router pattern [orchestrations]
- Sequential Convoy pattern [orchestrations]
- Scatter and Gather pattern [orchestrations]
- Splitter pattern, orchestrations
- Message Translator pattern [orchestrations]
ms.assetid: f62ba955-018a-40e7-b303-497acc906019
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a4837ddf1199425a76a6fa82bbfd6e44615b6c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-design-patterns-in-orchestrations"></a>實作協調流程中的設計模式
本節討論 BizTalk Server 程式設計的常見模式以及企業整合模式。 您可以利用單一模式或結合數個模式來設計您的商務程序，然後再使用 BizTalk 協調流程設計師中的圖形來實作設計。  
  
## <a name="design-patterns"></a>設計模式  
 下列項目將簡短描述每個模式，並指向說明如何使用 BizTalk 協調流程設計師實作模式的主題或範例。  
  
### <a name="aggregator"></a>彙總工具  
 彙總工具模式可從多個來源接收資訊並將它併入單一訊息。 如需此模式的範例，請參閱中的 Aggregate.odx[彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。  
  
### <a name="calling-pipelines-from-an-orchestration"></a>從協調流程呼叫管線  
 您可以從協調流程傳送及接收管線。 這允許重複使用管線並協助維護管線階段的協調流程解離。 如需此模式的範例，請參閱中的 Aggregate.odx[彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。 另一個例子是中的 CMP.odx[撰寫訊息處理器 （BizTalk Server 範例）](../core/composed-message-processor-biztalk-server-sample.md)。 另請參閱[如何使用運算式執行管線](../core/how-to-use-expressions-to-execute-pipelines.md)。  
  
### <a name="composed-message-processor"></a>撰寫訊息處理器  
 撰寫訊息處理器模式可從匯總的或批次的交換訊息來處理個別的項目。 如需此模式的範例，請參閱中的 CMP.odx[撰寫訊息處理器 （BizTalk Server 範例）](../core/composed-message-processor-biztalk-server-sample.md)。  
  
### <a name="content-based-router"></a>以內容為基礎的路由  
 以內容為基礎的路由模式可根據訊息內容的某些部分來決定訊息收件者。 如需此模式的範例，請參閱[CBRSample （BizTalk Server 範例）](../core/cbrsample-biztalk-server-sample.md)。  
  
### <a name="dynamic-router"></a>動態路由器  
 動態路由器模式可根據訊息處理的結果而決定目的地位址以及傳輸通訊協定。 您可以使用動態傳送埠或**角色連結**圖形來實作此模式。 如需此模式的範例，請參閱中的 ReceiveSend.odx [SendMail](../core/sendmail.md)。 另一個例子是中的 SupplierProcess.odx [PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)。  
  
### <a name="error-handling"></a>錯誤處理  
 BizTalk Server 可讓您指定自動化處理傳訊失敗，做為在已擱置佇列中放置失敗訊息的預設行為替代解決方案。 您可以將失敗的訊息路由至訂閱連接埠，以進行報告或處理。 如需此模式的範例，請參閱中的 ResubmitLogic.odx[錯誤處理 （BizTalk Server 範例資料夾）](../core/error-handling-biztalk-server-samples-folder.md)。  
  
### <a name="exception-handling-and-compensation"></a>例外狀況處理和補償  
 您可以使用例外狀況處理常式和**擲回的例外狀況**圖形或**運算式**例外狀況處理的圖形。 例如，您可以在其中放置中的下列程式碼**運算式**擲回例外狀況的圖形:，  
  
```  
excp = new System.Exception();  
throw(excp);  
```  
  
 您可以使用補償區塊和**補償**圖形上的已認可的交易執行補償。 如需此模式的範例，請參閱中的 UpdateContact.odx[補償 （BizTalk Server 範例）](../core/compensation-biztalk-server-sample.md)。 另一個例子是在[自訂例外狀況](../core/custom-exceptions.md)。  
  
### <a name="message-broker"></a>訊息仲介  
 訊息仲介模式可決定訊息的目的地，並保持對訊息流量的控制。 如需詳細資訊，請參閱[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。  
  
### <a name="message-filter"></a>訊息篩選  
 訊息篩選模式會選取符合特殊準則的訊息，以進行處理。 您可以實作此模式的篩選運算式加入至啟動**接收**圖形。 如需詳細資訊，請參閱[使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md)。  
  
### <a name="message-translator"></a>訊息轉譯程式  
 訊息轉譯程式模式可將訊息從一種形式轉換成另一種形式。 您可以使用與 BizTalk 對應來實作此模式**轉換**使用協調流程。 如需此模式的範例，請參閱中的 HelloOrchestration.odx [HelloWorld （BizTalk Server 範例）](../core/helloworld-biztalk-server-sample.md)。  
  
### <a name="parallel-convoy"></a>平行群組  
 平行群組模式可以讓多個單一項目聯結在一起，達到個別項目無法完成的目標。 一組相關的項目會依任何順序抵達，但 BizTalk Server 必須收到所有的訊息，才能開始處理。 如需此模式的範例，請參閱[http://go.microsoft.com/fwlink/?LinkId=56035](http://go.microsoft.com/fwlink/?LinkId=56035)。  
  
### <a name="scatter-and-gather"></a>散佈和收集  
 散佈和收集模式可將訊息傳送至多個收件者，並從每個收件者接收回訊息。 您可以使用分隔器模式和彙總工具模式來實作此模式。 您可以使用彙總工具模式來組合使用分隔器模式的結果，並放在**平行動作**圖形。 如需分隔器模式的範例，請參閱 SDK 範例具名實作散佈和收集模式時[http://go.microsoft.com/fwlink/?LinkId=65185](http://go.microsoft.com/fwlink/?LinkId=65185)。  
  
### <a name="sequential-convoy"></a>循序群組  
 循序群組模式可以讓多個單一項目聯結在一起，達到個別項目無法完成的目標。 循序群組是具有預先定義順序的相關項目組。 雖然項目不需要完全相同，但 BizTalk Server 必須以循序方式接收這些項目。 如需此模式的範例，請參閱[http://go.microsoft.com/fwlink/?LinkId=56035](http://go.microsoft.com/fwlink/?LinkId=56035)。  
  
### <a name="splitter"></a>分隔器  
 分隔器模式會將單一訊息分割為多個訊息。  
  
### <a name="suspend-with-retry"></a>重試擱置模式  
 重試擱置模式可讓協調流程在錯誤發生時擱置訊息。 擱置會發生在迴圈中，讓協調流程擱置、要求操作人員介入、然後以固定次數重試作業。  
  
## <a name="see-also"></a>另請參閱  
 [設計協調流程](../core/designing-orchestration-flow.md)