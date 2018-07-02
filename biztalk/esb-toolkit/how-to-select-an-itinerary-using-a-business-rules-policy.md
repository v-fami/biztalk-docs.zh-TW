---
title: 如何： 選取使用商務規則原則路線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f6373a8-d9d6-46c6-95e3-f62dd33c342a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12496da0de4057e96be0b714ad1af048ee6b8ef1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976959"
---
# <a name="how-to-select-an-itinerary-using-a-business-rules-policy"></a><span data-ttu-id="649be-102">如何： 選取使用商務規則原則路線</span><span class="sxs-lookup"><span data-stu-id="649be-102">How to: Select an Itinerary Using a Business Rules Policy</span></span>
## <a name="goal"></a><span data-ttu-id="649be-103">目標</span><span class="sxs-lookup"><span data-stu-id="649be-103">Goal</span></span>  
 <span data-ttu-id="649be-104">本節示範如何建立可用來選取路線接收訊息的內容為基礎的商務規則，以及如何設定路線選取器管線元件中泛型路線入口匝呼叫這些規則。</span><span class="sxs-lookup"><span data-stu-id="649be-104">This section demonstrates how to create business rules that can be used to select an itinerary based on the content of a received message and how to configure the Itinerary Selector pipeline component within a generic itinerary on-ramp to call these rules.</span></span> <span data-ttu-id="649be-105">本章節描述在其中訊息會路由傳送以不同的方式，客戶所在的區域為基礎的商務案例。</span><span class="sxs-lookup"><span data-stu-id="649be-105">This section describes a business scenario in which messages are routed differently, based on the region in which the customer resides.</span></span>  
  
 <span data-ttu-id="649be-106">在本使用說明主題中，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="649be-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="649be-107">模型的客戶 Global Bank 西部和美國東部部門的路線。</span><span class="sxs-lookup"><span data-stu-id="649be-107">Model itineraries for the Western and Eastern divisions of customer Global Bank.</span></span>  
  
-   <span data-ttu-id="649be-108">建立將用來選取路線處理要求的商務規則原則。</span><span class="sxs-lookup"><span data-stu-id="649be-108">Create business rules policies that will be used to select an itinerary for processing request.</span></span>  
  
-   <span data-ttu-id="649be-109">設定路線選取器管線元件使用商務規則原則選取適當的路線。</span><span class="sxs-lookup"><span data-stu-id="649be-109">Configure the Itinerary Selector pipeline component to use a business rules policy to select the appropriate itinerary.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="649be-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="649be-110">Prerequisites</span></span>  
 <span data-ttu-id="649be-111">本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="649be-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="649be-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="649be-112">Before You Begin</span></span>  
 <span data-ttu-id="649be-113">您執行本使用說明主題中稍後的步驟之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="649be-113">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
- <span data-ttu-id="649be-114">建立 GlobalBank 西部測試訊息。</span><span class="sxs-lookup"><span data-stu-id="649be-114">Create the GlobalBank West test message.</span></span>  
  
- <span data-ttu-id="649be-115">建立 GlobalBank 東部測試訊息。</span><span class="sxs-lookup"><span data-stu-id="649be-115">Create the GlobalBank East test message.</span></span>  
  
  <span data-ttu-id="649be-116">下列程序描述如何進行每一種。</span><span class="sxs-lookup"><span data-stu-id="649be-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-the-globalbank-west-test-message"></a><span data-ttu-id="649be-117">若要建立 GlobalBank 西部測試訊息</span><span class="sxs-lookup"><span data-stu-id="649be-117">To create the GlobalBank West test message</span></span>  
  
1.  <span data-ttu-id="649be-118">在 Windows 檔案總管中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="649be-118">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="649be-119">建立一份 NAOrderDoc.xml，並命名 West.xml 的複本。</span><span class="sxs-lookup"><span data-stu-id="649be-119">Create a copy of NAOrderDoc.xml, and then name the copy West.xml.</span></span>  
  
