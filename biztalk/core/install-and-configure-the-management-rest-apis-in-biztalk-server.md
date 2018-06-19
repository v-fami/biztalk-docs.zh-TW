---
title: 安裝和設定管理 REST Api |Microsoft 文件
description: 查詢您使用管理資料 REST Api 與 BizTalk Server 中的功能組件的 BizTalk 環境中的成品
ms.custom: fp1
ms.date: 11/06/2017
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
ms.openlocfilehash: c207b0aca5f2673e615167f75f7f1c7c3fb0e042
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
ms.locfileid: "25497895"
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a><span data-ttu-id="ce3c8-103">安裝和設定 BizTalk Server 中的管理 REST Api</span><span class="sxs-lookup"><span data-stu-id="ce3c8-103">Install and configure the management REST APIs in BizTalk Server</span></span>

## <a name="what-are-management-data-apis"></a><span data-ttu-id="ce3c8-104">管理資料應用程式開發介面有哪些？</span><span class="sxs-lookup"><span data-stu-id="ce3c8-104">What are management data APIs</span></span>
<span data-ttu-id="ce3c8-105">管理資料應用程式開發介面是端點可讓您從遠端更新、 加入及查詢中的不同成品的狀態，您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-105">Management data APIs are endpoints that let you remotely update, add, and query the status of different artifacts in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="ce3c8-106">端點會新增使用 REST，並隨附 swagger 定義。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-106">The endpoints are added using REST, and come with a swagger definition.</span></span> 

