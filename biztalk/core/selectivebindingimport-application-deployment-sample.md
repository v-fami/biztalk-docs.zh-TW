---
title: "SelectiveBindingImport （應用程式部署範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- examples, applications
- binding files, examples
- examples, importing
- applications, binding files
- applications, examples
- applications, importing
- deploying, scripts
- examples, binding files
ms.assetid: 963bfc80-8cc4-4d90-96b4-e85ae04405cf
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88e6a2aa02decf1e4ed9c4a9838077be0c3b97b2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="selectivebindingimport-application-deployment-sample"></a><span data-ttu-id="0f714-102">SelectiveBindingImport (應用程式部署範例)</span><span class="sxs-lookup"><span data-stu-id="0f714-102">SelectiveBindingImport (Application Deployment Sample)</span></span>
<span data-ttu-id="0f714-103">此主題說明如何使用 SelectiveBindingImport 範例。</span><span class="sxs-lookup"><span data-stu-id="0f714-103">This topic explains how to use the SelectiveBindingImport sample.</span></span> <span data-ttu-id="0f714-104">將應用程式匯入不同的目的地環境時，您可以使用此範例指令碼，將不同的繫結套用至同一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f714-104">You can use this sample script to apply different bindings to an application when you import the application into different destination environments.</span></span> <span data-ttu-id="0f714-105">希望從儲存在網路共用上的繫結檔案匯入繫結時，您可以使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="0f714-105">You can use this approach when you want to import the bindings from binding files that are stored on a network share.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f714-106">如果應用程式匯入期間，不需要從網路共用自動匯入繫結檔案，可以將已指定不同目的地環境的不同繫結檔案加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f714-106">If you do not need to automatically import binding files from a network share during application import, you can add to the application different binding files that have different destination environments specified.</span></span> <span data-ttu-id="0f714-107">匯入應用程式時，您可以指定環境以及環境會自動套用的繫結。</span><span class="sxs-lookup"><span data-stu-id="0f714-107">When you import the application, you can specify the environment, and the bindings for that environment will be applied automatically.</span></span> <span data-ttu-id="0f714-108">如需詳細資訊，請參閱[繫結檔案和應用程式部署](../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="0f714-108">For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
 <span data-ttu-id="0f714-109">BizTalk 應用程式通常會從開發、測試、執行，再移至實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="0f714-109">BizTalk applications are typically moved from development to testing to staging and then to production environments.</span></span> <span data-ttu-id="0f714-110">通常不同環境所使用的繫結各異。</span><span class="sxs-lookup"><span data-stu-id="0f714-110">The bindings used in different environments are typically different.</span></span> <span data-ttu-id="0f714-111">使用此範例，您可以為不同的環境套用繫結，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0f714-111">Using this sample, you can apply bindings for different environments as follows:</span></span>  
  
1.  <span data-ttu-id="0f714-112">將您想使用的所有繫結檔案置於網路共用。</span><span class="sxs-lookup"><span data-stu-id="0f714-112">Placing all the binding files that you want to use on a network share.</span></span>  
  
2.  <span data-ttu-id="0f714-113">將後置處理指令碼加入至應用程式，該應用程式會於應用程式匯入時，從這個位置為特定的目的地環境匯入正確的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="0f714-113">Adding a post-processing script to the application that will import from this location the correct binding file for the particular destination environment during application import.</span></span> <span data-ttu-id="0f714-114">指令碼會讀取您在本機電腦上設定的 %ENVIRONMENT% 環境變數來偵測環境。</span><span class="sxs-lookup"><span data-stu-id="0f714-114">The script detects the environment by reading an environment variable named %ENVIRONMENT% that you set on the local computer,</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="0f714-115">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="0f714-115">What This Sample Does</span></span>  
 <span data-ttu-id="0f714-116">此範例說明如何使用 BizTalk 應用程式 .msi 檔內的後置處理指令碼，從網路共用選擇性匯入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="0f714-116">This sample illustrates how to selectively import binding files from a network share by using a post-processing script contained in a BizTalk application .msi file.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="0f714-117">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="0f714-117">Where to Find This Sample</span></span>  
 <span data-ttu-id="0f714-118">下列範例資料夾和下的檔案，您可以找到*\<範例路徑\>*\Application Deployment\SelectiveBindingImport:</span><span class="sxs-lookup"><span data-stu-id="0f714-118">You can find the following sample folders and files under *\<Samples Path\>*\Application Deployment\SelectiveBindingImport:</span></span>  
  
