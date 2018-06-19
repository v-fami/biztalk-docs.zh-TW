---
title: 訊息豐富 」 範例 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41ed707-dbdb-46b7-97a6-86fdbc8ad285
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3413345c4e2d0a2ce4cd7ee1cb5ebda50b1dea7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265206"
---
# <a name="message-enrichment-sample-biztalk-server-sample"></a><span data-ttu-id="c0c31-102">訊息豐富範例 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="c0c31-102">Message Enrichment Sample (BizTalk Server Sample)</span></span>
<span data-ttu-id="c0c31-103">「訊息豐富」範例會示範如何將交換標頭附加至 X12 和 EDIFACT 文件的交易集訊息。</span><span class="sxs-lookup"><span data-stu-id="c0c31-103">The Message Enrichment sample demonstrates how to append interchange headers to transaction-set messages for X12 and EDIFACT documents.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="c0c31-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="c0c31-104">What This Sample Does</span></span>  
 <span data-ttu-id="c0c31-105">此範例示範如何將針對 EDIFACT 的 UNA、UNB 和 UNG 標頭及針對 X12 的 ISA 標頭附加至交易集。</span><span class="sxs-lookup"><span data-stu-id="c0c31-105">This sample demonstrates how to append UNA, UNB, and UNG headers for EDIFACT, and ISA headers for X12, to transaction sets.</span></span> <span data-ttu-id="c0c31-106">具體來說，本範例執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="c0c31-106">Specifically, this sample does the following:</span></span>  
  
1.  <span data-ttu-id="c0c31-107">將測試訊息放置到 \Message Enrichment\In 資料夾後，接收埠會拾取訊息，處理後再放到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="c0c31-107">When you drop the test message to the \Message Enrichment\In folder, the receive port picks it up, processes it, and drops it in the MessageBox.</span></span>  
  
2.  <span data-ttu-id="c0c31-108">MessageEnrichmentOrchestration 會從 MessageBox 拾取測試訊息，因為它是根據其「接收」圖形上設定的篩選條件運算式訂閱訊息。</span><span class="sxs-lookup"><span data-stu-id="c0c31-108">The MessageEnrichmentOrchestration picks the test message up from the MessageBox, because it subscribes to messages based on a filter expression set on its receive shape.</span></span>  
  
3.  <span data-ttu-id="c0c31-109">協調流程會讀取訊息之內容屬性的交換標頭。</span><span class="sxs-lookup"><span data-stu-id="c0c31-109">The orchestration reads the interchange headers from the context properties of the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0c31-110">UNA 和 UNG 標頭為 EDIFACT 訊息中的選用項目，因此訊息的內容屬性中可能沒有這兩個標頭。</span><span class="sxs-lookup"><span data-stu-id="c0c31-110">UNA and UNG headers are optional in an EDIFACT message, so can be missing in the context properties of a message.</span></span>  
  
4.  <span data-ttu-id="c0c31-111">協調流程會將交換標頭和訊息內文皆寫入單一新訊息中。</span><span class="sxs-lookup"><span data-stu-id="c0c31-111">The orchestration writes both the interchange headers and the message body into a single new message.</span></span>  
  
5.  <span data-ttu-id="c0c31-112">協調流程會將設定於 ReceivePortNameCorrelationType 相互關聯類型中的其他屬性升級至訊息。</span><span class="sxs-lookup"><span data-stu-id="c0c31-112">The orchestration promotes additional properties that are set in the ReceivePortNameCorrelationType correlation type onto the message.</span></span> <span data-ttu-id="c0c31-113">這樣一來，協調流程的使用者就可以選取其訂閱所需的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="c0c31-113">These allow users of the orchestration to select a list of the properties they need for their subscription.</span></span> <span data-ttu-id="c0c31-114">這些屬性寫在「建構訊息」圖形中。</span><span class="sxs-lookup"><span data-stu-id="c0c31-114">These properties are written in a construct message shape.</span></span> <span data-ttu-id="c0c31-115">並非所有寫入原始訊息的內容屬性都會寫入新訊息中。</span><span class="sxs-lookup"><span data-stu-id="c0c31-115">Not all context properties that were written to the original message are written to the new message.</span></span>  
  
6.  <span data-ttu-id="c0c31-116">協調流程會將新訊息放至 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="c0c31-116">The orchestration drops the new message into the MessageBox.</span></span>  
  
