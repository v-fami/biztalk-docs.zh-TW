---
title: 元件的服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, pipelines
- pipelines, service solutions
- service solution tutorial, assemblies
- service solution tutorial, components [BizTalk Server]
- service solution tutorial, client applications
- assemblies, service solutions
- orchestrations, service solutions
- client applications, service solutions
- back-end systems
- service solution tutorial, orchestrations
- service solution tutorial, back-end applications
ms.assetid: 97b7b754-abfb-48f9-87bf-7fe171121166
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a50743b178f9394c74b137e265532542af2b579c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234254"
---
# <a name="components-of-the-service-oriented-solution"></a><span data-ttu-id="feecb-102">元件的服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="feecb-102">Components of the Service Oriented Solution</span></span>
<span data-ttu-id="feecb-103">本節描述服務導向解決方案的主要 BizTalk Server 元件。</span><span class="sxs-lookup"><span data-stu-id="feecb-103">This section describes the major BizTalk Server components of the Service Oriented Solution.</span></span> <span data-ttu-id="feecb-104">下列圖表顯示解決方案的主要元件：</span><span class="sxs-lookup"><span data-stu-id="feecb-104">The following diagram shows the major components of the solution:</span></span>  
  
 <span data-ttu-id="feecb-105">![服務導向解決方案流程圖](../core/media/service-oriented-flow-diagram.gif "Service_Oriented_Flow_Diagram")</span><span class="sxs-lookup"><span data-stu-id="feecb-105">![Service Oriented Solution Flow Diagram](../core/media/service-oriented-flow-diagram.gif "Service_Oriented_Flow_Diagram")</span></span>  
  
 <span data-ttu-id="feecb-106">服務導向解決方案有三個協調流程版本。</span><span class="sxs-lookup"><span data-stu-id="feecb-106">The Service Oriented solution has three versions of the orchestrations:</span></span>  
  
-   <span data-ttu-id="feecb-107">一個是其中所有三個後端應用程式都是虛設的版本</span><span class="sxs-lookup"><span data-stu-id="feecb-107">A version in which all three of the back-end applications are stubbed out</span></span>  
  
-   <span data-ttu-id="feecb-108">一個是其中所有三個後端應用程式都是內嵌叫用的版本</span><span class="sxs-lookup"><span data-stu-id="feecb-108">One in which all three back-end applications are invoked inline</span></span>  
  
