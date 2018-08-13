---
title: 步驟 2-建立 VSTS 權杖及安裝代理程式 |Microsoft Docs
description: Visual studio，建立 VSTS 安全性存取權杖，複製您的 VSTS 專案，並安裝組建代理程式自動部署您的 BizTalk Server 專案
ms.custom: ''
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d26a218b6de83b1ab2e5a2dd46be215dcbb0f49
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979343"
---
# <a name="step-2-create-the-token--install-the-agent"></a><span data-ttu-id="cd163-103">步驟 2： 建立權杖，並安裝代理程式</span><span class="sxs-lookup"><span data-stu-id="cd163-103">Step 2: Create the token & install the agent</span></span>

<span data-ttu-id="cd163-104">Visual Studio Team Services 中建立個人存取權杖 (PAT)。</span><span class="sxs-lookup"><span data-stu-id="cd163-104">A personal access token (PAT) is created in Visual Studio Team Services.</span></span> <span data-ttu-id="cd163-105">此權杖是您的密碼，並由 VSTS 組建代理程式用來驗證。</span><span class="sxs-lookup"><span data-stu-id="cd163-105">This token is your password, and is used by the VSTS build agent to authenticate.</span></span> <span data-ttu-id="cd163-106">當您在建立時，才會顯示此語彙基元。</span><span class="sxs-lookup"><span data-stu-id="cd163-106">The token is only displayed when you create it.</span></span> <span data-ttu-id="cd163-107">在那之後，它不會顯示不再。</span><span class="sxs-lookup"><span data-stu-id="cd163-107">After that, it isn't displayed anymore.</span></span> <span data-ttu-id="cd163-108">因此一旦您建立它，將它儲存到另一個可記住的位置中的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd163-108">So once you create it, save it to another file in a remember-able location.</span></span> 

<span data-ttu-id="cd163-109">深入了解在 PAT[驗證適用於 VSTS 和 TFS 的個人存取權杖以存取](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate)。</span><span class="sxs-lookup"><span data-stu-id="cd163-109">More info on PAT at [Authenticate access with personal access tokens for VSTS and TFS](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate).</span></span> 

<span data-ttu-id="cd163-110">建立權杖之後，您會安裝組建代理程式，並將它設定為使用此權杖。</span><span class="sxs-lookup"><span data-stu-id="cd163-110">After you create the token, you install the build agent, and configure it to use this token.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="cd163-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="cd163-111">Before you begin</span></span>
<span data-ttu-id="cd163-112">完整[步驟 1-新增應用程式專案，並更新 json](feature-pack-add-application-project.md)。</span><span class="sxs-lookup"><span data-stu-id="cd163-112">Complete [Step 1 - Add Application project and update json](feature-pack-add-application-project.md).</span></span>

