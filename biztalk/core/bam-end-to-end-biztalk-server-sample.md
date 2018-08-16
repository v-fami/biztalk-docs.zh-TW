---
title: 在 BizTalk Server 中的 BAM 端對端範例 |Microsoft Docs
description: 如何從使用 「 商務活動監控 BizTalk Server 中的多個元件的事件相互關聯的案例
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81406038-7f3f-499f-a003-12423d92c44b
caps.latest.revision: 35
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fca4bd709a872df739d82fbdfbeabc78df9d09f0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006495"
---
# <a name="bam-end-to-end-biztalk-server-sample"></a><span data-ttu-id="3aa9d-103">BAM 端對端 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="3aa9d-103">BAM End-to-End (BizTalk Server Sample)</span></span>
<span data-ttu-id="3aa9d-104">端對端範例會示範如何使用 BAM 來使多個元件 (在此例中是三個協調流程和一個管線) 中的事件相互產生關聯。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-104">The End-to-End sample demonstrates how to correlate events from multiple components (in this case, three orchestrations and a pipeline) by using BAM.</span></span>  

 <span data-ttu-id="3aa9d-105">BAM 會重新建構跨越管線元件和協調流程的商務活動。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-105">BAM reconstructs the business activity that spans the pipeline component and orchestrations.</span></span> <span data-ttu-id="3aa9d-106">這適用於在最低層級中，藉由呼叫**EventStream.EnableContinuation**從需要更多活動事件的每個實作元件。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-106">At the lowest level, this works by calls to **EventStream.EnableContinuation** from each implementation component that expects more events for the activity.</span></span> <span data-ttu-id="3aa9d-107">若要在呼叫**EnableContinuation**是明確的而 Orchestration1 和 Orchestration2 中會藉由將 Continuation 資料夾加入至一個排程，並依照排程的 [ContinuationID] 資料夾中的追蹤設定檔的呼叫它。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-107">The call to **EnableContinuation** is explicit, while calls in Orchestration1 and Orchestration2 are made by adding a Continuation folder to the Tracking profile in one schedule, and a ContinuationID folder to the schedule that follows it.</span></span>  

 <span data-ttu-id="3aa9d-108">下圖說明範例中使用的工作流程。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-108">The following diagram illustrates the workflow used in the sample.</span></span>  

 <span data-ttu-id="3aa9d-109">![](../core/media/ebiz-sdk-samples-bam-endtoendwkflw.gif "ebiz_sdk_samples_bam_endtoendwkflw")</span><span class="sxs-lookup"><span data-stu-id="3aa9d-109">![](../core/media/ebiz-sdk-samples-bam-endtoendwkflw.gif "ebiz_sdk_samples_bam_endtoendwkflw")</span></span>  


## <a name="what-this-sample-does"></a><span data-ttu-id="3aa9d-110">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="3aa9d-110">What This Sample Does</span></span>  
 <span data-ttu-id="3aa9d-111">BAM 端對端範例會示範如何使用 BAM 蒐集一個管線愈多個協調流程的資訊，並更新單一活動。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-111">The BAM end-to-end sample shows how you can use BAM to gather information from a pipeline and multiple orchestrations and update a single activity.</span></span>  

## <a name="how-this-sample-was-designed-and-why"></a><span data-ttu-id="3aa9d-112">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="3aa9d-112">How This Sample Was Designed and Why</span></span>  
 <span data-ttu-id="3aa9d-113">BAM 端對端範例是針對說明下列活動而設計：</span><span class="sxs-lookup"><span data-stu-id="3aa9d-113">The BAM end-to-end sample was designed to illustrate the following activities:</span></span>  

-   <span data-ttu-id="3aa9d-114">在管線內使用 BAM。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-114">Using BAM within a pipeline.</span></span>  

-   <span data-ttu-id="3aa9d-115">使用追蹤設定檔編輯器 (TPE) 將活動項目對應到協調流程與訊息元素中的圖形。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-115">Using the Tracking Profile Editor (TPE) to map activity items to shapes in an orchestration and elements of a message.</span></span>  

-   <span data-ttu-id="3aa9d-116">使用要保持活動作用中時多段方案參與活動的接續。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-116">Using continuations to keep an activity active when multiple pieces of a solution contribute to the activity.</span></span>  


<span data-ttu-id="3aa9d-117">範例的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="3aa9d-117">The sample works as follows:</span></span>  

1.  <span data-ttu-id="3aa9d-118">輸入的訊息會從*\<範例路徑\>* \BamEndToEnd\Input 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-118">An input message is retrieved from the *\<Samples Path\>* \BamEndToEnd\Input folder.</span></span>  

2.  <span data-ttu-id="3aa9d-119">管線元件指派唯一的 DocumentID 給訊息，並使用 BAM API 來開始新的 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-119">The pipeline component assigns a unique DocumentID to the message, and uses the BAM API to begin a new BAM activity.</span></span> <span data-ttu-id="3aa9d-120">DocumentID 會附加當做輸入訊息的個別部分，供協調流程使用。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-120">The DocumentID is attached as a separate part of the input message to make it available to the orchestrations.</span></span>  