3.  <span data-ttu-id="649be-120">在記事本中，開啟 West.xml，然後再將值變更**customerName**項目**GlobalBankWest**。</span><span class="sxs-lookup"><span data-stu-id="649be-120">In Notepad, open West.xml, and then change the value of the **customerName** element to **GlobalBankWest**.</span></span>  
  
4.  <span data-ttu-id="649be-121">儲存 West.xml 為 utf-8，，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="649be-121">Save West.xml as UTF-8, and then close Notepad.</span></span>  
  
#### <a name="to-create-the-globalbank-east-test-message"></a><span data-ttu-id="649be-122">若要建立 GlobalBank 東部測試訊息</span><span class="sxs-lookup"><span data-stu-id="649be-122">To create the GlobalBank East test message</span></span>  
  
1.  <span data-ttu-id="649be-123">在 Windows 檔案總管中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="649be-123">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="649be-124">建立一份 NAOrderDoc.xml，並命名 East.xml 的複本。</span><span class="sxs-lookup"><span data-stu-id="649be-124">Create a copy of NAOrderDoc.xml, and then name the copy East.xml.</span></span>  
  
3.  <span data-ttu-id="649be-125">在記事本中，開啟 East.xml，然後再將值變更**customerName**項目**GlobalBankEast**。</span><span class="sxs-lookup"><span data-stu-id="649be-125">In Notepad, open East.xml, and then change the value of the **customerName** element to **GlobalBankEast**.</span></span>  
  
4.  <span data-ttu-id="649be-126">儲存 East.xml 為 utf-8，，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="649be-126">Save East.xml as UTF-8, and then close Notepad.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="649be-127">步驟</span><span class="sxs-lookup"><span data-stu-id="649be-127">Steps</span></span>  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a><span data-ttu-id="649be-128">若要建立商務規則引擎 (BRE) 原則，以選取路線，使用自訂訊息屬性</span><span class="sxs-lookup"><span data-stu-id="649be-128">To create a Business Rules Engine (BRE) policy to select an itinerary using custom message properties</span></span>  
  
1.  <span data-ttu-id="649be-129">按一下 **開始**在工作列上，指向**所有程式**，指向**BizTalk Server**，然後按一下**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="649be-129">Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="649be-130">在 [原則總管] 中，以滑鼠右鍵按一下**原則**，然後按一下**新增新的原則**。</span><span class="sxs-lookup"><span data-stu-id="649be-130">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="649be-131">命名原則**ResolveItineraryBasedOnCustomer**。</span><span class="sxs-lookup"><span data-stu-id="649be-131">Name the policy **ResolveItineraryBasedOnCustomer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-132">本使用說明主題使用與本主題中所建立的相同商務規則原則和路線[如何： 分割交換，並將產生的訊息路由至多個檔案的位置使用不同路線](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)。</span><span class="sxs-lookup"><span data-stu-id="649be-132">This How-to topic uses the same business rules policy and itineraries as those created in the topic [How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md).</span></span> <span data-ttu-id="649be-133">如果您已經完成該區段，您可以跳至 」 來建立和設定 ESB 匝道 」 的程序，稍後在本主題中。</span><span class="sxs-lookup"><span data-stu-id="649be-133">If you have already completed that section, you can skip to the procedure, "To create and configure an ESB on-ramp" later in this topic.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a><span data-ttu-id="649be-134">若要新增客戶 GlobalBank 西部的選取項目規則</span><span class="sxs-lookup"><span data-stu-id="649be-134">To add a selection rule for customer GlobalBank West</span></span>  
  
1.  <span data-ttu-id="649be-135">在  **ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增規則**。</span><span class="sxs-lookup"><span data-stu-id="649be-135">In the **ResolveItineraryBasedOnCustomer** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="649be-136">命名規則**SetGlobalBankWestItinerary**。</span><span class="sxs-lookup"><span data-stu-id="649be-136">Name the rule **SetGlobalBankWestItinerary**.</span></span>  
  
2.  <span data-ttu-id="649be-137">在 [事實總管] 中，按一下**XML 結構描述**索引標籤上，以滑鼠右鍵按一下**結構描述**，然後按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="649be-137">In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="649be-138">在 [**結構描述檔案**] 對話方塊中，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。選取 DynamicResolution.Schemas **NAOrderDoc.xsd**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="649be-138">In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select **NAOrderDoc.xsd**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-139">這是定義 NAOrderDoc.xml 訊息，這用來建立您將用來測試西和東訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="649be-139">This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.</span></span>  
  
