---
title: "如何建立連結的伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, linking for backups
- backing up, linking servers
ms.assetid: 7d4aba3d-77c0-4cdf-8547-71e821ce34a1
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ae08df9b522e1a772d7c8a9ad7d02c36dcb999
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-linked-server"></a><span data-ttu-id="b5546-102">如何建立連結的伺服器</span><span class="sxs-lookup"><span data-stu-id="b5546-102">How to Create a Linked Server</span></span>
<span data-ttu-id="b5546-103">以分散式拓撲安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，屬於 BizTalk 群組的資料庫會存在於多個 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 上。</span><span class="sxs-lookup"><span data-stu-id="b5546-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed in a distributed topology, the databases that belong to a BizTalk Group exist on multiple [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="b5546-104">您必須先設定每個遠端伺服器的連結伺服器連線，才能從 BizTalk 管理伺服器備份整個 BizTalk 環境。</span><span class="sxs-lookup"><span data-stu-id="b5546-104">You must configure a linked server connection to each of the remote servers before you can back up the entire BizTalk environment from the BizTalk Management server.</span></span> <span data-ttu-id="b5546-105">連結的伺服器是 OLE DB 資料來源中所使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]分散式查詢。</span><span class="sxs-lookup"><span data-stu-id="b5546-105">A linked server is an OLE DB data source that is used in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] distributed queries.</span></span>  
  
 <span data-ttu-id="b5546-106">備份和還原程序的一部分，備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]工作會自動建立連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b5546-106">As a part of the backup and restore process, the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job automatically creates linked servers.</span></span> <span data-ttu-id="b5546-107">但是，如果需要，您可以手動使用這個程序來建立連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b5546-107">If necessary, however, you can manually create linked servers using this procedure.</span></span>  
  
 <span data-ttu-id="b5546-108">連結的伺服器也可以建立使用*sp_addlinkedserver*預存程序。</span><span class="sxs-lookup"><span data-stu-id="b5546-108">Linked servers can also be created using the *sp_addlinkedserver* stored procedure.</span></span> <span data-ttu-id="b5546-109">沒有與這項作業相關聯的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="b5546-109">There are security considerations associated with this operation.</span></span> <span data-ttu-id="b5546-110">使用 sp_addlinkedserver 來建立連結的伺服器時，所有本機登入將新連結的伺服器預設對應。</span><span class="sxs-lookup"><span data-stu-id="b5546-110">When a linked server is created using sp_addlinkedserver, all local logins will be mapped to the new linked server by default.</span></span> <span data-ttu-id="b5546-111">若要控制存取連結伺服器， *sp_droplinkedsvrlogin*程序應該用來卸除全域登入對應，後面接著*sp_addlinkedsvrlogin*對應所需的登入帳戶新增連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b5546-111">To control access to the linked server, the *sp_droplinkedsvrlogin* procedure should be used to drop the global login mapping, followed by *sp_addlinkedsvrlogin* to map the desired login account(s) to the new linked server.</span></span> <span data-ttu-id="b5546-112">當使用 sp_addlinkedsvrlogin，建議您設定@useself參數 = TRUE。</span><span class="sxs-lookup"><span data-stu-id="b5546-112">When using sp_addlinkedsvrlogin, it is recommended that you set the @useself parameter = TRUE.</span></span> <span data-ttu-id="b5546-113">這可避免需要將內嵌到您的 SQL 指令碼的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="b5546-113">This avoids the need to embed a user name and password into your SQL script.</span></span>  

> [!TIP]
> <span data-ttu-id="b5546-114">這些步驟可能會隨時間變更。</span><span class="sxs-lookup"><span data-stu-id="b5546-114">These steps may change over time.</span></span> <span data-ttu-id="b5546-115">我們建議您參考[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文件，網址[建立連結的伺服器](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine)。</span><span class="sxs-lookup"><span data-stu-id="b5546-115">We recommend referring to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation at [Create Linked Servers](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="b5546-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="b5546-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="b5546-117">使用成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] **sysadmin**固定的伺服器角色</span><span class="sxs-lookup"><span data-stu-id="b5546-117">Sign in with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] **sysadmin** fixed server role</span></span>  
  
-   <span data-ttu-id="b5546-118">建立本機[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登入。</span><span class="sxs-lookup"><span data-stu-id="b5546-118">Create a local [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] login.</span></span> <span data-ttu-id="b5546-119">在下列步驟中，此帳戶會對應至登入上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]您將會連結至。</span><span class="sxs-lookup"><span data-stu-id="b5546-119">In the following steps, this account is mapped to a login on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] you will link to.</span></span> 
  
## <a name="create-a-linked-server"></a><span data-ttu-id="b5546-120">建立連結的伺服器</span><span class="sxs-lookup"><span data-stu-id="b5546-120">Create a linked server</span></span>
  
1.  <span data-ttu-id="b5546-121">開啟**SQL Server Management Studio**，輸入您的本機名稱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，然後選取**連接**。</span><span class="sxs-lookup"><span data-stu-id="b5546-121">Open **SQL Server Management Studio**, enter the name of your local [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and then select **Connect**.</span></span>  
  
2.  <span data-ttu-id="b5546-122">展開**伺服器物件**，以滑鼠右鍵按一下**連結的伺服器**，然後選取**新增連結的伺服器**。</span><span class="sxs-lookup"><span data-stu-id="b5546-122">Expand **Server Objects**, right-click **Linked Servers**, and then select **New Linked Server**.</span></span>  

    <span data-ttu-id="b5546-123">若要查看**伺服器物件**，連接到本機內部[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5546-123">To see **Server Objects**, connect to a local on-premises [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="b5546-124">然後，**伺服器物件**應該顯示。</span><span class="sxs-lookup"><span data-stu-id="b5546-124">Then, **Server Objects** should be displayed.</span></span>
  
3.  <span data-ttu-id="b5546-125">在**連結的伺服器**文字方塊中，輸入完整的網路名稱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]您想要連結至。</span><span class="sxs-lookup"><span data-stu-id="b5546-125">In the **Linked server** text box, enter the full network name of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] you want to link to.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5546-126">此程序通常是指您要為遠端伺服器連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b5546-126">This procedure often refers to the server you are linking to as the remote server.</span></span> <span data-ttu-id="b5546-127">這只為方便使用，表示要在本機伺服器的連結 （「 遠端 」） 伺服器的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b5546-127">This is for convenience only, to indicate the relationship of the linked (“remote”) server to the local server.</span></span>  
  
