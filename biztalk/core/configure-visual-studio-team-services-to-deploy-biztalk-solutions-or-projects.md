---
redirect_url: /biztalk/core/feature-pack-add-build-release-definitions/
redirect_document_id: true
ROBOTS: NOINDEX
title: 設定要部署 BizTalk Server 方案或專案的 Visual Studio Team Services |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2555712a-dfe4-420e-9a61-1d1a6d98c322
caps.latest.revision: 6
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 7178f85bce4087e5bc740810050817676a6c8996
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992471"
---
# <a name="configure-visual-studio-team-services-to-deploy-biztalk-server-solutions-or-projects"></a><span data-ttu-id="f8e24-102">設定要部署 BizTalk Server 方案或專案的 Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="f8e24-102">Configure Visual Studio Team Services to deploy BizTalk Server solutions or projects</span></span>
<span data-ttu-id="f8e24-103">設定 VSTS 自動部署[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="f8e24-103">Set up VSTS to automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] projects.</span></span> 

<span data-ttu-id="f8e24-104">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可以自動建置您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]使用 Visual Studio Team Services (VSTS) 的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f8e24-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can automatically build your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] solutions using Visual Studio Team Services (VSTS).</span></span> 

<span data-ttu-id="f8e24-105">本主題說明如何安裝和設定 Visual Studio Team Service (VSTS) BizTalk 使用自動部署。</span><span class="sxs-lookup"><span data-stu-id="f8e24-105">This topic shows you how to set up and configure Visual Studio Team Service (VSTS) to use automatic deployment for BizTalk.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="f8e24-106">VSTS 代理程式只能安裝在上一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中。</span><span class="sxs-lookup"><span data-stu-id="f8e24-106">The VSTS agent can only be installed on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="f8e24-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="f8e24-107">Prerequisites</span></span>

