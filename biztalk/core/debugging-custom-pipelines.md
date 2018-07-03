---
title: 偵錯自訂管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27e5445a-6415-4c52-a450-b74a71fc4aa2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f03391660e7f06892294a84ba2be3fdabbc4703
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012015"
---
# <a name="debugging-custom-pipelines"></a><span data-ttu-id="2cc2b-102">偵錯自訂管線</span><span class="sxs-lookup"><span data-stu-id="2cc2b-102">Debugging Custom Pipelines</span></span>
<span data-ttu-id="2cc2b-103">當自訂管線中發生訊息處理失敗時，您可以使用來源層級偵錯來識別和修正問題。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-103">When message processing fails in your custom pipeline, you can use source level debugging to identify and correct problems.</span></span> <span data-ttu-id="2cc2b-104">使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 偵錯工具可以執行來源層級偵錯，其方式是將此工具附加到 BTSNTSVC.exe (如果自訂管線已部署) 或 Pipeline.exe (如果使用獨立管線工具)。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-104">Source level debugging is done using the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] debugger by attaching to BTSNTSVC.exe (if the custom pipeline is deployed) or Pipeline.exe (if using the stand-alone pipeline tool).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="2cc2b-105">程序</span><span class="sxs-lookup"><span data-stu-id="2cc2b-105">Procedures</span></span>  
 <span data-ttu-id="2cc2b-106">您可以使用下列程序，偵錯自訂管線。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-106">Use the following procedures to debug custom pipelines.</span></span>  
  
### <a name="how-to-debug-a-deployed-pipeline"></a><span data-ttu-id="2cc2b-107">如何偵錯已部署的管線</span><span class="sxs-lookup"><span data-stu-id="2cc2b-107">How to Debug a Deployed Pipeline</span></span>  
 <span data-ttu-id="2cc2b-108">從 [群組中樞] 頁面中，與事件檢視器中追蹤查詢，提供有關訊息處理已部署的元件中失敗的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-108">Tracking queries from the Group Hub page, and the event viewers, provide useful information about message processing failures in deployed components.</span></span> <span data-ttu-id="2cc2b-109">這項資訊通常可用來縮小問題的來源。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-109">This information can often be used to narrow down the origin of a problem.</span></span> <span data-ttu-id="2cc2b-110">一旦斷定是自訂管線的關係，就可以使用來源層級偵錯找出任何有問題的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-110">Once a custom pipeline has been implicated, source level debugging can be used to identify any problematic code.</span></span>  
  
##### <a name="to-debug-a-deployed-custom-pipeline-using-visual-studio"></a><span data-ttu-id="2cc2b-111">若要偵錯使用 Visual Studio 部署自訂管線</span><span class="sxs-lookup"><span data-stu-id="2cc2b-111">To Debug a Deployed Custom Pipeline using Visual Studio</span></span>  
  
1. <span data-ttu-id="2cc2b-112">將自訂管線專案方案載入至 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-112">Load the custom pipeline project solution into [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2. <span data-ttu-id="2cc2b-113">變更您的方案的輸出路徑*\<安裝資料夾\>* \Pipeline Components。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-113">Change the output path for your solution to *\<Installation Folder\>* \Pipeline Components.</span></span> <span data-ttu-id="2cc2b-114">在 方案總管 中，以滑鼠右鍵按一下您的專案，按一下 建置 索引標籤，按一下，以變更輸出路徑**瀏覽** 按鈕，然後選取*\<安裝資料夾\>* \Pipeline components 目錄。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-114">In Solution Explorer, right-click your project, click the Build tab, and then change the Output Path by clicking the **Browse** button and selecting the *\<Installation Folder\>* \Pipeline Components directory.</span></span>  
  
3. <span data-ttu-id="2cc2b-115">內在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按一下 部署方案**建置** &#124; **部署**。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-115">From within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], deploy the solution by clicking **Build** &#124; **Deploy**.</span></span>  
  
4. <span data-ttu-id="2cc2b-116">重新啟動執行管線的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-116">Restart the host instance that runs the pipeline.</span></span> <span data-ttu-id="2cc2b-117">使用 BizTalk Server 管理主控台，瀏覽至執行管線的主控件執行個體，以滑鼠右鍵按一下主控件執行個體然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-117">Using the BizTalk Server Management console, navigate to the host instance that runs the pipeline, right-click the host instance then click **Restart**.</span></span>  
  
