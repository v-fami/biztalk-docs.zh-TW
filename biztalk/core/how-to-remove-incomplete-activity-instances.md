---
title: 移除未完成的活動執行個體 |Microsoft Docs
description: 執行自訂的 RemoveDanglingInstances SQL 指令碼，以從 BizTalk Server 中的 BAM 主要匯入資料庫移除未完成的執行個體
ms.custom: ''
ms.date: 01/18/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7060578c-6267-487b-8530-efa18f9431ce
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a4ed81978dd275be8eb0348ff15dc8748258239
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977167"
---
# <a name="remove-incomplete-activity-instances"></a><span data-ttu-id="6c49d-103">移除未完成的活動執行個體</span><span class="sxs-lookup"><span data-stu-id="6c49d-103">Remove Incomplete Activity Instances</span></span>
<span data-ttu-id="6c49d-104">部署 BAM 定義檔案時，會為定義檔案中所定義的每個活動，在 BAM 主要匯入資料庫中建立五個資料表，</span><span class="sxs-lookup"><span data-stu-id="6c49d-104">When a BAM definition file is deployed, five tables are created in the BAM Primary Import database for each activity defined in the definition file.</span></span> <span data-ttu-id="6c49d-105">分別是：</span><span class="sxs-lookup"><span data-stu-id="6c49d-105">These tables are:</span></span>  
  
- <span data-ttu-id="6c49d-106">bam_`ActivityName`_Active</span><span class="sxs-lookup"><span data-stu-id="6c49d-106">bam_`ActivityName`_Active</span></span>  
  
- <span data-ttu-id="6c49d-107">bam_`ActivityName`_Completed</span><span class="sxs-lookup"><span data-stu-id="6c49d-107">bam_`ActivityName`_Completed</span></span>  
  
- <span data-ttu-id="6c49d-108">bam_`ActivityName`_ActiveRelationships</span><span class="sxs-lookup"><span data-stu-id="6c49d-108">bam_`ActivityName`_ActiveRelationships</span></span>  
  
- <span data-ttu-id="6c49d-109">bam_`ActivityName`_CompletedRelationships</span><span class="sxs-lookup"><span data-stu-id="6c49d-109">bam_`ActivityName`_CompletedRelationships</span></span>  
  
- <span data-ttu-id="6c49d-110">bam_`ActivityName`_Continuations</span><span class="sxs-lookup"><span data-stu-id="6c49d-110">bam_`ActivityName`_Continuations</span></span>  
  
  <span data-ttu-id="6c49d-111">其中 `ActivityName` 是使用者定義的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="6c49d-111">Where `ActivityName` is the name of the activity that the user has defined.</span></span>  
  
  <span data-ttu-id="6c49d-112">正常執行時，不完整的資料會保留在 bam_`ActivityName`*作用中的資料表。如果資料含有關係與參考，則資料會出在 bam\\*`ActivityName`_ActiveRelationships 資料表。</span><span class="sxs-lookup"><span data-stu-id="6c49d-112">During normal execution, incomplete data remains in the bam_`ActivityName`*Active table. If the data has relations and references, then there will be data in the bam\\*`ActivityName`_ActiveRelationships table.</span></span>  
  
  <span data-ttu-id="6c49d-113">追蹤使用接續的活動期間，有時候在 BAM 資料庫中的活動可能處在未完成狀態。</span><span class="sxs-lookup"><span data-stu-id="6c49d-113">During the tracking of activities that use continuations, there may be instances in which an activity is left in an incomplete state in the BAM databases.</span></span> <span data-ttu-id="6c49d-114">您可以使用本主題最後的預存程序建立指令碼，來建立將清除不完整記錄的預存程序。</span><span class="sxs-lookup"><span data-stu-id="6c49d-114">You can use the stored procedure creation script at the end of this topic to create a stored procedure that will purge the incomplete records.</span></span>  
  
  <span data-ttu-id="6c49d-115">如果要建立預存程序，使用 SQL Server Management 複製指令碼並針對 BAM 主要匯入資料庫執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="6c49d-115">To create the stored procedure, copy the script and execute it against the BAM Primary Import database by using SQL Server Management.</span></span> <span data-ttu-id="6c49d-116">此指令碼會產生名為預存程序**RemoveDanglingInstances**資料庫中。</span><span class="sxs-lookup"><span data-stu-id="6c49d-116">The script will generate a stored procedure named **RemoveDanglingInstances** in the database.</span></span>  
  
