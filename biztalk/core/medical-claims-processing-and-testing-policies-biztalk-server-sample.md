---
title: 醫療理賠處理和測試原則 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, business rules
- business rules, examples
ms.assetid: c0bdf7b7-3e55-4560-a5a8-00c5b661d14d
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e67b9a631764ed83659b05aa11f4c1570484f74
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994863"
---
# <a name="medical-claims-processing-and-testing-policies-biztalk-server-sample"></a><span data-ttu-id="9feb0-102">醫療理賠處理和測試原則 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="9feb0-102">Medical Claims Processing and Testing Policies (BizTalk Server Sample)</span></span>
<span data-ttu-id="9feb0-103">「醫療理賠處理和測試原則」範例示範如何建立一組規則集，其中多個規則會檢查衍生自資料庫資料表的事實和輸入文件，並使用 .NET 架構物件來記錄理賠處理的結果。</span><span class="sxs-lookup"><span data-stu-id="9feb0-103">The Medical Claims Processing and Testing Policies sample demonstrates how to create a rule set containing multiple rules that examine facts derived from a database table and the inbound document, and which use .NET-based objects to record the results of the claims processing.</span></span>  
  
 <span data-ttu-id="9feb0-104">這個範例會示範端對端執行理賠處理的實例，透過使用「商務規則引擎」的簡單 .NET 架構應用程式，對輸入的理賠申請執行醫療理賠規則集，判斷理賠申請的 STATUS 及其 REASON。</span><span class="sxs-lookup"><span data-stu-id="9feb0-104">This sample demonstrates end-end execution of the claim processing scenario using a simple .NET-based application that uses the Business Rule Engine to run a medical claims rule set against incoming claims to determine the STATUS of the claim and the REASON for the status.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9feb0-105">這個範例也會示範如何使用偵錯追蹤檔案，追蹤「商務規則引擎」的執行狀況。</span><span class="sxs-lookup"><span data-stu-id="9feb0-105">This sample also demonstrates how to trace Business Rule Engine execution using a debug trace file.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="9feb0-106">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="9feb0-106">What This Sample Does</span></span>  
 <span data-ttu-id="9feb0-107">這個範例會將下列一連串規則套用至提交的理賠申請：</span><span class="sxs-lookup"><span data-stu-id="9feb0-107">This sample applies the following sequence of rules to submitted claims:</span></span>  
  
1.  <span data-ttu-id="9feb0-108">如果理賠申請的總金額超過原則允許的上限，則拒絕理賠申請。</span><span class="sxs-lookup"><span data-stu-id="9feb0-108">Rejects the claim if the total amount claimed exceeds the maximum permitted by the policy.</span></span>  
  
2.  <span data-ttu-id="9feb0-109">如果客戶住院天數超過原則允許的上限，則拒絕理賠申請。</span><span class="sxs-lookup"><span data-stu-id="9feb0-109">Rejects the claim if the client has stayed in hospitals more nights than the maximum permitted by the policy.</span></span>  
  
3.  <span data-ttu-id="9feb0-110">如果理賠申請上的日期是在未來，則拒絕理賠申請。</span><span class="sxs-lookup"><span data-stu-id="9feb0-110">Rejects the claim if the date on the claim is in the future.</span></span>  
  
4.  <span data-ttu-id="9feb0-111">如果原則無效則拒絕理賠申請。</span><span class="sxs-lookup"><span data-stu-id="9feb0-111">Rejects the claim if the policy is not valid.</span></span>  
  
5.  <span data-ttu-id="9feb0-112">如果原則已過期，則傳送線索給銷售部門並附上原則識別碼和客戶名稱。</span><span class="sxs-lookup"><span data-stu-id="9feb0-112">Sends a lead to the sales department with the policy ID and customer name if the policy has expired.</span></span>  
  
