---
title: "使用 SQL Server Management Studio 的 SAP 資料匯入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing SAP data, how to
- SQL Server Management Studio, importing data
ms.assetid: c8151c6d-4b33-40fe-9b83-9bed27df9a99
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28981d2130e82a094e470de1e2b6904382be56b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="import-sap-data-using-sql-server-management-studio"></a><span data-ttu-id="704d0-102">使用 SQL Server Management Studio 匯入 SAP 資料</span><span class="sxs-lookup"><span data-stu-id="704d0-102">Import SAP Data Using SQL Server Management Studio</span></span>
<span data-ttu-id="704d0-103">本節提供有關如何使用 SQL Server Management Studio 從 SAP 系統的資料匯入到 SQL Server 資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="704d0-103">This section provides information on how to use the SQL Server Management Studio to import data from an SAP system into a SQL Server database.</span></span> <span data-ttu-id="704d0-104">本節提供有關如何建立 SSIS 封裝，您可以執行匯入資料的指示。</span><span class="sxs-lookup"><span data-stu-id="704d0-104">This section provides instruction on how to create an SSIS package that you can execute to import data.</span></span> <span data-ttu-id="704d0-105">本章節也會提供有關如何執行 SSIS 封裝的資訊。</span><span class="sxs-lookup"><span data-stu-id="704d0-105">This section also provides information on how to execute the SSIS package.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="704d0-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="704d0-106">Prerequisites</span></span>  
 <span data-ttu-id="704d0-107">然後再執行本主題提供的程序，請確定：</span><span class="sxs-lookup"><span data-stu-id="704d0-107">Before performing the procedures provided in this topic, make sure:</span></span>  
  
-   [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]<span data-ttu-id="704d0-108">已安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="704d0-108"> is installed on the computer.</span></span>  
  
-   <span data-ttu-id="704d0-109">在電腦上安裝 SQL Server Business Intelligence Development Studio。</span><span class="sxs-lookup"><span data-stu-id="704d0-109">SQL Server Business Intelligence Development Studio is installed on the computer.</span></span>  
  
### <a name="to-import-data-using-sql-server-management-studio"></a><span data-ttu-id="704d0-110">若要使用 SQL Server Management Studio 匯入資料</span><span class="sxs-lookup"><span data-stu-id="704d0-110">To import data using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="704d0-111">啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="704d0-111">Start the SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="704d0-112">在**連接到伺服器**對話方塊方塊中，指定要連接到 SQL Server 資料庫，然後按一下值**連接**。</span><span class="sxs-lookup"><span data-stu-id="704d0-112">In the **Connect to Server** dialog box, specify the values to connect to a SQL Server database and click **Connect**.</span></span> <span data-ttu-id="704d0-113">**Microsoft SQL Server Management Studio**隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="704d0-113">The **Microsoft SQL Server Management Studio** opens.</span></span>  
  
3.  <span data-ttu-id="704d0-114">在**物件總管] 中**、 依序展開 [SQL Server 名稱、 展開**資料庫**，以滑鼠右鍵按一下資料庫，其中您將會匯出資料表從 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="704d0-114">In the **Object Explorer**, expand the SQL Server name, expand **Databases**, and right-click the database into which you will be exporting the tables from the SAP system.</span></span> <span data-ttu-id="704d0-115">從內容功能表，指向**工作**，然後按一下**匯入資料**。</span><span class="sxs-lookup"><span data-stu-id="704d0-115">From the context menu, point to **Tasks**, and click **Import Data**.</span></span> <span data-ttu-id="704d0-116">這會啟動**SQL Server 匯入和匯出精靈**。</span><span class="sxs-lookup"><span data-stu-id="704d0-116">This starts the **SQL Server Import and Export Wizard**.</span></span>  
  
4.  <span data-ttu-id="704d0-117">閱讀歡迎] 畫面中，然後按一下上的資訊**下一步**。</span><span class="sxs-lookup"><span data-stu-id="704d0-117">Read the information on the welcome screen and click **Next**.</span></span>  
  
