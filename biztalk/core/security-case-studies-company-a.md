---
title: "安全性個案研究： 公司 A |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, examples
- security, architecture
- architecture, security
- security, case studies
ms.assetid: 9417ecf9-e340-479f-b120-552c62f3b189
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c1f48edfc2ab2228d910a0729025fd7b4da117f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-case-studies-company-a"></a><span data-ttu-id="60487-102">安全性個案研究： 公司 A</span><span class="sxs-lookup"><span data-stu-id="60487-102">Security Case Studies: Company A</span></span>
<span data-ttu-id="60487-103">公司 A 是工業方面材料與服務的主要供應商。</span><span class="sxs-lookup"><span data-stu-id="60487-103">Company A is a major supplier of material and services to the industrial sector.</span></span> <span data-ttu-id="60487-104">其商務模型需仰賴與重要客戶與供應商的電子交易。</span><span class="sxs-lookup"><span data-stu-id="60487-104">Its business model relies on electronic transactions with key customers and suppliers.</span></span> <span data-ttu-id="60487-105">公司 A 使用 Microsoft BizTalk Application 來管理內部與外部環境之間的交易與通訊。</span><span class="sxs-lookup"><span data-stu-id="60487-105">Company A uses Microsoft BizTalk Application to manage transactions and communications between internal and external environments.</span></span>  
  
## <a name="potential-threats-and-security-concerns"></a><span data-ttu-id="60487-106">潛在威脅與安全性考量</span><span class="sxs-lookup"><span data-stu-id="60487-106">Potential Threats and Security Concerns</span></span>  
 <span data-ttu-id="60487-107">公司 A 要確定它只會處理來自已驗證來源的訊息。</span><span class="sxs-lookup"><span data-stu-id="60487-107">Company A wants to make sure that it processes only messages from authenticated sources.</span></span> <span data-ttu-id="60487-108">BizTalk Server 處理的一些文件可以包含敏感性資訊，像是財務與個人資料。</span><span class="sxs-lookup"><span data-stu-id="60487-108">Some of the documents BizTalk Server processes can contain sensitive information such as financial and personnel data.</span></span> <span data-ttu-id="60487-109">公司 A 使用自訂的加密 API 來驗證內送訊息。</span><span class="sxs-lookup"><span data-stu-id="60487-109">Company A verifies each incoming message by using custom cryptographic APIs.</span></span> <span data-ttu-id="60487-110">它還建置自己的實體架構來處理安全性需求。</span><span class="sxs-lookup"><span data-stu-id="60487-110">It has also built its physical architecture to handle its security needs.</span></span>  
  
 <span data-ttu-id="60487-111">公司 A 使用檔案傳輸通訊協定 (FTP) 提供其部分訊息流量。</span><span class="sxs-lookup"><span data-stu-id="60487-111">Company A uses file transfer protocol (FTP) for some of its message traffic.</span></span> <span data-ttu-id="60487-112">雖然 FTP 基本上並不安全，但公司 A 可接受相關風險，因為它有許多防火牆來協助保護其他對外應用程式的安全。</span><span class="sxs-lookup"><span data-stu-id="60487-112">Although FTP is inherently not secure, Company A accepts the associated risks because it has many firewalls to help secure other outward-facing applications.</span></span> <span data-ttu-id="60487-113">因為公司 A 會透過 HTTPS 接受一些內送資料，所以來自外部來源的拒絕服務 (DoS) 攻擊是一個考量點。</span><span class="sxs-lookup"><span data-stu-id="60487-113">Because Company A receives some of its incoming data through HTTPS, it is concerned about denial of service (DoS) attacks from external sources.</span></span> <span data-ttu-id="60487-114">若是發生 DoS 攻擊，公司有對應的機制可以立即警示適當的人員。</span><span class="sxs-lookup"><span data-stu-id="60487-114">If a DoS attack does occur, the company has mechanisms to alert the appropriate people immediately.</span></span>  
  
