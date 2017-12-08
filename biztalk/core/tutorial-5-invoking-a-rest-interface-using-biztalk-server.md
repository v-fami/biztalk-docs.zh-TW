---
title: "教學課程 5： 叫用 REST 介面使用 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73871ca3-abd0-45ae-b379-6df76a967a80
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce915ec277b1f73f93a9508a5dd6c92fb0a5c9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-5-invoking-a-rest-interface-using-biztalk-server"></a><span data-ttu-id="c4b12-102">教學課程 5： 叫用 REST 介面使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c4b12-102">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>
<span data-ttu-id="c4b12-103">此章節提供如何叫用 REST 端點使用的逐步解說[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c4b12-103">This section provides a step-by-step walkthrough on how to invoke a REST endpoint using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c4b12-104">在本教學課程叫用 REST 端點可從[!INCLUDE[winazure](../includes/winazure-md.md)]Marketplace 傳回延遲班機美式空中承運業者寄送。</span><span class="sxs-lookup"><span data-stu-id="c4b12-104">In this tutorial you invoke a REST endpoint available from the [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace that returns the delays in flights of US air carriers.</span></span> <span data-ttu-id="c4b12-105">本教學課程會使用新**Wcf-webhttp**配接器中導入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]叫用 REST 端點。</span><span class="sxs-lookup"><span data-stu-id="c4b12-105">The tutorial uses the new **WCF-WebHttp** adapter introduced in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to invoke the REST endpoint.</span></span>  
  
##  <a name="BKMK_Scenario"></a><span data-ttu-id="c4b12-106">在本教學課程案例</span><span class="sxs-lookup"><span data-stu-id="c4b12-106">Scenario Used in This Tutorial</span></span>  
 [!INCLUDE[winazure](../includes/winazure-md.md)]<span data-ttu-id="c4b12-107">Marketplace 提供下列 REST 資源 URL，以擷取航班延誤的美國空中電信業者：</span><span class="sxs-lookup"><span data-stu-id="c4b12-107"> Marketplace provides the following the REST resource URL to retrieve flight delays of US air carriers:</span></span>  
  
```  
https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/On_Time_Performance  
```  
  
 <span data-ttu-id="c4b12-108">如果您在網頁瀏覽器的網址列輸入此 URL，系統會提示您認證以存取資源。</span><span class="sxs-lookup"><span data-stu-id="c4b12-108">If you enter this URL in the address bar of a Web browser, you are prompted for credentials to access the resource.</span></span> <span data-ttu-id="c4b12-109">您登入之後[Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913)，您可以取得的認證從**我的帳戶**web 頁面的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c4b12-109">After you have logged into the [Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913), you can get the credentials from the **My Account** tab of the web page.</span></span> <span data-ttu-id="c4b12-110">認證會列出針對**客戶 ID** （使用者名稱） 和**主要帳戶金鑰**（密碼） 標籤。</span><span class="sxs-lookup"><span data-stu-id="c4b12-110">The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels.</span></span>  
  
 <span data-ttu-id="c4b12-111">在本教學課程中，您使用的資源 URL 和認證來設定雙向**Wcf-webhttp**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c4b12-111">In this tutorial, you use the resource URL and the credentials to configure a two-way **WCF-WebHttp** send port.</span></span> <span data-ttu-id="c4b12-112">接收管線的雙向傳送埠接收回應訊息與飛行詳細資料，並將發佈的訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]messagebox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c4b12-112">The receive pipeline of the two-way send port receives the response message with the flight details and publishes the message to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message box database.</span></span> <span data-ttu-id="c4b12-113">您設定訂閱 Wcf-webhttp 傳送埠所發行的所有訊息的 FILE 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c4b12-113">You configure a FILE send port that subscribes to all the messages published by the WCF-WebHttp send port.</span></span> <span data-ttu-id="c4b12-114">FILE 傳送埠取用訊息從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並將它複製到檔案位置。</span><span class="sxs-lookup"><span data-stu-id="c4b12-114">The FILE send port consumes the message from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and copies it to a file location.</span></span>  
  
 <span data-ttu-id="c4b12-115">在真實世界的商業案例中，將它與較大的商務程序，例如商務應用程式從取得訊息的接收位置關聯可以觸發 Wcf-webhttp 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c4b12-115">In a real-world business scenario, the WCF-WebHttp send port can be triggered by associating it with a larger business process such as a receive location that gets a message from a business application.</span></span> <span data-ttu-id="c4b12-116">不過，在本教學課程中，因為的重點在於示範如何叫用 REST 介面，您可以使用簡單的檔案位置接收到觸發程序的傳送埠將虛擬訊息。</span><span class="sxs-lookup"><span data-stu-id="c4b12-116">However, in this tutorial, because the focus is on demonstrating how to invoke a REST interface, you can use a simple FILE location that receives a dummy message to trigger the send port.</span></span>  
  
 <span data-ttu-id="c4b12-117">因此，簡單來說，您必須執行下列步驟來設定此解決方案：</span><span class="sxs-lookup"><span data-stu-id="c4b12-117">So, to summarize, you must perform the following steps to configure this solution:</span></span>  
  
1.  <span data-ttu-id="c4b12-118">設定檔案接收位置挑選虛擬要求訊息。</span><span class="sxs-lookup"><span data-stu-id="c4b12-118">Configure a FILE receive location to pick a dummy request message.</span></span>  
  
2.  <span data-ttu-id="c4b12-119">設定雙向 Wcf-webhttp 傳送埠以叫用 REST 資源 URL，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="c4b12-119">Configure a two-way WCF-WebHttp send port to invoke the REST resource URL and receive a response.</span></span>  
  
3.  <span data-ttu-id="c4b12-120">設定單向 FILE 傳送埠取用回應訊息的飛行詳細資料，並將它複製到檔案位置。</span><span class="sxs-lookup"><span data-stu-id="c4b12-120">Configure a one-way FILE send port to consume the response message with the flight details and copy it to a file location.</span></span>  
  
## <a name="set-up-your-includewinazureincludeswinazure-mdmd-marketplace-account"></a><span data-ttu-id="c4b12-121">設定您[!INCLUDE[winazure](../includes/winazure-md.md)]的 Marketplace 帳戶</span><span class="sxs-lookup"><span data-stu-id="c4b12-121">Set up Your [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace Account</span></span>  
 <span data-ttu-id="c4b12-122">若要存取 公開透過 REST 端點的飛行延遲資料，您必須先訂閱美國空中載波航班延誤範例資料摘要。</span><span class="sxs-lookup"><span data-stu-id="c4b12-122">To access the flight delay data exposed through the REST endpoint, you must first subscribe to the US Air Carrier Flight Delays sample data feed.</span></span> <span data-ttu-id="c4b12-123">執行下列步驟來執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="c4b12-123">Perform the following steps to do so:</span></span>  
  
#### <a name="to-subscribe-to-the-data-feed"></a><span data-ttu-id="c4b12-124">若要訂閱的資料摘要</span><span class="sxs-lookup"><span data-stu-id="c4b12-124">To subscribe to the data feed</span></span>  
  
1.  <span data-ttu-id="c4b12-125">登入[!INCLUDE[winazure](../includes/winazure-md.md)]Marketplace 使用您的 Microsoft 帳戶。</span><span class="sxs-lookup"><span data-stu-id="c4b12-125">Log in to the [!INCLUDE[winazure](../includes/winazure-md.md)] Marketplace using your Microsoft account.</span></span>  
  
2.  <span data-ttu-id="c4b12-126">在**資料**索引標籤上，找出並按一下**美國空中載波航班延誤**服務。</span><span class="sxs-lookup"><span data-stu-id="c4b12-126">In the **Data** tab, locate and click the **US Air Carrier Flight Delays** service.</span></span>  
  
3.  <span data-ttu-id="c4b12-127">在 [資料服務] 頁面上按一下**註冊**。</span><span class="sxs-lookup"><span data-stu-id="c4b12-127">On the data service page, click **Sign Up**.</span></span> <span data-ttu-id="c4b12-128">在登入頁面上，接受合約的條款，然後按一下 **註冊**一次。</span><span class="sxs-lookup"><span data-stu-id="c4b12-128">On the Sign Up page, accept the terms of agreement and then click **Sign up** again.</span></span>  
  
4.  <span data-ttu-id="c4b12-129">在**我的帳戶**索引標籤上，擷取來存取資料服務的認證。</span><span class="sxs-lookup"><span data-stu-id="c4b12-129">In the **My Account** tab, retrieve the credentials to access the data service.</span></span> <span data-ttu-id="c4b12-130">認證會列出針對**客戶 ID** （使用者名稱） 和**主要帳戶金鑰**（密碼） 標籤。</span><span class="sxs-lookup"><span data-stu-id="c4b12-130">The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels.</span></span> <span data-ttu-id="c4b12-131">設定時，您會需要這些認證**Wcf-webhttp**傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c4b12-131">You will need these credentials while configuring the **WCF-WebHttp** send port.</span></span>  
  
## <a name="set-up-your-computer"></a><span data-ttu-id="c4b12-132">設定電腦</span><span class="sxs-lookup"><span data-stu-id="c4b12-132">Set up Your Computer</span></span>  
 <span data-ttu-id="c4b12-133">若要設定在本教學課程，您必須使用的案例[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您的電腦上安裝和設定。</span><span class="sxs-lookup"><span data-stu-id="c4b12-133">To configure the scenario used in this tutorial you must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installed and configured on your computer.</span></span> <span data-ttu-id="c4b12-134">如果您想要佈建[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上 Windows Azure VM，請遵循指示[Azure VM 上設定 BizTalk Server](http://msdn.microsoft.com/library/azure/jj248689.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c4b12-134">If you want to provision a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer on a Windows Azure VM, follow the instructions at [Configuring BizTalk Server on an Azure VM](http://msdn.microsoft.com/library/azure/jj248689.aspx).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4b12-135">本節內容</span><span class="sxs-lookup"><span data-stu-id="c4b12-135">In This Section</span></span>  
  
-   [<span data-ttu-id="c4b12-136">步驟 1： 設定檔案接收位置</span><span class="sxs-lookup"><span data-stu-id="c4b12-136">Step 1: Configure a FILE Receive Location</span></span>](../core/step-1-configure-a-file-receive-location.md)  
  
-   [<span data-ttu-id="c4b12-137">步驟 2： 設定雙向 Wcf-webhttp 傳送埠</span><span class="sxs-lookup"><span data-stu-id="c4b12-137">Step 2: Configure a Two-way WCF-WebHttp Send Port</span></span>](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md)  
  
-   [<span data-ttu-id="c4b12-138">步驟 3： 設定單向 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="c4b12-138">Step 3: Configure a One-way FILE Send Port</span></span>](../core/step-3-configure-a-one-way-file-send-port.md)  
  
-   [<span data-ttu-id="c4b12-139">步驟 4： 測試方案</span><span class="sxs-lookup"><span data-stu-id="c4b12-139">Step 4: Test the Solution</span></span>](../core/step-4-test-the-solution.md)