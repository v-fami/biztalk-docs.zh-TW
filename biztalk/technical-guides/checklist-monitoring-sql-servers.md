---
title: 檢查清單： 監視 SQL Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dea6db0-5347-497c-b07d-6a339e409f0a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cd47efb3bf9417c3733212b8f45946a2f13fa19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300094"
---
# <a name="checklist-monitoring-sql-servers"></a><span data-ttu-id="acdfd-102">檢查清單： 監視 SQL Server</span><span class="sxs-lookup"><span data-stu-id="acdfd-102">Checklist: Monitoring SQL Servers</span></span>
<span data-ttu-id="acdfd-103">本主題說明監視，應遵循的步驟[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]在生產環境中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="acdfd-103">This topic describes the steps that should be followed to monitor [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
|<span data-ttu-id="acdfd-104">工作</span><span class="sxs-lookup"><span data-stu-id="acdfd-104">Task</span></span>|<span data-ttu-id="acdfd-105">參考</span><span class="sxs-lookup"><span data-stu-id="acdfd-105">Reference</span></span>|  
|----------|---------------|  
|<span data-ttu-id="acdfd-106">安裝 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Operations manager 2007 管理組件</span><span class="sxs-lookup"><span data-stu-id="acdfd-106">Install the Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack for Operations Manager 2007</span></span>|<span data-ttu-id="acdfd-107">[SQL Server 監視管理組件](http://go.microsoft.com/fwlink/?linkid=109858)(http://go.microsoft.com/fwlink/?linkid=109858)</span><span class="sxs-lookup"><span data-stu-id="acdfd-107">[SQL Server Monitoring Management Pack](http://go.microsoft.com/fwlink/?linkid=109858) (http://go.microsoft.com/fwlink/?linkid=109858)</span></span>|  
|<span data-ttu-id="acdfd-108">指定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]為關鍵 SQL Server 管理組件中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="acdfd-108">Designate the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases as critical in the SQL Server Management Pack.</span></span>|[<span data-ttu-id="acdfd-109">如何將 BizTalk Server 資料庫標示為的自訂監視</span><span class="sxs-lookup"><span data-stu-id="acdfd-109">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)|  
|<span data-ttu-id="acdfd-110">請確定會監視 SQL server 電腦。</span><span class="sxs-lookup"><span data-stu-id="acdfd-110">Ensure that the SQL server machines are monitored.</span></span>|[<span data-ttu-id="acdfd-111">監視 SQL Server Agent 作業和資料庫</span><span class="sxs-lookup"><span data-stu-id="acdfd-111">Monitoring SQL Server Agent Jobs and Databases</span></span>](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)|  
|<span data-ttu-id="acdfd-112">確定 BizTalk SQL Agent 作業會受到監視。</span><span class="sxs-lookup"><span data-stu-id="acdfd-112">Ensure that the BizTalk SQL Agent jobs are monitored.</span></span>|[<span data-ttu-id="acdfd-113">監視 SQL Server Agent 作業和資料庫</span><span class="sxs-lookup"><span data-stu-id="acdfd-113">Monitoring SQL Server Agent Jobs and Databases</span></span>](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)|