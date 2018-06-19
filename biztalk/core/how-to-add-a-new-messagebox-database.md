---
title: 如何新增新的 MessageBox 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding, MessageBox database
- MessageBox database, adding
- managing [MessageBox database], adding
ms.assetid: 98d850dc-fe3e-43dd-8b5d-9b8c23c006ae
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cab4fd370aab2d85519b3fd52e0dadcd9583275e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247238"
---
# <a name="how-to-add-a-new-messagebox-database"></a><span data-ttu-id="7ba24-102">如何加入新的 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="7ba24-102">How to Add a New MessageBox Database</span></span>
<span data-ttu-id="7ba24-103">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，將新的 MessageBox 資料庫新增到 BizTalk Server 部署。</span><span class="sxs-lookup"><span data-stu-id="7ba24-103">You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console to add a new MessageBox database to your BizTalk Server deployment.</span></span> <span data-ttu-id="7ba24-104">MessageBox 資料庫是在執行協同處裡的伺服器之間進行負載平衡工作項目的基礎。</span><span class="sxs-lookup"><span data-stu-id="7ba24-104">MessageBox databases are the basis for load-balancing work items across servers that do cooperative processing.</span></span> <span data-ttu-id="7ba24-105">若要增加您的系統可以處理的訊息數目，您可能需要新增其他的 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7ba24-105">To increase the number of messages that your system can process, you may need to add additional MessageBox databases.</span></span>  
  
 <span data-ttu-id="7ba24-106">您無法同時建立新的 MessageBox 資料庫並完成協調流程、傳送埠或傳送埠群組的登錄。</span><span class="sxs-lookup"><span data-stu-id="7ba24-106">You cannot create a new MessageBox database and have enlisted orchestrations, send ports, or send port groups at the same time.</span></span> <span data-ttu-id="7ba24-107">已登錄的協調流程、傳送埠或傳送埠群組會存取 BizTalk Server 必須複製到新 MessageBox 資料庫的資料。</span><span class="sxs-lookup"><span data-stu-id="7ba24-107">Enlisted orchestrations, send ports, or send port groups access data that BizTalk Server must copy to the new MessageBox database.</span></span> <span data-ttu-id="7ba24-108">存取這個資料時，BizTalk Server 無法將其複製到新的 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7ba24-108">While this data is being accessed, BizTalk Server cannot copy it into the new MessageBox database.</span></span>  
  
 <span data-ttu-id="7ba24-109">您可以指定本機與遠端資料庫做為 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7ba24-109">You can designate both local and remote databases as MessageBox databases.</span></span> <span data-ttu-id="7ba24-110">BizTalk Server 資料庫的相關資訊，請參閱[BizTalk Server 中的資料庫](../core/databases-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7ba24-110">For information about BizTalk Server databases, see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7ba24-111">SQL Server 代理程式必須在您要新增 MessageBox 資料庫的所有 SQL 伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="7ba24-111">SQL Server Agent must be running on all of the SQL servers to which you want to add a new MessageBox database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7ba24-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="7ba24-112">Prerequisites</span></span>  
 <span data-ttu-id="7ba24-113">管理 MessageBox 資料庫的系統管理員必須具備必要的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="7ba24-113">Administrators who manage MessageBox databases must have the required user rights.</span></span> <span data-ttu-id="7ba24-114">您必須具備下列使用者權限，才能管理 MessageBox 資料庫和停用新訊息發佈：</span><span class="sxs-lookup"><span data-stu-id="7ba24-114">You must have the following user rights to manage MessageBox databases and disable new message publication:</span></span>  
  
-   <span data-ttu-id="7ba24-115">您必須以「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="7ba24-115">You must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
-   <span data-ttu-id="7ba24-116">您必須是資料庫所在電腦的 SQL Server 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="7ba24-116">You must be a SQL Server Administrator on the computer where the database exists.</span></span>  
  
### <a name="to-add-a-new-messagebox-database"></a><span data-ttu-id="7ba24-117">加入新的 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="7ba24-117">To add a new MessageBox database</span></span>  
  
1.  <span data-ttu-id="7ba24-118">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="7ba24-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7ba24-119">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開 [BizTalk 群組]，然後按一下**平台設定**。</span><span class="sxs-lookup"><span data-stu-id="7ba24-119">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then click **Platform Settings**.</span></span>  
  
