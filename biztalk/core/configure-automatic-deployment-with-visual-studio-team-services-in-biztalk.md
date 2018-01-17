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
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a>使用 BizTalk Server 中的 Visual Studio Team Services 中設定自動部署

## <a name="overview"></a>概觀

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]提供改良的自動部署和應用程式生命週期管理 (ALM) 體驗。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，我們已改進這項功能：

* 在 Visual Studio 中，設定**應用程式名稱**的 BizTalk 應用程式
* 除了使用代理程式為基礎的部署，您也可以使用[部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index)部署 BizTalk 應用程式的多個伺服器
* 在發行工作中，您可以安裝 BizTalk 應用程式，並輸入 BizTalk 管理電腦，以及該路徑的部署套件

Visual Studio Team Services，您可以使用自動部署[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]至不同的 BizTalk 環境的應用程式。 

一般而言，有兩個角色相關：

- BizTalk 開發人員會建立應用程式，並在本機建置它。 然後，會檢查應用程式進入 Git 或 Team Foundation 版本控制。
- VSTS 系統管理員會建立組建和發行定義中，並將部署到不同的環境 （開發人員、 使用者接受度測試、 生產環境） 的 BizTalk 應用程式。

如果您從未使用過 VSTS，本逐步解說可能是一項挑戰。 它需要 git，包括複製，以及將變更推入了的解。 

我們示範如何設定與 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並加入您要部署的第一個應用程式。 我們建議您參閱[VSTS 指引](https://docs.microsoft.com/vsts/user-guide/)，如 VSTS UI 變更。 

## <a name="before-you-begin"></a>開始之前

* 將您的 Visual Studio Team Services (VSTS) 帳戶就緒。 沒有網路怎麼辦？ [註冊 Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services)。
* 如果您已經有 BizTalk 電腦上安裝 VSTS 代理程式，以最新的 VSTS 代理程式覆寫現有的代理程式。 您可能必須更新您[VSTS 服務，以配合新的代理程式](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent)。
* VSTS 與自動部署功能組件 1，完成其中一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中。 確定電腦具有 Visual Studio 和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]開發者工具與 SDK 安裝。 請參閱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)][硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。
* Feature Pack 2，與使用 VSTS 自動部署，才可以使用[部署群組](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/howto-deployment-groups)。 您可以使用部署群組，來部署您的應用程式部署群組內的多部 BizTalk 伺服器。

## <a name="prerequisites"></a>필수 구성 요소

* 安裝[功能套件 2](https://aka.ms/bts2016fp2)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* 某些體驗和建立及使用定義於 VSTS 中的知識。 如果您是新手 VSTS，這些可能是很好的資源︰ 

  [Visual Studio Team Services 概觀](https://www.visualstudio.com/docs/overview)  
  [CI/CD 新手適用的](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)

## <a name="get-started"></a>開始使用
[步驟 1：新增應用程式專案及更新 .json 範本](feature-pack-add-application-project.md)  

[步驟 2：建立 VSTS 權杖及安裝組建代理程式](feature-pack-create-vsts-token.md)

[步驟 3： 建立組建和發行定義](feature-pack-add-build-release-definitions.md)

[設定環境的語彙基元和變數](configure-environmental-tokens-and-variables-for-automatic-deployment.md)