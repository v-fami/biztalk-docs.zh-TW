---
title: "測量最大持續性引擎輸送量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum sustainable throughput (MST)
- maximum sustainable throughput (MST), about maximum sustainable throughput (MST)
- performance, maximum sustainable thoughput (MST)
ms.assetid: d83f734f-1a44-4da0-a755-45ba204cadaf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5507aca58669ed5c81034ba91e16d1183e07188
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="measuring-maximum-sustainable-engine-throughput"></a><span data-ttu-id="2a854-102">測量最大的可負載引擎輸送量</span><span class="sxs-lookup"><span data-stu-id="2a854-102">Measuring Maximum Sustainable Engine Throughput</span></span>
<span data-ttu-id="2a854-103">在規劃 BizTalk Server 系統時，其中一個主要的考量應該是決定系統最大的可負載輸送量 (MST)。</span><span class="sxs-lookup"><span data-stu-id="2a854-103">One of the primary considerations when planning a BizTalk Server system should be to determine the maximum sustainable throughput (MST) of the system.</span></span> <span data-ttu-id="2a854-104">BizTalk Server 系統的 MST 可做為 BizTalk 系統在生產環境中可無限處理的訊息流量之最高負載。</span><span class="sxs-lookup"><span data-stu-id="2a854-104">The MST of a BizTalk Server system is measured as the highest load of message traffic that the BizTalk system can handle indefinitely in production.</span></span> <span data-ttu-id="2a854-105">這一點很重要，因為當負載超過 MST 時，會將訊息積存在 MessageBox 資料庫中且訊息傳遞可能會延遲。</span><span class="sxs-lookup"><span data-stu-id="2a854-105">This is important because as load exceeds MST, messages are backlogged in the MessageBox database and message delivery may be delayed.</span></span> <span data-ttu-id="2a854-106">若您將 BizTalk Server 系統的 MST 計算為一般測試的一部分，則您可以擴充系統以避免在生產環境中擴充超載的實例。</span><span class="sxs-lookup"><span data-stu-id="2a854-106">If you calculate the MST of your BizTalk Server system as part of normal testing then you can scale your system to avoid extended overload scenarios in production.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a854-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="2a854-107">In This Section</span></span>  
  
-   [<span data-ttu-id="2a854-108">影響最大持續性效能的因素</span><span class="sxs-lookup"><span data-stu-id="2a854-108">Factors that Affect Maximum Sustainable Performance</span></span>](../core/factors-that-affect-maximum-sustainable-performance.md)  
  
-   [<span data-ttu-id="2a854-109">測量引擎 MST 的測試案例</span><span class="sxs-lookup"><span data-stu-id="2a854-109">Test Scenarios for Measuring MST of the Engine</span></span>](../core/test-scenarios-for-measuring-mst-of-the-engine.md)  
  
-   [<span data-ttu-id="2a854-110">測試引擎效能時的建議</span><span class="sxs-lookup"><span data-stu-id="2a854-110">Recommendations When Testing Engine Performance</span></span>](../core/recommendations-when-testing-engine-performance.md)