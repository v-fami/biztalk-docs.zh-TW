---
title: 在封存資料庫中建立資料分割的檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases, partitioning
- partitioning
- Archive database [BAM], partitioning
ms.assetid: f9ef7480-2e37-4477-92c8-b5686ae9b54b
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42adf8f614f124c9b17597a44cdaaba9d7ed4f93
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968924"
---
# <a name="creating-a-partitioned-view-in-the-archiving-database"></a>在封存資料庫中建立分割檢視
當您執行 BAM 資料維護封裝 (BAM_DM_`<activity name>`) 時，BAM 會將 BAM 主要匯入資料庫中的每個資料分割各複製到 BAM 封存資料庫的不同資料表中。 如果您中斷封存資料庫的連線，然後重新連線以便進行查詢，將會發現很難找到您查詢的資料。  
  
 您可以在 BAM 封存資料庫中建立資料分割檢視，以便尋找資料。 BAM 支援最多 253 個資料分割。 BAM 會為每個活動各產生一個 BAM 資料維護 DTS 封裝，此封裝會將活動資料複製到 BAM 封存資料庫，再從 BAM 主要匯入資料庫移除該資料。 如果封存資料庫在複製資料後失敗，但是還沒到下一次備份，資料就會遺失。  
  
 預防資料遺失的解決方法是使用單一封存封裝，此封裝會先從所有活動中複製舊資料，再備份 BAM 封存資料庫，最後從主要匯入資料庫刪除先前複製的資料分割。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這個程序。  
  
### <a name="to-create-a-partitioned-view-in-the-bam-archive-database-in-sql-server-2008-sp1-or-sql-server-2008-r2"></a>若要使用 SQL Server 2008 SP1 或 SQL Server 2008 R2 在 BAM 封存資料庫中建立資料分割檢視  
  
1.  開啟 SQL Server Management Studio。  
  
2.  選取 BAM 封存資料庫，然後按一下**新查詢**。  
  
3.  在**查詢**功能表上，指向**結果至**，然後按一下 **以文字顯示結果**。  
  
4.  將下列 SQL 指令碼複製到查詢窗格中。 取代\<活動名稱\>與您的活動名稱取代`<view type>`其中一種**執行個體**執行個體檢視的或**關聯性**關聯性檢視。  
  
    ```  
    set nocount on  
  
    declare @activityName as nvarchar(128)  
    declare @viewType as nvarchar(50)  
    set @activityName = N'<activity name>'-- Substitute your activity name here  
    set @viewType = N'<view type>'-- Substitute the view type here, either "Instances" or "Relationships"  
  
    declare @tableName nvarchar(128)  
    declare @viewName nvarchar(128)  
    declare @isFirstTable bit  
    declare @scriptLine nvarchar(300)  
  
    set @viewName = N'bam_' + @activityName + '_' + @viewType + 'View'  
    select N'SELECT Name FROM sysobjects where name = N''' + @viewName + ''' and type = ''V'''   
     + char(13) + char(10) + 'IF @@ROWCOUNT > 0 DROP VIEW ' + @viewName   
     + char(13) + char(10) + 'GO'  
  
    select 'CREATE VIEW ' +  @viewName + ' AS ' + char(13) + char(10)  
  
    declare instance_cursor cursor local for  
    select name from sysobjects   
    where name like N'bam_' + @activityName + '_' + @viewType + '_%' and type = 'U'  
  
    SET @isFirstTable = 1  
    OPEN instance_cursor  
    FETCH NEXT FROM instance_cursor INTO @tableName  
  
    WHILE @@fetch_status = 0   
    BEGIN  
  
    if @isFirstTable = 1  
    BEGIN  
    SET @scriptLine = N'SELECT * FROM [' + @tableName + ']'  
    SET @isFirstTable = 0  
    END  
    ELSE  
    SET @scriptLine = N'UNION ALL SELECT * FROM [' + @tableName + ']'  
  
    SELECT @scriptLine  
  
    FETCH NEXT FROM instance_cursor INTO @tableName  
    END  
    CLOSE instance_cursor  
    DEALLOCATE instance_cursor  
  
    select 'GO'  
    set nocount off  
    ```  
  
5.  執行查詢。  
  
## <a name="see-also"></a>請參閱  
 [BAM DTS 封裝](../core/bam-dts-packages.md)   
 [如何備份 BAM 分析和追蹤 Analysis Server 資料庫](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)