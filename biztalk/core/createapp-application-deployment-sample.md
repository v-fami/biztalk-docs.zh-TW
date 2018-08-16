---
title: CreateApp （應用程式部署範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, examples
- deploying, .msi file
- deploying, exporting
- .msi files, deploying
- examples, deploying
ms.assetid: 825627ee-21d0-4505-9df4-1dadc51335b6
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 842683d2eec04d77bad2b7726af0d687fae12884
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969708"
---
# <a name="createapp-application-deployment-sample"></a><span data-ttu-id="ff5b9-102">CreateApp (應用程式部署範例)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-102">CreateApp (Application Deployment Sample)</span></span>
<span data-ttu-id="ff5b9-103">本主題說明如何使用 CreateApp 範例，此範例會示範如何使用 BTSTask 命令列工具來部署和解除部署 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-103">This topic explains how to use the CreateApp sample, which demonstrates using the BTSTask command-line tool to deploy and undeploy a BizTalk application.</span></span> <span data-ttu-id="ff5b9-104">您可以使用此範例中的指令碼，將部署和解除部署 BizTalk 應用程式的夜間建置程序自動化。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-104">You could use scripts such as those included in this sample to automate your nightly build process to deploy and undeploy BizTalk applications.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff5b9-105">當您編寫部署指令碼時，應該永遠讓其以無訊息模式執行。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-105">You should always write your deployment scripts to run in silent mode.</span></span> <span data-ttu-id="ff5b9-106">如果不這麼做，便會出現對話方塊要求使用者輸入內容。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-106">If you do not, dialog boxes will display that require user input.</span></span> <span data-ttu-id="ff5b9-107">這樣會停止部署程序，直到有人手動關閉對話方塊為止，如此會導致匯入程序停止進行。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-107">This will stop the deployment process until the dialog box is manually dismissed, which can cause the import process to hang.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="ff5b9-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="ff5b9-108">What This Sample Does</span></span>  
 <span data-ttu-id="ff5b9-109">此範例含有指定碼，可以將應用程式部署工作自動化。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-109">The sample includes scripts that automate application deployment tasks.</span></span> <span data-ttu-id="ff5b9-110">若要執行這些工作，請執行會產生 BizTalk 專案和檔案的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-110">To perform these tasks, you run a script that generates the BizTalk project and files.</span></span> <span data-ttu-id="ff5b9-111">接著再執行會產生兩個 BizTalk 應用程式 .msi 檔案的指令碼，其中一個 .msi 檔案包含應用程式的所有成品，而另一個只包含應用程式的一個組件。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-111">Then you run a script that generates two BizTalk application .msi files – an .msi file that contains all of the artifacts in an application, and another that contains only one assembly in the application.</span></span> <span data-ttu-id="ff5b9-112">下一步您要執行另一個指令碼，這個指令碼會使用 .msi 檔案將應用程式匯入 BizTalk 群組，並將該應用程式安裝在本機電腦。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-112">Next you run a script that uses an .msi file to import an application into a BizTalk group and install the application onto the local computer.</span></span> <span data-ttu-id="ff5b9-113">在安裝期間，應用程式所含的前置處理指令碼會建立應用程式所使用的資料夾，並在檔案中記錄其動作。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-113">During installation, a pre-processing script included in the application creates folders used by the application and logs its actions to a file.</span></span> <span data-ttu-id="ff5b9-114">最後，再執行一個指令碼，刪除並解除安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-114">Finally, you run a script that deletes and uninstalls the application.</span></span> <span data-ttu-id="ff5b9-115">在解除安裝期間，應用程式所含的前置處理指令碼會移除安裝期間所建立的檔案和應用程式，並在檔案中記錄其動作。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-115">During uninstallation, a pre-processing script included in the application removes the files and folders that were created during installation and logs its actions to a file.</span></span>  
  
 <span data-ttu-id="ff5b9-116">此範例包含的指令碼如下：</span><span class="sxs-lookup"><span data-stu-id="ff5b9-116">The following are the scripts included with this sample:</span></span>  
  
