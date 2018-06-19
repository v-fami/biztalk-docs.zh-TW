---
title: 排程備份 BizTalk Server 作業 |Microsoft 文件
description: 設定備份 BizTalk Server 的工作參數，並將排程設定為執行每月、 每週、 日或每小時
ms.custom: ''
ms.date: 11/02/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f09ca97f65605ac3bf427d1c1fcc322a14feb53
ms.sourcegitcommit: 9aaed443492b74729171fef79c634bff561af929
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2017
ms.locfileid: "23980750"
---
# <a name="schedule-the-backup-biztalk-server-job"></a>排程備份 BizTalk Server 作業
備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業執行依排程由 SQL Server Agent 服務。 如果您想要建立較頻繁或較不頻繁的備份，您可以使用 SQL Server Management Studio 來變更「備份 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]」作業的排程。  
  
## <a name="prerequisites"></a>必要條件  
使用 SQL Server sysadmin 固定伺服器角色的成員帳戶登入。  
  
## <a name="schedule-the-backup-biztalk-server-job"></a>排程備份 BizTalk Server 作業
  
1.  在裝載 BizTalk 管理資料庫的 SQL Server 上開啟**SQL Server Management Studio**。

2.  在**連接到伺服器**，輸入 BizTalk Server 資料庫位於，在其中選取驗證類型的 SQL server 名稱，然後**連接**。  
  
3.  在 [物件總管] 中，按兩下**SQL Server Agent**，然後選取**作業**。  
  
4.  在詳細資料窗格中，以滑鼠右鍵按一下**備份 BizTalk Server (BizTalkMgmtDb)**，然後選取**屬性**。  
  
5.  在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)** 下**選取頁面**，選取**步驟**。  
  
6.  在**作業步驟清單**，選取**BackupFull**，然後選取**編輯**。  
  
7.  在**作業步驟屬性-BackupFull**，請在**命令**方塊中，藉由變更要執行完整備份的頻率更新命令： **'h'** （每小時）、**有 '** （每天）、 **'w'** （每週）、 **am'** （每月）、 **'y'** （每年）。 選取 [確定]。  
  
    > [!NOTE]
    >  「 備份 BizTalk Server 」 工作執行時，第一次此作業完成的完整備份。  
    
8.  設定其他 **@frequency** 參數：  
  
    - **@ForceFullBackupAfterPartialSetFailure**： 預設值是**false**。 當**false**，如果完整備份失敗，系統會等到下一個循環，直到建立完整備份為止。  
    
        > [!NOTE]
        >  如果您 **@frequency** 設定長時間 （例如每週、 每月、 每年），然後將這個參數設定**false**可能會有風險。 在此案例中，可能是最佳這個旗標設為**true**。 當**true**每次失敗，系統會強制其本身，以建立完整備份。 可能有小方面的影響，但它是 safter 具有可復原的系統。
  
    - **@BackupHour**: 預設值 NULL。 此參數直接相關 **@Frequency** 。 當您將頻率設**h** （每小時），您設定要執行完整備份當天的小時。 您可以選擇介於 0 （午夜） 到 23 （晚上 11 點） 之間的值。 如果保留空白，每小時執行完整備份。  
    
       > [!NOTE]
        >  如果您設定此參數以數字 0 到 23 的範圍 （例如，100，則為-1） 以外，系統會強制其設為 0。
  
    - **@UseLocalTime**： 一種額外的參數，使用本地時間表示。 根據預設，工作會使用 UTC 時間。 因此如果您住在澳洲 （此為 UTC + 10 小時），您的備份會在上午 10，而不是午夜執行。 最佳做法，建議您將此設**1** (true)。  
  
9.  在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)** 下**選取頁面**，按一下 **排程**。  
  
10. 在**排程清單**，按一下  **MarkAndBackupLogSched**，然後按一下 **編輯**。  
  
11. 在**作業排程屬性-markandbackuplogsched**，在 排程類型 選取**週期性**從下拉式清單。  
  
     依照預設，作業將排程為每 15 分鐘執行一次。  
     
    > [!NOTE]
    >  您可以變更此值，根據您的需求，但是在非生產環境中的第一個測試。 頻繁的備份中將此值太低的結果，並將新增至您的 SQL 環境中的背景載入。 設定太高的值可能會增加交易記錄的大小，並影響效能。 在某些情況下，建議保留預設值。    
  
12. 更新排程，如有需要，，然後選取 **確定**。  
  
    > [!NOTE]
    >  [排程作業](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job)提供更多詳細資料。
  
13. 在**作業屬性-備份 BizTalk Server (BizTalkMgmtDb)**，按一下 **確定**。  
  
## <a name="more-good-stuff"></a>更多實用功能  
 [設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [設定記錄傳送的目的系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [還原資料庫](../core/how-to-restore-your-databases.md)   
 [備份和還原的進階資訊](../core/advanced-information-about-backup-and-restore1.md)
