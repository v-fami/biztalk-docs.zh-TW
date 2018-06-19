---
title: 範例架構： BizTalk 訊息佇列 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, security
- Message Queuing binary protocol
- architecture, examples
- security, examples
- security, architecture
- examples, architecture
- MSMQ adapters, security
- architecture, security
- MSMQ adapters, architecture examples
- servers, Windows Message Queuing
- Windows Message Queuing
- message queuing adapters
ms.assetid: a660c798-1c45-4759-a6c8-f11550683a31
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f38d373680fd1b47722fc1ac52c56b113ef59cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269790"
---
# <a name="sample-architecture-biztalk-message-queuing"></a><span data-ttu-id="bdbab-102">範例架構： BizTalk 訊息佇列</span><span class="sxs-lookup"><span data-stu-id="bdbab-102">Sample Architecture: BizTalk Message Queuing</span></span>
<span data-ttu-id="bdbab-103">當您使用 「 BizTalk 訊息佇列配接器傳送和接收訊息時，本主題描述的範例架構。</span><span class="sxs-lookup"><span data-stu-id="bdbab-103">This topic describes the sample architecture when you use the BizTalk Message Queuing adapter to send and receive messages.</span></span>  
  
 <span data-ttu-id="bdbab-104">下圖顯示使用 BizTalk 訊息佇列配接器時 BizTalk Server 範例架構的元件。</span><span class="sxs-lookup"><span data-stu-id="bdbab-104">The following figure shows the components of the BizTalk Server sample architecture when you use the BizTalk Message Queuing adapter.</span></span>  
  
 <span data-ttu-id="bdbab-105">**圖 1 顯示 BizTalk 訊息佇列配接器的範例架構**</span><span class="sxs-lookup"><span data-stu-id="bdbab-105">**Figure 1 Sample architecture that shows BizTalk Message Queuing adapter**</span></span>  
  
 <span data-ttu-id="bdbab-106">![BizTalk 訊息佇列的範例架構](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")</span><span class="sxs-lookup"><span data-stu-id="bdbab-106">![Sample architecture for BizTalk Message Queuing](../core/media/tdi-sec-refarch-msmq.gif "TDI_Sec_RefArch_MSMQ")</span></span>  
  
 <span data-ttu-id="bdbab-107">此範例架構包含下列章節所討論的元件。</span><span class="sxs-lookup"><span data-stu-id="bdbab-107">This sample architecture contains the components as discussed in the following sections.</span></span>  
  
## <a name="perimeter-networkinternet"></a><span data-ttu-id="bdbab-108">周邊網路─網際網路</span><span class="sxs-lookup"><span data-stu-id="bdbab-108">Perimeter network―Internet</span></span>  
 <span data-ttu-id="bdbab-109">我們不建議在網際網路上使用訊息佇列二進位通訊協定。</span><span class="sxs-lookup"><span data-stu-id="bdbab-109">We do not recommend using the Message Queuing binary protocol over the Internet.</span></span> <span data-ttu-id="bdbab-110">您不應該讓任何訊息佇列流量通過防火牆 1。</span><span class="sxs-lookup"><span data-stu-id="bdbab-110">You should not let any Message Queuing traffic through Firewall 1.</span></span> <span data-ttu-id="bdbab-111">如果您想要使用 BizTalk 訊息佇列配接器，透過網際網路接收訊息，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="bdbab-111">If you want to use the BizTalk Message Queuing adapter to receive messages over the Internet, do the following:</span></span>  
  
-   <span data-ttu-id="bdbab-112">在周邊網路中使用訊息佇列伺服器。</span><span class="sxs-lookup"><span data-stu-id="bdbab-112">Use a Message Queuing server in the perimeter network.</span></span>  
  
-   <span data-ttu-id="bdbab-113">透過網際網路使用訊息佇列 HTTP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="bdbab-113">Use the Message Queuing HTTP protocol over the Internet.</span></span>  
  
-   <span data-ttu-id="bdbab-114">周邊網路中有個轉送應用程式，它會拾取來自訊息佇列伺服器的訊息，然後使用二進位通訊協定轉送到 BizTalk 訊息佇列配接器。</span><span class="sxs-lookup"><span data-stu-id="bdbab-114">Have a forwarding application in the perimeter network that picks up the messages from the Message Queuing server and forwards them to the BizTalk Message Queuing adapter by using a binary protocol.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bdbab-115">即使您使用 BizTalk 訊息佇列從網際網路接收訊息，在防火牆 1 上仍必須讓 BizTalk 訊息佇列使用的連接埠保持關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="bdbab-115">Even if you use BizTalk Message Queuing to receive messages from the Internet, the ports that BizTalk Message Queuing uses should remain closed in Firewall 1.</span></span>  
  
## <a name="perimeter-networkintranet"></a><span data-ttu-id="bdbab-116">周邊網路─內部網路</span><span class="sxs-lookup"><span data-stu-id="bdbab-116">Perimeter network―intranet</span></span>  
 <span data-ttu-id="bdbab-117">當您使用 BizTalk 訊息佇列配接器從內部網路接收訊息時，有一個 Windows 訊息佇列伺服器會將訊息佇列流量轉送到 BizTalk Server，而此 BizTalk Server 是執行 BizTalk 訊息佇列配接器的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbab-117">When you use the BizTalk Message Queuing adapter to receive messages from the intranet, there is a Windows Message Queuing server that forwards the Message Queuing traffic to the BizTalk Server that runs a host instance of the BizTalk Message Queuing adapter.</span></span>  
  
 <span data-ttu-id="bdbab-118">若內部網路與電子商務網域共用一般的 Active Directory，訊息會通過一系列的訊息佇列路由器，直到它抵達正確的目的地 (執行 BizTalk 訊息佇列接收配接器的主控件執行個體的 BizTalk Server)。</span><span class="sxs-lookup"><span data-stu-id="bdbab-118">If the intranet and the E-Business domain share a common Active Directory, a message goes through a series of Message Queuing routers until it reaches the right destination (the BizTalk Server that runs a host instance of the BizTalk Message Queuing receive adapter).</span></span> <span data-ttu-id="bdbab-119">這個選項未顯示在圖中，因為它沒有第一個選項安全。</span><span class="sxs-lookup"><span data-stu-id="bdbab-119">This option is not represented in the diagram because it is less secure than the first one.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="bdbab-120">電子商務網域</span><span class="sxs-lookup"><span data-stu-id="bdbab-120">E-Business domain</span></span>  
 <span data-ttu-id="bdbab-121">此網域中的伺服器包括：</span><span class="sxs-lookup"><span data-stu-id="bdbab-121">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="bdbab-122">**BizTalk Server （處理、 BizTalk 訊息佇列配接器以及追蹤主控件）。**</span><span class="sxs-lookup"><span data-stu-id="bdbab-122">**BizTalk Server (processing, BizTalk Message Queuing adapter, and Tracking hosts).**</span></span> <span data-ttu-id="bdbab-123">此伺服器有 BizTalk Server 執行階段安裝，而且擁有主控件執行個體，其中包含 BizTalk 協調流程、管線、商務規則引擎以及其他商務程序。</span><span class="sxs-lookup"><span data-stu-id="bdbab-123">This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes.</span></span> <span data-ttu-id="bdbab-124">這是 BizTalk Server 連接埠、接收位置、管線、對應、結構描述以及組件的位置，用來接收、傳遞、處理和傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="bdbab-124">This is where the BizTalk Server ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route, process, and send messages.</span></span> <span data-ttu-id="bdbab-125">此伺服器還有可支援追蹤狀況監控與商務監控資料之主控件的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbab-125">This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.</span></span> <span data-ttu-id="bdbab-126">此外，此主控件還包含執行 BizTalk 訊息佇列傳送與接收配接器的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="bdbab-126">Additionally, this host contains instances of the host that runs the BizTalk Message Queuing send and receive adapters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bdbab-127">當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="bdbab-127">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span>  
  
-   <span data-ttu-id="bdbab-128">**主要密碼伺服器。**</span><span class="sxs-lookup"><span data-stu-id="bdbab-128">**Master secret server.**</span></span> <span data-ttu-id="bdbab-129">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbab-129">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="bdbab-130">**SQL Server。**</span><span class="sxs-lookup"><span data-stu-id="bdbab-130">**SQL Server.**</span></span> <span data-ttu-id="bdbab-131">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbab-131">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="bdbab-132">**網域控制站。**</span><span class="sxs-lookup"><span data-stu-id="bdbab-132">**Domain controller.**</span></span> <span data-ttu-id="bdbab-133">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbab-133">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="bdbab-134">**系統管理工具。**</span><span class="sxs-lookup"><span data-stu-id="bdbab-134">**Administration tools.**</span></span> <span data-ttu-id="bdbab-135">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbab-135">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdbab-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdbab-136">See Also</span></span>  
 <span data-ttu-id="bdbab-137">[小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="bdbab-137">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="bdbab-138">威脅模型分析的範例案例</span><span class="sxs-lookup"><span data-stu-id="bdbab-138">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)