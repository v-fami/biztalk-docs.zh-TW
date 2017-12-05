---
title: "EnvelopeProcessing （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, envelopes
- flat files, processing
- examples, flat files
- examples, messages
- examples, envelopes
- envelopes, messages
- flat files, examples
- envelopes, examples
ms.assetid: b4cd979b-c7b4-446c-be29-c9f3169afa1f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c2f2cd505aca89bbe72221b3a895dd21945cb5e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="envelopeprocessing-biztalk-server-sample"></a><span data-ttu-id="16743-102">EnvelopeProcessing （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="16743-102">EnvelopeProcessing (BizTalk Server Sample)</span></span>
<span data-ttu-id="16743-103">EnvelopeProcessing 範例示範如何在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線中處理訊息和訊息信封。</span><span class="sxs-lookup"><span data-stu-id="16743-103">The EnvelopeProcessing sample demonstrates how to process messages and message envelopes in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipelines.</span></span> <span data-ttu-id="16743-104">它也會進一步示範如何將一般檔案訊息處理為 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="16743-104">Further, it shows how to process flat file messages into XML messages.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="16743-105">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="16743-105">What This Sample Does</span></span>  
 <span data-ttu-id="16743-106">此範例會將 EnvInput 資料夾設定為接收位置。</span><span class="sxs-lookup"><span data-stu-id="16743-106">This sample configures the folder EnvInput as a receive location.</span></span> <span data-ttu-id="16743-107">將檔案 (例如範例檔案 EnvelopeProcessing_in.txt) 放置於此資料夾時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用下列步驟處理此檔案中的訊息：</span><span class="sxs-lookup"><span data-stu-id="16743-107">When you place a file, such as the sample file EnvelopeProcessing_in.txt, in this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the messages in this file using the following steps:</span></span>  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="16743-108"> 從接收位置資料夾 EnvInput 擷取訊息檔案。</span><span class="sxs-lookup"><span data-stu-id="16743-108"> retrieves the message file from the receive location folder EnvInput.</span></span>  
  
2.  <span data-ttu-id="16743-109">在接收管線中，「一般檔案解譯器」管線元件會移除一般檔案訊息的標頭與結尾，並將這些訊息剖析為個別訊息。</span><span class="sxs-lookup"><span data-stu-id="16743-109">In the receive pipeline, the Flat File Disassembler pipeline component removes the header and trailer from the flat file messages, and parses them into individual messages.</span></span>  
  
3.  <span data-ttu-id="16743-110">在 MessageBox 資料庫中，訊息會透過訂閱篩選器路由傳送至傳送埠。</span><span class="sxs-lookup"><span data-stu-id="16743-110">In the MessageBox database, the messages are routed to the send port using subscription filters.</span></span>  
  
4.  <span data-ttu-id="16743-111">在傳送埠的傳送管線中，「XML 組合器」管線元件會以 XML 信封包裝訊息，然後將信封放入傳送配接器資料夾 EnvOutput。</span><span class="sxs-lookup"><span data-stu-id="16743-111">In the send pipeline of the send port, XML Assembler pipeline component wraps the messages in XML envelopes and then places them into the send adapter folder EnvOutput.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="16743-112">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="16743-112">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="16743-113">此範例的設計必須顧及兩個基本需求：</span><span class="sxs-lookup"><span data-stu-id="16743-113">The design of this sample had to accommodate two basic requirements:</span></span>  
  
-   <span data-ttu-id="16743-114">接收及處理包含一或多份採購訂單的一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="16743-114">Receive and process a flat file message containing one or more purchase orders.</span></span>  
  
-   <span data-ttu-id="16743-115">將包含一份採購訂單和傳送者資訊的一個 XML 訊息傳送至目錄，讓後端處理系統取用。</span><span class="sxs-lookup"><span data-stu-id="16743-115">Send one XML message containing one purchase order and sender information to a directory for pickup by a back-end processing system.</span></span>  
  
 <span data-ttu-id="16743-116">為了符合這些需求，會使用一般檔案/XML 結構描述的組合和自訂管線。</span><span class="sxs-lookup"><span data-stu-id="16743-116">To meet these requirements, a combination of flat file/XML schemas and custom pipelines were used.</span></span> <span data-ttu-id="16743-117">這些和其他設計元素總結於下表中。</span><span class="sxs-lookup"><span data-stu-id="16743-117">These and other design elements are summarized in the following table.</span></span>  
  
