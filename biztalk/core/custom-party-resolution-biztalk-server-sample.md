---
title: 自訂合作對象解析 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, parties
- pipeline components [custom], examples
- pipeline components [custom], parties
- examples, pipeline components [custom]
- parties, pipeline components [custom]
- parties, custom
ms.assetid: 1f88450f-5fe9-486d-bfb8-fd11181c78b4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7b88d8126a1d63760888edbcd7691ad4bd76426
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238694"
---
# <a name="custom-party-resolution-biztalk-server-sample"></a><span data-ttu-id="5cf4b-102">自訂合作對象解析 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="5cf4b-102">Custom Party Resolution (BizTalk Server Sample)</span></span>
<span data-ttu-id="5cf4b-103">此「自訂合作對象解析」範例示範如何解析自訂合作對象。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-103">The Custom Party Resolution sample demonstrates how to write a custom pipeline component to resolve a custom party.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="5cf4b-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="5cf4b-104">What This Sample Does</span></span>  
 <span data-ttu-id="5cf4b-105">「自訂合作對象解析」範例使用下列步驟完成其工作：</span><span class="sxs-lookup"><span data-stu-id="5cf4b-105">The Custom Party Resolution sample accomplishes its task using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="5cf4b-106">從資料夾擷取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-106">An XML document is retrieved from a folder.</span></span>  
  
2.  <span data-ttu-id="5cf4b-107">管線會解析合作對象。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-107">The pipeline resolves the party.</span></span>  
  
3.  <span data-ttu-id="5cf4b-108">將 XML 訊息寫入資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-108">The XML message is written to a folder.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="5cf4b-109">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="5cf4b-109">Where to Find This Sample</span></span>  
 <span data-ttu-id="5cf4b-110">*\<範例路徑 >* \Pipelines\CustomPartyResolution\\</span><span class="sxs-lookup"><span data-stu-id="5cf4b-110">*\<Samples Path>* \Pipelines\CustomPartyResolution\\</span></span>  
  
 <span data-ttu-id="5cf4b-111">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-111">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="5cf4b-112">檔案</span><span class="sxs-lookup"><span data-stu-id="5cf4b-112">File(s)</span></span>|<span data-ttu-id="5cf4b-113">Description</span><span class="sxs-lookup"><span data-stu-id="5cf4b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5cf4b-114">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="5cf4b-114">AssemblyInfo.cs</span></span>|<span data-ttu-id="5cf4b-115">組件資訊 C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-115">Assembly information C# source file.</span></span>|  
|<span data-ttu-id="5cf4b-116">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="5cf4b-116">Cleanup.bat</span></span>|<span data-ttu-id="5cf4b-117">清除批次檔。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-117">Cleanup batch file.</span></span>|  
|<span data-ttu-id="5cf4b-118">CustomPartyResolution.sln</span><span class="sxs-lookup"><span data-stu-id="5cf4b-118">CustomPartyResolution.sln</span></span>|<span data-ttu-id="5cf4b-119">解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-119">Solution file.</span></span>|  
|<span data-ttu-id="5cf4b-120">CustomPartyResolutionBinding.xml</span><span class="sxs-lookup"><span data-stu-id="5cf4b-120">CustomPartyResolutionBinding.xml</span></span>|<span data-ttu-id="5cf4b-121">繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-121">Binding file.</span></span>|  
|<span data-ttu-id="5cf4b-122">CustomPartyResolutionPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="5cf4b-122">CustomPartyResolutionPipeline.btp</span></span>|<span data-ttu-id="5cf4b-123">管線檔案。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-123">Pipeline file.</span></span>|  
|<span data-ttu-id="5cf4b-124">CustomPartyResolutionPipeline.btproj</span><span class="sxs-lookup"><span data-stu-id="5cf4b-124">CustomPartyResolutionPipeline.btproj</span></span>|<span data-ttu-id="5cf4b-125">管線專案檔。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-125">Pipeline project file.</span></span>|  
|<span data-ttu-id="5cf4b-126">CustomPartyResolutionPipelineComponent.cs</span><span class="sxs-lookup"><span data-stu-id="5cf4b-126">CustomPartyResolutionPipelineComponent.cs</span></span>|<span data-ttu-id="5cf4b-127">管線元件 C# 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-127">Pipeline component C# source code.</span></span>|  
|<span data-ttu-id="5cf4b-128">CustomPartyResolutionPipelineComponent.csproj</span><span class="sxs-lookup"><span data-stu-id="5cf4b-128">CustomPartyResolutionPipelineComponent.csproj</span></span>|<span data-ttu-id="5cf4b-129">管線元件 Visual Studio 專案檔。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-129">Pipeline component Visual Studio project file.</span></span>|  
|<span data-ttu-id="5cf4b-130">InboundDocumentSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="5cf4b-130">InboundDocumentSchema.xsd</span></span>|<span data-ttu-id="5cf4b-131">輸入文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-131">Inbound document schema.</span></span>|  
|<span data-ttu-id="5cf4b-132">PartyResolutionStream.cs</span><span class="sxs-lookup"><span data-stu-id="5cf4b-132">PartyResolutionStream.cs</span></span>|<span data-ttu-id="5cf4b-133">合作對象解析資料流 C# 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-133">Party resolution stream C# source code.</span></span>|  
|<span data-ttu-id="5cf4b-134">RoutingPropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="5cf4b-134">RoutingPropertySchema.xsd</span></span>|<span data-ttu-id="5cf4b-135">路由屬性結構描述檔。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-135">Routing property schema file.</span></span>|  
|<span data-ttu-id="5cf4b-136">SampleInboundDocumentSchema.xml</span><span class="sxs-lookup"><span data-stu-id="5cf4b-136">SampleInboundDocumentSchema.xml</span></span>|<span data-ttu-id="5cf4b-137">輸入文件結構描述檔。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-137">Inbound document schema file.</span></span>|  
|<span data-ttu-id="5cf4b-138">SampleInboundDocumentSchema_Party1.xml</span><span class="sxs-lookup"><span data-stu-id="5cf4b-138">SampleInboundDocumentSchema_Party1.xml</span></span>|<span data-ttu-id="5cf4b-139">範例資料執行個體。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-139">Sample data instance.</span></span>|  
|<span data-ttu-id="5cf4b-140">SampleInboundDocumentSchema_Party2.xml</span><span class="sxs-lookup"><span data-stu-id="5cf4b-140">SampleInboundDocumentSchema_Party2.xml</span></span>|<span data-ttu-id="5cf4b-141">範例資料執行個體。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-141">Sample data instance.</span></span>|  
|<span data-ttu-id="5cf4b-142">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="5cf4b-142">Setup.bat</span></span>|<span data-ttu-id="5cf4b-143">建置和安裝範例管線元件批次檔。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-143">Build and setup sample pipeline component batch file.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="5cf4b-144">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="5cf4b-144">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-custom-party-resolution-sample"></a><span data-ttu-id="5cf4b-145">若要建置和初始化自訂合作對象解析範例</span><span class="sxs-lookup"><span data-stu-id="5cf4b-145">To build and initialize the Custom Party Resolution sample</span></span>  
  
