---
title: "步驟 1-新增應用程式專案和更新的 json |Microsoft 文件"
description: "在 Visual Studio 中，將 BizTalk Server 應用程式專案，並更新 BizTalkServerInventory.json 檔使用的 Dll、 繫結檔案和應用程式-Visual Studio Team Services 的部署序列"
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
ms.openlocfilehash: 46cb8a2072280e62cd8c3438521531f8cf3b55aa
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="step-1-add-the-biztalk-server-application-project-in-visual-studio"></a><span data-ttu-id="ab0d3-103">步驟 1: Visual Studio 中加入 BizTalk Server 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="ab0d3-103">Step 1: Add the BizTalk Server Application project in Visual Studio</span></span>

<span data-ttu-id="ab0d3-104">當您建置應用程式使用 Visual Studio Team Services 時，新的 BizTalk 專案檔會建立 –.btaproj。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-104">When you build your applications using Visual Studio Team Services, a new BizTalk project file is created – .btaproj.</span></span> <span data-ttu-id="ab0d3-105">這個新專案會保存所有的 BizTalk 應用程式您建置和部署使用 VSTS 建置和發行功能。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-105">This new project holds all the BizTalk applications that you build and deploy using the VSTS build and release features.</span></span> 

<span data-ttu-id="ab0d3-106">BizTalk 應用程式專案包含`BizTalkServerInventory.json`檔案。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-106">The BizTalk Application Project includes the `BizTalkServerInventory.json` file.</span></span> <span data-ttu-id="ab0d3-107">在此檔案中，新增 BizTalk 組件，加入 BizTalk 應用程式的繫結檔案，然後設定的部署順序。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-107">In this file, add your BizTalk assemblies, add the binding files for your BizTalk application, and then set a deployment sequence.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="ab0d3-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="ab0d3-108">Before you begin</span></span>

