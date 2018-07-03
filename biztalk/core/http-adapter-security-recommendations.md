---
title: HTTP 配接器安全性建議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, HTTP adapters
- configuring [HTTP adapters], security
- HTTP adapters, security
ms.assetid: ef6043c2-c62a-40e5-b2e1-53e60f87a761
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffb4ad155eed3788a76bdf8cdd342750f45dfe72
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992744"
---
# <a name="http-adapter-security-recommendations"></a><span data-ttu-id="666ef-102">HTTP 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="666ef-102">HTTP Adapter Security Recommendations</span></span>
<span data-ttu-id="666ef-103">您可以使用 HTTP 配接器透過「超文字傳輸通訊協定」(HTTP) 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與應用程式之間交換資訊。</span><span class="sxs-lookup"><span data-stu-id="666ef-103">You use the HTTP adapter to exchange information between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and an application by means of the Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="666ef-104">應用程式可以藉由傳送 HTTP POST 或 HTTP GET 要求到指定的 HTTP URL 來傳送訊息到伺服器。</span><span class="sxs-lookup"><span data-stu-id="666ef-104">Applications can send messages to a server by sending HTTP POST or HTTP GET requests to a specified HTTP URL.</span></span> <span data-ttu-id="666ef-105">如需有關 HTTP 配接器的詳細資訊，請參閱 < [HTTP 配接器](../core/http-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="666ef-105">For more information about the HTTP adapter, see [HTTP Adapter](../core/http-adapter.md).</span></span> <span data-ttu-id="666ef-106">建議您使用下列指導方針在環境中部署 HTTP 配接器並保護其安全：</span><span class="sxs-lookup"><span data-stu-id="666ef-106">It is recommended that you use the following guidelines for securing and deploying the HTTP adapter in your environment:</span></span>  
  
- <span data-ttu-id="666ef-107">請確定您為 HTTP 配接器設定 Internet Information Services (IIS) 設定。</span><span class="sxs-lookup"><span data-stu-id="666ef-107">Ensure you configure the Internet Information Services (IIS) settings for the HTTP adapter.</span></span> <span data-ttu-id="666ef-108">如需詳細資訊，請參閱 <<c0> [ 針對 HTTP 接收位置設定 IIS 如何](../core/how-to-configure-iis-for-an-http-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="666ef-108">For more information, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).</span></span>  
  
- <span data-ttu-id="666ef-109">若您使用 7.0，請確定您遵循 IIS 7.0 中對於設定應用程式隔離的建議。</span><span class="sxs-lookup"><span data-stu-id="666ef-109">If you use 7.0, ensure you follow the IIS 7.0 recommendations for configuring application isolation.</span></span>  
  
- <span data-ttu-id="666ef-110">當您使用基本驗證，或您未使用訊息層級加密，建議使用安全通訊端層 (SSL) 來接收和傳送訊息，以確保未經授權的人員無法而讓其竊取使用者認證。</span><span class="sxs-lookup"><span data-stu-id="666ef-110">When you use Basic Authentication, or when you do not use encryption at the message level, it is recommended to use Secure Sockets Layer (SSL) for both receiving and sending messages to ensure that an unauthorized person cannot sniff the user credentials.</span></span>  
  
- <span data-ttu-id="666ef-111">建議您使用 Windows 整合式驗證來傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="666ef-111">It is recommended to use Windows integrated authentication for both sending and receiving messages.</span></span>  
  
- <span data-ttu-id="666ef-112">建議您不要重新命名、複製或移動 ISAPI 延伸模組檔案。</span><span class="sxs-lookup"><span data-stu-id="666ef-112">It is recommended that you do not rename, copy, or move the ISAPI extension file.</span></span> <span data-ttu-id="666ef-113">這可確保安全性更新安裝程式可以正確地套用任何與此檔案相關的可能安全性更新。</span><span class="sxs-lookup"><span data-stu-id="666ef-113">This ensures that the security update installers can correctly apply any potential security updates pertinent to this file.</span></span>  
  
- <span data-ttu-id="666ef-114">您應該為包含 ISAPI 延伸模組檔案的目錄以及為接收訊息所建立的虛擬目錄，使用強式判別存取控制清單 (DACL)。</span><span class="sxs-lookup"><span data-stu-id="666ef-114">You should use strong discretionary access control lists (DACLs) for the directory containing the ISAPI extension file and for the virtual directory that you create for receiving messages.</span></span> <span data-ttu-id="666ef-115">執行 HTTP 配接器之主控件的「BizTalk 外掛式主控件」群組成員需要讀取和執行權限，而 HTTP 配接器所驗證的使用者則需要這些目錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="666ef-115">Members of the BizTalk Isolated Host group for the host running the HTTP adapter need read and execute permissions, and the users that the HTTP adapter authenticates need read permissions on these directories.</span></span>  
  
- <span data-ttu-id="666ef-116">當您搭配 HTTP 傳送配接器使用 SSL 用戶端憑證時，必須手動設定這些憑證。</span><span class="sxs-lookup"><span data-stu-id="666ef-116">When you use SSL client certificates with the HTTP send adapter, you must manually configure these certificates.</span></span>  
  
- <span data-ttu-id="666ef-117">如同其他的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件，建議您不要將 HTTP 配接器放置在周邊網路中。</span><span class="sxs-lookup"><span data-stu-id="666ef-117">Just like other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components, it is recommended you do not put the HTTP adapter in the perimeter network.</span></span> <span data-ttu-id="666ef-118">若您這麼做，就必須開啟從周邊網路到資料網域的連接埠，以便 SQL Server 傳輸至 MessageBox 資料庫，這樣非常容易有風險。</span><span class="sxs-lookup"><span data-stu-id="666ef-118">If you do, you have to open ports from the perimeter network to the data domain for SQL Server traffic to the MessageBox database, which is risk-prone.</span></span> <span data-ttu-id="666ef-119">建議您在處理網域中 (也就是說，不要在周邊網路中) 設定 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="666ef-119">It is recommended you configure the HTTP adapter in the processing domain (that is, not the perimeter network).</span></span> <span data-ttu-id="666ef-120">接著，您就可以設定最外層的防火牆 (FW4)，以透過處理網域中的防火牆 (FW3) 來轉送 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="666ef-120">You can then configure the outmost firewall (FW4) to forward HTTP requests through the firewall in the processing domain (FW3).</span></span> <span data-ttu-id="666ef-121">在此情況下，您不需要周邊網路中的 IIS。</span><span class="sxs-lookup"><span data-stu-id="666ef-121">In this case, you do not need IIS in the perimeter network.</span></span> <span data-ttu-id="666ef-122">此機制稱為反向 Proxy。</span><span class="sxs-lookup"><span data-stu-id="666ef-122">This mechanism is called reverse proxy.</span></span> <span data-ttu-id="666ef-123">(Forefront Threat Management Gateway (TMG) 2010 Server 實作稱為「Web 發佈」。)</span><span class="sxs-lookup"><span data-stu-id="666ef-123">(The Forefront Threat Management Gateway (TMG) 2010 server implementation is called Web Publishing.)</span></span>  
  
- <span data-ttu-id="666ef-124">當您為 HTTP 接收位置建立應用程式集區時，必須將它設定為在下列帳戶下執行：屬於執行 HTTP 接收配接器的外掛式主控件之 Windows 群組以及 Internet Information Services 工作處理序群組的成員 (IIS_WPG group)。</span><span class="sxs-lookup"><span data-stu-id="666ef-124">When you create an application pool for an HTTP receive location, you must configure it to run under an account that is a member of the Windows group for the isolated host running the HTTP receive adapter and the Internet Information Services Worker Process group (IIS_WPG group).</span></span> <span data-ttu-id="666ef-125">接著，您就必須使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 來設定 HTTP 接收配接器的主控件執行個體，才能使用此帳戶。</span><span class="sxs-lookup"><span data-stu-id="666ef-125">You must then use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the host instance for the HTTP receive adapter to use this account.</span></span> <span data-ttu-id="666ef-126">若您變更 IIS_WPG 群組的帳戶，必須確定您也同時更新主控件執行個體，才能在新帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="666ef-126">If you change the account for the IIS_WPG group, you must ensure you also update the host instance to run under the new account.</span></span> <span data-ttu-id="666ef-127">如需詳細資訊，請參閱 <<c0> [ 針對 HTTP 接收位置設定 IIS 如何](../core/how-to-configure-iis-for-an-http-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="666ef-127">For more information, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666ef-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="666ef-128">See Also</span></span>  
 <span data-ttu-id="666ef-129">[接收和傳送伺服器的連接埠](../core/ports-for-the-receive-and-send-servers.md) </span><span class="sxs-lookup"><span data-stu-id="666ef-129">[Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md) </span></span>  
 [<span data-ttu-id="666ef-130">最低安全性使用者權限</span><span class="sxs-lookup"><span data-stu-id="666ef-130">Minimum Security User Rights</span></span>](../core/minimum-security-user-rights.md)