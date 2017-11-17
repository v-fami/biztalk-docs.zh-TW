---
title: "BAM 攔截器的一般問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a32145e2-1367-4576-9103-86c9182c11a8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 312bcd2ea1eaedcf44f02e2d3b702989095969d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="common-issues-with-the-bam-interceptors"></a><span data-ttu-id="59000-102">BAM 攔截器的常見問題</span><span class="sxs-lookup"><span data-stu-id="59000-102">Common Issues with the BAM Interceptors</span></span>
<span data-ttu-id="59000-103">這個主題討論以下使用 BAM 攔截器時可能常發生的問題：</span><span class="sxs-lookup"><span data-stu-id="59000-103">This topic discusses the following common problems that can arise when using BAM interceptors:</span></span>  
  
-   <span data-ttu-id="59000-104">分散式交易的相關 SQL 例外狀況</span><span class="sxs-lookup"><span data-stu-id="59000-104">SQL Exception relating to a distributed transaction</span></span>  
  
## <a name="you-receive-a-sql-exception-concerning-a-completed-distributed-transaction-or-a-transaction-descriptor"></a><span data-ttu-id="59000-105">您收到已完成之分散式交易或交易描述項相關的 SQL 例外狀況</span><span class="sxs-lookup"><span data-stu-id="59000-105">You Receive a SQL Exception Concerning a Completed Distributed Transaction or a Transaction Descriptor</span></span>  
 <span data-ttu-id="59000-106">執行 BAM Windows Communication Framework (WCF) 攔截器時，可能出現下列其中一個例外狀況：</span><span class="sxs-lookup"><span data-stu-id="59000-106">You may see one of the following exceptions when running the BAM Windows Communication Framework (WCF) interceptor:</span></span>  
  
-   <span data-ttu-id="59000-107">分散式交易完成。</span><span class="sxs-lookup"><span data-stu-id="59000-107">Distributed transaction completed.</span></span> <span data-ttu-id="59000-108">請在新的交易或是 NULL 交易中編列這個工作階段。</span><span class="sxs-lookup"><span data-stu-id="59000-108">Either enlist this session in a new transaction or the NULL transaction.</span></span>  
  
-   <span data-ttu-id="59000-109">不允許啟動新要求，因為要求應該具備有效的交易描述項。</span><span class="sxs-lookup"><span data-stu-id="59000-109">New request is not allowed to start because it should come with a valid transaction descriptor.</span></span>  
  
 <span data-ttu-id="59000-110">疑難排解此問題的建議如下：</span><span class="sxs-lookup"><span data-stu-id="59000-110">Some suggestions for troubleshooting this problem are:</span></span>  
  
-   <span data-ttu-id="59000-111">啟用 BAM 追蹤。</span><span class="sxs-lookup"><span data-stu-id="59000-111">Enable BAM tracing.</span></span> <span data-ttu-id="59000-112">此追蹤會包括包含錯誤根本原因的所有相關訊息。</span><span class="sxs-lookup"><span data-stu-id="59000-112">This trace will include all relevant messages including the root cause of the error.</span></span> <span data-ttu-id="59000-113">如需有關 BAM 追蹤的詳細資訊，請參閱[如何在 BAM 中啟用的追蹤](../core/how-to-enable-tracing-in-bam.md)。</span><span class="sxs-lookup"><span data-stu-id="59000-113">For more information about BAM tracing, see [How to Enable Tracing in BAM](../core/how-to-enable-tracing-in-bam.md).</span></span>  
  
-   <span data-ttu-id="59000-114">看見此分散式交易協調器 (DTC) 例外狀況時，請嘗試在沒有交易的情況下重新執行完全相同的實例。</span><span class="sxs-lookup"><span data-stu-id="59000-114">When you see this distributed transaction coordinator (DTC) exception, try to rerun exactly the same scenario without transactions.</span></span>  
  
-   <span data-ttu-id="59000-115">使用 SQL Server Profiler，並尋找追蹤內可能導致交易被中止的錯誤。</span><span class="sxs-lookup"><span data-stu-id="59000-115">Use SQL Server Profiler and look for errors in the trace that will cause the transaction to be aborted.</span></span>  
  
## <a name="you-receive-an-error-similar-to-interceptor-configuration-polling-interval-0-must-be-at-least-5-seconds-when-using-the-wcf-interceptor"></a><span data-ttu-id="59000-116">使用 WCF 攔截器時，您收到類似「攔截器組態輪詢間隔 '0' 必須至少為 '5' 秒」的錯誤。</span><span class="sxs-lookup"><span data-stu-id="59000-116">You receive an error similar to "interceptor configuration polling interval '0' must be at least '5' seconds" when using the WCF Interceptor</span></span>  
 <span data-ttu-id="59000-117">您並未在應用程式組態檔內明確提供攔截器組態輪詢間隔值，或您提供的值小於必要的最小值 5 秒時，就可能發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="59000-117">You may encounter this error when you do not explicitly provide an interceptor configuration polling interval value in the application configuration file, or when you provide a value but it is less than 5 seconds, the required minimum.</span></span>  
  
 <span data-ttu-id="59000-118">若要解決這個問題，請提供有效的 PollingIntervalSec 值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="59000-118">To fix the problem, provide a valid value for PollingIntervalSec as shown:</span></span>  
  
```  
<BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" PollingIntervalSec="1500" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="59000-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59000-119">See Also</span></span>  
 [<span data-ttu-id="59000-120">BAM 攔截器疑難排解</span><span class="sxs-lookup"><span data-stu-id="59000-120">Troubleshooting BAM Interceptors</span></span>](../core/troubleshooting-bam-interceptors.md)