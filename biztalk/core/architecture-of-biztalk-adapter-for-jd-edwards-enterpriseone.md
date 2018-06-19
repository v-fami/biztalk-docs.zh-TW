---
title: BizTalk Adapter for JD Edwards EnterpriseOne 的架構 |Microsoft 文件
description: 在設計階段和執行的階段在 JD Edwards EnterpriseOne 配接器在 BizTalk 中，在設計階段和執行的階段，以及輸出的事件描述輸入的服務
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0441c5d2-6a46-45b6-8ab5-0bdac3590f56
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b495ee9a34cf464bd5cc11caed53c5df54948a49
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013757"
---
# <a name="architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone"></a><span data-ttu-id="01844-103">BizTalk Adapter for JD Edwards EnterpriseOne 的架構</span><span class="sxs-lookup"><span data-stu-id="01844-103">Architecture of BizTalk Adapter for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="01844-104">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 可讓您存取 JD Edwards EnterpriseOne 商務功能。</span><span class="sxs-lookup"><span data-stu-id="01844-104">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides access to JD Edwards EnterpriseOne business functions.</span></span> <span data-ttu-id="01844-105">JD Edwards EnterpriseOne 會使用名為 JDENet 的專屬傳訊架構，在用戶端與伺服器電腦之間通訊。</span><span class="sxs-lookup"><span data-stu-id="01844-105">JD Edwards EnterpriseOne communicates between client and server machines using a proprietary messaging architecture called JDENet.</span></span> <span data-ttu-id="01844-106">JDENet 是由 JAR 檔案 Connector.jar 和 Kernel.jar 中的 JD Edwards EnterpriseOne 連接器類別實作。</span><span class="sxs-lookup"><span data-stu-id="01844-106">JDENet is implemented by the JD Edwards EnterpriseOne connector classes found in the JAR files, Connector.jar and Kernel.jar.</span></span> <span data-ttu-id="01844-107">以 TCP/IP 做為傳輸通訊協定，與預設連接埠 6009 或 6010 來實作通訊。</span><span class="sxs-lookup"><span data-stu-id="01844-107">Communication is implemented using TCP/IP as a transport protocol, with a default port of 6009 or 6010.</span></span> <span data-ttu-id="01844-108">此值設定為位置的描述，請參閱[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)。</span><span class="sxs-lookup"><span data-stu-id="01844-108">For a description of where this value is set, see [Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md).</span></span>  
  
 <span data-ttu-id="01844-109">下圖顯示 BizTalk Adapter for JD Edwards EnterpriseOne 的架構。</span><span class="sxs-lookup"><span data-stu-id="01844-109">The following figure shows the architecture for BizTalk Adapter for JD Edwards EnterpriseOne.</span></span>  
  
 ![](../core/media/jd-enterpriseone-arch.gif "JD_EnterpriseOne_arch")  
  
## <a name="inbound-services-at-design-time"></a><span data-ttu-id="01844-110">設計階段的輸入服務</span><span class="sxs-lookup"><span data-stu-id="01844-110">Inbound Services at Design Time</span></span>  
  
-   <span data-ttu-id="01844-111">在設計階段，您會建立連接埠、選取配接器並提供認證資訊，以連接至目標 JD Edwards EnterpriseOne 伺服器。</span><span class="sxs-lookup"><span data-stu-id="01844-111">At design time, you create a port, select an adapter, and provide credential information to connect to the target JD Edwards EnterpriseOne server.</span></span> <span data-ttu-id="01844-112">Visual Studio 開發環境會呼叫配接器架構，以要求此連接埠的設計階段資訊。</span><span class="sxs-lookup"><span data-stu-id="01844-112">The Visual Studio development environment calls the adapter framework to request design-time information for this port.</span></span> <span data-ttu-id="01844-113">配接器會針對此連接埠使用 Browsingagent。</span><span class="sxs-lookup"><span data-stu-id="01844-113">The adapter uses the Browsingagent for this port.</span></span>  
  
-   <span data-ttu-id="01844-114">在設計階段，BizTalk Server 會對配接器進行呼叫來要求資訊。</span><span class="sxs-lookup"><span data-stu-id="01844-114">At design time, BizTalk Server requests information by making calls to the adapter.</span></span>  
  
