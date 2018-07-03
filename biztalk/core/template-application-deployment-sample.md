---
title: 範本 （應用程式部署範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, examples
- scripts, deploying
- deploying, scripts
- examples, deploying
ms.assetid: 7e77ff8e-b2bc-4d38-b5fd-329d6d54221f
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d096dac4d1c51101ddadff9eb6c49c04202d375
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000055"
---
# <a name="template-application-deployment-sample"></a><span data-ttu-id="42c43-102">範本 (應用程式部署範例)</span><span class="sxs-lookup"><span data-stu-id="42c43-102">Template (Application Deployment Sample)</span></span>
<span data-ttu-id="42c43-103">本主題描述如何使用「範本」範例進行應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="42c43-103">This topic describes how to use the Template sample for application deployment.</span></span>  
  
 <span data-ttu-id="42c43-104">您可以建立並使用兩種類型的部署指令碼自訂 BizTalk 應用程式部署： 前置處理指令碼和後置處理指令碼。</span><span class="sxs-lookup"><span data-stu-id="42c43-104">You can create and use two types of deployment scripts to customize BizTalk application deployment: pre-processing scripts and post-processing scripts.</span></span> <span data-ttu-id="42c43-105">前置處理指令碼的叫用時機為應用程式安裝及匯入開始前，以及完成解除安裝之後。</span><span class="sxs-lookup"><span data-stu-id="42c43-105">Pre-processing scripts are invoked before application installation and import begins and after uninstallation completes.</span></span> <span data-ttu-id="42c43-106">後置處理指令碼的叫用時機則為應用程式安裝及匯入完成後，以及解除安裝開始之前。</span><span class="sxs-lookup"><span data-stu-id="42c43-106">Post-processing scripts are invoked after application installation and import completes and before uninstallation begins.</span></span>  
  
 <span data-ttu-id="42c43-107">您可以撰寫前置及後置處理指令碼，讓上述每項作業都能叫用這些指令碼。</span><span class="sxs-lookup"><span data-stu-id="42c43-107">You can write pre- and post- processing scripts so that they are invoked for each of these operations.</span></span> <span data-ttu-id="42c43-108">或者，您也可以設定指令碼，使其只在上述某項作業後執行。</span><span class="sxs-lookup"><span data-stu-id="42c43-108">Alternatively, you can configure scripts to execute after only one of them.</span></span> <span data-ttu-id="42c43-109">如需有關如何撰寫指令碼的詳細資訊，請參閱 <<c0> [ 使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="42c43-109">For more information about writing scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>  
  
 <span data-ttu-id="42c43-110">本主題將示範如何撰寫和部署指令碼，以便只在某項作業之前或之後叫用此指令碼。</span><span class="sxs-lookup"><span data-stu-id="42c43-110">This topic demonstrates how to write and deploy a script so that it is invoked before or after only one operation.</span></span> <span data-ttu-id="42c43-111">若要這麼做，您可以撰寫指令碼來檢查三個環境 (Environment) 變數的值，判斷指令碼是在哪項作業的環境 (Context) 中受到呼叫。</span><span class="sxs-lookup"><span data-stu-id="42c43-111">You do this by writing a script that checks the values of three environment variables to determine the operation in the context of which it is being called.</span></span> <span data-ttu-id="42c43-112">指令碼會根據此環境 (Context) 繼續執行或中止執行。</span><span class="sxs-lookup"><span data-stu-id="42c43-112">Based on this context, the script either continues or discontinues execution.</span></span>  
  
 <span data-ttu-id="42c43-113">本主題描述如何採取下列步驟：</span><span class="sxs-lookup"><span data-stu-id="42c43-113">This topic describes how to take the following steps:</span></span>  
  
1.  <span data-ttu-id="42c43-114">設定記錄檔位置，以便產生指令檔作業的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="42c43-114">Set the log file location, so that you can generate a log file of the script operations.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42c43-115">您應該採用的最佳作法是一律產生記錄檔，如此就能驗證指令檔作業以及對問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="42c43-115">As a best practice, you should always generate a log file so that you can verify script operations and troubleshoot any problems.</span></span>  
  
2.  <span data-ttu-id="42c43-116">建立新的 BizTalk 應用程式，並且在其中加入範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="42c43-116">Create a new BizTalk application and add the sample scripts to it.</span></span>  
  
3.  <span data-ttu-id="42c43-117">匯出包含應用程式成品的 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="42c43-117">Export an .msi file containing the application artifacts.</span></span>  
  
4.  <span data-ttu-id="42c43-118">從 BizTalk 群組刪除應用程式，如此您就可以將 .msi 檔案匯入回相同群組，並從 .msi 檔案安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="42c43-118">Delete the application from the BizTalk group, so that you can import the .msi file back into the same group as well as install it from the .msi file.</span></span>  
  
5.  <span data-ttu-id="42c43-119">匯入應用程式，並檢查記錄檔，查看是否記錄了匯入作業。</span><span class="sxs-lookup"><span data-stu-id="42c43-119">Import the application, and check the log file to see that the import operation was logged.</span></span>  
  
6.  <span data-ttu-id="42c43-120">安裝應用程式，並檢查記錄檔，查看安裝記錄是否附加到記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="42c43-120">Install the application, and check the log file to see that the installation log was appended to the log file.</span></span>  
  
7.  <span data-ttu-id="42c43-121">檢視記錄檔，注意指令碼執行了哪些作業，以及作業的執行時間。</span><span class="sxs-lookup"><span data-stu-id="42c43-121">View the log files and note what operations the scripts performed and when they were performed.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="42c43-122">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="42c43-122">What This Sample Does</span></span>  
 <span data-ttu-id="42c43-123">本範例提供的兩個 .bat 檔案包含匯入、安裝和解除安裝的環境 (Environment) 變數值。</span><span class="sxs-lookup"><span data-stu-id="42c43-123">Two .bat files provided for this sample contain the values of the environment variables for import, installation, and uninstallation.</span></span> <span data-ttu-id="42c43-124">SamplePreProcessing.bat 包含前置處理指令碼的變數。</span><span class="sxs-lookup"><span data-stu-id="42c43-124">SamplePreProcessing.bat contains variables for a pre-processing script.</span></span> <span data-ttu-id="42c43-125">SamplePostProcessing.bat 包含後置處理指令碼的變數。</span><span class="sxs-lookup"><span data-stu-id="42c43-125">SamplePostProcessing.bat contains variables for a post-processing script.</span></span> <span data-ttu-id="42c43-126">這兩個檔案也會示範如何記錄指令碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="42c43-126">The files also demonstrate how to log messages from scripts.</span></span> <span data-ttu-id="42c43-127">您可以將這些檔案中的相關區段複製到您的指令碼中。</span><span class="sxs-lookup"><span data-stu-id="42c43-127">You can copy the relevant sections of these files into your scripts.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="42c43-128">指令碼檔案中的部分註解不正確，如下所示：</span><span class="sxs-lookup"><span data-stu-id="42c43-128">Some of the comments within the script files are incorrect, as follows:</span></span>  
>   
>  <span data-ttu-id="42c43-129">SamplePreProcessing.bat 中的指令碼註解 "Pre uninstall part of the script called for an existing application" (為現有應用程式呼叫之指令碼的前置解除安裝部分) 應該是 "Post uninstall part of the script called for an existing application" (為現有應用程式呼叫之指令碼的後置解除安裝部分)。</span><span class="sxs-lookup"><span data-stu-id="42c43-129">In SamplePreProcessing.bat, the script comment, “Pre uninstall part of the script called for an existing application” should read "Post uninstall part of the script called for an existing application."</span></span>  
>   
>  <span data-ttu-id="42c43-130">SamplePostProcessing.bat 中的指令碼註解 "Post uninstall part of the script called for an existing application" (為現有應用程式呼叫之指令碼的後置解除安裝部分) 應該是 "Pre uninstall part of the script called for an existing application" (為現有應用程式呼叫之指令碼的前置解除安裝部分)。</span><span class="sxs-lookup"><span data-stu-id="42c43-130">In SamplePostProcessing.bat, the script comment, “Post uninstall part of the script called for an existing application” should read "Pre uninstall part of the script called for an existing application."</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="42c43-131">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="42c43-131">Where to Find This Sample</span></span>  
 <span data-ttu-id="42c43-132">此範例位於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝資料夾內，如下所示：</span><span class="sxs-lookup"><span data-stu-id="42c43-132">The sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder, as follows:</span></span>  
  
 <span data-ttu-id="42c43-133">*\<範例路徑\>* \Application Deployment\Template</span><span class="sxs-lookup"><span data-stu-id="42c43-133">*\<Samples Path\>* \Application Deployment\Template</span></span>  
  
 <span data-ttu-id="42c43-134">如前所述，此範例包含下列兩個檔案：</span><span class="sxs-lookup"><span data-stu-id="42c43-134">As previously mentioned, the sample includes the following two files:</span></span>  
  
-   <span data-ttu-id="42c43-135">SamplePreProcessing.bat</span><span class="sxs-lookup"><span data-stu-id="42c43-135">SamplePreProcessing.bat</span></span>  
  
-   <span data-ttu-id="42c43-136">SamplePostProcessing.bat</span><span class="sxs-lookup"><span data-stu-id="42c43-136">SamplePostProcessing.bat</span></span>  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="42c43-137">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="42c43-137">How to Use This Sample</span></span>  
 <span data-ttu-id="42c43-138">若要執行範例，請採取下列步驟。</span><span class="sxs-lookup"><span data-stu-id="42c43-138">To run the sample, take the following steps.</span></span>  
  
### <a name="to-set-the-logging-location"></a><span data-ttu-id="42c43-139">若要設定記錄位置</span><span class="sxs-lookup"><span data-stu-id="42c43-139">To set the logging location</span></span>  
  
-   <span data-ttu-id="42c43-140">開啟這兩個指令碼範例，變更 LogFile 變數，讓其指向要寫入記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="42c43-140">Open both the script samples and change the LogFile variable to point to the location where the log files are to be written.</span></span> <span data-ttu-id="42c43-141">您必須提供完整路徑，包含檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="42c43-141">You must provide the full path including the file name.</span></span> <span data-ttu-id="42c43-142">如果路徑包含空格，您必須將它括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="42c43-142">If it includes spaces, you must enclose the path in double quotation marks (").</span></span>  
  
     <span data-ttu-id="42c43-143">範例</span><span class="sxs-lookup"><span data-stu-id="42c43-143">Example:</span></span>  
  
     <span data-ttu-id="42c43-144">設定記錄檔 ="*\<範例路徑\>* \ApplicationDeployment\Templates\SampleLogOut.txt"</span><span class="sxs-lookup"><span data-stu-id="42c43-144">set LogFile="*\<Samples Path\>* \ApplicationDeployment\Templates\SampleLogOut.txt"</span></span>  
  
### <a name="to-create-a-new-application"></a><span data-ttu-id="42c43-145">若要建立新的應用程式</span><span class="sxs-lookup"><span data-stu-id="42c43-145">To create a new application</span></span>  
  
1. <span data-ttu-id="42c43-146">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="42c43-146">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="42c43-147">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]並展開 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="42c43-147">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and expand the BizTalk group.</span></span>  
  
3. <span data-ttu-id="42c43-148">以滑鼠右鍵按一下**應用程式**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="42c43-148">Right-click **Applications** and then click **New**.</span></span>  
  
4. <span data-ttu-id="42c43-149">在 **應用程式名稱**，型別`SamplesTemplate`，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="42c43-149">In **Application name**, type `SamplesTemplate`, and then click **OK**.</span></span>  
  
### <a name="to-add-the-scripts-to-the-application"></a><span data-ttu-id="42c43-150">若要將指令碼加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="42c43-150">To add the scripts to the application</span></span>  
  
1.  <span data-ttu-id="42c43-151">展開您剛才建立的 SamplesTemplate 應用程式的資料夾，然後以滑鼠右鍵按一下**資源**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="42c43-151">Expand the folder of the SamplesTemplate application that you just created and right-click **Resources** in the left pane.</span></span>  
  
2.  <span data-ttu-id="42c43-152">指向**新增**然後按一下**前置處理指令碼**。</span><span class="sxs-lookup"><span data-stu-id="42c43-152">Point to **Add** and click **Pre-processing Scripts**.</span></span>  
  
3.  <span data-ttu-id="42c43-153">按一下 **新增**並瀏覽至 SamplePreProcessing.bat。</span><span class="sxs-lookup"><span data-stu-id="42c43-153">Click **Add** and browse to SamplePreProcessing.bat.</span></span>  
  
4.  <span data-ttu-id="42c43-154">選取檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="42c43-154">Select the file and click **Open**.</span></span>  
  
5.  <span data-ttu-id="42c43-155">在 **檔案類型**，按一下**system.biztalk: preprocessingscript**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="42c43-155">In **File type**, click **System.BizTalk:PreprocessingScript**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="42c43-156">SamplePreProcessing.bat 隨即加入至應用程式，而且會顯示在應用程式的 Resources 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="42c43-156">SamplePreProcessing.bat is added to the application and is displayed in the Resources folder of the application.</span></span>  
  
6.  <span data-ttu-id="42c43-157">資源上按一下滑鼠右鍵，指向**新增**，然後按一下**後置處理指令碼**。</span><span class="sxs-lookup"><span data-stu-id="42c43-157">Right-click Resources again, point to **Add**, and then click **Post-processing Scripts**.</span></span>  
  
7.  <span data-ttu-id="42c43-158">按一下 **新增**並瀏覽至 SamplePostProcessing.bat。</span><span class="sxs-lookup"><span data-stu-id="42c43-158">Click **Add** and browse to SamplePostProcessing.bat.</span></span>  
  
8.  <span data-ttu-id="42c43-159">選取檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="42c43-159">Select the file and click **Open**.</span></span>  
  
9. <span data-ttu-id="42c43-160">在 **檔案類型**，按一下**system.biztalk: postprocessingscript**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="42c43-160">In **File type**, click **System.BizTalk:PostprocessingScript**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="42c43-161">SamplePostProcessing.bat 隨即加入至應用程式，而且會顯示在應用程式的 Resources 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="42c43-161">SamplePostProcessing.bat is added to the application and is displayed in the Resources folder of the application.</span></span>  
  
### <a name="to-export-an-msi-file"></a><span data-ttu-id="42c43-162">若要匯出 .msi 檔案</span><span class="sxs-lookup"><span data-stu-id="42c43-162">To export an .msi file</span></span>  
  
1.  <span data-ttu-id="42c43-163">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下 [samplestemplate] 應用程式、 指向**匯出**，然後按一下**MSI 檔案**。</span><span class="sxs-lookup"><span data-stu-id="42c43-163">In the BizTalk Server Administration console, right-click the SamplesTemplate application, point to **Export**, and then click **MSI file**.</span></span>  
  
2.  <span data-ttu-id="42c43-164">在歡迎使用匯出精靈 頁面中，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="42c43-164">On the Welcome to the Export Wizard page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="42c43-165">在 [選取資源] 頁面中，按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="42c43-165">On the Select Resources page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="42c43-166">在 [指定 IIS 主控件] 頁面中，按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="42c43-166">On the Specify IIS Hosts page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="42c43-167">在相依性 頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="42c43-167">On the Dependencies page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="42c43-168">在 [目的地] 頁面中**目的地應用程式名稱**，輸入應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="42c43-168">On the Destination page, in **Destination application name**, type the application name.</span></span>  
  
7.  <span data-ttu-id="42c43-169">在  **MSI 檔案來產生**，輸入 MSI 檔案的完整路徑，然後按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="42c43-169">In **MSI file to generate**, type the full path for the MSI file, and then click **Export**.</span></span> <span data-ttu-id="42c43-170">範例： C:\MSI\SamplesTemplate.msi</span><span class="sxs-lookup"><span data-stu-id="42c43-170">Example: C:\MSI\SamplesTemplate.msi</span></span>  
  
8.  <span data-ttu-id="42c43-171">在 摘要 頁面中，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="42c43-171">On the Summary page, click **Finish**.</span></span>  
  
### <a name="delete-the-application"></a><span data-ttu-id="42c43-172">刪除應用程式</span><span class="sxs-lookup"><span data-stu-id="42c43-172">Delete the application</span></span>  
  
-   <span data-ttu-id="42c43-173">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下 [samplestemplate] 應用程式，然後**刪除**。</span><span class="sxs-lookup"><span data-stu-id="42c43-173">In the BizTalk Server Administration console, right-click the SamplesTemplate application, and then click **Delete**.</span></span>  
  
### <a name="to-import-the-msi-file"></a><span data-ttu-id="42c43-174">若要匯入 .msi 檔案</span><span class="sxs-lookup"><span data-stu-id="42c43-174">To import the .msi file</span></span>  
  
1.  <span data-ttu-id="42c43-175">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**應用程式**，指向**匯入**，然後按一下**MSI 檔案**。</span><span class="sxs-lookup"><span data-stu-id="42c43-175">In the BizTalk Server Administration console, right-click **Applications**, point to **Import**, and then click **MSI file**.</span></span>  
  
2.  <span data-ttu-id="42c43-176">在歡迎使用匯入精靈 頁面中，在**MSI 檔案匯入**，輸入您先前匯出，然後再按一下的.msi 檔案的路徑**下一步**。</span><span class="sxs-lookup"><span data-stu-id="42c43-176">On the Welcome to the Import Wizard page, in **MSI file to import**, type the path of the .msi file that you previously exported, and then click **Next**.</span></span> <span data-ttu-id="42c43-177">如果有必要，您可以瀏覽 MSI 檔案即可 **（...）**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="42c43-177">If necessary, you can browse for the MSI file by clicking the **(….)** button.</span></span>  
  
3.  <span data-ttu-id="42c43-178">在應用程式設定] 頁面中**應用程式名稱**下拉式清單中，選取 [應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="42c43-178">On the Application Settings page, in the **Application name** drop-down list, select the application name.</span></span>  
  
4.  <span data-ttu-id="42c43-179">在 [**可用的應用程式，將參考加入至**，選取要加入的參考，如果有的話，應用程式，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="42c43-179">In **Available applications to add references to**, select the applications to which to add references, if any, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="42c43-180">在應用程式目標環境設定 頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="42c43-180">On the Application Target Environment Settings page, click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42c43-181">您不必為此範例指定目標環境 (Environment)。</span><span class="sxs-lookup"><span data-stu-id="42c43-181">You do not need to specify a target environment for the purposes of this sample.</span></span> <span data-ttu-id="42c43-182">如需這項功能的背景資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="42c43-182">For background information on this feature, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span> <span data-ttu-id="42c43-183">如需新增繫結檔案的指示，請參閱[如何將繫結檔案新增至應用程式](../core/how-to-add-a-binding-file-to-an-application2.md)。</span><span class="sxs-lookup"><span data-stu-id="42c43-183">For instructions on adding binding files, see [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md).</span></span>  
  
6.  <span data-ttu-id="42c43-184">在匯入摘要] 頁面上，確認 [摘要資訊是否正確，，然後按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="42c43-184">On the Import Summary page, confirm that the summary information is correct, and then click **Import**.</span></span>  
  
7.  <span data-ttu-id="42c43-185">在 結果 頁面中，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="42c43-185">On the Results page, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="42c43-186">開啟在執行指令檔時所建立的記錄檔，確認是否記錄了匯入作業。</span><span class="sxs-lookup"><span data-stu-id="42c43-186">Open the log file that was created when the scripts executed, and verify that import operation was logged.</span></span>  
  
### <a name="to-install-the-application"></a><span data-ttu-id="42c43-187">若要安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="42c43-187">To install the application</span></span>  
  
1.  <span data-ttu-id="42c43-188">按兩下 .msi 檔案並執行「安裝精靈」。</span><span class="sxs-lookup"><span data-stu-id="42c43-188">Double-click the .msi file and run the Installation Wizard.</span></span>  
  
2.  <span data-ttu-id="42c43-189">開啟記錄檔，確認安裝作業已加入至記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="42c43-189">Open the log file and verify that installation operation was added to the logging information.</span></span>  
  
### <a name="to-verify-that-the-scripts-functioned-correctly"></a><span data-ttu-id="42c43-190">若要確認指令檔可正常運作</span><span class="sxs-lookup"><span data-stu-id="42c43-190">To verify that the scripts functioned correctly</span></span>  
  
-   <span data-ttu-id="42c43-191">開啟記錄檔，確認在指定的作業期間指令檔都有執行。</span><span class="sxs-lookup"><span data-stu-id="42c43-191">Open the log files and verify that they executed during the specified operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c43-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42c43-192">See Also</span></span>  
 <span data-ttu-id="42c43-193">[應用程式部署 （BizTalk Server Samples 資料夾）](../core/application-deployment-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="42c43-193">[Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="42c43-194">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="42c43-194">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)