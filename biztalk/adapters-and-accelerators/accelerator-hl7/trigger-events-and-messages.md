---
title: "觸發事件和訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- health care organizations, HL7 messages
- trigger events
- messages, trigger events
- messages, about messages
ms.assetid: e93b397c-8cbe-4589-aa88-e474d7722174
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 188d7f1e09ae3f96c953c6a83bbad42ccdce3643
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="trigger-events-and-messages"></a><span data-ttu-id="16fd7-102">觸發程序事件和訊息</span><span class="sxs-lookup"><span data-stu-id="16fd7-102">Trigger Events and Messages</span></span>
<span data-ttu-id="16fd7-103">在數位醫療保健系統中，應用程式會建立 HL7 訊息，因為真實世界的事件，例如實驗室順序或藥物順序放置。</span><span class="sxs-lookup"><span data-stu-id="16fd7-103">In a digital health care system, applications create HL7 messages because of a real-world event, such as the placing of a laboratory order or drug order.</span></span> <span data-ttu-id="16fd7-104">HL7 組織已寫入 HL7 標準根據健康照護真實世界中的事件建立資料流在應用程式，即使這些應用程式跨異質系統需要的假設。</span><span class="sxs-lookup"><span data-stu-id="16fd7-104">The HL7 organization has written the HL7 standard based on the assumption that an event in the real world of health care creates the need for data to flow among applications, even when these applications span heterogeneous systems.</span></span> <span data-ttu-id="16fd7-105">HL7 標準呼叫此真實世界事件*觸發程序事件*。</span><span class="sxs-lookup"><span data-stu-id="16fd7-105">The HL7 standard calls this real-world event a *trigger event*.</span></span> <span data-ttu-id="16fd7-106">自動化的系統必須有系統地辨識觸發程序事件。</span><span class="sxs-lookup"><span data-stu-id="16fd7-106">An automated system must systematically recognize the trigger event.</span></span>  
  
 <span data-ttu-id="16fd7-107">若要展開這個概念，請考慮下列案例。</span><span class="sxs-lookup"><span data-stu-id="16fd7-107">To expand this concept, consider the following scenario.</span></span> <span data-ttu-id="16fd7-108">在醫院抵達，一位病患註冊醫院使用病患的系統管理軟體應用程式中。</span><span class="sxs-lookup"><span data-stu-id="16fd7-108">On arrival at a hospital, a patient registers in a hospital using a patient administration software application.</span></span> <span data-ttu-id="16fd7-109">上認可的病患的記錄，應用程式需要通知其他醫院應用程式 （例如會計、 實驗室和等等） 有關的病患註冊。</span><span class="sxs-lookup"><span data-stu-id="16fd7-109">On committing the patient records, the application needs to inform other hospital applications (such as accounting, labs, and so on) about the registration of the patient.</span></span> <span data-ttu-id="16fd7-110">跨應用程式共用這項資訊是必要的以便使用這些應用程式的實體可以提供所需的服務與病患。</span><span class="sxs-lookup"><span data-stu-id="16fd7-110">Sharing this information across applications is necessary so that the entities that use those applications can provide the patient with the required services.</span></span> <span data-ttu-id="16fd7-111">註冊一位病患的動作是一種觸發程序事件。</span><span class="sxs-lookup"><span data-stu-id="16fd7-111">The act of registering a patient is a type of trigger event.</span></span> <span data-ttu-id="16fd7-112">Web 應用程式通常會建立此觸發程序事件藉由建立 HL7 訊息，其中包含病患記錄的資料。</span><span class="sxs-lookup"><span data-stu-id="16fd7-112">A Web application typically creates this trigger event by creating an HL7 message containing the data for the patient record.</span></span>  
  
 <span data-ttu-id="16fd7-113">觸發程序事件永遠會導致建立一或多個觸發動作的應用程式處理的訊息中的訊息。</span><span class="sxs-lookup"><span data-stu-id="16fd7-113">Trigger events always result in the creation of one or more messages that trigger an action in the application that processes the message.</span></span> <span data-ttu-id="16fd7-114">觸發程序事件是在其中內嵌 IT 人員的部署案例中相關[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 醫院特定業務應用程式中。</span><span class="sxs-lookup"><span data-stu-id="16fd7-114">Trigger events are relevant in deployment scenarios where IT personnel have embedded [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) within the hospital line-of-business application.</span></span> <span data-ttu-id="16fd7-115">在這種部署案例中，即使[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不需要留意的觸發程序事件，觸發程序事件產生的訊息。</span><span class="sxs-lookup"><span data-stu-id="16fd7-115">Even in such deployment scenarios, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not need to be aware of the trigger event, only the messages that the trigger event generates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16fd7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16fd7-116">See Also</span></span>  
 <span data-ttu-id="16fd7-117">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="16fd7-117">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="16fd7-118">[使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="16fd7-118">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="16fd7-119">[使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="16fd7-119">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 [<span data-ttu-id="16fd7-120">HL7 訊息</span><span class="sxs-lookup"><span data-stu-id="16fd7-120">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)