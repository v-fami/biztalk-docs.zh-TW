---
title: 更新 BAM Analysis Server 和星狀結構描述資料庫名稱參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 319caa26-1292-4453-a316-efca4fbffdb6
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184ab156770b0a62208a8e24c7870afa43d3a128
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302230"
---
# <a name="update-references-to-the-bam-analysis-server-and-star-schema-database-names"></a><span data-ttu-id="09252-102">在 BAM Analysis Server 和星狀結構描述資料庫名稱更新參考</span><span class="sxs-lookup"><span data-stu-id="09252-102">Update References to the BAM Analysis Server and Star Schema Database Names</span></span>
<span data-ttu-id="09252-103">如果您已備份 BAM 分析資料庫，則可以在發生系統或資料失敗時，將該備份還原到不同的電腦，並將此備份重新命名。</span><span class="sxs-lookup"><span data-stu-id="09252-103">If you backed up your BAM Analysis database, in the event of a system or data failure you can restore that backup to a different computer and you can rename the backup.</span></span>  
  
 <span data-ttu-id="09252-104">若要還原 BAM 分析和星狀結構描述的資料庫，執行中的步驟[如何還原資料庫中 「 備份 BizTalk Server 」 工作](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)。</span><span class="sxs-lookup"><span data-stu-id="09252-104">To restore the BAM Analysis and Star Schema databases, perform the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).</span></span> <span data-ttu-id="09252-105">此外，您必須更新 BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Integration Services (SSIS) 封裝，以新的伺服器名稱和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="09252-105">In addition, you must update the BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Integration Services (SSIS) packages with the new server name and database name.</span></span>  
  
## <a name="how-to-update-references-to-bam-analysis-server-and-star-schema-database-names"></a><span data-ttu-id="09252-106">如何更新 BAM Analysis Server 和星狀結構描述資料庫名稱的參考</span><span class="sxs-lookup"><span data-stu-id="09252-106">How to Update References to BAM Analysis Server and Star Schema Database Names</span></span>  
 <span data-ttu-id="09252-107">如需有關如何更新 BAM Analysis server 資料庫的參考的指示，請參閱[更新新的 BAM 分析資料庫的參考](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate)。</span><span class="sxs-lookup"><span data-stu-id="09252-107">For instructions on how to update references to BAM Analysis server databases, see [Updating References to the New BAM Analysis Database](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate).</span></span> <span data-ttu-id="09252-108">如需有關如何更新 BAM 星狀結構描述資料庫的參考的指示，請參閱[更新新的 BAM 星狀結構描述資料庫的參考](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate)。</span><span class="sxs-lookup"><span data-stu-id="09252-108">For instructions on how to update references to the BAM Star Schema databases, see [Updating References to the New BAM Star Schema Database](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate).</span></span>