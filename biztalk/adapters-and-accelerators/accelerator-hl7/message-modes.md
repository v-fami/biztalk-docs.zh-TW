---
title: 訊息模式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message modes, about message modes
- messages, message modes
- message modes, HL7 messages
ms.assetid: 2d832b67-6f0e-45e1-95ac-cb80b74a7831
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b09a610d000ae6beaef75b1ed0144d1597d517b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22205054"
---
# <a name="message-modes"></a><span data-ttu-id="ad22c-102">訊息模式</span><span class="sxs-lookup"><span data-stu-id="ad22c-102">Message Modes</span></span>
<span data-ttu-id="ad22c-103">有兩個構成所有 HL7 訊息的基本概念。</span><span class="sxs-lookup"><span data-stu-id="ad22c-103">There are two basic concepts that underlie all HL7 messages.</span></span> <span data-ttu-id="ad22c-104">這些概念位址不同方式交換資料的獨立系統可以互動，並提供一段時間內分散式醫療保健系統支援的互通性需求的結構。</span><span class="sxs-lookup"><span data-stu-id="ad22c-104">These concepts address different ways in which independent systems that exchange data can interact, and provide a structure that supports the requirements of interoperability over time within a distributed health care system.</span></span> <span data-ttu-id="ad22c-105">下面所列的概念定義 HL7 設計背後的基礎佈景主題：</span><span class="sxs-lookup"><span data-stu-id="ad22c-105">The concepts listed below define the underlying themes behind the HL7 design:</span></span>  
  
-   <span data-ttu-id="ad22c-106">**傳訊模式**。</span><span class="sxs-lookup"><span data-stu-id="ad22c-106">**Messaging Mode**.</span></span> <span data-ttu-id="ad22c-107">三種基本的用途的資訊交換的辨識： 廣播要求資訊 (interrogative)，（宣告式） 的資訊，以及要求系統採取的動作上 （必要）。</span><span class="sxs-lookup"><span data-stu-id="ad22c-107">The recognition of three fundamental purposes for information exchange: to broadcast information (declarative), to request information (interrogative), and to request that the system take an action (imperative).</span></span> <span data-ttu-id="ad22c-108">每個用途的特定需求和訊息流程的模式。</span><span class="sxs-lookup"><span data-stu-id="ad22c-108">Each of these purposes has its particular requirements and pattern of message flow.</span></span>  
  
-   <span data-ttu-id="ad22c-109">**通知模式**。</span><span class="sxs-lookup"><span data-stu-id="ad22c-109">**Acknowledgment Mode**.</span></span> <span data-ttu-id="ad22c-110">需要支援緊密和鬆散偶合樣式的傳訊。</span><span class="sxs-lookup"><span data-stu-id="ad22c-110">The need to support tightly and loosely coupled styles of messaging.</span></span> <span data-ttu-id="ad22c-111">HL7 的認可模式可讓傳送應用程式需要來自接收者的回應，或是啟用保證訊息傳遞基礎的網路。</span><span class="sxs-lookup"><span data-stu-id="ad22c-111">The acknowledgment modes for HL7 enable a sending application either to require a response from the receiver, or to enable the underlying network to guarantee message delivery.</span></span>  
  
-   <span data-ttu-id="ad22c-112">**當地語系化**。</span><span class="sxs-lookup"><span data-stu-id="ad22c-112">**Localization**.</span></span> <span data-ttu-id="ad22c-113">需要支援本機的特定需求，讓訊息規格中導入站台特有的資料實體。</span><span class="sxs-lookup"><span data-stu-id="ad22c-113">The need to support specific local requirements by allowing entities to introduce site-specific material into message specifications.</span></span>  
  
-   <span data-ttu-id="ad22c-114">**演進**。</span><span class="sxs-lookup"><span data-stu-id="ad22c-114">**Evolution**.</span></span> <span data-ttu-id="ad22c-115">支援許多介面和許多應用程式的站台啟用標準版本之間的互通性需求。</span><span class="sxs-lookup"><span data-stu-id="ad22c-115">The need to support sites with many interfaces and many applications by enabling interoperability between standard versions.</span></span> <span data-ttu-id="ad22c-116">這可讓實體階段介面升級，而不是需要的所有介面同時升級。</span><span class="sxs-lookup"><span data-stu-id="ad22c-116">This enables entities to stage interface upgrades, as opposed to requiring simultaneous upgrades of all interfaces.</span></span>  
  
 <span data-ttu-id="ad22c-117">下列函式的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援上述的需求：</span><span class="sxs-lookup"><span data-stu-id="ad22c-117">The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support the above requirements:</span></span>  
  
-   <span data-ttu-id="ad22c-118">HL7 通知模式。</span><span class="sxs-lookup"><span data-stu-id="ad22c-118">HL7 acknowledgment modes.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="ad22c-119">支援的原始通知模式藉由傳遞回原始訊息寄件者的應用程式通知。</span><span class="sxs-lookup"><span data-stu-id="ad22c-119"> supports the original acknowledgment mode by passing application acknowledgments back to the original message sender.</span></span>  
  
-   <span data-ttu-id="ad22c-120">不同的訊息模式。</span><span class="sxs-lookup"><span data-stu-id="ad22c-120">Different messaging modes.</span></span> <span data-ttu-id="ad22c-121">這可讓廣播至多個目的地，並結合至相關聯的查詢回應的查詢。</span><span class="sxs-lookup"><span data-stu-id="ad22c-121">This enables broadcast to multiple destinations, and ties together queries to the associated query response.</span></span>  
  
-   <span data-ttu-id="ad22c-122">支援多個版本，包括 XML 和管線分隔的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="ad22c-122">Support for multiple versions, including XML and pipe-delimited encodings.</span></span>  
  
-   <span data-ttu-id="ad22c-123">HL7 版本，以便進行各種不同的環境與升級之間的對應。</span><span class="sxs-lookup"><span data-stu-id="ad22c-123">Mapping between HL7 versions to enable diverse environments and upgrades.</span></span>  
  
-   <span data-ttu-id="ad22c-124">協調流程中的當地語系化 （自訂）。</span><span class="sxs-lookup"><span data-stu-id="ad22c-124">Localization (customization) within orchestration.</span></span>  
  
-   <span data-ttu-id="ad22c-125">工具，以便支援偵錯和評估新的介面。</span><span class="sxs-lookup"><span data-stu-id="ad22c-125">Tools to support debugging and evaluation of new interfaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad22c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad22c-126">See Also</span></span>  
 <span data-ttu-id="ad22c-127">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="ad22c-127">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="ad22c-128">[使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="ad22c-128">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="ad22c-129">[使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="ad22c-129">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 <span data-ttu-id="ad22c-130">[訊息類型和事件](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="ad22c-130">[Message Types and Events](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md) </span></span>  
 [<span data-ttu-id="ad22c-131">HL7 訊息</span><span class="sxs-lookup"><span data-stu-id="ad22c-131">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)