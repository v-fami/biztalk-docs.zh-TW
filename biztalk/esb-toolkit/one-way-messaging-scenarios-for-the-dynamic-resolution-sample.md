---
title: 動態解析範例的單向傳訊案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38237840-e957-4298-84c9-700ec72f2bc5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 359b91a1a5da9ce435d3d9aa5884d6928d0e0a9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987535"
---
# <a name="one-way-messaging-scenarios-for-the-dynamic-resolution-sample"></a><span data-ttu-id="6b995-102">動態解析範例的單向傳訊案例</span><span class="sxs-lookup"><span data-stu-id="6b995-102">One-Way Messaging Scenarios for the Dynamic Resolution Sample</span></span>
<span data-ttu-id="6b995-103">本主題說明如何執行的單向傳訊案例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態解析範例。</span><span class="sxs-lookup"><span data-stu-id="6b995-103">This topic shows how you can run the one-way messaging scenarios for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Dynamic Resolution sample.</span></span>  

 <span data-ttu-id="6b995-104">**若要執行動態解析範例的單向傳訊的案例**</span><span class="sxs-lookup"><span data-stu-id="6b995-104">**To run the one-way messaging scenarios for the Dynamic Resolution sample**</span></span>  

1. <span data-ttu-id="6b995-105">您第一次執行此範例之前，請確定接收位置 URL 指向適當的目錄。</span><span class="sxs-lookup"><span data-stu-id="6b995-105">Before you run this sample for the first time, make sure that the receive location URL points to the appropriate directory.</span></span> <span data-ttu-id="6b995-106">指定來源子資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\In DynamicResolution_FILE 接收位置。</span><span class="sxs-lookup"><span data-stu-id="6b995-106">Specify the source subfolder \Source\Samples\DynamicResolution\Test\Filedrop\In for the DynamicResolution_FILE receive location.</span></span> <span data-ttu-id="6b995-107">此外，請確定名為 DynamicResolutionOneWay 動態傳送埠存在。</span><span class="sxs-lookup"><span data-stu-id="6b995-107">Additionally, make sure that the dynamic send port named DynamicResolutionOneWay exists.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="6b995-108">動態解析範例會使用動態解析機制，將訊息傳送至輸出資料夾、 FTP 站台或 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="6b995-108">The Dynamic Resolution sample uses the dynamic resolution mechanism to send messages to the output folder, FTP site, or MQSeries queue.</span></span> <span data-ttu-id="6b995-109">這就是為什麼此範例中未定義的靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6b995-109">This is why a static send port is not defined for this sample.</span></span> <span data-ttu-id="6b995-110">動態解析元件會擷取解析中的輸出 URL 和配接器提供者架構 ESBReceiveXml 管線中，設定 DynamicResolution_FILE 內呼叫時，接收位置。</span><span class="sxs-lookup"><span data-stu-id="6b995-110">The Dynamic Resolution component retrieves the output URL from the Resolution and Adapter Provider Framework when called by the ESBReceiveXml pipeline, which is configured within the DynamicResolution_FILE receive location.</span></span>  

2. <span data-ttu-id="6b995-111">如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="6b995-111">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  

