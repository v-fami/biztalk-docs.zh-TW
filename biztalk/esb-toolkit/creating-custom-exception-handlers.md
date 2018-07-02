---
title: 建立自訂的例外狀況處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 401aec8d-d9ca-4a88-9e5b-d3ab605dc0a1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33d49fddb8a42c440f62acdd4ea337f43b876f6b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971519"
---
# <a name="creating-custom-exception-handlers"></a><span data-ttu-id="67713-102">建立自訂的例外狀況處理常式</span><span class="sxs-lookup"><span data-stu-id="67713-102">Creating Custom Exception Handlers</span></span>
<span data-ttu-id="67713-103">若要偵測和回應例外狀況的應用程式，開發人員必須提供例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="67713-103">For an application to detect and react to exceptions, developers must provide an exception handler.</span></span> <span data-ttu-id="67713-104">這個例外狀況處理常式可以訂閱一種例外狀況訊息或從一個系統或應用程式的部分或所有組件產生的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="67713-104">This exception handler can subscribe to a single type of exception message or to exception messages generated from some or all parts of a system or an application.</span></span> <span data-ttu-id="67713-105">例如，您可能需要在單一處理常式的所有訊息從特定的系統 （例如薪資系統中發生任何例外），或可能會改為所需目標的處理常式 （例如偵測是否檢查列印程序的特定失敗失敗）。</span><span class="sxs-lookup"><span data-stu-id="67713-105">For example, you may require only a single handler for all messages from a particular system (such as any exceptions occurring in the payroll system), or you may instead require targeted handlers for specific failures (such as detecting if the check print process fails).</span></span>  
  
 <span data-ttu-id="67713-106">若要訂閱特定類型的例外狀況，請使用篩選對啟動的 [接收] 圖形中，協調流程，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="67713-106">To subscribe to a specific type of exception, use an orchestration that has a filter on the activating Receive shape, as shown in the following example.</span></span>  
  
```csharp  
Microsoft.Practices.ESB.ExceptionHandling.Schemas.Property.FaultCode == "1000";  
```  
  
 <span data-ttu-id="67713-107">您也可以篩選條件將訊息傳送至檔案系統，或透過電子郵件訊息符合特定篩選條件的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="67713-107">You may also have a filter condition on a send port that sends a message to the file system or via e-mail if the message meets a specific filter condition.</span></span>  
  
## <a name="sample-exception-handling-projects"></a><span data-ttu-id="67713-108">範例例外狀況處理的專案</span><span class="sxs-lookup"><span data-stu-id="67713-108">Sample Exception Handling Projects</span></span>  
 <span data-ttu-id="67713-109">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個範例 BizTalk 應用程式，示範例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="67713-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several sample BizTalk applications that demonstrate exception handling.</span></span> <span data-ttu-id="67713-110">可以在 \Source\Samples\Exception 處理資料夾中找到這些範例。</span><span class="sxs-lookup"><span data-stu-id="67713-110">These samples can be found in the \Source\Samples\Exception Handling folder.</span></span>  
  
 <span data-ttu-id="67713-111">另外還有四個 BizTalk 專案，位於 GlobalBank.ESB.Samples.ExceptionHandling 解決方案中，示範如何使用 ESB 失敗的協調流程例外狀況路由機制。</span><span class="sxs-lookup"><span data-stu-id="67713-111">There are also four BizTalk projects, located in the GlobalBank.ESB.Samples.ExceptionHandling solution, that demonstrate how to use the ESB Failed Orchestration Exception Routing mechanism.</span></span> <span data-ttu-id="67713-112">這些專案預先設定為部署到 GlobalBank.ESB BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="67713-112">These projects are preconfigured to deploy into the GlobalBank.ESB BizTalk application.</span></span> <span data-ttu-id="67713-113">這些專案包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="67713-113">The projects are the following:</span></span>  
  
- <span data-ttu-id="67713-114">**ESB。ExceptionHandling.Schemas。**</span><span class="sxs-lookup"><span data-stu-id="67713-114">**ESB.ExceptionHandling.Schemas.**</span></span> <span data-ttu-id="67713-115">此專案包含範例協調流程使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="67713-115">This project contains the schemas used for the sample orchestrations.</span></span>  
  
- <span data-ttu-id="67713-116">**ESB。ExceptionHandling.Pipelines。**</span><span class="sxs-lookup"><span data-stu-id="67713-116">**ESB.ExceptionHandling.Pipelines.**</span></span> <span data-ttu-id="67713-117">此專案包含將用於傳送埠訂閱的所有例外狀況的例外狀況處理器設定的傳送管線。</span><span class="sxs-lookup"><span data-stu-id="67713-117">This project contains the send pipeline configured with the exception processor, used in a send port that subscribes to all exceptions.</span></span> <span data-ttu-id="67713-118">這包括產生 BizTalk 和例外狀況管理架構所產生的例外狀況的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="67713-118">This includes exceptions generated by BizTalk and exceptions generated by the Exception Management Framework.</span></span>  
  
