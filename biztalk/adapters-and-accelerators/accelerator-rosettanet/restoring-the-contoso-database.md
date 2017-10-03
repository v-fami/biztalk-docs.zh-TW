---
title: "還原 Contoso 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, restoring databases
- databases, restoring
ms.assetid: 291178c1-826e-49e0-a1d2-cbffee749659
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f77c242fe6477baac53b6a3e1b2fda545a7e4365
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-the-contoso-database"></a><span data-ttu-id="dfeba-102">還原 Contoso 資料庫</span><span class="sxs-lookup"><span data-stu-id="dfeba-102">Restoring the Contoso Database</span></span>
<span data-ttu-id="dfeba-103">在此步驟中，您將使用 SQL Server Management Studio 執行 SQL 指令碼，以還原 Contoso 資料庫及其關聯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dfeba-103">In this step, you use SQL Server Management Studio to run a SQL script to restore the Contoso database and its associated stored procedures.</span></span> <span data-ttu-id="dfeba-104">您也會在資料庫資料表中填入初步資料。</span><span class="sxs-lookup"><span data-stu-id="dfeba-104">You also populate the database tables with preliminary data.</span></span>  
  
### <a name="to-restore-the-contoso-database"></a><span data-ttu-id="dfeba-105">還原 Contoso 資料庫</span><span class="sxs-lookup"><span data-stu-id="dfeba-105">To restore the Contoso database</span></span>  
  
1.  <span data-ttu-id="dfeba-106">按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="dfeba-107">在 [連接到伺服器] 對話方塊中**SQL Server**方塊中，按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-107">In the Connect to Server dialog box, in the **SQL Server** box, click **Connect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dfeba-108">如果未啟動 SQL Server 代理程式，以滑鼠右鍵按一下，然後再按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-108">If the SQL Server Agent is not started, right-click it, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="dfeba-109">在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-109">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="dfeba-110">在 [查詢] 窗格中，複製下列 SQL 指令碼並貼到 [查詢] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="dfeba-110">In the Query pane, copy and paste the following SQL script into the Query window:</span></span>  
  
    ```  
    CREATE DATABASE Contoso  
    GO  
    USE Contoso  
    GO  
    CREATE TABLE Products (  
    [ProductID] [varchar] (255) NOT NULL ,  
    [Name] [varchar] (255) NOT NULL ,  
    [Description] [varchar] (800) NULL ,  
    [Price] [money] NULL ,  
    [NumberAvailable] [int] NOT NULL   
    ) ON [PRIMARY]  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901234', 'ADM Line Card','',200.65,820 )  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901235','Analog Line Card','',165.24,769 )  
    GO  
    INSERT INTO Products  
    VALUES( '12345678901236', 'Mapper/MUX','',150.54,948)  
    GO  
    CREATE TABLE StatusCodes (  
    [statusID] [int] NOT NULL ,  
    [statusCode] [nvarchar] (50) NOT NULL   
    ) ON [PRIMARY]  
    GO  
    CREATE PROCEDURE GetInventoryForProductID  
    @ProductID varchar(255),  
    @NumberAvailable INT OUTPUT,  
    @Price MONEY OUTPUT  
    AS  
    SET NOCOUNT ON  
    SELECT @NumberAvailable = NumberAvailable,  
     @Price = Price  
    FROM Products  
    WHERE  ProductID = @ProductID  
    RETURN(0)  
    GO  
    CREATE PROCEDURE SP_GetInventoryForProductID  
    @ProductID varchar(255)  
    AS  
    SET NOCOUNT ON  
    SELECT *  
    FROM Products  
    WHERE ProductID = @ProductID  
    for xml auto  
    RETURN(0)  
    ```  
  
5.  <span data-ttu-id="dfeba-111">按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-111">Click **Execute**.</span></span>  
  
### <a name="to-set-permissions-on-the-contoso-database"></a><span data-ttu-id="dfeba-112">在 Contoso 資料庫上設定權限</span><span class="sxs-lookup"><span data-stu-id="dfeba-112">To set permissions on the Contoso database</span></span>  
  
1.  <span data-ttu-id="dfeba-113">在 Microsoft SQL Server Management Studio 的 物件總管 中，展開**資料庫**，依序展開**Contoso**資料庫，然後再展開**安全性**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-113">In the Object Explorer of the Microsoft SQL Server Management Studio, expand **Databases**, expand the **Contoso** database, and then expand **Security**.</span></span> <span data-ttu-id="dfeba-114">以滑鼠右鍵按一下 **[使用者]**，然後按一下 **[新增使用者]**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-114">Right-click **Users**, and then click **New User**.</span></span>  
  
2.  <span data-ttu-id="dfeba-115">在資料庫使用者-新增 對話方塊的**登入名稱**，按一下省略符號。</span><span class="sxs-lookup"><span data-stu-id="dfeba-115">In the Database User - New dialog box, for **Login name**, click the ellipsis.</span></span>  
  
3.  <span data-ttu-id="dfeba-116">在 選取登入 對話方塊中，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-116">In the Select Login dialog box, click **Browse**.</span></span>  
  
4.  <span data-ttu-id="dfeba-117">在瀏覽物件] 對話方塊中，選取**BizTalk 應用程式使用者**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-117">In the Browse for Objects dialog box, select **BizTalk Application Users**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="dfeba-118">在 選取登入 對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-118">In the Select Login dialog box, click **OK**.</span></span>  
  
6.  <span data-ttu-id="dfeba-119">在 [資料庫使用者-新增] 對話方塊，在**資料庫角色成員資格**窗格中，選取**db_datareader**和**db_datawriter**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-119">In the Database User - New dialog box, in the **Database role membership** pane, select **db_datareader** and **db_datawriter**.</span></span> <span data-ttu-id="dfeba-120">如**使用者名**，輸入**BizTalk 應用程式使用者**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-120">For **User name**, enter **BizTalk Application Users**.</span></span> <span data-ttu-id="dfeba-121">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-121">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="dfeba-122">重複步驟 1 到 6 **BizTalk Isolated Host Users**、 選取**db_datareader**和**db_datawriter**如**資料庫角色成員資格**，並輸入**BizTalk Isolated Host Users**如**使用者名**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-122">Repeat steps 1 through 6 for **BizTalk Isolated Host Users**, selecting **db_datareader** and **db_datawriter** for **Database role membership**, and entering **BizTalk Isolated Host Users** for **User name**.</span></span>  
  
8.  <span data-ttu-id="dfeba-123">重複步驟 1 到 6 **BizTalk Server 系統管理員**、 選取**db_owner**如**資料庫角色成員資格**，並輸入**BizTalk Server系統管理員**如**使用者名**。</span><span class="sxs-lookup"><span data-stu-id="dfeba-123">Repeat steps 1 through 6 for **BizTalk Server Administrators**, selecting **db_owner** for **Database role membership**, and entering **BizTalk Server Administrators** for **User name**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfeba-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfeba-124">See Also</span></span>  
 [<span data-ttu-id="dfeba-125">產生並啟用憑證</span><span class="sxs-lookup"><span data-stu-id="dfeba-125">Generating and Enabling Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)