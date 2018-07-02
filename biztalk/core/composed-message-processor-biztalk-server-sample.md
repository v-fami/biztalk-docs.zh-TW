---
title: 撰寫訊息處理器 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, examples
- messages, processing
- messages, aggregated
- examples, pipelines
ms.assetid: a0f87f98-6f5f-4edb-8f65-49d22df5de97
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d884fba7d19e26613c457ed5789f847a5c23babc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969207"
---
# <a name="composed-message-processor-biztalk-server-sample"></a><span data-ttu-id="a3a24-102">撰寫訊息處理器 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="a3a24-102">Composed Message Processor (BizTalk Server Sample)</span></span>
<span data-ttu-id="a3a24-103">此範例的目的是建置撰寫訊息處理器應用程式，可處理來自彙總訊息的個別明細項目。</span><span class="sxs-lookup"><span data-stu-id="a3a24-103">The purpose of this sample is to build a composed message processor application that processes individual line items from aggregated messages.</span></span>  
  
 <span data-ttu-id="a3a24-104">具體而言，我們建置的協調流程排程會：</span><span class="sxs-lookup"><span data-stu-id="a3a24-104">Specifically we will build an orchestration schedule that:</span></span>  
  
1. <span data-ttu-id="a3a24-105">接收包含多筆訂單的批次交換訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-105">Receives a batched interchange message consisting of multiple purchase orders.</span></span>  
  
2. <span data-ttu-id="a3a24-106">將交換訊息解譯為個別訂單文件。</span><span class="sxs-lookup"><span data-stu-id="a3a24-106">Disassembles the interchange message into individual purchase order documents.</span></span>  
  
3. <span data-ttu-id="a3a24-107">處理每份文件，將每筆訂單轉換為發票訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-107">Processes each document – converts each purchase order into an invoice message.</span></span>  
  
4. <span data-ttu-id="a3a24-108">將所有發票訊息組合為一個批次交換。</span><span class="sxs-lookup"><span data-stu-id="a3a24-108">Assembles all the invoice messages into a batched interchange.</span></span>  
  
   <span data-ttu-id="a3a24-109">步驟 3 已經過簡化供範例使用。</span><span class="sxs-lookup"><span data-stu-id="a3a24-109">Step #3 is simplified for the sample purposes.</span></span> <span data-ttu-id="a3a24-110">例如，在更複雜的應用程式中，協調流程可能會將解譯的訂單傳送至不同的後端庫存系統，然後在收集所有回應後，再將它們彙總為一個批次發票訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-110">For example, in more complex applications, an orchestration may send disassembled purchase orders to different back-end inventory systems and then after collecting all the responses, aggregate them into one batched invoice message.</span></span>  
  
   <span data-ttu-id="a3a24-111">如需撰寫訊息處理器模式的詳細資訊，請參閱 [1]。</span><span class="sxs-lookup"><span data-stu-id="a3a24-111">For more information on the composed message processor pattern refer to [1].</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="a3a24-112">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="a3a24-112">What This Sample Does</span></span>  
 <span data-ttu-id="a3a24-113">範例解決方案內有兩種專案，將在以下章節中詳細描述。</span><span class="sxs-lookup"><span data-stu-id="a3a24-113">There are two projects within the sample solution, both of which are described in detail in the following sections.</span></span>  
  
### <a name="pipelines-and-schemas"></a><span data-ttu-id="a3a24-114">管線和結構描述</span><span class="sxs-lookup"><span data-stu-id="a3a24-114">Pipelines and Schemas</span></span>  
 <span data-ttu-id="a3a24-115">管線和結構描述專案包含：</span><span class="sxs-lookup"><span data-stu-id="a3a24-115">Pipelines and schemas project contains:</span></span>  
  
-   <span data-ttu-id="a3a24-116">輸入訂單交換和輸出發票交換所用的一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="a3a24-116">Flat file schemas for input purchase order interchange and for output invoice interchange.</span></span>  
  
-   <span data-ttu-id="a3a24-117">將訂單文件轉換為發票文件的對應。</span><span class="sxs-lookup"><span data-stu-id="a3a24-117">Map to transform purchase order document into an invoice document.</span></span>  
  
-   <span data-ttu-id="a3a24-118">接收管線和傳送管線。</span><span class="sxs-lookup"><span data-stu-id="a3a24-118">Receive and send pipelines.</span></span>  
  
#### <a name="flat-file-schemas-for-input-and-output-interchanges"></a><span data-ttu-id="a3a24-119">輸入交換和輸出交換所用的一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="a3a24-119">Flat File Schemas For Input and Output Interchanges</span></span>  
 <span data-ttu-id="a3a24-120">我們的範例應用程式會搭配一般檔案格式的交換使用。</span><span class="sxs-lookup"><span data-stu-id="a3a24-120">Our sample application will be working with the interchanges in the flat file format.</span></span> <span data-ttu-id="a3a24-121">以下是訂單交換和發票交換的範例：</span><span class="sxs-lookup"><span data-stu-id="a3a24-121">Below are the examples of the purchase order interchange and invoice interchange:</span></span>  
  
 <span data-ttu-id="a3a24-122">訂單交換 (CMPInput.txt)：</span><span class="sxs-lookup"><span data-stu-id="a3a24-122">Purchase order interchange (CMPInput.txt):</span></span>  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
