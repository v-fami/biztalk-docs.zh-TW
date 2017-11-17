---
title: "檢查清單： 測試操作整備 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecdf2609-ba77-4756-a949-ab4e10c54313
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6bc8ff5b2b3ca8d629c30b1cb37f83cb7847b2f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-testing-operational-readiness"></a><span data-ttu-id="f6911-102">檢查清單： 測試操作整備</span><span class="sxs-lookup"><span data-stu-id="f6911-102">Checklist: Testing Operational Readiness</span></span>
<span data-ttu-id="f6911-103">只有至少執行或經常忽略的重要程序就操作整備測試。</span><span class="sxs-lookup"><span data-stu-id="f6911-103">Testing for operational readiness is a vital procedure that is often overlooked or is performed only minimally.</span></span> <span data-ttu-id="f6911-104">是進行徹底測試所有企業級應用程式中，關鍵需求，並以開發方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也不例外。</span><span class="sxs-lookup"><span data-stu-id="f6911-104">Thorough testing is a critical requirement of any enterprise-level application, and a solution developed using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is no exception.</span></span> <span data-ttu-id="f6911-105">最少，您應該執行下列測試之前將 BizTalk 方案移到實際執行環境：</span><span class="sxs-lookup"><span data-stu-id="f6911-105">At a minimum, you should perform the following testing before moving a BizTalk solution into production:</span></span>  
  
|<span data-ttu-id="f6911-106">步驟</span><span class="sxs-lookup"><span data-stu-id="f6911-106">Steps</span></span>|<span data-ttu-id="f6911-107">參考</span><span class="sxs-lookup"><span data-stu-id="f6911-107">Reference</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="f6911-108">單元測試</span><span class="sxs-lookup"><span data-stu-id="f6911-108">Unit testing</span></span>|[<span data-ttu-id="f6911-109">執行單元測試</span><span class="sxs-lookup"><span data-stu-id="f6911-109">Performing Unit Testing</span></span>](../technical-guides/performing-unit-testing.md)|  
|<span data-ttu-id="f6911-110">功能測試</span><span class="sxs-lookup"><span data-stu-id="f6911-110">Functional testing</span></span>|[<span data-ttu-id="f6911-111">執行功能測試</span><span class="sxs-lookup"><span data-stu-id="f6911-111">Performing Functional Testing</span></span>](../technical-guides/performing-functional-testing.md)|  
|<span data-ttu-id="f6911-112">瓶頸測試與微調</span><span class="sxs-lookup"><span data-stu-id="f6911-112">Bottleneck testing and tuning</span></span>|[<span data-ttu-id="f6911-113">執行測試與微調瓶頸</span><span class="sxs-lookup"><span data-stu-id="f6911-113">Performing Bottleneck Testing and Tuning</span></span>](../technical-guides/performing-bottleneck-testing-and-tuning.md)|  
|<span data-ttu-id="f6911-114">負載和最大持續輸送量 (MST) 測試</span><span class="sxs-lookup"><span data-stu-id="f6911-114">Load and maximum sustainable throughput (MST) testing</span></span>|[<span data-ttu-id="f6911-115">執行負載和輸送量測試</span><span class="sxs-lookup"><span data-stu-id="f6911-115">Performing Load and Throughput Testing</span></span>](../technical-guides/performing-load-and-throughput-testing.md)|  
|<span data-ttu-id="f6911-116">可用性測試：</span><span class="sxs-lookup"><span data-stu-id="f6911-116">Availability testing:</span></span><br /><br /> <span data-ttu-id="f6911-117">-測試個別硬體元件失敗。</span><span class="sxs-lookup"><span data-stu-id="f6911-117">-   Test individual hardware component failure.</span></span><br /><span data-ttu-id="f6911-118">-測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]失敗。</span><span class="sxs-lookup"><span data-stu-id="f6911-118">-   Test [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] failure.</span></span><br /><span data-ttu-id="f6911-119">-測試叢集節點容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="f6911-119">-   Test cluster node failover.</span></span><br /><span data-ttu-id="f6911-120">-測試復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫使用 SQL Server 記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="f6911-120">-   Test recovery of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases using SQL Server log shipping.</span></span>|[<span data-ttu-id="f6911-121">執行可用性測試</span><span class="sxs-lookup"><span data-stu-id="f6911-121">Performing Availability Testing</span></span>](../technical-guides/performing-availability-testing.md)|  
  
## <a name="in-this-section"></a><span data-ttu-id="f6911-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="f6911-122">In This Section</span></span>  
  
-   [<span data-ttu-id="f6911-123">執行單元測試</span><span class="sxs-lookup"><span data-stu-id="f6911-123">Performing Unit Testing</span></span>](../technical-guides/performing-unit-testing.md)  
  
-   [<span data-ttu-id="f6911-124">執行功能測試</span><span class="sxs-lookup"><span data-stu-id="f6911-124">Performing Functional Testing</span></span>](../technical-guides/performing-functional-testing.md)  
  
-   [<span data-ttu-id="f6911-125">執行測試與微調瓶頸</span><span class="sxs-lookup"><span data-stu-id="f6911-125">Performing Bottleneck Testing and Tuning</span></span>](../technical-guides/performing-bottleneck-testing-and-tuning.md)  
  
-   [<span data-ttu-id="f6911-126">執行負載和輸送量測試</span><span class="sxs-lookup"><span data-stu-id="f6911-126">Performing Load and Throughput Testing</span></span>](../technical-guides/performing-load-and-throughput-testing.md)  
  
-   [<span data-ttu-id="f6911-127">執行可用性測試</span><span class="sxs-lookup"><span data-stu-id="f6911-127">Performing Availability Testing</span></span>](../technical-guides/performing-availability-testing.md)  
  
-   [<span data-ttu-id="f6911-128">測試的工具</span><span class="sxs-lookup"><span data-stu-id="f6911-128">Tools for Testing</span></span>](~/technical-guides/tools-for-testing.md)