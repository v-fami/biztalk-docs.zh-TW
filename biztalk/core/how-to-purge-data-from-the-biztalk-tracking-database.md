---
title: "如何從 BizTalk 追蹤資料庫清除資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- purging
- DTA Purge and Archive job, purging data
- purging, DTA Purge and Archive job
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01c56629aaa0934010ba79637b4e4a134bf29f26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-purge-data-from-the-biztalk-tracking-database"></a>如何從 BizTalk 追蹤資料庫清除資料
當您從「BizTalk 追蹤」(BizTalkDTADb) 資料庫清除資料時，「DTA 清除和封存」工作會從「BizTalk 追蹤」(BizTalkDTADb) 資料庫清除不同類型的追蹤資訊，例如訊息與服務執行個體資訊、協調流程事件資訊以及規則引擎追蹤資料。  
  
> [!IMPORTANT]
>  使用此程序不會封存「BizTalk 追蹤」(BizTalkDTADb) 資料庫。  
  
> [!WARNING]
>  在未啟用追蹤的情況下，如果在協調流程中攔截並處理例外狀況，則具有「已啟動」狀態及例外狀況資訊的孤立的追蹤執行個體可能會插入「BizTalk 追蹤」(BizTalkDTADb) 資料庫。 清除資料庫之後，這項記錄將會保留下來。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-purge-data-from-the-biztalk-tracking-database"></a>若要從 BizTalk 追蹤資料庫清除資料  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，指定 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL Server 和適當的驗證類型的名稱，然後按一下**連接**至連接到 SQL Server。  
  
3.  在**Microsoft SQL Server Management Studio**，連按兩下**SQL Server Agent**，然後按一下 **作業**。  
  
4.  在**物件總管詳細資料**] 窗格中，以滑鼠右鍵按一下**DTA 清除與封存 (BizTalkDTADb)**，然後按一下 [**屬性**。  
  
5.  在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，按一下 **步驟**。  
  
6.  在**作業步驟清單**，按一下 **封存及清除**，然後按一下 **編輯**。  
  
7.  在**作業步驟屬性-封存與清除**對話方塊**一般**頁面上，於**命令**方塊中，變更**exec dtasp_BackupAndPurgeTrackingDatabase**至**exec dtasp_PurgeTrackingDatabase**。  
  
    > [!CAUTION]
    >  **Exec dtasp_PurgeTrackingDatabase**預存程序不會封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫。 使用此選項前，請確定您已不需要封存的追蹤資料。  
  
8.  在**命令**方塊中，編輯適當的下列參數，然後按一下**確定**。  
  
    -   @nHourstinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。  
  
    -   @nDaystinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。 預設間隔是 1 天。  
  
    -   @nHardDaystinyint —，也將會刪除早於此日期的所有資料，即使資料不完整。 為 HardDeleteDays 指定的時間間隔應該大於資料存留窗期。 資料存留窗期是您想要在 BizTalk 追蹤 (BizTalkDTADb) 資料庫中維護追蹤資料的時間。 早於此間隔的資料都將在下次封存時進行封存，然後再予以清除。  
  
    -   @dtLastBackup— 將此設**getutcdate （)**從 BizTalk 追蹤 (BizTalkDTADb) 資料庫清除資料。 當設定為**NULL**，不會從資料庫清除資料。  
  
     編輯過的指令碼看起來應該類似下例：  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup  
    ```  
  
9. 在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，按一下 **一般**，選取**啟用**核取方塊，然後**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)