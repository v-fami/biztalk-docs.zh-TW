---
title: ACK 訊息模式 |Microsoft 文件
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
ms.openlocfilehash: 122f0851005c7d8abba6c1739ae86a1d65d89625
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204398"
---
# <a name="ack-message-modes"></a><span data-ttu-id="b910e-102">ACK 訊息模式</span><span class="sxs-lookup"><span data-stu-id="b910e-102">ACK Message Modes</span></span>
<span data-ttu-id="b910e-103">通知 (ACK) 訊息[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會決定通知模式以及要使用用來填入您想要產生的 ACK MSH15 和 MSH16 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="b910e-103">For acknowledgment (ACK) messages, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) determines the acknowledgment mode and values to use for populating MSH15 and MSH16 fields of the ACK you want to generate.</span></span> <span data-ttu-id="b910e-104">這些值會出現在交易夥伴管理 (TPM) 組態。</span><span class="sxs-lookup"><span data-stu-id="b910e-104">These values are present in the Trading Partner Management (TPM) configuration.</span></span> <span data-ttu-id="b910e-105">通知模式可能會有下列值：</span><span class="sxs-lookup"><span data-stu-id="b910e-105">The following values are possible for ACK mode:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b910e-106">在下列清單中，HL7 規格會強制項目 1 至 3，且包含 MSH15 和 MSH16 值。</span><span class="sxs-lookup"><span data-stu-id="b910e-106">In the following list, the HL7 specification mandates items 1 through 3 and that they contain MSH15 and MSH16 values.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="b910e-107">定義項目 4，表示不應該產生通知。</span><span class="sxs-lookup"><span data-stu-id="b910e-107"> defines item 4 to signify that an acknowledgment should not be generated.</span></span>  
  
1.  <span data-ttu-id="b910e-108">原始-一個通知之後驗證標頭和本文傳送。</span><span class="sxs-lookup"><span data-stu-id="b910e-108">Original - One ACK sent after validating the header and body.</span></span> <span data-ttu-id="b910e-109">此模式中包含結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="b910e-109">This mode involves schema validation.</span></span>  
  
2.  <span data-ttu-id="b910e-110">增強的兩個傳送的通知訊息：</span><span class="sxs-lookup"><span data-stu-id="b910e-110">Enhanced - Two ACK messages sent:</span></span>  
  
    -   <span data-ttu-id="b910e-111">接受通知 – 接收端系統的標頭驗證之後傳送這種類型的通知。</span><span class="sxs-lookup"><span data-stu-id="b910e-111">Accept ACK – The receiving system sends this type of ACK after validation of the header.</span></span> <span data-ttu-id="b910e-112">這 ACK 通知起始應用程式訊息是向資料庫認可。</span><span class="sxs-lookup"><span data-stu-id="b910e-112">This ACK signals to the initiating application that the message is committed to the database.</span></span>  
  
    -   <span data-ttu-id="b910e-113">應用程式通知接收系統會傳送這種類型的通知之後完成的訊息驗證，包括標頭和主體。</span><span class="sxs-lookup"><span data-stu-id="b910e-113">Application ACK- The receiving system sends this type of ACK after complete message validation, including the header and the body.</span></span>  
  
3.  <span data-ttu-id="b910e-114">延後的兩個傳送的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b910e-114">Deferred - Two ACK messages sent.</span></span>  
  
    -   <span data-ttu-id="b910e-115">原始模式： 接收端系統的標頭和主體的驗證之後傳送這種類型的通知。</span><span class="sxs-lookup"><span data-stu-id="b910e-115">Original Mode: The receiving system sends this type of ACK after validation of the header and body.</span></span> <span data-ttu-id="b910e-116">此模式中包含結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="b910e-116">This mode involves schema validation.</span></span>  
  
    -   <span data-ttu-id="b910e-117">延後的模式： 特定業務應用程式確認訊息之後加以處理。</span><span class="sxs-lookup"><span data-stu-id="b910e-117">Deferred Mode: The line-of-business application acknowledges the message after processing it.</span></span> <span data-ttu-id="b910e-118">應用程式能夠提供延後的訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，其處理做為獨立的訊息，並將其傳遞到目的地。</span><span class="sxs-lookup"><span data-stu-id="b910e-118">The application delivers the deferred message to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], which process it as a stand-alone message and delivers it to the destination.</span></span>  
  
4.  <span data-ttu-id="b910e-119">靜態-在成功或失敗認可。</span><span class="sxs-lookup"><span data-stu-id="b910e-119">Static - An on success or on failure ACK sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b910e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b910e-120">See Also</span></span>  
 <span data-ttu-id="b910e-121">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="b910e-121">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="b910e-122">[程式設計手冊](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span><span class="sxs-lookup"><span data-stu-id="b910e-122">[Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span></span>  
 <span data-ttu-id="b910e-123">[ACK 處理序模型](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md) </span><span class="sxs-lookup"><span data-stu-id="b910e-123">[ACK Process Model](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md) </span></span>  
 [<span data-ttu-id="b910e-124">靜態通知</span><span class="sxs-lookup"><span data-stu-id="b910e-124">Static Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/static-acknowledgments.md)