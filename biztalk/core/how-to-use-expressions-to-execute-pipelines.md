---
title: 如何使用運算式執行管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08f5933d3592d391087196f31185e279c40c4836
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974652"
---
# <a name="how-to-use-expressions-to-execute-pipelines"></a><span data-ttu-id="7cbe2-102">如何使用運算式執行管線</span><span class="sxs-lookup"><span data-stu-id="7cbe2-102">How to Use Expressions to Execute Pipelines</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7cbe2-103">能夠以同步方式呼叫從協調流程內的管線。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-103"> has the ability to synchronously call a pipeline from within an Orchestration.</span></span> <span data-ttu-id="7cbe2-104">這可以讓協調流程針對資料體而利用封裝在管線內容的訊息處理功能 (傳送或接收)，而不需透過傳訊基礎結構來傳送該資料。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-104">This enables orchestrations to leverage the message processing encapsulated within a pipeline (either send or receive) against a body of data without having to send that data through the messaging infrastructure.</span></span>  
  
 <span data-ttu-id="7cbe2-105">協調流程可藉由此功能呼叫傳送管線，以將數個訊息彙總為單一的外寄交換。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-105">You can use this feature to enable an orchestration to call a send pipeline in order to aggregate several messages into a single outgoing interchange.</span></span> <span data-ttu-id="7cbe2-106">相反地，協調流程也可以呼叫接收管線，針對在傳訊基礎結構外部所取得的交換進行解碼及解譯，而不需透過 MessageBox 進行處理。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-106">Conversely, an orchestration could call a receive pipeline to decode and disassemble an interchange obtained outside of the messaging infrastructure, without incurring the processing costs of going through the message box.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7cbe2-107">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7cbe2-107">Details</span></span>  
 <span data-ttu-id="7cbe2-108">協調流程中使用方法**XLANGPipelineManager**類別 (在**Microsoft.XLANGs.Pipeline**命名空間) 來呼叫傳送或接收管線。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-108">Orchestrations use methods in the **XLANGPipelineManager** class (in the **Microsoft.XLANGs.Pipeline** namespace) to call send or receive pipelines.</span></span>  <span data-ttu-id="7cbe2-109">接收管線會使用單一訊息或交換，並在管線於 BizTalk 傳訊內的接收訊息內容中執行時，產生零個或多個訊息。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-109">A Receive pipeline consumes either a single message or an interchange and yields zero or more messages, just as when the pipeline executes in the context of receiving a message within BizTalk messaging.</span></span> <span data-ttu-id="7cbe2-110">傳送管線會使用一個或多個訊息，並同樣在管線於 BizTalk 傳訊內的傳送訊息內容中執行時，產生單一的訊息或交換。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-110">A Send pipeline consumes one or more messages and yields a single message or interchange, again, just as when the pipeline executes in the context of sending a message within BizTalk messaging.</span></span>  
  
