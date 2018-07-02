---
title: 使用管線元件選取現有路線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b93c5cb6-071f-485d-b0bb-22f95bafa3d0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2aceef4385652918ee7326709e7838776501e885
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975495"
---
# <a name="using-a-pipeline-component-to-select-an-existing-itinerary"></a><span data-ttu-id="17698-102">使用管線元件選取現有路線</span><span class="sxs-lookup"><span data-stu-id="17698-102">Using a Pipeline Component to Select an Existing Itinerary</span></span>
## <a name="esb-itinerary-selector-pipeline-component"></a><span data-ttu-id="17698-103">ESB 路線選取器管線元件</span><span class="sxs-lookup"><span data-stu-id="17698-103">ESB Itinerary Selector Pipeline Component</span></span>  
 <span data-ttu-id="17698-104">使用泛型路線入口提交的訊息提交沒有路線的標頭。</span><span class="sxs-lookup"><span data-stu-id="17698-104">Messages submitted using generic itinerary on-ramps are submitted without an itinerary header.</span></span> <span data-ttu-id="17698-105">若要解決適當的路線，並將它附加到內送訊息，匝道必須提供一種機制，可以設定為從中央儲存機制存取路線。</span><span class="sxs-lookup"><span data-stu-id="17698-105">To resolve the appropriate itinerary and attach it to the incoming message, the on-ramp must provide a mechanism that can be configured to access itineraries from a central repository.</span></span>  

 <span data-ttu-id="17698-106">ESB 路線選取器管線元件會使用解析程式連接字串，搭配特製化的解析程式，若要解決伺服器端路線 （依預設，SQL Server） 儲存在中央儲存機制的內容。</span><span class="sxs-lookup"><span data-stu-id="17698-106">The ESB Itinerary Selector pipeline component uses a resolver connection string, in conjunction with specialized resolvers, to resolve the content of a server-side itinerary stored in a central repository (by default, SQL Server).</span></span>  

 <span data-ttu-id="17698-107">名稱和版本 （如所表示的 SOAP 標頭），用戶端要求路線中 WCF 入口路線靜態解析程式搭配使用 ESB 路線選取器管線元件時，會從訊息內容和用來選取適當的路線。</span><span class="sxs-lookup"><span data-stu-id="17698-107">When the ESB Itinerary Selector pipeline component is used in WCF on-ramps in conjunction with the ITINERARY-STATIC resolver, the name and version of the itinerary requested by the client (as represented in the SOAP header) is retrieved from the message context and is used to select the appropriate itinerary.</span></span>  

 <span data-ttu-id="17698-108">根據預設，ESB 路線選取器管線元件會位於下列管線：</span><span class="sxs-lookup"><span data-stu-id="17698-108">By default, the ESB Itinerary Selector pipeline component resides in the following pipelines:</span></span>  

- <span data-ttu-id="17698-109">ItinerarySelectReceive</span><span class="sxs-lookup"><span data-stu-id="17698-109">ItinerarySelectReceive</span></span>  

- <span data-ttu-id="17698-110">ItinerarySelectReceivePassthrough</span><span class="sxs-lookup"><span data-stu-id="17698-110">ItinerarySelectReceivePassthrough</span></span>  

- <span data-ttu-id="17698-111">ItinerarySelectReceiveXml</span><span class="sxs-lookup"><span data-stu-id="17698-111">ItinerarySelectReceiveXml</span></span>  

- <span data-ttu-id="17698-112">ItinerarySelectSendReceive</span><span class="sxs-lookup"><span data-stu-id="17698-112">ItinerarySelectSendReceive</span></span>  

  <span data-ttu-id="17698-113">下列各節說明每個元件所執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="17698-113">The following sections describe the steps performed by each component.</span></span>  

## <a name="esb-itinerary-selector-pipeline-component-processing-steps"></a><span data-ttu-id="17698-114">ESB 路線選取器管線元件處理步驟</span><span class="sxs-lookup"><span data-stu-id="17698-114">ESB Itinerary Selector Pipeline Component Processing Steps</span></span>  
 <span data-ttu-id="17698-115">ESB 路線選取器管線元件會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="17698-115">The ESB Itinerary Selector pipeline component executes the following steps:</span></span>  

- <span data-ttu-id="17698-116">提交的合作對象送出訊息，以進行處理。</span><span class="sxs-lookup"><span data-stu-id="17698-116">The submitting party submits a message for processing.</span></span> <span data-ttu-id="17698-117">路線選取器元件會指定為屬性設定的連接字串，讓開發人員的解析程式用以判斷並從路線的存放區，並根據訊息內容或內容中選取適當的路線。</span><span class="sxs-lookup"><span data-stu-id="17698-117">The Itinerary Selector component uses a resolver specified as a property connection string, configured by the developer, to determine and select the appropriate itinerary from the itinerary store, based on message content or context.</span></span>  

