---
title: "步驟 3-建立組建和發行定義 |Microsoft 文件"
description: "在 VSTS 中，會建立組建定義，以便建置您的 git 或 TFS 儲存機制中的專案，然後建立要部署 BizTalk Server 應用程式的發行定義"
ms.custom: 
ms.date: 11/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de86d35fd615d8c0f1eee1127804645067c4bf6e
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="step-3-create-the-build-and-release-definition"></a><span data-ttu-id="604bc-103">步驟 3： 建立組建和發行定義</span><span class="sxs-lookup"><span data-stu-id="604bc-103">Step 3: Create the build and release definition</span></span>

<span data-ttu-id="604bc-104">組建和發行定義是 Visual Studio Team Services 的工作，並可能由 VSTS 系統管理員。組建定義建置您的專案，在您的 git 儲存機制和發行定義將其部署到 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="604bc-104">The build and release definitions are Visual Studio Team Services tasks, and should probably be done by a VSTS admin. The build definition builds your project within your git repository, and the release definitions deploys it to your BizTalk Server environment.</span></span> 

## <a name="add-the-build-tasks"></a><span data-ttu-id="604bc-105">加入建置工作</span><span class="sxs-lookup"><span data-stu-id="604bc-105">Add the Build tasks</span></span>
1. <span data-ttu-id="604bc-106">在專案中，選取**組建與版本**。</span><span class="sxs-lookup"><span data-stu-id="604bc-106">In your project, select **Build and release**.</span></span> <span data-ttu-id="604bc-107">[組建] 索引標籤隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="604bc-107">The Builds tab opens.</span></span> <span data-ttu-id="604bc-108">建立**新增**定義：</span><span class="sxs-lookup"><span data-stu-id="604bc-108">Create a **New** definition:</span></span>

    ![新的組建定義](../core/media/vsts-new-definition.png)

2. <span data-ttu-id="604bc-110">選取**空**範本，然後選取**套用**:</span><span class="sxs-lookup"><span data-stu-id="604bc-110">Select the **Empty** template, and select **Apply**:</span></span>  

    ![選取空白的範本](../core/media/vsts-emtpy-template.png)
 
3. <span data-ttu-id="604bc-112">設定**代理程式佇列**為預設值：</span><span class="sxs-lookup"><span data-stu-id="604bc-112">Set the **Agent Queue** to Default:</span></span> 

    ![選擇預設佇列](../core/media/vsts-select-agent-queue.png)

4. <span data-ttu-id="604bc-114">在**階段 1**、 加入工作中，選取**Visual Studio 建置**，然後選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="604bc-114">In **Phase 1**, add a task, select **Visual Studio Build**, and select **Add**:</span></span>

    ![加入 VS 建置工作](../core/media/vsts-add-visual-studio-task.png)

5. <span data-ttu-id="604bc-116">按一下 Visual Studio 建置的工作只需要加入，並設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="604bc-116">Click the Visual Studio Build task you just added, and set the following properties:</span></span>  

    | <span data-ttu-id="604bc-117">屬性</span><span class="sxs-lookup"><span data-stu-id="604bc-117">Property</span></span> | <span data-ttu-id="604bc-118">設定為</span><span class="sxs-lookup"><span data-stu-id="604bc-118">Set to</span></span> |
    | --- | --- | 
    | <span data-ttu-id="604bc-119">顯示名稱</span><span class="sxs-lookup"><span data-stu-id="604bc-119">Display name</span></span> | <span data-ttu-id="604bc-120">*YourProjectName*建置方案 * *\*.sln</span><span class="sxs-lookup"><span data-stu-id="604bc-120">*YourProjectName* Build solution **\*.sln</span></span> | 
    | <span data-ttu-id="604bc-121">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="604bc-121">Visual Studio version</span></span> | <span data-ttu-id="604bc-122">Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="604bc-122">Visual Studio 2015</span></span> | 
    | <span data-ttu-id="604bc-123">MSBuild 架構</span><span class="sxs-lookup"><span data-stu-id="604bc-123">MSBuild Architecture</span></span> | <span data-ttu-id="604bc-124">MSBuild x86</span><span class="sxs-lookup"><span data-stu-id="604bc-124">MSBuild x86</span></span> | 

6. <span data-ttu-id="604bc-125">在**階段 1**、 加入工作中，選取**發行組建成品**，然後選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="604bc-125">In **Phase 1**, add a task, select **Publish Build Artifacts**, and select **Add**:</span></span> 

    ![加入 VS 建置工作](../core/media/vsts-add-publish-build-task.png)

7. <span data-ttu-id="604bc-127">選取**發行成品**工作，並輸入慣用**顯示名稱**。</span><span class="sxs-lookup"><span data-stu-id="604bc-127">Select the **Publish Artifact** task, and enter your preferred **Display name**.</span></span> <span data-ttu-id="604bc-128">如**發行路徑**，選取**...**按鈕，然後選擇應用程式專案的資料夾 (例如 appProjectHelloWorld)。</span><span class="sxs-lookup"><span data-stu-id="604bc-128">For **Path to publish**, select the **...**  button, and choose the application project folder (e.g. appProjectHelloWorld).</span></span> <span data-ttu-id="604bc-129">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="604bc-129">Select **OK**.</span></span>

