---
title: 從使用 BizTalk Server 的 SQL 以累加方式查詢通知接收 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6972e01-80be-47be-986a-c2e4e0fb0cd1
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e278b4e25db6c62127d2aac4ee8d29c3c422e463
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007759"
---
# <a name="receive-query-notifications-incrementally-from-sql-using-biztalk-server"></a><span data-ttu-id="e97a9-102">以累加方式查詢通知接收使用 BizTalk Server 的 SQL</span><span class="sxs-lookup"><span data-stu-id="e97a9-102">Receive Query Notifications Incrementally from SQL using BizTalk Server</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="e97a9-103">為了簡潔起見，本主題僅說明如何以累加方式接收通知。</span><span class="sxs-lookup"><span data-stu-id="e97a9-103">For the sake of brevity, this topic only describes how to receive notifications incrementally.</span></span> <span data-ttu-id="e97a9-104">在商務案例中，協調流程必須在理想情況下會納入邏輯來擷取收到的通知訊息的類型，然後再執行任何後續的作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-104">In business scenarios, the orchestration must ideally include the logic to extract the kind of notification message received and then perform any subsequent operations.</span></span> <span data-ttu-id="e97a9-105">本主題中所述的協調流程換句話說，必須採用協調流程中所述[處理通知訊息，以完成特定工作中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-105">In other words, the orchestration described in this topic must be built on top of the orchestration described in [Process notification messages to complete specific tasks in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md).</span></span>  
  
 <span data-ttu-id="e97a9-106">本主題示範如何設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收從 SQL Server 資料庫的累加式的查詢通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-106">This topic demonstrates how to configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive incremental query notification messages from a SQL Server database.</span></span> <span data-ttu-id="e97a9-107">為了示範累加通知，請考慮資料表，員工，且 [狀態] 資料行。</span><span class="sxs-lookup"><span data-stu-id="e97a9-107">To demonstrate incremental notifications, consider a table, Employee, with a “Status” column.</span></span> <span data-ttu-id="e97a9-108">此資料表插入新記錄時，[狀態] 欄的值設為 0。</span><span class="sxs-lookup"><span data-stu-id="e97a9-108">When a new record is inserted to this table, the value of the Status column is set to 0.</span></span> <span data-ttu-id="e97a9-109">您可以設定配接器接收累加的通知，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e97a9-109">You can configure the adapter to receive incremental notifications by doing the following:</span></span>  
  
- <span data-ttu-id="e97a9-110">註冊使用 SQL 陳述式會擷取具有 [狀態] 欄位為 0 的所有記錄的通知。</span><span class="sxs-lookup"><span data-stu-id="e97a9-110">Register for notifications using a SQL statement that retrieves all records that have Status column as 0.</span></span> <span data-ttu-id="e97a9-111">則可以藉由指定的 SQL 陳述式**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-111">You can do so by specifying the SQL statement for the **NotificationStatement** binding property.</span></span>  
  
- <span data-ttu-id="e97a9-112">對於已接收的通知訊息的資料列，更新 [狀態] 欄為 1。</span><span class="sxs-lookup"><span data-stu-id="e97a9-112">For rows for which notification messages have been received, update the Status column to 1.</span></span>  
  
  <span data-ttu-id="e97a9-113">本主題示範如何建立 BizTalk 協調流程和設定 BizTalk 應用程式來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="e97a9-113">This topic demonstrates how to create a BizTalk orchestration and configure a BizTalk application to achieve this.</span></span>  
  
## <a name="configuring-notifications-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="e97a9-114">使用 SQL 配接器繫結屬性中設定通知</span><span class="sxs-lookup"><span data-stu-id="e97a9-114">Configuring Notifications with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="e97a9-115">下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結屬性，您用來設定 從 SQL Server 中接收通知。</span><span class="sxs-lookup"><span data-stu-id="e97a9-115">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure receiving notifications from SQL Server.</span></span> <span data-ttu-id="e97a9-116">您必須在設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="e97a9-116">You must specify these binding properties while configuring the receive port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e97a9-117">您也可以指定這些繫結屬性，產生的結構描述時**通知**作業，即使它不是強制性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-117">You may choose to specify these binding properties when generating the schema for the **Notification** operation, even though it is not mandatory.</span></span> <span data-ttu-id="e97a9-118">如果您這樣做時，連接埠繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e97a9-118">If you do so, the port binding file that the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] generates as part of the metadata generation also contains the values you specify for the binding properties.</span></span> <span data-ttu-id="e97a9-119">您可以稍後匯入此繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂或 WCF-SQL 與繫結屬性已設定接收埠。</span><span class="sxs-lookup"><span data-stu-id="e97a9-119">You can later import this binding file in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create the WCF-custom or WCF-SQL receive port with the binding properties already set.</span></span> <span data-ttu-id="e97a9-120">如需建立使用該繫結檔案的連接埠的詳細資訊，請參閱 <<c0> [ 設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-120">For more information about creating a port using the binding file, see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span>  
  
|<span data-ttu-id="e97a9-121">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="e97a9-121">Binding Property</span></span>|<span data-ttu-id="e97a9-122">描述</span><span class="sxs-lookup"><span data-stu-id="e97a9-122">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e97a9-123">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="e97a9-123">**InboundOperationType**</span></span>|<span data-ttu-id="e97a9-124">指定輸入您想要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-124">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="e97a9-125">若要接收通知訊息，將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-125">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="e97a9-126">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="e97a9-126">**NotificationStatement**</span></span>|<span data-ttu-id="e97a9-127">指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序\>) 用來註冊查詢通知。</span><span class="sxs-lookup"><span data-stu-id="e97a9-127">Specifies the SQL statement (SELECT or EXEC \<stored procedure\>) used to register for query notifications.</span></span> <span data-ttu-id="e97a9-128">在結果集為指定的 SQL 陳述式變更時，才配接器從 SQL Server 取得通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-128">The adapter gets a notification message from SQL Server only when the result set for the specified SQL statement changes.</span></span>|  
|<span data-ttu-id="e97a9-129">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="e97a9-129">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="e97a9-130">指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。</span><span class="sxs-lookup"><span data-stu-id="e97a9-130">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="e97a9-131">如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-131">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="e97a9-132">如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]若要從 SQL Server 中接收通知，可深入閱讀。</span><span class="sxs-lookup"><span data-stu-id="e97a9-132">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive notifications from SQL Server, read further.</span></span>  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a><span data-ttu-id="e97a9-133">本主題示範接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="e97a9-133">How This Topic Demonstrates Receiving Notification Messages</span></span>  
 <span data-ttu-id="e97a9-134">若要示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援從 SQL Server 中接收通知訊息，本主題將示範如何設定配接器接收的 Employee 資料表的變更通知。</span><span class="sxs-lookup"><span data-stu-id="e97a9-134">To demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving notification messages from SQL Server, this topic will demonstrate how to configure the adapter to receive notifications for changes to an Employee table.</span></span> <span data-ttu-id="e97a9-135">假設員工資料表有資料行 Employee_ID、 名稱和狀態。</span><span class="sxs-lookup"><span data-stu-id="e97a9-135">Assume that the Employee table has columns Employee_ID, Name, and Status.</span></span> <span data-ttu-id="e97a9-136">每當新增新進員工時，[狀態] 欄的值設為 0。</span><span class="sxs-lookup"><span data-stu-id="e97a9-136">Whenever a new employee is added, the value of the Status column is set to 0.</span></span>  
  
 <span data-ttu-id="e97a9-137">為了示範如何接收通知，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e97a9-137">To demonstrate receiving notifications, do the following:</span></span>  
  
