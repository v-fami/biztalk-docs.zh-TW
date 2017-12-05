---
title: "錯誤處理 （BizTalk Server 範例資料夾） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, errors
- errors, examples
- examples, messages
- messages, examples
- messages, errors
ms.assetid: b39791ed-277b-4625-b9a9-72480a1b6ff6
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 386e9729ac32cb08863e2ac3e0699ecda7890dbc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="error-handling-biztalk-server-samples-folder"></a><span data-ttu-id="38ace-102">錯誤處理 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="38ace-102">Error Handling (BizTalk Server Samples Folder)</span></span>
<span data-ttu-id="38ace-103">此範例的目的是要建立「根據訊息內容決定路由」(CBR) 應用程式的錯誤處理功能。</span><span class="sxs-lookup"><span data-stu-id="38ace-103">The purpose of this sample is to build an error-handling functionality for the content-based routing (CBR) application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="38ace-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="38ace-104">Prerequisites</span></span>  
 <span data-ttu-id="38ace-105">若要執行範例時，建議您將 Microsoft Office InfoPath 2010 或更新版本安裝。</span><span class="sxs-lookup"><span data-stu-id="38ace-105">To run the sample, it is recommended that you have Microsoft Office InfoPath 2010 or later installed.</span></span> <span data-ttu-id="38ace-106">若不使用 InfoPath，也可以執行範例，但是在此情況下，則無法透過 HTTP 配接器檢視經費支出報表或提交經費支出報表。</span><span class="sxs-lookup"><span data-stu-id="38ace-106">You can run the sample without using InfoPath, but in that case you cannot see the expense reports and the submission of expense reports through the HTTP adapter.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="38ace-107">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="38ace-107">What This Sample Does</span></span>  
 <span data-ttu-id="38ace-108">此範例會實作經費支出報表處理系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="38ace-108">The sample implements part of an expense report processing system.</span></span> <span data-ttu-id="38ace-109">具體來說，本範例執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="38ace-109">Specifically, this sample does the following:</span></span>  
  
1.  <span data-ttu-id="38ace-110">定義經費支出報表結構描述，其中包含經費支出報表和內含部門名稱的個別傳送者相關資訊。</span><span class="sxs-lookup"><span data-stu-id="38ace-110">Defines an expense report schema containing information about an expense report and the individual submitter including department name.</span></span>  
  
2.  <span data-ttu-id="38ace-111">提供透過目錄或使用 InfoPath 的 Web 服務提交經費支出報表的功能。</span><span class="sxs-lookup"><span data-stu-id="38ace-111">Provides for the submission of the expense report through a directory or through a Web service using InfoPath.</span></span>  
  
3.  <span data-ttu-id="38ace-112">升級**部門**和**correlationID**訊息中的屬性文件，以便可以在連接埠篩選器中用來控制路由。</span><span class="sxs-lookup"><span data-stu-id="38ace-112">Promotes the **Department** and **correlationID** properties in the message document so that it can be used in a port filter to control routing.</span></span>  
  
4.  <span data-ttu-id="38ace-113">將屬於行銷部門的經費支出報表路由傳送至目錄中的檔案，模擬部門的後端系統傳遞作業。</span><span class="sxs-lookup"><span data-stu-id="38ace-113">Routes expense reports belonging to the Marketing department to a file in a directory, simulating delivery to the department's back-end system.</span></span>  
  
5.  <span data-ttu-id="38ace-114">針對非行銷部門的經費支出報表，產生失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="38ace-114">Generates a failed message for expense reports belonging to departments other than Marketing.</span></span> <span data-ttu-id="38ace-115">失敗的訊息包含錯誤資訊，包括錯誤碼和錯誤描述。</span><span class="sxs-lookup"><span data-stu-id="38ace-115">The failed message includes information about the error including error code and error description.</span></span>  
  
6.  <span data-ttu-id="38ace-116">將失敗的訊息路由傳送至收件人 (商務使用者或應用程式操作人員) 來更正並重新提交。</span><span class="sxs-lookup"><span data-stu-id="38ace-116">Routes failed messages to a human recipient (a business user or application operator) for correction and resubmission.</span></span>  
  