-   <span data-ttu-id="01844-115">Browsingagent 會將要求轉換成原生 JD Edwards EnterpriseOne 程式碼，再透過 ThinNet API 連線 (建立於 Connector.jar and Kernel.jar 中) 將要求傳輸至 JD Edwards EnterpriseOne。</span><span class="sxs-lookup"><span data-stu-id="01844-115">The Browsingagent converts the request into native JD Edwards EnterpriseOne code and transmits the requests to JD Edwards EnterpriseOne through the ThinNet API connection (established in Connector.jar and Kernel.jar).</span></span>  
  
-   <span data-ttu-id="01844-116">最初會傳回 JD Edwards EnterpriseOne 中模組的清單並傳輸至 Visual Studio 開發環境，以填入配接器精靈。</span><span class="sxs-lookup"><span data-stu-id="01844-116">A list of Modules in JD Edwards EnterpriseOne is initially returned and transported to the Visual Studio development environment, where it populates the Adapter Wizard.</span></span>  
  
-   <span data-ttu-id="01844-117">您可以先顯示程式庫名稱，再顯示模組名稱，來逐漸展開階層。</span><span class="sxs-lookup"><span data-stu-id="01844-117">You can expand the hierarchy by displaying the library name and then the module name.</span></span>  
  
-   <span data-ttu-id="01844-118">當您 選取特定模組時，您會看見模組內所有功能的結構描述 。</span><span class="sxs-lookup"><span data-stu-id="01844-118">When you select a specific module, you see schemas for all functions within the module.</span></span> <span data-ttu-id="01844-119">配接器會從 JD Edwards EnterpriseOne 取得必要資訊，而 Browsingagent 會建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="01844-119">The adapter gets the required information from JD Edwards EnterpriseOne, and the browsingagent creates the schemas.</span></span>  
  
-   <span data-ttu-id="01844-120">結構描述隨即新增至 BizTalk Server 專案協調流程。</span><span class="sxs-lookup"><span data-stu-id="01844-120">The schemas are added to the BizTalk Server project orchestration.</span></span>  
  
## <a name="inbound-services-at-run-time"></a><span data-ttu-id="01844-121">執行階段的輸入服務</span><span class="sxs-lookup"><span data-stu-id="01844-121">Inbound Services at Run Time</span></span>  
  
-   <span data-ttu-id="01844-122">BizTalk Server 會呼叫配接器，以在特定連接埠上傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="01844-122">BizTalk Server calls the adapter to send a message on a specific port.</span></span>  
  
-   <span data-ttu-id="01844-123">執行階段代理程式會將 XML 轉換成原生 JDE 程式碼。</span><span class="sxs-lookup"><span data-stu-id="01844-123">The run-time agent converts the XML into native JDE code.</span></span>  
  
-   <span data-ttu-id="01844-124">執行階段代理程式會透過 ThinNet，將要求提交給傳送埠的傳輸屬性中所指定的 JD Edwards EnterpriseOne 系統。</span><span class="sxs-lookup"><span data-stu-id="01844-124">The run-time agent submits the request through the ThinNet to the JD Edwards EnterpriseOne system specified in the transport properties of the send port.</span></span>  
  
-   <span data-ttu-id="01844-125">「主要商務功能」會在 JD Edwards EnterpriseOne 系統上執行，然後該系統會產生回應文件，指示執行成功或失敗以及商務功能所傳回的資料參數。</span><span class="sxs-lookup"><span data-stu-id="01844-125">The Master Business Function is executed on the JD Edwards EnterpriseOne system, which then generates a response document indicating success or failure as well as data parameters returned by the business function.</span></span>  
  
-   <span data-ttu-id="01844-126">傳送至 JD Edwards EnterpriseOne 的訊息是單一訊息、單一回覆架構。</span><span class="sxs-lookup"><span data-stu-id="01844-126">The message sent to JD Edwards EnterpriseOne is a single message, single reply architecture.</span></span> <span data-ttu-id="01844-127">系統無法同時處理多則訊息。</span><span class="sxs-lookup"><span data-stu-id="01844-127">Multiple messages cannot be processed at the same time.</span></span>  
  