-   <span data-ttu-id="0f714-119">Develop (資料夾)</span><span class="sxs-lookup"><span data-stu-id="0f714-119">Develop (Folder)</span></span>  
  
    -   <span data-ttu-id="0f714-120">Dev.xml</span><span class="sxs-lookup"><span data-stu-id="0f714-120">Dev.xml</span></span>  
  
-   <span data-ttu-id="0f714-121">Production (資料夾)</span><span class="sxs-lookup"><span data-stu-id="0f714-121">Production (Folder)</span></span>  
  
    -   <span data-ttu-id="0f714-122">Production.xml</span><span class="sxs-lookup"><span data-stu-id="0f714-122">Production.xml</span></span>  
  
-   <span data-ttu-id="0f714-123">Staging (資料夾)</span><span class="sxs-lookup"><span data-stu-id="0f714-123">Staging (Folder)</span></span>  
  
    -   <span data-ttu-id="0f714-124">Staging.xml</span><span class="sxs-lookup"><span data-stu-id="0f714-124">Staging.xml</span></span>  
  
-   <span data-ttu-id="0f714-125">Test (資料夾)</span><span class="sxs-lookup"><span data-stu-id="0f714-125">Test (Folder)</span></span>  
  
    -   <span data-ttu-id="0f714-126">Test.xml</span><span class="sxs-lookup"><span data-stu-id="0f714-126">Test.xml</span></span>  
  
-   <span data-ttu-id="0f714-127">SelectiveBindings.bat</span><span class="sxs-lookup"><span data-stu-id="0f714-127">SelectiveBindings.bat</span></span>  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="0f714-128">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="0f714-128">How to Use This Sample</span></span>  
 <span data-ttu-id="0f714-129">請使用下列程序來執行此範例。</span><span class="sxs-lookup"><span data-stu-id="0f714-129">Use the following procedures to run this sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="0f714-130">執行範例</span><span class="sxs-lookup"><span data-stu-id="0f714-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="0f714-131">執行**從 Build.Bat *\<範例路徑\>*\Application Deployment\CreateApp**目錄。</span><span class="sxs-lookup"><span data-stu-id="0f714-131">Run **Build.Bat from the *\<Samples Path\>*\Application Deployment\CreateApp** directory.</span></span> <span data-ttu-id="0f714-132">這會建立下列檔案中的*\<範例路徑\>*\Application Deployment\CreateApp\Dlls 資料夾： Schemas.dll、 Maps.dll 和 Orchestrations.dll。</span><span class="sxs-lookup"><span data-stu-id="0f714-132">This creates the following files in the *\<Samples Path\>*\Application Deployment\CreateApp\Dlls folder: Schemas.dll, Maps.dll, and Orchestrations.dll.</span></span>  
  
