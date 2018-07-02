---
title: 訊息通知區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- segments, acknowledgements
- acknowledgements, segments
ms.assetid: 6f2b9f6f-a328-4a0f-9e7d-edba32cc045a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8f771968e6d7c7f58ccd8d3e68b43aac0eb64e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968495"
---
# <a name="message-acknowledgment-segment"></a><span data-ttu-id="a7755-102">訊息通知區段</span><span class="sxs-lookup"><span data-stu-id="a7755-102">Message Acknowledgment Segment</span></span>
<span data-ttu-id="a7755-103">通知 (ACK) 訊息的訊息通知 」 (MSA) 區段識別何種系統傳送，並指出哪些訊息通知認可通知。</span><span class="sxs-lookup"><span data-stu-id="a7755-103">The Message Acknowledgment (MSA) segment of an acknowledgment (ACK) message identifies what type of acknowledgment the system is sending, and indicates what message the ACK is acknowledging.</span></span> <span data-ttu-id="a7755-104">它包含兩個必要區段： 認可程式碼和訊息的控制項識別碼。</span><span class="sxs-lookup"><span data-stu-id="a7755-104">It consists of two required segments: an acknowledgment code and a message control ID.</span></span>  

## <a name="acknowledgment-code-msa1"></a><span data-ttu-id="a7755-105">通知程式碼： MSA1</span><span class="sxs-lookup"><span data-stu-id="a7755-105">Acknowledgment Code: MSA1</span></span>  
 <span data-ttu-id="a7755-106">下表列出可用的 MSA1 欄位值，指出訊息接收的結果。</span><span class="sxs-lookup"><span data-stu-id="a7755-106">The following table lists the available MSA1 field values indicating the result of the message receiving.</span></span>  

|<span data-ttu-id="a7755-107">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="a7755-107">Value</span></span>|<span data-ttu-id="a7755-108">意義</span><span class="sxs-lookup"><span data-stu-id="a7755-108">Meaning</span></span>|<span data-ttu-id="a7755-109">描述</span><span class="sxs-lookup"><span data-stu-id="a7755-109">Description</span></span>|  
|-----------|-------------|-----------------|  
|<span data-ttu-id="a7755-110">AA</span><span class="sxs-lookup"><span data-stu-id="a7755-110">AA</span></span>|<span data-ttu-id="a7755-111">應用程式通知</span><span class="sxs-lookup"><span data-stu-id="a7755-111">Application Acknowledgment</span></span>|<span data-ttu-id="a7755-112">系統已收到訊息，並處理任何問題。</span><span class="sxs-lookup"><span data-stu-id="a7755-112">The system has received the message and processed it with no problem.</span></span>|  
|<span data-ttu-id="a7755-113">AE</span><span class="sxs-lookup"><span data-stu-id="a7755-113">AE</span></span>|<span data-ttu-id="a7755-114">應用程式錯誤</span><span class="sxs-lookup"><span data-stu-id="a7755-114">Application Error</span></span>|<span data-ttu-id="a7755-115">訊息或其結構與相關的處理問題發生在接收應用程式。</span><span class="sxs-lookup"><span data-stu-id="a7755-115">A processing problem related to the message or its structure occurred at the receiving application.</span></span> <span data-ttu-id="a7755-116">傳送的系統應該診斷並更正問題，然後再嘗試重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="a7755-116">The sending system should diagnose and correct the problem before attempting to resend the message.</span></span>|  
|<span data-ttu-id="a7755-117">AR</span><span class="sxs-lookup"><span data-stu-id="a7755-117">AR</span></span>|<span data-ttu-id="a7755-118">應用程式的拒絕</span><span class="sxs-lookup"><span data-stu-id="a7755-118">Application Reject</span></span>|<span data-ttu-id="a7755-119">問題發生在接收位置相關 MSH9 中的值 （訊息類型）、 MSH11 （處理識別碼），或 MSH12 （版本識別碼），在此情況下傳送的系統應該診斷並更正問題後再重新傳送訊息，或在已不相關的訊息或它的結構，在其中情況下，傳送端系統應重新傳送訊息後，不會變更訊息至接收端系統發生問題。</span><span class="sxs-lookup"><span data-stu-id="a7755-119">Either a problem occurred at the receiving location related to the value in MSH9 (message type), MSH11 (processing ID), or MSH12 (version ID), in which case the sending system should diagnose and correct the problem before resending the message; or a problem occurred at the receiving system that was unrelated to the message or its structure, in which case the sending system should resend the message after an appropriate period, without change to the message.</span></span>|  

