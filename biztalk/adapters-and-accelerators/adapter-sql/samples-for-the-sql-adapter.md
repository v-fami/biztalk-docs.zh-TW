---
title: "SQL 配接器範例 |Microsoft 文件"
description: "可以使用 BizTalk Server、 WCF 服務模型時，與 WCF 通道模型的 SQL WCF 配接器範例"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2438696-bc51-46df-81ca-00c17a52736e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0729b18dc900800ed39ccae31acfdd37b38b4573
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="samples-for-the-sql-adapter"></a><span data-ttu-id="0910e-103">SQL 配接器範例</span><span class="sxs-lookup"><span data-stu-id="0910e-103">Samples for the SQL adapter</span></span>

<span data-ttu-id="0910e-104">範例如[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]分類成：</span><span class="sxs-lookup"><span data-stu-id="0910e-104">Samples for [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] are categorized into:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0910e-105"> 範例</span><span class="sxs-lookup"><span data-stu-id="0910e-105"> samples</span></span>  
  
-   <span data-ttu-id="0910e-106">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="0910e-106">WCF service model samples</span></span>  
  
-   <span data-ttu-id="0910e-107">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="0910e-107">WCF channel model samples</span></span>  
  
<span data-ttu-id="0910e-108">這些範例位於[BizTalk Adapter Pack 2010: SQL 配接器範例](https://www.microsoft.com/download/details.aspx?id=22455)。</span><span class="sxs-lookup"><span data-stu-id="0910e-108">The samples are available at [BizTalk Adapter Pack 2010: SQL adapter samples](https://www.microsoft.com/download/details.aspx?id=22455).</span></span> <span data-ttu-id="0910e-109">建立之物件的 SQL 指令碼範例中所使用，例如資料庫、 資料表，而包含程序。</span><span class="sxs-lookup"><span data-stu-id="0910e-109">The SQL scripts for creating the objects used in the samples, such as database, tables, and procedures are included.</span></span> 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
<span data-ttu-id="0910e-110">下列清單描述的範例。</span><span class="sxs-lookup"><span data-stu-id="0910e-110">The following list describes the samples.</span></span>
  
## <a name="biztalk-server-samples"></a><span data-ttu-id="0910e-111">BizTalk Server 範例</span><span class="sxs-lookup"><span data-stu-id="0910e-111">BizTalk Server samples</span></span>  
  
|<span data-ttu-id="0910e-112">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="0910e-112">Sample Directory Name</span></span>|<span data-ttu-id="0910e-113">Description</span><span class="sxs-lookup"><span data-stu-id="0910e-113">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="0910e-114">ExecuteStoredProcedure</span><span class="sxs-lookup"><span data-stu-id="0910e-114">ExecuteStoredProcedure</span></span>|<span data-ttu-id="0910e-115">示範如何叫用使用配接器與 SQL Server 資料庫中的預存程序[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0910e-115">Demonstrates how to invoke a stored procedure in SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] .</span></span>|  
|<span data-ttu-id="0910e-116">SelectTable</span><span class="sxs-lookup"><span data-stu-id="0910e-116">SelectTable</span></span>|<span data-ttu-id="0910e-117">示範如何執行 SQL Server 資料庫資料表使用的介面卡上的選取作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0910e-117">Demonstrates how to perform a Select operation on a SQL Server database table using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
|<span data-ttu-id="0910e-118">CompositeOperations</span><span class="sxs-lookup"><span data-stu-id="0910e-118">CompositeOperations</span></span>|<span data-ttu-id="0910e-119">示範如何執行複合操作使用的介面卡在 SQL Server 資料庫上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0910e-119">Demonstrates how to perform composite operations on a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
|<span data-ttu-id="0910e-120">TypedPolling</span><span class="sxs-lookup"><span data-stu-id="0910e-120">TypedPolling</span></span>|<span data-ttu-id="0910e-121">示範如何執行 SQL Server 資料庫使用的介面卡上的強型別輪詢[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0910e-121">Demonstrates how to perform strongly-typed polling on a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
|<span data-ttu-id="0910e-122">FILESTREAMOperation</span><span class="sxs-lookup"><span data-stu-id="0910e-122">FILESTREAMOperation</span></span>|<span data-ttu-id="0910e-123">示範如何執行 SQL Server 2008 資料庫使用的介面卡上的 FILESTREAM 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0910e-123">Demonstrates how to perform FILESTREAM operations on a SQL Server 2008 database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
|<span data-ttu-id="0910e-124">IncrementalNotification</span><span class="sxs-lookup"><span data-stu-id="0910e-124">IncrementalNotification</span></span>|<span data-ttu-id="0910e-125">示範如何從使用配接器與 SQL Server 資料庫的增量通知[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0910e-125">Demonstrates how to receive incremental notification from a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>|  
|<span data-ttu-id="0910e-126">Employee_PurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="0910e-126">Employee_PurchaseOrder</span></span>|<span data-ttu-id="0910e-127">範例根據[教學課程 2： 員工-訂單程序使用 SQL 配接器](tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="0910e-127">Sample based on [Tutorial 2: Employee - Purchase Order Process using the SQL adapter](tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).</span></span>|  
  
## <a name="wcf-service-model-samples"></a><span data-ttu-id="0910e-128">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="0910e-128">WCF service model samples</span></span>   
  
|<span data-ttu-id="0910e-129">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="0910e-129">Sample Directory Name</span></span>|<span data-ttu-id="0910e-130">Description</span><span class="sxs-lookup"><span data-stu-id="0910e-130">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="0910e-131">EmployeeBasicOps</span><span class="sxs-lookup"><span data-stu-id="0910e-131">EmployeeBasicOps</span></span>|<span data-ttu-id="0910e-132">示範如何執行 Insert、 Select、 Update 和刪除作業上使用配接器的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0910e-132">Demonstrates how to perform Insert, Select, Update, and Delete operation on a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-133">ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="0910e-133">ExecuteReader</span></span>|<span data-ttu-id="0910e-134">示範如何叫用 ExecuteReader 作業上使用配接器的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0910e-134">Demonstrates how to invoke an ExecuteReader operation on a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-135">Execute_StoredProc</span><span class="sxs-lookup"><span data-stu-id="0910e-135">Execute_StoredProc</span></span>|<span data-ttu-id="0910e-136">示範如何叫用使用配接器的 SQL Server 資料庫中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="0910e-136">Demonstrates how to invoke a stored procedure in SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-137">Execute_TypedStoredProcedure</span><span class="sxs-lookup"><span data-stu-id="0910e-137">Execute_TypedStoredProcedure</span></span>|<span data-ttu-id="0910e-138">示範如何叫用的強型別預存程序中使用配接器的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0910e-138">Demonstrates how to invoke a strongly-typed stored procedure in SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-139">Records_FILESTREAM_Op</span><span class="sxs-lookup"><span data-stu-id="0910e-139">Records_FILESTREAM_Op</span></span>|<span data-ttu-id="0910e-140">示範如何使用配接器的 SQL Server 資料庫資料表中的 FILESTREAM 資料的更新。</span><span class="sxs-lookup"><span data-stu-id="0910e-140">Demonstrates how to update FILESTREAM data in a SQL Server database table using the adapter.</span></span>|  
|<span data-ttu-id="0910e-141">ScalarFunction_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0910e-141">ScalarFunction_ServiceModel</span></span>|<span data-ttu-id="0910e-142">示範如何叫用純量函數中使用配接器的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0910e-142">Demonstrates how to invoke scalar functions in a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-143">TableFunction_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0910e-143">TableFunction_ServiceModel</span></span>|<span data-ttu-id="0910e-144">示範如何叫用中使用配接器的 SQL Server 資料庫的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="0910e-144">Demonstrates how to invoke table-valued functions in a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-145">Polling_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0910e-145">Polling_ServiceModel</span></span>|<span data-ttu-id="0910e-146">示範如何從 SQL Server 資料庫使用配接器接收輪詢基礎資料變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="0910e-146">Demonstrates how to receive polling-based data-changed messages from a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-147">TypedPolling_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0910e-147">TypedPolling_ServiceModel</span></span>|<span data-ttu-id="0910e-148">示範如何從 SQL Server 資料庫使用配接器接收強型別輪詢基礎資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="0910e-148">Demonstrates how to receive strongly-typed polling-based data-changed messages from a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-149">Notification_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0910e-149">Notification_ServiceModel</span></span>|<span data-ttu-id="0910e-150">示範如何從 SQL Server 資料庫使用配接器接收查詢通知。</span><span class="sxs-lookup"><span data-stu-id="0910e-150">Demonstrates how to receive query notifications from a SQL Server database using the adapter.</span></span>|  
  
## <a name="wcf-channel-model-samples"></a><span data-ttu-id="0910e-151">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="0910e-151">WCF channel model samples</span></span> 
  
|<span data-ttu-id="0910e-152">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="0910e-152">Sample Directory Name</span></span>|<span data-ttu-id="0910e-153">Description</span><span class="sxs-lookup"><span data-stu-id="0910e-153">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="0910e-154">EmployeeInsertOp</span><span class="sxs-lookup"><span data-stu-id="0910e-154">EmployeeInsertOp</span></span>|<span data-ttu-id="0910e-155">示範如何執行插入作業上使用配接器的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0910e-155">Demonstrates how to perform an Insert operation on a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="0910e-156">Polling_ChannelModel</span><span class="sxs-lookup"><span data-stu-id="0910e-156">Polling_ChannelModel</span></span>|<span data-ttu-id="0910e-157">示範如何從 SQL Server 資料庫使用配接器接收輪詢基礎資料變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="0910e-157">Demonstrates how to receive polling-based data-changed messages from a SQL Server database using the adapter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0910e-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0910e-158">See Also</span></span>  
[<span data-ttu-id="0910e-159">開發 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="0910e-159">Develop your SQL applications</span></span>](develop-your-sql-applications.md)