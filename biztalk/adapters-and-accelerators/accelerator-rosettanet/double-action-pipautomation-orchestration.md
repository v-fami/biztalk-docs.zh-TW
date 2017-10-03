---
title: "Double 動作 PIPAutomation 協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9159f7b1-cb83-41f1-8637-39c5ddcc63ae
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18c2fd1fc45823aed0c61981251523776f886dcb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="double-action-pipautomation-orchestration"></a><span data-ttu-id="ac602-102">Double 動作 PIPAutomation 協調流程</span><span class="sxs-lookup"><span data-stu-id="ac602-102">Double Action PIPAutomation Orchestration</span></span>
<span data-ttu-id="ac602-103">DoubleAction.odx 範例顯示如何實作協調流程，自動為雙向動作「夥伴介面程序 (PIP)」0C2、0C4、3A2 和 3A4 產生回應。</span><span class="sxs-lookup"><span data-stu-id="ac602-103">The DoubleAction.odx sample illustrates how to implement an orchestration to automatically generate responses for the double-action Partner Interface Processes (PIPs) 0C2, 0C4, 3A2, and 3A4.</span></span> <span data-ttu-id="ac602-104">您可以擴充此範例專案來支援其他的雙向動作 PIP。</span><span class="sxs-lookup"><span data-stu-id="ac602-104">You can extend this sample project to support additional double-action PIPs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac602-105">在範例資料夾中的對應是範例。</span><span class="sxs-lookup"><span data-stu-id="ac602-105">The maps provided in the sample folder are samples.</span></span> <span data-ttu-id="ac602-106">您必須根據特定的需求，對這些對應進行變更後，才能加以使用。</span><span class="sxs-lookup"><span data-stu-id="ac602-106">To use them, you must change them based on your specific requirements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac602-107">您應該擴充這個範例專案，使其僅支援雙向動作 PIP，而非單向動作 PIP。</span><span class="sxs-lookup"><span data-stu-id="ac602-107">You should extend this sample project to support double-action PIPs only, not single-action PIPs.</span></span> <span data-ttu-id="ac602-108">如果將它擴充為處理單向動作 PIP，這個協調流程將會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ac602-108">This orchestration will return an error if you extend it to process a single-action PIP.</span></span> <span data-ttu-id="ac602-109">若要確認這個協調流程將不會處理單向動作 PIP，請參閱下面的「篩選單向動作訊息」部分。</span><span class="sxs-lookup"><span data-stu-id="ac602-109">To ensure that this orchestration will not process single-action PIPs, see the Filtering Out Single-Action Messages section below.</span></span>  
  
 <span data-ttu-id="ac602-110">根據預設， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]安裝程式會安裝在此範例\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft 2013 BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction。</span><span class="sxs-lookup"><span data-stu-id="ac602-110">By default, the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Setup program installs this sample in \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft 2013 BizTalk Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction.</span></span>  
  
 <span data-ttu-id="ac602-111">這個範例專案包括：</span><span class="sxs-lookup"><span data-stu-id="ac602-111">This sample project includes:</span></span>  
  
