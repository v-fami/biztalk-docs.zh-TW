---
title: "檢查清單： 執行每週維護檢查 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b13e43ba-4bac-4d4b-aaf8-46d60c0561bf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb754c0cfd7f153e4cefa3cd610ef1633ef1e073
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-performing-weekly-maintenance-checks"></a>檢查清單： 執行每週維護檢查
本主題描述每週執行的可靠性、 管理、 安全性與效能維護檢查所需的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  
  
|步驟|參考|  
|-----------|---------------|  
|請確定每個主機有兩個以上的實體 BizTalk 伺服器 （可靠性檢查） 上執行的執行個體。|[BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)|  
|請確定每個接收位置是多餘 （可靠性檢查）。|[向外擴充接收主控件](../technical-guides/scaling-out-receiving-hosts.md)|  
|確定 SQL Server Agent 服務正在執行 SQL server （管理檢查） 上。|-   [如何： 啟動 SQL Server Agent](http://go.microsoft.com/fwlink/p/?LinkId=154672) (http://go.microsoft.com/fwlink/p/?LinkId=154672)。<br />-   [SQL Server Agent](http://go.microsoft.com/fwlink/p/?LinkId=106728) (http://go.microsoft.com/fwlink/p/?LinkId=106728)。|  
|確保 BizTalk Server 相關的所有 SQL Server 作業都正常運作 （管理檢查）。|[監視 SQL Server Agent 作業](../technical-guides/monitoring-sql-server-agent-jobs.md)<br /><br /> 如果不執行 SQL Server Agent 作業，則會隨時間逐步下降系統效能。 如需有關 SQL Server Agent 作業，BizTalk Server 會提供可協助管理 BizTalk Server 資料庫，請參閱[資料庫結構與工作](http://go.microsoft.com/fwlink/p/?LinkID=153451)(http://go.microsoft.com/fwlink/p/?LinkID=153451)。|  
|請確定負責備份 BizTalk Server 資料庫的 SQL Server 作業都正常執行 （管理檢查）。|-   [如何設定 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/p/?LinkID=153813)(http://go.microsoft.com/fwlink/p/?LinkID=153813)<br />-   [如何排程 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/p/?LinkId=154674)(http://go.microsoft.com/fwlink/p/?LinkId=154674)|  
|請確認已安裝最新的安全性更新 （安全性檢查）。|在 Microsoft Update 站台[http://update.microsoft.com/microsoftupdate/v6/default.aspx](http://update.microsoft.com/microsoftupdate/v6/default.aspx)|  
|分析每週的效能監視針對基準和臨界值 （效能檢查） 的記錄檔。|-   [使用記錄檔 (PAL) 工具的效能的分析](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)<br />-   [疑難排解效能 Issues3](../technical-guides/troubleshooting-performance-issues3.md)|  
|請確認系統發生的 BizTalk Server 資料庫 （效能檢查） 的經常自動成長。|-   [定義資料庫的自動成長設定](../technical-guides/defining-auto-growth-settings-for-databases.md)<br />-   [追蹤資料庫大小的指導方針](http://go.microsoft.com/fwlink/p/?LinkId=154677)(http://go.microsoft.com/fwlink/p/?LinkId=154677)。<br />-   [識別資料庫層中的瓶頸](http://go.microsoft.com/fwlink/p/?LinkId=154678)(http://go.microsoft.com/fwlink/p/?LinkId=154678)。<br />-   [資料庫檔案初始化](http://go.microsoft.com/fwlink/p/?LinkID=101579)(http://go.microsoft.com/fwlink/p/?LinkID=101579)。<br />-   [執行 SQL Server 維護程序](~/technical-guides/checklist-configuring-sql-server.md)|  
|若要檢查長回應時間和高資源使用量 （效能檢查） 的高負載期間執行 SQL Server Profiler。|[使用 SQL Server Profiler](http://go.microsoft.com/fwlink/p/?LinkID=106720) (http://go.microsoft.com/fwlink/p/?LinkID=106720)。|  
|確定所有配接器的訊息批次處理是適用於資源耗用量或延遲 （效能檢查）。|-   [設定批次處理來改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)<br />-   [如何設計高效能的配接器](http://go.microsoft.com/fwlink/p/?LinkId=154679)(http://go.microsoft.com/fwlink/p/?LinkId=154679)。|  
|請確認大型訊息閾值適合資源耗用量 （效能檢查）。|[BizTalk Server 如何處理大型訊息](http://go.microsoft.com/fwlink/p/p/?LinkId=154680)(http://go.microsoft.com/fwlink/p/p/?LinkId=154680)。|  
|封存備份的檔案，並指定適當的電腦備份|若要避免資料遺失，您應該指定的電腦，做為不同的電腦與原始資料，以及備份\<目的地路徑 > 您應該指定不同的電腦，以儲存資料庫記錄檔與原始資料庫記錄檔的電腦。<br /><br /> 如需備份的最佳作法的詳細資訊，請參閱[Backing Up and Restoring Databases 的最佳作法](http://go.microsoft.com/fwlink/p/p/?LinkID=151391)(http://go.microsoft.com/fwlink/p/p/?LinkID=151391)。|  
  
## <a name="see-also"></a>另請參閱  
 [例行監視工作](../technical-guides/routine-monitoring-tasks.md)