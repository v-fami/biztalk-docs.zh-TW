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
# <a name="remove-incomplete-activity-instances"></a>移除未完成的活動執行個體
部署 BAM 定義檔案時，會為定義檔案中所定義的每個活動，在 BAM 主要匯入資料庫中建立五個資料表， 分別是：  
  
- bam_`ActivityName`_Active  
  
- bam_`ActivityName`_Completed  
  
- bam_`ActivityName`_ActiveRelationships  
  
- bam_`ActivityName`_CompletedRelationships  
  
- bam_`ActivityName`_Continuations  
  
  其中 `ActivityName` 是使用者定義的活動名稱。  
  
  正常執行時，不完整的資料會保留在 bam_`ActivityName`*作用中的資料表。如果資料含有關係與參考，則資料會出在 bam\\*`ActivityName`_ActiveRelationships 資料表。  
  
  追蹤使用接續的活動期間，有時候在 BAM 資料庫中的活動可能處在未完成狀態。 您可以使用本主題最後的預存程序建立指令碼，來建立將清除不完整記錄的預存程序。  
  
  如果要建立預存程序，使用 SQL Server Management 複製指令碼並針對 BAM 主要匯入資料庫執行指令碼。 此指令碼會產生名為預存程序**RemoveDanglingInstances**資料庫中。  
  
## <a name="create-the-removedanglinginstances-stored-procedure"></a>建立 RemoveDanglingInstances 預存程序  
  
1.  開啟**SQL Server Management Studio**，並連接到 SQL server。
  
2.  依序展開伺服器名稱**資料庫**，然後選取 BAM 主要匯入資料庫。  
  
3.  按一下 **[新增查詢]**。  
  
4.  複製預存程序建立指令碼，並將它貼到 [查詢] 窗格。  
  
5.  **執行**指令碼。 產生的預存程序會在預存程序清單中顯示為 dbo.RemoveDanglingInstances。  
  
## <a name="remove-incomplete-activity-instances"></a>移除未完成的活動執行個體  
  
1.  開啟**SQL Server Management Studio**，並連接到 SQL server。
  
2.  依序展開伺服器名稱**資料庫**，然後選取 BAM 主要匯入資料庫。  
  
3.  按一下 **[新增查詢]**。  
  
4.  在 [查詢] 窗格中，輸入`exec RemoveDanglingInstances`和適當的參數，您要執行之移除作業。 例如，若要移除 Purchase Order 活動的所有未完成執行個體，請輸入 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`。  
  
5.  **執行**指令碼。  
  
## <a name="removedanglinginstances-usage-examples"></a>RemoveDanglingInstances 使用範例  
 此預存程序可以接收 4 個參數：  
  
|參數|描述|  
|---------------|-----------------|  
|@ActivityName nvarchar(128)|指定要移除的未完成活動執行個體名稱。|  
|@ActivityId nvarchar(128)|(選擇性) 指定預存程序只移除具有指定之執行個體識別項的懸空執行個體。|  
|@DateThreshold 日期時間|(選擇性) 指定移除作用資料表中早於指定之日期 (不含等於此日期) 的所有作用中執行個體。|  
|@NewTableExtension nvarchar(30)|(選擇性) 指定預存程序藉由串連所提供的延伸模組與現有活動資料表，建立三個新資料表。<br /><br /> 產生的資料表為：<br /><br /> bam_ActivityName_Active_\<Extension\><br /><br /> bam_ActivityName_ActiveRelationships_\<Extension\><br /><br /> bam_ActivityName_Continuations_\<Extension\><br /><br /> 未完成的執行個體會移至新資料表，而不會從資料庫清除。<br /><br /> 如果資料表已存在，預存程序便會重複加以使用，否則會建立這些資料表。 **重要事項：** 如果資料表已存在，預存程序會假設其結構描述比對會在建立時所使用的項目。 如果結構描述不符合，預存程序將無法插入記錄，而且移除作業會失敗。|  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`  
  
 移除作用中資料表、作用中關係資料表和接續資料表內 'PurchaseOrder' 活動的所有作用中執行個體。  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567'`  
  
 從作用中資料表、作用中關係資料表和接續資料表，只移除具有活動識別碼 'PO220567' 之 'PurchaseOrder' 活動的活動執行個體。  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 從作用中資料表、作用中關係資料表和接續資料表，移除 LastModified 時間早於 2005 年 2 月 2 日下午 7:27:03.533 之 'PurchaseOrder' 活動的所有活動執行個體。  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 只有在 LastModified 欄早於 2005 年 2 月 2 日下午 7:27:03.533 時，才移除活動識別碼為 PO220567 的活動執行個體。  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533', @NewTableExtension=N'Dangling'`  
  
 在資料庫中建立下列資料表：  
  
 bam_PurchaseOrder_Active_Dangling  
  
 bam_PurchaseOrder_ActiveRelationships_Dangling  
  
 bam_PurchaseOrder_Continuations_Dangling  
  
 預存程序會從作用中資料表、作用中關係資料表和接續資料表，複製早於 2005 年 2 月 2 日下午 7:27:03.533 之 'PurchaseOrder' 活動的所有未完成活動執行個體，並將它們插入新建的資料表中。 接著從作用中資料表、作用中關係資料表和接續資料表移除已複製的活動執行個體。  
  
## <a name="stored-procedure-creation-script"></a>預存程序建立指令碼  
  
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

## <a name="another-method-of-resolving-incomplete-instances"></a>解析不完整的執行個體的另一種方法
您也可以使用 SQL 查詢，以解析從 BAMPrimaryImport 資料庫的未完成的活動執行個體。 請參閱[解析未完成的活動執行個體](how-to-resolve-incomplete-activity-instances.md)。

## <a name="see-also"></a>另請參閱  
 [管理 BAM 資料庫](../core/managing-bam-databases.md)
