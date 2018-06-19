---
title: 使用活動 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e218e2a-27f8-4df2-a1e0-27392112d369
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13b56424e06bdb8fad043acd92c22a88ca19f478
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287182"
---
# <a name="using-an-activity"></a><span data-ttu-id="5e467-102">使用活動</span><span class="sxs-lookup"><span data-stu-id="5e467-102">Using an Activity</span></span>
<span data-ttu-id="5e467-103">使用 BAM 最簡易的方式就是使用 BAM API 傳送明確里程碑或資料。</span><span class="sxs-lookup"><span data-stu-id="5e467-103">The simplest way to use BAM is to send explicit milestones or data using the BAM API.</span></span> <span data-ttu-id="5e467-104">您可以將 BAM 活動視為與實際工作單位保持同步的一筆 SQL 資料表記錄。</span><span class="sxs-lookup"><span data-stu-id="5e467-104">You can think of the BAM activity as a record in a SQL table that you are keeping in synchronization with the actual unit of work.</span></span>  
  
-   <span data-ttu-id="5e467-105">呼叫`BeginActivity`的每個新的工作單位。</span><span class="sxs-lookup"><span data-stu-id="5e467-105">Call `BeginActivity` for each new unit of work.</span></span>  
  
-   <span data-ttu-id="5e467-106">呼叫`EndActivity`當工作已完成，且您預期此工作單位的內容中的任何事件。</span><span class="sxs-lookup"><span data-stu-id="5e467-106">Call `EndActivity` when the work is complete and you expect no more events in the context of this unit of work.</span></span>  
  
-   <span data-ttu-id="5e467-107">呼叫[Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx)的實作中，若要傳送的資料和里程碑給資訊工作者有用的關鍵位置。</span><span class="sxs-lookup"><span data-stu-id="5e467-107">Call [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) in critical places of the implementation, to send data and milestones that will be useful to the information worker.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e467-108">事件資料流必須排清之前處置。</span><span class="sxs-lookup"><span data-stu-id="5e467-108">The Event Stream must be flushed before disposing.</span></span> <span data-ttu-id="5e467-109">EventStream 物件在受處置時不會自動排清資料。</span><span class="sxs-lookup"><span data-stu-id="5e467-109">The EventStream object does not perform an automatic flush of the data when disposed.</span></span> <span data-ttu-id="5e467-110">這表示若依照一般常見的程式碼寫法，總是等到活動處理完成後才排清資料流，則一旦發出排清呼叫前發生例外狀況，可能就會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="5e467-110">This means that code you would typically write in which you flush the stream only after you have finished processing your activities can result in data loss if an exception occurs before a call to flush.</span></span>  
>   
>  <span data-ttu-id="5e467-111">為避免資料遺失，建議您將處理和排清作業封裝在 try/finally 區塊中，如以下的虛擬程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="5e467-111">To avoid data loss, we recommend that you encapsulate the processing and flush in a try/finally block as shown in the pseudo code below:</span></span>  
  
```  
BufferedEventStream es = new BufferedEventStream(…)  
Try  
{  
   // Do the activity processing here.  
}  
Finally  
{  
   if (es != null ) es.Flush();  
}  
```  
  
 <span data-ttu-id="5e467-112">下列範例程式碼顯示如何使用 BeginActivity、UpdateActivity 和 EndActivity 處理採購單工作單位。</span><span class="sxs-lookup"><span data-stu-id="5e467-112">The following example code shows how to do use BeginActivity, UpdateActivity, and EndActivity when the unit of work is a Purchase Order.</span></span> <span data-ttu-id="5e467-113">在範例中，我們假設字串變數**poid**識別目前訂單程序中：</span><span class="sxs-lookup"><span data-stu-id="5e467-113">In the example, we assume that the string variable **poid** identifies the current Purchase Order in process:</span></span>  
  
```  
using Microsoft.BizTalk.BAM.EventObservation;  
...   
EventStream es=new DirectEventStream(connectionString,1);  
...  
// At the beginning of the processing of a new work:  
//    Here poid is a string variable that has the current   
//    Purchase Order identifier (e.g. PO number)  
es.BeginActivity("PurchaseOrder",poid);  
es.UpdateActivity("PurchaseOrder",poid,  
    "POReceived",DateTime.UtcNow,  
    "POAmount",100,  
    "CustomerName",""Joe",  
    "CustomerCity","Seattle");  
...  
// few days later  
es.UpdateActivity("PurchaseOrder",poid,  
    "POApproved",DateTime.UtcNow,  
    "ProductName","Widget");  
...  
// and another few days later  
es. UpdateActivity("PurchaseOrder",poid,  
    "POShipped",DateTime.UtcNow);  
...  
// and finally  
es. UpdateActivity("PurchaseOrder",poid,  
    "Delivered",DateTime.UtcNow);  
es.EndActivity("PurchaseOrder",poid);  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e467-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e467-114">See Also</span></span>  
 <span data-ttu-id="5e467-115">[使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md) </span><span class="sxs-lookup"><span data-stu-id="5e467-115">[Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md) </span></span>  
 <span data-ttu-id="5e467-116">[活動接續](../core/activity-continuation.md) </span><span class="sxs-lookup"><span data-stu-id="5e467-116">[Activity Continuation](../core/activity-continuation.md) </span></span>  
 <span data-ttu-id="5e467-117">[BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="5e467-117">[BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="5e467-118">BAM API （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="5e467-118">BAM API (BizTalk Server Sample)</span></span>](../core/bam-api-biztalk-server-sample.md)