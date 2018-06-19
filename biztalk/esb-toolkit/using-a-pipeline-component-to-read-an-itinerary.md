---
title: 使用管線元件讀取行程 |Microsoft 文件
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
ms.openlocfilehash: bceec4df732247be043e006b52c7abbfbf6a6b24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22296190"
---
# <a name="using-a-pipeline-component-to-read-an-itinerary"></a><span data-ttu-id="cb866-102">使用管線元件讀取行程</span><span class="sxs-lookup"><span data-stu-id="cb866-102">Using a Pipeline Component to Read an Itinerary</span></span>
<span data-ttu-id="cb866-103">接收管線中的訊息可以包含其定義了其處理需求 （用戶端路線） 的 SOAP 標頭中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cb866-103">A message that arrives in a receive pipeline can contain metadata in its SOAP header that defines its processing requirements (client-side itinerary).</span></span> <span data-ttu-id="cb866-104">圖 1 說明如何使用 「 ESB 行程和 ESB 發送器管線元件。</span><span class="sxs-lookup"><span data-stu-id="cb866-104">Figure 1 illustrates the use of the ESB Itinerary and ESB Dispatcher pipeline components.</span></span>  
  
 <span data-ttu-id="cb866-105">![管線元件讀取](../esb-toolkit/media/ch4-pipelinecomponentread.gif "第 4 章第 PipelineComponentRead")</span><span class="sxs-lookup"><span data-stu-id="cb866-105">![Pipeline Component Read](../esb-toolkit/media/ch4-pipelinecomponentread.gif "Ch4-PipelineComponentRead")</span></span>  
  
 <span data-ttu-id="cb866-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="cb866-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="cb866-107">**ESB 行程管線元件的範例**</span><span class="sxs-lookup"><span data-stu-id="cb866-107">**Example of an ESB Itinerary pipeline component**</span></span>  
  
 <span data-ttu-id="cb866-108">ESB 行程管線元件可以用來擷取中繼資料，從訊息內容屬性，可以定義 ESB 所套用的處理。</span><span class="sxs-lookup"><span data-stu-id="cb866-108">An ESB Itinerary pipeline component can be used to capture the metadata from a message as context properties that can define the processing applied by the ESB.</span></span>  
  
 <span data-ttu-id="cb866-109">下列章節說明每個元件所執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="cb866-109">The following sections describe the steps performed by each component.</span></span>  
  
## <a name="esb-itinerary-pipeline-component-process-steps"></a><span data-ttu-id="cb866-110">ESB 路線的管線元件處理序的步驟</span><span class="sxs-lookup"><span data-stu-id="cb866-110">ESB Itinerary Pipeline Component Process Steps</span></span>  
 <span data-ttu-id="cb866-111">在圖 1 所示的範例中，ESB 行程管線元件會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cb866-111">In the example shown in Figure 1, the ESB Itinerary pipeline component executes the following steps:</span></span>  
  
