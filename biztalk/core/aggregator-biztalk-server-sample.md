---
title: 彙總工具 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- pipelines, examples
- orchestrations, messages
- examples, pipelines
- messages, correlating to orchestrations
ms.assetid: eb8121df-4f5b-4f36-8228-4b5ad1abfb4e
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 493f4d28214a815aca88f214e5efb9cd883e7192
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "25965252"
---
# <a name="aggregator-biztalk-server-sample"></a><span data-ttu-id="25ff8-102">彙總工具 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="25ff8-102">Aggregator (BizTalk Server Sample)</span></span>
<span data-ttu-id="25ff8-103">此範例的目的是要建置使用協調流程和管線的訊息彙總功能。</span><span class="sxs-lookup"><span data-stu-id="25ff8-103">The purpose of this sample is to build a message aggregation functionality using orchestration and pipelines.</span></span> <span data-ttu-id="25ff8-104">具體而言，我們將會建立可執行下列作業的協調流程：</span><span class="sxs-lookup"><span data-stu-id="25ff8-104">Specifically we will build an orchestration that:</span></span>  
  
1.  <span data-ttu-id="25ff8-105">接收一組相互關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="25ff8-105">Receives a set of correlated messages.</span></span> <span data-ttu-id="25ff8-106">訊息會根據從訊息內容擷取的目的地夥伴 URI 資訊來進行相互關聯。</span><span class="sxs-lookup"><span data-stu-id="25ff8-106">Messages are correlated based on the destination partner URI information that is extracted from message content.</span></span>  
  
2.  <span data-ttu-id="25ff8-107">藉由執行 XML 傳送管線，將接收的訊息彙總到單一的交換批次。</span><span class="sxs-lookup"><span data-stu-id="25ff8-107">Aggregates received messages into a single interchange batch by executing an XML send pipeline.</span></span>  
  
3.  <span data-ttu-id="25ff8-108">每分鐘產生一次 XML 交換訊息，或是在有足夠彙總數量的訊息時立即產生。</span><span class="sxs-lookup"><span data-stu-id="25ff8-108">Produces an XML interchange message every minute or as soon as it has enough messages to aggregate.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="25ff8-109">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="25ff8-109">Where to Find This Sample</span></span>  
 <span data-ttu-id="25ff8-110">*\<範例路徑\>* \Pipelines\Aggregator</span><span class="sxs-lookup"><span data-stu-id="25ff8-110">*\<Samples Path\>* \Pipelines\Aggregator</span></span>  
  
 <span data-ttu-id="25ff8-111">下表列出此範例使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="25ff8-111">The following table lists the files for this sample.</span></span>  
  
