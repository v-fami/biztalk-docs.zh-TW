---
title: WCF 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e64cd189-8805-4209-bd06-971363f38585
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb77124dbad631cd521a285ff4f036e0545ca819
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290022"
---
# <a name="wcf-adapters"></a><span data-ttu-id="60bf3-102">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-102">WCF Adapters</span></span>

## <a name="overview"></a><span data-ttu-id="60bf3-103">概觀</span><span class="sxs-lookup"><span data-stu-id="60bf3-103">Overview</span></span>
<span data-ttu-id="60bf3-104">適用於 Windows Communication Foundation (WCF) 的 BizTalk 配接器讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 能與 WCF 應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="60bf3-104">The BizTalk Adapters for Windows Communication Foundation (WCF) allow  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to communicate with WCF-based applications.</span></span> <span data-ttu-id="60bf3-105">BizTalk WCF 配接器包括表示 WCF 預先定義繫結的五個實體配接器 —**BasicHttpBinding**， **WsHttpBinding**， **NetTcpBinding**， **NetNamedPipeBinding**，和**NetMsmqBinding**。</span><span class="sxs-lookup"><span data-stu-id="60bf3-105">The BizTalk WCF adapters include five physical adapters that represent the WCF predefined bindings—**BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, and **NetMsmqBinding**.</span></span> <span data-ttu-id="60bf3-106">提供這些表示預先定義繫結之 WCF 配接器的目的，是要讓您能夠輕鬆設定多數應用程式需求的必要資訊。</span><span class="sxs-lookup"><span data-stu-id="60bf3-106">The WCF adapters for the predefined bindings are provided to enable you to easily configure necessary information for most application requirements.</span></span>  
  
 <span data-ttu-id="60bf3-107">BizTalk WCF 配接器也包括兩個配接器，可讓您針對接收位置和傳送埠，自由設定 WCF 繫結和行為資訊。</span><span class="sxs-lookup"><span data-stu-id="60bf3-107">The BizTalk WCF adapters also include two adapters that enable you to freely configure WCF binding and behavior information for the receive location and send port.</span></span>  

## <a name="available-wcf-adapters"></a><span data-ttu-id="60bf3-108">可用的 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-108">Available WCF adapters</span></span>
    
-   <span data-ttu-id="60bf3-109">**Wcf-wshttp 配接器**。</span><span class="sxs-lookup"><span data-stu-id="60bf3-109">**WCF-WSHttp adapter**.</span></span> <span data-ttu-id="60bf3-110">提供透過 HTTP 傳輸的 WS-\* 標準支援。</span><span class="sxs-lookup"><span data-stu-id="60bf3-110">Provides the WS-\* standards support over the HTTP transport.</span></span> <span data-ttu-id="60bf3-111">WCF-WSHttp 配接器會實作下列規格：外部應用程式和 MessageBox 資料庫之間的交易式互動適用的 WS-Transaction，以及訊息安全性和驗證適用的 WS-Security。</span><span class="sxs-lookup"><span data-stu-id="60bf3-111">The WCF-WSHttp adapter implements the following specifications: WS-Transaction for the transactional interactions between external applications and the MessageBox database, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="60bf3-112">傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是「文字」或「訊息傳輸最佳化機制」(Message Transmission Optimization Mechanism，MTOM) 編碼。</span><span class="sxs-lookup"><span data-stu-id="60bf3-112">The transport is HTTP or HTTPS, and message encoding is a Text or Message Transmission Optimization Mechanism (MTOM) encoding.</span></span>  
  
-   <span data-ttu-id="60bf3-113">**Wcf-basichttp 配接器**。</span><span class="sxs-lookup"><span data-stu-id="60bf3-113">**WCF-BasicHttp adapter**.</span></span> <span data-ttu-id="60bf3-114">與 ASMX 架構 Web 服務和用戶端，以及其他符合 WS-I 基本設定檔 1.1 的服務和用戶端進行通訊。</span><span class="sxs-lookup"><span data-stu-id="60bf3-114">Communicates with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span> <span data-ttu-id="60bf3-115">傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是文字編碼。</span><span class="sxs-lookup"><span data-stu-id="60bf3-115">The transport is HTTP or HTTPS, and message encoding is a text encoding.</span></span>  
  
