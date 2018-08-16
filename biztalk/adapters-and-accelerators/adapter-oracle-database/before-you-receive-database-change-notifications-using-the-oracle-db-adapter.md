---
title: 接收資料庫變更通知使用 Oracle 資料庫配接器的考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 206439b9-0408-4fbb-80e3-cfda2f5a89a5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7237037794168ffb136c95734582b3df95db48
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015191"
---
# <a name="considerations-for-receiving-database-change-notifications-using-the-oracle-database-adapter"></a><span data-ttu-id="4c1d7-102">接收資料庫變更通知使用 Oracle 資料庫配接器的考量</span><span class="sxs-lookup"><span data-stu-id="4c1d7-102">Considerations for Receiving Database Change Notifications Using the Oracle Database adapter</span></span>
<span data-ttu-id="4c1d7-103">本主題提供一些考量和最佳作法，您必須謹記在心，同時使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 資料庫接收資料庫通知。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-103">This topic provides some considerations and best practices that you must keep in mind while using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive database notifications from an Oracle database.</span></span>  
  
## <a name="considerations-while-using-the-adapter-to-receive-notifications"></a><span data-ttu-id="4c1d7-104">使用配接器接收通知時的考量</span><span class="sxs-lookup"><span data-stu-id="4c1d7-104">Considerations While Using the Adapter to Receive Notifications</span></span>  
 <span data-ttu-id="4c1d7-105">您必須考慮使用下列[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收查詢通知。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-105">You must consider the following while using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive query notifications.</span></span>  
  
- <span data-ttu-id="4c1d7-106">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]只會將傳遞通知，從 Oracle 資料庫時，它會接收配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-106">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] simply passes on the notification, which it receives from the Oracle database, to the adapter clients.</span></span> <span data-ttu-id="4c1d7-107">配接器不會區分的通知不同的作業，也就是，配接器不提供任何資訊的特定通知是要用於插入作業或更新作業。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-107">The adapter does not distinguish between the notifications for different operations, i.e., the adapter does not have any information whether a particular notification is for an Insert operation or an Update operation.</span></span>  
  
- <span data-ttu-id="4c1d7-108">作業的通知訊息不會受到該作業所影響的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-108">The notification message for an operation is not affected by the number of records affected by that operation.</span></span> <span data-ttu-id="4c1d7-109">比方說，無論在 Oracle 資料庫資料表中插入的記錄數目，配接器用戶端會收到只有一個通知訊息。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-109">For example, irrespective of the number of records inserted in an Oracle database table, the adapter clients receive only one notification message.</span></span>  
  
