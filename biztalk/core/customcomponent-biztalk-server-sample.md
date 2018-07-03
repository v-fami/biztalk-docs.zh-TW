---
title: CustomComponent （BizTalk Server 範例） |Microsoft Docs
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
- messages, streamed
- pipeline components [custom], configuring
ms.assetid: ed0da9f5-8cc7-4528-be8c-35b80744fd38
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f46fe74b6cd8618cdc218048ea057e6968f2d99f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019351"
---
# <a name="customcomponent-biztalk-server-sample"></a><span data-ttu-id="1d31d-102">CustomComponent （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="1d31d-102">CustomComponent (BizTalk Server Sample)</span></span>
<span data-ttu-id="1d31d-103">此 CustomComponent 範例會示範如何建立和使用會修改資料流處理訊息的自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="1d31d-103">The CustomComponent sample demonstrates how to create and use a custom pipeline component that modifies a streamed message.</span></span> <span data-ttu-id="1d31d-104">這個範例也會示範使用「管線設計師」對自訂管線元件的設定。</span><span class="sxs-lookup"><span data-stu-id="1d31d-104">This sample also demonstrates the configuration of a custom pipeline component in Pipeline Designer.</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="1d31d-105">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="1d31d-105">What This Sample Does</span></span>  
 <span data-ttu-id="1d31d-106">這個範例會實作自訂管線元件，該元件可以在輸入訊息之前加上字串或是附加字串。</span><span class="sxs-lookup"><span data-stu-id="1d31d-106">This sample implements a custom pipeline component that can prefix or append strings to the input message.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1d31d-107"> 處理資料流處理模式中，這表示整個訊息永遠不會載入記憶體中的訊息。</span><span class="sxs-lookup"><span data-stu-id="1d31d-107"> processes the message in streaming mode, meaning that the entire message is never loaded into memory.</span></span> <span data-ttu-id="1d31d-108">自訂管線元件的示範會依下列步驟順序進行：</span><span class="sxs-lookup"><span data-stu-id="1d31d-108">The custom pipeline component is demonstrated using the following sequence of steps:</span></span>  

1. <span data-ttu-id="1d31d-109">BizTalk 從特定資料夾中的檔案擷取文字訊息。</span><span class="sxs-lookup"><span data-stu-id="1d31d-109">BizTalk retrieves a text message from a file in a specific folder.</span></span>  

2. <span data-ttu-id="1d31d-110">該文字訊息會透過包含 FixMsg 自訂管線元件的接收管線來傳送。</span><span class="sxs-lookup"><span data-stu-id="1d31d-110">The text message is sent through a receive pipeline containing the FixMsg custom pipeline component.</span></span> <span data-ttu-id="1d31d-111">您會設定這個元件，將字串插入到訊息的開頭。</span><span class="sxs-lookup"><span data-stu-id="1d31d-111">You configure this component to insert a string at the beginning of the message.</span></span>  

3. <span data-ttu-id="1d31d-112">您會使用 FixMsg 自訂管線元件，透過傳送管線來傳送產生的文字訊息。</span><span class="sxs-lookup"><span data-stu-id="1d31d-112">You send the resulting text message through a send pipeline with the FixMsg custom pipeline component.</span></span> <span data-ttu-id="1d31d-113">您會將這個元件設定成將字串附加到訊息的結尾。</span><span class="sxs-lookup"><span data-stu-id="1d31d-113">You configure the component to append a string to the end of the message.</span></span>  

4. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1d31d-114"> 會將產生的文字訊息寫入到特定資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="1d31d-114"> writes the resulting text message to a file in a specific folder.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="1d31d-115">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="1d31d-115">Where to Find This Sample</span></span>  
 <span data-ttu-id="1d31d-116">\<*範例路徑*\>\Pipelines\CustomComponent\\</span><span class="sxs-lookup"><span data-stu-id="1d31d-116">\<*Samples Path*\>\Pipelines\CustomComponent\\</span></span>  

 <span data-ttu-id="1d31d-117">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="1d31d-117">The following table shows the files in this sample and describes their purpose.</span></span>  


