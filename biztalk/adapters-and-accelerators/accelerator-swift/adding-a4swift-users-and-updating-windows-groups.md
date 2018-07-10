---
title: 新增 A4SWIFT 使用者和更新 Windows 群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user accounts, Windows groups
- Windows groups, user accounts
- user accounts, creating
- Windows groups, updating
- updating Windows groups
- A4SWIFT, creating user accounts
ms.assetid: ddc54457-6499-402c-9cc2-f7b17bbc255f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb276c069a86d060c319f960e666210691b69056
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973327"
---
# <a name="adding-a4swift-users-and-updating-windows-groups"></a><span data-ttu-id="10b8e-102">新增 A4SWIFT 使用者和更新 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="10b8e-102">Adding A4SWIFT Users and Updating Windows Groups</span></span>
<span data-ttu-id="10b8e-103">建立後，當您安裝 Message Repair 和 New Submission 角色的憑證時，您必須建立[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者，並新增[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者群組。</span><span class="sxs-lookup"><span data-stu-id="10b8e-103">After you create and install certificates for Message Repair and New Submission roles, you must create [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users and add [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] users to groups.</span></span>  
  
 <span data-ttu-id="10b8e-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="10b8e-104">**Summary**</span></span>  
  
 <span data-ttu-id="10b8e-105">建立 Message Repair 和 New Submission 的使用者，並將本機或網域帳戶加入[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者群組，，如下所示：</span><span class="sxs-lookup"><span data-stu-id="10b8e-105">Create Message Repair and New Submission users and add local or domain accounts to [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] user groups, as follows:</span></span>  
  
- <span data-ttu-id="10b8e-106">在 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管理主控台中，您需要建立 Message Repair 和 New Submission 程序的工作流程階段中有角色的使用者數目。</span><span class="sxs-lookup"><span data-stu-id="10b8e-106">In the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Management Console, you need to create as many users as there are roles in the workflow stages of your Message Repair and New Submission process.</span></span> <span data-ttu-id="10b8e-107">將完全不同的憑證與每個這些使用者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="10b8e-107">Associate a distinct certificate with each of these users.</span></span>  
  
- <span data-ttu-id="10b8e-108">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]電腦管理公用程式，新增建立、 修復，每個本機使用者驗證，或核准 A4SWIFT 使用者的訊息。</span><span class="sxs-lookup"><span data-stu-id="10b8e-108">Using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Computer Management utility, add each local user who is creating, repairing, verifying, or approving a message to the A4SWIFT Users.</span></span>  
  
- <span data-ttu-id="10b8e-109">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]電腦管理公用程式，將會列在 [BizTalk Service BizTalk Group 服務的 [登入身分] 欄位的本機使用者新增[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Users 群組。</span><span class="sxs-lookup"><span data-stu-id="10b8e-109">Using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Computer Management utility, add the local user that is listed in the Log On As field for the BizTalk Service BizTalk Group service to the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Users group.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="10b8e-110">如需詳細資訊[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者和角色，請參閱[建立部門和角色 Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)。</span><span class="sxs-lookup"><span data-stu-id="10b8e-110">For more information about [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users and roles, see [Creating Departments and Roles for Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).</span></span>  
  
### <a name="to-add-user-accounts-to-the-a4swift-users-group"></a><span data-ttu-id="10b8e-111">若要將使用者帳戶新增 A4SWIFT 使用者群組</span><span class="sxs-lookup"><span data-stu-id="10b8e-111">To add User Accounts to the A4SWIFT Users Group</span></span>  
  
1.  <span data-ttu-id="10b8e-112">按一下 **開始**，指向**所有程式**，指向**系統管理工具**，然後按一下**電腦管理**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-112">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="10b8e-113">在**電腦管理**對話方塊中，在左窗格中，展開**本機使用者和群組**，然後按一下**群組**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-113">In the **Computer Management** dialog box, in the left pane, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
3.  <span data-ttu-id="10b8e-114">在 **電腦管理**對話方塊中，在右窗格中，按兩下**A4SWIFT 使用者**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-114">In the **Computer Management** dialog box, in the right pane, double-click **A4SWIFT Users**.</span></span>  
  
4.  <span data-ttu-id="10b8e-115">在 [ **A4SWIFT 使用者屬性**] 對話方塊中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-115">In the **A4SWIFT Users Properties** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="10b8e-116">在**選取使用者、 電腦或群組**對話方塊中，於**輸入物件名稱來選取**] 窗格中，輸入本機使用者名稱建立、 修復、 驗證，或核准訊息，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-116">In the **Select Users, Computers, or Groups** dialog box, in the **Enter the object names to select** pane, type the name of a local user who is creating, repairing, verifying, or approving a message, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="10b8e-117">針對每個本機使用者建立、 修復、 驗證，或核准訊息重複步驟 5。</span><span class="sxs-lookup"><span data-stu-id="10b8e-117">Repeat step 5 for each local user who is creating, repairing, verifying, or approving a message.</span></span>  
  
7.  <span data-ttu-id="10b8e-118">在 [A4SWIFT 使用者屬性] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-118">In the A4SWIFT Users Properties dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="10b8e-119">在 電腦管理 對話方塊的左窗格中，展開 服務及應用程式，然後按一下服務。</span><span class="sxs-lookup"><span data-stu-id="10b8e-119">In the Computer Management dialog box, in the left pane, expand Services and Applications, and then click Services.</span></span> <span data-ttu-id="10b8e-120">在右窗格中，按一下**BizTalk 服務 BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-120">In the right pane, click **BizTalk Service BizTalk Group**.</span></span> <span data-ttu-id="10b8e-121">請注意在的 [登入身分] 欄中所列的使用者**BizTalk 服務 BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-121">Note the user listed in the Log On As column for **BizTalk Service BizTalk Group**.</span></span>  
  
9. <span data-ttu-id="10b8e-122">在左窗格中**電腦管理**對話方塊方塊中，展開**本機使用者和群組**，然後按一下**群組**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-122">In the left pane of the **Computer Management** dialog box, expand **Local Users and Groups**, and then click **Groups**.</span></span> <span data-ttu-id="10b8e-123">按兩下**A4SWIFT 使用者**。</span><span class="sxs-lookup"><span data-stu-id="10b8e-123">Double-click **A4SWIFT Users**.</span></span> <span data-ttu-id="10b8e-124">請確定在的 [登入身分] 欄中所列的使用者**BizTalk Service BizTalk Group**屬於**A4SWIFT 使用者**群組。</span><span class="sxs-lookup"><span data-stu-id="10b8e-124">Ensure that the user listed in the Log On As column for **BizTalk Service BizTalk Group** is part of the **A4SWIFT Users** group.</span></span> <span data-ttu-id="10b8e-125">如果沒有，請加入該使用者才**A4SWIFT 使用者**群組。</span><span class="sxs-lookup"><span data-stu-id="10b8e-125">If not, add that user to the **A4SWIFT Users** group.</span></span>  
  
10. <span data-ttu-id="10b8e-126">登出伺服器，然後再次登入。</span><span class="sxs-lookup"><span data-stu-id="10b8e-126">Log off the server, and then log back on.</span></span>