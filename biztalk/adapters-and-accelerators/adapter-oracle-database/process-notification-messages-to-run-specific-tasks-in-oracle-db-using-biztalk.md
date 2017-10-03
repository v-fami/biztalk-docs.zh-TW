---
title: "處理通知訊息，以便完成特定工作在 Oracle 資料庫中使用 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 376055a7-98a6-4055-b6cd-2f5971349a6a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97fa5f9d0eebeeaf7a7dcb264feb33373e48484d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="process-notification-messages-to-complete-specific-tasks-in-oracle-database-using-biztalk-server"></a><span data-ttu-id="1cada-102">若要完成使用 BizTalk Server 的 Oracle 資料庫中的特定工作的程序通知訊息</span><span class="sxs-lookup"><span data-stu-id="1cada-102">Process notification messages to complete specific tasks in Oracle Database using BizTalk Server</span></span>
<span data-ttu-id="1cada-103">您可以使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收通知的 Oracle 資料庫資料表的變更。</span><span class="sxs-lookup"><span data-stu-id="1cada-103">You can use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive notifications for changes to the Oracle database tables.</span></span> <span data-ttu-id="1cada-104">不過，配接器只會傳送一些記錄已插入、 更新或刪除特定資料庫資料表中的通知。</span><span class="sxs-lookup"><span data-stu-id="1cada-104">However, the adapter only sends you a notification that some records were inserted, updated, or deleted in a certain database table.</span></span> <span data-ttu-id="1cada-105">用戶端應用程式本身必須處理這些記錄的任何後續處理。</span><span class="sxs-lookup"><span data-stu-id="1cada-105">Any post-processing on those records must be handled by the client applications themselves.</span></span> <span data-ttu-id="1cada-106">本主題顯示如何處理從 Oracle 資料庫接收通知的種類為基礎的資料表中的記錄以案例為基礎的描述。</span><span class="sxs-lookup"><span data-stu-id="1cada-106">This topic presents a scenario-based description on how to process the records in the table based on the kind of notification received from the Oracle database.</span></span>  
  
## <a name="scenarios-for-performing-subsequent-actions-after-receiving-notification"></a><span data-ttu-id="1cada-107">執行後續的動作，在收到通知的案例</span><span class="sxs-lookup"><span data-stu-id="1cada-107">Scenarios for Performing Subsequent Actions After Receiving Notification</span></span>  
 <span data-ttu-id="1cada-108">以下是幾個案例中，配接器用戶端必須執行某些通知後工作。</span><span class="sxs-lookup"><span data-stu-id="1cada-108">Following are a couple of scenarios in which the adapter clients must perform certain post-notification tasks.</span></span>  
  
-   <span data-ttu-id="1cada-109">**案例 1。**</span><span class="sxs-lookup"><span data-stu-id="1cada-109">**Scenario 1.**</span></span> <span data-ttu-id="1cada-110">假設配接器用戶端必須執行特定工作，根據您從 Oracle 資料庫接收的通知類型的地方。</span><span class="sxs-lookup"><span data-stu-id="1cada-110">Consider a scenario where the adapter client must perform certain tasks based on the kind of notification you receive from the Oracle database.</span></span> <span data-ttu-id="1cada-111">例如，用戶端應用程式必須更新"A"資料表中的記錄，如果要在資料表"B"中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="1cada-111">For example, the client application must update the records in table “A” if records are inserted in table “B”.</span></span> <span data-ttu-id="1cada-112">同樣地，用戶端應用程式必須記錄如果刪除資料表"A"從"B"資料表刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="1cada-112">Similarly, the client application must delete records from table “A” if records are deleted from table “B”.</span></span>  
  
     <span data-ttu-id="1cada-113">在此案例中，我們收到的通知訊息從配接器用戶端必須擷取決定通知是否為 insert 或 delete 作業的通知類型。</span><span class="sxs-lookup"><span data-stu-id="1cada-113">In this scenario, from the notification message received, the adapter clients must extract the type of notification to decide whether the notification was for an insert operation or a delete operation.</span></span> <span data-ttu-id="1cada-114">一旦為 reflection 的通知類型，配接器用戶端必須執行插入或更新的相關資料表的後續動作。</span><span class="sxs-lookup"><span data-stu-id="1cada-114">Once the notification type is ascertained, the adapter clients must perform subsequent actions to insert or update the relevant tables.</span></span>  
  
