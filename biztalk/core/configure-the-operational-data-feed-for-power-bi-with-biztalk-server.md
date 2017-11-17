---
title: "啟用 Power BI |Microsoft 文件"
description: "安裝 BizTalk Server 中的功能套件中的 Power BI 範本"
ms.custom: fp1
ms.date: 11/06/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d3b3dde09351b9a0aa021ef28645cb114495152
ms.sourcegitcommit: 30189176c44873e3de42cc5f2b8951da51ffd251
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="configure-the-operational-data-feed-for-power-bi-with-biztalk-server"></a><span data-ttu-id="bf3f6-103">設定操作資料摘要與 BizTalk Server 的 Power bi</span><span class="sxs-lookup"><span data-stu-id="bf3f6-103">Configure the operational data feed for Power BI with BizTalk Server</span></span>

<span data-ttu-id="bf3f6-104">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** 、 將追蹤傳送到 Power BI 使用 Power BI 範本提供，或建立您自己。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, send tracking to Power BI using the Power BI template provided, or create your own.</span></span> 

## <a name="what-is-operational-data"></a><span data-ttu-id="bf3f6-105">什麼是操作資料</span><span class="sxs-lookup"><span data-stu-id="bf3f6-105">What is operational data</span></span>
<span data-ttu-id="bf3f6-106">操作資料是有關的執行個體和訊息通過您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-106">Operational data is information on the instances and messages flowing through your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="bf3f6-107">操作資料摘要是相同的資料取得查看中的 群組中樞[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-107">The operational data feed is the same data you get looking at Group Hub in [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span> <span data-ttu-id="bf3f6-108">資料存取，且查詢使用視覺化工具，包括 Power BI。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-108">The data is accessed and queried using visualization tools, including Power BI.</span></span> 

<span data-ttu-id="bf3f6-109">摘要會包含下表的資料：</span><span class="sxs-lookup"><span data-stu-id="bf3f6-109">The feed includes the following data tables:</span></span>
* <span data-ttu-id="bf3f6-110">應用程式資料</span><span class="sxs-lookup"><span data-stu-id="bf3f6-110">Application data</span></span>
* <span data-ttu-id="bf3f6-111">AS2 狀態記錄</span><span class="sxs-lookup"><span data-stu-id="bf3f6-111">AS2 Status Records</span></span>
* <span data-ttu-id="bf3f6-112">批次的資訊</span><span class="sxs-lookup"><span data-stu-id="bf3f6-112">Batching information</span></span>
* <span data-ttu-id="bf3f6-113">執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="bf3f6-113">Instance information</span></span>
* <span data-ttu-id="bf3f6-114">交換彙總記錄</span><span class="sxs-lookup"><span data-stu-id="bf3f6-114">Interchange Aggregations Records</span></span>
* <span data-ttu-id="bf3f6-115">交換狀態記錄</span><span class="sxs-lookup"><span data-stu-id="bf3f6-115">Interchange Status Records</span></span>
* <span data-ttu-id="bf3f6-116">訊息</span><span class="sxs-lookup"><span data-stu-id="bf3f6-116">Messages</span></span>
* <span data-ttu-id="bf3f6-117">訂閱</span><span class="sxs-lookup"><span data-stu-id="bf3f6-117">Subscriptions</span></span>
* <span data-ttu-id="bf3f6-118">追蹤的事件</span><span class="sxs-lookup"><span data-stu-id="bf3f6-118">Tracked Events</span></span>
* <span data-ttu-id="bf3f6-119">交易報表</span><span class="sxs-lookup"><span data-stu-id="bf3f6-119">Transaction reports</span></span>
* <span data-ttu-id="bf3f6-120">交易集</span><span class="sxs-lookup"><span data-stu-id="bf3f6-120">Transaction sets</span></span>

> [!TIP]
> <span data-ttu-id="bf3f6-121">[PowerBI.com](http://powerbi.microsoft.com)是了解，並深入了解 Power BI 的絕佳資源。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-121">[PowerBI.com](http://powerbi.microsoft.com) is a great resource to understand and learn more about Power BI.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bf3f6-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="bf3f6-122">Prerequisites</span></span>
* <span data-ttu-id="bf3f6-123">下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/)擁有網路存取權的任何電腦上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf3f6-123">Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) on any computer that has network access to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="bf3f6-124">安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf3f6-124">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="bf3f6-125">在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-125">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="bf3f6-126">在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-126">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="bf3f6-127">請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-127">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span> <span data-ttu-id="bf3f6-128">確認已安裝 IIS，藉由開啟**Internet Information Services 管理員**。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-128">Confirm IIS is installed by opening **Internet Information Services Manager**.</span></span> 

## <a name="step-1-enable-operational-data"></a><span data-ttu-id="bf3f6-129">步驟 1： 啟用操作資料</span><span class="sxs-lookup"><span data-stu-id="bf3f6-129">Step 1: Enable operational data</span></span>

1. <span data-ttu-id="bf3f6-130">以系統管理員身分執行 Windows PowerShell (**啟動**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-130">Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**).</span></span> 
2. <span data-ttu-id="bf3f6-131">移至 BizTalk 安裝資料夾 (例如，輸入： `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`)。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-131">Go to the BizTalk installation folder (for example, type: `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`).</span></span>
3. <span data-ttu-id="bf3f6-132">在下列文字，取代`Default Web Site`， `operationalDataServiceAppPool`， `domain\user`， `password`，和`domain\group`以您的值：</span><span class="sxs-lookup"><span data-stu-id="bf3f6-132">In the following text, replace `Default Web Site`, `operationalDataServiceAppPool`, `domain\user`, `password`, and `domain\group` with your values:</span></span>

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName '<Default Web Site>' -ApplicationPool <operationalDataServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group1>, <domain>\<group2>'
    ```

    <span data-ttu-id="bf3f6-133">在下列範例中，我們使用`Default Web Site`，建立名為應用程式集區`PowerBIAppPool`，執行做為 appPool`bootcampbts2016\btsservice`帳戶，請使用`BIZTALK-serviceacct`做為使用者帳戶密碼，並提供`BizTalk Server Administrators`群組權限。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-133">In the following example, we use the `Default Web Site`, create an application pool named `PowerBIAppPool`, run the appPool as the `bootcampbts2016\btsservice` account, use `BIZTALK-serviceacct` as the user account password, and give the `BizTalk Server Administrators` group permissions.</span></span> <span data-ttu-id="bf3f6-134">請務必輸入下列項目，包括單一引號周圍有空格的值：</span><span class="sxs-lookup"><span data-stu-id="bf3f6-134">Be sure to enter the following, including the single quotes surrounding values with spaces:</span></span> 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName 'Default Web Site' -ApplicationPool PowerBIAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
    ```

    <span data-ttu-id="bf3f6-135">完成時，IIS 內建立 BizTalkOperationalDataService 應用程式：</span><span class="sxs-lookup"><span data-stu-id="bf3f6-135">When complete, the BizTalkOperationalDataService application is created within IIS:</span></span>  
    ![BizTalkMOperationalDataServer 應用程式](../core/media/biztalkmanagementservice-apppool.png)


4. <span data-ttu-id="bf3f6-137">若要確認它是否運作，瀏覽至`http://localhost/OperationalDataService`。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-137">To confirm it’s working, browse to `http://localhost/OperationalDataService`.</span></span> 

    <span data-ttu-id="bf3f6-138">如果系統會提示您登入，是您在上一個步驟中輸入 「 網域 \ 群組成員的帳戶登入 (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`)。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-138">If you are prompted to sign-in, sign in with an account that is member of the domain\group you entered in the previous step (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`).</span></span> 

    <span data-ttu-id="bf3f6-139">如果系統提示您開啟或儲存 BizTalkOperationalDataService.json，然後完成您的安裝。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-139">If you are prompted to open or save BizTalkOperationalDataService.json, then your install completed.</span></span> <span data-ttu-id="bf3f6-140">您可以將它儲存在本機，然後再將它開啟在記事本或 Visual Studio 以查看內容中。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-140">You can save it locally, and then open it in notepad or Visual Studio to see the contents.</span></span> 

> [!WARNING]
> <span data-ttu-id="bf3f6-141">在 IIS 中的 BizTalkOperationalDataService 應用程式會使用 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-141">The BizTalkOperationalDataService application in IIS uses a web.config file.</span></span> <span data-ttu-id="bf3f6-142">在 web.config 中的項目**會區分大小寫**。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-142">Elements within web.config **are case sensitive**.</span></span> <span data-ttu-id="bf3f6-143">因此當您執行 Windows PowerShell 指令碼時，必須輸入正確的大小寫的`-AuthorizationRoles`值。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-143">So when you execute the Windows PowerShell script, be sure to enter the correct case for `-AuthorizationRoles` value.</span></span> <span data-ttu-id="bf3f6-144">如果您不確定的情況下，以下是可以輕鬆地找出：</span><span class="sxs-lookup"><span data-stu-id="bf3f6-144">If you’re not sure of the case, here’s an easy way to find out:</span></span> 
> 
> 1. <span data-ttu-id="bf3f6-145">開啟**電腦管理**，然後展開**本機使用者和群組**。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-145">Open **Computer Management**, and expand **Local Users and Groups**.</span></span>
> 2. <span data-ttu-id="bf3f6-146">選取**群組**，向下捲動至**SQLServer...**</span><span class="sxs-lookup"><span data-stu-id="bf3f6-146">Select **Groups**, and scroll down to the **SQLServer…**</span></span> <span data-ttu-id="bf3f6-147">群組。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-147">groups.</span></span> 
> 3. <span data-ttu-id="bf3f6-148">在下列範例中，請注意**BOOTCAMPBTS2016**中全部大寫。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-148">In the following example, notice **BOOTCAMPBTS2016** is in all caps.</span></span> <span data-ttu-id="bf3f6-149">如果您看到全部大寫，然後在 全部大寫中輸入電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-149">If you see all caps, then enter the computer name in all caps.</span></span> 
> 
> ![電腦名稱是以全部大寫](../core/media/groups-case.png)

## <a name="step-2-use-the-template-in-power-bi"></a><span data-ttu-id="bf3f6-151">步驟 2： 使用 Power BI 中的範本</span><span class="sxs-lookup"><span data-stu-id="bf3f6-151">Step 2: Use the template in Power BI</span></span>

1. <span data-ttu-id="bf3f6-152">下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/) BizTalk 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-152">Download and install the [Power BI Desktop](https://powerbi.microsoft.com/desktop/) on your BizTalk Server.</span></span> <span data-ttu-id="bf3f6-153">您可以選取以開啟它，這是選擇性。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-153">You can select to open it, which is optional.</span></span> <span data-ttu-id="bf3f6-154">如果您有工作或學校帳戶，您可能需要 Power BI 存取。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-154">If you have a work or school account, you may have access to Power BI.</span></span> <span data-ttu-id="bf3f6-155">請嘗試登入該帳戶。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-155">Try signing in with that account.</span></span> <span data-ttu-id="bf3f6-156">或者，您可以試試免費註冊之後。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-156">Or, you can try it for free after signing up.</span></span> 
2. <span data-ttu-id="bf3f6-157">開啟`\Program Files (x86)\Microsoft BizTalk Server 2016\OperationalDataService`資料夾，然後開啟`BizTalkOperationalData.pbit`檔案：</span><span class="sxs-lookup"><span data-stu-id="bf3f6-157">Open the `\Program Files (x86)\Microsoft BizTalk Server 2016\OperationalDataService` folder, and open the `BizTalkOperationalData.pbit` file:</span></span>  
<span data-ttu-id="bf3f6-158">![開啟 pbit 檔案](../core/media/operational-data-pbit.png)</span><span class="sxs-lookup"><span data-stu-id="bf3f6-158">![Open pbit file](../core/media/operational-data-pbit.png)</span></span>

3. <span data-ttu-id="bf3f6-159">Power BI desktop 會開啟，並提示您輸入的 URL。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-159">Power BI desktop opens, and you are prompted for a URL.</span></span> <span data-ttu-id="bf3f6-160">輸入`http://localhost/<yourWebSite>`您建立的 OData 摘要的 URL。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-160">Enter the `http://localhost/<yourWebSite>` URL that you created for your OData feed.</span></span> <span data-ttu-id="bf3f6-161">例如，輸入`http://localhost/OperationalDataService`。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-161">For example, enter `http://localhost/OperationalDataService`.</span></span> <span data-ttu-id="bf3f6-162">您的 URL 看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf3f6-162">Your URL looks similar to the following:</span></span>  
<span data-ttu-id="bf3f6-163">![輸入的 URL](../core/media/operational-data-url.png)</span><span class="sxs-lookup"><span data-stu-id="bf3f6-163">![Enter the URL](../core/media/operational-data-url.png)</span></span>

5. <span data-ttu-id="bf3f6-164">選取**負載**。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-164">Select **Load**.</span></span> <span data-ttu-id="bf3f6-165">載入視窗，並連接到不同的 oData 來源 BizTalkOperationalDataService.json 檔案中。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-165">The window loads and connects to the different oData sources in the BizTalkOperationalDataService.json file.</span></span> <span data-ttu-id="bf3f6-166">完成之後，儀表板會顯示您的環境相關的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-166">When it completes, the dashboard shows details about your environment.</span></span>

## <a name="couldnt-authenticate"></a><span data-ttu-id="bf3f6-167">無法驗證</span><span class="sxs-lookup"><span data-stu-id="bf3f6-167">Couldn't authenticate</span></span>
<span data-ttu-id="bf3f6-168">如果您收到`couldn't authenticate with the credentials provided`訊息類似於下列項目，則很可能您的應用程式集區識別沒有足夠的存取權，BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-168">If you get `couldn't authenticate with the credentials provided` message similar to the following, then it’s possible your application pool identity doesn’t have enough access to the BizTalk Server databases.</span></span> <span data-ttu-id="bf3f6-169">您可以變更 IIS 中的應用程式集區身分識別具有更多的權限的帳戶至或許您登入的使用者帳戶 （具有本機系統管理員權限）。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-169">You can change the appPool identity within IIS to an account with more privileges, maybe your signed-in user account (which has local admin privileges).</span></span> 

![無法使用提供的認證進行驗證](../core/media/operational-data-authentication-error.png)

## <a name="do-more"></a><span data-ttu-id="bf3f6-171">執行其他動作</span><span class="sxs-lookup"><span data-stu-id="bf3f6-171">Do more</span></span>
<span data-ttu-id="bf3f6-172">這只是一個開始。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-172">This is just the beginning.</span></span> <span data-ttu-id="bf3f6-173">Power BI 也有可安裝在 BizTalk Server 的閘道。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-173">Power BI also has a gateway that can be installed on the BizTalk Server.</span></span> <span data-ttu-id="bf3f6-174">您可以使用閘道，來發行您的儀表板、 取得即時資料，並建立排程來重新整理儀表板。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-174">Using the gateway, you can publish your dashboard, get real-time data, and create a schedule to refresh the dashboard.</span></span> <span data-ttu-id="bf3f6-175">下列部落格出色詳述這些步驟：</span><span class="sxs-lookup"><span data-stu-id="bf3f6-175">The following blog does a great job detailing these steps:</span></span> 

[<span data-ttu-id="bf3f6-176">如何發佈 BizTalk 上 Power BI – 逐步設定操作的資料</span><span class="sxs-lookup"><span data-stu-id="bf3f6-176">How to publish BizTalk operational data on Power BI – Step-by-step configuration</span></span>](https://blog.sandro-pereira.com/2017/05/07/biztalk-server-2016-feature-pack-1-how-to-publish-biztalk-operational-data-power-bi-step-by-step-configuration-part-3/)

<span data-ttu-id="bf3f6-177">[引導式學習](https://powerbi.microsoft.com/guided-learning/)也是了解 Power BI 中，有關的詳細資訊，以及可以執行的所有作業的好地方。</span><span class="sxs-lookup"><span data-stu-id="bf3f6-177">The [Guided Learning](https://powerbi.microsoft.com/guided-learning/) is also a great place to learn more about Power BI, and all the things you can do.</span></span> 

## <a name="see-also"></a><span data-ttu-id="bf3f6-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf3f6-178">See also</span></span>

[<span data-ttu-id="bf3f6-179">深入了解 Power BI</span><span class="sxs-lookup"><span data-stu-id="bf3f6-179">Learn more about Power BI</span></span>](https://www.powerbi.com)  
[<span data-ttu-id="bf3f6-180">設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="bf3f6-180">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)