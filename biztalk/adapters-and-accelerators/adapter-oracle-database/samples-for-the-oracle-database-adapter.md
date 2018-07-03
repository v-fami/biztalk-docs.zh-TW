---
title: Oracle 資料庫配接器範例 |Microsoft Docs
description: 可以使用 BizTalk Server、 WCF 服務模型，與 WCF 通道模型的 oracle DB WCF 配接器範例
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 744f19ce-3126-4745-92dd-4f68443180fc
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ac7a1c2cda4fd66e450d23022787f5e7d0e0324
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006447"
---
# <a name="samples-for-the-oracle-database-adapter"></a><span data-ttu-id="d8c3c-103">適用於 Oracle 資料庫配接器範例</span><span class="sxs-lookup"><span data-stu-id="d8c3c-103">Samples for the Oracle Database adapter</span></span>
<span data-ttu-id="d8c3c-104">範例[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]會分類為：</span><span class="sxs-lookup"><span data-stu-id="d8c3c-104">Samples for [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] are categorized into:</span></span>  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d8c3c-105"> 範例</span><span class="sxs-lookup"><span data-stu-id="d8c3c-105"> samples</span></span>  
  
- <span data-ttu-id="d8c3c-106">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="d8c3c-106">WCF service model samples</span></span>  
  
