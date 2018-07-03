---
title: 監視 BizTalk Server 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7fee5015-e818-459b-aeeb-a084ef355600
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3cb759bf377cfe77f1e346a94fca739b8532a44
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002127"
---
# <a name="monitoring-biztalk-server-databases"></a><span data-ttu-id="af595-102">監視 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="af595-102">Monitoring BizTalk Server Databases</span></span>
<span data-ttu-id="af595-103">您可以執行監視 BizTalk Server SQL Agent 作業，以識別任何已知的問題，管理、 訊息方塊或 DTA 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="af595-103">You can run the Monitor BizTalk Server SQL Agent job to identify any known issues in Management, Message Box, or DTA databases.</span></span> <span data-ttu-id="af595-104">當您在 BizTalk Server 管理主控台中設定 BizTalk 群組或從舊版本升級 BizTalk 時，就會建立此工作。</span><span class="sxs-lookup"><span data-stu-id="af595-104">The job is created when you configure a BizTalk group in BizTalk Server Administration console or upgrade BizTalk from the previous version.</span></span>  
  
## <a name="the-monitor-biztalk-server-job"></a><span data-ttu-id="af595-105">監視 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="af595-105">The Monitor BizTalk Server Job</span></span>  
 <span data-ttu-id="af595-106">[監控 BizTalk Server] 作業會在管理、訊息方塊或 DTA 資料庫中掃描下列問題：</span><span class="sxs-lookup"><span data-stu-id="af595-106">The Monitor BizTalk Server job scans for the following issues in Management, Message Box, and DTA databases:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af595-107">[監控 BizTalk Server] 工作只會掃描問題。</span><span class="sxs-lookup"><span data-stu-id="af595-107">The Monitor BizTalk Server job only scans for issues.</span></span> <span data-ttu-id="af595-108">並不會修正找到的問題。</span><span class="sxs-lookup"><span data-stu-id="af595-108">It does not fix the issues found.</span></span>  
  
- <span data-ttu-id="af595-109">不具任何參考的訊息</span><span class="sxs-lookup"><span data-stu-id="af595-109">Messages without any references</span></span>  
  
- <span data-ttu-id="af595-110">不具參考計數的訊息</span><span class="sxs-lookup"><span data-stu-id="af595-110">Messages without reference counts</span></span>  
  
- <span data-ttu-id="af595-111">參考計數小於 0 的訊息</span><span class="sxs-lookup"><span data-stu-id="af595-111">Messages with reference count less than 0</span></span>  
  
- <span data-ttu-id="af595-112">不具多工緩衝處理列的訊息參考</span><span class="sxs-lookup"><span data-stu-id="af595-112">Message references without spool rows</span></span>  
  
- <span data-ttu-id="af595-113">不具執行個體的訊息參考</span><span class="sxs-lookup"><span data-stu-id="af595-113">Message references without instances</span></span>  
  
- <span data-ttu-id="af595-114">不具執行個體的執行個體狀態</span><span class="sxs-lookup"><span data-stu-id="af595-114">Instance state without instances</span></span>  
  
- <span data-ttu-id="af595-115">不具對應執行個體的執行個體訂閱</span><span class="sxs-lookup"><span data-stu-id="af595-115">Instance subscriptions without corresponding instances</span></span>  
  
- <span data-ttu-id="af595-116">被遺棄的 DTA 服務執行個體</span><span class="sxs-lookup"><span data-stu-id="af595-116">Orphaned DTA service instances</span></span>  
  
- <span data-ttu-id="af595-117">被遺棄的 DTA 服務執行個體例外狀況</span><span class="sxs-lookup"><span data-stu-id="af595-117">Orphaned DTA service instance exceptions</span></span>  
  
- <span data-ttu-id="af595-118">啟用全域追蹤選項時，任何主控件執行個體上未執行 TDDS</span><span class="sxs-lookup"><span data-stu-id="af595-118">TDDS is not running on any host instance when global tracking option is enabled</span></span>  
  
  <span data-ttu-id="af595-119">已設定 [監控 BizTalk Server] 工作，而且已自動化成一週執行一次。</span><span class="sxs-lookup"><span data-stu-id="af595-119">The Monitor BizTalk Server job is configured and automated to run once in a week.</span></span> <span data-ttu-id="af595-120">因為工作會耗用大量運算資源，我們建議您排程的停機時間或低流量期間執行。</span><span class="sxs-lookup"><span data-stu-id="af595-120">Since the job is computationally intensive, we recommended that you schedule it to run during periods of downtime or low traffic.</span></span>  
  <span data-ttu-id="af595-121">作業失敗時，如果遇到任何問題;傳回的錯誤字串會包含找到的問題數。</span><span class="sxs-lookup"><span data-stu-id="af595-121">The job fails if it encounters any issues; the error string returned contains the number of issues found.</span></span> <span data-ttu-id="af595-122">否則表示已順利執行。</span><span class="sxs-lookup"><span data-stu-id="af595-122">Else, it runs successfully.</span></span> <span data-ttu-id="af595-123">您可以在工作記錄中查看詳細資料。</span><span class="sxs-lookup"><span data-stu-id="af595-123">You can see the details in the job history.</span></span> <span data-ttu-id="af595-124">如果您是系統管理員權限執行作業，將記錄錯誤字串，作業記錄和 SQL Server 應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="af595-124">If you run the job with Administrator privileges, the error string will be logged to both the job history and the SQL Server Application log.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="af595-125">這項作業失敗不一定是構成重要的問題，但相反地，應該調查和解決一部分的 BizTalk Server 資料庫的定期維護的問題。</span><span class="sxs-lookup"><span data-stu-id="af595-125">Failure of this job does not necessarily constitute a critical issue, but rather an issue that should be investigated and addressed as part of regular maintenance of the BizTalk Server databases.</span></span> <span data-ttu-id="af595-126">萬一它會探索其中一個上述問題，這項作業會失敗所設計。</span><span class="sxs-lookup"><span data-stu-id="af595-126">This job fails by design in the event it discovers one of the issues listed above.</span></span>