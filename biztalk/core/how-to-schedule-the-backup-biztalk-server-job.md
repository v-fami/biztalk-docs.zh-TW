---
title: "如何排程 「 備份 BizTalk Server 」 工作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, scheduling
- backing up, backup jobs
- scheduling, backup jobs
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d6b40ae933874e1c25cb3a93dbbeab514ef5dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-schedule-the-backup-biztalk-server-job"></a>如何排程備份 BizTalk Server 作業
備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業執行依排程由 SQL Server Agent 服務。 如果您想要建立較頻繁或較不頻繁的備份，您可以使用 SQL Server Management Studio 來變更「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業的排程。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-schedule-the-backup-biztalk-server-job-sql-server-2008"></a>若要排程備份 BizTalk Server 作業 (SQL Server 2008)  
  
1.  包含 BizTalk 管理資料庫的電腦，按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **Microsoft SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，指定位於 BizTalk Server 資料庫所在的 SQL server 的名稱以及適當的驗證類型，然後按一下 **連接**。  
  
3.  在 物件總管 中，按兩下**SQL Server Agent**，然後按一下 **作業**。  
  
4.  在詳細資料窗格中，以滑鼠右鍵按一下**備份 BizTalk Server (BizTalkMgmtDb)**，然後按一下 **屬性**。  
  
5.  在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**對話方塊的 **選取頁面**，按一下 **步驟**。  
  
6.  在**作業步驟清單**，按一下  **BackupFull**，然後按一下 **編輯**。  
  
7.  在**作業步驟屬性-BackupFull**對話方塊中，於**命令**方塊中，將頻率變更成要執行完整備份的所需間隔來編輯命令： **'h'**（每小時）、**有 '** （每天）、 **'w'** （每週）、 **am'** （每月） **'y'** （每年），然後按一下**[確定]**.  
  
    > [!NOTE]
    >  第一次的「備份 BizTalk Server」工作會在新週期中執行，並且會進行完整備份。  
  
8.  在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**對話方塊的 **選取頁面**，按一下 **排程**。  
  
9. 在**排程清單**，按一下  **MarkAndBackupLogSched**，然後按一下 **編輯**。  
  
10. 在**作業排程屬性-markandbackuplogsched**對話方塊中的，在 排程類型 選取**週期性**從下拉式清單方塊 （如果尚未選取）。  
  
     依照預設，作業將排程為每 15 分鐘執行一次。  
  
11. 視需要排程的更新，然後按一下**確定**。  
  
    > [!NOTE]
    >  如需有關排程 SQL Server Agent 作業的詳細資訊，請參閱 「[排程作業](http://go.microsoft.com/fwlink/?LinkId=195887)。 」  
  
12. 在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**對話方塊中，按一下 **確定**。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [如何設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [如何還原資料庫](../core/how-to-restore-your-databases.md)   
 [備份和還原的相關進階的資訊](../core/advanced-information-about-backup-and-restore1.md)