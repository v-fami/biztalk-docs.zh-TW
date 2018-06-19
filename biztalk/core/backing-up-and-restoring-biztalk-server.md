---
title: 備份和還原 BizTalk Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe03a75a-1ea6-4ccc-9543-7989ec6b1cff
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1adac25b23c69b51e07ed5f30768d046a453887a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230782"
---
# <a name="backing-up-and-restoring-biztalk-server"></a><span data-ttu-id="7cefc-102">備份和還原 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7cefc-102">Backing Up and Restoring BizTalk Server</span></span>
<span data-ttu-id="7cefc-103">當發生硬體故障時，擁有良好的 BizTalk Server 資料庫與元件備份是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="7cefc-103">In the event of hardware failure, having a good backup of your BizTalk Server databases and components is essential.</span></span> <span data-ttu-id="7cefc-104">良好的備份可讓您進行還原，而只有輕微的損失或毫無損失。</span><span class="sxs-lookup"><span data-stu-id="7cefc-104">A good backup will enable you to recover with little or no data loss.</span></span> <span data-ttu-id="7cefc-105">BizTalk Server 的還原方式根據發生硬體故障的系統上所安裝的元件而不同。</span><span class="sxs-lookup"><span data-stu-id="7cefc-105">How you restore BizTalk Server depends on which components were installed on the system where hardware failure occurred.</span></span> <span data-ttu-id="7cefc-106">本指南包含下列硬體故障的情況：</span><span class="sxs-lookup"><span data-stu-id="7cefc-106">This guide covers the following hardware failure scenarios:</span></span>  
  
 <span data-ttu-id="7cefc-107">**執行 BizTalk Server 的電腦硬體發生故障**</span><span class="sxs-lookup"><span data-stu-id="7cefc-107">**Hardware failure in the computer running BizTalk Server**</span></span>  
  
 <span data-ttu-id="7cefc-108">如果 BizTalk 群組不是設計為高可用性，當執行 BizTalk Server 的電腦硬體發生故障時，可能導致系統停機或效能降低。</span><span class="sxs-lookup"><span data-stu-id="7cefc-108">A hardware failure in the computer running BizTalk Server may cause system downtime or degraded performance if the BizTalk group is not designed for high availability.</span></span> <span data-ttu-id="7cefc-109">如需如何建立高可用性的 BizTalk 群組的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。</span><span class="sxs-lookup"><span data-stu-id="7cefc-109">For more information about how to create a highly available BizTalk group, see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
 <span data-ttu-id="7cefc-110">若要確保可在硬體故障時替換執行 BizTalk Server 的電腦，您必須備份該電腦上的 BizTalk Server 元件。</span><span class="sxs-lookup"><span data-stu-id="7cefc-110">To ensure that you can replace a computer running BizTalk Server after a hardware failure, you must back up the BizTalk Server components on that computer.</span></span> <span data-ttu-id="7cefc-111">如需如何備份和還原執行 BizTalk Server 的電腦的詳細資訊，請參閱[Backing Up a 的電腦執行 BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)和[復原電腦執行 BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7cefc-111">For more information about how to back up and restore a computer running BizTalk Server, see [Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) and [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="7cefc-112">**執行 SQL Server 的電腦硬體發生故障**</span><span class="sxs-lookup"><span data-stu-id="7cefc-112">**Hardware failure in the computer running SQL Server**</span></span>  
  
 <span data-ttu-id="7cefc-113">您可以使用 SQL Server 叢集來降低執行 SQL Server 的電腦發生硬體故障的風險。</span><span class="sxs-lookup"><span data-stu-id="7cefc-113">You can minimize the risk of a hardware failure in a computer running SQL Server by using SQL Server clustering.</span></span> <span data-ttu-id="7cefc-114">但即使您使用了 SQL Server 叢集，包含 BizTalk Server 資料庫的 SQL 伺服器還是有可能發生無法還原的硬體故障。</span><span class="sxs-lookup"><span data-stu-id="7cefc-114">Even when using SQL Server clustering, however, there may be situations when the SQL server(s) containing the BizTalk Server databases experiences an unrecoverable hardware failure.</span></span> <span data-ttu-id="7cefc-115">例如，整個資料層都發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7cefc-115">For example, the entire data tier suffered a failure.</span></span> <span data-ttu-id="7cefc-116">在這樣的情況下，您必須還原最近備份的資料庫集以恢復 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="7cefc-116">In these situations, you must revive the BizTalk group by restoring the most recent set of backed up databases.</span></span>  
  
 <span data-ttu-id="7cefc-117">如需為 BizTalk Server 資料庫提供容錯功能的詳細資訊，請參閱[的 BizTalk Server 資料庫提供高可用性](../core/providing-high-availability-for-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="7cefc-117">For more information about providing fault tolerance for the BizTalk Server databases, see [Providing High Availability for BizTalk Server Databases](../core/providing-high-availability-for-biztalk-server-databases.md).</span></span> <span data-ttu-id="7cefc-118">發生嚴重的 SQL Server 失敗發生的停機時間，您應該依照[Backing Up and Restoring BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="7cefc-118">In the case of a catastrophic SQL Server failure where downtime has occurred, you should follow the instructions in [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md).</span></span>  
  
 <span data-ttu-id="7cefc-119">如果發生硬體故障的電腦上同時安裝了 SQL Server 與 BizTalk Server，您應該先還原 BizTalk Server 資料庫，再還原 BizTalk Server 元件。</span><span class="sxs-lookup"><span data-stu-id="7cefc-119">If you experience a hardware failure on a computer where both SQL Server and BizTalk Server are installed, you should restore the BizTalk Server databases, and then recover the BizTalk Server components.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7cefc-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="7cefc-120">In This Section</span></span>  
  
-   [<span data-ttu-id="7cefc-121">檢查清單： 備份與還原</span><span class="sxs-lookup"><span data-stu-id="7cefc-121">Checklist: Backup and Restore</span></span>](../core/checklist-backup-and-restore.md)  
  
-   [<span data-ttu-id="7cefc-122">備份和還原的最佳作法</span><span class="sxs-lookup"><span data-stu-id="7cefc-122">Best Practices for Backup and Restore</span></span>](../core/best-practices-for-backup-and-restore.md)  
  
-   [<span data-ttu-id="7cefc-123">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="7cefc-123">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="7cefc-124">執行 BizTalk Server 之電腦的嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="7cefc-124">Disaster Recovery for Computers Running BizTalk Server</span></span>](../core/disaster-recovery-for-computers-running-biztalk-server.md)  
  
-   [<span data-ttu-id="7cefc-125">備份執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="7cefc-125">Backing Up a Computer Running BizTalk Server</span></span>](../core/backing-up-a-computer-running-biztalk-server.md)  
  
-   [<span data-ttu-id="7cefc-126">復原執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="7cefc-126">Recovering a Computer Running BizTalk Server</span></span>](../core/recovering-a-computer-running-biztalk-server.md)