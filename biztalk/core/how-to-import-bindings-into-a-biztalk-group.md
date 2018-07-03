---
title: 如何將繫結匯入到 BizTalk 群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- groups, importing
- importing, bindings
- groups, bindings
- bindings, groups
ms.assetid: 38da14fb-3522-4274-a633-2ff24e4bd574
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bdc3f8c25e50567c9e12df5c61ba28cc225e5a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000375"
---
# <a name="how-to-import-bindings-into-a-biztalk-group"></a><span data-ttu-id="95059-102">如何將繫結匯入到 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="95059-102">How to Import Bindings into a BizTalk Group</span></span>
<span data-ttu-id="95059-103">本主題描述如何使用 [BizTalk Server 管理主控台] 或命令列，從 .xml 檔案將繫結匯入到 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="95059-103">This topic describes how to use the BizTalk Server Administration console or the command line to import bindings into a BizTalk group from an .xml file.</span></span> <span data-ttu-id="95059-104">如需從 BizTalk 群組匯出繫結，到.xml 檔案，您可以匯入的指示，請參閱 <<c0> [ 如何為 BizTalk 群組匯出的繫結](../core/how-to-export-bindings-for-a-biztalk-group.md)。</span><span class="sxs-lookup"><span data-stu-id="95059-104">For instructions on exporting the bindings from a BizTalk group into an .xml file that you can import, see [How to Export Bindings for a BizTalk Group](../core/how-to-export-bindings-for-a-biztalk-group.md).</span></span>  
  
 <span data-ttu-id="95059-105">您也可以匯入繫結至 BizTalk 應用程式中所述[如何匯入至 BizTalk 應用程式的繫結](../core/how-to-import-bindings-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="95059-105">You can also import bindings into a BizTalk application, as described in [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="95059-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="95059-106">Prerequisites</span></span>  
 <span data-ttu-id="95059-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="95059-107">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="95059-108">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="95059-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-import-bindings-into-a-biztalk-group"></a><span data-ttu-id="95059-109">若要將繫結匯入到 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="95059-109">To import bindings into a BizTalk group</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="95059-110">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="95059-110">Using the BizTalk Server Administration console</span></span>  
  
1. <span data-ttu-id="95059-111">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="95059-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="95059-112">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，然後以滑鼠右鍵按一下**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="95059-112">In the console tree, expand  **BizTalk Server Administration**, expand the BizTalk group, and then right-click **Applications**.</span></span>  
  
3. <span data-ttu-id="95059-113">指向**匯入**，然後按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="95059-113">Point to **Import**, and then click **Bindings**.</span></span>  
  
4. <span data-ttu-id="95059-114">按一下 繫結檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="95059-114">Click the binding file and click **Open**.</span></span>  
  
    <span data-ttu-id="95059-115">繫結檔案中的成品會寫入此群組。</span><span class="sxs-lookup"><span data-stu-id="95059-115">The artifacts in the binding file are written to the group.</span></span> <span data-ttu-id="95059-116">在適當資料夾中顯示\<所有成品\>節點。</span><span class="sxs-lookup"><span data-stu-id="95059-116">They display in appropriate folders of the \<All Artifacts\> node.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="95059-117">使用命令列</span><span class="sxs-lookup"><span data-stu-id="95059-117">Using the command line</span></span>  
  
1. <span data-ttu-id="95059-118">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="95059-118">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="95059-119">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="95059-119">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
    <span data-ttu-id="95059-120">**BTSTask ImportBindings /Source:** *值* **/GroupLevel** [**/Server:**<em>值</em>] [  **/資料庫:**<em>值</em>]</span><span class="sxs-lookup"><span data-stu-id="95059-120">**BTSTask ImportBindings /Source:** *value* **/GroupLevel** [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]</span></span>  
  
    <span data-ttu-id="95059-121">例如，下列命令會將繫結匯入到在 BizTalk 管理資料庫中定義的群組，該資料庫則是在名為 MyServer 的 SQL Server 執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="95059-121">For example, the following command imports bindings into the group defined in the BizTalk Management database running on a SQL Server instance named MyServer.</span></span>  
  
    <span data-ttu-id="95059-122">**BTSTask ImportBindings GroupLevel /Server:MyServer /Database:BiztalkMgmtDb /Source:C:\Bindings\Binding1.xml**</span><span class="sxs-lookup"><span data-stu-id="95059-122">**BTSTask ImportBindings /GroupLevel /Server:MyServer /Database:BiztalkMgmtDb /Source:C:\Bindings\Binding1.xml**</span></span>  
  
   |<span data-ttu-id="95059-123">參數</span><span class="sxs-lookup"><span data-stu-id="95059-123">Parameter</span></span>|<span data-ttu-id="95059-124">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="95059-124">Value</span></span>|  
   |---------------|-----------|  
   |<span data-ttu-id="95059-125">**/ 來源**</span><span class="sxs-lookup"><span data-stu-id="95059-125">**/Source**</span></span>|<span data-ttu-id="95059-126">要匯入的繫結檔案完整路徑 (包含檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="95059-126">Full path of the binding file to import, including the file name.</span></span> <span data-ttu-id="95059-127">路徑如果包含空格，必須括在引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="95059-127">Paths that include spaces must be enclosed in quotation marks (").</span></span>|  
   |<span data-ttu-id="95059-128">**/ GroupLevel**</span><span class="sxs-lookup"><span data-stu-id="95059-128">**/GroupLevel**</span></span>|<span data-ttu-id="95059-129">此選項指定將繫結檔案匯入到目前的群組。</span><span class="sxs-lookup"><span data-stu-id="95059-129">Option to import the binding file into the current group.</span></span>|  
   |<span data-ttu-id="95059-130">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="95059-130">**/Server**</span></span>|<span data-ttu-id="95059-131">裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱，其格式為：伺服器名稱\執行個體名稱,連接埠。</span><span class="sxs-lookup"><span data-stu-id="95059-131">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="95059-132">只有在執行個體名稱和伺服器名稱不同時，才需要執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="95059-132">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="95059-133">只有在 SQL Server 使用預設值 (1433) 以外的連接埠編號時，才需要連接埠。</span><span class="sxs-lookup"><span data-stu-id="95059-133">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="95059-134">範例:</span><span class="sxs-lookup"><span data-stu-id="95059-134">Examples:</span></span><br /><br /> <span data-ttu-id="95059-135">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="95059-135">Server=MyServer</span></span><br /><br /> <span data-ttu-id="95059-136">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="95059-136">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="95059-137">如果不提供，將會使用在本機電腦上執行的 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="95059-137">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
   |<span data-ttu-id="95059-138">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="95059-138">**/Database**</span></span>|<span data-ttu-id="95059-139">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="95059-139">Name of the BizTalk Management database.</span></span> <span data-ttu-id="95059-140">如果沒有指定，將會使用在 SQL Server 本機執行個體中執行的 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="95059-140">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95059-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95059-141">See Also</span></span>  
 <span data-ttu-id="95059-142">[匯入 BizTalk 應用程式、 繫結和原則](../core/importing-biztalk-applications-bindings-and-policies.md) </span><span class="sxs-lookup"><span data-stu-id="95059-142">[Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md) </span></span>  
 [<span data-ttu-id="95059-143">ImportBindings 命令</span><span class="sxs-lookup"><span data-stu-id="95059-143">ImportBindings Command</span></span>](../core/importbindings-command.md)