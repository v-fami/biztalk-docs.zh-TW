---
title: "JD Edwards OneWorld 的架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: architecture
ms.assetid: 9200a090-a587-4b60-9447-d281580f2078
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1daee7d44152817da1ac536dd98cbaf898e2ac7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-jd-edwards-oneworld"></a><span data-ttu-id="62178-102">JD Edwards OneWorld 的結構</span><span class="sxs-lookup"><span data-stu-id="62178-102">Architecture of JD Edwards OneWorld</span></span>
<span data-ttu-id="62178-103">Microsoft BizTalk Adapter for JD Edwards OneWorld 提供對 JD Edwards OneWorld 商務功能的存取 。</span><span class="sxs-lookup"><span data-stu-id="62178-103">Microsoft BizTalk Adapter for JD Edwards OneWorld provides access to JD Edwards OneWorld business functions.</span></span> <span data-ttu-id="62178-104">JD Edwards OneWorld 會使用名為 JDENet 的專屬傳訊架構進行用戶端與伺服器電腦之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="62178-104">JD Edwards OneWorld communicates between client and server machines using a proprietary messaging architecture called JDENet.</span></span> <span data-ttu-id="62178-105">JDENet 是由 JAR 檔案 Connector.jar 和 Kernel.jar 中的 JD Edwards OneWorld 連接器類別實作。</span><span class="sxs-lookup"><span data-stu-id="62178-105">JDENet is implemented by the JD Edwards OneWorld connector classes found in the JAR files, Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="62178-106">以 TCP/IP 做為傳輸通訊協定，與預設連接埠 6009 或 6010 來實作通訊。</span><span class="sxs-lookup"><span data-stu-id="62178-106">Communication is implemented using TCP/IP as a transport protocol, with a default port of 6009 or 6010.</span></span> <span data-ttu-id="62178-107">此值設定為位置的描述，請參閱[如何設定 JD Edwards OneWorld 傳輸屬性](../core/how-to-set-jd-edwards-oneworld-transport-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="62178-107">For a description of where this value is set, see [How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md).</span></span>  
  
 <span data-ttu-id="62178-108">**BizTalk Adapter for JD Edwards OneWorld 的架構**</span><span class="sxs-lookup"><span data-stu-id="62178-108">**Architecture for BizTalk Adapter for JD Edwards OneWorld**</span></span>  
  
 ![](../core/media/jdedadapter-01-architecture.gif "JDEdAdapter_01_Architecture")  
  
 <span data-ttu-id="62178-109">呼叫 JD Edwards OneWorld 商務功能需要兩個訊息：</span><span class="sxs-lookup"><span data-stu-id="62178-109">Calls to JD Edwards OneWorld business functions require two messages:</span></span>  
  
-   <span data-ttu-id="62178-110">第一個訊息會以處理商務功能的伺服器位置來回應。</span><span class="sxs-lookup"><span data-stu-id="62178-110">The first message responds with the location of the server that processes the business function.</span></span> <span data-ttu-id="62178-111">這會透過一組資料表呼叫中執行查閱*物件組態對應 (OCM)*。</span><span class="sxs-lookup"><span data-stu-id="62178-111">This is accomplished by performing a lookup in a set of tables called *object configuration mapping (OCM)*.</span></span>  
  
-   <span data-ttu-id="62178-112">第二個訊息會將格式化的訊息緩衝區 (含有要與 JD Edwards OneWorld 之間往返傳遞的參數) 傳送至適當的伺服器，然後等待回覆。</span><span class="sxs-lookup"><span data-stu-id="62178-112">The second message sends a formatted message buffer containing the arguments to pass to or from JD Edwards OneWorld to the appropriate server, and waits for a reply.</span></span> <span data-ttu-id="62178-113">緩衝區是根據基礎 C + + 結構 (struct) 的 typedef 進行格式化。</span><span class="sxs-lookup"><span data-stu-id="62178-113">The buffers are formatted according to the typedefs of the underlying C++ structs.</span></span>  
  
## <a name="inbound-services-at-design-time"></a><span data-ttu-id="62178-114">設計階段的輸入服務</span><span class="sxs-lookup"><span data-stu-id="62178-114">Inbound Services at Design Time</span></span>  
  
-   <span data-ttu-id="62178-115">在設計階段，您會建立連接埠、選取配接器，並提供連接至目標 JD Edwards OneWorld 伺服器所需的認證資訊。</span><span class="sxs-lookup"><span data-stu-id="62178-115">At design time, you create your port, select the adapter, and provide credential information to connect to the target JD Edwards OneWorld server.</span></span> <span data-ttu-id="62178-116">Visual Studio 開發環境會呼叫配接器架構，以要求此連接埠的設計階段資訊。</span><span class="sxs-lookup"><span data-stu-id="62178-116">The Visual Studio development environment calls the adapter framework to request design-time information for this port.</span></span> <span data-ttu-id="62178-117">BizTalk Adapter for JD Edwards OneWorld 則會針對此連接埠使用 Browsingagent。</span><span class="sxs-lookup"><span data-stu-id="62178-117">BizTalk Adapter for JD Edwards OneWorld uses the Browsingagent for this port.</span></span>  
  
-   <span data-ttu-id="62178-118">在設計階段，BizTalk Server 會對配接器進行呼叫來要求資訊。</span><span class="sxs-lookup"><span data-stu-id="62178-118">At design time, BizTalk Server requests information by making calls to the adapter.</span></span>  
  
-   <span data-ttu-id="62178-119">Browsingagent 會將要求轉換為 JD Edwards OneWorld 機器碼，然後透過 ThinNet API 連線 (以 Connector.jar 和 Kernel.jar 建立) 將要求傳輸至 JD Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="62178-119">The Browsingagent converts the request into native JD Edwards OneWorld code and then transmits the requests to JD Edwards OneWorld through the ThinNet API connection (established in the Connector and Kernel.jars).</span></span>  
  
-   <span data-ttu-id="62178-120">自訂商務功能透過 BTSREL 安裝來安裝： 它會公開主要商務功能。</span><span class="sxs-lookup"><span data-stu-id="62178-120">A custom business function is installed through the BTSREL installation: it exposes the master business functions.</span></span>  
  
-   <span data-ttu-id="62178-121">一開始會傳回 JD Edwards OneWorld 中的模組清單並將此清單傳輸至 Visual Studio，而 Visual Studio 會將此清單填入「配接器精靈」。</span><span class="sxs-lookup"><span data-stu-id="62178-121">A list of modules in JD Edwards OneWorld is initially returned and transported to Visual Studio, where it populates the Adapter Wizard.</span></span>  
  
-   <span data-ttu-id="62178-122">您可以展開階層，以顯示程式庫名稱和模組名稱。</span><span class="sxs-lookup"><span data-stu-id="62178-122">You can expand the hierarchy to display the library name and module name.</span></span>  
  
-   <span data-ttu-id="62178-123">當您 選取特定模組時，您會看見模組內所有功能的結構描述 。</span><span class="sxs-lookup"><span data-stu-id="62178-123">When you select a specific module, you see schemas for all functions within the module.</span></span> <span data-ttu-id="62178-124">配接器會從 JD Edwards OneWorld 取得必要資訊，而 Browsingagent 會建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="62178-124">The adapter obtains the required information from JD Edwards OneWorld, and the browsingagent creates the schemas.</span></span>  
  
-   <span data-ttu-id="62178-125">結構描述隨即新增至 BizTalk Server 專案協調流程。</span><span class="sxs-lookup"><span data-stu-id="62178-125">The schemas are added to the BizTalk Server project orchestration.</span></span>  
  
## <a name="inbound-services-at-run-time"></a><span data-ttu-id="62178-126">執行階段的輸入服務</span><span class="sxs-lookup"><span data-stu-id="62178-126">Inbound Services at Run Time</span></span>  
  
-   <span data-ttu-id="62178-127">BizTalk Server 會呼叫 BizTalk Adapter for JD Edwards OneWorld，以在特定連接埠上傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="62178-127">BizTalk Server calls the BizTalk Adapter for JD Edwards OneWorld to send a message on a specific port.</span></span>  
  
-   <span data-ttu-id="62178-128">執行階段代理程式會將 XML 轉換成 JD Edwards 機器碼。</span><span class="sxs-lookup"><span data-stu-id="62178-128">The run-time agent converts the XML into native JD Edwards code.</span></span>  
  
-   <span data-ttu-id="62178-129">執行階段代理程式會透過 ThinNet 將要求提交至在傳送埠的傳輸屬性中指定的 JD Edwards 企業系統。</span><span class="sxs-lookup"><span data-stu-id="62178-129">The run-time agent submits the request through the ThinNet to the JD Edwards enterprise system specified in the transport properties of the send port.</span></span>  
  
-   <span data-ttu-id="62178-130">主要商務功能會在 JD Edwards 系統上執行，而該系統會接著產生回應文件，指出執行成功與否以及此商務功能所傳回的資料參數。</span><span class="sxs-lookup"><span data-stu-id="62178-130">The master business function is executed on the JD Edwards system, which then generates a response document indicating success or failure as well as data parameters returned by the business function.</span></span>  
  
-   <span data-ttu-id="62178-131">傳送至 JD Edwards OneWorld 的訊息是單一訊息、單一回覆架構。</span><span class="sxs-lookup"><span data-stu-id="62178-131">The message sent to JD Edwards OneWorld is a single message, single reply architecture.</span></span> <span data-ttu-id="62178-132">系統無法同時處理多則訊息。</span><span class="sxs-lookup"><span data-stu-id="62178-132">Multiple messages cannot be processed at the same time.</span></span>  
  
-   <span data-ttu-id="62178-133">透過 ThinNet 送回回應文件並轉換為 XML，然後再傳回給 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="62178-133">The response document is sent back through ThinNet, converted to XML, and transmitted back to BizTalk Server.</span></span>  
  
## <a name="outbound-events-at-design-time"></a><span data-ttu-id="62178-134">設計階段的輸出事件</span><span class="sxs-lookup"><span data-stu-id="62178-134">Outbound Events at Design Time</span></span>  
  
-   <span data-ttu-id="62178-135">無法以系統化方式建立事件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="62178-135">No systematic creation of event metadata is available.</span></span>  
  
-   <span data-ttu-id="62178-136">必須將事件文件的摹本提供給 Visual Studio，以便產生結構描述並將之連同目標命名空間一起併入專案中。</span><span class="sxs-lookup"><span data-stu-id="62178-136">A facsimile of the event document must be supplied to Visual Studio so that a schema can be generated and incorporated into the project along with the target namespace.</span></span>  
  
## <a name="outbound-events-at-run-time"></a><span data-ttu-id="62178-137">執行階段的輸出事件</span><span class="sxs-lookup"><span data-stu-id="62178-137">Outbound Events at Run Time</span></span>  
  
-   <span data-ttu-id="62178-138">JD Edwards 企業伺服器中會建立檔案傳輸機制，以將結果產生的 XML 文件 (在事件完成時觸發) 傳輸至該伺服器上的目標目錄。</span><span class="sxs-lookup"><span data-stu-id="62178-138">A file transport mechanism is established in the JD Edwards enterprise server to transport the resulting XML document, triggered by the event completion, to the target directory on that server.</span></span>  
  
-   <span data-ttu-id="62178-139">BizTalk Server 電腦有個對應磁碟機會對應至企業伺服器上的該目錄。</span><span class="sxs-lookup"><span data-stu-id="62178-139">The BizTalk Server computer has a mapped drive to the directory on the enterprise server.</span></span>  
  
-   <span data-ttu-id="62178-140">接收埠傳輸屬性會針對該對應磁碟機做好設定。</span><span class="sxs-lookup"><span data-stu-id="62178-140">The receive port transport properties are configured for the mapped drive.</span></span> <span data-ttu-id="62178-141">接收埠會 接收由企業伺服器公佈至目錄的訊息 。</span><span class="sxs-lookup"><span data-stu-id="62178-141">The receive port receives messages posted to directory by the enterprise server.</span></span>  
  
-   <span data-ttu-id="62178-142">識別的目標命名空間可確保會將正確的訊息路由傳送至所設定的接收埠。</span><span class="sxs-lookup"><span data-stu-id="62178-142">The target namespace identification ensures that the correct messages are routed to the configured receive port.</span></span>  
  
-   <span data-ttu-id="62178-143">接收埠會將 XML 文件提交至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="62178-143">The receive port submits the XML document to BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62178-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62178-144">See Also</span></span>  
 <span data-ttu-id="62178-145">[如何設定 JD Edwards OneWorld 傳輸屬性](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span><span class="sxs-lookup"><span data-stu-id="62178-145">[How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md) </span></span>  
 [<span data-ttu-id="62178-146">規劃與架構</span><span class="sxs-lookup"><span data-stu-id="62178-146">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)