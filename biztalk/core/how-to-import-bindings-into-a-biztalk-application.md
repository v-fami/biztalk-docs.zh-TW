---
title: 如何將繫結匯入到 BizTalk 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings, applications
- applications, importing
- applications, bindings
- bindings, importing
ms.assetid: 89841b23-4e1b-46ff-8f00-cdad65d6216d
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 174a54b5f1ad98b4ba57c70a24ec2f621577271d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011943"
---
# <a name="how-to-import-bindings-into-a-biztalk-application"></a><span data-ttu-id="3fa94-102">如何將繫結匯入到 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="3fa94-102">How to Import Bindings into a BizTalk Application</span></span>
<span data-ttu-id="3fa94-103">本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列，從 .xml 檔案將繫結匯入到 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3fa94-103">This topic describes how to use the BizTalk Server Administration console or the command line to import bindings into a BizTalk application from an .xml file.</span></span> <span data-ttu-id="3fa94-104">您也可以匯入繫結至 BizTalk 群組，如中所述[如何匯入到 BizTalk 群組的繫結](../core/how-to-import-bindings-into-a-biztalk-group.md)。</span><span class="sxs-lookup"><span data-stu-id="3fa94-104">You can also import bindings into a BizTalk group, as described in [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md).</span></span>  
  
 <span data-ttu-id="3fa94-105">您可以匯入已經從組件、應用程式或群組匯出的繫結。</span><span class="sxs-lookup"><span data-stu-id="3fa94-105">You can import bindings that have been exported from an assembly, application, or group.</span></span> <span data-ttu-id="3fa94-106">如果您要匯入群組繫結，只有同名應用程式的繫結才會套用到匯入繫結的目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="3fa94-106">If you import group bindings, only the bindings for an application having the same name are applied to the application into which you import the bindings.</span></span> <span data-ttu-id="3fa94-107">您也可以從不同名稱的應用程式匯入繫結。</span><span class="sxs-lookup"><span data-stu-id="3fa94-107">You can also import bindings from an application that has a different name.</span></span> <span data-ttu-id="3fa94-108">如需匯出繫結的指示，請參閱 <<c0> [ 匯出的繫結](../core/exporting-bindings6.md)。</span><span class="sxs-lookup"><span data-stu-id="3fa94-108">For instructions on exporting bindings, see [Exporting Bindings](../core/exporting-bindings6.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3fa94-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="3fa94-109">Prerequisites</span></span>  
 <span data-ttu-id="3fa94-110">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="3fa94-110">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="3fa94-111">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3fa94-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-import-bindings-into-a-biztalk-application"></a><span data-ttu-id="3fa94-112">將繫結匯入到 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="3fa94-112">To import bindings into a BizTalk application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="3fa94-113">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="3fa94-113">Using the BizTalk Server Administration console</span></span>  
  
1. <span data-ttu-id="3fa94-114">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="3fa94-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="3fa94-115">在主控台樹狀結構中，依序展開 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、BizTalk 群組和 [應用程式]。</span><span class="sxs-lookup"><span data-stu-id="3fa94-115">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then expand Applications.</span></span>  
  
3. <span data-ttu-id="3fa94-116">以滑鼠右鍵按一下 應用的程式在其中您要匯入繫結，並指向**匯入**，然後按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="3fa94-116">Right-click the application into which you want to import bindings, point to **Import**, and then click **Bindings**.</span></span>  
  
4. <span data-ttu-id="3fa94-117">按一下 繫結檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="3fa94-117">Click the binding file and click **Open**.</span></span>  
  
    <span data-ttu-id="3fa94-118">繫結檔案中的成品會寫入此應用程式，</span><span class="sxs-lookup"><span data-stu-id="3fa94-118">The artifacts in the binding file are written to the application.</span></span> <span data-ttu-id="3fa94-119">這些成品會顯示在應用程式的適當資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3fa94-119">They display in appropriate folders of the application.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="3fa94-120">使用命令列</span><span class="sxs-lookup"><span data-stu-id="3fa94-120">Using the command line</span></span>  
  
1. <span data-ttu-id="3fa94-121">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="3fa94-121">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="3fa94-122">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="3fa94-122">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
    <span data-ttu-id="3fa94-123">**BTSTask ImportBindings /Source:** *值*[**/ApplicationName:**<em>值</em>] [**/Server:** <em>值</em>] [**/database:**<em>值</em>]</span><span class="sxs-lookup"><span data-stu-id="3fa94-123">**BTSTask ImportBindings /Source:** *value* [**/ApplicationName:**<em>value</em>] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]</span></span>  
  
    <span data-ttu-id="3fa94-124">例如，下列命令會將繫結匯入到預設 BizTalk 群組中名為 MyApplication 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3fa94-124">For example, the following command imports bindings into the application named MyApplication in the default BizTalk group.</span></span>  
  
    <span data-ttu-id="3fa94-125">**BTSTask ImportBindings /applicationname: myapplication** /**Source:C:\Bindings\Binding1.xml**</span><span class="sxs-lookup"><span data-stu-id="3fa94-125">**BTSTask ImportBindings /ApplicationName:MyApplication** /**Source:C:\Bindings\Binding1.xml**</span></span>  
  
   |<span data-ttu-id="3fa94-126">參數</span><span class="sxs-lookup"><span data-stu-id="3fa94-126">Parameter</span></span>|<span data-ttu-id="3fa94-127">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="3fa94-127">Value</span></span>|  
   |---------------|-----------|  
   |<span data-ttu-id="3fa94-128">**/ 來源**</span><span class="sxs-lookup"><span data-stu-id="3fa94-128">**/Source**</span></span>|<span data-ttu-id="3fa94-129">要匯入的繫結檔案完整路徑 (包含檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="3fa94-129">Full path of the binding file to import, including the file name.</span></span> <span data-ttu-id="3fa94-130">路徑如果包含空格，必須括在引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="3fa94-130">Paths that include spaces must be enclosed in quotation marks (").</span></span>|  
   |<span data-ttu-id="3fa94-131">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="3fa94-131">**/ApplicationName**</span></span>|<span data-ttu-id="3fa94-132">要匯入繫結的 BizTalk 應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="3fa94-132">Name of the BizTalk application into which the bindings are to be imported.</span></span> <span data-ttu-id="3fa94-133">應用程式必須存在，否則匯入作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3fa94-133">The application must exist or the import operation will fail.</span></span> <span data-ttu-id="3fa94-134">如果沒有指定這個參數，將會使用預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3fa94-134">If this parameter is not specified, the default BizTalk application is used.</span></span> <span data-ttu-id="3fa94-135">應用程式名稱如果包含空格，必須括在引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="3fa94-135">Application names that include spaces must be enclosed in quotation marks (").</span></span>|  
   |<span data-ttu-id="3fa94-136">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="3fa94-136">**/Server**</span></span>|<span data-ttu-id="3fa94-137">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="3fa94-137">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="3fa94-138">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="3fa94-138">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="3fa94-139">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="3fa94-139">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="3fa94-140">範例:</span><span class="sxs-lookup"><span data-stu-id="3fa94-140">Examples:</span></span><br /><br /> <span data-ttu-id="3fa94-141">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="3fa94-141">Server=MyServer</span></span><br /><br /> <span data-ttu-id="3fa94-142">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="3fa94-142">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="3fa94-143">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="3fa94-143">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
   |<span data-ttu-id="3fa94-144">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="3fa94-144">**/Database**</span></span>|<span data-ttu-id="3fa94-145">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3fa94-145">Name of the BizTalk Management database.</span></span> <span data-ttu-id="3fa94-146">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="3fa94-146">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3fa94-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fa94-147">See Also</span></span>  
 <span data-ttu-id="3fa94-148">[匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md) </span><span class="sxs-lookup"><span data-stu-id="3fa94-148">[Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md) </span></span>  
 [<span data-ttu-id="3fa94-149">ImportBindings 命令</span><span class="sxs-lookup"><span data-stu-id="3fa94-149">ImportBindings Command</span></span>](../core/importbindings-command.md)