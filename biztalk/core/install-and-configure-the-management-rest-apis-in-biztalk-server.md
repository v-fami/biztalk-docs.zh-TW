---
title: "安裝和設定管理 REST Api |Microsoft 文件"
description: "查詢中使用管理資料 REST Api 與 BizTalk Server 中的功能組件 1 BizTalk 環境的成品的狀態"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 009b3b0bb333b8f92f6235da57b0c3e9f5daca96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a><span data-ttu-id="9b545-103">安裝和設定 BizTalk Server 中的管理 REST Api</span><span class="sxs-lookup"><span data-stu-id="9b545-103">Install and configure the management REST APIs in BizTalk Server</span></span>
<span data-ttu-id="9b545-104">若要啟用遠端管理的 REST Api 中使用 Windows PowerShell 指令程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9b545-104">Use a Windows PowerShell script to enable REST APIs that remotely manage your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

## <a name="what-are-management-data-apis"></a><span data-ttu-id="9b545-105">管理資料應用程式開發介面有哪些？</span><span class="sxs-lookup"><span data-stu-id="9b545-105">What are Management data APIs</span></span>
<span data-ttu-id="9b545-106">管理資料應用程式開發介面是可讓您從遠端更新、 加入及查詢中的不同成品的狀態的端點您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="9b545-106">Management data APIs are the endpoints that let you remotely update, add, and query the status of different artifacts in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="9b545-107">端點會新增使用 REST，並隨附 Swagger 定義。</span><span class="sxs-lookup"><span data-stu-id="9b545-107">The endpoints are added using REST, and come with a Swagger definition.</span></span> 

<span data-ttu-id="9b545-108">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，沒有安裝這些 REST Api，以及其 swagger 定義的 Windows PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="9b545-108">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, there's a Windows PowerShell script that installs these REST APIs, and their swagger definitions.</span></span> <span data-ttu-id="9b545-109">這些 Api 進行遠端管理連接埠、 協調流程、 夥伴、 協議、 管線和更多的 REST 呼叫。</span><span class="sxs-lookup"><span data-stu-id="9b545-109">These APIs make REST calls to remotely manage ports, orchestrations, partners, agreements, pipelines, and more.</span></span> 

<span data-ttu-id="9b545-110">本主題說明如何安裝 REST Api。</span><span class="sxs-lookup"><span data-stu-id="9b545-110">This topic shows you how to install the REST APIs.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b545-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="9b545-111">Prerequisites</span></span>
* <span data-ttu-id="9b545-112">安裝[功能套件 1](https://www.microsoft.com/download/details.aspx?id=55100)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b545-112">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

* <span data-ttu-id="9b545-113">在上安裝 IIS [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9b545-113">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="9b545-114">在大部分[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]環境中，IIS 已安裝。</span><span class="sxs-lookup"><span data-stu-id="9b545-114">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="9b545-115">請參閱[硬體和軟體需求適用於 BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="9b545-115">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span>

## <a name="enable-the-rest-apis"></a><span data-ttu-id="9b545-116">啟用 REST Api</span><span class="sxs-lookup"><span data-stu-id="9b545-116">Enable the REST APIs</span></span>

1. <span data-ttu-id="9b545-117">以系統管理員身分執行 Windows PowerShell (**啟動**功能表中，輸入**PowerShell**，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**)。</span><span class="sxs-lookup"><span data-stu-id="9b545-117">Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**).</span></span> 
2. <span data-ttu-id="9b545-118">瀏覽至 [BizTalk] 資料夾下**Program Files (x86)/Microsoft BizTalk Server 2016**</span><span class="sxs-lookup"><span data-stu-id="9b545-118">Browse to the BizTalk folder under **Program Files (x86)/Microsoft BizTalk Server 2016**</span></span>
3. <span data-ttu-id="9b545-119">執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="9b545-119">Run the following command.</span></span> <span data-ttu-id="9b545-120">請務必更新您`website`， `domain/user`， `password`，和`domain\group`以您的值：</span><span class="sxs-lookup"><span data-stu-id="9b545-120">Be sure to update your `website`, `domain/user`, `password`, and `domain\group` with your values:</span></span> 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```
4. <span data-ttu-id="9b545-121">執行指令碼之後，瀏覽新的 IIS 應用程式：</span><span class="sxs-lookup"><span data-stu-id="9b545-121">After you run the script, browse the new IIS application:</span></span>  
    1. <span data-ttu-id="9b545-122">開啟網頁瀏覽器</span><span class="sxs-lookup"><span data-stu-id="9b545-122">Open your web browser</span></span>
    2. <span data-ttu-id="9b545-123">瀏覽至**http://localhost/OperationalDataService/swagger**</span><span class="sxs-lookup"><span data-stu-id="9b545-123">Browse to **http://localhost/OperationalDataService/swagger**</span></span>

5. <span data-ttu-id="9b545-124">Swagger 定義負載。</span><span class="sxs-lookup"><span data-stu-id="9b545-124">The Swagger definitions loads.</span></span> <span data-ttu-id="9b545-125">您也可以變更誰可以存取藉由更新**web.config**管理應用程式的根資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="9b545-125">You can also change who has access by updating the **web.config** file in the root folder of the Management Application.</span></span>

<span data-ttu-id="9b545-126">REST Api 公開會透過此機器，以及可以存取和其他應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="9b545-126">The REST APIs are exposed through the machine, and can be accessed and executed by other applications.</span></span> 


## <a name="see-also"></a><span data-ttu-id="9b545-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b545-127">See also</span></span>
 [<span data-ttu-id="9b545-128">設定此功能套件</span><span class="sxs-lookup"><span data-stu-id="9b545-128">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)