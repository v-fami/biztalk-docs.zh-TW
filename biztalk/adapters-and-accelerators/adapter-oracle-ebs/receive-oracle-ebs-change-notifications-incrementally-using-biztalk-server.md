---
title: 接收以累加方式使用 BizTalk Server 的 Oracle E-business Suite 變更通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63dbeacc-ecde-497d-b12d-d5f9944a33f0
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c596a5a383f55f38f90a367caae45a4ce3ec0e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004847"
---
# <a name="receive-oracle-e-business-suite-change-notifications-incrementally-using-biztalk-server"></a><span data-ttu-id="26bec-102">接收以累加方式使用 BizTalk Server 的 Oracle E-business Suite 變更通知</span><span class="sxs-lookup"><span data-stu-id="26bec-102">Receive Oracle E-Business Suite change notifications incrementally using BizTalk Server</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="26bec-103">為了簡潔起見，本主題僅說明如何以累加方式接收通知。</span><span class="sxs-lookup"><span data-stu-id="26bec-103">For the sake of brevity, this topic only describes how to receive notifications incrementally.</span></span> <span data-ttu-id="26bec-104">在商務案例中，協調流程必須在理想情況下會納入邏輯來擷取收到的通知訊息的類型，然後再執行任何後續的作業。</span><span class="sxs-lookup"><span data-stu-id="26bec-104">In business scenarios, the orchestration must ideally include the logic to extract the kind of notification message received and then perform any subsequent operations.</span></span> <span data-ttu-id="26bec-105">本主題中所述的協調流程換句話說，必須採用協調流程中所述[處理通知訊息，以便將 Oracle E-business Suite 中完成特定工作](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-105">In other words, the orchestration described in this topic must be built on top of the orchestration described in [Process Notification Messages to Complete Specific Tasks in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md).</span></span>  
  
 <span data-ttu-id="26bec-106">本主題示範如何設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle 接收累加式的查詢通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-106">This topic demonstrates how to configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive incremental query notification messages from Oracle.</span></span> <span data-ttu-id="26bec-107">為了示範累加通知，我們假設資料表，ACCOUNTACTIVITY，具有 「 處理 」 資料行。</span><span class="sxs-lookup"><span data-stu-id="26bec-107">To demonstrate incremental notifications, we consider a table, ACCOUNTACTIVITY, with a “Processed” column.</span></span> <span data-ttu-id="26bec-108">此資料表插入新記錄時，「 處理 」 資料行的值設為 ' n '。</span><span class="sxs-lookup"><span data-stu-id="26bec-108">When a new record is inserted to this table, the value of the “Processed” column is set to ‘n’.</span></span> <span data-ttu-id="26bec-109">您可以設定配接器接收累加的通知，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="26bec-109">You can configure the adapter to receive incremental notifications by doing the following:</span></span>  
  
- <span data-ttu-id="26bec-110">註冊通知使用的 SELECT 陳述式會擷取所有記錄具有 「 處理 」 資料行做為 ' n '。</span><span class="sxs-lookup"><span data-stu-id="26bec-110">Register for notifications using a SELECT statement that retrieves all records that have “Processed” column as ‘n’.</span></span> <span data-ttu-id="26bec-111">則可以藉由指定 SELECT 陳述式，如**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-111">You can do so by specifying the SELECT statement for the **NotificationStatement** binding property.</span></span>  
  
- <span data-ttu-id="26bec-112">對於已通知的資料列，更新為 'y' 的 「 處理 」 資料行。</span><span class="sxs-lookup"><span data-stu-id="26bec-112">For rows which have been notified for, update the “Processed” column to ‘y’.</span></span>  
  
  <span data-ttu-id="26bec-113">本主題示範如何建立 BizTalk 協調流程和設定 BizTalk 應用程式來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="26bec-113">This topic demonstrates how to create a BizTalk orchestration and configure a BizTalk application to achieve this.</span></span>  
  
## <a name="configuring-notifications-with-the-oracle-e-business-adapter-binding-properties"></a><span data-ttu-id="26bec-114">使用 Oracle E-business 配接器繫結屬性中設定通知</span><span class="sxs-lookup"><span data-stu-id="26bec-114">Configuring Notifications with the Oracle E-Business Adapter Binding Properties</span></span>  
 <span data-ttu-id="26bec-115">下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，您用來設定從 Oracle E-business Suite 接收通知。</span><span class="sxs-lookup"><span data-stu-id="26bec-115">The table below summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure receiving notifications from Oracle E-Business Suite.</span></span> <span data-ttu-id="26bec-116">您必須在設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="26bec-116">You must specify these binding properties while configuring the receive port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26bec-117">您也可以指定這些繫結屬性，產生的結構描述時**通知**作業，即使它不是強制性。</span><span class="sxs-lookup"><span data-stu-id="26bec-117">You may choose to specify these binding properties when generating the schema for the **Notification** operation, even though it is not mandatory.</span></span> <span data-ttu-id="26bec-118">如果您這樣做時，連接埠繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="26bec-118">If you do so, the port binding file that the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] generates as part of the metadata generation also contains the values you specify for the binding properties.</span></span> <span data-ttu-id="26bec-119">您可以稍後匯入此繫結檔案中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂或 Wcf-oracleebs 與繫結屬性已設定接收埠。</span><span class="sxs-lookup"><span data-stu-id="26bec-119">You can later import this binding file in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create the WCF-custom or WCF-OracleEBS receive port with the binding properties already set.</span></span> <span data-ttu-id="26bec-120">如需建立接收埠使用的繫結檔案的詳細資訊，請參閱 <<c0> [ 設定實體的連接埠繫結使用的連接埠繫結檔案至 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-120">For more information about creating a receive port using the binding file, see [Configure a Physical Port Binding Using a Port Binding File to Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).</span></span>  
  
