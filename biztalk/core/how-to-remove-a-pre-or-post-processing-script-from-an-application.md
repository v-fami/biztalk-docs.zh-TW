---
title: 如何從應用程式移除前置或後置處理指令碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [scripts], deleting
- deleting, scripts
- managing [applications], scripts
- scripts, deleting
- applications, scripts
ms.assetid: 7911f098-97f2-4a5d-87fe-20b55231113e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c9742b6c523f193a8670c1171f38949ef5dd1cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010007"
---
# <a name="how-to-remove-a-pre--or-post-processing-script-from-an-application"></a><span data-ttu-id="48b72-102">如何從應用程式移除前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="48b72-102">How to Remove a Pre- or Post-processing Script from an Application</span></span>
<span data-ttu-id="48b72-103">本主題說明如何使用 BizTalk Server 管理主控台或命令列，將前置或後置處理指令碼從應用程式移除。</span><span class="sxs-lookup"><span data-stu-id="48b72-103">This topic describes how to use the BizTalk Server Administration console or the command line to remove a pre- or post-processing script from an application.</span></span> <span data-ttu-id="48b72-104">這會從 BizTalk 管理資料庫移除指令碼，所以它不會匯出到應用程式 .msi 檔案中。</span><span class="sxs-lookup"><span data-stu-id="48b72-104">This removes the script from the BizTalk Management database, so that it will not be exported in the application .msi file.</span></span> <span data-ttu-id="48b72-105">如果在本機檔案系統中有此指令碼，則不會移除它。</span><span class="sxs-lookup"><span data-stu-id="48b72-105">This does not remove the script from the local file system, if it exists there.</span></span>  
  
 <span data-ttu-id="48b72-106">如果包含指令碼的應用程式已安裝在本機檔案系統，而且指令碼是設計為解除安裝期間執行，您必須從檔案系統移除此指令碼，以避免在解除安裝應用程式時執行它。</span><span class="sxs-lookup"><span data-stu-id="48b72-106">If the application containing the script has been installed on the local file system, and the script is designed to run during uninstallation, you must remove the script from the file system to prevent it from running when the application is uninstalled.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="48b72-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="48b72-107">Prerequisites</span></span>  
 <span data-ttu-id="48b72-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="48b72-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="48b72-109">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="48b72-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-a-script-from-an-application"></a><span data-ttu-id="48b72-110">若要從應用程式移除指令碼</span><span class="sxs-lookup"><span data-stu-id="48b72-110">To remove a script from an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="48b72-111">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="48b72-111">Using the BizTalk Server Administration console</span></span>  
  
1. <span data-ttu-id="48b72-112">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="48b72-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="48b72-113">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 BizTalk 群組包含指令碼中移除，然後再展開 包含的指令碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="48b72-113">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the script to remove, and then expand the application containing the script.</span></span>  
  
3. <span data-ttu-id="48b72-114">按一下 **資源**資料夾中，以滑鼠右鍵按一下指令碼，然後**移除**。</span><span class="sxs-lookup"><span data-stu-id="48b72-114">Click the **Resources** folder, right-click the script, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="48b72-115">使用命令列</span><span class="sxs-lookup"><span data-stu-id="48b72-115">Using the command line</span></span>  
  
1. <span data-ttu-id="48b72-116">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="48b72-116">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="48b72-117">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="48b72-117">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
    <span data-ttu-id="48b72-118">**BTSTask RemoveResource** [**/ApplicationName:**<em>值</em>] **/Luid:**<em>值</em>[**/Server:** <em>值</em>] [**/database:**<em>值</em>]</span><span class="sxs-lookup"><span data-stu-id="48b72-118">**BTSTask RemoveResource** [**/ApplicationName:**<em>value</em>] **/Luid:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]</span></span>  
  
    <span data-ttu-id="48b72-119">範例</span><span class="sxs-lookup"><span data-stu-id="48b72-119">Example:</span></span>  
  
    <span data-ttu-id="48b72-120">**BTSTask RemoveResource /applicationname: myapplication /Luid:"MyApplication:MyScript.vbs"**</span><span class="sxs-lookup"><span data-stu-id="48b72-120">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApplication:MyScript.vbs"**</span></span>  
  
   |<span data-ttu-id="48b72-121">參數</span><span class="sxs-lookup"><span data-stu-id="48b72-121">Parameter</span></span>|<span data-ttu-id="48b72-122">描述</span><span class="sxs-lookup"><span data-stu-id="48b72-122">Description</span></span>|  
   |---------------|-----------------|  
   |<span data-ttu-id="48b72-123">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="48b72-123">**/ApplicationName**</span></span>|<span data-ttu-id="48b72-124">含有所要刪除之 BizTalk 指令碼的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="48b72-124">Name of the BizTalk application containing the BizTalk script to delete.</span></span> <span data-ttu-id="48b72-125">如果名稱包含空格，必須以雙引號 (") 將其括住。</span><span class="sxs-lookup"><span data-stu-id="48b72-125">If the name includes spaces, it must be enclosed in double quotation marks (").</span></span> <span data-ttu-id="48b72-126">如果沒有指定這個參數，將會使用預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="48b72-126">If this parameter is not specified, the default application is used.</span></span>|  
   |<span data-ttu-id="48b72-127">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="48b72-127">**/Luid**</span></span>|<span data-ttu-id="48b72-128">指令碼的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="48b72-128">Locally unique identifier (LUID) of the script.</span></span> <span data-ttu-id="48b72-129">您可以使用來取得 LUID [ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="48b72-129">You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).</span></span>|  
   |<span data-ttu-id="48b72-130">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="48b72-130">**/Server**</span></span>|<span data-ttu-id="48b72-131">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="48b72-131">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="48b72-132">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="48b72-132">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="48b72-133">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="48b72-133">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="48b72-134">範例:</span><span class="sxs-lookup"><span data-stu-id="48b72-134">Examples:</span></span><br /><br /> <span data-ttu-id="48b72-135">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="48b72-135">Server=MyServer</span></span><br /><br /> <span data-ttu-id="48b72-136">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="48b72-136">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="48b72-137">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="48b72-137">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
   |<span data-ttu-id="48b72-138">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="48b72-138">**/Database**</span></span>|<span data-ttu-id="48b72-139">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="48b72-139">Name of the BizTalk Management database.</span></span> <span data-ttu-id="48b72-140">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="48b72-140">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48b72-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48b72-141">See Also</span></span>  
 <span data-ttu-id="48b72-142">[管理前置和後置處理指令碼](../core/managing-pre-and-post-processing-scripts.md) </span><span class="sxs-lookup"><span data-stu-id="48b72-142">[Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md) </span></span>  
 [<span data-ttu-id="48b72-143">RemoveResource 命令</span><span class="sxs-lookup"><span data-stu-id="48b72-143">RemoveResource Command</span></span>](../core/removeresource-command.md)