-   <span data-ttu-id="ff5b9-117">**Build.bat。**</span><span class="sxs-lookup"><span data-stu-id="ff5b9-117">**Build.bat.**</span></span> <span data-ttu-id="ff5b9-118">會產生金鑰檔案、在 Visual Studio 中建置專案，以及簽署 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-118">Generates a key file, builds the project in Visual Studio, and signs the .dll files.</span></span>  
  
-   <span data-ttu-id="ff5b9-119">**CreateFullAndPartialMSI.bat。**</span><span class="sxs-lookup"><span data-stu-id="ff5b9-119">**CreateFullAndPartialMSI.bat.**</span></span> <span data-ttu-id="ff5b9-120">依序採取下列動作：</span><span class="sxs-lookup"><span data-stu-id="ff5b9-120">Takes the following actions, in order:</span></span>  
  
    1.  <span data-ttu-id="ff5b9-121">使用 BTSTask [AddApp 命令](../core/addapp-command.md)建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-121">Uses the BTSTask [AddApp command](../core/addapp-command.md) to create an application.</span></span>  
  
    2.  <span data-ttu-id="ff5b9-122">使用 BTSTask [AddResource 命令](../core/addresource-command.md)將新增至應用程式三個 BizTalk 組件 Build.bat 產生的以及其他資源。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-122">Uses the BTSTask [AddResource command](../core/addresource-command.md) to add to the application three BizTalk assemblies as well as other resources that were generated by Build.bat.</span></span>  
  
    3.  <span data-ttu-id="ff5b9-123">使用 BTSTask [ExportApp 命令](../core/exportapp-command.md)應用程式的成品匯出至.msi 檔案 createapplicationsample.msi。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-123">Uses the BTSTask [ExportApp command](../core/exportapp-command.md) to export the application's artifacts into an .msi file named CreateApplicationSample.msi.</span></span>  
  
    4.  <span data-ttu-id="ff5b9-124">使用 BTSTask [ListApp 命令](../core/listapp-command.md)產生名為 AppManifest.xml，列出所有應用程式中所包含的成品的應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-124">Uses the BTSTask [ListApp Command](../core/listapp-command.md) to generate an application manifest named AppManifest.xml, which lists all of the artifacts contained in the application.</span></span>  
  
    5.  <span data-ttu-id="ff5b9-125">使用 BTSTask [ExportApp 命令](../core/exportapp-command.md)匯出只至名為 CreateApplicationSamplePartial.msi.msi 檔案將協調流程組件。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-125">Uses the BTSTask [ExportApp command](../core/exportapp-command.md) to export only the orchestrations assembly into an .msi file named CreateApplicationSamplePartial.msi.</span></span> <span data-ttu-id="ff5b9-126">只將協調流程組件匯出至 CreateApplicationSamplePartial.msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-126">It does this by providing ResourceSpecPartial.xml for the ResourceSpec parameter.</span></span> <span data-ttu-id="ff5b9-127">ResouceSpecPartial.xml 是 ResourceSpecComplete.xml 的已編輯版本，隨此範例提供。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-127">ResouceSpecPartial.xml is an edited version of ResourceSpecComplete.xml that has been provided with this sample.</span></span> <span data-ttu-id="ff5b9-128">這個檔案已經過編輯，因此只包含對協調流程組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-128">This file has been edited so that it contains a reference to the orchestrations assembly only.</span></span> <span data-ttu-id="ff5b9-129">搭配這個參數時，BTSTask 只會匯出 ResourceSpecPartial.xml 檔案中所列的成品，在此例中是協調流程組件。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-129">When provided with this parameter, BTSTask exports only the artifacts listed in the ResourceSpecPartial.xml file – in this case, the orchestrations assembly.</span></span>  
  
    6.  <span data-ttu-id="ff5b9-130">從群組的「BizTalk 管理」資料庫移除應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-130">Deletes the application from the BizTalk Management database for the group.</span></span>  
  
