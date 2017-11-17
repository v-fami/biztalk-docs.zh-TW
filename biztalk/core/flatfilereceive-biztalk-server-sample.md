---
title: "FlatFileReceive （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bd9e8d-6ed9-49c4-8437-c0c8b2a9a78d
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e990e402b0b05c530764d578219adccc386b82cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="flatfilereceive-biztalk-server-sample"></a><span data-ttu-id="86ff8-102">FlatFileReceive （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="86ff8-102">FlatFileReceive (BizTalk Server Sample)</span></span>
<span data-ttu-id="86ff8-103">FlatFileReceive 範例會示範如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將一般檔案處理成相等的 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="86ff8-103">The FlatFileReceive sample demonstrates how you can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process a flat file into the equivalent .xml file.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="86ff8-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="86ff8-104">What This Sample Does</span></span>  
 <span data-ttu-id="86ff8-105">此範例將 [FFInput] 資料夾設定為接收位置。</span><span class="sxs-lookup"><span data-stu-id="86ff8-105">This sample configures the folder FFInput as a receive location.</span></span> <span data-ttu-id="86ff8-106">當您將檔案 (例如範例檔案 FlatFileReceive_in.txt) 放置於此資料夾時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會依序使用下列步驟處理此檔案內的訊息。</span><span class="sxs-lookup"><span data-stu-id="86ff8-106">When you place a file, such as the sample file FlatFileReceive_in.txt, into this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message in this file using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="86ff8-107">讀取接收位置內 [FFInput] 資料夾中輸入檔的訊息。</span><span class="sxs-lookup"><span data-stu-id="86ff8-107">Reads the message from the input file in the receive location folder FFInput.</span></span>  
  
2.  <span data-ttu-id="86ff8-108">在接收管線中，「一般檔案解譯器」元件會將訊息由一般檔案格式轉換為相等的 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="86ff8-108">In the receive pipeline, the Flat File Disassembler component converts the message from flat file format to the equivalent XML message.</span></span>  
  
3.  <span data-ttu-id="86ff8-109">在 MessageBox 資料庫中，訊息會路由至 FILE 傳送埠，該傳送埠會將 XML 訊息寫入傳送配接器檔案夾 FFOutput 內的檔案。</span><span class="sxs-lookup"><span data-stu-id="86ff8-109">In the MessageBox database, the message is routed to a FILE send port that writes the XML message to a file in the send adapter folder FFOutput.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="86ff8-110">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="86ff8-110">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="86ff8-111">範例訊息大致指出了此範例的基本設計。</span><span class="sxs-lookup"><span data-stu-id="86ff8-111">The sample message dictates much of the basic design in this sample.</span></span> <span data-ttu-id="86ff8-112">一般檔案訊息必須使用一般檔案解譯器和自訂接收管線內一般檔案結構描述進行反組譯。</span><span class="sxs-lookup"><span data-stu-id="86ff8-112">Flat file messages must be disassembled using the Flat File Disassembler and a flat file schema within a custom receive pipeline.</span></span> <span data-ttu-id="86ff8-113">這些和其他設計元素總結於下表中。</span><span class="sxs-lookup"><span data-stu-id="86ff8-113">These and other design elements are summarized in the following table.</span></span>  
  