4.  <span data-ttu-id="b5546-128">在下**伺服器類型**，選取**SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="b5546-128">Under **Server type**, select **SQL Server**.</span></span>  
  
5.  <span data-ttu-id="b5546-129">在左窗格中選取 [安全性] 。</span><span class="sxs-lookup"><span data-stu-id="b5546-129">In the left pane, select **Security**.</span></span> 

    <span data-ttu-id="b5546-130">在此步驟中，您可以將您建立的本機帳戶對應到遠端伺服器登入。</span><span class="sxs-lookup"><span data-stu-id="b5546-130">In this step, you map the local account you created to the remote server login.</span></span> <span data-ttu-id="b5546-131">您的選項：</span><span class="sxs-lookup"><span data-stu-id="b5546-131">Your options:</span></span> 
    
    | | | 
    |---|---|
    | <span data-ttu-id="b5546-132">**會使用登入的目前安全性內容**</span><span class="sxs-lookup"><span data-stu-id="b5546-132">**Be made using the login’s current security context**</span></span> | <span data-ttu-id="b5546-133">在網域環境中，使用者通常使用連線其網域登入。</span><span class="sxs-lookup"><span data-stu-id="b5546-133">In domain environments, users typically connect with their domain logins.</span></span> <span data-ttu-id="b5546-134">由於登入的網域帳戶的安全性內容對應至您所建立的本機帳戶，可能是最佳這個選項。</span><span class="sxs-lookup"><span data-stu-id="b5546-134">This option may be best since the security context of the signed-in domain account is mapped to the local account you created.</span></span>|
    | <span data-ttu-id="b5546-135">**使用此安全性內容建立**</span><span class="sxs-lookup"><span data-stu-id="b5546-135">**Be made using this security context**</span></span> | <span data-ttu-id="b5546-136">當使用者連線到本機的 SQL Server 使用 SQL Server 登入時，此選項可能是最佳的。</span><span class="sxs-lookup"><span data-stu-id="b5546-136">When users connect to the local SQL Server using a SQL Server login, then this option may be best.</span></span> <span data-ttu-id="b5546-137">然後輸入登入和密碼的帳戶連結的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b5546-137">Then enter the login and password for the account on the linked server.</span></span> |


6. <span data-ttu-id="b5546-138">選取**新增**，並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b5546-138">Select **Add**, and enter the following:</span></span> 

    1. <span data-ttu-id="b5546-139">在下**本機登入**，選取您建立的本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="b5546-139">Under **Local Login**, select the local account you created.</span></span> 
    2. <span data-ttu-id="b5546-140">請檢查**Impersonate**如果本機登入也存在於遠端伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b5546-140">Check **Impersonate** if the local login also exists on the remote server.</span></span> 
    3. <span data-ttu-id="b5546-141">或者，如果本機登入將會對應到遠端[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登入，請輸入**遠端使用者**名稱和**遠端密碼**遠端伺服器登入。</span><span class="sxs-lookup"><span data-stu-id="b5546-141">Alternatively, if the local login will be mapped to a remote [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] login you, enter the **Remote User** name and **Remote Password** for the remote server login.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5546-142">若要使用模擬，您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]組態和登入帳戶必須符合委派的需求。</span><span class="sxs-lookup"><span data-stu-id="b5546-142">To use impersonation, your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] configuration and login accounts must meet the requirements for delegation.</span></span> <span data-ttu-id="b5546-143">請參閱[委派設定連結伺服器](https://msdn.microsoft.com/library/ms189580.aspx)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b5546-143">See [Configuring Linked Servers for Delegation](https://msdn.microsoft.com/library/ms189580.aspx) for more details.</span></span>  

7. <span data-ttu-id="b5546-144">在左窗格中，選擇 **伺服器選項**。</span><span class="sxs-lookup"><span data-stu-id="b5546-144">In the left pane, choose **Server Options**.</span></span> <span data-ttu-id="b5546-145">設定**RPC**和**RPC 輸出**參數**True**，然後選取**[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b5546-145">Set the **RPC** and **RPC Out** parameters to **True**, and then select **OK**.</span></span> 
 
> [!TIP]
> <span data-ttu-id="b5546-146">如需詳細資訊和建立連結的伺服器時建議使用 includig`sp_addlinkedserver`儲存 procedcure，請參閱[建立連結的伺服器](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine)。</span><span class="sxs-lookup"><span data-stu-id="b5546-146">For more details and recommendations when creating linked servers, includig using the `sp_addlinkedserver` stored procedcure, see [Create Linked Servers](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine).</span></span>

  
## <a name="see-also"></a><span data-ttu-id="b5546-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5546-147">See Also</span></span>  
 [<span data-ttu-id="b5546-148">備份和還原的相關進階的資訊</span><span class="sxs-lookup"><span data-stu-id="b5546-148">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)