|<span data-ttu-id="16743-118">設計元素</span><span class="sxs-lookup"><span data-stu-id="16743-118">Design element</span></span>|<span data-ttu-id="16743-119">已選取的原因</span><span class="sxs-lookup"><span data-stu-id="16743-119">Reason(s) selected</span></span>|  
|--------------------|--------------------------|  
|<span data-ttu-id="16743-120">自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="16743-120">Custom receive pipeline</span></span>|<span data-ttu-id="16743-121">-使用一般檔案解譯器和一般檔案結構描述來轉譯內送的採購訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="16743-121">-   Uses the Flat File Disassembler and flat file schemas to translate inbound purchase order messages.</span></span>|  
|<span data-ttu-id="16743-122">訊息標頭、內文和結尾的一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="16743-122">Flat file schemas for message header, body, and trailer</span></span>|<span data-ttu-id="16743-123">-定義的所有相同記錄與欄位特性 （包含結構） 為 XML 結構描述，並提供一個機制來定義一般檔案特性，將一般檔案執行個體訊息轉譯成相等的 XML 執行個體所需的所有訊息 （反之亦然）。</span><span class="sxs-lookup"><span data-stu-id="16743-123">-   Defines all of the same record and field characteristics (including structure) as XML schemas and provide a mechanism for defining all of the flat file characteristics that are required to translate a flat file instance message into an equivalent XML instance message (or vice versa).</span></span><br /><span data-ttu-id="16743-124">標頭、 內文和結尾結構描述可用來將內文分割成不連續區塊來處理。</span><span class="sxs-lookup"><span data-stu-id="16743-124">-   Header, body, and trailer schemas are used to split the body into discrete chunks for processing.</span></span>|  
|<span data-ttu-id="16743-125">信封結構描述</span><span class="sxs-lookup"><span data-stu-id="16743-125">Envelope schema</span></span>|<span data-ttu-id="16743-126">-用來從標頭資訊與個別訂單一併包裝。</span><span class="sxs-lookup"><span data-stu-id="16743-126">-   Used to wrap individual purchase orders with information from the header.</span></span>|  
|<span data-ttu-id="16743-127">訂閱篩選器</span><span class="sxs-lookup"><span data-stu-id="16743-127">Subscription filter</span></span>|<span data-ttu-id="16743-128">-訂用帳戶篩選器會執行實際的路由擷取符合根據屬性欄位的一或多個準則的訊息。</span><span class="sxs-lookup"><span data-stu-id="16743-128">-   The subscription filter performs the actual routing by capturing messages that meet one or more criteria based on property fields.</span></span>|  
|<span data-ttu-id="16743-129">自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="16743-129">Custom send pipeline</span></span>|<span data-ttu-id="16743-130">-若要將執行個體訊息轉譯成 XML 格式，會使用 XML 組合器和信封和內文結構描述的組合。</span><span class="sxs-lookup"><span data-stu-id="16743-130">-   Uses the XML Assembler and a combination of envelope and body schemas to translate the instance messages into XML format.</span></span>|  
  
 <span data-ttu-id="16743-131">下列考量適用於這個範例的設計。</span><span class="sxs-lookup"><span data-stu-id="16743-131">The following considerations apply to the design of this sample.</span></span>  
  
-   <span data-ttu-id="16743-132">一般檔案結構描述 (PO.xsd) 包含擴充註解，會說明採購訂單一般檔案的結構。</span><span class="sxs-lookup"><span data-stu-id="16743-132">The flat file schema (PO.xsd) contains extended annotations describing the structure of the purchase order flat file.</span></span> <span data-ttu-id="16743-133">這些檔案可以用手動方式建立，但有不少可以透過 [一般檔案精靈] 產生。</span><span class="sxs-lookup"><span data-stu-id="16743-133">These files can be created by hand, but many can be generated by using the Flat File Wizard.</span></span>  
  
-   <span data-ttu-id="16743-134">採購訂單 (PO.xsd) 一般檔案結構描述會使用值為 Unqualified 的 elementFormDefault 屬性。</span><span class="sxs-lookup"><span data-stu-id="16743-134">The purchase order (PO.xsd) flat file schema uses an elementFormDefault value of Unqualified.</span></span> <span data-ttu-id="16743-135">雖然產生的結果正確無誤，但包含其他未預期的 xmlns 限定性條件。</span><span class="sxs-lookup"><span data-stu-id="16743-135">This produces correct results but with additional and unexpected xmlns qualifications.</span></span> <span data-ttu-id="16743-136">使用值為 Qualified 的 elementFormDefault 即可避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="16743-136">Use an elementFormDefault of Qualified to avoid this issue.</span></span>  
  
