---
title: 如何從應用程式移除.NET 組件、 憑證或其他資源成品 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual directories, deleting
- managing [.NET assemblies], deleting
- managing [applications], COM components
- managing [applications], deleting artifcats
- managing [certificates], deleting
- deleting, binding files
- binding files, deleting
- managing, COM components
- COM components, deleting
- managing [artifacts], deleting
- .NET assemblies, deleting
- deleting, virtual directories
- deleting, definitions [BAM]
- applications, .NET assemblies
- certificates, deleting
- deleting, .NET assemblies
- deleting, artifacts
- deleting, certificates
ms.assetid: b84eebac-261d-495f-80cd-ddda5bb08bef
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dce140e7adeaf6115ad2f8b2199a3a77292a953
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002919"
---
# <a name="how-to-remove-a-net-assembly-certificate-or-other-resource-artifact-from-an-application"></a><span data-ttu-id="e4938-102">如何從應用程式移除 .NET 組件、憑證或其他資源成品</span><span class="sxs-lookup"><span data-stu-id="e4938-102">How to Remove a .NET Assembly, Certificate, or Other Resource Artifact from an Application</span></span>
<span data-ttu-id="e4938-103">本主題說明如何使用 BizTalk Server 管理主控台或命令列，從 BizTalk 應用程式移除下列資源成品。</span><span class="sxs-lookup"><span data-stu-id="e4938-103">This topic describes how to use the BizTalk Server Administration console or the command line to remove the following resource artifacts from a BizTalk application.</span></span> <span data-ttu-id="e4938-104">使用本主題提供的程序可以從 BizTalk 管理資料庫移除成品，</span><span class="sxs-lookup"><span data-stu-id="e4938-104">Using the procedures in this topic removes the artifact from the BizTalk Management database.</span></span> <span data-ttu-id="e4938-105">但是不會從檔案系統、憑證存放區、Internet Information Services (IIS) 或 Windows 登錄等任何位置中，移除現有的成品。</span><span class="sxs-lookup"><span data-stu-id="e4938-105">It does not remove the artifact from the file system, certificate store, Internet Information Services (IIS), or the Windows registry, if it exists in any of these locations.</span></span> <span data-ttu-id="e4938-106">此外，如果您移除繫結檔案，繫結仍將原封不動，而只會移除繫結檔案而已。</span><span class="sxs-lookup"><span data-stu-id="e4938-106">In addition, if you remove a binding file, the bindings remain unchanged – only the binding file is removed.</span></span>  
  
- <span data-ttu-id="e4938-107">.NET 組件</span><span class="sxs-lookup"><span data-stu-id="e4938-107">.NET assemblies</span></span>  
  
- <span data-ttu-id="e4938-108">COM 元件</span><span class="sxs-lookup"><span data-stu-id="e4938-108">COM components</span></span>  
  
- <span data-ttu-id="e4938-109">憑證</span><span class="sxs-lookup"><span data-stu-id="e4938-109">Certificates</span></span>  
  
- <span data-ttu-id="e4938-110">臨機操作檔案</span><span class="sxs-lookup"><span data-stu-id="e4938-110">Ad hoc files</span></span>  
  
- <span data-ttu-id="e4938-111">BAM 定義</span><span class="sxs-lookup"><span data-stu-id="e4938-111">BAM definitions</span></span>  
  
- <span data-ttu-id="e4938-112">繫結檔案</span><span class="sxs-lookup"><span data-stu-id="e4938-112">Binding files</span></span>  
  
- <span data-ttu-id="e4938-113">虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="e4938-113">Virtual directories</span></span>  
  
  <span data-ttu-id="e4938-114">如果虛擬目錄是透過匯入或新增的方式，明確加入至應用程式，您可以使用本主題明的程序將它移除；</span><span class="sxs-lookup"><span data-stu-id="e4938-114">If a virtual directory is explicitly added to an application, either by being imported from or added, it can be removed by using the procedures in this topic.</span></span> <span data-ttu-id="e4938-115">但是如果沒有明確加入，而是在設定接收位置時以參考的方式加入，則不能使用本主題中的程序移除它。</span><span class="sxs-lookup"><span data-stu-id="e4938-115">If it was not explicitly added, but rather was added by reference when a receive location was configured, you cannot remove it by using the procedures in this topic.</span></span> <span data-ttu-id="e4938-116">這是因為虛擬目錄不是儲存在 BizTalk 管理資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e4938-116">This is because the virtual directory is not stored in the BizTalk Management database.</span></span> <span data-ttu-id="e4938-117">當您匯出應用程式 .msi 檔案時，系統會從 IIS 取得虛擬目錄，並將它新增到 .msi 檔案；</span><span class="sxs-lookup"><span data-stu-id="e4938-117">When you export the application .msi file the virtual directory will be obtained from IIS and added to the .msi file.</span></span> <span data-ttu-id="e4938-118">而當您匯入 .msi 檔案時，虛擬目錄則會新增到該群組的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="e4938-118">When you import the .msi file, the virtual directory will be added to the BizTalk Management database for that group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e4938-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="e4938-119">Prerequisites</span></span>  
 <span data-ttu-id="e4938-120">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="e4938-120">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="e4938-121">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e4938-121">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-a-resource-artifact-from-an-application"></a><span data-ttu-id="e4938-122">從應用程式移除資源成品</span><span class="sxs-lookup"><span data-stu-id="e4938-122">To remove a resource artifact from an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="e4938-123">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="e4938-123">Using the BizTalk Server Administration console</span></span>  
  
