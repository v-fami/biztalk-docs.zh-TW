---
title: "接收以累加方式使用 BizTalk Server 的 Oracle 資料庫變更通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17cef39f-a1aa-4f46-993f-620008f3890d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eebcd37124e0ddde2171f21b233ca8bd8ce23f55
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="receive-oracle-database-change-notifications-incrementally-using-biztalk-server"></a><span data-ttu-id="f4692-102">接收以累加方式使用 BizTalk Server 的 Oracle 資料庫變更通知</span><span class="sxs-lookup"><span data-stu-id="f4692-102">Receive Oracle Database change notifications incrementally using BizTalk Server</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="f4692-103">為了簡短起見，本主題只說明如何以累加方式收到通知。</span><span class="sxs-lookup"><span data-stu-id="f4692-103">For the sake of brevity, this topic only describes how to receive notifications incrementally.</span></span> <span data-ttu-id="f4692-104">在商務案例中，協調流程必須在理想情況下包含擷取的收到的通知訊息類型，然後再執行任何後續作業的邏輯。</span><span class="sxs-lookup"><span data-stu-id="f4692-104">In business scenarios, the orchestration must ideally include the logic to extract the kind of notification message received and then perform any subsequent operations.</span></span> <span data-ttu-id="f4692-105">換句話說，本主題中所述的協調流程必須建立在協調流程中所述之上[程序通知訊息，以便完成特定工作在 Oracle 資料庫中使用 BizTalk Sever](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-105">In other words, the orchestration described in this topic must be built on top of the orchestration described in [Process Notification Messages to complete Specific Tasks in Oracle Database using BizTalk Sever](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md).</span></span>  
  
 <span data-ttu-id="f4692-106">本主題示範如何設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來從 Oracle 接收累加的查詢通知訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-106">This topic demonstrates how to configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive incremental query notification messages from Oracle.</span></span> <span data-ttu-id="f4692-107">若要示範累加通知，我們假設有資料表，ACCOUNTACTIVITY，與 「 處理 」 資料行。</span><span class="sxs-lookup"><span data-stu-id="f4692-107">To demonstrate incremental notifications, we consider a table, ACCOUNTACTIVITY, with a “Processed” column.</span></span> <span data-ttu-id="f4692-108">當新的記錄插入此資料表時，「 處理 」 資料行的值設定為 ' n '。</span><span class="sxs-lookup"><span data-stu-id="f4692-108">When a new record is inserted to this table, the value of the “Processed” column is set to ‘n’.</span></span> <span data-ttu-id="f4692-109">您可以設定配接器接收累加的通知，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f4692-109">You can configure the adapter to receive incremental notifications by doing the following:</span></span>  
  
-   <span data-ttu-id="f4692-110">註冊通知使用 SELECT 陳述式可擷取所有記錄的 「 處理 」 資料行做為 ' n '。</span><span class="sxs-lookup"><span data-stu-id="f4692-110">Register for notifications using a SELECT statement that retrieves all records that have “Processed” column as ‘n’.</span></span> <span data-ttu-id="f4692-111">您可以藉由指定 SELECT 陳述式**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-111">You can do so by specifying the SELECT statement for the **NotificationStatement** binding property.</span></span>  
  
-   <span data-ttu-id="f4692-112">如已收到通知的資料列，更新為 'y' 的 「 處理 」 資料行。</span><span class="sxs-lookup"><span data-stu-id="f4692-112">For rows which have been notified for, update the “Processed” column to ‘y’.</span></span>  
  
 <span data-ttu-id="f4692-113">本主題示範如何建立 BizTalk 協調流程和設定 BizTalk 應用程式，以達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="f4692-113">This topic demonstrates how to create a BizTalk orchestration and configure a BizTalk application to achieve this.</span></span>  
  
## <a name="configuring-notifications-with-the-oracle-database-adapter-binding-properties"></a><span data-ttu-id="f4692-114">Oracle 資料庫配接器繫結屬性與設定通知</span><span class="sxs-lookup"><span data-stu-id="f4692-114">Configuring Notifications with the Oracle Database Adapter Binding Properties</span></span>  
 <span data-ttu-id="f4692-115">下表摘要說明[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結，您用來設定從 Oracle 資料庫接收通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-115">The following table summarizes the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties that you use to configure receiving notifications from the Oracle database.</span></span> <span data-ttu-id="f4692-116">您必須同時設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f4692-116">You must specify these binding properties while configuring the receive port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4692-117">您可以選擇指定這些繫結內容產生的結構描述時**通知**作業，即使它不是強制性。</span><span class="sxs-lookup"><span data-stu-id="f4692-117">You may choose to specify these binding properties when generating the schema for the **Notification** operation, even though it is not mandatory.</span></span> <span data-ttu-id="f4692-118">如果您這樣做，連接埠繫結檔，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f4692-118">If you do so, the port binding file that the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] generates as part of the metadata generation also contains the values you specify for the binding properties.</span></span> <span data-ttu-id="f4692-119">您可以稍後匯入此繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂或 Wcf-oracledb 接收埠以繫結已設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-119">You can later import this binding file in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create the WCF-custom or WCF-OracleDB receive port with the binding properties already set.</span></span> <span data-ttu-id="f4692-120">如需有關如何建立接收埠使用的繫結檔案的詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-120">For more information about creating a receive port using the binding file, see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).</span></span>  
  
