---
title: "建立自訂的路線傳訊服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2de44c21-68ca-4cf1-a117-bcb35af1b4a9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f08168e69e26d56cb39fb5c05cc53c3cbb51202
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-custom-itinerary-messaging-service"></a><span data-ttu-id="95124-102">建立自訂的路線訊息處理服務</span><span class="sxs-lookup"><span data-stu-id="95124-102">Creating a Custom Itinerary Messaging Service</span></span>
<span data-ttu-id="95124-103">屬於路線 framework[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援路線步驟使用實作類別的執行**IMessagingService**執行路線訊息服務的介面。</span><span class="sxs-lookup"><span data-stu-id="95124-103">The itinerary framework that is part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports execution of itinerary steps using classes implementing the **IMessagingService** interface that execute itinerary messaging services.</span></span> <span data-ttu-id="95124-104">當您想要負責下列服務時，您可以實作自訂訊息處理服務：</span><span class="sxs-lookup"><span data-stu-id="95124-104">You can implement a custom messaging service when you want the service to be responsible for the following:</span></span>  
  
-   <span data-ttu-id="95124-105">路線中設定的自訂訊息驗證</span><span class="sxs-lookup"><span data-stu-id="95124-105">Custom message validation configured in the itinerary</span></span>  
  
-   <span data-ttu-id="95124-106">在路線中設定的自訂訊息轉換</span><span class="sxs-lookup"><span data-stu-id="95124-106">Custom message transformation configured in the itinerary</span></span>  
  
-   <span data-ttu-id="95124-107">自訂訊息處理</span><span class="sxs-lookup"><span data-stu-id="95124-107">Custom processing of the message</span></span>  
  
 <span data-ttu-id="95124-108">在這些情況下，您實作自訂路線服務做為攔截器，並由發送器管線元件呼叫。</span><span class="sxs-lookup"><span data-stu-id="95124-108">In all these cases, a custom itinerary service that you implement acts as an interceptor and is called by the Dispatcher pipeline component.</span></span>  
  
 <span data-ttu-id="95124-109">自訂訊息型路線服務或訊息的服務，所有實作**IMessagingService**介面。</span><span class="sxs-lookup"><span data-stu-id="95124-109">Custom messaging-based itinerary services, or messaging services, all implement the **IMessagingService** interface.</span></span> <span data-ttu-id="95124-110">此介面會公開**名稱**和**SupportsDisassemble**屬性和**Execute**和**ShouldAdvanceStep**方法。</span><span class="sxs-lookup"><span data-stu-id="95124-110">This interface exposes the **Name** and **SupportsDisassemble** properties and the **Execute** and **ShouldAdvanceStep** methods.</span></span>  
  
 <span data-ttu-id="95124-111">**名稱**屬性是服務的名稱，因為它會出現在路線。</span><span class="sxs-lookup"><span data-stu-id="95124-111">The **Name** property is the name of the service as it will appear in an itinerary.</span></span> <span data-ttu-id="95124-112">它必須符合 Esb.config 檔案中的計劃的服務組態中設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="95124-112">It must match the configured name in the itinerary services configuration in the Esb.config file.</span></span>  
  
 <span data-ttu-id="95124-113">**SupportsDisassemble**屬性會指出是否自訂的訊息處理服務，您要建立支援反組譯及多個的解析程式執行。</span><span class="sxs-lookup"><span data-stu-id="95124-113">The **SupportsDisassemble** property indicates whether the custom messaging service you are creating supports disassemble and the execution of multiple resolvers.</span></span>  
  
 <span data-ttu-id="95124-114">**ShouldAdvanceStep**方法接受目前的路線步驟和目前的訊息，並傳回布林值，指出發送器是否應該在服務執行之後前進的路線。</span><span class="sxs-lookup"><span data-stu-id="95124-114">The **ShouldAdvanceStep** method takes in the current itinerary step, and the current message, and returns a Boolean value that indicates whether the dispatcher should advance the itinerary after the service executes.</span></span> <span data-ttu-id="95124-115">在大多數情況下，此方法應傳回**true**。</span><span class="sxs-lookup"><span data-stu-id="95124-115">In almost all cases, this method should return **true**.</span></span>  
  
 <span data-ttu-id="95124-116">**Execute**方法是重要性最高的訊息處理服務，並包含將在執行階段執行的邏輯。</span><span class="sxs-lookup"><span data-stu-id="95124-116">The **Execute** method is of greatest importance for a messaging service and contains the logic that will be executed at run time.</span></span> <span data-ttu-id="95124-117">它會在管線內容、 訊息、 解析程式的字串，以及目前路線的步驟。它會傳回更新的訊息。</span><span class="sxs-lookup"><span data-stu-id="95124-117">It takes in the pipeline context, the message, the resolver string, and the current itinerary step; and it returns the updated message.</span></span>  
  
 <span data-ttu-id="95124-118">參考實作**Execute** ESB RoutingService.cs 檔案中找到方法。Itinerary.Services 專案，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="95124-118">A reference implementation of the **Execute** method can be found in the RoutingService.cs file of the ESB.Itinerary.Services project, as shown in the following code.</span></span>  
  
```csharp  
public IBaseMessage ExecuteRoute(IPipelineContext context, IBaseMessage msg, string resolverString)  
        {  
            if (context == null)  
                throw new ArgumentNullException("context");  
            if (msg == null)  
                throw new ArgumentNullException("msg");  
            if (string.IsNullOrEmpty(resolverString))  
                throw new ArgumentException(Properties.Resources.ArgumentStringRequired, "resolverString");  
            try  
            {  
                ResolverInfo info = ResolverMgr.GetResolverInfo(ResolutionType.Endpoint, resolverString);  
                if (!info.Success)  
                    throw new RoutingException(Properties.Resources.ResolverStringInvalid, resolverString);  
  
                // Resolve configuration for routing.  
                Dictionary<string, string> resolverDictionary = ResolverMgr.Resolve(info, msg, context);  
  
                if (string.IsNullOrEmpty(resolverDictionary["Resolver.TransportLocation"]))  
                    throw new RoutingException(Properties.Resources.TransportLocationNotResolved, resolverString);  
  
                AdapterMgr.SetEndpoint(resolverDictionary, msg.Context);  
  
                return msg;  
            }  
            catch (System.Exception ex)  
            {  
                EventLogger.Write(MethodInfo.GetCurrentMethod(), ex);  
                throw;  
            }        
        }  
```  
  
 <span data-ttu-id="95124-119">**若要實作自訂路線服務的訊息**</span><span class="sxs-lookup"><span data-stu-id="95124-119">**To implement a custom itinerary service for messaging**</span></span>  
  
1.  <span data-ttu-id="95124-120">建立組件的類別衍生自**IMessagingService;**中**Execute**方法，包括可修改訊息或訊息內容 （如果有的話） 所需的所有邏輯。</span><span class="sxs-lookup"><span data-stu-id="95124-120">Create an assembly with a class that derives from **IMessagingService;** in the **Execute** method, include all logic necessary to make modifications to the message or the message context (if any).</span></span>  
  
2.  <span data-ttu-id="95124-121">新增項目中的**itineraryServices** Esb.config 檔案加入您的服務區段 **\<itineraryService\>** 項目以做為 GUID**識別碼**屬性，做為服務的名稱**名稱**屬性，做為類別的完整的名稱**類型**屬性**傳訊**為**範圍**屬性，並允許的階段 (例如， **OnRampReceive**， **OnRampSend**， **OffRampSend**， **OffRampReceive**， **AllSend**， **AllReceive**，或**所有**) 做為**階段**屬性。</span><span class="sxs-lookup"><span data-stu-id="95124-121">Add an entry in the **itineraryServices** section of the Esb.config file for your service by adding an **\<itineraryService\>** element with a GUID as the **id** attribute, the name of the service as the **name** attribute, the fully qualified name of the class as the **type** attribute, **Messaging** as the **scope** attribute, and the allowed stage (for example, **OnRampReceive**, **OnRampSend**, **OffRampSend**, **OffRampReceive**, **AllSend**, **AllReceive**, or **All**) as the **stage** attribute.</span></span>  
  
3.  <span data-ttu-id="95124-122">在全域組件快取中註冊新的組件。</span><span class="sxs-lookup"><span data-stu-id="95124-122">Register the new assembly in the global assembly cache.</span></span>