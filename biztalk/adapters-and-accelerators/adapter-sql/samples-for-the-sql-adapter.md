---
title: SQL 配接器範例 |Microsoft Docs
description: 可以使用 BizTalk Server、 WCF 服務模型，與 WCF 通道模型的 SQL WCF 配接器範例
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2438696-bc51-46df-81ca-00c17a52736e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f7ff1e686fd8de344c4de4513fbda84003c69a8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982631"
---
# <a name="samples-for-the-sql-adapter"></a><span data-ttu-id="d5cd7-103">SQL 配接器的範例</span><span class="sxs-lookup"><span data-stu-id="d5cd7-103">Samples for the SQL adapter</span></span>

<span data-ttu-id="d5cd7-104">範例[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]會分類為：</span><span class="sxs-lookup"><span data-stu-id="d5cd7-104">Samples for [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] are categorized into:</span></span>  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d5cd7-105"> 範例</span><span class="sxs-lookup"><span data-stu-id="d5cd7-105"> samples</span></span>  
  
- <span data-ttu-id="d5cd7-106">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="d5cd7-106">WCF service model samples</span></span>  
  
- <span data-ttu-id="d5cd7-107">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="d5cd7-107">WCF channel model samples</span></span>  
  
<span data-ttu-id="d5cd7-108">這些範例位於[BizTalk Adapter Pack 2010: SQL 配接器範例](https://www.microsoft.com/download/details.aspx?id=22455)。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-108">The samples are available at [BizTalk Adapter Pack 2010: SQL adapter samples](https://www.microsoft.com/download/details.aspx?id=22455).</span></span> <span data-ttu-id="d5cd7-109">建立物件的 SQL 指令碼使用在範例中，例如資料庫資料表，而包含程序。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-109">The SQL scripts for creating the objects used in the samples, such as database, tables, and procedures are included.</span></span> 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
<span data-ttu-id="d5cd7-110">下列清單描述的範例。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-110">The following list describes the samples.</span></span>
  
## <a name="biztalk-server-samples"></a><span data-ttu-id="d5cd7-111">BizTalk Server 範例</span><span class="sxs-lookup"><span data-stu-id="d5cd7-111">BizTalk Server samples</span></span>  
  
|  <span data-ttu-id="d5cd7-112">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="d5cd7-112">Sample Directory Name</span></span>  |                                                                                          <span data-ttu-id="d5cd7-113">描述</span><span class="sxs-lookup"><span data-stu-id="d5cd7-113">Description</span></span>                                                                                          |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d5cd7-114">ExecuteStoredProcedure</span><span class="sxs-lookup"><span data-stu-id="d5cd7-114">ExecuteStoredProcedure</span></span>  |      <span data-ttu-id="d5cd7-115">示範如何叫用使用配接器使用的 SQL Server 資料庫中的預存程序[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-115">Demonstrates how to invoke a stored procedure in SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] .</span></span>      |
|       <span data-ttu-id="d5cd7-116">SelectTable</span><span class="sxs-lookup"><span data-stu-id="d5cd7-116">SelectTable</span></span>       |  <span data-ttu-id="d5cd7-117">示範如何執行 SQL Server 資料庫資料表使用的介面卡上的選取作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-117">Demonstrates how to perform a Select operation on a SQL Server database table using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  |
|   <span data-ttu-id="d5cd7-118">CompositeOperations</span><span class="sxs-lookup"><span data-stu-id="d5cd7-118">CompositeOperations</span></span>   |    <span data-ttu-id="d5cd7-119">示範如何執行複合作業使用的介面卡在 SQL Server 資料庫上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-119">Demonstrates how to perform composite operations on a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>    |
|      <span data-ttu-id="d5cd7-120">TypedPolling</span><span class="sxs-lookup"><span data-stu-id="d5cd7-120">TypedPolling</span></span>       |   <span data-ttu-id="d5cd7-121">示範如何使用配接器使用 SQL Server 資料庫上執行強型別輪詢[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-121">Demonstrates how to perform strongly-typed polling on a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>   |
|   <span data-ttu-id="d5cd7-122">FILESTREAMOperation</span><span class="sxs-lookup"><span data-stu-id="d5cd7-122">FILESTREAMOperation</span></span>   | <span data-ttu-id="d5cd7-123">示範如何執行 SQL Server 2008 資料庫使用的介面卡上的 FILESTREAM 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-123">Demonstrates how to perform FILESTREAM operations on a SQL Server 2008 database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> |
| <span data-ttu-id="d5cd7-124">IncrementalNotification</span><span class="sxs-lookup"><span data-stu-id="d5cd7-124">IncrementalNotification</span></span> | <span data-ttu-id="d5cd7-125">示範如何從 SQL Server 資料庫使用的配接器接收累加通知[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-125">Demonstrates how to receive incremental notification from a SQL Server database using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> |
| <span data-ttu-id="d5cd7-126">Employee_PurchaseOrder</span><span class="sxs-lookup"><span data-stu-id="d5cd7-126">Employee_PurchaseOrder</span></span>  |                  <span data-ttu-id="d5cd7-127">範例根據[教學課程 2： 員工-訂單程序使用 SQL 配接器](tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-127">Sample based on [Tutorial 2: Employee - Purchase Order Process using the SQL adapter](tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).</span></span>                  |
  
## <a name="wcf-service-model-samples"></a><span data-ttu-id="d5cd7-128">WCF 服務模型範例</span><span class="sxs-lookup"><span data-stu-id="d5cd7-128">WCF service model samples</span></span>   
  
|<span data-ttu-id="d5cd7-129">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="d5cd7-129">Sample Directory Name</span></span>|<span data-ttu-id="d5cd7-130">描述</span><span class="sxs-lookup"><span data-stu-id="d5cd7-130">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="d5cd7-131">EmployeeBasicOps</span><span class="sxs-lookup"><span data-stu-id="d5cd7-131">EmployeeBasicOps</span></span>|<span data-ttu-id="d5cd7-132">示範如何執行 Insert、 Select、 Update 和刪除使用配接器在 SQL Server 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-132">Demonstrates how to perform Insert, Select, Update, and Delete operation on a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-133">ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="d5cd7-133">ExecuteReader</span></span>|<span data-ttu-id="d5cd7-134">示範如何叫用 ExecuteReader 作業上使用配接器的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-134">Demonstrates how to invoke an ExecuteReader operation on a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-135">Execute_StoredProc</span><span class="sxs-lookup"><span data-stu-id="d5cd7-135">Execute_StoredProc</span></span>|<span data-ttu-id="d5cd7-136">示範如何叫用使用配接器的 SQL Server 資料庫中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-136">Demonstrates how to invoke a stored procedure in SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-137">Execute_TypedStoredProcedure</span><span class="sxs-lookup"><span data-stu-id="d5cd7-137">Execute_TypedStoredProcedure</span></span>|<span data-ttu-id="d5cd7-138">示範如何叫用強型別的預存程序中使用配接器的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-138">Demonstrates how to invoke a strongly-typed stored procedure in SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-139">Records_FILESTREAM_Op</span><span class="sxs-lookup"><span data-stu-id="d5cd7-139">Records_FILESTREAM_Op</span></span>|<span data-ttu-id="d5cd7-140">示範如何更新使用配接器的 SQL Server 資料庫資料表中的 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-140">Demonstrates how to update FILESTREAM data in a SQL Server database table using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-141">ScalarFunction_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5cd7-141">ScalarFunction_ServiceModel</span></span>|<span data-ttu-id="d5cd7-142">示範如何叫用使用配接器的 SQL Server 資料庫中的純量函式。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-142">Demonstrates how to invoke scalar functions in a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-143">TableFunction_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5cd7-143">TableFunction_ServiceModel</span></span>|<span data-ttu-id="d5cd7-144">示範如何叫用中使用配接器的 SQL Server 資料庫的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-144">Demonstrates how to invoke table-valued functions in a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-145">Polling_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5cd7-145">Polling_ServiceModel</span></span>|<span data-ttu-id="d5cd7-146">示範如何從 SQL Server 資料庫，使用配接器接收以輪詢為基礎的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-146">Demonstrates how to receive polling-based data-changed messages from a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-147">TypedPolling_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5cd7-147">TypedPolling_ServiceModel</span></span>|<span data-ttu-id="d5cd7-148">示範如何從 SQL Server 資料庫，使用配接器接收強型別輪詢為基礎的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-148">Demonstrates how to receive strongly-typed polling-based data-changed messages from a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-149">Notification_ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5cd7-149">Notification_ServiceModel</span></span>|<span data-ttu-id="d5cd7-150">示範如何從 SQL Server 資料庫，使用配接器接收查詢通知。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-150">Demonstrates how to receive query notifications from a SQL Server database using the adapter.</span></span>|  
  
## <a name="wcf-channel-model-samples"></a><span data-ttu-id="d5cd7-151">WCF 通道模型範例</span><span class="sxs-lookup"><span data-stu-id="d5cd7-151">WCF channel model samples</span></span> 
  
|<span data-ttu-id="d5cd7-152">範例目錄名稱</span><span class="sxs-lookup"><span data-stu-id="d5cd7-152">Sample Directory Name</span></span>|<span data-ttu-id="d5cd7-153">描述</span><span class="sxs-lookup"><span data-stu-id="d5cd7-153">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="d5cd7-154">EmployeeInsertOp</span><span class="sxs-lookup"><span data-stu-id="d5cd7-154">EmployeeInsertOp</span></span>|<span data-ttu-id="d5cd7-155">示範如何執行插入作業上使用配接器的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-155">Demonstrates how to perform an Insert operation on a SQL Server database using the adapter.</span></span>|  
|<span data-ttu-id="d5cd7-156">Polling_ChannelModel</span><span class="sxs-lookup"><span data-stu-id="d5cd7-156">Polling_ChannelModel</span></span>|<span data-ttu-id="d5cd7-157">示範如何從 SQL Server 資料庫，使用配接器接收以輪詢為基礎的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="d5cd7-157">Demonstrates how to receive polling-based data-changed messages from a SQL Server database using the adapter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5cd7-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5cd7-158">See Also</span></span>  
[<span data-ttu-id="d5cd7-159">開發 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="d5cd7-159">Develop your SQL applications</span></span>](develop-your-sql-applications.md)