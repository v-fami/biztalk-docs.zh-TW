---
title: "在 ESB 例外狀況管理架構的設計 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfc2688c-c01c-4244-9e35-3d482135d8b7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 089942c8b531575c157c0037777e85fe6d8608a7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="design-of-the-esb-exception-management-framework"></a><span data-ttu-id="2e460-102">在 ESB 例外狀況管理架構的設計</span><span class="sxs-lookup"><span data-stu-id="2e460-102">Design of the ESB Exception Management Framework</span></span>
<span data-ttu-id="2e460-103">一致且可重複使用管理例外狀況的模式是核心考量任何開發專案。這些資訊可協助最大化可維護性，並簡化支援應用程式部署之後。</span><span class="sxs-lookup"><span data-stu-id="2e460-103">Consistent and re-usable patterns for managing exceptions are a core consideration of any development project; they help to maximize maintainability and make it easier to support the application after deployment.</span></span>  
  
 <span data-ttu-id="2e460-104">典型的 BizTalk 應用程式可能會使用 BizTalk 傳訊功能、 選擇性地開始處理協調流程、 呼叫商務規則引擎、 數的特定業務 (LOB) 或企業資源規劃 (ERP) 系統互動以及傳回個別的協力廠商系統的回應。</span><span class="sxs-lookup"><span data-stu-id="2e460-104">A typical BizTalk application might use the BizTalk messaging features, optionally start processing an orchestration, call the Business Rule Engine, interact with several line-of-business (LOB) or enterprise resource planning (ERP) systems, and return a response to a separate third-party system.</span></span> <span data-ttu-id="2e460-105">此外，這些元件，包括 BizTalk 子系統的執行階段位置可能位於分散於整個目前環境的一或多個伺服器上。</span><span class="sxs-lookup"><span data-stu-id="2e460-105">In addition, the run-time location of these components, including the BizTalk subsystems, may reside on one or more servers distributed throughout the current environment.</span></span> <span data-ttu-id="2e460-106">這是常見的案例，並且需要系統支援攔截和報告例外狀況，可能會發生的任何 ESB 或 BizTalk 分離子系統，或在各種協力廠商 LOB 系統中，每一個都有它自己的例外狀況處理條件約束。</span><span class="sxs-lookup"><span data-stu-id="2e460-106">This is a typical scenario and requires the system to support catching and reporting exceptions that may occur in any of the ESB or BizTalk decoupled subsystems or in the various third-party LOB systems, each of which has its own exception handling constraints.</span></span> <span data-ttu-id="2e460-107">例如，大型主機可能會拒絕正常處理期間，從網站傳送訂單網站必須修正這個錯誤，並通知使用者。</span><span class="sxs-lookup"><span data-stu-id="2e460-107">For example, the mainframe may reject an order sent from a Web site during a normal processing cycle; the Web site must compensate for this error and notify the user.</span></span>  
  
 <span data-ttu-id="2e460-108">ESB 應用程式的複雜性和其環境中，由於一致的應用程式例外狀況管理方案的開發應該只限下列常見的設計目標：</span><span class="sxs-lookup"><span data-stu-id="2e460-108">Because of the complexity of ESB applications and their environment, development of a consistent solution for application exception management should embody the following common design goals:</span></span>  
  
-   <span data-ttu-id="2e460-109">提供標準化的方法來偵測及 BizTalk Server 環境中發生的例外狀況處理 (亦即，傳訊與協調流程子系統中)。</span><span class="sxs-lookup"><span data-stu-id="2e460-109">Provide a standardized approach for detecting and handling exceptions that occur in the BizTalk Server environment (that is, in the messaging and orchestration subsystems).</span></span>  
  
-   <span data-ttu-id="2e460-110">提供一般模式，好讓自動化程序來回應，以及管理應用程式例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2e460-110">Provide common patterns that allow automated processes to react to and manage application exceptions.</span></span>  
  
-   <span data-ttu-id="2e460-111">提供的鬆散偶合的例外狀況管理模式，可促進重複使用。</span><span class="sxs-lookup"><span data-stu-id="2e460-111">Provide a loosely coupled exception management pattern that facilitates reuse.</span></span>  
  
