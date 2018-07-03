---
title: BTSTask 命令列參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c350695-13e9-441a-9f1e-03cdc3e41328
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44aa603f777b2634422a6cbf5962088bc6724351
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015575"
---
# <a name="btstask-command-line-reference"></a><span data-ttu-id="31f9e-102">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="31f9e-102">BTSTask Command-Line Reference</span></span>
<span data-ttu-id="31f9e-103">本節主題提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所附 BTSTask 命令列工具的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="31f9e-103">The topics in this section provide reference information for the BTSTask command-line tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="31f9e-104">您可以使用 BTSTask 從命令列執行許多應用程式部署工作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="31f9e-104">You can use BTSTask to perform many application deployment tasks from the command line, as follows:</span></span>  
  
- <span data-ttu-id="31f9e-105">使用 AddApp 命令，將 BizTalk 應用程式新增至 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="31f9e-105">Add a BizTalk application to the BizTalk Management database by using the AddApp command.</span></span>  
  
- <span data-ttu-id="31f9e-106">使用 AddResource 命令，將成品新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="31f9e-106">Add an artifact to an application by using the AddResource command.</span></span>  
  
- <span data-ttu-id="31f9e-107">使用 ExportApp 命令，將應用程式及其成品匯出至 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="31f9e-107">Export an application and its artifacts to an .msi file by using the ExportApp command.</span></span>  
  
- <span data-ttu-id="31f9e-108">使用 ExportBindings 命令，將繫結資訊匯出至 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="31f9e-108">Export binding information to an .xml file by using the ExportBindings command.</span></span>  
  
- <span data-ttu-id="31f9e-109">使用 ImportApp 命令，從 .msi 檔案匯入應用程式。</span><span class="sxs-lookup"><span data-stu-id="31f9e-109">Import an application from an .msi file by using the ImportApp command.</span></span>  
  
- <span data-ttu-id="31f9e-110">使用 ImportBindings 命令，從 .xml 檔案匯入繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="31f9e-110">Import binding information from an .xml file by using the ImportBindings command.</span></span>  
  
- <span data-ttu-id="31f9e-111">使用 ListApp 命令，列出包含在應用程式中的成品以及成品的本機唯一識別碼 (LUID)。</span><span class="sxs-lookup"><span data-stu-id="31f9e-111">List the artifacts included in an application along with their locally unique identifiers (LUIDs) by using the ListApp command.</span></span>  
  
- <span data-ttu-id="31f9e-112">使用 ListApps 命令，列出 BizTalk 群組在 BizTalk 管理資料庫中的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="31f9e-112">List all applications in the BizTalk Management database for the BizTalk group by using the ListApps command.</span></span>  
  
- <span data-ttu-id="31f9e-113">使用 ListPackage 命令，列出 .msi 檔案中的資源。</span><span class="sxs-lookup"><span data-stu-id="31f9e-113">List the resources in an .msi file by using the ListPackage command.</span></span>  
  
- <span data-ttu-id="31f9e-114">使用 ListTypes 命令，列出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援的所有成品類型。</span><span class="sxs-lookup"><span data-stu-id="31f9e-114">List all of the artifact types supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the ListTypes command.</span></span>  
  
- <span data-ttu-id="31f9e-115">使用 RemoveApp 命令，從 BizTalk 管理資料庫及 BizTalk 管理主控台移除應用程式。</span><span class="sxs-lookup"><span data-stu-id="31f9e-115">Remove an application from the BizTalk Management database and the BizTalk Administration console by using the RemoveApp command.</span></span>  
  
- <span data-ttu-id="31f9e-116">使用 RemoveResource 命令，從應用程式移除成品。</span><span class="sxs-lookup"><span data-stu-id="31f9e-116">Remove an artifact from an application by using the RemoveResource command.</span></span>  
  