7.  <span data-ttu-id="c0c31-117">傳送埠會拾取新訊息，並透過 FILE 配接器傳送至 \Message Enrichment\Out 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0c31-117">The send port picks up the new message and sends it via the FILE adapter to the \Message Enrichment\Out folder.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="c0c31-118">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="c0c31-118">Where to Find This Sample</span></span>  
 <span data-ttu-id="c0c31-119">此範例位於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝資料夾： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message 擴充。</span><span class="sxs-lookup"><span data-stu-id="c0c31-119">This sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\Message Enrichment.</span></span>  
  
 <span data-ttu-id="c0c31-120">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="c0c31-120">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="c0c31-121">檔案</span><span class="sxs-lookup"><span data-stu-id="c0c31-121">File(s)</span></span>|<span data-ttu-id="c0c31-122">Description</span><span class="sxs-lookup"><span data-stu-id="c0c31-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0c31-123">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="c0c31-123">Cleanup.bat</span></span>|<span data-ttu-id="c0c31-124">解除部署範例實例。</span><span class="sxs-lookup"><span data-stu-id="c0c31-124">Undeploys the example scenario.</span></span> <span data-ttu-id="c0c31-125">協調流程的執行個體不得為作用中才能成功。</span><span class="sxs-lookup"><span data-stu-id="c0c31-125">In order for it to succeed there must be no active instances of the orchestration.</span></span> <span data-ttu-id="c0c31-126">否則會失敗。</span><span class="sxs-lookup"><span data-stu-id="c0c31-126">Otherwise, it will fail.</span></span>|  
