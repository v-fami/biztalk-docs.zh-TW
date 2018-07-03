---
title: 修復訊息並提交新訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- repairing messages
- Message Repair and New Submission
- submitting, messages
- submitting, Message Repair and New Submission
- messages, Message Repair and New Submission
- messages, submitting
- Message Repair and New Submission. about Message Repair and New Submission
ms.assetid: 6abcce90-f611-422a-b3c8-e25f1e75b039
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 569ab44588c2bd89c3533af8cc765e58f743a229
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003311"
---
# <a name="repairing-messages-and-submitting-new-messages"></a><span data-ttu-id="18c7c-102">修復訊息並提交新訊息</span><span class="sxs-lookup"><span data-stu-id="18c7c-102">Repairing Messages and Submitting New Messages</span></span>
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="18c7c-103"> Message Repair 和 New Submission 可讓您修復 XML 或商務規則引擎的驗證失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="18c7c-103"> Message Repair and New Submission enables you to repair a message that has failed XML or Business Rules Engine validation.</span></span> <span data-ttu-id="18c7c-104">修復程序包含驗證和核准步驟，以確保精確度和訊息修復恰當。</span><span class="sxs-lookup"><span data-stu-id="18c7c-104">The repair process includes verification and approval steps that ensure the accuracy and appropriateness of the message repair.</span></span> <span data-ttu-id="18c7c-105">使用 Microsoft 來執行此程序[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] MRSR 站台內的表單。</span><span class="sxs-lookup"><span data-stu-id="18c7c-105">This process is performed using Microsoft [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms within MRSR site.</span></span>  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="18c7c-106"> 也可讓您提交新訊息，使用此程序。</span><span class="sxs-lookup"><span data-stu-id="18c7c-106"> also enables you to submit a new message using this process.</span></span> <span data-ttu-id="18c7c-107">建立者提交的訊息，而且工作流程可以包含 repairer、 驗證器，並執行相同的工作，如訊息修復所示的核准者。</span><span class="sxs-lookup"><span data-stu-id="18c7c-107">A creator submits the message, and the workflow can include a repairer, a verifier, and an approver performing the same tasks as in message repair.</span></span>  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="18c7c-108"> 藉由指派不同的使用者執行每項工作，可確保此程序的安全性。</span><span class="sxs-lookup"><span data-stu-id="18c7c-108"> ensures the security of this process by assigning different users to perform each task.</span></span> <span data-ttu-id="18c7c-109">您指派適當的修復、 確認，或核准每個這些使用者的角色和每個使用者必須使用特定的認證來執行工作。</span><span class="sxs-lookup"><span data-stu-id="18c7c-109">You assign the appropriate repair, verify, or approve role to each of these users, and each user must use a specific certificate to perform the task.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="18c7c-110"> 也支援部門的使用中處理訊息修復和提交訊息。</span><span class="sxs-lookup"><span data-stu-id="18c7c-110"> also supports the use of departments in processing repaired and submitted messages.</span></span> <span data-ttu-id="18c7c-111">每個部門牽涉到特定的工作流程的一組特定的訊息上執行的工作。</span><span class="sxs-lookup"><span data-stu-id="18c7c-111">Each department involves a specific workflow of tasks performed on a specific set of messages.</span></span> <span data-ttu-id="18c7c-112">在任何建立修復、 確認，或核准步驟，當您送出訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]呼叫 BRE 驗證，並確認使用者適當的部門的成員。</span><span class="sxs-lookup"><span data-stu-id="18c7c-112">In any of the create, repair, verify, or approve steps, when you submit the message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] calls BRE validation and verifies that the user is a member of the appropriate department.</span></span> <span data-ttu-id="18c7c-113">如需有關訊息 repair 和 new submission 的詳細資訊，請參閱 <<c0> [ 訊息修復和 New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md)。</span><span class="sxs-lookup"><span data-stu-id="18c7c-113">For more information about message repair and new submission, see [Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md).</span></span>  
  
 <span data-ttu-id="18c7c-114">如果您接收未剖析的訊息，Message Repair 和 New Submission 顯示訊息，並在失敗的描述，[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單，並可讓您列印訊息，或將它儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="18c7c-114">If you receive an unparsed message, Message Repair and New Submission displays the message and a description of the failure in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, and enables you to print the message or save it to a file.</span></span> <span data-ttu-id="18c7c-115">您可以修復，然後重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="18c7c-115">You can then repair and resubmit the message.</span></span> <span data-ttu-id="18c7c-116">不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不會呼叫 BRE 驗證或檢查在部門的成員資格，當您送出您修復未剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="18c7c-116">However, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not call BRE validation or check membership in a department when you submit an unparsed message that you have repaired.</span></span> <span data-ttu-id="18c7c-117">此外，重新提交未剖析的訊息未驗證或認可。</span><span class="sxs-lookup"><span data-stu-id="18c7c-117">In addition, a resubmitted unparsed message is not verified or approved.</span></span> <span data-ttu-id="18c7c-118">如需有關未剖析的訊息的詳細資訊，請參閱[修復未剖析的訊息](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="18c7c-118">For more information about unparsed messages, see [Repairing Unparsed Messages](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).</span></span>  
  
 <span data-ttu-id="18c7c-119">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="18c7c-119">This section contains:</span></span>  
  
-   [<span data-ttu-id="18c7c-120">修復訊息</span><span class="sxs-lookup"><span data-stu-id="18c7c-120">Repairing a Message</span></span>](../../adapters-and-accelerators/accelerator-swift/repairing-a-message.md)  
  
-   [<span data-ttu-id="18c7c-121">驗證訊息</span><span class="sxs-lookup"><span data-stu-id="18c7c-121">Verifying a Message</span></span>](../../adapters-and-accelerators/accelerator-swift/verifying-a-message.md)  
  
-   [<span data-ttu-id="18c7c-122">核准訊息</span><span class="sxs-lookup"><span data-stu-id="18c7c-122">Approving a Message</span></span>](../../adapters-and-accelerators/accelerator-swift/approving-a-message.md)  
  
-   [<span data-ttu-id="18c7c-123">處理未剖析的訊息</span><span class="sxs-lookup"><span data-stu-id="18c7c-123">Handling an Unparsed Message</span></span>](../../adapters-and-accelerators/accelerator-swift/handling-an-unparsed-message.md)  
  
-   [<span data-ttu-id="18c7c-124">建立和提交新的訊息</span><span class="sxs-lookup"><span data-stu-id="18c7c-124">Creating and Submitting a New Message</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md)  
  
-   [<span data-ttu-id="18c7c-125">建立新的訊息範本</span><span class="sxs-lookup"><span data-stu-id="18c7c-125">Creating a New Message Template</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-a-new-message-template.md)