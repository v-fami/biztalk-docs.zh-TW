---
title: 複合作業的訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d80c023b-1912-43d4-be29-eb9e1b323593
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 716e87dd2973572d473f6637e12c5a80ac6cf847
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015290"
---
# <a name="message-schemas-for-composite-operations"></a><span data-ttu-id="84f53-102">複合作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="84f53-102">Message Schemas for Composite Operations</span></span>
<span data-ttu-id="84f53-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]可讓您執行 SQL Server 資料庫上的複合作業。</span><span class="sxs-lookup"><span data-stu-id="84f53-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] enables you to execute composite operations on the SQL Server database.</span></span> <span data-ttu-id="84f53-104">複合作業可以包含多項作業包括 Insert、 Update 和刪除作業的資料表和檢視表和預存程序的作業。</span><span class="sxs-lookup"><span data-stu-id="84f53-104">A composite operation can contain multiple operations including the Insert, Update, and Delete operations on the tables and views, and operations on stored procedures.</span></span> <span data-ttu-id="84f53-105">複合作業可以依任何順序來包含這些作業。</span><span class="sxs-lookup"><span data-stu-id="84f53-105">A composite operation can include these operations in any order.</span></span>  
  
 <span data-ttu-id="84f53-106">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="84f53-106">For more information about:</span></span>  
  
- <span data-ttu-id="84f53-107">複合作業，請參閱[支援複合作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)。</span><span class="sxs-lookup"><span data-stu-id="84f53-107">Composite operations, see [Support for Composite Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).</span></span>  
  
- <span data-ttu-id="84f53-108">如何執行複合作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 使用 SQL 配接器的 SQL Server 中執行複合作業](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="84f53-108">How to perform composite operations using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], see [Run composite operations in SQL Server  using the SQL adapter](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
## <a name="message-structure-for-the-composite-operation"></a><span data-ttu-id="84f53-109">複合作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="84f53-109">Message Structure for the Composite Operation</span></span>  
 <span data-ttu-id="84f53-110">由於複合作業包含多個個別的作業;複合作業的訊息結構包含的個別作業的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="84f53-110">Since a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations.</span></span> <span data-ttu-id="84f53-111">複合作業包含資料表、 檢視和預存程序上的作業，因為複合作業訊息會遵循要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="84f53-111">As a composite operation contains operations on tables, views, and stored procedures, the composite operation message follows a request-response message exchange pattern.</span></span>  
  
 <span data-ttu-id="84f53-112">下表顯示包含插入作業的複合作業的要求和回應訊息的結構，不接受任何預存程序輸入參數和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="84f53-112">The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a stored procedure that does not take any input parameters, and a Delete operation.</span></span>  
  
|<span data-ttu-id="84f53-113">作業</span><span class="sxs-lookup"><span data-stu-id="84f53-113">Operation</span></span>|<span data-ttu-id="84f53-114">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="84f53-114">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84f53-115">複合作業要求</span><span class="sxs-lookup"><span data-stu-id="84f53-115">Composite Operation Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[Value1]</[FIELD2_NAME]>         …       </[TABLE_NAME]>     </Rows>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]" />   <Delete xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <Rows>       <[TABLE_NAME]>         <[FIELD1_NAME]>[Value1]</[FIELD1_NAME]>       </[TABLE_NAME]>     </Rows>   </Delete> </Request>`|  
|<span data-ttu-id="84f53-116">複合作業回應</span><span class="sxs-lookup"><span data-stu-id="84f53-116">Composite Operation Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <InsertResult>       <long>[value]</long>      </InsertResult>   </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/[SCHEMA]">     <[SP_NAME]Result>       <DataSet>         <any>[Value]</any>          <any>[Value]</any>          …       </DataSet>     </[SP_NAME]Result>     <ReturnValue>[value]</ReturnValue>    </[SP_NAME]Response>   <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 <span data-ttu-id="84f53-117">[PROJECT_NAME] = 包含複合作業結構描述的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="84f53-117">[PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.</span></span>  
  
 <span data-ttu-id="84f53-118">[COMPOSITE_SCHEMA_NAME] = 由使用者指定的複合作業結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="84f53-118">[COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.</span></span>  
  
 <span data-ttu-id="84f53-119">[SCHEMA] = Collection 的 SQL Server 成品、比方說，dbo。</span><span class="sxs-lookup"><span data-stu-id="84f53-119">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
 <span data-ttu-id="84f53-120">[TABLE_NAME] = 資料表的名稱例如，員工。</span><span class="sxs-lookup"><span data-stu-id="84f53-120">[TABLE_NAME] = Name of the table; for example, Employee.</span></span>  
  
 <span data-ttu-id="84f53-121">[FIELD1_NAME] = 資料表的欄位名稱;例如，名稱。</span><span class="sxs-lookup"><span data-stu-id="84f53-121">[FIELD1_NAME] = Table field name; for example, NAME.</span></span>  
  
 <span data-ttu-id="84f53-122">[SP_NAME] = 預存程序的執行;比方說，ADD_EMP_DETAILS。</span><span class="sxs-lookup"><span data-stu-id="84f53-122">[SP_NAME] = The stored procedure to be executed; for example, ADD_EMP_DETAILS.</span></span>  
  
## <a name="message-action-for-the-composite-operation"></a><span data-ttu-id="84f53-123">複合作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="84f53-123">Message Action for the Composite Operation</span></span>  
 <span data-ttu-id="84f53-124">複合作業的訊息動作是 「 CompositeOperation。 」</span><span class="sxs-lookup"><span data-stu-id="84f53-124">The message action for the composite operation is “CompositeOperation.”</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f53-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84f53-125">See Also</span></span>  
 [<span data-ttu-id="84f53-126">訊息和訊息結構描述，BizTalk adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="84f53-126">Messages and Message Schemas for BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)