---
title: （適用於 Azure) 的步驟 2： 建立 EDI 協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8003697-4955-45c0-ba0b-e7c293a050a2
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc2db7361aef663c70c7227febfea5fc08dc699a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22280070"
---
# <a name="step-2-for-azure-create-an-edi-agreement"></a><span data-ttu-id="95f66-102">（適用於 Azure) 的步驟 2： 建立 EDI 協議</span><span class="sxs-lookup"><span data-stu-id="95f66-102">Step 2 (For Azure): Create an EDI Agreement</span></span>
<span data-ttu-id="95f66-103">在本主題中，您將建立使用 Azure BizTalk 入口網站可做為夥伴的一部分[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95f66-103">In this topic, you will create partners using the Azure BizTalk portal available as part of the [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)].</span></span> <span data-ttu-id="95f66-104">您也會建立兩個夥伴 （Northwind 和 Contoso） 來處理的 X12 銷售訂單訊息傳送至 Northwind 的 contoso 之間的協議。</span><span class="sxs-lookup"><span data-stu-id="95f66-104">You will also create an agreement between the two partners (Northwind and Contoso) to process the X12 sales order message sent by Contoso to Northwind.</span></span>  
  
### <a name="to-create-partners"></a><span data-ttu-id="95f66-105">若要建立夥伴</span><span class="sxs-lookup"><span data-stu-id="95f66-105">To create partners</span></span>  
  
1.  <span data-ttu-id="95f66-106">使用您的 Microsoft 帳戶，登入入口網站， [http://go.microsoft.com/fwlink/p/?LinkId=235056](http://go.microsoft.com/fwlink/p/?LinkId=235056)。</span><span class="sxs-lookup"><span data-stu-id="95f66-106">Using your Microsoft account, log into the portal at [http://go.microsoft.com/fwlink/p/?LinkId=235056](http://go.microsoft.com/fwlink/p/?LinkId=235056).</span></span>  
  
2.  <span data-ttu-id="95f66-107">建立 Northwind 的合作夥伴。</span><span class="sxs-lookup"><span data-stu-id="95f66-107">Create a partner for Northwind.</span></span> <span data-ttu-id="95f66-108">請依照下列步驟[夥伴和設定檔](http://msdn.microsoft.com/library/windowsazure/hh689791)建立夥伴。</span><span class="sxs-lookup"><span data-stu-id="95f66-108">Follow the steps at [Partners and Profiles](http://msdn.microsoft.com/library/windowsazure/hh689791) to create a partner.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="95f66-109">將標示為受管理夥伴此夥伴。</span><span class="sxs-lookup"><span data-stu-id="95f66-109">Mark this partner as the managed partner.</span></span>  
  
3.  <span data-ttu-id="95f66-110">重複步驟，建立 contoso 交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="95f66-110">Repeat the steps to create a partner for Contoso.</span></span> <span data-ttu-id="95f66-111">***不這麼做***標示為受管理夥伴此夥伴。</span><span class="sxs-lookup"><span data-stu-id="95f66-111">***Do not*** mark this partner as a managed partner.</span></span>  
  
### <a name="to-create-an-agreement"></a><span data-ttu-id="95f66-112">建立協議</span><span class="sxs-lookup"><span data-stu-id="95f66-112">To create an agreement</span></span>  
  
1.  <span data-ttu-id="95f66-113">在入口網站的首頁上，按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="95f66-113">In the portal home page, click **Agreements**.</span></span>  
  
2.  <span data-ttu-id="95f66-114">在**協議**頁面上，按一下**X12**索引標籤上，如果您已不在該索引標籤上。然後按一下 **建立協議**。</span><span class="sxs-lookup"><span data-stu-id="95f66-114">On the **Agreements** page, click the **X12** tab if you are not already on that tab. Then click **Create Agreement**.</span></span>  
  
3.  <span data-ttu-id="95f66-115">在**新協議**頁面上，輸入下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="95f66-115">In the **New Agreement** page, enter the following details:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="95f66-116">**欄位**</span><span class="sxs-lookup"><span data-stu-id="95f66-116">**Field**</span></span>|<span data-ttu-id="95f66-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="95f66-117">**Description**</span></span>|  
    |<span data-ttu-id="95f66-118">名稱</span><span class="sxs-lookup"><span data-stu-id="95f66-118">Name</span></span>|<span data-ttu-id="95f66-119">輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="95f66-119">Enter a name for the agreement.</span></span> <span data-ttu-id="95f66-120">此教學課程中，將名稱指定為`DemoAgreement`。</span><span class="sxs-lookup"><span data-stu-id="95f66-120">For this tutorial, specify the name as `DemoAgreement`.</span></span><br /><br /> <span data-ttu-id="95f66-121">**注意：** 這是必要欄位。</span><span class="sxs-lookup"><span data-stu-id="95f66-121">**Note:** This is a mandatory field.</span></span> <span data-ttu-id="95f66-122">協議的名稱必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="95f66-122">The name for the agreement must be unique.</span></span>|  
    |<span data-ttu-id="95f66-123">Description</span><span class="sxs-lookup"><span data-stu-id="95f66-123">Description</span></span>|<span data-ttu-id="95f66-124">輸入附註或針對協議的描述。</span><span class="sxs-lookup"><span data-stu-id="95f66-124">Enter notes or a description for the agreement.</span></span>|  
    |<span data-ttu-id="95f66-125">夥伴 1 設定檔 (managed)</span><span class="sxs-lookup"><span data-stu-id="95f66-125">Partner 1 Profile (managed)</span></span>|<span data-ttu-id="95f66-126">選取受管理的夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="95f66-126">Select the managed partner for the agreement.</span></span> <span data-ttu-id="95f66-127">受管理的夥伴是由服務提供者管理，而且合約部署期間為該合作夥伴部署管線。</span><span class="sxs-lookup"><span data-stu-id="95f66-127">A managed partner is a partner managed by the service provider and the pipelines are deployed for that partner during agreement deployment.</span></span> <span data-ttu-id="95f66-128">企業夥伴未標示為受管理夥伴時，服務提供者所管理的夥伴一般是設定為受管理夥伴。</span><span class="sxs-lookup"><span data-stu-id="95f66-128">Typically partners managed by service provider are configured as a managed partner while the enterprise partners are not marked as managed partners.</span></span><br /><br /> <span data-ttu-id="95f66-129">**注意：** 此教學課程中，受管理的夥伴是**Northwind**。</span><span class="sxs-lookup"><span data-stu-id="95f66-129">**Note:** For this tutorial, the managed partner is **Northwind**.</span></span><br /><br /> <span data-ttu-id="95f66-130">**注意：** 的預設設定檔會顯示在 [設定檔] 欄位。</span><span class="sxs-lookup"><span data-stu-id="95f66-130">**Note:** The default profile is displayed in the Profile field.</span></span> <span data-ttu-id="95f66-131">選擇所需的設定檔已設定為夥伴。</span><span class="sxs-lookup"><span data-stu-id="95f66-131">Choose the desired profile which has been configured for the partner.</span></span>|  
    |<span data-ttu-id="95f66-132">2 的夥伴設定檔</span><span class="sxs-lookup"><span data-stu-id="95f66-132">Partner 2 Profile</span></span>|<span data-ttu-id="95f66-133">選取的夥伴協議 （使用者不受管理的夥伴）。</span><span class="sxs-lookup"><span data-stu-id="95f66-133">Select the partner for the agreement (who is not a managed partner).</span></span><br /><br /> <span data-ttu-id="95f66-134">**注意：** 的預設設定檔會顯示在 [設定檔] 欄位。</span><span class="sxs-lookup"><span data-stu-id="95f66-134">**Note:** The default profile is displayed in the Profile field.</span></span> <span data-ttu-id="95f66-135">選擇所需的設定檔已設定為夥伴。</span><span class="sxs-lookup"><span data-stu-id="95f66-135">Choose the desired profile which has been configured for the partner.</span></span>|  
  
     <span data-ttu-id="95f66-136">**身分識別**</span><span class="sxs-lookup"><span data-stu-id="95f66-136">**Identities**</span></span>  
  
    |<span data-ttu-id="95f66-137">**欄位**</span><span class="sxs-lookup"><span data-stu-id="95f66-137">**Field**</span></span>|<span data-ttu-id="95f66-138">**說明**</span><span class="sxs-lookup"><span data-stu-id="95f66-138">**Description**</span></span>|  
    |---------------|---------------------|  
    |<span data-ttu-id="95f66-139">1 合作夥伴 ID 限定詞</span><span class="sxs-lookup"><span data-stu-id="95f66-139">Partner 1 ID Qualifier</span></span>|<span data-ttu-id="95f66-140">提供驗證限定詞，來為交易夥伴提供唯一的商務識別。</span><span class="sxs-lookup"><span data-stu-id="95f66-140">Select an authenticating qualifier that provides unique business identities to the trading partners.</span></span> <span data-ttu-id="95f66-141">此教學課程中，選取**ZZ 使用者相互定義**。</span><span class="sxs-lookup"><span data-stu-id="95f66-141">For this tutorial, select **ZZ-Mutually Defined**.</span></span>|  
    |<span data-ttu-id="95f66-142">值</span><span class="sxs-lookup"><span data-stu-id="95f66-142">Value</span></span>|<span data-ttu-id="95f66-143">輸入`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="95f66-143">Enter `Northwind`.</span></span>|  
    |<span data-ttu-id="95f66-144">2 合作夥伴 ID 限定詞</span><span class="sxs-lookup"><span data-stu-id="95f66-144">Partner 2 ID Qualifier</span></span>|<span data-ttu-id="95f66-145">提供驗證限定詞，來為交易夥伴提供唯一的商務識別。</span><span class="sxs-lookup"><span data-stu-id="95f66-145">Select an authenticating qualifier that provides unique business identities to the trading partners.</span></span> <span data-ttu-id="95f66-146">此教學課程中，選取**ZZ 使用者相互定義**。</span><span class="sxs-lookup"><span data-stu-id="95f66-146">For this tutorial, select **ZZ-Mutually Defined**.</span></span>|  
    |<span data-ttu-id="95f66-147">值</span><span class="sxs-lookup"><span data-stu-id="95f66-147">Value</span></span>|<span data-ttu-id="95f66-148">輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="95f66-148">Enter `Contoso`.</span></span>|  
  
     <span data-ttu-id="95f66-149">**追蹤**</span><span class="sxs-lookup"><span data-stu-id="95f66-149">**Tracking**</span></span>  
  
    |<span data-ttu-id="95f66-150">**欄位**</span><span class="sxs-lookup"><span data-stu-id="95f66-150">**Field**</span></span>|<span data-ttu-id="95f66-151">**說明**</span><span class="sxs-lookup"><span data-stu-id="95f66-151">**Description**</span></span>|  
    |---------------|---------------------|  
    |<span data-ttu-id="95f66-152">追蹤傳送端訊息屬性</span><span class="sxs-lookup"><span data-stu-id="95f66-152">Track Send side message properties</span></span>|<span data-ttu-id="95f66-153">勾選這 EDI 訊息傳送到夥伴時儲存訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="95f66-153">Check this to store the message properties when the EDI message is sent to the partner.</span></span> <span data-ttu-id="95f66-154">一旦儲存之後，您可以查詢此資料，即可**追蹤**從在 Azure BizTalk 入口網站的左窗格。</span><span class="sxs-lookup"><span data-stu-id="95f66-154">Once stored, you can query this data by clicking **Tracking** from the left pane on the Azure BizTalk Portal.</span></span><br /><br /> <span data-ttu-id="95f66-155">啟用時，您可以藉由檢查也儲存訊息主體**追蹤傳送端訊息內文**。</span><span class="sxs-lookup"><span data-stu-id="95f66-155">When enabled, you can also store the message body by checking **Track Send side message body**.</span></span>|  
    |<span data-ttu-id="95f66-156">追蹤接收端訊息屬性</span><span class="sxs-lookup"><span data-stu-id="95f66-156">Track Receive side message properties</span></span>|<span data-ttu-id="95f66-157">勾選這從夥伴接收 EDI 訊息時儲存訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="95f66-157">Check this to store the message properties when the EDI message is received from a partner.</span></span> <span data-ttu-id="95f66-158">一旦儲存之後，您可以查詢此資料，即可**追蹤**從在 Azure BizTalk 入口網站的左窗格。</span><span class="sxs-lookup"><span data-stu-id="95f66-158">Once stored, you can query this data by clicking **Tracking** from the left pane on the Azure BizTalk Portal.</span></span><br /><br /> <span data-ttu-id="95f66-159">啟用時，您可以藉由檢查也儲存訊息主體**追蹤接收端訊息內文**。</span><span class="sxs-lookup"><span data-stu-id="95f66-159">When enabled, you can also store the message body by checking **Track Receive side message body**.</span></span>|  
  
4.  <span data-ttu-id="95f66-160">按一下 **[繼續]**。</span><span class="sxs-lookup"><span data-stu-id="95f66-160">Click **Continue**.</span></span>  
  
     <span data-ttu-id="95f66-161">按一下**繼續**加入兩個新的索引標籤，一個用於接收設定，而另一個用於傳送設定。</span><span class="sxs-lookup"><span data-stu-id="95f66-161">Clicking **Continue** adds two new tabs, one for receive settings and the other for send settings.</span></span> <span data-ttu-id="95f66-162">每個索引標籤是一個用於接收訊息，另一個用於傳送訊息的兩個夥伴之間的單向協議。</span><span class="sxs-lookup"><span data-stu-id="95f66-162">Each tab is for a one-way agreement between the two partners, one for receiving messages and the other for sending messages.</span></span>  
  
5.  <span data-ttu-id="95f66-163">指定的接收設定。</span><span class="sxs-lookup"><span data-stu-id="95f66-163">Specify the receive settings.</span></span>  
  
    1.  <span data-ttu-id="95f66-164">在**傳輸**頁面上，設定**傳輸類型**為 HTTP。</span><span class="sxs-lookup"><span data-stu-id="95f66-164">On the **Transport** page, set the **Transport type** to HTTP.</span></span>  
  
         <span data-ttu-id="95f66-165">**端點**欄位會顯示 URL，Contoso 必須將 X12 銷售訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="95f66-165">The **Endpoint** field shows the URL to which Contoso must send the X12 sales order message.</span></span>  
  
    2.  <span data-ttu-id="95f66-166">在**通訊協定**頁面上，指定下列值。</span><span class="sxs-lookup"><span data-stu-id="95f66-166">On the **Protocol** page, specify the following values.</span></span>  
  
        1.  <span data-ttu-id="95f66-167">如有需要，請為 ISA1、 ISA2、 ISA3 和 ISA4 中指定值。</span><span class="sxs-lookup"><span data-stu-id="95f66-167">If required, specify values for ISA1, ISA2, ISA3, and ISA4.</span></span>  
  
        2.  <span data-ttu-id="95f66-168">在下**通知**，選取**預期 TA1**和**997 預期**如果您想要接收的回應中產生技術性和功能性通知訊息。</span><span class="sxs-lookup"><span data-stu-id="95f66-168">Under **Acknowledgements**, select **TA1 expected** and **997 expected** if you want to generate technical and functional acknowledgements in response for receiving the message.</span></span>  
  
        3.  <span data-ttu-id="95f66-169">在下**結構描述**，按一下 **上傳**按鈕，然後上傳**X12 840 結構描述**(從您下載[http://go.microsoft.com/fwlink/p/?LinkId = 235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)) 和**SalesOrder**結構描述 (您在建立[建立 EDI 專案中的結構描述](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateSchema))。</span><span class="sxs-lookup"><span data-stu-id="95f66-169">Under **Schemas**, click the **Upload** button and upload the **X12 840 schema** (you downloaded from [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)) and the **SalesOrder** schema (you created in [To create a schema within the EDI project](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateSchema)).</span></span>  
  
             <span data-ttu-id="95f66-170">設定下列屬性下的**結構描述**> 一節。</span><span class="sxs-lookup"><span data-stu-id="95f66-170">Set the following properties under the **Schemas** section.</span></span>  
  
            |||  
            |-|-|  
            |<span data-ttu-id="95f66-171">Version</span><span class="sxs-lookup"><span data-stu-id="95f66-171">Version</span></span>|<span data-ttu-id="95f66-172">00401</span><span class="sxs-lookup"><span data-stu-id="95f66-172">00401</span></span>|  
            |<span data-ttu-id="95f66-173">交易類型 (ST1)</span><span class="sxs-lookup"><span data-stu-id="95f66-173">Transaction Type (ST1)</span></span>|<span data-ttu-id="95f66-174">840</span><span class="sxs-lookup"><span data-stu-id="95f66-174">840</span></span>|  
            |<span data-ttu-id="95f66-175">結構描述</span><span class="sxs-lookup"><span data-stu-id="95f66-175">Schema</span></span>|<span data-ttu-id="95f66-176">/ X12_00401_840.xsd</span><span class="sxs-lookup"><span data-stu-id="95f66-176">/X12_00401_840.xsd</span></span>|  
  
    3.  <span data-ttu-id="95f66-177">在**轉換**頁面上上, 傳您在建立轉換[建立 EDI 專案中的轉換](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateTrfm)。</span><span class="sxs-lookup"><span data-stu-id="95f66-177">On the **Transform** page, upload the transform you created in [To create a transform within the EDI project](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateTrfm).</span></span>  
  
         <span data-ttu-id="95f66-178">在下**選擇您想要當做此協議的一部分執行的對應**，選擇 **/X12_00401_840.xsd**如**結構描述**和 **/EDI840TOSALESORDER。TRFM**如**轉換檔名稱**。</span><span class="sxs-lookup"><span data-stu-id="95f66-178">Under **Choose the maps you want to execute as part of this agreement**, choose **/X12_00401_840.xsd** for **Schemas** and **/EDI840TOSALESORDER.TRFM** for **Transform file name**.</span></span>  
  
    4.  <span data-ttu-id="95f66-179">在**路由**頁面上，選取**路由至服務匯流排佇列**並提供的佇列傳送訊息的相對位址。</span><span class="sxs-lookup"><span data-stu-id="95f66-179">On the **Route** page, select **Route to Service Bus Queue** and provide the relative address of the queue to which the message is sent.</span></span> <span data-ttu-id="95f66-180">此教學課程中，指定相對位址，表示為`queueordersedi`使的完整 URL `https://<namespace>.servicebus.appfabriclabs.com/queueordersedi`。</span><span class="sxs-lookup"><span data-stu-id="95f66-180">For this tutorial, specify the relative address as `queueordersedi` so that the complete URL is `https://<namespace>.servicebus.appfabriclabs.com/queueordersedi`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="95f66-181">此教學課程未涵蓋失敗的訊息的傳送目標端點您的案例中訊息暫停設定所指定。</span><span class="sxs-lookup"><span data-stu-id="95f66-181">This tutorial does not cover the scenario where a failed message is sent to the endpoint you specify in the Message Suspension Settings.</span></span> <span data-ttu-id="95f66-182">不過，才能順利部署協議，您必須提供值，此設定。</span><span class="sxs-lookup"><span data-stu-id="95f66-182">However, for successful deployment of the agreement, you must provide a value for this setting.</span></span> <span data-ttu-id="95f66-183">您可以輸入非空白值。</span><span class="sxs-lookup"><span data-stu-id="95f66-183">You can enter a non-empty value.</span></span>  
  
6.  <span data-ttu-id="95f66-184">指定傳送設定。</span><span class="sxs-lookup"><span data-stu-id="95f66-184">Specify the send settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="95f66-185">對於此教學課程中所述的案例，您不需要任何協議的傳送端設定。</span><span class="sxs-lookup"><span data-stu-id="95f66-185">For the scenario described in this tutorial, you don’t need any send-side configuration for the agreement.</span></span> <span data-ttu-id="95f66-186">不過，協議無法部署而不指定傳送設定 中，即使它們是空的值。</span><span class="sxs-lookup"><span data-stu-id="95f66-186">However, an agreement cannot be deployed without specifying the send settings, even if they are dummy values.</span></span> <span data-ttu-id="95f66-187">此外，在**傳送設定**索引標籤上，您不需要提供的任何空值**輸入 URI**，**轉換**，和**批次處理**。</span><span class="sxs-lookup"><span data-stu-id="95f66-187">Also, On the **Send Settings** tab, you don’t need to provide any dummy values for **Inbound URI**, **Transform**, and **Batching**.</span></span>  
  
    1.  <span data-ttu-id="95f66-188">上**通訊協定**頁面的 **結構描述**，按一下**上傳**按鈕，然後上傳結構描述 x12 840 訊息。</span><span class="sxs-lookup"><span data-stu-id="95f66-188">On the **Protocol** page, under **Schemas**, click the **Upload** button and upload the schema for the X12 840 message.</span></span>  
  
         <span data-ttu-id="95f66-189">設定**版本**至**00401**，**交易類型**至**840**，和**結構描述**至**X12_00401_840**。</span><span class="sxs-lookup"><span data-stu-id="95f66-189">Set the **Version** to **00401**, **Transaction Type** to **840**, and **Schema** to **X12_00401_840**.</span></span>  
  
    2.  <span data-ttu-id="95f66-190">在**傳輸**頁面上，指定在回應訊息或通知會傳送至夥伴的端點。</span><span class="sxs-lookup"><span data-stu-id="95f66-190">On the **Transport** page, specify the endpoints where the response messages or acknowledgements will be sent to the partners.</span></span> <span data-ttu-id="95f66-191">您必須指定的端點，每個已成功處理的訊息，以及取得因處理失敗而擱置的訊息。</span><span class="sxs-lookup"><span data-stu-id="95f66-191">You must specify an endpoint each for the messages that are processed successfully as well as the messages that get suspended due to a failure in processing.</span></span>  
  
7.  <span data-ttu-id="95f66-192">按一下**部署協議**部署合約。</span><span class="sxs-lookup"><span data-stu-id="95f66-192">Click **Deploy Agreement** to deploy the agreement.</span></span> <span data-ttu-id="95f66-193">協議現在部署於 URL 中原先顯示**傳輸**頁面**接收設定** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="95f66-193">The agreement is now deployed at the URL that was displayed in the **Transport** page of the **Receive Settings** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f66-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95f66-194">See Also</span></span>  
 [<span data-ttu-id="95f66-195">教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="95f66-195">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)