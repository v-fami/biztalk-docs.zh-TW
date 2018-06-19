---
title: 訊息通知區段 |Microsoft 文件
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
ms.openlocfilehash: 9547b6d8ddf3013facd94930b5d91ec42db0e5d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204934"
---
# <a name="message-acknowledgment-segment"></a><span data-ttu-id="04547-102">訊息通知區段</span><span class="sxs-lookup"><span data-stu-id="04547-102">Message Acknowledgment Segment</span></span>
<span data-ttu-id="04547-103">通知 (ACK) 訊息的訊息通知 (MSA) 區段會識別哪些類型的通知系統傳送，並指出哪些訊息認可通知。</span><span class="sxs-lookup"><span data-stu-id="04547-103">The Message Acknowledgment (MSA) segment of an acknowledgment (ACK) message identifies what type of acknowledgment the system is sending, and indicates what message the ACK is acknowledging.</span></span> <span data-ttu-id="04547-104">它包含兩個必要區段： 認可程式碼和訊息的控制項識別碼。</span><span class="sxs-lookup"><span data-stu-id="04547-104">It consists of two required segments: an acknowledgment code and a message control ID.</span></span>  
  
## <a name="acknowledgment-code-msa1"></a><span data-ttu-id="04547-105">通知程式碼： MSA1</span><span class="sxs-lookup"><span data-stu-id="04547-105">Acknowledgment Code: MSA1</span></span>  
 <span data-ttu-id="04547-106">下表列出可用的 MSA1 欄位值，指出訊息接收的結果。</span><span class="sxs-lookup"><span data-stu-id="04547-106">The following table lists the available MSA1 field values indicating the result of the message receiving.</span></span>  
  
|<span data-ttu-id="04547-107">值</span><span class="sxs-lookup"><span data-stu-id="04547-107">Value</span></span>|<span data-ttu-id="04547-108">意義</span><span class="sxs-lookup"><span data-stu-id="04547-108">Meaning</span></span>|<span data-ttu-id="04547-109">Description</span><span class="sxs-lookup"><span data-stu-id="04547-109">Description</span></span>|  
|-----------|-------------|-----------------|  
|<span data-ttu-id="04547-110">AA</span><span class="sxs-lookup"><span data-stu-id="04547-110">AA</span></span>|<span data-ttu-id="04547-111">應用程式通知</span><span class="sxs-lookup"><span data-stu-id="04547-111">Application Acknowledgment</span></span>|<span data-ttu-id="04547-112">系統已收到訊息並處理沒有解決問題。</span><span class="sxs-lookup"><span data-stu-id="04547-112">The system has received the message and processed it with no problem.</span></span>|  
|<span data-ttu-id="04547-113">AE</span><span class="sxs-lookup"><span data-stu-id="04547-113">AE</span></span>|<span data-ttu-id="04547-114">應用程式錯誤</span><span class="sxs-lookup"><span data-stu-id="04547-114">Application Error</span></span>|<span data-ttu-id="04547-115">此訊息或其結構與相關的處理問題發生在接收應用程式。</span><span class="sxs-lookup"><span data-stu-id="04547-115">A processing problem related to the message or its structure occurred at the receiving application.</span></span> <span data-ttu-id="04547-116">傳送系統應該診斷並更正問題，再嘗試重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="04547-116">The sending system should diagnose and correct the problem before attempting to resend the message.</span></span>|  
|<span data-ttu-id="04547-117">AR</span><span class="sxs-lookup"><span data-stu-id="04547-117">AR</span></span>|<span data-ttu-id="04547-118">應用程式的拒絕</span><span class="sxs-lookup"><span data-stu-id="04547-118">Application Reject</span></span>|<span data-ttu-id="04547-119">問題發生在接收位置相關 MSH9 中的值 （訊息類型），MSH11 （處理識別碼），或 MSH12 （版本識別碼），在此情況下傳送系統應該診斷並更正問題後再重新傳送訊息。或在接收端系統的相關訊息或它的結構，在其中傳送系統案例應重新傳送訊息適當的時間，而不需要變更至訊息後發生的問題。</span><span class="sxs-lookup"><span data-stu-id="04547-119">Either a problem occurred at the receiving location related to the value in MSH9 (message type), MSH11 (processing ID), or MSH12 (version ID), in which case the sending system should diagnose and correct the problem before resending the message; or a problem occurred at the receiving system that was unrelated to the message or its structure, in which case the sending system should resend the message after an appropriate period, without change to the message.</span></span>|  
  
