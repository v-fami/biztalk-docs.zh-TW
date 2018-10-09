---
title: 還原您的資料庫 |Microsoft Docs
description: 請參閱還原 BizTalk Server 資料庫，包括使用 SQL Agent 作業，並執行 UpdateDatabase.vbs 及 UpdateRegistry.vbs 指令碼的步驟。 另請參閱還原資料庫，包括 SQL Server 執行個體名稱，在 BizTalk 管理主控台中更新後，該怎麼辦。
ms.custom: ''
ms.date: 09/30/18
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0176932a-6b3d-4502-975b-a76296189092
caps.latest.revision: 52
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c318511902b31ffbe3fab4e055bdbf097d0f6865
ms.sourcegitcommit: 51ce182c5b71d3999a3920dd884bc9ec8334a899
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48575681"
---
# <a name="how-to-restore-your-databases"></a>如何還原資料庫
您必須將所有資料庫還原為相同的標記，以確保資料庫間的交易狀態一致。 請參閱[Marked Transactions，Full Backups，and 記錄備份](../core/marked-transactions-full-backups-and-log-backups.md)。  
  
 如果目的系統中只有一個伺服器，請確認已還原所有記錄檔備份集 (除了最新的記錄檔備份集以外)。 請參閱[檢視的記錄備份還原](../core/viewing-the-history-of-restored-backups.md)。 如果尚未還原所有記錄檔備份集，且目前沒有執行還原作業，請執行還原作業 (如果需要，請以手動執行)。 如果有可還原的未完成備份集，此作業會處理這些備份集，直到全部都還原為止。  
  
 如果目的系統中有多部伺服器，必須將所有伺服器還原為相同的備份集。 檢視每部伺服器上的還原記錄，同時確認所有伺服器上最近所還原的記錄檔備份集皆相同。 否則，您必須在每部需要還原最新記錄檔備份集的伺服器上，手動執行還原作業。  
  
 當所有伺服器都位在相同的備份集後，便可手動還原最後的備份集。  
  
 adm_BackupHistory 資料表是來源系統中記錄檔傳送程序的中央歷程記錄點。 所有執行的備份工作都會記錄到這個資料表中。 您目的系統中的所有伺服器都會讀取這個資料表，以接收執行其還原工作所需的資訊。  
  
> [!NOTE]
>  - 如果您是從備份還原「BAM 主要匯入」資料庫，那麼您也應該使用比 BAM 主要備份還舊的備份，來還原「BAM 封存」、「BAM 星狀結構描述」及「BAM 分析」資料庫。 請參閱[Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)。  
>  - 如果您要從「備份 BizTalk Server」工作放置來源資料庫之完整或記錄檔備份的位置移動它們，就應該透過在目的系統的 bts_LogShippingDatabases 資料表中，將 LogFileLocation 或 DBFileLocation 設定為目的系統應該讀取完整/記錄檔備份檔案的新位置，更新該資料庫的相關聯資料列。 當您執行 bts_ConfigureBtsLogShipping 預存程序時，便會填入此資料表。 依照預設，會將這些資料行設為空值，這表示目的系統應該從 adm_BackupHistory 資料表中儲存的位置讀取備份檔案。  
>  - 請務必在安全的位置保留備份檔案的複本。 即使您擁有記錄檔備份，也無法在沒有備份檔案的情況下還原資料庫。  
  
## <a name="prerequisites"></a>先決條件  
 使用系統管理員 SQL Server 角色之成員的帳戶登入 SQL Server。  
  
## <a name="restore-your-databases"></a>還原資料庫  
  
1. 在目的地系統上，開啟**SQL Server Management Studio**，並連接到您的 SQL Server。  
  
2. 展開 [SQL Server Agent] ，再展開 [作業] 。 請執行下列動作：  
  
   1. 在 **BTS 記錄傳送 - 取得備份記錄** 作業上按一下滑鼠右鍵，然後選取 [停用] 。 狀態會變更為「成功」。  
  
   2. 在 **BTS 記錄傳送 - 還原資料庫** 作業上按一下滑鼠右鍵，然後選取 [停用] 。 狀態會變更為「成功」。  
  
   3. 在 **BTS 檔記錄傳送 - 還原為標示** 上按一下滑鼠右鍵，然後選取 [從下列步驟啟動作業] 。 選取 [步驟 ID 1]  ，然後選取 [開始] 。  
  
       當狀態變更為**成功**，SQL Server Agent 作業和 BizTalk Server 資料庫還原至目的地系統。  
  
   > [!IMPORTANT]
   >  若 **狀態** 為「錯誤」，請選取 [訊息] 欄位中的連結判斷原因。 這些作業的狀態必須都是成功才能繼續。  
  
