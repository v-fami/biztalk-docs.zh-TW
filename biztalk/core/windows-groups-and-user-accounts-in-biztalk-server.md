---
title: Windows 群組和 BizTalk Server 中的使用者帳戶 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, BTS_ADMIN_USERS role [SQL Server database]
- MessageBox database, BTS_HOST_USERS role [SQL Server database]
- Rule Engine database, BTS_HOST_USERS role [SQL Server database]
- Management database, BTS_OPERATORS role [SQL Server database]
- BTS_HOST_USERS role [SQL Server database]
- NSSubscriberAdmin role [SQL Server database]
- Management database, tpm_user role [SQL Server database]
- SSO, securityadmin role [SQL Server database]
- IIS_WPG group
- BAM Notification service account
- EDI_ADMIN_USERS role [SQL Server database]
- Archive database [BAM], db_owner role [SQL Server database]
- Primary Import database [BAM], db_owner role [SQL Server database]
- Primary Import database [BAM], BAM_EVENT_WRITER role [SQL Server database]
- Notification Services Application database [BAM], db_owner role [SQL Server database]
- NSRunService role [SQL Server database]
- RE_HOST_USERS role [SQL Server database]
- MessageBox database, BTS_OPERATORS role [SQL Server database]
- Rule Engine database, RE_HOST_USERS role [SQL Server database]
- Windows groups, creating
- securityadmin role [SQL Server database]
- BizTalk Isolated Host Instance service account
- In-Process BizTalk Host groups
- Primary Import database [BAM], BTS_ADMIN_USERS role [SQL Server database]
- SSO Affiliate Administrators [Windows group]
- Star Schema database [BAM], db_owner role [SQL Server database]
- Notification Services Instance database [BAM], db_owner role [SQL Server database]
- MessageBox database, BTS_ADMIN_USERS role [SQL Server database]
- Rule Engine Update Service account
- Configuration Manager, creating user accounts
- SSO Administrators [Windows group]
- Rule Engine database, BTS_ADMIN_USERS role [SQL Server database]
- Tracking database, BTS_OPERATORS role [SQL Server database]
- Primary Import database [BAM], BAM_ManagementNSReader role [SQL Server database]
- Notification Services Instance database [BAM], role [SQL Server database]
- BizTalk Application Users [Windows group]
- user accounts, creating
- Rule Engine database, BTS_OPERATORS role [SQL Server database]
- STS_WPG group
- BAM_ManagementWS role [SQL Server database]
- BTS_OPERATORS role [SQL Server database]
- Tracking database, BTS_HOST_USERS role [SQL Server database]
- SSO, db_owner role [SQL Server database]
- Notification Services Application database [BAM], role [SQL Server database]
- OLAP Administrators
- BAM_EVENT_WRITER role [SQL Server database]
- Windows groups, group list
- tpm_user role [SQL Server database]
- BizTalk Host Instance service account
- Base DBI database, EDI_ADMIN_USERS role [SQL Server database]
- Primary Import database [BAM], role [SQL Server database]
- BizTalk SharePoint Adapter Enabled Hosts [Windows group]
- BAM Management Web service account
- db_owner role [SQL Server database]
- Management database, BTS_ADMIN_USERS role [SQL Server database]
- Configuration Manager, creating groups
- Management database, BTS_HOST_USERS role [SQL Server database]
- BizTalk Server Operators [Windows group]
- Base DBI database, BTS_OPERATORS role [SQL Server database]
- Enterprise Single Sign-On Service account
- NSAdmin role [SQL Server database]
- BAM_ManagementNSReader role [SQL Server database]
- Notification Services Application database [BAM], NSRunService role [SQL Server database]
- BTS_ADMIN_USERS role [SQL Server database]
- BizTalk Isolated Host Users [Windows group]
- Notification Services Instance database [BAM], NSAdmin role [SQL Server database]
- SQLServer2005NotificationServicesUser
- EDI Subsystem Users [Windows group]
- Primary Import database [BAM], BTS_HOST_USERS role [SQL Server database]
- BizTalk Server Administrators [Windows group]
- BAM Portal Users [Windows group]
- Notification Services Application database [BAM], NSAdmin role [SQL Server database]
ms.assetid: a01603bd-4105-4691-819d-de43b00b40f3
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a04b8e774156acaaa44dc49377bbdd7e3f91b198
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976100"
---
# <a name="windows-groups-and-user-accounts-in-biztalk-server"></a>BizTalk Server 中的 Windows 群組和使用者帳戶
BizTalk Server 本機和網域群組和使用者帳戶的相關資訊。 如果您在單一電腦安裝 BizTalk Server 以及所有必備的軟體，「組態管理員」預設會為您建立所需的 BizTalk 群組帳戶。 本節中所包含的資訊適用於多個電腦的拓撲。  
  
