---
title: 從 BizTalk 追蹤資料庫清除資料 |Microsoft 文件
description: 設定要清除追蹤資料庫 (BizTalkDTADB) 在 BizTalk Server 中的 dtasp_PurgeTrackingDatabase 預存程序
ms.custom: ''
ms.date: 10/11/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06217a7d5012eb402698ad35e76ccfc886952f6e
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "23129703"
---
# <a name="purge-data-from-the-biztalk-tracking-database"></a>從 BizTalk 追蹤資料庫清除資料
當您從「BizTalk 追蹤」(BizTalkDTADb) 資料庫清除資料時，「DTA 清除和封存」工作會從「BizTalk 追蹤」(BizTalkDTADb) 資料庫清除不同類型的追蹤資訊，例如訊息與服務執行個體資訊、協調流程事件資訊以及規則引擎追蹤資料。  
  
> [!IMPORTANT]
>  使用此程序不會封存「BizTalk 追蹤」(BizTalkDTADb) 資料庫。  
  
> [!WARNING]
>  在未啟用追蹤的情況下，如果在協調流程中攔截並處理例外狀況，則具有「已啟動」狀態及例外狀況資訊的孤立的追蹤執行個體可能會插入「BizTalk 追蹤」(BizTalkDTADb) 資料庫。 清除資料庫之後，這項記錄將會保留下來。  
  
## <a name="prerequisites"></a>필수 구성 요소  
使用 SQL Server sysadmin 固定伺服器角色的成員，才能執行此程序的帳戶登入。  
  
## <a name="purge-data-from-the-biztalk-tracking-database"></a>從 BizTalk 追蹤資料庫清除資料  
  
1.  在裝載 「 BizTalk 追蹤 (BizTalkDTADb) 資料庫伺服器上開啟 **SQL Server Management Studio**。 
  
2.  在 **連接到伺服器**, ，輸入 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL server 的名稱、 輸入驗證類型，然後選取 **連接** 連接到 SQL server。 
  
3.  按兩下**SQL Server Agent**，然後選取**作業**。  
  
4.  在**物件總管詳細資料**，以滑鼠右鍵按一下**DTA 清除與封存 (BizTalkDTADb)**，然後選取**屬性**。  
  
5.  在**作業屬性-DTA 清除與封存 (BizTalkDTADb)** 下**選取頁面**，選取**步驟**。  
  
6.  在**作業步驟清單**，選取**封存及清除**，然後選取**編輯**。  
  
7.  在**作業步驟屬性-封存與清除**上**一般**頁面上，於**命令**方塊中，變更**exec dtasp_BackupAndPurgeTrackingDatabase**至**exec dtasp_PurgeTrackingDatabase**。  
  
    > [!CAUTION]
    >  **Exec dtasp_PurgeTrackingDatabase** 預存程序不會封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫。 使用此選項前，請確定您已不需要封存的追蹤資料。  
  
8.  在**命令**方塊中，更新下列參數，並選取**確定**。  
  
    -   @nHours tinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。  
  
    -   @nDays tinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。 預設間隔是 1 天。  
  
    -   @nHardDays tinyint —，也將會刪除早於此日期的所有資料，即使資料不完整。 為 HardDeleteDays 指定的時間間隔應該大於資料存留窗期。 資料存留窗期是您想要在 BizTalk 追蹤 (BizTalkDTADb) 資料庫中維護追蹤資料的時間。 早於此間隔的資料都將在下次封存時進行封存，然後再予以清除。  
  
    -   @dtLastBackup — 請設為 **Getutcdate** 從 BizTalk 追蹤 (BizTalkDTADb) 資料庫清除資料。 當設定為 **NULL**, ，不會從資料庫清除資料。  

    -  @fHardDeleteRunningInstances int-預設值為 0。 設定為 1 時，刪除所有執行中服務執行個體早於@nHardDeleteDays值。  
    
        > [!NOTE] 
        > @fHardDeleteRunningInstances屬性是從開始提供[BizTalk Server 2016 的累計更新 1年](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016)， [BizTalk Server 2013 R2 累計更新 6年](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2)，和[BizTalk Server 2013 累計更新 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013)。   

    您已編輯的指令碼看起來如下所示：  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup, 1  
    ```  
    
9. 在**作業屬性-DTA 清除與封存 (BizTalkDTADb)** 對話方塊的 **選取頁面**，選取**一般**，選取**啟用**核取方塊，然後再選取**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)
