---
title: "使用 WCF 服務模型中的 SELECT 陳述式輪詢 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 521d58e4-73b1-48a8-9a0a-9e733386c1b5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2cac950ced0fb0d7133e99bc3d12699f9379bcb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-select-statement-with-the-wcf-service-model"></a><span data-ttu-id="f0748-102">輪詢 Oracle E-business Suite 與 WCF 服務模型中使用 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0748-102">Poll Oracle E-Business Suite using SELECT statement with the WCF service model</span></span>
<span data-ttu-id="f0748-103">您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收定期的資料變更訊息，若要連續輪詢介面資料表使用 SELECT 陳述式，介面檢視、 資料表以及 Oracle E-business Suite 中的檢視。</span><span class="sxs-lookup"><span data-stu-id="f0748-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using a SELECT statement to continuously poll the interface tables, interface views, tables and views in Oracle E-Business Suite.</span></span> <span data-ttu-id="f0748-104">您可以指定 SELECT 陳述式為輪詢 Oracle E-business Suite 會定期執行配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0748-104">You can specify a SELECT statement as a polling statement that the adapter executes periodically to poll Oracle E-Business Suite.</span></span> <span data-ttu-id="f0748-105">您也可以指定後續輪詢 PL/SQL 程式碼區塊後輪詢陳述式執行配接器。</span><span class="sxs-lookup"><span data-stu-id="f0748-105">You can also specify a post-poll PL/SQL code block that the adapter executes after the polling statement is executed.</span></span>  
  
 <span data-ttu-id="f0748-106">若要啟用輪詢，您必須指定特定繫結屬性，本主題中所述。</span><span class="sxs-lookup"><span data-stu-id="f0748-106">To enable polling, you must specify certain binding properties as described in this topic.</span></span>  <span data-ttu-id="f0748-107">如需如何配接器支援在輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。</span><span class="sxs-lookup"><span data-stu-id="f0748-107">For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a><span data-ttu-id="f0748-108">使用 Oracle E-business Suite 配接器繫結屬性中設定輪詢作業</span><span class="sxs-lookup"><span data-stu-id="f0748-108">Configuring a Polling Operation with Oracle E-Business Suite Adapter Binding Properties</span></span>  
 <span data-ttu-id="f0748-109">下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，您用來設定配接器接收的資料變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="f0748-109">The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data change messages.</span></span> <span data-ttu-id="f0748-110">執行輪詢應用程式時，您必須指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-110">You must specify these binding properties while running the polling application.</span></span>  
  
