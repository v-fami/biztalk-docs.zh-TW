---
title: 更新追蹤 Analysis Server 資料庫的參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a403325-1394-4668-946f-01b610cb686e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 417569d99b7326b435422b5fa0dff28019006116
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014703"
---
# <a name="update-references-to-the-tracking-analysis-server-database"></a><span data-ttu-id="c0f4e-102">更新追蹤 Analysis Server 資料庫的參考</span><span class="sxs-lookup"><span data-stu-id="c0f4e-102">Update References to the Tracking Analysis Server Database</span></span>
<span data-ttu-id="c0f4e-103">追蹤 Analysis Server 資料庫是選擇性的包含的線上分析處理 (OLAP) cube。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-103">The Tracking Analysis Server database is an optional and contains the online analytical processing (OLAP) cubes.</span></span> <span data-ttu-id="c0f4e-104">這些 OLAP Cube 是包含在 BizTalk 追蹤資料庫中的資料彙總。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-104">These OLAP cubes are aggregations of data contained in the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="c0f4e-105">若要還原追蹤 Analysis Server 資料庫，請使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]分析管理員來處理 MessageMetrics 和 ServiceMetrics cube。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-105">To restore the Tracking Analysis Server database, use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager to process the MessageMetrics and ServiceMetrics cubes.</span></span> <span data-ttu-id="c0f4e-106">如需相關指示，請參閱 <<c0> [ 管理備份和還原 (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (<http://go.microsoft.com/fwlink/?LinkId=130939>) 中[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-106">For instructions, see [Managing Backing Up and Restoring (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (<http://go.microsoft.com/fwlink/?LinkId=130939>) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="c0f4e-107">追蹤 Analysis Server 資料庫還原到其他電腦，您也必須使用下列程序更新 BizTalk 管理資料庫中的資料庫名稱的參考。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-107">To restore the Tracking Analysis Server database to an alternate computer, you must also update references to the database name in the BizTalk Management database by using the following procedure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c0f4e-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="c0f4e-108">Prerequisites</span></span>  
 <span data-ttu-id="c0f4e-109">您必須以 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators 群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-tracking-analysis-server-database-name"></a><span data-ttu-id="c0f4e-110">若要更新追蹤 Analysis Server 資料庫名稱的參考</span><span class="sxs-lookup"><span data-stu-id="c0f4e-110">To update references to the Tracking Analysis Server database name</span></span>  
  
1.  <span data-ttu-id="c0f4e-111">在目的地系統上，按一下**開始**，按一下**程式**，按一下  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="c0f4e-111">On the destination system, click **Start**, click **Programs**, click **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="c0f4e-112">在**連接到伺服器**對話方塊中，選取**伺服器類型**做為**Database Engine**、 提供伺服器名稱、 提供認證以連線至伺服器，然後按一下  **Connect**。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-112">In the **Connect to Server** dialog box, select the **Server type** as **Database Engine**, provide a server name, provide the credentials to connect ot the server, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="c0f4e-113">按一下以開啟適當的伺服器，按兩下**資料庫**，按兩下**BizTalkMgmtDb**，然後按一下**資料表**。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-113">Open the appropriate server by clicking it, double-clicking **Databases**, double-clicking **BizTalkMgmtDb**, and then clicking **Tables**.</span></span>  
  
4.  <span data-ttu-id="c0f4e-114">在 [詳細資料] 窗格中，以滑鼠右鍵按一下 **[adm_group]**，再指向**開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-114">In the details pane, right-click **adm_Group**, and then point to **Open Table**.</span></span>  
  
5.  <span data-ttu-id="c0f4e-115">將對應至原始資料庫的資料行修改為參考新資料庫的適當值。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-115">Modify the columns corresponding to the original database to reference the appropriate values for the new database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c0f4e-116">*\<DBType\>*  DBServerName 並*\<DBType\>* DBName 指示位置的資料庫，其中*\<DBType\>* 對應至資料庫，例如，TrackingAnalysis 的型別。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-116">*\<DBType\>* DBServerName and *\<DBType\>* DBName indicate the location of the database, where *\<DBType\>* corresponds to the type of the database, for example, TrackingAnalysis.</span></span>  
  
6.  <span data-ttu-id="c0f4e-117">關閉資料表以儲存新值。</span><span class="sxs-lookup"><span data-stu-id="c0f4e-117">Close the table to save the new values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0f4e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f4e-118">See Also</span></span>  
 [<span data-ttu-id="c0f4e-119">更新資料庫參考</span><span class="sxs-lookup"><span data-stu-id="c0f4e-119">Updating Database References</span></span>](../technical-guides/updating-database-references.md)