|                                                     <span data-ttu-id="1d31d-118">檔案</span><span class="sxs-lookup"><span data-stu-id="1d31d-118">File(s)</span></span>                                                     |                                                                                              <span data-ttu-id="1d31d-119">描述</span><span class="sxs-lookup"><span data-stu-id="1d31d-119">Description</span></span>                                                                                               |
|-----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                   <span data-ttu-id="1d31d-120">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="1d31d-120">Cleanup.bat</span></span>                                                   | <span data-ttu-id="1d31d-121">用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。</span><span class="sxs-lookup"><span data-stu-id="1d31d-121">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="1d31d-122">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="1d31d-122">Removes send and receive ports.</span></span> <span data-ttu-id="1d31d-123">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="1d31d-123">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span> |
|                                                    <span data-ttu-id="1d31d-124">Input.txt</span><span class="sxs-lookup"><span data-stu-id="1d31d-124">Input.txt</span></span>                                                    |                                                                                           <span data-ttu-id="1d31d-125">範例輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="1d31d-125">Sample input file.</span></span>                                                                                           |
|                                                    <span data-ttu-id="1d31d-126">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="1d31d-126">Setup.bat</span></span>                                                    |                                                                               <span data-ttu-id="1d31d-127">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="1d31d-127">Used to build and initialize this sample.</span></span>                                                                                |
|                  <span data-ttu-id="1d31d-128">在 \FixMsg 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="1d31d-128">In the \FixMsg folder:</span></span><br /><br /> <span data-ttu-id="1d31d-129">AssemblyInfo.cs、FixMsg.csproj、FixMsg.sln</span><span class="sxs-lookup"><span data-stu-id="1d31d-129">AssemblyInfo.cs, FixMsg.csproj, FixMsg.sln</span></span>                  |                                              <span data-ttu-id="1d31d-130">此範例之自訂管線元件部分的專案、方案及組件資訊檔案。</span><span class="sxs-lookup"><span data-stu-id="1d31d-130">Project, solution, and assembly information files for the custom pipeline component portion of this sample.</span></span>                                               |
|                                  <span data-ttu-id="1d31d-131">在 \FixMsg 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="1d31d-131">In the \FixMsg folder:</span></span><br /><br /> <span data-ttu-id="1d31d-132">FixMsg.cs</span><span class="sxs-lookup"><span data-stu-id="1d31d-132">FixMsg.cs</span></span>                                   |                                                                             <span data-ttu-id="1d31d-133">實作管線元件介面。</span><span class="sxs-lookup"><span data-stu-id="1d31d-133">Implements the pipeline component interfaces.</span></span>                                                                              |
|                               <span data-ttu-id="1d31d-134">在 \FixMsg 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="1d31d-134">In the \FixMsg folder:</span></span><br /><br /> <span data-ttu-id="1d31d-135">FixMsgStream.cs</span><span class="sxs-lookup"><span data-stu-id="1d31d-135">FixMsgStream.cs</span></span>                                |                                                      <span data-ttu-id="1d31d-136">實作的包裝函式**System.IO.Stream**類別，啟用資料流處理的資料。</span><span class="sxs-lookup"><span data-stu-id="1d31d-136">Implements a wrapper for the **System.IO.Stream** class, enabling stream processing of data.</span></span>                                                      |
|                             <span data-ttu-id="1d31d-137">在 \FixMsg 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="1d31d-137">In the \FixMsg folder:</span></span><br /><br /> <span data-ttu-id="1d31d-138">FixMsgDescription.cs</span><span class="sxs-lookup"><span data-stu-id="1d31d-138">FixMsgDescription.cs</span></span>                             |                                                       <span data-ttu-id="1d31d-139">提供存取和轉譯管線設計師 」 中的元件 UI 資源的方法。</span><span class="sxs-lookup"><span data-stu-id="1d31d-139">Provides methods for accessing and rendering component UI resources in Pipeline Designer.</span></span>                                                        |
|                                 <span data-ttu-id="1d31d-140">在 \FixMsg 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="1d31d-140">In the \FixMsg folder:</span></span><br /><br /> <span data-ttu-id="1d31d-141">FixMsg.resx</span><span class="sxs-lookup"><span data-stu-id="1d31d-141">FixMsg.resx</span></span>                                  |                                                                      <span data-ttu-id="1d31d-142">包含屬性描述、圖示及錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1d31d-142">Contains property descriptions, an icon, and error messages.</span></span>                                                                      |
| <span data-ttu-id="1d31d-143">在 \PipelineComponentSample 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="1d31d-143">In the \PipelineComponentSample folder:</span></span><br /><br /> <span data-ttu-id="1d31d-144">PipelineComponentSample.btproj、PipelineComponentSample.sln</span><span class="sxs-lookup"><span data-stu-id="1d31d-144">PipelineComponentSample.btproj, PipelineComponentSample.sln</span></span> |                                                               <span data-ttu-id="1d31d-145">此範例之 BizTalk 專案部分的專案和方案檔案。</span><span class="sxs-lookup"><span data-stu-id="1d31d-145">Project and solution files for the BizTalk project portion of this sample.</span></span>                                                               |
|             <span data-ttu-id="1d31d-146">在 \PipelineComponentSample 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="1d31d-146">In the \PipelineComponentSample folder:</span></span><br /><br /> <span data-ttu-id="1d31d-147">PipelineComponentSampleBinding.xml</span><span class="sxs-lookup"><span data-stu-id="1d31d-147">PipelineComponentSampleBinding.xml</span></span>              |                                                                             <span data-ttu-id="1d31d-148">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="1d31d-148">Used for automated setup such as port binding.</span></span>                                                                             |
|      <span data-ttu-id="1d31d-149">在 \PipelineComponentSample 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="1d31d-149">In the \PipelineComponentSample folder:</span></span><br /><br /> <span data-ttu-id="1d31d-150">FixMsgReceivePipeline.btp、FixMsgSendPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="1d31d-150">FixMsgReceivePipeline.btp, FixMsgSendPipeline.btp</span></span>      |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1d31d-151"> 管線 (內含 FixMsg 自訂管線元件)，分別代表接收管線和傳送管線。</span><span class="sxs-lookup"><span data-stu-id="1d31d-151"> pipelines containing the FixMsg custom pipeline component, for the receive and the send pipelines, respectively.</span></span>   |

## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="1d31d-152">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="1d31d-152">Building and Initializing This Sample</span></span>  

#### <a name="to-build-and-initialize-the-customcomponent-sample"></a><span data-ttu-id="1d31d-153">若要建置和初始化此 CustomComponent 範例</span><span class="sxs-lookup"><span data-stu-id="1d31d-153">To build and initialize the CustomComponent sample</span></span>  

1. <span data-ttu-id="1d31d-154">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="1d31d-154">In a command window, navigate to the following folder:</span></span>  

    <span data-ttu-id="1d31d-155">\<*範例路徑*\>\Pipelines\CustomComponent</span><span class="sxs-lookup"><span data-stu-id="1d31d-155">\<*Samples Path*\>\Pipelines\CustomComponent</span></span>  

2. <span data-ttu-id="1d31d-156">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1d31d-156">Run the file Setup.bat, which performs the following actions:</span></span>  

   - <span data-ttu-id="1d31d-157">在此資料夾中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d31d-157">Creates the input (In) and output (Out) folders for this sample in the folder:</span></span>  

      <span data-ttu-id="1d31d-158">\<*範例路徑*\>\Pipelines\CustomComponent</span><span class="sxs-lookup"><span data-stu-id="1d31d-158">\<*Samples Path*\>\Pipelines\CustomComponent</span></span>  

   - <span data-ttu-id="1d31d-159">為這個範例編譯和部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="1d31d-159">Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  

   - <span data-ttu-id="1d31d-160">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="1d31d-160">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  

     > [!NOTE]
     >  <span data-ttu-id="1d31d-161">此範例會在建立和繫結連接埠時顯示下列警告：</span><span class="sxs-lookup"><span data-stu-id="1d31d-161">This sample displays the following warnings when creating and binding the ports:</span></span>  
     >   
     >  `Warning: Receive handler not specified for receive location "PCReceiveLocation"; updating with first receive handler with matching transport type.`  
     >   
     >  `Warning: Host not specified for orchestration "CustomComponent"; updating with first available host.`  
     >   
     >  <span data-ttu-id="1d31d-162">您可以安全地忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="1d31d-162">You can safely ignore these warnings.</span></span> <span data-ttu-id="1d31d-163">(繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。</span><span class="sxs-lookup"><span data-stu-id="1d31d-163">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  

   - <span data-ttu-id="1d31d-164">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="1d31d-164">Enables the receive location, and starts the send port.</span></span>  

> [!NOTE]
>  <span data-ttu-id="1d31d-165">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="1d31d-165">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="1d31d-166">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="1d31d-166">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="1d31d-167">這個金鑰組的用途是簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="1d31d-167">Use this key pair is used to sign the resulting assemblies.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="1d31d-168">若要復原 Setup.bat 所進行的變更，必須先從 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理] MMC 主控台停止並重新啟動主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d31d-168">To undo changes made by Setup.bat, you must first stop and restart the host instance from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration MMC console.</span></span> <span data-ttu-id="1d31d-169">接著，執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="1d31d-169">Next, run Cleanup.bat.</span></span> <span data-ttu-id="1d31d-170">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="1d31d-170">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  

