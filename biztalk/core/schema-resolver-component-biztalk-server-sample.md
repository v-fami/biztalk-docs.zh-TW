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
ms.openlocfilehash: 37ec562cbc64d15e66d2f265c52606817169bb85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-resolver-component-biztalk-server-sample"></a><span data-ttu-id="34557-102">結構描述解析程式元件 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="34557-102">Schema Resolver Component (BizTalk Server Sample)</span></span>
<span data-ttu-id="34557-103">「結構描述解析程式元件」範例會示範如何擴充 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一般檔案解譯器元件的功能。</span><span class="sxs-lookup"><span data-stu-id="34557-103">The Schema Resolver Component sample demonstrates how to extend the functionality of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] flat file disassembler component.</span></span>  
  
 <span data-ttu-id="34557-104">一般檔案解譯器元件通常需要在設計階段定義剖析結構描述。</span><span class="sxs-lookup"><span data-stu-id="34557-104">The flat file disassembler component normally requires you to define a parsing schema at design time.</span></span> <span data-ttu-id="34557-105">因此，若您希望在同一個接收位置接收不同的一般檔案文件，通常需要在接收管線加入數個一般檔案解譯器，每個結構描述一個。</span><span class="sxs-lookup"><span data-stu-id="34557-105">So if you expect to receive different flat file documents on the same receive location, you typically include several flat file disassemblers in the receive pipeline, one for each schema.</span></span> <span data-ttu-id="34557-106">在設計階段，會使用管線探查機制選取正確的解譯器元件。</span><span class="sxs-lookup"><span data-stu-id="34557-106">At run time, the correct disassembler component is selected using a pipeline probing mechanism.</span></span> <span data-ttu-id="34557-107">不過，這個方法是高度耗費資源，如果您有多個一般檔案結構描述，因為探查每個對應的解譯器元件會使管線效能降低。</span><span class="sxs-lookup"><span data-stu-id="34557-107">However, this approach is expensive if you have many flat file schemas because probing for every corresponding disassembler component degrades pipeline performance.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="34557-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="34557-108">What This Sample Does</span></span>  
 <span data-ttu-id="34557-109">「結構描述解析程式」元件會示範選取一般檔案解譯器的替代方法。</span><span class="sxs-lookup"><span data-stu-id="34557-109">The Schema Resolver component demonstrates an alternative method of selecting the schema for a flat file disassembler.</span></span> <span data-ttu-id="34557-110">在此範例中會定義四個結構描述，而每個結構描述訊息的前兩個字元都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="34557-110">In this sample, four schemas are defined and the first two characters of a message for each schema are unique.</span></span> <span data-ttu-id="34557-111">會定義唯一的前兩個字元與對應的結構描述之間的對應。</span><span class="sxs-lookup"><span data-stu-id="34557-111">A mapping is defined between the unique first two characters and the corresponding schema.</span></span> <span data-ttu-id="34557-112">「結構描述解析程式」元件收到輸入訊息時，會讀取前兩個字元，判斷要為對應文件使用哪一個結構描述，再將結構描述資訊儲存於訊息內容，然後呼叫標準一般檔案解譯器元件。</span><span class="sxs-lookup"><span data-stu-id="34557-112">When the input message is given to the Schema Resolver component, it reads the first two characters, determines which schema to use for the corresponding document, saves the schema information on the message context, and then calls into the standard flat file disassembler component.</span></span> <span data-ttu-id="34557-113">標準一般檔案解譯器元件會從訊息內容讀取結構描述資訊，並用該結構描述剖析文件。</span><span class="sxs-lookup"><span data-stu-id="34557-113">The standard flat file disassembler component reads the schema information from the message context and uses that schema to parse the document.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="34557-114">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="34557-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="34557-115">*\<範例路徑 >*\Pipelines\SchemaResolverComponent\\</span><span class="sxs-lookup"><span data-stu-id="34557-115">*\<Samples Path>*\Pipelines\SchemaResolverComponent\\</span></span>  
  
 <span data-ttu-id="34557-116">下表顯示此範例所用的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="34557-116">The following table shows the files used in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="34557-117">檔案</span><span class="sxs-lookup"><span data-stu-id="34557-117">File(s)</span></span>|<span data-ttu-id="34557-118">Description</span><span class="sxs-lookup"><span data-stu-id="34557-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34557-119">SchemaResolverSample.sln</span><span class="sxs-lookup"><span data-stu-id="34557-119">SchemaResolverSample.sln</span></span>|<span data-ttu-id="34557-120">執行自訂管線元件的 BizTalk 專案解決方案。</span><span class="sxs-lookup"><span data-stu-id="34557-120">Solution for the BizTalk project that exercises the custom pipeline component.</span></span>|  
