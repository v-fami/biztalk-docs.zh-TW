---
title: 正在還原 BizTalk 群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14a9af44-d6de-49c7-9600-21ece389727f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9bea20bacdd6b681d39e2bf3995d7626b9b1f63
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021638"
---
# <a name="restoring-the-biztalk-group"></a><span data-ttu-id="f4905-102">正在還原 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="f4905-102">Restoring the BizTalk Group</span></span>
<span data-ttu-id="f4905-103">BizTalk 群組由一組[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫、 SSIS 封裝和 SQL Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="f4905-103">The BizTalk group is represented by the set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases, SSIS packages, and SQL Agent Jobs.</span></span> <span data-ttu-id="f4905-104">本章節描述還原 BizTalk 群組的程序。</span><span class="sxs-lookup"><span data-stu-id="f4905-104">This section describes the process for restoring the BizTalk group.</span></span>  
  
 <span data-ttu-id="f4905-105">轉換，轉換為目的系統 （災害復原站台） 是必要的則必須完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f4905-105">In the event that a switchover to the destination system (disaster recovery site) is required, the following steps must be completed:</span></span>  
  
1. <span data-ttu-id="f4905-106">還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和 Analysis Services 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f4905-106">Restore [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and Analysis Services databases.</span></span>  
  
2. <span data-ttu-id="f4905-107">還原 BizTalk Server 執行階段伺服器和應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4905-107">Restore BizTalk Server runtime servers and applications.</span></span>  
  
   <span data-ttu-id="f4905-108">完成這些步驟的詳細資訊，BizTalk 群組已在災害復原站台，建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以設定執行階段伺服器，而且應用程式可以部署到 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="f4905-108">Upon completion of these steps, the BizTalk group has been established at the disaster recovery site, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime servers can be configured, and the applications can be deployed into the BizTalk group.</span></span> <span data-ttu-id="f4905-109">在本節中的主題涵蓋了此程序的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f4905-109">The topics in this section cover the details of this process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4905-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="f4905-110">In This Section</span></span>  
  
-   [<span data-ttu-id="f4905-111">停止來源系統上的應用程式處理</span><span class="sxs-lookup"><span data-stu-id="f4905-111">Stopping Application Processing on the Source System</span></span>](../technical-guides/stopping-application-processing-on-the-source-system.md)  
  
-   [<span data-ttu-id="f4905-112">如何在備份 BizTalk Server 作業中還原資料庫</span><span class="sxs-lookup"><span data-stu-id="f4905-112">How to Restore Databases in the Backup BizTalk Server Job</span></span>](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)  
  
-   [<span data-ttu-id="f4905-113">還原不包含在備份 BizTalk Server 作業中的資料庫</span><span class="sxs-lookup"><span data-stu-id="f4905-113">Restoring Databases Not Included in the Backup BizTalk Server Job</span></span>](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)