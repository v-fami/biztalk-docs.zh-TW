---
title: 教學課程 5： 叫用 REST 介面，使用 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73871ca3-abd0-45ae-b379-6df76a967a80
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d45daa5f567863fd3531edb1f951ac673628fd6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967567"
---
# <a name="tutorial-5-invoking-a-rest-interface-using-biztalk-server"></a><span data-ttu-id="02c9f-102">教學課程 5： 叫用 REST 介面，使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="02c9f-102">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>
<span data-ttu-id="02c9f-103">本節提供如何叫用 REST 端點使用的逐步解說[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="02c9f-103">This section provides a step-by-step walkthrough on how to invoke a REST endpoint using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="02c9f-104">在本教學課程中您叫用 REST 端點，可從[!INCLUDE[winazure](../includes/winazure-md.md)]航空電訊廠商會傳回在美國的航班延遲的 Marketplace。</span><span class="sxs-lookup"><span data-stu-id="02c9f-104">In this tutorial you invoke a REST endpoint available from the [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace that returns the delays in flights of US air carriers.</span></span> <span data-ttu-id="02c9f-105">本教學課程會使用新**Wcf-webhttp**配接器中導入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]叫用 REST 端點。</span><span class="sxs-lookup"><span data-stu-id="02c9f-105">The tutorial uses the new **WCF-WebHttp** adapter introduced in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to invoke the REST endpoint.</span></span>  
  
##  <a name="BKMK_Scenario"></a> <span data-ttu-id="02c9f-106">在本教學課程中使用的案例</span><span class="sxs-lookup"><span data-stu-id="02c9f-106">Scenario Used in This Tutorial</span></span>  
 [!INCLUDE[winazure](../includes/winazure-md.md)]<span data-ttu-id="02c9f-107"> Marketplace 會提供下列 REST 資源 URL，以擷取航班延誤的美國空軍電信業者：</span><span class="sxs-lookup"><span data-stu-id="02c9f-107"> Marketplace provides the following the REST resource URL to retrieve flight delays of US air carriers:</span></span>  
  
```  
https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/On_Time_Performance  
```  
  
 <span data-ttu-id="02c9f-108">如果您在網頁瀏覽器的網址列中輸入此 URL，系統會提示您提供認證來存取資源。</span><span class="sxs-lookup"><span data-stu-id="02c9f-108">If you enter this URL in the address bar of a Web browser, you are prompted for credentials to access the resource.</span></span> <span data-ttu-id="02c9f-109">您已登入後[Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913)，您可以取得的認證**我的帳戶**web 頁面的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02c9f-109">After you have logged into the [Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913), you can get the credentials from the **My Account** tab of the web page.</span></span> <span data-ttu-id="02c9f-110">認證會列出針對**Customer ID** （使用者名稱） 及**主要帳戶金鑰**（密碼） 標籤。</span><span class="sxs-lookup"><span data-stu-id="02c9f-110">The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels.</span></span>  
  
 <span data-ttu-id="02c9f-111">在本教學課程中，您使用的資源 URL 和認證來設定雙向**Wcf-webhttp**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="02c9f-111">In this tutorial, you use the resource URL and the credentials to configure a two-way **WCF-WebHttp** send port.</span></span> <span data-ttu-id="02c9f-112">接收管線的雙向傳送埠接收回應訊息含有航班詳細資料，並將發佈的訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]message box 資料庫。</span><span class="sxs-lookup"><span data-stu-id="02c9f-112">The receive pipeline of the two-way send port receives the response message with the flight details and publishes the message to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message box database.</span></span> <span data-ttu-id="02c9f-113">您設定 FILE 傳送埠訂閱 Wcf-webhttp 傳送埠所發行的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="02c9f-113">You configure a FILE send port that subscribes to all the messages published by the WCF-WebHttp send port.</span></span> <span data-ttu-id="02c9f-114">FILE 傳送埠會取用來自訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並將它複製到檔案位置。</span><span class="sxs-lookup"><span data-stu-id="02c9f-114">The FILE send port consumes the message from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and copies it to a file location.</span></span>  
  
 <span data-ttu-id="02c9f-115">在真實世界的商業案例中，將它與較大的商務程序，例如從企業營運應用程式取得訊息的接收位置關聯可以觸發 Wcf-webhttp 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="02c9f-115">In a real-world business scenario, the WCF-WebHttp send port can be triggered by associating it with a larger business process such as a receive location that gets a message from a business application.</span></span> <span data-ttu-id="02c9f-116">不過，在本教學課程中，重點在於示範如何叫用 REST 介面，因為您可以使用簡單的檔案位置，收到空的訊息，以便觸發程序的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="02c9f-116">However, in this tutorial, because the focus is on demonstrating how to invoke a REST interface, you can use a simple FILE location that receives a dummy message to trigger the send port.</span></span>  
  
 <span data-ttu-id="02c9f-117">因此，簡單來說，您必須執行下列步驟來設定此解決方案：</span><span class="sxs-lookup"><span data-stu-id="02c9f-117">So, to summarize, you must perform the following steps to configure this solution:</span></span>  
  
1.  <span data-ttu-id="02c9f-118">設定檔案接收位置挑選虛擬要求訊息。</span><span class="sxs-lookup"><span data-stu-id="02c9f-118">Configure a FILE receive location to pick a dummy request message.</span></span>  
  
2.  <span data-ttu-id="02c9f-119">設定雙向 Wcf-webhttp 傳送埠，以叫用 REST 資源 URL，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="02c9f-119">Configure a two-way WCF-WebHttp send port to invoke the REST resource URL and receive a response.</span></span>  
  
