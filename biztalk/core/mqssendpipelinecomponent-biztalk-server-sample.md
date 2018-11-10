---
title: MQSSendPipelineComponent （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- pipelines, examples
- MQSeries adapters, examples
- examples, pipelines
ms.assetid: ac709e45-524b-45ab-9673-060790ecbed2
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3416b4a1ba58a1262e9ff27e3558a2532c839cd4
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752340"
---
# <a name="mqssendpipelinecomponent-biztalk-server-sample"></a><span data-ttu-id="f5f94-102">MQSSendPipelineComponent (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="f5f94-102">MQSSendPipelineComponent (BizTalk Server Sample)</span></span>
<span data-ttu-id="f5f94-103">本範例示範如何撰寫可從 XML 檔案讀取一組 MQSeries 屬性值，並將這些屬性值套用至訊息的管線元件。</span><span class="sxs-lookup"><span data-stu-id="f5f94-103">This sample demonstrates how to write a pipeline component that reads a set of MQSeries property values from an XML file and applies them to a message.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="f5f94-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="f5f94-104">What This Sample Does</span></span>  
 <span data-ttu-id="f5f94-105">本範例由兩個 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案組成，分別是一個管線元件專案以及一個可利用該管線元件的管線專案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-105">This sample is composed of two [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects, a pipeline component project and a pipeline project that makes use of the pipeline component.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="f5f94-106">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="f5f94-106">Where to Find This Sample</span></span>  
  
- <span data-ttu-id="f5f94-107">*\<SamplesPath\>* \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyComponent</span><span class="sxs-lookup"><span data-stu-id="f5f94-107">*\<SamplesPath\>* \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyComponent</span></span>  
  
- <span data-ttu-id="f5f94-108">*\<SamplesPath\>* \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyPipeline</span><span class="sxs-lookup"><span data-stu-id="f5f94-108">*\<SamplesPath\>* \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyPipeline</span></span>  
  
  <span data-ttu-id="f5f94-109">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="f5f94-109">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|                                                                              <span data-ttu-id="f5f94-110">**檔案**</span><span class="sxs-lookup"><span data-stu-id="f5f94-110">**File**</span></span>                                                                               |                                         <span data-ttu-id="f5f94-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="f5f94-111">**Description**</span></span>                                          |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f5f94-112">SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln,</span><span class="sxs-lookup"><span data-stu-id="f5f94-112">SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln,</span></span><br /><br /> <span data-ttu-id="f5f94-113">SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.csproj</span><span class="sxs-lookup"><span data-stu-id="f5f94-113">SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.csproj</span></span> |                    <span data-ttu-id="f5f94-114">管線元件的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="f5f94-114">The project and solution files for the pipeline component.</span></span>                    |
|                                              <span data-ttu-id="f5f94-115">SetMQSeriesHeaderPropertyComponent\CSetMQSeriesHeaderPropertyComponent.cs</span><span class="sxs-lookup"><span data-stu-id="f5f94-115">SetMQSeriesHeaderPropertyComponent\CSetMQSeriesHeaderPropertyComponent.cs</span></span>                                              |                      <span data-ttu-id="f5f94-116">管線元件的 Visual C#® 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="f5f94-116">The Visual C#® source file for the pipeline component.</span></span>                      |
|                                                      <span data-ttu-id="f5f94-117">SetMQSeriesHeaderPropertyComponent\SetMQSMQMDHdrProps.xml</span><span class="sxs-lookup"><span data-stu-id="f5f94-117">SetMQSeriesHeaderPropertyComponent\SetMQSMQMDHdrProps.xml</span></span>                                                      |                 <span data-ttu-id="f5f94-118">管線元件讀取及使用的 MQSeries 屬性。</span><span class="sxs-lookup"><span data-stu-id="f5f94-118">The MQSeries properties read and used by the pipeline component.</span></span>                 |
|   <span data-ttu-id="f5f94-119">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btproj,</span><span class="sxs-lookup"><span data-stu-id="f5f94-119">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btproj,</span></span><br /><br /> <span data-ttu-id="f5f94-120">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln</span><span class="sxs-lookup"><span data-stu-id="f5f94-120">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln</span></span>   |                     <span data-ttu-id="f5f94-121">BizTalk 管線的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="f5f94-121">The project and solution files for the BizTalk pipeline.</span></span>                     |
|                                               <span data-ttu-id="f5f94-122">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.snk</span><span class="sxs-lookup"><span data-stu-id="f5f94-122">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.snk</span></span>                                               |                   <span data-ttu-id="f5f94-123">BizTalk 管線元件的強式命名金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-123">The strong naming key file for the BizTalk pipeline project.</span></span>                   |
|                                               <span data-ttu-id="f5f94-124">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="f5f94-124">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btp</span></span>                                               | <span data-ttu-id="f5f94-125">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線。</span><span class="sxs-lookup"><span data-stu-id="f5f94-125">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline.</span></span> |
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="f5f94-126">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="f5f94-126">How to Use This Sample</span></span>  
 <span data-ttu-id="f5f94-127">若要建立此應用程式，您必須完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f5f94-127">To create the application, you must complete the following steps:</span></span>  
  
