---
title: "ACK 訊息結構描述類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, ACK schemas
- acknowledgements, ACK schema types
- ACK messages
ms.assetid: da6981a0-a70a-481e-8db4-4a6851f205f1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c29657226c993a68b8cd557a39a7837717e2c66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ack-message-schema-types"></a><span data-ttu-id="f5506-102">ACK 訊息結構描述類型</span><span class="sxs-lookup"><span data-stu-id="f5506-102">ACK Message Schema Types</span></span>
<span data-ttu-id="f5506-103">通知訊息結構描述有兩種形式：</span><span class="sxs-lookup"><span data-stu-id="f5506-103">Acknowledgment message schemas come in two forms:</span></span>  
  
-   <span data-ttu-id="f5506-104">**一般通知 (ACK)**。</span><span class="sxs-lookup"><span data-stu-id="f5506-104">**General acknowledgment (ACK)**.</span></span> <span data-ttu-id="f5506-105">您可以使用一般通知 (ACK) 的應用程式不會定義特殊的特定業務應用程式層級的通知訊息或發生錯誤，使應用程式處理的地方。</span><span class="sxs-lookup"><span data-stu-id="f5506-105">You can use a general acknowledgment (ACK) where the application does not define a special line-of-business application level acknowledgment message or where an error occurred that precludes application processing.</span></span> <span data-ttu-id="f5506-106">您也可以使用它針對接受的層級的通知。</span><span class="sxs-lookup"><span data-stu-id="f5506-106">You can also use it for accept level acknowledgments.</span></span> <span data-ttu-id="f5506-107">下表列出的 ACK 訊息結構。</span><span class="sxs-lookup"><span data-stu-id="f5506-107">The following table lists the ACK message structure.</span></span>  
  
    |<span data-ttu-id="f5506-108">ACK ^ 變化 ^ 通知</span><span class="sxs-lookup"><span data-stu-id="f5506-108">ACK^varies^ACK</span></span>|<span data-ttu-id="f5506-109">一般通知</span><span class="sxs-lookup"><span data-stu-id="f5506-109">General acknowledgment</span></span>|<span data-ttu-id="f5506-110">章節</span><span class="sxs-lookup"><span data-stu-id="f5506-110">Chapter</span></span>|  
    |--------------------|----------------------------|-------------|  
    |<span data-ttu-id="f5506-111">MSH</span><span class="sxs-lookup"><span data-stu-id="f5506-111">MSH</span></span>|<span data-ttu-id="f5506-112">訊息標頭</span><span class="sxs-lookup"><span data-stu-id="f5506-112">Message Header</span></span>|<span data-ttu-id="f5506-113">2</span><span class="sxs-lookup"><span data-stu-id="f5506-113">2</span></span>|  
    |<span data-ttu-id="f5506-114">MSA</span><span class="sxs-lookup"><span data-stu-id="f5506-114">MSA</span></span>|<span data-ttu-id="f5506-115">通知訊息</span><span class="sxs-lookup"><span data-stu-id="f5506-115">Message Acknowledgment</span></span>|<span data-ttu-id="f5506-116">2</span><span class="sxs-lookup"><span data-stu-id="f5506-116">2</span></span>|  
    |<span data-ttu-id="f5506-117">[錯誤]</span><span class="sxs-lookup"><span data-stu-id="f5506-117">[ ERR ]</span></span>|<span data-ttu-id="f5506-118">錯誤</span><span class="sxs-lookup"><span data-stu-id="f5506-118">Error</span></span>|<span data-ttu-id="f5506-119">2</span><span class="sxs-lookup"><span data-stu-id="f5506-119">2</span></span>|  
  
