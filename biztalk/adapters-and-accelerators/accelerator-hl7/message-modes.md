---
title: 訊息模式 |Microsoft Docs
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
ms.openlocfilehash: cfce63f527dbe9643228b3b47a509b404e78c510
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009135"
---
# <a name="message-modes"></a><span data-ttu-id="d2409-102">訊息模式</span><span class="sxs-lookup"><span data-stu-id="d2409-102">Message Modes</span></span>
<span data-ttu-id="d2409-103">有兩個基本概念的基礎 HL7 的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="d2409-103">There are two basic concepts that underlie all HL7 messages.</span></span> <span data-ttu-id="d2409-104">這些概念解決不同的方式交換資料的獨立系統可以進行互動，並提供一段時間內的分散式的醫療保健系統支援的互通性需求的結構。</span><span class="sxs-lookup"><span data-stu-id="d2409-104">These concepts address different ways in which independent systems that exchange data can interact, and provide a structure that supports the requirements of interoperability over time within a distributed health care system.</span></span> <span data-ttu-id="d2409-105">下面所列的概念定義 HL7 設計背後的基礎佈景主題：</span><span class="sxs-lookup"><span data-stu-id="d2409-105">The concepts listed below define the underlying themes behind the HL7 design:</span></span>  
  
- <span data-ttu-id="d2409-106">**傳訊模式**。</span><span class="sxs-lookup"><span data-stu-id="d2409-106">**Messaging Mode**.</span></span> <span data-ttu-id="d2409-107">三個基本的用途的資訊交換辨識： 廣播要求資訊 (interrogative)，（宣告） 的資訊，並要求系統採取的動作上 （必要）。</span><span class="sxs-lookup"><span data-stu-id="d2409-107">The recognition of three fundamental purposes for information exchange: to broadcast information (declarative), to request information (interrogative), and to request that the system take an action (imperative).</span></span> <span data-ttu-id="d2409-108">每個用途有其特定需求和訊息流程的模式。</span><span class="sxs-lookup"><span data-stu-id="d2409-108">Each of these purposes has its particular requirements and pattern of message flow.</span></span>  
  
- <span data-ttu-id="d2409-109">**通知模式**。</span><span class="sxs-lookup"><span data-stu-id="d2409-109">**Acknowledgment Mode**.</span></span> <span data-ttu-id="d2409-110">需要支援緊密和鬆散結合的訊息的樣式。</span><span class="sxs-lookup"><span data-stu-id="d2409-110">The need to support tightly and loosely coupled styles of messaging.</span></span> <span data-ttu-id="d2409-111">HL7 的通知模式讓傳送應用程式需要回應的接收者，或是啟用為了保證訊息傳遞基礎的網路。</span><span class="sxs-lookup"><span data-stu-id="d2409-111">The acknowledgment modes for HL7 enable a sending application either to require a response from the receiver, or to enable the underlying network to guarantee message delivery.</span></span>  
  
- <span data-ttu-id="d2409-112">**當地語系化**。</span><span class="sxs-lookup"><span data-stu-id="d2409-112">**Localization**.</span></span> <span data-ttu-id="d2409-113">需要支援本機的特定需求，讓站台特定的資料引入訊息規格的實體。</span><span class="sxs-lookup"><span data-stu-id="d2409-113">The need to support specific local requirements by allowing entities to introduce site-specific material into message specifications.</span></span>  
  
- <span data-ttu-id="d2409-114">**發展**。</span><span class="sxs-lookup"><span data-stu-id="d2409-114">**Evolution**.</span></span> <span data-ttu-id="d2409-115">需要支援許多介面和許多應用程式的站台，藉由啟用標準版本之間的互通性。</span><span class="sxs-lookup"><span data-stu-id="d2409-115">The need to support sites with many interfaces and many applications by enabling interoperability between standard versions.</span></span> <span data-ttu-id="d2409-116">這可讓實體階段介面升級，而不需要同時升級所有介面。</span><span class="sxs-lookup"><span data-stu-id="d2409-116">This enables entities to stage interface upgrades, as opposed to requiring simultaneous upgrades of all interfaces.</span></span>  
  
  <span data-ttu-id="d2409-117">Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援上述的需求：</span><span class="sxs-lookup"><span data-stu-id="d2409-117">The following functions of Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support the above requirements:</span></span>  
  
- <span data-ttu-id="d2409-118">HL7 通知模式。</span><span class="sxs-lookup"><span data-stu-id="d2409-118">HL7 acknowledgment modes.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="d2409-119"> 支援的原始通知模式藉由傳遞回原始訊息寄件者的應用程式通知。</span><span class="sxs-lookup"><span data-stu-id="d2409-119"> supports the original acknowledgment mode by passing application acknowledgments back to the original message sender.</span></span>  
  
- <span data-ttu-id="d2409-120">不同的傳訊模式。</span><span class="sxs-lookup"><span data-stu-id="d2409-120">Different messaging modes.</span></span> <span data-ttu-id="d2409-121">這可讓廣播至多個目的地，並結合至相關聯的查詢回應的查詢。</span><span class="sxs-lookup"><span data-stu-id="d2409-121">This enables broadcast to multiple destinations, and ties together queries to the associated query response.</span></span>  
  
- <span data-ttu-id="d2409-122">支援多種版本，包括 XML 和直立線符號分隔的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="d2409-122">Support for multiple versions, including XML and pipe-delimited encodings.</span></span>  
  
- <span data-ttu-id="d2409-123">若要啟用各種不同的環境 HL7 版本和升級之間的對應。</span><span class="sxs-lookup"><span data-stu-id="d2409-123">Mapping between HL7 versions to enable diverse environments and upgrades.</span></span>  
  
- <span data-ttu-id="d2409-124">協調流程中的當地語系化 （自訂）。</span><span class="sxs-lookup"><span data-stu-id="d2409-124">Localization (customization) within orchestration.</span></span>  
  
- <span data-ttu-id="d2409-125">若要支援偵錯和評估新的介面的工具。</span><span class="sxs-lookup"><span data-stu-id="d2409-125">Tools to support debugging and evaluation of new interfaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2409-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2409-126">See Also</span></span>  
 <span data-ttu-id="d2409-127">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="d2409-127">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="d2409-128">[使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="d2409-128">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="d2409-129">[使用 HL7 2.xml 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="d2409-129">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 <span data-ttu-id="d2409-130">[訊息類型和事件](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="d2409-130">[Message Types and Events](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md) </span></span>  
 [<span data-ttu-id="d2409-131">HL7 傳訊</span><span class="sxs-lookup"><span data-stu-id="d2409-131">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)