-   <span data-ttu-id="60bf3-116">**Wcf-nettcp 配接器**。</span><span class="sxs-lookup"><span data-stu-id="60bf3-116">**WCF-NetTcp adapter**.</span></span> <span data-ttu-id="60bf3-117">提供透過 TCP 傳輸的 WS-\* 標準支援。</span><span class="sxs-lookup"><span data-stu-id="60bf3-117">Provides the WS-\* standards support over the TCP transport.</span></span> <span data-ttu-id="60bf3-118">WCF-NetTcp 配接器在 WCF-to-WCF 環境中提供有效率的通訊。</span><span class="sxs-lookup"><span data-stu-id="60bf3-118">The WCF-NetTcp adapter provides efficient communication in a WCF-to-WCF environment.</span></span> <span data-ttu-id="60bf3-119">配接器實作下列規格： 交易的交易之間的互動外部應用程式和 MessageBox 資料庫，以及 Ws-security 用於訊息安全性和驗證。</span><span class="sxs-lookup"><span data-stu-id="60bf3-119">The adapter implements the following specifications: WS-Transaction for the transactional interactions between external applications and the MessageBox database, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="60bf3-120">傳輸方式是 TCP，訊息編碼方式則是二進位編碼。</span><span class="sxs-lookup"><span data-stu-id="60bf3-120">The transport is TCP, and message encoding is binary encoding.</span></span>  
  
-   <span data-ttu-id="60bf3-121">**Wcf-netmsmq 配接器**。</span><span class="sxs-lookup"><span data-stu-id="60bf3-121">**WCF-NetMsmq adapter**.</span></span> <span data-ttu-id="60bf3-122">提供利用 [!INCLUDE[btsCoName](../includes/btsconame-md.md)] 訊息佇列 (Message Queuing，MSMQ) 為傳輸方式的佇列支援，並支援鬆散偶合的應用程式、失敗隔離、負載調節，以及已中斷連線作業。</span><span class="sxs-lookup"><span data-stu-id="60bf3-122">Provides support for queuing by leveraging [!INCLUDE[btsCoName](../includes/btsconame-md.md)] Message Queuing (MSMQ) as a transport and enables support for loosely coupled applications, failure isolation, load leveling, and disconnected operations.</span></span>  
  
-   <span data-ttu-id="60bf3-123">**Wcf-netnamedpipe 配接器**。</span><span class="sxs-lookup"><span data-stu-id="60bf3-123">**WCF-NetNamedPipe adapter**.</span></span> <span data-ttu-id="60bf3-124">針對機器上跨處理序通訊提供安全的最佳化。</span><span class="sxs-lookup"><span data-stu-id="60bf3-124">Provides secure optimization for on-machine cross-process communication.</span></span> <span data-ttu-id="60bf3-125">WCF-NetNamedPipe 配接器會針對傳輸安全性使用轉送安全性，針對訊息傳遞使用具名管線，並使用二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="60bf3-125">The WCF-NetNamedPipe adapter uses transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
-   <span data-ttu-id="60bf3-126">**Wcf-custom 配接器**。</span><span class="sxs-lookup"><span data-stu-id="60bf3-126">**WCF-Custom adapter**.</span></span> <span data-ttu-id="60bf3-127">啟用使用 WCF 擴充性功能。</span><span class="sxs-lookup"><span data-stu-id="60bf3-127">Enables the use of WCF extensibility features.</span></span> <span data-ttu-id="60bf3-128">這個配接器讓您能夠針對接收位置和傳送埠，選取及設定 WCF 繫結和行為資訊。</span><span class="sxs-lookup"><span data-stu-id="60bf3-128">The adapter allows you to select and configure a WCF binding and the behavior information for the receive location and send port.</span></span>  
  
