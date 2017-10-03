---
title: "在 BizTalk Server 中的資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM]
- Archive database [BAM]
- Analysis database [BAM]
- Windows SharePoint Services, content database
- Windows SharePoint Services, configuration database
- TPM database
- BizTalk Server, databases
- Notification Services Instance database [BAM]
- Star Schema database [BAM]
- Primary Import database [BAM]
- Rule Engine database
- databases, BizTalk Server
- SSO database
- Tracking Analysis Server database [BAM]
- Management database
- Tracking database
- MessageBox database
ms.assetid: bb504a26-cae6-4f2a-9b86-3554ef8f6045
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08cd452aa7f56ad7802c1ea458620ed9fcd21047
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="databases-in-biztalk-server"></a>BizTalk Server 中的資料庫
Microsoft BizTalk Server 會在 SQL Server 中安裝數個資料庫。 本主題說明這些資料庫和這些資料庫所使用的 SQL 邏輯群組。  

## <a name="database-descriptions"></a>描述資料庫
下表描述 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的一般使用特性。  
  
BizTalk Server 執行階段作業通常會使用前四個資料庫： BizTalk Server 管理資料庫、 MessageBox 資料庫、 追蹤資料庫以及 SSO 資料庫。 視您所使用的 BizTalk Server 功能而定，您可能有資料表中部分或全部的其他資料庫。  
  
|資料庫|預設資料庫名稱|Description|  
|--------------|---------------------------|-----------------|  
|BAM 分析|BAMAnalysis|這個資料庫含有可供線上及離線分析使用的「商務活動監控」(BAM) OLAP Cube。|  
|BAM 封存|BAMArchive|這個資料庫會封存舊的商務活動資料。 建立 BAM 封存資料庫可將 BAM 主要匯入資料庫中的商務活動資料累積降到最低。|  
|BAM Notification Services 應用程式資料庫|BAMAlertsApplication|這個資料庫包含 BAM 通知的警示資訊。 例如，當您使用 BAM 入口網站建立警示時，就會在資料庫中插入項目以指定與警示相關的條件和事件，以及警示的其他支援資料項目。|  
|BAM Notification Services 執行個體資料庫|BAMAlertsNSMain|這個資料庫包含執行個體資訊，指定通知服務連接到 BAM 正在監控之系統的方法。|  
|BAM 主要匯入資料庫|BAMPrimaryImport|這是 BAM 收集原始追蹤資料的資料庫。|  
|BAM 星狀結構描述|BAMStarSchema|這個資料庫含有臨時資料表以及量值和維度資料表。|  
|BizTalk 管理資料庫|BizTalkMgmtDb|這個資料庫是所有 BizTalk Server 執行個體的中央中繼資訊存放區。|  
|BizTalk MessageBox 資料庫|BizTalkMsgBoxDb|BizTalk Server 引擎使用這個資料庫執行路由、排入佇列、執行個體管理及其他各種工作。|  
|BizTalk 追蹤資料庫|BizTalkDTADb|這個資料庫儲存了 BizTalk Server 追蹤引擎所追蹤的狀況監控資料。|  
|規則引擎資料庫|BizTalkRuleEngineDb|這個資料庫是下列項目的儲存機制：<br /><br /> -原則，也就是相關規則的集合。<br />-詞彙，規則中關於資料參考的使用者易記、 網域特定名稱的集合。|  
|SSO 資料庫|SSODB|這個「企業單一登入」資料庫會安全地儲存接收位置的組態資訊。|  
|Windows SharePoint Services 組態資料庫|*使用者定義*|這個資料庫包含伺服器的所有全域設定。|  
|Windows SharePoint Services 內容資料庫|*使用者定義*|這個資料庫包含所有的網站內容，如清單項目及文件。|  

## <a name="database-login-accounts"></a>資料庫登入帳戶

[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]建立 SQL 登入群組，並將之對應的 SQL Server 角色和資料庫角色，如下表所示：  
  
