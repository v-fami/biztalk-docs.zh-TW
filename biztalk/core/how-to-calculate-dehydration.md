---
title: "如何計算凍結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88f2d09c-60db-4daf-b850-23f2c8915502
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a327695099ec575f2a13ccb75b4152e4a7de1af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-calculate-dehydration"></a><span data-ttu-id="cdbcf-102">如何計算凍結</span><span class="sxs-lookup"><span data-stu-id="cdbcf-102">How to Calculate Dehydration</span></span>
<span data-ttu-id="cdbcf-103">若要計算凍結，您可使用設定的屬性及某些執行階段的值。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-103">To calculate dehydration, you use the configured properties and certain run-time values.</span></span> <span data-ttu-id="cdbcf-104">下列範例會示範如何計算假設性的凍結案例。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-104">The following example demonstrates how to calculate a hypothetical dehydration scenario.</span></span>  
  
### <a name="to-calculate-dehydration"></a><span data-ttu-id="cdbcf-105">計算凍結</span><span class="sxs-lookup"><span data-stu-id="cdbcf-105">To calculate dehydration</span></span>  
  
1.  <span data-ttu-id="cdbcf-106">讓 Alpha 代表 0 和 1 之間測量記憶體壓力的因數。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-106">Let alpha represent a factor between 0 and 1 that measures memory stress.</span></span>  <span data-ttu-id="cdbcf-107">在實務中，Alpha 對於 3 個記憶體節流準則 (凍結屬性) 的每一個都有一個元件；在此範例中，我們用 alpha(virtual)、alpha(private) 和 alpha(physical) 來代表它們。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-107">In practice, alpha has a component for each of the three memory throttling criteria (dehydration properties); in this example we denote them as alpha(virtual), alpha(private) and alpha(physical).</span></span> <span data-ttu-id="cdbcf-108">定義以下項目：</span><span class="sxs-lookup"><span data-stu-id="cdbcf-108">Define the following:</span></span>  
  
    ```  
    IF ActualPrivateBytes < OptimalUsage  
       alpha(private) = 1  
    ELSE IF ActualPrivateBytes > MaximalUsage  
       alpha(private) = 0  
    ELSE  
       alpha(private) = (MaximalUsage - ActualPrivateBytes) / (MaximalUsage - OptimalUsage)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="cdbcf-109">OptimalUsage 和 MaximalUsage 針對每一個凍結屬性皆有預設值。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-109">OptimalUsage and MaximalUsage have default values for each dehydration property.</span></span> <span data-ttu-id="cdbcf-110">您可以在 BTSNTSvc.exe.config 檔案中變更這些值 。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-110">These values can be changed in the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="cdbcf-111">如需詳細資訊，請參閱[凍結預設屬性](../core/dehydration-default-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-111">For more information, see [Dehydration Default Properties](../core/dehydration-default-properties.md).</span></span>  
  
2.  <span data-ttu-id="cdbcf-112">以類似方式定義其他 Alpha 元件。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-112">Define the other alpha components analogously.</span></span> <span data-ttu-id="cdbcf-113">定義以下項目：</span><span class="sxs-lookup"><span data-stu-id="cdbcf-113">Define the following:</span></span>  
  
    ```  
    alpha = Minimum { alpha(virtual), alpha(private), alpha(physical) }  
    where alpha(…) = 1 whenever IsActive=false for that given memory unit  
    ```  
  
3.  <span data-ttu-id="cdbcf-114">然後定義 TestThreshold (TestThreshold 、 MinThreshold 和 MaxThreshold 的定義單位為秒數)：</span><span class="sxs-lookup"><span data-stu-id="cdbcf-114">Then define TestThreshold (TestThreshold, MinThreshold, and MaxThreshold are defined in seconds):</span></span>  
  
    ```  
    TestThreshold = MinThreshold + (alpha * (MaxThreshold – MinThreshold))  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="cdbcf-115">MinThreshold 預設值 = 1。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-115">MinThreshold default value = 1.</span></span> <span data-ttu-id="cdbcf-116">MaxThreshold 預設值 = 1800年。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-116">MaxThreshold default value = 1800.</span></span> <span data-ttu-id="cdbcf-117">您可以在 BTSNTSvc.exe.config 檔案中變更這些值 。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-117">These values can be changed in the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="cdbcf-118">如需詳細資訊，請參閱[凍結預設屬性](../core/dehydration-default-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-118">For more information, see [Dehydration Default Properties](../core/dehydration-default-properties.md).</span></span>  
  
4.  <span data-ttu-id="cdbcf-119">然後定義 TimeBlocked 和 EstimatedTime：</span><span class="sxs-lookup"><span data-stu-id="cdbcf-119">Then define TimeBlocked and EstimatedTime:</span></span>  
  
    -   <span data-ttu-id="cdbcf-120">TimeBlocked = 我們實際等待此訂閱獲得滿足的時間</span><span class="sxs-lookup"><span data-stu-id="cdbcf-120">TimeBlocked = actual time we have been waiting for this subscription to be satisfied</span></span>  
  
    -   <span data-ttu-id="cdbcf-121">EstimatedTime = 預估此協調流程將維持閒置的時間 (例如：剩餘要接聽的逾時)</span><span class="sxs-lookup"><span data-stu-id="cdbcf-121">EstimatedTime = estimated time that this orchestration will remain idle (e.g. remaining timeout on the listen)</span></span>  
  
 <span data-ttu-id="cdbcf-122">是否要凍結的決定是下列布林值條件的結果 (true = 凍結)：</span><span class="sxs-lookup"><span data-stu-id="cdbcf-122">The decision whether to dehydrate is the result of the following Boolean condition (true = dehydrate):</span></span>  
  
-   <span data-ttu-id="cdbcf-123">凍結 = (EstimatedTime > TestThreshold OR TimeBlocked > (2* TestThreshold))</span><span class="sxs-lookup"><span data-stu-id="cdbcf-123">Dehydrate = (EstimatedTime > TestThreshold OR TimeBlocked > (2* TestThreshold))</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdbcf-124">預估時間就是在延遲結束前的剩餘時間 (如果延遲 5 分鐘並且已經過了 2 分鐘，則 TimeBlocked=120 秒、EstimatedTime=180 秒)。</span><span class="sxs-lookup"><span data-stu-id="cdbcf-124">Estimated time is the time remaining until the delay is ended (if delayed for 5 minutes and 2 minutes has passed, TimeBlocked=120 seconds, EstimatedTime=180 seconds).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbcf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdbcf-125">See Also</span></span>  
 <span data-ttu-id="cdbcf-126">[凍結預設屬性](../core/dehydration-default-properties.md) </span><span class="sxs-lookup"><span data-stu-id="cdbcf-126">[Dehydration Default Properties](../core/dehydration-default-properties.md) </span></span>  
 [<span data-ttu-id="cdbcf-127">BTSNTSvc.exe.config 檔案</span><span class="sxs-lookup"><span data-stu-id="cdbcf-127">BTSNTSvc.exe.config File</span></span>](../core/btsntsvc-exe-config-file.md)