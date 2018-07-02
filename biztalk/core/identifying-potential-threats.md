---
title: 識別潛在的威脅 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- planning, security
- security, potential threats
- security, planning
ms.assetid: 1d70a0c1-6daf-47bb-af15-a4b35a7bafc2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbd2feb0b6a09905efb7275b1cc6f0e6ef2b13d7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972567"
---
# <a name="identifying-potential-threats"></a><span data-ttu-id="ca43a-102">識別潛在的威脅</span><span class="sxs-lookup"><span data-stu-id="ca43a-102">Identifying Potential Threats</span></span>
<span data-ttu-id="ca43a-103">您可以使用 STRIDE 模型來識別 BizTalk Server 部署的潛在威脅。</span><span class="sxs-lookup"><span data-stu-id="ca43a-103">You can use the STRIDE model to identify potential threats to your BizTalk Server deployment.</span></span> <span data-ttu-id="ca43a-104">STRIDE 是衍生自下列類別目錄的縮寫： *S*假冒識別*T*的資料，ampering *R*否認，*我*若資訊洩漏*D*拒絕服務，以及提高權限。</span><span class="sxs-lookup"><span data-stu-id="ca43a-104">STRIDE is an acronym derived from the following categories: *S*poofing identity, *T*ampering with data, *R*epudiation, *I*nformation disclosure, *D*enial of service, and Elevation of privileges.</span></span> <span data-ttu-id="ca43a-105">本節包含 BizTalk Server 環境潛在威脅的範例，以及如何減輕這些威脅的機制。</span><span class="sxs-lookup"><span data-stu-id="ca43a-105">This section contains examples of potential threats to a BizTalk Server environment, and mechanisms to mitigate them.</span></span>  
  
 <span data-ttu-id="ca43a-106">**偽造識別**</span><span class="sxs-lookup"><span data-stu-id="ca43a-106">**Spoofing identity**</span></span>  
  
- <span data-ttu-id="ca43a-107">若您在繫結檔案中儲存密碼，然後儲存這些繫結檔案，則未授權使用者可能可以讀取密碼，並使用它們來連接 BizTalk Server，進而造成損害。</span><span class="sxs-lookup"><span data-stu-id="ca43a-107">If you save passwords in the binding files, and save these binding files, unauthorized users could read the passwords and use them to connect to the BizTalk Servers, and possibly cause harm.</span></span> <span data-ttu-id="ca43a-108">您不應該在繫結檔案中儲存密碼，而應該使用判別存取控制清單 (DACL) 來限制存取可能含有敏感性資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="ca43a-108">You should not save passwords in binding files, and you should use discretionary access control lists (DACLs) to restrict access to files that may contain sensitive data.</span></span>  
  
  <span data-ttu-id="ca43a-109">**竄改資料**</span><span class="sxs-lookup"><span data-stu-id="ca43a-109">**Tampering with data**</span></span>  
  
- <span data-ttu-id="ca43a-110">惡意使用者可以攔截夥伴送至 BizTalk Server 的訊息，並修改訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="ca43a-110">Malicious users can intercept messages from partners to BizTalk Server, and modify the content of the message.</span></span> <span data-ttu-id="ca43a-111">您可以使用數位簽章來防止惡意使用者篡改傳送中的訊息。</span><span class="sxs-lookup"><span data-stu-id="ca43a-111">You can use digital signatures to prevent malicious users from tampering with messages while they are in transit.</span></span>  
  
  <span data-ttu-id="ca43a-112">**不可否認性**</span><span class="sxs-lookup"><span data-stu-id="ca43a-112">**Repudiation**</span></span>  
  
- <span data-ttu-id="ca43a-113">您需要追蹤 BizTalk 傳送和接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="ca43a-113">You need to keep track of messages that BizTalk sends and receives.</span></span> <span data-ttu-id="ca43a-114">您可以使用數位簽章來證明訊息確實是由您和您的夥伴所傳送。</span><span class="sxs-lookup"><span data-stu-id="ca43a-114">You can use digital signatures to prove that you sent a message and that your partners sent you a message.</span></span>  
  
  <span data-ttu-id="ca43a-115">**資訊洩漏**</span><span class="sxs-lookup"><span data-stu-id="ca43a-115">**Information disclosure**</span></span>  
  
- <span data-ttu-id="ca43a-116">惡意使用者可以讀取 BizTalk Server 與 Microsoft SQL Server™ 之間的純文字通訊。</span><span class="sxs-lookup"><span data-stu-id="ca43a-116">Malicious users can read clear-text communication between BizTalk Server and Microsoft SQL Server™.</span></span> <span data-ttu-id="ca43a-117">您可以使用網際網路通訊協定安全性 (IPSec) 或「安全通訊端層」(SSL) 來協助保護伺服器之間的通訊安全。</span><span class="sxs-lookup"><span data-stu-id="ca43a-117">You can use Internet Protocol security (IPSec), or Secure Sockets Layer (SSL) to help secure the communication between servers.</span></span> <span data-ttu-id="ca43a-118">您可以使用防火牆來限制每部伺服器的存取。</span><span class="sxs-lookup"><span data-stu-id="ca43a-118">You can use firewalls to limit access to each server.</span></span> <span data-ttu-id="ca43a-119">也可以使用加密協助保障傳送中訊息的私密性。</span><span class="sxs-lookup"><span data-stu-id="ca43a-119">You can use encryption to help ensure the privacy of the message while it is in transit.</span></span>  
  
