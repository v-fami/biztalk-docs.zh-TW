---
title: 任意 XPath 屬性處理常式 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
ms.assetid: 4eb26c38-5ece-42b0-a28e-73214df1dc41
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f2f59ce48a3d46ebf33889e31a55f9aa452fd17
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25966756"
---
# <a name="arbitrary-xpath-property-handler-biztalk-server-sample"></a><span data-ttu-id="951cd-102">任意 XPath 屬性處理常式 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="951cd-102">Arbitrary XPath Property Handler (BizTalk Server Sample)</span></span>
<span data-ttu-id="951cd-103">「任意 XPath 屬性處理常式」([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 範例) 示範如何撰寫自訂管線元件，以針對提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 XML 文件升級特定屬性。</span><span class="sxs-lookup"><span data-stu-id="951cd-103">The Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample) demonstrates how to write a custom pipeline component to promote specific properties on an XML document that is submitted to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="951cd-104">您可以使用範例中包含的功能來建立自訂規則、組合器和解譯器元件，以評估 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="951cd-104">You can use functionality contained in the sample to create custom regular, assembler, and disassembler components to evaluate XPath expressions.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="951cd-105">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="951cd-105">What This Sample Does</span></span>  
 <span data-ttu-id="951cd-106">此範例包含要進行處理的訂單 (PO) XML 文件 DocInstance.xml，</span><span class="sxs-lookup"><span data-stu-id="951cd-106">The sample includes a purchase order (PO) XML document to process, DocInstance.xml.</span></span> <span data-ttu-id="951cd-107">並且會使用下列步驟來處理 DocInstance.xml：</span><span class="sxs-lookup"><span data-stu-id="951cd-107">The sample uses the following steps to process DocInstance.xml:</span></span>  
  
1.  <span data-ttu-id="951cd-108">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收埠擷取 DocInstance.xml，再由名為「任意 XPath 屬性處理常式」的自訂管線元件處理。</span><span class="sxs-lookup"><span data-stu-id="951cd-108">DocInstance.xml is retrieved by a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive port and processed by a custom pipeline component called Arbitrary XPath Property Handler.</span></span>  
  
2.  <span data-ttu-id="951cd-109">任意 XPath 屬性處理常式元件會升級所有\<價格\>和\<數量\>PO 結構描述中定義具有任意的 XPath 運算式做為項目。</span><span class="sxs-lookup"><span data-stu-id="951cd-109">The arbitrary XPath property handler component promotes all \<Price\> and \<Quantity\> elements with an arbitrary XPath expression as defined in the PO schema.</span></span> <span data-ttu-id="951cd-110">這個 XPath 運算式也包含位置建構，可搭配 PO 文件根項目的模稜兩可子項目使用。</span><span class="sxs-lookup"><span data-stu-id="951cd-110">The XPath expression also contains the position construct for use with ambiguous child elements of the PO document root element.</span></span>  
  
3.  <span data-ttu-id="951cd-111">任意 XPath 屬性處理常式元件判斷訊息類型，並將它升級為訊息內容。</span><span class="sxs-lookup"><span data-stu-id="951cd-111">The arbitrary XPath property handler component determines the message type and promotes it into the message context.</span></span>  
  
4.  <span data-ttu-id="951cd-112">該元件接著將 XML 文件以及升級後的項目傳送至協調流程進一步處理。</span><span class="sxs-lookup"><span data-stu-id="951cd-112">The component then sends the XML document with the promoted elements to an orchestration for further processing.</span></span>  
  
5.  <span data-ttu-id="951cd-113">協調流程存取 PO 文件中的已升級項目，然後計算 PO 中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="951cd-113">The orchestration accesses the promoted elements in the PO document and calculates the total number of items in the PO.</span></span>  
  
6.  <span data-ttu-id="951cd-114">協調流程建立新的 PO 文件，其中包含原始 PO 的資訊以及已更新的總計。</span><span class="sxs-lookup"><span data-stu-id="951cd-114">The orchestration creates a new PO document that contains the information from the original PO as well as the updated total.</span></span>  
  
