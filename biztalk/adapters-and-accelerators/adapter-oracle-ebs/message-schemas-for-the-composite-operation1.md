---
title: 訊息結構描述的複合 Operation1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 768473ef-da8d-4e58-86cb-597c28ded49c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b22861d36693ab3ef487e5e3d0b86544f048e95
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215174"
---
# <a name="message-schemas-for-the-composite-operation"></a><span data-ttu-id="9f6fa-102">複合作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="9f6fa-102">Message Schemas for the Composite Operation</span></span>
<span data-ttu-id="9f6fa-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]可讓您執行複合操作 Oracle E-business Suite 中。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] enables you to execute composite operations in Oracle E-Business Suite.</span></span> <span data-ttu-id="9f6fa-104">複合作業可以包含多個作業，並依照任何順序。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-104">A composite operation can contain multiple operations, and in any order.</span></span> <span data-ttu-id="9f6fa-105">有關哪些作業可以包含在複合作業的資訊，請參閱[複合作業的支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-105">For information about which operations can be included in a composite operation, see [Support for Composite Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md).</span></span>  
  
 <span data-ttu-id="9f6fa-106">如需如何執行複合操作使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[使用 BizTalk Server 的 Oracle 資料庫上執行複合操作](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-106">For information about how to perform composite operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).</span></span>  
  
## <a name="message-structure-for-the-composite-operation"></a><span data-ttu-id="9f6fa-107">複合作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="9f6fa-107">Message Structure for the Composite Operation</span></span>  
 <span data-ttu-id="9f6fa-108">由於複合作業包含多個個別作業;複合作業的訊息結構包含個別作業的訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-108">Since a composite operation contains multiple individual operations; the message structure of a composite operation contains message structures of the individual operations.</span></span> <span data-ttu-id="9f6fa-109">複合作業訊息會遵循要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-109">The composite operation message follows a request-response message exchange pattern.</span></span>  
  
 <span data-ttu-id="9f6fa-110">下表顯示包含一個插入作業的複合作業的要求和回應訊息的結構、 已封裝的預存程序不接受任何輸入參數和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-110">The following table shows the structure of the request and response messages of a composite operation that contains an Insert operation, a packaged stored procedure that does not take any input parameters, and a Delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f6fa-111">在資料表之後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-111">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="9f6fa-112">作業</span><span class="sxs-lookup"><span data-stu-id="9f6fa-112">Operation</span></span>|<span data-ttu-id="9f6fa-113">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="9f6fa-113">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f6fa-114">複合作業要求</span><span class="sxs-lookup"><span data-stu-id="9f6fa-114">Composite Operation Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <Request xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <Recordset>       <InsertRecord>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>           <InLineValue>[value]</InlineValue>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>           <InLineValue>[value]</InlineValue>         …       <InsertRecord>    </RECORDSET>   </Insert>   <[SP_NAME] xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/[SCHEMA]/[APP_NAME]" />   <Delete xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <FILTER>[WHERE_clause]</FILTER>   </Delete> </Request>`|  
|<span data-ttu-id="9f6fa-115">複合作業回應</span><span class="sxs-lookup"><span data-stu-id="9f6fa-115">Composite Operation Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?>  <RequestResponse xmlns="http://[PROJECT_NAME].[COMPOSITE_SCHEMA_NAME]">   <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Tables/[SCHEMA]/[TABLE_NAME]">     <InsertResult>[value]</InsertResult>    </InsertResponse>   <[SP_NAME]Response xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Procedures/[SCHEMA]">     <[PRM1_NAME]>value1<[PRM1_NAME]>     <[PRM2_NAME]>value2</[PRM2_NAME]>     …   </[SP_NAME]Response>    <DeleteResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableOp/[SCHEMA]/[TABLE_NAME]">     <DeleteResult>[value]</DeleteResult>    </DeleteResponse> </RequestResponse>`|  
  
 <span data-ttu-id="9f6fa-116">實體描述：</span><span class="sxs-lookup"><span data-stu-id="9f6fa-116">Entity descriptions:</span></span>  
  
 <span data-ttu-id="9f6fa-117">[PROJECT_NAME] = 包含複合作業結構描述的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-117">[PROJECT_NAME] = Name of the BizTalk project that contains the composite operation schema.</span></span>  
  
 <span data-ttu-id="9f6fa-118">[COMPOSITE_SCHEMA_NAME] = 由使用者指定的複合作業結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-118">[COMPOSITE_SCHEMA_NAME] = Name of the composite operation schema given by the user.</span></span>  
  
 <span data-ttu-id="9f6fa-119">[SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-119">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="9f6fa-120">[TABLE_NAME] = 表格的名稱例如，員工。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-120">[TABLE_NAME] = Name of the table; for example, EMPLOYEE.</span></span>  
  
 <span data-ttu-id="9f6fa-121">[FIELD1_NAME] = 表格欄位的名稱。例如，名稱。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-121">[FIELD1_NAME] = Table field name; for example, NAME.</span></span>  
  
 <span data-ttu-id="9f6fa-122">[SP_NAME] = 封裝預存程序的執行。例如，ADD_EMP_DETAILS。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-122">[SP_NAME] = The packaged stored procedure to be executed; for example, ADD_EMP_DETAILS.</span></span>  
  
 <span data-ttu-id="9f6fa-123">[APP_NAME] = Oracle 應用程式，其中包含封裝的預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-123">[APP_NAME] = Name of the Oracle Application that contains the packaged stored procedure.</span></span>  
  
 <span data-ttu-id="9f6fa-124">[PRM1_NAME] = Oracle 中的參數封裝的預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f6fa-124">[PRM1_NAME] = The name of the Oracle parameter in the packaged stored procedure.</span></span>  
  
## <a name="message-action-for-the-composite-operation"></a><span data-ttu-id="9f6fa-125">複合作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="9f6fa-125">Message Action for the Composite Operation</span></span>  
 <span data-ttu-id="9f6fa-126">複合作業的訊息動作是 「 CompositeOperation。 」</span><span class="sxs-lookup"><span data-stu-id="9f6fa-126">The message action for the composite operation is “CompositeOperation.”</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6fa-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f6fa-127">See Also</span></span>  
 [<span data-ttu-id="9f6fa-128">訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="9f6fa-128">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)