3.  <span data-ttu-id="02c9f-120">設定單向 FILE 傳送埠取用回應訊息的飛行詳細資料，並將它複製到檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="02c9f-120">Configure a one-way FILE send port to consume the response message with the flight details and copy it to a file location.</span></span>  
  
## <a name="set-up-your-includewinazureincludeswinazure-mdmd-marketplace-account"></a><span data-ttu-id="02c9f-121">設定您[!INCLUDE[winazure](../includes/winazure-md.md)]Marketplace 帳戶</span><span class="sxs-lookup"><span data-stu-id="02c9f-121">Set up Your [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace Account</span></span>  
 <span data-ttu-id="02c9f-122">若要存取透過 REST 端點公開的航班延誤資料，您必須先訂閱美國航空電訊廠商航班誤點範例資料摘要。</span><span class="sxs-lookup"><span data-stu-id="02c9f-122">To access the flight delay data exposed through the REST endpoint, you must first subscribe to the US Air Carrier Flight Delays sample data feed.</span></span> <span data-ttu-id="02c9f-123">執行下列步驟來執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="02c9f-123">Perform the following steps to do so:</span></span>  
  
#### <a name="to-subscribe-to-the-data-feed"></a><span data-ttu-id="02c9f-124">若要訂閱摘要的資料</span><span class="sxs-lookup"><span data-stu-id="02c9f-124">To subscribe to the data feed</span></span>  
  
1. <span data-ttu-id="02c9f-125">登入[!INCLUDE[winazure](../includes/winazure-md.md)]Marketplace 使用 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="02c9f-125">Log in to the [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace using your Microsoft account.</span></span>  
  
2. <span data-ttu-id="02c9f-126">在 **資料**索引標籤上，找出並按一下 **美國航空電訊廠商航班誤點**服務。</span><span class="sxs-lookup"><span data-stu-id="02c9f-126">In the **Data** tab, locate and click the **US Air Carrier Flight Delays** service.</span></span>  
  
3. <span data-ttu-id="02c9f-127">在 資料服務 頁面中，按一下 **註冊**。</span><span class="sxs-lookup"><span data-stu-id="02c9f-127">On the data service page, click **Sign Up**.</span></span> <span data-ttu-id="02c9f-128">在 註冊 頁面上，接受合約的條款，然後按一下 **註冊**一次。</span><span class="sxs-lookup"><span data-stu-id="02c9f-128">On the Sign Up page, accept the terms of agreement and then click **Sign up** again.</span></span>  
  
4. <span data-ttu-id="02c9f-129">在 **我的帳戶**索引標籤上，擷取認證，以存取資料服務。</span><span class="sxs-lookup"><span data-stu-id="02c9f-129">In the **My Account** tab, retrieve the credentials to access the data service.</span></span> <span data-ttu-id="02c9f-130">認證會列出針對**Customer ID** （使用者名稱） 及**主要帳戶金鑰**（密碼） 標籤。</span><span class="sxs-lookup"><span data-stu-id="02c9f-130">The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels.</span></span> <span data-ttu-id="02c9f-131">設定時，您將需要這些認證**Wcf-webhttp**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="02c9f-131">You will need these credentials while configuring the **WCF-WebHttp** send port.</span></span>  
  
## <a name="set-up-your-computer"></a><span data-ttu-id="02c9f-132">設定電腦</span><span class="sxs-lookup"><span data-stu-id="02c9f-132">Set up Your Computer</span></span>  
 <span data-ttu-id="02c9f-133">若要設定您必須擁有本教學課程中使用的案例[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您的電腦上安裝和設定。</span><span class="sxs-lookup"><span data-stu-id="02c9f-133">To configure the scenario used in this tutorial you must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installed and configured on your computer.</span></span> <span data-ttu-id="02c9f-134">如果您想要佈建[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上 Windows Azure VM，請遵循指示[設定 Azure VM 上的 BizTalk Server](http://msdn.microsoft.com/library/azure/jj248689.aspx)。</span><span class="sxs-lookup"><span data-stu-id="02c9f-134">If you want to provision a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer on a Windows Azure VM, follow the instructions at [Configuring BizTalk Server on an Azure VM](http://msdn.microsoft.com/library/azure/jj248689.aspx).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="02c9f-135">本節內容</span><span class="sxs-lookup"><span data-stu-id="02c9f-135">In This Section</span></span>  
  
-   [<span data-ttu-id="02c9f-136">步驟 1：設定 FILE 接收位置</span><span class="sxs-lookup"><span data-stu-id="02c9f-136">Step 1: Configure a FILE Receive Location</span></span>](../core/step-1-configure-a-file-receive-location.md)  
  
-   [<span data-ttu-id="02c9f-137">步驟 2：設定雙向 WCF-WebHttp 傳送埠</span><span class="sxs-lookup"><span data-stu-id="02c9f-137">Step 2: Configure a Two-way WCF-WebHttp Send Port</span></span>](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md)  
  
-   [<span data-ttu-id="02c9f-138">步驟 3：設定單向 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="02c9f-138">Step 3: Configure a One-way FILE Send Port</span></span>](../core/step-3-configure-a-one-way-file-send-port.md)  
  
-   [<span data-ttu-id="02c9f-139">步驟 4：測試解決方案</span><span class="sxs-lookup"><span data-stu-id="02c9f-139">Step 4: Test the Solution</span></span>](../core/step-4-test-the-solution.md)