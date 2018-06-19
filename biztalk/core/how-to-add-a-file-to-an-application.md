---
title: 如何將檔案新增至應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [applications], adding files
- files, adding to applications
- managing [resources], adding files
ms.assetid: 6665b946-113a-4026-a0a3-6b67ede4b689
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4493eafe2bba4e1203a230180024e0e5a8a2ce08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247734"
---
# <a name="how-to-add-a-file-to-an-application"></a><span data-ttu-id="048e8-102">如何新增檔案至應用程式</span><span class="sxs-lookup"><span data-stu-id="048e8-102">How to Add a File to an Application</span></span>
<span data-ttu-id="048e8-103">本主題說明如何使用「BizTalk Server 管理」主控台或命令列，將檔案新增至 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="048e8-103">This topic describes how to use the BizTalk Server Administration console or the command line to add a file to a BizTalk application.</span></span> <span data-ttu-id="048e8-104">在安裝應用程式時，新增至應用程式的檔案會複製到安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="048e8-104">Files that you add to your application are copied to the installation folder when the application is installed.</span></span> <span data-ttu-id="048e8-105">檔案也可以匯出至應用程式的 .msi 檔案中，並且隨著應用程式移至不同的部署環境。</span><span class="sxs-lookup"><span data-stu-id="048e8-105">Files can also can be exported into the application's .msi file and moved to different deployment environments with the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="048e8-106">如需新增讀我檔案的指示，請參閱[如何連結到讀我檔案](../core/how-to-link-to-a-readme-file.md)。</span><span class="sxs-lookup"><span data-stu-id="048e8-106">For instructions on adding a Readme file, see [How to Link to a Readme File](../core/how-to-link-to-a-readme-file.md).</span></span>  
  
 <span data-ttu-id="048e8-107">如果您想要覆寫應用程式中現有的檔案，請指定 [覆寫] 選項。</span><span class="sxs-lookup"><span data-stu-id="048e8-107">If you want to overwrite a file that already exists in the application, specify the Overwrite option.</span></span> <span data-ttu-id="048e8-108">只有在兩個檔案都具有相同的名稱時，覆寫選項才有作用。</span><span class="sxs-lookup"><span data-stu-id="048e8-108">The overwrite option only works when both files have the same file name.</span></span> <span data-ttu-id="048e8-109">若未指定此選項，而且應用程式中現有的檔案與所加入的檔案同名，新增作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="048e8-109">If not specified, and a file already exists in the application with the same file name as the one being added, the add operation will fail.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="048e8-110">不同於其他的成品類型，BizTalk 群組可包含一個以上的同名檔案。</span><span class="sxs-lookup"><span data-stu-id="048e8-110">Unlike some other types of artifacts, you can have more than one file having the same file name in a BizTalk group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="048e8-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="048e8-111">Prerequisites</span></span>  
 <span data-ttu-id="048e8-112">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="048e8-112">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="048e8-113">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="048e8-113">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-add-a-file-to-an-application"></a><span data-ttu-id="048e8-114">若要新增檔案至應用程式</span><span class="sxs-lookup"><span data-stu-id="048e8-114">To add a file to an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="048e8-115">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="048e8-115">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="048e8-116">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="048e8-116">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="048e8-117">在主控台樹狀目錄中，依序展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]] 和包含您想要新增檔案之應用程式的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="048e8-117">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and the BizTalk Group containing the application to which you want to add the file.</span></span>  
  
3.  <span data-ttu-id="048e8-118">展開 [應用程式]，再展開您想要在其中新增檔案的應用程式。</span><span class="sxs-lookup"><span data-stu-id="048e8-118">Expand Applications and the application to which you want to add a file.</span></span>  
  
4.  <span data-ttu-id="048e8-119">以滑鼠右鍵按一下**資源**資料夾，指向**新增**，然後按一下 **資源**。</span><span class="sxs-lookup"><span data-stu-id="048e8-119">Right-click the **Resources** folder, point to **Add**, and then click **Resources**.</span></span>  
  
5.  <span data-ttu-id="048e8-120">按一下**新增**，並選取檔案，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="048e8-120">Click **Add**, select the file, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="048e8-121">在**檔案類型**下拉式清單中，選取**system.biztalk: file**。</span><span class="sxs-lookup"><span data-stu-id="048e8-121">In the **File type** drop-down list, select **System.BizTalk:File**.</span></span>  
  
7.  <span data-ttu-id="048e8-122">在**目的地**，輸入從.msi 檔案，包括檔案名稱安裝應用程式時複製檔案之位置的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="048e8-122">In **Destination**, type the full path of the location where the file is to be copied when the application is installed from the .msi file, including the file name.</span></span> <span data-ttu-id="048e8-123">預設值為應用程式安裝資料夾 %BTAD_InstallDir%。</span><span class="sxs-lookup"><span data-stu-id="048e8-123">The default is %BTAD_InstallDir%, the application installation folder.</span></span> <span data-ttu-id="048e8-124">如果未提供此路徑，安裝期間就不會將組件檔案複製到本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="048e8-124">If this path is not provided, the file is not copied to the local file system during installation.</span></span>  
  
