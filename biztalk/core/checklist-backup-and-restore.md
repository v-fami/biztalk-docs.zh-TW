---
title: "檢查清單： 備份和還原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1d46a59-54f9-483e-9290-f4a9461006a7
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9c9a540467b24374fec7ca5881fef129f582f3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-backup-and-restore"></a>檢查清單： 備份與還原
在您的硬體還能正常運作時，執行下列步驟以確保您可以還原 BizTalk Server 系統。  
  
## <a name="backing-up-biztalk-server"></a>備份 BizTalk Server  
  
|步驟|參考|  
|----------|---------------|  
|將您 BizTalk Server 系統上的所有變更寫下來。||  
|請確定您擁有備份和還原 BizTalk Server 的適當權限。|[最小安全性使用者權限](../core/minimum-security-user-rights.md)|  
|瞭解如何備份和還原 BizTalk Server 資料庫。|[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)|  
|設定備份 BizTalk Server 工作來備份 BizTalk Server 資料庫。|[如何設定備份 BizTalk Server 作業](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|設定要還原資料庫備份檔的目的伺服器。|[如何設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)|  
|如果您有使用商務活動監控 (BAM)，請備份 BAM 資料庫。|[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)|  
|如果您有使用「企業單一登入」(SSO)，請備份主要密碼。|[管理主要密碼](../core/managing-the-master-secret.md)|  
|備份 BizTalk Server 組態檔。|[如何備份 BizTalk Server 組態](../core/how-to-back-up-the-biztalk-server-configuration.md)|  
|備份「企業單一登入」主要密碼。|[如何備份主要密碼](../core/how-to-back-up-the-master-secret.md)|  
|備份 BAM 入口網站應用程式集區與虛擬目錄組態資訊。 如果您沒有使用 BAM，就不需要執行此步驟。|[如何備份 BAM 入口網站](../core/how-to-back-up-the-bam-portal.md)|  
|備份您的 BizTalk 應用程式。|[備份 BizTalk Server 應用程式](../core/backing-up-biztalk-server-applications.md)|  
  
## <a name="restoring-biztalk-server"></a>還原 BizTalk Server  
  
|步驟|參考|  
|----------|---------------|  
|還原您的資料庫。|[如何還原資料庫](../core/how-to-restore-your-databases.md)|  
|更新 BAM 資料庫名稱的參考。|[如何備份 BAM 分析和追蹤 Analysis Server 資料庫](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)<br /><br /> [如何更新 BAM Analysis Server 和星狀結構描述資料庫名稱的參考](../core/update-references-to-the-bam-analysis-server-and-star-schema-database-names.md)<br /><br /> [如何更新 BAM 封存資料庫名稱的參考](../core/how-to-update-references-to-the-bam-archive-database-name.md)<br /><br /> [如何更新 BAM 主要匯入資料庫名稱和連接字串的參考](../core/update-references-to-bam-primary-import-database-name-and-connection-string.md)<br /><br /> [如何更新參考 BAM Notification Services 資料庫](../core/how-to-update-references-to-the-bam-notification-services-databases.md)<br /><br /> [如何解析未完成的活動執行個體](../core/how-to-resolve-incomplete-activity-instances.md)|  
|如果您有使用「企業單一登入」，請還原主要密碼。|[管理主要密碼](../core/managing-the-master-secret.md)|  
|如果執行 BizTalk Server 的電腦無法運作，請在替換電腦上安裝 BizTalk Server。|[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)|  
|還原憑證存放區。<br /><br /> Standard 版需要執行此步驟。 其他版本不需要執行此步驟，例如 Enterprise 版，因為組態檔會自動執行此步驟。|[如何還原憑證存放區](../core/how-to-restore-the-certificate-store.md)|  
|還原企業單一登入|[如何復原企業單一登入](../core/how-to-recover-enterprise-single-sign-on.md)|  
|還原 BizTalk 群組|[如何復原 BizTalk 群組](../core/how-to-recover-the-biztalk-group.md)<br /><br /> 如果您要還原 Standard Edition，您必須下載能夠協助復原伺服器的指令碼。 下載[RestoreConfig.vbe](http://go.microsoft.com/fwlink/?LinkId=195799)。|  
|還原 BizTalk Server 組態|[如何復原 BizTalk Server 組態](../core/how-to-recover-the-biztalk-server-configuration.md)|  
|如果您有使用 BAM，應該還原 BAM 警示。<br /><br /> 如果您沒有使用 BAM，就不需要執行此步驟。|[如何復原 BAM 警示](../core/how-to-recover-bam-alerts.md)|  
|如果您有使用 BAM，應該還原 BAM 入口網站。<br /><br /> 如果您沒有使用 BAM，就不需要執行此步驟。|[如何復原 BAM 入口網站](../core/how-to-recover-the-bam-portal.md)|  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)