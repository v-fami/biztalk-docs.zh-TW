---
title: 檢查清單： 測試作業整備 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecdf2609-ba77-4756-a949-ab4e10c54313
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58a10610595b990e6fc2bae1838fa5653a4b2be0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982597"
---
# <a name="checklist-testing-operational-readiness"></a><span data-ttu-id="78379-102">檢查清單： 測試作業整備</span><span class="sxs-lookup"><span data-stu-id="78379-102">Checklist: Testing Operational Readiness</span></span>
<span data-ttu-id="78379-103">作業整備測試是常被忽略，或只有最少執行的重要程序。</span><span class="sxs-lookup"><span data-stu-id="78379-103">Testing for operational readiness is a vital procedure that is often overlooked or is performed only minimally.</span></span> <span data-ttu-id="78379-104">任何企業級應用程式中，關鍵需求是進行徹底測試和開發的方案使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也不例外。</span><span class="sxs-lookup"><span data-stu-id="78379-104">Thorough testing is a critical requirement of any enterprise-level application, and a solution developed using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is no exception.</span></span> <span data-ttu-id="78379-105">至少，您應該執行下列測試，再移至生產環境的 BizTalk 解決方案：</span><span class="sxs-lookup"><span data-stu-id="78379-105">At a minimum, you should perform the following testing before moving a BizTalk solution into production:</span></span>  


|                                                                                                                                                                                         <span data-ttu-id="78379-106">步驟</span><span class="sxs-lookup"><span data-stu-id="78379-106">Steps</span></span>                                                                                                                                                                                          |                                                  <span data-ttu-id="78379-107">參考</span><span class="sxs-lookup"><span data-stu-id="78379-107">Reference</span></span>                                                  |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                                      <span data-ttu-id="78379-108">單元測試</span><span class="sxs-lookup"><span data-stu-id="78379-108">Unit testing</span></span>                                                                                                                                                                                      |                  [<span data-ttu-id="78379-109">執行單元測試</span><span class="sxs-lookup"><span data-stu-id="78379-109">Performing Unit Testing</span></span>](../technical-guides/performing-unit-testing.md)                  |
|                                                                                                                                                                                   <span data-ttu-id="78379-110">功能測試</span><span class="sxs-lookup"><span data-stu-id="78379-110">Functional testing</span></span>                                                                                                                                                                                   |            [<span data-ttu-id="78379-111">執行功能測試</span><span class="sxs-lookup"><span data-stu-id="78379-111">Performing Functional Testing</span></span>](../technical-guides/performing-functional-testing.md)            |
|                                                                                                                                                                             <span data-ttu-id="78379-112">瓶頸測試與微調</span><span class="sxs-lookup"><span data-stu-id="78379-112">Bottleneck testing and tuning</span></span>                                                                                                                                                                              | [<span data-ttu-id="78379-113">執行瓶頸測試與調整</span><span class="sxs-lookup"><span data-stu-id="78379-113">Performing Bottleneck Testing and Tuning</span></span>](../technical-guides/performing-bottleneck-testing-and-tuning.md) |
|                                                                                                                                                                 <span data-ttu-id="78379-114">負載和測試的最大持續輸送量 (MST)</span><span class="sxs-lookup"><span data-stu-id="78379-114">Load and maximum sustainable throughput (MST) testing</span></span>                                                                                                                                                                  |   [<span data-ttu-id="78379-115">執行負載和輸送量測試</span><span class="sxs-lookup"><span data-stu-id="78379-115">Performing Load and Throughput Testing</span></span>](../technical-guides/performing-load-and-throughput-testing.md)   |
| <span data-ttu-id="78379-116">可用性測試：</span><span class="sxs-lookup"><span data-stu-id="78379-116">Availability testing:</span></span><br /><br /> <span data-ttu-id="78379-117">-測試個別硬體元件失敗。</span><span class="sxs-lookup"><span data-stu-id="78379-117">-   Test individual hardware component failure.</span></span><br /><span data-ttu-id="78379-118">-測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]失敗。</span><span class="sxs-lookup"><span data-stu-id="78379-118">-   Test [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] failure.</span></span><br /><span data-ttu-id="78379-119">-測試叢集節點容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="78379-119">-   Test cluster node failover.</span></span><br /><span data-ttu-id="78379-120">-測試復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫使用 SQL Server 記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="78379-120">-   Test recovery of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases using SQL Server log shipping.</span></span> |          [<span data-ttu-id="78379-121">執行可用性測試</span><span class="sxs-lookup"><span data-stu-id="78379-121">Performing Availability Testing</span></span>](../technical-guides/performing-availability-testing.md)          |

## <a name="in-this-section"></a><span data-ttu-id="78379-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="78379-122">In This Section</span></span>  

-   [<span data-ttu-id="78379-123">執行單元測試</span><span class="sxs-lookup"><span data-stu-id="78379-123">Performing Unit Testing</span></span>](../technical-guides/performing-unit-testing.md)  

-   [<span data-ttu-id="78379-124">執行功能測試</span><span class="sxs-lookup"><span data-stu-id="78379-124">Performing Functional Testing</span></span>](../technical-guides/performing-functional-testing.md)  

-   [<span data-ttu-id="78379-125">執行瓶頸測試與調整</span><span class="sxs-lookup"><span data-stu-id="78379-125">Performing Bottleneck Testing and Tuning</span></span>](../technical-guides/performing-bottleneck-testing-and-tuning.md)  

-   [<span data-ttu-id="78379-126">執行負載和輸送量測試</span><span class="sxs-lookup"><span data-stu-id="78379-126">Performing Load and Throughput Testing</span></span>](../technical-guides/performing-load-and-throughput-testing.md)  

-   [<span data-ttu-id="78379-127">執行可用性測試</span><span class="sxs-lookup"><span data-stu-id="78379-127">Performing Availability Testing</span></span>](../technical-guides/performing-availability-testing.md)  

-   [<span data-ttu-id="78379-128">測試的工具</span><span class="sxs-lookup"><span data-stu-id="78379-128">Tools for Testing</span></span>](~/technical-guides/tools-for-testing.md)