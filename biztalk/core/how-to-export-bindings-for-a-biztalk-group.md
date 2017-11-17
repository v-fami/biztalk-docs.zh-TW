---
title: "如何匯出 BizTalk 群組的繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, exporting
- groups, bindings
- groups, exporting
ms.assetid: 51955266-f87f-41c9-992c-93036b40f663
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df08f99a9e37bf1a4d4a794c17d483fdc381f463
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-a-biztalk-group"></a><span data-ttu-id="70775-102">如何匯出 BizTalk 群組的繫結</span><span class="sxs-lookup"><span data-stu-id="70775-102">How to Export Bindings for a BizTalk Group</span></span>
<span data-ttu-id="70775-103">本主題描述如何使用 [BizTalk Server 管理主控台] 或命令列，將 BizTalk 群組的繫結匯出到 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="70775-103">This topic describes how to use the BizTalk Server Administration console or the command line to export the bindings for a BizTalk group to an .xml file.</span></span> <span data-ttu-id="70775-104">您可以再這些繫結匯入到 BizTalk 群組或應用程式中所述[如何匯入到 BizTalk 群組的繫結](../core/how-to-import-bindings-into-a-biztalk-group.md)和[如何匯入到 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="70775-104">You can then import these bindings into a BizTalk group or application, as described in [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md) and [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md).</span></span> <span data-ttu-id="70775-105">如需有關如何使用繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="70775-105">For more information about using binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70775-106">無論是否有指定這個選項，匯出群組的繫結必定都會匯出全域合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="70775-106">Exporting bindings for a group always exports global party information, whether this option is specified or not.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="70775-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="70775-107">Prerequisites</span></span>  
 <span data-ttu-id="70775-108">若要執行本主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk 操作員」群組的成員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="70775-108">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="70775-109">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="70775-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-export-bindings-for-a-biztalk-group"></a><span data-ttu-id="70775-110">若要匯出 BizTalk 群組的繫結</span><span class="sxs-lookup"><span data-stu-id="70775-110">To export bindings for a BizTalk group</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="70775-111">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="70775-111">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="70775-112">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="70775-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="70775-113">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 以滑鼠右鍵按一下**應用程式**，指向 **匯出**，然後按一下 **繫結**。</span><span class="sxs-lookup"><span data-stu-id="70775-113">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, right-click **Applications**, point to **Export**, and then click **Bindings**.</span></span>  
  
3.  <span data-ttu-id="70775-114">在 [匯出繫結] 頁面中**匯出至檔案**，輸入要匯出繫結的.xml 檔案的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="70775-114">On the Export Bindings page, in **Export to file**, type the absolute path of the .xml file to which to export the bindings.</span></span>  
  
     <span data-ttu-id="70775-115">範例： C:\Bindings\Group1Bindings_Staging1.xml</span><span class="sxs-lookup"><span data-stu-id="70775-115">Example: C:\Bindings\Group1Bindings_Staging1.xml</span></span>  
  
4.  <span data-ttu-id="70775-116">請確認**從目前的群組匯出所有繫結**已選取，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="70775-116">Ensure that **Export all bindings from the current group** is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="70775-117">繫結就會匯出到您所指定位置中的 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="70775-117">The bindings are exported to an .xml file in the location that you specified.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="70775-118">使用命令列</span><span class="sxs-lookup"><span data-stu-id="70775-118">Using the command line</span></span>  
  
1.  <span data-ttu-id="70775-119">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="70775-119">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="70775-120">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="70775-120">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="70775-121">**BTSTask ExportBindings /Destination:** *值* **/GroupLevel** [**/GlobalParties**] [**/Server:** *值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="70775-121">**BTSTask ExportBindings /Destination:** *value* **/GroupLevel** [**/GlobalParties**] [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="70775-122">範例：</span><span class="sxs-lookup"><span data-stu-id="70775-122">Example:</span></span>  
  
     <span data-ttu-id="70775-123">**BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml"GroupLevel /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span><span class="sxs-lookup"><span data-stu-id="70775-123">**BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml" /GroupLevel /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span></span>  
  
    |<span data-ttu-id="70775-124">參數</span><span class="sxs-lookup"><span data-stu-id="70775-124">Parameter</span></span>|<span data-ttu-id="70775-125">值</span><span class="sxs-lookup"><span data-stu-id="70775-125">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="70775-126">**/ 目的地**</span><span class="sxs-lookup"><span data-stu-id="70775-126">**/Destination**</span></span>|<span data-ttu-id="70775-127">要建立的繫結檔案完整路徑 (包含檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="70775-127">Full path of the binding file to create, including the file name.</span></span> <span data-ttu-id="70775-128">如果具有相同路徑的繫結檔案已存在，將會覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="70775-128">If a binding file having the same path already exists, it is overwritten.</span></span> <span data-ttu-id="70775-129">如果路徑中有空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="70775-129">If there are spaces in the path, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="70775-130">**/ GroupLevel**</span><span class="sxs-lookup"><span data-stu-id="70775-130">**/GroupLevel**</span></span>|<span data-ttu-id="70775-131">如果有指定，將匯出目前 BizTalk 群組中的所有繫結。</span><span class="sxs-lookup"><span data-stu-id="70775-131">When specified, all bindings in the current BizTalk group are exported.</span></span>|  
    |<span data-ttu-id="70775-132">**/ GlobalParties**</span><span class="sxs-lookup"><span data-stu-id="70775-132">**/GlobalParties**</span></span>|<span data-ttu-id="70775-133">如果有指定，將匯出群組的全域合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="70775-133">When specified, exports global party information for the group.</span></span>|  
    |<span data-ttu-id="70775-134">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="70775-134">**/Server**</span></span>|<span data-ttu-id="70775-135">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="70775-135">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="70775-136">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="70775-136">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="70775-137">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="70775-137">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="70775-138">範例:</span><span class="sxs-lookup"><span data-stu-id="70775-138">Examples:</span></span><br /><br /> <span data-ttu-id="70775-139">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="70775-139">Server=MyServer</span></span><br /><br /> <span data-ttu-id="70775-140">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="70775-140">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="70775-141">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="70775-141">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="70775-142">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="70775-142">**/Database**</span></span>|<span data-ttu-id="70775-143">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="70775-143">Name of the BizTalk Management database.</span></span> <span data-ttu-id="70775-144">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="70775-144">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70775-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70775-145">See Also</span></span>  
 <span data-ttu-id="70775-146">[匯出繫結](../core/exporting-bindings6.md) </span><span class="sxs-lookup"><span data-stu-id="70775-146">[Exporting Bindings](../core/exporting-bindings6.md) </span></span>  
 <span data-ttu-id="70775-147">[ExportBindings 命令](../core/exportbindings-command.md) </span><span class="sxs-lookup"><span data-stu-id="70775-147">[ExportBindings Command](../core/exportbindings-command.md) </span></span>  
 [<span data-ttu-id="70775-148">匯入 BizTalk 應用程式、 繫結和原則</span><span class="sxs-lookup"><span data-stu-id="70775-148">Importing BizTalk Applications, Bindings, and Policies</span></span>](../core/importing-biztalk-applications-bindings-and-policies.md)