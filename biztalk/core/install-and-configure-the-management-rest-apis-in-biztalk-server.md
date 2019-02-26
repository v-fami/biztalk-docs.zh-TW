---
title: 安裝和設定管理 REST Api |Microsoft Docs
description: 查詢中使用管理資料 REST Api 搭配 BizTalk Server 中的 Feature Pack BizTalk 環境的成品
ms.custom: fp1
ms.date: 02/25/2019
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 680b7390462a7a64d3064f621b2011952ba2551c
ms.sourcegitcommit: 0e14c3e018b091d81d0e4a68fafc10f6e31697e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56828563"
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a><span data-ttu-id="48a18-103">安裝和設定 BizTalk Server 中的管理 REST Api</span><span class="sxs-lookup"><span data-stu-id="48a18-103">Install and configure the management REST APIs in BizTalk Server</span></span>

## <a name="what-are-management-data-apis"></a><span data-ttu-id="48a18-104">管理資料的 Api 有哪些？</span><span class="sxs-lookup"><span data-stu-id="48a18-104">What are management data APIs</span></span>
<span data-ttu-id="48a18-105">管理資料的 Api 是可讓您從遠端更新、 加入及查詢中的不同成品的狀態端點您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="48a18-105">Management data APIs are endpoints that let you remotely update, add, and query the status of different artifacts in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="48a18-106">將端點新增使用其餘部分，並隨附的 swagger 定義。</span><span class="sxs-lookup"><span data-stu-id="48a18-106">The endpoints are added using REST, and come with a swagger definition.</span></span> 

<span data-ttu-id="48a18-107">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，沒有安裝這些 REST Api 和其 swagger 定義的 Windows PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="48a18-107">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, there's a Windows PowerShell script that installs these REST APIs, and their swagger definitions.</span></span> <span data-ttu-id="48a18-108">這些 Api 進行 REST 呼叫，從遠端管理連接埠、 協調流程、 合作夥伴、 合約、 管線和更多功能。</span><span class="sxs-lookup"><span data-stu-id="48a18-108">These APIs make REST calls to remotely manage ports, orchestrations, partners, agreements, pipelines, and more.</span></span> 

