---
title: "訊息結構描述的複合 Operation2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0164ea07-a373-430b-b569-3e29df1d081b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1014ea162e9fab33aa6630d0cdb4eb774f91031
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-composite-operation"></a><span data-ttu-id="04bae-102">複合作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="04bae-102">Message Schemas for the Composite Operation</span></span>
<span data-ttu-id="04bae-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]可讓您執行複合操作的 Oracle 資料庫上。</span><span class="sxs-lookup"><span data-stu-id="04bae-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] enables you to execute composite operations on the Oracle database.</span></span> <span data-ttu-id="04bae-104">複合作業可以包含多個作業，並依照任何順序。</span><span class="sxs-lookup"><span data-stu-id="04bae-104">A composite operation can contain multiple operations, and in any order.</span></span> <span data-ttu-id="04bae-105">有關哪些作業可以包含在複合作業的資訊，請參閱[Oracle 資料庫中執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="04bae-105">For information about which operations can be included in a composite operation, see [Run Composite Operations in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md).</span></span>  
  
 <span data-ttu-id="04bae-106">如需如何執行複合操作使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[使用 BizTalk Server 的 Oracle 資料庫上執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="04bae-106">For information about how to perform composite operations using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
## <a name="message-structure-for-the-composite-operation"></a><span data-ttu-id="04bae-107">複合作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="04bae-107">Message Structure for the Composite Operation</span></span>  
 <span data-ttu-id="04bae-108">因為複合作業包含多個個別作業;複合作業的訊息結構包含個別作業的訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="04bae-108">Because a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations.</span></span> <span data-ttu-id="04bae-109">複合作業訊息會遵循要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="04bae-109">The composite operation message follows a request-response message exchange pattern.</span></span>  
  
 <span data-ttu-id="04bae-110">下表顯示包含一個插入作業的複合作業的要求和回應訊息的結構、 已封裝的預存程序不接受任何輸入參數和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="04bae-110">The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a packaged stored procedure that does not take any input parameters, and a Delete operation.</span></span>  
  
|<span data-ttu-id="04bae-111">作業</span><span class="sxs-lookup"><span data-stu-id="04bae-111">Operation</span></span>|<span data-ttu-id="04bae-112">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="04bae-112">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04bae-113">複合作業要求</span><span class="sxs-lookup"><span data-stu-id="04bae-113">Composite Operation Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <RECORDSET>       <[TABLE_NAME]RECORDINSERT>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>         …       </[TABLE_NAME]RECORDINSERT>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="[VERSION]/[SCHEMA]/Procedure" />   <Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|<span data-ttu-id="04bae-114">複合作業回應</span><span class="sxs-lookup"><span data-stu-id="04bae-114">Composite Operation Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="[VERSION]/[SCHEMA]/Procedure">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 <span data-ttu-id="04bae-115">[版本] = 訊息版本字串。例如，http://Microsoft.LobServices.OracleDB/2007/03</span><span class="sxs-lookup"><span data-stu-id="04bae-115">[VERSION] = The message version string; for example, http://Microsoft.LobServices.OracleDB/2007/03</span></span>  
  
 <span data-ttu-id="04bae-116">[PROJECT_NAME] = 包含複合作業結構描述的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="04bae-116">[PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.</span></span>  
  
 <span data-ttu-id="04bae-117">[COMPOSITE_SCHEMA_NAME] = 由使用者指定的複合作業結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="04bae-117">[COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.</span></span>  
  
 <span data-ttu-id="04bae-118">[SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="04bae-118">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="04bae-119">[TABLE_NAME] = 表格的名稱例如，員工。</span><span class="sxs-lookup"><span data-stu-id="04bae-119">[TABLE_NAME] = Name of the table; for example, EMPLOYEE.</span></span>  
  
 <span data-ttu-id="04bae-120">[FIELD1_NAME] = 表格欄位的名稱。例如，名稱。</span><span class="sxs-lookup"><span data-stu-id="04bae-120">[FIELD1_NAME] = Table field name; for example, NAME.</span></span>  
  
 <span data-ttu-id="04bae-121">[SP_NAME] = 封裝預存程序的執行。例如，ADD_EMP_DETAILS。</span><span class="sxs-lookup"><span data-stu-id="04bae-121">[SP_NAME] = The packaged stored procedure to be executed; for example, ADD_EMP_DETAILS.</span></span>  
  
 <span data-ttu-id="04bae-122">[PRM1_NAME] = Oracle 參數，預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="04bae-122">[PRM1_NAME] = The name of the Oracle parameter in the stored procedure.</span></span>  
  
## <a name="message-action-for-the-composite-operation"></a><span data-ttu-id="04bae-123">複合作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="04bae-123">Message Action for the Composite Operation</span></span>  
 <span data-ttu-id="04bae-124">複合作業的訊息動作是 「 http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation。 」</span><span class="sxs-lookup"><span data-stu-id="04bae-124">The message action for the composite operation is “http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation.”</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bae-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04bae-125">See Also</span></span>  
 [<span data-ttu-id="04bae-126">訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="04bae-126">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)