---
title: 預存程序使用 WCF 服務模型輪詢 Oracle E-business Suite |Microsoft Docs
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
ms.openlocfilehash: c2d01bcfd2b004042ce69f4843bb9ae7bb2f323f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007407"
---
# <a name="poll-oracle-e-business-suite-using-stored-procedures-with-the-wcf-service-model"></a><span data-ttu-id="427ea-102">預存程序使用 WCF 服務模型輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="427ea-102">Poll Oracle E-Business Suite using stored procedures with the WCF service model</span></span>
<span data-ttu-id="427ea-103">您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來使用預存程序，定期輪詢 Oracle 資料庫接收定期的資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="427ea-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using stored procedures to periodically poll the Oracle database.</span></span> <span data-ttu-id="427ea-104">您可以指定預存程序來輪詢 Oracle 資料庫定期執行配接器輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="427ea-104">You can specify a stored procedure as a polling statement that the adapter executes periodically to poll the Oracle database.</span></span>  

 <span data-ttu-id="427ea-105">若要啟用輪詢，您必須指定特定繫結屬性，本主題中所述。</span><span class="sxs-lookup"><span data-stu-id="427ea-105">To enable polling, you must specify certain binding properties as described in this topic.</span></span>  <span data-ttu-id="427ea-106">如需配接器如何支援輪詢的詳細資訊，請參閱[支援的輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。</span><span class="sxs-lookup"><span data-stu-id="427ea-106">For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  

## <a name="configuring-a-polling-operation-with-oracle-e-business-adapter-binding-properties"></a><span data-ttu-id="427ea-107">使用 Oracle E-business 配接器繫結屬性中設定輪詢作業</span><span class="sxs-lookup"><span data-stu-id="427ea-107">Configuring a Polling Operation with Oracle E-Business Adapter Binding Properties</span></span>  
 <span data-ttu-id="427ea-108">下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，您用來設定配接器接收資料變更訊息。</span><span class="sxs-lookup"><span data-stu-id="427ea-108">The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages.</span></span> <span data-ttu-id="427ea-109">執行輪詢應用程式時，您必須指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-109">You must specify these binding properties while running the polling application.</span></span>  


|         <span data-ttu-id="427ea-110">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="427ea-110">Binding Property</span></span>         |                                                                                                                                                                                                                                                                       <span data-ttu-id="427ea-111">描述</span><span class="sxs-lookup"><span data-stu-id="427ea-111">Description</span></span>                                                                                                                                                                                                                                                                       |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     <span data-ttu-id="427ea-112">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="427ea-112">**InboundOperationType**</span></span>     |                                                                                                                                                                                                                   <span data-ttu-id="427ea-113">指定是否要執行**輪詢**或是**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-113">Specifies whether you want to perform a **Polling** or **Notification** inbound operation.</span></span> <span data-ttu-id="427ea-114">預設值是**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="427ea-114">Default is **Polling**.</span></span>                                                                                                                                                                                                                    |
| <span data-ttu-id="427ea-115">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="427ea-115">**PolledDataAvailableStatement**</span></span> |                                                                                                                                                       <span data-ttu-id="427ea-116">指定配接器執行，以判斷是否有任何資料可供輪詢 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="427ea-116">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="427ea-117">只有當可用的記錄時，預存程序指定**PollingInput**屬性繫結將會執行。</span><span class="sxs-lookup"><span data-stu-id="427ea-117">Only if a record is available, the stored procedure you specified for the **PollingInput** binding property will be executed.</span></span>                                                                                                                                                       |
|       <span data-ttu-id="427ea-118">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="427ea-118">**PollingInterval**</span></span>        |                                           <span data-ttu-id="427ea-119">指定間隔 （秒），此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-119">Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="427ea-120">預設值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="427ea-120">The default is 30 seconds.</span></span> <span data-ttu-id="427ea-121">輪詢間隔會決定後續輪詢間隔的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="427ea-121">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="427ea-122">如果指定的間隔內執行的陳述式，則配接器會睡剩餘的時間間隔中。</span><span class="sxs-lookup"><span data-stu-id="427ea-122">If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval.</span></span>                                            |
|         <span data-ttu-id="427ea-123">**PollingInput**</span><span class="sxs-lookup"><span data-stu-id="427ea-123">**PollingInput**</span></span>         | <span data-ttu-id="427ea-124">指定輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="427ea-124">Specifies the polling statement.</span></span> <span data-ttu-id="427ea-125">若要使用預存程序進行輪詢，您必須指定這個繫結屬性的整個要求訊息。</span><span class="sxs-lookup"><span data-stu-id="427ea-125">To poll using a stored procedure, you must specify the entire request message for this binding property.</span></span> <span data-ttu-id="427ea-126">要求訊息必須相同，您傳送給配接器，叫用預存程序，做為輸出的作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-126">The request message must be the same that you send to the adapter for invoking the stored procedure as an outbound operation.</span></span> <span data-ttu-id="427ea-127">預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="427ea-127">The default is null.</span></span><br /><br /> <span data-ttu-id="427ea-128">您必須指定的值**PollingInput**繫結屬性，來啟用輪詢。</span><span class="sxs-lookup"><span data-stu-id="427ea-128">You must specify a value for **PollingInput** binding property to enable polling.</span></span> <span data-ttu-id="427ea-129">輪詢陳述式在沒有可供輪詢，取決於使用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-129">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span> |
|        <span data-ttu-id="427ea-130">**PollingAction**</span><span class="sxs-lookup"><span data-stu-id="427ea-130">**PollingAction**</span></span>         |                                                                                                                                                          <span data-ttu-id="427ea-131">指定輪詢作業的動作。</span><span class="sxs-lookup"><span data-stu-id="427ea-131">Specifies the action for the polling operation.</span></span> <span data-ttu-id="427ea-132">您可以決定從產生的作業使用的服務介面的輪詢動作[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="427ea-132">You can determine the polling action from the service interface generated for the operation using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>                                                                                                                                                           |
|      <span data-ttu-id="427ea-133">**PostPollStatement**</span><span class="sxs-lookup"><span data-stu-id="427ea-133">**PostPollStatement**</span></span>       |                                                                                                                                                                                                            <span data-ttu-id="427ea-134">指定執行所指定的陳述式之後的陳述式區塊**PollingInput**屬性繫結會執行。</span><span class="sxs-lookup"><span data-stu-id="427ea-134">Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.</span></span>                                                                                                                                                                                                             |
|      <span data-ttu-id="427ea-135">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="427ea-135">**PollWhileDataFound**</span></span>      |                                                                               <span data-ttu-id="427ea-136">指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會忽略的輪詢間隔，並持續執行輪詢陳述式，如果資料可在所輪詢的資料表。</span><span class="sxs-lookup"><span data-stu-id="427ea-136">Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled.</span></span> <span data-ttu-id="427ea-137">如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="427ea-137">If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval.</span></span> <span data-ttu-id="427ea-138">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="427ea-138">Default is false.</span></span>                                                                               |

 <span data-ttu-id="427ea-139">如需這些屬性的更完整說明，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="427ea-139">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="427ea-140">如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來輪詢，請閱讀下列各節。</span><span class="sxs-lookup"><span data-stu-id="427ea-140">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll, read the following sections.</span></span>  

## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="427ea-141">本主題將輪詢的示範</span><span class="sxs-lookup"><span data-stu-id="427ea-141">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="427ea-142">本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援接收資料變更，使用預存程序的訊息，您會使用 GET_ACTIVITYS 預存程序來輪詢 ACCOUNTACTIVITY Oracle 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="427ea-142">In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using stored procedures, you use the GET_ACTIVITYS stored procedure to poll the ACCOUNTACTIVITY table in the Oracle database.</span></span> <span data-ttu-id="427ea-143">這個預存程序可與 ACCOUNT_PKG 封裝。</span><span class="sxs-lookup"><span data-stu-id="427ea-143">This stored procedure is available with the ACCOUNT_PKG package.</span></span> <span data-ttu-id="427ea-144">您可以執行 SQL 指令碼隨附的範例，在資料庫中建立這些物件。</span><span class="sxs-lookup"><span data-stu-id="427ea-144">You can run the SQL scripts provided with the samples to create these objects in the database.</span></span>  

> [!NOTE]
>  <span data-ttu-id="427ea-145">此主題投票中 ACCOUNTACTIVITY 資料表，這基底資料庫建立的資料表執行提供的範例指令碼的範例。</span><span class="sxs-lookup"><span data-stu-id="427ea-145">The example in this topic polls the ACCOUNTACTIVITY table, which is a base database table created by running the scripts provided with the samples.</span></span> <span data-ttu-id="427ea-146">若要輪詢的任何其他資料表，包括介面資料表本主題中所述，您必須執行類似的程序。</span><span class="sxs-lookup"><span data-stu-id="427ea-146">You must perform similar procedures as described in this topic to poll any other table, including interface tables.</span></span>  

 <span data-ttu-id="427ea-147">為了示範輪詢作業，我們執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="427ea-147">To demonstrate a polling operation, we do the following:</span></span>  

-   <span data-ttu-id="427ea-148">指定的 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中資料表輪詢 (ACCOUNTACTIVITY) 有任何資料。</span><span class="sxs-lookup"><span data-stu-id="427ea-148">Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the table being polled (ACCOUNTACTIVITY) has any data.</span></span> <span data-ttu-id="427ea-149">在此範例中，您可以設定為這個繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="427ea-149">In this example, you can set this binding property as:</span></span>  

    ```  
    SELECT COUNT (*) FROM ACCOUNTACTIVITY  
    ```  

     <span data-ttu-id="427ea-150">這可確保當配接器 ACCOUNTACTIVITY 資料表有一些記錄時，才會執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="427ea-150">This ensures that the adapter executes the polling statement only when the ACCOUNTACTIVITY table has some records.</span></span>  

-   <span data-ttu-id="427ea-151">執行預存程序 GET_ACTIVITYS，藉由提供的要求訊息的一部分**PollingInput**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-151">Execute a stored procedure, GET_ACTIVITYS, by providing the request message as part of the **PollingInput** binding property.</span></span> <span data-ttu-id="427ea-152">這個預存程序會擷取 ACCOUNTACTIVITY 資料表中的所有資料列，然後就會從配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="427ea-152">This stored procedure will retrieve all the rows in the ACCOUNTACTIVITY table and you will get a response message from the adapter.</span></span>  

-   <span data-ttu-id="427ea-153">執行一部分的 PL/SQL 區塊**PostPollStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-153">Execute a PL/SQL block as part of the **PostPollStatement** binding property.</span></span> <span data-ttu-id="427ea-154">此陳述式會從 ACCOUNTACTIVITY 資料表移動所有資料到資料庫中的另一個資料表。</span><span class="sxs-lookup"><span data-stu-id="427ea-154">This statement will move all data from ACCOUNTACTIVITY table to another table in the database.</span></span> <span data-ttu-id="427ea-155">發生這種情況，在下一次之後**PollingInput**會執行，它不會擷取任何資料，並因此 GET_ACTIVITYS 預存程序會傳回空白的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="427ea-155">After this happens, the next time **PollingInput** is executed, it will not fetch any data and hence the GET_ACTIVITYS stored procedure will return an empty response message.</span></span>  

-   <span data-ttu-id="427ea-156">更多資料新增至 ACCOUNTACTIVITY 資料表，直到您將繼續收到空的回應訊息，因此您必須重新擴展 ACCOUNTACTIVITY 資料表與新的記錄。</span><span class="sxs-lookup"><span data-stu-id="427ea-156">Until more data is added to the ACCOUNTACTIVITY table, you will continue to get empty response messages so you must repopulate the ACCOUNTACTIVITY table with new records.</span></span> <span data-ttu-id="427ea-157">您可以執行 more_activity_data.sql 指令碼提供範例來這麼做。</span><span class="sxs-lookup"><span data-stu-id="427ea-157">You can do so by running the more_activity_data.sql script provided with the samples.</span></span> <span data-ttu-id="427ea-158">執行此指令碼之後下, 一個輪詢作業會擷取新記錄插入至資料表。</span><span class="sxs-lookup"><span data-stu-id="427ea-158">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span>  

## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="427ea-159">在 WCF 服務模型中設定輪詢</span><span class="sxs-lookup"><span data-stu-id="427ea-159">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="427ea-160">若要使用預存程序進行輪詢[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 WCF 服務模型中，您必須：</span><span class="sxs-lookup"><span data-stu-id="427ea-160">To poll using stored procedures with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with the WCF service model, you must:</span></span>  

- <span data-ttu-id="427ea-161">產生預存程序中使用哪些即將要輪詢的 WCF 服務合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="427ea-161">Generate a WCF service contract (interface) for the stored procedure using which you are going to poll.</span></span> <span data-ttu-id="427ea-162">針對此範例中，您必須產生的 WCF 服務合約**GET_ACTIVITYS**預存程序，做為輸入的作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-162">For this example, you must generate the WCF service contract for the **GET_ACTIVITYS** stored procedure as an inbound operation.</span></span> <span data-ttu-id="427ea-163">若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="427ea-163">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

- <span data-ttu-id="427ea-164">實作此介面的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="427ea-164">Implement a WCF service from this interface.</span></span>  

- <span data-ttu-id="427ea-165">裝載此 WCF 服務，使用服務主機 (**System.ServiceModel.ServiceHost**)。</span><span class="sxs-lookup"><span data-stu-id="427ea-165">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  

## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="427ea-166">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="427ea-166">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="427ea-167">此主題輪詢使用 GET_ACTIVITYS ACCOUNTACTIVITY 資料庫資料表中的範例預存程序。</span><span class="sxs-lookup"><span data-stu-id="427ea-167">The examples in this topic poll the ACCOUNTACTIVITY database table using the GET_ACTIVITYS stored procedure.</span></span> <span data-ttu-id="427ea-168">若要產生的資料表和預存程序的指令碼會提供範例。</span><span class="sxs-lookup"><span data-stu-id="427ea-168">A script to generate the table and the stored procedure is supplied with the samples.</span></span> <span data-ttu-id="427ea-169">如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="427ea-169">For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="427ea-170">範例中， **StoredProcPolling_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="427ea-170">A sample, **StoredProcPolling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  

## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="427ea-171">類別與 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="427ea-171">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="427ea-172">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]來建立 WCF 服務合約 （介面） 和支援類別**GET_ACTIVITYS**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-172">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **GET_ACTIVITYS** inbound operation.</span></span> <span data-ttu-id="427ea-173">如需有關如何產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="427ea-173">For more information about generating a WCF service contract, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  

### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="427ea-174">WCF 服務合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="427ea-174">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="427ea-175">下列程式碼示範 WCF 服務合約 （介面） 產生**GET_ACTIVITYS**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-175">The following code shows the WCF service contract (interface) generated for the **GET_ACTIVITYS** inbound operation.</span></span>  

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

### <a name="the-message-contracts"></a><span data-ttu-id="427ea-176">訊息合約</span><span class="sxs-lookup"><span data-stu-id="427ea-176">The Message Contracts</span></span>  
 <span data-ttu-id="427ea-177">以下是訊息合約**GET_ACTIVITYS**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-177">Following is the message contract for the **GET_ACTIVITYS** inbound operation.</span></span>  

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

### <a name="wcf-service-class"></a><span data-ttu-id="427ea-178">WCF 服務類別</span><span class="sxs-lookup"><span data-stu-id="427ea-178">WCF Service Class</span></span>  
 <span data-ttu-id="427ea-179">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生已實作服務合約 （介面） 的 WCF 服務類別的虛設常式檔案。</span><span class="sxs-lookup"><span data-stu-id="427ea-179">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="427ea-180">OracleEBSBindingService.cs 為檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="427ea-180">The name of the file is OracleEBSBindingService.cs.</span></span> <span data-ttu-id="427ea-181">您可以插入邏輯來處理**GET_ACTIVITYS**直接將此類別的作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-181">You can insert the logic to process the **GET_ACTIVITYS** operation directly into this class.</span></span> <span data-ttu-id="427ea-182">下列程式碼會顯示所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="427ea-182">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  

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

## <a name="receiving-inbound-messages-for-polling-using-a-stored-procedure"></a><span data-ttu-id="427ea-183">用於輪詢使用預存程序接收內送的訊息</span><span class="sxs-lookup"><span data-stu-id="427ea-183">Receiving Inbound Messages For Polling Using a Stored Procedure</span></span>  
 <span data-ttu-id="427ea-184">本節說明如何撰寫.NET 應用程式以接收輸入的輪詢訊息使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="427ea-184">This section provides instructions on how to write a .NET application to receive inbound polling messages using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  

#### <a name="to-receive-polling-messages-using-a-stored-procedure"></a><span data-ttu-id="427ea-185">若要接收輪詢訊息使用的預存程序</span><span class="sxs-lookup"><span data-stu-id="427ea-185">To receive polling messages using a stored procedure</span></span>  

1. <span data-ttu-id="427ea-186">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生的 WCF 服務合約 （介面） 和 helper 類別**GET_ACTIVITYS**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-186">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **GET_ACTIVITYS** inbound operation.</span></span> <span data-ttu-id="427ea-187">如需詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="427ea-187">For more information, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span> <span data-ttu-id="427ea-188">產生服務合約和協助程式類別時，您可以選擇指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-188">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="427ea-189">這可確保它們已正確設定在產生的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="427ea-189">This guarantees that they are properly set in the generated configuration file.</span></span>  

2. <span data-ttu-id="427ea-190">實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="427ea-190">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="427ea-191">**GET_ACTIVITYS**此類別的方法可以擲回例外狀況中止輪詢交易，處理從收到的資料時發生錯誤**GET_ACTIVITYS**作業; 否則為此方法不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="427ea-191">The **GET_ACTIVITYS** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **GET_ACTIVITYS** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="427ea-192">WCF 服務類別必須屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="427ea-192">You must attribute the WCF service class as follows:</span></span>  

   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  

    <span data-ttu-id="427ea-193">內**GET_ACTIVITYS**方法中，您可以直接實作應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="427ea-193">Within the **GET_ACTIVITYS** method, you can implement your application logic directly.</span></span> <span data-ttu-id="427ea-194">這個類別可以位於 OracleEBSBindingService.cs。</span><span class="sxs-lookup"><span data-stu-id="427ea-194">This class can be found in OracleEBSBindingService.cs.</span></span> <span data-ttu-id="427ea-195">此程式碼，在此範例中的子類別**OracleEBSBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="427ea-195">This code in this example sub-classes the **OracleEBSBindingService** class.</span></span> <span data-ttu-id="427ea-196">在此程式碼中，收到輪詢訊息，並寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="427ea-196">In this code, the polling message received and is written to the console.</span></span>  

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

3. <span data-ttu-id="427ea-197">您必須實作下列類別，以避免將認證傳遞做為 URI 的一部分。</span><span class="sxs-lookup"><span data-stu-id="427ea-197">You must implement the following class to avoid passing credentials as part of the URI.</span></span> <span data-ttu-id="427ea-198">在應用程式的後半部，您將會具現化這個類別，以傳遞的認證。</span><span class="sxs-lookup"><span data-stu-id="427ea-198">In the latter part of the application, you will instantiate this class to pass on the credentials.</span></span>  

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

4. <span data-ttu-id="427ea-199">建立**OracleEBSBinding**和設定輪詢作業藉由指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-199">Create an **OracleEBSBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="427ea-200">在程式碼中明確或是宣告式組態中，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="427ea-200">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="427ea-201">至少，您必須指定**InboundOperationType**， **PolledDataAvailableStatement**， **PollingInput**，和**PollingAction**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-201">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, and **PollingAction** binding properties.</span></span>  

   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   binding.InboundOperationType = InboundOperation.Polling;  
   binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM ACCOUNTACTIVITY";  
   binding.PollingInput = "<GET_ACTIVITYS xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/PackageApis/APPS/ACCOUNT_PKG'><INRECS>OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY</INRECS></GET_ACTIVITYS>";  
   binding.PollingAction = "PollingPackageApis/APPS/ACCOUNT_PKG/GET_ACTIVITYS";  
   binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
   ```  

   > [!NOTE]
   >  <span data-ttu-id="427ea-202">請注意，值**PollingInput**繫結屬性包含要求訊息來叫用**GET_ACTIVITYS**預存程序，做為輸出的作業。</span><span class="sxs-lookup"><span data-stu-id="427ea-202">Note that the value for the **PollingInput** binding property contains the request message for invoking the **GET_ACTIVITYS** stored procedure as an outbound operation.</span></span>  

   > [!IMPORTANT]
   >  <span data-ttu-id="427ea-203">在此範例中，因為您正在輪詢資料庫資料表時，您不需要設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="427ea-203">In this example, because you are polling a database table, you do not need to set the applications context.</span></span> <span data-ttu-id="427ea-204">不過，如果您已輪詢介面資料表，您必須設定應用程式內容藉由指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="427ea-204">However, if you were polling an interface table, you must set the applications context by specifying the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="427ea-205">如需有關應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="427ea-205">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  

5. <span data-ttu-id="427ea-206">指定 Oracle E-business Suite 的認證，藉由執行個體化**PollingCredentials**您在步驟 3 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="427ea-206">Specify Oracle E-Business Suite credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  

   ```  
   PollingCredentials credentials = new PollingCredentials();  
   credentials.UserName.UserName = "<Enter user name here>";  
   credentials.UserName.Password = "<Enter password here>";  
   ```  

6. <span data-ttu-id="427ea-207">建立在步驟 2 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="427ea-207">Create an instance of the WCF service created in step 2.</span></span>  

   ```  
   // create service instance  
   PollingService service = new PollingService();  
   ```  

7. <span data-ttu-id="427ea-208">建立的執行個體**System.ServiceModel.ServiceHost**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="427ea-208">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="427ea-209">如果指定，基底的連線 URI 不能包含的輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="427ea-209">The base connection URI cannot contain the inbound ID, if specified.</span></span> <span data-ttu-id="427ea-210">您也必須在此傳遞認證。</span><span class="sxs-lookup"><span data-stu-id="427ea-210">You must also pass the credentials here.</span></span>  

   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
   ServiceHost serviceHost = new ServiceHost(service, baseUri);  
   serviceHost.Description.Behaviors.Add(credentials);  

   ```  

8. <span data-ttu-id="427ea-211">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="427ea-211">Add a service endpoint to the service host.</span></span> <span data-ttu-id="427ea-212">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="427ea-212">To do this:</span></span>  

   -   <span data-ttu-id="427ea-213">使用在步驟 4 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="427ea-213">Use the binding created in step 4.</span></span>  

   -   <span data-ttu-id="427ea-214">指定連線 URI，其中包含認證並在必要時輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="427ea-214">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  

   -   <span data-ttu-id="427ea-215">為 「 PollingPackageApis_APPS_ACCOUNT_PKG"輪詢 MS_SAMPLE_EMPLOYEE 介面資料表中指定的合約。</span><span class="sxs-lookup"><span data-stu-id="427ea-215">Specify the contract as "PollingPackageApis_APPS_ACCOUNT_PKG" to poll the MS_SAMPLE_EMPLOYEE interface table.</span></span>  

   ```  
   // Add service endpoint: be sure to specify PollingPackageApis_APPS_ACCOUNT_PKG as the contract  
   Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
   serviceHost.AddServiceEndpoint("PollingPackageApis_APPS_ACCOUNT_PKG", binding, ConnectionUri);  
   ```  

9. <span data-ttu-id="427ea-216">若要收到輪詢資料，請開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="427ea-216">To receive polling data, open the service host.</span></span> <span data-ttu-id="427ea-217">每當查詢傳回結果集時，配接器會傳回資料。</span><span class="sxs-lookup"><span data-stu-id="427ea-217">The adapter will return data whenever the query returns a result set.</span></span>  

    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  

10. <span data-ttu-id="427ea-218">若要終止輪詢，關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="427ea-218">To terminate polling, close the service host.</span></span>  

    > [!IMPORTANT]
    >  <span data-ttu-id="427ea-219">配接器將繼續輪詢直到關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="427ea-219">The adapter will continue to poll until the service host is closed.</span></span>  

    ```  
    serviceHost.Close();  
    ```  

### <a name="example"></a><span data-ttu-id="427ea-220">範例</span><span class="sxs-lookup"><span data-stu-id="427ea-220">Example</span></span>  
 <span data-ttu-id="427ea-221">下列範例會顯示輪詢應用程式會輪詢使用 GET_ACTIVITYS ACCOUNTACTIVITY 資料庫資料表的預存程序。</span><span class="sxs-lookup"><span data-stu-id="427ea-221">The following example shows a polling application that polls the ACCOUNTACTIVITY database table using the GET_ACTIVITYS stored procedure.</span></span> <span data-ttu-id="427ea-222">**PollingInput**繫結屬性包含要叫用從 ACCOUNTACTIVITY 資料表讀取所有資料 GET_ACTIVITYS 預存程序的要求訊息和後輪詢陳述式會從 ACCOUNTACTIVITY 移動所有資料ACTIVITYHISTORY 資料表。</span><span class="sxs-lookup"><span data-stu-id="427ea-222">The **PollingInput** binding property contains the request message to invoke the GET_ACTIVITYS stored procedure that reads all the data from the ACCOUNTACTIVITY table and the post poll statement moves all the data from ACCOUNTACTIVITY to ACTIVITYHISTORY table.</span></span>  

 <span data-ttu-id="427ea-223">第一次輪詢訊息提供 ACCOUNTACTIVITY 資料表中的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="427ea-223">The first polling message gives all the records from the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="427ea-224">後續輪詢訊息不會包含任何記錄，因為後輪詢陳述式會刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="427ea-224">Subsequent polling messages will not contain any records because the post poll statement deletes the records.</span></span> <span data-ttu-id="427ea-225">更多資料新增至 ACCOUNTACTIVITY 資料表之前則不會收到任何輪詢訊息讓您必須重新擴展 ACCOUNTACTIVITY 資料表與新的記錄。</span><span class="sxs-lookup"><span data-stu-id="427ea-225">Until more data is added to the ACCOUNTACTIVITY table, you will not get any polling messages so you must repopulate the ACCOUNTACTIVITY table with new records.</span></span> <span data-ttu-id="427ea-226">您可以執行 more_activity_data.sql 指令碼提供範例來這麼做。</span><span class="sxs-lookup"><span data-stu-id="427ea-226">You can do so by running the more_activity_data.sql script provided with the samples.</span></span>  

 <span data-ttu-id="427ea-227">執行此指令碼之後下, 一個輪詢作業會擷取新記錄插入至資料表。</span><span class="sxs-lookup"><span data-stu-id="427ea-227">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span> <span data-ttu-id="427ea-228">配接器將繼續輪詢直到按關閉服務主機`<RETURN>`。</span><span class="sxs-lookup"><span data-stu-id="427ea-228">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="427ea-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="427ea-229">See Also</span></span>  
 [<span data-ttu-id="427ea-230">使用 WCF 服務模型輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="427ea-230">Poll Oracle E-Business Suite using the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)