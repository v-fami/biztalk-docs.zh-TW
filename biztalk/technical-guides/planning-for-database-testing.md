---
title: 規劃資料庫測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a4cf5e1f-a960-4702-a050-a2cdacddcbca
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bce48244f67fd757fae5c2657634274625677850
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996615"
---
# <a name="planning-for-database-testing"></a><span data-ttu-id="327e1-102">規劃資料庫測試</span><span class="sxs-lookup"><span data-stu-id="327e1-102">Planning for Database Testing</span></span>
<span data-ttu-id="327e1-103">完整的壓力負載測試 BizTalk 解決方案 ultimate 的成功或失敗的方案中以突顯的方式判斷。</span><span class="sxs-lookup"><span data-stu-id="327e1-103">Thorough stress/load testing of a BizTalk solution figures prominently in the ultimate success or failure of the solution.</span></span> <span data-ttu-id="327e1-104">由於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能非常依賴的效能[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫、 測試和最佳化的 BizTalk 解決方案常見問題的焦點在於測試和最佳化執行的電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]除此之外[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="327e1-104">Since [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance is so dependent on the performance of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, testing and optimization of a BizTalk solution frequently focuses on testing and optimization of the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
## <a name="considerations-when-planning-for-database-testing"></a><span data-ttu-id="327e1-105">規劃資料庫測試時的考量</span><span class="sxs-lookup"><span data-stu-id="327e1-105">Considerations When Planning for Database Testing</span></span>  
 <span data-ttu-id="327e1-106">規劃資料庫測試時，請考慮下列：</span><span class="sxs-lookup"><span data-stu-id="327e1-106">Consider the following when planning for database testing:</span></span>  
  
1. <span data-ttu-id="327e1-107">**請確定測試環境盡可能符合生產環境。**</span><span class="sxs-lookup"><span data-stu-id="327e1-107">**Ensure that the test environment matches the production environment as closely as possible.**</span></span> <span data-ttu-id="327e1-108">使用虛擬環境，例如 Microsoft HYPER-V Server 2008 進行單元測試是完全可以接受;不過，所有的載入/壓力測試應執行針對儘可能密集地符合最後一個生產環境的硬體。</span><span class="sxs-lookup"><span data-stu-id="327e1-108">Using a virtual environment such as Microsoft Hyper-V Server 2008 for unit testing is perfectly acceptable; however, all load/stress testing should be performed against hardware that matches the final production environment as closely as possible.</span></span>  
  
2. <span data-ttu-id="327e1-109">**計劃測量最大持續輸送量和 BizTalk Server 系統的最大持續性追蹤輸送量**。</span><span class="sxs-lookup"><span data-stu-id="327e1-109">**Plan to measure maximum sustainable throughput and maximum sustainable tracking throughput of the BizTalk Server system**.</span></span> <span data-ttu-id="327e1-110">最大持續輸送量會以 BizTalk Server 系統在生產環境中可無限處理的訊息流量最高的負載。</span><span class="sxs-lookup"><span data-stu-id="327e1-110">Maximum sustainable throughput is measured as the highest load of message traffic that the BizTalk Server system can handle indefinitely in production.</span></span> <span data-ttu-id="327e1-111">請依照下列 BizTalk Server 說明中的下列主題中的步驟：</span><span class="sxs-lookup"><span data-stu-id="327e1-111">Follow the steps in the following topics in BizTalk Server Help:</span></span>  
  
   - <span data-ttu-id="327e1-112">[測量最大持續性引擎輸送量](http://go.microsoft.com/fwlink/?LinkID=154388)(http://go.microsoft.com/fwlink/?LinkID=154388)。</span><span class="sxs-lookup"><span data-stu-id="327e1-112">[Measuring Maximum Sustainable Engine Throughput](http://go.microsoft.com/fwlink/?LinkID=154388) (http://go.microsoft.com/fwlink/?LinkID=154388).</span></span>  
  
   - <span data-ttu-id="327e1-113">[測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID=153815)。</span><span class="sxs-lookup"><span data-stu-id="327e1-113">[Measuring Maximum Sustainable Tracking Throughput](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815).</span></span>  
  
     <span data-ttu-id="327e1-114">這些主題說明的方法來產生負載與針對系統、 要測量的參數和測試 MST 時要遵循的一般建議。</span><span class="sxs-lookup"><span data-stu-id="327e1-114">These topics describe the methodology for generating load against the system, the parameters that should be measured, and general recommendations to follow when testing MST.</span></span>  
  
3. <span data-ttu-id="327e1-115">**了解如何影響 BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="327e1-115">**Understand the implications of how BizTalk Server**</span></span>  
    <span data-ttu-id="327e1-116">**實作主控件節流。**</span><span class="sxs-lookup"><span data-stu-id="327e1-116">**implements host throttling.**</span></span> <span data-ttu-id="327e1-117">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件節流演算法會嘗試中度的工作負載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件執行個體，以確保工作負載不超過主控件執行個體的容量，或任何下游主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="327e1-117">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host throttling algorithm attempts to moderate the workload of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host instances to ensure that the workload does not exceed the capacity of the host instance or any downstream host instances.</span></span> <span data-ttu-id="327e1-118">節流機制會自行調整而且預設的設定選項適用於大部分的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理案例。</span><span class="sxs-lookup"><span data-stu-id="327e1-118">The throttling mechanism is self tuning and the default configuration options are suitable for the majority of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processing scenarios.</span></span> <span data-ttu-id="327e1-119">您應，不過，有的節流機制實作負載/壓力測試之前先深入了解。</span><span class="sxs-lookup"><span data-stu-id="327e1-119">You should, however, have a good understanding of the throttling mechanism before implementing load/stress testing.</span></span> <span data-ttu-id="327e1-120">如需詳細資訊，請參閱 <<c0> [ 最佳化資源使用狀況透過主控件節流](http://go.microsoft.com/fwlink/?LinkId=155770)(<http://go.microsoft.com/fwlink/?LinkId=155770>) 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="327e1-120">For more information, see [Optimizing Resource Usage Through Host Throttling](http://go.microsoft.com/fwlink/?LinkId=155770) (<http://go.microsoft.com/fwlink/?LinkId=155770>) in BizTalk Server Help.</span></span>