---
title: "教學課程： 將與 Salesforce 整合 BizTalk Server 2013 |Microsoft 文件"
description: "使用 Service Bus 與 BIzTalk Server 與 Salesforce 整合"
ms.custom: 
ms.date: 12/07/2015
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06c9ae51-3f48-4086-883b-ab4d5b6e62e3
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8af013bc97ae9618dc19cab57d52fcb4829f0842
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-integrating-biztalk-server-2013-with-salesforce"></a><span data-ttu-id="55f55-103">教學課程： 將與 Salesforce 整合 BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="55f55-103">Tutorial: Integrating BizTalk Server 2013 with Salesforce</span></span>
<span data-ttu-id="55f55-104">審稿者： [Nick Hauenstein](http://social.msdn.microsoft.com/profile/nick.hauenstein/)， [Steef-jan Wiggers](http://social.msdn.microsoft.com/profile/steef-jan%20wiggers)</span><span class="sxs-lookup"><span data-stu-id="55f55-104">Reviewers: [Nick Hauenstein](http://social.msdn.microsoft.com/profile/nick.hauenstein/), [Steef-Jan Wiggers](http://social.msdn.microsoft.com/profile/steef-jan%20wiggers)</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="55f55-105">導入了一些新的配接器可進行混合式案例，牽涉到在內部部署和 Azure 技術。</span><span class="sxs-lookup"><span data-stu-id="55f55-105"> introduces some new adapters that make a lot of hybrid scenarios, involving on-premises and Azure technologies now possible.</span></span> <span data-ttu-id="55f55-106">在此教學課程中，我們會了解如何使用新的配接器和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來整合單純的雲端實體，像是 Salesforce 與內部部署 [!INCLUDE[winazure](../includes/winazure-md.md)] 進行整合。</span><span class="sxs-lookup"><span data-stu-id="55f55-106">In this tutorial, we see how to integrate a purely cloud entity like Salesforce integrate with an on-premises [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using some of the new adapters and [!INCLUDE[winazure](../includes/winazure-md.md)].</span></span> <span data-ttu-id="55f55-107">開始之前，讓我們先了解透過與 Salesforce 整合的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所達成的商務目標。</span><span class="sxs-lookup"><span data-stu-id="55f55-107">Before we start, let’s understand the business objective we try to achieve by integrating [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with Salesforce.</span></span>  
  
 <span data-ttu-id="55f55-108">我們也能建立包括 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 Salesforce 以及舊版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的混合式方案；然而，該方案包括了透過使用 Web 服務 (SOAP) 和 Salesforce 整合，因此更加複雜。</span><span class="sxs-lookup"><span data-stu-id="55f55-108">We could also create hybrid solutions involving [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and Salesforce with previous version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], however the solution would be much more complex involving interaction with Salesforce by consuming a Web service (SOAP).</span></span> <span data-ttu-id="55f55-109">透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和新的配接器，會讓方案簡單許多。</span><span class="sxs-lookup"><span data-stu-id="55f55-109">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the new adapters, the solution is that much easier.</span></span>  
  
## <a name="business-scenario"></a><span data-ttu-id="55f55-110">商務案例</span><span class="sxs-lookup"><span data-stu-id="55f55-110">Business Scenario</span></span>  
 <span data-ttu-id="55f55-111">Northwind 使用 Salesforce 線上 CRM 系統做為方案，以透過準銷售案源追蹤客戶。</span><span class="sxs-lookup"><span data-stu-id="55f55-111">Northwind uses the Salesforce online CRM system as their solution for tracking customers through the sales pipeline.</span></span> <span data-ttu-id="55f55-112">每當在 Salesforce 系統中建立了商機時，Northwind 會希望能夠通知自己的內部部署系統，例如 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便讓其他下遊的系統能抓取相關資料並開始進行其他相關的處理程序。</span><span class="sxs-lookup"><span data-stu-id="55f55-112">Every time a sales opportunity is created in the Salesforce system, Northwind wants its on-premise systems, such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], to be notified so that other down-stream systems can pick up that data and start other relevant processes.</span></span> <span data-ttu-id="55f55-113">Northwind 計劃使用可透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 取用的新配接器實作此方案，並包含部份 [!INCLUDE[winazure](../includes/winazure-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="55f55-113">Northwind plans to implement this solution using the new adapters available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and also by including some components of [!INCLUDE[winazure](../includes/winazure-md.md)].</span></span> <span data-ttu-id="55f55-114">方案中的端對端資料流看起來如下：</span><span class="sxs-lookup"><span data-stu-id="55f55-114">This is how the end-to-end data flow looks like for the solution:</span></span>  
  
-   <span data-ttu-id="55f55-115">業務代表會在 Salesforce 系統中建立一個「商機」。</span><span class="sxs-lookup"><span data-stu-id="55f55-115">A sales representative creates an “opportunity” in the Salesforce system.</span></span>  
  
-   <span data-ttu-id="55f55-116">當商機狀態設為 "Closed Won" 時，會傳送通知到 [!INCLUDE[winazure](../includes/winazure-md.md)] 上裝載的轉送端點。</span><span class="sxs-lookup"><span data-stu-id="55f55-116">When the status of the opportunity is set to “Closed Won”, a notification is sent to a relay endpoint hosted on [!INCLUDE[winazure](../includes/winazure-md.md)].</span></span>  
  
-   <span data-ttu-id="55f55-117">使用新的 WCF-BasicHttpRelay 配接器，會將通知資訊傳至含有內部部署的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統。</span><span class="sxs-lookup"><span data-stu-id="55f55-117">Using the new WCF-BasicHttpRelay adapter, the notification information is passed on to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system housed on-premise.</span></span>  
  
-   <span data-ttu-id="55f55-118">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用接收到的資訊做為通知的一部份、叫用 Salesforce 中的 REST 端點、使用新的 WCF-WebHttp 配接器並取得商機的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="55f55-118">Using the information received as part of the notification, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] invokes a REST endpoint in Salesforce, using the new WCF-WebHttp adapter, to get more information about the opportunity.</span></span>  
  
-   <span data-ttu-id="55f55-119">最後，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用從 Salesforce 收到的資訊，在內部 SQL Server 資料庫表格中建立一個訂單項目。</span><span class="sxs-lookup"><span data-stu-id="55f55-119">Finally, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the information received from Salesforce to create a purchase order entry in an in-house SQL Server database table.</span></span>  
  
 <span data-ttu-id="55f55-120">以上是您必須執行的步驟集，才能達成本方案中說明的整合目標。</span><span class="sxs-lookup"><span data-stu-id="55f55-120">These are the set of steps that you must perform to achieve the integration objective outlined in this solution.</span></span> <span data-ttu-id="55f55-121">每個步驟都包含廣泛的活動集，當我們在建立方案時會看見。</span><span class="sxs-lookup"><span data-stu-id="55f55-121">Each of these steps involves broad set of activities that we’ll look at as we proceed with creating the solution.</span></span>  
  
 <span data-ttu-id="55f55-122">這裡是描述端對端整合方案的說明：</span><span class="sxs-lookup"><span data-stu-id="55f55-122">Here’s an illustration that describes the end-to-end integration solution:</span></span>  
  
 <span data-ttu-id="55f55-123">![BizTalk Server 和 Sharepoint 整合案例](../core/media/bts-sf-scenario.gif "BTS_SF_Scenario")</span><span class="sxs-lookup"><span data-stu-id="55f55-123">![BizTalk Server and Salesforce integration scenario](../core/media/bts-sf-scenario.gif "BTS_SF_Scenario")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="55f55-124">必要條件</span><span class="sxs-lookup"><span data-stu-id="55f55-124">Prerequisites</span></span>  
 <span data-ttu-id="55f55-125">您必須先設定此解決方案的電腦上安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="55f55-125">You must have the following software installed on the computer where you set up this solution:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]  
  
