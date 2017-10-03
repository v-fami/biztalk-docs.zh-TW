---
title: "如何從應用程式移除協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, orchestrations
- deleting, orchestrations
- managing [orchestrations], deleting
- orchestrations, applications
- orchestrations, deleting
ms.assetid: e6d635ea-3513-42de-a667-b56c536e5328
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef4909f5430ae2d0435d519823abe9735cbc1cc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-an-orchestration-from-an-application"></a><span data-ttu-id="0eaab-102">如何從應用程式移除協調流程</span><span class="sxs-lookup"><span data-stu-id="0eaab-102">How to Remove an Orchestration from an Application</span></span>
<span data-ttu-id="0eaab-103">本主題描述如何使用 BizTalk Server 管理主控台或命令列，從 BizTalk 應用程式移除協調流程。</span><span class="sxs-lookup"><span data-stu-id="0eaab-103">This topic describes how to use the BizTalk Server Administration console or the command line to remove an orchestration from a BizTalk application.</span></span> <span data-ttu-id="0eaab-104">從應用程式移除協調流程也會將它從 BizTalk 群組的 BizTalk 管理資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="0eaab-104">Removing an orchestration from an application also deletes it from the BizTalk Management database for the BizTalk group.</span></span>  
  
 <span data-ttu-id="0eaab-105">移除協調流程時，會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="0eaab-105">When you remove an orchestration, the following occurs:</span></span>  
  
-   <span data-ttu-id="0eaab-106">協調流程會從 BizTalk 管理資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="0eaab-106">The orchestration is deleted from the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="0eaab-107">包含協調流程的 BizTalk 組件會從 BizTalk 管理資料庫中刪除，但是不會從本機檔案系統或全域組件快取 (GAC) 中移除 (如果存在於這些位置)。</span><span class="sxs-lookup"><span data-stu-id="0eaab-107">The BizTalk assembly that contains the orchestration is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.</span></span>  
  
-   <span data-ttu-id="0eaab-108">由於會刪除 BizTalk 組件，所以包含在組件中的所有成品也會從 BizTalk 管理資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="0eaab-108">As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are deleted from the BizTalk Management database as well.</span></span>  
  
 <span data-ttu-id="0eaab-109">從應用程式移除協調流程前，請牢住下列要點：</span><span class="sxs-lookup"><span data-stu-id="0eaab-109">Before removing an orchestration from an application, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="0eaab-110">如果其他成品對此協調流程或對包含在也將移除之組件中的成品有相依性，則當您移除協調流程時，這些成品將再也無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="0eaab-110">If other artifacts have dependencies on this orchestration or the artifacts contained in the assembly that will also be removed, they will no longer function correctly when you remove the orchestration.</span></span> <span data-ttu-id="0eaab-111">相依性的相關背景資訊，請參閱[相依性和應用程式部署](../core/dependencies-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="0eaab-111">For background information about dependencies, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).</span></span>  
  
-   <span data-ttu-id="0eaab-112">您不可以移除具有執行中執行個體的協調流程。</span><span class="sxs-lookup"><span data-stu-id="0eaab-112">You cannot remove an orchestration that has running instances.</span></span> <span data-ttu-id="0eaab-113">您必須終止任何在執行中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0eaab-113">You must terminate any running instances.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0eaab-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="0eaab-114">Prerequisites</span></span>  
 <span data-ttu-id="0eaab-115">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="0eaab-115">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="0eaab-116">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0eaab-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-an-orchestration-from-an-application"></a><span data-ttu-id="0eaab-117">從應用程式移除協調流程</span><span class="sxs-lookup"><span data-stu-id="0eaab-117">To remove an orchestration from an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="0eaab-118">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="0eaab-118">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="0eaab-119">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0eaab-119">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0eaab-120">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您想要移除的協調流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0eaab-120">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to remove.</span></span>  
  
3.  <span data-ttu-id="0eaab-121">按一下**協調流程**，協調流程中，以滑鼠右鍵按一下，然後按一下**取消登錄**。</span><span class="sxs-lookup"><span data-stu-id="0eaab-121">Click **Orchestrations**, right-click the orchestration, and then click **Unenlist**.</span></span>  
  