## <a name="calling-a-receive-pipeline"></a><span data-ttu-id="7cbe2-111">呼叫接收管線</span><span class="sxs-lookup"><span data-stu-id="7cbe2-111">Calling a Receive Pipeline</span></span>  
 <span data-ttu-id="7cbe2-112">若要呼叫從協調流程內部，應用程式會呼叫接收管線**executereceivepipeline （)** 方法**XLANGPipelineManager**類別。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-112">In order to call a receive pipeline from within an orchestration, the application calls the **ExecuteReceivePipeline()** method of the **XLANGPipelineManager** class.</span></span>  <span data-ttu-id="7cbe2-113">這個方法會使用單一的交換，並傳回零個或多個訊息的集合 (執行個體中包含**ReceivePipelineOutputMessages**類別)。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-113">This method consumes a single interchange and returns a collection of zero or more messages (contained in an instance of the **ReceivePipelineOutputMessages** class).</span></span> <span data-ttu-id="7cbe2-114">這個方法的語法會詳細說明.NET 類別庫參考**XLANGPipelineManager**類別。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-114">The syntax of this method is detailed in the .NET class library reference for the **XLANGPipelineManager** class.</span></span>  
  
 <span data-ttu-id="7cbe2-115">從協調流程內執行接收管線的 API 為：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-115">The API for executing a receive pipeline from within an orchestration is:</span></span>  
  
 `// Execute receive pipeline`  
  
 `static public ReceivePipelineOutputMessages ExecuteReceivePipeline(System.Type receivePipelineType, XLANGMessage msg);`  
  
 <span data-ttu-id="7cbe2-116">通常會完成對接收管線的呼叫**運算式**圖形在協調流程中的。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-116">A call to a receive pipeline would typically be done in an **Expression** shape within the orchestration.</span></span>  
  
 <span data-ttu-id="7cbe2-117">為了從協調流程內部呼叫接收管線，開發人員必須在協調流程專案中參考管線組件。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-117">In order to call a receive pipeline from within an orchestration, the developer must reference the pipeline assembly in the orchestration project.</span></span> <span data-ttu-id="7cbe2-118">以下是呼叫接收管線的協調流程範例：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-118">Following is an example of an orchestration that calls a receive pipeline:</span></span>  
  
 <span data-ttu-id="7cbe2-119">![呼叫接收管線畫面](../core/media/callingreceivepipelinefromorchestration.gif "CallingReceivePipelineFromOrchestration")</span><span class="sxs-lookup"><span data-stu-id="7cbe2-119">![Calling Receive Pipeline screen](../core/media/callingreceivepipelinefromorchestration.gif "CallingReceivePipelineFromOrchestration")</span></span>  
  
 <span data-ttu-id="7cbe2-120">如需更詳細的範例，請參閱 SDK 範例[撰寫訊息處理器 （BizTalk Server 範例）](../core/composed-message-processor-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-120">For a more detailed example, see the SDK sample [Composed Message Processor (BizTalk Server Sample)](../core/composed-message-processor-biztalk-server-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cbe2-121">類型的變數**ReceivePipelineOutputMessages**可以只在協調流程中不可部分完成的範圍內宣告。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-121">A variable of type **ReceivePipelineOutputMessages** can be declared only within an atomic scope in an orchestration.</span></span>  <span data-ttu-id="7cbe2-122">這是因為此類型的變數並未序列化，因此無法在持續的協調流程使用，而在不可部分完成的範圍內執行的協調流程也絕對無法持續。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-122">This is because variables of this type are not serializable and thus would not survive persistence of the orchestration, and orchestrations are never persisted while executing within an atomic scope.</span></span>  <span data-ttu-id="7cbe2-123">這代表接收管線只能在不可部分完成的範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-123">This means that a receive pipeline can be executed only within an atomic scope.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cbe2-124">當呼叫**PassThruReceive**管線或協調流程內的自訂管線元件，您必須宣告內送訊息的變數類型為 System.Xml.XmlDocument，不論內送訊息類型是否為 XML.</span><span class="sxs-lookup"><span data-stu-id="7cbe2-124">When calling **PassThruReceive** pipeline or custom pipeline component from within an orchestration, you must declare the variable type for incoming message as System.Xml.XmlDocument despite of the incoming message type is XML or not.</span></span> <span data-ttu-id="7cbe2-125">因此，如果內送訊息為一般檔案格式訊息的非 XML 訊息，而您嘗試要在其上作業，則可能會遇到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-125">Therefore, you may encounter exception if you try to operate on it if the incoming message is a non-XML message such as a flat file format message.</span></span> <span data-ttu-id="7cbe2-126">這是因為在上述的案例中，該協調流程引擎會對任何類型的內送訊息使用 System.Xml.XmlDocument。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-126">This is because of that orchestration engine intends to use System.Xml.XmlDocument for any type of incoming message in the scenario described above.</span></span>  
  
## <a name="calling-a-send-pipeline"></a><span data-ttu-id="7cbe2-127">呼叫傳送管線</span><span class="sxs-lookup"><span data-stu-id="7cbe2-127">Calling a Send Pipeline</span></span>  
 <span data-ttu-id="7cbe2-128">若要呼叫傳送管線從協調流程，應用程式會呼叫內**executesendpipeline （)** 方法**XLANGPipelineManager**類別。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-128">To call a send pipeline from within an orchestration, the application calls the **ExecuteSendPipeline()** method of the **XLANGPipelineManager** class.</span></span> <span data-ttu-id="7cbe2-129">這個方法會使用一或多個訊息的集合 (執行個體中包含**SendPipelineInputMessages**類別)，並傳回單一的交換。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-129">This method consumes a collection of one or more messages (contained in an instance of the **SendPipelineInputMessages** class) and returns a single interchange.</span></span> <span data-ttu-id="7cbe2-130">這個方法的語法會詳細說明.NET 類別庫參考**XLANGPipelineManager**類別。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-130">The syntax of this method is detailed in the .NET class library reference for the **XLANGPipelineManager** class.</span></span>  <span data-ttu-id="7cbe2-131">因為執行傳送管線會產生新的交易，在呼叫**executesendpipeline （)** 方法必須由訊息指派圖形內，在這種情況：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-131">Because execution of a send pipeline yields a new interchange, the call to **ExecuteSendPipeline()** method must be made within a message assignment shape, as such:</span></span>  
  
 <span data-ttu-id="7cbe2-132">從協調流程內部執行傳送管線的 API 為：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-132">The API for executing a send pipeline from within an orchestration is:</span></span>  
  
 `// Execute a send pipeline`  
  
 `static public ExecuteSendPipeline(System.Type sendPipelineType, SendPipelineInputMessages inputMsgs, XLANGMessage msg);`  
  
 <span data-ttu-id="7cbe2-133">在中，必須完成呼叫傳送管線**訊息指派**圖形在協調流程中的。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-133">A call to a send pipeline must be done in a **Message Assignment** shape within the orchestration.</span></span>  
  
 <span data-ttu-id="7cbe2-134">為了從協調流程內部呼叫傳送管線，開發人員必須在協調流程專案中參考管線組件。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-134">In order to call a send pipeline from within an orchestration, the developer must reference the pipeline assembly in the orchestration project.</span></span>  <span data-ttu-id="7cbe2-135">呼叫傳送管線的協調流程範例：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-135">An example of an orchestration that calls a send pipeline:</span></span>  
  
 <span data-ttu-id="7cbe2-136">![呼叫傳送管線畫面](../core/media/example-callingsendpipelinefromorchestration.gif "Example_CallingSendPipelineFromOrchestration")</span><span class="sxs-lookup"><span data-stu-id="7cbe2-136">![Calling Send Pipeline screen](../core/media/example-callingsendpipelinefromorchestration.gif "Example_CallingSendPipelineFromOrchestration")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cbe2-137">在呼叫預設的 XMLTransmit 管線時，必須將訊息內容屬性 XMLNORM.EnvelopeSpecName 設定為「信封」結構描述的完整格式名稱。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-137">When calling the default XMLTransmit pipeline, you must set the message context property XMLNORM.EnvelopeSpecName to the fully qualified name of the Envelope schema.</span></span> <span data-ttu-id="7cbe2-138">例如：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-138">For example:</span></span>  
