---
title: 訊息類型和事件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, message events
- HL7, message types
- message types
- messages, message types
ms.assetid: d53d51d0-216d-472b-97b7-8a96b8013510
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b9880da0ca5fea84c5a2b3d6e9f3a43ace41970
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22205950"
---
# <a name="message-types-and-events"></a><span data-ttu-id="cdd7e-102">訊息類型和事件</span><span class="sxs-lookup"><span data-stu-id="cdd7e-102">Message Types and Events</span></span>
<span data-ttu-id="cdd7e-103">HL7 標準已分組到真實世界的事件一起做為特定群組相關的訊息*訊息類型*ADT。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-103">The HL7 standard has grouped messages that relate to a particular grouping of real-world events together as *message type* ADT.</span></span> <span data-ttu-id="cdd7e-104">這些訊息包含觸發程序事件，例如病患的管理。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-104">These messages involve trigger events, such as patient administration.</span></span> <span data-ttu-id="cdd7e-105">2.4 版 HL7 標準定義 100 個以上的訊息類型，其中每個 HL7 組織已指派唯一三個字元的訊息型別程式碼。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-105">Version 2.4 of the HL7 standard defines more than 100 message types, each of which the HL7 organization has assigned a unique three-character message type code.</span></span> <span data-ttu-id="cdd7e-106">HL7 標準版本進化，HL7 組織已加入新的訊息類型來提供新功能。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-106">As versions of the HL7 standard have evolved, the HL7 organization has added new message types to provide new capabilities.</span></span>  
  
 <span data-ttu-id="cdd7e-107">所有的訊息類型包含訊息的事件，也稱為*事件*。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-107">All message types contain message events, also called *events*.</span></span> <span data-ttu-id="cdd7e-108">您可以將做為訊息群組內的特定訊息類型的唯一類型事件。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-108">You can think of an event as a unique type of message grouped within a particular message type.</span></span> <span data-ttu-id="cdd7e-109">比方說，瀏覽系統管理員/通知 （訊息事件 A01） 和放電/結束，請瀏覽 （訊息事件 A03） 是唯一病患管理訊息類型 (ADT) 所包含的訊息。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-109">For example, the Admin/Visit Notification (message event A01) and Discharge/End Visit (message event A03) are unique messages contained by the Patient Administration message type (ADT).</span></span> <span data-ttu-id="cdd7e-110">HL7 組織已指派唯一的三個字元事件程式碼的每個訊息的事件。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-110">The HL7 organization has assigned each message event a unique three-character event code.</span></span>  
  
 <span data-ttu-id="cdd7e-111">只有一個訊息類型可以包含特定的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-111">Only one message type can contain a particular message event.</span></span> <span data-ttu-id="cdd7e-112">訊息類型可以包含多個訊息的事件。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-112">Message types can contain multiple message events.</span></span> <span data-ttu-id="cdd7e-113">不過，特定的訊息事件的結構有所不同 HL7 標準版本。</span><span class="sxs-lookup"><span data-stu-id="cdd7e-113">However, the structure of a particular message event can vary between versions of the HL7 standard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd7e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdd7e-114">See Also</span></span>  
 <span data-ttu-id="cdd7e-115">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="cdd7e-115">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="cdd7e-116">[使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="cdd7e-116">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="cdd7e-117">[使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="cdd7e-117">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 <span data-ttu-id="cdd7e-118">[觸發程序事件和訊息](../../adapters-and-accelerators/accelerator-hl7/trigger-events-and-messages.md) </span><span class="sxs-lookup"><span data-stu-id="cdd7e-118">[Trigger Events and Messages](../../adapters-and-accelerators/accelerator-hl7/trigger-events-and-messages.md) </span></span>  
 [<span data-ttu-id="cdd7e-119">HL7 訊息</span><span class="sxs-lookup"><span data-stu-id="cdd7e-119">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)