3. <span data-ttu-id="6b995-112">決定您想要執行的範例。</span><span class="sxs-lookup"><span data-stu-id="6b995-112">Decide which example you want to execute.</span></span> <span data-ttu-id="6b995-113">全都是單向傳訊 （除了使用 XPATH 解析程式） 的範例使用 NAOrderDoc.xml 位於 \Source\Samples\DynamicResolution\Test\Data 的資料夾中的檔案輸入至名為 DynamicResolution_FILE 的接收位置。</span><span class="sxs-lookup"><span data-stu-id="6b995-113">All one-way messaging examples (except the one that uses the XPATH Resolver) use the file NAOrderDoc.xml located in the \Source\Samples\DynamicResolution\Test\Data folder as input to the receive location named DynamicResolution_FILE.</span></span> <span data-ttu-id="6b995-114">有七個單向傳訊範例，每一個由唯一的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="6b995-114">There are seven one-way messaging examples, each represented by a unique binding file.</span></span> <span data-ttu-id="6b995-115">下表列出這些範例中，使用其相關聯的繫結檔案和描述。</span><span class="sxs-lookup"><span data-stu-id="6b995-115">The following tables list these examples, with their associated binding files and descriptions.</span></span>  

   |<span data-ttu-id="6b995-116">檔案輸入輸出使用靜態的解析程式的檔案</span><span class="sxs-lookup"><span data-stu-id="6b995-116">File Inbound to File Outbound Using the STATIC Resolver</span></span>|  
   |-------------------------------------------------------------|  
   |<span data-ttu-id="6b995-117">您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="6b995-117">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml to set the receive location and send port properties.</span></span>|  
   |<span data-ttu-id="6b995-118">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="6b995-118">Sets the maps statically at the receive port.</span></span>|  
   |<span data-ttu-id="6b995-119">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="6b995-119">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  

   |<span data-ttu-id="6b995-120">檔案輸入輸出使用 UDDI 解析程式的檔案</span><span class="sxs-lookup"><span data-stu-id="6b995-120">File Inbound to File Outbound Using the UDDI Resolver</span></span>|  
   |-----------------------------------------------------------|  
   |<span data-ttu-id="6b995-121">您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="6b995-121">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_Bindings.xml to set the receive location and send port properties.</span></span>|  
   |<span data-ttu-id="6b995-122">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="6b995-122">Sets the maps statically at the receive port.</span></span>|  
   |<span data-ttu-id="6b995-123">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="6b995-123">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  

   |<span data-ttu-id="6b995-124">檔案輸入輸出使用 UDDI 解析程式，透過 「 UDDI 服務金鑰的檔案</span><span class="sxs-lookup"><span data-stu-id="6b995-124">File Inbound to File Outbound Using UDDI Resolver via UDDI Service Key</span></span>|  
   |----------------------------------------------------------------------------|  
   |<span data-ttu-id="6b995-125">您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_SERVICEKEY_ Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="6b995-125">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_UDDI_SERVICEKEY_ Bindings.xml to set the receive location and send port properties.</span></span>|  
   |<span data-ttu-id="6b995-126">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="6b995-126">Sets the maps statically at the receive port.</span></span>|  
   |<span data-ttu-id="6b995-127">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="6b995-127">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  

   > [!NOTE]
   >  <span data-ttu-id="6b995-128">如上述範例中，您必須存在於目標 UDDI 伺服器上的其中一個變更繫結檔案中的服務金鑰。</span><span class="sxs-lookup"><span data-stu-id="6b995-128">For the preceding example, you must change the service key in the binding file to one that exists on the target UDDI server.</span></span>  

   |<span data-ttu-id="6b995-129">檔案輸入與輸出使用靜態的解析程式的 FTP</span><span class="sxs-lookup"><span data-stu-id="6b995-129">File Inbound to FTP Outbound Using the STATIC Resolver</span></span>|  
   |------------------------------------------------------------|  
   |<span data-ttu-id="6b995-130">您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="6b995-130">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC_Bindings.xml to set the receive location and send port properties.</span></span>|  
   |<span data-ttu-id="6b995-131">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="6b995-131">Sets the maps statically at the receive port.</span></span>|  
   |<span data-ttu-id="6b995-132">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="6b995-132">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  

   |<span data-ttu-id="6b995-133">檔案輸入與輸出使用 ENDPOINTCONFIG 參數與靜態的解析程式的 FTP</span><span class="sxs-lookup"><span data-stu-id="6b995-133">File Inbound to FTP Outbound Using the STATIC Resolver and ENDPOINTCONFIG Parameter</span></span>|  
   |-----------------------------------------------------------------------------------------|  
   |<span data-ttu-id="6b995-134">您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC__ ENDPOINTCONFIG_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="6b995-134">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FTP_STATIC__ ENDPOINTCONFIG_Bindings.xml to set the receive location and send port properties.</span></span>|  
   |<span data-ttu-id="6b995-135">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="6b995-135">Sets the maps statically at the receive port.</span></span>|  
   |<span data-ttu-id="6b995-136">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="6b995-136">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  
   |<span data-ttu-id="6b995-137">會將配接器提供者設定的其他名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="6b995-137">Passes additional name/values pairs for the adapter provider to set.</span></span>|  

   |<span data-ttu-id="6b995-138">檔案輸入至 MQS 輸出使用靜態的解析程式</span><span class="sxs-lookup"><span data-stu-id="6b995-138">File Inbound to MQS Outbound Using the STATIC Resolver</span></span>|  
   |------------------------------------------------------------|  
   |<span data-ttu-id="6b995-139">您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_MQS_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="6b995-139">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_MQS_STATIC_Bindings.xml to set the receive location and send port properties.</span></span>|  
   |<span data-ttu-id="6b995-140">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="6b995-140">Sets the maps statically at the receive port.</span></span>|  
   |<span data-ttu-id="6b995-141">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="6b995-141">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>|  

   |                                                                             <span data-ttu-id="6b995-142">檔案輸入輸出使用 XPATH 解析程式的檔案</span><span class="sxs-lookup"><span data-stu-id="6b995-142">File Inbound to FILE Outbound Using the XPATH Resolver</span></span>                                                                             |
   |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                        <span data-ttu-id="6b995-143">您可以使用名為 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_XPATH_STATIC_Bindings.xml 繫結檔案來設定接收位置和傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="6b995-143">Uses the binding file named GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_XPATH_STATIC_Bindings.xml to set the receive location and send port properties.</span></span>                        |
   |                                                                                 <span data-ttu-id="6b995-144">在接收埠以靜態方式設定對應。</span><span class="sxs-lookup"><span data-stu-id="6b995-144">Sets the maps statically at the receive port.</span></span>                                                                                  |
   |                                                                    <span data-ttu-id="6b995-145">ESB 發送器會在使用接收位置的端點解析。</span><span class="sxs-lookup"><span data-stu-id="6b995-145">Uses the ESB Dispatcher at the receive location for endpoint resolution.</span></span>                                                                    |
   | <span data-ttu-id="6b995-146">使用訊息內的資訊來判斷適當的端點。</span><span class="sxs-lookup"><span data-stu-id="6b995-146">Uses information within the message to determine the appropriate endpoint.</span></span> <span data-ttu-id="6b995-147">您可以使用此範例中的測試檔案是 NAOrderDoc_XPATH_FILE.xml、 NAOrderDoc_XPATH_FTP.xml 和 NAOrderDoc_XPATH_MQS.xml。</span><span class="sxs-lookup"><span data-stu-id="6b995-147">The test files you can use with this example are NAOrderDoc_XPATH_FILE.xml, NAOrderDoc_XPATH_FTP.xml, and NAOrderDoc_XPATH_MQS.xml.</span></span> |