-   <span data-ttu-id="ff5b9-131">**CreateNewAppFromMSI.bat。**</span><span class="sxs-lookup"><span data-stu-id="ff5b9-131">**CreateNewAppFromMSI.bat.**</span></span> <span data-ttu-id="ff5b9-132">使用 CreateFullAndPartialMSI.bat 產生的 CreateApplicationSample.msi，將名為 CreateApplicationSample 的應用程式安裝至本機電腦，並將應用程式匯入 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-132">Uses CreateApplicationSample.msi generated by CreateFullAndPartialMSI.bat to install an application named CreateApplicationSample on the local computer as well as import the application into the BizTalk group.</span></span> <span data-ttu-id="ff5b9-133">在安裝期間，PreProcScript.bat 會自動執行 (稍後說明)。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-133">During installation, PreProcScript.bat runs automatically, as described later.</span></span>  
  
-   <span data-ttu-id="ff5b9-134">**RemoveApp.bat。**</span><span class="sxs-lookup"><span data-stu-id="ff5b9-134">**RemoveApp.bat.**</span></span> <span data-ttu-id="ff5b9-135">依序採取下列動作：</span><span class="sxs-lookup"><span data-stu-id="ff5b9-135">Takes the following actions, in order:</span></span>  
  
    1.  <span data-ttu-id="ff5b9-136">使用 BTSTask [RemoveApp 命令](../core/removeapp-command.md)從群組的 BizTalk 管理 」 資料庫刪除 CreateApplicationSample 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-136">Uses the BTSTask [RemoveApp Command](../core/removeapp-command.md) to delete the CreateApplicationSample application from the BizTalk Management database for the group.</span></span>  
  
    2.  <span data-ttu-id="ff5b9-137">使用 BTSTask [UninstallApp 命令](../core/uninstallapp-command.md)從本機電腦解除安裝 CreateApplicationSample 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-137">Uses the BTSTask [UninstallApp Command](../core/uninstallapp-command.md) to uninstall the CreateApplicationSample application from the local computer.</span></span> <span data-ttu-id="ff5b9-138">在安裝期間，PreProcScript.bat 會自動執行 (如下所述)。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-138">During installation, PreProcScript.bat runs automatically, as described next.</span></span>  
  
