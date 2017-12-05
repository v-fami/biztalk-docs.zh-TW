---
title: "如何： 選取 使用商務規則原則路線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f6373a8-d9d6-46c6-95e3-f62dd33c342a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 521b3768251cfcd31defe271a21d4b2d0bc771e6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-select-an-itinerary-using-a-business-rules-policy"></a><span data-ttu-id="d4d01-102">如何： 選取 使用商務規則原則路線</span><span class="sxs-lookup"><span data-stu-id="d4d01-102">How to: Select an Itinerary Using a Business Rules Policy</span></span>
## <a name="goal"></a><span data-ttu-id="d4d01-103">目標</span><span class="sxs-lookup"><span data-stu-id="d4d01-103">Goal</span></span>  
 <span data-ttu-id="d4d01-104">本節示範如何建立可用來選取行程已接收訊息的內容為基礎的商務規則，以及如何設定路線選取器管線元件內泛型路線上手呼叫這些規則。</span><span class="sxs-lookup"><span data-stu-id="d4d01-104">This section demonstrates how to create business rules that can be used to select an itinerary based on the content of a received message and how to configure the Itinerary Selector pipeline component within a generic itinerary on-ramp to call these rules.</span></span> <span data-ttu-id="d4d01-105">本章節描述中的訊息會路由傳送方式會不同，客戶所在的區域為基礎的商務案例。</span><span class="sxs-lookup"><span data-stu-id="d4d01-105">This section describes a business scenario in which messages are routed differently, based on the region in which the customer resides.</span></span>  
  
 <span data-ttu-id="d4d01-106">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d4d01-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="d4d01-107">模型西部和美國東部客戶 Global 銀行畫分之行程。</span><span class="sxs-lookup"><span data-stu-id="d4d01-107">Model itineraries for the Western and Eastern divisions of customer Global Bank.</span></span>  
  
-   <span data-ttu-id="d4d01-108">建立商務規則原則將用來選取行程處理要求。</span><span class="sxs-lookup"><span data-stu-id="d4d01-108">Create business rules policies that will be used to select an itinerary for processing request.</span></span>  
  
-   <span data-ttu-id="d4d01-109">設定要用來選取適當的行程的商務規則原則路線選取器管線元件。</span><span class="sxs-lookup"><span data-stu-id="d4d01-109">Configure the Itinerary Selector pipeline component to use a business rules policy to select the appropriate itinerary.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d4d01-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="d4d01-110">Prerequisites</span></span>  
 <span data-ttu-id="d4d01-111">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d01-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="d4d01-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="d4d01-112">Before You Begin</span></span>  
 <span data-ttu-id="d4d01-113">在執行本使用說明主題中稍後的步驟之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="d4d01-113">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="d4d01-114">建立 GlobalBank 西測試訊息。</span><span class="sxs-lookup"><span data-stu-id="d4d01-114">Create the GlobalBank West test message.</span></span>  
  
-   <span data-ttu-id="d4d01-115">建立 GlobalBank 東部測試訊息。</span><span class="sxs-lookup"><span data-stu-id="d4d01-115">Create the GlobalBank East test message.</span></span>  
  
 <span data-ttu-id="d4d01-116">下列程序說明如何執行每一種。</span><span class="sxs-lookup"><span data-stu-id="d4d01-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-the-globalbank-west-test-message"></a><span data-ttu-id="d4d01-117">若要建立 GlobalBank 西測試訊息</span><span class="sxs-lookup"><span data-stu-id="d4d01-117">To create the GlobalBank West test message</span></span>  
  
1.  <span data-ttu-id="d4d01-118">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="d4d01-118">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="d4d01-119">建立一份 NAOrderDoc.xml，，然後複製 West.xml。</span><span class="sxs-lookup"><span data-stu-id="d4d01-119">Create a copy of NAOrderDoc.xml, and then name the copy West.xml.</span></span>  
  
3.  <span data-ttu-id="d4d01-120">在 [記事本] 開啟 West.xml，並將值**customerName**元素**GlobalBankWest**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-120">In Notepad, open West.xml, and then change the value of the **customerName** element to **GlobalBankWest**.</span></span>  
  
4.  <span data-ttu-id="d4d01-121">儲存 West.xml 為 utf-8，，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="d4d01-121">Save West.xml as UTF-8, and then close Notepad.</span></span>  
  