1. <span data-ttu-id="f5f94-128">建立應用程式的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5f94-128">Create the folders for the application.</span></span>  
  
2. <span data-ttu-id="f5f94-129">修改及編譯管線元件的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-129">Modify and compile the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the pipeline component.</span></span>  
  
3. <span data-ttu-id="f5f94-130">將編譯後的組件和標頭檔複製到適當的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5f94-130">Copy the compiled assembly and the header file to the appropriate folders.</span></span>  
  
4. <span data-ttu-id="f5f94-131">修改 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 管線的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-131">Modify the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline.</span></span>  
  
5. <span data-ttu-id="f5f94-132">編譯及部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線專案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-132">Compile and deploy the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline project.</span></span>  
  
6. <span data-ttu-id="f5f94-133">設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置。</span><span class="sxs-lookup"><span data-stu-id="f5f94-133">Set up a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location.</span></span>  
  
7. <span data-ttu-id="f5f94-134">建立 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="f5f94-134">Create a MQSeries queue.</span></span>  
  
8. <span data-ttu-id="f5f94-135">設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f5f94-135">Set up a send port.</span></span>  
  
9. <span data-ttu-id="f5f94-136">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f5f94-136">Enable the receive location and start the send port.</span></span>  
  
## <a name="creating-the-folders-for-the-application"></a><span data-ttu-id="f5f94-137">為應用程式建立資料夾</span><span class="sxs-lookup"><span data-stu-id="f5f94-137">Creating the Folders for the Application</span></span>  
 <span data-ttu-id="f5f94-138">這個程序會為應用程式建立適當的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5f94-138">This procedure creates the appropriate folders for the application.</span></span>  
  
#### <a name="to-create-the-folders-for-the-application"></a><span data-ttu-id="f5f94-139">若要為應用程式建立資料夾</span><span class="sxs-lookup"><span data-stu-id="f5f94-139">To create the folders for the application</span></span>  
  
1.  <span data-ttu-id="f5f94-140">建立名為的資料夾**temp**在 C:\ 磁碟機不存在時。</span><span class="sxs-lookup"><span data-stu-id="f5f94-140">Create a folder named **temp** on your C:\ drive if it does not already exist.</span></span>  
  
2.  <span data-ttu-id="f5f94-141">下建立資料夾**C:\temp**名為目錄**Pickup3**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-141">Create a folder under the **C:\temp** directory named **Pickup3**.</span></span>  
  
## <a name="modifying-and-compiling-the-project-for-the-pipeline-component"></a><span data-ttu-id="f5f94-142">修改及編譯管線元件的專案</span><span class="sxs-lookup"><span data-stu-id="f5f94-142">Modifying and Compiling the Project for the Pipeline Component</span></span>  
 <span data-ttu-id="f5f94-143">這個程序會修改及編譯管線元件的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-143">This procedure modifies and compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the pipeline component.</span></span>  
  
