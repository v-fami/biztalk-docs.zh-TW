---
title: 匯入 Siebel 資料使用 Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33701361-eca2-4795-a5e0-78162a98e9ba
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d631c461c876ef4066e497d7d72d2e5fe13d022
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978031"
---
# <a name="import-siebel-data-using-visual-studio"></a><span data-ttu-id="8bc3e-102">使用 Visual Studio 的 Siebel 資料匯入</span><span class="sxs-lookup"><span data-stu-id="8bc3e-102">Import Siebel Data Using Visual Studio</span></span>
<span data-ttu-id="8bc3e-103">本節提供有關如何使用 Microsoft 的資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Siebel 系統的資料匯入到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-103">This section provides information about how to use Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to import data from a Siebel system into a SQL Server database.</span></span> <span data-ttu-id="8bc3e-104">它也會提供有關如何建立和執行 SSIS 套件，此資料匯入的指示。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-104">It also provides instructions on how to create and execute an SSIS package to import this data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8bc3e-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="8bc3e-105">Prerequisites</span></span>  
 <span data-ttu-id="8bc3e-106">然後再執行本主題所提供的程序，請確定：</span><span class="sxs-lookup"><span data-stu-id="8bc3e-106">Before performing the procedures provided in this topic, make sure:</span></span>  
  
- <span data-ttu-id="8bc3e-107">[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-107">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] is installed on the computer.</span></span>  
  
- <span data-ttu-id="8bc3e-108">Microsoft Visual Studio 會安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-108">Microsoft Visual Studio is installed on the computer.</span></span>  
  
## <a name="import-in-visual-studio"></a><span data-ttu-id="8bc3e-109">在 Visual Studio 中的匯入</span><span class="sxs-lookup"><span data-stu-id="8bc3e-109">Import in Visual Studio</span></span>  
 
1. <span data-ttu-id="8bc3e-110">啟動[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]並建立的整合服務專案。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-110">Start [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and create an Integration Service project.</span></span>  
  
2. <span data-ttu-id="8bc3e-111">從**專案**功能表上，選取**SSIS 匯入和匯出精靈**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-111">From the **Project** menu, select **SSIS Import and Export Wizard**.</span></span> <span data-ttu-id="8bc3e-112">這會啟動 SQL Server 匯入和匯出精靈。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-112">This starts the SQL Server Import and Export Wizard.</span></span>  
  
3. <span data-ttu-id="8bc3e-113">閱讀 歡迎 畫面上的資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-113">Read the information on the Welcome screen, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="8bc3e-114">在 [**選擇資料來源**] 對話方塊中，從**資料來源**下拉式清單 **.NET Framework Data Provider for Siebel eBusiness 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-114">In the **Choose a Data Source** dialog box, from the **Data Source** drop-down list **.NET Framework Data Provider for Siebel eBusiness Applications**.</span></span> <span data-ttu-id="8bc3e-115">指定不同的連接屬性的值[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]連接字串。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-115">Specify values for the different connection properties for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] connection string.</span></span> <span data-ttu-id="8bc3e-116">如需連接字串屬性的詳細資訊，請參閱[Siebel 連接字串的資料提供者屬性](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-116">For more information about the connection string properties, see [Data provider properties for the Siebel connection string](../../adapters-and-accelerators/adapter-siebel/data-provider-properties-for-the-siebel-connection-string.md).</span></span>  
  
    <span data-ttu-id="8bc3e-117">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-117">Click **Next**.</span></span>  
  
5. <span data-ttu-id="8bc3e-118">在 [**選擇目的地**] 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="8bc3e-118">In the **Choose a Destination** dialog box:</span></span>  
  
   1.  <span data-ttu-id="8bc3e-119">從**目的地**下拉式清單中，選取**SQL Native Client**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-119">From the **Destination** drop-down list, select **SQL Native Client**.</span></span>  
  
   2.  <span data-ttu-id="8bc3e-120">從**伺服器名稱**下拉式清單中，選取 SQL Server 名稱。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-120">From the **Server name** drop-down list, select a SQL Server name.</span></span>  
  
   3.  <span data-ttu-id="8bc3e-121">選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-121">Select an authentication mode.</span></span>  
  
   4.  <span data-ttu-id="8bc3e-122">從**資料庫**下拉式清單中，選取您要匯入 Siebel 的資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-122">From the **Database** drop-down list, select the database to which you want to import the Siebel table.</span></span>  
  
   5.  <span data-ttu-id="8bc3e-123">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-123">Click **Next**.</span></span>  
  
6. <span data-ttu-id="8bc3e-124">在 **指定資料表複製或查詢**對話方塊方塊中，選擇**撰寫查詢來指定要傳送的資料**選項。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-124">In the **Specify Table Copy or Query** dialog box, choose the **Write a query to specify the data to transfer** option.</span></span>  
  
7. <span data-ttu-id="8bc3e-125">在 **提供來源查詢**對話方塊方塊中，指定選取的查詢，以篩選要匯入到 SQL Server 的資料。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-125">In the **Provide a Source Query** dialog box, specify a SELECT query to filter the data to be imported into the SQL Server.</span></span> <span data-ttu-id="8bc3e-126">如需詳細資訊，選取 「 了解文法查詢[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，請參閱 < [Siebel 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md)。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-126">For more information about the grammar for a SELECT query for the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], see [Syntax for a SELECT Statement in Siebel](../../adapters-and-accelerators/adapter-siebel/syntax-for-a-select-statement-in-siebel.md).</span></span>  
  
