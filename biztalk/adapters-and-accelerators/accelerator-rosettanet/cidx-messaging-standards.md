---
title: "CIDX 訊息標準 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CIDX, RosettaNet
- RosettaNet, CIDX
ms.assetid: 6f70fa56-1fc3-4016-ac9e-6af18026292a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d37cd02f92a8a13857071d0b3d84ab40c480787
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="cidx-messaging-standards"></a><span data-ttu-id="81eaf-102">CIDX 訊息標準</span><span class="sxs-lookup"><span data-stu-id="81eaf-102">CIDX Messaging Standards</span></span>
<span data-ttu-id="81eaf-103">CIDX (Chemical Industry Data Exchange，化學產業資料交換) 為一標準組織，支援及維護 Chem eStandards 標準化訊息交換。</span><span class="sxs-lookup"><span data-stu-id="81eaf-103">CIDX (Chemical Industry Data Exchange) operates as a standards organization that supports and maintains the Chem eStandards for standardized message exchange.</span></span> <span data-ttu-id="81eaf-104">化學工業公司使用這些標準，因應其業界特有的訊息傳送需求。</span><span class="sxs-lookup"><span data-stu-id="81eaf-104">Companies in the chemical industry use these standards for their industry-specific messaging needs.</span></span>  
  
 <span data-ttu-id="81eaf-105">CIDX 在訊息傳送層已採用 RosettaNet 實作架構 (RNIF)，以便進行 XML 文件的交換。</span><span class="sxs-lookup"><span data-stu-id="81eaf-105">CIDX has adopted the RosettaNet Implementation Framework (RNIF) at the messaging layer to enable the exchange of XML documents.</span></span> <span data-ttu-id="81eaf-106">CIDX 尚未採用 RNIF 標準的公開程序層。</span><span class="sxs-lookup"><span data-stu-id="81eaf-106">CIDX has not adopted the public-process layer of the RNIF standards.</span></span>  
  
 <span data-ttu-id="81eaf-107">Chem eStandards 定義了 XML 文件類型定義 (DTD)，描述了系統交換的訊息服務內容。</span><span class="sxs-lookup"><span data-stu-id="81eaf-107">Chem eStandards define XML document type definitions (DTDs) that describe the service content of a message that systems exchange.</span></span> <span data-ttu-id="81eaf-108">訊息在結構上與 RNIF 1.1 RosettaNet 物件相同，差別在於服務內容及部分標頭值。</span><span class="sxs-lookup"><span data-stu-id="81eaf-108">The message is the same as an RNIF 1.1 RosettaNet object in structure, with differences in the service content and some header values.</span></span> <span data-ttu-id="81eaf-109">當 CIDX 標準與 RosettaNet 訊息相符時，CIDX 標準會採用 RosettaNet 項目名稱及資料結構。</span><span class="sxs-lookup"><span data-stu-id="81eaf-109">When there is a match between CIDX standards and RosettaNet messages, the CIDX standard adopts RosettaNet element names and data structures.</span></span>  
  
 <span data-ttu-id="81eaf-110">CIDX 之前都是使用電子文件交換 (EDI) 格式來交換訊息，但如今已形成一組以 XML 技術為主的新文件。</span><span class="sxs-lookup"><span data-stu-id="81eaf-110">CIDX has traditionally used electronic document interchange (EDI) for message exchange, but has formed a new set of documents based on XML technologies.</span></span> <span data-ttu-id="81eaf-111">Chem eStandards 提供 EDI 訊息的 XML 複本。</span><span class="sxs-lookup"><span data-stu-id="81eaf-111">Chem eStandards provide XML replicas of EDI messages.</span></span>  
  
 <span data-ttu-id="81eaf-112">Chem eStandards 為每個商務交易建立個別的訊息。</span><span class="sxs-lookup"><span data-stu-id="81eaf-112">Chem eStandards create individual messages for every business transaction.</span></span> <span data-ttu-id="81eaf-113">Chem eStandards 使用兩種類型的訊息回應： 技術回應與交易回應。</span><span class="sxs-lookup"><span data-stu-id="81eaf-113">Chem eStandards use two types of message responses: technical responses and transaction responses.</span></span> <span data-ttu-id="81eaf-114">為了達到安全且可靠的訊息傳送，Chem eStandards 只會使用 RNIF 1.1 的通知 (Notification) 類型程序，</span><span class="sxs-lookup"><span data-stu-id="81eaf-114">For secure and reliable messaging, Chem eStandards only use Notification type processes of RNIF 1.1.</span></span> <span data-ttu-id="81eaf-115">而不會使用交易夥伴介面程序 (PIP) 0A1。</span><span class="sxs-lookup"><span data-stu-id="81eaf-115">Chem eStandards do not use Partner Interface Process (PIP) 0A1.</span></span>  
  