-   <span data-ttu-id="f5506-120">**延遲認可 (MCF)**。</span><span class="sxs-lookup"><span data-stu-id="f5506-120">**Delayed acknowledgment (MCF)**.</span></span> <span data-ttu-id="f5506-121">此訊息存在只為了回溯相容性 HL7 版本 2.1。</span><span class="sxs-lookup"><span data-stu-id="f5506-121">This message exists only for backward compatibility with HL7 Version 2.1.</span></span> <span data-ttu-id="f5506-122">您可以使用它做為建立泛型表單的非同步應用程式層級的通知，mom 連接器架構訊息的通訊協定的一部分。</span><span class="sxs-lookup"><span data-stu-id="f5506-122">You use it as part of the protocol that creates a generic form of an asynchronous application level acknowledgment, the MCF message.</span></span> <span data-ttu-id="f5506-123">下表列出 mom 連接器架構訊息結構。</span><span class="sxs-lookup"><span data-stu-id="f5506-123">The following table lists the MCF message structure.</span></span>  
  
    |<span data-ttu-id="f5506-124">Mom 連接器架構 ^ 變化 ^ 通知</span><span class="sxs-lookup"><span data-stu-id="f5506-124">MCF^varies^ACK</span></span>|<span data-ttu-id="f5506-125">延遲的認可</span><span class="sxs-lookup"><span data-stu-id="f5506-125">Delayed Acknowledgment</span></span>|<span data-ttu-id="f5506-126">章節</span><span class="sxs-lookup"><span data-stu-id="f5506-126">Chapter</span></span>|  
    |--------------------|----------------------------|-------------|  
    |<span data-ttu-id="f5506-127">MSH</span><span class="sxs-lookup"><span data-stu-id="f5506-127">MSH</span></span>|<span data-ttu-id="f5506-128">訊息標頭</span><span class="sxs-lookup"><span data-stu-id="f5506-128">Message Header</span></span>|<span data-ttu-id="f5506-129">2</span><span class="sxs-lookup"><span data-stu-id="f5506-129">2</span></span>|  
    |<span data-ttu-id="f5506-130">MSA</span><span class="sxs-lookup"><span data-stu-id="f5506-130">MSA</span></span>|<span data-ttu-id="f5506-131">通知訊息</span><span class="sxs-lookup"><span data-stu-id="f5506-131">Message Acknowledgment</span></span>|<span data-ttu-id="f5506-132">2</span><span class="sxs-lookup"><span data-stu-id="f5506-132">2</span></span>|  
    |<span data-ttu-id="f5506-133">[錯誤]</span><span class="sxs-lookup"><span data-stu-id="f5506-133">[ ERR ]</span></span>|<span data-ttu-id="f5506-134">錯誤</span><span class="sxs-lookup"><span data-stu-id="f5506-134">Error</span></span>|<span data-ttu-id="f5506-135">2</span><span class="sxs-lookup"><span data-stu-id="f5506-135">2</span></span>|  
  
 <span data-ttu-id="f5506-136">認可訊息有 MSH9 欄位設定為**ACK ^\<***觸發程序事件***> ^ ACK**或**MCF ^\<** *觸發程序事件***> ^ ACK**。</span><span class="sxs-lookup"><span data-stu-id="f5506-136">Acknowledgment messages have the MSH9 field set as either **ACK^\<***trigger event***>^ACK** or **MCF^\<***trigger event***>^ACK**.</span></span> <span data-ttu-id="f5506-137">如此一來，第 1 個元件 MSH9 就足以判斷通知結構描述。</span><span class="sxs-lookup"><span data-stu-id="f5506-137">As a result, the first component of MSH9 is sufficient to determine the ACK schema.</span></span> <span data-ttu-id="f5506-138">文件名稱[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 管線會使用一定會包含 HL7 為命名空間。</span><span class="sxs-lookup"><span data-stu-id="f5506-138">The document name that the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) pipeline uses always contains HL7 as the namespace.</span></span> <span data-ttu-id="f5506-139">型別名稱是 MSH9_1 欄位中，這是通知或 mom 連接器架構的內容。</span><span class="sxs-lookup"><span data-stu-id="f5506-139">The type name is the contents of the MSH9_1 field, which is ACK or MCF.</span></span> <span data-ttu-id="f5506-140">如此一來，如上述範例所示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]管線會尋找名稱 HL7 結構描述。ACK 或 HL7。MCF MSH9_1 欄位的值而定。</span><span class="sxs-lookup"><span data-stu-id="f5506-140">As a result, as in the example above, the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pipeline looks for a schema with the names HL7.ACK or HL7.MCF, depending on the value of the MSH9_1 field.</span></span> <span data-ttu-id="f5506-141">針對訊息內文結構描述是相同的 2.X 版的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="f5506-141">The schema for the message body is the same for all 2.X version messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5506-142">在批次中 / 出通知案例中，通知標頭內容的批次如下所示：</span><span class="sxs-lookup"><span data-stu-id="f5506-142">In a batch in/batch out ACK scenario, the contents of the ACK header is as follows:</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f5506-143">設定 MSH1 2、 8 與 15 到您的使用者介面中的設定。</span><span class="sxs-lookup"><span data-stu-id="f5506-143"> sets MSH1, 2, 8 and 15 to what you configure in the user interface.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f5506-144">設定 MSH7 系統時間。</span><span class="sxs-lookup"><span data-stu-id="f5506-144"> sets MSH7 to the system time.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f5506-145">MSH9 所設的通知。</span><span class="sxs-lookup"><span data-stu-id="f5506-145"> sets MSH9 to ACK.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f5506-146">設定 MSH12 2.4 或 2.5。</span><span class="sxs-lookup"><span data-stu-id="f5506-146"> sets MSH12 to 2.4 or 2.5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5506-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5506-147">See Also</span></span>  
 <span data-ttu-id="f5506-148">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="f5506-148">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="f5506-149">[訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span><span class="sxs-lookup"><span data-stu-id="f5506-149">[Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span></span>  
 <span data-ttu-id="f5506-150">[設定傳送埠來接收通知](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md) </span><span class="sxs-lookup"><span data-stu-id="f5506-150">[Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md) </span></span>  
 [<span data-ttu-id="f5506-151">通知錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="f5506-151">Acknowledgment Error Conditions</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)