-   <span data-ttu-id="ff5b9-139">**PreProcScript.bat。**</span><span class="sxs-lookup"><span data-stu-id="ff5b9-139">**PreProcScript.bat.**</span></span> <span data-ttu-id="ff5b9-140">會採取以下動作：</span><span class="sxs-lookup"><span data-stu-id="ff5b9-140">Takes the following actions:</span></span>  
  
    -   <span data-ttu-id="ff5b9-141">每次執行時，都會針對使用者所提供的組件設定公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-141">Each time it runs, sets the public key token for the assembly that has been provided by the user.</span></span>  
  
    -   <span data-ttu-id="ff5b9-142">在應用程式安裝期間，會建立下列資料夾，CreateApplicationSample 應用程式會使用這些資料夾來存放訊息：</span><span class="sxs-lookup"><span data-stu-id="ff5b9-142">During application installation, creates the following folders that will be used by the CreateApplicationSample application to contain messages:</span></span>  
  
         <span data-ttu-id="ff5b9-143">C:\CreateApplicationSample\Out</span><span class="sxs-lookup"><span data-stu-id="ff5b9-143">C:\CreateApplicationSample\Out</span></span>  
  
         <span data-ttu-id="ff5b9-144">C:\CreateApplicationSample\In</span><span class="sxs-lookup"><span data-stu-id="ff5b9-144">C:\CreateApplicationSample\In</span></span>  
  
    -   <span data-ttu-id="ff5b9-145">在應用程式解除安裝期間，會刪除安裝期間所建立的檔案和資料夾，</span><span class="sxs-lookup"><span data-stu-id="ff5b9-145">During application uninstallation, deletes the files and folders that were created during installation.</span></span> <span data-ttu-id="ff5b9-146">也會解除安裝期間安裝在全域組件快取 (GAC) 中的所有組件，並在檔案中記錄其動作。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-146">Also uninstalls from the global assembly cache (GAC) any assemblies that were installed in the GAC during installation and logs its actions to a file.</span></span> <span data-ttu-id="ff5b9-147">為了要解除安裝 GAC 中的組件，這個檔案必須參考使用者所提供的公開金鑰 Token。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-147">To uninstall the assemblies from the GAC, it refers to the public key token provided by the user.</span></span>  
  
    -   <span data-ttu-id="ff5b9-148">在安裝和解除安裝期間，會在下列位置建立記錄檔：</span><span class="sxs-lookup"><span data-stu-id="ff5b9-148">During both installation and uninstallation, creates a log file in the following location:</span></span>  
  
         <span data-ttu-id="ff5b9-149">C:\ScriptLog.txt</span><span class="sxs-lookup"><span data-stu-id="ff5b9-149">C:\ScriptLog.txt</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ff5b9-150">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="ff5b9-150">Where to Find This Sample</span></span>  
 <span data-ttu-id="ff5b9-151">您可以在下列資料夾中找到範例檔案*\<範例路徑\>* \Application 部署\\:</span><span class="sxs-lookup"><span data-stu-id="ff5b9-151">You can find the sample files in the following folders under *\<Samples Path\>* \Application Deployment\\:</span></span>  
  
