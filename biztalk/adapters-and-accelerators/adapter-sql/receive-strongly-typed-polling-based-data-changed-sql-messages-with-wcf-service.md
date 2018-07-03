---
title: 接收從 SQL Server 使用 WCF 服務模型的強型別輪詢為基礎的資料變更訊息 |Microsoft Docs
description: 使用.NET 應用程式來設定具型別的輪詢或使用 BizTalk Server 中的 WCF-SQL 配接器的 WCF 服務的強型別輪詢
ms.custom: ''
ms.date: 10/09/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b55eda71-1226-43f2-bc2f-e6b35563210b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adf6f1e322485521504259f24dade00bb33a4539
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012647"
---
# <a name="receive-strongly-typed-polling-based-data-changed-messages-from-sql-server-using-wcf-service-model"></a><span data-ttu-id="9f454-103">接收從 SQL Server 使用 WCF 服務模型的強型別輪詢為基礎的資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="9f454-103">Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using WCF Service Model</span></span>
<span data-ttu-id="9f454-104">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來接收 SQL Server 中的強型別輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="9f454-104">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive strongly-typed polling messages from SQL Server.</span></span> <span data-ttu-id="9f454-105">您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="9f454-105">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="9f454-106">輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="9f454-106">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span> <span data-ttu-id="9f454-107">您必須使用強型別輪詢，在案例中您要接收的強型別結果集。</span><span class="sxs-lookup"><span data-stu-id="9f454-107">You must use strongly-typed polling in a scenario where you want to receive a strongly-typed result set.</span></span> <span data-ttu-id="9f454-108">如需有關配接器如何支援強型別輪詢的詳細資訊，請參閱[支援的輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。</span><span class="sxs-lookup"><span data-stu-id="9f454-108">For more information on how the adapter supports strongly-typed polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="9f454-109">如果您想要在單一應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分的連線 URI，使其成為唯一的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="9f454-109">If you want to have more than one polling operation in a single application, you must specify an **InboundID** connection property as part of the connection URI to make it unique.</span></span> <span data-ttu-id="9f454-110">您指定的輸入的識別碼會新增至作業命名空間，使其成為唯一。</span><span class="sxs-lookup"><span data-stu-id="9f454-110">The inbound ID you specify is added to the operation namespace to make it unique.</span></span>  

## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="9f454-111">本主題將輪詢的示範</span><span class="sxs-lookup"><span data-stu-id="9f454-111">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="9f454-112">本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援接收強型別資料變更訊息中，建立.NET 應用程式，並產生的 WCF 服務合約**TypedPolling**作業。</span><span class="sxs-lookup"><span data-stu-id="9f454-112">In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving strongly-typed data change messages, create a .NET application and generate the WCF service contract for the **TypedPolling** operation.</span></span> <span data-ttu-id="9f454-113">請確定您指定下列項目時產生 WCF 服務合約：</span><span class="sxs-lookup"><span data-stu-id="9f454-113">Make sure you specify the following while generating the WCF service contract:</span></span>  

- <span data-ttu-id="9f454-114">您必須指定**InboundID**連線 URI 的一部分。</span><span class="sxs-lookup"><span data-stu-id="9f454-114">You must specify an **InboundID** as part of the connection URI.</span></span>  

- <span data-ttu-id="9f454-115">您必須指定輪詢陳述式**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="9f454-115">You must specify a polling statement for the **PollingStatement** binding property.</span></span>  

  <span data-ttu-id="9f454-116">此外，如果您想要指定其他輪詢相關繫結屬性，產生 proxy 類別時指定**PolledDataAvailableStatement**為：</span><span class="sxs-lookup"><span data-stu-id="9f454-116">Additionally, if you want to specify other polling related binding properties while generating the proxy class, specify the **PolledDataAvailableStatement** as:</span></span>  

```  
SELECT COUNT(*) FROM Employee  
```  

 <span data-ttu-id="9f454-117">**PolledDataAvailableStatement**必須傳回含有包含正值的第一個儲存格的結果集。</span><span class="sxs-lookup"><span data-stu-id="9f454-117">The **PolledDataAvailableStatement** must return a result set with the first cell containing a positive value.</span></span> <span data-ttu-id="9f454-118">如果第一個資料格不包含正值，配接器不會執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="9f454-118">If the first cell does not contain a positive value, the adapter does not execute the polling statement.</span></span>  

 <span data-ttu-id="9f454-119">輪詢陳述式的一部分，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="9f454-119">As part of the polling statement, perform the following operations:</span></span>  

1. <span data-ttu-id="9f454-120">從 [員工] 資料表中選取所有資料列。</span><span class="sxs-lookup"><span data-stu-id="9f454-120">Select all the rows from the Employee table.</span></span>  

2. <span data-ttu-id="9f454-121">執行預存程序 (MOVE_EMP_DATA) 將從 Employee 資料表的所有記錄都移至 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-121">Execute a stored procedure (MOVE_EMP_DATA) to move all the records from the Employee table to an EmployeeHistory table.</span></span>  

3. <span data-ttu-id="9f454-122">執行預存程序 (ADD_EMP_DETAILS)，將新記錄新增至 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-122">Execute a stored procedure (ADD_EMP_DETAILS) to add a new record to the Employee table.</span></span> <span data-ttu-id="9f454-123">此程序會接受員工名稱、 指定和薪資做為參數。</span><span class="sxs-lookup"><span data-stu-id="9f454-123">This procedure takes the employee name, designation, and salary as parameters.</span></span>  

   <span data-ttu-id="9f454-124">若要執行這些作業，您必須指定下列**PollingStatement**屬性繫結產生 WCF 服務合約和協助程式類別時：</span><span class="sxs-lookup"><span data-stu-id="9f454-124">To perform these operations, you must specify the following for the **PollingStatement** binding property while generating the WCF service contract and helper classes:</span></span>  

```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  

 <span data-ttu-id="9f454-125">執行輪詢陳述式之後，選取從 Employee 資料表的所有記錄，而且會在收到來自 SQL Server 的訊息。</span><span class="sxs-lookup"><span data-stu-id="9f454-125">After the polling statement is executed, all the records from the Employee table are selected and the message from SQL Server is received.</span></span> <span data-ttu-id="9f454-126">MOVE_EMP_DATA 預存程序執行的配接器之後，所有的記錄會移至 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-126">After the MOVE_EMP_DATA stored procedure is executed by the adapter, all the records are moved to the EmployeeHistory table.</span></span> <span data-ttu-id="9f454-127">然後，會執行 ADD_EMP_DETAILS 預存程序，將新記錄新增至 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-127">Then, the ADD_EMP_DETAILS stored procedure is executed to add a new record to the Employee table.</span></span> <span data-ttu-id="9f454-128">下一個輪詢執行只會傳回單一記錄。</span><span class="sxs-lookup"><span data-stu-id="9f454-128">The next polling execution will only return a single record.</span></span> <span data-ttu-id="9f454-129">此週期會持續直到您關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="9f454-129">This cycle continues until you close the service host.</span></span>  

## <a name="configuring-typed-polling-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="9f454-130">設定 SQL 配接器繫結屬性的型別的輪詢</span><span class="sxs-lookup"><span data-stu-id="9f454-130">Configuring Typed Polling with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="9f454-131">下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="9f454-131">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="9f454-132">以外**PollingStatement**繫結屬性，所有其他繫結屬性列出這一節則需要執行.NET 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="9f454-132">Other than the **PollingStatement** binding property, all the other binding properties listed in this section are required while running the .NET application.</span></span> <span data-ttu-id="9f454-133">您必須指定**PollingStatement**屬性繫結才會產生 WCF 服務合約**TypedPolling**作業。</span><span class="sxs-lookup"><span data-stu-id="9f454-133">You must specify the **PollingStatement** binding property before generating the WCF service contract **TypedPolling** operation.</span></span>  


|         <span data-ttu-id="9f454-134">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="9f454-134">Binding Property</span></span>         |                                                                                                                                                                                                                                                                                              <span data-ttu-id="9f454-135">描述</span><span class="sxs-lookup"><span data-stu-id="9f454-135">Description</span></span>                                                                                                                                                                                                                                                                                              |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     <span data-ttu-id="9f454-136">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="9f454-136">**InboundOperationType**</span></span>     |                                                                                                                                                                                             <span data-ttu-id="9f454-137">指定是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="9f454-137">Specifies whether you want to perform **Polling**, **TypedPolling**, or **Notification** inbound operation.</span></span> <span data-ttu-id="9f454-138">預設值是**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="9f454-138">Default is **Polling**.</span></span> <span data-ttu-id="9f454-139">若要接收強型別輪詢訊息，將此設**TypedPolling**。</span><span class="sxs-lookup"><span data-stu-id="9f454-139">To receive strongly-typed polling messages, set this to **TypedPolling**.</span></span>                                                                                                                                                                                             |
| <span data-ttu-id="9f454-140">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="9f454-140">**PolledDataAvailableStatement**</span></span> |                                                                                                                                           <span data-ttu-id="9f454-141">指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9f454-141">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="9f454-142">SQL 陳述式必須傳回的結果集資料列和資料行所組成。</span><span class="sxs-lookup"><span data-stu-id="9f454-142">The SQL statement must return a result set consisting of rows and columns.</span></span> <span data-ttu-id="9f454-143">如果可用的資料列，為指定的 SQL 陳述式僅**PollingStatement**屬性繫結將會執行。</span><span class="sxs-lookup"><span data-stu-id="9f454-143">Only if a row is available, the SQL statement specified for the **PollingStatement** binding property will be executed.</span></span>                                                                                                                                            |
|   <span data-ttu-id="9f454-144">**PollingIntervalInSeconds**</span><span class="sxs-lookup"><span data-stu-id="9f454-144">**PollingIntervalInSeconds**</span></span>   |                                                                              <span data-ttu-id="9f454-145">指定間隔 （秒），此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="9f454-145">Specifies the interval, in seconds, at which the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="9f454-146">預設值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="9f454-146">The default is 30 seconds.</span></span> <span data-ttu-id="9f454-147">輪詢間隔會決定後續輪詢間隔的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9f454-147">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="9f454-148">如果指定的間隔內執行的陳述式，則配接器會等候剩餘的時間間隔中。</span><span class="sxs-lookup"><span data-stu-id="9f454-148">If the statement is executed within the specified interval, the adapter waits for the remaining time in the interval.</span></span>                                                                              |
|       <span data-ttu-id="9f454-149">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="9f454-149">**PollingStatement**</span></span>       | <span data-ttu-id="9f454-150">指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9f454-150">Specifies the SQL statement to poll the SQL Server database table.</span></span> <span data-ttu-id="9f454-151">您可以指定簡單的 SELECT 陳述式或輪詢陳述式的預存程序。</span><span class="sxs-lookup"><span data-stu-id="9f454-151">You can specify a simple SELECT statement or a stored procedure for the polling statement.</span></span> <span data-ttu-id="9f454-152">預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="9f454-152">The default is null.</span></span> <span data-ttu-id="9f454-153">您必須指定的值**PollingStatement**啟用輪詢。</span><span class="sxs-lookup"><span data-stu-id="9f454-153">You must specify a value for **PollingStatement** to enable polling.</span></span> <span data-ttu-id="9f454-154">輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="9f454-154">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="9f454-155">您可以指定任意數目的 SQL 陳述式以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="9f454-155">You can specify any number of SQL statements separated by a semi-colon.</span></span> <span data-ttu-id="9f454-156">**重要事項︰** For **TypedPolling**，您必須指定這個繫結屬性才能產生中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9f454-156">**Important:**  For **TypedPolling**, you must specify this binding property before generating metadata.</span></span> |
|      <span data-ttu-id="9f454-157">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="9f454-157">**PollWhileDataFound**</span></span>      |                                                                                 <span data-ttu-id="9f454-158">指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並持續執行 SQL 陳述式指定**PolledDataAvailableStatement**繫結屬性，如果資料可在所輪詢的資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-158">Specifies whether the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignores the polling interval and continuously executes the SQL statement specified for the **PolledDataAvailableStatement** binding property, if data is available in the table being polled.</span></span> <span data-ttu-id="9f454-159">如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="9f454-159">If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval.</span></span> <span data-ttu-id="9f454-160">預設值是**false**。</span><span class="sxs-lookup"><span data-stu-id="9f454-160">Default is **false**.</span></span>                                                                                 |

 <span data-ttu-id="9f454-161">如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9f454-161">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="9f454-162">如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]輪詢 SQL Server，可深入閱讀。</span><span class="sxs-lookup"><span data-stu-id="9f454-162">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll SQL Server, read further.</span></span>  

## <a name="configure-strongly-typed-polling-in-the-wcf-service-model"></a><span data-ttu-id="9f454-163">在 WCF 服務模型中設定強型別輪詢</span><span class="sxs-lookup"><span data-stu-id="9f454-163">Configure Strongly-typed Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="9f454-164">若要接收**輪詢**作業使用 WCF 服務模型時，您必須：</span><span class="sxs-lookup"><span data-stu-id="9f454-164">To receive the **Polling** operation when you use the WCF service model, you must:</span></span>  

1. <span data-ttu-id="9f454-165">產生的 WCF 服務合約 （介面），如**TypedPolling**從配接器所公開的中繼資料的作業。</span><span class="sxs-lookup"><span data-stu-id="9f454-165">Generate a WCF service contract (interface) for the **TypedPolling** operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="9f454-166">若要這樣做，您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9f454-166">To do this, you could use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span> <span data-ttu-id="9f454-167">在產生此範例中的 WCF 服務合約時，請確定：</span><span class="sxs-lookup"><span data-stu-id="9f454-167">While generating the WCF service contract for this example, make sure:</span></span>  

   -   <span data-ttu-id="9f454-168">您指定**InboundID**作為**員工**。</span><span class="sxs-lookup"><span data-stu-id="9f454-168">You specify the **InboundID** as **Employee**.</span></span>  

   -   <span data-ttu-id="9f454-169">指定輪詢陳述式**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="9f454-169">You specify a polling statement for the **PollingStatement** binding property.</span></span> <span data-ttu-id="9f454-170">針對此範例中，指定輪詢陳述式，因為：</span><span class="sxs-lookup"><span data-stu-id="9f454-170">For this example, specify the polling statement as:</span></span>  

       ```  
       SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000  
       ```  

2. <span data-ttu-id="9f454-171">實作此介面的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="9f454-171">Implement a WCF service from this interface.</span></span>  

3. <span data-ttu-id="9f454-172">裝載此 WCF 服務，使用服務主機 (**System.ServiceModel.ServiceHost**)。</span><span class="sxs-lookup"><span data-stu-id="9f454-172">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  

## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="9f454-173">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="9f454-173">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="9f454-174">本主題中的範例輪詢 Employee 資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-174">The examples in this topic poll the Employee table.</span></span> <span data-ttu-id="9f454-175">此範例也會使用 MOVE_EMP_DATA 和 ADD_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="9f454-175">The example also uses the MOVE_EMP_DATA and ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="9f454-176">指令碼來產生這些成品會提供範例。</span><span class="sxs-lookup"><span data-stu-id="9f454-176">A script to generate these artifacts is supplied with the samples.</span></span> <span data-ttu-id="9f454-177">如需有關範例的詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="9f454-177">For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="9f454-178">範例中， **TypedPolling_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="9f454-178">A sample, **TypedPolling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  

## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="9f454-179">類別與 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="9f454-179">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="9f454-180">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來建立 WCF 服務合約 （介面） 和支援類別**TypedPolling**作業。</span><span class="sxs-lookup"><span data-stu-id="9f454-180">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **TypedPolling** operation.</span></span> <span data-ttu-id="9f454-181">如需有關如何產生 WCF 服務合約的詳細資訊，請參閱[產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="9f454-181">For more information about generating a WCF service contract, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  

### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="9f454-182">WCF 服務合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="9f454-182">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="9f454-183">下列程式碼示範 WCF 服務合約 （介面） 產生**TypedPolling**作業。</span><span class="sxs-lookup"><span data-stu-id="9f454-183">The following code shows the WCF service contract (interface) generated for the **TypedPolling** operation.</span></span>  

```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="TypedPolling_Employee")]  
public interface TypedPolling_Employee {  

    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee) of message TypedPolling  
    // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="TypedPolling")]  
    void TypedPolling(TypedPolling request);  
}  
```  

### <a name="the-message-contracts"></a><span data-ttu-id="9f454-184">訊息合約</span><span class="sxs-lookup"><span data-stu-id="9f454-184">The Message Contracts</span></span>  
 <span data-ttu-id="9f454-185">訊息合約命名空間會修改**InboundID**中的連線 URI，如果指定的參數。</span><span class="sxs-lookup"><span data-stu-id="9f454-185">The message contract namespace is modified by the **InboundID** parameter in the connection URI, if specified.</span></span> <span data-ttu-id="9f454-186">在此範例中，您已指定為輸入的識別碼**員工**。</span><span class="sxs-lookup"><span data-stu-id="9f454-186">In this example, you specified the inbound ID as **Employee**.</span></span> <span data-ttu-id="9f454-187">要求訊息會傳回強型別結果集。</span><span class="sxs-lookup"><span data-stu-id="9f454-187">The request message returns a strongly-typed result set.</span></span>  

```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="TypedPolling", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", IsWrapped=true)]  
public partial class TypedPolling {  

[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", Order=0)]  
    public schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet0[] TypedPollingResultSet0;  

[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", Order=1)]  
    public schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet1[] TypedPollingResultSet1;  

    public TypedPolling() {  
    }  

    public TypedPolling(schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet0[] TypedPollingResultSet0, schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet1[] TypedPollingResultSet1) {  
        this.TypedPollingResultSet0 = TypedPollingResultSet0;  
        this.TypedPollingResultSet1 = TypedPollingResultSet1;  
    }  
}  
```  

### <a name="wcf-service-class"></a><span data-ttu-id="9f454-188">WCF 服務類別</span><span class="sxs-lookup"><span data-stu-id="9f454-188">WCF Service Class</span></span>  
 <span data-ttu-id="9f454-189">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生已實作服務合約 （介面） 的 WCF 服務類別的虛設常式檔案。</span><span class="sxs-lookup"><span data-stu-id="9f454-189">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="9f454-190">SqlAdapterBindingService.cs 為檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f454-190">The name of the file is SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="9f454-191">您可以插入邏輯來處理**TypedPolling**直接將此類別的作業。</span><span class="sxs-lookup"><span data-stu-id="9f454-191">You can insert the logic to process the **TypedPolling** operation directly into this class.</span></span> <span data-ttu-id="9f454-192">下列程式碼會顯示所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9f454-192">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

```  
namespace SqlAdapterBindingNamespace {  

    public class SqlAdapterBindingService : TypedPolling_Employee {  

        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee) of message TypedPolling  
        // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void TypedPolling(TypedPolling request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  

## <a name="receive-strongly-typed-inbound-messages-for-polling-operation"></a><span data-ttu-id="9f454-193">輪詢作業接收強型別傳入的訊息</span><span class="sxs-lookup"><span data-stu-id="9f454-193">Receive Strongly-typed Inbound Messages for Polling Operation</span></span>  
 <span data-ttu-id="9f454-194">本節說明如何撰寫.NET 應用程式以接收使用的強型別輸入的輪詢訊息[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9f454-194">This section provides instructions on how to write a .NET application to receive strongly-typed inbound polling messages using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

1. <span data-ttu-id="9f454-195">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生的 WCF 服務合約 （介面） 和 helper 類別**TypedPolling**作業。</span><span class="sxs-lookup"><span data-stu-id="9f454-195">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **TypedPolling** operation.</span></span> <span data-ttu-id="9f454-196">請確定您指定下列項目時產生此範例中的 WCF 服務合約：</span><span class="sxs-lookup"><span data-stu-id="9f454-196">Make sure you specify the following while generating the WCF service contract for this example:</span></span>  

   - <span data-ttu-id="9f454-197">您必須指定**InboundID**作為**員工**。</span><span class="sxs-lookup"><span data-stu-id="9f454-197">You must specify the **InboundID** as **Employee**.</span></span>  

   - <span data-ttu-id="9f454-198">您必須指定輪詢陳述式**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="9f454-198">You must specify a polling statement for the **PollingStatement** binding property.</span></span> <span data-ttu-id="9f454-199">針對此範例中，指定輪詢陳述式，因為：</span><span class="sxs-lookup"><span data-stu-id="9f454-199">For this example, specify the polling statement as:</span></span>  

     ```  
     SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000  
     ```  

     <span data-ttu-id="9f454-200">如需詳細資訊，請參閱 <<c0> [ 產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="9f454-200">For more information, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span> <span data-ttu-id="9f454-201">產生服務合約和協助程式類別時，您可以選擇指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="9f454-201">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="9f454-202">這可確保它們已正確設定在產生的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="9f454-202">This guarantees that they are properly set in the generated configuration file.</span></span>  

2. <span data-ttu-id="9f454-203">實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="9f454-203">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="9f454-204">**TypedPolling**此類別的方法可以擲回例外狀況中止輪詢交易，處理從收到的資料時發生錯誤**TypedPolling**作業; 否則為方法沒有傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="9f454-204">The **TypedPolling** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **TypedPolling** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="9f454-205">WCF 服務類別必須屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9f454-205">You must attribute the WCF service class as follows:</span></span>  

   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  

    <span data-ttu-id="9f454-206">內**TypedPolling**方法中，您可以直接實作應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="9f454-206">Within the **TypedPolling** method, you can implement your application logic directly.</span></span> <span data-ttu-id="9f454-207">這個類別可以位於 SqlAdapterBindingService.cs。</span><span class="sxs-lookup"><span data-stu-id="9f454-207">This class can be found in SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="9f454-208">此程式碼，在此範例中的子類別**SqlAdapterBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="9f454-208">This code in this example sub-classes the **SqlAdapterBindingService** class.</span></span> <span data-ttu-id="9f454-209">在此程式碼，做為強型別結果集所收到的輪詢訊息會寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="9f454-209">In this code, the polling message received as a strongly-typed result set is written to the console.</span></span>  

   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  

   public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
   {  
       public override void TypedPolling(TypedPolling request)  
       {  
           Console.WriteLine("\nNew Polling Records Received");  
           Console.WriteLine("*************************************************");  
           Console.WriteLine("Employee ID\tName\tDesignation\tSalary");  

           for (int i = 0; i < request.TypedPollingResultSet0.Length; i++)  
           {  
               Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
               request.TypedPollingResultSet0[i].Employee_ID,  
               request.TypedPollingResultSet0[i].Name,  
               request.TypedPollingResultSet0[i].Designation,  
               request.TypedPollingResultSet0[i].Salary);  
           }  
           Console.WriteLine("*************************************************");  
           Console.WriteLine("\nHit <RETURN> to stop polling");  
       }  
   }  
   ```  

3. <span data-ttu-id="9f454-210">因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]未接受認證的連線 URI 的一部分，您必須實作下列的類別，以 SQL Server 資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="9f454-210">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not accept credentials as part of the connection URI, you must implement the following class to pass credentials for the SQL Server database.</span></span> <span data-ttu-id="9f454-211">在應用程式的後半部，您將會具現化這個類別，以在 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="9f454-211">In the latter part of the application, you will instantiate this class to pass on the SQL Server credentials.</span></span>  

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

4. <span data-ttu-id="9f454-212">建立**SqlAdapterBinding**和設定輪詢作業藉由指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="9f454-212">Create a **SqlAdapterBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="9f454-213">在程式碼中明確或是宣告式組態中，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="9f454-213">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="9f454-214">至少，您必須指定**InboundOperationType**， **PolledDataAvailableStatement**，並**PollingStatement**。</span><span class="sxs-lookup"><span data-stu-id="9f454-214">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement**.</span></span>  

   ```  
   SqlAdapterBinding binding = new SqlAdapterBinding();  
   binding.InboundOperationType = InboundOperation.TypedPolling;  
   binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
   binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
   ```  

5. <span data-ttu-id="9f454-215">指定 SQL Server 資料庫認證，藉由執行個體化**PollingCredentials**您在步驟 3 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="9f454-215">Specify SQL Server database credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  

   ```  
   PollingCredentials credentials = new PollingCredentials();  
   credentials.UserName.UserName = "<Enter user name here>";  
   credentials.UserName.Password = "<Enter password here>";  
   ```  

6. <span data-ttu-id="9f454-216">建立在步驟 2 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f454-216">Create an instance of the WCF service created in step 2.</span></span>  

   ```  
   // create service instance  
   PollingService service = new PollingService();  
   ```  

7. <span data-ttu-id="9f454-217">建立的執行個體**System.ServiceModel.ServiceHost**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="9f454-217">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="9f454-218">基底的連線 URI 不能包含輸入識別碼。</span><span class="sxs-lookup"><span data-stu-id="9f454-218">The base connection URI cannot contain the inbound ID.</span></span> <span data-ttu-id="9f454-219">您也必須指定的認證。</span><span class="sxs-lookup"><span data-stu-id="9f454-219">You must also specify the credentials here.</span></span>  

   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
   ServiceHost serviceHost = new ServiceHost(service, baseUri);  
   serviceHost.Description.Behaviors.Add(credentials);  

   ```  

8. <span data-ttu-id="9f454-220">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="9f454-220">Add a service endpoint to the service host.</span></span> <span data-ttu-id="9f454-221">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="9f454-221">To do this:</span></span>  

   -   <span data-ttu-id="9f454-222">使用在步驟 4 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="9f454-222">Use the binding created in step 4.</span></span>  

   -   <span data-ttu-id="9f454-223">指定連線 URI，其中包含認證並在必要時輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9f454-223">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  

   -   <span data-ttu-id="9f454-224">為 「 TypedPolling_Employee"指定的合約。</span><span class="sxs-lookup"><span data-stu-id="9f454-224">Specify the contract as "TypedPolling_Employee".</span></span>  

   ```  
   // Add service endpoint: be sure to specify TypedPolling_Employee as the contract  
   Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?InboundID=Employee");  
   serviceHost.AddServiceEndpoint("TypedPolling_Employee", binding, ConnectionUri);  
   ```  

9. <span data-ttu-id="9f454-225">若要收到輪詢資料，請開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="9f454-225">To receive polling data, open the service host.</span></span> <span data-ttu-id="9f454-226">每當查詢傳回結果集時，配接器會傳回資料。</span><span class="sxs-lookup"><span data-stu-id="9f454-226">The adapter will return data whenever the query returns a result set.</span></span>  

    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  

10. <span data-ttu-id="9f454-227">若要終止輪詢，關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="9f454-227">To terminate polling, close the service host.</span></span>  

    > [!IMPORTANT]
    >  <span data-ttu-id="9f454-228">配接器將繼續輪詢直到關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="9f454-228">The adapter will continue to poll until the service host is closed.</span></span>  

    ```  
    serviceHost.Close();  
    ```  

### <a name="example"></a><span data-ttu-id="9f454-229">範例</span><span class="sxs-lookup"><span data-stu-id="9f454-229">Example</span></span>  
 <span data-ttu-id="9f454-230">下列範例顯示在有輪詢查詢執行 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-230">The following example shows a polling query that executes the Employee table.</span></span> <span data-ttu-id="9f454-231">輪詢陳述式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="9f454-231">The polling statement performs the following tasks:</span></span>  

1. <span data-ttu-id="9f454-232">從 [員工] 資料表中選取所有記錄。</span><span class="sxs-lookup"><span data-stu-id="9f454-232">Selects all the records from the Employee table.</span></span>  

2. <span data-ttu-id="9f454-233">執行 MOVE_EMP_DATA 預存程序，以從 Employee 資料表的所有記錄都移至 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-233">Executes the MOVE_EMP_DATA stored procedure to move all records from Employee table to EmployeeHistory table.</span></span>  

3. <span data-ttu-id="9f454-234">執行 ADD_EMP_DETAILS 預存程序，將單一記錄新增至 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="9f454-234">Executes the ADD_EMP_DETAILS stored procedure to add a single record to the Employee table.</span></span>  

   <span data-ttu-id="9f454-235">第一次輪詢訊息會包含從 Employee 資料表的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="9f454-235">The first polling message will contain all the records from the Employee table.</span></span> <span data-ttu-id="9f454-236">後續輪詢訊息會包含只有 ADD_EMP_DETAILS 預存程序插入的最後一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="9f454-236">The subsequent polling messages will contain only the last record inserted by the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="9f454-237">配接器將繼續輪詢直到按關閉服務主機`<RETURN>`。</span><span class="sxs-lookup"><span data-stu-id="9f454-237">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  

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

namespace TypedPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  

    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
        public override void TypedPolling(TypedPolling request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Employee ID\tName\tDesignation\tSalary");  

            for (int i = 0; i < request.TypedPollingResultSet0.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.TypedPollingResultSet0[i].Employee_ID,  
                request.TypedPollingResultSet0[i].Name,  
                request.TypedPollingResultSet0[i].Designation,  
                request.TypedPollingResultSet0[i].Salary);  
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
                binding.InboundOperationType = InboundOperation.TypedPolling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
                Console.WriteLine("Binding properties assigned...");  

                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?InboundId=Employee");  

                // This URI is used to initialize the ServiceHost. It cannot contain  
                // the InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  

                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  

                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("TypedPolling_Employee", binding, ConnectionUri);  
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

## <a name="see-also"></a><span data-ttu-id="9f454-238">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f454-238">See Also</span></span>  
 [<span data-ttu-id="9f454-239">使用 WCF 服務模型中的 SQL 配接器的輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="9f454-239">Poll SQL Server using the SQL Adapter with WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)
