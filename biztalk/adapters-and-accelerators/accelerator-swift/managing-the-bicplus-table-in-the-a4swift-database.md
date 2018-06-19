---
title: 管理 Bicplus 資料庫中的資料表 A4SWIFT |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Bank Identifier Code (BIC), Bicplus table
- A4SWIFT database, Bicplus table
- Bicplus table
ms.assetid: a255cdea-5ed4-4481-97f1-8425877a76d6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a58396a9dd6627f2913da8e3845a99b17cf7698
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962100"
---
# <a name="managing-the-bicplus-table-in-the-a4swift-database"></a><span data-ttu-id="fecae-102">管理 Bicplus 資料表 A4SWIFT 資料庫中</span><span class="sxs-lookup"><span data-stu-id="fecae-102">Managing the Bicplus Table in the A4SWIFT Database</span></span>
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="fecae-103">執行 BIC 驗證使用 BIC 項目的資料表。</span><span class="sxs-lookup"><span data-stu-id="fecae-103"> uses a table of BIC entries to perform BIC validation.</span></span> <span data-ttu-id="fecae-104">這個資料表可以在任一個 Bicplus 資料表[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫或自訂資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="fecae-104">This table can be either the Bicplus table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database or a table in a custom database.</span></span>  
  
 <span data-ttu-id="fecae-105">若要管理這個資料表，您必須使用來自 SWIFT BIC 值擴展。</span><span class="sxs-lookup"><span data-stu-id="fecae-105">To manage this table, you must populate it with BIC values from SWIFT.</span></span> <span data-ttu-id="fecae-106">如果您使用自訂資料庫，您也必須匯出中的 SQL 檢視[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]到自訂資料庫的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fecae-106">If you use a custom database, you must also export SQL views in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database into the custom database.</span></span>  
  
## <a name="importing-bic-data-from-the-swift-bicplus-database"></a><span data-ttu-id="fecae-107">從 SWIFT Bicplus 資料庫匯入 BIC 資料</span><span class="sxs-lookup"><span data-stu-id="fecae-107">Importing BIC data from the SWIFT Bicplus database</span></span>  
 <span data-ttu-id="fecae-108">您必須填入來自 SWIFT BIC 值 （預設或自訂的資料表） 的 BIC 項目的資料表。</span><span class="sxs-lookup"><span data-stu-id="fecae-108">You must populate the table of BIC entries (either the default or the custom table) with BIC values from SWIFT.</span></span> <span data-ttu-id="fecae-109">SWIFT BIC 資料均可在[!INCLUDE[btsExcel](../../includes/btsexcel-md.md)]試算表或每月更新的 Oracle 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fecae-109">The SWIFT BIC data is available in an [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet or in an Oracle database that is updated monthly.</span></span> <span data-ttu-id="fecae-110">如需有關 SWIFT BIC 資料的詳細資訊，請移至[http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885)。</span><span class="sxs-lookup"><span data-stu-id="fecae-110">For more information about SWIFT BIC data, go to [http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885).</span></span>  
  
 <span data-ttu-id="fecae-111">如果您使用自訂資料庫，您必須從 SWIFT Bicplus 資料庫匯出 BIC 資料到自訂資料庫。</span><span class="sxs-lookup"><span data-stu-id="fecae-111">If you use a custom database, you must export BIC data from the SWIFT Bicplus database into the custom database.</span></span> <span data-ttu-id="fecae-112">您必須</span><span class="sxs-lookup"><span data-stu-id="fecae-112">You must</span></span>  
  
 <span data-ttu-id="fecae-113">您可以將資料匯入從 BIC [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] SWIFT 所提供的 Bicplus 資料表的試算表[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫，因為它們彼此相容。</span><span class="sxs-lookup"><span data-stu-id="fecae-113">You can import data from the BIC [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet provided by SWIFT into the Bicplus table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, because they are compatible.</span></span> <span data-ttu-id="fecae-114">如果您匯入資料來自 SWIFT 的試算表非[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫時，請確定欄位和資料庫，特別是 BIC 資料行中的資料行是否相容 SWIFT 的試算表。</span><span class="sxs-lookup"><span data-stu-id="fecae-114">If you import the data from the SWIFT spreadsheet into a non-[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, make sure that the fields and columns in your database, particularly the BIC column, are compatible with the SWIFT spreadsheet.</span></span>  
  
 <span data-ttu-id="fecae-115">它會發行 SWIFT 資料表中的程式碼以更新目的地資料表時，匯入作業並不會移除任何未發行的 BIC 代碼。</span><span class="sxs-lookup"><span data-stu-id="fecae-115">The import operation does not remove any unpublished BIC codes when it updates the destination table with the codes published in the SWIFT table.</span></span>  
  
 <span data-ttu-id="fecae-116">Bicplus 資料表所做的變更[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫登入[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fecae-116">The changes made to the Bicplus table of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database are logged in the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] log file.</span></span>  
  
#### <a name="to-import-bic-data-from-the-swift-bicplus-database"></a><span data-ttu-id="fecae-117">從 SWIFT Bicplus 資料庫匯入 BIC 資料</span><span class="sxs-lookup"><span data-stu-id="fecae-117">To import BIC data from the SWIFT Bicplus database</span></span>  
  
1.  <span data-ttu-id="fecae-118">按一下**啟動**，指向 **所有程式**，指向 inistalled 版本的 SQL Server，然後按一下**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="fecae-118">Click **Start**, point to **All Programs**, point to the inistalled version of SQL Server, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="fecae-119">在 連接到伺服器 對話方塊中，按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="fecae-119">In the Connect to Server dialog box, click **Connect**.</span></span>  
  
3.  <span data-ttu-id="fecae-120">在 [Microsoft SQL Server Management Studio] 視窗中，展開伺服器節點，然後**資料庫**。</span><span class="sxs-lookup"><span data-stu-id="fecae-120">In the Microsoft SQL Server Management Studio window, expand your server node, and then **Databases**.</span></span>  
  
4.  <span data-ttu-id="fecae-121">以滑鼠右鍵按一下**A4SWIFT**，指向 **工作**，然後按一下 **匯入資料**。</span><span class="sxs-lookup"><span data-stu-id="fecae-121">Right-click **A4SWIFT**, point to **Tasks**, and then click **Import Data**.</span></span>  
  
5.  <span data-ttu-id="fecae-122">在 SQL Server 匯入和匯出精靈歡迎使用] 頁面中，按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="fecae-122">On the SQL Server Import and Export Wizard welcome page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="fecae-123">在**選擇資料來源**頁面上，如果從 SWIFT Bicplus 匯入 BIC 資料[!INCLUDE[btsExcel](../../includes/btsexcel-md.md)]試算表，選取**Microsoft Excel**中**資料來源**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="fecae-123">On the **Choose a Data Source** page, if importing BIC data from the SWIFT Bicplus [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet, select **Microsoft Excel** in the **Data Source** text box.</span></span> <span data-ttu-id="fecae-124">位置的試算表中，瀏覽並選取試算表中的檔案名稱**Excel 檔案路徑**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="fecae-124">Browse to the location of the spreadsheet, and select the file name of the spreadsheet in the **Excel file path** text box.</span></span> <span data-ttu-id="fecae-125">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fecae-125">Click **Next**.</span></span>  
  
     <span data-ttu-id="fecae-126">如果匯入 BIC 資料，從 Oracle 資料庫，選取**Microsoft ODBC Driver for Oracle**中**資料來源**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="fecae-126">If importing BIC data from the Oracle database, select **Microsoft ODBC Driver for Oracle** in the **Data Source** text box.</span></span> <span data-ttu-id="fecae-127">輸入 Oracle 資料庫時，以及使用者名稱和密碼以連接到該伺服器，然後按一下所需的伺服器**下一步**。</span><span class="sxs-lookup"><span data-stu-id="fecae-127">Enter the server with the Oracle database, and the user name and password required to connect to that server, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="fecae-128">在**選擇目的地**頁面上，確認**Microsoft OLE DB Provider for SQL Server**輸入**目的地**文字方塊中，且**使用Windows 驗證**已選取。</span><span class="sxs-lookup"><span data-stu-id="fecae-128">On the **Choose a Destination** page, verify that **Microsoft OLE DB Provider for SQL Server** is entered in the **Destination** text box, and that **Use Windows Authentication** is selected.</span></span> <span data-ttu-id="fecae-129">如果您在擴展 Bicplus 資料表中的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫中，確認**A4SWIFT**輸入**資料庫**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="fecae-129">If you are populating the Bicplus table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, verify that **A4SWIFT** is entered in the **Database** text box.</span></span> <span data-ttu-id="fecae-130">如果您使用自訂資料庫，輸入該資料庫中的名稱**資料庫**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="fecae-130">If you are using a custom database, enter the name of that database in the **Database** text box.</span></span> <span data-ttu-id="fecae-131">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fecae-131">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="fecae-132">在**選取資料表複製或查詢**頁面上，確認**從一或多個資料表或檢視表複製資料**已選取。</span><span class="sxs-lookup"><span data-stu-id="fecae-132">On the **Select Table Copy or Query** page, verify that **Copy data from one or more tables or views** is selected.</span></span> <span data-ttu-id="fecae-133">如果您要使用查詢來指定的資料，請選取**撰寫查詢來指定要傳送的資料**。</span><span class="sxs-lookup"><span data-stu-id="fecae-133">If you need to use a query to specify the data, select **Write a query to specify the data to transfer**.</span></span> <span data-ttu-id="fecae-134">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fecae-134">Click **Next**.</span></span>  
  
9. <span data-ttu-id="fecae-135">在**選取來源資料表和檢視**頁面上，按一下**Bicplus**中**來源**資料行中，選取**Bicplus**中**目的地**資料行，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="fecae-135">On the **Select Source Tables and Views** page, click **Bicplus** in the **Source** column, select **Bicplus** in the **Destination** column, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="fecae-136">在**儲存並執行封裝**頁面上，輸入適當的排程資訊，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="fecae-136">On the **Save and Execute Package** page, enter the appropriate schedule information, and then click **Next**.</span></span>  
  
11. <span data-ttu-id="fecae-137">在**完成精靈**頁面上，檢閱摘要，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="fecae-137">On the **Complete the Wizard** page, review the summary and then click **Finish**.</span></span>  
  
## <a name="importing-sql-views-from-the-a4swift-database-into-a-custom-database"></a><span data-ttu-id="fecae-138">將匯入 SQL 檢視從 A4SWIFT 資料庫自訂資料庫</span><span class="sxs-lookup"><span data-stu-id="fecae-138">Importing SQL views from the A4SWIFT database into a Custom Database</span></span>  
 <span data-ttu-id="fecae-139">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式會安裝在兩個 SQL 檢視[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="fecae-139">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] setup program installs two SQL views in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database.</span></span> <span data-ttu-id="fecae-140">一個檢視為 8 個字元 BICs 和另一個則用於 BICs 11 個字元。</span><span class="sxs-lookup"><span data-stu-id="fecae-140">One view is for eight-character BICs and the other is for 11-character BICs.</span></span>  
  
 <span data-ttu-id="fecae-141">如果您使用自訂的資料庫，而不是[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]資料庫，您必須將自訂資料庫匯入這些 SQL 檢視。</span><span class="sxs-lookup"><span data-stu-id="fecae-141">If you use a custom database instead of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, you must importing these SQL views into the custom database.</span></span> <span data-ttu-id="fecae-142">您藉由在 Query Analyzer 執行 CreateBICViews.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="fecae-142">You do so by executing the CreateBICViews.sql script in the Query Analyzer.</span></span> <span data-ttu-id="fecae-143">此指令碼位於\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT/指令碼。</span><span class="sxs-lookup"><span data-stu-id="fecae-143">This script is in \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT/Scripts.</span></span>  
  
#### <a name="to-import-sql-views-from-the-a4swift-database-into-a-custom-database"></a><span data-ttu-id="fecae-144">若要從 A4SWIFT 資料庫的 SQL 檢視表匯入自訂資料庫</span><span class="sxs-lookup"><span data-stu-id="fecae-144">To import SQL views from the A4SWIFT database into a custom database</span></span>  
  
1.  <span data-ttu-id="fecae-145">在 Windows 檔案總管 中，移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\Scripts。</span><span class="sxs-lookup"><span data-stu-id="fecae-145">In Windows Explorer, move to \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\Scripts.</span></span> <span data-ttu-id="fecae-146">按兩下**CreateBICViews.sql**。</span><span class="sxs-lookup"><span data-stu-id="fecae-146">Double-click **CreateBICViews.sql**.</span></span>  
  
2.  <span data-ttu-id="fecae-147">在 連接到伺服器 對話方塊中，按一下 **連接**。</span><span class="sxs-lookup"><span data-stu-id="fecae-147">In the Connect to Server dialog box, click **Connect**.</span></span>  
  
3.  <span data-ttu-id="fecae-148">在 [Microsoft SQL Server Management Studio] 視窗中，選取**A4SWIFT**資料庫文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="fecae-148">In the Microsoft SQL Server Management Studio window, select **A4SWIFT** in the database text box.</span></span>  
  
4.  <span data-ttu-id="fecae-149">在 [查詢] 窗格中，如果您儲存 BICs 名為"Bicplus"以外的資料表中，尋找**dbo。Bicplus**檢視中**dbo。Bic11**，並將它變更為適當的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="fecae-149">In the query pane, if you are storing BICs in a table that is named other than "Bicplus", find **dbo.Bicplus** in the view **dbo.Bic11**, and change it to the appropriate table name.</span></span> <span data-ttu-id="fecae-150">對檢視執行相同的**dbo。Bic8**。</span><span class="sxs-lookup"><span data-stu-id="fecae-150">Do the same for the view **dbo.Bic8**.</span></span>  
  
5.  <span data-ttu-id="fecae-151">如果您要將 BICs 儲存名為"BIC"以外的資料行中，尋找**BIC**中**選取**，**其中**，和**ORDER BY**子句，和請將它變更為適當的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="fecae-151">If you are storing BICs in a column that is named other than "BIC", find **BIC** in the **SELECT**, **WHERE**, and **ORDER BY** clauses, and change it to the appropriate column name.</span></span>  
  
6.  <span data-ttu-id="fecae-152">按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="fecae-152">Click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecae-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="fecae-153">See Also</span></span>  
 [<span data-ttu-id="fecae-154">啟用驗證 Bank Identifier Code</span><span class="sxs-lookup"><span data-stu-id="fecae-154">Enabling Validation of Bank Identifier Codes</span></span>](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)