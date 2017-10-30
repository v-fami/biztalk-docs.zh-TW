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
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a>使用 BizTalk Server 中的 Visual Studio Team Services 中設定自動部署
自動部署[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]使用 Visual Studio Team Services 的應用程式。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]提供改良的自動部署和應用程式生命週期管理 (ALM) 體驗。 

這個區段會顯示如何設定與 VSTS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並加入您要部署的第一個應用程式。

## <a name="before-you-begin"></a>開始之前

* 將您的 Visual Studio Team Services (VSTS) 帳戶就緒。 沒有網路怎麼辦？ [註冊 Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services)。
* 如果您已經有 BizTalk 電腦上安裝 VSTS 代理程式，以最新的 VSTS 代理程式覆寫現有的代理程式。 您可能必須更新您[VSTS 服務，以配合新的代理程式](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent)。
* 自動部署 VSTS 對其中一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]群組中。 確定電腦具有 Visual Studio 和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]開發者工具與 SDK 安裝。 請參閱[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)][硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。

## <a name="next-steps"></a>後續的步驟
[VSTS 設定用於自動部署](../core/configure-visual-studio-team-services-to-deploy-biztalk-solutions-or-projects.md)

[設定的 JSON 範本](../core/configure-the-json-template-for-automatic-deployment.md)

[設定環境的語彙基元和變數](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md)

[加入 VSTS BizTalk 應用程式](../core/add-a-biztalk-server-application-to-visual-studio-team-services.md)