---
title: 複合 Operation2 如訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0164ea07-a373-430b-b569-3e29df1d081b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04ff8ec57d3c94e2191b1615593f0047e01b0e01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967991"
---
# <a name="message-schemas-for-the-composite-operation"></a><span data-ttu-id="001fe-102">複合作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="001fe-102">Message Schemas for the Composite Operation</span></span>
<span data-ttu-id="001fe-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]可讓您執行的 Oracle 資料庫上的複合作業。</span><span class="sxs-lookup"><span data-stu-id="001fe-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] enables you to execute composite operations on the Oracle database.</span></span> <span data-ttu-id="001fe-104">複合作業可以包含多個作業，並依照任何順序。</span><span class="sxs-lookup"><span data-stu-id="001fe-104">A composite operation can contain multiple operations, and in any order.</span></span> <span data-ttu-id="001fe-105">如需哪些作業可以包含在複合作業的資訊，請參閱[Oracle 資料庫中執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="001fe-105">For information about which operations can be included in a composite operation, see [Run Composite Operations in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-in-oracle-database.md).</span></span>  
  
 <span data-ttu-id="001fe-106">如需有關如何執行複合作業使用資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 使用 BizTalk Server 的 Oracle 資料庫上執行複合作業](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="001fe-106">For information about how to perform composite operations using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
## <a name="message-structure-for-the-composite-operation"></a><span data-ttu-id="001fe-107">複合作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="001fe-107">Message Structure for the Composite Operation</span></span>  
 <span data-ttu-id="001fe-108">因為複合作業包含多個個別的作業;複合作業的訊息結構包含的個別作業的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="001fe-108">Because a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations.</span></span> <span data-ttu-id="001fe-109">複合作業訊息會遵循要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="001fe-109">The composite operation message follows a request-response message exchange pattern.</span></span>  
  
 <span data-ttu-id="001fe-110">下表顯示包含插入作業的複合作業的要求和回應訊息的結構、 已封裝的預存程序不接受任何輸入參數和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="001fe-110">The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a packaged stored procedure that does not take any input parameters, and a Delete operation.</span></span>  
  
|<span data-ttu-id="001fe-111">作業</span><span class="sxs-lookup"><span data-stu-id="001fe-111">Operation</span></span>|<span data-ttu-id="001fe-112">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="001fe-112">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="001fe-113">複合作業要求</span><span class="sxs-lookup"><span data-stu-id="001fe-113">Composite Operation Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <RECORDSET>       <[TABLE_NAME]RECORDINSERT>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>         …       </[TABLE_NAME]RECORDINSERT>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="[VERSION]/[SCHEMA]/Procedure" />   <Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|<span data-ttu-id="001fe-114">複合作業回應</span><span class="sxs-lookup"><span data-stu-id="001fe-114">Composite Operation Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="[VERSION]/[SCHEMA]/Procedure">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 <span data-ttu-id="001fe-115">[VERSION] = 訊息版本字串;比方說， http://Microsoft.LobServices.OracleDB/2007/03</span><span class="sxs-lookup"><span data-stu-id="001fe-115">[VERSION] = The message version string; for example, http://Microsoft.LobServices.OracleDB/2007/03</span></span>  
  
 <span data-ttu-id="001fe-116">[PROJECT_NAME] = 包含複合作業結構描述的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="001fe-116">[PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.</span></span>  
  
 <span data-ttu-id="001fe-117">[COMPOSITE_SCHEMA_NAME] = 由使用者指定的複合作業結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="001fe-117">[COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.</span></span>  
  
 <span data-ttu-id="001fe-118">[SCHEMA] = 集合的 Oracle 成品、比方說，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="001fe-118">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="001fe-119">[TABLE_NAME] = 資料表的名稱例如，員工。</span><span class="sxs-lookup"><span data-stu-id="001fe-119">[TABLE_NAME] = Name of the table; for example, EMPLOYEE.</span></span>  
  
 <span data-ttu-id="001fe-120">[FIELD1_NAME] = 資料表的欄位名稱;例如，名稱。</span><span class="sxs-lookup"><span data-stu-id="001fe-120">[FIELD1_NAME] = Table field name; for example, NAME.</span></span>  
  
 <span data-ttu-id="001fe-121">[SP_NAME] = [執行封裝的預存程序比方說，ADD_EMP_DETAILS。</span><span class="sxs-lookup"><span data-stu-id="001fe-121">[SP_NAME] = The packaged stored procedure to be executed; for example, ADD_EMP_DETAILS.</span></span>  
  
 <span data-ttu-id="001fe-122">[PRM1_NAME] = Oracle 參數在預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="001fe-122">[PRM1_NAME] = The name of the Oracle parameter in the stored procedure.</span></span>  
  
## <a name="message-action-for-the-composite-operation"></a><span data-ttu-id="001fe-123">複合作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="001fe-123">Message Action for the Composite Operation</span></span>  
 <span data-ttu-id="001fe-124">複合作業的訊息動作是 」<http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation.”></span><span class="sxs-lookup"><span data-stu-id="001fe-124">The message action for the composite operation is “<http://Microsoft.LobServices.OracleDB/2007/03/CompositeOperation.”></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001fe-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="001fe-125">See Also</span></span>  
 [<span data-ttu-id="001fe-126">BizTalk Adapter for Oracle Database 的訊息和訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="001fe-126">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)