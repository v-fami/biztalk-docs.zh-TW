---
title: 使用 WCF 服務模型中的預存程序的輪詢 Oracle E-business Suite |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47dcb866-9161-4b28-9481-2761794ce805
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3fb7ebcbccb1f0edb3370176192f55f0db4985a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967716"
---
# <a name="poll-oracle-e-business-suite-using-stored-procedures-with-the-wcf-service-model"></a><span data-ttu-id="35661-102">輪詢 Oracle E-business Suite 使用 WCF 服務模型中的預存程序</span><span class="sxs-lookup"><span data-stu-id="35661-102">Poll Oracle E-Business Suite using stored procedures with the WCF service model</span></span>
<span data-ttu-id="35661-103">您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來使用預存程序，以定期輪詢 Oracle 資料庫接收定期的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="35661-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using stored procedures to periodically poll the Oracle database.</span></span> <span data-ttu-id="35661-104">您可以指定預存程序，為配接器執行定期輪詢 Oracle 資料庫的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="35661-104">You can specify a stored procedure as a polling statement that the adapter executes periodically to poll the Oracle database.</span></span>  
  
 <span data-ttu-id="35661-105">若要啟用輪詢，您必須指定特定繫結屬性，本主題中所述。</span><span class="sxs-lookup"><span data-stu-id="35661-105">To enable polling, you must specify certain binding properties as described in this topic.</span></span>  <span data-ttu-id="35661-106">如需如何配接器支援在輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。</span><span class="sxs-lookup"><span data-stu-id="35661-106">For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-adapter-binding-properties"></a><span data-ttu-id="35661-107">使用 Oracle E-business 配接器繫結屬性中設定輪詢作業</span><span class="sxs-lookup"><span data-stu-id="35661-107">Configuring a Polling Operation with Oracle E-Business Adapter Binding Properties</span></span>  
 <span data-ttu-id="35661-108">下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結，您用來設定配接器來接收資料變更訊息的屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-108">The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="35661-109">執行輪詢應用程式時，您必須指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-109">You must specify these binding properties while running the polling application.</span></span>  
  