7.  <span data-ttu-id="38ace-117">根據上述部門，路由傳送重新提交的經費支出報表。</span><span class="sxs-lookup"><span data-stu-id="38ace-117">Routes resubmitted expense reports based on department as described above.</span></span>  
  
 <span data-ttu-id="38ace-118">這項工作的大部分是透過 BizTalk 協調流程排程所完成。</span><span class="sxs-lookup"><span data-stu-id="38ace-118">Much of this work is done through a BizTalk orchestration schedule.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="38ace-119">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="38ace-119">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="38ace-120">其設計依賴 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的預設傳送和接收 XML 管線、屬性升級、訂閱篩選條件和協調流程排程來路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="38ace-120">The design relies on the default send and receive XML pipelines, property promotion, subscription filters, and orchestration schedules within [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to route messages.</span></span> <span data-ttu-id="38ace-121">下表列出設計元素及其理由。</span><span class="sxs-lookup"><span data-stu-id="38ace-121">Design elements and their justification are listed in the following table.</span></span>  
  
|<span data-ttu-id="38ace-122">設計元素</span><span class="sxs-lookup"><span data-stu-id="38ace-122">Design element</span></span>|<span data-ttu-id="38ace-123">已選取的原因</span><span class="sxs-lookup"><span data-stu-id="38ace-123">Reason(s) selected</span></span>|  
|--------------------|--------------------------|  
|<span data-ttu-id="38ace-124">預設 XML 接收管線</span><span class="sxs-lookup"><span data-stu-id="38ace-124">Default XML receive pipeline</span></span>|<span data-ttu-id="38ace-125">-XMLReceive 管線支援屬性升級;PassThruReceive 管線則否。</span><span class="sxs-lookup"><span data-stu-id="38ace-125">-   The XMLReceive pipeline supports property promotion; the PassThruReceive pipeline does not.</span></span><br /><span data-ttu-id="38ace-126">-輸入的訊息已經是 XML 格式，而且不需要基本解譯和合作對象解析之外的處理。</span><span class="sxs-lookup"><span data-stu-id="38ace-126">-   The inbound message is already in XML format and does not require processing beyond basic disassembly and party resolution.</span></span>|  
|<span data-ttu-id="38ace-127">失敗訊息的路由</span><span class="sxs-lookup"><span data-stu-id="38ace-127">Routing for failed messages</span></span>|<span data-ttu-id="38ace-128">接收連接埠擱置失敗的訊息，並產生負值通知預設。</span><span class="sxs-lookup"><span data-stu-id="38ace-128">-   Receive ports suspend failed messages and generate a negative acknowledgment by default.</span></span> <span data-ttu-id="38ace-129">啟用路由時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會嘗試將處理失敗的訊息路由傳送至訂閱應用程式 (例如其他接收埠或協調流程排程)。</span><span class="sxs-lookup"><span data-stu-id="38ace-129">When routing is enabled [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attempts to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule).</span></span>|  
|<span data-ttu-id="38ace-130">屬性升級</span><span class="sxs-lookup"><span data-stu-id="38ace-130">Property promotion</span></span>|<span data-ttu-id="38ace-131">BizTalk Server 取決於屬性欄位來進行路由。</span><span class="sxs-lookup"><span data-stu-id="38ace-131">-   BizTalk Server depends upon property fields to do routing.</span></span> <span data-ttu-id="38ace-132">辨別欄位可用於協調流程，不能用於路由。</span><span class="sxs-lookup"><span data-stu-id="38ace-132">Distinguished fields are used by orchestrations and cannot be used for routing.</span></span>|  
|<span data-ttu-id="38ace-133">訂閱篩選器</span><span class="sxs-lookup"><span data-stu-id="38ace-133">Subscription filter</span></span>|<span data-ttu-id="38ace-134">-訂用帳戶篩選會執行擷取符合根據屬性欄位的一或多個準則的訊息路由。</span><span class="sxs-lookup"><span data-stu-id="38ace-134">-   The subscription filter performs the routing by capturing messages that meet one or more criteria based on property fields.</span></span>|  
|<span data-ttu-id="38ace-135">BizTalk 協調流程排程</span><span class="sxs-lookup"><span data-stu-id="38ace-135">BizTalk orchestration schedule</span></span>|<span data-ttu-id="38ace-136">-提供機會將資訊加入失敗訊息。</span><span class="sxs-lookup"><span data-stu-id="38ace-136">-   Provides the opportunity to add information to failed messages.</span></span><br /><span data-ttu-id="38ace-137">-啟用路由傳送至專屬位置，讓人為介入的失敗訊息。</span><span class="sxs-lookup"><span data-stu-id="38ace-137">-   Enables routing of failed messages to a dedicated location for human intervention.</span></span><br /><span data-ttu-id="38ace-138">-處理重新提交的經費支出報表。</span><span class="sxs-lookup"><span data-stu-id="38ace-138">-   Processes resubmitted expense reports.</span></span>|  
|<span data-ttu-id="38ace-139">XMLTransmit</span><span class="sxs-lookup"><span data-stu-id="38ace-139">XMLTransmit</span></span>|<span data-ttu-id="38ace-140">-執行外寄 XML 訊息的基本組件。</span><span class="sxs-lookup"><span data-stu-id="38ace-140">-   Performs basic assembly of outgoing XML messages.</span></span> <span data-ttu-id="38ace-141">PassThruTransmit 管線不會提供其他支援。</span><span class="sxs-lookup"><span data-stu-id="38ace-141">The PassThruTransmit pipeline provides no additional support.</span></span>|  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="38ace-142">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="38ace-142">Where to Find This Sample</span></span>  
 <span data-ttu-id="38ace-143">此範例位於 <`Samples Path>`\Messaging\ErrorHandling\\。</span><span class="sxs-lookup"><span data-stu-id="38ace-143">This sample is located at <`Samples Path>`\Messaging\ErrorHandling\\.</span></span>  
  
 <span data-ttu-id="38ace-144">下表包含此範例的檔案清單。</span><span class="sxs-lookup"><span data-stu-id="38ace-144">The following table contains a list of files for this sample.</span></span>  
  
|<span data-ttu-id="38ace-145">檔案</span><span class="sxs-lookup"><span data-stu-id="38ace-145">File</span></span>|<span data-ttu-id="38ace-146">Description</span><span class="sxs-lookup"><span data-stu-id="38ace-146">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="38ace-147">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="38ace-147">Cleanup.bat</span></span>|<span data-ttu-id="38ace-148">用來解除部署組件，以及將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="38ace-148">Used to undeploy assemblies and remove them from the global assembly cache.</span></span><br /><br /> <span data-ttu-id="38ace-149">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="38ace-149">Removes send and receive ports.</span></span><br /><br /> <span data-ttu-id="38ace-150">視需要移除 Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="38ace-150">Removes Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="38ace-151">ErrorHandling.sln</span><span class="sxs-lookup"><span data-stu-id="38ace-151">ErrorHandling.sln</span></span>|<span data-ttu-id="38ace-152">此範例的 Visual Studio 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="38ace-152">Visual Studio solution file for the sample.</span></span>|  
|<span data-ttu-id="38ace-153">ErrorHandlingBinding.xml</span><span class="sxs-lookup"><span data-stu-id="38ace-153">ErrorHandlingBinding.xml</span></span>|<span data-ttu-id="38ace-154">此範例的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="38ace-154">Binding file for the sample.</span></span>|  
|<span data-ttu-id="38ace-155">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="38ace-155">Setup.bat</span></span>|<span data-ttu-id="38ace-156">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="38ace-156">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="38ace-157">Expense Report – John Doe.xml</span><span class="sxs-lookup"><span data-stu-id="38ace-157">Expense Report – John Doe.xml</span></span>|<span data-ttu-id="38ace-158">範例經費支出報表 InfoPath 文件。</span><span class="sxs-lookup"><span data-stu-id="38ace-158">Example expense report InfoPath document.</span></span>|  
|<span data-ttu-id="38ace-159">Invalid Expense Report – John Doe.xml</span><span class="sxs-lookup"><span data-stu-id="38ace-159">Invalid Expense Report – John Doe.xml</span></span>|<span data-ttu-id="38ace-160">內含無效資料的範例經費支出報表 InfoPath 文件。</span><span class="sxs-lookup"><span data-stu-id="38ace-160">Example expense report InfoPath document with invalid data in it.</span></span>|  
|<span data-ttu-id="38ace-161">在 ErrorHandler 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="38ace-161">In ErrorHandler folder:</span></span><br /><br /> <span data-ttu-id="38ace-162">ErrorHandler.btproj</span><span class="sxs-lookup"><span data-stu-id="38ace-162">ErrorHandler.btproj</span></span>|<span data-ttu-id="38ace-163">協調流程所使用的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="38ace-163">BizTalk project for orchestration.</span></span>|  
|<span data-ttu-id="38ace-164">在 ErrorHandler 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="38ace-164">In ErrorHandler folder:</span></span><br /><br /> <span data-ttu-id="38ace-165">ResubmitLogic.odx</span><span class="sxs-lookup"><span data-stu-id="38ace-165">ResubmitLogic.odx</span></span>|<span data-ttu-id="38ace-166">訂閱失敗訊息的協調流程會將失敗訊息傳送至收件人來更正，然後重新提交已更正的訊息至伺服器來路由。</span><span class="sxs-lookup"><span data-stu-id="38ace-166">Orchestration that subscribes to failed messages, sends them to the human recipient for correction, and then resubmits corrected messages back into the server for routing.</span></span>|  
|<span data-ttu-id="38ace-167">在 ErrorHandler 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="38ace-167">In ErrorHandler folder:</span></span><br /><br /> <span data-ttu-id="38ace-168">SuspendMessage.odx</span><span class="sxs-lookup"><span data-stu-id="38ace-168">SuspendMessage.odx</span></span>|<span data-ttu-id="38ace-169">協調流程，用於擱置無法在錯誤處理協調流程內處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="38ace-169">Orchestration used for suspending messages that cannot be processed within the error-handling orchestration.</span></span>|  
|<span data-ttu-id="38ace-170">在 InfoPathForms 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="38ace-170">In InfoPathForms folder:</span></span><br /><br /> <span data-ttu-id="38ace-171">Expense Report.xsn</span><span class="sxs-lookup"><span data-stu-id="38ace-171">Expense Report.xsn</span></span><br /><br /> <span data-ttu-id="38ace-172">Expense Report - Resubmit.xsn</span><span class="sxs-lookup"><span data-stu-id="38ace-172">Expense Report - Resubmit.xsn</span></span>|<span data-ttu-id="38ace-173">經費支出報表 InfoPath 表單，以及用於檢視和重新提交失敗訊息的表單。</span><span class="sxs-lookup"><span data-stu-id="38ace-173">Expense report InfoPath form and form used for viewing and resubmitting failed messages.</span></span>|  
|<span data-ttu-id="38ace-174">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="38ace-174">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="38ace-175">ExpenseReportSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="38ace-175">ExpenseReportSchema.xsd</span></span>|<span data-ttu-id="38ace-176">經費支出報表文件的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="38ace-176">XML schema for the expense report document.</span></span>|  
|<span data-ttu-id="38ace-177">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="38ace-177">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="38ace-178">PipelinesAndSchemas.btproj</span><span class="sxs-lookup"><span data-stu-id="38ace-178">PipelinesAndSchemas.btproj</span></span>|<span data-ttu-id="38ace-179">此範例所使用的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="38ace-179">BizTalk project for the sample.</span></span>|  
|<span data-ttu-id="38ace-180">在 PipelinesAndSchemas 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="38ace-180">In PipelinesAndSchemas folder:</span></span><br /><br /> <span data-ttu-id="38ace-181">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="38ace-181">PropertySchema.xsd</span></span>|<span data-ttu-id="38ace-182">此範例的屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="38ace-182">Property schema for the sample.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="38ace-183">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="38ace-183">How to Use This Sample</span></span>  
 <span data-ttu-id="38ace-184">以此範例做為起點，可讓您建立專屬錯誤處理程序。</span><span class="sxs-lookup"><span data-stu-id="38ace-184">This sample provides a starting point for creating your own error handling procedure.</span></span>  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="38ace-185">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="38ace-185">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-compose-sample"></a><span data-ttu-id="38ace-186">若要建置及初始化「編輯」範例</span><span class="sxs-lookup"><span data-stu-id="38ace-186">To build and initialize the Compose sample</span></span>  
  
1.  <span data-ttu-id="38ace-187">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="38ace-187">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="38ace-188"><`Samples Path`>**\Messaging\ErrorHandling**</span><span class="sxs-lookup"><span data-stu-id="38ace-188"><`Samples Path`>**\Messaging\ErrorHandling**</span></span>  
  
2.  <span data-ttu-id="38ace-189">執行**Setup.bat**，它會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="38ace-189">Run **Setup.bat**, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="38ace-190">建立三個資料夾： **ExpenseReportIn**， **ExpenseReportOut**，和**ResubmittedReportIn**下列路徑底下：</span><span class="sxs-lookup"><span data-stu-id="38ace-190">Creates three folders: **ExpenseReportIn**, **ExpenseReportOut**, and **ResubmittedReportIn** under the following path:</span></span>  
  
         <span data-ttu-id="38ace-191"><`Samples Path`>**\Messaging\ErrorHandling**</span><span class="sxs-lookup"><span data-stu-id="38ace-191"><`Samples Path`>**\Messaging\ErrorHandling**</span></span>  
  
    -   <span data-ttu-id="38ace-192">複製並發行 InfoPath 表單**Expense Report.xsn**和**Expense Report – Resubmit.xsn**到資料夾**C:\Temp\InfoPathForms**。</span><span class="sxs-lookup"><span data-stu-id="38ace-192">Copies and publishes the InfoPath forms **Expense Report.xsn** and **Expense Report – Resubmit.xsn** into the folder **C:\Temp\InfoPathForms**.</span></span>  
  
    -   <span data-ttu-id="38ace-193">為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="38ace-193">Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample.</span></span>  
  
    -   <span data-ttu-id="38ace-194">建立虛擬目錄稱為**ExpenseReports**。</span><span class="sxs-lookup"><span data-stu-id="38ace-194">Creates a virtual directory called **ExpenseReports**.</span></span>  
  
    -   <span data-ttu-id="38ace-195">建立新的 BizTalk 應用程式呼叫**Error Handling Sample**和部署範例組件。</span><span class="sxs-lookup"><span data-stu-id="38ace-195">Creates a new BizTalk application called **Error Handling Sample** and deploys the sample assemblies into it.</span></span>  
  
    -   <span data-ttu-id="38ace-196">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="38ace-196">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive locations, and the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="38ace-197">登錄和啟動協調流程，啟用接收位置，並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="38ace-197">Enlists and starts orchestrations, enables the receive locations, and starts the send ports.</span></span>  
  
         <span data-ttu-id="38ace-198">如果您選擇不執行 Setup.bat 就開啟和建置此範例中的專案，則必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="38ace-198">If you choose to open and build the projects in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="38ace-199">您可以使用此金鑰組簽署範例組件。</span><span class="sxs-lookup"><span data-stu-id="38ace-199">Use this key pair to sign the sample assemblies.</span></span>  
  
3.  <span data-ttu-id="38ace-200">在嘗試執行此範例之前，請確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置或初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="38ace-200">Before attempting to run this sample, confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build or initialization process.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38ace-201">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="38ace-201">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="38ace-202">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="38ace-202">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
4.  <span data-ttu-id="38ace-203">若是使用 Internet Information Services (IIS) 7.0，您必須執行額外的設定步驟，針對此範例所使用之 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收位置的對應虛擬目錄來調整設定。</span><span class="sxs-lookup"><span data-stu-id="38ace-203">If you are using Internet Information Services (IIS) 7.0, you need to perform additional configuration steps to adjust the setting for the virtual directory that corresponds to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP receive location used by the sample.</span></span> <span data-ttu-id="38ace-204">請執行下列動作來設定 IIS：</span><span class="sxs-lookup"><span data-stu-id="38ace-204">Configure IIS by doing the following:</span></span>  
  
    1.  <span data-ttu-id="38ace-205">使用 [IIS 7.0 管理員]，建立「BizTalk 外掛式主控件使用者」群組的新應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="38ace-205">Using IIS 7.0 Manager, create a new application pool for the BizTalk Isolated Host Users group.</span></span>  
  
    2.  <span data-ttu-id="38ace-206">將應用程式集區設定為以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 外掛式主控件」使用者的身分執行</span><span class="sxs-lookup"><span data-stu-id="38ace-206">Configure the application pool to run under the identity of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Isolated Host user.</span></span> <span data-ttu-id="38ace-207">(如果您已經為其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收位置設定應用程式集區，可以略過這個步驟)。</span><span class="sxs-lookup"><span data-stu-id="38ace-207">(You may skip this step if you already have an application pool configured for other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP receive locations.)</span></span>  
  
    3.  <span data-ttu-id="38ace-208">設定虛擬目錄**ExpenseReport**若要使用 HTTP 接收先前步驟中建立的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="38ace-208">Configure the virtual directory **ExpenseReport** to use the HTTP receive application pool created in the previous step.</span></span>  
  
     <span data-ttu-id="38ace-209">如果您還沒有 BTSHTTPReceive.dll ISAPI 延伸模組的網頁伺服器延伸，請建立並將它的狀態設定為「允許」來啟用它。</span><span class="sxs-lookup"><span data-stu-id="38ace-209">If you do not already have a Web server extension for the BTSHTTPReceive.dll ISAPI extension, create and enable it by setting its status to "Allowed".</span></span> <span data-ttu-id="38ace-210">您可以在 IIS 7.0 中使用 IIS 管理主控台 (請直接在**系統管理工具**或透過電腦管理主控台)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="38ace-210">You can do this in IIS 7.0 by using the IIS Management console (either directly under **Administrative Tools** or through the Computer Management console) as follows:</span></span>  
  
    1.  <span data-ttu-id="38ace-211">展開**Internet Information Services 管理員**樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="38ace-211">Expand the **Internet Information Services Manager** tree.</span></span>  
  
    2.  <span data-ttu-id="38ace-212">按一下**網頁服務延伸**資料夾。</span><span class="sxs-lookup"><span data-stu-id="38ace-212">Click the **Web Service Extensions** folder.</span></span>  
  
    3.  <span data-ttu-id="38ace-213">在 [管理] 主控台的右窗格中，按一下**新增 Web 服務延伸**。</span><span class="sxs-lookup"><span data-stu-id="38ace-213">In the right pane of the management console, click **Add a new Web Service extension**.</span></span>  
  
    4.  <span data-ttu-id="38ace-214">在**新增網頁服務延伸**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="38ace-214">In the **New Web Service Extension** dialog box, click **Add**.</span></span>  
  
    5.  <span data-ttu-id="38ace-215">在**Add file**對話方塊中，按一下 **瀏覽**以選取的檔案 <`BizTalkInstallPath>`**\HttpReceive\BTSHTTPReceive.dll**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="38ace-215">In the **Add file** dialog box, click **Browse** to select the file <`BizTalkInstallPath>`**\HttpReceive\BTSHTTPReceive.dll**, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="38ace-216">設定虛擬目錄**ExpenseReport**為使用本機路徑[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HTTPReceive</span><span class="sxs-lookup"><span data-stu-id="38ace-216">Configure the virtual directory **ExpenseReport** to use local path [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HTTPReceive</span></span>  
  
     <span data-ttu-id="38ace-217">如需詳細資訊，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="38ace-217">For more information, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="38ace-218">執行範例</span><span class="sxs-lookup"><span data-stu-id="38ace-218">Running the Sample</span></span>  
 <span data-ttu-id="38ace-219">使用正確經費支出報表執行範例之前，請依照下列程序確認「沒有錯誤」案例的範例會正確執行。</span><span class="sxs-lookup"><span data-stu-id="38ace-219">Before running the sample with the correct expense report, use the following procedure to verify that the "no errors" case sample works correctly.</span></span>  
  
#### <a name="to-verify-that-the-no-errors-case-sample-works-correctly"></a><span data-ttu-id="38ace-220">若要確認沒有錯誤案例的範例會正確執行</span><span class="sxs-lookup"><span data-stu-id="38ace-220">To verify that the "no errors" case sample works correctly</span></span>  
  
1.  <span data-ttu-id="38ace-221">開啟 InfoPath 表單**Expense Report-John Doe.xml**。</span><span class="sxs-lookup"><span data-stu-id="38ace-221">Open the InfoPath form **Expense Report - John Doe.xml**.</span></span> <span data-ttu-id="38ace-222">查看**部門**欄位中的表單。</span><span class="sxs-lookup"><span data-stu-id="38ace-222">Look at the **Department** field within the form.</span></span> <span data-ttu-id="38ace-223">這個欄位應該設定為 [Marketing]。</span><span class="sxs-lookup"><span data-stu-id="38ace-223">This field should be set to "Marketing".</span></span>  
  
2.  <span data-ttu-id="38ace-224">在 InfoPath 視窗左上角，按一下**送出**或按一下**重新提交經費支出報表**。</span><span class="sxs-lookup"><span data-stu-id="38ace-224">In the upper-left corner of the InfoPath window, click **Submit** or click **Resubmit Expense Report**.</span></span> <span data-ttu-id="38ace-225">等候確認視窗表示經費支出報表已成功重新提交。</span><span class="sxs-lookup"><span data-stu-id="38ace-225">Wait for a confirmation window that says the expense report was successfully submitted.</span></span>  
  
     <span data-ttu-id="38ace-226">-或-</span><span class="sxs-lookup"><span data-stu-id="38ace-226">-OR-</span></span>  
  
     <span data-ttu-id="38ace-227">複製並貼到這個檔案**ExpenseReportIn**資料夾。</span><span class="sxs-lookup"><span data-stu-id="38ace-227">Copy and paste this file into the **ExpenseReportIn** folder.</span></span>  
  
3.  <span data-ttu-id="38ace-228">您應該會看到新的檔案放入**ExpenseReportOut**資料夾。</span><span class="sxs-lookup"><span data-stu-id="38ace-228">You should see a new file dropped into the **ExpenseReportOut** folder.</span></span> <span data-ttu-id="38ace-229">這個檔案是上面步驟中所提交的相同經費支出報表。</span><span class="sxs-lookup"><span data-stu-id="38ace-229">This file is the same expense report form that was submitted during previous steps.</span></span>  
  
 <span data-ttu-id="38ace-230">確認「沒有錯誤」案例之後，請依照下列程序使用不正確的經費支出報表執行範例，以觸發錯誤處理功能。</span><span class="sxs-lookup"><span data-stu-id="38ace-230">After you confirm the "no errors" case, use the following procedure to run the sample with an incorrect expense report to trigger error-handling functionality.</span></span>  
  
#### <a name="to-trigger-error-handling"></a><span data-ttu-id="38ace-231">若要觸發錯誤處理</span><span class="sxs-lookup"><span data-stu-id="38ace-231">To trigger error handling</span></span>  
  
1.  <span data-ttu-id="38ace-232">開啟 InfoPath 表單**Invalid Expense Report-John Doe.xml**。</span><span class="sxs-lookup"><span data-stu-id="38ace-232">Open the InfoPath form **Invalid Expense Report - John Doe.xml**.</span></span> <span data-ttu-id="38ace-233">查看**部門**欄位中的表單。</span><span class="sxs-lookup"><span data-stu-id="38ace-233">Look at the **Department** field within the form.</span></span> <span data-ttu-id="38ace-234">這個欄位是設定為某個無效值。</span><span class="sxs-lookup"><span data-stu-id="38ace-234">This field is set to some invalid value.</span></span>  
  
2.  <span data-ttu-id="38ace-235">在 InfoPath 視窗左上角，按一下**送出**。</span><span class="sxs-lookup"><span data-stu-id="38ace-235">In the upper-left corner of the InfoPath window, click **Submit**.</span></span> <span data-ttu-id="38ace-236">等候確認視窗表示經費支出報表已成功重新提交。</span><span class="sxs-lookup"><span data-stu-id="38ace-236">Wait for a confirmation window that says the expense report was successfully submitted.</span></span>  
  
     <span data-ttu-id="38ace-237">-或-</span><span class="sxs-lookup"><span data-stu-id="38ace-237">-OR-</span></span>  
  
     <span data-ttu-id="38ace-238">複製並貼到這個檔案**ExpenseReportIn**資料夾。</span><span class="sxs-lookup"><span data-stu-id="38ace-238">Copy and paste this file into the **ExpenseReportIn** folder.</span></span>  
  
3.  <span data-ttu-id="38ace-239">您應該會看到新的檔案，稱為**ErrorReport_\<***日期*_*時間***\>.xml**放入**ExpenseReportOut**資料夾。</span><span class="sxs-lookup"><span data-stu-id="38ace-239">You should see a new file called **ErrorReport_\<***date*_*time***\>.xml** dropped into the **ExpenseReportOut** folder.</span></span>  
  
     <span data-ttu-id="38ace-240">開啟這個檔案，觀察這是上一個步驟中所提交，但是開頭包含錯誤資訊的經費支出報表。</span><span class="sxs-lookup"><span data-stu-id="38ace-240">Open this file and observe that this is the expense report submitted in the previous step but with the error information added at the beginning.</span></span>  
  
4.  <span data-ttu-id="38ace-241">錯誤的部門值取代為"Marketing"，然後**送出**InfoPath 視窗左上角。</span><span class="sxs-lookup"><span data-stu-id="38ace-241">Replace the erroneous department value with "Marketing", and then click **Submit** in the upper-left corner of the InfoPath window.</span></span>  
  
     <span data-ttu-id="38ace-242">-或-</span><span class="sxs-lookup"><span data-stu-id="38ace-242">-OR-</span></span>  
  
     <span data-ttu-id="38ace-243">複製並貼到這個檔案**ResubmittedReportIn**資料夾。</span><span class="sxs-lookup"><span data-stu-id="38ace-243">Copy and paste this file into the **ResubmittedReportIn** folder.</span></span>  
  
5.  <span data-ttu-id="38ace-244">您應該會看到新的檔案中建立**ExpenseReportOut**資料夾。</span><span class="sxs-lookup"><span data-stu-id="38ace-244">You should see a new file created in the **ExpenseReportOut** folder.</span></span> <span data-ttu-id="38ace-245">這個檔案是更正後重新提交至伺服器的經費支出報表。</span><span class="sxs-lookup"><span data-stu-id="38ace-245">This file is the corrected expense report that was resubmitted into the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ace-246">請參閱</span><span class="sxs-lookup"><span data-stu-id="38ace-246">See Also</span></span>  
 <span data-ttu-id="38ace-247">[使用失敗的訊息路由](../core/using-failed-message-routing.md) </span><span class="sxs-lookup"><span data-stu-id="38ace-247">[Using Failed Message Routing](../core/using-failed-message-routing.md) </span></span>  
 [<span data-ttu-id="38ace-248">傳訊 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="38ace-248">Messaging (BizTalk Server Samples Folder)</span></span>](../core/messaging-biztalk-server-samples-folder.md)