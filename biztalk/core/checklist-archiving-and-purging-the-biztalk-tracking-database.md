---
title: "檢查清單： 封存和清除 BizTalk 追蹤資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- archiving [Tracking database], checklist
- checklists, purging [Tracking database]
- purging, checklist
- checklists, archiving [Tracking database]
ms.assetid: dccbf471-2add-498e-b292-287d9a94161b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22e97ac12e6b6b304318f57f309767ec7c63815f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-archiving-and-purging-the-biztalk-tracking-database"></a>檢查清單：封存和清除 BizTalk 追蹤資料庫
|步驟|參考|  
|----------|---------------|  
|閱讀「封存和清除」概觀，以更熟悉封存和清除追蹤資料的程序。|[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)|  
|雖然您可使用登入認證來執行 DTA 清除和封存工作，但是為了提高安全性，您應該以必要的 SQL Server 認證設定 BTS_BACKUP_USERS 角色，以執行 DTA 清除和封存工作。 如此可協助避免權限提升的情形發生。|[如何設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫的資料](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)|  
|設定 DTA 清除和封存工作。|[如何設定 DTA 清除與封存作業](../core/how-to-configure-the-dta-purge-and-archive-job.md)|  
|執行 DTA 清除和封存工作，此工作會封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫中的資料，並清除舊資料。|[如何從 BizTalk 追蹤資料庫清除資料](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)|  
|您可以選擇從 BizTalk 追蹤 (BizTalkDTADb) 資料庫手動清除資料。|[如何從 BizTalk 追蹤資料庫手動清除資料](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)|  
|從 BizTalk 追蹤 (BizTalkDTADb) 資料庫啟用封存資料的自動驗證。|[如何啟用自動封存驗證](../core/how-to-enable-automatic-archive-validation.md)|  
|將追蹤的訊息複製到 BizTalk 追蹤 (BizTalkDTADb) 資料庫。 若要使用「DTA 清除與封存」清除與封存工作來清除資料，則這是有必要的。|[如何將追蹤的訊息複製到 BizTalk 追蹤資料庫](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)|  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)