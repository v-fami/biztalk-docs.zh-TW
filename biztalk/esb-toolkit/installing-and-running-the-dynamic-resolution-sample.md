---
title: 安裝和執行動態解析範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4359987-b18c-44f5-a2cf-e30e17ac5e9f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0939111bc0a62ecf31286045f412ed160a97c3f9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967727"
---
# <a name="installing-and-running-the-dynamic-resolution-sample"></a><span data-ttu-id="dbcd9-102">安裝和執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="dbcd9-102">Installing and Running the Dynamic Resolution Sample</span></span>
<span data-ttu-id="dbcd9-103">動態解析範例示範的 ESB 發送器和 ESB 發送器解譯器管線元件的一般使用案例。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-103">The Dynamic Resolution sample demonstrates typical usage scenarios for the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components.</span></span> <span data-ttu-id="dbcd9-104">它示範如何使用元件動態解析端點位置、 設定路由的屬性，並解決並執行 Microsoft BizTalk 對應，在訊息層級，而不需使用協調流程。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-104">It demonstrates how you can use the components to dynamically resolve endpoint location, set routing properties, and resolve and execute Microsoft BizTalk maps at the messaging level without using an orchestration.</span></span> <span data-ttu-id="dbcd9-105">它也會示範單向和雙向傳訊模式。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-105">It also demonstrates both one-way and two-way messaging patterns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbcd9-106">為了取得最佳結果，當解析機制，在您熟悉[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，您應該執行[安裝和執行解析程式服務範例](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)執行動態解析範例之前。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-106">For optimum results when familiarizing yourself with the resolution mechanism within the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], you should run the [Installing and Running the Resolver Service Sample](../esb-toolkit/installing-and-running-the-resolver-service-sample.md) before you run the Dynamic Resolution sample.</span></span>  
  
 <span data-ttu-id="dbcd9-107">範例應用程式包含兩個接收位置和兩個動態傳送埠，此範例會示範多個使用動態解析元件的使用案例。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-107">The sample application contains two receive locations and two dynamic send ports, which the sample uses to demonstrate multiple use cases for the dynamic resolution components.</span></span> <span data-ttu-id="dbcd9-108">每個使用案例會示範如何解析程式和配接器提供者，在解決和配接器提供者架構，用來結合，可以提供各式各樣的鬆散偶合的傳訊解決方案的基礎。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-108">Each use case shows how the resolvers and adapter providers in the Resolution and Adapter Provider Framework, when used in combination, can provide the basis for a variety of loosely coupled messaging solutions.</span></span>  
  
## <a name="one-way-messaging-scenarios"></a><span data-ttu-id="dbcd9-109">單向傳訊案例</span><span class="sxs-lookup"><span data-stu-id="dbcd9-109">One-Way Messaging Scenarios</span></span>  
 <span data-ttu-id="dbcd9-110">全都是單向傳訊案例 （除了使用 XPATH 解析程式） 使用檔案 NAOrderDoc.xml，位於 [\Source\Samples\DynamicResolution\Test\Data] 資料夾中，輸入接收位置名為 DynamicResolution_FILE。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-110">All one-way messaging scenarios (except the one that uses the XPATH Resolver) use the file NAOrderDoc.xml, located in the \Source\Samples\DynamicResolution\Test\Data folder, as input to the receive location named DynamicResolution_FILE.</span></span> <span data-ttu-id="dbcd9-111">有七個單向的訊息範例中，所有由唯一的繫結檔案，您必須匯入，然後再執行每個範例。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-111">There are seven one-way messaging examples, all represented by a unique binding file that you must import before you execute each example.</span></span>  
  
## <a name="two-way-messaging-scenarios"></a><span data-ttu-id="dbcd9-112">雙向傳訊案例</span><span class="sxs-lookup"><span data-stu-id="dbcd9-112">Two-Way Messaging Scenarios</span></span>  
 <span data-ttu-id="dbcd9-113">所有的雙向傳訊案例使用範例 ESB。NorthAmericanServices Web 服務位於http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx發佈到 BizTalk 的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-113">All two-way messaging scenarios use the sample ESB.NorthAmericanServices Web service located at http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx to publish the request message into BizTalk.</span></span> <span data-ttu-id="dbcd9-114">您可以執行使用 Microsoft InfoPath 此 Web 服務或透過公用程式，例如可從 Storm [CodePlex](http://go.microsoft.com/fwlink/?LinkID=187762&clcid=0x409)。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-114">You can execute this Web service using Microsoft InfoPath or through a utility such as the Storm available from [CodePlex](http://go.microsoft.com/fwlink/?LinkID=187762&clcid=0x409).</span></span>  
  
 <span data-ttu-id="dbcd9-115">每個範例，動態地解析提交訊息至範例 ESB 的端點 URL。CanadianServices Web 服務位於http://localhost/ESB.CanadianServices/SubmitPOService.asmx。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-115">Each example dynamically resolves the endpoint URL to submit the message to the sample ESB.CanadianServices Web service located at http://localhost/ESB.CanadianServices/SubmitPOService.asmx.</span></span> <span data-ttu-id="dbcd9-116">此範例會執行**submitOrder**動作或**submitPurchase**動作，根據解析程序的結果。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-116">The example will execute either the **submitOrder** action or the **submitPurchase** action, depending on the results of the resolution process.</span></span> <span data-ttu-id="dbcd9-117">雙向傳訊案例的接收位置是 DynamicResolutionReqResp_SOAP。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-117">The receive location for two-way messaging scenarios is DynamicResolutionReqResp_SOAP.</span></span> <span data-ttu-id="dbcd9-118">有 10 個的雙向傳訊範例中，所有由唯一的繫結檔案，您必須匯入，然後再執行每個範例。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-118">There are 10 two-way messaging examples, all represented by a unique binding file that you must import before you execute each example.</span></span>  
  
## <a name="binding-files"></a><span data-ttu-id="dbcd9-119">繫結檔案</span><span class="sxs-lookup"><span data-stu-id="dbcd9-119">Binding Files</span></span>  
 <span data-ttu-id="dbcd9-120">此範例的繫結檔案位於名為 \Source\Samples\DynamicResolution\Samples\Release 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-120">The binding files for this sample are located in the folder named \Source\Samples\DynamicResolution\Samples\Release.</span></span>  
  
 <span data-ttu-id="dbcd9-121">所有的繫結檔案名稱的開頭 GlobalBank.ESB.DynamicResolution_SubmitOrder_To，後面接著所套用之個別範例的指示。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-121">The binding file names all start with GlobalBank.ESB.DynamicResolution_SubmitOrder_To, followed by an indication of the individual example to which they apply.</span></span> <span data-ttu-id="dbcd9-122">比方說，繫結檔案，例如 「 檔案輸出到檔案輸入會使用靜態的解析程式 」 是 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-122">For example, the binding file for the "File Inbound to File Outbound using the STATIC Resolver" example is GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml.</span></span>  
  
 <span data-ttu-id="dbcd9-123">每次您匯入其中一個繫結至 GlobalBank.ESB BizTalk 應用程式，基礎的檔案接收位置內的範例應用程式會重設。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-123">Every time you import one of the binding files into the GlobalBank.ESB BizTalk application, the underlying receive location within the sample application is reset.</span></span> <span data-ttu-id="dbcd9-124">在 接收埠名稱相關聯的動態傳送埠篩選條件。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-124">The associated dynamic send port filters on the receive port name.</span></span> <span data-ttu-id="dbcd9-125">因此，若要執行測試，只匯入其中一個繫結檔案，請卸除的適當命名的訊息則輸入資料夾 （適用於單向傳訊的案例），或呼叫使用 InfoPath、 Storm 公用程式，或任何其他的 NorthAmerican Web 服務適合的用戶端。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-125">Therefore, to execute a test, you just import one of the binding files and either drop the appropriately named message into the input folder (for one-way messaging scenarios) or call the NorthAmerican Web service using InfoPath, the Storm utility, or any other suitable client.</span></span>  
  
## <a name="sample-dependencies"></a><span data-ttu-id="dbcd9-126">範例相依性</span><span class="sxs-lookup"><span data-stu-id="dbcd9-126">Sample Dependencies</span></span>  
 <span data-ttu-id="dbcd9-127">動態解析範例有多個核心 ESB 安裝一部分的組件的相依性。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-127">The Dynamic Resolution sample has dependencies on a number of assemblies that are part of the core ESB installation.</span></span> <span data-ttu-id="dbcd9-128">這些組件如下所示：</span><span class="sxs-lookup"><span data-stu-id="dbcd9-128">These assemblies are the following:</span></span>  
  
- <span data-ttu-id="dbcd9-129">**Microsoft.Practices.ESB.PipelineComponents.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-129">**Microsoft.Practices.ESB.PipelineComponents.dll**.</span></span> <span data-ttu-id="dbcd9-130">這包含 ESB 發送器管線元件。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-130">This contains the ESB Dispatcher Pipeline component.</span></span>  
  
- <span data-ttu-id="dbcd9-131">**Microsoft.Practices.ESB.Resolver.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-131">**Microsoft.Practices.ESB.Resolver.dll**.</span></span> <span data-ttu-id="dbcd9-132">這會實作管線由呼叫的解析程式管理員。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-132">This implements the Resolver Manager called by the pipeline.</span></span>  
  
- <span data-ttu-id="dbcd9-133">**Microsoft.Practices.ESB.Resolver.BRE.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-133">**Microsoft.Practices.ESB.Resolver.BRE.dll**.</span></span> <span data-ttu-id="dbcd9-134">這會實作商務規則引擎的解析程式。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-134">This implements the Business Rules Engine Resolver.</span></span>  
  
- <span data-ttu-id="dbcd9-135">**Microsoft.Practices.ESB.Resolver.STATIC.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-135">**Microsoft.Practices.ESB.Resolver.STATIC.dll**.</span></span> <span data-ttu-id="dbcd9-136">這會實作靜態的解析程式。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-136">This implements the STATIC Resolver.</span></span>  
  
- <span data-ttu-id="dbcd9-137">**Microsoft.Practices.ESB.Resolver.UDDI.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-137">**Microsoft.Practices.ESB.Resolver.UDDI.dll**.</span></span> <span data-ttu-id="dbcd9-138">這會實作 UDDI 解析程式。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-138">This implements the UDDI Resolver.</span></span>  
  
- <span data-ttu-id="dbcd9-139">**Microsoft.Practices.ESB.Resolver.UDDI3.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-139">**Microsoft.Practices.ESB.Resolver.UDDI3.dll**.</span></span> <span data-ttu-id="dbcd9-140">這會實作 UDDI3 解析程式。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-140">This implements the UDDI3 Resolver.</span></span>  
  
- <span data-ttu-id="dbcd9-141">**Microsoft.Practices.ESB.Resolver.XPATH.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-141">**Microsoft.Practices.ESB.Resolver.XPATH.dll**.</span></span> <span data-ttu-id="dbcd9-142">這會實作 XPATH 解析程式。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-142">This implements the XPATH Resolver.</span></span>  
  
- <span data-ttu-id="dbcd9-143">**Microsoft.Practices.ESB.Resolver.Schemas.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-143">**Microsoft.Practices.ESB.Resolver.Schemas.dll**.</span></span> <span data-ttu-id="dbcd9-144">這包含解析程式的結構描述。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-144">This contains the resolver schemas.</span></span>  
  
- <span data-ttu-id="dbcd9-145">**Microsoft.Practices.ESB.Adapter.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-145">**Microsoft.Practices.ESB.Adapter.dll**.</span></span> <span data-ttu-id="dbcd9-146">這會實作配接器管理員。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-146">This implements the adapter manager.</span></span>  
  
- <span data-ttu-id="dbcd9-147">**Microsoft.Practices.ESB.Adapter.FTP.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-147">**Microsoft.Practices.ESB.Adapter.FTP.dll**.</span></span> <span data-ttu-id="dbcd9-148">這會實作 FTP 配接器提供者。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-148">This implements the FTP adapter provider.</span></span>  
  
- <span data-ttu-id="dbcd9-149">**Microsoft.Practices.ESB.Adapter.FILE.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-149">**Microsoft.Practices.ESB.Adapter.FILE.dll**.</span></span> <span data-ttu-id="dbcd9-150">這會實作檔案配接器提供者。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-150">This implements the FILE adapter provider.</span></span>  
  
- <span data-ttu-id="dbcd9-151">**Microsoft.Practices.ESB.Adapter.MQSeries.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-151">**Microsoft.Practices.ESB.Adapter.MQSeries.dll**.</span></span> <span data-ttu-id="dbcd9-152">這會實作 MQSeries 配接器提供者。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-152">This implements the MQSeries adapter provider.</span></span>  
  
- <span data-ttu-id="dbcd9-153">**Microsoft.Practices.ESB.Adapter.WcfBasicHttp.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-153">**Microsoft.Practices.ESB.Adapter.WcfBasicHttp.dll**.</span></span> <span data-ttu-id="dbcd9-154">這會實作 Wcf-basichttp 配接器提供者。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-154">This implements the WCF-BasicHttp adapter provider.</span></span>  
  
- <span data-ttu-id="dbcd9-155">**Microsoft.Practices.ESB.Adapter.WcfWSHttp.dll**。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-155">**Microsoft.Practices.ESB.Adapter.WcfWSHttp.dll**.</span></span> <span data-ttu-id="dbcd9-156">這會實作 Wcf-wshttp 配接器提供者。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-156">This implements the WCF-WSHttp adapter provider.</span></span>  
  
  <span data-ttu-id="dbcd9-157">動態解析範例也是取決於先前的解析程式和配接器的正確組態。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-157">The Dynamic Resolution sample is also dependent on correct configuration of the preceding resolvers and adapters.</span></span> <span data-ttu-id="dbcd9-158">請確定您在安裝中所述完成處理程序設定這些項目， [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dbcd9-158">Make sure that you complete the process for configuring these, as described in Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
  <span data-ttu-id="dbcd9-159">本節包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="dbcd9-159">This section contains the following topics:</span></span>  
  
- [<span data-ttu-id="dbcd9-160">安裝動態解析範例</span><span class="sxs-lookup"><span data-stu-id="dbcd9-160">Installing the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-the-dynamic-resolution-sample.md)  
  
- [<span data-ttu-id="dbcd9-161">執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="dbcd9-161">Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/running-the-dynamic-resolution-sample.md)
