---
title: "查詢排程彙總資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, scheduled data
- queries [BAM], scheduled data
ms.assetid: fb785ec0-7862-4d83-bb6f-0ebd69a28ce6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1aed1d63b1ebd1e54fd229236a94f3ac9a5f6837
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="querying-scheduled-aggregated-data"></a><span data-ttu-id="9aa68-102">查詢排程的彙總資料</span><span class="sxs-lookup"><span data-stu-id="9aa68-102">Querying Scheduled Aggregated Data</span></span>
<span data-ttu-id="9aa68-103">透過 BAM 分析資料庫中動態建立的 OLAP Cube 可以查詢排程的彙總資料。</span><span class="sxs-lookup"><span data-stu-id="9aa68-103">Scheduled aggregation data is available to queries through dynamically created OLAP cubes in the  BAM Analysis database.</span></span>  
  
 <span data-ttu-id="9aa68-104">這個 Cube 的名稱與 BAM 定義 XML 中 View 項目的 Name 屬性相同 (與 Excel 精靈中輸入的檢視名稱相同)。</span><span class="sxs-lookup"><span data-stu-id="9aa68-104">The name of this cube is the same as the Name attribute of the View element in the BAM definition XML, which is the same as the view name entered in the Excel wizards.</span></span> <span data-ttu-id="9aa68-105">當您執行 Data Transformation Services (DTS) 封裝 BAM_AN_< BAM 重新整理此 cube\<*ViewName*\>，其中\< *ViewName* \>為檢視的名稱，描述您在 Excel 精靈中使用。</span><span class="sxs-lookup"><span data-stu-id="9aa68-105">BAM refreshes this cube when you run the Data Transformation Services (DTS) package BAM_AN_\<*ViewName*\>, where the \<*ViewName*\> is the name of the view described you used in the Excel wizards.</span></span>  
  
 <span data-ttu-id="9aa68-106">在查詢排程的彙總資料時，請特別注意下列條件：</span><span class="sxs-lookup"><span data-stu-id="9aa68-106">It is important to note the following conditions when querying scheduled aggregated data:</span></span>  
  
-   <span data-ttu-id="9aa68-107">這是虛擬 Cube，其中包含在 DTS 封裝開始執行的確切時間擷取到的商務快照。</span><span class="sxs-lookup"><span data-stu-id="9aa68-107">This is a virtual cube containing a snapshot of the business at the exact moment that the DTS package execution started.</span></span> <span data-ttu-id="9aa68-108">它同時包含完成的活動以及仍在進行中的活動的彙總。</span><span class="sxs-lookup"><span data-stu-id="9aa68-108">It contains aggregations both for the completed activities and for the ones still in progress.</span></span> <span data-ttu-id="9aa68-109">您可以使用進度維度篩選彙總或將彙總分組。</span><span class="sxs-lookup"><span data-stu-id="9aa68-109">You can use the progress dimension to filter or group the aggregations accordingly.</span></span>  
  
-   <span data-ttu-id="9aa68-110">如果您不感興趣目前的活動 （例如，如果它們的完成速度非常快），您就可以查詢對應的真實 cube \< *ViewName*\>#Completed。</span><span class="sxs-lookup"><span data-stu-id="9aa68-110">If you are never interested in the current activities (for example, if they complete very fast) you can query the corresponding real cube \<*ViewName*\>#Completed.</span></span>  
  
-   <span data-ttu-id="9aa68-111">如果您也有即時彙總，請排程 DTS 封裝，讓重新整理 Cube 的頻率，比為即時彙總設定的線上視窗更頻繁。</span><span class="sxs-lookup"><span data-stu-id="9aa68-111">If you also have real-time aggregations, schedule the DTS package for refreshing the cube more frequently than the online window you set for the real-time aggregations.</span></span> <span data-ttu-id="9aa68-112">否則，將會出現一個時間窗口，而您在此時間窗口內沒有任何彙總。</span><span class="sxs-lookup"><span data-stu-id="9aa68-112">Otherwise, there will be a window of time for which you do not have aggregations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa68-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="9aa68-113">See Also</span></span>  
 [<span data-ttu-id="9aa68-114">查詢 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="9aa68-114">Querying BAM Data</span></span>](../core/querying-bam-data.md)