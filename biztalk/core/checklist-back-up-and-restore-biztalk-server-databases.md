---
title: 檢查清單： 備份和還原 BizTalk Server 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- restoring, checklists
- maintaining, restoring
- maintaining, checklists
- restoring, BizTalk Server
- maintaining, backing up
- checklists, backing up
- backing up, checklists
- BizTalk Server, backing up
- checklists, restoring
- BizTalk Server, restoring
ms.assetid: 12f7e02e-57b1-4e55-8e44-7fe2d7920f5a
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f3c8c68eb62273562b0f703ae79c0db76ec837c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232702"
---
# <a name="checklist-back-up-and-restore-biztalk-server-databases"></a>檢查清單： 備份和還原 BizTalk Server 資料庫
在嘗試備份或還原 BizTalk Server 之前，務必讓自己先熟悉相關的程序。  
  
## <a name="backing-up-biztalk-server"></a>備份 BizTalk Server  
  
|步驟|參考|  
|----------|---------------|  
|瞭解如何備份和還原 BizTalk Server。|[備份和還原資料庫的最佳作法](../core/best-practices-for-backing-up-and-restoring-databases.md)<br /><br /> [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)|  
|請確定您擁有備份和還原 BizTalk Server 的適當權限。|[最小安全性使用者權限](../core/minimum-security-user-rights.md)|  
|設定「備份 BizTalk Server」工作。|[如何設定備份 BizTalk Server 作業](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|設定將要儲存備份的伺服器。|[如何設定記錄傳送目的地系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)|  
|如果您有使用商務活動監控 (BAM)，請備份 BAM 資料庫。|[備份和還原 BAM](../core/backing-up-and-restoring-bam.md)|  
|如果您有使用「企業單一登入」，請備份主要密碼。|[管理主要密碼](../core/managing-the-master-secret.md)|  
  
## <a name="restoring-biztalk-server"></a>還原 BizTalk Server  
  
|步驟|參考|  
|----------|---------------|  
|還原您的資料庫。|[如何還原資料庫](../core/how-to-restore-your-databases.md)|  
|更新 BAM 資料庫名稱的參考。|[如何備份 BAM 分析和追蹤 Analysis Server 資料庫](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)<br /><br /> [如何更新 BAM Analysis Server 和星狀結構描述資料庫名稱的參考](../core/update-references-to-the-bam-analysis-server-and-star-schema-database-names.md)<br /><br /> [如何更新 BAM 封存資料庫名稱的參考](../core/how-to-update-references-to-the-bam-archive-database-name.md)<br /><br /> [如何更新 BAM 主要匯入資料庫名稱和連接字串的參考](../core/update-references-to-bam-primary-import-database-name-and-connection-string.md)<br /><br /> [如何更新參考 BAM Notification Services 資料庫](../core/how-to-update-references-to-the-bam-notification-services-databases.md)<br /><br /> [如何解析未完成的活動執行個體](../core/how-to-resolve-incomplete-activity-instances.md)|  
|如果您有使用「企業單一登入」，請還原主要密碼。|[管理主要密碼](../core/managing-the-master-secret.md)|  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)