|<span data-ttu-id="f0748-111">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="f0748-111">Binding Property</span></span>|<span data-ttu-id="f0748-112">Description</span><span class="sxs-lookup"><span data-stu-id="f0748-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="f0748-113">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="f0748-113">**InboundOperationType**</span></span>|<span data-ttu-id="f0748-114">指定您是否要執行**輪詢**或**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="f0748-114">Specifies whether you want to perform **Polling** or **Notification** inbound operation.</span></span> <span data-ttu-id="f0748-115">預設值是**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="f0748-115">Default is **Polling**.</span></span>|  
|<span data-ttu-id="f0748-116">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="f0748-116">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="f0748-117">指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。</span><span class="sxs-lookup"><span data-stu-id="f0748-117">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="f0748-118">只有當可用的記錄時，SELECT 陳述式您為指定**PollingInput**繫結屬性將會執行。</span><span class="sxs-lookup"><span data-stu-id="f0748-118">Only if a record is available, the SELECT statement you specify for the **PollingInput** binding property will be executed.</span></span>|  
|<span data-ttu-id="f0748-119">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="f0748-119">**PollingInterval**</span></span>|<span data-ttu-id="f0748-120">指定間隔，以秒為單位，此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-120">Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="f0748-121">預設值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="f0748-121">The default is 30 seconds.</span></span> <span data-ttu-id="f0748-122">輪詢間隔會決定後續輪詢間隔時間。</span><span class="sxs-lookup"><span data-stu-id="f0748-122">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="f0748-123">如果指定的間隔內執行的陳述式，則配接器進入睡眠狀態的剩餘時間間隔中。</span><span class="sxs-lookup"><span data-stu-id="f0748-123">If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="f0748-124">**PollingInput**</span><span class="sxs-lookup"><span data-stu-id="f0748-124">**PollingInput**</span></span>|<span data-ttu-id="f0748-125">指定輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0748-125">Specifies the polling statement.</span></span> <span data-ttu-id="f0748-126">若要輪詢使用 SELECT 陳述式，您必須指定這個繫結屬性的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0748-126">To poll using a SELECT statement, you must specify a SELECT statement for this binding property.</span></span> <span data-ttu-id="f0748-127">預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="f0748-127">The default is null.</span></span><br /><br /> <span data-ttu-id="f0748-128">您必須指定的值**PollingInput**繫結內容來啟用輪詢。</span><span class="sxs-lookup"><span data-stu-id="f0748-128">You must specify a value for **PollingInput** binding property to enable polling.</span></span> <span data-ttu-id="f0748-129">輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-129">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span>|  
|<span data-ttu-id="f0748-130">**PollingAction**</span><span class="sxs-lookup"><span data-stu-id="f0748-130">**PollingAction**</span></span>|<span data-ttu-id="f0748-131">指定輪詢作業的動作。</span><span class="sxs-lookup"><span data-stu-id="f0748-131">Specifies the action for the polling operation.</span></span> <span data-ttu-id="f0748-132">您可以決定產生的作業使用的服務介面的輪詢動作[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f0748-132">You can determine the polling action from the service interface generated for the operation using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>|  
|<span data-ttu-id="f0748-133">**PostPollStatement**</span><span class="sxs-lookup"><span data-stu-id="f0748-133">**PostPollStatement**</span></span>|<span data-ttu-id="f0748-134">指定執行所指定的陳述式之後的陳述式區塊**PollingInput**執行繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-134">Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.</span></span>|  
|<span data-ttu-id="f0748-135">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="f0748-135">**PollWhileDataFound**</span></span>|<span data-ttu-id="f0748-136">指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]忽略的輪詢間隔，並持續執行輪詢陳述式，如果輪詢資料表中的可用資料。</span><span class="sxs-lookup"><span data-stu-id="f0748-136">Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled.</span></span> <span data-ttu-id="f0748-137">如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0748-137">If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval.</span></span> <span data-ttu-id="f0748-138">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="f0748-138">Default is false.</span></span>|  
  
 <span data-ttu-id="f0748-139">如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f0748-139">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="f0748-140">如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]進一步來輪詢 Oracle 資料庫，請閱讀。</span><span class="sxs-lookup"><span data-stu-id="f0748-140">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database, read further.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="f0748-141">本主題示範輪詢的方式</span><span class="sxs-lookup"><span data-stu-id="f0748-141">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="f0748-142">本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援接收資料變更使用 SELECT 陳述式的訊息，請您輪詢**MS_SAMPLE_EMPLOYEE**介面中的資料表**應用程式物件程式庫**應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0748-142">In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using SELECT statements, you poll the **MS_SAMPLE_EMPLOYEE** interface table in the **Application Object Library** application.</span></span> <span data-ttu-id="f0748-143">當您執行範例建立 Oracle E-business Suite 中的這些物件提供的 create_apps_artifacts.sql 指令碼時，會建立此資料表。</span><span class="sxs-lookup"><span data-stu-id="f0748-143">This table is created when you run the create_apps_artifacts.sql script provided with the samples to create these objects in Oracle E-Business Suite.</span></span>  
  
 <span data-ttu-id="f0748-144">若要示範輪詢作業，我們執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f0748-144">To demonstrate a polling operation, we do the following:</span></span>  
  
-   <span data-ttu-id="f0748-145">指定 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中介面資料表輪詢 (MS_SAMPLE_EMPLOYEE) 有任何資料。</span><span class="sxs-lookup"><span data-stu-id="f0748-145">Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the interface table being polled (MS_SAMPLE_EMPLOYEE) has any data.</span></span> <span data-ttu-id="f0748-146">在此範例中，您可以設定為這個繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="f0748-146">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     <span data-ttu-id="f0748-147">這可確保當配接器 MS_SAMPLE_EMPLOYEE 介面資料表具有一些記錄時才會執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0748-147">This ensures that the adapter executes the polling statement only when the MS_SAMPLE_EMPLOYEE interface table has some records.</span></span>  
  