#### <a name="to-modify-and-compile-the-project-for-the-pipeline-component"></a><span data-ttu-id="f5f94-144">若要修改及編譯管線元件的專案</span><span class="sxs-lookup"><span data-stu-id="f5f94-144">To modify and compile the project for the pipeline component</span></span>  
  
1. <span data-ttu-id="f5f94-145">按兩下方案檔 **[setmqseriesheaderpropertycomponent\setmqseriesheaderpropertycomponent.sln]** 來開啟的方案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f5f94-145">Double-click the solution file, **SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln** to open the solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2. <span data-ttu-id="f5f94-146">按兩下類別檔 **[csetmqseriesheaderpropertycomponent.cs]** 以開啟中的類別檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f5f94-146">Double-click the class file **CSetMQSeriesHeaderPropertyComponent.cs** to open the class file in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
3. <span data-ttu-id="f5f94-147">找出變數**samplesDir**，確認這個變數設為位置**C:\temp**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-147">Locate the variable **samplesDir**, verify that this variable is set to the location **C:\temp**.</span></span>  
  
4. <span data-ttu-id="f5f94-148">以滑鼠右鍵按一下 方案總管 中的方案，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-148">Right-click the solution in the Solution Explorer and click **Build**.</span></span> <span data-ttu-id="f5f94-149">這會將專案編譯成 dll，位於**SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent\bin\Debug\\** 目錄。</span><span class="sxs-lookup"><span data-stu-id="f5f94-149">This will compile the project into a dll located in the **SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent\bin\Debug\\** directory.</span></span>  
  
## <a name="copying-the-assembly-and-header-file-to-appropriate-folders"></a><span data-ttu-id="f5f94-150">將組件和標頭檔複製到適當的資料夾</span><span class="sxs-lookup"><span data-stu-id="f5f94-150">Copying the Assembly and Header File to Appropriate Folders</span></span>  
 <span data-ttu-id="f5f94-151">這個程序會將編譯後的組件和標頭檔複製到適當的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5f94-151">This procedure copies the compiled assembly and the header file to the appropriate folders.</span></span>  
  
#### <a name="to-copy-the-compiled-assembly-and-header-file-to-the-appropriate-folders"></a><span data-ttu-id="f5f94-152">若要將編譯後的組件和標頭檔複製到適當的資料夾</span><span class="sxs-lookup"><span data-stu-id="f5f94-152">To copy the compiled assembly and header file to the appropriate folders</span></span>  
  
1. <span data-ttu-id="f5f94-153">將已編譯的組件複製**SetMQSeriesHeaderPropertyComponent.dll** BizTalk 管線元件資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5f94-153">Copy the compiled assembly **SetMQSeriesHeaderPropertyComponent.dll** to the BizTalk pipeline components folder.</span></span> <span data-ttu-id="f5f94-154">BizTalk 管線元件資料夾的預設位置是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components。</span><span class="sxs-lookup"><span data-stu-id="f5f94-154">The default location for the BizTalk pipeline components folder is [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components.</span></span>  
  
2. <span data-ttu-id="f5f94-155">將 MQHeader 屬性檔複製**SetMQSMQMDHdrProps.xml**要**C:\temp**目錄。</span><span class="sxs-lookup"><span data-stu-id="f5f94-155">Copy the MQHeader properties file **SetMQSMQMDHdrProps.xml** to the **C:\temp** directory.</span></span>  
  
## <a name="modifying-the-project-for-the-biztalk-server-pipeline"></a><span data-ttu-id="f5f94-156">修改 BizTalk Server 管線的專案</span><span class="sxs-lookup"><span data-stu-id="f5f94-156">Modifying the Project for the BizTalk Server Pipeline</span></span>  
 <span data-ttu-id="f5f94-157">這個程序會修改 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 管線的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-157">This procedure modifies the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline.</span></span>  
  
