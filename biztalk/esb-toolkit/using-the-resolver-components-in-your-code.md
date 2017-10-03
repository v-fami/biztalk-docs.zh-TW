---
title: "在您的程式碼中使用解析程式元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d197cb28-78a9-4c8a-872b-f61ef15e6622
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 220ae4983f2fcbf60f6de02f818095fe5c0c50a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-resolver-components-in-your-code"></a><span data-ttu-id="bdd0a-102">在您的程式碼中使用解析程式元件</span><span class="sxs-lookup"><span data-stu-id="bdd0a-102">Using the Resolver Components in Your Code</span></span>
<span data-ttu-id="bdd0a-103">動態轉換代理程式的下列程式碼片段會顯示預設在 just-in-time (JIT) 解析功能。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-103">The following code fragment from the dynamic transformation agent shows the default just-in-time (JIT) resolution functionality.</span></span> <span data-ttu-id="bdd0a-104">您可以輕鬆實作解析您自己的應用程式中使用類似的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-104">You can easily implement resolution in your own application by using similar code.</span></span>  
  
```  
  
//XLANGs  
itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
resolvers = step.ItineraryStep.ResolverCollection;  
resolvers.MoveNext();  
resolver = resolvers.Current;  
  
// Pass the resolver configuration to the Resolver mgr for resolution.  
resolverDictionary = Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage, resolver);  
  
// Set the transform type.  
transformType = resolverDictionary.Item("Resolver.TransformType");  
```  
  
 <span data-ttu-id="bdd0a-105">在上述清單中，**解決**方法**ResolverMgr**類別會傳回**字典**物件，其中包含所有預設解析屬性及其解析的值。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-105">In the preceding listing, the **Resolve** method of the **ResolverMgr** class returns a **Dictionary** object that contains all the default resolution properties and their resolved values.</span></span> <span data-ttu-id="bdd0a-106">任何自訂解決器可以新增自訂屬性至**字典**物件，執行這會讓這些屬性可供任何自訂計劃的服務。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-106">Any custom resolver can add custom properties to the **Dictionary** object; doing this makes those properties available to any custom itinerary service.</span></span>  
  
 <span data-ttu-id="bdd0a-107">下表顯示可以選擇性地包含在解析程式所填入的屬性[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-107">The following table shows the properties that can be optionally populated by the resolvers included in the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="bdd0a-108">任何路線服務可以擷取這些屬性值擷取它們傳回**字典**物件。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-108">Any itinerary service can retrieve these property values by extracting them from the returned **Dictionary** object.</span></span>  
  
 <span data-ttu-id="bdd0a-109">**屬性**:</span><span class="sxs-lookup"><span data-stu-id="bdd0a-109">**Properties**:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="bdd0a-110">**Resolver.Action**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-110">**Resolver.Action**</span></span>|<span data-ttu-id="bdd0a-111">**Resolver.ActionField**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-111">**Resolver.ActionField**</span></span>|<span data-ttu-id="bdd0a-112">**Resolver.DocumentSpecName**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-112">**Resolver.DocumentSpecName**</span></span>|  
|<span data-ttu-id="bdd0a-113">**Resolver.Success**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-113">**Resolver.Success**</span></span>|<span data-ttu-id="bdd0a-114">**Resolver.EndpointConfig**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-114">**Resolver.EndpointConfig**</span></span>|<span data-ttu-id="bdd0a-115">**Resolver.DocumentSpecStrongName**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-115">**Resolver.DocumentSpecStrongName**</span></span>|  
|<span data-ttu-id="bdd0a-116">**Resolver.FixJaxRpc**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-116">**Resolver.FixJaxRpc**</span></span>|<span data-ttu-id="bdd0a-117">**Resolver.InboundTransportType**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-117">**Resolver.InboundTransportType**</span></span>|<span data-ttu-id="bdd0a-118">**Resolver.EpmRRCorrelationToken**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-118">**Resolver.EpmRRCorrelationToken**</span></span>|  
|<span data-ttu-id="bdd0a-119">**Resolver.InterchangeId**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-119">**Resolver.InterchangeId**</span></span>|<span data-ttu-id="bdd0a-120">**Resolver.IsRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-120">**Resolver.IsRequestResponse**</span></span>|<span data-ttu-id="bdd0a-121">**Resolver.InboundTransportLocation**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-121">**Resolver.InboundTransportLocation**</span></span>|  
|<span data-ttu-id="bdd0a-122">**Resolver.MessageType**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-122">**Resolver.MessageType**</span></span>|<span data-ttu-id="bdd0a-123">**Resolver.MethodName**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-123">**Resolver.MethodName**</span></span>|<span data-ttu-id="bdd0a-124">**Resolver.MessageExchangePattern**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-124">**Resolver.MessageExchangePattern**</span></span>|  
|<span data-ttu-id="bdd0a-125">**Resolver.ReceivePortName**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-125">**Resolver.ReceivePortName**</span></span>|<span data-ttu-id="bdd0a-126">**Resolver.TransportLocation**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-126">**Resolver.TransportLocation**</span></span>|<span data-ttu-id="bdd0a-127">**Resolver.OutboundTransportCLSID**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-127">**Resolver.OutboundTransportCLSID**</span></span>|  
|<span data-ttu-id="bdd0a-128">**Resolver.TransformType**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-128">**Resolver.TransformType**</span></span>|<span data-ttu-id="bdd0a-129">**Resolver.TargetNamespace**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-129">**Resolver.TargetNamespace**</span></span>|<span data-ttu-id="bdd0a-130">**Resolver.ReceiveLocationName**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-130">**Resolver.ReceiveLocationName**</span></span>|  
|<span data-ttu-id="bdd0a-131">**Resolver.TransportType**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-131">**Resolver.TransportType**</span></span>|<span data-ttu-id="bdd0a-132">**Resolver.TransportNamespace**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-132">**Resolver.TransportNamespace**</span></span>|<span data-ttu-id="bdd0a-133">**Resolver.WindowUserField**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-133">**Resolver.WindowUserField**</span></span>|  
|<span data-ttu-id="bdd0a-134">**Resolver.CacheTimeout**</span><span class="sxs-lookup"><span data-stu-id="bdd0a-134">**Resolver.CacheTimeout**</span></span>|||  
  
 <span data-ttu-id="bdd0a-135">之後的解析程式管理員會傳回**字典**物件執行個體，配接器管理員設定訊息的特定 BizTalk 配接器內容屬性。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-135">After the resolver manager returns the **Dictionary** object instance, the adapter manager sets the specific BizTalk Adapter Context properties of the message.</span></span> <span data-ttu-id="bdd0a-136">路由的代理程式的下列程式碼片段示範如何使用配接器管理員來設定端點的屬性外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-136">The following code fragment from the routing agent demonstrates how you can use the adapter manager to set the endpoint properties of the outgoing message.</span></span>  
  
```  
  
//XLANGs  
// Set the transport properties.  
transportLocation = resolverDictionary.Item("Resolver.TransportLocation");  
transportType = resolverDictionary.Item("Resolver.TransportType");  
  
// Create the delivery message.  
DeliveryMessage = InboundMessage;  
  
// Call the adapter manager to set all necessary properties on the message.  
Microsoft.Practices.ESB.Adapter.AdapterMgr.SetEndpoint(  
                                resolverDictionary,DeliveryMessage);  
  
// Set the delivery port address.  
DeliveryPort(Microsoft.XLANGs.BaseTypes.Address) = transportLocation;  
DeliveryPort(Microsoft.XLANGs.BaseTypes.TransportType) = transportType;  
```  
  
 <span data-ttu-id="bdd0a-137">路由的代理程式的下列程式碼片段示範如何使用自訂管線元件中的從配接器管理員來設定外寄訊息的端點內容。</span><span class="sxs-lookup"><span data-stu-id="bdd0a-137">The following code fragment from the routing agent demonstrates how to use the adapter manager from within a custom pipeline component to set the endpoint properties of an outgoing message.</span></span>  
  
```csharp  
// Resolve the configuration for routing.  
ResolverDictionary = ResolverMgr.Resolve(info, pInMsg, pContext);  
  
// Call the adapter manager to set all required message properties.  
AdapterMgr.SetEndpoint(ResolverDictionary, pInMsg.Context);  
```