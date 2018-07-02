---
title: 資料表和檢視表包含 Oracle 資料庫中的 LOB 資料的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data type
- binary file
- UpdateLOB
- ReadLOB
- LOB data types
- NCLOB
- large object
- binary large object
- CLOB
- national character large object
- BFILE
- BLOB
- character large object
ms.assetid: 25afd8c7-8ca3-4855-a231-2bec28c9a5cb
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a35be7008c47e46ca65962d113c4604c1cfad42b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984295"
---
# <a name="operations-on-tables-and-views-that-contain-lob-data-in-oracle-database"></a><span data-ttu-id="ee4bb-102">資料表和檢視表包含 Oracle 資料庫中的 LOB 資料的作業</span><span class="sxs-lookup"><span data-stu-id="ee4bb-102">Operations on tables and views that contain LOB data in Oracle Database</span></span>
<span data-ttu-id="ee4bb-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]提供 Oracle 的大型物件 (LOB) 資料類型的支援：</span><span class="sxs-lookup"><span data-stu-id="ee4bb-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] provides support for the Oracle large object (LOB) data types:</span></span>  
  
- <span data-ttu-id="ee4bb-104">二進位大型物件 (BLOB)</span><span class="sxs-lookup"><span data-stu-id="ee4bb-104">Binary large object (BLOB)</span></span>  
  
- <span data-ttu-id="ee4bb-105">字元大型物件 (CLOB)</span><span class="sxs-lookup"><span data-stu-id="ee4bb-105">Character large object (CLOB)</span></span>  
  
- <span data-ttu-id="ee4bb-106">國家字元大型物件 (NCLOB)</span><span class="sxs-lookup"><span data-stu-id="ee4bb-106">National character large object (NCLOB)</span></span>  
  
- <span data-ttu-id="ee4bb-107">二進位檔案 (BFILE)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-107">Binary file (BFILE).</span></span> <span data-ttu-id="ee4bb-108">如需詳細資訊，請參閱 <<c0> [ 資料表包含 BFILE 資料類型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-108">For more information, see [Operations on Tables that contains BFILE Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).</span></span>  
  
  <span data-ttu-id="ee4bb-109">在 Oracle 資料庫時，LOB 資料類型用來儲存大量資料 (最多 4 GB)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-109">On the Oracle database, LOB data types are used to store large amounts of data (up to 4 GB).</span></span> <span data-ttu-id="ee4bb-110">LOB 類型支援輸入和輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-110">LOB types support both input and output streaming.</span></span>  
  
  <span data-ttu-id="ee4bb-111">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現資料表和包含 LOB 資料行的檢視執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ee4bb-111">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces the following operations for tables and views that contain LOB columns:</span></span>  
  
