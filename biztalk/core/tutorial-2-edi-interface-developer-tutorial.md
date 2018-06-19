---
title: '教學課程 2: EDI 介面開發人員教學課程 |Microsoft 文件'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10fb650-cbb9-41e5-a80d-06afd0513814
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cb84454d2570ae6833847b598b55af6cf7777e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286942"
---
# <a name="tutorial-2-edi-interface-developer-tutorial"></a><span data-ttu-id="19eb6-102">教學課程 2: EDI 介面開發人員教學課程</span><span class="sxs-lookup"><span data-stu-id="19eb6-102">Tutorial 2: EDI Interface Developer Tutorial</span></span>
<span data-ttu-id="19eb6-103">本教學課程將示範如何在介面開發人員實例中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 EDI 功能。</span><span class="sxs-lookup"><span data-stu-id="19eb6-103">This tutorial demonstrates how to use the EDI functionality in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in an Interface Developer scenario.</span></span>  
  
 <span data-ttu-id="19eb6-104">**教學課程案例**</span><span class="sxs-lookup"><span data-stu-id="19eb6-104">**Tutorial Scenario**</span></span>  
  
 <span data-ttu-id="19eb6-105">在此實例中，您的交易夥伴會使用 ANSI X12 版本 4010 850 交易集 (850 訊息)，傳送訂單至您的公司。</span><span class="sxs-lookup"><span data-stu-id="19eb6-105">In this scenario, your trading partner sends Purchase Orders to your company using the ANSI X12 Version 4010 850 Transaction Set (an 850 message).</span></span> <span data-ttu-id="19eb6-106">您的公司則使用內部應用程式 (「訂單系統」) 來處理訂單。</span><span class="sxs-lookup"><span data-stu-id="19eb6-106">Your company uses an internal application, the Order System, to process purchase orders.</span></span>  
  
 <span data-ttu-id="19eb6-107">您是介面開發人員，負責設計 850 訊息 (接收自交易夥伴) 和公司內部訂單系統之間的介面。</span><span class="sxs-lookup"><span data-stu-id="19eb6-107">You are an interface developer responsible for designing the interface between the 850 message you receive from your trading partner and your company’s internal Order System.</span></span> <span data-ttu-id="19eb6-108">您的交易夥伴要求其每傳送一個 850 訊息都要收到功能通知 (997)。</span><span class="sxs-lookup"><span data-stu-id="19eb6-108">Your trading partner requires a Functional Acknowledgement (997) for each 850 message it sends.</span></span>  
  
 <span data-ttu-id="19eb6-109">為方便參考，此例使用下列識別項：</span><span class="sxs-lookup"><span data-stu-id="19eb6-109">For ease of reference, the following identifiers are used:</span></span>  
  
|<span data-ttu-id="19eb6-110">實體</span><span class="sxs-lookup"><span data-stu-id="19eb6-110">Entity</span></span>|<span data-ttu-id="19eb6-111">識別碼</span><span class="sxs-lookup"><span data-stu-id="19eb6-111">Identifier</span></span>|  
|------------|----------------|  
|<span data-ttu-id="19eb6-112">您的公司</span><span class="sxs-lookup"><span data-stu-id="19eb6-112">Your company</span></span>|<span data-ttu-id="19eb6-113">OrderSystem</span><span class="sxs-lookup"><span data-stu-id="19eb6-113">OrderSystem</span></span>|  
|<span data-ttu-id="19eb6-114">您的交易夥伴</span><span class="sxs-lookup"><span data-stu-id="19eb6-114">Your trading partner</span></span>|<span data-ttu-id="19eb6-115">Fabrikam</span><span class="sxs-lookup"><span data-stu-id="19eb6-115">Fabrikam</span></span>|  
  
 <span data-ttu-id="19eb6-116">在已完成解決方案中的訊息流程如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="19eb6-116">The message flow in the completed solution will be as follows:</span></span>  
  
 <span data-ttu-id="19eb6-117">![EDI 介面開發人員教學課程訊息流程](../core/media/4944352a-dc77-47f1-a324-bf71444670c5.gif "4944352a-dc77-47f1-a324-bf71444670c5")</span><span class="sxs-lookup"><span data-stu-id="19eb6-117">![EDI Interface Developer Tutorial message flow](../core/media/4944352a-dc77-47f1-a324-bf71444670c5.gif "4944352a-dc77-47f1-a324-bf71444670c5")</span></span>  
  
 <span data-ttu-id="19eb6-118">**訊息流程**</span><span class="sxs-lookup"><span data-stu-id="19eb6-118">**Message Flow**</span></span>  
  
 <span data-ttu-id="19eb6-119">在此教學課程中的解決方案，將會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="19eb6-119">The solution in this tutorial will do the following:</span></span>  
  
1.  <span data-ttu-id="19eb6-120">從交易夥伴 Fabrikam 接收一般檔案交換。</span><span class="sxs-lookup"><span data-stu-id="19eb6-120">Receive a flat-file interchange from the trading partner Fabrikam.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19eb6-121">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="19eb6-121">The events in this list may not occur in the order shown.</span></span>  
  
2.  <span data-ttu-id="19eb6-122">驗證 EDI 交換 (根據其結構描述)、將訊息解譯成 XML，並將訊息 XML 放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="19eb6-122">Validate the EDI interchange against its schema, disassemble the message into XML, and drop the message XML into the MessageBox.</span></span>  
  
3.  <span data-ttu-id="19eb6-123">產生 997 通知給接收的 EDI 交換，並將其放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="19eb6-123">Generate a 997 acknowledgment to the received EDI interchange, and drop it in the MessageBox.</span></span>  
  
