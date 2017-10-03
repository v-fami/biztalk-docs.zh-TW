---
title: "如何整合 BAM 與 SQL Server Reporting Services |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e2d66b7-c8eb-4871-8a47-544955ccd51e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61478bde3dd224029a6e3d6fd7c73ee84554f93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-integrate-bam-with-sql-server-reporting-services"></a>如何整合 BAM 與 SQL Server Reporting Services
根據 BAM 基礎結構中的資料來建立報表，會執行與任何其他 SQL Server 資料來源報表建立相關聯的一般工作。 如需有關使用報表設計師建立報表的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=82437](http://go.microsoft.com/fwlink/?LinkId=82437)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須具有必要的權限，才能存取建立報表所需的資料。  
  
### <a name="how-to-create-a-report-in-bam-by-using-sql-server-reporting-service"></a>如何使用 SQL Server Reporting Service 在 BAM 建立報表  
  
1.  選取要建立之報表的資料來源。  
  
     BAM 提供兩個 Reporting Services 可指向的資料來源。  
  
    |資料來源|Description|  
    |-----------------|-----------------|  
    |BAM 主要匯入資料庫|包含活動執行個體和即時彙總的檢視。 選取 類型 ="Microsoft SQL Server"以及 Connection String ="資料來源 =\<*伺服器名稱*>;初始目錄 =\<*資料庫名稱*>"，其中\<*伺服器名稱*> 和\<*資料庫名稱*> 是Bam 主要匯入資料庫的伺服器和資料庫名稱。|  
    |BAM 分析資料庫|包含用來查詢分析 Cube 的資料。 選取 類型 ="Microsoft SQL Server Analysis Server"以及 Connection String ="資料來源 =\<*伺服器名稱*>;初始目錄 =\<*資料庫名稱*>"，其中\<*伺服器名稱*> 和\<*資料庫名稱*> 是BAM 分析資料庫的伺服器和資料庫名稱。|  
  
2.  設計查詢。 BAM 主要匯入資料庫有兩種類型的檢視：  
  
    |檢視表名稱|Description|  
    |---------------|-----------------|  
    |dbo.bam_\<*檢視名稱*> _\<*活動名稱*> View_View。|這個檢視包含執行個體資料。|  
    |dbo.bam_\<*檢視名稱*> _\<*即時彙總樞紐分析表名稱*> _RTAView|這個檢視包含即時彙總中使用的資料。|  
  
    > [!NOTE]
    >  您可以輸入**選取\*從檢視**以傳回所要的結果集。 BAM 分析資料庫中，按一下 [查詢產生器]，維度和 cube 的量值拖曳\<*檢視名稱*> 以傳回所要的結果集。  
  
## <a name="next-steps"></a>後續步驟  
 完成 [報表精靈] 中的步驟，指定您要顯示的資料和顯示方式。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 資料庫](../core/managing-bam-databases.md)