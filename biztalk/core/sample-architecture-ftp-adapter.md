---
title: 範例架構： FTP 配接器 |Microsoft 文件
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
- independent software vendor (ISV)
- security, examples
- security, architecture
- examples, architecture
- architecture, security
- FTP adapters, security
- FTP adapters, architecture examples
ms.assetid: 13fc1086-6acc-483c-be83-4ff6a60cd2bc
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bed15e06027bec5e73c19cf73548674bc51ce68a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269846"
---
# <a name="sample-architecture-ftp-adapter"></a><span data-ttu-id="5440f-102">範例架構： FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="5440f-102">Sample Architecture: FTP Adapter</span></span>
<span data-ttu-id="5440f-103">當您使用 FTP 配接器傳送和接收訊息時，本主題描述的範例架構。</span><span class="sxs-lookup"><span data-stu-id="5440f-103">This topic describes the sample architecture when you use the FTP adapter to send and receive messages.</span></span>  
  
 <span data-ttu-id="5440f-104">下圖顯示使用 FTP 配接器時 BizTalk Server 範例架構的元件。</span><span class="sxs-lookup"><span data-stu-id="5440f-104">The following figure shows the components of the BizTalk Server sample architecture when you use the FTP adapter.</span></span>  
  
 <span data-ttu-id="5440f-105">**圖 1 顯示 FTP 配接器的範例架構**</span><span class="sxs-lookup"><span data-stu-id="5440f-105">**Figure 1 Sample architecture that shows FTP adapter**</span></span>  
  
 <span data-ttu-id="5440f-106">![範例架構的 FTP 配接器](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")</span><span class="sxs-lookup"><span data-stu-id="5440f-106">![Sample architecture for FTP adapter](../core/media/tdi-sec-refarch-ftp.gif "TDI_Sec_RefArch_FTP")</span></span>  
  
 <span data-ttu-id="5440f-107">此範例架構包含下列章節所討論的元件。</span><span class="sxs-lookup"><span data-stu-id="5440f-107">This sample architecture contains the components as discussed in following sections.</span></span>  
  
## <a name="perimeter-networkinternet"></a><span data-ttu-id="5440f-108">周邊網路─網際網路</span><span class="sxs-lookup"><span data-stu-id="5440f-108">Perimeter network―Internet</span></span>  
 <span data-ttu-id="5440f-109">當您使用 FTP 配接器時，網際網路周邊網路中有一個 FTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5440f-109">When you use the FTP adapter, there is an FTP server in the Internet perimeter network.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5440f-110">FTP 伺服器也可以位於環境外部-在協力電腦的網路中，或第三方獨立軟體廠商 (ISV) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="5440f-110">The FTP server can also be located outside your environment—in the partner's network, or hosted by a third-party independent software vendor (ISV).</span></span>  
  
## <a name="perimeter-networkintranet"></a><span data-ttu-id="5440f-111">周邊網路─內部網路</span><span class="sxs-lookup"><span data-stu-id="5440f-111">Perimeter network―intranet</span></span>  
 <span data-ttu-id="5440f-112">公司通常使用 FTP 通訊協定來進行網際網路通訊，因此內部網路周邊網路中不需要任何伺服器來支援此實例。</span><span class="sxs-lookup"><span data-stu-id="5440f-112">Companies commonly use the FTP protocol for Internet-based communications, and therefore you do not need any servers in the intranet perimeter network to support this scenario.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="5440f-113">電子商務網域</span><span class="sxs-lookup"><span data-stu-id="5440f-113">E-Business domain</span></span>  
 <span data-ttu-id="5440f-114">此網域中的伺服器包括：</span><span class="sxs-lookup"><span data-stu-id="5440f-114">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="5440f-115">**BizTalk Server （處理、 FTP 配接器，以及追蹤主控件）。**</span><span class="sxs-lookup"><span data-stu-id="5440f-115">**BizTalk Server (processing, FTP adapter, and tracking hosts).**</span></span> <span data-ttu-id="5440f-116">此伺服器有 BizTalk Server 執行階段安裝，而且擁有主控件執行個體，其中包含 BizTalk 協調流程、管線、商務規則引擎以及其他商務程序。</span><span class="sxs-lookup"><span data-stu-id="5440f-116">This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes.</span></span> <span data-ttu-id="5440f-117">這是 BizTalk Server 連接埠、接收位置、管線、對應、結構描述以及組件的位置，用來接收、傳遞、處理和傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="5440f-117">This is where the BizTalk Server ports, receive locations, pipelines, maps, schemas, and assemblies are located to receive, route, process, and send messages.</span></span> <span data-ttu-id="5440f-118">此伺服器還有可支援追蹤狀況監控與商務監控資料之主控件的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="5440f-118">This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.</span></span> <span data-ttu-id="5440f-119">此外，此主控件還包含執行 FTP 傳送與接收配接器的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="5440f-119">Additionally, this host contains instances of the host that runs the FTP send and receive adapters.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5440f-120">當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="5440f-120">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span> <span data-ttu-id="5440f-121">如需如何設定 BizTalk Server 高可用性的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。</span><span class="sxs-lookup"><span data-stu-id="5440f-121">For more information about how to configure BizTalk Server for high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
-   <span data-ttu-id="5440f-122">**主要密碼伺服器。**</span><span class="sxs-lookup"><span data-stu-id="5440f-122">**Master secret server.**</span></span> <span data-ttu-id="5440f-123">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5440f-123">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="5440f-124">**SQL Server。**</span><span class="sxs-lookup"><span data-stu-id="5440f-124">**SQL Server.**</span></span> <span data-ttu-id="5440f-125">與相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5440f-125">Same as the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="5440f-126">**網域控制站。**</span><span class="sxs-lookup"><span data-stu-id="5440f-126">**Domain controller.**</span></span> <span data-ttu-id="5440f-127">與中的相同相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5440f-127">Same as in the Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="5440f-128">**系統管理工具。**</span><span class="sxs-lookup"><span data-stu-id="5440f-128">**Administration tools.**</span></span> <span data-ttu-id="5440f-129">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5440f-129">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5440f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5440f-130">See Also</span></span>  
 <span data-ttu-id="5440f-131">[小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="5440f-131">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="5440f-132">威脅模型分析的範例案例</span><span class="sxs-lookup"><span data-stu-id="5440f-132">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)