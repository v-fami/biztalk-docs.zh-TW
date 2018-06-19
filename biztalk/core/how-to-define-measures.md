---
title: 如何定義量值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], creating measures
- aggregations [BAM], measures
- BAM views, measures
ms.assetid: fd3dfe6b-cc63-4306-8aad-a9d2a9af01e8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e56fea736baaec3f259fc8831a7256e28eaabc9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249142"
---
# <a name="how-to-define-measures"></a><span data-ttu-id="ae9c5-102">如何定義量值</span><span class="sxs-lookup"><span data-stu-id="ae9c5-102">How to Define Measures</span></span>
<span data-ttu-id="ae9c5-103">量值可以定義計算活動的方式。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-103">A measure defines how an activity is calculated.</span></span> <span data-ttu-id="ae9c5-104">建立 BAM 檢視時，您可以定義檢視中的活動量值。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-104">When you create a BAM view you can define a measure for the activity in the view.</span></span> <span data-ttu-id="ae9c5-105">例如，對於「訂單」活動，您可以計算訂單總金額、訂單件數、訂單平均金額等。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-105">For example, for a purchase order activity, you can calculate the total PO amount, the number of POs, the average PO amount, and so on.</span></span>  
  
 <span data-ttu-id="ae9c5-106">BAM 支援的量值包括：</span><span class="sxs-lookup"><span data-stu-id="ae9c5-106">BAM supported measures include:</span></span>  
  
-   <span data-ttu-id="ae9c5-107">Sum</span><span class="sxs-lookup"><span data-stu-id="ae9c5-107">Sum</span></span>  
  
-   <span data-ttu-id="ae9c5-108">Count</span><span class="sxs-lookup"><span data-stu-id="ae9c5-108">Count</span></span>  
  
-   <span data-ttu-id="ae9c5-109">平均值</span><span class="sxs-lookup"><span data-stu-id="ae9c5-109">Average</span></span>  
  
-   <span data-ttu-id="ae9c5-110">最小值</span><span class="sxs-lookup"><span data-stu-id="ae9c5-110">Minimum</span></span>  
  
-   <span data-ttu-id="ae9c5-111">最大值</span><span class="sxs-lookup"><span data-stu-id="ae9c5-111">Maximum</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae9c5-112">「BAM 即時彙總」(RTA) 功能目前不支援「最小值」和「最大值」量值。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-112">The BAM Real-time Aggregation (RTA) feature doesn't currently support Minimum and Maximum measures.</span></span> <span data-ttu-id="ae9c5-113">您可以使用這些量值，但是將 Excel 樞紐分析表標示為 RTA 時，「最小值」和「最大值」會被忽略。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-113">You can use those measures, but when you mark the Excel pivot table as an RTA, Minimum and Maximum are ignored.</span></span>  
  
### <a name="to-add-new-measures"></a><span data-ttu-id="ae9c5-114">新增量值</span><span class="sxs-lookup"><span data-stu-id="ae9c5-114">To add new measures</span></span>  
  
1.  <span data-ttu-id="ae9c5-115">在 BAM 檢視精靈中，按一下 **下一步**直到您看到**新 BAM 檢視： 彙總維度與量值**頁面。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-115">In the BAM View wizard, click **Next** until you see the **New BAM View: Aggregation Dimensions and Measures** page.</span></span> <span data-ttu-id="ae9c5-116">按一下**新的量值**。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-116">Click **New Measures**.</span></span>  
  
2.  <span data-ttu-id="ae9c5-117">輸入量值的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-117">Type a name for your measure.</span></span>  
  
3.  <span data-ttu-id="ae9c5-118">從下拉式清單選取**基底資料項**。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-118">From the drop-down list, select the **Base data item**.</span></span>  
  
4.  <span data-ttu-id="ae9c5-119">按一下**彙總類型**您想要使用。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-119">Click the **Aggregation type** you want to use.</span></span> <span data-ttu-id="ae9c5-120">選項包括：</span><span class="sxs-lookup"><span data-stu-id="ae9c5-120">The choices include:</span></span>  
  
    -   <span data-ttu-id="ae9c5-121">Sum</span><span class="sxs-lookup"><span data-stu-id="ae9c5-121">Sum</span></span>  
  
    -   <span data-ttu-id="ae9c5-122">Count</span><span class="sxs-lookup"><span data-stu-id="ae9c5-122">Count</span></span>  
  
    -   <span data-ttu-id="ae9c5-123">平均值</span><span class="sxs-lookup"><span data-stu-id="ae9c5-123">Average</span></span>  
  
    -   <span data-ttu-id="ae9c5-124">最小值 （Rta 不支援）。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-124">Minimum (not supported for RTAs).</span></span>  
  
    -   <span data-ttu-id="ae9c5-125">最大值 (RTA 不支援)</span><span class="sxs-lookup"><span data-stu-id="ae9c5-125">Maximum (not supported for RTAs)</span></span>  
  
5.  <span data-ttu-id="ae9c5-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-126">Click **OK**.</span></span> <span data-ttu-id="ae9c5-127">當您完成新增維度和量值時，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-127">When you finish adding dimensions and measures, click **Next**.</span></span>  
  
6.  <span data-ttu-id="ae9c5-128">在**新 BAM 檢視： 摘要**頁面上，檢閱您的新檢視的相關資訊，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-128">On the **New BAM View: Summary** page, review the information regarding your new view, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="ae9c5-129">按一下**完成**完成**BAM 檢視精靈**。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-129">Click **Finish** to complete the **BAM View Wizard**.</span></span>  
  
 <span data-ttu-id="ae9c5-130">如果您已將量值和維度新增至 BAM 檢視，就可以將這些項目新增到 Excel 活頁簿中的樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-130">If you added measures and dimensions to your BAM view, you can add those items to the PivotTable in the Excel workbook.</span></span> <span data-ttu-id="ae9c5-131">如需有關建立樞紐分析表的詳細資訊，請參閱[如何使用樞紐分析表](../core/how-to-use-the-pivottable.md)。</span><span class="sxs-lookup"><span data-stu-id="ae9c5-131">For more information about creating a PivotTable, see [How to Use the PivotTable](../core/how-to-use-the-pivottable.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae9c5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae9c5-132">See Also</span></span>  
 [<span data-ttu-id="ae9c5-133">定義維度</span><span class="sxs-lookup"><span data-stu-id="ae9c5-133">Defining Dimensions</span></span>](../core/defining-dimensions.md)