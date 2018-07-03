---
title: 後置設定資料庫 Optimizations1 |Microsoft Docs
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
ms.openlocfilehash: e89da931e7f7a007734d69dfec8921556982ec24
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975079"
---
# <a name="post-configuration-database-optimizations"></a>後置設定資料庫最佳化
除了遵循中的建議[預先設定資料庫最佳化](../technical-guides/post-configuration-database-optimizations1.md)，應該遵循數個步驟，才能將 SQL Server 上的 BizTalk Server 資料庫效能最佳化*之後*在安裝 BizTalk Server，而且已設定 BizTalk Server 資料庫。 本主題提供這些最佳化的清單。  
  
## <a name="pre-allocate-space-for-biztalk-server-databases-and-define-auto-growth-settings-for-biztalk-server-databases-to-a-fixed-value-instead-of-a-percentage-value"></a>預先配置空間給 BizTalk Server 資料庫，並定義 BizTalk Server 資料庫的自動成長設定為固定的值，而不是百分比值  
  
-   SQL Server 資料庫自動成長是 BizTalk Server 資料庫效能會防礙的封鎖作業。 因此務必配置足夠的空間，BizTalk Server 資料庫，以減少資料庫自動成長的相符項目。  
  
-   資料庫自動成長應該設定為固定數目的 mb，而不是百分比 (指定的檔案成長**以 mb 為單位**)。 這應該讓發生自動成長時，它會測量的方式可減少過多的資料庫成長的可能性。 一般應該不能大於 100 MB （適用於大型檔案）、 10 MB （適用於中型檔案） 或 1 MB （適用於小型檔案） 的成長遞增。  
  
