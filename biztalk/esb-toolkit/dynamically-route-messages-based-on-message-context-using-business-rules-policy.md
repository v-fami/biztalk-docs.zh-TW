---
title: "如何： 動態地路由傳送訊息根據訊息內容使用商務規則原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d3b68de-6b24-46fe-ae0d-91afb630bc19
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717e0180ba92d49751342e00a4d0367832084135
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-dynamically-route-a-message-based-on-message-context-using-a-business-rules-policy"></a><span data-ttu-id="724cf-102">如何： 動態地路由傳送訊息的內容使用商務規則原則為基礎的訊息</span><span class="sxs-lookup"><span data-stu-id="724cf-102">How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy</span></span>
## <a name="goal"></a><span data-ttu-id="724cf-103">目標</span><span class="sxs-lookup"><span data-stu-id="724cf-103">Goal</span></span>  
 <span data-ttu-id="724cf-104">本節示範如何建立會決定訊息的端點，根據訊息內容屬性，使用行程[!INCLUDE[prague](../includes/prague-md.md)]商務規則引擎 (BRE) 原則，然後再路由訊息使用[!INCLUDE[prague](../includes/prague-md.md)]FILE 配接器。</span><span class="sxs-lookup"><span data-stu-id="724cf-104">This section demonstrates how to create an itinerary that determines message endpoints, based on message context properties, using a [!INCLUDE[prague](../includes/prague-md.md)] Business Rules Engine (BRE) policy, and then routes the message using the [!INCLUDE[prague](../includes/prague-md.md)] FILE adapter.</span></span>  
  
 <span data-ttu-id="724cf-105">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="724cf-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="724cf-106">建立商務規則原則評估訊息類型。</span><span class="sxs-lookup"><span data-stu-id="724cf-106">Create a business rules policy to evaluate message type.</span></span>  
  
-   <span data-ttu-id="724cf-107">建立動態路由使用商務規則原則路線路由受控滑動。</span><span class="sxs-lookup"><span data-stu-id="724cf-107">Create an itinerary routing slip to dynamically route using a business rules policy.</span></span>  
  
-   <span data-ttu-id="724cf-108">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="724cf-108">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="724cf-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="724cf-109">Prerequisites</span></span>  
 <span data-ttu-id="724cf-110">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="724cf-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="724cf-111">步驟</span><span class="sxs-lookup"><span data-stu-id="724cf-111">Steps</span></span>  
 <span data-ttu-id="724cf-112">**若要建立使用訊息內容屬性將訊息路由傳送的 BRE 原則**</span><span class="sxs-lookup"><span data-stu-id="724cf-112">**To create a BRE policy to route a message using message context properties**</span></span>  
  
1.  <span data-ttu-id="724cf-113">按一下**啟動**在工作列上，指向**所有程式**，指向   **[!INCLUDE[prague](../includes/prague-md.md)]** ，然後按一下**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="724cf-113">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="724cf-114">在 [原則總管] 中，以滑鼠右鍵按一下**原則**，然後按一下**新增原則**。</span><span class="sxs-lookup"><span data-stu-id="724cf-114">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="724cf-115">命名原則**RouteBasedOnMessageType**。</span><span class="sxs-lookup"><span data-stu-id="724cf-115">Name the policy **RouteBasedOnMessageType**.</span></span>  
  
 <span data-ttu-id="724cf-116">**若要加入北美地區的訂單的路由規則**</span><span class="sxs-lookup"><span data-stu-id="724cf-116">**To add a routing rule for North American orders**</span></span>  
  
1.  <span data-ttu-id="724cf-117">在**RouteBasedOnMessageType**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增規則**。</span><span class="sxs-lookup"><span data-stu-id="724cf-117">In the **RouteBasedOnMessageType** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="724cf-118">命名規則**SetNAOrderEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="724cf-118">Name the rule **SetNAOrderEndpoint**.</span></span>  
  
