---
title: "還原 BizTalk 群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14a9af44-d6de-49c7-9600-21ece389727f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c12a1deff8fea6d769f138aa34bf6dab269a167f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-the-biztalk-group"></a><span data-ttu-id="db75b-102">還原 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="db75b-102">Restoring the BizTalk Group</span></span>
<span data-ttu-id="db75b-103">BizTalk 群組由一組[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫、 SSIS 封裝和 SQL 代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="db75b-103">The BizTalk group is represented by the set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases, SSIS packages, and SQL Agent Jobs.</span></span> <span data-ttu-id="db75b-104">本章節描述還原 BizTalk 群組的程序。</span><span class="sxs-lookup"><span data-stu-id="db75b-104">This section describes the process for restoring the BizTalk group.</span></span>  
  
 <span data-ttu-id="db75b-105">確認需要轉換，轉換為目的系統 （災害復原站台），則必須完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="db75b-105">In the event that a switchover to the destination system (disaster recovery site) is required, the following steps must be completed:</span></span>  
  
1.  <span data-ttu-id="db75b-106">還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和 Analysis Services 資料庫。</span><span class="sxs-lookup"><span data-stu-id="db75b-106">Restore [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and Analysis Services databases.</span></span>  
  
2.  <span data-ttu-id="db75b-107">還原[!INCLUDE[prague](../includes/prague-md.md)]執行階段伺服器及應用程式。</span><span class="sxs-lookup"><span data-stu-id="db75b-107">Restore [!INCLUDE[prague](../includes/prague-md.md)] runtime servers and applications.</span></span>  
  
 <span data-ttu-id="db75b-108">完成這些步驟的詳細資訊，BizTalk 群組已建立在災害復原站台，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以設定執行階段伺服器，而且應用程式部署到 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="db75b-108">Upon completion of these steps, the BizTalk group has been established at the disaster recovery site, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime servers can be configured, and the applications can be deployed into the BizTalk group.</span></span> <span data-ttu-id="db75b-109">本節中的主題涵蓋在此程序的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="db75b-109">The topics in this section cover the details of this process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db75b-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="db75b-110">In This Section</span></span>  
  
-   [<span data-ttu-id="db75b-111">停止處理在來源系統上的應用程式</span><span class="sxs-lookup"><span data-stu-id="db75b-111">Stopping Application Processing on the Source System</span></span>](../technical-guides/stopping-application-processing-on-the-source-system.md)  
  
-   [<span data-ttu-id="db75b-112">如何還原 「 備份 BizTalk Server 」 工作中的資料庫</span><span class="sxs-lookup"><span data-stu-id="db75b-112">How to Restore Databases in the Backup BizTalk Server Job</span></span>](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)  
  
-   [<span data-ttu-id="db75b-113">還原資料庫不包含在備份 BizTalk Server 作業</span><span class="sxs-lookup"><span data-stu-id="db75b-113">Restoring Databases Not Included in the Backup BizTalk Server Job</span></span>](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)