|<span data-ttu-id="25ff8-112">檔案</span><span class="sxs-lookup"><span data-stu-id="25ff8-112">File(s)</span></span>|<span data-ttu-id="25ff8-113">Description</span><span class="sxs-lookup"><span data-stu-id="25ff8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25ff8-114">Aggregator.sln</span><span class="sxs-lookup"><span data-stu-id="25ff8-114">Aggregator.sln</span></span>|<span data-ttu-id="25ff8-115">此範例的 Visual Studio 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="25ff8-115">Visual Studio solution file for the sample.</span></span>|  
|<span data-ttu-id="25ff8-116">AggretatorBinding.xml</span><span class="sxs-lookup"><span data-stu-id="25ff8-116">AggretatorBinding.xml</span></span>|<span data-ttu-id="25ff8-117">此範例的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="25ff8-117">Binding file for the sample.</span></span>|  
|<span data-ttu-id="25ff8-118">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="25ff8-118">Cleanup.bat</span></span>|<span data-ttu-id="25ff8-119">用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。</span><span class="sxs-lookup"><span data-stu-id="25ff8-119">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="25ff8-120">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="25ff8-120">Removes send and receive ports.</span></span> <span data-ttu-id="25ff8-121">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="25ff8-121">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="25ff8-122">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="25ff8-122">Setup.bat</span></span>|<span data-ttu-id="25ff8-123">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="25ff8-123">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="25ff8-124">在 [Aggregate] 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-124">In Aggregate folder:</span></span><br /><br /> <span data-ttu-id="25ff8-125">Aggregate.btproj</span><span class="sxs-lookup"><span data-stu-id="25ff8-125">Aggregate.btproj</span></span>|<span data-ttu-id="25ff8-126">彙總協調流程所使用的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="25ff8-126">BizTalk project for aggregating orchestration.</span></span>|  
|<span data-ttu-id="25ff8-127">在 Aggregator 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-127">In Aggregator folder:</span></span><br /><br /> <span data-ttu-id="25ff8-128">Aggregate.odx</span><span class="sxs-lookup"><span data-stu-id="25ff8-128">Aggregate.odx</span></span>|<span data-ttu-id="25ff8-129">協調流程，其可將相互關聯的訊息收集在一起，然後執行傳送管線，將這些訊息組合成單一個交換。</span><span class="sxs-lookup"><span data-stu-id="25ff8-129">Orchestration that collects correlated messages together and then executes send pipeline to assemble them into a single interchange.</span></span>|  
|<span data-ttu-id="25ff8-130">在 [Aggregate] 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-130">In Aggregate folder:</span></span><br /><br /> <span data-ttu-id="25ff8-131">SuspendMessage.odx</span><span class="sxs-lookup"><span data-stu-id="25ff8-131">SuspendMessage.odx</span></span>|<span data-ttu-id="25ff8-132">協調流程，用於擱置無法在彙總協調流程內處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="25ff8-132">Orchestration used for suspending messages that cannot be processed within aggregating orchestration.</span></span>|  
|<span data-ttu-id="25ff8-133">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-133">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="25ff8-134">FFReceivePipeline.btp</span><span class="sxs-lookup"><span data-stu-id="25ff8-134">FFReceivePipeline.btp</span></span>|<span data-ttu-id="25ff8-135">具有一般檔案解譯器的接收管線</span><span class="sxs-lookup"><span data-stu-id="25ff8-135">Receive pipeline with flat file disassembler.</span></span>|  
|<span data-ttu-id="25ff8-136">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-136">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="25ff8-137">Instance1.txt、Instance2.txt、Instance3.txt、Instance4.txt</span><span class="sxs-lookup"><span data-stu-id="25ff8-137">Instance1.txt, Instance2.txt, Instance3.txt, Instance4.txt</span></span>|<span data-ttu-id="25ff8-138">此範例的文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="25ff8-138">Document instances for the sample.</span></span> <span data-ttu-id="25ff8-139">Instance1.txt 和 instance2.txt 都應該加入到目的地夥伴交換[ http://www.contoso.com ](http://www.contoso.com/)而 Instance3.txt 和 Instance4.txt 應該加入到目的地夥伴交換[ http://www.northwind.com](http://www.northwind.com/).</span><span class="sxs-lookup"><span data-stu-id="25ff8-139">Instance1.txt and Instance2.txt should be added to an interchange for destination partner [http://www.contoso.com](http://www.contoso.com/) while Instance3.txt and Instance4.txt should be added to an interchange for destination partner [http://www.northwind.com](http://www.northwind.com/).</span></span>|  
|<span data-ttu-id="25ff8-140">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-140">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="25ff8-141">Invoice.xsd、InvoiceEnvelope.xsd</span><span class="sxs-lookup"><span data-stu-id="25ff8-141">Invoice.xsd, InvoiceEnvelope.xsd</span></span>|<span data-ttu-id="25ff8-142">輸出交換的文件結構描述和信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="25ff8-142">Document schema and envelope schema for output interchange.</span></span>|  
|<span data-ttu-id="25ff8-143">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-143">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="25ff8-144">PipelinesAndSchemas.btproj</span><span class="sxs-lookup"><span data-stu-id="25ff8-144">PipelinesAndSchemas.btproj</span></span>|<span data-ttu-id="25ff8-145">結構描述和管線的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="25ff8-145">BizTalk project for the schemas and pipelines.</span></span>|  
|<span data-ttu-id="25ff8-146">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-146">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="25ff8-147">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="25ff8-147">PropertySchema.xsd</span></span>|<span data-ttu-id="25ff8-148">此範例的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="25ff8-148">Property schema for the sample.</span></span>|  
|<span data-ttu-id="25ff8-149">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="25ff8-149">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="25ff8-150">XMLAggregatingPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="25ff8-150">XMLAggregatingPipeline.btp</span></span>|<span data-ttu-id="25ff8-151">傳送管線，其將從協調流程執行，以便將收集到的訊息組合成 XML 交換。</span><span class="sxs-lookup"><span data-stu-id="25ff8-151">Send pipeline that is executed from orchestration to assemble collected messages into an XML interchange.</span></span>|  
  
