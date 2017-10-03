---
title: "部署和應用程式匯出 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4106a0a7-878d-4052-8eca-02d546233048
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b33762f50f32dda58f1453fde7be37bc959af6aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-and-exporting-an-application"></a><span data-ttu-id="7afff-102">部署及匯出應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-102">Deploying and Exporting an Application</span></span>
<span data-ttu-id="7afff-103">本節包含有關如何執行所需的步驟，將 BizTalk 應用程式部署的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="7afff-103">This section contains detailed information about how to perform the steps involved in deploying a BizTalk application.</span></span> <span data-ttu-id="7afff-104">本節中的主題也支援下列檢查清單：</span><span class="sxs-lookup"><span data-stu-id="7afff-104">The topics in this section support the following checklists:</span></span>  
  
-   <span data-ttu-id="7afff-105">[檢查清單： 部署應用程式](../technical-guides/checklist-deploying-an-application.md)，其示範如何部署開發環境中的應用程式，將它匯出至.msi 檔案，然後將它匯入到生產環境中，從.msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="7afff-105">[Checklist: Deploying an Application](../technical-guides/checklist-deploying-an-application.md), which shows how to deploy an application in a development environment, export it into an .msi file, and then import it into a production environment from the .msi file.</span></span>  
  
-   <span data-ttu-id="7afff-106">[檢查清單： 匯出繫結到另一個應用程式從](../technical-guides/checklist-exporting-bindings-from-one-application-to-another.md)，其示範如何從應用程式中的另一個應用程式匯出繫結在開發或實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="7afff-106">[Checklist: Exporting Bindings from One Application to Another](../technical-guides/checklist-exporting-bindings-from-one-application-to-another.md), which shows how to export bindings from an application into another application in either a development or production environment.</span></span>  
  
 <span data-ttu-id="7afff-107">您可以使用下列工具來部署和管理 BizTalk 應用程式：</span><span class="sxs-lookup"><span data-stu-id="7afff-107">You can use the following tools to deploy and manage a BizTalk application:</span></span>  
  
|<span data-ttu-id="7afff-108">工具</span><span class="sxs-lookup"><span data-stu-id="7afff-108">Tool</span></span>|<span data-ttu-id="7afff-109">使用</span><span class="sxs-lookup"><span data-stu-id="7afff-109">Use</span></span>|  
|----------|---------|  
|<span data-ttu-id="7afff-110">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="7afff-110">BizTalk Server Administration console</span></span>|<span data-ttu-id="7afff-111">從這個圖形化使用者介面，您可以執行的所有部署和管理 BizTalk 應用程式，包括下列作業：</span><span class="sxs-lookup"><span data-stu-id="7afff-111">From this graphical user interface, you can perform all of the deployment and management operations for a BizTalk application, including the following:</span></span><br /><br /> <span data-ttu-id="7afff-112">啟動匯入、 安裝和匯出精靈</span><span class="sxs-lookup"><span data-stu-id="7afff-112">-   Starting the Import, Installation, and Export Wizards</span></span><br /><span data-ttu-id="7afff-113">-加入和移除應用程式的成品，以及進行其他修改應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-113">-   Adding and removing an application's artifacts, and making other modifications to the application</span></span><br /><span data-ttu-id="7afff-114">的產生 BizTalk 應用程式的 BizTalk Server.msi 檔案</span><span class="sxs-lookup"><span data-stu-id="7afff-114">-   Generating BizTalk Server .msi files for a BizTalk application</span></span><br /><span data-ttu-id="7afff-115">-從.msi 檔案安裝應用程式的電腦上，或從.msi 檔案將應用程式匯入到另一個 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="7afff-115">-   Installing the application onto a computer from the .msi file or importing the application from the .msi file into another BizTalk group</span></span><br /><span data-ttu-id="7afff-116">-從匯入應用程式的繫結的繫結檔案</span><span class="sxs-lookup"><span data-stu-id="7afff-116">-   Importing the bindings for an application from a binding file</span></span><br /><br /> <span data-ttu-id="7afff-117">如需管理主控台的詳細資訊，請參閱[使用 BizTalk Server 管理主控台](http://go.microsoft.com/fwlink/?LinkID=154689)(http://go.microsoft.com/fwlink/?LinkID=154689)。</span><span class="sxs-lookup"><span data-stu-id="7afff-117">For more information about the administration console, see [Using the BizTalk Server Administration Console](http://go.microsoft.com/fwlink/?LinkID=154689) (http://go.microsoft.com/fwlink/?LinkID=154689).</span></span>|  
|<span data-ttu-id="7afff-118">BTSTask 命令列工具</span><span class="sxs-lookup"><span data-stu-id="7afff-118">BTSTask command-line tool</span></span>|<span data-ttu-id="7afff-119">您可以從命令列執行許多應用程式管理工作。</span><span class="sxs-lookup"><span data-stu-id="7afff-119">You can perform many application management tasks from the command line.</span></span> <span data-ttu-id="7afff-120">如需命令列工具的詳細資訊，請參閱[BTSTask 命令列參考](http://go.microsoft.com/fwlink/?LinkId=155003)(http://go.microsoft.com/fwlink/?LinkId=155003)。</span><span class="sxs-lookup"><span data-stu-id="7afff-120">For more information about the command-line tool, see [BTSTask Command Line Reference](http://go.microsoft.com/fwlink/?LinkId=155003) (http://go.microsoft.com/fwlink/?LinkId=155003).</span></span>|  
|<span data-ttu-id="7afff-121">指令碼和程式設計 Api</span><span class="sxs-lookup"><span data-stu-id="7afff-121">Scripting and programmability APIs</span></span>|<span data-ttu-id="7afff-122">您可以使用 Microsoft Windows Management Instrumentation (WMI) 或 BizTalk 總管物件模型，建立和執行會自動化許多應用程式管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7afff-122">You can use Microsoft Windows Management Instrumentation (WMI) or the BizTalk Explorer Object Model to create and run scripts that automate many application management tasks.</span></span> <span data-ttu-id="7afff-123">如需指令碼的詳細資訊，請參閱[WMI 類別參考](http://go.microsoft.com/fwlink/?LinkId=155004)(http://go.microsoft.com/fwlink/?LinkId=155004)。</span><span class="sxs-lookup"><span data-stu-id="7afff-123">For more information about scripting, see [WMI Class Reference](http://go.microsoft.com/fwlink/?LinkId=155004) (http://go.microsoft.com/fwlink/?LinkId=155004).</span></span>|  
|[!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)]|<span data-ttu-id="7afff-124">您可以在 Visual Studio 中建立 BizTalk 組件、 使用 部署 命令會自動將它們部署到 BizTalk 應用程式和設定從 Visual Studio 中的應用程式成品使用 BizTalk 總管 中。</span><span class="sxs-lookup"><span data-stu-id="7afff-124">You can create BizTalk assemblies in Visual Studio, use the Deploy command to automatically deploy them into a BizTalk application, and use BizTalk Explorer to configure application artifacts from within Visual Studio.</span></span> <span data-ttu-id="7afff-125">如需 Visual Studio 中運作的詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。</span><span class="sxs-lookup"><span data-stu-id="7afff-125">For more information about working within Visual Studio, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="7afff-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="7afff-126">In This Section</span></span>  
  
