---
title: "BizTalk Adapter for JD Edwards EnterpriseOne 的架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: architecture
ms.assetid: 0441c5d2-6a46-45b6-8ab5-0bdac3590f56
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 828d0ed6affc44edbf49beb204cd4afe21196747
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone"></a><span data-ttu-id="048ef-102">BizTalk Adapter for JD Edwards EnterpriseOne 的架構</span><span class="sxs-lookup"><span data-stu-id="048ef-102">Architecture of BizTalk Adapter for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="048ef-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 可讓您存取 JD Edwards EnterpriseOne 商務功能。</span><span class="sxs-lookup"><span data-stu-id="048ef-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides access to JD Edwards EnterpriseOne business functions.</span></span> <span data-ttu-id="048ef-104">JD Edwards EnterpriseOne 會使用名為 JDENet 的專屬傳訊架構，在用戶端與伺服器電腦之間通訊。</span><span class="sxs-lookup"><span data-stu-id="048ef-104">JD Edwards EnterpriseOne communicates between client and server machines using a proprietary messaging architecture called JDENet.</span></span> <span data-ttu-id="048ef-105">JDENet 是由 JAR 檔案 Connector.jar 和 Kernel.jar 中的 JD Edwards EnterpriseOne 連接器類別實作。</span><span class="sxs-lookup"><span data-stu-id="048ef-105">JDENet is implemented by the JD Edwards EnterpriseOne connector classes found in the JAR files, Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="048ef-106">以 TCP/IP 做為傳輸通訊協定，與預設連接埠 6009 或 6010 來實作通訊。</span><span class="sxs-lookup"><span data-stu-id="048ef-106">Communication is implemented using TCP/IP as a transport protocol, with a default port of 6009 or 6010.</span></span> <span data-ttu-id="048ef-107">此值設定為位置的描述，請參閱[如何設定 JD Edwards OneWorld 傳輸屬性](../core/how-to-set-jd-edwards-oneworld-transport-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="048ef-107">For a description of where this value is set, see [How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md).</span></span>  
  
 <span data-ttu-id="048ef-108">下圖顯示 BizTalk Adapter for JD Edwards EnterpriseOne 的架構。</span><span class="sxs-lookup"><span data-stu-id="048ef-108">The following figure shows the architecture for BizTalk Adapter for JD Edwards EnterpriseOne.</span></span>  
  
 ![](../core/media/jd-enterpriseone-arch.gif "JD_EnterpriseOne_arch")  
  
## <a name="inbound-services-at-design-time"></a><span data-ttu-id="048ef-109">設計階段的輸入服務</span><span class="sxs-lookup"><span data-stu-id="048ef-109">Inbound Services at Design Time</span></span>  
  
-   <span data-ttu-id="048ef-110">在設計階段，您會建立連接埠、選取配接器並提供認證資訊，以連接至目標 JD Edwards EnterpriseOne 伺服器。</span><span class="sxs-lookup"><span data-stu-id="048ef-110">At design time, you create a port, select an adapter, and provide credential information to connect to the target JD Edwards EnterpriseOne server.</span></span> <span data-ttu-id="048ef-111">Visual Studio 開發環境會呼叫配接器架構，以要求此連接埠的設計階段資訊。</span><span class="sxs-lookup"><span data-stu-id="048ef-111">The Visual Studio development environment calls the adapter framework to request design-time information for this port.</span></span> <span data-ttu-id="048ef-112">配接器會針對此連接埠使用 Browsingagent。</span><span class="sxs-lookup"><span data-stu-id="048ef-112">The adapter uses the Browsingagent for this port.</span></span>  
  
-   <span data-ttu-id="048ef-113">在設計階段，BizTalk Server 會對配接器進行呼叫來要求資訊。</span><span class="sxs-lookup"><span data-stu-id="048ef-113">At design time, BizTalk Server requests information by making calls to the adapter.</span></span>  
  
-   <span data-ttu-id="048ef-114">Browsingagent 會將要求轉換成原生 JD Edwards EnterpriseOne 程式碼，再透過 ThinNet API 連線 (建立於 Connector.jar and Kernel.jar 中) 將要求傳輸至 JD Edwards EnterpriseOne。</span><span class="sxs-lookup"><span data-stu-id="048ef-114">The Browsingagent converts the request into native JD Edwards EnterpriseOne code and transmits the requests to JD Edwards EnterpriseOne through the ThinNet API connection (established in Connector.jar and Kernel.jar).</span></span>  
  
-   <span data-ttu-id="048ef-115">最初會傳回 JD Edwards EnterpriseOne 中模組的清單並傳輸至 Visual Studio 開發環境，以填入配接器精靈。</span><span class="sxs-lookup"><span data-stu-id="048ef-115">A list of Modules in JD Edwards EnterpriseOne is initially returned and transported to the Visual Studio development environment, where it populates the Adapter Wizard.</span></span>  
  
-   <span data-ttu-id="048ef-116">您可以先顯示程式庫名稱，再顯示模組名稱，來逐漸展開階層。</span><span class="sxs-lookup"><span data-stu-id="048ef-116">You can expand the hierarchy by displaying the library name and then the module name.</span></span>  
  
-   <span data-ttu-id="048ef-117">當您 選取特定模組時，您會看見模組內所有功能的結構描述 。</span><span class="sxs-lookup"><span data-stu-id="048ef-117">When you select a specific module, you see schemas for all functions within the module.</span></span> <span data-ttu-id="048ef-118">配接器會從 JD Edwards EnterpriseOne 取得必要資訊，而 Browsingagent 會建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="048ef-118">The adapter gets the required information from JD Edwards EnterpriseOne, and the browsingagent creates the schemas.</span></span>  
  