-   <span data-ttu-id="60bf3-129">**Wcf-customisolated 配接器**。</span><span class="sxs-lookup"><span data-stu-id="60bf3-129">**WCF-CustomIsolated adapter**.</span></span> <span data-ttu-id="60bf3-130">啟用透過 HTTP 傳輸使用 WCF 擴充性功能。</span><span class="sxs-lookup"><span data-stu-id="60bf3-130">Enables the use of WCF extensibility features over the HTTP transport.</span></span> <span data-ttu-id="60bf3-131">這個配接器讓您能夠針對在外掛式主控件中執行的接收位置，選取和設定 WCF 繫結和行為資訊。</span><span class="sxs-lookup"><span data-stu-id="60bf3-131">The adapter allows you to select and configure a WCF binding and the behavior information for the receive location running in an isolated host.</span></span>  
  
 <span data-ttu-id="60bf3-132">此外，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 還提供「BizTalk WCF 服務發佈精靈」和「BizTalk WCF 服務使用精靈」。</span><span class="sxs-lookup"><span data-stu-id="60bf3-132">In addition, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides the BizTalk WCF Service Publishing Wizard and the BizTalk WCF Service Consuming Wizard.</span></span> <span data-ttu-id="60bf3-133">您可以使用 [BizTalk WCF 服務發佈精靈] 來建立 BizTalk 協調流程，並將其發佈成 WCF 服務，同時將結構描述發佈為 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="60bf3-133">You can use the BizTalk WCF Service Publishing Wizard to create and publish BizTalk orchestrations as WCF services, and to publish schemas as WCF services.</span></span> <span data-ttu-id="60bf3-134">您可以使用 [BizTalk WCF 服務使用精靈] 來產生 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 成品 (例如協調流程和型別)，以根據 WCF 服務的中繼資料文件來使用 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="60bf3-134">You can use the BizTalk WCF Service Consuming Wizard to generate [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] artifacts, such as orchestrations and types, to consume a WCF service based on the metadata document of the WCF service.</span></span>  
  
 <span data-ttu-id="60bf3-135">本節提供可協助您設定和部署 WCF 配接器的資源。</span><span class="sxs-lookup"><span data-stu-id="60bf3-135">This section provides resources to help you configure and deploy the WCF adapters.</span></span>  
  
## <a name="next"></a><span data-ttu-id="60bf3-136">下一個</span><span class="sxs-lookup"><span data-stu-id="60bf3-136">Next</span></span> 
  
-   [<span data-ttu-id="60bf3-137">WCF 配接器有哪些？</span><span class="sxs-lookup"><span data-stu-id="60bf3-137">What Are the WCF Adapters?</span></span>](../core/what-are-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="60bf3-138">設定 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-138">Configuring the WCF Adapters</span></span>](../core/configuring-the-wcf-adapters.md)  
  
-   [<span data-ttu-id="60bf3-139">WCF-BasicHttp 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-139">WCF-BasicHttp Adapter</span></span>](../core/wcf-basichttp-adapter.md)  
  
-   [<span data-ttu-id="60bf3-140">Wcf-wshttp 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-140">WCF-WSHttp Adapter</span></span>](../core/wcf-wshttp-adapter.md)  
  
-   [<span data-ttu-id="60bf3-141">Wcf-nettcp 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-141">WCF-NetTcp Adapter</span></span>](../core/wcf-nettcp-adapter.md)  
  
-   [<span data-ttu-id="60bf3-142">Wcf-netmsmq 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-142">WCF-NetMsmq Adapter</span></span>](../core/wcf-netmsmq-adapter.md)  
  
-   [<span data-ttu-id="60bf3-143">Wcf-netnamedpipe 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-143">WCF-NetNamedPipe Adapter</span></span>](../core/wcf-netnamedpipe-adapter.md)  
  
-   [<span data-ttu-id="60bf3-144">Wcf-custom 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-144">WCF-Custom Adapter</span></span>](../core/wcf-custom-adapter.md)  
  
-   [<span data-ttu-id="60bf3-145">Wcf-customisolated 配接器</span><span class="sxs-lookup"><span data-stu-id="60bf3-145">WCF-CustomIsolated Adapter</span></span>](../core/wcf-customisolated-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="60bf3-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60bf3-146">See Also</span></span>  
 [<span data-ttu-id="60bf3-147">使用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="60bf3-147">Using WCF Services</span></span>](../core/using-wcf-services.md)   