* <span data-ttu-id="ab0d3-109">這些步驟假設您有現有的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-109">These steps assume you have an existing BizTalk project.</span></span> <span data-ttu-id="ab0d3-110">如果沒有，您可以使用 HelloWorld sdk > 範例 (\Program Files (x86) \Microsoft BizTalk Server *yourVersion*\SDK\Samples\Orchestrations\HelloWorld)。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-110">If not, you can use the HelloWorld SDK sample (\Program Files (x86)\Microsoft BizTalk Server *yourVersion*\SDK\Samples\Orchestrations\HelloWorld).</span></span> 
* <span data-ttu-id="ab0d3-111">需要您準備好的 BizTalk 專案的 XML 繫結檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-111">Have the path to the XML binding file to your BizTalk project ready.</span></span> 
* <span data-ttu-id="ab0d3-112">知道 VSTS 帳戶、 您的集合和 team 專案的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-112">Know your VSTS account, your collection, and your team project details.</span></span>
* <span data-ttu-id="ab0d3-113">要熟悉 git 概念，包括複製，以及使用儲存機制。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-113">Be familiar with git concepts, including cloning and working with repositories.</span></span> 
* <span data-ttu-id="ab0d3-114">請務必[功能組件 1](https://www.microsoft.com/download/details.aspx?id=55100)安裝</span><span class="sxs-lookup"><span data-stu-id="ab0d3-114">Be sure [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) is installed</span></span>

## <a name="add-the-application-project"></a><span data-ttu-id="ab0d3-115">新增應用程式專案</span><span class="sxs-lookup"><span data-stu-id="ab0d3-115">Add the application project</span></span>

1. <span data-ttu-id="ab0d3-116">在 BizTalk 伺服器上，請在 Visual Studio 中開啟方案 (ProjectName.sln)。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-116">On the BizTalk Server, open your solution (ProjectName.sln) in Visual Studio.</span></span> <span data-ttu-id="ab0d3-117">請勿選取 Visual Studio 的 Blend。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-117">Do not select Visual Studio Blend.</span></span>

2. <span data-ttu-id="ab0d3-118">在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取**建置**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-118">In solution explorer, right-click your project, and select **Build**.</span></span> <span data-ttu-id="ab0d3-119">請確定您的組建成功。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-119">Be sure your build succeeds.</span></span> <span data-ttu-id="ab0d3-120">以滑鼠右鍵按一下您的專案，然後選取**部署**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-120">Right-click your project, and select **Deploy**.</span></span> <span data-ttu-id="ab0d3-121">請確定您的部署成功。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-121">Be sure your deploy succeeds.</span></span>

3. <span data-ttu-id="ab0d3-122">以滑鼠右鍵按一下您的方案中，選取**新增**，然後選取**加入新的專案**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-122">Right-click your solution, select **Add**, and select **Add New Project**.</span></span>

4. <span data-ttu-id="ab0d3-123">選取**BizTalk 專案**索引標籤上，選取**.NET Framework 4.6.1**從下拉式清單中，然後選取**BizTalk Server 應用程式專案**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-123">Select the **BizTalk Projects** tab, select **.NET Framework 4.6.1** from the drop-down list, and select **BizTalk Server Application Project**.</span></span> <span data-ttu-id="ab0d3-124">輸入名稱 (例如 appProjectHelloWorld)，並選取**確定**:</span><span class="sxs-lookup"><span data-stu-id="ab0d3-124">Enter a name (e.g. appProjectHelloWorld), and select **OK**:</span></span>  

    ![新增應用程式專案](../core/media/add-application-project.png)

5. <span data-ttu-id="ab0d3-126">在 [方案總管] 中，以滑鼠右鍵按一下新加入的應用程式專案 (.btaproj) 中，選取**新增**，選取**參考**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-126">In Solution Explorer, right-click your newly-added application project (.btaproj), select **Add**, select **Reference**.</span></span> <span data-ttu-id="ab0d3-127">展開**專案**索引標籤，並檢查您的 BizTalk 專案 （您要部署使用 VSTS 專案）。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-127">Expand the **Projects** tab, and check your BizTalk project (the project you are deploying using VSTS).</span></span> <span data-ttu-id="ab0d3-128">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-128">Select **OK**.</span></span>  
    <span data-ttu-id="ab0d3-129">一旦加入，依序展開**參考**應用程式專案 (例如 appProjectHelloWorld)，以查看 BizTalk 專案在您剛才加入。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-129">Once added, expand **References** under your application project (e.g. appProjectHelloWorld) to see the BizTalk project you just added.</span></span> 

6. <span data-ttu-id="ab0d3-130">在 [方案總管] 中，以滑鼠右鍵按一下您的應用程式專案 (.btaproj) 中，選取**新增**，選取**現有項目**，和**新增**您繫結的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-130">In Solution Explorer, right-click your application project (.btaproj), select **Add**, select **Existing Item**, and **Add** your binding XML file.</span></span>

7. <span data-ttu-id="ab0d3-131">開啟 binding.xml，內容和設定**複製到輸出目錄**至**永遠複製**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-131">Open the properties of binding.xml, and set **Copy to Output Directory** to **Copy always**.</span></span> <span data-ttu-id="ab0d3-132">**儲存**您的變更：</span><span class="sxs-lookup"><span data-stu-id="ab0d3-132">**Save** your changes:</span></span>  

    ![繫結檔案屬性](../core/media/xml-binding-file-properties.png)


## <a name="configure-the-json-template"></a><span data-ttu-id="ab0d3-134">設定的 JSON 範本</span><span class="sxs-lookup"><span data-stu-id="ab0d3-134">Configure the JSON template</span></span>

1. <span data-ttu-id="ab0d3-135">在 Visual Studio 中，在應用程式專案 (.btaproj)，開啟`BizTalkServerInventory.json`檔案。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-135">In Visual Studio, in your application project (.btaproj), open the `BizTalkServerInventory.json` file.</span></span> 

2. <span data-ttu-id="ab0d3-136">範本包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="ab0d3-136">The template includes the following sections:</span></span> 

    | | |
    |---|---|
    |<span data-ttu-id="ab0d3-137">BizTalkAssemblies</span><span class="sxs-lookup"><span data-stu-id="ab0d3-137">BizTalkAssemblies</span></span> | <span data-ttu-id="ab0d3-138">在應用程式中使用的組件</span><span class="sxs-lookup"><span data-stu-id="ab0d3-138">The assemblies used in your applications</span></span> |
    |<span data-ttu-id="ab0d3-139">BindingFiles</span><span class="sxs-lookup"><span data-stu-id="ab0d3-139">BindingFiles</span></span> | <span data-ttu-id="ab0d3-140">您所參考的繫結檔案</span><span class="sxs-lookup"><span data-stu-id="ab0d3-140">The binding files you are referencing</span></span>|
    |<span data-ttu-id="ab0d3-141">DeploymentSequence</span><span class="sxs-lookup"><span data-stu-id="ab0d3-141">DeploymentSequence</span></span> | <span data-ttu-id="ab0d3-142">若要安裝元素的順序</span><span class="sxs-lookup"><span data-stu-id="ab0d3-142">The sequence for the elements to be installed</span></span>|
    
    <span data-ttu-id="ab0d3-143">範例範本：</span><span class="sxs-lookup"><span data-stu-id="ab0d3-143">Sample template:</span></span> 
    
    ![FP1 Json 範本映像 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > <span data-ttu-id="ab0d3-145">根據您的方案的複雜度，您要在組建中的元素必須參考此 JSON 範本檔案中。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-145">Depending on the complexity of your solution, the elements you want in the build must be referenced in this JSON template file.</span></span>

3. <span data-ttu-id="ab0d3-146">在`BizTalkAssemblies`，將 BizTalk 專案所使用的組件：</span><span class="sxs-lookup"><span data-stu-id="ab0d3-146">In `BizTalkAssemblies`, add the assemblies used by your BizTalk project:</span></span> 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName"
            "Path": "PathToAssembly
        }
    ]
    ```

4. <span data-ttu-id="ab0d3-147">在`BindingsFiles`，新增您的 BizTalk 專案的繫結檔案：</span><span class="sxs-lookup"><span data-stu-id="ab0d3-147">In `BindingsFiles`, add the binding files for your BizTalk project:</span></span> 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name"
            "Path": "PathToBindingFile
        }
    ]
    ```