- <span data-ttu-id="4c1d7-110">建議配接器用戶端應用程式，包含要解譯的從 Oracle 資料庫接收的通知類型的邏輯。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-110">We recommend that the adapter client application contain the logic to interpret the kind of notification received from the Oracle database.</span></span> <span data-ttu-id="4c1d7-111">配接器用戶端應用程式可以達到此目的擷取中的資訊**\<Info\>** 接收的通知訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-111">The adapter client applications can do so by extracting the information in the **\<Info\>** element of the received notification message.</span></span> <span data-ttu-id="4c1d7-112">以下是範例插入作業所接收的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-112">Here’s an example of a notification message received for an Insert operation.</span></span>  
  
  ```  
  <?xml version="1.0" encoding="utf-8" ?>   
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
  
   <span data-ttu-id="4c1d7-113">請注意內的值**\<Info\>** 項目。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-113">Notice the value within the **\<Info\>** element.</span></span> <span data-ttu-id="4c1d7-114">這個值會提供收到通知訊息的作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-114">This value provides information on the operation for which the notification message was received.</span></span> <span data-ttu-id="4c1d7-115">您的應用程式應該有的功能內的值中擷取**\<Info\>** 項目，然後根據的值，執行後續的工作。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-115">Your application should have the functionality to extract the value within the **\<Info\>** element and then based on the value, perform subsequent tasks.</span></span> <span data-ttu-id="4c1d7-116">本主題[處理通知訊息來完成 Oracle 資料庫中的特定工作](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)有關如何擷取內的值中的指示**\<資訊\>** 項目。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-116">The topic [Processing Notification Messages to complete Specific Tasks in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md) has instructions on how to extract the value within the **\<Info\>** element.</span></span>  
  
- <span data-ttu-id="4c1d7-117">在理想情況下，用戶端應用程式會收到通知之後，它應該更新為其已收到通知，讓後續的通知不會針對同一筆記錄的記錄。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-117">Ideally, after the client application receives a notification, it should update the record for which the notification is already received so that the subsequent notifications are not for the same record.</span></span> <span data-ttu-id="4c1d7-118">例如，請考慮**ACCOUNTACTIVITY**具有資料表**處理**資料行。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-118">For example, consider an **ACCOUNTACTIVITY** table that has a **Processed** column.</span></span> <span data-ttu-id="4c1d7-119">針對所有新記錄插入至**ACCOUNTACTIVITY**資料表中的值**處理**資料行一律是 ' n '。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-119">For all new records inserted into the **ACCOUNTACTIVITY** table, the value in the **Processed** column is always ‘n’.</span></span> <span data-ttu-id="4c1d7-120">例如，在插入作業後中的記錄**ACCOUNTACTIVITY**資料表看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="4c1d7-120">For example, after an insert operation, the records in the **ACCOUNTACTIVITY** table will look like the following:</span></span>  
  
  |<span data-ttu-id="4c1d7-121">帳戶的交易識別碼</span><span class="sxs-lookup"><span data-stu-id="4c1d7-121">Account Transaction ID</span></span>|<span data-ttu-id="4c1d7-122">已處理</span><span class="sxs-lookup"><span data-stu-id="4c1d7-122">Processed</span></span>|  
  |----------------------------|---------------|  
  |<span data-ttu-id="4c1d7-123">10001</span><span class="sxs-lookup"><span data-stu-id="4c1d7-123">10001</span></span>|<span data-ttu-id="4c1d7-124">n</span><span class="sxs-lookup"><span data-stu-id="4c1d7-124">n</span></span>|  
  
   <span data-ttu-id="4c1d7-125">若要取得之新插入的資料錄的通知，將配接器用戶端**NotificationStatement**繫結屬性設為：</span><span class="sxs-lookup"><span data-stu-id="4c1d7-125">To get notifications for the newly inserted record, the adapter client will set the **NotificationStatement** binding property as:</span></span>  
  
  ```  
  SELECT * FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
  ```  
  
   <span data-ttu-id="4c1d7-126">之後，接收通知，用戶端應用程式必須設定的值**處理**為 'y' 的資料行，讓 notification 陳述式前已收到通知的記錄上無法運作。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-126">After, receiving the notification, the client application must set the value of the **Processed** column to ‘y’ so that the notification statement does not operate on the record that was already notified for.</span></span> <span data-ttu-id="4c1d7-127">因此，若要達到此目的，用戶端應用程式必須在更新作業上執行**ACCOUNTACTIVITY**資料表。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-127">So, to achieve this, the client application must perform an Update operation on the **ACCOUNTACTIVITY** table.</span></span> <span data-ttu-id="4c1d7-128">更新作業之後，相同記錄**ACCOUNTACTIVITY**資料表看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="4c1d7-128">After the Update operation, the same record in the **ACCOUNTACTIVITY** table will look like the following:</span></span>  
  
  |<span data-ttu-id="4c1d7-129">帳戶的交易識別碼</span><span class="sxs-lookup"><span data-stu-id="4c1d7-129">Account Transaction ID</span></span>|<span data-ttu-id="4c1d7-130">已處理</span><span class="sxs-lookup"><span data-stu-id="4c1d7-130">Processed</span></span>|  
  |----------------------------|---------------|  
  |<span data-ttu-id="4c1d7-131">10001</span><span class="sxs-lookup"><span data-stu-id="4c1d7-131">10001</span></span>|<span data-ttu-id="4c1d7-132">y</span><span class="sxs-lookup"><span data-stu-id="4c1d7-132">y</span></span>|  
  
   <span data-ttu-id="4c1d7-133">有趣的是，更新作業將會再次傳送通知給配接器用戶端，並且會再次重複整個程序。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-133">Interestingly, the Update operation will again send a notification to the adapter client and the whole process will be repeated again.</span></span> <span data-ttu-id="4c1d7-134">因此，用戶端應用程式必須具有必要的邏輯，以捨棄這類不必要的通知。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-134">So, the client application must have the required logic to discard such unwanted notifications.</span></span>  
  
- <span data-ttu-id="4c1d7-135">如果**NotifyOnListenerStart**繫結屬性為 true 時，配接器會傳送通知給配接器用戶端每次接收位置開始。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-135">If the **NotifyOnListenerStart** binding property is true, the adapter will send a notification to the adapter client every time the receive location starts.</span></span> <span data-ttu-id="4c1d7-136">如需有關如何使用繫結屬性和解譯的通知訊息的詳細資訊，請參閱 <<c0> [ 接收 Oracle 資料庫變更通知之後接收位置解析](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-after-a-receive-location-breakdown.md)。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-136">For more information on how to use the binding property and interpret the notification message, see [Receiving Oracle Database Change Notifications After a Receive Location Breakdown](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-after-a-receive-location-breakdown.md).</span></span>  
  
## <a name="typical-orchestration-for-receiving-notifications"></a><span data-ttu-id="4c1d7-137">典型的協調流程接收通知</span><span class="sxs-lookup"><span data-stu-id="4c1d7-137">Typical Orchestration for Receiving Notifications</span></span>  
 <span data-ttu-id="4c1d7-138">本節將概述在一般的協調流程，接收通知使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-138">This section outlines the typical orchestration flow for receiving notifications using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
1. <span data-ttu-id="4c1d7-139">協調流程必須進行第一件事是通知的要檢查的收到類型。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-139">The first thing that the orchestration must do is to check the kind of notification received.</span></span> <span data-ttu-id="4c1d7-140">若要檢查的事項如下：</span><span class="sxs-lookup"><span data-stu-id="4c1d7-140">The things to check for are:</span></span>  
  
   - <span data-ttu-id="4c1d7-141">是否收到通知的接收位置重新啟動。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-141">Whether the notification was received for the receive location restart.</span></span>  
  
   - <span data-ttu-id="4c1d7-142">是否已收到通知，作業會在資料庫資料表，例如 Insert、 Update 或 Delete。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-142">Whether the notification was received for an operation on a database table, such as Insert, Update, or Delete.</span></span>  
  
     <span data-ttu-id="4c1d7-143">協調流程必須包含**運算式**圖形，並在其中接收 xpath 查詢，以決定何種訊息。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-143">The orchestration must include an **Expression** shape, and within that an xpath query, to decide what kind of message is received.</span></span>  
  
2. <span data-ttu-id="4c1d7-144">可用的通知類型之後，協調流程必須包含所要執行特定動作，根據收到的通知類型的決策區塊。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-144">After the notification type is available, the orchestration must include a decision block to perform specific actions based on the type of notification received.</span></span> <span data-ttu-id="4c1d7-145">若要達到此目的，協調流程必須包含**決定**圖形。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-145">To achieve this, the orchestration must include a **Decide** shape.</span></span> <span data-ttu-id="4c1d7-146">**決定**圖形組成**規則**區塊並**Else**區塊。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-146">The **Decide** shape consists of a **Rule** block and an **Else** block.</span></span> <span data-ttu-id="4c1d7-147">內**規則**區塊中，您必須指定條件，然後包含 如果符合條件時執行特定作業的協調流程圖形。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-147">Within the **Rule** block, you must specify the condition and then include orchestration shapes to perform certain operations if the condition is met.</span></span> <span data-ttu-id="4c1d7-148">內**Else**區塊中，您必須包含如果條件為執行特定作業的協調流程圖形*不*符合。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-148">Within the **Else** block, you must include orchestration shapes to perform certain operations if the condition is *not* met.</span></span>  
  
   <span data-ttu-id="4c1d7-149">在將詳細說明上述的建議[處理通知訊息，以完成使用 BizTalk Server 的 Oracle 資料庫中的特定工作](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="4c1d7-149">The preceding recommendations are described in detail in [Processing Notification Messages to complete Specific Tasks in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c1d7-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c1d7-150">See Also</span></span>  
 [<span data-ttu-id="4c1d7-151">使用 BizTalk Server 接收的 Oracle 資料庫變更通知</span><span class="sxs-lookup"><span data-stu-id="4c1d7-151">Receiving Oracle Database Change Notifications Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)