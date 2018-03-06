---
title: "追蹤資料至 Application Insights 或事件中心 |Microsoft 文件"
description: "若要啟用分析追蹤資料與 Azure Application Insights 或 BizTalk Server 中的 Azure 事件中心的功能套件的安裝"
ms.custom: fp1, fp2
ms.date: 11/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: 
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5ddd60f72955c7196edfc8bf2310b73226d2abe
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="send-biztalk-tracking-data-to-azure-application-insights-or-event-hubs"></a><span data-ttu-id="24cd3-103">傳送 BizTalk 追蹤資料到 Azure Application Insights 或事件中心</span><span class="sxs-lookup"><span data-stu-id="24cd3-103">Send BizTalk tracking data to Azure Application Insights or Event Hubs</span></span>

<span data-ttu-id="24cd3-104">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可以處理，並將您的追蹤資料傳送至 Azure Application Insights。</span><span class="sxs-lookup"><span data-stu-id="24cd3-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can process and send your tracking data to Azure Application Insights.</span></span> 
          
<span data-ttu-id="24cd3-105">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]功能套件 2**:</span><span class="sxs-lookup"><span data-stu-id="24cd3-105">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**:</span></span>

* <span data-ttu-id="24cd3-106">Application Insights 支援 SQL 預設執行個體和具名執行個體的 SQL</span><span class="sxs-lookup"><span data-stu-id="24cd3-106">Application Insights supports SQL default instances, and SQL named instances</span></span>
* <span data-ttu-id="24cd3-107">您可以處理，並將追蹤資料傳送至 Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="24cd3-107">You can process and send tracking data to Azure Event Hubs</span></span>