## <a name="sign-into-vsts-and-create-the-token"></a><span data-ttu-id="cd163-113">登入 VSTS，並建立權杖</span><span class="sxs-lookup"><span data-stu-id="cd163-113">Sign into VSTS, and create the token</span></span>
1. <span data-ttu-id="cd163-114">移至[ https://app.vsaex.visualstudio.com/go/profile ](https://app.vsaex.visualstudio.com/go/profile)，並使用您的公司或學校帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="cd163-114">Go to [https://app.vsaex.visualstudio.com/go/profile](https://app.vsaex.visualstudio.com/go/profile), and sign-in with your work or school account.</span></span> <span data-ttu-id="cd163-115">登入之後，會列出您的 VSTS 帳戶。</span><span class="sxs-lookup"><span data-stu-id="cd163-115">After you sign in, your VSTS account is listed.</span></span> <span data-ttu-id="cd163-116">在下列範例中，帳戶是**mandiaprojects.visualstudio.com**。</span><span class="sxs-lookup"><span data-stu-id="cd163-116">In the following example, the account is **mandiaprojects.visualstudio.com**.</span></span>  

    ![VSTS 帳戶](../core/media/team-services-accounts.png)

    <span data-ttu-id="cd163-118">如果您還沒有帳戶，請選取**建立新帳戶**，然後輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="cd163-118">If you don’t have an account, select **Create new account**, and enter a name.</span></span> <span data-ttu-id="cd163-119">若要管理您的程式碼，請選擇您個人的喜好設定之間**Git 或 Team Foundation 版本控制**。</span><span class="sxs-lookup"><span data-stu-id="cd163-119">To manage your code, choose your personal preference between **Git or Team Foundation Version Control**.</span></span> <span data-ttu-id="cd163-120">完成時，會建立新的帳戶，和類似的站台*https://YourAccountName.visualstudio.com/MyFirstProject*開啟：</span><span class="sxs-lookup"><span data-stu-id="cd163-120">When finished, your new account is created, and a site similar to *https://YourAccountName.visualstudio.com/MyFirstProject* opens:</span></span>  

    ![Git 或 TFS](../core/media/git-or-team-foundation.png)

2. <span data-ttu-id="cd163-122">開啟您的 VSTS 帳戶 (https://<em>YourAccountName</em>。 visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="cd163-122">Open your VSTS account (https://<em>YourAccountName</em>.visualstudio.com).</span></span> <span data-ttu-id="cd163-123">在右側角，選取您的圖示，然後選取**安全性**:</span><span class="sxs-lookup"><span data-stu-id="cd163-123">Select your icon in the top right-side corner, and select **Security**:</span></span> 

    ![開啟您的帳戶安全性](../core/media/vsts-account-security.png)

3. <span data-ttu-id="cd163-125">**個人存取權杖**會自動開啟。</span><span class="sxs-lookup"><span data-stu-id="cd163-125">**Personal access tokens** automatically opens.</span></span> <span data-ttu-id="cd163-126">如果您有現有的代理程式時，加以選取，並確認**代理程式集區 （讀取、 管理）** 選取：</span><span class="sxs-lookup"><span data-stu-id="cd163-126">If you have an existing agent, select it, and confirm **Agent Pools (read, manage)** is selected:</span></span>

    ![代理程式集區-讀取與管理](../core/media/agent-pools-read-manage.png)

    > [!IMPORTANT]
    > <span data-ttu-id="cd163-128">您必須知道的存取權杖。</span><span class="sxs-lookup"><span data-stu-id="cd163-128">You must know the access token.</span></span> <span data-ttu-id="cd163-129">如果您不這麼做，並沒有記下任何位置，便無法加以擷取。</span><span class="sxs-lookup"><span data-stu-id="cd163-129">If you don’t, and didn’t note it anywhere, it cannot be retrieved.</span></span> <span data-ttu-id="cd163-130">在此情況下，建立新的代理程式。</span><span class="sxs-lookup"><span data-stu-id="cd163-130">In this situation, create a new agent.</span></span> 

    <span data-ttu-id="cd163-131">如果您沒有現有的代理程式，請選取**新增**、 輸入描述，設定到期日，然後選取您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="cd163-131">If you don’t have an existing agent, select **Add**, enter a description, set the expiration date, and select your account.</span></span> <span data-ttu-id="cd163-132">在 **選取範圍**，選取**代理程式集區 （讀取、 管理）**:</span><span class="sxs-lookup"><span data-stu-id="cd163-132">In **Selected scopes**, select **Agent Pools (read, manage)**:</span></span> 

    ![建立新的代理程式-讀取與管理](../core/media/vsts-new-build-agent.png)

    <span data-ttu-id="cd163-134">選取 **建立權杖**。</span><span class="sxs-lookup"><span data-stu-id="cd163-134">Select **Create Token**.</span></span> <span data-ttu-id="cd163-135">**請注意語彙基元的值;您必須在未來的步驟。**</span><span class="sxs-lookup"><span data-stu-id="cd163-135">**Note the token value; you need in future steps.**</span></span>

4. <span data-ttu-id="cd163-136">選取 **程式碼**，然後選取**在 Visual Studio 中的複製**:</span><span class="sxs-lookup"><span data-stu-id="cd163-136">Select **Code**, and select **Clone in Visual Studio**:</span></span>  

    ![在專案中，選取 程式碼](../core/media/vsts-project-code.png)  

    ![在 Visual Studio 中複製](../core/media/vsts-clone-in-visual-studio.png)

5. <span data-ttu-id="cd163-139">Visual Studio 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="cd163-139">Visual Studio opens.</span></span> <span data-ttu-id="cd163-140">在 Visual Studio 中，開啟您的 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="cd163-140">Within Visual Studio, open your BizTalk solution.</span></span> 

## <a name="install-the-build-agent"></a><span data-ttu-id="cd163-141">安裝組建代理程式</span><span class="sxs-lookup"><span data-stu-id="cd163-141">Install the Build Agent</span></span>

<span data-ttu-id="cd163-142">BizTalk 開發電腦上安裝組建代理程式。</span><span class="sxs-lookup"><span data-stu-id="cd163-142">The build agent is installed on the BizTalk development computer.</span></span> <span data-ttu-id="cd163-143">使用部署群組，如果您想要部署到的所有 BizTalk 伺服器上安裝組建代理程式。</span><span class="sxs-lookup"><span data-stu-id="cd163-143">If using deployment groups, the build agent is installed on all the BizTalk servers you want to deploy to.</span></span> <span data-ttu-id="cd163-144">下列步驟會示範如何在單一電腦上安裝組建代理程式。</span><span class="sxs-lookup"><span data-stu-id="cd163-144">The following steps show you how to install the build agent on a single computer.</span></span> <span data-ttu-id="cd163-145">如需有關使用部署群組的詳細資訊，請參閱 <<c0> [ 部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index)。</span><span class="sxs-lookup"><span data-stu-id="cd163-145">For details on using deployment groups, see [Deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index).</span></span>

1. <span data-ttu-id="cd163-146">開啟您的 VSTS 帳戶和專案中，這不是想 *https://YourAccountName.visualstudio.com/MyFirstProject* 。</span><span class="sxs-lookup"><span data-stu-id="cd163-146">Open your VSTS account and project, which is something like *https://YourAccountName.visualstudio.com/MyFirstProject*.</span></span> <span data-ttu-id="cd163-147">選取 [設定] 圖示，然後選取**代理程式佇列**:</span><span class="sxs-lookup"><span data-stu-id="cd163-147">Select the settings icon, and select **Agent Queues**:</span></span>  

    ![設定 > 代理程式佇列](../core/media/vsts-settings-agent-queues.png)

2. <span data-ttu-id="cd163-149">選取 **預設**代理程式，然後選取**下載代理程式**。</span><span class="sxs-lookup"><span data-stu-id="cd163-149">Select the **Default** agent, and select **Download Agent**.</span></span> <span data-ttu-id="cd163-150">選取 **下載**按鈕，然後將檔案儲存到您**下載**資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd163-150">Select the **Download** button, and save the file to your **Downloads** folders.</span></span>

3. <span data-ttu-id="cd163-151">安裝步驟自動開啟。</span><span class="sxs-lookup"><span data-stu-id="cd163-151">The install steps automatically open.</span></span> <span data-ttu-id="cd163-152">請遵循這些步驟的最新詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cd163-152">Follow those steps for the most up-to-date details.</span></span> <span data-ttu-id="cd163-153">以下是一些指引：</span><span class="sxs-lookup"><span data-stu-id="cd163-153">Here is some guidance:</span></span> 

   1. <span data-ttu-id="cd163-154">系統管理員身分開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cd163-154">Open Windows PowerShell as Administrator.</span></span>

   2. <span data-ttu-id="cd163-155">若要建立代理程式，請輸入：</span><span class="sxs-lookup"><span data-stu-id="cd163-155">To create the agent, enter:</span></span> 

       ```powershell
       PS C:\> mkdir agent ; cd agent  

       PS C:\agent> Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win7-x64-2.124.0.zip", "$PWD")
       ```

       <span data-ttu-id="cd163-156">Vsts 代理程式的檔案版本變更。</span><span class="sxs-lookup"><span data-stu-id="cd163-156">The vsts-agent file version changes.</span></span> <span data-ttu-id="cd163-157">因此請遵循 VSTS 安裝步驟的特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="cd163-157">So follow the VSTS install steps for specific details.</span></span> <span data-ttu-id="cd163-158">您按下之後輸入，可能需要數分鐘，返回提示字元。</span><span class="sxs-lookup"><span data-stu-id="cd163-158">After you hit enter, it may take a couple of minutes for the prompt to return.</span></span> 

   3. <span data-ttu-id="cd163-159">若要設定代理程式，請輸入：</span><span class="sxs-lookup"><span data-stu-id="cd163-159">To configure the agent, enter:</span></span> 

       ```powershell
       PS C:\agent> .\config.cmd
       ```

   4. <span data-ttu-id="cd163-160">輸入下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="cd163-160">Enter the following details:</span></span>  


      |        <span data-ttu-id="cd163-161">屬性</span><span class="sxs-lookup"><span data-stu-id="cd163-161">Property</span></span>        |                                                                      <span data-ttu-id="cd163-162">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="cd163-162">Value</span></span>                                                                       |
      |------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
      |       <span data-ttu-id="cd163-163">伺服器 URL</span><span class="sxs-lookup"><span data-stu-id="cd163-163">Server URL</span></span>       |                                                     <span data-ttu-id="cd163-164">https://{your-account}.visualstudio.com</span><span class="sxs-lookup"><span data-stu-id="cd163-164">https://{your-account}.visualstudio.com</span></span>                                                      |
      |  <span data-ttu-id="cd163-165">驗證類型</span><span class="sxs-lookup"><span data-stu-id="cd163-165">Authentication Type</span></span>   |                                                                       <span data-ttu-id="cd163-166">PAT</span><span class="sxs-lookup"><span data-stu-id="cd163-166">PAT</span></span>                                                                        |
      | <span data-ttu-id="cd163-167">個人存取權杖</span><span class="sxs-lookup"><span data-stu-id="cd163-167">Personal access token</span></span>  |                                                              <span data-ttu-id="cd163-168">貼上您的 VSTS 權杖</span><span class="sxs-lookup"><span data-stu-id="cd163-168">Paste your VSTS token</span></span>                                                               |
      |       <span data-ttu-id="cd163-169">代理程式集區</span><span class="sxs-lookup"><span data-stu-id="cd163-169">Agent pool</span></span>       |                                                              <span data-ttu-id="cd163-170">輸入預設值</span><span class="sxs-lookup"><span data-stu-id="cd163-170">Enter for the default</span></span>                                                               |
      |       <span data-ttu-id="cd163-171">代理程式名稱</span><span class="sxs-lookup"><span data-stu-id="cd163-171">Agent name</span></span>       |                                                              <span data-ttu-id="cd163-172">輸入預設值</span><span class="sxs-lookup"><span data-stu-id="cd163-172">Enter for the default</span></span>                                                               |
      |        <span data-ttu-id="cd163-173">取代</span><span class="sxs-lookup"><span data-stu-id="cd163-173">Replace</span></span>         |                                                  <span data-ttu-id="cd163-174">*只會顯示如果您有現有的代理程式*</span><span class="sxs-lookup"><span data-stu-id="cd163-174">*Only displays if you have an existing agent*</span></span>                                                   |
      |      <span data-ttu-id="cd163-175">工作資料夾</span><span class="sxs-lookup"><span data-stu-id="cd163-175">Work folder</span></span>       |                                                              <span data-ttu-id="cd163-176">輸入預設值</span><span class="sxs-lookup"><span data-stu-id="cd163-176">Enter for the default</span></span>                                                               |
      | <span data-ttu-id="cd163-177">以服務方式執行代理程式</span><span class="sxs-lookup"><span data-stu-id="cd163-177">Run agent as a service</span></span> |                                                                        <span data-ttu-id="cd163-178">Y</span><span class="sxs-lookup"><span data-stu-id="cd163-178">Y</span></span>                                                                         |
      |      <span data-ttu-id="cd163-179">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cd163-179">User account</span></span>      | <span data-ttu-id="cd163-180">這是由您決定，但您可能會遇到權限問題。</span><span class="sxs-lookup"><span data-stu-id="cd163-180">This is up to you, but you may run into a permissions issue.</span></span> <br/><br/><span data-ttu-id="cd163-181">請考慮輸入您目前已登入的帳戶，也就是本機系統管理員。</span><span class="sxs-lookup"><span data-stu-id="cd163-181">Consider entering your current logged-on account, which is a local Admin.</span></span> |


   5. <span data-ttu-id="cd163-182">完成時，您的 PowerShell 視窗看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="cd163-182">When finished, your PowerShell window looks like the following:</span></span>  

       ![代理程式安裝](../core/media/vsts-agent-powershell-install.png)

4. <span data-ttu-id="cd163-184">若要查看新的服務開啟 services.msc。</span><span class="sxs-lookup"><span data-stu-id="cd163-184">Open services.msc to see the new service.</span></span> <span data-ttu-id="cd163-185">它應該執行：</span><span class="sxs-lookup"><span data-stu-id="cd163-185">It should be running:</span></span>  

    ![服務正在執行](../core/media/vsts-service.png)

    <span data-ttu-id="cd163-187">如果服務無法啟動，請[移除並重新設定代理程式](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows)使用具有更多的權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="cd163-187">If the service fails to start, [remove and re-configure an agent](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows) using an account with more privilages.</span></span>


## <a name="what-you-did"></a><span data-ttu-id="cd163-188">您的作法</span><span class="sxs-lookup"><span data-stu-id="cd163-188">What you did</span></span>

<span data-ttu-id="cd163-189">您登入您的 VSTS 帳戶，並建立安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="cd163-189">You signed into your VSTS account, and created a security token.</span></span> <span data-ttu-id="cd163-190">這個安全性權杖就像是使用密碼，並可讓您存取您的 VSTS 專案。</span><span class="sxs-lookup"><span data-stu-id="cd163-190">This security token is like a password, and gives you access to your VSTS project.</span></span> <span data-ttu-id="cd163-191">它只會顯示一次，因此要確定您儲存它。</span><span class="sxs-lookup"><span data-stu-id="cd163-191">It's only displayed once, so be sure you saved it.</span></span> <span data-ttu-id="cd163-192">您也可以複製您的 VSTS 專案至 Visual Studio，然後建立 BizTalk 開發電腦以服務形式執行的代理程式。</span><span class="sxs-lookup"><span data-stu-id="cd163-192">You also cloned your VSTS project into Visual Studio, and created an agent that runs as a service on your BizTalk development computer.</span></span> <span data-ttu-id="cd163-193">此代理程式會使用安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="cd163-193">This agent uses the security token.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="cd163-194">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="cd163-194">Next steps</span></span>
[<span data-ttu-id="cd163-195">步驟 3： 建立組建和發行定義</span><span class="sxs-lookup"><span data-stu-id="cd163-195">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)  
[<span data-ttu-id="cd163-196">設定環境權杖和變數</span><span class="sxs-lookup"><span data-stu-id="cd163-196">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)