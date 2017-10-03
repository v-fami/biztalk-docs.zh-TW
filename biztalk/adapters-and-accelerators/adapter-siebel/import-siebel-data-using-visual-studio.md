---
title: "使用 Visual Studio 的 Siebel 資料匯入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSIS
- Data Provider for Siebel, importing Siebel data by using Visual Studio
ms.assetid: 33701361-eca2-4795-a5e0-78162a98e9ba
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0671459b39462422768e42e18bf16336a469f43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="import-siebel-data-using-visual-studio"></a><span data-ttu-id="04a32-102">使用 Visual Studio 的 Siebel 資料匯入</span><span class="sxs-lookup"><span data-stu-id="04a32-102">Import Siebel Data Using Visual Studio</span></span>
<span data-ttu-id="04a32-103">本節提供有關如何使用 Microsoft 的資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Siebel 系統的資料匯入至 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="04a32-103">This section provides information about how to use Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to import data from a Siebel system into a SQL Server database.</span></span> <span data-ttu-id="04a32-104">它也會提供有關如何建立和執行 SSIS 封裝，此資料匯入的指示。</span><span class="sxs-lookup"><span data-stu-id="04a32-104">It also provides instructions on how to create and execute an SSIS package to import this data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="04a32-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="04a32-105">Prerequisites</span></span>  
 <span data-ttu-id="04a32-106">然後再執行本主題提供的程序，請確定：</span><span class="sxs-lookup"><span data-stu-id="04a32-106">Before performing the procedures provided in this topic, make sure:</span></span>  
  
-   <span data-ttu-id="04a32-107">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="04a32-107">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] is installed on the computer.</span></span>  
  
-   <span data-ttu-id="04a32-108">Microsoft[!INCLUDE[vs2010](../../includes/vs2010-md.md)]安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="04a32-108">Microsoft [!INCLUDE[vs2010](../../includes/vs2010-md.md)] is installed on the computer.</span></span>  
  
