---
title: 匯入 Siebel 資料使用 SQL Server Management Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio, importing data by using
- how to, import data by using SQL Server Management Studio
ms.assetid: 67da7f7b-37ea-4a31-89ef-a9f6974ff976
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdcc6140bb50ebca299cd58f78063be8f108dea4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013175"
---
# <a name="import-siebel-data-using-sql-server-management-studio"></a><span data-ttu-id="5b500-102">匯入使用 SQL Server Management Studio 的 Siebel 資料</span><span class="sxs-lookup"><span data-stu-id="5b500-102">Import Siebel Data Using SQL Server Management Studio</span></span>
<span data-ttu-id="5b500-103">本節提供如何使用 SQL Server Management Studio Siebel 系統的資料匯入到 SQL Server 資料庫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5b500-103">This section provides information about how to use SQL Server Management Studio to import data from a Siebel system into a SQL Server database.</span></span> <span data-ttu-id="5b500-104">它也會提供有關如何建立和執行 SSIS 套件，此資料匯入的指示。</span><span class="sxs-lookup"><span data-stu-id="5b500-104">It also provides instructions on how to create and execute an SSIS package to import this data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5b500-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="5b500-105">Prerequisites</span></span>  
 <span data-ttu-id="5b500-106">然後再執行本主題所提供的程序，請確定：</span><span class="sxs-lookup"><span data-stu-id="5b500-106">Before performing the procedures provided in this topic, make sure:</span></span>  
  
- <span data-ttu-id="5b500-107">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="5b500-107">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] is installed on the computer.</span></span>  
  
- <span data-ttu-id="5b500-108">在電腦上安裝 SQL Server Business Intelligence Development Studio。</span><span class="sxs-lookup"><span data-stu-id="5b500-108">SQL Server Business Intelligence Development Studio is installed on the computer.</span></span>  
  
## <a name="importing-data-by-using-sql-server-management-studio"></a><span data-ttu-id="5b500-109">使用 SQL Server Management Studio 匯入資料</span><span class="sxs-lookup"><span data-stu-id="5b500-109">Importing Data by Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="5b500-110">執行下列步驟將資料匯入從 Siebel 系統使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]與 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="5b500-110">Perform the following steps to import data from Siebel system using [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] with SQL Server Management Studio.</span></span>  
  
#### <a name="to-import-data-by-using-sql-server-management-studio"></a><span data-ttu-id="5b500-111">若要使用 SQL Server Management Studio 匯入資料</span><span class="sxs-lookup"><span data-stu-id="5b500-111">To import data by using SQL Server Management Studio</span></span>  
  
1. <span data-ttu-id="5b500-112">啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="5b500-112">Start the SQL Server Management Studio.</span></span>  
  
2. <span data-ttu-id="5b500-113">在 **連接到伺服器**對話方塊方塊中，指定的值，以連接到 SQL Server 資料庫，然後按一下**Connect**。</span><span class="sxs-lookup"><span data-stu-id="5b500-113">In the **Connect to Server** dialog box, specify the values to connect to a SQL Server database, and then click **Connect**.</span></span> <span data-ttu-id="5b500-114">此時會開啟 Microsoft SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="5b500-114">Microsoft SQL Server Management Studio opens.</span></span>  
  
3. <span data-ttu-id="5b500-115">在 物件總管 中，展開 SQL Server 名稱、 依序展開**資料庫**，以滑鼠右鍵按一下資料庫，其中您將會將資料表匯出來自 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="5b500-115">In Object Explorer, expand the SQL Server name, expand **Databases**, and right-click the database into which you will be exporting the tables from the Siebel system.</span></span> <span data-ttu-id="5b500-116">從操作功能表，指向**任務**，然後按一下**匯入資料**。</span><span class="sxs-lookup"><span data-stu-id="5b500-116">From the context menu, point to **Tasks**, and then click **Import Data**.</span></span> <span data-ttu-id="5b500-117">這會啟動 SQL Server 匯入和匯出精靈。</span><span class="sxs-lookup"><span data-stu-id="5b500-117">This starts the SQL Server Import and Export Wizard.</span></span>  
  