|群組|描述|SQL Server 角色或資料庫角色|  
|-----------|-----------------|----------------------------------------|  
|BizTalk 應用程式使用者|包括具有「內含式 BizTalk 主控件」(裝載 BizTalk Server 中的程序，BTSNTSvc.exe) 存取權的帳戶。  針對環境中的每個「內含式主控件」，各使用一個 BizTalk 主控件群組。|下列資料庫中的 BTS_HOST_USERS SQL Server 資料庫角色：<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> 在 BAMPrimaryImport 中的 BAM_EVENT_WRITER SQL Server 資料庫角色|  
|BizTalk 外掛式主控件使用者|包括具有「外掛式 BizTalk 主控件」存取權的帳戶。 針對環境中的每個「外掛式主控件」，各使用一個 BizTalk 外掛式主控件群組。|下列資料庫中的 BTS_HOST_USERS SQL Server 資料庫角色：<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport|  
|BizTalk Server 系統管理員|包括所有 BizTalk Server 系統管理員，其工作包括部署解決方案、管理應用程式以及解決訊息處理問題。|在下列資料庫中的 BTS_ADMIN_USERS SQL Server 資料庫角色：<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb<br /><br /> BizTalkDTADb<br /><br /> BAMPrimaryImport<br /><br /> 下列資料庫的 db_owner SQL Server 資料庫角色：<br /><br /> BAMStarSchema<br /><br /> BAMPrimaryImport<br /><br /> BAMArchive<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> 下列資料庫中的 NSAdmin SQL Server 資料庫角色：<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BizTalkDTADb<br /><br /> BizTalkMgmtDb<br /><br /> 在裝載 BAMAnalysis OLAP 資料庫之電腦上的 OLAP 系統管理員。|  
|BizTalk Server 操作員|具備低權限角色，僅有用來監控和疑難排解動作的存取權<br /><br /> 沒有包含服務帳戶|下列資料庫中的 BTS_OPERATORS SQL Server 資料庫角色：<br /><br /> BizTalkDTADb<br /><br /> BizTalkMgmtDb<br /><br /> BizTalkMsgBoxDb<br /><br /> BizTalkRuleEngineDb|  
|SSO 系統管理員|「企業單一登入」(SSO) 服務的最上層系統管理員。<br /><br /> 包含必須隸屬此群組、且用於執行 BizTalk 組態的使用者帳戶。<br /><br /> 包含「企業單一登入」(SSO) 服務帳戶，以及必須能夠設定和管理 BizTalk Server 及 SSO 的任何使用者/群組。|SSO 的 db_owner SQL Server 資料庫角色<br /><br /> SSO 所在之 SQL Server 的 securityadmin SQL Server 角色|  

[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]建立 SQL 登入帳戶，並將之對應至 SQL Server 資料庫角色，如下表所示：  
  
|使用者帳戶|描述|SQL 資料庫角色|  
|------------------|-----------------|------------------------|  
|規則引擎更新服務|用於規則引擎更新服務的使用者帳戶。|在 BizTalkRuleEngineDb 中的 RE_HOST_USERS SQL Server 資料庫角色|  
|BAM Notification Services 使用者|用於 BAM Notification Services 的使用者帳戶。|在下列資料庫中的 NSRunService SQL Server 資料庫角色：<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BAMPrimaryImport 的 BAM_ManagementNSReader SQL Server 資料庫角色|  
|BAM 管理 Web 服務使用者|用於 BAM 管理 Web 服務的使用者帳戶。|在下列資料庫中的 NSSubscriberAdmin SQL Server 資料庫角色：<br /><br /> BAMAlertsApplication<br /><br /> BAMAlertsNSMain<br /><br /> BAMPrimaryImport 的 BAM_ManagementWS SQL Server 資料庫角色|  
  
  
## <a name="see-also"></a>另請參閱  
 [資料庫結構與工作](../core/database-structure-and-jobs.md)   
 [MessageBox 資料庫](../core/the-messagebox-database.md)   
 [維護 BizTalk Server](../technical-guides/maintaining-biztalk-server-databases.md)   
 [擴充您的解決方案](../core/scaling-your-solutions.md)   
 [Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [如何變更服務帳戶和密碼](../core/how-to-change-service-accounts-and-passwords.md)