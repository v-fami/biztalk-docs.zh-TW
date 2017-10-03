---
title: "中樞架構實例的範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supply chains, examples
- hub-and-spoke systems
- supply chains, hub-and-spoke systems
- examples, supply chains
- trading partners, supply chains
ms.assetid: ee92c24d-a281-4950-a61e-9cb3bd08d291
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b417398786e602379d16d6734a5ed366b9d6f2ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-hub-based-scenario"></a><span data-ttu-id="db635-102">範例中樞架構實例</span><span class="sxs-lookup"><span data-stu-id="db635-102">Sample Hub-Based Scenario</span></span>
<span data-ttu-id="db635-103">在許多供應鏈實例中，公司將與每個交易夥伴合作設立 RosettaNet 實作架構 (RNIF) 連線。</span><span class="sxs-lookup"><span data-stu-id="db635-103">In many supply-chain scenarios, a company will work with each of their trading partners to institute a RosettaNet Implementation Framework (RNIF) connection.</span></span> <span data-ttu-id="db635-104">這是標準化整個供應鏈通訊的有效方式。</span><span class="sxs-lookup"><span data-stu-id="db635-104">This is an effective way to standardize communications throughout the supply chain.</span></span> <span data-ttu-id="db635-105">此案例中所述[範例提供鏈結案例](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="db635-105">This scenario is described in [Sample Supply Chain Scenario](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md).</span></span>  
  
 <span data-ttu-id="db635-106">另一個自動化整個供應鏈交易的方式，是公司與其他公司簽約，設定及管理整合系統。</span><span class="sxs-lookup"><span data-stu-id="db635-106">Another way to automate transactions throughout the supply chain is for the company to contract with another company to set up and manage the integrated system.</span></span> <span data-ttu-id="db635-107">這是使用中樞架構的實例。</span><span class="sxs-lookup"><span data-stu-id="db635-107">This is a hub-based scenario.</span></span>  
  
## <a name="how-a-hub-based-system-works"></a><span data-ttu-id="db635-108">中樞架構系統的運作方式</span><span class="sxs-lookup"><span data-stu-id="db635-108">How a Hub-Based System Works</span></span>  
 <span data-ttu-id="db635-109">在中樞架構系統中，簽約使用整合系統的公司會透過 RNIF 連線連接至中樞公司。</span><span class="sxs-lookup"><span data-stu-id="db635-109">In a hub-based system, the company contracting for an integrated system connects to the hub company using an RNIF connection.</span></span> <span data-ttu-id="db635-110">接著中樞公司會使用所需的任何電子連線類型，連接到公司的所有交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="db635-110">The hub then connects to all the company's trading partners using whatever type of electronic connection is required.</span></span> <span data-ttu-id="db635-111">中樞公司提供所有交易夥伴的連線選項：RNIF 連線、EDI、一般檔案、Web 應用程式或非相容的專屬連線。</span><span class="sxs-lookup"><span data-stu-id="db635-111">The hub company provides all the trading partners with connection options: RNIF connections, EDI, flat file, Web applications, or non-compliant, proprietary connections.</span></span> <span data-ttu-id="db635-112">管理通訊系統是中樞公司的責任。</span><span class="sxs-lookup"><span data-stu-id="db635-112">Managing the communications system is the hub company's business.</span></span> <span data-ttu-id="db635-113">下圖顯示這類系統如何運作。</span><span class="sxs-lookup"><span data-stu-id="db635-113">The following figure shows how such a system might work.</span></span>  
  
 <span data-ttu-id="db635-114">![&#60;沒有變更 &#62;] (../../adapters-and-accelerators/accelerator-rosettanet/media/hub-based-scenario.gif "Hub_Based_Scenario")</span><span class="sxs-lookup"><span data-stu-id="db635-114">![&#60;No Change&#62;](../../adapters-and-accelerators/accelerator-rosettanet/media/hub-based-scenario.gif "Hub_Based_Scenario")</span></span>  
  
 <span data-ttu-id="db635-115">中樞架構系統具有許多優點：</span><span class="sxs-lookup"><span data-stu-id="db635-115">A hub-based system has many advantages:</span></span>  
  
-   <span data-ttu-id="db635-116">簽約公司不用處理供應鏈的複雜性；中樞公司將負責處理這些工作。</span><span class="sxs-lookup"><span data-stu-id="db635-116">The contracting company does not have to deal with the complexity of the supply chain; the hub company handles it.</span></span>  
  
-   <span data-ttu-id="db635-117">簽約公司不用維護或升級系統，也不負責處理當機；系統維護與當機維修都由中樞公司負責。</span><span class="sxs-lookup"><span data-stu-id="db635-117">The contracting company does not have to maintain or upgrade the system, and it is not responsible for downtime; the hub company is responsible for system maintenance and downtime.</span></span>  
  
-   <span data-ttu-id="db635-118">簽約公司可以獲得 RosettaNet 相容系統的好處，包括標準化、自動化、節省成本以及透明度。</span><span class="sxs-lookup"><span data-stu-id="db635-118">The contracting company gains the advantages of a RosettaNet-compliant system, including standardization, automation, cost savings, and visibility.</span></span>  
  
-   <span data-ttu-id="db635-119">簽約公司可以透過各種電子連線自動化本身的供應鏈，這些連線讓交易夥伴擁有完備的連線選擇。</span><span class="sxs-lookup"><span data-stu-id="db635-119">The contracting company has fully automated their supply chain with a variety of electronic connections that give the full array of trading partners a choice of connections.</span></span> <span data-ttu-id="db635-120">簽約公司也不用具備維護各種連線選擇的技術性專業知識。</span><span class="sxs-lookup"><span data-stu-id="db635-120">The contracting company does not have to maintain technological expertise in a variety of connection options.</span></span>  
  
-   <span data-ttu-id="db635-121">只要中樞公司支援，交易夥伴就可以繼續使用專屬連線。</span><span class="sxs-lookup"><span data-stu-id="db635-121">A trading partner can continue to use a proprietary connection, as long as the hub company supports it.</span></span>  
  
-   <span data-ttu-id="db635-122">系統具有彈性。</span><span class="sxs-lookup"><span data-stu-id="db635-122">The system is flexible.</span></span> <span data-ttu-id="db635-123">交易夥伴不必採用 RosettaNet 相容系統。</span><span class="sxs-lookup"><span data-stu-id="db635-123">Trading partners do not have to adopt a RosettaNet-compliant system.</span></span> <span data-ttu-id="db635-124">不過，交易夥伴若採用 RosettaNet 相容系統，將會從這種系統大大受益。</span><span class="sxs-lookup"><span data-stu-id="db635-124">However, if they do so, they will gain the benefits from such a system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db635-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db635-125">See Also</span></span>  
 <span data-ttu-id="db635-126">[BizTalk Server 如何解決商務需求](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md) </span><span class="sxs-lookup"><span data-stu-id="db635-126">[How BizTalk Server Solves the Business Need](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md) </span></span>  
 <span data-ttu-id="db635-127">[交易夥伴整合需求](../../adapters-and-accelerators/accelerator-rosettanet/the-need-for-trading-partner-integration.md) </span><span class="sxs-lookup"><span data-stu-id="db635-127">[The Need for Trading Partner Integration](../../adapters-and-accelerators/accelerator-rosettanet/the-need-for-trading-partner-integration.md) </span></span>  
 <span data-ttu-id="db635-128">[供應鏈面臨的挑戰](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-challenge.md) </span><span class="sxs-lookup"><span data-stu-id="db635-128">[The Supply Chain Challenge](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-challenge.md) </span></span>  
 <span data-ttu-id="db635-129">[供應鏈方案](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-solution.md) </span><span class="sxs-lookup"><span data-stu-id="db635-129">[The Supply Chain Solution](../../adapters-and-accelerators/accelerator-rosettanet/the-supply-chain-solution.md) </span></span>  
 [<span data-ttu-id="db635-130">範例供應鏈實例</span><span class="sxs-lookup"><span data-stu-id="db635-130">Sample Supply Chain Scenario</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/sample-supply-chain-scenario.md)