## <a name="running-this-sample"></a><span data-ttu-id="1d31d-171">執行此範例</span><span class="sxs-lookup"><span data-stu-id="1d31d-171">Running This Sample</span></span>  

#### <a name="to-run-the-customcomponent-sample"></a><span data-ttu-id="1d31d-172">若要執行此 CustomComponent 範例</span><span class="sxs-lookup"><span data-stu-id="1d31d-172">To run the CustomComponent sample</span></span>  

1.  <span data-ttu-id="1d31d-173">請將文字檔 Input.txt 的複本貼到 In 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1d31d-173">Paste a copy of the text file Input.txt into the folder In.</span></span>  

2.  <span data-ttu-id="1d31d-174">請觀察建立於 Out 資料夾中的文字檔。這個檔案所包含的內容，就是開頭由接收管線插入和結尾由傳送管線插入其他文字之 Input.txt 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="1d31d-174">Observe the text file created in the folder Out. This file contains the contents of the file Input.txt with additional text inserted at the beginning (by the receive pipeline) and at the end (by the send pipeline).</span></span> <span data-ttu-id="1d31d-175">這個檔案的名稱的格式\< *MessageID*\>.xml，其中*\<MessageID\>* 會產生來唯一識別該訊息的 GUID.</span><span class="sxs-lookup"><span data-stu-id="1d31d-175">The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.</span></span>  

## <a name="comments"></a><span data-ttu-id="1d31d-176">註解</span><span class="sxs-lookup"><span data-stu-id="1d31d-176">Comments</span></span>  
 <span data-ttu-id="1d31d-177">您可以依照以下步驟執行，使用 [管線設計師] 來檢視事先設定的管線：</span><span class="sxs-lookup"><span data-stu-id="1d31d-177">You can view the preconfigured pipelines in Pipeline Designer by following these steps:</span></span>  

1.  <span data-ttu-id="1d31d-178">在 [方案總管] 中，按兩下 ReceivePipeline.btp，以便在 [管線設計師] 中開啟接收管線。</span><span class="sxs-lookup"><span data-stu-id="1d31d-178">In Solution Explorer, double-click ReceivePipeline.btp to open the receive pipeline in Pipeline Designer.</span></span> <span data-ttu-id="1d31d-179">觀察 FixMsg 元件會放置**驗證**接收管線階段。</span><span class="sxs-lookup"><span data-stu-id="1d31d-179">Observe that the FixMsg component is placed in the **Validate** stage of the receive pipeline.</span></span>  

2.  <span data-ttu-id="1d31d-180">按一下該 FixMsg 元件，在**驗證**設計介面上的階段。</span><span class="sxs-lookup"><span data-stu-id="1d31d-180">Click the FixMsg component in the **Validate** stage on the design surface.</span></span> <span data-ttu-id="1d31d-181">您可以在 [屬性] 視窗中，查看該管線元件的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="1d31d-181">In the Properties window, you can see the configuration properties of the pipeline component.</span></span> <span data-ttu-id="1d31d-182">觀察**PrependData**屬性設定為**到前面的資料接收管線字串**。</span><span class="sxs-lookup"><span data-stu-id="1d31d-182">Observe that the **PrependData** property is set to **Data to prepend in receive pipeline string**.</span></span>  

3.  <span data-ttu-id="1d31d-183">在 [方案總管] 中，按兩下 SendPipeline.btp，以便在 [管線設計師] 中開啟傳送管線。</span><span class="sxs-lookup"><span data-stu-id="1d31d-183">In Solution Explorer, double-click SendPipeline.btp to open the send pipeline in Pipeline Designer.</span></span> <span data-ttu-id="1d31d-184">觀察 FixMsg 元件會放置**Pre-assemble**傳送管線階段。</span><span class="sxs-lookup"><span data-stu-id="1d31d-184">Observe that the FixMsg component is placed in the **Pre-Assemble** stage of the send pipeline.</span></span>  

4.  <span data-ttu-id="1d31d-185">按一下該 FixMsg 元件，在**Pre-assemble**設計介面上的階段。</span><span class="sxs-lookup"><span data-stu-id="1d31d-185">Click the FixMsg component in **Pre-Assemble** stage on the design surface.</span></span> <span data-ttu-id="1d31d-186">請注意， **AppendData**屬性設定為**資料在傳送管線字串**。</span><span class="sxs-lookup"><span data-stu-id="1d31d-186">Note that the **AppendData** property is set to **Data to append in send pipeline string**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1d31d-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d31d-187">See Also</span></span>  
 [<span data-ttu-id="1d31d-188">管線 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="1d31d-188">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)