-   [<span data-ttu-id="7afff-127">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-127">Creating an Application</span></span>](../technical-guides/creating-an-application.md)  
  
-   [<span data-ttu-id="7afff-128">部署組件</span><span class="sxs-lookup"><span data-stu-id="7afff-128">Deploying an Assembly</span></span>](../technical-guides/deploying-an-assembly.md)  
  
-   [<span data-ttu-id="7afff-129">將成品新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-129">Adding Artifacts to an Application</span></span>](../technical-guides/adding-artifacts-to-an-application.md)  
  
-   [<span data-ttu-id="7afff-130">如何匯出至.msi 檔案的應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-130">How to Export an Application to an .msi File</span></span>](../technical-guides/how-to-export-an-application-to-an-msi-file.md)  
  
-   [<span data-ttu-id="7afff-131">如何匯出繫結至繫結檔案</span><span class="sxs-lookup"><span data-stu-id="7afff-131">How to Export Bindings to a Binding File</span></span>](../technical-guides/how-to-export-bindings-to-a-binding-file.md)  
  
-   [<span data-ttu-id="7afff-132">如何將繫結檔案新增至 Application1</span><span class="sxs-lookup"><span data-stu-id="7afff-132">How to Add a Binding File to an Application1</span></span>](../technical-guides/how-to-add-a-binding-file-to-an-application1.md)  
  
-   [<span data-ttu-id="7afff-133">如何從.msi 檔案匯入應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-133">How to Import an Application from an .msi File</span></span>](../technical-guides/how-to-import-an-application-from-an-msi-file.md)  
  
-   [<span data-ttu-id="7afff-134">如何安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-134">How to Install an Application</span></span>](../technical-guides/how-to-install-an-application.md)  
  
-   [<span data-ttu-id="7afff-135">如何從繫結檔案匯入繫結</span><span class="sxs-lookup"><span data-stu-id="7afff-135">How to Import Bindings from a Binding File</span></span>](../technical-guides/how-to-import-bindings-from-a-binding-file.md)  
  
-   [<span data-ttu-id="7afff-136">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-136">Testing an Application</span></span>](../technical-guides/testing-an-application.md)  
  
-   [<span data-ttu-id="7afff-137">如何將參考加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="7afff-137">How to Add a Reference to an Application</span></span>](../technical-guides/how-to-add-a-reference-to-an-application.md)