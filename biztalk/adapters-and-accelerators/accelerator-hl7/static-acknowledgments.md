---
title: 靜態通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- static acknowledgements
- acknowledgements, static acknowledgements
ms.assetid: 1cdd01fc-1dae-4851-917f-4f13a0f9595a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8081dc0f3c37c40cb1103567ae06f80037a12730
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206278"
---
# <a name="static-acknowledgments"></a><span data-ttu-id="35f65-102">靜態通知</span><span class="sxs-lookup"><span data-stu-id="35f65-102">Static Acknowledgments</span></span>
<span data-ttu-id="35f65-103">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援原始、 增強型、 延遲，和靜態通知 (ACK) 模式。</span><span class="sxs-lookup"><span data-stu-id="35f65-103">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) supports original, enhanced, deferred, and static acknowledgment (ACK) modes.</span></span> <span data-ttu-id="35f65-104">如果您選取靜態 ACK 模式中的合作對象[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生靜態包含只表示成功或失敗的通知。</span><span class="sxs-lookup"><span data-stu-id="35f65-104">If you select static ACK mode for a party in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will generate static ACKs that contain only an indication of success or failure.</span></span> <span data-ttu-id="35f65-105">靜態通知會指出是否接收系統接收和處理訊息時，於成功和失敗的值設定在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管。</span><span class="sxs-lookup"><span data-stu-id="35f65-105">The static ACK indicates whether the receiving system received and processed the message, in success and failure values configured in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
 <span data-ttu-id="35f65-106">在原始、 增強，及延遲模式，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]產生動態認可。</span><span class="sxs-lookup"><span data-stu-id="35f65-106">In original, enhanced, and deferred modes, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates dynamic ACKs.</span></span> <span data-ttu-id="35f65-107">它們 HL7 編碼，而且所包含的欄位，例如 MSA.1 通知代碼欄位和錯誤區段。</span><span class="sxs-lookup"><span data-stu-id="35f65-107">They are HL7-encoded, and contain fields such as the MSA.1 Acknowledgment Code field and the ERR segment.</span></span> <span data-ttu-id="35f65-108">動態 ACK MSA.1 欄位會指出失敗狀況已拒絕或發生錯誤，導致不同的處理 (請參閱[訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md))。</span><span class="sxs-lookup"><span data-stu-id="35f65-108">The MSA.1 field of a dynamic ACK will indicate whether a failure condition is a Reject or an Error, which result in different processing (see [Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)).</span></span> <span data-ttu-id="35f65-109">錯誤區段會提供有關錯誤的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="35f65-109">The ERR segment provides detailed information about the error.</span></span> <span data-ttu-id="35f65-110">靜態 Ack 沒有提供這類資訊。</span><span class="sxs-lookup"><span data-stu-id="35f65-110">Static ACKs provide no such information.</span></span>  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="35f65-111">處理靜態通知以不同的方式從動態的通知。</span><span class="sxs-lookup"><span data-stu-id="35f65-111"> processes a static ACK differently from a dynamic ACK.</span></span> <span data-ttu-id="35f65-112">如果接收到的雙向傳送埠 （這只會傳送下一個訊息收到通知之後） 靜態的通知，並通知表示失敗 （或不是有效的通知），[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會移至次要傳輸或擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="35f65-112">If a two-way send port (which will only send the next message after receiving the ACK) receives the static ACK, and the ACK indicates failure (or is not a valid ACK), [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will move to the secondary transport or suspend the message.</span></span> <span data-ttu-id="35f65-113">如果收到動態 ACK，視失敗狀況，它不會重試訊息。</span><span class="sxs-lookup"><span data-stu-id="35f65-113">It will not retry the message, as it would if it received a dynamic ACK, depending upon the failure condition.</span></span>  
  
 <span data-ttu-id="35f65-114">當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]剖析器處理靜態通知時，它會將寫入**IsStaticAck**至訊息內容的布林值屬性。</span><span class="sxs-lookup"><span data-stu-id="35f65-114">When the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parser processes a static ACK, it writes the **IsStaticAck** Boolean property to the message context.</span></span> <span data-ttu-id="35f65-115">序列化程式會使用此值來判斷它是否應該處理為靜態的通知訊息</span><span class="sxs-lookup"><span data-stu-id="35f65-115">The serializer uses this value to determine whether it should process the message as a static ACK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f65-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35f65-116">See Also</span></span>  
 <span data-ttu-id="35f65-117">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="35f65-117">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 [<span data-ttu-id="35f65-118">訊息通知區段</span><span class="sxs-lookup"><span data-stu-id="35f65-118">Message Acknowledgment Segment</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)