6.  <span data-ttu-id="9feb0-113">否則核准理賠申請。</span><span class="sxs-lookup"><span data-stu-id="9feb0-113">Otherwise, approves the claim.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="9feb0-114">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="9feb0-114">Where to Find This Sample</span></span>  
 <span data-ttu-id="9feb0-115">\<*範例路徑*\>\Business Rules\Medical 理賠處理和測試 Policies\\</span><span class="sxs-lookup"><span data-stu-id="9feb0-115">\<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\\</span></span>  
  
 <span data-ttu-id="9feb0-116">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="9feb0-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="9feb0-117">檔案</span><span class="sxs-lookup"><span data-stu-id="9feb0-117">File(s)</span></span>|<span data-ttu-id="9feb0-118">描述</span><span class="sxs-lookup"><span data-stu-id="9feb0-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9feb0-119">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="9feb0-119">Cleanup.bat</span></span>|<span data-ttu-id="9feb0-120">用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。</span><span class="sxs-lookup"><span data-stu-id="9feb0-120">Used to undeploy assemblies and remove them from the global assembly cache (GAC).</span></span> <span data-ttu-id="9feb0-121">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="9feb0-121">Removes send and receive ports.</span></span> <span data-ttu-id="9feb0-122">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="9feb0-122">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="9feb0-123">Create_PolicyValidity_Table.sql</span><span class="sxs-lookup"><span data-stu-id="9feb0-123">Create_PolicyValidity_Table.sql</span></span>|<span data-ttu-id="9feb0-124">將新資料表 PolicyValidity 加入 Northwind 範例資料庫的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="9feb0-124">SQL script that adds a new table named PolicyValidity to the Northwind sample database.</span></span>|  
|<span data-ttu-id="9feb0-125">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="9feb0-125">Setup.bat</span></span>|<span data-ttu-id="9feb0-126">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="9feb0-126">Used to build and initialize this sample.</span></span>|  
|<span data-ttu-id="9feb0-127">在 \Claims 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9feb0-127">In the \Claims folder:</span></span><br /><br /> <span data-ttu-id="9feb0-128">AssemblyInfo.cs、Claims.csproj、Claims.sln、Claims.cs</span><span class="sxs-lookup"><span data-stu-id="9feb0-128">AssemblyInfo.cs, Claims.csproj, Claims.sln, Claims.cs</span></span>|<span data-ttu-id="9feb0-129">專案、 解決方案、 來源和相關的檔案，這個記錄理賠處理，結果的範例部分稱為**然後**規則的一部分。</span><span class="sxs-lookup"><span data-stu-id="9feb0-129">Project, solution, source, and related files for the portion of this sample that records the result of the claims processing, called the **THEN** portion of a rule.</span></span>|  
|<span data-ttu-id="9feb0-130">在 \FactRetrieverForClaimsProcessing 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9feb0-130">In the \FactRetrieverForClaimsProcessing folder:</span></span><br /><br /> <span data-ttu-id="9feb0-131">AssemblyInfo.cs、FactRetrieverForClaimsProcessing.cs、FactRetrieverForClaimsProcessing.csproj、FactRetrieverForClaimsProcessing.sln</span><span class="sxs-lookup"><span data-stu-id="9feb0-131">AssemblyInfo.cs, FactRetrieverForClaimsProcessing.cs, FactRetrieverForClaimsProcessing.csproj, FactRetrieverForClaimsProcessing.sln</span></span>|<span data-ttu-id="9feb0-132">這個範例所屬的專案、解決方案、來源和相關檔案，其提供長期事實擷取器 (會從這個範例所建立的 PolicyValidity 資料表擷取資訊)。</span><span class="sxs-lookup"><span data-stu-id="9feb0-132">Project, solution, source, and related files for the portion of this sample that provides the long-term fact retriever that retrieves information from the PolicyValidity table created by this sample.</span></span>|  
|<span data-ttu-id="9feb0-133">在 \RulesForMedicalClaims 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9feb0-133">In the \RulesForMedicalClaims folder:</span></span><br /><br /> <span data-ttu-id="9feb0-134">App.ico、AssemblyInfo.cs、RulesForMedicalClaims.cs、RulesForMedicalClaims.csproj、RulesForMedicalClaims.sln</span><span class="sxs-lookup"><span data-stu-id="9feb0-134">App.ico, AssemblyInfo.cs, RulesForMedicalClaims.cs, RulesForMedicalClaims.csproj, RulesForMedicalClaims.sln</span></span>|<span data-ttu-id="9feb0-135">專案、 解決方案、 來源和相關的檔案，這個範例所屬的構成主要可執行檔 (RulesForMedicalClaims.exe)，此範例和以程式設計方式定義及儲存規則集，建構範例事實，和接著執行使用設定的規則**PolicyTester**物件。</span><span class="sxs-lookup"><span data-stu-id="9feb0-135">Project, solution, source, and related files for the portion of this sample that constitutes the main executable for this sample (RulesForMedicalClaims.exe), and which programmatically defines and stores the rule set, constructs sample facts, and then runs the rule set using a **PolicyTester** object.</span></span>|  
|<span data-ttu-id="9feb0-136">在 \RulesForMedicalClaims 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9feb0-136">In the \RulesForMedicalClaims folder:</span></span><br /><br /> <span data-ttu-id="9feb0-137">MedicalClaims.xsd</span><span class="sxs-lookup"><span data-stu-id="9feb0-137">MedicalClaims.xsd</span></span>|<span data-ttu-id="9feb0-138">結構描述檔案，定義提交至此範例之範例醫療理賠申請的結構。</span><span class="sxs-lookup"><span data-stu-id="9feb0-138">Schema file that defines the structure of the sample medical claims submitted to this sample.</span></span>|  
|<span data-ttu-id="9feb0-139">在 \RulesForMedicalClaims 資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9feb0-139">In the \RulesForMedicalClaims folder:</span></span><br /><br /> <span data-ttu-id="9feb0-140">sampleClaim.xml</span><span class="sxs-lookup"><span data-stu-id="9feb0-140">sampleClaim.xml</span></span>|<span data-ttu-id="9feb0-141">範例輸入檔，與 MedicalClaims.xsd 檔中定義的結構描述相符。</span><span class="sxs-lookup"><span data-stu-id="9feb0-141">Sample input file that conforms to the schema defined in the file MedicalClaims.xsd.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="9feb0-142">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="9feb0-142">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-medical-claims-processing-and-testing-policies-sample"></a><span data-ttu-id="9feb0-143">若要建置及初始化醫療理賠處理和測試原則範例</span><span class="sxs-lookup"><span data-stu-id="9feb0-143">To build and initialize the Medical Claims Processing and Testing Policies sample</span></span>  
  
