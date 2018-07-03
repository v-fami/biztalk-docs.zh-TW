---
title: 讓 Power BI |Microsoft Docs
description: 安裝 BizTalk Server 功能套件在 Power BI 範本
ms.custom: fp1
ms.date: 6/26/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe6d3a97-c7c0-4147-baa9-ee12f93248eb
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bfe842e3b131e6b0fcde75485c1d472320644c3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994175"
---
# <a name="configure-the-power-bi-operational-data-feed-in-biztalk-server"></a><span data-ttu-id="365c9-103">設定 Power BI 操作資料，使用 BizTalk Server 中的摘要</span><span class="sxs-lookup"><span data-stu-id="365c9-103">Configure the Power BI operational data feed in BizTalk Server</span></span>

<span data-ttu-id="365c9-104">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** 、 將追蹤傳送至 Power BI 使用的 Power BI 範本，或建立您自己。</span><span class="sxs-lookup"><span data-stu-id="365c9-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, send tracking to Power BI using the Power BI template provided, or create your own.</span></span> 

## <a name="what-is-operational-data"></a><span data-ttu-id="365c9-105">什麼是作業中的資料</span><span class="sxs-lookup"><span data-stu-id="365c9-105">What is operational data</span></span>
<span data-ttu-id="365c9-106">操作資料是有關的執行個體和郵件流經您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="365c9-106">Operational data is information on the instances and messages flowing through your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="365c9-107">操作資料摘要是相同的資料取得查看中的 群組中樞[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="365c9-107">The operational data feed is the same data you get looking at Group Hub in [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span> <span data-ttu-id="365c9-108">資料存取，並使用視覺效果工具，包括 Power BI 查詢。</span><span class="sxs-lookup"><span data-stu-id="365c9-108">The data is accessed and queried using visualization tools, including Power BI.</span></span> 

<span data-ttu-id="365c9-109">摘要包含下列資料表：</span><span class="sxs-lookup"><span data-stu-id="365c9-109">The feed includes the following data tables:</span></span>
* <span data-ttu-id="365c9-110">應用程式資料</span><span class="sxs-lookup"><span data-stu-id="365c9-110">Application data</span></span>
* <span data-ttu-id="365c9-111">AS2 狀態記錄</span><span class="sxs-lookup"><span data-stu-id="365c9-111">AS2 Status Records</span></span>
* <span data-ttu-id="365c9-112">批次資訊</span><span class="sxs-lookup"><span data-stu-id="365c9-112">Batching information</span></span>
* <span data-ttu-id="365c9-113">執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="365c9-113">Instance information</span></span>
* <span data-ttu-id="365c9-114">交換彙總記錄</span><span class="sxs-lookup"><span data-stu-id="365c9-114">Interchange Aggregations Records</span></span>
* <span data-ttu-id="365c9-115">交換狀態記錄</span><span class="sxs-lookup"><span data-stu-id="365c9-115">Interchange Status Records</span></span>
* <span data-ttu-id="365c9-116">訊息</span><span class="sxs-lookup"><span data-stu-id="365c9-116">Messages</span></span>
* <span data-ttu-id="365c9-117">訂閱</span><span class="sxs-lookup"><span data-stu-id="365c9-117">Subscriptions</span></span>
* <span data-ttu-id="365c9-118">追蹤的事件</span><span class="sxs-lookup"><span data-stu-id="365c9-118">Tracked Events</span></span>
* <span data-ttu-id="365c9-119">交易報表</span><span class="sxs-lookup"><span data-stu-id="365c9-119">Transaction reports</span></span>
* <span data-ttu-id="365c9-120">交易集</span><span class="sxs-lookup"><span data-stu-id="365c9-120">Transaction sets</span></span>

> [!TIP]
> <span data-ttu-id="365c9-121">[PowerBI.com](http://powerbi.microsoft.com)是了解並深入了解 Power BI 的絕佳資源。</span><span class="sxs-lookup"><span data-stu-id="365c9-121">[PowerBI.com](http://powerbi.microsoft.com) is a great resource to understand and learn more about Power BI.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="365c9-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="365c9-122">Prerequisites</span></span>
* <span data-ttu-id="365c9-123">下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/)擁有網路存取權的任何電腦上您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="365c9-123">Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) on any computer that has network access to your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="365c9-124">安裝[Feature Pack 2](https://aka.ms/bts2016fp2)，或更新版本上的功能組件中，您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="365c9-124">Install [Feature Pack 2](https://aka.ms/bts2016fp2), or newer feature pack, on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="365c9-125">在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="365c9-125">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="365c9-126">在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。</span><span class="sxs-lookup"><span data-stu-id="365c9-126">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="365c9-127">請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="365c9-127">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span> <span data-ttu-id="365c9-128">確認 IIS 已安裝 %installationdirectory **Internet Information Services 管理員**。</span><span class="sxs-lookup"><span data-stu-id="365c9-128">Confirm IIS is installed by opening **Internet Information Services Manager**.</span></span> 
* <span data-ttu-id="365c9-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="365c9-129">Optional.</span></span> <span data-ttu-id="365c9-130">安裝和設定[Power BI Gateway](https://powerbi.microsoft.com/gateway/)連接[PowerBI.com](http://powerbi.microsoft.com)與您內部部署的 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="365c9-130">Install and configure a [Power BI Gateway](https://powerbi.microsoft.com/gateway/) to connect [PowerBI.com](http://powerbi.microsoft.com) with your on-premises BizTalk Server.</span></span> <span data-ttu-id="365c9-131">如果您不使用內部部署 BizTalk Server，您不需要閘道。</span><span class="sxs-lookup"><span data-stu-id="365c9-131">If you're not using an on-premises BizTalk Server, then you don't need the gateway.</span></span>

## <a name="step-1-enable-operational-data"></a><span data-ttu-id="365c9-132">步驟 1： 啟用操作資料</span><span class="sxs-lookup"><span data-stu-id="365c9-132">Step 1: Enable operational data</span></span>

1. <span data-ttu-id="365c9-133">以系統管理員身分執行 Windows PowerShell (**開始**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。</span><span class="sxs-lookup"><span data-stu-id="365c9-133">Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**).</span></span> 
2. <span data-ttu-id="365c9-134">移至 BizTalk 安裝資料夾 (例如，輸入： `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`)。</span><span class="sxs-lookup"><span data-stu-id="365c9-134">Go to the BizTalk installation folder (for example, type: `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`).</span></span>
3. <span data-ttu-id="365c9-135">在下列文字，取代`Default Web Site`， `operationalDataServiceAppPool`， `domain\user`， `password`，和`domain\group`以您的值：</span><span class="sxs-lookup"><span data-stu-id="365c9-135">In the following text, replace `Default Web Site`, `operationalDataServiceAppPool`, `domain\user`, `password`, and `domain\group` with your values:</span></span>

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName '<Default Web Site>' -ApplicationPool <operationalDataServiceAppPool> -ApplicationPoolUser <domain>\<user\> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group1\>, <domain>\<group2\>, <domain>\<user\>, <domain>\<user2\>'
    ```

   * <span data-ttu-id="365c9-136">**服務**： 若要設定服務 (**OperationalData**適用於 Power BI)</span><span class="sxs-lookup"><span data-stu-id="365c9-136">**Service**: The service to be configured (**OperationalData** for Power BI)</span></span>
   * <span data-ttu-id="365c9-137">**WebSiteName**： 現有的 IIS 網站上裝載服務。</span><span class="sxs-lookup"><span data-stu-id="365c9-137">**WebSiteName**: The existing IIS web site that hosts the service.</span></span> <span data-ttu-id="365c9-138">預設值是**Default Web Site**。</span><span class="sxs-lookup"><span data-stu-id="365c9-138">The default value is **Default Web Site**.</span></span>
   * <span data-ttu-id="365c9-139">**ApplicationPool**： 服務所使用的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="365c9-139">**ApplicationPool**: The Application Pool used by the service.</span></span> <span data-ttu-id="365c9-140">若有的話，不會建立一個新。</span><span class="sxs-lookup"><span data-stu-id="365c9-140">If it exists, a new one is not created.</span></span> <span data-ttu-id="365c9-141">預設值是**DefaultAppPool**。</span><span class="sxs-lookup"><span data-stu-id="365c9-141">The default value is **DefaultAppPool**.</span></span>
   * <span data-ttu-id="365c9-142">**ApplicationPoolUser**： 設定應用程式集區，以做為此使用者的身分識別執行。</span><span class="sxs-lookup"><span data-stu-id="365c9-142">**ApplicationPoolUser**: Configures the application pool to run as this user identity.</span></span> <span data-ttu-id="365c9-143">必須具有 BizTalk Server 操作員或更高的權限。</span><span class="sxs-lookup"><span data-stu-id="365c9-143">Must have BizTalk Server Operator, or higher privileges.</span></span>
   * <span data-ttu-id="365c9-144">**ApplicationPoolUserPassword**: ApplicationPoolUser 密碼</span><span class="sxs-lookup"><span data-stu-id="365c9-144">**ApplicationPoolUserPassword**: Password for the ApplicationPoolUser</span></span>
   * <span data-ttu-id="365c9-145">**AuthorizationAccount**： 已獲授權的群組或使用者可以使用此服務的清單</span><span class="sxs-lookup"><span data-stu-id="365c9-145">**AuthorizationAccount**: List of authorized Groups or Users that can use this service</span></span>

     <span data-ttu-id="365c9-146">在下列範例中，我們會使用`Default Web Site`，建立名為應用程式集區`PowerBIAppPool`，執行為 appPool`bootcampbts2016\btsservice`帳戶，請使用`BIZTALK-serviceacct`做為使用者帳戶密碼，並提供`BizTalk Server Administrators`群組權限。</span><span class="sxs-lookup"><span data-stu-id="365c9-146">In the following example, we use the `Default Web Site`, create an application pool named `PowerBIAppPool`, run the appPool as the `bootcampbts2016\btsservice` account, use `BIZTALK-serviceacct` as the user account password, and give the `BizTalk Server Administrators` group permissions.</span></span> <span data-ttu-id="365c9-147">請務必輸入下列項目，包括單一引號周圍有空格的值：</span><span class="sxs-lookup"><span data-stu-id="365c9-147">Be sure to enter the following, including the single quotes surrounding values with spaces:</span></span> 

     ```Powershell
     FeaturePack.ConfigureServices.ps1 -Service operationaldata -WebSiteName 'Default Web Site' -ApplicationPool PowerBIAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
     ```

     <span data-ttu-id="365c9-148">完成時，就會在 IIS 中建立 BizTalkOperationalDataService 應用程式：</span><span class="sxs-lookup"><span data-stu-id="365c9-148">When complete, the BizTalkOperationalDataService application is created within IIS:</span></span>  
     ![BizTalkMOperationalDataServer 應用程式](../core/media/biztalkmanagementservice-apppool.png)


4. <span data-ttu-id="365c9-150">若要確認它是否能運作，瀏覽至`http://localhost/BizTalkOperationalDataService`。</span><span class="sxs-lookup"><span data-stu-id="365c9-150">To confirm it’s working, browse to `http://localhost/BizTalkOperationalDataService`.</span></span> 

    <span data-ttu-id="365c9-151">如果系統會提示您登入、 使用您在上一個步驟中輸入 「 網域 \ 群組的成員帳戶登入 (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`)。</span><span class="sxs-lookup"><span data-stu-id="365c9-151">If you are prompted to sign-in, sign in with an account that is member of the domain\group you entered in the previous step (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`).</span></span> 

    <span data-ttu-id="365c9-152">如果系統提示您開啟或儲存 BizTalkOperationalDataService.json，然後完成您的安裝。</span><span class="sxs-lookup"><span data-stu-id="365c9-152">If you are prompted to open or save BizTalkOperationalDataService.json, then your install completed.</span></span> <span data-ttu-id="365c9-153">您可以將它儲存在本機，然後再將它開啟在記事本或 Visual Studio 以查看內容中。</span><span class="sxs-lookup"><span data-stu-id="365c9-153">You can save it locally, and then open it in notepad or Visual Studio to see the contents.</span></span> 

> [!WARNING]
> <span data-ttu-id="365c9-154">在 IIS 中 BizTalkOperationalDataService 應用程式在 web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="365c9-154">The BizTalkOperationalDataService application in IIS uses a web.config file.</span></span> <span data-ttu-id="365c9-155">在 web.config 中的項目**區分大小寫**。</span><span class="sxs-lookup"><span data-stu-id="365c9-155">Elements within web.config **are case sensitive**.</span></span> <span data-ttu-id="365c9-156">因此當您執行 Windows PowerShell 指令碼，請務必輸入正確的大小寫的`-AuthorizationRoles`值。</span><span class="sxs-lookup"><span data-stu-id="365c9-156">So when you execute the Windows PowerShell script, be sure to enter the correct case for `-AuthorizationRoles` value.</span></span> <span data-ttu-id="365c9-157">如果您不確定的情況下，以下是簡單的方法，若要了解：</span><span class="sxs-lookup"><span data-stu-id="365c9-157">If you’re not sure of the case, here’s an easy way to find out:</span></span> 
> 
> 1. <span data-ttu-id="365c9-158">開啟**電腦管理**，展開**本機使用者和群組**。</span><span class="sxs-lookup"><span data-stu-id="365c9-158">Open **Computer Management**, and expand **Local Users and Groups**.</span></span>
> 2. <span data-ttu-id="365c9-159">選取 **群組**，向下捲動至**SQLServer...**</span><span class="sxs-lookup"><span data-stu-id="365c9-159">Select **Groups**, and scroll down to the **SQLServer…**</span></span> <span data-ttu-id="365c9-160">群組。</span><span class="sxs-lookup"><span data-stu-id="365c9-160">groups.</span></span> 
> 3. <span data-ttu-id="365c9-161">在下列範例中，請注意**BOOTCAMPBTS2016**是全部大寫字。</span><span class="sxs-lookup"><span data-stu-id="365c9-161">In the following example, notice **BOOTCAMPBTS2016** is in all caps.</span></span> <span data-ttu-id="365c9-162">如果您看到全部大寫，然後輸入電腦名稱全部大寫。</span><span class="sxs-lookup"><span data-stu-id="365c9-162">If you see all caps, then enter the computer name in all caps.</span></span> 
> 
> ![電腦名稱是全部大寫字](../core/media/groups-case.png)

## <a name="step-2-use-the-template-in-power-bi"></a><span data-ttu-id="365c9-164">步驟 2： 在 Power BI 中使用範本</span><span class="sxs-lookup"><span data-stu-id="365c9-164">Step 2: Use the template in Power BI</span></span>

1. <span data-ttu-id="365c9-165">下載並安裝[Power BI Desktop](https://powerbi.microsoft.com/desktop/) BizTalk 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="365c9-165">Download and install the [Power BI Desktop](https://powerbi.microsoft.com/desktop/) on your BizTalk Server.</span></span> <span data-ttu-id="365c9-166">您可以選取以開啟它，這是選擇性。</span><span class="sxs-lookup"><span data-stu-id="365c9-166">You can select to open it, which is optional.</span></span> <span data-ttu-id="365c9-167">如果您有工作或學校帳戶，您可能會有存取 Power BI。</span><span class="sxs-lookup"><span data-stu-id="365c9-167">If you have a work or school account, you may have access to Power BI.</span></span> <span data-ttu-id="365c9-168">請嘗試登入該帳戶。</span><span class="sxs-lookup"><span data-stu-id="365c9-168">Try signing in with that account.</span></span> <span data-ttu-id="365c9-169">或者，您可以免費試用註冊之後。</span><span class="sxs-lookup"><span data-stu-id="365c9-169">Or, you can try it for free after signing up.</span></span> 
2. <span data-ttu-id="365c9-170">開啟`\Program Files (x86)\Microsoft BizTalk Server 2016\OperationalDataService`資料夾，然後開啟`BizTalkOperationalData.pbit`檔案：</span><span class="sxs-lookup"><span data-stu-id="365c9-170">Open the `\Program Files (x86)\Microsoft BizTalk Server 2016\OperationalDataService` folder, and open the `BizTalkOperationalData.pbit` file:</span></span>  
<span data-ttu-id="365c9-171">![開啟 pbit 檔案](../core/media/operational-data-pbit.png)</span><span class="sxs-lookup"><span data-stu-id="365c9-171">![Open pbit file](../core/media/operational-data-pbit.png)</span></span>

3. <span data-ttu-id="365c9-172">Power BI desktop 便會開啟，並會提示您輸入的 URL。</span><span class="sxs-lookup"><span data-stu-id="365c9-172">Power BI desktop opens, and you are prompted for a URL.</span></span> <span data-ttu-id="365c9-173">輸入`http://localhost/<yourWebSite>`您建立的 OData 摘要的 URL。</span><span class="sxs-lookup"><span data-stu-id="365c9-173">Enter the `http://localhost/<yourWebSite>` URL that you created for your OData feed.</span></span> <span data-ttu-id="365c9-174">例如，輸入`http://localhost/BizTalkOperationalDataService`。</span><span class="sxs-lookup"><span data-stu-id="365c9-174">For example, enter `http://localhost/BizTalkOperationalDataService`.</span></span> <span data-ttu-id="365c9-175">您的 URL 看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="365c9-175">Your URL looks similar to the following:</span></span>  
<span data-ttu-id="365c9-176">![輸入的 URL](../core/media/operational-data-url.png)</span><span class="sxs-lookup"><span data-stu-id="365c9-176">![Enter the URL](../core/media/operational-data-url.png)</span></span>

4. <span data-ttu-id="365c9-177">選取 **負載**。</span><span class="sxs-lookup"><span data-stu-id="365c9-177">Select **Load**.</span></span> <span data-ttu-id="365c9-178">載入視窗，並連接到不同的 oData 來源 BizTalkOperationalDataService.json 檔案中。</span><span class="sxs-lookup"><span data-stu-id="365c9-178">The window loads and connects to the different oData sources in the BizTalkOperationalDataService.json file.</span></span> <span data-ttu-id="365c9-179">完成之後，儀表板會顯示您環境的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="365c9-179">When it completes, the dashboard shows details about your environment.</span></span>

## <a name="couldnt-authenticate"></a><span data-ttu-id="365c9-180">無法驗證</span><span class="sxs-lookup"><span data-stu-id="365c9-180">Couldn't authenticate</span></span>
<span data-ttu-id="365c9-181">如果您收到`couldn't authenticate with the credentials provided`訊息類似於下列項目，則很可能您的應用程式集區身分識別沒有足夠的存取權，BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="365c9-181">If you get `couldn't authenticate with the credentials provided` message similar to the following, then it’s possible your application pool identity doesn’t have enough access to the BizTalk Server databases.</span></span> <span data-ttu-id="365c9-182">您可以變更 IIS 中的應用程式集區識別至具有更多的權限的帳戶可能是您的登入的使用者帳戶 （其具有本機系統管理員權限）。</span><span class="sxs-lookup"><span data-stu-id="365c9-182">You can change the appPool identity within IIS to an account with more privileges, maybe your signed-in user account (which has local admin privileges).</span></span> 

![無法使用提供的認證進行驗證](../core/media/operational-data-authentication-error.png)

## <a name="do-more"></a><span data-ttu-id="365c9-184">執行更多作業</span><span class="sxs-lookup"><span data-stu-id="365c9-184">Do more</span></span>
<span data-ttu-id="365c9-185">這只是開端。</span><span class="sxs-lookup"><span data-stu-id="365c9-185">This is just the beginning.</span></span> <span data-ttu-id="365c9-186">Power BI 也會有可以在內部部署 BizTalk Server 安裝閘道。</span><span class="sxs-lookup"><span data-stu-id="365c9-186">Power BI also has a gateway that can be installed on an on-premises BizTalk Server.</span></span> <span data-ttu-id="365c9-187">使用閘道時，可以發佈您的儀表板，取得即時資料，並建立排程來重新整理儀表板。</span><span class="sxs-lookup"><span data-stu-id="365c9-187">Using the gateway, you can publish your dashboard, get real-time data, and create a schedule to refresh the dashboard.</span></span> <span data-ttu-id="365c9-188">下列部落格直接挑明解詳述這些步驟：</span><span class="sxs-lookup"><span data-stu-id="365c9-188">The following blog does a great job detailing these steps:</span></span> 

* [<span data-ttu-id="365c9-189">如何發佈 Power BI – 逐步設定上的 BizTalk 作業資料</span><span class="sxs-lookup"><span data-stu-id="365c9-189">How to publish BizTalk operational data on Power BI – Step-by-step configuration</span></span>](https://blog.sandro-pereira.com/2017/05/07/biztalk-server-2016-feature-pack-1-how-to-publish-biztalk-operational-data-power-bi-step-by-step-configuration-part-3/)

<span data-ttu-id="365c9-190">[引導式學習](https://powerbi.microsoft.com/guided-learning/)也是深入了解 Power BI 中，以及您可以執行的所有事項的最佳去處。</span><span class="sxs-lookup"><span data-stu-id="365c9-190">The [Guided Learning](https://powerbi.microsoft.com/guided-learning/) is also a great place to learn more about Power BI, and all the things you can do.</span></span> 

## <a name="see-also"></a><span data-ttu-id="365c9-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="365c9-191">See also</span></span>

[<span data-ttu-id="365c9-192">深入了解 Power BI</span><span class="sxs-lookup"><span data-stu-id="365c9-192">Learn more about Power BI</span></span>](https://www.powerbi.com)  
[<span data-ttu-id="365c9-193">設定 Feature Pack</span><span class="sxs-lookup"><span data-stu-id="365c9-193">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)