8. <span data-ttu-id="604bc-130">**成品名稱**可以是您想要的任何項目。</span><span class="sxs-lookup"><span data-stu-id="604bc-130">The **Artifact Name** can be anything you want.</span></span> <span data-ttu-id="604bc-131">選取**儲存**。</span><span class="sxs-lookup"><span data-stu-id="604bc-131">Select **Save**.</span></span> 

9. <span data-ttu-id="604bc-132">移至**觸發程序**，並設定**觸發狀態**至**啟用**:</span><span class="sxs-lookup"><span data-stu-id="604bc-132">Go to **Triggers**, and set the **Trigger status** to **Enabled**:</span></span>  

    ![加入 VS 建置工作](../core/media/vsts-continuous-integration.png)

10. <span data-ttu-id="604bc-134">**儲存並佇列**來測試您的組建定義。</span><span class="sxs-lookup"><span data-stu-id="604bc-134">**Save & Queue** to test your build definition.</span></span> <span data-ttu-id="604bc-135">當您排入佇列時，系統會提示您為代理程式佇列和您的分支。</span><span class="sxs-lookup"><span data-stu-id="604bc-135">When you queue, you are prompted for the agent queue and your branch.</span></span> <span data-ttu-id="604bc-136">選取**預設**代理程式佇列，然後選擇您的分支。</span><span class="sxs-lookup"><span data-stu-id="604bc-136">Select the **Default** agent queue, and choose your branch.</span></span> <span data-ttu-id="604bc-137">選取**佇列**。</span><span class="sxs-lookup"><span data-stu-id="604bc-137">Select **Queue**.</span></span>  

11. <span data-ttu-id="604bc-138">新組建會啟動，且您可以選取它，以便檢查成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="604bc-138">A new build is started, and you can select it to check for a success or failure.</span></span> 

## <a name="add-the-release-tasks"></a><span data-ttu-id="604bc-139">將發行工作</span><span class="sxs-lookup"><span data-stu-id="604bc-139">Add the release tasks</span></span>

<span data-ttu-id="604bc-140">建置成功時，發行定義部署到 BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="604bc-140">When the build succeeds, the release definition deploys your application to your BizTalk Server.</span></span> 

1. <span data-ttu-id="604bc-141">選取**版本**索引標籤上，選取**新定義**。</span><span class="sxs-lookup"><span data-stu-id="604bc-141">Select the **Releases** tab, select **New definition**.</span></span> 

2. <span data-ttu-id="604bc-142">選取**空**範本，然後選取**套用**:</span><span class="sxs-lookup"><span data-stu-id="604bc-142">Select the **Empty** template, and select **Apply**:</span></span>

    ![加入空白的範本](../core/media/vsts-empty-release-template.png)

3. <span data-ttu-id="604bc-144">變更**環境名稱**至**Dev**，或任何您要呼叫它。</span><span class="sxs-lookup"><span data-stu-id="604bc-144">Change the **Environment name** to **Dev**, or whatever you want to call it.</span></span> 

4. <span data-ttu-id="604bc-145">選取**新增成品**，選取您的專案，您的組建定義，然後選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="604bc-145">Select **Add artifact**, select your project, your build definition, and select **Add**:</span></span> 

5. <span data-ttu-id="604bc-146">移至**工作**索引標籤上，將新工作：</span><span class="sxs-lookup"><span data-stu-id="604bc-146">Go to the **Tasks** tab, add a new task:</span></span> 

    ![將發行工作](../core/media/vsts-new-release-tasks.png)

6. <span data-ttu-id="604bc-148">從清單中，篩選的結果，請選取**BizTalk Server 應用程式部署**工作，並選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="604bc-148">From the list, filter the results, select the **BizTalk Server Application Deployment** task, and select **Add**:</span></span>  

    ![新增 BizTalk 部署工作](../core/media/vsts-biztalk-application-deployment-task.png)

    <span data-ttu-id="604bc-150">如果**BizTalk Server 應用程式部署**ins't 列出，然後將它安裝在[部署 BizTalk 應用程式](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application)。</span><span class="sxs-lookup"><span data-stu-id="604bc-150">If **BizTalk Server Application Deployment** ins't listed, then install it at [Deploy BizTalk Application](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application).</span></span>

