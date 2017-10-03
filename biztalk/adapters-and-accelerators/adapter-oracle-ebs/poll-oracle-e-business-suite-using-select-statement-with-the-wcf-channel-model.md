---
title: "使用 SELECT 陳述式搭配 WCF 通道模型輪詢 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 495b9010-856f-4782-bd19-1522bc3eb950
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71f689b035f926e0fd5bbdaa159e1450fbad92b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model"></a><span data-ttu-id="1ae1d-102">輪詢 Oracle E-business Suite 搭配 WCF 通道模型中使用 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="1ae1d-102">Poll Oracle E-Business Suite using SELECT statement with the WCF channel model</span></span>
<span data-ttu-id="1ae1d-103">您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收定期的資料變更訊息，若要連續輪詢介面資料表使用 SELECT 陳述式，介面檢視、 資料表以及 Oracle E-business Suite 中的檢視。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-103">You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using a SELECT statement to continuously poll the interface tables, interface views, tables and views in Oracle E-Business Suite.</span></span> <span data-ttu-id="1ae1d-104">您可以指定 SELECT 陳述式為輪詢 Oracle E-business Suite 會定期執行配接器的輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-104">You can specify a SELECT statement as a polling statement that the adapter executes periodically to poll Oracle E-Business Suite.</span></span> <span data-ttu-id="1ae1d-105">您也可以指定後續輪詢 PL/SQL 程式碼區塊後輪詢陳述式執行配接器。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-105">You can also specify a post-poll PL/SQL code block that the adapter executes after the polling statement is executed.</span></span>  
  
 <span data-ttu-id="1ae1d-106">若要啟用輪詢，您必須指定特定繫結屬性，本主題中所述。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-106">To enable polling, you must specify certain binding properties as described in this topic.</span></span> <span data-ttu-id="1ae1d-107">如需如何配接器支援在輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-107">For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a><span data-ttu-id="1ae1d-108">使用 Oracle E-business Suite 配接器繫結屬性中設定輪詢作業</span><span class="sxs-lookup"><span data-stu-id="1ae1d-108">Configuring a Polling Operation with Oracle E-Business Suite Adapter Binding Properties</span></span>  
 <span data-ttu-id="1ae1d-109">下表摘要說明[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]繫結屬性，您用來設定配接器接收的資料變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-109">The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data change messages.</span></span> <span data-ttu-id="1ae1d-110">執行輪詢應用程式時，您必須指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-110">You must specify these binding properties while running the polling application.</span></span>  
  