|<span data-ttu-id="35661-110">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="35661-110">Binding Property</span></span>|<span data-ttu-id="35661-111">Description</span><span class="sxs-lookup"><span data-stu-id="35661-111">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="35661-112">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="35661-112">**InboundOperationType**</span></span>|<span data-ttu-id="35661-113">指定您是否要執行**輪詢**或**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="35661-113">Specifies whether you want to perform a **Polling** or **Notification** inbound operation.</span></span> <span data-ttu-id="35661-114">預設值是**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="35661-114">Default is **Polling**.</span></span>|  
|<span data-ttu-id="35661-115">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="35661-115">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="35661-116">指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。</span><span class="sxs-lookup"><span data-stu-id="35661-116">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="35661-117">只有當可用的記錄時，預存程序指定為**PollingInput**繫結屬性將會執行。</span><span class="sxs-lookup"><span data-stu-id="35661-117">Only if a record is available, the stored procedure you specified for the **PollingInput** binding property will be executed.</span></span>|  
|<span data-ttu-id="35661-118">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="35661-118">**PollingInterval**</span></span>|<span data-ttu-id="35661-119">指定間隔，以秒為單位，此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-119">Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="35661-120">預設值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="35661-120">The default is 30 seconds.</span></span> <span data-ttu-id="35661-121">輪詢間隔會決定後續輪詢間隔時間。</span><span class="sxs-lookup"><span data-stu-id="35661-121">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="35661-122">如果指定的間隔內執行的陳述式，則配接器進入睡眠狀態的剩餘時間間隔中。</span><span class="sxs-lookup"><span data-stu-id="35661-122">If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="35661-123">**PollingInput**</span><span class="sxs-lookup"><span data-stu-id="35661-123">**PollingInput**</span></span>|<span data-ttu-id="35661-124">指定輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="35661-124">Specifies the polling statement.</span></span> <span data-ttu-id="35661-125">若要輪詢使用預存程序，您必須指定這個繫結屬性的整個要求訊息。</span><span class="sxs-lookup"><span data-stu-id="35661-125">To poll using a stored procedure, you must specify the entire request message for this binding property.</span></span> <span data-ttu-id="35661-126">要求訊息必須相同，您傳送給配接器叫用預存程序，做為輸出的作業。</span><span class="sxs-lookup"><span data-stu-id="35661-126">The request message must be the same that you send to the adapter for invoking the stored procedure as an outbound operation.</span></span> <span data-ttu-id="35661-127">預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="35661-127">The default is null.</span></span><br /><br /> <span data-ttu-id="35661-128">您必須指定的值**PollingInput**繫結內容來啟用輪詢。</span><span class="sxs-lookup"><span data-stu-id="35661-128">You must specify a value for **PollingInput** binding property to enable polling.</span></span> <span data-ttu-id="35661-129">輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-129">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span>|  
|<span data-ttu-id="35661-130">**PollingAction**</span><span class="sxs-lookup"><span data-stu-id="35661-130">**PollingAction**</span></span>|<span data-ttu-id="35661-131">指定輪詢作業的動作。</span><span class="sxs-lookup"><span data-stu-id="35661-131">Specifies the action for the polling operation.</span></span> <span data-ttu-id="35661-132">您可以決定產生的作業使用的服務介面的輪詢動作[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35661-132">You can determine the polling action from the service interface generated for the operation using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>|  
|<span data-ttu-id="35661-133">**PostPollStatement**</span><span class="sxs-lookup"><span data-stu-id="35661-133">**PostPollStatement**</span></span>|<span data-ttu-id="35661-134">指定執行所指定的陳述式之後的陳述式區塊**PollingInput**執行繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-134">Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.</span></span>|  
|<span data-ttu-id="35661-135">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="35661-135">**PollWhileDataFound**</span></span>|<span data-ttu-id="35661-136">指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]忽略的輪詢間隔，並持續執行輪詢陳述式，如果輪詢資料表中的可用資料。</span><span class="sxs-lookup"><span data-stu-id="35661-136">Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled.</span></span> <span data-ttu-id="35661-137">如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="35661-137">If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval.</span></span> <span data-ttu-id="35661-138">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="35661-138">Default is false.</span></span>|  
  
 <span data-ttu-id="35661-139">如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="35661-139">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="35661-140">如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢，請閱讀下列各節。</span><span class="sxs-lookup"><span data-stu-id="35661-140">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll, read the following sections.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="35661-141">本主題示範輪詢的方式</span><span class="sxs-lookup"><span data-stu-id="35661-141">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="35661-142">本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援接收訊息使用預存程序，使用 GET_ACTIVITYS 資料變更預存程序來輪詢 ACCOUNTACTIVITY 資料表 Oracle 資料庫中的。</span><span class="sxs-lookup"><span data-stu-id="35661-142">In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using stored procedures, you use the GET_ACTIVITYS stored procedure to poll the ACCOUNTACTIVITY table in the Oracle database.</span></span> <span data-ttu-id="35661-143">這個預存程序可與 ACCOUNT_PKG 封裝。</span><span class="sxs-lookup"><span data-stu-id="35661-143">This stored procedure is available with the ACCOUNT_PKG package.</span></span> <span data-ttu-id="35661-144">您可以執行這些範例資料庫中建立這些物件提供的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="35661-144">You can run the SQL scripts provided with the samples to create these objects in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35661-145">此主題輪詢中 ACCOUNTACTIVITY 資料表，其中基底資料庫資料表建立執行範例所提供的指令碼的範例。</span><span class="sxs-lookup"><span data-stu-id="35661-145">The example in this topic polls the ACCOUNTACTIVITY table, which is a base database table created by running the scripts provided with the samples.</span></span> <span data-ttu-id="35661-146">若要輪詢的任何其他資料表，包括介面資料表本主題中所述，您必須執行類似的程序。</span><span class="sxs-lookup"><span data-stu-id="35661-146">You must perform similar procedures as described in this topic to poll any other table, including interface tables.</span></span>  
  
 <span data-ttu-id="35661-147">若要示範輪詢作業，我們執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="35661-147">To demonstrate a polling operation, we do the following:</span></span>  
  
-   <span data-ttu-id="35661-148">指定 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中資料表輪詢 (ACCOUNTACTIVITY) 有任何資料。</span><span class="sxs-lookup"><span data-stu-id="35661-148">Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the table being polled (ACCOUNTACTIVITY) has any data.</span></span> <span data-ttu-id="35661-149">在此範例中，您可以設定為這個繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="35661-149">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  
  
     <span data-ttu-id="35661-150">這可確保當配接器 ACCOUNTACTIVITY 資料表具有一些記錄時才會執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="35661-150">This ensures that the adapter executes the polling statement only when the ACCOUNTACTIVITY table has some records.</span></span>  
  