7. <span data-ttu-id="604bc-151">選取**部署**工作，並輸入值：</span><span class="sxs-lookup"><span data-stu-id="604bc-151">Select the **Deploy** task, and enter the values:</span></span> 

    <span data-ttu-id="604bc-152">**作業名稱**： 選取**建立新的 BizTalk 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="604bc-152">**Operation Name**: Select **Create new BizTalk Application**.</span></span> <span data-ttu-id="604bc-153">此選項會將新的應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="604bc-153">This option deploys a new application.</span></span> <span data-ttu-id="604bc-154">如果應用程式已經存在，它會解除安裝目前的應用程式 （完全停止），並會安裝新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="604bc-154">If the application already exists, it uninstalls the current applications (full stop), and installs the new application.</span></span> <span data-ttu-id="604bc-155">如果已啟用持續整合，它會自動重新部署應用程式更新儲存機制中時。</span><span class="sxs-lookup"><span data-stu-id="604bc-155">If continuous integration is enabled, it automatically redeploys the application when it is updated in the repository.</span></span> <span data-ttu-id="604bc-156">**更新現有的 BizTalk 應用程式**將變更，例如結構描述、 附加至正在執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="604bc-156">**Update an existing BizTalk Application** appends changes, such as schemas, to an already running application.</span></span> <span data-ttu-id="604bc-157">它不需要完整的重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="604bc-157">It does not require a full redeploy of the application.</span></span>

    <span data-ttu-id="604bc-158">**應用程式名稱**： 您輸入的文字將會在 BizTalk 管理中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="604bc-158">**Application Name**: The text you enter will be the application name in BizTalk Administration.</span></span> <span data-ttu-id="604bc-159">請勿**不**輸入 BizTalk Application 1。</span><span class="sxs-lookup"><span data-stu-id="604bc-159">Do **not** enter BizTalk Application 1.</span></span>

    <span data-ttu-id="604bc-160">**部署套件**： 選取您的應用程式專案，zip 檔案，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="604bc-160">**Deployment package**: Select the zip file to your application project, and select **OK**.</span></span> 

8. <span data-ttu-id="604bc-161">選取**代理程式階段**工作。</span><span class="sxs-lookup"><span data-stu-id="604bc-161">Select the **Agent phase** task.</span></span> <span data-ttu-id="604bc-162">選取**預設**代理程式佇列。</span><span class="sxs-lookup"><span data-stu-id="604bc-162">Select the **Default** Agent queue.</span></span> <span data-ttu-id="604bc-163">**儲存**您的變更。</span><span class="sxs-lookup"><span data-stu-id="604bc-163">**Save** your changes.</span></span>

9. <span data-ttu-id="604bc-164">選取**釋放** > **建立發行**:</span><span class="sxs-lookup"><span data-stu-id="604bc-164">Select **Release** > **Create release**:</span></span>  

    ![版本中，建立發行](../core/media/vsts-create-release.png)

10. <span data-ttu-id="604bc-166">選取**佇列**。</span><span class="sxs-lookup"><span data-stu-id="604bc-166">Select **Queue**.</span></span> <span data-ttu-id="604bc-167">檢查狀態，依序按一下 [版本] 連結。</span><span class="sxs-lookup"><span data-stu-id="604bc-167">Check the status by clicking the release link.</span></span> <span data-ttu-id="604bc-168">如果失敗，錯誤訊息中顯示。</span><span class="sxs-lookup"><span data-stu-id="604bc-168">If it fails, the error displays.</span></span> <span data-ttu-id="604bc-169">如果成功，應用程式會加入至 BizTalk 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="604bc-169">If it succeeds, the application is added to the BizTalk Administration console.</span></span> 

## <a name="what-you-did"></a><span data-ttu-id="604bc-170">您的作法</span><span class="sxs-lookup"><span data-stu-id="604bc-170">What you did</span></span>

<span data-ttu-id="604bc-171">在 VSTS 中，您可以建立組建 Git 或 Team Foundation 版本控制 （無論您選擇） 內的應用程式的組建定義。</span><span class="sxs-lookup"><span data-stu-id="604bc-171">In VSTS, you created a build definition that builds your application within Git or Team Foundation Version Control (whatever you chose).</span></span> <span data-ttu-id="604bc-172">原始檔控制中變更時，所做的變更會自動偵測，您可以將其推送。</span><span class="sxs-lookup"><span data-stu-id="604bc-172">When changes are made within the source control, the changes are automatically detected, and you can push them.</span></span> <span data-ttu-id="604bc-173">在建置完成之後，您會建立應用程式部署至 BizTalk Server 中，您可以在 BizTalk Server 管理 中看到的發行定義。</span><span class="sxs-lookup"><span data-stu-id="604bc-173">After the build completes, you created a release definition that deploys the application to BizTalk Server, which you can see in BizTalk Server Administration.</span></span> 

## <a name="next-step"></a><span data-ttu-id="604bc-174">下一步</span><span class="sxs-lookup"><span data-stu-id="604bc-174">Next step</span></span>
<span data-ttu-id="604bc-175">在此步驟中，您已完成。</span><span class="sxs-lookup"><span data-stu-id="604bc-175">At this step, you're done.</span></span> <span data-ttu-id="604bc-176">如果您想要的話，您可以在 BizTalk XML 繫結檔案中，建立環境的語彙基元，並建立符合環境的語彙基元的 VSTS 中的變數。</span><span class="sxs-lookup"><span data-stu-id="604bc-176">If you prefer, you can create environmental tokens within your BizTalk XML binding file, and create variables within VSTS that match the environmental tokens.</span></span> <span data-ttu-id="604bc-177">請參閱[設定環境的語彙基元和變數](configure-environmental-tokens-and-variables-for-automatic-deployment.md)詳細資料。</span><span class="sxs-lookup"><span data-stu-id="604bc-177">See [Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) for the details.</span></span> 