* <span data-ttu-id="f8e24-108">安裝[Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100)上您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8e24-108">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="f8e24-109">一些經驗及建立與使用定義在 VSTS 中的知識。</span><span class="sxs-lookup"><span data-stu-id="f8e24-109">Some experience and knowledge with creating and working with definitions in VSTS.</span></span> <span data-ttu-id="f8e24-110">如果您是新手 VSTS，這些可能是不錯的資源：</span><span class="sxs-lookup"><span data-stu-id="f8e24-110">If you're brand new to VSTS, these may be good resources:</span></span> 

  [<span data-ttu-id="f8e24-111">Visual Studio Team Services 概觀</span><span class="sxs-lookup"><span data-stu-id="f8e24-111">Visual Studio Team Services overview</span></span>](https://www.visualstudio.com/docs/overview)  
  [<span data-ttu-id="f8e24-112">新手的 CI/CD</span><span class="sxs-lookup"><span data-stu-id="f8e24-112">CI/CD for newbies</span></span>](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)
  

## <a name="create-a-vsts-account-and-create-a-definition"></a><span data-ttu-id="f8e24-113">建立 VSTS 帳戶，並建立定義</span><span class="sxs-lookup"><span data-stu-id="f8e24-113">Create a VSTS account and create a definition</span></span>

1. <span data-ttu-id="f8e24-114">在 web 瀏覽器中，移至您[Visual Studio online 設定檔](https://app.vsaex.visualstudio.com/go/profile)、 登入，然後選取**建立新帳戶**:</span><span class="sxs-lookup"><span data-stu-id="f8e24-114">In a web browser, go to your [Visual Studio online profile](https://app.vsaex.visualstudio.com/go/profile), sign in, and select a **Create new account**:</span></span>

    ![建立新帳戶](../core/media/create-a-new-account.png)

2. <span data-ttu-id="f8e24-116">輸入帳戶的名稱，選取您偏好的原始檔的程式碼存放庫，然後選取**繼續**:</span><span class="sxs-lookup"><span data-stu-id="f8e24-116">Enter a name for the account, select your preferred source code repository, and select **Continue**:</span></span>

    ![建立新的專案](../core/media/create-a-new-project.png)

3. <span data-ttu-id="f8e24-118">建立新的帳戶時，與類似於站台`https://YourAccountName.visualstudio.com/MyFirstProject`隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f8e24-118">Your new account is created, and a site similar to `https://YourAccountName.visualstudio.com/MyFirstProject` opens.</span></span>
    
4. <span data-ttu-id="f8e24-119">安裝[部署 BizTalk 應用程式服務](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application)至您剛才建立的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f8e24-119">Install the [Deploy BizTalk Application service](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application) to the account you just created.</span></span>

    ![建立新的版本](../core/media/build-new-release.png)

5. <span data-ttu-id="f8e24-121">您可能會收到一些提示。</span><span class="sxs-lookup"><span data-stu-id="f8e24-121">You may get some prompts.</span></span> <span data-ttu-id="f8e24-122">確認以繼續。</span><span class="sxs-lookup"><span data-stu-id="f8e24-122">Confirm to continue.</span></span> <span data-ttu-id="f8e24-123">請確定您已登入您的專案，在 VSTS 中。</span><span class="sxs-lookup"><span data-stu-id="f8e24-123">Be sure you're signed in to your project in VSTS.</span></span>

6. <span data-ttu-id="f8e24-124">選取 **組建和發行**，然後建立**新增**組建定義：</span><span class="sxs-lookup"><span data-stu-id="f8e24-124">Select **Build and release**, and create a **New** build definition:</span></span>

    ![選取的組建和發行](../core/media/select-build-and-release.png)

    > [!TIP]
    > <span data-ttu-id="f8e24-126">確定您是在`https://YourAccountName.visualstudio.com/MyFirstProject`。</span><span class="sxs-lookup"><span data-stu-id="f8e24-126">Be sure you're at `https://YourAccountName.visualstudio.com/MyFirstProject`.</span></span> <span data-ttu-id="f8e24-127">否則**新增**或是**新的定義**按鈕可能不會有。</span><span class="sxs-lookup"><span data-stu-id="f8e24-127">Otherwise, the **New** or **New definition** buttons may not be there.</span></span> 
    
7. <span data-ttu-id="f8e24-128">選取 [ **Visual Studio**範本，然後選取**下一步]**:</span><span class="sxs-lookup"><span data-stu-id="f8e24-128">Select the **Visual Studio** template, and select **Next**:</span></span>

    ![選取 visual studio，然後按一下 下一步](../core/media/select-visual-studio-and-click-next.png)

8. <span data-ttu-id="f8e24-130">檢閱您的設定，然後選取**建立**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-130">Review your settings, and select **Create**.</span></span>

9. <span data-ttu-id="f8e24-131">刪除您不需要的步驟。</span><span class="sxs-lookup"><span data-stu-id="f8e24-131">Delete the steps you don't need.</span></span> <span data-ttu-id="f8e24-132">本教學課程中，您可以刪除下列項目：</span><span class="sxs-lookup"><span data-stu-id="f8e24-132">For this tutorial, you can delete the following:</span></span> 
10. <span data-ttu-id="f8e24-133">NuGet 還原</span><span class="sxs-lookup"><span data-stu-id="f8e24-133">NuGet Restore</span></span>
11. <span data-ttu-id="f8e24-134">測試組件</span><span class="sxs-lookup"><span data-stu-id="f8e24-134">Test assemblies</span></span>
12. <span data-ttu-id="f8e24-135">發行符號路徑</span><span class="sxs-lookup"><span data-stu-id="f8e24-135">Publish symbols path</span></span> 

      ![刪除不需要的步驟](../core/media/delete-steps-not-needed.png)

13. <span data-ttu-id="f8e24-137">**選擇性**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-137">**Optional**.</span></span> <span data-ttu-id="f8e24-138">如果您想要啟用持續整合 (CI) 中，選取**觸發程序**功能表中，核取**連續整合 (CI)**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-138">If you want to enable Continous Integration (CI), select **Triggers** in the menu, and check **Continous integration (CI)**.</span></span>

<span data-ttu-id="f8e24-139">接下來，將代理程式安裝在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f8e24-139">Next, install the agent on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

## <a name="install-the-agent"></a><span data-ttu-id="f8e24-140">安裝代理程式</span><span class="sxs-lookup"><span data-stu-id="f8e24-140">Install the Agent</span></span>

<span data-ttu-id="f8e24-141">運作的解決方案，讓本機電腦上的私人 Windows 代理程式。</span><span class="sxs-lookup"><span data-stu-id="f8e24-141">For the solution to work, enable a private Windows Agent on your local machine.</span></span> <span data-ttu-id="f8e24-142">請記住，**必須只有其中安裝代理程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-142">Remember, **the agent must be installed on only one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group**.</span></span> 

1. <span data-ttu-id="f8e24-143">在定義中，選取**一般**（頂端） 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8e24-143">In your definition, select the **General** tab (at the top).</span></span>
2. <span data-ttu-id="f8e24-144">針對**預設代理程式佇列**屬性中，選取**預設**從清單中的代理程式。</span><span class="sxs-lookup"><span data-stu-id="f8e24-144">For the **Default agent queue** property, select the **Default** agent from the list.</span></span> 
3. <span data-ttu-id="f8e24-145">選取 **管理**旁**預設代理程式佇列**屬性。</span><span class="sxs-lookup"><span data-stu-id="f8e24-145">Select **Manage** next to the **Default agent queue** property.</span></span> <span data-ttu-id="f8e24-146">新的瀏覽器索引標籤隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f8e24-146">A new browser tab opens.</span></span>

    ![建立新的管理代理程式](../core/media/create-new-management-agent.png)

4. <span data-ttu-id="f8e24-148">在左窗格中，會選取預設佇列。</span><span class="sxs-lookup"><span data-stu-id="f8e24-148">In the left pane, the Default queue is selected.</span></span> <span data-ttu-id="f8e24-149">如果代理程式已列出，且在線上，您已大功告成。</span><span class="sxs-lookup"><span data-stu-id="f8e24-149">If an agent is already listed, and online, then you're done.</span></span> <span data-ttu-id="f8e24-150">您有代理程式，安裝並執行。</span><span class="sxs-lookup"><span data-stu-id="f8e24-150">You have an agent installed, and running.</span></span> 

    <span data-ttu-id="f8e24-151">如果未列出的代理程式，然後選取**下載代理程式**，並繼續進行安裝程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f8e24-151">If an agent is not listed, then select **Download agent**, and continue with the installation on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f8e24-152">**移至[代理程式部署到 Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows)的完整步驟**安裝代理程式，並啟動代理程式。</span><span class="sxs-lookup"><span data-stu-id="f8e24-152">**Go to [Deploy an agent on Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows) for the complete steps** to install the agent, and start an agent.</span></span> 

    > [!IMPORTANT]
    > <span data-ttu-id="f8e24-153">請遵循所有的步驟[代理程式部署到 Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows)。</span><span class="sxs-lookup"><span data-stu-id="f8e24-153">Follow all the steps at [Deploy an agent on Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows).</span></span> <span data-ttu-id="f8e24-154">請勿略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="f8e24-154">Do not skip this step.</span></span> 

5. <span data-ttu-id="f8e24-155">預設代理程式**線上**返回**一般**索引標籤上，在定義中，並確認**預設**選取**預設代理程式佇列**.</span><span class="sxs-lookup"><span data-stu-id="f8e24-155">With the default agent **Online**, go back to the **General** tab in your definition, and confirm **Default** is selected for the **Default agent queue**.</span></span>
6. <span data-ttu-id="f8e24-156">**儲存**並**新組建排入佇列**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-156">**Save** and **Queue new build**.</span></span>

<span data-ttu-id="f8e24-157">接下來，建立 BizTalk Server 應用程式部署定義。</span><span class="sxs-lookup"><span data-stu-id="f8e24-157">Next, create the BizTalk Server Application Deployment definition.</span></span>

## <a name="create-the-biztalk-deployment-definition"></a><span data-ttu-id="f8e24-158">建立 BizTalk 部署定義</span><span class="sxs-lookup"><span data-stu-id="f8e24-158">Create the BizTalk deployment definition</span></span>

1. <span data-ttu-id="f8e24-159">選取 **組建**索引標籤上，選取**所有定義**，然後選取**新增**:</span><span class="sxs-lookup"><span data-stu-id="f8e24-159">Select the **Builds** tab, select **All Definitions**, and select **New**:</span></span>

    ![建立新的發行定義](../core/media/create-new-release-defintion.png)

2. <span data-ttu-id="f8e24-161">選取 [**空**範本，然後選取**下一步]**:</span><span class="sxs-lookup"><span data-stu-id="f8e24-161">Select the **Empty** template, and select **Next**:</span></span>

    ![從空白範本建立新的定義](../core/media/create-new-defintion-from-an-empty-template.png)

3. <span data-ttu-id="f8e24-163">選取您**儲存機制**來源並**分支**定義。</span><span class="sxs-lookup"><span data-stu-id="f8e24-163">Select your **Repository** source and **Branch** for the definition.</span></span>
4. <span data-ttu-id="f8e24-164">**選擇性**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-164">**Optional**.</span></span> <span data-ttu-id="f8e24-165">選取 **持續整合**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-165">Select **Continous Integration**.</span></span>
5. <span data-ttu-id="f8e24-166">選取 **預設**代理程式從該佇列清單，然後選取**建立**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-166">Select the **Default** agent from the queue list, and select **Create**.</span></span>
6. <span data-ttu-id="f8e24-167">**新增組建步驟**，選取**BizTalk Server 應用程式部署**工作，並選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-167">**Add build step**, select the **BizTalk Server Application Deployment** task, and select **Add**.</span></span> <span data-ttu-id="f8e24-168">**關閉**工作目錄中。</span><span class="sxs-lookup"><span data-stu-id="f8e24-168">**Close** the task catalog.</span></span>

    ![加入新的部署定義](../core/media/add-new-deploy-definition.png)

7. <span data-ttu-id="f8e24-170">選取 **作業名稱**您想要使用：</span><span class="sxs-lookup"><span data-stu-id="f8e24-170">Select the **Operation Name** you want to use:</span></span>
    * <span data-ttu-id="f8e24-171">**建立新的 BizTalk 應用程式**部署新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8e24-171">**Create new BizTalk Application** deploys a new application.</span></span> <span data-ttu-id="f8e24-172">如果應用程式已經 exsist，它會解除安裝目前的應用程式 （句點），並會安裝新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8e24-172">If the application already exsist, it uninstalls the current applications (full stop), and installs the new application.</span></span> <span data-ttu-id="f8e24-173">如果已啟用持續整合，它會自動重新部署應用程式更新存放庫中時。</span><span class="sxs-lookup"><span data-stu-id="f8e24-173">If continous integration is enabled, it automatically redeploys the application when it is updated in the repository.</span></span>
    * <span data-ttu-id="f8e24-174">**更新現有的 BizTalk 應用程式**附加的變更，例如**結構描述**已在執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8e24-174">**Update an exsisting BizTalk Application** appends changes, such as **Schemas** to an already running application.</span></span> <span data-ttu-id="f8e24-175">它不需要完整的重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8e24-175">It does not require a full redeploy of the application.</span></span>
8. <span data-ttu-id="f8e24-176">請輸入**應用程式名稱**中您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="f8e24-176">Enter the **Application name** in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>
9. <span data-ttu-id="f8e24-177">在 **部署套件路徑**，選取您的存放庫中的 zip 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f8e24-177">In **Deployment package path**, select the path to the zip file in your repository.</span></span>
10. <span data-ttu-id="f8e24-178">選取 **觸發程序**從功能表中，啟用**連續整合**，然後選取正確**分支**組建。</span><span class="sxs-lookup"><span data-stu-id="f8e24-178">Select **Triggers** from the menu, enable **Continous Integration**, and select the correct **Branch** for the build.</span></span>
11. <span data-ttu-id="f8e24-179">選取 **儲存**:</span><span class="sxs-lookup"><span data-stu-id="f8e24-179">Select **Save**:</span></span>

    ![儲存新的組建定義](../core/media/save-the-new-build-definition.png)

12. <span data-ttu-id="f8e24-181">指定新**定義**，而且設定正確的路徑。</span><span class="sxs-lookup"><span data-stu-id="f8e24-181">Name the new **Definition**, and set the correct path.</span></span> 
13. <span data-ttu-id="f8e24-182">定義儲存之後，選取**新的組建排入佇列**。</span><span class="sxs-lookup"><span data-stu-id="f8e24-182">Once the definition is saved, select **Queue the new build**.</span></span> <span data-ttu-id="f8e24-183">然後，選取**佇列代理程式**，並將註解新增至認可。</span><span class="sxs-lookup"><span data-stu-id="f8e24-183">Then, select the **Queue agent**, and add a comment to the commit.</span></span>
