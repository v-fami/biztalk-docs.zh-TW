---
title: 範例架構的小型&amp;中型公司 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
ms.assetid: fc8c2fdd-bcb1-481c-b351-03092dd48540
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fa7911b7b2da942d559f2c85ad32e896c79d174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269550"
---
# <a name="sample-architectures-for-small-amp-medium-sized-companies"></a><span data-ttu-id="23d99-102">範例架構的小型&amp;中型公司</span><span class="sxs-lookup"><span data-stu-id="23d99-102">Sample Architectures for Small &amp; Medium-Sized Companies</span></span>
<span data-ttu-id="23d99-103">本節提供您要協助保護小型或中型公司資產安全時部署 Microsoft BizTalk Server 的範例架構。</span><span class="sxs-lookup"><span data-stu-id="23d99-103">This section provides a sample architecture to deploy Microsoft BizTalk Server when you want to help to protect the assets in a small or medium-sized company.</span></span> <span data-ttu-id="23d99-104">雖然這些架構鼓勵使用深層防禦與服務分隔使攻擊的影響降至最低，但它們假設的硬體、軟體與人力資源的數量是大型公司一般才有的數量。</span><span class="sxs-lookup"><span data-stu-id="23d99-104">While these architectures encourage defense in depth and separation of services to minimize the impact of an attack, they assume quantities of hardware, software, and human resources that are generally available to large companies.</span></span>  
  
 <span data-ttu-id="23d99-105">不過，小型與中型公司 (或擁有小型 BizTalk Server 部署的大型公司) 應該也關心如何保護其環境。</span><span class="sxs-lookup"><span data-stu-id="23d99-105">However, small and medium-sized companies (or large companies with small BizTalk Server deployments) should also be concerned with how to protect their environments.</span></span> <span data-ttu-id="23d99-106">在查看過公司如何部署或規劃部署其 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 方案之後，我們衍生出中小型公司的範例架構，以便平衡可用資源與可能的最大安全性。</span><span class="sxs-lookup"><span data-stu-id="23d99-106">After we looked at how companies deployed or plan to deploy their [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions, we derived a sample architecture for small and medium-sized companies that balances available resources with the greatest possible security.</span></span> <span data-ttu-id="23d99-107">您應該使用本節中的資訊，協助規劃您自己的部署。</span><span class="sxs-lookup"><span data-stu-id="23d99-107">You should use the information in this section to help you plan your own deployment.</span></span> <span data-ttu-id="23d99-108">評估您的商務需求與資產之後，您可能決定對 BizTalk Server 部署使用不同的架構。</span><span class="sxs-lookup"><span data-stu-id="23d99-108">After you evaluate your business needs and assets you might decide on a different architecture for your BizTalk Server deployment.</span></span>  
  
 <span data-ttu-id="23d99-109">為了易於查看架構的外觀，本節根據您可能在環境中使用的各種配接器提供範例架構。</span><span class="sxs-lookup"><span data-stu-id="23d99-109">To make it easier to see how your architecture would look, this section provides sample architectures based on various adapters that you might use in your environment.</span></span> <span data-ttu-id="23d99-110">這些圖會顯示哪些拓樸元件與配接器無關，以及哪些元件與您在 BizTalk Server 環境中使用的配接器有關。</span><span class="sxs-lookup"><span data-stu-id="23d99-110">The figures show you which components of the topology are adapter-independent, and which components depend on the adapter you use in your BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="23d99-111">我們也會根據您可搭配 BizTalk Server 使用的一些配接器來檢查使用實例。</span><span class="sxs-lookup"><span data-stu-id="23d99-111">We also examine usage scenarios based on some of the adapters you can use with BizTalk Server.</span></span> <span data-ttu-id="23d99-112">為了協助您規劃和設計自己的架構，我們提供此範例架構的威脅模型分析。</span><span class="sxs-lookup"><span data-stu-id="23d99-112">To help you as you plan and design your own architecture, we provide a threat model analysis of this sample architecture.</span></span> <span data-ttu-id="23d99-113">此分析視您用來與夥伴通訊的配接器而定，提供您對可能影響公司的潛在安全性問題更深入的觀察。</span><span class="sxs-lookup"><span data-stu-id="23d99-113">This analysis gives you a deeper look at the potential security issues that might affect your company, depending on the adapters you use to communicate with your partners.</span></span>  
  
 <span data-ttu-id="23d99-114">雖然本節提供協助您設計 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安全部署的資訊，但若要增加環境的安全性，您還要考慮在環境中保護各伺服器之間的通訊安全。</span><span class="sxs-lookup"><span data-stu-id="23d99-114">While this section gives you information to help you design a secure deployment of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], to increase the security in your environment you should also consider securing the communication between the servers in the environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="23d99-115">本節假設您不使用「商務活動監控」(BAM)。</span><span class="sxs-lookup"><span data-stu-id="23d99-115">This section assumes that you are not using Business Activity Monitoring (BAM).</span></span> <span data-ttu-id="23d99-116">此功能需要額外考量安全性。</span><span class="sxs-lookup"><span data-stu-id="23d99-116">This feature requires additional security considerations.</span></span> <span data-ttu-id="23d99-117">討論這[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。</span><span class="sxs-lookup"><span data-stu-id="23d99-117">This is discussed in [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23d99-118">如需配接器不在本文件中描述的詳細資訊，請參閱 BizTalk Server 開發人員中心 ([http://go.microsoft.com/fwlink/?LinkId=46420](http://go.microsoft.com/fwlink/?LinkId=46420)。)</span><span class="sxs-lookup"><span data-stu-id="23d99-118">For more information about adapters not described in this document, see the BizTalk Server Developer Center ([http://go.microsoft.com/fwlink/?LinkId=46420](http://go.microsoft.com/fwlink/?LinkId=46420).)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23d99-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="23d99-119">In This Section</span></span>  
  
-   [<span data-ttu-id="23d99-120">範例架構： 基本 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="23d99-120">Sample Architecture: Base BizTalk Server</span></span>](../core/sample-architecture-base-biztalk-server.md)  
  
-   [<span data-ttu-id="23d99-121">範例架構： HTTP 和 SOAP 配接器</span><span class="sxs-lookup"><span data-stu-id="23d99-121">Sample Architecture: HTTP and SOAP Adapters</span></span>](../core/sample-architecture-http-and-soap-adapters.md)  
  
-   [<span data-ttu-id="23d99-122">範例架構： BizTalk 訊息佇列</span><span class="sxs-lookup"><span data-stu-id="23d99-122">Sample Architecture: BizTalk Message Queuing</span></span>](../core/sample-architecture-biztalk-message-queuing.md)  
  
-   [<span data-ttu-id="23d99-123">範例架構： FTP 配接器</span><span class="sxs-lookup"><span data-stu-id="23d99-123">Sample Architecture: FTP Adapter</span></span>](../core/sample-architecture-ftp-adapter.md)  
  
-   [<span data-ttu-id="23d99-124">範例架構： File 配接器</span><span class="sxs-lookup"><span data-stu-id="23d99-124">Sample Architecture: File Adapter</span></span>](../core/sample-architecture-file-adapter.md)