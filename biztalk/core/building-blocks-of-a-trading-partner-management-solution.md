---
title: 建置組塊的交易夥伴管理解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0dabb562-7065-44b8-a26f-658d70b126eb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52e72d0fc6ff852b18d6cfe18e8c1a6fe9eb9839
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993087"
---
# <a name="building-blocks-of-a-trading-partner-management-solution"></a><span data-ttu-id="5d1b1-102">交易夥伴管理方案的建置區塊</span><span class="sxs-lookup"><span data-stu-id="5d1b1-102">Building Blocks of a Trading Partner Management Solution</span></span>
## <a name="overview"></a><span data-ttu-id="5d1b1-103">概觀</span><span class="sxs-lookup"><span data-stu-id="5d1b1-103">Overview</span></span>
<span data-ttu-id="5d1b1-104">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的其中一個核心價值定位就是要讓客戶能夠與其商務合作夥伴進行企業對企業 (B2B) 通訊。</span><span class="sxs-lookup"><span data-stu-id="5d1b1-104">One of the core value propositions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is to empower customers to enable business-to-business (B2B) communication with their business partners.</span></span> <span data-ttu-id="5d1b1-105">為了滿足這類商務需求，企業需要針對下列方面的資訊進行模式建立、儲存與管理：</span><span class="sxs-lookup"><span data-stu-id="5d1b1-105">To fulfill such business needs, enterprises need to model, store, and manage information about:</span></span>  
  
- <span data-ttu-id="5d1b1-106">合作夥伴與其企業</span><span class="sxs-lookup"><span data-stu-id="5d1b1-106">Partners and their businesses</span></span>  
  
- <span data-ttu-id="5d1b1-107">與合作夥伴往來的規則 - 這些包括要使用的訊息編碼通訊協定 (EDI 標準) 及要使用的傳輸通訊協定 (AS2) 等詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5d1b1-107">Rules of engagement with the partners – These include details such as which message encoding protocol to use (EDI standards), which transport protocol to use (AS2), etc.</span></span>  
  
  <span data-ttu-id="5d1b1-108">雖然[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會繼續提供支援 EDI 和 AS2，它將如何管理與儲存夥伴和其業務的相關資訊的基本概念。</span><span class="sxs-lookup"><span data-stu-id="5d1b1-108">While [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] continues to provide support for EDI and AS2, it adds to the fundamental concepts around how to manage and store information about partners and their business.</span></span> <span data-ttu-id="5d1b1-109">EDI 標準、 AS2 訊息和概念共同奠定形成了 B2B 通訊或交易夥伴管理 (TPM) 方案的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="5d1b1-109">EDI standards, AS2 messaging, and the concepts put together form the building blocks of a B2B communication or a Trading Partner Management (TPM) solution.</span></span> <span data-ttu-id="5d1b1-110">本節提供有關這些概念的詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="5d1b1-110">This section provides detailed explanation about these concepts.</span></span> 
 
  <span data-ttu-id="5d1b1-111">如需有關資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]支援 EDI 和 AS2，請參閱：</span><span class="sxs-lookup"><span data-stu-id="5d1b1-111">For information about how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports EDI and AS2, see:</span></span>
 
  - [<span data-ttu-id="5d1b1-112">BizTalk Server EDI 功能</span><span class="sxs-lookup"><span data-stu-id="5d1b1-112">BizTalk Server EDI functionality</span></span>](../core/biztalk-server-edi-functionality.md)
  - [<span data-ttu-id="5d1b1-113">BizTalk Server AS2 功能</span><span class="sxs-lookup"><span data-stu-id="5d1b1-113">BizTalk Server AS2 functionality</span></span>](../core/biztalk-server-as2-functionality.md)
  
## <a name="in-this-section"></a><span data-ttu-id="5d1b1-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="5d1b1-114">In This Section</span></span>  
  
-   [<span data-ttu-id="5d1b1-115">交易夥伴和商務設定檔</span><span class="sxs-lookup"><span data-stu-id="5d1b1-115">Trading partners and business profiles</span></span>](../core/trading-partners-and-business-profiles.md)
  
-   [<span data-ttu-id="5d1b1-116">通訊協定設定</span><span class="sxs-lookup"><span data-stu-id="5d1b1-116">Protocol settings</span></span>](../core/protocol-settings.md)  
  
-   [<span data-ttu-id="5d1b1-117">交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="5d1b1-117">Trading partner agreement</span></span>](../core/trading-partner-agreement.md)  
  
-   [<span data-ttu-id="5d1b1-118">總結： 定義交易夥伴管理解決方案</span><span class="sxs-lookup"><span data-stu-id="5d1b1-118">Putting it all together: Defining a trading partner management solution</span></span>](../core/putting-it-all-together-defining-a-trading-partner-management-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="5d1b1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d1b1-119">See Also</span></span>  
 [<span data-ttu-id="5d1b1-120">使用 BizTalk Server 的交易夥伴管理</span><span class="sxs-lookup"><span data-stu-id="5d1b1-120">Trading Partner Management Using BizTalk Server</span></span>](../core/trading-partner-management-using-biztalk-server.md)