|<span data-ttu-id="1ae1d-111">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="1ae1d-111">Binding Property</span></span>|<span data-ttu-id="1ae1d-112">Description</span><span class="sxs-lookup"><span data-stu-id="1ae1d-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="1ae1d-113">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="1ae1d-113">**InboundOperationType**</span></span>|<span data-ttu-id="1ae1d-114">指定您是否要執行**輪詢**或**通知**輸入作業。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-114">Specifies whether you want to perform **Polling** or **Notification** inbound operation.</span></span> <span data-ttu-id="1ae1d-115">預設值是**輪詢**。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-115">Default is **Polling**.</span></span>|  
|<span data-ttu-id="1ae1d-116">**PolledDataAvailableStatement**</span><span class="sxs-lookup"><span data-stu-id="1ae1d-116">**PolledDataAvailableStatement**</span></span>|<span data-ttu-id="1ae1d-117">指定的 SQL 陳述式來判斷是否可用於輪詢的任何資料執行配接器。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-117">Specifies the SQL statement that the adapter executes to determine whether any data is available for polling.</span></span> <span data-ttu-id="1ae1d-118">只有當可用的記錄時，SELECT 陳述式您為指定**PollingInput**繫結屬性將會執行。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-118">Only if a record is available, the SELECT statement you specify for the **PollingInput** binding property will be executed.</span></span>|  
|<span data-ttu-id="1ae1d-119">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="1ae1d-119">**PollingInterval**</span></span>|<span data-ttu-id="1ae1d-120">指定間隔，以秒為單位，此時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行陳述式指定**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-120">Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property.</span></span> <span data-ttu-id="1ae1d-121">預設值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-121">The default is 30 seconds.</span></span> <span data-ttu-id="1ae1d-122">輪詢間隔會決定後續輪詢間隔時間。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-122">The polling interval determines the time interval between successive polls.</span></span> <span data-ttu-id="1ae1d-123">如果指定的間隔內執行的陳述式，則配接器進入睡眠狀態的剩餘時間間隔中。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-123">If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval.</span></span>|  
|<span data-ttu-id="1ae1d-124">**PollingInput**</span><span class="sxs-lookup"><span data-stu-id="1ae1d-124">**PollingInput**</span></span>|<span data-ttu-id="1ae1d-125">指定輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-125">Specifies the polling statement.</span></span> <span data-ttu-id="1ae1d-126">若要輪詢使用 SELECT 陳述式，您必須指定這個繫結屬性的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-126">To poll using a SELECT statement, you must specify a SELECT statement for this binding property.</span></span> <span data-ttu-id="1ae1d-127">預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-127">The default is null.</span></span><br /><br /> <span data-ttu-id="1ae1d-128">您必須指定的值**PollingInput**繫結內容來啟用輪詢。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-128">You must specify a value for **PollingInput** binding property to enable polling.</span></span> <span data-ttu-id="1ae1d-129">輪詢陳述式在沒有進行輪詢，取決於可用的資料時，才會執行**PolledDataAvailableStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-129">The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.</span></span>|  
|<span data-ttu-id="1ae1d-130">**PollingAction**</span><span class="sxs-lookup"><span data-stu-id="1ae1d-130">**PollingAction**</span></span>|<span data-ttu-id="1ae1d-131">指定輪詢作業的動作。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-131">Specifies the action for the polling operation.</span></span> <span data-ttu-id="1ae1d-132">您可以決定產生的作業使用的服務介面的輪詢動作[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-132">You can determine the polling action from the service interface generated for the operation using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].</span></span>|  
|<span data-ttu-id="1ae1d-133">**PostPollStatement**</span><span class="sxs-lookup"><span data-stu-id="1ae1d-133">**PostPollStatement**</span></span>|<span data-ttu-id="1ae1d-134">指定執行所指定的陳述式之後的陳述式區塊**PollingInput**執行繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-134">Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.</span></span>|  
|<span data-ttu-id="1ae1d-135">**PollWhileDataFound**</span><span class="sxs-lookup"><span data-stu-id="1ae1d-135">**PollWhileDataFound**</span></span>|<span data-ttu-id="1ae1d-136">指定是否[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]忽略的輪詢間隔，並持續執行輪詢陳述式，如果輪詢資料表中的可用資料。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-136">Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled.</span></span> <span data-ttu-id="1ae1d-137">如果沒有資料可在資料表中，配接器會還原為執行指定的輪詢間隔輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-137">If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval.</span></span> <span data-ttu-id="1ae1d-138">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-138">Default is false.</span></span>|  
  
 <span data-ttu-id="1ae1d-139">如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-139">For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).</span></span> <span data-ttu-id="1ae1d-140">如需完整的說明，如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢 Oracle 資料庫，請閱讀本主題的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-140">For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database, read the remainder of this topic.</span></span>  
  
