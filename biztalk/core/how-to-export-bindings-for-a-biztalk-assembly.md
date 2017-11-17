---
title: "如何匯出 BizTalk 組件的繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies, bindings
- assemblies, exporting
- exporting, assemblies
ms.assetid: 7e37348d-5fa5-43cc-b3c0-2d8cb6a8f394
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64086cc8e54d89180d3c95268c78bc53e5ec9f55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-a-biztalk-assembly"></a><span data-ttu-id="41a0f-102">如何匯出 BizTalk 組件的繫結</span><span class="sxs-lookup"><span data-stu-id="41a0f-102">How to Export Bindings for a BizTalk Assembly</span></span>
<span data-ttu-id="41a0f-103">本主題說明如何使用 BizTalk Server 管理主控台或命令列，將 BizTalk 組件的繫結匯出至 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="41a0f-103">This topic describes how to use the BizTalk Server Administration console or the command line to export the bindings for a BizTalk assembly to an .xml file.</span></span> <span data-ttu-id="41a0f-104">接著您可以將這些繫結匯入至 BizTalk 應用程式，這時匯入的同名繫結會覆寫現有繫結。</span><span class="sxs-lookup"><span data-stu-id="41a0f-104">You can then import these bindings into a BizTalk application, which overwrites existing bindings with the imported bindings of the same name.</span></span> <span data-ttu-id="41a0f-105">在更新組件之前，您可能想要匯出其繫結，以便在更新後匯入繫結，重新套用它們。</span><span class="sxs-lookup"><span data-stu-id="41a0f-105">You might want to export the bindings for an assembly before you update it, so that you can import the bindings after you update it to reapply them.</span></span> <span data-ttu-id="41a0f-106">如需更新應用程式和組件的詳細資訊，請參閱[更新 BizTalk 應用程式](../core/updating-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="41a0f-106">For more information about updating applications and assemblies, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).</span></span> <span data-ttu-id="41a0f-107">如需有關如何使用繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="41a0f-107">For more information about using binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="41a0f-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="41a0f-108">Prerequisites</span></span>  
 <span data-ttu-id="41a0f-109">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk Server 操作員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="41a0f-109">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators or BizTalk Server Operators group.</span></span> <span data-ttu-id="41a0f-110">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="41a0f-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-export-bindings-for-a-biztalk-assembly"></a><span data-ttu-id="41a0f-111">若要匯出 BizTalk 組件的繫結</span><span class="sxs-lookup"><span data-stu-id="41a0f-111">To export bindings for a BizTalk assembly</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="41a0f-112">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="41a0f-112">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="41a0f-113">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="41a0f-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="41a0f-114">在主控台樹狀結構中，依序展開 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、BizTalk 群組和 [應用程式]。</span><span class="sxs-lookup"><span data-stu-id="41a0f-114">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then expand Applications.</span></span>  
  
3.  <span data-ttu-id="41a0f-115">以滑鼠右鍵按一下包含組件的應用程式，指向**匯出**，然後按一下 **繫結**。</span><span class="sxs-lookup"><span data-stu-id="41a0f-115">Right-click the application containing the assembly, point to **Export**, and then click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="41a0f-116">在 [匯出繫結] 頁面中**匯出至檔案**，輸入要匯出繫結的.xml 檔案的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="41a0f-116">On the Export Bindings page, in **Export to file**, type the absolute path of the .xml file to which to export the bindings.</span></span>  
  
     <span data-ttu-id="41a0f-117">範例： **C:\Bindings\MyAssemblyBindings_Staging1.xml**</span><span class="sxs-lookup"><span data-stu-id="41a0f-117">Example: **C:\Bindings\MyAssemblyBindings_Staging1.xml**</span></span>  
  
5.  <span data-ttu-id="41a0f-118">在匯出繫結 頁面上，按一下 **匯出所選組件的繫結**，然後在**組件**，按一下 組件。</span><span class="sxs-lookup"><span data-stu-id="41a0f-118">On the Export Bindings page, click **Export bindings for the selected assembly**, and then in **Assembly**, click the assembly.</span></span>  
  
6.  <span data-ttu-id="41a0f-119">如果您要匯出的所有群組中的合作對象資訊，請選取**匯出全域合作對象資訊**。</span><span class="sxs-lookup"><span data-stu-id="41a0f-119">If you want to export all of the party information in the group, select **Export Global Party Information**.</span></span>  
  
     <span data-ttu-id="41a0f-120">繫結就會匯出到您所指定位置中的 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="41a0f-120">The bindings are exported to an .xml file in the location that you specified.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="41a0f-121">使用命令列</span><span class="sxs-lookup"><span data-stu-id="41a0f-121">Using the command line</span></span>  
  
