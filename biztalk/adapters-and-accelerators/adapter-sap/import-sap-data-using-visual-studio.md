---
title: 匯入 SAP 資料使用 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- importing SAP data, how to
- importing SAP data, using Visual Studio
- Visual Studio, importing SAP data
ms.assetid: 70cce089-232d-4ab9-81bd-6b0d6f0097d7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 700d597b3532c0034623553a6d1f0f8147e5642d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985999"
---
# <a name="import-sap-data-using-visual-studio"></a><span data-ttu-id="0a192-102">使用 Visual Studio 的匯入 SAP 資料</span><span class="sxs-lookup"><span data-stu-id="0a192-102">Import SAP Data Using Visual Studio</span></span>
<span data-ttu-id="0a192-103">本節提供有關如何使用 Microsoft 的資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]到 SAP 系統的資料匯入到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a192-103">This section provides information on how to use Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to import data from an SAP system into a SQL Server database.</span></span> <span data-ttu-id="0a192-104">本節提供如何建立匯入資料，您可以執行 SSIS 套件的指示。</span><span class="sxs-lookup"><span data-stu-id="0a192-104">This section provides instruction on how to create an SSIS package that you can execute to import data.</span></span> <span data-ttu-id="0a192-105">本章節也會提供有關如何執行 SSIS 套件的資訊。</span><span class="sxs-lookup"><span data-stu-id="0a192-105">This section also provides information on how to execute the SSIS package.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0a192-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="0a192-106">Prerequisites</span></span>  
 <span data-ttu-id="0a192-107">然後再執行本主題所提供的程序，請確定：</span><span class="sxs-lookup"><span data-stu-id="0a192-107">Before performing the procedures provided in this topic, make sure:</span></span>  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="0a192-108"> 會安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="0a192-108"> is installed on the computer.</span></span>  
  
- [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]<span data-ttu-id="0a192-109"> 會安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="0a192-109"> is installed on the computer.</span></span>  
  
### <a name="to-import-data-using-visual-studio"></a><span data-ttu-id="0a192-110">若要使用 Visual Studio 匯入資料</span><span class="sxs-lookup"><span data-stu-id="0a192-110">To import data using Visual Studio</span></span>  
  
