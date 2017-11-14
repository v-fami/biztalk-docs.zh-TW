---
redirect_url: /biztalk/core/feature-pack-add-application-project/
redirect_document_id: True
ROBOTS: NOINDEX
title: "設定自動部署的 JSON 範本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 0b7755a6-5a5a-4a6b-8f99-ac12a5fbf3d4
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 10d85b625d759af675ecc1a38d540da8a304ba43
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="configure-the-json-template-for-automatic-deployment"></a><span data-ttu-id="71792-102">設定自動部署的 JSON 範本</span><span class="sxs-lookup"><span data-stu-id="71792-102">Configure the JSON template for automatic deployment</span></span>


<span data-ttu-id="71792-103">當您建置應用程式使用 Visual Studio Team Services 時，新的 BizTalk 專案檔會建立 – (.btaproj)。</span><span class="sxs-lookup"><span data-stu-id="71792-103">When you build your applications using Visual Studio Team Services, a new BizTalk project file is created – (.btaproj).</span></span> <span data-ttu-id="71792-104">這個新的專案會保存所有的 BizTalk 應用程式使用 VSTS 所建立。</span><span class="sxs-lookup"><span data-stu-id="71792-104">This new project holds all the BizTalk applications that you build using VSTS.</span></span> 

<span data-ttu-id="71792-105">您的專案包含`BizTalkServerInventory.json`檔案。</span><span class="sxs-lookup"><span data-stu-id="71792-105">Your project includes the `BizTalkServerInventory.json` file.</span></span> <span data-ttu-id="71792-106">在此檔案中，加入您的 BizTalk 組件、 將 BizTalk 應用程式的繫結檔案新增及設定的部署順序。</span><span class="sxs-lookup"><span data-stu-id="71792-106">In this file, add your BizTalk assemblies, add the binding files for your BizTalk application, and set a deployment sequence.</span></span> 

<span data-ttu-id="71792-107">本主題說明如何更新 json 檔案。</span><span class="sxs-lookup"><span data-stu-id="71792-107">This topic shows you how to update the json file.</span></span> 

## <a name="add-assemblies-binding-files-and-deployment-sequence"></a><span data-ttu-id="71792-108">加入組件、 繫結檔案和部署順序</span><span class="sxs-lookup"><span data-stu-id="71792-108">Add assemblies, binding files, and deployment sequence</span></span>

1. <span data-ttu-id="71792-109">開啟`BizTalkServerInventory.json`檔案中您**BizTalk Server 應用程式**專案 (.btaproj)。</span><span class="sxs-lookup"><span data-stu-id="71792-109">Open the `BizTalkServerInventory.json` file in your **BizTalk Server Application** project (.btaproj).</span></span>

2. <span data-ttu-id="71792-110">範本包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="71792-110">The template includes the following sections:</span></span> 

    | | |
    |---|---|
    |<span data-ttu-id="71792-111">BizTalkAssemblies</span><span class="sxs-lookup"><span data-stu-id="71792-111">BizTalkAssemblies</span></span> | <span data-ttu-id="71792-112">在應用程式中使用的組件</span><span class="sxs-lookup"><span data-stu-id="71792-112">The assemblies used in your applications</span></span> |
    |<span data-ttu-id="71792-113">BindingFiles</span><span class="sxs-lookup"><span data-stu-id="71792-113">BindingFiles</span></span> | <span data-ttu-id="71792-114">您所參考的繫結檔案</span><span class="sxs-lookup"><span data-stu-id="71792-114">The binding files you are referencing</span></span>|
    | <span data-ttu-id="71792-115">DeploymentSequence</span><span class="sxs-lookup"><span data-stu-id="71792-115">DeploymentSequence</span></span> | <span data-ttu-id="71792-116">若要安裝元素的順序</span><span class="sxs-lookup"><span data-stu-id="71792-116">The sequence for the elements to be installed</span></span>|
    
    <span data-ttu-id="71792-117">範例範本：</span><span class="sxs-lookup"><span data-stu-id="71792-117">Sample template:</span></span> 
    
    ![FP1 Json 範本映像 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > <span data-ttu-id="71792-119">根據您的方案的複雜度，您要在組建中的元素必須參考此 JSON 範本檔案中。</span><span class="sxs-lookup"><span data-stu-id="71792-119">Depending on the complexity of your solution, the elements you want in the build must be referenced in this JSON template file.</span></span>

3. <span data-ttu-id="71792-120">在`BizTalkAssemblies`，將您的 BizTalk 應用程式所使用的組件：</span><span class="sxs-lookup"><span data-stu-id="71792-120">In `BizTalkAssemblies`, add the assemblies used by your BizTalk applications:</span></span> 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName"
            "Path": "PathToAssembly
        }
    ]
    ```

4. <span data-ttu-id="71792-121">在`BindingsFiles`，新增您的 BizTalk 應用程式的繫結檔案：</span><span class="sxs-lookup"><span data-stu-id="71792-121">In `BindingsFiles`, add the binding files for your BizTalk applications:</span></span> 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name"
            "Path": "PathToBindingFile
        }
    ]
    ```

5. <span data-ttu-id="71792-122">在`DeploymentSequence`，部署並安裝在您想要的順序新增應用程式名稱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="71792-122">In `DeploymentSequence`, add the application names in the order you want them deployed and installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span></span> 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```
    
6. <span data-ttu-id="71792-123">**儲存**您的變更。</span><span class="sxs-lookup"><span data-stu-id="71792-123">**Save** your changes.</span></span> 

<span data-ttu-id="71792-124">完成後，Visual Studio Team 服務部署工作會接受所需的檔案和安裝順序。</span><span class="sxs-lookup"><span data-stu-id="71792-124">Once completed, the Visual Studio Team Service deployment task honors the required files and the install sequence.</span></span> 

## <a name="next-step"></a><span data-ttu-id="71792-125">下一步</span><span class="sxs-lookup"><span data-stu-id="71792-125">Next step</span></span>
<span data-ttu-id="71792-126">[設定語彙基元和變數](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md)繫結檔案部署至多個相同的 BizTalk 應用程式中[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]s。</span><span class="sxs-lookup"><span data-stu-id="71792-126">[Configure tokens and variables](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md) in your binding file to deploy the same BizTalk application to multiple [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]s.</span></span>

 