-   <span data-ttu-id="e97a9-138">產生結構描述**通知**（輸入作業），和**選取**（輸出作業） 在 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="e97a9-138">Generate schema for the **Notification** (inbound operation), and **Select** (outbound operation) on the Employee table.</span></span>  
  
-   <span data-ttu-id="e97a9-139">建立具有下列的協調流程：</span><span class="sxs-lookup"><span data-stu-id="e97a9-139">Create an orchestration that has the following:</span></span>  
  
    -   <span data-ttu-id="e97a9-140">接收位置來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-140">A receive location to receive notification messages.</span></span> <span data-ttu-id="e97a9-141">您可以藉由指定 SELECT 陳述式設定通知：</span><span class="sxs-lookup"><span data-stu-id="e97a9-141">You can configure for notification by specifying the SELECT statement as:</span></span>  
  
        ```  
        SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="e97a9-142">具體來說，您必須指定資料行名稱，在此所示的陳述式中的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e97a9-142">You must specifically specify the column names in the statement as shown in this SELECT statement.</span></span> <span data-ttu-id="e97a9-143">此外，您一律必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="e97a9-143">Also, you must always specify the table name along with the schema name.</span></span> <span data-ttu-id="e97a9-144">例如， `dbo.Employee`。</span><span class="sxs-lookup"><span data-stu-id="e97a9-144">For example, `dbo.Employee`.</span></span>  
  
    -   <span data-ttu-id="e97a9-145">傳送埠，以更新的通知已傳送的資料列。</span><span class="sxs-lookup"><span data-stu-id="e97a9-145">A send port to update the rows for which notification has already been sent.</span></span> <span data-ttu-id="e97a9-146">您這樣做，將值設定為 1 的 [狀態] 欄中。</span><span class="sxs-lookup"><span data-stu-id="e97a9-146">You do so by setting the value in the Status column to 1.</span></span> <span data-ttu-id="e97a9-147">您可以選取作業的一部分傳送至配接器的下列訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-147">You can do this as part of the Select operation by sending the following message to the adapter.</span></span>  
  
        ```  
        <Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
          <Columns>Employee_ID,Name,Status</Columns>  
          <Query>where Status=0;UPDATE Employee SET Status=1 WHERE Status=0</Query>  
        </Select>  
        ```  
  
         <span data-ttu-id="e97a9-148">在此訊息中，做為一部分`<Query>`元素中，指定更新的狀態資料行 UPDATE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e97a9-148">In this message, as part of the `<Query>` element, you specify the UPDATE statement to update the Status column.</span></span> <span data-ttu-id="e97a9-149">請注意接收通知訊息，以便處理的資料列更新之後，必須執行此作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-149">Note that this operation must be executed after receiving the notification messages so that the processed rows are updated.</span></span> <span data-ttu-id="e97a9-150">若要執行立即等候取得通知回應，然後再手動卸除要求訊息來更新資料列的負擔，您將會產生更新協調流程本身內的資料列的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-150">To do away with the overhead of waiting to get the notification response and then manually dropping a request message to update the rows, you will generate the request message for updating the rows within the orchestration itself.</span></span> <span data-ttu-id="e97a9-151">您可以使用來進行這**建構訊息**協調流程內的圖形。</span><span class="sxs-lookup"><span data-stu-id="e97a9-151">You can do so by using the **Construct Message** shape within an orchestration.</span></span>  
  
## <a name="how-to-receive-notification-messages-from-the-sql-server-database"></a><span data-ttu-id="e97a9-152">如何從 SQL Server 資料庫中接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="e97a9-152">How to Receive Notification Messages from the SQL Server Database</span></span>  
 <span data-ttu-id="e97a9-153">執行 SQL Server 資料庫使用運算[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-153">Performing an operation on the SQL Server database using [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves the procedural tasks described in [Building blocks to develop BizTalk applications with the SQL adapter](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md).</span></span> <span data-ttu-id="e97a9-154">若要設定要接收通知訊息的介面卡，這些工作如下：</span><span class="sxs-lookup"><span data-stu-id="e97a9-154">To configure the adapter to receive notification messages, these tasks are:</span></span>  
  
1. <span data-ttu-id="e97a9-155">建立 BizTalk 專案，然後再產生結構描述**通知**（輸入作業） 和**選取**（輸出作業） 在 [員工] 資料表。</span><span class="sxs-lookup"><span data-stu-id="e97a9-155">Create a BizTalk project, and then generate schema for the **Notification** (inbound operation) and **Select** (outbound operation) on the Employee table.</span></span> <span data-ttu-id="e97a9-156">您可以選擇性地指定值**InboundOperationType**並**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-156">Optionally, you can specify values for the **InboundOperationType** and **NotificationStatement** binding properties.</span></span>  
  
2. <span data-ttu-id="e97a9-157">從 SQL Server 資料庫中接收通知的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-157">Create a message in the BizTalk project for receiving notification from the SQL Server database.</span></span>  
  
3. <span data-ttu-id="e97a9-158">在 SQL Server 資料庫上執行選取的資訊，並接收回應訊息的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-158">Create messages in the BizTalk project for performing the Select information on the SQL Server database and receiving response messages.</span></span>  
  
4. <span data-ttu-id="e97a9-159">建立協調流程，會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e97a9-159">Create an orchestration that does the following:</span></span>  
  
   -   <span data-ttu-id="e97a9-160">從 SQL Server 中接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-160">Receives notification message from SQL Server.</span></span>  
  
   -   <span data-ttu-id="e97a9-161">建立選取及更新的資料列，收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-161">Creates a message to select and update the rows for which notification is received.</span></span>  
  
   -   <span data-ttu-id="e97a9-162">將此訊息傳送到 SQL Server 更新的資料列，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="e97a9-162">Sends this message to the SQL Server to update the rows and receives a response.</span></span>  
  
5. <span data-ttu-id="e97a9-163">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="e97a9-163">Build and deploy the BizTalk project.</span></span>  
  
6. <span data-ttu-id="e97a9-164">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="e97a9-164">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="e97a9-165">輸入的作業，例如接收通知訊息，您必須只設定單向的 WCF 自訂或 WCF SQL 接收埠。</span><span class="sxs-lookup"><span data-stu-id="e97a9-165">For inbound operations, like receiving notification messages, you must only configure a one-way WCF-Custom or WCF-SQL receive port.</span></span> <span data-ttu-id="e97a9-166">雙向 WCF 自訂] 或 [WCF-SQL 接收埠不支援的輸入作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-166">Two-way WCF-Custom or WCF-SQL receive ports are not supported for inbound operations.</span></span>  
  
7. <span data-ttu-id="e97a9-167">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e97a9-167">Start the BizTalk application.</span></span>  
  
   <span data-ttu-id="e97a9-168">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="e97a9-168">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="sample-based-on-this-topic"></a><span data-ttu-id="e97a9-169">根據本主題的範例</span><span class="sxs-lookup"><span data-stu-id="e97a9-169">Sample Based on This Topic</span></span>  
 <span data-ttu-id="e97a9-170">，IncrementalNotification，根據本主題提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e97a9-170">A sample, IncrementalNotification, based on this topic is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="e97a9-171">如需詳細資訊，請參閱 < [SQL 配接器的範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-171">For more information, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="e97a9-172">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="e97a9-172">Generating Schema</span></span>  
 <span data-ttu-id="e97a9-173">您必須產生的結構描述**通知**作業並**選取**員工資料表上的執行作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-173">You must generate the schema for the **Notification** operation and **Select** operation on Employee table.</span></span> <span data-ttu-id="e97a9-174">請參閱[取得 Visual Studio 中使用 SQL 配接器中的 SQL Server 作業的中繼資料](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="e97a9-174">See [Get metadata for SQL Server operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) for more information about how to generate the schema.</span></span> <span data-ttu-id="e97a9-175">產生結構描述時，請執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="e97a9-175">Perform the following tasks when generating the schema.</span></span> <span data-ttu-id="e97a9-176">如果您不想在設計階段指定的繫結屬性，請略過第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="e97a9-176">Skip the first step if you do not want to specify the binding properties at design time.</span></span>  
  
1.  <span data-ttu-id="e97a9-177">指定的值**InboundOperationType**並**NotificationStatement**時產生結構描述繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-177">Specify a value for **InboundOperationType** and **NotificationStatement** binding properties while generating the schema.</span></span> <span data-ttu-id="e97a9-178">如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-178">For more information about this binding property, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="e97a9-179">如需有關如何指定繫結屬性的指示，請參閱 <<c0> [ 設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-179">For instructions on how to specify binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
2.  <span data-ttu-id="e97a9-180">選取合約類型作為**服務 （輸入作業）**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-180">Select the contract type as **Service (Inbound operations)**.</span></span>  
  
3.  <span data-ttu-id="e97a9-181">產生結構描述**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-181">Generate schema for the **Notification** operation.</span></span>  
  
4.  <span data-ttu-id="e97a9-182">選取合約類型作為**用戶端 （傳出作業）**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-182">Select the contract type as **Client (Outbound operations)**.</span></span>  
  
5.  <span data-ttu-id="e97a9-183">產生結構描述**選取 **上的作業**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="e97a9-183">Generate schema for the **Select** operation on **Employee** table.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="e97a9-184">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="e97a9-184">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="e97a9-185">您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。</span><span class="sxs-lookup"><span data-stu-id="e97a9-185">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="e97a9-186">訊息通常是一個變數，要為其類型會定義對應的結構。</span><span class="sxs-lookup"><span data-stu-id="e97a9-186">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="e97a9-187">一旦產生結構描述時，您必須訊息從 BizTalk 專案的協調流程檢視以將它的連結。</span><span class="sxs-lookup"><span data-stu-id="e97a9-187">Once the schema is generated, you must link it to the messages from the Orchestration view of the BizTalk project.</span></span>  
  
 <span data-ttu-id="e97a9-188">本主題中，您必須建立三個訊息，一個用於接收通知，從 SQL Server 資料庫，以執行所選取的作業和一個用來接收選取作業的回應。</span><span class="sxs-lookup"><span data-stu-id="e97a9-188">For this topic, you must create three messages—one to receive notifications from the SQL Server database, one to perform the Select operation, and one to receive the response for Select operation.</span></span>  
  
 <span data-ttu-id="e97a9-189">執行下列步驟來建立訊息，並將它們連結至結構描述。</span><span class="sxs-lookup"><span data-stu-id="e97a9-189">Perform the following steps to create messages and link them to schema.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="e97a9-190">若要建立訊息，並連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="e97a9-190">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="e97a9-191">BizTalk 專案中新增協調流程。</span><span class="sxs-lookup"><span data-stu-id="e97a9-191">Add an orchestration to the BizTalk project.</span></span> <span data-ttu-id="e97a9-192">從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-192">From the Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="e97a9-193">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-193">Type a name for the BizTalk orchestration and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="e97a9-194">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e97a9-194">Open the orchestration view window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="e97a9-195">按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-195">Click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="e97a9-196">在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-196">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="e97a9-197">以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-197">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="e97a9-198">在 [**屬性**] 窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e97a9-198">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="e97a9-199">使用</span><span class="sxs-lookup"><span data-stu-id="e97a9-199">Use this</span></span>|<span data-ttu-id="e97a9-200">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="e97a9-200">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e97a9-201">識別碼</span><span class="sxs-lookup"><span data-stu-id="e97a9-201">Identifier</span></span>|<span data-ttu-id="e97a9-202">輸入 `NotifyReceive`。</span><span class="sxs-lookup"><span data-stu-id="e97a9-202">Type `NotifyReceive`.</span></span>|  
    |<span data-ttu-id="e97a9-203">訊息類型</span><span class="sxs-lookup"><span data-stu-id="e97a9-203">Message Type</span></span>|<span data-ttu-id="e97a9-204">從下拉式清單中，依序展開**結構描述**，然後選取*SQLNotify.Notification*，其中*SQLNotify*是 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="e97a9-204">From the drop-down list, expand **Schemas**, and select *SQLNotify.Notification*, where *SQLNotify* is the name of your BizTalk project.</span></span> <span data-ttu-id="e97a9-205">*通知*是針對產生的結構描述**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-205">*Notification* is the schema generated for the **Notification** operation.</span></span>|  
  
6.  <span data-ttu-id="e97a9-206">重複步驟 3 以建立兩個新的訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-206">Repeat step 3 to create two new messages.</span></span> <span data-ttu-id="e97a9-207">在 **屬性**窗格中的新訊息，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e97a9-207">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="e97a9-208">若要設定識別項</span><span class="sxs-lookup"><span data-stu-id="e97a9-208">Set Identifier to</span></span>|<span data-ttu-id="e97a9-209">若要設定訊息類型</span><span class="sxs-lookup"><span data-stu-id="e97a9-209">Set Message Type to</span></span>|  
    |-----------------------|-------------------------|  
    |<span data-ttu-id="e97a9-210">Select</span><span class="sxs-lookup"><span data-stu-id="e97a9-210">Select</span></span>|<span data-ttu-id="e97a9-211">*SQLNotify.TableOperation_dbo_Employee.Select*，其中*TableOperation_dbo_Employee*是針對產生的結構描述**選取**作業</span><span class="sxs-lookup"><span data-stu-id="e97a9-211">*SQLNotify.TableOperation_dbo_Employee.Select*, where  *TableOperation_dbo_Employee* is the schema generated for the **Select** operation</span></span>|  
    |<span data-ttu-id="e97a9-212">SelectResponse</span><span class="sxs-lookup"><span data-stu-id="e97a9-212">SelectResponse</span></span>|<span data-ttu-id="e97a9-213">*SQLNotify.TableOperation_dbo_Employee.SelectResponse*</span><span class="sxs-lookup"><span data-stu-id="e97a9-213">*SQLNotify.TableOperation_dbo_Employee.SelectResponse*</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="e97a9-214">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="e97a9-214">Setting up the Orchestration</span></span>  
 <span data-ttu-id="e97a9-215">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]for SQL Server 資料庫中接收通知訊息，然後更新 收到通知的資料列。</span><span class="sxs-lookup"><span data-stu-id="e97a9-215">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving notification messages from the SQL Server database and then updating the rows for which notification was received.</span></span> <span data-ttu-id="e97a9-216">在此協調流程中，配接器會接收依據指定的 SELECT 陳述式的通知訊息**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-216">In this orchestration, the adapter receives the notification message based on the SELECT statement specified for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="e97a9-217">檔案位置就會收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-217">The notification message is received at a FILE location.</span></span> <span data-ttu-id="e97a9-218">一旦收到回應時，協調流程會建構的訊息，將用來更新資料列，收到通知。</span><span class="sxs-lookup"><span data-stu-id="e97a9-218">Once the response is received, the orchestration constructs a message that will be used to update the rows for which notification is received.</span></span> <span data-ttu-id="e97a9-219">此訊息的回應也就會收到相同的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="e97a9-219">The response for this message is also received at the same FILE location.</span></span>  
  
 <span data-ttu-id="e97a9-220">因此，您的協調流程必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="e97a9-220">So, your orchestration must contain the following:</span></span>  
  
- <span data-ttu-id="e97a9-221">單向接收埠以接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-221">A one-way receive port to receive notification messages.</span></span>  
  
- <span data-ttu-id="e97a9-222">雙向傳送埠以傳送訊息以更新資料列，並接收相同的回應。</span><span class="sxs-lookup"><span data-stu-id="e97a9-222">A two-way send port to send messages to update rows and receive response for the same.</span></span>  
  
- <span data-ttu-id="e97a9-223">A**建構訊息**來建構訊息，以執行更新作業，在協調流程中的圖形。</span><span class="sxs-lookup"><span data-stu-id="e97a9-223">A **Construct Message** shape to construct messages, to execute the Update operation, within the orchestration.</span></span>  
  
- <span data-ttu-id="e97a9-224">FILE 傳送埠以儲存更新作業的回應。</span><span class="sxs-lookup"><span data-stu-id="e97a9-224">A FILE send port to save the response for the Update operation.</span></span>  
  
- <span data-ttu-id="e97a9-225">接收和傳送圖形。</span><span class="sxs-lookup"><span data-stu-id="e97a9-225">Receive and send shapes.</span></span>  
  
  <span data-ttu-id="e97a9-226">範例協調流程如下所示。</span><span class="sxs-lookup"><span data-stu-id="e97a9-226">A sample orchestration resembles the following.</span></span>  
  
  <span data-ttu-id="e97a9-227">![用於接收 SQL Server 通知的協調流程](../../adapters-and-accelerators/adapter-sql/media/f13ad3b8-8161-42e5-a521-424bbf549ad5.gif "f13ad3b8-8161-42e5-a521-424bbf549ad5")</span><span class="sxs-lookup"><span data-stu-id="e97a9-227">![Orchestration to receive SQL Server notifications](../../adapters-and-accelerators/adapter-sql/media/f13ad3b8-8161-42e5-a521-424bbf549ad5.gif "f13ad3b8-8161-42e5-a521-424bbf549ad5")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="e97a9-228">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="e97a9-228">Adding Message Shapes</span></span>  
 <span data-ttu-id="e97a9-229">請確定您針對每個訊息 圖形中指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-229">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="e97a9-230">剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。</span><span class="sxs-lookup"><span data-stu-id="e97a9-230">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="e97a9-231">形狀圖</span><span class="sxs-lookup"><span data-stu-id="e97a9-231">Shape</span></span>|<span data-ttu-id="e97a9-232">圖形類型</span><span class="sxs-lookup"><span data-stu-id="e97a9-232">Shape Type</span></span>|<span data-ttu-id="e97a9-233">屬性</span><span class="sxs-lookup"><span data-stu-id="e97a9-233">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="e97a9-234">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="e97a9-234">ReceiveNotification</span></span>|<span data-ttu-id="e97a9-235">Receive</span><span class="sxs-lookup"><span data-stu-id="e97a9-235">Receive</span></span>|<span data-ttu-id="e97a9-236">-設定**名稱**到*ReceiveNotification*</span><span class="sxs-lookup"><span data-stu-id="e97a9-236">- Set **Name** to *ReceiveNotification*</span></span><br /><br /> <span data-ttu-id="e97a9-237">-設定**啟用**到 *，則為 True*</span><span class="sxs-lookup"><span data-stu-id="e97a9-237">- Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="e97a9-238">SaveNotification</span><span class="sxs-lookup"><span data-stu-id="e97a9-238">SaveNotification</span></span>|<span data-ttu-id="e97a9-239">Send</span><span class="sxs-lookup"><span data-stu-id="e97a9-239">Send</span></span>|<span data-ttu-id="e97a9-240">-設定**名稱**到*SaveNotification*</span><span class="sxs-lookup"><span data-stu-id="e97a9-240">- Set **Name** to *SaveNotification*</span></span>|  
|<span data-ttu-id="e97a9-241">SendSelectMessage</span><span class="sxs-lookup"><span data-stu-id="e97a9-241">SendSelectMessage</span></span>|<span data-ttu-id="e97a9-242">Send</span><span class="sxs-lookup"><span data-stu-id="e97a9-242">Send</span></span>|<span data-ttu-id="e97a9-243">-設定**名稱**到*SendSelectMessage*</span><span class="sxs-lookup"><span data-stu-id="e97a9-243">- Set **Name** to *SendSelectMessage*</span></span>|  
|<span data-ttu-id="e97a9-244">ReceiveSelectResponse</span><span class="sxs-lookup"><span data-stu-id="e97a9-244">ReceiveSelectResponse</span></span>|<span data-ttu-id="e97a9-245">Receive</span><span class="sxs-lookup"><span data-stu-id="e97a9-245">Receive</span></span>|<span data-ttu-id="e97a9-246">-設定**名稱**到*ReceiveSelectResponse*</span><span class="sxs-lookup"><span data-stu-id="e97a9-246">- Set **Name** to *ReceiveSelectResponse*</span></span>|  
|<span data-ttu-id="e97a9-247">SaveSelectResponse</span><span class="sxs-lookup"><span data-stu-id="e97a9-247">SaveSelectResponse</span></span>|<span data-ttu-id="e97a9-248">Send</span><span class="sxs-lookup"><span data-stu-id="e97a9-248">Send</span></span>|<span data-ttu-id="e97a9-249">-設定**名稱**到*SaveSelectResponse*</span><span class="sxs-lookup"><span data-stu-id="e97a9-249">- Set **Name** to *SaveSelectResponse*</span></span>|  
  
### <a name="adding-construct-message-shape"></a><span data-ttu-id="e97a9-250">新增 建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="e97a9-250">Adding Construct Message Shape</span></span>  
 <span data-ttu-id="e97a9-251">您可以使用**建構訊息**圖形，以產生在作業中執行選取的作業要求訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-251">You can use the **Construct Message** shape to generate a request message within the operation to perform the Select operation.</span></span> <span data-ttu-id="e97a9-252">若要這樣做，您必須加入**建構的訊息**圖形，並在其中**訊息指派**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="e97a9-252">To do so, you must add a **Construct Message** shape and within that a **Message Assignment** shape to your orchestration.</span></span> <span data-ttu-id="e97a9-253">此範例中，如**訊息指派**圖形叫用所產生的訊息，傳送到 SQL Server 來執行選取作業的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e97a9-253">For this example, the **Message Assignment** shape invokes code that generates a message that is sent to SQL Server to perform the Select operation.</span></span> <span data-ttu-id="e97a9-254">**訊息指派**圖形也會將訊息傳送到 SQL Server 的動作。</span><span class="sxs-lookup"><span data-stu-id="e97a9-254">The **Message Assignment** shape also sets the action for the message to be sent to SQL Server.</span></span>  
  
 <span data-ttu-id="e97a9-255">針對 「 建構訊息 」 圖形中，設定**建構的訊息**屬性設**選取**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-255">For the construct message shape, set the **Message Constructed** property to **Select**.</span></span>  
  
 <span data-ttu-id="e97a9-256">若要產生回應的程式碼可以是相同的 Visual Studio 方案，為您的 BizTalk 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="e97a9-256">The code to generate the response could be part of the same Visual Studio solution as your BizTalk project.</span></span> <span data-ttu-id="e97a9-257">產生回應訊息的範例程式碼看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="e97a9-257">A sample code for generating a response message looks like this.</span></span>  
  
```  
namespace SampleMessageCreator  
{  
    public class SampleMessageCreator  
    {  
        private static XmlDocument Message;  
        private static string XmlFileLocation;  
        private static string ResponseDoc;  
        public static XmlDocument XMLMessageCreator()  
        {  
            XmlFileLocation = "C:\\TestLocation\\CreateMessage";  
            try  
            {  
                ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                Console.WriteLine("EXCEPTION: " + ex.ToString());  
                throw ex;  
            }  
            //Create Message From XML  
            Message = new XmlDocument();  
            Message.PreserveWhitespace = true;  
            Message.Load(ResponseDoc);  
            return Message;  
        }   
    }  
}  
```  
  
 <span data-ttu-id="e97a9-258">上述程式碼摘錄中能夠產生要求訊息，您必須 （適用於 [員工] 資料表的 Select 作業） 的 XML 要求訊息中所指定的位置`XmlFileLocation`變數。</span><span class="sxs-lookup"><span data-stu-id="e97a9-258">For the preceding code excerpt to be able to generate a request message, you must have an XML request message (for the Select operation on the Employee table) in the location specified for the `XmlFileLocation` variable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e97a9-259">建置專案之後，就會建立 SampleMessageCreator.dll 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="e97a9-259">After you build the project, SampleMessageCreator.dll will be created in the project directory.</span></span> <span data-ttu-id="e97a9-260">您必須將此 DLL 加入全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-260">You must add this DLL to the global assembly cache (GAC).</span></span> <span data-ttu-id="e97a9-261">此外，您必須新增 SampleMessageCreator.dll 做為 BizTalk 專案中的參考。</span><span class="sxs-lookup"><span data-stu-id="e97a9-261">Also, you must add the SampleMessageCreator.dll as a reference in the BizTalk project.</span></span>  
  
 <span data-ttu-id="e97a9-262">加入下列運算式來叫用此程式碼**訊息指派**圖形，並設定訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="e97a9-262">Add the following expression to invoke this code from the **Message Assignment** shape and to set the action for message.</span></span> <span data-ttu-id="e97a9-263">若要新增運算式，請按兩下**訊息指派**圖形以開啟 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="e97a9-263">To add an expression, double-click the **Message Assignment** shape to open the Expression Editor.</span></span>  
  
```  
Select = SampleMessageCreator.SampleMessageCreator.XMLMessageCreator();  
Select(WCF.Action) = "TableOp/Select/dbo/Employee";  
```  
  
### <a name="adding-ports"></a><span data-ttu-id="e97a9-264">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="e97a9-264">Adding Ports</span></span>  
 <span data-ttu-id="e97a9-265">請確定您針對每個邏輯連接埠中指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-265">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="e97a9-266">協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="e97a9-266">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="e97a9-267">通訊埠</span><span class="sxs-lookup"><span data-stu-id="e97a9-267">Port</span></span>|<span data-ttu-id="e97a9-268">屬性</span><span class="sxs-lookup"><span data-stu-id="e97a9-268">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="e97a9-269">SQLNotifyPort</span><span class="sxs-lookup"><span data-stu-id="e97a9-269">SQLNotifyPort</span></span>|<span data-ttu-id="e97a9-270">-設定**識別碼**到*SQLNotifyPort*</span><span class="sxs-lookup"><span data-stu-id="e97a9-270">- Set **Identifier** to *SQLNotifyPort*</span></span><br /><br /> <span data-ttu-id="e97a9-271">-設定**型別**到*SQLNotifyPortType*</span><span class="sxs-lookup"><span data-stu-id="e97a9-271">- Set **Type** to *SQLNotifyPortType*</span></span><br /><br /> <span data-ttu-id="e97a9-272">-設定**通訊模式**到*單向*</span><span class="sxs-lookup"><span data-stu-id="e97a9-272">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="e97a9-273">-設定**通訊方向**到*接收*</span><span class="sxs-lookup"><span data-stu-id="e97a9-273">- Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="e97a9-274">SaveMessagePort</span><span class="sxs-lookup"><span data-stu-id="e97a9-274">SaveMessagePort</span></span>|<span data-ttu-id="e97a9-275">-設定**識別碼**到*SaveMessagePort*</span><span class="sxs-lookup"><span data-stu-id="e97a9-275">- Set **Identifier** to *SaveMessagePort*</span></span><br /><br /> <span data-ttu-id="e97a9-276">-設定**型別**到*SaveMessagePortType*</span><span class="sxs-lookup"><span data-stu-id="e97a9-276">- Set **Type** to *SaveMessagePortType*</span></span><br /><br /> <span data-ttu-id="e97a9-277">-設定**通訊模式**到*單向*</span><span class="sxs-lookup"><span data-stu-id="e97a9-277">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="e97a9-278">-設定**通訊方向**到*傳送*</span><span class="sxs-lookup"><span data-stu-id="e97a9-278">- Set **Communication Direction** to *Send*</span></span><br /><br /> <span data-ttu-id="e97a9-279">-建立作業*通知*。</span><span class="sxs-lookup"><span data-stu-id="e97a9-279">- Create an operation *Notify*.</span></span> <span data-ttu-id="e97a9-280">這項作業用於通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-280">This operation is used for notification messages.</span></span><br /><br /> <span data-ttu-id="e97a9-281">-建立作業*選取*。</span><span class="sxs-lookup"><span data-stu-id="e97a9-281">- Create an operation *Select*.</span></span> <span data-ttu-id="e97a9-282">此作業可用於選取的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-282">This operation is used for select response messages.</span></span>|  
|<span data-ttu-id="e97a9-283">SQLOutboundPort</span><span class="sxs-lookup"><span data-stu-id="e97a9-283">SQLOutboundPort</span></span>|<span data-ttu-id="e97a9-284">-設定**識別碼**到*SQLOutboundPort*</span><span class="sxs-lookup"><span data-stu-id="e97a9-284">- Set **Identifier** to *SQLOutboundPort*</span></span><br /><br /> <span data-ttu-id="e97a9-285">-設定**型別**到*SQLOutboundPortType*</span><span class="sxs-lookup"><span data-stu-id="e97a9-285">- Set **Type** to *SQLOutboundPortType*</span></span><br /><br /> <span data-ttu-id="e97a9-286">-設定**通訊模式**到*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="e97a9-286">- Set **Communication Pattern** to *Request-Response*</span></span><br /><br /> <span data-ttu-id="e97a9-287">-設定**通訊方向**到*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="e97a9-287">- Set **Communication Direction** to *Send-Receive*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a><span data-ttu-id="e97a9-288">為動作圖形指定訊息，並連接到連接埠</span><span class="sxs-lookup"><span data-stu-id="e97a9-288">Specify Messages for Action Shapes and Connect to Ports</span></span>  
 <span data-ttu-id="e97a9-289">下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。</span><span class="sxs-lookup"><span data-stu-id="e97a9-289">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="e97a9-290">先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。</span><span class="sxs-lookup"><span data-stu-id="e97a9-290">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="e97a9-291">形狀圖</span><span class="sxs-lookup"><span data-stu-id="e97a9-291">Shape</span></span>|<span data-ttu-id="e97a9-292">屬性</span><span class="sxs-lookup"><span data-stu-id="e97a9-292">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="e97a9-293">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="e97a9-293">ReceiveNotification</span></span>|<span data-ttu-id="e97a9-294">-設定**訊息**到*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="e97a9-294">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="e97a9-295">-設定**作業**到*SQLNotifyPort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="e97a9-295">- Set **Operation** to *SQLNotifyPort.Notify.Request*</span></span>|  
|<span data-ttu-id="e97a9-296">SaveNotification</span><span class="sxs-lookup"><span data-stu-id="e97a9-296">SaveNotification</span></span>|<span data-ttu-id="e97a9-297">-設定**訊息**到*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="e97a9-297">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="e97a9-298">-設定**作業**到*SaveMessagePort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="e97a9-298">- Set **Operation** to *SaveMessagePort.Notify.Request*</span></span>|  
|<span data-ttu-id="e97a9-299">SendSelectMessage</span><span class="sxs-lookup"><span data-stu-id="e97a9-299">SendSelectMessage</span></span>|<span data-ttu-id="e97a9-300">-設定**訊息**到*選取*</span><span class="sxs-lookup"><span data-stu-id="e97a9-300">- Set **Message** to *Select*</span></span><br /><br /> <span data-ttu-id="e97a9-301">-設定**作業**到*SQLOutboundPort.Select.Request*</span><span class="sxs-lookup"><span data-stu-id="e97a9-301">- Set **Operation** to *SQLOutboundPort.Select.Request*</span></span>|  
|<span data-ttu-id="e97a9-302">ReceiveSelectResponse</span><span class="sxs-lookup"><span data-stu-id="e97a9-302">ReceiveSelectResponse</span></span>|<span data-ttu-id="e97a9-303">此訊息通知記錄已更新 Employee 資料表中。\*</span><span class="sxs-lookup"><span data-stu-id="e97a9-303">- Set **Message** to *SelectResponse*</span></span><br /><br /> <span data-ttu-id="e97a9-304">請注意，值\**項目是 「 更新 」。*</span><span class="sxs-lookup"><span data-stu-id="e97a9-304">- Set **Operation** to *SQLOutboundPort.Select.Response*</span></span>|  
|<span data-ttu-id="e97a9-305">SaveSelectResponse</span><span class="sxs-lookup"><span data-stu-id="e97a9-305">SaveSelectResponse</span></span>|<span data-ttu-id="e97a9-306">此訊息通知記錄已更新 Employee 資料表中。\*</span><span class="sxs-lookup"><span data-stu-id="e97a9-306">- Set **Message** to *SelectResponse*</span></span><br /><br /> <span data-ttu-id="e97a9-307">第二個通知之後，配接器會執行 Select 陳述式。\*</span><span class="sxs-lookup"><span data-stu-id="e97a9-307">- Set **Operation** to *SaveMessagePort.Select.Request*</span></span>|  
  
 <span data-ttu-id="e97a9-308">您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="e97a9-308">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="e97a9-309">您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e97a9-309">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e97a9-310">如需詳細資訊，請參閱 <<c0> [ 建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-310">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="e97a9-311">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="e97a9-311">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="e97a9-312">您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程**在 BizTalk Server 管理主控台 窗格。</span><span class="sxs-lookup"><span data-stu-id="e97a9-312">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the BizTalk Server Administration console.</span></span> <span data-ttu-id="e97a9-313">您必須使用 BizTalk Server 管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="e97a9-313">You must use the BizTalk Server Administration console to configure the application.</span></span> <span data-ttu-id="e97a9-314">如需逐步解說，請參閱 <<c0> [ 逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-314">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>
  
 <span data-ttu-id="e97a9-315">設定應用程式包含：</span><span class="sxs-lookup"><span data-stu-id="e97a9-315">Configuring an application involves:</span></span>  
  
- <span data-ttu-id="e97a9-316">選取應用程式主機。</span><span class="sxs-lookup"><span data-stu-id="e97a9-316">Selecting a host for the application.</span></span>  
  
- <span data-ttu-id="e97a9-317">對應您在您在 BizTalk Server 管理主控台中的實體連接埠的協調流程中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e97a9-317">Mapping the ports that you created in your orchestration to physical ports in the BizTalk Server Administration console.</span></span> <span data-ttu-id="e97a9-318">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="e97a9-318">For this orchestration you must:</span></span>  
  
  - <span data-ttu-id="e97a9-319">不過，因為現在具有狀態為 0，則需要不有任何記錄，所以配接器會取得空的回應，如下列所示。</span><span class="sxs-lookup"><span data-stu-id="e97a9-319">Define a physical WCF-Custom or WCF-SQL one-way receive port.</span></span> <span data-ttu-id="e97a9-320">如需有關繫結檔案的詳細資訊，請參閱 <<c0>  重複使用的 SQL 配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="e97a9-320">This port listens for notifications coming from the SQL Server database.</span></span> <span data-ttu-id="e97a9-321">如需有關如何建立連接埠的資訊，請參閱 <<c0> [ 手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-321">For information about how to create ports, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).</span></span> <span data-ttu-id="e97a9-322">請確定指定接收埠的下列繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-322">Make sure you specify the following binding properties for the receive port.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e97a9-323">您不需要執行此步驟中，如果您在設計階段指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e97a9-323">You do not need to perform this step if you specified the binding properties at design time.</span></span> <span data-ttu-id="e97a9-324">在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠中，設定必要的繫結屬性，藉由匯入所建立的繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e97a9-324">In such a case, you can create a WCF-custom or WCF-SQL receive port, with the required binding properties set, by importing the binding file created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="e97a9-325">如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-325">For more information see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span>  
  
    |<span data-ttu-id="e97a9-326">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="e97a9-326">Binding Property</span></span>|<span data-ttu-id="e97a9-327">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="e97a9-327">Value</span></span>|  
    |----------------------|-----------|  
    |<span data-ttu-id="e97a9-328">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="e97a9-328">**InboundOperationType**</span></span>|<span data-ttu-id="e97a9-329">將此設為**通知**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-329">Set this to **Notification**.</span></span>|  
    |<span data-ttu-id="e97a9-330">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="e97a9-330">**NotificationStatement**</span></span>|<span data-ttu-id="e97a9-331">將此設為：</span><span class="sxs-lookup"><span data-stu-id="e97a9-331">Set this to:</span></span><br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> <span data-ttu-id="e97a9-332">**注意：** 您必須特別指定的資料行名稱的陳述式中，這個 SELECT 陳述式中所示。</span><span class="sxs-lookup"><span data-stu-id="e97a9-332">**Note:** You must specifically specify the column names in the statement as shown in this SELECT statement.</span></span> <span data-ttu-id="e97a9-333">此外，您一律必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="e97a9-333">Also, you must always specify the table name along with the schema name.</span></span> <span data-ttu-id="e97a9-334">例如， `dbo.Employee`。</span><span class="sxs-lookup"><span data-stu-id="e97a9-334">For example, `dbo.Employee`.</span></span>|  
    |<span data-ttu-id="e97a9-335">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="e97a9-335">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="e97a9-336">將此設為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="e97a9-336">Set this to **True**.</span></span>|  
  
     <span data-ttu-id="e97a9-337">如需不同的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-337">For more information about the different binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e97a9-338">我們建議您執行使用的輸入的操作時設定的交易隔離等級和交易等待時間[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e97a9-338">We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="e97a9-339">您可以執行加上服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。</span><span class="sxs-lookup"><span data-stu-id="e97a9-339">You can do so by adding the service behavior while configuring the WCF-Custom or WCF-SQL receive port.</span></span> <span data-ttu-id="e97a9-340">如需有關如何新增服務行為的指示，請參閱[設定交易隔離等級和交易等待時間，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-340">For instruction on how to add the service behavior, see [Configure Transaction Isolation Level and Transaction Timeout with SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).</span></span>  
  
  - <span data-ttu-id="e97a9-341">定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e97a9-341">Define a physical WCF-Custom or WCF-SQL send port to send messages to the SQL Server database.</span></span> <span data-ttu-id="e97a9-342">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="e97a9-342">You must also specify the action in the send port.</span></span>  
  
  - <span data-ttu-id="e97a9-343">硬碟和對應的檔案連接埠，其中的 BizTalk 協調流程會從卸除訊息的 SQL Server 資料庫上定義的位置。</span><span class="sxs-lookup"><span data-stu-id="e97a9-343">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the messages from the SQL Server database.</span></span> <span data-ttu-id="e97a9-344">這些會收到來自 SQL Server 的通知訊息和 select 的訊息，而且您透過 WCF 自訂或 WCF-SQL 執行更新作業的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e97a9-344">These will be the notification messages received from SQL Server and messages for the Select and Update operation you perform through the WCF-Custom or WCF-SQL send port.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="e97a9-345">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="e97a9-345">Starting the Application</span></span>  
 <span data-ttu-id="e97a9-346">您必須啟動 BizTalk 應用程式從 SQL Server 資料庫中接收通知訊息，並用來執行後續的 Select 和 Update 作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-346">You must start the BizTalk application for receiving notification messages from the SQL Server database and for performing the subsequent Select and Update operations.</span></span> <span data-ttu-id="e97a9-347">如需有關啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-347">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>
  
 <span data-ttu-id="e97a9-348">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="e97a9-348">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="e97a9-349">Wcf-custom 或 WCF-SQL 單向接收埠，以從 SQL Server 資料庫執行時接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a9-349">The WCF-Custom or WCF-SQL one-way receive port, which receives the notification messages from the SQL Server database is running.</span></span>  
  
-   <span data-ttu-id="e97a9-350">選取要執行的 WCF 自訂] 或 [WCF-SQL 傳送連接埠和員工資料表上的更新作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="e97a9-350">The WCF-Custom or WCF-SQL send port to perform Select and Update operations on the Employee table is running.</span></span>  
  
-   <span data-ttu-id="e97a9-351">FILE 傳送埠，會從 SQL Server 中接收的訊息，正在執行。</span><span class="sxs-lookup"><span data-stu-id="e97a9-351">The FILE send port, which receives messages from SQL Server, is running.</span></span>  
  
-   <span data-ttu-id="e97a9-352">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="e97a9-352">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="e97a9-353">執行作業</span><span class="sxs-lookup"><span data-stu-id="e97a9-353">Executing the Operation</span></span>  
 <span data-ttu-id="e97a9-354">若要執行這項作業，您必須將記錄插入員工資料表。</span><span class="sxs-lookup"><span data-stu-id="e97a9-354">To execute this operation, you must insert a record into the Employee table.</span></span> <span data-ttu-id="e97a9-355">讓我們假設您插入具有下列詳細資料的記錄：</span><span class="sxs-lookup"><span data-stu-id="e97a9-355">Let us assume you insert a record with following details:</span></span>  
  
```  
Name = John Smith  
Designation = Manager  
Salary = 100000  
```  
  
 <span data-ttu-id="e97a9-356">此外，請確定選取要執行的 XML 訊息，並更新作業將會位於 C:\TestLocation\MessageIn。</span><span class="sxs-lookup"><span data-stu-id="e97a9-356">Also, make sure the XML message to perform Select and Update operations is available at C:\TestLocation\MessageIn.</span></span> <span data-ttu-id="e97a9-357">XML 檔案應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="e97a9-357">The XML file should resemble the following:</span></span>  
  
```  
<Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Columns>Employee_ID,Name,Status</Columns>  
  <Query>where Status=0;UPDATE Employee SET Status=1 WHERE Status=0</Query>  
