---
title: "安裝服務導向解決方案之前 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service solution tutorial, deployment prerequisites
ms.assetid: 865bd21c-e49a-4647-af91-fefee07ee806
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7e611996e58291cdf6ed5d6b38b2b2fe5c299d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="before-installing-the-service-oriented-solution"></a><span data-ttu-id="4ea6e-102">安裝服務導向解決方案之前</span><span class="sxs-lookup"><span data-stu-id="4ea6e-102">Before Installing the Service Oriented Solution</span></span>
<span data-ttu-id="4ea6e-103">必須具備下列必要條件才能在單一電腦上安裝服務導向解決方案的虛設常式版本：</span><span class="sxs-lookup"><span data-stu-id="4ea6e-103">The following prerequisites must be available to install the stub version of the service-oriented solution on a single computer:</span></span>  
  
-   [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)]<span data-ttu-id="4ea6e-104">。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-104">.</span></span>  
  
-   <span data-ttu-id="4ea6e-105">[!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)] 支援的軟體。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-105">Supported software for [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].</span></span>  
  
-   <span data-ttu-id="4ea6e-106">最新版本的 IBM WebSphere MQ Client for Windows</span><span class="sxs-lookup"><span data-stu-id="4ea6e-106">The latest version of IBM WebSphere MQ Client for Windows</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ea6e-107">MQSeries Server 不是解決方案的虛設常式版本之必要項目。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-107">MQSeries Server is not required for the stub version of the solution.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ea6e-108">您可以從 IBM 網站下載 IBM WebSphere MQ Client for Windows。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-108">You can download IBM WebSphere MQ Client for Windows from the IBM Web site.</span></span>  
  
 <span data-ttu-id="4ea6e-109">在單一電腦上安裝服務導向解決方案的內嵌與配接器版本：</span><span class="sxs-lookup"><span data-stu-id="4ea6e-109">For installing the inline and adapter version of the service oriented solution on a single computer:</span></span>  
  
-   [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)]<span data-ttu-id="4ea6e-110">。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-110">.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ea6e-111">必須要有網域帳戶以對應「企業單一登入」(SSO) 認證。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-111">A domain account is required to map credentials for Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="4ea6e-112">建議在 BizTalk 服務和 ENTSSO 服務帳戶使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-112">We recommend using domain accounts for the BizTalk service and for the ENTSSO service accounts.</span></span>  
  
-   <span data-ttu-id="4ea6e-113">[!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)] 支援的軟體。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-113">Supported software for [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].</span></span>  
  
-   <span data-ttu-id="4ea6e-114">本機電腦上的 MQSeries Server，或存取執行 MQSeries Server 的電腦。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-114">MQSeries Server on the local computer or access to the computer running the MQSeries Server.</span></span> <span data-ttu-id="4ea6e-115">在內嵌版本中，MQSeries 用戶端 API 必須可以在執行解決方案之協調流程的 BizTalk Server 上使用。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-115">For the inline version, MQSeries client APIs must be available on the BizTalk server running the solution’s orchestrations.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ea6e-116">MQSeries Server 的版本必須與 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] MQSeries 配接器所需的版本相符。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-116">The version of MQSeries Server must match the version required by the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] MQSeries Adapter.</span></span> <span data-ttu-id="4ea6e-117">這可以包括 IBM WebSphere MQ for Windows Version 5.3 搭配 Fix Pack 10 (CSD10) 或更新的版本。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-117">This can include IBM WebSphere MQ for Windows Version 5.3 with Fix Pack 10 (CSD10) or later.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ea6e-118">當使用 MQSeries 這類會對伺服器進行「分散式元件物件模型」(Distributed Component Object Model，DCOM) 呼叫的功能時，請確定您並未啟用「網路位址轉譯」(Network Address Translation，NAT) 架構的防火牆。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-118">When using features such as MQSeries which make Distributed Component Object Model (DCOM) calls to the server, make sure you do not have a Network Address Translation (NAT)-based firewall enabled.</span></span> <span data-ttu-id="4ea6e-119">用戶端必須能以伺服器的實際 IP 位址來存取伺服器，而 NAT 架構的防火牆會將此位址轉譯為用戶端無法辨識的位址。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-119">The client must be able to access the server by its actual IP address, and NAT-based firewalls translate this address to something the client will not recognize.</span></span>  
  
-   <span data-ttu-id="4ea6e-120">若您使用需要大型主機的其他解決方案，則需要 IBM Mainframe 搭配 CICS 與 Transaction X。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-120">IBM Mainframe with CICS and Transaction X if you are using a variation of the solution that requires a mainframe.</span></span> <span data-ttu-id="4ea6e-121">在這種情況下，必須在大型主機和 Microsoft Host Integration Server (HIS) 上安裝 CICS 應用程式 (COBOL 程式碼) 才能存取大型主機。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-121">In this case, the CICS application (COBOL code) must be installed on the mainframe and Microsoft Host Integration Server (HIS) is required to access the mainframe.</span></span>  
  
     <span data-ttu-id="4ea6e-122">若您的解決方案沒有大型主機，可以修改連接埠繫結以使用虛設常式 Web 服務來進行擱置交易。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-122">If you don’t have a mainframe for the solution, you can modify the port binding to use the stub Web service for Pending Transactions.</span></span> <span data-ttu-id="4ea6e-123">Web 服務會在本機產生交易，以模擬大型主機交易。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-123">The Web service generates transactions locally to emulate the mainframe transactions.</span></span> <span data-ttu-id="4ea6e-124">如需如何修改虛設常式擱置交易 Web 服務的連接埠繫結的詳細資訊，請參閱[如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-124">For more information about how to modify the port binding for the stub Pending Transactions Web service, see [How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md).</span></span>  
  
-   <span data-ttu-id="4ea6e-125">連接大型主機必須要有 Host Integration Server。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-125">Host Integration Server is required to connect to the mainframe.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ea6e-126">Host Integration Server 是包含在[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-126">Host Integration Server is included as part of [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
-   <span data-ttu-id="4ea6e-127">以 HTTPS 連線憑證設定的 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="4ea6e-127">Web server configured with a certificate for HTTPS connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea6e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ea6e-128">See Also</span></span>  
 <span data-ttu-id="4ea6e-129">[How to Install 虛設常式版本的服務導向解決方案](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="4ea6e-129">[How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="4ea6e-130">[如何安裝內嵌和配接器版本的服務導向解決方案](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="4ea6e-130">[How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="4ea6e-131">[如何執行服務導向解決方案](../core/how-to-run-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="4ea6e-131">[How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="4ea6e-132">開發人員電腦設定為服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="4ea6e-132">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)