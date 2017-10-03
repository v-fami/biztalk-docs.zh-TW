---
title: "OperationsSamples （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c9e3f3e-a570-4edd-aa2e-3f8e2e37c8a0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3e190d06c084a6b1b3c9965856897e0df94daab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operationssamples-biztalk-server-sample"></a><span data-ttu-id="3edc7-102">OperationsSamples (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="3edc7-102">OperationsSamples (BizTalk Server Sample)</span></span>
<span data-ttu-id="3edc7-103">OperationsSamples 範例示範如何利用 Operations 物件模型來執行操作活動。</span><span class="sxs-lookup"><span data-stu-id="3edc7-103">The OperationsSamples sample demonstrates how to perform operational activities using the Operations object model.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="3edc7-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="3edc7-104">What This Sample Does</span></span>  
 <span data-ttu-id="3edc7-105">這個範例示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="3edc7-105">This sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="3edc7-106">如何使用追蹤設定檔，在協調流程加上活動註解。</span><span class="sxs-lookup"><span data-stu-id="3edc7-106">How to use a tracking profile to comment an orchestration with activities.</span></span>  
  
-   <span data-ttu-id="3edc7-107">如何使用 BAM 追蹤資料庫尋找活動識別碼，並接著使用此識別碼尋找相關的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="3edc7-107">How to use the BAM tracking database to find an activity ID and then use the ID to find a related orchestration instance.</span></span>  
  
-   <span data-ttu-id="3edc7-108">如何尋找及使用訊息流程透過**MessageFlow**類別和其他作業物件模型類別和應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="3edc7-108">How to find and work with message flows by using the **MessageFlow** class and other Operations object model classes and APIs.</span></span>  
  
-   <span data-ttu-id="3edc7-109">如何存取連接埠、 訊息，以及其他執行個體所使用的類別衍生自**執行個體**類別。</span><span class="sxs-lookup"><span data-stu-id="3edc7-109">How to access ports, messages, and other instances by using classes derived from the **Instance** class.</span></span>  
  
 <span data-ttu-id="3edc7-110">此範例包含許多可用來支援上述作業的協助程式類別和方法。</span><span class="sxs-lookup"><span data-stu-id="3edc7-110">The sample contains many useful helper classes and methods to support the operations above.</span></span> <span data-ttu-id="3edc7-111">下節內容將討論這些範例程式碼和其他程式碼的重點。</span><span class="sxs-lookup"><span data-stu-id="3edc7-111">These and other code highlights are discussed in the next section.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="3edc7-112">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="3edc7-112">How This Sample Is Designed and Why</span></span>  
 <span data-ttu-id="3edc7-113">本範例是設計用來示範 Operations 物件模型中的幾個重要類別和方法，並會示範如何查詢公開的 BAM 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="3edc7-113">This sample is designed to demonstrate several of the key classes and methods in the Operations object model and to show how to query the publicly available BAM tracking database.</span></span>  
  
 <span data-ttu-id="3edc7-114">Operations 物件模型所包含的類別，可在 BizTalk Server 內操作訊息和其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="3edc7-114">The Operations object model contains classes that provide the ability to manipulate messages and other instances within BizTalk Server.</span></span>  
  
### <a name="using-a-bam-activity-id"></a><span data-ttu-id="3edc7-115">使用 BAM 活動識別碼</span><span class="sxs-lookup"><span data-stu-id="3edc7-115">Using a BAM Activity ID</span></span>  
 <span data-ttu-id="3edc7-116">本範例會示範如何與 BAM 互動，以及如何使用追蹤資料庫的公開檢視，以便透過使用商務資料來找出 MessageBox 中的即時訊息。</span><span class="sxs-lookup"><span data-stu-id="3edc7-116">This sample shows how to interact with BAM and how to use the publicly available views in the tracking database to locate a live message in the message box by using business data.</span></span> <span data-ttu-id="3edc7-117">此範例會擷取對應於訂單編號的協調流程識別碼，完成此作業。</span><span class="sxs-lookup"><span data-stu-id="3edc7-117">The sample does this by retrieving an orchestration ID corresponding to a purchase order number.</span></span> <span data-ttu-id="3edc7-118">為了成功完成這項工作，此範例必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3edc7-118">For this task to succeed, it must do the following:</span></span>  
  
1.  <span data-ttu-id="3edc7-119">使用商務資料 (訂單號碼) 尋找活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="3edc7-119">Use business data (a purchase order number) to find an activity ID.</span></span> <span data-ttu-id="3edc7-120">這個步驟會將商務資料對應到可用來尋找其他資訊的內部識別碼。</span><span class="sxs-lookup"><span data-stu-id="3edc7-120">This step maps business data to an internal ID that can be used to find additional information.</span></span>  
  
2.  <span data-ttu-id="3edc7-121">擷取與活動識別碼相關的 BAM 參考。</span><span class="sxs-lookup"><span data-stu-id="3edc7-121">Retrieve the BAM references related to the activity ID.</span></span>  
  
3.  <span data-ttu-id="3edc7-122">尋找類型為 "BizTalkService" 且參考至特定協調流程的參考。</span><span class="sxs-lookup"><span data-stu-id="3edc7-122">Find a reference that has a type of "BizTalkService" and refers to an orchestration.</span></span> <span data-ttu-id="3edc7-123">如果有找到符合的項目，便傳回其執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="3edc7-123">If one is found, return its instance ID.</span></span>  
  
 <span data-ttu-id="3edc7-124">這項功能由**BAMWebService.GetOrchestrationID**靜態方法和相關聯的 helper 方法，包括 BamManagementService.cs 原始程式檔中的類別和方法。</span><span class="sxs-lookup"><span data-stu-id="3edc7-124">This functionality is provided by the **BAMWebService.GetOrchestrationID** static method and associated helper methods including classes and methods in the BamManagementService.cs source file.</span></span>  
  
### <a name="suspending-terminating-and-resuming-an-instance"></a><span data-ttu-id="3edc7-125">擱置、終止與繼續執行個體</span><span class="sxs-lookup"><span data-stu-id="3edc7-125">Suspending, Terminating, and Resuming an Instance</span></span>  
 <span data-ttu-id="3edc7-126">範例程式中包含**Samples.OperateOnInstance**接受作業和執行個體的識別碼，並執行指定的作業的執行個體上的方法。</span><span class="sxs-lookup"><span data-stu-id="3edc7-126">The sample program includes a **Samples.OperateOnInstance** method that takes an operation and instance ID and performs the specified operation on the instance.</span></span> <span data-ttu-id="3edc7-127">有效的作業會由**InstanceOperation**列舉型別，並包含 Suspend、 Terminate 和 Resume。</span><span class="sxs-lookup"><span data-stu-id="3edc7-127">Valid operations are defined by the **InstanceOperation** enumeration and include Suspend, Terminate, and Resume.</span></span> <span data-ttu-id="3edc7-128">這些作業會直接對應到 BizTalkOperations 類別的方法-**SuspendInstance**， **TerminateInstance**，和**ResumeInstance**。</span><span class="sxs-lookup"><span data-stu-id="3edc7-128">These operations map directly to methods of the BizTalkOperations class—**SuspendInstance**, **TerminateInstance**, and **ResumeInstance**.</span></span>  
  
 <span data-ttu-id="3edc7-129">請注意，此方法會處理 ArgumentException 和 SqlException 等例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3edc7-129">Notice that the method handles both ArgumentException and SqlException exceptions.</span></span> <span data-ttu-id="3edc7-130">在使用 Operations 物件模型中的類別和方法時，您必須謹慎地預先考慮到包括 SqlException 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3edc7-130">You must be careful to anticipate exceptions—including SqlException—when working with the classes and methods in the Operations object model.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3edc7-131">許多 Operations 方法必須要存取該資料庫。</span><span class="sxs-lookup"><span data-stu-id="3edc7-131">Many of the Operations methods require access to the database.</span></span> <span data-ttu-id="3edc7-132">您應該預先考慮到這些方法所擲回的例外狀況，並適當進行處理。</span><span class="sxs-lookup"><span data-stu-id="3edc7-132">You should anticipate the exceptions thrown by these methods and handle them appropriately.</span></span>  
  
### <a name="retrieving-all-live-messages"></a><span data-ttu-id="3edc7-133">擷取所有即時訊息</span><span class="sxs-lookup"><span data-stu-id="3edc7-133">Retrieving All Live Messages</span></span>  
 <span data-ttu-id="3edc7-134">Operations 物件模型可以讓您直接逐一查看所有可用的即時訊息，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="3edc7-134">The Operations object model makes it straightforward to iterate over all of the available live messages, as shown in the following code fragment:</span></span>  
  
```  
BizTalkOperations _operations = new BizTalkOperations()  
IEnumerable messages = _operations.GetMessages();  
foreach (BizTalkMessage msg in messages)  
…  
```  
  
 <span data-ttu-id="3edc7-135">OperationsSamples 程式會進一步示範如何存取每個訊息的相關資訊，包括訊息識別碼、訊息類型，以及訊息部份的數目和類型。</span><span class="sxs-lookup"><span data-stu-id="3edc7-135">The OperationsSamples program takes this a step further by demonstrating how to access information about each message, including message ID and message type along with the number and types of message parts.</span></span> <span data-ttu-id="3edc7-136">您可以針對必須逐一查看 BizTalk Server 中的多數或全部即時訊息的情況，修改並使用此程式碼。</span><span class="sxs-lookup"><span data-stu-id="3edc7-136">You can modify this code and use it in scenarios where you have to iterate through many or all of the available live messages in BizTalk Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3edc7-137">可用的訊息數目可能是成千上百個。</span><span class="sxs-lookup"><span data-stu-id="3edc7-137">There may be hundreds or thousands of messages available.</span></span> <span data-ttu-id="3edc7-138">若是掃描整個清單，可能會對效能造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="3edc7-138">Scanning the entire list may adversely affect performance.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="3edc7-139">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="3edc7-139">Where to Find This Sample</span></span>  
 <span data-ttu-id="3edc7-140">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="3edc7-140">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="3edc7-141">\<*範例路徑*> \Admin\OperationsOM\OperationsSamples\\</span><span class="sxs-lookup"><span data-stu-id="3edc7-141">\<*Samples Path*>\Admin\OperationsOM\OperationsSamples\\</span></span>  
  
 <span data-ttu-id="3edc7-142">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="3edc7-142">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="3edc7-143">檔案</span><span class="sxs-lookup"><span data-stu-id="3edc7-143">File(s)</span></span>|<span data-ttu-id="3edc7-144">Description</span><span class="sxs-lookup"><span data-stu-id="3edc7-144">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3edc7-145">BamManagementService.cs</span><span class="sxs-lookup"><span data-stu-id="3edc7-145">BamManagementService.cs</span></span>|<span data-ttu-id="3edc7-146">BAM Web 服務的 Web Proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="3edc7-146">Web proxy class for the BAM Web service.</span></span>|  
|<span data-ttu-id="3edc7-147">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="3edc7-147">Cleanup.bat</span></span>|<span data-ttu-id="3edc7-148">移除範例協調流程，並將 HelloWorld 範例還原成原始狀態。</span><span class="sxs-lookup"><span data-stu-id="3edc7-148">Removes the sample orchestration and restores the HelloWorld sample to its original state.</span></span>|  
|<span data-ttu-id="3edc7-149">HelloOrchestration.btt</span><span class="sxs-lookup"><span data-stu-id="3edc7-149">HelloOrchestration.btt</span></span>|<span data-ttu-id="3edc7-150">用來將 BizTalk 事件來源對應到 BAM 目標活動的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="3edc7-150">Tracking profile used to map BizTalk event sources to BAM target activities.</span></span>|  
|<span data-ttu-id="3edc7-151">HelloOrchestration.xls</span><span class="sxs-lookup"><span data-stu-id="3edc7-151">HelloOrchestration.xls</span></span>|<span data-ttu-id="3edc7-152">BAM 定義樣式表。</span><span class="sxs-lookup"><span data-stu-id="3edc7-152">BAM definition style sheet.</span></span>|  
|<span data-ttu-id="3edc7-153">OperationsSamples.cs</span><span class="sxs-lookup"><span data-stu-id="3edc7-153">OperationsSamples.cs</span></span>|<span data-ttu-id="3edc7-154">C# 原始程式檔，其中包含示範 Operations 物件模型各方面的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3edc7-154">C# source file containing code that demonstrates various aspects of the Operations object model.</span></span>|  
|<span data-ttu-id="3edc7-155">OperationsSamples.csproj、OperationsSamples.sln、AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="3edc7-155">OperationsSamples.csproj, OperationsSamples.sln, AssemblyInfo.cs</span></span>|<span data-ttu-id="3edc7-156">此範例的專案、解決方案和組件資訊檔案。</span><span class="sxs-lookup"><span data-stu-id="3edc7-156">Project, solution, and assembly information files for this sample.</span></span>|  
|<span data-ttu-id="3edc7-157">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="3edc7-157">Setup.bat</span></span>|<span data-ttu-id="3edc7-158">這個檔案是用來建置及初始化這個範例，其方法是修改 HelloWorld 協調流程範例。</span><span class="sxs-lookup"><span data-stu-id="3edc7-158">Used to build and initialize this sample by modifying the HelloWorld orchestration sample.</span></span> <span data-ttu-id="3edc7-159">此檔案會安裝範例協調流程、部署 BAM 活動定義和追蹤設定檔編輯器檔案、設定連接埠，並將範例檔放在接收位置中。</span><span class="sxs-lookup"><span data-stu-id="3edc7-159">It installs a sample orchestration, deploys a BAM Activity Definition and a Tracking Profile Editor file, configures ports, and drops a sample file into the receive location.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="3edc7-160">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="3edc7-160">How to Use This Sample</span></span>  
 <span data-ttu-id="3edc7-161">使用此範例，瞭解 Operations 作業物件模型的可用功能。</span><span class="sxs-lookup"><span data-stu-id="3edc7-161">Use this sample to explore the functionality available in the Operations object model.</span></span> <span data-ttu-id="3edc7-162">修改現有常式尋找訊息，以便採取不同方式來使用訊息；或是加入新程式碼，以便複寫 [BizTalk Server 管理] 主控台中的 [群組中樞] 部分。</span><span class="sxs-lookup"><span data-stu-id="3edc7-162">Modify existing routines to find and work with messages differently or add new code that replicates portions of the Group Hub in the BizTalk Server Management console.</span></span>  
  
 <span data-ttu-id="3edc7-163">您也可以考慮執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3edc7-163">You may also consider some of the following tasks:</span></span>  
  
-   <span data-ttu-id="3edc7-164">撰寫應用程式，將最常使用的 [群組中樞] 子集複寫到自訂的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3edc7-164">Write an application that replicates the most-used subset of the Group Hub into a custom application.</span></span>  
  
-   <span data-ttu-id="3edc7-165">撰寫自訂的佈建應用程式，以便建立連接埠，並透過連接埠傳送測試訊息給新交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="3edc7-165">Write a custom provisioning application that creates ports and sends a test message through for new trading partners.</span></span>  
  
-   <span data-ttu-id="3edc7-166">將範例程式修改為命令列公用程式，以便在螢幕、XML 檔案或文字報告中提供單一訂單或各種訂單的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3edc7-166">Modify the sample program into a command-line utility that provides information about a single purchase order or a range of purchase orders to the screen, an XML file, or a text report.</span></span>  
  
## <a name="installing-sample-support-files"></a><span data-ttu-id="3edc7-167">安裝範例支援檔案</span><span class="sxs-lookup"><span data-stu-id="3edc7-167">Installing Sample Support Files</span></span>  
 <span data-ttu-id="3edc7-168">本節將引導您完成安裝及執行範例的必要程序。</span><span class="sxs-lookup"><span data-stu-id="3edc7-168">This section walks through the procedures required to install and run the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3edc7-169">安裝及執行此範例之前，您必須確定 BAM 已安裝且運作。</span><span class="sxs-lookup"><span data-stu-id="3edc7-169">Before installing and running this sample, you must verify that BAM has been installed and is functioning.</span></span> <span data-ttu-id="3edc7-170">若未安裝 BAM，此範例將無法執行。</span><span class="sxs-lookup"><span data-stu-id="3edc7-170">If BAM has not been installed, this sample will not work.</span></span>  
  
#### <a name="to-compile-and-install-the-support-files-for-this-sample"></a><span data-ttu-id="3edc7-171">若要編譯及安裝此範例的支援檔案</span><span class="sxs-lookup"><span data-stu-id="3edc7-171">To compile and install the support files for this sample</span></span>  
  
1.  <span data-ttu-id="3edc7-172">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3edc7-172">In a command window, navigate to the following folder:</span></span>  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
2.  <span data-ttu-id="3edc7-173">執行 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3edc7-173">Run Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="3edc7-174">建立傳送和接收目錄</span><span class="sxs-lookup"><span data-stu-id="3edc7-174">Creates send and receive directories</span></span>  
  
    -   <span data-ttu-id="3edc7-175">建立及啟動傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="3edc7-175">Creates and starts send and receive ports</span></span>  
  
    -   <span data-ttu-id="3edc7-176">編譯及部署 `<Samples Path>`\Orchestrations\HelloWorld 資料夾中的 HelloWorld 協調流程。</span><span class="sxs-lookup"><span data-stu-id="3edc7-176">Compiles and deploys the HelloWorld orchestration in the `<Samples Path>`\Orchestrations\HelloWorld folder.</span></span>  
  
    -   <span data-ttu-id="3edc7-177">修改 HelloWorld 協調流程的公開金鑰 Token</span><span class="sxs-lookup"><span data-stu-id="3edc7-177">Modifies the public key token for the HelloWorld orchestration</span></span>  
  
    -   <span data-ttu-id="3edc7-178">部署 BAM 活動定義和追蹤設定檔編輯器檔案</span><span class="sxs-lookup"><span data-stu-id="3edc7-178">Deploys the BAM Activity Definition and Tracking Profile Editor file</span></span>  
  
    -   <span data-ttu-id="3edc7-179">重新命名此 out 目錄</span><span class="sxs-lookup"><span data-stu-id="3edc7-179">Renames the out directory</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3edc7-180">若要中止安裝，請在第一個「請按任何一個鍵繼續」提示時按 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="3edc7-180">To abort the installation, press CTRL+C at the first "press any key to continue" prompt.</span></span> <span data-ttu-id="3edc7-181">這樣就可停止指令碼，並使 HelloWorld 範例保留在原始狀態。</span><span class="sxs-lookup"><span data-stu-id="3edc7-181">This stops the script and leaves the HelloWorld sample in its original state.</span></span> <span data-ttu-id="3edc7-182">若是在第二個 (也是最後一個) 提示中按 CTRL+C，並不會停止安裝。</span><span class="sxs-lookup"><span data-stu-id="3edc7-182">Pressing CTRL+C on the second and final prompt does not stop the installation.</span></span> <span data-ttu-id="3edc7-183">在此狀況下，請執行 Cleanup.bat 以解除安裝 OperationsOM 範例並還原 HelloWorld 範例。</span><span class="sxs-lookup"><span data-stu-id="3edc7-183">In this case, run Cleanup.bat to uninstall the OperationsOM sample and restore the HelloWorld sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="3edc7-184">執行此範例</span><span class="sxs-lookup"><span data-stu-id="3edc7-184">Running This Sample</span></span>  
 <span data-ttu-id="3edc7-185">使用下列程序執行 OperationsOM 範例。</span><span class="sxs-lookup"><span data-stu-id="3edc7-185">Use the following procedure to run the OperationsOM sample.</span></span>  
  
#### <a name="to-compile-and-run-the-sample"></a><span data-ttu-id="3edc7-186">若要編譯及執行範例</span><span class="sxs-lookup"><span data-stu-id="3edc7-186">To compile and run the sample</span></span>  
  
1.  <span data-ttu-id="3edc7-187">按一下**啟動**，選取**所有程式**，選取**Microsoft BizTalk Server**，然後選取**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="3edc7-187">Click **Start**, select **All Programs**, select **Microsoft BizTalk Server**, and then select **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="3edc7-188">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="3edc7-188">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="3edc7-189">以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="3edc7-189">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3edc7-190">如果在設定產品之後尚未重新啟動該主控件執行個體，這時您可能需要重新啟動 BizTalkServerApplication 主控件執行個體，以設定 BAM 正確的工作資料庫。</span><span class="sxs-lookup"><span data-stu-id="3edc7-190">Restarting the BizTalkServerApplication host instance may be necessary to set the correct working database for BAM if you have not restarted the host instance since configuring the product.</span></span>  
  
4.  <span data-ttu-id="3edc7-191">從 Windows 檔案總管瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="3edc7-191">From Windows Explorer, navigate to the following folder:</span></span>  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
5.  <span data-ttu-id="3edc7-192">按兩下**[operationsom.sln]**專案檔，將它載入[!INCLUDE[vs2010](../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3edc7-192">Double-click the **OperationsOM.sln** project file to load it into [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span></span>  
  
6.  <span data-ttu-id="3edc7-193">按 F5 執行範例。</span><span class="sxs-lookup"><span data-stu-id="3edc7-193">Press F5 to run the sample.</span></span>  
  
     <span data-ttu-id="3edc7-194">-或-</span><span class="sxs-lookup"><span data-stu-id="3edc7-194">-- OR --</span></span>  
  
     <span data-ttu-id="3edc7-195">在**建置**功能表上，按一下 **重建方案**。</span><span class="sxs-lookup"><span data-stu-id="3edc7-195">On the **Build** menu, click **Rebuild Solution**.</span></span> <span data-ttu-id="3edc7-196">當組建完成時，使用 Windows 檔案總管瀏覽至`<Samples Path>\Admin\OperationsOM\OperationSamples\bin\Debug,`，然後按兩下  **OperationsSamples.exe**。</span><span class="sxs-lookup"><span data-stu-id="3edc7-196">When the build is complete, use Windows Explorer to navigate to `<Samples Path>\Admin\OperationsOM\OperationSamples\bin\Debug,` and then double-click **OperationsSamples.exe**.</span></span>  
  
## <a name="classes-or-methods-used-in-this-sample"></a><span data-ttu-id="3edc7-197">在此範例中使用的類別或方法</span><span class="sxs-lookup"><span data-stu-id="3edc7-197">Classes or Methods Used in This Sample</span></span>  
 <span data-ttu-id="3edc7-198">[Microsoft.BizTalk.Operations.BizTalkOperations](http://msdn.microsoft.com/library/microsoft.biztalk.operations.biztalkoperations.aspx)&#124;[Microsoft.BizTalk.Operations.MessageFlow](http://msdn.microsoft.com/library/microsoft.biztalk.operations.messageflow.aspx)&#124;[Microsoft.BizTalk.Operations.SendPortInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.sendportinstance.aspx)&#124;[Microsoft.BizTalk.Operations.RoutingFailureInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.routingfailureinstance.aspx)&#124;[Microsoft.BizTalk.Operations.OrchestrationInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.orchestrationinstance.aspx)&#124;[Microsoft.BizTalk.Operations.MSMQtInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.msmqtinstance.aspx)&#124;[Microsoft.BizTalk.Operations.TrackedServiceInstance](http://msdn.microsoft.com/library/Microsoft.BizTalk.Operations.TrackedServiceInstance.aspx)</span><span class="sxs-lookup"><span data-stu-id="3edc7-198">[Microsoft.BizTalk.Operations.BizTalkOperations](http://msdn.microsoft.com/library/microsoft.biztalk.operations.biztalkoperations.aspx)&#124; [Microsoft.BizTalk.Operations.MessageFlow](http://msdn.microsoft.com/library/microsoft.biztalk.operations.messageflow.aspx)&#124; [Microsoft.BizTalk.Operations.SendPortInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.sendportinstance.aspx)&#124; [Microsoft.BizTalk.Operations.RoutingFailureInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.routingfailureinstance.aspx)&#124; [Microsoft.BizTalk.Operations.OrchestrationInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.orchestrationinstance.aspx)&#124; [Microsoft.BizTalk.Operations.MSMQtInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.msmqtinstance.aspx)&#124; [Microsoft.BizTalk.Operations.TrackedServiceInstance](http://msdn.microsoft.com/library/Microsoft.BizTalk.Operations.TrackedServiceInstance.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3edc7-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3edc7-199">See Also</span></span>  
 [<span data-ttu-id="3edc7-200">系統管理員 OperationsOM （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="3edc7-200">Admin-OperationsOM (BizTalk Server Samples Folder)</span></span>](../core/admin-operationsom-biztalk-server-samples-folder.md)