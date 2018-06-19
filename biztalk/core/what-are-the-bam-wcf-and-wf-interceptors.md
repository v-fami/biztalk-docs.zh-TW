---
title: 何謂 BAM WCF 和 WF 攔截器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 198bfdc9-86ff-4017-b65f-19616deeb9f4
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c819d219a9796b485434101ee1c2f2d4be136ae0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288886"
---
# <a name="what-are-the-bam-wcf-and-wf-interceptors"></a><span data-ttu-id="a9bee-103">何謂 BAM WCF 和 WF 攔截器？</span><span class="sxs-lookup"><span data-stu-id="a9bee-103">What Are the BAM WCF and WF Interceptors?</span></span>
<span data-ttu-id="a9bee-104">商務活動監控 (Business Activity Monitoring，BAM) 是一組工具、API 和服務的集合，可以讓您管理彙總、警示與設定檔，並進行自動化的程序來傳送事件，以監控相關的商務計量。</span><span class="sxs-lookup"><span data-stu-id="a9bee-104">Business Activity Monitoring (BAM) is a collection of tools, APIs, and services that allow you to manage aggregations, alerts, and profiles, and to instrument automated processes to send events to monitor relevant business metrics.</span></span> <span data-ttu-id="a9bee-105">這些功能結合在一起後，可以為商務程序提供了端對端的可見性，而且可以讓您持續掌握商務程序的狀態和結果。</span><span class="sxs-lookup"><span data-stu-id="a9bee-105">Together, these provide end-to-end visibility into business processes and enable you to stay abreast of business process status and results.</span></span>  
  
 <span data-ttu-id="a9bee-106">BAM 攔截器將相同的功能擴充至 Windows Workflow Foundation (WF)、Windows Communication Foundation (WCF) 及其他執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="a9bee-106">BAM interceptors extend this same functionality into Windows Workflow Foundation (WF), Windows Communication Foundation (WCF), and other runtime environments.</span></span> <span data-ttu-id="a9bee-107">藉由使用 BAM 攔截器，您可以追蹤商務程序而不需要重新編譯 WF 或 WCF 解決方案。只要透過組態檔即可完成整合。</span><span class="sxs-lookup"><span data-stu-id="a9bee-107">By using a BAM interceptor, you can track your business processes without recompiling your WF or WCF solution—integration is done through a configuration file.</span></span>  
  
 <span data-ttu-id="a9bee-108">在專案中使用 BAM WF 或 WCF 攔截器可以讓您：</span><span class="sxs-lookup"><span data-stu-id="a9bee-108">By using the BAM WF or WCF interceptor in your project, you can:</span></span>  
  
-   <span data-ttu-id="a9bee-109">使用 BAM 入口網站來檢視在 WF 或 WCF 應用程式中執行之商務程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="a9bee-109">Use the BAM portal to view information about the business processes running in your WF or WCF application.</span></span>  
  
-   <span data-ttu-id="a9bee-110">使用 BAM 功能而不需要將其他程式碼加入應用程式。</span><span class="sxs-lookup"><span data-stu-id="a9bee-110">Use BAM functionality without adding additional code to your application.</span></span>  
  
-   <span data-ttu-id="a9bee-111">使用熟悉的 BizTalk Server 工具和公用程式來部署解決方案。</span><span class="sxs-lookup"><span data-stu-id="a9bee-111">Deploy your solution using familiar BizTalk Server tools and utilities.</span></span>  
  
-   <span data-ttu-id="a9bee-112">針對現有和全新的 WF 與 WCF 應用程式，利用您現有的 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="a9bee-112">Leverage your existing BizTalk Server environment for existing and new WF and WCF applications.</span></span>  
  
## <a name="interceptor-components"></a><span data-ttu-id="a9bee-113">攔截器元件</span><span class="sxs-lookup"><span data-stu-id="a9bee-113">Interceptor Components</span></span>  
 <span data-ttu-id="a9bee-114">每個 BAM 攔截器的核心都有 Common Interceptor Foundation，它是一組元件，提供了針對異質環境建置自訂攔截器的基礎。</span><span class="sxs-lookup"><span data-stu-id="a9bee-114">At the core of each BAM interceptor is the Common Interceptor Foundation, a set of components that provide the foundation for building custom interceptors for heterogeneous environments.</span></span> <span data-ttu-id="a9bee-115">Common Interceptor Foundation 包含下列共用元件：</span><span class="sxs-lookup"><span data-stu-id="a9bee-115">The Common Interceptor Foundation contains the following shared components:</span></span>  
  
-   <span data-ttu-id="a9bee-116">**bm.exe**，BAM 部署公用程式的增強型的版本擴充為可修改攔截器組態，包括新增、 移除、 更新及清單功能。</span><span class="sxs-lookup"><span data-stu-id="a9bee-116">**bm.exe**, an enhanced version of the BAM deployment utility extended to modify interceptor configurations including add, remove, update, and list functionality.</span></span>  
  
-   <span data-ttu-id="a9bee-117">**CommonInterceptorConfiguration.xsd**，Common Interceptor Foundation 組態 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="a9bee-117">**CommonInterceptorConfiguration.xsd**, the Common Interceptor Foundation configuration XML schema.</span></span> <span data-ttu-id="a9bee-118">所有的攔截器組態至少都必須根據這個結構描述進行驗證。</span><span class="sxs-lookup"><span data-stu-id="a9bee-118">At minimum, all interceptor configurations must validate against this schema.</span></span>  
  
