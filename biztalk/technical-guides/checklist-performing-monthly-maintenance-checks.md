---
title: "檢查清單： 執行每月維護檢查 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 588b74fa-6bf5-43ad-aa15-3595adde76d1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40f5e5d7d6c6732c203ac7a34308c546388206c3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="checklist-complete-monthly-maintenance-checks-in-biztalk-server"></a>在 BizTalk Server 中的檢查清單： 完成每月維護檢查
本主題說明在執行每個月的可靠性、 管理、 安全性與效能維護檢查所需的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。  

## <a name="checklist"></a>檢查清單
|步驟|參考|  
|-----------|---------------|  
|請確定主要密碼金鑰備份的最新且使用方便上離線存放區 （可靠性檢查）。|[如何備份主要密碼](../core/how-to-back-up-the-master-secret.md)|  
|確保容錯移轉叢集的所有服務都已測試 （可靠性檢查）。|[檢閱及測試容錯移轉案例的 SQL Server 叢集設定](../technical-guides/reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)|  
|請確定已叢集化 「 企業單一登入服務 （可靠性檢查）。|[叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)|  
|確定 BizTalk Server 資料庫已叢集化，在 SQL Server 服務 （可靠性檢查）。|[叢集 BizTalk Server 資料庫](../technical-guides/clustering-the-biztalk-server-databases2.md)|  
|確認至少兩個實體 BizTalk 伺服器都屬於 BizTalk 群組 （可靠性檢查）。|[確保多部伺服器是 BizTalk 群組的一部分](../technical-guides/maintaining-reliability.md#BKMK_BTSGrp)|  
|判斷是否正在使用任何不穩定的程式碼，而且如果是，請使用不同的主機 （可靠性檢查）。|[BizTalk 主控件的高可用性](../technical-guides/high-availability-for-biztalk-hosts.md)|  
|執行所有新 BizTalk 應用程式 （可靠性檢查） 的功能測試。|-   [測試應用程式](../technical-guides/testing-an-application.md)<br />-   [BizTalk 應用程式部署的預備工作](../core/staging-tasks-for-biztalk-application-deployment.md)|  
|設定及排程備份 BizTalk Server 作業 （可靠性檢查）。|-   [如何設定 「 備份 BizTalk Server 」 工作](../core/how-to-configure-the-backup-biztalk-server-job.md)<br />-   [如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)|  
|請確認組件集合的正確版本已安裝在每個 BizTalk 電腦 （完整性檢查） 上。|使用**BizTalk 組件檢查] 和 [遠端 GAC**工具 (BTSAssemblyChecker.exe) 來檢查組件部署到 BizTalk 管理資料庫的版本，並確認它們正確登錄所有上的GAC中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。 若要確認 BizTalk 的所有節點上已安裝的所有組件包含特定的 BizTalk 應用程式的成品，您可以使用此工具。 此工具是搭配實心版本控制策略，以確認組件集合的正確版本已安裝每個 BizTalk 在電腦上，特別使用並存的部署方法時特別有用。 此工具會與[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Support\Tools\x86\BTSAssemblyChecker.exe 安裝媒體。|  
|判斷是否有任何不必要 BizTalk 應用程式、 成品和組態 （管理檢查）。|-移除所有不必要 BizTalk 應用程式、 成品和組態。<br />-使用 BTSTask 命令列工具看到如需有關移除 BizTalk 應用程式或成品[RemoveApp 命令](../core/removeapp-command.md)。<br />-如需有關如何從 BizTalk Server 管理主控台或 BTSTask 命令列工具使用的應用程式移除成品的詳細資訊，請參閱[如何從應用程式移除成品](../core/how-to-remove-an-artifact-from-an-application.md)。|  
|請檢查任何未經核准的變更 （管理檢查） 的 BizTalk Server 管理主控台。|[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)|  
|BTSNTSvc.exe.config 檢查任何未經核准的修改 （管理檢查）。|[BTSNTSvc.exe.config 檔案](../core/btsntsvc-exe-config-file.md)|  
|請檢查任何未經核准的修改 （管理檢查） 的 BizTalk Server 相關的登錄機碼。|Microsoft 知識庫文章 256986[進階使用者的 Windows 登錄資訊](https://support.microsoft.com/kb/256986)|  
|執行最佳做法分析程式，以便讓 BizTalk Server （管理檢查）。|[BizTalk Server Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=43382)|  
|請確認已安裝最新的 service pack 和更新 （系統管理和安全性檢查）。|[Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)|  
|請在相同的主機 （安全性檢查） 上沒有安裝的不同交易夥伴的構件。|[設定主控件與主控件執行個體](../technical-guides/configuring-hosts-and-host-instances.md)|  
|確定 BizTalk Server 使用只有網域層級使用者和群組 （安全性檢查）。|[網域群組](../core/domain-groups.md)|  
|請確定已啟用 MSDTC 安全性組態 （安全性檢查）。|請參閱**設定適當的 MSDTC 安全性組態選項**中[疑難排解 MSDTC 問題的](../core/troubleshooting-problems-with-msdtc.md)。|  
|判斷是否必須是 BizTalk Server 快取重新整理間隔增加 （效能檢查）。|[如何調整設定快取重新整理間隔](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)|  
|判斷是否需要每個主控件節流的選項會調整 （效能檢查）。|-若為輸入和輸出主控件節流的相關資訊，請參閱[何謂主控件節流？](../core/what-is-host-throttling.md)。<br />-如需觸發程序、 動作，以及移轉策略輸入和輸出節流的資訊，請參閱**節流狀況觸發程序、 動作和緩和策略**在[如何 BizTalk Server 實作裝載節流](../core/how-biztalk-server-implements-host-throttling.md)。|  
|判斷是否啟用不必要的追蹤，例如協調流程、 圖形與商務規則引擎 (BRE) 事件追蹤 （效能檢查）。|-   [如何停用追蹤](../technical-guides/how-to-disable-tracking.md)<br />-   [規劃追蹤](../technical-guides/planning-for-tracking.md)<br />-   [追蹤的最佳作法](../technical-guides/planning-for-tracking.md#BKMK_TrackingBP)|  
|決定您是否使用專用的主控件追蹤維護 （效能檢查）。|[設定專用的追蹤主控件](../technical-guides/configuring-a-dedicated-tracking-host.md)|  
|請檢查 BizTalk Server 資料庫的大小增加的趨勢 （效能檢查）。|-如需有關調整追蹤資料庫大小的詳細資訊，請參閱[追蹤資料庫大小的指導方針](../core/tracking-database-sizing-guidelines.md)。<br />-如需有關如何調整大小的 MessageBox，BizTalkDTADb、 BAMPrimaryImport 資料庫的詳細資訊，請參閱[找出效能瓶頸](../core/identifying-performance-bottlenecks.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [例行性維護工作檢查清單](../technical-guides/routine-maintenance-checklists.md)