|<span data-ttu-id="26bec-121">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="26bec-121">Binding Property</span></span>|<span data-ttu-id="26bec-122">描述</span><span class="sxs-lookup"><span data-stu-id="26bec-122">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="26bec-123">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="26bec-123">**InboundOperationType**</span></span>|<span data-ttu-id="26bec-124">指定輸入您想要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="26bec-124">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="26bec-125">若要接收通知訊息，將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="26bec-125">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="26bec-126">**NotificationPort**</span><span class="sxs-lookup"><span data-stu-id="26bec-126">**NotificationPort**</span></span>|<span data-ttu-id="26bec-127">指定 ODP.NET 必須開啟以接聽從 Oracle 資料庫的資料庫變更通知的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="26bec-127">Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.</span></span>|  
|<span data-ttu-id="26bec-128">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="26bec-128">**NotificationStatement**</span></span>|<span data-ttu-id="26bec-129">指定用來註冊查詢通知的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="26bec-129">Specifies the SELECT statement used to register for query notifications.</span></span> <span data-ttu-id="26bec-130">配接器在結果集，指定 SELECT 陳述式變更時，才取得通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-130">The adapter gets a notification message only when the result set for the specified SELECT statement changes.</span></span>|  
|<span data-ttu-id="26bec-131">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="26bec-131">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="26bec-132">指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。</span><span class="sxs-lookup"><span data-stu-id="26bec-132">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="26bec-133">如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-133">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="26bec-134">如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]若要從 Oracle E-business Suite 接收通知，可深入閱讀。</span><span class="sxs-lookup"><span data-stu-id="26bec-134">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive notifications from Oracle E-Business Suite, read further.</span></span>  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a><span data-ttu-id="26bec-135">本主題示範接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="26bec-135">How This Topic Demonstrates Receiving Notification Messages</span></span>  
 <span data-ttu-id="26bec-136">本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援從 Oracle E-business Suite 接收累加資料庫變更通知訊息，我們會設定配接器接收 ACCOUNTACTIVTY 資料表所做變更的通知。</span><span class="sxs-lookup"><span data-stu-id="26bec-136">In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving incremental database change notification messages from Oracle E-Business Suite, we will configure the adapter to receive notifications for changes to the ACCOUNTACTIVTY table.</span></span> <span data-ttu-id="26bec-137">讓我們假設 ACCOUNTACTIVITY 資料表有資料行"TID 」、 「 帳戶 」 和 「 處理 」。</span><span class="sxs-lookup"><span data-stu-id="26bec-137">Let us assume that the ACCOUNTACTIVITY table has columns “TID”, “Account”, and “Processed”.</span></span> <span data-ttu-id="26bec-138">每當新增新的記錄時，「 處理 」 資料行的值設為 ' n '。</span><span class="sxs-lookup"><span data-stu-id="26bec-138">Whenever a new record is added, the value of the “Processed” column is set to ‘n’.</span></span> <span data-ttu-id="26bec-139">因此，若要取得累加通知您必須為 BizTalk 協調流程的一部分執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="26bec-139">So, to get incremental notifications you will have to do the following tasks as part of the BizTalk orchestration:</span></span>  
  
- <span data-ttu-id="26bec-140">取得通知，其中是 「 處理 」 的所有記錄的 ' n '。</span><span class="sxs-lookup"><span data-stu-id="26bec-140">Get notification for all records where “Processed” is ‘n’.</span></span> <span data-ttu-id="26bec-141">您可以指定做為通知的陳述式的 SELECT 陳述式來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="26bec-141">You can do this by specifying a SELECT statement as a notification statement.</span></span>  
  
- <span data-ttu-id="26bec-142">某些記錄收到通知之後，請為 'y' 中設定 「 處理 」。</span><span class="sxs-lookup"><span data-stu-id="26bec-142">After the notification is received for a certain record, set “Processed” to ‘y’.</span></span> <span data-ttu-id="26bec-143">您可以執行預存程序，PROCESS_RECORDS，更新 「 處理 」 的資料行來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="26bec-143">You can do this by executing a stored procedure, PROCESS_RECORDS, which updates the “Processed” column.</span></span>  
  
  <span data-ttu-id="26bec-144">為了示範接收累加的通知，我們執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="26bec-144">To demonstrate receiving incremental notifications, we do the following:</span></span>  
  
- <span data-ttu-id="26bec-145">產生結構描述**通知**（輸入作業），以及**PROCESS_RECORDS** （輸出作業） ACCOUNTACTIVITY 資料表上。</span><span class="sxs-lookup"><span data-stu-id="26bec-145">Generate schema for the **Notification** (inbound operation), and **PROCESS_RECORDS** (outbound operation) on the ACCOUNTACTIVITY table.</span></span>  
  
- <span data-ttu-id="26bec-146">建立具有下列的協調流程：</span><span class="sxs-lookup"><span data-stu-id="26bec-146">Create an orchestration that has the following:</span></span>  
  
  -   <span data-ttu-id="26bec-147">接收位置來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-147">A receive location to receive notification messages.</span></span> <span data-ttu-id="26bec-148">您可以藉由指定 SELECT 陳述式設定通知：</span><span class="sxs-lookup"><span data-stu-id="26bec-148">You can configure for notification by specifying the SELECT statement as:</span></span>  
  
      ```  
      SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
      ```  
  
      > [!NOTE]
      >  <span data-ttu-id="26bec-149">您必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="26bec-149">You must specify the table name along with the schema name.</span></span> <span data-ttu-id="26bec-150">例如， `SCOTT.ACCOUNTACTIVITY`。</span><span class="sxs-lookup"><span data-stu-id="26bec-150">For example, `SCOTT.ACCOUNTACTIVITY`.</span></span>  
  
  -   <span data-ttu-id="26bec-151">傳送埠，以更新的通知已傳送的資料列。</span><span class="sxs-lookup"><span data-stu-id="26bec-151">A send port to update the rows for which notification has already been sent.</span></span> <span data-ttu-id="26bec-152">您將執行 PROCESS_RECORDS 預存程序，在此連接埠設為 'y' 收到通知的記錄的 「 處理 」 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="26bec-152">You will execute the PROCESS_RECORDS stored procedure on this port to set the value of “Processed” column to ‘y’ for the records for which notification is received.</span></span>  
  
       <span data-ttu-id="26bec-153">請注意接收通知訊息，以便處理的資料列更新之後，必須執行此作業。</span><span class="sxs-lookup"><span data-stu-id="26bec-153">Note that this operation must be executed after receiving the notification messages so that the processed rows are updated.</span></span> <span data-ttu-id="26bec-154">若要執行立即等候取得通知回應，然後再手動卸除執行 PROCESS_RECORDS 程序的要求訊息的額外負荷，您將會產生 PROCESS_RECORDS 程序協調流程本身內的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-154">To do away with the overhead of waiting to get the notification response and then manually dropping a request message to execute the PROCESS_RECORDS procedure, you will generate the request message for PROCESS_RECORDS procedure within the orchestration itself.</span></span> <span data-ttu-id="26bec-155">您可以使用來進行這**建構訊息**協調流程內的圖形。</span><span class="sxs-lookup"><span data-stu-id="26bec-155">You can do so by using the **Construct Message** shape within an orchestration.</span></span>  
  