7.  <span data-ttu-id="951cd-115">將新的 PO 文件寫入至 \Output 目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="951cd-115">The new PO document is written to a file in the \Output directory.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="951cd-116">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="951cd-116">Where to Find This Sample</span></span>  
 <span data-ttu-id="951cd-117">*\<範例路徑\>* \Pipelines\ArbitraryXPathPropertyHandler</span><span class="sxs-lookup"><span data-stu-id="951cd-117">*\<Samples Path\>* \Pipelines\ArbitraryXPathPropertyHandler</span></span>  
  
 <span data-ttu-id="951cd-118">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="951cd-118">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="951cd-119">파일</span><span class="sxs-lookup"><span data-stu-id="951cd-119">File(s)</span></span>|<span data-ttu-id="951cd-120">Description</span><span class="sxs-lookup"><span data-stu-id="951cd-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="951cd-121">ArbitraryXPathPropertyHandler.sln</span><span class="sxs-lookup"><span data-stu-id="951cd-121">ArbitraryXPathPropertyHandler.sln</span></span>|<span data-ttu-id="951cd-122">自訂管線元件解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="951cd-122">Custom pipeline component solution file.</span></span>|  
|<span data-ttu-id="951cd-123">ArbitraryXPathPropertyHandler.resX</span><span class="sxs-lookup"><span data-stu-id="951cd-123">ArbitraryXPathPropertyHandler.resX</span></span>|<span data-ttu-id="951cd-124">資源檔。</span><span class="sxs-lookup"><span data-stu-id="951cd-124">Resource file.</span></span>|  
|<span data-ttu-id="951cd-125">ArbitraryXPathPropertyHandlerComp.cs</span><span class="sxs-lookup"><span data-stu-id="951cd-125">ArbitraryXPathPropertyHandlerComp.cs</span></span>|<span data-ttu-id="951cd-126">主要元件實作。</span><span class="sxs-lookup"><span data-stu-id="951cd-126">Main component implementation.</span></span>|  
|<span data-ttu-id="951cd-127">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="951cd-127">AssemblyInfo.cs</span></span>|<span data-ttu-id="951cd-128">組件資訊。</span><span class="sxs-lookup"><span data-stu-id="951cd-128">Assembly information.</span></span>|  
|<span data-ttu-id="951cd-129">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="951cd-129">Cleanup.bat</span></span>|<span data-ttu-id="951cd-130">範例清除檔。</span><span class="sxs-lookup"><span data-stu-id="951cd-130">Sample cleanup file.</span></span>|  
|<span data-ttu-id="951cd-131">PromotingMap.cs</span><span class="sxs-lookup"><span data-stu-id="951cd-131">PromotingMap.cs</span></span>|<span data-ttu-id="951cd-132">做為原生 CLR 型別對應實作的屬性升級。</span><span class="sxs-lookup"><span data-stu-id="951cd-132">Property promotion as native CLR types map implementation.</span></span>|  
|<span data-ttu-id="951cd-133">PropertyAttributes.cs</span><span class="sxs-lookup"><span data-stu-id="951cd-133">PropertyAttributes.cs</span></span>|<span data-ttu-id="951cd-134">自訂屬性 (Attribute)、屬性 (Property) 描述元和 ICustomTypePropertyDescriptor 實作。</span><span class="sxs-lookup"><span data-stu-id="951cd-134">Custom attributes, property descriptor, and ICustomTypePropertyDescriptor implementation.</span></span>|  
|<span data-ttu-id="951cd-135">SchemaMap.cs</span><span class="sxs-lookup"><span data-stu-id="951cd-135">SchemaMap.cs</span></span>|<span data-ttu-id="951cd-136">從訊息類型到 IDocumentSpec 的結構描述對應，以解析結構描述模稜兩可的情形。</span><span class="sxs-lookup"><span data-stu-id="951cd-136">Schema mapping from message type to IDocumentSpec to resolve schema ambiguity.</span></span>|  
|<span data-ttu-id="951cd-137">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="951cd-137">Setup.bat</span></span>|<span data-ttu-id="951cd-138">建置和安裝範例管線元件。</span><span class="sxs-lookup"><span data-stu-id="951cd-138">Build and setup sample pipeline component.</span></span>|  
|<span data-ttu-id="951cd-139">VirtualStream.cs</span><span class="sxs-lookup"><span data-stu-id="951cd-139">VirtualStream.cs</span></span>|<span data-ttu-id="951cd-140">虛擬資料流實作。</span><span class="sxs-lookup"><span data-stu-id="951cd-140">Virtual stream implementation.</span></span>|  
|<span data-ttu-id="951cd-141">SeekableReadOnlyStream.cs</span><span class="sxs-lookup"><span data-stu-id="951cd-141">SeekableReadOnlyStream.cs</span></span>|<span data-ttu-id="951cd-142">可搜尋的唯讀資料流實作。</span><span class="sxs-lookup"><span data-stu-id="951cd-142">Seekable read-only stream implementation.</span></span>|  
|<span data-ttu-id="951cd-143">ArbitraryXPathSample.sln</span><span class="sxs-lookup"><span data-stu-id="951cd-143">ArbitraryXPathSample.sln</span></span>|<span data-ttu-id="951cd-144">範例協調流程解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="951cd-144">Sample orchestration solution file.</span></span>|  
|<span data-ttu-id="951cd-145">CalculateTotalAmount.odx</span><span class="sxs-lookup"><span data-stu-id="951cd-145">CalculateTotalAmount.odx</span></span>|<span data-ttu-id="951cd-146">範例協調流程。</span><span class="sxs-lookup"><span data-stu-id="951cd-146">Sample orchestration.</span></span>|  
|<span data-ttu-id="951cd-147">PODocument.xsd</span><span class="sxs-lookup"><span data-stu-id="951cd-147">PODocument.xsd</span></span>|<span data-ttu-id="951cd-148">訂單結構描述。</span><span class="sxs-lookup"><span data-stu-id="951cd-148">Purchase order schema.</span></span>|  
|<span data-ttu-id="951cd-149">DocInstance.xml</span><span class="sxs-lookup"><span data-stu-id="951cd-149">DocInstance.xml</span></span>|<span data-ttu-id="951cd-150">範例訂單執行個體。</span><span class="sxs-lookup"><span data-stu-id="951cd-150">Sample purchase order instance.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="951cd-151">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="951cd-151">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="951cd-152">此範例需在同時安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="951cd-152">This sample is designed to run in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment with [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] running on the same machine.</span></span> <span data-ttu-id="951cd-153">如果您的環境不符合此組態，則必須修改「任意 XPath 屬性處理常式」([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 範例)，以指向正確的 SQL Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="951cd-153">If your environment does not match this configuration, you must modify the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample) to point to the correct SQL Server computer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="951cd-154">Setup.bat 會假設您的 Microsoft Windows 安裝目錄為 C:\Windows。</span><span class="sxs-lookup"><span data-stu-id="951cd-154">Setup.bat assumes your Microsoft Windows installation directory is C:\Windows.</span></span> <span data-ttu-id="951cd-155">如果您的 Windows 安裝在其他目錄，則必須修改 ArbitraryXPathPropertyHandler.csproj 檔案，以在全域組件快取中反映 Microsoft.BizTalk.Component.Utilities 組件的位置。</span><span class="sxs-lookup"><span data-stu-id="951cd-155">If your Windows installation is in another directory, you must modify the ArbitraryXPathPropertyHandler.csproj file to reflect the location of the Microsoft.BizTalk.Component.Utilities assembly in the global assembly cache.</span></span> <span data-ttu-id="951cd-156">在 Reference 項目中，變更\<SYSTEMROOT\>至已安裝 Windows 的位置 (例如，C:\WINNT\\)。</span><span class="sxs-lookup"><span data-stu-id="951cd-156">In the Reference element, change \<SYSTEMROOT\> to the location where Windows is installed (for example, C:\WINNT\\).</span></span>  
  