> [!IMPORTANT]
>  BizTalk Server 僅在單一電腦組態中支援本機群組和使用者帳戶。 BizTalk Server 在單一電腦組態和多電腦組態中都支援網域群組和使用者帳戶。 若您在 BizTalk Server 組態使用網域群組，則必須在設定 BizTalk Server 之前手動建立群組。 「組態管理員」無法建立網域群組。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-windows-group-and-user-accounts-in-biztalk-server"></a>在 BizTalk Server 中建立 Windows 群組和使用者帳戶  
  
1.  使用 Active Directory 中，從**啟動**功能表上，指向**程式**，指向 **系統管理工具**，然後選取**Active Directory 使用者和電腦**。  
  
2.  在 Active Directory 使用者和電腦 視窗中，以滑鼠右鍵按一下底部的右窗格中，或以滑鼠右鍵按一下**使用者**在瀏覽樹狀目錄中的左窗格中的資料夾。  
  
3.  選取**新增**，然後選取**群組**或**使用者**。  
  
4.  輸入下表中提供的群組或使用者資訊。  
  
 下表列出 BizTalk Server 使用的 Windows 群組及其成員資格。 本表也可以用來識別群組的「SQL Server 角色」或「資料庫角色」。  
  
|群組|群組描述|成員資格|SQL Server 角色或資料庫角色|  
|-----------|-----------------------|----------------|----------------------------------------|  
|SSO 系統管理員|「企業單一登入」(SSO) 服務的系統管理員。|包含「企業單一登入服務」的服務帳戶。<br /><br /> 包含需要設定及管理 BizTalk Server 和 SSO 服務之能力的使用者/群組。<br /><br /> 包含可在設定 SSO 主要密碼伺服器時用來執行 BizTalk 組態管理員的帳戶。|SSO 的 db_owner SQL Server 資料庫角色<br /><br /> SSO 所在之 SQL Server 的 securityadmin SQL Server 角色|  
|SSO 分支機構系統管理員|特定 SSO 分支機構應用程式的系統管理員。<br /><br /> 可以建立/刪除 SSO 分支機構應用程式；管理使用者對應；以及設定分支機構應用程式使用者的認證|沒有包含服務帳戶。<br /><br /> 包含 BizTalk Server 系統管理員使用的帳戶。||  
|BizTalk Server 系統管理員|擁有執行管理工作所需的最低權限<br /><br /> 可以部署解決方案；管理應用程式；以及解決訊息處理問題。<br /><br /> 若要執行配接器、接收和傳送處理常式以及接收位置的管理工作，必須將「BizTalk Server 系統管理員」新增到「單一登入分支機構系統管理員」。<br /><br /> 如需詳細資訊，請參閱[管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)。|包含需要設定及管理 BizTalk Server 之能力的使用者/群組。|在下列資料庫中的 BTS_ADMIN_USERS SQL Server 資料庫角色：<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> 下列資料庫的 db_owner SQL Server 資料庫角色：<br /><br /> BAMStarSchema<br /><br /> BAMPrimaryImport<br /><br /> BAMArchive<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> 下列資料庫中的 NSAdmin SQL Server 資料庫角色：<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> 在裝載 BAMAnalysis OLAP 資料庫之電腦上的 OLAP 系統管理員。|  
|BizTalk Server 操作員|具備低權限角色，僅有用來監控和疑難排解動作的存取權<br /><br /> 如需詳細資訊，請參閱[管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)|包含將會監控解決方案的使用者/群組。<br /><br /> 沒有包含服務帳戶。|下列資料庫中的 BTS_OPERATORS SQL Server 資料庫角色：<br /><br /> BizTalkDTADb<br /><br /> BizTalkEDIDb<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb|  
|BizTalk 應用程式使用者|「組態管理員」建立的第一個「內含式 BizTalk 主控件群組」的預設名稱。<br /><br /> 針對環境中的每個「內含式主控件」，各使用一個 BizTalk 主控件群組。<br /><br /> 包括具有「內含式 BizTalk 主控件」(裝載 BizTalk Server 中的處理程序，BTSNTSvc.exe) 存取權的帳戶。|包含「BizTalk 內含式主控件執行個體」(屬於「內含式 BizTalk 主控件群組」被指定到的主控件) 的服務帳戶。|下列資料庫中的 BTS_HOST_USERS SQL Server 資料庫角色：<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> 在 BAMPrimaryImport 中的 BAM_EVENT_WRITER SQL Server 資料庫角色|  
|BizTalk 外掛式主控件使用者|「組態管理員」建立的第一個「外掛式 BizTalk 主控件群組」的預設名稱。 不在 BizTalk Server 上執行的外掛式 BizTalk 主控件，如 HTTP 和 SOAP。<br /><br /> 針對環境中的每個「外掛式主控件」，各使用一個 BizTalk 外掛式主控件群組。|包含「BizTalk 外掛式主控件執行個體」(屬於「外掛式 BizTalk 主控件群組」被指定到的主控件) 的服務帳戶。|下列資料庫中的 BTS_HOST_USERS SQL Server 資料庫角色：<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport|  
|BAM 入口網站使用者|擁有 BAM 入口網站的存取權。|這個角色預設使用 Everyone 群組。<br /><br /> 沒有包含服務帳戶。||  
|啟用 BizTalk SharePoint 配接器的主控件|擁有 Windows SharePoint Services 配接器 Web 服務的存取權|包含能讓 BizTalk 主控件執行個體呼叫 SharePoint 配接器的服務帳戶。||  
|BizTalk B2B 操作員群組|新的 BizTalk 角色可減少系統管理員執行所有合作對象管理作業的負擔。 此角色可讓 Windows 使用者與角色關聯，以執行所有合作對象管理作業。|包含必須能夠設定和管理 BizTalk Server TPM 資料並監視解決方案的使用者/群組。|在下列資料庫 BTS_OPERATORS SQL Server 資料庫角色： BizTalkDTADb、 BizTalkMgmtDb、 BizTalkMsgBoxDb、 BizTalkRuleEngineDb 和 BAMPrimaryImport|  
  
 下表列出 BizTalk Server 使用的 Windows 使用者或服務帳戶以及群組分支機構。 它也會識別 SQL Server 角色或資料庫角色的帳戶。  
  
