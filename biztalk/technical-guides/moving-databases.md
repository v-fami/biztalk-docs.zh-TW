---
title: 移動資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a0d09a1-90a5-4a5d-a783-b979724e101b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15562fc1fb642a4766190dabe912e81b38bb1ea8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972415"
---
# <a name="moving-databases"></a><span data-ttu-id="60589-102">移動資料庫</span><span class="sxs-lookup"><span data-stu-id="60589-102">Moving Databases</span></span>
<span data-ttu-id="60589-103">建議的方法，移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（除了商務活動監控 (BAM) 資料庫中） 的資料庫是設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]一節中所述，記錄傳送[嚴重損壞修復](../technical-guides/disaster-recovery.md)。</span><span class="sxs-lookup"><span data-stu-id="60589-103">The recommended method for moving [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases (except for the Business Activity Monitoring (BAM) databases) is to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping as described in the section [Disaster Recovery](../technical-guides/disaster-recovery.md).</span></span> <span data-ttu-id="60589-104">使用 BAM，所有的資料庫除外[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以備份資料庫使用**備份 BizTalk Server** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="60589-104">With the exception of the databases used by BAM, all of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases can be backed up by using the **Backup BizTalk Server**[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent job.</span></span> <span data-ttu-id="60589-105">如需有關這項作業的詳細資訊，請參閱 <<c0> [ 如何排程 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/?LinkId=154674)(<http://go.microsoft.com/fwlink/?LinkId=154674>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="60589-105">For more information about this job, see [How to Schedule the Backup BizTalk Server Job](http://go.microsoft.com/fwlink/?LinkId=154674) (<http://go.microsoft.com/fwlink/?LinkId=154674>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="60589-106">本章節描述如何移動 BAM 相關的資料庫以及如何移動其餘[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，而不先設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="60589-106">This section describes how to move the BAM-related databases and how to move the remaining [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases without first configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping.</span></span> <span data-ttu-id="60589-107">升級時，這種方法可能會很有用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫或在其他情況下，不會與災害復原。</span><span class="sxs-lookup"><span data-stu-id="60589-107">This approach may be useful when upgrading the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases or in other scenarios that are not related to disaster recovery.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60589-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="60589-108">In This Section</span></span>  
  
-   [<span data-ttu-id="60589-109">移動 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="60589-109">Moving BAM Databases</span></span>](../technical-guides/moving-bam-databases.md)  
  
-   [<span data-ttu-id="60589-110">移動非 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="60589-110">Moving Non-BAM Databases</span></span>](../technical-guides/moving-non-bam-databases.md)  
  
## <a name="see-also"></a><span data-ttu-id="60589-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60589-111">See Also</span></span>  
 [<span data-ttu-id="60589-112">管理 BizTalk Server2</span><span class="sxs-lookup"><span data-stu-id="60589-112">Managing BizTalk Server2</span></span>](../technical-guides/managing-biztalk-server2.md)