|<span data-ttu-id="c0c31-127">MessageEnrichment.sln</span><span class="sxs-lookup"><span data-stu-id="c0c31-127">MessageEnrichment.sln</span></span>|<span data-ttu-id="c0c31-128">包含 MessageEnrichment 和 MessageEnrichmentLibrary 專案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-128">Contains the MessageEnrichment and MessageEnrichmentLibrary projects.</span></span>|  
|<span data-ttu-id="c0c31-129">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="c0c31-129">Setup.bat</span></span>|<span data-ttu-id="c0c31-130">部署包含接收埠、傳送埠和協調流程的範例實例。</span><span class="sxs-lookup"><span data-stu-id="c0c31-130">Deploys an example scenario that consists of a receive port, send port, and orchestration.</span></span>|  
|<span data-ttu-id="c0c31-131">EDIFACT_example.edi</span><span class="sxs-lookup"><span data-stu-id="c0c31-131">EDIFACT_example.edi</span></span>|<span data-ttu-id="c0c31-132">為輸入 EDIFACT 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0c31-132">An input EDIFACT message.</span></span>|  
|<span data-ttu-id="c0c31-133">X12_example.edi</span><span class="sxs-lookup"><span data-stu-id="c0c31-133">X12_example.edi</span></span>|<span data-ttu-id="c0c31-134">為輸入 X12 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0c31-134">An input X12 message.</span></span>|  
|<span data-ttu-id="c0c31-135">MessageEnrichment.btproj</span><span class="sxs-lookup"><span data-stu-id="c0c31-135">MessageEnrichment.btproj</span></span>|<span data-ttu-id="c0c31-136">包含 MessageEnrichment 協調流程和結構描述的專案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-136">The project containing the MessageEnrichment orchestrations and schemas.</span></span>|  
|<span data-ttu-id="c0c31-137">MessageEnrichmentBindings.xml</span><span class="sxs-lookup"><span data-stu-id="c0c31-137">MessageEnrichmentBindings.xml</span></span>|<span data-ttu-id="c0c31-138">包含協調流程、連接埠和合作對象繫結的檔案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-138">The file containing bindings for the orchestration, the ports, and the parties.</span></span>|  
|<span data-ttu-id="c0c31-139">MessageEnrichmentOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="c0c31-139">MessageEnrichmentOrchestration.odx</span></span>|<span data-ttu-id="c0c31-140">將標頭附加至訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="c0c31-140">The orchestration that appends the headers to the message.</span></span>|  
|<span data-ttu-id="c0c31-141">MessageEnrichmentOrchestration.odx.cs</span><span class="sxs-lookup"><span data-stu-id="c0c31-141">MessageEnrichmentOrchestration.odx.cs</span></span>|<span data-ttu-id="c0c31-142">將標頭附加至訊息的協調流程程式碼。</span><span class="sxs-lookup"><span data-stu-id="c0c31-142">The orchestration code that appends the headers to the message.</span></span>|  
|<span data-ttu-id="c0c31-143">EFACT_D98B_APERAK.xsd</span><span class="sxs-lookup"><span data-stu-id="c0c31-143">EFACT_D98B_APERAK.xsd</span></span>|<span data-ttu-id="c0c31-144">輸入訊息的 EDIFACT 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0c31-144">The EDIFACT schema for the input message.</span></span>|  
|<span data-ttu-id="c0c31-145">Enriched_EFACT_D98B_APERAK.xsd</span><span class="sxs-lookup"><span data-stu-id="c0c31-145">Enriched_EFACT_D98B_APERAK.xsd</span></span>|<span data-ttu-id="c0c31-146">輸出訊息的 EDIFACT 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0c31-146">The EDIFACT schema for the output message.</span></span>|  
|<span data-ttu-id="c0c31-147">X12_00401_864.xsd</span><span class="sxs-lookup"><span data-stu-id="c0c31-147">X12_00401_864.xsd</span></span>|<span data-ttu-id="c0c31-148">輸入訊息的 X12 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0c31-148">The X12 schema for the input message.</span></span>|  
|<span data-ttu-id="c0c31-149">Enriched_X12_00401_864.xsd</span><span class="sxs-lookup"><span data-stu-id="c0c31-149">Enriched_X12_00401_864.xsd</span></span>|<span data-ttu-id="c0c31-150">輸出訊息的 X12 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0c31-150">The X12 schema for the output message.</span></span>|  
|<span data-ttu-id="c0c31-151">Headers.xsd</span><span class="sxs-lookup"><span data-stu-id="c0c31-151">Headers.xsd</span></span>|<span data-ttu-id="c0c31-152">加入至輸入訊息之標頭的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0c31-152">The schemas for the headers added to the input messages.</span></span>|  
|<span data-ttu-id="c0c31-153">MessageEnrichmentLibrary.csproj</span><span class="sxs-lookup"><span data-stu-id="c0c31-153">MessageEnrichmentLibrary.csproj</span></span>|<span data-ttu-id="c0c31-154">包含 Headers.cs、OrchestrationUtilities.cs 和 ParseHeaders.cs 檔案的專案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-154">The project containing the Headers.cs, OrchestrationUtilities.cs, and ParseHeaders.cs files.</span></span>|  
|<span data-ttu-id="c0c31-155">Headers.cs</span><span class="sxs-lookup"><span data-stu-id="c0c31-155">Headers.cs</span></span>|<span data-ttu-id="c0c31-156">包含代表標頭資料類別。</span><span class="sxs-lookup"><span data-stu-id="c0c31-156">Includes classes representing headers data.</span></span>|  
|<span data-ttu-id="c0c31-157">OrchestrationUtilities.cs</span><span class="sxs-lookup"><span data-stu-id="c0c31-157">OrchestrationUtilities.cs</span></span>|<span data-ttu-id="c0c31-158">包含協調流程所使用的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="c0c31-158">Includes utility methods used by orchestration.</span></span>|  
|<span data-ttu-id="c0c31-159">ParseHeaders.cs</span><span class="sxs-lookup"><span data-stu-id="c0c31-159">ParseHeaders.cs</span></span>|<span data-ttu-id="c0c31-160">包含新訊息中所使用之 UNA 的預設值。</span><span class="sxs-lookup"><span data-stu-id="c0c31-160">Includes the default values for UNA that are used in the new messages.</span></span> <span data-ttu-id="c0c31-161">這些值取自 ParseHeaders.cs 中的 SerializeEDIFACTHeaders 方法。</span><span class="sxs-lookup"><span data-stu-id="c0c31-161">These values are taken from the SerializeEDIFACTHeaders method in ParseHeaders.cs.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="c0c31-162">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="c0c31-162">How to Use This Sample</span></span>  
 <span data-ttu-id="c0c31-163">使用此範例做為附加交換標頭至 EDI 交易集訊息所需動作的實用範例。</span><span class="sxs-lookup"><span data-stu-id="c0c31-163">Use this sample as a working example of the actions required to append interchange headers to EDI transaction-set messages.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="c0c31-164">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="c0c31-164">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="c0c31-165">若要建置和初始化「訊息豐富」範例，必須為此範例建置和部署 BizTalk 專案、設定接收埠和位置，以及設定兩個不同的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c0c31-165">To build and initialize the Message Enrichment sample, you need to build and deploy the BizTalk project for this sample, configure the receive port and location, and configure two different send ports.</span></span>  
  
