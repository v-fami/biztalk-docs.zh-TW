---
title: 組態後資料庫 Optimizations1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 763b5358-97ed-4ada-8318-0ad07388ba89
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eeb1c5c8bbb93bce5eb69462585c2da69d587dad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302326"
---
# <a name="post-configuration-database-optimizations"></a>組態後資料庫最佳化
除了下列中的建議[預先設定資料庫最佳化](../technical-guides/post-configuration-database-optimizations1.md)，應該遵循幾個步驟來最佳化 SQL Server 上的 BizTalk Server 資料庫效能*之後*已安裝 BizTalk Server，且已設定 BizTalk Server 資料庫。 本主題提供這些最佳化的清單。  
  
## <a name="pre-allocate-space-for-biztalk-server-databases-and-define-auto-growth-settings-for-biztalk-server-databases-to-a-fixed-value-instead-of-a-percentage-value"></a>預先配置空間給 BizTalk Server 資料庫，並定義為固定的值，而不是百分比值的 BizTalk Server 資料庫的自動成長設定  
  
-   SQL Server 資料庫自動成長是 BizTalk Server 資料庫效能會防礙封鎖作業。 因此務必配置足夠的空間，BizTalk Server 資料庫，事先來減少資料庫自動成長的相符項目。  
  
-   自動成長的資料庫應該設為固定數目的 mb，而不是百分比 (指定的檔案成長**以 mb 為單位**)。 這應完成，如果自動成長，就會發生，它會以降低過多資料庫成長的測量方式。 成長遞增值通常是不能大於 100 MB （適用於大型的檔案）、 10 MB （適用於中小型檔案） 或 1 MB （適用於小型檔案）。  
  