>   
>  `MyMessage(XMLNORM.EnvelopeSpecName) = "PipelineSchemas.POEnv, PipelineSchemas, Version=1.0.0.0, Culture=nuetral, PublicKeyToken=12e5cc95621c33e8";`  
  
 <span data-ttu-id="7cbe2-139">如需更詳細的範例，請參閱 SDK 範例[彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-139">For a more detailed example, see the SDK sample [Aggregator (BizTalk Server Sample)](../core/aggregator-biztalk-server-sample.md).</span></span>  
  
## <a name="pipeline-execution---behavioral-differences"></a><span data-ttu-id="7cbe2-140">管線執行 - 行為差異</span><span class="sxs-lookup"><span data-stu-id="7cbe2-140">Pipeline Execution - Behavioral Differences</span></span>  
 <span data-ttu-id="7cbe2-141">由協調流程呼叫傳送或接收管線時，該管線的執行，大致與它在傳訊基礎結構內 (在接收位置或傳送埠上) 執行時相同。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-141">The execution of a send or receive pipeline when called by an orchestration is predominantly the same as when the same pipeline executes within the messaging infrastructure (i.e. at receive location or send port).</span></span>  <span data-ttu-id="7cbe2-142">不過仍有些特定的行為差異，如下所述。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-142">However, there are certain behavioral differences that are noted below.</span></span>  
  
### <a name="differences-within-pipeline-stages"></a><span data-ttu-id="7cbe2-143">管線階段內的差異</span><span class="sxs-lookup"><span data-stu-id="7cbe2-143">Differences Within Pipeline Stages</span></span>  
 <span data-ttu-id="7cbe2-144">從協調流程內呼叫傳送或接收管線時，其階段的執行，幾乎與該管線是從 BizTalk 傳訊基礎結構呼叫時的階段執行相同，例外狀況如下所示。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-144">The execution of the stages within a send or receive pipeline that is called from within an orchestration is nearly identical to the execution of those stages when the pipeline is called from the BizTalk messaging infrastructure, with the exceptions noted by stage below.</span></span>  
  
-   <span data-ttu-id="7cbe2-145">組合器/解譯器： 組合器和解譯器階段不會處理**追蹤設定檔**資料。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-145">Assembler/Disassembler:  The assembler and disassembler stages will not process **Tracking Profile** data.</span></span>  
  
-   <span data-ttu-id="7cbe2-146">編碼器/解碼器： MIME 編碼器以數位方式簽署訊息使用設定在主機與主機相關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-146">Encoder/Decoder:  The MIME encoder digitally signs messages using the certificate configured at the host with which the host is associated.</span></span>  <span data-ttu-id="7cbe2-147">SMIME 編碼器會在傳遞給管線的訊息內容上，使用該憑證來加密訊息。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-147">The SMIME encoder encrypts messages using the certificate on the context of the message passed into the pipeline.</span></span>  
  
### <a name="schema-resolution"></a><span data-ttu-id="7cbe2-148">結構描述解析</span><span class="sxs-lookup"><span data-stu-id="7cbe2-148">Schema Resolution</span></span>  
 <span data-ttu-id="7cbe2-149">從協調流程執行管線時，會支援兩種結構描述尋查演算法。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-149">There are two schema lookup algorithms that are supported when executing a pipeline from an orchestration:</span></span>  
  
-   <span data-ttu-id="7cbe2-150">依型別解析</span><span class="sxs-lookup"><span data-stu-id="7cbe2-150">Resolution by type</span></span>  
  
-   <span data-ttu-id="7cbe2-151">依名稱解析</span><span class="sxs-lookup"><span data-stu-id="7cbe2-151">Resolution by name</span></span>  
  
 <span data-ttu-id="7cbe2-152">如果部署了重複的結構描述，則用於選取適當結構描述的演算法邏輯，與在傳訊基礎結構內容中執行時所使用的邏輯相同。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-152">In cases where duplicate schemas are deployed, the algorithm's logic for selecting the appropriate schema is identical to that used when executing in the context of the messaging infrastructure.</span></span>  
  
### <a name="transactional-pipelines"></a><span data-ttu-id="7cbe2-153">交易管線</span><span class="sxs-lookup"><span data-stu-id="7cbe2-153">Transactional Pipelines</span></span>  
 <span data-ttu-id="7cbe2-154">如果管線的階段會呼叫交易式元件，則該管線沒有可用的交易式內容。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-154">Pipelines whose stages call transactional components will not have a transactional context available.</span></span>  <span data-ttu-id="7cbe2-155">呼叫**ipipelinecontext.gettransaction （)** 將會擲回**NotSupportedException**。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-155">Any call to **IPipelineContext.GetTransaction()** will throw **NotSupportedException**.</span></span>  <span data-ttu-id="7cbe2-156">這樣並不會造成無法從協調流程執行此類管線，但的確代表該管線不必偵測和處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-156">This does not preclude execution of such a pipeline from an orchestration, but it does mean that the pipeline will have to detect and handle this situation.</span></span>  
  
### <a name="message-destination"></a><span data-ttu-id="7cbe2-157">訊息目的地</span><span class="sxs-lookup"><span data-stu-id="7cbe2-157">Message Destination</span></span>  
 <span data-ttu-id="7cbe2-158">在此內容中並不支援依管線元件控制訊息目的地。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-158">Controlling message destination by pipeline components is not supported in this context.</span></span>  <span data-ttu-id="7cbe2-159">設定內容屬性**MessageDestination**或**SuspendOnRoutingFailure**會導致**XLANGPipelineManagerException**擲回。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-159">Setting the context properties **MessageDestination** or **SuspendOnRoutingFailure** will cause an **XLANGPipelineManagerException** to be thrown.</span></span>  
  
### <a name="pipeline-component-types"></a><span data-ttu-id="7cbe2-160">管線元件類型</span><span class="sxs-lookup"><span data-stu-id="7cbe2-160">Pipeline Component Types</span></span>  
 <span data-ttu-id="7cbe2-161">若要從協調流程內呼叫管線元件，則該元件必須以下列項目為基礎：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-161">Pipeline components must be based on the following in order to be called from within an orchestration:</span></span>  
  
-   <span data-ttu-id="7cbe2-162">.NET Framework v1.1</span><span class="sxs-lookup"><span data-stu-id="7cbe2-162">.NET Framework v1.1</span></span>  
  
-   <span data-ttu-id="7cbe2-163">.NET Framework v2.0</span><span class="sxs-lookup"><span data-stu-id="7cbe2-163">.NET Framework v2.0</span></span>  
  
-   <span data-ttu-id="7cbe2-164">.NET Framework v3.0</span><span class="sxs-lookup"><span data-stu-id="7cbe2-164">.NET Framework v3.0</span></span>  
  
-   <span data-ttu-id="7cbe2-165">.NET Framework v3.5</span><span class="sxs-lookup"><span data-stu-id="7cbe2-165">.NET Framework v3.5</span></span>  
  
-   <span data-ttu-id="7cbe2-166">.NET Framework v4.0</span><span class="sxs-lookup"><span data-stu-id="7cbe2-166">.NET Framework v4.0</span></span>  
  
-   <span data-ttu-id="7cbe2-167">.NET Framework v2.0</span><span class="sxs-lookup"><span data-stu-id="7cbe2-167">.NET Framework v2.0</span></span>  
  
-   <span data-ttu-id="7cbe2-168">COM</span><span class="sxs-lookup"><span data-stu-id="7cbe2-168">COM</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="7cbe2-169">限制</span><span class="sxs-lookup"><span data-stu-id="7cbe2-169">Restrictions</span></span>  
 <span data-ttu-id="7cbe2-170">下列類型的管線**無法**從協調流程內執行：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-170">The following types of pipelines **cannot** be executed from within an orchestration:</span></span>  
  
-   <span data-ttu-id="7cbe2-171">交易管線</span><span class="sxs-lookup"><span data-stu-id="7cbe2-171">Transactional pipelines</span></span>  
  
-   <span data-ttu-id="7cbe2-172">可復原管線</span><span class="sxs-lookup"><span data-stu-id="7cbe2-172">Recoverable pipelines</span></span>  
  
-   <span data-ttu-id="7cbe2-173">管線會呼叫 BAM 攔截器 API ( **NotSupportedException**就會擲回)。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-173">Pipelines which call the BAM interceptor API (a **NotSupportedException** will be thrown).</span></span>  
  
-   <span data-ttu-id="7cbe2-174">相同的管線執行個體無法在不同分支的平行圖形中執行，除非是放在每個分支的同步化範圍中。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-174">The same pipeline instance cannot be executed in different branches of the parallel shape unless it is placed in a synchronized scope in every branch.</span></span>  
  
-   <span data-ttu-id="7cbe2-175">根據 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] SDK 所建置的現有管線 (組件)。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-175">Existing pipelines (assemblies) that were built against the [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] SDK.</span></span>  
  