-   <span data-ttu-id="ff5b9-152">CreateApp (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-152">CreateApp (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-153">Build.bat</span><span class="sxs-lookup"><span data-stu-id="ff5b9-153">Build.bat</span></span>  
  
    -   <span data-ttu-id="ff5b9-154">CreateFullAndPartialMSI.bat</span><span class="sxs-lookup"><span data-stu-id="ff5b9-154">CreateFullAndPartialMSI.bat</span></span>  
  
    -   <span data-ttu-id="ff5b9-155">CreateNewAppFromMSI.bat</span><span class="sxs-lookup"><span data-stu-id="ff5b9-155">CreateNewAppFromMSI.bat</span></span>  
  
    -   <span data-ttu-id="ff5b9-156">RemoveApp.bat</span><span class="sxs-lookup"><span data-stu-id="ff5b9-156">RemoveApp.bat</span></span>  
  
-   <span data-ttu-id="ff5b9-157">CreateApp\Bindings (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-157">CreateApp\Bindings (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-158">CreateApplicationSampleBindings.xml</span><span class="sxs-lookup"><span data-stu-id="ff5b9-158">CreateApplicationSampleBindings.xml</span></span>  
  
-   <span data-ttu-id="ff5b9-159">CreateApp\Dlls (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-159">CreateApp\Dlls (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-160">Empty</span><span class="sxs-lookup"><span data-stu-id="ff5b9-160">Empty</span></span>  
  
-   <span data-ttu-id="ff5b9-161">CreateApp\ResourceSpecs (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-161">CreateApp\ResourceSpecs (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-162">ResourceSpecPartial.xml</span><span class="sxs-lookup"><span data-stu-id="ff5b9-162">ResourceSpecPartial.xml</span></span>  
  
    -   <span data-ttu-id="ff5b9-163">ResourceSpecComplete.xml</span><span class="sxs-lookup"><span data-stu-id="ff5b9-163">ResourceSpecComplete.xml</span></span>  
  
-   <span data-ttu-id="ff5b9-164">CreateApp\Scripts (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-164">CreateApp\Scripts (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-165">PreProcScript.bat</span><span class="sxs-lookup"><span data-stu-id="ff5b9-165">PreProcScript.bat</span></span>  
  
-   <span data-ttu-id="ff5b9-166">CreateApp\HelloApplicationDeployment (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-166">CreateApp\HelloApplicationDeployment (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-167">HelloApplicationDeployment.suo</span><span class="sxs-lookup"><span data-stu-id="ff5b9-167">HelloApplicationDeployment.suo</span></span>  
  
    -   <span data-ttu-id="ff5b9-168">HelloApplicationDeployment.sln</span><span class="sxs-lookup"><span data-stu-id="ff5b9-168">HelloApplicationDeployment.sln</span></span>  
  
-   <span data-ttu-id="ff5b9-169">CreateApp\HelloApplicationDeployment\Maps (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-169">CreateApp\HelloApplicationDeployment\Maps (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-170">POToInvoice.btm</span><span class="sxs-lookup"><span data-stu-id="ff5b9-170">POToInvoice.btm</span></span>  
  
    -   <span data-ttu-id="ff5b9-171">Maps.btproj</span><span class="sxs-lookup"><span data-stu-id="ff5b9-171">Maps.btproj</span></span>  
  
-   <span data-ttu-id="ff5b9-172">CreateApp\HelloApplicationDeployment\Orchestrations (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-172">CreateApp\HelloApplicationDeployment\Orchestrations (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-173">Orchestrations.btproj</span><span class="sxs-lookup"><span data-stu-id="ff5b9-173">Orchestrations.btproj</span></span>  
  
    -   <span data-ttu-id="ff5b9-174">HelloOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="ff5b9-174">HelloOrchestration.odx</span></span>  
  
-   <span data-ttu-id="ff5b9-175">CreateApp\HelloApplicationDeployment\Schemas (資料夾)</span><span class="sxs-lookup"><span data-stu-id="ff5b9-175">CreateApp\HelloApplicationDeployment\Schemas (Folder)</span></span>  
  
    -   <span data-ttu-id="ff5b9-176">Schemas.btproj</span><span class="sxs-lookup"><span data-stu-id="ff5b9-176">Schemas.btproj</span></span>  
  
    -   <span data-ttu-id="ff5b9-177">POSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="ff5b9-177">POSchema.xsd</span></span>  
  
    -   <span data-ttu-id="ff5b9-178">InvoiceSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="ff5b9-178">InvoiceSchema.xsd</span></span>  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="ff5b9-179">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="ff5b9-179">How to Use This Sample</span></span>  
 <span data-ttu-id="ff5b9-180">請根據下列程序來使用此範例。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-180">Use the following procedure to use this sample.</span></span>  
  
### <a name="to-use-the-sample"></a><span data-ttu-id="ff5b9-181">若要使用範例</span><span class="sxs-lookup"><span data-stu-id="ff5b9-181">To use the sample</span></span>  
  
1.  <span data-ttu-id="ff5b9-182">執行 Build.bat。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-182">Run Build.bat.</span></span> <span data-ttu-id="ff5b9-183">這個檔案會產生金鑰檔案、在 HelloApplicationDeployment 資料夾下建置專案、簽署所產生的 .dll 檔案，以及將 .dll 檔案置於 Dlls 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-183">This generates a key file, builds the projects under the folder HelloApplicationDeployment, signs the resulting .dll files, and places the.dll files in the Dlls folder.</span></span>  
  
2.  <span data-ttu-id="ff5b9-184">開啟 PreProcScript.bat 檔案，這個檔案位在 CreateApp\Scripts 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-184">Open the PreProcScript.bat file, which is located in the CreateApp\Scripts folder.</span></span> <span data-ttu-id="ff5b9-185">從下列程式碼行中移除 REM 並提供組件的公開金鑰 Token：</span><span class="sxs-lookup"><span data-stu-id="ff5b9-185">In the following line of code, remove REM and provide the public key token for the assembly:</span></span>  
  
     <span data-ttu-id="ff5b9-186">**REM 設定 PublicKeyToken =**</span><span class="sxs-lookup"><span data-stu-id="ff5b9-186">**REM set PublicKeyToken=**</span></span>  
  
     <span data-ttu-id="ff5b9-187">範例：</span><span class="sxs-lookup"><span data-stu-id="ff5b9-187">Example:</span></span>  
  
     <span data-ttu-id="ff5b9-188">**設定 PublicKeyToken = 1234a5b6c1234567**</span><span class="sxs-lookup"><span data-stu-id="ff5b9-188">**set PublicKeyToken=1234a5b6c1234567**</span></span>  
  
3.  <span data-ttu-id="ff5b9-189">執行 CreateFullAndPartialMSI.bat。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-189">Run CreateFullAndPartialMSI.bat.</span></span> <span data-ttu-id="ff5b9-190">這個檔案會建立兩個應用程式 .msi 檔案：CreateApplicationSample.msi 和 CreateApplicationSamplePartial.msi。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-190">This creates two application .msi files, CreateApplicationSample.msi and CreateApplicationSamplePartial.msi.</span></span>  
  
4.  <span data-ttu-id="ff5b9-191">執行 CreateNewAppFromMSI.bat。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-191">Run CreateNewAppFromMSI.bat.</span></span> <span data-ttu-id="ff5b9-192">這個檔案會將 CreateApplicationSample 應用程式匯入 BizTalk 群組，並將該應用程式安裝到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-192">This imports the CreateApplicationSample application into the BizTalk group and installs it on the local computer.</span></span>  
  
5.  <span data-ttu-id="ff5b9-193">檢查 C:\ScriptLog.txt 這個指令碼記錄檔，確認指令碼有記錄其安裝動作。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-193">Check the script log file, located at C:\ScriptLog.txt to verify that the script logged its installation actions.</span></span>  
  
6.  <span data-ttu-id="ff5b9-194">確認 [BizTalk Server 管理主控台] 和 [新增或移除程式] 中都有出現 CreateApplicationSample 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-194">Verify that the CreateApplicationSample application appears both in the BizTalk Server Administration console and Add or Remove Programs.</span></span>  
  
7.  <span data-ttu-id="ff5b9-195">執行 RemoveApp.bat。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-195">Run RemoveApp.bat.</span></span> <span data-ttu-id="ff5b9-196">這個檔案會從「BizTalk 管理」資料庫刪除 CreateApplicationSample，同時從本機電腦解除安裝此應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-196">This deletes the CreateApplicationSample from the BizTalk Management database and uninstalls it from the local computer.</span></span>  
  
8.  <span data-ttu-id="ff5b9-197">檢查 C:\ScriptLog.txt 這個指令碼記錄檔，確認指令碼有記錄其解除安裝動作。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-197">Check the script log file, located at C:\ScriptLog.txt to verify that the script logged its uninstallation actions.</span></span> <span data-ttu-id="ff5b9-198">這些動作的記錄位置應該在稍早安裝期間所記錄的安裝動作之後。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-198">They should appear after the installation actions logged earlier, during installation.</span></span>  
  
9. <span data-ttu-id="ff5b9-199">確認 [BizTalk Server 管理主控台] 和 [新增或移除程式] 中都不再出現 CreateApplicationSample 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-199">Verify that the CreateApplicationSample application no longer appears in either the BizTalk Server Administration console or Add or Remove Programs.</span></span>  
  
10. <span data-ttu-id="ff5b9-200">確認在安裝期間所建立的資料夾都已刪除。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-200">Verify that the folders that were created during installation have been deleted.</span></span>  
  
11. <span data-ttu-id="ff5b9-201">確認已從 GAC 解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="ff5b9-201">Verify that the assemblies have been uninstalled from the GAC.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5b9-202">請參閱</span><span class="sxs-lookup"><span data-stu-id="ff5b9-202">See Also</span></span>  
 <span data-ttu-id="ff5b9-203">[應用程式部署 （BizTalk Server 範例資料夾）](../core/application-deployment-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="ff5b9-203">[Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="ff5b9-204">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="ff5b9-204">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)