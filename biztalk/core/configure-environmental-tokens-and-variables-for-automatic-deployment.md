---
title: "設定環境的語彙基元和自動部署的變數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 28bb2d4a-f45c-466d-ba65-0ca8cad0bffd
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 7d148f79fceb68b24feb45882ab89767369ed7e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-environmental-tokens-and-variables-for-automatic-deployment"></a><span data-ttu-id="ba69d-102">設定環境的語彙基元和自動部署的變數</span><span class="sxs-lookup"><span data-stu-id="ba69d-102">Configure environmental tokens and variables for automatic deployment</span></span>
<span data-ttu-id="ba69d-103">使用 Visual Studio Team Services (VSTS) 變數，在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="ba69d-103">Use Visual Studio Team Services (VSTS) variables in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] binding files.</span></span>

## <a name="overview"></a><span data-ttu-id="ba69d-104">概觀</span><span class="sxs-lookup"><span data-stu-id="ba69d-104">Overview</span></span>
<span data-ttu-id="ba69d-105">在 VSTS 環境中，您可以加入變數，並設為值。</span><span class="sxs-lookup"><span data-stu-id="ba69d-105">In a VSTS environment, you can add variables, and set them to a value.</span></span> <span data-ttu-id="ba69d-106">例如，您可以建立*sendPortPath*變數，並將其值設定在實體資料夾您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ba69d-106">For example, you can create a *sendPortPath* variable, and set its value to a physical folder on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

<span data-ttu-id="ba69d-107">內[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]應用程式繫結檔案，可設定的變數可以是任何項目內的 XML 標記，例如接收位置名稱、 主機、 傳送埠的 URI，等等。</span><span class="sxs-lookup"><span data-stu-id="ba69d-107">Within the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] application binding file, the configurable variables can be anything within an XML tag, such as the receive location name, host, send port URI, and so on.</span></span> 

<span data-ttu-id="ba69d-108">這些變數專屬於您 VSTS 的環境，而且可用來部署至多個相同的應用程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="ba69d-108">These variables are specific to your VSTS environment, and can be used to deploy the same application to multiple [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments.</span></span> 

<span data-ttu-id="ba69d-109">在本主題中，我們會示範如何新增 VSTS 中的變數繫結檔案，以及如何建立在 VSTS 中的變數。</span><span class="sxs-lookup"><span data-stu-id="ba69d-109">In this topic, we show you how add the VSTS variable in your binding file, and how to create the variable within VSTS.</span></span> 

## <a name="configure-the-variables-in-your-biztalk-binding-file"></a><span data-ttu-id="ba69d-110">BizTalk 繫結檔案中設定的變數</span><span class="sxs-lookup"><span data-stu-id="ba69d-110">Configure the variables in your BizTalk Binding file</span></span>

<span data-ttu-id="ba69d-111">下列範例是屬於[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]繫結檔案，並示範如何套用語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ba69d-111">The following example is a part of a [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] binding file, and shows how to apply the tokens.</span></span>

1. <span data-ttu-id="ba69d-112">開啟應用程式繫結檔案：</span><span class="sxs-lookup"><span data-stu-id="ba69d-112">Open the application binding file:</span></span>

    ![BizTalk Feature Pack 1 繫結 1](../core/media/biztalk-feature-pack-1-binding-1.png)

2. <span data-ttu-id="ba69d-114">尋找您想要變更的項目：</span><span class="sxs-lookup"><span data-stu-id="ba69d-114">Find the element you want to change:</span></span>

    ![BizTalk Feature Pack 2 的繫結的 1](../core/media/biztalk-feature-pack-1-binding-2.png)
    
3. <span data-ttu-id="ba69d-116">移除填入的值，以取代您變數： `$(YourValue)`。</span><span class="sxs-lookup"><span data-stu-id="ba69d-116">Remove the populated value, and replace it with you variables: `$(YourValue)`.</span></span> <span data-ttu-id="ba69d-117">例如，輸入`$(SendPort1)`:</span><span class="sxs-lookup"><span data-stu-id="ba69d-117">For example, enter `$(SendPort1)`:</span></span> 

    ![BizTalk Feature Pack 1 繫結 3](../core/media/biztalk-feature-pack-1-binding-3.png)


4. <span data-ttu-id="ba69d-119">完成時，儲存繫結檔案，並將它套用到您的 JSON 建置範本。</span><span class="sxs-lookup"><span data-stu-id="ba69d-119">When done, save the binding file, and apply it to your JSON build template.</span></span>
5. <span data-ttu-id="ba69d-120">登入至 Visual Studio Team 服務方案，並選取**組建與版本**。</span><span class="sxs-lookup"><span data-stu-id="ba69d-120">Sign in to your Visual Studio Team Service solution, and select **Build and release**.</span></span>
6. <span data-ttu-id="ba69d-121">移至**發行**。</span><span class="sxs-lookup"><span data-stu-id="ba69d-121">Go to **Release**.</span></span> <span data-ttu-id="ba69d-122">選取您**發行定義**，或建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="ba69d-122">Select your **Release definition**, or create a new one.</span></span>
7. <span data-ttu-id="ba69d-123">在下**環境**，選取**加入新的環境**，或變更現有的環境：</span><span class="sxs-lookup"><span data-stu-id="ba69d-123">Under **Environments**, select **Add a new environment**, or change to an existing environment:</span></span> 

    ![加入新的環境](../core/media/add-a-new-environment.png)

8. <span data-ttu-id="ba69d-125">按一下省略符號，然後選取**設定變數**:</span><span class="sxs-lookup"><span data-stu-id="ba69d-125">Click the ellipses, and select **configure variables**:</span></span>

    ![設定變數](../core/media/configure-variables.png)

9. <span data-ttu-id="ba69d-127">藉由新增每個環境中，使用繫結檔中建立的語彙基元名稱的變數中，您可以部署至具有不同值的多個環境的應用程式：</span><span class="sxs-lookup"><span data-stu-id="ba69d-127">By adding the variables for each environment, using the token names created in the binding file, you can deploy your applications to multiple environments with different values:</span></span>

    ![環境特定變數](../core/media/environment-specific-variables.png)
    
10. <span data-ttu-id="ba69d-129">選取**確定**儲存新變數。</span><span class="sxs-lookup"><span data-stu-id="ba69d-129">Select **OK** to save the new variables.</span></span>
11. <span data-ttu-id="ba69d-130">一旦起始組建時，這些值會加入從繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="ba69d-130">Once the build is initiated, the values are added from binding file.</span></span>

## <a name="next-step"></a><span data-ttu-id="ba69d-131">下一步</span><span class="sxs-lookup"><span data-stu-id="ba69d-131">Next step</span></span>
[<span data-ttu-id="ba69d-132">加入 VSTS BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="ba69d-132">Add a BizTalk application to VSTS</span></span>](../core/add-a-biztalk-server-application-to-visual-studio-team-services.md)