|<span data-ttu-id="86ff8-114">設計元素</span><span class="sxs-lookup"><span data-stu-id="86ff8-114">Design element</span></span>|<span data-ttu-id="86ff8-115">已選取的原因</span><span class="sxs-lookup"><span data-stu-id="86ff8-115">Reason(s) selected</span></span>|  
|--------------------|--------------------------|  
|<span data-ttu-id="86ff8-116">自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="86ff8-116">Custom receive pipeline</span></span>|<span data-ttu-id="86ff8-117">-自訂管線會使用一般檔案解譯器和一般檔案結構描述來轉譯內送訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="86ff8-117">-   The custom pipeline uses the Flat File Disassembler and a flat file schema to translate inbound purchase order messages.</span></span> <span data-ttu-id="86ff8-118">「一般檔案解譯器」本身並非管線，在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中設定接收管線時無法使用它。</span><span class="sxs-lookup"><span data-stu-id="86ff8-118">The Flat File Disassembler is not itself a pipeline and cannot be used when configuring a receive pipeline in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management console.</span></span>|  
|<span data-ttu-id="86ff8-119">一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="86ff8-119">Flat file schema</span></span>|<span data-ttu-id="86ff8-120">-定義的所有相同記錄與欄位特性 （包含結構） 的 XML 結構描述，並提供一個機制來定義一般檔案特性，將一般檔案執行個體訊息轉譯成相等的 XML 執行個體所需的所有訊息 （反之亦然）。</span><span class="sxs-lookup"><span data-stu-id="86ff8-120">-   Define all of the same record and field characteristics (including structure) as an XML schema and provide a mechanism for defining all of the flat file characteristics that are required to translate a flat file instance message into an equivalent XML instance message (or vice versa).</span></span>|  
|<span data-ttu-id="86ff8-121">訂閱篩選器</span><span class="sxs-lookup"><span data-stu-id="86ff8-121">Subscription filter</span></span>|<span data-ttu-id="86ff8-122">-訂用帳戶篩選器會執行實際的路由擷取符合根據屬性欄位的一或多個準則的訊息。</span><span class="sxs-lookup"><span data-stu-id="86ff8-122">-   The subscription filter performs the actual routing by capturing messages that meet one or more criteria based on property fields.</span></span>|  
|<span data-ttu-id="86ff8-123">XMLTransmit</span><span class="sxs-lookup"><span data-stu-id="86ff8-123">XMLTransmit</span></span>|<span data-ttu-id="86ff8-124">-執行基本組件外寄 XML 訊息所需。</span><span class="sxs-lookup"><span data-stu-id="86ff8-124">-   Performs basic assembly of outgoing XML messages where needed.</span></span> <span data-ttu-id="86ff8-125">PassThruTransmit 管線不會提供其他支援。</span><span class="sxs-lookup"><span data-stu-id="86ff8-125">The PassThruTransmit pipeline provides no additional support.</span></span>|  
  
 <span data-ttu-id="86ff8-126">這些元素結合後產生的解決方案，可從接收位置接受一般檔案格式的訂單訊息，再將產生的 XML 表示法寫出至傳送位置。</span><span class="sxs-lookup"><span data-stu-id="86ff8-126">These elements are combined to produce a solution that accepts purchase order messages in flat file format from the receive location and writes out the resulting XML representation to the send location.</span></span>  
  
 <span data-ttu-id="86ff8-127">下列考量適用於此範例的設計：</span><span class="sxs-lookup"><span data-stu-id="86ff8-127">The following considerations apply to the design of this sample:</span></span>  
  
-   <span data-ttu-id="86ff8-128">一般檔案結構描述 (PO.xsd) 包含擴充註解，會說明採購訂單一般檔案的結構。</span><span class="sxs-lookup"><span data-stu-id="86ff8-128">The flat file schema (PO.xsd) contains extended annotations describing the structure of the purchase order flat file.</span></span> <span data-ttu-id="86ff8-129">這些檔案可以用手動方式建立，但有不少可以透過 [一般檔案精靈] 產生。</span><span class="sxs-lookup"><span data-stu-id="86ff8-129">These files can be created by hand, but many can be generated by using the Flat File Wizard.</span></span>  
  
-   <span data-ttu-id="86ff8-130">一般檔案結構描述使用的是 Unqualified 的 elementFormDefault 值。</span><span class="sxs-lookup"><span data-stu-id="86ff8-130">The flat file schema uses an elementFormDefault value of Unqualified.</span></span> <span data-ttu-id="86ff8-131">雖然產生的結果正確無誤，但包含其他未預期的 XML 命名空間 (xmlns) 限定性條件。</span><span class="sxs-lookup"><span data-stu-id="86ff8-131">This produces correct results but with additional and unexpected XML namespace (xmlns) qualifications.</span></span> <span data-ttu-id="86ff8-132">使用值為 Qualified 的 elementFormDefault 即可避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="86ff8-132">Use an elementFormDefault of Qualified to avoid this issue.</span></span>  
  
-   <span data-ttu-id="86ff8-133">傳送管線會使用 XmlTransmit。</span><span class="sxs-lookup"><span data-stu-id="86ff8-133">XmlTransmit is used as the send pipeline.</span></span> <span data-ttu-id="86ff8-134">傳送埠不需要屬性降級或其他訊息的處理時，請使用 PassThruTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="86ff8-134">Use the PassThruTransmit pipeline when property demotion or other messaging processing is not required in the send port.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="86ff8-135">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="86ff8-135">Where to Find This Sample</span></span>  
 <span data-ttu-id="86ff8-136">*\<範例路徑 >*\Pipelines\AssemblerDisassembler\FlatFileReceive\\</span><span class="sxs-lookup"><span data-stu-id="86ff8-136">*\<Samples Path>*\Pipelines\AssemblerDisassembler\FlatFileReceive\\</span></span>  
  
 <span data-ttu-id="86ff8-137">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="86ff8-137">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="86ff8-138">檔案</span><span class="sxs-lookup"><span data-stu-id="86ff8-138">File(s)</span></span>|<span data-ttu-id="86ff8-139">Description</span><span class="sxs-lookup"><span data-stu-id="86ff8-139">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86ff8-140">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="86ff8-140">Cleanup.bat</span></span>|<span data-ttu-id="86ff8-141">用來解除部署組件，以及將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="86ff8-141">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="86ff8-142">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="86ff8-142">Removes send and receive ports.</span></span> <span data-ttu-id="86ff8-143">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="86ff8-143">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="86ff8-144">FFReceivePipeline.btp</span><span class="sxs-lookup"><span data-stu-id="86ff8-144">FFReceivePipeline.btp</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="86ff8-145"> 接收管線檔案，含「一般檔案解譯器」元件。</span><span class="sxs-lookup"><span data-stu-id="86ff8-145"> receive pipeline file with the Flat File Disassembler component.</span></span>|  
