---
title: "步驟 3-建立組建和發行定義 |Microsoft 文件"
description: "在 VSTS 中，會建立組建定義，以便建置您的 git 或 TFS 儲存機制中的專案，然後建立要部署 BizTalk Server 應用程式的發行定義"
ms.custom: 
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ce84071fbc105fd9faddd794792273aae2e76b9
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="step-3-create-the-build-and-release-definition"></a><span data-ttu-id="b3b28-103">步驟 3： 建立組建和發行定義</span><span class="sxs-lookup"><span data-stu-id="b3b28-103">Step 3: Create the build and release definition</span></span>

<span data-ttu-id="b3b28-104">組建和發行定義是 Visual Studio Team Services 的工作，並可能由 VSTS 系統管理員。組建定義建置您的專案，在您的 git 儲存機制和發行定義將其部署到 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="b3b28-104">The build and release definitions are Visual Studio Team Services tasks, and should probably be done by a VSTS admin. The build definition builds your project within your git repository, and the release definitions deploys it to your BizTalk Server environment.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="b3b28-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="b3b28-105">Before you begin</span></span>
<span data-ttu-id="b3b28-106">完成[步驟 2-建立 VSTS 語彙基元，並安裝代理程式](feature-pack-create-vsts-token.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b28-106">Complete [Step 2 - Create VSTS token and install agent](feature-pack-create-vsts-token.md).</span></span>

## <a name="add-the-build-tasks"></a><span data-ttu-id="b3b28-107">加入建置工作</span><span class="sxs-lookup"><span data-stu-id="b3b28-107">Add the Build tasks</span></span>
1. <span data-ttu-id="b3b28-108">在專案中，選取**組建與版本**。</span><span class="sxs-lookup"><span data-stu-id="b3b28-108">In your project, select **Build and release**.</span></span> <span data-ttu-id="b3b28-109">[組建] 索引標籤隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="b3b28-109">The Builds tab opens.</span></span> <span data-ttu-id="b3b28-110">建立**新增**定義：</span><span class="sxs-lookup"><span data-stu-id="b3b28-110">Create a **New** definition:</span></span>

    ![新的組建定義](../core/media/vsts-new-definition.png)

2. <span data-ttu-id="b3b28-112">選取**空**範本，然後選取**套用**:</span><span class="sxs-lookup"><span data-stu-id="b3b28-112">Select the **Empty** template, and select **Apply**:</span></span>  

    ![選取空白的範本](../core/media/vsts-emtpy-template.png)
 
3. <span data-ttu-id="b3b28-114">設定**代理程式佇列**為預設值：</span><span class="sxs-lookup"><span data-stu-id="b3b28-114">Set the **Agent Queue** to Default:</span></span> 

    ![選擇預設佇列](../core/media/vsts-select-agent-queue.png)

4. <span data-ttu-id="b3b28-116">在**階段 1**、 加入工作中，選取**Visual Studio 建置**，然後選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="b3b28-116">In **Phase 1**, add a task, select **Visual Studio Build**, and select **Add**:</span></span>

    ![加入 VS 建置工作](../core/media/vsts-add-visual-studio-task.png)

5. <span data-ttu-id="b3b28-118">按一下 Visual Studio 建置的工作只需要加入，並設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b3b28-118">Click the Visual Studio Build task you just added, and set the following properties:</span></span>  

    | <span data-ttu-id="b3b28-119">屬性</span><span class="sxs-lookup"><span data-stu-id="b3b28-119">Property</span></span> | <span data-ttu-id="b3b28-120">設定為</span><span class="sxs-lookup"><span data-stu-id="b3b28-120">Set to</span></span> |
    | --- | --- | 
    | <span data-ttu-id="b3b28-121">顯示名稱</span><span class="sxs-lookup"><span data-stu-id="b3b28-121">Display name</span></span> | <span data-ttu-id="b3b28-122">*YourProjectName*建置方案 * *\*.sln</span><span class="sxs-lookup"><span data-stu-id="b3b28-122">*YourProjectName* Build solution **\*.sln</span></span> | 
    | <span data-ttu-id="b3b28-123">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="b3b28-123">Visual Studio version</span></span> | <span data-ttu-id="b3b28-124">Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="b3b28-124">Visual Studio 2015</span></span> | 
    | <span data-ttu-id="b3b28-125">MSBuild 架構</span><span class="sxs-lookup"><span data-stu-id="b3b28-125">MSBuild Architecture</span></span> | <span data-ttu-id="b3b28-126">MSBuild x86</span><span class="sxs-lookup"><span data-stu-id="b3b28-126">MSBuild x86</span></span> | 

6. <span data-ttu-id="b3b28-127">在**階段 1**、 加入工作中，選取**發行組建成品**，然後選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="b3b28-127">In **Phase 1**, add a task, select **Publish Build Artifacts**, and select **Add**:</span></span> 

    ![加入 VS 建置工作](../core/media/vsts-add-publish-build-task.png)

7. <span data-ttu-id="b3b28-129">選取**發行成品**工作，並輸入慣用**顯示名稱**。</span><span class="sxs-lookup"><span data-stu-id="b3b28-129">Select the **Publish Artifact** task, and enter your preferred **Display name**.</span></span> <span data-ttu-id="b3b28-130">如**發行路徑**，選取**...**按鈕，然後選擇應用程式專案的資料夾 (例如 appProjectHelloWorld)。</span><span class="sxs-lookup"><span data-stu-id="b3b28-130">For **Path to publish**, select the **...**  button, and choose the application project folder (e.g. appProjectHelloWorld).</span></span> <span data-ttu-id="b3b28-131">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="b3b28-131">Select **OK**.</span></span>

8. <span data-ttu-id="b3b28-132">**成品名稱**可以是您想要的任何項目。</span><span class="sxs-lookup"><span data-stu-id="b3b28-132">The **Artifact Name** can be anything you want.</span></span> <span data-ttu-id="b3b28-133">選取**儲存**。</span><span class="sxs-lookup"><span data-stu-id="b3b28-133">Select **Save**.</span></span> 

9. <span data-ttu-id="b3b28-134">移至**觸發程序**，並設定**觸發狀態**至**啟用**:</span><span class="sxs-lookup"><span data-stu-id="b3b28-134">Go to **Triggers**, and set the **Trigger status** to **Enabled**:</span></span>  

    ![加入 VS 建置工作](../core/media/vsts-continuous-integration.png)

10. <span data-ttu-id="b3b28-136">**儲存並佇列**來測試您的組建定義。</span><span class="sxs-lookup"><span data-stu-id="b3b28-136">**Save & Queue** to test your build definition.</span></span> <span data-ttu-id="b3b28-137">當您排入佇列時，系統會提示您為代理程式佇列和您的分支。</span><span class="sxs-lookup"><span data-stu-id="b3b28-137">When you queue, you are prompted for the agent queue and your branch.</span></span> <span data-ttu-id="b3b28-138">選取**預設**代理程式佇列，然後選擇您的分支。</span><span class="sxs-lookup"><span data-stu-id="b3b28-138">Select the **Default** agent queue, and choose your branch.</span></span> <span data-ttu-id="b3b28-139">選取**佇列**。</span><span class="sxs-lookup"><span data-stu-id="b3b28-139">Select **Queue**.</span></span>  

11. <span data-ttu-id="b3b28-140">新組建會啟動，且您可以選取它，以便檢查成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="b3b28-140">A new build is started, and you can select it to check for a success or failure.</span></span> 

## <a name="add-the-release-tasks"></a><span data-ttu-id="b3b28-141">將發行工作</span><span class="sxs-lookup"><span data-stu-id="b3b28-141">Add the release tasks</span></span>

<span data-ttu-id="b3b28-142">建置成功時，發行定義部署到 BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3b28-142">When the build succeeds, the release definition deploys your application to your BizTalk Server.</span></span> 

1. <span data-ttu-id="b3b28-143">選取**版本**索引標籤上，選取**新定義**。</span><span class="sxs-lookup"><span data-stu-id="b3b28-143">Select the **Releases** tab, select **New definition**.</span></span> 

2. <span data-ttu-id="b3b28-144">選取**空**範本，然後選取**套用**:</span><span class="sxs-lookup"><span data-stu-id="b3b28-144">Select the **Empty** template, and select **Apply**:</span></span>

    ![加入空白的範本](../core/media/vsts-empty-release-template.png)

3. <span data-ttu-id="b3b28-146">變更**環境名稱**至**Dev**，或任何您要呼叫它。</span><span class="sxs-lookup"><span data-stu-id="b3b28-146">Change the **Environment name** to **Dev**, or whatever you want to call it.</span></span> 

4. <span data-ttu-id="b3b28-147">選取**新增成品**，選取您的專案，您的組建定義，然後選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="b3b28-147">Select **Add artifact**, select your project, your build definition, and select **Add**:</span></span> 

5. <span data-ttu-id="b3b28-148">移至**工作**索引標籤上，將新工作：</span><span class="sxs-lookup"><span data-stu-id="b3b28-148">Go to the **Tasks** tab, add a new task:</span></span> 

    ![將發行工作](../core/media/vsts-new-release-tasks.png)

6. <span data-ttu-id="b3b28-150">從清單中，篩選的結果，請選取**BizTalk Server 應用程式部署**工作，並選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="b3b28-150">From the list, filter the results, select the **BizTalk Server Application Deployment** task, and select **Add**:</span></span>  

    ![新增 BizTalk 部署工作](../core/media/vsts-biztalk-application-deployment-task.png)

    <span data-ttu-id="b3b28-152">如果**BizTalk Server 應用程式部署**ins't 列出，然後將它安裝在[部署 BizTalk 應用程式](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application)。</span><span class="sxs-lookup"><span data-stu-id="b3b28-152">If **BizTalk Server Application Deployment** ins't listed, then install it at [Deploy BizTalk Application](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application).</span></span>

7. <span data-ttu-id="b3b28-153">選取**部署**工作，並輸入值：</span><span class="sxs-lookup"><span data-stu-id="b3b28-153">Select the **Deploy** task, and enter the values:</span></span> 

    <span data-ttu-id="b3b28-154">**作業名稱**： 您的選項: ***建立新的 BizTalk 應用程式**： 將新的應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="b3b28-154">**Operation Name**: Your options: * **Create new BizTalk Application**: Deploys a new application.</span></span> <span data-ttu-id="b3b28-155">如果應用程式已經存在，它會解除安裝目前的應用程式 （完全停止），並會安裝新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3b28-155">If the application already exists, it uninstalls the current applications (full stop), and installs the new application.</span></span> <span data-ttu-id="b3b28-156">如果已啟用持續整合，它會自動重新部署應用程式更新儲存機制中時。</span><span class="sxs-lookup"><span data-stu-id="b3b28-156">If continuous integration is enabled, it automatically redeploys the application when it is updated in the repository.</span></span> 
        <span data-ttu-id="b3b28-157">* **更新現有的 BizTalk 應用程式**： 將變更，例如結構描述、 附加至正在執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3b28-157">* **Update an existing BizTalk Application**: Appends changes, such as schemas, to an already running application.</span></span> <span data-ttu-id="b3b28-158">它不需要完整的重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3b28-158">It does not require a full redeploy of the application.</span></span>
        <span data-ttu-id="b3b28-159">* **安裝 BizTalk Server 應用程式**:[安裝的應用程式](../core/how-to-install-a-biztalk-application.md)，輸入 BizTalk 管理的電腦名稱和部署封裝路徑。</span><span class="sxs-lookup"><span data-stu-id="b3b28-159">* **Install BizTalk Server Application**: [Install the applications](../core/how-to-install-a-biztalk-application.md), and you enter the BizTalk management computer name, and the deployment package path.</span></span>

        ![Deploy operations](../core/media/vsts-deploy-operations.png)

    <span data-ttu-id="b3b28-160">**應用程式名稱**： 您輸入的文字將會在 BizTalk 管理中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="b3b28-160">**Application Name**: The text you enter will be the application name in BizTalk Administration.</span></span> <span data-ttu-id="b3b28-161">請勿**不**輸入 BizTalk Application 1。</span><span class="sxs-lookup"><span data-stu-id="b3b28-161">Do **not** enter BizTalk Application 1.</span></span>

    <span data-ttu-id="b3b28-162">**部署套件**： 選取您的應用程式專案，zip 檔案，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="b3b28-162">**Deployment package**: Select the zip file to your application project, and select **OK**.</span></span> 

8. <span data-ttu-id="b3b28-163">選取**代理程式階段**工作。</span><span class="sxs-lookup"><span data-stu-id="b3b28-163">Select the **Agent phase** task.</span></span> <span data-ttu-id="b3b28-164">選取**預設**代理程式佇列。</span><span class="sxs-lookup"><span data-stu-id="b3b28-164">Select the **Default** Agent queue.</span></span> <span data-ttu-id="b3b28-165">**儲存**您的變更。</span><span class="sxs-lookup"><span data-stu-id="b3b28-165">**Save** your changes.</span></span>

9. <span data-ttu-id="b3b28-166">選取**釋放** > **建立發行**:</span><span class="sxs-lookup"><span data-stu-id="b3b28-166">Select **Release** > **Create release**:</span></span>  

    ![版本中，建立發行](../core/media/vsts-create-release.png)

10. <span data-ttu-id="b3b28-168">選取**佇列**。</span><span class="sxs-lookup"><span data-stu-id="b3b28-168">Select **Queue**.</span></span> <span data-ttu-id="b3b28-169">檢查狀態，依序按一下 [版本] 連結。</span><span class="sxs-lookup"><span data-stu-id="b3b28-169">Check the status by clicking the release link.</span></span> <span data-ttu-id="b3b28-170">如果失敗，錯誤訊息中顯示。</span><span class="sxs-lookup"><span data-stu-id="b3b28-170">If it fails, the error displays.</span></span> <span data-ttu-id="b3b28-171">如果成功，應用程式會加入至 BizTalk 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b3b28-171">If it succeeds, the application is added to the BizTalk Administration console.</span></span> 

## <a name="what-you-did"></a><span data-ttu-id="b3b28-172">您的作法</span><span class="sxs-lookup"><span data-stu-id="b3b28-172">What you did</span></span>

<span data-ttu-id="b3b28-173">在 VSTS 中，您可以建立組建 Git 或 Team Foundation 版本控制 （無論您選擇） 內的應用程式的組建定義。</span><span class="sxs-lookup"><span data-stu-id="b3b28-173">In VSTS, you created a build definition that builds your application within Git or Team Foundation Version Control (whatever you chose).</span></span> <span data-ttu-id="b3b28-174">原始檔控制中變更時，所做的變更會自動偵測，您可以將其推送。</span><span class="sxs-lookup"><span data-stu-id="b3b28-174">When changes are made within the source control, the changes are automatically detected, and you can push them.</span></span> <span data-ttu-id="b3b28-175">在建置完成之後，您會建立應用程式部署至 BizTalk Server 中，您可以在 BizTalk Server 管理 中看到的發行定義。</span><span class="sxs-lookup"><span data-stu-id="b3b28-175">After the build completes, you created a release definition that deploys the application to BizTalk Server, which you can see in BizTalk Server Administration.</span></span> 

## <a name="next-step"></a><span data-ttu-id="b3b28-176">下一步</span><span class="sxs-lookup"><span data-stu-id="b3b28-176">Next step</span></span>
<span data-ttu-id="b3b28-177">在此步驟中，您已完成。</span><span class="sxs-lookup"><span data-stu-id="b3b28-177">At this step, you're done.</span></span> <span data-ttu-id="b3b28-178">如果您想要的話，您可以在 BizTalk XML 繫結檔案中，建立環境的語彙基元，並建立符合環境的語彙基元的 VSTS 中的變數。</span><span class="sxs-lookup"><span data-stu-id="b3b28-178">If you prefer, you can create environmental tokens within your BizTalk XML binding file, and create variables within VSTS that match the environmental tokens.</span></span> <span data-ttu-id="b3b28-179">請參閱[設定環境的語彙基元和變數](configure-environmental-tokens-and-variables-for-automatic-deployment.md)詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b3b28-179">See [Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) for the details.</span></span> 