## <a name="failure-modes-and-effects"></a><span data-ttu-id="7cbe2-176">失敗模式和效果</span><span class="sxs-lookup"><span data-stu-id="7cbe2-176">Failure Modes and Effects</span></span>  
 <span data-ttu-id="7cbe2-177">如果因為從 BizTalk Server 傳訊基礎結構內呼叫管線而導致訊息擱置，則該執行管線時的任何失敗都會導致擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-177">Any failure in pipeline execution which would have resulted in a suspended message were this pipeline to be called from within the BizTalk Server Messaging Infrastructure will instead result in an exception being thrown.</span></span>  <span data-ttu-id="7cbe2-178">擲回的例外狀況屬於型別**Microsoft.XLANGs.Pipeline.XLANGPipelineManagerException**。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-178">The exception thrown is of type **Microsoft.XLANGs.Pipeline.XLANGPipelineManagerException**.</span></span>  <span data-ttu-id="7cbe2-179">可在呼叫協調流程中的 Catch 區塊中處理這個擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-179">This thrown exception can be handled in a catch block within the calling orchestration.</span></span>  <span data-ttu-id="7cbe2-180">如果協調流程並未捕捉到擲回的例外狀況，則 XLANGs 引擎會報告錯誤，並在文字中包含擲回例外狀況中的例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-180">If the orchestration does not catch the thrown exception, the XLANGs engine reports an error the text of which includes the exception information in the thrown exception.</span></span>  
  
 <span data-ttu-id="7cbe2-181">例外狀況會對管線元件所產生的錯誤訊息執行格式設定。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-181">The exception performs formatting of the error messages generated by the pipeline components.</span></span>  
  
 <span data-ttu-id="7cbe2-182">**訊息**屬性**XLANGPipelineManagerException**類別包含管線執行錯誤的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-182">The **Message** property of the **XLANGPipelineManagerException** class contains details of the pipeline's execution error.</span></span> <span data-ttu-id="7cbe2-183">此詳細資料會使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-183">This detail is in the following format:</span></span>  
  