#### <a name="to-create-the-globalbank-east-test-message"></a><span data-ttu-id="d4d01-122">若要建立 GlobalBank 東部測試訊息</span><span class="sxs-lookup"><span data-stu-id="d4d01-122">To create the GlobalBank East test message</span></span>  
  
1.  <span data-ttu-id="d4d01-123">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="d4d01-123">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="d4d01-124">建立一份 NAOrderDoc.xml，，然後複製 East.xml。</span><span class="sxs-lookup"><span data-stu-id="d4d01-124">Create a copy of NAOrderDoc.xml, and then name the copy East.xml.</span></span>  
  
3.  <span data-ttu-id="d4d01-125">在 [記事本] 開啟 East.xml，並將值**customerName**元素**GlobalBankEast**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-125">In Notepad, open East.xml, and then change the value of the **customerName** element to **GlobalBankEast**.</span></span>  
  
4.  <span data-ttu-id="d4d01-126">儲存 East.xml 為 utf-8，，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="d4d01-126">Save East.xml as UTF-8, and then close Notepad.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="d4d01-127">步驟</span><span class="sxs-lookup"><span data-stu-id="d4d01-127">Steps</span></span>  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a><span data-ttu-id="d4d01-128">若要建立商務規則引擎 (BRE) 原則，選取 使用自訂訊息屬性路線</span><span class="sxs-lookup"><span data-stu-id="d4d01-128">To create a Business Rules Engine (BRE) policy to select an itinerary using custom message properties</span></span>  
  
1.  <span data-ttu-id="d4d01-129">按一下**啟動**在工作列上，指向**所有程式**，指向  **BizTalk Server**，然後按一下 **商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-129">Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="d4d01-130">在 原則總管 中，以滑鼠右鍵按一下**原則**，然後按一下 **新增原則**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-130">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="d4d01-131">命名原則**ResolveItineraryBasedOnCustomer**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-131">Name the policy **ResolveItineraryBasedOnCustomer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-132">此說明主題使用與本主題中所建立的相同商務規則原則和旅[How to： 將交換分割，並將產生的訊息路由至多個檔案的位置使用不同旅](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d01-132">This How-to topic uses the same business rules policy and itineraries as those created in the topic [How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md).</span></span> <span data-ttu-id="d4d01-133">如果您已經完成該區段，您可以跳至 「 程序，建立並設定 ESB 上手"本主題稍後的。</span><span class="sxs-lookup"><span data-stu-id="d4d01-133">If you have already completed that section, you can skip to the procedure, "To create and configure an ESB on-ramp" later in this topic.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a><span data-ttu-id="d4d01-134">若要加入客戶 GlobalBank 西的選取範圍規則</span><span class="sxs-lookup"><span data-stu-id="d4d01-134">To add a selection rule for customer GlobalBank West</span></span>  
  
1.  <span data-ttu-id="d4d01-135">在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增規則**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-135">In the **ResolveItineraryBasedOnCustomer** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="d4d01-136">命名規則**SetGlobalBankWestItinerary**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-136">Name the rule **SetGlobalBankWestItinerary**.</span></span>  
  
2.  <span data-ttu-id="d4d01-137">在 事實總管 中，按一下  **XML 結構描述**索引標籤上，以滑鼠右鍵按一下**結構描述**，然後按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-137">In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="d4d01-138">在**結構描述檔案**對話方塊中，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。選取 DynamicResolution.Schemas **NAOrderDoc.xsd**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-138">In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select **NAOrderDoc.xsd**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-139">這是定義用來建立將用於測試的西和東訊息 NAOrderDoc.xml 訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d4d01-139">This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.</span></span>  
  
4.  <span data-ttu-id="d4d01-140">在 事實總管 中，按一下  **NAOrderDoc.xsd**，按一下 **文件類型**屬性 屬性 窗格中，然後輸入**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="d4d01-140">In Facts Explorer, click **NAOrderDoc.xsd**, click the **Document Type** property in the Properties pane, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-141">這是結構描述的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4d01-141">This is the fully qualified name of the schema.</span></span>  
  
5.  <span data-ttu-id="d4d01-142">在 [事實總管] 中，展開**NAOrderDoc.xsd**，然後展開**OrderDoc**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-142">In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.</span></span>  
  
6.  <span data-ttu-id="d4d01-143">在 規則 視窗中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下 **等於**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-143">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
7.  <span data-ttu-id="d4d01-144">從 [事實總管] 中，拖曳**customerName**元素**引數 1**節點下的**條件**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-144">From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.</span></span>  
  
8.  <span data-ttu-id="d4d01-145">按一下**引數 2**  節點，然後輸入**GlobalBankWest**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-145">Click the **argument2** node, and then type **GlobalBankWest**.</span></span>  
  
9. <span data-ttu-id="d4d01-146">在 [事實總管] 中，按一下 [**詞彙**] 索引標籤。展開**ESB。行程**詞彙中，展開**1.1 版**，然後將拖曳**設定路線名稱**定義，以**動作**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-146">In Facts Explorer, click the **Vocabularies** tab. Expand the **ESB.Itinerary** vocabulary, expand **Version 1.1**, and then drag the **Set Itinerary Name** definition to **Actions**.</span></span>  
  
10. <span data-ttu-id="d4d01-147">按一下**\<空字串\>**，然後輸入**GlobalBankWestItinerary**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-147">Click **\<empty string\>**, and then type **GlobalBankWestItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-148">稍後在本使用說明主題中，您會根據 GlobalBank 西這個行程建立來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d4d01-148">Later in this How-to topic, you will create this itinerary to process messages from GlobalBank West.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a><span data-ttu-id="d4d01-149">加入客戶 GlobalBank 東部選取規則</span><span class="sxs-lookup"><span data-stu-id="d4d01-149">To add a selection rule for Customer GlobalBank East</span></span>  
  
1.  <span data-ttu-id="d4d01-150">在 原則總管 中，以滑鼠右鍵按一下**SetGlobalBankWestItinerary**規則，，然後按一下 **複製**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-150">In Policy Explorer, right-click the **SetGlobalBankWestItinerary** rule, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="d4d01-151">以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **貼上**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-151">Right-click **Version 1.0 (not saved)**, and then click **Paste**.</span></span>  
  
3.  <span data-ttu-id="d4d01-152">在**新規則的名稱**] 對話方塊中，輸入**SetGlobalBankEastItinerary**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-152">In the **New Rule Name** dialog box, type **SetGlobalBankEastItinerary**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="d4d01-153">在 原則總管 中，按一下  **SetGlobalBankEastItinerary**規則。</span><span class="sxs-lookup"><span data-stu-id="d4d01-153">In Policy Explorer, click the **SetGlobalBankEastItinerary** rule.</span></span>  
  