3.  <span data-ttu-id="3aa9d-121">收到輸入訊息時，就會啟動 Orchestration1 服務。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-121">The service Orchestration1 is activated when the input message is received.</span></span>  

4.  <span data-ttu-id="3aa9d-122">Orchestration1 修改輸入訊息，並將它當做參數傳遞給 Orchestration2。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-122">Orchestration1 modifies the input message and passes it as a parameter to Orchestration2.</span></span>  

5.  <span data-ttu-id="3aa9d-123">Orchestration2 修改輸入的訊息，並將它傳送至 MessageBox 資料庫中，會啟動 Orchestration3。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-123">Orchestration2 modifies the input message and sends it to the MessageBox database, which activates Orchestration3.</span></span>  

6.  <span data-ttu-id="3aa9d-124">Orchestration3 修改訊息，並將它寫入至資料夾*\<範例路徑\>* \BamEndToEnd\Output。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-124">Orchestration3 modifies the message and writes it to the folder *\<Samples Path\>* \BamEndToEnd\Output.</span></span>  

7.  <span data-ttu-id="3aa9d-125">每個協調流程會更新 BAM 活動中的活動項目。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-125">Each orchestration updates activity items in the BAM activity.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="3aa9d-126">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="3aa9d-126">Where to Find This Sample</span></span>  
 <span data-ttu-id="3aa9d-127">您可以找到在此範例*\<範例路徑\>* \BAM\BamEndToEnd。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-127">You can find this sample at *\<Samples Path\>* \BAM\BamEndToEnd.</span></span>  

 <span data-ttu-id="3aa9d-128">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-128">The following table shows the files in this sample and describes their purpose.</span></span>  


