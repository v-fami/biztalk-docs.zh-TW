---
title: 如何設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- purging, BTS_BACKUP_USERS role
- Tracking database, purging
- BTS_BACKUP_USERS role
- DTA Purge and Archive job
- archiving [Tracking database], BTS_BACKUP_USERS role
- archiving [Tracking database], DTA Purge and Archive job
- Tracking database, BTS_BACKUP_USERS role
- Tracking database, archiving
- purging, DTA Purge and Archive job
ms.assetid: c27aad2a-5788-4236-b5eb-ca730bf79851
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923fb083f3755259ab2176541213d1637ce872c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232446"
---
# <a name="how-to-configure-the-btsbackupusers-role-for-archiving-and-purging-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="48bb8-102">如何設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫的資料</span><span class="sxs-lookup"><span data-stu-id="48bb8-102">How to Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database</span></span>
<span data-ttu-id="48bb8-103">DTA 清除與封存 (BizTAlkDTADb) 工作通常使用已登入 SQL Server 代理程式服務帳戶使用者的認證來執行。</span><span class="sxs-lookup"><span data-stu-id="48bb8-103">The DTA Purge and Archive (BizTAlkDTADb) job normally runs using the credentials of the logged-on SQL Server Agent service account user.</span></span> <span data-ttu-id="48bb8-104">不過，若要確保更高的安全性，您可以設定 DTA 清除與封存 (BizTalkDTADb) 工作使用 BTS_BACKUP_USERS 角色之成員帳戶的認證來執行。</span><span class="sxs-lookup"><span data-stu-id="48bb8-104">For added security, however, you can configure the DTA Purge and Archive (BizTalkDTADb) job to run using the credentials of an account which is a member of the BTS_BACKUP_USERS role.</span></span> <span data-ttu-id="48bb8-105">以具有基本權限之帳戶執行 SQL Server 代理程式工作有助於防止提升權限。</span><span class="sxs-lookup"><span data-stu-id="48bb8-105">This helps to prevent elevation of privileges by running SQL Server Agent jobs under accounts with essential permissions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="48bb8-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="48bb8-106">Prerequisites</span></span>  
 <span data-ttu-id="48bb8-107">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="48bb8-107">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-configure-the-btsbackupusers-role-for-archiving-and-purging-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="48bb8-108">若要設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫的資料</span><span class="sxs-lookup"><span data-stu-id="48bb8-108">To configure the BTS_BACKUP_USERS role for archiving and purging data from the BizTalk Tracking database</span></span>  
  
1.  <span data-ttu-id="48bb8-109">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="48bb8-109">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="48bb8-110">在**連接到伺服器**對話方塊中，指定 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL server 和適當的驗證類型的名稱，然後按一下**連接**至連接到適當的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="48bb8-110">In the **Connect to Server** dialog box, specify the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL Server.</span></span>  
  
3.  <span data-ttu-id="48bb8-111">在**Microsoft SQL Server Management Studio**，連按兩下**BizTalkDTADb**，連按兩下**安全性**，連按兩下**角色**，和然後按兩下**資料庫角色**。</span><span class="sxs-lookup"><span data-stu-id="48bb8-111">In **Microsoft SQL Server Management Studio**, double-click **BizTalkDTADb**, double-click **Security**, double-click **Roles**, and then double-click **Database Roles**.</span></span>  
  
4.  <span data-ttu-id="48bb8-112">在**物件總管詳細資料** 窗格中，按兩下**BTS_BACKUP_USERS**。</span><span class="sxs-lookup"><span data-stu-id="48bb8-112">In the **Object Explorer Details** pane, double-click **BTS_BACKUP_USERS**.</span></span>  
  
5.  <span data-ttu-id="48bb8-113">在**資料庫角色屬性 – BTS_BACKUP_USERS**對話方塊的 **此角色的成員**，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="48bb8-113">In the **Database Role Properties – BTS_BACKUP_USERS** dialog box, under **Members of this role**, click **Add**.</span></span>  
  
6.  <span data-ttu-id="48bb8-114">在**選取資料庫使用者或角色**對話方塊中，輸入具有 SQL Server Agent 服務認證的使用者帳戶，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="48bb8-114">In the **Select Database User or Role** dialog box, enter a user account with SQL Server Agent Service credentials, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48bb8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48bb8-115">See Also</span></span>  
 [<span data-ttu-id="48bb8-116">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="48bb8-116">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)