<span data-ttu-id="ce3c8-107">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，沒有安裝這些 REST Api，以及其 swagger 定義的 Windows PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-107">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, there's a Windows PowerShell script that installs these REST APIs, and their swagger definitions.</span></span> <span data-ttu-id="ce3c8-108">這些 Api 進行遠端管理連接埠、 協調流程、 夥伴、 協議、 管線和更多的 REST 呼叫。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-108">These APIs make REST calls to remotely manage ports, orchestrations, partners, agreements, pipelines, and more.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="ce3c8-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="ce3c8-109">Prerequisites</span></span>
* <span data-ttu-id="ce3c8-110">安裝[功能套件 2](https://aka.ms/bts2016fp2)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce3c8-110">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

* <span data-ttu-id="ce3c8-111">在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-111">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="ce3c8-112">在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-112">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="ce3c8-113">請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-113">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span> <span data-ttu-id="ce3c8-114">確認 IIS 已安裝 BizTalk Server 上開啟**Internet Information Services 管理員**。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-114">Confirm IIS is installed on the BizTalk Server by opening **Internet Information Services Manager**.</span></span> 

## <a name="step-1-install-the-rest-apis"></a><span data-ttu-id="ce3c8-115">步驟 1： 安裝 REST Api</span><span class="sxs-lookup"><span data-stu-id="ce3c8-115">Step 1: Install the REST APIs</span></span>

1. <span data-ttu-id="ce3c8-116">以系統管理員身分執行 Windows PowerShell (**啟動**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-116">Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**).</span></span> 
2. <span data-ttu-id="ce3c8-117">移至 BizTalk 安裝資料夾 (例如，輸入： `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`)。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-117">Go to the BizTalk installation folder (for example, type: `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`).</span></span>
3. <span data-ttu-id="ce3c8-118">在下列文字，取代`Default Web Site`， `mgmtServiceAppPool`， `domain/user`， `password`，和`domain\group`以您的值：</span><span class="sxs-lookup"><span data-stu-id="ce3c8-118">In the following text, replace `Default Web Site`, `mgmtServiceAppPool`, `domain/user`, `password`, and `domain\group` with your values:</span></span>

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```

    <span data-ttu-id="ce3c8-119">在下列範例中，我們使用`Default Web Site`，建立名為應用程式集區`RESTAppPool`，執行做為 appPool`bootcampbts2016\btsservice`帳戶，請使用`BIZTALK-serviceacct`做為使用者帳戶密碼，並提供 BizTalk Server 系統管理員群組的權限。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-119">In the following example, we use the `Default Web Site`, create an application pool named `RESTAppPool`, run the appPool as the `bootcampbts2016\btsservice` account, use `BIZTALK-serviceacct` as the user account password, and give the BizTalk Server Administrators group permissions.</span></span> <span data-ttu-id="ce3c8-120">請務必輸入下列項目，包括單一引號周圍有空格的值：</span><span class="sxs-lookup"><span data-stu-id="ce3c8-120">Be sure to enter the following, including the single quotes surrounding values with spaces:</span></span> 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName 'Default Web Site' -ApplicationPool RESTAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
    ```

    <span data-ttu-id="ce3c8-121">完成時， **BizTalkManagementService**在 IIS 中建立應用程式：</span><span class="sxs-lookup"><span data-stu-id="ce3c8-121">When complete, the **BizTalkManagementService** application is created within IIS:</span></span>  
    <span data-ttu-id="ce3c8-122">![BizTalkManagementService 應用程式](../core/media/biztalkmanagementservice-apppool.png)</span><span class="sxs-lookup"><span data-stu-id="ce3c8-122">![BizTalkManagementService application](../core/media/biztalkmanagementservice-apppool.png)</span></span>

4. <span data-ttu-id="ce3c8-123">若要確認它是否運作，瀏覽至`http://localhost/BizTalkManagementService/swagger`。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-123">To confirm it’s working, browse to `http://localhost/BizTalkManagementService/swagger`.</span></span> <span data-ttu-id="ce3c8-124">如果系統會提示您登入，是您在上一個步驟中輸入 「 網域 \ 群組成員的帳戶登入 (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`)。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-124">If you are prompted to sign-in, sign in with an account that is member of the domain\group you entered in the previous step (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`).</span></span> 

> [!WARNING]
> <span data-ttu-id="ce3c8-125">在 IIS 中的 BizTalkManagementService 應用程式會使用 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-125">The BizTalkManagementService application in IIS uses a web.config file.</span></span> <span data-ttu-id="ce3c8-126">在 web.config 中的項目**會區分大小寫**。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-126">Elements within web.config **are case sensitive**.</span></span> <span data-ttu-id="ce3c8-127">因此當您執行 Windows PowerShell 指令碼時，必須輸入正確的大小寫的`-AuthorizationRoles`值。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-127">So when you execute the Windows PowerShell script, be sure to enter the correct case for `-AuthorizationRoles` value.</span></span> <span data-ttu-id="ce3c8-128">如果您不確定的情況下，以下是可以輕鬆地找出：</span><span class="sxs-lookup"><span data-stu-id="ce3c8-128">If you’re not sure of the case, here’s an easy way to find out:</span></span> 
> 
> 1. <span data-ttu-id="ce3c8-129">開啟**電腦管理**，然後展開**本機使用者和群組**。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-129">Open **Computer Management**, and expand **Local Users and Groups**.</span></span>
> 2. <span data-ttu-id="ce3c8-130">選取**群組**，向下捲動至**SQLServer...**</span><span class="sxs-lookup"><span data-stu-id="ce3c8-130">Select **Groups**, and scroll down to the **SQLServer…**</span></span> <span data-ttu-id="ce3c8-131">群組。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-131">groups.</span></span> 
> 3. <span data-ttu-id="ce3c8-132">在下列範例中，請注意**BOOTCAMPBTS2016**中全部大寫。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-132">In the following example, notice **BOOTCAMPBTS2016** is in all caps.</span></span> <span data-ttu-id="ce3c8-133">如果您看到全部大寫，然後在 全部大寫中輸入電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-133">If you see all caps, then enter the computer name in all caps.</span></span> 
> 
> ![電腦名稱是以全部大寫](../core/media/groups-case.png)

<span data-ttu-id="ce3c8-135">現在，透過 IIS 公開 REST Api，它們可以存取及執行其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-135">Now that the REST APIs are exposed through IIS, they can be accessed and executed by other applications.</span></span> 

<span data-ttu-id="ce3c8-136">您可以變更誰可以存取透過手動更新**web.config**檔案也會管理應用程式的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-136">You can change who has access by manually updating the **web.config** file, which is in the root folder of the management application.</span></span> <span data-ttu-id="ce3c8-137">例如，使用下列命令以允許任何人存取 swagger 輸出：</span><span class="sxs-lookup"><span data-stu-id="ce3c8-137">For example, use the following to allow anyone access to the swagger output:</span></span> 

```
<authorization>
   <allow users="*" />
</authorization>
```

## <a name="step-2-test-the-apis"></a><span data-ttu-id="ce3c8-138">步驟 2： 測試應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="ce3c8-138">Step 2: Test the APIs</span></span>

1. <span data-ttu-id="ce3c8-139">在 BizTalk 伺服器上，瀏覽至`http://localhost/BizTalkManagementService/swagger`。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-139">On the BizTalk Server, browse to `http://localhost/BizTalkManagementService/swagger`.</span></span>

2. <span data-ttu-id="ce3c8-140">捲動到**主機**，然後選取**顯示/隱藏**。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-140">Scroll to **Hosts**, and select **Show/Hide**.</span></span> <span data-ttu-id="ce3c8-141">沒有 GET 命令，按一下此資料列：</span><span class="sxs-lookup"><span data-stu-id="ce3c8-141">There is a GET command; click this row:</span></span>  
<span data-ttu-id="ce3c8-142">![取得所有主機](../core/media/managment-rest-apis-hosts-get.png)</span><span class="sxs-lookup"><span data-stu-id="ce3c8-142">![GET all hosts](../core/media/managment-rest-apis-hosts-get.png)</span></span>

3. <span data-ttu-id="ce3c8-143">它會顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-143">It shows the details.</span></span> <span data-ttu-id="ce3c8-144">選取**現在就試試看**:</span><span class="sxs-lookup"><span data-stu-id="ce3c8-144">Select **Try it out**:</span></span>  
<span data-ttu-id="ce3c8-145">![現在就試試看](../core/media/managment-rest-apis-hosts-tryitout.png)</span><span class="sxs-lookup"><span data-stu-id="ce3c8-145">![Try it out](../core/media/managment-rest-apis-hosts-tryitout.png)</span></span>

4. <span data-ttu-id="ce3c8-146">回應主體會傳回所有主機：</span><span class="sxs-lookup"><span data-stu-id="ce3c8-146">The Response Body returns all the hosts:</span></span>  
![回應](../core/media/managment-rest-apis-hosts-response.png)

> [!NOTE]
> <span data-ttu-id="ce3c8-148">如果您瀏覽至`http://localhost/BizTalkManagementService`，您應該取得 500 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-148">If you browse to `http://localhost/BizTalkManagementService`, you should get a 500 error.</span></span> <span data-ttu-id="ce3c8-149">這是個好方法。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-149">That’s a good thing.</span></span> <span data-ttu-id="ce3c8-150">只要加入`/swagger`結尾 URL，而且您會看到可用的 REST Api。</span><span class="sxs-lookup"><span data-stu-id="ce3c8-150">Just add `/swagger` to the end of URL, and you’ll see the available REST APIs.</span></span> 


## <a name="see-also"></a><span data-ttu-id="ce3c8-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce3c8-151">See also</span></span>
 [<span data-ttu-id="ce3c8-152">設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="ce3c8-152">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)