1.  <span data-ttu-id="5cf4b-146">在命令視窗中，將目錄變更 (**cd**) 至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="5cf4b-146">In a command window, change directory (**cd**) to the following folder:</span></span>  
  
     <span data-ttu-id="5cf4b-147">*\<範例路徑 >* \Pipelines\CustomPartyResolution\\</span><span class="sxs-lookup"><span data-stu-id="5cf4b-147">*\<Samples Path>* \Pipelines\CustomPartyResolution\\</span></span>  
  
2.  <span data-ttu-id="5cf4b-148">執行 Setup.bat 檔案，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5cf4b-148">Run the file Setup.bat, which will perform the following actions:</span></span>  
  
    -   <span data-ttu-id="5cf4b-149">建立在範例中使用的輸入和輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-149">Creates the input and output directories used in the sample.</span></span>  
  
    -   <span data-ttu-id="5cf4b-150">產生新的金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-150">Generates a new key file.</span></span>  
  
    -   <span data-ttu-id="5cf4b-151">建置及部署「自訂合作對象解析」管線元件。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-151">Builds and deploys the Custom Party Resolution pipeline component.</span></span>  
  
    -   <span data-ttu-id="5cf4b-152">若要建置的管線元件會將複製*\<安裝路徑 >* \Pipeline Components 目錄。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-152">Copies the built pipeline component to the *\<Installation Path>* \Pipeline Components directory.</span></span>  
  
    -   <span data-ttu-id="5cf4b-153">建立傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-153">Creates the send and receive ports.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cf4b-154">在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-154">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="5cf4b-155">執行此範例</span><span class="sxs-lookup"><span data-stu-id="5cf4b-155">Running This Sample</span></span>  
  
#### <a name="to-run-the-custom-party-resolution-sample"></a><span data-ttu-id="5cf4b-156">若要執行自訂合作對象解析範例</span><span class="sxs-lookup"><span data-stu-id="5cf4b-156">To run the Custom Party Resolution sample</span></span>  
  
1.  <span data-ttu-id="5cf4b-157">將 SampleInboundDocumentSchema_Party1.xml 或 SampleInboundDocumentSchema_Party2.xml 檔案複製到 \In 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-157">Copy to file SampleInboundDocumentSchema_Party1.xml or SampleInboundDocumentSchema_Party2.xml to the \In folder.</span></span>  
  
2.  <span data-ttu-id="5cf4b-158">結果會出現在 \Out 資料夾與檔案名稱*guid*.xml。</span><span class="sxs-lookup"><span data-stu-id="5cf4b-158">The results will appear in the \Out folder with the filename *guid*.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf4b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cf4b-159">See Also</span></span>  
 [<span data-ttu-id="5cf4b-160">管線 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="5cf4b-160">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)