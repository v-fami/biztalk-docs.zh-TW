---
title: ACK 訊息結構描述型別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, ACK schemas
- acknowledgements, ACK schema types
- ACK messages
ms.assetid: da6981a0-a70a-481e-8db4-4a6851f205f1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a556155e364fe56b66f7938fd49036b47085aeac
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967464"
---
# <a name="ack-message-schema-types"></a><span data-ttu-id="0ca46-102">ACK 訊息結構描述類型</span><span class="sxs-lookup"><span data-stu-id="0ca46-102">ACK Message Schema Types</span></span>
<span data-ttu-id="0ca46-103">通知訊息結構描述有兩種形式：</span><span class="sxs-lookup"><span data-stu-id="0ca46-103">Acknowledgment message schemas come in two forms:</span></span>  

- <span data-ttu-id="0ca46-104">**一般通知 (ACK)**。</span><span class="sxs-lookup"><span data-stu-id="0ca46-104">**General acknowledgment (ACK)**.</span></span> <span data-ttu-id="0ca46-105">應用程式不會定義特殊的特定業務應用程式層級的通知訊息或發生錯誤，防止應用程式處理，您可以使用一般的通知 (ACK)。</span><span class="sxs-lookup"><span data-stu-id="0ca46-105">You can use a general acknowledgment (ACK) where the application does not define a special line-of-business application level acknowledgment message or where an error occurred that precludes application processing.</span></span> <span data-ttu-id="0ca46-106">您也可以使用它針對接受的層級的通知。</span><span class="sxs-lookup"><span data-stu-id="0ca46-106">You can also use it for accept level acknowledgments.</span></span> <span data-ttu-id="0ca46-107">下表列出的 ACK 訊息結構。</span><span class="sxs-lookup"><span data-stu-id="0ca46-107">The following table lists the ACK message structure.</span></span>  


  | <span data-ttu-id="0ca46-108">ACK ^ 而異 ^ 通知</span><span class="sxs-lookup"><span data-stu-id="0ca46-108">ACK^varies^ACK</span></span> | <span data-ttu-id="0ca46-109">一般通知</span><span class="sxs-lookup"><span data-stu-id="0ca46-109">General acknowledgment</span></span> | <span data-ttu-id="0ca46-110">章節</span><span class="sxs-lookup"><span data-stu-id="0ca46-110">Chapter</span></span> |
  |----------------|------------------------|---------|
  |      <span data-ttu-id="0ca46-111">MSH</span><span class="sxs-lookup"><span data-stu-id="0ca46-111">MSH</span></span>       |     <span data-ttu-id="0ca46-112">訊息標頭</span><span class="sxs-lookup"><span data-stu-id="0ca46-112">Message Header</span></span>     |    <span data-ttu-id="0ca46-113">2</span><span class="sxs-lookup"><span data-stu-id="0ca46-113">2</span></span>    |
  |      <span data-ttu-id="0ca46-114">MSA</span><span class="sxs-lookup"><span data-stu-id="0ca46-114">MSA</span></span>       | <span data-ttu-id="0ca46-115">訊息通知</span><span class="sxs-lookup"><span data-stu-id="0ca46-115">Message Acknowledgment</span></span> |    <span data-ttu-id="0ca46-116">2</span><span class="sxs-lookup"><span data-stu-id="0ca46-116">2</span></span>    |
  |    <span data-ttu-id="0ca46-117">[錯誤]</span><span class="sxs-lookup"><span data-stu-id="0ca46-117">[ ERR ]</span></span>     |         <span data-ttu-id="0ca46-118">錯誤</span><span class="sxs-lookup"><span data-stu-id="0ca46-118">Error</span></span>          |    <span data-ttu-id="0ca46-119">2</span><span class="sxs-lookup"><span data-stu-id="0ca46-119">2</span></span>    |


