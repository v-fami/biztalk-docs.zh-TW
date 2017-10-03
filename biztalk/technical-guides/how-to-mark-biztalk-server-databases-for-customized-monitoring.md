---
title: "BizTalk Server 資料庫標示為的自訂監視如何 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfbdc73d-a108-42ee-a5d8-401d5bfe5e7d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08807b1a365b84765221e3a71cb131d8c037fcf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-mark-biztalk-server-databases-for-customized-monitoring"></a><span data-ttu-id="45599-102">如何將 BizTalk Server 資料庫標示為的自訂監視</span><span class="sxs-lookup"><span data-stu-id="45599-102">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>
<span data-ttu-id="45599-103">如果您已安裝 Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件，您可以自訂方式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫會受到監視。</span><span class="sxs-lookup"><span data-stu-id="45599-103">If you have installed the Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack, you can customize the way [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are monitored.</span></span> <span data-ttu-id="45599-104">如此可確保[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]管理組件會監視下列[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫：</span><span class="sxs-lookup"><span data-stu-id="45599-104">This ensures that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Pack monitors the following [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases:</span></span>  
  
-   <span data-ttu-id="45599-105">BAM 封存 (BAMArchive) 資料庫</span><span class="sxs-lookup"><span data-stu-id="45599-105">BAM Archive (BAMArchive) database</span></span>  
  
-   <span data-ttu-id="45599-106">BAM 主要匯入 (BAMPrimaryImport) 資料庫</span><span class="sxs-lookup"><span data-stu-id="45599-106">BAM Primary Import (BAMPrimaryImport) database</span></span>  
  
-   <span data-ttu-id="45599-107">BAM 星狀結構描述 (BAMStarSchema) 資料庫</span><span class="sxs-lookup"><span data-stu-id="45599-107">BAM Star Schema (BAMStarSchema) database</span></span>  
  
-   <span data-ttu-id="45599-108">BizTalk 追蹤 (BizTalkDTADb) 資料庫</span><span class="sxs-lookup"><span data-stu-id="45599-108">BizTalk Tracking (BizTalkDTADb) database</span></span>  
  
-   <span data-ttu-id="45599-109">BizTalk 管理 (BizTalkMgmtDb) 資料庫</span><span class="sxs-lookup"><span data-stu-id="45599-109">BizTalk Management (BizTalkMgmtDb) database</span></span>  
  
-   <span data-ttu-id="45599-110">BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫</span><span class="sxs-lookup"><span data-stu-id="45599-110">BizTalk MessageBox (BizTalkMsgBoxDb) database</span></span>  
  
-   <span data-ttu-id="45599-111">規則引擎 (BizTalkRuleEngineDb) 資料庫</span><span class="sxs-lookup"><span data-stu-id="45599-111">Rule Engine (BizTalkRuleEngineDb) database</span></span>  
  
-   <span data-ttu-id="45599-112">企業單一登入 (SSODB) 資料庫</span><span class="sxs-lookup"><span data-stu-id="45599-112">Enterprise Single Sign-On (SSODB) database</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45599-113">您必須以 Operations Manager 進階操作員角色的成員登入或[!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)]管理群組。</span><span class="sxs-lookup"><span data-stu-id="45599-113">You must be logged on as a member of the Operations Manager Advanced Operator role or [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] Management Group.</span></span>  
  
### <a name="to-mark-biztalk-server-databases-for-customized-monitoring"></a><span data-ttu-id="45599-114">若要將 BizTalk Server 資料庫標示的自訂監視</span><span class="sxs-lookup"><span data-stu-id="45599-114">To mark BizTalk Server databases for customized monitoring</span></span>  
  
1.  <span data-ttu-id="45599-115">按一下**啟動**，按一下 **所有程式**，按一下  **System Center Operations Manager 2007**，然後按一下  **Operations 主控台**。</span><span class="sxs-lookup"><span data-stu-id="45599-115">Click **Start**, click **All Programs**, click **System Center Operations Manager 2007**, and then click **Operations Console**.</span></span>  
  
2.  <span data-ttu-id="45599-116">在 Operations 主控台中，按一下**製作** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="45599-116">In the Operations console, click the **Authoring** button.</span></span>  
  
3.  <span data-ttu-id="45599-117">在**製作** 窗格中，展開 **管理組件物件**，然後按一下 **物件探索**。</span><span class="sxs-lookup"><span data-stu-id="45599-117">In the **Authoring** pane, expand **Management Pack Objects**, and then click **Object Discoveries**.</span></span>  
  
4.  <span data-ttu-id="45599-118">若要找出適用於 SQL Server 的探索，Operations 主控台工具列上按一下**尋找**，然後在**尋找**文字方塊中，輸入**SQL 2008**搜尋 SQL Server 2008。</span><span class="sxs-lookup"><span data-stu-id="45599-118">To locate a discovery for SQL Server, on the Operations console toolbar click **Find**, and in the **Look for** text box enter **SQL 2008** to search for SQL Server 2008.</span></span>  
  
5.  <span data-ttu-id="45599-119">在下**找到的類型： SQL 2008 DB**類別目錄中，選取**探索資料庫引擎的資料庫**。</span><span class="sxs-lookup"><span data-stu-id="45599-119">Under the **Discovered Type: SQL 2008 DB** category, select **Discover Databases for a Database Engine**.</span></span>  
  
6.  <span data-ttu-id="45599-120">在 Operations 主控台工具列中，按一下 **會覆寫**，然後指向**覆寫物件探索**。</span><span class="sxs-lookup"><span data-stu-id="45599-120">On the Operations console toolbar, click **Overrides** and then point to **Override the Object Discovery**.</span></span> <span data-ttu-id="45599-121">您可以選擇覆寫探索，特定類型的物件或群組內的所有物件。</span><span class="sxs-lookup"><span data-stu-id="45599-121">You can choose to override the discovery for objects of a specific type or for all objects within a group.</span></span> <span data-ttu-id="45599-122">選擇要覆寫，物件類型的群組之後**覆寫內容**對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="45599-122">After you choose which group of object type to override, the **Override Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45599-123">如果**會覆寫**按鈕便無法使用，請確定您已在 [監視] 窗格中選取監視器，而不是容器物件。</span><span class="sxs-lookup"><span data-stu-id="45599-123">If the **Overrides** button is not available, make sure you have selected a monitor and not a container object in the Monitors pane.</span></span>  
  
7.  <span data-ttu-id="45599-124">選取核取方塊，在**覆寫**旁邊的資料行**排除清單**參數，然後在**覆寫值**資料行中，輸入您想要排除的資料庫名稱從監視。</span><span class="sxs-lookup"><span data-stu-id="45599-124">Select the check box in the **Override** column next to the **Exclude List** parameter, and in the **Override Value** column, type the name of the database that you want to exclude from monitoring.</span></span> <span data-ttu-id="45599-125">請確定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中不會列出您想要監視的資料庫**覆寫值**資料行。</span><span class="sxs-lookup"><span data-stu-id="45599-125">Make sure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases that you want to monitor are not listed in the **Override Value** column.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="45599-126">若要建立新的管理組件，您可以使用修改過的物件探索。</span><span class="sxs-lookup"><span data-stu-id="45599-126">You can use the modified object discoveries to create a new management pack.</span></span> <span data-ttu-id="45599-127">在底部窗格中，**選取目的地管理組件**下拉式清單會顯示預設值是**預設管理組件**。</span><span class="sxs-lookup"><span data-stu-id="45599-127">At the bottom of the pane, the **Select destination management pack** drop-down shows a default value of **Default Management Pack**.</span></span> <span data-ttu-id="45599-128">按一下**新增**建立新的管理組件，使用已修改的物件探索。</span><span class="sxs-lookup"><span data-stu-id="45599-128">Click **New** to create a new management pack using the modified object discoveries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45599-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45599-129">See Also</span></span>  
 [<span data-ttu-id="45599-130">監視 SQL Server</span><span class="sxs-lookup"><span data-stu-id="45599-130">Monitoring SQL Servers</span></span>](../technical-guides/monitoring-sql-servers.md)