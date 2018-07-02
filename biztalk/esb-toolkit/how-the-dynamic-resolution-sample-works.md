---
title: 動態解析範例運作方式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7789316d-f2c4-4018-a8e8-dd9359f1664f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bab7a46a02dc080fa27b9df2b30614bc8a45c6e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976431"
---
# <a name="how-the-dynamic-resolution-sample-works"></a><span data-ttu-id="a7981-102">動態解析範例運作方式</span><span class="sxs-lookup"><span data-stu-id="a7981-102">How the Dynamic Resolution Sample Works</span></span>
<span data-ttu-id="a7981-103">動態解析範例會使用 ESB 發送器解譯器管線元件的上一節中所述的所有傳訊範例。</span><span class="sxs-lookup"><span data-stu-id="a7981-103">The Dynamic Resolution sample uses the ESB Dispatcher Disassembler pipeline component for all the messaging examples described in the previous section.</span></span>  

 <span data-ttu-id="a7981-104">單向傳訊案例，此範例會解析使用 STATIC、 BRE 或 XPATH 解析程式的端點，並且訊息代理程式的通訊協定檔案從檔案、 FTP 或 MQSeries。</span><span class="sxs-lookup"><span data-stu-id="a7981-104">For one-way messaging scenarios, the example resolves the endpoint using the STATIC, BRE, or XPATH Resolver and brokers the protocol from FILE to FILE, FTP, or MQSeries.</span></span>  

 <span data-ttu-id="a7981-105">雙向傳訊案例中，範例解析靜態、 BRE、 UDDI、 或 XPATH 解析程式所使用的端點，並從 SOAP 通訊協定，SOAP 或 Wcf-basichttp 訊息代理程式。</span><span class="sxs-lookup"><span data-stu-id="a7981-105">For two-way messaging scenarios, the example resolves the endpoint using the STATIC, BRE, UDDI, or XPATH Resolver and brokers the protocol from SOAP to either SOAP or WCF-BasicHttp.</span></span> <span data-ttu-id="a7981-106">此外，這些範例解析，並執行 Microsoft BizTalk 對應使用 BRE 解析程式，以決定其解析結果使用包含在訊息內容屬性和訊息內文中的事實。</span><span class="sxs-lookup"><span data-stu-id="a7981-106">In addition, the examples resolve and execute Microsoft BizTalk maps using the BRE Resolver, which uses facts contained in the message context properties and the message body to determine the resolution result.</span></span>  

 <span data-ttu-id="a7981-107">解析程序的結果會是雙向的所有範例都提交 ESB 其訊息。CanadianServices Web 服務位於http://localhost/ESB.CanadianServices/SubmitPOService.asmx。</span><span class="sxs-lookup"><span data-stu-id="a7981-107">The result of the resolution process is that all the two-way examples submit their message to the ESB.CanadianServices Web service located at http://localhost/ESB.CanadianServices/SubmitPOService.asmx.</span></span> <span data-ttu-id="a7981-108">此外，根據解析結果，此範例會執行其中一個**submitOrder**或**submitPurchase**動作。</span><span class="sxs-lookup"><span data-stu-id="a7981-108">In addition, depending on the resolution result, the example executes either the **submitOrder** or the **submitPurchase** action.</span></span> <span data-ttu-id="a7981-109">此外，ESB 發送器解譯器管線元件會動態地執行 BizTalk 對應，根據指定 或 已解決 動作。</span><span class="sxs-lookup"><span data-stu-id="a7981-109">Additionally, the ESB Dispatcher Disassembler pipeline component dynamically executes a BizTalk map, depending on the specified or the resolved action.</span></span>  

 <span data-ttu-id="a7981-110">[圖 1] 顯示設定的管線，以 DynamicResolutionReqResp_SOAP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="a7981-110">Figure 1 shows the configured pipelines for the DynamicResolutionReqResp_SOAP receive location.</span></span>  

 <span data-ttu-id="a7981-111">![動態解析管線](../esb-toolkit/media/ch6-dynamicresolutionpipelines.gif "第 6 章第 DynamicResolutionPipelines")</span><span class="sxs-lookup"><span data-stu-id="a7981-111">![Dynamic Resolution Pipelines](../esb-toolkit/media/ch6-dynamicresolutionpipelines.gif "Ch6-DynamicResolutionPipelines")</span></span>  

 <span data-ttu-id="a7981-112">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="a7981-112">**Figure 1**</span></span>  

 <span data-ttu-id="a7981-113">**設定的管線的 DynamicResolutionReqResp_SOAP 接收動態解析範例應用程式的位置**</span><span class="sxs-lookup"><span data-stu-id="a7981-113">**The configured pipelines of the DynamicResolutionReqResp_SOAP receive location of the Dynamic Resolution sample application**</span></span>  

 <span data-ttu-id="a7981-114">[圖 2] 顯示 ESBReceiveXML 元件，它使用 ESB 發送器解譯器的每個執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="a7981-114">Figure 2 shows the per-instance properties of the ESBReceiveXML component that uses the ESB Dispatcher Disassembler.</span></span>  

 <span data-ttu-id="a7981-115">![動態解析接收 XML](../esb-toolkit/media/ch6-dynamicresolutionreceivexml.gif "第 6 章第 DynamicResolutionReceiveXML")</span><span class="sxs-lookup"><span data-stu-id="a7981-115">![Dynamic Resolution Receive XML](../esb-toolkit/media/ch6-dynamicresolutionreceivexml.gif "Ch6-DynamicResolutionReceiveXML")</span></span>  

 <span data-ttu-id="a7981-116">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="a7981-116">**Figure 2**</span></span>  

 <span data-ttu-id="a7981-117">**動態解析範例應用程式的 ESBReceiveXML 管線中的元件，每個執行個體屬性**</span><span class="sxs-lookup"><span data-stu-id="a7981-117">**The per-instance properties for the components in the ESBReceiveXML pipeline of the Dynamic Resolution sample application**</span></span>  

 <span data-ttu-id="a7981-118">圖 2 顯示下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a7981-118">The following properties are shown in Figure 2:</span></span>  