-   <span data-ttu-id="16743-137">標頭和結尾一般檔案結構描述用來分隔訊息中的標頭和結尾資料。</span><span class="sxs-lookup"><span data-stu-id="16743-137">Header and trailer flat file schemas are used to separate heading and trailing data from the message.</span></span> <span data-ttu-id="16743-138">「一般檔案解譯器」標頭、文件和結尾結構描述屬性已分別設定為標頭、採購訂單和結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="16743-138">The Flat File Disassembler header, document, and trailer schema properties were set to the header, purchase order, and trailer schema respectively.</span></span>  
  
-   <span data-ttu-id="16743-139">XML 信封結構描述會結合標頭和訂單中的項目，產生一個 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="16743-139">The XML envelope schema combines elements from the header and purchase order to produce a single XML message.</span></span> <span data-ttu-id="16743-140">標頭結構描述升級來源欄位中的 SourceParty 欄位**BTS.bts_system_properties**命名空間; 信封結構描述會升級此相同的值，就會降級為傳出訊息。</span><span class="sxs-lookup"><span data-stu-id="16743-140">The header schema promotes the Source field into the SourceParty field in the **BTS.bts_system_properties** namespace; the envelope schema promotes this same value, causing it to be demoted into the outbound message.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="16743-141">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="16743-141">Where to Find This Sample</span></span>  
 <span data-ttu-id="16743-142">`<Samples Path>`\Pipelines\AssemblerDisassembler\EnvelopeProcessing\\</span><span class="sxs-lookup"><span data-stu-id="16743-142">`<Samples Path>`\Pipelines\AssemblerDisassembler\EnvelopeProcessing\\</span></span>  
  
 <span data-ttu-id="16743-143">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="16743-143">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="16743-144">檔案</span><span class="sxs-lookup"><span data-stu-id="16743-144">File(s)</span></span>|<span data-ttu-id="16743-145">Description</span><span class="sxs-lookup"><span data-stu-id="16743-145">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16743-146">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="16743-146">Cleanup.bat</span></span>|<span data-ttu-id="16743-147">用來解除部署組件，以及將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="16743-147">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="16743-148">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="16743-148">Removes send and receive ports.</span></span> <span data-ttu-id="16743-149">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="16743-149">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="16743-150">EnvelopeProcessing.btproj、EnvelopeProcessing.sln</span><span class="sxs-lookup"><span data-stu-id="16743-150">EnvelopeProcessing.btproj, EnvelopeProcessing.sln</span></span>|<span data-ttu-id="16743-151">這個範例的專案及解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="16743-151">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="16743-152">EnvelopeProcessing_in.txt</span><span class="sxs-lookup"><span data-stu-id="16743-152">EnvelopeProcessing_in.txt</span></span>|<span data-ttu-id="16743-153">範例輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="16743-153">Sample input file.</span></span>|  
|<span data-ttu-id="16743-154">Header.xsd、PO.xsd、Trailer.xsd</span><span class="sxs-lookup"><span data-stu-id="16743-154">Header.xsd, PO.xsd, Trailer.xsd</span></span>|<span data-ttu-id="16743-155">一般檔案標頭、內文和結尾各自的結構描述。</span><span class="sxs-lookup"><span data-stu-id="16743-155">Schema for flat file header, body, and trailer, respectively.</span></span>|  
|<span data-ttu-id="16743-156">XmlEnvelope.xsd</span><span class="sxs-lookup"><span data-stu-id="16743-156">XmlEnvelope.xsd</span></span>|<span data-ttu-id="16743-157">輸出 XML 信封的結構描述。</span><span class="sxs-lookup"><span data-stu-id="16743-157">Schema for outbound XML envelope.</span></span>|  
|<span data-ttu-id="16743-158">EnvReceivePipeline.btp、EnvSendPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="16743-158">EnvReceivePipeline.btp, EnvSendPipeline.btp</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="16743-159"> 分別使用「一般檔案解譯器」和「XML 組合器」管線元件來接收和傳送管線檔案。</span><span class="sxs-lookup"><span data-stu-id="16743-159"> receive and send pipeline files with the Flat File Disassembler and XML Assembler pipeline components, respectively.</span></span>|  
|<span data-ttu-id="16743-160">EnvelopeProcessingBinding.xml</span><span class="sxs-lookup"><span data-stu-id="16743-160">EnvelopeProcessingBinding.xml</span></span>|<span data-ttu-id="16743-161">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="16743-161">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="16743-162">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="16743-162">Setup.bat</span></span>|<span data-ttu-id="16743-163">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="16743-163">Used to build and initialize this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="16743-164">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="16743-164">How to Use This Sample</span></span>  
 <span data-ttu-id="16743-165">您可以使用此範例，做為自己的一般檔案處理解決方案基礎。</span><span class="sxs-lookup"><span data-stu-id="16743-165">Use this sample as the basis for your own flat file processing solution.</span></span> <span data-ttu-id="16743-166">您可以將本範例中所用的許多設計元素加以擴充，以符合自己的需求。</span><span class="sxs-lookup"><span data-stu-id="16743-166">You can extend many of the design elements used in this sample to fit your own requirements.</span></span> <span data-ttu-id="16743-167">部分範例如下：</span><span class="sxs-lookup"><span data-stu-id="16743-167">Some examples are as follows:</span></span>  
  