-   當 SQL Server 會增加檔案大小時，才可以使用，必須先被初始化新的空間。 這是封鎖作業，包括新的空間中填入空白頁。 執行 Windows Server 2003 或更新版本的 SQL Server 2005 支援立即檔案初始化。 」 這可大幅減少檔案成長作業的效能影響。 如需詳細資訊，請參閱資料庫檔案初始化 」 中的 SQL Server 2008 文件，網址[http://go.microsoft.com/fwlink/?LinkId=132063](http://go.microsoft.com/fwlink/?LinkId=132063)。 本主題提供步驟啟用立即檔案初始化。  
  
## <a name="move-the-backup-biztalk-server-output-directory-to-a-dedicated-lun"></a>將備份 BizTalk Server 的輸出目錄移至的專用 LUN  
 將備份 BizTalk Server （完整和記錄備份） 的輸出目錄移至專用 LUN 中，編輯步驟 1 和 2 （插入新輸出路徑） 的 「 備份 BizTalk Server [BizTalkMgmtDb] 」 工作。 移動 備份 BizTalk Server 輸出目錄的專用 LUN 會減少磁碟 I/O 競爭，當工作正在執行工作與不同的磁碟寫入正在讀取。  
  
## <a name="verify-the-biztalk-server-sql-agent-jobs-are-running"></a>確認執行 BizTalk Server SQL Agent 工作  
 BizTalk Server 包含數個 SQL Server Agent 作業執行重要功能以維持伺服器運作且狀況良好。 您應該監視這些作業的狀況，並確保它們正在執行不會發生錯誤。 在 BizTalk Server 中的效能問題的最常見的原因之一是 BizTalk Server SQL Agent 作業不會執行，這種情況會導致 MessageBox 以及追蹤資料庫成長未核取。 請遵循這些步驟，以確保 BizTalk Server SQL Agent 工作正在執行不會有問題：  
  
 在 BizTalk Server 中的效能問題的最常見的原因之一是 BizTalk Server SQL Agent 作業不會執行，這種情況會導致 MessageBox 以及追蹤資料庫成長未核取。 請遵循這些步驟，以確保 BizTalk Server SQL Agent 工作正在執行不會有問題：  
  
-   **確認 SQL Server Agent 服務正在執行**。  
  
-   **確認 BizTalk Server 安裝的 SQL Server Agent 作業已啟用且正在執行成功**。  
  
     BizTalk Server SQL Server Agent 作業很重要，如果它們未執行，一段時間，將會降低系統效能。  
  
-   **確認 BizTalk Server SQL Server Agent 作業完成及時**。  
  
     設定 Microsoft Operations Manager (MOM) 2005年或 Microsoft System Center Operations Manager 2007，以監視作業。  
  
     您應留意某些工作特定的排程：  
  
    -   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作預設會持續執行。 監視軟體，應該考量此排程，而不會產生警告。  
  
    -   未啟用 MessageBox_Message_Cleanup_BizTalkMsgBoxDb 作業或排程，但它由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作啟動每隔 10 秒。 因此，此作業應該不啟用、 排程，或手動啟動。  
  
-   **確認已正確設定 SQL Server Agent 服務的啟動類型**。  
  
     確認 SQL Server Agent 服務已設定使用**啟動類型**的**自動**除非 SQL Server Agent 服務已設定為 Windows Server 叢集上叢集資源。 如果 SQL Server Agent 服務設定為叢集資源，則您應該設定**啟動類型**為**手動**因為服務會受叢集服務。  
  
## <a name="configure-purging-and-archiving-of-tracking-data"></a>設定清除和封存的追蹤資料  
 請遵循這些步驟，以確保清除和封存的追蹤資料已正確設定：  
  
-   確定 SQL Agent 作業 「 DTA 清除與封存 」 已正確設定、 啟用以及已成功完成。 如需詳細資訊，請參閱 「 如何以設定 DTA 清除和封存工作 」 在 BizTalk Server 文件中[http://go.microsoft.com/fwlink/?LinkId=104908](http://go.microsoft.com/fwlink/?LinkId=104908)。  
  
-   請確定作業能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。 如需詳細資訊，請參閱"測量持續性追蹤輸送量上限 」 中的 BizTalk Server 2006 R2 文件，網址[http://go.microsoft.com/fwlink/?LinkId=104909](http://go.microsoft.com/fwlink/?LinkId=104909)。  
  
-   檢閱軟清除和硬清除參數，以確保您保持最佳的時間長度的資料。 如需詳細資訊，請參閱 「 封存和清除 BizTalk 追蹤資料庫 」 中的 BizTalk Server 文件[http://go.microsoft.com/fwlink/?LinkId=101585](http://go.microsoft.com/fwlink/?LinkId=101585)。  
  
-   如果您只需要清除舊資料，而不需要封存第一次，變更的 SQL 代理程式作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase。 」 如需詳細資訊，請參閱 < 如何清除資料從 BizTalk 追蹤資料庫的 「 在 BizTalk Server 文件中[http://go.microsoft.com/fwlink/?LinkId=101584](http://go.microsoft.com/fwlink/?LinkId=101584)。  
  
## <a name="monitor-and-reduce-dtc-log-file-disk-io-contention"></a>監視及降低 DTC 記錄檔磁碟 I/O 競爭  
 Microsoft 分散式交易協調器 (MS DTC) 記錄檔可以成為在交易密集的環境中的磁碟 I/O 瓶頸。 使用支援交易，例如 SQL Server、 MSMQ 或 MQSeries，或在多個 MessageBox 的環境中的介面卡時，這是特別有用。 交易式配接器使用 DTC 交易，並多 MessageBox 環境會大量使用 DTC 交易。 若要確保 DTC 記錄檔不會發生磁碟 I/O 瓶頸，您應監視磁碟 I/O 使用量 DTC 記錄檔所在的 SQL Server 資料庫伺服器上的磁碟。 如果磁碟 I/O 使用量 DTC 記錄檔所在的磁碟變成過多請考慮將 DTC 記錄檔移至更快的磁碟。 在環境中，SQL Server 已叢集化，這是不太多的主要考量因為記錄檔，就會共用的磁碟機，可能會有多個磁針的快速 SAN 磁碟機上。 因為可能會成為非叢集環境中的瓶頸或 DTC 記錄檔時，與其他需要大量的磁碟檔案的共用磁碟上，不過還是應該監視磁碟 I/O 使用量。  
  
 若要確保 DTC 記錄檔不會發生磁碟 I/O 瓶頸，您應監視磁碟 I/O 使用量 DTC 記錄檔所在的 SQL Server 資料庫伺服器上的磁碟。 如果磁碟 I/O 使用量 DTC 記錄檔所在的磁碟變成過多，請考慮將 DTC 記錄檔移至更快的磁碟。  
  
 在環境中，SQL Server 已叢集化，這是不太多的主要考量因為記錄檔，就會共用的磁碟機，可能會有多個磁針的快速 SAN 磁碟機上。 因為可能會成為非叢集環境中的瓶頸或 DTC 記錄檔時，與其他需要大量的磁碟檔案的共用磁碟上，不過還是應該監視磁碟 I/O 使用量。  
  
## <a name="separate-the-messagebox-and-tracking-databases"></a>分隔 MessageBox 和追蹤資料庫  
 因為 BizTalk MessageBox 和 「 BizTalk 追蹤資料庫是最常使用，我們建議您針對每一種可降低發生問題的磁碟 I/O 競爭的可能性的專用磁碟機上放置資料檔和交易記錄檔。 比方說，您需要四個 MessageBox 和 「 BizTalk 追蹤資料庫檔案的磁碟機、 一部磁碟機的下列各項：  
  
-   MessageBox 資料檔案  
  
-   MessageBox 交易記錄檔  
  
-   BizTalk 追蹤 (DTA) 資料檔案  
  
-   BizTalk 追蹤 (DTA) 交易記錄檔  
  
 分隔 BizTalk MessageBox 和 「 BizTalk 追蹤資料庫，以及將資料庫檔案和交易記錄檔不同實體磁碟上的會被視為降低磁碟 I/O 競爭的最佳作法。 請試著儘可能將磁碟 I/O 分散數量的實體磁針。 您也可以降低磁碟 I/O 競爭放置在專用的 SQL Server 上的 BizTalk 追蹤資料庫，不過，您仍應該遵循上述作法，有關分隔資料檔和交易記錄檔。  
  
## <a name="optimize-filegroups-for-the-biztalk-server-databases"></a>最佳化檔案群組的 BizTalk Server 資料庫  
 請依照[Databases1 最佳化檔案群組](../technical-guides/optimizing-filegroups-for-the-databases1.md)和在 「 BizTalk Server 資料庫最佳化 」 白皮書[http://go.microsoft.com/fwlink/?LinkId = 101578](http://go.microsoft.com/fwlink/?LinkId=101578)建立額外的檔案群組和 BizTalk Server 資料庫檔案。 這會大幅增加 BizTalk Server 資料庫，從單一磁碟設定的效能。