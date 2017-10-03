---
title: "備份和還原 BizTalk Server 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up [BAM]
- databases, backing up
- databases, restoring
- backing up, restoring
- backing up, databases
- restoring, BAM
- backing up, BAM
- backing up, backup jobs
- BAM, restoring
- restoring, databases
- restoring [BAM]
- BAM, backing up
ms.assetid: 82fc1af2-1389-4c79-80dc-f2df5656d201
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dba0e9e7cb5d01bf845eaa4adf3557dc3b6ea34a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-biztalk-server-databases"></a>備份和還原 BizTalk Server 資料庫
除了商務活動監控 (BAM) 使用的部分資料庫是例外之外，您要使用「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」工作來備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來源系統中的所有資料庫。 來源系統是包含即時資料的伺服器或伺服器群組。 BAM 資料庫由於有不同的備份和還原需求，因此要使用其他方法來備份和還原。  
  
 備份和還原 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫包含下列步驟：  
  
1.  **設定 「 備份 BizTalk Server 」 工作**  
  
     在備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫之前，您必須先在來源系統上設定「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」工作，這會自動引導系統將備份寫入資料夾，往後便可在此資料夾中使用這些備份在目的系統上還原資料庫。 目的系統是將用來還原來源系統所產生的資料庫備份之伺服器或伺服器群組。 如需有關此步驟的詳細資訊，請參閱[如何設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md)。  
  
2.  **設定目的系統以進行記錄傳送**  
  
     您也必須設定目的系統以進行記錄傳送，當發生系統失敗時，便能提供待命伺服器功能並減少停機時間。 如需有關此步驟的詳細資訊，請參閱[如何設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)。  
  
3.  **還原資料庫**  
  
     發生硬體失敗時，您可以使用傳送到目的系統的備份和記錄來還原您的資料庫。 如需有關此步驟的詳細資訊，請參閱[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。  
  
## <a name="biztalk-server-databases"></a>BizTalk Server 資料庫  
 下表描述 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用的資料庫，並指示用來備份資料庫的方法。  
  
### <a name="databases-backed-up-by-the-backup-biztalk-server-job"></a>由備份 BizTalk Server 工作備份的資料庫  
 下表列出「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」工作會備份和還原的資料庫。 您可以修改「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」工作，藉由將自訂資料庫新增到 adm_OtherBackupDatabases 資料表來備份它們。 如需詳細資訊，請參閱[如何備份自訂資料庫](../core/how-to-back-up-custom-databases.md)。  
  
|資料庫|預設資料庫名稱|Description|  
|--------------|---------------------------|-----------------|  
|BAM 主要匯入資料庫|BAMPrimaryImport|這是商務活動監控 (BAM) 收集原始追蹤資料的資料庫。|  
|BAM Notification Services 應用程式資料庫|BAMAlertsApplication|這個資料庫包含 BAM 通知的警示資訊。 例如，當您使用 BAM 入口網站建立警示時，就會在資料庫中插入項目以指定與警示相關的條件和事件，以及警示的其他支援資料項目。|  
|BAM Notification Services 執行個體資料庫|BAMAlertsNSMain|這個資料庫包含執行個體資訊，指定通知服務連接到 BAM 正在監控之系統的方法。|  
|BizTalk 追蹤資料庫|BizTalkDTADb|這個資料庫儲存了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 追蹤引擎所追蹤的狀況監控資料。|  
|BizTalk 管理資料庫|BizTalkMgmtDb|這個資料庫是所有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行個體的中央中繼資訊存放區。|  
|BizTalk MessageBox 資料庫|BizTalkMsgBoxDb|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎使用這個資料庫進行路由、排入佇列、執行個體管理及其他不同的工作。|  
|規則引擎資料庫|BizTalkRuleEngineDb|這個資料庫是下列項目的儲存機制：<br /><br /> -原則，也就是相關規則的集合。<br />-詞彙，規則中關於資料參考的使用者易記、 網域特定名稱的集合。|  
|SSO 資料庫|SSODB|這個「企業單一登入」資料庫會安全地儲存接收位置的組態資訊。|  
  
### <a name="databases-backed-up-by-the-bam-backup-process"></a>由 BAM 備份程序備份的資料庫  
 下表列出的資料庫備份及還原使用中的程序的[備份和還原 BAM](../core/backing-up-and-restoring-bam.md):  
  
|資料庫|預設資料庫名稱|Description|  
|--------------|---------------------------|-----------------|  
|BAM 星狀結構描述|BAMStarSchema|這個資料庫含有臨時資料表以及量值和維度資料表。|  
|BAM 分析|BAMAnalysis|這個資料庫含有可供線上及離線分析使用的 BAM OLAP Cube。|  
|BAM 封存|BAMArchive|這個資料庫會封存舊的商務活動資料。 建立 BAM 封存資料庫可將 BAM 主要匯入資料庫中的商務活動資料累積降到最低。|  
|追蹤 Analysis Server|BizTalkAnalysisDb|這個資料庫會儲存狀況監控線上分析處理 (OLAP) Cube。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何設定備份 BizTalk Server 作業](../core/how-to-configure-the-backup-biztalk-server-job.md)  
  
-   [如何設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)  
  
-   [如何還原資料庫](../core/how-to-restore-your-databases.md)  
  
-   [如何備份和還原 SQL 代理程式作業](../core/how-to-back-up-and-restore-sql-agent-jobs.md)  
  
-   [如何備份和還原 SQL Server 登入](../core/how-to-back-up-and-restore-sql-server-logins.md)