PO1999-10-21  
US    John Dow       123 Elm Street      Mill Valley    CA 90952  
US    July Dow       8 Pine Avenue       Old Town       PA 95819  
Please ship it urgent!  
ITEMS,ITEM398-BB|Tire|4|324.99|Wrap them up nicely,ITEM201-BB|Engine Oil|1|12.99|SAE10W30|1999-05-22  
PO1999-10-23  
US    John Connor    123 Cedar Street    Mill Valley    CA 90952  
US    Sarah Connor   8 Grass Avenue      Old Town       PA 95819  
Use cheapest shipping method.  
ITEMS,ITEM101-TT|Plastic flowers|10|4.99|Fragile handle with care,ITEM202-RR|Fertilizer|1|10.99|Lawn fertilizer,ITEM453-XS|Weed killer|1|5.99|Lawn weed killer|1999-05-25  
```  
  
 <span data-ttu-id="a3a24-123">交換或訂單文件的標頭，都會識別其包含的文件類型：</span><span class="sxs-lookup"><span data-stu-id="a3a24-123">The interchange, or purchase order document, has a header that identifies what type of the documents it contains:</span></span>  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
```  
  
 <span data-ttu-id="a3a24-124">此交換包含三筆訂單文件。</span><span class="sxs-lookup"><span data-stu-id="a3a24-124">This interchange consist of three purchase order documents.</span></span> <span data-ttu-id="a3a24-125">一個執行個體會包含以下資訊。</span><span class="sxs-lookup"><span data-stu-id="a3a24-125">One instance consists of the information shown below.</span></span> <span data-ttu-id="a3a24-126">如您所見，其包含帳單地址和送貨地址以及所訂購項目的清單之類的資訊。</span><span class="sxs-lookup"><span data-stu-id="a3a24-126">As you can see, it contains such information as address for billing and shipping as well as the list of items that were ordered.</span></span>  
  
```  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
```  
  
 <span data-ttu-id="a3a24-127">我們要為此產生的發票交換應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3a24-127">The invoice interchange we want to generate for this should look like the following:</span></span>  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
INVOICE1999-10-21  
BILLTO,US,John Dow,123 Elm Street,Mill Valley,CA,90952  
398-BB    Tire              4    324.99    Wrap them up nicely  
201-BB    Engine Oil        1    12.99     SAE10W30  
INVOICE1999-10-20  
BILLTO,US,John Connor,123 Cedar Street,Mill Valley,CA,90952  
101-TT    Plastic flowers   10   4.99      Fragile handle with care  
202-RR    Fertilizer        1    10.99     Lawn fertilizer  
453-XS    Weed killer       1    5.99      Lawn weed killer  
```  
  
 <span data-ttu-id="a3a24-128">此交換包含訂單交換內的資訊子集，且交換的格式與標頭的格式不同。</span><span class="sxs-lookup"><span data-stu-id="a3a24-128">This interchange contains a subset of information that was in purchase order interchange and also the format of the interchange as well as format of the header are different.</span></span>  
  
 <span data-ttu-id="a3a24-129">標頭如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3a24-129">The header is as follows:</span></span>  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
```  
  
 <span data-ttu-id="a3a24-130">文件執行個體包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="a3a24-130">And the document instance includes the following:</span></span>  
  
```  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
```  
  
 <span data-ttu-id="a3a24-131">首先必須建立一般檔案結構描述，用於：</span><span class="sxs-lookup"><span data-stu-id="a3a24-131">First thing we need to create flat file schemas for:</span></span>  
  
- <span data-ttu-id="a3a24-132">訂單文件 (PO.xsd)</span><span class="sxs-lookup"><span data-stu-id="a3a24-132">Purchase order document (PO.xsd)</span></span>  
  
- <span data-ttu-id="a3a24-133">發票文件 (Invoice.xsd)</span><span class="sxs-lookup"><span data-stu-id="a3a24-133">Invoice document (Invoice.xsd)</span></span>  
  
- <span data-ttu-id="a3a24-134">訂單標頭 (POHeader.xsd)</span><span class="sxs-lookup"><span data-stu-id="a3a24-134">Purchase order header (POHeader.xsd)</span></span>  
  
- <span data-ttu-id="a3a24-135">發票標頭 (InvoiceHeader.xsd)</span><span class="sxs-lookup"><span data-stu-id="a3a24-135">Invoice header (InvoiceHeader.xsd)</span></span>  
  
  <span data-ttu-id="a3a24-136">針對這個範例，我們不會解釋建立一般文件結構描述的程序。</span><span class="sxs-lookup"><span data-stu-id="a3a24-136">For this sample, we are not going to explain the process of creating flat file schemas.</span></span> <span data-ttu-id="a3a24-137">若要學習如何從文件執行個體建立一般文件結構描述，請參閱＜從文件執行個體建立一般檔案結構描述＞文件章節。</span><span class="sxs-lookup"><span data-stu-id="a3a24-137">To learn how to create flat file schemas from document instances, refer to the "Creating flat file schemas from document instance" documentation section.</span></span>  
  
#### <a name="map-to-transform-purchase-order-document-into-invoice-document"></a><span data-ttu-id="a3a24-138">將訂單文件轉換為發票文件的對應</span><span class="sxs-lookup"><span data-stu-id="a3a24-138">Map to Transform Purchase Order Document Into Invoice Document</span></span>  
 <span data-ttu-id="a3a24-139">將訂單執行個體轉換為發票文件的對應 (PO2Invoice.btm)。</span><span class="sxs-lookup"><span data-stu-id="a3a24-139">The map (PO2Invoice.btm) transforms an instance of the purchase order into an invoice document.</span></span>  
  