## <a name="how-to-receive-notification-messages-from-oracle-e-business-suite"></a><span data-ttu-id="26bec-156">如何從 Oracle E-business Suite 接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="26bec-156">How to Receive Notification Messages from Oracle E-Business Suite</span></span>  
 <span data-ttu-id="26bec-157">執行的作業上使用 Oracle E-business Suite[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[若要建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-157">Performing an operation on Oracle E-Business Suite using [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves the procedural tasks described in [Building Blocks to create Oracle E-Business Suite Applications](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md).</span></span> <span data-ttu-id="26bec-158">若要設定要接收通知訊息的介面卡，這些工作如下：</span><span class="sxs-lookup"><span data-stu-id="26bec-158">To configure the adapter to receive notification messages, these tasks are:</span></span>  
  
1. <span data-ttu-id="26bec-159">建立 BizTalk 專案，然後再產生結構描述**通知**（輸入作業） 和**PROCESS_RECORDS** ACCOUNTACTIVITY 資料表上的程序 （輸出作業）。</span><span class="sxs-lookup"><span data-stu-id="26bec-159">Create a BizTalk project, and then generate schema for the **Notification** (inbound operation) and **PROCESS_RECORDS** procedure (outbound operation) on the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="26bec-160">您可以選擇性地指定值**InboundOperationType**， **NotificationPort**，並**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-160">Optionally, you can specify values for the **InboundOperationType**, **NotificationPort**, and **NotificationStatement** binding properties.</span></span>  
  
2. <span data-ttu-id="26bec-161">從 Oracle E-business Suite 接收通知的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-161">Create a message in the BizTalk project for receiving notification from Oracle E-Business Suite.</span></span>  
  
3. <span data-ttu-id="26bec-162">在執行 PROCESS_RECORDS 預存程序，並接收回應訊息的 BizTalk 專案中的訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-162">Create messages in the BizTalk project for executing the PROCESS_RECORDS stored procedure and receiving response messages.</span></span>  
  
4. <span data-ttu-id="26bec-163">建立協調流程，會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="26bec-163">Create an orchestration that does the following:</span></span>  
  
   -   <span data-ttu-id="26bec-164">從 Oracle E-business Suite 接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-164">Receives notification message from Oracle E-Business Suite.</span></span>  
  
   -   <span data-ttu-id="26bec-165">建立要執行 PROCESS_RECORDS 程序的訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-165">Creates a message to execute the PROCESS_RECORDS procedure.</span></span>  
  
   -   <span data-ttu-id="26bec-166">將此訊息傳送至 Oracle E-business Suite，以選取和更新記錄並接收回應。</span><span class="sxs-lookup"><span data-stu-id="26bec-166">Sends this message to Oracle E-Business Suite to select and update the records and receive a response.</span></span>  
  
5. <span data-ttu-id="26bec-167">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="26bec-167">Build and deploy the BizTalk project.</span></span>  
  
6. <span data-ttu-id="26bec-168">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="26bec-168">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="26bec-169">輸入的作業，例如接收通知訊息，您必須只設定單向的 WCF 自訂或 Wcf-oracleebs 接收埠。</span><span class="sxs-lookup"><span data-stu-id="26bec-169">For inbound operations, like receiving notification messages, you must only configure a one-way WCF-Custom or WCF-OracleEBS receive port.</span></span> <span data-ttu-id="26bec-170">雙向接收埠不支援的輸入作業。</span><span class="sxs-lookup"><span data-stu-id="26bec-170">Two-way receive ports are not supported for inbound operations.</span></span>  
  
7. <span data-ttu-id="26bec-171">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="26bec-171">Start the BizTalk application.</span></span>  
  
   <span data-ttu-id="26bec-172">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="26bec-172">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="26bec-173">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="26bec-173">Generating Schema</span></span>  
 <span data-ttu-id="26bec-174">您必須產生的結構描述**通知**作業並**PROCESS_RECORDS**程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-174">You must generate the schema for the **Notification** operation and **PROCESS_RECORDS** procedure.</span></span> <span data-ttu-id="26bec-175">請參閱[擷取 Oracle E-business Suite 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="26bec-175">See [Retrieving Metadata for Oracle E-Business Suite Operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) for more information about how to generate the schema.</span></span> <span data-ttu-id="26bec-176">產生結構描述時，請執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="26bec-176">Perform the following tasks when generating the schema.</span></span> <span data-ttu-id="26bec-177">如果您不想指定在設計階段的繫結屬性，請略過第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="26bec-177">Skip the first step if you do not want to specify the binding properties at design-time.</span></span>  
  
1.  <span data-ttu-id="26bec-178">指定的值**InboundOperationType**， **NotificationPort**，並**NotificationStatement**時產生結構描述繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-178">Specify a value for **InboundOperationType**, **NotificationPort**, and **NotificationStatement** binding properties while generating the schema.</span></span> <span data-ttu-id="26bec-179">如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-179">For more information about this binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="26bec-180">如需有關如何指定繫結屬性的指示，請參閱 < [for Oracle E-business Suite 中設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-180">For instructions on how to specify binding properties, see [Configure the Binding Properties for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).</span></span>  
  
2.  <span data-ttu-id="26bec-181">選取合約類型作為**服務 （輸入作業）**。</span><span class="sxs-lookup"><span data-stu-id="26bec-181">Select the contract type as **Service (Inbound operations)**.</span></span>  
  
3.  <span data-ttu-id="26bec-182">產生結構描述**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="26bec-182">Generate schema for the **Notification** operation.</span></span>  
  
4.  <span data-ttu-id="26bec-183">選取合約類型作為**用戶端 （傳出作業）**。</span><span class="sxs-lookup"><span data-stu-id="26bec-183">Select the contract type as **Client (Outbound operations)**.</span></span>  
  
5.  <span data-ttu-id="26bec-184">產生結構描述**PROCESS_RECORDS**程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-184">Generate schema for the **PROCESS_RECORDS** procedure.</span></span> <span data-ttu-id="26bec-185">此程序，會位於**ACCOUNT_PKG**封裝。</span><span class="sxs-lookup"><span data-stu-id="26bec-185">This procedure is available under the **ACCOUNT_PKG** package.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="26bec-186">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="26bec-186">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="26bec-187">您稍早產生的結構描述會描述協調流程中的訊息所需的 「 類型 」。</span><span class="sxs-lookup"><span data-stu-id="26bec-187">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="26bec-188">訊息通常是一個變數，要為其類型會定義對應的結構。</span><span class="sxs-lookup"><span data-stu-id="26bec-188">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="26bec-189">一旦產生結構描述時，您必須訊息從 BizTalk 專案的協調流程檢視以將它的連結。</span><span class="sxs-lookup"><span data-stu-id="26bec-189">Once the schema is generated, you must link it to the messages from the Orchestration view of the BizTalk project.</span></span>  
  
 <span data-ttu-id="26bec-190">本主題中，您必須建立三個訊息，分別從 Oracle E-business Suite 接收通知、 執行 PROCESS_RECORDS 程序，和一個用於接收程序的回應。</span><span class="sxs-lookup"><span data-stu-id="26bec-190">For this topic, you must create three messages—one to receive notifications from the Oracle E-Business Suite, one to execute the PROCESS_RECORDS procedure, and one to receive the response for the procedure.</span></span>  
  
 <span data-ttu-id="26bec-191">執行下列步驟來建立訊息，並將它們連結至結構描述。</span><span class="sxs-lookup"><span data-stu-id="26bec-191">Perform the following steps to create messages and link them to schema.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="26bec-192">若要建立訊息，並連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="26bec-192">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="26bec-193">BizTalk 專案中新增協調流程。</span><span class="sxs-lookup"><span data-stu-id="26bec-193">Add an orchestration to the BizTalk project.</span></span> <span data-ttu-id="26bec-194">從 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="26bec-194">From the Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="26bec-195">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="26bec-195">Type a name for the BizTalk orchestration and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="26bec-196">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="26bec-196">Open the orchestration view window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="26bec-197">按一下 **檢視**，指向**其他 Windows**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="26bec-197">Click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="26bec-198">在 **協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="26bec-198">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="26bec-199">以滑鼠右鍵按一下新建立的訊息，然後按**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="26bec-199">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="26bec-200">在 [**屬性**] 窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="26bec-200">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="26bec-201">使用</span><span class="sxs-lookup"><span data-stu-id="26bec-201">Use this</span></span>|<span data-ttu-id="26bec-202">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="26bec-202">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="26bec-203">識別碼</span><span class="sxs-lookup"><span data-stu-id="26bec-203">Identifier</span></span>|<span data-ttu-id="26bec-204">輸入 `NotifyReceive`。</span><span class="sxs-lookup"><span data-stu-id="26bec-204">Type `NotifyReceive`.</span></span>|  
    |<span data-ttu-id="26bec-205">訊息類型</span><span class="sxs-lookup"><span data-stu-id="26bec-205">Message Type</span></span>|<span data-ttu-id="26bec-206">從下拉式清單中，依序展開**結構描述**，然後選取*OracleNotifyIncremental.OracleEBSBinding.Notification*，其中*OracleNotifyIncremental*的名稱您的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="26bec-206">From the drop-down list, expand **Schemas**, and select *OracleNotifyIncremental.OracleEBSBinding.Notification*, where *OracleNotifyIncremental* is the name of your BizTalk project.</span></span> <span data-ttu-id="26bec-207">*OracleEBSBinding*是針對產生的結構描述**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="26bec-207">*OracleEBSBinding* is the schema generated for the **Notification** operation.</span></span>|  
  
6.  <span data-ttu-id="26bec-208">重複步驟 3 以建立兩個新的訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-208">Repeat step 3 to create two new messages.</span></span> <span data-ttu-id="26bec-209">在 **屬性**窗格中的新訊息，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="26bec-209">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="26bec-210">若要設定識別項</span><span class="sxs-lookup"><span data-stu-id="26bec-210">Set Identifier to</span></span>|<span data-ttu-id="26bec-211">若要設定訊息類型</span><span class="sxs-lookup"><span data-stu-id="26bec-211">Set Message Type to</span></span>|  
    |-----------------------|-------------------------|  
    |<span data-ttu-id="26bec-212">程序</span><span class="sxs-lookup"><span data-stu-id="26bec-212">Procedure</span></span>|<span data-ttu-id="26bec-213">*OracleNotifyIncremental.OracleEBSBinding1.PROCESS_RECORDS*，其中*OracleEBSBinding1*是針對產生的結構描述**PROCESS_RECORDS**程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-213">*OracleNotifyIncremental.OracleEBSBinding1.PROCESS_RECORDS*, where  *OracleEBSBinding1* is the schema generated for the **PROCESS_RECORDS** procedure.</span></span>|  
    |<span data-ttu-id="26bec-214">ProcedureResponse</span><span class="sxs-lookup"><span data-stu-id="26bec-214">ProcedureResponse</span></span>|<span data-ttu-id="26bec-215">*OracleNotifyIncremental.OracleEBSBinding1.PROCESS_RECORDSResponse*</span><span class="sxs-lookup"><span data-stu-id="26bec-215">*OracleNotifyIncremental.OracleEBSBinding1.PROCESS_RECORDSResponse*</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="26bec-216">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="26bec-216">Setting up the Orchestration</span></span>  
 <span data-ttu-id="26bec-217">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]for Oracle E-business Suite 中接收通知訊息，然後更新 收到通知的資料列。</span><span class="sxs-lookup"><span data-stu-id="26bec-217">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving notification messages from Oracle E-Business Suite and then updating the rows for which notification was received.</span></span> <span data-ttu-id="26bec-218">在此協調流程中，配接器會接收依據指定的 SELECT 陳述式的通知訊息**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-218">In this orchestration, the adapter receives the notification message based on the SELECT statement specified for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="26bec-219">檔案位置就會收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-219">The notification message is received at a FILE location.</span></span> <span data-ttu-id="26bec-220">一旦收到回應時，協調流程會建構要叫用的 PROCESS_RECORDS 程序，更新的資料列，收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-220">Once the response is received, the orchestration constructs a message to invoke the PROCESS_RECORDS procedure, which updates the rows for which notification is received.</span></span> <span data-ttu-id="26bec-221">此訊息的回應也就會收到相同的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="26bec-221">The response for this message is also received at the same FILE location.</span></span>  
  
 <span data-ttu-id="26bec-222">因此，您的協調流程必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="26bec-222">So, your orchestration must contain the following:</span></span>  
  
- <span data-ttu-id="26bec-223">單向的 「 WCF 自訂 」 或 「 Wcf-oracleebs 接收埠來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-223">A one-way WCF-Custom or WCF-OracleEBS receive port to receive notification messages.</span></span>  
  
- <span data-ttu-id="26bec-224">雙向的 「 WCF 自訂 」 或 「 Wcf-oracleebs 傳送埠將訊息傳送至執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-224">A two-way WCF-Custom or WCF-OracleEBS send port to send messages to execute the PROCESS_RECORDS procedure.</span></span>  
  
- <span data-ttu-id="26bec-225">A**建構訊息**圖形來建構執行 PROCESS_RECORDS 程序，在協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-225">A **Construct Message** shape to construct messages, to execute PROCESS_RECORDS procedure, within the orchestration.</span></span>  
  
- <span data-ttu-id="26bec-226">檔案傳送埠以儲存通知訊息和 PROCESS_RECORDS 程序的回應。</span><span class="sxs-lookup"><span data-stu-id="26bec-226">A FILE send port to save the notification message and the response for the PROCESS_RECORDS procedure.</span></span>  
  
- <span data-ttu-id="26bec-227">接收和傳送圖形。</span><span class="sxs-lookup"><span data-stu-id="26bec-227">Receive and send shapes.</span></span>  
  
  <span data-ttu-id="26bec-228">範例協調流程如下所示。</span><span class="sxs-lookup"><span data-stu-id="26bec-228">A sample orchestration resembles the following.</span></span>  
  
  <span data-ttu-id="26bec-229">![若要從 Oracle 接收通知的協調流程](../../adapters-and-accelerators/adapter-oracle-database/media/cef49414-490a-4bd5-a32d-b3f4cde5950a.gif "cef49414-490a-4bd5-a32d-b3f4cde5950a")</span><span class="sxs-lookup"><span data-stu-id="26bec-229">![Orchestration to receive notifications from Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/cef49414-490a-4bd5-a32d-b3f4cde5950a.gif "cef49414-490a-4bd5-a32d-b3f4cde5950a")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="26bec-230">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="26bec-230">Adding Message Shapes</span></span>  
 <span data-ttu-id="26bec-231">請確定您針對每個訊息 圖形中指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-231">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="26bec-232">剛剛提到的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。</span><span class="sxs-lookup"><span data-stu-id="26bec-232">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="26bec-233">形狀圖</span><span class="sxs-lookup"><span data-stu-id="26bec-233">Shape</span></span>|<span data-ttu-id="26bec-234">圖形類型</span><span class="sxs-lookup"><span data-stu-id="26bec-234">Shape Type</span></span>|<span data-ttu-id="26bec-235">屬性</span><span class="sxs-lookup"><span data-stu-id="26bec-235">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="26bec-236">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="26bec-236">ReceiveNotification</span></span>|<span data-ttu-id="26bec-237">Receive</span><span class="sxs-lookup"><span data-stu-id="26bec-237">Receive</span></span>|<span data-ttu-id="26bec-238">-設定**名稱**到*ReceiveNotification*</span><span class="sxs-lookup"><span data-stu-id="26bec-238">- Set **Name** to *ReceiveNotification*</span></span><br /><br /> <span data-ttu-id="26bec-239">-設定**啟用**到 *，則為 True*</span><span class="sxs-lookup"><span data-stu-id="26bec-239">- Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="26bec-240">SaveNotification</span><span class="sxs-lookup"><span data-stu-id="26bec-240">SaveNotification</span></span>|<span data-ttu-id="26bec-241">Send</span><span class="sxs-lookup"><span data-stu-id="26bec-241">Send</span></span>|<span data-ttu-id="26bec-242">-設定**名稱**到*SaveNotification*</span><span class="sxs-lookup"><span data-stu-id="26bec-242">- Set **Name** to *SaveNotification*</span></span>|  
|<span data-ttu-id="26bec-243">SendProcMessage</span><span class="sxs-lookup"><span data-stu-id="26bec-243">SendProcMessage</span></span>|<span data-ttu-id="26bec-244">Send</span><span class="sxs-lookup"><span data-stu-id="26bec-244">Send</span></span>|<span data-ttu-id="26bec-245">-設定**名稱**到*SendProcMessage*</span><span class="sxs-lookup"><span data-stu-id="26bec-245">- Set **Name** to *SendProcMessage*</span></span>|  
|<span data-ttu-id="26bec-246">ReceiveProcResponse</span><span class="sxs-lookup"><span data-stu-id="26bec-246">ReceiveProcResponse</span></span>|<span data-ttu-id="26bec-247">Receive</span><span class="sxs-lookup"><span data-stu-id="26bec-247">Receive</span></span>|<span data-ttu-id="26bec-248">-設定**名稱**到*ReceiveProcResponse*</span><span class="sxs-lookup"><span data-stu-id="26bec-248">- Set **Name** to *ReceiveProcResponse*</span></span>|  
|<span data-ttu-id="26bec-249">SaveProcResponse</span><span class="sxs-lookup"><span data-stu-id="26bec-249">SaveProcResponse</span></span>|<span data-ttu-id="26bec-250">Send</span><span class="sxs-lookup"><span data-stu-id="26bec-250">Send</span></span>|<span data-ttu-id="26bec-251">-設定**名稱**到*SaveProcResponse*</span><span class="sxs-lookup"><span data-stu-id="26bec-251">- Set **Name** to *SaveProcResponse*</span></span>|  
  
### <a name="adding-construct-message-shape"></a><span data-ttu-id="26bec-252">新增 建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="26bec-252">Adding Construct Message Shape</span></span>  
 <span data-ttu-id="26bec-253">您可以使用**建構訊息**產生要求訊息的協調流程內執行 PROCESS_RECORDS 程序的圖形。</span><span class="sxs-lookup"><span data-stu-id="26bec-253">You can use the **Construct Message** shape to generate a request message within the orchestration to execute the PROCESS_RECORDS procedure.</span></span> <span data-ttu-id="26bec-254">若要這樣做，您必須加入**建構的訊息**圖形，並在其中**訊息指派**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="26bec-254">To do so, you must add a **Construct Message** shape and within that a **Message Assignment** shape to your orchestration.</span></span> <span data-ttu-id="26bec-255">此範例中，如**訊息指派**圖形叫用程式碼，就會產生執行程序傳送至 Oracle E-business Suite 的訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-255">For this example, the **Message Assignment** shape invokes code that generates a message that is sent to Oracle E-Business Suite to execute the procedure.</span></span> <span data-ttu-id="26bec-256">**訊息指派**圖形也會將訊息傳送至 Oracle E-business Suite 的動作。</span><span class="sxs-lookup"><span data-stu-id="26bec-256">The **Message Assignment** shape also sets the action for the message to be sent to Oracle E-Business Suite.</span></span>  
  
 <span data-ttu-id="26bec-257">針對 「 建構訊息 」 圖形中，設定**建構的訊息**屬性設**程序**。</span><span class="sxs-lookup"><span data-stu-id="26bec-257">For the construct message shape, set the **Message Constructed** property to **Procedure**.</span></span>  
  
 <span data-ttu-id="26bec-258">若要產生回應的程式碼可以是相同的 Visual Studio 方案，為您的 BizTalk 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="26bec-258">The code to generate the response could be part of the same Visual Studio solution as your BizTalk project.</span></span> <span data-ttu-id="26bec-259">產生回應訊息的範例程式碼看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="26bec-259">A sample code for generating a response message looks like this.</span></span>  
  
```  
namespace MessageCreator  
{  
    public class MessageCreator  
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
  
 <span data-ttu-id="26bec-260">上述程式碼摘錄中能夠產生要求訊息，您必須 （適用於 PROCESS_RECORDS 程序） XML 要求訊息中指定的位置`XmlFileLocation`變數。</span><span class="sxs-lookup"><span data-stu-id="26bec-260">For the above code excerpt to be able to generate a request message, you must have an XML request message (for the PROCESS_RECORDS procedure) in the location specified for the `XmlFileLocation` variable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26bec-261">建置專案之後，就會建立 MessageCreator.dll 專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="26bec-261">After you build the project, MessageCreator.dll will be created in the project directory.</span></span> <span data-ttu-id="26bec-262">您必須將此 DLL 加入全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="26bec-262">You must add this DLL to the global assembly cache (GAC).</span></span> <span data-ttu-id="26bec-263">此外，您必須新增 MessageCreator.dll 做為 BizTalk 專案中的參考。</span><span class="sxs-lookup"><span data-stu-id="26bec-263">Also, you must add the MessageCreator.dll as a reference in the BizTalk project.</span></span>  
  
 <span data-ttu-id="26bec-264">加入下列運算式來叫用此程式碼**訊息指派**圖形，並設定訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="26bec-264">Add the following expression to invoke this code from the **Message Assignment** shape and to set the action for message.</span></span> <span data-ttu-id="26bec-265">若要新增運算式，請按兩下**訊息指派**圖形以開啟 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="26bec-265">To add an expression, double-click the **Message Assignment** shape to open the Expression Editor.</span></span>  
  
```  
Procedure = MessageCreator.MessageCreator.XMLMessageCreator();  
Procedure(WCF.Action) = "PackageApis/SCOTT/ACCOUNT_PKG/PROCESS_RECORDS";  
```  
  
### <a name="adding-ports"></a><span data-ttu-id="26bec-266">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="26bec-266">Adding Ports</span></span>  
 <span data-ttu-id="26bec-267">請確定您針對每個邏輯連接埠中指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-267">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="26bec-268">協調流程中所示，連接埠資料行中所列的名稱會是連接埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="26bec-268">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="26bec-269">通訊埠</span><span class="sxs-lookup"><span data-stu-id="26bec-269">Port</span></span>|<span data-ttu-id="26bec-270">屬性</span><span class="sxs-lookup"><span data-stu-id="26bec-270">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="26bec-271">OracleNotifyPort</span><span class="sxs-lookup"><span data-stu-id="26bec-271">OracleNotifyPort</span></span>|<span data-ttu-id="26bec-272">-設定**識別碼**到*OracleNotifyPort*</span><span class="sxs-lookup"><span data-stu-id="26bec-272">- Set **Identifier** to *OracleNotifyPort*</span></span><br /><br /> <span data-ttu-id="26bec-273">-設定**型別**到*OracleNotifyPortType*</span><span class="sxs-lookup"><span data-stu-id="26bec-273">- Set **Type** to *OracleNotifyPortType*</span></span><br /><br /> <span data-ttu-id="26bec-274">-設定**通訊模式**到*單向*</span><span class="sxs-lookup"><span data-stu-id="26bec-274">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="26bec-275">-設定**通訊方向**到*接收*</span><span class="sxs-lookup"><span data-stu-id="26bec-275">- Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="26bec-276">SaveMessagePort</span><span class="sxs-lookup"><span data-stu-id="26bec-276">SaveMessagePort</span></span>|<span data-ttu-id="26bec-277">-設定**識別碼**到*SaveMessagePort*</span><span class="sxs-lookup"><span data-stu-id="26bec-277">- Set **Identifier** to *SaveMessagePort*</span></span><br /><br /> <span data-ttu-id="26bec-278">-設定**型別**到*SaveMessagePortType*</span><span class="sxs-lookup"><span data-stu-id="26bec-278">- Set **Type** to *SaveMessagePortType*</span></span><br /><br /> <span data-ttu-id="26bec-279">-設定**通訊模式**到*單向*</span><span class="sxs-lookup"><span data-stu-id="26bec-279">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="26bec-280">-設定**通訊方向**到*傳送*</span><span class="sxs-lookup"><span data-stu-id="26bec-280">- Set **Communication Direction** to *Send*</span></span><br /><br /> <span data-ttu-id="26bec-281">-建立作業*通知*。</span><span class="sxs-lookup"><span data-stu-id="26bec-281">- Create an operation *Notify*.</span></span> <span data-ttu-id="26bec-282">這項作業用於通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-282">This operation is used for notification messages.</span></span><br /><br /> <span data-ttu-id="26bec-283">-建立作業*程序*。</span><span class="sxs-lookup"><span data-stu-id="26bec-283">- Create an operation *Procedure*.</span></span> <span data-ttu-id="26bec-284">此作業可用於選取的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-284">This operation is used for select response messages.</span></span>|  
|<span data-ttu-id="26bec-285">OracleOutboundPort</span><span class="sxs-lookup"><span data-stu-id="26bec-285">OracleOutboundPort</span></span>|<span data-ttu-id="26bec-286">-設定**識別碼**到*OracleOutboundPort*</span><span class="sxs-lookup"><span data-stu-id="26bec-286">- Set **Identifier** to *OracleOutboundPort*</span></span><br /><br /> <span data-ttu-id="26bec-287">-設定**型別**到*OracleOutboundPortType*</span><span class="sxs-lookup"><span data-stu-id="26bec-287">- Set **Type** to *OracleOutboundPortType*</span></span><br /><br /> <span data-ttu-id="26bec-288">-設定**通訊模式**到*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="26bec-288">- Set **Communication Pattern** to *Request-Response*</span></span><br /><br /> <span data-ttu-id="26bec-289">-設定**通訊方向**到*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="26bec-289">- Set **Communication Direction** to *Send-Receive*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a><span data-ttu-id="26bec-290">為動作圖形指定訊息，並連接到連接埠</span><span class="sxs-lookup"><span data-stu-id="26bec-290">Specify Messages for Action Shapes and Connect to Ports</span></span>  
 <span data-ttu-id="26bec-291">下表指定的屬性和屬性來指定動作圖形的訊息，以及連結至連接埠的訊息，您應該設定的值。</span><span class="sxs-lookup"><span data-stu-id="26bec-291">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="26bec-292">先前所述的協調流程中所示，圖形資料行中所列的名稱會是訊息 圖形的名稱。</span><span class="sxs-lookup"><span data-stu-id="26bec-292">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="26bec-293">形狀圖</span><span class="sxs-lookup"><span data-stu-id="26bec-293">Shape</span></span>|<span data-ttu-id="26bec-294">屬性</span><span class="sxs-lookup"><span data-stu-id="26bec-294">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="26bec-295">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="26bec-295">ReceiveNotification</span></span>|<span data-ttu-id="26bec-296">-設定**訊息**到*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="26bec-296">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="26bec-297">-設定**作業**到*OracleNotifyPort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="26bec-297">- Set **Operation** to *OracleNotifyPort.Notify.Request*</span></span>|  
|<span data-ttu-id="26bec-298">SaveNotification</span><span class="sxs-lookup"><span data-stu-id="26bec-298">SaveNotification</span></span>|<span data-ttu-id="26bec-299">-設定**訊息**到*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="26bec-299">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="26bec-300">-設定**作業**到*SaveMessagePort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="26bec-300">- Set **Operation** to *SaveMessagePort.Notify.Request*</span></span>|  
|<span data-ttu-id="26bec-301">SendProcMessage</span><span class="sxs-lookup"><span data-stu-id="26bec-301">SendProcMessage</span></span>|<span data-ttu-id="26bec-302">-設定**訊息**到*程序*</span><span class="sxs-lookup"><span data-stu-id="26bec-302">- Set **Message** to *Procedure*</span></span><br /><br /> <span data-ttu-id="26bec-303">-設定**作業**到*OracleOutboundPort.Procedure.Request*</span><span class="sxs-lookup"><span data-stu-id="26bec-303">- Set **Operation** to *OracleOutboundPort.Procedure.Request*</span></span>|  
|<span data-ttu-id="26bec-304">ReceiveProcResponse</span><span class="sxs-lookup"><span data-stu-id="26bec-304">ReceiveProcResponse</span></span>|<span data-ttu-id="26bec-305">-設定**訊息**到*ProcedureResponse*</span><span class="sxs-lookup"><span data-stu-id="26bec-305">- Set **Message** to *ProcedureResponse*</span></span><br /><br /> <span data-ttu-id="26bec-306">-設定**作業**到*OracleOutboundPort.Procedure.Response*</span><span class="sxs-lookup"><span data-stu-id="26bec-306">- Set **Operation** to *OracleOutboundPort.Procedure.Response*</span></span>|  
|<span data-ttu-id="26bec-307">SaveProcResponse</span><span class="sxs-lookup"><span data-stu-id="26bec-307">SaveProcResponse</span></span>|<span data-ttu-id="26bec-308">-設定**訊息**到*ProedureResponse*</span><span class="sxs-lookup"><span data-stu-id="26bec-308">- Set **Message** to *ProedureResponse*</span></span><br /><br /> <span data-ttu-id="26bec-309">-設定**作業**到*SaveMessagePort.Procedure.Request*</span><span class="sxs-lookup"><span data-stu-id="26bec-309">- Set **Operation** to *SaveMessagePort.Procedure.Request*</span></span>|  
  
 <span data-ttu-id="26bec-310">您指定這些屬性之後，連線的訊息 圖形和連接埠和協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="26bec-310">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="26bec-311">您現在必須建置 BizTalk 方案，並將其部署至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="26bec-311">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="26bec-312">詳細資訊，請參閱 < 建置和執行協調流程 >，網址[ http://go.microsoft.com/fwlink/?LinkId=102359 ](http://go.microsoft.com/fwlink/?LinkId=102359)。</span><span class="sxs-lookup"><span data-stu-id="26bec-312">For more information, see "Building and Running Orchestrations" at [http://go.microsoft.com/fwlink/?LinkId=102359](http://go.microsoft.com/fwlink/?LinkId=102359).</span></span>  
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="26bec-313">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="26bec-313">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="26bec-314">您已部署的 BizTalk 專案之後，您稍早建立的協調流程會列在下**協調流程** 窗格中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="26bec-314">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="26bec-315">您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="26bec-315">You must use the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the application.</span></span> <span data-ttu-id="26bec-316">設定應用程式的詳細資訊，請參閱 「 如何設定應用程式 」，網址[ http://go.microsoft.com/fwlink/?LinkID=196961 ](http://go.microsoft.com/fwlink/?LinkID=196961)。</span><span class="sxs-lookup"><span data-stu-id="26bec-316">For more information about configuring an application, see "How to Configure an Application" at [http://go.microsoft.com/fwlink/?LinkID=196961](http://go.microsoft.com/fwlink/?LinkID=196961).</span></span>  
  
 <span data-ttu-id="26bec-317">設定應用程式包含：</span><span class="sxs-lookup"><span data-stu-id="26bec-317">Configuring an application involves:</span></span>  
  
- <span data-ttu-id="26bec-318">選取應用程式主機。</span><span class="sxs-lookup"><span data-stu-id="26bec-318">Selecting a host for the application.</span></span>  
  
- <span data-ttu-id="26bec-319">對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="26bec-319">Mapping the ports that you created in your orchestration to physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="26bec-320">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="26bec-320">For this orchestration you must:</span></span>  
  
  - <span data-ttu-id="26bec-321">定義實體的 Wcf-custom 或 Wcf-oracleebs 單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="26bec-321">Define a physical WCF-Custom or WCF-OracleEBS one-way receive port.</span></span> <span data-ttu-id="26bec-322">此連接埠會接聽來自 Oracle E-business Suite 的通知。</span><span class="sxs-lookup"><span data-stu-id="26bec-322">This port listens for notifications coming from Oracle E-Business Suite.</span></span> <span data-ttu-id="26bec-323">如需有關如何建立接收埠，請參閱[手動設定實體連接埠繫結來 Oracle E-business 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-323">For information about how to create receive ports, see [Manually Configuring a Physical Port Binding to the Oracle E-Business Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md).</span></span> <span data-ttu-id="26bec-324">請確定指定接收埠的下列繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-324">Make sure you specify the following binding properties for the receive port.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="26bec-325">您不需要執行此步驟中，如果您指定在設計階段的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-325">You do not need to perform this step if you specified the binding properties at design-time.</span></span> <span data-ttu-id="26bec-326">在這種情況下，您可以建立接收埠，設定必要的繫結屬性，藉由匯入所建立的繫結檔[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="26bec-326">In such a case, you can create a receive port, with the required binding properties set, by importing the binding file created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="26bec-327">如需詳細資訊，請參閱[實體連接埠繫結使用的連接埠繫結檔設定到 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-327">For more information see [Configure a Physical Port Binding Using a Port Binding File to Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).</span></span>  
  
    |<span data-ttu-id="26bec-328">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="26bec-328">Binding Property</span></span>|<span data-ttu-id="26bec-329">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="26bec-329">Value</span></span>|  
    |----------------------|-----------|  
    |<span data-ttu-id="26bec-330">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="26bec-330">**InboundOperationType**</span></span>|<span data-ttu-id="26bec-331">將此設為**通知**。</span><span class="sxs-lookup"><span data-stu-id="26bec-331">Set this to **Notification**.</span></span>|  
    |<span data-ttu-id="26bec-332">**NotificationPort**</span><span class="sxs-lookup"><span data-stu-id="26bec-332">**NotificationPort**</span></span>|<span data-ttu-id="26bec-333">指定 ODP.NET 必須開啟以接聽從 Oracle 資料庫的資料庫變更通知的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="26bec-333">Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.</span></span> <span data-ttu-id="26bec-334">設定為相同的連接埠號碼，您必須已加入的 Windows 防火牆例外清單。</span><span class="sxs-lookup"><span data-stu-id="26bec-334">Set this to the same port number that you must have added to the Windows Firewall exceptions list.</span></span> <span data-ttu-id="26bec-335">如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=196959 ](http://go.microsoft.com/fwlink/?LinkID=196959)。</span><span class="sxs-lookup"><span data-stu-id="26bec-335">For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).</span></span><br /><br /> <span data-ttu-id="26bec-336">**重要事項：** 如果您設定為預設值-1，您必須完全停用 Windows 防火牆，以接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-336">**Important:** If you set this to the default value of -1, you will have to completely disable Windows Firewall to receive notification messages.</span></span>|  
    |<span data-ttu-id="26bec-337">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="26bec-337">**NotificationStatement**</span></span>|<span data-ttu-id="26bec-338">將此設為：</span><span class="sxs-lookup"><span data-stu-id="26bec-338">Set this to:</span></span><br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’`<br /><br /> <span data-ttu-id="26bec-339">**注意：** 您必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="26bec-339">**Note:** You must specify the table name along with the schema name.</span></span> <span data-ttu-id="26bec-340">例如， `SCOTT.ACCOUNTACTIVITY`。</span><span class="sxs-lookup"><span data-stu-id="26bec-340">For example, `SCOTT.ACCOUNTACTIVITY`.</span></span>|  
    |<span data-ttu-id="26bec-341">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="26bec-341">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="26bec-342">將此設為 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="26bec-342">Set this to **True**.</span></span>|  
  
     <span data-ttu-id="26bec-343">如需不同的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-343">For more information about the different binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="26bec-344">如果您要設定的介面資料表的通知，您必須設定應用程式內容，藉由指定必要的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="26bec-344">If you are configuring notifications for an interface table, you must set the application context by specifying the requisite binding properties.</span></span> <span data-ttu-id="26bec-345">如需設定應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-345">For more information about setting the application context see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
    > 
    > [!NOTE]
    >  <span data-ttu-id="26bec-346">我們建議您執行使用的輸入的操作時設定的交易隔離等級和交易等待時間[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="26bec-346">We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="26bec-347">您可以這麼設定 Wcf-custom 時新增的服務行為或 Wcf-oracleebs 接收埠。</span><span class="sxs-lookup"><span data-stu-id="26bec-347">You can do so by adding the service behavior while configuring the WCF-Custom or WCF-OracleEBS receive port.</span></span> <span data-ttu-id="26bec-348">如需有關如何新增服務行為的指示，請參閱[設定交易隔離等級和交易等待時間，使用 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-348">For instruction on how to add the service behavior, see [Configure Transaction Isolation Level and Transaction Timeout with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).</span></span>  
  
  - <span data-ttu-id="26bec-349">定義實體的 Wcf-custom 或 Wcf-oracleebs 傳送埠將訊息傳送至 Oracle E-business Suite，才能執行 PROCESS_REOCRDS 程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-349">Define a physical WCF-Custom or WCF-OracleEBS send port to send messages to Oracle E-Business Suite to execute the PROCESS_REOCRDS procedure.</span></span> <span data-ttu-id="26bec-350">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="26bec-350">You must also specify the action in the send port.</span></span>  
  
  - <span data-ttu-id="26bec-351">定義位置上的硬碟和對應的檔案連接埠，其中 BizTalk 協調流程時，會從 Oracle E-business Suite 捨棄訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-351">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the messages from Oracle E-Business Suite.</span></span> <span data-ttu-id="26bec-352">這些是從 Oracle E-business Suite 接收通知訊息和傳送埠執行透過 Wcf-custom 或 Wcf-oracleebs PROCESS_RECORDS 程序的訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-352">These will be the notification messages received from Oracle E-Business Suite and messages for the PROCESS_RECORDS procedure you execute through the WCF-Custom or WCF-OracleEBS send port.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="26bec-353">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="26bec-353">Starting the Application</span></span>  
 <span data-ttu-id="26bec-354">您必須啟動 BizTalk 應用程式從 Oracle E-business Suite 接收通知訊息，並執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-354">You must start the BizTalk application for receiving notification messages from Oracle E-Business Suite and for executing the PROCESS_RECORDS procedure.</span></span> <span data-ttu-id="26bec-355">如需啟動 BizTalk 應用程式的指示，請參閱 」 方式來啟動協調流程 」 在[ http://go.microsoft.com/fwlink/?LinkId=102387 ](http://go.microsoft.com/fwlink/?LinkId=102387)。</span><span class="sxs-lookup"><span data-stu-id="26bec-355">For instructions on starting a BizTalk application, see “How to Start an Orchestration” at  [http://go.microsoft.com/fwlink/?LinkId=102387](http://go.microsoft.com/fwlink/?LinkId=102387).</span></span>  
  
 <span data-ttu-id="26bec-356">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="26bec-356">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="26bec-357">Wcf-custom 或 Wcf-oracleebs 單向接收埠，它會從 Oracle E-business Suite 接收通知訊息正在執行。</span><span class="sxs-lookup"><span data-stu-id="26bec-357">The WCF-Custom or WCF-OracleEBS one-way receive port, which receives the notification messages from Oracle E-Business Suite is running.</span></span>  
  
-   <span data-ttu-id="26bec-358">Wcf-custom 或 Wcf-oracleebs 傳送埠，才能執行 PROCESS_RECORDS 程序正在執行。</span><span class="sxs-lookup"><span data-stu-id="26bec-358">The WCF-Custom or WCF-OracleEBS send port to execute the PROCESS_RECORDS procedure is running.</span></span>  
  
-   <span data-ttu-id="26bec-359">FILE 傳送埠，會從 Oracle E-business Suite 接收的訊息，正在執行。</span><span class="sxs-lookup"><span data-stu-id="26bec-359">The FILE send port, which receives messages from Oracle E-Business Suite, is running.</span></span>  
  
-   <span data-ttu-id="26bec-360">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="26bec-360">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="26bec-361">執行作業</span><span class="sxs-lookup"><span data-stu-id="26bec-361">Executing the Operation</span></span>  
 <span data-ttu-id="26bec-362">假設 ACCOUNTACTIVITY 資料表已經有一些記錄。</span><span class="sxs-lookup"><span data-stu-id="26bec-362">Assume that the ACCOUNTACTIVITY table already has some records.</span></span> <span data-ttu-id="26bec-363">此外，請確定要執行 PROCESS_RECORDS 程序的 XML 訊息將會位於 C:\TestLocation\MessageIn。</span><span class="sxs-lookup"><span data-stu-id="26bec-363">Also, make sure the XML message to execute PROCESS_RECORDS procedure is available at C:\TestLocation\MessageIn.</span></span> <span data-ttu-id="26bec-364">XML 檔案應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="26bec-364">The XML file should resemble the following:</span></span>  
  
```  
<PROCESS_RECORDS xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/SCOTT/ACCOUNT_PKG" />  
```  
  
 <span data-ttu-id="26bec-365">一旦啟動 BizTalk 協調流程之後，下列的一組動作進行相同的順序：</span><span class="sxs-lookup"><span data-stu-id="26bec-365">Once the BizTalk orchestration is started, the following set of actions take place, in the same sequence:</span></span>  
  
-   <span data-ttu-id="26bec-366">配接器接收通知訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="26bec-366">The adapter receives a notification message that resembles the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/">  
      <Info>ListenerStarted</Info>   
      <Source>OracleEBSBinding</Source>   
      <Type>Startup</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="26bec-367">此訊息會通知已啟動 接收埠來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="26bec-367">This message notifies that the receive port for receiving the notification messages is started.</span></span> <span data-ttu-id="26bec-368">請注意，值`<Info>`項目是 「 ListnerStarted"。</span><span class="sxs-lookup"><span data-stu-id="26bec-368">Note that the value for the `<Info>` element is “ListnerStarted”.</span></span>  
  
-   <span data-ttu-id="26bec-369">配接器執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-369">The adapter executes the PROCESS_RECORDS procedure.</span></span> <span data-ttu-id="26bec-370">Oracle E-business Suite 的下一個回應是程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-370">The next response from Oracle E-Business Suite is for the procedure.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <PROCESS_RECORDSResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/SCOTT/ACCOUNT_PKG">  
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
  
     <span data-ttu-id="26bec-371">這是回應 PROCESS_RECORDS 程序的一部分執行的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="26bec-371">This is the response for the SELECT statement execute as part of the PROCESS_RECORDS procedure.</span></span>  
  
-   <span data-ttu-id="26bec-372">PROCESS_RECORDS 程序也會更新為 'y' 設定已處理的資料列。</span><span class="sxs-lookup"><span data-stu-id="26bec-372">The PROCESS_RECORDS procedure also updates the rows to set PROCESSED to ‘y’.</span></span> <span data-ttu-id="26bec-373">因此，配接器接收的更新作業的另一個通知。</span><span class="sxs-lookup"><span data-stu-id="26bec-373">Hence, the adapter receives another notification for the Update operation.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/">  
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
  
     <span data-ttu-id="26bec-374">請注意，`Info`元素包含"Update"。</span><span class="sxs-lookup"><span data-stu-id="26bec-374">Note that the `Info` element contains “Update”.</span></span>  
  
-   <span data-ttu-id="26bec-375">第二個通知之後，配接器一次執行 PROCESS_RECORDS 程序。</span><span class="sxs-lookup"><span data-stu-id="26bec-375">After the second notification, the adapter again executes the PROCESS_RECORDS procedure.</span></span> <span data-ttu-id="26bec-376">不過，現在因為沒有的記錄之已處理的資料行設定為 ' n '，此程序會傳回類似下列的空白回應。</span><span class="sxs-lookup"><span data-stu-id="26bec-376">However, now because there are no records where PROCESSED column is set to ‘n’, the procedure returns an empty response resembling the following.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <PROCESS_RECORDSResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/SCOTT/ACCOUNT_PKG">  
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
  
## <a name="best-practices"></a><span data-ttu-id="26bec-377">最佳作法</span><span class="sxs-lookup"><span data-stu-id="26bec-377">Best Practices</span></span>  
 <span data-ttu-id="26bec-378">您部署和設定 BizTalk 專案之後，您可以匯出至 XML 檔案，稱為繫結檔案的組態設定。</span><span class="sxs-lookup"><span data-stu-id="26bec-378">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="26bec-379">一旦您產生繫結檔案時，您可以匯入的組態設定檔案，，讓您不需要建立傳送埠和接收相同的協調流程的連接埠。</span><span class="sxs-lookup"><span data-stu-id="26bec-379">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create the send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="26bec-380">如需有關繫結檔案的詳細資訊，請參閱 <<c0> [ 重複使用與 Oracle E-business Suite 配接器繫結](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="26bec-380">For more information about binding files, see [Reuse Adapter Bindings with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bec-381">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26bec-381">See Also</span></span>  
 [<span data-ttu-id="26bec-382">Oracle E-business Suite 使用接收資料庫變更通知 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="26bec-382">Receive Oracle E-Business Suite Database Change Notifications using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-biztalk-server.md)