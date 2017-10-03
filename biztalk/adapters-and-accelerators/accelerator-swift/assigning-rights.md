---
title: "指派權限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user accounts, assigning permissions
- security, user accounts
- document library, new messages
- document library, unparsed
- messages, document library
- privileges
- permissions
- unparsed document library
- security, permissions
ms.assetid: cee44240-aa00-4080-9e7f-728b2421102b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a980fde1a4aea5d2e741fa576e55e659c0835f9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="assigning-rights"></a><span data-ttu-id="0632b-102">指派權限</span><span class="sxs-lookup"><span data-stu-id="0632b-102">Assigning Rights</span></span>
<span data-ttu-id="0632b-103">文件庫，針對上述主題中建立每個網站群組上，應該被授與下列權限：</span><span class="sxs-lookup"><span data-stu-id="0632b-103">The following permissions should be granted on the Document libraries for each site group created in the preceding topic:</span></span>  
  
|<span data-ttu-id="0632b-104">文件庫</span><span class="sxs-lookup"><span data-stu-id="0632b-104">Document library</span></span>|<span data-ttu-id="0632b-105">網站群組</span><span class="sxs-lookup"><span data-stu-id="0632b-105">Site groups</span></span>|<span data-ttu-id="0632b-106">要套用的自訂文件庫權限</span><span class="sxs-lookup"><span data-stu-id="0632b-106">Custom document library permissions to apply</span></span>|  
|----------------------|-----------------|--------------------------------------------------|  
|<span data-ttu-id="0632b-107">範本文件庫</span><span class="sxs-lookup"><span data-stu-id="0632b-107">Templates document library</span></span>|<span data-ttu-id="0632b-108">Payments_Creators</span><span class="sxs-lookup"><span data-stu-id="0632b-108">Payments_Creators</span></span><br /><br /> <span data-ttu-id="0632b-109">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="0632b-109">Payments_Repairers</span></span><br /><br /> <span data-ttu-id="0632b-110">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="0632b-110">Payments_Approvers</span></span>|<span data-ttu-id="0632b-111">檢視項目</span><span class="sxs-lookup"><span data-stu-id="0632b-111">View items</span></span>|  
|<span data-ttu-id="0632b-112">未剖析 （下列詳細資料）</span><span class="sxs-lookup"><span data-stu-id="0632b-112">Unparsed (details below)</span></span>|<span data-ttu-id="0632b-113">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="0632b-113">Payments_Repairers</span></span>|<span data-ttu-id="0632b-114">檢視、 插入、 編輯、 刪除項目</span><span class="sxs-lookup"><span data-stu-id="0632b-114">View, insert, edit, delete items</span></span>|  
|<span data-ttu-id="0632b-115">新的 SWIFT MT 訊息 （下面的詳細資料）</span><span class="sxs-lookup"><span data-stu-id="0632b-115">New SWIFT MT Messages (details below)</span></span>|<span data-ttu-id="0632b-116">Payments_Creators</span><span class="sxs-lookup"><span data-stu-id="0632b-116">Payments_Creators</span></span>|<span data-ttu-id="0632b-117">檢視、 插入、 編輯、 刪除項目</span><span class="sxs-lookup"><span data-stu-id="0632b-117">View, insert, edit, delete items</span></span>|  
|<span data-ttu-id="0632b-118">新的 SWIFT MX 訊息 （下面的詳細資料）</span><span class="sxs-lookup"><span data-stu-id="0632b-118">New SWIFT MX Messages (details below)</span></span>|<span data-ttu-id="0632b-119">Payments_Creators</span><span class="sxs-lookup"><span data-stu-id="0632b-119">Payments_Creators</span></span>|<span data-ttu-id="0632b-120">檢視、 插入、 編輯、 刪除項目</span><span class="sxs-lookup"><span data-stu-id="0632b-120">View, insert, edit, delete items</span></span>|  
|<span data-ttu-id="0632b-121">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="0632b-121">Payments_Repairers</span></span>|<span data-ttu-id="0632b-122">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="0632b-122">Payments_Repairers</span></span>|<span data-ttu-id="0632b-123">檢視、 插入、 編輯、 刪除項目</span><span class="sxs-lookup"><span data-stu-id="0632b-123">View, insert, edit, delete items</span></span>|  
|<span data-ttu-id="0632b-124">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="0632b-124">Payments_Approvers</span></span>|<span data-ttu-id="0632b-125">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="0632b-125">Payments_Approvers</span></span>|<span data-ttu-id="0632b-126">檢視、 插入、 編輯、 刪除項目</span><span class="sxs-lookup"><span data-stu-id="0632b-126">View, insert, edit, delete items</span></span>|  
|[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="0632b-127">_Outbox</span><span class="sxs-lookup"><span data-stu-id="0632b-127">_Outbox</span></span>|<span data-ttu-id="0632b-128">Payments_Creators</span><span class="sxs-lookup"><span data-stu-id="0632b-128">Payments_Creators</span></span><br /><br /> <span data-ttu-id="0632b-129">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="0632b-129">Payments_Repairers</span></span><br /><br /> <span data-ttu-id="0632b-130">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="0632b-130">Payments_Approvers</span></span>|<span data-ttu-id="0632b-131">檢視、 插入、 編輯、 刪除項目</span><span class="sxs-lookup"><span data-stu-id="0632b-131">View, insert, edit, delete items</span></span>|  
  
## <a name="unparsed-document-library"></a><span data-ttu-id="0632b-132">未剖析的文件庫</span><span class="sxs-lookup"><span data-stu-id="0632b-132">Unparsed Document Library</span></span>  
 <span data-ttu-id="0632b-133">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]訊息修復程序會處理無法以特殊方式剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="0632b-133">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair process deals with messages that fail parsing in a special manner.</span></span> <span data-ttu-id="0632b-134">未剖析的訊息 （無法轉譯成 XML 的訊息） 會路由傳送至單一未剖析的訊息文件庫。</span><span class="sxs-lookup"><span data-stu-id="0632b-134">Unparsed messages (messages that cannot be translated into XML) are routed to a single unparsed message document library.</span></span> <span data-ttu-id="0632b-135">未剖析的文件庫應該限制為允許只有特定人員，而不是整個群組，來存取資料夾。</span><span class="sxs-lookup"><span data-stu-id="0632b-135">The unparsed document library should be restricted to allow only specific people, rather than entire groups, to access the folder.</span></span> <span data-ttu-id="0632b-136">這可確保未剖析的資料夾是儘可能安全。</span><span class="sxs-lookup"><span data-stu-id="0632b-136">This will ensure that the unparsed folder is as secure as possible.</span></span>  
  
 <span data-ttu-id="0632b-137">使用者擁有修復未剖析的訊息的權限定義在 MMC 的 [設定] 主控台，至少一個部門需要修復角色中的權限，也需要註冊在 NT 群組[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Users 群組。</span><span class="sxs-lookup"><span data-stu-id="0632b-137">Users who have permissions to repair unparsed messages need permissions in the repair role for at least one department defined in the MMC configuration console, and also need to be enrolled in the NT Group [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Users Group.</span></span>  
  
## <a name="new-swift-mt-mx-messages-document-library"></a><span data-ttu-id="0632b-138">新的 SWIFT MT / MX 訊息文件庫</span><span class="sxs-lookup"><span data-stu-id="0632b-138">New SWIFT MT/ MX Messages Document Library</span></span>  
 <span data-ttu-id="0632b-139">MRSR 網站部署時，會建立新 SWIFT MT 訊息和新 SWIFT MX 訊息文件庫。</span><span class="sxs-lookup"><span data-stu-id="0632b-139">The New SWIFT MT Messages and New SWIFT MX Messages document libraries are created at the time of deploying the MRSR site.</span></span> <span data-ttu-id="0632b-140">新的 SWIFT MT 訊息及新 SWIFT MX 郵件的文件庫儲存新的 SWIFT XML 範本或 「 重複使用 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="0632b-140">The New SWIFT MT Messages and New SWIFT MX Messages document libraries store new SWIFT XML templates or "boilerplate" messages.</span></span> <span data-ttu-id="0632b-141">若要建立新的 SWIFT InfoPath XML 格式表示的訊息，您可以使用這些訊息。</span><span class="sxs-lookup"><span data-stu-id="0632b-141">You can use these messages to create new SWIFT messages represented in InfoPath XML format.</span></span> <span data-ttu-id="0632b-142">這些訊息上傳到新的 SWIFT MT 訊息及新 SWIFT MX 郵件的文件庫使用者按一下文件庫中的 [上載] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0632b-142">These messages are uploaded into the New SWIFT MT Messages and New SWIFT MX Messages document libraries by the user by clicking on the Upload button in the document library.</span></span> <span data-ttu-id="0632b-143">您可以進一步散發新 SWIFT 訊息範本來限制對指定的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="0632b-143">You can further distribute the New SWIFT Message templates to restrict access to specified users.</span></span> <span data-ttu-id="0632b-144">若要這樣做您會先建立新的文件庫，然後再複製所需的文件庫中的 XML 範本。</span><span class="sxs-lookup"><span data-stu-id="0632b-144">To do so you first create a new document library, and then copy the XML templates required for the document library.</span></span>  
  
 <span data-ttu-id="0632b-145">如需 FormPublish 工具的詳細資訊，請參閱[FormPublish 工具](http://msdn.microsoft.com/en-us/09a6ed31-5917-4776-9a5e-955af440cdac)工具 > 一節中。</span><span class="sxs-lookup"><span data-stu-id="0632b-145">For more information about the FormPublish tool, see [FormPublish Tool](http://msdn.microsoft.com/en-us/09a6ed31-5917-4776-9a5e-955af440cdac) in the Tools section.</span></span>