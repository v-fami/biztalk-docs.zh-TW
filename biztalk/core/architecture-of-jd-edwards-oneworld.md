---
title: "JD Edwards OneWorld 的架構 |Microsoft 文件"
description: "在設計階段和執行的階段在 JD Edwards OneWorld 配接器在 BizTalk 中，在設計階段和執行的階段，以及輸出的事件描述輸入的服務"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9200a090-a587-4b60-9447-d281580f2078
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f866e5d72e392136d19c155785aaf6b71db2ce3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-jd-edwards-oneworld"></a><span data-ttu-id="31e7d-103">JD Edwards OneWorld 的結構</span><span class="sxs-lookup"><span data-stu-id="31e7d-103">Architecture of JD Edwards OneWorld</span></span>
<span data-ttu-id="31e7d-104">Microsoft BizTalk Adapter for JD Edwards OneWorld 提供對 JD Edwards OneWorld 商務功能的存取 。</span><span class="sxs-lookup"><span data-stu-id="31e7d-104">Microsoft BizTalk Adapter for JD Edwards OneWorld provides access to JD Edwards OneWorld business functions.</span></span> <span data-ttu-id="31e7d-105">JD Edwards OneWorld 會使用名為 JDENet 的專屬傳訊架構進行用戶端與伺服器電腦之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="31e7d-105">JD Edwards OneWorld communicates between client and server machines using a proprietary messaging architecture called JDENet.</span></span> <span data-ttu-id="31e7d-106">JDENet 是由 JAR 檔案 Connector.jar 和 Kernel.jar 中的 JD Edwards OneWorld 連接器類別實作。</span><span class="sxs-lookup"><span data-stu-id="31e7d-106">JDENet is implemented by the JD Edwards OneWorld connector classes found in the JAR files, Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="31e7d-107">以 TCP/IP 做為傳輸通訊協定，與預設連接埠 6009 或 6010 來實作通訊。</span><span class="sxs-lookup"><span data-stu-id="31e7d-107">Communication is implemented using TCP/IP as a transport protocol, with a default port of 6009 or 6010.</span></span> <span data-ttu-id="31e7d-108">此值設定為位置的描述，請參閱[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)。</span><span class="sxs-lookup"><span data-stu-id="31e7d-108">For a description of where this value is set, see [Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md).</span></span>  
  
 <span data-ttu-id="31e7d-109">**BizTalk Adapter for JD Edwards OneWorld 的架構**</span><span class="sxs-lookup"><span data-stu-id="31e7d-109">**Architecture for BizTalk Adapter for JD Edwards OneWorld**</span></span>  
  
 ![](../core/media/jdedadapter-01-architecture.gif "JDEdAdapter_01_Architecture")  
  
 <span data-ttu-id="31e7d-110">呼叫 JD Edwards OneWorld 商務功能需要兩個訊息：</span><span class="sxs-lookup"><span data-stu-id="31e7d-110">Calls to JD Edwards OneWorld business functions require two messages:</span></span>  
  
-   <span data-ttu-id="31e7d-111">第一個訊息會以處理商務功能的伺服器位置來回應。</span><span class="sxs-lookup"><span data-stu-id="31e7d-111">The first message responds with the location of the server that processes the business function.</span></span> <span data-ttu-id="31e7d-112">這會透過一組資料表呼叫中執行查閱*物件組態對應 (OCM)*。</span><span class="sxs-lookup"><span data-stu-id="31e7d-112">This is accomplished by performing a lookup in a set of tables called *object configuration mapping (OCM)*.</span></span>  
  
-   <span data-ttu-id="31e7d-113">第二個訊息會將格式化的訊息緩衝區 (含有要與 JD Edwards OneWorld 之間往返傳遞的參數) 傳送至適當的伺服器，然後等待回覆。</span><span class="sxs-lookup"><span data-stu-id="31e7d-113">The second message sends a formatted message buffer containing the arguments to pass to or from JD Edwards OneWorld to the appropriate server, and waits for a reply.</span></span> <span data-ttu-id="31e7d-114">緩衝區是根據基礎 C + + 結構 (struct) 的 typedef 進行格式化。</span><span class="sxs-lookup"><span data-stu-id="31e7d-114">The buffers are formatted according to the typedefs of the underlying C++ structs.</span></span>  
  
## <a name="inbound-services-at-design-time"></a><span data-ttu-id="31e7d-115">設計階段的輸入服務</span><span class="sxs-lookup"><span data-stu-id="31e7d-115">Inbound Services at Design Time</span></span>  
  
