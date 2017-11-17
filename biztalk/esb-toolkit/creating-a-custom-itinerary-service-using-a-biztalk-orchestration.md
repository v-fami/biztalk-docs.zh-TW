---
title: "建立自訂路線服務使用 BizTalk 協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bd7ed38-02a3-41b1-9990-754d5539f15e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723c0bc93192267f404d42e7fe859bb37ea59895
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-itinerary-service-using-a-biztalk-orchestration"></a><span data-ttu-id="b020c-102">建立自訂路線服務使用 BizTalk 協調流程</span><span class="sxs-lookup"><span data-stu-id="b020c-102">Creating a Custom Itinerary Service Using a BizTalk Orchestration</span></span>
<span data-ttu-id="b020c-103">屬於路線 framework[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援的計劃使用協調流程的步驟執行。</span><span class="sxs-lookup"><span data-stu-id="b020c-103">The itinerary framework that is part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports execution of itinerary steps using orchestrations.</span></span> <span data-ttu-id="b020c-104">您可以實作自訂的路線服務為 Microsoft BizTalk Server 協調流程根據功能需求，這可能包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="b020c-104">You can implement a custom itinerary service as a Microsoft BizTalk Server orchestration based on your functional requirements, which may include the following:</span></span>  
  
-   <span data-ttu-id="b020c-105">多個服務引動過程 (所示[安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md))</span><span class="sxs-lookup"><span data-stu-id="b020c-105">Multiple service invocations (as demonstrated by the [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md))</span></span>  
  
-   <span data-ttu-id="b020c-106">通訊協定中繼和訊息相互關聯 (例如，MQSeries HTTP)</span><span class="sxs-lookup"><span data-stu-id="b020c-106">Protocol mediation and message correlation (for example, HTTP-MQSeries)</span></span>  
  
-   <span data-ttu-id="b020c-107">複雜的路由決策根據訊息豐富 」，從外部資料來源</span><span class="sxs-lookup"><span data-stu-id="b020c-107">Complex routing decisions based on message enrichment from external data sources</span></span>  
  
-   <span data-ttu-id="b020c-108">商務處理邏輯</span><span class="sxs-lookup"><span data-stu-id="b020c-108">Business processing logic</span></span>  
  
 <span data-ttu-id="b020c-109">使用 BizTalk Server 協調流程實作的每個路線服務會負責下列各項：</span><span class="sxs-lookup"><span data-stu-id="b020c-109">Every itinerary service implemented using a BizTalk Server orchestration is responsible for the following:</span></span>  
  
-   <span data-ttu-id="b020c-110">例外狀況和錯誤處理使用 ESB 例外狀況處理的架構或選擇性的自訂例外狀況處理常式，支援重新提交 （單向旅）</span><span class="sxs-lookup"><span data-stu-id="b020c-110">Exception and error handling using the ESB Exception Handling Framework or optional custom exception handlers that support resubmission (one-way itineraries)</span></span>  
  
-   <span data-ttu-id="b020c-111">前進的路線，如此路線服務下一步可以執行發行輸出訊息透過 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b020c-111">Advancing the itinerary and publishing outbound messages through BizTalk Server so that the next itinerary service step can execute</span></span>  
  
#### <a name="to-create-a-custom-itinerary-service-using-a-biztalk-server-orchestration"></a><span data-ttu-id="b020c-112">若要建立自訂路線服務使用的 BizTalk Server 協調流程</span><span class="sxs-lookup"><span data-stu-id="b020c-112">To create a custom itinerary service using a BizTalk Server orchestration</span></span>  
  
1.  <span data-ttu-id="b020c-113">建立包含新的協調流程; 新的 BizTalk Server 專案例如，MyCustomeItineraryService.odx。</span><span class="sxs-lookup"><span data-stu-id="b020c-113">Create new BizTalk Server project containing a new orchestration; for example, MyCustomeItineraryService.odx.</span></span>  
  
2.  <span data-ttu-id="b020c-114">加入下列組件的參考：</span><span class="sxs-lookup"><span data-stu-id="b020c-114">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="b020c-115">**Microsoft.Practices.ESB.Itinerary**</span><span class="sxs-lookup"><span data-stu-id="b020c-115">**Microsoft.Practices.ESB.Itinerary**</span></span>  
  
    -   <span data-ttu-id="b020c-116">**Microsoft.Practices.ESB.Itinerary.Schemas**</span><span class="sxs-lookup"><span data-stu-id="b020c-116">**Microsoft.Practices.ESB.Itinerary.Schemas**</span></span>  
  
    -   <span data-ttu-id="b020c-117">**Microsoft.Practices.ESB.ExceptionHandling**</span><span class="sxs-lookup"><span data-stu-id="b020c-117">**Microsoft.Practices.ESB.ExceptionHandling**</span></span>  
  
    -   <span data-ttu-id="b020c-118">**Microsoft.Practices.ESB.ExceptionHandling.Faults**</span><span class="sxs-lookup"><span data-stu-id="b020c-118">**Microsoft.Practices.ESB.ExceptionHandling.Faults**</span></span>  
  
3.  <span data-ttu-id="b020c-119">定義邏輯直接繫結協調流程中接收埠，並啟動的接收 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="b020c-119">Define a logical direct-bound receive port and an activated receive shape in the orchestration.</span></span>  
  
4.  <span data-ttu-id="b020c-120">定義要啟動訊息路線內容從協調流程，使協調流程執行的訂用帳戶篩選**MyCustomItineraryService**步驟。</span><span class="sxs-lookup"><span data-stu-id="b020c-120">Define a subscription filter to activate the orchestration from the message itinerary context so that the orchestration executes the **MyCustomItineraryService** step.</span></span> <span data-ttu-id="b020c-121">下列程式碼顯示適當的篩選器的範例。</span><span class="sxs-lookup"><span data-stu-id="b020c-121">The following code shows an example of a suitable filter.</span></span>  
  
    ```csharp  
    (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName   
        == "MyCustomItineraryService")   
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
        == "Orchestration")  
    ```  
  
5.  <span data-ttu-id="b020c-122">定義類型的協調流程**Microsoft.Practices.ESB.Itinerary.ItineraryStep**。</span><span class="sxs-lookup"><span data-stu-id="b020c-122">Define an orchestration of type **Microsoft.Practices.ESB.Itinerary.ItineraryStep**.</span></span> <span data-ttu-id="b020c-123">運算式將活動新增至協調流程會填入此變數，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="b020c-123">Add an expression activity to the orchestration that populates this variable, as shown in the following code.</span></span>  
  
    ```csharp  
    // Retrieve the current itinerary step.  
    itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
    step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
    itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
    step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
  
    ```  
  
6.  <span data-ttu-id="b020c-124">將您的自訂實作新增至路線建立外寄訊息路線接下來的步驟。例如，OutboundMsg。</span><span class="sxs-lookup"><span data-stu-id="b020c-124">Add your custom implementation to the itinerary that creates the outbound message for the next itinerary steps; for example, OutboundMsg.</span></span>  
  
7.  <span data-ttu-id="b020c-125">前進的路線，使用下列的運算式活動，會使用從輸入訊息的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="b020c-125">Advance the itinerary using the following expression activity that uses the message context from inbound message.</span></span>  
  
    ```csharp  
    OutboundMessage(*) = InboundMessage(*);   
    itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
    ```  
  
8.  <span data-ttu-id="b020c-126">透過直接繫結傳送埠以啟用 下一步路線服務傳送外寄訊息與更新的路線。</span><span class="sxs-lookup"><span data-stu-id="b020c-126">Send the outbound message with the updated itinerary through a direct-bound send port to activate the next itinerary service.</span></span>  
  
 <span data-ttu-id="b020c-127">如需有關如何實作自訂路線服務使用 BizTalk Server 協調流程的詳細資訊，請參閱[安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)和[安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="b020c-127">For more information about implementing a custom itinerary service using BizTalk Server orchestrations, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) and [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).</span></span>