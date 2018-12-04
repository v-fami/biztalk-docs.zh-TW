---
title: 步驟 1-新增應用程式專案，並更新 json |Microsoft Docs
description: 在 Visual Studio 中，將 BizTalk Server 應用程式專案，並使用 Dll、 繫結檔案和應用程式-Visual Studio Team Services 的部署順序更新 BizTalkServerInventory.json 檔
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
ms.openlocfilehash: e0230d0b280be412e3138ffbafd83d3810cf1163
ms.sourcegitcommit: be6273d612669adfbb9dc9208aaae0a8437d4017
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52826358"
---
# <a name="step-1-add-the-biztalk-server-application-project-in-visual-studio"></a><span data-ttu-id="335e3-103">步驟 1： 在 Visual Studio 中將 BizTalk Server 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="335e3-103">Step 1: Add the BizTalk Server Application project in Visual Studio</span></span>

<span data-ttu-id="335e3-104">當您建置使用 Visual Studio Team Services 的應用程式時，新的 BizTalk 專案檔會建立 –.btaproj。</span><span class="sxs-lookup"><span data-stu-id="335e3-104">When you build your applications using Visual Studio Team Services, a new BizTalk project file is created – .btaproj.</span></span> <span data-ttu-id="335e3-105">這個新的專案會保存所有的 BizTalk 應用程式，您建置及部署使用 VSTS 建置及發行版本功能。</span><span class="sxs-lookup"><span data-stu-id="335e3-105">This new project holds all the BizTalk applications that you build and deploy using the VSTS build and release features.</span></span> 

<span data-ttu-id="335e3-106">BizTalk 應用程式專案包含`BizTalkServerInventory.json`檔案。</span><span class="sxs-lookup"><span data-stu-id="335e3-106">The BizTalk Application Project includes the `BizTalkServerInventory.json` file.</span></span> <span data-ttu-id="335e3-107">在此檔案中，新增您的 BizTalk 組件，加入您的 BizTalk 應用程式的繫結檔案，然後設定部署序列。</span><span class="sxs-lookup"><span data-stu-id="335e3-107">In this file, add your BizTalk assemblies, add the binding files for your BizTalk application, and then set a deployment sequence.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="335e3-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="335e3-108">Before you begin</span></span>

