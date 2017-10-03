---
title: "如何使用運算式執行管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExecuteReceivePipeline() method
- pipelines, schema resolution
- ExecuteSendPipeline() method
- SendPipelineInputMessages class
- pipelines, restrictions
- pipelines, errors
- XLANGPipelineManager class
- receive pipelines, orchestrations
- ReceivePipelineOutputMessages class
- orchestrations, pipelines
- pipelines, component types
- send pipelines, orchestrations
- pipelines, states
- pipelines, executing
- Microsoft.XLANGs.Pipeline namespace
- pipelines, transactional
- pipelines, orchestrations
- Message Assignment shape [Orchestration Designer], pipelines
ms.assetid: f947fa73-526c-4747-8de7-df557a93056c
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5a6090e0d7322a0e5b10d13016c073b73074392
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expressions-to-execute-pipelines"></a>如何使用運算式執行管線
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]能夠以同步方式呼叫從協調流程內的管線。 這可以讓協調流程針對資料體而利用封裝在管線內容的訊息處理功能 (傳送或接收)，而不需透過傳訊基礎結構來傳送該資料。  
  
 協調流程可藉由此功能呼叫傳送管線，以將數個訊息彙總為單一的外寄交換。 相反地，協調流程也可以呼叫接收管線，針對在傳訊基礎結構外部所取得的交換進行解碼及解譯，而不需透過 MessageBox 進行處理。  
  
## <a name="details"></a>詳細資料  
 協調流程中使用方法**XLANGPipelineManager**類別 (在**Microsoft.XLANGs.Pipeline**命名空間) 來呼叫傳送或接收管線。  接收管線會使用單一訊息或交換，並在管線於 BizTalk 傳訊內的接收訊息內容中執行時，產生零個或多個訊息。 傳送管線會使用一個或多個訊息，並同樣在管線於 BizTalk 傳訊內的傳送訊息內容中執行時，產生單一的訊息或交換。  
  
## <a name="calling-a-receive-pipeline"></a>呼叫接收管線  
 若要呼叫從協調流程內部，應用程式會呼叫接收管線**executereceivepipeline （)**方法**XLANGPipelineManager**類別。  這個方法會使用單一的交換，並傳回零個或多個訊息的集合 (執行個體中包含**ReceivePipelineOutputMessages**類別)。 這個方法的語法會詳細說明.NET 類別庫參考**XLANGPipelineManager**類別。  
  
 從協調流程內執行接收管線的 API 為：  
  
 `// Execute receive pipeline`  
  
 `static public ReceivePipelineOutputMessages ExecuteReceivePipeline(System.Type receivePipelineType, XLANGMessage msg);`  
  
 通常會完成對接收管線的呼叫**運算式**圖形在協調流程中的。  
  
 為了從協調流程內部呼叫接收管線，開發人員必須在協調流程專案中參考管線組件。 以下是呼叫接收管線的協調流程範例：  
  
 ![呼叫接收管線畫面](../core/media/callingreceivepipelinefromorchestration.gif "CallingReceivePipelineFromOrchestration")  
  
 如需更詳細的範例，請參閱 SDK 範例[撰寫訊息處理器 （BizTalk Server 範例）](../core/composed-message-processor-biztalk-server-sample.md)。  
  
> [!NOTE]
>  類型的變數**ReceivePipelineOutputMessages**可以只在協調流程中不可部分完成的範圍內宣告。  這是因為此類型的變數並未序列化，因此無法在持續的協調流程使用，而在不可部分完成的範圍內執行的協調流程也絕對無法持續。  這代表接收管線只能在不可部分完成的範圍內執行。  
  
> [!NOTE]
>  當呼叫**PassThruReceive**管線或協調流程內的自訂管線元件，您必須宣告內送訊息的變數類型為 System.Xml.XmlDocument，不論內送訊息類型是否為 XML. 因此，如果內送訊息為一般檔案格式訊息的非 XML 訊息，而您嘗試要在其上作業，則可能會遇到例外狀況。 這是因為在上述的案例中，該協調流程引擎會對任何類型的內送訊息使用 System.Xml.XmlDocument。  
  
## <a name="calling-a-send-pipeline"></a>呼叫傳送管線  
 若要呼叫傳送管線從協調流程，應用程式會呼叫內**executesendpipeline （)**方法**XLANGPipelineManager**類別。 這個方法會使用一或多個訊息的集合 (執行個體中包含**SendPipelineInputMessages**類別)，並傳回單一的交換。 這個方法的語法會詳細說明.NET 類別庫參考**XLANGPipelineManager**類別。  因為執行傳送管線會產生新的交易，在呼叫**executesendpipeline （)**方法必須由訊息指派圖形內，在這種情況：  
  
 從協調流程內部執行傳送管線的 API 為：  
  
 `// Execute a send pipeline`  
  
 `static public ExecuteSendPipeline(System.Type sendPipelineType, SendPipelineInputMessages inputMsgs, XLANGMessage msg);`  
  
 在中，必須完成呼叫傳送管線**訊息指派**圖形在協調流程中的。  
  
 為了從協調流程內部呼叫傳送管線，開發人員必須在協調流程專案中參考管線組件。  呼叫傳送管線的協調流程範例：  
  
 ![呼叫傳送管線畫面](../core/media/example-callingsendpipelinefromorchestration.gif "Example_CallingSendPipelineFromOrchestration")  
  
