---
title: "處理階段數目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- processing, stages
- process management solution tutorial, processing stages
ms.assetid: 74bd9f8c-99b4-4931-a096-6c54221ab2e5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f61c5c348e54ea096c921cb6fc63f0db339dbf4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-processing-stages"></a><span data-ttu-id="c66dc-102">處理階段數目</span><span class="sxs-lookup"><span data-stu-id="c66dc-102">Number of Processing Stages</span></span>
<span data-ttu-id="c66dc-103">解決方案將訂單程序分隔成階段，如此即可不中斷長時間執行的訂單而修改程序 (透過取代階段)。</span><span class="sxs-lookup"><span data-stu-id="c66dc-103">The solution separates the order process into stages, so that it is possible to modify the process (by replacing stages) without disrupting long-running orders.</span></span> <span data-ttu-id="c66dc-104">如需如何處理程序分成兩階段的詳細資訊，請參閱 < 分割商務程序 」 中的[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="c66dc-104">For more information about how the process was divided into stages, see "Dividing Business Processes" in [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).</span></span>  
  
 <span data-ttu-id="c66dc-105">目前版本的解決方案僅包含兩個處理階段。</span><span class="sxs-lookup"><span data-stu-id="c66dc-105">The current version of the solution contains only two processing stages.</span></span> <span data-ttu-id="c66dc-106">不過，它可以包含更多階段。</span><span class="sxs-lookup"><span data-stu-id="c66dc-106">It could, however, contain many more.</span></span> <span data-ttu-id="c66dc-107">更多的階段會提供更多的點，您可以在版本處理序，並繼續處理階段的最新版本上工作。</span><span class="sxs-lookup"><span data-stu-id="c66dc-107">More stages provide more points where you can version the process and continue working on the latest version of a processing stage.</span></span> <span data-ttu-id="c66dc-108">但是，各個階段會導致通過 MessageBox 資料庫之額外協調訊息的負擔，而增加處理時間。</span><span class="sxs-lookup"><span data-stu-id="c66dc-108">However, each stage introduces the overhead of additional coordinating messages going through the MessageBox database, which increases processing time.</span></span> <span data-ttu-id="c66dc-109">您必須監控解決方案的效能，以判斷多個階段的數目是否過多。</span><span class="sxs-lookup"><span data-stu-id="c66dc-109">You must monitor the solution's performance to determine if the number of multiple stages is excessive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66dc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c66dc-110">See Also</span></span>  
 <span data-ttu-id="c66dc-111">[商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="c66dc-111">[Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="c66dc-112">程序管理員邏輯</span><span class="sxs-lookup"><span data-stu-id="c66dc-112">Process Manager Logic</span></span>](../core/process-manager-logic.md)