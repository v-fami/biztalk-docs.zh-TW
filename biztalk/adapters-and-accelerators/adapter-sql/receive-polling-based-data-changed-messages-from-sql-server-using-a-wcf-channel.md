---
title: 使用 WCF 通道模型，從 SQL Server 接收以輪詢為基礎的資料變更訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0f4af71-fb0c-433d-ba74-48ee6487eb1a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6b87cdb7d36b5f143a833547e4b5522a40e0eb4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987352"
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-by-using-the-wcf-channel-model"></a><span data-ttu-id="f65c5-102">使用 WCF 通道模型，從 SQL Server 接收以輪詢為基礎的資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="f65c5-102">Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model</span></span>
<span data-ttu-id="f65c5-103">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收 SQL Server 資料表或檢視表的定期的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="f65c5-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive periodic data-change messages for SQL Server tables or views.</span></span> <span data-ttu-id="f65c5-104">您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="f65c5-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="f65c5-105">輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="f65c5-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span>  

 <span data-ttu-id="f65c5-106">如需有關配接器如何支援輪詢的詳細資訊，請參閱[支援的輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。</span><span class="sxs-lookup"><span data-stu-id="f65c5-106">For more information on how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="f65c5-107">如果您想要在單一應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分的連線 URI，使其成為唯一的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="f65c5-107">If you want to have more than one polling operation in a single application, you must specify an **InboundID** connection property as part of the connection URI to make it unique.</span></span> <span data-ttu-id="f65c5-108">您指定的輸入的識別碼會新增至作業命名空間，使其成為唯一。</span><span class="sxs-lookup"><span data-stu-id="f65c5-108">The inbound ID you specify is added to the operation namespace to make it unique.</span></span>  

## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="f65c5-109">本主題將輪詢的示範</span><span class="sxs-lookup"><span data-stu-id="f65c5-109">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="f65c5-110">本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援的接收資料變更訊息，請建立.NET 應用程式**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="f65c5-110">In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving data change messages, create a .NET application for the **Polling** operation.</span></span> <span data-ttu-id="f65c5-111">本主題中，指定**PolledDataAvailableStatement**為：</span><span class="sxs-lookup"><span data-stu-id="f65c5-111">For this topic, specify the **PolledDataAvailableStatement** as:</span></span>  

```  
SELECT COUNT(*) FROM Employee  
```  

 <span data-ttu-id="f65c5-112">**PolledDataAvailableStatement**必須傳回含有包含正值的第一個儲存格的結果集。</span><span class="sxs-lookup"><span data-stu-id="f65c5-112">The **PolledDataAvailableStatement** must return a result set with the first cell containing a positive value.</span></span> <span data-ttu-id="f65c5-113">如果第一個資料格不包含正值，配接器不會執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="f65c5-113">If the first cell does not contain a positive value, the adapter does not execute the polling statement.</span></span>  

 <span data-ttu-id="f65c5-114">輪詢陳述式的一部分，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f65c5-114">As part of the polling statement, perform the following operations:</span></span>  

1. <span data-ttu-id="f65c5-115">從 [員工] 資料表中選取所有資料列。</span><span class="sxs-lookup"><span data-stu-id="f65c5-115">Select all the rows from the Employee table.</span></span>  

2. <span data-ttu-id="f65c5-116">執行預存程序 (MOVE_EMP_DATA) 將從 Employee 資料表的所有記錄都移至 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="f65c5-116">Execute a stored procedure (MOVE_EMP_DATA) to move all the records from the Employee table to an EmployeeHistory table.</span></span>  

3. <span data-ttu-id="f65c5-117">執行預存程序 (ADD_EMP_DETAILS)，將新記錄新增至 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="f65c5-117">Execute a stored procedure (ADD_EMP_DETAILS) to add a new record to the Employee table.</span></span> <span data-ttu-id="f65c5-118">此程序會接受員工名稱、 指定和薪資做為參數。</span><span class="sxs-lookup"><span data-stu-id="f65c5-118">This procedure takes the employee name, designation, and salary as parameters.</span></span>  

   <span data-ttu-id="f65c5-119">若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="f65c5-119">To perform these operations, you must specify the following for the **PollingStatement** binding property:</span></span>  

```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  

 <span data-ttu-id="f65c5-120">執行輪詢陳述式之後，選取從 Employee 資料表的所有記錄，而且會在收到來自 SQL Server 的訊息。</span><span class="sxs-lookup"><span data-stu-id="f65c5-120">After the polling statement is executed, all the records from the Employee table are selected and the message from SQL Server is received.</span></span> <span data-ttu-id="f65c5-121">一旦由配接器執行 MOVE_EMP_DATA 預存程序之後，所有的記錄會移至 EmployeeHistory 資料表中。</span><span class="sxs-lookup"><span data-stu-id="f65c5-121">Once the MOVE_EMP_DATA stored procedure is executed by the adapter, all the records are moved to the EmployeeHistory table.</span></span> <span data-ttu-id="f65c5-122">然後，會執行 ADD_EMP_DETAILS 預存程序，將新記錄新增至 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="f65c5-122">Then, the ADD_EMP_DETAILS stored procedure is executed to add a new record to the Employee table.</span></span> <span data-ttu-id="f65c5-123">下一個輪詢執行只會傳回單一記錄。</span><span class="sxs-lookup"><span data-stu-id="f65c5-123">The next polling execution will only return a single record.</span></span> <span data-ttu-id="f65c5-124">此週期會持續直到您關閉通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="f65c5-124">This cycle continues until you close the channel listener.</span></span>  

## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="f65c5-125">使用 SQL 配接器繫結屬性中設定輪詢查詢</span><span class="sxs-lookup"><span data-stu-id="f65c5-125">Configuring a Polling Query with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="f65c5-126">下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="f65c5-126">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="f65c5-127">輪詢的.NET 應用程式的一部分，您必須指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f65c5-127">You must specify these binding properties as part of the .NET application for polling.</span></span>  


|         <span data-ttu-id="f65c5-128">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="f65c5-128">Binding Property</span></span>         |                                                                                                                                                                                                                                         <span data-ttu-id="f65c5-129">描述</span><span class="sxs-lookup"><span data-stu-id="f65c5-129">Description</span></span>                                                                                                                                                                                                                                          |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     <span data-ttu-id="f65c5-130">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="f65c5-130">**InboundOperationType**</span></span>     |                                                                                                                                                                             <span data-ttu-id="f65c5-131">指定是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="f65c5-131">Specifies whether you want to perform **Polling**, **TypedPolling**, or **Notification** inbound operation.</span></span> <span data-ttu-id="f65c5-132">預設值是**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="f65c5-132">Default is **Polling**.</span></span>                                                                                                                                                                              |
| <span data-ttu-id="f65c5-133">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="f65c5-133">**PolledDataAvailableStatement**</span></span> |                                                                                       <span data-ttu-id="f65c5-134">指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f65c5-134">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="f65c5-135">SQL 陳述式必須傳回的結果集資料列和資料行所組成。</span><span class="sxs-lookup"><span data-stu-id="f65c5-135">The SQL statement must return a result set consisting of rows and columns.</span></span> <span data-ttu-id="f65c5-136">如果可用的資料列，為指定的 SQL 陳述式僅**PollingStatement**屬性繫結將會執行。</span><span class="sxs-lookup"><span data-stu-id="f65c5-136">Only if a row is available, the SQL statement specified for the **PollingStatement** binding property will be executed.</span></span>                                                                                       |
|   <span data-ttu-id="f65c5-137">**PollingIntervalInSeconds**</span><span class="sxs-lookup"><span data-stu-id="f65c5-137">**PollingIntervalInSeconds**</span></span>   |                         <span data-ttu-id="f65c5-138">指定間隔 （秒），此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f65c5-138">Specifies the interval, in seconds, at which the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="f65c5-139">預設值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="f65c5-139">The default is 30 seconds.</span></span> <span data-ttu-id="f65c5-140">輪詢間隔會決定後續輪詢間隔的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f65c5-140">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="f65c5-141">如果指定的間隔內執行的陳述式，則配接器會等候剩餘的時間間隔中。</span><span class="sxs-lookup"><span data-stu-id="f65c5-141">If the statement is executed within the specified interval, the adapter waits for the remaining time in the interval.</span></span>                          |
|       <span data-ttu-id="f65c5-142">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="f65c5-142">**PollingStatement**</span></span>       | <span data-ttu-id="f65c5-143">指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f65c5-143">Specifies the SQL statement to poll the SQL Server database table.</span></span> <span data-ttu-id="f65c5-144">您可以指定簡單的 SELECT 陳述式或輪詢陳述式的預存程序。</span><span class="sxs-lookup"><span data-stu-id="f65c5-144">You can specify a simple SELECT statement or a stored procedure for the polling statement.</span></span> <span data-ttu-id="f65c5-145">預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="f65c5-145">The default is null.</span></span> <span data-ttu-id="f65c5-146">您必須指定的值**PollingStatement**啟用輪詢。</span><span class="sxs-lookup"><span data-stu-id="f65c5-146">You must specify a value for **PollingStatement** to enable polling.</span></span> <span data-ttu-id="f65c5-147">輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f65c5-147">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="f65c5-148">您可以指定任意數目的 SQL 陳述式以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="f65c5-148">You can specify any number of SQL statements separated by a semi-colon.</span></span> |
|      <span data-ttu-id="f65c5-149">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="f65c5-149">**PollWhileDataFound**</span></span>      |                            <span data-ttu-id="f65c5-150">指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並持續執行 SQL 陳述式指定**PolledDataAvailableStatement**繫結屬性，如果資料可在所輪詢的資料表。</span><span class="sxs-lookup"><span data-stu-id="f65c5-150">Specifies whether the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignores the polling interval and continuously executes the SQL statement specified for the **PolledDataAvailableStatement** binding property, if data is available in the table being polled.</span></span> <span data-ttu-id="f65c5-151">如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="f65c5-151">If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval.</span></span> <span data-ttu-id="f65c5-152">預設值是**false**。</span><span class="sxs-lookup"><span data-stu-id="f65c5-152">Default is **false**.</span></span>                             |

 <span data-ttu-id="f65c5-153">如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f65c5-153">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="f65c5-154">如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]若要輪詢 SQL Server，請參閱本主題的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="f65c5-154">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll SQL Server, read the remainder of this topic.</span></span>  

## <a name="consuming-the-polling-request-message"></a><span data-ttu-id="f65c5-155">使用輪詢要求訊息</span><span class="sxs-lookup"><span data-stu-id="f65c5-155">Consuming the Polling Request Message</span></span>  
 <span data-ttu-id="f65c5-156">配接器會叫用**輪詢**在您的程式碼，以輪詢 SQL Server 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="f65c5-156">The adapter invokes the **Polling** operation on your code to poll the SQL Server database.</span></span> <span data-ttu-id="f65c5-157">也就是配接器會傳送您所收到的輪詢要求訊息透過 IInputChannel 通道組織結構。</span><span class="sxs-lookup"><span data-stu-id="f65c5-157">That is, the adapter sends a Polling request message that you receive over an IInputChannel channel shape.</span></span> <span data-ttu-id="f65c5-158">輪詢要求訊息包含 PollingStatement 繫結屬性所指定之查詢的結果集。</span><span class="sxs-lookup"><span data-stu-id="f65c5-158">The Polling request message contains the result set of the query specified by the PollingStatement binding property.</span></span> <span data-ttu-id="f65c5-159">您可以使用輪詢訊息中有兩種：</span><span class="sxs-lookup"><span data-stu-id="f65c5-159">You can consume the Polling message in one of two ways:</span></span>  

-   <span data-ttu-id="f65c5-160">若要使用訊息使用節點值串流，您必須呼叫**WriteBodyContents**方法的回應訊息，並將它傳遞**XmlDictionaryWriter**實作資料流處理的節點值。</span><span class="sxs-lookup"><span data-stu-id="f65c5-160">To consume the message using node-value streaming you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  

-   <span data-ttu-id="f65c5-161">若要取用使用節點資料流處理的訊息，您可以呼叫**GetReaderAtBodyContents**回應訊息，可取得**XmlReader**。</span><span class="sxs-lookup"><span data-stu-id="f65c5-161">To consume the message using node streaming you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.</span></span>  

## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="f65c5-162">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="f65c5-162">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="f65c5-163">本主題中的範例輪詢 Employee 資料表。</span><span class="sxs-lookup"><span data-stu-id="f65c5-163">The examples in this topic poll the Employee table.</span></span> <span data-ttu-id="f65c5-164">此範例也會使用 MOVE_EMP_DATA 和 ADD_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="f65c5-164">The example also uses the MOVE_EMP_DATA and ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="f65c5-165">指令碼來產生這些成品會提供範例。</span><span class="sxs-lookup"><span data-stu-id="f65c5-165">A script to generate these artifacts is supplied with the samples.</span></span> <span data-ttu-id="f65c5-166">如需有關範例的詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f65c5-166">For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="f65c5-167">範例中， **Polling_ChannelModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="f65c5-167">A sample, **Polling_ChannelModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  

## <a name="receiving-inbound-messages-for-polling-operation-using-the-wcf-channel-model"></a><span data-ttu-id="f65c5-168">使用 WCF 通道模型的輪詢作業接收內送的訊息</span><span class="sxs-lookup"><span data-stu-id="f65c5-168">Receiving Inbound Messages for Polling Operation Using the WCF Channel Model</span></span>  
 <span data-ttu-id="f65c5-169">本節說明如何撰寫.NET 應用程式 （通道模型），以接收輸入的輪詢訊息使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f65c5-169">This section provides instructions on how to write a .NET application (channel model) to receive inbound polling messages using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  

#### <a name="to-receive-polling-messages-from-the-sql-adapter"></a><span data-ttu-id="f65c5-170">若要從 SQL 配接器接收輪詢訊息</span><span class="sxs-lookup"><span data-stu-id="f65c5-170">To receive polling messages from the SQL adapter</span></span>  

1. <span data-ttu-id="f65c5-171">Microsoft Visual C# 中建立的專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f65c5-171">Create a Microsoft Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="f65c5-172">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="f65c5-172">For this topic, create a console application.</span></span>  

2. <span data-ttu-id="f65c5-173">在 [方案總管] 中，加入參考`Microsoft.Adapters.Sql`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。</span><span class="sxs-lookup"><span data-stu-id="f65c5-173">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  

3. <span data-ttu-id="f65c5-174">開啟 Program.cs 檔案並新增下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="f65c5-174">Open the Program.cs file and add the following namespaces:</span></span>  

   -   `Microsoft.Adapters.Sql`  

   -   `System.ServiceModel`  

   -   `System.ServiceModel.Description`  

   -   `System.ServiceModel.Channels`  

   -   `System.Xml`  

4. <span data-ttu-id="f65c5-175">指定連線 URI。</span><span class="sxs-lookup"><span data-stu-id="f65c5-175">Specify a connection URI.</span></span> <span data-ttu-id="f65c5-176">如需配接器連線 URI 的詳細資訊，請參閱[建立 SQL Server 連接 URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="f65c5-176">For more information about the adapter connection URI, see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).</span></span>  

   ```  
   Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
   ```  

5. <span data-ttu-id="f65c5-177">建立的執行個體**SqlAdapterBinding**和設定必要設定輪詢的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f65c5-177">Create an instance of **SqlAdapterBinding** and set the binding properties required to configure polling.</span></span> <span data-ttu-id="f65c5-178">您必須設定至少**InboundOperationType**， **PolledDataAvailableStatement**，並**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f65c5-178">At a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement** binding properties.</span></span> <span data-ttu-id="f65c5-179">如需有關用來設定輪詢的屬性繫結的詳細資訊，請參閱[支援的輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。</span><span class="sxs-lookup"><span data-stu-id="f65c5-179">For more information about binding properties used to configure polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  

   ```  
   SqlAdapterBinding binding = new SqlAdapterBinding();  
   binding.InboundOperationType = InboundOperation.Polling;  
   binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
   binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
   ```  

6. <span data-ttu-id="f65c5-180">建立繫結參數集合，並設定認證。</span><span class="sxs-lookup"><span data-stu-id="f65c5-180">Create a binding parameter collection and set the credentials.</span></span>  

   ```  
   ClientCredentials credentials = new ClientCredentials();  
   credentials.UserName.UserName = "<Enter user name here>";  
   credentials.UserName.Password = "<Enter password here>";  

   BindingParameterCollection bindingParams = new BindingParameterCollection();  
   bindingParams.Add(credentials);  
   ```  

7. <span data-ttu-id="f65c5-181">建立通道接聽程式，然後開啟它。</span><span class="sxs-lookup"><span data-stu-id="f65c5-181">Create a channel listener and open it.</span></span> <span data-ttu-id="f65c5-182">您可以建立接聽程式所叫用**BuildChannelListener < IInputChannel\>** 方法**SqlAdapterBinding**。</span><span class="sxs-lookup"><span data-stu-id="f65c5-182">You create the listener by invoking **BuildChannelListener<IInputChannel\>** method on the **SqlAdapterBinding**.</span></span>  

   ```  
   IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
   listener.Open();  
   ```  

8. <span data-ttu-id="f65c5-183">取得**IInputChannel**藉由叫用的通道**AcceptChannel**接聽程式上的方法並將它開啟。</span><span class="sxs-lookup"><span data-stu-id="f65c5-183">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on the listener and open it.</span></span>  

   ```  
   IInputChannel channel = listener.AcceptChannel();  
   channel.Open();  
   ```  

9. <span data-ttu-id="f65c5-184">叫用**接收**從配接器取得的下一個 POLLINGSTMT 訊息的通道上。</span><span class="sxs-lookup"><span data-stu-id="f65c5-184">Invoke **Receive** on the channel to get the next POLLINGSTMT message from the adapter.</span></span>  

    ```  
    Message message = channel.Receive();  
    ```  

10. <span data-ttu-id="f65c5-185">取用 POLLINGSTMT 作業所傳回的結果集。</span><span class="sxs-lookup"><span data-stu-id="f65c5-185">Consume the result set returned by the POLLINGSTMT operation.</span></span> <span data-ttu-id="f65c5-186">您可以使用使用訊息**XmlReader**該**XmlDictionaryWriter**。</span><span class="sxs-lookup"><span data-stu-id="f65c5-186">You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.</span></span>  

    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  

11. <span data-ttu-id="f65c5-187">當您完成處理要求，請關閉通道。</span><span class="sxs-lookup"><span data-stu-id="f65c5-187">Close the channel when you have completed processing the request.</span></span>  

    ```  
    channel.Close()  
    ```  

    > [!IMPORTANT]
    >  <span data-ttu-id="f65c5-188">處理 POLLINGSTMT 作業完成之後，您必須關閉通道。</span><span class="sxs-lookup"><span data-stu-id="f65c5-188">You must close the channel after you have finished processing the POLLINGSTMT operation.</span></span> <span data-ttu-id="f65c5-189">若要關閉通道的失敗可能會影響您的程式碼的行為。</span><span class="sxs-lookup"><span data-stu-id="f65c5-189">Failure to close the channel may affect the behavior of your code.</span></span>  

12. <span data-ttu-id="f65c5-190">當您完成接收的資料變更訊息時，請關閉接聽程式。</span><span class="sxs-lookup"><span data-stu-id="f65c5-190">Close the listener when you are finished receiving data-changed messages.</span></span>  

    ```  
    listener.Close()  
    ```  

    > [!IMPORTANT]
    >  <span data-ttu-id="f65c5-191">關閉接聽程式不會關閉建立使用接聽程式通道。</span><span class="sxs-lookup"><span data-stu-id="f65c5-191">Closing the listener does not close channels created using the listener.</span></span> <span data-ttu-id="f65c5-192">您必須明確地關閉每一個色頻建立使用接聽程式。</span><span class="sxs-lookup"><span data-stu-id="f65c5-192">You must explicitly close each channel created using the listener.</span></span>  

### <a name="example"></a><span data-ttu-id="f65c5-193">範例</span><span class="sxs-lookup"><span data-stu-id="f65c5-193">Example</span></span>  
 <span data-ttu-id="f65c5-194">下列範例顯示在有輪詢查詢執行 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="f65c5-194">The following example shows a polling query that executes the Employee table.</span></span> <span data-ttu-id="f65c5-195">輪詢陳述式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f65c5-195">The polling statement performs the following tasks:</span></span>  

- <span data-ttu-id="f65c5-196">從 [員工] 資料表中選取所有記錄。</span><span class="sxs-lookup"><span data-stu-id="f65c5-196">Selects all the records from the Employee table.</span></span>  

- <span data-ttu-id="f65c5-197">執行 MOVE_EMP_DATA 預存程序，以從 Employee 資料表的所有記錄都移至 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="f65c5-197">Executes the MOVE_EMP_DATA stored procedure to move all records from Employee table to EmployeeHistory table.</span></span>  

- <span data-ttu-id="f65c5-198">執行 ADD_EMP_DETAILS 預存程序，將單一記錄新增至 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="f65c5-198">Executes the ADD_EMP_DETAILS stored procedure to add a single record to the Employee table.</span></span>  

  <span data-ttu-id="f65c5-199">輪詢訊息儲存在`C:\PollingOutput.xml`。</span><span class="sxs-lookup"><span data-stu-id="f65c5-199">The polling messages are saved at `C:\PollingOutput.xml`.</span></span>  

```  
using System;  
using Microsoft.Adapters.Sql;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  

using System.Xml;  

namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("Sample started. This sample will poll 5 times and will perform the following tasks:");  
            Console.WriteLine("Press any key to start polling...");  
            Console.ReadLine();  
            IChannelListener<IInputChannel> listener = null;  

            IInputChannel channel = null;  

            try  
            {  
                TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  

                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  

                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  

                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  

                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  

                listener = binding.BuildChannelListener<IInputChannel>(ConnectionUri, bindingParams);  
                listener.Open();  

                channel = listener.AcceptChannel();  
                channel.Open();  

                Console.WriteLine("Channel and Listener opened...");  
                Console.WriteLine("\nWaiting for polled data...");  
                Console.WriteLine("Receive request timeout is {0}", messageTimeout);  

                // Poll five times with the specified message timeout   
                // If a timeout occurs polling will be aborted  
                for (int i = 0; i < 5; i++)  
                {  
                    Console.WriteLine("Polling: " + i);  
                    Message message = null;  
                    XmlReader reader = null;  
                    try  
                    {  
                        //Message is received so process the results  
                        message = channel.Receive(messageTimeout);  
                    }  
                    catch (System.TimeoutException toEx)  
                    {  
                        Console.WriteLine("\nNo data for request number {0}: {1}", i + 1, toEx.Message);  
                        continue;  
                    }  

                    // Get the query results using an XML reader  
                    try  
                    {  
                        reader = message.GetReaderAtBodyContents();  
                    }  
                    catch (Exception ex)  
                    {  
                        Console.WriteLine("Exception :" + ex);  
                        throw;  
                    }  

                    XmlDocument doc = new XmlDocument();  
                    doc.Load(reader);  
                    using (XmlWriter writer = XmlWriter.Create("C:\\PollingOutput.xml"))  
                    {  
                        doc.WriteTo(writer);  
                        Console.WriteLine("The polling response is saved at 'C:\\PollingOutput.xml'");  
                    }  

                    // return the cursor  
                    Console.WriteLine();  

                    // close the reader  
                    reader.Close();  

                    message.Close();  
                }  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // IMPORTANT: close the channel and listener to stop polling  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  

                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  

```  

## <a name="see-also"></a><span data-ttu-id="f65c5-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f65c5-200">See Also</span></span>  
[<span data-ttu-id="f65c5-201">開發 SQL 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="f65c5-201">Develop SQL applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)