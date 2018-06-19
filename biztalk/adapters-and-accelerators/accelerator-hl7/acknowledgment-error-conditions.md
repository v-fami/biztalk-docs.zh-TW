---
title: 通知錯誤情況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, errors
- errors, acknowledgements
ms.assetid: 605c7fa0-2365-4cb6-92fb-6df570905ca8
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15b481f4cdb60822841021f7f708a6caea021b8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204582"
---
# <a name="acknowledgment-error-conditions"></a><span data-ttu-id="fcb5c-102">通知錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="fcb5c-102">Acknowledgment Error Conditions</span></span>
<span data-ttu-id="fcb5c-103">在下列情況會導致嚴重的錯誤條件時[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會處理通知 (ACK) 訊息：</span><span class="sxs-lookup"><span data-stu-id="fcb5c-103">The following conditions will result in a fatal error condition when [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) is processing acknowledgment (ACK) messages:</span></span>  
  
-   <span data-ttu-id="fcb5c-104">遺漏 MSH9 中必要的欄位</span><span class="sxs-lookup"><span data-stu-id="fcb5c-104">Missing required fields in MSH9</span></span>  
  
-   <span data-ttu-id="fcb5c-105">遺漏 MSH12 中必要的欄位</span><span class="sxs-lookup"><span data-stu-id="fcb5c-105">Missing required fields in MSH12</span></span>  
  
 <span data-ttu-id="fcb5c-106">在下列情況會導致非嚴重錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="fcb5c-106">The following conditions result in a non-fatal error condition.</span></span> <span data-ttu-id="fcb5c-107">在此情況下，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生通知，但也會暫止的通知：</span><span class="sxs-lookup"><span data-stu-id="fcb5c-107">In this situation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates the ACK, but also suspends the ACK:</span></span>  
  
-   <span data-ttu-id="fcb5c-108">遺失必要的欄位中 MSH11</span><span class="sxs-lookup"><span data-stu-id="fcb5c-108">Missing a required field in MSH11</span></span>  
  
-   <span data-ttu-id="fcb5c-109">遺漏 MSH10 值</span><span class="sxs-lookup"><span data-stu-id="fcb5c-109">Missing a MSH10 value</span></span>  
  
-   <span data-ttu-id="fcb5c-110">列舉型別為選擇性欄位標頭中的的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fcb5c-110">Enumeration type errors for optional fields in the header.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcb5c-111">MSH 15 AL 或增，設定標頭中找到的列舉型別錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會產生狀態為認可通知**MSA_1 = CR**。</span><span class="sxs-lookup"><span data-stu-id="fcb5c-111">For enumeration type errors found in the header when MSH 15 is set to AL or ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates a commit ACK with the status **MSA_1=CR**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb5c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcb5c-112">See Also</span></span>  
 <span data-ttu-id="fcb5c-113">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="fcb5c-113">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="fcb5c-114">[ACK 訊息結構描述類型](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span><span class="sxs-lookup"><span data-stu-id="fcb5c-114">[ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span></span>  
 <span data-ttu-id="fcb5c-115">[訊息通知區段](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span><span class="sxs-lookup"><span data-stu-id="fcb5c-115">[Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span></span>  
 [<span data-ttu-id="fcb5c-116">設定傳送埠來接收通知</span><span class="sxs-lookup"><span data-stu-id="fcb5c-116">Setting Up a Send Port for Receiving ACKs</span></span>](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)