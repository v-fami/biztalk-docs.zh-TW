---
title: 如何從應用程式移除協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, orchestrations
- deleting, orchestrations
- managing [orchestrations], deleting
- orchestrations, applications
- orchestrations, deleting
ms.assetid: e6d635ea-3513-42de-a667-b56c536e5328
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6e024ec32a8b84cc1d883a2a9382e6aa06109b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998183"
---
# <a name="how-to-remove-an-orchestration-from-an-application"></a><span data-ttu-id="b7a3f-102">如何從應用程式移除協調流程</span><span class="sxs-lookup"><span data-stu-id="b7a3f-102">How to Remove an Orchestration from an Application</span></span>
<span data-ttu-id="b7a3f-103">本主題描述如何使用 BizTalk Server 管理主控台或命令列，從 BizTalk 應用程式移除協調流程。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-103">This topic describes how to use the BizTalk Server Administration console or the command line to remove an orchestration from a BizTalk application.</span></span> <span data-ttu-id="b7a3f-104">從應用程式移除協調流程也會將它從 BizTalk 群組的 BizTalk 管理資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-104">Removing an orchestration from an application also deletes it from the BizTalk Management database for the BizTalk group.</span></span>  
  
 <span data-ttu-id="b7a3f-105">移除協調流程時，會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="b7a3f-105">When you remove an orchestration, the following occurs:</span></span>  
  
- <span data-ttu-id="b7a3f-106">協調流程會從 BizTalk 管理資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-106">The orchestration is deleted from the BizTalk Management database.</span></span>  
  
- <span data-ttu-id="b7a3f-107">包含協調流程的 BizTalk 組件會從 BizTalk 管理資料庫中刪除，但是不會從本機檔案系統或全域組件快取 (GAC) 中移除 (如果存在於這些位置)。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-107">The BizTalk assembly that contains the orchestration is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.</span></span>  
  
- <span data-ttu-id="b7a3f-108">由於會刪除 BizTalk 組件，所以包含在組件中的所有成品也會從 BizTalk 管理資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-108">As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are deleted from the BizTalk Management database as well.</span></span>  
  
  <span data-ttu-id="b7a3f-109">從應用程式移除協調流程前，請牢住下列要點：</span><span class="sxs-lookup"><span data-stu-id="b7a3f-109">Before removing an orchestration from an application, bear in mind the following important points:</span></span>  
  
- <span data-ttu-id="b7a3f-110">如果其他成品對此協調流程或對包含在也將移除之組件中的成品有相依性，則當您移除協調流程時，這些成品將再也無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-110">If other artifacts have dependencies on this orchestration or the artifacts contained in the assembly that will also be removed, they will no longer function correctly when you remove the orchestration.</span></span> <span data-ttu-id="b7a3f-111">如需相依性的背景資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-111">For background information about dependencies, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).</span></span>  
  
- <span data-ttu-id="b7a3f-112">您不可以移除具有執行中執行個體的協調流程。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-112">You cannot remove an orchestration that has running instances.</span></span> <span data-ttu-id="b7a3f-113">您必須終止任何在執行中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-113">You must terminate any running instances.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b7a3f-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="b7a3f-114">Prerequisites</span></span>  
 <span data-ttu-id="b7a3f-115">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-115">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="b7a3f-116">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-an-orchestration-from-an-application"></a><span data-ttu-id="b7a3f-117">從應用程式移除協調流程</span><span class="sxs-lookup"><span data-stu-id="b7a3f-117">To remove an orchestration from an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="b7a3f-118">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="b7a3f-118">Using the BizTalk Server Administration console</span></span>  
  
1. <span data-ttu-id="b7a3f-119">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-119">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="b7a3f-120">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您想要移除的協調流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-120">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to remove.</span></span>  
  
3. <span data-ttu-id="b7a3f-121">按一下 **協調流程**，以滑鼠右鍵按一下協調流程，然後按一下**取消登錄**。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-121">Click **Orchestrations**, right-click the orchestration, and then click **Unenlist**.</span></span>  
  
4. <span data-ttu-id="b7a3f-122">選取協調流程，指向**檢視**，然後按一下**執行個體資訊**。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-122">Select the orchestration, point to **View**, and then click **Instance Information**.</span></span>  
  
