---
title: 建立部門和角色 Message Repair 和 New Submission |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- departments, creating
- creating, roles
- roles, requirements
- roles, creating
- creating, departments
- certificates, messages
- messages, certificates
ms.assetid: 6337bd57-63c5-4d97-b558-ac27d5eb60d7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d033ab3910657373f6e48b1f6e6bed076f730b51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210534"
---
# <a name="creating-departments-and-roles-for-message-repair-and-new-submission"></a><span data-ttu-id="1663b-102">Message Repair 和 New Submission 建立部門和角色</span><span class="sxs-lookup"><span data-stu-id="1663b-102">Creating Departments and Roles for Message Repair and New Submission</span></span>
<span data-ttu-id="1663b-103">Message Repair 和 New Submission 牽涉到下列四個不同的作業：</span><span class="sxs-lookup"><span data-stu-id="1663b-103">Message Repair and New Submission involves the following four different operations:</span></span>  
  
-   <span data-ttu-id="1663b-104">驗證失敗的訊息的修復</span><span class="sxs-lookup"><span data-stu-id="1663b-104">Repair of a message that has failed validation</span></span>  
  
-   <span data-ttu-id="1663b-105">修復 （包括重設金鑰） 的驗證</span><span class="sxs-lookup"><span data-stu-id="1663b-105">Verification of the repair (including rekeying)</span></span>  
  
-   <span data-ttu-id="1663b-106">核准的修復</span><span class="sxs-lookup"><span data-stu-id="1663b-106">Approval of the repair</span></span>  
  
-   <span data-ttu-id="1663b-107">建立的新訊息</span><span class="sxs-lookup"><span data-stu-id="1663b-107">Creation of a new message</span></span>  
  
 <span data-ttu-id="1663b-108">若要執行這些作業，使用者必須假設與作業相關聯的角色。</span><span class="sxs-lookup"><span data-stu-id="1663b-108">To perform one of these operations, a user must assume the role associated with the operation.</span></span> <span data-ttu-id="1663b-109">角色也必須處理部門 （如下所述） 的一部分。</span><span class="sxs-lookup"><span data-stu-id="1663b-109">The role must also be a part of the processing department (described below).</span></span> <span data-ttu-id="1663b-110">若要在工作流程執行階段之後提交訊息，使用者必須與使用者相關聯的有效憑證簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="1663b-110">To submit the message after performing a stage in the workflow, the user must sign the message with a valid certificate associated with the user.</span></span>  
  
## <a name="creating-departments-and-roles"></a><span data-ttu-id="1663b-111">建立部門和角色</span><span class="sxs-lookup"><span data-stu-id="1663b-111">Creating Departments and Roles</span></span>  
 <span data-ttu-id="1663b-112">設定檔的 Web 用戶端文件，請參閱。</span><span class="sxs-lookup"><span data-stu-id="1663b-112">Refer Profile Web client documentation.</span></span>  
  
## <a name="rules-of-role-use"></a><span data-ttu-id="1663b-113">角色，請使用規則</span><span class="sxs-lookup"><span data-stu-id="1663b-113">Rules of Role Use</span></span>  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="1663b-114">使用者、 角色和部門必須符合下列規則：</span><span class="sxs-lookup"><span data-stu-id="1663b-114"> users, roles, and departments must conform to the following rules:</span></span>  
  
-   <span data-ttu-id="1663b-115">已修復的訊息的完整工作流程是要修復，確認，然後核准訊息。</span><span class="sxs-lookup"><span data-stu-id="1663b-115">The full workflow for a repaired message is to repair, verify, and then approve the message.</span></span> <span data-ttu-id="1663b-116">建立訊息的完整工作流程是要建立、 修復、 確認，然後核准訊息。</span><span class="sxs-lookup"><span data-stu-id="1663b-116">The full workflow for a created message is to create, repair, verify, and then approve the message.</span></span> <span data-ttu-id="1663b-117">驗證及核准步驟是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="1663b-117">The verification and approval steps are optional.</span></span>  
  
