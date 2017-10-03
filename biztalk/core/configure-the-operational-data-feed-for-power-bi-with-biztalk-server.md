---
title: "設定操作資料摘要與 BizTalk Server 的 Power bi |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: "11"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 09b1b1fd7f350e168b2bb13d6bee2e45c12d49cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-operational-data-feed-for-power-bi-with-biztalk-server"></a><span data-ttu-id="c4bad-102">設定操作資料摘要與 BizTalk Server 的 Power bi</span><span class="sxs-lookup"><span data-stu-id="c4bad-102">Configure the operational data feed for Power BI with BizTalk Server</span></span>
<span data-ttu-id="c4bad-103">讀取透過 oData 摘要中所提供的操作資料[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4bad-103">Read operational data provided through an oData feed in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

<span data-ttu-id="c4bad-104">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** 、 將追蹤傳送到 Power BI 使用 Power BI 範本提供，或建立您自己。</span><span class="sxs-lookup"><span data-stu-id="c4bad-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, send tracking to Power BI using the Power BI template provided, or create your own.</span></span> 

## <a name="what-is-operational-data"></a><span data-ttu-id="c4bad-105">什麼是操作資料</span><span class="sxs-lookup"><span data-stu-id="c4bad-105">What is operational data</span></span>
<span data-ttu-id="c4bad-106">操作資料是有關的執行個體和訊息通過您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="c4bad-106">Operational data is information on the instances and messages flowing through your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="c4bad-107">操作資料摘要是相同的資料取得查看中的 群組中樞[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]主控台。</span><span class="sxs-lookup"><span data-stu-id="c4bad-107">The operational data feed is the same data you get looking at Group Hub in the [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] console.</span></span> <span data-ttu-id="c4bad-108">可存取的資料，且查詢使用視覺化工具，包括 Power BI。</span><span class="sxs-lookup"><span data-stu-id="c4bad-108">The data can be accessed and queried using visualization tools, including Power BI.</span></span> 

<span data-ttu-id="c4bad-109">摘要會包含下表的資料：</span><span class="sxs-lookup"><span data-stu-id="c4bad-109">The feed includes the following data tables:</span></span>
* <span data-ttu-id="c4bad-110">應用程式資料</span><span class="sxs-lookup"><span data-stu-id="c4bad-110">Application data</span></span>
* <span data-ttu-id="c4bad-111">AS2 狀態記錄</span><span class="sxs-lookup"><span data-stu-id="c4bad-111">AS2 Status Records</span></span>
* <span data-ttu-id="c4bad-112">批次的資訊</span><span class="sxs-lookup"><span data-stu-id="c4bad-112">Batching information</span></span>
* <span data-ttu-id="c4bad-113">執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="c4bad-113">Instance information</span></span>
* <span data-ttu-id="c4bad-114">交換彙總記錄</span><span class="sxs-lookup"><span data-stu-id="c4bad-114">Interchange Aggregations Records</span></span>
* <span data-ttu-id="c4bad-115">交換狀態記錄</span><span class="sxs-lookup"><span data-stu-id="c4bad-115">Interchange Status Records</span></span>
* <span data-ttu-id="c4bad-116">訊息</span><span class="sxs-lookup"><span data-stu-id="c4bad-116">Messages</span></span>
* <span data-ttu-id="c4bad-117">訂閱</span><span class="sxs-lookup"><span data-stu-id="c4bad-117">Subscriptions</span></span>
* <span data-ttu-id="c4bad-118">追蹤的事件</span><span class="sxs-lookup"><span data-stu-id="c4bad-118">Tracked Events</span></span>
* <span data-ttu-id="c4bad-119">交易報表</span><span class="sxs-lookup"><span data-stu-id="c4bad-119">Transaction reports</span></span>
* <span data-ttu-id="c4bad-120">交易集</span><span class="sxs-lookup"><span data-stu-id="c4bad-120">Transaction sets</span></span>

> [!TIP]
> <span data-ttu-id="c4bad-121">[PowerBI.com](http://powerbi.microsoft.com)是了解，並深入了解 Power BI 的絕佳資源。</span><span class="sxs-lookup"><span data-stu-id="c4bad-121">[PowerBI.com](http://powerbi.microsoft.com) is a great resource to understand and learn more about Power BI.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4bad-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="c4bad-122">Prerequisites</span></span>
* <span data-ttu-id="c4bad-123">下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/)擁有網路存取權的任何電腦上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4bad-123">Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) on any computer that has network access to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="c4bad-124">安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4bad-124">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="c4bad-125">在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4bad-125">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c4bad-126">在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。</span><span class="sxs-lookup"><span data-stu-id="c4bad-126">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="c4bad-127">請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="c4bad-127">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span> 

## <a name="enable-operational-data-feed"></a><span data-ttu-id="c4bad-128">啟用操作的資料摘要</span><span class="sxs-lookup"><span data-stu-id="c4bad-128">Enable operational data feed</span></span>

1. <span data-ttu-id="c4bad-129">以系統管理員身分執行 Windows PowerShell (**啟動**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。</span><span class="sxs-lookup"><span data-stu-id="c4bad-129">Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**).</span></span> 
2. <span data-ttu-id="c4bad-130">瀏覽的資料夾位置[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]安裝**Program Files (x86)/Microsoft BizTalk Server 2016**</span><span class="sxs-lookup"><span data-stu-id="c4bad-130">Browse to the folder where [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] is installed **Program Files (x86)/Microsoft BizTalk Server 2016**</span></span>
3. <span data-ttu-id="c4bad-131">執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c4bad-131">Run the following command.</span></span> <span data-ttu-id="c4bad-132">請務必更新您`website`， `domain\user`， `password`，和`domain\group`以您的值：</span><span class="sxs-lookup"><span data-stu-id="c4bad-132">Be sure to update your `website`, `domain\user`, `password`, and `domain\group` with your values:</span></span> 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName '<Default Web Site>' -ApplicationPool <operationalDataServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group1>, <domain>\<group2>'
    ```
4. <span data-ttu-id="c4bad-133">執行指令碼之後，瀏覽新的 IIS 應用程式：</span><span class="sxs-lookup"><span data-stu-id="c4bad-133">After you run the script, browse the new IIS Application:</span></span>  
    1. <span data-ttu-id="c4bad-134">開啟網頁瀏覽器</span><span class="sxs-lookup"><span data-stu-id="c4bad-134">Open your web browser</span></span>
    2. <span data-ttu-id="c4bad-135">移至**http://localhost/BizTalkOperationalDataService**</span><span class="sxs-lookup"><span data-stu-id="c4bad-135">Go to **http://localhost/BizTalkOperationalDataService**</span></span>

## <a name="use-the-power-bi-template"></a><span data-ttu-id="c4bad-136">使用 Power BI 範本</span><span class="sxs-lookup"><span data-stu-id="c4bad-136">Use the Power BI template</span></span>
<span data-ttu-id="c4bad-137">若要存取 Power BI 範本檔案，並使用 microsoft 提供的視覺效果，使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c4bad-137">To access the Power BI Template file, and use the provided visualization from Microsoft, use the following steps:</span></span>

1. <span data-ttu-id="c4bad-138">下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/)。</span><span class="sxs-lookup"><span data-stu-id="c4bad-138">Download and install the [Power BI Desktop](https://powerbi.microsoft.com/desktop/).</span></span>
2. <span data-ttu-id="c4bad-139">瀏覽至您的 BizTalk Server 資料夾下**Program Files (x86) \Microsoft BizTalk Server 2016\OperationalDataService**。</span><span class="sxs-lookup"><span data-stu-id="c4bad-139">Browse to your BizTalk Server folder under **Program Files (x86)\Microsoft BizTalk Server 2016\OperationalDataService**.</span></span>
3. <span data-ttu-id="c4bad-140">開啟**BizTalkOperationalData.pbit**檔案。</span><span class="sxs-lookup"><span data-stu-id="c4bad-140">Open the **BizTalkOperationalData.pbit** file.</span></span>
4. <span data-ttu-id="c4bad-141">當系統提示您從 Power BI，貼上**http://localhost/\<yourWebSite\>** 您建立的 OData 摘要的 URL。</span><span class="sxs-lookup"><span data-stu-id="c4bad-141">When prompted from Power BI, paste the **http://localhost/\<yourWebSite\>** URL that you created for your OData feed.</span></span> <span data-ttu-id="c4bad-142">例如，輸入**http://localhost/OperationalDataService**。</span><span class="sxs-lookup"><span data-stu-id="c4bad-142">For example, enter **http://localhost/OperationalDataService**.</span></span> 

    <span data-ttu-id="c4bad-143">您的 URL 看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4bad-143">Your URL looks similar to the following:</span></span> 
    
    ![貼上 Power BI 範本檔案的 OData URL](../core/media/pasteurltopowerbitempaltefile.PNG)

5. <span data-ttu-id="c4bad-145">選取**負載**來填入您的 Power BI 報表中的欄位。</span><span class="sxs-lookup"><span data-stu-id="c4bad-145">Select **Load** to populate the fields in your Power BI report.</span></span> 
6. <span data-ttu-id="c4bad-146">範本檔案會自動產生的資訊和可用的資料表，從 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="c4bad-146">The Template file automatically generates the information and tables available from the OData feed.</span></span>

<span data-ttu-id="c4bad-147">操作資料公開透過電腦和可存取，並根據權限的其他應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="c4bad-147">The operational data is exposed through the computer, and can be accessed and executed by other applications based on permissions.</span></span> 

<span data-ttu-id="c4bad-148">若要深入了解 Power BI 中，以及如何發佈報表線上移至[PowerBI.com](http://powerbi.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="c4bad-148">To learn more about Power BI, and how to publish the report online go to [PowerBI.com](http://powerbi.microsoft.com)</span></span>

## <a name="see-also"></a><span data-ttu-id="c4bad-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4bad-149">See also</span></span>

[<span data-ttu-id="c4bad-150">深入了解 Power BI</span><span class="sxs-lookup"><span data-stu-id="c4bad-150">Learn more about Power BI</span></span>](https://www.powerbi.com)  
[<span data-ttu-id="c4bad-151">設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="c4bad-151">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)