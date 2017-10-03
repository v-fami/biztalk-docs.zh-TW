---
title: "如何管理 BizTalk Server 系統管理員群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Administrators group, user accounts
- BizTalk Administrators group
- user accounts, BizTalk Administrators group
- Windows Management Instrumentation (WMI), administering
- BizTalk Administrators group, privileges
- security, BizTalk Administrators group
- Administration Console [BizTalk Server], security
- Administration Console [BizTalk Server], administering
- BizTalk Administrators group, about BizTalk Administrators group
ms.assetid: 60ea689b-0b93-4fcc-b49c-6436e7be473f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fe92c9c43ccef242d8c14b5f1aa48e0b1a8d852
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-the-biztalk-server-administrators-group"></a><span data-ttu-id="74ee4-102">如何管理 BizTalk Server 系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="74ee4-102">How to Manage the BizTalk Server Administrators Group</span></span>
<span data-ttu-id="74ee4-103">「BizTalk Server 系統管理員」群組擁有執行管理工作所需的最低權限。</span><span class="sxs-lookup"><span data-stu-id="74ee4-103">The BizTalk Server Administrators group has the fewest privileges necessary to perform administrative tasks.</span></span> <span data-ttu-id="74ee4-104">您要將使用者新增到「BizTalk Server 系統管理員」群組，以便他們可以使用 BizTalk Server 管理主控台或 WMI 提供者來執行管理工作。</span><span class="sxs-lookup"><span data-stu-id="74ee4-104">You add users to the BizTalk Server Administrators group so that they can perform administrative tasks by using the BizTalk Server Administration Console or the WMI provider.</span></span> <span data-ttu-id="74ee4-105">當使用者不需再使用 BizTalk Server 管理主控台或 WMI 提供者執行管理工作時，您也要將他們從「BizTalk Server 系統管理員」中移除。</span><span class="sxs-lookup"><span data-stu-id="74ee4-105">You also remove users from the BizTalk Server Administrators group when they no longer need to perform administrative tasks by using the BizTalk Server Administration Console or the WMI provider.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="74ee4-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="74ee4-106">Prerequisites</span></span>  
 <span data-ttu-id="74ee4-107">您必須是系統管理員或 Domain Admins 群組的成員，才能執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="74ee4-107">You must be a member of the Administrators or Domain Admins group to perform this procedure.</span></span>  
  
### <a name="to-add-users-to-the-local-biztalk-server-administrators-group"></a><span data-ttu-id="74ee4-108">將使用者新增到本機 BizTalk Server 系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="74ee4-108">To add users to the local BizTalk Server Administrators group</span></span>  
  
1.  <span data-ttu-id="74ee4-109">按一下**啟動**，指向 **系統管理工具**，然後按一下 **電腦管理**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-109">Click **Start**, point to **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="74ee4-110">展開**系統工具**，依序展開**本機使用者和群組**，然後按一下 **群組**資料夾。</span><span class="sxs-lookup"><span data-stu-id="74ee4-110">Expand **System Tools**, expand **Local Users and Groups**, and then click the **Groups** folder.</span></span> <span data-ttu-id="74ee4-111">資料夾內容會在詳細資料窗格中出現。</span><span class="sxs-lookup"><span data-stu-id="74ee4-111">The folder contents appear in the details pane.</span></span>  
  
3.  <span data-ttu-id="74ee4-112">在 [詳細資料] 窗格中，按一下**BizTalk Server 系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-112">In the details pane, click **BizTalk Server Administrators**.</span></span>  
  
4.  <span data-ttu-id="74ee4-113">在**動作**功能表上，指向**所有工作**，然後按一下 **新增到群組**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-113">On the **Action** menu, point to **All Tasks**, and then click **Add to Group**.</span></span>  
  
5.  <span data-ttu-id="74ee4-114">在**BizTalk Server 系統管理員屬性**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-114">In the **BizTalk Server Administrators Properties** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="74ee4-115">在**查看**清單中，選取您的網域或電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="74ee4-115">In the **Look in** list, select your domain or computer name.</span></span>  
  
7.  <span data-ttu-id="74ee4-116">在包含使用者和電腦相關聯的網域或您在步驟 6 選取的電腦清單中，選取的使用者帳戶新增，請按一下 **新增**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-116">In the list that contains the users and computers associated with the domain or computer you selected in step 6, select the user account to add, click **Add**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="74ee4-117">按一下**確定**關閉**BizTalk Server 系統管理員屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="74ee4-117">Click **OK** to close the **BizTalk Server Administrators Properties** dialog box.</span></span>  
  
### <a name="to-remove-users-from-local-the-biztalk-server-administrators-group"></a><span data-ttu-id="74ee4-118">從本機 BizTalk Server 系統管理員群組移除使用者</span><span class="sxs-lookup"><span data-stu-id="74ee4-118">To remove users from local the BizTalk Server Administrators group</span></span>  
  
1.  <span data-ttu-id="74ee4-119">按一下**啟動**，指向 **系統管理工具**，然後按一下 **電腦管理**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-119">Click **Start**, point to **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="74ee4-120">展開**系統工具**，依序展開**本機使用者和群組**，然後按一下 **群組**資料夾。</span><span class="sxs-lookup"><span data-stu-id="74ee4-120">Expand **System Tools**, expand **Local Users and Groups**, and then click the **Groups** folder.</span></span> <span data-ttu-id="74ee4-121">資料夾內容會在詳細資料窗格中出現。</span><span class="sxs-lookup"><span data-stu-id="74ee4-121">The folder contents appear in the details pane.</span></span>  
  