- <span data-ttu-id="d8c3c-107">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="d8c3c-107">WCF channel model samples</span></span>  

  
<span data-ttu-id="d8c3c-108">這些範例位於[BizTalk Adapter Pack 2010: Oracle 資料庫配接器範例](https://www.microsoft.com/download/details.aspx?id=4675)。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-108">The samples are available at [BizTalk Adapter Pack 2010: Oracle Database adapter samples](https://www.microsoft.com/download/details.aspx?id=4675).</span></span> <span data-ttu-id="d8c3c-109">建立資料表和封裝範例中使用的 SQL 指令碼會包含項目。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-109">The SQL scripts for creating the tables and packages used in the samples are included.</span></span> 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
<span data-ttu-id="d8c3c-110">下列清單描述的範例。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-110">The following list describes the samples.</span></span>
  
## <a name="biztalk-server-samples"></a><span data-ttu-id="d8c3c-111">BizTalk Server 範例</span><span class="sxs-lookup"><span data-stu-id="d8c3c-111">BizTalk Server samples</span></span>
  
| <span data-ttu-id="d8c3c-112">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="d8c3c-112">Sample Directory Name</span></span> |                                                                                         <span data-ttu-id="d8c3c-113">描述</span><span class="sxs-lookup"><span data-stu-id="d8c3c-113">Description</span></span>                                                                                         |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   <span data-ttu-id="d8c3c-114">Func_RecordTypes</span><span class="sxs-lookup"><span data-stu-id="d8c3c-114">Func_RecordTypes</span></span>    |      <span data-ttu-id="d8c3c-115">示範如何使用記錄型別參數和傳回值，函式和程序使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-115">Demonstrates how to use RECORD type parameters and return values in functions and procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>      |
|    <span data-ttu-id="d8c3c-116">Func_RefCursor</span><span class="sxs-lookup"><span data-stu-id="d8c3c-116">Func_RefCursor</span></span>     |               <span data-ttu-id="d8c3c-117">示範如何使用函式和程序使用中的 REF CURSOR 參數[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-117">Demonstrates how to use REF CURSOR parameters in functions and procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>                |
|    <span data-ttu-id="d8c3c-118">InvokeFunction</span><span class="sxs-lookup"><span data-stu-id="d8c3c-118">InvokeFunction</span></span>     |                        <span data-ttu-id="d8c3c-119">示範如何叫用 Oracle 資料庫使用中的函式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-119">Demonstrates how to invoke a function in Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>                        |
| <span data-ttu-id="d8c3c-120">InvokeOverloadedProc</span><span class="sxs-lookup"><span data-stu-id="d8c3c-120">InvokeOverloadedProc</span></span>  |         <span data-ttu-id="d8c3c-121">示範如何使用多載函式和 Oracle database 中的程序叫用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-121">Demonstrates how to invoke with overloaded functions and procedures in Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>         |
|     <span data-ttu-id="d8c3c-122">Operate_BFILE</span><span class="sxs-lookup"><span data-stu-id="d8c3c-122">Operate_BFILE</span></span>     |                    <span data-ttu-id="d8c3c-123">示範如何使用 Oracle 程序中使用 Oracle BFILE 類型[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-123">Demonstrates how to use Oracle BFILE types in Oracle procedures using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>                     |
|      <span data-ttu-id="d8c3c-124">Operate_LOB</span><span class="sxs-lookup"><span data-stu-id="d8c3c-124">Operate_LOB</span></span>      |       <span data-ttu-id="d8c3c-125">示範如何執行 LOB 資料類型使用的資料表上 ReadLOB 和 UpdateLOB 作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-125">Demonstrates how to perform ReadLOB and UpdateLOB operations on tables with LOB data types using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>       |
|     <span data-ttu-id="d8c3c-126">PollingQuery</span><span class="sxs-lookup"><span data-stu-id="d8c3c-126">PollingQuery</span></span>      |                 <span data-ttu-id="d8c3c-127">示範如何設定在有輪詢查詢，並接收結果使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-127">Demonstrates how to configure a polling query and receive the results using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>                  |
|    <span data-ttu-id="d8c3c-128">SelectAccTable</span><span class="sxs-lookup"><span data-stu-id="d8c3c-128">SelectAccTable</span></span>     |                 <span data-ttu-id="d8c3c-129">示範如何執行 select 查詢 Oracle 資料庫資料表使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-129">Demonstrates how to perform a select query on an Oracle database table using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>                 |
|        <span data-ttu-id="d8c3c-130">SqlExec</span><span class="sxs-lookup"><span data-stu-id="d8c3c-130">SqlExec</span></span>        | <span data-ttu-id="d8c3c-131">示範如何執行參數化的查詢使用 Oracle 資料庫使用 SQLEXECUTE 作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-131">Demonstrates how to perform parameterized queries using the SQLEXECUTE operation on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> |
  
## <a name="wcf-service-model-samples"></a><span data-ttu-id="d8c3c-132">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="d8c3c-132">WCF service model samples</span></span>  
  
|<span data-ttu-id="d8c3c-133">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="d8c3c-133">Sample Directory Name</span></span>|<span data-ttu-id="d8c3c-134">描述</span><span class="sxs-lookup"><span data-stu-id="d8c3c-134">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="d8c3c-135">OracleBfileTypeSM</span><span class="sxs-lookup"><span data-stu-id="d8c3c-135">OracleBfileTypeSM</span></span>|<span data-ttu-id="d8c3c-136">示範如何在 Oracle 程序中可見的 Oracle 資料表和做為參數的基本 SQL 作業中使用 Oracle BFILE 類型。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-136">Demonstrates how to use Oracle BFILE types in basic SQL operations surfaced for Oracle tables and as parameters to Oracle procedures.</span></span>|  
|<span data-ttu-id="d8c3c-137">OracleOverloadsSM</span><span class="sxs-lookup"><span data-stu-id="d8c3c-137">OracleOverloadsSM</span></span>|<span data-ttu-id="d8c3c-138">示範如何叫用多載函式，並在封裝中的程序。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-138">Demonstrates how to invoke overloaded functions and procedures in a package.</span></span>|  
|<span data-ttu-id="d8c3c-139">OraclePollingSM</span><span class="sxs-lookup"><span data-stu-id="d8c3c-139">OraclePollingSM</span></span>|<span data-ttu-id="d8c3c-140">示範如何設定在有輪詢查詢，並接收結果。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-140">Demonstrates how to configure a polling query and receive the results.</span></span>|  
|<span data-ttu-id="d8c3c-141">OracleRecordTypesSM</span><span class="sxs-lookup"><span data-stu-id="d8c3c-141">OracleRecordTypesSM</span></span>|<span data-ttu-id="d8c3c-142">示範如何使用記錄型別參數和傳回值，函式和程序中。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-142">Demonstrates how to use RECORD type parameters and return values in functions and procedures.</span></span>|  
|<span data-ttu-id="d8c3c-143">OracleRefCursorsSM</span><span class="sxs-lookup"><span data-stu-id="d8c3c-143">OracleRefCursorsSM</span></span>|<span data-ttu-id="d8c3c-144">示範如何使用函式和程序中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="d8c3c-144">Demonstrates how to use REF CURSOR parameters in functions and procedures</span></span>|  
|<span data-ttu-id="d8c3c-145">OracleTransactedDmlSM</span><span class="sxs-lookup"><span data-stu-id="d8c3c-145">OracleTransactedDmlSM</span></span>|<span data-ttu-id="d8c3c-146">示範如何在使用 WCF 服務模型的交易中執行的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-146">Demonstrates how to perform operations on the Oracle database in a transaction using the WCF service model.</span></span>|  
  
## <a name="wcf-channel-model-samples"></a><span data-ttu-id="d8c3c-147">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="d8c3c-147">WCF channel model samples</span></span>  
  
|<span data-ttu-id="d8c3c-148">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="d8c3c-148">Sample Directory Name</span></span>|<span data-ttu-id="d8c3c-149">描述</span><span class="sxs-lookup"><span data-stu-id="d8c3c-149">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="d8c3c-150">OraclePollingCM</span><span class="sxs-lookup"><span data-stu-id="d8c3c-150">OraclePollingCM</span></span>|<span data-ttu-id="d8c3c-151">示範如何設定在有輪詢查詢，並接收結果。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-151">Demonstrates how to configure a polling query and receive the results.</span></span>|  
|<span data-ttu-id="d8c3c-152">OracleStreamingDemo</span><span class="sxs-lookup"><span data-stu-id="d8c3c-152">OracleStreamingDemo</span></span>|<span data-ttu-id="d8c3c-153">示範如何執行端對端使用 UpdateLOB 和資料表的 Select 作業的 LOB 資料的資料流</span><span class="sxs-lookup"><span data-stu-id="d8c3c-153">Demonstrates how to perform end-to-end streaming of LOB data using the UpdateLOB and table Select operations</span></span>|  
|<span data-ttu-id="d8c3c-154">OracleTransactedDmlCM</span><span class="sxs-lookup"><span data-stu-id="d8c3c-154">OracleTransactedDmlCM</span></span>|<span data-ttu-id="d8c3c-155">示範如何在使用 WCF 通道模型的交易中執行的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="d8c3c-155">Demonstrates how to perform operations on the Oracle database in a transaction using the WCF channel model.</span></span>|  
  

## <a name="see-also"></a><span data-ttu-id="d8c3c-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8c3c-156">See Also</span></span>  
[<span data-ttu-id="d8c3c-157">開發您的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="d8c3c-157">Develop your Oracle Database applications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)