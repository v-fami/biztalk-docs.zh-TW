---
title: 範例架構： File 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, security
- architecture, examples
- File adapters, security
- security, examples
- security, architecture
- examples, architecture
- architecture, security
- File adapters, architecture examples
ms.assetid: fdcbba0c-e301-46ce-8940-d617232cafbd
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11884786f743ece21a8009ea339a251b107420c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269606"
---
# <a name="sample-architecture-file-adapter"></a><span data-ttu-id="85f4a-102">範例架構： File 配接器</span><span class="sxs-lookup"><span data-stu-id="85f4a-102">Sample Architecture: File Adapter</span></span>
<span data-ttu-id="85f4a-103">當您使用 File 配接器傳送和接收訊息時，本主題描述的範例架構。</span><span class="sxs-lookup"><span data-stu-id="85f4a-103">This topic describes the sample architecture when you use the File adapter to send and receive messages.</span></span>  
  
## <a name="file-adapter-components"></a><span data-ttu-id="85f4a-104">FILE 配接器元件</span><span class="sxs-lookup"><span data-stu-id="85f4a-104">File Adapter Components</span></span>  
 <span data-ttu-id="85f4a-105">下圖顯示使用 FILE 配接器時 BizTalk Server 範例架構的元件。</span><span class="sxs-lookup"><span data-stu-id="85f4a-105">The following figure shows the components of the BizTalk Server sample architecture when you use the File adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85f4a-106">此範例架構也適用於使用 EDI 配接器時。</span><span class="sxs-lookup"><span data-stu-id="85f4a-106">This sample architecture is also applicable when you use the EDI adapter.</span></span>  
  
 <span data-ttu-id="85f4a-107">**圖 1 顯示 File 配接器的範例架構**</span><span class="sxs-lookup"><span data-stu-id="85f4a-107">**Figure 1 Sample architecture that shows File adapter**</span></span>  
  
 <span data-ttu-id="85f4a-108">![範例檔案配接器的架構](../core/media/tdi-sec-refarch-file.gif "TDI_Sec_RefArch_File")</span><span class="sxs-lookup"><span data-stu-id="85f4a-108">![Sample architecture for File adapter](../core/media/tdi-sec-refarch-file.gif "TDI_Sec_RefArch_File")</span></span>  
  
 <span data-ttu-id="85f4a-109">此範例架構包含以下各節所討論的元件。</span><span class="sxs-lookup"><span data-stu-id="85f4a-109">This sample architecture contains the components discussed in the following sections.</span></span>  
  
## <a name="perimeter-network-internet"></a><span data-ttu-id="85f4a-110">周邊網路-網際網路</span><span class="sxs-lookup"><span data-stu-id="85f4a-110">Perimeter network-Internet</span></span>  
 <span data-ttu-id="85f4a-111">公司通常會使用 File 通訊協定來進行內部網路通訊，因此網際網路周邊網路中不需要任何伺服器來支援此實例。</span><span class="sxs-lookup"><span data-stu-id="85f4a-111">Companies commonly use the File protocol for intranet-based communications, and therefore you do not need any servers in the Internet perimeter network to support this scenario.</span></span>  
  
## <a name="perimeter-network-intranet"></a><span data-ttu-id="85f4a-112">周邊網路-內部網路</span><span class="sxs-lookup"><span data-stu-id="85f4a-112">Perimeter network-intranet</span></span>  
 <span data-ttu-id="85f4a-113">當您使用 FILE 配接器時，內部網路周邊網路中會有一部檔案伺服器。</span><span class="sxs-lookup"><span data-stu-id="85f4a-113">When you use the File adapter, there is a File server in the intranet perimeter network.</span></span> <span data-ttu-id="85f4a-114">這是您的夥伴放置其訊息的伺服器，而且 BizTalk FILE 接收配接器由此伺服器拾取訊息。</span><span class="sxs-lookup"><span data-stu-id="85f4a-114">This is the server where your partners drop their messages, and the BizTalk File receive adapter picks up messages from this server.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="85f4a-115">電子商務網域</span><span class="sxs-lookup"><span data-stu-id="85f4a-115">E-Business domain</span></span>  
 <span data-ttu-id="85f4a-116">此網域中的伺服器包括：</span><span class="sxs-lookup"><span data-stu-id="85f4a-116">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="85f4a-117">**BizTalk Server （處理、 File 配接器，以及追蹤主控件）。**</span><span class="sxs-lookup"><span data-stu-id="85f4a-117">**BizTalk Server (processing, File adapter, and tracking hosts).**</span></span> <span data-ttu-id="85f4a-118">此伺服器有 BizTalk Server 執行階段安裝，而且擁有主控件執行個體，其中包含 BizTalk 協調流程、管線、商務規則引擎以及其他商務程序。</span><span class="sxs-lookup"><span data-stu-id="85f4a-118">This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes.</span></span> <span data-ttu-id="85f4a-119">這是 BizTalk Server 連接埠、接收位置、管線、對應、結構描述以及組件的位置，用來接收、傳遞、處理和傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="85f4a-119">This is where the BizTalk Server ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route, process, and send messages.</span></span> <span data-ttu-id="85f4a-120">此伺服器還有可支援追蹤狀況監控與商務監控資料之主控件的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="85f4a-120">This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.</span></span> <span data-ttu-id="85f4a-121">此外，此主控件還包含執行 FILE 傳送與接收配接器的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="85f4a-121">Additionally, this host contains instances of the host that runs the File send and receive adapters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85f4a-122">當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="85f4a-122">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span> <span data-ttu-id="85f4a-123">如需如何設定 BizTalk Server 高可用性的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。</span><span class="sxs-lookup"><span data-stu-id="85f4a-123">For more information about how to configure BizTalk Server for high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
-   <span data-ttu-id="85f4a-124">**主要密碼伺服器。**</span><span class="sxs-lookup"><span data-stu-id="85f4a-124">**Master secret server.**</span></span> <span data-ttu-id="85f4a-125">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="85f4a-125">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="85f4a-126">**SQL Server。**</span><span class="sxs-lookup"><span data-stu-id="85f4a-126">**SQL Server.**</span></span> <span data-ttu-id="85f4a-127">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="85f4a-127">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="85f4a-128">**網域控制站。**</span><span class="sxs-lookup"><span data-stu-id="85f4a-128">**Domain controller.**</span></span> <span data-ttu-id="85f4a-129">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="85f4a-129">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="85f4a-130">**系統管理工具。**</span><span class="sxs-lookup"><span data-stu-id="85f4a-130">**Administration tools.**</span></span> <span data-ttu-id="85f4a-131">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="85f4a-131">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f4a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85f4a-132">See Also</span></span>  
 <span data-ttu-id="85f4a-133">[小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="85f4a-133">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="85f4a-134">威脅模型分析的範例案例</span><span class="sxs-lookup"><span data-stu-id="85f4a-134">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)