---
title: "如何還原 「 備份 BizTalk Server 」 工作中的資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bcac40f-ef0b-4ff0-8743-cf1614e14422
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb7c52b810343c1807e982e637372c74baeb84fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-databases-in-the-backup-biztalk-server-job"></a><span data-ttu-id="9626f-102">如何還原 「 備份 BizTalk Server 」 工作中的資料庫</span><span class="sxs-lookup"><span data-stu-id="9626f-102">How to Restore Databases in the Backup BizTalk Server Job</span></span>
<span data-ttu-id="9626f-103">本章節涵蓋上線所備份的 「 備份 BizTalk Server 」 工作的 BizTalk 群組中資料庫的步驟。</span><span class="sxs-lookup"><span data-stu-id="9626f-103">This section covers the steps to bring online the databases in the BizTalk group that are backed up by the Backup BizTalk Server job.</span></span> <span data-ttu-id="9626f-104">根據預設，所有資料庫都備份可以使用備份 BizTalk Server 作業，除了 BAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9626f-104">By default, all databases are backed up by using the Backup BizTalk Server job except for the BAM databases.</span></span> <span data-ttu-id="9626f-105">請參閱[還原 Analysis Services 和支援的資料庫](../technical-guides/restoring-analysis-services-and-supporting-databases.md)如需備份和還原 BAM 資料庫的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="9626f-105">See [Restoring Analysis Services and Supporting Databases](../technical-guides/restoring-analysis-services-and-supporting-databases.md) for more information about backup and restore of the BAM databases.</span></span> <span data-ttu-id="9626f-106">您必須將所有資料庫還原為相同的標記，以確保資料庫間的交易狀態一致。</span><span class="sxs-lookup"><span data-stu-id="9626f-106">You must restore all databases to the same mark to ensure a consistent transactional state among the databases.</span></span> <span data-ttu-id="9626f-107">如需詳細資訊，請參閱[標示的交易、 完整備份和記錄檔備份](http://go.microsoft.com/fwlink/?LinkId=151565)(http://go.microsoft.com/fwlink/?LinkId=151565)。</span><span class="sxs-lookup"><span data-stu-id="9626f-107">For more information, see [Marked Transactions, Full Backups, and Log Backups](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).</span></span>  
  
 <span data-ttu-id="9626f-108">如需詳細資訊和指示，關於還原資料庫的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[如何還原您的資料庫](http://go.microsoft.com/fwlink/?LinkId=151406)(http://go.microsoft.com/fwlink/?LinkId=151406)。</span><span class="sxs-lookup"><span data-stu-id="9626f-108">For more information and instructions about restoring databases for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [How to Restore Your Databases](http://go.microsoft.com/fwlink/?LinkId=151406) (http://go.microsoft.com/fwlink/?LinkId=151406).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9626f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9626f-109">See Also</span></span>  
 [<span data-ttu-id="9626f-110">還原資料庫不包含在備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="9626f-110">Restoring Databases Not Included in the Backup BizTalk Server Job</span></span>](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)