#### <a name="receive-and-send-pipelines"></a><span data-ttu-id="a3a24-140">接收管線和傳送管線</span><span class="sxs-lookup"><span data-stu-id="a3a24-140">Receive and Send Pipelines</span></span>  
 <span data-ttu-id="a3a24-141">接收管線 (FFReceivePipeline.btp) 包含用於處理訂單交換的一般檔案解譯器元件。</span><span class="sxs-lookup"><span data-stu-id="a3a24-141">The receive pipeline (FFReceivePipeline.btp) contains a flat file disassembler component that is used to process a purchase order interchange.</span></span> <span data-ttu-id="a3a24-142">尤其是針對 CMPInput.txt 檔案內的交換，它會移除交換標頭，並產生三份對應至三筆訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a3a24-142">In particular, for the interchange in file CMPInput.txt, it removes the interchange header and produces three XML documents corresponding to three purchase orders.</span></span>  
  
 <span data-ttu-id="a3a24-143">接收管線內一般檔案解譯器的設定如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3a24-143">The flat file disassembler in the receive pipeline is configured as shown:</span></span>  
  
- <span data-ttu-id="a3a24-144">**文件結構描述：** 屬於 PipelinesAndSchemas.PO</span><span class="sxs-lookup"><span data-stu-id="a3a24-144">**Document schema:** PipelinesAndSchemas.PO</span></span>  
  
- <span data-ttu-id="a3a24-145">**標頭結構描述：** PipelinesAndSchemas.POHeader</span><span class="sxs-lookup"><span data-stu-id="a3a24-145">**Header schema:** PipelinesAndSchemas.POHeader</span></span>  
  
- <span data-ttu-id="a3a24-146">**保留標頭：** False</span><span class="sxs-lookup"><span data-stu-id="a3a24-146">**Preserve header:** False</span></span>  
  
- <span data-ttu-id="a3a24-147">**可復原交換：** False</span><span class="sxs-lookup"><span data-stu-id="a3a24-147">**Recoverable interchange:** False</span></span>  
  
- <span data-ttu-id="a3a24-148">**結尾結構描述：** （無）</span><span class="sxs-lookup"><span data-stu-id="a3a24-148">**Trailer schema:** (None)</span></span>  
  
- <span data-ttu-id="a3a24-149">**驗證文件結構：** False</span><span class="sxs-lookup"><span data-stu-id="a3a24-149">**Validate document structure:** False</span></span>  
  
  <span data-ttu-id="a3a24-150">傳送管線 (FFSendPipeline.btp) 包含用於建立彙總發票交換的一般檔案組合器元件。</span><span class="sxs-lookup"><span data-stu-id="a3a24-150">The send pipeline (FFSendPipeline.btp) contains a flat file assembler component that is used to create aggregated invoice interchange.</span></span>  
  
  <span data-ttu-id="a3a24-151">傳送管線內一般檔案組合器的設定如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3a24-151">The flat file assembler in send pipeline is configured as shown:</span></span>  
  
- <span data-ttu-id="a3a24-152">**文件結構描述：** PipelinesandSchemas.Invoice</span><span class="sxs-lookup"><span data-stu-id="a3a24-152">**Document schema:** PipelinesandSchemas.Invoice</span></span>  
  
- <span data-ttu-id="a3a24-153">**標頭結構描述：** PipelinesAndSchemas.InvoiceHeader</span><span class="sxs-lookup"><span data-stu-id="a3a24-153">**Header schema:** PipelinesAndSchemas.InvoiceHeader</span></span>  
  
- <span data-ttu-id="a3a24-154">**保留位元順序標記：** False</span><span class="sxs-lookup"><span data-stu-id="a3a24-154">**Preserve byte order mark:** False</span></span>  
  
- <span data-ttu-id="a3a24-155">**目標字元集：** （無）</span><span class="sxs-lookup"><span data-stu-id="a3a24-155">**Target charset:** (None)</span></span>  
  
- <span data-ttu-id="a3a24-156">**結尾結構描述：** （無）</span><span class="sxs-lookup"><span data-stu-id="a3a24-156">**Trailer schema:** (None)</span></span>  
  
### <a name="orchestration-schedule"></a><span data-ttu-id="a3a24-157">協調流程排程</span><span class="sxs-lookup"><span data-stu-id="a3a24-157">Orchestration Schedule</span></span>  
 <span data-ttu-id="a3a24-158">協調流程排程 (CMP.odx) 就是所有主要處理發生的位置。</span><span class="sxs-lookup"><span data-stu-id="a3a24-158">Orchestration schedule (CMP.odx) is where all the main processing happens.</span></span> <span data-ttu-id="a3a24-159">尤其會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a3a24-159">Specifically the following actions are performed:</span></span>  
  
-   <span data-ttu-id="a3a24-160">執行接收管線以解譯訂單交換</span><span class="sxs-lookup"><span data-stu-id="a3a24-160">Receive pipeline is executed to disassemble purchase order interchange</span></span>  
  
-   <span data-ttu-id="a3a24-161">轉換接收管線的每個輸出訊息</span><span class="sxs-lookup"><span data-stu-id="a3a24-161">Every output message of receive pipeline is transformed</span></span>  
  
-   <span data-ttu-id="a3a24-162">執行傳送管線以組合發票交換</span><span class="sxs-lookup"><span data-stu-id="a3a24-162">Send pipeline is executed to assemble an invoice interchange</span></span>  
  