-   <span data-ttu-id="f0748-148">指定 SELECT 陳述式**PollingInput**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-148">Specify a SELECT statement for the **PollingInput** binding property.</span></span> <span data-ttu-id="f0748-149">此陳述式擷取 MS_SAMPLE_EMPLOYEE 介面資料表中的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="f0748-149">This statement retrieves all the rows in the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="f0748-150">在此範例中，您可以設定為這個繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="f0748-150">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f0748-151">FOR UPDATE 子句用於 SELECT 陳述式的相關資訊，請參閱[從 Oracle E-business Suite 接收輪詢基礎資料變更訊息](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="f0748-151">For information about the FOR UPDATE clause used in the SELECT statement, see [Receive polling-based data-changed messages from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).</span></span>  
  
-   <span data-ttu-id="f0748-152">指定 DELETE 陳述式的一部分**PostPollStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-152">Specify a DELETE statement as part of the **PostPollStatement** binding property.</span></span> <span data-ttu-id="f0748-153">這個陳述式會從 MS_SAMPLE_EMPLOYEE 介面資料表刪除所有資料。</span><span class="sxs-lookup"><span data-stu-id="f0748-153">This statement will delete all data from MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="f0748-154">在此範例中，您可以設定為這個繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="f0748-154">In this example, you can set this binding property as:</span></span>  
  
    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     <span data-ttu-id="f0748-155">發生這種情況之後下, 一次針對指定的陳述式**PollingInput**將會執行，它將會不提取任何資料。</span><span class="sxs-lookup"><span data-stu-id="f0748-155">After this happens, the next time the statement specified for **PollingInput** will be executed, it will not fetch any data.</span></span>  
  
-   <span data-ttu-id="f0748-156">更多資料加入到 MS_SAMPLE_EMPLOYEE 介面資料表之前, 則不會收到任何輪詢訊息，您必須重新擴展 MS_SAMPLE_EMPLOYEE 介面資料表與新的記錄。</span><span class="sxs-lookup"><span data-stu-id="f0748-156">Until more data is added to the MS_SAMPLE_EMPLOYEE interface table, you will not get any polling messages so you must repopulate the MS_SAMPLE_EMPLOYEE interface table with new records.</span></span> <span data-ttu-id="f0748-157">您可以藉由執行範例所提供的 insert_apps_data.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="f0748-157">You can do so by running the insert_apps_data.sql script provided with the samples.</span></span> <span data-ttu-id="f0748-158">執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。</span><span class="sxs-lookup"><span data-stu-id="f0748-158">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span>  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="f0748-159">在 WCF 服務模型中設定輪詢</span><span class="sxs-lookup"><span data-stu-id="f0748-159">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="f0748-160">若要輪詢介面資料表使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 WCF 服務模型中，您必須：</span><span class="sxs-lookup"><span data-stu-id="f0748-160">To poll an interface table using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="f0748-161">產生 WCF 服務合約 （介面）**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="f0748-161">Generate a WCF service contract (interface) for the **Poll** operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="f0748-162">若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f0748-162">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="f0748-163">實作這個介面從 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="f0748-163">Implement a WCF service from this interface.</span></span>  
  
-   <span data-ttu-id="f0748-164">裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。</span><span class="sxs-lookup"><span data-stu-id="f0748-164">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="f0748-165">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="f0748-165">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="f0748-166">本主題中的範例輪詢 MS_SAMPLE_EMPLOYEE 介面資料表。</span><span class="sxs-lookup"><span data-stu-id="f0748-166">The examples in this topic poll the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="f0748-167">若要產生資料表的指令碼會提供範例。</span><span class="sxs-lookup"><span data-stu-id="f0748-167">A script to generate the table is supplied with the samples.</span></span> <span data-ttu-id="f0748-168">如需這些範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f0748-168">For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="f0748-169">範例中， **SelectPolling_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="f0748-169">A sample, **SelectPolling_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="f0748-170">WCF 服務合約和類別</span><span class="sxs-lookup"><span data-stu-id="f0748-170">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="f0748-171">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]建立 WCF 服務合約 （介面） 和支援類別**輪詢**作業。</span><span class="sxs-lookup"><span data-stu-id="f0748-171">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Polling** operation.</span></span> <span data-ttu-id="f0748-172">如需產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="f0748-172">For more information about generating a WCF service contract, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="f0748-173">WCF 服務合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="f0748-173">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="f0748-174">下列程式碼顯示產生的 WCF 服務合約 （介面）**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="f0748-174">The following code shows the WCF service contract (interface) generated for the **Poll** operation on MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/", ConfigurationName="InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE")]  
public interface InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE) of message Poll   
    // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE")]  
    void Poll(Poll request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="f0748-175">訊息合約</span><span class="sxs-lookup"><span data-stu-id="f0748-175">The Message Contracts</span></span>  
 <span data-ttu-id="f0748-176">以下是訊息合約**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="f0748-176">Following is the message contract for the **Poll** operation on MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Poll", WrapperNamespace="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE" +  
    "_EMPLOYEE", IsWrapped=true)]  
