---
title: "定義維度 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], dimensions
- BAM, dimensions
- BAM views, dimensions
- Excel add-in [BAM], creating dimensions
- dimensions [BAM]
ms.assetid: c00e0c45-eef2-42d9-832c-4be08d79203f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 916e8f29d7f1e48a7bab5f9ad78e65cb78e51802
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="defining-dimensions"></a><span data-ttu-id="e0a7b-102">定義維度</span><span class="sxs-lookup"><span data-stu-id="e0a7b-102">Defining Dimensions</span></span>
<span data-ttu-id="e0a7b-103">Microsoft Excel 將維度定義成類別，可用來將表格資料組織到用於分析的層級中。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-103">Microsoft Excel defines dimensions as categories used to organize data in a table into levels that will be used for analysis.</span></span> <span data-ttu-id="e0a7b-104">例如，位置資料維度可能包含城市、州/省和國家/地區等層級。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-104">For example, a location data dimension might contain levels such as city, state/province, and country/region.</span></span> <span data-ttu-id="e0a7b-105">在「BAM 檢視精靈」中建立 BAM 檢視時，您可以新增一或多個下列維度類型：</span><span class="sxs-lookup"><span data-stu-id="e0a7b-105">When creating BAM Views in the BAM View wizard, you can add one or more of the following dimension types:</span></span>  
  
-   [<span data-ttu-id="e0a7b-106">進度維度</span><span class="sxs-lookup"><span data-stu-id="e0a7b-106">Progress Dimension</span></span>](../core/progress-dimension.md)  
  
-   [<span data-ttu-id="e0a7b-107">資料維度</span><span class="sxs-lookup"><span data-stu-id="e0a7b-107">Data Dimension</span></span>](../core/data-dimension.md)  
  
-   [<span data-ttu-id="e0a7b-108">時間維度</span><span class="sxs-lookup"><span data-stu-id="e0a7b-108">Time Dimension</span></span>](../core/time-dimension.md)  
  
-   [<span data-ttu-id="e0a7b-109">數字範圍維度</span><span class="sxs-lookup"><span data-stu-id="e0a7b-109">Numeric Range Dimension</span></span>](../core/numeric-range-dimension.md)  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
<span data-ttu-id="e0a7b-110">預先計算的彙總資料</span><span class="sxs-lookup"><span data-stu-id="e0a7b-110">Pre-calculated Aggregation Data</span></span>  
  
 <span data-ttu-id="e0a7b-111">您可以在「BAM 檢視精靈」中新增維度。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-111">You add new dimensions in the BAM View wizard.</span></span> <span data-ttu-id="e0a7b-112">但是在新增維度之前，您必須先使用此精靈來建立商務活動檢視。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-112">Before you can add dimensions, you need to use the wizard to create business activity views.</span></span> <span data-ttu-id="e0a7b-113">如需有關如何使用精靈的詳細資訊，請參閱[定義商務活動和在 Excel 中的檢視](../core/defining-business-activities-and-views-in-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-113">For more information about using the wizard, see [Define Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md).</span></span>  
  
### <a name="to-add-new-dimensions"></a><span data-ttu-id="e0a7b-114">新增維度</span><span class="sxs-lookup"><span data-stu-id="e0a7b-114">To add new dimensions</span></span>  
  
1.  <span data-ttu-id="e0a7b-115">在 BAM 檢視精靈中，按一下 **下一步**直到您看到**新 BAM 檢視： 彙總維度與量值**頁面。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-115">In the BAM View wizard, click **Next** until you see the **New BAM View: Aggregation Dimensions and Measures** page.</span></span> <span data-ttu-id="e0a7b-116">按一下**新維度**。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-116">Click **New Dimensions**.</span></span>  
  
2.  <span data-ttu-id="e0a7b-117">輸入維度的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-117">Type a name for the dimension.</span></span>  
  
3.  <span data-ttu-id="e0a7b-118">從下拉式清單中選取維度類型。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-118">From the drop-down list, select a dimension type.</span></span>  
  
4.  <span data-ttu-id="e0a7b-119">根據您所選取維度類型，填入適當的資料，並再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="e0a7b-119">Based on the dimension type you selected, fill in the appropriate data, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a7b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0a7b-120">See Also</span></span>  
 [<span data-ttu-id="e0a7b-121">進度維度</span><span class="sxs-lookup"><span data-stu-id="e0a7b-121">Progress Dimension</span></span>](../core/progress-dimension.md)