#### <a name="to-build-and-deploy-the-biztalk-project-for-this-sample"></a><span data-ttu-id="c0c31-166">若要為此範例建置和部署 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="c0c31-166">To build and deploy the BizTalk project for this sample</span></span>  
  
1.  <span data-ttu-id="c0c31-167">使用 Notepad.Exe 開啟[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\MessageEnrichment\\</span><span class="sxs-lookup"><span data-stu-id="c0c31-167">Using Notepad.Exe, open [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\EDI\MessageEnrichment\\</span></span>  
    <span data-ttu-id="c0c31-168">MessageEnrichment\properties\AssemblyInfo.cs 然後在檔案最下方加入下行：</span><span class="sxs-lookup"><span data-stu-id="c0c31-168">MessageEnrichment\properties\AssemblyInfo.cs and add the following line at the bottom of the file:</span></span>  
  
    ```  
    [assembly: Microsoft.XLANGs.BaseTypes.BizTalkAssembly(typeof(Microsoft.BizTalk.XLANGs.BTXEngine.BTXService))]  
    ```  
  
2.  <span data-ttu-id="c0c31-169">儲存修改的 AssemblyInfo.cs 檔案，然後結束 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="c0c31-169">Save the modified AssemblyInfo.cs file and then exit Notepad.</span></span>  
  
3.  <span data-ttu-id="c0c31-170">在命令視窗中，移動至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="c0c31-170">In a command window, move to the following folder:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="c0c31-171">SDK\Samples\EDI\Message 擴充</span><span class="sxs-lookup"><span data-stu-id="c0c31-171">SDK\Samples\EDI\Message Enrichment</span></span>  
  
4.  <span data-ttu-id="c0c31-172">執行**Setup.bat**，它會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c0c31-172">Run **Setup.bat**, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="c0c31-173">建立接收 (**中**) 和傳送 (**出**) \MessageEnrichment 資料夾中建立此範例的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0c31-173">Creates the receive (**in**) and send (**out**) folders for this sample in the \MessageEnrichment folder.</span></span>  
  
    -   <span data-ttu-id="c0c31-174">將金鑰組寫入 MessageEnrichmentLibrary\testkey.snk</span><span class="sxs-lookup"><span data-stu-id="c0c31-174">Writes a key pair to MessageEnrichmentLibrary\testkey.snk</span></span>  
  
    -   <span data-ttu-id="c0c31-175">建置並部署 MessageEnrichmentLibrary.btproj 專案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-175">Builds and deploys the MessageEnrichmentLibrary.btproj project.</span></span>  
  
    -   <span data-ttu-id="c0c31-176">建置並部署 MessageEnrichment.btproj 專案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-176">Builds and deploys the MessageEnrichment.btproj project.</span></span>  
  
    -   <span data-ttu-id="c0c31-177">讀取 MessageEnrichmentBindings.xml 內的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="c0c31-177">Reads binding information in MessageEnrichmentBindings.xml.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c0c31-178">這個專案的繫結需要的 BizTalk 主控件標示為信任的驗證。</span><span class="sxs-lookup"><span data-stu-id="c0c31-178">The binding for this project requires that the BizTalk host is marked as Authentication Trusted.</span></span>  <span data-ttu-id="c0c31-179">若要使用此功能不受信任的主機，修改 MessageEnrichmentBindings.xml 以及如何變更 HostTrusted ="true"的項目，以 HostTrusted ="false"。</span><span class="sxs-lookup"><span data-stu-id="c0c31-179">In order to use this with a host that is not trusted, modify the MessageEnrichmentBindings.xml and change the HostTrusted=”true” entries to HostTrusted=”false”.</span></span>  
  
    -   <span data-ttu-id="c0c31-180">更新協調流程繫結。</span><span class="sxs-lookup"><span data-stu-id="c0c31-180">Updates orchestration bindings.</span></span>  
  
    -   <span data-ttu-id="c0c31-181">更新傳送埠、傳送埠群組和接收埠。</span><span class="sxs-lookup"><span data-stu-id="c0c31-181">Updates send ports, send port groups, and receive ports.</span></span>  
  
    -   <span data-ttu-id="c0c31-182">更新合作對象和登錄。</span><span class="sxs-lookup"><span data-stu-id="c0c31-182">Updates parties and enlistments.</span></span>  
  
    -   <span data-ttu-id="c0c31-183">啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c0c31-183">Starts the send port.</span></span>  
  
    -   <span data-ttu-id="c0c31-184">啟用接收位置。</span><span class="sxs-lookup"><span data-stu-id="c0c31-184">Enables the receive location.</span></span>  
  
    -   <span data-ttu-id="c0c31-185">登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="c0c31-185">Enlists and starts the orchestration.</span></span>  
  
 <span data-ttu-id="c0c31-186">BizTalk Server 現在已準備就緒可使用此範例。</span><span class="sxs-lookup"><span data-stu-id="c0c31-186">BizTalk Server is ready now to work with this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="c0c31-187">執行此範例</span><span class="sxs-lookup"><span data-stu-id="c0c31-187">Running This Sample</span></span>  
 <span data-ttu-id="c0c31-188">使用下列程序執行「訊息豐富」範例。</span><span class="sxs-lookup"><span data-stu-id="c0c31-188">Use the following procedure to run the Message Enrichment sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="c0c31-189">執行此範例</span><span class="sxs-lookup"><span data-stu-id="c0c31-189">To run this sample</span></span>  
  
1.  <span data-ttu-id="c0c31-190">將 EDIFACT_examples.edi 檔案從 \MessageEnrichment\Instances 資料夾複製至 \MessageEnrichment\In 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0c31-190">Copy the EDIFACT_examples.edi file from the \MessageEnrichment\Instances folder into the \MessageEnrichment\In folder.</span></span>  
  
2.  <span data-ttu-id="c0c31-191">確認 EDIFACT_examples.edi 檔案已從 \MessageEnrichment\In 資料夾消失並出現在 \MessageEnrichment\Out 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="c0c31-191">Verify that the EDIFACT_examples.edi files disappears from the \MessageEnrichment\In folder, and appears in the \MessageEnrichment\Out folder.</span></span>  
  
3.  <span data-ttu-id="c0c31-192">開啟 \MessageEnrichment\Out 資料夾內的檔案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-192">Open the file in the \MessageEnrichment\Out folder.</span></span> <span data-ttu-id="c0c31-193">確認 \MessageEnrichment\Instances 資料夾中有 EDIFACT_examples.edi 檔案的 XML 表示法，而且除輸出檔案具有 EDIFACT UNA、UNB 和 UNG 標頭之外，其內容與 EDIFACT_examples.edi 檔案相同。</span><span class="sxs-lookup"><span data-stu-id="c0c31-193">Verify that it is an XML representation of the EDIFACT_examples.edi file in the \MessageEnrichment\Instances folder, and that is has the same contents as the EDIFACT_examples.edi file, with the exception that the output file has EDIFACT UNA, UNB, and UNG headers.</span></span>  
  
4.  <span data-ttu-id="c0c31-194">重複步驟 1 和 2 處理 \MessageEnrichment\Instances 資料夾內的 X12_examples.edi 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-194">Repeat steps 1 and 2 with the X12_examples.edi file from the \MessageEnrichment\Instances folder.</span></span>  
  
5.  <span data-ttu-id="c0c31-195">開啟 \MessageEnrichment\Out 資料夾內的新檔案。</span><span class="sxs-lookup"><span data-stu-id="c0c31-195">Open the new file in the \MessageEnrichment\Out folder.</span></span> <span data-ttu-id="c0c31-196">確認 \MessageEnrichment\Instances 資料夾中有 X12_examples.edi 檔案的 XML 表示法，而且除輸出檔案具有 X12 ISA 標頭之外，其內容與 X12_examples.edi 檔案相同。</span><span class="sxs-lookup"><span data-stu-id="c0c31-196">Verify that it is an XML representation of the X12_examples.edi file in the \MessageEnrichment\Instances folder, and that is has the same contents as the X12_examples.edi file, with the exception that the output file has X12 ISA headers.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="c0c31-197">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="c0c31-197">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="c0c31-198">無</span><span class="sxs-lookup"><span data-stu-id="c0c31-198">None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c31-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0c31-199">See Also</span></span>  
 [<span data-ttu-id="c0c31-200">EDI 和 AS2 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c0c31-200">EDI and AS2 (BizTalk Server Samples Folder)</span></span>](../core/edi-and-as2-biztalk-server-samples-folder.md)