---
title: 使用管線元件讀取路線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e3b40c7-0f17-4d33-a26f-f51346a98be5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c03e4e48b125d7a8236c66ce36e458dd2d51a6f7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991119"
---
# <a name="using-a-pipeline-component-to-read-an-itinerary"></a><span data-ttu-id="9704b-102">使用管線元件讀取路線</span><span class="sxs-lookup"><span data-stu-id="9704b-102">Using a Pipeline Component to Read an Itinerary</span></span>
<span data-ttu-id="9704b-103">接收管線中的訊息可以包含其定義其處理需求 （用戶端路線） 的 SOAP 標頭中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9704b-103">A message that arrives in a receive pipeline can contain metadata in its SOAP header that defines its processing requirements (client-side itinerary).</span></span> <span data-ttu-id="9704b-104">圖 1 說明如何使用 ESB 路線和 ESB 發送器管線元件。</span><span class="sxs-lookup"><span data-stu-id="9704b-104">Figure 1 illustrates the use of the ESB Itinerary and ESB Dispatcher pipeline components.</span></span>  

 <span data-ttu-id="9704b-105">![管線元件讀取](../esb-toolkit/media/ch4-pipelinecomponentread.gif "第 4 章第 PipelineComponentRead")</span><span class="sxs-lookup"><span data-stu-id="9704b-105">![Pipeline Component Read](../esb-toolkit/media/ch4-pipelinecomponentread.gif "Ch4-PipelineComponentRead")</span></span>  

 <span data-ttu-id="9704b-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="9704b-106">**Figure 1**</span></span>  

 <span data-ttu-id="9704b-107">**ESB 路線管線元件的範例**</span><span class="sxs-lookup"><span data-stu-id="9704b-107">**Example of an ESB Itinerary pipeline component**</span></span>  

 <span data-ttu-id="9704b-108">ESB 路線管線元件可用來擷取中繼資料，從訊息內容屬性，可以定義 ESB 所套用的處理。</span><span class="sxs-lookup"><span data-stu-id="9704b-108">An ESB Itinerary pipeline component can be used to capture the metadata from a message as context properties that can define the processing applied by the ESB.</span></span>  

 <span data-ttu-id="9704b-109">下列各節說明每個元件所執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="9704b-109">The following sections describe the steps performed by each component.</span></span>  

## <a name="esb-itinerary-pipeline-component-process-steps"></a><span data-ttu-id="9704b-110">ESB 路線的管線元件的程序步驟</span><span class="sxs-lookup"><span data-stu-id="9704b-110">ESB Itinerary Pipeline Component Process Steps</span></span>  
 <span data-ttu-id="9704b-111">[圖 1] 所示的範例中，在 ESB 路線管線元件會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9704b-111">In the example shown in Figure 1, the ESB Itinerary pipeline component executes the following steps:</span></span>  