* <span data-ttu-id="335e3-109">這些步驟假設您有現有的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="335e3-109">These steps assume you have an existing BizTalk project.</span></span> <span data-ttu-id="335e3-110">如果沒有，您可以使用 HelloWorld SDK > 範例 (BizTalk Server 的 \Program 檔案 (x86) \Microsoft *yourVersion*\SDK\Samples\Orchestrations\HelloWorld)。</span><span class="sxs-lookup"><span data-stu-id="335e3-110">If not, you can use the HelloWorld SDK sample (\Program Files (x86)\Microsoft BizTalk Server *yourVersion*\SDK\Samples\Orchestrations\HelloWorld).</span></span> 
* <span data-ttu-id="335e3-111">具有您準備好的 BizTalk 專案之 XML 繫結檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="335e3-111">Have the path to the XML binding file to your BizTalk project ready.</span></span> 
* <span data-ttu-id="335e3-112">瞭解您的 VSTS 帳戶，您的集合，以及您的 team 專案詳細資料。</span><span class="sxs-lookup"><span data-stu-id="335e3-112">Know your VSTS account, your collection, and your team project details.</span></span>
* <span data-ttu-id="335e3-113">要熟悉 git 概念，包括複製和使用存放庫。</span><span class="sxs-lookup"><span data-stu-id="335e3-113">Be familiar with git concepts, including cloning and working with repositories.</span></span> 
* <span data-ttu-id="335e3-114">請務必[Feature Pack 2](https://aka.ms/bts2016fp2)安裝。</span><span class="sxs-lookup"><span data-stu-id="335e3-114">Be sure [Feature Pack 2](https://aka.ms/bts2016fp2) is installed.</span></span>

## <a name="add-the-application-project"></a><span data-ttu-id="335e3-115">新增應用程式專案</span><span class="sxs-lookup"><span data-stu-id="335e3-115">Add the application project</span></span>

1. <span data-ttu-id="335e3-116">在 BizTalk 伺服器上，請在 Visual Studio 中開啟方案 (ProjectName.sln)。</span><span class="sxs-lookup"><span data-stu-id="335e3-116">On the BizTalk Server, open your solution (ProjectName.sln) in Visual Studio.</span></span> <span data-ttu-id="335e3-117">請勿選取 Visual Studio 的 Blend。</span><span class="sxs-lookup"><span data-stu-id="335e3-117">Do not select Visual Studio Blend.</span></span>

2. <span data-ttu-id="335e3-118">在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取**建置**。</span><span class="sxs-lookup"><span data-stu-id="335e3-118">In solution explorer, right-click your project, and select **Build**.</span></span> <span data-ttu-id="335e3-119">請確定您的組建成功。</span><span class="sxs-lookup"><span data-stu-id="335e3-119">Be sure your build succeeds.</span></span> <span data-ttu-id="335e3-120">以滑鼠右鍵按一下您的專案，然後選取**部署**。</span><span class="sxs-lookup"><span data-stu-id="335e3-120">Right-click your project, and select **Deploy**.</span></span> <span data-ttu-id="335e3-121">請確定您的部署成功。</span><span class="sxs-lookup"><span data-stu-id="335e3-121">Be sure your deploy succeeds.</span></span>

3. <span data-ttu-id="335e3-122">以滑鼠右鍵按一下您的解決方案，請選取**新增**，然後選取**加入新的專案**。</span><span class="sxs-lookup"><span data-stu-id="335e3-122">Right-click your solution, select **Add**, and select **Add New Project**.</span></span>

4. <span data-ttu-id="335e3-123">選取  **BizTalk 專案**索引標籤上，選取 **.NET Framework 4.6.1**從下拉式清單選取**BizTalk Server 應用程式專案**。</span><span class="sxs-lookup"><span data-stu-id="335e3-123">Select the **BizTalk Projects** tab, select **.NET Framework 4.6.1** from the drop-down list, and select **BizTalk Server Application Project**.</span></span> <span data-ttu-id="335e3-124">輸入名稱 (例如 appProjectHelloWorld)，然後選取**確定**:</span><span class="sxs-lookup"><span data-stu-id="335e3-124">Enter a name (e.g. appProjectHelloWorld), and select **OK**:</span></span>  

    ![新增應用程式專案](../core/media/add-application-project.png)

5. <span data-ttu-id="335e3-126">在 [方案總管] 中，以滑鼠右鍵按一下您剛新增的應用程式的專案 (.btaproj) 中，選取**新增**，選取**參考**。</span><span class="sxs-lookup"><span data-stu-id="335e3-126">In Solution Explorer, right-click your newly-added application project (.btaproj), select **Add**, select **Reference**.</span></span> <span data-ttu-id="335e3-127">依序展開**專案**索引標籤，然後檢查您的 BizTalk 專案 （您要部署使用 VSTS 專案）。</span><span class="sxs-lookup"><span data-stu-id="335e3-127">Expand the **Projects** tab, and check your BizTalk project (the project you are deploying using VSTS).</span></span> <span data-ttu-id="335e3-128">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="335e3-128">Select **OK**.</span></span>  
    <span data-ttu-id="335e3-129">新增之後，依序展開**參考**在您的應用程式專案 (例如 appProjectHelloWorld)，以查看 BizTalk 專案下您剛才加入。</span><span class="sxs-lookup"><span data-stu-id="335e3-129">Once added, expand **References** under your application project (e.g. appProjectHelloWorld) to see the BizTalk project you just added.</span></span> 

6. <span data-ttu-id="335e3-130">在 [方案總管] 中，以滑鼠右鍵按一下您的應用程式專案 (.btaproj) 中，選取**新增**，選取**現有項目**，並**新增**您繫結的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="335e3-130">In Solution Explorer, right-click your application project (.btaproj), select **Add**, select **Existing Item**, and **Add** your binding XML file.</span></span>

7. <span data-ttu-id="335e3-131">開啟的 binding.xml，屬性並將**複製到輸出目錄**要**永遠複製**。</span><span class="sxs-lookup"><span data-stu-id="335e3-131">Open the properties of binding.xml, and set **Copy to Output Directory** to **Copy always**.</span></span> <span data-ttu-id="335e3-132">**儲存**您的變更：</span><span class="sxs-lookup"><span data-stu-id="335e3-132">**Save** your changes:</span></span>  

    ![繫結檔案屬性](../core/media/xml-binding-file-properties.png)

8. <span data-ttu-id="335e3-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="335e3-134">Optional.</span></span> <span data-ttu-id="335e3-135">以滑鼠右鍵按一下 新增應用程式專案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="335e3-135">Right-click your newly-added application project, and select **Properties**.</span></span> <span data-ttu-id="335e3-136">來自訂**應用程式名稱**您想要顯示在 BizTalk 管理中：</span><span class="sxs-lookup"><span data-stu-id="335e3-136">Customize the **Application Name** you want displayed in BizTalk Administration:</span></span>  

    ![應用程式名稱](../core/media/application-project-name.png)

## <a name="configure-the-json-template"></a><span data-ttu-id="335e3-138">設定 JSON 範本</span><span class="sxs-lookup"><span data-stu-id="335e3-138">Configure the JSON template</span></span>

1. <span data-ttu-id="335e3-139">在 Visual Studio 中，在您的應用程式專案 (.btaproj)，開啟`BizTalkServerInventory.json`檔案。</span><span class="sxs-lookup"><span data-stu-id="335e3-139">In Visual Studio, in your application project (.btaproj), open the `BizTalkServerInventory.json` file.</span></span> 

2. <span data-ttu-id="335e3-140">範本包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="335e3-140">The template includes the following sections:</span></span> 

    | | |
    |---|---|
    |<span data-ttu-id="335e3-141">BizTalkAssemblies</span><span class="sxs-lookup"><span data-stu-id="335e3-141">BizTalkAssemblies</span></span> | <span data-ttu-id="335e3-142">在您的應用程式中使用的組件</span><span class="sxs-lookup"><span data-stu-id="335e3-142">The assemblies used in your applications</span></span> |
    |<span data-ttu-id="335e3-143">BindingFiles</span><span class="sxs-lookup"><span data-stu-id="335e3-143">BindingFiles</span></span> | <span data-ttu-id="335e3-144">您所參考的繫結檔案</span><span class="sxs-lookup"><span data-stu-id="335e3-144">The binding files you are referencing</span></span>|
    |<span data-ttu-id="335e3-145">DeploymentSequence</span><span class="sxs-lookup"><span data-stu-id="335e3-145">DeploymentSequence</span></span> | <span data-ttu-id="335e3-146">若要安裝之項目的序列</span><span class="sxs-lookup"><span data-stu-id="335e3-146">The sequence for the elements to be installed</span></span>|
    
    <span data-ttu-id="335e3-147">範例範本：</span><span class="sxs-lookup"><span data-stu-id="335e3-147">Sample template:</span></span> 
    
    ![FP1 Json 範本映像 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > <span data-ttu-id="335e3-149">根據您的解決方案的複雜度，您要在組建中的元素必須參考此 JSON 範本檔案中。</span><span class="sxs-lookup"><span data-stu-id="335e3-149">Depending on the complexity of your solution, the elements you want in the build must be referenced in this JSON template file.</span></span>

3. <span data-ttu-id="335e3-150">在  `BizTalkAssemblies`，新增 BizTalk 專案所使用的組件：</span><span class="sxs-lookup"><span data-stu-id="335e3-150">In `BizTalkAssemblies`, add the assemblies used by your BizTalk project:</span></span> 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName",
            "Path": "PathToAssembly
        }
    ]
    ```

4. <span data-ttu-id="335e3-151">在  `BindingsFiles`，新增您的 BizTalk 專案的繫結檔案：</span><span class="sxs-lookup"><span data-stu-id="335e3-151">In `BindingsFiles`, add the binding files for your BizTalk project:</span></span> 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name",
            "Path": "PathToBindingFile
        }
    ]
    ```