#### <a name="creating-orchestration-schedule-and-defining-global-variables"></a><span data-ttu-id="a3a24-163">建立協調流程排程和定義全域變數</span><span class="sxs-lookup"><span data-stu-id="a3a24-163">Creating Orchestration Schedule and Defining Global Variables</span></span>  
 <span data-ttu-id="a3a24-164">我們的協調流程會接收一般檔案交換做為輸入，傳送一般檔案交換做為輸出。</span><span class="sxs-lookup"><span data-stu-id="a3a24-164">Our orchestration will receive a flat file interchange as an input and will send a flat file interchange as an output.</span></span> <span data-ttu-id="a3a24-165">因此我們必須將輸入訊息和輸出訊息 (分別稱為 InputInterchange 和 OutputInterchange) 定義為無從驗證的型別 (也就是 System.Xml.XmlDocument 型別)。</span><span class="sxs-lookup"><span data-stu-id="a3a24-165">Because of that, we need to define input and output messages (called InputInterchange and OutputInterchange respectively) as type agnostic (i.e. having type of System.Xml.XmlDocument).</span></span>  
  
 <span data-ttu-id="a3a24-166">另外，還必須定義不可部分完成的範圍，我們將在此範圍處理訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-166">Also, we need to define an atomic scope where we will process messages.</span></span> <span data-ttu-id="a3a24-167">這是必要的，因為接收管線可以在不可部分完成的範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="a3a24-167">This is required because the receive pipeline can be executed within atomic scope.</span></span>  
  
#### <a name="executing-receive-pipeline"></a><span data-ttu-id="a3a24-168">執行接收管線</span><span class="sxs-lookup"><span data-stu-id="a3a24-168">Executing Receive Pipeline</span></span>  
 <span data-ttu-id="a3a24-169">下一步我們會新增邏輯，以便執行協調流程中所接收之訊息的接收管線。</span><span class="sxs-lookup"><span data-stu-id="a3a24-169">As a next step, we will add logic to execute a receive pipeline for the message that was received in orchestration.</span></span> <span data-ttu-id="a3a24-170">若要執行這項操作，首先必須在範圍內宣告 Microsoft.XLANGs.Pipeline.ReceivePipelineOutputMessages 型別的變數 (稱為 RcvPipeOutput)。</span><span class="sxs-lookup"><span data-stu-id="a3a24-170">To do this, first we declare a variable (called RcvPipeOutput) of type Microsoft.XLANGs.Pipeline.ReceivePipelineOutputMessages within the scope.</span></span> <span data-ttu-id="a3a24-171">此變數是允許我們循環接收管線輸出訊息的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a3a24-171">This variable is an enumerator that allows us to cycle through the receive pipeline output messages.</span></span> <span data-ttu-id="a3a24-172">請注意，為了存取此型別及執行來自協調流程之管線的其他型別，必須新增對下列組件的參考：</span><span class="sxs-lookup"><span data-stu-id="a3a24-172">Note that in order to access this type, as well as all the other types for execution of pipelines from orchestration, you need to add references to the following assemblies:</span></span>  
  
- <span data-ttu-id="a3a24-173">Microsoft.XLANGs.Pipeline.dll</span><span class="sxs-lookup"><span data-stu-id="a3a24-173">Microsoft.XLANGs.Pipeline.dll</span></span>  
  
- <span data-ttu-id="a3a24-174">Microsoft.BizTalk.Pipeline.dll：</span><span class="sxs-lookup"><span data-stu-id="a3a24-174">Microsoft.BizTalk.Pipeline.dll</span></span>  
  
  <span data-ttu-id="a3a24-175">接收管線不一定都能成功執行。</span><span class="sxs-lookup"><span data-stu-id="a3a24-175">There is no guarantee that the receive pipeline will always execute successfully.</span></span> <span data-ttu-id="a3a24-176">有時候訊息可能格式不正確，導致管線處理失敗。</span><span class="sxs-lookup"><span data-stu-id="a3a24-176">Sometimes messages may be malformed, which would cause the pipeline processing to fail.</span></span> <span data-ttu-id="a3a24-177">管線在協調流程執行失敗時，就有可攔截之擲回的例外狀況，且可執行錯誤處理邏輯。</span><span class="sxs-lookup"><span data-stu-id="a3a24-177">When a pipeline fails execution in the orchestration, there is an exception thrown that can be caught and the error handling logic can be performed.</span></span> <span data-ttu-id="a3a24-178">為了攔截管線所擲回的例外狀況，我們必須以例外狀況處理在非不可部分完成範圍內執行管線。</span><span class="sxs-lookup"><span data-stu-id="a3a24-178">In order for us to catch the exception thrown by pipeline, we need to execute the pipeline within a non-atomic scope with an exception handling.</span></span> <span data-ttu-id="a3a24-179">執行管線的實際程式碼是該範圍內從「運算式」圖形叫用。</span><span class="sxs-lookup"><span data-stu-id="a3a24-179">The actual code to execute pipeline is invoked from an expression shape within that scope.</span></span>  
  
  <span data-ttu-id="a3a24-180">在 ExecuteRcvPipe「運算式」圖形內，寫入下列這行執行接收管線的程式碼：</span><span class="sxs-lookup"><span data-stu-id="a3a24-180">In the ExecuteRcvPipe expression shape, write the following line of code to execute the receive pipeline:</span></span>  
  
