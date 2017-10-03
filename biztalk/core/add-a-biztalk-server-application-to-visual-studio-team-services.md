---
title: "加入 Visual Studio Team Services 的 BizTalk Server 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2c7a1ff-0f26-45f3-9a9b-4c99a67b51a9
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: d3fc8c0253c8e2517f78c2d60fdc7c74a983bdbd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="add-a-biztalk-server-application-to-visual-studio-team-services"></a><span data-ttu-id="3b84e-102">加入 Visual Studio Team Services 的 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="3b84e-102">Add a BizTalk Server application to Visual Studio Team Services</span></span>
<span data-ttu-id="3b84e-103">新增[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]VSTS 自動部署使用持續整合至專案。</span><span class="sxs-lookup"><span data-stu-id="3b84e-103">Add a [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] project to VSTS to automatically deploy using continuous integration.</span></span>  

<span data-ttu-id="3b84e-104">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可自動部署應用程式，以便您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]使用 Visual Studio Team Services (VSTS) 的環境。</span><span class="sxs-lookup"><span data-stu-id="3b84e-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can automatically deploy your applications to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments using Visual Studio Team Services (VSTS).</span></span> 

<span data-ttu-id="3b84e-105">本主題提供概觀，並列出部署從 Visual Studio 方案的重要步驟您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3b84e-105">This topics provides an overview, and lists the key steps to deploy your solution from Visual Studio to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="3b84e-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="3b84e-106">Prerequisites</span></span>
* <span data-ttu-id="3b84e-107">安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b84e-107">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* [<span data-ttu-id="3b84e-108">VSTS 設定用於自動部署</span><span class="sxs-lookup"><span data-stu-id="3b84e-108">Configure VSTS for automatic deployment</span></span>](../core/configure-visual-studio-team-services-to-deploy-biztalk-solutions-or-projects.md)
* <span data-ttu-id="3b84e-109">知識和經驗使用 Git 和 Visual Studio 中的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="3b84e-109">Knowledge and experience working with Git and repositories in Visual Studio.</span></span> <span data-ttu-id="3b84e-110">如果您是新手儲存機制和版本控制，這些可能是很好的資源：</span><span class="sxs-lookup"><span data-stu-id="3b84e-110">If you're brand new to repositories and version control, these may be good resources:</span></span> 

    [<span data-ttu-id="3b84e-111">了解 Git</span><span class="sxs-lookup"><span data-stu-id="3b84e-111">Learn Git</span></span>](https://www.visualstudio.com/learn-git/)  
    [<span data-ttu-id="3b84e-112">Git 和 Team Services</span><span class="sxs-lookup"><span data-stu-id="3b84e-112">Git and Team Services</span></span>](https://www.visualstudio.com/docs/git/overview)
* <span data-ttu-id="3b84e-113">知識和經驗的使用中的 BizTalk 專案[!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b84e-113">Knowledge and experience working with BizTalk projects in [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]</span></span>

## <a name="add-biztalk-project-to-vsts"></a><span data-ttu-id="3b84e-114">將 BizTalk 專案加入至 VSTS</span><span class="sxs-lookup"><span data-stu-id="3b84e-114">Add BizTalk project to VSTS</span></span>
1. <span data-ttu-id="3b84e-115">在**Visual Studio**，連接到您**來源儲存機制**，和**複製**以您的電腦。</span><span class="sxs-lookup"><span data-stu-id="3b84e-115">In **Visual Studio**, connect to your **Source repository**, and **Clone** it to your machine.</span></span>
2. <span data-ttu-id="3b84e-116">開啟或建立**BizTalk 專案**(.btproj)。</span><span class="sxs-lookup"><span data-stu-id="3b84e-116">Open or Create a **BizTalk Project** (.btproj).</span></span>

   > [!NOTE]
   > <span data-ttu-id="3b84e-117">您可以將多個專案新增至相同的方案。</span><span class="sxs-lookup"><span data-stu-id="3b84e-117">You can add multiple project into the same solution.</span></span>
   
3. <span data-ttu-id="3b84e-118">加入新**BizTalk Server 應用程式專案**(.btaproj)。</span><span class="sxs-lookup"><span data-stu-id="3b84e-118">Add a new **BizTalk Server Application Project** (.btaproj).</span></span>
4. <span data-ttu-id="3b84e-119">中的專案上按一下滑鼠右鍵**方案總管 中**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3b84e-119">Right-click the project in the **Solution Explorer**, and select **Properties**.</span></span>
5. <span data-ttu-id="3b84e-120">設定**版本**和連接屬性，以您**Visual Studio Team Services**帳戶。</span><span class="sxs-lookup"><span data-stu-id="3b84e-120">Configure the **Version** and the connection properties to your **Visual Studio Team Services** account.</span></span>

    ![Visual Studio 組態 FP1 BizTalk](../core/media/visual-studio-configuration-fp1-biztalk.png)

6. <span data-ttu-id="3b84e-122">新增所有組件和應用程式所需的成品。</span><span class="sxs-lookup"><span data-stu-id="3b84e-122">Add all the assemblies and artifacts needed by your application.</span></span>
7. <span data-ttu-id="3b84e-123">更新**binding.xml**具有正確的繫結資訊檔案。</span><span class="sxs-lookup"><span data-stu-id="3b84e-123">Update the **binding.xml** file with the correct binding information.</span></span>
8. <span data-ttu-id="3b84e-124">更新**BizTalkServerInventory.json**成品安裝在正確的順序與所有的成品， [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3b84e-124">Update the **BizTalkServerInventory.json** with all the artifacts, and the correct order for the artifacts to be installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>
9. <span data-ttu-id="3b84e-125">以滑鼠右鍵按一下和**建置**方案中，以便檢查是否有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="3b84e-125">Right-click and **build** your solution to check for any errors.</span></span> 
10. <span data-ttu-id="3b84e-126">建置成功完成時，以滑鼠右鍵按一下您的方案，然後選取**部署**。</span><span class="sxs-lookup"><span data-stu-id="3b84e-126">When the build completes successfully, right-click your solution, and select **Deploy**.</span></span>
11. <span data-ttu-id="3b84e-127">您的應用程式應該自動部署到您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3b84e-127">Your application should automatically deploy to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="3b84e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b84e-128">See also</span></span>
[<span data-ttu-id="3b84e-129">設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="3b84e-129">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)