---
title: "結構描述解析程式元件 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Flat File Disassembler [pipeline component], examples
- examples, schemas
- schemas, examples
- examples, Flat File Disassembler [pipeline component]
ms.assetid: 9ef68988-c4ee-42d5-83b5-a5c978b2007d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22b59a0606b3cb30827078e28a89d0a51f52c430
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="schema-resolver-component-biztalk-server-sample"></a><span data-ttu-id="f0909-102">結構描述解析程式元件 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="f0909-102">Schema Resolver Component (BizTalk Server Sample)</span></span>
<span data-ttu-id="f0909-103">「結構描述解析程式元件」範例會示範如何擴充 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一般檔案解譯器元件的功能。</span><span class="sxs-lookup"><span data-stu-id="f0909-103">The Schema Resolver Component sample demonstrates how to extend the functionality of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] flat file disassembler component.</span></span>  
  
 <span data-ttu-id="f0909-104">一般檔案解譯器元件通常需要在設計階段定義剖析結構描述。</span><span class="sxs-lookup"><span data-stu-id="f0909-104">The flat file disassembler component normally requires you to define a parsing schema at design time.</span></span> <span data-ttu-id="f0909-105">因此，若您希望在同一個接收位置接收不同的一般檔案文件，通常需要在接收管線加入數個一般檔案解譯器，每個結構描述一個。</span><span class="sxs-lookup"><span data-stu-id="f0909-105">So if you expect to receive different flat file documents on the same receive location, you typically include several flat file disassemblers in the receive pipeline, one for each schema.</span></span> <span data-ttu-id="f0909-106">在設計階段，會使用管線探查機制選取正確的解譯器元件。</span><span class="sxs-lookup"><span data-stu-id="f0909-106">At run time, the correct disassembler component is selected using a pipeline probing mechanism.</span></span> <span data-ttu-id="f0909-107">不過，這個方法是高度耗費資源，如果您有多個一般檔案結構描述，因為探查每個對應的解譯器元件會使管線效能降低。</span><span class="sxs-lookup"><span data-stu-id="f0909-107">However, this approach is expensive if you have many flat file schemas because probing for every corresponding disassembler component degrades pipeline performance.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="f0909-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="f0909-108">What This Sample Does</span></span>  
 <span data-ttu-id="f0909-109">「結構描述解析程式」元件會示範選取一般檔案解譯器的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f0909-109">The Schema Resolver component demonstrates an alternative method of selecting the schema for a flat file disassembler.</span></span> <span data-ttu-id="f0909-110">在此範例中會定義四個結構描述，而每個結構描述訊息的前兩個字元都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f0909-110">In this sample, four schemas are defined and the first two characters of a message for each schema are unique.</span></span> <span data-ttu-id="f0909-111">會定義唯一的前兩個字元與對應的結構描述之間的對應。</span><span class="sxs-lookup"><span data-stu-id="f0909-111">A mapping is defined between the unique first two characters and the corresponding schema.</span></span> <span data-ttu-id="f0909-112">「結構描述解析程式」元件收到輸入訊息時，會讀取前兩個字元，判斷要為對應文件使用哪一個結構描述，再將結構描述資訊儲存於訊息內容，然後呼叫標準一般檔案解譯器元件。</span><span class="sxs-lookup"><span data-stu-id="f0909-112">When the input message is given to the Schema Resolver component, it reads the first two characters, determines which schema to use for the corresponding document, saves the schema information on the message context, and then calls into the standard flat file disassembler component.</span></span> <span data-ttu-id="f0909-113">標準一般檔案解譯器元件會從訊息內容讀取結構描述資訊，並用該結構描述剖析文件。</span><span class="sxs-lookup"><span data-stu-id="f0909-113">The standard flat file disassembler component reads the schema information from the message context and uses that schema to parse the document.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="f0909-114">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="f0909-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="f0909-115">*\<範例路徑\>*\Pipelines\SchemaResolverComponent\\</span><span class="sxs-lookup"><span data-stu-id="f0909-115">*\<Samples Path\>*\Pipelines\SchemaResolverComponent\\</span></span>  
  
 <span data-ttu-id="f0909-116">下表顯示此範例所用的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="f0909-116">The following table shows the files used in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="f0909-117">檔案</span><span class="sxs-lookup"><span data-stu-id="f0909-117">File(s)</span></span>|<span data-ttu-id="f0909-118">Description</span><span class="sxs-lookup"><span data-stu-id="f0909-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0909-119">SchemaResolverSample.sln</span><span class="sxs-lookup"><span data-stu-id="f0909-119">SchemaResolverSample.sln</span></span>|<span data-ttu-id="f0909-120">執行自訂管線元件的 BizTalk 專案解決方案。</span><span class="sxs-lookup"><span data-stu-id="f0909-120">Solution for the BizTalk project that exercises the custom pipeline component.</span></span>|  