## <a name="message-control-id-msa2"></a><span data-ttu-id="04547-120">訊息控制項 ID (MSA2)</span><span class="sxs-lookup"><span data-stu-id="04547-120">Message Control ID (MSA2)</span></span>  
 <span data-ttu-id="04547-121">MSA2 欄位識別認可通知訊息。</span><span class="sxs-lookup"><span data-stu-id="04547-121">The MSA2 field identifies the message that the ACK is acknowledging.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="04547-122">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 產生認可模式為基礎的 MSA2 中的值。</span><span class="sxs-lookup"><span data-stu-id="04547-122"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) generates the value in MSA2 based upon the acknowledgment mode.</span></span> <span data-ttu-id="04547-123">這個值會啟用傳送和接收應用程式，讓訊息維持與處理通知。</span><span class="sxs-lookup"><span data-stu-id="04547-123">This value enables the sending and receiving applications to keep the message and the acknowledgment synchronized.</span></span> <span data-ttu-id="04547-124">下表列出可用 MSA2 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="04547-124">The following table lists the available values for the MSA2 field.</span></span>  
  
|<span data-ttu-id="04547-125">認可模式</span><span class="sxs-lookup"><span data-stu-id="04547-125">Acknowledgment Mode</span></span>|<span data-ttu-id="04547-126">MSA2 中的值</span><span class="sxs-lookup"><span data-stu-id="04547-126">Value in MSA2</span></span>|  
|-------------------------|-------------------|  
|<span data-ttu-id="04547-127">原始模式</span><span class="sxs-lookup"><span data-stu-id="04547-127">Original mode</span></span>|<span data-ttu-id="04547-128">MSH10 中的值已轉置的值 （訊息控制項 ID） 的原始訊息欄位</span><span class="sxs-lookup"><span data-stu-id="04547-128">A transposed value of the value in the MSH10 (message control ID) field of the original message</span></span>|  
|<span data-ttu-id="04547-129">增強的模式： 認可通知</span><span class="sxs-lookup"><span data-stu-id="04547-129">Enhanced Mode: Commit Acknowledgment</span></span>|<span data-ttu-id="04547-130">MSH10 中的值已轉置的值 （訊息控制項 ID） 的原始訊息欄位</span><span class="sxs-lookup"><span data-stu-id="04547-130">A transposed value of the value in the MSH10 (message control ID) field of the original message</span></span>|  
|<span data-ttu-id="04547-131">增強的模式： 應用程式通知</span><span class="sxs-lookup"><span data-stu-id="04547-131">Enhanced Mode: Application Acknowledgment</span></span>|<span data-ttu-id="04547-132">所產生的 GUID[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通知</span><span class="sxs-lookup"><span data-stu-id="04547-132">A GUID generated by [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] for the acknowledgment</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04547-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04547-133">See Also</span></span>  
 <span data-ttu-id="04547-134">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="04547-134">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="04547-135">[ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span><span class="sxs-lookup"><span data-stu-id="04547-135">[ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span></span>  
 <span data-ttu-id="04547-136">[設定傳送埠來接收通知](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md) </span><span class="sxs-lookup"><span data-stu-id="04547-136">[Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md) </span></span>  
 [<span data-ttu-id="04547-137">通知錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="04547-137">Acknowledgment Error Conditions</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)