8. <span data-ttu-id="8bc3e-127">若要驗證的查詢，請按一下**剖析**按鈕，再按一下**確定**中的快顯對話方塊中，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-127">To validate the query, click the **Parse** button, click **OK** in the pop-up dialog box, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="8bc3e-128">在 **選取來源資料表和檢視**對話方塊方塊中，選取核取方塊，針對來源和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-128">In the **Select Source Tables and Views** dialog box, select the check box against the source and destination tables.</span></span> <span data-ttu-id="8bc3e-129">來源是您指定用來擷取 Siebel 的資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-129">The source is the query you specified to retrieve data from Siebel.</span></span> <span data-ttu-id="8bc3e-130">目的地會將 SQL Server 資料庫中建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-130">The destination will be the table that will be created in the SQL Server database.</span></span>  
  
10. <span data-ttu-id="8bc3e-131">精靈會建立預設的對應來源與目的地之間資料表欄位。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-131">The wizard creates a default mapping between the source and destination table fields.</span></span> <span data-ttu-id="8bc3e-132">不過，您可以變更對應，根據您的需求。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-132">However, you can change the mappings according to your requirement.</span></span> <span data-ttu-id="8bc3e-133">若要變更欄位對應，請按一下**編輯對應**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-133">To change the field mappings, click **Edit Mappings**.</span></span>  
  
