---
title: 資料庫結構與工作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PurgeSubscriptionsJob_BizTalkMsgBoxDb job
- MessageBox database, jobs [SQL Server Agent]
- DTA Purge and Archive (BizTalkDTADb) job
- TrackedMessages_Copy_BizTalkMsgBoxDb job
- MessageBox_Message_Cleanup_BizTalkMsgBoxDb job
- MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job
- Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], MessageBox database
- CleanupBTFExpiredEntriesJob_BizTalkMgmtDb job
- databases, structure
- Tracking database, jobs [SQL Server Agent]
- jobs [SQL Server Agent], Management database
- Backup BizTalk Server (BizTalkMgmtDb) job
- databases, SQL Server Agent jobs
- Business Rules Engine, jobs [SQL Server Agent]
- jobs, databases
- Management database, jobs [SQL Server Agent]
- MessageBox_UpdateStats_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], Business Rules Engine
- Rules_Database_Cleanup_BizTalkRuleEngineDb job
- MessageBox_Parts_Cleanup_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], Tracking database
- MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb job
ms.assetid: f5f6b17d-0f5e-4821-a7eb-c345234ffc65
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf98ef7fe236261fd3ee65ac6f4695455ba8c704
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240558"
---
# <a name="database-structure-and-jobs"></a>資料庫結構與工作
本主題討論 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的資料庫結構與資料庫工作。  
  
## <a name="database-write-diagram"></a>資料庫寫入圖  
 下圖顯示寫入 BizTalk Server 資料庫的程序和實體。  
  
 ![寫入 BizTalk Server 資料庫的處理序](../core/media/ebiz-ops-backup.gif "ebiz_ops_backup")  
  
        Database write diagram showing the processes and entities that write to the BizTalk Server databases  
  
## <a name="biztalk-server-database-jobs"></a>BizTalk Server 資料庫工作  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 內附下列 SQL Server Agent 工作，以協助您管理 BizTalk Server 資料庫：  
  
> [!NOTE]
>  工作名稱可根據組態期間指定的資料庫名稱來變更。 若您在環境中部署多個 MessageBox 資料庫，每個 MessageBox 將會有數個工作。  
  
> [!WARNING]
>  在 BizTalk 管理 (BizTalkMgmtDb) 資料庫中，沒有名為預存程序**adm_CleanupMgmtDB**。 **無法執行此預存程序 ！** 如果您真的執行這個預存程序，資料庫中的所有項目都會遭到刪除。  
  
|作業|Description|  
|---------|-----------------|  
|備份 BizTalk Server (BizTalkMgmtDb)|這個工作會執行 BizTalk Server 資料庫的完整資料庫和記錄備份。 如需有關設定和執行這項作業的詳細資訊，請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)。|  
|CleanupBTFExpiredEntriesJob_BizTalkMgmtDb|這個工作會清除 BizTalk 管理 (BizTalkMgmtDb) 資料庫中過期的 BizTalk Framework (BTF) 項目。|  
|DTA 清除與封存 (BizTalkDTADb)|這個工作會自動封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫中的資料，並清除過期資料。 如需有關設定和執行這項作業的詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。|  
|MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb|這個工作會偵測出 BizTalk Server 主控件執行個體 (NT 服務) 何時停止，並釋放出該主控件執行個體所即將完成的所有工作，如此即可由另一個主控件執行個體來作業。|  
|MessageBox_Message_Cleanup_BizTalkMsgBoxDb|這個工作會移除在 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫資料表中任何訂閱者所不再參考的所有訊息。 **注意：** 這是由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作所啟動的未排程的作業。 請勿手動啟動這個工作。|  
|MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb|這個工作會管理訊息的參考計數記錄，並決定訊息何時不再被任何訂閱者所參考。 **注意：** 即使這個 SQL Server Agent 作業已排程執行每分鐘，這項作業會呼叫預存程序包含邏輯，以確保持續執行的預存程序之後。 此行為是經過設計的，不可修改。|  
|MessageBox_Parts_Cleanup_BizTalkMsgBoxDb|這個工作會移除在 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫資料表中任何訊息所不再參考的所有訊息部分。 所有訊息皆是由一或多個訊息部分所組成，這些訊息部分會包含實際訊息資料。|  
|MessageBox_UpdateStats_BizTalkMsgBoxDb|這個工作會手動更新 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫的統計資料。|  
|監控 BizTalk Server|這項作業會掃描 BizTalkMgmtDb、 BizTalkMsgBoxDb 和 BizTalkDTADb 資料庫的任何已知的問題，包括被遺棄使用者執行個體。|  
|Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb|此為多個 MessageBox 部署的必要工作。 它會在變更已套用到附屬 MessageBox 之後，於主要 MessageBox 上非同步執行像是大量終止這類的作業動作。|  
|PurgeSubscriptionsJob_BizTalkMsgBoxDb|這個工作會從 BizTalk Server MessageBox (BizTalkMsgBoxDb) 資料庫清除未使用的訂閱述詞。|  
|Rules_Database_Cleanup_BizTalkRuleEngineDb|這個動作每 90 天就會自動從規則引擎 (BizTalkRuleEngineDb) 資料庫清除舊的稽核資料。 另外，這個動作每 3 天就會從規則引擎 (BizTalkRuleEngineDb) 資料庫清除舊的歷程記錄資料 (部署/解除部署通知)。|  
  
## <a name="see-also"></a>另請參閱  
 [傳訊引擎](../core/the-messaging-engine.md)