```  
<Reference  
  Name = "Microsoft.BizTalk.Component.Utilities"  
  AssemblyName = "Microsoft.BizTalk.Component.Utilities"  
  HintPath = "<SYSTEMROOT>\assembly\GAC\Microsoft.BizTalk.Component.Utilities\3.0.1.0__31bf3856ad364e35\Microsoft.BizTalk.Component.Utilities.dll"  
/>  
```  
  
 <span data-ttu-id="951cd-157">請使用下列程序，建置並初始化「任意 XPath 屬性處理常式」([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 範例)。</span><span class="sxs-lookup"><span data-stu-id="951cd-157">Use the following procedure to build and initialize the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample).</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="951cd-158">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="951cd-158">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="951cd-159">在命令視窗中，將目錄變更 (**cd**) 至下列資料夾︰</span><span class="sxs-lookup"><span data-stu-id="951cd-159">In a command window, change directories (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="951cd-160">*\<範例路徑\>* \Pipelines\ArbitraryXPathPropertyHandler</span><span class="sxs-lookup"><span data-stu-id="951cd-160">*\<Samples Path\>* \Pipelines\ArbitraryXPathPropertyHandler</span></span>  
  
2.  <span data-ttu-id="951cd-161">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="951cd-161">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="951cd-162">建置「任意 XPath 屬性處理常式」管線元件。</span><span class="sxs-lookup"><span data-stu-id="951cd-162">Builds the Arbitrary XPath Property Handler pipeline component.</span></span>  
  
    -   <span data-ttu-id="951cd-163">複本建立管線元件來*\<安裝路徑\>* \Pipeline Components 目錄。</span><span class="sxs-lookup"><span data-stu-id="951cd-163">Copies built pipeline component to the *\<Installation Path\>* \Pipeline Components directory.</span></span>  
  
    -   <span data-ttu-id="951cd-164">建立傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="951cd-164">Creates the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="951cd-165">建立在範例中使用的輸入和輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="951cd-165">Creates the input and output directories used in the sample.</span></span>  
  
    -   <span data-ttu-id="951cd-166">安裝範例 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程 ArbitraryXPathSample。</span><span class="sxs-lookup"><span data-stu-id="951cd-166">Installs the sample [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration ArbitraryXPathSample.</span></span>  
  
    -   <span data-ttu-id="951cd-167">將連接埠繫結至範例協調流程。</span><span class="sxs-lookup"><span data-stu-id="951cd-167">Binds the ports to the sample orchestration.</span></span>  
  
    -   <span data-ttu-id="951cd-168">啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="951cd-168">Starts the orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="951cd-169">建置和初始化期間應不會出現任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="951cd-169">No errors should be reported during the build and initialization.</span></span> <span data-ttu-id="951cd-170">如果發生錯誤，請確定您已安裝所有必要軟體，而且 Microsoft 建置工具也位於路徑上。</span><span class="sxs-lookup"><span data-stu-id="951cd-170">If any errors occur, make sure that you have all necessary software installed and that Microsoft build tools are available on the path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="951cd-171">若要復原 Setup.bat 所做的變更，必須先從 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理] 主控台停止並重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="951cd-171">To undo changes made by Setup.bat, you must first stop and restart the host instance from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="951cd-172">接著，執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="951cd-172">Next, run Cleanup.bat.</span></span> <span data-ttu-id="951cd-173">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="951cd-173">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="951cd-174">執行此範例</span><span class="sxs-lookup"><span data-stu-id="951cd-174">Running This Sample</span></span>  
 <span data-ttu-id="951cd-175">請使用下列程序，執行「任意 XPath 屬性處理常式」([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 範例)。</span><span class="sxs-lookup"><span data-stu-id="951cd-175">Use the following procedure to run the Arbitrary XPath Property Handler ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Sample).</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="951cd-176">執行此範例</span><span class="sxs-lookup"><span data-stu-id="951cd-176">To run this sample</span></span>  
  
1.  <span data-ttu-id="951cd-177">將訂單 (PO) 檔案 DocInstance.xml 複製到 \Input 目錄。</span><span class="sxs-lookup"><span data-stu-id="951cd-177">Copy the purchase order (PO) file DocInstance.xml to the \Input directory.</span></span> <span data-ttu-id="951cd-178">接收埠會取用這個 PO 檔案，然後將 XML 資料傳送到「任意 XPath 屬性處理常式」管線元件。</span><span class="sxs-lookup"><span data-stu-id="951cd-178">The PO file is picked up by a receive port, which sends the XML data to the Arbitrary XPath Property Handler pipeline component.</span></span>  
  
2.  <span data-ttu-id="951cd-179">檢視 \Output 目錄中的內容。</span><span class="sxs-lookup"><span data-stu-id="951cd-179">View the contents in the \Output directory.</span></span> <span data-ttu-id="951cd-180">請注意，這時會建立新的檔案，其中包含您先前複製到 \Input 目錄之 DocInstance.xml 檔案的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="951cd-180">Notice that a new file is created that contains all the information from the DocInstance.xml file that you copied to the \Input directory.</span></span> <span data-ttu-id="951cd-181">在檔案中的差異在於現在\<TotalAmount\>項目已填入了 po 的總容量。</span><span class="sxs-lookup"><span data-stu-id="951cd-181">The difference in the file is that now the \<TotalAmount\> element has been populated with the total amount for the PO.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="951cd-182">註解</span><span class="sxs-lookup"><span data-stu-id="951cd-182">Comments</span></span>  
 <span data-ttu-id="951cd-183">標準 XPath 運算式是簡單運算式，例如"/ \* [local-name =' 項目名稱 'and ='http://MyUri.org'] /\*[local-name =' 項目名稱 '] / @\*[區域名稱 =' 屬性名稱']"。</span><span class="sxs-lookup"><span data-stu-id="951cd-183">Canonical XPath expressions are simple expressions such as "/\*[local-name()='element-name' and namespaceURI()='http://MyUri.org']/\*[local-name()='element-name']/@\*[local-name='attribute-name']".</span></span>  
  
 <span data-ttu-id="951cd-184">任意 XPath 運算式則可以複雜如 "//element-name//\*[local-name()='element-name' and position()=2]"。</span><span class="sxs-lookup"><span data-stu-id="951cd-184">An arbitrary XPath expression can be as complex as "//element-name//\*[local-name()='element-name' and position()=2]".</span></span> <span data-ttu-id="951cd-185">事實上，如果您的結構描述在 XPath 主體或 XPath 屬性中使用非標準 XPath，便會收到執行階段錯誤，指出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不支援非標準 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="951cd-185">If fact, you will receive a run-time error stating that non-canonical XPath expressions are not supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] if your schema has a non-canonical XPath used in the XPath body or an XPath property.</span></span> <span data-ttu-id="951cd-186">要支援任意 XPath 運算式，解決方法是建立自訂解譯器和組合器元件，以支援任意 XPath 主體和任意 XPath 屬性運算式。</span><span class="sxs-lookup"><span data-stu-id="951cd-186">A solution to support arbitrary XPath expressions is to create custom disassembler and assembler components that support an arbitrary XPath body as well as arbitrary XPath property expressions.</span></span>  
  
 <span data-ttu-id="951cd-187">這個範例會使用自訂管線元件中的下列一連串步驟時 **IComponent.Execute** 實作︰</span><span class="sxs-lookup"><span data-stu-id="951cd-187">This sample uses the following sequence of steps in the custom pipeline component when **IComponent.Execute** is implemented:</span></span>  
  