4. <span data-ttu-id="6b995-148">匯入繫結檔案，您想要執行到 GlobalBank.ESB 應用程式的範例訊息。</span><span class="sxs-lookup"><span data-stu-id="6b995-148">Import the binding file for the messaging example you want to execute into the GlobalBank.ESB application.</span></span>  

5. <span data-ttu-id="6b995-149">在 Windows 檔案總管中，開啟資料夾 \Source\Samples\DynamicResolution\Test\Data 並將適當的輸入的檔案複製到資料夾 \Source\Samples\DynamicResolution\Test\Filedrop\In。</span><span class="sxs-lookup"><span data-stu-id="6b995-149">In Windows Explorer, open the folder \Source\Samples\DynamicResolution\Test\Data and copy the appropriate input file into the folder \Source\Samples\DynamicResolution\Test\Filedrop\In.</span></span> <span data-ttu-id="6b995-150">您使用的檔案取決於您決定要執行的範例：</span><span class="sxs-lookup"><span data-stu-id="6b995-150">The file you use depends on the example you decided to execute:</span></span>  

   -   <span data-ttu-id="6b995-151">XPATH 範例中，使用下列檔案： NAOrderDoc_XPATH_FILE.xml、 NAOrderDoc_XPATH_FTP.xml 或 NAOrderDoc_XPATH_MQS.xml。</span><span class="sxs-lookup"><span data-stu-id="6b995-151">For the XPATH example, use one of the following files: NAOrderDoc_XPATH_FILE.xml, NAOrderDoc_XPATH_FTP.xml, or NAOrderDoc_XPATH_MQS.xml.</span></span>  

   -   <span data-ttu-id="6b995-152">如需其他範例，使用檔案 NAOrderDoc.xml。</span><span class="sxs-lookup"><span data-stu-id="6b995-152">For all other examples, use the file NAOrderDoc.xml.</span></span>  

