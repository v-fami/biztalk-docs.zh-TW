---
title: "訊息修復和新送出 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages
- resubmitting messages
- errors, messages
- messages, errors
- messages, resubmitting
ms.assetid: 5bc6bfa2-8210-4dd3-89bb-5455e294ca92
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bc15351848fe68d6ef54c31fc6d58c075bb1c58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-and-new-submission"></a><span data-ttu-id="6f6cd-102">Message Repair 和 New Submission</span><span class="sxs-lookup"><span data-stu-id="6f6cd-102">Message Repair and New Submission</span></span>
<span data-ttu-id="6f6cd-103">訊息修復和 New Submission 功能[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]可讓您修復 MT 與 MX 驗證失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-103">The Message Repair and New Submission feature of [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides a way for you to repair MT and MX messages that fail validation.</span></span> <span data-ttu-id="6f6cd-104">使用 MRSR SharePoint 網站 （由使用者部署），您可以看到訊息驗證的失敗。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-104">Using the MRSR SharePoint site (deployed by user), you can see how the message failed validation.</span></span> <span data-ttu-id="6f6cd-105">您可以從 MRSR 網站，來開啟 InfoPath 表單，可讓您識別錯誤，修復該郵件，並提交以進行重新處理訊息。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-105">From MRSR site, you can open the message in an InfoPath form that enables you to identify the error, repair the message, and submit it for reprocessing.</span></span>  
  
 <span data-ttu-id="6f6cd-106">Message Repair 和 New Submission 支援以角色為基礎的訊息修復。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-106">Message Repair and New Submission supports role-based message repair.</span></span> <span data-ttu-id="6f6cd-107">完整的修復工作流程包含修復、 驗證和核准。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-107">A full repair workflow includes repair, verification, and approval.</span></span> <span data-ttu-id="6f6cd-108">修復工作流程是一個部門中定義的工作流程角色 （或階段） 及設定每個角色 A4SWIFT 使用者相關聯。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-108">A repair workflow is associated with a department that defines the roles (or stages) of the workflow and configures an A4SWIFT user for each role.</span></span> <span data-ttu-id="6f6cd-109">每個修復角色都有個別的 MRSR 站台檢視，為角色量身訂做。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-109">Each repair role has a separate MRSR site view tailored to the role.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6f6cd-110">執行驗證，以及使用的認證，以確保安全的程序執行角色簽署訊息，每個 A4SWIFT 使用者。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-110"> performs validation, and each A4SWIFT user performing a role signs the message, using a certificate, to ensure a secure process.</span></span>  
  
 <span data-ttu-id="6f6cd-111">除了訊息修復 A4SWIFT 可讓您提交新訊息，使用增強[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-111">In addition to message repair, A4SWIFT enables you to submit a new message using an enhanced [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form.</span></span> <span data-ttu-id="6f6cd-112">第四個 A4SWIFT 使用者，建立者，執行此函式。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-112">A fourth A4SWIFT user, a creator, performs this function.</span></span> <span data-ttu-id="6f6cd-113">程序也會執行驗證，並可包含修復、 驗證和核准的角色，以確保成功送出。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-113">The process also performs validation, and can involve repair, verification, and approval roles to ensure successful submission.</span></span> <span data-ttu-id="6f6cd-114">A4SWIFT 處理新訊息提交到[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成一樣，它會處理已修復的訊息。</span><span class="sxs-lookup"><span data-stu-id="6f6cd-114">A4SWIFT handles new message submission through an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form the same way that it handles a repaired message.</span></span>  
  
 <span data-ttu-id="6f6cd-115">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="6f6cd-115">This section contains:</span></span>  
  
-   [<span data-ttu-id="6f6cd-116">訊息修復程序</span><span class="sxs-lookup"><span data-stu-id="6f6cd-116">Message Repair Process</span></span>](../../adapters-and-accelerators/accelerator-swift/message-repair-process.md)  
  
-   [<span data-ttu-id="6f6cd-117">Message Repair 和 New Submission 建立部門和角色</span><span class="sxs-lookup"><span data-stu-id="6f6cd-117">Creating Departments and Roles for Message Repair and New Submission</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="6f6cd-118">若要修復的訊息或提交新訊息使用 InfoPath 表單</span><span class="sxs-lookup"><span data-stu-id="6f6cd-118">Using an InfoPath Form to Repair a Message or Submit a New Message</span></span>](../../adapters-and-accelerators/accelerator-swift/using-an-infopath-form-to-repair-a-message-or-submit-a-new-message.md)  
  
-   [<span data-ttu-id="6f6cd-119">在 訊息修復和新送出的特殊處理</span><span class="sxs-lookup"><span data-stu-id="6f6cd-119">Special Processing in Message Repair and New Submission</span></span>](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="6f6cd-120">修復未剖析的訊息</span><span class="sxs-lookup"><span data-stu-id="6f6cd-120">Repairing Unparsed Messages</span></span>](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)  
  
-   [<span data-ttu-id="6f6cd-121">訊息修復和新送出服務處理</span><span class="sxs-lookup"><span data-stu-id="6f6cd-121">Message Repair and New Submission Service Processing</span></span>](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-service-processing.md)