---
title: "在 BizTalk Server 中的 BAM 端對端範例 |Microsoft 文件"
description: "如何從使用 「 商務活動監控 BizTalk Server 中的多個元件的事件相互關聯案例"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81406038-7f3f-499f-a003-12423d92c44b
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21cf3bcfae53d3204a1b4de23c1476591be2b453
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-end-to-end-biztalk-server-sample"></a><span data-ttu-id="44e8e-103">BAM 端對端 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="44e8e-103">BAM End-to-End (BizTalk Server Sample)</span></span>
<span data-ttu-id="44e8e-104">端對端範例會示範如何使用 BAM 來使多個元件 (在此例中是三個協調流程和一個管線) 中的事件相互產生關聯。</span><span class="sxs-lookup"><span data-stu-id="44e8e-104">The End-to-End sample demonstrates how to correlate events from multiple components (in this case, three orchestrations and a pipeline) by using BAM.</span></span>  
  
 <span data-ttu-id="44e8e-105">BAM 會重新建構跨越管線元件和協調流程的商務活動。</span><span class="sxs-lookup"><span data-stu-id="44e8e-105">BAM reconstructs the business activity that spans the pipeline component and orchestrations.</span></span> <span data-ttu-id="44e8e-106">這適用於以最低層級，藉由呼叫**EventStream.EnableContinuation**從預期有更多活動事件的每個實作元件。</span><span class="sxs-lookup"><span data-stu-id="44e8e-106">At the lowest level, this works by calls to **EventStream.EnableContinuation** from each implementation component that expects more events for the activity.</span></span> <span data-ttu-id="44e8e-107">若要呼叫**EnableContinuation**是明確的而 Orchestration1 和 Orchestration2 中會藉由將 Continuation 資料夾加入至一個排程和 ContinuationID 資料夾的排程中的追蹤設定檔的呼叫它。</span><span class="sxs-lookup"><span data-stu-id="44e8e-107">The call to **EnableContinuation** is explicit, while calls in Orchestration1 and Orchestration2 are made by adding a Continuation folder to the Tracking profile in one schedule, and a ContinuationID folder to the schedule that follows it.</span></span>  
  
 <span data-ttu-id="44e8e-108">下圖說明範例中使用的工作流程。</span><span class="sxs-lookup"><span data-stu-id="44e8e-108">The following diagram illustrates the workflow used in the sample.</span></span>  
  
 ![](../core/media/ebiz-sdk-samples-bam-endtoendwkflw.gif "ebiz_sdk_samples_bam_endtoendwkflw")  

  
## <a name="what-this-sample-does"></a><span data-ttu-id="44e8e-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="44e8e-109">What This Sample Does</span></span>  
 <span data-ttu-id="44e8e-110">BAM 端對端範例會示範如何使用 BAM 蒐集一個管線愈多個協調流程的資訊，並更新單一活動。</span><span class="sxs-lookup"><span data-stu-id="44e8e-110">The BAM end-to-end sample shows how you can use BAM to gather information from a pipeline and multiple orchestrations and update a single activity.</span></span>  
  
## <a name="how-this-sample-was-designed-and-why"></a><span data-ttu-id="44e8e-111">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="44e8e-111">How This Sample Was Designed and Why</span></span>  
 <span data-ttu-id="44e8e-112">BAM 端對端範例是針對說明下列活動而設計：</span><span class="sxs-lookup"><span data-stu-id="44e8e-112">The BAM end-to-end sample was designed to illustrate the following activities:</span></span>  
  
-   <span data-ttu-id="44e8e-113">在管線內使用 BAM。</span><span class="sxs-lookup"><span data-stu-id="44e8e-113">Using BAM within a pipeline.</span></span>  
  
-   <span data-ttu-id="44e8e-114">使用追蹤設定檔編輯器 (TPE) 將活動項目對應到協調流程與訊息元素中的圖形。</span><span class="sxs-lookup"><span data-stu-id="44e8e-114">Using the Tracking Profile Editor (TPE) to map activity items to shapes in an orchestration and elements of a message.</span></span>  
  
-   <span data-ttu-id="44e8e-115">使用接續活動作用中時好解決方案的多個片段提供給活動。</span><span class="sxs-lookup"><span data-stu-id="44e8e-115">Using continuations to keep an activity active when multiple pieces of a solution contribute to the activity.</span></span>  
  

<span data-ttu-id="44e8e-116">範例的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="44e8e-116">The sample works as follows:</span></span>  
  
1.  <span data-ttu-id="44e8e-117">輸入的訊息會從*\<範例路徑 >*\BamEndToEnd\Input 資料夾。</span><span class="sxs-lookup"><span data-stu-id="44e8e-117">An input message is retrieved from the *\<Samples Path>*\BamEndToEnd\Input folder.</span></span>  
  
2.  <span data-ttu-id="44e8e-118">管線元件指派唯一的 DocumentID 給訊息，並使用 BAM API 來開始新的 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="44e8e-118">The pipeline component assigns a unique DocumentID to the message, and uses the BAM API to begin a new BAM activity.</span></span> <span data-ttu-id="44e8e-119">DocumentID 會附加當做輸入訊息的個別部分，供協調流程使用。</span><span class="sxs-lookup"><span data-stu-id="44e8e-119">The DocumentID is attached as a separate part of the input message to make it available to the orchestrations.</span></span>  
  
