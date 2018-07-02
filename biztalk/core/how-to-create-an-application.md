---
title: 如何建立應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, creating
- creating, applications
ms.assetid: 6a8682a7-3bef-4978-996f-5a9c5154ce62
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b81a90c4e013d9eb8d882f2d9901e70920d0c46a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983055"
---
# <a name="how-to-create-an-application"></a><span data-ttu-id="e0ced-102">如何建立應用程式</span><span class="sxs-lookup"><span data-stu-id="e0ced-102">How to Create an Application</span></span>
<span data-ttu-id="e0ced-103">有三個方法可建立新的 BizTalk 應用程式：</span><span class="sxs-lookup"><span data-stu-id="e0ced-103">There are three ways to create a new BizTalk application:</span></span>  
  
- <span data-ttu-id="e0ced-104">使用 BizTalk Server 管理主控台的 [新增應用程式] 命令或 BTSTask 命令列工具的 AddApp 命令，建立 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0ced-104">Create the BizTalk application by using the New Application command of the BizTalk Server Administration console or the AddApp command of the BTSTask command-line tool.</span></span> <span data-ttu-id="e0ced-105">本主題稍後將提供執行此作業的程序。</span><span class="sxs-lookup"><span data-stu-id="e0ced-105">You can find the procedures for doing this later in this topic.</span></span>  
  