2.  <span data-ttu-id="724cf-119">在 規則 視窗中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下**等於**。</span><span class="sxs-lookup"><span data-stu-id="724cf-119">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
3.  <span data-ttu-id="724cf-120">在 [事實總管] 中，展開**ESB。ContextInfo**詞彙中，展開**1.0 版**，然後將拖曳**內容的訊息類型**事實**引數 1**節點下的**條件**。</span><span class="sxs-lookup"><span data-stu-id="724cf-120">In Facts Explorer, expand the **ESB.ContextInfo** vocabulary, expand **Version 1.0**, and then drag the **Context Message Type** fact to the **argument1** node under **Conditions**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="724cf-121">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個可以用來建立規則的詞彙。</span><span class="sxs-lookup"><span data-stu-id="724cf-121">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several vocabularies that can be used for creating rules.</span></span> <span data-ttu-id="724cf-122">這些應該取代或夾帶您自己的詞彙。</span><span class="sxs-lookup"><span data-stu-id="724cf-122">Some of these should be replaced or augmented with your own vocabularies.</span></span> <span data-ttu-id="724cf-123">例如， **DynamicRunTimeMaptypes**原則都有定義中的對應**GlobalBank**範例。</span><span class="sxs-lookup"><span data-stu-id="724cf-123">For example, the **DynamicRunTimeMaptypes** policy has definitions for the maps provided in the **GlobalBank** samples.</span></span>  
  
4.  <span data-ttu-id="724cf-124">按一下**引數 2**  節點，然後輸入**http://globalbank.esb.dynamicresolution.com/northamericanservices/#OrderDoc**</span><span class="sxs-lookup"><span data-stu-id="724cf-124">Click the **argument2** node, and then type **http://globalbank.esb.dynamicresolution.com/northamericanservices/#OrderDoc**</span></span>  
  
5.  <span data-ttu-id="724cf-125">在 [事實總管] 中，展開**ESB。EndPointInfo**詞彙中，展開**1.0 版**，然後將拖曳**設定結束點輸出傳輸位置**定義**動作**。</span><span class="sxs-lookup"><span data-stu-id="724cf-125">In Facts Explorer, expand the **ESB.EndPointInfo** vocabulary, expand **Version 1.0**, and then drag the **Set End Point Outbound Transport Location** definition to **Actions**.</span></span>  
  
6.  <span data-ttu-id="724cf-126">按一下**\<空字串 >**，然後輸入**C:\HowTos\Out\NorthAmerica%MessageID%.xml**</span><span class="sxs-lookup"><span data-stu-id="724cf-126">Click **\<empty string>**, and then type **C:\HowTos\Out\NorthAmerica%MessageID%.xml**</span></span>  
  
7.  <span data-ttu-id="724cf-127">從 [事實總管] 中，拖曳**設定結束點輸出傳輸類型**定義**動作**。</span><span class="sxs-lookup"><span data-stu-id="724cf-127">From Facts Explorer, drag the **Set End Point Outbound Transport Type** definition to **Actions**.</span></span>  
  
8.  <span data-ttu-id="724cf-128">在 [事實總管] 中，展開**ESB。TansportTypes**詞彙中，展開**1.0 版**，然後將拖曳**配接器提供者**定義**\<空字串 >**。</span><span class="sxs-lookup"><span data-stu-id="724cf-128">In Facts Explorer, expand the **ESB.TansportTypes** vocabulary, expand **Version 1.0**, and then drag the **Adaptor Providers** definition to **\<empty string>**.</span></span>  
  
9. <span data-ttu-id="724cf-129">在 [動作] 窗格中，依序展開**配接器提供者**下拉式清單，然後按一下**檔案**。</span><span class="sxs-lookup"><span data-stu-id="724cf-129">In the Actions pane, expand the **Adaptor Providers** drop-down list, and then click **FILE**.</span></span>  
  
 <span data-ttu-id="724cf-130">**若要發行和部署原則**</span><span class="sxs-lookup"><span data-stu-id="724cf-130">**To publish and deploy the policy**</span></span>  
  
1.  <span data-ttu-id="724cf-131">在 [原則總管] 中，在**RouteBasedOnMessageType**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="724cf-131">In Policy Explorer, under the **RouteBasedOnMessageType** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="724cf-132">在 [原則總管] 中，在**RouteBasedOnMessageType**原則，以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="724cf-132">In Policy Explorer, under the **RouteBasedOnMessageType** policy, right click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="724cf-133">**若要建立 ESB 路線網域特定領域語言 (DSL) 模型**</span><span class="sxs-lookup"><span data-stu-id="724cf-133">**To create an ESB itinerary domain-specific language (DSL) model**</span></span>  
  
