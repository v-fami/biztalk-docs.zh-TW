---
title: 檢查清單： 監視 SQL Server |Microsoft Docs
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
ms.openlocfilehash: 8835af94ec16d344cd85c0321731ac4150451acf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993391"
---
# <a name="checklist-monitoring-sql-servers"></a><span data-ttu-id="e70d0-102">檢查清單： 監視 SQL Server</span><span class="sxs-lookup"><span data-stu-id="e70d0-102">Checklist: Monitoring SQL Servers</span></span>
<span data-ttu-id="e70d0-103">本主題說明監視時應該遵循的步驟[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]生產環境中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="e70d0-103">This topic describes the steps that should be followed to monitor [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  


|                                                                       <span data-ttu-id="e70d0-104">工作</span><span class="sxs-lookup"><span data-stu-id="e70d0-104">Task</span></span>                                                                        |                                                                        <span data-ttu-id="e70d0-105">參考</span><span class="sxs-lookup"><span data-stu-id="e70d0-105">Reference</span></span>                                                                        |
|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
|   <span data-ttu-id="e70d0-106">安裝 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Operations Manager 2007 管理組件</span><span class="sxs-lookup"><span data-stu-id="e70d0-106">Install the Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack for Operations Manager 2007</span></span>    |        <span data-ttu-id="e70d0-107">[SQL Server 監視管理組件](http://go.microsoft.com/fwlink/?linkid=109858)(<http://go.microsoft.com/fwlink/?linkid=109858>)</span><span class="sxs-lookup"><span data-stu-id="e70d0-107">[SQL Server Monitoring Management Pack](http://go.microsoft.com/fwlink/?linkid=109858) (<http://go.microsoft.com/fwlink/?linkid=109858>)</span></span>         |
| <span data-ttu-id="e70d0-108">指定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫為 SQL Server 管理組件中的關鍵。</span><span class="sxs-lookup"><span data-stu-id="e70d0-108">Designate the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases as critical in the SQL Server Management Pack.</span></span> | [<span data-ttu-id="e70d0-109">如何標示 BizTalk Server 資料庫以進行自訂監視</span><span class="sxs-lookup"><span data-stu-id="e70d0-109">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md) |
|                                                <span data-ttu-id="e70d0-110">請確定 SQL server 機器會受到監視。</span><span class="sxs-lookup"><span data-stu-id="e70d0-110">Ensure that the SQL server machines are monitored.</span></span>                                                 |                 [<span data-ttu-id="e70d0-111">監視 SQL Server Agent 作業和資料庫</span><span class="sxs-lookup"><span data-stu-id="e70d0-111">Monitoring SQL Server Agent Jobs and Databases</span></span>](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)                 |
|                                               <span data-ttu-id="e70d0-112">請確定 BizTalk SQL Agent 作業會受到監視。</span><span class="sxs-lookup"><span data-stu-id="e70d0-112">Ensure that the BizTalk SQL Agent jobs are monitored.</span></span>                                               |                 [<span data-ttu-id="e70d0-113">監視 SQL Server Agent 作業和資料庫</span><span class="sxs-lookup"><span data-stu-id="e70d0-113">Monitoring SQL Server Agent Jobs and Databases</span></span>](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)                 |