3.  <span data-ttu-id="7ba24-120">以滑鼠右鍵按一下**訊息方塊**，按一下 **新增**，然後按一下 **訊息方塊**。</span><span class="sxs-lookup"><span data-stu-id="7ba24-120">Right-click **Message Boxes**, click **New**, and then click **Message Box**.</span></span>  
  
4.  <span data-ttu-id="7ba24-121">在**Messagebox 屬性**對話方塊中，執行下列命令，，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="7ba24-121">In the **Message Box Properties** dialog box, do the following, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="7ba24-122">使用</span><span class="sxs-lookup"><span data-stu-id="7ba24-122">Use this</span></span>|<span data-ttu-id="7ba24-123">動作</span><span class="sxs-lookup"><span data-stu-id="7ba24-123">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7ba24-124">**[SQL Server]**</span><span class="sxs-lookup"><span data-stu-id="7ba24-124">**SQL Server**</span></span>|<span data-ttu-id="7ba24-125">顯示裝載 MessageBox 資料庫的 SQL Server 名稱。</span><span class="sxs-lookup"><span data-stu-id="7ba24-125">Displays the name of the SQL server that hosts the MessageBox database.</span></span>|  
    |<span data-ttu-id="7ba24-126">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="7ba24-126">**Database**</span></span>|<span data-ttu-id="7ba24-127">顯示 MessageBox 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ba24-127">Displays the name of the MessageBox database.</span></span>|  
    |<span data-ttu-id="7ba24-128">**主要訂閱訊息方塊**</span><span class="sxs-lookup"><span data-stu-id="7ba24-128">**Master subscription message box**</span></span>|<span data-ttu-id="7ba24-129">指示選取的 MessageBox 資料庫是否為主要。</span><span class="sxs-lookup"><span data-stu-id="7ba24-129">Indicates whether the selected MessageBox database is the master.</span></span> <span data-ttu-id="7ba24-130">若目前的 MessageBox 資料庫為主要，此核取方塊將為已選取和無法使用的狀態。</span><span class="sxs-lookup"><span data-stu-id="7ba24-130">If the current MessageBox database is the master, this check box is selected and unavailable.</span></span> <span data-ttu-id="7ba24-131">當您執行「組態精靈」所建立的第一個 MessageBox 資料庫預設為主要。</span><span class="sxs-lookup"><span data-stu-id="7ba24-131">The first MessageBox database created when you run the Configuration Wizard is the master by default.</span></span>|  
    |<span data-ttu-id="7ba24-132">**停用新訊息發佈**</span><span class="sxs-lookup"><span data-stu-id="7ba24-132">**Disable new message publication**</span></span>|<span data-ttu-id="7ba24-133">選取此核取方塊以指定您不想讓此 MessageBox 資料庫接收啟動訊息。</span><span class="sxs-lookup"><span data-stu-id="7ba24-133">Select this check box to specify that you do not want this MessageBox database to receive activation messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ba24-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ba24-134">See Also</span></span>  
 <span data-ttu-id="7ba24-135">[管理 MessageBox 資料庫](../core/managing-messagebox-databases.md) </span><span class="sxs-lookup"><span data-stu-id="7ba24-135">[Managing MessageBox Databases](../core/managing-messagebox-databases.md) </span></span>  
 <span data-ttu-id="7ba24-136">[如何停用新訊息發佈](../core/how-to-disable-new-message-publication.md) </span><span class="sxs-lookup"><span data-stu-id="7ba24-136">[How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md) </span></span>  
 <span data-ttu-id="7ba24-137">[如何刪除 MessageBox 資料庫](../core/how-to-delete-a-messagebox-database.md) </span><span class="sxs-lookup"><span data-stu-id="7ba24-137">[How to Delete a MessageBox Database](../core/how-to-delete-a-messagebox-database.md) </span></span>  
 <span data-ttu-id="7ba24-138">[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="7ba24-138">[Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md) </span></span>  
 [<span data-ttu-id="7ba24-139">MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="7ba24-139">The MessageBox Database</span></span>](../core/the-messagebox-database.md)