-   <span data-ttu-id="31e7d-116">在設計階段，您會建立連接埠、選取配接器，並提供連接至目標 JD Edwards OneWorld 伺服器所需的認證資訊。</span><span class="sxs-lookup"><span data-stu-id="31e7d-116">At design time, you create your port, select the adapter, and provide credential information to connect to the target JD Edwards OneWorld server.</span></span> <span data-ttu-id="31e7d-117">Visual Studio 開發環境會呼叫配接器架構，以要求此連接埠的設計階段資訊。</span><span class="sxs-lookup"><span data-stu-id="31e7d-117">The Visual Studio development environment calls the adapter framework to request design-time information for this port.</span></span> <span data-ttu-id="31e7d-118">BizTalk Adapter for JD Edwards OneWorld 則會針對此連接埠使用 Browsingagent。</span><span class="sxs-lookup"><span data-stu-id="31e7d-118">BizTalk Adapter for JD Edwards OneWorld uses the Browsingagent for this port.</span></span>  
  
-   <span data-ttu-id="31e7d-119">在設計階段，BizTalk Server 會對配接器進行呼叫來要求資訊。</span><span class="sxs-lookup"><span data-stu-id="31e7d-119">At design time, BizTalk Server requests information by making calls to the adapter.</span></span>  
  
-   <span data-ttu-id="31e7d-120">Browsingagent 會將要求轉換為 JD Edwards OneWorld 機器碼，然後透過 ThinNet API 連線 (以 Connector.jar 和 Kernel.jar 建立) 將要求傳輸至 JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="31e7d-120">The Browsingagent converts the request into native JD Edwards OneWorld code and then transmits the requests to JD Edwards OneWorld through the ThinNet API connection (established in the Connector and Kernel.jars).</span></span>  
  
-   <span data-ttu-id="31e7d-121">自訂商務功能透過 BTSREL 安裝來安裝： 它會公開主要商務功能。</span><span class="sxs-lookup"><span data-stu-id="31e7d-121">A custom business function is installed through the BTSREL installation: it exposes the master business functions.</span></span>  
  
-   <span data-ttu-id="31e7d-122">一開始會傳回 JD Edwards OneWorld 中的模組清單並將此清單傳輸至 Visual Studio，而 Visual Studio 會將此清單填入「配接器精靈」。</span><span class="sxs-lookup"><span data-stu-id="31e7d-122">A list of modules in JD Edwards OneWorld is initially returned and transported to Visual Studio, where it populates the Adapter Wizard.</span></span>  
  
-   <span data-ttu-id="31e7d-123">您可以展開階層，以顯示程式庫名稱和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="31e7d-123">You can expand the hierarchy to display the library name and module name.</span></span>  
  
-   <span data-ttu-id="31e7d-124">當您 選取特定模組時，您會看見模組內所有功能的結構描述 。</span><span class="sxs-lookup"><span data-stu-id="31e7d-124">When you select a specific module, you see schemas for all functions within the module.</span></span> <span data-ttu-id="31e7d-125">配接器會從 JD Edwards OneWorld 取得必要資訊，而 Browsingagent 會建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="31e7d-125">The adapter obtains the required information from JD Edwards OneWorld, and the browsingagent creates the schemas.</span></span>  
  
-   <span data-ttu-id="31e7d-126">結構描述隨即新增至 BizTalk Server 專案協調流程。</span><span class="sxs-lookup"><span data-stu-id="31e7d-126">The schemas are added to the BizTalk Server project orchestration.</span></span>  
  
## <a name="inbound-services-at-run-time"></a><span data-ttu-id="31e7d-127">執行階段的輸入服務</span><span class="sxs-lookup"><span data-stu-id="31e7d-127">Inbound Services at Run Time</span></span>  
  
-   <span data-ttu-id="31e7d-128">BizTalk Server 會呼叫 BizTalk Adapter for JD Edwards OneWorld，以在特定連接埠上傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="31e7d-128">BizTalk Server calls the BizTalk Adapter for JD Edwards OneWorld to send a message on a specific port.</span></span>  
  
-   <span data-ttu-id="31e7d-129">執行階段代理程式會將 XML 轉換成 JD Edwards 機器碼。</span><span class="sxs-lookup"><span data-stu-id="31e7d-129">The run-time agent converts the XML into native JD Edwards code.</span></span>  
  