```  
RcvPipeOutput = Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteReceivePipeline(typeof(PipelinesAndSchemas.FFReceivePipeline), InputInterchange);  
```  
  
 <span data-ttu-id="a3a24-181">我們來以更詳細的方式分析這行程式碼。</span><span class="sxs-lookup"><span data-stu-id="a3a24-181">Let's analyze this line of code in more detail.</span></span> <span data-ttu-id="a3a24-182">如您所見，我們呼叫了 ExecuteReceivePipeline 靜態方法，該方法會將參數當成要執行的接收管線類型和輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-182">As you can see, we call a static method ExecuteReceivePipeline that takes as a parameter a type of receive pipeline to execute and an input message.</span></span> <span data-ttu-id="a3a24-183">因此會產生含輸出訊息集的列舉器物件。</span><span class="sxs-lookup"><span data-stu-id="a3a24-183">As a result, it produces an enumerator object with the set of output messages.</span></span> <span data-ttu-id="a3a24-184">結果會被指派為 ReceivePipelineOutputMessages 型別的變數，該型別先前已經在此範圍內加以定義了。</span><span class="sxs-lookup"><span data-stu-id="a3a24-184">The result is assigned to a variable of type ReceivePipelineOutputMessages that was defined in this scope before.</span></span>  
  
 <span data-ttu-id="a3a24-185">我們還針對這個管線執行範圍加入了例外狀況處理區塊。</span><span class="sxs-lookup"><span data-stu-id="a3a24-185">We have also included an exception handling block for the pipeline execution scope.</span></span> <span data-ttu-id="a3a24-186">此區塊會攔截 XLANGPipelineManagerException 型別的例外狀況，接著為了簡化起見，直接終止含自訂錯誤訊息的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3a24-186">This block catches the exception of type XLANGPipelineManagerException and then for simplicity reasons just terminates an orchestration instance with customized error message.</span></span>  
  
 <span data-ttu-id="a3a24-187">在更複雜的案例中，可以在此執行其他錯誤處理，例如產生錯誤通知訊息，然後用電子郵件將它傳送給商務使用者或系統管理員。</span><span class="sxs-lookup"><span data-stu-id="a3a24-187">In more complex scenarios, additional error handling can be performed here, such as generation or the error notification message and sending it to a business user or administrator using email.</span></span>  
  
#### <a name="transforming-pipeline-output-messages"></a><span data-ttu-id="a3a24-188">轉換管線輸出訊息</span><span class="sxs-lookup"><span data-stu-id="a3a24-188">Transforming Pipeline Output Messages</span></span>  
 <span data-ttu-id="a3a24-189">我們執行管線並產生解譯訊息集後，必須將每則輸出訊息轉換為不同的格式。</span><span class="sxs-lookup"><span data-stu-id="a3a24-189">After the pipeline has been executed and the set of disassembled messages has been produced, we need to transform each output message into a different format.</span></span>  
  
 <span data-ttu-id="a3a24-190">若要在協調流程中使用轉換，我們必須定義轉換輸入和轉換輸出這兩種訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-190">To use transformation in orchestration we need to define two messages – transformation input and output.</span></span> <span data-ttu-id="a3a24-191">我們會在不可部分完成的範圍內定義那些訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-191">We will define those messages within the atomic scope.</span></span> <span data-ttu-id="a3a24-192">名為 TmpMessageIn 的轉換輸入訊息將屬於 PipelinesAndSchemas.PO 型別。</span><span class="sxs-lookup"><span data-stu-id="a3a24-192">The transformation input message called TmpMessageIn will be of type PipelinesAndSchemas.PO.</span></span> <span data-ttu-id="a3a24-193">名為 TmpMessageOut 的轉換輸出訊息則屬於 PipeliensAndSchemas.Invoice 型別。</span><span class="sxs-lookup"><span data-stu-id="a3a24-193">The transformation output message called TmpMessageOut will be of type PipeliensAndSchemas.Invoice.</span></span> <span data-ttu-id="a3a24-194">我們會套用 PipelinesAndSchemas 專案中所定義的 PO2Invoice.btm 對應。</span><span class="sxs-lookup"><span data-stu-id="a3a24-194">We will apply the map PO2Invoice.btm that is defined in project PipelinesAndSchemas.</span></span>  
  
 <span data-ttu-id="a3a24-195">如果要對應各管線輸出訊息，我們必須在迴圈中執行轉換。</span><span class="sxs-lookup"><span data-stu-id="a3a24-195">As we want to map each pipeline output message we need to perform transformation in the loop.</span></span> <span data-ttu-id="a3a24-196">我們會使用具下列結束條件的「迴圈」圖形：</span><span class="sxs-lookup"><span data-stu-id="a3a24-196">We will use a loop shape with the condition for exiting as below:</span></span>  
  
```  
RcvPipeOutput.MoveNext()  
```  
  
 <span data-ttu-id="a3a24-197">MoveNext() 方法是 IEnumerator .NET 介面的標準方法，允許在管線輸出訊息的集合內移動。</span><span class="sxs-lookup"><span data-stu-id="a3a24-197">MoveNext() method is a standard method of IEnumerator .NET interface that allows to move within the collection of pipeline output messages.</span></span> <span data-ttu-id="a3a24-198">當它到達集合的結尾時，會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="a3a24-198">When it reaches the end of collection it returns false.</span></span>  
  
 <span data-ttu-id="a3a24-199">第一個「建構」圖形會用來從管線輸出訊息，建構 TmpMessageIn 協調流程訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-199">The first construct shape is used to construct an orchestration message TmpMessageIn out of the pipeline output message.</span></span>  
  
 <span data-ttu-id="a3a24-200">「建構」圖形內的程式碼：</span><span class="sxs-lookup"><span data-stu-id="a3a24-200">The code in the construct shape:</span></span>  
  