|                                        <span data-ttu-id="3aa9d-129">檔案</span><span class="sxs-lookup"><span data-stu-id="3aa9d-129">File(s)</span></span>                                        |                                         <span data-ttu-id="3aa9d-130">描述</span><span class="sxs-lookup"><span data-stu-id="3aa9d-130">Description</span></span>                                          |
|---------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
|                                    <span data-ttu-id="3aa9d-131">BamEndToEnd.sln</span><span class="sxs-lookup"><span data-stu-id="3aa9d-131">BamEndToEnd.sln</span></span>                                    |                               <span data-ttu-id="3aa9d-132">BAM 端對端範例方案。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-132">BAM End-to-End sample solution.</span></span>                                |
|                                    <span data-ttu-id="3aa9d-133">BamEndToEnd.xls</span><span class="sxs-lookup"><span data-stu-id="3aa9d-133">BamEndToEnd.xls</span></span>                                    |                                 <span data-ttu-id="3aa9d-134">BAM 定義樣式表。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-134">BAM definition style sheet.</span></span>                                  |
|                                    <span data-ttu-id="3aa9d-135">BamEndToEnd.xml</span><span class="sxs-lookup"><span data-stu-id="3aa9d-135">BamEndToEnd.xml</span></span>                                    |                                     <span data-ttu-id="3aa9d-136">BAM 定義 XML。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-136">BAM definition XML.</span></span>                                      |
|                                <span data-ttu-id="3aa9d-137">BAMEndToEndBinding.xml</span><span class="sxs-lookup"><span data-stu-id="3aa9d-137">BAMEndToEndBinding.xml</span></span>                                 |                                         <span data-ttu-id="3aa9d-138">BAM 繫結。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-138">BAM binding.</span></span>                                         |
|                                      <span data-ttu-id="3aa9d-139">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="3aa9d-139">Cleanup.bat</span></span>                                      |                              <span data-ttu-id="3aa9d-140">用來解除部署範例的批次檔。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-140">Batch file to undeploy the sample.</span></span>                              |
|                                   <span data-ttu-id="3aa9d-141">InputMessage.xml</span><span class="sxs-lookup"><span data-stu-id="3aa9d-141">InputMessage.xml</span></span>                                    |                                        <span data-ttu-id="3aa9d-142">輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-142">Input message.</span></span>                                        |
|                                       <span data-ttu-id="3aa9d-143">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="3aa9d-143">Setup.bat</span></span>                                       |                         <span data-ttu-id="3aa9d-144">用來編譯和部署範例的批次檔。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-144">Batch file to compile and deploy the sample.</span></span>                         |
|                              <span data-ttu-id="3aa9d-145">\Components\AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="3aa9d-145">\Components\AssemblyInfo.cs</span></span>                              |                                   <span data-ttu-id="3aa9d-146">管線元件程式碼。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-146">Pipeline component code.</span></span>                                   |
|                       <span data-ttu-id="3aa9d-147">\Components\BAMMessagePartPLComponent.cs</span><span class="sxs-lookup"><span data-stu-id="3aa9d-147">\Components\BAMMessagePartPLComponent.cs</span></span>                        |                                   <span data-ttu-id="3aa9d-148">管線元件程式碼。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-148">Pipeline component code.</span></span>                                   |
|                             <span data-ttu-id="3aa9d-149">\Components\Components.csproj</span><span class="sxs-lookup"><span data-stu-id="3aa9d-149">\Components\Components.csproj</span></span>                             |                                 <span data-ttu-id="3aa9d-150">管線元件專案。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-150">Pipeline component project.</span></span>                                  |
| <span data-ttu-id="3aa9d-151">\Messages\InputMessage01.xml</span><span class="sxs-lookup"><span data-stu-id="3aa9d-151">\Messages\InputMessage01.xml</span></span><br /><br /> <span data-ttu-id="3aa9d-152">...</span><span class="sxs-lookup"><span data-stu-id="3aa9d-152">...</span></span><br /><br /> <span data-ttu-id="3aa9d-153">\Messages\InputMessage10.xml</span><span class="sxs-lookup"><span data-stu-id="3aa9d-153">\Messages\InputMessage10.xml</span></span> |                                    <span data-ttu-id="3aa9d-154">輸入訊息範例。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-154">Sample input messages.</span></span>                                    |
|                               <span data-ttu-id="3aa9d-155">\Services\BAMInbound.btp</span><span class="sxs-lookup"><span data-stu-id="3aa9d-155">\Services\BAMInbound.btp</span></span>                                |                                    <span data-ttu-id="3aa9d-156">輸入管線檔案。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-156">Inbound pipeline file.</span></span>                                    |
|                              <span data-ttu-id="3aa9d-157">\Services\BAMPartSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="3aa9d-157">\Services\BAMPartSchema.xsd</span></span>                              |                                   <span data-ttu-id="3aa9d-158">BAM 部分訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-158">BAM part message schema.</span></span>                                   |
|                             <span data-ttu-id="3aa9d-159">\Services\Orchestration1.odx</span><span class="sxs-lookup"><span data-stu-id="3aa9d-159">\Services\Orchestration1.odx</span></span>                              |                                        <span data-ttu-id="3aa9d-160">協調流程。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-160">Orchestration.</span></span>                                        |
|                             <span data-ttu-id="3aa9d-161">\Services\Orchestration2.odx</span><span class="sxs-lookup"><span data-stu-id="3aa9d-161">\Services\Orchestration2.odx</span></span>                              |                                        <span data-ttu-id="3aa9d-162">協調流程。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-162">Orchestration.</span></span>                                        |
|                             <span data-ttu-id="3aa9d-163">\Services\Orchestration3.odx</span><span class="sxs-lookup"><span data-stu-id="3aa9d-163">\Services\Orchestration3.odx</span></span>                              |                                        <span data-ttu-id="3aa9d-164">協調流程。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-164">Orchestration.</span></span>                                        |
|                             <span data-ttu-id="3aa9d-165">\Services\PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="3aa9d-165">\Services\PropertySchema.xsd</span></span>                              |                                       <span data-ttu-id="3aa9d-166">屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-166">Property schema.</span></span>                                       |
|                                 <span data-ttu-id="3aa9d-167">\Services\Schema1.xsd</span><span class="sxs-lookup"><span data-stu-id="3aa9d-167">\Services\Schema1.xsd</span></span>                                 |                                       <span data-ttu-id="3aa9d-168">訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-168">Message schema.</span></span>                                        |
|                                 <span data-ttu-id="3aa9d-169">\Services\Schema2.xsd</span><span class="sxs-lookup"><span data-stu-id="3aa9d-169">\Services\Schema2.xsd</span></span>                                 |                                       <span data-ttu-id="3aa9d-170">訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-170">Message schema.</span></span>                                        |
|                                 <span data-ttu-id="3aa9d-171">Services\Schema3.xsd</span><span class="sxs-lookup"><span data-stu-id="3aa9d-171">Services\Schema3.xsd</span></span>                                  |                                       <span data-ttu-id="3aa9d-172">訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-172">Message schema.</span></span>                                        |
|                               <span data-ttu-id="3aa9d-173">\Services\Services.btproj</span><span class="sxs-lookup"><span data-stu-id="3aa9d-173">\Services\Services.btproj</span></span>                               | [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="3aa9d-174"> BizTalk 檔案專案。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-174"> BizTalk file project.</span></span> |
|                               <span data-ttu-id="3aa9d-175">\Services\Transform_1.btm</span><span class="sxs-lookup"><span data-stu-id="3aa9d-175">\Services\Transform_1.btm</span></span>                               |                                          <span data-ttu-id="3aa9d-176">對應檔案。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-176">Map file.</span></span>                                           |
|                               <span data-ttu-id="3aa9d-177">\Services\Transform_2.btm</span><span class="sxs-lookup"><span data-stu-id="3aa9d-177">\Services\Transform_2.btm</span></span>                               |                                          <span data-ttu-id="3aa9d-178">對應檔案。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-178">Map file.</span></span>                                           |
|                               <span data-ttu-id="3aa9d-179">\Services\Transform_3.btm</span><span class="sxs-lookup"><span data-stu-id="3aa9d-179">\Services\Transform_3.btm</span></span>                               |                                          <span data-ttu-id="3aa9d-180">對應檔案。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-180">Map file.</span></span>                                           |

## <a name="how-to-use-this-sample"></a><span data-ttu-id="3aa9d-181">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="3aa9d-181">How to Use This Sample</span></span>  
 <span data-ttu-id="3aa9d-182">您可以使用下列程序來建置並執行 BAM 端對端範例：</span><span class="sxs-lookup"><span data-stu-id="3aa9d-182">Use the following procedures to build and run the BAM End-to-End sample:</span></span>  

-   [<span data-ttu-id="3aa9d-183">若要建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="3aa9d-183">To build and initialize this sample</span></span>](#To_Build_Sample)  

-   [<span data-ttu-id="3aa9d-184">若要執行此範例</span><span class="sxs-lookup"><span data-stu-id="3aa9d-184">To run this sample</span></span>](#To_Run_Sample)  

-   [<span data-ttu-id="3aa9d-185">若要檢視 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="3aa9d-185">To view the BAM data</span></span>](#To_View_Data)  

##  <a name="To_Build_Sample"></a><span data-ttu-id="3aa9d-186">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="3aa9d-186">Build and initialize this sample</span></span>  

1.  <span data-ttu-id="3aa9d-187">開啟命令提示字元，以系統管理員身分，然後執行*\<範例路徑\>* \BAM\BAMEndToEnd\Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-187">Open a command prompt as Administrator, and run *\<Samples Path\>* \BAM\BAMEndToEnd\Setup.bat.</span></span> <span data-ttu-id="3aa9d-188">Setup.bat 隨即建置及初始化此範例的 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-188">Setup.bat builds and initializes the BAM infrastructure for this sample.</span></span> <span data-ttu-id="3aa9d-189">保持命令提示字元開啟。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-189">Keep the command prompt open.</span></span>  

2.  <span data-ttu-id="3aa9d-190">建立追蹤設定檔，將 Orchestration1、 Orchestration2 和 Orchestration3 對應到 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-190">Create a tracking profile to map Orchestration1, Orchestration2, and Orchestration3 to the BAM activity.</span></span> <span data-ttu-id="3aa9d-191">(在個別的程序呼叫中建立追蹤設定檔是複雜的程序，因為有詳細的指示**建立追蹤設定檔**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-191">(Because creating the tracking profile is a complex process, the detailed instructions are in a separate procedure called **To create a tracking profile**.</span></span> <span data-ttu-id="3aa9d-192">此程序會出現在本文稍後。）</span><span class="sxs-lookup"><span data-stu-id="3aa9d-192">This procedure appears later in this document.)</span></span>  

3.  <span data-ttu-id="3aa9d-193">部署您在上一個步驟中建立的 BamEndToEnd.btt 追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-193">Deploy the tracking profile BamEndToEnd.btt that you created in the previous step.</span></span>  <span data-ttu-id="3aa9d-194">在 命令提示字元變更為*\<範例路徑\>* \BAM\BamEndToEnd 目錄。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-194">In the command prompt change to the *\<Samples Path\>* \BAM\BamEndToEnd directory.</span></span> <span data-ttu-id="3aa9d-195">若要部署追蹤設定檔，輸入下列命令，命令並按**Enter**:</span><span class="sxs-lookup"><span data-stu-id="3aa9d-195">To deploy the tracking profile, type the following line, and then press **Enter**:</span></span>  

    `“<BizTalkInstallationPath>\Tracking\bttdeploy” BamEndToEnd.btt`

     <span data-ttu-id="3aa9d-196">[如何使用追蹤設定檔管理公用程式部署追蹤設定檔](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md)提供詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-196">[How to Deploy Tracking Profiles with the Tracking Profiles Management Utility](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md) provides more information.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="3aa9d-197">您可以忽略訊息 ContinuationID Orch1_ 沒有相符的接續。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-197">You can ignore the message that the ContinuationID Orch1_ does not have a matching Continuation.</span></span> <span data-ttu-id="3aa9d-198">預期此訊息，因為在管線元件中，而不是在追蹤設定檔，會定義名為 Orch1_ 接續。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-198">This message is expected, because the continuation named Orch1_ is defined in the pipeline component, and not in the tracking profile.</span></span>  

##  <a name="To_Run_Sample"></a><span data-ttu-id="3aa9d-199">執行此範例</span><span class="sxs-lookup"><span data-stu-id="3aa9d-199">Run this sample</span></span>  

<span data-ttu-id="3aa9d-200">將檔案複製*\<範例路徑\>* \BamEndToEnd\InputMessage.xml 到資料夾*\<範例路徑\>* \BamEndToEnd\Input。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-200">Copy the file *\<Samples Path\>* \BamEndToEnd\InputMessage.xml into the folder *\<Samples Path\>* \BamEndToEnd\Input.</span></span> <span data-ttu-id="3aa9d-201">幾秒鐘後，訊息會消失在輸入資料夾中，而輸出訊息會出現在*\<範例路徑\>* \BamEndToEnd\Output 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-201">After a few seconds, the message disappears from the Input folder, and an output message appears in the *\<Samples Path\>* \BamEndToEnd\Output folder.</span></span>  

##  <a name="To_View_Data"></a><span data-ttu-id="3aa9d-202">檢視 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="3aa9d-202">View the BAM data</span></span>  

1.  <span data-ttu-id="3aa9d-203">開啟 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-203">Open SQL Server Management Studio.</span></span>  

2.  <span data-ttu-id="3aa9d-204">在 SQL Server Management Studio 中，展開伺服器，展開**資料庫**，展開**BAMPrimaryImport**，然後展開**資料表**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-204">In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.</span></span>  

3.  <span data-ttu-id="3aa9d-205">以滑鼠右鍵按一下**dbo.bam_EndToEndActivity_Completed**，然後按一下**開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-205">Right-click **dbo.bam_EndToEndActivity_Completed**, and then click **Open Table**.</span></span> <span data-ttu-id="3aa9d-206">如果您使用 SQL Server，請按一下**選取前 1000 個資料列**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-206">If you are using SQL Server, click **Select top 1000 rows**.</span></span>  

     <span data-ttu-id="3aa9d-207">Bam_EndToEndActivity_Completed 資料表的內容會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-207">The contents of the bam_EndToEndActivity_Completed table are displayed in the right pane.</span></span> <span data-ttu-id="3aa9d-208">在資料表中的每個資料列會代表已完成的 [endtoendactivity] 活動。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-208">Each row in the table represents an EndToEndActivity activity that has been completed.</span></span>  

#### <a name="rerun-this-sample"></a><span data-ttu-id="3aa9d-209">重新執行此範例</span><span class="sxs-lookup"><span data-stu-id="3aa9d-209">Rerun this sample</span></span>  

1. <span data-ttu-id="3aa9d-210">開啟命令提示字元，以系統管理員身分，並將*\<範例路徑\>* \BAM\BamEndToEnd 目錄。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-210">Open a command prompt as Administrator, and change to the *\<Samples Path\>* \BAM\BamEndToEnd directory.</span></span> <span data-ttu-id="3aa9d-211">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="3aa9d-211">Type the following line:</span></span>  

   `“C:\Program Files\Microsoft BizTalk Server <version>\Tracking\bttdeploy” BamEndToEnd.btt /remove`  

   > [!NOTE]
   >  <span data-ttu-id="3aa9d-212">如果您未安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]到 C 磁碟機中，取代為"C"安裝所在的磁碟機代號[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-212">If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the C drive, replace "C" with the drive letter where you installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  

2. <span data-ttu-id="3aa9d-213">執行*\<範例路徑\>* \BAM\BAMEndToEnd\Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-213">Run *\<Samples Path\>* \BAM\BAMEndToEnd\Cleanup.bat.</span></span> <span data-ttu-id="3aa9d-214">Cleanup.bat 會移除此範例的 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-214">Cleanup.bat removes the BAM infrastructure for this sample.</span></span>  

3. <span data-ttu-id="3aa9d-215">執行中的步驟**建置和初始化此範例**本主題中的區段。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-215">Perform the steps in **To build and initialize this sample** section in this topic.</span></span>  

##  <a name="TPE_procedure"></a><span data-ttu-id="3aa9d-216">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="3aa9d-216">Create a tracking profile</span></span>  

1. <span data-ttu-id="3aa9d-217">按一下 **開始**，指向**所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-217">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)].</span></span> <span data-ttu-id="3aa9d-218">以滑鼠右鍵按一下**Tracking Profile Editor**，並**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-218">Right-click **Tracking Profile Editor**, and **Run as administrator**.</span></span>  

2. <span data-ttu-id="3aa9d-219">在左窗格中**Tracking Profile Editor**  視窗中，按一下**匯入 BAM 活動定義，請按一下這裡**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-219">In the left pane of the **Tracking Profile Editor** window, click **Click here to import a BAM Activity Definition**.</span></span>  

3. <span data-ttu-id="3aa9d-220">在  **BAM 活動定義名稱**一節**匯入 BAM 活動定義**對話方塊中，選取**endtoendactivity**，然後按一下  **確定**.</span><span class="sxs-lookup"><span data-stu-id="3aa9d-220">In the  **BAM Activity Definition Name** section of the **Import BAM Activity Definition** dialog box, select **EndToEndActivity**, and then click **OK**.</span></span>  

4. <span data-ttu-id="3aa9d-221">在右窗格中**Tracking Profile Editor**  視窗中，按一下**按一下這裡選取事件來源**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-221">In the right pane of the **Tracking Profile Editor** window, click **Click here to select an event source**.</span></span>  

5. <span data-ttu-id="3aa9d-222">在 [**組件名稱**一節**選取的事件來源父組件**] 對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-222">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, and then click **Next**.</span></span>  

6. <span data-ttu-id="3aa9d-223">在**協調流程的名稱**一節**選取協調流程**] 對話方塊中，選取**BamEndToEnd.Services.Orchestration1**，然後按一下 [ **[確定]**.</span><span class="sxs-lookup"><span data-stu-id="3aa9d-223">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamEndToEnd.Services.Orchestration1**, and then click **OK**.</span></span>  

7. <span data-ttu-id="3aa9d-224">在左窗格中**Tracking Profile Editor**  視窗中，以滑鼠右鍵按一下**endtoendactivity**，然後按一下**新 ContinuationID**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-224">In the left pane of the **Tracking Profile Editor** window, right-click **EndToEndActivity**, and then click **New ContinuationID**.</span></span> <span data-ttu-id="3aa9d-225">命名新接續識別碼**Orch1_**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-225">Name the new continuation ID **Orch1_**.</span></span> <span data-ttu-id="3aa9d-226">重複此步驟，建立兩個多個接續識別碼名為**Orch2_** 並**Orch3_**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-226">Repeat this step to create two more continuation IDs named **Orch2_** and **Orch3_**.</span></span>  

8. <span data-ttu-id="3aa9d-227">以滑鼠右鍵按一下 **[endtoendactivity]**，然後按一下**新的接續**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-227">Right-click **EndToEndActivity**, and then click **New Continuation**.</span></span> <span data-ttu-id="3aa9d-228">命名新接續**Orch2_**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-228">Name the new continuation **Orch2_**.</span></span> <span data-ttu-id="3aa9d-229">重複此步驟，建立名為另一個接續**Orch3_**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-229">Repeat this step to create another continuation named **Orch3_**.</span></span>  

9. <span data-ttu-id="3aa9d-230">以滑鼠右鍵按一下 **[receive1]** 圖形，，然後按一下**內容屬性結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-230">Right-click the **Receive1** shape, and then click **Context Property Schemas**.</span></span>  

10. <span data-ttu-id="3aa9d-231">捲動至結尾**內容屬性名稱**清單，然後再連按兩下**BAMEndToEnd.Services.PropertySchema.DocumentID**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-231">Scroll to the end of the **Context Property Name** list, and then double-click **BAMEndToEnd.Services.PropertySchema.DocumentID**.</span></span>  

11. <span data-ttu-id="3aa9d-232">依序展開**\<結構描述\>**，然後將拖曳**DocumentID**右窗格中**Orch1_** 的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-232">Expand **\<Schema\>**, and then drag **DocumentID** in the right pane to **Orch1_** in the left pane.</span></span>  

12. <span data-ttu-id="3aa9d-233">按一下資料夾圖示的箭號 (![資料夾與向上箭號按鈕](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，顯示協調流程。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-233">Click the folder icon with the arrow (![button with folder and up arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) twice to display the orchestration.</span></span>  

13. <span data-ttu-id="3aa9d-234">拖曳 **[receive1]** 右窗格中的圖形**SBegin1**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-234">Drag the **Receive1** shape in the right pane to **SBegin1** in the left pane.</span></span>  

14. <span data-ttu-id="3aa9d-235">拖曳**StartOrchestration_1**右窗格中的圖形**SEnd1**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-235">Drag the **StartOrchestration_1** shape in the right pane to **SEnd1** in the left pane.</span></span>  

15. <span data-ttu-id="3aa9d-236">以滑鼠右鍵按一下**StartOrchestration_1**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-236">Right-click the **StartOrchestration_1** shape, and then click **Message Payload Schemas**.</span></span>  

16. <span data-ttu-id="3aa9d-237">按兩下包含值 「 Message_2"的資料列**訊息**資料行和值"MessageBody 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-237">Double-click the row that contains the value “Message_2” in the **Message** column and the value “MessageBody” in the **Part** column.</span></span>  

     <span data-ttu-id="3aa9d-238">![TPE 訊息內容結構描述顯示訊息&#95;2](../core/media/77fbc444-46cf-4d45-8e9c-c330da7ba7d1.gif "77fbc444-46cf-4d45-8e9c-c330da7ba7d1")</span><span class="sxs-lookup"><span data-stu-id="3aa9d-238">![TPE Message Payload schema showing message&#95;2](../core/media/77fbc444-46cf-4d45-8e9c-c330da7ba7d1.gif "77fbc444-46cf-4d45-8e9c-c330da7ba7d1")</span></span>  

17. <span data-ttu-id="3aa9d-239">依序展開**Schema2**，然後將拖曳**Data2**在右窗格**Data1**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-239">Expand **Schema2**, and then drag **Data2** in the right pane to **Data1** in the left pane.</span></span>  

18. <span data-ttu-id="3aa9d-240">按一下 **選取事件來源**，然後按一下**選取內容屬性**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-240">Click **Select Event Source**, and then click **Select Context Property**.</span></span>  

19. <span data-ttu-id="3aa9d-241">捲動至結尾**內容屬性名稱**清單，然後再連按兩下**BAMEndToEnd.Services.PropertySchema.DocumentID**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-241">Scroll to the end of the **Context Property Name** list, and then double-click **BAMEndToEnd.Services.PropertySchema.DocumentID**.</span></span>  

20. <span data-ttu-id="3aa9d-242">依序展開**\<結構描述\>**，然後將拖曳**DocumentID**至**Orch2_** 的左窗格中的接續。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-242">Expand **\<Schema\>**, and then drag **DocumentID** to the **Orch2_** continuation in the left pane.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="3aa9d-243">請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="3aa9d-243">Do not confuse the Orch2_ continuation with the Orch2_ continuation ID.</span></span> <span data-ttu-id="3aa9d-244">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-244">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  

21. <span data-ttu-id="3aa9d-245">按一下 **選取事件來源**，然後按一下**選取協調流程排程**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-245">Click **Select Event Source**, and then click **Select Orchestration Schedule**.</span></span>  

22. <span data-ttu-id="3aa9d-246">在 [**組件名稱**一節**選取的事件來源父組件**] 對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-246">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, and then click **Next**.</span></span>  

23. <span data-ttu-id="3aa9d-247">在**協調流程的名稱**一節**選取協調流程**] 對話方塊中，選取**BamEndToEnd.Services.Orchestration2**，然後按一下 [ **[確定]**.</span><span class="sxs-lookup"><span data-stu-id="3aa9d-247">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamEndToEnd.Services.Orchestration2**, and then click **OK**.</span></span>  

24. <span data-ttu-id="3aa9d-248">以滑鼠右鍵按一下 **[constructmessage_1]** 圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-248">Right-click the **ConstructMessage_1** shape, and then click **Message Payload Schemas**.</span></span>  

25. <span data-ttu-id="3aa9d-249">按兩下包含值 「 Message_3"的資料列**訊息**資料行和值"BAMPart 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-249">Double-click the row that contains the value “Message_3” in the **Message** column and the value “BAMPart” in the **Part** column.</span></span>  

26. <span data-ttu-id="3aa9d-250">依序展開**BAMPart**，然後將拖曳**DocumentID**在右窗格**Orch2_** 接續識別碼的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-250">Expand **BAMPart**, and then drag **DocumentID** in the right pane to the **Orch2_** continuation ID in the left pane.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="3aa9d-251">請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="3aa9d-251">Do not confuse the Orch2_ continuation with the Orch2_ continuation ID.</span></span> <span data-ttu-id="3aa9d-252">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-252">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  

27. <span data-ttu-id="3aa9d-253">按一下資料夾圖示的箭號 (![按鈕與資料夾，然後註冊&#45;箭號](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，顯示協調流程。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-253">Click the folder icon with the arrow (![button with folder and up&#45;arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) twice to display the orchestration.</span></span>  

28. <span data-ttu-id="3aa9d-254">拖曳 **[constructmessage_1]** 右窗格中的圖形**SBegin2**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-254">Drag the **ConstructMessage_1** shape in the right pane to **SBegin2** in the left pane.</span></span>  

29. <span data-ttu-id="3aa9d-255">拖曳**Send_1**右窗格中的圖形**SEnd2**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-255">Drag the **Send_1** shape in the right pane to **SEnd2** in the left pane.</span></span>  

30. <span data-ttu-id="3aa9d-256">以滑鼠右鍵按一下**Send_1**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-256">Right-click the **Send_1** shape, and then click **Message Payload Schemas**.</span></span>  

31. <span data-ttu-id="3aa9d-257">按兩下包含值 「 Message_3"的資料列**訊息**資料行和值"MessageBody 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-257">Double-click the row that contains the value “Message_3” in the **Message** column and the value “MessageBody” in the **Part** column.</span></span>  

32. <span data-ttu-id="3aa9d-258">依序展開**Schema3**，然後將拖曳**Data3**在右窗格**Data2**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-258">Expand **Schema3**, and then drag **Data3** in the right pane to **Data2** in the left pane.</span></span>  

33. <span data-ttu-id="3aa9d-259">從右窗格上方的下拉式清單選取**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-259">From the drop-down list above the right pane, select **Message Payload Schemas**.</span></span>  

34. <span data-ttu-id="3aa9d-260">按兩下包含值 「 Message_3"的資料列**訊息**資料行和值"BAMPart 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-260">Double-click the row that contains the value “Message_3” in the **Message** column and the value “BAMPart” in the **Part** column.</span></span>  

35. <span data-ttu-id="3aa9d-261">依序展開**BAMPart**，然後將拖曳**DocumentID**在右窗格**Orch3_** 的左窗格中的接續。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-261">Expand **BAMPart**, and then drag **DocumentID** in the right pane to the **Orch3_** continuation in the left pane.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="3aa9d-262">請勿將 Orch3_ 接續與 Orch3_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="3aa9d-262">Do not confuse the Orch3_ continuation with the Orch3_ continuation ID.</span></span> <span data-ttu-id="3aa9d-263">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-263">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  

36. <span data-ttu-id="3aa9d-264">按一下 **選取事件來源**，然後按一下**選取協調流程排程**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-264">Click **Select Event Source**, and then click **Select Orchestration Schedule**.</span></span>  

37. <span data-ttu-id="3aa9d-265">在 [**組件名稱**一節**選取的事件來源父組件**] 對話方塊中，選取**Microsoft.Samples.BizTalk.BamEndToEnd.Services**，然後按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-265">In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamEndToEnd.Services**, and then click **Next**.</span></span>  

38. <span data-ttu-id="3aa9d-266">在**協調流程的名稱**一節**選取協調流程**] 對話方塊中，選取**BamEndToEnd.Services.Orchestration3**，然後按一下 [ **[確定]**.</span><span class="sxs-lookup"><span data-stu-id="3aa9d-266">In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamEndToEnd.Services.Orchestration3**, and then click **OK**.</span></span>  

39. <span data-ttu-id="3aa9d-267">以滑鼠右鍵按一下 **[receive1]** 圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-267">Right-click the **Receive1** shape, and then click **Message Payload Schemas**.</span></span>  

40. <span data-ttu-id="3aa9d-268">按兩下包含值 「 Message_3"的資料列**訊息**資料行和值"BAMPart 」 中**一部分**資料行。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-268">Double-click the row that contains the value “Message_3” in the **Message** column and the value “BAMPart” in the **Part** column.</span></span>  

41. <span data-ttu-id="3aa9d-269">依序展開**BAMPart**，然後將拖曳**DocumentID**在右窗格**Orch3_** 接續識別碼的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-269">Expand **BAMPart**, and then drag **DocumentID** in the right pane to the **Orch3_** continuation ID in the left pane.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="3aa9d-270">請勿將 Orch3_ 接續與 Orch3_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="3aa9d-270">Do not confuse the Orch3_ continuation with the Orch3_ continuation ID.</span></span> <span data-ttu-id="3aa9d-271">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-271">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  

42. <span data-ttu-id="3aa9d-272">按一下資料夾圖示的箭號 (![資料夾與向上箭號按鈕](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) 兩次，顯示協調流程。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-272">Click the folder icon with the arrow (![button with folder and up arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) twice to display the orchestration.</span></span>  

43. <span data-ttu-id="3aa9d-273">拖曳 **[receive1]** 右窗格中的圖形**SBegin3**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-273">Drag the **Receive1** shape in the right pane to **SBegin3** in the left pane.</span></span>  

44. <span data-ttu-id="3aa9d-274">拖曳**Send_1**右窗格中的圖形**SEnd3**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-274">Drag the **Send_1** shape in the right pane to **SEnd3** in the left pane.</span></span>  

45. <span data-ttu-id="3aa9d-275">以滑鼠右鍵按一下**Send_1**圖形，，然後按一下**訊息內容結構描述**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-275">Right-click the **Send_1** shape, and then click **Message Payload Schema**.</span></span>  

46. <span data-ttu-id="3aa9d-276">依序展開**Schema3**，然後將拖曳**Data3**在右窗格**Data3**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-276">Expand **Schema3**, and then drag **Data3** in the right pane to **Data3** in the left pane.</span></span>  

47. <span data-ttu-id="3aa9d-277">以滑鼠右鍵按一下**DocumentID**下方**Orch2_** 接續，，然後按一下**設定連接埠對應**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-277">Right-click **DocumentID** below the **Orch2_** continuation, and then click **Set Port Mappings**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="3aa9d-278">請勿將 Orch2_ 接續與 Orch2_ 接續識別碼混淆</span><span class="sxs-lookup"><span data-stu-id="3aa9d-278">Do not confuse the Orch2_ continuation with the Orch2_ continuation ID.</span></span> <span data-ttu-id="3aa9d-279">代表接續識別碼的圖示會包含索引鍵 (![接續識別碼的圖示](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea"))，則代表接續的圖示不含索引鍵 （![接續的圖示](../core/media/test.gif "測試"))。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-279">The icon that represents a continuation ID contains a key (![icon for a continuation ID](../core/media/2d04a714-ade9-4e96-b89e-00002da75bea.gif "2d04a714-ade9-4e96-b89e-00002da75bea")), whereas the icon that represents a continuation does not contain a key (![icon for a continuation](../core/media/test.gif "test")).</span></span>  

48. <span data-ttu-id="3aa9d-280">在**選取連接埠**一節**選取連接埠** 對話方塊中，按一下  **BamEndToEnd_ReceivePort**，按一下 更-符號 ( **>**)，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-280">In the **Select Ports** section of the **Select Ports** dialog box, click **BamEndToEnd_ReceivePort**, click the greater-than sign (**>**), and then click **OK**.</span></span>  

49. <span data-ttu-id="3aa9d-281">儲存追蹤設定檔，以*\<範例路徑\>* \BAM\BamEndToEnd\BamEndToEnd.btt。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-281">Save the tracking profile to *\<Samples Path\>* \BAM\BamEndToEnd\BamEndToEnd.btt.</span></span>  

## <a name="important-details"></a><span data-ttu-id="3aa9d-282">重要的詳細資料</span><span class="sxs-lookup"><span data-stu-id="3aa9d-282">Important details</span></span>  
 <span data-ttu-id="3aa9d-283">追蹤設定檔不支援管線。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-283">Tracking profiles are not supported for pipelines.</span></span> <span data-ttu-id="3aa9d-284">不過，呼叫**BeginActivity**在管線元件是在協調流程中使用 ActivityID 相同。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-284">However, the call to **BeginActivity** in the pipeline component is the same as using ActivityID in an orchestration.</span></span> <span data-ttu-id="3aa9d-285">若要在呼叫**EnableContinuation**與協調流程中使用接續相同。</span><span class="sxs-lookup"><span data-stu-id="3aa9d-285">The call to **EnableContinuation** is the same as using a continuation in an orchestration.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3aa9d-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3aa9d-286">See Also</span></span>  
 [<span data-ttu-id="3aa9d-287">商務活動監控 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="3aa9d-287">Business Activity Monitoring (BizTalk Server Samples Folder)</span></span>](../core/business-activity-monitoring-biztalk-server-samples-folder.md)