4.  <span data-ttu-id="19eb6-124">透過單向傳送埠收取 997 XML，並組合 997 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="19eb6-124">Pick up the 997 XML by a one-way send port, and assemble the 997 EDI interchange.</span></span>  
  
5.  <span data-ttu-id="19eb6-125">傳送 997 交換給 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="19eb6-125">Send the 997 interchange to Fabrikam.</span></span>  
  
6.  <span data-ttu-id="19eb6-126">透過單向傳送埠收取訊息 XML，並組合訊息 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="19eb6-126">Pick up the Msg XML by a one-way send port, and assemble the message EDI interchange.</span></span>  
  
7.  <span data-ttu-id="19eb6-127">傳送 EDI 交換給 OrderSystem。</span><span class="sxs-lookup"><span data-stu-id="19eb6-127">Send the EDI interchange to OrderSystem.</span></span>  
  
 <span data-ttu-id="19eb6-128">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="19eb6-128">**Configuration**</span></span>  
  
 <span data-ttu-id="19eb6-129">在此教學課程中，您將執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="19eb6-129">In this tutorial, you will do the following:</span></span>  
  
-   <span data-ttu-id="19eb6-130">將 BizTalk 設定成期待來自交易夥伴的 850 訊息，以及傳回 997 通知</span><span class="sxs-lookup"><span data-stu-id="19eb6-130">Configure BizTalk to expect the 850 message from your trading partner and to send back a 997 acknowledgment</span></span>  
  
-   <span data-ttu-id="19eb6-131">使用 BizTalk 對應，將 850 訊息資料轉換為「訂單系統」所需要的格式。</span><span class="sxs-lookup"><span data-stu-id="19eb6-131">Use a BizTalk map to convert the 850 message data into the format required by the Order System.</span></span> <span data-ttu-id="19eb6-132">此對應提供於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK 的教學課程檔案中。</span><span class="sxs-lookup"><span data-stu-id="19eb6-132">This map is provided in the tutorial files in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK.</span></span>  
  
-   <span data-ttu-id="19eb6-133">設定接收 850 訊息的接收埠。</span><span class="sxs-lookup"><span data-stu-id="19eb6-133">Configure a receive port for receiving the 850 message.</span></span>  
  
-   <span data-ttu-id="19eb6-134">設定傳送埠，以便將 850 訊息以正確格式傳送到 OrderSystem。</span><span class="sxs-lookup"><span data-stu-id="19eb6-134">Configure a send port to send the 850 message to OrderSystem in the correct format.</span></span>  
  
-   <span data-ttu-id="19eb6-135">設定傳送埠，以便訂閱要路由傳回交易夥伴 Fabrikam 的由 BizTalk 產生的 997 通知。</span><span class="sxs-lookup"><span data-stu-id="19eb6-135">Configure a send port to subscribe to the BizTalk-generated 997 acknowledgment for routing back to the trading partner, Fabrikam.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19eb6-136">本節內容</span><span class="sxs-lookup"><span data-stu-id="19eb6-136">In This Section</span></span>  
  
-   [<span data-ttu-id="19eb6-137">步驟 1： 準備 EDI 介面開發人員教學課程</span><span class="sxs-lookup"><span data-stu-id="19eb6-137">Step 1: Prepare for the EDI Interface Developer Tutorial</span></span>](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)  
  
-   [<span data-ttu-id="19eb6-138">步驟 2： 更新和部署教學課程解決方案</span><span class="sxs-lookup"><span data-stu-id="19eb6-138">Step 2: Update and Deploy the Tutorial Solution</span></span>](../core/step-2-update-and-deploy-the-tutorial-solution.md)  
  
-   [<span data-ttu-id="19eb6-139">步驟 3： 為您的組織設定合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="19eb6-139">Step 3: Configure a Party and Business Profile for Your Organization</span></span>](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)  
  
-   [<span data-ttu-id="19eb6-140">步驟 4： 為交易夥伴設定合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="19eb6-140">Step 4: Configure a Party and Business Profile for Your Trading Partner</span></span>](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner1.md)  
  
-   [<span data-ttu-id="19eb6-141">步驟 5： 設定接收埠和接收位置</span><span class="sxs-lookup"><span data-stu-id="19eb6-141">Step 5: Configure a Receive Port and Receive Location</span></span>](../core/step-5-configure-a-receive-port-and-receive-location.md)  
  
-   [<span data-ttu-id="19eb6-142">步驟 6： 設定傳送埠，以便將資料傳送至您的組織</span><span class="sxs-lookup"><span data-stu-id="19eb6-142">Step 6: Configure a Send Port to Send Data to Your Organization</span></span>](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md)  
  
-   [<span data-ttu-id="19eb6-143">步驟 7： 設定要傳送給交易夥伴的通知的傳送埠</span><span class="sxs-lookup"><span data-stu-id="19eb6-143">Step 7: Configure a Send Port to Send the Acknowledgment to Your Trading Partner</span></span>](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md)  
  
-   [<span data-ttu-id="19eb6-144">步驟 8： 設定合作對象之間交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="19eb6-144">Step 8: Configure the Trading Partner Agreement between the Parties</span></span>](../core/step-8-configure-the-trading-partner-agreement-between-the-parties.md)  
  
-   [<span data-ttu-id="19eb6-145">步驟 9： 測試 EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="19eb6-145">Step 9: Test the EDI Solution</span></span>](../core/step-9-test-the-edi-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="19eb6-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19eb6-146">See Also</span></span>  
 [<span data-ttu-id="19eb6-147">BizTalk Server 教學課程</span><span class="sxs-lookup"><span data-stu-id="19eb6-147">BizTalk Server Tutorials</span></span>](../core/biztalk-server-tutorials.md)