-   <span data-ttu-id="1cada-115">**案例 2。**</span><span class="sxs-lookup"><span data-stu-id="1cada-115">**Scenario 2.**</span></span> <span data-ttu-id="1cada-116">假設接收到的資料表所做變更的通知訊息的接收位置會中斷。</span><span class="sxs-lookup"><span data-stu-id="1cada-116">Consider a scenario where the receive location that receives notification messages for changes to a table goes down.</span></span> <span data-ttu-id="1cada-117">接收位置已關閉，而某些記錄會加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="1cada-117">While the receive location is down, some records are added to the table.</span></span> <span data-ttu-id="1cada-118">不過，這些記錄配接器用戶端沒有收到任何通知。</span><span class="sxs-lookup"><span data-stu-id="1cada-118">However, for these records the adapter client does not receive any notification.</span></span> <span data-ttu-id="1cada-119">備份 接收位置時，配接器可以傳送特定訊息，通知用戶端，然後向下接收位置時，已插入資料庫資料表中的所有記錄必須都尋找用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="1cada-119">When the receive location is back up, the adapter notifies the client by sending a specific message, and then the client application must look for all the records that were inserted in the database table while the receive location was down.</span></span>  
  
     <span data-ttu-id="1cada-120">在此案例中，我們收到的通知訊息從配接器用戶端必須擷取之通知是資料庫資料表的變更或接收位置開始的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1cada-120">In this scenario, from the notification message received, the adapter clients must extract the information regarding whether the notification is for a change to a database table or for the receive location starting.</span></span> <span data-ttu-id="1cada-121">如果通知的接收位置開始，配接器用戶端必須實作邏輯以處理可能會有已插入、 更新或刪除接收位置時關閉記錄。</span><span class="sxs-lookup"><span data-stu-id="1cada-121">If the notification is for the receive location starting, the adapter clients must implement the logic to process the records that might have been inserted, updated, or deleted while the receive location was down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cada-122">這些是一些範例案例，進一步了解如何使用 「 通知 」 功能中的所列[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1cada-122">These are just some example scenarios that are listed for a better understanding of how to use the notification feature in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="1cada-123">不過，一組基本的擷取收到的通知類型所需的工作將會在所有案例類似。</span><span class="sxs-lookup"><span data-stu-id="1cada-123">However, the basic set of tasks required to extract the type of notification received will be similar for all scenarios.</span></span> <span data-ttu-id="1cada-124">本主題說明如何擷取通知訊息的通知類型。</span><span class="sxs-lookup"><span data-stu-id="1cada-124">This topic provides instructions on how to extract the type of notification from a notification message.</span></span>  
  
## <a name="how-this-topic-demonstrates-receiving-notification-messages"></a><span data-ttu-id="1cada-125">本主題示範接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="1cada-125">How This Topic Demonstrates Receiving Notification Messages</span></span>  
 <span data-ttu-id="1cada-126">本主題中，以示範如何處理通知訊息，以執行後續工作，我們假設基本配接器用戶端使用的 BizTalk 應用程式來接收 ACCOUNTACTIVITY 資料表所做變更的通知訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="1cada-126">In this topic, to demonstrate how to process notification messages to perform subsequent tasks, we consider a basic scenario where an adapter client uses BizTalk application to receive notification messages for changes to the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="1cada-127">在收到通知之後，用戶端篩選的收到的通知類型，並執行後續動作。</span><span class="sxs-lookup"><span data-stu-id="1cada-127">After the notification is received, the client filters the type of notification received and performs subsequent action.</span></span> <span data-ttu-id="1cada-128">若要示範非常基本的案例，讓我們考慮，配接器用戶端會將通知訊息複製到不同的資料夾，根據收到的通知類型。</span><span class="sxs-lookup"><span data-stu-id="1cada-128">To demonstrate a very basic scenario, let us consider that the adapter client copies the notification messages to different folders based on the kind of notification received.</span></span> <span data-ttu-id="1cada-129">因此：</span><span class="sxs-lookup"><span data-stu-id="1cada-129">Therefore:</span></span>  
  
-   <span data-ttu-id="1cada-130">如果 Insert 或 Update 作業的通知訊息，配接器用戶端會將訊息複製 C:\TestLocation\UpsertNotification 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1cada-130">If the notification message is for an Insert or Update operation, the adapter client copies the message to C:\TestLocation\UpsertNotification folder.</span></span>  
  
-   <span data-ttu-id="1cada-131">如果通知訊息的任何其他作業，例如刪除，配接器用戶端會將訊息複製到 C:\TestLocation\OtherNotificaiton 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1cada-131">If the notification message is for any other operation, for example Delete, the adapter client copies the message to C:\TestLocation\OtherNotificaiton folder.</span></span>  
  
 <span data-ttu-id="1cada-132">若要達到這做為 BizTalk 應用程式的一部分，協調流程必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="1cada-132">To achieve this as part of a BizTalk application, the orchestration must contain the following:</span></span>  
  
-   <span data-ttu-id="1cada-133">單向接收埠以接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-133">A one-way receive port to receive notification messages.</span></span>  
  
-   <span data-ttu-id="1cada-134">「 運算式 」 圖形，其中包含 xpath 查詢來擷取收到的通知訊息的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="1cada-134">An Expression shape that contains an xpath query to extract the information about the kind of notification message received.</span></span>  
  
-   <span data-ttu-id="1cada-135">在協調流程中包含決策區塊 「 決定 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="1cada-135">A Decide shape to include a decision block in the orchestration.</span></span> <span data-ttu-id="1cada-136">在此決策區塊中，應用程式決定要執行的後續作業基礎收到的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-136">In this decision block, the application decides on what subsequent operations to perform based on the notification message received.</span></span>  
  
-   <span data-ttu-id="1cada-137">兩個單向傳送埠，最後接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-137">Two one-way send ports that finally receive the notification messages.</span></span>  
  
## <a name="configuring-notifications-with-the-oracle-database-binding-properties"></a><span data-ttu-id="1cada-138">與 Oracle 資料庫繫結屬性中設定通知</span><span class="sxs-lookup"><span data-stu-id="1cada-138">Configuring Notifications with the Oracle Database Binding Properties</span></span>  
 <span data-ttu-id="1cada-139">下表摘要說明[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結，您用來設定從 Oracle 資料庫接收通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-139">The following table summarizes the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties that you use to configure receiving notifications from the Oracle database.</span></span> <span data-ttu-id="1cada-140">您必須同時設定接收埠中的指定這些繫結屬性[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1cada-140">You must specify these binding properties while configuring the receive port in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cada-141">您可以選擇指定這些繫結內容產生的結構描述時**通知**作業，即使它不是強制性。</span><span class="sxs-lookup"><span data-stu-id="1cada-141">You may choose to specify these binding properties when generating the schema for the **Notification** operation, even though it is not mandatory.</span></span> <span data-ttu-id="1cada-142">如果您這樣做，連接埠繫結檔，[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]產生的中繼資料產生的組件也包含您指定的繫結屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1cada-142">If you do so, the port binding file that the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] generates as part of the metadata generation also contains the values you specify for the binding properties.</span></span> <span data-ttu-id="1cada-143">您可以稍後匯入此繫結檔案[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來建立 WCF 自訂或 Wcf-oracledb 接收埠以繫結已設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-143">You can later import this binding file in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create the WCF-custom or WCF-OracleDB receive port with the binding properties already set.</span></span> <span data-ttu-id="1cada-144">如需有關如何建立 wcf-custom 或 Wcf-oracledb 的連接埠，使用繫結檔案的詳細資訊，請參閱[設定使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-144">For more information about creating a WCF-custom or WCF-OracleDB port using the binding file, see [Configure a physical port binding using a port Binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).</span></span>  
  
|<span data-ttu-id="1cada-145">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="1cada-145">Binding Property</span></span>|<span data-ttu-id="1cada-146">Description</span><span class="sxs-lookup"><span data-stu-id="1cada-146">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="1cada-147">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="1cada-147">**InboundOperationType**</span></span>|<span data-ttu-id="1cada-148">指定輸入您想要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-148">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="1cada-149">若要接收通知訊息，將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="1cada-149">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="1cada-150">**NotificationPort**</span><span class="sxs-lookup"><span data-stu-id="1cada-150">**NotificationPort**</span></span>|<span data-ttu-id="1cada-151">指定 ODP.NET 必須開啟從 Oracle 資料庫的資料庫變更通知所接聽的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="1cada-151">Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.</span></span>|  
|<span data-ttu-id="1cada-152">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="1cada-152">**NotificationStatement**</span></span>|<span data-ttu-id="1cada-153">指定用來註冊查詢通知的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1cada-153">Specifies the SELECT statement used to register for query notifications.</span></span> <span data-ttu-id="1cada-154">僅在結果集，指定 SELECT 陳述式變更時，配接器會取得通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-154">The adapter gets a notification message only when the result set for the specified SELECT statement changes.</span></span>|  
|<span data-ttu-id="1cada-155">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="1cada-155">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="1cada-156">指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。</span><span class="sxs-lookup"><span data-stu-id="1cada-156">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="1cada-157">如需這些屬性的更完整說明，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1cada-157">For a more complete description of these properties, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span> <span data-ttu-id="1cada-158">如需完整的說明，如何使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]進一步若要從 Oracle 資料庫接收通知，閱讀。</span><span class="sxs-lookup"><span data-stu-id="1cada-158">For a complete description of how to use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive notifications from the Oracle database, read further.</span></span>  
  
## <a name="how-to-receive-notification-messages-from-oracle-database"></a><span data-ttu-id="1cada-159">如何從 Oracle 資料庫接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="1cada-159">How to Receive Notification Messages from Oracle Database</span></span>  
 <span data-ttu-id="1cada-160">針對 Oracle 資料庫使用執行運算[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]涉及程序中所述的工作[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-160">Performing an operation on the Oracle database using [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves the procedural tasks described in [Building blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md).</span></span> <span data-ttu-id="1cada-161">若要設定要接收通知訊息的介面卡，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="1cada-161">To configure the adapter to receive notification messages, these tasks are:</span></span>  
  
1.  <span data-ttu-id="1cada-162">建立 BizTalk 專案，然後再產生結構描述的**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-162">Create a BizTalk project, and then generate schema for the **Notification** inbound operation.</span></span> <span data-ttu-id="1cada-163">您可以選擇性地指定值**InboundOperationType**， **NotificationPort**，和**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-163">Optionally, you can specify values for the **InboundOperationType**, **NotificationPort**, and **NotificationStatement** binding properties.</span></span>  
  
2.  <span data-ttu-id="1cada-164">從 Oracle 資料庫接收通知的 BizTalk 專案中建立訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-164">Create a message in the BizTalk project for receiving notification from the Oracle database.</span></span>  
  
3.  <span data-ttu-id="1cada-165">上一節中所述，建立協調流程。</span><span class="sxs-lookup"><span data-stu-id="1cada-165">Create an orchestration as described in the preceding section.</span></span>  
  
4.  <span data-ttu-id="1cada-166">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1cada-166">Build and deploy the BizTalk project.</span></span>  
  
5.  <span data-ttu-id="1cada-167">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="1cada-167">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1cada-168">輸入的作業，像是接收通知訊息，您必須只設定單向的 WCF 自訂或 Wcf-oracledb 接收埠。</span><span class="sxs-lookup"><span data-stu-id="1cada-168">For inbound operations, like receiving notification messages, you must only configure a one-way WCF-Custom or WCF-OracleDB receive port.</span></span> <span data-ttu-id="1cada-169">雙向接收埠不支援的輸入操作。</span><span class="sxs-lookup"><span data-stu-id="1cada-169">Two-way receive ports are not supported for inbound operations.</span></span>  
  
6.  <span data-ttu-id="1cada-170">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1cada-170">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="1cada-171">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="1cada-171">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="1cada-172">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="1cada-172">Generating Schema</span></span>  
 <span data-ttu-id="1cada-173">您必須產生的結構描述**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-173">You must generate the schema for the **Notification** inbound operation.</span></span> <span data-ttu-id="1cada-174">請參閱[擷取 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="1cada-174">See [Retrieve metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) for more information about how to generate the schema.</span></span> <span data-ttu-id="1cada-175">產生結構描述時，請執行下列工作。</span><span class="sxs-lookup"><span data-stu-id="1cada-175">Perform the following tasks when generating the schema.</span></span> <span data-ttu-id="1cada-176">如果您不要指定繫結屬性在設計階段，請略過第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="1cada-176">Skip the first step if you do not want to specify the binding properties at design-time.</span></span>  
  
1.  <span data-ttu-id="1cada-177">指定的值**InboundOperationType**， **NotificationPort**，和**NotificationStatement**時產生結構描述繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-177">Specify a value for **InboundOperationType**, **NotificationPort**, and **NotificationStatement** binding properties while generating the schema.</span></span> <span data-ttu-id="1cada-178">如需此繫結屬性的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1cada-178">For more information about this binding property, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span> <span data-ttu-id="1cada-179">如需有關如何指定繫結屬性的指示，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-179">For instructions on how to specify binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span>  
  
2.  <span data-ttu-id="1cada-180">選取合約類型為**服務 （輸入操作）**。</span><span class="sxs-lookup"><span data-stu-id="1cada-180">Select the contract type as **Service (Inbound operations)**.</span></span>  
  
3.  <span data-ttu-id="1cada-181">產生結構描述的**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-181">Generate schema for the **Notification** operation.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="1cada-182">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="1cada-182">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="1cada-183">您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-183">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="1cada-184">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="1cada-184">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="1cada-185">一旦產生結構描述時，您必須訊息連結之協調流程檢視中的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1cada-185">Once the schema is generated, you must link it to the messages from the Orchestration view of the BizTalk project.</span></span>  
  
 <span data-ttu-id="1cada-186">本主題中，您必須建立一個要從 Oracle 資料庫接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-186">For this topic, you must create one message to receive notifications from the Oracle database.</span></span>  
  
 <span data-ttu-id="1cada-187">執行下列步驟來建立訊息，並將它們連結至結構描述。</span><span class="sxs-lookup"><span data-stu-id="1cada-187">Perform the following steps to create messages and link them to schema.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="1cada-188">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="1cada-188">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="1cada-189">BizTalk 專案中新增協調流程。</span><span class="sxs-lookup"><span data-stu-id="1cada-189">Add an orchestration to the BizTalk project.</span></span> <span data-ttu-id="1cada-190">從 方案總管 中，以滑鼠右鍵按一下 BizTalk 專案名稱，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="1cada-190">From the Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="1cada-191">輸入 BizTalk 協調流程的名稱，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="1cada-191">Type a name for the BizTalk orchestration and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="1cada-192">如果它尚未開啟，請開啟 BizTalk 專案中，[協調流程檢視] 視窗。</span><span class="sxs-lookup"><span data-stu-id="1cada-192">Open the orchestration view window of the BizTalk project, if it is not already open.</span></span> <span data-ttu-id="1cada-193">按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="1cada-193">Click **View**, point to **Other Windows**, and then click **Orchestration View**.</span></span>  
  
3.  <span data-ttu-id="1cada-194">在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="1cada-194">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
4.  <span data-ttu-id="1cada-195">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="1cada-195">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="1cada-196">在**屬性**窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1cada-196">In the **Properties** pane for **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="1cada-197">使用</span><span class="sxs-lookup"><span data-stu-id="1cada-197">Use this</span></span>|<span data-ttu-id="1cada-198">動作</span><span class="sxs-lookup"><span data-stu-id="1cada-198">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1cada-199">識別碼</span><span class="sxs-lookup"><span data-stu-id="1cada-199">Identifier</span></span>|<span data-ttu-id="1cada-200">輸入 `NotifyReceive`。</span><span class="sxs-lookup"><span data-stu-id="1cada-200">Type `NotifyReceive`.</span></span>|  
    |<span data-ttu-id="1cada-201">訊息類型</span><span class="sxs-lookup"><span data-stu-id="1cada-201">Message Type</span></span>|<span data-ttu-id="1cada-202">從下拉式清單中，展開 **結構描述**，然後選取*Process_Notification.OracleDBBinding.Notification*，其中*Process_Notification*名稱您BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="1cada-202">From the drop-down list, expand **Schemas**, and select *Process_Notification.OracleDBBinding.Notification*, where *Process_Notification* is the name of your BizTalk project.</span></span> <span data-ttu-id="1cada-203">*OracleDBBinding*是針對產生的結構描述**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-203">*OracleDBBinding* is the schema generated for the **Notification** operation.</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="1cada-204">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="1cada-204">Setting up the Orchestration</span></span>  
 <span data-ttu-id="1cada-205">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 Oracle 資料庫接收通知訊息，然後執行根據收到的通知類型的工作。</span><span class="sxs-lookup"><span data-stu-id="1cada-205">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for receiving notification messages from the Oracle database and then performing tasks based on the type of notification received.</span></span> <span data-ttu-id="1cada-206">在此協調流程中，配接器接收通知訊息，根據指定的 SELECT 陳述式**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-206">In this orchestration, the adapter receives the notification message based on the SELECT statement specified for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="1cada-207">「 運算式 」 圖形中指定的 xpath 查詢則會擷取類型的通知放入變數中，假設**notificationtype 而**。</span><span class="sxs-lookup"><span data-stu-id="1cada-207">The xpath query specified within the Expression shape extracts the type of notification into a variable, say **NotificationType**.</span></span> <span data-ttu-id="1cada-208">「 決定 」 圖形在此變數會使用值來決定的收到的通知類型，並採用適當"path"以執行後續的作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-208">The Decide shape uses the value in this variable to decide on the kind of notification received and takes the appropriate “path” to perform subsequent operations.</span></span> <span data-ttu-id="1cada-209">如前一節所述，協調流程將執行下列作業根據接收通知訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1cada-209">As mentioned in the preceding section, the orchestration will perform the following operations based on the kind of notification message received.</span></span>  
  
-   <span data-ttu-id="1cada-210">如果 Insert 或 Update 作業的通知訊息，配接器用戶端會將訊息複製 C:\TestLocation\UpsertNotification 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1cada-210">If the notification message is for an Insert or Update operation, the adapter client copies the message to C:\TestLocation\UpsertNotification folder.</span></span>  
  
-   <span data-ttu-id="1cada-211">如果通知訊息的任何其他作業，例如刪除，配接器用戶端會將訊息複製到 C:\TestLocation\OtherNotificaiton 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1cada-211">If the notification message is for any other operation, for example Delete, the adapter client copies the message to C:\TestLocation\OtherNotificaiton folder.</span></span>  
  
 <span data-ttu-id="1cada-212">因此，您的協調流程必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="1cada-212">So, your orchestration must contain the following:</span></span>  
  
-   <span data-ttu-id="1cada-213">單向接收埠以接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-213">A one-way receive port to receive notification messages.</span></span>  
  
-   <span data-ttu-id="1cada-214">「 運算式 」 圖形，其中包含 xpath 查詢來擷取的收到的通知類型。</span><span class="sxs-lookup"><span data-stu-id="1cada-214">An Expression shape that contains an xpath query to extract the kind of notification received.</span></span>  
  
-   <span data-ttu-id="1cada-215">在協調流程中包含決策區塊 「 決定 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="1cada-215">A Decide shape to include a decision block in the orchestration.</span></span> <span data-ttu-id="1cada-216">在此決策區塊中，應用程式決定要執行的後續作業基礎收到的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-216">In this decision block, the application decides on what subsequent operations to perform based on the notification message received.</span></span>  
  
-   <span data-ttu-id="1cada-217">兩個單向傳送埠，最後接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-217">Two one-way send ports that finally receive the notification messages.</span></span>  
  
-   <span data-ttu-id="1cada-218">接收圖形。</span><span class="sxs-lookup"><span data-stu-id="1cada-218">Receive shape.</span></span>  
  
 <span data-ttu-id="1cada-219">範例協調流程如下。</span><span class="sxs-lookup"><span data-stu-id="1cada-219">A sample orchestration resembles the following.</span></span>  
  
 <span data-ttu-id="1cada-220">![協調流程執行 post &#45; 通知工作](../../adapters-and-accelerators/adapter-oracle-database/media/40c637ea-dbec-47a8-b53b-58d6820093b4.gif "40c637ea-dbec-47a8-b53b-58d6820093b4")</span><span class="sxs-lookup"><span data-stu-id="1cada-220">![Orchestration to perform post&#45;notification task](../../adapters-and-accelerators/adapter-oracle-database/media/40c637ea-dbec-47a8-b53b-58d6820093b4.gif "40c637ea-dbec-47a8-b53b-58d6820093b4")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="1cada-221">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="1cada-221">Adding Message Shapes</span></span>  
 <span data-ttu-id="1cada-222">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-222">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="1cada-223">圖形資料行中所列的名稱是訊息 圖形的名稱，為顯示在剛才提及的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="1cada-223">The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.</span></span>  
  
|<span data-ttu-id="1cada-224">形狀圖</span><span class="sxs-lookup"><span data-stu-id="1cada-224">Shape</span></span>|<span data-ttu-id="1cada-225">圖形類型</span><span class="sxs-lookup"><span data-stu-id="1cada-225">Shape Type</span></span>|<span data-ttu-id="1cada-226">屬性</span><span class="sxs-lookup"><span data-stu-id="1cada-226">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="1cada-227">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="1cada-227">ReceiveNotification</span></span>|<span data-ttu-id="1cada-228">Receive</span><span class="sxs-lookup"><span data-stu-id="1cada-228">Receive</span></span>|<span data-ttu-id="1cada-229">-設定**名稱**至*ReceiveNotification*</span><span class="sxs-lookup"><span data-stu-id="1cada-229">- Set **Name** to *ReceiveNotification*</span></span><br /><br /> <span data-ttu-id="1cada-230">-設定**啟動**至*，則為 True*</span><span class="sxs-lookup"><span data-stu-id="1cada-230">- Set **Activate** to *True*</span></span>|  
  
### <a name="adding-an-expression-shape"></a><span data-ttu-id="1cada-231">新增 「 運算式 」 圖形</span><span class="sxs-lookup"><span data-stu-id="1cada-231">Adding an Expression Shape</span></span>  
 <span data-ttu-id="1cada-232">協調流程中包括 「 運算式 」 圖形的用途是將 xpath 查詢來擷取收到的通知訊息的類型。</span><span class="sxs-lookup"><span data-stu-id="1cada-232">The purpose of including an Expression shape in the orchestration is to have an xpath query to extract the kind of notification message received.</span></span> <span data-ttu-id="1cada-233">在之前建立 xpath 查詢，讓我們看看通知訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="1cada-233">Before creating an xpath query, let us look at the format of a notification message.</span></span> <span data-ttu-id="1cada-234">典型的通知訊息如下所示：</span><span class="sxs-lookup"><span data-stu-id="1cada-234">A typical notification message resembles the following:</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
  <Details>  
    <NotificationDetails>  
      <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
      <Info>1</Info>   
      <QueryId>0</QueryId>   
    </NotificationDetails>  
  </Details>  
  <Info>Insert</Info>   
  <ResourceNames>  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
  </ResourceNames>  
  <Source>Data</Source>   
  <Type>Change</Type>   
</Notification>  
```  
  
 <span data-ttu-id="1cada-235">您看到的通知類型的相關資訊可內`<info>`標記，在父系`<Notification>`標記。</span><span class="sxs-lookup"><span data-stu-id="1cada-235">As you see, the information about the type of the notification is available within the `<info>` tag, within the parent `<Notification>` tag.</span></span> <span data-ttu-id="1cada-236">因此，在此運算式圖形，您必須：</span><span class="sxs-lookup"><span data-stu-id="1cada-236">So, as part of this expression shape you must:</span></span>  
  
-   <span data-ttu-id="1cada-237">建立包含內值的變數，`<Info>`標記，並將其類型設為 System.String。</span><span class="sxs-lookup"><span data-stu-id="1cada-237">Create a variable that contains the value within the `<Info>` tag and set its type to System.String.</span></span> <span data-ttu-id="1cada-238">如需有關如何建立變數的詳細資訊，請參閱[在協調流程中使用變數](../../core/using-variables-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-238">For more information about creating variables, see [Using Variables in Orchestrations](../../core/using-variables-in-orchestrations.md).</span></span>  
  
     <span data-ttu-id="1cada-239">本主題中，命名為變數**notificationtype 而**。</span><span class="sxs-lookup"><span data-stu-id="1cada-239">For this topic, name the variable as **NotificationType**.</span></span>  
  
-   <span data-ttu-id="1cada-240">建立 xpath 查詢來擷取的值從\<資訊 > 標記。</span><span class="sxs-lookup"><span data-stu-id="1cada-240">Create an xpath query to extract the value from the \<Info> tag.</span></span> <span data-ttu-id="1cada-241">Xpath 查詢會如下所示：</span><span class="sxs-lookup"><span data-stu-id="1cada-241">The xpath query will resemble the following:</span></span>  
  
    ```  
    NotificationType = xpath(NotifyReceive,"string(/*[local-name()='Notification']/*[local-name()='Info']/text())");  
    ```  
  
     <span data-ttu-id="1cada-242">在此 xpath 查詢， **NotifyReceive**是您建立來接收通知訊息的訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-242">In this xpath query, **NotifyReceive** is the message you created for receiving notification messages.</span></span> <span data-ttu-id="1cada-243">內摘錄`string`函式表示的查詢必須解壓縮內的值`<Info>`標記，這又是內`<Notification>`標記。</span><span class="sxs-lookup"><span data-stu-id="1cada-243">The excerpt within the `string` function indicates that the query must extract the value within the `<Info>` tag, which in turn is within the `<Notification>` tag.</span></span> <span data-ttu-id="1cada-244">最後，將查詢所擷取的值指派給**NotificaitonType**變數。</span><span class="sxs-lookup"><span data-stu-id="1cada-244">Finally, the value extracted by the query is assigned to the **NotificaitonType** variable.</span></span>  
  
### <a name="adding-a-decide-shape"></a><span data-ttu-id="1cada-245">新增 「 決定 」 圖形</span><span class="sxs-lookup"><span data-stu-id="1cada-245">Adding a Decide Shape</span></span>  
 <span data-ttu-id="1cada-246">新增 「 決定 」 圖形的目的是要在協調流程以決定要執行的後續作業基礎接收通知訊息類型中包含決策區塊。</span><span class="sxs-lookup"><span data-stu-id="1cada-246">The purpose of adding a Decide shape is to include a decision block in the orchestration to decide what subsequent operations to perform based on the kind of notification message received.</span></span> <span data-ttu-id="1cada-247">根據的值所決定**notificationtype 而**變數。</span><span class="sxs-lookup"><span data-stu-id="1cada-247">The decision is made on the basis of the value of the **NotificationType** variable.</span></span> <span data-ttu-id="1cada-248">本主題中，協調流程會根據接收通知訊息類型決定。</span><span class="sxs-lookup"><span data-stu-id="1cada-248">In this topic, the orchestration makes a decision based on the kind of notification message received.</span></span> <span data-ttu-id="1cada-249">因此，「 規則 」 圖形中的條件的指定方式如下：</span><span class="sxs-lookup"><span data-stu-id="1cada-249">So, the condition in the Rule shape is specified as follows:</span></span>  
  
```  
NotificationType.Equals("Insert") | NotificationType.Equals("Update")  
```  
  
 <span data-ttu-id="1cada-250">此條件所示，如果值**NotificaitonType**變數是 Insert 或 Update，協調流程會執行一組工作。</span><span class="sxs-lookup"><span data-stu-id="1cada-250">This condition suggests that if the value for **NotificaitonType** variable is Insert or Update, the orchestration will perform one set of tasks.</span></span> <span data-ttu-id="1cada-251">如果值**notificationtype 而**變數可以是任何其他項目，協調流程會執行其他的工作集。</span><span class="sxs-lookup"><span data-stu-id="1cada-251">If the value of **NotificationType** variable is anything else, the orchestration will perform other set of tasks.</span></span>  
  
 <span data-ttu-id="1cada-252">如之前章節中所述，示範以簡單的方法，協調流程會將訊息複製到不同的資料夾，根據通知訊息類型。</span><span class="sxs-lookup"><span data-stu-id="1cada-252">As mentioned in the preceding sections, to demonstrate a simple approach, the orchestration will copy messages to different folders based on the notification message type.</span></span> <span data-ttu-id="1cada-253">因此，規則內和 Else 區塊，您必須新增傳送圖形，將訊息傳送至不同的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="1cada-253">So, within the Rule and Else blocks, you must add Send shapes to send the messages to different ports.</span></span> <span data-ttu-id="1cada-254">本主題中，命名為 「 傳送 」 圖形中的規則區塊**SendUpsertNotification**和在 Else 區塊中的 「 傳送 」 圖形**SendOtherNotification**。</span><span class="sxs-lookup"><span data-stu-id="1cada-254">For this topic, name the Send shape in the Rule block as **SendUpsertNotification** and the Send shape in the Else block as **SendOtherNotification**.</span></span>  
  
### <a name="adding-ports"></a><span data-ttu-id="1cada-255">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="1cada-255">Adding Ports</span></span>  
 <span data-ttu-id="1cada-256">您必須加入下列的邏輯連接埠至協調流程：</span><span class="sxs-lookup"><span data-stu-id="1cada-256">You must now add the following logical ports to the orchestration:</span></span>  
  
-   <span data-ttu-id="1cada-257">單向接收埠以接收通知訊息從 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1cada-257">One-way receive port to receive notification messages from the Oracle database.</span></span>  
  
-   <span data-ttu-id="1cada-258">單向傳送埠來傳送的 Insert 和 Update 作業的通知訊息給特定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1cada-258">One-way send port to send notification messages for Insert and Update operations to a specific folder.</span></span>  
  
-   <span data-ttu-id="1cada-259">單向傳送埠來傳送通知訊息的任何其他作業特定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1cada-259">One-way send port to send notification messages for any other operations to a specific folder.</span></span>  
  
 <span data-ttu-id="1cada-260">請確定您針對每個邏輯連接埠指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-260">Make sure you specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="1cada-261">連接埠資料行中所列的名稱是連接埠的名稱，為顯示協調流程中。</span><span class="sxs-lookup"><span data-stu-id="1cada-261">The names listed in the Port column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="1cada-262">通訊埠</span><span class="sxs-lookup"><span data-stu-id="1cada-262">Port</span></span>|<span data-ttu-id="1cada-263">屬性</span><span class="sxs-lookup"><span data-stu-id="1cada-263">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="1cada-264">OracleNotifyPort</span><span class="sxs-lookup"><span data-stu-id="1cada-264">OracleNotifyPort</span></span>|<span data-ttu-id="1cada-265">-設定**識別碼**至*OracleNotifyPort*</span><span class="sxs-lookup"><span data-stu-id="1cada-265">- Set **Identifier** to *OracleNotifyPort*</span></span><br /><br /> <span data-ttu-id="1cada-266">-設定**類型**至*OracleNotifyPortType*</span><span class="sxs-lookup"><span data-stu-id="1cada-266">- Set **Type** to *OracleNotifyPortType*</span></span><br /><br /> <span data-ttu-id="1cada-267">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="1cada-267">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="1cada-268">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="1cada-268">- Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="1cada-269">NotificationUpsertPort</span><span class="sxs-lookup"><span data-stu-id="1cada-269">NotificationUpsertPort</span></span>|<span data-ttu-id="1cada-270">-設定**識別碼**至*NotificationUpsertPort*</span><span class="sxs-lookup"><span data-stu-id="1cada-270">- Set **Identifier** to *NotificationUpsertPort*</span></span><br /><br /> <span data-ttu-id="1cada-271">-設定**類型**至*NotificationUpsertPortType*</span><span class="sxs-lookup"><span data-stu-id="1cada-271">- Set **Type** to *NotificationUpsertPortType*</span></span><br /><br /> <span data-ttu-id="1cada-272">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="1cada-272">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="1cada-273">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="1cada-273">- Set **Communication Direction** to *Send*</span></span>|  
|<span data-ttu-id="1cada-274">OtherNotificationPort</span><span class="sxs-lookup"><span data-stu-id="1cada-274">OtherNotificationPort</span></span>|<span data-ttu-id="1cada-275">-設定**識別碼**至*OtherNotificationPort*</span><span class="sxs-lookup"><span data-stu-id="1cada-275">- Set **Identifier** to *OtherNotificationPort*</span></span><br /><br /> <span data-ttu-id="1cada-276">-設定**類型**至*OtherNotificationPortType*</span><span class="sxs-lookup"><span data-stu-id="1cada-276">- Set **Type** to *OtherNotificationPortType*</span></span><br /><br /> <span data-ttu-id="1cada-277">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="1cada-277">- Set **Communication Pattern** to *One-Way*</span></span><br /><br /> <span data-ttu-id="1cada-278">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="1cada-278">- Set **Communication Direction** to *Send*</span></span>|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a><span data-ttu-id="1cada-279">指定動作圖形訊息並連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="1cada-279">Specify Messages for Action Shapes and Connect to Ports</span></span>  
 <span data-ttu-id="1cada-280">下表指定屬性和其值，您應該設定來指定動作圖形的訊息，以及連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-280">The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports.</span></span> <span data-ttu-id="1cada-281">圖形資料行中所列的名稱是 「 訊息 」 圖形的名稱，為顯示在協調流程中先前所述。</span><span class="sxs-lookup"><span data-stu-id="1cada-281">The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.</span></span>  
  
|<span data-ttu-id="1cada-282">形狀圖</span><span class="sxs-lookup"><span data-stu-id="1cada-282">Shape</span></span>|<span data-ttu-id="1cada-283">屬性</span><span class="sxs-lookup"><span data-stu-id="1cada-283">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="1cada-284">ReceiveNotification</span><span class="sxs-lookup"><span data-stu-id="1cada-284">ReceiveNotification</span></span>|<span data-ttu-id="1cada-285">-設定**訊息**至*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="1cada-285">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="1cada-286">-設定**作業**至*OracleNotifyPort.Notify.Request*</span><span class="sxs-lookup"><span data-stu-id="1cada-286">- Set **Operation** to *OracleNotifyPort.Notify.Request*</span></span>|  
|<span data-ttu-id="1cada-287">SendUpsertNotification</span><span class="sxs-lookup"><span data-stu-id="1cada-287">SendUpsertNotification</span></span>|<span data-ttu-id="1cada-288">-設定**訊息**至*NotifyReceive*</span><span class="sxs-lookup"><span data-stu-id="1cada-288">- Set **Message** to *NotifyReceive*</span></span><br /><br /> <span data-ttu-id="1cada-289">-設定**作業**至*NotificationUpsertPort.Upsert.Request*</span><span class="sxs-lookup"><span data-stu-id="1cada-289">- Set **Operation** to *NotificationUpsertPort.Upsert.Request*</span></span>|  
|<span data-ttu-id="1cada-290">SendOtherNotification</span><span class="sxs-lookup"><span data-stu-id="1cada-290">SendOtherNotification</span></span>|<span data-ttu-id="1cada-291">-設定**訊息**至*選取*</span><span class="sxs-lookup"><span data-stu-id="1cada-291">- Set **Message** to *Select*</span></span><br /><br /> <span data-ttu-id="1cada-292">-設定**作業**至*OtherNotificationPort.Other.Request*</span><span class="sxs-lookup"><span data-stu-id="1cada-292">- Set **Operation** to *OtherNotificationPort.Other.Request*</span></span>|  
  
 <span data-ttu-id="1cada-293">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="1cada-293">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="1cada-294">您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1cada-294">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="1cada-295">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-295">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>  
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="1cada-296">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="1cada-296">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="1cada-297">部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**窗格[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1cada-297">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="1cada-298">您必須使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="1cada-298">You must use the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the application.</span></span> <span data-ttu-id="1cada-299">如需逐步解說，請參閱[逐步解說： 部署基本 BizTalk 應用程式](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-299">For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).</span></span>
  
 <span data-ttu-id="1cada-300">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="1cada-300">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="1cada-301">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="1cada-301">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="1cada-302">對應至實體連接埠在協調流程中建立的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1cada-302">Mapping the ports that you created in your orchestration to physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="1cada-303">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="1cada-303">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="1cada-304">定義實體的 WCF 自訂或 Wcf-oracledb 單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="1cada-304">Define a physical WCF-Custom or WCF-OracleDB one-way receive port.</span></span> <span data-ttu-id="1cada-305">此連接埠會接聽來自 Oracle 資料庫的通知。</span><span class="sxs-lookup"><span data-stu-id="1cada-305">This port listens for notifications coming from the Oracle database.</span></span> <span data-ttu-id="1cada-306">如需如何建立接收埠，請參閱[手動設定 Oracle 資料庫配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-306">For information about how to create receive ports, see [Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).</span></span> <span data-ttu-id="1cada-307">請確定指定接收埠的下列繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-307">Make sure you specify the following binding properties for the receive port.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="1cada-308">您不需要執行這個步驟，如果您指定在設計階段的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1cada-308">You do not need to perform this step if you specified the binding properties at design-time.</span></span> <span data-ttu-id="1cada-309">在此情況下，您可以建立 wcf-custom 或 Wcf-oracledb 接收埠，設定必要的繫結屬性，藉由匯入所建立之繫結檔案[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1cada-309">In such a case, you can create a WCF-custom or WCF-OracleDB receive port, with the required binding properties set, by importing the binding file created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="1cada-310">如需詳細資訊，請參閱 < 設定實體連接埠繫結使用連接埠繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="1cada-310">For more information, see Configuring a Physical Port Binding Using a Port Binding File.</span></span>  
  
        |<span data-ttu-id="1cada-311">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="1cada-311">Binding Property</span></span>|<span data-ttu-id="1cada-312">值</span><span class="sxs-lookup"><span data-stu-id="1cada-312">Value</span></span>|  
        |----------------------|-----------|  
        |<span data-ttu-id="1cada-313">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="1cada-313">**InboundOperationType**</span></span>|<span data-ttu-id="1cada-314">將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="1cada-314">Set this to **Notification**.</span></span>|  
        |<span data-ttu-id="1cada-315">**NotificationPort**</span><span class="sxs-lookup"><span data-stu-id="1cada-315">**NotificationPort**</span></span>|<span data-ttu-id="1cada-316">指定 ODP.NET 必須開啟從 Oracle 資料庫的資料庫變更通知所接聽的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="1cada-316">Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.</span></span> <span data-ttu-id="1cada-317">設定為相同的連接埠號碼，您必須已加入 Windows 防火牆例外清單。</span><span class="sxs-lookup"><span data-stu-id="1cada-317">Set this to the same port number that you must have added to the Windows Firewall exceptions list.</span></span> <span data-ttu-id="1cada-318">如需如何將連接埠新增至 Windows 防火牆例外清單的指示，請參閱[http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959)。</span><span class="sxs-lookup"><span data-stu-id="1cada-318">For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).</span></span><br /><br /> <span data-ttu-id="1cada-319">**重要事項：**如果您設定為預設值-1，您必須完全停用 Windows 防火牆來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-319">**Important:** If you set this to the default value of -1, you will have to completely disable Windows Firewall to receive notification messages.</span></span>|  
        |<span data-ttu-id="1cada-320">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="1cada-320">**NotificationStatement**</span></span>|<span data-ttu-id="1cada-321">將此值設定為：</span><span class="sxs-lookup"><span data-stu-id="1cada-321">Set this to:</span></span><br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’`<br /><br /> <span data-ttu-id="1cada-322">**注意：**您必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="1cada-322">**Note:** You must specify the table name along with the schema name.</span></span> <span data-ttu-id="1cada-323">例如， `SCOTT.ACCOUNTACTIVITY`。</span><span class="sxs-lookup"><span data-stu-id="1cada-323">For example, `SCOTT.ACCOUNTACTIVITY`.</span></span>|  
        |<span data-ttu-id="1cada-324">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="1cada-324">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="1cada-325">將此設**True**。</span><span class="sxs-lookup"><span data-stu-id="1cada-325">Set this to **True**.</span></span>|  
  
         <span data-ttu-id="1cada-326">如需不同的繫結屬性的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1cada-326">For more information about the different binding properties, see [Working with binding properties](https://msdn.microsoft.com/library/dd788467.aspx).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="1cada-327">我們建議您執行使用的輸入的操作時設定的交易隔離等級和異動逾時[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1cada-327">We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="1cada-328">您可以藉由新增服務行為設定 Wcf-custom 或 Wcf-oracledb 時收到這些連接埠。</span><span class="sxs-lookup"><span data-stu-id="1cada-328">You can do so by adding the service behavior while configuring the WCF-Custom or WCF-OracleDB receive port.</span></span> <span data-ttu-id="1cada-329">如需如何新增服務行為的指示，請參閱[設定交易隔離等級和交易逾時與 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-329">For instruction on how to add the service behavior, see [Configure Transaction Isolation Level and Transaction Timeout with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md).</span></span>  
  
    -   <span data-ttu-id="1cada-330">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置，通知訊息從 Oracle 資料庫的 Insert 和 Update 作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-330">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the notification messages from the Oracle database for Insert and Update operations.</span></span> <span data-ttu-id="1cada-331">設定此連接埠來卸除資料夾 C:\TestLocation\UpsertNotification 的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-331">Configure this port to drop notification messages to the folder C:\TestLocation\UpsertNotification.</span></span>  
  
    -   <span data-ttu-id="1cada-332">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程會放置的位置，通知訊息從 Oracle 資料庫中針對所有其他作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-332">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the notification messages from the Oracle database for all other operations.</span></span> <span data-ttu-id="1cada-333">設定此連接埠來卸除資料夾 C:\TestLocation\OtherNotification 的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-333">Configure this port to drop notification messages to the folder C:\TestLocation\OtherNotification.</span></span>  
  
## <a name="starting-the-application"></a><span data-ttu-id="1cada-334">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="1cada-334">Starting the Application</span></span>  
 <span data-ttu-id="1cada-335">您必須啟動 BizTalk 應用程式接收通知訊息從 Oracle 資料庫以及執行後續的 Select 和 Update 作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-335">You must start the BizTalk application for receiving notification messages from the Oracle database and for performing the subsequent Select and Update operations.</span></span> <span data-ttu-id="1cada-336">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-336">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="1cada-337">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="1cada-337">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="1cada-338">Wcf-custom 或 Wcf-oracledb 單向接收埠，會從 Oracle 資料庫執行時接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1cada-338">The WCF-Custom or WCF-OracleDB one-way receive port, which receives the notification messages from the Oracle database is running.</span></span>  
  
-   <span data-ttu-id="1cada-339">兩個的檔案傳送埠，從 Oracle 資料庫接收訊息，正在執行。</span><span class="sxs-lookup"><span data-stu-id="1cada-339">The two FILE send ports, which receive messages from Oracle database, are running.</span></span>  
  
-   <span data-ttu-id="1cada-340">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="1cada-340">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="1cada-341">執行作業</span><span class="sxs-lookup"><span data-stu-id="1cada-341">Executing the Operation</span></span>  
 <span data-ttu-id="1cada-342">啟動 BizTalk 協調流程之後，下列的動作集合就會發生：</span><span class="sxs-lookup"><span data-stu-id="1cada-342">After you start the BizTalk orchestration, the following set of actions take place:</span></span>  
  
-   <span data-ttu-id="1cada-343">因為**NotifyOnListenerStart**繫結屬性設定為**True**，您會收到下列訊息：</span><span class="sxs-lookup"><span data-stu-id="1cada-343">Because the **NotifyOnListenerStart** binding property is set to **True**, you receive the following message:</span></span>  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
      <Info>ListenerStarted</Info>   
      <Source>OracleDBBinding</Source>   
      <Type>Startup</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="1cada-344">請注意，中的值`<Info>`標記為 「 ListnerStarted"。</span><span class="sxs-lookup"><span data-stu-id="1cada-344">Note that the value in the `<Info>` tag is “ListnerStarted”.</span></span> <span data-ttu-id="1cada-345">因此，會收到此訊息 C:\TestLocation\OtherNotification 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1cada-345">Hence, this message is received in C:\TestLocation\OtherNotification folder.</span></span>  
  
-   <span data-ttu-id="1cada-346">ACCOUNTACTIVITY 資料表中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="1cada-346">Insert a record in the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="1cada-347">您會收到通知訊息，如下列所示：</span><span class="sxs-lookup"><span data-stu-id="1cada-347">You will receive a notification message resembling the following:</span></span>  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
      <Details>  
        <NotificationDetails>  
          <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
          <Info>1</Info>   
          <QueryId>0</QueryId>   
        </NotificationDetails>  
      </Details>  
      <Info>Insert</Info>   
      <ResourceNames>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
      </ResourceNames>  
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="1cada-348">請注意，中的值`<Info>`標記為 「 插入 」。</span><span class="sxs-lookup"><span data-stu-id="1cada-348">Note that the value in the `<Info>` tag is “Insert”.</span></span> <span data-ttu-id="1cada-349">因此，會收到此訊息 C:\TestLocation\UpsertNotification 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1cada-349">Hence, this message is received in C:\TestLocation\UpsertNotification folder.</span></span>  
  
-   <span data-ttu-id="1cada-350">更新 ACCOUNTACTIVITY 資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="1cada-350">Update a record in the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="1cada-351">您會收到通知訊息，如下列所示：</span><span class="sxs-lookup"><span data-stu-id="1cada-351">You will receive a notification message resembling the following:</span></span>  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
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
  
     <span data-ttu-id="1cada-352">請注意，中的值`<Info>`標記為 「 更新 」。</span><span class="sxs-lookup"><span data-stu-id="1cada-352">Note that the value in the `<Info>` tag is “Update”.</span></span> <span data-ttu-id="1cada-353">因此，會收到此訊息 C:\TestLocation\UpsertNotification 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1cada-353">Hence, this message is received in C:\TestLocation\UpsertNotification folder.</span></span>  
  
-   <span data-ttu-id="1cada-354">從 ACCOUNTACTIVITY 資料表刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="1cada-354">Delete a record from the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="1cada-355">您會收到通知訊息，如下列所示：</span><span class="sxs-lookup"><span data-stu-id="1cada-355">You will receive a notification message resembling the following:</span></span>  
  
    ```  
    \<?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
      <Details>  
        <NotificationDetails>  
          <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
          <Info>16</Info>   
          <QueryId>0</QueryId>   
        </NotificationDetails>  
      </Details>  
      <Info>Delete</Info>   
      <ResourceNames>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
      </ResourceNames>  
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     <span data-ttu-id="1cada-356">請注意，中的值`<Info>`標記為 「 刪除 」。</span><span class="sxs-lookup"><span data-stu-id="1cada-356">Note that the value in the `<Info>` tag is “Delete”.</span></span> <span data-ttu-id="1cada-357">因此，會收到此訊息 C:\TestLocation\OtherNotification 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1cada-357">Hence, this message is received in C:\TestLocation\OtherNotification folder.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="1cada-358">最佳作法</span><span class="sxs-lookup"><span data-stu-id="1cada-358">Best Practices</span></span>  
 <span data-ttu-id="1cada-359">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="1cada-359">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file.</span></span> <span data-ttu-id="1cada-360">一旦產生繫結檔案時，可以組態設定匯入檔案，使您不需要建立傳送埠和接收相同的協調流程連接埠。</span><span class="sxs-lookup"><span data-stu-id="1cada-360">Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create the send ports and receive ports for the same orchestration.</span></span> <span data-ttu-id="1cada-361">如需繫結檔案的詳細資訊，請參閱[重複使用的 Oracle 資料庫配接器繫結](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="1cada-361">For more information about binding files, see [Reuse Oracle Database Adapter bindings](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).</span></span>  
  
## <a name="performing-complex-operations-after-receiving-notification-messages"></a><span data-ttu-id="1cada-362">執行複雜的作業之後接收通知訊息</span><span class="sxs-lookup"><span data-stu-id="1cada-362">Performing Complex Operations After Receiving Notification Messages</span></span>  
 <span data-ttu-id="1cada-363">為了簡化和更佳了解，本主題中的協調流程會將訊息複製到不同的資料夾，根據通知類型。</span><span class="sxs-lookup"><span data-stu-id="1cada-363">For simplicity and better understanding, the orchestration in this topic copies messages to different folders based on the notification type.</span></span> <span data-ttu-id="1cada-364">不過，在真實世界案例中，您可能想要執行更複雜的作業。</span><span class="sxs-lookup"><span data-stu-id="1cada-364">However, in real-world scenarios you might want to perform more complex operations.</span></span> <span data-ttu-id="1cada-365">您可以執行類似的程序，如本主題和組建，以執行您希望的作業所提供。</span><span class="sxs-lookup"><span data-stu-id="1cada-365">You can perform similar procedures as provided in this topic and build on them to perform the operations you wish.</span></span> <span data-ttu-id="1cada-366">例如，您可以變更另一個資料表中插入記錄，如果您收到 ACCOUNTACTIVITY 資料表上插入作業的通知訊息的協調流程。</span><span class="sxs-lookup"><span data-stu-id="1cada-366">For example, you can change the orchestration to insert records in another table if you get a notification message for an Insert operation on the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="1cada-367">在這種情況下，您可以進行適當的變更，「 決定 」 圖形內。</span><span class="sxs-lookup"><span data-stu-id="1cada-367">In such a case, you can make appropriate changes within the Decide shape.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cada-368">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cada-368">See Also</span></span>  
 [<span data-ttu-id="1cada-369">使用 BizTalk Server 接收的 Oracle 資料庫變更通知</span><span class="sxs-lookup"><span data-stu-id="1cada-369">Receiving Oracle Database Change Notifications Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)