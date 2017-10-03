---
title: "貸款處理使用商務規則 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, business rules
- business rules, examples
ms.assetid: 3e1c80c6-adc1-4a0f-83fd-409ce1b8f21f
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c51f0ff13b06bd57ccdd52ec6e35fdd7e0acf839
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="loans-processing-using-business-rules-biztalk-server-sample"></a><span data-ttu-id="9361f-102">貸款處理使用商務規則 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="9361f-102">Loans Processing Using Business Rules (BizTalk Server Sample)</span></span>
<span data-ttu-id="9361f-103">「使用商務規則處理貸款」範例將示範如何使用協調流程內管理的規則集，以及如何使用稱為「事實」的輸入組合，計算所處理文件內某些欄位的設定。</span><span class="sxs-lookup"><span data-stu-id="9361f-103">The Loans Processing Using Business Rules sample demonstrates how to use a set of rules managed within an orchestration, and how to use a combination of inputs known as facts, to calculate settings for some fields within a document being processed.</span></span> <span data-ttu-id="9361f-104">事實可以是呼叫 .NET 架構組件的結果，從訊息的 XML 擷取的值，或是從資料庫擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="9361f-104">Facts can be the result of calling a .NET-based assembly, the values retrieved from the XML of the message, or the data retrieved from a database.</span></span> <span data-ttu-id="9361f-105">此範例還會示範，如何隨時變更規則來影響後續計算，而不需重新部署。</span><span class="sxs-lookup"><span data-stu-id="9361f-105">The sample also demonstrates how you can change the rules at any time, affecting subsequent calculations without the need to redeploy.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="9361f-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="9361f-106">What This Sample Does</span></span>  
 <span data-ttu-id="9361f-107">此範例將使用簡化的貸款處理實例內容示範這些功能。</span><span class="sxs-lookup"><span data-stu-id="9361f-107">This sample demonstrates these capabilities within the context of a simplified loan processing scenario.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9361f-108">協調流程會挑選並處理貸款申請，也稱為貸款案件的 XML 訊息格式。</span><span class="sxs-lookup"><span data-stu-id="9361f-108"> orchestration picks up and processes a loan application, also known as a loan case, in XML message format.</span></span> <span data-ttu-id="9361f-109">此協調流程會使用「商務規則引擎」根據規則評估內送訊息、透過套用規則的結果修改訊息，然後將訊息做為檔案寫入輸入資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9361f-109">This orchestration uses the Business Rule Engine to evaluate incoming messages according to the rules, modifying the message with the result of the application of the rules, and then writing the message as a file to an output folder.</span></span>  
  
 <span data-ttu-id="9361f-110">這個範例根據事實從數個來源，包括正在處理的訊息設定**IncomeStatus**， **CommitmentsStatus**， **EmploymentStatus**，和**ResidencyStatus**正在處理的訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="9361f-110">Based on facts from several sources, including the message being processed, this sample sets the **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, and **ResidencyStatus** elements of the message being processed.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="9361f-111">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="9361f-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="9361f-112">\<*範例路徑*> \Business Rules\Loans 處理使用商務 Rules\\</span><span class="sxs-lookup"><span data-stu-id="9361f-112">\<*Samples Path*>\Business Rules\Loans Processing using Business Rules\\</span></span>  
  
 <span data-ttu-id="9361f-113">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="9361f-113">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="9361f-114">檔案</span><span class="sxs-lookup"><span data-stu-id="9361f-114">File(s)</span></span>|<span data-ttu-id="9361f-115">Description</span><span class="sxs-lookup"><span data-stu-id="9361f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9361f-116">Case.xsd</span><span class="sxs-lookup"><span data-stu-id="9361f-116">Case.xsd</span></span>|<span data-ttu-id="9361f-117">內送貸款申請的結構描述檔，亦稱為貸款案件。</span><span class="sxs-lookup"><span data-stu-id="9361f-117">Schema file for inbound loan applications, otherwise known as loan cases.</span></span>|  