5. <span data-ttu-id="ab0d3-148">在`DeploymentSequence`，這些部署，以及安裝在您想要的順序新增應用程式名稱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ab0d3-148">In `DeploymentSequence`, add the application names in the order you want them deployed, and installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span></span> 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```


6. <span data-ttu-id="ab0d3-149">**儲存**您的變更。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-149">**Save** your changes.</span></span> <span data-ttu-id="ab0d3-150">完成時，您的.json 檔案看起來如下：</span><span class="sxs-lookup"><span data-stu-id="ab0d3-150">When finished, your .json file looks like the following:</span></span> 

    ```
    {
      "$schema": "C:\\Program Files (x86)\\Microsoft BizTalk Server 2016\\Developer Tools\\BizTalkServerAppplicationSchema.json",
      "BizTalkAssemblies": [
        {
          "Name": "HelloWorld",
          "Path": "HelloWorld\\bin\\Release\\HelloWorld.dll"
        }
      ],
      "BindingsFiles": [
        {
          "Name": "HelloWorldBinding",
          "Path": "HelloWorld\\HelloWorldBinding.xml"
        }
      ],
      "DeploymentSequence": [
        "HelloWorld", "HelloWorldBinding"
      ]
    }
    ```

7. <span data-ttu-id="ab0d3-151">**選擇性**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-151">**Optional**.</span></span> <span data-ttu-id="ab0d3-152">以滑鼠右鍵按一下您的應用程式專案 (例如 appProjectHelloWorld)，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-152">Right-click your application project (e.g. appProjectHelloWorld), and select **Properties**.</span></span> <span data-ttu-id="ab0d3-153">您可以設定偵錯或發行版本，為新值。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-153">You can set the Debug or Release version to a new value.</span></span> <span data-ttu-id="ab0d3-154">我們不在這些步驟中，但請留意執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-154">We don’t in these steps, but be aware you can do this.</span></span>  

    ![設定偵錯或發行版本](../core/media/application-project-version.png)

8. <span data-ttu-id="ab0d3-156">以滑鼠右鍵按一下您的應用程式專案 (例如 appProjectHelloWorld)，然後選取**建置**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-156">Right-click your application project (e.g. appProjectHelloWorld), and select **Build**.</span></span> <span data-ttu-id="ab0d3-157">如果成功，zip 檔案中建立 ***yourApplicationProject*\bin\debug**資料夾：</span><span class="sxs-lookup"><span data-stu-id="ab0d3-157">If it succeeds, a zip file is created in ***yourApplicationProject*\bin\debug** folder:</span></span>  

    ![建立 zip 檔案](../core/media/application-project-zip-file.png)