- <span data-ttu-id="ee4bb-112">**ReadLOB**。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-112">**ReadLOB**.</span></span> <span data-ttu-id="ee4bb-113">ReadLOB 作業會顯示資料表和檢視表包含 BLOB、 CLOB、 NCLOB、 和 BFILE 資料行。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-113">The ReadLOB operation is surfaced for tables and views that contain BLOB, CLOB, NCLOB, and BFILE columns.</span></span> <span data-ttu-id="ee4bb-114">藉由使用 ReadLOB 作業，配接器用戶端可以做為資料流讀取的 LOB 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-114">By using the ReadLOB operation, adapter clients can read values in a LOB column as a data stream.</span></span> <span data-ttu-id="ee4bb-115">這項作業接受 LOB 資料類型資料行名稱和篩選條件字串，做為參數。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-115">This operation takes the LOB data type column name and a filter string as parameters.</span></span> <span data-ttu-id="ee4bb-116">配接器用戶端必須確定篩選條件字串擷取一個相符的資料列。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-116">Adapter clients must ensure that the filter string fetches exactly one matching row.</span></span> <span data-ttu-id="ee4bb-117">如果有多個相符的資料列，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]只會傳回第一個 （符合） 的資料列的 LOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-117">If there is more than one matching row, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] only returns the LOB column for the first (matching) row.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="ee4bb-118">ReadLOB 作業被設計來支援 WCF 服務模型中的 LOB 資料的輸入資料流。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-118">The ReadLOB operation is designed to support input streaming of LOB data in the WCF service model.</span></span> <span data-ttu-id="ee4bb-119">您應該使用資料表的選取作業來讀取 WCF 通道模型中的 LOB 資料或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-119">You should use a table Select operation to read LOB data from a WCF Channel Model or [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span> <span data-ttu-id="ee4bb-120">如需串流的詳細資訊，請參閱 < [Oracle 資料庫中的 LOB 資料類型的資料流支援](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-120">For more information about streaming, see [Streaming Support for LOB Data Types in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md).</span></span>  
  
- <span data-ttu-id="ee4bb-121">**UpdateLOB**。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-121">**UpdateLOB**.</span></span> <span data-ttu-id="ee4bb-122">UpdateLOB 作業會顯示資料表和檢視表包含 BLOB、 CLOB、 和 NCLOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-122">The UpdateLOB operation is surfaced for tables and views that contain BLOB, CLOB, and NCLOB columns.</span></span> <span data-ttu-id="ee4bb-123">藉由使用 UpdateLOB 作業，配接器用戶端可以更新 LOB 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-123">By using the UpdateLOB operation, adapter clients can update values in a LOB column.</span></span> <span data-ttu-id="ee4bb-124">此作業需要的 LOB 資料類型資料行名稱，篩選條件字串，並 base64binary 編碼資料做為參數。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-124">This operation takes the LOB data type column name, a filter string, and base64binary encoded data as parameters.</span></span> <span data-ttu-id="ee4bb-125">配接器用戶端必須確定篩選條件字串擷取一個相符的資料列;否則[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]XmlReaderParsingException 會擲回。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-125">Adapter clients must ensure that the filter string fetches exactly one matching row; otherwise the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] throws an XmlReaderParsingException.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="ee4bb-126">UpdateLOB 作業：</span><span class="sxs-lookup"><span data-stu-id="ee4bb-126">The UpdateLOB operation:</span></span>  
  > 
  > - <span data-ttu-id="ee4bb-127">不支援 BFILE 資料型別。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-127">Is not supported for the BFILE data type.</span></span> <span data-ttu-id="ee4bb-128">配接器用戶端，或者可以使用更新作業。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-128">Adapter clients can alternatively use the Update operation.</span></span> <span data-ttu-id="ee4bb-129">如需詳細資訊，請參閱 <<c0> [ 資料表包含 BFILE 資料類型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-129">For more information, see [Operations on Tables that contains BFILE Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).</span></span>  
  >   -   <span data-ttu-id="ee4bb-130">必須被執行交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-130">Must be performed as part of a transaction.</span></span> <span data-ttu-id="ee4bb-131">為了確保功效， **UseAmbientTransaction**繫結屬性必須設定為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-131">To ensure this, the **UseAmbientTransaction** binding property must be set to **True**.</span></span> <span data-ttu-id="ee4bb-132">如需**UseAmbientTransaction**繫結屬性，請參閱[Oracle 資料庫設定的繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-132">For information about the **UseAmbientTransaction** binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee4bb-133">ReadLOB 和 UpdateLOB 對單一資料表資料列中的單一 LOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-133">ReadLOB and UpdateLOB operate on a single LOB column in a single table row.</span></span> <span data-ttu-id="ee4bb-134">若要在多個資料列的 LOB 資料行上，或在單一資料列中的多個 LOB 資料行上操作，您必須叫用 ReadLOB 或 UpdateLOB 每個目標資料行中每個目標資料列。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-134">To operate on LOB columns in multiple rows or on multiple LOB columns within a single row, you must invoke ReadLOB or UpdateLOB for each target column within each target row.</span></span>  
  
 <span data-ttu-id="ee4bb-135">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="ee4bb-135">For more information about:</span></span>  
  
- <span data-ttu-id="ee4bb-136">叫用 Oracle 資料庫資料表使用 UpdateLOB 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 大型物件資料類型使用 BizTalk Server 所使用的資料表上執行的作業](https://msdn.microsoft.com/library/cc185405(v=bts.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-136">Invoking the UpdateLOB operation on an Oracle database table using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Performing Operations on Tables with Large Object Types Data by Using BizTalk Server](https://msdn.microsoft.com/library/cc185405(v=bts.10).aspx).</span></span> <span data-ttu-id="ee4bb-137">(您應該使用資料表的選取作業來讀取在 LOB 資料型別[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。)</span><span class="sxs-lookup"><span data-stu-id="ee4bb-137">(You should use a table Select operation to read LOB data types in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].)</span></span>  
  
- <span data-ttu-id="ee4bb-138">叫用 ReadLOB 和 UpdateLOB 使用 WCF 服務模型的 Oracle 資料庫資料表上的作業，請參閱[與使用 WCF 服務模型的大型物件類型的資料表上執行的作業](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-138">Invoking ReadLOB and UpdateLOB operations on an Oracle database table using WCF service model, see [Run Operations on Tables with Large Object Types by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md).</span></span>  
  
- <span data-ttu-id="ee4bb-139">訊息結構和執行 ReadLOB 和 UpdateLOB 作業的 SOAP 動作，請參閱[特殊 LOB 作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)。</span><span class="sxs-lookup"><span data-stu-id="ee4bb-139">Message structure and SOAP actions for performing ReadLOB and UpdateLOB operations, see [Message Schemas for Special LOB Operations](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4bb-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee4bb-140">See Also</span></span>  
 <span data-ttu-id="ee4bb-141">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="ee4bb-141">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)</span></span>