- <span data-ttu-id="a7981-119">**啟用**。</span><span class="sxs-lookup"><span data-stu-id="a7981-119">**Enabled**.</span></span> <span data-ttu-id="a7981-120">此屬性會決定是否為作用中的管線。</span><span class="sxs-lookup"><span data-stu-id="a7981-120">This property determines whether the pipeline is active.</span></span> <span data-ttu-id="a7981-121">如果此值設為**False**，訊息傳遞而不進行處理。</span><span class="sxs-lookup"><span data-stu-id="a7981-121">If this is set to **False**, messages pass through without processing.</span></span>  

- <span data-ttu-id="a7981-122">**端點**。</span><span class="sxs-lookup"><span data-stu-id="a7981-122">**Endpoint**.</span></span> <span data-ttu-id="a7981-123">這個屬性是用來決定要載入的解析程式的連接字串，它會指定端點組態。</span><span class="sxs-lookup"><span data-stu-id="a7981-123">This property is the connection string used to determine which resolver to load, and it specifies the endpoint configuration.</span></span>  

- <span data-ttu-id="a7981-124">**MapName**。</span><span class="sxs-lookup"><span data-stu-id="a7981-124">**MapName**.</span></span> <span data-ttu-id="a7981-125">這個屬性是用來決定要載入的解析程式和執行的 BizTalk 對應的連接字串。</span><span class="sxs-lookup"><span data-stu-id="a7981-125">This property is the connection string used to determine which resolver to load and which BizTalk map to execute.</span></span> <span data-ttu-id="a7981-126">它可以是完整的名稱，而不是解析程式的連接字串的對應。</span><span class="sxs-lookup"><span data-stu-id="a7981-126">It can be the fully qualified name of a map instead of a resolver connection string.</span></span>  