5.  <span data-ttu-id="d4d01-154">在**條件**區段中，以滑鼠右鍵按一下**GlobalBankWest**，然後按一下 **重設引數**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-154">In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.</span></span>  
  
6.  <span data-ttu-id="d4d01-155">按一下**引數 2**，然後輸入**GlobalBankEast**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-155">Click **argument2**, and then type **GlobalBankEast**.</span></span>  
  
7.  <span data-ttu-id="d4d01-156">在**動作**區段中，以滑鼠右鍵按一下**GlobalBankWestItinerary**，然後按一下 **重設引數**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-156">In the **Actions** section, right-click **GlobalBankWestItinerary**, and then click **Reset argument**.</span></span>  
  
8.  <span data-ttu-id="d4d01-157">按一下**\<空字串\>** ，然後輸入**GlobalBankEastItinerary**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-157">Click **\<empty string\>** and then type **GlobalBankEastItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-158">稍後的 「 如何 」 主題中，您將從 GlobalBank 東這個行程建立來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d4d01-158">Later in the How-to topic, you will create this itinerary to process messages from GlobalBank East.</span></span>  
  
#### <a name="to-publish-and-deploy-the-policy"></a><span data-ttu-id="d4d01-159">若要發行和部署原則</span><span class="sxs-lookup"><span data-stu-id="d4d01-159">To publish and deploy the policy</span></span>  
  
1.  <span data-ttu-id="d4d01-160">在 原則總管 中，在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **發行**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-160">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="d4d01-161">在 原則總管 中，在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-161">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model-for-globalbank-west-messages"></a><span data-ttu-id="d4d01-162">若要建立 GlobalBank 西訊息 ESB 路線網域特定領域語言 (DSL) 模型</span><span class="sxs-lookup"><span data-stu-id="d4d01-162">To create an ESB itinerary domain-specific language (DSL) model for GlobalBank West messages</span></span>  
  
