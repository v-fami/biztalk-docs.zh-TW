---
title: 訊息驗證 |Microsoft 文件
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
ms.openlocfilehash: 940b6aa811cbee845b287c09a66c4b9753313ee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22205942"
---
# <a name="message-validation"></a><span data-ttu-id="6e3c7-102">訊息驗證</span><span class="sxs-lookup"><span data-stu-id="6e3c7-102">Message Validation</span></span>
<span data-ttu-id="6e3c7-103">針對傳入和傳出 HL7 訊息與 HL7 2.X 接收和傳送管線進行的驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-103">Message validation occurs for incoming and outgoing HL7 messages with HL7 2.X receive and send pipelines.</span></span> <span data-ttu-id="6e3c7-104">您可以設定驗證只有 MSH （標頭） 區段，或整個訊息本文。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-104">You can configure validation for only the MSH (header) segment, or for the entire message body.</span></span> <span data-ttu-id="6e3c7-105">此外，便可驗證的結構描述的唯一當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-105">In addition, it is possible to validate against unique localized versions of the schema.</span></span> <span data-ttu-id="6e3c7-106">透過定義唯一的命名空間值，和使用此命名空間值 （在合作對象層級） 的 HL7 訊息組態和目標命名空間屬性，定義訊息的實際結構描述內完成此作業。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-106">You accomplish this by defining a unique namespace value, and using this namespace value within both the HL7 messaging configuration (at the party level) and the target namespace property of the actual schema that defines the message.</span></span> <span data-ttu-id="6e3c7-107">在執行階段， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會使用命名空間和結構描述的根參考 屬性的組合，來選取適當的結構描述的訊息剖析和驗證。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-107">At run time, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses the combination of namespace and the root reference property for the schema to select the appropriate schema for message parsing and validation.</span></span>  
  
 <span data-ttu-id="6e3c7-108">剖析器和序列化程式來執行驗證的設定與訊息相關聯的合作對象為基礎。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-108">The parser and serializer perform validation based on the settings for the party associated with a message.</span></span> <span data-ttu-id="6e3c7-109">其他合作對象設定，包括批次、 通知和訊息標頭的覆寫會影響剖析或序列化程式執行驗證的方式。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-109">Other party settings, including batching, acknowledgment, and message-header override affect how the parser or serializer performs validation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e3c7-110">序列化程式會執行一系列的步驟，包括 （如果適用） 標頭覆寫從 MSH 對應，以及執行 XML 驗證。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-110">The serializer performs a series of steps, including (if applicable) performing header overrides from an MSH map, and performing XML validation.</span></span> <span data-ttu-id="6e3c7-111">如果標頭覆寫和驗證處理程序同時啟用，且標頭覆寫程序的標頭欄位中輸入值不正確，訊息將無法通過驗證，即使訊息通過主體驗證。</span><span class="sxs-lookup"><span data-stu-id="6e3c7-111">If the header override and validation processes are both enabled, and the header override process enters an incorrect value into a header field, the message will fail validation, even if the message were to pass body validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3c7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e3c7-112">See Also</span></span>  
 [<span data-ttu-id="6e3c7-113">MSH 覆寫</span><span class="sxs-lookup"><span data-stu-id="6e3c7-113">MSH Override</span></span>](../../adapters-and-accelerators/accelerator-hl7/msh-override.md)