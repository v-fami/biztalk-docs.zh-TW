---
title: "檢測的高效能的 BizTalk 解決方案的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd16ea1e-055a-429b-912f-bff2b91f0fdb
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ef6f243f894071aebb0089f063ed0242ee09d9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instrumentation-best-practices-for-high-performance-biztalk-solutions"></a><span data-ttu-id="96702-102">檢測的高效能的 BizTalk 解決方案的最佳作法</span><span class="sxs-lookup"><span data-stu-id="96702-102">Instrumentation Best Practices for High Performance BizTalk Solutions</span></span>
<span data-ttu-id="96702-103">若要下載這份文件的複本，請移至[http://go.microsoft.com/fwlink/?LinkId=205874](http://go.microsoft.com/fwlink/?LinkId=205874)。</span><span class="sxs-lookup"><span data-stu-id="96702-103">To download a copy of this paper, go to [http://go.microsoft.com/fwlink/?LinkId=205874](http://go.microsoft.com/fwlink/?LinkId=205874).</span></span>  
  
 <span data-ttu-id="96702-104">**發行日期：** 2010 年 11 月</span><span class="sxs-lookup"><span data-stu-id="96702-104">**Published:** November 2010</span></span>  
  
 <span data-ttu-id="96702-105">**作者：** Valery Mizonov，Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="96702-105">**Author:** Valery Mizonov, Microsoft Corporation</span></span>  
  
 <span data-ttu-id="96702-106">**審稿者：**</span><span class="sxs-lookup"><span data-stu-id="96702-106">**Reviewed By:**</span></span>  
  
-   <span data-ttu-id="96702-107">Mark Simms，Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="96702-107">Mark Simms, Microsoft Corporation</span></span>  
  
-   <span data-ttu-id="96702-108">Jayanthi Sampathkumar，Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="96702-108">Jayanthi Sampathkumar, Microsoft Corporation</span></span>  
  
-   <span data-ttu-id="96702-109">Krish Srinivasan，Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="96702-109">Krish Srinivasan, Microsoft Corporation</span></span>  
  
 <span data-ttu-id="96702-110">**適用於：** Microsoft BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="96702-110">**Applies To:** Microsoft BizTalk Server</span></span>  
  
 <span data-ttu-id="96702-111">**摘要：**傳統的檢測 BizTalk 解決方案的方式可能永遠無法從效能觀點來看最有效。</span><span class="sxs-lookup"><span data-stu-id="96702-111">**Summary:** The traditional ways of instrumenting BizTalk solutions may not always be the most effective from a performance standpoint.</span></span> <span data-ttu-id="96702-112">常用的檢測和追蹤元件利用 Win32 偵錯 Api 可能會介紹潛在的瓶頸，並會變成負責多執行緒在壓力下執行的 BizTalk 應用程式中的效能降低。</span><span class="sxs-lookup"><span data-stu-id="96702-112">The commonly used instrumentation and tracing components leveraging the Win32 Debugging APIs may introduce a potential bottleneck and become responsible for performance degradations in multi-threaded BizTalk applications running under stress.</span></span>  
  
 <span data-ttu-id="96702-113">從另一端，來源的程式碼檢測會提供很大的可見性的應用程式行為，而且有助於減少整體的疑難排解工作。</span><span class="sxs-lookup"><span data-stu-id="96702-113">From the other side, source code instrumentation delivers a great degree of visibility into the application behavior and helps reduce the overall troubleshooting efforts.</span></span> <span data-ttu-id="96702-114">因此，基本上是新的方法檢測的高效能 BizTalk 解決方案變得少很重要，以啟用不會造成干擾的方式，使用幾乎任何額外負荷，不會影響收集的豐富且詳細的診斷資訊在應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="96702-114">Consequently, a fundamentally new approach to instrumenting high performance BizTalk solutions has become crucially important to enable collecting the rich and detailed diagnostic information in a non-intrusive manner with virtually no overhead and no impact on the application performance.</span></span>  
  
 <span data-ttu-id="96702-115">[Windows Server AppFabric 客戶諮詢團隊](http://blogs.msdn.com/appfabriccat)microsoft 社群提供已驗證的最佳做法的目標是協助 BizTalk 開發人員擴充與高效能檢測解決方案在內部採用許多 Microsoft 產品。</span><span class="sxs-lookup"><span data-stu-id="96702-115">The [Windows Server AppFabric Customer Advisory Team](http://blogs.msdn.com/appfabriccat) at Microsoft aimed to provide the community with validated best practices to help BizTalk developers enrich their solutions with the high-performance instrumentation internally adopted by many Microsoft products.</span></span> <span data-ttu-id="96702-116">這些最佳作法已反映在可重複使用的架構的 BizTalk 開發人員可以輕鬆地插入並採用它們自己的實作中的表單。</span><span class="sxs-lookup"><span data-stu-id="96702-116">These best practices have been reflected in the form of a reusable framework which BizTalk developers can easily plug in and adopt in their own implementations.</span></span>  
  
 <span data-ttu-id="96702-117">您可以下載的完整副本[檢測的高效能的 BizTalk 解決方案的最佳作法](http://go.microsoft.com/fwlink/?LinkId=205874)(http://go.microsoft.com/fwlink/?LinkId=205874) 在 Microsoft Download Center 上。</span><span class="sxs-lookup"><span data-stu-id="96702-117">You can download a complete copy of [Instrumentation Best Practices for High Performance BizTalk Solutions](http://go.microsoft.com/fwlink/?LinkId=205874) (http://go.microsoft.com/fwlink/?LinkId=205874) on the Microsoft Download Center.</span></span>