1.  <span data-ttu-id="724cf-134">在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="724cf-134">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="724cf-135">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新的行程**。</span><span class="sxs-lookup"><span data-stu-id="724cf-135">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="724cf-136">在**名稱**方塊中，輸入**MessageType**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="724cf-136">In the **Name** box, type **MessageType**, and then click **Add**.</span></span>  
  
 <span data-ttu-id="724cf-137">**若要設定的路線屬性**</span><span class="sxs-lookup"><span data-stu-id="724cf-137">**To configure the properties of the itinerary**</span></span>  
  
1.  <span data-ttu-id="724cf-138">在 Visual Studio 中，按一下設計介面的**MessageType.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="724cf-138">In Visual Studio, click the design surface of **MessageType.itinerary**.</span></span> <span data-ttu-id="724cf-139">在**MessageType**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="724cf-139">In the **MessageType** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="724cf-140">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="724cf-140">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="724cf-141">在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="724cf-141">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="724cf-142">在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\MessageType**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="724cf-142">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\MessageType**, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="724cf-143">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="724cf-143">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="724cf-144">將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="724cf-144">Exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="724cf-145">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="724cf-145">You will complete this process later in this How-to topic.</span></span>  
  
 <span data-ttu-id="724cf-146">**若要定義路線結構**</span><span class="sxs-lookup"><span data-stu-id="724cf-146">**To define the structure of the itinerary**</span></span>  
  
1.  <span data-ttu-id="724cf-147">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="724cf-147">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="724cf-148">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="724cf-148">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="724cf-149">按一下**名稱**屬性，，然後輸入**ReceiveOrders**。</span><span class="sxs-lookup"><span data-stu-id="724cf-149">Click the **Name** property, and then type **ReceiveOrders**.</span></span>  
  
    2.  <span data-ttu-id="724cf-150">在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="724cf-150">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="724cf-151">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="724cf-151">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="724cf-152">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="724cf-152">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="724cf-153">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。</span><span class="sxs-lookup"><span data-stu-id="724cf-153">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="724cf-154">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="724cf-154">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="724cf-155">按一下**名稱**屬性，，然後輸入**BreRoute**。</span><span class="sxs-lookup"><span data-stu-id="724cf-155">Click the **Name** property, and then type **BreRoute**.</span></span>  
  
    2.  <span data-ttu-id="724cf-156">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="724cf-156">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="724cf-157">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="724cf-157">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="724cf-158">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="724cf-158">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="724cf-159">在**容器**下拉式清單中，展開**ReceiveOrders**，然後按一下**接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="724cf-159">In the **Container** drop-down list, expand **ReceiveOrders**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="724cf-160">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="724cf-160">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3.  <span data-ttu-id="724cf-161">以滑鼠右鍵按一下**解析程式**集合**BreRoute**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="724cf-161">Right-click the **Resolver** collection of the **BreRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="724cf-162">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="724cf-162">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="724cf-163">按一下**名稱**屬性，，然後輸入**ByMessageType**。</span><span class="sxs-lookup"><span data-stu-id="724cf-163">Click the **Name** property, and then type **ByMessageType**.</span></span>  
  
    2.  <span data-ttu-id="724cf-164">在**解析程式實作**下拉式清單中，按一下  **Bre 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="724cf-164">In the **Resolver Implementation** drop-down list, click **Bre Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="724cf-165">在**原則**下拉式清單中，按一下  **RouteBasedOnMessageType v 1.0**。</span><span class="sxs-lookup"><span data-stu-id="724cf-165">In the **Policy** drop-down list, click **RouteBasedOnMessageType v 1.0**.</span></span>  
  
4.  <span data-ttu-id="724cf-166">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="724cf-166">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="724cf-167">拖曳連接**ReceiveOrders**模型項目的**BreRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="724cf-167">Drag a connection from the **ReceiveOrders** model element to the **BreRoute** model element.</span></span>  
  
5.  <span data-ttu-id="724cf-168">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**BreRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="724cf-168">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BreRoute** model element.</span></span> <span data-ttu-id="724cf-169">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="724cf-169">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="724cf-170">按一下**名稱**屬性，，然後輸入**SendBasedOnType**。</span><span class="sxs-lookup"><span data-stu-id="724cf-170">Click the **Name** property, and then type **SendBasedOnType**.</span></span>  
  
    2.  <span data-ttu-id="724cf-171">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="724cf-171">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="724cf-172">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="724cf-172">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="724cf-173">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="724cf-173">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