> [!NOTE]
>  在呼叫預設的 XMLTransmit 管線時，必須將訊息內容屬性 XMLNORM.EnvelopeSpecName 設定為「信封」結構描述的完整格式名稱。 例如：  
>   
>  `MyMessage(XMLNORM.EnvelopeSpecName) = "PipelineSchemas.POEnv, PipelineSchemas, Version=1.0.0.0, Culture=nuetral, PublicKeyToken=12e5cc95621c33e8";`  
  
 如需更詳細的範例，請參閱 SDK 範例[彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。  
  
## <a name="pipeline-execution---behavioral-differences"></a>管線執行 - 行為差異  
 由協調流程呼叫傳送或接收管線時，該管線的執行，大致與它在傳訊基礎結構內 (在接收位置或傳送埠上) 執行時相同。  不過仍有些特定的行為差異，如下所述。  
  
### <a name="differences-within-pipeline-stages"></a>管線階段內的差異  
 從協調流程內呼叫傳送或接收管線時，其階段的執行，幾乎與該管線是從 BizTalk 傳訊基礎結構呼叫時的階段執行相同，例外狀況如下所示。  
  
-   組合器/解譯器： 組合器和解譯器階段不會處理**追蹤設定檔**資料。  
  
-   編碼器/解碼器： MIME 編碼器以數位方式簽署訊息使用設定在主機與主機相關聯的憑證。  SMIME 編碼器會在傳遞給管線的訊息內容上，使用該憑證來加密訊息。  
  
### <a name="schema-resolution"></a>結構描述解析  
 從協調流程執行管線時，會支援兩種結構描述尋查演算法。  
  
-   依型別解析  
  
-   依名稱解析  
  
 如果部署了重複的結構描述，則用於選取適當結構描述的演算法邏輯，與在傳訊基礎結構內容中執行時所使用的邏輯相同。  
  
### <a name="transactional-pipelines"></a>交易管線  
 如果管線的階段會呼叫交易式元件，則該管線沒有可用的交易式內容。  呼叫**ipipelinecontext.gettransaction （)**將會擲回**NotSupportedException**。  這樣並不會造成無法從協調流程執行此類管線，但的確代表該管線不必偵測和處理這種情況。  
  
### <a name="message-destination"></a>訊息目的地  
 在此內容中並不支援依管線元件控制訊息目的地。  設定內容屬性**MessageDestination**或**SuspendOnRoutingFailure**會導致**XLANGPipelineManagerException**擲回。  
  
### <a name="pipeline-component-types"></a>管線元件類型  
 若要從協調流程內呼叫管線元件，則該元件必須以下列項目為基礎：  
  
-   .NET Framework v1.1  
  
-   .NET Framework v2.0  
  
-   .NET Framework v3.0  
  
-   .NET Framework v3.5  
  
-   .NET Framework v4.0  
  
-   .NET Framework v2.0  
  
-   COM  
  
## <a name="restrictions"></a>限制  
 下列類型的管線**無法**從協調流程內執行：  
  
-   交易管線  
  
-   可復原管線  
  
-   管線會呼叫 BAM 攔截器 API ( **NotSupportedException**就會擲回)。  
  
-   相同的管線執行個體無法在不同分支的平行圖形中執行，除非是放在每個分支的同步化範圍中。  
  
-   根據 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] SDK 所建置的現有管線 (組件)。  
  
## <a name="failure-modes-and-effects"></a>失敗模式和效果  
 如果因為從 BizTalk Server 傳訊基礎結構內呼叫管線而導致訊息擱置，則該執行管線時的任何失敗都會導致擲回例外狀況。  擲回的例外狀況屬於型別**Microsoft.XLANGs.Pipeline.XLANGPipelineManagerException**。  可在呼叫協調流程中的 Catch 區塊中處理這個擲回的例外狀況。  如果協調流程並未捕捉到擲回的例外狀況，則 XLANGs 引擎會報告錯誤，並在文字中包含擲回例外狀況中的例外狀況資訊。  
  
 例外狀況會對管線元件所產生的錯誤訊息執行格式設定。  
  
 **訊息**屬性**XLANGPipelineManagerException**類別包含管線執行錯誤的詳細資料。 此詳細資料會使用下列格式：  
  
-   執行管線失敗\<管線類型 >。  錯誤詳細資料\<格式化的錯誤訊息 >。  
  
 在此訊息中，\<管線類型 > 是管線類型的名稱和\<格式化的錯誤訊息 > 是在管線執行期間發生之特定失敗的描述。  
  
 例如，如果協調流程呼叫接收管線，而該管線執行失敗，因為沒有任何管線元件可辨識訊息的值**XLANGPipelineManagerException**的屬性會是：  
  
|XLANGPipelineManagerException 屬性|值|  
|--------------------------------------------|-----------|  
|訊息|執行接收管線 "MyPipelines.ReceivePipeline" 失敗。 錯誤詳細資料: 「 沒有解譯階段元件可辨識資料。|  
|元件|String.Empty|  
  
 另舉一例，如果協調流程呼叫傳送管線，而該管線執行失敗，因為驗證失敗中的文字**訊息**屬性**XLANGPipelineManagerException**會是：  
  
|XLANGPipelineManagerException 屬性|值|  
|--------------------------------------------|-----------|  
|訊息|執行傳送管線 "MyPipelines.SendPipeline" 失敗。  錯誤詳細資料: 「 無法驗證文件:"\<項目名稱 > 項目無效-值\<項目值 > 無效根據其資料類型為 'String' 的條件約束模式失敗。""|  
|元件|“Microsoft.BizTalk.Component.XmlValidator”|