## <a name="create-the-removedanglinginstances-stored-procedure"></a><span data-ttu-id="6c49d-117">建立 RemoveDanglingInstances 預存程序</span><span class="sxs-lookup"><span data-stu-id="6c49d-117">Create the RemoveDanglingInstances stored procedure</span></span>  
  
1.  <span data-ttu-id="6c49d-118">開啟**SQL Server Management Studio**，並連接到 SQL server。</span><span class="sxs-lookup"><span data-stu-id="6c49d-118">Open **SQL Server Management Studio**, and connect to the SQL server.</span></span>
  
2.  <span data-ttu-id="6c49d-119">依序展開伺服器名稱**資料庫**，然後選取 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="6c49d-119">Expand the server name, expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
3.  <span data-ttu-id="6c49d-120">按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="6c49d-120">Click **New Query**.</span></span>  
  
4.  <span data-ttu-id="6c49d-121">複製預存程序建立指令碼，並將它貼到 [查詢] 窗格。</span><span class="sxs-lookup"><span data-stu-id="6c49d-121">Copy the stored procedure creation script, and paste it into the query pane.</span></span>  
  
5.  <span data-ttu-id="6c49d-122">**執行**指令碼。</span><span class="sxs-lookup"><span data-stu-id="6c49d-122">**Execute** the script.</span></span> <span data-ttu-id="6c49d-123">產生的預存程序會在預存程序清單中顯示為 dbo.RemoveDanglingInstances。</span><span class="sxs-lookup"><span data-stu-id="6c49d-123">The resulting stored procedure can be viewed in the list of stored procedures as dbo.RemoveDanglingInstances.</span></span>  
  
## <a name="remove-incomplete-activity-instances"></a><span data-ttu-id="6c49d-124">移除未完成的活動執行個體</span><span class="sxs-lookup"><span data-stu-id="6c49d-124">Remove incomplete activity instances</span></span>  
  
1.  <span data-ttu-id="6c49d-125">開啟**SQL Server Management Studio**，並連接到 SQL server。</span><span class="sxs-lookup"><span data-stu-id="6c49d-125">Open **SQL Server Management Studio**, and connect to the SQL server.</span></span>
  
2.  <span data-ttu-id="6c49d-126">依序展開伺服器名稱**資料庫**，然後選取 BAM 主要匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="6c49d-126">Expand the server name, expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
3.  <span data-ttu-id="6c49d-127">按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="6c49d-127">Click **New Query**.</span></span>  
  
