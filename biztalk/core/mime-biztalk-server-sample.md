---
title: MIME （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send pipelines, MIME/SMIME Encoder [pipeline component]
- examples, send pipelines
- MIME/SMIME Encoder [pipeline component], send pipelines
- MIME/SMIME Encoder [pipeline component], examples
- examples, MIME/SMIME Encoder [pipeline component]
ms.assetid: f76c720d-3798-4f15-a5f9-885ddf421d57
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec6e6e290761ba6d1be2ed08c8519e96c2846fa7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974068"
---
# <a name="mime-biztalk-server-sample"></a><span data-ttu-id="f555d-102">MIME （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="f555d-102">MIME (BizTalk Server Sample)</span></span>
<span data-ttu-id="f555d-103">MIME 範例會示範如何在傳送管線內執行 MIME 編碼。</span><span class="sxs-lookup"><span data-stu-id="f555d-103">The MIME sample demonstrates how to perform MIME encoding within a send pipeline.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="f555d-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="f555d-104">What This Sample Does</span></span>  
 <span data-ttu-id="f555d-105">此範例會將 MIMEIn 資料夾設定為接收位置。</span><span class="sxs-lookup"><span data-stu-id="f555d-105">This sample configures the folder MIMEIn as a receive location.</span></span> <span data-ttu-id="f555d-106">將檔案 (例如範例檔案 ImageInput.gif) 放置於此資料夾時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用下列步驟處理此檔案中的訊息：</span><span class="sxs-lookup"><span data-stu-id="f555d-106">When you place a file, such as the sample file ImageInput.gif, in this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the message in this file using the following steps:</span></span>  
  
1.  <span data-ttu-id="f555d-107">從接收位置資料夾 MIMEIn 擷取訊息檔案。</span><span class="sxs-lookup"><span data-stu-id="f555d-107">Retrieve the message file from the receive location folder MIMEIn.</span></span>  
  
2.  <span data-ttu-id="f555d-108">在接收管線中，將訊息維持不變傳遞通過。</span><span class="sxs-lookup"><span data-stu-id="f555d-108">In the receive pipeline, pass the message through unchanged.</span></span>  
  
3.  <span data-ttu-id="f555d-109">在 MessageBox 資料庫中，將訊息路由至傳送管線。</span><span class="sxs-lookup"><span data-stu-id="f555d-109">In the MessageBox database, route the message to the send pipeline.</span></span>  
  
4.  <span data-ttu-id="f555d-110">在傳送管線中，執行 MIME 編碼，並將檔案放到傳送配接器資料夾 MIMEOut 中。</span><span class="sxs-lookup"><span data-stu-id="f555d-110">In the send pipeline, perform MIME encoding and place the file into the send adapter folder MIMEOut.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="f555d-111">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="f555d-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="f555d-112">\<*範例路徑*\>\Pipelines\MIME\\</span><span class="sxs-lookup"><span data-stu-id="f555d-112">\<*Samples Path*\>\Pipelines\MIME\\</span></span>  
  
 <span data-ttu-id="f555d-113">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="f555d-113">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="f555d-114">檔案</span><span class="sxs-lookup"><span data-stu-id="f555d-114">File(s)</span></span>|<span data-ttu-id="f555d-115">Description</span><span class="sxs-lookup"><span data-stu-id="f555d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f555d-116">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="f555d-116">Cleanup.bat</span></span>|<span data-ttu-id="f555d-117">用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。</span><span class="sxs-lookup"><span data-stu-id="f555d-117">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="f555d-118">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="f555d-118">Removes send and receive ports.</span></span> <span data-ttu-id="f555d-119">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="f555d-119">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="f555d-120">ImageInput.GIF</span><span class="sxs-lookup"><span data-stu-id="f555d-120">ImageInput.GIF</span></span>|<span data-ttu-id="f555d-121">範例輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="f555d-121">Sample input file.</span></span>|  
|<span data-ttu-id="f555d-122">SampleMimeEncoding.btproj</span><span class="sxs-lookup"><span data-stu-id="f555d-122">SampleMimeEncoding.btproj</span></span><br /><br /> <span data-ttu-id="f555d-123">SampleMimeEncoding.sln</span><span class="sxs-lookup"><span data-stu-id="f555d-123">SampleMimeEncoding.sln</span></span>|<span data-ttu-id="f555d-124">這個範例的專案及解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="f555d-124">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="f555d-125">SampleMimeEncodingBinding.xml</span><span class="sxs-lookup"><span data-stu-id="f555d-125">SampleMimeEncodingBinding.xml</span></span>|<span data-ttu-id="f555d-126">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="f555d-126">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="f555d-127">SendMimePipeline.btp</span><span class="sxs-lookup"><span data-stu-id="f555d-127">SendMimePipeline.btp</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f555d-128"> 會以 MIME 編碼器元件來傳送管線檔案。</span><span class="sxs-lookup"><span data-stu-id="f555d-128"> send pipeline file with the MIME Encoder component.</span></span>|  
|<span data-ttu-id="f555d-129">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="f555d-129">Setup.bat</span></span>|<span data-ttu-id="f555d-130">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="f555d-130">Used to build and initialize this sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="f555d-131">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="f555d-131">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="f555d-132">請使用下列程序，建置和初始化 MIME 範例。</span><span class="sxs-lookup"><span data-stu-id="f555d-132">Use the following procedure to build and initialize the MIME sample.</span></span>  
  
#### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="f555d-133">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="f555d-133">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="f555d-134">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="f555d-134">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="f555d-135">\<*範例路徑*\>\Pipelines\MIME</span><span class="sxs-lookup"><span data-stu-id="f555d-135">\<*Samples Path*\>\Pipelines\MIME</span></span>  
  
2.  <span data-ttu-id="f555d-136">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f555d-136">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="f555d-137">在此資料夾中建立此範例的輸入 (MIMEIn) 和輸出 (MIMEOut) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f555d-137">Creates the input (MIMEIn) and output (MIMEOut) folders for this sample in the folder:</span></span>  
  
         <span data-ttu-id="f555d-138">\<*範例路徑*\>\Pipelines\MIME</span><span class="sxs-lookup"><span data-stu-id="f555d-138">\<*Samples Path*\>\Pipelines\MIME</span></span>  
  
    -   <span data-ttu-id="f555d-139">為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f555d-139">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.</span></span>  
  
    -   <span data-ttu-id="f555d-140">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="f555d-140">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f555d-141">此範例會在建立和繫結連接埠時顯示警告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f555d-141">This sample displays the following warning when creating and binding the ports:</span></span>  
  
        > [!NOTE]
        >  `Warning: Receive handler not specified for receive location "MIMEReceiveLocation"; updating with first receive handler with matching transport type.`  
  
        > [!NOTE]
        >  <span data-ttu-id="f555d-142">您可以安全地忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="f555d-142">You can safely ignore these warnings.</span></span> <span data-ttu-id="f555d-143">(繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。</span><span class="sxs-lookup"><span data-stu-id="f555d-143">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  
  
    -   <span data-ttu-id="f555d-144">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f555d-144">Enables the receive location, and starts the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f555d-145">如果您從安裝位置以外的位置執行這個範例中，您必須先新增參考**Microsoft.BizTalk.Pipeline.Components**組件。</span><span class="sxs-lookup"><span data-stu-id="f555d-145">If you run this sample from a location other than where it is installed, you must first add a reference to the **Microsoft.BizTalk.Pipeline.Components** assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f555d-146">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="f555d-146">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f555d-147">如果您在此範例中選擇開啟並建置專案，而不執行檔案 Setup.bat，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="f555d-147">If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="f555d-148">請使用這個金鑰組來簽署產生的組件。</span><span class="sxs-lookup"><span data-stu-id="f555d-148">Use this key pair to sign the resulting assembly.</span></span> <span data-ttu-id="f555d-149">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="f555d-149">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="f555d-150">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="f555d-150">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="f555d-151">執行此範例</span><span class="sxs-lookup"><span data-stu-id="f555d-151">Running This Sample</span></span>  
 <span data-ttu-id="f555d-152">請使用下列程序來執行 MIME 範例。</span><span class="sxs-lookup"><span data-stu-id="f555d-152">Use the following procedure to run the MIME sample.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="f555d-153">執行此範例</span><span class="sxs-lookup"><span data-stu-id="f555d-153">To run this sample</span></span>  
  
1.  <span data-ttu-id="f555d-154">將檔案 ImageInput.gif 的複本放到 MIMEIn 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f555d-154">Put a copy of the file ImageInput.gif into the folder MIMEIn.</span></span>  
  
2.  <span data-ttu-id="f555d-155">請注意在 MIMEOut 資料夾中建立的文字檔。</span><span class="sxs-lookup"><span data-stu-id="f555d-155">Observe the text file created in the folder MIMEOut.</span></span> <span data-ttu-id="f555d-156">這個文字檔的名稱是以訊息識別碼 GUID 為根據。</span><span class="sxs-lookup"><span data-stu-id="f555d-156">The name of this text file is based on the message ID GUID.</span></span> <span data-ttu-id="f555d-157">這個檔案包含輸入檔 ImageInput.gif 的 MIME 編碼內容。</span><span class="sxs-lookup"><span data-stu-id="f555d-157">This file contains MIME-encoded content of the input file ImageInput.gif.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f555d-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="f555d-158">See Also</span></span>  
 [<span data-ttu-id="f555d-159">管線 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="f555d-159">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)