-   <span data-ttu-id="cb866-112">它會讀取行程 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="cb866-112">It reads the itinerary SOAP header.</span></span> <span data-ttu-id="cb866-113">正在提交的合作對象，設定路線他或她將訊息提交時，填入 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="cb866-113">The submitting party sets the itinerary by populating the SOAP header when he or she submits the message.</span></span> <span data-ttu-id="cb866-114">BizTalk 訊息內容屬性的一系列代表 SOAP 標頭。這些屬性會因所使用的 Web 服務配接器類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="cb866-114">A series of BizTalk message context properties represent the SOAP header; these properties vary, depending on the type of Web service adapter that is used.</span></span> <span data-ttu-id="cb866-115">以下是相關的 Web 服務配接器：</span><span class="sxs-lookup"><span data-stu-id="cb866-115">The following are the relevant Web service adapters:</span></span>  
  
    -   <span data-ttu-id="cb866-116">**WCF 配接器。**</span><span class="sxs-lookup"><span data-stu-id="cb866-116">**WCF adapter.**</span></span> <span data-ttu-id="cb866-117">此配接器會剖析 SOAP 標頭，並於其中填入下表所列的 BizTalk 訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="cb866-117">This adapter parses the SOAP headers and populates the BizTalk message context properties listed in the following table.</span></span>  
  
        |<span data-ttu-id="cb866-118">屬性</span><span class="sxs-lookup"><span data-stu-id="cb866-118">Properties</span></span>|  
        |----------------|  
        |<span data-ttu-id="cb866-119">**名稱 = 路線**</span><span class="sxs-lookup"><span data-stu-id="cb866-119">**Name = Itinerary**</span></span>|  
        |<span data-ttu-id="cb866-120">**命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary**</span><span class="sxs-lookup"><span data-stu-id="cb866-120">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary**</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="cb866-121">根據預設，Windows Communication Foundation (WCF) 配接器會使用名為的 ItineraryDescription.xsd （此結構描述用來產生 ESB 行程 SOAP 標頭） 的結構描述的根名稱做為 BizTalk 內容**名稱**引數，它是使用 BizTalk 內容結構描述的目標命名空間和**命名空間**引數。</span><span class="sxs-lookup"><span data-stu-id="cb866-121">By default, the Windows Communication Foundation (WCF) adapter uses the root name of the schema named ItineraryDescription.xsd (this schema is used to generate the ESB Itinerary SOAP header) as the BizTalk context **Name** argument, and it uses the target namespace of the schema as the BizTalk context **Namespace** argument.</span></span>  
  
    -   <span data-ttu-id="cb866-122">**SOAP 配接器。**</span><span class="sxs-lookup"><span data-stu-id="cb866-122">**SOAP adapter.**</span></span> <span data-ttu-id="cb866-123">此配接器會剖析 SOAP 標頭，並於其中填入下表所列的 BizTalk 訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="cb866-123">This adapter parses the SOAP headers and populates the BizTalk message context properties listed in the following table.</span></span>  
  
        |<span data-ttu-id="cb866-124">屬性</span><span class="sxs-lookup"><span data-stu-id="cb866-124">Properties</span></span>|  
        |----------------|  
        |<span data-ttu-id="cb866-125">**名稱 = 路線**</span><span class="sxs-lookup"><span data-stu-id="cb866-125">**Name = Itinerary**</span></span>|  
        |<span data-ttu-id="cb866-126">**命名空間 = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**</span><span class="sxs-lookup"><span data-stu-id="cb866-126">**Namespace = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="cb866-127">根據預設，SOAP 配接器會使用名為的 Itinerary.xsd （此結構描述用來產生 ESB 行程 SOAP 標頭） 的結構描述的根名稱做為 BizTalk 內容**名稱**引數，並使用做為 SOAP 標頭的命名空間BizTalk 內容**命名空間**引數。</span><span class="sxs-lookup"><span data-stu-id="cb866-127">By default, the SOAP Adapter uses the root name of the schema named Itinerary.xsd (this schema is used to generate the ESB Itinerary SOAP header) as the BizTalk context **Name** argument, and it uses the namespace of the SOAP header as the BizTalk context **Namespace** argument.</span></span>  
  
-   <span data-ttu-id="cb866-128">會從訊息內容中移除原始路線的值。</span><span class="sxs-lookup"><span data-stu-id="cb866-128">It removes the original itinerary value from the message context.</span></span>  
  
