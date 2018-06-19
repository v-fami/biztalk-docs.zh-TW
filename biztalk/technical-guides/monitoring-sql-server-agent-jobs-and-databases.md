---
title: 監視 SQL Server Agent 作業，以及資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2eb5f318-10d3-4f43-991d-9bff2ebc20e2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c9991e7ebd61c72bbeb6a090b0497244da63e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299198"
---
# <a name="monitoring-sql-server-agent-jobs-and-databases"></a><span data-ttu-id="23c1d-102">監視 SQL Server Agent 作業和資料庫</span><span class="sxs-lookup"><span data-stu-id="23c1d-102">Monitoring SQL Server Agent Jobs and Databases</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="23c1d-103">包含多個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行重要功能以維持伺服器運作且狀況良好的代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="23c1d-103"> includes multiple [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs that perform important functions to keep your servers operational and healthy.</span></span> <span data-ttu-id="23c1d-104">您應該監視這些作業的狀況，確保它們在沒有錯誤的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="23c1d-104">You should monitor the health of these jobs and ensure that they are running without errors.</span></span> <span data-ttu-id="23c1d-105">Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件包含監視 SQL 資料庫等項目規則和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="23c1d-105">The Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack contains rules for monitoring items such as SQL databases and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="23c1d-106">您應該設定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]全面監視所有的管理組件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="23c1d-106">You should configure the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack for comprehensive monitoring of all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs.</span></span>  
  
 <span data-ttu-id="23c1d-107">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件包含兩個已停用的規則，以便監視的健全狀況的兩個最重要的 BizTalk[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業：</span><span class="sxs-lookup"><span data-stu-id="23c1d-107">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack includes two disabled rules for monitoring the health of two of the most important BizTalk [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs:</span></span>  
  
-   <span data-ttu-id="23c1d-108">嚴重錯誤： BizTalk SQL Server Agent 作業失敗-備份 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="23c1d-108">Critical Error: A BizTalk SQL Server Agent job failed - Backup BizTalk Server</span></span>  
  
-   <span data-ttu-id="23c1d-109">嚴重錯誤： BizTalk SQL Server Agent 作業失敗-追蹤訊息複製</span><span class="sxs-lookup"><span data-stu-id="23c1d-109">Critical Error: A BizTalk SQL Server Agent job failed – Tracked Message Copy</span></span>  
  
 <span data-ttu-id="23c1d-110">若要監控所有 BizTalk Server[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件，您必須啟用這些規則，並建立額外的規則，您想要使用下列程序監視的其他作業。</span><span class="sxs-lookup"><span data-stu-id="23c1d-110">To monitor all BizTalk Server [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack, you must enable these rules and create additional rules for other jobs that you want to monitor using the following process.</span></span>  
  
-   <span data-ttu-id="23c1d-111">在 Operations Manager 系統管理員主控台中，建立一份在前述的兩個規則，在任一[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]核心規則群組，並適當地重新命名的規則。</span><span class="sxs-lookup"><span data-stu-id="23c1d-111">In the Operations Manager Administrator console, create a copy of either of the two preceding rules in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Core Rule group, and rename the rule appropriately.</span></span>  
  
-   <span data-ttu-id="23c1d-112">規則的準則區段中變更的萬用字元比較參數 1 適當。</span><span class="sxs-lookup"><span data-stu-id="23c1d-112">In the criteria section for the rule, change the wildcard comparison for Parameter 1 appropriately.</span></span>  
  
-   <span data-ttu-id="23c1d-113">在某些情況下，作業名稱為相依於資料庫名稱的使用者建立時，例如，MessageBox 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="23c1d-113">In some cases, job names are dependent on database names that the user creates, for example, the name of the MessageBox database.</span></span>  
  
-   <span data-ttu-id="23c1d-114">您可以將目標設您的規則優先的工作相關聯的單一 MessageBox 或所有的 Messagebox。</span><span class="sxs-lookup"><span data-stu-id="23c1d-114">Your rule can be targeted either towards a job associated with a single MessageBox or all MessageBoxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c1d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23c1d-115">See Also</span></span>  
 [<span data-ttu-id="23c1d-116">如何啟動 SQL Server 代理程式</span><span class="sxs-lookup"><span data-stu-id="23c1d-116">How to Start the SQL Server Agent</span></span>](../technical-guides/how-to-start-the-sql-server-agent.md)