5. <span data-ttu-id="b7a3f-123">在查詢結果 窗格中，以滑鼠右鍵按一下協調流程執行個體，然後**Terminate**。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-123">In the query results pane, right-click the orchestration instances, and then click **Terminate**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b7a3f-124">您可以取消登錄、 終止執行中的執行個體，並停止所有的應用程式中的協調流程一次使用完全停止 選項，則應用程式中所述[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-124">You can unenlist, terminate running instances, and stop all of the orchestrations in an application at once by using the Full Stop option for the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
6. <span data-ttu-id="b7a3f-125">按一下 **協調流程**，以滑鼠右鍵按一下協調流程，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-125">Click **Orchestrations**, right-click the orchestration, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="b7a3f-126">使用命令列</span><span class="sxs-lookup"><span data-stu-id="b7a3f-126">Using the command line</span></span>  
  
1. <span data-ttu-id="b7a3f-127">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-127">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="b7a3f-128">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="b7a3f-128">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
    <span data-ttu-id="b7a3f-129">**BTSTask RemoveResource** [**/ApplicationName:**<em>值</em>] **/Luid:**<em>值</em>[**/Server:** <em>值</em>] [**/database:**<em>值</em>]</span><span class="sxs-lookup"><span data-stu-id="b7a3f-129">**BTSTask RemoveResource** [**/ApplicationName:**<em>value</em>] **/Luid:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]</span></span>  
  
    <span data-ttu-id="b7a3f-130">範例</span><span class="sxs-lookup"><span data-stu-id="b7a3f-130">Example:</span></span>  
  
    <span data-ttu-id="b7a3f-131">**BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApp.Orchestrations，版本 = 1.0.0.0、 文化特性 = 中性，PublicKeyToken = 0123456789ABCDEF"**</span><span class="sxs-lookup"><span data-stu-id="b7a3f-131">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**</span></span>  
  
   |<span data-ttu-id="b7a3f-132">參數</span><span class="sxs-lookup"><span data-stu-id="b7a3f-132">Parameter</span></span>|<span data-ttu-id="b7a3f-133">描述</span><span class="sxs-lookup"><span data-stu-id="b7a3f-133">Description</span></span>|  
   |---------------|-----------------|  
   |<span data-ttu-id="b7a3f-134">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="b7a3f-134">**/ApplicationName**</span></span>|<span data-ttu-id="b7a3f-135">包含待刪除之協調流程的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-135">Name of the BizTalk application containing the orchestration to delete.</span></span> <span data-ttu-id="b7a3f-136">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-136">If the name includes spaces, you must enclose it in double quotation marks (").</span></span> <span data-ttu-id="b7a3f-137">如果沒有指定這個參數，將會使用預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-137">If this parameter is not specified, the default application is used.</span></span>|  
   |<span data-ttu-id="b7a3f-138">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="b7a3f-138">**/Luid**</span></span>|<span data-ttu-id="b7a3f-139">協調流程的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-139">Locally unique identifier (LUID) of the orchestration.</span></span> <span data-ttu-id="b7a3f-140">您可以使用來取得 LUID [ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-140">You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).</span></span>|  
   |<span data-ttu-id="b7a3f-141">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="b7a3f-141">**/Server**</span></span>|<span data-ttu-id="b7a3f-142">裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-142">Name of the SQL Server instance hosting the BizTalk Management database.</span></span> <span data-ttu-id="b7a3f-143">如果您指定 Database 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-143">Required if you specify the Database parameter.</span></span> <span data-ttu-id="b7a3f-144">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-144">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
   |<span data-ttu-id="b7a3f-145">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="b7a3f-145">**/Database**</span></span>|<span data-ttu-id="b7a3f-146">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-146">Name of the BizTalk Management database.</span></span> <span data-ttu-id="b7a3f-147">如果您指定 Server 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-147">Required if you specify the Server parameter.</span></span> <span data-ttu-id="b7a3f-148">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="b7a3f-148">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7a3f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7a3f-149">See Also</span></span>  
 <span data-ttu-id="b7a3f-150">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="b7a3f-150">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 [<span data-ttu-id="b7a3f-151">RemoveResource 命令</span><span class="sxs-lookup"><span data-stu-id="b7a3f-151">RemoveResource Command</span></span>](../core/removeresource-command.md)