-   <span data-ttu-id="ac602-112">預存程序 (`PipAutomationGetAction)`擷取新動作訊息，來為 Pip 0c2、 0c4、 3A2 和 3A4。</span><span class="sxs-lookup"><span data-stu-id="ac602-112">A stored procedure (`PipAutomationGetAction)` to retrieve new action messages for the PIPs 0C2, 0C4, 3A2, and 3A4.</span></span>  
  
-   <span data-ttu-id="ac602-113">繫結至 SQL 預存程序的接收位置 (MessagesToLOB_Receive_Location)。</span><span class="sxs-lookup"><span data-stu-id="ac602-113">A receive location (MessagesToLOB_Receive_Location) bound to the SQL stored procedure.</span></span>  
  
-   <span data-ttu-id="ac602-114">處理每個 PIP、根據每個 PIP 的對應產生適當的回應，以及將回應儲存在 BTARNDATA 資料庫之 MessagesFromLOB 資料表中的協調流程。</span><span class="sxs-lookup"><span data-stu-id="ac602-114">An orchestration (DoubleAction.odx) that processes each PIP, generates the appropriate response based on a map for each PIP, and saves the response in the MessagesFromLOB table of the BTARNDATA database.</span></span> <span data-ttu-id="ac602-115">協調流程會使用來自 Microsoft.Solutions.BTARN.Shared.dll 的 `RNIFSubmit` 方法來提交訊息。</span><span class="sxs-lookup"><span data-stu-id="ac602-115">The orchestration uses the `RNIFSubmit` method from Microsoft.Solutions.BTARN.Shared.dll to submit the message.</span></span>  
  
-   <span data-ttu-id="ac602-116">Setup.bat 檔用來建立 MessagesToLOB_Receive_Port (與 DoubleAction 協調流程搭配使用) 的繫結檔案 (DoubleActionBinding.xml)。</span><span class="sxs-lookup"><span data-stu-id="ac602-116">A binding file (DoubleActionBinding.xml) that the file Setup.bat uses to create the MessagesToLOB_Receive_Port for use with the DoubleAction orchestration.</span></span>  
  
-   <span data-ttu-id="ac602-117">用於建置及初始化範例的安裝程式檔案。</span><span class="sxs-lookup"><span data-stu-id="ac602-117">A setup file to build and initialize the sample.</span></span> <span data-ttu-id="ac602-118">如果您[!INCLUDE[bts2010R2](../../includes/bts2010r2-md.md)]安裝執行的 32 位元電腦上，執行 setup.bat 檔案\<磁碟機 >: \Program Files\Microsoft Microsoft 2013 BizTalk Accelerator for RosettaNet \SDK\PIPAutomation\DoubleAction 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac602-118">If your [!INCLUDE[bts2010R2](../../includes/bts2010r2-md.md)] installation is running on a 32-bit computer, run the file setup.bat in the \<drive>:\Program Files\Microsoft Microsoft 2013 BizTalk Accelerator for RosettaNet \SDK\PIPAutomation\DoubleAction folder.</span></span> <span data-ttu-id="ac602-119">如果您的 [!INCLUDE[bts2010R2](../../includes/bts2010r2-md.md)] 安裝是在 64 位元的電腦上執行，請執行相同資料夾中的 setupx64.bat。</span><span class="sxs-lookup"><span data-stu-id="ac602-119">If your [!INCLUDE[bts2010R2](../../includes/bts2010r2-md.md)] installation is running on a 64-bit computer, run setupx64.bat in the same folder.</span></span>  
  
 <span data-ttu-id="ac602-120">協調流程會使用 BTARNData 資料庫 (來源檔案是 DoubleAction 目錄中的 DoubleAction.sql 檔) 中的 PipAutomationGetAction 預存程序，接收訊息。</span><span class="sxs-lookup"><span data-stu-id="ac602-120">The orchestration receives messages using the PipAutomationGetAction stored procedure in the BTARNData database (the source file is DoubleAction.sql in the DoubleAction directory).</span></span> <span data-ttu-id="ac602-121">這個預存程序會接收來自 MessagesToLOB 資料表的訊息。</span><span class="sxs-lookup"><span data-stu-id="ac602-121">This stored procedure retrieves the messages from the MessagesToLOB table.</span></span>  
  
 <span data-ttu-id="ac602-122">若要擴充這個範例專案，使其支援其他的雙向動作 PIP，請在協調流程中，為該雙向動作 PIP 加入路徑。</span><span class="sxs-lookup"><span data-stu-id="ac602-122">To extend this sample project to support additional double-action PIPs, add a path in the orchestration for the double-action PIP.</span></span> <span data-ttu-id="ac602-123">這個路徑必須包含將把回應訊息建構為要求訊息的對應。</span><span class="sxs-lookup"><span data-stu-id="ac602-123">This path will include a map that will construct a respond message to a request message.</span></span> <span data-ttu-id="ac602-124">如需範例，請參閱 < [3A2 要求至 3A2 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md)和[3A4 要求至 3A4 回應的對應範例 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ac602-124">For example maps, see the [3A2 Request to 3A2 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md) and the [3A4 Request to 3A4 Response Map Sample &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md).</span></span>  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="ac602-125">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="ac602-125">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="ac602-126">在命令提示字元中，找出*\<磁碟機 >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for RosettaNet 2013 \SDK\PIPAutomation\DoubleAction 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac602-126">At a command prompt, locate the *\<drive>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for RosettaNet 2013 \SDK\PIPAutomation\DoubleAction folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac602-127">執行安裝程式前，在 [記事本] 中開啟 DoubleAction.sql 檔案 (在上述資料夾中)。</span><span class="sxs-lookup"><span data-stu-id="ac602-127">Before running the Setup program, open the file DoubleAction.sql (in the above folder) in Notepad.</span></span> <span data-ttu-id="ac602-128">在**檔案**功能表上，按一下 **存**。</span><span class="sxs-lookup"><span data-stu-id="ac602-128">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="ac602-129">在**編碼**清單中，選取**ANSI**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="ac602-129">In the **Encoding** list, select **ANSI**, and then click **Save**.</span></span> <span data-ttu-id="ac602-130">按一下**是**覆寫現有檔案。</span><span class="sxs-lookup"><span data-stu-id="ac602-130">Click **Yes** to overwrite the existing file.</span></span>  
  
2.  <span data-ttu-id="ac602-131">如果您[!INCLUDE[bts2010R2](../../includes/bts2010r2-md.md)]安裝執行的 32 位元電腦上，執行 setup.bat 檔案\<磁碟機 >: \Program Files\Microsoft BizTalk Accelerator for RosettaNet 2013 \SDK\PIPAutomation\DoubleAction 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac602-131">If your [!INCLUDE[bts2010R2](../../includes/bts2010r2-md.md)] installation is running on a 32-bit computer, run the file setup.bat in the \<drive>:\Program Files\Microsoft BizTalk Accelerator for RosettaNet 2013 \SDK\PIPAutomation\DoubleAction folder.</span></span> <span data-ttu-id="ac602-132">如果您的 BizTalk Server 2013 安裝是在 64 位元電腦上執行，請執行相同資料夾中的 setupx64.bat。</span><span class="sxs-lookup"><span data-stu-id="ac602-132">If your BizTalk Server 2013 installation is running on a 64-bit computer, run setupx64.bat in the same folder.</span></span> <span data-ttu-id="ac602-133">這個批次檔將會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac602-133">The batch file will perform the following actions:</span></span>  
  
    -   <span data-ttu-id="ac602-134">在 BTARNDATA 資料庫中建立 SQL 預存程序 (`PipAutomationGetAction`)，以便從 MessagesToLOB 資料表擷取動作訊息。</span><span class="sxs-lookup"><span data-stu-id="ac602-134">Creates a SQL stored procedure (`PipAutomationGetAction`) in the BTARNDATA database to retrieve the action message from the MessagesToLOB table.</span></span> <span data-ttu-id="ac602-135">這也能確保所擷取的記錄將不會再遭到讀取。</span><span class="sxs-lookup"><span data-stu-id="ac602-135">This also ensures that the retrieved records will not be read again.</span></span>  
  
    -   <span data-ttu-id="ac602-136">編譯 HeaderHelper [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 專案，並在全域組件快取中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="ac602-136">Compiles the HeaderHelper [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] project and registers the assembly in the global assembly cache.</span></span>  
  
    -   <span data-ttu-id="ac602-137">建立並繫結 BizTalk Server SQL 接收埠 (MessagesToLOB_Receive_Port)。</span><span class="sxs-lookup"><span data-stu-id="ac602-137">Creates and binds the BizTalk Server SQL receive port (MessagesToLOB_Receive_Port).</span></span>  
  
    -   <span data-ttu-id="ac602-138">啟用接收位置 (MessagesToLOB_Receive_Location)。</span><span class="sxs-lookup"><span data-stu-id="ac602-138">Enables the receive location (MessagesToLOB_Receive_Location).</span></span>  
  
    -   <span data-ttu-id="ac602-139">編譯及部署雙向動作 PIPAutomation 協調流程 (DoubleAction.odx)。</span><span class="sxs-lookup"><span data-stu-id="ac602-139">Compiles and deploys the Double-Action PIPAutomation Orchestration (DoubleAction.odx).</span></span>  
  
    -   <span data-ttu-id="ac602-140">繫結和啟動 BizTalk Server 協調流程。</span><span class="sxs-lookup"><span data-stu-id="ac602-140">Binds and starts the BizTalk Server orchestration.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="ac602-141">範例在編譯時會出現一些警告。</span><span class="sxs-lookup"><span data-stu-id="ac602-141">The sample displays some warnings while compiling.</span></span> <span data-ttu-id="ac602-142">您可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="ac602-142">You can ignore these warnings.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="ac602-143">此範例會使用預設主機名稱**BizTalkServerApplication**部署專案時。</span><span class="sxs-lookup"><span data-stu-id="ac602-143">The sample uses the default host name **BizTalkServerApplication** when deploying the project.</span></span> <span data-ttu-id="ac602-144">如果您想要不同的主控件下執行這個範例中，您必須編輯位於下 DoubleActionBinding.xml 的預設主機名稱\<SDK > \PIPAutomation\DoubleAction 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ac602-144">If you would like to run the sample under a different host, you will need to edit the default host names found in DoubleActionBinding.xml under \<SDK>\PIPAutomation\DoubleAction folder.</span></span>  
  
### <a name="to-run-the-double-action-pipautomation-sample"></a><span data-ttu-id="ac602-145">執行雙向動作 PIPAutomation 範例</span><span class="sxs-lookup"><span data-stu-id="ac602-145">To run the Double-Action PIPAutomation sample</span></span>  
  
1.  <span data-ttu-id="ac602-146">建立主要角色為啟動者的 3A4 協議。</span><span class="sxs-lookup"><span data-stu-id="ac602-146">Create a 3A4 agreement where the home role is an initiator.</span></span> <span data-ttu-id="ac602-147">將主要組織的 GBI 設為 123456789，並將夥伴組織的 GBI 設為 987654321。</span><span class="sxs-lookup"><span data-stu-id="ac602-147">Set the GBI for the home organization to 123456789, and set the GBI for the partner to 987654321.</span></span> <span data-ttu-id="ac602-148">這會讓您使用 SDK 的 SampleInstances 資料夾之 LOBApplication 資料夾底下提供的範例。</span><span class="sxs-lookup"><span data-stu-id="ac602-148">This lets you use the samples provided in the SampleInstances folder under the LOBApplication folder in the SDK.</span></span>  
  
2.  <span data-ttu-id="ac602-149">使用「回送」鏡像協議公用程式，為步驟 1 所建立的 3A4 PIP 建立鏡像。</span><span class="sxs-lookup"><span data-stu-id="ac602-149">Using the Loopback agreement-mirroring utility, create a mirror for the 3A4 PIP created in step 1.</span></span>  
  
3.  <span data-ttu-id="ac602-150">使用 LOBApplication.exe SDK 公用程式，提交「3A4 PIP 要求」訊息。</span><span class="sxs-lookup"><span data-stu-id="ac602-150">Using the LOBApplication.exe SDK utility, submit a 3A4 PIP Request message.</span></span> <span data-ttu-id="ac602-151">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 資料夾中包含了輸入的範例\<*安裝目錄*> \SDK\LOBApplication\SampleInstances\3A4_Request.xml。</span><span class="sxs-lookup"><span data-stu-id="ac602-151">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes an input sample in the folder \<*Installation Directory*>\SDK\LOBApplication\SampleInstances\3A4_Request.xml.</span></span>  
  
4.  <span data-ttu-id="ac602-152">在 [SQL Query Analyzer] 中，對 BTARNDATA 資料庫執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="ac602-152">IN SQL Query Analyzer, run the following query on the BTARNDATA database:</span></span>  
  
    ```  
    Select * from MessagesToLOB  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ac602-153">如果您使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServer2008](../../includes/btssqlserver2008-md.md)] R2/2008 SP1 中，使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] **Management Studio**執行 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="ac602-153">If you are using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServer2008](../../includes/btssqlserver2008-md.md)] R2/2008 SP1, use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] **Management Studio** to run the SQL query.</span></span>  
  
5.  <span data-ttu-id="ac602-154">經過數秒後，資料表中會出現四個訊息。</span><span class="sxs-lookup"><span data-stu-id="ac602-154">After several seconds, four new messages appear in this table.</span></span> <span data-ttu-id="ac602-155">其中兩個是確認信號。</span><span class="sxs-lookup"><span data-stu-id="ac602-155">Two of them are acknowledgment signals.</span></span> <span data-ttu-id="ac602-156">一個是「非同步 3A4 要求訊息」。</span><span class="sxs-lookup"><span data-stu-id="ac602-156">One signal is the Async 3A4 Request Message.</span></span> <span data-ttu-id="ac602-157">另一個則是「非同步 3A4 回應訊息」。</span><span class="sxs-lookup"><span data-stu-id="ac602-157">One signal is the Async 3A4 Response Message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac602-158">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="ac602-158">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="ac602-159">您必須先執行 Cleanup.bat，才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="ac602-159">You must run Cleanup.bat before running Setup.bat again.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac602-160">備註</span><span class="sxs-lookup"><span data-stu-id="ac602-160">Remarks</span></span>  
 <span data-ttu-id="ac602-161">公用協調流程會自動產生確認訊息 (ACK 和 NACK 信號訊息)。</span><span class="sxs-lookup"><span data-stu-id="ac602-161">The public orchestration automatically generates acknowledgments (ACK and NACK signal messages).</span></span> <span data-ttu-id="ac602-162">商務營運系統 (LOB) 應用程式則不需要產生這些訊息。</span><span class="sxs-lookup"><span data-stu-id="ac602-162">The line-of-business (LOB) application does not need to generate them.</span></span>  
  
 <span data-ttu-id="ac602-163">這種路由至 MessagesFromLOB 資料表的訊息格式，稱為 LOBMessage。</span><span class="sxs-lookup"><span data-stu-id="ac602-163">The format of the message that is routed to the MessagesFromLOB table is called LOBMessage.</span></span> <span data-ttu-id="ac602-164">結構描述位於 C:\Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for RosettaNet 2013 \SDK\RNIFSchemas\GlobalSchemas\LOBMessage.xsd。</span><span class="sxs-lookup"><span data-stu-id="ac602-164">The schema is available in C:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for RosettaNet 2013 \SDK\RNIFSchemas\GlobalSchemas\LOBMessage.xsd.</span></span> <span data-ttu-id="ac602-165">如果您使用 `RNIFSubmit` 方法，則不需要處理訊息格式。</span><span class="sxs-lookup"><span data-stu-id="ac602-165">If you use the `RNIFSubmit` method, you do not have to work with the message format.</span></span> <span data-ttu-id="ac602-166">您只需要提交具有其他資訊的 ServiceContent。</span><span class="sxs-lookup"><span data-stu-id="ac602-166">You only need to submit the ServiceContent with the additional information.</span></span> <span data-ttu-id="ac602-167">`RNIFSubmit` 會將記錄填入 MessagesFromLOB 資料表中。</span><span class="sxs-lookup"><span data-stu-id="ac602-167">`RNIFSubmit` populates the record in the MessagesFromLOB table.</span></span>  
  
## <a name="filtering-out-single-action-messages"></a><span data-ttu-id="ac602-168">篩選單向動作訊息</span><span class="sxs-lookup"><span data-stu-id="ac602-168">Filtering Out Single-Action Messages</span></span>  
 <span data-ttu-id="ac602-169">這個協調流程應該只會接收雙向動作訊息。</span><span class="sxs-lookup"><span data-stu-id="ac602-169">This orchestration should receive only double-action messages.</span></span> <span data-ttu-id="ac602-170">您不應該擴充此範例專案來支援單向動作 PIP。</span><span class="sxs-lookup"><span data-stu-id="ac602-170">You should not extend this sample project to support single-action PIPs.</span></span> <span data-ttu-id="ac602-171">如果您使用這個協調流程處理單向動作訊息，BTARN 將會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="ac602-171">BTARN will post errors if you use this orchestration to process single-action messages.</span></span> <span data-ttu-id="ac602-172">為了避免協調流程接收單向動作訊息，請變更下列 PIPAutomationGetAction 預存程序中的程式碼行：</span><span class="sxs-lookup"><span data-stu-id="ac602-172">In order to prevent the orchestration from receiving a single-action message, change the following line in the PIPAutomationGetAction stored procedure:</span></span>  
  
```  
SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion,ServiceContent FROM MessagesToLOB  
```  
  
 <span data-ttu-id="ac602-173">在上述程式碼行中，加入將會篩選出單向動作訊息的 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="ac602-173">To the above line, add a WHERE clause that will filter out single-action messages.</span></span> <span data-ttu-id="ac602-174">將所有您要處理的單向動作訊息包含在 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="ac602-174">Include in the WHERE clause all the single-action messages that you will be processing.</span></span> <span data-ttu-id="ac602-175">這個程式碼行看起來應該如下：</span><span class="sxs-lookup"><span data-stu-id="ac602-175">The line should be as follows:</span></span>  
  
```  
SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion,ServiceContent FROM MessagesToLOB WHERE PIPCode NOT IN ( '0A1', '3B2', '3C3', '0C1', '0C3' )  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac602-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac602-176">See Also</span></span>  
 <span data-ttu-id="ac602-177">[3A2 要求至 3A2 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md) </span><span class="sxs-lookup"><span data-stu-id="ac602-177">[3A2 Request to 3A2 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a2-request-to-3a2-response-map-sample.md) </span></span>  
 <span data-ttu-id="ac602-178">[3A4 要求至 3A4 回應的對應範例](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md) </span><span class="sxs-lookup"><span data-stu-id="ac602-178">[3A4 Request to 3A4 Response Map Sample](../../adapters-and-accelerators/accelerator-rosettanet/3a4-request-to-3a4-response-map-sample.md) </span></span>  
 [<span data-ttu-id="ac602-179">協調流程範例</span><span class="sxs-lookup"><span data-stu-id="ac602-179">Orchestration Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)