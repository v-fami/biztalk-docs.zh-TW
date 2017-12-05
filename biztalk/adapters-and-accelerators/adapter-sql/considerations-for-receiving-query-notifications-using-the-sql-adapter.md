---
title: "使用 SQL 配接器接收查詢通知的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0142f385-3d55-41a7-a50e-dda94b96d0a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02d7aa9eadc5e639e56cc526bfd5763abc432a4f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="considerations-for-receiving-query-notifications-using-the-sql-adapter"></a><span data-ttu-id="8431e-102">使用 SQL 配接器接收查詢通知的考量</span><span class="sxs-lookup"><span data-stu-id="8431e-102">Considerations for Receiving Query Notifications Using the SQL adapter</span></span>
<span data-ttu-id="8431e-103">本主題提供一些考量和最佳作法，以使用時請記住[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]要從 SQL Server 資料庫接收查詢通知。</span><span class="sxs-lookup"><span data-stu-id="8431e-103">This topic provides some considerations and best practices to keep in mind while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive query notifications from a SQL Server database.</span></span>  
  
## <a name="considerations-while-using-the-adapter-to-receive-notifications"></a><span data-ttu-id="8431e-104">使用配接器接收通知時的考量</span><span class="sxs-lookup"><span data-stu-id="8431e-104">Considerations While Using the Adapter to Receive Notifications</span></span>  
 <span data-ttu-id="8431e-105">您必須考慮下列使用時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收查詢通知：</span><span class="sxs-lookup"><span data-stu-id="8431e-105">You must consider the following while using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive query notifications:</span></span>  
  
-   <span data-ttu-id="8431e-106">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]收到來自 SQL Server 查詢通知，然後只是要傳送通知到配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="8431e-106">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] receives the query notification from SQL Server, and then simply passes on the notification to the adapter clients.</span></span> <span data-ttu-id="8431e-107">配接器不會區分不同的作業的通知 （亦即，配接器沒有任何資訊是否為插入作業或更新作業的特定通知）。</span><span class="sxs-lookup"><span data-stu-id="8431e-107">The adapter does not distinguish between the notifications for different operations (i.e., the adapter does not have any information whether a particular notification is for an Insert operation or an Update operation).</span></span>  
  
-   <span data-ttu-id="8431e-108">作業的通知訊息不會受到該作業所影響的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="8431e-108">The notification message for an operation is not affected by the number of records affected by that operation.</span></span> <span data-ttu-id="8431e-109">例如，插入、 更新或刪除 SQL Server 資料庫資料表中的記錄數目，不論配接器用戶端收到只有一個通知訊息。</span><span class="sxs-lookup"><span data-stu-id="8431e-109">For example, regardless of the number of records inserted, updated, or deleted in a SQL Server database table, the adapter client receives only one notification message.</span></span>  
  