-   [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]  
  
-   [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]  
  
 <span data-ttu-id="55f55-126">您必須擁有下列服務訂用帳戶：</span><span class="sxs-lookup"><span data-stu-id="55f55-126">You must have the following service subscriptions:</span></span>  
  
-   <span data-ttu-id="55f55-127">[!INCLUDE[winazure](../includes/winazure-md.md)] 訂閱</span><span class="sxs-lookup"><span data-stu-id="55f55-127">A [!INCLUDE[winazure](../includes/winazure-md.md)] subscription</span></span>  
  
-   <span data-ttu-id="55f55-128">Salesforce Developer Edition 帳戶</span><span class="sxs-lookup"><span data-stu-id="55f55-128">Salesforce Developer Edition account</span></span>  
  
## <a name="more-resources"></a><span data-ttu-id="55f55-129">其他資源</span><span class="sxs-lookup"><span data-stu-id="55f55-129">More Resources</span></span>  
 <span data-ttu-id="55f55-130">除了本教學課程中，您也可以查看下列資源，了解有關整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與使用新的配接器中導入的 Salesforce [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="55f55-130">In addition to this tutorial, you can also look at the following resources to understand more about integrating [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with Salesforce using the new adapters introduced in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="55f55-131">虛擬實驗室示範[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 Salesforce 整合將會位於[http://go.microsoft.com/fwlink/?LinkId=290930](http://go.microsoft.com/fwlink/?LinkId=290930)。</span><span class="sxs-lookup"><span data-stu-id="55f55-131">A virtual lab demonstrating [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and Salesforce integration is available at [http://go.microsoft.com/fwlink/?LinkId=290930](http://go.microsoft.com/fwlink/?LinkId=290930).</span></span>  
  
-   <span data-ttu-id="55f55-132">根據此教學課程的範例會下載[http://go.microsoft.com/fwlink/?LinkId=290932](http://go.microsoft.com/fwlink/?LinkId=290932)。</span><span class="sxs-lookup"><span data-stu-id="55f55-132">A sample based on this tutorial is available for download at [http://go.microsoft.com/fwlink/?LinkId=290932](http://go.microsoft.com/fwlink/?LinkId=290932).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="55f55-133">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="55f55-133">Next steps</span></span>
  
-   [<span data-ttu-id="55f55-134">步驟 1： 建立服務匯流排命名空間</span><span class="sxs-lookup"><span data-stu-id="55f55-134">Step 1: Create a Service Bus Namespace</span></span>](../core/step-1-create-a-service-bus-namespace.md)  
  
-   [<span data-ttu-id="55f55-135">步驟 2： 設定 Salesforce 系統</span><span class="sxs-lookup"><span data-stu-id="55f55-135">Step 2: Set up the Salesforce System</span></span>](../core/step-2-set-up-the-salesforce-system.md)  
  
-   [<span data-ttu-id="55f55-136">步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="55f55-136">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)  
  
-   [<span data-ttu-id="55f55-137">步驟 4： 設定 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="55f55-137">Step 4: Configure the BizTalk Server Solution</span></span>](../core/step-4-configure-the-biztalk-server-solution.md)  
  
-   [<span data-ttu-id="55f55-138">步驟 5： 測試方案</span><span class="sxs-lookup"><span data-stu-id="55f55-138">Step 5: Test the Solution</span></span>](../core/step-5-test-the-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="55f55-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55f55-139">See Also</span></span>  
 [<span data-ttu-id="55f55-140">BizTalk Server 教學課程</span><span class="sxs-lookup"><span data-stu-id="55f55-140">BizTalk Server Tutorials</span></span>](../core/biztalk-server-tutorials.md)