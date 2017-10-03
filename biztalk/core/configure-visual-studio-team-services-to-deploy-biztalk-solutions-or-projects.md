---
title: "設定要部署 BizTalk Server 方案或專案的 Visual Studio Team Services |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2555712a-dfe4-420e-9a61-1d1a6d98c322
caps.latest.revision: "6"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 6368300c714811d5b3c42e07ebb804d26362bf85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-visual-studio-team-services-to-deploy-biztalk-server-solutions-or-projects"></a><span data-ttu-id="3c66c-102">設定 Visual Studio Team Services 部署 BizTalk Server 方案或專案</span><span class="sxs-lookup"><span data-stu-id="3c66c-102">Configure Visual Studio Team Services to deploy BizTalk Server solutions or projects</span></span>
<span data-ttu-id="3c66c-103">若要自動部署設定 VSTS[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="3c66c-103">Set up VSTS to automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] projects.</span></span> 

<span data-ttu-id="3c66c-104">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可以自動建立您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]使用 Visual Studio Team Services (VSTS) 的解決方案。</span><span class="sxs-lookup"><span data-stu-id="3c66c-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can automatically build your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] solutions using Visual Studio Team Services (VSTS).</span></span> 

<span data-ttu-id="3c66c-105">本主題說明如何安裝和設定 Visual Studio Team 服務 (VSTS) 若要針對 BizTalk 使用自動部署。</span><span class="sxs-lookup"><span data-stu-id="3c66c-105">This topic shows you how to set up and configure Visual Studio Team Service (VSTS) to use automatic deployment for BizTalk.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="3c66c-106">VSTS 代理程式只能安裝一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中。</span><span class="sxs-lookup"><span data-stu-id="3c66c-106">The VSTS agent can only be installed on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="3c66c-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="3c66c-107">Prerequisites</span></span>

