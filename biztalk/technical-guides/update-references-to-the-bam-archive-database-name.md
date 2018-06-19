---
title: 更新 BAM 封存資料庫名稱的參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eed328e0-2826-4acb-952d-4a3a2844689e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16a04471e9f42744e4247f4202506839d2ade937
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302190"
---
# <a name="update-references-to-the-bam-archive-database-name"></a><span data-ttu-id="4ceda-102">更新 BAM 封存資料庫名稱的參考</span><span class="sxs-lookup"><span data-stu-id="4ceda-102">Update References to the BAM Archive Database Name</span></span>
<span data-ttu-id="4ceda-103">如果您已備份 BAM 封存資料庫，發生系統或資料失敗時可以將該備份還原至不同的電腦，您可以重新命名此備份。</span><span class="sxs-lookup"><span data-stu-id="4ceda-103">If you backed up your BAM Archive databases, in the event of a system or data failure you can restore that backup to a different computer, and you can rename the backup.</span></span>  
  
 <span data-ttu-id="4ceda-104">若要還原 BAM 封存資料庫，執行中的步驟[如何還原資料庫中 「 備份 BizTalk Server 」 工作](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)。</span><span class="sxs-lookup"><span data-stu-id="4ceda-104">To restore the BAM Archive databases, perform the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).</span></span> <span data-ttu-id="4ceda-105">此外，您必須以新的伺服器名稱和資料庫名稱更新 BAM SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="4ceda-105">In addition, you must update the BAM SSIS packages with the new server name and database name.</span></span>  
  
## <a name="how-to-update-references-to-bam-archive-database"></a><span data-ttu-id="4ceda-106">如何更新 BAM 封存資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="4ceda-106">How to Update References to BAM Archive Database</span></span>  
 <span data-ttu-id="4ceda-107">如需有關如何更新 BAM 封存資料庫的參考的指示，請參閱[更新新的 BAM 封存資料庫的參考](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArch)。</span><span class="sxs-lookup"><span data-stu-id="4ceda-107">For instructions on how to update references to BAM Archive database, see [Updating References to the New BAM Archive Database](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArch).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ceda-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ceda-108">See Also</span></span>  
 [<span data-ttu-id="4ceda-109">備份 BAM 分析和追蹤 Analysis Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="4ceda-109">Backing Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)