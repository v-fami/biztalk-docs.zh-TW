---
title: 規劃建立對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, planning
ms.assetid: e86af976-b989-4e24-80d5-3a9a3ac4e443
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72dde6b09b7777204547d00d26af571c9998d73f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="planning-to-create-maps"></a><span data-ttu-id="03eb8-102">規劃建立對應</span><span class="sxs-lookup"><span data-stu-id="03eb8-102">Planning to Create Maps</span></span>
<span data-ttu-id="03eb8-103">使用對應將符合某個結構描述的輸入訊息轉換成符合其他結構描述的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="03eb8-103">You use maps to convert input messages conforming to one schema into output messages conforming to a different schema.</span></span> <span data-ttu-id="03eb8-104">這些轉換可能很簡單或相當複雜，其中包含資訊的計算與合併。</span><span class="sxs-lookup"><span data-stu-id="03eb8-104">These conversions may be simple or quite complex, involving calculations and consolidation of information.</span></span>  
  
 <span data-ttu-id="03eb8-105">下表列出在您規劃建立對應時應回答的一些問題。</span><span class="sxs-lookup"><span data-stu-id="03eb8-105">The following table lists some of the questions that you need to answer when you plan to create maps.</span></span>  
  
|<span data-ttu-id="03eb8-106">規劃問題</span><span class="sxs-lookup"><span data-stu-id="03eb8-106">Planning question</span></span>|<span data-ttu-id="03eb8-107">建議</span><span class="sxs-lookup"><span data-stu-id="03eb8-107">Recommendation</span></span>|  
|-----------------------|--------------------|  
|<span data-ttu-id="03eb8-108">我需要建立哪些對應？</span><span class="sxs-lookup"><span data-stu-id="03eb8-108">What maps do I need to create?</span></span>|<span data-ttu-id="03eb8-109">為您將使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理的商務文件建立一份清單。</span><span class="sxs-lookup"><span data-stu-id="03eb8-109">Make a list of the business documents that you will process with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="03eb8-110">例如，這類清單可能包含訂單、發票、交貨確認等。</span><span class="sxs-lookup"><span data-stu-id="03eb8-110">Such a list might include, for example, a purchase order, an invoice, a shipping confirmation, and so on.</span></span> <span data-ttu-id="03eb8-111">此清單還可能包含多份這種商務文件，例如當您從某個交易夥伴接收的訂單結構不同於從另一位交易夥伴接收的訂單結構時。</span><span class="sxs-lookup"><span data-stu-id="03eb8-111">The list might also include more than one of each such business document, such as when the structure of a purchase order you receive from one trading partner is different than the structure of a purchase order you receive from another trading partner.</span></span><br /><br /> <span data-ttu-id="03eb8-112">瀏覽此清單並決定哪些文件需要使用不同格式，或者哪些文件最好轉換成一般格式來處理。</span><span class="sxs-lookup"><span data-stu-id="03eb8-112">Go through the list and decide which of the documents need to be in a different format, or which documents are best handled by conversion to a common format.</span></span>|  
|<span data-ttu-id="03eb8-113">在哪些地方需要對應？</span><span class="sxs-lookup"><span data-stu-id="03eb8-113">Where do I need maps?</span></span>|<span data-ttu-id="03eb8-114">您可以在傳送埠、接收埠，以及代表商業流程的協調流程上使用對應。</span><span class="sxs-lookup"><span data-stu-id="03eb8-114">You can use maps in send ports, receive ports, and in orchestrations representing business processes.</span></span> <span data-ttu-id="03eb8-115">考慮您想要或需要在哪些地方轉換文件。</span><span class="sxs-lookup"><span data-stu-id="03eb8-115">Consider where you want or need to convert documents.</span></span>|  
|<span data-ttu-id="03eb8-116">有需要轉換的舊對應嗎？</span><span class="sxs-lookup"><span data-stu-id="03eb8-116">Do I have old maps to convert?</span></span>|<span data-ttu-id="03eb8-117">在 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] 和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 中建立的對應不需要修改即可進行移轉。</span><span class="sxs-lookup"><span data-stu-id="03eb8-117">Maps created in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 should migrate without modification.</span></span> <span data-ttu-id="03eb8-118">分配足夠的時間來測試移轉的對應。</span><span class="sxs-lookup"><span data-stu-id="03eb8-118">Allocate enough time to test the migrated maps.</span></span> <span data-ttu-id="03eb8-119">不過，在舊版 BizTalk 中建立的對應可能並不一定是開啟 BizTalk Server 中。</span><span class="sxs-lookup"><span data-stu-id="03eb8-119">However, maps created in older versions of BizTalk may not necessarily open in BizTalk Server.</span></span> <span data-ttu-id="03eb8-120">**注意：**之前的版本中建立的對應[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]可能精確地在運作[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]或[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]2009年。</span><span class="sxs-lookup"><span data-stu-id="03eb8-120">**Note:**  Maps created in the versions prior to [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] may work accurately in [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009.</span></span> <span data-ttu-id="03eb8-121">但是，這些對應可能不會在 BizTalk Server 中開啟。</span><span class="sxs-lookup"><span data-stu-id="03eb8-121">But, those maps may not open in BizTalk Server.</span></span> <br /><br /> <span data-ttu-id="03eb8-122">對應包含**指令碼處理**運算質或自訂運算質可能需要額外的工作。</span><span class="sxs-lookup"><span data-stu-id="03eb8-122">Maps containing **Scripting** functoids or custom functoids may require additional work.</span></span> <span data-ttu-id="03eb8-123">如需詳細資訊，請參閱[移轉運算質](../core/migrating-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="03eb8-123">For more information, see [Migrating Functoids](../core/migrating-functoids.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03eb8-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="03eb8-124">See Also</span></span>  
 <span data-ttu-id="03eb8-125">[關於對應](../core/about-maps.md) </span><span class="sxs-lookup"><span data-stu-id="03eb8-125">[About Maps](../core/about-maps.md) </span></span>  
 [<span data-ttu-id="03eb8-126">移轉運算質</span><span class="sxs-lookup"><span data-stu-id="03eb8-126">Migrating Functoids</span></span>](../core/migrating-functoids.md)