|<span data-ttu-id="f4692-121">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="f4692-121">Binding Property</span></span>|<span data-ttu-id="f4692-122">Description</span><span class="sxs-lookup"><span data-stu-id="f4692-122">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="f4692-123">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="f4692-123">**InboundOperationType**</span></span>|<span data-ttu-id="f4692-124">指定輸入您想要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="f4692-124">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="f4692-125">若要接收通知訊息，將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="f4692-125">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="f4692-126">**NotificationPort**</span><span class="sxs-lookup"><span data-stu-id="f4692-126">**NotificationPort**</span></span>|<span data-ttu-id="f4692-127">指定 ODP.NET 必須開啟從 Oracle 資料庫的資料庫變更通知所接聽的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="f4692-127">Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.</span></span>|  
|<span data-ttu-id="f4692-128">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="f4692-128">**NotificationStatement**</span></span>|<span data-ttu-id="f4692-129">指定用來註冊查詢通知的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f4692-129">Specifies the SELECT statement used to register for query notifications.</span></span> <span data-ttu-id="f4692-130">僅在結果集，指定 SELECT 陳述式變更時，配接器會取得通知訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-130">The adapter gets a notification message only when the result set for the specified SELECT statement changes.</span></span>|  
|<span data-ttu-id="f4692-131">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="f4692-131">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="f4692-132">指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。</span><span class="sxs-lookup"><span data-stu-id="f4692-132">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="f4692-133">如需這些屬性的更完整說明，請參閱[使用 BizTalk Adapter for Oracle 資料庫繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f4692-133">For a more complete description of these properties, see [Working with BizTalk Adapter for Oracle Database Binding Properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span> <span data-ttu-id="f4692-134">如需完整的說明，如何使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]進一步若要從 Oracle 資料庫接收通知，閱讀。</span><span class="sxs-lookup"><span data-stu-id="f4692-134">For a complete description of how to use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive notifications from the Oracle database, read further.</span></span>  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a><span data-ttu-id="f4692-135">本主題示範接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="f4692-135">How This Topic Demonstrates Receiving Notification Messages</span></span>  
 <span data-ttu-id="f4692-136">本主題中，以示範如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援從 Oracle 資料庫接收增量資料庫變更的通知訊息，我們將會設定配接器接收 ACCOUNTACTIVTY 資料表所做變更的通知。</span><span class="sxs-lookup"><span data-stu-id="f4692-136">In this topic, to demonstrate how the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports receiving incremental database change notification messages from the Oracle database, we will configure the adapter to receive notifications for changes to the ACCOUNTACTIVTY table.</span></span> <span data-ttu-id="f4692-137">讓我們假設 ACCOUNTACTIVITY 資料表的資料行"TID 」、 「 帳戶 」 和 「 處理 」。</span><span class="sxs-lookup"><span data-stu-id="f4692-137">Let us assume that the ACCOUNTACTIVITY table has columns “TID”, “Account”, and “Processed”.</span></span> <span data-ttu-id="f4692-138">每當加入新的記錄，「 處理 」 資料行的值設定為 ' n '。</span><span class="sxs-lookup"><span data-stu-id="f4692-138">Whenever a new record is added, the value of the “Processed” column is set to ‘n’.</span></span> <span data-ttu-id="f4692-139">因此，若要取得累加通知您必須做為 BizTalk 協調流程的一部分，執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f4692-139">So, to get incremental notifications you will have to do the following tasks as part of the BizTalk orchestration:</span></span>  
  
-   <span data-ttu-id="f4692-140">收到通知，其中是 「 處理 」 的所有記錄的 ' n '。</span><span class="sxs-lookup"><span data-stu-id="f4692-140">Get notification for all records where “Processed” is ‘n’.</span></span> <span data-ttu-id="f4692-141">您可以指定為通知陳述式的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f4692-141">You can do this by specifying a SELECT statement as a notification statement.</span></span>  
  
-   <span data-ttu-id="f4692-142">特定記錄收到通知之後，設定 「 處理 」 為 'y'。</span><span class="sxs-lookup"><span data-stu-id="f4692-142">After the notification is received for a certain record, set “Processed” to ‘y’.</span></span> <span data-ttu-id="f4692-143">您可以執行預存程序，PROCESS_RECORDS，更新 「 處理 」 的資料行。</span><span class="sxs-lookup"><span data-stu-id="f4692-143">You can do this by executing a stored procedure, PROCESS_RECORDS, which updates the “Processed” column.</span></span>  
  
 <span data-ttu-id="f4692-144">若要示範接收累加的通知，我們執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f4692-144">To demonstrate receiving incremental notifications, we do the following:</span></span>  
  
-   <span data-ttu-id="f4692-145">產生結構描述的**通知**（輸入作業） 和**PROCESS_RECORDS** （輸出作業） ACCOUNTACTIVITY 資料表上。</span><span class="sxs-lookup"><span data-stu-id="f4692-145">Generate schema for the **Notification** (inbound operation), and **PROCESS_RECORDS** (outbound operation) on the ACCOUNTACTIVITY table.</span></span>  
  
-   <span data-ttu-id="f4692-146">建立具有下列的協調流程：</span><span class="sxs-lookup"><span data-stu-id="f4692-146">Create an orchestration that has the following:</span></span>  
  
    -   <span data-ttu-id="f4692-147">要接收通知訊息的接收位置。</span><span class="sxs-lookup"><span data-stu-id="f4692-147">A receive location to receive notification messages.</span></span> <span data-ttu-id="f4692-148">您可以藉由指定 SELECT 陳述式設定通知：</span><span class="sxs-lookup"><span data-stu-id="f4692-148">You can configure for notification by specifying the SELECT statement as:</span></span>  
  
        ```  
        SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="f4692-149">您必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="f4692-149">You must specify the table name along with the schema name.</span></span> <span data-ttu-id="f4692-150">例如， `SCOTT.ACCOUNTACTIVITY`。</span><span class="sxs-lookup"><span data-stu-id="f4692-150">For example, `SCOTT.ACCOUNTACTIVITY`.</span></span>  
  
    -   <span data-ttu-id="f4692-151">要更新的通知已傳送的資料列的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f4692-151">A send port to update the rows for which notification has already been sent.</span></span> <span data-ttu-id="f4692-152">您將執行 PROCESS_RECORDS 預存程序，在此連接埠設為 'y' 收到通知的記錄的 「 處理 」 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="f4692-152">You will execute the PROCESS_RECORDS stored procedure on this port to set the value of “Processed” column to ‘y’ for the records for which notification is received.</span></span>  
  
         <span data-ttu-id="f4692-153">請注意這項作業必須在接收通知訊息，以便處理的資料列更新之後執行。</span><span class="sxs-lookup"><span data-stu-id="f4692-153">Note that this operation must be executed after receiving the notification messages so that the processed rows are updated.</span></span> <span data-ttu-id="f4692-154">若要執行離開等候取得通知回應，然後再手動卸除執行 PROCESS_RECORDS 程序的要求訊息的負擔，您將會產生 PROCESS_RECORDS 程序協調流程本身內的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-154">To do away with the overhead of waiting to get the notification response and then manually dropping a request message to execute the PROCESS_RECORDS procedure, you will generate the request message for PROCESS_RECORDS procedure within the orchestration itself.</span></span> <span data-ttu-id="f4692-155">您可以使用**建構訊息**協調流程內的圖形。</span><span class="sxs-lookup"><span data-stu-id="f4692-155">You can do so by using the **Construct Message** shape within an orchestration.</span></span>  
  
## <a name="how-to-receive-notification-messages-from-the-oracle-database"></a><span data-ttu-id="f4692-156">如何從 Oracle 資料庫接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="f4692-156">How to Receive Notification Messages from the Oracle database</span></span>  
 <span data-ttu-id="f4692-157">針對 Oracle 資料庫使用執行運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及程序中所述的工作[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-157">Performing an operation on the Oracle database using [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves the procedural tasks described in [Building blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md).</span></span> <span data-ttu-id="f4692-158">若要設定要接收通知訊息的介面卡，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="f4692-158">To configure the adapter to receive notification messages, these tasks are:</span></span>  
  
1.  <span data-ttu-id="f4692-159">建立 BizTalk 專案，然後再產生結構描述的**通知**（輸入作業） 和**PROCESS_RECORDS** ACCOUNTACTIVITY 資料表上的程序 （輸出作業）。</span><span class="sxs-lookup"><span data-stu-id="f4692-159">Create a BizTalk project, and then generate schema for the **Notification** (inbound operation) and **PROCESS_RECORDS** procedure (outbound operation) on the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="f4692-160">您可以選擇性地指定值**InboundOperationType**， **NotificationPort**，和**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-160">Optionally, you can specify values for the **InboundOperationType**, **NotificationPort**, and **NotificationStatement** binding properties.</span></span>  
  
2.  <span data-ttu-id="f4692-161">從 Oracle 資料庫接收通知的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-161">Create a message in the BizTalk project for receiving notification from the Oracle database.</span></span>  
  
3.  <span data-ttu-id="f4692-162">建立訊息執行 PROCESS_RECORDS 預存程序，並接收回應訊息的 BizTalk 專案中。</span><span class="sxs-lookup"><span data-stu-id="f4692-162">Create messages in the BizTalk project for executing the PROCESS_RECORDS stored procedure and receiving response messages.</span></span>  
  
4.  <span data-ttu-id="f4692-163">建立的協調流程，會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f4692-163">Create an orchestration that does the following:</span></span>  
  
    -   <span data-ttu-id="f4692-164">從 Oracle 資料庫接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-164">Receives notification message from the Oracle database.</span></span>  
  
    -   <span data-ttu-id="f4692-165">建立訊息執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-165">Creates a message to execute the PROCESS_RECORDS procedure.</span></span>  
  
    -   <span data-ttu-id="f4692-166">將此訊息傳送到 Oracle 資料庫，以選取和更新記錄並接收回應。</span><span class="sxs-lookup"><span data-stu-id="f4692-166">Sends this message to the Oracle database to select and update the records and receive a response.</span></span>  
  
5.  <span data-ttu-id="f4692-167">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f4692-167">Build and deploy the BizTalk project.</span></span>  
  
6.  <span data-ttu-id="f4692-168">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="f4692-168">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4692-169">輸入的作業，像是接收通知訊息，您必須只設定單向的 WCF 自訂或 Wcf-oracledb 接收埠。</span><span class="sxs-lookup"><span data-stu-id="f4692-169">For inbound operations, like receiving notification messages, you must only configure a one-way WCF-Custom or WCF-OracleDB receive port.</span></span> <span data-ttu-id="f4692-170">雙向接收埠不支援的輸入操作。</span><span class="sxs-lookup"><span data-stu-id="f4692-170">Two-way receive ports are not supported for inbound operations.</span></span>  
  
7.  <span data-ttu-id="f4692-171">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4692-171">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="f4692-172">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="f4692-172">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="f4692-173">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="f4692-173">Generating Schema</span></span>  
 <span data-ttu-id="f4692-174">您必須產生的結構描述**通知**作業和**PROCESS_RECORDS**程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-174">You must generate the schema for the **Notification** operation and **PROCESS_RECORDS** procedure.</span></span> <span data-ttu-id="f4692-175">請參閱[擷取 Oracle 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="f4692-175">See [Retrieve metadata for Oracle operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) for more information about how to generate the schema.</span></span> <span data-ttu-id="f4692-176">產生結構描述時，請執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="f4692-176">Perform the following tasks when generating the schema.</span></span> <span data-ttu-id="f4692-177">如果您不要指定繫結屬性在設計階段，請略過第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="f4692-177">Skip the first step if you do not want to specify the binding properties at design-time.</span></span>  
  
1.  <span data-ttu-id="f4692-178">指定的值**InboundOperationType**， **NotificationPort**，和**NotificationStatement**時產生結構描述繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-178">Specify a value for **InboundOperationType**, **NotificationPort**, and **NotificationStatement** binding properties while generating the schema.</span></span> <span data-ttu-id="f4692-179">如需此繫結屬性的詳細資訊，請參閱[使用 BizTalk Adapter for Oracle 資料庫繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f4692-179">For more information about this binding property, see [Working with BizTalk Adapter for Oracle Database Binding Properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span> <span data-ttu-id="f4692-180">如需有關如何指定繫結屬性的指示，請參閱[指定繫結屬性](https://msdn.microsoft.com/library/dd788420.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f4692-180">For instructions on how to specify binding properties, see [Specifying Binding Properties](https://msdn.microsoft.com/library/dd788420.aspx).</span></span>  
  
2.  <span data-ttu-id="f4692-181">選取合約類型為**服務 （輸入操作）**。</span><span class="sxs-lookup"><span data-stu-id="f4692-181">Select the contract type as **Service (Inbound operations)**.</span></span>  
  
3.  <span data-ttu-id="f4692-182">產生結構描述的**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="f4692-182">Generate schema for the **Notification** operation.</span></span>  
  
4.  <span data-ttu-id="f4692-183">選取合約類型為**用戶端 （輸出作業）**。</span><span class="sxs-lookup"><span data-stu-id="f4692-183">Select the contract type as **Client (Outbound operations)**.</span></span>  
  
5.  <span data-ttu-id="f4692-184">產生結構描述的**PROCESS_RECORDS**程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-184">Generate schema for the **PROCESS_RECORDS** procedure.</span></span> <span data-ttu-id="f4692-185">此程序時才可使用**ACCOUNT_PKG**封裝。</span><span class="sxs-lookup"><span data-stu-id="f4692-185">This procedure is available under the **ACCOUNT_PKG** package.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="f4692-186">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="f4692-186">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="f4692-187">您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-187">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="f4692-188">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="f4692-188">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="f4692-189">一旦產生結構描述時，您必須訊息連結之協調流程檢視中的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f4692-189">Once the schema is generated, you must link it to the messages from the Orchestration view of the BizTalk project.</span></span>  
  
 <span data-ttu-id="f4692-190">本主題中，您必須建立三個訊息，一個用於接收從 Oracle 資料庫，一個是執行 PROCESS_RECORDS 程序中，一個用於接收程序回應的通知。</span><span class="sxs-lookup"><span data-stu-id="f4692-190">For this topic, you must create three messages—one to receive notifications from the Oracle database, one to execute the PROCESS_RECORDS procedure, and one to receive the response for the procedure.</span></span>  
  
 <span data-ttu-id="f4692-191">執行下列步驟來建立訊息，並將它們連結至結構描述。</span><span class="sxs-lookup"><span data-stu-id="f4692-191">Perform the following steps to create messages and link them to schema.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="f4692-192">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="f4692-192">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="f4692-193">BizTalk 專案中新增協調流程。</span><span class="sxs-lookup"><span data-stu-id="f4692-193">Add an orchestration to the BizTalk project.</span></span> <span data-ttu-id="f4692-194">從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="f4692-194">From the Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="f4692-195">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="f4692-195">Type a name for the BizTalk orchestration and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="f4692-196">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f4692-196">Open the orchestration view window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="f4692-197">按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="f4692-197">Click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="f4692-198">在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="f4692-198">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="f4692-199">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="f4692-199">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="f4692-200">在**屬性**窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f4692-200">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="f4692-201">使用</span><span class="sxs-lookup"><span data-stu-id="f4692-201">Use this</span></span>|<span data-ttu-id="f4692-202">動作</span><span class="sxs-lookup"><span data-stu-id="f4692-202">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f4692-203">識別碼</span><span class="sxs-lookup"><span data-stu-id="f4692-203">Identifier</span></span>|<span data-ttu-id="f4692-204">輸入 `NotifyReceive`。</span><span class="sxs-lookup"><span data-stu-id="f4692-204">Type `NotifyReceive`.</span></span>|  
    |<span data-ttu-id="f4692-205">訊息類型</span><span class="sxs-lookup"><span data-stu-id="f4692-205">Message Type</span></span>|<span data-ttu-id="f4692-206">從下拉式清單中，展開 **結構描述**，然後選取*OracleNotifyIncremental.OracleDBBinding.Notification*，其中*OracleNotifyIncremental*的名稱您的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f4692-206">From the drop-down list, expand **Schemas**, and select *OracleNotifyIncremental.OracleDBBinding.Notification*, where *OracleNotifyIncremental* is the name of your BizTalk project.</span></span> <span data-ttu-id="f4692-207">*OracleDBBinding*是針對產生的結構描述**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="f4692-207">*OracleDBBinding* is the schema generated for the **Notification** operation.</span></span>|  
  
6.  <span data-ttu-id="f4692-208">重複步驟 3 以建立兩個新的訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-208">Repeat step 3 to create two new messages.</span></span> <span data-ttu-id="f4692-209">在**屬性**窗格新訊息中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f4692-209">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="f4692-210">若要設定識別項</span><span class="sxs-lookup"><span data-stu-id="f4692-210">Set Identifier to</span></span>|<span data-ttu-id="f4692-211">若要設定訊息類型</span><span class="sxs-lookup"><span data-stu-id="f4692-211">Set Message Type to</span></span>|  
    |-----------------------|-------------------------|  
    |<span data-ttu-id="f4692-212">程序</span><span class="sxs-lookup"><span data-stu-id="f4692-212">Procedure</span></span>|<span data-ttu-id="f4692-213">*OracleNotifyIncremental.OracleDBBinding1.PROCESS_RECORDS*，其中*OracleDBBinding1*是針對產生的結構描述**PROCESS_RECORDS**程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-213">*OracleNotifyIncremental.OracleDBBinding1.PROCESS_RECORDS*, where  *OracleDBBinding1* is the schema generated for the **PROCESS_RECORDS** procedure.</span></span>|  
    |<span data-ttu-id="f4692-214">ProcedureResponse</span><span class="sxs-lookup"><span data-stu-id="f4692-214">ProcedureResponse</span></span>|<span data-ttu-id="f4692-215">*OracleNotifyIncremental.OracleDBBinding1.PROCESS_RECORDSResponse*</span><span class="sxs-lookup"><span data-stu-id="f4692-215">*OracleNotifyIncremental.OracleDBBinding1.PROCESS_RECORDSResponse*</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="f4692-216">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="f4692-216">Setting up the Orchestration</span></span>  
 <span data-ttu-id="f4692-217">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 Oracle 資料庫接收通知訊息，然後更新收到通知的資料列。</span><span class="sxs-lookup"><span data-stu-id="f4692-217">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving notification messages from the Oracle database and then updating the rows for which notification was received.</span></span> <span data-ttu-id="f4692-218">在此協調流程中，配接器接收通知訊息，根據指定的 SELECT 陳述式**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-218">In this orchestration, the adapter receives the notification message based on the SELECT statement specified for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="f4692-219">檔案位置接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-219">The notification message is received at a FILE location.</span></span> <span data-ttu-id="f4692-220">一旦收到回應時，協調流程會建構要叫用的 PROCESS_RECORDS 程序，更新的資料列收到通知的訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-220">Once the response is received, the orchestration constructs a message to invoke the PROCESS_RECORDS procedure, which updates the rows for which notification is received.</span></span> <span data-ttu-id="f4692-221">在相同的檔案位置也收到這個訊息的回應。</span><span class="sxs-lookup"><span data-stu-id="f4692-221">The response for this message is also received at the same FILE location.</span></span>  
  
 <span data-ttu-id="f4692-222">因此，您的協調流程必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="f4692-222">So, your orchestration must contain the following:</span></span>  
  
-   <span data-ttu-id="f4692-223">單向的 「 WCF 自訂 」 或 「 Wcf-oracledb 接收埠來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-223">A one-way WCF-Custom or WCF-OracleDB receive port to receive notification messages.</span></span>  
  
-   <span data-ttu-id="f4692-224">雙向的 「 WCF 自訂 」 或 「 Wcf-oracledb 傳送埠將訊息傳送至執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-224">A two-way WCF-Custom or WCF-OracleDB send port to send messages to execute the PROCESS_RECORDS procedure.</span></span>  
  
-   <span data-ttu-id="f4692-225">A**建構訊息**圖形來建構執行 PROCESS_RECORDS 程序，在協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-225">A **Construct Message** shape to construct messages, to execute PROCESS_RECORDS procedure, within the orchestration.</span></span>  
  
-   <span data-ttu-id="f4692-226">FILE 傳送埠以儲存通知訊息和 PROCESS_RECORDS 程序的回應。</span><span class="sxs-lookup"><span data-stu-id="f4692-226">A FILE send port to save the notification message and the response for the PROCESS_RECORDS procedure.</span></span>  
  
-   <span data-ttu-id="f4692-227">接收和傳送圖形。</span><span class="sxs-lookup"><span data-stu-id="f4692-227">Receive and send shapes.</span></span>  
  
 <span data-ttu-id="f4692-228">範例協調流程如下。</span><span class="sxs-lookup"><span data-stu-id="f4692-228">A sample orchestration resembles the following.</span></span>  
  
 <span data-ttu-id="f4692-229">![要從 Oracle 接收通知的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/cef49414-490a-4bd5-a32d-b3f4cde5950a.gif "cef49414-490a-4bd5-a32d-b3f4cde5950a")</span><span class="sxs-lookup"><span data-stu-id="f4692-229">![Orchestration to receive notifications from Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/cef49414-490a-4bd5-a32d-b3f4cde5950a.gif "cef49414-490a-4bd5-a32d-b3f4cde5950a")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="f4692-230">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="f4692-230">Adding Message Shapes</span></span>  
 <span data-ttu-id="f4692-231">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-231">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="f4692-232">圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="f4692-232">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="f4692-233">形狀圖</span><span class="sxs-lookup"><span data-stu-id="f4692-233">Shape</span></span>|<span data-ttu-id="f4692-234">圖形類型</span><span class="sxs-lookup"><span data-stu-id="f4692-234">Shape Type</span></span>|<span data-ttu-id="f4692-235">屬性</span><span class="sxs-lookup"><span data-stu-id="f4692-235">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="f4692-236">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="f4692-236">ReceiveNotification</span></span>|<span data-ttu-id="f4692-237">Receive</span><span class="sxs-lookup"><span data-stu-id="f4692-237">Receive</span></span>|<span data-ttu-id="f4692-238">-設定**名稱**至*ReceiveNotification*</span><span class="sxs-lookup"><span data-stu-id="f4692-238">- Set **Name** to *ReceiveNotification*</span></span><br /><br /> <span data-ttu-id="f4692-239">-設定**啟動**至*，則為 True*</span><span class="sxs-lookup"><span data-stu-id="f4692-239">- Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="f4692-240">SaveNotification</span><span class="sxs-lookup"><span data-stu-id="f4692-240">SaveNotification</span></span>|<span data-ttu-id="f4692-241">Send</span><span class="sxs-lookup"><span data-stu-id="f4692-241">Send</span></span>|<span data-ttu-id="f4692-242">-設定**名稱**至*SaveNotification*</span><span class="sxs-lookup"><span data-stu-id="f4692-242">- Set **Name** to *SaveNotification*</span></span>|  
|<span data-ttu-id="f4692-243">SendProcMessage</span><span class="sxs-lookup"><span data-stu-id="f4692-243">SendProcMessage</span></span>|<span data-ttu-id="f4692-244">Send</span><span class="sxs-lookup"><span data-stu-id="f4692-244">Send</span></span>|<span data-ttu-id="f4692-245">-設定**名稱**至*SendProcMessage*</span><span class="sxs-lookup"><span data-stu-id="f4692-245">- Set **Name** to *SendProcMessage*</span></span>|  
|<span data-ttu-id="f4692-246">ReceiveProcResponse</span><span class="sxs-lookup"><span data-stu-id="f4692-246">ReceiveProcResponse</span></span>|<span data-ttu-id="f4692-247">Receive</span><span class="sxs-lookup"><span data-stu-id="f4692-247">Receive</span></span>|<span data-ttu-id="f4692-248">-設定**名稱**至*ReceiveProcResponse*</span><span class="sxs-lookup"><span data-stu-id="f4692-248">- Set **Name** to *ReceiveProcResponse*</span></span>|  
|<span data-ttu-id="f4692-249">SaveProcResponse</span><span class="sxs-lookup"><span data-stu-id="f4692-249">SaveProcResponse</span></span>|<span data-ttu-id="f4692-250">Send</span><span class="sxs-lookup"><span data-stu-id="f4692-250">Send</span></span>|<span data-ttu-id="f4692-251">-設定**名稱**至*SaveProcResponse*</span><span class="sxs-lookup"><span data-stu-id="f4692-251">- Set **Name** to *SaveProcResponse*</span></span>|  
  
### <a name="adding-construct-message-shape"></a><span data-ttu-id="f4692-252">新增 建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="f4692-252">Adding Construct Message Shape</span></span>  
 <span data-ttu-id="f4692-253">您可以使用**建構訊息**產生要求訊息的協調流程內執行 PROCESS_RECORDS 程序的圖形。</span><span class="sxs-lookup"><span data-stu-id="f4692-253">You can use the **Construct Message** shape to generate a request message within the orchestration to execute the PROCESS_RECORDS procedure.</span></span> <span data-ttu-id="f4692-254">若要這樣做，您必須新增**建構訊息**圖形，並在其中**訊息指派**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="f4692-254">To do so, you must add a **Construct Message** shape and within that a **Message Assignment** shape to your orchestration.</span></span> <span data-ttu-id="f4692-255">例如，**訊息指派**圖形叫用會產生一個訊息傳送至 Oracle 資料庫執行此程序的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4692-255">For this example, the **Message Assignment** shape invokes code that generates a message that is sent to the Oracle database to execute the procedure.</span></span> <span data-ttu-id="f4692-256">**訊息指派**圖形也會設定傳送到 Oracle 資料庫之訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="f4692-256">The **Message Assignment** shape also sets the action for the message to be sent to the Oracle database.</span></span>  
  
 <span data-ttu-id="f4692-257">對於 「 建構訊息 」 圖形，設定**建構訊息**屬性**程序**。</span><span class="sxs-lookup"><span data-stu-id="f4692-257">For the construct message shape, set the **Message Constructed** property to **Procedure**.</span></span>  
  
 <span data-ttu-id="f4692-258">產生回應的程式碼可能是您的 BizTalk 專案相同的 Visual Studio 方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="f4692-258">The code to generate the response could be part of the same Visual Studio solution as your BizTalk project.</span></span> <span data-ttu-id="f4692-259">產生回應訊息的範例程式碼看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="f4692-259">A sample code for generating a response message looks like this.</span></span>  
  
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
            XmlFileLocation = "C:\\TestLocation\\MessageIn";  
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
  
 <span data-ttu-id="f4692-260">如上述的程式碼摘錄無法產生要求訊息中必須有 XML 要求訊息 （適用於 PROCESS_RECORDS 程序中） 所指定的位置`XmlFileLocation`變數。</span><span class="sxs-lookup"><span data-stu-id="f4692-260">For the above code excerpt to be able to generate a request message, you must have an XML request message (for the PROCESS_RECORDS procedure) in the location specified for the `XmlFileLocation` variable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4692-261">建置專案之後，會建立 MessageCreator.dll 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="f4692-261">After you build the project, MessageCreator.dll will be created in the project directory.</span></span> <span data-ttu-id="f4692-262">您必須將此 DLL 加入全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="f4692-262">You must add this DLL to the global assembly cache (GAC).</span></span> <span data-ttu-id="f4692-263">此外，您必須加入 MessageCreator.dll 當做 BizTalk 專案中的參考。</span><span class="sxs-lookup"><span data-stu-id="f4692-263">Also, you must add the MessageCreator.dll as a reference in the BizTalk project.</span></span>  
  
 <span data-ttu-id="f4692-264">加入下列運算式來叫用此程式碼從**訊息指派**圖形，並設定訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="f4692-264">Add the following expression to invoke this code from the **Message Assignment** shape and to set the action for message.</span></span> <span data-ttu-id="f4692-265">若要新增運算式，請按兩下**訊息指派**圖形以開啟 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="f4692-265">To add an expression, double-click the **Message Assignment** shape to open the Expression Editor.</span></span>  
  
```  
Procedure = SampleMessageCreator.SampleMessageCreator.XMLMessageCreator();  
Procedure(WCF.Action) = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/PROCESS_RECORDS";  
```  
  
### <a name="adding-ports"></a><span data-ttu-id="f4692-266">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="f4692-266">Adding Ports</span></span>  
 <span data-ttu-id="f4692-267">請確定您針對每個邏輯連接埠指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-267">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="f4692-268">連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。</span><span class="sxs-lookup"><span data-stu-id="f4692-268">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="f4692-269">通訊埠</span><span class="sxs-lookup"><span data-stu-id="f4692-269">Port</span></span>|<span data-ttu-id="f4692-270">屬性</span><span class="sxs-lookup"><span data-stu-id="f4692-270">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="f4692-271">OracleNotifyPort</span><span class="sxs-lookup"><span data-stu-id="f4692-271">OracleNotifyPort</span></span>|<span data-ttu-id="f4692-272">-設定**識別碼**至*OracleNotifyPort*</span><span class="sxs-lookup"><span data-stu-id="f4692-272">- Set **Identifier** to *OracleNotifyPort*</span></span><br /><br /> <span data-ttu-id="f4692-273">-設定**類型**至*OracleNotifyPortType*</span><span class="sxs-lookup"><span data-stu-id="f4692-273">- Set **Type** to *OracleNotifyPortType*</span></span><br /><br /> <span data-ttu-id="f4692-274">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="f4692-274">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="f4692-275">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="f4692-275">- Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="f4692-276">SaveMessagePort</span><span class="sxs-lookup"><span data-stu-id="f4692-276">SaveMessagePort</span></span>|<span data-ttu-id="f4692-277">-設定**識別碼**至*SaveMessagePort*</span><span class="sxs-lookup"><span data-stu-id="f4692-277">- Set **Identifier** to *SaveMessagePort*</span></span><br /><br /> <span data-ttu-id="f4692-278">-設定**類型**至*SaveMessagePortType*</span><span class="sxs-lookup"><span data-stu-id="f4692-278">- Set **Type** to *SaveMessagePortType*</span></span><br /><br /> <span data-ttu-id="f4692-279">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="f4692-279">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="f4692-280">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="f4692-280">- Set **Communication Direction** to *Send*</span></span><br /><br /> <span data-ttu-id="f4692-281">建立作業*通知*。</span><span class="sxs-lookup"><span data-stu-id="f4692-281">- Create an operation *Notify*.</span></span> <span data-ttu-id="f4692-282">通知訊息使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="f4692-282">This operation is used for notification messages.</span></span><br /><br /> <span data-ttu-id="f4692-283">建立作業*程序*。</span><span class="sxs-lookup"><span data-stu-id="f4692-283">- Create an operation *Procedure*.</span></span> <span data-ttu-id="f4692-284">選取回應訊息使用這項作業。</span><span class="sxs-lookup"><span data-stu-id="f4692-284">This operation is used for select response messages.</span></span>|  
|<span data-ttu-id="f4692-285">OracleOutboundPort</span><span class="sxs-lookup"><span data-stu-id="f4692-285">OracleOutboundPort</span></span>|<span data-ttu-id="f4692-286">-設定**識別碼**至*OracleOutboundPort*</span><span class="sxs-lookup"><span data-stu-id="f4692-286">- Set **Identifier** to *OracleOutboundPort*</span></span><br /><br /> <span data-ttu-id="f4692-287">-設定**類型**至*OracleOutboundPortType*</span><span class="sxs-lookup"><span data-stu-id="f4692-287">- Set **Type** to *OracleOutboundPortType*</span></span><br /><br /> <span data-ttu-id="f4692-288">-設定**通訊模式**至*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="f4692-288">- Set **Communication Pattern** to *Request-Response*</span></span><br /><br /> <span data-ttu-id="f4692-289">-設定**通訊方向**至*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="f4692-289">- Set **Communication Direction** to *Send-Receive*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a><span data-ttu-id="f4692-290">指定動作圖形訊息並連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="f4692-290">Specify Messages for Action Shapes and Connect to Ports</span></span>  
 <span data-ttu-id="f4692-291">下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-291">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="f4692-292">圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。</span><span class="sxs-lookup"><span data-stu-id="f4692-292">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="f4692-293">形狀圖</span><span class="sxs-lookup"><span data-stu-id="f4692-293">Shape</span></span>|<span data-ttu-id="f4692-294">屬性</span><span class="sxs-lookup"><span data-stu-id="f4692-294">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="f4692-295">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="f4692-295">ReceiveNotification</span></span>|<span data-ttu-id="f4692-296">-設定**訊息**至*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="f4692-296">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="f4692-297">-設定**作業**至*OracleNotifyPort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="f4692-297">- Set **Operation** to *OracleNotifyPort.Notify.Request*</span></span>|  
|<span data-ttu-id="f4692-298">SaveNotification</span><span class="sxs-lookup"><span data-stu-id="f4692-298">SaveNotification</span></span>|<span data-ttu-id="f4692-299">-設定**訊息**至*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="f4692-299">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="f4692-300">-設定**作業**至*SaveMessagePort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="f4692-300">- Set **Operation** to *SaveMessagePort.Notify.Request*</span></span>|  
|<span data-ttu-id="f4692-301">SendProcMessage</span><span class="sxs-lookup"><span data-stu-id="f4692-301">SendProcMessage</span></span>|<span data-ttu-id="f4692-302">-設定**訊息**至*程序*</span><span class="sxs-lookup"><span data-stu-id="f4692-302">- Set **Message** to *Procedure*</span></span><br /><br /> <span data-ttu-id="f4692-303">-設定**作業**至*OracleOutboundPort.Procedure.Request*</span><span class="sxs-lookup"><span data-stu-id="f4692-303">- Set **Operation** to *OracleOutboundPort.Procedure.Request*</span></span>|  
|<span data-ttu-id="f4692-304">ReceiveProcResponse</span><span class="sxs-lookup"><span data-stu-id="f4692-304">ReceiveProcResponse</span></span>|<span data-ttu-id="f4692-305">-設定**訊息**至*ProcedureResponse*</span><span class="sxs-lookup"><span data-stu-id="f4692-305">- Set **Message** to *ProcedureResponse*</span></span><br /><br /> <span data-ttu-id="f4692-306">-設定**作業**至*OracleOutboundPort.Procedure.Response*</span><span class="sxs-lookup"><span data-stu-id="f4692-306">- Set **Operation** to *OracleOutboundPort.Procedure.Response*</span></span>|  
|<span data-ttu-id="f4692-307">SaveProcResponse</span><span class="sxs-lookup"><span data-stu-id="f4692-307">SaveProcResponse</span></span>|<span data-ttu-id="f4692-308">-設定**訊息**至*ProedureResponse*</span><span class="sxs-lookup"><span data-stu-id="f4692-308">- Set **Message** to *ProedureResponse*</span></span><br /><br /> <span data-ttu-id="f4692-309">-設定**作業**至*SaveMessagePort.Procedure.Request*</span><span class="sxs-lookup"><span data-stu-id="f4692-309">- Set **Operation** to *SaveMessagePort.Procedure.Request*</span></span>|  
  
 <span data-ttu-id="f4692-310">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="f4692-310">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="f4692-311">您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4692-311">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f4692-312">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-312">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>  
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="f4692-313">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="f4692-313">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="f4692-314">部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**窗格[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f4692-314">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="f4692-315">您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4692-315">You must use the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the application.</span></span> <span data-ttu-id="f4692-316">如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-316">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>
  
 <span data-ttu-id="f4692-317">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="f4692-317">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="f4692-318">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="f4692-318">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="f4692-319">對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f4692-319">Mapping the ports that you created in your orchestration to physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="f4692-320">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="f4692-320">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="f4692-321">定義實體的 WCF 自訂或 Wcf-oracledb 單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="f4692-321">Define a physical WCF-Custom or WCF-OracleDB one-way receive port.</span></span> <span data-ttu-id="f4692-322">此連接埠會接聽來自 Oracle 資料庫的通知。</span><span class="sxs-lookup"><span data-stu-id="f4692-322">This port listens for notifications coming from the Oracle database.</span></span> <span data-ttu-id="f4692-323">如需如何建立接收埠，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-323">For information about how to create receive ports, see [Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).</span></span> <span data-ttu-id="f4692-324">請確定指定接收埠的下列繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-324">Make sure you specify the following binding properties for the receive port.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="f4692-325">您不需要執行這個步驟，如果您指定在設計階段的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f4692-325">You do not need to perform this step if you specified the binding properties at design-time.</span></span> <span data-ttu-id="f4692-326">在此情況下，您可以建立接收埠，設定必要的繫結屬性，藉由匯入所建立之繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4692-326">In such a case, you can create a receive port, with the required binding properties set, by importing the binding file created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="f4692-327">如需詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-327">For more information see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).</span></span>  
  
        |<span data-ttu-id="f4692-328">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="f4692-328">Binding Property</span></span>|<span data-ttu-id="f4692-329">值</span><span class="sxs-lookup"><span data-stu-id="f4692-329">Value</span></span>|  
        |----------------------|-----------|  
        |<span data-ttu-id="f4692-330">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="f4692-330">**InboundOperationType**</span></span>|<span data-ttu-id="f4692-331">將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="f4692-331">Set this to **Notification**.</span></span>|  
        |<span data-ttu-id="f4692-332">**NotificationPort**</span><span class="sxs-lookup"><span data-stu-id="f4692-332">**NotificationPort**</span></span>|<span data-ttu-id="f4692-333">指定 ODP.NET 必須開啟從 Oracle 資料庫的資料庫變更通知所接聽的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="f4692-333">Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.</span></span> <span data-ttu-id="f4692-334">設定為相同的連接埠號碼，您必須已加入 Windows 防火牆例外清單。</span><span class="sxs-lookup"><span data-stu-id="f4692-334">Set this to the same port number that you must have added to the Windows Firewall exceptions list.</span></span> <span data-ttu-id="f4692-335">如需如何將連接埠新增至 Windows 防火牆例外清單的指示，請參閱[http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959)。</span><span class="sxs-lookup"><span data-stu-id="f4692-335">For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).</span></span><br /><br /> <span data-ttu-id="f4692-336">**重要事項：**如果您設定為預設值-1，您必須完全停用 Windows 防火牆來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-336">**Important:** If you set this to the default value of -1, you will have to completely disable Windows Firewall to receive notification messages.</span></span>|  
        |<span data-ttu-id="f4692-337">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="f4692-337">**NotificationStatement**</span></span>|<span data-ttu-id="f4692-338">將此值設定為：</span><span class="sxs-lookup"><span data-stu-id="f4692-338">Set this to:</span></span><br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’`<br /><br /> <span data-ttu-id="f4692-339">**注意：**您必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="f4692-339">**Note:** You must specify the table name along with the schema name.</span></span> <span data-ttu-id="f4692-340">例如， `SCOTT.ACCOUNTACTIVITY`。</span><span class="sxs-lookup"><span data-stu-id="f4692-340">For example, `SCOTT.ACCOUNTACTIVITY`.</span></span>|  
        |<span data-ttu-id="f4692-341">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="f4692-341">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="f4692-342">將此設**True**。</span><span class="sxs-lookup"><span data-stu-id="f4692-342">Set this to **True**.</span></span>|  
  
         <span data-ttu-id="f4692-343">如需不同的繫結屬性的詳細資訊，請參閱[使用 BizTalk Adapter for Oracle 資料庫繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f4692-343">For more information about the different binding properties, see [Working with BizTalk Adapter for Oracle Database Binding Properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f4692-344">我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4692-344">We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="f4692-345">您可以藉由新增服務行為設定 Wcf-custom 或 Wcf-oracledb 時收到這些連接埠。</span><span class="sxs-lookup"><span data-stu-id="f4692-345">You can do so by adding the service behavior while configuring the WCF-Custom or WCF-OracleDB receive port.</span></span> <span data-ttu-id="f4692-346">如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-346">For instruction on how to add the service behavior, see [Configure Transaction Isolation Level and Transaction Timeout](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md).</span></span>  
  
    -   <span data-ttu-id="f4692-347">定義實體 Wcf-custom 或 Wcf-oracledb 傳送埠將訊息傳送至 Oracle 資料庫來執行 PROCESS_REOCRDS 程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-347">Define a physical WCF-Custom or WCF-OracleDB send port to send messages to the Oracle database to execute the PROCESS_REOCRDS procedure.</span></span> <span data-ttu-id="f4692-348">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="f4692-348">You must also specify the action in the send port.</span></span>  
  
    -   <span data-ttu-id="f4692-349">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置將訊息從 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f4692-349">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the messages from the Oracle database.</span></span> <span data-ttu-id="f4692-350">這些將會從 Oracle 資料庫接收的通知訊息和訊息執行透過 Wcf-custom PROCESS_RECORDS 程序或 Wcf-oracledb 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f4692-350">These will be the notification messages received from the Oracle database and messages for the PROCESS_RECORDS procedure you execute through the WCF-Custom or WCF-OracleDB send port.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="f4692-351">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="f4692-351">Starting the Application</span></span>  
 <span data-ttu-id="f4692-352">您必須啟動 BizTalk 應用程式來接收通知訊息，從 Oracle 資料庫及執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-352">You must start the BizTalk application for receiving notification messages from the Oracle database and for executing the PROCESS_RECORDS procedure.</span></span> <span data-ttu-id="f4692-353">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-353">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="f4692-354">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="f4692-354">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="f4692-355">Wcf-custom 或 Wcf-oracledb 單向接收埠，會從 Oracle 資料庫執行時接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="f4692-355">The WCF-Custom or WCF-OracleDB one-way receive port, which receives the notification messages from the Oracle database is running.</span></span>  
  
-   <span data-ttu-id="f4692-356">Wcf-custom 或 Wcf-oracledb 傳送埠執行 PROCESS_RECORDS 程序正在執行。</span><span class="sxs-lookup"><span data-stu-id="f4692-356">The WCF-Custom or WCF-OracleDB send port to execute the PROCESS_RECORDS procedure is running.</span></span>  
  
-   <span data-ttu-id="f4692-357">檔案傳送埠，從 Oracle 資料庫接收訊息，正在執行。</span><span class="sxs-lookup"><span data-stu-id="f4692-357">The FILE send port, which receives messages from the Oracle database, is running.</span></span>  
  
-   <span data-ttu-id="f4692-358">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="f4692-358">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="f4692-359">執行作業</span><span class="sxs-lookup"><span data-stu-id="f4692-359">Executing the Operation</span></span>  
 <span data-ttu-id="f4692-360">假設 ACCOUNTACTIVITY 資料表已經有一些記錄。</span><span class="sxs-lookup"><span data-stu-id="f4692-360">Assume that the ACCOUNTACTIVITY table already has some records.</span></span> <span data-ttu-id="f4692-361">此外，請確定執行 PROCESS_RECORDS 程序的 XML 訊息將會位於 C:\TestLocation\MessageIn。</span><span class="sxs-lookup"><span data-stu-id="f4692-361">Also, make sure the XML message to execute PROCESS_RECORDS procedure is available at C:\TestLocation\MessageIn.</span></span> <span data-ttu-id="f4692-362">XML 檔案應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="f4692-362">The XML file should resemble the following:</span></span>  
  
```  
<PROCESS_RECORDS xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG"/>  
```  
  
 <span data-ttu-id="f4692-363">一旦啟動 BizTalk 協調流程，執行下列一進行，以相同順序：</span><span class="sxs-lookup"><span data-stu-id="f4692-363">Once the BizTalk orchestration is started, the following set of actions take place, in the same sequence:</span></span>  
  
-   <span data-ttu-id="f4692-364">配接器接收通知訊息類似如下：</span><span class="sxs-lookup"><span data-stu-id="f4692-364">The adapter receives a notification message that resembles the following:</span></span>  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?\>   
    <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
      <Info>ListenerStarted</Info>   
      <Source>OracleDBBinding</Source>   
      <Type>Startup</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="f4692-365">此訊息會通知啟動時接收通知訊息的接收埠。</span><span class="sxs-lookup"><span data-stu-id="f4692-365">This message notifies that the receive port for receiving the notification messages is started.</span></span> <span data-ttu-id="f4692-366">請注意，值`<Info>`項目，則 「 ListnerStarted"。</span><span class="sxs-lookup"><span data-stu-id="f4692-366">Note that the value for the `<Info>` element is “ListnerStarted”.</span></span>  
  
-   <span data-ttu-id="f4692-367">配接器執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-367">The adapter executes the PROCESS_RECORDS procedure.</span></span> <span data-ttu-id="f4692-368">從 Oracle 資料庫的下一個回應是程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-368">The next response from the Oracle database is for the procedure.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <PROCESS_RECORDSResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
      <TABLE_DATA>  
        <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          <xs:element msdata:IsDataSet="true" name="NewDataSet">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  <xs:complexType>  
                    <xs:sequence>  
                      <xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
                    </xs:sequence>  
                  </xs:complexType>  
                </xs:element>  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
        </xs:schema>  
        <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
        <NewDataSet xmlns="">  
          <NewTable>  
            <TID>1</TID>   
            <ACCOUNT>100001</ACCOUNT>   
            <PROCESSED>n</PROCESSED>   
          </NewTable>  
          <NewTable>  
            ......  
            ......  
          </NewTable>  
          ......  
          ......  
        </NewDataSet>  
        </diffgr:diffgram>  
      </TABLE_DATA>  
    </PROCESS_RECORDSResponse>  
    ```  
  
     <span data-ttu-id="f4692-369">這是 SELECT 陳述式執行 PROCESS_RECORDS 程序的回應。</span><span class="sxs-lookup"><span data-stu-id="f4692-369">This is the response for the SELECT statement execute as part of the PROCESS_RECORDS procedure.</span></span>  
  
-   <span data-ttu-id="f4692-370">PROCESS_RECORDS 程序也會更新為 'y' 設定已處理的資料列。</span><span class="sxs-lookup"><span data-stu-id="f4692-370">The PROCESS_RECORDS procedure also updates the rows to set PROCESSED to ‘y’.</span></span> <span data-ttu-id="f4692-371">因此，配接器會接收另一個更新作業的通知。</span><span class="sxs-lookup"><span data-stu-id="f4692-371">Hence, the adapter receives another notification for the Update operation.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
      <Details>  
        <NotificationDetails>  
          <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
          <Info>32</Info>   
          <QueryId>0</QueryId>   
        </NotificationDetails>  
      </Details>  
      <Info>Update</Info>   
      <ResourceNames>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
      </ResourceNames>  
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="f4692-372">請注意，`Info`元素包含 「 更新 」。</span><span class="sxs-lookup"><span data-stu-id="f4692-372">Note that the `Info` element contains “Update”.</span></span>  
  
-   <span data-ttu-id="f4692-373">之後，第二個通知配接器一次執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="f4692-373">After the second notification, the adapter again executes the PROCESS_RECORDS procedure.</span></span> <span data-ttu-id="f4692-374">不過，現在已處理的資料行且設為沒有記錄，因為 ' n '，程序會傳回空的回應類似於下列。</span><span class="sxs-lookup"><span data-stu-id="f4692-374">However, now because there are no records where PROCESSED column is set to ‘n’, the procedure returns an empty response resembling the following.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <PROCESS_RECORDSResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
      <TABLE_DATA>  
        <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          <xs:element msdata:IsDataSet="true" name="NewDataSet">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  <xs:complexType>  
                    <xs:sequence>  
                      <xs:element minOccurs="0" name="TID" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="ACCOUNT" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="PROCESSED" type="xs:string" />   
                    </xs:sequence>  
                  </xs:complexType>  
                </xs:element>  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
        </xs:schema>  
        <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
          <NewDataSet xmlns="" />   
        </diffgr:diffgram>  
      </TABLE_DATA>  
    </PROCESS_RECORDSResponse>  
    ```  
  
## <a name="best-practices"></a><span data-ttu-id="f4692-375">最佳作法</span><span class="sxs-lookup"><span data-stu-id="f4692-375">Best Practices</span></span>  
 <span data-ttu-id="f4692-376">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="f4692-376">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="f4692-377">一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立傳送埠和接收相同的協調流程連接埠。</span><span class="sxs-lookup"><span data-stu-id="f4692-377">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create the send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="f4692-378">如需繫結檔案的詳細資訊，請參閱[重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="f4692-378">For more information about binding files, see [Reuse Oracle Database Adapter bindings](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4692-379">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4692-379">See Also</span></span>  
 [<span data-ttu-id="f4692-380">使用 BizTalk Server 接收的 Oracle 資料庫變更通知</span><span class="sxs-lookup"><span data-stu-id="f4692-380">Receiving Oracle Database Change Notifications Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)