- <span data-ttu-id="e0ced-106">匯入已經從另一個應用程式匯出的 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="e0ced-106">Import an .msi file that was exported from another application.</span></span> <span data-ttu-id="e0ced-107">如果目前 BizTalk 群組中沒有此應用程式，則會在目前 BizTalk 群組中自動建立此應用程式以及它的成品。</span><span class="sxs-lookup"><span data-stu-id="e0ced-107">If the application does not already exist in the current BizTalk group, the application, including its artifacts, is automatically created in the current BizTalk group.</span></span> <span data-ttu-id="e0ced-108">如需詳細資訊，請參閱 <<c0> [ 如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ced-108">For more information, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
- <span data-ttu-id="e0ced-109">從 Visual Studio 將 BizTalk 組件部署到 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0ced-109">Deploy BizTalk assemblies from Visual Studio into a BizTalk application.</span></span> <span data-ttu-id="e0ced-110">如果目前 BizTalk 群組中沒有 Visual Studio 所指定的應用程式，則會自動建立它。</span><span class="sxs-lookup"><span data-stu-id="e0ced-110">If the application specified in Visual Studio does not already exist in the current BizTalk group, it is automatically created.</span></span> <span data-ttu-id="e0ced-111">如需詳細資訊，請參閱 <<c0> [ 從 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ced-111">For more information, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
  <span data-ttu-id="e0ced-112">建立新應用程式之前，您可能想要決定如何設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="e0ced-112">Before creating a new application, you might want to decide how to configure the following options:</span></span>  
  
- <span data-ttu-id="e0ced-113">**如何命名新的應用程式。**</span><span class="sxs-lookup"><span data-stu-id="e0ced-113">**What to name the new application.**</span></span> <span data-ttu-id="e0ced-114">BizTalk 群組中的每個應用程式都必須有唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="e0ced-114">Each application in the BizTalk group must have a unique name.</span></span>  
  
- <span data-ttu-id="e0ced-115">**您是否需要新增任何其他應用程式的參考。**</span><span class="sxs-lookup"><span data-stu-id="e0ced-115">**Whether you need to add any references to other applications.**</span></span> <span data-ttu-id="e0ced-116">若要在這個應用程式中重複使用其他應用程式中的成品，您必須在此應用程式中新增其他應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="e0ced-116">You must add a reference from this application to any applications containing artifacts that you want to reuse in this application.</span></span> <span data-ttu-id="e0ced-117">這會建立應用程式之間的相依性，也會影響您必須部署這些應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="e0ced-117">This creates a dependency between the applications, which affects the way that you must deploy them.</span></span> <span data-ttu-id="e0ced-118">如需背景資訊，請參閱 <<c0> [ 相依性和應用程式部署](../core/dependencies-and-application-deployment.md)並[如何新增另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ced-118">For background information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md) and [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
- <span data-ttu-id="e0ced-119">**是否要建立多個應用程式。**</span><span class="sxs-lookup"><span data-stu-id="e0ced-119">**Whether you need to create more than one application.**</span></span> <span data-ttu-id="e0ced-120">您可能需要將一些成品部署至個別的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0ced-120">You may need to deploy some artifacts into separate applications.</span></span> <span data-ttu-id="e0ced-121">例如，共用的成品應部署至專屬、個別的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0ced-121">For example, shared artifacts should be deployed into their own, separate application.</span></span> <span data-ttu-id="e0ced-122">如需詳細資訊，請參閱 <<c0> [ 部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ced-122">For more information, see [Best Practices for Deploying a BizTalk Application](../core/best-practices-for-deploying-a-biztalk-application.md).</span></span>  
  
  <span data-ttu-id="e0ced-123">當您建立應用程式之後時，您可以將成品新增到它，並進行其他修改，在這一節中的其他主題中所述 ([建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md))。</span><span class="sxs-lookup"><span data-stu-id="e0ced-123">Once you have created an application, you can add artifacts to it and make other modifications, as described in the other topics in this section ([Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e0ced-124">必要條件</span><span class="sxs-lookup"><span data-stu-id="e0ced-124">Prerequisites</span></span>  
 <span data-ttu-id="e0ced-125">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="e0ced-125">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="e0ced-126">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ced-126">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-create-a-biztalk-application"></a><span data-ttu-id="e0ced-127">若要建立 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="e0ced-127">To create a BizTalk application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="e0ced-128">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="e0ced-128">Using the BizTalk Server Administration console</span></span>  
  
1. <span data-ttu-id="e0ced-129">按一下 **開始**，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e0ced-129">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="e0ced-130">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下 BizTalk 群組，您要建立新的應用程式，指向**新增**，然後按一下**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="e0ced-130">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click the BizTalk group in which you want to create the new application, point to **New**, and then click **Application**.</span></span>  
  
3. <span data-ttu-id="e0ced-131">在 **名稱**，輸入應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0ced-131">In **Name**, type the name of the application.</span></span> <span data-ttu-id="e0ced-132">此名稱必須是 BizTalk 群組中唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0ced-132">The name must be unique in the BizTalk group.</span></span>  
  
4. <span data-ttu-id="e0ced-133">如果您想要將此 BizTalk 群組的預設應用程式，請選取**將此設為預設應用程式**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e0ced-133">If you want to make this the default application for the BizTalk group, select the **Make this the default application** check box.</span></span>  
  
5. <span data-ttu-id="e0ced-134">在 **描述**，輸入應用程式的描述。</span><span class="sxs-lookup"><span data-stu-id="e0ced-134">In **Description**, type a description for the application.</span></span>  
  
6. <span data-ttu-id="e0ced-135">如果此應用程式會重複使用從其他應用程式的成品，請按一下**參考**和其餘的步驟。</span><span class="sxs-lookup"><span data-stu-id="e0ced-135">If this application will reuse artifacts from another application, click **References** and follow the remaining steps.</span></span> <span data-ttu-id="e0ced-136">否則，請按一下**確定**並採取任何進一步的步驟。</span><span class="sxs-lookup"><span data-stu-id="e0ced-136">Otherwise, click **OK** and take no further steps.</span></span>  
  
7. <span data-ttu-id="e0ced-137">按一下 **新增**，選取包含您想要在這個應用程式中重複使用，然後按一下 的成品的應用程式**確定**。</span><span class="sxs-lookup"><span data-stu-id="e0ced-137">Click **Add**, select the application that contains the artifacts you want to reuse in this application, and then click **OK**.</span></span> <span data-ttu-id="e0ced-138">對每個新增應用程式參考，重複這個步驟。</span><span class="sxs-lookup"><span data-stu-id="e0ced-138">Repeat this step for any additional applications for which you want to add references.</span></span>  
  
8. <span data-ttu-id="e0ced-139">如果您想要從清單中移除應用程式，請選取 應用程式，然後按一下**移除**。</span><span class="sxs-lookup"><span data-stu-id="e0ced-139">If you want to remove an application from the list, select the application and click **Remove**.</span></span>  
  
9. <span data-ttu-id="e0ced-140">完成後，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e0ced-140">When finished, click **OK**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="e0ced-141">使用命令列</span><span class="sxs-lookup"><span data-stu-id="e0ced-141">Using the command line</span></span>  
  
1. <span data-ttu-id="e0ced-142">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e0ced-142">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="e0ced-143">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="e0ced-143">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
    <span data-ttu-id="e0ced-144">**BTSTask AddApp /ApplicationName:** *值*[**/預設值**] [**/Description:**<em>值</em>] [**/伺服器：**<em>值</em>] [**/database:**<em>值</em>]</span><span class="sxs-lookup"><span data-stu-id="e0ced-144">**BTSTask AddApp /ApplicationName:** *value* [**/Default**] [**/Description:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]</span></span>  
  
    <span data-ttu-id="e0ced-145">範例</span><span class="sxs-lookup"><span data-stu-id="e0ced-145">Example:</span></span>  
  
    <span data-ttu-id="e0ced-146">**BTSTask AddApp /applicationname: myapplication /Description: 「 我最愛的應用程式 」 /Server:MySQLServer /Database:BizTalkMgmtDb**</span><span class="sxs-lookup"><span data-stu-id="e0ced-146">**BTSTask AddApp /ApplicationName:MyApplication /Description:"My favorite application" /Server:MySQLServer /Database:BizTalkMgmtDb**</span></span>  
  
   |<span data-ttu-id="e0ced-147">參數</span><span class="sxs-lookup"><span data-stu-id="e0ced-147">Parameter</span></span>|<span data-ttu-id="e0ced-148">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="e0ced-148">Value</span></span>|  
   |---------------|-----------|  
   |<span data-ttu-id="e0ced-149">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="e0ced-149">**/ApplicationName**</span></span>|<span data-ttu-id="e0ced-150">要建立的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="e0ced-150">Name of the application to be created.</span></span> <span data-ttu-id="e0ced-151">名稱如果包含空格，則必須括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="e0ced-151">Names containing spaces must be enclosed in double quotation marks (").</span></span>|  
   |<span data-ttu-id="e0ced-152">**/ 預設值**</span><span class="sxs-lookup"><span data-stu-id="e0ced-152">**/Default**</span></span>|<span data-ttu-id="e0ced-153">如果有指定，新應用程式將成為 BizTalk 群組預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0ced-153">When specified, makes the new application the default application for the BizTalk group.</span></span>|  
   |<span data-ttu-id="e0ced-154">**/ 描述**</span><span class="sxs-lookup"><span data-stu-id="e0ced-154">**/Description**</span></span>|<span data-ttu-id="e0ced-155">應用程式的說明。</span><span class="sxs-lookup"><span data-stu-id="e0ced-155">Description of the application.</span></span> <span data-ttu-id="e0ced-156">說明如果包含空格，則必須括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="e0ced-156">Descriptions containing spaces must be enclosed in double quotation marks (").</span></span>|  
   |<span data-ttu-id="e0ced-157">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="e0ced-157">**/Server**</span></span>|<span data-ttu-id="e0ced-158">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="e0ced-158">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="e0ced-159">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e0ced-159">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="e0ced-160">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="e0ced-160">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="e0ced-161">範例:</span><span class="sxs-lookup"><span data-stu-id="e0ced-161">Examples:</span></span><br /><br /> <span data-ttu-id="e0ced-162">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="e0ced-162">Server=MyServer</span></span><br /><br /> <span data-ttu-id="e0ced-163">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="e0ced-163">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="e0ced-164">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0ced-164">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
   |<span data-ttu-id="e0ced-165">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="e0ced-165">**/Database**</span></span>|<span data-ttu-id="e0ced-166">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0ced-166">Name of the BizTalk Management database.</span></span> <span data-ttu-id="e0ced-167">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="e0ced-167">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0ced-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0ced-168">See Also</span></span>  
 <span data-ttu-id="e0ced-169">[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e0ced-169">[Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="e0ced-170">AddApp 命令</span><span class="sxs-lookup"><span data-stu-id="e0ced-170">AddApp Command</span></span>](../core/addapp-command.md)