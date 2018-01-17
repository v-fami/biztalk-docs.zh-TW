---
title: "使用 Visual Studio Team Services 中設定自動部署 |Microsoft 文件"
description: "安裝 BizTalk 功能套件部署至不同的 BizTalk 環境的應用程式中使用 VSTS 應用程式生命週期管理"
ms.custom: 
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57f769bb-5105-43e2-9096-ed54cdf82b90
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d135960143fed33d1ce4847c681f5b1134489b65
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a><span data-ttu-id="1e281-103">使用 BizTalk Server 中的 Visual Studio Team Services 中設定自動部署</span><span class="sxs-lookup"><span data-stu-id="1e281-103">Configure automatic deployment with Visual Studio Team Services in BizTalk Server</span></span>

## <a name="overview"></a><span data-ttu-id="1e281-104">概觀</span><span class="sxs-lookup"><span data-stu-id="1e281-104">Overview</span></span>

<span data-ttu-id="1e281-105">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]提供改良的自動部署和應用程式生命週期管理 (ALM) 體驗。</span><span class="sxs-lookup"><span data-stu-id="1e281-105">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] provides an improved automatic deployment and application lifecycle management (ALM) experience.</span></span> 

<span data-ttu-id="1e281-106">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，我們已改進這項功能：</span><span class="sxs-lookup"><span data-stu-id="1e281-106">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, we've improved this feature:</span></span>

* <span data-ttu-id="1e281-107">在 Visual Studio 中，設定**應用程式名稱**的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="1e281-107">Within Visual Studio, set the **Application Name** of your BizTalk application</span></span>
* <span data-ttu-id="1e281-108">除了使用代理程式為基礎的部署，您也可以使用[部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index)部署 BizTalk 應用程式的多個伺服器</span><span class="sxs-lookup"><span data-stu-id="1e281-108">In addition to using an agent-based deployment, you can also use [deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) to deploy your BizTalk applications to multiple servers</span></span>
* <span data-ttu-id="1e281-109">在發行工作中，您可以安裝 BizTalk 應用程式，並輸入 BizTalk 管理電腦，以及該路徑的部署套件</span><span class="sxs-lookup"><span data-stu-id="1e281-109">In the release task, you can install the BizTalk application, and enter the BizTalk management computer, and the path to the deployment package</span></span>

<span data-ttu-id="1e281-110">Visual Studio Team Services，您可以使用自動部署[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]至不同的 BizTalk 環境的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e281-110">Using Visual Studio Team Services, you can automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications to different BizTalk environments.</span></span> 

<span data-ttu-id="1e281-111">一般而言，有兩個角色相關：</span><span class="sxs-lookup"><span data-stu-id="1e281-111">Typically, there are two roles involved:</span></span>

- <span data-ttu-id="1e281-112">BizTalk 開發人員會建立應用程式，並在本機建置它。</span><span class="sxs-lookup"><span data-stu-id="1e281-112">BizTalk developer creates the application, and builds it locally.</span></span> <span data-ttu-id="1e281-113">然後，會檢查應用程式進入 Git 或 Team Foundation 版本控制。</span><span class="sxs-lookup"><span data-stu-id="1e281-113">Then, checks the application into Git or Team Foundation Version Control.</span></span>
- <span data-ttu-id="1e281-114">VSTS 系統管理員會建立組建和發行定義中，並將部署到不同的環境 （開發人員、 使用者接受度測試、 生產環境） 的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e281-114">VSTS admin creates the build and release definitions, and deploys to the BizTalk application to different environments (Dev, UAT, Production).</span></span>

<span data-ttu-id="1e281-115">如果您從未使用過 VSTS，本逐步解說可能是一項挑戰。</span><span class="sxs-lookup"><span data-stu-id="1e281-115">If you’ve never used VSTS, this walkthrough may be challenging.</span></span> <span data-ttu-id="1e281-116">它需要 git，包括複製，以及將變更推入了的解。</span><span class="sxs-lookup"><span data-stu-id="1e281-116">It does require some understanding of git, including cloning, and pushing changes.</span></span> 

<span data-ttu-id="1e281-117">我們示範如何設定與 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並加入您要部署的第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e281-117">We show you how to setup VSTS with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and add your first application to deploy.</span></span> <span data-ttu-id="1e281-118">我們建議您參閱[VSTS 指引](https://docs.microsoft.com/vsts/user-guide/)，如 VSTS UI 變更。</span><span class="sxs-lookup"><span data-stu-id="1e281-118">We recommend you refer to the [VSTS guidance](https://docs.microsoft.com/vsts/user-guide/), as the VSTS UI changes.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="1e281-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="1e281-119">Before you begin</span></span>