4.  <span data-ttu-id="6c49d-128">在 [查詢] 窗格中，輸入`exec RemoveDanglingInstances`和適當的參數，您要執行之移除作業。</span><span class="sxs-lookup"><span data-stu-id="6c49d-128">In the query pane, type `exec RemoveDanglingInstances` and the appropriate parameters for the remove operation you are performing.</span></span> <span data-ttu-id="6c49d-129">例如，若要移除 Purchase Order 活動的所有未完成執行個體，請輸入 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`。</span><span class="sxs-lookup"><span data-stu-id="6c49d-129">For example, to remove all incomplete instances of the Purchase Order activity, type `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`.</span></span>  
  
5.  <span data-ttu-id="6c49d-130">**執行**指令碼。</span><span class="sxs-lookup"><span data-stu-id="6c49d-130">**Execute** the script.</span></span>  
  
## <a name="removedanglinginstances-usage-examples"></a><span data-ttu-id="6c49d-131">RemoveDanglingInstances 使用範例</span><span class="sxs-lookup"><span data-stu-id="6c49d-131">RemoveDanglingInstances Usage Examples</span></span>  
 <span data-ttu-id="6c49d-132">此預存程序可以接收 4 個參數：</span><span class="sxs-lookup"><span data-stu-id="6c49d-132">The stored procedure can receive four parameters:</span></span>  
  
|<span data-ttu-id="6c49d-133">參數</span><span class="sxs-lookup"><span data-stu-id="6c49d-133">Parameter</span></span>|<span data-ttu-id="6c49d-134">描述</span><span class="sxs-lookup"><span data-stu-id="6c49d-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c49d-135">@ActivityName nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="6c49d-135">@ActivityName nvarchar(128)</span></span>|<span data-ttu-id="6c49d-136">指定要移除的未完成活動執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="6c49d-136">Specifies the name of the incomplete activity instance to remove.</span></span>|  
|<span data-ttu-id="6c49d-137">@ActivityId nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="6c49d-137">@ActivityId nvarchar(128)</span></span>|<span data-ttu-id="6c49d-138">(選擇性) 指定預存程序只移除具有指定之執行個體識別項的懸空執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c49d-138">(Optional) Specifies that the stored procedure remove only the dangling instance with the specified instance identifier.</span></span>|  
|<span data-ttu-id="6c49d-139">@DateThreshold 日期時間</span><span class="sxs-lookup"><span data-stu-id="6c49d-139">@DateThreshold datetime</span></span>|<span data-ttu-id="6c49d-140">(選擇性) 指定移除作用資料表中早於指定之日期 (不含等於此日期) 的所有作用中執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c49d-140">(Optional) Specifies that all the active instances in the active table that are older (not equal to and older, only older) than the given date are removed.</span></span>|  
|<span data-ttu-id="6c49d-141">@NewTableExtension nvarchar(30)</span><span class="sxs-lookup"><span data-stu-id="6c49d-141">@NewTableExtension nvarchar(30)</span></span>|<span data-ttu-id="6c49d-142">(選擇性) 指定預存程序藉由串連所提供的延伸模組與現有活動資料表，建立三個新資料表。</span><span class="sxs-lookup"><span data-stu-id="6c49d-142">(Optional) Specifies that the stored procedure creates three new tables by concatenating the supplied extension to the existing activity tables.</span></span><br /><br /> <span data-ttu-id="6c49d-143">產生的資料表為：</span><span class="sxs-lookup"><span data-stu-id="6c49d-143">The resulting tables will be:</span></span><br /><br /> <span data-ttu-id="6c49d-144">bam_ActivityName_Active_\<Extension\></span><span class="sxs-lookup"><span data-stu-id="6c49d-144">bam_ActivityName_Active_\<Extension\></span></span><br /><br /> <span data-ttu-id="6c49d-145">bam_ActivityName_ActiveRelationships_\<Extension\></span><span class="sxs-lookup"><span data-stu-id="6c49d-145">bam_ActivityName_ActiveRelationships_\<Extension\></span></span><br /><br /> <span data-ttu-id="6c49d-146">bam_ActivityName_Continuations_\<Extension\></span><span class="sxs-lookup"><span data-stu-id="6c49d-146">bam_ActivityName_Continuations_\<Extension\></span></span><br /><br /> <span data-ttu-id="6c49d-147">未完成的執行個體會移至新資料表，而不會從資料庫清除。</span><span class="sxs-lookup"><span data-stu-id="6c49d-147">The incomplete instances are moved to the new tables rather than being purged from the database.</span></span><br /><br /> <span data-ttu-id="6c49d-148">如果資料表已存在，預存程序便會重複加以使用，否則會建立這些資料表。</span><span class="sxs-lookup"><span data-stu-id="6c49d-148">If the tables already exist, the stored procedure reuses them; otherwise they are created.</span></span> <span data-ttu-id="6c49d-149">**重要事項：** 如果資料表已存在，預存程序會假設其結構描述比對會在建立時所使用的項目。</span><span class="sxs-lookup"><span data-stu-id="6c49d-149">**Important:**  If the tables already exist, the stored procedure assumes that their schemas match the ones that would be used if they were created.</span></span> <span data-ttu-id="6c49d-150">如果結構描述不符合，預存程序將無法插入記錄，而且移除作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="6c49d-150">If a schema does not match, the stored procedure will fail to insert the records and the remove operation will fail.</span></span>|  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`  
  
 <span data-ttu-id="6c49d-151">移除作用中資料表、作用中關係資料表和接續資料表內 'PurchaseOrder' 活動的所有作用中執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c49d-151">Removes all active instances of the 'PurchaseOrder' activity in the active, active relationships, and continuations tables.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567'`  
  
 <span data-ttu-id="6c49d-152">從作用中資料表、作用中關係資料表和接續資料表，只移除具有活動識別碼 'PO220567' 之 'PurchaseOrder' 活動的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c49d-152">Removes only the activity instance that has an Activity ID of 'PO220567' from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 <span data-ttu-id="6c49d-153">從作用中資料表、作用中關係資料表和接續資料表，移除 LastModified 時間早於 2005 年 2 月 2 日下午 7:27:03.533 之 'PurchaseOrder' 活動的所有活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c49d-153">Removes all the activity instances that have a LastModified time that is older than Feb 2nd, 2005 7:27:03.533 PM from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 <span data-ttu-id="6c49d-154">只有在 LastModified 欄早於 2005 年 2 月 2 日下午 7:27:03.533 時，才移除活動識別碼為 PO220567 的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c49d-154">Removes the activity instance whose activity ID is PO220567 only if its LastModified column is older than Feb 2nd, 2005 7:27:03.533 PM.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533', @NewTableExtension=N'Dangling'`  
  
 <span data-ttu-id="6c49d-155">在資料庫中建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="6c49d-155">Creates the following tables in the database:</span></span>  
  
 <span data-ttu-id="6c49d-156">bam_PurchaseOrder_Active_Dangling</span><span class="sxs-lookup"><span data-stu-id="6c49d-156">bam_PurchaseOrder_Active_Dangling</span></span>  
  
 <span data-ttu-id="6c49d-157">bam_PurchaseOrder_ActiveRelationships_Dangling</span><span class="sxs-lookup"><span data-stu-id="6c49d-157">bam_PurchaseOrder_ActiveRelationships_Dangling</span></span>  
  
 <span data-ttu-id="6c49d-158">bam_PurchaseOrder_Continuations_Dangling</span><span class="sxs-lookup"><span data-stu-id="6c49d-158">bam_PurchaseOrder_Continuations_Dangling</span></span>  
  
 <span data-ttu-id="6c49d-159">預存程序會從作用中資料表、作用中關係資料表和接續資料表，複製早於 2005 年 2 月 2 日下午 7:27:03.533 之 'PurchaseOrder' 活動的所有未完成活動執行個體，並將它們插入新建的資料表中。</span><span class="sxs-lookup"><span data-stu-id="6c49d-159">The stored procedure copies all incomplete activity instances that are older than Feb 2nd, 2005 7:27:03.533 PM from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity, and inserts them into the newly created tables.</span></span> <span data-ttu-id="6c49d-160">接著從作用中資料表、作用中關係資料表和接續資料表移除已複製的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c49d-160">The copied activity instances are then removed from the active, active relationships, and continuations tables.</span></span>  
  