-   當 SQL Server 會增加檔案大小時，才可以使用，必須先被初始化新的空間。 這是牽涉到新的空間中填入空白頁的封鎖作業。 執行 Windows Server 2003 或更新版本的 SQL Server 2005 支援 「 立即檔案初始化 」。 這可以大幅降低檔案成長作業的效能影響。 詳細資訊，請參閱 「 資料庫檔案初始化 」，在 SQL Server 2008 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=132063 ](http://go.microsoft.com/fwlink/?LinkId=132063)。 本主題提供步驟啟用檔案立即初始化。  
  
## <a name="move-the-backup-biztalk-server-output-directory-to-a-dedicated-lun"></a>將備份 BizTalk Server 的輸出目錄移至專用的 LUN  
 將備份 BizTalk Server （完整和記錄備份） 的輸出目錄移至專用 LUN 中，編輯步驟 1 和 2 （插入新輸出路徑） 的 「 備份 BizTalk Server [BizTalkMgmtDb] 」 工作。 從讀取移動備份 BizTalk Server 的輸出目錄的專用 lun 會減少磁碟 I/O 競爭，當工作正在執行寫入作業與不同的磁碟。  
  
## <a name="verify-the-biztalk-server-sql-agent-jobs-are-running"></a>確認執行 BizTalk Server SQL Agent 工作  
 BizTalk Server 包含數個 SQL Server Agent 作業可執行以維持伺服器運作中且狀況良好的重要功能。 您應該監視這些作業的狀況，並確保它們正在執行無誤。 在 BizTalk Server 中的效能問題的最常見的原因之一是 BizTalk Server SQL Agent 作業不會執行，又會導致 MessageBox 和追蹤來抑制地成長的資料庫。 請遵循下列步驟以確保 BizTalk Server SQL Agent 作業皆正常地執行：  
  
 在 BizTalk Server 中的效能問題的最常見的原因之一是 BizTalk Server SQL Agent 作業不會執行，又會導致 MessageBox 和追蹤來抑制地成長的資料庫。 請遵循下列步驟以確保 BizTalk Server SQL Agent 作業皆正常地執行：  
  
-   **確認 SQL Server Agent 服務正在執行**。  
  
-   **確認 BizTalk Server 所安裝的 SQL Server Agent 作業已啟用且正在執行成功**。  
  
     BizTalk Server SQL Server Agent 作業很重要 — 如果它們並未執行，經過一段時間，會降低系統效能。  
  
-   **確認 BizTalk Server SQL Server Agent 作業所完成及時**。  
  
     設定 Microsoft Operations Manager (MOM) 2005年或 Microsoft System Center Operations Manager 2007，以監視作業。  
  
     您應該注意的是專門針對特定工作的排程：  
  
    -   預設會持續 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作執行。 監視軟體，請考量此排程，並不會產生警告。  
  
    -   MessageBox_Message_Cleanup_BizTalkMsgBoxDb 作業未啟用或排程，但它由 MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb 工作開始每隔 10 秒。 因此，這項作業不應啟用、 排程，或以手動方式啟動。  
  
-   **確認已正確設定 SQL Server Agent 服務的啟動類型**。  
  
     確認 SQL Server Agent 服務已設有**啟動類型**的**自動**除非 SQL Server Agent 服務設定為 Windows Server 叢集上叢集資源。 如果 SQL Server Agent 服務設定為叢集資源，則您應該設定**啟動類型**作為**手動**因為服務將受叢集服務。  
  
## <a name="configure-purging-and-archiving-of-tracking-data"></a>設定清除和封存的追蹤資料  
 請遵循下列步驟以確保清除和封存的追蹤資料已正確設定：  
  
-   請確定 SQL Agent 作業 「 DTA 清除與封存 」 是已正確設定、 啟用以及成功完成。 詳細資訊，請參閱 < 如何以設定 DTA 清除和封存工作 >，在 BizTalk Server 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=104908 ](http://go.microsoft.com/fwlink/?LinkId=104908)。  
  
-   請確定作業已能夠以最快速度的內送的追蹤資料會產生清除追蹤資料。 如需詳細資訊，請參閱 「 測量最大持續性追蹤輸送量 」 在 BizTalk Server 2006 R2 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=104909 ](http://go.microsoft.com/fwlink/?LinkId=104909)。  
  
-   檢閱軟清除和硬清除參數，以確保您會將最佳的時間長度的資料保留。 詳細資訊，請參閱 「 封存和清除 BizTalk 追蹤資料庫 」，在 BizTalk Server 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=101585 ](http://go.microsoft.com/fwlink/?LinkId=101585)。  
  
-   如果您只需要清除舊資料，也不需要將它保存第一次，變更的 SQL 代理程式作業來呼叫預存程序 」 dtasp_PurgeTrackingDatabase。 」 詳細資訊，請參閱 「 如何清除資料從 BizTalk 追蹤資料庫"，在 BizTalk Server 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=101584 ](http://go.microsoft.com/fwlink/?LinkId=101584)。  
  
## <a name="monitor-and-reduce-dtc-log-file-disk-io-contention"></a>監視及降低 DTC 記錄檔的磁碟 I/O 競爭  
 Microsoft 分散式交易協調器 (MS DTC) 記錄檔會在交易密集的環境中的磁碟 I/O 瓶頸。 使用支援交易，例如 SQL Server、 MSMQ 或 MQSeries，或在多個 MessageBox 的環境中的配接器時，這是特別有用。 交易式配接器使用 DTC 交易，以及多個 MessageBox 環境會大量使用 DTC 交易。 若要確保 DTC 記錄檔不會成為磁碟 I/O 瓶頸，您應該監視磁碟 I/O 使用量 DTC 記錄檔所在的 SQL Server 資料庫伺服器上的磁碟。 如果磁碟 DTC 記錄檔所在的磁碟 I/O 使用量變得過長則可考慮將 DTC 記錄檔移至磁碟速度更快。 在環境中已在叢集化 SQL Server，這是不太多無關緊要的因為記錄檔會在共用的磁碟機，可能會有多個磁針的快速 SAN 磁碟機上。 因為可能會成為非叢集環境中的瓶頸或 DTC 記錄檔時，與其他需要大量磁碟的檔案的共用磁碟上，不過仍應該監視的磁碟 I/O 使用量。  
  
 若要確保 DTC 記錄檔不會成為磁碟 I/O 瓶頸，您應該監視磁碟 I/O 使用量 DTC 記錄檔所在的 SQL Server 資料庫伺服器上的磁碟。 如果磁碟 DTC 記錄檔所在的磁碟 I/O 使用量變得過長，請考慮將 DTC 記錄檔移至磁碟速度更快。  
  
 在環境中已在叢集化 SQL Server，這是不太多無關緊要的因為記錄檔會在共用的磁碟機，可能會有多個磁針的快速 SAN 磁碟機上。 因為可能會成為非叢集環境中的瓶頸或 DTC 記錄檔時，與其他需要大量磁碟的檔案的共用磁碟上，不過仍應該監視的磁碟 I/O 使用量。  
  
## <a name="separate-the-messagebox-and-tracking-databases"></a>分隔 MessageBox 和追蹤資料庫  
 因為 BizTalk MessageBox 和 「 BizTalk 追蹤資料庫是最常使用，我們建議您針對每一種可降低磁碟 I/O 競爭問題的可能性的專用磁碟機上放置資料檔和交易記錄檔。 比方說，您需要四個 MessageBox 和 「 BizTalk 追蹤資料庫檔案的磁碟機、 一個磁碟機的下列各項：  
  
- MessageBox 資料檔案  
  
- MessageBox 交易記錄檔  
  
- BizTalk 追蹤 (DTA) 資料檔案  
  
- BizTalk 追蹤 (DTA) 交易記錄檔  
  
  分隔 BizTalk MessageBox 和 「 BizTalk 追蹤資料庫，並將資料庫檔案和交易記錄檔，在不同的實體磁碟上會被視為減少磁碟 I/O 競爭的最佳作法。 請試著盡可能分散多個實體磁針的磁碟 I/O。 您也可以藉由將 「 BizTalk 追蹤資料庫放在專用的 SQL Server 上減少磁碟 I/O 競爭，不過，您仍然應該遵循上述作法，關於用來分隔資料檔和交易記錄檔。  
  
## <a name="optimize-filegroups-for-the-biztalk-server-databases"></a>最佳化 BizTalk Server 資料庫檔案群組  
 請依照下列中的步驟[Databases1 最佳化檔案群組](../technical-guides/optimizing-filegroups-for-the-databases1.md)並在 「 BizTalk Server 資料庫最佳化 」 （英文） 白皮書[ http://go.microsoft.com/fwlink/?LinkId=101578 ](http://go.microsoft.com/fwlink/?LinkId=101578) biztalk 建立額外的檔案群組和檔案伺服器的資料庫。 這會大幅增加 BizTalk Server 資料庫，從單一磁碟設定的效能。