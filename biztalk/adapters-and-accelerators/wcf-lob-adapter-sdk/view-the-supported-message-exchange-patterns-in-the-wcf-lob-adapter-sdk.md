---
title: 檢視支援的訊息交換模式中 WCF LOB 配接器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6662f17-b4f8-45fe-a22f-5d027dc9f2ff
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77fee95033e669bf584220461b330afbb9fd25b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225518"
---
# <a name="view-the-supported-message-exchange-patterns-in-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="adc8f-102">檢視 WCF LOB 配接器 SDK 中的 支援的訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="adc8f-102">View the supported message exchange patterns in the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="adc8f-103">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]支援數個支援的基礎訊息模式[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]包括要求-回覆和單向通訊。</span><span class="sxs-lookup"><span data-stu-id="adc8f-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports several of the messaging patterns supported by the underlying [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] including request-reply, and one-way communication.</span></span> <span data-ttu-id="adc8f-104">不同傳輸支援不同傳訊模式，並因此會影響它們所支援的互動類型。</span><span class="sxs-lookup"><span data-stu-id="adc8f-104">Different transports support different messaging patterns, and thus affect the types of interactions that they support.</span></span>  
  
 <span data-ttu-id="adc8f-105">下表所列的模式由處理[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="adc8f-105">The patterns listed in the following table are handled by the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>  
  
|<span data-ttu-id="adc8f-106">模式</span><span class="sxs-lookup"><span data-stu-id="adc8f-106">Pattern</span></span>|<span data-ttu-id="adc8f-107">Description</span><span class="sxs-lookup"><span data-stu-id="adc8f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adc8f-108">單向輸入</span><span class="sxs-lookup"><span data-stu-id="adc8f-108">One-way inbound</span></span>|<span data-ttu-id="adc8f-109">收到來自特定業務系統的輸入的訊息，但不需要回應從配接器。</span><span class="sxs-lookup"><span data-stu-id="adc8f-109">Inbound messages are received from the line-of-business system but no response is expected from the adapter.</span></span>|  
|<span data-ttu-id="adc8f-110">要求-回應輸入</span><span class="sxs-lookup"><span data-stu-id="adc8f-110">Request-response inbound</span></span>|<span data-ttu-id="adc8f-111">從特定業務系統必須要有適當的回應從配接器接收內送的訊息。</span><span class="sxs-lookup"><span data-stu-id="adc8f-111">Inbound messages are received from the line-of-business system which expects an appropriate response from the adapter.</span></span>|  
|<span data-ttu-id="adc8f-112">單向輸出</span><span class="sxs-lookup"><span data-stu-id="adc8f-112">One-way outbound</span></span>|<span data-ttu-id="adc8f-113">輸出訊息傳送至特定業務系統，但不需要回應從配接器。</span><span class="sxs-lookup"><span data-stu-id="adc8f-113">Outbound messages are sent to the line-of-business system but no response is expected from the adapter.</span></span>|  
|<span data-ttu-id="adc8f-114">要求-回應輸出</span><span class="sxs-lookup"><span data-stu-id="adc8f-114">Request-response outbound</span></span>|<span data-ttu-id="adc8f-115">輸出訊息從配接器預期的回應會傳送給特定業務系統。</span><span class="sxs-lookup"><span data-stu-id="adc8f-115">Outbound messages are sent to the line-of-business system with a response expected from the adapter.</span></span>|  
|<span data-ttu-id="adc8f-116">工作階段輸入</span><span class="sxs-lookup"><span data-stu-id="adc8f-116">Sessionful inbound</span></span>|<span data-ttu-id="adc8f-117">從特定業務系統接收輸入的訊息內的唯一工作階段。</span><span class="sxs-lookup"><span data-stu-id="adc8f-117">Inbound messages are received from the line-of-business system within a unique session.</span></span> <span data-ttu-id="adc8f-118">不需要回應的特定業務系統從配接器。</span><span class="sxs-lookup"><span data-stu-id="adc8f-118">No response is expected by the line-of-business system from the adapter.</span></span>|  
|<span data-ttu-id="adc8f-119">工作階段的輸出</span><span class="sxs-lookup"><span data-stu-id="adc8f-119">Sessionful outbound</span></span>|<span data-ttu-id="adc8f-120">輸出訊息會傳送至特定業務系統中，唯一的工作階段內。</span><span class="sxs-lookup"><span data-stu-id="adc8f-120">Outbound messages are sent to the line-of-business system within a unique session.</span></span> <span data-ttu-id="adc8f-121">不需要回應的特定業務系統從配接器。</span><span class="sxs-lookup"><span data-stu-id="adc8f-121">No response is expected from the line-of-business system by the adapter.</span></span>|  
  
 <span data-ttu-id="adc8f-122">目標應用程式的功能，將會引導您選擇的訊息模式。</span><span class="sxs-lookup"><span data-stu-id="adc8f-122">Your choice of message pattern will be guided by the functionality of the target application.</span></span>  
  
## <a name="planning-for-sessions"></a><span data-ttu-id="adc8f-123">規劃的工作階段</span><span class="sxs-lookup"><span data-stu-id="adc8f-123">Planning for Sessions</span></span>  
 <span data-ttu-id="adc8f-124">訊息模式可能會使用工作的階段，當它想要確保所有配接器與特定業務系統之間交換的訊息必須是相同的交談的一部分。</span><span class="sxs-lookup"><span data-stu-id="adc8f-124">A messaging pattern may use a session when it wants to ensure that all messages exchanged between the adapter and the line-of-business system must be part of the same conversation.</span></span> <span data-ttu-id="adc8f-125">通常需要傳遞保證，但也可以用來支援訊息交換的配接器開發人員可能會有其他需求時，會使用工作階段。</span><span class="sxs-lookup"><span data-stu-id="adc8f-125">Typically sessions are used when delivery guarantee is needed, but they can also be used to support other requirements that an adapter developer may have for message exchange.</span></span>  
  
 <span data-ttu-id="adc8f-126">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]依賴[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]的工作階段支援。</span><span class="sxs-lookup"><span data-stu-id="adc8f-126">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] relies on the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] for session support.</span></span> <span data-ttu-id="adc8f-127">如需工作階段的詳細資訊，請參閱[工作階段、 執行個體，以及並行](https://msdn.microsoft.com/library/ms731193.aspx)。</span><span class="sxs-lookup"><span data-stu-id="adc8f-127">For more information about sessions, see [Sessions, Instancing, and Concurrency](https://msdn.microsoft.com/library/ms731193.aspx).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="adc8f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adc8f-128">See Also</span></span>  
 [<span data-ttu-id="adc8f-129">計劃和設計配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="adc8f-129">Plan and design an adapter using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)