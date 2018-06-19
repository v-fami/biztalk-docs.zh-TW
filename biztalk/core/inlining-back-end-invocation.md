---
title: 內嵌後端引動過程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MessageBox database, performance
- service solution tutorial, performance
- performance, in-line invocation
- Inline Invocation of Back-End Processes [service solutions], performance
- performance, MessageBox database
ms.assetid: 991d080f-a4cc-4f14-bab3-3b8b74636daf
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7300429e9f74abc7bc10569c653bdaa0a4c13b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257182"
---
# <a name="inlining-back-end-invocation"></a><span data-ttu-id="ba6b8-102">內嵌後端叫用</span><span class="sxs-lookup"><span data-stu-id="ba6b8-102">Inlining Back-end Invocation</span></span>
<span data-ttu-id="ba6b8-103">完整解決方案的內嵌呼叫版本可提供最快速的處理次數。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-103">The inline call version, of the full solutions, provides the fastest processing times.</span></span> <span data-ttu-id="ba6b8-104">內嵌版本消除了對 MessageBox 資料庫中後端系統持續傳送要求及取得回應的負擔。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-104">The inline version eliminates the overhead of persisting the request and response messages to and from the backend systems in the MessageBox database.</span></span> <span data-ttu-id="ba6b8-105">在配接器版本中，訊息會從傳送協調流程到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-105">In the adapter version, the message goes from the sending orchestration to the MessageBox.</span></span> <span data-ttu-id="ba6b8-106">執行配接器的主控件會取出訊息，並透過訊息再次發佈到 MessageBox 的方式，將訊息傳送到後端程序。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-106">The host running the adapter picks up the message, and sends the message to the back-end process by again posting it to the message box.</span></span>  
  
 <span data-ttu-id="ba6b8-107">內嵌的效率會犧牲協調流程直接與後端系統傳輸通訊協定的繫結。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-107">The efficiency of inlining comes at a cost of binding the orchestration directly to the transport protocols of the back-end systems.</span></span> <span data-ttu-id="ba6b8-108">在內嵌版本中，協調流程不是透過邏輯連接埠進行通訊，而是透過三個自訂組件呼叫後端系統。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-108">In the inline version, rather than communicating through logical ports, the orchestration calls the back-end systems through three custom assemblies.</span></span> <span data-ttu-id="ba6b8-109">若後端系統傳輸變更，則必須重新撰寫並重新編譯組件。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-109">If a back-end system transport changes, an assembly must be rewritten and recompiled.</span></span> <span data-ttu-id="ba6b8-110">下表描述組件及其功能：</span><span class="sxs-lookup"><span data-stu-id="ba6b8-110">The following table describes the assemblies and their function:</span></span>  
  
|<span data-ttu-id="ba6b8-111">組件名稱</span><span class="sxs-lookup"><span data-stu-id="ba6b8-111">Assembly Name</span></span>|<span data-ttu-id="ba6b8-112">後端連接</span><span class="sxs-lookup"><span data-stu-id="ba6b8-112">Back-end Connection</span></span>|  
|-------------------|--------------------------|  
|<span data-ttu-id="ba6b8-113">Microsoft.Samples.BizTalk.WoodgroveBank.PaymentTrackerCall</span><span class="sxs-lookup"><span data-stu-id="ba6b8-113">Microsoft.Samples.BizTalk.WoodgroveBank.PaymentTrackerCall</span></span>|<span data-ttu-id="ba6b8-114">使用 MQSeries**取得**和**放**訊息功能。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-114">Uses MQSeries **get** and **put** message functions.</span></span>|  
|<span data-ttu-id="ba6b8-115">Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactionsCall</span><span class="sxs-lookup"><span data-stu-id="ba6b8-115">Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactionsCall</span></span>|<span data-ttu-id="ba6b8-116">叫用交易系統的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-116">Invokes the Web service for the transaction system.</span></span>|  
|<span data-ttu-id="ba6b8-117">Microsoft.Samples.BizTalk.WoodgroveBank.SAPCall</span><span class="sxs-lookup"><span data-stu-id="ba6b8-117">Microsoft.Samples.BizTalk.WoodgroveBank.SAPCall</span></span>|<span data-ttu-id="ba6b8-118">呼叫模擬 SAP 的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="ba6b8-118">Calls the web services simulating SAP.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba6b8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba6b8-119">See Also</span></span>  
 <span data-ttu-id="ba6b8-120">[實作會反白顯示的服務導向解決方案](../core/implementation-highlights-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="ba6b8-120">[Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="ba6b8-121">[開發服務導向解決方案](../core/developing-a-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="ba6b8-121">[Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="ba6b8-122">[轉譯模式的服務導向解決方案](../core/translating-the-patterns-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="ba6b8-122">[Translating the Patterns of the Service Oriented Solution](../core/translating-the-patterns-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="ba6b8-123">監控服務導向 BAM 解決方案</span><span class="sxs-lookup"><span data-stu-id="ba6b8-123">Monitoring the Service Oriented Solution with BAM</span></span>](../core/monitoring-the-service-oriented-solution-with-bam.md)