-   <span data-ttu-id="35661-151">藉由提供要求訊息的一部分執行的預存程序 GET_ACTIVITYS， **PollingInput**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-151">Execute a stored procedure, GET_ACTIVITYS, by providing the request message as part of the **PollingInput** binding property.</span></span> <span data-ttu-id="35661-152">這個預存程序會擷取 ACCOUNTACTIVITY 資料表中的所有資料列，您會從配接器收到回應訊息。</span><span class="sxs-lookup"><span data-stu-id="35661-152">This stored procedure will retrieve all the rows in the ACCOUNTACTIVITY table and you will get a response message from the adapter.</span></span>  
  
-   <span data-ttu-id="35661-153">執行一部分的 PL/SQL 區塊**PostPollStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-153">Execute a PL/SQL block as part of the **PostPollStatement** binding property.</span></span> <span data-ttu-id="35661-154">這個陳述式會移動所有資料從 ACCOUNTACTIVITY 資料表在資料庫中的另一個資料表。</span><span class="sxs-lookup"><span data-stu-id="35661-154">This statement will move all data from ACCOUNTACTIVITY table to another table in the database.</span></span> <span data-ttu-id="35661-155">發生這種情況，在下一次之後**PollingInput**會執行，它將會不提取任何資料，因此 GET_ACTIVITYS 預存程序會傳回空白的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="35661-155">After this happens, the next time **PollingInput** is executed, it will not fetch any data and hence the GET_ACTIVITYS stored procedure will return an empty response message.</span></span>  
  
-   <span data-ttu-id="35661-156">更多資料加入至 ACCOUNTACTIVITY 資料表，直到您將會持續取得空的回應訊息，因此您必須重新擴展 ACCOUNTACTIVITY 資料表與新的記錄。</span><span class="sxs-lookup"><span data-stu-id="35661-156">Until more data is added to the ACCOUNTACTIVITY table, you will continue to get empty response messages so you must repopulate the ACCOUNTACTIVITY table with new records.</span></span> <span data-ttu-id="35661-157">您可以藉由執行範例所提供的 more_activity_data.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="35661-157">You can do so by running the more_activity_data.sql script provided with the samples.</span></span> <span data-ttu-id="35661-158">執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。</span><span class="sxs-lookup"><span data-stu-id="35661-158">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span>  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="35661-159">在 WCF 服務模型中設定輪詢</span><span class="sxs-lookup"><span data-stu-id="35661-159">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="35661-160">若要輪詢使用預存程序[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 WCF 服務模型中，您必須：</span><span class="sxs-lookup"><span data-stu-id="35661-160">To poll using stored procedures with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="35661-161">使用您要輪詢的預存程序產生的 WCF 服務合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="35661-161">Generate a WCF service contract (interface) for the stored procedure using which you are going to poll.</span></span> <span data-ttu-id="35661-162">此範例中，您必須產生的 WCF 服務合約**GET_ACTIVITYS**預存程序做為輸入的作業。</span><span class="sxs-lookup"><span data-stu-id="35661-162">For this example, you must generate the WCF service contract for the **GET_ACTIVITYS** stored procedure as an inbound operation.</span></span> <span data-ttu-id="35661-163">若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35661-163">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="35661-164">實作這個介面從 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="35661-164">Implement a WCF service from this interface.</span></span>  
  
-   <span data-ttu-id="35661-165">裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。</span><span class="sxs-lookup"><span data-stu-id="35661-165">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="35661-166">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="35661-166">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="35661-167">此主題輪詢使用 GET_ACTIVITYS ACCOUNTACTIVITY 資料庫資料表中的範例預存程序。</span><span class="sxs-lookup"><span data-stu-id="35661-167">The examples in this topic poll the ACCOUNTACTIVITY database table using the GET_ACTIVITYS stored procedure.</span></span> <span data-ttu-id="35661-168">若要產生的資料表和預存程序的指令碼會提供範例。</span><span class="sxs-lookup"><span data-stu-id="35661-168">A script to generate the table and the stored procedure is supplied with the samples.</span></span> <span data-ttu-id="35661-169">如需這些範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="35661-169">For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="35661-170">範例中， **StoredProcPolling_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="35661-170">A sample, **StoredProcPolling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="35661-171">WCF 服務合約和類別</span><span class="sxs-lookup"><span data-stu-id="35661-171">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="35661-172">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]建立 WCF 服務合約 （介面） 和支援類別**GET_ACTIVITYS**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="35661-172">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **GET_ACTIVITYS** inbound operation.</span></span> <span data-ttu-id="35661-173">如需產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="35661-173">For more information about generating a WCF service contract, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="35661-174">WCF 服務合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="35661-174">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="35661-175">下列程式碼顯示產生的 WCF 服務合約 （介面） **GET_ACTIVITYS**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="35661-175">The following code shows the WCF service contract (interface) generated for the **GET_ACTIVITYS** inbound operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/", ConfigurationName="PollingPackageApis_APPS_ACCOUNT_PKG")]  
public interface PollingPackageApis_APPS_ACCOUNT_PKG {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PKG) of message GET_ACTIVITYS   
    // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS")]  
    void GET_ACTIVITYS(GET_ACTIVITYS request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="35661-176">訊息合約</span><span class="sxs-lookup"><span data-stu-id="35661-176">The Message Contracts</span></span>  
 <span data-ttu-id="35661-177">以下是訊息合約**GET_ACTIVITYS**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="35661-177">Following is the message contract for the **GET_ACTIVITYS** inbound operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="GET_ACTIVITYS", WrapperNamespace="http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PK" +  
    "G", IsWrapped=true)]  
