---
title: 移動 BizTalk Server 資料庫 |Microsoft Docs
description: 若要將 BizTalk Server 資料庫移至新的伺服器，包括停止服務，以及使用 SQL Server Agent 作業步驟
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec302e6d-c89d-4fe7-849f-97b5566e8ba4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a3509a6a0297b0f58a16cfd3eff1dc29420232b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978903"
---
# <a name="how-to-move-the-biztalk-server-databases"></a><span data-ttu-id="1ad20-103">如何移動 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ad20-103">How to Move the BizTalk Server Databases</span></span>

## <a name="overview"></a><span data-ttu-id="1ad20-104">概觀</span><span class="sxs-lookup"><span data-stu-id="1ad20-104">Overview</span></span>
<span data-ttu-id="1ad20-105">您可以使用此程序，在主要複本移[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]另一部伺服器的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1ad20-105">You can use this procedure to move the primary [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases to another server.</span></span> <span data-ttu-id="1ad20-106">這個相同的基本程序也可用來移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫從本機[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]至遠端[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]或[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集。</span><span class="sxs-lookup"><span data-stu-id="1ad20-106">This same basic procedure can also be used to move the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases from a local [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to a remote [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] or to a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="1ad20-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="1ad20-107">Prerequisites</span></span>  
<span data-ttu-id="1ad20-108">使用成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]sysadmin 固定的伺服器角色，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="1ad20-108">Sign in with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
## <a name="move-steps"></a><span data-ttu-id="1ad20-109">移動步驟</span><span class="sxs-lookup"><span data-stu-id="1ad20-109">Move steps</span></span>
  
1. <span data-ttu-id="1ad20-110">停止所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="1ad20-110">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="1ad20-111">如需詳細資訊，請參閱 <<c0> [ 重新啟動 BizTalk Server 服務，並關閉的 BizTalk Server](how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad20-111">For more information, see [Restart BizTalk Server Services, and shut down BizTalk Server](how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>
  
   > [!IMPORTANT]
   >  <span data-ttu-id="1ad20-112">請務必確定所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在移動資料庫之前停止服務和作業。</span><span class="sxs-lookup"><span data-stu-id="1ad20-112">It is critical to make sure that all the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services and jobs are stopped before you move the databases.</span></span>  
  
2. <span data-ttu-id="1ad20-113">停止 IIS 服務。</span><span class="sxs-lookup"><span data-stu-id="1ad20-113">Stop the IIS service.</span></span>  
  
3. <span data-ttu-id="1ad20-114">停止 SQL Server Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="1ad20-114">Stop the SQL Server Agent service.</span></span>  
  
4. <span data-ttu-id="1ad20-115">備份 BizTalk 資料庫遵循的資料庫備份程序，在所述[Backing Up and Restoring BizTalk Server 資料庫](../core/backing-up-and-restoring-the-biztalk-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad20-115">Back up the BizTalk databases by following the database backup procedures as described at [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md).</span></span>  
  
5. <span data-ttu-id="1ad20-116">還原資料庫，新伺服器上的 BizTalk 資料庫還原程序[如何還原您的資料庫](../core/how-to-restore-your-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad20-116">Restore the BizTalk databases on the new server following the database restore procedures at [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span>  
  
6. <span data-ttu-id="1ad20-117">SQL Server Agent 作業下列傳輸到新的伺服器，在所述的指令碼[如何備份和還原 SQL 代理程式作業](../core/how-to-back-up-and-restore-sql-agent-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad20-117">Script the SQL Server Agent jobs listed below for transfer to the new server, as described at [How to Back Up and Restore SQL Agent Jobs](../core/how-to-back-up-and-restore-sql-agent-jobs.md).</span></span>  <span data-ttu-id="1ad20-118">執行每個指令碼來重新建立作業在新伺服器上。</span><span class="sxs-lookup"><span data-stu-id="1ad20-118">Run each of the scripts on the new server to recreate the jobs.</span></span>  
  
    <span data-ttu-id="1ad20-119">執行每個指令碼來重新建立作業在新伺服器上。</span><span class="sxs-lookup"><span data-stu-id="1ad20-119">Run each of the scripts on the new server to recreate the jobs.</span></span> <span data-ttu-id="1ad20-120">某些作業，例如**備份 BizTalk Server (BizTalkMsgBoxDb)** 作業，必須重新設定，除非新的伺服器檔案路徑和伺服器名稱會與舊伺服器相同。</span><span class="sxs-lookup"><span data-stu-id="1ad20-120">Certain jobs, such as the **Backup BizTalk Server (BizTalkMsgBoxDb)** job, will have to be reconfigured unless the new server file paths and server name are identical to the old server.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="1ad20-121">您也可以使用 SSIS/DTS**傳送作業**工作將作業移至新的伺服器，但大部分的使用者可能會發現它容易編寫指令碼工作使用 SQL Management Studio。</span><span class="sxs-lookup"><span data-stu-id="1ad20-121">You can also use the SSIS/DTS **Transfer Jobs** task to move the jobs to the new server, but most users will probably find it easier to script the jobs using SQL Management Studio.</span></span>  
  
7. <span data-ttu-id="1ad20-122">除了上一個步驟中所述，指令碼處理 SQL Server Agent 作業，您必須也編寫指令碼登入中所述[如何備份和還原 SQL Server 登入](../core/how-to-back-up-and-restore-sql-server-logins.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad20-122">In addition to scripting SQL Server Agent jobs as described in the previous step, you must also script logins as described in [How to Back Up and Restore SQL Server Logins](../core/how-to-back-up-and-restore-sql-server-logins.md).</span></span> <span data-ttu-id="1ad20-123">這些登入，就必須在目的地伺服器上進行還原。</span><span class="sxs-lookup"><span data-stu-id="1ad20-123">These logins need to be restored on the destination server.</span></span>  
  
8. <span data-ttu-id="1ad20-124">還原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，依照下列步驟 9 至 22 英[還原您的資料庫如何](../core/how-to-restore-your-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad20-124">Restore the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases by following steps 9 through 22 in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="1ad20-125">此程序更新 BizTalk 資料庫的新位置的 BizTalk 管理資料庫 (BizTalkMgmtDb) 和登錄。</span><span class="sxs-lookup"><span data-stu-id="1ad20-125">This procedure updates the BizTalk Management (BizTalkMgmtDb) database and registry with the new location of the BizTalk databases.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="1ad20-126">在  **SampleUpdateInfo.xml**檔案，標記為註解的所有資料庫，除了已移至新的伺服器。</span><span class="sxs-lookup"><span data-stu-id="1ad20-126">In the **SampleUpdateInfo.xml** file, comment out all of the databases except for those you have moved to the new server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad20-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ad20-127">See Also</span></span>  
 [<span data-ttu-id="1ad20-128">移動 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="1ad20-128">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)