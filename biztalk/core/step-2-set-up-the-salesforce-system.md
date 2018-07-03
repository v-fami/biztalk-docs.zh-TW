---
title: 步驟 2︰ 設定 Salesforce 系統 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0a4b09fb-70a7-4eec-b1e3-f05de0e84df1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 772c18f87351d17b726ad498122715659dca79bc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986527"
---
# <a name="step-2-set-up-the-salesforce-system"></a><span data-ttu-id="b7fe1-102">步驟 2︰ 設定 Salesforce 系統</span><span class="sxs-lookup"><span data-stu-id="b7fe1-102">Step 2: Set up the Salesforce System</span></span>
<span data-ttu-id="b7fe1-103">在此步驟中，您可在成功關閉商機時將 Salesforce 設定為傳送通知。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-103">In this step, you configure Salesforce to send notifications when an opportunity is successfully closed.</span></span> <span data-ttu-id="b7fe1-104">傳送通知之前，您必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b7fe1-104">Before you can send notifications, you need to perform the following steps:</span></span>  
  
-   <span data-ttu-id="b7fe1-105">在 Salesforce 中建立帳戶。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-105">Create an account in Salesforce.</span></span> <span data-ttu-id="b7fe1-106">帳戶代表 northwind 客戶。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-106">An account represents a customer for Northwind.</span></span>  
  
-   <span data-ttu-id="b7fe1-107">為帳戶建立商機。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-107">Create an opportunity for the account.</span></span> <span data-ttu-id="b7fe1-108">商機代表與客戶建立的正面銷售商機。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-108">An opportunity represents a prospective sales opportunity with the customer.</span></span> <span data-ttu-id="b7fe1-109">您也可以在商機中新增客戶感興趣的產品詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-109">As part of the opportunity, you also add the product details that the customer is interested in.</span></span>  
  
-   <span data-ttu-id="b7fe1-110">在 Salesforce 中建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-110">Create a workflow in Salesforce.</span></span>  
  