-   <span data-ttu-id="7cbe2-184">執行管線失敗\<管線類型\>。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-184">There was a failure executing pipeline \<pipeline type\>.</span></span>  <span data-ttu-id="7cbe2-185">錯誤詳細資料\<格式化的錯誤訊息\>。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-185">Error details \<formatted error message\>.</span></span>  
  
 <span data-ttu-id="7cbe2-186">在此訊息中，\<管線類型\>是管線類型的名稱和\<格式化的錯誤訊息\>管線執行期間發生之特定失敗的描述。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-186">In this message, \<pipeline type\> is the name of the pipeline class and \<formatted error message\> is a description of the specific failure that occurred during pipeline execution.</span></span>  
  
 <span data-ttu-id="7cbe2-187">例如，如果協調流程呼叫接收管線，而該管線執行失敗，因為沒有任何管線元件可辨識訊息的值**XLANGPipelineManagerException**的屬性會是：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-187">For example, if an orchestration calls a receive pipeline and that pipeline's execution fails because none of the pipeline's components recognizes the message, the values of the **XLANGPipelineManagerException**'s properties would be:</span></span>  
  
|<span data-ttu-id="7cbe2-188">XLANGPipelineManagerException 屬性</span><span class="sxs-lookup"><span data-stu-id="7cbe2-188">XLANGPipelineManagerException property</span></span>|<span data-ttu-id="7cbe2-189">值</span><span class="sxs-lookup"><span data-stu-id="7cbe2-189">Value</span></span>|  
|--------------------------------------------|-----------|  
|<span data-ttu-id="7cbe2-190">訊息</span><span class="sxs-lookup"><span data-stu-id="7cbe2-190">Message</span></span>|<span data-ttu-id="7cbe2-191">執行接收管線 "MyPipelines.ReceivePipeline" 失敗。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-191">There was a failure executing the receive pipeline "MyPipelines.ReceivePipeline".</span></span> <span data-ttu-id="7cbe2-192">錯誤詳細資料: 「 沒有解譯階段元件可辨識資料。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-192">Error details: "No Disassemble stage components can recognize the data.</span></span>|  
|<span data-ttu-id="7cbe2-193">元件</span><span class="sxs-lookup"><span data-stu-id="7cbe2-193">Component</span></span>|<span data-ttu-id="7cbe2-194">String.Empty</span><span class="sxs-lookup"><span data-stu-id="7cbe2-194">String.Empty</span></span>|  
  
 <span data-ttu-id="7cbe2-195">另舉一例，如果協調流程呼叫傳送管線，而該管線執行失敗，因為驗證失敗中的文字**訊息**屬性**XLANGPipelineManagerException**會是：</span><span class="sxs-lookup"><span data-stu-id="7cbe2-195">As another example, if an orchestration calls a send pipeline and that pipeline's execution fails because there is a validation failure, the text in the **Message** property of **XLANGPipelineManagerException** would be:</span></span>  
  
