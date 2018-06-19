---
title: 更新 BAM 主要匯入資料庫的參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3da3b545-0d81-491b-bc37-0a980a7814b6
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ba37a32c82967e84b61bb46c58c62af9bf23b1b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301822"
---
# <a name="update-references-to-the-bam-primary-import-database"></a>更新 BAM 主要匯入資料庫的參考
如果在發生系統或資料失敗時，您已備份 BAM 主要匯入資料庫，則可以將該備份還原至不同的電腦，並重新命名此備份。  
  
 BAM 事件匯流排服務會將事件資料從 MessageBox 資料庫移至 BAM 主要匯入資料庫。 BAM 事件匯流排服務包含容錯邏輯，可讓它從意外的失敗中復原和重新啟動，而不會遺失任何資料。 如需有關 BAM 事件匯流排服務的詳細資訊，請參閱[管理 BAM 事件匯流排服務](http://go.microsoft.com/fwlink/?LinkID=154194)(http://go.microsoft.com/fwlink/?LinkID=154194)。  
  
 若要還原 BAM 主要匯入資料庫，執行中的步驟[如何還原資料庫中 「 備份 BizTalk Server 」 工作](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)。 此外，您必須以新的伺服器名稱和資料庫名稱更新 BAM SSIS 封裝。  
  
## <a name="how-to-update-references-to-bam-primary-import-database"></a>如何更新 BAM 主要匯入資料庫的參考  
 如需有關如何更新 BAM 主要匯入資料庫的參考指示[更新新的 BAM 主要匯入資料庫的參考](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef)。  
  
## <a name="see-also"></a>另請參閱  
 [備份 BAM 分析和追蹤 Analysis Server 資料庫](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)