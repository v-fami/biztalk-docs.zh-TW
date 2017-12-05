---
title: "網際網路對向 Web 服務和 WCF 服務發佈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7553608-f57a-470e-91d4-75504b3fd52b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e466c4fc2a5f83f5a8445601235b53f44404a912
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="publishing-internet-facing-web-services-and-wcf-services"></a><span data-ttu-id="6b210-102">發行的網際網路對向 Web 服務和 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="6b210-102">Publishing Internet-facing Web Services and WCF Services</span></span>
<span data-ttu-id="6b210-103">您可以使用多種發行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和到網際網路的 WCF 服務：</span><span class="sxs-lookup"><span data-stu-id="6b210-103">You can use multiple approaches for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services to the Internet:</span></span>  
  
-   <span data-ttu-id="6b210-104">周邊網路 （也稱為 DMZ、 非軍事區域和遮蔽式子網路） 中使用反向 proxy 規則。</span><span class="sxs-lookup"><span data-stu-id="6b210-104">Use reverse proxy rules in a perimeter network (also known as DMZ, demilitarized zone, and screened subnet).</span></span>  
  
-   <span data-ttu-id="6b210-105">將執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將 Web 服務或 WCF 服務發佈至周邊網路的網域。</span><span class="sxs-lookup"><span data-stu-id="6b210-105">Put the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that publish the Web services or WCF services into the perimeter network domain.</span></span>  
  
-   <span data-ttu-id="6b210-106">使用 BizTalk Server 雲端推手功能來發佈 Web 服務或 WCF 服務，為 Azure AppFabric 服務匯流排轉送端點。</span><span class="sxs-lookup"><span data-stu-id="6b210-106">Use BizTalk Server cloud enabler functionality to publish the Web services or WCF services as an Azure AppFabric Service Bus relay endpoint.</span></span>  
  
## <a name="using-a-reverse-proxy"></a><span data-ttu-id="6b210-107">使用反向 Proxy</span><span class="sxs-lookup"><span data-stu-id="6b210-107">Using a Reverse Proxy</span></span>  
 <span data-ttu-id="6b210-108">這是已發行的傳統方法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="6b210-108">This has been the traditional approach for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services and WCF services.</span></span> <span data-ttu-id="6b210-109">在周邊網路中使用反向 proxy 規則而毋需有 BizTalk 伺服器位於周邊網路中。</span><span class="sxs-lookup"><span data-stu-id="6b210-109">Using reverse proxy rules in the perimeter network obviates the need to have BizTalk servers located in the perimeter network.</span></span> <span data-ttu-id="6b210-110">反向 proxy 規則只是轉送給 HTTP 與 SOAP 要求從周邊網路的電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內部網路網域中。</span><span class="sxs-lookup"><span data-stu-id="6b210-110">The reverse proxy rules simply forward the HTTP and SOAP requests from the perimeter network to the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the intranet domain.</span></span>  
  
 <span data-ttu-id="6b210-111">如需有關使用反向 proxy 的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="6b210-111">For more information about using a reverse proxy, see the following topics in BizTalk Server Help:</span></span>  
  