|<span data-ttu-id="7cbe2-196">XLANGPipelineManagerException 屬性</span><span class="sxs-lookup"><span data-stu-id="7cbe2-196">XLANGPipelineManagerException property</span></span>|<span data-ttu-id="7cbe2-197">值</span><span class="sxs-lookup"><span data-stu-id="7cbe2-197">Value</span></span>|  
|--------------------------------------------|-----------|  
|<span data-ttu-id="7cbe2-198">訊息</span><span class="sxs-lookup"><span data-stu-id="7cbe2-198">Message</span></span>|<span data-ttu-id="7cbe2-199">執行傳送管線 "MyPipelines.SendPipeline" 失敗。</span><span class="sxs-lookup"><span data-stu-id="7cbe2-199">There was a failure executing the send pipeline "MyPipelines.SendPipeline".</span></span>  <span data-ttu-id="7cbe2-200">錯誤詳細資料: 「 無法驗證文件:"\<項目名稱\>元素無效-值\<元素值\>無效根據其資料類型為 'String' 的條件約束模式失敗。""</span><span class="sxs-lookup"><span data-stu-id="7cbe2-200">Error details:  "Failed to validate the document: "The \<element name\> element is invalid - The value \<element value\> is invalid according to its datatype 'String' - The Pattern constraint failed.""</span></span>|  
|<span data-ttu-id="7cbe2-201">元件</span><span class="sxs-lookup"><span data-stu-id="7cbe2-201">Component</span></span>|<span data-ttu-id="7cbe2-202">“Microsoft.BizTalk.Component.XmlValidator”</span><span class="sxs-lookup"><span data-stu-id="7cbe2-202">“Microsoft.BizTalk.Component.XmlValidator”</span></span>|