4.  <span data-ttu-id="0eaab-122">選取的協調流程，指向**檢視**，然後按一下 **執行個體資訊**。</span><span class="sxs-lookup"><span data-stu-id="0eaab-122">Select the orchestration, point to **View**, and then click **Instance Information**.</span></span>  
  
5.  <span data-ttu-id="0eaab-123">查詢結果] 窗格中，以滑鼠右鍵按一下協調流程執行個體，然後按一下 [ **Terminate**。</span><span class="sxs-lookup"><span data-stu-id="0eaab-123">In the query results pane, right-click the orchestration instances, and then click **Terminate**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0eaab-124">您可以取消登錄、 終止執行中的執行個體，並停止所有協調流程的應用程式中的一次使用完全停止 選項，則應用程式中所述[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0eaab-124">You can unenlist, terminate running instances, and stop all of the orchestrations in an application at once by using the Full Stop option for the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
6.  <span data-ttu-id="0eaab-125">按一下**協調流程**，協調流程中，以滑鼠右鍵按一下，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="0eaab-125">Click **Orchestrations**, right-click the orchestration, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="0eaab-126">使用命令列</span><span class="sxs-lookup"><span data-stu-id="0eaab-126">Using the command line</span></span>  
  
1.  <span data-ttu-id="0eaab-127">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="0eaab-127">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="0eaab-128">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="0eaab-128">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="0eaab-129">**BTSTask RemoveResource** [**/ApplicationName:***值*] **/Luid:***值*[**/Server:***值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="0eaab-129">**BTSTask RemoveResource** [**/ApplicationName:***value*] **/Luid:***value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="0eaab-130">範例：</span><span class="sxs-lookup"><span data-stu-id="0eaab-130">Example:</span></span>  
  
     <span data-ttu-id="0eaab-131">**BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApp.Orchestrations，版本 = 1.0.0.0，Culture = neutral，PublicKeyToken = 0123456789ABCDEF"**</span><span class="sxs-lookup"><span data-stu-id="0eaab-131">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**</span></span>  
  
    |<span data-ttu-id="0eaab-132">參數</span><span class="sxs-lookup"><span data-stu-id="0eaab-132">Parameter</span></span>|<span data-ttu-id="0eaab-133">Description</span><span class="sxs-lookup"><span data-stu-id="0eaab-133">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="0eaab-134">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="0eaab-134">**/ApplicationName**</span></span>|<span data-ttu-id="0eaab-135">包含待刪除之協調流程的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="0eaab-135">Name of the BizTalk application containing the orchestration to delete.</span></span> <span data-ttu-id="0eaab-136">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="0eaab-136">If the name includes spaces, you must enclose it in double quotation marks (").</span></span> <span data-ttu-id="0eaab-137">如果沒有指定這個參數，將會使用預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0eaab-137">If this parameter is not specified, the default application is used.</span></span>|  
    |<span data-ttu-id="0eaab-138">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="0eaab-138">**/Luid**</span></span>|<span data-ttu-id="0eaab-139">協調流程的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="0eaab-139">Locally unique identifier (LUID) of the orchestration.</span></span> <span data-ttu-id="0eaab-140">您可以使用來取得 LUID [ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="0eaab-140">You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).</span></span>|  
    |<span data-ttu-id="0eaab-141">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="0eaab-141">**/Server**</span></span>|<span data-ttu-id="0eaab-142">裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="0eaab-142">Name of the SQL Server instance hosting the BizTalk Management database.</span></span> <span data-ttu-id="0eaab-143">如果您指定 Database 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="0eaab-143">Required if you specify the Database parameter.</span></span> <span data-ttu-id="0eaab-144">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="0eaab-144">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
    |<span data-ttu-id="0eaab-145">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="0eaab-145">**/Database**</span></span>|<span data-ttu-id="0eaab-146">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="0eaab-146">Name of the BizTalk Management database.</span></span> <span data-ttu-id="0eaab-147">如果您指定 Server 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="0eaab-147">Required if you specify the Server parameter.</span></span> <span data-ttu-id="0eaab-148">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="0eaab-148">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0eaab-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eaab-149">See Also</span></span>  
 <span data-ttu-id="0eaab-150">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="0eaab-150">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 [<span data-ttu-id="0eaab-151">RemoveResource 命令</span><span class="sxs-lookup"><span data-stu-id="0eaab-151">RemoveResource Command</span></span>](../core/removeresource-command.md)