## <a name="how-this-topic-demonstrates-polling"></a><span data-ttu-id="1ae1d-141">本主題示範輪詢的方式</span><span class="sxs-lookup"><span data-stu-id="1ae1d-141">How This Topic Demonstrates Polling</span></span>  
 <span data-ttu-id="1ae1d-142">本主題中，以示範如何[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援接收資料變更使用 SELECT 陳述式的訊息，請您輪詢**MS_SAMPLE_EMPLOYEE**介面中的資料表**應用程式物件程式庫**應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-142">In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using SELECT statements, you poll the **MS_SAMPLE_EMPLOYEE** interface table in the **Application Object Library** application.</span></span> <span data-ttu-id="1ae1d-143">當您執行範例建立 Oracle E-business Suite 中的這些物件提供的 create_apps_artifacts.sql 指令碼時，會建立此資料表。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-143">This table is created when you run the create_apps_artifacts.sql script provided with the samples to create these objects in Oracle E-Business Suite.</span></span>  
  
 <span data-ttu-id="1ae1d-144">若要示範輪詢作業，我們執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1ae1d-144">To demonstrate a polling operation, we do the following:</span></span>  
  
-   <span data-ttu-id="1ae1d-145">指定 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷其中介面資料表輪詢 (MS_SAMPLE_EMPLOYEE) 有任何資料。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-145">Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the interface table being polled (MS_SAMPLE_EMPLOYEE) has any data.</span></span> <span data-ttu-id="1ae1d-146">在此範例中，您可以設定為這個繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="1ae1d-146">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     <span data-ttu-id="1ae1d-147">這可確保當配接器 MS_SAMPLE_EMPLOYEE 介面資料表具有一些記錄時才會執行輪詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-147">This ensures that the adapter executes the polling statement only when the MS_SAMPLE_EMPLOYEE interface table has some records.</span></span>  
  
-   <span data-ttu-id="1ae1d-148">指定 SELECT 陳述式**PollingInput**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-148">Specify a SELECT statement for the **PollingInput** binding property.</span></span> <span data-ttu-id="1ae1d-149">此陳述式擷取 MS_SAMPLE_EMPLOYEE 介面資料表中的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-149">This statement retrieves all the rows in the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="1ae1d-150">在此範例中，您可以設定為這個繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="1ae1d-150">In this example, you can set this binding property as:</span></span>  
  
    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1ae1d-151">FOR UPDATE 子句用於 SELECT 陳述式的相關資訊，請參閱[從 Oracle E-business Suite 接收輪詢基礎資料變更訊息](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-151">For information about the FOR UPDATE clause used in the SELECT statement, see [Receive polling-based data-changed messages from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).</span></span>  
  
-   <span data-ttu-id="1ae1d-152">指定 DELETE 陳述式的一部分**PostPollStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-152">Specify a DELETE statement as part of the **PostPollStatement** binding property.</span></span> <span data-ttu-id="1ae1d-153">這個陳述式會從 MS_SAMPLE_EMPLOYEE 介面資料表刪除所有資料。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-153">This statement will delete all data from MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="1ae1d-154">在此範例中，您可以設定為這個繫結屬性：</span><span class="sxs-lookup"><span data-stu-id="1ae1d-154">In this example, you can set this binding property as:</span></span>  
  
    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     <span data-ttu-id="1ae1d-155">發生這種情況之後下, 一次針對指定的陳述式**PollingInput**將會執行，它將會不提取任何資料。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-155">After this happens, the next time the statement specified for **PollingInput** will be executed, it will not fetch any data.</span></span>  
  
-   <span data-ttu-id="1ae1d-156">更多資料加入到 MS_SAMPLE_EMPLOYEE 介面資料表之前, 則不會收到任何輪詢訊息，您必須重新擴展 MS_SAMPLE_EMPLOYEE 介面資料表與新的記錄。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-156">Until more data is added to the MS_SAMPLE_EMPLOYEE interface table, you will not get any polling messages so you must repopulate the MS_SAMPLE_EMPLOYEE interface table with new records.</span></span> <span data-ttu-id="1ae1d-157">您可以藉由執行範例所提供的 insert_apps_data.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-157">You can do so by running the insert_apps_data.sql script provided with the samples.</span></span> <span data-ttu-id="1ae1d-158">執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-158">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span>  
  
## <a name="consuming-the-polling-request-message"></a><span data-ttu-id="1ae1d-159">使用輪詢要求訊息</span><span class="sxs-lookup"><span data-stu-id="1ae1d-159">Consuming the Polling Request Message</span></span>  
 <span data-ttu-id="1ae1d-160">配接器會叫用您的程式碼，以輪詢 Oracle E-business Suite 的輪詢作業。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-160">The adapter invokes the polling operation on your code to poll the Oracle E-Business Suite.</span></span> <span data-ttu-id="1ae1d-161">也就是說，配接器傳送輪詢要求訊息，您會收到透過 IInputChannel 通道形狀。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-161">That is, the adapter sends a polling request message that you receive over an IInputChannel channel shape.</span></span> <span data-ttu-id="1ae1d-162">輪詢要求訊息包含所指定的查詢的結果集**PollingInput**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-162">The polling request message contains the result set of the query specified by the **PollingInput** binding property.</span></span> <span data-ttu-id="1ae1d-163">您可以使用輪詢訊息中有兩種：</span><span class="sxs-lookup"><span data-stu-id="1ae1d-163">You can consume the polling message in one of two ways:</span></span>  
  
-   <span data-ttu-id="1ae1d-164">若要使用訊息使用的節點值的資料流處理，您必須呼叫**WriteBodyContents**方法回應訊息，並將它傳遞**XmlDictionaryWriter**實作節點值的資料流。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-164">To consume the message using node-value streaming, you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  
  
-   <span data-ttu-id="1ae1d-165">若要使用使用節點資料流處理的訊息，您可以呼叫**GetReaderAtBodyContents**要取得的回應訊息上**XmlReader**。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-165">To consume the message using node streaming, you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="1ae1d-166">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="1ae1d-166">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="1ae1d-167">本主題中的範例輪詢 MS_SAMPLE_EMPLOYEE 介面資料表。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-167">The examples in this topic poll the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="1ae1d-168">若要產生資料表的指令碼會提供範例。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-168">A script to generate the table is supplied with the samples.</span></span> <span data-ttu-id="1ae1d-169">如需這些範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-169">For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="1ae1d-170">範例中， **SelectPolling_ChannelModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-170">A sample, **SelectPolling_ChannelModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="receiving-inbound-messages-for-polling-operation-using-the-wcf-channel-model"></a><span data-ttu-id="1ae1d-171">使用 WCF 通道模型的輪詢作業接收內送的訊息</span><span class="sxs-lookup"><span data-stu-id="1ae1d-171">Receiving Inbound Messages for Polling Operation Using the WCF Channel Model</span></span>  
 <span data-ttu-id="1ae1d-172">本節說明如何撰寫.NET 應用程式 （通道模型） 來接收傳入的輪詢訊息使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-172">This section provides instructions on how to write a .NET application (channel model) to receive inbound polling messages using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
#### <a name="to-receive-polling-messages-from-the-adapter"></a><span data-ttu-id="1ae1d-173">若要接收來自配接器的輪詢訊息</span><span class="sxs-lookup"><span data-stu-id="1ae1d-173">To receive polling messages from the adapter</span></span>  
  
1.  <span data-ttu-id="1ae1d-174">Microsoft Visual C#® 中建立專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-174">Create a Microsoft Visual C#® project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="1ae1d-175">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-175">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="1ae1d-176">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-176">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="1ae1d-177">開啟 Program.cs 檔案並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="1ae1d-177">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  <span data-ttu-id="1ae1d-178">指定連線 URI。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-178">Specify a connection URI.</span></span> <span data-ttu-id="1ae1d-179">如需配接器的連線 URI 的詳細資訊，請參閱[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-179">For more information about the adapter connection URI, see [Create the Oracle E-Business Suite connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).</span></span>  
  
    ```  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    ```  
  
5.  <span data-ttu-id="1ae1d-180">建立的執行個體**OracleEBSBinding**並設定繫結屬性才能設定輪詢。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-180">Create an instance of **OracleEBSBinding** and set the binding properties required to configure polling.</span></span> <span data-ttu-id="1ae1d-181">您必須設定至少**InboundOperationType**， **PolledDataAvailableStatement**， **PollingInput**，和**PollingAction**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-181">At a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, and **PollingAction** binding properties.</span></span> <span data-ttu-id="1ae1d-182">如需繫結屬性用來設定輪詢的詳細資訊，請參閱[支援輸入呼叫使用輪詢](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-182">For more information about binding properties used to configure polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
    binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
    binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
    binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
    ```  
  
6.  <span data-ttu-id="1ae1d-183">因為您正在輪詢介面資料表，您也必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-183">Because you are polling an interface table, you must also set the applications context.</span></span> <span data-ttu-id="1ae1d-184">如需應用程式內容和設定應用程式內容所需的繫結屬性的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-184">For more information about application context and binding properties required for setting application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "<Enter user name here>";  
    binding.OraclePassword = "<Enter password here>";  
    binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  
    ```  
  
7.  <span data-ttu-id="1ae1d-185">建立繫結參數集合，並設定認證。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-185">Create a binding parameter collection and set the credentials.</span></span>  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
8.  <span data-ttu-id="1ae1d-186">建立通道接聽程式，並將它開啟。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-186">Create a channel listener and open it.</span></span> <span data-ttu-id="1ae1d-187">您建立的接聽程式叫用**BuildChannelListener < IInputChannel\>** 方法**OracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-187">You create the listener by invoking **BuildChannelListener<IInputChannel\>** method on the **OracleEBSBinding**.</span></span>  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
9. <span data-ttu-id="1ae1d-188">取得**IInputChannel**叫用的通道**AcceptChannel**接聽程式上的方法，並開啟它。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-188">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on the listener and open it.</span></span>  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
10. <span data-ttu-id="1ae1d-189">叫用**接收**從配接器取得下一個傳入的訊息的通道上。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-189">Invoke **Receive** on the channel to get the next inbound message from the adapter.</span></span>  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
11. <span data-ttu-id="1ae1d-190">使用輸入作業所傳回的結果集。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-190">Consume the result set returned by the inbound operation.</span></span> <span data-ttu-id="1ae1d-191">您可以使用訊息使用**XmlReader**或**XmlDictionaryWriter**。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-191">You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.</span></span>  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
12. <span data-ttu-id="1ae1d-192">當您完成處理要求，請關閉通道。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-192">Close the channel when you have completed processing the request.</span></span>  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1ae1d-193">處理傳入的作業完成之後，您必須關閉通道。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-193">You must close the channel after you have finished processing the inbound operation.</span></span> <span data-ttu-id="1ae1d-194">無法關閉通道可能會影響您的程式碼的行為。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-194">Failure to close the channel may affect the behavior of your code.</span></span>  
  
13. <span data-ttu-id="1ae1d-195">當您完成接收的資料變更的訊息時，請關閉接聽程式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-195">Close the listener when you are finished receiving data-changed messages.</span></span>  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1ae1d-196">關閉接聽程式不會關閉建立使用接聽程式通道。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-196">Closing the listener does not close channels created using the listener.</span></span> <span data-ttu-id="1ae1d-197">您必須明確地關閉使用接聽程式所建立的每個通道。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-197">You must explicitly close each channel created using the listener.</span></span>  
  
### <a name="example"></a><span data-ttu-id="1ae1d-198">範例</span><span class="sxs-lookup"><span data-stu-id="1ae1d-198">Example</span></span>  
 <span data-ttu-id="1ae1d-199">下列範例會示範輪詢 MS_SAMPLE_EMPLOYEE 介面資料表輪詢應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-199">The following example shows a polling application that polls the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="1ae1d-200">**PollingInput**屬性包含從 MS_SAMPLE_EMPLOYEE 資料表讀取所有資料的 select 陳述式和後輪詢陳述式會從相同的資料表刪除所有資料。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-200">The **PollingInput** property contains the select statement that reads all the data from the MS_SAMPLE_EMPLOYEE table and the post poll statement deletes all the data from the same table.</span></span> <span data-ttu-id="1ae1d-201">輪詢訊息會寫入`C:\PollingOutput.xml`。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-201">The polling message is written to `C:\PollingOutput.xml`.</span></span>  
  
 <span data-ttu-id="1ae1d-202">更多資料加入到 MS_SAMPLE_EMPLOYEE 介面資料表之前，後續的輪詢訊息將不會包含任何記錄。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-202">Subsequent polling messages will not contain any records until more data is added to the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="1ae1d-203">您可以藉由執行範例所提供的 insert_apps_data.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-203">You can do so by running the insert_apps_data.sql script provided with the samples.</span></span> <span data-ttu-id="1ae1d-204">執行這個指令碼之後下, 一個輪詢作業將會提取新的記錄插入至資料表。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-204">After you run this script, the next polling operation will fetch the new records inserted into the table.</span></span> <span data-ttu-id="1ae1d-205">配接器將繼續輪詢直到按關閉服務主機\<傳回 >。</span><span class="sxs-lookup"><span data-stu-id="1ae1d-205">The adapter will continue to poll until you close the service host by pressing \<RETURN>.</span></span>  
  
```  
using System;  
using Microsoft.Adapters.OracleEBS;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Xml;  
  
namespace SelectPolling_ChannelModel  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("Sample started. This sample will poll 5 times and will perform the following tasks:");  
            Console.WriteLine("Press any key to start polling...");  
            Console.ReadLine();  
            IChannelListener<IInputChannel> listener = null;  
  
            IInputChannel channel = null;  
  
            try  
            {  
                TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
                binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
                binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
                binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
                binding.OracleUserName = "<Enter user name here>";  
                binding.OraclePassword = "<Enter password here>";  
                binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  
  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name?");  
  
                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  
  
                listener = binding.BuildChannelListener<IInputChannel>(ConnectionUri, bindingParams);  
                listener.Open();  
  
                channel = listener.AcceptChannel();  
                channel.Open();  
  
                Console.WriteLine("Channel and Listener opened...");  
                Console.WriteLine("\nWaiting for polled data...");  
                Console.WriteLine("Receive request timeout is {0}", messageTimeout);  
  
                // Poll five times with the specified message timeout   
                // If a timeout occurs polling will be aborted  
                for (int i = 0; i < 5; i++)  
                {  
                    Console.WriteLine("Polling: " + i);  
                    Message message = null;  
                    XmlReader reader = null;  
                    try  
                    {  
                        //Message is received so process the results  
                        message = channel.Receive(messageTimeout);  
                    }  
                    catch (System.TimeoutException toEx)  
                    {  
                        Console.WriteLine("\nNo data for request number {0}: {1}", i + 1, toEx.Message);  
                        continue;  
                    }  
  
                    // Get the query results using an XML reader  
                    try  
                    {  
                        reader = message.GetReaderAtBodyContents();  
                    }  
                    catch (Exception ex)  
                    {  
                        Console.WriteLine("Exception :" + ex);  
                        throw;                          
                    }  
  
                    XmlDocument doc = new XmlDocument();  
                    doc.Load(reader);  
                    using (XmlWriter writer = XmlWriter.Create("C:\\PollingOutput.xml"))  
                    {  
                        doc.WriteTo(writer);  
                        Console.WriteLine("The polling response is saved at 'C:\\PollingOutput.xml'");  
                    }  
                    // return the cursor  
                    Console.WriteLine();  
  
                    // close the reader  
                    reader.Close();  
  
                    message.Close();  
                }  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                Console.ReadLine();  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: close the channel and listener to stop polling  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  
  
                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ae1d-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae1d-206">See Also</span></span>  
 [<span data-ttu-id="1ae1d-207">開發 Oracle E-business Suite 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="1ae1d-207">Develop Oracle E-Business Suite applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)