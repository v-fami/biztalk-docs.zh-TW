---
title: "備份和還原 BizTalk Server 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- backing up, transaction logs
- maintaining, restoring
- restoring, BizTalk Server
- maintaining, backing up
- transaction logs
ms.assetid: 7c08ce19-614c-4728-8dde-c40d4052339e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44bbb9316f1d036551acba5441424bcce65c2549
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-the-biztalk-server-databases"></a><span data-ttu-id="36ad0-102">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="36ad0-102">Backing Up and Restoring the BizTalk Server Databases</span></span>
<span data-ttu-id="36ad0-103">本節提供有關如何備份和還原 BizTalk Server 資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="36ad0-103">This section provides information about how to back up and restore the BizTalk Server databases.</span></span> <span data-ttu-id="36ad0-104">您應該遵循本節中的程序，以確保在發生硬體失敗時有能力還原前後一致的 BizTalk Server 環境。</span><span class="sxs-lookup"><span data-stu-id="36ad0-104">You should follow the procedures in this section to ensure your ability to restore a consistent BizTalk Server environment in the event of a hardware failure.</span></span> <span data-ttu-id="36ad0-105">BizTalk Server 會跨資料庫執行分散式交易，因此備份然後還原所有資料庫很重要。</span><span class="sxs-lookup"><span data-stu-id="36ad0-105">BizTalk Server performs distributed transactions across databases, so it is critical that you back up and then restore all databases.</span></span>  
  
 <span data-ttu-id="36ad0-106">BizTalk Server 需要使用完整資料庫備份和記錄備份並搭配交易式記錄標示的自訂備份程序。</span><span class="sxs-lookup"><span data-stu-id="36ad0-106">BizTalk Server requires a customized backup process that uses full database backups and log backups in conjunction with transactional log marking.</span></span> <span data-ttu-id="36ad0-107">此程序的相關資訊，請參閱[標示的交易、 完整備份和記錄檔備份](../core/marked-transactions-full-backups-and-log-backups.md)。</span><span class="sxs-lookup"><span data-stu-id="36ad0-107">For information about this process, see [Marked Transactions, Full Backups, and Log Backups](../core/marked-transactions-full-backups-and-log-backups.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36ad0-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="36ad0-108">In This Section</span></span>  
  
-   [<span data-ttu-id="36ad0-109">檢查清單： 備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="36ad0-109">Checklist: Back Up and Restore BizTalk Server Databases</span></span>](../core/checklist-back-up-and-restore-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="36ad0-110">備份和還原資料庫的最佳作法</span><span class="sxs-lookup"><span data-stu-id="36ad0-110">Best Practices for Backing Up and Restoring Databases</span></span>](../core/best-practices-for-backing-up-and-restoring-databases.md)  
  
-   [<span data-ttu-id="36ad0-111">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="36ad0-111">Backing Up and Restoring BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="36ad0-112">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="36ad0-112">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)  
  
-   [<span data-ttu-id="36ad0-113">解決資料遺失</span><span class="sxs-lookup"><span data-stu-id="36ad0-113">Resolving Data Loss</span></span>](../core/resolving-data-loss.md)  
  
-   [<span data-ttu-id="36ad0-114">備份和還原的相關進階的資訊</span><span class="sxs-lookup"><span data-stu-id="36ad0-114">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)