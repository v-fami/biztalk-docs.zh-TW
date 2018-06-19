---
title: 何謂 BAM 定義？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- definitions [BAM], observation models
- definitions [BAM], about BAM definitions
- definitions [BAM]
ms.assetid: 1ba1f45e-85fe-492f-8a2e-98bf3570c633
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cbc600f66be7167aabb4cf0273cb1c0bda78973
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289678"
---
# <a name="what-is-a-bam-definition"></a><span data-ttu-id="b4cdf-103">何謂 BAM 定義？</span><span class="sxs-lookup"><span data-stu-id="b4cdf-103">What Is a BAM Definition?</span></span>
<span data-ttu-id="b4cdf-104">BAM 定義是 BAM 觀察模型的 XML 表示法，代表所監控之商務程序的高階定義。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-104">A BAM definition is an XML representation of a BAM observation model, which is a high-level definition a business process that you want to monitor.</span></span> <span data-ttu-id="b4cdf-105">觀察模型的主要部分包括里程碑和蒐集的資料事件 (BAM 活動)、任何資料彙總的描述，以及向使用者呈現資訊的方式 (BAM 檢視)；因此這些同樣也是 BAM 定義的主要部分。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-105">The main parts of the observation model, and therefore the BAM definition, are the milestone and data events to collect (the BAM activity); a description of any data aggregations; and how to present the information to users (the BAM view).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4cdf-106">您也可以手動建立遵循 BAM 結構描述的 XML 檔案，但不建議以此方式建立 BAM 定義，因為這類定義沒有經過驗證。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-106">You can also manually create an XML file that follows the BAM schema, but this is not a recommended way to create the BAM definition as it does not provide a definition that has been validated.</span></span>  
  
 <span data-ttu-id="b4cdf-107">BAM 定義可包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="b4cdf-107">BAM definitions can contain the following items:</span></span>  
  