1.  <span data-ttu-id="d4d01-163">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="d4d01-163">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="d4d01-164">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-164">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="d4d01-165">在**加入新項目**對話方塊，在 [範本] 窗格中，按一下**ItineraryDsl**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-165">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="d4d01-166">在**名稱**方塊中，輸入**GlobalBankWestItinerary**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-166">In the **Name** box, type **GlobalBankWestItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a><span data-ttu-id="d4d01-167">若要設定 GlobalBank 西路線的屬性</span><span class="sxs-lookup"><span data-stu-id="d4d01-167">To configure the properties of the GlobalBank West itinerary</span></span>  
  
1.  <span data-ttu-id="d4d01-168">在 Visual Studio 中，按一下設計介面的**GlobalBankWestItinerary.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-168">In Visual Studio, click the design surface of **GlobalBankWestItinerary.itinerary**.</span></span> <span data-ttu-id="d4d01-169">在**GlobalBankWestItinerary**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-169">In the **GlobalBankWestItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-170">在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-170">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-171">按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="d4d01-171">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="d4d01-172">在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。</span><span class="sxs-lookup"><span data-stu-id="d4d01-172">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="d4d01-173">在**路線狀態**下拉式清單中，按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-173">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-174">這個步驟可讓您匯出至中央儲存機制; 路線選取並從這個儲存機制，在訊息接收時附加行程。</span><span class="sxs-lookup"><span data-stu-id="d4d01-174">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository upon message reception.</span></span> <span data-ttu-id="d4d01-175">您稍後將設定路線選取器管線元件使用 「 商務規則引擎解析程式 」 (BRI) 評估內送的訊息，並從這個儲存機制中選取適當的路線。</span><span class="sxs-lookup"><span data-stu-id="d4d01-175">You will later configure the Itinerary Selector pipeline component to use the Business Rules Engine resolver (BRI) to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="d4d01-176">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="d4d01-176">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="d4d01-177">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-177">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="d4d01-178">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-178">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-179">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-179">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-180">在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-180">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="d4d01-181">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-181">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="d4d01-182">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-182">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="d4d01-183">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**ReceiveNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-183">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="d4d01-184">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-184">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-185">按一下**名稱**屬性，，然後輸入**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-185">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-186">在**Extender**下拉式清單中，按一下 **匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-186">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="d4d01-187">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-187">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="d4d01-188">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-188">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="d4d01-189">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-189">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="d4d01-190">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-190">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-191">按一下**名稱**屬性，，然後輸入**RouteMessage**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-191">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-192">在**路線服務的擴充項**下拉式清單中，按一下 **匝道路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-192">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="d4d01-193">在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-193">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="d4d01-194">以滑鼠右鍵按一下**解析程式**集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-194">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="d4d01-195">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-195">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-196">按一下**名稱**屬性，，然後輸入**StaticResolver**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-196">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-197">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-197">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="d4d01-198">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-198">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="d4d01-199">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\West%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-199">Click the **Transport Location** property, and then type **C:\HowTos\Out\West%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="d4d01-200">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-200">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="d4d01-201">拖曳連接**ReceiveNAOrder**模型項目的**RouteMessage**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-201">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="d4d01-202">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-202">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="d4d01-203">拖曳連接**RouteMessage**模型項目的**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-203">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="d4d01-204">將模型匯出至路線資料庫</span><span class="sxs-lookup"><span data-stu-id="d4d01-204">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="d4d01-205">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**GlobalBankWestItinerary**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-205">In Visual Studio, right-click the design surface of the **GlobalBankWestItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-206">路線已經匯出成路線的資料庫，現在可供路線選取器元件。</span><span class="sxs-lookup"><span data-stu-id="d4d01-206">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="d4d01-207">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="d4d01-207">Save all project artifacts.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a><span data-ttu-id="d4d01-208">若要建立 GlobalBank 東部訊息 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="d4d01-208">To create an ESB itinerary DSL model for GlobalBank East message</span></span>  
  
