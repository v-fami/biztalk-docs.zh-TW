---
title: 執行階段架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- runtime, architecture
- architecture, runtime
- runtime
ms.assetid: feff9a84-f19b-44c9-8d05-8e6015bb1ef9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e45ac745dbf6704f06f61155b3f57edfdec9e09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268990"
---
# <a name="runtime-architecture"></a><span data-ttu-id="c211b-102">執行階段架構</span><span class="sxs-lookup"><span data-stu-id="c211b-102">Runtime Architecture</span></span>
<span data-ttu-id="c211b-103">檢視有關在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中各種元件的更多詳細資訊之前，您必須先瞭解元件如何適用於產品的整體架構。</span><span class="sxs-lookup"><span data-stu-id="c211b-103">Before reviewing more detailed information about the various components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], it is important that you have an understanding of how the components fit into the overall architecture of the product.</span></span> <span data-ttu-id="c211b-104">BizTalk Server 執行階段是在發佈/訂閱架構中建置的，在其中訊息會發佈到系統，然後由一或多個作用中訂閱者所接收。</span><span class="sxs-lookup"><span data-stu-id="c211b-104">The BizTalk Server runtime is built on a publish/subscribe architecture in which a message is published into the system, and then received by one or more active subscribers.</span></span> <span data-ttu-id="c211b-105">這個架構的不同類別存在，但在 BizTalk Server 中實作模型通常稱為*以內容為基礎的發佈/訂閱*。</span><span class="sxs-lookup"><span data-stu-id="c211b-105">Different flavors of this architecture exist, but the model implemented in BizTalk Server is often called *content-based publish/subscribe*.</span></span>  
  
 <span data-ttu-id="c211b-106">在以內容為基礎的發佈/訂閱模型中，訂閱者會使用有關訊息的準則集，來指定他們想接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="c211b-106">In a content-based publish/subscribe model, subscribers specify the messages they want to receive using a set of criteria about the message.</span></span> <span data-ttu-id="c211b-107">訊息會在發佈時進行評估，而所有具有相符訂閱 (由篩選條件運算式所指定) 的作用中訂閱者，將會接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c211b-107">The message is evaluated at the time it is published, and all of the active subscribers with matching subscriptions (indicated by filter expressions), receive the message.</span></span> <span data-ttu-id="c211b-108">不過在套用到 BizTalk Server 時，以內文為基礎會有一點點的誤稱，因為用來建置訂閱的準則不一定是來自訊息內文，也可能包含與訊息有關的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="c211b-108">As it applies to BizTalk Server, content-based is a bit of a misnomer, however, because the criteria used to build subscriptions do not have to come from the message content, and may include contextual information about the message as well.</span></span> <span data-ttu-id="c211b-109">如需訂閱機制的詳細資訊，請參閱[發行和訂閱架構](../core/publish-and-subscribe-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="c211b-109">For details of the subscription mechanism, see [Publish and Subscribe Architecture](../core/publish-and-subscribe-architecture.md).</span></span>  
  
 <span data-ttu-id="c211b-110">下列各節描述 BizTalk Server 執行階段架構的各種元件。</span><span class="sxs-lookup"><span data-stu-id="c211b-110">The sections that follow describe the various components of the BizTalk Server runtime architecture.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c211b-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="c211b-111">In This Section</span></span>  
  
-   [<span data-ttu-id="c211b-112">BizTalk Server 訊息</span><span class="sxs-lookup"><span data-stu-id="c211b-112">The BizTalk Server Message</span></span>](../core/the-biztalk-server-message.md)  
  
-   [<span data-ttu-id="c211b-113">訊息的生命週期</span><span class="sxs-lookup"><span data-stu-id="c211b-113">Lifecycle of a Message</span></span>](../core/lifecycle-of-a-message.md)  
  
-   [<span data-ttu-id="c211b-114">處理訊息</span><span class="sxs-lookup"><span data-stu-id="c211b-114">Processing the Message</span></span>](../core/processing-the-message.md)  
  
-   [<span data-ttu-id="c211b-115">要求-回應傳訊</span><span class="sxs-lookup"><span data-stu-id="c211b-115">Request-Response Messaging</span></span>](../core/request-response-messaging.md)  
  
-   [<span data-ttu-id="c211b-116">傳訊引擎</span><span class="sxs-lookup"><span data-stu-id="c211b-116">The Messaging Engine</span></span>](../core/the-messaging-engine.md)  
  
-   [<span data-ttu-id="c211b-117">實體</span><span class="sxs-lookup"><span data-stu-id="c211b-117">Entities</span></span>](../core/entities.md)  
  
-   [<span data-ttu-id="c211b-118">成品</span><span class="sxs-lookup"><span data-stu-id="c211b-118">Artifacts</span></span>](../core/artifacts.md)  
  
-   [<span data-ttu-id="c211b-119">企業單一登入 (SSO)</span><span class="sxs-lookup"><span data-stu-id="c211b-119">Enterprise Single Sign-On (SSO)</span></span>](../core/enterprise-single-sign-on-sso.md)  
  
-   [<span data-ttu-id="c211b-120">商務規則引擎</span><span class="sxs-lookup"><span data-stu-id="c211b-120">Business Rules Engine</span></span>](../core/business-rules-engine.md)  
  
-   [<span data-ttu-id="c211b-121">BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="c211b-121">BizTalk Assemblies</span></span>](../core/biztalk-assemblies.md)