- <span data-ttu-id="ca43a-120">未經授權的使用者可能存取網路共用或目錄中的資訊。</span><span class="sxs-lookup"><span data-stu-id="ca43a-120">Unauthorized users may access information on network shares or directories.</span></span> <span data-ttu-id="ca43a-121">您可以使用強式判別存取控制清單 (DACL) 來限制存取使用資源的帳戶。</span><span class="sxs-lookup"><span data-stu-id="ca43a-121">You can use strong discretionary access control lists (DACLs) to limit access to the accounts that use the resources.</span></span>  
  
- <span data-ttu-id="ca43a-122">執行 BizTalk 主控件執行個體的電腦之 Windows 系統管理員有可能發生行為不當的情形，並執行不同層次的攻擊 (例如資訊洩露或拒絕服務)。</span><span class="sxs-lookup"><span data-stu-id="ca43a-122">The Windows administrator on a computer running a BizTalk Host instance can misbehave and carry out different levels of attacks (for example, information disclosure, or denial of service).</span></span> <span data-ttu-id="ca43a-123">不過，在多數狀況下，您可以將這些攻擊限制在電腦遭到攻擊者危害的特定主控件。</span><span class="sxs-lookup"><span data-stu-id="ca43a-123">However, in most cases you can limit these attacks to the particular host whose computer the attacker compromised.</span></span>  
  
  <span data-ttu-id="ca43a-124">**阻斷服務**</span><span class="sxs-lookup"><span data-stu-id="ca43a-124">**Denial of service**</span></span>  
  
- <span data-ttu-id="ca43a-125">惡意使用者可以傳送大量訊息至 BizTalk Server，讓 BizTalk 無法接收有效的訊息。</span><span class="sxs-lookup"><span data-stu-id="ca43a-125">A malicious user can send a large number of messages to BizTalk Server, which could prevent BizTalk from receiving valid messages.</span></span> <span data-ttu-id="ca43a-126">如需有關此威脅的防護技術的詳細資訊，請參閱[減少阻斷的服務攻擊](../core/mitigating-denial-of-service-attacks.md)。</span><span class="sxs-lookup"><span data-stu-id="ca43a-126">For more information about mitigation techniques to this threat, see [Mitigating Denial of Service Attacks](../core/mitigating-denial-of-service-attacks.md).</span></span>  
  
  <span data-ttu-id="ca43a-127">**提高權限**</span><span class="sxs-lookup"><span data-stu-id="ca43a-127">**Elevation of privileges**</span></span>  
  
- <span data-ttu-id="ca43a-128">提升權限的威脅通常發生於在信任的環境中執行不信任的程式碼時，或惡意使用者利用軟體或組態缺陷時。</span><span class="sxs-lookup"><span data-stu-id="ca43a-128">Elevation of privileges threats typically occur when code you do not trust runs in a trusted environment, or when a malicious user exploits a software or configuration flaw.</span></span> <span data-ttu-id="ca43a-129">您必須確定您信任要在環境中部署的組件與其他元件。</span><span class="sxs-lookup"><span data-stu-id="ca43a-129">You must ensure that you trust the assemblies and other components you deploy in your environment.</span></span> <span data-ttu-id="ca43a-130">若要將提升權限攻擊的可能性降到最低，應該使用非重疊的最低權限帳戶，而且應該避免使用系統管理帳戶進行執行階段的服務和作業。</span><span class="sxs-lookup"><span data-stu-id="ca43a-130">To minimize the possibility of an elevation of privileges attack, you should use non-overlapping, least permission accounts, and you should avoid the use of administrative accounts for run time services and operations.</span></span> <span data-ttu-id="ca43a-131">您還要將環境中執行的元件、應用程式與服務的數目降到最低。</span><span class="sxs-lookup"><span data-stu-id="ca43a-131">You should also minimize the number of components, applications, and services running in the environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca43a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca43a-132">See Also</span></span>  
 <span data-ttu-id="ca43a-133">[減少阻斷服務攻擊](../core/mitigating-denial-of-service-attacks.md) </span><span class="sxs-lookup"><span data-stu-id="ca43a-133">[Mitigating Denial of Service Attacks](../core/mitigating-denial-of-service-attacks.md) </span></span>  
 <span data-ttu-id="ca43a-134">[BizTalk Server 部署的安全性建議](../core/security-recommendations-for-a-biztalk-server-deployment.md) </span><span class="sxs-lookup"><span data-stu-id="ca43a-134">[Security Recommendations for a BizTalk Server Deployment](../core/security-recommendations-for-a-biztalk-server-deployment.md) </span></span>  
 [<span data-ttu-id="ca43a-135">安全性規劃</span><span class="sxs-lookup"><span data-stu-id="ca43a-135">Planning for Security</span></span>](../core/planning-for-security.md)