---
title: 條件式迴圈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Looping functoids, conditional
- Equal functoids
- maps, conditional looping
ms.assetid: eb16efb8-b12c-47d6-afc9-579fc85ea59c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5452f6b8768442b95ac6bddde0e84ba07f68c85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231974"
---
# <a name="conditional-looping"></a><span data-ttu-id="e58fe-102">條件式迴圈</span><span class="sxs-lookup"><span data-stu-id="e58fe-102">Conditional Looping</span></span>
<span data-ttu-id="e58fe-103">您可以將條件加入至**迴圈**運算質所連結的輸出**迴圈**運算質和**邏輯**運算質到相同目的記錄。</span><span class="sxs-lookup"><span data-stu-id="e58fe-103">You can add conditions to a **Looping** functoid by linking the output of a **Looping** functoid and a **Logical** functoid to the same destination record.</span></span> <span data-ttu-id="e58fe-104">只有在邏輯條件相符時，才會建立目的記錄。</span><span class="sxs-lookup"><span data-stu-id="e58fe-104">The destination records are created only when the logical condition is met.</span></span>  
  
## <a name="conditional-looping-map"></a><span data-ttu-id="e58fe-105">條件式迴圈對應</span><span class="sxs-lookup"><span data-stu-id="e58fe-105">Conditional Looping Map</span></span>  
 <span data-ttu-id="e58fe-106">![說明條件式迴圈運算質的對應。] (../core/media/loopingconditionalfunctoid.gif "loopingconditionalfunctoid")</span><span class="sxs-lookup"><span data-stu-id="e58fe-106">![Map illustrating conditional looping functoid.](../core/media/loopingconditionalfunctoid.gif "loopingconditionalfunctoid")</span></span>  
  
 <span data-ttu-id="e58fe-107">在上圖中，第一個**等於**運算質會**名稱**欄位底下 **[foodsurvey]** 至"Wendy wheeler"做比較。</span><span class="sxs-lookup"><span data-stu-id="e58fe-107">In the preceding figure, the first **Equal** functoid compares the **Name** field under **FoodSurvey** to "Wendy Wheeler".</span></span> <span data-ttu-id="e58fe-108">第二個**等於**運算質會**名稱**欄位底下 **[flowersurvey]** 至"Kelly focht"做比較。</span><span class="sxs-lookup"><span data-stu-id="e58fe-108">The second **Equal** functoid compares the **Name** field under **FlowerSurvey** to "Kelly Focht".</span></span> <span data-ttu-id="e58fe-109">因此，對應會建立目的地**位址**記錄只會針對兩個名稱。</span><span class="sxs-lookup"><span data-stu-id="e58fe-109">Thus, the map creates the destination **Address** records only for the two names.</span></span> <span data-ttu-id="e58fe-110">使用中的範例資料**迴圈**運算質範例中，輸出執行個體訊息會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="e58fe-110">Using the sample data from the **Looping** functoid example, the output instance message would appear as follows.</span></span>  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://ConditionalLoop.MasterAddresses">  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290">  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406">  
</ns0:MasterAddresses>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e58fe-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e58fe-111">See Also</span></span>  
 <span data-ttu-id="e58fe-112">[如何新增迴圈運算質至對應](../core/how-to-add-looping-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="e58fe-112">[How to Add Looping Functoids to a Map](../core/how-to-add-looping-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="e58fe-113">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="e58fe-113">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="e58fe-114">[索引運算質](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="e58fe-114">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="e58fe-115">[反覆項目運算質](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="e58fe-115">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="e58fe-116">[迴圈運算質](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="e58fe-116">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="e58fe-117">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="e58fe-117">Record Count Functoid</span></span>](../core/record-count-functoid.md)