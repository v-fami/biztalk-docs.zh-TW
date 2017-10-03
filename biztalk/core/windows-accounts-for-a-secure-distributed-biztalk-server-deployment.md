---
title: "Windows 帳戶的安全分散式的 BizTalk Server 部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, Windows groups
- user accounts, naming conventions
- user accounts
- access control, Windows groups
- security, access control
- architecture, security
- security, Windows accounts
- administrator accounts
- user accounts, administrators
- architecture, large distributions
ms.assetid: 2a0893ef-8bfb-481b-b024-7f7d6e2a6f09
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 678977b23f377425718e483d87725ba191bbda86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="windows-accounts-for-a-secure-distributed-biztalk-server-deployment"></a>用於安全分散式 BizTalk Server 部署的 Windows 帳戶
完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 本節提供在分散式 BizTalk Server 環境中建立 Windows 群組與帳戶的建議。 群組與帳戶名稱是根據群組與帳戶的功能而建議的。 而您可以選擇這些群組與帳戶的名稱。 如需有關分散式 BizTalk Server 架構的詳細資訊，請參閱[大型分散式架構](../core/large-distributed-architecture.md)。  
  
## <a name="windows-groups-for-a-secure-distributed-biztalk-server-deployment"></a>用於安全分散式 BizTalk Server 部署的 Windows 群組  
 下列清單是建議網域系統管理員，應在資料層的網域控制站中建立的 Windows 群組。  
  
-   SSO 系統管理員  
  
-   SSO 分支機構系統管理員  
  
-   BizTalk Server 系統管理員  
  
-   BizTalk Server 操作員  
  
 如需 BizTalk Server 使用的 Windows 群組的完整資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
 除了先前的網域群組之外，下表列出在資料層的網域控制站中，為了保護網域的安全部署，系統管理員要建立的其他群組。  
  
|群組名稱 (建議)|目的|  
|------------------------------|-------------|  
|BizTalk 處理主控件使用者 1|用來處理訊息的特定內含式主控件的主控件執行個體群組。 為您在 BizTalk Server 環境中要用來處理訊息的每個內含式主控件建立群組。|  
|BizTalk 傳送主控件使用者 1|用來傳送訊息的特定內含式主控件的主控件執行個體群組。 為您在 BizTalk Server 環境中要用來傳送訊息的每個內含式主控件建立群組。|  
|BizTalk 接收主控件使用者 1|用來接收訊息的特定內含式主控件的主控件執行個體群組。 為您要在 BizTalk Server 環境中用來接收訊息的每個內含式主控件建立群組。|  
|BizTalk 追蹤主控件使用者|專門用來追蹤的 BizTalk 主控件群組。|  
|BizTalk SOAP 使用者|用於 SOAP 配接器的外掛式主控件的主控件執行個體群組。|  
|BizTalk HTTP 使用者|用於 HTTP 配接器的外掛式主控件的主控件執行個體群組。|  
  
 網域系統管理員必須在服務介面網域的網域控制站中建立下列群組：  
  
-   BizTalk BAM 入口網站使用者  
  
## <a name="windows-user-or-service-accounts-for-a-secure-distributed-biztalk-server-deployment"></a>用於安全分散式 BizTalk Server 部署的 Windows 使用者或服務帳戶  
 下表列出在資料網域的網域控制站中，建議要為網域系統管理員建立的帳戶。 網域系統管理員必須確定這些帳戶是指定群組的成員。  
  
 完成 BizTalk Server 使用的使用者帳戶的詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
|帳戶名稱 (範例)|類型|群組成員|  
|------------------------------|----------|---------------------|  
|SSO 系統管理員|使用者|SSO 系統管理員|  
|SSO 服務|服務|SSO 系統管理員|  
|SSO 主要密碼|服務|SSO 系統管理員|  
|BizTalk 系統管理員|使用者|BizTalk 系統管理員<br /><br /> SSO 分支機構系統管理員|  
|BizTalk 操作員|使用者|BizTalk 操作員|  
|BizTalk 處理 1|服務|BizTalk 處理主控件使用者 1|  
|BizTalk 處理 2**附註：**您可以針對每個處理主控件建立多個帳戶，您的環境中。|服務|BizTalk 處理主控件使用者 1|  
|BizTalk 追蹤|服務|BizTalk 追蹤主控件使用者|  
|SOAP adapter (SOAP 配接器)|服務|BizTalk SOAP 使用者|  
|HTTP 配接器|服務|BizTalk HTTP 使用者|  
|規則引擎更新服務|服務||  
|安裝|使用者|SSO 系統管理員 (僅限設定主要密碼伺服器)<br /><br /> 本機系統管理員<br /><br /> 系統管理員 (sysadmin) SQL Server 角色<br /><br /> OLAP 系統管理員|  
|BAM 應用程式集區|服務|IIS_WPG|  
|BAM 管理|服務|IIS_WPG|  
|BAM 通知|服務|SQLServer2005NotificationServicesUser$\<**ComputerName**>|  
  
 下表所列帳戶是建議網域系統管理員，應在企業網域的網域控制站中建立的帳戶。  
  
|帳戶名稱|類型|  
|------------------|----------|  
|SharePoint 系統管理員|使用者|  
|SharePoint 網站認證|使用者|  
  
## <a name="see-also"></a>另請參閱  
 [大型分散式的架構](../core/large-distributed-architecture.md)   
 [最低安全性使用者權限](../core/minimum-security-user-rights.md)   
 [Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)