* <span data-ttu-id="3c66c-108">安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c66c-108">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="3c66c-109">某些體驗和建立及使用定義於 VSTS 中的知識。</span><span class="sxs-lookup"><span data-stu-id="3c66c-109">Some experience and knowledge with creating and working with definitions in VSTS.</span></span> <span data-ttu-id="3c66c-110">如果您是新手 VSTS，這些可能是很好的資源：</span><span class="sxs-lookup"><span data-stu-id="3c66c-110">If you're brand new to VSTS, these may be good resources:</span></span> 

  [<span data-ttu-id="3c66c-111">Visual Studio Team Services 概觀</span><span class="sxs-lookup"><span data-stu-id="3c66c-111">Visual Studio Team Services overview</span></span>](https://www.visualstudio.com/docs/overview)  
  [<span data-ttu-id="3c66c-112">CI/CD 新手適用的</span><span class="sxs-lookup"><span data-stu-id="3c66c-112">CI/CD for newbies</span></span>](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)
  

## <a name="create-a-vsts-account-and-create-a-definition"></a><span data-ttu-id="3c66c-113">建立 VSTS 帳戶，然後建立定義</span><span class="sxs-lookup"><span data-stu-id="3c66c-113">Create a VSTS account and create a definition</span></span>

1. <span data-ttu-id="3c66c-114">在網頁瀏覽器，移至您[Visual Studio online 設定檔](https://app.vsaex.visualstudio.com/go/profile)、 登入，並選取**建立新帳戶**:</span><span class="sxs-lookup"><span data-stu-id="3c66c-114">In a web browser, go to your [Visual Studio online profile](https://app.vsaex.visualstudio.com/go/profile), sign in, and select a **Create new account**:</span></span>

    ![建立新帳戶](../core/media/create-a-new-account.png)

2. <span data-ttu-id="3c66c-116">輸入帳戶的名稱，選取您偏好的來源的程式碼儲存機制，並選取**繼續**:</span><span class="sxs-lookup"><span data-stu-id="3c66c-116">Enter a name for the account, select your preferred source code repository, and select **Continue**:</span></span>

    ![建立新的專案](../core/media/create-a-new-project.png)

3. <span data-ttu-id="3c66c-118">建立新的帳戶，而且類似於站台`https://YourAccountName.visualstudio.com/MyFirstProject`隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="3c66c-118">Your new account is created, and a site similar to `https://YourAccountName.visualstudio.com/MyFirstProject` opens.</span></span>
    
4. <span data-ttu-id="3c66c-119">安裝[部署 BizTalk 應用程式服務](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application)您剛才建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="3c66c-119">Install the [Deploy BizTalk Application service](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application) to the account you just created.</span></span>

    ![建立新的版本](../core/media/build-new-release.png)

5. <span data-ttu-id="3c66c-121">您可能會看到一些提示。</span><span class="sxs-lookup"><span data-stu-id="3c66c-121">You may get some prompts.</span></span> <span data-ttu-id="3c66c-122">確認以繼續。</span><span class="sxs-lookup"><span data-stu-id="3c66c-122">Confirm to continue.</span></span> <span data-ttu-id="3c66c-123">請確定您已登入您在 VSTS 中的專案。</span><span class="sxs-lookup"><span data-stu-id="3c66c-123">Be sure you're signed in to your project in VSTS.</span></span>

6. <span data-ttu-id="3c66c-124">選取**組建和發行**，並建立**新增**組建定義：</span><span class="sxs-lookup"><span data-stu-id="3c66c-124">Select **Build and release**, and create a **New** build definition:</span></span>

    ![選取組建和發行](../core/media/select-build-and-release.png)

    > [!TIP]
    > <span data-ttu-id="3c66c-126">請確定您在`https://YourAccountName.visualstudio.com/MyFirstProject`。</span><span class="sxs-lookup"><span data-stu-id="3c66c-126">Be sure you're at `https://YourAccountName.visualstudio.com/MyFirstProject`.</span></span> <span data-ttu-id="3c66c-127">否則，**新增**或**新定義**按鈕可能不存在。</span><span class="sxs-lookup"><span data-stu-id="3c66c-127">Otherwise, the **New** or **New definition** buttons may not be there.</span></span> 
    
7. <span data-ttu-id="3c66c-128">選取**Visual Studio**範本，然後選取**下一步**:</span><span class="sxs-lookup"><span data-stu-id="3c66c-128">Select the **Visual Studio** template, and select **Next**:</span></span>

    ![選取 visual studio，然後按一下 下一步](../core/media/select-visual-studio-and-click-next.png)

8. <span data-ttu-id="3c66c-130">檢閱您的設定，並選取**建立**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-130">Review your settings, and select **Create**.</span></span>

9. <span data-ttu-id="3c66c-131">刪除您不需要的步驟。</span><span class="sxs-lookup"><span data-stu-id="3c66c-131">Delete the steps you don't need.</span></span> <span data-ttu-id="3c66c-132">此教學課程中，您可以刪除下列項目：</span><span class="sxs-lookup"><span data-stu-id="3c66c-132">For this tutorial, you can delete the following:</span></span> 
* <span data-ttu-id="3c66c-133">NuGet 還原</span><span class="sxs-lookup"><span data-stu-id="3c66c-133">NuGet Restore</span></span>
* <span data-ttu-id="3c66c-134">測試組件</span><span class="sxs-lookup"><span data-stu-id="3c66c-134">Test assemblies</span></span>
* <span data-ttu-id="3c66c-135">發行符號路徑</span><span class="sxs-lookup"><span data-stu-id="3c66c-135">Publish symbols path</span></span> 

    ![刪除不需要的步驟](../core/media/delete-steps-not-needed.png)

10. <span data-ttu-id="3c66c-137">**選擇性**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-137">**Optional**.</span></span> <span data-ttu-id="3c66c-138">如果您要啟用連續整合 (CI)，請選取**觸發程序**在功能表上，並檢查**連續整合 (CI)**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-138">If you want to enable Continous Integration (CI), select **Triggers** in the menu, and check **Continous integration (CI)**.</span></span>

<span data-ttu-id="3c66c-139">接下來，代理程式安裝在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3c66c-139">Next, install the agent on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

## <a name="install-the-agent"></a><span data-ttu-id="3c66c-140">安裝代理程式</span><span class="sxs-lookup"><span data-stu-id="3c66c-140">Install the Agent</span></span>

<span data-ttu-id="3c66c-141">針對工作解決方案，可讓私用的 Windows 代理程式在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="3c66c-141">For the solution to work, enable a private Windows Agent on your local machine.</span></span> <span data-ttu-id="3c66c-142">請記住，**必須只有其中安裝代理程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-142">Remember, **the agent must be installed on only one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group**.</span></span> 

1. <span data-ttu-id="3c66c-143">在定義中，選取**一般**（頂端） 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3c66c-143">In your definition, select the **General** tab (at the top).</span></span>
2. <span data-ttu-id="3c66c-144">如**預設代理程式佇列**屬性選取**預設**從清單中的代理程式。</span><span class="sxs-lookup"><span data-stu-id="3c66c-144">For the **Default agent queue** property, select the **Default** agent from the list.</span></span> 
3. <span data-ttu-id="3c66c-145">選取**管理**旁**預設代理程式佇列**屬性。</span><span class="sxs-lookup"><span data-stu-id="3c66c-145">Select **Manage** next to the **Default agent queue** property.</span></span> <span data-ttu-id="3c66c-146">新的瀏覽器索引標籤隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="3c66c-146">A new browser tab opens.</span></span>

    ![建立新的管理代理程式](../core/media/create-new-management-agent.png)

4. <span data-ttu-id="3c66c-148">在左窗格中，會選取預設佇列。</span><span class="sxs-lookup"><span data-stu-id="3c66c-148">In the left pane, the Default queue is selected.</span></span> <span data-ttu-id="3c66c-149">如果代理程式已列出，且在線上，然後瀏覽完畢。</span><span class="sxs-lookup"><span data-stu-id="3c66c-149">If an agent is already listed, and online, then you're done.</span></span> <span data-ttu-id="3c66c-150">您有代理程式，安裝並執行。</span><span class="sxs-lookup"><span data-stu-id="3c66c-150">You have an agent installed, and running.</span></span> 

    <span data-ttu-id="3c66c-151">如果未列出的代理程式，然後選取**下載代理程式**，並繼續進行安裝程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3c66c-151">If an agent is not listed, then select **Download agent**, and continue with the installation on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3c66c-152">**移至[代理程式部署到 Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows)的完整步驟**安裝代理程式，並啟動代理程式。</span><span class="sxs-lookup"><span data-stu-id="3c66c-152">**Go to [Deploy an agent on Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows) for the complete steps** to install the agent, and start an agent.</span></span> 

    > [!IMPORTANT]
    > <span data-ttu-id="3c66c-153">遵循所有步驟，在[代理程式部署到 Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows)。</span><span class="sxs-lookup"><span data-stu-id="3c66c-153">Follow all the steps at [Deploy an agent on Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows).</span></span> <span data-ttu-id="3c66c-154">請勿略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="3c66c-154">Do not skip this step.</span></span> 

5. <span data-ttu-id="3c66c-155">預設代理程式**線上**，請回到**一般**索引標籤上，在定義中，並確認**預設**選取**預設代理程式佇列**.</span><span class="sxs-lookup"><span data-stu-id="3c66c-155">With the default agent **Online**, go back to the **General** tab in your definition, and confirm **Default** is selected for the **Default agent queue**.</span></span>
6. <span data-ttu-id="3c66c-156">**儲存**和**新組建排入佇列**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-156">**Save** and **Queue new build**.</span></span>

<span data-ttu-id="3c66c-157">接下來，建立 BizTalk Server 應用程式部署定義。</span><span class="sxs-lookup"><span data-stu-id="3c66c-157">Next, create the BizTalk Server Application Deployment definition.</span></span>

## <a name="create-the-biztalk-deployment-definition"></a><span data-ttu-id="3c66c-158">建立 BizTalk 部署定義</span><span class="sxs-lookup"><span data-stu-id="3c66c-158">Create the BizTalk deployment definition</span></span>

1. <span data-ttu-id="3c66c-159">選取**建置**索引標籤上，選取**所有定義**，然後選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="3c66c-159">Select the **Builds** tab, select **All Definitions**, and select **New**:</span></span>

    ![建立新的發行定義](../core/media/create-new-release-defintion.png)

2. <span data-ttu-id="3c66c-161">選取**空**範本，然後選取**下一步**:</span><span class="sxs-lookup"><span data-stu-id="3c66c-161">Select the **Empty** template, and select **Next**:</span></span>

    ![從空白範本建立新的定義](../core/media/create-new-defintion-from-an-empty-template.png)

3. <span data-ttu-id="3c66c-163">選取您**儲存機制**來源和**分支**定義。</span><span class="sxs-lookup"><span data-stu-id="3c66c-163">Select your **Repository** source and **Branch** for the definition.</span></span>
4. <span data-ttu-id="3c66c-164">**選擇性**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-164">**Optional**.</span></span> <span data-ttu-id="3c66c-165">選取**連續整合**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-165">Select **Continous Integration**.</span></span>
5. <span data-ttu-id="3c66c-166">選取**預設**代理程式從佇列清單，然後選取**建立**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-166">Select the **Default** agent from the queue list, and select **Create**.</span></span>
6. <span data-ttu-id="3c66c-167">**加入建置步驟**，選取**BizTalk Server 應用程式部署**工作，並選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-167">**Add build step**, select the **BizTalk Server Application Deployment** task, and select **Add**.</span></span> <span data-ttu-id="3c66c-168">**關閉**工作目錄。</span><span class="sxs-lookup"><span data-stu-id="3c66c-168">**Close** the task catalog.</span></span>

    ![加入新的部署定義](../core/media/add-new-deploy-definition.png)

7. <span data-ttu-id="3c66c-170">選取**作業名稱**您想要使用：</span><span class="sxs-lookup"><span data-stu-id="3c66c-170">Select the **Operation Name** you want to use:</span></span>
    * <span data-ttu-id="3c66c-171">**建立新的 BizTalk 應用程式**部署新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c66c-171">**Create new BizTalk Application** deploys a new application.</span></span> <span data-ttu-id="3c66c-172">如果應用程式已經 exsist，它會解除安裝目前的應用程式 （完全停止），並會安裝新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c66c-172">If the application already exsist, it uninstalls the current applications (full stop), and installs the new application.</span></span> <span data-ttu-id="3c66c-173">如果已啟用連續整合，它會自動重新部署應用程式更新儲存機制中時。</span><span class="sxs-lookup"><span data-stu-id="3c66c-173">If continous integration is enabled, it automatically redeploys the application when it is updated in the repository.</span></span>
    * <span data-ttu-id="3c66c-174">**更新現有的 BizTalk 應用程式**附加變更，例如**結構描述**正在執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c66c-174">**Update an exsisting BizTalk Application** appends changes, such as **Schemas** to an already running application.</span></span> <span data-ttu-id="3c66c-175">它不需要完整的重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c66c-175">It does not require a full redeploy of the application.</span></span>
8. <span data-ttu-id="3c66c-176">輸入**應用程式名稱**中您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="3c66c-176">Enter the **Application name** in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>
9. <span data-ttu-id="3c66c-177">在**部署封裝路徑**，選取您的儲存機制中的 zip 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="3c66c-177">In **Deployment package path**, select the path to the zip file in your repository.</span></span>
10. <span data-ttu-id="3c66c-178">選取**觸發程序**從功能表中，啟用**連續整合**，然後選取正確的**分支**組建。</span><span class="sxs-lookup"><span data-stu-id="3c66c-178">Select **Triggers** from the menu, enable **Continous Integration**, and select the correct **Branch** for the build.</span></span>
11. <span data-ttu-id="3c66c-179">選取**儲存**:</span><span class="sxs-lookup"><span data-stu-id="3c66c-179">Select **Save**:</span></span>

    ![儲存新的組建定義](../core/media/save-the-new-build-definition.png)

12. <span data-ttu-id="3c66c-181">指定新**定義**，而且設定正確的路徑。</span><span class="sxs-lookup"><span data-stu-id="3c66c-181">Name the new **Definition**, and set the correct path.</span></span> 
13. <span data-ttu-id="3c66c-182">定義儲存之後，選取**新組建排入佇列**。</span><span class="sxs-lookup"><span data-stu-id="3c66c-182">Once the definition is saved, select **Queue the new build**.</span></span> <span data-ttu-id="3c66c-183">然後，選取**佇列代理程式**，並將註解加入至認可。</span><span class="sxs-lookup"><span data-stu-id="3c66c-183">Then, select the **Queue agent**, and add a comment to the commit.</span></span>

## <a name="next-step"></a><span data-ttu-id="3c66c-184">下一步</span><span class="sxs-lookup"><span data-stu-id="3c66c-184">Next step</span></span>
[<span data-ttu-id="3c66c-185">設定自動部署的 JSON 範本</span><span class="sxs-lookup"><span data-stu-id="3c66c-185">Configure the JSON template for automatic deployment</span></span>](../core/configure-the-json-template-for-automatic-deployment.md)