---
title: 測試時的建議引擎效能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maximum sustainable throughput (MST), best practices
ms.assetid: 0aa9d833-0e7d-4347-a6ca-8d658749b4f2
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06fc2d81ca8121fe625a30258070281d2b3ff4bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268422"
---
# <a name="recommendations-when-testing-engine-performance"></a><span data-ttu-id="c20ea-102">測試引擎效能時的建議</span><span class="sxs-lookup"><span data-stu-id="c20ea-102">Recommendations When Testing Engine Performance</span></span>
<span data-ttu-id="c20ea-103">在測試 BizTalk 引擎效能時，應該遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="c20ea-103">The following guidelines should be followed when testing BizTalk engine performance:</span></span>  
  
 <span data-ttu-id="c20ea-104">**知道您的負載行為設定檔**已說明三種負載測試，因為，請務必知道您根據一段時間處理訊息的負載設定檔。</span><span class="sxs-lookup"><span data-stu-id="c20ea-104">**Know your load behavior profile** As the three load tests have illustrated, it is critical to know the profile of your load in terms of messages processed over time.</span></span>  <span data-ttu-id="c20ea-105">您越瞭解這點，就能越正確地測試和調整您的系統容量。</span><span class="sxs-lookup"><span data-stu-id="c20ea-105">The better this is understood, the more accurately you can test and adjust your system capacity.</span></span> <span data-ttu-id="c20ea-106">若您只知道峰值傳輸量需求，則最保險的方式就是調整您的系統大小，使可持續的傳輸量上限大於或等於您的峰值負載。</span><span class="sxs-lookup"><span data-stu-id="c20ea-106">If all you know is your peak throughput requirement, then the most conservative approach would be to size your system so that your maximum sustainable throughput is the same or higher than your peak load.</span></span> <span data-ttu-id="c20ea-107">不過，若您可預測負載的峰值與谷值，可以將系統大小的最佳值調整在峰值之間，這樣能有較低且較少的整體部署成本。</span><span class="sxs-lookup"><span data-stu-id="c20ea-107">However, if you know that you have predictable peaks and valleys in your load, you can better optimize your system to recover between peaks, resulting in a smaller, less expensive overall deployment.</span></span>  
  
 <span data-ttu-id="c20ea-108">**及早測試效能**避免陷入大筆投資中設計和測試的功能，您的方案，而是等到過去一分鐘測試生產硬體的效能。</span><span class="sxs-lookup"><span data-stu-id="c20ea-108">**Test performance early** Avoid falling into the trap of investing significant effort in designing and testing the functionality of your solution, but waiting until the last minute to test performance on production hardware.</span></span> <span data-ttu-id="c20ea-109">請盡早在您的開發週期中，於模擬預期負載設定檔的系統上，執行效能測試。</span><span class="sxs-lookup"><span data-stu-id="c20ea-109">Run performance tests on your system that simulate the expected load profile as early as you possibly can in your development cycle.</span></span> <span data-ttu-id="c20ea-110">若您必須變更任何的設計或結構來完成您的目標，能越早知道必須這樣做，便能有越充裕的時間去進行調整和再次測試。</span><span class="sxs-lookup"><span data-stu-id="c20ea-110">If you have to change anything in your design or architecture to achieve your goals knowing this early will give you time to adjust and test again.</span></span>  
  
 <span data-ttu-id="c20ea-111">**測試效能時，模擬預期的負載設定檔**這兩個主要元件：</span><span class="sxs-lookup"><span data-stu-id="c20ea-111">**Emulate your expected load profile when testing performance** There are two primary components to this:</span></span>  
  
1.  <span data-ttu-id="c20ea-112">模擬某段時間的負載設定檔。</span><span class="sxs-lookup"><span data-stu-id="c20ea-112">Emulate the load profile over time.</span></span>  
  