11. <span data-ttu-id="8bc3e-134">在 [**資料行對應**] 對話方塊中，您可以：</span><span class="sxs-lookup"><span data-stu-id="8bc3e-134">In the **Column Mappings** dialog box, you can:</span></span>  
  
    - <span data-ttu-id="8bc3e-135">變更目的地資料表中的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-135">Change the names of columns in the destination table.</span></span>  
  
    - <span data-ttu-id="8bc3e-136">忽略特定的目的地資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-136">Ignore certain columns in the destination table.</span></span>  
  
    - <span data-ttu-id="8bc3e-137">變更目的地資料表中的欄位資料類型。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-137">Change the data type for fields in destination table.</span></span>  
  
    - <span data-ttu-id="8bc3e-138">變更其他欄位屬性，例如可為 null，大小、 有效位數和小數位數。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-138">Change other field attributes such as nullable, size, precision, and scale.</span></span>  
  
    - <span data-ttu-id="8bc3e-139">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-139">Click **OK**.</span></span>  
  
      <span data-ttu-id="8bc3e-140">![Siebel 與 SQL 資料表之間的資料行對應](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span><span class="sxs-lookup"><span data-stu-id="8bc3e-140">![Column mappings between Siebel and SQL table](../../adapters-and-accelerators/adapter-siebel/media/a3047801-3fa6-496b-91d8-3888dfbb0169.gif "a3047801-3fa6-496b-91d8-3888dfbb0169")</span></span>  
  
12. <span data-ttu-id="8bc3e-141">在 **選取來源資料表和檢視表** 對話方塊中，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-141">In the **Select Source Tables and Views** dialog box, click **Next**.</span></span>  
  
13. <span data-ttu-id="8bc3e-142">在 **完成精靈**對話方塊方塊中，檢閱精靈將會執行，然後再按一下的動作的摘要**完成**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-142">In the **Complete the Wizard** dialog box, review the summary of actions that the wizard will perform, and then click **Finish**.</span></span>  
  
14. <span data-ttu-id="8bc3e-143">在 [**正在執行作業**] 對話方塊中，精靈會啟動執行工作，以從 Siebel 將資訊匯入到 SQL Server 資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-143">In the **Performing Operations** dialog box, the wizard starts executing tasks to import the information from Siebel into a SQL Server database table.</span></span> <span data-ttu-id="8bc3e-144">每個工作的狀態會顯示在精靈中。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-144">The status for each task is displayed in the wizard.</span></span>  
  
15. <span data-ttu-id="8bc3e-145">所有工作都成功都執行之後，請按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-145">After all the tasks are successfully executed, click **Close**.</span></span> <span data-ttu-id="8bc3e-146">如果工作失敗，請參閱對應的錯誤訊息、 修正問題，並返回精靈。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-146">If a task fails, see the corresponding error message, fix the issue, and rerun the wizard.</span></span>  
  
16. <span data-ttu-id="8bc3e-147">精靈會將您的整合服務專案中的 SSIS 套件。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-147">The wizard adds an SSIS package to your Integration Service project.</span></span> <span data-ttu-id="8bc3e-148">儲存整合服務專案。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-148">Save the Integration Service project.</span></span>  
  
## <a name="run-the-ssis-package"></a><span data-ttu-id="8bc3e-149">執行 SSIS 套件</span><span class="sxs-lookup"><span data-stu-id="8bc3e-149">Run the SSIS Package</span></span>  
 <span data-ttu-id="8bc3e-150">封裝建立後的整合服務專案中，您可以將它 Siebel 系統的資料匯入到 SQL Server 資料庫執行。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-150">Once the package is created within an Integration Service project, you can execute it to import data from a Siebel system into a SQL Server database.</span></span> <span data-ttu-id="8bc3e-151">執行下列步驟來執行封裝來匯入 Siebel 資料。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-151">Perform the following steps to import Siebel data by executing the package.</span></span>  
  
1.  <span data-ttu-id="8bc3e-152">瀏覽至 [方案總管] 中的 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-152">Navigate to the SSIS package in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="8bc3e-153">以滑鼠右鍵按一下封裝名稱，然後按**執行封裝**。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-153">Right-click the package name, and then select **Execute Package**.</span></span>  
  
<span data-ttu-id="8bc3e-154">[執行 Integration Services (SSIS) 封裝](https://docs.microsoft.com/sql/integration-services/packages/run-integration-services-ssis-packages)提供詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-154">[Run Integration Services (SSIS) Packages](https://docs.microsoft.com/sql/integration-services/packages/run-integration-services-ssis-packages) provides more info.</span></span> 
  
## <a name="verify-the-results"></a><span data-ttu-id="8bc3e-155">驗證結果</span><span class="sxs-lookup"><span data-stu-id="8bc3e-155">Verify the Results</span></span>  
 <span data-ttu-id="8bc3e-156">執行封裝之後, 您必須登入 SQL Server，並瀏覽至要匯入 Siebel 資料的資料庫驗證結果。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-156">After executing the package, you must verify the results by logging on to the SQL Server and navigating to the database to which the Siebel data is imported.</span></span> <span data-ttu-id="8bc3e-157">執行封裝應該已建立資料表的目的地資料庫中。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-157">Executing the package should have created a table in the destination database.</span></span> <span data-ttu-id="8bc3e-158">此資料表應該填入 Siebel 資料表中的值。</span><span class="sxs-lookup"><span data-stu-id="8bc3e-158">This table should be populated with the values from the Siebel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc3e-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bc3e-159">See Also</span></span>  
 [<span data-ttu-id="8bc3e-160">搭配使用 Data Provider for Siebel 與 SSIS</span><span class="sxs-lookup"><span data-stu-id="8bc3e-160">Use the Data Provider for Siebel with SSIS</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-data-provider-for-siebel-with-ssis.md)