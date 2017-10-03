---
title: "設計安全架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- firewalls
- architecture, security
- installation, firewalls
- installation, security
ms.assetid: 93df6a3f-396c-4767-99c8-2145bddf8fdf
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 157c11477efb9dec455e9ac2de81736cd4ea72ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="designing-a-secure-architecture"></a><span data-ttu-id="64820-102">設計安全架構</span><span class="sxs-lookup"><span data-stu-id="64820-102">Designing a Secure Architecture</span></span>
<span data-ttu-id="64820-103">完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。</span><span class="sxs-lookup"><span data-stu-id="64820-103">For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="64820-104">主題中所提供的架構[大型分散式架構](../core/large-distributed-architecture.md)解決了許多 BizTalk 環境是易受攻擊的潛在安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="64820-104">The architecture presented in the topic [Large Distributed Architecture](../core/large-distributed-architecture.md) addresses many of the potential security threats to which a BizTalk environment is vulnerable.</span></span> <span data-ttu-id="64820-105">不過，您需要評估您的商務判斷提示、您的商務所關心的威脅以及可以保護您的判斷提示並減輕潛在威脅的資源，以確定最適於您的架構。</span><span class="sxs-lookup"><span data-stu-id="64820-105">However, you need to evaluate your business assets, the threats that are a concern for your business, and the resources you have available to protect your assets and mitigate your potential threats to determine what the best architecture is for you.</span></span> <span data-ttu-id="64820-106">本節提供設計 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 架構時您可以考量的其他安全性選項。</span><span class="sxs-lookup"><span data-stu-id="64820-106">This section provides additional security options you can consider when designing your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture.</span></span>  
  
## <a name="firewalls"></a><span data-ttu-id="64820-107">防火牆</span><span class="sxs-lookup"><span data-stu-id="64820-107">Firewalls</span></span>  
 <span data-ttu-id="64820-108">您可以使用實體 (硬體) 或軟體防火牆來限制存取環境中的資源。</span><span class="sxs-lookup"><span data-stu-id="64820-108">You can use physical (hardware) or software firewalls to restrict access to the resources in your environment.</span></span> <span data-ttu-id="64820-109">雖然本主題[大型分散式架構](../core/large-distributed-architecture.md)使用 Forefront Threat Management Gateway (TMG) 2010 server，您可以使用硬體或協力廠商軟體防火牆、 建立類似的架構，只要您開啟和設定不同的 BizTalk Server 元件之間的通訊時所需的連接埠。</span><span class="sxs-lookup"><span data-stu-id="64820-109">While the topic [Large Distributed Architecture](../core/large-distributed-architecture.md) uses Forefront Threat Management Gateway (TMG) 2010 server, you can create a similar architecture by using hardware or third-party software firewalls, as long as you open and configure the ports required for communication between the different BizTalk Server components.</span></span> <span data-ttu-id="64820-110">如需 BizTalk Server 使用的連接埠的詳細資訊，請參閱[所需的 BizTalk Server 的連接埠](../core/required-ports-for-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="64820-110">For more information about the ports BizTalk Server uses, see [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md).</span></span>  
  
## <a name="active-directory"></a><span data-ttu-id="64820-111">Active Directory</span><span class="sxs-lookup"><span data-stu-id="64820-111">Active Directory</span></span>  
 <span data-ttu-id="64820-112">在範例部署中，可以使用 Active Directory® 目錄服務，在每個伺服器群組周圍建立堅固的安全界限。</span><span class="sxs-lookup"><span data-stu-id="64820-112">In the sample deployment, Active Directory® directory service is used to create a hard security boundary around each group of servers.</span></span> <span data-ttu-id="64820-113">您可以使用單向信任，進一步保護 BizTalk Server 環境免於遭到在處理伺服器上執行的其他非 BizTalk Server 應用程式缺陷的攻擊，而使用在資料網域中建立的帳戶來執行 BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="64820-113">With the one-way trusts, you can further protect the BizTalk Server environment from attacks due to flaws in other non-BizTalk Server applications running on the processing servers, as the BizTalk Server applications run under accounts created in the data domain.</span></span> <span data-ttu-id="64820-114">因為資料網域不信任其他網域中的任何帳戶，所以其他網域中帳戶的洩漏仍可保持 BizTalk Server 環境免於受害。</span><span class="sxs-lookup"><span data-stu-id="64820-114">Because the data domain does not trust any accounts in any other domain, a compromise of an account in another domain keeps the BizTalk Server environment from being compromised.</span></span>  
  
## <a name="ipsec-and-ssl"></a><span data-ttu-id="64820-115">IPSec 與 SSL</span><span class="sxs-lookup"><span data-stu-id="64820-115">IPSec and SSL</span></span>  
 <span data-ttu-id="64820-116">若您的環境沒有造成需要提供安全性防火牆層級的重要威脅，但是連接資料、處理以及服務網域的網路區段並未實際防護各種網路攻擊 (例如封包探查或竄改)，則您仍需要保護在伺服器之間傳送的資料。</span><span class="sxs-lookup"><span data-stu-id="64820-116">If your environment does not pose critical threats that require the level of security firewalls provide, but the network segments that connect the data, processing, and services domains are not physically secure from various network attacks (for example packet sniffing or tampering), you still need to protect the data as it goes from one server to another.</span></span> <span data-ttu-id="64820-117">在此狀況下，建議您使用「網際網路通訊協定安全性」(IPSec) 或「安全通訊端層」(SSL) 來加密伺服器之間的流量。</span><span class="sxs-lookup"><span data-stu-id="64820-117">In this case, you can use Internet Protocol security (IPSec) or Secure Sockets Layer (SSL) to encrypt traffic from one server to another.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64820-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64820-118">See Also</span></span>  
 <span data-ttu-id="64820-119">[設計分散式的架構](../core/designing-a-distributed-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="64820-119">[Designing a Distributed Architecture](../core/designing-a-distributed-architecture.md) </span></span>  
 <span data-ttu-id="64820-120">[安全性規劃](../core/planning-for-security.md) </span><span class="sxs-lookup"><span data-stu-id="64820-120">[Planning for Security](../core/planning-for-security.md) </span></span>  
 <span data-ttu-id="64820-121">[設計 BizTalk Server 的系統架構](../core/designing-the-system-architectures-for-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="64820-121">[Designing the System Architectures for BizTalk Server](../core/designing-the-system-architectures-for-biztalk-server.md) </span></span>  
 [<span data-ttu-id="64820-122">BizTalk Server 架構範例</span><span class="sxs-lookup"><span data-stu-id="64820-122">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)