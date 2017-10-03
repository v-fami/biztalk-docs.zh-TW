---
title: "將追蹤資料傳送至 Azure Application Insights 使用 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: "10"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: f587c3049e191505c87ba456b5ddfd41011862c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="send-tracking-data-to-azure-application-insights-using-biztalk-server"></a><span data-ttu-id="89177-102">將追蹤資料傳送至 Azure Application Insights 使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="89177-102">Send tracking data to Azure Application Insights using BizTalk Server</span></span>
<span data-ttu-id="89177-103">傳送[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]Azure 應用程式 Inisights 追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="89177-103">Send [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] tracking data to Azure Application Inisights.</span></span> 

<span data-ttu-id="89177-104">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，您可以處理，並將您的追蹤資料傳送至 Azure Application Insights。</span><span class="sxs-lookup"><span data-stu-id="89177-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can process and send your tracking data to Azure Application Insights.</span></span> <span data-ttu-id="89177-105">使用 Application Insights 功能來追蹤您的執行個體從接收埠、 傳送埠和協調流程。</span><span class="sxs-lookup"><span data-stu-id="89177-105">Use the Application Insights features to track your instances from receive ports, send ports, and orchestrations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89177-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="89177-106">Prerequisites</span></span>
* <span data-ttu-id="89177-107">建立的新執行個體[Application Insights](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)</span><span class="sxs-lookup"><span data-stu-id="89177-107">Create a new instance of [Application Insights](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)</span></span>
* <span data-ttu-id="89177-108">安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89177-108">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

## <a name="enable-analytics-for-your-environment"></a><span data-ttu-id="89177-109">啟用分析為您的環境</span><span class="sxs-lookup"><span data-stu-id="89177-109">Enable analytics for your environment</span></span>

1. <span data-ttu-id="89177-110">開啟**BizTalk Server 管理**主控台中，展開**BizTalk 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後選取**設定**.</span><span class="sxs-lookup"><span data-stu-id="89177-110">Open the **BizTalk Server Administration** console, expand **BizTalk Administration**, right-click the **BizTalk Group**, and select **Settings**.</span></span> 
2. <span data-ttu-id="89177-111">請檢查**啟用群組層級分析**。</span><span class="sxs-lookup"><span data-stu-id="89177-111">Check **Enable group-level analytics**.</span></span>
3. <span data-ttu-id="89177-112">如**目標類型**，選取**Application Insight**從清單中。</span><span class="sxs-lookup"><span data-stu-id="89177-112">For the **Target type**, select **Application Insight** from the list.</span></span>
4. <span data-ttu-id="89177-113">如**連接參數**，輸入您的 Application Insights **[檢測金鑰](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)** （可在 Azure 入口網站）。</span><span class="sxs-lookup"><span data-stu-id="89177-113">For the **Connection parameters**, enter your Application Insights **[instrumentation key](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)** (available in the Azure portal).</span></span>

    <span data-ttu-id="89177-114">群組設定看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="89177-114">Your Group settings look similar to the following:</span></span> 

    ![啟用分析為您的環境](../core/media/environmentsettingapplicationinishgt.PNG)

5. <span data-ttu-id="89177-116">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="89177-116">Select **OK** to save your changes.</span></span> 

<span data-ttu-id="89177-117">一旦啟用[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]已準備好傳送至 Application Insights 資料。</span><span class="sxs-lookup"><span data-stu-id="89177-117">Once enabled, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] is ready to transmit data to Application Insights.</span></span> <span data-ttu-id="89177-118">接下來，啟用您的連接埠和協調流程上的分析。</span><span class="sxs-lookup"><span data-stu-id="89177-118">Next, enable analytics on your ports and orchestrations.</span></span> 

## <a name="enable-analytics-on-your-artifacts"></a><span data-ttu-id="89177-119">啟用您的成品上的分析</span><span class="sxs-lookup"><span data-stu-id="89177-119">Enable analytics on your artifacts</span></span>

1. <span data-ttu-id="89177-120">在 BizTalk Server 管理，以滑鼠右鍵按一下**接收埠**，**傳送埠**或**協調流程**，然後選取**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="89177-120">In BizTalk Server Administration, right-click a **receive port**, **send port** or **orchestration**, and select **Tracking**.</span></span>
2. <span data-ttu-id="89177-121">在下**分析**，檢查**啟用分析**。</span><span class="sxs-lookup"><span data-stu-id="89177-121">Under **Analytics**, check **Enable Analytics**.</span></span> <span data-ttu-id="89177-122">這項設定會啟動追蹤，以及將傳送至 Application Insights 從成品資料。</span><span class="sxs-lookup"><span data-stu-id="89177-122">This setting starts tracking and transmitting data from the artifact to Application Insights.</span></span>

    <span data-ttu-id="89177-123">成品設定看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="89177-123">Your artifact settings look similar to the following:</span></span> 
    
    ![協調流程的追蹤資料](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. <span data-ttu-id="89177-125">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="89177-125">Select **OK** to save your changes.</span></span>

<span data-ttu-id="89177-126">接下來，執行以查看您的資料的 Application Insights 中的查詢。</span><span class="sxs-lookup"><span data-stu-id="89177-126">Next, run queries within Application Insights to see your data.</span></span>  

> [!TIP]
> <span data-ttu-id="89177-127">若要深入組織資料的更多其他系統連接 BizTalk Server 的分析。</span><span class="sxs-lookup"><span data-stu-id="89177-127">Connect your BizTalk Server Analytics with other systems to gain even more insight into your organizations data.</span></span>

## <a name="run-queries-on-your-data"></a><span data-ttu-id="89177-128">在您的資料上執行查詢</span><span class="sxs-lookup"><span data-stu-id="89177-128">Run queries on your data</span></span>
<span data-ttu-id="89177-129">一旦將資料傳送至 Application Insights，您可以使用在 Azure 中的分析工具來建立進階的查詢、 及分析您的資料。</span><span class="sxs-lookup"><span data-stu-id="89177-129">Once the data is sent to Application Insights, you can use the analytics tools within Azure to create advanced queries, and analyze your data.</span></span>

1. <span data-ttu-id="89177-130">登入[Azure 入口網站](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="89177-130">Sign in to the [Azure Portal](https://portal.azure.com).</span></span>
2. <span data-ttu-id="89177-131">開啟 Application Insights 資源，並選取**分析**。</span><span class="sxs-lookup"><span data-stu-id="89177-131">Open your Application Insights resource, and select **Analytics**.</span></span>
3. <span data-ttu-id="89177-132">選取**使用量**，並執行所提供的查詢。</span><span class="sxs-lookup"><span data-stu-id="89177-132">Select **usage**, and run the query provided.</span></span>

    > [!TIP]
    > <span data-ttu-id="89177-133">深入了解如何在 Application Insights 中撰寫查詢[Application Insights 中的分析](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)。</span><span class="sxs-lookup"><span data-stu-id="89177-133">Learn more about how to write queries in Application Insights at [Analytics in Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="89177-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89177-134">See also</span></span>
 [<span data-ttu-id="89177-135">設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="89177-135">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)