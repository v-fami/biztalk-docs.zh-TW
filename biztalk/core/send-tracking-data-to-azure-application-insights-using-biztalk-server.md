---
title: "將追蹤資料傳送至 Azure Application Insights |Microsoft 文件"
description: "若要啟用分析與 BizTalk Server 中的 Azure Application Insights 追蹤資料的功能套件的安裝"
ms.custom: fp1
ms.date: 11/06/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: "10"
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a65ffd2c5ee76d857effde6ab82dddf17b3de4b
ms.sourcegitcommit: 30189176c44873e3de42cc5f2b8951da51ffd251
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="send-tracking-data-to-azure-application-insights-using-biztalk-server"></a><span data-ttu-id="2ec23-103">將追蹤資料傳送至 Azure Application Insights 使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2ec23-103">Send tracking data to Azure Application Insights using BizTalk Server</span></span>

<span data-ttu-id="2ec23-104">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可以處理，並將您的追蹤資料傳送至 Azure Application Insights。</span><span class="sxs-lookup"><span data-stu-id="2ec23-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can process and send your tracking data to Azure Application Insights.</span></span> <span data-ttu-id="2ec23-105">使用 Application Insights 功能來追蹤您的執行個體從接收埠、 傳送埠和協調流程。</span><span class="sxs-lookup"><span data-stu-id="2ec23-105">Use the Application Insights features to track your instances from receive ports, send ports, and orchestrations.</span></span>
          
> [!IMPORTANT]
> <span data-ttu-id="2ec23-106">這項功能目前不適用於 SQL 具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ec23-106">This feature currently does not work with SQL Named Instances.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ec23-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="2ec23-107">Prerequisites</span></span>
* <span data-ttu-id="2ec23-108">建立的新執行個體[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource)。</span><span class="sxs-lookup"><span data-stu-id="2ec23-108">Create a new instance of [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-create-new-resource).</span></span> <span data-ttu-id="2ec23-109">在其內容中，複製**檢測金鑰**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-109">In its properties, copy the **Instrumentation Key**.</span></span> <span data-ttu-id="2ec23-110">因此您需要準備，請將它貼入另一個檔案中。</span><span class="sxs-lookup"><span data-stu-id="2ec23-110">Paste it in another file so you have it ready.</span></span> <span data-ttu-id="2ec23-111">我們使用 BizTalk Server 內的這個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2ec23-111">We use this key within BizTalk Server.</span></span> 
* <span data-ttu-id="2ec23-112">安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec23-112">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

## <a name="enable-analytics-for-your-environment"></a><span data-ttu-id="2ec23-113">啟用分析為您的環境</span><span class="sxs-lookup"><span data-stu-id="2ec23-113">Enable analytics for your environment</span></span>

1. <span data-ttu-id="2ec23-114">開啟**BizTalk Server 管理**主控台中，以滑鼠右鍵按一下**BizTalk 群組**，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-114">Open the **BizTalk Server Administration** console, right-click the **BizTalk Group**, and select **Settings**.</span></span> 
2. <span data-ttu-id="2ec23-115">請檢查**啟用群組層級分析**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-115">Check **Enable group-level analytics**.</span></span>
3. <span data-ttu-id="2ec23-116">如**目標類型**，選取**Application Insight**從清單中。</span><span class="sxs-lookup"><span data-stu-id="2ec23-116">For the **Target type**, select **Application Insight** from the list.</span></span>
4. <span data-ttu-id="2ec23-117">如**連接參數**，輸入您的 Application Insights **[檢測金鑰](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)** （可在 Azure 入口網站）。</span><span class="sxs-lookup"><span data-stu-id="2ec23-117">For the **Connection parameters**, enter your Application Insights **[instrumentation key](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)** (available in the Azure portal).</span></span> <span data-ttu-id="2ec23-118">群組設定看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ec23-118">Your Group settings look similar to the following:</span></span> 

    ![啟用分析為您的環境](../core/media/environmentsettingapplicationinishgt.PNG)

5. <span data-ttu-id="2ec23-120">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="2ec23-120">Select **OK** to save your changes.</span></span> 

<span data-ttu-id="2ec23-121">一旦啟用[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]已準備好傳送至 Application Insights 資料。</span><span class="sxs-lookup"><span data-stu-id="2ec23-121">Once enabled, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] is ready to transmit data to Application Insights.</span></span> <span data-ttu-id="2ec23-122">接下來，啟用您的連接埠和協調流程上的分析。</span><span class="sxs-lookup"><span data-stu-id="2ec23-122">Next, enable analytics on your ports and orchestrations.</span></span> 

## <a name="enable-analytics-on-your-artifacts"></a><span data-ttu-id="2ec23-123">啟用您的成品上的分析</span><span class="sxs-lookup"><span data-stu-id="2ec23-123">Enable analytics on your artifacts</span></span>

