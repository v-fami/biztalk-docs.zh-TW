---
title: 標示的交易，完整備份，並記錄備份 |Microsoft 文件
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
ms.openlocfilehash: ff71cbe7eb910c66530dee3264822eae121c0ce2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973588"
---
# <a name="marked-transactions-full-backups-and-log-backups"></a><span data-ttu-id="bca6b-102">標示的交易、完整備份和記錄備份</span><span class="sxs-lookup"><span data-stu-id="bca6b-102">Marked Transactions, Full Backups, and Log Backups</span></span>
<span data-ttu-id="bca6b-103">「 備份 BizTalk Server 」 工作建立的所有 BizTalk Server 資料庫使用完整資料庫備份和交易記錄備份，搭配一種稱為交易的已同步處理的備份*標示的交易*。</span><span class="sxs-lookup"><span data-stu-id="bca6b-103">The Backup BizTalk Server Job creates synchronized backups of all BizTalk Server databases by using full database backups and transaction log backups, in conjunction with a type of transaction known as a *marked transaction*.</span></span> <span data-ttu-id="bca6b-104">標示的交易是會在所有參與交易之資料庫的交易記錄中放置標示的交易。</span><span class="sxs-lookup"><span data-stu-id="bca6b-104">Marked transactions are transactions that place a mark into the transaction log of all databases participating in the transaction.</span></span> <span data-ttu-id="bca6b-105">標示的交易會阻止新的分散式交易啟動，並等候目前執行的分散式交易完成，然後再執行以放置標示。</span><span class="sxs-lookup"><span data-stu-id="bca6b-105">The marked transaction blocks new distributed transactions from starting, waits for the distributed transactions that are currently running to complete, and then executes to place the mark.</span></span>  
  
 <span data-ttu-id="bca6b-106">標示代表在所有資料庫中皆一致的交易點；您可以搭配後續的記錄備份使用此標示，將資料庫還原至該點。</span><span class="sxs-lookup"><span data-stu-id="bca6b-106">The mark represents a transaction point that is consistent across all databases; you can use the mark with subsequent log backups to restore your databases to that point.</span></span>  
  
 <span data-ttu-id="bca6b-107">在每個 BizTalk Server 資料庫中，「備份 BizTalk Server」工作會在每次執行時建立標示的交易記錄備份，並且依據您指定的時間週期建立完整備份。</span><span class="sxs-lookup"><span data-stu-id="bca6b-107">For each BizTalk Server database, the Backup BizTalk Server job creates a marked transaction log backup every time it runs, and it creates a full backup based on a time period that you specify.</span></span>  
  
## <a name="full-backups"></a><span data-ttu-id="bca6b-108">完整備份</span><span class="sxs-lookup"><span data-stu-id="bca6b-108">Full backups</span></span>  
 <span data-ttu-id="bca6b-109">當您執行 「 備份 BizTalk Server 」 工作執行的第一個備份程序*BackupFull*，一次每個週期 （而非每次執行作業時）。</span><span class="sxs-lookup"><span data-stu-id="bca6b-109">When you run the Backup BizTalk Server job it runs the first backup process, *BackupFull*, once every period (not every time the job runs).</span></span> <span data-ttu-id="bca6b-110">如需如何排程 「 備份 BizTalk Server 」 工作的詳細資訊，請參閱[如何排程 「 備份 BizTalk Server 」 工作](../core/how-to-schedule-the-backup-biztalk-server-job.md)。</span><span class="sxs-lookup"><span data-stu-id="bca6b-110">For more information about how to schedule the Backup BizTalk Server job, see [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md).</span></span>  
  
 <span data-ttu-id="bca6b-111">「備份 BizTalk Server」工作會在新週期第一次執行時執行完整備份。</span><span class="sxs-lookup"><span data-stu-id="bca6b-111">The first time the Backup BizTalk Server job runs during a new period, it performs a full backup.</span></span> <span data-ttu-id="bca6b-112">例如，如果您將工作排程為每小時執行，卻將週期設定為每日，那麼「備份 BizTalk Server」工作會在第一次執行時執行完整備份，此後則每日在午夜執行。</span><span class="sxs-lookup"><span data-stu-id="bca6b-112">For example, if you schedule the job to run every hour but configure the period to be daily, the Backup BizTalk Server job performs a full backup the first time it runs, and then every day at midnight.</span></span>  
  
## <a name="transaction-log-backups"></a><span data-ttu-id="bca6b-113">交易記錄備份</span><span class="sxs-lookup"><span data-stu-id="bca6b-113">Transaction log backups</span></span>  
 <span data-ttu-id="bca6b-114">「 備份 BizTalk Server 」 工作執行的第二個程序是*MarkAndBackupLog*。</span><span class="sxs-lookup"><span data-stu-id="bca6b-114">The second process that the Backup BizTalk Server job performs is *MarkAndBackupLog*.</span></span> <span data-ttu-id="bca6b-115">此程序會在所有 BizTalk Server 資料庫中放置標示，並且每次在工作執行時執行交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="bca6b-115">This process places a mark in all BizTalk Server databases and performs a transaction log backup every time the job executes.</span></span>  
  
 <span data-ttu-id="bca6b-116">此標示是使用建立的字串 *\<ServerName\>*_*\<DatabaseName\>*_Log\_  *\<LogMarkName\>*\_*\<時間戳記\>*.bak，其中*\<記錄標示名稱\>* 設定中的 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="bca6b-116">The mark is the string created by using *\<ServerName\>*_*\<DatabaseName\>*_Log\_*\<LogMarkName\>*\_*\<Timestamp\>*.bak, where the *\<Log Mark Name\>* is configured in the SQL Server Agent job.</span></span> <span data-ttu-id="bca6b-117">還原上一個記錄至每個資料庫時，必須使用這個標示。</span><span class="sxs-lookup"><span data-stu-id="bca6b-117">This mark must be used when restoring the last log to each database.</span></span>  
  
 <span data-ttu-id="bca6b-118">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜相關資料庫的備份與復原＞(英文)。</span><span class="sxs-lookup"><span data-stu-id="bca6b-118">For more information, see "Transaction Log Backups" and "Backup and Recovery of Related Databases" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca6b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="bca6b-119">See Also</span></span>  
 [<span data-ttu-id="bca6b-120">備份和還原的進階資訊</span><span class="sxs-lookup"><span data-stu-id="bca6b-120">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)