- <span data-ttu-id="9704b-112">它會讀取路線 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="9704b-112">It reads the itinerary SOAP header.</span></span> <span data-ttu-id="9704b-113">提交的合作對象設定路線他或她將訊息提交時，填入 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="9704b-113">The submitting party sets the itinerary by populating the SOAP header when he or she submits the message.</span></span> <span data-ttu-id="9704b-114">BizTalk 訊息內容屬性的一系列代表 SOAP 標頭;這些屬性會因所使用的 Web 服務配接器的類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="9704b-114">A series of BizTalk message context properties represent the SOAP header; these properties vary, depending on the type of Web service adapter that is used.</span></span> <span data-ttu-id="9704b-115">以下是相關的 Web 服務配接器：</span><span class="sxs-lookup"><span data-stu-id="9704b-115">The following are the relevant Web service adapters:</span></span>  

  - <span data-ttu-id="9704b-116">**WCF 配接器。**</span><span class="sxs-lookup"><span data-stu-id="9704b-116">**WCF adapter.**</span></span> <span data-ttu-id="9704b-117">此配接器會剖析 SOAP 標頭，並於其中填入下表所列的 BizTalk 訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9704b-117">This adapter parses the SOAP headers and populates the BizTalk message context properties listed in the following table.</span></span>  


    |                                  <span data-ttu-id="9704b-118">屬性</span><span class="sxs-lookup"><span data-stu-id="9704b-118">Properties</span></span>                                  |
    |------------------------------------------------------------------------------|
    |                             <span data-ttu-id="9704b-119">**名稱 = 路線**</span><span class="sxs-lookup"><span data-stu-id="9704b-119">**Name = Itinerary**</span></span>                             |
    | <span data-ttu-id="9704b-120">**命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary**</span><span class="sxs-lookup"><span data-stu-id="9704b-120">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary**</span></span> |

    > [!NOTE]
    >  <span data-ttu-id="9704b-121">根據預設，Windows Communication Foundation (WCF) 配接器會使用名為的 ItineraryDescription.xsd （此結構描述用來產生 ESB 路線 SOAP 標頭） 的結構描述根名稱做為 BizTalk 內容**名稱**引數，也會使用結構描述的目標命名空間，做為 BizTalk 內容**命名空間**引數。</span><span class="sxs-lookup"><span data-stu-id="9704b-121">By default, the Windows Communication Foundation (WCF) adapter uses the root name of the schema named ItineraryDescription.xsd (this schema is used to generate the ESB Itinerary SOAP header) as the BizTalk context **Name** argument, and it uses the target namespace of the schema as the BizTalk context **Namespace** argument.</span></span>  

  - <span data-ttu-id="9704b-122">**SOAP 配接器。**</span><span class="sxs-lookup"><span data-stu-id="9704b-122">**SOAP adapter.**</span></span> <span data-ttu-id="9704b-123">此配接器會剖析 SOAP 標頭，並於其中填入下表所列的 BizTalk 訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9704b-123">This adapter parses the SOAP headers and populates the BizTalk message context properties listed in the following table.</span></span>  


    |                              <span data-ttu-id="9704b-124">屬性</span><span class="sxs-lookup"><span data-stu-id="9704b-124">Properties</span></span>                              |
    |----------------------------------------------------------------------|
    |                         <span data-ttu-id="9704b-125">**名稱 = 路線**</span><span class="sxs-lookup"><span data-stu-id="9704b-125">**Name = Itinerary**</span></span>                         |
    | <span data-ttu-id="9704b-126">**命名空間 = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**</span><span class="sxs-lookup"><span data-stu-id="9704b-126">**Namespace = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**</span></span> |

    > [!NOTE]
    >  <span data-ttu-id="9704b-127">根據預設，SOAP 配接器會使用名為的 Itinerary.xsd （此結構描述用來產生 ESB 路線 SOAP 標頭） 的結構描述根名稱做為 BizTalk 內容**名稱**引數，並使用的 SOAP 標頭，因為命名空間BizTalk 內容**命名空間**引數。</span><span class="sxs-lookup"><span data-stu-id="9704b-127">By default, the SOAP Adapter uses the root name of the schema named Itinerary.xsd (this schema is used to generate the ESB Itinerary SOAP header) as the BizTalk context **Name** argument, and it uses the namespace of the SOAP header as the BizTalk context **Namespace** argument.</span></span>  

- <span data-ttu-id="9704b-128">它從訊息內容中移除原始的路線值。</span><span class="sxs-lookup"><span data-stu-id="9704b-128">It removes the original itinerary value from the message context.</span></span>  