-   <span data-ttu-id="2e460-112">應用程式例外狀況，其可用的訊息狀態可套用至任何 BizTalk 子系統提供常見的報告機制。</span><span class="sxs-lookup"><span data-stu-id="2e460-112">Provide a common reporting mechanism for application exceptions and their available message states that can apply to any BizTalk subsystem.</span></span>  
  
 <span data-ttu-id="2e460-113">若要了解為什麼[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供一個機制，自訂錯誤，也就是在例外狀況管理架構，以及它的運作方式，就必須了解可在 BizTalk Server 和為什麼這些功能不是完整的例外狀況管理功能能夠達到上述的設計目標。</span><span class="sxs-lookup"><span data-stu-id="2e460-113">To understand why the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides a custom error mechanism, namely the Exception Management Framework, and how it works, it is necessary to understand the exception management features available in BizTalk Server and why these features are not fully capable of meeting the preceding design goals.</span></span>  
  
## <a name="biztalk-server-exception-reporting"></a><span data-ttu-id="2e460-114">BizTalk Server 例外狀況報告</span><span class="sxs-lookup"><span data-stu-id="2e460-114">BizTalk Server Exception Reporting</span></span>  
 <span data-ttu-id="2e460-115">BizTalk Server 支援下列的例外狀況處理和報告機制：</span><span class="sxs-lookup"><span data-stu-id="2e460-115">BizTalk Server supports the following exception handling and reporting mechanisms:</span></span>  
  
-   <span data-ttu-id="2e460-116">失敗的訊息路由</span><span class="sxs-lookup"><span data-stu-id="2e460-116">Failed Message Routing</span></span>  
  
-   <span data-ttu-id="2e460-117">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="2e460-117">BizTalk Server Administration Console</span></span>  
  
-   <span data-ttu-id="2e460-118">Microsoft 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="2e460-118">Microsoft Event Log</span></span>  
  
-   <span data-ttu-id="2e460-119">自訂開發選項</span><span class="sxs-lookup"><span data-stu-id="2e460-119">Custom development options</span></span>  
  
 <span data-ttu-id="2e460-120">根據預設，BizTalk Server 例外狀況處理功能依賴許多操作人員介入。</span><span class="sxs-lookup"><span data-stu-id="2e460-120">By default, BizTalk Server's capabilities for handling exceptions rely a great deal on operator intervention.</span></span> <span data-ttu-id="2e460-121">例如，假設當使用者送出至 BizTalk Server 會在驗證階段期間發生例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="2e460-121">For example, consider the situation where a user submits a message to BizTalk Server that causes an exception during the validation stage.</span></span> <span data-ttu-id="2e460-122">根據預設，訊息會發佈到 Messagebox 資料庫，則會路由傳送到擱置佇列。</span><span class="sxs-lookup"><span data-stu-id="2e460-122">By default, the message is published to the Message Box database, where it is routed to a suspended queue.</span></span> <span data-ttu-id="2e460-123">這表示，操作員必須下列作業：</span><span class="sxs-lookup"><span data-stu-id="2e460-123">This means that an operator must do the following:</span></span>  
  
-   <span data-ttu-id="2e460-124">獨立偵測到發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2e460-124">Independently detect that an exception occurred.</span></span>  
  
-   <span data-ttu-id="2e460-125">手動儲存使用 BizTalk Server 管理主控台磁碟失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="2e460-125">Manually save the failed message to disk using the BizTalk Server Administration Console.</span></span>  
  
-   <span data-ttu-id="2e460-126">手動編輯和更正的訊息，並重新送出至系統。</span><span class="sxs-lookup"><span data-stu-id="2e460-126">Manually edit and correct the message and re-submit it to the system.</span></span> <span data-ttu-id="2e460-127">在某些情況下，此程序可能會發生遺失的重要內容資訊。</span><span class="sxs-lookup"><span data-stu-id="2e460-127">In some instances, this process has the potential for losing important context information.</span></span>  
  
 <span data-ttu-id="2e460-128">若要解決這些問題，BizTalk Server 會提供失敗訊息路由的機制。</span><span class="sxs-lookup"><span data-stu-id="2e460-128">To resolve these issues, BizTalk Server provides the Failed Message Routing mechanism.</span></span> <span data-ttu-id="2e460-129">開發人員和管理員可以使用這個來建立協調流程或傳訊的傳送埠設定為訂閱傳訊子系統中發生任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2e460-129">Developers and administrators can use this to create orchestration processes or messaging send ports configured to subscribe to any exceptions that occur in the messaging subsystem.</span></span> <span data-ttu-id="2e460-130">這可提供自動化的錯誤偵測與路由機制，會保留原始訊息的狀態，並解決偵測到例外狀況的問題。</span><span class="sxs-lookup"><span data-stu-id="2e460-130">This provides an automated error-detection and routing mechanism that preserves the original message state and solves the problem of detecting exceptions.</span></span>  
  
 <span data-ttu-id="2e460-131">協調流程未提供自動的失敗的訊息路由，因為開發人員必須負責錯誤例外狀況處理常式區塊新增到協調流程範圍圖形。</span><span class="sxs-lookup"><span data-stu-id="2e460-131">Because automatic failed message routing is not provided for orchestration processes, the developer must account for errors by adding exception handler blocks to orchestration scope shapes.</span></span> <span data-ttu-id="2e460-132">使用此解決方案中，每個協調流程可以有它自己的例外狀況處理，但沒有任何機制可重複使用例外狀況處理跨多個協調流程的功能。</span><span class="sxs-lookup"><span data-stu-id="2e460-132">With this solution, each orchestration can have its own exception handling, but there is no mechanism for reusing exception handling functionality across multiple orchestrations.</span></span>  
  
 <span data-ttu-id="2e460-133">這表示，現在有兩個非常不同的方式在其中訊息的例外狀況處理與在 BizTalk Server 系統中，管理，以及哪一個協調流程中處理例外狀況的第三個方法。</span><span class="sxs-lookup"><span data-stu-id="2e460-133">This means that there are now two very different ways in which messaging exceptions are processed and managed in a BizTalk Server system, and a third way in which orchestration exceptions are processed.</span></span> <span data-ttu-id="2e460-134">因此，開發人員必須自訂的例外狀況處理機制，以符合自己的需求，如果他們想要實作符合本節中稍早所述之需求的系統。</span><span class="sxs-lookup"><span data-stu-id="2e460-134">Therefore, developers must customize the exception handling mechanism to suit their own requirements if they want to implement a system that matches the requirements described earlier in this section.</span></span>  
  
## <a name="biztalk-server-administration-console"></a><span data-ttu-id="2e460-135">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="2e460-135">BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="2e460-136">BizTalk Server 管理主控台提供一組群組概觀頁面，稱為 BizTalk 群組的中樞。</span><span class="sxs-lookup"><span data-stu-id="2e460-136">The BizTalk Server Administration Console provides a set of Group Overview pages, referred to as the BizTalk Group Hub.</span></span> <span data-ttu-id="2e460-137">使用這些頁面時，系統管理員可以查詢擱置的訊息和例外狀況，依應用程式、 服務名稱、 錯誤代碼或 URI，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="2e460-137">Using these pages, administrators can query for suspended messages and exceptions grouped by application, service name, error code, or URI, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="2e460-138">![系統管理員主控台](../esb-toolkit/media/ch4-adminconsole.gif "第 4 章第 AdminConsole")</span><span class="sxs-lookup"><span data-stu-id="2e460-138">![Admin Console](../esb-toolkit/media/ch4-adminconsole.gif "Ch4-AdminConsole")</span></span>  
  
 <span data-ttu-id="2e460-139">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="2e460-139">**Figure 1**</span></span>  
  
 <span data-ttu-id="2e460-140">**[BizTalk Server 管理主控台群組概觀] 頁面**</span><span class="sxs-lookup"><span data-stu-id="2e460-140">**The BizTalk Server Administration Console Group Overview pages**</span></span>  
  
 <span data-ttu-id="2e460-141">雖然 [群組概觀] 功能提供了通用使用者介面來檢視例外狀況，但是這些檢視會受限於 「 即時 」 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e460-141">Although the Group Overview feature provides a common user interface to view exceptions, the views are limited to "live" service instances.</span></span> <span data-ttu-id="2e460-142">檢查狀態可以是麻煩的工作，因為系統管理員必須向下鑽研至每個項目樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2e460-142">Examining the state can be a cumbersome task because administrators must drill down through the tree to each item.</span></span> <span data-ttu-id="2e460-143">此外，許多其他因素會限制 BizTalk Server 管理主控台功能做為應用程式例外狀況報告工具：</span><span class="sxs-lookup"><span data-stu-id="2e460-143">In addition, several other factors limit the BizTalk Server Administration Console capabilities as an application exception-reporting tool:</span></span>  
  
-   <span data-ttu-id="2e460-144">沒有任何功能採礦的商業智慧資料。</span><span class="sxs-lookup"><span data-stu-id="2e460-144">There is no capability for mining the data for business intelligence.</span></span> <span data-ttu-id="2e460-145">比方說，您無法查詢的每月為基礎的最差違規應用程式，或檢查應用程式例外狀況的每季趨勢。</span><span class="sxs-lookup"><span data-stu-id="2e460-145">For example, you cannot query for the worst offending applications on a monthly basis or examine quarterly trends for application exceptions.</span></span>  
  
-   <span data-ttu-id="2e460-146">企業可能會需要某些應用程式例外狀況發生時或達到特定的閾值時發出警示，但沒有任何設備，訂閱這些類型的例外狀況事件。</span><span class="sxs-lookup"><span data-stu-id="2e460-146">The business may require alerts to be raised when certain application exceptions occur or when reaching specific thresholds, but there is no facility to subscribe to these types of exception events.</span></span>  
  
-   <span data-ttu-id="2e460-147">Microsoft Management Console (MMC) 的管理主控台會使用為其使用者介面 (UI) 機制不是理想的介面，而且它不一定方便在生產環境中存取。</span><span class="sxs-lookup"><span data-stu-id="2e460-147">The Microsoft Management Console (MMC) that the Administration Console uses as its user interface (UI) mechanism is not an ideal interface, and it is not always convenient to access in production environments.</span></span> <span data-ttu-id="2e460-148">最小值，會要求使用者必須是 「 BizTalk 操作員 」 角色; 的成員而，在生產環境中存取 MMC 也通常僅能透過終端機伺服器。</span><span class="sxs-lookup"><span data-stu-id="2e460-148">At minimum, it requires users to be members of the BizTalk Operators role; and, in production environments, access to the MMC is usually only possible through Terminal Server.</span></span>  
  
-   <span data-ttu-id="2e460-149">主控台會顯示只有未處理例外狀況 （已擱置的服務執行個體）。</span><span class="sxs-lookup"><span data-stu-id="2e460-149">The console displays only unhandled exceptions (suspended service instances).</span></span> <span data-ttu-id="2e460-150">如果開發人員可以處理協調流程中的例外狀況，讓協調流程，一般來說，完成的例外狀況資訊會永遠不會出現在 [管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="2e460-150">If the developer handles the exception in the orchestration, allowing the orchestration to complete normally, the exception information will never appear in the Administration Console.</span></span>  
  
 <span data-ttu-id="2e460-151">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]透過 ESB 無法協調流程的例外狀況路由機制會解決這些限制。</span><span class="sxs-lookup"><span data-stu-id="2e460-151">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] addresses these limitations through the ESB Failed Orchestration Exception Routing mechanism.</span></span> <span data-ttu-id="2e460-152">這會非常接近 BizTalk Server 的失敗訊息路由機制。</span><span class="sxs-lookup"><span data-stu-id="2e460-152">This closely resembles the Failed Message Routing mechanism of BizTalk Server.</span></span> <span data-ttu-id="2e460-153">此外，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]訂閱從 ESB 無法協調流程的例外狀況路由的機制和失敗訊息路由機制產生的訊息的傳送埠中包含的管線元件，然後加以正規化。</span><span class="sxs-lookup"><span data-stu-id="2e460-153">In addition, the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes a pipeline component in a send port that subscribes to messages generated from both the ESB Failed Orchestration Exception Routing mechanism and the Failed Message Routing mechanism and normalizes them.</span></span>  
  
 <span data-ttu-id="2e460-154">在 ESB 例外狀況管理架構利用其他功能在 BizTalk Server 中，例如訂閱模型和以事件為基礎商務活動監控 (BAM)。</span><span class="sxs-lookup"><span data-stu-id="2e460-154">The ESB Exception Management Framework takes advantage of other features in BizTalk Server, such as the subscription model, and event-based Business Activity Monitoring (BAM).</span></span> <span data-ttu-id="2e460-155">這表示 ESB 例外狀況管理架構可以追蹤例外狀況資料點與 BAM，並將它們發行到 BizTalk BAM 入口網站使用監視。</span><span class="sxs-lookup"><span data-stu-id="2e460-155">This means that the ESB Exception Management Framework can track the exception data points with BAM, and then publish them to the BizTalk BAM Portal for monitoring.</span></span>