---
title: 使用 BizTalk Server 的 sql 查詢通知以累加的方式接收 |Microsoft 文件
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
ms.openlocfilehash: 6fc9eda3ba1bee61b4737428f41870fc31504e3a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967924"
---
# <a name="receive-query-notifications-incrementally-from-sql-using-biztalk-server"></a><span data-ttu-id="b3b3d-102">使用 BizTalk Server 的 sql 查詢通知以累加的方式接收</span><span class="sxs-lookup"><span data-stu-id="b3b3d-102">Receive Query Notifications Incrementally from SQL using BizTalk Server</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="b3b3d-103">為了簡短起見，本主題只說明如何以累加方式收到通知。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-103">For the sake of brevity, this topic only describes how to receive notifications incrementally.</span></span> <span data-ttu-id="b3b3d-104">在商務案例中，協調流程必須在理想情況下包含擷取的收到的通知訊息類型，然後再執行任何後續作業的邏輯。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-104">In business scenarios, the orchestration must ideally include the logic to extract the kind of notification message received and then perform any subsequent operations.</span></span> <span data-ttu-id="b3b3d-105">換句話說，本主題中所述的協調流程必須建立在協調流程中所述之上[處理通知訊息，以便完成特定工作中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-105">In other words, the orchestration described in this topic must be built on top of the orchestration described in [Process notification messages to complete specific tasks in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md).</span></span>  
  
 <span data-ttu-id="b3b3d-106">本主題示範如何設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]來接收從 SQL Server 資料庫的累加式的查詢通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-106">This topic demonstrates how to configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive incremental query notification messages from a SQL Server database.</span></span> <span data-ttu-id="b3b3d-107">為了示範累加通知，請考慮的資料表，員工與 「 狀態 」 資料行。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-107">To demonstrate incremental notifications, consider a table, Employee, with a “Status” column.</span></span> <span data-ttu-id="b3b3d-108">當新的記錄插入此資料表時，[狀態] 欄的值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-108">When a new record is inserted to this table, the value of the Status column is set to 0.</span></span> <span data-ttu-id="b3b3d-109">您可以設定配接器接收累加的通知，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-109">You can configure the adapter to receive incremental notifications by doing the following:</span></span>  
  
-   <span data-ttu-id="b3b3d-110">註冊使用 SQL 陳述式可擷取狀態 資料行具有 0 的所有記錄的通知。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-110">Register for notifications using a SQL statement that retrieves all records that have Status column as 0.</span></span> <span data-ttu-id="b3b3d-111">您可以藉由指定的 SQL 陳述式**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-111">You can do so by specifying the SQL statement for the **NotificationStatement** binding property.</span></span>  
  
-   <span data-ttu-id="b3b3d-112">尚未收到的通知訊息的資料列，更新 [狀態] 資料行設為 1。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-112">For rows for which notification messages have been received, update the Status column to 1.</span></span>  
  
 <span data-ttu-id="b3b3d-113">本主題示範如何建立 BizTalk 協調流程和設定 BizTalk 應用程式，以達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-113">This topic demonstrates how to create a BizTalk orchestration and configure a BizTalk application to achieve this.</span></span>  
  
## <a name="configuring-notifications-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="b3b3d-114">使用 SQL 配接器繫結屬性中設定通知</span><span class="sxs-lookup"><span data-stu-id="b3b3d-114">Configuring Notifications with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="b3b3d-115">下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結，您用來設定 SQL Server 從接收通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-115">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure receiving notifications from SQL Server.</span></span> <span data-ttu-id="b3b3d-116">您必須同時設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-116">You must specify these binding properties while configuring the receive port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3b3d-117">您可以選擇指定這些繫結內容產生的結構描述時**通知**作業，即使它不是強制性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-117">You may choose to specify these binding properties when generating the schema for the **Notification** operation, even though it is not mandatory.</span></span> <span data-ttu-id="b3b3d-118">如果您這樣做，連接埠繫結檔，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-118">If you do so, the port binding file that the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] generates as part of the metadata generation also contains the values you specify for the binding properties.</span></span> <span data-ttu-id="b3b3d-119">您可以稍後匯入此繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台建立 wcf-custom 或 WCF SQL 接收埠以繫結已設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-119">You can later import this binding file in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create the WCF-custom or WCF-SQL receive port with the binding properties already set.</span></span> <span data-ttu-id="b3b3d-120">如需有關如何建立使用該繫結檔案的連接埠的詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-120">For more information about creating a port using the binding file, see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span>  
  
