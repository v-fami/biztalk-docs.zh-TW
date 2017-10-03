---
title: "使用 BizTalk Server 從 SQL Server 接收輪詢基礎資料變更的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ecaf6f7-974b-4487-8c65-d1ab628cbfeb
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b86a58a092f5f38c4a09c014feb0b4fe85d1fc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-from-sql-server-using-biztalk-server"></a><span data-ttu-id="419a3-102">使用 BizTalk Server 從 SQL Server 接收輪詢基礎資料變更的訊息</span><span class="sxs-lookup"><span data-stu-id="419a3-102">Receive Polling-based Data-changed Messages from SQL Server using BizTalk Server</span></span>
<span data-ttu-id="419a3-103">您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收 SQL Server 資料表或檢視表的週期性的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="419a3-103">You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive periodic data-change messages for SQL Server tables or views.</span></span> <span data-ttu-id="419a3-104">您可以指定執行以輪詢資料庫配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-104">You can specify a polling statement that the adapter executes to poll the database.</span></span> <span data-ttu-id="419a3-105">輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="419a3-105">The polling statement can be a SELECT statement or a stored procedure that returns a result set.</span></span>  

  
 <span data-ttu-id="419a3-106">如需有關如何配接器支援在輪詢的詳細資訊，請參閱[支援輪詢](https://msdn.microsoft.com/library/dd788416.aspx)。</span><span class="sxs-lookup"><span data-stu-id="419a3-106">For more information on how the adapter supports polling, see [Support for Polling](https://msdn.microsoft.com/library/dd788416.aspx).</span></span> <span data-ttu-id="419a3-107">輪詢作業的 SOAP 訊息結構的相關資訊，請參閱[輪詢和 TypedPolling 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-107">For information about the structure of the SOAP message for polling operations, see [Message Schemas for the Polling and TypedPolling Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="419a3-108">本主題示範如何使用**輪詢**輸入作業使用輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="419a3-108">This topic demonstrates how to use the **Polling** inbound operation to use polling messages.</span></span> <span data-ttu-id="419a3-109">輪詢作業的訊息不是強型別，以及在執行階段訊息擷取輪詢的物件結構描述。</span><span class="sxs-lookup"><span data-stu-id="419a3-109">The message for the Polling operation is not strongly-typed and schema of the object being polled is retrieved along with the message at run-time.</span></span> <span data-ttu-id="419a3-110">如果您想要取得強型別輪詢訊息，您必須使用**TypedPolling**作業。</span><span class="sxs-lookup"><span data-stu-id="419a3-110">If you want to get strongly-typed polling message, you must use the **TypedPolling** operation.</span></span> <span data-ttu-id="419a3-111">您也必須使用**TypedPolling**作業使用單一的 BizTalk 應用程式中的多個輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="419a3-111">You must also use the **TypedPolling** operation to have multiple polling operations in a single BizTalk application.</span></span> <span data-ttu-id="419a3-112">如需有關如何執行指示**TypedPolling**作業，請參閱[接收強型別輪詢基礎資料變更訊息從 SQL Server 使用 BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-112">For instructions on how to perform **TypedPolling** operation, see [Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="419a3-113">如果您想要在單一的 BizTalk 應用程式中有一個以上的輪詢作業，您必須指定**InboundID**一部分連線 URI 成為唯一的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-113">If you want to have more than one polling operation in a single BizTalk application, you must specify an **InboundID** connection property as part of the connection URI to make it unique.</span></span> <span data-ttu-id="419a3-114">使用一個唯一的連接 URI，您可以建立多個接收輪詢相同的資料庫或甚至相同資料庫的資料表中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-114">With a unique connection URI, you can create multiple receive ports that poll the same database, or even the same table in a database.</span></span> <span data-ttu-id="419a3-115">如需詳細資訊，請參閱[收到輪詢訊息跨多個接收埠使用 BizTalk Server 的 sql](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-115">For more information, see [Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md).</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="419a3-116">本主題示範輪詢的方式</span><span class="sxs-lookup"><span data-stu-id="419a3-116">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="419a3-117">本主題中，以示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收資料的支援變更訊息、 建立 BizTalk 專案和產生結構描述的**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="419a3-117">In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving data change messages, create a BizTalk project and generate schema for the **Polling** operation.</span></span> <span data-ttu-id="419a3-118">如果您想要指定輪詢相關設計階段繫結屬性，指定**PolledDataAvailableStatement**為：</span><span class="sxs-lookup"><span data-stu-id="419a3-118">If you want to specify the polling related binding properties at design time, specify the **PolledDataAvailableStatement** as:</span></span>  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 <span data-ttu-id="419a3-119">**PolledDataAvailableStatement**必須傳回一個結果集包含正值的第一個儲存格。</span><span class="sxs-lookup"><span data-stu-id="419a3-119">The **PolledDataAvailableStatement** must return a result set with the first cell containing a positive value.</span></span> <span data-ttu-id="419a3-120">如果第一個資料格不包含正值，配接器不會執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-120">If the first cell does not contain a positive value, the adapter does not execute the polling statement.</span></span>  
  
 <span data-ttu-id="419a3-121">輪詢陳述式的一部分，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="419a3-121">As part of the polling statement, perform the following operations:</span></span>  
  
-   <span data-ttu-id="419a3-122">選取從 Employee 資料表的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="419a3-122">Select all the rows from the Employee table.</span></span>  
  
-   <span data-ttu-id="419a3-123">執行預存程序 (MOVE_EMP_DATA) 會將所有的記錄從 Employee 資料表 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="419a3-123">Execute a stored procedure (MOVE_EMP_DATA) to move all the records from the Employee table to an EmployeeHistory table.</span></span>  
  
-   <span data-ttu-id="419a3-124">執行預存程序 (ADD_EMP_DETAILS) Employee 資料表中加入新的記錄。</span><span class="sxs-lookup"><span data-stu-id="419a3-124">Execute a stored procedure (ADD_EMP_DETAILS) to add a new record to the Employee table.</span></span> <span data-ttu-id="419a3-125">此程序會接受員工名稱、 指定和薪資做為參數。</span><span class="sxs-lookup"><span data-stu-id="419a3-125">This procedure takes the employee name, designation, and salary as parameters.</span></span>  
  
 <span data-ttu-id="419a3-126">若要執行這些作業，您必須指定下列**PollingStatement**繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="419a3-126">To perform these operations, you must specify the following for the **PollingStatement** binding property:</span></span>  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 <span data-ttu-id="419a3-127">執行輪詢陳述式之後，選取從 Employee 資料表的所有記錄，則從 SQL Server 會捨棄訊息至接收位置。</span><span class="sxs-lookup"><span data-stu-id="419a3-127">After the polling statement is executed, all the records from the Employee table are selected and the message from SQL Server is dropped to a receive location.</span></span> <span data-ttu-id="419a3-128">一旦執行 MOVE_EMP_DATA 預存程序之後，配接器，所有的記錄會移至 EmployeeHistory 資料表。</span><span class="sxs-lookup"><span data-stu-id="419a3-128">Once the MOVE_EMP_DATA stored procedure is executed by the adapter, all the records are moved to the EmployeeHistory table.</span></span> <span data-ttu-id="419a3-129">然後，ADD_EMP_DETAILS 預存程序會執行以將新記錄新增至 Employee 資料表。</span><span class="sxs-lookup"><span data-stu-id="419a3-129">Then, the ADD_EMP_DETAILS stored procedure is executed to add a new record to the Employee table.</span></span> <span data-ttu-id="419a3-130">下次輪詢執行只會傳回單一記錄。</span><span class="sxs-lookup"><span data-stu-id="419a3-130">The next polling execution will only return a single record.</span></span> <span data-ttu-id="419a3-131">此週期會繼續執行，直到您停用接收輪詢 SQL Server 的連接埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-131">This cycle continues until you disable the receive port that polls SQL Server.</span></span>  
  
## <a name="configuring-a-polling-query-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="419a3-132">使用 SQL 配接器繫結屬性中設定輪詢查詢</span><span class="sxs-lookup"><span data-stu-id="419a3-132">Configuring a Polling Query with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="419a3-133">下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結，您用來設定配接器來接收資料變更訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-133">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="419a3-134">您必須同時設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="419a3-134">You must specify these binding properties while configuring the receive port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="419a3-135">您可以選擇指定這些繫結內容產生的結構描述時**輪詢**作業，即使它不是強制性。</span><span class="sxs-lookup"><span data-stu-id="419a3-135">You may choose to specify these binding properties when generating the schema for the **Polling** operation, even though it is not mandatory.</span></span> <span data-ttu-id="419a3-136">如果您這樣做，連接埠繫結檔，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="419a3-136">If you do so, the port binding file that the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] generates as part of the metadata generation also contains the values you specify for the binding properties.</span></span> <span data-ttu-id="419a3-137">您可以稍後匯入此繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 wcf-custom 或 WCF SQL 接收埠以繫結已設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-137">You can later import this binding file in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create the WCF-custom or WCF-SQL receive port with the binding properties already set.</span></span> <span data-ttu-id="419a3-138">如需有關如何建立使用該繫結檔案的連接埠的詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-138">For more information about creating a port using the binding file, see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span>  
  
|<span data-ttu-id="419a3-139">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="419a3-139">Binding Property</span></span>|<span data-ttu-id="419a3-140">Description</span><span class="sxs-lookup"><span data-stu-id="419a3-140">Description</span></span>|  
|---|---|  
|<span data-ttu-id="419a3-141">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="419a3-141">**InboundOperationType**</span></span>|<span data-ttu-id="419a3-142">指定您是否要執行**輪詢**， **TypedPolling**，或**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="419a3-142">Specifies whether you want to perform **Polling**, **TypedPolling**, or **Notification** inbound operation.</span></span> <span data-ttu-id="419a3-143">預設值是**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="419a3-143">Default is **Polling**.</span></span>|  
|<span data-ttu-id="419a3-144">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="419a3-144">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="419a3-145">指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。</span><span class="sxs-lookup"><span data-stu-id="419a3-145">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="419a3-146">SQL 陳述式必須傳回的結果集資料列和資料行所組成。</span><span class="sxs-lookup"><span data-stu-id="419a3-146">The SQL statement must return a result set consisting of rows and columns.</span></span> <span data-ttu-id="419a3-147">只有一個資料列是否可用，SQL 陳述式指定**PollingStatement**繫結屬性將會執行。</span><span class="sxs-lookup"><span data-stu-id="419a3-147">Only if a row is available, the SQL statement specified for the **PollingStatement** binding property will be executed.</span></span>|  
|<span data-ttu-id="419a3-148">**PollingIntervalInSeconds**</span><span class="sxs-lookup"><span data-stu-id="419a3-148">**PollingIntervalInSeconds**</span></span>|<span data-ttu-id="419a3-149">指定間隔，以秒為單位，此時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-149">Specifies the interval, in seconds, at which the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="419a3-150">預設值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="419a3-150">The default is 30 seconds.</span></span> <span data-ttu-id="419a3-151">輪詢間隔會決定後續輪詢間隔時間。</span><span class="sxs-lookup"><span data-stu-id="419a3-151">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="419a3-152">如果指定的間隔內執行的陳述式，則配接器就會等候剩餘的時間間隔中。</span><span class="sxs-lookup"><span data-stu-id="419a3-152">If the statement is executed within the specified interval, the adapter waits for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="419a3-153">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="419a3-153">**PollingStatement**</span></span>|<span data-ttu-id="419a3-154">指定輪詢 SQL Server 資料庫資料表的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-154">Specifies the SQL statement to poll the SQL Server database table.</span></span> <span data-ttu-id="419a3-155">您可以指定簡單的 SELECT 陳述式或預存程序輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-155">You can specify a simple SELECT statement or a stored procedure for the polling statement.</span></span> <span data-ttu-id="419a3-156">預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="419a3-156">The default is null.</span></span> <span data-ttu-id="419a3-157">您必須指定的值**PollingStatement**來啟用輪詢。</span><span class="sxs-lookup"><span data-stu-id="419a3-157">You must specify a value for **PollingStatement** to enable polling.</span></span> <span data-ttu-id="419a3-158">輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-158">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="419a3-159">您可以指定任意數目的 SQL 陳述式以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="419a3-159">You can specify any number of SQL statements separated by a semi-colon.</span></span>|  
|<span data-ttu-id="419a3-160">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="419a3-160">**PollWhileDataFound**</span></span>|<span data-ttu-id="419a3-161">指定是否[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]忽略的輪詢間隔，並為指定的 SQL 陳述式會持續執行**PolledDataAvailableStatement**如果輪詢資料表中的資料可繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-161">Specifies whether the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignores the polling interval and continuously executes the SQL statement specified for the **PolledDataAvailableStatement** binding property, if data is available in the table being polled.</span></span> <span data-ttu-id="419a3-162">如果沒有資料可在資料表中，配接器會還原為執行 SQL 陳述式，在指定的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="419a3-162">If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval.</span></span> <span data-ttu-id="419a3-163">預設值是**false**。</span><span class="sxs-lookup"><span data-stu-id="419a3-163">Default is **false**.</span></span>|  
  
 <span data-ttu-id="419a3-164">如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-164">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="419a3-165">如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]進一步來輪詢 SQL Server，請閱讀。</span><span class="sxs-lookup"><span data-stu-id="419a3-165">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll SQL Server, read further.</span></span>  
  
## <a name="how-to-receive-data-change-messages-from-the-sql-server-database"></a><span data-ttu-id="419a3-166">如何接收來自 SQL Server 資料庫的資料變更訊息</span><span class="sxs-lookup"><span data-stu-id="419a3-166">How to Receive Data-change Messages from the SQL Server Database</span></span>  
 <span data-ttu-id="419a3-167">使用 SQL Server 資料庫上執行操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及程序中所述的工作[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-167">Performing an operation on the SQL Server database using [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves the procedural tasks described in [Building blocks to develop BizTalk applications with the SQL adapter](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md).</span></span> <span data-ttu-id="419a3-168">若要設定要接收的資料變更訊息的介面卡，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="419a3-168">To configure the adapter to receive data-change messages, these tasks are:</span></span>  
  
1.  <span data-ttu-id="419a3-169">建立 BizTalk 專案，然後再產生結構描述的**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="419a3-169">Create a BizTalk project, and then generate schema for the **Polling** operation.</span></span> <span data-ttu-id="419a3-170">您可以選擇性地指定值**PolledDataAvailableStatement**和**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-170">Optionally, you can specify values for the **PolledDataAvailableStatement** and **PollingStatement** binding properties.</span></span>  
  
2.  <span data-ttu-id="419a3-171">從 SQL Server 資料庫接收訊息的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="419a3-171">Create a message in the BizTalk project for receiving messages from the SQL Server database.</span></span>  
  
3.  <span data-ttu-id="419a3-172">建立協調流程接收訊息，從 SQL Server 資料庫，並將它們儲存到資料夾。</span><span class="sxs-lookup"><span data-stu-id="419a3-172">Create an orchestration to receive messages from the SQL Server database and to save them to a folder.</span></span>  
  
4.  <span data-ttu-id="419a3-173">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="419a3-173">Build and deploy the BizTalk project.</span></span>  
  
5.  <span data-ttu-id="419a3-174">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-174">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="419a3-175">輸入的輪詢案例對於您永遠必須設定單向的 WCF 自訂或 WCF SQL 接收埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-175">For inbound polling scenarios you must always configure a one-way WCF-Custom or WCF-SQL receive port.</span></span> <span data-ttu-id="419a3-176">雙向 Wcf-custom 或 WCF SQL 接收埠的輸入作業不支援。</span><span class="sxs-lookup"><span data-stu-id="419a3-176">Two-way WCF-Custom or WCF-SQL receive ports are not supported for inbound operations.</span></span>  
  
6.  <span data-ttu-id="419a3-177">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="419a3-177">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="419a3-178">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="419a3-178">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="419a3-179">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="419a3-179">Generating Schema</span></span>  
 <span data-ttu-id="419a3-180">您必須產生的結構描述**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="419a3-180">You must generate the schema for the **Polling** operation.</span></span> <span data-ttu-id="419a3-181">請參閱[擷取中繼資料，使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業的](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="419a3-181">See [Retrieving Metadata for SQL Server Operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) for more information about how to generate the schema.</span></span> <span data-ttu-id="419a3-182">產生結構描述時，請執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="419a3-182">Perform the following tasks when generating the schema.</span></span> <span data-ttu-id="419a3-183">如果您不要指定繫結屬性在設計階段，請略過第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="419a3-183">Skip the first step if you do not want to specify the binding properties at design-time.</span></span>  
  
1.  <span data-ttu-id="419a3-184">指定的值**PolledDataAvailableStatement**和**PollingStatement**時產生結構描述繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-184">Specify a value for **PolledDataAvailableStatement** and **PollingStatement** binding properties while generating the schema.</span></span> <span data-ttu-id="419a3-185">如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-185">For more information about this binding property, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
     <span data-ttu-id="419a3-186">如需有關如何指定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-186">For instructions on how to specify binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
2.  <span data-ttu-id="419a3-187">選取合約類型為**服務 （輸入作業）**。</span><span class="sxs-lookup"><span data-stu-id="419a3-187">Select the contract type as **Service (Inbound operation)**.</span></span>  
  
3.  <span data-ttu-id="419a3-188">產生結構描述的**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="419a3-188">Generate schema for the **Polling** operation.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="419a3-189">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="419a3-189">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="419a3-190">您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="419a3-190">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="419a3-191">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="419a3-191">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="419a3-192">一旦產生結構描述時，您必須訊息連結之協調流程檢視中的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="419a3-192">Once the schema is generated, you must link it to the messages from the Orchestration view of the BizTalk project.</span></span>  
  
 <span data-ttu-id="419a3-193">本主題中，您必須建立一個從 SQL Server 資料庫接收訊息的訊息。</span><span class="sxs-lookup"><span data-stu-id="419a3-193">For this topic, you must create one message to receive messages from the SQL Server database.</span></span>  
  
 <span data-ttu-id="419a3-194">執行下列步驟來建立訊息，並將它們連結至結構描述。</span><span class="sxs-lookup"><span data-stu-id="419a3-194">Perform the following steps to create messages and link them to schema.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="419a3-195">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="419a3-195">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="419a3-196">BizTalk 專案中新增協調流程。</span><span class="sxs-lookup"><span data-stu-id="419a3-196">Add an orchestration to the BizTalk project.</span></span> <span data-ttu-id="419a3-197">從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="419a3-197">From the Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="419a3-198">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="419a3-198">Type a name for the BizTalk orchestration and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="419a3-199">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="419a3-199">Open the orchestration view window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="419a3-200">按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="419a3-200">Click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="419a3-201">在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="419a3-201">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="419a3-202">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="419a3-202">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="419a3-203">在**屬性**窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="419a3-203">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="419a3-204">使用</span><span class="sxs-lookup"><span data-stu-id="419a3-204">Use this</span></span>|<span data-ttu-id="419a3-205">動作</span><span class="sxs-lookup"><span data-stu-id="419a3-205">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="419a3-206">識別碼</span><span class="sxs-lookup"><span data-stu-id="419a3-206">Identifier</span></span>|<span data-ttu-id="419a3-207">型別**接收**。</span><span class="sxs-lookup"><span data-stu-id="419a3-207">Type **Receive**.</span></span>|  
    |<span data-ttu-id="419a3-208">訊息類型</span><span class="sxs-lookup"><span data-stu-id="419a3-208">Message Type</span></span>|<span data-ttu-id="419a3-209">從下拉式清單中，展開 **結構描述**，然後選取*PollingQuery.Polling*，其中*PollingQuery*是您的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="419a3-209">From the drop-down list, expand **Schemas**, and select *PollingQuery.Polling*, where *PollingQuery* is the name of your BizTalk project.</span></span> <span data-ttu-id="419a3-210">*輪詢*是針對產生的結構描述**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="419a3-210">*Polling* is the schema generated for the **Polling** operation.</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="419a3-211">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="419a3-211">Setting up the Orchestration</span></span>  
 <span data-ttu-id="419a3-212">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收訊息以輪詢為基礎的資料變更從 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="419a3-212">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving polling-based data-change messages from the SQL Server database.</span></span> <span data-ttu-id="419a3-213">在此協調流程中，配接器接收的 select 陳述式指定的回應**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-213">In this orchestration, the adapter receives the response of the select statement specified for the **PollingStatement** binding property.</span></span> <span data-ttu-id="419a3-214">SELECT 陳述式的回應會儲存到檔案位置。</span><span class="sxs-lookup"><span data-stu-id="419a3-214">The response for the SELECT statement is saved to a FILE location.</span></span> <span data-ttu-id="419a3-215">用於輪詢 SQL Server 資料庫的一般協調流程就會包含：</span><span class="sxs-lookup"><span data-stu-id="419a3-215">A typical orchestration for polling a SQL Server database would contain:</span></span>  
  
-   <span data-ttu-id="419a3-216">接收和傳送圖形，從 SQL Server 接收訊息，並分別將傳送至檔案連接埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-216">Receive and Send shapes to receive messages from SQL Server and send to a FILE port, respectively.</span></span>  
  
-   <span data-ttu-id="419a3-217">單向接收埠以接收來自 SQL Server 訊息。</span><span class="sxs-lookup"><span data-stu-id="419a3-217">A one-way receive port to receive messages from SQL Server.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="419a3-218">輸入的輪詢案例，您必須一律先設定單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-218">For inbound polling scenarios you must always configure a one-way receive port.</span></span> <span data-ttu-id="419a3-219">雙向接收埠不支援的輸入操作。</span><span class="sxs-lookup"><span data-stu-id="419a3-219">Two-way receive ports are not supported for inbound operations.</span></span>  
  
-   <span data-ttu-id="419a3-220">單向傳送埠以傳送輪詢回應從 SQL Server 資料庫，到資料夾。</span><span class="sxs-lookup"><span data-stu-id="419a3-220">A one-way send port to send polling responses from a SQL Server database to a folder.</span></span>  
  
 <span data-ttu-id="419a3-221">範例協調流程如下。</span><span class="sxs-lookup"><span data-stu-id="419a3-221">A sample orchestration resembles the following.</span></span>  
  
 <span data-ttu-id="419a3-222">![用於輪詢 SQL Server 資料庫的協調流程](../../adapters-and-accelerators/adapter-sql/media/5cf65d53-d70d-444d-82f7-2561efcd9ee4.gif "5cf65d53-d70d-444d-82f7-2561efcd9ee4")</span><span class="sxs-lookup"><span data-stu-id="419a3-222">![Orchestration for polling a SQL Server database](../../adapters-and-accelerators/adapter-sql/media/5cf65d53-d70d-444d-82f7-2561efcd9ee4.gif "5cf65d53-d70d-444d-82f7-2561efcd9ee4")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="419a3-223">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="419a3-223">Adding Message Shapes</span></span>  
 <span data-ttu-id="419a3-224">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-224">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="419a3-225">圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="419a3-225">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="419a3-226">形狀圖</span><span class="sxs-lookup"><span data-stu-id="419a3-226">Shape</span></span>|<span data-ttu-id="419a3-227">圖形類型</span><span class="sxs-lookup"><span data-stu-id="419a3-227">Shape Type</span></span>|<span data-ttu-id="419a3-228">屬性</span><span class="sxs-lookup"><span data-stu-id="419a3-228">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="419a3-229">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="419a3-229">ReceiveMessage</span></span>|<span data-ttu-id="419a3-230">Receive</span><span class="sxs-lookup"><span data-stu-id="419a3-230">Receive</span></span>|<span data-ttu-id="419a3-231">-設定**名稱**至*ReceiveMessage*</span><span class="sxs-lookup"><span data-stu-id="419a3-231">- Set **Name** to *ReceiveMessage*</span></span><br /><br /> <span data-ttu-id="419a3-232">-設定**啟動**至*，則為 True*</span><span class="sxs-lookup"><span data-stu-id="419a3-232">- Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="419a3-233">SaveMessage</span><span class="sxs-lookup"><span data-stu-id="419a3-233">SaveMessage</span></span>|<span data-ttu-id="419a3-234">Send</span><span class="sxs-lookup"><span data-stu-id="419a3-234">Send</span></span>|<span data-ttu-id="419a3-235">-設定**名稱**至*SaveMessage*</span><span class="sxs-lookup"><span data-stu-id="419a3-235">- Set **Name** to *SaveMessage*</span></span>|  
  
### <a name="adding-ports"></a><span data-ttu-id="419a3-236">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="419a3-236">Adding Ports</span></span>  
 <span data-ttu-id="419a3-237">請確定您針對每個邏輯連接埠指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-237">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="419a3-238">連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。</span><span class="sxs-lookup"><span data-stu-id="419a3-238">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="419a3-239">通訊埠</span><span class="sxs-lookup"><span data-stu-id="419a3-239">Port</span></span>|<span data-ttu-id="419a3-240">屬性</span><span class="sxs-lookup"><span data-stu-id="419a3-240">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="419a3-241">SQLReceivePort</span><span class="sxs-lookup"><span data-stu-id="419a3-241">SQLReceivePort</span></span>|<span data-ttu-id="419a3-242">-設定**識別碼**至*SQLReceivePort*</span><span class="sxs-lookup"><span data-stu-id="419a3-242">- Set **Identifier** to *SQLReceivePort*</span></span><br /><br /> <span data-ttu-id="419a3-243">-設定**類型**至*SQLReceivePortType*</span><span class="sxs-lookup"><span data-stu-id="419a3-243">- Set **Type** to *SQLReceivePortType*</span></span><br /><br /> <span data-ttu-id="419a3-244">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="419a3-244">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="419a3-245">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="419a3-245">- Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="419a3-246">SaveMessagePort</span><span class="sxs-lookup"><span data-stu-id="419a3-246">SaveMessagePort</span></span>|<span data-ttu-id="419a3-247">-設定**識別碼**至*SaveMessagePort*</span><span class="sxs-lookup"><span data-stu-id="419a3-247">- Set **Identifier** to *SaveMessagePort*</span></span><br /><br /> <span data-ttu-id="419a3-248">-設定**類型**至*SaveMessagePortType*</span><span class="sxs-lookup"><span data-stu-id="419a3-248">- Set **Type** to *SaveMessagePortType*</span></span><br /><br /> <span data-ttu-id="419a3-249">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="419a3-249">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="419a3-250">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="419a3-250">- Set **Communication Direction** to *Send*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a><span data-ttu-id="419a3-251">指定動作圖形訊息並連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="419a3-251">Specify Messages for Action Shapes and Connect to Ports</span></span>  
 <span data-ttu-id="419a3-252">下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="419a3-252">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="419a3-253">圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。</span><span class="sxs-lookup"><span data-stu-id="419a3-253">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="419a3-254">形狀圖</span><span class="sxs-lookup"><span data-stu-id="419a3-254">Shape</span></span>|<span data-ttu-id="419a3-255">屬性</span><span class="sxs-lookup"><span data-stu-id="419a3-255">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="419a3-256">ReceiveMessage</span><span class="sxs-lookup"><span data-stu-id="419a3-256">ReceiveMessage</span></span>|<span data-ttu-id="419a3-257">-設定**訊息**至*接收*</span><span class="sxs-lookup"><span data-stu-id="419a3-257">- Set **Message** to *Receive*</span></span><br /><br /> <span data-ttu-id="419a3-258">-設定**作業**至*SQLReceivePort.Polling.Request*</span><span class="sxs-lookup"><span data-stu-id="419a3-258">- Set **Operation** to *SQLReceivePort.Polling.Request*</span></span>|  
|<span data-ttu-id="419a3-259">SaveMessage</span><span class="sxs-lookup"><span data-stu-id="419a3-259">SaveMessage</span></span>|<span data-ttu-id="419a3-260">-設定**訊息**至*接收*</span><span class="sxs-lookup"><span data-stu-id="419a3-260">- Set **Message** to *Receive*</span></span><br /><br /> <span data-ttu-id="419a3-261">-設定**作業**至*SaveMessagePort.Polling.Request*</span><span class="sxs-lookup"><span data-stu-id="419a3-261">- Set **Operation** to *SaveMessagePort.Polling.Request*</span></span>|  
  
 <span data-ttu-id="419a3-262">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="419a3-262">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="419a3-263">您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="419a3-263">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="419a3-264">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-264">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span> 
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="419a3-265">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="419a3-265">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="419a3-266">部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。</span><span class="sxs-lookup"><span data-stu-id="419a3-266">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the BizTalk Server Administration console.</span></span> <span data-ttu-id="419a3-267">您必須使用 BizTalk Server 管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="419a3-267">You must use the BizTalk Server Administration console to configure the application.</span></span> <span data-ttu-id="419a3-268">如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-268">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>  
  
 <span data-ttu-id="419a3-269">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="419a3-269">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="419a3-270">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="419a3-270">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="419a3-271">對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-271">Mapping the ports that you created in your orchestration to physical ports in the BizTalk Server Administration console.</span></span> <span data-ttu-id="419a3-272">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="419a3-272">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="419a3-273">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置將訊息從 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="419a3-273">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the messages from the SQL Server database.</span></span> <span data-ttu-id="419a3-274">這些訊息會在您指定的接收埠對輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-274">These messages will be in response to the polling statement that you specify for the receive port.</span></span>  
  
    -   <span data-ttu-id="419a3-275">定義實體的 WCF 自訂或 WCF-SQL 單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-275">Define a physical WCF-Custom or WCF-SQL one-way receive port.</span></span> <span data-ttu-id="419a3-276">此連接埠輪詢 SQL Server 資料庫與您指定連接埠輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-276">This port polls the SQL Server database with the polling statement you specify for the port.</span></span> <span data-ttu-id="419a3-277">如需如何建立連接埠相關資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-277">For information about how to create ports, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).</span></span> <span data-ttu-id="419a3-278">請確定指定接收埠的下列繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-278">Make sure you specify the following binding properties for the receive port.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="419a3-279">您不需要執行這個步驟，如果您指定在設計階段的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-279">You do not need to perform this step if you specified the binding properties at design-time.</span></span> <span data-ttu-id="419a3-280">在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠，設定必要的繫結屬性，藉由匯入所建立之繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="419a3-280">In such a case, you can create a WCF-custom or WCF-SQL receive port, with the required binding properties set, by importing the binding file created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="419a3-281">如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-281">For more information see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span>  
  
        |<span data-ttu-id="419a3-282">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="419a3-282">Binding Property</span></span>|<span data-ttu-id="419a3-283">值</span><span class="sxs-lookup"><span data-stu-id="419a3-283">Value</span></span>|  
        |----------------------|-----------|  
        |<span data-ttu-id="419a3-284">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="419a3-284">**InboundOperationType**</span></span>|<span data-ttu-id="419a3-285">請確定您設定為**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="419a3-285">Make sure you set this to **Polling**.</span></span>|  
        |<span data-ttu-id="419a3-286">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="419a3-286">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="419a3-287">請確定您指定 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-287">Make sure you specify a SQL statement.</span></span> <span data-ttu-id="419a3-288">本主題中，指定：</span><span class="sxs-lookup"><span data-stu-id="419a3-288">For this topic, specify:</span></span><br /><br /> `SELECT COUNT(*) FROM Employee`|  
        |<span data-ttu-id="419a3-289">**PollingStatement**</span><span class="sxs-lookup"><span data-stu-id="419a3-289">**PollingStatement**</span></span>|<span data-ttu-id="419a3-290">請確定您指定輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-290">Make sure you specify the polling statement.</span></span> <span data-ttu-id="419a3-291">本主題中，指定：</span><span class="sxs-lookup"><span data-stu-id="419a3-291">For this topic, specify:</span></span><br /><br /> `SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000`|  
  
         <span data-ttu-id="419a3-292">如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-292">For more information about the different binding properties, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="419a3-293">我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="419a3-293">We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="419a3-294">您可以執行新增服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-294">You can do so by adding the service behavior while configuring the WCF-Custom or WCF-SQL receive port.</span></span> <span data-ttu-id="419a3-295">如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-295">For instruction on how to add the service behavior, see [Configure Transaction Isolation Level and Transaction Timeout with SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="419a3-296">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="419a3-296">Starting the Application</span></span>  
 <span data-ttu-id="419a3-297">您必須啟動 SQL Server 資料庫從接收訊息的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="419a3-297">You must start the BizTalk application for receiving messages from the SQL Server database.</span></span> <span data-ttu-id="419a3-298">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-298">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="419a3-299">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="419a3-299">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="419a3-300">Wcf-custom 或 WCF-SQL 單向接收埠，會使用指定的陳述式的 SQL Server 資料庫的輪詢**PollingStatement**繫結屬性，正在執行。</span><span class="sxs-lookup"><span data-stu-id="419a3-300">The WCF-Custom or WCF-SQL one-way receive port, which polls the SQL Server database using the statements specified for the **PollingStatement** binding property, is running.</span></span>  
  
-   <span data-ttu-id="419a3-301">FILE 傳送埠，從 SQL Server 所接收訊息，正在執行。</span><span class="sxs-lookup"><span data-stu-id="419a3-301">The FILE send port, which receives messages from SQL Server, is running.</span></span>  
  
-   <span data-ttu-id="419a3-302">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="419a3-302">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="419a3-303">執行作業</span><span class="sxs-lookup"><span data-stu-id="419a3-303">Executing the Operation</span></span>  
 <span data-ttu-id="419a3-304">執行應用程式之後，執行下列一進行，以相同順序：</span><span class="sxs-lookup"><span data-stu-id="419a3-304">After you run the application, the following set of actions take place, in the same sequence:</span></span>  
  
-   <span data-ttu-id="419a3-305">執行配接器**PolledDataAvailableStatement** employee 資料表，並判斷資料表是否有記錄進行輪詢。</span><span class="sxs-lookup"><span data-stu-id="419a3-305">The adapter executes the **PolledDataAvailableStatement** on the Employee table and determines that the table has records for polling.</span></span>  
  
-   <span data-ttu-id="419a3-306">配接器執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="419a3-306">The adapter executes the polling statement.</span></span> <span data-ttu-id="419a3-307">輪詢陳述式包含 SELECT 陳述式和預存程序，因為配接器的其他之後不會執行所有陳述式一個。</span><span class="sxs-lookup"><span data-stu-id="419a3-307">Because the polling statement consists of a SELECT statement and stored procedures, the adapter will execute all the statements one after the other.</span></span>  
  
    -   <span data-ttu-id="419a3-308">配接器會先執行 SELECT 陳述式會傳回 Employee 資料表中的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="419a3-308">The adapter first executes the SELECT statement that returns all the records in the Employee table.</span></span>  
  
    -   <span data-ttu-id="419a3-309">然後執行 MOVE_EMP_DATA 預存程序，會從 Employee 資料表的所有資料都移至 EmployeeHistory 資料表配接器。</span><span class="sxs-lookup"><span data-stu-id="419a3-309">The adapter then executes the MOVE_EMP_DATA stored procedure that moves all data from the Employee table to the EmployeeHistory table.</span></span> <span data-ttu-id="419a3-310">這個預存程序沒有傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="419a3-310">This stored procedure does not return any value.</span></span>  
  
    -   <span data-ttu-id="419a3-311">然後執行配接器加入 Employee 資料表中的一筆記錄的 ADD_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="419a3-311">The adapter then executes the ADD_EMP_DETAILS stored procedure that adds one record to the Employee table.</span></span> <span data-ttu-id="419a3-312">這個預存程序傳回的員工識別碼插入記錄。</span><span class="sxs-lookup"><span data-stu-id="419a3-312">This stored procedure returns the Employee ID for the inserted record.</span></span>  
  
     <span data-ttu-id="419a3-313">因此，從 SQL Server 收到的訊息將包含多個結果集 （如 SELECT 陳述式以及 ADD_EMP_DETAILS 預存程序），並將如下所示：</span><span class="sxs-lookup"><span data-stu-id="419a3-313">So, the message received from SQL Server will contain multiple result sets (for SELECT statement and for ADD_EMP_DETAILS stored procedure), and will resemble the following:</span></span>  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <Polling xmlns="http://schemas.microsoft.com/Sql/2008/05/Polling/">  
      <PolledData>  
        <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
          \<xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
            \<xs:element msdata:IsDataSet="true" name="NewDataSet">  
              \<xs:complexType>  
                \<xs:sequence>  
                  \<xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                    \<xs:complexType>  
                      \<xs:sequence>  
                        \<xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                        \<xs:element minOccurs="0" name="Name" type="xs:string" />   
                        \<xs:element minOccurs="0" name="DOJ" type="xs:dateTime" />   
                        \<xs:element minOccurs="0" name="Designation" type="xs:string" />   
                        \<xs:element minOccurs="0" name="Job_Description" type="xs:string" />   
                        \<xs:element minOccurs="0" name="Photo" type="xs:base64Binary" />   
                        \<xs:element minOccurs="0" name="Rating" type="xs:string" />   
                        \<xs:element minOccurs="0" name="Salary" type="xs:decimal" />   
                        \<xs:element minOccurs="0" name="Last_Modified" type="xs:base64Binary" />   
                      \</xs:sequence>  
                    \</xs:complexType>  
                  \</xs:element>  
                \</xs:sequence>  
              \</xs:complexType>  
            \</xs:element>  
          \</xs:schema>  
          \<diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
            <NewDataSet xmlns="">  
              <NewTable>  
                <Employee_ID>10001</Employee_ID>   
                <Name>John</Name>   
                <Designation>Tester</Designation>   
                <Salary>100000.00</Salary>   
                <Last_Modified>AAAAAAAAF34=</Last_Modified>   
              </NewTable>  
              ........  
              ........  
              <NewTable>  
                <Employee_ID>10005</Employee_ID>   
                <Name>Wilson</Name>   
                <Designation>Tester3</Designation>   
                <Salary>100000.00</Salary>   
                <Last_Modified>AAAAAAAAF4E=</Last_Modified>   
              </NewTable>  
            </NewDataSet>  
          \</diffgr:diffgram>  
        </DataSet>  
        <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
          \<xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
            \<xs:element msdata:IsDataSet="true" name="NewDataSet">  
              \<xs:complexType>  
                \<xs:sequence>  
                  \<xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                    \<xs:complexType>  
                      \<xs:sequence>  
                        \<xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                      \</xs:sequence>  
                    \</xs:complexType>  
                  \</xs:element>  
                \</xs:sequence>  
              \</xs:complexType>  
            \</xs:element>  
          \</xs:schema>  
          \<diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
            <NewDataSet xmlns="">  
              <NewTable>  
                <Employee_ID>10006</Employee_ID>  
              </NewTable>  
            </NewDataSet>  
          \</diffgr:diffgram>  
        </DataSet>  
      </PolledData>  
    </Polling>  
    ```  
  
     <span data-ttu-id="419a3-314">上述的回應包含兩個資料集。</span><span class="sxs-lookup"><span data-stu-id="419a3-314">The preceding response contains two data sets.</span></span> <span data-ttu-id="419a3-315">第一個資料集包含 SELECT 陳述式的回應。</span><span class="sxs-lookup"><span data-stu-id="419a3-315">The first data set contains the response for the SELECT statement.</span></span> <span data-ttu-id="419a3-316">SELECT 陳述式選取 Employee 資料表中的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="419a3-316">The SELECT statement selects all the records in the Employee table.</span></span> <span data-ttu-id="419a3-317">第二個資料集是 ADD_EMP_DETAILS 預存程序。</span><span class="sxs-lookup"><span data-stu-id="419a3-317">The second data set is for the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="419a3-318">這個預存程序會將記錄加入 Employee 資料表，並傳回新的記錄的員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="419a3-318">This stored procedure adds a record to the Employee table and returns the employee ID for the new record.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="419a3-319">MOVE_EMP_DATA 預存程序不會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="419a3-319">The MOVE_EMP_DATA stored procedure does not return a result set.</span></span> <span data-ttu-id="419a3-320">因此，回應訊息中沒有任何對應的資料集。</span><span class="sxs-lookup"><span data-stu-id="419a3-320">So, there is no corresponding data set in the response message.</span></span>  
  
-   <span data-ttu-id="419a3-321">當配接器執行**PollDataAvailableStatement**同樣地，它會尋找一筆記錄 ADD_EMP_DETAILS 所插入的預存程序。</span><span class="sxs-lookup"><span data-stu-id="419a3-321">When the adapter executes the **PollDataAvailableStatement** again, it finds one record that was inserted by the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="419a3-322">然後執行所有三個陳述式所指定的配接器**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="419a3-322">The adapter then executes all three statements that are specified for the **PollingStatement** binding property.</span></span> <span data-ttu-id="419a3-323">這次會從 SQL Server 的回應包含 SELECT 陳述式只有一項記錄，並且 ADD_EMP_DETAILS 的一筆記錄的預存程序。</span><span class="sxs-lookup"><span data-stu-id="419a3-323">This time, the response from SQL Server contains just one record for the SELECT statement and one record for the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="419a3-324">所有後續輪詢會傳回類似的回應。</span><span class="sxs-lookup"><span data-stu-id="419a3-324">All subsequent polls will return similar responses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="419a3-325">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]將繼續輪詢直到您明確地停用接收埠從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="419a3-325">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] will continue to poll until you explicitly disable the receive port from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="419a3-326">最佳作法</span><span class="sxs-lookup"><span data-stu-id="419a3-326">Best Practices</span></span>  
 <span data-ttu-id="419a3-327">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="419a3-327">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="419a3-328">一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立傳送埠和接收相同的協調流程連接埠。</span><span class="sxs-lookup"><span data-stu-id="419a3-328">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create the send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="419a3-329">如需繫結檔案的詳細資訊，請參閱[重複使用配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="419a3-329">For more information about binding files, see [Reuse adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="419a3-330">另請參閱</span><span class="sxs-lookup"><span data-stu-id="419a3-330">See Also</span></span>  
 [<span data-ttu-id="419a3-331">與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server</span><span class="sxs-lookup"><span data-stu-id="419a3-331">Poll SQL Server using the SQL Adapter with BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)