3.  <span data-ttu-id="74ee4-122">在 [詳細資料] 窗格中，按一下**BizTalk Server 系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-122">In the details pane, click **BizTalk Server Administrators**.</span></span>  
  
4.  <span data-ttu-id="74ee4-123">在**動作**功能表上，按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-123">On the **Action** menu, click **Properties**.</span></span>  
  
5.  <span data-ttu-id="74ee4-124">在**BizTalk Server 系統管理員屬性**對話方塊中選取的使用者帳戶您想来移除，然後再按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-124">In the **BizTalk Server Administrators Properties** dialog box, select the user account you want to remove, and then click **Remove**.</span></span>  
  
6.  <span data-ttu-id="74ee4-125">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-125">Click **OK**.</span></span>  
  
### <a name="to-add-users-to-the-domain-biztalk-server-administrators-group"></a><span data-ttu-id="74ee4-126">將使用者新增到網域 BizTalk Server 系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="74ee4-126">To add users to the domain BizTalk Server Administrators group</span></span>  
  
1.  <span data-ttu-id="74ee4-127">使用 Domain Admins 帳戶登入連結 SQL Server 資料庫的網域控制站。</span><span class="sxs-lookup"><span data-stu-id="74ee4-127">Log on to the domain controller where the SQL Server databases are joined by using the Domain Admins account.</span></span>  
  
2.  <span data-ttu-id="74ee4-128">按一下**啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **Active Directory 使用者和電腦**至啟動**Active Directory 使用者和電腦**主控台。</span><span class="sxs-lookup"><span data-stu-id="74ee4-128">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Active Directory Users and Computers** to start the **Active Directory Users and Computers** console.</span></span>  
  
    1.  <span data-ttu-id="74ee4-129">在主控台樹狀目錄中，按一下包含您要新增成員之「BizTalk Server 系統管理員」群組的資料夾。</span><span class="sxs-lookup"><span data-stu-id="74ee4-129">In the console tree, click the folder that contains the BizTalk Server Administrators group to which you want to add a member.</span></span>  
  
    2.  <span data-ttu-id="74ee4-130">在詳細資料窗格中，以滑鼠右鍵按一下 BizTalk Server 系統管理員群組，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-130">In the details pane, right-click the BizTalk Server Administrators group, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="74ee4-131">在**成員**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-131">On the **Members** tab, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="74ee4-132">在**輸入物件名稱來選取**，輸入使用者名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-132">In **Enter the object names to select**, type the name of the user, and then click **OK**.</span></span>  
  
### <a name="to-remove-users-from-the-domain-biztalk-server-administrators-group"></a><span data-ttu-id="74ee4-133">從網域 BizTalk Server 系統管理員群組移除使用者</span><span class="sxs-lookup"><span data-stu-id="74ee4-133">To remove users from the domain BizTalk Server Administrators group</span></span>  
  
1.  <span data-ttu-id="74ee4-134">使用 Domain Admins 帳戶登入連結 SQL 資料庫的網域控制站。</span><span class="sxs-lookup"><span data-stu-id="74ee4-134">Log on to the domain controller where SQL databases are joined using the Domain Admins account.</span></span>  
  
2.  <span data-ttu-id="74ee4-135">按一下**啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **Active Directory 使用者和電腦**至啟動**Active Directory 使用者和電腦**主控台。</span><span class="sxs-lookup"><span data-stu-id="74ee4-135">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Active Directory Users and Computers** to start the **Active Directory Users and Computers** console.</span></span>  
  
    1.  <span data-ttu-id="74ee4-136">在主控台樹狀目錄中，按一下包含您要新增成員之「BizTalk Server 系統管理員」群組的資料夾。</span><span class="sxs-lookup"><span data-stu-id="74ee4-136">In the console tree, click the folder that contains the BizTalk Server Administrators group to which you want to add a member.</span></span>  
  
    2.  <span data-ttu-id="74ee4-137">在詳細資料窗格中，以滑鼠右鍵按一下 BizTalk Server 系統管理員群組，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-137">In the details pane, right-click the BizTalk Server Administrators group, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="74ee4-138">在**成員**索引標籤上，按一下您想要移除，然後按一下的成員**移除**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-138">On the **Members** tab, click the member you want to remove, and then click **Remove**.</span></span>  
  
    4.  <span data-ttu-id="74ee4-139">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="74ee4-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ee4-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74ee4-140">See Also</span></span>  
 <span data-ttu-id="74ee4-141">[管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md) </span><span class="sxs-lookup"><span data-stu-id="74ee4-141">[Managing BizTalk Server Security](../core/managing-biztalk-server-security.md) </span></span>  
 <span data-ttu-id="74ee4-142">[管理主控件和服務帳戶](../core/managing-hosts-and-service-accounts.md) </span><span class="sxs-lookup"><span data-stu-id="74ee4-142">[Managing Hosts and Service Accounts](../core/managing-hosts-and-service-accounts.md) </span></span>  
 <span data-ttu-id="74ee4-143">[管理 Windows 群組和使用者帳戶的最佳作法](../core/best-practices-for-managing-windows-groups-and-user-accounts.md) </span><span class="sxs-lookup"><span data-stu-id="74ee4-143">[Best Practices for Managing Windows Groups and User Accounts](../core/best-practices-for-managing-windows-groups-and-user-accounts.md) </span></span>  
 <span data-ttu-id="74ee4-144">[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="74ee4-144">[Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md) </span></span>  
 [<span data-ttu-id="74ee4-145">管理 Windows 群組和使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="74ee4-145">Managing Windows Groups and User Accounts</span></span>](../core/managing-windows-groups-and-user-accounts.md)