## <a name="security-architecture"></a><span data-ttu-id="60487-115">安全性架構</span><span class="sxs-lookup"><span data-stu-id="60487-115">Security Architecture</span></span>  
 <span data-ttu-id="60487-116">下圖顯示公司 A 使用的安全性架構。</span><span class="sxs-lookup"><span data-stu-id="60487-116">The following figure shows the security architecture that Company A uses.</span></span> <span data-ttu-id="60487-117">請注意，它以防火牆將其環境分段，以協助保護它的前端應用程式與內容伺服器、後端資料庫與商務邏輯伺服器，以及外送訊息基礎結構。</span><span class="sxs-lookup"><span data-stu-id="60487-117">Notice that it has segmented its environment with firewalls to help protect its front-end application and content servers, its back-end database and business logic servers, and its outgoing message infrastructure.</span></span>  
  
 <span data-ttu-id="60487-118">**圖 1 公司 A 安全性架構**</span><span class="sxs-lookup"><span data-stu-id="60487-118">**Figure 1 Company A security architecture**</span></span>  
  
 <span data-ttu-id="60487-119">![公司 A 安全性架構](../core/media/airproductsbiztalkinfrastructure.gif "AirProductsBizTalkInfrastructure")</span><span class="sxs-lookup"><span data-stu-id="60487-119">![Company A security architecture](../core/media/airproductsbiztalkinfrastructure.gif "AirProductsBizTalkInfrastructure")</span></span>  
  
 <span data-ttu-id="60487-120">公司 A 有兩個主要方法來傳送和接收 BizTalk Server 的資訊。</span><span class="sxs-lookup"><span data-stu-id="60487-120">Company A has two main methods to send and receive information to and from BizTalk Server.</span></span> <span data-ttu-id="60487-121">第一種方法是使用 FTP。</span><span class="sxs-lookup"><span data-stu-id="60487-121">The first method uses FTP.</span></span> <span data-ttu-id="60487-122">公司 A 使用協力廠商轉譯服務提供者來支援電子資料交換 (EDI)，以和它的供應商及夥伴通訊。</span><span class="sxs-lookup"><span data-stu-id="60487-122">Company A supports electronic data interchange (EDI) transactions by using a third-party translation service provider to communicate with its suppliers and partners.</span></span> <span data-ttu-id="60487-123">此協力廠商轉譯服務提供者以 EDI 格式處理 BizTalk Server 必須處理的內送與外送訂單。</span><span class="sxs-lookup"><span data-stu-id="60487-123">This third-party translation service provider handles incoming and outgoing orders that BizTalk Server must process in an EDI format.</span></span>  
  
 <span data-ttu-id="60487-124">公司 A 所使用的第二種方法是 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="60487-124">The second method that Company A uses is HTTPS.</span></span> <span data-ttu-id="60487-125">公司 A 還使用協力廠商服務提供者做為其工業的中樞，並使公司 A 銷售和消費產品的採購與銷售更容易。</span><span class="sxs-lookup"><span data-stu-id="60487-125">Company A also works with a third-party service provider that serves as a hub for its industry and makes the purchase and sale of products Company A sells and consumes easier.</span></span>  
  
## <a name="secure-digital-certificates"></a><span data-ttu-id="60487-126">安全數位憑證</span><span class="sxs-lookup"><span data-stu-id="60487-126">Secure Digital Certificates</span></span>  
 <span data-ttu-id="60487-127">公司 A 實作它自己的安全數位憑證。</span><span class="sxs-lookup"><span data-stu-id="60487-127">Company A implements its own secure digital certificates.</span></span> <span data-ttu-id="60487-128">它只管理少數憑證。</span><span class="sxs-lookup"><span data-stu-id="60487-128">It manages only a few certificates.</span></span> <span data-ttu-id="60487-129">因為它使用協力廠商服務提供者，所以比較不關注數位憑證。</span><span class="sxs-lookup"><span data-stu-id="60487-129">Because it uses a third-party service provider, it is less concerned about digital certificates.</span></span> <span data-ttu-id="60487-130">公司 A 瞭解服務提供者比較關注數位憑證，因為服務提供者會和許多不同的機構互動。</span><span class="sxs-lookup"><span data-stu-id="60487-130">Company A realizes that digital certificates are a greater concern for the service provider, because the service provider interacts with many different institutions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60487-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60487-131">See Also</span></span>  
 <span data-ttu-id="60487-132">[小型與中型公司的安全性案例研究](../core/security-case-studies-for-small-to-medium-sized-companies.md)  </span><span class="sxs-lookup"><span data-stu-id="60487-132">[Security Case Studies for Small & Medium-Sized Companies](../core/security-case-studies-for-small-to-medium-sized-companies.md)  </span></span>  
 [<span data-ttu-id="60487-133">威脅模型分析的範例案例</span><span class="sxs-lookup"><span data-stu-id="60487-133">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)