## <a name="message-control-id-msa2"></a><span data-ttu-id="a7755-120">訊息的控制項 ID (MSA2)</span><span class="sxs-lookup"><span data-stu-id="a7755-120">Message Control ID (MSA2)</span></span>  
 <span data-ttu-id="a7755-121">MSA2 欄位識別認可通知訊息。</span><span class="sxs-lookup"><span data-stu-id="a7755-121">The MSA2 field identifies the message that the ACK is acknowledging.</span></span> <span data-ttu-id="a7755-122">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會產生在 MSA2 通知模式為基礎的值。</span><span class="sxs-lookup"><span data-stu-id="a7755-122">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) generates the value in MSA2 based upon the acknowledgment mode.</span></span> <span data-ttu-id="a7755-123">這個值會啟用傳送和接收應用程式，讓訊息維持和同步處理通知。</span><span class="sxs-lookup"><span data-stu-id="a7755-123">This value enables the sending and receiving applications to keep the message and the acknowledgment synchronized.</span></span> <span data-ttu-id="a7755-124">下表列出可用的值，以 MSA2 欄位。</span><span class="sxs-lookup"><span data-stu-id="a7755-124">The following table lists the available values for the MSA2 field.</span></span>  


|            <span data-ttu-id="a7755-125">通知模式</span><span class="sxs-lookup"><span data-stu-id="a7755-125">Acknowledgment Mode</span></span>            |                                                           <span data-ttu-id="a7755-126">MSA2 中的值</span><span class="sxs-lookup"><span data-stu-id="a7755-126">Value in MSA2</span></span>                                                            |
|-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
|               <span data-ttu-id="a7755-127">原始的模式</span><span class="sxs-lookup"><span data-stu-id="a7755-127">Original mode</span></span>               |                  <span data-ttu-id="a7755-128">已轉置 MSH10 中值的值 （訊息的控制項 ID），原始訊息的欄位</span><span class="sxs-lookup"><span data-stu-id="a7755-128">A transposed value of the value in the MSH10 (message control ID) field of the original message</span></span>                   |
|   <span data-ttu-id="a7755-129">增強的模式： 認可通知</span><span class="sxs-lookup"><span data-stu-id="a7755-129">Enhanced Mode: Commit Acknowledgment</span></span>    |                  <span data-ttu-id="a7755-130">已轉置 MSH10 中值的值 （訊息的控制項 ID），原始訊息的欄位</span><span class="sxs-lookup"><span data-stu-id="a7755-130">A transposed value of the value in the MSH10 (message control ID) field of the original message</span></span>                   |
| <span data-ttu-id="a7755-131">增強的模式： 應用程式通知</span><span class="sxs-lookup"><span data-stu-id="a7755-131">Enhanced Mode: Application Acknowledgment</span></span> | <span data-ttu-id="a7755-132">所產生的 GUID[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通知</span><span class="sxs-lookup"><span data-stu-id="a7755-132">A GUID generated by [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] for the acknowledgment</span></span> |

## <a name="see-also"></a><span data-ttu-id="a7755-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7755-133">See Also</span></span>  
 <span data-ttu-id="a7755-134">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="a7755-134">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="a7755-135">[ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span><span class="sxs-lookup"><span data-stu-id="a7755-135">[ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span></span>  
 <span data-ttu-id="a7755-136">[設定傳送埠來接收 Ack](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md) </span><span class="sxs-lookup"><span data-stu-id="a7755-136">[Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md) </span></span>  
 [<span data-ttu-id="a7755-137">通知錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="a7755-137">Acknowledgment Error Conditions</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)