</Select>  
```  
  
 <span data-ttu-id="e97a9-358">一旦插入記錄時，下列的一組動作進行相同的順序：</span><span class="sxs-lookup"><span data-stu-id="e97a9-358">Once the record is inserted, the following set of actions take place, in the same sequence:</span></span>  
  
-   <span data-ttu-id="e97a9-359">配接器接收通知訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e97a9-359">The adapter receives a notification message that resembles the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="e97a9-360">此訊息會告知 Employee 資料表中已插入一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="e97a9-360">This message notifies that a record was inserted in the Employee table.</span></span> <span data-ttu-id="e97a9-361">請注意，值`<Info>`項目是 「 插入 」。</span><span class="sxs-lookup"><span data-stu-id="e97a9-361">Note that the value for the `<Info>` element is “Insert”.</span></span>  
  
-   <span data-ttu-id="e97a9-362">配接器執行選取的作業。</span><span class="sxs-lookup"><span data-stu-id="e97a9-362">The adapter executes the Select operation.</span></span> <span data-ttu-id="e97a9-363">因為選取的 XML 作業也包括 Update 陳述式，也會執行 Update 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e97a9-363">Because the Select operation XML also includes an Update statement, the Update statement is also executed.</span></span> <span data-ttu-id="e97a9-364">SQL Server 的下一個回應是 Select 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e97a9-364">The next response from SQL Server is for the Select statement.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <SelectResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <SelectResult>  
        <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
          <Employee_ID>10006</Employee_ID>   
          <Name>John</Name>   
          <Status>0</Status>  
        </Employee>  
      </SelectResult>  
    </SelectResponse>  
    ```  
  
     <span data-ttu-id="e97a9-365">此回應會顯示一筆記錄插入員工資料表，以及該記錄的狀態是 0。</span><span class="sxs-lookup"><span data-stu-id="e97a9-365">This response shows that a record was inserted into the Employee table and the Status for that record is 0.</span></span>  
  