-   <span data-ttu-id="cb866-129">它會驗證路線，並設定特定的屬性，以設定預設值，如果它們是在路線; null例如：</span><span class="sxs-lookup"><span data-stu-id="cb866-129">It validates the itinerary and sets specific properties to preset default values if they are null in the itinerary; for example:</span></span>  
  
    -   <span data-ttu-id="cb866-130">如果服務計數小於 1，元件就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cb866-130">If Service count is less than 1, the component throws an exception.</span></span>  
  
    -   <span data-ttu-id="cb866-131">元件會設定服務計數，識別項使用的值的路線根屬性 (**Uuid**)、 開始時間 (**BeginTime**)，以及是否這是單向或雙向的要求 (**IsRequestResponse**)。</span><span class="sxs-lookup"><span data-stu-id="cb866-131">The component sets the itinerary root attributes using the values for the Service count, the identifier (**Uuid**), the start time (**BeginTime**), and whether this is a one-way or two-way request (**IsRequestResponse**).</span></span>  
  
    -   <span data-ttu-id="cb866-132">元件會驗證服務、 設定的識別碼，設定目前的服務執行個體 （接下來處理服務），和會驗證任何相關聯的解析程式。</span><span class="sxs-lookup"><span data-stu-id="cb866-132">The component validates the services, sets the identifiers, sets the current service instance (the service to process next), and validates any associated resolvers.</span></span>  
  
    -   <span data-ttu-id="cb866-133">元件會先設定 BizTalk 區段的路線，使用下列屬性：</span><span class="sxs-lookup"><span data-stu-id="cb866-133">The component sets the BizTalk Segment of the itinerary using the following properties:</span></span>  
  
        -   <span data-ttu-id="cb866-134">**correlationToken**</span><span class="sxs-lookup"><span data-stu-id="cb866-134">**correlationToken**</span></span>  
  
        -   <span data-ttu-id="cb866-135">**reqRespTransmitPipelineID**</span><span class="sxs-lookup"><span data-stu-id="cb866-135">**reqRespTransmitPipelineID**</span></span>  
  
        -   <span data-ttu-id="cb866-136">**interchangeId**</span><span class="sxs-lookup"><span data-stu-id="cb866-136">**interchangeId**</span></span>  
  
        -   <span data-ttu-id="cb866-137">**receiveInstanceId**</span><span class="sxs-lookup"><span data-stu-id="cb866-137">**receiveInstanceId**</span></span>  
  
        -   <span data-ttu-id="cb866-138">**epmRRCorrelationToken**</span><span class="sxs-lookup"><span data-stu-id="cb866-138">**epmRRCorrelationToken**</span></span>  
  
    -   <span data-ttu-id="cb866-139">元件會使用系統 Properties.xsd 結構描述中定義的屬性如下表所示的 BizTalk 訊息內容屬性寫入已修改的路線。</span><span class="sxs-lookup"><span data-stu-id="cb866-139">The component writes the modified itinerary to the BizTalk message context properties listed in the following table using the properties defined in the System-Properties.xsd schema.</span></span>  
  
        |<span data-ttu-id="cb866-140">屬性</span><span class="sxs-lookup"><span data-stu-id="cb866-140">Properties</span></span>|  
        |----------------|  
        |<span data-ttu-id="cb866-141">**名稱 = ItineraryHeader**</span><span class="sxs-lookup"><span data-stu-id="cb866-141">**Name = ItineraryHeader**</span></span>|  
        |<span data-ttu-id="cb866-142">**命名空間 = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span><span class="sxs-lookup"><span data-stu-id="cb866-142">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span></span>|  
  
    -   <span data-ttu-id="cb866-143">元件會升級使用系統 Properties.xsd 結構描述中定義的值如下表所示的四個 BizTalk 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="cb866-143">The component promotes the four BizTalk context properties listed in the following table using the values defined in the System-Properties.xsd schema.</span></span>  
  
        |<span data-ttu-id="cb866-144">屬性</span><span class="sxs-lookup"><span data-stu-id="cb866-144">Property</span></span>|<span data-ttu-id="cb866-145">值</span><span class="sxs-lookup"><span data-stu-id="cb866-145">Value</span></span>|  
        |--------------|-----------|  
        |<span data-ttu-id="cb866-146">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="cb866-146">**ServiceName**</span></span>|<span data-ttu-id="cb866-147">目前行程中定義的服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="cb866-147">The name of the current service instance defined in the itinerary.</span></span>|  
        |<span data-ttu-id="cb866-148">**ServiceType**</span><span class="sxs-lookup"><span data-stu-id="cb866-148">**ServiceType**</span></span>|<span data-ttu-id="cb866-149">設定為 **協調流程**或**傳訊**</span><span class="sxs-lookup"><span data-stu-id="cb866-149">Set to either **Orchestration** or **Messaging**</span></span>|  
        |<span data-ttu-id="cb866-150">**IsRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="cb866-150">**IsRequestResponse**</span></span>|<span data-ttu-id="cb866-151">設定為  **True**或**False**</span><span class="sxs-lookup"><span data-stu-id="cb866-151">Set to either **True** or **False**</span></span>|  
        |<span data-ttu-id="cb866-152">**ServiceState**</span><span class="sxs-lookup"><span data-stu-id="cb866-152">**ServiceState**</span></span>|<span data-ttu-id="cb866-153">設定為**暫止**</span><span class="sxs-lookup"><span data-stu-id="cb866-153">Set to **Pending**</span></span>|  
  