|使用者|使用者描述|群組分支機構|SQL Server 角色或資料庫角色|  
|----------|----------------------|-----------------------|----------------------------------------|  
|企業單一登入服務|用以執行會存取 SSO 資料庫的「企業單一登入服務」的服務帳戶。|SSO 系統管理員||  
|BizTalk 主控件執行個體帳戶|用以執行會存取「內含式 BizTalk 主控件執行個體」(BTNTSVC) 的「BizTalk 內含式主控件執行個體」的服務帳戶。|BizTalk 應用程式使用者<br /><br /> SSO 分支機構系統管理員||  
|BizTalk 外掛式主控件執行個體帳戶|用以執行「BizTalk 外掛式主控件執行個體」(HTTP/SOAP) 的服務帳戶。|BizTalk 外掛式主控件使用者<br /><br /> SSO 分支機構系統管理員<br /><br /> IIS_WPG||  
|規則引擎更新服務|用以執行會從規則引擎資料庫接收部署/解除部署原則通知的「規則引擎更新服務」的服務帳戶。||在 BizTalkRuleEngineDb 中的 RE_HOST_USERS SQL Server 資料庫角色|  
|BAM Notification Services 使用者|用以執行會存取 BAM 資料庫的 BAM Notification Services 的服務帳戶。|SQLServer2008NotificationServicesUser$\<**ComputerName**\>|在下列資料庫中的 NSRunService SQL Server 資料庫角色：<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BAMPrimaryImport 的 BAM_ManagementNSReader SQL Server 角色|  
|BAM 管理 Web 服務使用者|可讓 BAM 管理 Web 服務 (BAMManagementService) 存取各種 BAM 資源的使用者帳戶。 BAM 入口網站透過登入 BAM 入口網站的使用者認證呼叫 BAMManagementService，以管理警示、取得 BAM 定義 XML 和 BAM 檢視|IIS_WPG|在下列資料庫中的 NSSubscriberAdmin SQL Server 資料庫角色：<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BAMPrimaryImport 的 BAM_ManagementWS SQL Server 角色|  
|BAM 應用程式集區帳戶|裝載 BAM 入口網站的 BAMAppPool 的應用程式集區帳戶。|IIS_WPG||  
  
## <a name="in-this-section"></a>本節內容  
  
-   [本機群組](../core/local-groups.md)  
  
-   [網域群組](../core/domain-groups.md)