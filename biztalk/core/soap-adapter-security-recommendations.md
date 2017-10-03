---
title: "SOAP 配接器安全性建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, security
- security, SOAP adapters
ms.assetid: f869bd82-df93-45e1-b747-b538820253fb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3053bccde7830d2e8275c8e2f6f668c428709860
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-security-recommendations"></a><span data-ttu-id="c2cb2-102">SOAP 配接器安全性建議</span><span class="sxs-lookup"><span data-stu-id="c2cb2-102">SOAP Adapter Security Recommendations</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c2cb2-103"> 會使用 SOAP 配接器來發佈 (接收) 和取用 (傳送) Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-103"> uses the SOAP adapter to publish (receive) and consume (send) Web services.</span></span> <span data-ttu-id="c2cb2-104">如需有關 SOAP 配接器的詳細資訊，請參閱[SOAP 配接器](../core/soap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-104">For more information about the SOAP adapter, see [SOAP Adapter](../core/soap-adapter.md).</span></span> <span data-ttu-id="c2cb2-105">如需 Web 服務的詳細資訊，請參閱[使用 Web Services](../core/using-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-105">For more information about Web services, see [Using Web Services](../core/using-web-services.md).</span></span> <span data-ttu-id="c2cb2-106">建議您依照這些指導方針，來保護和部署您作業環境中的 SOAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-106">It is recommended you follow these guidelines for securing and deploying the SOAP adapter in your environment.</span></span>  
  
-   <span data-ttu-id="c2cb2-107">如需發佈 Web 服務的安全性建議，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-107">For security recommendations for publishing Web services, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
-   <span data-ttu-id="c2cb2-108">SOAP 配接器會利用超文字傳輸通訊協定 (HTTP)，從 BizTalk Server 傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-108">The SOAP adapter leverages the Hypertext Transfer Protocol (HTTP) to send and receive messages to and from BizTalk Server.</span></span> <span data-ttu-id="c2cb2-109">因此，您必須遵循安全性建議來保護 Internet Information Services (IIS) 的安全。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-109">Therefore, you must follow the security recommendations for securing Internet Information Services (IIS).</span></span> <span data-ttu-id="c2cb2-110">若您使用 IIS 7.0，請確定您遵循 IIS 7.0 中對於設定應用程式隔離的建議。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-110">If you use IIS 7.0, ensure you follow the IIS 7.0 recommendations for configuring application isolation.</span></span> <span data-ttu-id="c2cb2-111">如需詳細資訊，請參閱[建立應用程式集區 (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=196674)。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-111">For more information, see [Create an Application Pool (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=196674).</span></span>  
  
-   <span data-ttu-id="c2cb2-112">當您為 SOAP 接收位置建立應用程式集區時，必須將它設定成在下列帳戶下執行：屬於執行 SOAP 接收配接器之外掛式主控件的 Windows 群組及 Internet Information Services 工作處理序群組 (IIS_WPG group) 的成員。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-112">When you create an application pool for a SOAP receive location, you must configure it to run under an account that is a member of the Windows group for the isolated host running the SOAP receive adapter and the Internet Information Services Worker Process group (IIS_WPG group).</span></span> <span data-ttu-id="c2cb2-113">接著您必須設定 SOAP 接收配接器的主控件執行個體，才能使用此帳戶。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-113">You must then configure the host instance for the SOAP receive adapter to use this account.</span></span> <span data-ttu-id="c2cb2-114">若您變更 IIS_WPG 群組的帳戶，必須確定您也同時更新主控件執行個體，才能在新帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-114">If you change the account for the IIS_WPG group, you must ensure you also update the host instance to run under the new account.</span></span>  
  
-   <span data-ttu-id="c2cb2-115">當您利用 SOAP 傳送配接器來使用「安全通訊端層」(SSL) 用戶端憑證時，必須手動設定這些憑證。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-115">When you use Secure Sockets Layer (SSL) client certificates with the SOAP send adapter, you must manually configure these certificates.</span></span>  
  
-   <span data-ttu-id="c2cb2-116">在取用 Web 服務時，您可以使用匿名、基本、摘要、Windows 整合或是用戶端憑證來驗證。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-116">When consuming Web services, you can use anonymous, basic, digest, Windows integrated, or client certificates for authentication.</span></span> <span data-ttu-id="c2cb2-117">使用基本驗證來取用 Web 服務時，建議您使用 SSL，以確保未授權的人員無法從訊息讀取使用者認證。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-117">When consuming Web services by using basic authentication, it is recommended to use SSL to ensure that an unauthorized person cannot read the user credentials from the message.</span></span>  
  
-   <span data-ttu-id="c2cb2-118">您可以在需要將前端使用者的內容對應到後端系統之認證的實例中，使用「企業單一登入」(SSO)。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-118">You can use Enterprise Single Sign-On (SSO) in scenarios where you need to map the content of the front-end user to credentials in a back-end system.</span></span> <span data-ttu-id="c2cb2-119">如需詳細資訊，請參閱[如何對應單一登入認證](../core/how-to-map-single-sign-on-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-119">For more information, see [How to Map Single Sign-On Credentials](../core/how-to-map-single-sign-on-credentials.md).</span></span>  
  
-   <span data-ttu-id="c2cb2-120">當您使用基本驗證時，或當您未在訊息層次使用加密時，建議您使用 SSL 來接收和傳送訊息，以確保未經授權的人員無法讀取使用者認證。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-120">When using basic authentication, or when you do not use encryption at the message level, it is recommended to use SSL for both receiving and sending messages to ensure that an unauthorized person cannot read the user credentials.</span></span>  
  
-   <span data-ttu-id="c2cb2-121">建議您使用 Windows 整合式驗證來傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-121">It is recommended to use Windows integrated authentication for both sending and receiving messages.</span></span>  
  
-   <span data-ttu-id="c2cb2-122">執行 SOAP 配接器的電腦也有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-122">The computer running the SOAP adapter also has the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime.</span></span> <span data-ttu-id="c2cb2-123">建議您不要在週邊網路中放置 SOAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-123">It is recommended you do not put the SOAP adapter in the perimeter network.</span></span> <span data-ttu-id="c2cb2-124">若您這麼做，就必須從 SQL Server 資料網域的週邊網路開啟連接埠，以連至 MessageBox 資料庫，但這樣將會使 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段暴露在可能的攻擊之下。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-124">If you do, you have to open ports from the perimeter network to the data domain for SQL Server traffic to the MessageBox database, and you are exposing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime to potential attacks.</span></span> <span data-ttu-id="c2cb2-125">建議您在處理網域中 (也就是說，不要在週邊網路中) 設定 SOAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-125">It is recommended you configure the SOAP adapter in the processing domain (that is, not the perimeter network).</span></span> <span data-ttu-id="c2cb2-126">接著就可以設定最外層的防火牆，以透過處理網域中的防火牆來轉送 SOAP 要求。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-126">You can then configure the outermost firewall to forward SOAP requests through the firewall in the processing domain.</span></span> <span data-ttu-id="c2cb2-127">此機制稱為反向 Proxy。</span><span class="sxs-lookup"><span data-stu-id="c2cb2-127">This mechanism is called reverse proxy.</span></span> <span data-ttu-id="c2cb2-128">(Forefront Threat Management Gateway (TMG) 2010 Server 實作稱為「Web 發佈」。)</span><span class="sxs-lookup"><span data-stu-id="c2cb2-128">(The Forefront Threat Management Gateway (TMG) 2010 server implementation is called Web Publishing.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cb2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2cb2-129">See Also</span></span>  
 <span data-ttu-id="c2cb2-130">[接收和傳送伺服器的連接埠](../core/ports-for-the-receive-and-send-servers.md) </span><span class="sxs-lookup"><span data-stu-id="c2cb2-130">[Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md) </span></span>  
 [<span data-ttu-id="c2cb2-131">最小安全性使用者權限</span><span class="sxs-lookup"><span data-stu-id="c2cb2-131">Minimum Security User Rights</span></span>](../core/minimum-security-user-rights.md)