-   <span data-ttu-id="b7fe1-111">建立和應用程式定義連線的 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-111">Create a Salesforce connected application definition.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7fe1-112">本主題中的步驟假設您已經擁有 Salesforce 開發人員帳戶。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-112">The steps in this topic assume that you already have a Salesforce developer account.</span></span> <span data-ttu-id="b7fe1-113">若要在 Salesforce 中建立新的開發人員帳戶，請前往[ http://go.microsoft.com/fwlink/?LinkId=296424 ](http://go.microsoft.com/fwlink/?LinkId=296424)。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-113">To create a new developer account in Salesforce, go to [http://go.microsoft.com/fwlink/?LinkId=296424](http://go.microsoft.com/fwlink/?LinkId=296424).</span></span>  
  
### <a name="to-create-an-account-in-salesforce"></a><span data-ttu-id="b7fe1-114">在 Salesforce 中建立帳戶</span><span class="sxs-lookup"><span data-stu-id="b7fe1-114">To create an Account in Salesforce</span></span>  
  
1.  <span data-ttu-id="b7fe1-115">使用您的開發人員認證登入 Salesforce.com 入口網站。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-115">Log on to the Salesforce.com portal using your developer credentials.</span></span>  
  
2.  <span data-ttu-id="b7fe1-116">在入口網站中，按一下 **帳號**索引標籤，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-116">On the portal, click the **Accounts** tab, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="b7fe1-117">在 **新帳戶**頁面上，提供各種欄位的值。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-117">On the **New Account** page, provide values for the various fields.</span></span> <span data-ttu-id="b7fe1-118">指定的值**帳戶名稱**是必要的。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-118">Specifying a value for **Account Name** is mandatory.</span></span> <span data-ttu-id="b7fe1-119">本教學課程中，將帳戶名稱指定為`Customer1`。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-119">For this tutorial, specify the account name as `Customer1`.</span></span>  
  
4.  <span data-ttu-id="b7fe1-120">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-120">Click **Save**.</span></span>  
  
### <a name="to-create-an-opportunity-for-the-customer"></a><span data-ttu-id="b7fe1-121">為客戶建立商機</span><span class="sxs-lookup"><span data-stu-id="b7fe1-121">To create an Opportunity for the customer</span></span>  
  
1. <span data-ttu-id="b7fe1-122">在 Salesforce.com 入口網站中，按一下 [**機會**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-122">On the Salesforce.com portal, click the **Opportunities** tab.</span></span>  
  
2. <span data-ttu-id="b7fe1-123">在 **最近商機**區段中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-123">In the **Recent Opportunities** section, click **New**.</span></span>  
  
3. <span data-ttu-id="b7fe1-124">在 新的商機頁面上，指定下列值：</span><span class="sxs-lookup"><span data-stu-id="b7fe1-124">In the New Opportunity page, specify the following values:</span></span>  
  
   1. <span data-ttu-id="b7fe1-125">指定**商機名稱**，例如`Opportunity with Customer 1`。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-125">Specify an **Opportunity Name**, for example, `Opportunity with Customer 1`.</span></span>  
  
   2. <span data-ttu-id="b7fe1-126">指定**帳戶名稱**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-126">Specify the **Account Name**.</span></span> <span data-ttu-id="b7fe1-127">這表示已關聯與此商機相關的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-127">This represents the account with which this opportunity is associated.</span></span> <span data-ttu-id="b7fe1-128">本教學課程的帳戶設定為`Customer1`。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-128">For this tutorial, set the Account to `Customer1`.</span></span> <span data-ttu-id="b7fe1-129">您已在先前的處理程序中建立了此帳戶。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-129">You created this account in the previous procedure.</span></span>  
  
   3. <span data-ttu-id="b7fe1-130">指定**關閉日期**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-130">Specify a **Close Date**.</span></span> <span data-ttu-id="b7fe1-131">這表示要關閉商機的日期。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-131">This represents the date by which the opportunity should be closed.</span></span>  
  
   4. <span data-ttu-id="b7fe1-132">指定**階段**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-132">Specify a **Stage**.</span></span> <span data-ttu-id="b7fe1-133">這表示商機的目前階段。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-133">This denotes the current stage for the opportunity.</span></span> <span data-ttu-id="b7fe1-134">若要開始，您可以設定有機會到任何項目，例如**需要分析**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-134">To start with, you can set the opportunity to anything, for example, **Needs Analysis**.</span></span>  
  
       <span data-ttu-id="b7fe1-135">![在 Salesforce 中建立商機](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")</span><span class="sxs-lookup"><span data-stu-id="b7fe1-135">![Create an opportunity in Salesforce](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="b7fe1-136">請確定您未設定階段**Closed Won**開始。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-136">Make sure you do not set the stage to **Closed Won** to start with.</span></span> <span data-ttu-id="b7fe1-137">在本教學課程，每次當階段設為案例**Closed Won**通知上傳送的轉送端點[!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-137">For the scenario in this tutorial, every time the stage is set to **Closed Won** a notification is sent to a relay endpoint on [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)].</span></span> <span data-ttu-id="b7fe1-138">我們尚未設定該方案的一部分，因此您不應該將階段設**Closed Won**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-138">We haven’t set up that part of the solution yet, so you should not set the stage to **Closed Won**.</span></span>  
  
   5. <span data-ttu-id="b7fe1-139">指定其他可選欄位的值，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-139">Specify values for other optional fields and then click **Save**.</span></span>  
  
   6. <span data-ttu-id="b7fe1-140">在有機會頁面 Customer1 底下**產品**區段中，按一下**新增產品**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-140">On the Opportunity page for Customer1, under the **Products** section, click **Add Product**.</span></span>  
  
   7. <span data-ttu-id="b7fe1-141">從清單中的產品，請在選取的產品，客戶有興趣，，，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-141">From the list of products, select the products that the customer is interested in, and then click **Select**.</span></span>  
  
   8. <span data-ttu-id="b7fe1-142">針對每個選取的產品，指定客戶想，數量，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-142">For each selected product, specify a quantity that the customer wants, and then click **Save**.</span></span>  
  
       <span data-ttu-id="b7fe1-143">![新增產品至商機](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span><span class="sxs-lookup"><span data-stu-id="b7fe1-143">![Add products to an opportunity](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span></span>  
  
## <a name="create-a-salesforce-workflow"></a><span data-ttu-id="b7fe1-144">建立 Salesforce 工作流程</span><span class="sxs-lookup"><span data-stu-id="b7fe1-144">Create a Salesforce Workflow</span></span>  
 <span data-ttu-id="b7fe1-145">在此步驟中，我們會在每次成功關閉商機時，建立工作流程來傳出通知。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-145">In this step we create a workflow to send out a notification every time an opportunity is closed successfully.</span></span> <span data-ttu-id="b7fe1-146">通知是 SOAP 訊息格式和傳送至轉送端點上裝載[!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-146">The notification is in the form of a SOAP message and is sent to a relay endpoint hosted on [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)].</span></span>  
  
#### <a name="to-create-a-workflow-for-opportunities"></a><span data-ttu-id="b7fe1-147">為商機建立工作流程</span><span class="sxs-lookup"><span data-stu-id="b7fe1-147">To create a workflow for opportunities</span></span>  
  
1. <span data-ttu-id="b7fe1-148">在上 Salesforce 入口網站中，按一下右上角的頁面上，在您登入名稱，然後按一下**安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-148">On the Salesforce portal, click your login name at the top right corner of the page, and then click **Setup**.</span></span>  
  
2. <span data-ttu-id="b7fe1-149">在左窗格中，在**應用程式安裝程式**，展開**建立**，展開**工作流程與核准**，然後按一下**工作流程規則**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-149">In the left pane, under **App Setup**, expand **Create**, expand **Workflow & Approvals**, and then click **Workflow Rules**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b7fe1-150">若您是第一次開啟工作流程規則頁面，會看見一些相關的資訊，幫助您了解 Salesforce 中的工作流程如何運作。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-150">If you are opening the Workflow Rules page for the first time, you will be presented with some information to understand how workflows work in Salesforce.</span></span> <span data-ttu-id="b7fe1-151">閱讀這些資訊，然後按一下**繼續**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-151">Read through the information and then click **Continue**.</span></span>  
  
3. <span data-ttu-id="b7fe1-152">在 **所有的工作流程規則**頁面上，按一下**新規則**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-152">On the **All Workflow Rules** page, click **New Rule**.</span></span>  
  
4. <span data-ttu-id="b7fe1-153">從**選取物件**清單中，按一下**機會**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-153">From the **Select Object** list, click **Opportunity**, and then click **Next**.</span></span>  
  
5. <span data-ttu-id="b7fe1-154">在下一個頁面中，指定以下項目：</span><span class="sxs-lookup"><span data-stu-id="b7fe1-154">In the next page, specify the following:</span></span>  
  
   1.  <span data-ttu-id="b7fe1-155">設定**規則名稱**做為`Closed Opportunity`。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-155">Set the **Rule Name** as `Closed Opportunity`.</span></span>  
  
   2.  <span data-ttu-id="b7fe1-156">設定**Evaluation Criteria**作為**建立，並隨時編輯為準則相符**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-156">Set the **Evaluation Criteria** as **created, and any time it’s edited to subsequently meet criteria**.</span></span>  
  
   3.  <span data-ttu-id="b7fe1-157">針對**規則條件**，設定執行規則時**符合準則**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-157">For the **Rule Criteria**, set to run the rule when the **criteria are met**.</span></span>  
  
   4.  <span data-ttu-id="b7fe1-158">設定**欄位**來**機會： 階段**，**運算子**至**等於**，並**值**至`Closed Won`.</span><span class="sxs-lookup"><span data-stu-id="b7fe1-158">Set **Field** to **Opportunity: Stage**, **Operator** to **equals**, and **Value** to `Closed Won`.</span></span>  
  
        <span data-ttu-id="b7fe1-159">![建立 Salesforce 工作流程](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")</span><span class="sxs-lookup"><span data-stu-id="b7fe1-159">![Create a Salesforce workflow](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")</span></span>  
  
   5.  <span data-ttu-id="b7fe1-160">按一下 **儲存並下一步**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-160">Click **Save & Next**.</span></span>  
  
6. <span data-ttu-id="b7fe1-161">定義新規則的工作流程動作：</span><span class="sxs-lookup"><span data-stu-id="b7fe1-161">Define the workflow action for the new rule:</span></span>  
  
   1. <span data-ttu-id="b7fe1-162">在 **指定工作流程動作**頁面上，按一下**加入工作流程動作**按鈕，然後按一下**新增輸出訊息**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-162">On the **Specify Workflow Actions** page, click **Add Workflow Action** button and then click **New Outbound Message**.</span></span>  
  
   2. <span data-ttu-id="b7fe1-163">設定**名稱**並**唯一名稱**欄位`NewOp1`。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-163">Set the **Name** and **Unique Name** fields to `NewOp1`.</span></span>  
  
   3. <span data-ttu-id="b7fe1-164">例如，指定描述， `Message sent when an opportunity is successfully closed`。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-164">Specify a description, such as, the `Message sent when an opportunity is successfully closed`.</span></span>  
  
   4. <span data-ttu-id="b7fe1-165">指定**端點 URL**做為`https://btssalesforce.servicebus.windows.net/notifications/opportunity`。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-165">Specify the **Endpoint URL** as `https://btssalesforce.servicebus.windows.net/notifications/opportunity`.</span></span>  
  
       <span data-ttu-id="b7fe1-166">在這裡， **btssalesforce**是您[!INCLUDE[sb](../includes/sb-md.md)]您在先前步驟中建立的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-166">Here, **btssalesforce** is your [!INCLUDE[sb](../includes/sb-md.md)] namespace that you created in earlier steps.</span></span> <span data-ttu-id="b7fe1-167">**/notifications/opportunity/** 表示我們將在本教學課程的稍後步驟中建立的轉送。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-167">**/notifications/opportunity/** represents the relay that we will create in later steps of this tutorial.</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="b7fe1-168">您必須指定[!INCLUDE[sb](../includes/sb-md.md)]您稍早建立的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-168">You must specify the [!INCLUDE[sb](../includes/sb-md.md)] namespace that you created earlier.</span></span>  
  
   5. <span data-ttu-id="b7fe1-169">請確定**受保護的元件**已清除核取方塊並**傳送工作階段識別碼** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-169">Make sure the **Protected Component** check box is clear and the **Send Session ID** check box is checked.</span></span>  
  
   6. <span data-ttu-id="b7fe1-170">針對**機會欄位傳送**選取相關的欄位，從**可用的欄位**清單，然後按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-170">For **Opportunity fields to send** select the relevant fields from the **Available Fields** list and then click the **Add** button.</span></span>  
  
   7. <span data-ttu-id="b7fe1-171">按一下 **儲存**，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-171">Click **Save** and then click **Done**.</span></span>  
  
   8. <span data-ttu-id="b7fe1-172">在左窗格中，在**應用程式安裝程式**，展開**建立**，展開**工作流程與核准**，然後按一下**工作流程規則**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-172">In the left pane, under **App Setup**, expand **Create**, expand **Workflow & Approvals**, and then click **Workflow Rules**.</span></span> <span data-ttu-id="b7fe1-173">確認**已關閉商機**規則會列在那裡。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-173">Verify that the **Closed Opportunity** rule is listed there.</span></span> <span data-ttu-id="b7fe1-174">底下**動作**資料行**已關閉商機**規則中，按一下 **啟動**以啟動規則。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-174">Under the **Action** column for the **Closed Opportunity** rule, click **Activate** to activate the rule.</span></span>  
  
## <a name="create-a-salesforce-connected-application"></a><span data-ttu-id="b7fe1-175">建立 Salesforce 連線應用程式</span><span class="sxs-lookup"><span data-stu-id="b7fe1-175">Create a Salesforce Connected Application</span></span>  
 <span data-ttu-id="b7fe1-176">建立連線的應用程式定義會產生在要求 OAuth 權杖以存取連線至 Salesforce 時所需的一組金鑰。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-176">Creating a connected application definition generates a set of keys required to request OAuth tokens to access to connect to Salesforce.</span></span> <span data-ttu-id="b7fe1-177">在本教學課程的之後階段，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會成為使用已連線應用程式定義來查詢 Salesforce 的已連線應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-177">In the later stages of this tutorial, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will be the connected application that queries Salesforce using the connected application definition.</span></span>  
  
#### <a name="to-create-a-connected-application-for-salesforce"></a><span data-ttu-id="b7fe1-178">為 Salesforce 中建立連接的應用程式</span><span class="sxs-lookup"><span data-stu-id="b7fe1-178">To create a connected application for Salesforce</span></span>  
  
1. <span data-ttu-id="b7fe1-179">在上 Salesforce 入口網站中，按一下右上角的頁面上，在您登入名稱，然後按一下**安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-179">On the Salesforce portal, click your login name at the top right corner of the page, and then click **Setup**.</span></span>  
  
2. <span data-ttu-id="b7fe1-180">在左窗格中，在**應用程式安裝程式**，展開**建立**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-180">In the left pane, under **App Setup**, expand **Create**, and then expand **Apps**.</span></span> <span data-ttu-id="b7fe1-181">在 **應用程式**頁面的 **連線到應用程式**區段中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-181">On the **Apps** page, under the **Connected Apps** section, click **New**.</span></span>  
  
3. <span data-ttu-id="b7fe1-182">在 **新的連線應用程式**頁面上，指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="b7fe1-182">In the **New Connection App** page, specify the following:</span></span>  
  
   1. <span data-ttu-id="b7fe1-183">針對**連線的應用程式名稱**，指定`BizTalk_Salesforce`。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-183">For **Connected App Name**, specify `BizTalk_Salesforce`.</span></span>  
  
   2. <span data-ttu-id="b7fe1-184">針對**開發人員名稱**，指定您的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-184">For **Developer Name**, specify your log on name.</span></span>  
  
   3. <span data-ttu-id="b7fe1-185">針對**Contact Email**，指定您的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-185">For **Contact Email**, specify your e-mail.</span></span>  
  
   4. <span data-ttu-id="b7fe1-186">針對**回呼 URL**，指定有效的 URL。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-186">For **Callback URL**, specify a valid URL.</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="b7fe1-187">由於我們在此方案中透過 Salesforce 進行驗證的方法，您在這裡指定的值無法使用。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-187">Because of the way we authenticate with Salesforce in this scenario, the value you specify here is not used.</span></span>  
  
   5. <span data-ttu-id="b7fe1-188">底下**可用的 OAuth 領域**，選取**完整存取權**，**代替您執行要求，在任何時候**，和**存取及管理您的資料**，然後按一下 **新增**按鈕，以將它們移至**選取 OAuth 範圍**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-188">Under **Available OAuth Scopes**, select **Full access**, **Perform requests on your behalf at any time**, and **Access and manage your data** and then click the **Add** button to move them into the **Selected OAuth Scopes**.</span></span>  
  
   6. <span data-ttu-id="b7fe1-189">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-189">Click **Save**.</span></span> <span data-ttu-id="b7fe1-190">出現的頁面包含的相關資訊**取用者索引鍵**並**取用者祕密**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-190">The page that appears contains information about the **Consumer Key** and **Consumer Secret**.</span></span> <span data-ttu-id="b7fe1-191">您必須記下這些值。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-191">You must make a note of these values.</span></span> <span data-ttu-id="b7fe1-192">當從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 連線至 Saleforce 時，您會需要這些值。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-192">You will need these values while connecting to Salesforce from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
       <span data-ttu-id="b7fe1-193">![Salesforce 存取金鑰](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")</span><span class="sxs-lookup"><span data-stu-id="b7fe1-193">![Keys for Salesforce access](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")</span></span>  
  
4. <span data-ttu-id="b7fe1-194">最後，會產生從不明網路位置連線至 Salesforce 所需的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-194">Finally, generate a security token required for connecting to Salesforce from unknown network locations.</span></span>  
  
   1.  <span data-ttu-id="b7fe1-195">在 Salesforce 入口網站的左窗格底下**個人的安裝程式**，展開**個人資訊**，然後按一下**重設我的安全性權杖**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-195">On the left pane of the Salesforce portal, under **Personal Setup**, expand **Personal Information**, and then click **Reset My Security Token**.</span></span>  
  
   2.  <span data-ttu-id="b7fe1-196">閱讀警告，然後按一下**重設安全性權杖**。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-196">Read the warning and then click **Reset Security Token**.</span></span>  
  
   3.  <span data-ttu-id="b7fe1-197">您應該會在建立 Salesforce 帳戶時指定的電子郵件位置收到安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="b7fe1-197">You should receive the security token at the e-mail address you specified while creating your Salesforce account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fe1-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7fe1-198">See Also</span></span>  
 [<span data-ttu-id="b7fe1-199">教學課程 6： 整合 BizTalk Server 2013 與 Salesforce</span><span class="sxs-lookup"><span data-stu-id="b7fe1-199">Tutorial 6: Integrating BizTalk Server 2013 with Salesforce</span></span>](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)