- <span data-ttu-id="67713-119">**ESB。ExceptionHandling.Processes。**</span><span class="sxs-lookup"><span data-stu-id="67713-119">**ESB.ExceptionHandling.Processes.**</span></span> <span data-ttu-id="67713-120">此專案包含 EAIProcess.odx 協調流程，藉由嘗試除以零並呼叫模擬例外狀況**CreateFaultMessage**並**AddMessage**来產生合適的方法錯誤訊息，如 圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="67713-120">This project contains the EAIProcess.odx orchestration, which simulates an exception by attempting to divide by zero and calls the **CreateFaultMessage** and **AddMessage** methods to generate a suitable fault message, as shown in Figure 1.</span></span>  
  
   <span data-ttu-id="67713-121">![協調流程處理範例](../esb-toolkit/media/ch4-orchestrationprocessessample.gif "第 4 章第 OrchestrationProcessesSample")</span><span class="sxs-lookup"><span data-stu-id="67713-121">![Orchestration Processes Sample](../esb-toolkit/media/ch4-orchestrationprocessessample.gif "Ch4-OrchestrationProcessesSample")</span></span>  
  
   <span data-ttu-id="67713-122">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="67713-122">**Figure 1**</span></span>  
  
  <span data-ttu-id="67713-123">**EAIProcess.odx 協調流程中處理程序範例專案**</span><span class="sxs-lookup"><span data-stu-id="67713-123">**The EAIProcess.odx orchestration in the Processes sample project**</span></span>  
  
- <span data-ttu-id="67713-124">**ESB。ExceptionHandling.Handlers。**</span><span class="sxs-lookup"><span data-stu-id="67713-124">**ESB.ExceptionHandling.Handlers.**</span></span> <span data-ttu-id="67713-125">此專案包含 EAIGenericHandler.odx 協調流程中，它會呼叫**GetMessages**方法，並逐一**MessageCollection**使用**MoveNext**方法，如 [圖 2] 所示。</span><span class="sxs-lookup"><span data-stu-id="67713-125">This project contains the EAIGenericHandler.odx orchestration, which calls the **GetMessages** method and iterates through the **MessageCollection** using the **MoveNext** method, as shown in Figure 2.</span></span>  
  
  <span data-ttu-id="67713-126">![協調流程處理常式範例泛型](../esb-toolkit/media/ch4-orchestrationhandlerssamplegeneric.gif "第 4 章第 OrchestrationHandlersSampleGeneric")</span><span class="sxs-lookup"><span data-stu-id="67713-126">![Orchestration Handlers Sample Generic](../esb-toolkit/media/ch4-orchestrationhandlerssamplegeneric.gif "Ch4-OrchestrationHandlersSampleGeneric")</span></span>  
  
  <span data-ttu-id="67713-127">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="67713-127">**Figure 2**</span></span>  
  
  <span data-ttu-id="67713-128">**EAIGenericHandler.odx 中的協調流程處理常式範例專案**</span><span class="sxs-lookup"><span data-stu-id="67713-128">**The EAIGenericHandler.odx orchestration in the Handlers sample project**</span></span>  
  
  <span data-ttu-id="67713-129">ESB。ExceptionHandling.Handlers 專案也包含 EAIProcessHandler.odx 協調流程中，它會呼叫**GetMessage**並**GetException**方法，如 [圖 3] 所示。</span><span class="sxs-lookup"><span data-stu-id="67713-129">The ESB.ExceptionHandling.Handlers project also contains the EAIProcessHandler.odx orchestration, which calls the **GetMessage** and **GetException** methods, as shown in Figure 3.</span></span>  
  
  <span data-ttu-id="67713-130">![協調流程處理常式範例處理程序](../esb-toolkit/media/ch4-orchestrationhandlerssampleprocess.gif "第 4 章第 OrchestrationHandlersSampleProcess")</span><span class="sxs-lookup"><span data-stu-id="67713-130">![Orchestration Handlers Sample Process](../esb-toolkit/media/ch4-orchestrationhandlerssampleprocess.gif "Ch4-OrchestrationHandlersSampleProcess")</span></span>  
  
  <span data-ttu-id="67713-131">**圖 3**</span><span class="sxs-lookup"><span data-stu-id="67713-131">**Figure 3**</span></span>  
  
  <span data-ttu-id="67713-132">**EAIProcessHandler.odx 中的協調流程處理常式範例專案**</span><span class="sxs-lookup"><span data-stu-id="67713-132">**The EAIProcessHandler.odx orchestration in the Handlers sample project**</span></span>