<span data-ttu-id="24cd3-108">您可以使用這些 Azure 服務，從接收埠、 傳送埠和協調流程追蹤您的執行個體。</span><span class="sxs-lookup"><span data-stu-id="24cd3-108">Use these Azure services to track your instances from receive ports, send ports, and orchestrations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24cd3-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="24cd3-109">Prerequisites</span></span>
* <span data-ttu-id="24cd3-110">建立的新執行個體[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource)。</span><span class="sxs-lookup"><span data-stu-id="24cd3-110">Create a new instance of [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource).</span></span> <span data-ttu-id="24cd3-111">BizTalk Server 會使用**檢測金鑰**來驗證。</span><span class="sxs-lookup"><span data-stu-id="24cd3-111">BizTalk Server uses the **Instrumentation Key** to authenticate.</span></span>
* <span data-ttu-id="24cd3-112">建立[Azure 事件中樞命名空間和事件中樞](https://docs.microsoft.com/azure/event-hubs/event-hubs-create)。</span><span class="sxs-lookup"><span data-stu-id="24cd3-112">Create an [Azure Event Hubs namespace and event hub](https://docs.microsoft.com/azure/event-hubs/event-hubs-create).</span></span> <span data-ttu-id="24cd3-113">BizTalk Server 會使用 SAS （命名空間層級） 或事件中心層級的原則來驗證。</span><span class="sxs-lookup"><span data-stu-id="24cd3-113">BizTalk Server uses the SAS (namespace-level) or event hub-level policy to authenticate.</span></span>
* <span data-ttu-id="24cd3-114">安裝[功能套件 2](https://aka.ms/bts2016fp2)上您</span><span class="sxs-lookup"><span data-stu-id="24cd3-114">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on your</span></span> [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

## <a name="enable-analytics-for-your-environment"></a><span data-ttu-id="24cd3-115">啟用分析為您的環境</span><span class="sxs-lookup"><span data-stu-id="24cd3-115">Enable analytics for your environment</span></span>

1. <span data-ttu-id="24cd3-116">開啟**BizTalk Server 管理**主控台中，以滑鼠右鍵按一下**BizTalk 群組**，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-116">Open the **BizTalk Server Administration** console, right-click the **BizTalk Group**, and select **Settings**.</span></span> 
2. <span data-ttu-id="24cd3-117">請檢查**啟用群組層級分析**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-117">Check **Enable group-level analytics**.</span></span>
3. <span data-ttu-id="24cd3-118">如**目標類型**，選取**Application Insight**或**事件中心**從清單中。</span><span class="sxs-lookup"><span data-stu-id="24cd3-118">For the **Target type**, select **Application Insight** or **Event Hub** from the list.</span></span>
    <span data-ttu-id="24cd3-119">![啟用分析為您的環境](../core/media/environmentsettingapplicationinishgt.PNG)</span><span class="sxs-lookup"><span data-stu-id="24cd3-119">![Enable analytics for your environment](../core/media/environmentsettingapplicationinishgt.PNG)</span></span>

4. <span data-ttu-id="24cd3-120">如**連接參數**，選取**...**  按鈕，和**登入**到您的 Azure 帳戶。</span><span class="sxs-lookup"><span data-stu-id="24cd3-120">For the **Connection parameters**, select the **...** button, and **Sign-in** to your Azure account.</span></span>  

    <span data-ttu-id="24cd3-121">**Application insights**</span><span class="sxs-lookup"><span data-stu-id="24cd3-121">**For Application Insights**</span></span>  
    <span data-ttu-id="24cd3-122">選取您**訂用帳戶**，**資源群組**，和您的 Application Insights 執行個體。</span><span class="sxs-lookup"><span data-stu-id="24cd3-122">Select your **Subscription**, **Resource Group**, and your Application Insights instance.</span></span>

    ![啟用分析為您的環境](../core/media/analytics-group-application-insights.png)

    <span data-ttu-id="24cd3-124">**事件中樞**</span><span class="sxs-lookup"><span data-stu-id="24cd3-124">**For Event Hub**</span></span>  
    <span data-ttu-id="24cd3-125">選取您**訂用帳戶**，**資源群組**，事件中樞命名空間，與事件中心。</span><span class="sxs-lookup"><span data-stu-id="24cd3-125">Select your **Subscription**, **Resource Group**, Event Hub namespace, and event hub.</span></span> <span data-ttu-id="24cd3-126">進行驗證，您可以使用在命名空間層級或在事件中心層級的實體簽章的存取簽章 (SAS)。</span><span class="sxs-lookup"><span data-stu-id="24cd3-126">For authentication, you can use an access signature (SAS) at the namespace-level, or entity signature at the event hub-level.</span></span> <span data-ttu-id="24cd3-127">可用的索引鍵與先前設定內的值是 自動填入[Azure](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="24cd3-127">Your available keys are auto-populated with the values previously configured within [Azure](https://portal.azure.com).</span></span>

    ![啟用分析為您的環境](../core/media/send-tracking-data-to-azure.png)

5. <span data-ttu-id="24cd3-129">選取 **確定** 以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="24cd3-129">Select **OK** to save your changes.</span></span> 

<span data-ttu-id="24cd3-130">一旦啟用[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]已準備好傳送您的 Azure 資源的資料。</span><span class="sxs-lookup"><span data-stu-id="24cd3-130">Once enabled, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] is ready to transmit data to your Azure resource.</span></span> <span data-ttu-id="24cd3-131">接下來，啟用您的連接埠和協調流程上的分析。</span><span class="sxs-lookup"><span data-stu-id="24cd3-131">Next, enable analytics on your ports and orchestrations.</span></span> 

## <a name="enable-analytics-on-your-artifacts"></a><span data-ttu-id="24cd3-132">啟用您的成品上的分析</span><span class="sxs-lookup"><span data-stu-id="24cd3-132">Enable analytics on your artifacts</span></span>

1. <span data-ttu-id="24cd3-133">在 BizTalk Server 管理，以滑鼠右鍵按一下**接收埠**，**傳送埠**或**協調流程**，然後選取**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-133">In BizTalk Server Administration, right-click a **receive port**, **send port** or **orchestration**, and select **Tracking**.</span></span>
2. <span data-ttu-id="24cd3-134">在下**分析**，檢查**啟用分析**，類似於下列。</span><span class="sxs-lookup"><span data-stu-id="24cd3-134">Under **Analytics**, check **Enable Analytics**, similar to the following.</span></span> <span data-ttu-id="24cd3-135">這項設定會啟動追蹤和傳輸您的 Azure 資源成品的資料。</span><span class="sxs-lookup"><span data-stu-id="24cd3-135">This setting starts tracking and transmitting data from the artifact to your Azure resource.</span></span>
    
    ![協調流程的追蹤資料](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. <span data-ttu-id="24cd3-137">選取 **確定** 以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="24cd3-137">Select **OK** to save your changes.</span></span>
4. <span data-ttu-id="24cd3-138">重新啟動追蹤主控件執行個體，並確認 BizTalk 應用程式已啟動。</span><span class="sxs-lookup"><span data-stu-id="24cd3-138">Restart the tracking host Instance, and confirm the BizTalk Application is started.</span></span>

> [!TIP]
> <span data-ttu-id="24cd3-139">若要深入組織資料的更多其他系統連接 BizTalk Server 的分析。</span><span class="sxs-lookup"><span data-stu-id="24cd3-139">Connect your BizTalk Server Analytics with other systems to gain even more insight into your organizations data.</span></span>

## <a name="view-your-data"></a><span data-ttu-id="24cd3-140">檢視您的資料</span><span class="sxs-lookup"><span data-stu-id="24cd3-140">View your data</span></span>

#### <a name="use-application-insights"></a><span data-ttu-id="24cd3-141">使用 Application Insights</span><span class="sxs-lookup"><span data-stu-id="24cd3-141">Use Application Insights</span></span>
<span data-ttu-id="24cd3-142">一旦將資料傳送至 Application Insights，您可以使用在 Azure 中的分析工具來建立進階的查詢、 及分析您的資料。</span><span class="sxs-lookup"><span data-stu-id="24cd3-142">Once the data is sent to Application Insights, you can use the analytics tools within Azure to create advanced queries, and analyze your data.</span></span>

1. <span data-ttu-id="24cd3-143">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="24cd3-143">Sign in to the [Azure Portal](https://portal.azure.com).</span></span>
2. <span data-ttu-id="24cd3-144">開啟 Application Insights 資源，並選取**計量瀏覽器**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-144">Open your Application Insights resource, and select **Metrics Explorer**.</span></span>
3. <span data-ttu-id="24cd3-145">空白圖表可能會顯示。</span><span class="sxs-lookup"><span data-stu-id="24cd3-145">Empty charts may display.</span></span> <span data-ttu-id="24cd3-146">在圖表中，選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-146">In a chart, select **Edit**.</span></span> <span data-ttu-id="24cd3-147">在下**度量**，選取**自訂**若要查看可用的追蹤的屬性。</span><span class="sxs-lookup"><span data-stu-id="24cd3-147">Under **Metrics**, select **Custom** to see the available tracked properties.</span></span> <span data-ttu-id="24cd3-148">選取 [一些] 才能看到這些變更在圖表上的不同選項：</span><span class="sxs-lookup"><span data-stu-id="24cd3-148">Select some of the different options to see the changes on your chart:</span></span> 

    ![Azure Analytics](../core/media/azure-stream-metrics-custom.png)

4. <span data-ttu-id="24cd3-150">返回您的 Application Insights 資源，並選取**分析**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-150">Go back to your Application Insights resource, and select **Analytics**.</span></span> <span data-ttu-id="24cd3-151">在**使用量**，選取**執行**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-151">In **Usage**, select **Run**.</span></span> <span data-ttu-id="24cd3-152">範例查詢會執行，而且結果會顯示在圖表中。</span><span class="sxs-lookup"><span data-stu-id="24cd3-152">A sample query is executed, and the results are displayed in a chart.</span></span>  

> [!TIP]
> <span data-ttu-id="24cd3-153">Azure 的 Application Insights 是功能強大的工具。</span><span class="sxs-lookup"><span data-stu-id="24cd3-153">Azure Application Insights is a powerful tool.</span></span> <span data-ttu-id="24cd3-154">沒有可協助您撰寫查詢，在 Application Insights 中的資源[Application Insights 中的分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)，以及甚至開始在[Application Insights 是什麼？](https://docs.microsoft.com/azure/application-insights/app-insights-overview)。</span><span class="sxs-lookup"><span data-stu-id="24cd3-154">There are resources to help you write queries in Application Insights at [Analytics in Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics), and even to get started at [What is Application Insights?](https://docs.microsoft.com/azure/application-insights/app-insights-overview).</span></span>

#### <a name="use-event-hubs"></a><span data-ttu-id="24cd3-155">使用事件中心</span><span class="sxs-lookup"><span data-stu-id="24cd3-155">Use Event Hubs</span></span>
<span data-ttu-id="24cd3-156">一旦將資料傳送至事件中心時，有幾種方式，以查看資料。</span><span class="sxs-lookup"><span data-stu-id="24cd3-156">Once the data is sent to Event Hubs, there are a couple of ways to see the data.</span></span> <span data-ttu-id="24cd3-157">許多事件中心的使用者都使用事件中心擷取資料流的資料載入至 Azure。</span><span class="sxs-lookup"><span data-stu-id="24cd3-157">Many Event Hubs users are using Event Hubs Capture to load streaming data into Azure.</span></span> <span data-ttu-id="24cd3-158">目的是讓您將重點放在資料處理，而不是在資料擷取。</span><span class="sxs-lookup"><span data-stu-id="24cd3-158">The intent is for you to focus on data processing, rather than on data capture.</span></span> <span data-ttu-id="24cd3-159">[事件中心擷取](https://docs.microsoft.com/azure/event-hubs/event-hubs-capture-overview)說明運作方式以及如何加以設定。</span><span class="sxs-lookup"><span data-stu-id="24cd3-159">[Event Hubs Capture](https://docs.microsoft.com/azure/event-hubs/event-hubs-capture-overview) explains how it works, and how to set it up.</span></span>

<span data-ttu-id="24cd3-160">另一個選項是建立接收埠和接收位置使用事件中樞配接器。</span><span class="sxs-lookup"><span data-stu-id="24cd3-160">Another option is to create a receive port and receive location using the Event Hub Adapter.</span></span> <span data-ttu-id="24cd3-161">然後，您可以將資料輸出至資料夾。</span><span class="sxs-lookup"><span data-stu-id="24cd3-161">Then, you can output the data to a folder.</span></span> <span data-ttu-id="24cd3-162">這個概念是如果您想要測試的案例。</span><span class="sxs-lookup"><span data-stu-id="24cd3-162">This idea may be best if you want to test the scenario.</span></span> <span data-ttu-id="24cd3-163">[事件中心配接器](event-hubs-adapter.md)列出 BizTalk server 從事件中心接收訊息的步驟。</span><span class="sxs-lookup"><span data-stu-id="24cd3-163">[Event Hubs adapter](event-hubs-adapter.md) lists the steps to receive messages into BizTalk Server from Event Hubs.</span></span>

## <a name="where-the-data-is-stored"></a><span data-ttu-id="24cd3-164">儲存資料</span><span class="sxs-lookup"><span data-stu-id="24cd3-164">Where the data is stored</span></span>

<span data-ttu-id="24cd3-165">將追蹤資料應該相當快速 （在幾分鐘） 內會顯示在您的 Azure 資源。</span><span class="sxs-lookup"><span data-stu-id="24cd3-165">Your tracking data should display fairly quickly (within a few minutes) within your Azure resources.</span></span> <span data-ttu-id="24cd3-166">如果沒有，則有可能發生問題的追蹤主控件。</span><span class="sxs-lookup"><span data-stu-id="24cd3-166">If it doesn't, then there may be an issue with the tracking host.</span></span> <span data-ttu-id="24cd3-167">在 SQL Server 中，分析資料儲存在 BizTalkMsgBoxDb 資料庫中，在 TrackingData_2_*x*資料表。</span><span class="sxs-lookup"><span data-stu-id="24cd3-167">In SQL Server, the Analytics data is stored in the BizTalkMsgBoxDb database, in the TrackingData_2_*x* tables.</span></span> <span data-ttu-id="24cd3-168">在 SQL Server Management Studio，傳回這些四個資料表中的前 1000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="24cd3-168">In SQL Server Management Studio, return the top 1000 rows on these four tables.</span></span> <span data-ttu-id="24cd3-169">如果是有資料，然後追蹤主控件不將資料移到 BizTalkDTADb 資料庫。</span><span class="sxs-lookup"><span data-stu-id="24cd3-169">If the data is there, then the tracking host is not moving the data to the BizTalkDTADb database.</span></span> 

<span data-ttu-id="24cd3-170">一些可能的解決方式：</span><span class="sxs-lookup"><span data-stu-id="24cd3-170">Some possible resolutions:</span></span>

1. <span data-ttu-id="24cd3-171">重新啟動追蹤主控件。</span><span class="sxs-lookup"><span data-stu-id="24cd3-171">Restart the tracking host.</span></span>
2. <span data-ttu-id="24cd3-172">建立專用的追蹤主控件。</span><span class="sxs-lookup"><span data-stu-id="24cd3-172">Create a dedicated tracking host.</span></span> <span data-ttu-id="24cd3-173">安裝 BizTalk Server 時，可能會在啟用追蹤**BizTalk Server 應用程式 1**主機。</span><span class="sxs-lookup"><span data-stu-id="24cd3-173">When BizTalk Server is installed, tracking may be enabled on the **BizTalk Server Application 1** host.</span></span> <span data-ttu-id="24cd3-174">一般而言，此應用程式也會用來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="24cd3-174">Typically, this application is also used to process messages.</span></span> <span data-ttu-id="24cd3-175">建立專用的追蹤主控件使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="24cd3-175">Create a dedicated tracking host using the following steps:</span></span> 

    1. <span data-ttu-id="24cd3-176">在 BizTalk Server 管理中，開啟 BizTalk Server 應用程式 1 主控件的屬性，然後取消核取**允許主控件追蹤**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-176">In BizTalk Server Administration, open the properties of the BizTalk Server Application 1 host, and uncheck **Allow Host Tracking**.</span></span> <span data-ttu-id="24cd3-177">重新啟動此主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="24cd3-177">Restart this host instance.</span></span>

    2. <span data-ttu-id="24cd3-178">建立新的主機名稱為**追蹤**，並檢查**允許主控件追蹤**。</span><span class="sxs-lookup"><span data-stu-id="24cd3-178">Create a new host named **Tracking**, and check **Allow Host Tracking**.</span></span> <span data-ttu-id="24cd3-179">建立主控件執行個體，並將它啟動。</span><span class="sxs-lookup"><span data-stu-id="24cd3-179">Create a host instance, and start it.</span></span>

<span data-ttu-id="24cd3-180">現在，再次查詢 BizTalkMsgBoxDb TrackingData_2_x 資料表。</span><span class="sxs-lookup"><span data-stu-id="24cd3-180">Now, query the BizTalkMsgBoxDb TrackingData_2_x tables again.</span></span> <span data-ttu-id="24cd3-181">如果資料表是空的資料移動，而且應該開始在 Application Insights 中顯示。</span><span class="sxs-lookup"><span data-stu-id="24cd3-181">If the tables are empty, then the data was moved, and should start displaying in Application Insights.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="24cd3-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24cd3-182">See also</span></span>
 [<span data-ttu-id="24cd3-183">安裝及設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="24cd3-183">Install & configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)