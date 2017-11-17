---
title: "動態解析範例的雙向傳訊案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e89792f1-c725-46c4-946c-23211e2f892a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 852b1f203b693c7783c7eb461c521f3fbe0ceffe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="two-way-messaging-scenarios-for-the-dynamic-resolution-sample"></a><span data-ttu-id="e0158-102">動態解析範例雙向傳訊的案例</span><span class="sxs-lookup"><span data-stu-id="e0158-102">Two-Way Messaging Scenarios for the Dynamic Resolution Sample</span></span>
<span data-ttu-id="e0158-103">本主題說明如何執行雙向傳訊案例的[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態解析 」 範例。</span><span class="sxs-lookup"><span data-stu-id="e0158-103">This topic shows how you can run the two-way messaging scenarios for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Dynamic Resolution sample.</span></span>  
  
 <span data-ttu-id="e0158-104">**若要執行雙向傳訊案例動態解析範例**</span><span class="sxs-lookup"><span data-stu-id="e0158-104">**To run the two-way messaging scenarios for the Dynamic Resolution sample**</span></span>  
  
1.  <span data-ttu-id="e0158-105">第一次執行此範例之前，請確定接收位置 URL 指向適當的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="e0158-105">Before you run this sample for the first time, make sure that the receive location URL points to the appropriate Web service.</span></span> <span data-ttu-id="e0158-106">指定 Web 服務 URL /ESB。NorthAmericanServices/CustomerOrder.asmx DynamicResolutionReqResp_SOAP 的接收位置。</span><span class="sxs-lookup"><span data-stu-id="e0158-106">Specify the Web service URL /ESB.NorthAmericanServices/CustomerOrder.asmx for the DynamicResolutionReqResp_SOAP receive location.</span></span> <span data-ttu-id="e0158-107">此外，請確定存在名為 DynamicResolutionSolicitResp 動態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e0158-107">Also, make sure that the dynamic send port named DynamicResolutionSolicitResp exists.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0158-108">動態解析 」 範例會使用動態解析傳送和接收來自加拿大的 Web 服務 (http://localhost/ESB.CanadianServices/SubmitPOService.asmx) 的回應。</span><span class="sxs-lookup"><span data-stu-id="e0158-108">The Dynamic Resolution sample uses dynamic resolution to send messages to, and receive responses from, the Canadian Web service (http://localhost/ESB.CanadianServices/SubmitPOService.asmx).</span></span> <span data-ttu-id="e0158-109">這就是為什麼此範例中未定義靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e0158-109">This is why a static send port is not defined for this sample.</span></span> <span data-ttu-id="e0158-110">動態解析元件擷取輸出 URL 從解析度，並由 ESBReceiveXml 管線中，設定 DynamicResolutionReqResp_SOAP 內呼叫配接器提供者架構接收位置。</span><span class="sxs-lookup"><span data-stu-id="e0158-110">The dynamic resolution component retrieves the outbound URL from the Resolution and Adapter Provider Framework called by the ESBReceiveXml pipeline, which is configured within the DynamicResolutionReqResp_SOAP receive location.</span></span> <span data-ttu-id="e0158-111">在某些的雙向傳訊範例 ESBMapSend 管線會解析並執行 Microsoft BizTalk 對應。</span><span class="sxs-lookup"><span data-stu-id="e0158-111">In some of the two-way messaging examples, the ESBMapSend pipeline resolves and executes Microsoft BizTalk maps.</span></span>  
  
2.  <span data-ttu-id="e0158-112">如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="e0158-112">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
3.  <span data-ttu-id="e0158-113">決定您想要執行的範例。</span><span class="sxs-lookup"><span data-stu-id="e0158-113">Decide which example you want to execute.</span></span> <span data-ttu-id="e0158-114">所有的雙向傳訊案例使用 ESB。NorthAmericanServices Web 服務位於 http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx 發佈要求訊息至 BizTalk，會使用名為 DynamicResolutionReqResp_SOAP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="e0158-114">All two-way messaging scenarios use the ESB.NorthAmericanServices Web service located at http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx to publish the request message to BizTalk, which uses the receive location named DynamicResolutionReqResp_SOAP.</span></span> <span data-ttu-id="e0158-115">10 的雙向傳訊範例，分別由唯一的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="e0158-115">There are 10 two-way messaging examples, each represented by a unique binding file.</span></span> <span data-ttu-id="e0158-116">下表列出這些範例中，關聯的繫結檔案與說明。</span><span class="sxs-lookup"><span data-stu-id="e0158-116">The following tables list these examples, with their associated binding files and descriptions.</span></span>  
  
    |<span data-ttu-id="e0158-117">SOAP 輸出 (submitOrder 動作) 的 SOAP 輸入使用 BRE 解析程式</span><span class="sxs-lookup"><span data-stu-id="e0158-117">SOAP Inbound to SOAP Outbound (submitOrder Action) Using the BRE Resolver</span></span>|  
    |---------------------------------------------------------------------------------|  
    |<span data-ttu-id="e0158-118">會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="e0158-118">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Bindings.xml to set the receive location and send port properties.</span></span>|  
    |<span data-ttu-id="e0158-119">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="e0158-119">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
  
    |<span data-ttu-id="e0158-120">SOAP 輸出 (submitOrder 動作) 的 SOAP 輸入端點和轉換解析使用 BRE 解析程式</span><span class="sxs-lookup"><span data-stu-id="e0158-120">SOAP Inbound to SOAP Outbound (submitOrder Action) Using the BRE Resolver for Endpoint and Transformation Resolution</span></span>|  
    |----------------------------------------------------------------------------------------------------------------------------|  
    |<span data-ttu-id="e0158-121">會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Routing_AND_ Transform_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="e0158-121">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Routing_AND_ Transform_Bindings.xml to set the receive location and send port properties.</span></span>|  
    |<span data-ttu-id="e0158-122">使用 ESB 發送器上的元件輸出的傳送埠管線，並輸出接收位置管線，若要以動態方式解決並執行對應。</span><span class="sxs-lookup"><span data-stu-id="e0158-122">Uses the ESB Dispatcher component on the outbound send port pipeline and the outbound receive location pipeline to dynamically resolve and execute the map.</span></span>|  
    |<span data-ttu-id="e0158-123">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="e0158-123">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
  
    |<span data-ttu-id="e0158-124">SOAP 輸出 (submitOrder 動作) 的 SOAP 輸入使用靜態的解析程式</span><span class="sxs-lookup"><span data-stu-id="e0158-124">SOAP Inbound to SOAP Outbound (submitOrder Action) Using the STATIC Resolver</span></span>|  
    |------------------------------------------------------------------------------------|  
    |<span data-ttu-id="e0158-125">會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_STATIC_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="e0158-125">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_STATIC_Bindings.xml to set the receive location and send port properties.</span></span>|  
    |<span data-ttu-id="e0158-126">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="e0158-126">Sets the maps statically at the receive port.</span></span>|  
    |<span data-ttu-id="e0158-127">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="e0158-127">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
  
    |<span data-ttu-id="e0158-128">SOAP 輸出 (submitOrder 動作) 的 SOAP 輸入使用 UDDI 解析程式對 Microsoft UDDI 伺服器</span><span class="sxs-lookup"><span data-stu-id="e0158-128">SOAP Inbound to SOAP Outbound (submitOrder Action) Using the UDDI Resolver Against the Microsoft UDDI Server</span></span>|  
    |--------------------------------------------------------------------------------------------------------------------|  
    |<span data-ttu-id="e0158-129">會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_MSFTREGISTRY_ Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="e0158-129">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_MSFTREGISTRY_ Bindings.xml to set the receive location and send port properties.</span></span>|  
    |<span data-ttu-id="e0158-130">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="e0158-130">Sets the maps statically at the receive port.</span></span>|  
    |<span data-ttu-id="e0158-131">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="e0158-131">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="e0158-132">上述範例中，您必須變更成目標 UDDI 伺服器上現有的繫結檔案中的服務金鑰。</span><span class="sxs-lookup"><span data-stu-id="e0158-132">For the preceding example, you must change the service key in the binding file to one that exists on the target UDDI server.</span></span>  
  
    |<span data-ttu-id="e0158-133">SOAP 輸出 (submitOrder 動作) 的 SOAP 輸入使用 UDDI 解析程式對 SOA 軟體 UDDI 伺服器</span><span class="sxs-lookup"><span data-stu-id="e0158-133">SOAP Inbound to SOAP Outbound (submitOrder Action) Using the UDDI Resolver Against the SOA Software UDDI Server</span></span>|  
    |-----------------------------------------------------------------------------------------------------------------------|  
    |<span data-ttu-id="e0158-134">會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_SOAREGISTRY_ Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="e0158-134">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_SOAREGISTRY_ Bindings.xml to set the receive location and send port properties.</span></span>|  
    |<span data-ttu-id="e0158-135">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="e0158-135">Sets the maps statically at the receive port.</span></span>|  
    |<span data-ttu-id="e0158-136">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="e0158-136">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
  
    |<span data-ttu-id="e0158-137">SOAP 輸入 SOAP 輸出 (submitOrder 動作) 使用 XPATH 解析程式</span><span class="sxs-lookup"><span data-stu-id="e0158-137">SOAP Inbound to SOAP Outbound (submitOrder Action) Using the XPATH Resolver</span></span>|  
    |-----------------------------------------------------------------------------------|  
    |<span data-ttu-id="e0158-138">會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_XPATH_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="e0158-138">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_XPATH_Bindings.xml to set the receive location and send port properties.</span></span>|  
    |<span data-ttu-id="e0158-139">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="e0158-139">Sets the maps statically at the receive port.</span></span>|  
    |<span data-ttu-id="e0158-140">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="e0158-140">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
    |<span data-ttu-id="e0158-141">訊息包含端點的組態識別碼 = http://localhost/ESB.CanadianServices/SubmitPOService.asmx 和 customerName = http://globalbank.esb.dynamicresolution.com/canadianservices/。</span><span class="sxs-lookup"><span data-stu-id="e0158-141">The message contains the endpoint configuration ID=http://localhost/ESB.CanadianServices/SubmitPOService.asmx and customerName=http://globalbank.esb.dynamicresolution.com/canadianservices/.</span></span>|  
  
    |<span data-ttu-id="e0158-142">SOAP 輸出 (submitPurchase 動作) 的 SOAP 輸入使用 BRE 解析程式端點和轉換解析</span><span class="sxs-lookup"><span data-stu-id="e0158-142">SOAP Inbound to SOAP Outbound (submitPurchase Action) Using the BRE Resolver Endpoint and Transformation Resolution</span></span>|  
    |---------------------------------------------------------------------------------------------------------------------------|  
    |<span data-ttu-id="e0158-143">會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_BRE_Routing_ AND_Transform_Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="e0158-143">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_BRE_Routing_ AND_Transform_Bindings.xml to set the receive location and send port properties.</span></span>|  
    |<span data-ttu-id="e0158-144">使用 ESB 發送器上的元件輸出的傳送埠管線，並輸出接收位置管線，若要以動態方式解決並執行對應。</span><span class="sxs-lookup"><span data-stu-id="e0158-144">Uses the ESB Dispatcher component on the outbound send port pipeline and the outbound receive location pipeline to dynamically resolve and execute the map.</span></span>|  
    |<span data-ttu-id="e0158-145">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="e0158-145">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
    |<span data-ttu-id="e0158-146">BRE 解析程式變更**動作**從**submitOrder**至**submitPurchase**。</span><span class="sxs-lookup"><span data-stu-id="e0158-146">The BRE Resolver changes the **Action** from **submitOrder** to **submitPurchase**.</span></span>|  
  
    |<span data-ttu-id="e0158-147">SOAP 輸出 (submitPurchase 動作) 的 SOAP 輸入使用靜態的解析程式</span><span class="sxs-lookup"><span data-stu-id="e0158-147">SOAP Inbound to SOAP Outbound (submitPurchase Action) Using the STATIC Resolver</span></span>|  
    |---------------------------------------------------------------------------------------|  
    |<span data-ttu-id="e0158-148">會使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_STATIC_ Bindings.xml 繫結檔來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="e0158-148">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_STATIC_ Bindings.xml to set the receive location and send port properties.</span></span>|  
    |<span data-ttu-id="e0158-149">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="e0158-149">Sets the maps statically at the receive port.</span></span>|  
    |<span data-ttu-id="e0158-150">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="e0158-150">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
    |<span data-ttu-id="e0158-151">靜態解析程式變更**動作**從**submitOrder**至**submitPurchase**。</span><span class="sxs-lookup"><span data-stu-id="e0158-151">The STATIC Resolver changes the **Action** from **submitOrder** to **submitPurchase**.</span></span>|  
  
4.  <span data-ttu-id="e0158-152">訊息的範例，您要執行到 GlobalBank.ESB 應用程式的繫結檔匯入。</span><span class="sxs-lookup"><span data-stu-id="e0158-152">Import the binding file for the messaging example you want to execute into the GlobalBank.ESB application.</span></span>  
  
5.  <span data-ttu-id="e0158-153">呼叫 NorthAmerican Web 服務使用 Microsoft InfoPath、.NET Web 服務 Studio 中或任何其他適當的機制。</span><span class="sxs-lookup"><span data-stu-id="e0158-153">Call the NorthAmerican Web service using Microsoft InfoPath, the .NET Web Service Studio, or any other appropriate mechanism.</span></span> <span data-ttu-id="e0158-154">請確定您包含作業所需的所有參數。</span><span class="sxs-lookup"><span data-stu-id="e0158-154">Make sure that you include all parameters required by the operation.</span></span>  
  
6.  <span data-ttu-id="e0158-155">查詢傳回的訊息回應。</span><span class="sxs-lookup"><span data-stu-id="e0158-155">Look for the returned message response.</span></span> <span data-ttu-id="e0158-156">如果您指定**submitOrder**動作，「 提交訂單 」 的文字會在之前的值**識別碼**欄位中傳回的訊息。</span><span class="sxs-lookup"><span data-stu-id="e0158-156">If you specified the **submitOrder** action, the text "Submit Order" will precede the value of the **ID** field in the returned message.</span></span> <span data-ttu-id="e0158-157">如果您指定**submitPurchase**動作，「 送出採購 」 的文字會在之前的值**識別碼**欄位中傳回的訊息。</span><span class="sxs-lookup"><span data-stu-id="e0158-157">If you specified the **submitPurchase** action, the text "Submit Purchase" will precede the value of the **ID** field in the returned message.</span></span>  
  
 <span data-ttu-id="e0158-158">若要了解此範例會使用 「 ESB 發送器和 ESB 發送器解譯器管線元件，請參閱[動態解析範例的運作方式](../esb-toolkit/how-the-dynamic-resolution-sample-works.md)。</span><span class="sxs-lookup"><span data-stu-id="e0158-158">To understand how the sample uses the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components, see [How the Dynamic Resolution Sample Works](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).</span></span>