-   <span data-ttu-id="8431e-110">我們建議配接器用戶端應用程式包含的邏輯來解譯收到來自 SQL Server 通知的類型。</span><span class="sxs-lookup"><span data-stu-id="8431e-110">We recommend that the adapter client application contain the logic to interpret the type of notification received from SQL Server.</span></span> <span data-ttu-id="8431e-111">通知類型可以決定所擷取的資訊，從**\<資訊\>**接收的通知訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="8431e-111">The notification type can be determined by extracting the information from, the **\<Info\>** element of the received notification message.</span></span> <span data-ttu-id="8431e-112">插入作業接收通知訊息的範例如下：</span><span class="sxs-lookup"><span data-stu-id="8431e-112">Here’s an example of a notification message received for an Insert operation:</span></span>  
  
    ```  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>  
      <Source>Data</Source>  
      <Type>Change</Type>  
    </Notification>  
    ```  
  
     <span data-ttu-id="8431e-113">請注意內的值**\<資訊\>**項目。</span><span class="sxs-lookup"><span data-stu-id="8431e-113">Notice the value within the **\<Info\>** element.</span></span> <span data-ttu-id="8431e-114">此值會提供資訊在收到通知訊息的作業。</span><span class="sxs-lookup"><span data-stu-id="8431e-114">This value provides information on the operation for which the notification message was received.</span></span> <span data-ttu-id="8431e-115">您的應用程式應該有的功能來擷取內的值**\<資訊\>**項目，然後根據的值，執行後續的工作。</span><span class="sxs-lookup"><span data-stu-id="8431e-115">Your application should have the functionality to extract the value within the **\<Info\>** element and then based on the value, perform subsequent tasks.</span></span> <span data-ttu-id="8431e-116">本主題[處理通知訊息，以便完成特定工作中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)如何擷取內的值中的指示**\<資訊\>**項目.</span><span class="sxs-lookup"><span data-stu-id="8431e-116">The topic [Process Notification Messages to complete Specific Tasks in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md) has instructions on how to extract the value within the **\<Info\>** element.</span></span> <span data-ttu-id="8431e-117">詳細的教學課程，執行類似的工作也會提供在[教學課程 2： 員工-訂單程序使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="8431e-117">A detailed tutorial that performs similar tasks is also available at [Tutorial 2: Employee - Purchase Order Process using the SQL adapter](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).</span></span>  
  
-   <span data-ttu-id="8431e-118">在理想情況下，用戶端應用程式會收到通知的特定記錄後，該記錄應該會更新，讓沒有收到其他通知。</span><span class="sxs-lookup"><span data-stu-id="8431e-118">Ideally, after the client application receives a notification for a specific record, that record should be updated so that additional notifications are not received.</span></span> <span data-ttu-id="8431e-119">例如，請考慮**員工**資料表具有**狀態**資料行。</span><span class="sxs-lookup"><span data-stu-id="8431e-119">For example, consider an **Employee** table that has a **Status** column.</span></span> <span data-ttu-id="8431e-120">針對所有新記錄插入至**員工**資料表中的值**狀態**資料行一律是"0"，資料表看起來像下面：</span><span class="sxs-lookup"><span data-stu-id="8431e-120">For all new records inserted into the **Employee** table, the value in the **Status** column is always “0” so the table will look like the following:</span></span>  
  
    |<span data-ttu-id="8431e-121">員工名稱</span><span class="sxs-lookup"><span data-stu-id="8431e-121">Employee Name</span></span>|<span data-ttu-id="8431e-122">狀態</span><span class="sxs-lookup"><span data-stu-id="8431e-122">Status</span></span>|  
    |-------------------|------------|  
    |<span data-ttu-id="8431e-123">John</span><span class="sxs-lookup"><span data-stu-id="8431e-123">John</span></span>|<span data-ttu-id="8431e-124">0</span><span class="sxs-lookup"><span data-stu-id="8431e-124">0</span></span>|  
  
     <span data-ttu-id="8431e-125">若要接收通知之新插入的記錄，設定配接器用戶端將**NotificatonStatement**繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="8431e-125">To receive notifications for the newly inserted record, the adapter client will set the **NotificatonStatement** binding property as:</span></span>  
  
    ```  
    SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8431e-126">具體來說，您必須指定資料行名稱中的陳述式中所示 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8431e-126">You must specifically specify the column names in the statement as shown in this SELECT statement.</span></span> <span data-ttu-id="8431e-127">此外，您永遠必須指定資料表名稱，以及結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="8431e-127">Also, you must always specify the table name along with the schema name.</span></span> <span data-ttu-id="8431e-128">例如，dbo。員工。</span><span class="sxs-lookup"><span data-stu-id="8431e-128">For example, dbo.Employee.</span></span>  
  
     <span data-ttu-id="8431e-129">在收到通知，用戶端應用程式必須重設的值**狀態**為"1"的資料行，以便通知陳述式不能進行資料錄一次。</span><span class="sxs-lookup"><span data-stu-id="8431e-129">After receiving the notification, the client application must reset the value of the **Status** column to “1” so that the notification statement does not operate on the record again.</span></span> <span data-ttu-id="8431e-130">若要達成此目的，用戶端應用程式必須在執行更新作業**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="8431e-130">To achieve this, the client application must perform an Update operation on the **Employee** table.</span></span> <span data-ttu-id="8431e-131">更新作業之後，相同記錄**員工**資料表看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="8431e-131">After the Update operation, the same record in the **Employee** table will look like the following:</span></span>  
  
    |<span data-ttu-id="8431e-132">員工名稱</span><span class="sxs-lookup"><span data-stu-id="8431e-132">Employee Name</span></span>|<span data-ttu-id="8431e-133">狀態</span><span class="sxs-lookup"><span data-stu-id="8431e-133">Status</span></span>|  
    |-------------------|------------|  
    |<span data-ttu-id="8431e-134">John</span><span class="sxs-lookup"><span data-stu-id="8431e-134">John</span></span>|<span data-ttu-id="8431e-135">1</span><span class="sxs-lookup"><span data-stu-id="8431e-135">1</span></span>|  
  
     <span data-ttu-id="8431e-136">有趣的是，更新作業將會再次傳送通知給配接器用戶端和整個程序會重複一次，因此，用戶端應用程式必須具備所需的邏輯，以捨棄這類的不必要的通知。</span><span class="sxs-lookup"><span data-stu-id="8431e-136">Interestingly, the Update operation will again send a notification to the adapter client and the whole process will be repeated again, therefore, the client application must have the required logic to discard such unwanted notifications.</span></span>  
  
-   <span data-ttu-id="8431e-137">如果**NotifyOnListenerStart**繫結屬性為 true，每次啟動接收位置配接器用戶端會收到通知訊息。</span><span class="sxs-lookup"><span data-stu-id="8431e-137">If the **NotifyOnListenerStart** binding property is true, the adapter client will receive a notification message every time the receive location starts.</span></span> <span data-ttu-id="8431e-138">如需有關如何使用繫結屬性和解譯的通知訊息的詳細資訊，請參閱[接收查詢通知之後接收位置分解在使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="8431e-138">For more information on how to use the binding property and interpret the notification message, see [Receive Query Notifications After a Receive Location Breakdown in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md).</span></span>  
  
## <a name="typical-orchestration-for-receiving-notifications"></a><span data-ttu-id="8431e-139">典型的協調流程接收通知</span><span class="sxs-lookup"><span data-stu-id="8431e-139">Typical Orchestration for Receiving Notifications</span></span>  
 <span data-ttu-id="8431e-140">本節將概述接收通知使用一般的協調流程[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8431e-140">This section outlines the typical orchestration flow for receiving notifications using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
1.  <span data-ttu-id="8431e-141">協調流程必須進行第一件事是要判斷接收通知的類型包括：</span><span class="sxs-lookup"><span data-stu-id="8431e-141">The first thing that the orchestration must do is to determine the type of notification received, including:</span></span>  
  
    -   <span data-ttu-id="8431e-142">接收位置重新啟動之後，是否已收到通知。</span><span class="sxs-lookup"><span data-stu-id="8431e-142">Whether the notification was received after a receive location restarts.</span></span>  
  
    -   <span data-ttu-id="8431e-143">是否已收到通知，作業會在資料庫資料表，例如 Insert、 Update 或 Delete。</span><span class="sxs-lookup"><span data-stu-id="8431e-143">Whether the notification was received for an operation on a database table, such as Insert, Update, or Delete.</span></span>  
  
     <span data-ttu-id="8431e-144">協調流程必須包含**運算式**圖形，並在其中，xpath 查詢來決定接收的訊息種類。</span><span class="sxs-lookup"><span data-stu-id="8431e-144">The orchestration must include an **Expression** shape, and within that, an xpath query to decide what kind of message is received.</span></span>  
  
2.  <span data-ttu-id="8431e-145">在通知之後類型決定，協調流程必須包含所要執行特定動作，根據收到的通知類型的決策區塊。</span><span class="sxs-lookup"><span data-stu-id="8431e-145">After the notification type is determined, the orchestration must include a decision block to perform specific actions based on the type of notification received.</span></span> <span data-ttu-id="8431e-146">若要達成此目的，協調流程必須包含**決定**圖形，其中包括**規則**區塊和**Else**區塊：</span><span class="sxs-lookup"><span data-stu-id="8431e-146">To achieve this, the orchestration must include a **Decide** shape, which includes a **Rule** block and an **Else** block:</span></span>  
  
    -   <span data-ttu-id="8431e-147">內**規則**區塊中，您必須指定的條件，並再包含執行某些作業，如果符合條件的協調流程圖形。</span><span class="sxs-lookup"><span data-stu-id="8431e-147">Within the **Rule** block, you must specify the condition and then include orchestration shapes to perform certain operations if the condition is met.</span></span>  
  
    -   <span data-ttu-id="8431e-148">內**Else**區塊中，您必須包含執行某些作業，如果條件為協調流程圖形*不*符合。</span><span class="sxs-lookup"><span data-stu-id="8431e-148">Within the **Else** block, you must include orchestration shapes to perform certain operations if the condition is *not* met.</span></span>  
  
 <span data-ttu-id="8431e-149">中所述的上述需求的詳細資料[處理通知訊息，以便完成特定工作中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="8431e-149">Details of the preceding requirements are described in [Process Notification Messages to complete Specific Tasks in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md).</span></span> <span data-ttu-id="8431e-150">詳細的教學課程也會提供[教學課程 2： 員工-訂單程序使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="8431e-150">A detailed tutorial is also available in [Tutorial 2: Employee - Purchase Order Process using the SQL adapter](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).</span></span>