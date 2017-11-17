---
title: "如何匯出 BizTalk 應用程式的繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, exportings
- applications, exporting
- applications, bindings
ms.assetid: 700d2781-480b-42ed-a313-1a67a7406369
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d08b97146fd327619a97e304a4167c9b62871c8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-a-biztalk-application"></a><span data-ttu-id="e121e-102">如何匯出 BizTalk 應用程式的繫結</span><span class="sxs-lookup"><span data-stu-id="e121e-102">How to Export Bindings for a BizTalk Application</span></span>
<span data-ttu-id="e121e-103">本主題說明如何使用 BizTalk Server 管理主控台或命令列，將 BizTalk 應用程式的繫結匯出到 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="e121e-103">This topic describes how to use the BizTalk Server Administration console or the command line export the bindings for a BizTalk application to an .xml file.</span></span> <span data-ttu-id="e121e-104">接著，您可以將繫結檔案匯入到另一個應用程式，以匯入的同名繫結覆寫應用程式中目前的繫結。</span><span class="sxs-lookup"><span data-stu-id="e121e-104">You can then import the binding file into another application, which overwrites the current bindings in the application with the imported bindings of the same name.</span></span> <span data-ttu-id="e121e-105">如需詳細資訊，請參閱[如何匯入到 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e121e-105">For more information, see [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md).</span></span> <span data-ttu-id="e121e-106">如需有關如何使用繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="e121e-106">For more information about using binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e121e-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="e121e-107">Prerequisites</span></span>  
 <span data-ttu-id="e121e-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk Server 操作員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="e121e-108">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators or BizTalk Server Operators group.</span></span> <span data-ttu-id="e121e-109">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e121e-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-export-bindings-for-a-biztalk-application"></a><span data-ttu-id="e121e-110">若要匯出 BizTalk 應用程式的繫結</span><span class="sxs-lookup"><span data-stu-id="e121e-110">To export bindings for a BizTalk application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="e121e-111">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="e121e-111">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="e121e-112">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e121e-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e121e-113">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 展開 [BizTalk 群組]，然後再展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e121e-113">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="e121e-114">以滑鼠右鍵按一下您想要匯出其繫的結指向應用程式**匯出**，然後按一下 **繫結**。</span><span class="sxs-lookup"><span data-stu-id="e121e-114">Right-click the application whose bindings you want to export, point to **Export**, and then click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="e121e-115">在 [匯出繫結] 頁面中**匯出至檔案**，輸入要匯出繫結的.xml 檔案的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="e121e-115">On the Export Bindings page, in **Export to file**, type the absolute path of the .xml file to which to export the bindings.</span></span>  
  
     <span data-ttu-id="e121e-116">範例： **C:\Bindings\Application1Bindings_Staging1.xml**</span><span class="sxs-lookup"><span data-stu-id="e121e-116">Example: **C:\Bindings\Application1Bindings_Staging1.xml**</span></span>  
  
5.  <span data-ttu-id="e121e-117">請確認**從目前的應用程式匯出所有繫結**已選取，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e121e-117">Ensure that **Export all bindings from the current application** is selected, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="e121e-118">若要匯出群組的所有合作對象資訊，請選取**匯出全域合作對象資訊**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e121e-118">To export all party information for the group, select the **Export Global Party information** check box.</span></span>  
  
     <span data-ttu-id="e121e-119">繫結就會匯出到您所指定位置中的 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="e121e-119">The bindings are exported into an .xml file in the location that you specified.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="e121e-120">使用命令列</span><span class="sxs-lookup"><span data-stu-id="e121e-120">Using the command line</span></span>  
  
1.  <span data-ttu-id="e121e-121">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e121e-121">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="e121e-122">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="e121e-122">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="e121e-123">**BTSTask ExportBindings /Destination:** *值*[**/ApplicationName:***值*] [**/GlobalParties**] [**/Server:***值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="e121e-123">**BTSTask ExportBindings /Destination:** *value* [**/ApplicationName:***value*] [**/GlobalParties**] [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="e121e-124">範例：</span><span class="sxs-lookup"><span data-stu-id="e121e-124">Example:</span></span>  
  
     <span data-ttu-id="e121e-125">**BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml"/applicationname: myapplication /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span><span class="sxs-lookup"><span data-stu-id="e121e-125">**BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml" /ApplicationName:MyApplication /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span></span>  
  
    |<span data-ttu-id="e121e-126">參數</span><span class="sxs-lookup"><span data-stu-id="e121e-126">Parameter</span></span>|<span data-ttu-id="e121e-127">值</span><span class="sxs-lookup"><span data-stu-id="e121e-127">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="e121e-128">**/ 目的地**</span><span class="sxs-lookup"><span data-stu-id="e121e-128">**/Destination**</span></span>|<span data-ttu-id="e121e-129">要建立的繫結檔案完整路徑 (包含檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="e121e-129">Full path of the binding file to create, including the file name.</span></span> <span data-ttu-id="e121e-130">如果具有相同路徑的繫結檔案已存在，將會覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="e121e-130">If a binding file having the same path already exists, it is overwritten.</span></span> <span data-ttu-id="e121e-131">如果路徑中有空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="e121e-131">If there are spaces in the path, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="e121e-132">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="e121e-132">**/ApplicationName**</span></span>|<span data-ttu-id="e121e-133">要匯出其繫結的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="e121e-133">Name of the application from which to export bindings.</span></span> <span data-ttu-id="e121e-134">應用程式必須存在。</span><span class="sxs-lookup"><span data-stu-id="e121e-134">The application must exist.</span></span> <span data-ttu-id="e121e-135">若要確認應用程式名稱，您可以使用**ListApps**命令中所述[ListApps 命令](../core/listapps-command.md)。</span><span class="sxs-lookup"><span data-stu-id="e121e-135">To verify the application name, you can use the **ListApps** command, as described in [ListApps Command](../core/listapps-command.md).</span></span> <span data-ttu-id="e121e-136">如果沒有指定這個參數，將會使用預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e121e-136">If this parameter is not specified, the default BizTalk application is used.</span></span> <span data-ttu-id="e121e-137">如果名稱中有空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="e121e-137">If there are spaces in the name, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="e121e-138">**/ GlobalParties**</span><span class="sxs-lookup"><span data-stu-id="e121e-138">**/GlobalParties**</span></span>|<span data-ttu-id="e121e-139">如果有指定，將匯出群組的全域合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="e121e-139">When specified, exports global party information for the group.</span></span>|  
    |<span data-ttu-id="e121e-140">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="e121e-140">**/Server**</span></span>|<span data-ttu-id="e121e-141">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="e121e-141">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="e121e-142">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e121e-142">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="e121e-143">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="e121e-143">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="e121e-144">範例:</span><span class="sxs-lookup"><span data-stu-id="e121e-144">Examples:</span></span><br /><br /> <span data-ttu-id="e121e-145">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="e121e-145">Server=MyServer</span></span><br /><br /> <span data-ttu-id="e121e-146">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="e121e-146">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="e121e-147">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="e121e-147">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="e121e-148">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="e121e-148">**/Database**</span></span>|<span data-ttu-id="e121e-149">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="e121e-149">Name of the BizTalk Management database.</span></span> <span data-ttu-id="e121e-150">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="e121e-150">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e121e-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e121e-151">See Also</span></span>  
 <span data-ttu-id="e121e-152">[匯出繫結](../core/exporting-bindings6.md) </span><span class="sxs-lookup"><span data-stu-id="e121e-152">[Exporting Bindings](../core/exporting-bindings6.md) </span></span>  
 <span data-ttu-id="e121e-153">[ExportBindings 命令](../core/exportbindings-command.md) </span><span class="sxs-lookup"><span data-stu-id="e121e-153">[ExportBindings Command](../core/exportbindings-command.md) </span></span>  
 [<span data-ttu-id="e121e-154">匯入 BizTalk 應用程式、 繫結和原則</span><span class="sxs-lookup"><span data-stu-id="e121e-154">Importing BizTalk Applications, Bindings, and Policies</span></span>](../core/importing-biztalk-applications-bindings-and-policies.md)