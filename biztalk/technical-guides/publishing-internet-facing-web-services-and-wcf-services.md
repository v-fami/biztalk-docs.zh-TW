---
title: 網際網路對向 Web 服務和 WCF 服務發佈 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7553608-f57a-470e-91d4-75504b3fd52b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32a0478e43f87dfbf29f736fde062c67fb4a94cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009199"
---
# <a name="publishing-internet-facing-web-services-and-wcf-services"></a><span data-ttu-id="13c59-102">發佈網際網路對向 Web 服務和 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="13c59-102">Publishing Internet-facing Web Services and WCF Services</span></span>
<span data-ttu-id="13c59-103">您可以使用多個方法發佈[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和網際網路的 WCF 服務：</span><span class="sxs-lookup"><span data-stu-id="13c59-103">You can use multiple approaches for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services to the Internet:</span></span>  
  
- <span data-ttu-id="13c59-104">周邊網路 （也也稱為 DMZ 和遮蔽式子網路） 中使用反向 proxy 規則。</span><span class="sxs-lookup"><span data-stu-id="13c59-104">Use reverse proxy rules in a perimeter network (also known as DMZ, demilitarized zone, and screened subnet).</span></span>  
  
- <span data-ttu-id="13c59-105">將執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將 Web 服務或 WCF 服務發佈至周邊網路的網域。</span><span class="sxs-lookup"><span data-stu-id="13c59-105">Put the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that publish the Web services or WCF services into the perimeter network domain.</span></span>  
  
- <span data-ttu-id="13c59-106">使用 BizTalk Server 的雲端啟用程式功能，將 Web 服務或 WCF 服務發佈為 Azure AppFabric 服務匯流排轉送端點。</span><span class="sxs-lookup"><span data-stu-id="13c59-106">Use BizTalk Server cloud enabler functionality to publish the Web services or WCF services as an Azure AppFabric Service Bus relay endpoint.</span></span>  
  
## <a name="using-a-reverse-proxy"></a><span data-ttu-id="13c59-107">使用反向 Proxy</span><span class="sxs-lookup"><span data-stu-id="13c59-107">Using a Reverse Proxy</span></span>  
 <span data-ttu-id="13c59-108">這已發行的傳統方法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="13c59-108">This has been the traditional approach for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services.</span></span> <span data-ttu-id="13c59-109">在周邊網路中使用反向 proxy 規則，而毋需已位於周邊網路中的 BizTalk server。</span><span class="sxs-lookup"><span data-stu-id="13c59-109">Using reverse proxy rules in the perimeter network obviates the need to have BizTalk servers located in the perimeter network.</span></span> <span data-ttu-id="13c59-110">反向 proxy 規則只是轉送 HTTP 與 SOAP 要求從周邊網路到執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內部網路網域中。</span><span class="sxs-lookup"><span data-stu-id="13c59-110">The reverse proxy rules simply forward the HTTP and SOAP requests from the perimeter network to the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the intranet domain.</span></span>  
  
 <span data-ttu-id="13c59-111">如需使用反向 proxy 的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="13c59-111">For more information about using a reverse proxy, see the following topics in BizTalk Server Help:</span></span>  
  
-   <span data-ttu-id="13c59-112">[「 架構的範例： HTTP 和 SOAP 配接器"](http://go.microsoft.com/fwlink/?LinkId=153339) (http://go.microsoft.com/fwlink/?LinkId=153339)。</span><span class="sxs-lookup"><span data-stu-id="13c59-112">["Sample Architecture: HTTP and SOAP Adapters"](http://go.microsoft.com/fwlink/?LinkId=153339) (http://go.microsoft.com/fwlink/?LinkId=153339).</span></span>  
  
-   <span data-ttu-id="13c59-113">[「 範例 TMA: HTTP 和 SOAP 配接器"](http://go.microsoft.com/fwlink/?LinkId=153340) (http://go.microsoft.com/fwlink/?LinkId=153340)。</span><span class="sxs-lookup"><span data-stu-id="13c59-113">["Sample TMA: HTTP and SOAP Adapters"](http://go.microsoft.com/fwlink/?LinkId=153340) (http://go.microsoft.com/fwlink/?LinkId=153340).</span></span>  
  
-   <span data-ttu-id="13c59-114">[「 大型分散式架構 」](http://go.microsoft.com/fwlink/?LinkId=153341) (http://go.microsoft.com/fwlink/?LinkId=153341)。</span><span class="sxs-lookup"><span data-stu-id="13c59-114">["Large Distributed Architecture"](http://go.microsoft.com/fwlink/?LinkId=153341) (http://go.microsoft.com/fwlink/?LinkId=153341).</span></span>  
  
## <a name="using-computers-running-biztalk-server-in-the-perimeter-network"></a><span data-ttu-id="13c59-115">使用周邊網路中執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="13c59-115">Using Computers Running BizTalk Server in the Perimeter Network</span></span>  
 <span data-ttu-id="13c59-116">這不是慣用的方法，供發行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務或 WCF 服務到網際網路，因為它需要執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]位於周邊網路中。</span><span class="sxs-lookup"><span data-stu-id="13c59-116">This is not the preferred approach for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services or WCF services to the Internet because it requires computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to be located in the perimeter network.</span></span> <span data-ttu-id="13c59-117">不過，無法使用周邊網路中的反向 proxy 時，您可以使用這種方法。</span><span class="sxs-lookup"><span data-stu-id="13c59-117">However, when a reverse proxy is not available in the perimeter network, you can use this approach.</span></span>  
  
 <span data-ttu-id="13c59-118">此方法需要周邊網路網域，在與內部網路網域的單向信任中登記 （但內部網路網域不信任周邊網路網域）。</span><span class="sxs-lookup"><span data-stu-id="13c59-118">This approach requires the perimeter network domain to enlist in a one-way trust with the intranet domain (but the intranet domain does not trust the perimeter network domain).</span></span> <span data-ttu-id="13c59-119">在 「 BizTalk 外掛式主控件使用者 」 網域群組的內部網路網域帳戶，則必須執行的 Web 服務或周邊網路網域中的 WCF 服務裝載集區的 IIS 應用程式。</span><span class="sxs-lookup"><span data-stu-id="13c59-119">The IIS application pools that host the Web services or WCF services in the perimeter network domain must be running under an intranet domain account that is in the "BizTalk Isolated Host Users" domain group.</span></span> <span data-ttu-id="13c59-120">這可讓應用程式集區 發佈訊息，以將必要權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="13c59-120">This gives the application pool the required rights to publish messages to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database.</span></span>  
  
 <span data-ttu-id="13c59-121">您必須在防火牆，以配合這一點，來開啟特定連接埠。</span><span class="sxs-lookup"><span data-stu-id="13c59-121">You must open specific ports in the firewall to accommodate this.</span></span> <span data-ttu-id="13c59-122">如需有關必要的連接埠的詳細資訊，請參閱[連接埠的接收和傳送伺服器 >](http://go.microsoft.com/fwlink/?LinkId=153342) (<http://go.microsoft.com/fwlink/?LinkId=153342>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="13c59-122">For more information about the required ports, see ["Ports for the Receive and Send Servers"](http://go.microsoft.com/fwlink/?LinkId=153342) (<http://go.microsoft.com/fwlink/?LinkId=153342>) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
## <a name="exposing-biztalk-applications-on-the-cloud-using-appfabric-connect-for-services"></a><span data-ttu-id="13c59-123">公開使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="13c59-123">Exposing BizTalk Applications on the Cloud using AppFabric Connect for Services</span></span>  
 <span data-ttu-id="13c59-124">請參閱文章[公開使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=204700)(http://go.microsoft.com/fwlink/?LinkID=204700)如需詳細資訊，請為在雲端上的 WCF 服務公開的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="13c59-124">See the article [Exposing BizTalk Applications on the Cloud using AppFabric Connect for Services](http://go.microsoft.com/fwlink/?LinkID=204700) (http://go.microsoft.com/fwlink/?LinkID=204700) for more information about expose BizTalk Applications as WCF Services on the cloud.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c59-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13c59-125">See Also</span></span>  
 [<span data-ttu-id="13c59-126">發佈 Web Services1 規劃</span><span class="sxs-lookup"><span data-stu-id="13c59-126">Planning for Publishing Web Services1</span></span>](../technical-guides/planning-for-publishing-web-services1.md)