1. <span data-ttu-id="9feb0-144">確定您的電腦上已安裝 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9feb0-144">Make sure that you have the Northwind database on your machine.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="9feb0-145">若要執行此範例中，您必須具有 Northwind SQL Server 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="9feb0-145">To run this sample, you must have the Northwind SQL Server sample database.</span></span> <span data-ttu-id="9feb0-146">[下載](https://www.microsoft.com/download/details.aspx?id=23654)，並安裝。</span><span class="sxs-lookup"><span data-stu-id="9feb0-146">[Download](https://www.microsoft.com/download/details.aspx?id=23654), and install.</span></span> 
  
2. <span data-ttu-id="9feb0-147">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="9feb0-147">In a command window, navigate to the following folder:</span></span>  
  
    <span data-ttu-id="9feb0-148">\<*範例路徑*\>\Business Rules\Medical 理賠處理和測試 Policies\\</span><span class="sxs-lookup"><span data-stu-id="9feb0-148">\<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\\</span></span>  
  
3. <span data-ttu-id="9feb0-149">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9feb0-149">Run the file Setup.bat, which performs the following actions:</span></span>  
  
   - <span data-ttu-id="9feb0-150">為這個範例編譯及部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，包括 Claims.dll、FactRetrieverForClaimsProcessing.dll 和 RulesForMedicalClaims.dll。</span><span class="sxs-lookup"><span data-stu-id="9feb0-150">Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects for this sample, including Claims.dll, FactRetrieverForClaimsProcessing.dll, and RulesForMedicalClaims.dll.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9feb0-151">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="9feb0-151">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="9feb0-152">若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。</span><span class="sxs-lookup"><span data-stu-id="9feb0-152">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe).</span></span> <span data-ttu-id="9feb0-153">使用此金鑰組簽署所產生的組件。</span><span class="sxs-lookup"><span data-stu-id="9feb0-153">Use this key pair to sign the resulting assemblies.</span></span>  
  
   - <span data-ttu-id="9feb0-154">使用 SQL Query Analyzer 執行所提供的 SQL 指令碼 Create_PolicyValidity_Table.sql。</span><span class="sxs-lookup"><span data-stu-id="9feb0-154">Runs the provided SQL script Create_PolicyValidity_Table.sql using SQL Query Analyzer.</span></span> <span data-ttu-id="9feb0-155">此指令碼會使用 Northwind 範例資料庫中的兩個範例資料列來建立資料表 PolicyValidity。</span><span class="sxs-lookup"><span data-stu-id="9feb0-155">The script creates the table, PolicyValidity, with two sample rows in the Northwind sample database.</span></span> <span data-ttu-id="9feb0-156">此資料表有兩個資料行： ID 和 PolicyStatus。</span><span class="sxs-lookup"><span data-stu-id="9feb0-156">This table has two columns: ID and PolicyStatus.</span></span>  
  
   - <span data-ttu-id="9feb0-157">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="9feb0-157">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports.</span></span>  
  
   - <span data-ttu-id="9feb0-158">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="9feb0-158">Enables the receive location, and starts the send port.</span></span>  
  
   - <span data-ttu-id="9feb0-159">登錄和啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="9feb0-159">Enlists and starts orchestration.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9feb0-160">若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="9feb0-160">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="9feb0-161">您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="9feb0-161">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="9feb0-162">執行此範例</span><span class="sxs-lookup"><span data-stu-id="9feb0-162">Running This Sample</span></span>  
  
