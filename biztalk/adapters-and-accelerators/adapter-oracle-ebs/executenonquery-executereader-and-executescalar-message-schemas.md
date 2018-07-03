---
title: ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar Operations1 如訊息結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8aa5fdb2-1e7f-4a34-a1e5-c16d8fb477d5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7078fed7a007eca4dfb3eb5608eb6e688bb74a45
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011967"
---
# <a name="message-schemas-for-the-executenonquery-executereader-and-executescalar-operations"></a><span data-ttu-id="44ce5-102">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="44ce5-102">Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>
<span data-ttu-id="44ce5-103">[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]公開執行 Oracle E-business Suite 中的 任何任意的 SQL 陳述式或 PL/SQL 封鎖根層級的 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 輸出作業。</span><span class="sxs-lookup"><span data-stu-id="44ce5-103">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes the ExecuteNonQuery, ExecuteReader, and ExecuteScalar outbound operations at the root level to execute any arbitrary SQL statements or PL/SQL blocks in Oracle E-Business Suite.</span></span>  
  
 <span data-ttu-id="44ce5-104">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="44ce5-104">For more information about:</span></span>  
  
- <span data-ttu-id="44ce5-105">這些作業，請參閱[支援 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="44ce5-105">These operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span></span>  
  
- <span data-ttu-id="44ce5-106">執行這些作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 < [ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="44ce5-106">Performing these operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).</span></span>  
  
## <a name="message-structure-for-the-executenonquery-executereader-and-executescalar-operations"></a><span data-ttu-id="44ce5-107">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="44ce5-107">Message Structure for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>  
 <span data-ttu-id="44ce5-108">在這些作業訊息會遵循要求-回應訊息交換模式，以及下表顯示這些要求和回應訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="44ce5-108">The messages in these operations follow a request-response message exchange pattern, and the following table shows the structure of these request and response messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44ce5-109">表格後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="44ce5-109">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="44ce5-110">作業</span><span class="sxs-lookup"><span data-stu-id="44ce5-110">Operation</span></span>|<span data-ttu-id="44ce5-111">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="44ce5-111">XML Message</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44ce5-112">ExecuteNonQuery 要求</span><span class="sxs-lookup"><span data-stu-id="44ce5-112">ExecuteNonQuery Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQuery xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query>   <OutputRefCursorNames>     <string>[stringvalue1]</string>     <string>[stringvalue2]</string>     …   </OutputRefCursorNames> </ExecuteNonQuery>`|  
|<span data-ttu-id="44ce5-113">ExecuteNonQuery 回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-113">ExecuteNonQuery Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult>   <OutputRefCursors>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </OutputRefCursors> </ExecuteNonQueryResponse>`|  
|<span data-ttu-id="44ce5-114">ExecuteReader 要求</span><span class="sxs-lookup"><span data-stu-id="44ce5-114">ExecuteReader Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReader xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteReader>`|  
|<span data-ttu-id="44ce5-115">ExecuteReader 回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-115">ExecuteReader Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteReaderResult>     <Any>[value]</Any>     <Any>[value]</Any>       …   </ExecuteReaderResult> </ExecuteReaderResponse>`|  
|<span data-ttu-id="44ce5-116">ExecuteScalar 要求</span><span class="sxs-lookup"><span data-stu-id="44ce5-116">ExecuteScalar Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalar xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteScalar>`|  
|<span data-ttu-id="44ce5-117">ExecuteScalar 回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-117">ExecuteScalar Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|  
  
 <span data-ttu-id="44ce5-118">實體描述：</span><span class="sxs-lookup"><span data-stu-id="44ce5-118">Entity descriptions:</span></span>  
  
 <span data-ttu-id="44ce5-119">[PL/SQL 區塊] = 整個 PL/SQL 區塊執行。</span><span class="sxs-lookup"><span data-stu-id="44ce5-119">[PL/SQL block] = The entire PL/SQL block to be executed.</span></span>  
  
 <span data-ttu-id="44ce5-120">[stringvalue1] = 的字串陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="44ce5-120">[stringvalue1] = A value in the array of strings.</span></span>  
  
## <a name="message-action-for-the-executenonquery-executereader-and-executescalar-operations"></a><span data-ttu-id="44ce5-121">ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="44ce5-121">Message Action for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>  
 <span data-ttu-id="44ce5-122">下表顯示使用 ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="44ce5-122">The following table shows the message actions that are used by the ExecuteNonQuery, ExecuteReader, and ExecuteScalar operations.</span></span>  
  
|<span data-ttu-id="44ce5-123">作業</span><span class="sxs-lookup"><span data-stu-id="44ce5-123">Operation</span></span>|<span data-ttu-id="44ce5-124">動作</span><span class="sxs-lookup"><span data-stu-id="44ce5-124">Action</span></span>|  
|---------------|------------|  
|<span data-ttu-id="44ce5-125">ExecuteNonQuery 要求</span><span class="sxs-lookup"><span data-stu-id="44ce5-125">ExecuteNonQuery Request</span></span>|<span data-ttu-id="44ce5-126">GenericOp/ExecuteNonQuery</span><span class="sxs-lookup"><span data-stu-id="44ce5-126">GenericOp/ExecuteNonQuery</span></span>|  
|<span data-ttu-id="44ce5-127">ExecuteNonQuery 回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-127">ExecuteNonQuery Response</span></span>|<span data-ttu-id="44ce5-128">GenericOp/ExecuteNonQuery/回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-128">GenericOp/ExecuteNonQuery/response</span></span>|  
|<span data-ttu-id="44ce5-129">ExecuteReader 要求</span><span class="sxs-lookup"><span data-stu-id="44ce5-129">ExecuteReader Request</span></span>|<span data-ttu-id="44ce5-130">GenericOp/ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="44ce5-130">GenericOp/ExecuteReader</span></span>|  
|<span data-ttu-id="44ce5-131">ExecuteReader 回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-131">ExecuteReader Response</span></span>|<span data-ttu-id="44ce5-132">GenericOp/ExecuteReader/回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-132">GenericOp/ExecuteReader/response</span></span>|  
|<span data-ttu-id="44ce5-133">ExecuteScalar 要求</span><span class="sxs-lookup"><span data-stu-id="44ce5-133">ExecuteScalar Request</span></span>|<span data-ttu-id="44ce5-134">GenericOp/ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="44ce5-134">GenericOp/ExecuteScalar</span></span>|  
|<span data-ttu-id="44ce5-135">ExecuteScalar 回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-135">ExecuteScalar Response</span></span>|<span data-ttu-id="44ce5-136">GenericOp/ExecuteScalar/回應</span><span class="sxs-lookup"><span data-stu-id="44ce5-136">GenericOp/ExecuteScalar/response</span></span>|