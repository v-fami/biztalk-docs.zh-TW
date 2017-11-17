---
title: "如何將 BAM 成品新增至應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, definition files [BAM]
- BAM, applications
- managing [applications], definition files [BAM]
- definition files [BAM], managing
ms.assetid: 86f19030-e510-4527-ba74-10498c361c00
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b4a55141b2e5cfbc527dd386c9f1cbdd464dc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-bam-artifact-to-an-application"></a><span data-ttu-id="c58bf-102">如何將 BAM 成品新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="c58bf-102">How to Add a BAM Artifact to an Application</span></span>
<span data-ttu-id="c58bf-103">本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列，將 BAM 成品新增至 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c58bf-103">This topic describes how to use the BizTalk Server Administration console or the command line to add a BAM artifact to a BizTalk application.</span></span> <span data-ttu-id="c58bf-104">新增 BAM 定義檔案時，不會一併部署 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="c58bf-104">Adding a BAM definition file does not deploy the BAM definition.</span></span> <span data-ttu-id="c58bf-105">當匯入應用程式 .msi 檔案時，會部署此 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="c58bf-105">The BAM definition is deployed when the application .msi file is imported.</span></span>  
  
 <span data-ttu-id="c58bf-106">如果您想要覆寫應用程式中現有的 BAM 成品，請指定覆寫選項。</span><span class="sxs-lookup"><span data-stu-id="c58bf-106">If you want to overwrite a BAM artifact that already exists in the application, specify the overwrite option.</span></span> <span data-ttu-id="c58bf-107">現有的 BAM 成品具有相同的檔案名稱與您想要加入時才需要覆寫選項。</span><span class="sxs-lookup"><span data-stu-id="c58bf-107">The overwrite option is required only when the existing BAM artifact has the same file name as the one you want to add.</span></span> <span data-ttu-id="c58bf-108">如果未指定，而且 BAM 成品已經存在於相同的檔案名稱與所新增的應用程式，新增作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c58bf-108">If not specified, and BAM artifact already exists in the application with the same file name as the one being added, the add operation will fail.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c58bf-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="c58bf-109">Prerequisites</span></span>  
 <span data-ttu-id="c58bf-110">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c58bf-110">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="c58bf-111">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c58bf-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-add-a-bam-artifact-to-an-application"></a><span data-ttu-id="c58bf-112">新增 BAM 成品至應用程式</span><span class="sxs-lookup"><span data-stu-id="c58bf-112">To add a BAM artifact to an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="c58bf-113">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="c58bf-113">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="c58bf-114">按一下**啟動**，按一下  **Al 程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="c58bf-114">Click **Start**, click **Al Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="c58bf-115">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]展開 BizTalk 群組、 展開 應用程式，，然後展開您要加入 BAM 成品檔案的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c58bf-115">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk Group, expand Applications, and then expand the application to which you want to add a BAM artifact file.</span></span>  
  
3.  <span data-ttu-id="c58bf-116">以滑鼠右鍵按一下**資源**資料夾，指向**新增**，然後按一下 **資源**。</span><span class="sxs-lookup"><span data-stu-id="c58bf-116">Right-click the **Resources** folder, point to **Add**, and then click **Resources**.</span></span>  
  
4.  <span data-ttu-id="c58bf-117">按一下**新增**選取 BAM 成品的檔案，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="c58bf-117">Click **Add**, select the file of the BAM artifact, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="c58bf-118">在**檔案類型**下拉式清單中，選取**system.biztalk: bam**。</span><span class="sxs-lookup"><span data-stu-id="c58bf-118">In the **File type** drop-down list, select **System.BizTalk:BAM**.</span></span>  
  
6.  <span data-ttu-id="c58bf-119">在**目的地**，輸入從.msi 檔案，包括檔案名稱安裝應用程式時複製成品檔案之位置的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c58bf-119">In **Destination**, type the full path of the location where the artifact file is to be copied when the application is installed from the .msi file, including the file name.</span></span> <span data-ttu-id="c58bf-120">如果未提供此路徑，安裝期間就不會將檔案複製到本機檔案系統，以致安裝期間無法將元件寫入 Windows 登錄。</span><span class="sxs-lookup"><span data-stu-id="c58bf-120">If this path is not provided, the file is not copied to the local file system during installation, but it will be deployed when the application .msi file is imported.</span></span>  
  
     <span data-ttu-id="c58bf-121">範例： **C:\My Applications\MyBAMfile.xml**</span><span class="sxs-lookup"><span data-stu-id="c58bf-121">Example: **C:\My Applications\MyBAMfile.xml**</span></span>  
  
7.  <span data-ttu-id="c58bf-122">完成後，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c58bf-122">When finished, click **OK**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="c58bf-123">使用命令列</span><span class="sxs-lookup"><span data-stu-id="c58bf-123">Using the command line</span></span>  
  
