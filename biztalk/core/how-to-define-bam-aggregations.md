---
title: 如何定義 BAM 彙總 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, BAM
- aggregations [BAM], creating
- Excel add-in [BAM], security
- Excel add-in [BAM], creating aggregations
- managing [BAM], creating aggregations
ms.assetid: a5ef3a15-b1de-4099-8e94-64af4b5ec746
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57df4978f2b133794efd8fbdc99819bcedf144cb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015903"
---
# <a name="how-to-define-bam-aggregations"></a><span data-ttu-id="80171-102">如何定義 BAM 彙總</span><span class="sxs-lookup"><span data-stu-id="80171-102">How to Define BAM Aggregations</span></span>
<span data-ttu-id="80171-103">BAM 支援兩種資料彙總：</span><span class="sxs-lookup"><span data-stu-id="80171-103">BAM supports two types of data aggregation:</span></span>  
  
- <span data-ttu-id="80171-104">線上分析處理 (OLAP) 彙總</span><span class="sxs-lookup"><span data-stu-id="80171-104">Online analytical processing (OLAP) aggregations</span></span>  
  
- <span data-ttu-id="80171-105">即時彙總 (RTA)</span><span class="sxs-lookup"><span data-stu-id="80171-105">Real-time aggregations (RTA)</span></span>  
  
  <span data-ttu-id="80171-106">BAM 使用 Microsoft SQL Server Analysis Services 實作 OLAP 彙總。</span><span class="sxs-lookup"><span data-stu-id="80171-106">BAM uses Microsoft SQL Server Analysis Services to implement OLAP aggregations.</span></span>  
  
  <span data-ttu-id="80171-107">您必須在 BAM 主要匯入資料庫上設定定義 RTA 的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="80171-107">You must configure the triggers on the BAM Primary Import database that define RTA.</span></span>  
  
### <a name="to-define-olap-aggregations"></a><span data-ttu-id="80171-108">定義 OLAP 彙總</span><span class="sxs-lookup"><span data-stu-id="80171-108">To define OLAP aggregations</span></span>  
  
1.  <span data-ttu-id="80171-109">在 BAM Excel 活頁簿中，建立檢視，並至少在樞紐分析表中新增一個維度和一個量值，清除 RTA 工具列按鈕，然後儲存此活頁簿。</span><span class="sxs-lookup"><span data-stu-id="80171-109">In the BAM Excel workbook, create a view, add at least one dimension and one measure to the PivotTable report, clear the RTA toolbar button, and then save the workbook.</span></span>  
  
    -   <span data-ttu-id="80171-110">如需開啟 BAM 活頁簿，建立檢視，以及新增維度和量值，請參閱[定義 BAM 檢視](../core/defining-a-bam-view.md)。</span><span class="sxs-lookup"><span data-stu-id="80171-110">For information about opening the BAM workbook, creating a view, and adding dimensions and measures, see [Defining a BAM View](../core/defining-a-bam-view.md).</span></span>  
  
