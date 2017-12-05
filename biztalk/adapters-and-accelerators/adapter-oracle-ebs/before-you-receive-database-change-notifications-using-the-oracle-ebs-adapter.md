---
title: "變更通知使用 Oracle E-business Suite 配接器的接收資料庫的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95bbb19e-8d31-4b27-8cfe-6760e4bb0808
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3157b8ab7a706203d3b9475de890fb2a8f8dd3a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="considerations-for-receiving-database-change-notifications-using-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="3f0df-102">變更通知使用 Oracle E-business Suite 配接器的接收資料庫的考量</span><span class="sxs-lookup"><span data-stu-id="3f0df-102">Considerations for receiving database change notifications using the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="3f0df-103">本主題提供一些考量和最佳作法，您必須使用時請記住[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要從 Oracle 資料庫接收資料庫通知。</span><span class="sxs-lookup"><span data-stu-id="3f0df-103">This topic provides some considerations and best practices that you must keep in mind while using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive database notifications from an Oracle database.</span></span>  
  
## <a name="considerations-while-using-the-adapter-to-receive-notifications"></a><span data-ttu-id="3f0df-104">使用配接器接收通知時的考量</span><span class="sxs-lookup"><span data-stu-id="3f0df-104">Considerations While Using the Adapter to Receive Notifications</span></span>  
 <span data-ttu-id="3f0df-105">您必須考慮下列使用時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收查詢通知。</span><span class="sxs-lookup"><span data-stu-id="3f0df-105">You must consider the following while using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive query notifications.</span></span>  
  
-   <span data-ttu-id="3f0df-106">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]只會傳遞通知，從 Oracle 資料庫時，它會接收配接器用戶端上。</span><span class="sxs-lookup"><span data-stu-id="3f0df-106">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] simply passes on the notification, which it receives from the Oracle database, to the adapter clients.</span></span> <span data-ttu-id="3f0df-107">配接器不會區分的通知不同的作業，也就是，配接器沒有任何資訊的特定通知適用於插入作業或更新作業。</span><span class="sxs-lookup"><span data-stu-id="3f0df-107">The adapter does not distinguish between the notifications for different operations, i.e., the adapter does not have any information whether a particular notification is for an Insert operation or an Update operation.</span></span>  
  
-   <span data-ttu-id="3f0df-108">作業的通知訊息不會受到該作業所影響的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="3f0df-108">The notification message for an operation is not affected by the number of records affected by that operation.</span></span> <span data-ttu-id="3f0df-109">例如，Oracle 資料庫資料表中插入的記錄數目，不論配接器用戶端收到只有一個通知訊息。</span><span class="sxs-lookup"><span data-stu-id="3f0df-109">For example, irrespective of the number of records inserted in an Oracle database table, the adapter clients receive only one notification message.</span></span>  
  
-   <span data-ttu-id="3f0df-110">我們建議配接器用戶端應用程式包含的邏輯來解譯的從 Oracle 資料庫接收的通知類型。</span><span class="sxs-lookup"><span data-stu-id="3f0df-110">We recommend that the adapter client application contain the logic to interpret the kind of notification received from the Oracle database.</span></span> <span data-ttu-id="3f0df-111">配接器用戶端應用程式可以這樣做來擷取中的資訊**\<資訊\>**接收的通知訊息的項目。</span><span class="sxs-lookup"><span data-stu-id="3f0df-111">The adapter client applications can do so by extracting the information in the **\<Info\>** element of the received notification message.</span></span> <span data-ttu-id="3f0df-112">以下是 Insert 作業接收通知訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="3f0df-112">Here’s an example of a notification message received for an Insert operation.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/">  
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
  
     <span data-ttu-id="3f0df-113">請注意內的值**\<資訊\>**項目。</span><span class="sxs-lookup"><span data-stu-id="3f0df-113">Notice the value within the **\<Info\>** element.</span></span> <span data-ttu-id="3f0df-114">此值會提供資訊在收到通知訊息的作業。</span><span class="sxs-lookup"><span data-stu-id="3f0df-114">This value provides information on the operation for which the notification message was received.</span></span> <span data-ttu-id="3f0df-115">您的應用程式應該有的功能來擷取內的值**\<資訊\>**項目，然後根據的值，執行後續的工作。</span><span class="sxs-lookup"><span data-stu-id="3f0df-115">Your application should have the functionality to extract the value within the **\<Info\>** element and then based on the value, perform subsequent tasks.</span></span> <span data-ttu-id="3f0df-116">本主題[Oracle E-business Suite 中完成特定工作的程序通知訊息](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)如何擷取內的值中的指示**\<資訊\>**項目.</span><span class="sxs-lookup"><span data-stu-id="3f0df-116">The topic [Process Notification Messages to Complete Specific Tasks in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md) has instructions on how to extract the value within the **\<Info\>** element.</span></span>  
  
