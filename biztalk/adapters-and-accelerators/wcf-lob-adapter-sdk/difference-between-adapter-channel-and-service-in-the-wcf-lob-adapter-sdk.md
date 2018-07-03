---
title: 配接器通道與服務之間的差異在 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24d41d96-0ea1-4a97-bd45-b65afdbbd923
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8583b615e6a6e8fcd999e5120bca531d3c74090d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010031"
---
# <a name="difference-between-adapter-channel-and-service-in-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="4035b-102">配接器通道與服務之間的差異在 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="4035b-102">Difference between adapter channel and service in the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="4035b-103">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]各提供一組可用來公開 （expose） 至取用端應用程式在相同電腦上或網路上的應用程式功能的 Api。</span><span class="sxs-lookup"><span data-stu-id="4035b-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] each provide a set of APIs that can be used to expose application functionality to consuming applications on the same computer or across a network.</span></span> <span data-ttu-id="4035b-104">若要選擇最適當的架構，您必須考慮目標系統應用程式公開功能的商務需求以及要公開的屬性。</span><span class="sxs-lookup"><span data-stu-id="4035b-104">To choose the most appropriate framework, you must consider the properties of the target system application you are exposing as well as the business requirements for the exposed functionality.</span></span> <span data-ttu-id="4035b-105">本主題提供可供您選擇適當的架構指導方針。</span><span class="sxs-lookup"><span data-stu-id="4035b-105">This topic provides guidelines that you can use to choose the appropriate framework.</span></span>  
  
## <a name="when-to-write-an-adapter"></a><span data-ttu-id="4035b-106">撰寫配接器的時機</span><span class="sxs-lookup"><span data-stu-id="4035b-106">When to Write an Adapter</span></span>  
 <span data-ttu-id="4035b-107">請考慮撰寫配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]時：</span><span class="sxs-lookup"><span data-stu-id="4035b-107">Consider writing an adapter using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] when:</span></span>  
  
- <span data-ttu-id="4035b-108">目標系統是現有的非*Web 服務啟用*系統</span><span class="sxs-lookup"><span data-stu-id="4035b-108">The target system is an existing, non-*Web services-enabled* system</span></span>  
  
- <span data-ttu-id="4035b-109">目標系統是動態的且皆可使用新的作業</span><span class="sxs-lookup"><span data-stu-id="4035b-109">The target system is dynamic and can be enhanced with new operations</span></span>  
  
- <span data-ttu-id="4035b-110">目標系統有大量的中繼資料</span><span class="sxs-lookup"><span data-stu-id="4035b-110">The target system has a large amount of metadata</span></span>  
  
- <span data-ttu-id="4035b-111">大量、 多元化的目標系統的資料的使用者數目</span><span class="sxs-lookup"><span data-stu-id="4035b-111">There is a large, diverse number of users for the target system's data</span></span>  
  
- <span data-ttu-id="4035b-112">取用端應用程式需要豐富的應用程式中繼資料探索功能</span><span class="sxs-lookup"><span data-stu-id="4035b-112">Consuming applications need rich application metadata discovery functionality</span></span>  
  
  <span data-ttu-id="4035b-113">例如，如果目標系統包含數百個用於管理健康照護理賠，作業，而且作業是動態的 （表示使用者可以加入新的作業，執行額外的工作），是合理來公開此功能，使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4035b-113">For example, if the target system contains hundreds of operations for managing health care claims, and the operations are dynamic (meaning users can add new operations that perform additional tasks), it makes sense to expose this functionality using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="4035b-114">這可確保新的作業是使用配接器的應用程式設定為可探索。</span><span class="sxs-lookup"><span data-stu-id="4035b-114">This will ensure that new operations are discoverable by applications using the adapter.</span></span> <span data-ttu-id="4035b-115">使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，您必須修改服務合約，因為它是靜態。</span><span class="sxs-lookup"><span data-stu-id="4035b-115">With [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], you would have to modify the service contract because it is static.</span></span>  
  
## <a name="when-to-write-a-service"></a><span data-ttu-id="4035b-116">撰寫服務的時機</span><span class="sxs-lookup"><span data-stu-id="4035b-116">When to Write a Service</span></span>  
 <span data-ttu-id="4035b-117">使用*WCF 服務模型*來建立服務時：</span><span class="sxs-lookup"><span data-stu-id="4035b-117">Use the *WCF Service Model* to create a service when:</span></span>  
  