- <span data-ttu-id="9704b-129">它會驗證路線，並設定特定的屬性，以設定預設值，如果它們是在路線; 為 null例如：</span><span class="sxs-lookup"><span data-stu-id="9704b-129">It validates the itinerary and sets specific properties to preset default values if they are null in the itinerary; for example:</span></span>  

  - <span data-ttu-id="9704b-130">如果服務計數小於 1，元件就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9704b-130">If Service count is less than 1, the component throws an exception.</span></span>  

  - <span data-ttu-id="9704b-131">元件會設定使用的服務計數，而識別碼值的路線根屬性 (**Uuid**)、 開始時間 (**BeginTime**)，以及是否這是單向或雙向的要求 (**IsRequestResponse**)。</span><span class="sxs-lookup"><span data-stu-id="9704b-131">The component sets the itinerary root attributes using the values for the Service count, the identifier (**Uuid**), the start time (**BeginTime**), and whether this is a one-way or two-way request (**IsRequestResponse**).</span></span>  

  - <span data-ttu-id="9704b-132">元件會驗證服務、 設定的識別碼，設定目前的服務執行個體 （接下來處理服務），並驗證任何相關聯的解析程式的資料。</span><span class="sxs-lookup"><span data-stu-id="9704b-132">The component validates the services, sets the identifiers, sets the current service instance (the service to process next), and validates any associated resolvers.</span></span>  

  - <span data-ttu-id="9704b-133">元件會設定 BizTalk 區段的路線，使用下列屬性：</span><span class="sxs-lookup"><span data-stu-id="9704b-133">The component sets the BizTalk Segment of the itinerary using the following properties:</span></span>  

    -   <span data-ttu-id="9704b-134">**correlationToken**</span><span class="sxs-lookup"><span data-stu-id="9704b-134">**correlationToken**</span></span>  

    -   <span data-ttu-id="9704b-135">**reqRespTransmitPipelineID**</span><span class="sxs-lookup"><span data-stu-id="9704b-135">**reqRespTransmitPipelineID**</span></span>  

    -   <span data-ttu-id="9704b-136">**interchangeId**</span><span class="sxs-lookup"><span data-stu-id="9704b-136">**interchangeId**</span></span>  

    -   <span data-ttu-id="9704b-137">**receiveInstanceId**</span><span class="sxs-lookup"><span data-stu-id="9704b-137">**receiveInstanceId**</span></span>  

    -   <span data-ttu-id="9704b-138">**epmRRCorrelationToken**</span><span class="sxs-lookup"><span data-stu-id="9704b-138">**epmRRCorrelationToken**</span></span>  

  - <span data-ttu-id="9704b-139">元件會使用系統 Properties.xsd 結構描述中定義的屬性如下表所示的 BizTalk 訊息內容屬性寫入已修改的路線。</span><span class="sxs-lookup"><span data-stu-id="9704b-139">The component writes the modified itinerary to the BizTalk message context properties listed in the following table using the properties defined in the System-Properties.xsd schema.</span></span>  


    |                                           <span data-ttu-id="9704b-140">屬性</span><span class="sxs-lookup"><span data-stu-id="9704b-140">Properties</span></span>                                           |
    |------------------------------------------------------------------------------------------------|
    |                                   <span data-ttu-id="9704b-141">**名稱 = ItineraryHeader**</span><span class="sxs-lookup"><span data-stu-id="9704b-141">**Name = ItineraryHeader**</span></span>                                   |
    | <span data-ttu-id="9704b-142">**命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span><span class="sxs-lookup"><span data-stu-id="9704b-142">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span></span> |


  - <span data-ttu-id="9704b-143">元件會升級使用系統 Properties.xsd 結構描述中定義的值如下表所示的四個 BizTalk 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9704b-143">The component promotes the four BizTalk context properties listed in the following table using the values defined in the System-Properties.xsd schema.</span></span>  

    |<span data-ttu-id="9704b-144">屬性</span><span class="sxs-lookup"><span data-stu-id="9704b-144">Property</span></span>|<span data-ttu-id="9704b-145">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="9704b-145">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="9704b-146">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="9704b-146">**ServiceName**</span></span>|<span data-ttu-id="9704b-147">路線中所定義的目前服務執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="9704b-147">The name of the current service instance defined in the itinerary.</span></span>|  
    |<span data-ttu-id="9704b-148">**ServiceType**</span><span class="sxs-lookup"><span data-stu-id="9704b-148">**ServiceType**</span></span>|<span data-ttu-id="9704b-149">設定為 **協調流程**或**傳訊**</span><span class="sxs-lookup"><span data-stu-id="9704b-149">Set to either **Orchestration** or **Messaging**</span></span>|  
    |<span data-ttu-id="9704b-150">**IsRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="9704b-150">**IsRequestResponse**</span></span>|<span data-ttu-id="9704b-151">設定為 **真**或**False**</span><span class="sxs-lookup"><span data-stu-id="9704b-151">Set to either **True** or **False**</span></span>|  
    |<span data-ttu-id="9704b-152">**ServiceState**</span><span class="sxs-lookup"><span data-stu-id="9704b-152">**ServiceState**</span></span>|<span data-ttu-id="9704b-153">若要設定**暫止**</span><span class="sxs-lookup"><span data-stu-id="9704b-153">Set to **Pending**</span></span>|  