-   <span data-ttu-id="feecb-109">一個則是使用配接器連接到應用程式的版本</span><span class="sxs-lookup"><span data-stu-id="feecb-109">A version that uses adapters to connect to the applications.</span></span>  
  
 <span data-ttu-id="feecb-110">所有的協調流程版本都會出現在 SDK\Senarios\SO\BTSSoln\Orchestrations 目錄中。</span><span class="sxs-lookup"><span data-stu-id="feecb-110">All versions of the orchestrations appear in the SDK\Senarios\SO\BTSSoln\Orchestrations directory.</span></span>  
  
 <span data-ttu-id="feecb-111">協調流程的內嵌版本提供解決方案內要求和回應之間的最低延遲時間。</span><span class="sxs-lookup"><span data-stu-id="feecb-111">The inline version of the orchestrations provides the lowest latency time within the solution between requests and responses.</span></span>  
  
 <span data-ttu-id="feecb-112">來源檔案的相關資訊，請參閱[服務導向解決方案的檔案庫存](../core/file-inventory-for-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="feecb-112">For information about the source files, see [File Inventory for the Service Oriented Solution](../core/file-inventory-for-the-service-oriented-solution.md).</span></span>  
  
## <a name="orchestrations-in-the-service-oriented-solution"></a><span data-ttu-id="feecb-113">服務導向解決方案中的協調流程</span><span class="sxs-lookup"><span data-stu-id="feecb-113">Orchestrations in the Service Oriented Solution</span></span>  
 <span data-ttu-id="feecb-114">三個協調流程， **CustomerServiceReceiveSend**， **CustomerServiceNativeRequestResponse**，和**CustomerService**組成方案。</span><span class="sxs-lookup"><span data-stu-id="feecb-114">Three orchestrations, **CustomerServiceReceiveSend**, **CustomerServiceNativeRequestResponse**, and **CustomerService** compose the bulk of the solution.</span></span> <span data-ttu-id="feecb-115">**CustomerServiceReceiveSend**和**CustomerServiceNativeRequestResponse**協調流程做為前端呼叫**CustomerService**協調流程。</span><span class="sxs-lookup"><span data-stu-id="feecb-115">The **CustomerServiceReceiveSend** and **CustomerServiceNativeRequestResponse** orchestrations act as front-ends that call the **CustomerService** orchestration.</span></span> <span data-ttu-id="feecb-116">**CustomerService**協調流程會執行大部分的工作，將要求傳送到後端應用程式、 收集回應，回應結合為單一訊息，並傳送訊息至適當前端協調流程。</span><span class="sxs-lookup"><span data-stu-id="feecb-116">The **CustomerService** orchestration does most of the work—sending requests to the back-end applications, gathering the replies, combining the replies into a single message, and sending the message to the appropriate front-end orchestration.</span></span> <span data-ttu-id="feecb-117">由於前端協調流程呼叫**CustomerService**協調流程，因此前端協調流程等候直到**CustomerService**協調流程完成。</span><span class="sxs-lookup"><span data-stu-id="feecb-117">Because the front-end orchestrations call the **CustomerService** orchestration, the front-end orchestrations wait until the **CustomerService** orchestration finishes.</span></span>  
  
 <span data-ttu-id="feecb-118">解決方案會公開**CustomerServiceNativeRequestResponse**為 Web 服務的協調流程。</span><span class="sxs-lookup"><span data-stu-id="feecb-118">The solution exposes the **CustomerServiceNativeRequestResponse** orchestration as a Web service.</span></span> <span data-ttu-id="feecb-119">**CustomerServiceReceiveSend**協調流程會從 MQSeries 佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="feecb-119">The **CustomerServiceReceiveSend** orchestration takes messages from an MQSeries queue.</span></span>  
  
## <a name="back-end-applications"></a><span data-ttu-id="feecb-120">後端應用程式</span><span class="sxs-lookup"><span data-stu-id="feecb-120">Back-end Applications</span></span>  
 <span data-ttu-id="feecb-121">服務導向解決方案會與三個後端應用程式通訊：</span><span class="sxs-lookup"><span data-stu-id="feecb-121">The Service Oriented solution communicates with three back-end applications:</span></span>  
  
-   <span data-ttu-id="feecb-122">**付款追蹤器**應用程式會傳回最近付款的模擬的清單。</span><span class="sxs-lookup"><span data-stu-id="feecb-122">The **PaymentTracker** application returns a simulated list of recent payments.</span></span> <span data-ttu-id="feecb-123">**付款追蹤器**從 MQSeries 佇列讀取要求並傳送回應至另一個 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="feecb-123">**PaymentTracker** reads the request from an MQSeries queue and sends the response to another MQSeries queue.</span></span>  
  
-   <span data-ttu-id="feecb-124">**PendingTransaction**應用程式會報告根據客戶帳戶擱置的交易總數。</span><span class="sxs-lookup"><span data-stu-id="feecb-124">The **PendingTransaction** application reports the sum of transactions pending against the customer account.</span></span> <span data-ttu-id="feecb-125">應用程式是 Web 服務，會接著使用 Microsoft Host Integration Server (HIS) 與大型主機電腦上的 CICS/COBOL 程式通訊。</span><span class="sxs-lookup"><span data-stu-id="feecb-125">The application is a Web service that, in turn, uses Microsoft Host Integration Server (HIS) to communicate with a CICS/COBOL program on a mainframe computer.</span></span>  
  
-   <span data-ttu-id="feecb-126">SAP 應用程式會提供有關客戶整個信用限制的資訊。</span><span class="sxs-lookup"><span data-stu-id="feecb-126">The SAP application provides information about the customer's overall credit limit.</span></span> <span data-ttu-id="feecb-127">解決方案會連接到 SAP 應用程式以做為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="feecb-127">The solution connects to the SAP application as a Web service.</span></span> <span data-ttu-id="feecb-128">應用程式使用中的 SAP 配接器[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]與 SAP 系統進行通訊。</span><span class="sxs-lookup"><span data-stu-id="feecb-128">The application uses the SAP adapter in [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] to communicate with a SAP system.</span></span>  
  
## <a name="pipelines"></a><span data-ttu-id="feecb-129">管線</span><span class="sxs-lookup"><span data-stu-id="feecb-129">Pipelines</span></span>  
 <span data-ttu-id="feecb-130">服務導向解決方案會使用預設管線，除了在兩個地方： 的接收管線**CustomerServiceReceiveSend**協調流程，而**CustomerService**協調流程的傳送管線**付款追蹤器**。</span><span class="sxs-lookup"><span data-stu-id="feecb-130">The Service Oriented solution uses default pipelines except in two places: the receive pipeline for the **CustomerServiceReceiveSend** orchestration, and the **CustomerService** orchestration's send pipeline to the **PaymentTracker**.</span></span> <span data-ttu-id="feecb-131">這兩個管線均使用自訂元件。</span><span class="sxs-lookup"><span data-stu-id="feecb-131">Both pipelines use custom components.</span></span>  
  
 <span data-ttu-id="feecb-132">接收管線**CustomerServiceReceiveSend**包含自訂合作對象解析 」 元件， **SSO 票證發照者管線元件**。</span><span class="sxs-lookup"><span data-stu-id="feecb-132">The receive pipeline for **CustomerServiceReceiveSend** includes a custom party resolution component, **SSO Ticket Issuer Pipeline Component**.</span></span> <span data-ttu-id="feecb-133">訊息的**CustomerServiceReceiveSend**協調流程收到沒有認證。</span><span class="sxs-lookup"><span data-stu-id="feecb-133">The messages that the **CustomerServiceReceiveSend** orchestration receives do not have credentials.</span></span> <span data-ttu-id="feecb-134">這可模擬若訊息來自「互動式語音回應」(Interactive Voice Response) 系統時會發生的情形。</span><span class="sxs-lookup"><span data-stu-id="feecb-134">This simulates what would happen if the messages came from an Interactive Voice Response system.</span></span> <span data-ttu-id="feecb-135">自訂管線元件會使用 BizTalk 接收主控件的服務帳戶，來新增認證。</span><span class="sxs-lookup"><span data-stu-id="feecb-135">The custom pipeline component adds credentials using the service account of the BizTalk receive host.</span></span>  
  
 <span data-ttu-id="feecb-136">相較之下，訊息**CustomerSericeNativeRequestResponse**協調流程收到已經具有認證。</span><span class="sxs-lookup"><span data-stu-id="feecb-136">In contrast, the messages the **CustomerSericeNativeRequestResponse** orchestration receives already have credentials.</span></span> <span data-ttu-id="feecb-137">由於 Web 服務的虛擬資料夾是針對整合式安全性所設定，而 SOAP 接收位置則是設定為要整合「企業單一登入」(SSO)，因此 SOAP 配接器會產生訊息票證。</span><span class="sxs-lookup"><span data-stu-id="feecb-137">Because the virtual folder for the Web service is configured for integrated security and the SOAP receive location is configured to integrate Enterprise Single Sign-On (SSO), the SOAP adapter generates a ticket for the message.</span></span>  
  
 <span data-ttu-id="feecb-138">其他的自訂管線會出現在**CustomerService**傳送管線**付款追蹤器**應用程式。</span><span class="sxs-lookup"><span data-stu-id="feecb-138">The other custom pipeline appears in the **CustomerService** send pipeline to the **PaymentTracker** application.</span></span> <span data-ttu-id="feecb-139">MQSeries Header Setter Pipeline Component 元件會設定兩個 MQSeries 訊息標頭屬性的值。</span><span class="sxs-lookup"><span data-stu-id="feecb-139">The component, MQSeries Header Setter Pipeline Component, sets values for two MQSeries message header properties.</span></span> <span data-ttu-id="feecb-140">元件設定的第一個訊息資料格式 (**MQMD_Format**)，以指示訊息的形式**MQCIH**結構，通常用來與 CICS 程式通訊的結構。</span><span class="sxs-lookup"><span data-stu-id="feecb-140">The component sets the first, the Message Data Format (**MQMD_Format**), to indicate the message is in the form of an **MQCIH** structure, a structure commonly used to communicate with CICS programs.</span></span> <span data-ttu-id="feecb-141">第二個，資料本身的格式內**MQCIH**結構 (**MQCIH_Format**)，設定為 顯示訊息是一個字串。</span><span class="sxs-lookup"><span data-stu-id="feecb-141">The second, the format of the data itself within the **MQCIH** structure (**MQCIH_Format**),is set to show the message is a string.</span></span>  
  
 <span data-ttu-id="feecb-142">使用**MQCIH**格式可讓您傳遞使用者 ID 和密碼在**MQCIH**結構。</span><span class="sxs-lookup"><span data-stu-id="feecb-142">Using the **MQCIH** format enables you to pass the user ID and password in the **MQCIH** structure.</span></span> <span data-ttu-id="feecb-143">SSO 分支機構應用程式會將 BizTalk 應用程式的 Windows 使用者識別碼對應至付款追蹤系統的使用者識別碼傳入**MQCIH**結構。</span><span class="sxs-lookup"><span data-stu-id="feecb-143">SSO affiliate applications map the BizTalk application's Windows user ID to the Payment Tracking System's user IDs passed in the **MQCIH** structure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feecb-144">解決方案的內嵌版本可從協調流程呼叫相同的管線來使用。</span><span class="sxs-lookup"><span data-stu-id="feecb-144">The inline version of the solution uses the same pipelines by calling them from the orchestration.</span></span> <span data-ttu-id="feecb-145">這樣即可重複使用管線程式碼。</span><span class="sxs-lookup"><span data-stu-id="feecb-145">This enables re-use of the pipeline code.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="feecb-146">用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="feecb-146">Client Application</span></span>  
 <span data-ttu-id="feecb-147">解決方案包含以 C# 撰寫的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="feecb-147">The solution includes a client application written in C#.</span></span> <span data-ttu-id="feecb-148">您可以使用應用程式，以 SOAP 或 MQSeries 訊息傳送要求，並檢查結果。</span><span class="sxs-lookup"><span data-stu-id="feecb-148">You can use the application to send requests as SOAP or MQSeries messages, and examine the results.</span></span>  
  
## <a name="other-assemblies"></a><span data-ttu-id="feecb-149">其他組件</span><span class="sxs-lookup"><span data-stu-id="feecb-149">Other Assemblies</span></span>  
 <span data-ttu-id="feecb-150">應用程式包含上述摘要圖表中沒有顯示的數個輔助組件。</span><span class="sxs-lookup"><span data-stu-id="feecb-150">The application includes several auxiliary assemblies not shown in the summary diagram above.</span></span> <span data-ttu-id="feecb-151">**公用程式**方案的組件公用程式函式。</span><span class="sxs-lookup"><span data-stu-id="feecb-151">The **Utilities** assembly utility functions for the solution.</span></span>  
  
 <span data-ttu-id="feecb-152">**ErrorHelper**組件包含類別，將錯誤碼轉譯為訊息，以及將錯誤訊息轉換為錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="feecb-152">The **ErrorHelper** assembly contains classes to translate error codes into messages, and to convert error messages to error codes.</span></span>  
  
 <span data-ttu-id="feecb-153">**ServiceLevelTracking**組件包括 helper 方法來追蹤服務等級協定的資料使用商務活動監控 (BAM) API。</span><span class="sxs-lookup"><span data-stu-id="feecb-153">The **ServiceLevelTracking** assembly includes helper methods using the Business Activity Monitoring (BAM) API to track service-level agreement data.</span></span>  
  
 <span data-ttu-id="feecb-154">**ConfigHelper**組件包含協助程式方法，以擷取組態值，從方案**SSOConfigStore**應用程式。</span><span class="sxs-lookup"><span data-stu-id="feecb-154">The **ConfigHelper** assembly contains helper methods to retrieve configuration values for the solution from the **SSOConfigStore** application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feecb-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feecb-155">See Also</span></span>  
 <span data-ttu-id="feecb-156">[開發服務導向解決方案](../core/developing-a-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="feecb-156">[Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="feecb-157">檔案庫存服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="feecb-157">File Inventory for the Service Oriented Solution</span></span>](../core/file-inventory-for-the-service-oriented-solution.md)