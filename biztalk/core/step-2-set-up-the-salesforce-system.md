---
title: 步驟 2： 設定 Salesforce 系統 |Microsoft 文件
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
ms.openlocfilehash: d65a1c741103b9c8f1e9493b7bd2aa56eef8cf18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279926"
---
# <a name="step-2-set-up-the-salesforce-system"></a><span data-ttu-id="52289-102">步驟 2： 設定 Salesforce 系統</span><span class="sxs-lookup"><span data-stu-id="52289-102">Step 2: Set up the Salesforce System</span></span>
<span data-ttu-id="52289-103">在此步驟中，您可在成功關閉商機時將 Salesforce 設定為傳送通知。</span><span class="sxs-lookup"><span data-stu-id="52289-103">In this step, you configure Salesforce to send notifications when an opportunity is successfully closed.</span></span> <span data-ttu-id="52289-104">傳送通知之前，您必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="52289-104">Before you can send notifications, you need to perform the following steps:</span></span>  
  
-   <span data-ttu-id="52289-105">在 Salesforce 中建立帳戶。</span><span class="sxs-lookup"><span data-stu-id="52289-105">Create an account in Salesforce.</span></span> <span data-ttu-id="52289-106">帳戶代表 Northwind 的客戶。</span><span class="sxs-lookup"><span data-stu-id="52289-106">An account represents a customer for Northwind.</span></span>  
  
-   <span data-ttu-id="52289-107">為帳戶建立商機。</span><span class="sxs-lookup"><span data-stu-id="52289-107">Create an opportunity for the account.</span></span> <span data-ttu-id="52289-108">商機代表與客戶建立的正面銷售商機。</span><span class="sxs-lookup"><span data-stu-id="52289-108">An opportunity represents a prospective sales opportunity with the customer.</span></span> <span data-ttu-id="52289-109">您也可以在商機中新增客戶感興趣的產品詳細資料。</span><span class="sxs-lookup"><span data-stu-id="52289-109">As part of the opportunity, you also add the product details that the customer is interested in.</span></span>  
  
-   <span data-ttu-id="52289-110">在 Salesforce 中建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="52289-110">Create a workflow in Salesforce.</span></span>  
  
-   <span data-ttu-id="52289-111">建立和應用程式定義連線的 Salesforce。</span><span class="sxs-lookup"><span data-stu-id="52289-111">Create a Salesforce connected application definition.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52289-112">本主題中的步驟假設您已經擁有 Salesforce 開發人員帳戶。</span><span class="sxs-lookup"><span data-stu-id="52289-112">The steps in this topic assume that you already have a Salesforce developer account.</span></span> <span data-ttu-id="52289-113">若要在 Salesforce 中建立新的開發人員帳戶，請移至[http://go.microsoft.com/fwlink/?LinkId=296424](http://go.microsoft.com/fwlink/?LinkId=296424)。</span><span class="sxs-lookup"><span data-stu-id="52289-113">To create a new developer account in Salesforce, go to [http://go.microsoft.com/fwlink/?LinkId=296424](http://go.microsoft.com/fwlink/?LinkId=296424).</span></span>  
  
### <a name="to-create-an-account-in-salesforce"></a><span data-ttu-id="52289-114">在 Salesforce 中建立帳戶</span><span class="sxs-lookup"><span data-stu-id="52289-114">To create an Account in Salesforce</span></span>  
  
1.  <span data-ttu-id="52289-115">使用您的開發人員認證登入 Salesforce.com 入口網站。</span><span class="sxs-lookup"><span data-stu-id="52289-115">Log on to the Salesforce.com portal using your developer credentials.</span></span>  
  
