---
title: "BAM 工作流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring business activities [BAM], collecting business data
- XML files
- orchestrations, XML files
- business activities, business data
- infrastructure, managing [BAM]
- business activities, monitoring
- monitoring business activities [BAM], monitoring flow
- managing [BAM], infrastructure
- monitoring business activities [BAM], viewing business data
- managing [orchestrations], mapping XML to orchestrations
ms.assetid: 8b4ae145-3e16-4bb8-bfba-09b9f666218d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19356d6191963ec441f0b85c0e987c8515dcf1f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-workflow"></a><span data-ttu-id="5942d-102">BAM 工作流程</span><span class="sxs-lookup"><span data-stu-id="5942d-102">BAM Workflow</span></span>
<span data-ttu-id="5942d-103">下圖顯示四個與「商務活動監控」共同工作的使用者角色，以及其所使用的工具。</span><span class="sxs-lookup"><span data-stu-id="5942d-103">The following figure shows the four user roles who work with Business Activity Monitoring, and the tools that they use.</span></span>  
  
 ![](../core/media/ebiz-tut-bamworkflow.gif "ebiz_tut_bamworkflow")  
<span data-ttu-id="5942d-104">BAM 角色</span><span class="sxs-lookup"><span data-stu-id="5942d-104">BAM Roles</span></span>  
  
 <span data-ttu-id="5942d-105">下列步驟針對如何使用「商務活動監控」，提供其工作流程的高階概觀。</span><span class="sxs-lookup"><span data-stu-id="5942d-105">The following steps provide a high-level overview of the workflow for using Business Activity Monitoring.</span></span>  
  
## <a name="specifying-the-business-data-to-collect"></a><span data-ttu-id="5942d-106">指定要收集的商務資料</span><span class="sxs-lookup"><span data-stu-id="5942d-106">Specifying the business data to collect</span></span>  
 <span data-ttu-id="5942d-107">商務資料會以下列方式收集：</span><span class="sxs-lookup"><span data-stu-id="5942d-107">Business data is collected in the following manner:</span></span>  
  
-   <span data-ttu-id="5942d-108">商務分析師使用「BAM 活動精靈」來指定所有商務使用者所要收集的資料。</span><span class="sxs-lookup"><span data-stu-id="5942d-108">The business analyst uses the BAM Activity Wizard to specify what data to collect for all business users.</span></span>  
  
-   <span data-ttu-id="5942d-109">商務分析師使用「BAM 檢視精靈」來定義每個商務使用者類別的檢視。</span><span class="sxs-lookup"><span data-stu-id="5942d-109">The business analyst uses the BAM View Wizard to define the view for each category of business user.</span></span>  
  
-   <span data-ttu-id="5942d-110">完成定義後，他會在名為「BAM 定義活頁簿」的 Microsoft® Excel 活頁簿中儲存活動和檢視。</span><span class="sxs-lookup"><span data-stu-id="5942d-110">When finished, he saves the activities and views in a Microsoft® Excel Workbook called the BAM Definition Workbook.</span></span>  
  
-   <span data-ttu-id="5942d-111">商務分析師可以將「BAM 定義活頁簿」匯出為 XML。</span><span class="sxs-lookup"><span data-stu-id="5942d-111">The business analyst exports the BAM Definition Workbook to XML.</span></span>  
  
-   <span data-ttu-id="5942d-112">系統管理員和開發人員則使用 XML 來執行各自的角色。</span><span class="sxs-lookup"><span data-stu-id="5942d-112">The system administrator and developer use the XML to perform their roles.</span></span>  
  
