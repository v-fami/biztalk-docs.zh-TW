---
title: "如何設定 DTA 的清除與封存工作 |Microsoft 文件"
ms.custom: 
ms.date: 2015-11-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- purging, configuring
- DTA Purge and Archive job, configuring
- archiving [Tracking database], DTA Purge and Archive job
- archiving [Tracking database], configuring
- purging, DTA Purge and Archive job
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f4985e657f26945aa2fdc168b273dbfdb159efc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-dta-purge-and-archive-job"></a>如何設定 DTA 的清除與封存工作
您必須先設定 DTA 的清除與封存 (BizTalkDTADb) 工作，才能封存或清除「BizTalk 追蹤」(BizTalkDTADb) 資料庫的資料。 這項作業會設定為呼叫 dtasp_BackupAndPurgeTrackingDatabase 預存程序，它會使用六個參數，您必須設定。  
  
## <a name="prerequisites"></a>必要條件  
 您必須是 SQL Server sysadmin 固定伺服器角色的成員，才能依照這些步驟的帳戶登入。  
  
### <a name="to-configure-the-dta-purge-and-archive-job"></a>若要設定 DTA 的清除與封存工作  
  
1.  在裝載 「 BizTalk 追蹤 (BizTalkDTADb) 資料庫的 SQL Server 上開啟**SQL Server Management Studio**。  
  
2.  在**連接到伺服器**，輸入 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL server 的名稱、 輸入驗證類型，然後選取**連接**連接到 SQL server。  
  
3.  在**Microsoft SQL Server Management Studio**，連按兩下**SQL Server Agent**，然後按一下 **作業**。  
  
4.  在**物件總管詳細資料**] 窗格中，以滑鼠右鍵按一下**DTA 清除與封存 (BizTalkDTADb)**，然後按一下 [**屬性**。  
  
5.  在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，按一下 **步驟**。  
  
6.  在**作業步驟清單**，按一下 **封存及清除**，然後按一下 **編輯**。  
  
7.  在**一般**頁面上，於**命令**方塊中，編輯適當的下列參數，然後按一下**確定**。  
  
    -   @nLiveHourstinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。 這是必要的參數沒有預設值。  
  
    -   @nLiveDaystinyint — 任何已完成執行個體超過 （生效小時） + （生效天數） 將會刪除連同所有相關資料。 預設間隔為 0 天。  
  
        > [!NOTE]
        >  基於 BizTalk 追蹤 (BizTalkDTADb) 資料庫的目的，LiveHours 加上 LiveDays 的總和是您要在 BizTalk Server 環境中維持的資料存留窗期。 存留時間超過資料存留窗期之已完成執行個體的所有相關資料都會被刪除。  
  
    -   @nHardDeleteDaystinyint — 所有資料 （即使未完成） 早於這將會被刪除。 為 HardDeleteDays 指定的時間間隔應該大於資料存留窗期。 資料存留窗期是您想要在 BizTalk 追蹤 (BizTalkDTADb) 資料庫中維護追蹤資料的時間。 早於此間隔的資料都將在下次封存時進行封存，然後再予以清除。 預設值為 0 天。  
  
    -   @nvcFoldernvarchar （1024) — 放置備份檔案的資料夾。 這是必要的參數沒有預設值。  
  
    -   @nvcValidatingServersysname — 將完成驗證的伺服器。 NULL 值表示沒有完成任何驗證。 預設值是 NULL。  
  
    -   @fForceBackupint — 預設值為 0。 這被保留供未來使用。  
  
     編輯後的命令看起來應該如下所示。 在下列範例中，還有 1 小時的即時視窗和硬清除 1 天：  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0  
    ```  
  
8.  在**作業屬性-DTA 清除與封存 (BizTalkDTADb)**對話方塊的 **選取頁面**，按一下 **一般**，選取**啟用**核取方塊，然後**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)