---
title: 如何從應用程式和 BizTalk 群組移除原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting, policies
- managing [policies], applications
- managing [policies], deleting
- groups, policies
- managing [policies], groups
- applications, policies
ms.assetid: e9882cb3-8808-4258-a107-a24905290288
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4bb4b162d90811a4eddaa513556ecb1f6c6cd8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254510"
---
# <a name="how-to-remove-a-policy-from-an-application-and-the-biztalk-group"></a><span data-ttu-id="5e698-102">如何從應用程式和 BizTalk 群組移除原則</span><span class="sxs-lookup"><span data-stu-id="5e698-102">How to Remove a Policy from an Application and the BizTalk Group</span></span>
<span data-ttu-id="5e698-103">本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列將原則從應用程式以及 BizTalk 群組的「規則引擎」資料庫移除。</span><span class="sxs-lookup"><span data-stu-id="5e698-103">This topic describes how to use the BizTalk Server Administration console or the command-line to remove a policy from an application and the Rule Engine database for the BizTalk group.</span></span>  
  
 <span data-ttu-id="5e698-104">在移除原則之前，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="5e698-104">Before removing a policy, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="5e698-105">您無法移除已部署的原則。</span><span class="sxs-lookup"><span data-stu-id="5e698-105">You cannot remove a deployed policy.</span></span> <span data-ttu-id="5e698-106">您必須先解除部署原則中所述[如何部署或解除部署原則](../core/how-to-deploy-or-undeploy-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="5e698-106">You must first undeploy the policy, as described in [How to Deploy or Undeploy a Policy](../core/how-to-deploy-or-undeploy-a-policy.md).</span></span> <span data-ttu-id="5e698-107">解除部署原則會讓它成為非使用中，所以此原則在 BizTalk 群組中使用它的任何應用程式內都不再有任何作用。</span><span class="sxs-lookup"><span data-stu-id="5e698-107">Undeploying a policy makes it inactive so that it no longer functions in any application that uses it in the BizTalk group.</span></span>  
  
-   <span data-ttu-id="5e698-108">移除原則會將它從「規則引擎」資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="5e698-108">Removing a policy deletes it from the Rule Engine database.</span></span> <span data-ttu-id="5e698-109">如果想要再次使用這個原則，則應該在將它移除之前，先將它匯出至 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="5e698-109">If you want to use this policy again, you should export it to an .xml file before removing it.</span></span> <span data-ttu-id="5e698-110">如需指示，請參閱[如何匯出原則](../core/how-to-export-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="5e698-110">For instructions, see [How to Export a Policy](../core/how-to-export-a-policy.md).</span></span>  
  
-   <span data-ttu-id="5e698-111">如果有其他的應用程式使用該原則，則在移除之後，該原則在其他的應用程式都將失效。</span><span class="sxs-lookup"><span data-stu-id="5e698-111">If the policy is used by other applications, it will no longer be in effect for the other applications.</span></span> <span data-ttu-id="5e698-112">請在移除原則之前，確認您不想再針對任何其他的應用程式使用該原則。</span><span class="sxs-lookup"><span data-stu-id="5e698-112">Verify that you no longer want to use the policy for any other applications that reference it before you remove it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5e698-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="5e698-113">Prerequisites</span></span>  
 <span data-ttu-id="5e698-114">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="5e698-114">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="5e698-115">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5e698-115">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-a-policy"></a><span data-ttu-id="5e698-116">移除原則</span><span class="sxs-lookup"><span data-stu-id="5e698-116">To remove a policy</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="5e698-117">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="5e698-117">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="5e698-118">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="5e698-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5e698-119">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組包含原則移除，和包含原則的應用程式</span><span class="sxs-lookup"><span data-stu-id="5e698-119">In the console tree, expand  **BizTalk Server Administration**, expand the BizTalk group containing the policy to remove, and then expand the application containing the policy</span></span>  
  
3.  <span data-ttu-id="5e698-120">按一下**原則**，以滑鼠右鍵按一下原則，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="5e698-120">Click **Policies**, right-click the policy, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="5e698-121">使用命令列</span><span class="sxs-lookup"><span data-stu-id="5e698-121">Using the command line</span></span>  
  
1.  <span data-ttu-id="5e698-122">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="5e698-122">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="5e698-123">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="5e698-123">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="5e698-124">**BTSTask RemoveResource** [**/ApplicationName:***值*] **/Luid:***值*[**/Server:***值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="5e698-124">**BTSTask RemoveResource** [**/ApplicationName:***value*] **/Luid:***value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="5e698-125">範例：</span><span class="sxs-lookup"><span data-stu-id="5e698-125">Example:</span></span>  
  
     <span data-ttu-id="5e698-126">**BTSTask RemoveResource /applicationname: myapplication /Luid:"Rule/Policy1/1.0"**</span><span class="sxs-lookup"><span data-stu-id="5e698-126">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"Rule/Policy1/1.0"**</span></span>  
  
    |<span data-ttu-id="5e698-127">參數</span><span class="sxs-lookup"><span data-stu-id="5e698-127">Parameter</span></span>|<span data-ttu-id="5e698-128">Description</span><span class="sxs-lookup"><span data-stu-id="5e698-128">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="5e698-129">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="5e698-129">**/ApplicationName**</span></span>|<span data-ttu-id="5e698-130">包含待刪除之原則的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e698-130">Name of the BizTalk application containing the policy to delete.</span></span> <span data-ttu-id="5e698-131">如果沒有指定這個參數，將會使用預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e698-131">If this parameter is not specified, the default application is used.</span></span>|  
    |<span data-ttu-id="5e698-132">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="5e698-132">**/Luid**</span></span>|<span data-ttu-id="5e698-133">原則的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="5e698-133">Locally unique identifier (LUID) of the policy.</span></span> <span data-ttu-id="5e698-134">您可以使用來取得 LUID **ListApp**命令中所述[ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="5e698-134">You can obtain the LUID by using the **ListApp** command, as described in [ListApp Command](../core/listapp-command.md).</span></span>|  
    |<span data-ttu-id="5e698-135">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="5e698-135">**/Server**</span></span>|<span data-ttu-id="5e698-136">裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="5e698-136">Name of the SQL Server instance hosting the BizTalk Management database.</span></span> <span data-ttu-id="5e698-137">如果您指定 Database 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="5e698-137">Required if you specify the Database parameter.</span></span> <span data-ttu-id="5e698-138">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="5e698-138">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
    |<span data-ttu-id="5e698-139">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="5e698-139">**/Database**</span></span>|<span data-ttu-id="5e698-140">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e698-140">Name of the BizTalk Management database.</span></span> <span data-ttu-id="5e698-141">如果您指定 Server 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="5e698-141">Required if you specify the Server parameter.</span></span> <span data-ttu-id="5e698-142">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="5e698-142">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e698-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e698-143">See Also</span></span>  
 [<span data-ttu-id="5e698-144">管理原則</span><span class="sxs-lookup"><span data-stu-id="5e698-144">Managing Policies</span></span>](../core/managing-policies.md)