6.  <span data-ttu-id="724cf-174">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**BreRoute**模型項目和**SendBasedOnType**模型項目。</span><span class="sxs-lookup"><span data-stu-id="724cf-174">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BreRoute** model element and the **SendBasedOnType** model element.</span></span> <span data-ttu-id="724cf-175">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="724cf-175">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="724cf-176">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="724cf-176">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="724cf-177">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="724cf-177">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="724cf-178">在**匝道**下拉式清單中，展開**SendBasedOnType**，然後按一下**傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="724cf-178">In the **Off-Ramp** drop-down list, expand **SendBasedOnType**, and then click **Send Handlers**.</span></span>  
  
7.  <span data-ttu-id="724cf-179">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="724cf-179">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="724cf-180">拖曳連接**BreRoute**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="724cf-180">Drag a connection from the **BreRoute** model element to the **SendPortFilter** model element.</span></span>  
  
8.  <span data-ttu-id="724cf-181">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="724cf-181">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="724cf-182">拖曳連接**SendPortFilter**模型項目的**SendBasedOnType**模型項目。</span><span class="sxs-lookup"><span data-stu-id="724cf-182">Drag a connection from the **SendPortFilter** model element to the **SendBasedOnType** model element.</span></span>  
  
 <span data-ttu-id="724cf-183">**若要匯出的行程測試用戶端使用的模型**</span><span class="sxs-lookup"><span data-stu-id="724cf-183">**To export the model for use with the Itinerary Test Client**</span></span>  
  
1.  <span data-ttu-id="724cf-184">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**MessageType**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="724cf-184">In Visual Studio, right-click the design surface of the **MessageType** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="724cf-185">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="724cf-185">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="724cf-186">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="724cf-186">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="724cf-187">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (MessageType.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="724cf-187">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (MessageType.xml).</span></span>  
  
 <span data-ttu-id="724cf-188">**若要測試路線**</span><span class="sxs-lookup"><span data-stu-id="724cf-188">**To test the itinerary**</span></span>  
  
1.  <span data-ttu-id="724cf-189">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="724cf-189">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="724cf-190">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="724cf-190">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="724cf-191">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="724cf-191">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="724cf-192">選取**MessageType.xml**，然後按一下**開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="724cf-192">Select **MessageType.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="724cf-193">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="724cf-193">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="724cf-194">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="724cf-194">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="724cf-195">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="724cf-195">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="724cf-196">選取**NAOrderDoc.xml**，然後按一下**開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="724cf-196">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="724cf-197">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="724cf-197">Click the **Submit Request** button.</span></span> <span data-ttu-id="724cf-198">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="724cf-198">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="724cf-199">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out\\。</span><span class="sxs-lookup"><span data-stu-id="724cf-199">In Windows Explorer, browse to C:\HowTos\Out\\.</span></span> <span data-ttu-id="724cf-200">請確認 NorthAmerica%MessageID%.xml 訊息已寫入至目錄。</span><span class="sxs-lookup"><span data-stu-id="724cf-200">Verify that the NorthAmerica%MessageID%.xml message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="724cf-201">其他資源</span><span class="sxs-lookup"><span data-stu-id="724cf-201">Additional Resources</span></span>  
 <span data-ttu-id="724cf-202">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="724cf-202">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="724cf-203">如何： 選取 使用商務規則原則路線</span><span class="sxs-lookup"><span data-stu-id="724cf-203">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="724cf-204">如何： 轉換訊息，並將產生的訊息路由至使用路線的路由名單的檔案位置</span><span class="sxs-lookup"><span data-stu-id="724cf-204">How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip</span></span>](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [<span data-ttu-id="724cf-205">如何： 實作內容架構路由使用商務規則原則已知的訊息類型</span><span class="sxs-lookup"><span data-stu-id="724cf-205">How to: Implement Content-Based Routing Using a Business Rules Policy for a Known Message Type</span></span>](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
-   [<span data-ttu-id="724cf-206">開發活動</span><span class="sxs-lookup"><span data-stu-id="724cf-206">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="724cf-207">訊息的路由模式</span><span class="sxs-lookup"><span data-stu-id="724cf-207">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="724cf-208">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="724cf-208">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)