<span data-ttu-id="48a18-109">若要查看可用的 Api，以及您可以做什麼，請參閱[功能套件的 REST API 參考](https://docs.microsoft.com/rest/api/biztalk/?view=rest-biztalk-2016)。</span><span class="sxs-lookup"><span data-stu-id="48a18-109">To see the available APIs, and what you can do, see [Feature Pack REST API reference](https://docs.microsoft.com/rest/api/biztalk/?view=rest-biztalk-2016).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48a18-110">先決條件</span><span class="sxs-lookup"><span data-stu-id="48a18-110">Prerequisites</span></span>
* <span data-ttu-id="48a18-111">安裝[Feature Pack 2](https://aka.ms/bts2016fp2)上您 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48a18-111">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

* <span data-ttu-id="48a18-112">在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="48a18-112">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="48a18-113">確認 IIS 已安裝 BizTalk Server 上開啟**Internet Information Services 管理員**。</span><span class="sxs-lookup"><span data-stu-id="48a18-113">Confirm IIS is installed on the BizTalk Server by opening **Internet Information Services Manager**.</span></span> 

  <span data-ttu-id="48a18-114">在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。</span><span class="sxs-lookup"><span data-stu-id="48a18-114">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="48a18-115">請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="48a18-115">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span> 

## <a name="step-1-install-the-rest-apis"></a><span data-ttu-id="48a18-116">步驟 1：安裝 REST Api</span><span class="sxs-lookup"><span data-stu-id="48a18-116">Step 1: Install the REST APIs</span></span>

1. <span data-ttu-id="48a18-117">以系統管理員身分執行 Windows PowerShell (**開始**功能表 > 型別**PowerShell** > 以滑鼠右鍵按一下 >**系統管理員身分執行**)。</span><span class="sxs-lookup"><span data-stu-id="48a18-117">Run Windows PowerShell as Administrator (**Start** menu > type **PowerShell** > right click > **Run as administrator**).</span></span> 
2. <span data-ttu-id="48a18-118">移至 BizTalk 安裝資料夾 (例如，輸入： `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`)。</span><span class="sxs-lookup"><span data-stu-id="48a18-118">Go to the BizTalk installation folder (for example, type: `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`).</span></span>
3. <span data-ttu-id="48a18-119">在下列文字，取代`Default Web Site`， `mgmtServiceAppPool`， `domain/user`， `password`，和`domain\group`以您的值：</span><span class="sxs-lookup"><span data-stu-id="48a18-119">In the following text, replace `Default Web Site`, `mgmtServiceAppPool`, `domain/user`, `password`, and `domain\group` with your values:</span></span>

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```

    <span data-ttu-id="48a18-120">在下列範例中，我們會使用`Default Web Site`，建立名為應用程式集區`RESTAppPool`，執行為 appPool`bootcampbts2016\btsservice`帳戶，請使用`BIZTALK-serviceacct`做為使用者帳戶密碼，並提供 BizTalk Server 系統管理員群組權限。</span><span class="sxs-lookup"><span data-stu-id="48a18-120">In the following example, we use the `Default Web Site`, create an application pool named `RESTAppPool`, run the appPool as the `bootcampbts2016\btsservice` account, use `BIZTALK-serviceacct` as the user account password, and give the BizTalk Server Administrators group permissions.</span></span> <span data-ttu-id="48a18-121">請務必輸入下列項目，包括單一引號周圍有空格的值：</span><span class="sxs-lookup"><span data-stu-id="48a18-121">Be sure to enter the following, including the single quotes surrounding values with spaces:</span></span> 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName 'Default Web Site' -ApplicationPool RESTAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
    ```

    <span data-ttu-id="48a18-122">完成時， **BizTalkManagementService**在 IIS 中建立應用程式：</span><span class="sxs-lookup"><span data-stu-id="48a18-122">When complete, the **BizTalkManagementService** application is created within IIS:</span></span>  
    <span data-ttu-id="48a18-123">![BizTalkManagementService 應用程式](../core/media/biztalkmanagementservice-apppool.png)</span><span class="sxs-lookup"><span data-stu-id="48a18-123">![BizTalkManagementService application](../core/media/biztalkmanagementservice-apppool.png)</span></span>

4. <span data-ttu-id="48a18-124">若要確認它是否能運作，瀏覽至`http://localhost/BizTalkManagementService/swagger`。</span><span class="sxs-lookup"><span data-stu-id="48a18-124">To confirm it’s working, browse to `http://localhost/BizTalkManagementService/swagger`.</span></span> <span data-ttu-id="48a18-125">如果系統會提示您登入、 使用您在上一個步驟中輸入 「 網域 \ 群組的成員帳戶登入 (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`)。</span><span class="sxs-lookup"><span data-stu-id="48a18-125">If you are prompted to sign-in, sign in with an account that is member of the domain\group you entered in the previous step (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`).</span></span> 

> [!WARNING]
> <span data-ttu-id="48a18-126">在 IIS 中 BizTalkManagementService 應用程式在 web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="48a18-126">The BizTalkManagementService application in IIS uses a web.config file.</span></span> <span data-ttu-id="48a18-127">在 web.config 中的項目**區分大小寫**。</span><span class="sxs-lookup"><span data-stu-id="48a18-127">Elements within web.config **are case sensitive**.</span></span> <span data-ttu-id="48a18-128">因此當您執行 Windows PowerShell 指令碼，請務必輸入正確的大小寫的`-AuthorizationRoles`值。</span><span class="sxs-lookup"><span data-stu-id="48a18-128">So when you execute the Windows PowerShell script, be sure to enter the correct case for `-AuthorizationRoles` value.</span></span> <span data-ttu-id="48a18-129">如果您不確定的情況下，以下是簡單的方法，若要了解：</span><span class="sxs-lookup"><span data-stu-id="48a18-129">If you’re not sure of the case, here’s an easy way to find out:</span></span> 
> 
> 1. <span data-ttu-id="48a18-130">開啟**電腦管理**，展開**本機使用者和群組**。</span><span class="sxs-lookup"><span data-stu-id="48a18-130">Open **Computer Management**, and expand **Local Users and Groups**.</span></span>
> 2. <span data-ttu-id="48a18-131">選取 **群組**，向下捲動至**SQLServer...**</span><span class="sxs-lookup"><span data-stu-id="48a18-131">Select **Groups**, and scroll down to the **SQLServer…**</span></span> <span data-ttu-id="48a18-132">群組。</span><span class="sxs-lookup"><span data-stu-id="48a18-132">groups.</span></span> 
> 3. <span data-ttu-id="48a18-133">在下列範例中，請注意**BOOTCAMPBTS2016**是全部大寫字。</span><span class="sxs-lookup"><span data-stu-id="48a18-133">In the following example, notice **BOOTCAMPBTS2016** is in all caps.</span></span> <span data-ttu-id="48a18-134">如果您看到全部大寫，然後輸入電腦名稱全部大寫。</span><span class="sxs-lookup"><span data-stu-id="48a18-134">If you see all caps, then enter the computer name in all caps.</span></span> 
> 
> ![電腦名稱是全部大寫字](../core/media/groups-case.png)

<span data-ttu-id="48a18-136">現在，透過 IIS 公開 REST Api，它們可以存取及執行其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="48a18-136">Now that the REST APIs are exposed through IIS, they can be accessed and executed by other applications.</span></span> <span data-ttu-id="48a18-137">[功能套件的 REST API 參考](https://docs.microsoft.com/rest/api/biztalk/?view=rest-biztalk-2016)列出的 Api。</span><span class="sxs-lookup"><span data-stu-id="48a18-137">[Feature Pack REST API reference](https://docs.microsoft.com/rest/api/biztalk/?view=rest-biztalk-2016) lists the APIs.</span></span>

<span data-ttu-id="48a18-138">您可以變更誰可以存取透過手動更新**web.config**檔案，這是管理應用程式的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="48a18-138">You can change who has access by manually updating the **web.config** file, which is in the root folder of the management application.</span></span> <span data-ttu-id="48a18-139">例如，使用下列命令來允許任何人存取 swagger 輸出：</span><span class="sxs-lookup"><span data-stu-id="48a18-139">For example, use the following to allow anyone access to the swagger output:</span></span> 

```
<authorization>
   <allow users="*" />
</authorization>
```

## <a name="step-2-test-the-apis"></a><span data-ttu-id="48a18-140">步驟 2：測試 Api</span><span class="sxs-lookup"><span data-stu-id="48a18-140">Step 2: Test the APIs</span></span>

1. <span data-ttu-id="48a18-141">在 BizTalk 伺服器上，瀏覽至`http://localhost/BizTalkManagementService/swagger`。</span><span class="sxs-lookup"><span data-stu-id="48a18-141">On the BizTalk Server, browse to `http://localhost/BizTalkManagementService/swagger`.</span></span>

2. <span data-ttu-id="48a18-142">捲動到 **主機**，然後選取**顯示/隱藏**。</span><span class="sxs-lookup"><span data-stu-id="48a18-142">Scroll to **Hosts**, and select **Show/Hide**.</span></span> <span data-ttu-id="48a18-143">沒有 GET 命令;按一下此資料列：</span><span class="sxs-lookup"><span data-stu-id="48a18-143">There is a GET command; click this row:</span></span>  
<span data-ttu-id="48a18-144">![取得所有主機](../core/media/managment-rest-apis-hosts-get.png)</span><span class="sxs-lookup"><span data-stu-id="48a18-144">![GET all hosts](../core/media/managment-rest-apis-hosts-get.png)</span></span>

3. <span data-ttu-id="48a18-145">它會顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="48a18-145">It shows the details.</span></span> <span data-ttu-id="48a18-146">選取 **試用看看**:</span><span class="sxs-lookup"><span data-stu-id="48a18-146">Select **Try it out**:</span></span>  
<span data-ttu-id="48a18-147">![現在就試試看](../core/media/managment-rest-apis-hosts-tryitout.png)</span><span class="sxs-lookup"><span data-stu-id="48a18-147">![Try it out](../core/media/managment-rest-apis-hosts-tryitout.png)</span></span>

4. <span data-ttu-id="48a18-148">回應主體會傳回所有主機：</span><span class="sxs-lookup"><span data-stu-id="48a18-148">The Response Body returns all the hosts:</span></span>  
![回應](../core/media/managment-rest-apis-hosts-response.png)

> [!NOTE]
> <span data-ttu-id="48a18-150">如果您瀏覽至`http://localhost/BizTalkManagementService`，您應該取得 500 錯誤。</span><span class="sxs-lookup"><span data-stu-id="48a18-150">If you browse to `http://localhost/BizTalkManagementService`, you should get a 500 error.</span></span> <span data-ttu-id="48a18-151">這是一件好事。</span><span class="sxs-lookup"><span data-stu-id="48a18-151">That’s a good thing.</span></span> <span data-ttu-id="48a18-152">只要加入`/swagger`結尾的 URL，而且您會看到可用的 REST Api。</span><span class="sxs-lookup"><span data-stu-id="48a18-152">Just add `/swagger` to the end of URL, and you’ll see the available REST APIs.</span></span> 


## <a name="see-also"></a><span data-ttu-id="48a18-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a18-153">See also</span></span>
 [<span data-ttu-id="48a18-154">設定 Feature Pack</span><span class="sxs-lookup"><span data-stu-id="48a18-154">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)