1. <span data-ttu-id="0a192-111">啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並建立的整合服務專案。</span><span class="sxs-lookup"><span data-stu-id="0a192-111">Start [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and create an Integration Service project.</span></span>  
  
2. <span data-ttu-id="0a192-112">從**專案**功能表上，選取**SSIS 匯入和匯出精靈**。</span><span class="sxs-lookup"><span data-stu-id="0a192-112">From the **Project** menu, select **SSIS Import and Export Wizard**.</span></span> <span data-ttu-id="0a192-113">這會啟動**SQL Server 匯入和匯出精靈**。</span><span class="sxs-lookup"><span data-stu-id="0a192-113">This starts the **SQL Server Import and Export Wizard**.</span></span>  
  
3. <span data-ttu-id="0a192-114">閱讀 [歡迎使用] 畫面，然後按一下 [資訊**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="0a192-114">Read the information on the welcome screen and click **Next**.</span></span>  
  
4. <span data-ttu-id="0a192-115">在 [**選擇資料來源**] 對話方塊中，從**資料來源**下拉式清單 **.NET Framework Data Provider for mySAP Business Suite**。</span><span class="sxs-lookup"><span data-stu-id="0a192-115">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list **.NET Framework Data Provider for mySAP Business Suite**.</span></span> <span data-ttu-id="0a192-116">對話方塊會列出不同的連線參數，以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="0a192-116">The dialog box lists the different connection parameters to connect to an SAP system.</span></span> <span data-ttu-id="0a192-117">一般連接字串來連接到 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要：</span><span class="sxs-lookup"><span data-stu-id="0a192-117">A typical connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires:</span></span>  
  
   - <span data-ttu-id="0a192-118">輸入連接的連接參數。</span><span class="sxs-lookup"><span data-stu-id="0a192-118">The connection parameters for a connection type.</span></span> <span data-ttu-id="0a192-119">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援連接類型 A、 B 和 d。若要連接到 SAP 系統必須提供連接參數的任何*一個*一種連線類型。</span><span class="sxs-lookup"><span data-stu-id="0a192-119">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports connection types A, B, and D. To connect to an SAP system you must provide connection parameters for any *one* of these connection types.</span></span> <span data-ttu-id="0a192-120">比方說，針對 A 的連線類型，您必須提供名稱的應用程式伺服器主機和系統編號。</span><span class="sxs-lookup"><span data-stu-id="0a192-120">For example, for connection type A, you must provide the name of the application server host and the system number.</span></span>  
  
   - <span data-ttu-id="0a192-121">若要連接到 SAP 系統，例如使用者名稱和密碼登入資訊。</span><span class="sxs-lookup"><span data-stu-id="0a192-121">The login information to connect to an SAP system such as username and password.</span></span>  
  
     <span data-ttu-id="0a192-122">如需有關連接到 SAP 系統使用的連接字串[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱 <<c2> [ 了解 Data Provider for SAP 連接字串](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="0a192-122">For more information about the connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Read about Data Provider for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
     <span data-ttu-id="0a192-123">在 **選擇資料來源**對話方塊方塊中，指定：</span><span class="sxs-lookup"><span data-stu-id="0a192-123">In the **Choose a Data Source** dialog box, specify:</span></span>  
  
   - <span data-ttu-id="0a192-124">任何一種連線類型連線參數。</span><span class="sxs-lookup"><span data-stu-id="0a192-124">The connection parameters for any one connection type.</span></span>  
  
   - <span data-ttu-id="0a192-125">要連接到 SAP 系統的登入資訊。</span><span class="sxs-lookup"><span data-stu-id="0a192-125">The login information to connect to an SAP system.</span></span>  
  
   - <span data-ttu-id="0a192-126">是否要啟用 SAP GUI 偵錯。</span><span class="sxs-lookup"><span data-stu-id="0a192-126">Whether you want to enable SAP GUI debugging.</span></span>  
  
   - <span data-ttu-id="0a192-127">是否要使用 RFC SDK 追蹤。</span><span class="sxs-lookup"><span data-stu-id="0a192-127">Whether you want to use RFC SDK tracing.</span></span>  
  
     <span data-ttu-id="0a192-128">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="0a192-128">Click **Next**.</span></span>  
  
5. <span data-ttu-id="0a192-129">在 [**選擇目的地**] 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="0a192-129">In the **Choose a Destination** dialog box:</span></span>  
  
   1.  <span data-ttu-id="0a192-130">從**目的地**下拉式清單中，選取**SQL Native Client**。</span><span class="sxs-lookup"><span data-stu-id="0a192-130">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
   2.  <span data-ttu-id="0a192-131">從**伺服器名稱**下拉式清單中，選取 SQL server 名稱。</span><span class="sxs-lookup"><span data-stu-id="0a192-131">From the **Server name** drop-down list, select a SQL server name.</span></span>  
  
   3.  <span data-ttu-id="0a192-132">選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="0a192-132">Select an authentication mode.</span></span>  
  
   4.  <span data-ttu-id="0a192-133">從**資料庫**下拉式清單中，選取您要匯入 SAP 資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a192-133">From the **Database** drop-down list, select the database to which you want to import the SAP table.</span></span>  
  
   5.  <span data-ttu-id="0a192-134">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="0a192-134">Click **Next**.</span></span>  
  
6. <span data-ttu-id="0a192-135">在 [**指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="0a192-135">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option and click **Next**.</span></span>  
  
7. <span data-ttu-id="0a192-136">在 **提供來源查詢**對話方塊方塊中，指定選取的查詢，以篩選要匯入到 SQL Server 的資料。</span><span class="sxs-lookup"><span data-stu-id="0a192-136">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="0a192-137">如需詳細資訊，選取 「 了解文法查詢[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="0a192-137">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span>  
  
    <span data-ttu-id="0a192-138">按一下 **剖析**按鈕以驗證查詢，並按一下 **確定**快顯對話方塊方塊中。</span><span class="sxs-lookup"><span data-stu-id="0a192-138">Click the **Parse** button to validate the query and click **OK** in the pop-up dialog box.</span></span> <span data-ttu-id="0a192-139">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="0a192-139">Click **Next**.</span></span>  
  
8. <span data-ttu-id="0a192-140">在 **選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="0a192-140">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="0a192-141">來源是您指定要從 SAP 擷取資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="0a192-141">The source is the query you specified to retrieve data from SAP.</span></span> <span data-ttu-id="0a192-142">目的地是將 SQL Server 資料庫中建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="0a192-142">The destination is the table that will be created in the SQL Server database.</span></span>  
  
9. <span data-ttu-id="0a192-143">精靈會建立預設的對應來源與目的地之間資料表欄位。</span><span class="sxs-lookup"><span data-stu-id="0a192-143">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="0a192-144">不過，您可以變更對應，根據您的需求。</span><span class="sxs-lookup"><span data-stu-id="0a192-144">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="0a192-145">若要變更欄位對應，請按一下**編輯對應**。</span><span class="sxs-lookup"><span data-stu-id="0a192-145">To change the field mappings, click **Edit Mappings**.</span></span>  
  
     <span data-ttu-id="0a192-146">![SAP 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")</span><span class="sxs-lookup"><span data-stu-id="0a192-146">![Column mappings between SAP and SQL tables](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")</span></span>  
  
10. <span data-ttu-id="0a192-147">在 [**資料行對應**] 對話方塊中，您可以：</span><span class="sxs-lookup"><span data-stu-id="0a192-147">In the **Column Mappings** dialog box, you can:</span></span>  
  
    -   <span data-ttu-id="0a192-148">變更目的地資料表中的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a192-148">Change the names of columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="0a192-149">忽略特定的目的地資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="0a192-149">Ignore certain columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="0a192-150">變更目的地資料表中的欄位資料類型。</span><span class="sxs-lookup"><span data-stu-id="0a192-150">Change the data type for fields in destination table.</span></span>  
  
    -   <span data-ttu-id="0a192-151">變更其他欄位屬性，例如可為 null，大小、 有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="0a192-151">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
    -   <span data-ttu-id="0a192-152">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="0a192-152">Click **OK**.</span></span>  
  
11. <span data-ttu-id="0a192-153">在 **選取來源資料表和檢視表** 對話方塊中，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="0a192-153">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
12. <span data-ttu-id="0a192-154">在 **完成精靈**對話方塊方塊中，檢閱精靈將會執行，並按一下的動作的摘要**完成**。</span><span class="sxs-lookup"><span data-stu-id="0a192-154">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and click **Finish**.</span></span>  
  
13. <span data-ttu-id="0a192-155">在 [**正在執行作業**] 對話方塊中，精靈會啟動執行工作，以從 SAP 將資訊匯入到 SQL Server 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="0a192-155">In the **Performing Operation** dialog box, the wizard starts executing tasks to import the information from SAP into a SQL Server database table.</span></span> <span data-ttu-id="0a192-156">每個工作的狀態會顯示在精靈中。</span><span class="sxs-lookup"><span data-stu-id="0a192-156">The status for each task is displayed in the wizard.</span></span>  
  
14. <span data-ttu-id="0a192-157">所有工作都成功都執行之後，請按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="0a192-157">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="0a192-158">如果工作失敗，請參閱對應的錯誤訊息、 修正問題，並返回精靈。</span><span class="sxs-lookup"><span data-stu-id="0a192-158">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
15. <span data-ttu-id="0a192-159">精靈會將您的整合服務專案中的 SSIS 套件。</span><span class="sxs-lookup"><span data-stu-id="0a192-159">The wizard adds an SSIS package to your Integration Service project.</span></span> <span data-ttu-id="0a192-160">儲存整合服務專案。</span><span class="sxs-lookup"><span data-stu-id="0a192-160">Save the Integration Service project.</span></span>  
  
## <a name="running-the-ssis-package"></a><span data-ttu-id="0a192-161">執行 SSIS 套件</span><span class="sxs-lookup"><span data-stu-id="0a192-161">Running the SSIS Package</span></span>  
 <span data-ttu-id="0a192-162">封裝建立後的整合服務專案中，您可以執行其 SAP 系統的資料匯入到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a192-162">Once the package is created within an Integration Service project, you can execute it to import data from an SAP system into a SQL Server database.</span></span> <span data-ttu-id="0a192-163">執行下列步驟來執行封裝來匯入 SAP 資料。</span><span class="sxs-lookup"><span data-stu-id="0a192-163">Perform the following steps to import SAP data by executing the package.</span></span>  
  
#### <a name="to-run-the-package-from-visual-studio"></a><span data-ttu-id="0a192-164">若要從 Visual Studio 執行封裝</span><span class="sxs-lookup"><span data-stu-id="0a192-164">To run the package from Visual Studio</span></span>  
  
1. <span data-ttu-id="0a192-165">瀏覽至 [方案總管] 中的 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="0a192-165">Navigate to the SSIS package in the Solution Explorer.</span></span>  
  
2. <span data-ttu-id="0a192-166">以滑鼠右鍵按一下封裝名稱，然後選取**執行封裝**。</span><span class="sxs-lookup"><span data-stu-id="0a192-166">Right-click the package name and select **Execute Package**.</span></span>  
  
   <span data-ttu-id="0a192-167">如需執行封裝的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=94972 ](http://go.microsoft.com/fwlink/?LinkId=94972)。</span><span class="sxs-lookup"><span data-stu-id="0a192-167">For more information about running packages, see [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span></span> <span data-ttu-id="0a192-168">任何其他資訊與 SSIS 封裝，請參閱[ http://go.microsoft.com/fwlink/?LinkId=94973 ](http://go.microsoft.com/fwlink/?LinkId=94973)。</span><span class="sxs-lookup"><span data-stu-id="0a192-168">For any other information related to SSIS packages, see [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span></span>  
  
## <a name="verifying-the-results"></a><span data-ttu-id="0a192-169">驗證結果</span><span class="sxs-lookup"><span data-stu-id="0a192-169">Verifying the Results</span></span>  
 <span data-ttu-id="0a192-170">執行封裝之後, 您必須登入 SQL Server，並瀏覽至要匯入 SAP 資料的資料庫來驗證結果。</span><span class="sxs-lookup"><span data-stu-id="0a192-170">After executing the package, you must verify the results by logging on to the SQL Server and navigating to the database to which the SAP data is imported.</span></span> <span data-ttu-id="0a192-171">執行封裝應該已在目的地資料庫中建立資料表，以填入 SAP 資料表中的值。</span><span class="sxs-lookup"><span data-stu-id="0a192-171">Executing the package should have created a table in destination database and populated with the values from the SAP table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a192-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a192-172">See Also</span></span>  
 [<span data-ttu-id="0a192-173">搭配使用 Data Provider for SAP 與 SSIS</span><span class="sxs-lookup"><span data-stu-id="0a192-173">Use the Data Provider for SAP with SSIS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)