* <span data-ttu-id="1e281-120">將您的 Visual Studio Team Services (VSTS) 帳戶就緒。</span><span class="sxs-lookup"><span data-stu-id="1e281-120">Have your Visual Studio Team Services (VSTS) account ready.</span></span> <span data-ttu-id="1e281-121">沒有網路怎麼辦？</span><span class="sxs-lookup"><span data-stu-id="1e281-121">Don't have one?</span></span> <span data-ttu-id="1e281-122">[註冊 Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services)。</span><span class="sxs-lookup"><span data-stu-id="1e281-122">[Sign up for Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).</span></span>
* <span data-ttu-id="1e281-123">如果您已經有 BizTalk 電腦上安裝 VSTS 代理程式，以最新的 VSTS 代理程式覆寫現有的代理程式。</span><span class="sxs-lookup"><span data-stu-id="1e281-123">If you already have a VSTS Agent installed on your BizTalk computer, then the existing agent is overwritten with the latest VSTS Agent.</span></span> <span data-ttu-id="1e281-124">您可能必須更新您[VSTS 服務，以配合新的代理程式](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent)。</span><span class="sxs-lookup"><span data-stu-id="1e281-124">You may have to update your [VSTS service to align with the new agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).</span></span>
* <span data-ttu-id="1e281-125">VSTS 與自動部署功能組件 1，完成其中一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中。</span><span class="sxs-lookup"><span data-stu-id="1e281-125">With Feature Pack 1, automatic deployment with VSTS is done on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> <span data-ttu-id="1e281-126">確定電腦具有 Visual Studio 和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]開發者工具與 SDK 安裝。</span><span class="sxs-lookup"><span data-stu-id="1e281-126">Be sure the computer has Visual Studio and the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] Developer Tools and SDK installed.</span></span> <span data-ttu-id="1e281-127">請參閱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)][硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="1e281-127">See the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [hardware and software requirements](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span>
* <span data-ttu-id="1e281-128">Feature Pack 2，與使用 VSTS 自動部署，才可以使用[部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/howto-deployment-groups)。</span><span class="sxs-lookup"><span data-stu-id="1e281-128">With Feature Pack 2, automatic deployment with VSTS can be done using [deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/howto-deployment-groups).</span></span> <span data-ttu-id="1e281-129">您可以使用部署群組，來部署您的應用程式部署群組內的多部 BizTalk 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1e281-129">Using deployment groups, you can deploy your applications to multiple BizTalk Servers within the deployment group.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1e281-130">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="1e281-130">Prerequisites</span></span>

* <span data-ttu-id="1e281-131">安裝[功能套件 2](https://aka.ms/bts2016fp2)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e281-131">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="1e281-132">某些體驗和建立及使用定義於 VSTS 中的知識。</span><span class="sxs-lookup"><span data-stu-id="1e281-132">Some experience and knowledge with creating and working with definitions in VSTS.</span></span> <span data-ttu-id="1e281-133">如果您是新手 VSTS，這些可能是很好的資源︰</span><span class="sxs-lookup"><span data-stu-id="1e281-133">If you're brand new to VSTS, these may be good resources:</span></span> 

  [<span data-ttu-id="1e281-134">Visual Studio Team Services 概觀</span><span class="sxs-lookup"><span data-stu-id="1e281-134">Visual Studio Team Services overview</span></span>](https://www.visualstudio.com/docs/overview)  
  [<span data-ttu-id="1e281-135">CI/CD 新手適用的</span><span class="sxs-lookup"><span data-stu-id="1e281-135">CI/CD for newbies</span></span>](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)

## <a name="get-started"></a><span data-ttu-id="1e281-136">開始使用</span><span class="sxs-lookup"><span data-stu-id="1e281-136">Get started</span></span>
[<span data-ttu-id="1e281-137">步驟 1：新增應用程式專案及更新 .json 範本</span><span class="sxs-lookup"><span data-stu-id="1e281-137">Step 1: Add Application project & update .json template</span></span>](feature-pack-add-application-project.md)  

[<span data-ttu-id="1e281-138">步驟 2：建立 VSTS 權杖及安裝組建代理程式</span><span class="sxs-lookup"><span data-stu-id="1e281-138">Step 2: Create the VSTS token & install the build agent</span></span>](feature-pack-create-vsts-token.md)

[<span data-ttu-id="1e281-139">步驟 3： 建立組建和發行定義</span><span class="sxs-lookup"><span data-stu-id="1e281-139">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)

[<span data-ttu-id="1e281-140">設定環境的語彙基元和變數</span><span class="sxs-lookup"><span data-stu-id="1e281-140">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)