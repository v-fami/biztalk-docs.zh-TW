---
title: "RosettaNet 與 CIDX 訊息標準 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messaging standards
- CIDX, messaging standards
- RosettaNet, messaging standards
ms.assetid: 3e9c090b-9425-41ae-ae86-d39ca2abfb63
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65eeb63a8e397837b5a512b4a9f5450107ec36bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rosettanet-and-cidx-messaging-standards"></a><span data-ttu-id="4ab99-102">RosettaNet 與 CIDX 訊息標準</span><span class="sxs-lookup"><span data-stu-id="4ab99-102">RosettaNet and CIDX Messaging Standards</span></span>
<span data-ttu-id="4ab99-103">[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 的主要目的，是處理遵循 RosettaNet 或化學產業資料交換 (CIDX) 訊息標準的訊息。</span><span class="sxs-lookup"><span data-stu-id="4ab99-103">The primary purpose of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] is to process messages that conform to the RosettaNet or Chemical Industry Data Exchange (CIDX) messaging standards.</span></span> <span data-ttu-id="4ab99-104">本節提供兩個主要 RosettaNet 標準的相關資訊： RosettaNet 實作架構 (RNIF) 和交易夥伴介面程序 (Pip)。</span><span class="sxs-lookup"><span data-stu-id="4ab99-104">This section provides information about the two major RosettaNet standards: the RosettaNet Implementation Framework (RNIF) and Partner Interface Processes (PIPs).</span></span> <span data-ttu-id="4ab99-105">同時提供有關 CIDX Chem eStandards 的資訊。</span><span class="sxs-lookup"><span data-stu-id="4ab99-105">It also provides information about the CIDX Chem eStandards.</span></span>  
  
 <span data-ttu-id="4ab99-106">RosettaNet 標準是一個新興的、大多數接受的標準集合，以在高科技實例中實作自動訊息交換。</span><span class="sxs-lookup"><span data-stu-id="4ab99-106">The RosettaNet standards are an emerging, widely accepted set of standards for implementing automated message exchange in high-technology scenarios.</span></span> <span data-ttu-id="4ab99-107">RosettaNet 組織的主要目標是建立、實作並促進電子商務程序標準。</span><span class="sxs-lookup"><span data-stu-id="4ab99-107">The purpose of the RosettaNet organization is to create, implement, and promote eBusiness process standards.</span></span> <span data-ttu-id="4ab99-108">這些標準廣泛地運用在高科技製造以及供應鏈程式中。</span><span class="sxs-lookup"><span data-stu-id="4ab99-108">These standards are widely used in high-technology manufacturing and supply-chain applications.</span></span> <span data-ttu-id="4ab99-109">掌管 RosettaNet 組織的六個不同產業協會展示應用程式的廣度：</span><span class="sxs-lookup"><span data-stu-id="4ab99-109">The six different industry councils that govern the RosettaNet organization demonstrate the breadth of the application:</span></span>  
  
-   <span data-ttu-id="4ab99-110">電子元件</span><span class="sxs-lookup"><span data-stu-id="4ab99-110">Electronic components</span></span>  
  
-   <span data-ttu-id="4ab99-111">半導體製造</span><span class="sxs-lookup"><span data-stu-id="4ab99-111">Semiconductor manufacturers</span></span>  
  
-   <span data-ttu-id="4ab99-112">資訊科技</span><span class="sxs-lookup"><span data-stu-id="4ab99-112">Information technology</span></span>  
  
-   <span data-ttu-id="4ab99-113">行動通訊</span><span class="sxs-lookup"><span data-stu-id="4ab99-113">Telecommunications</span></span>  
  
-   <span data-ttu-id="4ab99-114">後勤</span><span class="sxs-lookup"><span data-stu-id="4ab99-114">Logistics</span></span>  
  
-   <span data-ttu-id="4ab99-115">解決方案供應商</span><span class="sxs-lookup"><span data-stu-id="4ab99-115">Solution providers</span></span>  
  
 <span data-ttu-id="4ab99-116">CIDX Chem eStandards 是一套在化學產業實例中，普遍被接受的自動化訊息交換標準集合。</span><span class="sxs-lookup"><span data-stu-id="4ab99-116">The CIDX Chem eStandards are a widely accepted set of standards for implementing automated message exchange in chemical-industry scenarios.</span></span>  
  
 <span data-ttu-id="4ab99-117">如需標準的詳細資訊，請參閱 RosettaNet 網站，網址[http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859)和 CIDX 網站，網址[http://go.microsoft.com/FWLink/?LinkID=34540](http://go.microsoft.com/FWLink/?LinkID=34540)。</span><span class="sxs-lookup"><span data-stu-id="4ab99-117">For more information about standards, see the RosettaNet Web site at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859) and the CIDX Web site at [http://go.microsoft.com/FWLink/?LinkID=34540](http://go.microsoft.com/FWLink/?LinkID=34540).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4ab99-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="4ab99-118">In This Section</span></span>  
  
-   [<span data-ttu-id="4ab99-119">RNIF 標準</span><span class="sxs-lookup"><span data-stu-id="4ab99-119">RNIF Standard</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)  
  
-   [<span data-ttu-id="4ab99-120">RosettaNet Pip</span><span class="sxs-lookup"><span data-stu-id="4ab99-120">RosettaNet PIPs</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)  
  
-   [<span data-ttu-id="4ab99-121">CIDX 訊息標準</span><span class="sxs-lookup"><span data-stu-id="4ab99-121">CIDX Messaging Standards</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)