1.  <span data-ttu-id="d4d01-209">在 Visual Studio 中開啟 C:\HowTos\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="d4d01-209">In Visual Studio, open C:\HowTos\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="d4d01-210">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-210">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="d4d01-211">在**加入新項目**對話方塊，在 [範本] 窗格中，按一下**ItineraryDsl**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-211">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="d4d01-212">在**名稱**方塊中，輸入**GlobalBankEastItinerary**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-212">In the **Name** box, type **GlobalBankEastItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a><span data-ttu-id="d4d01-213">若要設定的 GlobalBank 東部路線屬性</span><span class="sxs-lookup"><span data-stu-id="d4d01-213">To configure the properties of the GlobalBank East itinerary</span></span>  
  
1.  <span data-ttu-id="d4d01-214">在 Visual Studio 中，按一下設計介面的**GlobalBankEastItinerary.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-214">In Visual Studio, click the design surface of **GlobalBankEastItinerary.itinerary**.</span></span> <span data-ttu-id="d4d01-215">在**GlobalBankEastItinerary**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-215">In the **GlobalBankEastItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-216">在**模型匯出工具**下拉式清單中，按一下 **資料庫路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-216">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-217">按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="d4d01-217">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="d4d01-218">在**連接屬性**對話方塊中，選擇裝載路線的儲存機制資料庫，SQL Server，，然後指定資料庫的名稱 (預設名稱是**EsbItineraryDb**)。</span><span class="sxs-lookup"><span data-stu-id="d4d01-218">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="d4d01-219">在**路線狀態**下拉式清單中，按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-219">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-220">這個步驟可讓您匯出至中央儲存機制; 路線可以選取和接收訊息時就會從這個儲存機制附加行程。</span><span class="sxs-lookup"><span data-stu-id="d4d01-220">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received.</span></span> <span data-ttu-id="d4d01-221">您稍後將設定要用於評估內送的訊息，並從這個儲存機制中選取適當的行程 BRI 解析程式路線選取器管線元件。</span><span class="sxs-lookup"><span data-stu-id="d4d01-221">You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="d4d01-222">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="d4d01-222">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="d4d01-223">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-223">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="d4d01-224">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-224">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-225">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-225">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-226">在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-226">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="d4d01-227">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-227">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="d4d01-228">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-228">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="d4d01-229">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**ReceiveNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-229">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="d4d01-230">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-230">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-231">按一下**名稱**屬性，，然後輸入**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-231">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-232">在**Extender**下拉式清單中，按一下 **匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-232">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="d4d01-233">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-233">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="d4d01-234">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-234">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="d4d01-235">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-235">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="d4d01-236">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-236">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-237">按一下**名稱**屬性，，然後輸入**RouteMessage**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-237">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-238">在**路線服務的擴充項**下拉式清單中，按一下 **匝道路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-238">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="d4d01-239">在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-239">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="d4d01-240">以滑鼠右鍵按一下**解析程式**集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-240">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="d4d01-241">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-241">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-242">按一下**名稱**屬性，，然後輸入**StaticResolver**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-242">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-243">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-243">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="d4d01-244">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-244">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="d4d01-245">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\East%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-245">Click the **Transport Location** property, and then type **C:\HowTos\Out\East%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="d4d01-246">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-246">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="d4d01-247">拖曳連接**ReceiveNAOrder**模型項目的**RouteMessage**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-247">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="d4d01-248">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-248">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="d4d01-249">拖曳連接**RouteMessage**模型項目的**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d4d01-249">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="d4d01-250">將模型匯出至路線資料庫</span><span class="sxs-lookup"><span data-stu-id="d4d01-250">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="d4d01-251">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**GlobalBankEastItinerary**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-251">In Visual Studio, right-click the design surface of the **GlobalBankEastItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-252">路線已經匯出成路線的資料庫，現在可供路線選取器元件。</span><span class="sxs-lookup"><span data-stu-id="d4d01-252">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="d4d01-253">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="d4d01-253">Save all project artifacts.</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="d4d01-254">若要建立及設定 ESB 上手</span><span class="sxs-lookup"><span data-stu-id="d4d01-254">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="d4d01-255">按一下**啟動**在工作列上，指向**所有程式**，指向  **BizTalk Server**，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-255">Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d4d01-256">在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，依序展開**應用程式**，然後展開**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-256">In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="d4d01-257">以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-257">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="d4d01-258">在**選取接收埠**對話方塊中，按一下  **OnRamp.Itinerary**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-258">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="d4d01-259">在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**OnRamp.Itinerary.HowTo**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-259">In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.HowTo**.</span></span>  
  
