---
title: 如何還原資料庫，在 「 備份 BizTalk Server 」 工作中的 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9bcac40f-ef0b-4ff0-8743-cf1614e14422
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fde33b46937118aa29aa8259225da2c4d2c0439
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992407"
---
# <a name="how-to-restore-databases-in-the-backup-biztalk-server-job"></a><span data-ttu-id="c8998-102">如何還原資料庫中備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="c8998-102">How to Restore Databases in the Backup BizTalk Server Job</span></span>
<span data-ttu-id="c8998-103">本章節涵蓋上線的資料庫會由 「 備份 BizTalk Server 」 工作在 BizTalk 群組中的步驟。</span><span class="sxs-lookup"><span data-stu-id="c8998-103">This section covers the steps to bring online the databases in the BizTalk group that are backed up by the Backup BizTalk Server job.</span></span> <span data-ttu-id="c8998-104">根據預設，所有資料庫會都由使用 「 備份 BizTalk Server 」 作業，除了 BAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c8998-104">By default, all databases are backed up by using the Backup BizTalk Server job except for the BAM databases.</span></span> <span data-ttu-id="c8998-105">請參閱[還原 Analysis Services 和支援資料庫](../technical-guides/restoring-analysis-services-and-supporting-databases.md)如需備份和還原 BAM 資料庫的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c8998-105">See [Restoring Analysis Services and Supporting Databases](../technical-guides/restoring-analysis-services-and-supporting-databases.md) for more information about backup and restore of the BAM databases.</span></span> <span data-ttu-id="c8998-106">您必須將所有資料庫還原為相同的標記，以確保資料庫間的交易狀態一致。</span><span class="sxs-lookup"><span data-stu-id="c8998-106">You must restore all databases to the same mark to ensure a consistent transactional state among the databases.</span></span> <span data-ttu-id="c8998-107">如需詳細資訊，請參閱 <<c0> [ 標示的交易、 完整備份和記錄備份](http://go.microsoft.com/fwlink/?LinkId=151565)(http://go.microsoft.com/fwlink/?LinkId=151565)。</span><span class="sxs-lookup"><span data-stu-id="c8998-107">For more information, see [Marked Transactions, Full Backups, and Log Backups](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).</span></span>  
  
 <span data-ttu-id="c8998-108">如需詳細資訊和指示還原資料庫的相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 還原您的資料庫如何](http://go.microsoft.com/fwlink/?LinkId=151406)(<http://go.microsoft.com/fwlink/?LinkId=151406>)。</span><span class="sxs-lookup"><span data-stu-id="c8998-108">For more information and instructions about restoring databases for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [How to Restore Your Databases](http://go.microsoft.com/fwlink/?LinkId=151406) (<http://go.microsoft.com/fwlink/?LinkId=151406>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8998-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8998-109">See Also</span></span>  
 [<span data-ttu-id="c8998-110">還原不包含在備份 BizTalk Server 作業中的資料庫</span><span class="sxs-lookup"><span data-stu-id="c8998-110">Restoring Databases Not Included in the Backup BizTalk Server Job</span></span>](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)