-   <span data-ttu-id="3f0df-117">在理想情況下，用戶端應用程式會收到通知之後，它應該更新其已收到通知，讓後續的通知沒有相同的記錄的記錄。</span><span class="sxs-lookup"><span data-stu-id="3f0df-117">Ideally, after the client application receives a notification, it should update the record for which the notification is already received so that the subsequent notifications are not for the same record.</span></span> <span data-ttu-id="3f0df-118">例如，請考慮**ACCOUNTACTIVITY**資料表具有**處理**資料行。</span><span class="sxs-lookup"><span data-stu-id="3f0df-118">For example, consider an **ACCOUNTACTIVITY** table that has a **Processed** column.</span></span> <span data-ttu-id="3f0df-119">針對所有新記錄插入至**ACCOUNTACTIVITY**資料表中的值**處理**資料行一律是 ' n '。</span><span class="sxs-lookup"><span data-stu-id="3f0df-119">For all new records inserted into the **ACCOUNTACTIVITY** table, the value in the **Processed** column is always ‘n’.</span></span> <span data-ttu-id="3f0df-120">例如，在插入作業中的記錄之後**ACCOUNTACTIVITY**資料表看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f0df-120">For example, after an insert operation, the records in the **ACCOUNTACTIVITY** table will look like the following:</span></span>  
  
    |<span data-ttu-id="3f0df-121">帳戶交易識別碼</span><span class="sxs-lookup"><span data-stu-id="3f0df-121">Account Transaction ID</span></span>|<span data-ttu-id="3f0df-122">已處理</span><span class="sxs-lookup"><span data-stu-id="3f0df-122">Processed</span></span>|  
    |----------------------------|---------------|  
    |<span data-ttu-id="3f0df-123">10001</span><span class="sxs-lookup"><span data-stu-id="3f0df-123">10001</span></span>|n|  
  
     <span data-ttu-id="3f0df-124">若要取得之新插入的資料錄的通知，設定配接器用戶端將**NotificaitonStatement**繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="3f0df-124">To get notifications for the newly inserted record, the adapter client will set the **NotificaitonStatement** binding property as:</span></span>  
  
    ```  
    SELECT * FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
    ```  
  
     <span data-ttu-id="3f0df-125">之後，收到通知，用戶端應用程式必須設定的值**處理**'y' 資料行，以便在 notification 陳述式不能進行已收到的記錄。</span><span class="sxs-lookup"><span data-stu-id="3f0df-125">After, receiving the notification, the client application must set the value of the **Processed** column to ‘y’ so that the notification statement does not operate on the record that was already notified for.</span></span> <span data-ttu-id="3f0df-126">因此，若要達成此目的，用戶端應用程式必須執行更新作業上**ACCOUNTACTIVITY**資料表。</span><span class="sxs-lookup"><span data-stu-id="3f0df-126">So, to achieve this, the client application must perform an Update operation on the **ACCOUNTACTIVITY** table.</span></span> <span data-ttu-id="3f0df-127">更新作業之後，相同記錄**ACCOUNTACTIVITY**資料表看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f0df-127">After the Update operation, the same record in the **ACCOUNTACTIVITY** table will look like the following:</span></span>  
  
    |<span data-ttu-id="3f0df-128">帳戶交易識別碼</span><span class="sxs-lookup"><span data-stu-id="3f0df-128">Account Transaction ID</span></span>|<span data-ttu-id="3f0df-129">已處理</span><span class="sxs-lookup"><span data-stu-id="3f0df-129">Processed</span></span>|  
    |----------------------------|---------------|  
    |<span data-ttu-id="3f0df-130">10001</span><span class="sxs-lookup"><span data-stu-id="3f0df-130">10001</span></span>|<span data-ttu-id="3f0df-131">y</span><span class="sxs-lookup"><span data-stu-id="3f0df-131">y</span></span>|  
  
     <span data-ttu-id="3f0df-132">有趣的是，更新作業將會再次傳送通知給配接器用戶端，整個程序會重複一次。</span><span class="sxs-lookup"><span data-stu-id="3f0df-132">Interestingly, the Update operation will again send a notification to the adapter client and the whole process will be repeated again.</span></span> <span data-ttu-id="3f0df-133">因此，用戶端應用程式必須有必要的邏輯，以捨棄這類的不必要的通知。</span><span class="sxs-lookup"><span data-stu-id="3f0df-133">So, the client application must have the required logic to discard such unwanted notifications.</span></span>  
  
