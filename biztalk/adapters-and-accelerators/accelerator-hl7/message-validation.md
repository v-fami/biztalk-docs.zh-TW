---
title: 訊息驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, messages
- messages, validating
ms.assetid: 720ab16a-7ab4-4741-9951-9ab10a2c4c24
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b4c94b7a7122572724060b2a45447699e15c1a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970191"
---
# <a name="message-validation"></a><span data-ttu-id="e71e3-102">訊息驗證</span><span class="sxs-lookup"><span data-stu-id="e71e3-102">Message Validation</span></span>
<span data-ttu-id="e71e3-103">針對傳入和傳出 HL7 訊息使用 HL7 2.X 接收和傳送管線進行的驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="e71e3-103">Message validation occurs for incoming and outgoing HL7 messages with HL7 2.X receive and send pipelines.</span></span> <span data-ttu-id="e71e3-104">您可以設定驗證只有 MSH （標頭） 區段，或整個訊息本文。</span><span class="sxs-lookup"><span data-stu-id="e71e3-104">You can configure validation for only the MSH (header) segment, or for the entire message body.</span></span> <span data-ttu-id="e71e3-105">此外，就可以針對唯一的當地語系化版本的結構描述進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e71e3-105">In addition, it is possible to validate against unique localized versions of the schema.</span></span> <span data-ttu-id="e71e3-106">您完成定義唯一的命名空間值，並使用此 HL7 傳訊組態 （在合作對象層級） 和實際的結構描述定義訊息的目標命名空間屬性內的命名空間值。</span><span class="sxs-lookup"><span data-stu-id="e71e3-106">You accomplish this by defining a unique namespace value, and using this namespace value within both the HL7 messaging configuration (at the party level) and the target namespace property of the actual schema that defines the message.</span></span> <span data-ttu-id="e71e3-107">在執行階段，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用命名空間和結構描述根參考屬性的組合來選取適當的結構描述的訊息剖析和驗證。</span><span class="sxs-lookup"><span data-stu-id="e71e3-107">At run time, Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses the combination of namespace and the root reference property for the schema to select the appropriate schema for message parsing and validation.</span></span>  
  
 <span data-ttu-id="e71e3-108">剖析器和序列化程式來執行與訊息相關聯的合作對象的設定為基礎的驗證。</span><span class="sxs-lookup"><span data-stu-id="e71e3-108">The parser and serializer perform validation based on the settings for the party associated with a message.</span></span> <span data-ttu-id="e71e3-109">其他合作對象設定，包括批次、 通知和訊息標頭的覆寫會影響剖析或序列化程式執行驗證的方式。</span><span class="sxs-lookup"><span data-stu-id="e71e3-109">Other party settings, including batching, acknowledgment, and message-header override affect how the parser or serializer performs validation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e71e3-110">序列化程式會執行一系列的步驟，包括 （如果適用） 標頭覆寫從 MSH 對應，以及執行 XML 驗證。</span><span class="sxs-lookup"><span data-stu-id="e71e3-110">The serializer performs a series of steps, including (if applicable) performing header overrides from an MSH map, and performing XML validation.</span></span> <span data-ttu-id="e71e3-111">如果標頭覆寫和驗證處理程序同時啟用，且標頭覆寫程序的標頭欄位中輸入值不正確，訊息將無法通過驗證，即使訊息傳遞內文驗證。</span><span class="sxs-lookup"><span data-stu-id="e71e3-111">If the header override and validation processes are both enabled, and the header override process enters an incorrect value into a header field, the message will fail validation, even if the message were to pass body validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71e3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e71e3-112">See Also</span></span>  
 [<span data-ttu-id="e71e3-113">MSH 覆寫</span><span class="sxs-lookup"><span data-stu-id="e71e3-113">MSH Override</span></span>](../../adapters-and-accelerators/accelerator-hl7/msh-override.md)