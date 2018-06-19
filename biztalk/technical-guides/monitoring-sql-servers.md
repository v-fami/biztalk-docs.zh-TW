---
title: 監視 SQL Server |Microsoft 文件
description: 使用來檢查效能、 可用空間、 資料庫組態、 封鎖處理序、 連線、 失敗 SQL agent 作業、 複寫和多個 BizTalk Server 中的 SQL Server 管理組件
ms.custom: ''
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31871432-e13d-4ef3-b886-16c833371f6d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d0e3ea9ecb9d9d910549790568d5891b72d06de
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006959"
---
# <a name="monitoring-sql-servers"></a><span data-ttu-id="0ecab-103">監視 SQL Server</span><span class="sxs-lookup"><span data-stu-id="0ecab-103">Monitoring SQL Servers</span></span>

## <a name="use-sql-management-pack"></a><span data-ttu-id="0ecab-104">使用 SQL 管理組件</span><span class="sxs-lookup"><span data-stu-id="0ecab-104">Use SQL management pack</span></span>
<span data-ttu-id="0ecab-105">Microsoft SQL Server 管理組件提供主動式與反應式監視 SQL Server 的企業環境中。</span><span class="sxs-lookup"><span data-stu-id="0ecab-105">The Microsoft SQL Server management pack provides both proactive and reactive monitoring of SQL Server in an enterprise environment.</span></span> <span data-ttu-id="0ecab-106">可用性和組態監視，效能資料集合及預設臨界值會建立監視企業層級。</span><span class="sxs-lookup"><span data-stu-id="0ecab-106">Availability and configuration monitoring, performance data collection, and default thresholds are built for enterprise-level monitoring.</span></span> <span data-ttu-id="0ecab-107">本機和遠端連接檢查，有助於確保資料庫的可用性。</span><span class="sxs-lookup"><span data-stu-id="0ecab-107">Both local and remote connectivity checks help ensure database availability.</span></span>  
  
 <span data-ttu-id="0ecab-108">與 SQL Server 管理組件中內嵌的專業技術，您可以主動管理 SQL Server，並找出問題變嚴重之前。</span><span class="sxs-lookup"><span data-stu-id="0ecab-108">With the embedded expertise in the SQL Server management pack, you can proactively manage SQL Server, and identify issues before they become critical.</span></span> <span data-ttu-id="0ecab-109">此管理組件會增加安全性、 可用性和效能的 SQL Server 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="0ecab-109">This management pack increases the security, availability, and performance of your SQL Server infrastructure.</span></span>  
  
 <span data-ttu-id="0ecab-110">隨附的組件的 Microsoft SQL Server 管理組件指南描述管理組件的內容，並說明如何將其部署。</span><span class="sxs-lookup"><span data-stu-id="0ecab-110">The Microsoft SQL Server management pack guide that comes with the pack describes the content of the management pack, and describes how to deploy it.</span></span> <span data-ttu-id="0ecab-111">管理組件的功能包括：</span><span class="sxs-lookup"><span data-stu-id="0ecab-111">Features of the management pack include:</span></span>  
  
-   <span data-ttu-id="0ecab-112">監視 SQL Server、 SQL Agent、 報表伺服器、 Notification Services 包含服務的狀態</span><span class="sxs-lookup"><span data-stu-id="0ecab-112">Monitoring the state of the included services such as SQL Server, SQL Agent, Report Server, Notification Services</span></span>  
  
-   <span data-ttu-id="0ecab-113">監視資料庫的狀態</span><span class="sxs-lookup"><span data-stu-id="0ecab-113">Monitoring the state of databases</span></span>  
  
-   <span data-ttu-id="0ecab-114">監視在資料庫中，可設定 %或 MB 的可用空間</span><span class="sxs-lookup"><span data-stu-id="0ecab-114">Monitoring the available space in databases, configurable by % or MB</span></span>  
  
-   <span data-ttu-id="0ecab-115">確保資料庫已正確設定</span><span class="sxs-lookup"><span data-stu-id="0ecab-115">Ensuring databases are configured correctly</span></span>  
  
-   <span data-ttu-id="0ecab-116">確定用戶端可以連線至 SQL Server</span><span class="sxs-lookup"><span data-stu-id="0ecab-116">Ensure clients can connect to the SQL Server</span></span>  
  
-   <span data-ttu-id="0ecab-117">監視封鎖的處理序</span><span class="sxs-lookup"><span data-stu-id="0ecab-117">Monitor blocked processes</span></span>  
  
-   <span data-ttu-id="0ecab-118">失敗的代理程式監看的工作，以及花了過多的時間來執行的工作</span><span class="sxs-lookup"><span data-stu-id="0ecab-118">Watch for failed agent jobs, and jobs taking an excessive time to execute</span></span>  
  
-   <span data-ttu-id="0ecab-119">監視複寫和警示失敗的健全狀況</span><span class="sxs-lookup"><span data-stu-id="0ecab-119">Monitor the health of replication and alert on failures</span></span>  
  
-   <span data-ttu-id="0ecab-120">監視資料庫鏡像狀態</span><span class="sxs-lookup"><span data-stu-id="0ecab-120">Monitor the state of Database Mirroring</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0ecab-121">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="0ecab-121">Next steps</span></span>
  
-   [<span data-ttu-id="0ecab-122">監視 SQL Server Agent 作業和資料庫</span><span class="sxs-lookup"><span data-stu-id="0ecab-122">Monitoring SQL Server Agent Jobs and Databases</span></span>](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)  
  
-   [<span data-ttu-id="0ecab-123">如何標示 BizTalk Server 資料庫以進行自訂監視</span><span class="sxs-lookup"><span data-stu-id="0ecab-123">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
-   [<span data-ttu-id="0ecab-124">監視 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="0ecab-124">Monitor the BizTalk Server Databases</span></span>](../technical-guides/monitor-the-biztalk-server-databases.md)