5.  <span data-ttu-id="704d0-118">在**選擇資料來源**對話方塊中，從**資料來源**下拉式選單**.NET Framework Data Provider for mySAP Business Suite**。</span><span class="sxs-lookup"><span data-stu-id="704d0-118">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list **.NET Framework Data Provider for mySAP Business Suite**.</span></span> <span data-ttu-id="704d0-119">對話方塊會列出不同的連線參數，以連接至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="704d0-119">The dialog box lists the different connection parameters to connect to an SAP system.</span></span> <span data-ttu-id="704d0-120">一般連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要：</span><span class="sxs-lookup"><span data-stu-id="704d0-120">A typical connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires:</span></span>  
  
    -   <span data-ttu-id="704d0-121">輸入連接的連接參數。</span><span class="sxs-lookup"><span data-stu-id="704d0-121">The connection parameters for a connection type.</span></span> <span data-ttu-id="704d0-122">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援連線類型 A、 B 和 d。若要連接到 SAP 系統必須提供連接參數的任何*一個*一種連線類型。</span><span class="sxs-lookup"><span data-stu-id="704d0-122">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports connection types A, B, and D. To connect to an SAP system you must provide connection parameters for any *one* of these connection types.</span></span> <span data-ttu-id="704d0-123">比方說，連接類型的您必須提供應用程式伺服器主機和系統編號的名稱。</span><span class="sxs-lookup"><span data-stu-id="704d0-123">For example, for connection type A, you must provide the name of the application server host and the system number.</span></span>  
  
    -   <span data-ttu-id="704d0-124">若要連接到 SAP 系統，例如使用者名稱和密碼登入資訊。</span><span class="sxs-lookup"><span data-stu-id="704d0-124">The login information to connect to an SAP system such as username and password.</span></span>  
  
     <span data-ttu-id="704d0-125">如需有關連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[了解 Data Provider for SAP 連接字串](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="704d0-125">For more information about the connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Read about Data Provider for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
     <span data-ttu-id="704d0-126">在**選擇資料來源**對話方塊方塊中，指定：</span><span class="sxs-lookup"><span data-stu-id="704d0-126">In the **Choose a Data Source** dialog box, specify:</span></span>  
  
    -   <span data-ttu-id="704d0-127">連接類型之參數的任何一個連線。</span><span class="sxs-lookup"><span data-stu-id="704d0-127">The connection parameters for any one connection type.</span></span>  
  
    -   <span data-ttu-id="704d0-128">要連接至 SAP 系統的登入資訊。</span><span class="sxs-lookup"><span data-stu-id="704d0-128">The login information to connect to an SAP system.</span></span>  
  
    -   <span data-ttu-id="704d0-129">您是否要啟用 SAP GUI 偵錯。</span><span class="sxs-lookup"><span data-stu-id="704d0-129">Whether you want to enable SAP GUI debugging.</span></span>  
  
    -   <span data-ttu-id="704d0-130">您是否要使用 RFC SDK 追蹤。</span><span class="sxs-lookup"><span data-stu-id="704d0-130">Whether you want to use RFC SDK tracing.</span></span>  
  
     <span data-ttu-id="704d0-131">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="704d0-131">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="704d0-132">在**選擇目的地**對話方塊：</span><span class="sxs-lookup"><span data-stu-id="704d0-132">In the **Choose a Destination** dialog box:</span></span>  
  
    1.  <span data-ttu-id="704d0-133">從**目的地**下拉式清單中，選取**SQL Native Client**。</span><span class="sxs-lookup"><span data-stu-id="704d0-133">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
    2.  <span data-ttu-id="704d0-134">從**伺服器名稱**下拉式清單中，選取 [SQL server 名稱。</span><span class="sxs-lookup"><span data-stu-id="704d0-134">From the **Server name** drop-down list, select a SQL server name.</span></span>  
  
    3.  <span data-ttu-id="704d0-135">選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="704d0-135">Select an authentication mode.</span></span>  
  
    4.  <span data-ttu-id="704d0-136">從**資料庫**下拉式清單中，選取您要匯入 SAP 資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="704d0-136">From the **Database** drop-down list, select the database to which you want to import the SAP table.</span></span>  
  
    5.  <span data-ttu-id="704d0-137">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="704d0-137">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="704d0-138">在**指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="704d0-138">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option and click **Next**.</span></span>  
  
8.  <span data-ttu-id="704d0-139">在**提供來源查詢**對話方塊方塊中，指定 SELECT 查詢來篩選要匯入 SQL Server 的資料。</span><span class="sxs-lookup"><span data-stu-id="704d0-139">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="704d0-140">如需文法的 SELECT 查詢[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[語法選取陳述式 SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="704d0-140">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Syntax for a SELECT Statement SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span>  
  
     <span data-ttu-id="704d0-141">按一下**剖析**按鈕驗證查詢，並按一下**確定**快顯對話方塊方塊中。</span><span class="sxs-lookup"><span data-stu-id="704d0-141">Click the **Parse** button to validate the query and click **OK** in the pop-up dialog box.</span></span> <span data-ttu-id="704d0-142">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="704d0-142">Click **Next**.</span></span>  
  
9. <span data-ttu-id="704d0-143">在**選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="704d0-143">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="704d0-144">來源是您指定要從 SAP 擷取資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="704d0-144">The source is the query you specified to retrieve data from SAP.</span></span> <span data-ttu-id="704d0-145">目的地是將 SQL Server 資料庫中建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="704d0-145">The destination is the table that will be created in the SQL Server database.</span></span>  
  
10. <span data-ttu-id="704d0-146">精靈會建立預設的對應來源與目的地之間資料表欄位。</span><span class="sxs-lookup"><span data-stu-id="704d0-146">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="704d0-147">不過，您可以變更對應，根據您的需求。</span><span class="sxs-lookup"><span data-stu-id="704d0-147">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="704d0-148">若要變更欄位對應，請按一下**編輯對應**。</span><span class="sxs-lookup"><span data-stu-id="704d0-148">To change the field mappings, click **Edit Mappings**.</span></span>  
  
     <span data-ttu-id="704d0-149">![SAP 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")</span><span class="sxs-lookup"><span data-stu-id="704d0-149">![Column mappings between SAP and SQL tables](../../adapters-and-accelerators/adapter-sap/media/73751f74-4cd0-47c6-85ea-de7f507131a0.gif "73751f74-4cd0-47c6-85ea-de7f507131a0")</span></span>  
  
11. <span data-ttu-id="704d0-150">在**資料行對應**對話方塊中，您可以：</span><span class="sxs-lookup"><span data-stu-id="704d0-150">In the **Column Mappings** dialog box, you can:</span></span>  
  
    -   <span data-ttu-id="704d0-151">變更目的地資料表中的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="704d0-151">Change the names of columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="704d0-152">忽略特定資料行與目的地資料表中。</span><span class="sxs-lookup"><span data-stu-id="704d0-152">Ignore certain columns in the destination table.</span></span>  
  
    -   <span data-ttu-id="704d0-153">變更目的地資料表中的欄位的資料類型。</span><span class="sxs-lookup"><span data-stu-id="704d0-153">Change the data type for fields in destination table.</span></span>  
  
    -   <span data-ttu-id="704d0-154">變更其他欄位屬性，例如可為 null，大小、 精確度和小數位數。</span><span class="sxs-lookup"><span data-stu-id="704d0-154">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
    -   <span data-ttu-id="704d0-155">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="704d0-155">Click **OK**.</span></span>  
  
12. <span data-ttu-id="704d0-156">在**選取來源資料表和檢視**對話方塊中，按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="704d0-156">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
13. <span data-ttu-id="704d0-157">在**儲存並執行封裝**對話方塊中，</span><span class="sxs-lookup"><span data-stu-id="704d0-157">In the **Save and Execute Package** dialog box,</span></span>  
  
    -   <span data-ttu-id="704d0-158">選取**立即執行**核取方塊，以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="704d0-158">Select the **Execute immediately** check box to execute the query.</span></span>  
  
    -   <span data-ttu-id="704d0-159">選取**儲存 SSIS 封裝**核取方塊，來將查詢儲存為封裝和更新版本執行。</span><span class="sxs-lookup"><span data-stu-id="704d0-159">Select the **Save SSIS Package** check box to save the query as a package and execute it later.</span></span> <span data-ttu-id="704d0-160">如果您選擇儲存封裝，您也必須指定您是否要將封裝儲存在 SQL Server 或檔案系統。</span><span class="sxs-lookup"><span data-stu-id="704d0-160">If you chose to save the package, you must also specify whether you want to save the package in the SQL Server or the file system.</span></span>  
  
    -   <span data-ttu-id="704d0-161">從**封裝保護等級**下拉式清單中，選取封裝層級的保護，然後指定認證必要。</span><span class="sxs-lookup"><span data-stu-id="704d0-161">From the **Package protection level** drop-down list, select a protection level for the package and specify credentials where required.</span></span>  
  
    -   <span data-ttu-id="704d0-162">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="704d0-162">Click **Next**.</span></span>  
  
     <span data-ttu-id="704d0-163">如果您選擇儲存封裝，請繼續進行下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="704d0-163">If you chose to save the package, proceed to next step.</span></span> <span data-ttu-id="704d0-164">否則，請跳至步驟 15。</span><span class="sxs-lookup"><span data-stu-id="704d0-164">Otherwise, skip to step 15.</span></span>  
  
14. <span data-ttu-id="704d0-165">在**儲存 SSIS 封裝**對話方塊方塊中，指定：</span><span class="sxs-lookup"><span data-stu-id="704d0-165">In the **Save SSIS Package** dialog box, specify:</span></span>  
  
    -   <span data-ttu-id="704d0-166">封裝名稱</span><span class="sxs-lookup"><span data-stu-id="704d0-166">Name for the package</span></span>  
  
    -   <span data-ttu-id="704d0-167">套件描述</span><span class="sxs-lookup"><span data-stu-id="704d0-167">Description for the package</span></span>  
  
    -   <span data-ttu-id="704d0-168">如果您選擇將封裝儲存至 SQL server，請選取 [從 SQL Server**伺服器名稱**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="704d0-168">If you chose to save the package to a SQL server, select a SQL Server from the **Server name** drop-down list.</span></span>  
  
    -   <span data-ttu-id="704d0-169">如果您選擇將封裝儲存至檔案系統中，指定的名稱和位置中的檔案**檔案名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="704d0-169">If you chose to save the package to the file system, specify the name and location of the file in the **File name** text box.</span></span>  
  
    -   <span data-ttu-id="704d0-170">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="704d0-170">Click **Next**.</span></span>  
  
15. <span data-ttu-id="704d0-171">在**完成精靈**對話方塊方塊中，檢閱精靈將執行，並按一下動作的摘要**完成**。</span><span class="sxs-lookup"><span data-stu-id="704d0-171">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and click **Finish**.</span></span>  
  
16. <span data-ttu-id="704d0-172">在**執行運算**對話方塊中，精靈會啟動執行工作，以從 SAP 的資訊匯入到 SQL Server 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="704d0-172">In the **Performing Operations** dialog box, the wizard starts executing tasks to import the information from SAP into a SQL Server database table.</span></span> <span data-ttu-id="704d0-173">每個工作的狀態會顯示在精靈中。</span><span class="sxs-lookup"><span data-stu-id="704d0-173">The status for each task is displayed in the wizard.</span></span>  
  
17. <span data-ttu-id="704d0-174">所有工作都執行成功之後，請按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="704d0-174">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="704d0-175">如果工作失敗，請參閱對應的錯誤訊息、 修正問題，和重新執行精靈。</span><span class="sxs-lookup"><span data-stu-id="704d0-175">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
## <a name="running-the-ssis-package"></a><span data-ttu-id="704d0-176">執行 SSIS 封裝</span><span class="sxs-lookup"><span data-stu-id="704d0-176">Running the SSIS Package</span></span>  
 <span data-ttu-id="704d0-177">如果您選擇儲存 SSIS 封裝，您可以執行它從 SAP 系統中擷取最新的資訊。</span><span class="sxs-lookup"><span data-stu-id="704d0-177">If you chose to save the SSIS package, you can run it to retrieve the most recent information from the SAP system.</span></span> <span data-ttu-id="704d0-178">本節提供如何執行封裝，如果您選擇將它儲存到檔案系統資訊。</span><span class="sxs-lookup"><span data-stu-id="704d0-178">This section provides information on how to run the package if you chose to save it to the file system.</span></span>  
  
#### <a name="to-run-the-package-from-windows-explorer"></a><span data-ttu-id="704d0-179">若要從 Windows 檔案總管中執行封裝</span><span class="sxs-lookup"><span data-stu-id="704d0-179">To run the package from Windows Explorer</span></span>  
  
1.  <span data-ttu-id="704d0-180">從**Windows 檔案總管**、 瀏覽至您儲存封裝的位置，然後按兩下封裝。</span><span class="sxs-lookup"><span data-stu-id="704d0-180">From the **Windows Explorer**, navigate to the location where you saved the package, and double-click the package.</span></span>  
  
2.  <span data-ttu-id="704d0-181">在**執行封裝公用程式**對話方塊中，按一下 [ **Execute**。</span><span class="sxs-lookup"><span data-stu-id="704d0-181">On the **Execute Package Utility** dialog box, click **Execute**.</span></span>  
  
3.  <span data-ttu-id="704d0-182">**封裝執行進度**對話方塊會顯示不同的工作的進度。</span><span class="sxs-lookup"><span data-stu-id="704d0-182">The **Package Execution Progress** dialog box displays the progress of the different tasks.</span></span>  
  
4.  <span data-ttu-id="704d0-183">所有工作都執行成功之後，請按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="704d0-183">After all the tasks are successfully executed, click **Close**.</span></span>  
  
5.  <span data-ttu-id="704d0-184">在**執行封裝公用程式**對話方塊中，按一下 [**關閉**。</span><span class="sxs-lookup"><span data-stu-id="704d0-184">On the **Execute Package Utility** dialog box, click **Close**.</span></span>  
  
 <span data-ttu-id="704d0-185">如需有關執行封裝的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972)。</span><span class="sxs-lookup"><span data-stu-id="704d0-185">For more information about running packages, see [http://go.microsoft.com/fwlink/?LinkId=94972](http://go.microsoft.com/fwlink/?LinkId=94972).</span></span> <span data-ttu-id="704d0-186">任何其他相關資訊的 SSIS 封裝，請參閱[http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973)。</span><span class="sxs-lookup"><span data-stu-id="704d0-186">For any other information related to SSIS packages, see [http://go.microsoft.com/fwlink/?LinkId=94973](http://go.microsoft.com/fwlink/?LinkId=94973).</span></span>  
  
## <a name="verifying-the-results"></a><span data-ttu-id="704d0-187">驗證結果</span><span class="sxs-lookup"><span data-stu-id="704d0-187">Verifying the Results</span></span>  
 <span data-ttu-id="704d0-188">執行封裝之後, 您必須確認結果，請前往 SAP 資料匯入的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="704d0-188">After executing the package, you must verify the results by going to the SQL Server database to which the SAP data is imported.</span></span> <span data-ttu-id="704d0-189">執行封裝應該目的地資料庫中建立資料表並填入從 SAP 資料表的值。</span><span class="sxs-lookup"><span data-stu-id="704d0-189">Executing the package should have created a table in destination database and populated with the values from the SAP table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704d0-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="704d0-190">See Also</span></span>  
 [<span data-ttu-id="704d0-191">適用於 SAP 使用 SSIS 中使用資料提供者</span><span class="sxs-lookup"><span data-stu-id="704d0-191">Using the Data Provider for SAP with SSIS</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)