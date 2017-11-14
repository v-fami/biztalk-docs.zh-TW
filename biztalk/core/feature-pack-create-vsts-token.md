---
title: "步驟 2-建立 VSTS 權杖並安裝代理程式 |Microsoft 文件"
description: "Visual studio，建立 VSTS 安全性存取語彙基元，複製 VSTS 專案，並安裝來自動化部署的 BizTalk Server 專案的組建代理程式"
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
ms.openlocfilehash: 46047f0bb6a536642d503d68bb4f9161ecdf7fc5
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="step-2-create-the-token--install-the-agent"></a><span data-ttu-id="c9870-103">步驟 2： 建立權杖，並安裝代理程式</span><span class="sxs-lookup"><span data-stu-id="c9870-103">Step 2: Create the token & install the agent</span></span>

<span data-ttu-id="c9870-104">Visual Studio Team Services 中建立個人存取權杖 (PAT)。</span><span class="sxs-lookup"><span data-stu-id="c9870-104">A personal access token (PAT) is created in Visual Studio Team Services.</span></span> <span data-ttu-id="c9870-105">這個語彙基元是您的密碼，並可由 VSTS 組建代理程式來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="c9870-105">This token is your password, and is used by the VSTS build agent to authenticate.</span></span> <span data-ttu-id="c9870-106">當您建立它時，才會顯示語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c9870-106">The token is only displayed when you create it.</span></span> <span data-ttu-id="c9870-107">在這之後，它不會顯示不再。</span><span class="sxs-lookup"><span data-stu-id="c9870-107">After that, it isn't displayed anymore.</span></span> <span data-ttu-id="c9870-108">因此一旦您建立它，將它儲存到另一個檔案中可記住的位置。</span><span class="sxs-lookup"><span data-stu-id="c9870-108">So once you create it, save it to another file in a remember-able location.</span></span> 

<span data-ttu-id="c9870-109">在 PAT 上的進一歩[驗證個人存取權杖以存取 VSTS 和 TFS](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate)。</span><span class="sxs-lookup"><span data-stu-id="c9870-109">More info on PAT at [Authenticate access with personal access tokens for VSTS and TFS](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate).</span></span> 

<span data-ttu-id="c9870-110">建立權杖之後，您會安裝組建代理程式，並將它設定為使用此權杖。</span><span class="sxs-lookup"><span data-stu-id="c9870-110">After you create the token, you install the build agent, and configure it to use this token.</span></span> 