|<span data-ttu-id="34557-121">SchemaResolverSample.btproj</span><span class="sxs-lookup"><span data-stu-id="34557-121">SchemaResolverSample.btproj</span></span>|<span data-ttu-id="34557-122">執行自訂管線元件的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="34557-122">BizTalk project that exercises the custom pipeline component.</span></span>|  
|<span data-ttu-id="34557-123">SchemaResolverRP.btp</span><span class="sxs-lookup"><span data-stu-id="34557-123">SchemaResolverRP.btp</span></span>|<span data-ttu-id="34557-124">包含自訂元件的接收管線。</span><span class="sxs-lookup"><span data-stu-id="34557-124">Receive pipeline that contains the custom component.</span></span>|  
|<span data-ttu-id="34557-125">PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd</span><span class="sxs-lookup"><span data-stu-id="34557-125">PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd</span></span>|<span data-ttu-id="34557-126">一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="34557-126">Flat file schemas.</span></span>|  
|<span data-ttu-id="34557-127">POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt</span><span class="sxs-lookup"><span data-stu-id="34557-127">POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt</span></span>|<span data-ttu-id="34557-128">對應的一般檔案文件執行個體。</span><span class="sxs-lookup"><span data-stu-id="34557-128">Corresponding flat file document instances.</span></span>|  
|<span data-ttu-id="34557-129">SchemaResolverFlatFileDasm.sln</span><span class="sxs-lookup"><span data-stu-id="34557-129">SchemaResolverFlatFileDasm.sln</span></span>|<span data-ttu-id="34557-130">管線元件實作的解決方案。</span><span class="sxs-lookup"><span data-stu-id="34557-130">Solution for the implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="34557-131">SchemaResolverFlatFileDasm.csproj</span><span class="sxs-lookup"><span data-stu-id="34557-131">SchemaResolverFlatFileDasm.csproj</span></span>|<span data-ttu-id="34557-132">管線元件實作的 C# 專案。</span><span class="sxs-lookup"><span data-stu-id="34557-132">C# project for the implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="34557-133">SchemaResolverFlatFileDasmComp.cs</span><span class="sxs-lookup"><span data-stu-id="34557-133">SchemaResolverFlatFileDasmComp.cs</span></span>|<span data-ttu-id="34557-134">管線元件的實作。</span><span class="sxs-lookup"><span data-stu-id="34557-134">Implementation of the pipeline component.</span></span>|  
|<span data-ttu-id="34557-135">SeekableReadOnlyStream.cs</span><span class="sxs-lookup"><span data-stu-id="34557-135">SeekableReadOnlyStream.cs</span></span>|<span data-ttu-id="34557-136">元件所用之可搜尋唯讀資料流的實作。</span><span class="sxs-lookup"><span data-stu-id="34557-136">Implementation of the seekable read-only stream used by component.</span></span>|  
|<span data-ttu-id="34557-137">VirtualStream.cs</span><span class="sxs-lookup"><span data-stu-id="34557-137">VirtualStream.cs</span></span>|<span data-ttu-id="34557-138">管線元件所用之虛擬資料流的實作。</span><span class="sxs-lookup"><span data-stu-id="34557-138">Implementation of the virtual stream used by pipeline component.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="34557-139">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="34557-139">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="34557-140">請使用下列程序，建置和初始化「結構描述解析程式元件」範例。</span><span class="sxs-lookup"><span data-stu-id="34557-140">Use the following procedure to build and initialize the Schema Resolver Component sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="34557-141">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="34557-141">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="34557-142">在命令視窗中，將目錄變更 (cd) 至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="34557-142">In a command window, change directory (cd) to the following folder:</span></span>  
  
     <span data-ttu-id="34557-143">*\<範例路徑 >*\Pipelines\SchemaResolverComponent</span><span class="sxs-lookup"><span data-stu-id="34557-143">*\<Samples Path>*\Pipelines\SchemaResolverComponent</span></span>  
  
2.  <span data-ttu-id="34557-144">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="34557-144">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="34557-145">建置元件。</span><span class="sxs-lookup"><span data-stu-id="34557-145">Builds the component.</span></span>  
  
    -   <span data-ttu-id="34557-146">將元件組件複製至 BizTalk \Pipeline 元件資料夾。</span><span class="sxs-lookup"><span data-stu-id="34557-146">Copies the component assembly into the BizTalk \Pipeline components folder.</span></span>  
  
    -   <span data-ttu-id="34557-147">建置和部署範例 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="34557-147">Builds and deploys the sample BizTalk project.</span></span>  
  
    -   <span data-ttu-id="34557-148">設定並啟動接收位置和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="34557-148">Configures the receive location and send port, and starts them.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34557-149">在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="34557-149">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="34557-150">執行此範例</span><span class="sxs-lookup"><span data-stu-id="34557-150">Running This Sample</span></span>  
 <span data-ttu-id="34557-151">請使用下列程序，執行「結構描述解析程式元件」範例。</span><span class="sxs-lookup"><span data-stu-id="34557-151">Use the following procedure to run the Schema Resolver Component sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="34557-152">執行此範例</span><span class="sxs-lookup"><span data-stu-id="34557-152">To run this sample</span></span>  
  
1.  <span data-ttu-id="34557-153">POInstance.txt、 PRInstance.txt、 SOInstance.txt 和 SRInstance.txt 檔案放入接收位置\<*安裝路徑*> \SDK\Samples\Pipelines\SchemaResolverComponent\In</span><span class="sxs-lookup"><span data-stu-id="34557-153">Drop the POInstance.txt, PRInstance.txt, SOInstance.txt, and SRInstance.txt files into the receive location \<*Installation Path*>\SDK\Samples\Pipelines\SchemaResolverComponent\In</span></span>  
  
2.  <span data-ttu-id="34557-154">觀察寫入的四個.xml 檔案\<Installdir > \SDK\Samples\Pipelines\SchemaResolverComponent\Out 資料夾。</span><span class="sxs-lookup"><span data-stu-id="34557-154">Observe the four .xml files written to the \<Installdir>\SDK\Samples\Pipelines\SchemaResolverComponent\Out folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34557-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34557-155">See Also</span></span>  
 [<span data-ttu-id="34557-156">管線 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="34557-156">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)