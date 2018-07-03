---
title: 範例凍結計算 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4da41d0d-10ee-4f64-97d1-3cfa9da153f7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77701083272da9e09c21cb05daf3c4e9764b604c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993039"
---
# <a name="sample-dehydration-calculation"></a><span data-ttu-id="9d1ca-102">範例凍結計算</span><span class="sxs-lookup"><span data-stu-id="9d1ca-102">Sample Dehydration Calculation</span></span>
<span data-ttu-id="9d1ca-103">以下是範例計算的範例，使用私用位元組來決定 BizTalk 是否會凍結。</span><span class="sxs-lookup"><span data-stu-id="9d1ca-103">Here is an example of a sample calculation, using private bytes, to determine if BizTalk will dehydrate or not.</span></span> <span data-ttu-id="9d1ca-104">該範例使用預設的設定值，以及一些範例執行階段值。</span><span class="sxs-lookup"><span data-stu-id="9d1ca-104">It uses the default configured values, and some example run-time values.</span></span>  
  
 <span data-ttu-id="9d1ca-105">假設凍結屬性具有下列的值：</span><span class="sxs-lookup"><span data-stu-id="9d1ca-105">Assume the following values for the dehydration properties:</span></span>  
  
- <span data-ttu-id="9d1ca-106">**TimeBlocked** = 60 （範例封鎖時間以秒為單位）</span><span class="sxs-lookup"><span data-stu-id="9d1ca-106">**TimeBlocked** = 60 (example time blocked in seconds)</span></span>  
  
- <span data-ttu-id="9d1ca-107">**WaitingHistory** = 90 （範例等候記錄以秒為單位）</span><span class="sxs-lookup"><span data-stu-id="9d1ca-107">**WaitingHistory** = 90 (example waiting history in seconds)</span></span>  
  
- <span data-ttu-id="9d1ca-108">**ActualPrivateBytes** = 250 （私用位元組的範例值）</span><span class="sxs-lookup"><span data-stu-id="9d1ca-108">**ActualPrivateBytes** = 250 (example value for private bytes)</span></span>  
  
- <span data-ttu-id="9d1ca-109">**OptimalUsage** = 50 （預設組態值）</span><span class="sxs-lookup"><span data-stu-id="9d1ca-109">**OptimalUsage** = 50 (default configuration value)</span></span>  
  
- <span data-ttu-id="9d1ca-110">**MaximalUsage** = 350 （預設組態值）</span><span class="sxs-lookup"><span data-stu-id="9d1ca-110">**MaximalUsage** = 350 (default configuration value)</span></span>  
  
  <span data-ttu-id="9d1ca-111">由於**ActualPrivateBytes**介於**OptimalUsage**並**MaximalUsage**，計算 alpha:</span><span class="sxs-lookup"><span data-stu-id="9d1ca-111">Since the **ActualPrivateBytes** are between **OptimalUsage** and **MaximalUsage**, alpha is calculated as:</span></span>  
  
```  
alpha(private) = (350 – 250) / 350 – 50)  
alpha(private) = 100 / 300  
alpha(private) = 0.33  
```  
  
 <span data-ttu-id="9d1ca-112">然後您計算**TestThreshold** ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9d1ca-112">Then you calculate the **TestThreshold** as follows:</span></span>  
  
```  
TestThreshold = 1 + (0.33 * (1800 – 1))  
TestThreshold = 1 + 599.66  
TestThreshold = 600.66  
```  
  
 <span data-ttu-id="9d1ca-113">最後，再決定是否要凍結：</span><span class="sxs-lookup"><span data-stu-id="9d1ca-113">And finally, make the decision to dehydrate or not:</span></span>  
  
```  
Dehydrate = (90 == -1 OR 90 > 600 OR 60 > (2 * 600))  
Dehydrate = false  
```  
  
 <span data-ttu-id="9d1ca-114">使用這個範例，您可以決定此時將不會凍結協調流程。</span><span class="sxs-lookup"><span data-stu-id="9d1ca-114">Using this example, you can determine that the orchestration will not be dehydrated at this time.</span></span>