-   <span data-ttu-id="16743-168">除了 XML 版本之外，加強範例來撰寫每個採購訂單的一般檔案版本。</span><span class="sxs-lookup"><span data-stu-id="16743-168">Enhance the sample to write a flat file version of each purchase order in addition to the XML version.</span></span> <span data-ttu-id="16743-169">您可以建立新的自訂傳送管線及使用「一般檔案組合器」來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="16743-169">You can do this by creating a new custom send pipeline and using the Flat File Assembler.</span></span> <span data-ttu-id="16743-170">在「一般檔案組合器」上，指定一般檔案標頭、採購訂單和結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="16743-170">On the Flat File Assembler, specify the flat file header, purchase order, and trailer schemas.</span></span> <span data-ttu-id="16743-171">在傳送埠中使用時，它會產生具有標頭/結尾資訊的個別採購訂單。</span><span class="sxs-lookup"><span data-stu-id="16743-171">When used in a send port, it produces individual purchase orders with header/trailer information.</span></span>  
  
-   <span data-ttu-id="16743-172">以採購訂單中的更多資訊加強信封。</span><span class="sxs-lookup"><span data-stu-id="16743-172">Enhance the envelope with more information from the purchase order.</span></span> <span data-ttu-id="16743-173">若要將其他資訊寫入至輸出訊息，請使用「快速升級」升級 "ship to" 名稱或其他欄位，將欄位加入信封，然後將信封欄位升級為相同欄位。</span><span class="sxs-lookup"><span data-stu-id="16743-173">To write additional information into the outbound message, promote the "ship to" name or other fields using Quick Promote, add fields to the envelope, and then promote the envelope fields to the same field.</span></span> <span data-ttu-id="16743-174">透過組合器處理訊息時，升級的屬性會降級並複製到輸出訊息中。</span><span class="sxs-lookup"><span data-stu-id="16743-174">When the message is processed through the assembler, promoted properties are demoted and copied into the outbound message.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="16743-175">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="16743-175">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-envelopeprocessing-sample"></a><span data-ttu-id="16743-176">若要建置及初始化 EnvelopeProcessing 範例</span><span class="sxs-lookup"><span data-stu-id="16743-176">To build and initialize the EnvelopeProcessing sample</span></span>  
  
1.  <span data-ttu-id="16743-177">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="16743-177">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="16743-178">*\<範例路徑\>*\Pipelines\AssemblerDisassembler\EnvelopeProcessing</span><span class="sxs-lookup"><span data-stu-id="16743-178">*\<Samples Path\>*\Pipelines\AssemblerDisassembler\EnvelopeProcessing</span></span>  
  
