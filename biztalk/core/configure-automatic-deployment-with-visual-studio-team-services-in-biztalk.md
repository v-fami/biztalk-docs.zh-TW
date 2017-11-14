---
title: "使用 Visual Studio Team Services 中設定自動部署 |Microsoft 文件"
description: "安裝 BizTalk 功能套件部署至不同的 BizTalk 環境的應用程式中使用 VSTS 應用程式生命週期管理"
ms.custom: 
ms.date: 11/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57f769bb-5105-43e2-9096-ed54cdf82b90
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04a7d2b2430a5dc57403fc179fa1c1859d3a82b3
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a><span data-ttu-id="6f06a-103">使用 BizTalk Server 中的 Visual Studio Team Services 中設定自動部署</span><span class="sxs-lookup"><span data-stu-id="6f06a-103">Configure automatic deployment with Visual Studio Team Services in BizTalk Server</span></span>

## <a name="overview"></a><span data-ttu-id="6f06a-104">概觀</span><span class="sxs-lookup"><span data-stu-id="6f06a-104">Overview</span></span>

<span data-ttu-id="6f06a-105">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]提供改良的自動部署和應用程式生命週期管理 (ALM) 體驗。</span><span class="sxs-lookup"><span data-stu-id="6f06a-105">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] provides an improved automatic deployment and application lifecycle management (ALM) experience.</span></span> 

<span data-ttu-id="6f06a-106">Visual Studio Team Services，您可以使用自動部署[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]至不同的 BizTalk 環境的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f06a-106">Using Visual Studio Team Services, you can automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications to different BizTalk environments.</span></span> 

<span data-ttu-id="6f06a-107">一般而言，有兩個角色相關：</span><span class="sxs-lookup"><span data-stu-id="6f06a-107">Typically, there are two roles involved:</span></span>

- <span data-ttu-id="6f06a-108">BizTalk 開發人員會建立應用程式，並在本機建置它。</span><span class="sxs-lookup"><span data-stu-id="6f06a-108">BizTalk developer creates the application, and builds it locally.</span></span> <span data-ttu-id="6f06a-109">然後，會檢查應用程式進入 Git 或 Team Foundation 版本控制。</span><span class="sxs-lookup"><span data-stu-id="6f06a-109">Then, checks the application into Git or Team Foundation Version Control.</span></span>
- <span data-ttu-id="6f06a-110">VSTS 系統管理員會建立組建和發行定義中，並將部署到不同的環境 （開發人員、 使用者接受度測試、 生產環境） 的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f06a-110">VSTS admin creates the build and release definitions, and deploys to the BizTalk application to different environments (Dev, UAT, Production).</span></span>

<span data-ttu-id="6f06a-111">如果您從未使用過 VSTS，本逐步解說可能是一項挑戰。</span><span class="sxs-lookup"><span data-stu-id="6f06a-111">If you’ve never used VSTS, this walkthrough may be challenging.</span></span> <span data-ttu-id="6f06a-112">它需要 git，包括複製，以及將變更推入了的解。</span><span class="sxs-lookup"><span data-stu-id="6f06a-112">It does require some understanding of git, including cloning, and pushing changes.</span></span> 

<span data-ttu-id="6f06a-113">我們示範如何設定與 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並加入您要部署的第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f06a-113">We show you how to setup VSTS with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and add your first application to deploy.</span></span> <span data-ttu-id="6f06a-114">我們建議您參閱[VSTS 指引](https://docs.microsoft.com/vsts/user-guide/)，如 VSTS UI 變更。</span><span class="sxs-lookup"><span data-stu-id="6f06a-114">We recommend you refer to the [VSTS guidance](https://docs.microsoft.com/vsts/user-guide/), as the VSTS UI changes.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="6f06a-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="6f06a-115">Before you begin</span></span>

