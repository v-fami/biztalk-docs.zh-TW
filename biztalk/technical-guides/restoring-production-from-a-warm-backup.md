---
title: 從暖備份還原生產 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bda14b8-b3cc-4a5e-a353-fca5885fd594
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66177cd1f6f10e252a71d2875b4079e660125719
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971359"
---
# <a name="restoring-production-from-a-warm-backup"></a><span data-ttu-id="2631d-102">從暖備份還原生產環境</span><span class="sxs-lookup"><span data-stu-id="2631d-102">Restoring Production from a Warm Backup</span></span>
<span data-ttu-id="2631d-103">如果來源系統變得不可靠，您可從目的地的資料庫還原至原始檔。</span><span class="sxs-lookup"><span data-stu-id="2631d-103">If the source system becomes unreliable, it is possible to restore the databases from the destination to the source.</span></span> <span data-ttu-id="2631d-104">執行下列程序，將來自目的地的資料庫還原至原始檔。</span><span class="sxs-lookup"><span data-stu-id="2631d-104">Perform the following procedure to restore databases from the destination to the source.</span></span>  
  
### <a name="to-restore-the-databases-from-the-destination-to-the-source-follow-these-steps"></a><span data-ttu-id="2631d-105">若要還原目的地的資料庫來源請遵循下列步驟</span><span class="sxs-lookup"><span data-stu-id="2631d-105">To restore the databases from the destination to the source follow these steps</span></span>  
  
1. <span data-ttu-id="2631d-106">停用來源 （生產） 上的所有備份工作[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-106">Disable all backup jobs on the source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
2. <span data-ttu-id="2631d-107">所有還原目的地的災害復原 (DR) 上完成的工作等候[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-107">Wait for all restore jobs to complete on the destination disaster recovery (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
3. <span data-ttu-id="2631d-108">停用的目的地 (DR) 上的所有還原作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-108">Disable all restore jobs on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
4. <span data-ttu-id="2631d-109">還原所有資料庫與目的地 (DR) 上的 STOPATMARK[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-109">Restore all databases with STOPATMARK on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
5. <span data-ttu-id="2631d-110">停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所有 BizTalk 伺服器上的服務。</span><span class="sxs-lookup"><span data-stu-id="2631d-110">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services on all BizTalk servers.</span></span>  
  
6. <span data-ttu-id="2631d-111">卸除所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關來源 （生產） 上的資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-111">Drop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related databases on the source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
7. <span data-ttu-id="2631d-112">所有資料庫 （完整） 都備份目的地 (DR) 上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-112">Back up (full) all databases on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
8. <span data-ttu-id="2631d-113">還原 （完整） 與所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份在步驟 7 到來源 （生產）[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-113">Restore (full) all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases backed up in step 7 to the source (production) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
9. <span data-ttu-id="2631d-114">重新啟動所有 BizTalk 伺服器，包括主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="2631d-114">Restart all BizTalk servers including the master secret server.</span></span>  
  
10. <span data-ttu-id="2631d-115">卸除所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關的目的地 (DR) 上的資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-115">Drop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related databases on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
11. <span data-ttu-id="2631d-116">啟用來源上的備份作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-116">Enable backup jobs on the source [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
12. <span data-ttu-id="2631d-117">啟用目的地 (DR) 上的還原作業[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2631d-117">Enable restore jobs on the destination (DR) [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2631d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2631d-118">See Also</span></span>  
 [<span data-ttu-id="2631d-119">備份和 Restore2 進階的資訊</span><span class="sxs-lookup"><span data-stu-id="2631d-119">Advanced Information About Backup and Restore2</span></span>](../technical-guides/advanced-information-about-backup-and-restore2.md)