## <a name="building-and-initializing-the-sample"></a><span data-ttu-id="25ff8-152">建置和初始化範例</span><span class="sxs-lookup"><span data-stu-id="25ff8-152">Building and Initializing the Sample</span></span>  
 <span data-ttu-id="25ff8-153">請使用下列程序，建置和初始化此「彙總工具」範例。</span><span class="sxs-lookup"><span data-stu-id="25ff8-153">Use the following procedure to build and initialize the Aggregator sample.</span></span>  
  
#### <a name="to-build-and-initialize-the-aggregator-sample"></a><span data-ttu-id="25ff8-154">若要建置和初始化此彙總工具範例</span><span class="sxs-lookup"><span data-stu-id="25ff8-154">To build and initialize the Aggregator sample</span></span>  
  
1.  <span data-ttu-id="25ff8-155">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="25ff8-155">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="25ff8-156">\<範例路徑\>\Pipelines\Aggregator</span><span class="sxs-lookup"><span data-stu-id="25ff8-156">\<Samples Path\>\Pipelines\Aggregator</span></span>  
  
2.  <span data-ttu-id="25ff8-157">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="25ff8-157">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="25ff8-158">在此資料夾中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="25ff8-158">Creates the input (In) and output (Out) folders for this sample in the folder:</span></span>  
  
         <span data-ttu-id="25ff8-159">\<範例路徑\>\Pipelines\Aggregator</span><span class="sxs-lookup"><span data-stu-id="25ff8-159">\<Samples Path\>\Pipelines\Aggregator</span></span>  
  
    -   <span data-ttu-id="25ff8-160">為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="25ff8-160">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  
  
    -   <span data-ttu-id="25ff8-161">建立稱為 "Aggregator Sample" 的新應用程式，並在其中部署此範例組件。</span><span class="sxs-lookup"><span data-stu-id="25ff8-161">Creates a new application called "Aggregator Sample" and deploys the sample assemblies into it.</span></span>  
  
    -   <span data-ttu-id="25ff8-162">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="25ff8-162">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="25ff8-163">登錄和啟動協調流程、啟用接收位置，並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="25ff8-163">Enlists and starts orchestration, enables the receive location, and starts the send port.</span></span>  
  
         <span data-ttu-id="25ff8-164">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="25ff8-164">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="25ff8-165">這個金鑰組的用途是簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="25ff8-165">Use this key pair is used to sign the resulting assemblies.</span></span>  
  
3.  <span data-ttu-id="25ff8-166">在嘗試執行此範例之前，請確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 未在建置和初始化程序期間報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="25ff8-166">Before attempting to run this sample, confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process.</span></span>  
  
     <span data-ttu-id="25ff8-167">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="25ff8-167">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="25ff8-168">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="25ff8-168">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="25ff8-169">執行範例</span><span class="sxs-lookup"><span data-stu-id="25ff8-169">Running the Sample</span></span>  
 <span data-ttu-id="25ff8-170">請使用下列程序執行「彙總工具」範例。</span><span class="sxs-lookup"><span data-stu-id="25ff8-170">Use the following procedure to run the Aggregator sample.</span></span>  
  
#### <a name="to-run-the-aggregator-sample"></a><span data-ttu-id="25ff8-171">若要執行此彙總工具範例</span><span class="sxs-lookup"><span data-stu-id="25ff8-171">To run the Aggregator sample</span></span>  
  