9. <span data-ttu-id="ab0d3-159">選取您的方案，然後選取**Team Explorer**  索引標籤。在 VSTS 中，選取**連接**。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-159">Select your solution, and select the **Team Explorer** tab. Under VSTS, select **Connect**.</span></span>  

    ![連接到 Team Services](../core/media/connect-team-services.png)

10. <span data-ttu-id="ab0d3-161">選取 VSTS 帳戶、 您的集合和 team 專案。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-161">Select your VSTS account, your collection, and your team project.</span></span> <span data-ttu-id="ab0d3-162">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-162">Select **OK**.</span></span> <span data-ttu-id="ab0d3-163">如果您尚未建立 VSTS 帳戶，然後建立一個 ([步驟 2： 建立 VSTS 權杖](feature-pack-create-vsts-token.md)提供一些指引)。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-163">If you didn’t create a VSTS account yet, then create one ([Step 2: Create the VSTS token](feature-pack-create-vsts-token.md) provides some guidance).</span></span> <span data-ttu-id="ab0d3-164">一旦建立之後，請返回此步驟中，並連接。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-164">Once it's created, come back to this step, and connect.</span></span>  

    ![選取您的集合和專案](../core/media/team-collections-projects.png)

11. <span data-ttu-id="ab0d3-166">當您連線時，可能會收到提示，要複製這個儲存機制。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-166">When you connect, you may get a prompt to clone this repository.</span></span> <span data-ttu-id="ab0d3-167">選取**複製這個儲存機制**連結。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-167">Select the **Clone this repository** link.</span></span>  

    ![複製儲存機制](../core/media/vsts-clone-repository.png)

12. <span data-ttu-id="ab0d3-169">請注意 URL 和路徑，然後選取**複製**:</span><span class="sxs-lookup"><span data-stu-id="ab0d3-169">Note the URL and paths, and select **Clone**:</span></span>  

    ![儲存機制路徑](../core/media/clone-repo-paths.png)

<span data-ttu-id="ab0d3-171">完成後，Visual Studio Team 服務部署工作會接受所需的檔案和安裝順序。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-171">Once completed, the Visual Studio Team Service deployment task honors the required files and the install sequence.</span></span> 

> [!TIP]
> <span data-ttu-id="ab0d3-172">如果您的專案後再製 git 中進行變更，您可以**階段**您的變更，然後**推送**，全部都在 Visual Studio 內。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-172">If you make changes to your project after you clone in git, you can **Stage** your changes, and then **Push**, all within Visual Studio.</span></span> 

## <a name="what-you-did"></a><span data-ttu-id="ab0d3-173">您的作法</span><span class="sxs-lookup"><span data-stu-id="ab0d3-173">What you did</span></span>

<span data-ttu-id="ab0d3-174">在 BizTalk 專案中，您可以加入的 BizTalk 應用程式專案 (.btaproj)。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-174">In your BizTalk project, you added a BizTalk Application project (.btaproj).</span></span> <span data-ttu-id="ab0d3-175">這個專案用來自動化使用 VSTS BizTalk Server 專案的部署。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-175">This project is used to automate deployments of your BizTalk Server projects using VSTS.</span></span> <span data-ttu-id="ab0d3-176">建立應用程式專案之後，您會加入到 BizTalk 應用程式專案的參考。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-176">After you created the application project, you added a reference to your BizTalk application project.</span></span> <span data-ttu-id="ab0d3-177">然後，您可以更新通知自動化的部署，哪些 Dll 部署，若要使用，哪一個繫結檔案，才能部署應用程式的 JSON 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab0d3-177">Then, you updated a JSON file that tells the automated deployment what DLLs to deploy, which binding file to use, and the order to deploy the applications.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="ab0d3-178">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="ab0d3-178">Next steps</span></span>
[<span data-ttu-id="ab0d3-179">步驟 2： 建立 VSTS 語彙基元</span><span class="sxs-lookup"><span data-stu-id="ab0d3-179">Step 2: Create the VSTS token</span></span>](feature-pack-create-vsts-token.md)  
[<span data-ttu-id="ab0d3-180">步驟 3： 建立組建和發行定義</span><span class="sxs-lookup"><span data-stu-id="ab0d3-180">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)  
[<span data-ttu-id="ab0d3-181">設定環境的語彙基元和變數</span><span class="sxs-lookup"><span data-stu-id="ab0d3-181">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)