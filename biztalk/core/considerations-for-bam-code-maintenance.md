---
title: "BAM 的考量，程式碼維護 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, code maintenance
- BAMInterceptor class
ms.assetid: e1f1d8e0-207c-47e1-b9bd-a473c86922ce
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f7cfdb75a32c23ef5c8dedec3b6a4c783bf089a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-bam-code-maintenance"></a><span data-ttu-id="34043-102">BAM 程式碼維護的考量</span><span class="sxs-lookup"><span data-stu-id="34043-102">Considerations for BAM Code Maintenance</span></span>
<span data-ttu-id="34043-103">在決定如何檢測應用程式以便使用 BAM 時，您應該考量未來需求變更的可能性。</span><span class="sxs-lookup"><span data-stu-id="34043-103">When you decide how to instrument your application to use BAM, you should consider the likelihood that requirements will change.</span></span> <span data-ttu-id="34043-104">如果您在其中一個 [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) 類別上呼叫方法來寫入受監視的資料，您基本上就是以「硬式編碼」的方式在應用程式中寫入觀察模型。</span><span class="sxs-lookup"><span data-stu-id="34043-104">If you call methods on one of the [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) classes to write the data that is being monitored, you are essentially “hard-coding” the observation model into the application.</span></span> <span data-ttu-id="34043-105">如果您需要變更受監視的資料，就必須先讓應用程式離線，變更程式碼並重新編譯該應用程式，然後重新部署更新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="34043-105">If you need to change which data is being monitored, you will have to take the application offline, change the code, recompile the application, and then redeploy the updated application.</span></span>  
  
 <span data-ttu-id="34043-106">或者，您可以在 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) 類別上呼叫方法，檢測您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="34043-106">Alternatively, you can instrument your application by calling methods on the [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) class.</span></span> <span data-ttu-id="34043-107">[Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) 類別會參考組態檔來判斷要監視的事件及資料。</span><span class="sxs-lookup"><span data-stu-id="34043-107">The [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) class refers to a configuration file to determine which events and data to monitor.</span></span> <span data-ttu-id="34043-108">藉由使用 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) 類別，您可以檢測程式碼一次，然後藉由更新中繼資料來變更受監視的資料，而不需要將應用程式離線。</span><span class="sxs-lookup"><span data-stu-id="34043-108">By using the [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) class, you can instrument your code once, and then change the data that is being monitored by updating the metadata, without having to take the application offline.</span></span>  
  
## <a name="instrumenting-your-application-by-using-the-eventstream-object"></a><span data-ttu-id="34043-109">使用 EventStream 物件來檢測應用程式</span><span class="sxs-lookup"><span data-stu-id="34043-109">Instrumenting Your Application by Using the EventStream Object</span></span>  
 <span data-ttu-id="34043-110">當您要建置具有特定已知監視需求的專用應用程式時，這個方法比較簡單並且很適用。</span><span class="sxs-lookup"><span data-stu-id="34043-110">This approach is simpler and applies when you are building a dedicated application with specific, well-known monitoring requirements.</span></span> <span data-ttu-id="34043-111">在決定使用這個方法之前，您需要知道下列問題的答案：</span><span class="sxs-lookup"><span data-stu-id="34043-111">Before deciding to use this approach, you need to know the answers to the following questions:</span></span>  
  
-   <span data-ttu-id="34043-112">何謂 BAM 里程碑，以及在程式碼中執行其發生？</span><span class="sxs-lookup"><span data-stu-id="34043-112">What are the BAM milestones, and where in the code do they occur?</span></span>  
  