2.  <span data-ttu-id="80171-111">部署活頁簿。</span><span class="sxs-lookup"><span data-stu-id="80171-111">Deploy the workbook.</span></span>  
  
    -   <span data-ttu-id="80171-112">若要部署活頁簿，請依照下列中的指示[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)。</span><span class="sxs-lookup"><span data-stu-id="80171-112">To deploy the workbook, follow the instructions in [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
3.  <span data-ttu-id="80171-113">方案開發人員使用**DirectEventStream**匯入事件至 BAM 主要匯入資料庫的類別。</span><span class="sxs-lookup"><span data-stu-id="80171-113">A solutions developer uses the **DirectEventStream** class to import events into the BAM Primary Import database.</span></span>  
  
    -   <span data-ttu-id="80171-114">如需**DirectEventStream**類別，請參閱[DirectEventStream 類別](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx)。</span><span class="sxs-lookup"><span data-stu-id="80171-114">For information about the **DirectEventStream** class, see [DirectEventStream Class](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx).</span></span>  
  
4.  <span data-ttu-id="80171-115">執行更新 Cube Data Transformation Services (DTS) 封裝。</span><span class="sxs-lookup"><span data-stu-id="80171-115">Run the update cube Data Transformation Services (DTS) package.</span></span>  
  
    -   <span data-ttu-id="80171-116">如需執行更新 cube DTS 封裝的資訊，請參閱[BAM DTS 封裝](../core/bam-dts-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="80171-116">For information about running the update cube DTS package, see [BAM DTS Packages](../core/bam-dts-packages.md).</span></span>  
  
5.  <span data-ttu-id="80171-117">開啟此活頁簿最近的即時資料複本，以檢視 OLAP 彙總。</span><span class="sxs-lookup"><span data-stu-id="80171-117">Open the most recent live data copy of the workbook to see the OLAP aggregations.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="80171-118">基於安全性理由，BAM 不會刪除活頁簿現有的即時資料複本，</span><span class="sxs-lookup"><span data-stu-id="80171-118">For security reasons, BAM does not delete existing live data copies of the workbook.</span></span> <span data-ttu-id="80171-119">而是遞增即時資料複本的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="80171-119">Instead, BAM increments the file name of the live data copy.</span></span>  
  
### <a name="to-define-the-rta"></a><span data-ttu-id="80171-120">定義 RTA</span><span class="sxs-lookup"><span data-stu-id="80171-120">To define the RTA</span></span>  
  
1.  <span data-ttu-id="80171-121">在 BAM Excel 活頁簿中，建立檢視，並至少在樞紐分析表中新增一個維度和一個量值，選取 RTA 工具列按鈕，然後儲存此活頁簿。</span><span class="sxs-lookup"><span data-stu-id="80171-121">In the BAM Excel workbook, create a view, add at least one dimension and one measure to the PivotTable report, select the RTA toolbar button, and then save the workbook.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="80171-122">請勿定義多個使用相同 BAM 活動的 RTA。</span><span class="sxs-lookup"><span data-stu-id="80171-122">Do not define multiple RTAs that use the same BAM activity.</span></span> <span data-ttu-id="80171-123">若是這麼做，當您封存 BAM 資料時，RTA 資料將是錯誤的資料。</span><span class="sxs-lookup"><span data-stu-id="80171-123">If you do so, the RTA data will be incorrect when you archive the BAM data.</span></span>  
  
    -   <span data-ttu-id="80171-124">如需開啟 BAM 活頁簿的相關資訊，建立檢視，以及新增維度和量值，請參閱 < 定義商務活動檢視 > 和 < 定義彙總 」 中*資訊工作者使用者手冊 》*。</span><span class="sxs-lookup"><span data-stu-id="80171-124">For information about opening the BAM workbook, creating a view, and adding dimensions and measures, see "Defining a Business Activity View" and "Defining Aggregations" in the *Information Workers User Guide*.</span></span>  
  
2.  <span data-ttu-id="80171-125">部署活頁簿。</span><span class="sxs-lookup"><span data-stu-id="80171-125">Deploy the workbook.</span></span>  
  
    -   <span data-ttu-id="80171-126">若要部署活頁簿，請依照下列中的指示[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md)。</span><span class="sxs-lookup"><span data-stu-id="80171-126">To deploy the workbook, follow the instructions in [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
3.  <span data-ttu-id="80171-127">方案開發人員使用**DirectEventStream**匯入事件至 BAM 主要匯入資料庫的類別。</span><span class="sxs-lookup"><span data-stu-id="80171-127">A solutions developer uses the **DirectEventStream** class to import events into the BAM Primary Import database.</span></span>  

  
4.  <span data-ttu-id="80171-128">開啟此活頁簿最近的即時資料複本，以檢視 RTA。</span><span class="sxs-lookup"><span data-stu-id="80171-128">Open the most recent live data copy of the workbook to see the RTAs.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="80171-129">基於安全性理由，BAM 不會刪除活頁簿現有的即時資料複本，</span><span class="sxs-lookup"><span data-stu-id="80171-129">For security reasons, BAM does not delete existing live data copies of the workbook.</span></span> <span data-ttu-id="80171-130">而是遞增即時資料複本的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="80171-130">Instead, BAM increments the file name of the live data copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80171-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80171-131">See Also</span></span>  
 <span data-ttu-id="80171-132">[BAM DTS 封裝](../core/bam-dts-packages.md) </span><span class="sxs-lookup"><span data-stu-id="80171-132">[BAM DTS Packages](../core/bam-dts-packages.md) </span></span>  
 <span data-ttu-id="80171-133">[如何部署 BAM 定義](../core/how-to-deploy-bam-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="80171-133">[How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md) </span></span>  
 <span data-ttu-id="80171-134">[更新 OLAP 和 RTA 連接字串屬性](../core/updating-olap-and-rta-connection-string-properties.md) </span><span class="sxs-lookup"><span data-stu-id="80171-134">[Updating OLAP and RTA Connection String Properties](../core/updating-olap-and-rta-connection-string-properties.md) </span></span>  
 [<span data-ttu-id="80171-135">管理 BAM 動態基礎結構</span><span class="sxs-lookup"><span data-stu-id="80171-135">Managing the BAM Dynamic Infrastructure</span></span>](../core/managing-the-bam-dynamic-infrastructure.md)