## <a name="esb-dispatcher-pipeline-component-process-steps"></a><span data-ttu-id="cb866-154">ESB 發送器管線元件處理步驟</span><span class="sxs-lookup"><span data-stu-id="cb866-154">ESB Dispatcher Pipeline Component Process Steps</span></span>  
 <span data-ttu-id="cb866-155">在圖 1 所示的範例中，ESB 發送器管線元件會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cb866-155">In the example shown in Figure 1, the ESB Dispatcher pipeline component executes the following steps:</span></span>  
  
-   <span data-ttu-id="cb866-156">它會管理任何類型的路線的步驟執行**傳訊**，並往前移路線。</span><span class="sxs-lookup"><span data-stu-id="cb866-156">It manages the execution of any itinerary steps of type **Messaging** and advances the itinerary.</span></span> <span data-ttu-id="cb866-157">ESB 發送器元件是位置感知和執行在訊息處理循環，這可能會根據其位置的邏輯**接收輸入，傳送傳輸**，**傳送輸入**，或**接收輸出**。</span><span class="sxs-lookup"><span data-stu-id="cb866-157">The ESB Dispatcher component is location-aware and executes logic based on its location in the messaging processing cycle, which could be **Receive Inbound, Send Transmit**, **Send Inbound**, or **Receive Outbound**.</span></span> <span data-ttu-id="cb866-158">ESB 發送器管線元件會叫用路線 ESB Esb.config 檔案中指定訊息服務。</span><span class="sxs-lookup"><span data-stu-id="cb866-158">The ESB Dispatcher pipeline component invokes ESB itinerary messaging services specified in the Esb.config file.</span></span> <span data-ttu-id="cb866-159">根據預設，此路由和轉換元件的組態屬性與相關聯的下列服務：</span><span class="sxs-lookup"><span data-stu-id="cb866-159">By default, the configuration properties of this component for routing and transformation are associated with the following services:</span></span>  
  
    -   <span data-ttu-id="cb866-160">**Microsoft.Practices.ESB.Services.Transform。**</span><span class="sxs-lookup"><span data-stu-id="cb866-160">**Microsoft.Practices.ESB.Services.Transform.**</span></span> <span data-ttu-id="cb866-161">此服務會執行對傳入訊息的裝載 BizTalk 對應。</span><span class="sxs-lookup"><span data-stu-id="cb866-161">This service executes BizTalk maps against the payload of an inbound message.</span></span> <span data-ttu-id="cb866-162">服務驗證的轉換需求，並更新 BizTalk 內容屬性包含文件規格名稱和訊息類型。</span><span class="sxs-lookup"><span data-stu-id="cb866-162">The service validates transform requirements and updates the BizTalk context properties that contain the document specification name and the message type.</span></span> <span data-ttu-id="cb866-163">ESB 發送器會執行這項服務，才出現在 ESB 發送器管線元件的對應屬性，這會是轉換服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="cb866-163">The ESB Dispatcher executes this service only if this is the name of the transform service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>  
  
    -   <span data-ttu-id="cb866-164">**Microsoft.Practices.ESB.Services.Routing。** 此服務使用的解析程式和配接器提供者架構設定適當的端點的路由資訊。</span><span class="sxs-lookup"><span data-stu-id="cb866-164">**Microsoft.Practices.ESB.Services.Routing.** This service uses the Resolver and Adapter Provider Framework to set the appropriate endpoint routing information.</span></span> <span data-ttu-id="cb866-165">ESB 發送器會執行這項服務，才出現在 ESB 發送器管線元件的對應屬性，這會是路由服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="cb866-165">The ESB Dispatcher executes this service only if this is the name of the routing service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>