4.  <span data-ttu-id="649be-140">在 [事實總管] 中，按一下**NAOrderDoc.xsd**，按一下**文件類型**屬性，在 [屬性] 窗格中，然後按**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="649be-140">In Facts Explorer, click **NAOrderDoc.xsd**, click the **Document Type** property in the Properties pane, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-141">這是結構描述的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="649be-141">This is the fully qualified name of the schema.</span></span>  
  
5.  <span data-ttu-id="649be-142">在 [事實總管] 中，展開**NAOrderDoc.xsd**，然後展開**OrderDoc**。</span><span class="sxs-lookup"><span data-stu-id="649be-142">In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.</span></span>  
  
6.  <span data-ttu-id="649be-143">在 [規則] 視窗中，以滑鼠右鍵按一下**條件**，指向**述詞**，然後按一下**等於**。</span><span class="sxs-lookup"><span data-stu-id="649be-143">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
7.  <span data-ttu-id="649be-144">從 [事實總管] 中，拖曳**customerName**項目**引數 1**節點底下**條件**。</span><span class="sxs-lookup"><span data-stu-id="649be-144">From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.</span></span>  
  
8.  <span data-ttu-id="649be-145">按一下  **argument2**節點，然後按**GlobalBankWest**。</span><span class="sxs-lookup"><span data-stu-id="649be-145">Click the **argument2** node, and then type **GlobalBankWest**.</span></span>  
  
9. <span data-ttu-id="649be-146">在 事實總管 中，按一下**詞彙** 索引標籤。展開**ESB。路線**詞彙，依序展開**1.1 版**，然後將拖曳**設定路線名稱**定義**動作**。</span><span class="sxs-lookup"><span data-stu-id="649be-146">In Facts Explorer, click the **Vocabularies** tab. Expand the **ESB.Itinerary** vocabulary, expand **Version 1.1**, and then drag the **Set Itinerary Name** definition to **Actions**.</span></span>  
  
10. <span data-ttu-id="649be-147">按一下  **\<空字串\>**，然後輸入**GlobalBankWestItinerary**。</span><span class="sxs-lookup"><span data-stu-id="649be-147">Click **\<empty string\>**, and then type **GlobalBankWestItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-148">稍後在本使用說明主題中，您將建立此行程來處理訊息從 GlobalBank 西部。</span><span class="sxs-lookup"><span data-stu-id="649be-148">Later in this How-to topic, you will create this itinerary to process messages from GlobalBank West.</span></span>  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a><span data-ttu-id="649be-149">將選取的規則適用於客戶 GlobalBank 東部</span><span class="sxs-lookup"><span data-stu-id="649be-149">To add a selection rule for Customer GlobalBank East</span></span>  
  
1.  <span data-ttu-id="649be-150">在 [原則總管] 中，以滑鼠右鍵按一下**SetGlobalBankWestItinerary**規則，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="649be-150">In Policy Explorer, right-click the **SetGlobalBankWestItinerary** rule, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="649be-151">以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="649be-151">Right-click **Version 1.0 (not saved)**, and then click **Paste**.</span></span>  
  
3.  <span data-ttu-id="649be-152">在**新的規則名稱**] 對話方塊中，輸入**SetGlobalBankEastItinerary**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="649be-152">In the **New Rule Name** dialog box, type **SetGlobalBankEastItinerary**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="649be-153">在 [原則總管] 中，按一下**SetGlobalBankEastItinerary**規則。</span><span class="sxs-lookup"><span data-stu-id="649be-153">In Policy Explorer, click the **SetGlobalBankEastItinerary** rule.</span></span>  
  
5.  <span data-ttu-id="649be-154">在 **條件**區段中，以滑鼠右鍵按一下**GlobalBankWest**，然後按一下**重設引數**。</span><span class="sxs-lookup"><span data-stu-id="649be-154">In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.</span></span>  
  