6.  <span data-ttu-id="d4d01-260">在**類型**下拉式清單中，按一下 **檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-260">In the **Type** drop-down list, click **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="d4d01-261">中**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\HowTos\DropFolder**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-261">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\HowTos\DropFolder**, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="d4d01-262">若要設定路線選取器管線元件</span><span class="sxs-lookup"><span data-stu-id="d4d01-262">To configure the Itinerary Selector pipeline component</span></span>  
  
1.  <span data-ttu-id="d4d01-263">在**接收位置屬性**對話方塊中，於**接收管線**下拉式清單中，按一下  **ItinerarySelectReceiveXml**，然後按一下省略符號按鈕 （...).</span><span class="sxs-lookup"><span data-stu-id="d4d01-263">In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, click **ItinerarySelectReceiveXml**, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="d4d01-264">使用**設定管線**對話方塊來設定下列**路線選取器**元件屬性：</span><span class="sxs-lookup"><span data-stu-id="d4d01-264">Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="d4d01-265">按一下**ItineraryFactKey**屬性，，然後輸入**Resolver.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-265">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="d4d01-266">按一下**ResolverConnectionString**屬性，，然後輸入**BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span><span class="sxs-lookup"><span data-stu-id="d4d01-266">Click the **ResolverConnectionString** property, and then type **BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span></span>  
  
    3.  <span data-ttu-id="d4d01-267">按一下**確定**關閉**設定管線** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4d01-267">Click **OK** to close the **Configure Pipeline** dialog box.</span></span>  
  
3.  <span data-ttu-id="d4d01-268">按一下**確定**關閉**接收位置屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4d01-268">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="d4d01-269">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-269">In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a><span data-ttu-id="d4d01-270">若要測試的計劃的選取器 」 和 「 商務規則</span><span class="sxs-lookup"><span data-stu-id="d4d01-270">To test the itinerary selector and business rules</span></span>  
  
1.  <span data-ttu-id="d4d01-271">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="d4d01-271">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="d4d01-272">複製 （不會移動） 到 DropFolder 資料夾 East.xml 和 West.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="d4d01-272">Copy (do not move) the files East.xml and West.xml to the DropFolder folder.</span></span>  
  
3.  <span data-ttu-id="d4d01-273">瀏覽至 C:\HowTos\Out。請確認 East%MessageID%.xml 和 West%MessageID%.xml 訊息已寫入目錄。</span><span class="sxs-lookup"><span data-stu-id="d4d01-273">Browse to C:\HowTos\Out. Verify that the East%MessageID%.xml and West%MessageID%.xml messages have been written to the directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d4d01-274">除了客戶元素的值相同，但使用不同的行程，根據路線選取器管線元件的解析度處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d4d01-274">Though identical except for the value of the customer element, the messages were processed using different itineraries, based on the resolution of the Itinerary Selector pipeline component.</span></span>  
  
4.  <span data-ttu-id="d4d01-275">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-275">In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Disable**.</span></span>  
  
5.  <span data-ttu-id="d4d01-276">之後**OnRamp.Itinerary.HowTo**接收位置已停用，以滑鼠右鍵按一下，，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-276">After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="d4d01-277">在**確認刪除接收位置**對話方塊中，按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="d4d01-277">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="d4d01-278">其他資源</span><span class="sxs-lookup"><span data-stu-id="d4d01-278">Additional Resources</span></span>  
 <span data-ttu-id="d4d01-279">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="d4d01-279">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="d4d01-280">如何：分割交換，並使用不同路線將產生的訊息路由至多個檔案位置</span><span class="sxs-lookup"><span data-stu-id="d4d01-280">How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries</span></span>](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
-   [<span data-ttu-id="d4d01-281">開發活動</span><span class="sxs-lookup"><span data-stu-id="d4d01-281">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="d4d01-282">安裝和執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="d4d01-282">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [<span data-ttu-id="d4d01-283">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="d4d01-283">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [<span data-ttu-id="d4d01-284">訊息路由模式</span><span class="sxs-lookup"><span data-stu-id="d4d01-284">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)