8.  <span data-ttu-id="048e8-125">完成後，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="048e8-125">When finished, click **OK**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="048e8-126">使用命令列</span><span class="sxs-lookup"><span data-stu-id="048e8-126">Using the command line</span></span>  
  
1.  <span data-ttu-id="048e8-127">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="048e8-127">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="048e8-128">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="048e8-128">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="048e8-129">**BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:File** [**/覆寫**] **/Source:***值*[**/Destination:***值*] [**/Server:** *值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="048e8-129">**BTSTask AddResource** [**/ApplicationName:***value*] **/Type:System.BizTalk:File** [**/Overwrite**] **/Source:***value* [**/Destination:***value*] [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="048e8-130">範例：</span><span class="sxs-lookup"><span data-stu-id="048e8-130">Example:</span></span>  
  
     <span data-ttu-id="048e8-131">**BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:File / 覆寫 /Source:"C:\Source Files\File.txt"/Destination:"C:\New Files\File.txt"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span><span class="sxs-lookup"><span data-stu-id="048e8-131">**BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:File /Overwrite /Source:"C:\Source Files\File.txt" /Destination:"C:\New Files\File.txt" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span></span>  
  
    |<span data-ttu-id="048e8-132">參數</span><span class="sxs-lookup"><span data-stu-id="048e8-132">Parameter</span></span>|<span data-ttu-id="048e8-133">值</span><span class="sxs-lookup"><span data-stu-id="048e8-133">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="048e8-134">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="048e8-134">**/ApplicationName**</span></span>|<span data-ttu-id="048e8-135">加入檔案的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="048e8-135">Name of the BizTalk application to which to add the file.</span></span> <span data-ttu-id="048e8-136">如果沒有指定應用程式名稱，將會使用預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="048e8-136">If the application name is not specified, the default BizTalk application is used.</span></span> <span data-ttu-id="048e8-137">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="048e8-137">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="048e8-138">**/ 類型**</span><span class="sxs-lookup"><span data-stu-id="048e8-138">**/Type**</span></span>|<span data-ttu-id="048e8-139">**System.biztalk: file** （此值不區分大小寫）。</span><span class="sxs-lookup"><span data-stu-id="048e8-139">**System.BizTalk:File** (This value is not case-sensitive.)</span></span>|  
    |<span data-ttu-id="048e8-140">**/ 覆寫**</span><span class="sxs-lookup"><span data-stu-id="048e8-140">**/Overwrite**</span></span>|<span data-ttu-id="048e8-141">此選項指定更新現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="048e8-141">Option to update an existing file.</span></span> <span data-ttu-id="048e8-142">若未指定此選項，且應用程式中現有的檔案與所加入的檔案同名，AddResource 作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="048e8-142">If not specified, and a file already exists in the application that has the same name as the file being added, the AddResource operation fails.</span></span>|  
    |<span data-ttu-id="048e8-143">**/ 來源**</span><span class="sxs-lookup"><span data-stu-id="048e8-143">**/Source**</span></span>|<span data-ttu-id="048e8-144">檔案的完整路徑 (包含檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="048e8-144">Full path of the file, including the file name.</span></span> <span data-ttu-id="048e8-145">如果路徑包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="048e8-145">If the path includes spaces, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="048e8-146">**/ 目的地**</span><span class="sxs-lookup"><span data-stu-id="048e8-146">**/Destination**</span></span>|<span data-ttu-id="048e8-147">從 .msi 檔案安裝應用程式時，檔案之複製目的位置的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="048e8-147">Full path of the location where the file is to be copied when the application is installed from the .msi file.</span></span> <span data-ttu-id="048e8-148">如果路徑包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="048e8-148">If the path includes spaces, you must enclose it in double quotation marks (").</span></span> <span data-ttu-id="048e8-149">如果不提供，安裝期間就不會將檔案複製到本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="048e8-149">If not provided, the file is not copied to the local file system during installation.</span></span>|  
    |<span data-ttu-id="048e8-150">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="048e8-150">**/Server**</span></span>|<span data-ttu-id="048e8-151">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="048e8-151">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="048e8-152">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="048e8-152">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="048e8-153">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="048e8-153">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="048e8-154">範例:</span><span class="sxs-lookup"><span data-stu-id="048e8-154">Examples:</span></span><br /><br /> <span data-ttu-id="048e8-155">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="048e8-155">Server=MyServer</span></span><br /><br /> <span data-ttu-id="048e8-156">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="048e8-156">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="048e8-157">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="048e8-157">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="048e8-158">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="048e8-158">**/Database**</span></span>|<span data-ttu-id="048e8-159">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="048e8-159">Name of the BizTalk Management database.</span></span> <span data-ttu-id="048e8-160">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="048e8-160">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="048e8-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="048e8-161">See Also</span></span>  
 <span data-ttu-id="048e8-162">[管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md) </span><span class="sxs-lookup"><span data-stu-id="048e8-162">[Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md) </span></span>  
 <span data-ttu-id="048e8-163">[AddResource 命令： 檔案](../core/addresource-command-file.md) </span><span class="sxs-lookup"><span data-stu-id="048e8-163">[AddResource Command: File](../core/addresource-command-file.md) </span></span>  
 [<span data-ttu-id="048e8-164">建立和修改 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="048e8-164">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)