---
title: 監控 BizTalk Server 資料庫 |Microsoft 文件
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
ms.openlocfilehash: fed740f0c2689c8c531a2f92ad4be356d82205db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298166"
---
# <a name="monitoring-biztalk-server-databases"></a><span data-ttu-id="742bd-102">監控 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="742bd-102">Monitoring BizTalk Server Databases</span></span>
<span data-ttu-id="742bd-103">您可以執行監視 BizTalk Server SQL 代理程式作業，以識別任何已知的問題，管理、 訊息方塊或 DTA 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="742bd-103">You can run the Monitor BizTalk Server SQL Agent job to identify any known issues in Management, Message Box, or DTA databases.</span></span> <span data-ttu-id="742bd-104">當您在 BizTalk Server 管理主控台中設定 BizTalk 群組或從舊版本升級 BizTalk 時，就會建立此工作。</span><span class="sxs-lookup"><span data-stu-id="742bd-104">The job is created when you configure a BizTalk group in BizTalk Server Administration console or upgrade BizTalk from the previous version.</span></span>  
  
## <a name="the-monitor-biztalk-server-job"></a><span data-ttu-id="742bd-105">監視 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="742bd-105">The Monitor BizTalk Server Job</span></span>  
 <span data-ttu-id="742bd-106">[監控 BizTalk Server] 作業會在管理、訊息方塊或 DTA 資料庫中掃描下列問題：</span><span class="sxs-lookup"><span data-stu-id="742bd-106">The Monitor BizTalk Server job scans for the following issues in Management, Message Box, and DTA databases:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="742bd-107">[監控 BizTalk Server] 工作只會掃描問題。</span><span class="sxs-lookup"><span data-stu-id="742bd-107">The Monitor BizTalk Server job only scans for issues.</span></span> <span data-ttu-id="742bd-108">並不會修正找到的問題。</span><span class="sxs-lookup"><span data-stu-id="742bd-108">It does not fix the issues found.</span></span>  
  
-   <span data-ttu-id="742bd-109">不具任何參考的訊息</span><span class="sxs-lookup"><span data-stu-id="742bd-109">Messages without any references</span></span>  
  
-   <span data-ttu-id="742bd-110">不具參考計數的訊息</span><span class="sxs-lookup"><span data-stu-id="742bd-110">Messages without reference counts</span></span>  
  
-   <span data-ttu-id="742bd-111">參考計數小於 0 的訊息</span><span class="sxs-lookup"><span data-stu-id="742bd-111">Messages with reference count less than 0</span></span>  
  
-   <span data-ttu-id="742bd-112">不具多工緩衝處理列的訊息參考</span><span class="sxs-lookup"><span data-stu-id="742bd-112">Message references without spool rows</span></span>  
  
-   <span data-ttu-id="742bd-113">不具執行個體的訊息參考</span><span class="sxs-lookup"><span data-stu-id="742bd-113">Message references without instances</span></span>  
  
-   <span data-ttu-id="742bd-114">不具執行個體的執行個體狀態</span><span class="sxs-lookup"><span data-stu-id="742bd-114">Instance state without instances</span></span>  
  
-   <span data-ttu-id="742bd-115">不具對應執行個體的執行個體訂閱</span><span class="sxs-lookup"><span data-stu-id="742bd-115">Instance subscriptions without corresponding instances</span></span>  
  
-   <span data-ttu-id="742bd-116">被遺棄的 DTA 服務執行個體</span><span class="sxs-lookup"><span data-stu-id="742bd-116">Orphaned DTA service instances</span></span>  
  
-   <span data-ttu-id="742bd-117">被遺棄的 DTA 服務執行個體例外狀況</span><span class="sxs-lookup"><span data-stu-id="742bd-117">Orphaned DTA service instance exceptions</span></span>  
  
-   <span data-ttu-id="742bd-118">啟用全域追蹤選項時，任何主控件執行個體上沒有執行 TDDS</span><span class="sxs-lookup"><span data-stu-id="742bd-118">TDDS is not running on any host instance when global tracking option is enabled</span></span>  
  
 <span data-ttu-id="742bd-119">已設定 [監控 BizTalk Server] 工作，而且已自動化成一週執行一次。</span><span class="sxs-lookup"><span data-stu-id="742bd-119">The Monitor BizTalk Server job is configured and automated to run once in a week.</span></span> <span data-ttu-id="742bd-120">因為工作會耗用大量運算資源，我們建議您排定的停機時間或低流量期間執行。</span><span class="sxs-lookup"><span data-stu-id="742bd-120">Since the job is computationally intensive, we recommended that you schedule it to run during periods of downtime or low traffic.</span></span>  
<span data-ttu-id="742bd-121">作業失敗時，如果遇到任何問題。傳回的錯誤字串會包含找到的問題數。</span><span class="sxs-lookup"><span data-stu-id="742bd-121">The job fails if it encounters any issues; the error string returned contains the number of issues found.</span></span> <span data-ttu-id="742bd-122">否則表示已順利執行。</span><span class="sxs-lookup"><span data-stu-id="742bd-122">Else, it runs successfully.</span></span> <span data-ttu-id="742bd-123">您可以在工作記錄中查看詳細資料。</span><span class="sxs-lookup"><span data-stu-id="742bd-123">You can see the details in the job history.</span></span> <span data-ttu-id="742bd-124">如果您使用系統管理員權限執行作業，就會記錄錯誤字串作業歷程記錄和 SQL Server 應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="742bd-124">If you run the job with Administrator privileges, the error string will be logged to both the job history and the SQL Server Application log.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="742bd-125">這項工作的失敗不一定是構成嚴重的問題，但而不是問題，應調查和解決的定期維護 BizTalk Server 資料庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="742bd-125">Failure of this job does not necessarily constitute a critical issue, but rather an issue that should be investigated and addressed as part of regular maintenance of the BizTalk Server databases.</span></span> <span data-ttu-id="742bd-126">此作業失敗時設計事件會探索其中一個上面所列的問題。</span><span class="sxs-lookup"><span data-stu-id="742bd-126">This job fails by design in the event it discovers one of the issues listed above.</span></span>