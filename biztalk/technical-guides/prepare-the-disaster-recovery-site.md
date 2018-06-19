---
title: 準備災害復原站台 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b66f3c8-afe0-4ac0-b925-8f780d14bd4b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a60be6d04d0f73013f67c5fe8e5b0144357fd1f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008863"
---
# <a name="prepare-the-disaster-recovery-site"></a><span data-ttu-id="7f13e-102">準備災害復原站台</span><span class="sxs-lookup"><span data-stu-id="7f13e-102">Prepare the Disaster Recovery Site</span></span>
<span data-ttu-id="7f13e-103">BizTalk Server 記錄傳送具有兩個支援的案例。</span><span class="sxs-lookup"><span data-stu-id="7f13e-103">BizTalk Server log shipping has two supported scenarios.</span></span> <span data-ttu-id="7f13e-104">其中一個是記錄傳送的所有生產執行個體上的所有資料庫的位置[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]套用至單一災害復原執行個體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7f13e-104">One is where log shipping for all databases on all production instances of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is applied to a single disaster recovery instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="7f13e-105">其他的案例是記錄的位置的每個實際執行個體的資料庫傳送[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]套用到對應的執行個體的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在災害復原站台。</span><span class="sxs-lookup"><span data-stu-id="7f13e-105">The other scenario is where log shipping for the databases for each production instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is applied to a corresponding instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] at the disaster recovery site.</span></span> <span data-ttu-id="7f13e-106">請注意，它會完全支援有相同數目的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫執行個體在災害復原站台，因為沒有在生產環境中，但是在較少的實體伺服器上。</span><span class="sxs-lookup"><span data-stu-id="7f13e-106">Note that it is fully supported to have the same number of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances in the disaster recovery site as there is in production but on fewer physical servers.</span></span> <span data-ttu-id="7f13e-107">本節提供這些準備工作的指引。</span><span class="sxs-lookup"><span data-stu-id="7f13e-107">This section provides guidance on these preparations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f13e-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="7f13e-108">In This Section</span></span>  
  
-   [<span data-ttu-id="7f13e-109">準備災害復原 SQL Server</span><span class="sxs-lookup"><span data-stu-id="7f13e-109">Preparing the Disaster Recovery SQL Servers</span></span>](../technical-guides/preparing-the-disaster-recovery-sql-servers.md)  
  
-   [<span data-ttu-id="7f13e-110">備份 BAM 分析和追蹤 Analysis Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="7f13e-110">Backing Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)  
  
-   [<span data-ttu-id="7f13e-111">準備災害復原 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7f13e-111">Preparing the Disaster Recovery BizTalk Servers</span></span>](../technical-guides/preparing-the-disaster-recovery-biztalk-servers.md)  
  
-   [<span data-ttu-id="7f13e-112">準備應用程式的災害復原</span><span class="sxs-lookup"><span data-stu-id="7f13e-112">Preparing Applications for Disaster Recovery</span></span>](../technical-guides/preparing-applications-for-disaster-recovery.md)  
  
-   [<span data-ttu-id="7f13e-113">如何還原主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="7f13e-113">How to Restore the Master Secret Server</span></span>](../technical-guides/how-to-restore-the-master-secret-server.md)