## <a name="stored-procedure-creation-script"></a><span data-ttu-id="6c49d-161">預存程序建立指令碼</span><span class="sxs-lookup"><span data-stu-id="6c49d-161">Stored Procedure Creation Script</span></span>  
  
```  
EXEC sp_stored_procedures @sp_name = 'RemoveDanglingInstances'  
IF @@ROWCOUNT > 0 DROP PROCEDURE RemoveDanglingInstances  
GO  
  
CREATE PROCEDURE RemoveDanglingInstances  
    @ActivityName nvarchar(128),  
    @ActivityId nvarchar(128) = NULL,  
    @DateThreshold datetime = NULL,  
    @NewTableExtension nvarchar(30) = NULL  
AS  
    DECLARE @QueryString nvarchar(4000)  
    DECLARE @ActiveTableName sysname  
    DECLARE @ActiveRelationshipsTableName sysname  
    DECLARE @ContinuationsTableName sysname  
    DECLARE @DanglingActiveTableName sysname  
    DECLARE @DanglingActiveRelationshipsTableName sysname  
    DECLARE @DanglingContinuationsTableName sysname  
  
    SET @ActiveTableName = 'bam_' + @ActivityName + '_Active'  
    SET @ActiveRelationshipsTableName = 'bam_' + @ActivityName + '_ActiveRelationships'  
    SET @ContinuationsTableName = 'bam_' + @ActivityName + '_Continuations'  
  
    SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
    BEGIN TRAN  
  
    DECLARE @LockActivity nvarchar(128)  
    SELECT @LockActivity = ActivityName  
    FROM bam_Metadata_Activities WITH (XLOCK)  
    WHERE ActivityName = @ActivityName  
  
    EXEC sp_tables @table_name = #DanglingActivities  
    IF @@ROWCOUNT > 0 DROP TABLE #DanglingActivities  
  
    CREATE TABLE #DanglingActivities(ActivityID nvarchar(128) PRIMARY KEY)  
  
    SET @QueryString = N'INSERT INTO #DanglingActivities (ActivityID) SELECT ActivityID FROM [bam_' + @ActivityName + '_Active]'  
  
    IF (@DateThreshold is not NULL) OR (@ActivityId is not NULL)  
    BEGIN  
        SET @QueryString = @QueryString + ' WHERE'  
    END  
  
    IF (@DateThreshold is not NULL)  
    BEGIN  
        SET @QueryString = @QueryString + ' LastModified < N''' + CONVERT(nvarchar(50), @DateThreshold, 109) + ''''  
        IF (@ActivityId is not NULL)  
        BEGIN  
            SET @QueryString = @QueryString + ' AND'  
        END  
    END  
  
    IF (@ActivityId is not NULL)  
    BEGIN  
        SET @QueryString = @QueryString + ' ActivityID = N''' + @ActivityId + ''''  
    END  
  
    EXEC sp_executesql @QueryString  
    SELECT * FROM #DanglingActivities  
  
    SET @QueryString = N''  
  
    -- If the user gave a table extension, the dangling instances will be inserted  
    -- into that table.   
    IF (isnull(@NewTableExtension, '') <> '')  
    BEGIN  
        SET @DanglingActiveTableName = @ActiveTableName + '_' + @NewTableExtension  
        SET @DanglingActiveRelationshipsTableName = @ActiveRelationshipsTableName + '_' + @NewTableExtension  
        SET @DanglingContinuationsTableName = @ContinuationsTableName + '_' + @NewTableExtension  
  
        -- If the table for the dangling instances exists then insert into it  
        -- If the table does not exist, then create the dangling instances table  
        -- and then insert into it. SELECT INTO will do that.  
        EXEC sp_tables @table_name = @DanglingActiveTableName  
        IF @@ROWCOUNT > 0  
        BEGIN  
            SET @QueryString = N'INSERT INTO ' + '[' + @DanglingActiveTableName + '] SELECT active.* FROM [' + @ActiveTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
        ELSE  
        BEGIN  
            SET @QueryString = N'SELECT active.* INTO [' + @DanglingActiveTableName + '] FROM [' + @ActiveTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
  
        -- Now do what you did for the Active Instances table for the   
        -- ActiveRelationships table  
        EXEC sp_tables @table_name = @DanglingActiveRelationshipsTableName  
        IF @@ROWCOUNT > 0  
        BEGIN  
            SET @QueryString = N'INSERT INTO ' + '[' + @DanglingActiveRelationshipsTableName + '] SELECT active.* FROM [' + @ActiveRelationshipsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
        ELSE  
        BEGIN  
            SET @QueryString = N'SELECT active.* INTO [' + @DanglingActiveRelationshipsTableName + '] FROM [' + @ActiveRelationshipsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
  
        -- And finally for the continuations table  
        EXEC sp_tables @table_name = @DanglingContinuationsTableName  
        IF @@ROWCOUNT > 0  
        BEGIN  
            SET @QueryString = N'INSERT INTO ' + '[' + @DanglingContinuationsTableName + '] SELECT active.* FROM [' + @ContinuationsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ParentActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
        ELSE  
        BEGIN  
            SET @QueryString = N'SELECT active.* INTO [' + @DanglingContinuationsTableName + '] FROM [' + @ContinuationsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ParentActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
    END  
  
    -- Remove the dangling instances from the Active Instances Table  
    SET @QueryString = 'DELETE FROM [' + @ActiveTableName + '] FROM [' + @ActiveTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID '  
    EXEC sp_executesql @QueryString  
  
    SET @QueryString = 'DELETE FROM [' + @ActiveRelationshipsTableName + '] FROM [' + @ActiveRelationshipsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID '  
    EXEC sp_executesql @QueryString  
  
    SET @QueryString = 'DELETE FROM [' + @ContinuationsTableName + '] FROM [' + @ContinuationsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ParentActivityID = dangling.ActivityID '  
    EXEC sp_executesql @QueryString  
  
    DROP TABLE #DanglingActivities  
  
    COMMIT TRAN      
GO  
```  

## <a name="another-method-of-resolving-incomplete-instances"></a><span data-ttu-id="6c49d-162">解析不完整的執行個體的另一種方法</span><span class="sxs-lookup"><span data-stu-id="6c49d-162">Another method of resolving incomplete instances</span></span>
<span data-ttu-id="6c49d-163">您也可以使用 SQL 查詢，以解析從 BAMPrimaryImport 資料庫的未完成的活動執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c49d-163">You can also resolve incomplete activity instances from the BAMPrimaryImport database by using a SQL query.</span></span> <span data-ttu-id="6c49d-164">請參閱[解析未完成的活動執行個體](how-to-resolve-incomplete-activity-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="6c49d-164">See [Resolve incomplete activity instances](how-to-resolve-incomplete-activity-instances.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c49d-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c49d-165">See Also</span></span>  
 [<span data-ttu-id="6c49d-166">管理 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="6c49d-166">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)