-   <span data-ttu-id="6b210-112">[「 範例架構： HTTP 和 SOAP 配接器 」](http://go.microsoft.com/fwlink/?LinkId=153339) (http://go.microsoft.com/fwlink/?LinkId=153339)。</span><span class="sxs-lookup"><span data-stu-id="6b210-112">["Sample Architecture: HTTP and SOAP Adapters"](http://go.microsoft.com/fwlink/?LinkId=153339) (http://go.microsoft.com/fwlink/?LinkId=153339).</span></span>  
  
-   <span data-ttu-id="6b210-113">[「 範例 TMA: HTTP 和 SOAP 配接器 」](http://go.microsoft.com/fwlink/?LinkId=153340) (http://go.microsoft.com/fwlink/?LinkId=153340)。</span><span class="sxs-lookup"><span data-stu-id="6b210-113">["Sample TMA: HTTP and SOAP Adapters"](http://go.microsoft.com/fwlink/?LinkId=153340) (http://go.microsoft.com/fwlink/?LinkId=153340).</span></span>  
  
-   <span data-ttu-id="6b210-114">["Large Distributed Architecture"](http://go.microsoft.com/fwlink/?LinkId=153341) (http://go.microsoft.com/fwlink/?LinkId=153341)。</span><span class="sxs-lookup"><span data-stu-id="6b210-114">["Large Distributed Architecture"](http://go.microsoft.com/fwlink/?LinkId=153341) (http://go.microsoft.com/fwlink/?LinkId=153341).</span></span>  
  
## <a name="using-computers-running-biztalk-server-in-the-perimeter-network"></a><span data-ttu-id="6b210-115">使用周邊網路中執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="6b210-115">Using Computers Running BizTalk Server in the Perimeter Network</span></span>  
 <span data-ttu-id="6b210-116">這不是慣用的方法發行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務或網際網路的 WCF 服務，因為它需要執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]位於周邊網路中。</span><span class="sxs-lookup"><span data-stu-id="6b210-116">This is not the preferred approach for publishing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services or WCF services to the Internet because it requires computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to be located in the perimeter network.</span></span> <span data-ttu-id="6b210-117">不過，無法在周邊網路中使用反向 proxy 時，您可以使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="6b210-117">However, when a reverse proxy is not available in the perimeter network, you can use this approach.</span></span>  
  
 <span data-ttu-id="6b210-118">這個方法需要登記在與內部網路網域的單向信任周邊網路網域 （但內部網路網域不信任周邊網路網域）。</span><span class="sxs-lookup"><span data-stu-id="6b210-118">This approach requires the perimeter network domain to enlist in a one-way trust with the intranet domain (but the intranet domain does not trust the perimeter network domain).</span></span> <span data-ttu-id="6b210-119">IIS 應用程式集區必須處於 「 BizTalk 外掛式主控件使用者 」 網域群組的內部網路網域帳戶底下執行 Web 服務或在周邊網路網域中的 WCF 服務主機。</span><span class="sxs-lookup"><span data-stu-id="6b210-119">The IIS application pools that host the Web services or WCF services in the perimeter network domain must be running under an intranet domain account that is in the "BizTalk Isolated Host Users" domain group.</span></span> <span data-ttu-id="6b210-120">這可讓應用程式集區 發佈訊息至必要的權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b210-120">This gives the application pool the required rights to publish messages to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database.</span></span>  
  
 <span data-ttu-id="6b210-121">您必須配合這種情形在防火牆中開啟特定連接埠。</span><span class="sxs-lookup"><span data-stu-id="6b210-121">You must open specific ports in the firewall to accommodate this.</span></span> <span data-ttu-id="6b210-122">如需必要的連接埠的詳細資訊，請參閱[「 連接埠的接收和傳送伺服器 」](http://go.microsoft.com/fwlink/?LinkId=153342) (http://go.microsoft.com/fwlink/?LinkId=153342) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="6b210-122">For more information about the required ports, see ["Ports for the Receive and Send Servers"](http://go.microsoft.com/fwlink/?LinkId=153342) (http://go.microsoft.com/fwlink/?LinkId=153342) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
## <a name="exposing-biztalk-applications-on-the-cloud-using-appfabric-connect-for-services"></a><span data-ttu-id="6b210-123">公開使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="6b210-123">Exposing BizTalk Applications on the Cloud using AppFabric Connect for Services</span></span>  
 <span data-ttu-id="6b210-124">請參閱文章[使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式公開](http://go.microsoft.com/fwlink/?LinkID=204700)(http://go.microsoft.com/fwlink/?LinkID=204700) 如需有關將 BizTalk 應用程式公開為 WCF 服務在雲端上。</span><span class="sxs-lookup"><span data-stu-id="6b210-124">See the article [Exposing BizTalk Applications on the Cloud using AppFabric Connect for Services](http://go.microsoft.com/fwlink/?LinkID=204700) (http://go.microsoft.com/fwlink/?LinkID=204700) for more information about expose BizTalk Applications as WCF Services on the cloud.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b210-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b210-125">See Also</span></span>  
 [<span data-ttu-id="6b210-126">發佈 Web Services1 規劃</span><span class="sxs-lookup"><span data-stu-id="6b210-126">Planning for Publishing Web Services1</span></span>](../technical-guides/planning-for-publishing-web-services1.md)