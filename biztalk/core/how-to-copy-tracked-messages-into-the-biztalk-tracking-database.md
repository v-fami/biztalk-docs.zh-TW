---
title: 如何將追蹤的訊息複製到 BizTalk 追蹤資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, copying between servers
- MessageBox database, Tracking database
- Tracking database, linking servers
- MessageBox database, copying messages
- linking, servers
- Tracking database, archiving
- archiving [Tracking database], linking servers
- Tracking database, MessageBox database
- Tracking database, copying messages
- archiving [Tracking database], MessageBox database
- MessageBox database, linking servers
- MessageBox database, archiving
ms.assetid: 369e972a-efbe-4ad5-a68f-aa3bbfb9ad54
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23aaa8e3bea3405d51a18da1778d420550ad4584
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-copy-tracked-messages-into-the-biztalk-tracking-database"></a><span data-ttu-id="78a42-102">如何將追蹤的訊息複製到 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="78a42-102">How to Copy Tracked Messages into the BizTalk Tracking Database</span></span>
<span data-ttu-id="78a42-103">因為封存與清除程序可能會存取並 (或) 更新不同 SQL Server 中的資料庫，所以您必須在相關 SQL Server 執行個體之間設定連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="78a42-103">The archiving and purging process potentially accesses and/or updates databases in different SQL servers, so you must set up linked servers between the involved SQL Server instances.</span></span> <span data-ttu-id="78a42-104">您可以使用連結的伺服器，將追蹤的訊息從 [BizTalk MessageBox] (BizTalkMsgBoxDb) 資料庫伺服器直接複製到 [BizTalk 追蹤] (BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="78a42-104">You can directly copy tracked messages from the BizTalk MessageBox (BizTalkMsgBoxDb) database server to your BizTalk Tracking (BizTalkDTADb) database using a linked server.</span></span> <span data-ttu-id="78a42-105">您必須設定下列各項之間的連結伺服器：</span><span class="sxs-lookup"><span data-stu-id="78a42-105">You must set up linked servers between:</span></span>  
  
-   <span data-ttu-id="78a42-106">每一個 [BizTalk MessageBox] (BizTalkMsgBoxDb) 資料庫與 [BizTalk 追蹤] (BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="78a42-106">Each of your BizTalk MessageBox (BizTalkMsgBoxDb) databases and the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
-   <span data-ttu-id="78a42-107">[BizTalk 追蹤] (BizTalkDTADb) 資料庫與封存驗證的驗證伺服器。</span><span class="sxs-lookup"><span data-stu-id="78a42-107">The BizTalk Tracking (BizTalkDTADb) database and the validating server for archive validation.</span></span>  
  
-   <span data-ttu-id="78a42-108">在裝載 BizTalk MessageBox (BizTalkMsgBoxDb) 資料庫的電腦上，SQL Server 代理程式的服務帳戶必須對連結伺服器上的 BizTalk 追蹤 (BizTalkDTADb) 資料庫擁有 db_datareader 和 db_datawriter 權限。</span><span class="sxs-lookup"><span data-stu-id="78a42-108">The service accounts for the SQL Server Agent on the computer hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database must have the db_datareader and db_datawriter permissions for the BizTalk Tracking (BizTalkDTADb) database on the linked server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78a42-109">在 SQL Server Agent 中，確認複製作業執行無誤。</span><span class="sxs-lookup"><span data-stu-id="78a42-109">In SQL Server Agent, verify that the copy job runs without errors.</span></span> <span data-ttu-id="78a42-110">否則，錯誤可能使資料無法移至追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="78a42-110">Otherwise, errors might prevent data from being moved to the tracking database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="78a42-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="78a42-111">Prerequisites</span></span>  
 <span data-ttu-id="78a42-112">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="78a42-112">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-copy-tracked-messages-into-the-biztalk-tracking-database-sql-server-2008"></a><span data-ttu-id="78a42-113">將追蹤的訊息複製到「BizTalk 追蹤」資料庫 (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="78a42-113">To copy tracked messages into the BizTalk Tracking database (SQL Server 2008)</span></span>  
  
1.  <span data-ttu-id="78a42-114">按一下  **啟動**, ，按一下  **所有程式**, ，按一下  **Microsoft SQL Server 2008 R2**, ，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="78a42-114">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="78a42-115">在 **連接到伺服器** 對話方塊中，指定 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL server 和適當的驗證類型的名稱，然後按一下 **連接** 連接到適當的 SQL server。</span><span class="sxs-lookup"><span data-stu-id="78a42-115">In the **Connect to Server** dialog box, specify the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL server.</span></span>  
  
3.  <span data-ttu-id="78a42-116">在 **Microsoft SQL Server Management Studio**, ，連按兩下  **SQL Server Agent**, ，然後按一下  **工作**。</span><span class="sxs-lookup"><span data-stu-id="78a42-116">In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
4.  <span data-ttu-id="78a42-117">在詳細資料窗格中，以滑鼠右鍵按一下 **TrackedMessages_Copy_BizTalkMsgBoxDb**, ，然後按一下  **屬性**。</span><span class="sxs-lookup"><span data-stu-id="78a42-117">In the details pane, right-click **TrackedMessages_Copy_BizTalkMsgBoxDb**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="78a42-118">在 **作業屬性-TrackedMessages_Copy_BizTalkMsgBoxDb** 對話方塊的  **選取頁面**, ，按一下  **步驟**。</span><span class="sxs-lookup"><span data-stu-id="78a42-118">In the **Job Properties - TrackedMessages_Copy_BizTalkMsgBoxDb** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
6.  <span data-ttu-id="78a42-119">在 **作業步驟清單**, ，按一下  **清除**, ，然後按一下  **編輯**。</span><span class="sxs-lookup"><span data-stu-id="78a42-119">Under **Job step list**, click **Purge**, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="78a42-120">在 **命令** 方塊、 編輯追蹤伺服器和資料庫名稱參數，視需要，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="78a42-120">In the **Command** box, edit the tracking server and database names parameters as appropriate, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="78a42-121">上 **作業屬性-TrackedMessages_Copy_BizTalkMsgBoxDb** 對話方塊的  **選取頁面**, ，按一下  **一般**,，請選取 **啟用** 核取方塊，，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="78a42-121">On the **Job Properties - TrackedMessages_Copy_BizTalkMsgBoxDb** dialog box, under **Select a page**, click **General**,select the **Enabled** check box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="78a42-122">訊息將會從 BizTalk MessageBox (BizTalkMsgBoxDb) 複製到 BizTalk 追蹤 (BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="78a42-122">The messages will be copied from the BizTalk MessageBox (BizTalkMsgBoxDb) to the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78a42-123">若您加入新 MessageBox 資料庫，則必須為此新 MessageBox 資料庫再次執行此程序。</span><span class="sxs-lookup"><span data-stu-id="78a42-123">If you add a new MessageBox database, you will need to perform this procedure again for the new MessageBox database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a42-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78a42-124">See Also</span></span>  
 [<span data-ttu-id="78a42-125">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="78a42-125">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)