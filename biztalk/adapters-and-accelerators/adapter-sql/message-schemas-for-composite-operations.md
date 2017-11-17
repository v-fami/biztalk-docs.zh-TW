---
title: "複合作業的訊息結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d80c023b-1912-43d4-be29-eb9e1b323593
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b89c354baea2ddb46abf549752dc09699b9c9695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-composite-operations"></a><span data-ttu-id="9c258-102">複合操作的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="9c258-102">Message Schemas for Composite Operations</span></span>
<span data-ttu-id="9c258-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]可讓您執行 SQL Server 資料庫上的複合作業。</span><span class="sxs-lookup"><span data-stu-id="9c258-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] enables you to execute composite operations on the SQL Server database.</span></span> <span data-ttu-id="9c258-104">複合作業可以包含多項作業包括 Insert、 Update 及刪除資料表和檢視表上的作業和預存程序上的作業。</span><span class="sxs-lookup"><span data-stu-id="9c258-104">A composite operation can contain multiple operations including the Insert, Update, and Delete operations on the tables and views, and operations on stored procedures.</span></span> <span data-ttu-id="9c258-105">複合作業可以依任何順序包含這些作業。</span><span class="sxs-lookup"><span data-stu-id="9c258-105">A composite operation can include these operations in any order.</span></span>  
  
 <span data-ttu-id="9c258-106">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="9c258-106">For more information about:</span></span>  
  
-   <span data-ttu-id="9c258-107">複合作業，請參閱[複合作業的支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)。</span><span class="sxs-lookup"><span data-stu-id="9c258-107">Composite operations, see [Support for Composite Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).</span></span>  
  
-   <span data-ttu-id="9c258-108">如何執行複合操作使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[使用 SQL 配接器的 SQL Server 中執行複合操作](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="9c258-108">How to perform composite operations using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Run composite operations in SQL Server  using the SQL adapter](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
## <a name="message-structure-for-the-composite-operation"></a><span data-ttu-id="9c258-109">複合作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="9c258-109">Message Structure for the Composite Operation</span></span>  
 <span data-ttu-id="9c258-110">由於複合作業包含多個個別作業;複合作業的訊息結構包含個別作業的訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="9c258-110">Since a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations.</span></span> <span data-ttu-id="9c258-111">複合作業包含資料表、 檢視和預存程序上的作業，因為複合作業訊息會遵循要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9c258-111">As a composite operation contains operations on tables, views, and stored procedures, the composite operation message follows a request-response message exchange pattern.</span></span>  
  
 <span data-ttu-id="9c258-112">下表顯示包含一個插入作業的複合作業的要求和回應訊息的結構、 預存程序不接受任何輸入參數和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="9c258-112">The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a stored procedure that does not take any input parameters, and a Delete operation.</span></span>  
  
|<span data-ttu-id="9c258-113">作業</span><span class="sxs-lookup"><span data-stu-id="9c258-113">Operation</span></span>|<span data-ttu-id="9c258-114">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="9c258-114">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c258-115">複合作業要求</span><span class="sxs-lookup"><span data-stu-id="9c258-115">Composite Operation Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[Value1]</[FIELD2_NAME]>         …       </[TABLE_NAME]>     </Rows>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]" />   <Delete xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>       </[TABLE_NAME]>     </Rows>   </Delete> </Request>`|  
|<span data-ttu-id="9c258-116">複合作業回應</span><span class="sxs-lookup"><span data-stu-id="9c258-116">Composite Operation Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <InsertResult>       <long>[value]</long>      </InsertResult>   </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">     <[SP_NAME]Result>       <DataSet>         <any>[Value]</any>          <any>[Value]</any>          …       </DataSet>     </[SP_NAME]Result>     <ReturnValue>[value]</ReturnValue>    </[SP_NAME]Response>   <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 <span data-ttu-id="9c258-117">[PROJECT_NAME] = 包含複合作業結構描述的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c258-117">[PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.</span></span>  
  
 <span data-ttu-id="9c258-118">[COMPOSITE_SCHEMA_NAME] = 由使用者指定的複合作業結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c258-118">[COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.</span></span>  
  
 <span data-ttu-id="9c258-119">[SCHEMA] = 集合 SQL Server 成品。例如，dbo。</span><span class="sxs-lookup"><span data-stu-id="9c258-119">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
 <span data-ttu-id="9c258-120">[TABLE_NAME] = 表格的名稱例如，員工。</span><span class="sxs-lookup"><span data-stu-id="9c258-120">[TABLE_NAME] = Name of the table; for example, Employee.</span></span>  
  
 <span data-ttu-id="9c258-121">[FIELD1_NAME] = 表格欄位的名稱。例如，名稱。</span><span class="sxs-lookup"><span data-stu-id="9c258-121">[FIELD1_NAME] = Table field name; for example, NAME.</span></span>  
  
 <span data-ttu-id="9c258-122">[SP_NAME] = 預存程序的執行。例如，ADD_EMP_DETAILS。</span><span class="sxs-lookup"><span data-stu-id="9c258-122">[SP_NAME] = The stored procedure to be executed; for example, ADD_EMP_DETAILS.</span></span>  
  
## <a name="message-action-for-the-composite-operation"></a><span data-ttu-id="9c258-123">複合作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="9c258-123">Message Action for the Composite Operation</span></span>  
 <span data-ttu-id="9c258-124">複合作業的訊息動作是 「 CompositeOperation。 」</span><span class="sxs-lookup"><span data-stu-id="9c258-124">The message action for the composite operation is “CompositeOperation.”</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c258-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c258-125">See Also</span></span>  
 [<span data-ttu-id="9c258-126">訊息與 BizTalk adapter for SQL Server 的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="9c258-126">Messages and Message Schemas for BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)