|<span data-ttu-id="86ff8-146">FlatFileReceive.btproj, FlatFileReceive.sln</span><span class="sxs-lookup"><span data-stu-id="86ff8-146">FlatFileReceive.btproj, FlatFileReceive.sln</span></span>|<span data-ttu-id="86ff8-147">這個範例的專案及解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="86ff8-147">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="86ff8-148">FlatFileReceive_in.txt</span><span class="sxs-lookup"><span data-stu-id="86ff8-148">FlatFileReceive_in.txt</span></span>|<span data-ttu-id="86ff8-149">範例輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="86ff8-149">Sample input file.</span></span>|  
|<span data-ttu-id="86ff8-150">FlatFileReceiveBinding.xml</span><span class="sxs-lookup"><span data-stu-id="86ff8-150">FlatFileReceiveBinding.xml</span></span>|<span data-ttu-id="86ff8-151">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="86ff8-151">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="86ff8-152">PO.xsd</span><span class="sxs-lookup"><span data-stu-id="86ff8-152">PO.xsd</span></span>|<span data-ttu-id="86ff8-153">內送一般檔案的結構描述。</span><span class="sxs-lookup"><span data-stu-id="86ff8-153">Schema for the inbound flat file.</span></span>|  
|<span data-ttu-id="86ff8-154">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="86ff8-154">Setup.bat</span></span>|<span data-ttu-id="86ff8-155">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="86ff8-155">Used to build and initialize this sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="86ff8-156">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="86ff8-156">How to Use This Sample</span></span>  
 <span data-ttu-id="86ff8-157">您可以使用此範例，做為自己的一般檔案處理解決方案基礎。</span><span class="sxs-lookup"><span data-stu-id="86ff8-157">Use this sample as the basis for your own flat file processing solution.</span></span> <span data-ttu-id="86ff8-158">您可以將本範例中所用的許多設計元素加以擴充，以符合自己的需求。</span><span class="sxs-lookup"><span data-stu-id="86ff8-158">You can extend many of the design elements used in this sample to fit your own requirements.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="86ff8-159">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="86ff8-159">Building and Initializing This Sample</span></span>  
  
1.  <span data-ttu-id="86ff8-160">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="86ff8-160">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="86ff8-161">*\<範例路徑 >*\Pipelines\AssemblerDisassembler\FlatFileReceive</span><span class="sxs-lookup"><span data-stu-id="86ff8-161">*\<Samples Path>*\Pipelines\AssemblerDisassembler\FlatFileReceive</span></span>  
  