2.  <span data-ttu-id="16743-179">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="16743-179">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="16743-180">為檔案夾內的這個範例建立輸入 (EnvInput) 和輸出 (EnvOutput) 檔案夾：</span><span class="sxs-lookup"><span data-stu-id="16743-180">Creates the input (EnvInput) and output (EnvOutput) folders for this sample in the folder:</span></span>  
  
         <span data-ttu-id="16743-181">*\<範例路徑\>*\Pipelines\AssemblerDisassembler\EnvelopeProcessing\\</span><span class="sxs-lookup"><span data-stu-id="16743-181">*\<Samples Path\>*\Pipelines\AssemblerDisassembler\EnvelopeProcessing\\</span></span>  
  
    -   <span data-ttu-id="16743-182">為這個範例編譯和部署 Visual Studio 專案。</span><span class="sxs-lookup"><span data-stu-id="16743-182">Compiles and deploys the Visual Studio project for this sample.</span></span>  
  
    -   <span data-ttu-id="16743-183">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="16743-183">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
         <span data-ttu-id="16743-184">這個範例會在建立和繫結連接埠時顯示下列警告：</span><span class="sxs-lookup"><span data-stu-id="16743-184">This sample displays the following warnings when creating and binding ports:</span></span>  
  
        ```  
        Warning: Receive handler not specified for receive location "EnvelopeProcessing_RL"; updating with first receive handler with matching transport type.  
        Warning: Host not specified for orchestration "EnvelopeProcessing"; updating with first available host.  
        ```  
  
         <span data-ttu-id="16743-185">您可以安全地忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="16743-185">You can safely ignore these warnings.</span></span> <span data-ttu-id="16743-186">(繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。</span><span class="sxs-lookup"><span data-stu-id="16743-186">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  
  
    -   <span data-ttu-id="16743-187">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="16743-187">Enables the receive location, and starts the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16743-188">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="16743-188">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16743-189">如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="16743-189">If you choose to open and build the project in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="16743-190">請使用這個金鑰組來簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="16743-190">Use this key pair to sign the resulting assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16743-191">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="16743-191">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="16743-192">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="16743-192">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="16743-193">執行此範例</span><span class="sxs-lookup"><span data-stu-id="16743-193">Running This Sample</span></span>  
  
#### <a name="to-run-the-envelopeprocessing-sample"></a><span data-ttu-id="16743-194">若要執行 EnvelopeProcessing 範例</span><span class="sxs-lookup"><span data-stu-id="16743-194">To run the EnvelopeProcessing sample</span></span>  
  
1.  <span data-ttu-id="16743-195">將檔案 EnvelopeProcessing_in.txt 複製到資料夾 EnvInput。</span><span class="sxs-lookup"><span data-stu-id="16743-195">Put a copy of the file EnvelopeProcessing_in.txt into the folder EnvInput.</span></span>  
  
2.  <span data-ttu-id="16743-196">觀察資料夾 EnvOutput 中建立的三個 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="16743-196">Observe the three .xml files created in the folder EnvOutput.</span></span> <span data-ttu-id="16743-197">這些 .xml 檔案的名稱是根據它們的訊息識別碼 GUID 為基礎。</span><span class="sxs-lookup"><span data-stu-id="16743-197">The names of these .xml files are based on their message ID GUIDs.</span></span> <span data-ttu-id="16743-198">這些檔案包含從輸入檔擷取和信封中包裝的訊息。</span><span class="sxs-lookup"><span data-stu-id="16743-198">They contain the messages extracted from the input file and wrapped in envelopes.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="16743-199">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="16743-199">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="16743-200">組態指令碼 Setup.bat 和 Cleanup.bat 依賴下列系統管理 Windows Management Instrumentation (WMI) 指令碼：</span><span class="sxs-lookup"><span data-stu-id="16743-200">The configuration scripts Setup.bat and Cleanup.bat rely on the following administrative Windows Management Instrumentation (WMI) scripts:</span></span>  
  
-   <span data-ttu-id="16743-201">啟動傳送埠\StartSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="16743-201">Start Send Port\StartSendPort.vbs</span></span>  
  
-   <span data-ttu-id="16743-202">啟用接收位置\EnableRecLoc</span><span class="sxs-lookup"><span data-stu-id="16743-202">Enable Receive Location\EnableRecLoc</span></span>  
  
-   <span data-ttu-id="16743-203">移除傳送埠\RemoveSendPort</span><span class="sxs-lookup"><span data-stu-id="16743-203">Remove Send Port\RemoveSendPort</span></span>  
  
 <span data-ttu-id="16743-204">安裝和清除批次檔使用的是下列 BTSTask：</span><span class="sxs-lookup"><span data-stu-id="16743-204">The setup and cleanup batch files use BTSTask as follows:</span></span>  
  
-   <span data-ttu-id="16743-205">**BTSTask ImportBindings**套用繫結檔案，並建立應用程式、 連接埠和繫結</span><span class="sxs-lookup"><span data-stu-id="16743-205">**BTSTask ImportBindings** to apply the binding file and create the application, ports, and bindings</span></span>  
  
-   <span data-ttu-id="16743-206">**BTSTask RemoveApp**用以移除 FlatFileReceiveApplication</span><span class="sxs-lookup"><span data-stu-id="16743-206">**BTSTask RemoveApp** to remove the FlatFileReceiveApplication</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16743-207">請參閱</span><span class="sxs-lookup"><span data-stu-id="16743-207">See Also</span></span>  
 [<span data-ttu-id="16743-208">Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="16743-208">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)