## <a name="importing-data-by-using-visual-studio"></a><span data-ttu-id="04a32-109">使用 Visual Studio 匯入資料</span><span class="sxs-lookup"><span data-stu-id="04a32-109">Importing Data by Using Visual Studio</span></span>  
 <span data-ttu-id="04a32-110">執行下列步驟來匯入資料使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="04a32-110">Perform the following steps to import data using [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
#### <a name="to-import-data-by-using-visual-studio"></a><span data-ttu-id="04a32-111">若要使用 Visual Studio 來匯入資料</span><span class="sxs-lookup"><span data-stu-id="04a32-111">To import data by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="04a32-112">啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]建立整合服務專案。</span><span class="sxs-lookup"><span data-stu-id="04a32-112">Start [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and create an Integration Service project.</span></span>  
  
2.  <span data-ttu-id="04a32-113">從**專案**功能表上，選取**SSIS 匯入和匯出精靈**。</span><span class="sxs-lookup"><span data-stu-id="04a32-113">From the **Project** menu, select **SSIS Import and Export Wizard**.</span></span> <span data-ttu-id="04a32-114">這樣會啟動 SQL Server 匯入和匯出精靈。</span><span class="sxs-lookup"><span data-stu-id="04a32-114">This starts the SQL Server Import and Export Wizard.</span></span>  
  
3.  <span data-ttu-id="04a32-115">閱讀 [歡迎] 畫面上的資訊，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="04a32-115">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="04a32-116">在**選擇資料來源**對話方塊中，從**資料來源**下拉式選單**for Siebel eBusiness 應用程式的.NET Framework Data Provider**。</span><span class="sxs-lookup"><span data-stu-id="04a32-116">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list **.NET Framework Data Provider for Siebel eBusiness Applications**.</span></span> <span data-ttu-id="04a32-117">指定的不同連接屬性的值[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]連接字串。</span><span class="sxs-lookup"><span data-stu-id="04a32-117">Specify values for the different connection properties for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] connection string.</span></span> <span data-ttu-id="04a32-118">如需連接字串屬性的詳細資訊，請參閱[Siebel 連接字串的資料提供者內容](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="04a32-118">For more information about the connection string properties, see [Data provider properties for the Siebel connection string](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span></span>  
  
     <span data-ttu-id="04a32-119">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="04a32-119">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="04a32-120">在**選擇目的地**對話方塊：</span><span class="sxs-lookup"><span data-stu-id="04a32-120">In the **Choose a Destination** dialog box:</span></span>  
  
    1.  <span data-ttu-id="04a32-121">從**目的地**下拉式清單中，選取**SQL Native Client**。</span><span class="sxs-lookup"><span data-stu-id="04a32-121">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
    2.  <span data-ttu-id="04a32-122">從**伺服器名稱**下拉式清單中，選取 SQL Server 名稱。</span><span class="sxs-lookup"><span data-stu-id="04a32-122">From the **Server name** drop-down list, select a SQL Server name.</span></span>  
  
    3.  <span data-ttu-id="04a32-123">選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="04a32-123">Select an authentication mode.</span></span>  
  
    4.  <span data-ttu-id="04a32-124">從**資料庫**下拉式清單中，選取您要匯入 Siebel 資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="04a32-124">From the **Database** drop-down list, select the database to which you want to import the Siebel table.</span></span>  
  
    5.  <span data-ttu-id="04a32-125">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="04a32-125">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="04a32-126">在**指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項。</span><span class="sxs-lookup"><span data-stu-id="04a32-126">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option.</span></span>  
  
7.  <span data-ttu-id="04a32-127">在**提供來源查詢**對話方塊方塊中，指定 SELECT 查詢來篩選要匯入 SQL Server 的資料。</span><span class="sxs-lookup"><span data-stu-id="04a32-127">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="04a32-128">如需文法的 SELECT 查詢[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，請參閱[Siebel 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)。</span><span class="sxs-lookup"><span data-stu-id="04a32-128">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], see [Syntax for a SELECT Statement in Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span></span>  
  
8.  <span data-ttu-id="04a32-129">若要驗證查詢，請按一下**剖析**按鈕，再按一下**確定**在快顯對話方塊中，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="04a32-129">To validate the query, click the **Parse** button, click **OK** in the pop-up dialog box, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="04a32-130">在**選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="04a32-130">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="04a32-131">來源是您指定從 Siebel 擷取資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="04a32-131">The source is the query you specified to retrieve data from Siebel.</span></span> <span data-ttu-id="04a32-132">目的地會將 SQL Server 資料庫中建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="04a32-132">The destination will be the table that will be created in the SQL Server database.</span></span>  
  
10. <span data-ttu-id="04a32-133">精靈會建立預設的對應來源與目的地之間資料表欄位。</span><span class="sxs-lookup"><span data-stu-id="04a32-133">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="04a32-134">不過，您可以變更對應，根據您的需求。</span><span class="sxs-lookup"><span data-stu-id="04a32-134">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="04a32-135">若要變更欄位對應，請按一下**編輯對應**。</span><span class="sxs-lookup"><span data-stu-id="04a32-135">To change the field mappings, click **Edit Mappings**.</span></span>  
  
11. <span data-ttu-id="04a32-136">在**資料行對應**對話方塊中，您可以：</span><span class="sxs-lookup"><span data-stu-id="04a32-136">In the **Column Mappings** dialog box, you can:</span></span>  
  
    -   <span data-ttu-id="04a32-137">變更目的地資料表中的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="04a32-137">Change the names of columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="04a32-138">忽略特定資料行與目的地資料表中。</span><span class="sxs-lookup"><span data-stu-id="04a32-138">Ignore certain columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="04a32-139">變更目的地資料表中的欄位的資料類型。</span><span class="sxs-lookup"><span data-stu-id="04a32-139">Change the data type for fields in destination table.</span></span>  
  
    -   <span data-ttu-id="04a32-140">變更其他欄位屬性，例如可為 null，大小、 精確度和小數位數。</span><span class="sxs-lookup"><span data-stu-id="04a32-140">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
    -   <span data-ttu-id="04a32-141">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="04a32-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="04a32-142">![Siebel 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span><span class="sxs-lookup"><span data-stu-id="04a32-142">![Column mappings between Siebel and SQL table](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span></span>  
  
12. <span data-ttu-id="04a32-143">在**選取來源資料表和檢視**對話方塊中，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="04a32-143">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
13. <span data-ttu-id="04a32-144">在**完成精靈**對話方塊方塊中，檢閱精靈將會執行，然後再按一下動作的摘要**完成**。</span><span class="sxs-lookup"><span data-stu-id="04a32-144">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and then click **Finish**.</span></span>  
  
14. <span data-ttu-id="04a32-145">在**執行運算**對話方塊中，精靈會啟動執行工作，以從 Siebel 的資訊匯入到 SQL Server 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="04a32-145">In the **Performing Operations** dialog box, the wizard starts executing tasks to import the information from Siebel into a SQL Server database table.</span></span> <span data-ttu-id="04a32-146">每個工作的狀態會顯示在精靈中。</span><span class="sxs-lookup"><span data-stu-id="04a32-146">The status for each task is displayed in the wizard.</span></span>  
  
15. <span data-ttu-id="04a32-147">所有工作都執行成功之後，請按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="04a32-147">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="04a32-148">如果工作失敗，請參閱對應的錯誤訊息、 修正問題，和重新執行精靈。</span><span class="sxs-lookup"><span data-stu-id="04a32-148">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
16. <span data-ttu-id="04a32-149">精靈會新增至您的整合服務專案的 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="04a32-149">The wizard adds an SSIS package to your Integration Service project.</span></span> <span data-ttu-id="04a32-150">儲存整合服務專案。</span><span class="sxs-lookup"><span data-stu-id="04a32-150">Save the Integration Service project.</span></span>  
  
## <a name="running-the-ssis-package"></a><span data-ttu-id="04a32-151">執行 SSIS 封裝</span><span class="sxs-lookup"><span data-stu-id="04a32-151">Running the SSIS Package</span></span>  
 <span data-ttu-id="04a32-152">一旦在整合服務專案中建立封裝時，您可以執行它 Siebel 系統的資料匯入至 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="04a32-152">Once the package is created within an Integration Service project, you can execute it to import data from a Siebel system into a SQL Server database.</span></span> <span data-ttu-id="04a32-153">執行下列步驟來匯入的 Siebel 資料執行封裝。</span><span class="sxs-lookup"><span data-stu-id="04a32-153">Perform the following steps to import Siebel data by executing the package.</span></span>  
  
#### <a name="to-run-the-package-from-visual-studio"></a><span data-ttu-id="04a32-154">若要從 Visual Studio 執行封裝</span><span class="sxs-lookup"><span data-stu-id="04a32-154">To run the package from Visual Studio</span></span>  
  
1.  <span data-ttu-id="04a32-155">瀏覽至 [方案總管] 中的 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="04a32-155">Navigate to the SSIS package in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="04a32-156">以滑鼠右鍵按一下封裝名稱，然後選取**執行封裝**。</span><span class="sxs-lookup"><span data-stu-id="04a32-156">Right-click the package name, and then select **Execute Package**.</span></span>  
  
 <span data-ttu-id="04a32-157">執行封裝的詳細資訊，請參閱 < 執行封裝 >，網址[http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972)。</span><span class="sxs-lookup"><span data-stu-id="04a32-157">For more information about running packages, see "Running Packages" at [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span></span> <span data-ttu-id="04a32-158">針對任何其他資訊與 SSIS 封裝，查看 「 封裝使用說明主題 (SSIS) 」 [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973)。</span><span class="sxs-lookup"><span data-stu-id="04a32-158">For any other information related to SSIS packages, see "Package How-to Topics (SSIS)" at [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span></span>  
  
## <a name="verifying-the-results"></a><span data-ttu-id="04a32-159">驗證結果</span><span class="sxs-lookup"><span data-stu-id="04a32-159">Verifying the Results</span></span>  
 <span data-ttu-id="04a32-160">執行封裝之後, 您必須確認登入 SQL Server，並巡覽至資料庫的 Siebel 資料匯入的結果。</span><span class="sxs-lookup"><span data-stu-id="04a32-160">After executing the package, you must verify the results by logging on to the SQL Server and navigating to the database to which the Siebel data is imported.</span></span> <span data-ttu-id="04a32-161">執行封裝應已建立了資料表目的地資料庫中。</span><span class="sxs-lookup"><span data-stu-id="04a32-161">Executing the package should have created a table in the destination database.</span></span> <span data-ttu-id="04a32-162">Siebel 資料表中的值來擴展這個資料表。</span><span class="sxs-lookup"><span data-stu-id="04a32-162">This table should be populated with the values from the Siebel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a32-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04a32-163">See Also</span></span>  
 [<span data-ttu-id="04a32-164">Siebel 與 SSIS 中使用資料提供者</span><span class="sxs-lookup"><span data-stu-id="04a32-164">Use the Data Provider for Siebel with SSIS</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)