- <span data-ttu-id="31f9e-117">使用 UninstallApp 命令，從本機電腦解除安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="31f9e-117">Uninstall an application from the local computer by using the UninstallApp command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31f9e-118">在將於應用程式匯入期間執行的前置處理或後置處理指令碼中不得使用 BTSTask 命令。</span><span class="sxs-lookup"><span data-stu-id="31f9e-118">You cannot use BTSTask commands in a preprocessing or postprocessing script that will run during application import.</span></span> <span data-ttu-id="31f9e-119">若您這麼做，匯入就會失敗。</span><span class="sxs-lookup"><span data-stu-id="31f9e-119">If you do, the import may fail.</span></span> <span data-ttu-id="31f9e-120">這是因為指令碼看不見匯入期間所做的變更。</span><span class="sxs-lookup"><span data-stu-id="31f9e-120">This is because changes being made during import are not visible to scripts.</span></span>  
  
 <span data-ttu-id="31f9e-121">此外，您還可以試著編輯 BTSTask 的主控台前景色彩。</span><span class="sxs-lookup"><span data-stu-id="31f9e-121">In addition, you can learn how to edit the console foreground colors for BTSTask.</span></span> <span data-ttu-id="31f9e-122">如果主控台背景色彩是白色的，就難以判讀 BTSTask 主控台的輸出，因而需要修改主控台前景色彩。</span><span class="sxs-lookup"><span data-stu-id="31f9e-122">If your console background color is white, you will have difficulty reading the BTSTask console output and will need to modify the console foreground colors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31f9e-123">當指令碼完成後，將傳回零 (0) 表示已順利完成，或傳回非零值表示失敗。</span><span class="sxs-lookup"><span data-stu-id="31f9e-123">When a script completes, it returns a zero (0) to indicate successful completion or a non-zero number to indicate failure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31f9e-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="31f9e-124">In This Section</span></span>  
  
-   [<span data-ttu-id="31f9e-125">AddApp 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-125">AddApp Command</span></span>](../core/addapp-command.md)  
  
-   [<span data-ttu-id="31f9e-126">AddResource 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-126">AddResource Command</span></span>](../core/addresource-command.md)  
  
-   [<span data-ttu-id="31f9e-127">ExportApp 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-127">ExportApp Command</span></span>](../core/exportapp-command.md)  
  
-   [<span data-ttu-id="31f9e-128">ExportBindings 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-128">ExportBindings Command</span></span>](../core/exportbindings-command.md)  

- [<span data-ttu-id="31f9e-129">ExportParties 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-129">ExportParties Command</span></span>](../core/exportparties-command.md)

- [<span data-ttu-id="31f9e-130">ExportSettings 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-130">ExportSettings Command</span></span>](../core/exportsettings-command.md)
  
-   [<span data-ttu-id="31f9e-131">ImportApp 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-131">ImportApp Command</span></span>](../core/importapp-command.md)  
  
-   [<span data-ttu-id="31f9e-132">ImportBindings 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-132">ImportBindings Command</span></span>](../core/importbindings-command.md)  

- [<span data-ttu-id="31f9e-133">ImportParties 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-133">ImportParties Command</span></span>](../core/importparties-command.md)

- [<span data-ttu-id="31f9e-134">ImportSettings 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-134">ImportSettings Command</span></span>](../core/importsettings-command.md)
  
-   [<span data-ttu-id="31f9e-135">ListApp 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-135">ListApp Command</span></span>](../core/listapp-command.md)  
  
-   [<span data-ttu-id="31f9e-136">ListApps 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-136">ListApps Command</span></span>](../core/listapps-command.md)  
  
-   [<span data-ttu-id="31f9e-137">ListPackage 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-137">ListPackage Command</span></span>](../core/listpackage-command.md)  
  
-   [<span data-ttu-id="31f9e-138">ListTypes 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-138">ListTypes Command</span></span>](../core/listtypes-command.md)  
  
-   [<span data-ttu-id="31f9e-139">RemoveApp 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-139">RemoveApp Command</span></span>](../core/removeapp-command.md)  
  
-   [<span data-ttu-id="31f9e-140">RemoveResource 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-140">RemoveResource Command</span></span>](../core/removeresource-command.md)  
  
-   [<span data-ttu-id="31f9e-141">UninstallApp 命令</span><span class="sxs-lookup"><span data-stu-id="31f9e-141">UninstallApp Command</span></span>](../core/uninstallapp-command.md)  
  
-   [<span data-ttu-id="31f9e-142">如何編輯 BTSTask 的主控台色彩</span><span class="sxs-lookup"><span data-stu-id="31f9e-142">How to Edit the Console Colors for BTSTask</span></span>](../core/how-to-edit-the-console-colors-for-btstask.md)