1.  <span data-ttu-id="c58bf-124">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c58bf-124">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="c58bf-125">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="c58bf-125">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="c58bf-126">**BTSTask AddResource** [**/ApplicationName:***值*] **/Type:System.BizTalk:Bam** [**/覆寫**] **/Source:***值*[**/Destination:***值*] [**/Server:** *值*] [**/database:***值*]</span><span class="sxs-lookup"><span data-stu-id="c58bf-126">**BTSTask AddResource** [**/ApplicationName:***value*] **/Type:System.BizTalk:Bam** [**/Overwrite**] **/Source:***value* [**/Destination:***value*] [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="c58bf-127">範例：</span><span class="sxs-lookup"><span data-stu-id="c58bf-127">Example:</span></span>  
  
     <span data-ttu-id="c58bf-128">**BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:Bam / 覆寫 /Source:"C:\Source BAMfiles\MyBAMfile.xml"/Destination:"%BTADInstallDir%\BAMfiles\MyBAMfile.xml"/Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span><span class="sxs-lookup"><span data-stu-id="c58bf-128">**BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Bam /Overwrite /Source:"C:\Source BAMfiles\MyBAMfile.xml" /Destination:"%BTADInstallDir%\ BAMfiles\MyBAMfile.xml" /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span></span>  
  
    |<span data-ttu-id="c58bf-129">參數</span><span class="sxs-lookup"><span data-stu-id="c58bf-129">Parameter</span></span>|<span data-ttu-id="c58bf-130">值</span><span class="sxs-lookup"><span data-stu-id="c58bf-130">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="c58bf-131">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="c58bf-131">**/ApplicationName**</span></span>|<span data-ttu-id="c58bf-132">加入 BAM 成品的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="c58bf-132">Name of the BizTalk application to which to add the BAM artifact.</span></span> <span data-ttu-id="c58bf-133">若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c58bf-133">If the application name is not specified, the default BizTalk application for the group is used.</span></span> <span data-ttu-id="c58bf-134">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="c58bf-134">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="c58bf-135">**/ 類型**</span><span class="sxs-lookup"><span data-stu-id="c58bf-135">**/Type**</span></span>|<span data-ttu-id="c58bf-136">**System.biztalk: bam** （此值不區分大小寫）。</span><span class="sxs-lookup"><span data-stu-id="c58bf-136">**System.BizTalk:Bam** (This value is not case-sensitive.)</span></span>|  
    |<span data-ttu-id="c58bf-137">**/ 覆寫**</span><span class="sxs-lookup"><span data-stu-id="c58bf-137">**/Overwrite**</span></span>|<span data-ttu-id="c58bf-138">覆寫現有 BAM 成品的選項。</span><span class="sxs-lookup"><span data-stu-id="c58bf-138">Option to overwrite an existing BAM artifact.</span></span> <span data-ttu-id="c58bf-139">若未指定此選項，且應用程式中現有的 BAM 成品與所新增之 BAM 成品同檔名，則 AddResource 作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c58bf-139">If not specified, and a BAM artifact already exists in the application that has the same file name as the BAM artifact being added, the AddResource operation fails.</span></span>|  
    |<span data-ttu-id="c58bf-140">**/ 來源**</span><span class="sxs-lookup"><span data-stu-id="c58bf-140">**/Source**</span></span>|<span data-ttu-id="c58bf-141">BAM 成品檔案的完整路徑 (包含檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="c58bf-141">Full path of the BAM artifact file, including the file name.</span></span> <span data-ttu-id="c58bf-142">如果路徑包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="c58bf-142">If the path includes spaces, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="c58bf-143">**/ 目的地**</span><span class="sxs-lookup"><span data-stu-id="c58bf-143">**/Destination**</span></span>|<span data-ttu-id="c58bf-144">從 .msi 檔案安裝應用程式時，BAM 成品檔案之複製目的位置的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c58bf-144">Full path of the location where the BAM artifact file is to be copied when the application is installed from the .msi file.</span></span> <span data-ttu-id="c58bf-145">如果不提供，安裝期間就不會將檔案複製到本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="c58bf-145">If not provided, the file is not copied to the local file system during installation.</span></span> <span data-ttu-id="c58bf-146">如果路徑包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="c58bf-146">If the path includes spaces, you must enclose it in double quotation marks (").</span></span> <span data-ttu-id="c58bf-147">您可以在路徑中使用 %BTADInstallDir% 環境變數來指定應用程式安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="c58bf-147">You can use the environment variable %BTADInstallDir% in the path to specify the application installation folder.</span></span>|  
    |<span data-ttu-id="c58bf-148">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="c58bf-148">**/Server**</span></span>|<span data-ttu-id="c58bf-149">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="c58bf-149">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="c58bf-150">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="c58bf-150">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="c58bf-151">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="c58bf-151">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="c58bf-152">範例:</span><span class="sxs-lookup"><span data-stu-id="c58bf-152">Examples:</span></span><br /><br /> <span data-ttu-id="c58bf-153">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="c58bf-153">Server=MyServer</span></span><br /><br /> <span data-ttu-id="c58bf-154">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="c58bf-154">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="c58bf-155">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="c58bf-155">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="c58bf-156">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="c58bf-156">**/Database**</span></span>|<span data-ttu-id="c58bf-157">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="c58bf-157">Name of the BizTalk Management database.</span></span> <span data-ttu-id="c58bf-158">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="c58bf-158">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c58bf-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c58bf-159">See Also</span></span>  
 <span data-ttu-id="c58bf-160">[管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md) </span><span class="sxs-lookup"><span data-stu-id="c58bf-160">[Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md) </span></span>  
 <span data-ttu-id="c58bf-161">[AddResource 命令： BAM 成品](../core/addresource-command-bam-artifact.md) </span><span class="sxs-lookup"><span data-stu-id="c58bf-161">[AddResource Command: BAM Artifact](../core/addresource-command-bam-artifact.md) </span></span>  
 <span data-ttu-id="c58bf-162">[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="c58bf-162">[Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="c58bf-163">如何匯入 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="c58bf-163">How to Import a BizTalk Application</span></span>](../core/how-to-import-a-biztalk-application.md)