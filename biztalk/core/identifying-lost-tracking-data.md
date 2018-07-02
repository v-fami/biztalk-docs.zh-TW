---
title: 識別遺失的追蹤資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data loss, HAT
- reporting tools
- Orchestration Debugger
- Tracking database, data loss
- HAT, data loss
- HAT, Operation View tool
- HAT, reporting tools
- Operation View tool, MessageBox database
- MessageBox database, Operation View tool
- Operation View tool, data loss
ms.assetid: 1ac13e2c-cd5e-437e-b924-d4547931874e
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17116d3a560e968e8dd9da0e42f5af221c23f5d3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982855"
---
# <a name="identifying-lost-tracking-data"></a><span data-ttu-id="dd9a6-102">識別遺失的追蹤資料</span><span class="sxs-lookup"><span data-stu-id="dd9a6-102">Identifying Lost Tracking Data</span></span>
<span data-ttu-id="dd9a6-103">您可以使用 BizTalk Server 管理主控台，幫助您識別哪些追蹤資料因為硬體失敗而遺失。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-103">You can use the BizTalk Server Administration console to help identify which tracking data has been lost as a result of a hardware failure.</span></span> <span data-ttu-id="dd9a6-104">您可以使用 BizTalk Server 管理主控台的即時或封存的資料。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-104">You can use the BizTalk Server Administration console for live or archived data.</span></span>  
  
 <span data-ttu-id="dd9a6-105">您可以使用 BizTalk Server 管理主控台來判斷復原 MessageBox 時哪些服務為作用中。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-105">You can use the BizTalk Server Administration console to determine which services were active at the time the MessageBox was recovered.</span></span> <span data-ttu-id="dd9a6-106">因為復原資料庫的時間與發生硬體錯誤的時間之間有差距，您可能無法判斷部分交易的狀態。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-106">Because there is a gap between the time that the database was recovered and the time of the hardware failure, you may not be able to determine the state of some of the transactions.</span></span>  
  
 <span data-ttu-id="dd9a6-107">您可以使用追蹤資料來識別哪些服務執行個體完成，而且啟動之後的復原點，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd9a6-107">You can use tracking data to identify which service instances completed and started after the point of recovery, as follows:</span></span>  
  
- <span data-ttu-id="dd9a6-108">尋找自您最後一次備份資料庫之後已完成或啟動的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-108">Look for which instances completed or started since the last time you backed up the database.</span></span>  
  
- <span data-ttu-id="dd9a6-109">如果 BizTalk 追蹤 (BizTalkDTADb) 資料庫中的資料指出訊息已啟動但尚未完成，且訊息不在資料庫中，則會在最後一次備份後傳送該訊息。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-109">If data in the BizTalk Tracking (BizTalkDTADb) database indicates that the message started but did not complete, and the message is not in the database, then that message was sent after the last backup.</span></span>  
  
  <span data-ttu-id="dd9a6-110">追蹤可以報告完成時，任何服務，可能表示服務已啟動。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-110">Tracking can report on any service that completed, and it can indicate that a service started.</span></span> <span data-ttu-id="dd9a6-111">追蹤資料會先存放在 MessageBox 中，然後再移動到 BizTalk 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-111">Tracking data is first staged to the MessageBox and then moved to the BizTalk Tracking database.</span></span> <span data-ttu-id="dd9a6-112">存放的資料可能已在 BAM 事件匯流排服務的積存中遺失。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-112">The data that was staged may have been lost to the backlog of the BAM Event Bus service.</span></span>  
  
  <span data-ttu-id="dd9a6-113">當所有資料庫因操作因素需要還原為相同的標記時，您可以封存模式來使用 BizTalk 追蹤資料庫 (未遺失的)，以查看標記之後發生了什麼事。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-113">While all databases need to be restored to the same mark for operational reasons, you can use a BizTalk Tracking database (that was not lost) in Archive mode to see what happened after the mark.</span></span>  
  
  <span data-ttu-id="dd9a6-114">如果追蹤會顯示已完成的服務執行個體，您可以終止該執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-114">If tracking shows a service instance as having completed, you can terminate that instance.</span></span> <span data-ttu-id="dd9a6-115">它可能會顯示在復原時間點之後啟動的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-115">It may show instances that started after the point of recovery.</span></span> <span data-ttu-id="dd9a6-116">如果是這樣，您將需要補償這些執行個體執行的任何動作，然後重新提交它們的初始啟動訊息。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-116">If so, you will need to compensate for any actions these instances took and then resubmit their initial activation messages.</span></span>  
  
  <span data-ttu-id="dd9a6-117">若要查看執行，然後使用 若要查看哪些訊息應已傳送或接收的 訊息流程的最後一個圖形，您可以使用協調流程偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-117">You can use the Orchestration Debugger to see the last shapes that executed, and then use Message Flow to see what message should have been sent or received.</span></span>  
  
  <span data-ttu-id="dd9a6-118">如果 BizTalk 追蹤資料庫遺失，必須使用外部系統報告機制來探索還原時間點之後發生的所有動作。</span><span class="sxs-lookup"><span data-stu-id="dd9a6-118">If the BizTalk Tracking database was lost, all discovery of what happened past the point of recovery will need to be done by using the external systems reporting mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9a6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd9a6-119">See Also</span></span>  
 [<span data-ttu-id="dd9a6-120">解決資料遺失</span><span class="sxs-lookup"><span data-stu-id="dd9a6-120">Resolving Data Loss</span></span>](../core/resolving-data-loss.md)