## <a name="cidx-and-rosettanet-differences"></a><span data-ttu-id="81eaf-116">CIDX 與 RosettaNet 之間的差異</span><span class="sxs-lookup"><span data-stu-id="81eaf-116">CIDX and RosettaNet Differences</span></span>  
 <span data-ttu-id="81eaf-117">下表顯示 RosettaNet 與 CIDX 之間的一些差異。</span><span class="sxs-lookup"><span data-stu-id="81eaf-117">The following table shows some of the differences between RosettaNet and CIDX.</span></span>  
  
|<span data-ttu-id="81eaf-118">RosettaNet 實作</span><span class="sxs-lookup"><span data-stu-id="81eaf-118">RosettaNet implementation</span></span>|<span data-ttu-id="81eaf-119">CIDX 實作</span><span class="sxs-lookup"><span data-stu-id="81eaf-119">CIDX implementation</span></span>|  
|-------------------------------|-------------------------|  
|<span data-ttu-id="81eaf-120">RosettaNet 會將「Application/x-RosettaNet」當做「多用途網際網路郵件延伸標準」(Multipurpose Internet Mail Extensions，MIME) 類型使用。</span><span class="sxs-lookup"><span data-stu-id="81eaf-120">RosettaNet uses the "Application/x-RosettaNet" as the Multipurpose Internet Mail Extensions (MIME) type.</span></span>|<span data-ttu-id="81eaf-121">CIDX 會將「Application/x-ChemXML」當做 MIME 類型使用。</span><span class="sxs-lookup"><span data-stu-id="81eaf-121">CIDX uses "Application/x-ChemXML" as the MIME type.</span></span>|  
|<span data-ttu-id="81eaf-122">對於 RosettaNet 標頭，RosettaNet 會使用 GlobalAdministeringAuthorityCode = RosettaNet</span><span class="sxs-lookup"><span data-stu-id="81eaf-122">For RosettaNet headers, RosettaNet uses GlobalAdministeringAuthorityCode = RosettaNet</span></span>|<span data-ttu-id="81eaf-123">CIDX 會使用 GlobalAdministeringAuthorityCode = CIDX</span><span class="sxs-lookup"><span data-stu-id="81eaf-123">CIDX uses GlobalAdministeringAuthorityCode = CIDX</span></span>|  
|<span data-ttu-id="81eaf-124">RosettaNet 支援單向動作和雙向動作訊息。</span><span class="sxs-lookup"><span data-stu-id="81eaf-124">RosettaNet supports single-action and double-action messages.</span></span>|<span data-ttu-id="81eaf-125">CIDX 僅支援單向動作訊息。</span><span class="sxs-lookup"><span data-stu-id="81eaf-125">CIDX supports only single-action messages.</span></span>|  
|<span data-ttu-id="81eaf-126">RosettaNet 支援 PIP 0A1 (失敗通知)。</span><span class="sxs-lookup"><span data-stu-id="81eaf-126">RosettaNet supports PIP 0A1 (Notification of Failure).</span></span>|<span data-ttu-id="81eaf-127">CIDX 不支援 PIP 0A1。</span><span class="sxs-lookup"><span data-stu-id="81eaf-127">CIDX does not support PIP 0A1.</span></span>|  
|<span data-ttu-id="81eaf-128">RosettaNet 訊息可以是「交易」(Transaction) 或「通知」(Notification) 類型。</span><span class="sxs-lookup"><span data-stu-id="81eaf-128">RosettaNet messages can be of Transaction or Notification type.</span></span>|<span data-ttu-id="81eaf-129">所有 CIDX 訊息都屬於「通知」類型。</span><span class="sxs-lookup"><span data-stu-id="81eaf-129">All CIDX messages are of the Notification type.</span></span>|  
|<span data-ttu-id="81eaf-130">在 RosettaNet 中，必須從 PIP 規格衍生 PIP 組態設定。</span><span class="sxs-lookup"><span data-stu-id="81eaf-130">In RosettaNet, you must derive PIP Configuration Settings from the PIP specifications.</span></span>|<span data-ttu-id="81eaf-131">在 CIDX 中，必須從 CIDX Chem eStandards 規格衍生 PIP 組態設定。</span><span class="sxs-lookup"><span data-stu-id="81eaf-131">In CIDX, you must derive PIP Configuration Settings from the CIDX Chem eStandards specifications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81eaf-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81eaf-132">See Also</span></span>  
 <span data-ttu-id="81eaf-133">[RosettaNet 與 CIDX 訊息標準](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md) </span><span class="sxs-lookup"><span data-stu-id="81eaf-133">[RosettaNet and CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md) </span></span>  
 <span data-ttu-id="81eaf-134">[RNIF 標準](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md) </span><span class="sxs-lookup"><span data-stu-id="81eaf-134">[RNIF Standard](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md) </span></span>  
 <span data-ttu-id="81eaf-135">[RosettaNet Pip](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md) </span><span class="sxs-lookup"><span data-stu-id="81eaf-135">[RosettaNet PIPs](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md) </span></span>  
 [<span data-ttu-id="81eaf-136">CIDX 支援</span><span class="sxs-lookup"><span data-stu-id="81eaf-136">CIDX Support</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)