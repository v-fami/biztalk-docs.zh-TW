---
title: 建立環境的語彙基元 & 變數 |Microsoft 文件 」
description: 繫結檔案更新為使用環境語彙基元，並在 VSTS 來自動化部署的 BizTalk Server 應用程式中建立變數
ms.custom: ''
ms.date: 11/08/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 28bb2d4a-f45c-466d-ba65-0ca8cad0bffd
caps.latest.revision: 4
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d84fa393410e3084c87e762140530a45b0b78b5
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
ms.locfileid: "24054566"
---
# <a name="configure-environmental-tokens-and-variables-for-automatic-deployment"></a><span data-ttu-id="9268c-103">設定環境的語彙基元和自動部署的變數</span><span class="sxs-lookup"><span data-stu-id="9268c-103">Configure environmental tokens and variables for automatic deployment</span></span>
<span data-ttu-id="9268c-104">使用 Visual Studio Team Services (VSTS) 變數，在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="9268c-104">Use Visual Studio Team Services (VSTS) variables in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] binding files.</span></span>

## <a name="overview"></a><span data-ttu-id="9268c-105">概觀</span><span class="sxs-lookup"><span data-stu-id="9268c-105">Overview</span></span>
<span data-ttu-id="9268c-106">在 VSTS 環境中，您可以加入變數，並設為值。</span><span class="sxs-lookup"><span data-stu-id="9268c-106">In a VSTS environment, you can add variables, and set them to a value.</span></span> <span data-ttu-id="9268c-107">例如，您可以建立*sendPortPath*變數，並將其值設定在實體資料夾您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9268c-107">For example, you can create a *sendPortPath* variable, and set its value to a physical folder on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

<span data-ttu-id="9268c-108">內[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]應用程式繫結檔案，可設定的變數可以是任何項目內的 XML 標記，例如接收位置名稱、 主機、 傳送埠的 URI，等等。</span><span class="sxs-lookup"><span data-stu-id="9268c-108">Within the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] application binding file, the configurable variables can be anything within an XML tag, such as the receive location name, host, send port URI, and so on.</span></span> 

<span data-ttu-id="9268c-109">這些變數專屬於您 VSTS 的環境，而且可用來部署至多個相同的應用程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="9268c-109">These variables are specific to your VSTS environment, and can be used to deploy the same application to multiple [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments.</span></span> 

<span data-ttu-id="9268c-110">我們會示範如何加入 VSTS 變數在繫結檔案中，以及如何建立在 VSTS 中的變數。</span><span class="sxs-lookup"><span data-stu-id="9268c-110">We show you how to add the VSTS variable in your binding file, and how to create the variable within VSTS.</span></span> 

## <a name="add-variables-to-the-binding-file"></a><span data-ttu-id="9268c-111">將變數加入至繫結檔案</span><span class="sxs-lookup"><span data-stu-id="9268c-111">Add variables to the binding file</span></span>

1. <span data-ttu-id="9268c-112">開啟應用程式繫結檔案：</span><span class="sxs-lookup"><span data-stu-id="9268c-112">Open the application binding file:</span></span>

    ![開啟 繫結檔案](../core/media/biztalk-feature-pack-1-binding-1.png)

2. <span data-ttu-id="9268c-114">尋找您想要變更的項目：</span><span class="sxs-lookup"><span data-stu-id="9268c-114">Find the element you want to change:</span></span>

    ![選取的項目](../core/media/biztalk-feature-pack-1-binding-2.png)
    
3. <span data-ttu-id="9268c-116">移除填入的值，以取代您變數： `$(YourValue)`。</span><span class="sxs-lookup"><span data-stu-id="9268c-116">Remove the populated value, and replace it with you variables: `$(YourValue)`.</span></span> <span data-ttu-id="9268c-117">例如，輸入`$(SendPort1)`:</span><span class="sxs-lookup"><span data-stu-id="9268c-117">For example, enter `$(SendPort1)`:</span></span> 

    ![繫結檔案](../core/media/biztalk-feature-pack-1-binding-3.png)

4. <span data-ttu-id="9268c-119">完成時，儲存繫結檔案，並將它加入至您的 JSON 建置範本 (步驟[步驟 1： 新增應用程式專案 （& s） 更新.json 範本](feature-pack-add-application-project.md))。</span><span class="sxs-lookup"><span data-stu-id="9268c-119">When done, save the binding file, and add it to your JSON build template (steps in [Step 1: Add Application project & update .json template](feature-pack-add-application-project.md)).</span></span>

## <a name="create-the-variables-in-vsts"></a><span data-ttu-id="9268c-120">建立於 VSTS 中的變數</span><span class="sxs-lookup"><span data-stu-id="9268c-120">Create the variables in VSTS</span></span>

1. <span data-ttu-id="9268c-121">VSTS 帳戶中，選取**組建與版本**，然後選取**版本**。</span><span class="sxs-lookup"><span data-stu-id="9268c-121">In your VSTS account, select **Build and release**, and select **Releases**.</span></span>

2. <span data-ttu-id="9268c-122">選取您**發行定義**，然後選取**變數**:</span><span class="sxs-lookup"><span data-stu-id="9268c-122">Select your **Release definition**, and select **Variables**:</span></span>  

    ![繫結檔案](../core/media/vsts-release-variables.png)

3. <span data-ttu-id="9268c-124">選取**新增**，並建立的變數名稱和值：</span><span class="sxs-lookup"><span data-stu-id="9268c-124">Select **Add**, and create the variable names and values:</span></span>   

    ![設定變數](../core/media/environment-specific-variables.png)

4. <span data-ttu-id="9268c-126">**儲存**您的變更。</span><span class="sxs-lookup"><span data-stu-id="9268c-126">**Save** your changes.</span></span> <span data-ttu-id="9268c-127">起始部署時，這些值會加入從繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="9268c-127">When the deploy is initiated, the values are added from the binding file.</span></span>

## <a name="see-also"></a><span data-ttu-id="9268c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9268c-128">See also</span></span>
[<span data-ttu-id="9268c-129">使用 Visual Studio Team Services 中設定自動部署</span><span class="sxs-lookup"><span data-stu-id="9268c-129">Configure automatic deployment with Visual Studio Team Services</span></span>](configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  
[<span data-ttu-id="9268c-130">設定 Feature Pack</span><span class="sxs-lookup"><span data-stu-id="9268c-130">Configure the feature pack</span></span>](configure-the-feature-pack.md)