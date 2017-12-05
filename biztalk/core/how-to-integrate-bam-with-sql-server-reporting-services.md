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
ms.openlocfilehash: 8a55d0fa09267cc23d54533427da326e5028d3f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-integrate-bam-with-sql-server-reporting-services"></a><span data-ttu-id="ecbef-102">如何整合 BAM 與 SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="ecbef-102">How to Integrate BAM with SQL Server Reporting Services</span></span>
<span data-ttu-id="ecbef-103">根據 BAM 基礎結構中的資料來建立報表，會執行與任何其他 SQL Server 資料來源報表建立相關聯的一般工作。</span><span class="sxs-lookup"><span data-stu-id="ecbef-103">Creating a report based on data in the BAM infrastructure use the typical tasks associated with creating a report for any other SQL Server data source.</span></span> <span data-ttu-id="ecbef-104">如需有關使用報表設計師建立報表的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=82437](http://go.microsoft.com/fwlink/?LinkId=82437)。</span><span class="sxs-lookup"><span data-stu-id="ecbef-104">For more information about creating a report with Report Designer, see [http://go.microsoft.com/fwlink/?LinkId=82437](http://go.microsoft.com/fwlink/?LinkId=82437).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ecbef-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="ecbef-105">Prerequisites</span></span>  
 <span data-ttu-id="ecbef-106">您必須具有必要的權限，才能存取建立報表所需的資料。</span><span class="sxs-lookup"><span data-stu-id="ecbef-106">You must have permissions to access the data necessary to create the report.</span></span>  
  
### <a name="how-to-create-a-report-in-bam-by-using-sql-server-reporting-service"></a><span data-ttu-id="ecbef-107">如何使用 SQL Server Reporting Service 在 BAM 建立報表</span><span class="sxs-lookup"><span data-stu-id="ecbef-107">How to Create a Report in BAM by Using SQL Server Reporting Service</span></span>  
  
1.  <span data-ttu-id="ecbef-108">選取要建立之報表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="ecbef-108">Select the data source from which to create the report.</span></span>  
  
     <span data-ttu-id="ecbef-109">BAM 提供兩個 Reporting Services 可指向的資料來源。</span><span class="sxs-lookup"><span data-stu-id="ecbef-109">BAM provides two data sources to which Reporting Services can point.</span></span>  
  
    |<span data-ttu-id="ecbef-110">資料來源</span><span class="sxs-lookup"><span data-stu-id="ecbef-110">Data Source</span></span>|<span data-ttu-id="ecbef-111">Description</span><span class="sxs-lookup"><span data-stu-id="ecbef-111">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="ecbef-112">BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="ecbef-112">BAM Primary Import database</span></span>|<span data-ttu-id="ecbef-113">包含活動執行個體和即時彙總的檢視。</span><span class="sxs-lookup"><span data-stu-id="ecbef-113">Contains views on activity instances and real-time aggregations.</span></span> <span data-ttu-id="ecbef-114">選取 類型 ="Microsoft SQL Server"以及 Connection String ="資料來源 =\<*伺服器名稱*\>;初始目錄 =\<*資料庫名稱*\>"，其中\<*伺服器名稱*\>和\<*資料庫名稱*\>是 Bam 主要匯入資料庫的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ecbef-114">Select Type=”Microsoft SQL Server” and Connection String=”Data Source=\<*server name*\>; Initial Catalog=\<*database name*\>”, where \<*server name*\> and \<*database name*\> are the server and database names of your Bam Primary Import database.</span></span>|  
    |<span data-ttu-id="ecbef-115">BAM 分析資料庫</span><span class="sxs-lookup"><span data-stu-id="ecbef-115">BAM Analysis database</span></span>|<span data-ttu-id="ecbef-116">包含用來查詢分析 Cube 的資料。</span><span class="sxs-lookup"><span data-stu-id="ecbef-116">Contains data that is used to query the analysis cube.</span></span> <span data-ttu-id="ecbef-117">選取 類型 ="Microsoft SQL Server Analysis Server"以及 Connection String ="資料來源 =\<*伺服器名稱*\>;初始目錄 =\<*資料庫名稱*\>"，其中\<*伺服器名稱*\>和\<*資料庫名稱*\>是 BAM 分析資料庫的伺服器和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ecbef-117">Select Type=”Microsoft SQL Server Analysis Server” and Connection String=”Data Source=\<*server name*\>; Initial Catalog=\<*database name*\>”, where \<*server name*\> and \<*database name*\> are the server and database names of your BAM Analysis database.</span></span>|  
  
2.  <span data-ttu-id="ecbef-118">設計查詢。</span><span class="sxs-lookup"><span data-stu-id="ecbef-118">Design the query.</span></span> <span data-ttu-id="ecbef-119">BAM 主要匯入資料庫有兩種類型的檢視：</span><span class="sxs-lookup"><span data-stu-id="ecbef-119">For the BAM Primary Import database, there are two types of views:</span></span>  
  
    |<span data-ttu-id="ecbef-120">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="ecbef-120">View Name</span></span>|<span data-ttu-id="ecbef-121">Description</span><span class="sxs-lookup"><span data-stu-id="ecbef-121">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="ecbef-122">dbo.bam_\<*檢視名稱*\>_\<*活動名稱*\>View_View。</span><span class="sxs-lookup"><span data-stu-id="ecbef-122">dbo.bam_\<*view name*\>_\<*activity name*\>View_View.</span></span>|<span data-ttu-id="ecbef-123">這個檢視包含執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="ecbef-123">This view contains instance data.</span></span>|  
    |<span data-ttu-id="ecbef-124">dbo.bam_\<*檢視名稱*\>_\<*即時彙總樞紐分析表名稱*\>_RTAView</span><span class="sxs-lookup"><span data-stu-id="ecbef-124">dbo.bam_\<*view name*\>_\<*real time aggregation pivot table name*\>_RTAView</span></span>|<span data-ttu-id="ecbef-125">這個檢視包含即時彙總中使用的資料。</span><span class="sxs-lookup"><span data-stu-id="ecbef-125">This view contains data used in real-time aggregations.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="ecbef-126">您可以輸入**選取\*從檢視**以傳回所要的結果集。</span><span class="sxs-lookup"><span data-stu-id="ecbef-126">You can type **select \* from view** to return the desired result set.</span></span> <span data-ttu-id="ecbef-127">BAM 分析資料庫中，按一下 [查詢產生器]，維度和 cube 的量值拖曳\<*檢視名稱*\>以傳回所要的結果集。</span><span class="sxs-lookup"><span data-stu-id="ecbef-127">For the BAM Analysis database, click the query builder and drag the dimensions and measures of the cube named \<*view name*\> to return the desired result set.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ecbef-128">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ecbef-128">Next Steps</span></span>  
 <span data-ttu-id="ecbef-129">完成 [報表精靈] 中的步驟，指定您要顯示的資料和顯示方式。</span><span class="sxs-lookup"><span data-stu-id="ecbef-129">Complete the steps in the Report Wizard to specify which data you are going to present and how the data is to be presented.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbef-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="ecbef-130">See Also</span></span>  
 [<span data-ttu-id="ecbef-131">管理 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="ecbef-131">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)