```  
TmpMessageIn = null;  
RcvPipeOutput.GetCurrent(TmpMessageIn);  
```  
  
 <span data-ttu-id="a3a24-201">在此程式碼中，我們會先初始化協調流程訊息為空值，然後將它自管線輸出訊息集合設定為目前的訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-201">In this code we first initialize orchestration message to null and then set it to the current message from the pipeline output messages collection.</span></span>  
  
 <span data-ttu-id="a3a24-202">在第二個「建構」圖形中，會實際執行 TmpMessageIn 的轉換，並建構 PipelinesAndSchemas.Invoice 型別的 TmpMessageOut。</span><span class="sxs-lookup"><span data-stu-id="a3a24-202">In second construct shape the actual transformation of the TmpMessageIn is performed and the TmpMessageOut of type PipelinesAndSchemas.Invoice is constructed.</span></span>  
  
#### <a name="executing-send-pipeline"></a><span data-ttu-id="a3a24-203">執行傳送管線</span><span class="sxs-lookup"><span data-stu-id="a3a24-203">Executing Send Pipeline</span></span>  
 <span data-ttu-id="a3a24-204">協調流程中的最後一個處理步驟，就是執行一般檔案傳送管線，將所有轉換的 xml 訊息組合為一個一般檔案交換。</span><span class="sxs-lookup"><span data-stu-id="a3a24-204">Last processing step in orchestration is to execute flat file send pipeline to assemble all the transformed xml messages into one flat file interchange.</span></span>  
  
 <span data-ttu-id="a3a24-205">為了執行傳送管線，我們必須使用 Microsoft.XLANGs.Pipeline.SendPipelineInputMessages 型別之名為 SendPipeInput 的變數，該變數會保存需要在傳送管線內處理的協調流程訊息集合。</span><span class="sxs-lookup"><span data-stu-id="a3a24-205">In order to execute a send pipeline we need to use a variable of type Microsoft.XLANGs.Pipeline.SendPipelineInputMessages called SendPipeInput that will hold a collection of orchestration messages that need to be processed in a send pipeline.</span></span>  
  
 <span data-ttu-id="a3a24-206">我們會在執行轉換之迴圈內的最後一個運算式中寫入程式碼，將每則轉換的訊息加入至傳送管線的訊息集合。</span><span class="sxs-lookup"><span data-stu-id="a3a24-206">In the last expression of the loop where we performed transformation we will write a code that will add each transformed message to a message collection for send pipeline:</span></span>  
  
```  
SendPipeInput.Add(TmpMessageOut);  
```  
  
 <span data-ttu-id="a3a24-207">與執行接收管線的方式類似，用來執行傳送管線的程式碼，會放在具例外狀況處理區塊的非不可部分完成的範圍內。</span><span class="sxs-lookup"><span data-stu-id="a3a24-207">Similar to the part where we execute receive pipeline the code for execution of send pipeline is placed within a non-atomic scope with exception handling block.</span></span> <span data-ttu-id="a3a24-208">傳送管線執行程式碼位在建構區塊的「訊息指派」圖形內。</span><span class="sxs-lookup"><span data-stu-id="a3a24-208">The send pipeline execution code is located in the message assignment shape of the construct block.</span></span>  
  
```  
OutputInterchange = null;  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(typeof(PipelinesAndSchemas.FFSendPipeline), SendPipeInput, OutputInterchange);  
```  
  
 <span data-ttu-id="a3a24-209">建構區塊是用於建構無從驗證的型別 (也就是 System.Xml.XmlDocument) 管線輸出訊息 OutputInterchange。</span><span class="sxs-lookup"><span data-stu-id="a3a24-209">The construct block is used to construct type agnostic (i.e. System.Xml.XmlDocument) pipeline output message OutputInterchange.</span></span> <span data-ttu-id="a3a24-210">接著，在「訊息指派」圖形內，新建構的訊息會初始化為 null。</span><span class="sxs-lookup"><span data-stu-id="a3a24-210">Then in the message assignment shape the newly constructed message is initialized to null.</span></span> <span data-ttu-id="a3a24-211">然後，就會叫用 ExecuteSendPipeline 靜態方法執行傳送管線。</span><span class="sxs-lookup"><span data-stu-id="a3a24-211">After that the static method ExecuteSendPipeline is invoked to execute a send pipeline.</span></span> <span data-ttu-id="a3a24-212">該方法會將參數當成要執行的傳送管線類型、輸入訊息，及對儲存管線輸出之輸出訊息的參考。</span><span class="sxs-lookup"><span data-stu-id="a3a24-212">This method takes as a parameter a type of the send pipeline to execute, the input message and the reference to output message where the pipeline output will be stored.</span></span>  
  
 <span data-ttu-id="a3a24-213">與執行接收管線的方式類似，管線執行範圍也會有例外狀況處理區塊。</span><span class="sxs-lookup"><span data-stu-id="a3a24-213">As with the execution of the receive pipeline, here we also have an exception handling block for the pipeline execution scope.</span></span> <span data-ttu-id="a3a24-214">此區塊會攔截 XLANGPipelineManagerException 型別的例外狀況，接著為了簡化起見，直接終止含自訂錯誤訊息的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3a24-214">This block catches the exception of type XLANGPipelineManagerException and then for simplicity reasons just terminates an orchestration instance with customized error message.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="a3a24-215">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="a3a24-215">Where to Find This Sample</span></span>  
 <span data-ttu-id="a3a24-216">下表列出此範例使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="a3a24-216">The following table lists the files for this sample.</span></span>  
  
