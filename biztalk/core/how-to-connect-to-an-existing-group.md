---
title: 如何連接到現有的群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.connecttogroup
helpviewer_keywords:
- groups, existing
- groups, connecting
- managing [groups], connecting
ms.assetid: 1eedbcd5-f3f1-4da5-b91c-67377131f889
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 942093faa4a556f31d090de97b3feff4eb7a9a45
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005495"
---
# <a name="how-to-connect-to-an-existing-group"></a><span data-ttu-id="daffb-102">如何連接至現有的群組</span><span class="sxs-lookup"><span data-stu-id="daffb-102">How to Connect to an Existing Group</span></span>
<span data-ttu-id="daffb-103">您可以使用企業中任何電腦上的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，從遠端管理企業內一或多個 BizTalk Server 群組，只要這些群組位於相同網域或信任網域中的電腦上。</span><span class="sxs-lookup"><span data-stu-id="daffb-103">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console on any computer in your enterprise to remotely manage one or more BizTalk Server groups within your enterprise, as long as these groups are located on computers within the same domain or within trusted domains.</span></span>  
  
 <span data-ttu-id="daffb-104">BizTalk Server 管理主控台中的 [BizTalk Server 管理] 節點是所有的 BizTalk 群組的最高層節點，您將現有的 BizTalk Server 群組加入至 BizTalk Server 管理主控台時使用的層級。</span><span class="sxs-lookup"><span data-stu-id="daffb-104">The BizTalk Server Administration node in the BizTalk Server Administration console is the highest-level node for all BizTalk groups, and is the level that you use when adding an existing BizTalk Server group to the BizTalk Server Administration console.</span></span> <span data-ttu-id="daffb-105">在新增群組時，必須指定您要連接的現有伺服器與「BizTalk 管理」資料庫。</span><span class="sxs-lookup"><span data-stu-id="daffb-105">When you add a group, you must specify an existing server and BizTalk Management database to which you want to connect.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="daffb-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="daffb-106">Prerequisites</span></span>  
 <span data-ttu-id="daffb-107">若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員登入，或以「BizTalk Server 系統管理員」群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="daffb-107">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group or as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-connect-to-an-existing-group"></a><span data-ttu-id="daffb-108">連接至現有的群組</span><span class="sxs-lookup"><span data-stu-id="daffb-108">To connect to an existing group</span></span>  
  
1.  <span data-ttu-id="daffb-109">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="daffb-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="daffb-110">在主控台樹狀目錄中，以滑鼠右鍵按一下**BizTalk Server 管理**，然後按一下 **連接至現有的群組**。</span><span class="sxs-lookup"><span data-stu-id="daffb-110">In the console tree, right-click **BizTalk Server Administration**, and then click **Connect to Existing Group**.</span></span>  
  
3.  <span data-ttu-id="daffb-111">在**連接至現有的 BizTalk Server 組態資料庫**對話方塊中，於**SQL Server 名稱**下拉式清單方塊中，選取裝載 BizTalk 的 Microsoft SQL Server 執行個體的名稱管理資料庫 （也稱為 「 組態 」 資料庫）。</span><span class="sxs-lookup"><span data-stu-id="daffb-111">In the **Connect to Existing BizTalk Server Configuration Database** dialog box, in the **SQL Server name** drop-down list box, select the name of the Microsoft SQL Server instance that hosts the BizTalk Management database (also referred to as the Configuration database).</span></span> <span data-ttu-id="daffb-112">當您選取 SQL Server 執行個體時，BizTalk Server 會自動嘗試偵測位於該電腦上的 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="daffb-112">When you select the instance of SQL Server, BizTalk Server automatically attempts to detect BizTalk Server databases on that computer.</span></span>  
  
4.  <span data-ttu-id="daffb-113">在**資料庫名稱**下拉式清單方塊中，選取 BizTalk Server 管理資料庫 (**BizTalkMgmtDb**) 至您要連接，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="daffb-113">In the **Database name** drop-down list box, select the BizTalk Server Management database (**BizTalkMgmtDb**) to which you want to connect, and then click **OK**.</span></span>  
  
     <span data-ttu-id="daffb-114">BizTalk Server 管理主控台會將 BizTalk Server 群組加入至主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="daffb-114">The BizTalk Server Administration console adds the BizTalk Server group to the console tree.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="daffb-115">如果 BizTalk Server 管理資料庫位於 SQL Server 叢集上，而叢集正在進行容錯移轉，那麼當您嘗試連接管理資料庫時，就可能收到類似下列的錯誤：</span><span class="sxs-lookup"><span data-stu-id="daffb-115">If the BizTalk Server Management database is housed on a SQL Server cluster and the cluster is in the process of failing over then you may receive an error similar to the following when you attempt to connect to the Management database:</span></span>  
    >   
    >  <span data-ttu-id="daffb-116">無法載入群組 [\<servername\>:\<管理資料庫\>] 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="daffb-116">Failed to load Group [\<servername\>:\<management database\>] data providers.</span></span>  
    >   
    >  <span data-ttu-id="daffb-117">And</span><span class="sxs-lookup"><span data-stu-id="daffb-117">And</span></span>  
    >   
    >  <span data-ttu-id="daffb-118">其他資訊:</span><span class="sxs-lookup"><span data-stu-id="daffb-118">ADDITIONAL INFORMATION:</span></span>  
    >   
    >  <span data-ttu-id="daffb-119">找不到 WMI 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="daffb-119">Instance of the WMI class is not found.</span></span> <span data-ttu-id="daffb-120">(WinMgmt)</span><span class="sxs-lookup"><span data-stu-id="daffb-120">(WinMgmt)</span></span>  
    >   
    >  <span data-ttu-id="daffb-121">發生這個錯誤的原因，是因為在進行容錯移轉時，無法使用 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="daffb-121">This error can occur because the BizTalk databases are not available while they are being failed over.</span></span> <span data-ttu-id="daffb-122">若要解決這個問題，請等候 SQL Server 的叢集執行個體之後，才是線上然後再嘗試將它連接到 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="daffb-122">To workaround this issue, wait until after the clustered instance of SQL Server is online before attempting to connect to it with the BizTalk Server Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daffb-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="daffb-123">See Also</span></span>  
 <span data-ttu-id="daffb-124">[管理群組](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="daffb-124">[Managing Groups](../core/managing-groups.md) </span></span>  
 [<span data-ttu-id="daffb-125">BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="daffb-125">BizTalk Groups</span></span>](../core/biztalk-groups.md)