- <span data-ttu-id="17698-118">它會驗證路線，並設定特定的屬性，以設定預設值，如果它們是在路線; 為 null例如：</span><span class="sxs-lookup"><span data-stu-id="17698-118">It validates the itinerary and sets specific properties to preset default values if they are null in the itinerary; for example:</span></span>  

  - <span data-ttu-id="17698-119">如果服務計數小於 1，元件就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="17698-119">If Service count is less than 1, the component throws an exception.</span></span>  

  - <span data-ttu-id="17698-120">元件會設定使用的服務計數，而識別碼值的路線根屬性 (**Uuid**)、 開始時間 (**BeginTime**)，以及是否這是單向或雙向的要求 (**IsRequestResponse**)。</span><span class="sxs-lookup"><span data-stu-id="17698-120">The component sets the itinerary root attributes using the values for the Service count, the identifier (**Uuid**), the start time (**BeginTime**), and whether this is a one-way or two-way request (**IsRequestResponse**).</span></span>  

  - <span data-ttu-id="17698-121">元件會驗證服務、 設定的識別碼，設定目前的服務執行個體 （接下來處理服務），並驗證任何相關聯的解析程式的資料。</span><span class="sxs-lookup"><span data-stu-id="17698-121">The component validates the services, sets the identifiers, sets the current service instance (the service to process next), and validates any associated resolvers.</span></span>  

  - <span data-ttu-id="17698-122">元件會設定 Microsoft BizTalk Server 區段的路線，使用下列屬性：</span><span class="sxs-lookup"><span data-stu-id="17698-122">The component sets the Microsoft BizTalk Server segment of the itinerary using the following properties:</span></span>  

    -   <span data-ttu-id="17698-123">**correlationToken**</span><span class="sxs-lookup"><span data-stu-id="17698-123">**correlationToken**</span></span>  

    -   <span data-ttu-id="17698-124">**reqRespTransmitPipelineID**</span><span class="sxs-lookup"><span data-stu-id="17698-124">**reqRespTransmitPipelineID**</span></span>  

    -   <span data-ttu-id="17698-125">**interchangeId**</span><span class="sxs-lookup"><span data-stu-id="17698-125">**interchangeId**</span></span>  

    -   <span data-ttu-id="17698-126">**receiveInstanceId**</span><span class="sxs-lookup"><span data-stu-id="17698-126">**receiveInstanceId**</span></span>  

    -   <span data-ttu-id="17698-127">**epmRRCorrelationToken**</span><span class="sxs-lookup"><span data-stu-id="17698-127">**epmRRCorrelationToken**</span></span>  

  - <span data-ttu-id="17698-128">元件會使用系統 Properties.xsd 結構描述中定義的屬性如下表所示的 BizTalk 訊息內容屬性寫入已修改的路線。</span><span class="sxs-lookup"><span data-stu-id="17698-128">The component writes the modified itinerary to the BizTalk message context properties listed in the following table using the properties defined in the System-Properties.xsd schema.</span></span>  


    |                                           <span data-ttu-id="17698-129">屬性</span><span class="sxs-lookup"><span data-stu-id="17698-129">Properties</span></span>                                           |
    |------------------------------------------------------------------------------------------------|
    |                                   <span data-ttu-id="17698-130">**名稱 = ItineraryHeader**</span><span class="sxs-lookup"><span data-stu-id="17698-130">**Name = ItineraryHeader**</span></span>                                   |
    | <span data-ttu-id="17698-131">**命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span><span class="sxs-lookup"><span data-stu-id="17698-131">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span></span> |


  - <span data-ttu-id="17698-132">元件會升級使用系統 Properties.xsd 結構描述中定義的值如下表所示的四個 BizTalk 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="17698-132">The component promotes the four BizTalk context properties listed in the following table using the values defined in the System-Properties.xsd schema.</span></span>  

    |<span data-ttu-id="17698-133">屬性</span><span class="sxs-lookup"><span data-stu-id="17698-133">Property</span></span>|<span data-ttu-id="17698-134">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="17698-134">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="17698-135">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="17698-135">**ServiceName**</span></span>|<span data-ttu-id="17698-136">路線中所定義的目前服務執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="17698-136">The name of the current service instance defined in the itinerary.</span></span>|  
    |<span data-ttu-id="17698-137">**ServiceType**</span><span class="sxs-lookup"><span data-stu-id="17698-137">**ServiceType**</span></span>|<span data-ttu-id="17698-138">設定為 **協調流程**或是**傳訊**。</span><span class="sxs-lookup"><span data-stu-id="17698-138">Set to either **Orchestration** or **Messaging**.</span></span>|  
    |<span data-ttu-id="17698-139">**IsRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="17698-139">**IsRequestResponse**</span></span>|<span data-ttu-id="17698-140">設定為 **真**或是**False**。</span><span class="sxs-lookup"><span data-stu-id="17698-140">Set to either **True** or **False**.</span></span>|  
    |<span data-ttu-id="17698-141">**ServiceState**</span><span class="sxs-lookup"><span data-stu-id="17698-141">**ServiceState**</span></span>|<span data-ttu-id="17698-142">設定為**暫止**。</span><span class="sxs-lookup"><span data-stu-id="17698-142">Set to **Pending**.</span></span>|  