## <a name="windows-workflow-foundation-wf-interceptor"></a><span data-ttu-id="a9bee-119">Windows Workflow Foundation (WF) 攔截器</span><span class="sxs-lookup"><span data-stu-id="a9bee-119">Windows Workflow Foundation (WF) Interceptor</span></span>  
 <span data-ttu-id="a9bee-120">Windows Workflow Foundation 攔截器可讓您將 BAM 追蹤功能直接新增到全新和現有的 WF 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="a9bee-120">The Windows Workflow Foundation interceptor enables you to transparently add BAM tracking functionality to new and existing WF applications.</span></span> <span data-ttu-id="a9bee-121">在將攔截器組態部署到 BAM 主要匯入資料庫，而且 WF 應用程式的每個執行個體也已設定為載入 BAM WF 攔截器之後，工作流程資料便會寫入到 BAM，而不需要額外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a9bee-121">After the interceptor configuration has been deployed to the BAM Primary Import database and each instance of the WF application has been configured to load the BAM WF Interceptor, workflow data will be written to BAM with no additional code.</span></span> <span data-ttu-id="a9bee-122">WF 攔截器提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="a9bee-122">The WF interceptor provides the following functionality:</span></span>  
  
-   <span data-ttu-id="a9bee-123">插入現有的 WF 應用程式，而不需要變更或重新編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="a9bee-123">Plugs into existing WF applications without requiring code changes or recompilation.</span></span>  
  
-   <span data-ttu-id="a9bee-124">啟用變更組態檔的執行階段偵測和支援功能。</span><span class="sxs-lookup"><span data-stu-id="a9bee-124">Enables run-time detection and support for changed configuration files.</span></span> <span data-ttu-id="a9bee-125">如果偵測到攔截器組態檔的新版本，新的工作流程執行個體將會使用新組態，但是舊的工作流程執行個體仍會使用舊的組態來完成。</span><span class="sxs-lookup"><span data-stu-id="a9bee-125">If a new version of an interceptor configuration file is detected, new workflow instances will use the new configuration while old workflow instances will complete using the old configuration.</span></span>  
  
-   <span data-ttu-id="a9bee-126">支援交易。</span><span class="sxs-lookup"><span data-stu-id="a9bee-126">Supports transactions.</span></span> <span data-ttu-id="a9bee-127">WF 攔截器會保存追蹤的項目，保存的方式在交易上與 WF 交易一致。</span><span class="sxs-lookup"><span data-stu-id="a9bee-127">The WF interceptor persists tracked items in a transactionally consistent way with WF transactions.</span></span> <span data-ttu-id="a9bee-128">只有在 WF 交易和攔截器交易順利完成時，才會保存追蹤的項目。</span><span class="sxs-lookup"><span data-stu-id="a9bee-128">Tracked items are only persisted when the WF transaction and the interceptor trasaction complete successfully.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9bee-129">Windows Workflow 攔截器不支援在追蹤和保存服務中都使用相同連線的 SharedConnectionWorkflowCommitWorkBatchService。</span><span class="sxs-lookup"><span data-stu-id="a9bee-129">The Windows Workflow interceptor does not support SharedConnectionWorkflowCommitWorkBatchService which uses the same SQL connection for both the tracking and persistence services.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9bee-130">在 BizTalk Server 中 Windows Workflow Foundation (WF) 攔截器不適用於.NET Framework 4 中的新 WF 引擎。</span><span class="sxs-lookup"><span data-stu-id="a9bee-130">In BizTalk Server, the Windows Workflow Foundation (WF) interceptor will not work with the new WF engine in .NET Framework 4.</span></span> <span data-ttu-id="a9bee-131">WF 攔截器會繼續在.NET Framework 3.5 SP2 中運作。</span><span class="sxs-lookup"><span data-stu-id="a9bee-131">The WF interceptor will continue to work in .NET Framework 3.5 SP2.</span></span>  
  
## <a name="windows-communication-foundation-wcf-interceptor"></a><span data-ttu-id="a9bee-132">Windows Communication Foundation (WCF) 攔截器</span><span class="sxs-lookup"><span data-stu-id="a9bee-132">Windows Communication Foundation (WCF) Interceptor</span></span>  
 <span data-ttu-id="a9bee-133">Windows Communication Foundation 擱截器為 WCF 應用程式提供了 BAM 追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="a9bee-133">The Windows Communication Foundation interceptor provides BAM tracking functionality to your WCF applications.</span></span> <span data-ttu-id="a9bee-134">這個攔截器提供的功能包括：</span><span class="sxs-lookup"><span data-stu-id="a9bee-134">It provides the following functionality:</span></span>  
  
-   <span data-ttu-id="a9bee-135">插入現有的 WCF 應用程式，而不需要變更或重新編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="a9bee-135">Plugs into existing WCF applications without requiring code changes or recompilation.</span></span>  
  
-   <span data-ttu-id="a9bee-136">追蹤 WCF 服務呼叫中包含的訊息。</span><span class="sxs-lookup"><span data-stu-id="a9bee-136">Tracks messages contained in WCF service calls.</span></span>  
  
-   <span data-ttu-id="a9bee-137">從 WCF 服務呼叫的訊息中追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="a9bee-137">Tracks information from messages in WCF service calls.</span></span>  
  
-   <span data-ttu-id="a9bee-138">參與來自用戶端的交易，或是針對交易服務呼叫從內部啟動的交易。</span><span class="sxs-lookup"><span data-stu-id="a9bee-138">Participates in transactions flowed from the client or initiated internally for transacted service calls.</span></span>