3.  <span data-ttu-id="44e8e-120">收到輸入訊息時，就會啟動 Orchestration1 服務。</span><span class="sxs-lookup"><span data-stu-id="44e8e-120">The service Orchestration1 is activated when the input message is received.</span></span>  
  
4.  <span data-ttu-id="44e8e-121">Orchestration1 修改輸入訊息，並將它當做參數傳遞給 Orchestration2。</span><span class="sxs-lookup"><span data-stu-id="44e8e-121">Orchestration1 modifies the input message and passes it as a parameter to Orchestration2.</span></span>  
  
5.  <span data-ttu-id="44e8e-122">Orchestration2 修改輸入的訊息，並將它傳送至 MessageBox 資料庫中，會啟動 Orchestration3。</span><span class="sxs-lookup"><span data-stu-id="44e8e-122">Orchestration2 modifies the input message and sends it to the MessageBox database, which activates Orchestration3.</span></span>  
  
6.  <span data-ttu-id="44e8e-123">Orchestration3 修改訊息，並將它寫入至資料夾*\<範例路徑 >*\BamEndToEnd\Output。</span><span class="sxs-lookup"><span data-stu-id="44e8e-123">Orchestration3 modifies the message and writes it to the folder *\<Samples Path>*\BamEndToEnd\Output.</span></span>  
  
7.  <span data-ttu-id="44e8e-124">每個協調流程更新中的 BAM 活動的活動項目。</span><span class="sxs-lookup"><span data-stu-id="44e8e-124">Each orchestration updates activity items in the BAM activity.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="44e8e-125">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="44e8e-125">Where to Find This Sample</span></span>  
 <span data-ttu-id="44e8e-126">您可以找到此範例位於*\<範例路徑 >*\BAM\BamEndToEnd。</span><span class="sxs-lookup"><span data-stu-id="44e8e-126">You can find this sample at *\<Samples Path>*\BAM\BamEndToEnd.</span></span>  
  
 <span data-ttu-id="44e8e-127">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="44e8e-127">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="44e8e-128">檔案</span><span class="sxs-lookup"><span data-stu-id="44e8e-128">File(s)</span></span>|<span data-ttu-id="44e8e-129">Description</span><span class="sxs-lookup"><span data-stu-id="44e8e-129">Description</span></span>|  