|<span data-ttu-id="b3b3d-121">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="b3b3d-121">Binding Property</span></span>|<span data-ttu-id="b3b3d-122">Description</span><span class="sxs-lookup"><span data-stu-id="b3b3d-122">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="b3b3d-123">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="b3b3d-123">**InboundOperationType**</span></span>|<span data-ttu-id="b3b3d-124">指定輸入您想要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-124">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="b3b3d-125">若要接收通知訊息，將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-125">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="b3b3d-126">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="b3b3d-126">**NotificationStatement**</span></span>|<span data-ttu-id="b3b3d-127">指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序\>) 用來註冊查詢通知。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-127">Specifies the SQL statement (SELECT or EXEC \<stored procedure\>) used to register for query notifications.</span></span> <span data-ttu-id="b3b3d-128">在結果集為指定的 SQL 陳述式變更時，才配接器從 SQL Server 取得通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-128">The adapter gets a notification message from SQL Server only when the result set for the specified SQL statement changes.</span></span>|  
|<span data-ttu-id="b3b3d-129">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="b3b3d-129">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="b3b3d-130">指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-130">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="b3b3d-131">如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-131">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="b3b3d-132">如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]進一步要從 SQL Server 中接收通知，閱讀。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-132">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive notifications from SQL Server, read further.</span></span>  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a><span data-ttu-id="b3b3d-133">本主題示範接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="b3b3d-133">How This Topic Demonstrates Receiving Notification Messages</span></span>  
 <span data-ttu-id="b3b3d-134">若要示範如何[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援從 SQL Server 中接收通知訊息，本主題將示範如何設定配接器收到的員工資料表的變更通知。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-134">To demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving notification messages from SQL Server, this topic will demonstrate how to configure the adapter to receive notifications for changes to an Employee table.</span></span> <span data-ttu-id="b3b3d-135">假設員工資料表的資料行 Employee_ID、 名稱和狀態。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-135">Assume that the Employee table has columns Employee_ID, Name, and Status.</span></span> <span data-ttu-id="b3b3d-136">每當加入為新員工，[狀態] 欄的值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-136">Whenever a new employee is added, the value of the Status column is set to 0.</span></span>  
  
 <span data-ttu-id="b3b3d-137">若要示範接收通知，請執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-137">To demonstrate receiving notifications, do the following:</span></span>  
  
-   <span data-ttu-id="b3b3d-138">產生結構描述的**通知**（輸入作業），和**選取**（輸出作業） 的員工資料表。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-138">Generate schema for the **Notification** (inbound operation), and **Select** (outbound operation) on the Employee table.</span></span>  
  
-   <span data-ttu-id="b3b3d-139">建立具有下列的協調流程：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-139">Create an orchestration that has the following:</span></span>  
  
    -   <span data-ttu-id="b3b3d-140">要接收通知訊息的接收位置。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-140">A receive location to receive notification messages.</span></span> <span data-ttu-id="b3b3d-141">您可以藉由指定 SELECT 陳述式設定通知：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-141">You can configure for notification by specifying the SELECT statement as:</span></span>  
  
        ```  
        SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="b3b3d-142">具體來說，您必須指定資料行名稱中的陳述式中所示 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-142">You must specifically specify the column names in the statement as shown in this SELECT statement.</span></span> <span data-ttu-id="b3b3d-143">此外，您永遠必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-143">Also, you must always specify the table name along with the schema name.</span></span> <span data-ttu-id="b3b3d-144">例如， `dbo.Employee`。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-144">For example, `dbo.Employee`.</span></span>  
  
    -   <span data-ttu-id="b3b3d-145">要更新的通知已傳送的資料列的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-145">A send port to update the rows for which notification has already been sent.</span></span> <span data-ttu-id="b3b3d-146">您將此值設定為 1 的 [狀態] 欄中。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-146">You do so by setting the value in the Status column to 1.</span></span> <span data-ttu-id="b3b3d-147">您可以選取作業的一部分傳送至配接器的下列訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-147">You can do this as part of the Select operation by sending the following message to the adapter.</span></span>  
  
        ```  
        <Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
          <Columns>Employee_ID,Name,Status</Columns>  
          <Query>where Status=0;UPDATE Employee SET Status=1 WHERE Status=0</Query>  
        </Select>  
        ```  
  
         <span data-ttu-id="b3b3d-148">在此訊息中，做為一部分`<Query>`元素中，指定 UPDATE 陳述式來更新狀態 資料行。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-148">In this message, as part of the `<Query>` element, you specify the UPDATE statement to update the Status column.</span></span> <span data-ttu-id="b3b3d-149">請注意這項作業必須在接收通知訊息，以便處理的資料列更新之後執行。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-149">Note that this operation must be executed after receiving the notification messages so that the processed rows are updated.</span></span> <span data-ttu-id="b3b3d-150">若要執行離開等候取得通知回應，然後再手動卸除更新的資料列的要求訊息的負擔，您將會產生更新協調流程本身內的資料列的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-150">To do away with the overhead of waiting to get the notification response and then manually dropping a request message to update the rows, you will generate the request message for updating the rows within the orchestration itself.</span></span> <span data-ttu-id="b3b3d-151">您可以使用**建構訊息**協調流程內的圖形。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-151">You can do so by using the **Construct Message** shape within an orchestration.</span></span>  
  
## <a name="how-to-receive-notification-messages-from-the-sql-server-database"></a><span data-ttu-id="b3b3d-152">如何從 SQL Server 資料庫中接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="b3b3d-152">How to Receive Notification Messages from the SQL Server Database</span></span>  
 <span data-ttu-id="b3b3d-153">使用 SQL Server 資料庫上執行操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及程序中所述的工作[開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-153">Performing an operation on the SQL Server database using [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves the procedural tasks described in [Building blocks to develop BizTalk applications with the SQL adapter](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md).</span></span> <span data-ttu-id="b3b3d-154">若要設定要接收通知訊息的介面卡，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-154">To configure the adapter to receive notification messages, these tasks are:</span></span>  
  
1.  <span data-ttu-id="b3b3d-155">建立 BizTalk 專案，然後再產生結構描述的**通知**（輸入作業） 和**選取**（輸出作業） 的員工資料表。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-155">Create a BizTalk project, and then generate schema for the **Notification** (inbound operation) and **Select** (outbound operation) on the Employee table.</span></span> <span data-ttu-id="b3b3d-156">您可以選擇性地指定值**InboundOperationType**和**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-156">Optionally, you can specify values for the **InboundOperationType** and **NotificationStatement** binding properties.</span></span>  
  
2.  <span data-ttu-id="b3b3d-157">從 SQL Server 資料庫中接收通知的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-157">Create a message in the BizTalk project for receiving notification from the SQL Server database.</span></span>  
  
3.  <span data-ttu-id="b3b3d-158">SQL Server 資料庫上執行選取的資訊，並接收回應訊息的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-158">Create messages in the BizTalk project for performing the Select information on the SQL Server database and receiving response messages.</span></span>  
  
4.  <span data-ttu-id="b3b3d-159">建立的協調流程，會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-159">Create an orchestration that does the following:</span></span>  
  
    -   <span data-ttu-id="b3b3d-160">從 SQL Server 中接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-160">Receives notification message from SQL Server.</span></span>  
  
    -   <span data-ttu-id="b3b3d-161">建立選取及更新的資料列收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-161">Creates a message to select and update the rows for which notification is received.</span></span>  
  
    -   <span data-ttu-id="b3b3d-162">將此訊息傳送到 SQL Server 更新的資料列，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-162">Sends this message to the SQL Server to update the rows and receives a response.</span></span>  
  
5.  <span data-ttu-id="b3b3d-163">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-163">Build and deploy the BizTalk project.</span></span>  
  
6.  <span data-ttu-id="b3b3d-164">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-164">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b3b3d-165">輸入的作業，像是接收通知訊息，您必須只設定單向的 WCF 自訂或 WCF SQL 接收埠。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-165">For inbound operations, like receiving notification messages, you must only configure a one-way WCF-Custom or WCF-SQL receive port.</span></span> <span data-ttu-id="b3b3d-166">雙向 Wcf-custom 或 WCF SQL 接收埠的輸入作業不支援。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-166">Two-way WCF-Custom or WCF-SQL receive ports are not supported for inbound operations.</span></span>  
  
7.  <span data-ttu-id="b3b3d-167">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-167">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="b3b3d-168">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-168">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="sample-based-on-this-topic"></a><span data-ttu-id="b3b3d-169">根據本主題的範例</span><span class="sxs-lookup"><span data-stu-id="b3b3d-169">Sample Based on This Topic</span></span>  
 <span data-ttu-id="b3b3d-170">基礎的範例，IncrementalNotification，本主題隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-170">A sample, IncrementalNotification, based on this topic is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="b3b3d-171">如需詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-171">For more information, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="b3b3d-172">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="b3b3d-172">Generating Schema</span></span>  
 <span data-ttu-id="b3b3d-173">您必須產生的結構描述**通知**作業和**選取**「 員工 」 資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-173">You must generate the schema for the **Notification** operation and **Select** operation on Employee table.</span></span> <span data-ttu-id="b3b3d-174">請參閱[取得中繼資料使用 SQL 配接器的 Visual Studio 中的 SQL Server 作業](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-174">See [Get metadata for SQL Server operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) for more information about how to generate the schema.</span></span> <span data-ttu-id="b3b3d-175">產生結構描述時，請執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-175">Perform the following tasks when generating the schema.</span></span> <span data-ttu-id="b3b3d-176">如果您不想要在設計階段指定的繫結屬性，請略過第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-176">Skip the first step if you do not want to specify the binding properties at design time.</span></span>  
  
1.  <span data-ttu-id="b3b3d-177">指定的值**InboundOperationType**和**NotificationStatement**時產生結構描述繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-177">Specify a value for **InboundOperationType** and **NotificationStatement** binding properties while generating the schema.</span></span> <span data-ttu-id="b3b3d-178">如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-178">For more information about this binding property, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="b3b3d-179">如需有關如何指定繫結屬性的指示，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-179">For instructions on how to specify binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
2.  <span data-ttu-id="b3b3d-180">選取合約類型為**服務 （輸入操作）**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-180">Select the contract type as **Service (Inbound operations)**.</span></span>  
  
3.  <span data-ttu-id="b3b3d-181">產生結構描述的**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-181">Generate schema for the **Notification** operation.</span></span>  
  
4.  <span data-ttu-id="b3b3d-182">選取合約類型為**用戶端 （輸出作業）**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-182">Select the contract type as **Client (Outbound operations)**.</span></span>  
  
5.  <span data-ttu-id="b3b3d-183">產生結構描述的**選取**作業**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-183">Generate schema for the **Select** operation on **Employee** table.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="b3b3d-184">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="b3b3d-184">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="b3b3d-185">您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-185">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="b3b3d-186">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-186">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="b3b3d-187">一旦產生結構描述時，您必須訊息連結之協調流程檢視中的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-187">Once the schema is generated, you must link it to the messages from the Orchestration view of the BizTalk project.</span></span>  
  
 <span data-ttu-id="b3b3d-188">本主題中，您必須建立三個訊息，一個用於接收通知，從 SQL Server 資料庫、 要執行選取的作業，以及一個用來接收選取作業的回應。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-188">For this topic, you must create three messages—one to receive notifications from the SQL Server database, one to perform the Select operation, and one to receive the response for Select operation.</span></span>  
  
 <span data-ttu-id="b3b3d-189">執行下列步驟來建立訊息，並將它們連結至結構描述。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-189">Perform the following steps to create messages and link them to schema.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="b3b3d-190">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="b3b3d-190">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="b3b3d-191">BizTalk 專案中新增協調流程。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-191">Add an orchestration to the BizTalk project.</span></span> <span data-ttu-id="b3b3d-192">從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-192">From the Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="b3b3d-193">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-193">Type a name for the BizTalk orchestration and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="b3b3d-194">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-194">Open the orchestration view window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="b3b3d-195">按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-195">Click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="b3b3d-196">在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-196">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="b3b3d-197">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-197">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="b3b3d-198">在**屬性**窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-198">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="b3b3d-199">使用</span><span class="sxs-lookup"><span data-stu-id="b3b3d-199">Use this</span></span>|<span data-ttu-id="b3b3d-200">動作</span><span class="sxs-lookup"><span data-stu-id="b3b3d-200">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b3b3d-201">識別碼</span><span class="sxs-lookup"><span data-stu-id="b3b3d-201">Identifier</span></span>|<span data-ttu-id="b3b3d-202">輸入 `NotifyReceive`。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-202">Type `NotifyReceive`.</span></span>|  
    |<span data-ttu-id="b3b3d-203">訊息類型</span><span class="sxs-lookup"><span data-stu-id="b3b3d-203">Message Type</span></span>|<span data-ttu-id="b3b3d-204">從下拉式清單中，展開 **結構描述**，然後選取*SQLNotify.Notification*，其中*SQLNotify*是您的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-204">From the drop-down list, expand **Schemas**, and select *SQLNotify.Notification*, where *SQLNotify* is the name of your BizTalk project.</span></span> <span data-ttu-id="b3b3d-205">*通知*是針對產生的結構描述**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-205">*Notification* is the schema generated for the **Notification** operation.</span></span>|  
  
6.  <span data-ttu-id="b3b3d-206">重複步驟 3 以建立兩個新的訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-206">Repeat step 3 to create two new messages.</span></span> <span data-ttu-id="b3b3d-207">在**屬性**窗格新訊息中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-207">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="b3b3d-208">若要設定識別項</span><span class="sxs-lookup"><span data-stu-id="b3b3d-208">Set Identifier to</span></span>|<span data-ttu-id="b3b3d-209">若要設定訊息類型</span><span class="sxs-lookup"><span data-stu-id="b3b3d-209">Set Message Type to</span></span>|  
    |-----------------------|-------------------------|  
    |<span data-ttu-id="b3b3d-210">Select</span><span class="sxs-lookup"><span data-stu-id="b3b3d-210">Select</span></span>|<span data-ttu-id="b3b3d-211">*SQLNotify.TableOperation_dbo_Employee.Select*，其中*TableOperation_dbo_Employee*是針對產生的結構描述**選取**作業</span><span class="sxs-lookup"><span data-stu-id="b3b3d-211">*SQLNotify.TableOperation_dbo_Employee.Select*, where  *TableOperation_dbo_Employee* is the schema generated for the **Select** operation</span></span>|  
    |<span data-ttu-id="b3b3d-212">SelectResponse</span><span class="sxs-lookup"><span data-stu-id="b3b3d-212">SelectResponse</span></span>|<span data-ttu-id="b3b3d-213">*SQLNotify.TableOperation_dbo_Employee.SelectResponse*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-213">*SQLNotify.TableOperation_dbo_Employee.SelectResponse*</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="b3b3d-214">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="b3b3d-214">Setting up the Orchestration</span></span>  
 <span data-ttu-id="b3b3d-215">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收通知訊息從 SQL Server 資料庫，然後更新收到通知的資料列。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-215">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving notification messages from the SQL Server database and then updating the rows for which notification was received.</span></span> <span data-ttu-id="b3b3d-216">在此協調流程中，配接器接收通知訊息，根據指定的 SELECT 陳述式**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-216">In this orchestration, the adapter receives the notification message based on the SELECT statement specified for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="b3b3d-217">檔案位置接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-217">The notification message is received at a FILE location.</span></span> <span data-ttu-id="b3b3d-218">一旦收到回應時，協調流程會建構的訊息，將用來更新資料列，收到通知。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-218">Once the response is received, the orchestration constructs a message that will be used to update the rows for which notification is received.</span></span> <span data-ttu-id="b3b3d-219">在相同的檔案位置也收到這個訊息的回應。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-219">The response for this message is also received at the same FILE location.</span></span>  
  
 <span data-ttu-id="b3b3d-220">因此，您的協調流程必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-220">So, your orchestration must contain the following:</span></span>  
  
-   <span data-ttu-id="b3b3d-221">單向接收埠以接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-221">A one-way receive port to receive notification messages.</span></span>  
  
-   <span data-ttu-id="b3b3d-222">雙向傳送埠以傳送訊息，更新資料列，並接收回應的相同。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-222">A two-way send port to send messages to update rows and receive response for the same.</span></span>  
  
-   <span data-ttu-id="b3b3d-223">A**建構訊息**圖形來建構訊息，來執行更新作業，在協調流程中的。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-223">A **Construct Message** shape to construct messages, to execute the Update operation, within the orchestration.</span></span>  
  
-   <span data-ttu-id="b3b3d-224">FILE 傳送埠以儲存更新作業的回應。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-224">A FILE send port to save the response for the Update operation.</span></span>  
  
-   <span data-ttu-id="b3b3d-225">接收和傳送圖形。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-225">Receive and send shapes.</span></span>  
  
 <span data-ttu-id="b3b3d-226">範例協調流程如下。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-226">A sample orchestration resembles the following.</span></span>  
  
 <span data-ttu-id="b3b3d-227">![協調流程接收的 SQL Server 通知](../../adapters-and-accelerators/adapter-sql/media/f13ad3b8-8161-42e5-a521-424bbf549ad5.gif "f13ad3b8-8161-42e5-a521-424bbf549ad5")</span><span class="sxs-lookup"><span data-stu-id="b3b3d-227">![Orchestration to receive SQL Server notifications](../../adapters-and-accelerators/adapter-sql/media/f13ad3b8-8161-42e5-a521-424bbf549ad5.gif "f13ad3b8-8161-42e5-a521-424bbf549ad5")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="b3b3d-228">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="b3b3d-228">Adding Message Shapes</span></span>  
 <span data-ttu-id="b3b3d-229">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-229">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="b3b3d-230">圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-230">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="b3b3d-231">形狀圖</span><span class="sxs-lookup"><span data-stu-id="b3b3d-231">Shape</span></span>|<span data-ttu-id="b3b3d-232">圖形類型</span><span class="sxs-lookup"><span data-stu-id="b3b3d-232">Shape Type</span></span>|<span data-ttu-id="b3b3d-233">屬性</span><span class="sxs-lookup"><span data-stu-id="b3b3d-233">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="b3b3d-234">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="b3b3d-234">ReceiveNotification</span></span>|<span data-ttu-id="b3b3d-235">Receive</span><span class="sxs-lookup"><span data-stu-id="b3b3d-235">Receive</span></span>|<span data-ttu-id="b3b3d-236">-設定**名稱**至*ReceiveNotification*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-236">- Set **Name** to *ReceiveNotification*</span></span><br /><br /> <span data-ttu-id="b3b3d-237">-設定**啟動**至 *，則為 True*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-237">- Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="b3b3d-238">SaveNotification</span><span class="sxs-lookup"><span data-stu-id="b3b3d-238">SaveNotification</span></span>|<span data-ttu-id="b3b3d-239">Send</span><span class="sxs-lookup"><span data-stu-id="b3b3d-239">Send</span></span>|<span data-ttu-id="b3b3d-240">-設定**名稱**至*SaveNotification*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-240">- Set **Name** to *SaveNotification*</span></span>|  
|<span data-ttu-id="b3b3d-241">SendSelectMessage</span><span class="sxs-lookup"><span data-stu-id="b3b3d-241">SendSelectMessage</span></span>|<span data-ttu-id="b3b3d-242">Send</span><span class="sxs-lookup"><span data-stu-id="b3b3d-242">Send</span></span>|<span data-ttu-id="b3b3d-243">-設定**名稱**至*SendSelectMessage*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-243">- Set **Name** to *SendSelectMessage*</span></span>|  
|<span data-ttu-id="b3b3d-244">ReceiveSelectResponse</span><span class="sxs-lookup"><span data-stu-id="b3b3d-244">ReceiveSelectResponse</span></span>|<span data-ttu-id="b3b3d-245">Receive</span><span class="sxs-lookup"><span data-stu-id="b3b3d-245">Receive</span></span>|<span data-ttu-id="b3b3d-246">-設定**名稱**至*ReceiveSelectResponse*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-246">- Set **Name** to *ReceiveSelectResponse*</span></span>|  
|<span data-ttu-id="b3b3d-247">SaveSelectResponse</span><span class="sxs-lookup"><span data-stu-id="b3b3d-247">SaveSelectResponse</span></span>|<span data-ttu-id="b3b3d-248">Send</span><span class="sxs-lookup"><span data-stu-id="b3b3d-248">Send</span></span>|<span data-ttu-id="b3b3d-249">-設定**名稱**至*SaveSelectResponse*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-249">- Set **Name** to *SaveSelectResponse*</span></span>|  
  
### <a name="adding-construct-message-shape"></a><span data-ttu-id="b3b3d-250">新增 建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="b3b3d-250">Adding Construct Message Shape</span></span>  
 <span data-ttu-id="b3b3d-251">您可以使用**建構訊息**圖形產生作業中的執行 Select 作業要求訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-251">You can use the **Construct Message** shape to generate a request message within the operation to perform the Select operation.</span></span> <span data-ttu-id="b3b3d-252">若要這樣做，您必須新增**建構訊息**圖形，並在其中**訊息指派**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-252">To do so, you must add a **Construct Message** shape and within that a **Message Assignment** shape to your orchestration.</span></span> <span data-ttu-id="b3b3d-253">例如，**訊息指派**圖形叫用來執行選取的作業傳送至 SQL Server 的訊息會產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-253">For this example, the **Message Assignment** shape invokes code that generates a message that is sent to SQL Server to perform the Select operation.</span></span> <span data-ttu-id="b3b3d-254">**訊息指派**圖形也會設定傳送到 SQL Server 之訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-254">The **Message Assignment** shape also sets the action for the message to be sent to SQL Server.</span></span>  
  
 <span data-ttu-id="b3b3d-255">對於 「 建構訊息 」 圖形，設定**建構訊息**屬性**選取**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-255">For the construct message shape, set the **Message Constructed** property to **Select**.</span></span>  
  
 <span data-ttu-id="b3b3d-256">產生回應的程式碼可能是您的 BizTalk 專案相同的 Visual Studio 方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-256">The code to generate the response could be part of the same Visual Studio solution as your BizTalk project.</span></span> <span data-ttu-id="b3b3d-257">產生回應訊息的範例程式碼看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-257">A sample code for generating a response message looks like this.</span></span>  
  
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
  
 <span data-ttu-id="b3b3d-258">如前面的程式碼摘錄無法產生要求訊息中必須有 XML 要求訊息 （如員工資料表的 Select 作業） 所指定的位置`XmlFileLocation`變數。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-258">For the preceding code excerpt to be able to generate a request message, you must have an XML request message (for the Select operation on the Employee table) in the location specified for the `XmlFileLocation` variable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3b3d-259">建置專案之後，會建立 SampleMessageCreator.dll 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-259">After you build the project, SampleMessageCreator.dll will be created in the project directory.</span></span> <span data-ttu-id="b3b3d-260">您必須將此 DLL 加入全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-260">You must add this DLL to the global assembly cache (GAC).</span></span> <span data-ttu-id="b3b3d-261">此外，您必須加入 SampleMessageCreator.dll 當做 BizTalk 專案中的參考。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-261">Also, you must add the SampleMessageCreator.dll as a reference in the BizTalk project.</span></span>  
  
 <span data-ttu-id="b3b3d-262">加入下列運算式來叫用此程式碼從**訊息指派**圖形，並設定訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-262">Add the following expression to invoke this code from the **Message Assignment** shape and to set the action for message.</span></span> <span data-ttu-id="b3b3d-263">若要新增運算式，請按兩下**訊息指派**圖形以開啟 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-263">To add an expression, double-click the **Message Assignment** shape to open the Expression Editor.</span></span>  
  
```  
Select = SampleMessageCreator.SampleMessageCreator.XMLMessageCreator();  
Select(WCF.Action) = "TableOp/Select/dbo/Employee";  
```  
  
### <a name="adding-ports"></a><span data-ttu-id="b3b3d-264">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="b3b3d-264">Adding Ports</span></span>  
 <span data-ttu-id="b3b3d-265">請確定您針對每個邏輯連接埠指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-265">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="b3b3d-266">連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-266">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="b3b3d-267">通訊埠</span><span class="sxs-lookup"><span data-stu-id="b3b3d-267">Port</span></span>|<span data-ttu-id="b3b3d-268">屬性</span><span class="sxs-lookup"><span data-stu-id="b3b3d-268">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="b3b3d-269">SQLNotifyPort</span><span class="sxs-lookup"><span data-stu-id="b3b3d-269">SQLNotifyPort</span></span>|<span data-ttu-id="b3b3d-270">-設定**識別碼**至*SQLNotifyPort*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-270">- Set **Identifier** to *SQLNotifyPort*</span></span><br /><br /> <span data-ttu-id="b3b3d-271">-設定**類型**至*SQLNotifyPortType*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-271">- Set **Type** to *SQLNotifyPortType*</span></span><br /><br /> <span data-ttu-id="b3b3d-272">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-272">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="b3b3d-273">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-273">- Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="b3b3d-274">SaveMessagePort</span><span class="sxs-lookup"><span data-stu-id="b3b3d-274">SaveMessagePort</span></span>|<span data-ttu-id="b3b3d-275">-設定**識別碼**至*SaveMessagePort*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-275">- Set **Identifier** to *SaveMessagePort*</span></span><br /><br /> <span data-ttu-id="b3b3d-276">-設定**類型**至*SaveMessagePortType*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-276">- Set **Type** to *SaveMessagePortType*</span></span><br /><br /> <span data-ttu-id="b3b3d-277">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-277">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="b3b3d-278">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-278">- Set **Communication Direction** to *Send*</span></span><br /><br /> <span data-ttu-id="b3b3d-279">建立作業*通知*。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-279">- Create an operation *Notify*.</span></span> <span data-ttu-id="b3b3d-280">通知訊息使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-280">This operation is used for notification messages.</span></span><br /><br /> <span data-ttu-id="b3b3d-281">建立作業*選取*。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-281">- Create an operation *Select*.</span></span> <span data-ttu-id="b3b3d-282">選取回應訊息使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-282">This operation is used for select response messages.</span></span>|  
|<span data-ttu-id="b3b3d-283">SQLOutboundPort</span><span class="sxs-lookup"><span data-stu-id="b3b3d-283">SQLOutboundPort</span></span>|<span data-ttu-id="b3b3d-284">-設定**識別碼**至*SQLOutboundPort*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-284">- Set **Identifier** to *SQLOutboundPort*</span></span><br /><br /> <span data-ttu-id="b3b3d-285">-設定**類型**至*SQLOutboundPortType*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-285">- Set **Type** to *SQLOutboundPortType*</span></span><br /><br /> <span data-ttu-id="b3b3d-286">-設定**通訊模式**至*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-286">- Set **Communication Pattern** to *Request-Response*</span></span><br /><br /> <span data-ttu-id="b3b3d-287">-設定**通訊方向**至*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-287">- Set **Communication Direction** to *Send-Receive*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a><span data-ttu-id="b3b3d-288">指定動作圖形訊息並連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="b3b3d-288">Specify Messages for Action Shapes and Connect to Ports</span></span>  
 <span data-ttu-id="b3b3d-289">下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-289">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="b3b3d-290">圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-290">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="b3b3d-291">形狀圖</span><span class="sxs-lookup"><span data-stu-id="b3b3d-291">Shape</span></span>|<span data-ttu-id="b3b3d-292">屬性</span><span class="sxs-lookup"><span data-stu-id="b3b3d-292">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="b3b3d-293">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="b3b3d-293">ReceiveNotification</span></span>|<span data-ttu-id="b3b3d-294">-設定**訊息**至*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-294">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="b3b3d-295">-設定**作業**至*SQLNotifyPort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-295">- Set **Operation** to *SQLNotifyPort.Notify.Request*</span></span>|  
|<span data-ttu-id="b3b3d-296">SaveNotification</span><span class="sxs-lookup"><span data-stu-id="b3b3d-296">SaveNotification</span></span>|<span data-ttu-id="b3b3d-297">-設定**訊息**至*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-297">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="b3b3d-298">-設定**作業**至*SaveMessagePort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-298">- Set **Operation** to *SaveMessagePort.Notify.Request*</span></span>|  
|<span data-ttu-id="b3b3d-299">SendSelectMessage</span><span class="sxs-lookup"><span data-stu-id="b3b3d-299">SendSelectMessage</span></span>|<span data-ttu-id="b3b3d-300">-設定**訊息**至*選取*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-300">- Set **Message** to *Select*</span></span><br /><br /> <span data-ttu-id="b3b3d-301">-設定**作業**至*SQLOutboundPort.Select.Request*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-301">- Set **Operation** to *SQLOutboundPort.Select.Request*</span></span>|  
|<span data-ttu-id="b3b3d-302">ReceiveSelectResponse</span><span class="sxs-lookup"><span data-stu-id="b3b3d-302">ReceiveSelectResponse</span></span>|<span data-ttu-id="b3b3d-303">-設定**訊息**至*SelectResponse*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-303">- Set **Message** to *SelectResponse*</span></span><br /><br /> <span data-ttu-id="b3b3d-304">-設定**作業**至*SQLOutboundPort.Select.Response*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-304">- Set **Operation** to *SQLOutboundPort.Select.Response*</span></span>|  
|<span data-ttu-id="b3b3d-305">SaveSelectResponse</span><span class="sxs-lookup"><span data-stu-id="b3b3d-305">SaveSelectResponse</span></span>|<span data-ttu-id="b3b3d-306">-設定**訊息**至*SelectResponse*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-306">- Set **Message** to *SelectResponse*</span></span><br /><br /> <span data-ttu-id="b3b3d-307">-設定**作業**至*SaveMessagePort.Select.Request*</span><span class="sxs-lookup"><span data-stu-id="b3b3d-307">- Set **Operation** to *SaveMessagePort.Select.Request*</span></span>|  
  
 <span data-ttu-id="b3b3d-308">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-308">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="b3b3d-309">您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-309">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="b3b3d-310">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-310">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="b3b3d-311">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="b3b3d-311">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="b3b3d-312">部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-312">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the BizTalk Server Administration console.</span></span> <span data-ttu-id="b3b3d-313">您必須使用 BizTalk Server 管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-313">You must use the BizTalk Server Administration console to configure the application.</span></span> <span data-ttu-id="b3b3d-314">如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-314">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>
  
 <span data-ttu-id="b3b3d-315">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-315">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="b3b3d-316">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-316">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="b3b3d-317">對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-317">Mapping the ports that you created in your orchestration to physical ports in the BizTalk Server Administration console.</span></span> <span data-ttu-id="b3b3d-318">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-318">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="b3b3d-319">定義實體的 WCF 自訂或 WCF-SQL 單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-319">Define a physical WCF-Custom or WCF-SQL one-way receive port.</span></span> <span data-ttu-id="b3b3d-320">此連接埠會接聽來自 SQL Server 資料庫的通知。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-320">This port listens for notifications coming from the SQL Server database.</span></span> <span data-ttu-id="b3b3d-321">如需如何建立連接埠相關資訊，請參閱[手動設定 SQL 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-321">For information about how to create ports, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).</span></span> <span data-ttu-id="b3b3d-322">請確定指定接收埠的下列繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-322">Make sure you specify the following binding properties for the receive port.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="b3b3d-323">您不需要執行這個步驟，如果您在設計階段指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-323">You do not need to perform this step if you specified the binding properties at design time.</span></span> <span data-ttu-id="b3b3d-324">在此情況下，您可以建立 wcf-custom 或 WCF SQL 接收埠，設定必要的繫結屬性，藉由匯入所建立之繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-324">In such a case, you can create a WCF-custom or WCF-SQL receive port, with the required binding properties set, by importing the binding file created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="b3b3d-325">如需詳細資訊，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-325">For more information see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span>  
  
        |<span data-ttu-id="b3b3d-326">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="b3b3d-326">Binding Property</span></span>|<span data-ttu-id="b3b3d-327">值</span><span class="sxs-lookup"><span data-stu-id="b3b3d-327">Value</span></span>|  
        |----------------------|-----------|  
        |<span data-ttu-id="b3b3d-328">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="b3b3d-328">**InboundOperationType**</span></span>|<span data-ttu-id="b3b3d-329">將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-329">Set this to **Notification**.</span></span>|  
        |<span data-ttu-id="b3b3d-330">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="b3b3d-330">**NotificationStatement**</span></span>|<span data-ttu-id="b3b3d-331">將此值設定為：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-331">Set this to:</span></span><br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> <span data-ttu-id="b3b3d-332">**注意：** 您必須明確指定資料行名稱的陳述式中這個 SELECT 陳述式中所示。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-332">**Note:** You must specifically specify the column names in the statement as shown in this SELECT statement.</span></span> <span data-ttu-id="b3b3d-333">此外，您永遠必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-333">Also, you must always specify the table name along with the schema name.</span></span> <span data-ttu-id="b3b3d-334">例如， `dbo.Employee`。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-334">For example, `dbo.Employee`.</span></span>|  
        |<span data-ttu-id="b3b3d-335">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="b3b3d-335">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="b3b3d-336">將此設**True**。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-336">Set this to **True**.</span></span>|  
  
         <span data-ttu-id="b3b3d-337">如需不同的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-337">For more information about the different binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b3b3d-338">我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-338">We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="b3b3d-339">您可以執行新增服務行為設定 Wcf-custom 或 WCF-SQL 時接收埠。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-339">You can do so by adding the service behavior while configuring the WCF-Custom or WCF-SQL receive port.</span></span> <span data-ttu-id="b3b3d-340">如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時，使用 SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-340">For instruction on how to add the service behavior, see [Configure Transaction Isolation Level and Transaction Timeout with SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).</span></span>  
  
    -   <span data-ttu-id="b3b3d-341">定義實體 Wcf-custom 或 WCF SQL 傳送埠將訊息傳送至 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-341">Define a physical WCF-Custom or WCF-SQL send port to send messages to the SQL Server database.</span></span> <span data-ttu-id="b3b3d-342">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-342">You must also specify the action in the send port.</span></span>  
  
    -   <span data-ttu-id="b3b3d-343">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置將訊息從 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-343">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the messages from the SQL Server database.</span></span> <span data-ttu-id="b3b3d-344">這些將會收到來自 SQL Server 的通知訊息和 select 的訊息，並透過 Wcf-custom 或 WCF-SQL 您執行更新作業的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-344">These will be the notification messages received from SQL Server and messages for the Select and Update operation you perform through the WCF-Custom or WCF-SQL send port.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="b3b3d-345">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="b3b3d-345">Starting the Application</span></span>  
 <span data-ttu-id="b3b3d-346">您必須啟動 BizTalk 應用程式接收通知訊息從 SQL Server 資料庫以及執行後續的 Select 和 Update 作業。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-346">You must start the BizTalk application for receiving notification messages from the SQL Server database and for performing the subsequent Select and Update operations.</span></span> <span data-ttu-id="b3b3d-347">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-347">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>
  
 <span data-ttu-id="b3b3d-348">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-348">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="b3b3d-349">Wcf-custom 或 WCF-SQL 單向接收埠，會從 SQL Server 資料庫執行時接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-349">The WCF-Custom or WCF-SQL one-way receive port, which receives the notification messages from the SQL Server database is running.</span></span>  
  
-   <span data-ttu-id="b3b3d-350">Wcf-custom 或 WCF SQL 傳送埠來執行選取而且員工資料表上的更新作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-350">The WCF-Custom or WCF-SQL send port to perform Select and Update operations on the Employee table is running.</span></span>  
  
-   <span data-ttu-id="b3b3d-351">FILE 傳送埠，從 SQL Server 所接收訊息，正在執行。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-351">The FILE send port, which receives messages from SQL Server, is running.</span></span>  
  
-   <span data-ttu-id="b3b3d-352">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-352">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="b3b3d-353">執行作業</span><span class="sxs-lookup"><span data-stu-id="b3b3d-353">Executing the Operation</span></span>  
 <span data-ttu-id="b3b3d-354">若要執行這項作業，您必須將記錄插入員工資料表。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-354">To execute this operation, you must insert a record into the Employee table.</span></span> <span data-ttu-id="b3b3d-355">讓我們假設您將插入的記錄中包含下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-355">Let us assume you insert a record with following details:</span></span>  
  
```  
Name = John Smith  
Designation = Manager  
Salary = 100000  
```  
  
 <span data-ttu-id="b3b3d-356">此外，請確定選取要執行的 XML 訊息，而且更新作業將會位於 C:\TestLocation\MessageIn。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-356">Also, make sure the XML message to perform Select and Update operations is available at C:\TestLocation\MessageIn.</span></span> <span data-ttu-id="b3b3d-357">XML 檔案應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-357">The XML file should resemble the following:</span></span>  
  
```  
<Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Columns>Employee_ID,Name,Status</Columns>  
  <Query>where Status=0;UPDATE Employee SET Status=1 WHERE Status=0</Query>  
</Select>  
```  
  
 <span data-ttu-id="b3b3d-358">一旦記錄插入時，下列的動作集合進行，以相同順序：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-358">Once the record is inserted, the following set of actions take place, in the same sequence:</span></span>  
  
-   <span data-ttu-id="b3b3d-359">配接器接收通知訊息類似如下：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-359">The adapter receives a notification message that resembles the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="b3b3d-360">此訊息會通知 Employee 資料表中插入了資料錄。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-360">This message notifies that a record was inserted in the Employee table.</span></span> <span data-ttu-id="b3b3d-361">請注意，值`<Info>`項目，則 「 插入 」。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-361">Note that the value for the `<Info>` element is “Insert”.</span></span>  
  
-   <span data-ttu-id="b3b3d-362">在 Select 作業執行配接器。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-362">The adapter executes the Select operation.</span></span> <span data-ttu-id="b3b3d-363">因為選取的 XML 作業也會包含 Update 陳述式，也會執行 Update 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-363">Because the Select operation XML also includes an Update statement, the Update statement is also executed.</span></span> <span data-ttu-id="b3b3d-364">從 SQL Server 的下一個回應是 Select 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-364">The next response from SQL Server is for the Select statement.</span></span>  
  
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
  
     <span data-ttu-id="b3b3d-365">此回應會顯示一筆記錄插入員工資料表，和該記錄的狀態是 0。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-365">This response shows that a record was inserted into the Employee table and the Status for that record is 0.</span></span>  
  
-   <span data-ttu-id="b3b3d-366">Select 陳述式的一部分，也會執行 Update 陳述式和新記錄的狀態資料行變更為 1。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-366">As part of the Select statement, the Update statement is also executed and the Status column for the new record is changed to 1.</span></span> <span data-ttu-id="b3b3d-367">這會再次觸發從 SQL Server 的另一個通知和配接器收到對應通知訊息時，類似如下：</span><span class="sxs-lookup"><span data-stu-id="b3b3d-367">This again triggers another notification from SQL Server and the adapter receives a corresponding notification message, that resembles the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Update</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="b3b3d-368">此訊息通知記錄已更新 Employee 資料表中。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-368">This message notifies that a record was updated in the Employee table.</span></span> <span data-ttu-id="b3b3d-369">請注意，值`<Info>`項目是 「 更新 」。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-369">Note that the value for the `<Info>` element is “Update”.</span></span>  
  
-   <span data-ttu-id="b3b3d-370">之後，第二個通知配接器會執行 Select 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-370">After the second notification, the adapter executes the Select statement.</span></span> <span data-ttu-id="b3b3d-371">不過，現在，有狀態為 0，沒有記錄，因為配接器取得空的回應，如下列所示。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-371">However, because there are no records now that have Status as 0, the adapter gets an empty response resembling the following.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <SelectResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <SelectResult />   
    </SelectResponse>  
    ```  
  
## <a name="best-practices"></a><span data-ttu-id="b3b3d-372">最佳作法</span><span class="sxs-lookup"><span data-stu-id="b3b3d-372">Best Practices</span></span>  
 <span data-ttu-id="b3b3d-373">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-373">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="b3b3d-374">一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立傳送埠和接收相同的協調流程連接埠。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-374">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create the send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="b3b3d-375">如需繫結檔案的詳細資訊，請參閱[重複使用的 SQL 配接器繫結](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b3d-375">For more information about binding files, see [Reuse SQL adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b3b3d-376">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3b3d-376">See Also</span></span>  
 [<span data-ttu-id="b3b3d-377">接收使用 BizTalk Server 的 SQL 查詢通知</span><span class="sxs-lookup"><span data-stu-id="b3b3d-377">Receive SQL Query Notifications using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)