## <a name="sign-into-vsts-and-create-the-token"></a><span data-ttu-id="c9870-111">登入 VSTS，並建立語彙基元</span><span class="sxs-lookup"><span data-stu-id="c9870-111">Sign into VSTS, and create the token</span></span>
1. <span data-ttu-id="c9870-112">移至[https://app.vsaex.visualstudio.com/go/profile](https://app.vsaex.visualstudio.com/go/profile)，並使用您的工作或學校帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c9870-112">Go to [https://app.vsaex.visualstudio.com/go/profile](https://app.vsaex.visualstudio.com/go/profile), and sign-in with your work or school account.</span></span> <span data-ttu-id="c9870-113">在您登入後，會列出 VSTS 帳戶。</span><span class="sxs-lookup"><span data-stu-id="c9870-113">After you sign in, your VSTS account is listed.</span></span> <span data-ttu-id="c9870-114">在下列範例中，此帳戶是**mandiaprojects.visualstudio.com**。</span><span class="sxs-lookup"><span data-stu-id="c9870-114">In the following example, the account is **mandiaprojects.visualstudio.com**.</span></span>  

    ![VSTS 帳戶](../core/media/team-services-accounts.png)

    <span data-ttu-id="c9870-116">如果您沒有帳戶，請選取**建立新帳戶**，然後輸入的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9870-116">If you don’t have an account, select **Create new account**, and enter a name.</span></span> <span data-ttu-id="c9870-117">若要管理您的程式碼中，選擇您個人的喜好設定之間**Git 或 Team Foundation 版本控制**。</span><span class="sxs-lookup"><span data-stu-id="c9870-117">To manage your code, choose your personal preference between **Git or Team Foundation Version Control**.</span></span> <span data-ttu-id="c9870-118">完成時，會建立新的帳戶，而且類似於站台*https://YourAccountName.visualstudio.com/MyFirstProject*開啟：</span><span class="sxs-lookup"><span data-stu-id="c9870-118">When finished, your new account is created, and a site similar to *https://YourAccountName.visualstudio.com/MyFirstProject* opens:</span></span>  

    ![Git 或 TFS](../core/media/git-or-team-foundation.png)

2. <span data-ttu-id="c9870-120">開啟 VSTS 帳戶 (https://*YourAccountName*。 visualstudio.com)。</span><span class="sxs-lookup"><span data-stu-id="c9870-120">Open your VSTS account (https://*YourAccountName*.visualstudio.com).</span></span> <span data-ttu-id="c9870-121">在右邊的角，選取您的圖示，然後選取**安全性**:</span><span class="sxs-lookup"><span data-stu-id="c9870-121">Select your icon in the top right-side corner, and select **Security**:</span></span> 

    ![開啟您的帳戶安全性](../core/media/vsts-account-security.png)

3. <span data-ttu-id="c9870-123">**個人存取權杖**會自動開啟。</span><span class="sxs-lookup"><span data-stu-id="c9870-123">**Personal access tokens** automatically opens.</span></span> <span data-ttu-id="c9870-124">如果您有現有的代理程式時，加以選取，並確認**代理程式集區 （讀取、 管理）**選取：</span><span class="sxs-lookup"><span data-stu-id="c9870-124">If you have an existing agent, select it, and confirm **Agent Pools (read, manage)** is selected:</span></span>

    ![代理程式集區的讀取及管理](../core/media/agent-pools-read-manage.png)

    > [!IMPORTANT]
    > <span data-ttu-id="c9870-126">您必須知道存取權杖。</span><span class="sxs-lookup"><span data-stu-id="c9870-126">You must know the access token.</span></span> <span data-ttu-id="c9870-127">如果您不這麼做，而且沒有任何位置注意它，便無法加以擷取。</span><span class="sxs-lookup"><span data-stu-id="c9870-127">If you don’t, and didn’t note it anywhere, it cannot be retrieved.</span></span> <span data-ttu-id="c9870-128">在此情況下，建立新的代理程式。</span><span class="sxs-lookup"><span data-stu-id="c9870-128">In this situation, create a new agent.</span></span> 

    <span data-ttu-id="c9870-129">如果您沒有現有的代理程式，選取**新增**、 輸入描述、 設定到期日，然後選取您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c9870-129">If you don’t have an existing agent, select **Add**, enter a description, set the expiration date, and select your account.</span></span> <span data-ttu-id="c9870-130">在**選取範圍**，選取**代理程式集區 （讀取、 管理）**:</span><span class="sxs-lookup"><span data-stu-id="c9870-130">In **Selected scopes**, select **Agent Pools (read, manage)**:</span></span> 

    ![建立新的代理程式-讀取及管理](../core/media/vsts-new-build-agent.png)

    <span data-ttu-id="c9870-132">選取**建立語彙基元**。</span><span class="sxs-lookup"><span data-stu-id="c9870-132">Select **Create Token**.</span></span> <span data-ttu-id="c9870-133">**請注意語彙基元的值;您需要在未來步驟。**</span><span class="sxs-lookup"><span data-stu-id="c9870-133">**Note the token value; you need in future steps.**</span></span>

4. <span data-ttu-id="c9870-134">選取**程式碼**，然後選取**Visual Studio 中的複製**:</span><span class="sxs-lookup"><span data-stu-id="c9870-134">Select **Code**, and select **Clone in Visual Studio**:</span></span>  

    ![在專案中，選取 程式碼](../core/media/vsts-project-code.png)  

    ![在 Visual Studio 中複製](../core/media/vsts-clone-in-visual-studio.png)

5. <span data-ttu-id="c9870-137">Visual Studio 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="c9870-137">Visual Studio opens.</span></span> <span data-ttu-id="c9870-138">在 Visual Studio 中，開啟您的 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="c9870-138">Within Visual Studio, open your BizTalk solution.</span></span> 

## <a name="install-the-build-agent"></a><span data-ttu-id="c9870-139">安裝組建代理程式</span><span class="sxs-lookup"><span data-stu-id="c9870-139">Install the Build Agent</span></span>

<span data-ttu-id="c9870-140">BizTalk 開發電腦上安裝的組建代理程式。</span><span class="sxs-lookup"><span data-stu-id="c9870-140">The build agent is installed on the BizTalk development computer.</span></span> 

1. <span data-ttu-id="c9870-141">開啟您的 VSTS 帳戶和專案中，這不是像*https://YourAccountName.visualstudio.com/MyFirstProject*。</span><span class="sxs-lookup"><span data-stu-id="c9870-141">Open your VSTS account and project, which is something like *https://YourAccountName.visualstudio.com/MyFirstProject*.</span></span> <span data-ttu-id="c9870-142">選取 [設定] 圖示，然後選取**代理程式佇列**:</span><span class="sxs-lookup"><span data-stu-id="c9870-142">Select the settings icon, and select **Agent Queues**:</span></span>  

    ![設定 > 代理程式佇列](../core/media/vsts-settings-agent-queues.png)

2. <span data-ttu-id="c9870-144">選取**預設**代理程式，然後選取**下載代理程式**。</span><span class="sxs-lookup"><span data-stu-id="c9870-144">Select the **Default** agent, and select **Download Agent**.</span></span> <span data-ttu-id="c9870-145">選取**下載**按鈕，然後檔案儲存到您**下載**資料夾。</span><span class="sxs-lookup"><span data-stu-id="c9870-145">Select the **Download** button, and save the file to your **Downloads** folders.</span></span>

3. <span data-ttu-id="c9870-146">安裝步驟，自動開啟。</span><span class="sxs-lookup"><span data-stu-id="c9870-146">The install steps automatically open.</span></span> <span data-ttu-id="c9870-147">請遵循這些步驟最新詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c9870-147">Follow those steps for the most up-to-date details.</span></span> <span data-ttu-id="c9870-148">以下是一些指導方針：</span><span class="sxs-lookup"><span data-stu-id="c9870-148">Here is some guidance:</span></span> 

    1. <span data-ttu-id="c9870-149">以系統管理員身分開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c9870-149">Open Windows PowerShell as Administrator.</span></span>

    2. <span data-ttu-id="c9870-150">若要建立代理程式，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c9870-150">To create the agent, enter:</span></span> 

        ```powershell
        PS C:\> mkdir agent ; cd agent  

        PS C:\agent> Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win7-x64-2.124.0.zip", "$PWD")
        ```
    
        <span data-ttu-id="c9870-151">Vsts 代理程式的檔案版本變更。</span><span class="sxs-lookup"><span data-stu-id="c9870-151">The vsts-agent file version changes.</span></span> <span data-ttu-id="c9870-152">因此請依照 VSTS 安裝的特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c9870-152">So follow the VSTS install steps for specific details.</span></span> <span data-ttu-id="c9870-153">您到達後輸入，可能需要幾分鐘的提示，以傳回。</span><span class="sxs-lookup"><span data-stu-id="c9870-153">After you hit enter, it may take a couple of minutes for the prompt to return.</span></span> 

    3. <span data-ttu-id="c9870-154">若要設定代理程式，請輸入：</span><span class="sxs-lookup"><span data-stu-id="c9870-154">To configure the agent, enter:</span></span> 

        ```powershell
        PS C:\agent> .\config.cmd
        ```

    4. <span data-ttu-id="c9870-155">輸入下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="c9870-155">Enter the following details:</span></span>  
        
        | <span data-ttu-id="c9870-156">屬性</span><span class="sxs-lookup"><span data-stu-id="c9870-156">Property</span></span> | <span data-ttu-id="c9870-157">值</span><span class="sxs-lookup"><span data-stu-id="c9870-157">Value</span></span> |
        | --- | --- |
        | <span data-ttu-id="c9870-158">伺服器 URL</span><span class="sxs-lookup"><span data-stu-id="c9870-158">Server URL</span></span>| <span data-ttu-id="c9870-159">https://{your-account}.visualstudio.com</span><span class="sxs-lookup"><span data-stu-id="c9870-159">https://{your-account}.visualstudio.com</span></span> |
        | <span data-ttu-id="c9870-160">驗證類型</span><span class="sxs-lookup"><span data-stu-id="c9870-160">Authentication Type</span></span> | <span data-ttu-id="c9870-161">PAT</span><span class="sxs-lookup"><span data-stu-id="c9870-161">PAT</span></span> |
        | <span data-ttu-id="c9870-162">個人存取權杖</span><span class="sxs-lookup"><span data-stu-id="c9870-162">Personal access token</span></span> | <span data-ttu-id="c9870-163">貼上您 VSTS 語彙基元</span><span class="sxs-lookup"><span data-stu-id="c9870-163">Paste your VSTS token</span></span> |
        | <span data-ttu-id="c9870-164">代理程式集區</span><span class="sxs-lookup"><span data-stu-id="c9870-164">Agent pool</span></span> | <span data-ttu-id="c9870-165">輸入預設值</span><span class="sxs-lookup"><span data-stu-id="c9870-165">Enter for the default</span></span> |
        | <span data-ttu-id="c9870-166">代理程式名稱</span><span class="sxs-lookup"><span data-stu-id="c9870-166">Agent name</span></span> | <span data-ttu-id="c9870-167">輸入預設值</span><span class="sxs-lookup"><span data-stu-id="c9870-167">Enter for the default</span></span> |
        | <span data-ttu-id="c9870-168">取代</span><span class="sxs-lookup"><span data-stu-id="c9870-168">Replace</span></span> | <span data-ttu-id="c9870-169">*如果您有現有的代理程式只會顯示*</span><span class="sxs-lookup"><span data-stu-id="c9870-169">*Only displays if you have an existing agent*</span></span> |
        | <span data-ttu-id="c9870-170">工作資料夾</span><span class="sxs-lookup"><span data-stu-id="c9870-170">Work folder</span></span> | <span data-ttu-id="c9870-171">輸入預設值</span><span class="sxs-lookup"><span data-stu-id="c9870-171">Enter for the default</span></span> |
        | <span data-ttu-id="c9870-172">以服務方式執行代理程式</span><span class="sxs-lookup"><span data-stu-id="c9870-172">Run agent as a service</span></span> | <span data-ttu-id="c9870-173">Y</span><span class="sxs-lookup"><span data-stu-id="c9870-173">Y</span></span> |
        | <span data-ttu-id="c9870-174">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c9870-174">User account</span></span> | <span data-ttu-id="c9870-175">這是可以自行決定，但您可能會遇到權限問題。</span><span class="sxs-lookup"><span data-stu-id="c9870-175">This is up to you, but you may run into a permissions issue.</span></span> <br/><br/><span data-ttu-id="c9870-176">請考慮輸入您目前登入的帳戶，也就是本機系統管理員。</span><span class="sxs-lookup"><span data-stu-id="c9870-176">Consider entering your current logged-on account, which is a local Admin.</span></span> |

    5. <span data-ttu-id="c9870-177">完成時，您的 PowerShell 視窗看起來如下：</span><span class="sxs-lookup"><span data-stu-id="c9870-177">When finished, your PowerShell window looks like the following:</span></span>  
    
        ![代理程式安裝](../core/media/vsts-agent-powershell-install.png)

4. <span data-ttu-id="c9870-179">若要查看新的服務開啟 services.msc。</span><span class="sxs-lookup"><span data-stu-id="c9870-179">Open services.msc to see the new service.</span></span> <span data-ttu-id="c9870-180">它應執行：</span><span class="sxs-lookup"><span data-stu-id="c9870-180">It should be running:</span></span>  

    ![服務正在執行](../core/media/vsts-service.png)

    <span data-ttu-id="c9870-182">如果服務無法啟動，[移除並重新設定代理程式](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows)使用具有更多的權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c9870-182">If the service fails to start, [remove and re-configure an agent](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows) using an account with more privilages.</span></span>


## <a name="what-you-did"></a><span data-ttu-id="c9870-183">您的作法</span><span class="sxs-lookup"><span data-stu-id="c9870-183">What you did</span></span>

<span data-ttu-id="c9870-184">您登入您的 VSTS 帳戶，並建立安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="c9870-184">You signed into your VSTS account, and created a security token.</span></span> <span data-ttu-id="c9870-185">這個安全性權杖就像密碼，並可讓您存取 VSTS 專案。</span><span class="sxs-lookup"><span data-stu-id="c9870-185">This security token is like a password, and gives you access to your VSTS project.</span></span> <span data-ttu-id="c9870-186">它只會顯示一次，因此會確定您儲存它。</span><span class="sxs-lookup"><span data-stu-id="c9870-186">It's only displayed once, so be sure you saved it.</span></span> <span data-ttu-id="c9870-187">您也可以複製 VSTS 專案到 Visual Studio 中，然後建立 BizTalk 開發電腦以服務方式執行的代理程式。</span><span class="sxs-lookup"><span data-stu-id="c9870-187">You also cloned your VSTS project into Visual Studio, and created an agent that runs as a service on your BizTalk development computer.</span></span> <span data-ttu-id="c9870-188">此代理程式會使用安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="c9870-188">This agent uses the security token.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="c9870-189">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="c9870-189">Next steps</span></span>
[<span data-ttu-id="c9870-190">步驟 3： 建立組建和發行定義</span><span class="sxs-lookup"><span data-stu-id="c9870-190">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)  
[<span data-ttu-id="c9870-191">設定環境的語彙基元和變數</span><span class="sxs-lookup"><span data-stu-id="c9870-191">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)