---
title: 如何從 BizTalk 群組刪除 BizTalk 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- undeploying, applications
- applications, deleting
- applications, groups
- undeploying, deleting
- managing [applications], deleting
- deleting, applications
- applications, undeploying
- managing [applications], groups
- groups, applications
ms.assetid: 968a6436-ae1a-4f85-bb44-e704826a0197
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 269ef99a3244d0aba55d9dad856c0262d0d14ba0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250102"
---
# <a name="how-to-delete-a-biztalk-application-from-the-biztalk-group"></a><span data-ttu-id="a3d0b-102">如何從 BizTalk 群組刪除 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="a3d0b-102">How to Delete a BizTalk Application from the BizTalk Group</span></span>
<span data-ttu-id="a3d0b-103">您可以從 BizTalk 群組刪除應用程式，</span><span class="sxs-lookup"><span data-stu-id="a3d0b-103">You can delete an application from the BizTalk group.</span></span> <span data-ttu-id="a3d0b-104">這樣會從此群組的 BizTalk 資料庫中移除它的所有資料，而此應用程式將不再顯示於 BizTalk Server 管理主控台中；</span><span class="sxs-lookup"><span data-stu-id="a3d0b-104">This removes all of its data from the BizTalk databases for the group, and the application no longer displays in the BizTalk Server Administration console.</span></span> <span data-ttu-id="a3d0b-105">但是，這並不會解除安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-105">It does not uninstall the application.</span></span>  
  
 <span data-ttu-id="a3d0b-106">在您刪除應用程式之前，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="a3d0b-106">Before you delete an application, bear in mind the following points:</span></span>  
  