6.  <span data-ttu-id="649be-155">按一下  **argument2**，然後輸入**GlobalBankEast**。</span><span class="sxs-lookup"><span data-stu-id="649be-155">Click **argument2**, and then type **GlobalBankEast**.</span></span>  
  
7.  <span data-ttu-id="649be-156">在 **動作**區段中，以滑鼠右鍵按一下**GlobalBankWestItinerary**，然後按一下**重設引數**。</span><span class="sxs-lookup"><span data-stu-id="649be-156">In the **Actions** section, right-click **GlobalBankWestItinerary**, and then click **Reset argument**.</span></span>  
  
8.  <span data-ttu-id="649be-157">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo\<接收位置，然後按一下\>停用**。</span><span class="sxs-lookup"><span data-stu-id="649be-157">Click **\<empty string\>** and then type **GlobalBankEastItinerary**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-158">在後OnRamp.Itinerary.HowTo接收位置已停用，以滑鼠右鍵按一下，然後按一下 刪除。</span><span class="sxs-lookup"><span data-stu-id="649be-158">Later in the How-to topic, you will create this itinerary to process messages from GlobalBank East.</span></span>  
  
#### <a name="to-publish-and-deploy-the-policy"></a><span data-ttu-id="649be-159">發佈和部署原則</span><span class="sxs-lookup"><span data-stu-id="649be-159">To publish and deploy the policy</span></span>  
  
1.  <span data-ttu-id="649be-160">在 [**確認刪除接收位置**] 對話方塊中，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="649be-160">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="649be-161">在 [原則總管] 中，在**ResolveItineraryBasedOnCustomer**原則，以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="649be-161">In Policy Explorer, under the **ResolveItineraryBasedOnCustomer** policy, right click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model-for-globalbank-west-messages"></a><span data-ttu-id="649be-162">若要建立 GlobalBank 西部訊息 ESB 路線的特定領域語言 (DSL) 模型</span><span class="sxs-lookup"><span data-stu-id="649be-162">To create an ESB itinerary domain-specific language (DSL) model for GlobalBank West messages</span></span>  
  
1.  <span data-ttu-id="649be-163">在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。</span><span class="sxs-lookup"><span data-stu-id="649be-163">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="649be-164">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。</span><span class="sxs-lookup"><span data-stu-id="649be-164">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="649be-165">在 **加入新項目**對話方塊，在 範本 窗格中，按一下**ItineraryDsl**。</span><span class="sxs-lookup"><span data-stu-id="649be-165">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="649be-166">在 **名稱**方塊中，輸入**GlobalBankWestItinerary**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="649be-166">In the **Name** box, type **GlobalBankWestItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a><span data-ttu-id="649be-167">若要設定 GlobalBank 西部路線的屬性</span><span class="sxs-lookup"><span data-stu-id="649be-167">To configure the properties of the GlobalBank West itinerary</span></span>  
  
