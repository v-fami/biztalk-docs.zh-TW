---
title: "更新追蹤 Analysis Server 資料庫的參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a403325-1394-4668-946f-01b610cb686e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ed784eeca992d32f431a7c6794b7051b7595e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="update-references-to-the-tracking-analysis-server-database"></a><span data-ttu-id="f3f4c-102">更新追蹤 Analysis Server 資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="f3f4c-102">Update References to the Tracking Analysis Server Database</span></span>
<span data-ttu-id="f3f4c-103">追蹤 Analysis Server 資料庫是選擇性，而且包含線上分析處理 (OLAP) cube。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-103">The Tracking Analysis Server database is an optional and contains the online analytical processing (OLAP) cubes.</span></span> <span data-ttu-id="f3f4c-104">這些 OLAP Cube 是包含在 BizTalk 追蹤資料庫中的資料彙總。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-104">These OLAP cubes are aggregations of data contained in the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="f3f4c-105">若要還原追蹤 Analysis Server 資料庫，請使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]分析管理員 」 來處理 MessageMetrics 和 ServiceMetrics cube。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-105">To restore the Tracking Analysis Server database, use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager to process the MessageMetrics and ServiceMetrics cubes.</span></span> <span data-ttu-id="f3f4c-106">如需指示，請參閱[管理備份與還原 (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (http://go.microsoft.com/fwlink/?LinkId=130939) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-106">For instructions, see [Managing Backing Up and Restoring (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (http://go.microsoft.com/fwlink/?LinkId=130939) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="f3f4c-107">若要還原追蹤 Analysis Server 資料庫到其他電腦，您也必須使用下列程序更新 BizTalk 管理資料庫中的資料庫名稱的參考。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-107">To restore the Tracking Analysis Server database to an alternate computer, you must also update references to the database name in the BizTalk Management database by using the following procedure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f3f4c-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="f3f4c-108">Prerequisites</span></span>  
 <span data-ttu-id="f3f4c-109">您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-tracking-analysis-server-database-name"></a><span data-ttu-id="f3f4c-110">若要更新追蹤 Analysis Server 資料庫名稱的參考</span><span class="sxs-lookup"><span data-stu-id="f3f4c-110">To update references to the Tracking Analysis Server database name</span></span>  
  
1.  <span data-ttu-id="f3f4c-111">在目的地系統上，按一下 **啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="f3f4c-111">On the destination system, click **Start**, click **Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="f3f4c-112">在**連接到伺服器**對話方塊中，選取**伺服器類型**為**Database Engine**、 提供伺服器名稱、 提供認證來連線至伺服器，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-112">In the **Connect to Server** dialog box, select the **Server type** as **Database Engine**, provide a server name, provide the credentials to connect ot the server, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="f3f4c-113">按一下以開啟適當的伺服器，按兩下**資料庫**，按兩下**BizTalkMgmtDb**，然後按一下**資料表**。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-113">Open the appropriate server by clicking it, double-clicking **Databases**, double-clicking **BizTalkMgmtDb**, and then clicking **Tables**.</span></span>  
  
4.  <span data-ttu-id="f3f4c-114">在詳細資料窗格中，以滑鼠右鍵按一下**[adm_group]**，然後指向**開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-114">In the details pane, right-click **adm_Group**, and then point to **Open Table**.</span></span>  
  
5.  <span data-ttu-id="f3f4c-115">將對應至原始資料庫的資料行修改為參考新資料庫的適當值。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-115">Modify the columns corresponding to the original database to reference the appropriate values for the new database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3f4c-116">*\<DBType >* DBServerName 和 *\<DBType >* DBName 代表資料庫位置，其中 *\<DBType >*對應的型別資料庫中，例如，TrackingAnalysis。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-116">*\<DBType>* DBServerName and *\<DBType>* DBName indicate the location of the database, where *\<DBType>* corresponds to the type of the database, for example, TrackingAnalysis.</span></span>  
  
6.  <span data-ttu-id="f3f4c-117">關閉資料表以儲存新值。</span><span class="sxs-lookup"><span data-stu-id="f3f4c-117">Close the table to save the new values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f4c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3f4c-118">See Also</span></span>  
 [<span data-ttu-id="f3f4c-119">更新資料庫參考</span><span class="sxs-lookup"><span data-stu-id="f3f4c-119">Updating Database References</span></span>](../technical-guides/updating-database-references.md)