## <a name="esb-dispatcher-pipeline-component-process-steps"></a><span data-ttu-id="17698-143">ESB 發送器管線元件處理程序步驟</span><span class="sxs-lookup"><span data-stu-id="17698-143">ESB Dispatcher Pipeline Component Process Steps</span></span>  
 <span data-ttu-id="17698-144">ESB 發送器管線元件會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="17698-144">The ESB Dispatcher pipeline component executes the following steps:</span></span>  

-   <span data-ttu-id="17698-145">管理任何類型的路線的步驟執行**Messaging**和前進的路線。</span><span class="sxs-lookup"><span data-stu-id="17698-145">It manages the execution of any itinerary steps of type **Messaging** and advances the itinerary.</span></span> <span data-ttu-id="17698-146">ESB 發送器元件是位置感知和執行訊息處理循環，這可能是根據其位置的邏輯**收到傳入**，**傳送傳輸**，**傳送輸入**，或**接收輸出**。</span><span class="sxs-lookup"><span data-stu-id="17698-146">The ESB Dispatcher component is location-aware and executes logic based on its location in the messaging processing cycle, which could be **Receive Inbound**, **Send Transmit**, **Send Inbound**, or **Receive Outbound**.</span></span> <span data-ttu-id="17698-147">ESB 發送器管線元件會叫用 ESB 路線傳訊服務的 Esb.config 檔案中指定。</span><span class="sxs-lookup"><span data-stu-id="17698-147">The ESB Dispatcher pipeline component invokes ESB itinerary messaging services specified in the Esb.config file.</span></span> <span data-ttu-id="17698-148">根據預設，此元件進行路由與轉換的組態屬性會與下列服務相關聯：</span><span class="sxs-lookup"><span data-stu-id="17698-148">By default, the configuration properties of this component for routing and transformation are associated with the following services:</span></span>  

    -   <span data-ttu-id="17698-149">**Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="17698-149">**Microsoft.Practices.ESB.Services.Transform**.</span></span> <span data-ttu-id="17698-150">此服務會執行對傳入訊息的承載的 BizTalk 對應。</span><span class="sxs-lookup"><span data-stu-id="17698-150">This service executes BizTalk maps against the payload of an inbound message.</span></span> <span data-ttu-id="17698-151">服務會驗證轉換需求，並更新包含的文件規格名稱和訊息類型的 BizTalk 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="17698-151">The service validates transform requirements and updates the BizTalk context properties that contain the document specification name and the message type.</span></span> <span data-ttu-id="17698-152">ESB 發送器執行這項服務，如果這是轉換服務的名稱，在 ESB 發送器管線元件的對應屬性中所顯示的樣子。</span><span class="sxs-lookup"><span data-stu-id="17698-152">The ESB Dispatcher executes this service only if this is the name of the transform service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>  

    -   <span data-ttu-id="17698-153">**Microsoft.Practices.ESB.Services.Routing。**</span><span class="sxs-lookup"><span data-stu-id="17698-153">**Microsoft.Practices.ESB.Services.Routing.**</span></span> <span data-ttu-id="17698-154">此服務會使用解析程式和配接器提供者架構設定適當的端點路由資訊。</span><span class="sxs-lookup"><span data-stu-id="17698-154">This service uses the Resolver and Adapter Provider Framework to set the appropriate endpoint routing information.</span></span> <span data-ttu-id="17698-155">ESB 發送器執行這項服務，如果這是路由服務的名稱，在 ESB 發送器管線元件的對應屬性中所顯示的樣子。</span><span class="sxs-lookup"><span data-stu-id="17698-155">The ESB Dispatcher executes this service only if this is the name of the routing service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>