1. <span data-ttu-id="e4938-124">按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e4938-124">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="e4938-125">在主控台樹狀目錄中，展開 [BizTalk Server 管理]、 展開 BizTalk 群組包含之資源成品移除，然後再展開包含成品的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4938-125">In the console tree, expand BizTalk Server Administration, expand the BizTalk group containing the resource artifact to remove, and then expand the application containing the artifact.</span></span>  
  
3. <span data-ttu-id="e4938-126">按一下 **資源**資料夾中，以滑鼠右鍵按一下成品，然後**移除**。</span><span class="sxs-lookup"><span data-stu-id="e4938-126">Click the **Resources** folder, right-click the artifact, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="e4938-127">使用命令列</span><span class="sxs-lookup"><span data-stu-id="e4938-127">Using the command line</span></span>  
  
1. <span data-ttu-id="e4938-128">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e4938-128">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="e4938-129">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="e4938-129">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
    <span data-ttu-id="e4938-130">**BTSTask RemoveResource** [**/ApplicationName:**<em>值</em>] **/Luid:**<em>值</em>[**/Server:** <em>值</em>] [**/database:**<em>值</em>]</span><span class="sxs-lookup"><span data-stu-id="e4938-130">**BTSTask RemoveResource** [**/ApplicationName:**<em>value</em>] **/Luid:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]</span></span>  
  
    <span data-ttu-id="e4938-131">範例</span><span class="sxs-lookup"><span data-stu-id="e4938-131">Example:</span></span>  
  
    <span data-ttu-id="e4938-132">**BTSTask RemoveResource /applicationname: myapplication /Luid:"MyAssembly，version=1.0.0.0，Culture = neutral，PublicKeyToken = 0123456789ABCDEF"**</span><span class="sxs-lookup"><span data-stu-id="e4938-132">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**</span></span>  
  
   |<span data-ttu-id="e4938-133">參數</span><span class="sxs-lookup"><span data-stu-id="e4938-133">Parameter</span></span>|<span data-ttu-id="e4938-134">描述</span><span class="sxs-lookup"><span data-stu-id="e4938-134">Description</span></span>|  
   |---------------|-----------------|  
   |<span data-ttu-id="e4938-135">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="e4938-135">**/ApplicationName**</span></span>|<span data-ttu-id="e4938-136">含有所要刪除之成品的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4938-136">Name of the BizTalk application containing the artifact to delete.</span></span> <span data-ttu-id="e4938-137">如果沒有指定，將會使用預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4938-137">If not specified, the default application is used.</span></span> <span data-ttu-id="e4938-138">如果名稱包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="e4938-138">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
   |<span data-ttu-id="e4938-139">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="e4938-139">**/Luid**</span></span>|<span data-ttu-id="e4938-140">成品的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="e4938-140">Locally unique identifier (LUID) of the artifact.</span></span> <span data-ttu-id="e4938-141">您可以使用來取得 LUID **ListApp**命令，如中所述[ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="e4938-141">You can obtain the LUID by using the **ListApp** command, as described in [ListApp Command](../core/listapp-command.md).</span></span>|  
   |<span data-ttu-id="e4938-142">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="e4938-142">**/Server**</span></span>|<span data-ttu-id="e4938-143">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="e4938-143">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="e4938-144">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e4938-144">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="e4938-145">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="e4938-145">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="e4938-146">範例:</span><span class="sxs-lookup"><span data-stu-id="e4938-146">Examples:</span></span><br /><br /> <span data-ttu-id="e4938-147">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="e4938-147">Server=MyServer</span></span><br /><br /> <span data-ttu-id="e4938-148">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="e4938-148">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="e4938-149">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4938-149">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
   |<span data-ttu-id="e4938-150">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="e4938-150">**/Database**</span></span>|<span data-ttu-id="e4938-151">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4938-151">Name of the BizTalk Management database.</span></span> <span data-ttu-id="e4938-152">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="e4938-152">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4938-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4938-153">See Also</span></span>  
 <span data-ttu-id="e4938-154">[管理.NET 組件、 憑證和其他資源](../core/managing-net-assemblies-certificates-and-other-resources.md) </span><span class="sxs-lookup"><span data-stu-id="e4938-154">[Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md) </span></span>  
 [<span data-ttu-id="e4938-155">RemoveResource 命令</span><span class="sxs-lookup"><span data-stu-id="e4938-155">RemoveResource Command</span></span>](../core/removeresource-command.md)