- <span data-ttu-id="0ca46-120">**延遲的通知 (MCF)**。</span><span class="sxs-lookup"><span data-stu-id="0ca46-120">**Delayed acknowledgment (MCF)**.</span></span> <span data-ttu-id="0ca46-121">此訊息僅存在於 HL7 2.1 版的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="0ca46-121">This message exists only for backward compatibility with HL7 Version 2.1.</span></span> <span data-ttu-id="0ca46-122">您可以使用它做為建立一般表單的非同步應用程式層級的通知，mom 連接器架構訊息通訊協定的一部分。</span><span class="sxs-lookup"><span data-stu-id="0ca46-122">You use it as part of the protocol that creates a generic form of an asynchronous application level acknowledgment, the MCF message.</span></span> <span data-ttu-id="0ca46-123">下表列出 MCF 訊息結構。</span><span class="sxs-lookup"><span data-stu-id="0ca46-123">The following table lists the MCF message structure.</span></span>  

  |<span data-ttu-id="0ca46-124">Mom 連接器架構 ^ 而異 ^ 通知</span><span class="sxs-lookup"><span data-stu-id="0ca46-124">MCF^varies^ACK</span></span>|<span data-ttu-id="0ca46-125">延遲的通知</span><span class="sxs-lookup"><span data-stu-id="0ca46-125">Delayed Acknowledgment</span></span>|<span data-ttu-id="0ca46-126">章節</span><span class="sxs-lookup"><span data-stu-id="0ca46-126">Chapter</span></span>|  
  |--------------------|----------------------------|-------------|  
  |<span data-ttu-id="0ca46-127">MSH</span><span class="sxs-lookup"><span data-stu-id="0ca46-127">MSH</span></span>|<span data-ttu-id="0ca46-128">訊息標頭</span><span class="sxs-lookup"><span data-stu-id="0ca46-128">Message Header</span></span>|<span data-ttu-id="0ca46-129">2</span><span class="sxs-lookup"><span data-stu-id="0ca46-129">2</span></span>|  
  |<span data-ttu-id="0ca46-130">MSA</span><span class="sxs-lookup"><span data-stu-id="0ca46-130">MSA</span></span>|<span data-ttu-id="0ca46-131">訊息通知</span><span class="sxs-lookup"><span data-stu-id="0ca46-131">Message Acknowledgment</span></span>|<span data-ttu-id="0ca46-132">2</span><span class="sxs-lookup"><span data-stu-id="0ca46-132">2</span></span>|  
  |<span data-ttu-id="0ca46-133">[錯誤]</span><span class="sxs-lookup"><span data-stu-id="0ca46-133">[ ERR ]</span></span>|<span data-ttu-id="0ca46-134">錯誤</span><span class="sxs-lookup"><span data-stu-id="0ca46-134">Error</span></span>|<span data-ttu-id="0ca46-135">2</span><span class="sxs-lookup"><span data-stu-id="0ca46-135">2</span></span>|  

  <span data-ttu-id="0ca46-136">認可訊息有 MSH9 欄位設定為**ACK ^\<**<em>觸發程序事件</em>**\>^ ACK**或**MCF ^\<** <em>觸發程序事件</em>**\>^ ACK**。</span><span class="sxs-lookup"><span data-stu-id="0ca46-136">Acknowledgment messages have the MSH9 field set as either **ACK^\<**<em>trigger event</em>**\>^ACK** or **MCF^\<**<em>trigger event</em>**\>^ACK**.</span></span> <span data-ttu-id="0ca46-137">如此一來，MSH9 的第一個部分就足以判斷通知的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0ca46-137">As a result, the first component of MSH9 is sufficient to determine the ACK schema.</span></span> <span data-ttu-id="0ca46-138">Microsoft BizTalk Accelerator for HL7 文件命名 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 管線會使用一定會包含 HL7 為命名空間。</span><span class="sxs-lookup"><span data-stu-id="0ca46-138">The document name that the Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) pipeline uses always contains HL7 as the namespace.</span></span> <span data-ttu-id="0ca46-139">型別名稱是 MSH9_1 欄位中，因為這是通知或 mom 連接器架構的內容。</span><span class="sxs-lookup"><span data-stu-id="0ca46-139">The type name is the contents of the MSH9_1 field, which is ACK or MCF.</span></span> <span data-ttu-id="0ca46-140">如此一來，如上述範例所示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]管線會尋找名稱 HL7 結構描述。ACK 或 HL7。MCF MSH9_1 欄位的值而定。</span><span class="sxs-lookup"><span data-stu-id="0ca46-140">As a result, as in the example above, the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pipeline looks for a schema with the names HL7.ACK or HL7.MCF, depending on the value of the MSH9_1 field.</span></span> <span data-ttu-id="0ca46-141">訊息內文結構描述是相同的 2.X 版的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="0ca46-141">The schema for the message body is the same for all 2.X version messages.</span></span>  

> [!NOTE]
>  <span data-ttu-id="0ca46-142">在批次中 / 批次出通知案例中，通知標頭的內容如下所示：</span><span class="sxs-lookup"><span data-stu-id="0ca46-142">In a batch in/batch out ACK scenario, the contents of the ACK header is as follows:</span></span>  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="0ca46-143"> 設定 MSH1、 2、 8 和 15 到您的使用者介面中的設定。</span><span class="sxs-lookup"><span data-stu-id="0ca46-143"> sets MSH1, 2, 8 and 15 to what you configure in the user interface.</span></span>  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="0ca46-144"> 將 MSH7 設定系統時間。</span><span class="sxs-lookup"><span data-stu-id="0ca46-144"> sets MSH7 to the system time.</span></span>  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="0ca46-145"> MSH9 設通知。</span><span class="sxs-lookup"><span data-stu-id="0ca46-145"> sets MSH9 to ACK.</span></span>  

- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="0ca46-146"> 設定 MSH12 2.4 或 2.5。</span><span class="sxs-lookup"><span data-stu-id="0ca46-146"> sets MSH12 to 2.4 or 2.5.</span></span>  

## <a name="see-also"></a><span data-ttu-id="0ca46-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ca46-147">See Also</span></span>  
 <span data-ttu-id="0ca46-148">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="0ca46-148">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="0ca46-149">[訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span><span class="sxs-lookup"><span data-stu-id="0ca46-149">[Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span></span>  
 <span data-ttu-id="0ca46-150">[設定傳送埠來接收 Ack](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md) </span><span class="sxs-lookup"><span data-stu-id="0ca46-150">[Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md) </span></span>  
 [<span data-ttu-id="0ca46-151">通知錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="0ca46-151">Acknowledgment Error Conditions</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)