-   <span data-ttu-id="e97a9-366">Select 陳述式的一部分，也會執行 Update 陳述式，以及新記錄的狀態資料行變更為 1。</span><span class="sxs-lookup"><span data-stu-id="e97a9-366">As part of the Select statement, the Update statement is also executed and the Status column for the new record is changed to 1.</span></span> <span data-ttu-id="e97a9-367">這會再次觸發另一個通知，從 SQL Server 和配接器接收對應的通知訊息，類似下列：</span><span class="sxs-lookup"><span data-stu-id="e97a9-367">This again triggers another notification from SQL Server and the adapter receives a corresponding notification message, that resembles the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Update</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="e97a9-368">此訊息通知記錄已更新 Employee 資料表中。</span><span class="sxs-lookup"><span data-stu-id="e97a9-368">This message notifies that a record was updated in the Employee table.</span></span> <span data-ttu-id="e97a9-369">請注意，值`<Info>`項目是 「 更新 」。</span><span class="sxs-lookup"><span data-stu-id="e97a9-369">Note that the value for the `<Info>` element is “Update”.</span></span>  
  
-   <span data-ttu-id="e97a9-370">第二個通知之後，配接器會執行 Select 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e97a9-370">After the second notification, the adapter executes the Select statement.</span></span> <span data-ttu-id="e97a9-371">不過，因為現在具有狀態為 0，則需要不有任何記錄，所以配接器會取得空的回應，如下列所示。</span><span class="sxs-lookup"><span data-stu-id="e97a9-371">However, because there are no records now that have Status as 0, the adapter gets an empty response resembling the following.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <SelectResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <SelectResult />   
    </SelectResponse>  
    ```  
  
## <a name="best-practices"></a><span data-ttu-id="e97a9-372">最佳作法</span><span class="sxs-lookup"><span data-stu-id="e97a9-372">Best Practices</span></span>  
 <span data-ttu-id="e97a9-373">您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。</span><span class="sxs-lookup"><span data-stu-id="e97a9-373">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="e97a9-374">一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立傳送埠和接收相同的協調流程的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e97a9-374">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create the send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="e97a9-375">如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用的 SQL 配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a9-375">For more information about binding files, see [Reuse SQL adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e97a9-376">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e97a9-376">See Also</span></span>  
 [<span data-ttu-id="e97a9-377">接收使用 BizTalk Server 的 SQL 查詢通知</span><span class="sxs-lookup"><span data-stu-id="e97a9-377">Receive SQL Query Notifications using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)