|----|---|  
|<span data-ttu-id="44e8e-130">BamEndToEnd.sln</span><span class="sxs-lookup"><span data-stu-id="44e8e-130">BamEndToEnd.sln</span></span>|<span data-ttu-id="44e8e-131">BAM 端對端範例方案。</span><span class="sxs-lookup"><span data-stu-id="44e8e-131">BAM End-to-End sample solution.</span></span>|  
|<span data-ttu-id="44e8e-132">BamEndToEnd.xls</span><span class="sxs-lookup"><span data-stu-id="44e8e-132">BamEndToEnd.xls</span></span>|<span data-ttu-id="44e8e-133">BAM 定義樣式表。</span><span class="sxs-lookup"><span data-stu-id="44e8e-133">BAM definition style sheet.</span></span>|  
|<span data-ttu-id="44e8e-134">BamEndToEnd.xml</span><span class="sxs-lookup"><span data-stu-id="44e8e-134">BamEndToEnd.xml</span></span>|<span data-ttu-id="44e8e-135">BAM 定義 XML。</span><span class="sxs-lookup"><span data-stu-id="44e8e-135">BAM definition XML.</span></span>|  
|<span data-ttu-id="44e8e-136">BAMEndToEndBinding.xml</span><span class="sxs-lookup"><span data-stu-id="44e8e-136">BAMEndToEndBinding.xml</span></span>|<span data-ttu-id="44e8e-137">BAM 繫結。</span><span class="sxs-lookup"><span data-stu-id="44e8e-137">BAM binding.</span></span>|  
|<span data-ttu-id="44e8e-138">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="44e8e-138">Cleanup.bat</span></span>|<span data-ttu-id="44e8e-139">用來解除部署範例的批次檔。</span><span class="sxs-lookup"><span data-stu-id="44e8e-139">Batch file to undeploy the sample.</span></span>|  
|<span data-ttu-id="44e8e-140">InputMessage.xml</span><span class="sxs-lookup"><span data-stu-id="44e8e-140">InputMessage.xml</span></span>|<span data-ttu-id="44e8e-141">輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="44e8e-141">Input message.</span></span>|  
|<span data-ttu-id="44e8e-142">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="44e8e-142">Setup.bat</span></span>|<span data-ttu-id="44e8e-143">用來編譯和部署範例的批次檔。</span><span class="sxs-lookup"><span data-stu-id="44e8e-143">Batch file to compile and deploy the sample.</span></span>|  
|<span data-ttu-id="44e8e-144">\Components\AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="44e8e-144">\Components\AssemblyInfo.cs</span></span>|<span data-ttu-id="44e8e-145">管線元件程式碼。</span><span class="sxs-lookup"><span data-stu-id="44e8e-145">Pipeline component code.</span></span>|  
|<span data-ttu-id="44e8e-146">\Components\BAMMessagePartPLComponent.cs</span><span class="sxs-lookup"><span data-stu-id="44e8e-146">\Components\BAMMessagePartPLComponent.cs</span></span>|<span data-ttu-id="44e8e-147">管線元件程式碼。</span><span class="sxs-lookup"><span data-stu-id="44e8e-147">Pipeline component code.</span></span>|  
|<span data-ttu-id="44e8e-148">\Components\Components.csproj</span><span class="sxs-lookup"><span data-stu-id="44e8e-148">\Components\Components.csproj</span></span>|<span data-ttu-id="44e8e-149">管線元件專案。</span><span class="sxs-lookup"><span data-stu-id="44e8e-149">Pipeline component project.</span></span>|  
|<span data-ttu-id="44e8e-150">\Messages\InputMessage01.xml</span><span class="sxs-lookup"><span data-stu-id="44e8e-150">\Messages\InputMessage01.xml</span></span><br /><br /> <span data-ttu-id="44e8e-151">...</span><span class="sxs-lookup"><span data-stu-id="44e8e-151">...</span></span><br /><br /> <span data-ttu-id="44e8e-152">\Messages\InputMessage10.xml</span><span class="sxs-lookup"><span data-stu-id="44e8e-152">\Messages\InputMessage10.xml</span></span>|<span data-ttu-id="44e8e-153">輸入訊息範例。</span><span class="sxs-lookup"><span data-stu-id="44e8e-153">Sample input messages.</span></span>|  
|<span data-ttu-id="44e8e-154">\Services\BAMInbound.btp</span><span class="sxs-lookup"><span data-stu-id="44e8e-154">\Services\BAMInbound.btp</span></span>|<span data-ttu-id="44e8e-155">輸入管線檔案。</span><span class="sxs-lookup"><span data-stu-id="44e8e-155">Inbound pipeline file.</span></span>|  
|<span data-ttu-id="44e8e-156">\Services\BAMPartSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="44e8e-156">\Services\BAMPartSchema.xsd</span></span>|<span data-ttu-id="44e8e-157">BAM 部分訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="44e8e-157">BAM part message schema.</span></span>|  
|<span data-ttu-id="44e8e-158">\Services\Orchestration1.odx</span><span class="sxs-lookup"><span data-stu-id="44e8e-158">\Services\Orchestration1.odx</span></span>|<span data-ttu-id="44e8e-159">協調流程。</span><span class="sxs-lookup"><span data-stu-id="44e8e-159">Orchestration.</span></span>|  
|<span data-ttu-id="44e8e-160">\Services\Orchestration2.odx</span><span class="sxs-lookup"><span data-stu-id="44e8e-160">\Services\Orchestration2.odx</span></span>|<span data-ttu-id="44e8e-161">協調流程。</span><span class="sxs-lookup"><span data-stu-id="44e8e-161">Orchestration.</span></span>|  
|<span data-ttu-id="44e8e-162">\Services\Orchestration3.odx</span><span class="sxs-lookup"><span data-stu-id="44e8e-162">\Services\Orchestration3.odx</span></span>|<span data-ttu-id="44e8e-163">協調流程。</span><span class="sxs-lookup"><span data-stu-id="44e8e-163">Orchestration.</span></span>|  
|<span data-ttu-id="44e8e-164">\Services\PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="44e8e-164">\Services\PropertySchema.xsd</span></span>|<span data-ttu-id="44e8e-165">屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="44e8e-165">Property schema.</span></span>|  
|<span data-ttu-id="44e8e-166">\Services\Schema1.xsd</span><span class="sxs-lookup"><span data-stu-id="44e8e-166">\Services\Schema1.xsd</span></span>|<span data-ttu-id="44e8e-167">訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="44e8e-167">Message schema.</span></span>|  
|<span data-ttu-id="44e8e-168">\Services\Schema2.xsd</span><span class="sxs-lookup"><span data-stu-id="44e8e-168">\Services\Schema2.xsd</span></span>|<span data-ttu-id="44e8e-169">訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="44e8e-169">Message schema.</span></span>|  
<span data-ttu-id="44e8e-170">Services\Schema3.xsd</span><span class="sxs-lookup"><span data-stu-id="44e8e-170">Services\Schema3.xsd</span></span>|<span data-ttu-id="44e8e-171">訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="44e8e-171">Message schema.</span></span>|  
|<span data-ttu-id="44e8e-172">\Services\Services.btproj</span><span class="sxs-lookup"><span data-stu-id="44e8e-172">\Services\Services.btproj</span></span>|[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="44e8e-173"> BizTalk 檔案專案。</span><span class="sxs-lookup"><span data-stu-id="44e8e-173"> BizTalk file project.</span></span>|  
|<span data-ttu-id="44e8e-174">\Services\Transform_1.btm</span><span class="sxs-lookup"><span data-stu-id="44e8e-174">\Services\Transform_1.btm</span></span>|<span data-ttu-id="44e8e-175">對應檔案。</span><span class="sxs-lookup"><span data-stu-id="44e8e-175">Map file.</span></span>|  
|<span data-ttu-id="44e8e-176">\Services\Transform_2.btm</span><span class="sxs-lookup"><span data-stu-id="44e8e-176">\Services\Transform_2.btm</span></span>|<span data-ttu-id="44e8e-177">對應檔案。</span><span class="sxs-lookup"><span data-stu-id="44e8e-177">Map file.</span></span>|  
|<span data-ttu-id="44e8e-178">\Services\Transform_3.btm</span><span class="sxs-lookup"><span data-stu-id="44e8e-178">\Services\Transform_3.btm</span></span>|<span data-ttu-id="44e8e-179">對應檔案。</span><span class="sxs-lookup"><span data-stu-id="44e8e-179">Map file.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="44e8e-180">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="44e8e-180">How to Use This Sample</span></span>  
 <span data-ttu-id="44e8e-181">若要建置並執行 BAM 端對端範例使用下列程序：</span><span class="sxs-lookup"><span data-stu-id="44e8e-181">Use the following procedures to build and run the BAM End-to-End sample:</span></span>  
  
-   [<span data-ttu-id="44e8e-182">若要建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="44e8e-182">To build and initialize this sample</span></span>](#To_Build_Sample)  
  
-   [<span data-ttu-id="44e8e-183">若要執行這個範例</span><span class="sxs-lookup"><span data-stu-id="44e8e-183">To run this sample</span></span>](#To_Run_Sample)  
  
-   [<span data-ttu-id="44e8e-184">若要檢視 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="44e8e-184">To view the BAM data</span></span>](#To_View_Data)  
  
##  <span data-ttu-id="44e8e-185"><a name="To_Build_Sample"></a>建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="44e8e-185"><a name="To_Build_Sample"></a>Build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="44e8e-186">開啟命令提示字元，以系統管理員身分，並執行*\<範例路徑 >*\BAM\BAMEndToEnd\Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="44e8e-186">Open a command prompt as Administrator, and run *\<Samples Path>*\BAM\BAMEndToEnd\Setup.bat.</span></span> <span data-ttu-id="44e8e-187">Setup.bat 隨即建置及初始化這個範例的 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="44e8e-187">Setup.bat builds and initializes the BAM infrastructure for this sample.</span></span> <span data-ttu-id="44e8e-188">保持開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="44e8e-188">Keep the command prompt open.</span></span>  
  
2.  <span data-ttu-id="44e8e-189">建立將 Orchestration1、 Orchestration2 和 Orchestration3 對應到 BAM 活動的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="44e8e-189">Create a tracking profile to map Orchestration1, Orchestration2, and Orchestration3 to the BAM activity.</span></span> <span data-ttu-id="44e8e-190">(詳細的指示建立追蹤設定檔是複雜的程序，因為位於個別的程序呼叫**建立追蹤設定檔**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-190">(Because creating the tracking profile is a complex process, the detailed instructions are in a separate procedure called **To create a tracking profile**.</span></span> <span data-ttu-id="44e8e-191">此程序會顯示在本文件稍後）。</span><span class="sxs-lookup"><span data-stu-id="44e8e-191">This procedure appears later in this document.)</span></span>  
  
3.  <span data-ttu-id="44e8e-192">部署您在上一個步驟中建立的 BamEndToEnd.btt 追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="44e8e-192">Deploy the tracking profile BamEndToEnd.btt that you created in the previous step.</span></span>  <span data-ttu-id="44e8e-193">在命令提示字元將變更為*\<範例路徑 >*\BAM\BamEndToEnd 目錄。</span><span class="sxs-lookup"><span data-stu-id="44e8e-193">In the command prompt change to the *\<Samples Path>*\BAM\BamEndToEnd directory.</span></span> <span data-ttu-id="44e8e-194">若要部署追蹤設定檔，輸入下列命令，並按一下**Enter**:</span><span class="sxs-lookup"><span data-stu-id="44e8e-194">To deploy the tracking profile, type the following line, and then press **Enter**:</span></span>  
  
    `“<BizTalkInstallationPath>\Tracking\bttdeploy” BamEndToEnd.btt`
  
     <span data-ttu-id="44e8e-195">[如何使用 「 追蹤設定檔管理公用程式部署追蹤設定檔](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md)提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="44e8e-195">[How to Deploy Tracking Profiles with the Tracking Profiles Management Utility](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md) provides more information.</span></span>
  
    > [!IMPORTANT]
    >  <span data-ttu-id="44e8e-196">您可以忽略訊息 ContinuationID Orch1_ 沒有相符的接續。</span><span class="sxs-lookup"><span data-stu-id="44e8e-196">You can ignore the message that the ContinuationID Orch1_ does not have a matching Continuation.</span></span> <span data-ttu-id="44e8e-197">預期這個訊息，因為在管線元件中，而不是在追蹤設定檔，會定義名為 Orch1_ 接續。</span><span class="sxs-lookup"><span data-stu-id="44e8e-197">This message is expected, because the continuation named Orch1_ is defined in the pipeline component, and not in the tracking profile.</span></span>  
  
##  <span data-ttu-id="44e8e-198"><a name="To_Run_Sample"></a>執行這個範例</span><span class="sxs-lookup"><span data-stu-id="44e8e-198"><a name="To_Run_Sample"></a>Run this sample</span></span>  
  
<span data-ttu-id="44e8e-199">將檔案複製*\<範例路徑 >*到資料夾 \BamEndToEnd\InputMessage.xml *\<範例路徑 >*\BamEndToEnd\Input。</span><span class="sxs-lookup"><span data-stu-id="44e8e-199">Copy the file *\<Samples Path>*\BamEndToEnd\InputMessage.xml into the folder *\<Samples Path>*\BamEndToEnd\Input.</span></span> <span data-ttu-id="44e8e-200">幾秒之後，訊息將會消失輸入資料夾中，並輸出訊息出現在*\<範例路徑 >*\BamEndToEnd\Output 資料夾。</span><span class="sxs-lookup"><span data-stu-id="44e8e-200">After a few seconds, the message disappears from the Input folder, and an output message appears in the *\<Samples Path>*\BamEndToEnd\Output folder.</span></span>  
  
##  <span data-ttu-id="44e8e-201"><a name="To_View_Data"></a>檢視 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="44e8e-201"><a name="To_View_Data"></a>View the BAM data</span></span>  
  
1.  <span data-ttu-id="44e8e-202">開啟 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="44e8e-202">Open SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="44e8e-203">在 SQL Server Management Studio，展開伺服器，展開 **資料庫**，依序展開**BAMPrimaryImport**，然後展開**資料表**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-203">In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="44e8e-204">以滑鼠右鍵按一下**dbo.bam_EndToEndActivity_Completed**，然後按一下 **開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-204">Right-click **dbo.bam_EndToEndActivity_Completed**, and then click **Open Table**.</span></span> <span data-ttu-id="44e8e-205">如果您使用[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，按一下 **選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-205">If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.</span></span>  
  
     <span data-ttu-id="44e8e-206">Bam_EndToEndActivity_Completed 資料表的內容會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-206">The contents of the bam_EndToEndActivity_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="44e8e-207">資料表中的每個資料列代表 [endtoendactivity] 活動已完成。</span><span class="sxs-lookup"><span data-stu-id="44e8e-207">Each row in the table represents an EndToEndActivity activity that has been completed.</span></span>  
  
#### <a name="rerun-this-sample"></a><span data-ttu-id="44e8e-208">重新執行此範例</span><span class="sxs-lookup"><span data-stu-id="44e8e-208">Rerun this sample</span></span>  
  
1.  <span data-ttu-id="44e8e-209">開啟命令提示字元，以系統管理員身分，並將變更*\<範例路徑 >*\BAM\BamEndToEnd 目錄。</span><span class="sxs-lookup"><span data-stu-id="44e8e-209">Open a command prompt as Administrator, and change to the *\<Samples Path>*\BAM\BamEndToEnd directory.</span></span> <span data-ttu-id="44e8e-210">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="44e8e-210">Type the following line:</span></span>  
  
    `“C:\Program Files\Microsoft BizTalk Server <version>\Tracking\bttdeploy” BamEndToEnd.btt /remove`  
  
    > [!NOTE]
    >  <span data-ttu-id="44e8e-211">如果您未安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]到 C 磁碟機中，您的安裝所在的磁碟機代號取代"C" [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="44e8e-211">If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the C drive, replace "C" with the drive letter where you installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="44e8e-212">執行*\<範例路徑 >*\BAM\BAMEndToEnd\Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="44e8e-212">Run *\<Samples Path>*\BAM\BAMEndToEnd\Cleanup.bat.</span></span> <span data-ttu-id="44e8e-213">Cleanup.bat 會移除此範例的 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="44e8e-213">Cleanup.bat removes the BAM infrastructure for this sample.</span></span>  
  
3.  <span data-ttu-id="44e8e-214">執行中的步驟**建置和初始化此範例**本主題中的區段。</span><span class="sxs-lookup"><span data-stu-id="44e8e-214">Perform the steps in **To build and initialize this sample** section in this topic.</span></span>  
  
##  <span data-ttu-id="44e8e-215"><a name="TPE_procedure"></a>建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="44e8e-215"><a name="TPE_procedure"></a>Create a tracking profile</span></span>  
  
1.  <span data-ttu-id="44e8e-216">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="44e8e-216">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)].</span></span> <span data-ttu-id="44e8e-217">以滑鼠右鍵按一下**追蹤設定檔編輯器**，和**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-217">Right-click **Tracking Profile Editor**, and **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="44e8e-218">在左窗格中**追蹤設定檔編輯器**視窗中，按一下 **按一下這裡匯入 BAM 活動定義**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-218">In the left pane of the **Tracking Profile Editor** window, click **Click here to import a BAM Activity Definition**.</span></span>  
  
3.  <span data-ttu-id="44e8e-219">在**BAM 活動定義名稱**區段**匯入 BAM 活動定義**對話方塊中，選取**endtoendactivity**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="44e8e-219">In the  **BAM Activity Definition Name** section of the **Import BAM Activity Definition** dialog box, select **EndToEndActivity**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="44e8e-220">在右窗格中**追蹤設定檔編輯器**視窗中，按一下 **按一下這裡選取事件來源**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-220">In the right pane of the **Tracking Profile Editor** window, click **Click here to select an event source**.</span></span>  
  
5.  <span data-ttu-id="44e8e-221">在**組件名稱**區段**選取的事件來源父組件**對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-221">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="44e8e-222">在**協調流程的名稱**區段**選取協調流程**對話方塊中，選取**BamEndToEnd.Services.Orchestration1**，然後按一下  **確定**.</span><span class="sxs-lookup"><span data-stu-id="44e8e-222">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamEndToEnd.Services.Orchestration1**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="44e8e-223">在左窗格中**追蹤設定檔編輯器**視窗中，以滑鼠右鍵按一下**endtoendactivity**，然後按一下 **新 ContinuationID**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-223">In the left pane of the **Tracking Profile Editor** window, right-click **EndToEndActivity**, and then click **New ContinuationID**.</span></span> <span data-ttu-id="44e8e-224">命名新接續識別碼**Orch1_**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-224">Name the new continuation ID **Orch1_**.</span></span> <span data-ttu-id="44e8e-225">重複此步驟，建立兩個的多個接續識別碼名為**Orch2_**和**Orch3_**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-225">Repeat this step to create two more continuation IDs named **Orch2_** and **Orch3_**.</span></span>  
  
8.  <span data-ttu-id="44e8e-226">以滑鼠右鍵按一下**endtoendactivity**，然後按一下 **新的接續**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-226">Right-click **EndToEndActivity**, and then click **New Continuation**.</span></span> <span data-ttu-id="44e8e-227">命名新的接續**Orch2_**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-227">Name the new continuation **Orch2_**.</span></span> <span data-ttu-id="44e8e-228">重複此步驟，建立名為另一個接續**Orch3_**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-228">Repeat this step to create another continuation named **Orch3_**.</span></span>  
  
9. <span data-ttu-id="44e8e-229">以滑鼠右鍵按一下**[receive1]**圖形，，然後按一下**內容屬性結構描述**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-229">Right-click the **Receive1** shape, and then click **Context Property Schemas**.</span></span>  
  
10. <span data-ttu-id="44e8e-230">捲動到結尾**內容屬性名稱**清單，，然後按兩下  **BAMEndToEnd.Services.PropertySchema.DocumentID**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-230">Scroll to the end of the **Context Property Name** list, and then double-click **BAMEndToEnd.Services.PropertySchema.DocumentID**.</span></span>  
  
11. <span data-ttu-id="44e8e-231">展開**\<結構描述 >**，然後將拖曳**DocumentID**右窗格中**Orch1_**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-231">Expand **\<Schema>**, and then drag **DocumentID** in the right pane to **Orch1_** in the left pane.</span></span>  
  
12. <span data-ttu-id="44e8e-232">按一下資料夾圖示的箭號 (![資料夾和向上箭號按鈕](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，以顯示協調流程。</span><span class="sxs-lookup"><span data-stu-id="44e8e-232">Click the folder icon with the arrow (![button with folder and up arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) twice to display the orchestration.</span></span>  
  
13. <span data-ttu-id="44e8e-233">拖曳**[receive1]**右窗格中的圖形**SBegin1**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-233">Drag the **Receive1** shape in the right pane to **SBegin1** in the left pane.</span></span>  
  
14. <span data-ttu-id="44e8e-234">拖曳**StartOrchestration_1**右窗格中的圖形**SEnd1**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-234">Drag the **StartOrchestration_1** shape in the right pane to **SEnd1** in the left pane.</span></span>  
  
15. <span data-ttu-id="44e8e-235">以滑鼠右鍵按一下**StartOrchestration_1**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-235">Right-click the **StartOrchestration_1** shape, and then click **Message Payload Schemas**.</span></span>  
  
16. <span data-ttu-id="44e8e-236">按兩下包含值"Message_2"的資料列中**訊息**資料行和值"MessageBody 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="44e8e-236">Double-click the row that contains the value “Message_2” in the **Message** column and the value “MessageBody” in the **Part** column.</span></span>  
  
     <span data-ttu-id="44e8e-237">![顯示訊息 & #95 的 TPE 訊息內容結構描述，則為 2](../core/media/77fbc444-46cf-4d45-8e9c-c330da7ba7d1.gif "77fbc444-46cf-4d45-8e9c-c330da7ba7d1")</span><span class="sxs-lookup"><span data-stu-id="44e8e-237">![TPE Message Payload schema showing message&#95;2](../core/media/77fbc444-46cf-4d45-8e9c-c330da7ba7d1.gif "77fbc444-46cf-4d45-8e9c-c330da7ba7d1")</span></span>  
  
17. <span data-ttu-id="44e8e-238">展開**Schema2**，然後將拖曳**Data2**右窗格中**Data1**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-238">Expand **Schema2**, and then drag **Data2** in the right pane to **Data1** in the left pane.</span></span>  
  
18. <span data-ttu-id="44e8e-239">按一下**選取事件來源**，然後按一下 **選取內容屬性**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-239">Click **Select Event Source**, and then click **Select Context Property**.</span></span>  
  
19. <span data-ttu-id="44e8e-240">捲動到結尾**內容屬性名稱**清單，，然後按兩下  **BAMEndToEnd.Services.PropertySchema.DocumentID**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-240">Scroll to the end of the **Context Property Name** list, and then double-click **BAMEndToEnd.Services.PropertySchema.DocumentID**.</span></span>  
  
20. <span data-ttu-id="44e8e-241">展開**\<結構描述 >**，然後將拖曳**DocumentID**至**Orch2_**的左窗格中的接續。</span><span class="sxs-lookup"><span data-stu-id="44e8e-241">Expand **\<Schema>**, and then drag **DocumentID** to the **Orch2_** continuation in the left pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44e8e-242">請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="44e8e-242">Do not confuse the Orch2_ continuation with the Orch2_ continuation ID.</span></span> <span data-ttu-id="44e8e-243">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="44e8e-243">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  
  
21. <span data-ttu-id="44e8e-244">按一下**選取事件來源**，然後按一下 **選取協調流程排程**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-244">Click **Select Event Source**, and then click **Select Orchestration Schedule**.</span></span>  
  
22. <span data-ttu-id="44e8e-245">在**組件名稱**區段**選取的事件來源父組件**對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-245">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, and then click **Next**.</span></span>  
  
23. <span data-ttu-id="44e8e-246">在**協調流程的名稱**區段**選取協調流程**對話方塊中，選取**BamEndToEnd.Services.Orchestration2**，然後按一下  **確定**.</span><span class="sxs-lookup"><span data-stu-id="44e8e-246">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamEndToEnd.Services.Orchestration2**, and then click **OK**.</span></span>  
  
24. <span data-ttu-id="44e8e-247">以滑鼠右鍵按一下**[constructmessage_1]**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-247">Right-click the **ConstructMessage_1** shape, and then click **Message Payload Schemas**.</span></span>  
  
25. <span data-ttu-id="44e8e-248">按兩下包含值"Message_3"的資料列中**訊息**資料行和值"BAMPart 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="44e8e-248">Double-click the row that contains the value “Message_3” in the **Message** column and the value “BAMPart” in the **Part** column.</span></span>  
  
26. <span data-ttu-id="44e8e-249">展開**BAMPart**，然後將拖曳**DocumentID**右窗格中**Orch2_**接續識別碼的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-249">Expand **BAMPart**, and then drag **DocumentID** in the right pane to the **Orch2_** continuation ID in the left pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44e8e-250">請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="44e8e-250">Do not confuse the Orch2_ continuation with the Orch2_ continuation ID.</span></span> <span data-ttu-id="44e8e-251">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="44e8e-251">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  
  
27. <span data-ttu-id="44e8e-252">按一下資料夾圖示的箭號 (![資料夾和向上按鈕 &#45; 箭號](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，以顯示協調流程。</span><span class="sxs-lookup"><span data-stu-id="44e8e-252">Click the folder icon with the arrow (![button with folder and up&#45;arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) twice to display the orchestration.</span></span>  
  
28. <span data-ttu-id="44e8e-253">拖曳**[constructmessage_1]**右窗格中的圖形**SBegin2**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-253">Drag the **ConstructMessage_1** shape in the right pane to **SBegin2** in the left pane.</span></span>  
  
29. <span data-ttu-id="44e8e-254">拖曳**[send_1]**右窗格中的圖形**SEnd2**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-254">Drag the **Send_1** shape in the right pane to **SEnd2** in the left pane.</span></span>  
  
30. <span data-ttu-id="44e8e-255">以滑鼠右鍵按一下**[send_1]**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-255">Right-click the **Send_1** shape, and then click **Message Payload Schemas**.</span></span>  
  
31. <span data-ttu-id="44e8e-256">按兩下包含值"Message_3"的資料列中**訊息**資料行和值"MessageBody 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="44e8e-256">Double-click the row that contains the value “Message_3” in the **Message** column and the value “MessageBody” in the **Part** column.</span></span>  
  
32. <span data-ttu-id="44e8e-257">展開**Schema3**，然後將拖曳**Data3**右窗格中**Data2**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-257">Expand **Schema3**, and then drag **Data3** in the right pane to **Data2** in the left pane.</span></span>  
  
33. <span data-ttu-id="44e8e-258">從右窗格上方的下拉式清單選取**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-258">From the drop-down list above the right pane, select **Message Payload Schemas**.</span></span>  
  
34. <span data-ttu-id="44e8e-259">按兩下包含值"Message_3"的資料列中**訊息**資料行和值"BAMPart 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="44e8e-259">Double-click the row that contains the value “Message_3” in the **Message** column and the value “BAMPart” in the **Part** column.</span></span>  
  
35. <span data-ttu-id="44e8e-260">展開**BAMPart**，然後將拖曳**DocumentID**右窗格中**Orch3_**的左窗格中的接續。</span><span class="sxs-lookup"><span data-stu-id="44e8e-260">Expand **BAMPart**, and then drag **DocumentID** in the right pane to the **Orch3_** continuation in the left pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44e8e-261">請勿將 Orch3_ 接續與 Orch3_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="44e8e-261">Do not confuse the Orch3_ continuation with the Orch3_ continuation ID.</span></span> <span data-ttu-id="44e8e-262">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="44e8e-262">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  
  
36. <span data-ttu-id="44e8e-263">按一下**選取事件來源**，然後按一下 **選取協調流程排程**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-263">Click **Select Event Source**, and then click **Select Orchestration Schedule**.</span></span>  
  
37. <span data-ttu-id="44e8e-264">在**組件名稱**區段**選取的事件來源父組件**對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-264">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, and then click **Next**.</span></span>  
  
38. <span data-ttu-id="44e8e-265">在**協調流程的名稱**區段**選取協調流程**對話方塊中，選取**BamEndToEnd.Services.Orchestration3**，然後按一下  **確定**.</span><span class="sxs-lookup"><span data-stu-id="44e8e-265">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamEndToEnd.Services.Orchestration3**, and then click **OK**.</span></span>  
  
39. <span data-ttu-id="44e8e-266">以滑鼠右鍵按一下**[receive1]**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-266">Right-click the **Receive1** shape, and then click **Message Payload Schemas**.</span></span>  
  
40. <span data-ttu-id="44e8e-267">按兩下包含值"Message_3"的資料列中**訊息**資料行和值"BAMPart 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="44e8e-267">Double-click the row that contains the value “Message_3” in the **Message** column and the value “BAMPart” in the **Part** column.</span></span>  
  
41. <span data-ttu-id="44e8e-268">展開**BAMPart**，然後將拖曳**DocumentID**右窗格中**Orch3_**接續識別碼的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-268">Expand **BAMPart**, and then drag **DocumentID** in the right pane to the **Orch3_** continuation ID in the left pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44e8e-269">請勿將 Orch3_ 接續與 Orch3_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="44e8e-269">Do not confuse the Orch3_ continuation with the Orch3_ continuation ID.</span></span> <span data-ttu-id="44e8e-270">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="44e8e-270">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  
  
42. <span data-ttu-id="44e8e-271">按一下資料夾圖示的箭號 (![資料夾和向上箭號按鈕](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，以顯示協調流程。</span><span class="sxs-lookup"><span data-stu-id="44e8e-271">Click the folder icon with the arrow (![button with folder and up arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) twice to display the orchestration.</span></span>  
  
43. <span data-ttu-id="44e8e-272">拖曳**[receive1]**右窗格中的圖形**SBegin3**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-272">Drag the **Receive1** shape in the right pane to **SBegin3** in the left pane.</span></span>  
  
44. <span data-ttu-id="44e8e-273">拖曳**[send_1]**右窗格中的圖形**SEnd3**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-273">Drag the **Send_1** shape in the right pane to **SEnd3** in the left pane.</span></span>  
  
45. <span data-ttu-id="44e8e-274">以滑鼠右鍵按一下**[send_1]**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-274">Right-click the **Send_1** shape, and then click **Message Payload Schema**.</span></span>  
  
46. <span data-ttu-id="44e8e-275">展開**Schema3**，然後將拖曳**Data3**右窗格中**Data3**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="44e8e-275">Expand **Schema3**, and then drag **Data3** in the right pane to **Data3** in the left pane.</span></span>  
  
47. <span data-ttu-id="44e8e-276">以滑鼠右鍵按一下**DocumentID**下方**Orch2_**接續，然後再按一下**設定連接埠對應**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-276">Right-click **DocumentID** below the **Orch2_** continuation, and then click **Set Port Mappings**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="44e8e-277">請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="44e8e-277">Do not confuse the Orch2_ continuation with the Orch2_ continuation ID.</span></span> <span data-ttu-id="44e8e-278">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="44e8e-278">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  
  
48. <span data-ttu-id="44e8e-279">在**選取連接埠**區段**選取連接埠**對話方塊中，按一下**BamEndToEnd_ReceivePort**，按一下 較大-符號 ( **>**)，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="44e8e-279">In the **Select Ports** section of the **Select Ports** dialog box, click **BamEndToEnd_ReceivePort**, click the greater-than sign (**>**), and then click **OK**.</span></span>  
  
49. <span data-ttu-id="44e8e-280">儲存追蹤設定檔來*\<範例路徑 >*\BAM\BamEndToEnd\BamEndToEnd.btt。</span><span class="sxs-lookup"><span data-stu-id="44e8e-280">Save the tracking profile to *\<Samples Path>*\BAM\BamEndToEnd\BamEndToEnd.btt.</span></span>  
  
## <a name="important-details"></a><span data-ttu-id="44e8e-281">重要的詳細資料</span><span class="sxs-lookup"><span data-stu-id="44e8e-281">Important details</span></span>  
 <span data-ttu-id="44e8e-282">追蹤設定檔不支援管線。</span><span class="sxs-lookup"><span data-stu-id="44e8e-282">Tracking profiles are not supported for pipelines.</span></span> <span data-ttu-id="44e8e-283">不過，呼叫**BeginActivity**在管線元件是在協調流程中使用 ActivityID 相同。</span><span class="sxs-lookup"><span data-stu-id="44e8e-283">However, the call to **BeginActivity** in the pipeline component is the same as using ActivityID in an orchestration.</span></span> <span data-ttu-id="44e8e-284">若要呼叫**EnableContinuation**與協調流程中使用接續相同。</span><span class="sxs-lookup"><span data-stu-id="44e8e-284">The call to **EnableContinuation** is the same as using a continuation in an orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e8e-285">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44e8e-285">See Also</span></span>  
 [<span data-ttu-id="44e8e-286">商務活動監控 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="44e8e-286">Business Activity Monitoring (BizTalk Server Samples Folder)</span></span>](../core/business-activity-monitoring-biztalk-server-samples-folder.md)