public partial class GET_ACTIVITYS {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PK" +  
        "G", Order=0)]  
    public schemas.microsoft.com.OracleEBS._2008._05.RecordTypes.APPS.ACCOUNT_PKG.GET_ACTIVITYS.OUTRECSRecord[] OUTRECS;  
  
    public GET_ACTIVITYS() {  
    }  
  
    public GET_ACTIVITYS(schemas.microsoft.com.OracleEBS._2008._05.RecordTypes.APPS.ACCOUNT_PKG.GET_ACTIVITYS.OUTRECSRecord[] OUTRECS) {  
        this.OUTRECS = OUTRECS;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="35661-178">WCF 服務類別</span><span class="sxs-lookup"><span data-stu-id="35661-178">WCF Service Class</span></span>  
 <span data-ttu-id="35661-179">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生虛設常式實作的服務合約 （介面） 的 WCF 服務類別的檔案。</span><span class="sxs-lookup"><span data-stu-id="35661-179">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="35661-180">檔案的名稱是 OracleEBSBindingService.cs。</span><span class="sxs-lookup"><span data-stu-id="35661-180">The name of the file is OracleEBSBindingService.cs.</span></span> <span data-ttu-id="35661-181">您可以插入要處理邏輯**GET_ACTIVITYS**直接將這個類別的作業。</span><span class="sxs-lookup"><span data-stu-id="35661-181">You can insert the logic to process the **GET_ACTIVITYS** operation directly into this class.</span></span> <span data-ttu-id="35661-182">下列程式碼將示範所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35661-182">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace OracleEBSBindingNamespace {  
  
    public class OracleEBSBindingService : PollingPackageApis_APPS_ACCOUNT_PKG {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/PollingPackageApis/APPS/ACCOUNT_PKG) of message GET_ACTIVITYS   
        // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
        public virtual void GET_ACTIVITYS(GET_ACTIVITYS request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-inbound-messages-for-polling-using-a-stored-procedure"></a><span data-ttu-id="35661-183">輪詢使用預存程序接收內送的訊息</span><span class="sxs-lookup"><span data-stu-id="35661-183">Receiving Inbound Messages For Polling Using a Stored Procedure</span></span>  
 <span data-ttu-id="35661-184">本節說明如何撰寫.NET 應用程式來接收傳入的輪詢訊息使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="35661-184">This section provides instructions on how to write a .NET application to receive inbound polling messages using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-using-a-stored-procedure"></a><span data-ttu-id="35661-185">若要接收的輪詢訊息使用預存程序</span><span class="sxs-lookup"><span data-stu-id="35661-185">To receive polling messages using a stored procedure</span></span>  
  
1.  <span data-ttu-id="35661-186">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 服務合約 （介面） 和協助程式類別，如**GET_ACTIVITYS**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="35661-186">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **GET_ACTIVITYS** inbound operation.</span></span> <span data-ttu-id="35661-187">如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="35661-187">For more information, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span> <span data-ttu-id="35661-188">您可以選擇性地產生服務合約和協助程式類別時指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-188">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="35661-189">這可確保它們已正確設定在產生的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="35661-189">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="35661-190">實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="35661-190">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="35661-191">**GET_ACTIVITYS**這個類別的方法可以擲回例外狀況中止輪詢交易，處理從接收的資料發生錯誤**GET_ACTIVITYS**作業; 否則為此方法不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="35661-191">The **GET_ACTIVITYS** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **GET_ACTIVITYS** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="35661-192">您必須屬性 WCF 服務類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="35661-192">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="35661-193">內**GET_ACTIVITYS**方法，您可以直接實作應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="35661-193">Within the **GET_ACTIVITYS** method, you can implement your application logic directly.</span></span> <span data-ttu-id="35661-194">這個類別可以 OracleEBSBindingService.cs 中找到。</span><span class="sxs-lookup"><span data-stu-id="35661-194">This class can be found in OracleEBSBindingService.cs.</span></span> <span data-ttu-id="35661-195">這段程式碼，在此範例中的子類別**OracleEBSBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="35661-195">This code in this example sub-classes the **OracleEBSBindingService** class.</span></span> <span data-ttu-id="35661-196">在此程式碼中，接收輪詢訊息，並寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="35661-196">In this code, the polling message received and is written to the console.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void  GET_ACTIVITYS(GET_ACTIVITYS request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tProcessed");  
            for (int i = 0; i < request.OUTRECS.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.OUTRECS[i].TID,  
                request.OUTRECS[i].ACCOUNT,  
                request.OUTRECS[i].AMOUNT,  
                request.OUTRECS[i].PROCESSED);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="35661-197">您必須實作下列類別，以避免將認證傳遞做為 URI 的一部分。</span><span class="sxs-lookup"><span data-stu-id="35661-197">You must implement the following class to avoid passing credentials as part of the URI.</span></span> <span data-ttu-id="35661-198">在應用程式的第二個部分中，您會具現化這個類別，以傳遞的認證。</span><span class="sxs-lookup"><span data-stu-id="35661-198">In the latter part of the application, you will instantiate this class to pass on the credentials.</span></span>  
  
    ```  
    class PollingCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new PollingCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="35661-199">建立**OracleEBSBinding**和設定輪詢作業藉由指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-199">Create an **OracleEBSBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="35661-200">您可以在程式碼中明確或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="35661-200">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="35661-201">最少，您必須指定**InboundOperationType**， **PolledDataAvailableStatement**， **PollingInput**，和**PollingAction**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-201">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, and **PollingAction** binding properties.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM ACCOUNTACTIVITY";  
    binding.PollingInput = "<GET_ACTIVITYS xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG'><INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS></GET_ACTIVITYS>";  
    binding.PollingAction = "PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="35661-202">請注意，值**PollingInput**繫結屬性會包含要求訊息來叫用**GET_ACTIVITYS**預存程序做為輸出的作業。</span><span class="sxs-lookup"><span data-stu-id="35661-202">Note that the value for the **PollingInput** binding property contains the request message for invoking the **GET_ACTIVITYS** stored procedure as an outbound operation.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="35661-203">在此範例中，因為您正在輪詢資料庫資料表時，您不需要設定的應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="35661-203">In this example, because you are polling a database table, you do not need to set the applications context.</span></span> <span data-ttu-id="35661-204">不過，如果您已輪詢介面資料表，您必須設定應用程式內容藉由指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="35661-204">However, if you were polling an interface table, you must set the applications context by specifying the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="35661-205">如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="35661-205">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
5.  <span data-ttu-id="35661-206">藉由執行個體化指定 Oracle E-business Suite 認證**PollingCredentials**您在步驟 3 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="35661-206">Specify Oracle E-Business Suite credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
6.  <span data-ttu-id="35661-207">建立在步驟 2 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="35661-207">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
7.  <span data-ttu-id="35661-208">建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="35661-208">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="35661-209">如果指定基底的連線 URI 不能包含輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="35661-209">The base connection URI cannot contain the inbound ID, if specified.</span></span> <span data-ttu-id="35661-210">您也必須將認證傳遞這裡。</span><span class="sxs-lookup"><span data-stu-id="35661-210">You must also pass the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
8.  <span data-ttu-id="35661-211">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="35661-211">Add a service endpoint to the service host.</span></span> <span data-ttu-id="35661-212">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="35661-212">To do this:</span></span>  
  
    -   <span data-ttu-id="35661-213">使用步驟 4 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="35661-213">Use the binding created in step 4.</span></span>  
  
    -   <span data-ttu-id="35661-214">指定連線 URI，其中包含認證並在必要時輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="35661-214">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="35661-215">為 「 PollingPackageApis_APPS_ACCOUNT_PKG"輪詢 MS_SAMPLE_EMPLOYEE 介面資料表中指定的合約。</span><span class="sxs-lookup"><span data-stu-id="35661-215">Specify the contract as "PollingPackageApis_APPS_ACCOUNT_PKG" to poll the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify PollingPackageApis_APPS_ACCOUNT_PKG as the contract  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    serviceHost.AddServiceEndpoint("PollingPackageApis_APPS_ACCOUNT_PKG", binding, ConnectionUri);  
    ```  
  
9. <span data-ttu-id="35661-216">若要收到輪詢資料，請開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="35661-216">To receive polling data, open the service host.</span></span> <span data-ttu-id="35661-217">每當查詢會傳回結果集時，配接器會傳回資料。</span><span class="sxs-lookup"><span data-stu-id="35661-217">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
10. <span data-ttu-id="35661-218">若要終止輪詢，關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="35661-218">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="35661-219">配接器將會繼續輪詢直到關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="35661-219">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="35661-220">範例</span><span class="sxs-lookup"><span data-stu-id="35661-220">Example</span></span>  
 <span data-ttu-id="35661-221">下列範例會示範一個輪詢的應用程式，輪詢使用 GET_ACTIVITYS ACCOUNTACTIVITY 資料庫資料表的預存程序。</span><span class="sxs-lookup"><span data-stu-id="35661-221">The following example shows a polling application that polls the ACCOUNTACTIVITY database table using the GET_ACTIVITYS stored procedure.</span></span> <span data-ttu-id="35661-222">**PollingInput**繫結屬性包含要叫用從 ACCOUNTACTIVITY 資料表讀取所有資料 GET_ACTIVITYS 預存程序的要求訊息和後輪詢陳述式從 ACCOUNTACTIVITY 移動所有資料ACTIVITYHISTORY 資料表。</span><span class="sxs-lookup"><span data-stu-id="35661-222">The **PollingInput** binding property contains the request message to invoke the GET_ACTIVITYS stored procedure that reads all the data from the ACCOUNTACTIVITY table and the post poll statement moves all the data from ACCOUNTACTIVITY to ACTIVITYHISTORY table.</span></span>  
  
 <span data-ttu-id="35661-223">第一個輪詢訊息會說明 ACCOUNTACTIVITY 資料表中的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="35661-223">The first polling message gives all the records from the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="35661-224">後續的輪詢訊息不會包含任何記錄，因為後輪詢陳述式會刪除的記錄。</span><span class="sxs-lookup"><span data-stu-id="35661-224">Subsequent polling messages will not contain any records because the post poll statement deletes the records.</span></span> <span data-ttu-id="35661-225">更多資料加入到 ACCOUNTACTIVITY 資料表之前, 則不會收到任何輪詢訊息，您必須重新擴展 ACCOUNTACTIVITY 資料表與新的記錄。</span><span class="sxs-lookup"><span data-stu-id="35661-225">Until more data is added to the ACCOUNTACTIVITY table, you will not get any polling messages so you must repopulate the ACCOUNTACTIVITY table with new records.</span></span> <span data-ttu-id="35661-226">您可以藉由執行範例所提供的 more_activity_data.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="35661-226">You can do so by running the more_activity_data.sql script provided with the samples.</span></span>  
  
 <span data-ttu-id="35661-227">執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。</span><span class="sxs-lookup"><span data-stu-id="35661-227">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span> <span data-ttu-id="35661-228">配接器將繼續輪詢直到按關閉服務主機`<RETURN>`。</span><span class="sxs-lookup"><span data-stu-id="35661-228">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.Adapters.OracleEBS;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace StoredProcPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void  GET_ACTIVITYS(GET_ACTIVITYS request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tProcessed");  
            for (int i = 0; i < request.OUTRECS.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.OUTRECS[i].TID,  
                request.OUTRECS[i].ACCOUNT,  
                request.OUTRECS[i].AMOUNT,  
                request.OUTRECS[i].PROCESSED);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
  
    class PollingCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new PollingCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost serviceHost = null;  
            try  
            {  
                Console.WriteLine("Sample started...");  
                Console.WriteLine("Press any key to start polling...");  
                Console.ReadLine();  
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM ACCOUNTACTIVITY";  
                binding.PollingInput = "<GET_ACTIVITYS xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG'><INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS></GET_ACTIVITYS>";  
                binding.PollingAction = "PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // an InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
  
                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("PollingPackageApis_APPS_ACCOUNT_PKG", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Polling started...");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="35661-229">請參閱</span><span class="sxs-lookup"><span data-stu-id="35661-229">See Also</span></span>  
 [<span data-ttu-id="35661-230">使用 WCF 服務模型輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="35661-230">Poll Oracle E-Business Suite using the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)