-   <span data-ttu-id="048ef-119">結構描述隨即新增至 BizTalk Server 專案協調流程。</span><span class="sxs-lookup"><span data-stu-id="048ef-119">The schemas are added to the BizTalk Server project orchestration.</span></span>  
  
## <a name="inbound-services-at-run-time"></a><span data-ttu-id="048ef-120">執行階段的輸入服務</span><span class="sxs-lookup"><span data-stu-id="048ef-120">Inbound Services at Run Time</span></span>  
  
-   <span data-ttu-id="048ef-121">BizTalk Server 會呼叫配接器，以在特定連接埠上傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="048ef-121">BizTalk Server calls the adapter to send a message on a specific port.</span></span>  
  
-   <span data-ttu-id="048ef-122">執行階段代理程式會將 XML 轉換成原生 JDE 程式碼。</span><span class="sxs-lookup"><span data-stu-id="048ef-122">The run-time agent converts the XML into native JDE code.</span></span>  
  
-   <span data-ttu-id="048ef-123">執行階段代理程式會透過 ThinNet，將要求提交給傳送埠的傳輸屬性中所指定的 JD Edwards EnterpriseOne 系統。</span><span class="sxs-lookup"><span data-stu-id="048ef-123">The run-time agent submits the request through the ThinNet to the JD Edwards EnterpriseOne system specified in the transport properties of the send port.</span></span>  
  
-   <span data-ttu-id="048ef-124">「主要商務功能」會在 JD Edwards EnterpriseOne 系統上執行，然後該系統會產生回應文件，指示執行成功或失敗以及商務功能所傳回的資料參數。</span><span class="sxs-lookup"><span data-stu-id="048ef-124">The Master Business Function is executed on the JD Edwards EnterpriseOne system, which then generates a response document indicating success or failure as well as data parameters returned by the business function.</span></span>  
  
-   <span data-ttu-id="048ef-125">傳送至 JD Edwards EnterpriseOne 的訊息是單一訊息、單一回覆架構。</span><span class="sxs-lookup"><span data-stu-id="048ef-125">The message sent to JD Edwards EnterpriseOne is a single message, single reply architecture.</span></span> <span data-ttu-id="048ef-126">系統無法同時處理多則訊息。</span><span class="sxs-lookup"><span data-stu-id="048ef-126">Multiple messages cannot be processed at the same time.</span></span>  
  
-   <span data-ttu-id="048ef-127">透過 ThinNet 送回回應文件並轉換為 XML，然後再傳回給 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="048ef-127">The response document is sent back through ThinNet, converted to XML, and transmitted back to BizTalk Server.</span></span>  
  
## <a name="outbound-events-at-design-time"></a><span data-ttu-id="048ef-128">設計階段的輸出事件</span><span class="sxs-lookup"><span data-stu-id="048ef-128">Outbound Events at Design Time</span></span>  
  
-   <span data-ttu-id="048ef-129">無法以系統化方式建立事件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="048ef-129">No systematic creation of event metadata is available.</span></span>  
  
-   <span data-ttu-id="048ef-130">必須將事件文件的摹本提供給 Visual Studio，以便產生結構描述並將之連同目標命名空間一起併入專案中。</span><span class="sxs-lookup"><span data-stu-id="048ef-130">A facsimile of the event document must be supplied to Visual Studio so that a schema can be generated and incorporated into the project along with the target namespace.</span></span>  
  
## <a name="outbound-events-at-run-time"></a><span data-ttu-id="048ef-131">執行階段的輸出事件</span><span class="sxs-lookup"><span data-stu-id="048ef-131">Outbound Events at Run Time</span></span>  
  
-   <span data-ttu-id="048ef-132">JD Edwards EnterpriseOne 伺服器中會建立檔案傳輸機制，以將結果產生的 XML 文件 (在事件完成時觸發) 傳輸至該電腦上的目標目錄。</span><span class="sxs-lookup"><span data-stu-id="048ef-132">A file transport mechanism is established in the JD Edwards EnterpriseOne server to transport the resulting XML document, triggered by the event completion, to the target directory on that computer.</span></span>  
  
-   <span data-ttu-id="048ef-133">BizTalk Server 電腦有個對應磁碟機對應至 EnterpriseOne 伺服器上的該目錄。</span><span class="sxs-lookup"><span data-stu-id="048ef-133">The BizTalk Server computer has a mapped drive to the directory on the EnterpriseOne server.</span></span>  
  
-   <span data-ttu-id="048ef-134">接收埠傳輸屬性會針對該對應磁碟機做好設定。</span><span class="sxs-lookup"><span data-stu-id="048ef-134">The receive port transport properties are configured for the mapped drive.</span></span> <span data-ttu-id="048ef-135">接收埠會接收由 EnterpriseOne 伺服器公佈至某個目錄的訊息。</span><span class="sxs-lookup"><span data-stu-id="048ef-135">The receive port receives messages, which are posted to a directory by the EnterpriseOne server.</span></span>  
  
-   <span data-ttu-id="048ef-136">識別目標命名空間可確保將正確的訊息路由傳送至所設定的接收埠。</span><span class="sxs-lookup"><span data-stu-id="048ef-136">The target namespace identification ensures that the correct messages are routed to the configured receive port</span></span>  
  
-   <span data-ttu-id="048ef-137">接收埠會在 BizTalk Server 中提交 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="048ef-137">The receive port submits the XML document in BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048ef-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="048ef-138">See Also</span></span>  
 [<span data-ttu-id="048ef-139">規劃與架構</span><span class="sxs-lookup"><span data-stu-id="048ef-139">Planning and Architecture</span></span>](../core/planning-and-architecture8.md)