2.  <span data-ttu-id="86ff8-162">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="86ff8-162">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="86ff8-163">為資料夾內的這個範例建立輸入 (FFInput) 和輸出 (FFOutput) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="86ff8-163">Creates the input (FFInput) and output (FFOutput) folders for this sample in the folder:</span></span>  
  
         <span data-ttu-id="86ff8-164">*\<範例路徑 >*\Pipelines\AssemblerDisassembler\FlatFileReceive</span><span class="sxs-lookup"><span data-stu-id="86ff8-164">*\<Samples Path>*\Pipelines\AssemblerDisassembler\FlatFileReceive</span></span>  
  
    -   <span data-ttu-id="86ff8-165">為這個範例編譯和部署 Visual Studio 專案。</span><span class="sxs-lookup"><span data-stu-id="86ff8-165">Compiles and deploys the Visual Studio project for this sample.</span></span>  
  
    -   <span data-ttu-id="86ff8-166">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="86ff8-166">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="86ff8-167">此範例會顯示下列警告時建立並繫結連接埠：`Warning: Receive handler not specified for receive location "FlatFileReceive_RL"; updating with first receive handler with matching transport type.`您可以放心忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="86ff8-167">This sample displays the following warning when creating and binding ports: `Warning: Receive handler not specified for receive location "FlatFileReceive_RL"; updating with first receive handler with matching transport type.` You can safely ignore these warnings.</span></span> <span data-ttu-id="86ff8-168">(繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。</span><span class="sxs-lookup"><span data-stu-id="86ff8-168">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  
  
    -   <span data-ttu-id="86ff8-169">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="86ff8-169">Enables the receive location, and starts the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86ff8-170">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="86ff8-170">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86ff8-171">如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="86ff8-171">If you choose to open and build the project in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="86ff8-172">請使用這個金鑰組來簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="86ff8-172">Use this key pair to sign the resulting assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86ff8-173">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="86ff8-173">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="86ff8-174">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="86ff8-174">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="86ff8-175">執行此範例</span><span class="sxs-lookup"><span data-stu-id="86ff8-175">Running This Sample</span></span>  
  
1.  <span data-ttu-id="86ff8-176">請將 FlatFileReceive_in.txt 檔案的複本放在 [FFInput] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="86ff8-176">Put a copy of the file FlatFileReceive_in.txt into the folder FFInput.</span></span>  
  
2.  <span data-ttu-id="86ff8-177">觀察建立於 [FFOutput] 資料夾內的 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="86ff8-177">Observe the .xml file created in the folder FFOutput.</span></span> <span data-ttu-id="86ff8-178">輸出檔的名稱的根據是訊息識別碼 GUID。</span><span class="sxs-lookup"><span data-stu-id="86ff8-178">The name of the output file is based on the message ID GUID.</span></span> <span data-ttu-id="86ff8-179">此檔案包含置於接收資料夾內與一般檔案相等的 XML。</span><span class="sxs-lookup"><span data-stu-id="86ff8-179">This file contains XML equivalent of the flat file placed in the receive folder.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="86ff8-180">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="86ff8-180">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="86ff8-181">組態指令碼 Setup.bat 和 Cleanup.bat 依賴下列系統管理 Windows Management Instrumentation (WMI) 指令碼：</span><span class="sxs-lookup"><span data-stu-id="86ff8-181">The configuration scripts Setup.bat and Cleanup.bat rely on the following administrative Windows Management Instrumentation (WMI) scripts:</span></span>  
  
-   <span data-ttu-id="86ff8-182">啟動傳送埠\StartSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="86ff8-182">Start Send Port\StartSendPort.vbs</span></span>  
  
-   <span data-ttu-id="86ff8-183">啟用接收位置\EnableRecLoc</span><span class="sxs-lookup"><span data-stu-id="86ff8-183">Enable Receive Location\EnableRecLoc</span></span>  
  
-   <span data-ttu-id="86ff8-184">移除傳送埠\RemoveSendPort</span><span class="sxs-lookup"><span data-stu-id="86ff8-184">Remove Send Port\RemoveSendPort</span></span>  
  
 <span data-ttu-id="86ff8-185">安裝和清除批次檔使用的是下列 BTSTask：</span><span class="sxs-lookup"><span data-stu-id="86ff8-185">The setup and cleanup batch files use BTSTask as follows:</span></span>  
  
-   <span data-ttu-id="86ff8-186">**BTSTask ImportBindings**套用繫結檔案，並建立應用程式、 連接埠和繫結</span><span class="sxs-lookup"><span data-stu-id="86ff8-186">**BTSTask ImportBindings** to apply the binding file and create the application, ports, and bindings</span></span>  
  
-   <span data-ttu-id="86ff8-187">**BTSTask RemoveApp**用以移除 FlatFileReceiveApplication</span><span class="sxs-lookup"><span data-stu-id="86ff8-187">**BTSTask RemoveApp** to remove the FlatFileReceiveApplication</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86ff8-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86ff8-188">See Also</span></span>  
-  [<span data-ttu-id="86ff8-189">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="86ff8-189">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)   
-  [<span data-ttu-id="86ff8-190">一般檔案解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="86ff8-190">Flat File Disassembler Pipeline Component</span></span>](../core/flat-file-disassembler-pipeline-component.md)   
-  [<span data-ttu-id="86ff8-191">一般檔案結構描述</span><span class="sxs-lookup"><span data-stu-id="86ff8-191">Flat File Schemas</span></span>](../core/flat-file-schemas.md)   
-  [<span data-ttu-id="86ff8-192">預設管線</span><span class="sxs-lookup"><span data-stu-id="86ff8-192">Default Pipelines</span></span>](../core/default-pipelines.md)   
-  <span data-ttu-id="86ff8-193">**WMI 指令碼範例**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="86ff8-193">**WMI Script Samples** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>   
-  [<span data-ttu-id="86ff8-194">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="86ff8-194">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)   
-  [<span data-ttu-id="86ff8-195">FlatFileSend （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="86ff8-195">FlatFileSend (BizTalk Server Sample)</span></span>](../core/flatfilesend-biztalk-server-sample.md)