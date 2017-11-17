---
title: "如何從應用程式移除 BizTalk 組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], assemblies
- assemblies, deleting
- deleting, assemblies
- applications, assemblies
- managing [assemblies], deleting
ms.assetid: 0691c3b6-476d-4e01-b50b-47d7c0b299bf
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c6731183fd4be4655d0365c1ce6277dd4052b6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-biztalk-assembly-from-an-application"></a><span data-ttu-id="9b6d6-102">如何從應用程式移除 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="9b6d6-102">How to Remove a BizTalk Assembly from an Application</span></span>
<span data-ttu-id="9b6d6-103">本主題描述如何使用 BizTalk Server 管理主控台或命令列，從 BizTalk 應用程式移除 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-103">This topic describes how use the BizTalk Server Administration console or the command line to remove a BizTalk assembly from a BizTalk application.</span></span> <span data-ttu-id="9b6d6-104">當您這麼做時，將會從應用程式及 BizTalk 管理資料庫移除組件及其包含的成品 (例如，協調流程、結構描述和管線)。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-104">When you do this, the assembly and the artifacts that it includes, such as orchestrations, schemas, and pipelines, are removed from the application and the BizTalk Management database.</span></span>  
  
 <span data-ttu-id="9b6d6-105">在移除 BizTalk 組件時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="9b6d6-105">Before removing a BizTalk assembly, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="9b6d6-106">移除 BizTalk 組件時，不會自動移除位於全域組件快取 (GAC) 或本機檔案系統中的組件檔案。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-106">When you remove a BizTalk assembly, the assembly file is not automatically removed from the global assembly cache (GAC) or the local file system, if it exists there.</span></span> <span data-ttu-id="9b6d6-107">您必須手動移除它。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-107">You must manually remove it.</span></span> <span data-ttu-id="9b6d6-108">如需指示，請參閱[如何從 GAC 解除安裝組件](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4)和[如何移除其他檔案和設定 BizTalk 應用程式](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-108">For instructions, see [How to Uninstall an Assembly from the GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4) and [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="9b6d6-109">如果您移除包含管線的 BizTalk 組件，則在同一應用程式中，任何使用該管線的傳送埠都會重設為使用預設的 PassThruTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-109">If you remove a BizTalk assembly that includes a pipeline, any send ports in the same application that use the pipeline will be reset to use the default, PassThruTransmit pipeline.</span></span>  
  
-   <span data-ttu-id="9b6d6-110">您無法移除有其他成品相依於其上的 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-110">You cannot remove a BizTalk assembly on which other artifacts depend.</span></span> <span data-ttu-id="9b6d6-111">您必須先移除相依的成品，</span><span class="sxs-lookup"><span data-stu-id="9b6d6-111">You must first remove the dependent artifacts.</span></span> <span data-ttu-id="9b6d6-112">然後才能移除該 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-112">Then you can remove the BizTalk assembly.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9b6d6-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="9b6d6-113">Prerequisites</span></span>  
 <span data-ttu-id="9b6d6-114">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-114">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="9b6d6-115">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-115">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-a-biztalk-assembly-from-an-application"></a><span data-ttu-id="9b6d6-116">從應用程式移除 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="9b6d6-116">To remove a BizTalk assembly from an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="9b6d6-117">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="9b6d6-117">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="9b6d6-118">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="9b6d6-119">在主控台樹狀目錄中，依序展開 [[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 管理]、包含您想要移除之 BizTalk 組件的 BizTalk 群組，然後展開包含此 BizTalk 組件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-119">In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration, expand the BizTalk group containing the BizTalk assembly to remove, and then expand the application containing the BizTalk assembly.</span></span>  
  
3.  <span data-ttu-id="9b6d6-120">按一下**資源**資料夾中，以滑鼠右鍵按一下 BizTalk 組件，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-120">Click the **Resources** folder, right-click the BizTalk assembly, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="9b6d6-121">使用命令列</span><span class="sxs-lookup"><span data-stu-id="9b6d6-121">Using the command line</span></span>  
  
1.  <span data-ttu-id="9b6d6-122">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-122">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="9b6d6-123">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="9b6d6-123">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="9b6d6-124">**BTSTask RemoveResource** [**/ApplicationName:***值*] **/Luid:***值*[**/Server:***值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="9b6d6-124">**BTSTask RemoveResource** [**/ApplicationName:***value*] **/Luid:***value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="9b6d6-125">範例：</span><span class="sxs-lookup"><span data-stu-id="9b6d6-125">Example:</span></span>  
  
     <span data-ttu-id="9b6d6-126">**BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApp.Orchestrations，版本 = 1.0.0.0，Culture = neutral，PublicKeyToken = 0123456789ABCDEF"**</span><span class="sxs-lookup"><span data-stu-id="9b6d6-126">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**</span></span>  
  
    |<span data-ttu-id="9b6d6-127">參數</span><span class="sxs-lookup"><span data-stu-id="9b6d6-127">Parameter</span></span>|<span data-ttu-id="9b6d6-128">Description</span><span class="sxs-lookup"><span data-stu-id="9b6d6-128">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="9b6d6-129">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="9b6d6-129">**/ApplicationName**</span></span>|<span data-ttu-id="9b6d6-130">包含待刪除之 BizTalk 組件的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-130">Name of the BizTalk application containing the BizTalk assembly to delete.</span></span> <span data-ttu-id="9b6d6-131">如果沒有指定這個參數，將會使用預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-131">If this parameter is not specified, the default application is used.</span></span> <span data-ttu-id="9b6d6-132">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-132">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="9b6d6-133">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="9b6d6-133">**/Luid**</span></span>|<span data-ttu-id="9b6d6-134">BizTalk 組件的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-134">Locally unique identifier (LUID) of the BizTalk assembly.</span></span> <span data-ttu-id="9b6d6-135">您可以使用來取得 LUID **ListApp**命令中所述[ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-135">You can obtain the LUID by using the **ListApp** command, as described in [ListApp Command](../core/listapp-command.md).</span></span>|  
    |<span data-ttu-id="9b6d6-136">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="9b6d6-136">**/Server**</span></span>|<span data-ttu-id="9b6d6-137">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-137">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="9b6d6-138">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-138">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="9b6d6-139">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-139">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="9b6d6-140">範例:</span><span class="sxs-lookup"><span data-stu-id="9b6d6-140">Examples:</span></span><br /><br /> <span data-ttu-id="9b6d6-141">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="9b6d6-141">Server=MyServer</span></span><br /><br /> <span data-ttu-id="9b6d6-142">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="9b6d6-142">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="9b6d6-143">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-143">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="9b6d6-144">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="9b6d6-144">**/Database**</span></span>|<span data-ttu-id="9b6d6-145">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-145">Name of the BizTalk Management database.</span></span> <span data-ttu-id="9b6d6-146">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="9b6d6-146">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b6d6-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b6d6-147">See Also</span></span>  
 <span data-ttu-id="9b6d6-148">[管理 BizTalk 組件](../core/managing-biztalk-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="9b6d6-148">[Managing BizTalk Assemblies](../core/managing-biztalk-assemblies.md) </span></span>  
 [<span data-ttu-id="9b6d6-149">RemoveResource 命令</span><span class="sxs-lookup"><span data-stu-id="9b6d6-149">RemoveResource Command</span></span>](../core/removeresource-command.md)