## <a name="esb-dispatcher-pipeline-component-process-steps"></a><span data-ttu-id="9704b-154">ESB 發送器管線元件處理程序步驟</span><span class="sxs-lookup"><span data-stu-id="9704b-154">ESB Dispatcher Pipeline Component Process Steps</span></span>  
 <span data-ttu-id="9704b-155">在 [圖 1] 所示的範例中，ESB 發送器管線元件會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9704b-155">In the example shown in Figure 1, the ESB Dispatcher pipeline component executes the following steps:</span></span>  

- <span data-ttu-id="9704b-156">管理任何類型的路線的步驟執行**Messaging**和前進的路線。</span><span class="sxs-lookup"><span data-stu-id="9704b-156">It manages the execution of any itinerary steps of type **Messaging** and advances the itinerary.</span></span> <span data-ttu-id="9704b-157">ESB 發送器元件是位置感知和執行訊息處理循環，這可能是根據其位置的邏輯**接收輸入、 傳送傳輸**，**傳送輸入**，或**接收輸出**。</span><span class="sxs-lookup"><span data-stu-id="9704b-157">The ESB Dispatcher component is location-aware and executes logic based on its location in the messaging processing cycle, which could be **Receive Inbound, Send Transmit**, **Send Inbound**, or **Receive Outbound**.</span></span> <span data-ttu-id="9704b-158">ESB 發送器管線元件會叫用 ESB 路線傳訊服務的 Esb.config 檔案中指定。</span><span class="sxs-lookup"><span data-stu-id="9704b-158">The ESB Dispatcher pipeline component invokes ESB itinerary messaging services specified in the Esb.config file.</span></span> <span data-ttu-id="9704b-159">根據預設，此元件進行路由與轉換的組態屬性會與下列服務相關聯：</span><span class="sxs-lookup"><span data-stu-id="9704b-159">By default, the configuration properties of this component for routing and transformation are associated with the following services:</span></span>  

  - <span data-ttu-id="9704b-160">**Microsoft.Practices.ESB.Services.Transform。**</span><span class="sxs-lookup"><span data-stu-id="9704b-160">**Microsoft.Practices.ESB.Services.Transform.**</span></span> <span data-ttu-id="9704b-161">此服務會執行對傳入訊息的承載的 BizTalk 對應。</span><span class="sxs-lookup"><span data-stu-id="9704b-161">This service executes BizTalk maps against the payload of an inbound message.</span></span> <span data-ttu-id="9704b-162">服務會驗證轉換需求，並更新包含的文件規格名稱和訊息類型的 BizTalk 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9704b-162">The service validates transform requirements and updates the BizTalk context properties that contain the document specification name and the message type.</span></span> <span data-ttu-id="9704b-163">ESB 發送器執行這項服務，如果這是轉換服務的名稱，在 ESB 發送器管線元件的對應屬性中所顯示的樣子。</span><span class="sxs-lookup"><span data-stu-id="9704b-163">The ESB Dispatcher executes this service only if this is the name of the transform service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>  

  - <span data-ttu-id="9704b-164"><strong>Microsoft.Practices.ESB.Services.Routing。</strong>這項服務使用的解析程式和配接器提供者架構來設定適當的端點路由資訊。</span><span class="sxs-lookup"><span data-stu-id="9704b-164"><strong>Microsoft.Practices.ESB.Services.Routing.</strong>This service uses the Resolver and Adapter Provider Framework to set the appropriate endpoint routing information.</span></span> <span data-ttu-id="9704b-165">ESB 發送器執行這項服務，如果這是路由服務的名稱，在 ESB 發送器管線元件的對應屬性中所顯示的樣子。</span><span class="sxs-lookup"><span data-stu-id="9704b-165">The ESB Dispatcher executes this service only if this is the name of the routing service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>