2.  <span data-ttu-id="c20ea-113">執行測試的時間夠久才能評估是否有持續性。</span><span class="sxs-lookup"><span data-stu-id="c20ea-113">Run the test long enough to evaluate if it is sustainable.</span></span>  
  
 <span data-ttu-id="c20ea-114">一般來說，若您的週期為每日時，您至少應該規劃執行一天的效能測試，以驗證其持續性。</span><span class="sxs-lookup"><span data-stu-id="c20ea-114">If, as is commonly the case, your cycles are daily in nature you should plan to run performance tests for at least one day to validate sustainability.</span></span> <span data-ttu-id="c20ea-115">執行測試的時間越久越好。</span><span class="sxs-lookup"><span data-stu-id="c20ea-115">The longer that you run the tests, the better.</span></span>  
  
 <span data-ttu-id="c20ea-116">**模擬生產組態**範例、 數目和類型的連接埠的內容，在主機和主機執行個體組態、 資料庫組態和配接器安裝程式。</span><span class="sxs-lookup"><span data-stu-id="c20ea-116">**Emulate the production configuration** For example, the number and type of ports, the host and host instance configuration, database configuration, and adapter setup.</span></span> <span data-ttu-id="c20ea-117">請勿假設組態變更不會嚴重影響效能。</span><span class="sxs-lookup"><span data-stu-id="c20ea-117">Don’t assume that configuration changes will not significantly impact performance.</span></span>  
  
 <span data-ttu-id="c20ea-118">**使用真實的訊息**訊息大小與訊息複雜性會影響效能，因此請務必和測試具有相同的訊息結構描述與您打算在生產環境中看到的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c20ea-118">**Use real messages** Message sizes and message complexity affect performance, so be sure and test with the same message schemas and instances that you plan to see in production.</span></span>  
  
 <span data-ttu-id="c20ea-119">**效能測試期間模擬您正常作業**雖然負載測試不包括它們的標準作業活動，如定期資料庫查詢、 備份以及清除都會影響到您的持續性輸送量，因此請確定您在效能與容量測試回合執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="c20ea-119">**Emulate your normal operations during performance tests** Though the load tests did not include them, standard operations activities such as periodic database queries, backups, and purging will affect your sustainable throughput, so make sure you are performing these tasks during your performance and capacity test runs.</span></span> <span data-ttu-id="c20ea-120">若您計畫在產品中使用到 DTA 和 BAM 追蹤時，請加入它們。</span><span class="sxs-lookup"><span data-stu-id="c20ea-120">This includes both DTA and BAM tracking, if you plan to use them in production.</span></span>  
  
 <span data-ttu-id="c20ea-121">**MessageBox 的 I/O 子系統的速度是成功的關鍵因素**執行負載測試進行快速的存放區域網路使用專門用來增建之 MessageBox 資料庫檔案。即使在這種情況下，清除工作也能將 SQL 資料檔的閒置時間趨近於零。</span><span class="sxs-lookup"><span data-stu-id="c20ea-121">**The speed of the I/O subsystem for the MessageBox is a key success factor** The load tests that were performed made use of a fast Storage Area Network for the MessageBox database files that is dedicated to this build-out. Even in this case, the cleanup jobs were able to drive the idle time to near zero for the SQL data file.</span></span> <span data-ttu-id="c20ea-122">生產系統中的 I/O 子系統經常是瓶頸的所在。</span><span class="sxs-lookup"><span data-stu-id="c20ea-122">The I/O subsystem is frequently a bottleneck in production systems.</span></span> <span data-ttu-id="c20ea-123">常用的最佳化 SQL I/O 策略就是在個別的實體磁碟機上放置資料檔與記錄檔 (若可行的話)。</span><span class="sxs-lookup"><span data-stu-id="c20ea-123">A common strategy to optimize SQL I/O is to place the database data file(s) and log file(s) on separate physical drives, if possible.</span></span>  
  
 <span data-ttu-id="c20ea-124">**請確定 SQL 代理程式正在執行所有的 MessageBox 伺服器上**很明顯地，清除工作會永遠不會執行，如果 SQL 代理程式未執行，因此請確定它們正在執行。</span><span class="sxs-lookup"><span data-stu-id="c20ea-124">**Make sure the SQL Agent is running on all MessageBox servers** Clearly, the cleanup jobs will never run if the SQL Agent is not running, so make sure these are running.</span></span>  
  
 <span data-ttu-id="c20ea-125">**多工緩衝處理深度是重要的指示器**其他指標，不論此量值可讓您快速且輕鬆的方式，來評估您的系統正在既。</span><span class="sxs-lookup"><span data-stu-id="c20ea-125">**Spool depth is a key indicator** Regardless of other indicators, this measure will give you a quick and easy way to assess if your system is being overdriven or not.</span></span>