---
title: "如何備份和還原 SQL 代理程式作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82fc5a5-5ea5-476c-bed1-c5d41a50e673
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 253055f9a45dfdb9864d4d5202661e750d28b1b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-and-restore-sql-agent-jobs"></a>如何備份和還原 SQL 代理程式作業
本主題描述如何備份和還原 SQL Server Agent 作業。 您在設定之後，您應該先備份您的 SQL 作業。  
  
## <a name="biztalk-server-jobs"></a>BizTalk Server 作業  
 下列的 SQL Server Agent 作業會與 BizTalk Server 關聯。 安裝在每一部伺服器上的作業會安裝及設定的功能而有所不同。 大部分的這些作業會在 BizTalk Server 安裝期間建立。 設定記錄傳送時，會建立數個項目。  
  
-   備份 BizTalk Server (BizTalkMgmtDb)  
  
-   CleanupBTFExpiredEntriesJob_BizTalkMgmtDb  
  
-   DTA 清除與封存 (BizTalkDTADb)  
  
-   MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_Message_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb  
  
-   MessageBox_Parts_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_UpdateStats_BizTalkMsgBoxDb  
  
-   Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb  
  
-   PurgeSubscriptionsJob_BizTalkMsgBoxDb  
  
-   Rules_Database_Cleanup_BizTalkRuleEngineDb  
  
-   TrackedMessages_Copy_BizTalkMsgBoxDb  
  
-   BTS 記錄傳送取得備份歷程記錄  
  
-   BTS 記錄傳送還原資料庫  
  
-   BTS 記錄傳送還原為標示  
  
## <a name="back-up-a-job-using-a-script"></a>備份作業，使用指令碼  
  
1.  開啟**SQL Server Management Studio**。  
  
2.  展開 [SQL Server Agent] ，再展開 [作業] 。  
  
3.  以滑鼠右鍵按一下您想要建立的備份指令碼，然後再選取的作業**與指令碼工作**。  
  
4.  選取**CREATE 至**或**DROP To**，然後選取**新增查詢編輯器視窗**，**檔案**，或**剪貼簿**若要選取指令碼的目的地。 通常，目的地是檔案之**.sql**延伸模組。  
  
5.  重複此程序，從步驟 3 的每個您要編寫指令碼的工作。 清單，請參閱 BizTalk Server 的相關工作，以判斷其作業您需要指令碼。  
  
     最少，您應該先備份**備份 BizTalk Server (BizTalkMgmtDb)**作業之後設定。  
  
## <a name="restore-a-job-from-a-script"></a>還原作業，從指令碼  
  
1.  開啟**SQL Server Management Studio**。  
  
2.  在**檔案**功能表上，**開啟**包含已編寫指令碼的工作的檔案。  
  
3.  執行指令碼來建立作業。  
  
## <a name="next-steps"></a>後續步驟  
 [如何備份和還原 SQL Server 登入](../core/how-to-back-up-and-restore-sql-server-logins.md)