-   <span data-ttu-id="5942d-113">使用 「 BAM 定義活頁簿的指示都位於[定義商務活動和在 Excel 中的檢視](../core/defining-business-activities-and-views-in-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="5942d-113">Instructions for using the BAM Definition Workbook are located in [Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md).</span></span>  
  
## <a name="managing-the-bam-infrastructure"></a><span data-ttu-id="5942d-114">管理 BAM 基礎結構</span><span class="sxs-lookup"><span data-stu-id="5942d-114">Managing the BAM Infrastructure</span></span>  
 <span data-ttu-id="5942d-115">商務分析師定義過所需的 BAM 檢視後，系統管理員會使用命令列工具「BAM 管理公用程式」(BM.EXE)，從「BAM 定義活頁簿」或由活頁簿所匯出的 XML 中部署 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="5942d-115">After the business analyst has defined the BAM view he wants, the system administrator uses the BAM management utility (BM.EXE), a command-line tool, to deploy the BAM infrastructure from the BAM Definition Workbook or the XML exported from the workbook.</span></span>  
  
 <span data-ttu-id="5942d-116">BAM 管理公用程式會動態建立支援 BAM 檢視所需的資料表、觸發程序、DTS 封裝和 OLAP Cube。</span><span class="sxs-lookup"><span data-stu-id="5942d-116">The BAM management utility dynamically creates the tables, triggers, DTS packages, and OLAP cubes necessary to support the BAM view.</span></span>  
  
 <span data-ttu-id="5942d-117">每當商務分析師定義不同的 BAM 檢視，或變更現有的 BAM 檢視時，系統管理員都必須重新部署 BAM 定義活頁簿。</span><span class="sxs-lookup"><span data-stu-id="5942d-117">Each time the business analyst defines a different BAM view, or changes an existing BAM view, the system administrator must redeploy the BAM Definition Workbook.</span></span>  
  
## <a name="mapping-the-xml-to-an-orchestration"></a><span data-ttu-id="5942d-118">對應 XML 至協調流程</span><span class="sxs-lookup"><span data-stu-id="5942d-118">Mapping the XML to an orchestration</span></span>  
 <span data-ttu-id="5942d-119">商務分析師將「BAM 定義活頁簿」匯出為 XML 後，開發人員會將 XML 檔案匯入至「追蹤設定檔編輯器」。</span><span class="sxs-lookup"><span data-stu-id="5942d-119">After the business analyst exports the BAM Definition Workbook to XML, the developer imports the XML file into the Tracking Profile Editor.</span></span> <span data-ttu-id="5942d-120">開發人員則實作商務分析師的資訊需求，將 XML 對應到協調流程。</span><span class="sxs-lookup"><span data-stu-id="5942d-120">The developer implements the business analyst's information requirements, mapping the XML to an orchestration.</span></span>  
  
 <span data-ttu-id="5942d-121">使用「追蹤設定檔編輯器」時，開發人員可以執行下列步驟，將 XML 對應到協調流程：</span><span class="sxs-lookup"><span data-stu-id="5942d-121">Using the Tracking Profile Editor, the developer performs the following steps to map the XML to an orchestration:</span></span>  
  
-   <span data-ttu-id="5942d-122">將儲存在 BizTalk 管理資料庫 (也稱為組態資料庫) 中的部署組件載入。</span><span class="sxs-lookup"><span data-stu-id="5942d-122">Loads the deployed assembly that is stored in the BizTalk Management database (also known as the Configuration database).</span></span> <span data-ttu-id="5942d-123">部署的組件包含一或多個協調流程，對應至商務分析師在上述「步驟 1」指定的需求。</span><span class="sxs-lookup"><span data-stu-id="5942d-123">The deployed assembly contains one or more orchestrations corresponding to the requirements that the business analyst specified in Step 1 above.</span></span>  
  
-   <span data-ttu-id="5942d-124">定義要從協調流程中擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="5942d-124">Defines the data to be extracted from an orchestration.</span></span> <span data-ttu-id="5942d-125">若要這麼做，您可以將項目從訊息結構描述和協調流程圖形放置在適當的商務里程碑 (事件) 和資料項目資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5942d-125">You do this by dropping items from the message schemas and orchestration shapes into the appropriate business milestone (event) and data item folders.</span></span>  
  
-   <span data-ttu-id="5942d-126">完成後，他會在存放資料庫 (如 Visual SourceSafe) 中，將設定檔儲存為 BizTalk® Server 追蹤 (.btt) 檔案。</span><span class="sxs-lookup"><span data-stu-id="5942d-126">When he is finished, he saves the profile as a BizTalk® Server tracking (.btt) file, to a storage database such as Visual SourceSafe.</span></span>  
  
 <span data-ttu-id="5942d-127">開發人員再將 .btt 檔案部署到測試資料庫，並透過整合測試確認結果。</span><span class="sxs-lookup"><span data-stu-id="5942d-127">The developer deploys the .btt file to a testing database, and verifies the result through integration testing.</span></span>  
  
## <a name="deploying-the-tracking-profile"></a><span data-ttu-id="5942d-128">部署追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="5942d-128">Deploying the Tracking Profile</span></span>  
 <span data-ttu-id="5942d-129">使用「追蹤設定檔編輯器」時，系統管理員可以將設定檔部署到一或多個 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="5942d-129">Using the Tracking Profile Editor, the system administrator deploys the profile to one or more BizTalk Management databases.</span></span>  
  
 <span data-ttu-id="5942d-130">每當開發人員變更協調流程，或商務使用者需求變更而要追蹤更多資料時，系統管理員都必須使用命令列公用程式 bttdeploy.exe 來重新部署追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="5942d-130">Each time the developer changes the orchestration, or the requirements of the business users change and they want to track more data, the system administrator needs to redeploy the tracking profile using the bttdeploy.exe command line utility.</span></span>  
  
## <a name="viewing-the-business-data"></a><span data-ttu-id="5942d-131">檢視商務資料</span><span class="sxs-lookup"><span data-stu-id="5942d-131">Viewing the business data</span></span>  
 <span data-ttu-id="5942d-132">商務使用者使用由 BM.exe 公用程式產生的 _LiveData 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="5942d-132">The business user uses the _LiveData workbook, which is produced by the BM.exe utility.</span></span> <span data-ttu-id="5942d-133">每當商務使用者開啟 _LiveData 活頁簿時，都會收到最新版的即時資料，這些資料是收集用來監控商務程序的特定層面。</span><span class="sxs-lookup"><span data-stu-id="5942d-133">Each time the business user opens the _LiveData workbook, he receives a new live version of the data that is collected to monitor a specific aspect of the business process.</span></span>  
  
-   <span data-ttu-id="5942d-134">若要檢視定義為即時彙總的資料，商務使用者只需按一下**重新整理**要檢視資料的活頁簿中。</span><span class="sxs-lookup"><span data-stu-id="5942d-134">To view data that is defined as real-time aggregation, the business user just needs to click **Refresh** in the workbook to view the data.</span></span>  
  
-   <span data-ttu-id="5942d-135">如果彙總資料不是即時的，商務使用者可以檢視排程 DTS 封裝在執行時所攝取的商務資料快照集。</span><span class="sxs-lookup"><span data-stu-id="5942d-135">If the aggregation data is not real-time, the business user views a snapshot of the business data that is taken at the time that the scheduled DTS package runs.</span></span>  
  
-   <span data-ttu-id="5942d-136">如果您的組織有協同作業的需求，商務使用者可以從 BAS Web 網站存取即時資料。</span><span class="sxs-lookup"><span data-stu-id="5942d-136">If your organization has collaboration requirements, the business user can access the live data from the BAS Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5942d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5942d-137">See Also</span></span>  
 <span data-ttu-id="5942d-138">[在 Excel 中定義商務活動和檢視](../core/defining-business-activities-and-views-in-excel.md) </span><span class="sxs-lookup"><span data-stu-id="5942d-138">[Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md) </span></span>  
 [<span data-ttu-id="5942d-139">使用 BAM 監控商務活動</span><span class="sxs-lookup"><span data-stu-id="5942d-139">Monitoring Business Activities with BAM</span></span>](../core/monitoring-business-activities-with-bam.md)