1. <span data-ttu-id="2ec23-124">在 BizTalk Server 管理，以滑鼠右鍵按一下**接收埠**，**傳送埠**或**協調流程**，然後選取**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-124">In BizTalk Server Administration, right-click a **receive port**, **send port** or **orchestration**, and select **Tracking**.</span></span>
2. <span data-ttu-id="2ec23-125">在下**分析**，檢查**啟用分析**，類似於下列。</span><span class="sxs-lookup"><span data-stu-id="2ec23-125">Under **Analytics**, check **Enable Analytics**, similar to the following.</span></span> <span data-ttu-id="2ec23-126">這項設定會啟動追蹤，以及將傳送至 Application Insights 從成品資料。</span><span class="sxs-lookup"><span data-stu-id="2ec23-126">This setting starts tracking and transmitting data from the artifact to Application Insights.</span></span>
    
    ![協調流程的追蹤資料](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. <span data-ttu-id="2ec23-128">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="2ec23-128">Select **OK** to save your changes.</span></span>
4. <span data-ttu-id="2ec23-129">重新啟動追蹤主控件執行個體，並確認 BizTalk 應用程式已啟動。</span><span class="sxs-lookup"><span data-stu-id="2ec23-129">Restart the tracking host Instance, and confirm the BizTalk Application is started.</span></span>

<span data-ttu-id="2ec23-130">接下來，執行以查看您的資料的 Application Insights 中的查詢。</span><span class="sxs-lookup"><span data-stu-id="2ec23-130">Next, run queries within Application Insights to see your data.</span></span>  

> [!TIP]
> <span data-ttu-id="2ec23-131">若要深入組織資料的更多其他系統連接 BizTalk Server 的分析。</span><span class="sxs-lookup"><span data-stu-id="2ec23-131">Connect your BizTalk Server Analytics with other systems to gain even more insight into your organizations data.</span></span>

## <a name="view-your-data"></a><span data-ttu-id="2ec23-132">檢視您的資料</span><span class="sxs-lookup"><span data-stu-id="2ec23-132">View your data</span></span>
<span data-ttu-id="2ec23-133">一旦將資料傳送至 Application Insights，您可以使用在 Azure 中的分析工具來建立進階的查詢、 及分析您的資料。</span><span class="sxs-lookup"><span data-stu-id="2ec23-133">Once the data is sent to Application Insights, you can use the analytics tools within Azure to create advanced queries, and analyze your data.</span></span>

1. <span data-ttu-id="2ec23-134">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="2ec23-134">Sign in to the [Azure Portal](https://portal.azure.com).</span></span>
2. <span data-ttu-id="2ec23-135">開啟 Application Insights 資源，並選取**計量瀏覽器**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-135">Open your Application Insights resource, and select **Metrics Explorer**.</span></span>
3. <span data-ttu-id="2ec23-136">空白圖表可能會顯示。</span><span class="sxs-lookup"><span data-stu-id="2ec23-136">Empty charts may display.</span></span> <span data-ttu-id="2ec23-137">在圖表中，選取**編輯**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-137">In a chart, select **Edit**.</span></span> <span data-ttu-id="2ec23-138">在下**度量**，選取**自訂**若要查看可用的追蹤的屬性。</span><span class="sxs-lookup"><span data-stu-id="2ec23-138">Under **Metrics**, select **Custom** to see the available tracked properties.</span></span> <span data-ttu-id="2ec23-139">選取 [一些] 才能看到這些變更在圖表上的不同選項：</span><span class="sxs-lookup"><span data-stu-id="2ec23-139">Select some of the different options to see the changes on your chart:</span></span> 

    ![Azure Analytics](../core/media/azure-stream-metrics-custom.png)

4. <span data-ttu-id="2ec23-141">返回您的 Application Insights 資源，並選取**分析**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-141">Go back to your Application Insights resource, and select **Analytics**.</span></span> <span data-ttu-id="2ec23-142">在**使用量**，選取**執行**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-142">In **Usage**, select **Run**.</span></span> <span data-ttu-id="2ec23-143">範例查詢會執行，而且結果會顯示在圖表中。</span><span class="sxs-lookup"><span data-stu-id="2ec23-143">A sample query is executed, and the results are displayed in a chart.</span></span>  

> [!TIP]
> <span data-ttu-id="2ec23-144">Azure 的 Application Insights 是功能強大的工具。</span><span class="sxs-lookup"><span data-stu-id="2ec23-144">Azure Application Insights is a powerful tool.</span></span> <span data-ttu-id="2ec23-145">沒有可協助您撰寫查詢，在 Application Insights 中的資源[Application Insights 中的分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)，以及甚至開始在[Application Insights 是什麼？](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-overview)。</span><span class="sxs-lookup"><span data-stu-id="2ec23-145">There are resources to help you write queries in Application Insights at [Analytics in Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics), and even to get started at [What is Application Insights?](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-overview).</span></span>

## <a name="where-the-data-is-stored"></a><span data-ttu-id="2ec23-146">儲存資料</span><span class="sxs-lookup"><span data-stu-id="2ec23-146">Where the data is stored</span></span>

<span data-ttu-id="2ec23-147">將追蹤資料應該相當快速 （在幾分鐘） 內會顯示在 Application Insights。</span><span class="sxs-lookup"><span data-stu-id="2ec23-147">Your tracking data should display fairly quickly (within a few minutes) within Application Insights.</span></span> <span data-ttu-id="2ec23-148">如果沒有，則有可能發生問題的追蹤主控件。</span><span class="sxs-lookup"><span data-stu-id="2ec23-148">If it doesn't, then there may be an issue with the tracking host.</span></span> <span data-ttu-id="2ec23-149">在 SQL Server 中，分析資料儲存在 BizTalkMsgBoxDb 資料庫中，在 TrackingData_2_*x*資料表。</span><span class="sxs-lookup"><span data-stu-id="2ec23-149">In SQL Server, the Analytics data is stored in the BizTalkMsgBoxDb database, in the TrackingData_2_*x* tables.</span></span> <span data-ttu-id="2ec23-150">在 SQL Server Management Studio，傳回這些四個資料表中的前 1000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="2ec23-150">In SQL Server Management Studio, return the top 1000 rows on these four tables.</span></span> <span data-ttu-id="2ec23-151">如果是有資料，然後追蹤主控件不將資料移到 BizTalkDTADb 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ec23-151">If the data is there, then the tracking host is not moving the data to the BizTalkDTADb database.</span></span> 

<span data-ttu-id="2ec23-152">一些可能的解決方式：</span><span class="sxs-lookup"><span data-stu-id="2ec23-152">Some possible resolutions:</span></span>

1. <span data-ttu-id="2ec23-153">重新啟動追蹤主控件。</span><span class="sxs-lookup"><span data-stu-id="2ec23-153">Restart the tracking host.</span></span>
2. <span data-ttu-id="2ec23-154">建立專用的追蹤主控件。</span><span class="sxs-lookup"><span data-stu-id="2ec23-154">Create a dedicated tracking host.</span></span> <span data-ttu-id="2ec23-155">安裝 BizTalk Server 時，可能會在啟用追蹤**BizTalk Server 應用程式 1**主機。</span><span class="sxs-lookup"><span data-stu-id="2ec23-155">When BizTalk Server is installed, tracking may be enabled on the **BizTalk Server Application 1** host.</span></span> <span data-ttu-id="2ec23-156">一般而言，此應用程式也會用來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="2ec23-156">Typically, this application is also used to process messages.</span></span> <span data-ttu-id="2ec23-157">建立專用的追蹤主控件使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2ec23-157">Create a dedicated tracking host using the following steps:</span></span> 

    1. <span data-ttu-id="2ec23-158">在 BizTalk Server 管理中，開啟 BizTalk Server 應用程式 1 主控件的屬性，然後取消核取**允許主控件追蹤**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-158">In BizTalk Server Administration, open the properties of the BizTalk Server Application 1 host, and uncheck **Allow Host Tracking**.</span></span> <span data-ttu-id="2ec23-159">重新啟動此主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ec23-159">Restart this host instance.</span></span>

    2. <span data-ttu-id="2ec23-160">建立新的主機名稱為**追蹤**，並檢查**允許主控件追蹤**。</span><span class="sxs-lookup"><span data-stu-id="2ec23-160">Create a new host named **Tracking**, and check **Allow Host Tracking**.</span></span> <span data-ttu-id="2ec23-161">建立主控件執行個體，並將它啟動。</span><span class="sxs-lookup"><span data-stu-id="2ec23-161">Create a host instance, and start it.</span></span>

<span data-ttu-id="2ec23-162">現在，再次查詢 BizTalkMsgBoxDb TrackingData_2_x 資料表。</span><span class="sxs-lookup"><span data-stu-id="2ec23-162">Now, query the BizTalkMsgBoxDb TrackingData_2_x tables again.</span></span> <span data-ttu-id="2ec23-163">如果資料表是空的資料移動，而且應該開始在 Application Insights 中顯示。</span><span class="sxs-lookup"><span data-stu-id="2ec23-163">If the tables are empty, then the data was moved, and should start displaying in Application Insights.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="2ec23-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ec23-164">See also</span></span>
 [<span data-ttu-id="2ec23-165">設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="2ec23-165">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)