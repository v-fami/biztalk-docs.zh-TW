---
title: "檢查清單： 提高可用性與災害復原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b315110-206a-4fa7-9bde-abab1429c83b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8790d82e3e5830e8145a8af2614413936f3e4b55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-increasing-availability-with-disaster-recovery"></a>檢查清單： 提高可用性與災害復原
本主題描述的步驟，您應遵循以提高可用性生產[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中使用災害復原。 提供高可用性與容錯能力和/或負載平衡後通常實作災害復原。  
  
## <a name="backing-up-biztalk-server"></a>備份 BizTalk Server  
  
|步驟|參考|  
|----------|---------------|  
|寫入記錄的所有變更您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。||  
|請確定您有適當的權限，來備份和還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。|請參閱[最低安全性使用者權限](http://go.microsoft.com/fwlink/?LinkId=154374)(http://go.microsoft.com/fwlink/?LinkId=154374)|  
|建立高可用性檔案共用，基於儲存[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄檔。 使用 Windows 叢集在硬體層級使用 SAN，及/或 Windows 伺服器層級設定高可用性檔案共用。|請參閱[如何在叢集上建立檔案共用](http://support.microsoft.com/kb/224967)(http://support.microsoft.com/kb/224967)|  
|安裝並使用一或多個待命[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]做為目的地執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送。 硬體和目的地數目[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體應該符合的硬體和數目[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]實際執行環境中的執行個體。 這可確保目的地[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體可以處理相同的負載為生產[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。|請參閱[安裝 SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=154377) (http://go.microsoft.com/fwlink/?LinkId=154377)|  
|準備災害復原站台。|[準備災害復原站台](../technical-guides/prepare-the-disaster-recovery-site.md)|  
|備份和還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫|-   [備份和還原資料庫的最佳作法](http://go.microsoft.com/fwlink/?LinkId=157758)(http://go.microsoft.com/fwlink/?LinkId=157758)<br />-   [備份和還原 BizTalk Server 資料庫](http://go.microsoft.com/fwlink/?LinkId=157757)(http://go.microsoft.com/fwlink/?LinkId=157757)|  
|設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送。|[設定 BizTalk Server 記錄傳送](../technical-guides/configuring-biztalk-server-log-shipping.md)|  
|設定備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業。|[如何設定 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/?LinkID=154072)(http://go.microsoft.com/fwlink/?LinkID=154072)|  
|設定將要儲存備份的伺服器。|[如何設定記錄傳送目的地系統](http://go.microsoft.com/fwlink/?LinkID=151402)(http://go.microsoft.com/fwlink/?LinkID=151402)|  
|如果您有使用商務活動監控 (BAM)，請備份 BAM 資料庫。|[備份 BAM 分析和追蹤 Analysis Server 資料庫](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)|  
|如果您使用 BAM，備份 BAM 入口網站應用程式集區和虛擬目錄組態資訊。 如果您沒有使用 BAM，就不需要執行此步驟。|[如何備份 BAM 入口網站](http://go.microsoft.com/fwlink/?LinkId=154378)(http://go.microsoft.com/fwlink/?LinkId=154378)|  
|備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態檔。|[如何備份 BizTalk Server 組態](http://go.microsoft.com/fwlink/?LinkId=154379)(http://go.microsoft.com/fwlink/?LinkId=154379)|  
|如果您使用企業單一登入，請備份主要密碼伺服器。|[如何備份主要密碼](http://go.microsoft.com/fwlink/?LinkID=151395)(http://go.microsoft.com/fwlink/?LinkID=151395)|  
  
## <a name="restoring-biztalk-server"></a>還原 BizTalk Server  
  
|步驟|參考|  
|-----------|---------------|  
|還原 BizTalk 群組。|[還原 BizTalk 群組](../technical-guides/restoring-the-biztalk-group.md)|  
|復原執行的執行階段電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。|[復原執行階段電腦](../technical-guides/recovering-the-runtime-computers.md)|  
|復原 BAM 警示。|[如何復原 BAM 警示](http://go.microsoft.com/fwlink/?LinkId=154380)(http://go.microsoft.com/fwlink/?LinkId=154380)|  
|復原 BAM 入口網站。|[如何復原 BAM 入口網站](http://go.microsoft.com/fwlink/?LinkId=154381)(http://go.microsoft.com/fwlink/?LinkId=154381)|  
|還原主要密碼伺服器。|[如何還原主要密碼](http://go.microsoft.com/fwlink/?LinkId=151394)(http://go.microsoft.com/fwlink/?LinkId=151394)|  
|還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。|[如何還原資料庫](http://go.microsoft.com/fwlink/?LinkId=151406)(http://go.microsoft.com/fwlink/?LinkId=151406)|  
|更新 BAM 資料庫名稱的參考。|-   [更新至新的 BAM 主要匯入資料庫的參考](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef)<br />-   [更新至新的 BAM 封存資料庫的參考](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArch)<br />-   [更新至新的 BAM 星狀結構描述資料庫的參考](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate)<br />-   [更新至新的 BAM 分析資料庫的參考](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate)<br />-   [更新參考新的 BAM notification Services 資料庫](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdate)<br />-   [如何解析未完成的活動執行個體](http://go.microsoft.com/fwlink/?LinkId=151475)(http://go.microsoft.com/fwlink/?LinkId=151475)|  
  
## <a name="see-also"></a>另請參閱  
 [嚴重損壞修復](../technical-guides/disaster-recovery.md)