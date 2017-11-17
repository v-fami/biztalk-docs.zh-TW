---
title: "監視 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31871432-e13d-4ef3-b886-16c833371f6d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ac37905574090fb346aeee198ea8e92a0f436f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-servers"></a><span data-ttu-id="f1364-102">監視 SQL Server</span><span class="sxs-lookup"><span data-stu-id="f1364-102">Monitoring SQL Servers</span></span>
<span data-ttu-id="f1364-103">Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件提供主動式與反應式監視[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]企業環境中。</span><span class="sxs-lookup"><span data-stu-id="f1364-103">The Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] management pack provides both proactive and reactive monitoring of [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] and [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] in an enterprise environment.</span></span> <span data-ttu-id="f1364-104">可用性和組態監視，效能資料集合及預設臨界值會建立監視企業層級。</span><span class="sxs-lookup"><span data-stu-id="f1364-104">Availability and configuration monitoring, performance data collection, and default thresholds are built for enterprise-level monitoring.</span></span> <span data-ttu-id="f1364-105">本機和遠端連接檢查，有助於確保資料庫的可用性。</span><span class="sxs-lookup"><span data-stu-id="f1364-105">Both local and remote connectivity checks help ensure database availability.</span></span>  
  
 <span data-ttu-id="f1364-106">在內嵌的專門技術與[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件，您可以主動管理[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，並識別問題變嚴重之前。</span><span class="sxs-lookup"><span data-stu-id="f1364-106">With the embedded expertise in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] management pack, you can proactively manage [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and identify issues before they become critical.</span></span> <span data-ttu-id="f1364-107">此管理組件會增加安全性、 可用性和效能的程式[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]基礎結構。</span><span class="sxs-lookup"><span data-stu-id="f1364-107">This management pack increases the security, availability, and performance of your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] infrastructure.</span></span>  
  
 <span data-ttu-id="f1364-108">Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]隨附的組件的管理組件指南說明內容的管理組件，並說明如何部署它。</span><span class="sxs-lookup"><span data-stu-id="f1364-108">The Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] management pack guide that comes with the pack describes the content of the management pack, and describes how to deploy it.</span></span> <span data-ttu-id="f1364-109">管理組件的功能包括：</span><span class="sxs-lookup"><span data-stu-id="f1364-109">Features of the management pack include:</span></span>  
  
-   <span data-ttu-id="f1364-110">監視包含服務的狀態，例如[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，SQL 代理程式，報表伺服器時，Notification Services</span><span class="sxs-lookup"><span data-stu-id="f1364-110">Monitoring the state of the included services such as [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], SQL Agent, Report Server, Notification Services</span></span>  
  
-   <span data-ttu-id="f1364-111">監視資料庫的狀態</span><span class="sxs-lookup"><span data-stu-id="f1364-111">Monitoring the state of databases</span></span>  
  
-   <span data-ttu-id="f1364-112">監視在資料庫中，可設定 %或 MB 的可用空間</span><span class="sxs-lookup"><span data-stu-id="f1364-112">Monitoring the available space in databases, configurable by % or MB</span></span>  
  
-   <span data-ttu-id="f1364-113">確保資料庫已正確設定</span><span class="sxs-lookup"><span data-stu-id="f1364-113">Ensuring databases are configured correctly</span></span>  
  
-   <span data-ttu-id="f1364-114">確定用戶端可以連線至[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1364-114">Ensure clients can connect to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="f1364-115">監視封鎖的處理序</span><span class="sxs-lookup"><span data-stu-id="f1364-115">Monitor blocked processes</span></span>  
  
-   <span data-ttu-id="f1364-116">失敗的代理程式監看的工作，以及花了過多的時間來執行的工作</span><span class="sxs-lookup"><span data-stu-id="f1364-116">Watch for failed agent jobs, and jobs taking an excessive time to execute</span></span>  
  
-   <span data-ttu-id="f1364-117">監視複寫和警示失敗的健全狀況</span><span class="sxs-lookup"><span data-stu-id="f1364-117">Monitor the health of replication and alert on failures</span></span>  
  
-   <span data-ttu-id="f1364-118">監視資料庫鏡像狀態</span><span class="sxs-lookup"><span data-stu-id="f1364-118">Monitor the state of Database Mirroring</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1364-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="f1364-119">In This Section</span></span>  
  
-   [<span data-ttu-id="f1364-120">監視 SQL Server Agent 作業和資料庫</span><span class="sxs-lookup"><span data-stu-id="f1364-120">Monitoring SQL Server Agent Jobs and Databases</span></span>](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)  
  
-   [<span data-ttu-id="f1364-121">如何將 BizTalk Server 資料庫標示為的自訂監視</span><span class="sxs-lookup"><span data-stu-id="f1364-121">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
-   [<span data-ttu-id="f1364-122">監控 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="f1364-122">Monitor the BizTalk Server Databases</span></span>](../technical-guides/monitor-the-biztalk-server-databases.md)