-   <span data-ttu-id="a3d0b-107">您必須先停止應用程式，才能將它刪除。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-107">The application must be stopped before you can delete it.</span></span> <span data-ttu-id="a3d0b-108">中所述，您應該停止應用程式，使用完全停止 選項[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-108">You should use the Full Stop option for stopping the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="a3d0b-109">只有當沒有其他應用程式包含此應用程式的參考時，您才可以刪除此應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-109">You can delete an application only if no other applications contain references to it.</span></span> <span data-ttu-id="a3d0b-110">如果其他應用程式含有對此即將移除之應用程式的參考，您必須先從其他應用程式移除這些參考。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-110">If other applications contain references to the application you want to remove, you must first remove the references from the other applications.</span></span> <span data-ttu-id="a3d0b-111">如需指示，請參閱[如何移除另一個應用程式的參考](../core/how-to-remove-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-111">For instructions, see [How to Remove a Reference to Another Application](../core/how-to-remove-a-reference-to-another-application.md).</span></span>  
  
-   <span data-ttu-id="a3d0b-112">如果應用程式含有傳送埠群組，而另一個應用程式中的傳送埠是該群組的成員時，您無法刪除此應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-112">You cannot delete an application if it contains a send port group of which a send port in another application is a member.</span></span> <span data-ttu-id="a3d0b-113">您必須取消登錄該成員傳送埠，然後才能刪除應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-113">You must unenlist the member send port before you can delete the application.</span></span> <span data-ttu-id="a3d0b-114">如需指示，請參閱[如何取消登錄傳送埠或傳送埠群組](../core/how-to-unenlist-a-send-port-or-send-port-group.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-114">For instructions, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="a3d0b-115">如果應用程式含有某合作對象所參考的傳送埠，您將無法刪除此應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-115">You cannot delete an application if it contains a send port that is referenced by a party.</span></span> <span data-ttu-id="a3d0b-116">您可以刪除該合作對象所做的參考、刪除此傳送埠，或將傳送埠移至其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-116">You can delete the reference from the party, delete the send port, or move the send port to a different application.</span></span> <span data-ttu-id="a3d0b-117">如需執行這些工作的指示，請參閱[如何檢視或編輯合作對象](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca)，[如何刪除傳送埠](../core/how-to-delete-a-send-port.md)，或[如何將成品移至不同的應用程式](../core/how-to-move-an-artifact-to-a-different-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-117">For instructions on performing these tasks, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca), [How to Delete a Send Port](../core/how-to-delete-a-send-port.md), or [How to Move an Artifact to a Different Application](../core/how-to-move-an-artifact-to-a-different-application.md).</span></span>  
  
-   <span data-ttu-id="a3d0b-118">您無法刪除預設應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-118">You cannot delete the default application.</span></span> <span data-ttu-id="a3d0b-119">如果您要將其刪除，必須先指定其他應用程式做為預設應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-119">If you want to delete it, you must first make another application the default.</span></span> <span data-ttu-id="a3d0b-120">如需指示，請參閱[如何變更預設的應用程式](../core/how-to-change-the-default-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-120">For instructions, see [How to Change the Default Application](../core/how-to-change-the-default-application.md).</span></span>  
  
-   <span data-ttu-id="a3d0b-121">如果應用程式中有協調流程具有擱置的執行個體，您將無法刪除此應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-121">You cannot delete an application if an orchestration in the application has a suspended instance.</span></span>  
  
-   <span data-ttu-id="a3d0b-122">若要完全解除部署 BizTalk 應用程式，您還必須考慮中所述的步驟[如何解除安裝 BizTalk 應用程式](../core/how-to-uninstall-a-biztalk-application.md)，而且您也可能需要移除其他檔案和設定 中所述[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-122">To completely undeploy a BizTalk application, you must also take the steps described in [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md), and you may also need to remove other files and settings, as described in [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a3d0b-123">必要條件</span><span class="sxs-lookup"><span data-stu-id="a3d0b-123">Prerequisites</span></span>  
 <span data-ttu-id="a3d0b-124">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-124">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="a3d0b-125">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-125">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-delete-a-biztalk-application"></a><span data-ttu-id="a3d0b-126">刪除 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="a3d0b-126">To delete a BizTalk application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="a3d0b-127">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="a3d0b-127">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="a3d0b-128">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-128">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a3d0b-129">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，依序展開 [BizTalk 群組] 並展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-129">In the console tree, expand  **BizTalk Server Administration**, expand the BizTalk group, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="a3d0b-130">以滑鼠右鍵按一下 [應用程式] 資料夾，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-130">Right-click the application folder, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="a3d0b-131">按一下**是**確認刪除。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-131">Click **Yes** to confirm the deletion.</span></span>  
  
     <span data-ttu-id="a3d0b-132">BizTalk Server 會從 BizTalk 資料庫刪除所有的應用程式資料，並從管理主控台移除此應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-132">BizTalk Server deletes all of the application data from the BizTalk databases and removes the application from the administration console.</span></span>  
  
     <span data-ttu-id="a3d0b-133">如果 BizTalk Server 無法刪除任何應用程式成品，刪除作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-133">If BizTalk Server cannot delete any of the application artifacts, the delete operation fails.</span></span> <span data-ttu-id="a3d0b-134">在此情況下，BizTalk Server 會嘗試回復刪除作業。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-134">In this case, BizTalk Server attempts to roll back the delete operation.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="a3d0b-135">使用命令列</span><span class="sxs-lookup"><span data-stu-id="a3d0b-135">Using the command line</span></span>  
  
1.  <span data-ttu-id="a3d0b-136">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-136">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="a3d0b-137">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="a3d0b-137">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="a3d0b-138">**BTSTask RemoveApp /ApplicationName:** *值*[**/Server:***值*] [**/database:** *值*]</span><span class="sxs-lookup"><span data-stu-id="a3d0b-138">**BTSTask RemoveApp /ApplicationName:** *value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="a3d0b-139">範例：</span><span class="sxs-lookup"><span data-stu-id="a3d0b-139">Example:</span></span>  
  
     <span data-ttu-id="a3d0b-140">**BTSTask RemoveApp /applicationname: myapplication**</span><span class="sxs-lookup"><span data-stu-id="a3d0b-140">**BTSTask RemoveApp /ApplicationName:MyApplication**</span></span>  
  
    |<span data-ttu-id="a3d0b-141">參數</span><span class="sxs-lookup"><span data-stu-id="a3d0b-141">Parameter</span></span>|<span data-ttu-id="a3d0b-142">值</span><span class="sxs-lookup"><span data-stu-id="a3d0b-142">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="a3d0b-143">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="a3d0b-143">**/ApplicationName**</span></span>|<span data-ttu-id="a3d0b-144">要刪除的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-144">Name of the BizTalk application to delete.</span></span> <span data-ttu-id="a3d0b-145">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-145">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="a3d0b-146">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="a3d0b-146">**/Server**</span></span>|<span data-ttu-id="a3d0b-147">裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-147">Name of the SQL Server instance hosting the BizTalk Management database.</span></span> <span data-ttu-id="a3d0b-148">如果您指定 Database 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-148">Required if you specify the Database parameter.</span></span> <span data-ttu-id="a3d0b-149">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-149">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
    |<span data-ttu-id="a3d0b-150">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="a3d0b-150">**/Database**</span></span>|<span data-ttu-id="a3d0b-151">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-151">Name of the BizTalk Management database.</span></span> <span data-ttu-id="a3d0b-152">如果您指定 Server 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-152">Required if you specify the Server parameter.</span></span> <span data-ttu-id="a3d0b-153">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="a3d0b-153">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3d0b-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3d0b-154">See Also</span></span>  
 <span data-ttu-id="a3d0b-155">[解除部署 BizTalk 應用程式](../core/undeploying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="a3d0b-155">[Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="a3d0b-156">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="a3d0b-156">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)