-   <span data-ttu-id="01844-128">透過 ThinNet 送回回應文件並轉換為 XML，然後再傳回給 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="01844-128">The response document is sent back through ThinNet, converted to XML, and transmitted back to BizTalk Server.</span></span>  
  
## <a name="outbound-events-at-design-time"></a><span data-ttu-id="01844-129">設計階段的輸出事件</span><span class="sxs-lookup"><span data-stu-id="01844-129">Outbound Events at Design Time</span></span>  
  
-   <span data-ttu-id="01844-130">無法以系統化方式建立事件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="01844-130">No systematic creation of event metadata is available.</span></span>  
  
-   <span data-ttu-id="01844-131">必須將事件文件的摹本提供給 Visual Studio，以便產生結構描述並將之連同目標命名空間一起併入專案中。</span><span class="sxs-lookup"><span data-stu-id="01844-131">A facsimile of the event document must be supplied to Visual Studio so that a schema can be generated and incorporated into the project along with the target namespace.</span></span>  
  
## <a name="outbound-events-at-run-time"></a><span data-ttu-id="01844-132">執行階段的輸出事件</span><span class="sxs-lookup"><span data-stu-id="01844-132">Outbound Events at Run Time</span></span>  
  
-   <span data-ttu-id="01844-133">JD Edwards EnterpriseOne 伺服器中會建立檔案傳輸機制，以將結果產生的 XML 文件 (在事件完成時觸發) 傳輸至該電腦上的目標目錄。</span><span class="sxs-lookup"><span data-stu-id="01844-133">A file transport mechanism is established in the JD Edwards EnterpriseOne server to transport the resulting XML document, triggered by the event completion, to the target directory on that computer.</span></span>  
  
-   <span data-ttu-id="01844-134">BizTalk Server 電腦有個對應磁碟機對應至 EnterpriseOne 伺服器上的該目錄。</span><span class="sxs-lookup"><span data-stu-id="01844-134">The BizTalk Server computer has a mapped drive to the directory on the EnterpriseOne server.</span></span>  
  
-   <span data-ttu-id="01844-135">接收埠傳輸屬性會針對該對應磁碟機做好設定。</span><span class="sxs-lookup"><span data-stu-id="01844-135">The receive port transport properties are configured for the mapped drive.</span></span> <span data-ttu-id="01844-136">接收埠會接收由 EnterpriseOne 伺服器公佈至某個目錄的訊息。</span><span class="sxs-lookup"><span data-stu-id="01844-136">The receive port receives messages, which are posted to a directory by the EnterpriseOne server.</span></span>  
  
-   <span data-ttu-id="01844-137">識別目標命名空間可確保將正確的訊息路由傳送至所設定的接收埠。</span><span class="sxs-lookup"><span data-stu-id="01844-137">The target namespace identification ensures that the correct messages are routed to the configured receive port</span></span>  
  
-   <span data-ttu-id="01844-138">接收埠會在 BizTalk Server 中提交 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="01844-138">The receive port submits the XML document in BizTalk Server.</span></span>  
  
## <a name="more-good-stuff"></a><span data-ttu-id="01844-139">更多實用功能</span><span class="sxs-lookup"><span data-stu-id="01844-139">More good stuff</span></span>
[<span data-ttu-id="01844-140">BizTalk Adapter for JD Edwards EnterpriseOne 中的安全性</span><span class="sxs-lookup"><span data-stu-id="01844-140">Security in BizTalk Adapter for JD Edwards EnterpriseOne</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)  
[<span data-ttu-id="01844-141">建立應用程式成品</span><span class="sxs-lookup"><span data-stu-id="01844-141">Create the application artifacts</span></span>](../core/developing-applications2.md)  
[<span data-ttu-id="01844-142">匯入您的 JD Edwards EnterpriseOne 應用程式</span><span class="sxs-lookup"><span data-stu-id="01844-142">Import your JD Edwards EnterpriseOne app</span></span>](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)  
[<span data-ttu-id="01844-143">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="01844-143">Use BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling3.md)  
[<span data-ttu-id="01844-144">疑難排解</span><span class="sxs-lookup"><span data-stu-id="01844-144">Troubleshoot</span></span>](../core/troubleshooting-jd-edwards-enterpriseone.md)  
