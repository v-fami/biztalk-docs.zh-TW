---
title: "災害復原的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afbb0a57-0d31-4a2f-847c-02b40361c0ed
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e988055205203c5c4bc7a4d9d6e84706414967c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-disaster-recovery"></a><span data-ttu-id="ee952-102">災害復原的最佳作法</span><span class="sxs-lookup"><span data-stu-id="ee952-102">Best Practices for Disaster Recovery</span></span>
<span data-ttu-id="ee952-103">如需有關災害復原的最佳作法資訊[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，請參閱[的備份與還原最佳作法](http://go.microsoft.com/fwlink/?LinkId=151391)(http://go.microsoft.com/fwlink/?LinkId=151391) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]協助。</span><span class="sxs-lookup"><span data-stu-id="ee952-103">For information about best practices for disaster recovery for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], see [Best Practices for Backup and Restore](http://go.microsoft.com/fwlink/?LinkId=151391) (http://go.microsoft.com/fwlink/?LinkId=151391) in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="ee952-104">**建立備份和還原計劃**</span><span class="sxs-lookup"><span data-stu-id="ee952-104">**Create a backup and restore plan**</span></span>  
  
-   <span data-ttu-id="ee952-105">確定您的備份計劃指定了下列項目：</span><span class="sxs-lookup"><span data-stu-id="ee952-105">Be sure your backup plan specifies:</span></span>  
  
    -   <span data-ttu-id="ee952-106">用以儲存備份的電腦</span><span class="sxs-lookup"><span data-stu-id="ee952-106">The computer where backups will be stored</span></span>  
  
    -   <span data-ttu-id="ee952-107">用以備份系統的程式</span><span class="sxs-lookup"><span data-stu-id="ee952-107">The programs that you will use to back up your system</span></span>  
  
    -   <span data-ttu-id="ee952-108">您要備份的電腦</span><span class="sxs-lookup"><span data-stu-id="ee952-108">The computers you want to back up</span></span>  
  
    -   <span data-ttu-id="ee952-109">產生備份的排程</span><span class="sxs-lookup"><span data-stu-id="ee952-109">The schedule when backups will occur</span></span>  
  
    -   <span data-ttu-id="ee952-110">可封存備份的公司之外位置</span><span class="sxs-lookup"><span data-stu-id="ee952-110">The offsite location where you will archive backups</span></span>  
  
 <span data-ttu-id="ee952-111">**BizTalk Server 系統保留所有變更的記錄**</span><span class="sxs-lookup"><span data-stu-id="ee952-111">**Keep a written record of all changes to your BizTalk Server system**</span></span>  
  
-   <span data-ttu-id="ee952-112">請確定記下系統的所有變更，例如已套用的 Service Pack、Hotfix 以及 QFE。</span><span class="sxs-lookup"><span data-stu-id="ee952-112">Be sure to write down all changes to your system, such as service packs, hotfixes, and QFEs that have been applied.</span></span> <span data-ttu-id="ee952-113">這個動作非常重要，它可讓您的系統儘可能還原成接近硬體失敗前的狀態。</span><span class="sxs-lookup"><span data-stu-id="ee952-113">This is crucial to getting your system restored as closely as possible to what existed before the hardware failure.</span></span>  
  
 <span data-ttu-id="ee952-114">**實作下列措施來協助防止或嚴重損壞的影響降至最低**</span><span class="sxs-lookup"><span data-stu-id="ee952-114">**Implement the following measures to help prevent or minimize the effect of a disaster**</span></span>  
  
-   <span data-ttu-id="ee952-115">取得軟體和韌體更新。</span><span class="sxs-lookup"><span data-stu-id="ee952-115">Have your software and firmware updates available.</span></span>  
  
-   <span data-ttu-id="ee952-116">安全存放軟體磁片以便隨時取用。</span><span class="sxs-lookup"><span data-stu-id="ee952-116">Have all software disks readily available.</span></span>  
  
-   <span data-ttu-id="ee952-117">擬定主動監視伺服器的計劃。</span><span class="sxs-lookup"><span data-stu-id="ee952-117">Have a plan to monitor servers proactively.</span></span> <span data-ttu-id="ee952-118">這是非常重要，因為失敗之主控件上的協調流程執行個體可能會復原第二部主機的最多 10 分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="ee952-118">This is very important since orchestration instances on a failed host may not be recovered by a second host for up to 10 minutes.</span></span>  
  
-   <span data-ttu-id="ee952-119">維護硬體記錄。</span><span class="sxs-lookup"><span data-stu-id="ee952-119">Maintain hardware records.</span></span>  
  
-   <span data-ttu-id="ee952-120">維護軟體記錄。</span><span class="sxs-lookup"><span data-stu-id="ee952-120">Maintain software records.</span></span>  
  
 <span data-ttu-id="ee952-121">**在硬體或軟體層級組織中實作容錯功能**</span><span class="sxs-lookup"><span data-stu-id="ee952-121">**Implement fault tolerance in your organization at the hardware or software level**</span></span>  
  
-   <span data-ttu-id="ee952-122">實作叢集及獨立磁碟容錯陣列 (RAID) 可確保您的系統能在硬體失敗之後繼續運作。</span><span class="sxs-lookup"><span data-stu-id="ee952-122">Implementing clusters and redundant array of independent disks (RAID) helps ensure that your system can survive a hardware failure.</span></span>  
  
 <span data-ttu-id="ee952-123">**保存在安全的位置以規則為基礎的備份媒體**</span><span class="sxs-lookup"><span data-stu-id="ee952-123">**Archive the backup media on a regular basis in a secure location**</span></span>  
  
-   <span data-ttu-id="ee952-124">建立排程，以定期封存備份媒體，並將封存儲存在公司外安全的位置。</span><span class="sxs-lookup"><span data-stu-id="ee952-124">Create a schedule for archiving your backup media on a regular basis and keep the archives in a secure, offsite location.</span></span> <span data-ttu-id="ee952-125">這可確保您需要備份時可隨時取得備份。</span><span class="sxs-lookup"><span data-stu-id="ee952-125">This ensures that you have a backup available when you need it.</span></span>  
  
 <span data-ttu-id="ee952-126">**確認備份的完整性，並執行無誤**</span><span class="sxs-lookup"><span data-stu-id="ee952-126">**Verify the integrity of your backups and that they occur without error**</span></span>  
  
-   <span data-ttu-id="ee952-127">監視所有的備份工作，確定其成功完成，沒有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="ee952-127">Monitor all of your backup jobs and ensure that they complete without any errors.</span></span>  
  
 <span data-ttu-id="ee952-128">**保留相同的備用硬體**</span><span class="sxs-lookup"><span data-stu-id="ee952-128">**Keep identical spare hardware available**</span></span>  
  
-   <span data-ttu-id="ee952-129">具有相同的備用硬體，可確保您可以快速地取代才能啟動硬體故障和更快速地執行。</span><span class="sxs-lookup"><span data-stu-id="ee952-129">Having identical spare hardware available ensures that you can quickly replace defective hardware to get up and running more quickly.</span></span>  
  
 <span data-ttu-id="ee952-130">**文件和測試您的復原程序**</span><span class="sxs-lookup"><span data-stu-id="ee952-130">**Document and test your recovery procedures**</span></span>  
  
-   <span data-ttu-id="ee952-131">在實際環境中執行系統之前，應該先執行損毀修復測試。</span><span class="sxs-lookup"><span data-stu-id="ee952-131">Disaster recovery testing should be conducted before ever running your system in production.</span></span> <span data-ttu-id="ee952-132">妥當計畫並執行發行前測試，將確保您的 IT 人員可復原 BizTalk Server 系統。</span><span class="sxs-lookup"><span data-stu-id="ee952-132">Having plans in place and performing prerelease testing will ensure that your IT staff can recover your BizTalk Server systems.</span></span>  
  
 <span data-ttu-id="ee952-133">**訓練您的 IT 人員在嚴重損壞修復程序**</span><span class="sxs-lookup"><span data-stu-id="ee952-133">**Train your IT staff on disaster recovery procedures**</span></span>  
  
-   <span data-ttu-id="ee952-134">確定您的 IT 人員隨時可在必要時復原系統。</span><span class="sxs-lookup"><span data-stu-id="ee952-134">Ensure that your IT staff is prepared to recover the system should the need arise.</span></span>  
  
 <span data-ttu-id="ee952-135">**練習在測試環境中從備份還原**</span><span class="sxs-lookup"><span data-stu-id="ee952-135">**Practice restoring from a backup in a test environment**</span></span>  
  
-   <span data-ttu-id="ee952-136">在測試環境中練習還原您的 BizTalk Server 系統，確保您可在失敗發生時將其還原為實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="ee952-136">Practice restoring your BizTalk Server system in a test environment to ensure that you can restore it to your production environment if a failure occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee952-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee952-137">See Also</span></span>  
 [<span data-ttu-id="ee952-138">嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="ee952-138">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)