-   <span data-ttu-id="3f0df-134">如果**NotifyOnListenerStart**繫結屬性為 true，配接器會傳送通知給配接器用戶端每次啟動接收位置。</span><span class="sxs-lookup"><span data-stu-id="3f0df-134">If the **NotifyOnListenerStart** binding property is true, the adapter will send a notification to the adapter client every time the receive location starts.</span></span> <span data-ttu-id="3f0df-135">如需有關如何使用繫結屬性和解譯的通知訊息的詳細資訊，請參閱[接收 Oracle E-business Suite 資料庫變更通知之後接收位置分解](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md)。</span><span class="sxs-lookup"><span data-stu-id="3f0df-135">For more information on how to use the binding property and interpret the notification message, see [Receive Oracle E-Business Suite Database Change Notifications After a Receive Location Breakdown](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md).</span></span>  
  
## <a name="typical-orchestration-for-receiving-notifications"></a><span data-ttu-id="3f0df-136">典型的協調流程接收通知</span><span class="sxs-lookup"><span data-stu-id="3f0df-136">Typical Orchestration for Receiving Notifications</span></span>  
 <span data-ttu-id="3f0df-137">本節將概述接收通知使用一般的協調流程[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f0df-137">This section outlines the typical orchestration flow for receiving notifications using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
1.  <span data-ttu-id="3f0df-138">協調流程必須進行第一件事是通知的檢查的收到類型。</span><span class="sxs-lookup"><span data-stu-id="3f0df-138">The first thing that the orchestration must do is to check the kind of notification received.</span></span> <span data-ttu-id="3f0df-139">若要檢查的事項如下：</span><span class="sxs-lookup"><span data-stu-id="3f0df-139">The things to check for are:</span></span>  
  
    -   <span data-ttu-id="3f0df-140">是否已收到通知，接收位置重新啟動。</span><span class="sxs-lookup"><span data-stu-id="3f0df-140">Whether the notification was received for the receive location restart.</span></span>  
  
    -   <span data-ttu-id="3f0df-141">是否已收到通知，作業會在資料庫資料表，例如 Insert、 Update 或 Delete。</span><span class="sxs-lookup"><span data-stu-id="3f0df-141">Whether the notification was received for an operation on a database table, such as Insert, Update, or Delete.</span></span>  
  
     <span data-ttu-id="3f0df-142">協調流程必須包含**運算式**圖形，並在接收到 xpath 查詢，以決定何種訊息。</span><span class="sxs-lookup"><span data-stu-id="3f0df-142">The orchestration must include an **Expression** shape, and within that an xpath query, to decide what kind of message is received.</span></span>  
  
2.  <span data-ttu-id="3f0df-143">提供的通知類型之後，協調流程必須包含所要執行特定動作，根據收到的通知類型的決策區塊。</span><span class="sxs-lookup"><span data-stu-id="3f0df-143">After the notification type is available, the orchestration must include a decision block to perform specific actions based on the type of notification received.</span></span> <span data-ttu-id="3f0df-144">若要達成此目的，協調流程必須包含**決定**圖形。</span><span class="sxs-lookup"><span data-stu-id="3f0df-144">To achieve this, the orchestration must include a **Decide** shape.</span></span> <span data-ttu-id="3f0df-145">**決定**圖形組成**規則**區塊和**Else**區塊。</span><span class="sxs-lookup"><span data-stu-id="3f0df-145">The **Decide** shape consists of a **Rule** block and an **Else** block.</span></span> <span data-ttu-id="3f0df-146">內**規則**區塊中，您必須指定的條件，並再包含執行某些作業，如果符合條件的協調流程圖形。</span><span class="sxs-lookup"><span data-stu-id="3f0df-146">Within the **Rule** block, you must specify the condition and then include orchestration shapes to perform certain operations if the condition is met.</span></span> <span data-ttu-id="3f0df-147">內**Else**區塊中，您必須包含執行某些作業，如果條件為協調流程圖形*不*符合。</span><span class="sxs-lookup"><span data-stu-id="3f0df-147">Within the **Else** block, you must include orchestration shapes to perform certain operations if the condition is *not* met.</span></span>  
  
 <span data-ttu-id="3f0df-148">中的詳細說明上述建議[Oracle E-business Suite 中完成特定工作的程序通知訊息](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="3f0df-148">The preceding recommendations are described in detail in [Process Notification Messages to Complete Specific Tasks in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f0df-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="3f0df-149">See Also</span></span>  
 [<span data-ttu-id="3f0df-150">接收 Oracle E-business Suite 資料庫變更通知使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3f0df-150">Receive Oracle E-Business Suite Database Change Notifications using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-biztalk-server.md)