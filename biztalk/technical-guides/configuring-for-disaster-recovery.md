---
title: "設定災害復原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acdafe68-c8bf-4064-afca-6dfd22d15052
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c6a188255097f0a1c1e85086688252f9154b36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-for-disaster-recovery"></a><span data-ttu-id="413a4-102">設定災害復原</span><span class="sxs-lookup"><span data-stu-id="413a4-102">Configuring for Disaster Recovery</span></span>
<span data-ttu-id="413a4-103">[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送功能可延伸現有的備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業。</span><span class="sxs-lookup"><span data-stu-id="413a4-103">The [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Log Shipping feature extends the existing Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job.</span></span> [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="413a4-104">記錄傳送就不需要手動還原一系列的備份作業所產生的備份組，以及在系統失敗時減少停機時間。</span><span class="sxs-lookup"><span data-stu-id="413a4-104"> Log Shipping eliminates the need to manually restore a series of backup sets produced by the backup job, and reduces downtime in the event of a system failure.</span></span> [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="413a4-105">記錄傳送是 BizTalk 嚴重損壞修復程序的重要元件。</span><span class="sxs-lookup"><span data-stu-id="413a4-105"> Log Shipping is a critical component for BizTalk disaster recovery procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="413a4-106">每個應用程式的小組必須有記錄的備份和還原補充本主題提供的概念的災害復原計畫。</span><span class="sxs-lookup"><span data-stu-id="413a4-106">Each application team must have a documented backup and restore plan for disaster recovery that complements the concepts provided in this topic.</span></span> <span data-ttu-id="413a4-107">整體計劃應可解決整個系統，包括應用程式和作業系統的元件。</span><span class="sxs-lookup"><span data-stu-id="413a4-107">The overall plan should address the entire system, including applications and the components of the operating system.</span></span>  
  
 <span data-ttu-id="413a4-108">執行嚴重損壞修復作業是非常類似於以手動方式執行的 BizTalk 群組，一組新的還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="413a4-108">Performing a disaster recovery operation is very similar to manually performing a restore of a BizTalk group to a new set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances.</span></span> <span data-ttu-id="413a4-109">主要的差別在於[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]記錄傳送會套用記錄檔，持續災害復原站台，儲存許多手動步驟。</span><span class="sxs-lookup"><span data-stu-id="413a4-109">The primary difference is that [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] log shipping applies logs continuously at the disaster recovery site, saving many manual steps.</span></span> <span data-ttu-id="413a4-110">因此，記錄檔的上一組必須以手動方式還原當[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]實作記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="413a4-110">Therefore, only the last set of logs must be restored manually when [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] log shipping is implemented.</span></span> <span data-ttu-id="413a4-111">否則，後面的所有記錄備份，最後一個完整備份之後的最後一個完整備份必須以手動方式還原。</span><span class="sxs-lookup"><span data-stu-id="413a4-111">Otherwise, the last full backup followed by all log backups since the last full backup would have to be manually restored.</span></span> [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="413a4-112">記錄傳送會減少此手動程序，加速災害復原站台的還原作業所需的時間。</span><span class="sxs-lookup"><span data-stu-id="413a4-112"> log shipping reduces the effort for this manual process, speeding restoration of the disaster recovery site.</span></span>  
  
 <span data-ttu-id="413a4-113">本節涵蓋有關 production 組態來加速災害復原程序的建議事項。</span><span class="sxs-lookup"><span data-stu-id="413a4-113">This section covers recommendations on production configuration to facilitate the disaster recovery process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="413a4-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="413a4-114">In This Section</span></span>  
  
-   [<span data-ttu-id="413a4-115">準備災害復原站台</span><span class="sxs-lookup"><span data-stu-id="413a4-115">Prepare the Disaster Recovery Site</span></span>](../technical-guides/prepare-the-disaster-recovery-site.md)  
  
-   [<span data-ttu-id="413a4-116">記錄傳送的使用者帳戶和角色</span><span class="sxs-lookup"><span data-stu-id="413a4-116">Log Shipping User Accounts and Roles</span></span>](../technical-guides/log-shipping-user-accounts-and-roles.md)  
  
-   [<span data-ttu-id="413a4-117">設定 BizTalk Server 記錄傳送</span><span class="sxs-lookup"><span data-stu-id="413a4-117">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)  
  
## <a name="see-also"></a><span data-ttu-id="413a4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="413a4-118">See Also</span></span>  
 [<span data-ttu-id="413a4-119">嚴重損壞修復</span><span class="sxs-lookup"><span data-stu-id="413a4-119">Disaster Recovery</span></span>](../technical-guides/disaster-recovery.md)