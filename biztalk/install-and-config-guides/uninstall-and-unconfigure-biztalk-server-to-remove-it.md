---
title: 解除安裝並取消設定 BizTalk Server 將它移除 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9ea8757-ca49-421b-bf7b-89344201398a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 704c1f54a01ceb4c4b7b4cd80ad2df6fc34faa68
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976260"
---
# <a name="uninstall-and-unconfigure-biztalk-server-to-remove-it"></a>將 BizTalk Server 解除安裝並取消設定以將其移除
將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解除安裝並取消設定。 
  
##  <a name="BKMK_BeforeYouBegin"></a> 開始之前  
  
-   解除安裝之前，您必須將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 取消設定。  
  
-   本主題列出要刪除的不同作業、套件和資料庫。 列出的名稱是預設名稱。 您的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境可能使用非預設名稱。  
  
-   請依列出的順序完成步驟。 否則，不會完成解除安裝。  
  
##  <a name="BKMK_Unconfigure"></a> 將 BizTalk Server 取消設定  
  
1.  以滑鼠右鍵按一下 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態]，然後選取 [以系統管理員身分執行]。  
  
2.  在 [組態] 中，選取 [取消設定功能]。  
  
3.  選取您要取消設定的功能，然後選取 [確定]。 如果系統提示您繼續，請選取 [是]。 若要移除電腦中的所有項目，您可以選取所有功能。  
  
4.  選取 [下一步]，然後繼續執行精靈。  
  
 會在暫存資料夾中產生記錄檔，類似於︰C:\Users\username\AppData\Local\Temp\ConfigLog(8-29-2016 0h37m59s).log。  
  
##  <a name="BKMK_Uninstall"></a> 解除安裝 BizTalk Server 執行階段元件  
  
1.  開啟 [程式和功能]。  
  
2.  從清單中選取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 版本，然後選取 [解除安裝]。  
  
3.  [移除] 它，然後繼續執行精靈。  
  
 會在暫存資料夾中產生記錄檔，類似於︰C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm  
  
##  <a name="BKMK_UninstallSSO"></a> 解除安裝企業單一登入  
  
1.  開啟 [程式和功能]。  
  
2.  從清單中選取 [Microsoft 企業單一登入]，然後選取 [解除安裝]。  
  
3.  [移除] 它，然後繼續執行精靈。  
  
 會在暫存資料夾中產生記錄檔，類似於︰C:\Users\\*username*\AppData\Local\Setup(083016 xxxxxx).htm  
  
##  <a name="BKMK_RemoveRemaining"></a> 刪除 SQL 作業、資料庫和套件  
  
#### <a name="delete-sql-server-agent-jobs"></a>移除 SQL Server Agent 作業  
  
1.  以系統管理員身分開啟 **SQL Server Management Studio**。  
  
2.  在 [SQL Server Management Studio] 中，連接至 [Database Engine]，並依序展開 [SQL Server Agent] 和 [作業]。  
  
3.  刪除下列作業 (以滑鼠右鍵按一下作業，然後選取 [刪除])：  
  
    -   備份 BizTalk Server (BizTalkMgmtDb)  
  
    -   CleanupBTFExpiredEntriesJob_BizTalkMgmtDb  
  
    -   DTA 清除與封存 (BizTalkDTADb)  
  
    -   MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_Message_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb  
  
    -   MessageBox_Parts_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_UpdateStats_BizTalkMsgBoxDb  
  
    -   監控 BizTalk Server (BizTalkMgmtDb)  
  
    -   Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb  
  
    -   PurgeSubscriptionsJob_BizTalkMsgBoxDb  
  
    -   Rules_Database_Cleanup_BizTalkRuleEngineDb  
  
    -   TrackedMessages_Copy_BizTalkMsgBoxDb  
  
        > [!NOTE]
        >  如果您部署 BAM 時，您可能也需要移除 bam_\<*Cube 名稱*\>_\<*檢視名稱*\>作業。  
  
#### <a name="delete-biztalk-server-databases"></a>刪除 BizTalk Server 資料庫  
  
1.  在 [物件總管] 中，展開 [資料庫]。  
  
2.  刪除下列資料庫 (以滑鼠右鍵按一下資料庫，然後選取 [刪除])：  
  
    -   BAMArchive  
  
    -   BAMPrimaryImport  
  
    -   BAMStarSchema  
  
    -   BizTalkDTADb  
  
    -   BizTalkMgmtDb  
  
    -   BizTalkMsgBoxDb  
  
    -   BizTalkRuleEngineDb  
  
    -   SSODB  
  
#### <a name="remove-sql-server-integration-services-packages"></a>移除 SQL Server Integration Services 套件  
  
1.  在 [物件總管] 中，[連接] 至 [Integration Services]。  
  
2.  依序展開 [存放的套件] 和 [MSDB]。  
  
3.  刪除具有下列前置詞的套件 (以滑鼠右鍵按一下套件，然後選取 [刪除])：  
  
    -   BAM_AN_\<*Cube 名稱*\>  
  
    -   BAM_DM_\<*檢視名稱*\>  
  