-   <span data-ttu-id="31e7d-130">執行階段代理程式會透過 ThinNet 將要求提交至在傳送埠的傳輸屬性中指定的 JD Edwards 企業系統。</span><span class="sxs-lookup"><span data-stu-id="31e7d-130">The run-time agent submits the request through the ThinNet to the JD Edwards enterprise system specified in the transport properties of the send port.</span></span>  
  
-   <span data-ttu-id="31e7d-131">主要商務功能會在 JD Edwards 系統上執行，而該系統會接著產生回應文件，指出執行成功與否以及此商務功能所傳回的資料參數。</span><span class="sxs-lookup"><span data-stu-id="31e7d-131">The master business function is executed on the JD Edwards system, which then generates a response document indicating success or failure as well as data parameters returned by the business function.</span></span>  
  
-   <span data-ttu-id="31e7d-132">傳送至 JD Edwards OneWorld 的訊息是單一訊息、單一回覆架構。</span><span class="sxs-lookup"><span data-stu-id="31e7d-132">The message sent to JD Edwards OneWorld is a single message, single reply architecture.</span></span> <span data-ttu-id="31e7d-133">系統無法同時處理多則訊息。</span><span class="sxs-lookup"><span data-stu-id="31e7d-133">Multiple messages cannot be processed at the same time.</span></span>  
  
-   <span data-ttu-id="31e7d-134">透過 ThinNet 送回回應文件並轉換為 XML，然後再傳回給 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="31e7d-134">The response document is sent back through ThinNet, converted to XML, and transmitted back to BizTalk Server.</span></span>  
  
## <a name="outbound-events-at-design-time"></a><span data-ttu-id="31e7d-135">設計階段的輸出事件</span><span class="sxs-lookup"><span data-stu-id="31e7d-135">Outbound Events at Design Time</span></span>  
  
-   <span data-ttu-id="31e7d-136">無法以系統化方式建立事件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e7d-136">No systematic creation of event metadata is available.</span></span>  
  
-   <span data-ttu-id="31e7d-137">必須將事件文件的摹本提供給 Visual Studio，以便產生結構描述並將之連同目標命名空間一起併入專案中。</span><span class="sxs-lookup"><span data-stu-id="31e7d-137">A facsimile of the event document must be supplied to Visual Studio so that a schema can be generated and incorporated into the project along with the target namespace.</span></span>  
  
## <a name="outbound-events-at-run-time"></a><span data-ttu-id="31e7d-138">執行階段的輸出事件</span><span class="sxs-lookup"><span data-stu-id="31e7d-138">Outbound Events at Run Time</span></span>  
  
-   <span data-ttu-id="31e7d-139">JD Edwards 企業伺服器中會建立檔案傳輸機制，以將結果產生的 XML 文件 (在事件完成時觸發) 傳輸至該伺服器上的目標目錄。</span><span class="sxs-lookup"><span data-stu-id="31e7d-139">A file transport mechanism is established in the JD Edwards enterprise server to transport the resulting XML document, triggered by the event completion, to the target directory on that server.</span></span>  
  
-   <span data-ttu-id="31e7d-140">BizTalk Server 電腦有個對應磁碟機會對應至企業伺服器上的該目錄。</span><span class="sxs-lookup"><span data-stu-id="31e7d-140">The BizTalk Server computer has a mapped drive to the directory on the enterprise server.</span></span>  
  
-   <span data-ttu-id="31e7d-141">接收埠傳輸屬性會針對該對應磁碟機做好設定。</span><span class="sxs-lookup"><span data-stu-id="31e7d-141">The receive port transport properties are configured for the mapped drive.</span></span> <span data-ttu-id="31e7d-142">接收埠會 接收由企業伺服器公佈至目錄的訊息 。</span><span class="sxs-lookup"><span data-stu-id="31e7d-142">The receive port receives messages posted to directory by the enterprise server.</span></span>  
  
-   <span data-ttu-id="31e7d-143">識別的目標命名空間可確保會將正確的訊息路由傳送至所設定的接收埠。</span><span class="sxs-lookup"><span data-stu-id="31e7d-143">The target namespace identification ensures that the correct messages are routed to the configured receive port.</span></span>  
  
-   <span data-ttu-id="31e7d-144">接收埠會將 XML 文件提交至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="31e7d-144">The receive port submits the XML document to BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e7d-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31e7d-145">See Also</span></span>  
 <span data-ttu-id="31e7d-146">[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="31e7d-146">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="31e7d-147">規劃和架構</span><span class="sxs-lookup"><span data-stu-id="31e7d-147">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)