#### <a name="to-modify-the-project-for-the-biztalk-server-pipeline"></a><span data-ttu-id="f5f94-158">若要修改 BizTalk Server 管線的專案</span><span class="sxs-lookup"><span data-stu-id="f5f94-158">To modify the project for the BizTalk Server pipeline</span></span>  
  
1. <span data-ttu-id="f5f94-159">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按兩下方案檔中，開啟方案 **[setmqseriesheaderpropertypipeline\setmqseriesheaderpropertypipeline.sln]**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-159">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution by double-clicking the solution file, **SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln**.</span></span>  
  
2. <span data-ttu-id="f5f94-160">為專案建立強式名稱金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-160">Create a strong name key file for the project.</span></span> <span data-ttu-id="f5f94-161">若要這樣做，請執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="f5f94-161">To do that, do the following:</span></span>  
  
   1. <span data-ttu-id="f5f94-162">開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f5f94-162">Open a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command prompt.</span></span>  
  
   2. <span data-ttu-id="f5f94-163">將目錄變更為\<範例路徑\>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent。</span><span class="sxs-lookup"><span data-stu-id="f5f94-163">Change directories to \<SamplesPath\>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent.</span></span>  
  
   3. <span data-ttu-id="f5f94-164">輸入以下內容：</span><span class="sxs-lookup"><span data-stu-id="f5f94-164">Type the following:</span></span>  
  
       `sn -k MQSSendPipelineComponent.snk`  
  
   4. <span data-ttu-id="f5f94-165">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f5f94-165">Press ENTER.</span></span> <span data-ttu-id="f5f94-166">金鑰檔隨即建立。</span><span class="sxs-lookup"><span data-stu-id="f5f94-166">This will create the key file.</span></span>  
  
