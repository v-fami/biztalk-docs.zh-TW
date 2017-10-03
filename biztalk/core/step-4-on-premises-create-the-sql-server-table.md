---
title: "步驟 4 （內部部署）： 建立 SQL Server 資料表 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e253ac-8707-484f-8461-f098cc7ec7d8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6a6934a98ccd101003519486388b09504b5f0ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-on-premises-create-the-sql-server-table"></a><span data-ttu-id="946f1-102">步驟 4 （內部部署）： 建立 SQL Server 資料表</span><span class="sxs-lookup"><span data-stu-id="946f1-102">Step 4 (On Premises): Create the SQL Server Table</span></span>
<span data-ttu-id="946f1-103">在商務案例，Contoso 銷售訂單訊息傳送至 Northwind 的 X12 訊息必須最後插入**SalesOrder**資料表，如果訂購數量大於 100。</span><span class="sxs-lookup"><span data-stu-id="946f1-103">As part of the business scenario, the message X12 sales order message sent by Contoso to Northwind must finally be inserted in a **SalesOrder** table, if the quantity ordered is greater than 100.</span></span> <span data-ttu-id="946f1-104">本主題說明如何建立**SalesOrder**是儲存在內部部署 SQL Server 資料庫執行個體中的資料表。</span><span class="sxs-lookup"><span data-stu-id="946f1-104">This topic provides instructions on how to create the **SalesOrder** table within a SQL Server database instance that is housed on-premises.</span></span>  
  
### <a name="to-create-the-salesorder-table"></a><span data-ttu-id="946f1-105">若要建立 SalesOrder 資料表</span><span class="sxs-lookup"><span data-stu-id="946f1-105">To create the SalesOrder table</span></span>  
  
1.  <span data-ttu-id="946f1-106">開啟 SQL Server Management Studio，您要建立資料表對資料庫執行下列查詢。</span><span class="sxs-lookup"><span data-stu-id="946f1-106">Open SQL Server Management Studio and run the following query against the database where you want to create the table.</span></span>  
  
2.  <span data-ttu-id="946f1-107">執行下列查詢，以建立**SalesOrder**資料表：</span><span class="sxs-lookup"><span data-stu-id="946f1-107">Run the following query to create the **SalesOrder** table:</span></span>  
  
    ```  
    CREATE TABLE [dbo].[SalesOrder] (  
        [SalesOrderID] int IDENTITY(1,1) NOT NULL,  
        [PartNum] int  NOT NULL,  
        [DateRequested] datetime  NULL,  
        [CompanyCode] varchar(3)  NOT NULL,  
        [Qty] int  NOT NULL,  
        [UnitAskPrice] float  NULL,  
        [ShipDate] datetime  NOT NULL,  
        [SellToAddress] varchar(255)  NULL,  
        [BillToAddress] varchar(255)  NOT NULL,  
        [PartnerContact] varchar(128)  NULL,  
        [CustomerComments] varchar(500)  NULL,  
        [RFQStatuesId] smallint  NULL  
    );  
    GO  
    ```  
  
3.  <span data-ttu-id="946f1-108">請確認目標資料庫中建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="946f1-108">Verify that the table is created in the target database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946f1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="946f1-109">See Also</span></span>  
 [<span data-ttu-id="946f1-110">教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="946f1-110">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)