1.  <span data-ttu-id="649be-168">在 Visual Studio 中，按一下設計介面**GlobalBankWestItinerary.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="649be-168">In Visual Studio, click the design surface of **GlobalBankWestItinerary.itinerary**.</span></span> <span data-ttu-id="649be-169">在 [ **GlobalBankWestItinerary**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-169">In the **GlobalBankWestItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-170">在 **模型匯出工具**下拉式清單中，按一下**資料庫路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="649be-170">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="649be-171">按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="649be-171">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="649be-172">在 **連接屬性** 對話方塊中，選擇裝載路線的存放庫資料庫中，SQL Server，然後指定 資料庫名稱 (預設名稱是**EsbItineraryDb**)。</span><span class="sxs-lookup"><span data-stu-id="649be-172">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="649be-173">在 **路線狀態**下拉式清單中，按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="649be-173">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-174">此步驟可讓您匯出至中央儲存機制; 的路線可以選取路線，並將它附加在訊息接收時從此存放庫中。</span><span class="sxs-lookup"><span data-stu-id="649be-174">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository upon message reception.</span></span> <span data-ttu-id="649be-175">您稍後將會設定路線選取器管線元件，用以評估內送的訊息，並選取適當的路線，從這個儲存機制中的商務規則引擎解析程式 (BRI)。</span><span class="sxs-lookup"><span data-stu-id="649be-175">You will later configure the Itinerary Selector pipeline component to use the Business Rules Engine resolver (BRI) to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="649be-176">若要定義的路線結構</span><span class="sxs-lookup"><span data-stu-id="649be-176">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="649be-177">從 [工具箱] 拖曳**匝道**模型項目到設計介面。</span><span class="sxs-lookup"><span data-stu-id="649be-177">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="649be-178">在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-178">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-179">按一下 **名稱**屬性，然後按**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="649be-179">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="649be-180">在  **Extender**下拉式清單中，按一下**匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="649be-180">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="649be-181">在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="649be-181">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="649be-182">在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="649be-182">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="649be-183">從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**ReceiveNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="649be-183">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="649be-184">在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-184">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-185">按一下 **名稱**屬性，然後按**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="649be-185">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="649be-186">在  **Extender**下拉式清單中，按一下**出口匝 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="649be-186">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="649be-187">在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="649be-187">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="649be-188">在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="649be-188">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="649be-189">從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="649be-189">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="649be-190">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-190">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-191">按一下 **名稱**屬性，然後按**RouteMessage**。</span><span class="sxs-lookup"><span data-stu-id="649be-191">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="649be-192">在 **路線服務的擴充項**下拉式清單中，按一下**出口匝路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="649be-192">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="649be-193">在 **出口匝**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="649be-193">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="649be-194">以滑鼠右鍵按一下**解析**的集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="649be-194">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="649be-195">在 [ **Resolver1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-195">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-196">按一下 **名稱**屬性，然後按**StaticResolver**。</span><span class="sxs-lookup"><span data-stu-id="649be-196">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="649be-197">在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。</span><span class="sxs-lookup"><span data-stu-id="649be-197">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="649be-198">在 **傳輸名稱**下拉式清單中，按一下**檔案**。</span><span class="sxs-lookup"><span data-stu-id="649be-198">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="649be-199">按一下 **傳輸位置**屬性，然後按**C:\HowTos\Out\West%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="649be-199">Click the **Transport Location** property, and then type **C:\HowTos\Out\West%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="649be-200">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="649be-200">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="649be-201">拖曳連接，以從**ReceiveNAOrder**模型項目**RouteMessage**模型項目。</span><span class="sxs-lookup"><span data-stu-id="649be-201">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="649be-202">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="649be-202">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="649be-203">拖曳連接，以從**RouteMessage**模型項目**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="649be-203">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="649be-204">將模型匯出至路線資料庫</span><span class="sxs-lookup"><span data-stu-id="649be-204">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="649be-205">在 Visual Studio 中，以滑鼠右鍵按一下設計介面**GlobalBankWestItinerary**路線，，然後按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="649be-205">In Visual Studio, right-click the design surface of the **GlobalBankWestItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-206">路線已匯出至路線資料庫，並可立即供路線選取器元件。</span><span class="sxs-lookup"><span data-stu-id="649be-206">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="649be-207">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="649be-207">Save all project artifacts.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a><span data-ttu-id="649be-208">若要建立 GlobalBank 東部訊息 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="649be-208">To create an ESB itinerary DSL model for GlobalBank East message</span></span>  
  
1.  <span data-ttu-id="649be-209">在 Visual Studio 中，開啟 [C:\HowTos\Patterns.sln]。</span><span class="sxs-lookup"><span data-stu-id="649be-209">In Visual Studio, open C:\HowTos\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="649be-210">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。</span><span class="sxs-lookup"><span data-stu-id="649be-210">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="649be-211">在 **加入新項目**對話方塊，在 範本 窗格中，按一下**ItineraryDsl**。</span><span class="sxs-lookup"><span data-stu-id="649be-211">In the **Add New Item** dialog box, in the Templates pane, click **ItineraryDsl**.</span></span>  
  
4.  <span data-ttu-id="649be-212">在 **名稱**方塊中，輸入**GlobalBankEastItinerary**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="649be-212">In the **Name** box, type **GlobalBankEastItinerary**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a><span data-ttu-id="649be-213">若要設定 GlobalBank 東部路線的屬性</span><span class="sxs-lookup"><span data-stu-id="649be-213">To configure the properties of the GlobalBank East itinerary</span></span>  
  
1.  <span data-ttu-id="649be-214">在 Visual Studio 中，按一下設計介面**GlobalBankEastItinerary.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="649be-214">In Visual Studio, click the design surface of **GlobalBankEastItinerary.itinerary**.</span></span> <span data-ttu-id="649be-215">在 [ **GlobalBankEastItinerary**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-215">In the **GlobalBankEastItinerary** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-216">在 **模型匯出工具**下拉式清單中，按一下**資料庫路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="649be-216">In the **Model Exporter** drop-down list, click **Database Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="649be-217">按一下旁邊的省略符號按鈕 （...）**路線資料庫**屬性。</span><span class="sxs-lookup"><span data-stu-id="649be-217">Click the ellipsis button (...) next to the **Itinerary Database** property.</span></span>  
  
    3.  <span data-ttu-id="649be-218">在 **連接屬性** 對話方塊中，選擇裝載路線的存放庫資料庫中，SQL Server，然後指定 資料庫名稱 (預設名稱是**EsbItineraryDb**)。</span><span class="sxs-lookup"><span data-stu-id="649be-218">In the **Connection Properties** dialog box, choose the SQL Server that hosts the itinerary repository database, and then specify the name of the database (the default name is **EsbItineraryDb**).</span></span>  
  
2.  <span data-ttu-id="649be-219">在 **路線狀態**下拉式清單中，按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="649be-219">In the **Itinerary Status** drop-down list, click **Deployed**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-220">此步驟可讓您匯出至中央儲存機制; 的路線可以選取路線，並將其接收訊息時，從這個儲存機制連接。</span><span class="sxs-lookup"><span data-stu-id="649be-220">This step enables you to export the itinerary to a central repository; itineraries can be selected and attached from this repository when messages are received.</span></span> <span data-ttu-id="649be-221">您稍後將會設定路線選取器管線元件，用以評估內送的訊息，並選取適當的路線，從這個儲存機制的 BRI 解析程式。</span><span class="sxs-lookup"><span data-stu-id="649be-221">You will later configure the Itinerary Selector pipeline component to use the BRI resolver to evaluate inbound messages and select the appropriate itinerary from this repository.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="649be-222">若要定義的路線結構</span><span class="sxs-lookup"><span data-stu-id="649be-222">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="649be-223">從 [工具箱] 拖曳**匝道**模型項目到設計介面。</span><span class="sxs-lookup"><span data-stu-id="649be-223">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="649be-224">在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-224">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-225">按一下 **名稱**屬性，然後按**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="649be-225">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="649be-226">在  **Extender**下拉式清單中，按一下**匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="649be-226">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="649be-227">在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="649be-227">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="649be-228">在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="649be-228">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="649be-229">從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**ReceiveNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="649be-229">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="649be-230">在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-230">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-231">按一下 **名稱**屬性，然後按**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="649be-231">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="649be-232">在  **Extender**下拉式清單中，按一下**出口匝 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="649be-232">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="649be-233">在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="649be-233">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="649be-234">在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="649be-234">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="649be-235">從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="649be-235">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="649be-236">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-236">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-237">按一下 **名稱**屬性，然後按**RouteMessage**。</span><span class="sxs-lookup"><span data-stu-id="649be-237">Click the **Name** property, and then type **RouteMessage**.</span></span>  
  
    2.  <span data-ttu-id="649be-238">在 **路線服務的擴充項**下拉式清單中，按一下**出口匝路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="649be-238">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="649be-239">在 **出口匝**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="649be-239">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="649be-240">以滑鼠右鍵按一下**解析**的集合**RouteMessage**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="649be-240">Right-click the **Resolver** collection of the **RouteMessage** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="649be-241">在 [ **Resolver1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-241">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="649be-242">按一下 **名稱**屬性，然後按**StaticResolver**。</span><span class="sxs-lookup"><span data-stu-id="649be-242">Click the **Name** property, and then type **StaticResolver**.</span></span>  
  
    2.  <span data-ttu-id="649be-243">在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。</span><span class="sxs-lookup"><span data-stu-id="649be-243">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="649be-244">在 **傳輸名稱**下拉式清單中，按一下**檔案**。</span><span class="sxs-lookup"><span data-stu-id="649be-244">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="649be-245">按一下 **傳輸位置**屬性，然後按**C:\HowTos\Out\East%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="649be-245">Click the **Transport Location** property, and then type **C:\HowTos\Out\East%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="649be-246">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="649be-246">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="649be-247">拖曳連接，以從**ReceiveNAOrder**模型項目**RouteMessage**模型項目。</span><span class="sxs-lookup"><span data-stu-id="649be-247">Drag a connection from the **ReceiveNAOrder** model element to the **RouteMessage** model element.</span></span>  
  
6.  <span data-ttu-id="649be-248">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="649be-248">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="649be-249">拖曳連接，以從**RouteMessage**模型項目**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="649be-249">Drag a connection from the **RouteMessage** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a><span data-ttu-id="649be-250">將模型匯出至路線資料庫</span><span class="sxs-lookup"><span data-stu-id="649be-250">To export the model to the itinerary database</span></span>  
  
1.  <span data-ttu-id="649be-251">在 Visual Studio 中，以滑鼠右鍵按一下設計介面**GlobalBankEastItinerary**路線，，然後按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="649be-251">In Visual Studio, right-click the design surface of the **GlobalBankEastItinerary** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-252">路線已匯出至路線資料庫，並可立即供路線選取器元件。</span><span class="sxs-lookup"><span data-stu-id="649be-252">The itinerary has been exported to the itinerary database and can now be used by the Itinerary Selector component.</span></span>  
  
2.  <span data-ttu-id="649be-253">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="649be-253">Save all project artifacts.</span></span>  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a><span data-ttu-id="649be-254">建立和設定 ESB 匝道</span><span class="sxs-lookup"><span data-stu-id="649be-254">To create and configure an ESB on-ramp</span></span>  
  
1.  <span data-ttu-id="649be-255">按一下 **開始**在工作列上，指向**所有程式**，指向**BizTalk Server**，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="649be-255">Click **Start** on the taskbar, point to **All Programs**, point to **BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="649be-256">在 BizTalk Server 管理主控台中，展開**BizTalk 群組**，展開**應用程式**，然後展開**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="649be-256">In the BizTalk Server Administration Console, expand **BizTalk Group**, expand **Applications**, and then expand **Microsoft.Practices.ESB**.</span></span>  
  
3.  <span data-ttu-id="649be-257">以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="649be-257">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
4.  <span data-ttu-id="649be-258">在 [**選取接收埠**] 對話方塊中，按一下**OnRamp.Itinerary**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="649be-258">In the **Select a Receive Port** dialog box, click **OnRamp.Itinerary**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="649be-259">在 **接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**OnRamp.Itinerary.HowTo**。</span><span class="sxs-lookup"><span data-stu-id="649be-259">In the **Receive Location Properties** dialog box, in the **Name** box, type **OnRamp.Itinerary.HowTo**.</span></span>  
  
6.  <span data-ttu-id="649be-260">在 **型別**下拉式清單中，按一下**檔案**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="649be-260">In the **Type** drop-down list, click **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="649be-261">中**FILE 傳輸屬性**對話方塊中，於**接收資料夾**方塊中，輸入**C:\HowTos\DropFolder**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="649be-261">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\HowTos\DropFolder**, and then click **OK**.</span></span>  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a><span data-ttu-id="649be-262">若要設定路線選取器管線元件</span><span class="sxs-lookup"><span data-stu-id="649be-262">To configure the Itinerary Selector pipeline component</span></span>  
  
1.  <span data-ttu-id="649be-263">在 **接收位置屬性**對話方塊的 **接收管線**下拉式清單中，按一下**ItinerarySelectReceiveXml**，然後按一下省略符號按鈕 （...).</span><span class="sxs-lookup"><span data-stu-id="649be-263">In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, click **ItinerarySelectReceiveXml**, and then click the ellipsis button (...).</span></span>  
  
2.  <span data-ttu-id="649be-264">使用**設定管線**對話方塊，即可設定下列各項**路線選取器**元件屬性：</span><span class="sxs-lookup"><span data-stu-id="649be-264">Use the **Configure Pipeline** dialog box to configure the following **Itinerary Selector** component properties:</span></span>  
  
    1.  <span data-ttu-id="649be-265">按一下  **ItineraryFactKey**屬性，然後按**Resolver.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="649be-265">Click the **ItineraryFactKey** property, and then type **Resolver.Itinerary**.</span></span>  
  
    2.  <span data-ttu-id="649be-266">按一下  **ResolverConnectionString**屬性，然後按**BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span><span class="sxs-lookup"><span data-stu-id="649be-266">Click the **ResolverConnectionString** property, and then type **BRI:\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true;**</span></span>  
  
    3.  <span data-ttu-id="649be-267">按一下 [ **[確定]** 以關閉**設定管線**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="649be-267">Click **OK** to close the **Configure Pipeline** dialog box.</span></span>  
  
3.  <span data-ttu-id="649be-268">按一下 [ **[確定]** 以關閉**接收位置屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="649be-268">Click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="649be-269">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="649be-269">In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Enable**.</span></span>  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a><span data-ttu-id="649be-270">若要測試的路線選取器 」 和 「 商務規則</span><span class="sxs-lookup"><span data-stu-id="649be-270">To test the itinerary selector and business rules</span></span>  
  
1.  <span data-ttu-id="649be-271">在 Windows 檔案總管中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="649be-271">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="649be-272">複製 （不會移動） 到 DropFolder 資料夾 East.xml 和 West.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="649be-272">Copy (do not move) the files East.xml and West.xml to the DropFolder folder.</span></span>  
  
3.  <span data-ttu-id="649be-273">瀏覽至 C:\HowTos\Out。請確認 East%MessageID%.xml 和 West%MessageID%.xml 訊息已寫入該目錄。</span><span class="sxs-lookup"><span data-stu-id="649be-273">Browse to C:\HowTos\Out. Verify that the East%MessageID%.xml and West%MessageID%.xml messages have been written to the directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="649be-274">除了客戶元素的值相同，但使用不同路線，根據路線選取器管線元件的解析度處理訊息。</span><span class="sxs-lookup"><span data-stu-id="649be-274">Though identical except for the value of the customer element, the messages were processed using different itineraries, based on the resolution of the Itinerary Selector pipeline component.</span></span>  
  
4.  <span data-ttu-id="649be-275">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**OnRamp.Itinerary.HowTo**接收位置，然後按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="649be-275">In the BizTalk Server Administration Console, right-click the **OnRamp.Itinerary.HowTo** receive location, and then click **Disable**.</span></span>  
  
5.  <span data-ttu-id="649be-276">在後**OnRamp.Itinerary.HowTo**接收位置已停用，以滑鼠右鍵按一下，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="649be-276">After the **OnRamp.Itinerary.HowTo** receive location is disabled, right-click it, and then click **Delete**.</span></span> <span data-ttu-id="649be-277">在 [**確認刪除接收位置**] 對話方塊中，按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="649be-277">In the **Confirm delete receive location** dialog box, click **Yes**.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="649be-278">其他資源</span><span class="sxs-lookup"><span data-stu-id="649be-278">Additional Resources</span></span>  
 <span data-ttu-id="649be-279">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="649be-279">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="649be-280">如何：分割交換，並使用不同路線將產生的訊息路由至多個檔案位置</span><span class="sxs-lookup"><span data-stu-id="649be-280">How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries</span></span>](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
-   [<span data-ttu-id="649be-281">開發活動</span><span class="sxs-lookup"><span data-stu-id="649be-281">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="649be-282">安裝和執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="649be-282">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [<span data-ttu-id="649be-283">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="649be-283">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [<span data-ttu-id="649be-284">訊息路由模式</span><span class="sxs-lookup"><span data-stu-id="649be-284">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)