|<span data-ttu-id="f0909-121">SchemaResolverSample.btproj</span><span class="sxs-lookup"><span data-stu-id="f0909-121">SchemaResolverSample.btproj</span></span>|<span data-ttu-id="f0909-122">執行自訂管線元件的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f0909-122">BizTalk project that exercises the custom pipeline component.</span></span>|  
|<span data-ttu-id="f0909-123">SchemaResolverRP.btp</span><span class="sxs-lookup"><span data-stu-id="f0909-123">SchemaResolverRP.btp</span></span>|<span data-ttu-id="f0909-124">包含自訂元件的接收管線。</span><span class="sxs-lookup"><span data-stu-id="f0909-124">Receive pipeline that contains the custom component.</span></span>|  
|<span data-ttu-id="f0909-125">PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd</span><span class="sxs-lookup"><span data-stu-id="f0909-125">PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd</span></span>|<span data-ttu-id="f0909-126">一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="f0909-126">Flat file schemas.</span></span>|  
|<span data-ttu-id="f0909-127">POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt</span><span class="sxs-lookup"><span data-stu-id="f0909-127">POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt</span></span>|<span data-ttu-id="f0909-128">對應的一般檔案文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="f0909-128">Corresponding flat file document instances.</span></span>|  
|<span data-ttu-id="f0909-129">SchemaResolverFlatFileDasm.sln</span><span class="sxs-lookup"><span data-stu-id="f0909-129">SchemaResolverFlatFileDasm.sln</span></span>|<span data-ttu-id="f0909-130">管線元件實作的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f0909-130">Solution for the implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="f0909-131">SchemaResolverFlatFileDasm.csproj</span><span class="sxs-lookup"><span data-stu-id="f0909-131">SchemaResolverFlatFileDasm.csproj</span></span>|<span data-ttu-id="f0909-132">管線元件實作的 C# 專案。</span><span class="sxs-lookup"><span data-stu-id="f0909-132">C# project for the implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="f0909-133">SchemaResolverFlatFileDasmComp.cs</span><span class="sxs-lookup"><span data-stu-id="f0909-133">SchemaResolverFlatFileDasmComp.cs</span></span>|<span data-ttu-id="f0909-134">管線元件的實作。</span><span class="sxs-lookup"><span data-stu-id="f0909-134">Implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="f0909-135">SeekableReadOnlyStream.cs</span><span class="sxs-lookup"><span data-stu-id="f0909-135">SeekableReadOnlyStream.cs</span></span>|<span data-ttu-id="f0909-136">元件所用之可搜尋唯讀資料流的實作。</span><span class="sxs-lookup"><span data-stu-id="f0909-136">Implementation of the seekable read-only stream used by component.</span></span>|  
|<span data-ttu-id="f0909-137">VirtualStream.cs</span><span class="sxs-lookup"><span data-stu-id="f0909-137">VirtualStream.cs</span></span>|<span data-ttu-id="f0909-138">管線元件所用之虛擬資料流的實作。</span><span class="sxs-lookup"><span data-stu-id="f0909-138">Implementation of the virtual stream used by pipeline component.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="f0909-139">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="f0909-139">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="f0909-140">請使用下列程序，建置和初始化「結構描述解析程式元件」範例。</span><span class="sxs-lookup"><span data-stu-id="f0909-140">Use the following procedure to build and initialize the Schema Resolver Component sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="f0909-141">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="f0909-141">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="f0909-142">在命令視窗中，將目錄變更 (cd) 至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="f0909-142">In a command window, change directory (cd) to the following folder:</span></span>  
  
     <span data-ttu-id="f0909-143">*\<範例路徑\>*\Pipelines\SchemaResolverComponent</span><span class="sxs-lookup"><span data-stu-id="f0909-143">*\<Samples Path\>*\Pipelines\SchemaResolverComponent</span></span>  
  
2.  <span data-ttu-id="f0909-144">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f0909-144">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="f0909-145">建置元件。</span><span class="sxs-lookup"><span data-stu-id="f0909-145">Builds the component.</span></span>  
  
    -   <span data-ttu-id="f0909-146">將元件組件複製至 BizTalk \Pipeline 元件資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0909-146">Copies the component assembly into the BizTalk \Pipeline components folder.</span></span>  
  
    -   <span data-ttu-id="f0909-147">建置和部署範例 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f0909-147">Builds and deploys the sample BizTalk project.</span></span>  
  
    -   <span data-ttu-id="f0909-148">設定並啟動接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f0909-148">Configures the receive location and send port, and starts them.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0909-149">在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="f0909-149">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="f0909-150">執行此範例</span><span class="sxs-lookup"><span data-stu-id="f0909-150">Running This Sample</span></span>  
 <span data-ttu-id="f0909-151">請使用下列程序，執行「結構描述解析程式元件」範例。</span><span class="sxs-lookup"><span data-stu-id="f0909-151">Use the following procedure to run the Schema Resolver Component sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="f0909-152">執行此範例</span><span class="sxs-lookup"><span data-stu-id="f0909-152">To run this sample</span></span>  
  
1.  <span data-ttu-id="f0909-153">POInstance.txt、 PRInstance.txt、 SOInstance.txt 和 SRInstance.txt 檔案放入接收位置\<*安裝路徑*\>\SDK\Samples\Pipelines\SchemaResolverComponent\In</span><span class="sxs-lookup"><span data-stu-id="f0909-153">Drop the POInstance.txt, PRInstance.txt, SOInstance.txt, and SRInstance.txt files into the receive location \<*Installation Path*\>\SDK\Samples\Pipelines\SchemaResolverComponent\In</span></span>  
  
2.  <span data-ttu-id="f0909-154">觀察寫入的四個.xml 檔案\<Installdir\>\SDK\Samples\Pipelines\SchemaResolverComponent\Out 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0909-154">Observe the four .xml files written to the \<Installdir\>\SDK\Samples\Pipelines\SchemaResolverComponent\Out folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0909-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0909-155">See Also</span></span>  
 [<span data-ttu-id="f0909-156">管線 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="f0909-156">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)