1.  <span data-ttu-id="25ff8-172">開啟位於 PipelinesAndSchemas 資料夾中的 Instance1.txt 和 Instance2.txt 檔案，檢查其內容。</span><span class="sxs-lookup"><span data-stu-id="25ff8-172">Open Instance1.txt and Instance2.txt files located in PipelinesAndSchemas folder to inspect their content.</span></span>  
  
     <span data-ttu-id="25ff8-173">請注意，在檔案的 DestinationPartnerURI 項目包含值http://www.contoso.com 。這個值會用來將這兩個訊息相互關聯，如此它們就可加入到同一個交換中。</span><span class="sxs-lookup"><span data-stu-id="25ff8-173">Notice that in both files the DestinationPartnerURI element contains the value http://www.contoso.com. This value will be used to correlate these two messages together so that they can be added to one interchange.</span></span>  
  
     <span data-ttu-id="25ff8-174">同樣地 Instance3.txt 和 Instance4.txt 檔案具有 DestinationPatnerURI 項目設為http://www.northwind.com 。</span><span class="sxs-lookup"><span data-stu-id="25ff8-174">Similarly Instance3.txt and Instance4.txt files have DestinationPatnerURI element set to http://www.northwind.com.</span></span>  
  
     <span data-ttu-id="25ff8-175">這兩個訊息會一起加入到另一個交換中。</span><span class="sxs-lookup"><span data-stu-id="25ff8-175">These two messages together will be added to a different interchange.</span></span>  
  
2.  <span data-ttu-id="25ff8-176">Instance1.txt、 Instance2.txt、 Instance3.txt、 和 Instance4.txt 的文字檔案的複本貼入資料夾中。</span><span class="sxs-lookup"><span data-stu-id="25ff8-176">Paste copies of the text files Instance1.txt, Instance2.txt, Instance3.txt, and Instance4.txt into the folder In.</span></span>  
  
3.  <span data-ttu-id="25ff8-177">彙總協調流程會在收集到 10 則訊息後立即產生輸出交換，或是在 1 分鐘逾時後產生輸出交換。</span><span class="sxs-lookup"><span data-stu-id="25ff8-177">Aggregating orchestrations produce output interchanges as soon as they collect 10 messages or after timeout of 1 minute.</span></span> <span data-ttu-id="25ff8-178">因此，在 Out 資料夾中的檔案可能會延遲出現。</span><span class="sxs-lookup"><span data-stu-id="25ff8-178">Because of that, the files in the Out folder may appear with delay.</span></span>  
  
     <span data-ttu-id="25ff8-179">若要避免逾時，您可以將四個輸入檔案再貼上四次，以便觸發彙總協調流程產生交換。</span><span class="sxs-lookup"><span data-stu-id="25ff8-179">To avoid the timeout, you can paste the four input files four more times, which would trigger the aggregating orchestrations to produce the interchanges.</span></span>  
  
4.  <span data-ttu-id="25ff8-180">觀察在 Out 資料夾中建立的 XML 檔案。其中應該有兩個檔案，也就是每個目的地夥伴 URI 各有一個。</span><span class="sxs-lookup"><span data-stu-id="25ff8-180">Observe the XML files created in the folder Out. There should be two files – one per each destination partner URI.</span></span>  
  
     <span data-ttu-id="25ff8-181">開啟一個檔案檢查其內容。</span><span class="sxs-lookup"><span data-stu-id="25ff8-181">Open one of the file to inspect its content.</span></span> <span data-ttu-id="25ff8-182">該檔案應該包含由一個信封和兩個內部 XML 文件所組成的 XML 交換。</span><span class="sxs-lookup"><span data-stu-id="25ff8-182">The file should contain an XML interchange that consists of an envelope and two XML documents within it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="25ff8-183">此範例實作可能會於群組實例中的高負載情況下，造成「已傳遞，未使用訊息」或「完成並有捨棄的訊息」的問題。</span><span class="sxs-lookup"><span data-stu-id="25ff8-183">The sample implementation may cause "Delivered, not consumed messages" or "Completed with discarded messages" under high load in a convoy scenario.</span></span> <span data-ttu-id="25ff8-184">每當訊息路由至已經在結束階段的商務程序時，或是每當有未預期的訊息抵達到商務程序時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="25ff8-184">This occurs any time a message routes to a business process that is in the process of ending, or any time unexpected messages arrive into a business process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ff8-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25ff8-185">See Also</span></span>  
 [<span data-ttu-id="25ff8-186">管線 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="25ff8-186">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)