2.  <span data-ttu-id="0f714-133">**建立應用程式。**</span><span class="sxs-lookup"><span data-stu-id="0f714-133">**Create the application.**</span></span> <span data-ttu-id="0f714-134">在 BizTalk Server 管理主控台中，建立應用程式中所述[如何建立應用程式](../core/how-to-create-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0f714-134">In the BizTalk Server Administration console, create an application, as described in [How to Create an Application](../core/how-to-create-an-application.md).</span></span>  
  
3.  <span data-ttu-id="0f714-135">**加入第一個步驟中建立的.dll 檔案的應用程式。**</span><span class="sxs-lookup"><span data-stu-id="0f714-135">**Add to the application the .dll files created in the first step.**</span></span> <span data-ttu-id="0f714-136">如需指示，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0f714-136">For instructions, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
4.  <span data-ttu-id="0f714-137">**建立環境變數，如下所示：**</span><span class="sxs-lookup"><span data-stu-id="0f714-137">**Create the ENVIRONMENT variable, as follows:**</span></span>  
  
    1.  <span data-ttu-id="0f714-138">在 [開始] 功能表中，以滑鼠右鍵按一下**我的電腦**按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0f714-138">On the Start menu, right-click **My Computer** and click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="0f714-139">在**進階**索引標籤上，按一下 **環境變數**。</span><span class="sxs-lookup"><span data-stu-id="0f714-139">On the **Advanced** tab, click **Environment Variables**.</span></span>  
  
    3.  <span data-ttu-id="0f714-140">在**使用者變數**區段中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="0f714-140">In the **User variables** section, click **New**.</span></span>  
  
    4.  <span data-ttu-id="0f714-141">在**變數名稱**，型別**環境**。</span><span class="sxs-lookup"><span data-stu-id="0f714-141">In **Variable name**, type **ENVIRONMENT**.</span></span>  
  
    5.  <span data-ttu-id="0f714-142">在**變數值**，值型別上的下列環境：**開發**，**生產**，**臨時**，或**測試**。</span><span class="sxs-lookup"><span data-stu-id="0f714-142">In **Variable value**, type on of the following values for the environment: **Develop**, **Production**, **Staging**, or **Test**.</span></span> <span data-ttu-id="0f714-143">這些值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0f714-143">These values are case sensitive.</span></span>  
  
5.  <span data-ttu-id="0f714-144">按一下**確定**三次。</span><span class="sxs-lookup"><span data-stu-id="0f714-144">Click **OK** three times.</span></span>  
  
6.  <span data-ttu-id="0f714-145">**將繫結檔案複製到檔案系統上的位置。**</span><span class="sxs-lookup"><span data-stu-id="0f714-145">**Copy the binding files to a location on your file system.**</span></span> <span data-ttu-id="0f714-146">從 [Develop]、[Test]、[Staging] 和 [Production] 資料夾，將繫結 .xml 檔複製至檔案系統上的位置。</span><span class="sxs-lookup"><span data-stu-id="0f714-146">Copy the binding .xml files from the Develop, Test, Staging, and Production folders to a location on your file system.</span></span>  
  
7.  <span data-ttu-id="0f714-147">**編輯後置處理指令碼。**</span><span class="sxs-lookup"><span data-stu-id="0f714-147">**Edit the post-processing script.**</span></span> <span data-ttu-id="0f714-148">編輯 SelectiveBindings.bat，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0f714-148">Edit SelectiveBindings.bat as follows:</span></span>  
  
    1.  <span data-ttu-id="0f714-149">**指定的繫結檔案的位置。**</span><span class="sxs-lookup"><span data-stu-id="0f714-149">**Specify the binding file location.**</span></span> <span data-ttu-id="0f714-150">刪除包含 BINDINGS_LOC 那一行的 REM，並提供您複製繫結檔案所在位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="0f714-150">In the line containing BINDINGS_LOC, delete REM, and provide the path to the location where you copied the binding files.</span></span>  
  
         <span data-ttu-id="0f714-151">範例：</span><span class="sxs-lookup"><span data-stu-id="0f714-151">Example:</span></span>  
  
         <span data-ttu-id="0f714-152">BINDINGS_LOC=C:\MyBindings</span><span class="sxs-lookup"><span data-stu-id="0f714-152">BINDINGS_LOC=C:\MyBindings</span></span>  
  
    2.  <span data-ttu-id="0f714-153">**指定應用程式名稱。**</span><span class="sxs-lookup"><span data-stu-id="0f714-153">**Specify the application name.**</span></span> <span data-ttu-id="0f714-154">刪除包含 APPLICATION_NAME 那一行的 REM，並提供您想匯入繫結之應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f714-154">In the line containing APPLICATION_NAME, delete REM, and provide the name of the application into which you want to import the bindings.</span></span>  
  
         <span data-ttu-id="0f714-155">範例：</span><span class="sxs-lookup"><span data-stu-id="0f714-155">Example:</span></span>  
  
         <span data-ttu-id="0f714-156">APPLICATION_Name=SelectiveBindingImport</span><span class="sxs-lookup"><span data-stu-id="0f714-156">APPLICATION_Name=SelectiveBindingImport</span></span>  
  
8.  <span data-ttu-id="0f714-157">**將指令碼加入至應用程式做為後置處理指令碼。**</span><span class="sxs-lookup"><span data-stu-id="0f714-157">**Add the script to the application as a post-processing script.**</span></span> <span data-ttu-id="0f714-158">如需指示，請參閱[如何新增前置或後置處理指令碼至應用程式](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0f714-158">For instructions, see [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).</span></span>  
  
9. <span data-ttu-id="0f714-159">**匯出應用程式。**</span><span class="sxs-lookup"><span data-stu-id="0f714-159">**Export the application.**</span></span> <span data-ttu-id="0f714-160">如需指示，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0f714-160">For instructions, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span>  
  
10. <span data-ttu-id="0f714-161">**刪除應用程式。**</span><span class="sxs-lookup"><span data-stu-id="0f714-161">**Delete the application.**</span></span> <span data-ttu-id="0f714-162">如需指示，請參閱[如何從 BizTalk 群組刪除 BizTalk 應用程式](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)。</span><span class="sxs-lookup"><span data-stu-id="0f714-162">For instructions, see [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).</span></span>  
  
11. <span data-ttu-id="0f714-163">**匯入應用程式。**</span><span class="sxs-lookup"><span data-stu-id="0f714-163">**Import the application.**</span></span> <span data-ttu-id="0f714-164">如需指示，請參閱[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0f714-164">For instructions, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span> <span data-ttu-id="0f714-165">您不需要指定目的地環境。</span><span class="sxs-lookup"><span data-stu-id="0f714-165">You do not need to specify a destination environment.</span></span>  
  
12. <span data-ttu-id="0f714-166">**請確認已套用正確的繫結檔案。**</span><span class="sxs-lookup"><span data-stu-id="0f714-166">**Verify that the right binding file was applied.**</span></span> <span data-ttu-id="0f714-167">只要檢查接收位置的描述欄位即可確認，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0f714-167">You can do this by checking the description field of the receive locations, as follows:</span></span>  
  
    1.  <span data-ttu-id="0f714-168">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0f714-168">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
    2.  <span data-ttu-id="0f714-169">在主控台樹狀結構中，展開 BizTalk 群組、BizTalk 應用程式和 [Receive Locations] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0f714-169">In the console tree, expand the BizTalk group, the BizTalk application, and the Receive Locations folder.</span></span>  
  
    3.  <span data-ttu-id="0f714-170">在右窗格中，檢視接收位置的描述。</span><span class="sxs-lookup"><span data-stu-id="0f714-170">In the right pane, view the description of the receive locations.</span></span>  
  
13. <span data-ttu-id="0f714-171">**安裝應用程式。**</span><span class="sxs-lookup"><span data-stu-id="0f714-171">**Install the application.**</span></span> <span data-ttu-id="0f714-172">如需指示，請參閱[如何安裝 BizTalk 應用程式](../core/how-to-install-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0f714-172">For instructions, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f714-173">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f714-173">See Also</span></span>  
 <span data-ttu-id="0f714-174">[應用程式部署 （BizTalk Server 範例資料夾）](../core/application-deployment-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="0f714-174">[Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="0f714-175">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="0f714-175">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)