- <span data-ttu-id="a7981-127">**驗證**。</span><span class="sxs-lookup"><span data-stu-id="a7981-127">**Validate**.</span></span> <span data-ttu-id="a7981-128">當設定為 **，則為 True** （預設設定），ESB 發送器解譯器元件會指示 ESB 轉換服務來驗證針對來源結構描述中的對應會定義來源訊息會解析並執行。</span><span class="sxs-lookup"><span data-stu-id="a7981-128">When set to **True** (the default setting), the ESB Dispatcher Disassembler component instructs the ESB Transformation service to validate the source message against the source schema defined in the map that is will resolve and execute.</span></span>  

  <span data-ttu-id="a7981-129">[圖 3] 顯示使用 ESB 發送器 ESBSendPassthrough 元件的每個執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="a7981-129">Figure 3 shows the per-instance properties of the ESBSendPassthrough component that uses the ESB Dispatcher.</span></span>  

  <span data-ttu-id="a7981-130">![動態解析傳送通過](../esb-toolkit/media/ch6-dynamicresolutionsendpassthrough.gif "第 6 章第 DynamicResolutionSendPassthrough")</span><span class="sxs-lookup"><span data-stu-id="a7981-130">![Dynamic Resolution Send Passthrough](../esb-toolkit/media/ch6-dynamicresolutionsendpassthrough.gif "Ch6-DynamicResolutionSendPassthrough")</span></span>  

  <span data-ttu-id="a7981-131">**圖 3**</span><span class="sxs-lookup"><span data-stu-id="a7981-131">**Figure 3**</span></span>  

  <span data-ttu-id="a7981-132">**動態解析範例應用程式的 ESBSendPassthrough 管線中的元件，每個執行個體屬性**</span><span class="sxs-lookup"><span data-stu-id="a7981-132">**The per-instance properties for the components in the ESBSendPassthrough pipeline of the Dynamic Resolution sample application**</span></span>  

  <span data-ttu-id="a7981-133">圖 3 顯示下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a7981-133">The following properties are shown in Figure 3:</span></span>  

- <span data-ttu-id="a7981-134">**啟用**。</span><span class="sxs-lookup"><span data-stu-id="a7981-134">**Enabled**.</span></span> <span data-ttu-id="a7981-135">此屬性會決定是否為作用中的管線。</span><span class="sxs-lookup"><span data-stu-id="a7981-135">This property determines whether the pipeline is active.</span></span> <span data-ttu-id="a7981-136">如果此值設為**False**，訊息傳遞而不進行處理。</span><span class="sxs-lookup"><span data-stu-id="a7981-136">If this is set to **False**, messages pass through without processing.</span></span>  

- <span data-ttu-id="a7981-137">**端點**。</span><span class="sxs-lookup"><span data-stu-id="a7981-137">**Endpoint**.</span></span> <span data-ttu-id="a7981-138">這個屬性是用來判斷哪些負載和端點組態的解析程式的連接字串。</span><span class="sxs-lookup"><span data-stu-id="a7981-138">This property is the connection string used to determine which resolver to load and the end-point configuration.</span></span>  

- <span data-ttu-id="a7981-139">**MapName**。</span><span class="sxs-lookup"><span data-stu-id="a7981-139">**MapName**.</span></span> <span data-ttu-id="a7981-140">這個屬性是用來決定要載入的解析程式和執行的 BizTalk 對應的連接字串。</span><span class="sxs-lookup"><span data-stu-id="a7981-140">This property is the connection string used to determine which resolver to load and which BizTalk map to execute.</span></span> <span data-ttu-id="a7981-141">對應的完整格式的名稱可用來解析程式的連接字串取代。</span><span class="sxs-lookup"><span data-stu-id="a7981-141">A fully qualified name of a map can be used in place of a resolver's connection string.</span></span>  

- <span data-ttu-id="a7981-142">**驗證**。</span><span class="sxs-lookup"><span data-stu-id="a7981-142">**Validate**.</span></span> <span data-ttu-id="a7981-143">當設定為 **，則為 True** （預設設定），ESB 發送器解譯器元件會指示 ESB 轉換服務來驗證針對來源結構描述中的對應會定義來源訊息會解析並執行。</span><span class="sxs-lookup"><span data-stu-id="a7981-143">When set to **True** (the default setting), the ESB Dispatcher Disassembler component instructs the ESB Transformation service to validate the source message against the source schema defined in the map that is will resolve and execute.</span></span>
