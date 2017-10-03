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
# <a name="restoring-the-contoso-database"></a>還原 Contoso 資料庫
在此步驟中，您將使用 SQL Server Management Studio 執行 SQL 指令碼，以還原 Contoso 資料庫及其關聯的預存程序。 您也會在資料庫資料表中填入初步資料。  
  
### <a name="to-restore-the-contoso-database"></a>還原 Contoso 資料庫  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在 [連接到伺服器] 對話方塊中**SQL Server**方塊中，按一下**連接**。  
  
    > [!NOTE]
    >  如果未啟動 SQL Server 代理程式，以滑鼠右鍵按一下，然後再按一下**啟動**。  
  
3.  在 Microsoft SQL Server Management Studio 中，按一下 **新查詢**。  
  
4.  在 [查詢] 窗格中，複製下列 SQL 指令碼並貼到 [查詢] 視窗中：  
  
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
  
5.  按一下 **[執行]**。  
  
### <a name="to-set-permissions-on-the-contoso-database"></a>在 Contoso 資料庫上設定權限  
  
1.  在 Microsoft SQL Server Management Studio 的 物件總管 中，展開**資料庫**，依序展開**Contoso**資料庫，然後再展開**安全性**。 以滑鼠右鍵按一下 **[使用者]**，然後按一下 **[新增使用者]**。  
  
2.  在資料庫使用者-新增 對話方塊的**登入名稱**，按一下省略符號。  
  
3.  在 選取登入 對話方塊中，按一下 **瀏覽**。  
  
4.  在瀏覽物件] 對話方塊中，選取**BizTalk 應用程式使用者**，然後按一下 [**確定**。  
  
5.  在 選取登入 對話方塊中，按一下 **確定**。  
  
6.  在 [資料庫使用者-新增] 對話方塊，在**資料庫角色成員資格**窗格中，選取**db_datareader**和**db_datawriter**。 如**使用者名**，輸入**BizTalk 應用程式使用者**。 按一下 **[確定]**。  
  
7.  重複步驟 1 到 6 **BizTalk Isolated Host Users**、 選取**db_datareader**和**db_datawriter**如**資料庫角色成員資格**，並輸入**BizTalk Isolated Host Users**如**使用者名**。  
  
8.  重複步驟 1 到 6 **BizTalk Server 系統管理員**、 選取**db_owner**如**資料庫角色成員資格**，並輸入**BizTalk Server系統管理員**如**使用者名**。  
  
## <a name="see-also"></a>另請參閱  
 [產生並啟用憑證](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)