6. <span data-ttu-id="6b995-153">查看已傳送訊息的適當位置。</span><span class="sxs-lookup"><span data-stu-id="6b995-153">Look in the appropriate location for the delivered message.</span></span> <span data-ttu-id="6b995-154">位置取決於您所使用的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="6b995-154">The location depends on the binding file you used.</span></span> <span data-ttu-id="6b995-155">以下是範例：</span><span class="sxs-lookup"><span data-stu-id="6b995-155">The following are examples:</span></span>  

   -   <span data-ttu-id="6b995-156">輸入 FTP 輸出的範例檔案會將訊息傳遞到名稱為 Out 的 FTP 虛擬目錄時建立安裝範例。</span><span class="sxs-lookup"><span data-stu-id="6b995-156">The File Inbound to FTP Outbound example delivers the message to the FTP virtual directory named Out that you created when you installed the sample.</span></span>  

   -   <span data-ttu-id="6b995-157">檔案輸入輸出檔的範例會將訊息傳遞至 \DynamicResolution\Test\Filedrop\Out 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="6b995-157">The File Inbound to FILE Outbound example delivers the message to the \DynamicResolution\Test\Filedrop\Out subfolder.</span></span>  

   -   <span data-ttu-id="6b995-158">檔案輸入 MQS 輸出的範例會將訊息傳遞至測試。放大時建立的佇列，您會安裝範例。</span><span class="sxs-lookup"><span data-stu-id="6b995-158">The File Inbound to MQS Outbound example delivers the message to the TEST.OUT queue that you created when you installed the sample.</span></span>  

   -   <span data-ttu-id="6b995-159">檔案輸入至 檔案輸出使用 XPATH 解析程式範例會將訊息傳遞到訊息中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="6b995-159">The File Inbound to FILE Outbound using the XPATH Resolver example delivers the message to the location specified in the message.</span></span> <span data-ttu-id="6b995-160">範例文件包含目的位置和傳輸型別 （傳輸類型會附加至訊息的檔案名稱; 例如，NAOrderDoc_XPATH_FTP.xml 訊息中包含的 FTP 傳輸的型別規格）。</span><span class="sxs-lookup"><span data-stu-id="6b995-160">The sample documents contain the destination location and transport type (the transport type is appended to the message file name; for example, the NAOrderDoc_XPATH_FTP.xml message contains the FTP transport type specification).</span></span>  

   <span data-ttu-id="6b995-161">若要了解此範例會使用 ESB 發送器和 ESB 發送器解譯器管線元件，請參閱[動態解析範例運作方式](../esb-toolkit/how-the-dynamic-resolution-sample-works.md)。</span><span class="sxs-lookup"><span data-stu-id="6b995-161">To understand how the sample uses the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components, see [How the Dynamic Resolution Sample Works](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).</span></span>