|<span data-ttu-id="9361f-118">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="9361f-118">Cleanup.bat</span></span>|<span data-ttu-id="9361f-119">用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。</span><span class="sxs-lookup"><span data-stu-id="9361f-119">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="9361f-120">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="9361f-120">Removes send and receive ports.</span></span> <span data-ttu-id="9361f-121">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="9361f-121">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="9361f-122">Create_CustInfo_Table.sql</span><span class="sxs-lookup"><span data-stu-id="9361f-122">Create_CustInfo_Table.sql</span></span>|<span data-ttu-id="9361f-123">SQL 指令碼，用於建立 SQL Northwind 範例資料庫中的 CustInfo 資料表。</span><span class="sxs-lookup"><span data-stu-id="9361f-123">SQL script for creating the CustInfo table in the SQL Northwind sample database.</span></span>|  
|<span data-ttu-id="9361f-124">LoanProcessorBinding.xml</span><span class="sxs-lookup"><span data-stu-id="9361f-124">LoanProcessorBinding.xml</span></span>|<span data-ttu-id="9361f-125">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="9361f-125">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="9361f-126">LoansProcessor.btproj、LoansProcessor.sln</span><span class="sxs-lookup"><span data-stu-id="9361f-126">LoansProcessor.btproj, LoansProcessor.sln</span></span>|<span data-ttu-id="9361f-127">此範例的 BizTalk 專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="9361f-127">BizTalk project and solution files for this sample.</span></span>|  
|<span data-ttu-id="9361f-128">My Sample Service.odx</span><span class="sxs-lookup"><span data-stu-id="9361f-128">My Sample Service.odx</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9361f-129">此範例協調流程。</span><span class="sxs-lookup"><span data-stu-id="9361f-129"> orchestration for this sample.</span></span>|  
|<span data-ttu-id="9361f-130">sampleLoan.xml</span><span class="sxs-lookup"><span data-stu-id="9361f-130">sampleLoan.xml</span></span>|<span data-ttu-id="9361f-131">範例輸入檔，其中 XML 結構結尾的四個狀態項目未包含值。</span><span class="sxs-lookup"><span data-stu-id="9361f-131">Sample input file, with empty values for the four status elements at the end of the XML structure in the file.</span></span>|  
|<span data-ttu-id="9361f-132">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="9361f-132">Setup.bat</span></span>|<span data-ttu-id="9361f-133">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="9361f-133">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="9361f-134">在 \CreateRules 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9361f-134">In the \CreateRules folder:</span></span><br /><br /> <span data-ttu-id="9361f-135">App.ico、AssemblyInfo.cs、Case.xsd、CreateLoanProcessingPolicy.csproj、CreateLoanProcessingPolicy.sln、WriteToBRL.cs</span><span class="sxs-lookup"><span data-stu-id="9361f-135">App.ico, AssemblyInfo.cs, Case.xsd, CreateLoanProcessingPolicy.csproj, CreateLoanProcessingPolicy.sln, WriteToBRL.cs</span></span>|<span data-ttu-id="9361f-136">Visual C# 專案、方案、原始程式及相關檔案，用來建立以程式設計方式建立規則集中各項規則的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9361f-136">Visual C# project, solution, source, and related files used to create the application that programmatically creates the rules in the set.</span></span> <span data-ttu-id="9361f-137">如需以程式設計方式建置的規則集範例，請參閱原始程式檔 WriteToBRL.cs。</span><span class="sxs-lookup"><span data-stu-id="9361f-137">For examples of programmatically building sets of rules, refer to the source file WriteToBRL.cs.</span></span>|  
|<span data-ttu-id="9361f-138">在 \myFactRetriever 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9361f-138">In the \myFactRetriever folder:</span></span><br /><br /> <span data-ttu-id="9361f-139">AssemblyInfo.cs</span><span class="sxs-lookup"><span data-stu-id="9361f-139">AssemblyInfo.cs</span></span><br /><br /> <span data-ttu-id="9361f-140">FactRetrieverForLoansProcessing.cs</span><span class="sxs-lookup"><span data-stu-id="9361f-140">FactRetrieverForLoansProcessing.cs</span></span><br /><br /> <span data-ttu-id="9361f-141">myFactRetriever.csproj</span><span class="sxs-lookup"><span data-stu-id="9361f-141">myFactRetriever.csproj</span></span><br /><br /> <span data-ttu-id="9361f-142">myFactRetriever.sln</span><span class="sxs-lookup"><span data-stu-id="9361f-142">myFactRetriever.sln</span></span>|<span data-ttu-id="9361f-143">Visual C# 專案、方案、原始程式集相關檔案，用來建立從之前新增至 Northwind 範例 SQL Server 資料庫中的 CustInfo 資料表擷取資訊的組件。</span><span class="sxs-lookup"><span data-stu-id="9361f-143">Visual C# project, solution, source, and related files used to create an assembly that you use to retrieve information from the CustInfo table added earlier to the Northwind sample SQL Server database.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="9361f-144">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="9361f-144">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-loans-processing-using-business-rules-sample"></a><span data-ttu-id="9361f-145">建置和初始化使用商務規則的貸款處理範例</span><span class="sxs-lookup"><span data-stu-id="9361f-145">To build and initialize the Loans Processing Using Business Rules sample</span></span>  
  