- <span data-ttu-id="4035b-118">目標系統是靜態的有一組固定的作業</span><span class="sxs-lookup"><span data-stu-id="4035b-118">The target system is static and has a fixed set of operations</span></span>  
  
- <span data-ttu-id="4035b-119">目標系統有少量或沒有中繼資料</span><span class="sxs-lookup"><span data-stu-id="4035b-119">The target system has little or no metadata</span></span>  
  
- <span data-ttu-id="4035b-120">服務開發人員能夠深入瞭解要公開的應用程式</span><span class="sxs-lookup"><span data-stu-id="4035b-120">Service developers have detailed knowledge of the application to be exposed</span></span>  
  
- <span data-ttu-id="4035b-121">公開全新的應用程式</span><span class="sxs-lookup"><span data-stu-id="4035b-121">A brand new application is being exposed</span></span>  
  
- <span data-ttu-id="4035b-122">您要建立泛用的傳輸配接器</span><span class="sxs-lookup"><span data-stu-id="4035b-122">You are creating generic transport adapters</span></span>  
  
  <span data-ttu-id="4035b-123">比方說，如果目標系統包含用於管理的運動團體 20 的作業，您可以將作業公開為靜態合約使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4035b-123">For example, if the target system contains 20 operations for managing sports teams, you can expose the operations as a static contract using [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span> <span data-ttu-id="4035b-124">如此一來，您避免不必要的中繼資料功能的實作，以及您可能可以減少開發時間。</span><span class="sxs-lookup"><span data-stu-id="4035b-124">By doing so, you avoid implementing unnecessary metadata features and you can potentially minimize development time.</span></span>  
  
## <a name="when-to-write-a-channel"></a><span data-ttu-id="4035b-125">撰寫通道的時機</span><span class="sxs-lookup"><span data-stu-id="4035b-125">When to Write a Channel</span></span>  
 <span data-ttu-id="4035b-126">使用*WCF 通道模型*來建立通道時：</span><span class="sxs-lookup"><span data-stu-id="4035b-126">Use the *WCF Channel Model* to create a channel when:</span></span>  
  
-   <span data-ttu-id="4035b-127">建立網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4035b-127">Creating a wire protocol.</span></span> <span data-ttu-id="4035b-128">網路通訊協定的範例包括 WS-ReliableMessaging 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4035b-128">Examples of wire protocols include WS-ReliableMessaging Protocol.</span></span>  
  
-   <span data-ttu-id="4035b-129">傳送/以外的 WCF （TCP、 HTTP、 具名管道、 MSMQ 和 PeerChannel） 中包含的傳輸接收 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="4035b-129">Send/receive WCF messages over a transport other than ones that are included in WCF (TCP, HTTP, Named Pipes, MSMQ and PeerChannel).</span></span> <span data-ttu-id="4035b-130">例如，您可以撰寫 UDP 傳輸、 TIBCO 或 Java 訊息服務 (JMS) 傳輸。</span><span class="sxs-lookup"><span data-stu-id="4035b-130">For example, you can write a UDP transport, TIBCO, or a Java Messaging Service (JMS) transport.</span></span>  
  
-   <span data-ttu-id="4035b-131">不會公開為 Web 服務的系統整合。</span><span class="sxs-lookup"><span data-stu-id="4035b-131">Integrating with a system that is not exposed as a Web service.</span></span>  <span data-ttu-id="4035b-132">在此情況下您的傳輸會做為調整現有系統的訊息格式或 API，可讓 WCF 用戶端直接與現有的系統通訊的 WCF 訊息的配接器。</span><span class="sxs-lookup"><span data-stu-id="4035b-132">In this case your transport acts as an adapter adapting WCF messages to the existing system's message format or API allowing a WCF client to talk directly to the existing system.</span></span> <span data-ttu-id="4035b-133">這個範例是 Web 服務加強 (WSE) 3.0 TCP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="4035b-133">An example of this is the Web Services Enhancement (WSE) 3.0 TCP transport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4035b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4035b-134">See Also</span></span>  
 <span data-ttu-id="4035b-135">[規劃和設計配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md) </span><span class="sxs-lookup"><span data-stu-id="4035b-135">[Plan and design an adapter using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md) </span></span>  
 [<span data-ttu-id="4035b-136">了解 LOB 系統與 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="4035b-136">Understand the LOB system with the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)