5. <span data-ttu-id="335e3-152">在  `DeploymentSequence`，這些部署，以及安裝在您想要的順序中新增的應用程式名稱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="335e3-152">In `DeploymentSequence`, add the application names in the order you want them deployed, and installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span></span> 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```


6. <span data-ttu-id="335e3-153">**儲存**您的變更。</span><span class="sxs-lookup"><span data-stu-id="335e3-153">**Save** your changes.</span></span> <span data-ttu-id="335e3-154">完成時，您的.json 檔案看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="335e3-154">When finished, your .json file looks like the following:</span></span> 

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

7. <span data-ttu-id="335e3-155">**選擇性**。</span><span class="sxs-lookup"><span data-stu-id="335e3-155">**Optional**.</span></span> <span data-ttu-id="335e3-156">以滑鼠右鍵按一下您的應用程式專案 (例如 appProjectHelloWorld)，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="335e3-156">Right-click your application project (e.g. appProjectHelloWorld), and select **Properties**.</span></span> <span data-ttu-id="335e3-157">您可以設定偵錯或發行版本，為新值。</span><span class="sxs-lookup"><span data-stu-id="335e3-157">You can set the Debug or Release version to a new value.</span></span> <span data-ttu-id="335e3-158">我們不在這些步驟中，但請留意執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="335e3-158">We don’t in these steps, but be aware you can do this.</span></span>  

    ![設定偵錯或發行版本](../core/media/application-project-version.png)

8. <span data-ttu-id="335e3-160">以滑鼠右鍵按一下您的應用程式專案 (例如 appProjectHelloWorld)，然後選取**建置**。</span><span class="sxs-lookup"><span data-stu-id="335e3-160">Right-click your application project (e.g. appProjectHelloWorld), and select **Build**.</span></span> <span data-ttu-id="335e3-161">如果成功，在中建立的 zip 檔案 **_yourApplicationProject_\bin\debug**資料夾：</span><span class="sxs-lookup"><span data-stu-id="335e3-161">If it succeeds, a zip file is created in **_yourApplicationProject_\bin\debug** folder:</span></span>  

    ![建立 zip 檔案](../core/media/application-project-zip-file.png)

9. <span data-ttu-id="335e3-163">選取您的方案，然後選取**Team Explorer**  索引標籤。在 VSTS 中，選取**Connect**。</span><span class="sxs-lookup"><span data-stu-id="335e3-163">Select your solution, and select the **Team Explorer** tab. Under VSTS, select **Connect**.</span></span>  

    ![連接至 Team Services](../core/media/connect-team-services.png)

10. <span data-ttu-id="335e3-165">選取您的 VSTS 帳戶，您的集合和您的 team 專案。</span><span class="sxs-lookup"><span data-stu-id="335e3-165">Select your VSTS account, your collection, and your team project.</span></span> <span data-ttu-id="335e3-166">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="335e3-166">Select **OK**.</span></span> <span data-ttu-id="335e3-167">如果您尚未建立 VSTS 帳戶，然後建立一個 ([步驟 2： 建立 VSTS 權杖](feature-pack-create-vsts-token.md)提供一些指引)。</span><span class="sxs-lookup"><span data-stu-id="335e3-167">If you didn’t create a VSTS account yet, then create one ([Step 2: Create the VSTS token](feature-pack-create-vsts-token.md) provides some guidance).</span></span> <span data-ttu-id="335e3-168">一旦建立之後，返回此步驟中，並連接。</span><span class="sxs-lookup"><span data-stu-id="335e3-168">Once it's created, come back to this step, and connect.</span></span>  

    ![選取您的集合和專案](../core/media/team-collections-projects.png)

11. <span data-ttu-id="335e3-170">當您連線時，您可能會收到提示，要複製這個存放庫。</span><span class="sxs-lookup"><span data-stu-id="335e3-170">When you connect, you may get a prompt to clone this repository.</span></span> <span data-ttu-id="335e3-171">選取 **複製這個存放庫**連結。</span><span class="sxs-lookup"><span data-stu-id="335e3-171">Select the **Clone this repository** link.</span></span>  

    ![複製存放庫](../core/media/vsts-clone-repository.png)

12. <span data-ttu-id="335e3-173">請注意 URL 和路徑，然後選取**複製品**:</span><span class="sxs-lookup"><span data-stu-id="335e3-173">Note the URL and paths, and select **Clone**:</span></span>  

    ![存放庫路徑](../core/media/clone-repo-paths.png)

<span data-ttu-id="335e3-175">完成後，Visual Studio Team Service 部署工作會接受所需的檔案和安裝順序。</span><span class="sxs-lookup"><span data-stu-id="335e3-175">Once completed, the Visual Studio Team Service deployment task honors the required files and the install sequence.</span></span> 

> [!TIP]
> <span data-ttu-id="335e3-176">如果您的專案之後您複製在 git 中進行變更，您可以**階段**您的變更，然後**推送**，全部都在 Visual Studio 內。</span><span class="sxs-lookup"><span data-stu-id="335e3-176">If you make changes to your project after you clone in git, you can **Stage** your changes, and then **Push**, all within Visual Studio.</span></span> 

## <a name="what-you-did"></a><span data-ttu-id="335e3-177">您的作法</span><span class="sxs-lookup"><span data-stu-id="335e3-177">What you did</span></span>

<span data-ttu-id="335e3-178">在 BizTalk 專案中，您可以新增 BizTalk 應用程式專案 (.btaproj)。</span><span class="sxs-lookup"><span data-stu-id="335e3-178">In your BizTalk project, you added a BizTalk Application project (.btaproj).</span></span> <span data-ttu-id="335e3-179">此專案用來將您使用 VSTS 的 BizTalk Server 專案的部署自動化。</span><span class="sxs-lookup"><span data-stu-id="335e3-179">This project is used to automate deployments of your BizTalk Server projects using VSTS.</span></span> <span data-ttu-id="335e3-180">建立應用程式專案之後，您會新增至您的 BizTalk 專案的參考。</span><span class="sxs-lookup"><span data-stu-id="335e3-180">After you created the application project, you added a reference to your BizTalk project.</span></span> <span data-ttu-id="335e3-181">然後，您可以更新告知自動化的部署哪些 Dll，若要部署，若要使用，哪一個繫結檔案，才能部署應用程式的 JSON 檔案。</span><span class="sxs-lookup"><span data-stu-id="335e3-181">Then, you updated a JSON file that tells the automated deployment what DLLs to deploy, which binding file to use, and the order to deploy the applications.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="335e3-182">後續步驟</span><span class="sxs-lookup"><span data-stu-id="335e3-182">Next steps</span></span>
[<span data-ttu-id="335e3-183">步驟 2： 建立 VSTS 權杖</span><span class="sxs-lookup"><span data-stu-id="335e3-183">Step 2: Create the VSTS token</span></span>](feature-pack-create-vsts-token.md)  
[<span data-ttu-id="335e3-184">步驟 3： 建立組建和發行定義</span><span class="sxs-lookup"><span data-stu-id="335e3-184">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)  
[<span data-ttu-id="335e3-185">設定環境權杖和變數</span><span class="sxs-lookup"><span data-stu-id="335e3-185">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)