* <span data-ttu-id="6f06a-116">將您的 Visual Studio Team Services (VSTS) 帳戶就緒。</span><span class="sxs-lookup"><span data-stu-id="6f06a-116">Have your Visual Studio Team Services (VSTS) account ready.</span></span> <span data-ttu-id="6f06a-117">沒有網路怎麼辦？</span><span class="sxs-lookup"><span data-stu-id="6f06a-117">Don't have one?</span></span> <span data-ttu-id="6f06a-118">[註冊 Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services)。</span><span class="sxs-lookup"><span data-stu-id="6f06a-118">[Sign up for Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).</span></span>
* <span data-ttu-id="6f06a-119">如果您已經有 BizTalk 電腦上安裝 VSTS 代理程式，以最新的 VSTS 代理程式覆寫現有的代理程式。</span><span class="sxs-lookup"><span data-stu-id="6f06a-119">If you already have a VSTS Agent installed on your BizTalk computer, then the existing agent is overwritten with the latest VSTS Agent.</span></span> <span data-ttu-id="6f06a-120">您可能必須更新您[VSTS 服務，以配合新的代理程式](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent)。</span><span class="sxs-lookup"><span data-stu-id="6f06a-120">You may have to update your [VSTS service to align with the new agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).</span></span>
* <span data-ttu-id="6f06a-121">自動部署 VSTS 對其中一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中。</span><span class="sxs-lookup"><span data-stu-id="6f06a-121">Automatic deployment with VSTS is done on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> <span data-ttu-id="6f06a-122">確定電腦具有 Visual Studio 和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]開發者工具與 SDK 安裝。</span><span class="sxs-lookup"><span data-stu-id="6f06a-122">Be sure the computer has Visual Studio and the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] Developer Tools and SDK installed.</span></span> <span data-ttu-id="6f06a-123">請參閱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)][硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="6f06a-123">See the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [hardware and software requirements](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f06a-124">必要條件</span><span class="sxs-lookup"><span data-stu-id="6f06a-124">Prerequisites</span></span>

* <span data-ttu-id="6f06a-125">安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f06a-125">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="6f06a-126">某些體驗和建立及使用定義於 VSTS 中的知識。</span><span class="sxs-lookup"><span data-stu-id="6f06a-126">Some experience and knowledge with creating and working with definitions in VSTS.</span></span> <span data-ttu-id="6f06a-127">如果您是新手 VSTS，這些可能是很好的資源：</span><span class="sxs-lookup"><span data-stu-id="6f06a-127">If you're brand new to VSTS, these may be good resources:</span></span> 

  [<span data-ttu-id="6f06a-128">Visual Studio Team Services 概觀</span><span class="sxs-lookup"><span data-stu-id="6f06a-128">Visual Studio Team Services overview</span></span>](https://www.visualstudio.com/docs/overview)  
  [<span data-ttu-id="6f06a-129">CI/CD 新手適用的</span><span class="sxs-lookup"><span data-stu-id="6f06a-129">CI/CD for newbies</span></span>](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)

## <a name="get-started"></a><span data-ttu-id="6f06a-130">快速入門</span><span class="sxs-lookup"><span data-stu-id="6f06a-130">Get started</span></span>
[<span data-ttu-id="6f06a-131">步驟 1： 在此加入應用程式專案 （& s) 更新.json 範本</span><span class="sxs-lookup"><span data-stu-id="6f06a-131">Step 1: Add Application project & update .json template</span></span>](feature-pack-add-application-project.md)  

[<span data-ttu-id="6f06a-132">步驟 2： 建立 VSTS 語彙基元，並安裝組建代理程式</span><span class="sxs-lookup"><span data-stu-id="6f06a-132">Step 2: Create the VSTS token & install the build agent</span></span>](feature-pack-create-vsts-token.md)

[<span data-ttu-id="6f06a-133">步驟 3： 建立組建和發行定義</span><span class="sxs-lookup"><span data-stu-id="6f06a-133">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)

[<span data-ttu-id="6f06a-134">設定環境的語彙基元和變數</span><span class="sxs-lookup"><span data-stu-id="6f06a-134">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)