public partial class Poll {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE" +  
        "_EMPLOYEE", Order=0)]  
    public schemas.microsoft.com.OracleEBS._2008._05.TableViewRecord.APPS.MS_SAMPLE_EMPLOYEE.SelectRecord[] DATA;  
  
    public Poll() {  
    }  
  
    public Poll(schemas.microsoft.com.OracleEBS._2008._05.TableViewRecord.APPS.MS_SAMPLE_EMPLOYEE.SelectRecord[] DATA) {  
        this.DATA = DATA;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="f0748-177">WCF 服務類別</span><span class="sxs-lookup"><span data-stu-id="f0748-177">WCF Service Class</span></span>  
 <span data-ttu-id="f0748-178">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生虛設常式實作的服務合約 （介面） 的 WCF 服務類別的檔案。</span><span class="sxs-lookup"><span data-stu-id="f0748-178">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="f0748-179">檔案的名稱是 OracleEBSBindingService.cs。</span><span class="sxs-lookup"><span data-stu-id="f0748-179">The name of the file is OracleEBSBindingService.cs.</span></span> <span data-ttu-id="f0748-180">您可以插入要處理邏輯**輪詢**直接將這個類別的作業。</span><span class="sxs-lookup"><span data-stu-id="f0748-180">You can insert the logic to process the **Poll** operation directly into this class.</span></span> <span data-ttu-id="f0748-181">下列程式碼將示範所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f0748-181">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace OracleEBSBindingNamespace {  
  
    public class OracleEBSBindingService : InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE) of message Poll   
        // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
        public virtual void Poll(Poll request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-inbound-messages-for-the-poll-operation-using-a-select-statement"></a><span data-ttu-id="f0748-182">使用 SELECT 陳述式的輪詢作業接收內送的訊息</span><span class="sxs-lookup"><span data-stu-id="f0748-182">Receiving Inbound Messages for the Poll Operation Using a SELECT Statement</span></span>  
 <span data-ttu-id="f0748-183">本節說明如何撰寫.NET 應用程式來接收傳入的輪詢訊息使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f0748-183">This section provides instructions on how to write a .NET application to receive inbound polling messages using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-using-a-select-statement"></a><span data-ttu-id="f0748-184">若要接收輪詢訊息使用 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0748-184">To receive polling messages using a SELECT statement</span></span>  
  
1.  <span data-ttu-id="f0748-185">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 服務合約 （介面） 和協助程式類別，如**輪詢**MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="f0748-185">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Poll** operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="f0748-186">如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="f0748-186">For more information, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span> <span data-ttu-id="f0748-187">您可以選擇性地產生服務合約和協助程式類別時指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-187">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="f0748-188">這可確保它們已正確設定在產生的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="f0748-188">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="f0748-189">實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="f0748-189">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="f0748-190">**輪詢**這個類別的方法可以擲回例外狀況中止輪詢交易，處理從接收的資料發生錯誤**輪詢**作業; 否則此方法並不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="f0748-190">The **Poll** method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the **Poll** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="f0748-191">您必須屬性 WCF 服務類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f0748-191">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="f0748-192">內**輪詢**方法，您可以直接實作應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="f0748-192">Within the **Poll** method, you can implement your application logic directly.</span></span> <span data-ttu-id="f0748-193">這個類別可以 OracleEBSBindingService.cs 中找到。</span><span class="sxs-lookup"><span data-stu-id="f0748-193">This class can be found in OracleEBSBindingService.cs.</span></span> <span data-ttu-id="f0748-194">這段程式碼，在此範例中的子類別**OracleEBSBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="f0748-194">This code in this example sub-classes the **OracleEBSBindingService** class.</span></span> <span data-ttu-id="f0748-195">在此程式碼中，接收輪詢訊息，並寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="f0748-195">In this code, the polling message received and is written to the console.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Poll(Poll request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Emp No\tName\tDesignation\tSalary");  
            for (int i = 0; i < request.DATA.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.DATA[i].EMP_NO,  
                request.DATA[i].NAME,  
                request.DATA[i].DESIGNATION,  
                request.DATA[i].SALARY);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="f0748-196">您必須實作下列類別，以避免將認證傳遞做為 URI 的一部分。</span><span class="sxs-lookup"><span data-stu-id="f0748-196">You must implement the following class to avoid passing credentials as part of the URI.</span></span> <span data-ttu-id="f0748-197">在應用程式的第二個部分中，您會具現化這個類別，以傳遞的認證。</span><span class="sxs-lookup"><span data-stu-id="f0748-197">In the latter part of the application, you will instantiate this class to pass on the credentials.</span></span>  
  
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
  
4.  <span data-ttu-id="f0748-198">建立**OracleEBSBinding**和設定輪詢作業藉由指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-198">Create an **OracleEBSBinding** and configure the polling operation by specifying the binding properties.</span></span> <span data-ttu-id="f0748-199">您可以在程式碼中明確或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="f0748-199">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="f0748-200">最少，您必須指定**InboundOperationType**， **PolledDataAvailableStatement**， **PollingInput**，和**PollingAction**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f0748-200">At a minimum, you must specify the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, and **PollingAction** binding properties.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
    binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
    binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
    binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
    ```  
  
5.  <span data-ttu-id="f0748-201">因為您正在輪詢介面資料表，您也必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="f0748-201">Because you are polling an interface table, you must also set the applications context.</span></span> <span data-ttu-id="f0748-202">如需應用程式內容和設定應用程式內容所需的繫結屬性的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="f0748-202">For more information about application context and the binding properties required for setting application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
6.  <span data-ttu-id="f0748-203">藉由執行個體化指定 Oracle E-business Suite 認證**PollingCredentials**您在步驟 3 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="f0748-203">Specify Oracle E-Business Suite credentials by instantiating the **PollingCredentials** class you created in Step 3.</span></span>  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
7.  <span data-ttu-id="f0748-204">建立在步驟 2 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f0748-204">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
8.  <span data-ttu-id="f0748-205">建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="f0748-205">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="f0748-206">如果指定基底的連線 URI 不能包含輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f0748-206">The base connection URI cannot contain the inbound ID, if specified.</span></span> <span data-ttu-id="f0748-207">您也必須將認證傳遞這裡。</span><span class="sxs-lookup"><span data-stu-id="f0748-207">You must also pass the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
9. <span data-ttu-id="f0748-208">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="f0748-208">Add a service endpoint to the service host.</span></span> <span data-ttu-id="f0748-209">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="f0748-209">To do this:</span></span>  
  
    -   <span data-ttu-id="f0748-210">使用步驟 4 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="f0748-210">Use the binding created in step 4.</span></span>  
  
    -   <span data-ttu-id="f0748-211">指定連線 URI，其中包含認證並在必要時輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f0748-211">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="f0748-212">為 「 InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE"輪詢 MS_SAMPLE_EMPLOYEE 介面資料表中指定的合約。</span><span class="sxs-lookup"><span data-stu-id="f0748-212">Specify the contract as "InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE" to poll the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE as the contract  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    serviceHost.AddServiceEndpoint("InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE", binding, ConnectionUri);  
    ```  
  
10. <span data-ttu-id="f0748-213">若要收到輪詢資料，請開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="f0748-213">To receive polling data, open the service host.</span></span> <span data-ttu-id="f0748-214">每當查詢會傳回結果集時，配接器會傳回資料。</span><span class="sxs-lookup"><span data-stu-id="f0748-214">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
11. <span data-ttu-id="f0748-215">若要終止輪詢，關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="f0748-215">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f0748-216">配接器將會繼續輪詢直到關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="f0748-216">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="f0748-217">範例</span><span class="sxs-lookup"><span data-stu-id="f0748-217">Example</span></span>  
 <span data-ttu-id="f0748-218">下列範例會示範輪詢 MS_SAMPLE_EMPLOYEE 介面資料表輪詢應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0748-218">The following example shows a polling application that polls the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="f0748-219">**PollingInput**屬性包含從 MS_SAMPLE_EMPLOYEE 資料表讀取所有資料的 select 陳述式和後輪詢陳述式會從相同的資料表刪除所有資料。</span><span class="sxs-lookup"><span data-stu-id="f0748-219">The **PollingInput** property contains the select statement that reads all the data from the MS_SAMPLE_EMPLOYEE table and the post poll statement deletes all the data from the same table.</span></span> <span data-ttu-id="f0748-220">第一個輪詢訊息會提供從 MS_SAMPLE_EMPLOYEE 介面資料表的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="f0748-220">The first polling message gives all the records from the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="f0748-221">後續的輪詢訊息不會包含任何記錄，因為後輪詢陳述式會刪除的記錄。</span><span class="sxs-lookup"><span data-stu-id="f0748-221">Subsequent polling messages will not contain any records because the post poll statement deletes the records.</span></span> <span data-ttu-id="f0748-222">更多資料加入到 MS_SAMPLE_EMPLOYEE 介面資料表之前, 不會收到任何輪詢訊息。</span><span class="sxs-lookup"><span data-stu-id="f0748-222">Until more data is added to the MS_SAMPLE_EMPLOYEE interface table, you will not get any polling messages.</span></span> <span data-ttu-id="f0748-223">因此，您必須重新擴展 MS_SAMPLE_EMPLOYEE 介面資料表與新的記錄。</span><span class="sxs-lookup"><span data-stu-id="f0748-223">So, you must repopulate the MS_SAMPLE_EMPLOYEE interface table with new records.</span></span> <span data-ttu-id="f0748-224">您可以藉由執行範例所提供的 insert_apps_data.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="f0748-224">You can do so by running the insert_apps_data.sql script provided with the samples.</span></span> <span data-ttu-id="f0748-225">執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。</span><span class="sxs-lookup"><span data-stu-id="f0748-225">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span> <span data-ttu-id="f0748-226">配接器將繼續輪詢直到按關閉服務主機`<RETURN>`。</span><span class="sxs-lookup"><span data-stu-id="f0748-226">The adapter will continue to poll until you close the service host by pressing `<RETURN>`.</span></span>  
  
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
  
namespace SelectPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Poll(Poll request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Emp No\tName\tDesignation\tSalary");  
            for (int i = 0; i < request.DATA.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.DATA[i].EMP_NO,  
                request.DATA[i].NAME,  
                request.DATA[i].DESIGNATION,  
                request.DATA[i].SALARY);  
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
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
                binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
                binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
                binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
                binding.OracleUserName = "myOracleEBSUserName";  
                binding.OraclePassword = "myOracleEBSPassword";  
                binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
  
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
                serviceHost.AddServiceEndpoint("InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE", binding, ConnectionUri);  
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
  
## <a name="see-also"></a><span data-ttu-id="f0748-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0748-227">See Also</span></span>  
 [<span data-ttu-id="f0748-228">使用 WCF 服務模型輪詢 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="f0748-228">Poll Oracle E-Business Suite using the WCF service model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)