3. 在 BizTalk 伺服器上編輯 SampleUpdateInfo.xml 檔案的位置，開啟命令提示字元，並移至：  
  
    32 位元電腦： `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
    64 位元電腦： `%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`  
  
4. 在命令提示字元中，輸入：  
  
    `cscript UpdateDatabase.vbs SampleUpdateInfo.xml`  
  
    這個指令碼會更新所有儲存其他資料庫位置相關資訊的資料表。  
  
   > [!IMPORTANT]
   >  - 您只須在 BizTalk 群組中的 **任一部** 伺服器上執行 UpdateDatabase.vbs 即可。  
   >  - 在 64 位元電腦上，您必須從 64 位元命令提示字元中執行 UpdateDatabase.vbs。 請注意，64 位元電腦上的預設命令提示字元是 64 位元的命令提示字元，位於 %systemdrive%\windows\system32\cmd.exe。  
   >  - BizTalk EDI 引擎不需要任何自己的修改後的 SampleUpdateInfo.xml 還原資料庫時。  它需倚賴連線到 BizTalkDTADb 資料庫存取的 EDI 資料表。  
  
5. 將編輯的 SampleUpdateInfo.xml 檔案複製到下列資料夾中上,**每個**此 BizTalk 群組中執行 BizTalk Server 電腦：  
  
    32 位元電腦： 複製到 `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
    64 位元電腦： 複製到 `%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`  
  
6. 在 **每個**電腦在 BizTalk Server 群組中，開啟命令提示字元，並移至：  
  
    32 位元電腦： `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
    64 位元電腦： `%SystemDrive%\Program Files (x86)Microsoft BizTalk Server <version>\Bins32\Schema\Restore`  
  
7. 在命令提示字元中，輸入：  
  
    `cscript UpdateRegistry.vbs SampleUpdateInfo.xml`  
  
    這個指令碼會更新所有儲存其他資料庫位置相關資訊的登錄項目。  
  
   > [!IMPORTANT]
   >  - 在 BizTalk 群組中的 **每部** 伺服器上執行 UpdateRegistry.vbs。  
   >  - 在 64 位元電腦上，您必須從 64 位元命令提示字元中執行 UpdateRegistry.vbs。  請注意，64 位元電腦上的預設命令提示字元是 64 位元的命令提示字元，位於 %systemdrive%\windows\system32\cmd.exe。  
  
8. 重新啟動所有 BizTalk Server 服務。 請參閱[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。  
  
9. 還原資料庫後，請重新啟動 Windows Management Instrumentation 服務。  
  
    1.  開啟 **services.msc**。  
  
    2.  在 [Windows Management Instrumentation] 上按一下滑鼠右鍵，然後按一下 [重新啟動] 。  
  
10. 開啟 [BizTalk Server 管理] 。 執行下列動作：  
  
    1. 在 [BizTalk 群組]  上按一下滑鼠右鍵，然後選取 [移除] 。  
  
    2. 在 [BizTalk Server 管理]  節點上按一下滑鼠右鍵，然後選取 [連接至現有的群組] 。  
  
    3. 在 [SQL Server 名稱] 中，選取裝載 BizTalk 管理資料庫之 SQL Server 執行個體的名稱。 當您選取 SQL Server 執行個體時，BizTalk Server 會自動偵測該電腦上的 BizTalk Server 資料庫。  
  
    4. 在 [資料庫名稱] 中選取您的 BizTalk 管理資料庫 (預設是**BizTalkMgmtDb** )，然後選取 [確定] 。  
  
       BizTalk Server 管理主控台會將 BizTalk 群組加入至 [管理] 主控台。  
  
       您的 BizTalk Server 現已還原，且應該執行。 接下來，設定備份 BizTalk Server 作業開始將備份寫入新的目的地伺服器。 您也應該重新設定新的目的系統。  

## <a name="important"></a>重要事項

- 如果您使用 [規則引擎]，還原資料庫之後，您必須重新啟動 BizTalk Server 群組的每部伺服器上的 「 規則引擎更新服務。 請參閱[如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。  
- 如果您使用 BAM，現在是還原 BAM 資料庫的時間。 請參閱[Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)。  
- 如果您要移動資料庫，而且您使用 BizTalk EDI 或 RosettaNet 加速器，某些 SQL 連接埠可能會對 BizTalk 資料庫的設定。 匯出繫結，搜尋舊的資料庫連結，並據以取代將資料庫連結。 

## <a name="next-steps"></a>後續步驟  
 [備份和還原 BAM](../core/backing-up-and-restoring-bam.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定備份 BizTalk Server 作業](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [設定記錄傳送的目的系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)