5. <span data-ttu-id="2cc2b-118">附加[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BTSNTSVC.exe 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-118">Attach the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] debugger to BTSNTSVC.exe.</span></span> <span data-ttu-id="2cc2b-119">做法是按一下**偵錯** &#124; **připojit k procesu**，按一下 所有的工作階段中的 顯示處理程序，然後按兩下 BTSNTSVC.exe。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-119">This can be done by clicking **Debug** &#124; **Attach to Process**, click Show processes in all sessions, and then double-click BTSNTSVC.exe.</span></span>  
  
6. <span data-ttu-id="2cc2b-120">設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-120">Set breakpoints.</span></span>  
  
7. <span data-ttu-id="2cc2b-121">將訊息拖放到適當的位置，以起始自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-121">Drop a message in the appropriate location to initiate the custom pipeline component.</span></span> <span data-ttu-id="2cc2b-122">處理應該會在您設定的中斷點上停下來。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-122">Processing should halt on the breakpoints you set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cc2b-123">如果程式碼擲回例外狀況，BizTalk Server 將會加以攔截，最終則擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-123">If your code throws an exception, BizTalk Server will catch it and ultimately suspend the message.</span></span> <span data-ttu-id="2cc2b-124">為了避免這種情況，您應該在最有可能發生的例外狀況上中斷。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-124">To avoid this behavior, you should break on first chance exceptions.</span></span>  
  
### <a name="how-to-debug-using-pipelineexe"></a><span data-ttu-id="2cc2b-125">如何使用 Pipeline.exe 進行偵錯</span><span class="sxs-lookup"><span data-stu-id="2cc2b-125">How to Debug Using Pipeline.exe</span></span>  
 <span data-ttu-id="2cc2b-126">您也可以測試使用 Pipeline.exe 的自訂管線。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-126">You can also test custom pipelines using Pipeline.exe.</span></span> <span data-ttu-id="2cc2b-127">這樣的好處是您不一定要部署到實際執行環境類似的狀況下執行管線。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-127">This has the advantage of not requiring you to deploy the pipeline at the expense of not running under conditions similar to production.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cc2b-128">如果自訂管線使用一般檔案組合器/解譯器，則 Pipeline.exe 將無法正確執行。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-128">If your custom pipeline uses the flat file assembler / disassembler, Pipeline.exe will not execute properly.</span></span> <span data-ttu-id="2cc2b-129">這是因為 Pipeline.exe 不會存取 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-129">This is because Pipeline.exe does not access the BizTalk database.</span></span> <span data-ttu-id="2cc2b-130">其中一個解決方案是移除組合器 / 解譯器元件和使用 FFDasm.exe 和 FFAsm.exe 個別進行測試。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-130">One solution is to remove the assembler / disassembler components and test them separately with FFDasm.exe and FFAsm.exe.</span></span> <span data-ttu-id="2cc2b-131">請參閱[管線工具](../core/pipeline-tools.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-131">See [Pipeline Tools](../core/pipeline-tools.md) for more information.</span></span>  
  
##### <a name="to-debug-a-custom-pipeline-using-pipelineexe-and-visual-studio"></a><span data-ttu-id="2cc2b-132">若要偵錯自訂管線使用 Pipeline.exe 和 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2cc2b-132">To Debug a Custom Pipeline using Pipeline.exe and Visual Studio</span></span>  
  
1. <span data-ttu-id="2cc2b-133">將自訂管線專案方案載入至 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-133">Load the custom pipeline project solution into [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2. <span data-ttu-id="2cc2b-134">變更您的方案的輸出路徑*\<安裝資料夾\>* \Pipeline Components。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-134">Change the output path for your solution to *\<Installation Folder\>* \Pipeline Components.</span></span> <span data-ttu-id="2cc2b-135">在 方案總管 中，以滑鼠右鍵按一下您的專案，按一下 建置 索引標籤，按一下，以變更輸出路徑**瀏覽** 按鈕，然後選取*\<安裝資料夾\>* \Pipeline components 目錄。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-135">In Solution Explorer, right-click your project, click the Build tab, and then change the Output Path by clicking the **Browse** button and selecting the *\<Installation Folder\>* \Pipeline Components directory.</span></span>  
  
3. <span data-ttu-id="2cc2b-136">變更方案的起始動作。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-136">Change the start action for your solution.</span></span> <span data-ttu-id="2cc2b-137">在 方案總管 中，以滑鼠右鍵按一下您的專案，按一下 偵錯 索引標籤，按一下 啟動外部程式，然後按一下  **...**</span><span class="sxs-lookup"><span data-stu-id="2cc2b-137">In Solution Explorer, right-click your project, click the Debug tab, click Start external program, then click **…**</span></span> <span data-ttu-id="2cc2b-138">瀏覽至*\<安裝資料夾\>* \SDK\Utilities\PipelineTools 並選擇 Pipeline.exe。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-138">and navigate to *\<Installation Folder\>* \SDK\Utilities\PipelineTools and choose Pipeline.exe.</span></span> <span data-ttu-id="2cc2b-139">啟動選項 之下，輸入適合您元件的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-139">Under Start Options, enter the command line arguments appropriate for your component.</span></span> <span data-ttu-id="2cc2b-140">如需 Pipeline.exe 的詳細資訊，請參閱[管線工具](../core/pipeline-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-140">For more information on Pipeline.exe, see [Pipeline Tools](../core/pipeline-tools.md).</span></span> <span data-ttu-id="2cc2b-141">指定管線和範例檔案的一般組態設定：</span><span class="sxs-lookup"><span data-stu-id="2cc2b-141">A typical configuration specifies the pipeline and a sample file:</span></span>  
  
   ```  
   <Path>\YourPipeline.btp -d <Path>\YourTestFile.txt -c  
   ```  
  
4. <span data-ttu-id="2cc2b-142">設定您的中斷點。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-142">Set your breakpoints.</span></span>  
  
5. <span data-ttu-id="2cc2b-143">按 F5 開始偵錯。</span><span class="sxs-lookup"><span data-stu-id="2cc2b-143">Press F5 to begin debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc2b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cc2b-144">See Also</span></span>  
 [<span data-ttu-id="2cc2b-145">管線工具</span><span class="sxs-lookup"><span data-stu-id="2cc2b-145">Pipeline Tools</span></span>](../core/pipeline-tools.md)