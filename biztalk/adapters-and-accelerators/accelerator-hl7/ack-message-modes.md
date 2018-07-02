---
title: ACK 訊息模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message modes, ACK messages
- messages, acknowledgements
- acknowledgements, message modes
- ACK message modes
ms.assetid: ab4a9470-dab2-46d4-8d0a-54dc12f2fa90
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 181617a41ba892a8ac04f2bf2154bbe78e8c892e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967849"
---
# <a name="ack-message-modes"></a><span data-ttu-id="c816b-102">ACK 訊息模式</span><span class="sxs-lookup"><span data-stu-id="c816b-102">ACK Message Modes</span></span>
<span data-ttu-id="c816b-103">針對通知 (ACK) 訊息，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 決定要用於填入您想要產生通知的電子郵件地址 和 MSH16 MSH15 欄位值與通知模式。</span><span class="sxs-lookup"><span data-stu-id="c816b-103">For acknowledgment (ACK) messages, Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) determines the acknowledgment mode and values to use for populating MSH15 and MSH16 fields of the ACK you want to generate.</span></span> <span data-ttu-id="c816b-104">這些值會出現在交易夥伴管理 (TPM) 組態。</span><span class="sxs-lookup"><span data-stu-id="c816b-104">These values are present in the Trading Partner Management (TPM) configuration.</span></span> <span data-ttu-id="c816b-105">下列是可能值為 ACK 模式：</span><span class="sxs-lookup"><span data-stu-id="c816b-105">The following values are possible for ACK mode:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c816b-106">在下列清單中，HL7 規格會強制項目 1 到 3，以及它們包含 MSH15 和 MSH16 值。</span><span class="sxs-lookup"><span data-stu-id="c816b-106">In the following list, the HL7 specification mandates items 1 through 3 and that they contain MSH15 and MSH16 values.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="c816b-107"> 定義項目 4，表示不產生通知。</span><span class="sxs-lookup"><span data-stu-id="c816b-107"> defines item 4 to signify that an acknowledgment should not be generated.</span></span>  
  
1. <span data-ttu-id="c816b-108">原始-一個通知之後驗證標頭和本文傳送。</span><span class="sxs-lookup"><span data-stu-id="c816b-108">Original - One ACK sent after validating the header and body.</span></span> <span data-ttu-id="c816b-109">此模式都會涉及結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="c816b-109">This mode involves schema validation.</span></span>  
  
2. <span data-ttu-id="c816b-110">增強式-傳送兩則通知訊息：</span><span class="sxs-lookup"><span data-stu-id="c816b-110">Enhanced - Two ACK messages sent:</span></span>  
  
   -   <span data-ttu-id="c816b-111">接受通知 – 接收端系統的標頭驗證之後傳送這種類型的通知。</span><span class="sxs-lookup"><span data-stu-id="c816b-111">Accept ACK – The receiving system sends this type of ACK after validation of the header.</span></span> <span data-ttu-id="c816b-112">此通知告知起始應用程式的訊息是認可到資料庫。</span><span class="sxs-lookup"><span data-stu-id="c816b-112">This ACK signals to the initiating application that the message is committed to the database.</span></span>  
  
   -   <span data-ttu-id="c816b-113">應用程式通知接收系統會傳送這種類型的通知之後完成的訊息驗證，包括標頭和主體。</span><span class="sxs-lookup"><span data-stu-id="c816b-113">Application ACK- The receiving system sends this type of ACK after complete message validation, including the header and the body.</span></span>  
  
3. <span data-ttu-id="c816b-114">延遲-傳送兩則通知訊息。</span><span class="sxs-lookup"><span data-stu-id="c816b-114">Deferred - Two ACK messages sent.</span></span>  
  
   - <span data-ttu-id="c816b-115">原始的模式： 接收端系統會在驗證標頭和本文之後，傳送這種類型的通知。</span><span class="sxs-lookup"><span data-stu-id="c816b-115">Original Mode: The receiving system sends this type of ACK after validation of the header and body.</span></span> <span data-ttu-id="c816b-116">此模式都會涉及結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="c816b-116">This mode involves schema validation.</span></span>  
  
   - <span data-ttu-id="c816b-117">延後模式： 特定業務應用程式會在處理它之後，確認訊息。</span><span class="sxs-lookup"><span data-stu-id="c816b-117">Deferred Mode: The line-of-business application acknowledges the message after processing it.</span></span> <span data-ttu-id="c816b-118">應用程式提供的延後的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，其處理為獨立的訊息，並將其傳遞到目的地。</span><span class="sxs-lookup"><span data-stu-id="c816b-118">The application delivers the deferred message to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], which process it as a stand-alone message and delivers it to the destination.</span></span>  
  
4. <span data-ttu-id="c816b-119">靜態-在成功或失敗傳送通知。</span><span class="sxs-lookup"><span data-stu-id="c816b-119">Static - An on success or on failure ACK sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c816b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c816b-120">See Also</span></span>  
 <span data-ttu-id="c816b-121">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="c816b-121">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="c816b-122">[程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span><span class="sxs-lookup"><span data-stu-id="c816b-122">[Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span></span>  
 <span data-ttu-id="c816b-123">[ACK 處理序模型](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md) </span><span class="sxs-lookup"><span data-stu-id="c816b-123">[ACK Process Model](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md) </span></span>  
 [<span data-ttu-id="c816b-124">靜態通知</span><span class="sxs-lookup"><span data-stu-id="c816b-124">Static Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/static-acknowledgments.md)