#### <a name="to-run-the-medical-claims-processing-and-testing-policies-sample"></a><span data-ttu-id="9feb0-163">若要執行醫療理賠處理和測試原則範例</span><span class="sxs-lookup"><span data-stu-id="9feb0-163">To run the Medical Claims Processing and Testing Policies sample</span></span>  
  
1. <span data-ttu-id="9feb0-164">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="9feb0-164">In a command window, navigate to the following folder:</span></span>  
  
    <span data-ttu-id="9feb0-165">\<*範例路徑*\>\Business Rules\Medical 理賠處理和測試 Policies\RulesForMedicalClaims\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="9feb0-165">\<*Samples Path*\>\Business Rules\Medical Claims Processing and Testing Policies\RulesForMedicalClaims\bin\Debug\\</span></span>  
  
2. <span data-ttu-id="9feb0-166">在命令列上執行檔案 RulesForMedicalClaims.exe。</span><span class="sxs-lookup"><span data-stu-id="9feb0-166">Run the file RulesForMedicalClaims.exe on the command line.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="9feb0-167">您可以變更範例理賠申請檔案 sampleClaim.xml 中的個別項目值，重複執行範例。</span><span class="sxs-lookup"><span data-stu-id="9feb0-167">You can change the values of individual elements in the sample claim file sampleClaim.xml and run the sample repeatedly.</span></span> <span data-ttu-id="9feb0-168">下列清單中會顯示不同項目值的預期輸出。</span><span class="sxs-lookup"><span data-stu-id="9feb0-168">The expected outputs for different values in these elements are shown in the list that follows.</span></span>  
  
   <span data-ttu-id="9feb0-169">根據所提交的範例理賠申請檔案中的各種組合值，輸出實例如下：</span><span class="sxs-lookup"><span data-stu-id="9feb0-169">Output scenarios based on various combinations of values in the submitted sample claims file are:</span></span>  
  
-   <span data-ttu-id="9feb0-170">對於金額超過 $1000 的理賠申請，會取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9feb0-170">For a claim whose amount exceeds $1000, the following output is obtained:</span></span>  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of claim has exceeded Policy limit  
    ```  
  
-   <span data-ttu-id="9feb0-171">對於住院天數超過 10 的理賠申請，會取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9feb0-171">For a claim whose number of nights exceeds 10, the following output is obtained:</span></span>  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of Nights has exceeded Policy limit  
    ```  
  
-   <span data-ttu-id="9feb0-172">對於日期無效 (日期 > 目前日期) 的理賠申請，會取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9feb0-172">For a claim whose date is not valid (date > current date), the following output in obtained:</span></span>  
  
    ```  
    Status:  REJECTED!  
    Reason:  Cannot submit claims for future dates!  
    ```  
  
