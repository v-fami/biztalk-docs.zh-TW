---
title: 記錄傳送 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- log shipping
ms.assetid: 25bc9724-1c99-43d0-8cd1-3ed8eaa60268
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd90e23fc99988bb134a77befe3195ca507037d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262110"
---
# <a name="log-shipping"></a><span data-ttu-id="a6fdc-102">記錄傳送</span><span class="sxs-lookup"><span data-stu-id="a6fdc-102">Log Shipping</span></span>
<span data-ttu-id="a6fdc-103">記錄傳送提供待命伺服器功能，有時稱為暖備份，發生系統錯誤時可減少停機時間。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-103">Log shipping provides standby server capabilities, sometimes called a warm backup, which reduces downtime in the event of a system failure.</span></span>  
  
 <span data-ttu-id="a6fdc-104">由於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的分散式資料庫設計，當您產生備份時，必須要提供一致的位置以便還原備份。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-104">Due to the distributed database design of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], when you produce backups you must be certain to provide a consistent point to which the backups can be restored.</span></span> <span data-ttu-id="a6fdc-105">交易可以跨越多個資料庫；如果一個資料庫離線且必須要還原，則所有相關的資料庫都必須即時還原到單一位置，以確保系統保持一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-105">Transactions can span multiple databases; if one database goes offline and must be restored, then all related databases must be restored to a single point in time to ensure that the system is in a consistent state.</span></span> <span data-ttu-id="a6fdc-106">並非所有資料庫都參與分散式交易。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-106">Not all databases participate in distributed transactions.</span></span> <span data-ttu-id="a6fdc-107">如需詳細資訊，請參閱[Backing Up and Restoring BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-107">For more information, see [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md).</span></span>  
  
 <span data-ttu-id="a6fdc-108">「備份 BizTalk Server」工作會使用 Microsoft SQL Server 記錄檔標示，以提供自動化程序來產生資料庫備份集。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-108">The Backup BizTalk Server job uses Microsoft SQL Server log marking to provide an automated process that produces database backup sets.</span></span> <span data-ttu-id="a6fdc-109">這些備份集包括同步處理的位置，可在還原程序期間使用。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-109">These backup sets include synchronized points that are used during the restoration process.</span></span> <span data-ttu-id="a6fdc-110">做為還原由「備份 BizTalk Server」工作產生一組資料庫的部分程序，使用倒數第二個標示，將每個資料庫的最後一個記錄備份檔案還原為特定的記錄標示。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-110">As part of the process of restoring a set of databases produced by the Backup BizTalk Server job, the last log backup file for each database is restored to a specific log mark, using the second to last mark.</span></span> <span data-ttu-id="a6fdc-111">這可讓您將資料庫還原為一致的狀態，大幅減少資料遺失的數量。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-111">This enables you to restore your databases to a consistent state and significantly reduce the amount of data lost.</span></span> <span data-ttu-id="a6fdc-112">應該使用倒數第二個記錄標示。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-112">The log mark before the last one should be used.</span></span> <span data-ttu-id="a6fdc-113">雖然 SQL Server 包含記錄傳送功能，您應該只在備份和還原 BizTalk Server 資料庫時使用 BizTalk Server 記錄傳送功能。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-113">Although SQL Server includes a log shipping feature, you should only use the BizTalk Server log shipping feature when backing up and restoring BizTalk Server databases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6fdc-114">SQL Server 簡單復原模式不支援搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫使用，因為簡單復原模式不會備份交易記錄，因此無法維護最近一次備份後的活動記錄內容。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-114">The SQL Server simple recovery model is not supported for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases because the simple recovery model does not backup the transaction log and therefore does not maintain a record of activity since the most recent backup.</span></span>  <span data-ttu-id="a6fdc-115">將 SQL Server 設定為使用完整復原模式，可以確保 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫備份集的資料完整性。</span><span class="sxs-lookup"><span data-stu-id="a6fdc-115">Configure SQL Server to use the full recovery model to ensure the integrity of data in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backup sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fdc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6fdc-116">See Also</span></span>  
 [<span data-ttu-id="a6fdc-117">備份和還原的相關進階的資訊</span><span class="sxs-lookup"><span data-stu-id="a6fdc-117">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)