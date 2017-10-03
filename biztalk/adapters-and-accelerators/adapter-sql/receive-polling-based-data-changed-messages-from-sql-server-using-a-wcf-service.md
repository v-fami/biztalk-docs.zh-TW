---
title: "從 SQL Server 使用 WCF 服務模型收到輪詢基礎資料變更的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8713dd38-65ff-4d89-b23b-a93c06c5ff22
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ff5ca099733a59fc5aa64c9ebbe261375f1a488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-using-the-wcf-service-model"></a><span data-ttu-id="5d86b-102">從 SQL Server 使用 WCF 服務模型收到輪詢基礎資料變更的訊息</span><span class="sxs-lookup"><span data-stu-id="5d86b-102">Receive Polling-based Data-changed Messages from SQL Server Using the WCF Service Model</span></span>
<span data-ttu-id="5d86b-103">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收 SQL Server 資料表或檢視表的週期性的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="5d86b-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive periodic data-change messages for SQL Server tables or views.</span></span> <span data-ttu-id="5d86b-104">您可以指定執行以輪詢資料庫配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="5d86b-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="5d86b-105">輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="5d86b-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span>  
  
 <span data-ttu-id="5d86b-106">如需有關如何配接器支援在輪詢的詳細資訊，請參閱[在 SQL Server 中使用 SQL 配接器輪詢](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5d86b-106">For more information on how the adapter supports polling, see [Polling in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d86b-107">本主題示範如何使用**輪詢**輸入作業使用輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="5d86b-107">This topic demonstrates how to use the **Polling** inbound operation to use polling messages.</span></span> <span data-ttu-id="5d86b-108">輪詢作業的訊息是不強型別。</span><span class="sxs-lookup"><span data-stu-id="5d86b-108">The message for the Polling operation is not strongly-typed.</span></span> <span data-ttu-id="5d86b-109">如果您想要取得強型別輪詢訊息，您必須使用**TypedPolling**作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-109">If you want to get strongly-typed polling message, you must use the **TypedPolling** operation.</span></span> <span data-ttu-id="5d86b-110">您也必須使用**TypedPolling**單一應用程式中有多個輪詢作業的作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-110">You must also use the **TypedPolling** operation to have multiple polling operations in a single application.</span></span> <span data-ttu-id="5d86b-111">如需有關如何執行指示**TypedPolling**作業，請參閱[接收強型別輪詢基礎資料變更訊息從 SQL Server 使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5d86b-111">For instructions on how to perform **TypedPolling** operation, see [Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using WCF Service Model](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5d86b-112">如果您想要在單一應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分連線 URI 成為唯一的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="5d86b-112">If you want to have more than one polling operation in a single application, you must specify an **InboundID** connection property as part of the connection URI to make it unique.</span></span> <span data-ttu-id="5d86b-113">您指定的輸入的識別碼會加入至作業的命名空間，使它成為唯一。</span><span class="sxs-lookup"><span data-stu-id="5d86b-113">The inbound ID you specify is added to the operation namespace to make it unique.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="5d86b-114">本主題示範輪詢的方式</span><span class="sxs-lookup"><span data-stu-id="5d86b-114">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="5d86b-115">本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援接收資料變更訊息，建立.NET 應用程式，並產生的 WCF 服務合約**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-115">In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving data change messages, create a .NET application and generate the WCF service contract for the **Polling** operation.</span></span> <span data-ttu-id="5d86b-116">如果您想要指定輪詢相關繫結屬性產生 WCF 服務合約時，指定**PolledDataAvailableStatement**為：</span><span class="sxs-lookup"><span data-stu-id="5d86b-116">If you want to specify the polling related binding properties while generating the WCF service contract, specify the **PolledDataAvailableStatement** as:</span></span>  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 <span data-ttu-id="5d86b-117">**PolledDataAvailableStatement**必須傳回一個結果集包含正值的第一個儲存格。</span><span class="sxs-lookup"><span data-stu-id="5d86b-117">The **PolledDataAvailableStatement** must return a result set with the first cell containing a positive value.</span></span> <span data-ttu-id="5d86b-118">如果第一個資料格不包含正值，配接器不會執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="5d86b-118">If the first cell does not contain a positive value, the adapter does not execute the polling statement.</span></span>  
  
 <span data-ttu-id="5d86b-119">輪詢陳述式的一部分，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="5d86b-119">As part of the polling statement, perform the following operations:</span></span>  
  
1.  <span data-ttu-id="5d86b-120">選取從 Employee 資料表的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="5d86b-120">Select all the rows from the Employee table.</span></span>  
  
2.  <span data-ttu-id="5d86b-121">執行預存程序 (MOVE_EMP_DATA) 會將所有的記錄從 Employee 資料表 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="5d86b-121">Execute a stored procedure (MOVE_EMP_DATA) to move all the records from the Employee table to an EmployeeHistory table.</span></span>  
  
3.  <span data-ttu-id="5d86b-122">執行預存程序 (ADD_EMP_DETAILS) Employee 資料表中加入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="5d86b-122">Execute a stored procedure (ADD_EMP_DETAILS) to add a new record to the Employee table.</span></span> <span data-ttu-id="5d86b-123">此程序會接受員工名稱、 指定和薪資做為參數。</span><span class="sxs-lookup"><span data-stu-id="5d86b-123">This procedure takes the employee name, designation, and salary as parameters.</span></span>  
  
 <span data-ttu-id="5d86b-124">若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="5d86b-124">To perform these operations, you must specify the following for the **PollingStatement** binding property:</span></span>  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 <span data-ttu-id="5d86b-125">執行輪詢陳述式之後，選取從 Employee 資料表的所有記錄，並收到來自 SQL Server 的訊息。</span><span class="sxs-lookup"><span data-stu-id="5d86b-125">After the polling statement is executed, all the records from the Employee table are selected and the message from SQL Server is received.</span></span> <span data-ttu-id="5d86b-126">MOVE_EMP_DATA 預存程序執行的配接器之後，所有的記錄會移至 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="5d86b-126">After the MOVE_EMP_DATA stored procedure is executed by the adapter, all the records are moved to the EmployeeHistory table.</span></span> <span data-ttu-id="5d86b-127">然後，ADD_EMP_DETAILS 預存程序會執行以將新記錄新增至 Employee 資料表。</span><span class="sxs-lookup"><span data-stu-id="5d86b-127">Then, the ADD_EMP_DETAILS stored procedure is executed to add a new record to the Employee table.</span></span> <span data-ttu-id="5d86b-128">下次輪詢執行只會傳回單一記錄。</span><span class="sxs-lookup"><span data-stu-id="5d86b-128">The next polling execution will only return a single record.</span></span> <span data-ttu-id="5d86b-129">關閉服務主機之前，此週期會持續進行。</span><span class="sxs-lookup"><span data-stu-id="5d86b-129">This cycle continues until you close the service host.</span></span>  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="5d86b-130">使用 SQL 配接器繫結屬性中設定輪詢查詢</span><span class="sxs-lookup"><span data-stu-id="5d86b-130">Configuring a Polling Query with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="5d86b-131">下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結，您用來設定配接器來接收資料變更訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="5d86b-131">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="5d86b-132">輪詢的.NET 應用程式的一部分，您必須指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="5d86b-132">You must specify these binding properties as part of the .NET application for polling.</span></span>  
  
|<span data-ttu-id="5d86b-133">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="5d86b-133">Binding Property</span></span>|<span data-ttu-id="5d86b-134">Description</span><span class="sxs-lookup"><span data-stu-id="5d86b-134">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="5d86b-135">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="5d86b-135">**InboundOperationType**</span></span>|<span data-ttu-id="5d86b-136">指定您是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-136">Specifies whether you want to perform **Polling**, **TypedPolling**, or **Notification** inbound operation.</span></span> <span data-ttu-id="5d86b-137">預設值是**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="5d86b-137">Default is **Polling**.</span></span>|  
|<span data-ttu-id="5d86b-138">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="5d86b-138">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="5d86b-139">指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。</span><span class="sxs-lookup"><span data-stu-id="5d86b-139">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="5d86b-140">SQL 陳述式必須傳回的結果集資料列和資料行所組成。</span><span class="sxs-lookup"><span data-stu-id="5d86b-140">The SQL statement must return a result set consisting of rows and columns.</span></span> <span data-ttu-id="5d86b-141">只有一個資料列是否可用，SQL 陳述式指定**PollingStatement**繫結屬性將會執行。</span><span class="sxs-lookup"><span data-stu-id="5d86b-141">Only if a row is available, the SQL statement specified for the **PollingStatement** binding property will be executed.</span></span>|  
|<span data-ttu-id="5d86b-142">**PollingIntervalInSeconds**</span><span class="sxs-lookup"><span data-stu-id="5d86b-142">**PollingIntervalInSeconds**</span></span>|<span data-ttu-id="5d86b-143">指定間隔，以秒為單位，此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="5d86b-143">Specifies the interval, in seconds, at which the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="5d86b-144">預設值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="5d86b-144">The default is 30 seconds.</span></span> <span data-ttu-id="5d86b-145">輪詢間隔會決定後續輪詢間隔時間。</span><span class="sxs-lookup"><span data-stu-id="5d86b-145">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="5d86b-146">如果指定的間隔內執行的陳述式，則配接器就會等候剩餘的時間間隔中。</span><span class="sxs-lookup"><span data-stu-id="5d86b-146">If the statement is executed within the specified interval, the adapter waits for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="5d86b-147">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="5d86b-147">**PollingStatement**</span></span>|<span data-ttu-id="5d86b-148">指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5d86b-148">Specifies the SQL statement to poll the SQL Server database table.</span></span> <span data-ttu-id="5d86b-149">您可以指定簡單的 SELECT 陳述式或預存程序輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="5d86b-149">You can specify a simple SELECT statement or a stored procedure for the polling statement.</span></span> <span data-ttu-id="5d86b-150">預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="5d86b-150">The default is null.</span></span> <span data-ttu-id="5d86b-151">您必須指定的值**PollingStatement**來啟用輪詢。</span><span class="sxs-lookup"><span data-stu-id="5d86b-151">You must specify a value for **PollingStatement** to enable polling.</span></span> <span data-ttu-id="5d86b-152">輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="5d86b-152">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="5d86b-153">您可以指定任意數目的 SQL 陳述式以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="5d86b-153">You can specify any number of SQL statements separated by a semi-colon.</span></span>|  
|<span data-ttu-id="5d86b-154">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="5d86b-154">**PollWhileDataFound**</span></span>|<span data-ttu-id="5d86b-155">指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並為指定的 SQL 陳述式會持續執行**PolledDataAvailableStatement**如果輪詢資料表中的資料可繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="5d86b-155">Specifies whether the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignores the polling interval and continuously executes the SQL statement specified for the **PolledDataAvailableStatement** binding property, if data is available in the table being polled.</span></span> <span data-ttu-id="5d86b-156">如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="5d86b-156">If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval.</span></span> <span data-ttu-id="5d86b-157">預設值是**false**。</span><span class="sxs-lookup"><span data-stu-id="5d86b-157">Default is **false**.</span></span>|  
  
 <span data-ttu-id="5d86b-158">如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5d86b-158">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="5d86b-159">如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]進一步來輪詢 SQL Server，請閱讀。</span><span class="sxs-lookup"><span data-stu-id="5d86b-159">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll SQL Server, read further.</span></span>  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="5d86b-160">在 WCF 服務模型中設定輪詢</span><span class="sxs-lookup"><span data-stu-id="5d86b-160">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="5d86b-161">若要接收**輪詢**作業使用 WCF 服務模型時，您必須：</span><span class="sxs-lookup"><span data-stu-id="5d86b-161">To receive the **Polling** operation when you use the WCF service model, you must:</span></span>  
  
1.  <span data-ttu-id="5d86b-162">產生 WCF 服務合約 （介面）**輪詢**從配接器所公開的中繼資料的作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-162">Generate a WCF service contract (interface) for the **Polling** operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="5d86b-163">若要這樣做，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d86b-163">To do this, you could use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>  
  
2.  <span data-ttu-id="5d86b-164">實作這個介面從 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="5d86b-164">Implement a WCF service from this interface.</span></span>  
  
3.  <span data-ttu-id="5d86b-165">裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。</span><span class="sxs-lookup"><span data-stu-id="5d86b-165">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="5d86b-166">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="5d86b-166">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="5d86b-167">本主題中的範例輪詢 Employee 資料表。</span><span class="sxs-lookup"><span data-stu-id="5d86b-167">The examples in this topic poll the Employee table.</span></span> <span data-ttu-id="5d86b-168">此範例也會使用 MOVE_EMP_DATA 和 ADD_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="5d86b-168">The example also uses the MOVE_EMP_DATA and ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="5d86b-169">指令碼來產生這些成品隨附的範例。</span><span class="sxs-lookup"><span data-stu-id="5d86b-169">A script to generate these artifacts is supplied with the samples.</span></span> <span data-ttu-id="5d86b-170">如需這些範例的詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5d86b-170">For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="5d86b-171">範例中， **Polling_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="5d86b-171">A sample, **Polling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="5d86b-172">WCF 服務合約和類別</span><span class="sxs-lookup"><span data-stu-id="5d86b-172">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="5d86b-173">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]建立 WCF 服務合約 （介面） 和支援類別**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-173">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Polling** operation.</span></span> <span data-ttu-id="5d86b-174">如需產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="5d86b-174">For more information about generating a WCF service contract, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="5d86b-175">WCF 服務合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="5d86b-175">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="5d86b-176">下列程式碼顯示產生的 WCF 服務合約 （介面）**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-176">The following code shows the WCF service contract (interface) generated for the **Polling** operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="PollingOperation")]  
public interface PollingOperation {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Polling/) of message Polling  
    // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="Polling")]  
    [System.ServiceModel.XmlSerializerFormatAttribute()]  
    void Polling(Polling request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="5d86b-177">訊息合約</span><span class="sxs-lookup"><span data-stu-id="5d86b-177">The Message Contracts</span></span>  
 <span data-ttu-id="5d86b-178">訊息合約命名空間來修改**InboundID**中連線的 URI，如果指定的參數。</span><span class="sxs-lookup"><span data-stu-id="5d86b-178">The message contract namespace is modified by the **InboundID** parameter in the connection URI, if specified.</span></span> <span data-ttu-id="5d86b-179">在此範例中，您未指定連線 URI 中的輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d86b-179">In this example, you did not specify an inbound ID in the connection URI.</span></span> <span data-ttu-id="5d86b-180">要求訊息傳回資料集。</span><span class="sxs-lookup"><span data-stu-id="5d86b-180">The request message returns a DataSet.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Polling", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/Polling/", IsWrapped=true)]  
public partial class Polling {  
  
[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Polling/", Order=0)]  
    [System.Xml.Serialization.XmlArrayAttribute(IsNullable=true)]  
    [System.Xml.Serialization.XmlArrayItemAttribute("DataSet", Namespace="http://schemas.datacontract.org/2004/07/System.Data", IsNullable=false)]  
    public System.Data.DataSet[] PolledData;  
  
    public Polling() {  
    }  
  
    public Polling(System.Data.DataSet[] PolledData) {  
        this.PolledData = PolledData;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="5d86b-181">WCF 服務類別</span><span class="sxs-lookup"><span data-stu-id="5d86b-181">WCF Service Class</span></span>  
 <span data-ttu-id="5d86b-182">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生虛設常式實作的服務合約 （介面） 的 WCF 服務類別的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d86b-182">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="5d86b-183">檔案的名稱是 SqlAdapterBindingService.cs。</span><span class="sxs-lookup"><span data-stu-id="5d86b-183">The name of the file is SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="5d86b-184">您可以插入要處理邏輯**輪詢**直接將這個類別的作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-184">You can insert the logic to process the **Polling** operation directly into this class.</span></span> <span data-ttu-id="5d86b-185">下列程式碼將示範所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d86b-185">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace SqlAdapterBindingNamespace {  
  
    public class SqlAdapterBindingService : PollingOperation {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Polling/) of message Polling   
        // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void Polling(Polling request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-inbound-messages-for-polling-operation"></a><span data-ttu-id="5d86b-186">輪詢作業接收內送的訊息</span><span class="sxs-lookup"><span data-stu-id="5d86b-186">Receiving Inbound Messages for Polling Operation</span></span>  
 <span data-ttu-id="5d86b-187">本節說明如何撰寫.NET 應用程式來接收傳入的輪詢訊息使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d86b-187">This section provides instructions on how to write a .NET application to receive inbound polling messages using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-from-the-sql-adapter"></a><span data-ttu-id="5d86b-188">若要接收 SQL 配接器的輪詢訊息</span><span class="sxs-lookup"><span data-stu-id="5d86b-188">To receive polling messages from the SQL adapter</span></span>  
  
1.  <span data-ttu-id="5d86b-189">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 服務合約 （介面） 和協助程式類別，如**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="5d86b-189">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Polling** operation.</span></span> <span data-ttu-id="5d86b-190">如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="5d86b-190">For more information, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span> <span data-ttu-id="5d86b-191">您可以選擇性地產生服務合約和協助程式類別時指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="5d86b-191">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="5d86b-192">這可確保它們已正確設定在產生的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="5d86b-192">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="5d86b-193">實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="5d86b-193">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="5d86b-194">**輪詢**這個類別的方法可以擲回例外狀況中止輪詢交易，處理從接收的資料發生錯誤**輪詢**作業; 否則方法會執行不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="5d86b-194">The **Polling** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **Polling** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="5d86b-195">您必須屬性 WCF 服務類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d86b-195">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="5d86b-196">內**輪詢**方法，您可以直接實作應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="5d86b-196">Within the **Polling** method, you can implement your application logic directly.</span></span> <span data-ttu-id="5d86b-197">這個類別可以 SqlAdapterBindingService.cs 中找到。</span><span class="sxs-lookup"><span data-stu-id="5d86b-197">This class can be found in SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="5d86b-198">這段程式碼，在此範例中的子類別**SqlAdapterBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="5d86b-198">This code in this example sub-classes the **SqlAdapterBindingService** class.</span></span> <span data-ttu-id="5d86b-199">在此程式碼，做為資料集所接收的輪詢訊息會寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="5d86b-199">In this code, the polling message received as a DataSet is written to the console.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
  
    public override void Polling(Polling request)  
    {  
        Console.WriteLine("\nNew Polling Records Received");  
        Console.WriteLine("*************************************************");  
        DataSet[] dataArray = request.PolledData;  
        foreach (DataTable tab in dataArray[0].Tables)  
        {  
            foreach (DataRow row in tab.Rows)  
            {  
                for (int i = 0; i < tab.Columns.Count; i++)  
                {  
                    Console.WriteLine(row[i]);  
                }  
            }  
        }  
        Console.WriteLine("*************************************************");  
        Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="5d86b-200">因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]未接受認證的連線 URI 的一部分，您必須實作下列類別，以 SQL Server 資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="5d86b-200">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not accept credentials as part of the connection URI, you must implement the following class to pass credentials for the SQL Server database.</span></span> <span data-ttu-id="5d86b-201">在應用程式的第二個部分中，您會具現化這個類別，以對 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="5d86b-201">In the latter part of the application, you will instantiate this class to pass on the SQL Server credentials.</span></span>  
  
    ```  
    class PollingCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new PollingCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="5d86b-202">建立**SqlAdapterBinding**和設定輪詢作業藉由指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="5d86b-202">Create a **SqlAdapterBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="5d86b-203">您可以在程式碼中明確或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="5d86b-203">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="5d86b-204">最少，您必須指定**InboundOperationType**， **PolledDataAvailableStatement**，和**PollingStatement**。</span><span class="sxs-lookup"><span data-stu-id="5d86b-204">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement**.</span></span>  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
    binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
    ```  
  
5.  <span data-ttu-id="5d86b-205">指定 SQL Server 資料庫認證，藉由執行個體化**PollingCredentials**您在步驟 3 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="5d86b-205">Specify SQL Server database credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
6.  <span data-ttu-id="5d86b-206">建立在步驟 2 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5d86b-206">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
7.  <span data-ttu-id="5d86b-207">建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="5d86b-207">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="5d86b-208">如果指定基底的連線 URI 不能包含輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d86b-208">The base connection URI cannot contain the inbound ID, if specified.</span></span> <span data-ttu-id="5d86b-209">您也應該指定的認證。</span><span class="sxs-lookup"><span data-stu-id="5d86b-209">You should also specify the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
8.  <span data-ttu-id="5d86b-210">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="5d86b-210">Add a service endpoint to the service host.</span></span> <span data-ttu-id="5d86b-211">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="5d86b-211">To do this:</span></span>  
  
    -   <span data-ttu-id="5d86b-212">使用步驟 4 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="5d86b-212">Use the binding created in step 4.</span></span>  
  
    -   <span data-ttu-id="5d86b-213">指定連線 URI，其中包含認證並在必要時輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d86b-213">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="5d86b-214">為 「 PollingOperation"指定的合約。</span><span class="sxs-lookup"><span data-stu-id="5d86b-214">Specify the contract as "PollingOperation".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify PollingOperation as the contract  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
    serviceHost.AddServiceEndpoint("PollingOperation", binding, ConnectionUri);  
    ```  
  
9. <span data-ttu-id="5d86b-215">若要收到輪詢資料，請開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="5d86b-215">To receive polling data, open the service host.</span></span> <span data-ttu-id="5d86b-216">每當查詢會傳回結果集時，配接器會傳回資料。</span><span class="sxs-lookup"><span data-stu-id="5d86b-216">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
10. <span data-ttu-id="5d86b-217">若要終止輪詢，關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="5d86b-217">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5d86b-218">配接器將會繼續輪詢直到關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="5d86b-218">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="5d86b-219">範例</span><span class="sxs-lookup"><span data-stu-id="5d86b-219">Example</span></span>  
 <span data-ttu-id="5d86b-220">下列範例會顯示執行 Employee 資料表的輪詢查詢。</span><span class="sxs-lookup"><span data-stu-id="5d86b-220">The following example shows a polling query that executes the Employee table.</span></span> <span data-ttu-id="5d86b-221">輪詢陳述式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="5d86b-221">The polling statement performs the following tasks:</span></span>  
  
1.  <span data-ttu-id="5d86b-222">選取從 Employee 資料表的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="5d86b-222">Selects all the records from the Employee table.</span></span>  
  
2.  <span data-ttu-id="5d86b-223">執行將從 Employee 資料表的所有記錄移動到 EmployeeHistory 資料表 MOVE_EMP_DATA 預存程序。</span><span class="sxs-lookup"><span data-stu-id="5d86b-223">Executes the MOVE_EMP_DATA stored procedure to move all records from Employee table to EmployeeHistory table.</span></span>  
  
3.  <span data-ttu-id="5d86b-224">執行 ADD_EMP_DETAILS 預存程序加入 Employee 資料表的單一記錄。</span><span class="sxs-lookup"><span data-stu-id="5d86b-224">Executes the ADD_EMP_DETAILS stored procedure to add a single record to the Employee table.</span></span>  
  
 <span data-ttu-id="5d86b-225">第一個輪詢訊息會包含從 Employee 資料表的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="5d86b-225">The first polling message will contain all the records from the Employee table.</span></span> <span data-ttu-id="5d86b-226">後續的輪詢訊息會包含只 ADD_EMP_DETAILS 預存程序所插入的最後一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="5d86b-226">The subsequent polling messages will contain only the last record inserted by the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="5d86b-227">配接器將繼續輪詢直到按關閉服務主機`<RETURN>`。</span><span class="sxs-lookup"><span data-stu-id="5d86b-227">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
using Microsoft.Adapters.Sql;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
using System.Data;  
  
namespace Polling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
  
        public override void Polling(Polling request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            DataSet[] dataArray = request.PolledData;  
            foreach (DataTable tab in dataArray[0].Tables)  
            {  
                foreach (DataRow row in tab.Rows)  
                {  
                    for (int i = 0; i < tab.Columns.Count; i++)  
                    {  
                        Console.WriteLine(row[i]);  
                    }  
                }  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
  
    class PollingCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new PollingCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost serviceHost = null;  
            try  
            {  
                Console.WriteLine("Sample started...");  
                Console.WriteLine("Press any key to start polling...");  
                Console.ReadLine();  
  
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
                Console.WriteLine("Binding properties assigned...");  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId (if any) that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // a query_string (InboundID); otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
  
                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("PollingOperation", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Polling started...");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d86b-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d86b-228">See Also</span></span>  
 [<span data-ttu-id="5d86b-229">搭配 WCF 服務模型中使用 SQL 配接器的輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d86b-229">Poll SQL Server using the SQL Adapter with WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)