-   <span data-ttu-id="1663b-118">部門的工作流程必須以建立角色或修復角色開頭。</span><span class="sxs-lookup"><span data-stu-id="1663b-118">A department's workflow must begin with a create role or repair role.</span></span> <span data-ttu-id="1663b-119">如果工作流程包括建立和修復步驟 （工作流程建立訊息），建立步驟必須之前立即修復步驟。</span><span class="sxs-lookup"><span data-stu-id="1663b-119">If a workflow includes both create and repair steps (a workflow for a created message), the create step must come immediately before the repair step.</span></span>  
  
-   <span data-ttu-id="1663b-120">建立訊息的工作流程必須包含只有一個具有的功能建立的角色。</span><span class="sxs-lookup"><span data-stu-id="1663b-120">A workflow for a created message must contain one and only one role that has a capability of create.</span></span>  
  
-   <span data-ttu-id="1663b-121">每個工作流程必須包含只有一個角色具備的修復功能。</span><span class="sxs-lookup"><span data-stu-id="1663b-121">Each workflow must contain one and only one role that has a capability of repair.</span></span>  
  
-   <span data-ttu-id="1663b-122">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者可以與一個以上的角色產生關聯，但沒有單一使用者可以執行單一工作流程中的多個步驟。</span><span class="sxs-lookup"><span data-stu-id="1663b-122">An [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user can be associated with more than one role, but no single user can execute more than one step in a single workflow.</span></span> <span data-ttu-id="1663b-123">例如，如果使用者 A 修復訊息和使用者 B 驗證訊息，然後使用者 A 和使用者 B 都不可以核准訊息。</span><span class="sxs-lookup"><span data-stu-id="1663b-123">For example, if user A repairs a message and user B verifies the message, then neither user A nor user B can approve the message.</span></span>  
  
-   <span data-ttu-id="1663b-124">沒有任何檢查角色或功能的 RekeyVerify 核准相對於其他角色與 RekeyVerify 或核准之功能的順序。</span><span class="sxs-lookup"><span data-stu-id="1663b-124">There is no check on the order of roles with the capability of RekeyVerify or Approve relative to other roles with the capability of RekeyVerify or Approve.</span></span>  
  
-   <span data-ttu-id="1663b-125">如果您已修復的訊息無法通過驗證一次，它會回到 MRSR 網站文件庫中的修復收件匣。</span><span class="sxs-lookup"><span data-stu-id="1663b-125">If a message that you have already repaired fails validation again, it goes back into the repair inbox in the MRSR site document library.</span></span> <span data-ttu-id="1663b-126">當發生這種情況時，不再適用的驗證和核准者角色 （根據誰已經在工作流程中執行的角色） 上先前的限制。</span><span class="sxs-lookup"><span data-stu-id="1663b-126">When this happens, the previous limitations on the verification and approver roles (based on who has already performed a role in the workflow) no longer apply.</span></span> <span data-ttu-id="1663b-127">例如，如果使用者 A 的訊息，使用者 B 的修復拒絕訊息驗證，與使用者 A 修復訊息第二次，然後使用者 B 以外的使用者無法檢查訊息。</span><span class="sxs-lookup"><span data-stu-id="1663b-127">For example, if user A repairs a message, user B rejects the message in verification, and user A repairs the message a second time, then a user other than user B could verify the message.</span></span> <span data-ttu-id="1663b-128">如果是這樣，使用者 B 無法核准訊息。</span><span class="sxs-lookup"><span data-stu-id="1663b-128">If that is the case, then user B could approve the message.</span></span> <span data-ttu-id="1663b-129">另一個例子是，如果使用者 A 建立的訊息，使用者 B 會拒絕訊息中的驗證，而且使用者 C 修復訊息，則使用者無法確認訊息。</span><span class="sxs-lookup"><span data-stu-id="1663b-129">Another example is that if user A creates a message, user B rejects the message in verification, and user C repairs the message, then user A could verify the message.</span></span>  
  
-   <span data-ttu-id="1663b-130">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]建立訊息的使用者也可以修復該訊息，如果它驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="1663b-130">An [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user who creates a message can also repair that message if it fails validation.</span></span>  
  
-   <span data-ttu-id="1663b-131">只有[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]部門與工作流程關聯的使用者可以執行工作流程中的步驟。</span><span class="sxs-lookup"><span data-stu-id="1663b-131">Only [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users in the department associated with a workflow can perform a step in the workflow.</span></span> <span data-ttu-id="1663b-132">當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者送出訊息時，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會驗證使用者，包含與訊息相關聯的部門中的角色 （透過使用者設定檔 （如果部門不是預設值） 設定檔的 web 用戶端中）。</span><span class="sxs-lookup"><span data-stu-id="1663b-132">When an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user submits a message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] verifies that the user has a role in the department associated with the message (through the User profiles (in case the department is not default) in Profile web client).</span></span>  
  
-   <span data-ttu-id="1663b-133">系統管理員可以授與單一[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者在部門內的多個角色。</span><span class="sxs-lookup"><span data-stu-id="1663b-133">An administrator can give a single [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user multiple roles within a department.</span></span> <span data-ttu-id="1663b-134">單一使用者可以執行修復、 驗證、 核准或建立或任何子集角色，但受限於上述任何一個工作流程上限制。</span><span class="sxs-lookup"><span data-stu-id="1663b-134">A single user can perform repair, verification, approval, or creation, or any subset of those roles, subject to the limitations on any one workflow described above.</span></span>  
  
## <a name="certificates"></a><span data-ttu-id="1663b-135">憑證</span><span class="sxs-lookup"><span data-stu-id="1663b-135">Certificates</span></span>  
 <span data-ttu-id="1663b-136">若要提交訊息，以在本機電腦上的修復、 驗證、 核准或建立之後,[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者必須登入他 / 她憑證的訊息。</span><span class="sxs-lookup"><span data-stu-id="1663b-136">To submit a message on your local computer after repair, verification, approval, or creation, the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user must sign the message with his or her certificate.</span></span> <span data-ttu-id="1663b-137">如需有關建立憑證的詳細資訊，請參閱[安裝憑證](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="1663b-137">For more information about creating certificates, see [Installing Certificates](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md).</span></span>  
  
 <span data-ttu-id="1663b-138">若要能夠將修復、 驗證、 核准，或藉由存取 MRSR 網站從遠端用戶端電腦建立一則訊息，使用者必須在 憑證-目前使用者/個人/憑證存放區 （使用者不需要其用戶端電腦加入他或她的憑證是系統管理員若要這樣做）。</span><span class="sxs-lookup"><span data-stu-id="1663b-138">To be able to repair, verify, approve, or create a message by accessing the MRSR site from a remote client computer, the user must add his or her certificate in the Certificates - Current User/Personal/Certificates store of their client computer (the user does not have to be an administrator to do so).</span></span> <span data-ttu-id="1663b-139">此外，系統管理員在伺服器上的必須將使用者的憑證 （以及任何其他使用者從他們的用戶端電腦存取伺服器） 的憑證 （本機電腦） 儲存在伺服器上的其他人員/憑證 /。</span><span class="sxs-lookup"><span data-stu-id="1663b-139">In addition, an administrator on the server must add the user's certificate (and those of any other users who access the server from their client computer) to the Certificates (Local Computer)/Other People/Certificates store on the server.</span></span>  
  
 <span data-ttu-id="1663b-140">單一使用者可能會有數個配置的角色，並執行任何這些角色時，應該使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="1663b-140">A single user might have several allotted roles, and should use the same certificate when performing any of those roles.</span></span>