4. <span data-ttu-id="5b500-118">閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="5b500-118">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
5. <span data-ttu-id="5b500-119">在 [**選擇資料來源**] 對話方塊中，從**資料來源**下拉式清單中，選取 **.NET Framework Data Provider for Siebel eBusiness 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="5b500-119">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list, select **.NET Framework Data Provider for Siebel eBusiness Applications**.</span></span> <span data-ttu-id="5b500-120">指定不同的連接屬性的值[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]連接字串。</span><span class="sxs-lookup"><span data-stu-id="5b500-120">Specify values for the different connection properties for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] connection string.</span></span> <span data-ttu-id="5b500-121">如需連接字串屬性的詳細資訊，請參閱[Siebel 連接字串的資料提供者屬性](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="5b500-121">For more information about the connection string properties, see [Data provider properties for the Siebel connection string](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span></span>  
  
    <span data-ttu-id="5b500-122">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="5b500-122">Click **Next**.</span></span>  
  
6. <span data-ttu-id="5b500-123">在 [**選擇目的地**] 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="5b500-123">In the **Choose a Destination** dialog box:</span></span>  
  
   1.  <span data-ttu-id="5b500-124">從**目的地**下拉式清單中，選取**SQL Native Client**。</span><span class="sxs-lookup"><span data-stu-id="5b500-124">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
   2.  <span data-ttu-id="5b500-125">從**伺服器名稱**下拉式清單中，選取 SQL Server 名稱。</span><span class="sxs-lookup"><span data-stu-id="5b500-125">From the **Server name** drop-down list, select a SQL Server name.</span></span>  
  
   3.  <span data-ttu-id="5b500-126">選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="5b500-126">Select an authentication mode.</span></span>  
  
   4.  <span data-ttu-id="5b500-127">從**資料庫**下拉式清單中，選取您要匯入 Siebel 的資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="5b500-127">From the **Database** drop-down list, select the database to which you want to import the Siebel table.</span></span>  
  
   5.  <span data-ttu-id="5b500-128">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="5b500-128">Click **Next**.</span></span>  
  
7. <span data-ttu-id="5b500-129">在 **指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項。</span><span class="sxs-lookup"><span data-stu-id="5b500-129">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option.</span></span>  
  
8. <span data-ttu-id="5b500-130">在 **提供來源查詢**對話方塊方塊中，指定選取的查詢，以篩選要匯入到 SQL Server 的資料。</span><span class="sxs-lookup"><span data-stu-id="5b500-130">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="5b500-131">如需詳細資訊，選取 「 了解文法查詢[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，請參閱 < [Siebel 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)。</span><span class="sxs-lookup"><span data-stu-id="5b500-131">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], see [Syntax for a SELECT Statement in Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span></span>  
  
    <span data-ttu-id="5b500-132">按一下 [**剖析**按鈕以驗證查詢中，按一下 **[確定]** 中的快顯對話方塊中，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="5b500-132">Click the **Parse** button to validate the query, click **OK** in the pop-up dialog box, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="5b500-133">在 **選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="5b500-133">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="5b500-134">來源是您指定用來擷取 Siebel 的資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="5b500-134">The source is the query you specified to retrieve data from Siebel.</span></span> <span data-ttu-id="5b500-135">目的地是將 SQL Server 資料庫中建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="5b500-135">The destination is the table that will be created in the SQL Server database.</span></span>  
  
10. <span data-ttu-id="5b500-136">精靈會建立預設的對應來源與目的地之間資料表欄位。</span><span class="sxs-lookup"><span data-stu-id="5b500-136">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="5b500-137">不過，您可以變更對應，根據您的需求。</span><span class="sxs-lookup"><span data-stu-id="5b500-137">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="5b500-138">若要變更欄位對應，請按一下**編輯對應**。</span><span class="sxs-lookup"><span data-stu-id="5b500-138">To change the field mappings, click **Edit Mappings**.</span></span>  
  
     <span data-ttu-id="5b500-139">![Siebel 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span><span class="sxs-lookup"><span data-stu-id="5b500-139">![Column mappings between Siebel and SQL table](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span></span>  
  
11. <span data-ttu-id="5b500-140">在 [**資料行對應**] 對話方塊中，您可以：</span><span class="sxs-lookup"><span data-stu-id="5b500-140">In the **Column Mappings** dialog box, you can:</span></span>  
  
    -   <span data-ttu-id="5b500-141">變更目的地資料表中的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b500-141">Change the names of columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="5b500-142">忽略特定的目的地資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="5b500-142">Ignore certain columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="5b500-143">變更目的地資料表中的欄位資料類型。</span><span class="sxs-lookup"><span data-stu-id="5b500-143">Change the data type for fields in destination table.</span></span>  
  
    -   <span data-ttu-id="5b500-144">變更其他欄位屬性，例如可為 null，大小、 有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="5b500-144">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
         <span data-ttu-id="5b500-145">完成後，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="5b500-145">When you are finished, click **OK**.</span></span>  
  
12. <span data-ttu-id="5b500-146">在 **選取來源資料表和檢視表** 對話方塊中，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="5b500-146">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
13. <span data-ttu-id="5b500-147">在 [**儲存並執行套件**] 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="5b500-147">In the **Save and Execute Package** dialog box:</span></span>  
  
    - <span data-ttu-id="5b500-148">選取 **立即執行**核取方塊以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="5b500-148">Select the **Execute immediately** check box to execute the query.</span></span>  
  
    - <span data-ttu-id="5b500-149">選取 **儲存 SSIS 封裝**核取方塊，將查詢儲存為封裝，並稍後再執行它。</span><span class="sxs-lookup"><span data-stu-id="5b500-149">Select the **Save SSIS Package** check box to save the query as a package and execute it later.</span></span> <span data-ttu-id="5b500-150">如果您選擇儲存封裝，您也必須指定是否要將封裝儲存在 SQL Server 或檔案系統。</span><span class="sxs-lookup"><span data-stu-id="5b500-150">If you chose to save the package, you must also specify whether you want to save the package in the SQL Server or the file system.</span></span>  
  
    - <span data-ttu-id="5b500-151">從**套件保護等級**下拉式清單中，選取封裝層級的保護，並指定認證要求。</span><span class="sxs-lookup"><span data-stu-id="5b500-151">From the **Package protection level** drop-down list, select a protection level for the package and specify credentials where required.</span></span>  
  
    - <span data-ttu-id="5b500-152">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="5b500-152">Click **Next**.</span></span>  
  
      <span data-ttu-id="5b500-153">如果您選擇儲存封裝，請繼續下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="5b500-153">If you chose to save the package, proceed to the next step.</span></span> <span data-ttu-id="5b500-154">否則，請跳至步驟 15。</span><span class="sxs-lookup"><span data-stu-id="5b500-154">Otherwise, skip to step 15.</span></span>  
  
14. <span data-ttu-id="5b500-155">在 **儲存 SSIS 封裝**對話方塊方塊中，指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="5b500-155">In the **Save SSIS Package** dialog box, specify the following:</span></span>  
  
    -   <span data-ttu-id="5b500-156">封裝的名稱</span><span class="sxs-lookup"><span data-stu-id="5b500-156">The name for the package</span></span>  
  
    -   <span data-ttu-id="5b500-157">套件描述</span><span class="sxs-lookup"><span data-stu-id="5b500-157">The description for the package</span></span>  
  
    -   <span data-ttu-id="5b500-158">如果您選擇將封裝儲存至 SQL Server，請選取 從 SQL Server**伺服器名稱**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="5b500-158">If you chose to save the package to a SQL Server, select a SQL Server from the **Server name** drop-down list.</span></span>  
  
    -   <span data-ttu-id="5b500-159">如果您選擇將封裝儲存至檔案系統中，指定的名稱和位置中的檔案**檔案名**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="5b500-159">If you chose to save the package to the file system, specify the name and location of the file in the **File name** text box.</span></span>  
  
         <span data-ttu-id="5b500-160">完成後，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="5b500-160">When you are finished, click **Next**.</span></span>  
  
15. <span data-ttu-id="5b500-161">在 **完成精靈**對話方塊方塊中，檢閱精靈將會執行，然後再按一下的動作的摘要**完成**。</span><span class="sxs-lookup"><span data-stu-id="5b500-161">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and then click **Finish**.</span></span>  
  
16. <span data-ttu-id="5b500-162">在 [**正在執行作業**] 對話方塊中，精靈會啟動執行工作，以從 Siebel 將資訊匯入到 SQL Server 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="5b500-162">In the **Performing Operations** dialog box, the wizard starts executing tasks to import the information from Siebel into a SQL Server database table.</span></span> <span data-ttu-id="5b500-163">每個工作的狀態會顯示在精靈中。</span><span class="sxs-lookup"><span data-stu-id="5b500-163">The status for each task is displayed in the wizard.</span></span>  
  
17. <span data-ttu-id="5b500-164">所有工作都成功都執行之後，請按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="5b500-164">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="5b500-165">如果工作失敗，請參閱對應的錯誤訊息、 修正問題，並返回精靈。</span><span class="sxs-lookup"><span data-stu-id="5b500-165">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
## <a name="running-the-ssis-package"></a><span data-ttu-id="5b500-166">執行 SSIS 套件</span><span class="sxs-lookup"><span data-stu-id="5b500-166">Running the SSIS Package</span></span>  
 <span data-ttu-id="5b500-167">如果您選擇儲存 SSIS 封裝，您可以執行它來擷取 Siebel 系統中的最新的資訊。</span><span class="sxs-lookup"><span data-stu-id="5b500-167">If you chose to save the SSIS package, you can run it to retrieve the most recent information from the Siebel system.</span></span> <span data-ttu-id="5b500-168">本節提供如何執行封裝，如果您選擇將它儲存至檔案系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5b500-168">This section provides information about how to run the package if you chose to save it to the file system.</span></span>  
  
#### <a name="to-run-the-package-from-windows-explorer"></a><span data-ttu-id="5b500-169">若要從 Windows 檔案總管中執行封裝</span><span class="sxs-lookup"><span data-stu-id="5b500-169">To run the package from Windows Explorer</span></span>  
  
1. <span data-ttu-id="5b500-170">從**Windows 檔案總管**，瀏覽至您儲存封裝的位置，按兩下封裝。</span><span class="sxs-lookup"><span data-stu-id="5b500-170">From **Windows Explorer**, navigate to the location where you saved the package, and double-click the package.</span></span>  
  
2. <span data-ttu-id="5b500-171">在 **[執行封裝公用程式]** 對話方塊中，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="5b500-171">In the **Execute Package Utility** dialog box, click **Execute**.</span></span> <span data-ttu-id="5b500-172">**封裝執行進度** 對話方塊中顯示的不同工作的進度。</span><span class="sxs-lookup"><span data-stu-id="5b500-172">The **Package Execution Progress** dialog box displays the progress of the different tasks.</span></span>  
  
3. <span data-ttu-id="5b500-173">所有工作都成功都執行之後，請按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="5b500-173">After all the tasks are successfully executed, click **Close**.</span></span>  
  
4. <span data-ttu-id="5b500-174">在 **[執行封裝公用程式]** 對話方塊中，按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="5b500-174">In the **Execute Package Utility** dialog box, click **Close**.</span></span>  
  
   <span data-ttu-id="5b500-175">執行封裝的詳細資訊，請參閱 < 執行封裝 >，網址[ http://go.microsoft.com/fwlink/?LinkId=94972 ](http://go.microsoft.com/fwlink/?LinkId=94972)。</span><span class="sxs-lookup"><span data-stu-id="5b500-175">For more information about running packages, see "Running Packages" at [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span></span> <span data-ttu-id="5b500-176">針對任何其他資訊與 SSIS 封裝，查看 「 封裝使用說明主題 (SSIS) 」 [ http://go.microsoft.com/fwlink/?LinkId=94973 ](http://go.microsoft.com/fwlink/?LinkId=94973)。</span><span class="sxs-lookup"><span data-stu-id="5b500-176">For any other information related to SSIS packages, see "Package How-to Topics (SSIS)" at [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span></span>  
  
## <a name="verifying-the-results"></a><span data-ttu-id="5b500-177">驗證結果</span><span class="sxs-lookup"><span data-stu-id="5b500-177">Verifying the Results</span></span>  
 <span data-ttu-id="5b500-178">執行封裝之後, 您必須移至要匯入 Siebel 資料的 SQL Server 資料庫來驗證結果。</span><span class="sxs-lookup"><span data-stu-id="5b500-178">After executing the package, you must verify the results by going to the SQL Server database to which the Siebel data is imported.</span></span> <span data-ttu-id="5b500-179">執行封裝應該已建立資料表的目的地資料庫中。</span><span class="sxs-lookup"><span data-stu-id="5b500-179">Executing the package should have created a table in the destination database.</span></span> <span data-ttu-id="5b500-180">此資料表應該填入 Siebel 資料表中的值。</span><span class="sxs-lookup"><span data-stu-id="5b500-180">This table should be populated with the values from the Siebel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b500-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b500-181">See Also</span></span>  
 [<span data-ttu-id="5b500-182">搭配使用 Data Provider for Siebel 與 SSIS</span><span class="sxs-lookup"><span data-stu-id="5b500-182">Use the Data Provider for Siebel with SSIS</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)