-   <span data-ttu-id="34043-113">要監視什麼資料？這些資料出現在程式碼中的時間和位置為何？</span><span class="sxs-lookup"><span data-stu-id="34043-113">What data will be monitored, and when and where in the code is that data available?</span></span>  
  
 <span data-ttu-id="34043-114">如果這些問題有任一答案可能會變更，您應該考慮改用 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx)物件來檢測應用程式。</span><span class="sxs-lookup"><span data-stu-id="34043-114">If the answer to either of these questions is likely to change, you should consider instrumenting your application by using the [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx)object instead.</span></span>  
  
 <span data-ttu-id="34043-115">依照這個「硬式編碼」方法進行時，您只要根據需要，在 [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx)、 [Microsoft.BizTalk.Bam.EventObservation.BufferedEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.bufferedeventstream.aspx)、 **MessagingEventStream** (在管線實作中) 或 **OrchestrationEventStream** (在協調流程實作中) 類別上呼叫方法即可。</span><span class="sxs-lookup"><span data-stu-id="34043-115">When you follow this “hard-coded” approach, you simply call methods on the [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx), [Microsoft.BizTalk.Bam.EventObservation.BufferedEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.bufferedeventstream.aspx), **MessagingEventStream** (from pipeline implementations) or **OrchestrationEventStream** (from orchestration implementations) class, depending on your requirements.</span></span>  
  
## <a name="instrumenting-your-application-by-using-the-baminterceptor-object"></a><span data-ttu-id="34043-116">使用 BAMInterceptor 物件來檢測應用程式</span><span class="sxs-lookup"><span data-stu-id="34043-116">Instrumenting Your Application by Using the BAMInterceptor Object</span></span>  
 <span data-ttu-id="34043-117">在下列情況中使用這個方法，效果較佳：</span><span class="sxs-lookup"><span data-stu-id="34043-117">This approach is better when:</span></span>  
  
-   <span data-ttu-id="34043-118">您需要平衡資料的可見性與應用程式的效能，並且想要控制在執行階段監視的資料。</span><span class="sxs-lookup"><span data-stu-id="34043-118">You need to balance visibility of data with performance of the application, and you want to be able to control the data that is monitored at run time.</span></span>  
  
-   <span data-ttu-id="34043-119">應用程式會處理大量的 XML 訊息，因此，任何資料都可能變成用於監視的重要資料。</span><span class="sxs-lookup"><span data-stu-id="34043-119">The application processes large XML messages, in which any data may eventually become important for monitoring.</span></span>  
  
-   <span data-ttu-id="34043-120">不接受停止應用程式再將程式碼變更成監視不同的資料。</span><span class="sxs-lookup"><span data-stu-id="34043-120">It is unacceptable to stop the application and change the code to monitor different data.</span></span>  
  
 <span data-ttu-id="34043-121">在這個方法中，您會藉由使用 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx)類別的方法，以一般方式檢測應用程式。</span><span class="sxs-lookup"><span data-stu-id="34043-121">In this approach, you instrument the application in a generic way by using the methods of the [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx)class.</span></span> <span data-ttu-id="34043-122">藉由傳遞不同的組態到攔截器，您就可以變更 BAM 監視的資料。</span><span class="sxs-lookup"><span data-stu-id="34043-122">By passing different configurations to the interceptor, you can change the data that BAM monitors.</span></span>  
  
 <span data-ttu-id="34043-123">您可以使用「追蹤設定檔編輯器」(TPE)，變更 BAM 從 BizTalk 協調流程收集的資料。</span><span class="sxs-lookup"><span data-stu-id="34043-123">You can use the Tracking Profile Editor (TPE) to change the data that BAM collects from a BizTalk orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34043-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34043-124">See Also</span></span>  
 <span data-ttu-id="34043-125">[使用活動](../core/using-an-activity.md) </span><span class="sxs-lookup"><span data-stu-id="34043-125">[Using an Activity](../core/using-an-activity.md) </span></span>  
 <span data-ttu-id="34043-126">[何謂 BAM 攔截器？](../core/what-is-the-bam-interceptor.md) </span><span class="sxs-lookup"><span data-stu-id="34043-126">[What Is the BAM Interceptor?](../core/what-is-the-bam-interceptor.md) </span></span>  
 [<span data-ttu-id="34043-127">BAM API （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="34043-127">BAM API (BizTalk Server Sample)</span></span>](../core/bam-api-biztalk-server-sample.md)