|<span data-ttu-id="a3a24-217">檔案</span><span class="sxs-lookup"><span data-stu-id="a3a24-217">File(s)</span></span>|<span data-ttu-id="a3a24-218">描述</span><span class="sxs-lookup"><span data-stu-id="a3a24-218">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3a24-219">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="a3a24-219">Cleanup.bat</span></span>|<span data-ttu-id="a3a24-220">用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。</span><span class="sxs-lookup"><span data-stu-id="a3a24-220">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span><br /><br /> <span data-ttu-id="a3a24-221">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="a3a24-221">Removes send and receive ports.</span></span><br /><br /> <span data-ttu-id="a3a24-222">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="a3a24-222">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="a3a24-223">ComposedMessageProcessor.sln</span><span class="sxs-lookup"><span data-stu-id="a3a24-223">ComposedMessageProcessor.sln</span></span>|<span data-ttu-id="a3a24-224">此範例的 Visual Studio 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="a3a24-224">Visual Studio solution file for the sample.</span></span>|  
|<span data-ttu-id="a3a24-225">ComposedMessageProcessorBinding.xml</span><span class="sxs-lookup"><span data-stu-id="a3a24-225">ComposedMessageProcessorBinding.xml</span></span>|<span data-ttu-id="a3a24-226">此範例的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="a3a24-226">Binding file for the sample.</span></span>|  
|<span data-ttu-id="a3a24-227">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="a3a24-227">Setup.bat</span></span>|<span data-ttu-id="a3a24-228">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="a3a24-228">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="a3a24-229">在 [協調流程] 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a3a24-229">In Orchestration folder:</span></span><br /><br /> <span data-ttu-id="a3a24-230">CMP.odx</span><span class="sxs-lookup"><span data-stu-id="a3a24-230">CMP.odx</span></span>|<span data-ttu-id="a3a24-231">該協調流程會執行接收管線來解譯訊息、轉換每個已解譯的訊息，然後執行傳送管線將訊息組合成一個交換。</span><span class="sxs-lookup"><span data-stu-id="a3a24-231">Orchestration that runs the receive pipeline to disassembler message, transforms each disassembled message and then runs send pipeline to assemble messages into an interchange.</span></span>|  
|<span data-ttu-id="a3a24-232">在 [協調流程] 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a3a24-232">In Orchestration folder:</span></span><br /><br /> <span data-ttu-id="a3a24-233">Orchestration.btproj</span><span class="sxs-lookup"><span data-stu-id="a3a24-233">Orchestration.btproj</span></span>|<span data-ttu-id="a3a24-234">協調流程所使用的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="a3a24-234">BizTalk project for orchestration.</span></span>|  
|<span data-ttu-id="a3a24-235">在 [協調流程] 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a3a24-235">In Orchestration folder:</span></span><br /><br /> <span data-ttu-id="a3a24-236">SuspendMessage.odx</span><span class="sxs-lookup"><span data-stu-id="a3a24-236">SuspendMessage.odx</span></span>|<span data-ttu-id="a3a24-237">協調流程用於擱置管線處理失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-237">Orchestration used for suspending messages that fail pipeline processing.</span></span>|  
|<span data-ttu-id="a3a24-238">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a3a24-238">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="a3a24-239">CMPInput.xml, CMPOutput.xml</span><span class="sxs-lookup"><span data-stu-id="a3a24-239">CMPInput.xml, CMPOutput.xml</span></span>|<span data-ttu-id="a3a24-240">此範例的輸入和輸出文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3a24-240">Input and output document instances for the sample.</span></span>|  
|<span data-ttu-id="a3a24-241">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a3a24-241">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="a3a24-242">FFReceivePipeline.btp, FFSendPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="a3a24-242">FFReceivePipeline.btp, FFSendPipeline.btp</span></span>|<span data-ttu-id="a3a24-243">具一般檔案元件的接收和傳送管線。</span><span class="sxs-lookup"><span data-stu-id="a3a24-243">Receive and send pipelines with flat file components.</span></span> <span data-ttu-id="a3a24-244">這些管線是在協調流程中執行。</span><span class="sxs-lookup"><span data-stu-id="a3a24-244">These pipelines are run within orchestration.</span></span>|  
|<span data-ttu-id="a3a24-245">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a3a24-245">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="a3a24-246">Invoice.xsd, InvoiceHeader.xsd</span><span class="sxs-lookup"><span data-stu-id="a3a24-246">Invoice.xsd, InvoiceHeader.xsd</span></span>|<span data-ttu-id="a3a24-247">輸出文件和標頭所用的一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="a3a24-247">Flat file schemas for the output document and header.</span></span>|  
|<span data-ttu-id="a3a24-248">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a3a24-248">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="a3a24-249">PO.xsd, POHeader.xsd</span><span class="sxs-lookup"><span data-stu-id="a3a24-249">PO.xsd, POHeader.xsd</span></span>|<span data-ttu-id="a3a24-250">輸入文件和標頭所用的一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="a3a24-250">Flat file schemas for the input document and header.</span></span>|  
|<span data-ttu-id="a3a24-251">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a3a24-251">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="a3a24-252">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="a3a24-252">PropertySchema.xsd</span></span>|<span data-ttu-id="a3a24-253">此範例的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="a3a24-253">Property schema for the sample.</span></span>|  
  
## <a name="building-and-initializing-the-sample"></a><span data-ttu-id="a3a24-254">建置和初始化範例</span><span class="sxs-lookup"><span data-stu-id="a3a24-254">Building and Initializing the Sample</span></span>  
 <span data-ttu-id="a3a24-255">請使用下列程序，建置和初始化「編輯」範例。</span><span class="sxs-lookup"><span data-stu-id="a3a24-255">Use the following procedure to build and initialize the Compose sample.</span></span>  
  
