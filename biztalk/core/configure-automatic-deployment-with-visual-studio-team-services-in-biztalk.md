---
title: "使用 BizTalk Server 中的 Visual Studio Team Services 中設定自動部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57f769bb-5105-43e2-9096-ed54cdf82b90
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 23d79eae3bd89a572a919cfeff800178f9163796
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a><span data-ttu-id="51dcf-102">使用 BizTalk Server 中的 Visual Studio Team Services 中設定自動部署</span><span class="sxs-lookup"><span data-stu-id="51dcf-102">Configure automatic deployment with Visual Studio Team Services in BizTalk Server</span></span>
<span data-ttu-id="51dcf-103">自動部署[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]使用 Visual Studio Team Services 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="51dcf-103">Automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications using Visual Studio Team Services.</span></span> 

<span data-ttu-id="51dcf-104">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]提供改良的自動部署和應用程式生命週期管理 (ALM) 體驗。</span><span class="sxs-lookup"><span data-stu-id="51dcf-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] provides an improved automatic deployment and application lifecycle management (ALM) experience.</span></span> 

<span data-ttu-id="51dcf-105">這個區段會顯示如何設定與 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並加入您要部署的第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="51dcf-105">This section shows you how to setup VSTS with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and add your first application to deploy.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="51dcf-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="51dcf-106">Before you begin</span></span>

* <span data-ttu-id="51dcf-107">將您的 Visual Studio Team Services (VSTS) 帳戶就緒。</span><span class="sxs-lookup"><span data-stu-id="51dcf-107">Have your Visual Studio Team Services (VSTS) account ready.</span></span> <span data-ttu-id="51dcf-108">沒有網路怎麼辦？</span><span class="sxs-lookup"><span data-stu-id="51dcf-108">Don't have one?</span></span> <span data-ttu-id="51dcf-109">[註冊 Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services)。</span><span class="sxs-lookup"><span data-stu-id="51dcf-109">[Sign up for Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).</span></span>
* <span data-ttu-id="51dcf-110">如果您已經有 BizTalk 電腦上安裝 VSTS 代理程式，以最新的 VSTS 代理程式覆寫現有的代理程式。</span><span class="sxs-lookup"><span data-stu-id="51dcf-110">If you already have a VSTS Agent installed on your BizTalk computer, then the existing agent is overwritten with the latest VSTS Agent.</span></span> <span data-ttu-id="51dcf-111">您可能必須更新您[VSTS 服務，以配合新的代理程式](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent)。</span><span class="sxs-lookup"><span data-stu-id="51dcf-111">You may have to update your [VSTS service to align with the new agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).</span></span>
* <span data-ttu-id="51dcf-112">自動部署 VSTS 對其中一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中。</span><span class="sxs-lookup"><span data-stu-id="51dcf-112">Automatic deployment with VSTS is done on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> <span data-ttu-id="51dcf-113">確定電腦具有 Visual Studio 和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]開發者工具與 SDK 安裝。</span><span class="sxs-lookup"><span data-stu-id="51dcf-113">Be sure the computer has Visual Studio and the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] Developer Tools and SDK installed.</span></span> <span data-ttu-id="51dcf-114">請參閱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)][硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="51dcf-114">See the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [hardware and software requirements](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="51dcf-115">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="51dcf-115">Next steps</span></span>
[<span data-ttu-id="51dcf-116">VSTS 設定用於自動部署</span><span class="sxs-lookup"><span data-stu-id="51dcf-116">Configure VSTS for automatic deployment</span></span>](../core/configure-visual-studio-team-services-to-deploy-biztalk-solutions-or-projects.md)

[<span data-ttu-id="51dcf-117">設定的 JSON 範本</span><span class="sxs-lookup"><span data-stu-id="51dcf-117">Configure the JSON template</span></span>](../core/configure-the-json-template-for-automatic-deployment.md)

[<span data-ttu-id="51dcf-118">設定環境的語彙基元和變數</span><span class="sxs-lookup"><span data-stu-id="51dcf-118">Configure environmental tokens and variables</span></span>](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md)

[<span data-ttu-id="51dcf-119">加入 VSTS BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="51dcf-119">Add a BizTalk application to VSTS</span></span>](../core/add-a-biztalk-server-application-to-visual-studio-team-services.md)