1.  <span data-ttu-id="951cd-188">透過輸入訊息內文部分資料流建立虛擬可搜尋資料流</span><span class="sxs-lookup"><span data-stu-id="951cd-188">Creates a virtual seekable stream over the input message body part stream.</span></span> <span data-ttu-id="951cd-189">(由於輸入訊息可能很大而且資料流可能無法搜尋，因此它應該只佔用少量的記憶體，而且能夠變更資料流位置)。</span><span class="sxs-lookup"><span data-stu-id="951cd-189">(Because the input message can be large and the stream can be non-seekable, it should have a small memory footprint and be able to change stream positions.)</span></span>  
  
2.  <span data-ttu-id="951cd-190">建立新的外寄訊息並為其建立新的內文部分、指派虛擬資料流給新的內文部分、複製內文部分屬性以及複製訊息內容。</span><span class="sxs-lookup"><span data-stu-id="951cd-190">Creates a new outgoing message and a new body part for it, assigns a virtual stream to the new body part, clones body part properties, and clones message context.</span></span>  
  
3.  <span data-ttu-id="951cd-191">取得輸入訊息的結構描述，或根據設計階段指定的結構描述。</span><span class="sxs-lookup"><span data-stu-id="951cd-191">Gets a schema for the input message or based on schemas specified during design time.</span></span>  
  
4.  <span data-ttu-id="951cd-192">載入的執行個體中的資料流 **System.Xml.XmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="951cd-192">Loads the stream into an instance of **System.Xml.XmlDocument**.</span></span>  
  
5.  <span data-ttu-id="951cd-193">逐一查看升級後的屬性和辨別欄位，再將它們升級或寫入至外寄訊息的訊息內容中。</span><span class="sxs-lookup"><span data-stu-id="951cd-193">Walks through promoted properties and distinguished fields and promotes or writes them to the message context of the outgoing message.</span></span>  
  
6.  <span data-ttu-id="951cd-194">傳回外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="951cd-194">Returns the outgoing message.</span></span>  
  
7.  <span data-ttu-id="951cd-195">將外寄訊息寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="951cd-195">Writes the outgoing message to a file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951cd-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="951cd-196">See Also</span></span>  
 [<span data-ttu-id="951cd-197">管線 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="951cd-197">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)