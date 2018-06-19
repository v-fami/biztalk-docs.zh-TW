---
title: 設定 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, command line utilities
- configuring, SSO
- SSO, interfaces
- SSOConfig [SSO]
- SSO, configuring
- SSOClient [SSO]
- SSO, tools
- SSOManage [SSO]
ms.assetid: 6f755735-9b48-4771-beec-ced844f3d532
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d729633717d709a83c10e9b50c55791029902010
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233038"
---
# <a name="configuring-sso"></a>設定 SSO
您可以使用命令列公用程式、UI 工具、COM 或 Microsoft .NET 介面，以設定「企業單一登入」。  
  
## <a name="sso-command-line-utilities"></a>SSO 命令列公用程式  
 您可使用 3 種不同的命令列公用程式，以執行「企業單一登入」工作：  
  
 **SSOConfig。** 可讓 SSO 系統管理員設定 SSO 資料庫和管理主要密碼。  
  
> [!NOTE]
>  「組態精靈」會建立 SSO 資料庫和主要密碼伺服器。  
  
 **SSOManage。** 可讓 SSO 系統管理員、SSO 分支機構系統管理員及應用程式系統管理員，更新 SSO 資料庫以新增、刪除和管理應用程式、管理使用者對應，以及設定分支機構應用程式使用者的認證。 部分作業只能由 SSO 系統管理員執行，或只能由 SSO 系統管理員和 SSO 分支機構系統管理員執行。 「應用程式系統管理員」執行的所有作業，也可由「SSO 系統管理員」或「SSO 分支機構系統管理員」執行。  
  
 **SSOClient。** 可讓「單一登入」使用者管理自己的使用者對應和設定其認證。  
  
 如需有關 SSO 帳戶的詳細資訊，請參閱[SSO 使用者群組](../core/sso-user-groups.md)。  
  
## <a name="sso-ui-tools"></a>SSO UI 工具  
 **企業 SSO MMC 嵌入式管理單元。** 可讓 SSO 系統管理員、SSO 分支機構系統管理員及應用程式系統管理員，更新 SSO 資料庫以新增、刪除和管理應用程式、管理使用者對應，以及設定分支機構應用程式使用者的認證。 部分作業只能由 SSO 系統管理員執行，或只能由 SSO 系統管理員和 SSO 分支機構系統管理員執行。 「應用程式系統管理員」執行的所有作業，也可由「SSO 系統管理員」或「SSO 分支機構系統管理員」執行。  
  
 **SSO 用戶端公用程式。** 可讓一般使用者使用 UI 工具，管理自己的對應和設定其認證。  
  
## <a name="sso-com-and-net-interfaces"></a>SSO COM 和 .NET 介面  
 「企業單一登入」提供 COM 和 .NET 程式設計介面，讓您可以建立自訂元件，以及建立指令碼以協助 SSO 系統的管理。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 元件](../core/sso-components.md)