3. <span data-ttu-id="f5f94-167">在 **方案總管**，以滑鼠右鍵按一下專案，然後按一下**屬性**專案期間 （在 中心 視窗中） 為啟動專案設計工具。</span><span class="sxs-lookup"><span data-stu-id="f5f94-167">In **Solution Explorer**, right-click the project and click **Properties** to launch Project Designer for the project (in the center window).</span></span>  
  
   1.  <span data-ttu-id="f5f94-168">在 [專案設計工具中，按一下**簽署**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5f94-168">In the Project Designer, click **Signing** tab.</span></span>  
  
   2.  <span data-ttu-id="f5f94-169">在右窗格中，選取**簽署組件**選項...</span><span class="sxs-lookup"><span data-stu-id="f5f94-169">In the right-hand pane, select the **Sign the assembly** option..</span></span>  
  
   3.  <span data-ttu-id="f5f94-170">按一下下拉式清單，如**選擇強式名稱金鑰檔**選項，然後按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-170">Click drop-down list for the **Choose a strong name key file** option, and click **Browse**.</span></span>  
  
   4.  <span data-ttu-id="f5f94-171">瀏覽至\<範例路徑\>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\MQSSendPipelineComponent.snk，按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-171">Browse to \<SamplesPath\>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\MQSSendPipelineComponent.snk, click **Open**.</span></span>  
  
4. <span data-ttu-id="f5f94-172">您稍早建立的管線元件已加入至**Pre-assemble**這個管線專案的階段。</span><span class="sxs-lookup"><span data-stu-id="f5f94-172">The pipeline component that you created earlier is already added to the **Pre-Assemble** stage of this pipeline project.</span></span> <span data-ttu-id="f5f94-173">如果這個元件尚未加入，您必須完成下列步驟將它加入：</span><span class="sxs-lookup"><span data-stu-id="f5f94-173">If this component was not already added you would need to complete the following steps to add it:</span></span>  
  
   1. <span data-ttu-id="f5f94-174">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE 中，按一下**工具箱**左邊的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f5f94-174">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE, click the **Toolbox** tab on the left side.</span></span>  
  
   2. <span data-ttu-id="f5f94-175">以滑鼠右鍵按一下**工具箱**，然後按一下**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-175">Right-click the **Toolbox**, and click **Choose Items**.</span></span>  
  
   3. <span data-ttu-id="f5f94-176">在 [**選擇工具箱項目**] 對話方塊中，按一下**BizTalk 管線元件**索引標籤上，選取**自訂元件以設定 MQseries 標頭屬性**元件，並然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-176">In the **Choose Toolbox Items** dialog box, click the **BizTalk Pipeline Components** tab, select the **Custom Component to Set MQseries header properties**component, and then click **OK**.</span></span>  
  
   4. <span data-ttu-id="f5f94-177">拖曳**自訂元件以設定 MQseries 標頭屬性**元件至**Pre-assemble**此管線的階段。</span><span class="sxs-lookup"><span data-stu-id="f5f94-177">Drag the **Custom Component to Set MQseries header properties**component to the **Pre-Assemble** stage of this pipeline.</span></span>  
  
## <a name="compiling-and-deploying-the-pipeline-project"></a><span data-ttu-id="f5f94-178">編譯及部署管線專案</span><span class="sxs-lookup"><span data-stu-id="f5f94-178">Compiling and Deploying the Pipeline Project</span></span>  
 <span data-ttu-id="f5f94-179">這個程序會編譯及部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線專案。</span><span class="sxs-lookup"><span data-stu-id="f5f94-179">This procedure compiles and deploys the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline project.</span></span>  
  
#### <a name="to-compile-and-deploy-the-pipeline-project"></a><span data-ttu-id="f5f94-180">若要編譯及部署管線專案</span><span class="sxs-lookup"><span data-stu-id="f5f94-180">To compile and deploy the pipeline project</span></span>  
  
1.  <span data-ttu-id="f5f94-181">在 [方案總管] 視窗中，以滑鼠右鍵按一下方案，然後**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-181">In the Solution Explorer window, right-click the solution, and then click **Deploy Solution**.</span></span> <span data-ttu-id="f5f94-182">這樣會建置解決方案並將組件部署至 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5f94-182">This builds the solution and deploys the assembly to the BizTalk Management database.</span></span>  
  
2.  <span data-ttu-id="f5f94-183">確認組件已部署至 BizTalk 管理資料庫：</span><span class="sxs-lookup"><span data-stu-id="f5f94-183">Verify the Assembly was deployed to the BizTalk Management database:</span></span>  
  
    1.  <span data-ttu-id="f5f94-184">開啟 [BizTalk 管理主控台]。</span><span class="sxs-lookup"><span data-stu-id="f5f94-184">Open the BizTalk Administration Console.</span></span>  
  
    2.  <span data-ttu-id="f5f94-185">按一下以展開**BizTalk 群組 [\<servername\>:\<管理資料庫\>]**，然後按一下以展開**組件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5f94-185">Click to expand **BizTalk Group [\<servername\>:\<management database\>]**, and then click to expand the **Assemblies** folder.</span></span>  
  
         <span data-ttu-id="f5f94-186">已部署的管線組件應該會顯示在**組件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5f94-186">The deployed pipeline assembly should be visible under the **Assemblies** folder.</span></span>  
  
## <a name="creating-the-receive-location"></a><span data-ttu-id="f5f94-187">建立接收位置</span><span class="sxs-lookup"><span data-stu-id="f5f94-187">Creating the Receive Location</span></span>  
 <span data-ttu-id="f5f94-188">這個程序會建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置。</span><span class="sxs-lookup"><span data-stu-id="f5f94-188">This procedure creates a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location.</span></span>  
  
#### <a name="to-create-the-receive-location"></a><span data-ttu-id="f5f94-189">若要建立接收位置</span><span class="sxs-lookup"><span data-stu-id="f5f94-189">To create the receive location</span></span>  
  
1.  <span data-ttu-id="f5f94-190">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-190">In the BizTalk Server Administration Console, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="f5f94-191">在 **單向接收埠屬性**對話方塊中，於**名稱**方塊中輸入"MQReply"，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-191">In the **One-way Receive Port Properties** dialog box, in the **Name** box type "MQReply" and click **OK**.</span></span>  
  
3.  <span data-ttu-id="f5f94-192">在左窗格中，按一下**接收位置**索引標籤，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-192">In the left pane, click **Receive Locations** tab, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="f5f94-193">在 **接收位置屬性**對話方塊中，於**名稱**欄位中，輸入"ReceiveFile"。</span><span class="sxs-lookup"><span data-stu-id="f5f94-193">In the **Receive Location Properties** dialog box, in the **Name** field, type "ReceiveFile".</span></span>  
  
5.  <span data-ttu-id="f5f94-194">在 **傳輸類型**方塊中，選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-194">In the **Transport Type** box, select **FILE**.</span></span>  
  
6.  <span data-ttu-id="f5f94-195">在 **接收處理常式**欄位中，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-195">In the **Receive Handler** field, select **BizTalkServerApplication**.</span></span>  
  
7.  <span data-ttu-id="f5f94-196">在 **接收管線**欄位中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-196">In the **Receive pipeline** field, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
8.  <span data-ttu-id="f5f94-197">在 **接收資料夾**欄位中，輸入"C:\temp\Pickup3"。</span><span class="sxs-lookup"><span data-stu-id="f5f94-197">In the **Receive folder** field, type "C:\temp\Pickup3".</span></span>  
  
9. <span data-ttu-id="f5f94-198">在 **檔案遮罩**欄位中，輸入 「\*。\*"。</span><span class="sxs-lookup"><span data-stu-id="f5f94-198">In the **File mask** field, type "\*.\*".</span></span>  
  
10. <span data-ttu-id="f5f94-199">按一下  **確定**，然後按一下**確定**  以結束**接收位置屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f5f94-199">Click **OK**, and then click **OK** again to exit the **Receive Location Properties** dialog box.</span></span>  
  
## <a name="creating-a-mqseries-queue-through-the-mqseries-explorer"></a><span data-ttu-id="f5f94-200">透過 MQSeries Explorer 建立 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="f5f94-200">Creating a MQSeries Queue Through the MQSeries Explorer</span></span>  
 <span data-ttu-id="f5f94-201">如果您有 MQSeries Server for Windows 安裝的必要權限，則可以透過配接器對話方塊建立 MQSeries 佇列並略過下一個程序。</span><span class="sxs-lookup"><span data-stu-id="f5f94-201">If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip this next procedure.</span></span>  
  
 <span data-ttu-id="f5f94-202">如果您沒有這類存取權限，可以依照下列程序使用 IBM WebSphere MQ Explorer 來建立佇列。</span><span class="sxs-lookup"><span data-stu-id="f5f94-202">If you do not have such access, you can use the following procedure to create the queue using the IBM WebSphere MQ Explorer.</span></span>  
  
#### <a name="to-create-a-mqseries-queue-through-the-mqseries-explorer"></a><span data-ttu-id="f5f94-203">若要透過 MQSeries Explorer 建立 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="f5f94-203">To create a MQSeries queue through the MQSeries Explorer</span></span>  
  
1.  <span data-ttu-id="f5f94-204">按一下 **開始**，指向**程式**，指向**IBM WebSphere MQ**，然後按一下**WebSphere MQ Explorer**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-204">Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="f5f94-205">按兩下**佇列管理員**，然後按兩下預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="f5f94-205">Double-click **Queue Managers**, and then double-click the default queue manager.</span></span> <span data-ttu-id="f5f94-206">預設佇列管理員通常會命名為**Qm_&lt**\<*machine_name* \>其中*machine_name*是您電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5f94-206">The default queue manager is typically named **QM_**\<*machine_name*\> where *machine_name* is the name of your computer.</span></span>  
  
3.  <span data-ttu-id="f5f94-207">以滑鼠右鍵按一下**佇列**，指向**新增**，然後按一下**本機佇列**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-207">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4.  <span data-ttu-id="f5f94-208">中**建立本機佇列**對話方塊中，於**佇列名稱**，型別**SETHEADER**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-208">In **Create Local Queue** dialog box, in **Queue Name**, type **SETHEADER**, and then click **OK**.</span></span>  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a><span data-ttu-id="f5f94-209">建立傳送埠和 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="f5f94-209">Creating the Send Port and MQSeries Queue</span></span>  
 <span data-ttu-id="f5f94-210">這個程序會建立輸出訊息所使用的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f5f94-210">This procedure creates the send port for the output message.</span></span> <span data-ttu-id="f5f94-211">如果您還沒有建立 MQSeries 佇列，在建立傳送埠時，也會建立 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="f5f94-211">The MQSeries queue is also created when you create the send port if you have not already created it.</span></span>  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a><span data-ttu-id="f5f94-212">若要建立傳送埠和 MQSeries 佇列</span><span class="sxs-lookup"><span data-stu-id="f5f94-212">To create the send port and MQSeries queue</span></span>  
  
1.  <span data-ttu-id="f5f94-213">以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-213">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="f5f94-214">在 **傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入"MQSolicitResponse"。</span><span class="sxs-lookup"><span data-stu-id="f5f94-214">In the **Send Port Properties** dialog box, in the **Name** box, type "MQSolicitResponse".</span></span>  
  
3.  <span data-ttu-id="f5f94-215">在 **傳輸類型**方塊中，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-215">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
4.  <span data-ttu-id="f5f94-216">在 **傳送管線**方塊中，選取**setmqseriesheaderpropertypipeline.setmqseriesheaderssendpipeline**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-216">In the **Send pipeline** box, select **SetMQSeriesHeaderPropertyPipeline.SetMQSeriesHeadersSendPipeline**.</span></span>  
  
5.  <span data-ttu-id="f5f94-217">在 **篩選**，具有下列名稱/值組加入新項目：</span><span class="sxs-lookup"><span data-stu-id="f5f94-217">In **Filters**, add a new entry with the following name/value pairs:</span></span>  
  
    -   <span data-ttu-id="f5f94-218">設定**屬性**來 「 BTS。ReceivePortName"。</span><span class="sxs-lookup"><span data-stu-id="f5f94-218">Set **Property** to "BTS.ReceivePortName".</span></span>  
  
    -   <span data-ttu-id="f5f94-219">設定**運算子**以 「 = = 」。</span><span class="sxs-lookup"><span data-stu-id="f5f94-219">Set **Operator** to "==".</span></span>  
  
    -   <span data-ttu-id="f5f94-220">設定**值**為"ReceiveFile"。</span><span class="sxs-lookup"><span data-stu-id="f5f94-220">Set **Value** to "ReceiveFile".</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f5f94-221">這樣會將傳送埠設定為訂閱到達 ReceiveFile 接收埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="f5f94-221">This sets the send port to subscribe to messages that arrive on the ReceiveFile receive port.</span></span>  
  
6.  <span data-ttu-id="f5f94-222">按一下 **傳輸**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-222">Click **Transport**.</span></span>  
  
7.  <span data-ttu-id="f5f94-223">在 **位址 (URI)** 欄位中，按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f5f94-223">In the **Address (URI)** field, click the ellipsis (…) button.</span></span>  
  
8.  <span data-ttu-id="f5f94-224">在  **MQSeries 傳輸屬性**對話方塊中，於**佇列定義**欄位中，按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f5f94-224">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** field, click the ellipsis (…) button.</span></span>  
  
9. <span data-ttu-id="f5f94-225">在 **佇列定義**對話方塊中，於**伺服器名稱**欄位中，輸入您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="f5f94-225">In the **Queue Definition** dialog box, in the **Server Name** field, type your computer name.</span></span>  
  
10. <span data-ttu-id="f5f94-226">在 **佇列管理員**欄位中，選取預設佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="f5f94-226">In the **Queue Manager** field, select the default queue manager.</span></span>  
  
11. <span data-ttu-id="f5f94-227">在 [佇列] 欄位中，輸入"SETHEADER"，然後再按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-227">In the Queue field, type "SETHEADER", and then click **Export**.</span></span>  
  
12. <span data-ttu-id="f5f94-228">在 **匯出** 對話方塊中，按一下**Create Queue**，然後按一下  **確定**或**完成**直到結束所有對話方塊為止。</span><span class="sxs-lookup"><span data-stu-id="f5f94-228">In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog.</span></span>  
  
## <a name="enabling-the-receive-location-and-starting-the-send-port"></a><span data-ttu-id="f5f94-229">啟用接收位置及啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="f5f94-229">Enabling the Receive Location and Starting the Send Port</span></span>  
 <span data-ttu-id="f5f94-230">這個程序會啟用接收位置及啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f5f94-230">This procedure enables the receive location and start the send port.</span></span>  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="f5f94-231">啟用接收位置和啟動傳送埠</span><span class="sxs-lookup"><span data-stu-id="f5f94-231">To enable the receive location and start the send port</span></span>  
  
1.  <span data-ttu-id="f5f94-232">在 BizTalk Server 管理主控台中，按一下**接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-232">In the BizTalk Server Administration console, click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="f5f94-233">在 [詳細資料] 窗格中，以滑鼠右鍵按一下**MQIn**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-233">In the details pane, right-click the **MQIn** receive location and click **Enable**.</span></span>  
  
3.  <span data-ttu-id="f5f94-234">在 [詳細資料] 窗格中，以滑鼠右鍵按一下 **[setmqheader]** 傳送埠，然後按一下**開始**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-234">In the details pane, right-click the **SetMQHeader** send port and click **Start**.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="f5f94-235">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="f5f94-235">Testing the Application</span></span>  
 <span data-ttu-id="f5f94-236">這個程序會測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5f94-236">This procedure tests the application.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="f5f94-237">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="f5f94-237">To test the application</span></span>  
  
1.  <span data-ttu-id="f5f94-238">將檔案放**C:\Temp\Pickup3**資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5f94-238">Put a file into the **C:\Temp\Pickup3** folder.</span></span>  
  
2.  <span data-ttu-id="f5f94-239">啟動 WebSphere MQ Explorer，然後按兩下 [SETHEADER] 佇列，檢查 SETHEADER 佇列中的訊息。</span><span class="sxs-lookup"><span data-stu-id="f5f94-239">Launch the WebSphere MQ Explorer and double-click the SETHEADER queue to examine the message(s) in the SETHEADER queue.</span></span>  
  
     <span data-ttu-id="f5f94-240">若要查看 SETHEADER 佇列中訊息的所有內容屬性，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f5f94-240">To see all of the context properties for the messages in the SETHEADER queue, complete the following steps:</span></span>  
  
    1.  <span data-ttu-id="f5f94-241">按兩下**SETHEADER**佇列，以便顯示**訊息瀏覽器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f5f94-241">Double-click the **SETHEADER** queue to display the **Message Browser** dialog box.</span></span>  
  
    2.  <span data-ttu-id="f5f94-242">在 **訊息瀏覽器** 對話方塊中，按一下**資料行**以顯示**訊息的顯示/隱藏資料行** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f5f94-242">In the **Message Browser** dialog box, click **Columns** to display the **Show/Hide Columns for Messages** dialog box.</span></span>  
  
    3.  <span data-ttu-id="f5f94-243">底下**可用的資料行**，連按兩下 若要顯示在每個項目**訊息瀏覽器**對話方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f5f94-243">Under **Available Columns**, double-click each entry to make it visible in the **Message Browser** dialog box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f5f94-244">每個訊息的訊息內容屬性應該會顯示在**訊息瀏覽器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f5f94-244">The message context properties for each message should be visible in the **Message Browser** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f94-245">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5f94-245">See Also</span></span>  
 [<span data-ttu-id="f5f94-246">MQSeries 配接器範例</span><span class="sxs-lookup"><span data-stu-id="f5f94-246">MQSeries Adapter Samples</span></span>](../core/mqseries-adapter-samples.md)