#### <a name="to-build-and-initialize-the-compose-sample"></a><span data-ttu-id="a3a24-256">若要建置及初始化「編輯」範例</span><span class="sxs-lookup"><span data-stu-id="a3a24-256">To build and initialize the Compose sample</span></span>  
  
1.  <span data-ttu-id="a3a24-257">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="a3a24-257">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="a3a24-258">\<範例路徑\>\Pipelines\ComposedMessageProcessor</span><span class="sxs-lookup"><span data-stu-id="a3a24-258">\<Samples Path\>\Pipelines\ComposedMessageProcessor</span></span>  
  
2.  <span data-ttu-id="a3a24-259">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a3a24-259">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="a3a24-260">在此資料夾中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a3a24-260">Creates the input (In) and output (Out) folders for this sample in the folder:</span></span>  
  
         <span data-ttu-id="a3a24-261">\<範例路徑\>\Pipelines\ComposedMessageProcessor</span><span class="sxs-lookup"><span data-stu-id="a3a24-261">\<Samples Path\>\Pipelines\ComposedMessageProcessor</span></span>  
  
    -   <span data-ttu-id="a3a24-262">編譯此範例的 Visual Studio 專案。</span><span class="sxs-lookup"><span data-stu-id="a3a24-262">Compiles the Visual Studio projects for this sample.</span></span>  
  
    -   <span data-ttu-id="a3a24-263">建立名為「CMP 範例」的新應用程式，並將範例組件部署到其中。</span><span class="sxs-lookup"><span data-stu-id="a3a24-263">Creates a new application called "CMP Sample" and deploys the sample assemblies into it.</span></span>  
  
    -   <span data-ttu-id="a3a24-264">建立並繫結 BizTalk Server 接收位置以及傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="a3a24-264">Creates and binds the BizTalk Server receive location, and the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="a3a24-265">登錄和啟動協調流程、啟用接收位置，並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a3a24-265">Enlists and starts orchestration, enables the receive location, and starts the send port.</span></span>  
  
         <span data-ttu-id="a3a24-266">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="a3a24-266">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="a3a24-267">這個金鑰組的用途是簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="a3a24-267">Use this key pair is used to sign the resulting assemblies.</span></span>  
  
3.  <span data-ttu-id="a3a24-268">在嘗試執行此範例之前，請確認 BizTalk Server 未在建置和初始化期間報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="a3a24-268">Before attempting to run this sample, confirm that BizTalk Server did not report any errors during the build and initialization process.</span></span>  
  
     <span data-ttu-id="a3a24-269">若要復原 Setup.bat 所做的變更，您必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a3a24-269">To undo changes made by Setup.bat, you must do the following:</span></span>  
  
    1.  <span data-ttu-id="a3a24-270">從 [BizTalk Server 管理] 主控台中，停止並重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3a24-270">Stop and restart the host instance from the BizTalk Server Administration console.</span></span>  
  
    2.  <span data-ttu-id="a3a24-271">執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="a3a24-271">Run Cleanup.bat.</span></span> <span data-ttu-id="a3a24-272">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="a3a24-272">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="a3a24-273">執行範例</span><span class="sxs-lookup"><span data-stu-id="a3a24-273">Running the sample</span></span>  
 <span data-ttu-id="a3a24-274">使用下列程序執行 ComposedMessageProcessor 範例。</span><span class="sxs-lookup"><span data-stu-id="a3a24-274">Use the following procedure to run the ComposedMessageProcessor sample.</span></span>  
  
#### <a name="to-run-the-composedmessageprocessor-sample"></a><span data-ttu-id="a3a24-275">若要執行 ComposedMessageProcessor 範例</span><span class="sxs-lookup"><span data-stu-id="a3a24-275">To run the ComposedMessageProcessor sample</span></span>  
  
1.  <span data-ttu-id="a3a24-276">複製 PipelinesAndSchemas 資料夾內的 CMPInput.txt 文字檔。</span><span class="sxs-lookup"><span data-stu-id="a3a24-276">Copy the text file CMPInput.txt located in the PipelinesAndSchemas folder.</span></span> <span data-ttu-id="a3a24-277">將複製的檔案貼入 [In] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a3a24-277">Paste the file into the folder In.</span></span>  
  
2.  <span data-ttu-id="a3a24-278">請觀察建立於 Out 資料夾中的文字檔。此檔案包含的記錄與 CMPInput.txt 相同，但是檔案內的資料格式不同。</span><span class="sxs-lookup"><span data-stu-id="a3a24-278">Observe the text file created in the folder Out. This file contains the same records as the CMPInput.txt, but the format of data in the file is different.</span></span>  
  
     <span data-ttu-id="a3a24-279">訊息通過 BizTalk Server 時，會發生以下狀況：</span><span class="sxs-lookup"><span data-stu-id="a3a24-279">As the message passes through the BizTalk Server, the following happens:</span></span>  
  
    1.  <span data-ttu-id="a3a24-280">訊息會被解譯並轉換為 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="a3a24-280">The message gets disassembled and converted into XML messages.</span></span> <span data-ttu-id="a3a24-281">每個訊息都會對應至不同的格式。</span><span class="sxs-lookup"><span data-stu-id="a3a24-281">Each message is mapped to a different format.</span></span>  
  
    2.  <span data-ttu-id="a3a24-282">所有對應的訊息都會組合在一起，並轉換為一般檔案格式。</span><span class="sxs-lookup"><span data-stu-id="a3a24-282">All mapped messages are assembled together and converted into the flat file format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a24-283">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3a24-283">See Also</span></span>  
 [<span data-ttu-id="a3a24-284">管線 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="a3a24-284">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)