1.  <span data-ttu-id="9361f-146">確定您的電腦上已安裝 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9361f-146">Make sure that you have the Northwind database on your machine.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9361f-147">您必須已安裝名為 Northwind 的資料庫，才能執行此範例。</span><span class="sxs-lookup"><span data-stu-id="9361f-147">In order to run this sample, you must have a database named Northwind.</span></span> [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]<span data-ttu-id="9361f-148">和[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]並未隨附 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="9361f-148"> and [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] do not ship with the Northwind sample database.</span></span> <span data-ttu-id="9361f-149">如果要建立 Northwind 資料庫，請從安裝檔案下載[http://go.microsoft.com/fwlink/?LinkId=196020](http://go.microsoft.com/fwlink/?LinkId=196020)，並遵循指示。</span><span class="sxs-lookup"><span data-stu-id="9361f-149">To create the Northwind database, download the install file from [http://go.microsoft.com/fwlink/?LinkId=196020](http://go.microsoft.com/fwlink/?LinkId=196020), and follow the instructions.</span></span>  
  
2.  <span data-ttu-id="9361f-150">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="9361f-150">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="9361f-151">\<*範例路徑*> \Business Rules\Loans 處理使用商務規則</span><span class="sxs-lookup"><span data-stu-id="9361f-151">\<*Samples Path*>\Business Rules\Loans Processing using Business Rules</span></span>  
  
3.  <span data-ttu-id="9361f-152">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9361f-152">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="9361f-153">清除 GAC 以便刪除之前執行此範例所留下的資料。</span><span class="sxs-lookup"><span data-stu-id="9361f-153">Cleans up the GAC to eliminate any residual data from previous runs of this sample.</span></span>  
  
    -   <span data-ttu-id="9361f-154">編譯及部署事實擷取器程式 myFactRetreiever.dll。</span><span class="sxs-lookup"><span data-stu-id="9361f-154">Compiles and deploys the fact retriever program, myFactRetreiever.dll.</span></span>  
  
    -   <span data-ttu-id="9361f-155">使用 SQL 指令碼檔案 Create_CustInfo_Table.sql、將名為 CustInfo 的資料表新增至 Northwind 範例 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9361f-155">Using the SQL script file Create_CustInfo_Table.sql, adds a table named CustInfo to the Northwind sample SQL database.</span></span>  
  
    -   <span data-ttu-id="9361f-156">清除共用 SQL 規則存放區，以便刪除之前執行此範例所留下的資料。</span><span class="sxs-lookup"><span data-stu-id="9361f-156">Cleans up the shared SQL rule store to eliminate residue of previous runs of this sample.</span></span>  
  
    -   <span data-ttu-id="9361f-157">建立、發佈及部署貸款處理規則集的最新版本 (1.0)。</span><span class="sxs-lookup"><span data-stu-id="9361f-157">Creates, publishes, and deploys the most recent version (1.0) of the loans processing rule set.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9361f-158">您可以使用商務規則編輯器工具隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]檢查以程式設計方式設定的規則。</span><span class="sxs-lookup"><span data-stu-id="9361f-158">You can use the Business Rule Composer tool supplied with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to examine the rules that have been set programmatically.</span></span>  
  
    -   <span data-ttu-id="9361f-159">建立此範例的輸入 (In) 和輸出 (Out) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9361f-159">Creates the input (In) and output (Out) folders for this sample.</span></span>  
  
    -   <span data-ttu-id="9361f-160">編譯及部署此範例的其餘 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，包括含有用來協調此範例之協調流程的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="9361f-160">Compiles and deploys the remaining [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, including the BizTalk project that contains the orchestration you use to coordinate this sample.</span></span>  
  
    -   <span data-ttu-id="9361f-161">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="9361f-161">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9361f-162">這個範例會在建立和繫結連接埠時顯示下列警告：</span><span class="sxs-lookup"><span data-stu-id="9361f-162">This sample displays the following warnings when creating and binding ports:</span></span>  
        >   
        >  `Warning: Receive handler not specified for receive location "LoansProcessor_1.0.0.0_LoansProcessor.My_Sample_Service_Incoming_ReceiveLocation"; updating with first receive handler with matching transport type.`  
        >   
        >  `Warning: Host not specified for orchestration "LoansProcessor.My_Sample_Service"; updating with first available host.`  
        >   
        >  <span data-ttu-id="9361f-163">您可以安全地忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="9361f-163">You can safely ignore these warnings.</span></span> <span data-ttu-id="9361f-164">(繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。</span><span class="sxs-lookup"><span data-stu-id="9361f-164">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  
  
    -   <span data-ttu-id="9361f-165">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9361f-165">Enables the receive location, and starts the send port.</span></span>  
  
    -   <span data-ttu-id="9361f-166">登錄並啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="9361f-166">Enlists and starts the orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9361f-167">如果您的 BizTalk 主控件名稱不是 BizTalkServerApplication，請修改 Setup.bat 檔和 LoanProcessorBinding.xml 檔以反映正確的主控件名稱。</span><span class="sxs-lookup"><span data-stu-id="9361f-167">If your BizTalk host name is not BizTalkServerApplication, modify the file Setup.bat and the file LoanProcessorBinding.xml to reflect the proper host name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9361f-168">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="9361f-168">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9361f-169">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="9361f-169">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="9361f-170">使用此金鑰組簽署所產生的組件。</span><span class="sxs-lookup"><span data-stu-id="9361f-170">Use this key pair to sign the resulting assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9361f-171">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="9361f-171">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="9361f-172">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="9361f-172">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="9361f-173">執行此範例</span><span class="sxs-lookup"><span data-stu-id="9361f-173">Running This Sample</span></span>  
  
#### <a name="to-run-the-loans-processing-using-business-rules-sample"></a><span data-ttu-id="9361f-174">執行使用商務規則處理貸款範例</span><span class="sxs-lookup"><span data-stu-id="9361f-174">To run the Loans Processing Using Business Rules sample</span></span>  
  
1.  <span data-ttu-id="9361f-175">到 sampleLoan.xml 檔的複本貼**\In**資料夾。</span><span class="sxs-lookup"><span data-stu-id="9361f-175">Paste a copy of the file sampleLoan.xml into the **\In** folder.</span></span>  
  
2.  <span data-ttu-id="9361f-176">觀察資料夾中建立的.xml 檔案**出**。它包含輸入的 XML 訊息與下列四個狀態項目，在 XML 結構結尾加入資料： **IncomeStatus**， **CommitmentsStatus**， **EmploymentStatus**，和**ResidencyStatus**。</span><span class="sxs-lookup"><span data-stu-id="9361f-176">Observe the .xml file created in the folder **Out**. It contains the input XML message with data added to the following four status elements at the end of the XML structure: **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, and **ResidencyStatus**.</span></span>  
  
 <span data-ttu-id="9361f-177">您可以使用「商務規則編輯器」工具變更規則集中的規則，然後重新部署這些規則。</span><span class="sxs-lookup"><span data-stu-id="9361f-177">You can use the Business Rule Composer tool to change the rules in the rule set, and then redeploy those rules.</span></span>  
  
#### <a name="to-use-the-business-rule-composer-tool-to-change-one-or-more-of-the-rules-in-a-rule-set"></a><span data-ttu-id="9361f-178">使用商務規則編輯器工具變更規則集中的一或多項規則</span><span class="sxs-lookup"><span data-stu-id="9361f-178">To use the Business Rule Composer tool to change one or more of the rules in a rule set</span></span>  
  
1.  <span data-ttu-id="9361f-179">按一下**啟動**，指向 **程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 **商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="9361f-179">Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rule Composer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9361f-180">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="9361f-180">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="9361f-181">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="9361f-181">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="9361f-182">在**SQL Server**對話方塊中，按一下 **確定**連接至規則存放區。</span><span class="sxs-lookup"><span data-stu-id="9361f-182">In the **SQL Server** dialog box, click **OK** to connect to the rule store.</span></span>  
  
3.  <span data-ttu-id="9361f-183">在**原則總管**，節點的下面**LoanProcessing**，以滑鼠右鍵按一下**1.0 版 – 已部署**節點，然後再按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="9361f-183">In **Policy Explorer**, below the node **LoanProcessing**, right-click the **Version 1.0 – Deployed** node, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="9361f-184">以滑鼠右鍵按一下**LoanProcessing**，然後按一下 **貼上**。</span><span class="sxs-lookup"><span data-stu-id="9361f-184">Right-click **LoanProcessing**, and then click **Paste**.</span></span>  
  
5.  <span data-ttu-id="9361f-185">變更任何規則或動作會導致不同的值的方式**IncomeStatus**， **CommitmentsStatus**， **EmploymentStatus**，和**ResidencyStatus**項目。</span><span class="sxs-lookup"><span data-stu-id="9361f-185">Change any rule or action in a way that will result in different values for the **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, and **ResidencyStatus** elements.</span></span> <span data-ttu-id="9361f-186">請確定您也可以變更負數部份的值 (基本上， **Else**子句) 的任何您選擇變更的規則。</span><span class="sxs-lookup"><span data-stu-id="9361f-186">Ensure that you also change the value of the negation portion (essentially, the **Else** clause) of any rule that you choose to change.</span></span>  
  
     <span data-ttu-id="9361f-187">下表顯示此範例使用的規則集。</span><span class="sxs-lookup"><span data-stu-id="9361f-187">The following table shows the set of rules used by this sample.</span></span> <span data-ttu-id="9361f-188">除非有另外特別說明，否則事實會來自內送 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="9361f-188">Unless specifically mentioned otherwise, facts are from the incoming XML message.</span></span> <span data-ttu-id="9361f-189">字串 (db) 表示，事實的來源為資料庫。</span><span class="sxs-lookup"><span data-stu-id="9361f-189">The string (db) indicates a database as the source of a fact.</span></span>  
  
    |<span data-ttu-id="9361f-190">規則號碼</span><span class="sxs-lookup"><span data-stu-id="9361f-190">Rule number</span></span>|<span data-ttu-id="9361f-191">規則名稱</span><span class="sxs-lookup"><span data-stu-id="9361f-191">Rule name</span></span>|<span data-ttu-id="9361f-192">Description</span><span class="sxs-lookup"><span data-stu-id="9361f-192">Description</span></span>|  
    |-----------------|---------------|-----------------|  
    |<span data-ttu-id="9361f-193">1</span><span class="sxs-lookup"><span data-stu-id="9361f-193">1</span></span>|<span data-ttu-id="9361f-194">Income Status Rule</span><span class="sxs-lookup"><span data-stu-id="9361f-194">Income Status Rule</span></span>|<span data-ttu-id="9361f-195">如果**BasicSalary** + **OtherIncome** > 0</span><span class="sxs-lookup"><span data-stu-id="9361f-195">IF **BasicSalary** + **OtherIncome** > 0</span></span><br /><br /> <span data-ttu-id="9361f-196">然後**IncomeStatus** = **有效**</span><span class="sxs-lookup"><span data-stu-id="9361f-196">THEN **IncomeStatus** = **Valid**</span></span>|  
    |<span data-ttu-id="9361f-197">2</span><span class="sxs-lookup"><span data-stu-id="9361f-197">2</span></span>|<span data-ttu-id="9361f-198">Commitments Status Rule</span><span class="sxs-lookup"><span data-stu-id="9361f-198">Commitments Status Rule</span></span>|<span data-ttu-id="9361f-199">如果**識別碼** == **識別碼 (db)**</span><span class="sxs-lookup"><span data-stu-id="9361f-199">IF **ID** == **ID (db)**</span></span><br /><br /> <span data-ttu-id="9361f-200">與</span><span class="sxs-lookup"><span data-stu-id="9361f-200">AND</span></span><br /><br /> <span data-ttu-id="9361f-201">如果**CreditCardBalance (db)** > 500</span><span class="sxs-lookup"><span data-stu-id="9361f-201">IF **CreditCardBalance (db)** > 500</span></span><br /><br /> <span data-ttu-id="9361f-202">然後**CommitmentsStatus** =</span><span class="sxs-lookup"><span data-stu-id="9361f-202">THEN **CommitmentsStatus** =</span></span><br /><br /> <span data-ttu-id="9361f-203">"Compute Commitments"</span><span class="sxs-lookup"><span data-stu-id="9361f-203">"Compute Commitments"</span></span>|  
    |<span data-ttu-id="9361f-204">3</span><span class="sxs-lookup"><span data-stu-id="9361f-204">3</span></span>|<span data-ttu-id="9361f-205">Employment Status Rule</span><span class="sxs-lookup"><span data-stu-id="9361f-205">Employment Status Rule</span></span>|<span data-ttu-id="9361f-206">如果**EmploymentType &#124;TimeInMonths** > 18</span><span class="sxs-lookup"><span data-stu-id="9361f-206">IF **EmploymentType &#124; TimeInMonths** > 18</span></span><br /><br /> <span data-ttu-id="9361f-207">然後**EmploymentStatus** = **有效**</span><span class="sxs-lookup"><span data-stu-id="9361f-207">THEN **EmploymentStatus** = **Valid**</span></span>|  
    |<span data-ttu-id="9361f-208">4</span><span class="sxs-lookup"><span data-stu-id="9361f-208">4</span></span>|<span data-ttu-id="9361f-209">Residency Status Rule</span><span class="sxs-lookup"><span data-stu-id="9361f-209">Residency Status Rule</span></span>|<span data-ttu-id="9361f-210">如果**PlaceOfResidence &#124;TimeInMonths** > 18</span><span class="sxs-lookup"><span data-stu-id="9361f-210">IF **PlaceOfResidence &#124; TimeInMonths** > 18</span></span><br /><br /> <span data-ttu-id="9361f-211">然後**ResidencyStatus** = **有效**</span><span class="sxs-lookup"><span data-stu-id="9361f-211">THEN **ResidencyStatus** = **Valid**</span></span>|  
    |<span data-ttu-id="9361f-212">!1, !2, !3, !4</span><span class="sxs-lookup"><span data-stu-id="9361f-212">!1, !2, !3, !4</span></span>|<span data-ttu-id="9361f-213">Negation Rules</span><span class="sxs-lookup"><span data-stu-id="9361f-213">Negation Rules</span></span>|<span data-ttu-id="9361f-214">條件的邏輯**不**對應規則 1 – 4 中所述的條件。</span><span class="sxs-lookup"><span data-stu-id="9361f-214">Conditions that are a logical **NOT** of the corresponding condition described in rules 1–4.</span></span> <span data-ttu-id="9361f-215">結果動作為所設定字串的變更。</span><span class="sxs-lookup"><span data-stu-id="9361f-215">Resulting actions are a change in the string that is being set.</span></span>|  
  
6.  <span data-ttu-id="9361f-216">以滑鼠右鍵按一下**版本 1.1 （未儲存）**節點，然後再按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="9361f-216">Right-click the **Version 1.1(not saved)** node, and then click **Save**.</span></span>  
  
7.  <span data-ttu-id="9361f-217">以滑鼠右鍵按一下**1.1 版**節點，然後再按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="9361f-217">Right-click the **Version 1.1** node, and then click **Publish**.</span></span>  
  
8.  <span data-ttu-id="9361f-218">以滑鼠右鍵按一下**1.1 版**節點，然後再按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="9361f-218">Right-click the **Version 1.1** node, and then click **Deploy**.</span></span>  
  
9. <span data-ttu-id="9361f-219">等候 60 秒，讓變更傳播到共用 SQL Server 規則存放區。</span><span class="sxs-lookup"><span data-stu-id="9361f-219">Wait for 60 seconds for the changes to propagate to the shared SQL Server rule store.</span></span>  
  
10. <span data-ttu-id="9361f-220">將 sampleLoan.xml 檔的複本貼到資料夾**中**。</span><span class="sxs-lookup"><span data-stu-id="9361f-220">Paste a copy of the file sampleLoan.xml into the folder **In**.</span></span>  
  
11. <span data-ttu-id="9361f-221">觀察資料夾中建立的.xml 檔案**出**。它包含輸入的 XML 訊息與下列四個狀態項目，在 XML 結構結尾加入資料： **IncomeStatus**， **CommitmentsStatus**， **EmploymentStatus**，和**ResidencyStatus**。</span><span class="sxs-lookup"><span data-stu-id="9361f-221">Observe the .xml file created in the folder **Out**. It contains the input XML message with data added to the following four status elements at the end of the XML structure: **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, and **ResidencyStatus**.</span></span> <span data-ttu-id="9361f-222">視此程序步驟 5 中所做的變更本質而定，新增至這些項目的資料可能會與上一次執行時的資料不同。</span><span class="sxs-lookup"><span data-stu-id="9361f-222">The data added to these elements will differ, or not, from the previous run, based on the nature of the changes made in step 5in this procedure.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="9361f-223">註解</span><span class="sxs-lookup"><span data-stu-id="9361f-223">Comments</span></span>  
 <span data-ttu-id="9361f-224">如果您要檢視此範例的追蹤資訊，您必須使用 [商務規則引擎部署精靈] 解除部署再重新部署相關的規則集 (貸款處理)。</span><span class="sxs-lookup"><span data-stu-id="9361f-224">If you want to view the tracking information for this sample, you must undeploy and then redeploy the relevant rule set (Loans Processing) by using the Business Rules Engine Deployment Wizard.</span></span>  
  
 <span data-ttu-id="9361f-225">此範例將示範如何使用商務規則，在協調流程內以規則的形式套用商務原則。</span><span class="sxs-lookup"><span data-stu-id="9361f-225">This sample demonstrates how you can use business rules to apply business policies in the form of rules within an orchestration.</span></span> <span data-ttu-id="9361f-226">此外還會示範如何變更原則，以及在協調流程中動態反映原則的變更，而不需重新編譯或重新部署協調流程方案。</span><span class="sxs-lookup"><span data-stu-id="9361f-226">It also demonstrates how you can change the policies, and have the change in the policy reflected dynamically within the orchestration without having to recompile or redeploy the orchestration solution.</span></span>  
  
 <span data-ttu-id="9361f-227">此範例的輸入貸款案件是 XML 訊息，其結構如下：</span><span class="sxs-lookup"><span data-stu-id="9361f-227">Input loan cases to this sample are XML messages that have the following structure:</span></span>  
  
```  
    Name  
    ID  
    Income  
        BasicSalary  
        OtherIncome  
    EmploymentType  
        TimeInMonths  
    PlaceOfResidence  
        TimeInMonths  
    CommitmentsStatus  
    IncomeStatus  
    EmploymentStatus  
    ResidencyStatus  
```  
  
## <a name="see-also"></a><span data-ttu-id="9361f-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9361f-228">See Also</span></span>  
 [<span data-ttu-id="9361f-229">商務規則 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="9361f-229">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)