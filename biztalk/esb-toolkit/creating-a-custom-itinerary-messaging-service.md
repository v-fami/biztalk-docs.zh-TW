---
title: 建立自訂路線傳訊服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2de44c21-68ca-4cf1-a117-bcb35af1b4a9
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecb6c6976493e05c9df747de4a358df7fff7809f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983919"
---
# <a name="creating-a-custom-itinerary-messaging-service"></a><span data-ttu-id="c4993-102">建立自訂路線傳訊服務</span><span class="sxs-lookup"><span data-stu-id="c4993-102">Creating a Custom Itinerary Messaging Service</span></span>
<span data-ttu-id="c4993-103">路線的架構，屬於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援的路線的步驟，使用實作的類別執行**IMessagingService**執行路線傳訊服務的介面。</span><span class="sxs-lookup"><span data-stu-id="c4993-103">The itinerary framework that is part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports execution of itinerary steps using classes implementing the **IMessagingService** interface that execute itinerary messaging services.</span></span> <span data-ttu-id="c4993-104">當您想要負責下列服務時，您可以實作自訂傳訊服務：</span><span class="sxs-lookup"><span data-stu-id="c4993-104">You can implement a custom messaging service when you want the service to be responsible for the following:</span></span>  
  
- <span data-ttu-id="c4993-105">路線中設定的自訂訊息驗證</span><span class="sxs-lookup"><span data-stu-id="c4993-105">Custom message validation configured in the itinerary</span></span>  
  
- <span data-ttu-id="c4993-106">路線中設定的自訂訊息轉換</span><span class="sxs-lookup"><span data-stu-id="c4993-106">Custom message transformation configured in the itinerary</span></span>  
  
- <span data-ttu-id="c4993-107">自訂訊息處理</span><span class="sxs-lookup"><span data-stu-id="c4993-107">Custom processing of the message</span></span>  
  
  <span data-ttu-id="c4993-108">在這些情況下，您實作自訂路線服務做為攔截器，並由 「 發送器 」 管線元件呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4993-108">In all these cases, a custom itinerary service that you implement acts as an interceptor and is called by the Dispatcher pipeline component.</span></span>  
  
  <span data-ttu-id="c4993-109">自訂訊息路線服務或傳訊服務，所有實作**IMessagingService**介面。</span><span class="sxs-lookup"><span data-stu-id="c4993-109">Custom messaging-based itinerary services, or messaging services, all implement the **IMessagingService** interface.</span></span> <span data-ttu-id="c4993-110">此介面會公開**名稱**並**SupportsDisassemble**屬性和**Execute**並**ShouldAdvanceStep**方法。</span><span class="sxs-lookup"><span data-stu-id="c4993-110">This interface exposes the **Name** and **SupportsDisassemble** properties and the **Execute** and **ShouldAdvanceStep** methods.</span></span>  
  
  <span data-ttu-id="c4993-111">**名稱**屬性是它會顯示在路線服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4993-111">The **Name** property is the name of the service as it will appear in an itinerary.</span></span> <span data-ttu-id="c4993-112">它必須符合路線服務組態中的 Esb.config 檔案中設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4993-112">It must match the configured name in the itinerary services configuration in the Esb.config file.</span></span>  
  
  <span data-ttu-id="c4993-113">**SupportsDisassemble**屬性會指出是否自訂的傳訊服務，您要建立支援反組譯及多個的解析程式執行。</span><span class="sxs-lookup"><span data-stu-id="c4993-113">The **SupportsDisassemble** property indicates whether the custom messaging service you are creating supports disassemble and the execution of multiple resolvers.</span></span>  
  
  <span data-ttu-id="c4993-114">**ShouldAdvanceStep**方法會接受目前的路線步驟中和目前的訊息，並傳回布林值，指出服務執行之後，發送器是否應該前進的路線。</span><span class="sxs-lookup"><span data-stu-id="c4993-114">The **ShouldAdvanceStep** method takes in the current itinerary step, and the current message, and returns a Boolean value that indicates whether the dispatcher should advance the itinerary after the service executes.</span></span> <span data-ttu-id="c4993-115">在幾乎所有的情況下，這個方法會傳回 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="c4993-115">In almost all cases, this method should return **true**.</span></span>  
  
  <span data-ttu-id="c4993-116">**Execute**方法是將重要性最高的傳訊服務，並包含將於執行階段上執行的邏輯。</span><span class="sxs-lookup"><span data-stu-id="c4993-116">The **Execute** method is of greatest importance for a messaging service and contains the logic that will be executed at run time.</span></span> <span data-ttu-id="c4993-117">它會採用管線內容、 訊息、 解析程式的字串，以及目前的路線步驟;它會傳回更新的訊息。</span><span class="sxs-lookup"><span data-stu-id="c4993-117">It takes in the pipeline context, the message, the resolver string, and the current itinerary step; and it returns the updated message.</span></span>  
  
  <span data-ttu-id="c4993-118">參考實作**Execute** ESB RoutingService.cs 檔案中找到方法。Itinerary.Services 專案，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c4993-118">A reference implementation of the **Execute** method can be found in the RoutingService.cs file of the ESB.Itinerary.Services project, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="c4993-119">**若要實作自訂路線傳訊服務**</span><span class="sxs-lookup"><span data-stu-id="c4993-119">**To implement a custom itinerary service for messaging**</span></span>  
  
1.  <span data-ttu-id="c4993-120">建立的組件的類別，衍生自**IMessagingService;** 中**Execute**方法，包含要修改訊息或訊息內容 （如果有的話），您所需的所有邏輯。</span><span class="sxs-lookup"><span data-stu-id="c4993-120">Create an assembly with a class that derives from **IMessagingService;** in the **Execute** method, include all logic necessary to make modifications to the message or the message context (if any).</span></span>  
  
2.  <span data-ttu-id="c4993-121">中新增項目**itineraryServices** Esb.config 檔案，為您的服務加上一節**\<itineraryService\>** GUID 做為項目**識別碼**屬性，做為服務名稱**名稱**屬性，做為類別的完整的名稱**類型**屬性， **Messaging**作為**範圍**屬性，而允許的階段 (例如**OnRampReceive**， **OnRampSend**， **OffRampSend**， **OffRampReceive**， **AllSend**， **AllReceive**，或**所有**) 做為**階段**屬性。</span><span class="sxs-lookup"><span data-stu-id="c4993-121">Add an entry in the **itineraryServices** section of the Esb.config file for your service by adding an **\<itineraryService\>** element with a GUID as the **id** attribute, the name of the service as the **name** attribute, the fully qualified name of the class as the **type** attribute, **Messaging** as the **scope** attribute, and the allowed stage (for example, **OnRampReceive**, **OnRampSend**, **OffRampSend**, **OffRampReceive**, **AllSend**, **AllReceive**, or **All**) as the **stage** attribute.</span></span>  
  
3.  <span data-ttu-id="c4993-122">在全域組件快取中註冊新的組件。</span><span class="sxs-lookup"><span data-stu-id="c4993-122">Register the new assembly in the global assembly cache.</span></span>