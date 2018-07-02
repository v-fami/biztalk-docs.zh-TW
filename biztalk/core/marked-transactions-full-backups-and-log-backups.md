---
title: 標示的交易，完整備份，備份和記錄備份 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, transaction logs
- backing up, full backups
- transaction logs
- backing up, backup jobs
ms.assetid: a383a16d-1e40-4b0b-a515-f1cb90bfb4d2
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a22f02fe6dde63c01707d15f4210c29f52f112e8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974839"
---
# <a name="marked-transactions-full-backups-and-log-backups"></a>標示的交易、完整備份和記錄備份
「 備份 BizTalk Server 」 工作會建立已同步處理的備份所有 BizTalk Server 資料庫使用完整資料庫備份和交易記錄備份，搭配一種稱為交易*標示的交易*。 標示的交易是會在所有參與交易之資料庫的交易記錄中放置標示的交易。 標示的交易會阻止新的分散式交易啟動，並等候目前執行的分散式交易完成，然後再執行以放置標示。  
  
 標示代表在所有資料庫中皆一致的交易點；您可以搭配後續的記錄備份使用此標示，將資料庫還原至該點。  
  
 在每個 BizTalk Server 資料庫中，「備份 BizTalk Server」工作會在每次執行時建立標示的交易記錄備份，並且依據您指定的時間週期建立完整備份。  
  
## <a name="full-backups"></a>完整備份  
 當您執行 「 備份 BizTalk Server 」 工作執行的第一個備份程序*BackupFull*，一次在每個週期 （而非每次執行作業時）。 如需如何排程 「 備份 BizTalk Server 」 工作的詳細資訊，請參閱[如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)。  
  
 「備份 BizTalk Server」工作會在新週期第一次執行時執行完整備份。 例如，如果您將工作排程為每小時執行，卻將週期設定為每日，那麼「備份 BizTalk Server」工作會在第一次執行時執行完整備份，此後則每日在午夜執行。  
  
## <a name="transaction-log-backups"></a>交易記錄備份  
 「 備份 BizTalk Server 」 工作執行的第二個程序會*MarkAndBackupLog*。 此程序會在所有 BizTalk Server 資料庫中放置標示，並且每次在工作執行時執行交易記錄備份。  
  
 Mark 是使用建立的字串 *\<ServerName\>*<em>*\<DatabaseName\>*（_l)\\</em>   *\<LogMarkName\>*\_*\<Timestamp\>*.bak，其中 *\<記錄標示名稱\>* 已在 SQL Server Agent 作業中。 還原上一個記錄至每個資料庫時，必須使用這個標示。  
  
 如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜相關資料庫的備份與復原＞(英文)。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原的進階資訊](../core/advanced-information-about-backup-and-restore1.md)