-   <span data-ttu-id="9feb0-173">不是有效的原則識別碼的宣告 (例如，藉由變更**識別碼**有值為 2 的項目) 因為原則到期，取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9feb0-173">For a claim with a policy ID that is not valid (for example, by changing the **ID** element to have a value of 2) because of policy expiration, the following output is obtained:</span></span>  
  
    ```  
    Sending to Renewal Department for Customer Smir with Policy # 2  
    Status:  REJECTED!  
    Reason:  Policy ID is invalid  
    ```  
  
-   <span data-ttu-id="9feb0-174">對於有效的理賠申請，會取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9feb0-174">For a claim that is valid, the following output is obtained:</span></span>  
  
    ```  
    Status:  Claim Accepted!  
    Reason:  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9feb0-175">每次您執行這個範例時，都會在資料夾 ...\RulesForMedicalClaims\bin\Debug 中建立文字檔 outputtrace.txt。</span><span class="sxs-lookup"><span data-stu-id="9feb0-175">A text file, outputtrace.txt, is created in the folder ...\RulesForMedicalClaims\bin\Debug folder every time you run this sample.</span></span> <span data-ttu-id="9feb0-176">它包含規則執行的偵錯追蹤，每個執行循環之後都會在資料夾 \RulesForMedicalClaims\bin\Debug 中建立。</span><span class="sxs-lookup"><span data-stu-id="9feb0-176">It contains a debug trace of rule execution, and it is created after every execution cycle under the folder \RulesForMedicalClaims\bin\Debug.</span></span> <span data-ttu-id="9feb0-177">您可以檢查這個檔案來查看規則執行的追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="9feb0-177">You can examine this file to see the output trace of rule execution.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="9feb0-178">註解</span><span class="sxs-lookup"><span data-stu-id="9feb0-178">Comments</span></span>  
 <span data-ttu-id="9feb0-179">評估規則集時，所使用的事實來源如下：</span><span class="sxs-lookup"><span data-stu-id="9feb0-179">The fact sources used in the rule set evaluation are:</span></span>  
  
- <span data-ttu-id="9feb0-180">長期事實擷取器。以.NET 為基礎的應用程式可實作**IFactReriever**介面中，建立在資料夾 FactRetrieverForClaimsProcessing 中。</span><span class="sxs-lookup"><span data-stu-id="9feb0-180">A long-term fact retriever, a .NET-based application that implements the **IFactReriever** interface, is built in the folder FactRetrieverForClaimsProcessing.</span></span> <span data-ttu-id="9feb0-181">醫療理賠處理原則會使用它從 PolicyValidity 資料庫擷取資料 (資料集格式)，用於評估規則條件。</span><span class="sxs-lookup"><span data-stu-id="9feb0-181">It is used by the medical claims processing policy to retrieve data (in the form of a dataset) from the PolicyValidity database and to use in rule condition evaluation.</span></span>  
  
- <span data-ttu-id="9feb0-182">宣告是 XML 文件包含下列資訊，儲存在同層級項目表單中： 名稱、 識別碼、 數量、 Nights 和日期。</span><span class="sxs-lookup"><span data-stu-id="9feb0-182">The claim is in the form of an XML document that contains the following information, stored in sibling elements: Name, ID, Amount, Nights, and Date.</span></span>  
  
- <span data-ttu-id="9feb0-183">答:。以.NET 為基礎的類別庫 (Claims) 與**ClaimResults**類別用來記錄的狀態與原因使用屬性的宣告，並傳送線索 （如果原則不是有效的） 叫用**SendLeads**具有識別碼和名稱做為參數的方法。</span><span class="sxs-lookup"><span data-stu-id="9feb0-183">A .NET-based class library (Claims), with a **ClaimResults** class is used to record the STATUS and REASON of the claim using properties, and to send a lead (if the policy is not valid) by invoking the **SendLeads** method with ID and name as parameters.</span></span>  
  
  <span data-ttu-id="9feb0-184">根據這些事實來源，您可以將針對此實例所定義的規則非正式地描述如下：</span><span class="sxs-lookup"><span data-stu-id="9feb0-184">Based on these fact sources, you can informally describe the rules defined for this scenario as follows:</span></span>  
  
1. <span data-ttu-id="9feb0-185">檢查輸入的理賠申請是否有效。</span><span class="sxs-lookup"><span data-stu-id="9feb0-185">Check to see if the incoming claim is valid.</span></span> <span data-ttu-id="9feb0-186">如果理賠申請金額超過允許的上限、如果原則已過期 (可檢查資料庫資料表來驗證)、如果住院天數超過允許的上限，而且如果理賠申請的日期是在未來，則理賠申請無效。</span><span class="sxs-lookup"><span data-stu-id="9feb0-186">The claim is not valid if the amount is over the allowable limit for a claim, if the policy has expired (verified by checking the database table), if the number of nights has exceeded the maximum allowable limit, and if the claim is made for a future date.</span></span> <span data-ttu-id="9feb0-187">如果判斷理賠申請無效，則適當地設定理賠申請的 STATUS 和 REASON。</span><span class="sxs-lookup"><span data-stu-id="9feb0-187">If the claim has been determined to be not valid, set the STATUS and REASON of the claim appropriately.</span></span>  
  
2. <span data-ttu-id="9feb0-188">如果輸入的理賠申請的原則識別碼已過期，則傳送線索給原則更新部門 (並附上原則識別碼和客戶名稱)。</span><span class="sxs-lookup"><span data-stu-id="9feb0-188">If the policy ID of the incoming claim has expired, send a lead (with policy ID and customer name) to the policy renewal department.</span></span>  
  
3. <span data-ttu-id="9feb0-189">如果理賠申請有效，則適當地設定理賠申請的 STATUS 和 REASON。</span><span class="sxs-lookup"><span data-stu-id="9feb0-189">If the claim is valid, set the STATUS and REASON of the claim appropriately.</span></span>  
  
   <span data-ttu-id="9feb0-190">規則及其條件繫結的正式表示如下：</span><span class="sxs-lookup"><span data-stu-id="9feb0-190">A more formal representation of the rules and their term bindings is as follows:</span></span>  
  
-   <span data-ttu-id="9feb0-191">**規則 1。數量檢查**</span><span class="sxs-lookup"><span data-stu-id="9feb0-191">**Rule 1. Amount check**</span></span>  
  
    ```  
    IF Amount in the XML document is > 1000  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"\  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   <span data-ttu-id="9feb0-192">**規則 2。花費在醫院住院**</span><span class="sxs-lookup"><span data-stu-id="9feb0-192">**Rule 2. Nights spent in the hospital**</span></span>  
  
    ```  
    IF number of nights in the XML document is > 10  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   <span data-ttu-id="9feb0-193">**規則 3。日期有效性**</span><span class="sxs-lookup"><span data-stu-id="9feb0-193">**Rule 3. Date validity**</span></span>  
  
    ```  
    IF date on the incoming XML claim is > Today  
      AND   
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Cannot submit claims in the future!"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   <span data-ttu-id="9feb0-194">**規則 4。原則有效性**</span><span class="sxs-lookup"><span data-stu-id="9feb0-194">**Rule 4. Policy validity**</span></span>  
  
    ```  
    IF Policy is invalid for the ID in the XML claim (check database)  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Policy Invalid"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   <span data-ttu-id="9feb0-195">**規則 5。銷售潛在客戶**</span><span class="sxs-lookup"><span data-stu-id="9feb0-195">**Rule 5. Sales lead**</span></span>  
  
    ```  
    IF Claim.ClaimResults.Reason = "Policy invalid"  
  
    THEN send a lead to the policy department by invoking the function Claim.ClaimResults.SendLead with customer ID and Name from the incoming XML document.  
  
    ```  
  
-   <span data-ttu-id="9feb0-196">**規則 6。接受的宣告**</span><span class="sxs-lookup"><span data-stu-id="9feb0-196">**Rule 6. Claim accepted**</span></span>  
  
    ```  
    IF Claim.ClaimResults.Status = null  
  
    THEN Set the claim status to be valid  
         &&  
         Send the lead to the sales department  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9feb0-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9feb0-197">See Also</span></span>  
 [<span data-ttu-id="9feb0-198">商務規則 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="9feb0-198">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)