---
title: 檢查清單： 備份和還原 BizTalk Server 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- restoring, checklists
- maintaining, restoring
- maintaining, checklists
- restoring, BizTalk Server
- maintaining, backing up
- checklists, backing up
- backing up, checklists
- BizTalk Server, backing up
- checklists, restoring
- BizTalk Server, restoring
ms.assetid: 12f7e02e-57b1-4e55-8e44-7fe2d7920f5a
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f3c8c68eb62273562b0f703ae79c0db76ec837c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232702"
---
# <a name="checklist-back-up-and-restore-biztalk-server-databases"></a><span data-ttu-id="a774b-102">檢查清單： 備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="a774b-102">Checklist: Back Up and Restore BizTalk Server Databases</span></span>
<span data-ttu-id="a774b-103">在嘗試備份或還原 BizTalk Server 之前，務必讓自己先熟悉相關的程序。</span><span class="sxs-lookup"><span data-stu-id="a774b-103">Before attempting to back up or restore BizTalk Server, be sure to familiarize yourself with the processes involved.</span></span>  
  
## <a name="backing-up-biztalk-server"></a><span data-ttu-id="a774b-104">備份 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a774b-104">Backing Up BizTalk Server</span></span>  
  
|<span data-ttu-id="a774b-105">步驟</span><span class="sxs-lookup"><span data-stu-id="a774b-105">Step</span></span>|<span data-ttu-id="a774b-106">參考</span><span class="sxs-lookup"><span data-stu-id="a774b-106">Reference</span></span>|  
|----------|---------------|  
|<span data-ttu-id="a774b-107">瞭解如何備份和還原 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="a774b-107">Learn how to back up and restore BizTalk Server.</span></span>|[<span data-ttu-id="a774b-108">備份和還原資料庫的最佳作法</span><span class="sxs-lookup"><span data-stu-id="a774b-108">Best Practices for Backing Up and Restoring Databases</span></span>](../core/best-practices-for-backing-up-and-restoring-databases.md)<br /><br /> [<span data-ttu-id="a774b-109">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="a774b-109">Backing Up and Restoring BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-biztalk-server-databases.md)|  
|<span data-ttu-id="a774b-110">請確定您擁有備份和還原 BizTalk Server 的適當權限。</span><span class="sxs-lookup"><span data-stu-id="a774b-110">Ensure that you have appropriate permissions to back up and restore BizTalk Server.</span></span>|[<span data-ttu-id="a774b-111">最小安全性使用者權限</span><span class="sxs-lookup"><span data-stu-id="a774b-111">Minimum Security User Rights</span></span>](../core/minimum-security-user-rights.md)|  
|<span data-ttu-id="a774b-112">設定「備份 BizTalk Server」工作。</span><span class="sxs-lookup"><span data-stu-id="a774b-112">Configure the Backup BizTalk Server job.</span></span>|[<span data-ttu-id="a774b-113">如何設定備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="a774b-113">How to Configure the Backup BizTalk Server Job</span></span>](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|<span data-ttu-id="a774b-114">設定將要儲存備份的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a774b-114">Configure the server where backups will be stored.</span></span>|[<span data-ttu-id="a774b-115">如何設定記錄傳送目的地系統</span><span class="sxs-lookup"><span data-stu-id="a774b-115">How to Configure the Destination System for Log Shipping</span></span>](../core/how-to-configure-the-destination-system-for-log-shipping.md)|  
|<span data-ttu-id="a774b-116">如果您有使用商務活動監控 (BAM)，請備份 BAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a774b-116">If you are using Business Activity Monitoring (BAM), back up the BAM databases.</span></span>|[<span data-ttu-id="a774b-117">備份和還原 BAM</span><span class="sxs-lookup"><span data-stu-id="a774b-117">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)|  
|<span data-ttu-id="a774b-118">如果您有使用「企業單一登入」，請備份主要密碼。</span><span class="sxs-lookup"><span data-stu-id="a774b-118">If you are using Enterprise Single Sign-on, back up the master secret.</span></span>|[<span data-ttu-id="a774b-119">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="a774b-119">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)|  
  
## <a name="restoring-biztalk-server"></a><span data-ttu-id="a774b-120">還原 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a774b-120">Restoring BizTalk Server</span></span>  
  
|<span data-ttu-id="a774b-121">步驟</span><span class="sxs-lookup"><span data-stu-id="a774b-121">Step</span></span>|<span data-ttu-id="a774b-122">參考</span><span class="sxs-lookup"><span data-stu-id="a774b-122">Reference</span></span>|  
|----------|---------------|  
|<span data-ttu-id="a774b-123">還原您的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a774b-123">Restore your databases.</span></span>|[<span data-ttu-id="a774b-124">如何還原資料庫</span><span class="sxs-lookup"><span data-stu-id="a774b-124">How to Restore Your Databases</span></span>](../core/how-to-restore-your-databases.md)|  
|<span data-ttu-id="a774b-125">更新 BAM 資料庫名稱的參考。</span><span class="sxs-lookup"><span data-stu-id="a774b-125">Update references to the BAM database names.</span></span>|[<span data-ttu-id="a774b-126">如何備份 BAM 分析和追蹤 Analysis Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="a774b-126">How to Back Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)<br /><br /> [<span data-ttu-id="a774b-127">如何更新 BAM Analysis Server 和星狀結構描述資料庫名稱的參考</span><span class="sxs-lookup"><span data-stu-id="a774b-127">How to Update References to the BAM Analysis Server and Star Schema Database Names</span></span>](../core/update-references-to-the-bam-analysis-server-and-star-schema-database-names.md)<br /><br /> [<span data-ttu-id="a774b-128">如何更新 BAM 封存資料庫名稱的參考</span><span class="sxs-lookup"><span data-stu-id="a774b-128">How to Update References to the BAM Archive Database Name</span></span>](../core/how-to-update-references-to-the-bam-archive-database-name.md)<br /><br /> [<span data-ttu-id="a774b-129">如何更新 BAM 主要匯入資料庫名稱和連接字串的參考</span><span class="sxs-lookup"><span data-stu-id="a774b-129">How to Update References to the BAM Primary Import Database Name and Connection String</span></span>](../core/update-references-to-bam-primary-import-database-name-and-connection-string.md)<br /><br /> [<span data-ttu-id="a774b-130">如何更新參考 BAM Notification Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="a774b-130">How to Update References to the BAM Notification Services Databases</span></span>](../core/how-to-update-references-to-the-bam-notification-services-databases.md)<br /><br /> [<span data-ttu-id="a774b-131">如何解析未完成的活動執行個體</span><span class="sxs-lookup"><span data-stu-id="a774b-131">How to Resolve Incomplete Activity Instances</span></span>](../core/how-to-resolve-incomplete-activity-instances.md)|  
|<span data-ttu-id="a774b-132">如果您有使用「企業單一登入」，請還原主要密碼。</span><span class="sxs-lookup"><span data-stu-id="a774b-132">If you are using Enterprise Single Sign-on, restore the master secret.</span></span>|[<span data-ttu-id="a774b-133">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="a774b-133">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)|  
  
## <a name="see-also"></a><span data-ttu-id="a774b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a774b-134">See Also</span></span>  
 [<span data-ttu-id="a774b-135">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="a774b-135">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)