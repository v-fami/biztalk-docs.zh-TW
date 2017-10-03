---
title: "執行負載和輸送量測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ff86ebd-a77f-4e29-bfea-0306e88bbf67
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3da46b2dc3208208305e60e9efbfadd0c60d7d32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="performing-load-and-throughput-testing"></a><span data-ttu-id="e0553-102">執行負載和輸送量測試</span><span class="sxs-lookup"><span data-stu-id="e0553-102">Performing Load and Throughput Testing</span></span>
<span data-ttu-id="e0553-103">您應該提供一個環境符合您的生產環境的效能和壓力測試。</span><span class="sxs-lookup"><span data-stu-id="e0553-103">You should make available an environment that matches your production environment for performance and stress testing.</span></span> <span data-ttu-id="e0553-104">此環境應該安裝和執行，例如監視代理程式和防毒軟體的所有標準服務。</span><span class="sxs-lookup"><span data-stu-id="e0553-104">This environment should have all standard services installed and running, such as monitoring agents and antivirus software.</span></span>  
  
## <a name="how-adding-applications-affects-load"></a><span data-ttu-id="e0553-105">如何新增應用程式會影響負載</span><span class="sxs-lookup"><span data-stu-id="e0553-105">How Adding Applications Affects Load</span></span>  
 <span data-ttu-id="e0553-106">您也應該測試新的 BizTalk 應用程式一起移至生產環境中的相同硬體上執行的其他 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0553-106">You should also test new BizTalk applications alongside the other BizTalk applications that are going to run on the same hardware in production.</span></span> <span data-ttu-id="e0553-107">這是因為新的 BizTalk 應用程式放入執行的電腦上的額外負載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e0553-107">This is because the new BizTalk applications put additional load on the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server.</span></span> <span data-ttu-id="e0553-108">這點特別重要的主控件節流演算法中使用按照[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e0553-108">This is especially important in light of the host throttling algorithms that are used in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e0553-109">節流演算法監視總計的可用資源，因此新的 BizTalk 應用程式所造成的額外負載可能誘使節流狀況，這會影響所有正在執行的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0553-109">The throttling algorithm monitors total available resources and hence the additional load incurred by a new BizTalk application may induce a throttling condition which affects all running BizTalk applications.</span></span> <span data-ttu-id="e0553-110">如需詳細資訊，請參閱[如何 BizTalk Server 實作主控件節流](http://go.microsoft.com/fwlink/?LinkId=154389)(http://go.microsoft.com/fwlink/?LinkId=154389)。</span><span class="sxs-lookup"><span data-stu-id="e0553-110">For more information, see [How BizTalk Server Implements Host Throttling](http://go.microsoft.com/fwlink/?LinkId=154389) (http://go.microsoft.com/fwlink/?LinkId=154389).</span></span>  
  
## <a name="testing-load-and-determining-recovery-time"></a><span data-ttu-id="e0553-111">測試負載，並決定復原時間</span><span class="sxs-lookup"><span data-stu-id="e0553-111">Testing Load and Determining Recovery Time</span></span>  
 <span data-ttu-id="e0553-112">您應該測試所有的 BizTalk 應用程式的效能與壓力，才能將它們放入實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="e0553-112">You should test all BizTalk applications for performance and stress before you put them into production.</span></span> <span data-ttu-id="e0553-113">您應該執行測試對預期負載和尖峰負載。</span><span class="sxs-lookup"><span data-stu-id="e0553-113">You should perform your testing against expected loads and against peak loads.</span></span> <span data-ttu-id="e0553-114">您應該判斷 BizTalk 應用程式最大持續輸送量 (MST)。</span><span class="sxs-lookup"><span data-stu-id="e0553-114">You should determine the maximum sustainable throughput (MST) for the BizTalk application.</span></span> <span data-ttu-id="e0553-115">此外，您應該決定從尖峰負載復原系統所需的時間。</span><span class="sxs-lookup"><span data-stu-id="e0553-115">In addition, you should determine how long it takes the system to recover from peak loads.</span></span> <span data-ttu-id="e0553-116">如果系統不會完全復原時，從 尖峰負載下一步的尖峰負載之前，則系統會逐漸遠，並不能完全復原。</span><span class="sxs-lookup"><span data-stu-id="e0553-116">If the system does not fully recover from a peak load before the next peak load occurs, then the system will get progressively farther behind and will not be able to fully recover.</span></span> <span data-ttu-id="e0553-117">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="e0553-117">For more information, see:</span></span>  
  
-   <span data-ttu-id="e0553-118">[測量最大持續性引擎輸送量](http://go.microsoft.com/fwlink/?LinkId=154388)(http://go.microsoft.com/fwlink/?LinkId=154388)</span><span class="sxs-lookup"><span data-stu-id="e0553-118">[Measuring Maximum Sustainable Engine Throughput](http://go.microsoft.com/fwlink/?LinkId=154388) (http://go.microsoft.com/fwlink/?LinkId=154388)</span></span>  
  
-   <span data-ttu-id="e0553-119">[測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID=153815)</span><span class="sxs-lookup"><span data-stu-id="e0553-119">[Measuring Maximum Sustainable Tracking Throughput](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0553-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0553-120">See Also</span></span>  
 [<span data-ttu-id="e0553-121">檢查清單： 測試操作整備</span><span class="sxs-lookup"><span data-stu-id="e0553-121">Checklist: Testing Operational Readiness</span></span>](../technical-guides/checklist-testing-operational-readiness.md)