---
title: "訊息結構描述的特殊 LOB Operations1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2e418a6-8bc7-42d9-9672-a9c149f32778
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ecc0554162b1cf8298b441c0d129bee83540011
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-special-lob-operations"></a><span data-ttu-id="5a39c-102">特殊 LOB 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="5a39c-102">Message Schemas for Special LOB Operations</span></span>
<span data-ttu-id="5a39c-103">Read_\<LOBColName > 和 Update_\<LOBColName > 作業便會顯示資料表和檢視表包含 LOB 資料行，其中\<LOBColName > 是資料表或檢視表中的 LOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="5a39c-103">The Read_\<LOBColName> and Update_\<LOBColName> operations are surfaced for tables and views that contain LOB columns, where \<LOBColName> is the LOB column in the table or view.</span></span> <span data-ttu-id="5a39c-104">這些作業可讓您讀取或寫入 base64Binary 編碼資料的資料流的形式的 LOB 資料。</span><span class="sxs-lookup"><span data-stu-id="5a39c-104">These operations enable you to read or write the LOB data as a stream of base64Binary-encoded data.</span></span> <span data-ttu-id="5a39c-105">它們是在單一資料列的 LOB 資料的單一資料行上運作。</span><span class="sxs-lookup"><span data-stu-id="5a39c-105">They operate on a single column of LOB data in a single row.</span></span>  
  
 <span data-ttu-id="5a39c-106">如需 Read_ 的概觀\<LOBColName > 和 Update_\<LOBColName > 作業和 Oracle LOB 資料類型的支援，請參閱[介面資料表、 介面檢視、 資料表和檢視表，包含 LOB 作業資料](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5a39c-106">For an overview of the Read_\<LOBColName> and Update_\<LOBColName> operations and of the Oracle LOB data types supported, see [Operations on Interface Tables, Interface Views, Tables, and Views That Contain LOB Data](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).</span></span>  
  
## <a name="message-structure-of-lob-data-type-operations"></a><span data-ttu-id="5a39c-107">LOB 資料型別作業的訊息結構</span><span class="sxs-lookup"><span data-stu-id="5a39c-107">Message Structure of LOB Data-Type Operations</span></span>  
 <span data-ttu-id="5a39c-108">下表顯示的要求和回應訊息結構 Read_\<LOBColName > 和 Update_\<LOBColName > 作業。</span><span class="sxs-lookup"><span data-stu-id="5a39c-108">The following table shows the structure of the request and response messages for the Read_\<LOBColName> and Update_\<LOBColName> operations.</span></span> <span data-ttu-id="5a39c-109">作業的目標資料表中的訊息動作指定，而且也會出現在 目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="5a39c-109">The target table for the operation is specified in the message action and also appears in the target namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a39c-110">在資料表之後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="5a39c-110">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="5a39c-111">作業</span><span class="sxs-lookup"><span data-stu-id="5a39c-111">Operation</span></span>|<span data-ttu-id="5a39c-112">XML 訊息</span><span class="sxs-lookup"><span data-stu-id="5a39c-112">XML Message</span></span>|<span data-ttu-id="5a39c-113">Description</span><span class="sxs-lookup"><span data-stu-id="5a39c-113">Description</span></span>|  
|---------------|-----------------|-----------------|  
|<span data-ttu-id="5a39c-114">Read_\<LOBColName ></span><span class="sxs-lookup"><span data-stu-id="5a39c-114">Read_\<LOBColName></span></span>|`<Read_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</FILTER></Read_[LOBColName]>`|<span data-ttu-id="5a39c-115">LOB 資料在資料列符合 where 子句篩選條件的項目中指定會傳回。</span><span class="sxs-lookup"><span data-stu-id="5a39c-115">The LOB data in the row that matches the where clause specified in the FILTER element is returned.</span></span> <span data-ttu-id="5a39c-116">Where 子句應符合的單一資料列。</span><span class="sxs-lookup"><span data-stu-id="5a39c-116">The where clause should match only a single row.</span></span> <span data-ttu-id="5a39c-117">如果有一個以上相符的資料列，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5a39c-117">If there is more than one matching row, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] will throw an exception.</span></span>|  
|<span data-ttu-id="5a39c-118">Read_\<LOBColName > 回應</span><span class="sxs-lookup"><span data-stu-id="5a39c-118">Read_\<LOBColName> Response</span></span>|`<Read_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <Read_[LOBColName]Result>    [LOB_DATA]  </Read_[LOBColName]Result></Read_[LOBColName]Response>`|<span data-ttu-id="5a39c-119">LOB 資料是 base64Binary 編碼資料的資料流的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="5a39c-119">The LOB data is returned as a stream of base64Binary encoded data.</span></span>|  
|<span data-ttu-id="5a39c-120">Update_\<LOBColName ></span><span class="sxs-lookup"><span data-stu-id="5a39c-120">Update_\<LOBColName></span></span>|`<Update_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</LOB_COLUMN>  <DATA>[Value]</DATA></Update_[LOBColName]>`|<span data-ttu-id="5a39c-121">LOB 資料中的資料列符合 where 子句篩選條件的項目中指定更新中的資料\<資料 > 項目。</span><span class="sxs-lookup"><span data-stu-id="5a39c-121">The LOB data in the row that matches the where clause specified in the FILTER element is updated with the data in the \<DATA> element.</span></span> <span data-ttu-id="5a39c-122">Where 子句應符合的單一資料列。</span><span class="sxs-lookup"><span data-stu-id="5a39c-122">The where clause should match only a single row.</span></span> <span data-ttu-id="5a39c-123">如果有一個以上相符的資料列，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5a39c-123">If there is more than one matching row, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] throws an exception.</span></span><br /><br /> <span data-ttu-id="5a39c-124">**請注意**更新 BLOB 的資料行時\<資料 > 項目必須永遠包含 base64 編碼值。</span><span class="sxs-lookup"><span data-stu-id="5a39c-124">**Note** While updating BLOB columns, the \<DATA> element must always contain a base64 encoded value.</span></span> <span data-ttu-id="5a39c-125">CLOB 和 NCLOB，\<資料 > 項目可以有字串值。</span><span class="sxs-lookup"><span data-stu-id="5a39c-125">For CLOB and NCLOB, the \<DATA> element can have string values.</span></span>|  
|<span data-ttu-id="5a39c-126">Update_\<LOBColName > 回應</span><span class="sxs-lookup"><span data-stu-id="5a39c-126">Update_\<LOBColName> Response</span></span>|`<Update_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]"></Update_[LOBColName]Response>`|<span data-ttu-id="5a39c-127">會傳回空白回應。</span><span class="sxs-lookup"><span data-stu-id="5a39c-127">An empty response is returned.</span></span>|  
  
 <span data-ttu-id="5a39c-128">實體描述：</span><span class="sxs-lookup"><span data-stu-id="5a39c-128">Entity descriptions:</span></span>  
  
 <span data-ttu-id="5a39c-129">[版本] = 訊息版本字串。例如，"http://schemas.microsoft.com/OracleEBS/2008/05。 」</span><span class="sxs-lookup"><span data-stu-id="5a39c-129">[VERSION] = The message version string; for example, "http://schemas.microsoft.com/OracleEBS/2008/05".</span></span>  
  
 <span data-ttu-id="5a39c-130">[SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="5a39c-130">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="5a39c-131">[TABLE_NAME] = 資料表，其中包含目標的 LOB 資料行;例如，客戶。</span><span class="sxs-lookup"><span data-stu-id="5a39c-131">[TABLE_NAME] = The table that contains the targeted LOB column; for example, CUSTOMER.</span></span>  
  
 <span data-ttu-id="5a39c-132">[LOBCol_Name] = 的 LOB 資料行名稱例如，相片。</span><span class="sxs-lookup"><span data-stu-id="5a39c-132">[LOBCol_Name] = The name of a LOB column; for example, Photo.</span></span>  
  
 <span data-ttu-id="5a39c-133">[WHERE_clause] = Oracle 資料庫的 SELECT 陳述式 WHERE 子句，比對單一資料列。例如，識別碼 = 1。</span><span class="sxs-lookup"><span data-stu-id="5a39c-133">[WHERE_clause] = An Oracle database SELECT statement WHERE clause that matches a single row; for example, ID = 1.</span></span>  
  
 <span data-ttu-id="5a39c-134">[LOB_DATA] = base64Binary 類型中的 LOB 資料行資料。</span><span class="sxs-lookup"><span data-stu-id="5a39c-134">[LOB_DATA] = The LOB column data in base64Binary type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a39c-135">Read_ 的訊息結構\<LOBColName > 和 Update_\<LOBColName > 檢視表上的作業的相同資料表上會有不同之處在於此作業的命名空間指定的檢視，而不是資料表： `<ReadLOB xmlns ="[VERSION]/Views/[SCHEMA]/[VIEW_NAME]">`。</span><span class="sxs-lookup"><span data-stu-id="5a39c-135">The message structure for the Read_\<LOBColName> and Update_\<LOBColName> operations on views is the same as that on tables except that the namespace for the operation specifies a view rather than a table: `<ReadLOB xmlns ="[VERSION]/Views/[SCHEMA]/[VIEW_NAME]">`.</span></span>  
  
## <a name="message-actions-for-lob-data-type-operations"></a><span data-ttu-id="5a39c-136">LOB 資料型別作業的訊息動作</span><span class="sxs-lookup"><span data-stu-id="5a39c-136">Message Actions for LOB Data-Type Operations</span></span>  
 <span data-ttu-id="5a39c-137">下表顯示所使用的訊息動作[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]如 Read_\<LOBColName > 和 Update_\<LOBColName > 資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="5a39c-137">The following table shows the message actions that are used by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] for the Read_\<LOBColName> and Update_\<LOBColName> operations on tables.</span></span> <span data-ttu-id="5a39c-138">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用資料表名稱和訊息動作中指定的 LOB 資料行名稱來判斷目標資料表和 LOB 資料行的作業。</span><span class="sxs-lookup"><span data-stu-id="5a39c-138">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the table name and the LOB column name specified in the message action to determine the target table and LOB column for the operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a39c-139">在資料表之後，請參閱實體描述。</span><span class="sxs-lookup"><span data-stu-id="5a39c-139">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="5a39c-140">作業</span><span class="sxs-lookup"><span data-stu-id="5a39c-140">Operation</span></span>|<span data-ttu-id="5a39c-141">動作</span><span class="sxs-lookup"><span data-stu-id="5a39c-141">Action</span></span>|<span data-ttu-id="5a39c-142">範例</span><span class="sxs-lookup"><span data-stu-id="5a39c-142">Example</span></span>|  
|---------------|------------|-------------|  
|<span data-ttu-id="5a39c-143">Read_\<LOBColName ></span><span class="sxs-lookup"><span data-stu-id="5a39c-143">Read_\<LOBColName></span></span>|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo`|  
|<span data-ttu-id="5a39c-144">Read_\<LOBColName > 回應</span><span class="sxs-lookup"><span data-stu-id="5a39c-144">Read_\<LOBColName> Response</span></span>|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo/response`|  
|<span data-ttu-id="5a39c-145">Update_\<LOBColName ></span><span class="sxs-lookup"><span data-stu-id="5a39c-145">Update_\<LOBColName></span></span>|<span data-ttu-id="5a39c-146">**Blob**:</span><span class="sxs-lookup"><span data-stu-id="5a39c-146">**For BLOB**:</span></span><br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`<br /><br /> <span data-ttu-id="5a39c-147">**CLOB 和 NCLOB**:</span><span class="sxs-lookup"><span data-stu-id="5a39c-147">**For CLOB and NCLOB**:</span></span><br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|<span data-ttu-id="5a39c-148">**Blob**:</span><span class="sxs-lookup"><span data-stu-id="5a39c-148">**For BLOB**:</span></span><br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/`<br /><br /> <span data-ttu-id="5a39c-149">**CLOB 和 NCLOB**:</span><span class="sxs-lookup"><span data-stu-id="5a39c-149">**For CLOB and NCLOB**:</span></span><br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/`|  
|<span data-ttu-id="5a39c-150">Update_\<LOBColName > 回應</span><span class="sxs-lookup"><span data-stu-id="5a39c-150">Update_\<LOBColName> Response</span></span>|<span data-ttu-id="5a39c-151">**Blob**:</span><span class="sxs-lookup"><span data-stu-id="5a39c-151">**For BLOB**:</span></span><br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`<br /><br /> <span data-ttu-id="5a39c-152">**CLOB 和 NCLOB**:</span><span class="sxs-lookup"><span data-stu-id="5a39c-152">**For CLOB and NCLOB**:</span></span><br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|<span data-ttu-id="5a39c-153">**Blob**:</span><span class="sxs-lookup"><span data-stu-id="5a39c-153">**For BLOB**:</span></span><br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/response`<br /><br /> <span data-ttu-id="5a39c-154">**CLOB 和 NCLOB**:</span><span class="sxs-lookup"><span data-stu-id="5a39c-154">**For CLOB and NCLOB**:</span></span><br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/response`|  
  
 <span data-ttu-id="5a39c-155">實體描述：</span><span class="sxs-lookup"><span data-stu-id="5a39c-155">Entity descriptions:</span></span>  
  
 <span data-ttu-id="5a39c-156">[SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。</span><span class="sxs-lookup"><span data-stu-id="5a39c-156">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="5a39c-157">[TABLE_NAME] = 資料表，其中包含目標的 LOB 資料行;例如，客戶。</span><span class="sxs-lookup"><span data-stu-id="5a39c-157">[TABLE_NAME] = The table that contains the targeted LOB column; for example, CUSTOMER.</span></span> <span data-ttu-id="5a39c-158">(SCOTT。CUSTOMER 資料表中會安裝所包含的範例中的 SQL 指令碼）。</span><span class="sxs-lookup"><span data-stu-id="5a39c-158">(The SCOTT.CUSTOMER table is installed by a SQL script included in the samples.)</span></span>  
  
 <span data-ttu-id="5a39c-159">[LOBCol_Name] = 的 LOB 資料行名稱例如，相片。</span><span class="sxs-lookup"><span data-stu-id="5a39c-159">[LOBCol_Name] = The name of a LOB column; for example, Photo.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a39c-160">Read_ 的訊息動作\<LOBColName > 和 Update_\<LOBColName > 檢視上的作業是所使用的資料表，類似，不同之處在於動作的作業指定的檢視，而不是資料表： `Views/ReadLOB/[SCHEMA]/[VIEW_NAME]/[LOBColName]`。</span><span class="sxs-lookup"><span data-stu-id="5a39c-160">The message action for Read_\<LOBColName> and Update_\<LOBColName> operations on views is similar to that used for tables, except that action for the operation specifies a view rather than a table: `Views/ReadLOB/[SCHEMA]/[VIEW_NAME]/[LOBColName]`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a39c-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a39c-161">See Also</span></span>  
 [<span data-ttu-id="5a39c-162">訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="5a39c-162">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)