-   <span data-ttu-id="b4cdf-108">商務活動 - 有效的 BAM 定義必須包含商務活動 (也稱為 BAM 活動)。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-108">Business activities - A valid BAM definition must contain a business activity (also referred to as a BAM activity).</span></span> <span data-ttu-id="b4cdf-109">定義中其餘所有項目皆為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-109">All other items in the definition are optional.</span></span> <span data-ttu-id="b4cdf-110">新增至定義商務活動的相關資訊，請參閱[如何定義商務活動](../core/how-to-define-a-business-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-110">For information about adding a business activity to a definition, see [How to Define a Business Activity](../core/how-to-define-a-business-activity.md).</span></span>  
  
-   <span data-ttu-id="b4cdf-111">檢視 – 檢視定義了能夠存取商務活動所定義之資料的使用者集合。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-111">Views – Views define the set of users that can access the data defined by the business activity.</span></span> <span data-ttu-id="b4cdf-112">檢視中包含篩選的資料、所篩選資料的彙總，以及呈現篩選資料的方式，例如樞紐分析圖報表。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-112">Views consist of filtered data, aggregations of the filtered data, and ways of presenting the filtered data, such as a PivotChart report.</span></span> <span data-ttu-id="b4cdf-113">每個 BAM 活動支援一或多個檢視的定義。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-113">BAM supports the definition of one or more views per activity.</span></span>  
  
     <span data-ttu-id="b4cdf-114">在檢視中可以定義下列商務程序：</span><span class="sxs-lookup"><span data-stu-id="b4cdf-114">In a view you can define the following business processes:</span></span>  
  
    -   <span data-ttu-id="b4cdf-115">別名商務資料 - 別名允許您對資料項目套用易記名稱。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-115">Aliased business data - Aliasing allows you to apply friendly names to data items.</span></span> <span data-ttu-id="b4cdf-116">例如，開發人員定義的資料項目名稱可能是 "LName"。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-116">For example, a developer may define a data item called “LName.”</span></span> <span data-ttu-id="b4cdf-117">您可以建立別名，以便於檢視 BAM 即時資料時將 “LName” 顯示為「姓氏」。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-117">You can create an alias so that the “LName” is displayed as “Last Name” when viewing the BAM live data.</span></span>  <span data-ttu-id="b4cdf-118">如需別名的詳細資訊，請參閱[如何重新命名檢視項目](../core/how-to-rename-view-items.md)。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-118">For more information about aliasing, see [How to Rename View Items](../core/how-to-rename-view-items.md).</span></span>  
  
    -   <span data-ttu-id="b4cdf-119">持續時間 - 監控活動的時間週期。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-119">Duration - The time period over which the activity is monitored.</span></span>  
  
    -   <span data-ttu-id="b4cdf-120">里程碑群組 - 一組商務里程碑。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-120">Milestone groups - Sets of business milestones.</span></span> <span data-ttu-id="b4cdf-121">您可以使用群組做為持續時間的開始或結束商務里程碑。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-121">You can use a group as either the starting or ending business milestone of a duration.</span></span>  
  
    -   <span data-ttu-id="b4cdf-122">彙總 - 可能是即時彙總 (RTA) 或排程彙總 (也稱為線上分析處理 (OLAP))，且包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="b4cdf-122">Aggregations -  These can be either real-time aggregations (RTAs) or scheduled aggregations (also referred to as online analytical processing (OLAP)), and consist of the following items:</span></span>  
  
-   <span data-ttu-id="b4cdf-123">量值 - 根據 Cube 事實資料表的資料行，在 Analysis Services (OLAP) Cube 中建立的數值集。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-123">Measures - A set of numeric values in an Analysis Services (OLAP) cube based on a column in the fact table of the cube.</span></span>  
  
-   <span data-ttu-id="b4cdf-124">進度維度 - 代表與仍在進行中之活動進度有關的彙總建立情況。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-124">Progress dimension - Represents the creation of aggregations with respect to the progress of activities that are still in process.</span></span>  
  
-   <span data-ttu-id="b4cdf-125">資料維度 - 用以將彙總分類。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-125">Data dimension - Used to categorize an aggregation.</span></span> <span data-ttu-id="b4cdf-126">資料維度是以 BAM 活動中的字串格式資料項目的值為依據。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-126">Data dimensions are based on the value of string formatted data items in the BAM activity.</span></span>  
  
-   <span data-ttu-id="b4cdf-127">時間維度 - 用以建立橫跨已定義時間區段的彙總。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-127">Time dimension - Used to create aggregations across defined time segments.</span></span>  
  
-   <span data-ttu-id="b4cdf-128">數字範圍維度 - 用以根據特定數字範圍的易記名稱將彙總分類。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-128">Numeric range dimension - Used to categorize aggregations based on friendly names of given numeric ranges.</span></span>  
  
 <span data-ttu-id="b4cdf-129">BAM 定義可以包含檢視中所定義的警示定義。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-129">BAM definitions can contain alert definitions that are defined in the views.</span></span> <span data-ttu-id="b4cdf-130">BAM 定義也能包含樞紐分析表版面配置。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-130">BAM definitions can also contain PivotTable layouts.</span></span> <span data-ttu-id="b4cdf-131">一旦部署 BAM 定義後，就能使用 Excel 即時資料活頁簿或透過 BAM 入口網站，檢視含有即時商務資料的樞紐分析表報表。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-131">Once the BAM definition is deployed, the PivotTable reports containing the live business data that can be viewed using the Excel livedata workbook or through the BAM portal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4cdf-132">使用 Excel 的 BAM 增益集所建立的 BAM 定義無法包含警示。</span><span class="sxs-lookup"><span data-stu-id="b4cdf-132">BAM definitions created using the BAM Add-in for Excel cannot contain alerts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4cdf-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4cdf-133">See Also</span></span>  
 <span data-ttu-id="b4cdf-134">[在 Excel 中定義商務活動和檢視](../core/defining-business-activities-and-views-in-excel.md) </span><span class="sxs-lookup"><span data-stu-id="b4cdf-134">[Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md) </span></span>  
 <span data-ttu-id="b4cdf-135">[BAM 入口網站](../core/bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="b4cdf-135">[BAM Portal](../core/bam-portal.md) </span></span>  
 [<span data-ttu-id="b4cdf-136">BAM 動態基礎結構</span><span class="sxs-lookup"><span data-stu-id="b4cdf-136">BAM Dynamic Infrastructure</span></span>](../core/bam-dynamic-infrastructure.md)