2.  <span data-ttu-id="52289-116">在入口網站中，按一下 **帳戶**索引標籤，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="52289-116">On the portal, click the **Accounts** tab, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="52289-117">在**新帳戶**頁面上，提供各種欄位的值。</span><span class="sxs-lookup"><span data-stu-id="52289-117">On the **New Account** page, provide values for the various fields.</span></span> <span data-ttu-id="52289-118">指定的值**帳戶名稱**是強制性。</span><span class="sxs-lookup"><span data-stu-id="52289-118">Specifying a value for **Account Name** is mandatory.</span></span> <span data-ttu-id="52289-119">此教學課程中，將帳戶名稱指定為`Customer1`。</span><span class="sxs-lookup"><span data-stu-id="52289-119">For this tutorial, specify the account name as `Customer1`.</span></span>  
  
4.  <span data-ttu-id="52289-120">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="52289-120">Click **Save**.</span></span>  
  
### <a name="to-create-an-opportunity-for-the-customer"></a><span data-ttu-id="52289-121">為客戶建立商機</span><span class="sxs-lookup"><span data-stu-id="52289-121">To create an Opportunity for the customer</span></span>  
  
1.  <span data-ttu-id="52289-122">在 Salesforce.com 入口網站中，按一下 [**機會**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="52289-122">On the Salesforce.com portal, click the **Opportunities** tab.</span></span>  
  
2.  <span data-ttu-id="52289-123">在**最近商機**區段中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="52289-123">In the **Recent Opportunities** section, click **New**.</span></span>  
  
3.  <span data-ttu-id="52289-124">在 新的商機頁面上，指定下列值：</span><span class="sxs-lookup"><span data-stu-id="52289-124">In the New Opportunity page, specify the following values:</span></span>  
  
    1.  <span data-ttu-id="52289-125">指定**商機名稱**，例如`Opportunity with Customer 1`。</span><span class="sxs-lookup"><span data-stu-id="52289-125">Specify an **Opportunity Name**, for example, `Opportunity with Customer 1`.</span></span>  
  
    2.  <span data-ttu-id="52289-126">指定**帳戶名稱**。</span><span class="sxs-lookup"><span data-stu-id="52289-126">Specify the **Account Name**.</span></span> <span data-ttu-id="52289-127">這表示已關聯與此商機相關的帳戶。</span><span class="sxs-lookup"><span data-stu-id="52289-127">This represents the account with which this opportunity is associated.</span></span> <span data-ttu-id="52289-128">此教學課程中，將帳戶設`Customer1`。</span><span class="sxs-lookup"><span data-stu-id="52289-128">For this tutorial, set the Account to `Customer1`.</span></span> <span data-ttu-id="52289-129">您已在先前的處理程序中建立了此帳戶。</span><span class="sxs-lookup"><span data-stu-id="52289-129">You created this account in the previous procedure.</span></span>  
  
    3.  <span data-ttu-id="52289-130">指定**關閉日期**。</span><span class="sxs-lookup"><span data-stu-id="52289-130">Specify a **Close Date**.</span></span> <span data-ttu-id="52289-131">這表示要關閉商機的日期。</span><span class="sxs-lookup"><span data-stu-id="52289-131">This represents the date by which the opportunity should be closed.</span></span>  
  
    4.  <span data-ttu-id="52289-132">指定**階段**。</span><span class="sxs-lookup"><span data-stu-id="52289-132">Specify a **Stage**.</span></span> <span data-ttu-id="52289-133">這表示商機的目前階段。</span><span class="sxs-lookup"><span data-stu-id="52289-133">This denotes the current stage for the opportunity.</span></span> <span data-ttu-id="52289-134">開始使用，您可以將商機設為任何項目，例如**需要分析**。</span><span class="sxs-lookup"><span data-stu-id="52289-134">To start with, you can set the opportunity to anything, for example, **Needs Analysis**.</span></span>  
  
         <span data-ttu-id="52289-135">![在 Salesforce 中建立商機](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")</span><span class="sxs-lookup"><span data-stu-id="52289-135">![Create an opportunity in Salesforce](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="52289-136">請確定您未設定階段**Closed Won**開始使用。</span><span class="sxs-lookup"><span data-stu-id="52289-136">Make sure you do not set the stage to **Closed Won** to start with.</span></span> <span data-ttu-id="52289-137">在本教學課程，每次當階段設為案例**Closed Won**傳送通知給轉送端點[!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="52289-137">For the scenario in this tutorial, every time the stage is set to **Closed Won** a notification is sent to a relay endpoint on [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)].</span></span> <span data-ttu-id="52289-138">我們您尚未設定該方案的一部分，因此您不應該將階段設**Closed Won**。</span><span class="sxs-lookup"><span data-stu-id="52289-138">We haven’t set up that part of the solution yet, so you should not set the stage to **Closed Won**.</span></span>  
  
    5.  <span data-ttu-id="52289-139">指定其他可選欄位的值，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="52289-139">Specify values for other optional fields and then click **Save**.</span></span>  
  
    6.  <span data-ttu-id="52289-140">在有機會 頁面上的 Customer1 底下**產品**區段中，按一下**新增產品**。</span><span class="sxs-lookup"><span data-stu-id="52289-140">On the Opportunity page for Customer1, under the **Products** section, click **Add Product**.</span></span>  
  
    7.  <span data-ttu-id="52289-141">從產品的清單，請在選取的產品的客戶感興趣，，，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="52289-141">From the list of products, select the products that the customer is interested in, and then click **Select**.</span></span>  
  
    8.  <span data-ttu-id="52289-142">針對每個選取的產品，請指定客戶想，數量，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="52289-142">For each selected product, specify a quantity that the customer wants, and then click **Save**.</span></span>  
  
         <span data-ttu-id="52289-143">![新增產品至商機](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span><span class="sxs-lookup"><span data-stu-id="52289-143">![Add products to an opportunity](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span></span>  
  
## <a name="create-a-salesforce-workflow"></a><span data-ttu-id="52289-144">建立 Salesforce 工作流程</span><span class="sxs-lookup"><span data-stu-id="52289-144">Create a Salesforce Workflow</span></span>  
 <span data-ttu-id="52289-145">在此步驟中，我們會在每次成功關閉商機時，建立工作流程來傳出通知。</span><span class="sxs-lookup"><span data-stu-id="52289-145">In this step we create a workflow to send out a notification every time an opportunity is closed successfully.</span></span> <span data-ttu-id="52289-146">通知是 SOAP 訊息的格式，且會傳送到上裝載的轉送端點[!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="52289-146">The notification is in the form of a SOAP message and is sent to a relay endpoint hosted on [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)].</span></span>  
  
#### <a name="to-create-a-workflow-for-opportunities"></a><span data-ttu-id="52289-147">為商機建立工作流程</span><span class="sxs-lookup"><span data-stu-id="52289-147">To create a workflow for opportunities</span></span>  
  
1.  <span data-ttu-id="52289-148">在 Salesforce 入口網站中，按一下右上角的頁面上，在您登入的名稱，然後按一下 **安裝**。</span><span class="sxs-lookup"><span data-stu-id="52289-148">On the Salesforce portal, click your login name at the top right corner of the page, and then click **Setup**.</span></span>  
  
2.  <span data-ttu-id="52289-149">在左窗格中下,**應用程式安裝**，依序展開**建立**，展開**工作流程 （& s) 核准**，然後按一下**工作流程規則**。</span><span class="sxs-lookup"><span data-stu-id="52289-149">In the left pane, under **App Setup**, expand **Create**, expand **Workflow & Approvals**, and then click **Workflow Rules**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="52289-150">若您是第一次開啟工作流程規則頁面，會看見一些相關的資訊，幫助您了解 Salesforce 中的工作流程如何運作。</span><span class="sxs-lookup"><span data-stu-id="52289-150">If you are opening the Workflow Rules page for the first time, you will be presented with some information to understand how workflows work in Salesforce.</span></span> <span data-ttu-id="52289-151">閱讀這些資訊，然後按一下**繼續**。</span><span class="sxs-lookup"><span data-stu-id="52289-151">Read through the information and then click **Continue**.</span></span>  
  
3.  <span data-ttu-id="52289-152">在**所有工作流程規則**頁面上，按一下**新規則**。</span><span class="sxs-lookup"><span data-stu-id="52289-152">On the **All Workflow Rules** page, click **New Rule**.</span></span>  
  
4.  <span data-ttu-id="52289-153">從**選取物件**清單中，按一下**機會**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="52289-153">From the **Select Object** list, click **Opportunity**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="52289-154">在下一個頁面中，指定以下項目：</span><span class="sxs-lookup"><span data-stu-id="52289-154">In the next page, specify the following:</span></span>  
  
    1.  <span data-ttu-id="52289-155">設定**規則名稱**為`Closed Opportunity`。</span><span class="sxs-lookup"><span data-stu-id="52289-155">Set the **Rule Name** as `Closed Opportunity`.</span></span>  
  
    2.  <span data-ttu-id="52289-156">設定**評估準則**為**建立，並隨時編輯為準則相符**。</span><span class="sxs-lookup"><span data-stu-id="52289-156">Set the **Evaluation Criteria** as **created, and any time it’s edited to subsequently meet criteria**.</span></span>  
  
    3.  <span data-ttu-id="52289-157">如**規則條件**，設定執行規則時**符合準則**。</span><span class="sxs-lookup"><span data-stu-id="52289-157">For the **Rule Criteria**, set to run the rule when the **criteria are met**.</span></span>  
  
    4.  <span data-ttu-id="52289-158">設定**欄位**至**機會： 階段**，**運算子**至**等於**，和**值**至`Closed Won`.</span><span class="sxs-lookup"><span data-stu-id="52289-158">Set **Field** to **Opportunity: Stage**, **Operator** to **equals**, and **Value** to `Closed Won`.</span></span>  
  
         <span data-ttu-id="52289-159">![建立 Salesforce 工作流程](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")</span><span class="sxs-lookup"><span data-stu-id="52289-159">![Create a Salesforce workflow](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")</span></span>  
  
    5.  <span data-ttu-id="52289-160">按一下**儲存與下一步**。</span><span class="sxs-lookup"><span data-stu-id="52289-160">Click **Save & Next**.</span></span>  
  
6.  <span data-ttu-id="52289-161">定義新規則的工作流程動作：</span><span class="sxs-lookup"><span data-stu-id="52289-161">Define the workflow action for the new rule:</span></span>  
  
    1.  <span data-ttu-id="52289-162">在**指定工作流程動作**頁面上，按一下**加入工作流程動作**按鈕，然後按一下**新增輸出訊息**。</span><span class="sxs-lookup"><span data-stu-id="52289-162">On the **Specify Workflow Actions** page, click **Add Workflow Action** button and then click **New Outbound Message**.</span></span>  
  
    2.  <span data-ttu-id="52289-163">設定**名稱**和**唯一名稱**欄位`NewOp1`。</span><span class="sxs-lookup"><span data-stu-id="52289-163">Set the **Name** and **Unique Name** fields to `NewOp1`.</span></span>  
  
    3.  <span data-ttu-id="52289-164">指定描述，例如， `Message sent when an opportunity is successfully closed`。</span><span class="sxs-lookup"><span data-stu-id="52289-164">Specify a description, such as, the `Message sent when an opportunity is successfully closed`.</span></span>  
  
    4.  <span data-ttu-id="52289-165">指定**端點 URL**為`https://btssalesforce.servicebus.windows.net/notifications/opportunity`。</span><span class="sxs-lookup"><span data-stu-id="52289-165">Specify the **Endpoint URL** as `https://btssalesforce.servicebus.windows.net/notifications/opportunity`.</span></span>  
  
         <span data-ttu-id="52289-166">在這裡， **btssalesforce**是您[!INCLUDE[sb](../includes/sb-md.md)]您在先前步驟中建立的命名空間。</span><span class="sxs-lookup"><span data-stu-id="52289-166">Here, **btssalesforce** is your [!INCLUDE[sb](../includes/sb-md.md)] namespace that you created in earlier steps.</span></span> <span data-ttu-id="52289-167">**/notifications/opportunity/** 表示我們將在本教學課程的後續步驟中建立的轉送。</span><span class="sxs-lookup"><span data-stu-id="52289-167">**/notifications/opportunity/** represents the relay that we will create in later steps of this tutorial.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="52289-168">您必須指定[!INCLUDE[sb](../includes/sb-md.md)]您稍早建立的命名空間。</span><span class="sxs-lookup"><span data-stu-id="52289-168">You must specify the [!INCLUDE[sb](../includes/sb-md.md)] namespace that you created earlier.</span></span>  
  
    5.  <span data-ttu-id="52289-169">請確定**保護元件**核取方塊已清除和**傳送工作階段識別碼**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="52289-169">Make sure the **Protected Component** check box is clear and the **Send Session ID** check box is checked.</span></span>  
  
    6.  <span data-ttu-id="52289-170">如**商機欄位傳送**選取相關欄位從**可用的欄位**清單，然後按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="52289-170">For **Opportunity fields to send** select the relevant fields from the **Available Fields** list and then click the **Add** button.</span></span>  
  
    7.  <span data-ttu-id="52289-171">按一下**儲存**，然後按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="52289-171">Click **Save** and then click **Done**.</span></span>  
  
    8.  <span data-ttu-id="52289-172">在左窗格中下,**應用程式安裝**，依序展開**建立**，展開**工作流程 （& s) 核准**，然後按一下**工作流程規則**。</span><span class="sxs-lookup"><span data-stu-id="52289-172">In the left pane, under **App Setup**, expand **Create**, expand **Workflow & Approvals**, and then click **Workflow Rules**.</span></span> <span data-ttu-id="52289-173">確認**已關閉商機**規則已列於此處。</span><span class="sxs-lookup"><span data-stu-id="52289-173">Verify that the **Closed Opportunity** rule is listed there.</span></span> <span data-ttu-id="52289-174">在下**動作**資料行**已關閉商機**規則中，按一下**Activate**來啟用規則。</span><span class="sxs-lookup"><span data-stu-id="52289-174">Under the **Action** column for the **Closed Opportunity** rule, click **Activate** to activate the rule.</span></span>  
  
## <a name="create-a-salesforce-connected-application"></a><span data-ttu-id="52289-175">建立 Salesforce 連接應用程式</span><span class="sxs-lookup"><span data-stu-id="52289-175">Create a Salesforce Connected Application</span></span>  
 <span data-ttu-id="52289-176">建立連線的應用程式定義會產生在要求 OAuth 權杖以存取連線至 Salesforce 時所需的一組金鑰。</span><span class="sxs-lookup"><span data-stu-id="52289-176">Creating a connected application definition generates a set of keys required to request OAuth tokens to access to connect to Salesforce.</span></span> <span data-ttu-id="52289-177">在本教學課程的之後階段，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會成為使用已連線應用程式定義來查詢 Salesforce 的已連線應用程式。</span><span class="sxs-lookup"><span data-stu-id="52289-177">In the later stages of this tutorial, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will be the connected application that queries Salesforce using the connected application definition.</span></span>  
  
#### <a name="to-create-a-connected-application-for-salesforce"></a><span data-ttu-id="52289-178">若要連接的應用程式建立 salesforce</span><span class="sxs-lookup"><span data-stu-id="52289-178">To create a connected application for Salesforce</span></span>  
  
1.  <span data-ttu-id="52289-179">在 Salesforce 入口網站中，按一下右上角的頁面上，在您登入的名稱，然後按一下 **安裝**。</span><span class="sxs-lookup"><span data-stu-id="52289-179">On the Salesforce portal, click your login name at the top right corner of the page, and then click **Setup**.</span></span>  
  
2.  <span data-ttu-id="52289-180">在左窗格中下,**應用程式安裝**，依序展開**建立**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="52289-180">In the left pane, under **App Setup**, expand **Create**, and then expand **Apps**.</span></span> <span data-ttu-id="52289-181">在**應用程式**頁面的 **己連線應用程式**區段中，按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="52289-181">On the **Apps** page, under the **Connected Apps** section, click **New**.</span></span>  
  
3.  <span data-ttu-id="52289-182">在**新連線應用程式**頁面上，指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="52289-182">In the **New Connection App** page, specify the following:</span></span>  
  
    1.  <span data-ttu-id="52289-183">如**連線應用程式名稱**，指定`BizTalk_Salesforce`。</span><span class="sxs-lookup"><span data-stu-id="52289-183">For **Connected App Name**, specify `BizTalk_Salesforce`.</span></span>  
  
    2.  <span data-ttu-id="52289-184">如**開發人員名稱**，指定您的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="52289-184">For **Developer Name**, specify your log on name.</span></span>  
  
    3.  <span data-ttu-id="52289-185">如**Contact Email**，指定您的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="52289-185">For **Contact Email**, specify your e-mail.</span></span>  
  
    4.  <span data-ttu-id="52289-186">如**回呼 URL**，指定有效的 URL。</span><span class="sxs-lookup"><span data-stu-id="52289-186">For **Callback URL**, specify a valid URL.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="52289-187">由於我們在此方案中透過 Salesforce 進行驗證的方法，您在這裡指定的值無法使用。</span><span class="sxs-lookup"><span data-stu-id="52289-187">Because of the way we authenticate with Salesforce in this scenario, the value you specify here is not used.</span></span>  
  
    5.  <span data-ttu-id="52289-188">下**可用的 OAuth 領域**，選取**完整存取權**，**代替您執行要求，在任何時候**，和**存取及管理 wit_nextref**，然後按一下 [**新增**] 按鈕，將它們移入**選取 OAuth 範圍**。</span><span class="sxs-lookup"><span data-stu-id="52289-188">Under **Available OAuth Scopes**, select **Full access**, **Perform requests on your behalf at any time**, and **Access and manage your data** and then click the **Add** button to move them into the **Selected OAuth Scopes**.</span></span>  
  
    6.  <span data-ttu-id="52289-189">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="52289-189">Click **Save**.</span></span> <span data-ttu-id="52289-190">出現的頁面包含有關的資訊**取用者索引鍵**和**取用者秘密**。</span><span class="sxs-lookup"><span data-stu-id="52289-190">The page that appears contains information about the **Consumer Key** and **Consumer Secret**.</span></span> <span data-ttu-id="52289-191">您必須記下這些值。</span><span class="sxs-lookup"><span data-stu-id="52289-191">You must make a note of these values.</span></span> <span data-ttu-id="52289-192">當從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 連線至 Saleforce 時，您會需要這些值。</span><span class="sxs-lookup"><span data-stu-id="52289-192">You will need these values while connecting to Salesforce from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
         <span data-ttu-id="52289-193">![Salesforce 存取金鑰](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")</span><span class="sxs-lookup"><span data-stu-id="52289-193">![Keys for Salesforce access](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")</span></span>  
  
4.  <span data-ttu-id="52289-194">最後，會產生從不明網路位置連線至 Salesforce 所需的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="52289-194">Finally, generate a security token required for connecting to Salesforce from unknown network locations.</span></span>  
  
    1.  <span data-ttu-id="52289-195">在 Salesforce 入口網站的左窗格下**個人設定**，依序展開**個人資訊**，然後按一下 **重設我的安全性 Token**。</span><span class="sxs-lookup"><span data-stu-id="52289-195">On the left pane of the Salesforce portal, under **Personal Setup**, expand **Personal Information**, and then click **Reset My Security Token**.</span></span>  
  
    2.  <span data-ttu-id="52289-196">閱讀警告，然後按一下**重設安全性 Token**。</span><span class="sxs-lookup"><span data-stu-id="52289-196">Read the warning and then click **Reset Security Token**.</span></span>  
  
    3.  <span data-ttu-id="52289-197">您應該會在建立 Salesforce 帳戶時指定的電子郵件位置收到安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="52289-197">You should receive the security token at the e-mail address you specified while creating your Salesforce account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52289-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52289-198">See Also</span></span>  
 [<span data-ttu-id="52289-199">教學課程 6： 與 Salesforce 整合 BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="52289-199">Tutorial 6: Integrating BizTalk Server 2013 with Salesforce</span></span>](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)