1.  <span data-ttu-id="41a0f-122">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="41a0f-122">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="41a0f-123">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="41a0f-123">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="41a0f-124">**BTSTask ExportBindings /Destination:** *值* **/AssemblyName:** *值*[**/GlobalParties**] [**/Server:***值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="41a0f-124">**BTSTask ExportBindings /Destination:** *value* **/AssemblyName:** *value* [**/GlobalParties**] [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="41a0f-125">範例：</span><span class="sxs-lookup"><span data-stu-id="41a0f-125">Example:</span></span>  
  
     <span data-ttu-id="41a0f-126">**BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml"/AssemblyName:"ErrorHandling.ErrorHandler，Version = 1.0.0.0，Culture = neutral，PublicKeyToken = 11e921d58826420e"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span><span class="sxs-lookup"><span data-stu-id="41a0f-126">**BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml" /AssemblyName:"ErrorHandling.ErrorHandler, Version=1.0.0.0, Culture=neutral, PublicKeyToken=11e921d58826420e" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span></span>  
  
    |<span data-ttu-id="41a0f-127">參數</span><span class="sxs-lookup"><span data-stu-id="41a0f-127">Parameter</span></span>|<span data-ttu-id="41a0f-128">值</span><span class="sxs-lookup"><span data-stu-id="41a0f-128">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="41a0f-129">**/ 目的地**</span><span class="sxs-lookup"><span data-stu-id="41a0f-129">**/Destination**</span></span>|<span data-ttu-id="41a0f-130">要建立的繫結檔案完整路徑 (包含檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="41a0f-130">Full path of the binding file to create, including the file name.</span></span> <span data-ttu-id="41a0f-131">如果具有相同路徑的繫結檔案已存在，將會覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="41a0f-131">If a binding file having the same path already exists, it is overwritten.</span></span> <span data-ttu-id="41a0f-132">如果路徑中有空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="41a0f-132">If there are spaces in the path, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="41a0f-133">**/ AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="41a0f-133">**/AssemblyName**</span></span>|<span data-ttu-id="41a0f-134">要匯出其繫結的組件的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="41a0f-134">Locally unique identifier (LUID) of the assembly from which to export bindings.</span></span> <span data-ttu-id="41a0f-135">您可以使用，以取得應用程式中的成品的 Luid 清單[ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="41a0f-135">You can obtain a list of LUIDs for the artifacts in an application by using the [ListApp Command](../core/listapp-command.md).</span></span>|  
    |<span data-ttu-id="41a0f-136">**/ GlobalParties**</span><span class="sxs-lookup"><span data-stu-id="41a0f-136">**/GlobalParties**</span></span>|<span data-ttu-id="41a0f-137">如果有指定，將匯出群組的全域合作對象資訊。</span><span class="sxs-lookup"><span data-stu-id="41a0f-137">When specified, exports global pary information for the group.</span></span>|  
    |<span data-ttu-id="41a0f-138">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="41a0f-138">**/Server**</span></span>|<span data-ttu-id="41a0f-139">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="41a0f-139">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="41a0f-140">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="41a0f-140">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="41a0f-141">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="41a0f-141">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="41a0f-142">範例:</span><span class="sxs-lookup"><span data-stu-id="41a0f-142">Examples:</span></span><br /><br /> <span data-ttu-id="41a0f-143">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="41a0f-143">Server=MyServer</span></span><br /><br /> <span data-ttu-id="41a0f-144">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="41a0f-144">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="41a0f-145">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="41a0f-145">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="41a0f-146">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="41a0f-146">**/Database**</span></span>|<span data-ttu-id="41a0f-147">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="41a0f-147">Name of the BizTalk Management database.</span></span> <span data-ttu-id="41a0f-148">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="41a0f-148">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41a0f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41a0f-149">See Also</span></span>  
 <span data-ttu-id="41a0f-150">[匯出繫結](../core/exporting-bindings6.md) </span><span class="sxs-lookup"><span data-stu-id="41a0f-150">[Exporting Bindings](../core/exporting-bindings6.md) </span></span>  
 <span data-ttu-id="41a0f-151">[ExportBindings 命令](../core/exportbindings-command.md) </span><span class="sxs-lookup"><span data-stu-id="41a0f-151">[ExportBindings Command](../core/exportbindings-command.md) </span></span>  
 [<span data-ttu-id="41a0f-152">匯入 BizTalk 應用程式、 繫結和原則</span><span class="sxs-lookup"><span data-stu-id="41a0f-152">Importing BizTalk Applications, Bindings, and Policies</span></span>](../core/importing-biztalk-applications-bindings-and-policies.md)